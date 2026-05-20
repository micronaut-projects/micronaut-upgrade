# Diff Report: micronaut-problem-json 3.9.x vs 4.0.x

| Property | mn4 (3.9.x) | mn5 (4.0.x) |
|---|---|---|
| Branch | `3.9.x` | `4.0.x` |
| Latest commit | `9885000` chore: Bump version to 3.9.1-SNAPSHOT | `16030fb` micronaut-logging = "2.0.0-M2" |
| Project version | 3.9.1-SNAPSHOT | 4.0.0-SNAPSHOT |
| Micronaut | 4.10.3 | 5.0.0-M22 |
| micronaut-serde | 2.15.5 | 3.0.0-M6 |
| micronaut-validation | 4.11.0 | 5.0.0-M1 |
| micronaut-logging | 1.7.1 | 2.0.0-M2 |
| kotlin | 1.9.25 | 2.3.20 |
| zalando-problem | 0.27.1 | 0.27.1 (unchanged) |
| Gradle | 8.14.3 | 9.4.1 |
| Shared settings plugin | 7.6.4 | 8.0.0-M17 |
| Java matrix | `['17', '21']` | `['25']` |

**Total changes: 37** (4 added, 32 modified, 1 binary skipped)

---

## Dependency Changes

### Third-Party Upgrades

No third-party library version changes — `org.zalando:problem` remains at `0.27.1`.

Micronaut module upgrades (not third-party):
- micronaut-serde: `2.15.5` → `3.0.0-M6`
- micronaut-validation: `4.11.0` → `5.0.0-M1`
- micronaut-logging: `1.7.1` → `2.0.0-M2`
- kotlin: `1.9.25` → `2.3.20` *(bundled via shared settings, not a standalone third-party dep)*

### `gradle/libs.versions.toml`

```diff
-micronaut = "4.10.3"
-micronaut-docs = '2.0.0'
-micronaut-test = "4.7.0"
-micronaut-serde = "2.15.5"
-micronaut-validation = "4.11.0"
-groovy = "4.0.25"
-kotlin = '1.9.25'
-spock = "2.3-groovy-4.0"
+micronaut = "5.0.0-M22"
+micronaut-serde = "3.0.0-M6"
+micronaut-validation = "5.0.0-M1"
+kotlin = '2.3.20'

-micronaut-logging = "1.7.1"
+micronaut-logging = "2.0.0-M2"

-junit-api = { module = "org.junit.jupiter:junit-jupiter-api" }
-junit-engine = { module = "org.junit.jupiter:junit-jupiter-engine" }
```

`micronaut-docs`, `micronaut-test`, `groovy`, `spock` versions removed — now provided by shared catalogs. JUnit entries removed from local catalog (moved to `mnTest` shared catalog).

### `gradle/wrapper/gradle-wrapper.properties`

```diff
-distributionUrl=https\://services.gradle.org/distributions/gradle-8.14.3-bin.zip
+distributionUrl=https\://services.gradle.org/distributions/gradle-9.4.1-bin.zip
```

### `settings.gradle`

```diff
-id("io.micronaut.build.shared.settings") version "7.6.4"
+id("io.micronaut.build.shared.settings") version "8.0.0-M17"
```

---

## Added Files

- `.sdkmanrc` — pins `java=25.0.1-graal`
- `.github/workflows/sonatype.yml` — dedicated Sonatype OSS Index scan (extracted from `gradle.yml`)
- `buildSrc/gradle.properties` — pins `micronaut-build-version=8.0.0-M17`
- `buildSrc/src/main/groovy/io.micronaut.build.internal.problem-json-tests-junit.gradle` — new JUnit convention plugin:

```groovy
plugins {
    id("io.micronaut.build.internal.problem-json-tests")
}
dependencies {
    testImplementation(mnTest.junit.jupiter.api)
    testRuntimeOnly(mnTest.junit.jupiter.engine)
    testImplementation mnTest.micronaut.test.junit5
}
```

---

## Modified Files

### Source changes — JSpecify migration

All 5 source files and 4 test files migrate `@NonNull`/`@Nullable` from `io.micronaut.core.annotation` to `org.jspecify.annotations`:

| File | Annotations migrated |
|---|---|
| `ProblemErrorResponseProcessor.java` | `@NonNull` |
| `ProblemJsonErrorResponseBodyProvider.java` | `@NonNull` |
| `violations/ConstraintViolationThrowableProblem.java` | `@NonNull`, `@Nullable` |
| `violations/ProblemConstraintViolationExceptionHandler.java` | `@NonNull` |
| `violations/Violation.java` | `@NonNull` |
| `test/.../ConfigurationFixture.groovy` | `@NonNull`, `@Nullable` |
| `test/.../ConstraintViolationProblemSpec.groovy` | `@NonNull`, `@Nullable` |
| `test/.../DataLeakageOverrideSpec.groovy` | `@NonNull` |
| `test/.../ProblemErrorResponseProcessorReplacement.java` | `@NonNull` |
| `test-suite-serde-java/.../ProblemSerdeTest.java` | `@NonNull` |

### Test fix — `ConfigurationFixture.groovy`

Minor fix: `specName` variable explicitly declared before use:

```diff
+String specName = getSpecName()
 if (specName) {
```

### Build changes

#### `problem-json/build.gradle.kts`

JUnit runtime dep moved from local catalog to shared catalog:

```diff
-testRuntimeOnly(libs.junit.engine)
+testRuntimeOnly(mnTest.junit.jupiter.engine)
```

#### `buildSrc/src/main/groovy/io.micronaut.build.internal.problem-json-tests.gradle`

Base convention plugin gained `java-library`, a `mavenCentral()` repo, and JUnit Platform Suite runtime dep:

```diff
 plugins {
     id("io.micronaut.build.internal.problem-json-base")
+    id "java-library"
+}
+repositories {
+    mavenCentral()
+}
+dependencies {
+    testRuntimeOnly(mnTest.junit.platform.suite)
 }
```

#### `test-suite/build.gradle`, `test-suite-kotlin/build.gradle`, `test-suite-serde-java/build.gradle`

All three test suites switch from `problem-json-tests` to `problem-json-tests-junit` convention plugin, and remove inline JUnit declarations (now handled by the plugin):

```diff
-id("io.micronaut.build.internal.problem-json-tests")
+id("io.micronaut.build.internal.problem-json-tests-junit")

-testImplementation libs.junit.api
-testImplementation mnTest.micronaut.test.junit5
-testRuntimeOnly libs.junit.engine
```

`test-suite-kotlin` additionally gains `io.micronaut.build.internal.kotlin-base` plugin and drops the inline `kotlin.jvmToolchain { languageVersion.set(JavaLanguageVersion.of(17)) }` block (Java version now controlled by shared settings).

### CI / infrastructure changes (identical to other mn5 repos)

- Branch regex: `[1-9]+.[0-9]+.x` → `[0-9]+.[0-9]+.x`
- Java matrix: `['17', '21']` → `['25']`
- Fork PR secret isolation via `github.event.pull_request == null && secrets.X || ''`
- SHA-pinned action references throughout
- "Remove system JDKs" step added to all workflows
- Sonatype scan extracted from `gradle.yml` → `sonatype.yml`
- `gradle.yml`: `check jacocoReport` task order, cleanup.sh step, extended disk cleanup
- `release.yml`: LATEST_TAG logic, updated artifact action SHAs, `ref: ${{ github.sha }}` on checkout
- `renovate.json`: SNAPSHOT block rule added
- `.gitignore`: `buildSrc/gradle.properties`, `.sisyphus/` added
- `.clineignore`: `!build/generated/**` added
- `MAINTAINING.md`: British → American English spelling
- `gradlew`/`gradlew.bat`: Gradle 9 wrapper — `CLASSPATH` argument removed

---

_Report generated by git-branch-diff skill._
