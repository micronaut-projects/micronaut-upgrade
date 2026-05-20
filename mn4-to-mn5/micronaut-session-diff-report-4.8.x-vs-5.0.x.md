# Diff Report: `4.8.x` vs `5.0.x`

**Generated:** 2026-04-17
**Base (A):** `/Users/sdelamo/github/micronaut/mn4/micronaut-session` — branch `4.8.x` @ `22aa84b4`
**Comparison (B):** `/Users/sdelamo/github/micronaut/mn5/micronaut-session` — branch `5.0.x` @ `141a7ca4`

---

## Summary

| Category | Count |
|----------|-------|
| Files added (only in B) | 5 |
| Files removed (only in A) | 0 |
| Files modified | 38 |
| Total changes | 43 |

> Build artifact directories (`.gradle/`, `.kotlin/`, `build/`) excluded — not source changes.

---

## Dependency Changes

### Third-Party Upgrades

- Gradle wrapper: `8.14.3` → `9.4.1` — [Release notes](https://github.com/gradle/gradle/releases/tag/v9.4.1)
- GraalVM Native Build Tools plugin: `0.10.6` → `1.0.0` — [Release notes](https://github.com/graalvm/native-build-tools/releases/tag/1.0.0)

### Micronaut Version Bumps

| Dependency | 4.8.x | 5.0.x |
|---|---|---|
| `micronaut` (BOM) | `4.10.3` | `5.0.0-M22` |
| `micronaut-cache` | `5.3.0` | `6.0.0-M2` |
| `micronaut-logging` | `1.7.0` | `2.0.0-M2` |
| `micronaut-serde` | `2.15.5` | `3.0.0-M6` |
| `micronaut-build` shared settings | `7.6.4` | `8.0.0-M17` |

### Removed from `libs.versions.toml`

- `micronaut-docs` `2.0.0` — removed
- `groovy` `4.0.18` — removed
- `kotlin` `2.1.21` — removed (Kotlin plugin now sourced via `io.micronaut.build.internal.kotlin-kapt`)

### `gradle/libs.versions.toml`

```diff
--- a/gradle/libs.versions.toml
+++ b/gradle/libs.versions.toml
@@ -1,12 +1,8 @@
 [versions]
-micronaut = "4.10.3"
-micronaut-cache = "5.3.0"
-micronaut-docs = "2.0.0"
-micronaut-logging = "1.7.0"
-micronaut-serde = "2.15.5"
-micronaut-test = "4.7.0"
-groovy = "4.0.18"
-kotlin = '2.1.21'
+micronaut = "5.0.0-M22"
+micronaut-cache = "6.0.0-M2"
+micronaut-logging = "2.0.0-M2"
+micronaut-serde = "3.0.0-M6"
 
 [libraries]
 micronaut-cache = { module = "io.micronaut.cache:micronaut-cache-bom", version.ref = "micronaut-cache" }
 micronaut-serde = { module = "io.micronaut.serde:micronaut-serde-bom", version.ref = "micronaut-serde" }
 
-junit-jupiter-engine = { module = 'org.junit.jupiter:junit-jupiter-engine' }
-kotlin-test = { module = "org.jetbrains.kotlin:kotlin-test", version.ref = "kotlin" }
 [plugins]
-kotlin-jvm = { id = 'org.jetbrains.kotlin.jvm', version.ref = 'kotlin' }
-kotlin-kapt = { id = 'org.jetbrains.kotlin.kapt', version.ref = 'kotlin' }
+
```

### `gradle.properties`

```diff
-projectVersion=4.8.1-SNAPSHOT
+projectVersion=5.0.0-SNAPSHOT
```

### `gradle/wrapper/gradle-wrapper.properties`

```diff
-distributionUrl=https\://services.gradle.org/distributions/gradle-8.14.3-bin.zip
+distributionUrl=https\://services.gradle.org/distributions/gradle-9.4.1-bin.zip
```

### `settings.gradle`

```diff
-    id 'io.micronaut.build.shared.settings' version '7.6.4'
+    id 'io.micronaut.build.shared.settings' version '8.0.0-M17'
```

---

## Added Files

- `.agents/` _(directory — content not inspected)_
- `.github/workflows/sonatype.yml`
- `.sdkmanrc`
- `buildSrc/gradle.properties`
- `session/src/test/java/io/micronaut/session/SessionEventListenerRegistrationTest.java`

---

## Removed Files

_(none)_

---

## Modified Files

### Nullability annotation migration (pervasive)

`@NonNull` / `@Nullable` imports switched from `io.micronaut.core.annotation` → `org.jspecify.annotations` across all main and test source files. Affected:

- `session/src/main/java/io/micronaut/session/InMemorySession.java`
- `session/src/main/java/io/micronaut/session/Session.java`
- `session/src/main/java/io/micronaut/session/SessionConfiguration.java`
- `session/src/main/java/io/micronaut/session/http/CookieHttpSessionIdGenerator.java`
- `session/src/main/java/io/micronaut/session/http/HttpSessionFilterConfiguration.java`
- `session/src/main/java/io/micronaut/session/http/HttpSessionFilterConfigurationProperties.java`
- `session/src/main/java/io/micronaut/session/http/SessionLocaleResolver.java`
- `session/src/test/groovy/io/micronaut/session/docs/ShoppingController.java`
- `session/src/test/groovy/io/micronaut/session/http/SessionBindingSpec.groovy`
- `docs-examples/example-java/src/test/java/io/micronaut/docs/session/ShoppingController.java`

Coding guidelines (`.clinerules/coding.md`, `.github/instructions/coding.instructions.md`) updated to match.

---

### `session/src/main/java/io/micronaut/session/InMemorySessionStore.java`

**Key change:** `ApplicationEventPublisher<? super AbstractSessionEvent>` replaced by four typed publishers — one per event type. Fixes a type-erasure issue that prevented concrete `ApplicationEventListener<SessionCreatedEvent>` beans from receiving events.

```diff
@@ -45,7 +45,11 @@
     private final SessionConfiguration sessionConfiguration;
-    private final ApplicationEventPublisher<? super AbstractSessionEvent> eventPublisher;
+    private final ApplicationEventPublisher<SessionCreatedEvent> sessionCreatedEventPublisher;
+    private final ApplicationEventPublisher<SessionDeletedEvent> sessionDeletedEventPublisher;
+    private final ApplicationEventPublisher<SessionExpiredEvent> sessionExpiredEventPublisher;
+    private final ApplicationEventPublisher<SessionDestroyedEvent> sessionDestroyedEventPublisher;

@@ -58,7 +62,10 @@
     public InMemorySessionStore(
         SessionIdGenerator sessionIdGenerator,
         SessionConfiguration sessionConfiguration,
-        ApplicationEventPublisher<? super AbstractSessionEvent> eventPublisher) {
+        ApplicationEventPublisher<SessionCreatedEvent> sessionCreatedEventPublisher,
+        ApplicationEventPublisher<SessionDeletedEvent> sessionDeletedEventPublisher,
+        ApplicationEventPublisher<SessionExpiredEvent> sessionExpiredEventPublisher,
+        ApplicationEventPublisher<SessionDestroyedEvent> sessionDestroyedEventPublisher) {

@@ -175,9 +175,9 @@
             switch (cause) {
-                case REPLACED -> eventPublisher.publishEvent(new SessionDestroyedEvent(value));
-                case SIZE, EXPIRED -> eventPublisher.publishEvent(new SessionExpiredEvent(value));
-                case EXPLICIT -> eventPublisher.publishEvent(new SessionDeletedEvent(value));
+                case REPLACED -> sessionDestroyedEventPublisher.publishEvent(new SessionDestroyedEvent(value));
+                case SIZE, EXPIRED -> sessionExpiredEventPublisher.publishEvent(new SessionExpiredEvent(value));
+                case EXPLICIT -> sessionDeletedEventPublisher.publishEvent(new SessionDeletedEvent(value));
```

Also removes the `AbstractSessionEvent` import (no longer needed).

---

### `session/src/test/java/io/micronaut/session/SessionEventListenerRegistrationTest.java` _(added)_

New test covering the fix above. Verifies both interface-based (`ApplicationEventListener<SessionCreatedEvent>`) and `@EventListener`-annotated beans receive `SessionCreatedEvent` after `sessionStore.save()`.

---

### `buildSrc/build.gradle`

```diff
 dependencies {
-    implementation "org.graalvm.buildtools.native:org.graalvm.buildtools.native.gradle.plugin:0.10.6"
+    implementation "org.graalvm.buildtools.native:org.graalvm.buildtools.native.gradle.plugin:1.0.0"
+    implementation(providers.gradleProperty("micronaut-build-version").map { "io.micronaut.build.internal:micronaut-kotlin-build-plugins:${it}" }.get())
 }
```

Kotlin build plugins now sourced dynamically from `micronaut-build-version` Gradle property (resolved from the generated `buildSrc/gradle.properties`).

---

### `buildSrc/gradle.properties` _(added)_

Generated file (now git-ignored in mn5):

```
micronaut-build-version=8.0.0-M17
```

---

### `buildSrc/src/main/groovy/io.micronaut.build.internal.session-examples.gradle`

```diff
+    testRuntimeOnly(mnTest.junit.platform.launcher)
```

---

### `session/build.gradle.kts`

```diff
-    testRuntimeOnly(libs.junit.jupiter.engine)
+    testRuntimeOnly(mnTest.junit.jupiter.engine)
```

`junit.jupiter.engine` moved from local `libs` catalog to `mnTest` BOM.

---

### `docs-examples/example-java/build.gradle`

```diff
-    testImplementation libs.junit.jupiter.engine
+    testRuntimeOnly(mnTest.junit.jupiter.engine)
```

Scope corrected: `testImplementation` → `testRuntimeOnly`.

---

### `docs-examples/example-kotlin/build.gradle`

```diff
+import org.jetbrains.kotlin.gradle.dsl.JvmTarget
 plugins {
     id 'io.micronaut.build.internal.session-examples'
-    alias libs.plugins.kotlin.jvm
-    alias libs.plugins.kotlin.kapt
+    id("io.micronaut.build.internal.kotlin-kapt")
 }
 dependencies {
-    testImplementation libs.kotlin.test
+    testImplementation(mn.kotlin.test)
 }
-kotlin {
-    jvmToolchain {
-        languageVersion.set(JavaLanguageVersion.of(17))
-    }
-}
```

Kotlin plugin consolidated to `io.micronaut.build.internal.kotlin-kapt`. Explicit JVM toolchain block removed (handled by convention plugin).

---

### `test-suite-graal/build.gradle`

```diff
+    testRuntimeOnly(mnTest.junit.jupiter.engine)
+    testRuntimeOnly(mnTest.junit.platform.launcher)
```

---

### `docs-examples/example-kotlin/src/test/kotlin/io/micronaut/docs/session/ShoppingControllerTest.kt`

```diff
+            assertNotNull(sessionId)
```

---

### `.sdkmanrc` _(added)_

```
java=25.0.1-graal
```

---

### `.gitignore`

```diff
+# Ignore gradle.properties generated by micronaut-build
+/buildSrc/gradle.properties
+
+# OpenCode files
+.sisyphus/
```

---

### `.clineignore`

```diff
+!build/generated/
+!build/generated/**
```

---

### `.github/renovate.json`

Added rule to block SNAPSHOT versions:

```diff
+    {
+      "matchDatasources": ["maven"],
+      "matchManagers": ["maven", "gradle"],
+      "allowedVersions": "!/.+-SNAPSHOT$/"
+    },
```

---

### GitHub Actions: CI / Workflow Changes

**Common changes across all workflows:**

- Java matrix: `['17', '21']` → `['25']`
- Branch pattern: `'[1-9]+.[0-9]+.x'` → `'[0-9]+.[0-9]+.x'`
- All action refs updated to SHA-pinned versions (supply-chain hardening)
- Added "Remove system JDKs" step before GraalVM setup in all build jobs
- Develocity/secrets now conditionally passed only on non-PR builds: `github.event.pull_request == null && secrets.X || ''`

#### `.github/workflows/gradle.yml`

- Sonatype OSS scan extracted to dedicated `sonatype.yml`
- Build step: `jacocoReport check` → `check jacocoReport`
- Added optional `cleanup.sh` step at end
- `upload-artifact`: v4 → v7

#### `.github/workflows/sonatype.yml` _(added)_

New dedicated workflow for Sonatype vulnerability scanning.

#### `.github/workflows/release.yml`

- JDK `17`+`21` → `25`
- `BETA` flag now checks `env.LATEST_TAG` (fetched via GitHub API) instead of `target_commitish`
- Added `ref: ${{ github.sha }}` on checkout in release upload job
- `download-artifact`: v5 → v8; `upload-artifact`: v4 → v7; `softprops/action-gh-release`: v2.4.1 → v2.6.2

#### `.github/workflows/graalvm-latest.yml`

- Matrix: `['17', '21']` → `['25']`
- `build-matrix` action gains `java-version: '25'`
- `graalvm/pre-build` now passes `nativeTestTask`

#### `.github/workflows/update-gradle-wrapper.yml`

```diff
-      - uses: stefanzweifel/git-auto-commit-action@v5
+      - uses: stefanzweifel/git-auto-commit-action@v7
```

---

### `MAINTAINING.md`

Spelling: `categorised` → `categorized`, `customisations` → `customizations`, `prioritised` → `prioritized` (British → American English).

---

### Binary files (diff not shown)

- `gradle/wrapper/gradle-wrapper.jar` — binary differs
- `gradlew` — differs
- `gradlew.bat` — differs

---

_Report generated by git-branch-diff skill._
