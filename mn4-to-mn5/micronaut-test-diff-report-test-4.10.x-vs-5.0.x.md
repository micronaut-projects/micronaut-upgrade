# Diff Report: `4.10.x` vs `5.0.x` (micronaut-test)

**Generated:** 2026-04-22
**Base (A):** `/Users/sdelamo/github/micronaut/mn4/micronaut-test` — branch `4.10.x` @ `48240e00`
**Comparison (B):** `/Users/sdelamo/github/micronaut/mn5/micronaut-test` — branch `5.0.x` @ `1107f75d`

---

## Summary

| Category | Count |
|----------|-------|
| Top-level added entries (only in B) | 28 |
| Top-level removed entries (only in A) | 0 |
| Files modified | 51 |

> Notes:
> - `.agents/` directory (14 skill files) added in B.
> - `.github/instructions/` (`coding.instructions.md`, `docs.instructions.md`) added in B.
> - `test-suite-micronaut-data-jdbc` module removed from `settings.gradle` (the subproject directory itself was not in either checkout scan).
> - `test-core/src/main/java/io/micronaut/test/extensions/AbstractMicronautExtension.java` is large (227 line changes); truncated to first 50 lines.
> - `gradle/wrapper/gradle-wrapper.jar` binary differs; content not shown.

---

## Dependency Changes

### Third-Party Upgrades

- `gradle`: `8.14.3` → `9.4.1` — [Release notes](https://docs.gradle.org/9.4.1/release-notes.html)
- `org.junit.jupiter:junit-jupiter` (managed-junit): `5.14.0` → `6.0.3` — [Release notes](https://junit.org/junit5/docs/current/release-notes/)
- `io.kotest:kotest-*` (managed-kotest): `5.9.1` → `6.1.9` — [Release notes](https://github.com/kotest/kotest/releases/tag/v6.1.9)
- `org.spockframework:spock-*` (managed-spock): `2.3-groovy-4.0` → `2.4-groovy-5.0` — [Release notes](https://github.com/spockframework/spock/releases)
- `org.mockito:mockito-*` (managed-mockito): `5.20.0` → `5.23.0` — [Release notes](https://github.com/mockito/mockito/releases/tag/v5.23.0)
- `io.mockk:mockk` (managed-mockk): `1.13.17` → `1.14.9` — [Release notes](https://github.com/mockk/mockk/releases/tag/1.14.9)
- `io.rest-assured:rest-assured` (managed-rest-assured): `5.5.6` → `6.0.0` — [Release notes](https://github.com/rest-assured/rest-assured/wiki/Downloads)
- `net.bytebuddy:byte-buddy` (managed-bytebuddy): `1.17.7` → `1.18.7` — [Release notes](https://github.com/raphw/byte-buddy/releases/tag/byte-buddy-1.18.7)
- `org.assertj:assertj-core` (managed-assertj): `3.27.4` → `3.27.7` — [Release notes](https://github.com/assertj/assertj/releases/tag/assertj-build-3.27.7)
- `org.graalvm.nativeimage:svm` (graal-svm): `24.2.2` → `25.0.2` — [Release notes](https://github.com/oracle/graal/releases)
- **New:** `org.testcontainers:testcontainers-bom` (managed-testcontainers) `2.0.4` plus split aliases for `testcontainers-postgresql`, `testcontainers-mysql`, `testcontainers-r2dbc`, `testcontainers-junit-jupiter`.

### Micronaut Version Bumps

- `micronaut-platform`: `4.10.0` → `4.10.11`
- `micronaut`: `4.10.7` → `5.0.0-M21`
- `micronaut-data`: `4.13.7` → `4.14.3`
- `micronaut-r2dbc`: `6.1.0` → `7.0.0`
- `micronaut-serde`: `2.15.5` → `3.0.0-M6`
- `micronaut-spring`: `5.11.2` → `5.12.1`
- `micronaut-sql`: `6.3.1` → `7.0.0`
- `micronaut-reactor`: `3.9.0` → `4.0.0-M1`
- `micronaut-gradle-plugin`: `4.5.5` → `4.6.2`
- `micronaut-test` (`4.10.1`): **removed** from versions (this is the project's own version)
- `micronaut-test-resources` (`2.10.1`): **removed** from versions
- `micronaut-logging` (`1.7.1`): **removed** from versions
- `micronaut-docs` (`3.0.0`): **removed** from versions
- `io.micronaut.build.shared.settings` plugin: `7.6.4` → `8.0.0-M17`
- `managed-junit-platform` unified into `managed-junit` (dropped separate platform version)

### Project Version

- `projectVersion`: `4.10.4-SNAPSHOT` → `5.0.0-SNAPSHOT`

### Kotest 5 → JUnit 6 Runner

- `managed-kotest-runner-junit5-jvm` module: `io.kotest:kotest-runner-junit5-jvm` → `io.kotest:kotest-runner-junit6-jvm` (library coordinate changed; version alias kept).

### Notes

- `develocity.predictiveTestSelection.enabled=false` added to `gradle.properties`.
- `settings.gradle` no longer imports `micronaut-test` / `micronaut-test-resources` catalogs.

### `gradle/libs.versions.toml`
```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/gradle/libs.versions.toml	2026-04-22 07:52:42.182330992 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/gradle/libs.versions.toml	2026-04-22 07:52:04.585088490 +0000
@@ -1,37 +1,31 @@
 [versions]
-managed-assertj = "3.27.4"
+managed-assertj = "3.27.7"
 managed-hamcrest = "3.0"
-managed-mockito = "5.20.0"
-managed-mockk = "1.13.17"
-managed-junit = "5.14.0"
-managed-junit-platform = "1.14.0"
-managed-rest-assured = "5.5.6"
-managed-kotest = "5.9.1"
-managed-spock = "2.3-groovy-4.0"
-managed-bytebuddy = "1.17.7"
-
-graal-svm = "24.2.2"
-
-micronaut-platform = "4.10.0"
-micronaut = "4.10.7"
-micronaut-docs = "3.0.0"
-micronaut-test = "4.10.1"
-micronaut-data = "4.13.7"
+managed-mockito = "5.23.0"
+managed-mockk = "1.14.9"
+managed-junit = "6.0.3"
+managed-rest-assured = "6.0.0"
+managed-kotest = "6.1.9"
+managed-spock = "2.4-groovy-5.0"
+managed-bytebuddy = "1.18.7"
+graal-svm = "25.0.2"
+managed-testcontainers = "2.0.4"
+
+micronaut-platform = "4.10.11"
+micronaut = "5.0.0-M21"
+micronaut-data = "4.14.3"
 micronaut-hibernate-validator = "4.8.0"
-micronaut-logging = "1.7.1"
-micronaut-r2dbc = "6.1.0"
-micronaut-serde = "2.15.5"
-micronaut-spring = "5.11.2"
-micronaut-sql = "6.3.1"
-micronaut-reactor = "3.9.0"
-micronaut-test-resources = "2.10.1"
-micronaut-gradle-plugin = "4.5.5"
+micronaut-r2dbc = "7.0.0"
+micronaut-serde = "3.0.0-M6"
+micronaut-spring = "5.12.1"
+micronaut-sql = "7.0.0"
+micronaut-reactor = "4.0.0-M1"
+micronaut-gradle-plugin = "4.6.2"
 
 [libraries]
 # Core
 micronaut-core = { module = 'io.micronaut:micronaut-core-bom', version.ref = 'micronaut' }
 micronaut-platform = { module = 'io.micronaut.platform:micronaut-platform', version.ref = 'micronaut-platform' }
-micronaut-logging = { module = "io.micronaut.logging:micronaut-logging-bom", version.ref = "micronaut-logging" }
 micronaut-data = { module = "io.micronaut.data:micronaut-data-bom", version.ref = "micronaut-data" }
 micronaut-hibernate-validator = { module = "io.micronaut.beanvalidation:micronaut-hibernate-validator-bom", version.ref = "micronaut-hibernate-validator" }
 micronaut-r2dbc = { module = "io.micronaut.r2dbc:micronaut-r2dbc-bom", version.ref = "micronaut-r2dbc" }
@@ -39,8 +33,6 @@
 micronaut-spring = { module = "io.micronaut.spring:micronaut-spring-bom", version.ref = "micronaut-spring" }
 micronaut-sql = { module = "io.micronaut.sql:micronaut-sql-bom", version.ref = "micronaut-sql" }
 micronaut-reactor = { module = 'io.micronaut.reactor:micronaut-reactor-bom', version.ref = "micronaut-reactor" }
-micronaut-test = { module = 'io.micronaut.test:micronaut-test-bom', version.ref = "micronaut-test" }
-micronaut-test-resources = { module = "io.micronaut.testresources:micronaut-test-resources-bom", version.ref = "micronaut-test-resources" }
 
 managed-assertj-core = { module = "org.assertj:assertj-core", version.ref = "managed-assertj" }
 managed-hamcrest = { module = "org.hamcrest:hamcrest", version.ref = "managed-hamcrest" }
@@ -49,29 +41,32 @@
 managed-mockk = { module = "io.mockk:mockk", version.ref = "managed-mockk" }
 # TODO kotest libs should stop be directly managed, boms-kotest should define the versions
 managed-kotest-assertions-core-jvm = { module = "io.kotest:kotest-assertions-core-jvm", version.ref = "managed-kotest" }
-managed-kotest-runner-junit5-jvm = { module = "io.kotest:kotest-runner-junit5-jvm", version.ref = "managed-kotest" }
+managed-kotest-runner-junit5-jvm = { module = "io.kotest:kotest-runner-junit6-jvm", version.ref = "managed-kotest" }
 
 managed-junit-jupiter-engine = { module = "org.junit.jupiter:junit-jupiter-engine", version.ref = "managed-junit" }
 managed-junit-jupiter-params = { module = "org.junit.jupiter:junit-jupiter-params", version.ref = "managed-junit" }
 managed-junit-jupiter-api = { module = "org.junit.jupiter:junit-jupiter-api", version.ref = "managed-junit" }
 managed-junit-vintage-engine = { module = "org.junit.vintage:junit-vintage-engine", version.ref = "managed-junit" }
-junit-testkit = { module = "org.junit.platform:junit-platform-testkit", version.ref = "managed-junit-platform" }
 
-managed-junit-platform-suite-engine = { module = "org.junit.platform:junit-platform-suite-engine", version.ref = "managed-junit-platform" }
-managed-junit-platform-suite = { module = "org.junit.platform:junit-platform-suite", version.ref = "managed-junit-platform" }
-managed-junit-platform-suite-api = { module = "org.junit.platform:junit-platform-suite-api", version.ref = "managed-junit-platform" }
-managed-junit-platform-launcher = { module = "org.junit.platform:junit-platform-launcher", version.ref = "managed-junit-platform" }
-managed-junit-platform-runner = { module = "org.junit.platform:junit-platform-runner", version.ref = "managed-junit-platform" }
-managed-junit-platform-engine = { module = "org.junit.platform:junit-platform-engine", version.ref = "managed-junit-platform" }
-managed-junit-platform-console = { module = "org.junit.platform:junit-platform-console", version.ref = "managed-junit-platform" }
-managed-junit-platform-jfr = { module = "org.junit.platform:junit-platform-jfr", version.ref = "managed-junit-platform" }
-managed-junit-platform-testkit = { module = "org.junit.platform:junit-platform-testkit", version.ref = "managed-junit-platform" }
+managed-junit-platform-suite-engine = { module = "org.junit.platform:junit-platform-suite-engine", version.ref = "managed-junit" }
+managed-junit-platform-suite = { module = "org.junit.platform:junit-platform-suite", version.ref = "managed-junit" }
+managed-junit-platform-suite-api = { module = "org.junit.platform:junit-platform-suite-api", version.ref = "managed-junit" }
+managed-junit-platform-launcher = { module = "org.junit.platform:junit-platform-launcher", version.ref = "managed-junit" }
+managed-junit-platform-engine = { module = "org.junit.platform:junit-platform-engine", version.ref = "managed-junit" }
+managed-junit-platform-console = { module = "org.junit.platform:junit-platform-console", version.ref = "managed-junit" }
+managed-junit-platform-testkit = { module = "org.junit.platform:junit-platform-testkit", version.ref = "managed-junit" }
 
 managed-bytebuddy = { module = "net.bytebuddy:byte-buddy", version.ref = "managed-bytebuddy" }
 managed-bytebuddy-agent = { module = "net.bytebuddy:byte-buddy-agent", version.ref = "managed-bytebuddy" }
 
-testcontainers-junit-jupiter = { module = "org.testcontainers:junit-jupiter"}
+testcontainers-postgresql = { module = "org.testcontainers:testcontainers-postgresql" }
+testcontainers-mysql = { module = "org.testcontainers:testcontainers-mysql" }
+testcontainers-junit-jupiter = { module = "org.testcontainers:testcontainers-junit-jupiter" }
+testcontainers-r2dbc = { module = "org.testcontainers:testcontainers-r2dbc" }
+
 # BOMs
+boms-testcontainers = { module = "org.testcontainers:testcontainers-bom", version.ref = "managed-testcontainers" }
+
 boms-junit = { module = "org.junit:junit-bom", version.ref = "managed-junit" }
 boms-kotest = { module = "io.kotest:kotest-bom", version.ref = "managed-kotest" }
 boms-spock = { module = "org.spockframework:spock-bom", version.ref = "managed-spock" }
@@ -83,3 +78,6 @@
 spock-core = { module = "org.spockframework:spock-core" }
 jakarta-inject-api = { module = "jakarta.inject:jakarta.inject-api" }
 rest-assured = { module = "io.rest-assured:rest-assured" }
+
+kotest-assertions-table = { module = "io.kotest:kotest-assertions-table" }
+
```

### `gradle/wrapper/gradle-wrapper.properties`
```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/gradle/wrapper/gradle-wrapper.properties	2026-04-22 07:52:42.182706621 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/gradle/wrapper/gradle-wrapper.properties	2026-04-22 07:52:04.585525120 +0000
@@ -1,6 +1,6 @@
 distributionBase=GRADLE_USER_HOME
 distributionPath=wrapper/dists
-distributionUrl=https\://services.gradle.org/distributions/gradle-8.14.3-bin.zip
+distributionUrl=https\://services.gradle.org/distributions/gradle-9.4.1-bin.zip
 networkTimeout=10000
 validateDistributionUrl=true
 zipStoreBase=GRADLE_USER_HOME
```

### `gradle.properties`
```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/gradle.properties	2026-04-22 07:52:42.182192199 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/gradle.properties	2026-04-22 07:52:04.584906197 +0000
@@ -1,4 +1,4 @@
-projectVersion=4.10.4-SNAPSHOT
+projectVersion=5.0.0-SNAPSHOT
 projectGroup=io.micronaut.test
 
 title=Micronaut Test
@@ -16,6 +16,8 @@
 org.gradle.caching=true
 org.gradle.jvmargs=-Xmx1g
 org.gradle.parallel=true
+develocity.predictiveTestSelection.enabled=false
+
 
 kotlin.daemon.jvmargs=--add-opens=jdk.compiler/com.sun.tools.javac.api=ALL-UNNAMED\
  --add-opens=jdk.compiler/com.sun.tools.javac.code=ALL-UNNAMED \
```

### `settings.gradle`
```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/settings.gradle	2026-04-22 07:52:42.183036874 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/settings.gradle	2026-04-22 07:52:04.585862248 +0000
@@ -6,7 +6,7 @@
 }
 
 plugins {
-    id("io.micronaut.build.shared.settings") version "7.6.4"
+    id("io.micronaut.build.shared.settings") version "8.0.0-M17"
 }
 
 enableFeaturePreview 'TYPESAFE_PROJECT_ACCESSORS'
@@ -20,8 +20,6 @@
     importMicronautCatalog("micronaut-sql")
     importMicronautCatalog("micronaut-r2dbc")
     importMicronautCatalog("micronaut-reactor")
-    importMicronautCatalog("micronaut-test")
-    importMicronautCatalog("micronaut-test-resources")
     importMicronautCatalog("micronaut-hibernate-validator")
 }
 
@@ -36,5 +34,4 @@
 include "test-rest-assured"
 include 'test-suite-sql-r2dbc'
 include 'test-suite-at-sql-jpa'
-include 'test-suite-micronaut-data-jdbc'
 include 'test-type-pollution'
```

---

## Added Files / Directories (only in B)

- `.agents/` (14 skill files: `agent-md-refactor`, `coding`, `docs`, `gradle`, `skill-creator`)
- `.github/instructions/coding.instructions.md`, `.github/instructions/docs.instructions.md`
- `.github/workflows/.rsync-filter`
- `.github/workflows/sonatype.yml`
- `.github/workflows/update-gradle-wrapper.yml`
- `.sdkmanrc`
- `src/main/docs/guide/breaks.adoc`
- `src/main/docs/guide/kotest5/Concurrency.adoc`
- `test-core/src/main/java/io/micronaut/test/support/sql/SqlScriptStatementSplitter.java`
- `test-core/src/test/java/io/micronaut/test/support/sql/SqlScriptStatementSplitterTest.java`
- `test-junit5/src/test/java/io/micronaut/test/junit5/ApplicationContextArgumentInjectionTest.java`
- `test-junit5/src/test/java/io/micronaut/test/junit5/DisableEnvironmentDeductionTest.java`
- `test-junit5/src/test/java/io/micronaut/test/junit5/DuplicatePropertyNameValidationTest.java`
- `test-junit5/src/test/java/io/micronaut/test/junit5/MicronautJunit5ExtensionValueParameterTest.java`
- `test-junit5/src/test/java/io/micronaut/test/junit5/TestPropertyProviderLifecycleValidationTest.java`
- `test-junit5/src/test/java/io/micronaut/test/junit5/TransactionalDefaultPropertyExplicitTest.java`
- `test-junit5/src/test/java/io/micronaut/test/junit5/TransactionalDefaultPropertyTest.java`
- `test-junit5/src/test/java/io/micronaut/test/junit5/TransactionalPropertyOverrideTest.java`
- `test-kotest5/src/test/kotlin/io/micronaut/test/kotest5/ConcurrentTestsSpec.kt`
- `test-kotest5/src/test/kotlin/io/micronaut/test/kotest5/DisableEnvironmentDeductionTest.kt`
- `test-kotest5/src/test/kotlin/io/micronaut/test/kotest5/TransactionalDefaultPropertyExplicitTest.kt`
- `test-kotest5/src/test/kotlin/io/micronaut/test/kotest5/TransactionalDefaultPropertyTest.kt`
- `test-spock/src/test/groovy/io/micronaut/test/spock/CleanupSpecRunningApplicationSpec.groovy`
- `test-spock/src/test/groovy/io/micronaut/test/spock/DisableEnvironmentDeductionSpec.groovy`
- `test-spock/src/test/groovy/io/micronaut/test/spock/TransactionalDefaultPropertyExplicitSpec.groovy`
- `test-spock/src/test/groovy/io/micronaut/test/spock/TransactionalDefaultPropertySpec.groovy`
- `test-suite-sql-r2dbc/src/test/java/io/micronaut/test/r2dbc/MySQL.java`
- `test-suite-sql-r2dbc/src/test/resources/META-INF/native-image/io.micronaut.test/test-suite-sql-r2dbc/native-image.properties`

## Removed Files / Directories (only in A)

_None._

---

## Modified Files

### `.clineignore`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/.clineignore	2026-04-22 07:52:42.179357588 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/.clineignore	2026-04-22 07:52:04.580721698 +0000
@@ -6,6 +6,8 @@
 */build/
 !build/docs/
 !build/docs/**
+!build/generated/
+!build/generated/**
 
 # === Dependency/Cache directories ===
 .gradle/
```

### `.clinerules/coding.md`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/.clinerules/coding.md	2026-04-22 07:52:42.179502048 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/.clinerules/coding.md	2026-04-22 07:52:04.580879616 +0000
@@ -41,14 +41,16 @@
 
 You SHOULD prefer modern Java idioms: records, pattern matching, sealed interfaces/classes, `var` for local variables.
 You MUST NOT use fully qualified class names unless there is a conflict between 2 class names in different packages.
-You MUST annotate the code with nullability annotations (`io.micronaut.core.annotation.Nullable`, `io.micronaut.core.annotation.NonNull`).
+You MUST annotate the code with nullability annotations (`org.jspecify.annotations.Nullable`, `org.jspecify.annotations.NonNull`).
+You MUST NOT use reflection: Micronaut is a reflection-free framework tailored for integration with GraalVM.
+You MUST use `jakarta.inject` for dependency injection, NOT `javax.inject`.
 
 ## Binary compatibility
 
 Micronaut projects are intended to be used in consumer applications and therefore follow semantic versioning. As a consequence:
 - You MUST NOT break any public facing API without explicit consent
 - You SHOULD run the `./gradlew japiCmp` task to get a report about binary breaking changes
-- You SHOULD reduce the visibility of members for non user-facing APIs.
+- You SHOULD reduce the visibility of members for non-user-facing APIs.
 - You MUST annotate non-user facing APIs with `@io.micronaut.core.annotation.Internal`
 
 ## Implementation Workflow (Required Checklist)
@@ -69,9 +71,9 @@
     - Checkstyle: `./gradlew -q cM`
 
 5) (Optional) If, and only if you have created new files, you SHOULD run
-  - Spotless check: `./gradlew -q spotlessCheck`
-  - If Spotless fails: `./gradlew -q spotlessApply` then re-run `spotlessCheck`
-  - You MUST NOT add new license headers on existing files: only focus on files you have added
+    - Spotless check: `./gradlew -q spotlessCheck`
+    - If Spotless fails: `./gradlew -q spotlessApply` then re-run `spotlessCheck`
+    - You MUST NOT add new license headers on existing files: only focus on files you have added
 
 6) Verify a clean working tree
     - You SHOULD ensure no unrelated changes are pending before proposing changes.
@@ -163,7 +165,7 @@
 
 ## Key Requirements
 
-You MUST confirm all of the following BEFORE using `attempt_completion`:
+You MUST confirm all the following BEFORE using `attempt_completion`:
 
 - Changes compile successfully (affected modules)
 - Targeted tests pass
@@ -174,3 +176,4 @@
 - Working tree is clean (no unrelated diffs)
 
 If ANY item is “no”, you MUST NOT use `attempt_completion`.
+While you SHOULD add new files using `git add`, you MUST NOT commit (`git commit`) files yourself.
```

### `.clinerules/docs.md`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/.clinerules/docs.md	2026-04-22 07:52:42.179571840 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/.clinerules/docs.md	2026-04-22 07:52:04.580964825 +0000
@@ -1,9 +1,9 @@
 ## Brief overview
-- Documentation for the Micronaut modules is primarily written in Asciidoc format, focusing on user guides, API references, and integration examples. The documentation emphasizes clarity, completeness, and practical examples to help developers integrate Micronaut modules effectively. Insights from the codebase show a focus on modular documentation aligned with subprojects, including setup instructions, usage examples, and troubleshooting tips.
+- Documentation for the Micronaut modules is primarily written in AsciiDoc format, focusing on user guides, API references, and integration examples. The documentation emphasizes clarity, completeness, and practical examples to help developers integrate Micronaut modules effectively. Insights from the codebase show a focus on modular documentation aligned with subprojects, including setup instructions, usage examples, and troubleshooting tips.
 - All the files are within `src/main/docs/guide`. In that directory, there is a `toc.yml` file that is used to generate the table of contents and decide which `.adoc` files are to be included.
 
 ## Development workflow
-- Write documentation in Asciidoc: Place source files in the appropriate `src/main/docs` directory.
+- Write documentation in AsciiDoc: Place source files in the appropriate `src/main/docs` directory.
 - Build and assemble the documentation guide: Use `./gradlew docs` from the root directory to generate HTML documentation. Since the output of this task may be huge, ignore the output and check the last process exit code to tell if it works. Otherwise, ask the user. If it works, verify the output for formatting and content accuracy.
 - Once assembled, the guide will be at `build/docs/`.
 - Include examples: Create and reference code examples from the doc-examples/ directory, ensuring they are testable and up-to-date with the latest service versions.
@@ -11,7 +11,7 @@
 - Review and update: Conduct peer reviews for new documentation or changes, ensuring alignment with coding standards and project updates.
 
 ## Documentation best practices
-- Follow Asciidoc conventions: Use consistent headings, lists, code blocks, and admonitions (e.g., NOTE, TIP, WARNING) for better readability.
+- Follow AsciiDoc conventions: Use consistent headings, lists, code blocks, and admonitions (e.g., NOTE, TIP, WARNING) for better readability.
 - Provide comprehensive coverage: Include installation instructions, configuration details, usage examples, error handling, and performance tips for each service.
 - Use practical examples: Incorporate runnable code snippets from doc-examples/ to demonstrate real-world usage, with clear explanations and expected outputs.
 - Ensure accessibility: Use descriptive alt text for images, maintain logical structure, and avoid jargon without explanations.
```

### `.github/renovate.json`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/.github/renovate.json	2026-04-22 07:52:42.180118262 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/.github/renovate.json	2026-04-22 07:52:04.581845500 +0000
@@ -24,6 +24,16 @@
       ]
     },
     {
+      "matchDatasources": [
+        "maven"
+      ],
+      "matchManagers": [
+        "maven",
+        "gradle"
+      ],
+      "allowedVersions": "!/.+-SNAPSHOT$/"
+    },
+    {
       "matchUpdateTypes": [
         "patch"
       ],
```

### `.github/workflows/central-sync.yml`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/.github/workflows/central-sync.yml	2026-04-22 07:52:42.180240763 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/.github/workflows/central-sync.yml	2026-04-22 07:52:04.582044294 +0000
@@ -14,18 +14,22 @@
   central-sync:
     runs-on: ubuntu-latest
     steps:
+      - name: Remove system JDKs
+        run: |
+          sudo rm -rf /usr/lib/jvm/*
+          unset JAVA_HOME
+          export PATH=$(echo "$PATH" | tr ':' '\n' | grep -v '/usr/lib/jvm' | paste -sd:)
       - name: Checkout repository
-        uses: actions/checkout@v5
+        uses: actions/checkout@de0fac2e4500dabe0009e67214ff5f5447ce83dd # v6
         with:
           ref: v${{ github.event.inputs.release_version }}
-      - uses: gradle/actions/wrapper-validation@v4
+      - uses: gradle/actions/wrapper-validation@39e147cb9de83bb9910b8ef8bd7fff0ee20fcd6f # v6
       - name: Set up JDK
-        uses: actions/setup-java@v5
+        uses: actions/setup-java@be666c2fcd27ec809703dec50e508c2fdc7f6654 # v5
         with:
           distribution: 'temurin'
           java-version: |
-            17
-            21
+            25
       - name: Publish to Sonatype OSSRH
         env:
           SONATYPE_USERNAME: ${{ secrets.SONATYPE_USERNAME }}
```

### `.github/workflows/graalvm-dev.yml`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/.github/workflows/graalvm-dev.yml	2026-04-22 07:52:42.180305639 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/.github/workflows/graalvm-dev.yml	2026-04-22 07:52:04.582122128 +0000
@@ -18,9 +18,9 @@
     outputs:
       matrix: ${{ steps.build-matrix.outputs.matrix }}
     steps:
-      - uses: actions/checkout@v5
+      - uses: actions/checkout@de0fac2e4500dabe0009e67214ff5f5447ce83dd # v6
       - name: Build Matrix
-        uses: micronaut-projects/github-actions/graalvm/build-matrix@master
+        uses: micronaut-projects/github-actions/graalvm/build-matrix@300bf6db7c062dcba77c90bb90e475df31b2acab # master
         id: build-matrix
   build:
     needs: build_matrix
@@ -42,15 +42,21 @@
       DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
       DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
     steps:
-      - uses: actions/checkout@v5
+      - name: Remove system JDKs
+        run: |
+          sudo rm -rf /usr/lib/jvm/*
+          unset JAVA_HOME
+          export PATH=$(echo "$PATH" | tr ':' '\n' | grep -v '/usr/lib/jvm' | paste -sd:)
+      - uses: actions/checkout@de0fac2e4500dabe0009e67214ff5f5447ce83dd # v6
       - name: Pre-Build Steps
-        uses: micronaut-projects/github-actions/graalvm/pre-build@master
+        uses: micronaut-projects/github-actions/graalvm/pre-build@300bf6db7c062dcba77c90bb90e475df31b2acab # master
         id: pre-build
         with:
           java: ${{ matrix.java }}
           distribution: ${{ matrix.distribution }}
+          nativeTestTask: ${{ matrix.native_test_task }}
       - name: Build Steps
-        uses: micronaut-projects/github-actions/graalvm/build@master
+        uses: micronaut-projects/github-actions/graalvm/build@300bf6db7c062dcba77c90bb90e475df31b2acab # master
         id: build
         env:
           GH_TOKEN_PUBLIC_REPOS_READONLY: ${{ secrets.GH_TOKEN_PUBLIC_REPOS_READONLY }}
@@ -59,7 +65,7 @@
         with:
           nativeTestTask: ${{ matrix.native_test_task }}
       - name: Post-Build Steps
-        uses: micronaut-projects/github-actions/graalvm/post-build@master
+        uses: micronaut-projects/github-actions/graalvm/post-build@300bf6db7c062dcba77c90bb90e475df31b2acab # master
         id: post-build
         with:
           java: ${{ matrix.java }}
```

### `.github/workflows/graalvm-latest.yml`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/.github/workflows/graalvm-latest.yml	2026-04-22 07:52:42.180359556 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/.github/workflows/graalvm-latest.yml	2026-04-22 07:52:04.582180754 +0000
@@ -8,26 +8,28 @@
   push:
     branches:
       - master
-      - '[1-9]+.[0-9]+.x'
+      - '[0-9]+.[0-9]+.x'
   pull_request:
     branches:
       - master
-      - '[1-9]+.[0-9]+.x'
+      - '[0-9]+.[0-9]+.x'
 jobs:
   build_matrix:
     if: github.repository != 'micronaut-projects/micronaut-project-template'
     runs-on: ubuntu-latest
     env:
-      DEVELOCITY_ACCESS_KEY: ${{ secrets.GRADLE_ENTERPRISE_ACCESS_KEY }}
-      DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
-      DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
+      DEVELOCITY_ACCESS_KEY: ${{ github.event.pull_request == null && secrets.GRADLE_ENTERPRISE_ACCESS_KEY || '' }}
+      DEVELOCITY_CACHE_USERNAME: ${{ github.event.pull_request == null && secrets.GRADLE_ENTERPRISE_CACHE_USERNAME || '' }}
+      DEVELOCITY_CACHE_PASSWORD: ${{ github.event.pull_request == null && secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD || '' }}
     outputs:
       matrix: ${{ steps.build-matrix.outputs.matrix }}
     steps:
-      - uses: actions/checkout@v5
+      - uses: actions/checkout@de0fac2e4500dabe0009e67214ff5f5447ce83dd # v6
       - name: Build Matrix
-        uses: micronaut-projects/github-actions/graalvm/build-matrix@master
+        uses: micronaut-projects/github-actions/graalvm/build-matrix@300bf6db7c062dcba77c90bb90e475df31b2acab # master
         id: build-matrix
+        with:
+          java-version: '25'
   build:
     needs: build_matrix
     if: github.repository != 'micronaut-projects/micronaut-project-template'
@@ -35,31 +37,38 @@
     strategy:
       max-parallel: 6
       matrix:
-        java: ['17', '21']
+        java: ['25']
         native_test_task: ${{ fromJson(needs.build_matrix.outputs.matrix).native_test_task }}
     env:
-      DEVELOCITY_ACCESS_KEY: ${{ secrets.GRADLE_ENTERPRISE_ACCESS_KEY }}
-      DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
-      DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
+      DEVELOCITY_ACCESS_KEY: ${{ github.event.pull_request == null && secrets.GRADLE_ENTERPRISE_ACCESS_KEY || '' }}
+      DEVELOCITY_CACHE_USERNAME: ${{ github.event.pull_request == null && secrets.GRADLE_ENTERPRISE_CACHE_USERNAME || '' }}
+      DEVELOCITY_CACHE_PASSWORD: ${{ github.event.pull_request == null && secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD || '' }}
     steps:
-      - uses: actions/checkout@v5
+      - name: Remove system JDKs
+        run: |
+          sudo rm -rf /usr/lib/jvm/*
+          unset JAVA_HOME
+          export PATH=$(echo "$PATH" | tr ':' '\n' | grep -v '/usr/lib/jvm' | paste -sd:)
+      - uses: actions/checkout@de0fac2e4500dabe0009e67214ff5f5447ce83dd # v6
       - name: Pre-Build Steps
-        uses: micronaut-projects/github-actions/graalvm/pre-build@master
+        uses: micronaut-projects/github-actions/graalvm/pre-build@300bf6db7c062dcba77c90bb90e475df31b2acab # master
         id: pre-build
         with:
           distribution: 'graalvm'
+          gradle-java: '25'
           java: ${{ matrix.java }}
+          nativeTestTask: ${{ matrix.native_test_task }}
       - name: Build Steps
-        uses: micronaut-projects/github-actions/graalvm/build@master
+        uses: micronaut-projects/github-actions/graalvm/build@300bf6db7c062dcba77c90bb90e475df31b2acab # master
         id: build
         env:
-          GH_TOKEN_PUBLIC_REPOS_READONLY: ${{ secrets.GH_TOKEN_PUBLIC_REPOS_READONLY }}
-          GH_USERNAME: ${{ secrets.GH_USERNAME }}
+          GH_TOKEN_PUBLIC_REPOS_READONLY: ${{ github.event.pull_request == null && secrets.GH_TOKEN_PUBLIC_REPOS_READONLY || '' }}
+          GH_USERNAME: ${{ github.event.pull_request == null && secrets.GH_USERNAME || '' }}
           GRAALVM_QUICK_BUILD: true
         with:
           nativeTestTask: ${{ matrix.native_test_task }}
       - name: Post-Build Steps
-        uses: micronaut-projects/github-actions/graalvm/post-build@master
+        uses: micronaut-projects/github-actions/graalvm/post-build@300bf6db7c062dcba77c90bb90e475df31b2acab # master
         id: post-build
         with:
           java: ${{ matrix.java }}
```

### `.github/workflows/gradle.yml`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/.github/workflows/gradle.yml	2026-04-22 07:52:42.180426890 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/.github/workflows/gradle.yml	2026-04-22 07:52:04.582392756 +0000
@@ -8,97 +8,99 @@
   push:
     branches:
       - master
-      - '[1-9]+.[0-9]+.x'
+      - '[0-9]+.[0-9]+.x'
   pull_request:
     branches:
       - master
-      - '[1-9]+.[0-9]+.x'
+      - '[0-9]+.[0-9]+.x'
 jobs:
   build:
     if: github.repository != 'micronaut-projects/micronaut-project-template'
     runs-on: ubuntu-latest
     strategy:
       matrix:
-        java: ['17', '21']
+        java: ['25']
     env:
-      DEVELOCITY_ACCESS_KEY: ${{ secrets.GRADLE_ENTERPRISE_ACCESS_KEY }}
-      DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
-      DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
-      GH_TOKEN_PUBLIC_REPOS_READONLY: ${{ secrets.GH_TOKEN_PUBLIC_REPOS_READONLY }}
-      GH_USERNAME: ${{ secrets.GH_USERNAME }}
+      DEVELOCITY_ACCESS_KEY: ${{ github.event.pull_request == null && secrets.GRADLE_ENTERPRISE_ACCESS_KEY || '' }}
+      DEVELOCITY_CACHE_USERNAME: ${{ github.event.pull_request == null && secrets.GRADLE_ENTERPRISE_CACHE_USERNAME || '' }}
+      DEVELOCITY_CACHE_PASSWORD: ${{ github.event.pull_request == null && secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD || '' }}
+      GH_TOKEN_PUBLIC_REPOS_READONLY: ${{ github.event.pull_request == null && secrets.GH_TOKEN_PUBLIC_REPOS_READONLY || '' }}
+      GH_USERNAME: ${{ github.event.pull_request == null && secrets.GH_USERNAME || '' }}
       TESTCONTAINERS_RYUK_DISABLED: true
-      PREDICTIVE_TEST_SELECTION: "${{ github.event_name == 'pull_request' && 'true' || 'false' }}"
-      SONAR_TOKEN: ${{ secrets.SONAR_TOKEN }}
-      GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
-      OSS_INDEX_USERNAME: ${{ secrets.OSS_INDEX_USERNAME }}
-      OSS_INDEX_PASSWORD: ${{ secrets.OSS_INDEX_PASSWORD }}
+      SONAR_TOKEN: ${{ github.event.pull_request == null && secrets.SONAR_TOKEN || '' }}
+      GITHUB_TOKEN: ${{ github.event.pull_request == null && github.token || '' }}
+      OSS_INDEX_USERNAME: ${{ github.event.pull_request == null && secrets.OSS_INDEX_USERNAME || '' }}
+      OSS_INDEX_PASSWORD: ${{ github.event.pull_request == null && secrets.OSS_INDEX_PASSWORD || '' }}
     steps:
        # https://github.com/actions/virtual-environments/issues/709
+      - name: Remove system JDKs
+        run: |
+          sudo rm -rf /usr/lib/jvm/*
+          unset JAVA_HOME
+          export PATH=$(echo "$PATH" | tr ':' '\n' | grep -v '/usr/lib/jvm' | paste -sd:)
       - name: "🗑 Free disk space"
         run: |
          sudo rm -rf "/usr/local/share/boost"
          sudo rm -rf "$AGENT_TOOLSDIRECTORY"
+         sudo rm -rf "/opt/ghc"
+         sudo rm -rf "/usr/share/dotnet"
+         sudo rm -rf "/usr/local/lib/android"
          sudo apt-get clean
          df -h
 
       - name: "📥 Checkout repository"
-        uses: actions/checkout@v5
+        uses: actions/checkout@de0fac2e4500dabe0009e67214ff5f5447ce83dd # v6
         with:
           fetch-depth: 0
 
       - name: "🔧 Setup GraalVM CE"
-        uses: graalvm/setup-graalvm@v1.3.6
+        uses: graalvm/setup-graalvm@2149f395d36ce12ad4ee5d7f334b26bf081fa555 # v1
         with:
           distribution: 'graalvm'
           java-version: ${{ matrix.java }}
-          github-token: ${{ secrets.GITHUB_TOKEN }}
+          github-token: ${{ github.token }}
 
       - name: "🔧 Setup Gradle"
-        uses: gradle/actions/setup-gradle@v4
+        uses: gradle/actions/setup-gradle@39e147cb9de83bb9910b8ef8bd7fff0ee20fcd6f # v6
 
       - name: "❓ Optional setup step"
         run: |
           [ -f ./setup.sh ] && ./setup.sh || [ ! -f ./setup.sh ]
 
-      - name: "🚔 Sonatype Scan"
-        id: sonatypescan
-        run: |
-          ./gradlew ossIndexAudit --no-parallel --info
-
       - name: "🛠 Build with Gradle"
         id: gradle
         run: |
-          ./gradlew check --no-daemon --continue
+          ./gradlew check jacocoReport --no-daemon --continue
 
       - name: "🔎 Run static analysis"
-        if: env.SONAR_TOKEN != '' && matrix.java == '17'
+        if: env.SONAR_TOKEN != '' && matrix.java == '25'
         run: |
-          ./gradlew sonar
+          ./gradlew sonar --no-parallel --continue
 
       - name: "📊 Publish Test Report"
         if: always()
-        uses: mikepenz/action-junit-report@v5
+        uses: mikepenz/action-junit-report@bccf2e31636835cf0874589931c4116687171386 # v6
         with:
           check_name: Java CI / Test Report (${{ matrix.java }})
           report_paths: '**/build/test-results/test/TEST-*.xml'
           check_retries: 'true'
 
       - name: "📜 Upload binary compatibility check results"
-        if: matrix.java == '17'
-        uses: actions/upload-artifact@65c4c4a1ddee5b72f698fdd19549f0f0fb45cf08 # v4.6.0
+        if: matrix.java == '25'
+        uses: actions/upload-artifact@bbbca2ddaa5d8feaa63e36b76fdaad77386f024f # v7
         with:
           name: binary-compatibility-reports
           path: "**/build/reports/binary-compatibility-*.html"
 
       - name: "📦 Publish to Sonatype Snapshots"
-        if: success() && github.event_name == 'push' && matrix.java == '17'
+        if: success() && github.event_name == 'push' && matrix.java == '25'
         env:
           SONATYPE_USERNAME: ${{ secrets.SONATYPE_USERNAME }}
           SONATYPE_PASSWORD: ${{ secrets.SONATYPE_PASSWORD }}
         run: ./gradlew publishToSonatype docs --no-daemon
 
       - name: "❓ Determine docs target repository"
-        uses: haya14busa/action-cond@v1
+        uses: haya14busa/action-cond@94f77f7a80cd666cb3155084e428254fea4281fd # v1
         id: docs_target
         with:
           cond: ${{ github.repository == 'micronaut-projects/micronaut-core' }}
@@ -106,10 +108,14 @@
           if_false: ${{ github.repository }}
 
       - name: "📑 Publish to Github Pages"
-        if: success() && github.event_name == 'push' && matrix.java == '17'
-        uses: micronaut-projects/github-pages-deploy-action@master
+        if: success() && github.event_name == 'push' && matrix.java == '25'
+        uses: micronaut-projects/github-pages-deploy-action@76d63aafbab7108d74e83be4e5b3b0501382e829 # master
         env:
           TARGET_REPOSITORY: ${{ steps.docs_target.outputs.value }}
           GH_TOKEN: ${{ secrets.GH_TOKEN }}
           BRANCH: gh-pages
           FOLDER: build/docs
+
+      - name: "❓ Optional cleanup step"
+        run: |
+          [ -f ./cleanup.sh ] && ./cleanup.sh || [ ! -f ./cleanup.sh ]
```

### `.github/workflows/publish-snapshot.yml`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/.github/workflows/publish-snapshot.yml	2026-04-22 07:52:42.180496849 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/.github/workflows/publish-snapshot.yml	2026-04-22 07:52:04.582545215 +0000
@@ -10,20 +10,24 @@
     if: github.repository != 'micronaut-projects/micronaut-project-template'
     runs-on: ubuntu-latest
     steps:
-      - uses: actions/checkout@v5
-      - uses: actions/cache@v4
+      - name: Remove system JDKs
+        run: |
+          sudo rm -rf /usr/lib/jvm/*
+          unset JAVA_HOME
+          export PATH=$(echo "$PATH" | tr ':' '\n' | grep -v '/usr/lib/jvm' | paste -sd:)
+      - uses: actions/checkout@de0fac2e4500dabe0009e67214ff5f5447ce83dd # v6
+      - uses: actions/cache@668228422ae6a00e4ad889ee87cd7109ec5666a7 # v5
         with:
           path: ~/.gradle/caches
           key: ${{ runner.os }}-gradle-${{ hashFiles('**/*.gradle') }}
           restore-keys: |
             ${{ runner.os }}-gradle-
       - name: Set up JDK
-        uses: actions/setup-java@v5
+        uses: actions/setup-java@be666c2fcd27ec809703dec50e508c2fdc7f6654 # v5
         with:
           distribution: 'temurin'
           java-version: |
-            17
-            21
+            25
       - name: Publish to Sonatype Snapshots
         if: success()
         env:
```

### `.github/workflows/release.yml`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/.github/workflows/release.yml	2026-04-22 07:52:42.180589767 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/.github/workflows/release.yml	2026-04-22 07:52:04.582662633 +0000
@@ -13,23 +13,27 @@
       artifacts-sha256: ${{ steps.hash.outputs.artifacts-sha256 }} # Computed hashes for build artifacts.
     runs-on: ubuntu-latest
     steps:
+      - name: Remove system JDKs
+        run: |
+          sudo rm -rf /usr/lib/jvm/*
+          unset JAVA_HOME
+          export PATH=$(echo "$PATH" | tr ':' '\n' | grep -v '/usr/lib/jvm' | paste -sd:)
       - name: Checkout repository
-        uses: actions/checkout@v5
+        uses: actions/checkout@de0fac2e4500dabe0009e67214ff5f5447ce83dd # v6
         with:
           token: ${{ secrets.GH_TOKEN }}
-      - uses: gradle/actions/wrapper-validation@v4
+      - uses: gradle/actions/wrapper-validation@39e147cb9de83bb9910b8ef8bd7fff0ee20fcd6f # v6
       - name: Set up JDK
-        uses: actions/setup-java@v5
+        uses: actions/setup-java@be666c2fcd27ec809703dec50e508c2fdc7f6654 # v5
         with:
           distribution: 'temurin'
           java-version: |
-            17
-            21
+            25
       - name: Set the current release version
         id: release_version
         run: echo "release_version=${GITHUB_REF:11}" >> $GITHUB_OUTPUT
       - name: Run pre-release
-        uses: micronaut-projects/github-actions/pre-release@master
+        uses: micronaut-projects/github-actions/pre-release@300bf6db7c062dcba77c90bb90e475df31b2acab # master
         env:
           MICRONAUT_BUILD_EMAIL: ${{ secrets.MICRONAUT_BUILD_EMAIL }}
         with:
@@ -68,13 +72,13 @@
           # Store the hash in a file, which is uploaded as a workflow artifact.
           sha256sum $ARTIFACTS | base64 -w0 > artifacts-sha256
       - name: Upload build artifacts
-        uses: actions/upload-artifact@65c4c4a1ddee5b72f698fdd19549f0f0fb45cf08 # v4.6.0
+        uses: actions/upload-artifact@bbbca2ddaa5d8feaa63e36b76fdaad77386f024f # v7.0.0
         with:
           name: gradle-build-outputs
           path: build/repo/${{ steps.publish.outputs.group }}/*/${{ steps.publish.outputs.version }}/*
           retention-days: 5
       - name: Upload artifacts-sha256
-        uses: actions/upload-artifact@65c4c4a1ddee5b72f698fdd19549f0f0fb45cf08 # v4.6.0
+        uses: actions/upload-artifact@bbbca2ddaa5d8feaa63e36b76fdaad77386f024f # v7.0.0
         with:
           name: artifacts-sha256
           path: artifacts-sha256
@@ -88,12 +92,15 @@
           GH_TOKEN_PUBLIC_REPOS_READONLY: ${{ secrets.GH_TOKEN_PUBLIC_REPOS_READONLY }}
           GH_USERNAME: ${{ secrets.GH_USERNAME }}
       - name: Export Gradle Properties
-        uses: micronaut-projects/github-actions/export-gradle-properties@master
+        uses: micronaut-projects/github-actions/export-gradle-properties@300bf6db7c062dcba77c90bb90e475df31b2acab # master
+      - name: LATEST_TAG
+        run: |
+          echo "LATEST_TAG=$(curl -s -L -H 'Accept: application/vnd.github+json' -H 'X-GitHub-Api-Version: 2022-11-28' https://api.github.com/repos/${{ github.repository }}/releases/latest | jq -r '.tag_name')" >> $GITHUB_ENV
       - name: Publish to Github Pages
         if: success()
-        uses: micronaut-projects/github-pages-deploy-action@master
+        uses: micronaut-projects/github-pages-deploy-action@76d63aafbab7108d74e83be4e5b3b0501382e829 # master
         env:
-          BETA: ${{ !(github.event.release.target_commitish == github.event.repository.default_branch) || contains(steps.release_version.outputs.release_version, 'M') || contains(steps.release_version.outputs.release_version, 'RC') }}
+          BETA: ${{ !(github.event.release.tag_name == env.LATEST_TAG) || github.event.release.draft || github.event.release.prerelease || contains(steps.release_version.outputs.release_version, 'M') || contains(steps.release_version.outputs.release_version, 'RC') }}
           GH_TOKEN: ${{ secrets.GH_TOKEN }}
           BRANCH: gh-pages
           FOLDER: build/docs
@@ -104,7 +111,7 @@
           DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
       - name: Run post-release
         if: success()
-        uses: micronaut-projects/github-actions/post-release@master
+        uses: micronaut-projects/github-actions/post-release@300bf6db7c062dcba77c90bb90e475df31b2acab # master
         env:
           MICRONAUT_BUILD_EMAIL: ${{ secrets.MICRONAUT_BUILD_EMAIL }}
         with:
@@ -117,7 +124,7 @@
       artifacts-sha256: ${{ steps.set-hash.outputs.artifacts-sha256 }}
     steps:
       - name: Download artifacts-sha256
-        uses: actions/download-artifact@634f93cb2916e3fdff6788551b99b062d0335ce0 # v5.0.0
+        uses: actions/download-artifact@3e5f45b2cfb9172054b4087a40e8e0b5a5461e7c # v8.0.1
         with:
           name: artifacts-sha256
       # The SLSA provenance generator expects the hash digest of artifacts to be passed as a job
@@ -136,7 +143,7 @@
       actions: read # To read the workflow path.
       id-token: write # To sign the provenance.
       contents: write # To add assets to a release.
-    uses: slsa-framework/slsa-github-generator/.github/workflows/generator_generic_slsa3.yml@v2.1.0
+    uses: slsa-framework/slsa-github-generator/.github/workflows/generator_generic_slsa3.yml@f7dd8c54c2067bafc12ca7a55595d5ee9b75204a # v2.1.0
     with:
       base64-subjects: "${{ needs.provenance-subject.outputs.artifacts-sha256 }}"
       upload-assets: true # Upload to a new release.
@@ -148,9 +155,11 @@
     if: startsWith(github.ref, 'refs/tags/')
     steps:
       - name: Checkout repository
-        uses: actions/checkout@08c6903cd8c0fde910a37f88322edcfb5dd907a8 # v5.0.0
+        uses: actions/checkout@de0fac2e4500dabe0009e67214ff5f5447ce83dd # v6.0.2
+        with:
+          ref: ${{ github.sha }}
       - name: Download artifacts
-        uses: actions/download-artifact@634f93cb2916e3fdff6788551b99b062d0335ce0 # v5.0.0
+        uses: actions/download-artifact@3e5f45b2cfb9172054b4087a40e8e0b5a5461e7c # v8.0.1
         with:
           name: gradle-build-outputs
           path: build/repo
@@ -162,6 +171,6 @@
       - name: Upload assets
         # Upload the artifacts to the existing release. Note that the SLSA provenance will
         # attest to each artifact file and not the aggregated ZIP file.
-        uses: softprops/action-gh-release@72f2c25fcb47643c292f7107632f7a47c1df5cd8 # v2.3.2
+        uses: softprops/action-gh-release@3bb12739c298aeb8a4eeaf626c5b8d85266b0e65 # v2.6.2
         with:
           files: artifacts.zip
```

### `.gitignore`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/.gitignore	2026-04-22 07:52:42.180651517 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/.gitignore	2026-04-22 07:52:04.582964386 +0000
@@ -5,6 +5,7 @@
 .idea/
 build/
 !build-logic/src/main/java/io/micronaut/build
+!build-logic/src/main/kotlin/io/micronaut/build
 classes/
 out/
 *.db
@@ -33,3 +34,9 @@
 
 # Ignore files generated by test-resources
 **/.micronaut/test-resources/
+
+# Ignore gradle.properties generated by micronaut-build
+/buildSrc/gradle.properties
+
+# OpenCode files
+.sisyphus/
```

### `MAINTAINING.md`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/MAINTAINING.md	2026-04-22 07:52:42.180931729 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/MAINTAINING.md	2026-04-22 07:52:04.583377307 +0000
@@ -2,7 +2,7 @@
 
 ## Triage incoming issues
 
-New issues need to be categorised. At least with one of the following labels:
+New issues need to be categorized. At least with one of the following labels:
 
 * `type: bug`: when something is not working as designed.
 * `type: improvement`: a minor improvement over an existing feature.
@@ -38,7 +38,7 @@
   revisited in the future.
 * `status: next major version`: it is a breaking change and therefore needs to be implemented in the next major version.
 
-There are also a bunch of `relates-to` labels that can be used to further categorise issues. This is helpful in projects
+There are also a bunch of `relates-to` labels that can be used to further categorize issues. This is helpful in projects
 with a lot of issues, or projects where different people work on different parts or modules.
 
 The majority of the issues are defined in the
@@ -48,7 +48,7 @@
 * If they can be beneficial to several repos, send a pull request to the management repo.
 * If they are repo-specific, just go ahead and create them with the GitHub UI.
 
-Finally, issues (especially bugs) should be prioritised with either `priority: high`, `priority: medium` or
+Finally, issues (especially bugs) should be prioritized with either `priority: high`, `priority: medium` or
 `priority: low`. Checkout the
 [Issue Priority Labels](https://github.com/micronaut-projects/micronaut-core/wiki/Issue-Priority-Labels) document for
 guidelines about when to use each of them.
@@ -146,8 +146,8 @@
 The "Java CI" (`gradle.yml`) workflow does have the ability to have an optional setup step, though. If there is a `setup.sh`
 file in the project root, it will be executed before invoking Gradle.
 
-There are projects, such as micronaut-gcp and micronaut-kubernetes, that have made customisations to sync'ed workflows
-because it's absolutely necessary. In those projects, the sync pull requests are manually merged so that the customisations
+There are projects, such as micronaut-gcp and micronaut-kubernetes, that have made customizations to sync'ed workflows
+because it's absolutely necessary. In those projects, the sync pull requests are manually merged so that the customizations
 aren't lost.
 
 Note that it is perfectly possible to have new workflows that aren't part of the sync process.
```

### `buildSrc/build.gradle`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/buildSrc/build.gradle	2026-04-22 07:52:42.181222273 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/buildSrc/build.gradle	2026-04-22 07:52:04.583826103 +0000
@@ -9,4 +9,6 @@
 
 dependencies {
     implementation(libs.micronaut.library.plugin)
+    // Ensure Kotlin Gradle plugin is on buildSrc classpath so convention plugins can apply it without versions
+    implementation(providers.gradleProperty("micronaut-build-version").map { "io.micronaut.build.internal:micronaut-kotlin-build-plugins:${it}" }.get())
 }
```

### `gradle/wrapper/gradle-wrapper.jar`

_Binary file differs._

### `gradlew`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/gradlew	2026-04-22 07:52:42.182829956 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/gradlew	2026-04-22 07:52:04.585656371 +0000
@@ -1,7 +1,7 @@
 #!/bin/sh
 
 #
-# Copyright © 2015-2021 the original authors.
+# Copyright © 2015 the original authors.
 #
 # Licensed under the Apache License, Version 2.0 (the "License");
 # you may not use this file except in compliance with the License.
@@ -57,7 +57,7 @@
 #       Darwin, MinGW, and NonStop.
 #
 #   (3) This script is generated from the Groovy template
-#       https://github.com/gradle/gradle/blob/HEAD/platforms/jvm/plugins-application/src/main/resources/org/gradle/api/internal/plugins/unixStartScript.txt
+#       https://github.com/gradle/gradle/blob/2d6327017519d23b96af35865dc997fcb544fb40/platforms/jvm/plugins-application/src/main/resources/org/gradle/api/internal/plugins/unixStartScript.txt
 #       within the Gradle project.
 #
 #       You can find Gradle at https://github.com/gradle/gradle/.
@@ -114,7 +114,6 @@
   NONSTOP* )        nonstop=true ;;
 esac
 
-CLASSPATH="\\\"\\\""
 
 
 # Determine the Java command to use to start the JVM.
@@ -172,7 +171,6 @@
 # For Cygwin or MSYS, switch paths to Windows format before running java
 if "$cygwin" || "$msys" ; then
     APP_HOME=$( cygpath --path --mixed "$APP_HOME" )
-    CLASSPATH=$( cygpath --path --mixed "$CLASSPATH" )
 
     JAVACMD=$( cygpath --unix "$JAVACMD" )
 
@@ -212,7 +210,6 @@
 
 set -- \
         "-Dorg.gradle.appname=$APP_BASE_NAME" \
-        -classpath "$CLASSPATH" \
         -jar "$APP_HOME/gradle/wrapper/gradle-wrapper.jar" \
         "$@"
 
```

### `gradlew.bat`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/gradlew.bat	2026-04-22 07:52:42.182940582 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/gradlew.bat	2026-04-22 07:52:04.585768789 +0000
@@ -70,11 +70,10 @@
 :execute
 @rem Setup the command line
 
-set CLASSPATH=
 
 
 @rem Execute Gradle
-"%JAVA_EXE%" %DEFAULT_JVM_OPTS% %JAVA_OPTS% %GRADLE_OPTS% "-Dorg.gradle.appname=%APP_BASE_NAME%" -classpath "%CLASSPATH%" -jar "%APP_HOME%\gradle\wrapper\gradle-wrapper.jar" %*
+"%JAVA_EXE%" %DEFAULT_JVM_OPTS% %JAVA_OPTS% %GRADLE_OPTS% "-Dorg.gradle.appname=%APP_BASE_NAME%" -jar "%APP_HOME%\gradle\wrapper\gradle-wrapper.jar" %*
 
 :end
 @rem End local scope for the variables with windows NT shell
```

### `src/main/docs/guide/includes/transaction.adoc`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/src/main/docs/guide/includes/transaction.adoc	2026-04-22 07:52:42.183596463 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/src/main/docs/guide/includes/transaction.adoc	2026-04-22 07:52:04.586508713 +0000
@@ -1,5 +1,7 @@
 When using `@MicronautTest` each `@Test` method will be wrapped in a transaction that will be rolled back when the test finishes. This behaviour can be changed by using the `transactional` and `rollback` properties.
 
+The default transactional behaviour can also be controlled through configuration. Set the `micronaut.test.transactional` property (for example in `application-test.properties` or as a system property) to `false` to disable transactions for all tests that do not explicitly specify the `transactional` member. Alternatively, set `micronaut.test.transactional-default=false` to require tests to opt in with `@MicronautTest(transactional = true)` while still allowing per-test overrides.
+
 To avoid creating a transaction:
 
 ```java
```

### `src/main/docs/guide/junit5/junit5DefiningAdditionalTestSpecificProperties.adoc`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/src/main/docs/guide/junit5/junit5DefiningAdditionalTestSpecificProperties.adoc	2026-04-22 07:52:42.184023676 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/src/main/docs/guide/junit5/junit5DefiningAdditionalTestSpecificProperties.adoc	2026-04-22 07:52:04.586747215 +0000
@@ -32,4 +32,4 @@
 include::{junit5tests}/PropertySourceMapTest.java[]
 ----
 
-NOTE: When using `TestPropertyProvider` your test must be declared with JUnit's `@TestInstance(TestInstance.Lifecycle.PER_CLASS)` annotation.
+NOTE: When using `TestPropertyProvider` your test must use JUnit's `PER_CLASS` test instance lifecycle, for example with `@TestInstance(TestInstance.Lifecycle.PER_CLASS)`. The properties are resolved from the test instance before the Micronaut context starts.
```

### `src/main/docs/guide/kotest5/kotest5MockingCollaborators.adoc`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/src/main/docs/guide/kotest5/kotest5MockingCollaborators.adoc	2026-04-22 07:52:42.185617983 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/src/main/docs/guide/kotest5/kotest5MockingCollaborators.adoc	2026-04-22 07:52:04.588054186 +0000
@@ -8,6 +8,10 @@
 
 The above controller uses the `MathService` to expose a `/math/compute/{number}` endpoint. See the following example for a test that tests interaction with the mock collaborator:
 
+IMPORTANT: Table-driven testing requires new dependency
+
+dependency:kotest-assertions-table[groupId="io.kotest",scope="test"]
+
 .Mocking Collaborators
 [source,kotlin]
 ----
```

### `src/main/docs/guide/kotest5/settingUpKoTest5.adoc`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/src/main/docs/guide/kotest5/settingUpKoTest5.adoc	2026-04-22 07:52:42.186136363 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/src/main/docs/guide/kotest5/settingUpKoTest5.adoc	2026-04-22 07:52:04.588393440 +0000
@@ -5,9 +5,9 @@
 ----
 dependencies {
     kaptTest "io.micronaut:micronaut-inject-java"
-    testImplementation "io.micronaut.test:micronaut-test-kotest5:{version}"
+    testImplementation "io.micronaut.test:micronaut-test-kotest5"
     testImplementation "io.mockk:mockk:{mockkVersion}"
-    testImplementation "io.kotest:kotest-runner-junit5-jvm:{kotestVersion}"
+    testImplementation "io.kotest:kotest-runner-junit6-jvm:{kotestVersion}"
 }
 
 // use JUnit 5 platform
@@ -35,7 +35,7 @@
 </dependency>
 <dependency>
     <groupId>io.kotest</groupId>
-    <artifactId>kotest-runner-junit5-jvm</artifactId>
+    <artifactId>kotest-runner-junit6-jvm</artifactId>
     <version>{kotestVersion}</version>
     <scope>test</scope>
 </dependency>
```

### `src/main/docs/guide/toc.yml`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/src/main/docs/guide/toc.yml	2026-04-22 07:52:42.187667378 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/src/main/docs/guide/toc.yml	2026-04-22 07:52:04.589548201 +0000
@@ -26,8 +26,8 @@
   junit5TestingExternalServers: Testing External Servers
   junit5TestMethodsInjection: Test Methods Injection
 kotest5:
-  title: Testing with Kotest 5
-  settingUpKoTest5: Setting up Kotest 5
+  title: Testing with Kotest
+  settingUpKoTest5: Setting up Kotest
   kotest5BeforeYouBegin: Before You Begin
   kotest5WritingAMicronautTest: Writing a Micronaut Test with Kotest
   kotest5EnvironmentClasspathScanning: Environments, Classpath Scanning etc.
```

### `test-bom/build.gradle`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/test-bom/build.gradle	2026-04-22 07:52:42.187922131 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/test-bom/build.gradle	2026-04-22 07:52:04.589760787 +0000
@@ -9,5 +9,8 @@
 micronautBom {
     suppressions {
         acceptedLibraryRegressions.add("micronaut-test-kotest")
+        acceptedLibraryRegressions.add("junit-platform-runner")
+        acceptedLibraryRegressions.add("junit-platform-jfr")
+        acceptedVersionRegressions.add("junit-platform")
     }
 }
```

### `test-core/build.gradle`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/test-core/build.gradle	2026-04-22 07:52:42.188049091 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/test-core/build.gradle	2026-04-22 07:52:04.589922122 +0000
@@ -13,6 +13,9 @@
     api(mn.micronaut.inject)
 
     implementation(mn.micronaut.context)
+
+    testImplementation(libs.managed.junit.jupiter.api)
+    testRuntimeOnly(libs.managed.junit.jupiter.engine)
 }
 
 jar {
```

### `test-core/src/main/java/io/micronaut/test/annotation/MicronautTestValue.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/test-core/src/main/java/io/micronaut/test/annotation/MicronautTestValue.java	2026-04-22 07:52:42.188676472 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/test-core/src/main/java/io/micronaut/test/annotation/MicronautTestValue.java	2026-04-22 07:52:04.590663712 +0000
@@ -40,6 +40,7 @@
     private final boolean startApplication;
 
     private final boolean resolveParameters;
+    private final boolean deduceEnvironment;
 
     /**
      * Default constructor.
@@ -55,13 +56,15 @@
      * @param transactionMode The transaction mode
      * @param startApplication Whether the start the app
      * @param resolveParameters Whether to resolve parameters to beans
+     * @param deduceEnvironment Whether to deduce additional active environments
      */
     @Creator
     public MicronautTestValue(Class<?> application, String[] environments, String[] packages, String[] propertySources,
                               boolean rollback, boolean transactional, boolean rebuildContext,
                               Class<? extends ApplicationContextBuilder>[] contextBuilder, TransactionMode transactionMode,
                               boolean startApplication,
-                              boolean resolveParameters) {
+                              boolean resolveParameters,
+                              boolean deduceEnvironment) {
         this.application = application;
         this.environments = environments;
         this.packages = packages;
@@ -73,6 +76,7 @@
         this.transactionMode = transactionMode;
         this.startApplication = startApplication;
         this.resolveParameters = resolveParameters;
+        this.deduceEnvironment = deduceEnvironment;
     }
 
     /**
@@ -163,4 +167,11 @@
     public boolean isResolveParameters() {
         return resolveParameters;
     }
+
+    /**
+     * @return Whether to deduce additional active environments
+     */
+    public boolean deduceEnvironment() {
+        return deduceEnvironment;
+    }
 }
```

### `test-core/src/main/java/io/micronaut/test/extensions/AbstractMicronautExtension.java`

_Large file: 119 lines added, 108 lines removed. Showing first 50 diff lines:_

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/test-core/src/main/java/io/micronaut/test/extensions/AbstractMicronautExtension.java	2026-04-22 07:52:42.189627439 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/test-core/src/main/java/io/micronaut/test/extensions/AbstractMicronautExtension.java	2026-04-22 07:52:04.591610888 +0000
@@ -22,14 +22,16 @@
 import io.micronaut.context.ApplicationContext;
 import io.micronaut.context.ApplicationContextBuilder;
 import io.micronaut.context.BeanRegistration;
-import io.micronaut.context.DefaultApplicationContextBuilder;
 import io.micronaut.context.annotation.Property;
-import io.micronaut.context.env.DefaultEnvironment;
+import io.micronaut.context.env.Environment;
 import io.micronaut.context.env.PropertySource;
 import io.micronaut.context.env.PropertySourceLoader;
+import io.micronaut.context.env.PropertySourcesLocator;
+import io.micronaut.core.annotation.AnnotationMetadata;
 import io.micronaut.core.annotation.Nullable;
-import io.micronaut.core.io.ResourceResolver;
-import io.micronaut.core.io.service.ServiceDefinition;
+import io.micronaut.core.io.scan.ClassClassPathResourceLoader;
+import io.micronaut.core.io.scan.ClassPathResourceLoader;
+import io.micronaut.core.io.scan.CombinedClassPathResourceLoader;
 import io.micronaut.core.io.service.SoftServiceLoader;
 import io.micronaut.core.naming.NameUtils;
 import io.micronaut.core.reflect.ClassUtils;
@@ -56,19 +58,17 @@
 import io.micronaut.test.support.sql.TestSqlAnnotationHandler;
 
 import java.io.IOException;
-import java.io.InputStream;
 import java.lang.reflect.AnnotatedElement;
 import java.lang.reflect.Method;
 import java.util.ArrayList;
 import java.util.Collection;
 import java.util.Collections;
 import java.util.HashMap;
+import java.util.HashSet;
 import java.util.LinkedHashMap;
 import java.util.List;
 import java.util.Map;
 import java.util.Optional;
-import java.util.ServiceConfigurationError;
-import java.util.ServiceLoader;
 import java.util.Set;
 
 /**
@@ -82,6 +82,7 @@
     public static final String TEST_ROLLBACK = "micronaut.test.rollback";
     public static final String TEST_TRANSACTIONAL = "micronaut.test.transactional";
     public static final String TEST_TRANSACTION_MODE = "micronaut.test.transaction-mode";
+    public static final String TEST_TRANSACTIONAL_DEFAULT = "micronaut.test.transactional-default";
     public static final String DISABLED_MESSAGE = "Test is not bean. Either the test does not satisfy requirements defined by @Requires or annotation processing is not enabled. If the latter ensure annotation processing is enabled in your IDE.";
... (truncated)
```

### `test-core/src/main/java/io/micronaut/test/support/sql/ConnectionFactoryHandler.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/test-core/src/main/java/io/micronaut/test/support/sql/ConnectionFactoryHandler.java	2026-04-22 07:52:42.190170861 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/test-core/src/main/java/io/micronaut/test/support/sql/ConnectionFactoryHandler.java	2026-04-22 07:52:04.592324229 +0000
@@ -24,6 +24,7 @@
 import jakarta.inject.Singleton;
 import org.slf4j.Logger;
 import org.slf4j.LoggerFactory;
+import reactor.core.publisher.Flux;
 import reactor.core.publisher.Mono;
 
 import java.util.List;
@@ -44,16 +45,23 @@
 
     @Override
     public void handle(@NonNull ConnectionFactory connectionFactory, @NonNull String sql) {
-        List<Long> rowsUpdated = Mono.from(connectionFactory.create())
-            .flatMapMany(c -> {
-                if (LOG.isDebugEnabled()) {
-                    LOG.debug("{}: Executing SQL: {}", connectionFactory, sql);
-                }
-                return c.createStatement(sql).execute();
-            })
-            .flatMap(Result::getRowsUpdated)
-            .collectList()
-            .block();
+        List<String> statements = SqlScriptStatementSplitter.split(sql);
+        if (statements.isEmpty()) {
+            return;
+        }
+        List<Long> rowsUpdated = Mono.usingWhen(
+            connectionFactory.create(),
+            c -> Flux.fromIterable(statements)
+                .concatMap(sqlStatement -> {
+                    if (LOG.isDebugEnabled()) {
+                        LOG.debug("{}: Executing SQL: {}", connectionFactory, sqlStatement);
+                    }
+                    return c.createStatement(sqlStatement).execute();
+                })
+                .flatMap(Result::getRowsUpdated)
+                .collectList(),
+            c -> Mono.from(c.close())
+        ).block();
 
         if (LOG.isDebugEnabled()) {
             LOG.debug("{}: Updated rows: {}", connectionFactory, rowsUpdated);
```

### `test-core/src/main/java/io/micronaut/test/support/sql/DataSourceSqlHandler.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/test-core/src/main/java/io/micronaut/test/support/sql/DataSourceSqlHandler.java	2026-04-22 07:52:42.190279029 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/test-core/src/main/java/io/micronaut/test/support/sql/DataSourceSqlHandler.java	2026-04-22 07:52:04.592428646 +0000
@@ -25,6 +25,8 @@
 
 import javax.sql.DataSource;
 import java.sql.SQLException;
+import java.util.Arrays;
+import java.util.List;
 
 /**
  * Handler for raw {@link DataSource} instances.
@@ -42,13 +44,23 @@
 
     @Override
     public void handle(@NonNull DataSource dataSource, @NonNull String sql) {
+        List<String> statements = SqlScriptStatementSplitter.split(sql);
+        if (statements.isEmpty()) {
+            return;
+        }
         try (var connection = dataSource.getConnection();
              var statement = connection.createStatement()
         ) {
+            for (String sqlStatement : statements) {
+                if (LOG.isDebugEnabled()) {
+                    LOG.debug("{}: Executing SQL: {}", dataSource, sqlStatement);
+                }
+                statement.addBatch(sqlStatement);
+            }
+            int[] rowsUpdated = statement.executeBatch();
             if (LOG.isDebugEnabled()) {
-                LOG.debug("{}: Executing SQL: {}", dataSource, sql);
+                LOG.debug("{}: Updated rows: {}", dataSource, Arrays.toString(rowsUpdated));
             }
-            statement.execute(sql);
         } catch (SQLException sqlException) {
             throw new SqlAnnotationHandlingException(sqlException);
         }
```

### `test-junit5/src/main/java/io/micronaut/test/extensions/junit5/MicronautJunit5Extension.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/test-junit5/src/main/java/io/micronaut/test/extensions/junit5/MicronautJunit5Extension.java	2026-04-22 07:52:42.191996379 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/test-junit5/src/main/java/io/micronaut/test/extensions/junit5/MicronautJunit5Extension.java	2026-04-22 07:52:04.594712252 +0000
@@ -50,6 +50,7 @@
 import org.junit.jupiter.api.extension.ConditionEvaluationResult;
 import org.junit.jupiter.api.extension.ExecutionCondition;
 import org.junit.jupiter.api.extension.ExtensionContext;
+import org.junit.jupiter.api.extension.ExtensionConfigurationException;
 import org.junit.jupiter.api.extension.InvocationInterceptor;
 import org.junit.jupiter.api.extension.ParameterContext;
 import org.junit.jupiter.api.extension.ParameterResolutionException;
@@ -78,16 +79,23 @@
  */
 public class MicronautJunit5Extension extends AbstractMicronautExtension<ExtensionContext> implements BeforeAllCallback, AfterAllCallback, BeforeEachCallback, AfterEachCallback, ExecutionCondition, BeforeTestExecutionCallback, AfterTestExecutionCallback, ParameterResolver, InvocationInterceptor {
     private static final ExtensionContext.Namespace NAMESPACE = ExtensionContext.Namespace.create(MicronautJunit5Extension.class);
+    private static final String TEST_PROPERTY_PROVIDER_LIFECYCLE_MESSAGE = "Tests that implement TestPropertyProvider must use the PER_CLASS test instance lifecycle.";
 
     @Override
     public void beforeAll(ExtensionContext extensionContext) throws Exception {
         final Class<?> testClass = extensionContext.getRequiredTestClass();
+        final TestInstance.Lifecycle testInstanceLifecycle = extensionContext.getTestInstanceLifecycle().orElse(TestInstance.Lifecycle.PER_METHOD);
+        if (TestPropertyProvider.class.isAssignableFrom(testClass)) {
+            if (testInstanceLifecycle != TestInstance.Lifecycle.PER_CLASS) {
+                throw new ExtensionConfigurationException(TEST_PROPERTY_PROVIDER_LIFECYCLE_MESSAGE);
+            }
+            extensionContext.getRequiredTestInstance();
+        }
         MicronautTestValue micronautTestValue = buildMicronautTestValue(testClass);
         beforeClass(extensionContext, testClass, micronautTestValue);
         getStore(extensionContext).put(ApplicationContext.class, applicationContext);
         if (specDefinition != null) {
-            TestInstance ti = AnnotationSupport.findAnnotation(testClass, TestInstance.class).orElse(null);
-            if (ti != null && ti.value() == TestInstance.Lifecycle.PER_CLASS) {
+            if (testInstanceLifecycle == TestInstance.Lifecycle.PER_CLASS) {
                 Object testInstance = extensionContext.getRequiredTestInstance();
                 if (specDefinition instanceof ProxyBeanDefinition<?>) {
                     // Proxy bean is not going to resolve bean definition, we need a small hack
@@ -366,6 +374,10 @@
                 return false;
             }
 
+            if (isApplicationContextParameter(parameterContext)) {
+                return true;
+            }
+
             final Argument<?> argument = getArgument(parameterContext, applicationContext);
             if (argument != null) {
                 if (argument.isAnnotationPresent(Value.class) || argument.isAnnotationPresent(Property.class)) {
@@ -383,15 +395,15 @@
 
     @Override
     public Object resolveParameter(ParameterContext parameterContext, ExtensionContext extensionContext) throws ParameterResolutionException {
+        if (isApplicationContextParameter(parameterContext)) {
+            return applicationContext;
+        }
+
         final Argument<?> argument = getArgument(parameterContext, applicationContext);
         if (argument != null) {
             Optional<String> v = argument.getAnnotationMetadata().stringValue(Value.class);
             if (v.isPresent()) {
-                Optional<String> finalV = v;
-                return applicationContext.getEnvironment().getProperty(v.get(), argument)
-                    .orElseThrow(() ->
-                        new ParameterResolutionException("Unresolvable property specified to @Value: " + finalV.get())
-                    );
+                return resolveValueParameter(parameterContext, argument, v.get());
             } else {
                 v = argument.getAnnotationMetadata().stringValue(Property.class, "name");
                 if (v.isPresent()) {
@@ -409,6 +421,32 @@
         }
     }
 
+    private Object resolveValueParameter(ParameterContext parameterContext, Argument<?> argument, String value) {
+        if (argument.getAnnotationMetadata().hasEvaluatedExpressions()) {
+            Object resolved = argument.getAnnotationMetadata().getValue(Value.class, argument).orElse(null);
+            if (resolved != null || argument.isDeclaredNullable()) {
+                return resolved;
+            }
+            throw new ParameterResolutionException("Unresolvable property specified to @Value: " + value);
+        }
+        BeanDefinition<?> beanDefinition = applicationContext
+            .findBeanDefinition(parameterContext.getDeclaringExecutable().getDeclaringClass())
+            .orElse(null);
+        if (beanDefinition == null) {
+            beanDefinition = specDefinition;
+        }
+        if (beanDefinition != null) {
+            try (DefaultBeanResolutionContext resolutionContext = new DefaultBeanResolutionContext(applicationContext, beanDefinition)) {
+                return resolutionContext.resolvePropertyValue(argument, value, null, true);
+            } catch (RuntimeException e) {
+                throw new ParameterResolutionException("Unresolvable property specified to @Value: " + value, e);
+            }
+        }
+        return applicationContext.resolvePlaceholders(value)
+            .flatMap(resolved -> applicationContext.getConversionService().convert(resolved, argument))
+            .orElseThrow(() -> new ParameterResolutionException("Unresolvable property specified to @Value: " + value));
+    }
+
     /**
      * @param context the current extension context
      * @return the store to use for this extension
@@ -429,7 +467,8 @@
             micronautTest.contextBuilder(),
             micronautTest.transactionMode(),
             micronautTest.startApplication(),
-            micronautTest.resolveParameters());
+            micronautTest.resolveParameters(),
+            micronautTest.deduceEnvironment());
     }
 
     private boolean isNestedTestClass(Class<?> testClass) {
@@ -442,6 +481,10 @@
         });
     }
 
+    private boolean isApplicationContextParameter(ParameterContext parameterContext) {
+        return ApplicationContext.class.isAssignableFrom(parameterContext.getParameter().getType());
+    }
+
     private Argument<?> getArgument(ParameterContext parameterContext, ApplicationContext applicationContext) {
         try {
             final Executable declaringExecutable = parameterContext.getDeclaringExecutable();
```

### `test-junit5/src/main/java/io/micronaut/test/extensions/junit5/annotation/MicronautTest.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/test-junit5/src/main/java/io/micronaut/test/extensions/junit5/annotation/MicronautTest.java	2026-04-22 07:52:42.192173756 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/test-junit5/src/main/java/io/micronaut/test/extensions/junit5/annotation/MicronautTest.java	2026-04-22 07:52:04.594899796 +0000
@@ -116,4 +116,11 @@
      * @return Whether to resolve test method parameters as beans.
      */
     boolean resolveParameters() default true;
+
+    /**
+     * Controls whether Micronaut should deduce additional active environments.
+     *
+     * @return {@code false} to mimic setting {@code MICRONAUT_ENV_DEDUCTION=false}
+     */
+    boolean deduceEnvironment() default true;
 }
```

### `test-junit5/src/main/resources/META-INF/native-image/io.micronaut.test/micronaut-test-junit5/native-image.properties`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/test-junit5/src/main/resources/META-INF/native-image/io.micronaut.test/micronaut-test-junit5/native-image.properties	2026-04-22 07:52:42.192668344 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/test-junit5/src/main/resources/META-INF/native-image/io.micronaut.test/micronaut-test-junit5/native-image.properties	2026-04-22 07:52:04.595551010 +0000
@@ -1,3 +1,2 @@
 Args = --initialize-at-run-time=io.micronaut.test.extensions.junit5.MicronautJunit5Extension \
-       --initialize-at-build-time=org.junit.platform.reporting.open.xml.OpenTestReportGeneratingListener \
-       --initialize-at-build-time=org.junit.platform.launcher.core.HierarchicalOutputDirectoryCreator
+       --initialize-at-build-time=org.junit.jupiter.engine.discovery.MethodSegmentResolver
```

### `test-junit5/src/test/java/io/micronaut/test/junit5/ArgumentInjectionTest.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/test-junit5/src/test/java/io/micronaut/test/junit5/ArgumentInjectionTest.java	2026-04-22 07:52:42.225138373 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/test-junit5/src/test/java/io/micronaut/test/junit5/ArgumentInjectionTest.java	2026-04-22 07:52:04.628327459 +0000
@@ -2,6 +2,7 @@
 package io.micronaut.test.junit5;
 
 import io.micronaut.context.annotation.Property;
+import io.micronaut.context.annotation.Value;
 import io.micronaut.http.client.HttpClient;
 import io.micronaut.http.client.annotation.Client;
 import io.micronaut.test.extensions.junit5.annotation.MicronautTest;
@@ -27,4 +28,14 @@
 
         assertEquals("test", val);
     }
+
+    @Test
+    void testValueArgumentInjected(@Value("${foo.bar}") String val) {
+        assertEquals("test", val);
+    }
+
+    @Test
+    void testExpressionValueArgumentInjected(@Value("#{1 + 1}") Integer val) {
+        assertEquals(2, val);
+    }
 }
```

### `test-kotest5/build.gradle`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/test-kotest5/build.gradle	2026-04-22 07:52:42.231885065 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/test-kotest5/build.gradle	2026-04-22 07:52:04.636889085 +0000
@@ -1,7 +1,6 @@
 plugins {
     id "io.micronaut.build.internal.micronaut-test-module"
-    alias(mn.plugins.kotlin.jvm)
-    alias(mn.plugins.kotlin.kapt)
+    id("io.micronaut.build.internal.kotlin-kapt")
 }
 
 dependencies {
@@ -30,6 +29,7 @@
     testImplementation(mnData.micronaut.data.hibernate.jpa)
     testImplementation(mn.snakeyaml)
     testImplementation(libs.managed.kotest.assertions.core.jvm)
+    testImplementation(libs.kotest.assertions.table)
 
     testRuntimeOnly(mnLogging.logback.classic)
     testRuntimeOnly(mnSql.micronaut.jdbc.tomcat)
@@ -38,17 +38,11 @@
     testRuntimeOnly(testFixtures(projects.micronautTestCore))
 }
 
-kotlin {
-    jvmToolchain {
-        languageVersion.set(JavaLanguageVersion.of(17))
-    }
-}
-
 tasks.named("test") {
     useJUnitPlatform {
         includeEngines("kotest")
     }
     // PTS fails for Kotest because it's not supported, yet.
     // see https://docs.gradle.com/enterprise/predictive-test-selection/#_frameworks_and_languages
-    develocity.predictiveTestSelection.enabled = false
+    // PTS is disabled via develocity.predictiveTestSelection.enabled in gradle.properties
 }
```

### `test-kotest5/src/main/kotlin/io/micronaut/test/extensions/kotest5/MicronautKotest5Context.kt`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/test-kotest5/src/main/kotlin/io/micronaut/test/extensions/kotest5/MicronautKotest5Context.kt	2026-04-22 07:52:42.232382612 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/test-kotest5/src/main/kotlin/io/micronaut/test/extensions/kotest5/MicronautKotest5Context.kt	2026-04-22 07:52:04.637371715 +0000
@@ -17,7 +17,7 @@
 
 import io.kotest.core.spec.Spec
 import io.kotest.core.test.TestCase
-import io.kotest.core.test.TestResult
+import io.kotest.engine.test.TestResult
 import io.micronaut.context.annotation.Property
 import io.micronaut.test.annotation.MicronautTestValue
 import io.micronaut.test.context.TestContext
@@ -65,7 +65,7 @@
     }
 
     fun beforeTest(testCase: TestCase) {
-        val filter = testCase.spec::class.memberFunctions.filter { it.name == testCase.name.testName }
+        val filter = testCase.spec::class.memberFunctions.filter { it.name == testCase.name.name }
         var propertyAnnotations: List<Property>? = emptyList()
         if (filter.isNotEmpty()) {
             propertyAnnotations = filter.first().annotations.filterIsInstance<Property>()
@@ -115,7 +115,7 @@
             testCase.test.javaClass,
             testCase.spec,
             error,
-            testCase.name.testName,
+            testCase.name.name,
             false
         )
     }
```

### `test-kotest5/src/main/kotlin/io/micronaut/test/extensions/kotest5/MicronautKotest5Extension.kt`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/test-kotest5/src/main/kotlin/io/micronaut/test/extensions/kotest5/MicronautKotest5Extension.kt	2026-04-22 07:52:42.232508363 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/test-kotest5/src/main/kotlin/io/micronaut/test/extensions/kotest5/MicronautKotest5Extension.kt	2026-04-22 07:52:04.637477883 +0000
@@ -20,7 +20,7 @@
 import io.kotest.core.listeners.TestListener
 import io.kotest.core.spec.Spec
 import io.kotest.core.test.TestCase
-import io.kotest.core.test.TestResult
+import io.kotest.engine.test.TestResult
 import io.micronaut.aop.InterceptedProxy
 import io.micronaut.test.annotation.MicronautTestValue
 import io.micronaut.test.extensions.kotest5.annotation.MicronautTest
@@ -130,6 +130,7 @@
             micronautTest.transactionMode,
             micronautTest.startApplication,
             false,
+            micronautTest.deduceEnvironment,
         )
     }
 
```

### `test-kotest5/src/main/kotlin/io/micronaut/test/extensions/kotest5/annotation/MicronautTest.kt`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/test-kotest5/src/main/kotlin/io/micronaut/test/extensions/kotest5/annotation/MicronautTest.kt	2026-04-22 07:52:42.232658864 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/test-kotest5/src/main/kotlin/io/micronaut/test/extensions/kotest5/annotation/MicronautTest.kt	2026-04-22 07:52:04.637611593 +0000
@@ -93,4 +93,5 @@
          *
          * @return true if [io.micronaut.runtime.EmbeddedApplication] should be started
          */
-        val startApplication: Boolean = true)
+        val startApplication: Boolean = true,
+        val deduceEnvironment: Boolean = true)
```

### `test-kotest5/src/test/kotlin/io/micronaut/test/kotest5/ProjectConfig.kt`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/test-kotest5/src/test/kotlin/io/micronaut/test/kotest5/ProjectConfig.kt	2026-04-22 07:52:42.234958929 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/test-kotest5/src/test/kotlin/io/micronaut/test/kotest5/ProjectConfig.kt	2026-04-22 07:52:04.639771947 +0000
@@ -6,5 +6,5 @@
 
 @Suppress("unused")
 object ProjectConfig : AbstractProjectConfig() {
-    override fun extensions() = listOf(MicronautKotest5Extension)
+    override val extensions = listOf(MicronautKotest5Extension)
 }
```

### `test-netty-leak/build.gradle.kts`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/test-netty-leak/build.gradle.kts	2026-04-22 07:52:42.237111533 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/test-netty-leak/build.gradle.kts	2026-04-22 07:52:04.641800551 +0000
@@ -24,7 +24,7 @@
     binaryCompatibility {
         enabledAfter("4.10.0")
     }
-    testFramework = TestFramework.JUNIT5
+    testFramework = TestFramework.JUNIT6
 }
 
 tasks.withType(Test::class.java) {
```

### `test-rest-assured/build.gradle`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/test-rest-assured/build.gradle	2026-04-22 07:52:42.238904176 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/test-rest-assured/build.gradle	2026-04-22 07:52:04.644313159 +0000
@@ -27,6 +27,6 @@
     testRuntimeOnly(mnSerde.micronaut.serde.jackson)
 }
 micronautBuild {
-    testFramework = io.micronaut.build.TestFramework.JUNIT5
+    testFramework = io.micronaut.build.TestFramework.JUNIT6
 }
 
```

### `test-spock/src/main/java/io/micronaut/test/extensions/spock/MicronautSpockExtension.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/test-spock/src/main/java/io/micronaut/test/extensions/spock/MicronautSpockExtension.java	2026-04-22 07:52:42.240741569 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/test-spock/src/main/java/io/micronaut/test/extensions/spock/MicronautSpockExtension.java	2026-04-22 07:52:04.646455930 +0000
@@ -46,6 +46,7 @@
 import java.util.Optional;
 import java.util.Queue;
 import java.util.concurrent.ConcurrentLinkedDeque;
+import java.util.concurrent.Callable;
 
 /**
  * Extension for Spock.
@@ -115,11 +116,23 @@
         );
 
         spec.addCleanupSpecInterceptor(invocation -> {
-            afterTestClass(buildContext(invocation, null));
-            afterClass(invocation);
-
-            invocation.proceed();
-            singletonMocks.clear();
+            Throwable primary = captureCleanupSpecFailure(invocation);
+            TestContext testContext = buildContext(invocation, primary);
+            primary = collectCleanupFailure(primary, () -> {
+                afterTestClass(testContext);
+                return null;
+            });
+            primary = collectCleanupFailure(primary, () -> {
+                afterClass(invocation);
+                return null;
+            });
+            primary = collectCleanupFailure(primary, () -> {
+                singletonMocks.clear();
+                return null;
+            });
+            if (primary != null) {
+                throw primary;
+            }
         });
 
         spec.addSetupInterceptor(invocation -> {
@@ -218,12 +231,43 @@
                     micronautTest.contextBuilder(),
                     micronautTest.transactionMode(),
                     micronautTest.startApplication(),
-                    false);
+                    false,
+                    micronautTest.deduceEnvironment());
         } else {
             return null;
         }
     }
 
+    private Throwable captureCleanupSpecFailure(IMethodInvocation invocation) throws Throwable {
+        try {
+            invocation.proceed();
+            return null;
+        } catch (Exception e) {
+            return e;
+        } catch (Error e) {
+            return e;
+        }
+    }
+
+    private Throwable collectCleanupFailure(Throwable primary, Callable<Void> cleanupStep) {
+        try {
+            cleanupStep.call();
+        } catch (Exception e) {
+            return addCleanupFailure(primary, e);
+        } catch (Error e) {
+            return addCleanupFailure(primary, e);
+        }
+        return primary;
+    }
+
+    private Throwable addCleanupFailure(Throwable primary, Throwable cleanupFailure) {
+        if (primary == null) {
+            return cleanupFailure;
+        }
+        primary.addSuppressed(cleanupFailure);
+        return primary;
+    }
+
     private TestContext buildContext(IMethodInvocation invocation, Throwable exception) {
         String displayName;
         if (invocation.getFeature() == null) {
```

### `test-spock/src/main/java/io/micronaut/test/extensions/spock/annotation/MicronautTest.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/test-spock/src/main/java/io/micronaut/test/extensions/spock/annotation/MicronautTest.java	2026-04-22 07:52:42.240876237 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/test-spock/src/main/java/io/micronaut/test/extensions/spock/annotation/MicronautTest.java	2026-04-22 07:52:04.646596348 +0000
@@ -105,4 +105,11 @@
      * @return true if {@link io.micronaut.runtime.EmbeddedApplication} should be started
      */
     boolean startApplication() default true;
+
+    /**
+     * Controls whether Micronaut should deduce additional active environments.
+     *
+     * @return {@code false} to mimic setting {@code MICRONAUT_ENV_DEDUCTION=false}
+     */
+    boolean deduceEnvironment() default true;
 }
```

### `test-spock/src/test/groovy/io/micronaut/test/spock/FixtureWithAnnotationSpec.groovy`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/test-spock/src/test/groovy/io/micronaut/test/spock/FixtureWithAnnotationSpec.groovy	2026-04-22 07:52:42.241733621 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/test-spock/src/test/groovy/io/micronaut/test/spock/FixtureWithAnnotationSpec.groovy	2026-04-22 07:52:04.648161155 +0000
@@ -7,6 +7,10 @@
 import org.spockframework.runtime.model.SpecInfo
 import spock.lang.Specification
 
+import java.lang.reflect.Field
+import java.util.ArrayDeque
+import java.util.Queue
+
 @MicronautTest
 class FixtureWithAnnotationSpec extends Specification {
     static Boolean firstTestPassed = false
@@ -73,4 +77,93 @@
         then:
         1 * invocation.proceed()
     }
+
+    def "CleanupSpec should retain the cleanupSpec failure and suppress teardown failures"() {
+        given:
+        SpecInfo specInfo = new SpecInfo()
+        IMethodInvocation invocation = Mock()
+        RuntimeException cleanupFailure = new RuntimeException("cleanupSpec failed")
+        Exception afterTestClassFailure = new Exception("afterTestClass failed")
+        RuntimeException afterClassFailure = new RuntimeException("afterClass failed")
+        RuntimeException singletonMocksFailure = new RuntimeException("singletonMocks.clear failed")
+        TestMicronautSpockExtension micronautSpockExtension = new TestMicronautSpockExtension(
+                afterTestClassFailure: afterTestClassFailure,
+                afterClassFailure: afterClassFailure
+        )
+        setSingletonMocks(micronautSpockExtension, new ThrowingQueue(failure: singletonMocksFailure))
+
+        when:
+        micronautSpockExtension.visitSpecAnnotation((MicronautTest) null, specInfo)
+        specInfo.cleanupSpecInterceptors[0].intercept(invocation)
+
+        then:
+        RuntimeException e = thrown()
+        e.is(cleanupFailure)
+        e.suppressed as List == [afterTestClassFailure, afterClassFailure, singletonMocksFailure]
+        1 * invocation.proceed() >> { throw cleanupFailure }
+    }
+
+    def "CleanupSpec should throw the first teardown failure when cleanupSpec succeeds"() {
+        given:
+        SpecInfo specInfo = new SpecInfo()
+        IMethodInvocation invocation = Mock()
+        Exception afterTestClassFailure = new Exception("afterTestClass failed")
+        RuntimeException afterClassFailure = new RuntimeException("afterClass failed")
+        RuntimeException singletonMocksFailure = new RuntimeException("singletonMocks.clear failed")
+        TestMicronautSpockExtension micronautSpockExtension = new TestMicronautSpockExtension(
+                afterTestClassFailure: afterTestClassFailure,
+                afterClassFailure: afterClassFailure
+        )
+        setSingletonMocks(micronautSpockExtension, new ThrowingQueue(failure: singletonMocksFailure))
+
+        when:
+        micronautSpockExtension.visitSpecAnnotation((MicronautTest) null, specInfo)
+        specInfo.cleanupSpecInterceptors[0].intercept(invocation)
+
+        then:
+        Exception e = thrown()
+        e.is(afterTestClassFailure)
+        e.suppressed as List == [afterClassFailure, singletonMocksFailure]
+        1 * invocation.proceed()
+    }
+
+    private static void setSingletonMocks(MicronautSpockExtension extension, Queue<Object> singletonMocks) {
+        Field field = MicronautSpockExtension.getDeclaredField("singletonMocks")
+        field.accessible = true
+        field.set(extension, singletonMocks)
+    }
+
+    static class TestMicronautSpockExtension extends MicronautSpockExtension {
+        Throwable afterTestClassFailure
+        Throwable afterClassFailure
+
+        @Override
+        void afterTestClass(io.micronaut.test.context.TestContext testContext) throws Exception {
+            throwFailure(afterTestClassFailure)
+        }
+
+        @Override
+        protected void afterClass(IMethodInvocation context) {
+            throwFailure(afterClassFailure)
+        }
+
+        private static void throwFailure(Throwable failure) throws Exception {
+            if (failure == null) {
+                return
+            }
+            if (failure instanceof Exception) {
+                throw (Exception) failure
+            }
+            throw (Error) failure
+        }
+    }
+
+    static class ThrowingQueue extends ArrayDeque<Object> {
+        RuntimeException failure
+
+        @Override
+        void clear() {
+            throw failure
+        }
+    }
 }
```

### `test-suite-at-sql-jpa/build.gradle.kts`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/test-suite-at-sql-jpa/build.gradle.kts	2026-04-22 07:52:42.244951069 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/test-suite-at-sql-jpa/build.gradle.kts	2026-04-22 07:52:04.651990401 +0000
@@ -21,10 +21,9 @@
     testImplementation(libs.managed.junit.jupiter.api)
     testImplementation(libs.managed.junit.platform.launcher)
     testImplementation(projects.micronautTestJunit5)
-    testImplementation(mnTestResources.testcontainers.postgres)
-    testImplementation(platform(mnTestResources.boms.testcontainers))
+    testImplementation(platform(libs.boms.testcontainers))
     testImplementation(libs.testcontainers.junit.jupiter)
-
+    testImplementation(libs.testcontainers.postgresql)
     testRuntimeOnly(libs.managed.junit.jupiter.engine)
 }
 
```

### `test-suite-at-sql-jpa/src/test/java/example/micronaut/PostgreSQL.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/test-suite-at-sql-jpa/src/test/java/example/micronaut/PostgreSQL.java	2026-04-22 07:52:42.245830870 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/test-suite-at-sql-jpa/src/test/java/example/micronaut/PostgreSQL.java	2026-04-22 07:52:04.652820284 +0000
@@ -1,7 +1,6 @@
 package example.micronaut;
 
 import io.micronaut.core.annotation.NonNull;
-import io.micronaut.test.support.TestPropertyProvider;
 import org.testcontainers.containers.PostgreSQLContainer;
 
 import java.util.Map;
```

### `test-suite-sql-r2dbc/build.gradle.kts`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/test-suite-sql-r2dbc/build.gradle.kts	2026-04-22 07:52:42.248011183 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/test-suite-sql-r2dbc/build.gradle.kts	2026-04-22 07:52:04.654895805 +0000
@@ -2,7 +2,6 @@
 
 plugins {
     id("io.micronaut.minimal.library")
-    id("io.micronaut.test-resources")
     id("io.micronaut.graalvm") // Required to configure Graal for nativeTest
 }
 
@@ -21,26 +20,20 @@
     testImplementation(projects.micronautTestJunit5)
     testImplementation(mnData.micronaut.data.r2dbc)
     testImplementation(mnSerde.micronaut.serde.jackson)
-    testImplementation(platform(mnTestResources.boms.testcontainers))
-    testImplementation(libs.testcontainers.junit.jupiter)
 
+    testImplementation(platform(libs.boms.testcontainers))
+    testImplementation(libs.testcontainers.junit.jupiter)
+    testImplementation(libs.testcontainers.mysql)
+    testImplementation(libs.testcontainers.r2dbc)
+    testRuntimeOnly(mnSql.mysql.connector.j)
     testRuntimeOnly(mnLogging.logback.classic)
     testRuntimeOnly(mnR2dbc.r2dbc.mysql)
     testRuntimeOnly(libs.managed.junit.platform.launcher)
     testRuntimeOnly(mn.micronaut.http.server.netty)
-    testResourcesService(mnSql.mysql.connector.java)
 }
 
 micronaut {
     testRuntime("junit5")
     importMicronautPlatform.set(false)
-    testResources {
-        version.set(libs.versions.micronaut.test.resources)
-        additionalModules.add(R2DBC_MYSQL)
-    }
 }
 
-java {
-    sourceCompatibility = JavaVersion.VERSION_17
-    targetCompatibility = JavaVersion.VERSION_17
-}
```

### `test-suite-sql-r2dbc/src/test/java/io/micronaut/test/r2dbc/MySqlConnectionTest.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/test-suite-sql-r2dbc/src/test/java/io/micronaut/test/r2dbc/MySqlConnectionTest.java	2026-04-22 07:52:42.248470854 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/test-suite-sql-r2dbc/src/test/java/io/micronaut/test/r2dbc/MySqlConnectionTest.java	2026-04-22 07:52:04.655309101 +0000
@@ -3,20 +3,31 @@
 import io.micronaut.context.annotation.Property;
 import io.micronaut.test.annotation.Sql;
 import io.micronaut.test.extensions.junit5.annotation.MicronautTest;
+import io.micronaut.test.support.TestPropertyProvider;
 import io.r2dbc.spi.ConnectionFactory;
 import jakarta.inject.Inject;
+import org.jspecify.annotations.NonNull;
 import org.junit.jupiter.api.Test;
+import org.junit.jupiter.api.TestInstance;
 import org.testcontainers.junit.jupiter.Testcontainers;
 import reactor.core.publisher.Flux;
 
+import java.util.Map;
+
 import static org.junit.jupiter.api.Assertions.assertEquals;
 
 // tag::clazz[]
 @MicronautTest
 @Property(name = "r2dbc.datasources.default.db-type", value = "mysql")
 @Sql(value = {"classpath:create.sql", "classpath:datasource_1_insert.sql"}, resourceType = ConnectionFactory.class)
+@TestInstance(TestInstance.Lifecycle.PER_CLASS)
 @Testcontainers(disabledWithoutDocker = true)
-class MySqlConnectionTest  {
+class MySqlConnectionTest implements TestPropertyProvider {
+    @Override
+    @NonNull
+    public Map<String, String> getProperties() {
+        return MySQL.getProperties();
+    }
 
     @Inject
     ConnectionFactory connectionFactory;
```

### `test-suite-sql-r2dbc/src/test/resources/application-test.properties`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/test-suite-sql-r2dbc/src/test/resources/application-test.properties	2026-04-22 07:52:42.248781815 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/test-suite-sql-r2dbc/src/test/resources/application-test.properties	2026-04-22 07:52:04.655747355 +0000
@@ -1 +1,2 @@
-test-resources.containers.mysql.image-name=mysql:lts
+r2dbc.datasources.default.dialect=MYSQL
+
```

### `test-type-pollution/build.gradle.kts`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-test/test-type-pollution/build.gradle.kts	2026-04-22 07:52:42.249152152 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-test/test-type-pollution/build.gradle.kts	2026-04-22 07:52:04.656035025 +0000
@@ -30,5 +30,5 @@
     binaryCompatibility {
         enabled.set(true)
     }
-    testFramework = TestFramework.JUNIT5
+    testFramework = TestFramework.JUNIT6
 }
```

---

_Report generated by git-branch-diff skill._
