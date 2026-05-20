# Diff Report: `5.12.x` vs `6.0.x`

**Generated:** 2026-04-22
**Base (A):** `/Users/sdelamo/github/micronaut/mn4/micronaut-spring` — branch `5.12.x` @ `da30421f`
**Comparison (B):** `/Users/sdelamo/github/micronaut/mn5/micronaut-spring` — branch `6.0.x` @ `95b439b9`

---

## Summary

| Category | Count |
|----------|-------|
| Files added (only in B) | 23 |
| Files removed (only in A) | 6 |
| Files modified | 66 |
| Total changes | 95 |

> Notes:
> - Six test files under `test-suite/src/test/groovy/io/micronaut/spring/tx/` in A were relocated to `test-suite/src/test/java/io/micronaut/spring/tx/` in B (counted as both removed and added).
> - `.agents/` directory added in B contains 14 new skill reference files.
> - `gradle/wrapper/gradle-wrapper.jar` is binary and differs; content not shown.

---

## Dependency Changes

### Third-Party Upgrades

- `gradle`: `8.14.3` → `9.4.1` — [Release notes](https://docs.gradle.org/9.4.1/release-notes.html)
- `org.springframework.boot:spring-boot` (managed-spring-boot): `3.5.11` → `4.0.5` — [Release notes](https://github.com/spring-projects/spring-boot/releases/tag/v4.0.5)
- `org.springframework:spring-core` (managed-spring): `6.2.16` → `7.0.7` — [Release notes](https://github.com/spring-projects/spring-framework/releases/tag/v7.0.7)

### Micronaut Version Bumps

- `micronaut`: `4.10.15` → `5.0.0-M23`
- `micronaut-sql`: `6.3.3` → `7.0.1-M2`
- `micronaut-cache`: `5.3.0` → `6.0.0-M3`
- `micronaut-views`: `5.9.0` → `6.0.0-M1`
- `micronaut-validation`: `4.12.0` → `5.0.0-M2`
- `micronaut-servlet`: `5.6.0` → `6.0.0-M3`
- `micronaut-shared-settings`: `7.6.6` → `8.0.0-M17`
- `micronaut-docs` (`3.0.0`): **removed** from versions
- `micronaut-test` (`4.10.2`): **removed** from versions

### Project Version

- `projectVersion`: `5.12.2-SNAPSHOT` → `6.0.0-SNAPSHOT`

### New Dependency Entries

- Added `managed-spring-boot-starter-jdbc` library alias in `libs.versions.toml`.

### Build Changes

- `test-suite`: plugin swap `io.micronaut.build.internal.spring-base` + `java-library` → `io.micronaut.build.internal.java-base` + `groovy`; added `testRuntimeOnly(mnTest.junit.platform.launcher)`.
- `spring-boot-starter`: `testFramework` switched from `JUNIT5` to `JUNIT6`; replaced `libs.managed.spring.jdbc` with `libs.managed.spring.boot.starter.jdbc`.

### `gradle/libs.versions.toml`
```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/gradle/libs.versions.toml	2026-04-22 07:18:33.798605534 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/gradle/libs.versions.toml	2026-04-22 07:16:43.315883801 +0000
@@ -1,16 +1,13 @@
 [versions]
-managed-spring-boot = "3.5.11"
-managed-spring = "6.2.16"
-
-micronaut = "4.10.15"
-micronaut-docs = "3.0.0"
-micronaut-test = "4.10.2"
-micronaut-sql = "6.3.3"
-micronaut-cache = "5.3.0"
-micronaut-views = "5.9.0"
-micronaut-validation = "4.12.0"
-micronaut-servlet = "5.6.0"
-micronaut-shared-settings = "7.6.6"
+managed-spring-boot = "4.0.5"
+managed-spring = "7.0.7"
+micronaut = "5.0.0-M23"
+micronaut-views = "6.0.0-M1"
+micronaut-sql = "7.0.1-M2"
+micronaut-cache = "6.0.0-M3"
+micronaut-validation = "5.0.0-M2"
+micronaut-servlet = "6.0.0-M3"
+micronaut-shared-settings = "8.0.0-M17"
 
 [libraries]
 # Micronaut
@@ -24,6 +21,7 @@
 managed-spring-boot = { module = 'org.springframework.boot:spring-boot', version.ref = 'managed-spring-boot' }
 managed-spring-boot-starter = { module = 'org.springframework.boot:spring-boot-starter', version.ref = 'managed-spring-boot' }
 managed-spring-boot-starter-web = { module = 'org.springframework.boot:spring-boot-starter-web', version.ref = 'managed-spring-boot' }
+managed-spring-boot-starter-jdbc = { module = 'org.springframework.boot:spring-boot-starter-jdbc', version.ref = 'managed-spring-boot' }
 
 managed-spring = { module = 'org.springframework:spring-core', version.ref = 'managed-spring' }
 managed-spring-context = { module = 'org.springframework:spring-context', version.ref = 'managed-spring' }
```

### `gradle/wrapper/gradle-wrapper.properties`
```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/gradle/wrapper/gradle-wrapper.properties	2026-04-22 07:18:33.798961454 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/gradle/wrapper/gradle-wrapper.properties	2026-04-22 07:16:43.316215638 +0000
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
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/gradle.properties	2026-04-22 07:18:33.798484616 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/gradle.properties	2026-04-22 07:16:43.315780217 +0000
@@ -1,4 +1,4 @@
-projectVersion=5.12.2-SNAPSHOT
+projectVersion=6.0.0-SNAPSHOT
 projectGroup=io.micronaut.spring
 
 title=Micronaut for Spring
```

### `settings.gradle.kts`
```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/settings.gradle.kts	2026-04-22 07:18:33.799176831 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/settings.gradle.kts	2026-04-22 07:16:43.316438931 +0000
@@ -7,7 +7,7 @@
 }
 
 plugins {
-    id("io.micronaut.build.shared.settings") version "7.6.6"
+    id("io.micronaut.build.shared.settings") version "8.0.0-M17"
 }
 
 rootProject.name = "spring-parent"
```

### `spring-boot-starter/build.gradle.kts`
```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-boot-starter/build.gradle.kts	2026-04-22 07:18:33.804630672 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-boot-starter/build.gradle.kts	2026-04-22 07:16:43.321451810 +0000
@@ -19,7 +19,7 @@
     testImplementation(libs.spring.boot.autoconfigure)
     testImplementation(libs.spring.boot.actuator)
     testImplementation(libs.spring.boot.test)
-    testImplementation(libs.managed.spring.jdbc)
+    testImplementation(libs.managed.spring.boot.starter.jdbc)
     testImplementation(mnSql.h2)
 
     testRuntimeOnly(libs.managed.spring.boot.starter.web)
@@ -27,5 +27,5 @@
 }
 
 micronautBuild {
-    testFramework =  io.micronaut.build.TestFramework.JUNIT5
+    testFramework =  io.micronaut.build.TestFramework.JUNIT6
 }
```

### `test-suite/build.gradle.kts`
```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/test-suite/build.gradle.kts	2026-04-22 07:18:33.826107656 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/test-suite/build.gradle.kts	2026-04-22 07:16:43.344291348 +0000
@@ -1,7 +1,7 @@
 plugins {
-    id("io.micronaut.build.internal.spring-base")
-    `java-library`
     groovy
+    id("io.micronaut.build.internal.java-base")
+
 }
 
 dependencies {
@@ -12,6 +12,7 @@
 
     testImplementation(projects.micronautSpring)
     testImplementation(mnTest.micronaut.test.spock)
+    testRuntimeOnly(mnTest.junit.platform.launcher)
 }
 
 tasks.test {
```

---

## Added Files

- `.agents/skills/agent-md-refactor/SKILL.md`
- `.agents/skills/agent-md-refactor/references/examples-and-anti-patterns.md`
- `.agents/skills/agent-md-refactor/references/refactor-playbook.md`
- `.agents/skills/coding/SKILL.md`
- `.agents/skills/docs/SKILL.md`
- `.agents/skills/docs/references/control-panel-patterns.md`
- `.agents/skills/docs/references/micronaut-docs-providers.md`
- `.agents/skills/gradle/SKILL.md`
- `.agents/skills/gradle/references/gradle-best-practices.md`
- `.agents/skills/gradle/references/micronaut-build-plugins.md`
- `.agents/skills/skill-creator/SKILL.md`
- `.agents/skills/skill-creator/references/research-synthesis.md`
- `.agents/skills/skill-creator/references/spec-checklist.md`
- `.agents/skills/skill-creator/references/templates.md`
- `.github/workflows/sonatype.yml`
- `.sdkmanrc`
- `src/main/docs/guide/breaks.adoc`
- `test-suite/src/test/java/io/micronaut/spring/tx/FakeEvent.java` (relocated from groovy, `.groovy` → `.java`)
- `test-suite/src/test/java/io/micronaut/spring/tx/MetaAnnotation.java` (relocated)
- `test-suite/src/test/java/io/micronaut/spring/tx/MetaTransactionalBean.java` (relocated)
- `test-suite/src/test/java/io/micronaut/spring/tx/MockTransactionManager.java` (relocated)
- `test-suite/src/test/java/io/micronaut/spring/tx/TransactionalBean.java` (relocated)
- `test-suite/src/test/java/io/micronaut/spring/tx/TransactionalListener.java` (relocated)

## Removed Files

- `test-suite/src/test/groovy/io/micronaut/spring/tx/FakeEvent.groovy` (moved to Java sources)
- `test-suite/src/test/groovy/io/micronaut/spring/tx/MetaAnnotation.java` (moved to Java sources)
- `test-suite/src/test/groovy/io/micronaut/spring/tx/MetaTransactionalBean.java` (moved to Java sources)
- `test-suite/src/test/groovy/io/micronaut/spring/tx/MockTransactionManager.java` (moved to Java sources)
- `test-suite/src/test/groovy/io/micronaut/spring/tx/TransactionalBean.java` (moved to Java sources)
- `test-suite/src/test/groovy/io/micronaut/spring/tx/TransactionalListener.java` (moved to Java sources)

---

## Modified Files

### `.clineignore`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/.clineignore	2026-04-22 07:18:33.795108878 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/.clineignore	2026-04-22 07:16:43.312579647 +0000
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
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/.clinerules/coding.md	2026-04-22 07:18:33.795235546 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/.clinerules/coding.md	2026-04-22 07:16:43.312703023 +0000
@@ -41,7 +41,7 @@
 
 You SHOULD prefer modern Java idioms: records, pattern matching, sealed interfaces/classes, `var` for local variables.
 You MUST NOT use fully qualified class names unless there is a conflict between 2 class names in different packages.
-You MUST annotate the code with nullability annotations (`io.micronaut.core.annotation.Nullable`, `io.micronaut.core.annotation.NonNull`).
+You MUST annotate the code with nullability annotations (`org.jspecify.annotations.Nullable`, `org.jspecify.annotations.NonNull`).
 You MUST NOT use reflection: Micronaut is a reflection-free framework tailored for integration with GraalVM.
 You MUST use `jakarta.inject` for dependency injection, NOT `javax.inject`.
 
@@ -50,7 +50,7 @@
 Micronaut projects are intended to be used in consumer applications and therefore follow semantic versioning. As a consequence:
 - You MUST NOT break any public facing API without explicit consent
 - You SHOULD run the `./gradlew japiCmp` task to get a report about binary breaking changes
-- You SHOULD reduce the visibility of members for non user-facing APIs.
+- You SHOULD reduce the visibility of members for non-user-facing APIs.
 - You MUST annotate non-user facing APIs with `@io.micronaut.core.annotation.Internal`
 
 ## Implementation Workflow (Required Checklist)
@@ -71,9 +71,9 @@
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
@@ -165,7 +165,7 @@
 
 ## Key Requirements
 
-You MUST confirm all of the following BEFORE using `attempt_completion`:
+You MUST confirm all the following BEFORE using `attempt_completion`:
 
 - Changes compile successfully (affected modules)
 - Targeted tests pass
```

### `.clinerules/docs.md`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/.clinerules/docs.md	2026-04-22 07:18:33.795305630 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/.clinerules/docs.md	2026-04-22 07:16:43.312774065 +0000
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

### `.github/instructions/coding.instructions.md`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/.github/instructions/coding.instructions.md	2026-04-22 07:18:33.795910218 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/.github/instructions/coding.instructions.md	2026-04-22 07:16:43.313360487 +0000
@@ -41,7 +41,7 @@
 
 You SHOULD prefer modern Java idioms: records, pattern matching, sealed interfaces/classes, `var` for local variables.
 You MUST NOT use fully qualified class names unless there is a conflict between 2 class names in different packages.
-You MUST annotate the code with nullability annotations (`io.micronaut.core.annotation.Nullable`, `io.micronaut.core.annotation.NonNull`).
+You MUST annotate the code with nullability annotations (`org.jspecify.annotations.Nullable`, `org.jspecify.annotations.NonNull`).
 You MUST NOT use reflection: Micronaut is a reflection-free framework tailored for integration with GraalVM.
 You MUST use `jakarta.inject` for dependency injection, NOT `javax.inject`.
 
@@ -50,7 +50,7 @@
 Micronaut projects are intended to be used in consumer applications and therefore follow semantic versioning. As a consequence:
 - You MUST NOT break any public facing API without explicit consent
 - You SHOULD run the `./gradlew japiCmp` task to get a report about binary breaking changes
-- You SHOULD reduce the visibility of members for non user-facing APIs.
+- You SHOULD reduce the visibility of members for non-user-facing APIs.
 - You MUST annotate non-user facing APIs with `@io.micronaut.core.annotation.Internal`
 
 ## Implementation Workflow (Required Checklist)
@@ -71,9 +71,9 @@
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
@@ -165,7 +165,7 @@
 
 ## Key Requirements
 
-You MUST confirm all of the following BEFORE using `attempt_completion`:
+You MUST confirm all the following BEFORE using `attempt_completion`:
 
 - Changes compile successfully (affected modules)
 - Targeted tests pass
```

### `.github/instructions/docs.instructions.md`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/.github/instructions/docs.instructions.md	2026-04-22 07:18:33.795978719 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/.github/instructions/docs.instructions.md	2026-04-22 07:16:43.313421696 +0000
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
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/.github/renovate.json	2026-04-22 07:18:33.796101262 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/.github/renovate.json	2026-04-22 07:16:43.313551031 +0000
@@ -19,9 +19,18 @@
       ],
       "matchCurrentVersion": "!/^0/",
       "automerge": true,
-      "matchPackageNames": [
-        "/actions.*/"
-      ]
+      "matchManagers": ["github-actions"],
+      "groupName": "GitHub Actions dependencies"
+    },
+    {
+      "matchDatasources": [
+        "maven"
+      ],
+      "matchManagers": [
+        "maven",
+        "gradle"
+      ],
+      "allowedVersions": "!/.+-SNAPSHOT$/"
     },
     {
       "matchUpdateTypes": [
@@ -29,6 +38,12 @@
       ],
       "matchCurrentVersion": "!/^0/",
       "automerge": true
+    },
+    {
+      "matchPackageNames": [
+        "/.*micronaut.*/"
+      ],
+      "groupName": "Micronaut dependencies"
     }
   ]
 }
```

### `.github/workflows/central-sync.yml`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/.github/workflows/central-sync.yml	2026-04-22 07:18:33.796240221 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/.github/workflows/central-sync.yml	2026-04-22 07:16:43.313666407 +0000
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
+      - uses: gradle/actions/wrapper-validation@50e97c2cd7a37755bbfafc9c5b7cafaece252f6e # v6
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
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/.github/workflows/graalvm-dev.yml	2026-04-22 07:18:33.796312472 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/.github/workflows/graalvm-dev.yml	2026-04-22 07:16:43.313752991 +0000
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
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/.github/workflows/graalvm-latest.yml	2026-04-22 07:18:33.796377431 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/.github/workflows/graalvm-latest.yml	2026-04-22 07:16:43.313818949 +0000
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
-    env:
-      DEVELOCITY_ACCESS_KEY: ${{ secrets.GRADLE_ENTERPRISE_ACCESS_KEY }}
-      DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
-      DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
     outputs:
       matrix: ${{ steps.build-matrix.outputs.matrix }}
     steps:
-      - uses: actions/checkout@v5
+      - uses: actions/checkout@de0fac2e4500dabe0009e67214ff5f5447ce83dd # v6
       - name: Build Matrix
-        uses: micronaut-projects/github-actions/graalvm/build-matrix@master
+        uses: micronaut-projects/github-actions/graalvm/build-matrix@300bf6db7c062dcba77c90bb90e475df31b2acab # master
         id: build-matrix
+        env:
+          DEVELOCITY_ACCESS_KEY: ${{ secrets.GRADLE_ENTERPRISE_ACCESS_KEY }}
+          DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
+          DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
+        with:
+          java-version: '25'
   build:
     needs: build_matrix
     if: github.repository != 'micronaut-projects/micronaut-project-template'
@@ -35,31 +37,45 @@
     strategy:
       max-parallel: 6
       matrix:
-        java: ['17', '21']
+        java: ['25']
         native_test_task: ${{ fromJson(needs.build_matrix.outputs.matrix).native_test_task }}
-    env:
-      DEVELOCITY_ACCESS_KEY: ${{ secrets.GRADLE_ENTERPRISE_ACCESS_KEY }}
-      DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
-      DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
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
+        env:
+          DEVELOCITY_ACCESS_KEY: ${{ secrets.GRADLE_ENTERPRISE_ACCESS_KEY }}
+          DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
+          DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
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
+          DEVELOCITY_ACCESS_KEY: ${{ secrets.GRADLE_ENTERPRISE_ACCESS_KEY }}
+          DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
+          DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
           GH_TOKEN_PUBLIC_REPOS_READONLY: ${{ secrets.GH_TOKEN_PUBLIC_REPOS_READONLY }}
           GH_USERNAME: ${{ secrets.GH_USERNAME }}
           GRAALVM_QUICK_BUILD: true
         with:
           nativeTestTask: ${{ matrix.native_test_task }}
       - name: Post-Build Steps
-        uses: micronaut-projects/github-actions/graalvm/post-build@master
+        uses: micronaut-projects/github-actions/graalvm/post-build@300bf6db7c062dcba77c90bb90e475df31b2acab # master
         id: post-build
+        env:
+          DEVELOCITY_ACCESS_KEY: ${{ secrets.GRADLE_ENTERPRISE_ACCESS_KEY }}
+          DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
+          DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
         with:
           java: ${{ matrix.java }}
```

### `.github/workflows/gradle.yml`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/.github/workflows/gradle.yml	2026-04-22 07:18:33.796445806 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/.github/workflows/gradle.yml	2026-04-22 07:16:43.313884784 +0000
@@ -8,98 +8,107 @@
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
       TESTCONTAINERS_RYUK_DISABLED: true
-      PREDICTIVE_TEST_SELECTION: "${{ github.event_name == 'pull_request' && 'true' || 'false' }}"
-      SONAR_TOKEN: ${{ secrets.SONAR_TOKEN }}
-      GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
-      OSS_INDEX_USERNAME: ${{ secrets.OSS_INDEX_USERNAME }}
-      OSS_INDEX_PASSWORD: ${{ secrets.OSS_INDEX_PASSWORD }}
+      SONAR_TOKEN_AVAILABLE: ${{ secrets.SONAR_TOKEN != '' }}
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
-        uses: graalvm/setup-graalvm@v1.4.1
+        uses: graalvm/setup-graalvm@60c26726de13f8b90771df4bc1641a52a3159994 # v1
         with:
           distribution: 'graalvm'
           java-version: ${{ matrix.java }}
           github-token: ${{ secrets.GITHUB_TOKEN }}
 
       - name: "🔧 Setup Gradle"
-        uses: gradle/actions/setup-gradle@v4
+        uses: gradle/actions/setup-gradle@50e97c2cd7a37755bbfafc9c5b7cafaece252f6e # v6
 
       - name: "❓ Optional setup step"
         run: |
           [ -f ./setup.sh ] && ./setup.sh || [ ! -f ./setup.sh ]
 
-      - name: "🚔 Sonatype Scan"
-        if: env.OSS_INDEX_PASSWORD != '' && matrix.java == '17'
-        id: sonatypescan
-        run: |
-          ./gradlew ossIndexAudit --no-parallel --info
-
       - name: "🛠 Build with Gradle"
         id: gradle
+        env:
+          DEVELOCITY_ACCESS_KEY: ${{ secrets.GRADLE_ENTERPRISE_ACCESS_KEY }}
+          DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
+          DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
+          GH_TOKEN_PUBLIC_REPOS_READONLY: ${{ secrets.GH_TOKEN_PUBLIC_REPOS_READONLY }}
+          GH_USERNAME: ${{ secrets.GH_USERNAME }}
+          OSS_INDEX_USERNAME: ${{ secrets.OSS_INDEX_USERNAME }}
+          OSS_INDEX_PASSWORD: ${{ secrets.OSS_INDEX_PASSWORD }}
         run: |
-          ./gradlew jacocoReport check --no-daemon --continue
+          ./gradlew check jacocoReport --no-daemon --continue
 
       - name: "🔎 Run static analysis"
-        if: env.SONAR_TOKEN != '' && matrix.java == '17'
+        if: env.SONAR_TOKEN_AVAILABLE == 'true' && matrix.java == '25'
+        env:
+          DEVELOCITY_ACCESS_KEY: ${{ secrets.GRADLE_ENTERPRISE_ACCESS_KEY }}
+          DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
+          DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
+          SONAR_TOKEN: ${{ secrets.SONAR_TOKEN }}
         run: |
           ./gradlew sonar --no-parallel --continue
 
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
+        uses: actions/upload-artifact@043fb46d1a93c77aae656e7c1c64a875d1fc6a0a # v7
         with:
           name: binary-compatibility-reports
           path: "**/build/reports/binary-compatibility-*.html"
 
       - name: "📦 Publish to Sonatype Snapshots"
-        if: success() && github.event_name == 'push' && matrix.java == '17'
+        if: success() && github.event_name == 'push' && matrix.java == '25'
         env:
+          DEVELOCITY_ACCESS_KEY: ${{ secrets.GRADLE_ENTERPRISE_ACCESS_KEY }}
+          DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
+          DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
           SONATYPE_USERNAME: ${{ secrets.SONATYPE_USERNAME }}
           SONATYPE_PASSWORD: ${{ secrets.SONATYPE_PASSWORD }}
         run: ./gradlew publishToSonatype docs --no-daemon
 
       - name: "❓ Determine docs target repository"
-        uses: haya14busa/action-cond@v1
+        uses: haya14busa/action-cond@94f77f7a80cd666cb3155084e428254fea4281fd # v1
         id: docs_target
         with:
           cond: ${{ github.repository == 'micronaut-projects/micronaut-core' }}
@@ -107,10 +116,14 @@
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
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/.github/workflows/publish-snapshot.yml	2026-04-22 07:18:33.796508182 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/.github/workflows/publish-snapshot.yml	2026-04-22 07:16:43.313950534 +0000
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
+      - uses: actions/cache@27d5ce7f107fe9357f9df03efb73ab90386fccae # v5
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
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/.github/workflows/release.yml	2026-04-22 07:18:33.796567308 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/.github/workflows/release.yml	2026-04-22 07:16:43.314022868 +0000
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
+      - uses: gradle/actions/wrapper-validation@50e97c2cd7a37755bbfafc9c5b7cafaece252f6e # v6
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
+        uses: actions/upload-artifact@043fb46d1a93c77aae656e7c1c64a875d1fc6a0a # v7.0.1
         with:
           name: gradle-build-outputs
           path: build/repo/${{ steps.publish.outputs.group }}/*/${{ steps.publish.outputs.version }}/*
           retention-days: 5
       - name: Upload artifacts-sha256
-        uses: actions/upload-artifact@65c4c4a1ddee5b72f698fdd19549f0f0fb45cf08 # v4.6.0
+        uses: actions/upload-artifact@043fb46d1a93c77aae656e7c1c64a875d1fc6a0a # v7.0.1
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
-        uses: softprops/action-gh-release@6da8fa9354ddfdc4aeace5fc48d7f679b5214090 # v2.4.1
+        uses: softprops/action-gh-release@b4309332981a82ec1c5618f44dd2e27cc8bfbfda # v3.0.0
         with:
           files: artifacts.zip
```

### `.gitignore`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/.gitignore	2026-04-22 07:18:33.796647225 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/.gitignore	2026-04-22 07:16:43.314149453 +0000
@@ -34,3 +34,9 @@
 
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
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/MAINTAINING.md	2026-04-22 07:18:33.797025062 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/MAINTAINING.md	2026-04-22 07:16:43.314525414 +0000
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

### `config/accepted-api-changes.json`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/config/accepted-api-changes.json	2026-04-22 07:18:33.798100530 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/config/accepted-api-changes.json	2026-04-22 07:16:43.315453881 +0000
@@ -183,5 +183,10 @@
     "type": "io.micronaut.spring.context.aop.$SpringConfigurationInterceptor$Definition$Reference",
     "member": "Implemented interface io.micronaut.inject.BeanDefinitionReference",
     "reason": "Internal runtime class moved from processors"
+  },
+  {
+    "type": "io.micronaut.spring.beans.MicronautBeanProcessor",
+    "member": "Field micronautContext",
+    "reason": "Changed from DefaultBeanContext to ApplicationContext for Micronaut 5 compatibility (DefaultEnvironment is now sealed)"
   }
 ]
```

### `gradle/wrapper/gradle-wrapper.jar`

_Binary file differs._

### `gradlew`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/gradlew	2026-04-22 07:18:33.799053122 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/gradlew	2026-04-22 07:16:43.316302222 +0000
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
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/gradlew.bat	2026-04-22 07:18:33.799119539 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/gradlew.bat	2026-04-22 07:16:43.316372972 +0000
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

### `spring/src/main/java/io/micronaut/spring/beans/MicronautBeanProcessor.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring/src/main/java/io/micronaut/spring/beans/MicronautBeanProcessor.java	2026-04-22 07:18:33.821501489 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring/src/main/java/io/micronaut/spring/beans/MicronautBeanProcessor.java	2026-04-22 07:16:43.338721506 +0000
@@ -15,11 +15,10 @@
  */
 package io.micronaut.spring.beans;
 
-import io.micronaut.context.DefaultApplicationContext;
-import io.micronaut.context.DefaultBeanContext;
+import io.micronaut.context.ApplicationContext;
+import io.micronaut.context.ApplicationContextBuilder;
 import io.micronaut.context.Qualifier;
-import io.micronaut.context.env.DefaultEnvironment;
-import io.micronaut.core.convert.ArgumentConversionContext;
+import io.micronaut.context.env.PropertySource;
 import io.micronaut.core.util.ArrayUtils;
 import io.micronaut.inject.qualifiers.Qualifiers;
 import org.springframework.beans.BeansException;
@@ -29,12 +28,15 @@
 import org.springframework.beans.factory.support.BeanDefinitionBuilder;
 import org.springframework.beans.factory.support.DefaultListableBeanFactory;
 import org.springframework.context.EnvironmentAware;
+import org.springframework.core.env.ConfigurableEnvironment;
+import org.springframework.core.env.EnumerablePropertySource;
 import org.springframework.core.env.Environment;
 
 import java.lang.annotation.Annotation;
+import java.util.ArrayList;
 import java.util.Arrays;
+import java.util.Iterator;
 import java.util.List;
-import java.util.Optional;
 
 /**
  * Adds Micronaut beans to a Spring application context.  This processor will
@@ -50,7 +52,7 @@
     private static final String MICRONAUT_CONTEXT_PROPERTY_NAME = "micronautContext";
     private static final String MICRONAUT_SINGLETON_PROPERTY_NAME = "micronautSingleton";
 
-    protected DefaultBeanContext micronautContext;
+    protected ApplicationContext micronautContext;
     protected final List<Class<?>> micronautBeanQualifierTypes;
     private Environment environment;
 
@@ -66,44 +68,48 @@
 
     @Override
     public void postProcessBeanFactory(ConfigurableListableBeanFactory beanFactory) throws BeansException {
+        ApplicationContextBuilder builder = ApplicationContext.builder();
+
         if (environment != null) {
             String[] profiles = getProfiles();
-            micronautContext = new DefaultApplicationContext(profiles) {
-                DefaultEnvironment env = new DefaultEnvironment(() -> Arrays.asList(profiles)) {
-                    @Override
-                    public io.micronaut.context.env.Environment start() {
-                        return this;
-                    }
-
-                    @Override
-                    public io.micronaut.context.env.Environment stop() {
-                        return this;
-                    }
-
-                    @Override
-                    public boolean containsProperty(String name) {
-                        return environment.containsProperty(name);
-                    }
+            builder.environments(profiles);
 
-                    @Override
-                    public boolean containsProperties(String name) {
-                        return environment.containsProperty(name);
+            if (environment instanceof ConfigurableEnvironment configurableEnv) {
+                builder.propertySourcesLocator(env -> {
+                    List<PropertySource> propertySources = new ArrayList<>();
+                    int order = 0;
+                    for (org.springframework.core.env.PropertySource<?> springSource : configurableEnv.getPropertySources()) {
+                        if (springSource instanceof EnumerablePropertySource<?> enumerableSource) {
+                            final int currentOrder = order++;
+                            propertySources.add(new PropertySource() {
+                                @Override
+                                public String getName() {
+                                    return springSource.getName();
+                                }
+
+                                @Override
+                                public Object get(String key) {
+                                    return enumerableSource.getProperty(key);
+                                }
+
+                                @Override
+                                public Iterator<String> iterator() {
+                                    return Arrays.asList(enumerableSource.getPropertyNames()).iterator();
+                                }
+
+                                @Override
+                                public int getOrder() {
+                                    return currentOrder;
+                                }
+                            });
+                        }
                     }
-
-                    @Override
-                    public <T> Optional<T> getProperty(String name, ArgumentConversionContext<T> conversionContext) {
-                        return Optional.ofNullable(environment.getProperty(name, conversionContext.getArgument().getType()));
-                    }
-                };
-
-                @Override
-                public io.micronaut.context.env.Environment getEnvironment() {
-                    return env;
-                }
-            };
-        } else {
-            micronautContext = new DefaultApplicationContext();
+                    return propertySources;
+                });
+            }
         }
+
+        micronautContext = builder.build();
         micronautContext.start();
 
         micronautBeanQualifierTypes
@@ -141,4 +147,3 @@
         this.environment = environment;
     }
 }
-
```

### `spring/src/main/java/io/micronaut/spring/beans/MicronautSpringBeanFactory.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring/src/main/java/io/micronaut/spring/beans/MicronautSpringBeanFactory.java	2026-04-22 07:18:33.821669241 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring/src/main/java/io/micronaut/spring/beans/MicronautSpringBeanFactory.java	2026-04-22 07:16:43.338888383 +0000
@@ -15,7 +15,7 @@
  */
 package io.micronaut.spring.beans;
 
-import io.micronaut.context.DefaultApplicationContext;
+import io.micronaut.context.ApplicationContext;
 import io.micronaut.context.exceptions.BeanInstantiationException;
 import org.springframework.beans.factory.FactoryBean;
 
@@ -31,7 +31,7 @@
 class MicronautSpringBeanFactory implements FactoryBean {
 
     private Class micronautBeanType;
-    private DefaultApplicationContext micronautContext;
+    private ApplicationContext micronautContext;
     private boolean isMicronautSingleton;
 
     /**
@@ -44,7 +44,7 @@
     /**
      * @param micronautContext The Micronaut application context
      */
-    public void setMicronautContext(DefaultApplicationContext micronautContext) {
+    public void setMicronautContext(ApplicationContext micronautContext) {
         this.micronautContext = micronautContext;
     }
 
```

### `spring/src/main/java/io/micronaut/spring/beans/ObjectProviderBeanDefinition.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring/src/main/java/io/micronaut/spring/beans/ObjectProviderBeanDefinition.java	2026-04-22 07:18:33.821746200 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring/src/main/java/io/micronaut/spring/beans/ObjectProviderBeanDefinition.java	2026-04-22 07:16:43.338965050 +0000
@@ -23,8 +23,8 @@
 import io.micronaut.context.DefaultBeanContext;
 import io.micronaut.context.Qualifier;
 import io.micronaut.core.annotation.Internal;
-import io.micronaut.core.annotation.NonNull;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.NonNull;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.core.reflect.InstantiationUtils;
 import io.micronaut.core.type.Argument;
 import io.micronaut.inject.BeanDefinition;
```

### `spring/src/main/java/io/micronaut/spring/tx/annotation/TransactionInterceptor.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring/src/main/java/io/micronaut/spring/tx/annotation/TransactionInterceptor.java	2026-04-22 07:18:33.823225713 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring/src/main/java/io/micronaut/spring/tx/annotation/TransactionInterceptor.java	2026-04-22 07:16:43.340713649 +0000
@@ -90,7 +90,7 @@
             try {
                 retVal = context.proceed();
             } catch (Throwable ex) {
-                completeTransactionAfterThrowing(transactionInfo, ex);
+                completeTransactionAfterThrowing(transactionInfo, context::proceed, ex);
                 throw ex;
             } finally {
                 cleanupTransactionInfo(transactionInfo);
```

### `spring-annotation/src/main/java/io/micronaut/spring/annotation/AbstractSpringAnnotationMapper.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-annotation/src/main/java/io/micronaut/spring/annotation/AbstractSpringAnnotationMapper.java	2026-04-22 07:18:33.799620127 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-annotation/src/main/java/io/micronaut/spring/annotation/AbstractSpringAnnotationMapper.java	2026-04-22 07:16:43.316904436 +0000
@@ -16,7 +16,7 @@
 package io.micronaut.spring.annotation;
 
 import io.micronaut.core.annotation.AnnotationValue;
-import io.micronaut.core.annotation.NonNull;
+import org.jspecify.annotations.NonNull;
 import io.micronaut.inject.annotation.NamedAnnotationMapper;
 import io.micronaut.inject.visitor.VisitorContext;
 
```

### `spring-annotation/src/main/java/io/micronaut/spring/annotation/beans/ImportAnnotationVisitor.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-annotation/src/main/java/io/micronaut/spring/annotation/beans/ImportAnnotationVisitor.java	2026-04-22 07:18:33.799824337 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-annotation/src/main/java/io/micronaut/spring/annotation/beans/ImportAnnotationVisitor.java	2026-04-22 07:16:43.317115521 +0000
@@ -21,7 +21,7 @@
 import java.util.Set;
 
 import io.micronaut.core.annotation.Internal;
-import io.micronaut.core.annotation.NonNull;
+import org.jspecify.annotations.NonNull;
 import jakarta.inject.Singleton;
 import org.springframework.beans.factory.BeanClassLoaderAware;
 import org.springframework.beans.factory.BeanFactoryAware;
```

### `spring-annotation/src/main/java/io/micronaut/spring/annotation/cache/CacheEvictAnnotationMapper.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-annotation/src/main/java/io/micronaut/spring/annotation/cache/CacheEvictAnnotationMapper.java	2026-04-22 07:18:33.799942129 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-annotation/src/main/java/io/micronaut/spring/annotation/cache/CacheEvictAnnotationMapper.java	2026-04-22 07:16:43.317229147 +0000
@@ -18,7 +18,7 @@
 import io.micronaut.cache.annotation.CacheInvalidate;
 import io.micronaut.core.annotation.AnnotationValue;
 import io.micronaut.core.annotation.AnnotationValueBuilder;
-import io.micronaut.core.annotation.NonNull;
+import org.jspecify.annotations.NonNull;
 
 import java.lang.annotation.Annotation;
 
```

### `spring-annotation/src/main/java/io/micronaut/spring/annotation/cache/CachePutAnnotationMapper.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-annotation/src/main/java/io/micronaut/spring/annotation/cache/CachePutAnnotationMapper.java	2026-04-22 07:18:33.800010964 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-annotation/src/main/java/io/micronaut/spring/annotation/cache/CachePutAnnotationMapper.java	2026-04-22 07:16:43.317294897 +0000
@@ -18,7 +18,7 @@
 import io.micronaut.cache.annotation.CachePut;
 import io.micronaut.core.annotation.AnnotationValue;
 import io.micronaut.core.annotation.AnnotationValueBuilder;
-import io.micronaut.core.annotation.NonNull;
+import org.jspecify.annotations.NonNull;
 
 import java.lang.annotation.Annotation;
 
```

### `spring-annotation/src/main/java/io/micronaut/spring/annotation/cache/CacheableAnnotationMapper.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-annotation/src/main/java/io/micronaut/spring/annotation/cache/CacheableAnnotationMapper.java	2026-04-22 07:18:33.800094131 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-annotation/src/main/java/io/micronaut/spring/annotation/cache/CacheableAnnotationMapper.java	2026-04-22 07:16:43.317375606 +0000
@@ -18,7 +18,7 @@
 import io.micronaut.cache.annotation.Cacheable;
 import io.micronaut.core.annotation.AnnotationValue;
 import io.micronaut.core.annotation.AnnotationValueBuilder;
-import io.micronaut.core.annotation.NonNull;
+import org.jspecify.annotations.NonNull;
 import io.micronaut.core.util.ArrayUtils;
 import io.micronaut.inject.visitor.VisitorContext;
 import io.micronaut.spring.annotation.AbstractSpringAnnotationMapper;
```

### `spring-annotation/src/main/java/io/micronaut/spring/annotation/context/AutowiredAnnotationMapper.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-annotation/src/main/java/io/micronaut/spring/annotation/context/AutowiredAnnotationMapper.java	2026-04-22 07:18:33.800193132 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-annotation/src/main/java/io/micronaut/spring/annotation/context/AutowiredAnnotationMapper.java	2026-04-22 07:16:43.317482732 +0000
@@ -17,7 +17,7 @@
 
 import io.micronaut.core.annotation.AnnotationUtil;
 import io.micronaut.core.annotation.AnnotationValue;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.inject.visitor.VisitorContext;
 import io.micronaut.spring.annotation.AbstractSpringAnnotationMapper;
 
```

### `spring-boot-annotation/src/main/java/io/micronaut/spring/boot/annotation/ConditionalOnBeanAnnotationMapper.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-boot-annotation/src/main/java/io/micronaut/spring/boot/annotation/ConditionalOnBeanAnnotationMapper.java	2026-04-22 07:18:33.802799905 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-boot-annotation/src/main/java/io/micronaut/spring/boot/annotation/ConditionalOnBeanAnnotationMapper.java	2026-04-22 07:16:43.320122298 +0000
@@ -19,7 +19,7 @@
 import io.micronaut.core.annotation.AnnotationClassValue;
 import io.micronaut.core.annotation.AnnotationMetadata;
 import io.micronaut.core.annotation.AnnotationValue;
-import io.micronaut.core.annotation.NonNull;
+import org.jspecify.annotations.NonNull;
 import io.micronaut.core.util.ArrayUtils;
 import io.micronaut.inject.visitor.VisitorContext;
 import io.micronaut.spring.annotation.AbstractSpringAnnotationMapper;
```

### `spring-boot-annotation/src/main/java/io/micronaut/spring/boot/annotation/ConditionalOnClassAnnotationMapper.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-boot-annotation/src/main/java/io/micronaut/spring/boot/annotation/ConditionalOnClassAnnotationMapper.java	2026-04-22 07:18:33.802893573 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-boot-annotation/src/main/java/io/micronaut/spring/boot/annotation/ConditionalOnClassAnnotationMapper.java	2026-04-22 07:16:43.320193382 +0000
@@ -15,7 +15,7 @@
  */
 package io.micronaut.spring.boot.annotation;
 
-import io.micronaut.core.annotation.NonNull;
+import org.jspecify.annotations.NonNull;
 
 /**
  * Maps ConditionalOnClass to Micronaut Requires.
```

### `spring-boot-annotation/src/main/java/io/micronaut/spring/boot/annotation/ConditionalOnMissingBeanAnnotationMapper.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-boot-annotation/src/main/java/io/micronaut/spring/boot/annotation/ConditionalOnMissingBeanAnnotationMapper.java	2026-04-22 07:18:33.802994449 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-boot-annotation/src/main/java/io/micronaut/spring/boot/annotation/ConditionalOnMissingBeanAnnotationMapper.java	2026-04-22 07:16:43.320264674 +0000
@@ -15,7 +15,7 @@
  */
 package io.micronaut.spring.boot.annotation;
 
-import io.micronaut.core.annotation.NonNull;
+import org.jspecify.annotations.NonNull;
 
 /**
  * Maps ConditionalOnMissingBean to Micronaut Requires.
```

### `spring-boot-annotation/src/main/java/io/micronaut/spring/boot/annotation/ConditionalOnMissingClassAnnotationMapper.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-boot-annotation/src/main/java/io/micronaut/spring/boot/annotation/ConditionalOnMissingClassAnnotationMapper.java	2026-04-22 07:18:33.803074324 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-boot-annotation/src/main/java/io/micronaut/spring/boot/annotation/ConditionalOnMissingClassAnnotationMapper.java	2026-04-22 07:16:43.320332800 +0000
@@ -15,7 +15,7 @@
  */
 package io.micronaut.spring.boot.annotation;
 
-import io.micronaut.core.annotation.NonNull;
+import org.jspecify.annotations.NonNull;
 
 /**
  * Maps ConditionalOnMissingClass to Micronaut Requires.
```

### `spring-boot-annotation/src/main/java/io/micronaut/spring/boot/annotation/DeleteOperationAnnotationMapper.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-boot-annotation/src/main/java/io/micronaut/spring/boot/annotation/DeleteOperationAnnotationMapper.java	2026-04-22 07:18:33.803685705 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-boot-annotation/src/main/java/io/micronaut/spring/boot/annotation/DeleteOperationAnnotationMapper.java	2026-04-22 07:16:43.320778929 +0000
@@ -15,7 +15,7 @@
  */
 package io.micronaut.spring.boot.annotation;
 
-import io.micronaut.core.annotation.NonNull;
+import org.jspecify.annotations.NonNull;
 
 /**
  * Maps Actuator DeleteOperation to Micronaut Delete.
```

### `spring-boot-annotation/src/main/java/io/micronaut/spring/boot/annotation/ReadOperationAnnotationMapper.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-boot-annotation/src/main/java/io/micronaut/spring/boot/annotation/ReadOperationAnnotationMapper.java	2026-04-22 07:18:33.803889415 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-boot-annotation/src/main/java/io/micronaut/spring/boot/annotation/ReadOperationAnnotationMapper.java	2026-04-22 07:16:43.320932222 +0000
@@ -16,7 +16,7 @@
 package io.micronaut.spring.boot.annotation;
 
 import io.micronaut.core.annotation.AnnotationValue;
-import io.micronaut.core.annotation.NonNull;
+import org.jspecify.annotations.NonNull;
 import io.micronaut.core.util.ArrayUtils;
 import io.micronaut.http.annotation.Produces;
 import io.micronaut.inject.visitor.VisitorContext;
```

### `spring-boot-annotation/src/main/java/io/micronaut/spring/boot/annotation/WriteOperationAnnotationMapper.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-boot-annotation/src/main/java/io/micronaut/spring/boot/annotation/WriteOperationAnnotationMapper.java	2026-04-22 07:18:33.804189251 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-boot-annotation/src/main/java/io/micronaut/spring/boot/annotation/WriteOperationAnnotationMapper.java	2026-04-22 07:16:43.321158265 +0000
@@ -15,7 +15,7 @@
  */
 package io.micronaut.spring.boot.annotation;
 
-import io.micronaut.core.annotation.NonNull;
+import org.jspecify.annotations.NonNull;
 
 /**
  * Maps Actuator WriteOperation to Micronaut Write.
```

### `spring-boot-starter/src/main/java/io/micronaut/spring/boot/starter/MicronautBeanFilter.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-boot-starter/src/main/java/io/micronaut/spring/boot/starter/MicronautBeanFilter.java	2026-04-22 07:18:33.805308719 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-boot-starter/src/main/java/io/micronaut/spring/boot/starter/MicronautBeanFilter.java	2026-04-22 07:16:43.321992148 +0000
@@ -16,7 +16,7 @@
 package io.micronaut.spring.boot.starter;
 
 import io.micronaut.core.annotation.Introspected;
-import io.micronaut.core.annotation.NonNull;
+import org.jspecify.annotations.NonNull;
 import io.micronaut.inject.BeanDefinition;
 
 /**
```

### `spring-boot-starter/src/main/java/io/micronaut/spring/boot/starter/MicronautImportRegistrar.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-boot-starter/src/main/java/io/micronaut/spring/boot/starter/MicronautImportRegistrar.java	2026-04-22 07:18:33.805414970 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-boot-starter/src/main/java/io/micronaut/spring/boot/starter/MicronautImportRegistrar.java	2026-04-22 07:16:43.322096274 +0000
@@ -33,8 +33,8 @@
 import io.micronaut.context.annotation.Infrastructure;
 import io.micronaut.context.annotation.Primary;
 import io.micronaut.core.annotation.Internal;
-import io.micronaut.core.annotation.NonNull;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.NonNull;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.core.naming.Named;
 import io.micronaut.core.reflect.InstantiationUtils;
 import io.micronaut.core.util.ArrayUtils;
@@ -188,8 +188,8 @@
             }
         }
 
-        Collection<BeanDefinition<?>> allBeanDefinitions = context.getAllBeanDefinitions();
-        for (BeanDefinition<?> definition : allBeanDefinitions) {
+        Collection<BeanDefinition<Object>> allBeanDefinitions = context.getAllBeanDefinitions();
+        for (BeanDefinition<Object> definition : allBeanDefinitions) {
             if (beanFilter.includes(definition) &&
                 !beanFilter.excludes(definition)) {
                 Class<?> beanType = definition.getBeanType();
```

### `spring-boot-starter/src/test/java/io/micronaut/spring/boot/customautoconfigure/CustomAutoConfigureMicronautTest.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-boot-starter/src/test/java/io/micronaut/spring/boot/customautoconfigure/CustomAutoConfigureMicronautTest.java	2026-04-22 07:18:33.806206186 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-boot-starter/src/test/java/io/micronaut/spring/boot/customautoconfigure/CustomAutoConfigureMicronautTest.java	2026-04-22 07:16:43.322815363 +0000
@@ -5,7 +5,7 @@
 import javax.sql.DataSource;
 
 import io.micronaut.context.ApplicationContext;
-import io.micronaut.core.annotation.NonNull;
+import org.jspecify.annotations.NonNull;
 import io.micronaut.http.codec.MediaTypeCodecRegistry;
 import io.micronaut.inject.BeanDefinition;
 import io.micronaut.spring.boot.starter.EnableMicronaut;
```

### `spring-context/src/main/java/io/micronaut/spring/context/MicronautApplicationContext.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-context/src/main/java/io/micronaut/spring/context/MicronautApplicationContext.java	2026-04-22 07:18:33.810943353 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-context/src/main/java/io/micronaut/spring/context/MicronautApplicationContext.java	2026-04-22 07:16:43.327977077 +0000
@@ -18,7 +18,7 @@
 import io.micronaut.context.ApplicationContextBuilder;
 import io.micronaut.context.annotation.Secondary;
 import io.micronaut.context.event.StartupEvent;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.core.reflect.GenericTypeUtils;
 import io.micronaut.inject.BeanDefinition;
 import io.micronaut.runtime.event.annotation.EventListener;
@@ -39,6 +39,7 @@
 import org.springframework.context.*;
 import org.springframework.context.event.ContextRefreshedEvent;
 import org.springframework.core.ResolvableType;
+import org.springframework.core.ParameterizedTypeReference;
 import org.springframework.core.env.ConfigurableEnvironment;
 import org.springframework.core.io.ProtocolResolver;
 import org.springframework.core.io.Resource;
@@ -159,6 +160,14 @@
     }
 
     @Override
+    public void pause() {
+    }
+
+    @Override
+    public void restart() {
+    }
+
+    @Override
     public boolean containsBeanDefinition(String beanName) {
         return beanFactory.containsBeanDefinition(beanName);
     }
@@ -184,6 +193,11 @@
     }
 
     @Override
+    public <T> ObjectProvider<T> getBeanProvider(ParameterizedTypeReference<T> requiredType) {
+        return beanFactory.getBeanProvider(ResolvableType.forType(requiredType.getType()));
+    }
+
+    @Override
     public String[] getBeanNamesForType(ResolvableType type) {
         return beanFactory.getBeanNamesForType(type);
     }
```

### `spring-context/src/main/java/io/micronaut/spring/context/aware/SpringAwareListener.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-context/src/main/java/io/micronaut/spring/context/aware/SpringAwareListener.java	2026-04-22 07:18:33.811354815 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-context/src/main/java/io/micronaut/spring/context/aware/SpringAwareListener.java	2026-04-22 07:16:43.328424914 +0000
@@ -25,7 +25,7 @@
 import io.micronaut.context.event.BeanInitializedEventListener;
 import io.micronaut.context.event.BeanInitializingEvent;
 import io.micronaut.core.annotation.Internal;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.core.naming.NameUtils;
 import io.micronaut.inject.BeanDefinition;
 import io.micronaut.inject.BeanIdentifier;
@@ -124,19 +124,6 @@
     /**
      * Execute when a bean is created.
      *
-     * @param o
-     * @param bean           The bean.
-     * @return The result
-     * @deprecated Use {@link #onBeanCreated(BeanDefinition, Object, String)}
-     */
-    @Deprecated
-    public Object onBeanCreated(Object o, Object bean) {
-        return onBeanCreated(null, bean, null);
-    }
-
-    /**
-     * Execute when a bean is created.
-     *
      * @param beanDefinition The bean definition
      * @param bean           The bean.
      * @param beanName       The bean name
@@ -192,7 +179,6 @@
             beanPostProcessors.addAll(processors);
         }
     }
-
     /**
      * Reset the bean processors.
      */
```

### `spring-context/src/main/java/io/micronaut/spring/context/env/MicronautEnvironment.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-context/src/main/java/io/micronaut/spring/context/env/MicronautEnvironment.java	2026-04-22 07:18:33.811692652 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-context/src/main/java/io/micronaut/spring/context/env/MicronautEnvironment.java	2026-04-22 07:16:43.328733000 +0000
@@ -19,8 +19,8 @@
 import io.micronaut.context.env.EnvironmentPropertySource;
 import io.micronaut.context.env.SystemPropertiesPropertySource;
 import io.micronaut.core.annotation.Internal;
-import io.micronaut.core.annotation.NonNull;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.NonNull;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.core.util.StringUtils;
 import io.micronaut.spring.beans.MicronautContextInternal;
 import jakarta.inject.Singleton;
@@ -141,7 +141,7 @@
      * The target environment.
      * @return The environment
      */
-    public @NonNull io.micronaut.context.env.Environment getEnvironment() {
+    public io.micronaut.context.env.@NonNull Environment getEnvironment() {
         return environment;
     }
 
```

### `spring-context/src/main/java/io/micronaut/spring/context/factory/MicronautBeanFactory.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-context/src/main/java/io/micronaut/spring/context/factory/MicronautBeanFactory.java	2026-04-22 07:18:33.812215240 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-context/src/main/java/io/micronaut/spring/context/factory/MicronautBeanFactory.java	2026-04-22 07:16:43.329277005 +0000
@@ -23,7 +23,8 @@
 import io.micronaut.core.annotation.AnnotationMetadata;
 import io.micronaut.core.annotation.AnnotationUtil;
 import io.micronaut.core.annotation.Internal;
-import io.micronaut.core.annotation.NonNull;
+import io.micronaut.core.reflect.ReflectionUtils;
+import org.jspecify.annotations.NonNull;
 import io.micronaut.core.naming.NameResolver;
 import io.micronaut.core.reflect.InstantiationUtils;
 import io.micronaut.core.util.ArgumentUtils;
@@ -95,9 +96,13 @@
         this.springAwareListener = awareListener;
         this.configuration = configuration;
         this.beanExcludes = configuration.getBeanExcludes();
-        final Collection<BeanDefinitionReference<?>> references = beanContext.getBeanDefinitionReferences();
+        final Collection<BeanDefinitionReference<Object>> references = beanContext.getBeanDefinitionReferences();
 
         for (BeanDefinitionReference<?> reference : references) {
+            // Check if bean type is present and enabled before loading
+            if (!reference.isPresent() || !reference.isEnabled(beanContext)) {
+                continue;
+            }
             final BeanDefinition<?> definition = reference.load(beanContext);
             if (definition instanceof ParametrizedInstantiatableBeanDefinition || (!(definition instanceof InstantiatableBeanDefinition))) {
                 // Spring doesn't have a similar concept. Consider these internal / non-public beans.
@@ -554,7 +559,7 @@
     public @NonNull
     String[] getBeanNamesForAnnotation(@NonNull Class<? extends Annotation> annotationType) {
         final String[] beanNamesForAnnotation = super.getBeanNamesForAnnotation(annotationType);
-        final Collection<BeanDefinition<?>> beanDefinitions = beanContext.getBeanDefinitions(Qualifiers.byStereotype(annotationType));
+        final Collection<BeanDefinition<Object>> beanDefinitions = beanContext.getBeanDefinitions(Qualifiers.byStereotype(annotationType));
         return ArrayUtils.concat(beansToNames(beanDefinitions), beanNamesForAnnotation);
     }
 
@@ -842,6 +847,7 @@
                     () -> InstantiationUtils.instantiate(beanClass)
                 );
             }
+            builder = builder.exposedTypes(ReflectionUtils.getAllClassesInHierarchy(beanClass).toArray(Class<?>[]::new));
             String scope = abstractBeanDefinition.getScope();
             if (scope != null) {
                 if ("prototype".equals(scope)) {
@@ -855,8 +861,7 @@
             builder.qualifier(Qualifiers.byName(beanName));
             beanContext.registerBeanDefinition(builder.build());
             if (BeanPostProcessor.class.isAssignableFrom(beanClass)) {
-                beanContext.getBean(SpringAwareListener.class)
-                    .resetPostProcessors();
+                beanContext.getBean(SpringAwareListener.class).resetPostProcessors();
             }
         }
     }
```

### `spring-context/src/main/java/io/micronaut/spring/context/factory/MicronautBeanFactoryConfiguration.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-context/src/main/java/io/micronaut/spring/context/factory/MicronautBeanFactoryConfiguration.java	2026-04-22 07:18:33.812313782 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-context/src/main/java/io/micronaut/spring/context/factory/MicronautBeanFactoryConfiguration.java	2026-04-22 07:16:43.329387756 +0000
@@ -16,7 +16,7 @@
 package io.micronaut.spring.context.factory;
 
 import io.micronaut.context.annotation.ConfigurationProperties;
-import io.micronaut.core.annotation.NonNull;
+import org.jspecify.annotations.NonNull;
 import io.micronaut.core.util.ArgumentUtils;
 import io.micronaut.spring.beans.MicronautContextInternal;
 
```

### `spring-context/src/test/groovy/io/micronaut/spring/annotation/context/MicronautBeanFactoryConfigurationSpec.groovy`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-context/src/test/groovy/io/micronaut/spring/annotation/context/MicronautBeanFactoryConfigurationSpec.groovy	2026-04-22 07:18:33.813172748 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-context/src/test/groovy/io/micronaut/spring/annotation/context/MicronautBeanFactoryConfigurationSpec.groovy	2026-04-22 07:16:43.330369806 +0000
@@ -15,7 +15,7 @@
  */
 package io.micronaut.spring.annotation.context
 
-import com.fasterxml.jackson.databind.ObjectMapper
+import tools.jackson.databind.ObjectMapper
 import io.micronaut.context.ApplicationContext
 import io.micronaut.spring.context.MicronautApplicationContext
 import org.springframework.beans.factory.NoSuchBeanDefinitionException
```

### `spring-web/build.gradle.kts`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-web/build.gradle.kts	2026-04-22 07:18:33.817423620 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-web/build.gradle.kts	2026-04-22 07:16:43.335039307 +0000
@@ -27,3 +27,4 @@
     testRuntimeOnly(mnViews.micronaut.views.thymeleaf)
     testRuntimeOnly(libs.spring.boot.starter.thymeleaf)
 }
+
```

### `spring-web/src/main/java/io/micronaut/spring/web/ModelAndViewServerFilter.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-web/src/main/java/io/micronaut/spring/web/ModelAndViewServerFilter.java	2026-04-22 07:18:33.817845165 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-web/src/main/java/io/micronaut/spring/web/ModelAndViewServerFilter.java	2026-04-22 07:16:43.335456102 +0000
@@ -22,9 +22,9 @@
 import io.micronaut.http.annotation.Filter;
 import io.micronaut.http.filter.HttpServerFilter;
 import io.micronaut.http.filter.ServerFilterChain;
+import io.micronaut.http.filter.ServerFilterPhase;
 import io.micronaut.spring.web.bind.ModelRequestArgumentBinder;
 import io.micronaut.views.ModelAndView;
-import io.micronaut.views.ViewsFilter;
 import io.micronaut.views.ViewsRenderer;
 import org.reactivestreams.Publisher;
 import org.springframework.ui.Model;
@@ -42,19 +42,15 @@
 @Requires(beans = ViewsRenderer.class)
 public class ModelAndViewServerFilter implements HttpServerFilter {
 
-    private final ViewsFilter viewsFilter;
-
     /**
      * Default constructor.
-     * @param viewsFilter The views filter
      */
-    public ModelAndViewServerFilter(ViewsFilter viewsFilter) {
-        this.viewsFilter = viewsFilter;
+    public ModelAndViewServerFilter() {
     }
 
     @Override
     public int getOrder() {
-        return viewsFilter.getOrder() + 10;
+        return ServerFilterPhase.RENDERING.order() + 10;
     }
 
     @Override
```

### `spring-web/src/main/java/io/micronaut/spring/web/ResponseEntityServerFilter.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-web/src/main/java/io/micronaut/spring/web/ResponseEntityServerFilter.java	2026-04-22 07:18:33.817944708 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-web/src/main/java/io/micronaut/spring/web/ResponseEntityServerFilter.java	2026-04-22 07:16:43.335532728 +0000
@@ -27,8 +27,6 @@
 import org.springframework.http.HttpHeaders;
 import org.springframework.http.ResponseEntity;
 
-import java.util.List;
-import java.util.Map;
 
 /**
  * A filter that adds support for {@link ResponseEntity} as a return type.
@@ -50,15 +48,13 @@
                 }
                 final HttpHeaders headers = entity.getHeaders();
                 final MutableHttpHeaders micronautHeaders = mutableHttpResponse.getHeaders();
-                for (Map.Entry<String, List<String>> entry : headers.entrySet()) {
-                    final String key = entry.getKey();
-                    final List<String> value = entry.getValue();
+                headers.forEach((key, value) -> {
                     for (String v : value) {
                         if (v != null) {
                             micronautHeaders.add(key, v);
                         }
                     }
-                }
+                });
                 final Object b = entity.getBody();
                 if (b != null) {
                     mutableHttpResponse.body(b);
```

### `spring-web/src/test/java/io/micronaut/spring/web/annotation/GreetingController.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-web/src/test/java/io/micronaut/spring/web/annotation/GreetingController.java	2026-04-22 07:18:33.820007143 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-web/src/test/java/io/micronaut/spring/web/annotation/GreetingController.java	2026-04-22 07:16:43.337489953 +0000
@@ -42,8 +42,6 @@
 import java.nio.charset.StandardCharsets;
 import java.util.concurrent.atomic.AtomicLong;
 
-import static org.junit.Assert.assertEquals;
-
 @RestController
 @Validated
 public class GreetingController {
@@ -65,10 +63,9 @@
 
     @PostMapping("/request")
     public Flux<String> request(ServerHttpRequest request, HttpMethod method) {
-        assertEquals("/request", request.getPath().value());
-        assertEquals(HttpMethod.POST, request.getMethod());
-        assertEquals(HttpMethod.POST, method);
-        assertEquals("Bar", request.getHeaders().getFirst("Foo"));
+        assert "/request".equals(request.getPath().value());
+        assert HttpMethod.POST.equals(request.getMethod());
+        assert "Bar".equals(request.getHeaders().getFirst("Foo"));
         return request.getBody().map(dataBuffer -> {
             var bytes = new byte[dataBuffer.readableByteCount()];
             dataBuffer.read(bytes);
```

### `spring-web/src/test/java/io/micronaut/spring/web/annotation/exchange/ExchangeGreetingController.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-web/src/test/java/io/micronaut/spring/web/annotation/exchange/ExchangeGreetingController.java	2026-04-22 07:18:33.820460480 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-web/src/test/java/io/micronaut/spring/web/annotation/exchange/ExchangeGreetingController.java	2026-04-22 07:16:43.337837790 +0000
@@ -30,8 +30,6 @@
 import java.util.HashMap;
 import java.util.concurrent.atomic.AtomicLong;
 
-import static org.junit.Assert.assertEquals;
-
 @RestController
 @RequestMapping("/exchange")
 public class ExchangeGreetingController implements ExchangeGreetingApi {
@@ -84,10 +82,10 @@
 
     @PostExchange("/request")
     public Flux<String> request(ServerHttpRequest request, HttpMethod method) {
-        assertEquals("/exchange/request", request.getPath().value());
-        assertEquals(HttpMethod.POST, request.getMethod());
-        assertEquals(HttpMethod.POST, method);
-        assertEquals("Bar", request.getHeaders().getFirst("Foo"));
+        assert "/exchange/request".equals(request.getPath().value());
+        assert HttpMethod.POST.equals(request.getMethod());
+        assert HttpMethod.POST.equals(method);
+        assert "Bar".equals(request.getHeaders().getFirst("Foo"));
         return request.getBody().map(dataBuffer -> {
             var bytes = new byte[dataBuffer.readableByteCount()];
             dataBuffer.read(bytes);
```

### `spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/CookieValueAnnotationMapper.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/CookieValueAnnotationMapper.java	2026-04-22 07:18:33.815359268 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/CookieValueAnnotationMapper.java	2026-04-22 07:16:43.332910579 +0000
@@ -16,7 +16,7 @@
 package io.micronaut.spring.web.annotation;
 
 import io.micronaut.core.annotation.AnnotationValue;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.http.annotation.CookieValue;
 import io.micronaut.inject.visitor.VisitorContext;
 import io.micronaut.spring.annotation.AbstractSpringAnnotationMapper;
```

### `spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/PathVariableAnnotationMapper.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/PathVariableAnnotationMapper.java	2026-04-22 07:18:33.815755771 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/PathVariableAnnotationMapper.java	2026-04-22 07:16:43.333273624 +0000
@@ -16,7 +16,7 @@
 package io.micronaut.spring.web.annotation;
 
 import io.micronaut.core.annotation.AnnotationValue;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.http.annotation.PathVariable;
 import io.micronaut.inject.visitor.VisitorContext;
 import io.micronaut.spring.annotation.AbstractSpringAnnotationMapper;
```

### `spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/RequestAttributeAnnotationMapper.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/RequestAttributeAnnotationMapper.java	2026-04-22 07:18:33.815960648 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/RequestAttributeAnnotationMapper.java	2026-04-22 07:16:43.333501751 +0000
@@ -16,7 +16,7 @@
 package io.micronaut.spring.web.annotation;
 
 import io.micronaut.core.annotation.AnnotationValue;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.http.annotation.RequestAttribute;
 import io.micronaut.inject.visitor.VisitorContext;
 import io.micronaut.spring.annotation.AbstractSpringAnnotationMapper;
```

### `spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/RequestBodyAnnotationMapper.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/RequestBodyAnnotationMapper.java	2026-04-22 07:18:33.816022607 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/RequestBodyAnnotationMapper.java	2026-04-22 07:16:43.333573543 +0000
@@ -16,7 +16,7 @@
 package io.micronaut.spring.web.annotation;
 
 import io.micronaut.core.annotation.AnnotationValue;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.core.bind.annotation.Bindable;
 import io.micronaut.http.annotation.Body;
 import io.micronaut.inject.visitor.VisitorContext;
```

### `spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/RequestHeaderAnnotationMapper.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/RequestHeaderAnnotationMapper.java	2026-04-22 07:18:33.816112775 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/RequestHeaderAnnotationMapper.java	2026-04-22 07:16:43.333662544 +0000
@@ -16,7 +16,7 @@
 package io.micronaut.spring.web.annotation;
 
 import io.micronaut.core.annotation.AnnotationValue;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.http.annotation.Header;
 import io.micronaut.inject.visitor.VisitorContext;
 import io.micronaut.spring.annotation.AbstractSpringAnnotationMapper;
```

### `spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/RequestMappingAnnotationTransformer.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/RequestMappingAnnotationTransformer.java	2026-04-22 07:18:33.816202900 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/RequestMappingAnnotationTransformer.java	2026-04-22 07:16:43.333745545 +0000
@@ -17,8 +17,8 @@
 
 import io.micronaut.core.annotation.AnnotationValue;
 import io.micronaut.core.annotation.AnnotationValueBuilder;
-import io.micronaut.core.annotation.NonNull;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.NonNull;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.core.util.ArrayUtils;
 import io.micronaut.http.HttpMethod;
 import io.micronaut.http.annotation.Consumes;
```

### `spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/RequestParamAnnotationMapper.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/RequestParamAnnotationMapper.java	2026-04-22 07:18:33.816287818 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/RequestParamAnnotationMapper.java	2026-04-22 07:16:43.333812587 +0000
@@ -16,7 +16,7 @@
 package io.micronaut.spring.web.annotation;
 
 import io.micronaut.core.annotation.AnnotationValue;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.http.annotation.QueryValue;
 import io.micronaut.inject.visitor.VisitorContext;
 import io.micronaut.spring.annotation.AbstractSpringAnnotationMapper;
```

### `spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/RequestPartAnnotationMapper.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/RequestPartAnnotationMapper.java	2026-04-22 07:18:33.816358902 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/RequestPartAnnotationMapper.java	2026-04-22 07:16:43.333899338 +0000
@@ -16,7 +16,7 @@
 package io.micronaut.spring.web.annotation;
 
 import io.micronaut.core.annotation.AnnotationValue;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.http.annotation.Part;
 import io.micronaut.inject.visitor.VisitorContext;
 import io.micronaut.spring.annotation.AbstractSpringAnnotationMapper;
```

### `spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/WebBindAnnotationMapper.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/WebBindAnnotationMapper.java	2026-04-22 07:18:33.816557612 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/WebBindAnnotationMapper.java	2026-04-22 07:16:43.334134715 +0000
@@ -18,7 +18,7 @@
 import io.micronaut.core.annotation.AnnotationUtil;
 import io.micronaut.core.annotation.AnnotationValue;
 import io.micronaut.core.annotation.AnnotationValueBuilder;
-import io.micronaut.core.annotation.NonNull;
+import org.jspecify.annotations.NonNull;
 import io.micronaut.core.bind.annotation.Bindable;
 import io.micronaut.core.util.StringUtils;
 import io.micronaut.inject.visitor.VisitorContext;
```

### `spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/exchange/HttpExchangeAnnotationTransformer.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/exchange/HttpExchangeAnnotationTransformer.java	2026-04-22 07:18:33.816810614 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/exchange/HttpExchangeAnnotationTransformer.java	2026-04-22 07:16:43.334417093 +0000
@@ -17,8 +17,8 @@
 
 import io.micronaut.core.annotation.AnnotationValue;
 import io.micronaut.core.annotation.AnnotationValueBuilder;
-import io.micronaut.core.annotation.NonNull;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.NonNull;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.core.util.ArrayUtils;
 import io.micronaut.core.util.StringUtils;
 import io.micronaut.http.annotation.Consumes;
```

### `src/main/docs/guide/toc.yml`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-spring/src/main/docs/guide/toc.yml	2026-04-22 07:18:33.825980280 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-spring/src/main/docs/guide/toc.yml	2026-04-22 07:16:43.344086304 +0000
@@ -21,4 +21,5 @@
   beanPostProcessor:
     title: Using a Bean Post Processor
 springGuides: Guides
+breaks: Breaking Changes
 repository: Repository
```

---

_Report generated by git-branch-diff skill._
