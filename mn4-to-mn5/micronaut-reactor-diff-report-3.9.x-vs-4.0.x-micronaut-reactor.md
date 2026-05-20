# Diff Report: `3.9.x` vs `4.0.x`

**Generated:** 2026-04-16
**Base (A):** `mn4/micronaut-reactor` — branch `3.9.x` @ `bcba818a` — _chore: Bump version to 3.9.2-SNAPSHOT_
**Comparison (B):** `mn5/micronaut-reactor` — branch `4.0.x` @ `0b94d7ec` — _chore: Bump version to 4.0.0-SNAPSHOT_

---

## Summary

| Category | Count |
|----------|-------|
| Files added (only in B) | 3 |
| Files removed (only in A) | 0 |
| Files modified | 35 |
| Binary files (skipped) | 2 (`gradle-wrapper.jar`, `gradlew`) |
| **Total** | **38** |

---

## Dependency Changes

### `gradle/libs.versions.toml`

```diff
-micronaut = "4.10.3"
-micronaut-docs = "2.0.0"
-micronaut-test = "4.9.0"
-groovy = "4.0.25"
-spock = "2.3-groovy-4.0"
-micronaut-logging = "1.7.1"
-micronaut-serde = "2.15.4"
-micronaut-tracing = "7.1.4"
-micronaut-validation = "4.11.0"
-micronaut-platform = "4.8.3"
+micronaut = "5.0.0-M22"
+micronaut-serde = "3.0.0-M6"
+micronaut-tracing = "8.0.0-M1"
+micronaut-validation = "5.0.0-M1"
+micronaut-platform = "4.10.3"

-rxjava3 = "3.1.11"
+rxjava3 = "3.1.12"

-managed-reactor-bom = "2024.0.11"
-managed-micrometer-context-propagation = "1.1.3"
+managed-reactor-bom = "2025.0.5"
+managed-micrometer-context-propagation = "1.2.1"

-micronaut-gradle-plugin = "4.5.5"
+micronaut-gradle-plugin = "4.6.2"

# Library entry removed:
-micronaut-test = { module = "io.micronaut.test:micronaut-test-bom", ... }
```

> ⚠️ `micronaut-docs`, `micronaut-test`, `groovy`, `spock`, `micronaut-logging` removed from versions — likely now sourced from the shared settings plugin. Reactor BOM jumps from `2024.0.11` → `2025.0.5`.

### `gradle.properties`

```diff
-projectVersion=3.9.2-SNAPSHOT
+projectVersion=4.0.0-SNAPSHOT
```

### `settings.gradle`

```diff
-id("io.micronaut.build.shared.settings") version "7.6.4"
+id("io.micronaut.build.shared.settings") version "8.0.0-M17"
```

### `gradle/wrapper/gradle-wrapper.properties`

```diff
-distributionUrl=...gradle-8.14.3-bin.zip
+distributionUrl=...gradle-9.4.1-bin.zip
```

---

## Added Files

- `.agents/` _(directory)_
- `.github/workflows/sonatype.yml` _(new Sonatype publishing workflow)_
- `.sdkmanrc` _(SDK version pinning)_

---

## Removed Files

_(none)_

---

## Modified Files

### Source Code

All 14 source files have the same single change: **JSpecify migration**.

`io.micronaut.core.annotation.NonNull` / `Nullable` → `org.jspecify.annotations.NonNull` / `Nullable`

Affected files:

- `reactor/src/main/java/io/micronaut/reactor/config/ReactorConfiguration.java`
- `reactor-http-client/src/main/java/io/micronaut/reactor/http/client/BridgedReactorHttpClient.java`
- `reactor-http-client/src/main/java/io/micronaut/reactor/http/client/BridgedReactorStreamingHttpClient.java`
- `reactor-http-client/src/main/java/io/micronaut/reactor/http/client/ReactorHttpClient.java`
- `reactor-http-client/src/main/java/io/micronaut/reactor/http/client/ReactorHttpClientFactory.java`
- `reactor-http-client/src/main/java/io/micronaut/reactor/http/client/ReactorSseClient.java`
- `reactor-http-client/src/main/java/io/micronaut/reactor/http/client/ReactorStreamingHttpClient.java`
- `reactor-http-client/src/main/java/io/micronaut/reactor/http/client/proxy/BridgedReactorProxyHttpClient.java`
- `reactor-http-client/src/main/java/io/micronaut/reactor/http/client/proxy/ReactorProxyHttpClient.java`
- `reactor-http-client/src/main/java/io/micronaut/reactor/http/client/proxy/ReactorProxyHttpClientFactory.java`
- `reactor-http-client/src/main/java/io/micronaut/reactor/http/client/sse/BridgedReactorSseClient.java`
- `reactor-http-client/src/main/java/io/micronaut/reactor/http/client/sse/ReactorSseClientFactory.java`
- `reactor-http-client/src/main/java/io/micronaut/reactor/http/client/websocket/ReactorWebSocketClient.java`
- `reactor-http-client/src/main/java/io/micronaut/reactor/http/client/websocket/ReactorWebSocketClientFactory.java`

---

### Build Scripts

#### `buildSrc/src/main/groovy/io.micronaut.build.internal.reactor-test-suite.gradle`

```diff
+dependencies {
+    testRuntimeOnly(mnTest.junit.platform.suite)
+}
+java {
+    sourceCompatibility = JavaVersion.VERSION_21
+    targetCompatibility = JavaVersion.VERSION_21
+}
```

> ⚠️ Notable: test suites now explicitly set Java 21 source/target compatibility and add JUnit Platform Suite as a test runtime dependency.

---

### Tests

#### `reactor-http-client/src/test/groovy/io/micronaut/reactor/http/client/StreamSpec.groovy`

```diff
-import io.micronaut.core.annotation.Nullable
+import org.jspecify.annotations.Nullable
```

#### `tests/micrometer-propagation/src/test/groovy/io/micronaut/context/propagation/MyTracingInterceptor.java`

```diff
-import org.reactivestreams.Publisher;
+import org.jspecify.annotations.Nullable;

-try (PropagatedContext.Scope ignore = PropagatedContext.getOrEmpty()
-    .plus(new TracePropagatedContext(trace))
-    .propagate()) {
-    PropagatedContext propagatedContext = PropagatedContext.get();
-    // switch on resultType...
-}
+PropagatedContext propagatedContext = PropagatedContext.getOrEmpty()
+    .plus(new TracePropagatedContext(trace));
+return propagatedContext.propagate(() -> interceptWithinContext(context, propagatedContext));

+private @Nullable Object interceptWithinContext(...) {
+    // switch on resultType (extracted to private method)
+}
```

> ⚠️ Notable: context propagation refactored from try-with-resources `Scope` to `propagate(Callable)` lambda pattern. The intercept logic extracted into a separate private method.

#### `tests/simple-propagation/src/test/groovy/io/micronaut/context/propagation/MyTracingInterceptor.java`

```diff
-try (PropagatedContext.Scope ignore = PropagatedContext.getOrEmpty()
-    .plus(new TracePropagatedContext(trace))
-    .propagate()) {
-    PropagatedContext propagatedContext = PropagatedContext.get();
-    // switch...
-}
+PropagatedContext propagatedContext = PropagatedContext.getOrEmpty()
+    .plus(new TracePropagatedContext(trace));
+return propagatedContext.propagate(() -> {
+    // switch...
+});
```

> Same `propagate(Callable)` migration as the micrometer variant.

---

### CI / Workflows

#### Key changes across all workflow files

- All GitHub Actions pinned to **commit SHAs** (supply-chain security hardening) — same pattern as micronaut-rss.
- Java matrix changed from `['17', '21']` → `['25']` in `gradle.yml`, `graalvm-latest.yml`, `central-sync.yml`, `release.yml`, `publish-snapshot.yml`.
- Branch trigger pattern changed from `'[1-9]+.[0-9]+.x'` → `'[0-9]+.[0-9]+.x'` in `gradle.yml` and `graalvm-latest.yml` (supports `4.0.x` which starts with a digit, not `[1-9]+`).
- Develocity/secret env vars scoped away from fork PRs (`github.event.pull_request == null && secrets.X || ''`).
- `graalvm-dev.yml` and `graalvm-latest.yml`: added JVM cleanup step (`sudo rm -rf /usr/lib/jvm/*`) before checkout.
- `graalvm-dev.yml`: `nativeTestTask` now passed explicitly to `pre-build` step.
- `graalvm-latest.yml`: added `gradle-java: '25'` and `nativeTestTask` to `pre-build` inputs.
- `gradle.yml`: removed Sonatype OSS Index audit step; added optional `cleanup.sh` step at end; Gradle actions `v4` → `v6`; `graalvm/setup-graalvm` `v1.4.1` → `v1` (SHA-pinned).
- `release.yml`: `BETA` flag logic improved — now checks `env.LATEST_TAG` + `draft`/`prerelease` flags instead of just `target_commitish == default_branch`; `LATEST_TAG` step added.
- `publish-snapshot.yml`: added JVM cleanup step.

#### `.github/renovate.json`

```diff
+{
+  "matchDatasources": ["maven"],
+  "matchManagers": ["maven", "gradle"],
+  "allowedVersions": "!/.+-SNAPSHOT$/"
+},
```

---

### Tooling / Config

#### `.gitignore`

```diff
+/buildSrc/gradle.properties
+.sisyphus/
```

#### `.clineignore`

```diff
+!build/generated/
+!build/generated/**
```

#### `.clinerules/coding.md` and `.github/instructions/coding.instructions.md`

```diff
-nullability annotations (`io.micronaut.core.annotation.Nullable`, `io.micronaut.core.annotation.NonNull`)
+nullability annotations (`org.jspecify.annotations.Nullable`, `org.jspecify.annotations.NonNull`)
```

#### `MAINTAINING.md`

British → American English spelling (`categorised`, `prioritised`, `customisations` → American equivalents).

---

## Key Themes

1. **JSpecify migration** — identical to micronaut-rss: all `io.micronaut.core.annotation.{NonNull,Nullable}` replaced with `org.jspecify.annotations.*` across all source and test files.
2. **Micronaut 5 milestone** — core `5.0.0-M22`, tracing `8.0.0-M1`, serde `3.0.0-M6`, validation `5.0.0-M1`.
3. **Reactor BOM 2025.0.5** — up from `2024.0.11`; micrometer-context-propagation `1.2.1` (from `1.1.3`).
4. **Gradle 9.4.1** — up from 8.14.3.
5. **Java 25 CI** — drops Java 17 and 21 in the matrix.
6. **Branch regex fix** — trigger pattern `[1-9]+` → `[0-9]+` to support `4.0.x`.
7. **Context propagation API change** — `PropagatedContext.Scope` try-with-resources pattern replaced by `propagate(Callable)` in both `MyTracingInterceptor` variants.
8. **Test suite build config** — explicit Java 21 source/target + JUnit Platform Suite runtime dep added to `reactor-test-suite.gradle`.
9. **Supply-chain hardening** — all Actions pinned to commit SHAs; secrets blocked on fork PRs.

---

_Report generated by git-branch-diff skill._
