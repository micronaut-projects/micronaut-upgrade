# Diff Report: micronaut-picocli 5.9.x vs 6.0.x

| Property | mn4 (5.9.x) | mn5 (6.0.x) |
|---|---|---|
| Branch | `5.9.x` | `6.0.x` |
| Latest commit | `9f7e0b8` chore: Bump version to 5.9.1-SNAPSHOT | `a1acf77` micronaut = "5.0.0-M22" |
| Project version | 5.9.1-SNAPSHOT | 6.0.0-SNAPSHOT |
| Micronaut | 4.10.4 | 5.0.0-M22 |
| picocli | 4.7.7 | 4.7.7 (unchanged) |
| Gradle | 8.14.3 | 9.4.1 |
| Shared settings plugin | 7.6.4 | 8.0.0-M17 |
| Java matrix | `['17', '21']` | `['25']` |

**Total changes: 33** (4 added, 29 modified, 1 binary skipped)

---

## Dependency Changes

### Third-Party Upgrades

No third-party dependency version changes — picocli remains at `4.7.7`.

### `gradle/libs.versions.toml`

```diff
-micronaut = "4.10.4"
+micronaut = "5.0.0-M22"
 managed-picocli = "4.7.7"

-micronaut-docs = "2.0.0"
-micronaut-test = "4.9.0"
-groovy = "4.0.13"
-spock = "2.3-groovy-4.0"
-kotlin = "1.9.25"
-micronaut-logging = "1.7.1"

 [libraries]
 micronaut-core = { module = 'io.micronaut:micronaut-core-bom', version.ref = 'micronaut' }
 managed-picocli = { module = "info.picocli:picocli", version.ref = "managed-picocli" }
 managed-picocli-codegen = { module = "info.picocli:picocli-codegen", version.ref = "managed-picocli" }

-junit-jupiter-api = { module = "org.junit.jupiter:junit-jupiter-api" }
-junit-jupiter-engine = { module = "org.junit.jupiter:junit-jupiter-engine" }

-[plugins]
-kotlin-jvm = { id = 'org.jetbrains.kotlin.jvm', version.ref = 'kotlin' }
-kotlin-kapt = { id = 'org.jetbrains.kotlin.kapt', version.ref = 'kotlin' }
```

Removed standalone versions for docs, test, groovy, spock, kotlin, and logging — these now come from shared catalogs (`mnTest`, `mnLogging`). JUnit and Kotlin plugin entries removed from local catalog for the same reason.

### `settings.gradle`

```diff
-id 'io.micronaut.build.shared.settings' version '7.6.4'
+id 'io.micronaut.build.shared.settings' version '8.0.0-M17'
```

Also removed `include 'test-suite-kotlin'` — the Kotlin test suite is now included via the shared settings plugin automatically.

### `gradle/wrapper/gradle-wrapper.properties`

```diff
-distributionUrl=https\://services.gradle.org/distributions/gradle-8.14.3-bin.zip
+distributionUrl=https\://services.gradle.org/distributions/gradle-9.4.1-bin.zip
```

---

## Added Files

- `.sdkmanrc` — pins `java=25.0.1-graal` for local dev
- `.github/workflows/sonatype.yml` — dedicated Sonatype OSS Index scan workflow (extracted from `gradle.yml`)
- `buildSrc/gradle.properties` — pins `micronaut-build-version=8.0.0-M17` for the buildSrc classpath
- `buildSrc/src/main/groovy/io.micronaut.build.internal.picocli-testsuite-kotlin.gradle` — new convention plugin for Kotlin test suites:

```groovy
plugins {
    id "io.micronaut.build.internal.picocli-testsuite"
    id "io.micronaut.build.internal.kotlin-kapt"
}
```

---

## Modified Files

### Source changes

#### `picocli/src/main/java/io/micronaut/configuration/picocli/PicocliRunner.java`

The `execute(Class<?>, ApplicationContext, String...)` method visibility changed from **`private`** to **`public`**:

```diff
-private static int execute(Class<?> clazz, ApplicationContext context, String... args) {
+public static int execute(Class<?> clazz, ApplicationContext context, String... args) {
```

This is a **breaking API addition** — it makes the method directly callable, enabling the new test case `testExecuteWithProvidedContextAndWildcardClassForSubcommandOnlyParent`.

### Test changes

#### `picocli/src/test/java/io/micronaut/configuration/picocli/MicronautFactoryCommandTest.java`

JUnit 4 → JUnit 5 migration:

```diff
-import org.junit.Test;
+import org.junit.jupiter.api.Test;
-import static org.junit.Assert.*;
+import static org.junit.jupiter.api.Assertions.assertEquals;
+import static org.junit.jupiter.api.Assertions.assertNotNull;
+import static org.junit.jupiter.api.Assertions.assertNull;
+import static org.junit.jupiter.api.Assertions.assertTrue;
```

#### `picocli/src/test/java/io/micronaut/configuration/picocli/MicronautFactoryTest.java`

JUnit 4 → JUnit 5 migration + assertion argument order fix:

```diff
-import org.junit.Test;
+import org.junit.jupiter.api.Test;
-assertSame("can get singleton A from factory and context", another, a);
-assertEquals("injected value is available", "testValue", a.injectedValue);
+assertSame(another, a, "can get singleton A from factory and context");
+assertEquals("testValue", a.injectedValue, "injected value is available");
```

JUnit 5 assertion parameter order for messages is `(expected, actual, message)` vs JUnit 4's `(message, expected, actual)`.

#### `picocli/src/test/java/io/micronaut/configuration/picocli/PicocliRunnerTest.java`

JUnit 4 → JUnit 5 migration + new test for subcommand-only parent:

```diff
-import org.junit.Before;
-import org.junit.Test;
+import org.junit.jupiter.api.BeforeEach;
+import org.junit.jupiter.api.Test;
-import static org.junit.Assert.*;
+import static org.junit.jupiter.api.Assertions.*;
-@Before
+@BeforeEach
```

New test added `testExecuteWithProvidedContextAndWildcardClassForSubcommandOnlyParent` — exercises the newly public `PicocliRunner.execute()` with a top-level command that delegates to a required subcommand:

```java
@Test
public void testExecuteWithProvidedContextAndWildcardClassForSubcommandOnlyParent() {
    try (ApplicationContext context = ApplicationContext.run(Environment.CLI, Environment.TEST)) {
        int exitCode = PicocliRunner.execute(TopLevelCommand.class, context, "sub");
        assertEquals(0, exitCode);
        assertTrue(RequiredSubcommand.executed);
    }
}
```

### Build changes

#### `picocli/build.gradle`

JUnit added explicitly to the main module tests (previously declared only in test suites):

```diff
+testImplementation(mnTest.junit.jupiter.api)
+testRuntimeOnly(mnTest.junit.jupiter.engine)
+
+tasks.withType(Test).configureEach {
+    useJUnitPlatform()
+}
```

#### `buildSrc/build.gradle`

Added Kotlin build plugins dependency from the shared catalog:

```diff
+repositories {
+    gradlePluginPortal()
+}
 dependencies {
+    implementation(providers.gradleProperty("micronaut-build-version").map { "io.micronaut.build.internal:micronaut-kotlin-build-plugins:${it}" }.get())
 }
```

#### `buildSrc/src/main/groovy/io.micronaut.build.internal.picocli-testsuite.gradle`

```diff
 plugins {
     id "io.micronaut.build.internal.picocli-base"
+    id "io.micronaut.build.internal.java-base"
 }
-testRuntimeOnly libs.junit.jupiter.engine
+testRuntimeOnly mnTest.junit.jupiter.engine
+testRuntimeOnly mnTest.junit.platform.launcher
```

Switched from local catalog (`libs`) to shared catalog (`mnTest`) for JUnit deps.

#### `test-suite/build.gradle`

```diff
-testImplementation(libs.junit.jupiter.api)
+testImplementation(mnTest.junit.jupiter.api)
-testRuntimeOnly("org.junit.platform:junit-platform-launcher")
```

JUnit API moved to shared catalog; `junit-platform-launcher` removed (now provided by convention plugin).

#### `test-suite-kotlin/build.gradle`

Kotlin plugin wiring simplified — replaced explicit plugin aliases with the new convention plugin:

```diff
 plugins {
-    alias libs.plugins.kotlin.jvm
-    alias libs.plugins.kotlin.kapt
-    id 'io.micronaut.build.internal.picocli-testsuite'
+    id 'io.micronaut.build.internal.picocli-testsuite-kotlin'
 }
-testImplementation(libs.junit.jupiter.api)
+testImplementation(mnTest.junit.jupiter.api)
-kotlin {
-    jvmToolchain {
-        languageVersion.set(JavaLanguageVersion.of(17))
-    }
-}
```

Kotlin JVM toolchain version removed — it will now be controlled by the shared settings plugin (Java 25).

### CI / infrastructure changes (identical to other mn5 repos)

- Branch regex: `[1-9]+.[0-9]+.x` → `[0-9]+.[0-9]+.x`
- Java matrix: `['17', '21']` → `['25']`
- All conditions gated on `matrix.java == '17'` → `matrix.java == '25'`
- Fork PR secret isolation via `github.event.pull_request == null && secrets.X || ''`
- SHA-pinned action references throughout
- "Remove system JDKs" step added to all workflows
- `central-sync.yml`: wrapper-validation `v4` → `v6`
- `gradle.yml`: Sonatype scan removed (moved to `sonatype.yml`), `jacocoReport` task order normalised (`check jacocoReport`), cleanup.sh step added
- `release.yml`: LATEST_TAG logic, `upload-artifact` v4→v7.0.1, `download-artifact` v5→v8, `softprops/action-gh-release` v2.4.1→v2.6.2
- `renovate.json`: SNAPSHOT block rule added
- `.gitignore`: `buildSrc/gradle.properties` and `.sisyphus/` added
- `MAINTAINING.md`: British → American English spelling
- `gradlew`/`gradlew.bat`: Gradle 9 wrapper — `CLASSPATH` argument removed

---

_Report generated by git-branch-diff skill._
