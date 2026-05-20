 Compared micronaut-opensearch as mn4 → mn5.

  Scope

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-opensearch, branch 1.7.x, SHA 8d07ae8
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-opensearch, branch 2.0.x, SHA 352dd7f
  - Report: /private/tmp/micronaut-opensearch-1.7-to-2.0-comparison.md

  Key Findings

  - Major baseline move: project 1.7.0-SNAPSHOT → 2.0.1-SNAPSHOT, Micronaut 4.10.4 → 5.0.0, platform 4.8.3 →
    5.0.0-RC1, Gradle wrapper 8.14.3 → 9.5.1, plus .sdkmanrc pinned to java=25.0.1-graal.
  - OpenSearch dependencies were upgraded substantially: Java client 2.26.0 → 3.8.0, REST client 2.19.3 →
    3.6.0, Testcontainers OpenSearch 2.1.4 → 4.1.0, HttpClient5 5.5.1 → 5.6.1.
  - REST client internals moved from old Apache org.apache.http.* imports to HttpComponents 5
    org.apache.hc.*; OpenSearchTransport construction no longer injects Micronaut/Jackson ObjectMapper and
    now uses new JacksonJsonpMapper().
  - Dependency hardening was added for Jackson core/databind 2.21.1 and HttpClient5, with comments
    referencing upstream vulnerability constraints.
  - Native image metadata was added for opensearch-httpclient5, opensearch-restclient, and test reflection
    config.
  - Test resources changed from Micronaut Test Resources provider registration to an explicit OpenSearch
    Testcontainers helper exposed through TestPropertyProvider; casing was updated to OpenSearchContainer.
  - Companion Micronaut BOMs were moved to the 5-compatible line: AWS, Kotlin, Serde, Validation, and Test.

  Diff size: 89 files changed, 3920 insertions(+), 363 deletions(-).

  I did not run tests; this was a folder comparison only.
# Release Note Comparison

Generated: 2026-05-19 10:56 UTC
Comparison: `1.7.x` -> `2.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-opensearch` | `1.7.x` | `8d07ae8647c3` | `git@github.com:micronaut-projects/micronaut-opensearch.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-opensearch` | `2.0.x` | `352dd7f56e16` | `git@github.com:micronaut-projects/micronaut-opensearch.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-opensearch`
- Commit candidates found: 60
- File changes listed: 89
- Version values listed: 38
- File status counts: A=29, D=4, M=56

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `1.7.0-SNAPSHOT` | `2.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.awaitility` | `org.awaitility:awaitility:4.3.0` | `org.awaitility:awaitility:4.3.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.gradle-micronaut` | `io.micronaut.gradle:micronaut-gradle-plugin:4.5.5` | `io.micronaut.gradle:micronaut-gradle-plugin:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.kotlin-reflect` | `org.jetbrains.kotlin:kotlin-reflect:1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.kotlin-stdlib-jdk8` | `org.jetbrains.kotlin:kotlin-stdlib-jdk8:1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.managed-apache-httpcomponents-httpclient5` | `org.apache.httpcomponents.client5:httpclient5:5.5.1` | `org.apache.httpcomponents.client5:httpclient5:5.6.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-jackson-core` | `not present` | `com.fasterxml.jackson.core:jackson-core:2.21.1` | `added` |
| `gradle/libs.versions.toml` | `libraries.managed-jackson-databind` | `not present` | `com.fasterxml.jackson.core:jackson-databind:2.21.1` | `added` |
| `gradle/libs.versions.toml` | `libraries.managed-opensearch-java` | `org.opensearch.client:opensearch-java:2.26.0` | `org.opensearch.client:opensearch-java:3.8.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-opensearch-rest-client` | `org.opensearch.client:opensearch-rest-client:2.19.3` | `org.opensearch.client:opensearch-rest-client:3.6.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-opensearch-testcontainers` | `org.opensearch:opensearch-testcontainers:2.1.4` | `org.opensearch:opensearch-testcontainers:4.1.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-aws` | `io.micronaut.aws:micronaut-aws-bom:4.11.0` | `io.micronaut.aws:micronaut-aws-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-kotlin` | `io.micronaut.kotlin:micronaut-kotlin-bom:4.7.0` | `io.micronaut.kotlin:micronaut-kotlin-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.15.5` | `io.micronaut.serde:micronaut-serde-bom:3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test` | `not present` | `io.micronaut.test:micronaut-test-bom:5.0.0` | `added` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-resources` | `io.micronaut.testresources:micronaut-test-resources-bom:2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-validation` | `io.micronaut.validation:micronaut-validation-bom:4.11.0` | `io.micronaut.validation:micronaut-validation-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.awaitility` | `4.3.0` | `4.3.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.kotlin` | `1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.managed-apache-httpcomponents-httpclient5` | `5.5.1` | `5.6.1` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-jackson` | `not present` | `2.21.1` | `added` |
| `gradle/libs.versions.toml` | `versions.managed-opensearch-java` | `2.26.0` | `3.8.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-opensearch-rest-client` | `2.19.3` | `3.6.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-opensearch-testcontainers` | `2.1.4` | `4.1.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.4` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-aws` | `4.11.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.5.5` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-kotlin` | `4.7.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-platform` | `4.8.3` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.15.5` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.7.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test-resources` | `2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.11.0` | `5.0.0` | `changed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |
| `settings.gradle.kts` | `plugin.io.micronaut.build.shared.settings` | `7.6.4` | `8.0.0-M18` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Fixes

- `256c065c422b` fix(deps): update dependency org.apache.httpcomponents.client5:httpclient5 to v5.6.1 (#248) (renovate[bot], 2026-05-08)
- `4414eddec365` fix(deps): update dependency org.opensearch.client:opensearch-java to v3.8.0 (#256) (renovate[bot], 2026-05-08)
- `d51356185c85` fix(deps): update dependency org.opensearch.client:opensearch-rest-client to v3.6.0 (#257) (renovate[bot], 2026-05-08)
- `290c77ed35f1` fix(deps): update dependency org.opensearch:opensearch-testcontainers to v4 (#239) (renovate[bot], 2026-05-08)
- `29c36070f094` fix(deps): update micronaut dependencies (#270) (renovate[bot], 2026-05-08)
- `e54170cae895` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m23 (#268) (renovate[bot], 2026-04-21)
- `2cedc663cd36` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m19 (#267) (renovate[bot], 2026-04-02)
- `5db9d700fa64` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m5 (#266) (renovate[bot], 2026-04-01)
- `18fe11251599` fix(deps): update dependency io.micronaut.test:micronaut-test-bom to v5.0.0-m7 (#263) (renovate[bot], 2026-04-01)
- `b497310997f1` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m18 (#259) (renovate[bot], 2026-03-27)
- `325954639b8e` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.1 (#227) (renovate[bot], 2025-12-10)
- `c9a96b645424` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.12.0 (#229) (renovate[bot], 2025-12-10)
- `b7cc9e728ae8` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#228) (renovate[bot], 2025-12-10)
- `b706f9c21833` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#224) (renovate[bot], 2025-12-10)
- `19cc3d0968dc` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.6 (#218) (renovate[bot], 2025-10-17)

### Dependency Updates

- `7e84d0e003e4` chore: Bump version to 2.0.1-SNAPSHOT (micronaut-build, 2026-05-18)
- `b698c1fc5fd9` chore: Bump version to 2.0.0-SNAPSHOT (micronaut-build, 2026-05-08)
- `e87e80ad4444` Constrain vulnerable OpenSearch transitive dependencies (Sergio del Amo, 2026-05-08)
- `cf68ec471712` chore(deps): update dependency org.bouncycastle:bc-fips to v2.1.2 (#254) (renovate[bot], 2026-05-08)
- `1029defadcfd` chore(deps): update gradle to v9.5.0 (#262) (renovate[bot], 2026-05-08)
- `6c0ffcac3d2f` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#258) (renovate[bot], 2026-04-01)
- `04dbe1ac53a9` chore: Bump version to 2.0.0-SNAPSHOT (micronaut-build, 2026-02-12)
- `91039f84375b` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m16 (#247) (renovate[bot], 2026-02-12)
- `a1cb41639c19` chore(deps): update stefanzweifel/git-auto-commit-action action to v7 (#236) (renovate[bot], 2025-12-10)
- `0de9d335b07b` chore(deps): update actions/checkout action (#232) (renovate[bot], 2025-12-10)
- `6ba68b686ad5` chore(deps): update gradle to v9.2.1 (#226) (renovate[bot], 2025-12-10)
- `6fbcac7a60f4` chore(deps): update softprops/action-gh-release action to v2.5.0 (#225) (renovate[bot], 2025-12-10)
- `04239d598be3` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#223) (renovate[bot], 2025-12-10)
- `7cb6e8a5ba12` chore(deps): update graalvm/setup-graalvm action to v1.4.3 (#222) (renovate[bot], 2025-11-28)

### Internal

- `823bc27103ab` ci: projectVersion=2.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-06-17)

### Review Candidates

- `352dd7f56e16` micronaut-aws = "5.0.0" (Sergio del Amo, 2026-05-19)
- `7e0d8a55e122` [skip ci] Release v2.0.0 (micronaut-build, 2026-05-18)
- `3b00cd6e2d87` sourceCompatibility 25 (Sergio del Amo, 2026-05-18)
- `e242bf8e2318` Update common files (#277) (micronaut-build, 2026-05-18)
- `0f709215bc9a` update versions (Sergio del Amo, 2026-05-18)
- `59cfef4577ee` Update mikepenz/action-junit-report digest to 3a81627 (#276) (renovate[bot], 2026-05-18)
- `7a45dd474741` Update common files (#275) (micronaut-build, 2026-05-18)
- `0b552e6b5d70` micronaut-platform = "5.0.0-RC1" (Sergio del Amo, 2026-05-13)
- `7b914376fb99` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `6577abb995bc` Update common files (#274) (micronaut-build, 2026-05-09)
- `50652ed3e9d4` [skip ci] Release v2.0.0-RC1 (micronaut-build, 2026-05-08)
- `84176cbc3902` enable binary compatibility (Sergio del Amo, 2026-05-08)
- `dbdf2eb972a3` change casing of OpenSearchContainer (Sergio del Amo, 2026-05-08)
- `afc53c9f40c4` update versions (Sergio del Amo, 2026-05-08)
- `56742d00f2ad` Update common files (#272) (micronaut-build, 2026-05-08)
- `c8cfc859d987` Merge pull request #261 from micronaut-projects/sync-files-2.0.x (Graeme Rocher, 2026-04-26)
- `84f2ed5c5532` Update common files (micronaut-build, 2026-04-21)
- `4aa9ed2a0357` [skip ci] Release v2.0.0-M1 (micronaut-build, 2026-02-12)
- `9fe9c75ded4a` Fix native build for jdk 25 (#255) (issam liqali, 2026-02-11)
- `010005f4b912` update to opensearch-rest-client 3.4.0 (#253) (issam liqali, 2026-02-06)
- `9291b65fd830` Update to opensearch-java 3.5.0 (#252) (issam liqali, 2026-02-06)
- `0df4fcb10e0c` Update to Micronaut 5 (#246) (issam liqali, 2026-02-03)
- `7b47a26b9dc9` Update common files (#220) (micronaut-build, 2025-12-10)
- `0a28d5f28822` Replace Micronaut nullability annotations with JSpecify annotations (#238) (Copilot, 2025-12-02)
- `664ef1b6fe9e` Update common files (#219) (micronaut-build, 2025-10-20)
- `77b47ab25d8f` Update common files (#217) (micronaut-build, 2025-10-17)
- `4954379aa4b7` OpenSearch 3 (#191) (Sergio del Amo, 2025-10-14)
- `0f338a5bfc2e` Micronaut Gradle build plugin 8.0.0-M4 (Sergio del Amo, 2025-10-14)
- `cb33f1f74d48` gradle 9.1 (Sergio del Amo, 2025-10-14)
- `0fe60abc5839` Merge branch '1.7.x' into 2.0.x (Sergio del Amo, 2025-10-14)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` .github/workflows/update-gradle-wrapper.yml
- `M` buildSrc/build.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.opensearch-module.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` opensearch-amazon/build.gradle.kts
- `M` opensearch-bom/build.gradle.kts
- `M` opensearch-httpclient5/build.gradle.kts
- `M` opensearch-restclient/build.gradle.kts
- `M` opensearch/build.gradle.kts
- `M` settings.gradle.kts
- `M` test-suite-groovy/build.gradle.kts
- `M` test-suite-httpclient5/build.gradle.kts
- `M` test-suite-kotlin/build.gradle.kts
- `M` test-suite-opensearch-container/build.gradle.kts
- `M` test-suite/build.gradle.kts

### Documentation

- `A` .agents/skills/docs/SKILL.md
- `A` .agents/skills/docs/references/control-panel-patterns.md
- `A` .agents/skills/docs/references/micronaut-docs-providers.md
- `A` .agents/skills/guides/SKILL.md
- `A` .agents/skills/guides/references/guide-authoring-conventions.md
- `A` .agents/skills/guides/references/guide-inventory.md
- `A` .agents/skills/guides/references/pdf-export-and-pr.md
- `A` .agents/skills/guides/references/repository-workflow.md
- `M` .github/workflows/release.yml

### Source

- `A` .agents/skills/agent-md-refactor/SKILL.md
- `A` .agents/skills/agent-md-refactor/references/examples-and-anti-patterns.md
- `A` .agents/skills/agent-md-refactor/references/refactor-playbook.md
- `A` .agents/skills/coding/SKILL.md
- `A` .agents/skills/micronaut-sourcegen/SKILL.md
- `A` .agents/skills/micronaut-sourcegen/references/sourcegen-cookbook.md
- `A` .agents/skills/skill-creator/SKILL.md
- `A` .agents/skills/skill-creator/references/research-synthesis.md
- `A` .agents/skills/skill-creator/references/templates.md
- `M` .clineignore
- `M` .clinerules/coding.md
- `M` .github/instructions/coding.instructions.md
- `M` .github/renovate.json
- `A` .github/scripts/vulnerability-audit-filter.py
- `A` .github/scripts/vulnerability-audit.sh
- `M` .github/workflows/central-sync.yml
- `M` .github/workflows/graalvm-dev.yml
- `M` .github/workflows/publish-snapshot.yml
- `A` .github/workflows/sonatype.yml
- `M` .gitignore
- `A` .sdkmanrc
- `M` MAINTAINING.md
- `M` config/checkstyle/checkstyle.xml
- `A` opensearch-httpclient5/src/main/resources/META-INF/native-image/io.micronaut.opensearch.httpclient5/native-image.properties
- `M` opensearch-restclient/src/main/java/io/micronaut/opensearch/restclient/RestClientFactory.java
- `M` opensearch-restclient/src/main/java/io/micronaut/opensearch/restclient/conf/RestClientOpenSearchConfiguration.java
- `M` opensearch-restclient/src/main/java/io/micronaut/opensearch/restclient/conf/RestClientOpenSearchConfigurationProperties.java
- `M` opensearch-restclient/src/main/java/io/micronaut/opensearch/restclient/converter/RestClientTypeConverterRegistrar.java
- `M` opensearch-restclient/src/main/java/io/micronaut/opensearch/restclient/converter/StringToHeaderConverter.java
- `M` opensearch-restclient/src/main/java/io/micronaut/opensearch/restclient/converter/StringToHttpHostConverter.java
- `A` opensearch-restclient/src/main/resources/META-INF/native-image/io.micronaut.opensearch.restclient/micronaut-opensearch-restclient/native-image.properties
- `M` opensearch/src/main/java/io/micronaut/opensearch/health/OpenSearchClientHealthIndicator.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` opensearch-restclient/src/test/java/io/micronaut/opensearch/restclient/RestClientFactoryTest.java
- `M` opensearch-restclient/src/test/java/io/micronaut/opensearch/restclient/conf/RestClientOpenSearchConfigurationTest.java
- `M` opensearch-restclient/src/test/java/io/micronaut/opensearch/restclient/converter/StringToHeaderConverterTest.java
- `M` opensearch-restclient/src/test/java/io/micronaut/opensearch/restclient/converter/StringToHttpHostConverterTest.java
- `M` opensearch/src/test/java/io/micronaut/opensearch/health/OpenSearchClientHealthIndicatorTest.java
- `M` test-suite-groovy/src/test/groovy/micronaut/example/HealthSpec.groovy
- `M` test-suite-groovy/src/test/groovy/micronaut/example/OpenSearchSpec.groovy
- `M` test-suite-httpclient5/src/test/java/micronaut/example/HealthTest.java
- `M` test-suite-httpclient5/src/test/java/micronaut/example/OpenSearchTest.java
- `D` test-suite-httpclient5/src/testResources/java/io/micronaut/opensearch/Http5ClientOpenSearchTestResourceProvider.java
- `D` test-suite-httpclient5/src/testResources/resources/META-INF/services/io.micronaut.testresources.core.TestResourcesResolver
- `M` test-suite-kotlin/src/test/kotlin/micronaut/example/HealthTest.kt
- `M` test-suite-kotlin/src/test/kotlin/micronaut/example/OpenSearchTest.kt
- `M` test-suite-kotlin/src/test/kotlin/micronaut/example/service/Movie.kt
- `M` test-suite-kotlin/src/test/kotlin/micronaut/example/service/MovieServiceImpl.kt
- `A` test-suite-opensearch-container/src/main/java/io/micronaut/opensearch/testresources/OpenSearch.java
- `D` test-suite-opensearch-container/src/main/java/io/micronaut/opensearch/testresources/OpenSearchTestResourceProvider.java
- `M` test-suite/src/test/java/micronaut/example/HealthTest.java
- `M` test-suite/src/test/java/micronaut/example/OpenSearchTest.java
- `M` test-suite/src/test/java/micronaut/example/service/Movie.java
- `A` test-suite/src/test/resources/META-INF/native-image/reflect-config.json
- `D` test-suite/src/testResources/resources/META-INF/services/io.micronaut.testresources.core.TestResourcesResolver

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

