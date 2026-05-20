Compared micronaut-jaxrs as mn4 → mn5.

  Scope

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-jaxrs, branch 4.10.x, SHA 72f39f6
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-jaxrs, branch 5.0.x, SHA 8c8b86c
  - Report: /private/tmp/micronaut-jaxrs-4.10-to-5.0-comparison.md

  Key Findings

  - projectVersion moves from 4.10.1-SNAPSHOT to 5.0.1-SNAPSHOT.
  - Core platform moves to Micronaut 5.0.0; Gradle wrapper moves 8.14.3 → 9.5.1; Java 25.0.1-graal is added
    via .sdkmanrc.
  - Jakarta REST API moves jakarta.ws.rs-api 3.1.0 → 4.0.0; TCK version remains 4.0.1.
  - Micronaut integrations move forward: Security 4.15.0 → 5.0.0, Servlet 5.5.1 → 6.0.0, Serde 2.15.5 → 3.0.0,
    Validation 4.11.0 → 5.0.0, Logging 1.7.1 → 2.0.0.
  - jaxrs-client now adds a Micronaut Reactor implementation dependency.
  - Public/internal nullability annotations were migrated from Micronaut annotations to JSpecify.
  - Processor and qualifier code was adjusted for Micronaut 5 APIs, including QualifiedBeanType filtering.
  - JAX-RS TCK exclusions were expanded for several Jakarta REST 4.0.1 tests.
  - CI/release common files were refreshed, including Java 25 CI and OSV/CycloneDX vulnerability audit scripts.

  Diff size: 98 files changed, 3785 insertions, 231 deletions. I did not run tests; this was a folder
  comparison only.

# Release Note Comparison

Generated: 2026-05-19 10:12 UTC
Comparison: `4.10.x` -> `5.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-jaxrs` | `4.10.x` | `72f39f6f79e3` | `git@github.com:micronaut-projects/micronaut-jaxrs.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-jaxrs` | `5.0.x` | `8c8b86c93729` | `git@github.com:micronaut-projects/micronaut-jaxrs.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-jaxrs`
- Commit candidates found: 67
- File changes listed: 98
- Version values listed: 20
- File status counts: A=25, M=73

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `4.10.1-SNAPSHOT` | `5.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.jakarta-jaxrs-tck-tests` | `jakarta-jaxrs-tck-tests:4.0.1` | `jakarta-jaxrs-tck-tests:4.0.1` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-jaxrs-api` | `jakarta.ws.rs:jakarta.ws.rs-api:3.1.0` | `jakarta.ws.rs:jakarta.ws.rs-api:4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-security` | `io.micronaut.security:micronaut-security-bom:4.15.0` | `io.micronaut.security:micronaut-security-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.15.5` | `io.micronaut.serde:micronaut-serde-bom:3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-servlet` | `io.micronaut.servlet:micronaut-servlet-bom:5.5.1` | `io.micronaut.servlet:micronaut-servlet-bom:6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-validation` | `io.micronaut.validation:micronaut-validation-bom:4.11.0` | `io.micronaut.validation:micronaut-validation-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.jakarta-jaxrs-tck` | `4.0.1` | `4.0.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-jaxrs-api` | `3.1.0` | `4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.5` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `2.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.1` | `2.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-reactor` | `not present` | `4.0.0` | `added` |
| `gradle/libs.versions.toml` | `versions.micronaut-security` | `4.15.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.15.5` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-servlet` | `5.5.1` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.9.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.11.0` | `5.0.0` | `changed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `94a8920fe6b2` del PackageConfigurationInjectProcessor it was removed in Core M5 (Sergio del Amo, 2025-12-05)

### Features

- `bd5d971acf59` add micronautBuild description (Sergio del Amo, 2025-12-05)

### Fixes

- `e514d7db382a` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m6 (#606) (renovate[bot], 2025-12-31)
- `ae5a3b8687bf` fix(deps): update dependency io.micronaut.security:micronaut-security-bom to v4.16.1 (#610) (renovate[bot], 2025-12-31)
- `85b0391196e9` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.12.0 (#596) (renovate[bot], 2025-12-05)
- `9bf8f49682fe` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#590) (renovate[bot], 2025-12-05)
- `411bed558896` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#593) (renovate[bot], 2025-12-05)
- `d8e6e51bd45c` fix(deps): update dependency io.micronaut.servlet:micronaut-servlet-bom to v5.6.0 (#594) (renovate[bot], 2025-12-05)
- `3e37420978ee` fix(deps): update dependency io.micronaut.security:micronaut-security-bom to v4.16.0 (#603) (renovate[bot], 2025-12-05)
- `591ed31d7b62` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.6 (#585) (renovate[bot], 2025-10-17)

### Dependency Updates

- `95ccff42959b` chore: Bump version to 5.0.1-SNAPSHOT (micronaut-build, 2026-05-14)
- `fd5edb7598a4` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-05-05)
- `e1495179eeae` Update Micronaut dependencies (#627) (renovate[bot], 2026-05-05)
- `c82b5fc8bcff` Update dependency jakarta.ws.rs:jakarta.ws.rs-api to v4 (#630) (renovate[bot], 2026-05-05)
- `32973fd491ad` Update dependency io.micronaut.servlet:micronaut-servlet-bom to v6.0.0-M2 (#620) (renovate[bot], 2026-04-16)
- `b45dcba73425` Update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-M6 (#617) (renovate[bot], 2026-04-16)
- `c572757d7f43` Update dependency io.micronaut:micronaut-core-bom to v5.0.0-M22 (#616) (renovate[bot], 2026-04-16)
- `556b13424faa` chore(deps): update gradle to v9.4.1 (#618) (renovate[bot], 2026-04-16)
- `7256b578e42a` chore(deps): update gradle/actions action to v6 (#625) (renovate[bot], 2026-04-16)
- `2919ee94020f` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2025-12-31)
- `c0528f003205` chore(deps): update actions/cache action to v5 (#607) (renovate[bot], 2025-12-31)
- `67f84852f561` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m13 (#608) (renovate[bot], 2025-12-31)
- `41a915bf859c` chore(deps): update github artifact actions (#609) (renovate[bot], 2025-12-31)
- `8c3161380adc` chore(deps): update graalvm/setup-graalvm action to v1.4.4 (#587) (renovate[bot], 2025-12-05)
- `d85cb785ae79` chore(deps): update github artifact actions (#598) (renovate[bot], 2025-12-05)
- `7786d15cb7fe` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#589) (renovate[bot], 2025-12-05)
- `2c39e812364a` chore(deps): update gradle/actions action to v5 (#599) (renovate[bot], 2025-12-05)
- `2a840b65cde4` chore(deps): update mikepenz/action-junit-report action to v6 (#600) (renovate[bot], 2025-12-05)
- `91b7ff2667a5` chore(deps): update softprops/action-gh-release action to v2.5.0 (#592) (renovate[bot], 2025-12-05)
- `e3b7dd24cc83` chore(deps): update gradle to v9.2.1 (#591) (renovate[bot], 2025-12-05)
- `4436eeb6f3ee` chore(deps): update actions/checkout action to v6 (#597) (renovate[bot], 2025-12-05)

### Documentation

- `70fcefc78c37` Docs: update micronaut-docs to 3.0.0 (#583) (issam liqali, 2025-10-16)

### Internal

- `3fe54b3b38a6` ci: projectVersion=5.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-10-13)

### Review Candidates

- `8c8b86c93729` Update common files (#635) (micronaut-build, 2026-05-19)
- `ba9cef05b2fc` update versions (Sergio del Amo, 2026-05-18)
- `14205479a1a9` micronaut-servlet = "6.0.0" (Sergio del Amo, 2026-05-14)
- `787dad5ddb40` [skip ci] Release v5.0.0 (micronaut-build, 2026-05-14)
- `2a7034a2b77c` Update versions (Sergio del Amo, 2026-05-14)
- `87404e8ad64d` Update common files (#633) (micronaut-build, 2026-05-14)
- `bf9ed5b7c3ed` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `bb831924ac8e` Update common files (#632) (micronaut-build, 2026-05-09)
- `7a9a888817aa` [skip ci] Release v5.0.0-RC1 (micronaut-build, 2026-05-05)
- `0a2774423dd4` Update Gradle to v9.5.0 (#628) (renovate[bot], 2026-05-05)
- `f4351563b7fe` Update common files (#629) (micronaut-build, 2026-05-05)
- `d71294e98ecd` fix compilation error on 5.0.x branch (#631) (Graeme Rocher, 2026-05-05)
- `a859a9a64d5d` Update common files (#626) (micronaut-build, 2026-04-26)
- `41b0ce996302` micronaut-reactor = "4.0.0-M2" (Sergio del Amo, 2026-04-16)
- `c5e2bd661f98` micronaut-logging = "2.0.0-M2" (Sergio del Amo, 2026-04-16)
- `b244c4f2f709` Update plugin io.micronaut.build.shared.settings to v8.0.0-M17 (#615) (renovate[bot], 2026-04-16)
- `6cb9691d7328` Update common files (#623) (micronaut-build, 2026-04-16)
- `c0a32a69f957` Update softprops/action-gh-release action to v2.6.2 (#624) (renovate[bot], 2026-04-16)
- `c5183aa93c36` Update common files (#614) (micronaut-build, 2026-03-12)
- `ee20e3d8d79c` [skip ci] Release v5.0.0-M1 (micronaut-build, 2025-12-31)
- `cb3b239a2f80` Update common files (#611) (micronaut-build, 2025-12-31)
- `6982f8e40518` Revert "adding reactor is necessary to compile" (#604) (Sergio del Amo, 2025-12-31)
- `6fadabcb616e` Update common files (#605) (micronaut-build, 2025-12-31)
- `344879b38403` adding reactor is necessary to compile (Sergio del Amo, 2025-12-05)
- `0753b32f0b37` fix Jspecify nullability annotations placement (Sergio del Amo, 2025-12-05)
- `e9fd7c1c0c91` micronaut-test = "4.7.0" (Sergio del Amo, 2025-12-05)
- `03c11346773a` micronaut-serde = "3.0.0-M1" (Sergio del Amo, 2025-12-05)
- `5f525cfaafa8` micronaut = "5.0.0-M2" (Sergio del Amo, 2025-12-05)
- `4a579d9c461b` micronaut-docs is provided by Micronaut Build (Sergio del Amo, 2025-12-05)
- `318be5e7b023` Update common files (#586) (micronaut-build, 2025-12-05)
- `cd98b3f2f766` Replace Micronaut nullability annotations with JSpecify annotations (#602) (Copilot, 2025-12-01)
- `6e3c4b76e96f` Update common files (#584) (micronaut-build, 2025-10-16)
- `9b40a37a9c40` MIronaut build plugin 8.0.0-M4 (Sergio del Amo, 2025-10-13)
- `6535a62e4e5b` gradle 9.1 (Sergio del Amo, 2025-10-13)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.jaxrs-module.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` jaxrs-client/build.gradle.kts
- `M` jaxrs-server-security/build.gradle.kts
- `M` settings.gradle

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
- `M` jaxrs-client/src/main/java/io/micronaut/jaxrs/client/JaxRsClientBuilder.java
- `M` jaxrs-client/src/main/java/io/micronaut/jaxrs/client/JaxRsConfiguration.java
- `M` jaxrs-client/src/main/java/io/micronaut/jaxrs/client/JaxRsEntityMessageBodyWriter.java
- `M` jaxrs-client/src/main/java/io/micronaut/jaxrs/client/JaxRsInvocation.java
- `M` jaxrs-common/src/main/java/io/micronaut/jaxrs/common/JaxRsArgumentUtil.java
- `M` jaxrs-common/src/main/java/io/micronaut/jaxrs/common/JaxRsContainerMessageBodyHandlerRegistry.java
- `M` jaxrs-common/src/main/java/io/micronaut/jaxrs/common/JaxRsGenericEntityMessageBodyWriter.java
- `M` jaxrs-common/src/main/java/io/micronaut/jaxrs/common/JaxRsInterceptedRead.java
- `M` jaxrs-common/src/main/java/io/micronaut/jaxrs/common/JaxRsInterceptedWrite.java
- `M` jaxrs-common/src/main/java/io/micronaut/jaxrs/common/JaxRsMessageBodyReader.java
- `M` jaxrs-common/src/main/java/io/micronaut/jaxrs/common/JaxRsMessageBodyWriter.java
- `M` jaxrs-common/src/main/java/io/micronaut/jaxrs/common/JaxRsResponse.java
- `M` jaxrs-common/src/main/java/io/micronaut/jaxrs/common/MicronautRuntimeDelegate.java
- `M` jaxrs-common/src/main/java/io/micronaut/jaxrs/common/body/standard/DefaultFormUrlEncodedDecoder.java
- `M` jaxrs-common/src/main/java/io/micronaut/jaxrs/common/body/standard/JaxRsMultivaluedMapMessageBodyWriter.java
- `M` jaxrs-common/src/main/java/io/micronaut/jaxrs/common/body/standard/JaxRsMultivaluedStringObjectMapMessageBodyReader.java
- `M` jaxrs-common/src/main/java/io/micronaut/jaxrs/common/body/standard/JaxRsMultivaluedStringStringMapMessageBodyReader.java
- `M` jaxrs-processor/src/main/java/io/micronaut/jaxrs/processor/ApplicationPathAnnotationMapper.java
- `M` jaxrs-processor/src/main/java/io/micronaut/jaxrs/processor/ConsumesMapper.java
- `M` jaxrs-processor/src/main/java/io/micronaut/jaxrs/processor/ContextMapper.java
- `M` jaxrs-processor/src/main/java/io/micronaut/jaxrs/processor/CookieParamMapper.java
- `M` jaxrs-processor/src/main/java/io/micronaut/jaxrs/processor/DefaultValueMapper.java
- `M` jaxrs-processor/src/main/java/io/micronaut/jaxrs/processor/DeleteAnnotationMapper.java
- `M` jaxrs-processor/src/main/java/io/micronaut/jaxrs/processor/FormParamMapper.java
- `M` jaxrs-processor/src/main/java/io/micronaut/jaxrs/processor/GetAnnotationMapper.java
- `M` jaxrs-processor/src/main/java/io/micronaut/jaxrs/processor/HeadAnnotationMapper.java
- `M` jaxrs-processor/src/main/java/io/micronaut/jaxrs/processor/HeaderParamMapper.java
- `M` jaxrs-processor/src/main/java/io/micronaut/jaxrs/processor/HttpMethodMapper.java
- `M` jaxrs-processor/src/main/java/io/micronaut/jaxrs/processor/JaxRsTypeElementVisitor.java
- `M` jaxrs-processor/src/main/java/io/micronaut/jaxrs/processor/OptionsAnnotationMapper.java
- `M` jaxrs-processor/src/main/java/io/micronaut/jaxrs/processor/PathAnnotationMapper.java
- `M` jaxrs-processor/src/main/java/io/micronaut/jaxrs/processor/PathParamMapper.java
- `M` jaxrs-processor/src/main/java/io/micronaut/jaxrs/processor/PostAnnotationMapper.java
- `M` jaxrs-processor/src/main/java/io/micronaut/jaxrs/processor/PriorityMapper.java
- `M` jaxrs-processor/src/main/java/io/micronaut/jaxrs/processor/ProducesMapper.java
- `M` jaxrs-processor/src/main/java/io/micronaut/jaxrs/processor/PutAnnotationMapper.java
- `M` jaxrs-server/src/main/java/io/micronaut/jaxrs/container/ApplicationProvider.java
- `M` jaxrs-server/src/main/java/io/micronaut/jaxrs/container/JaxRsApplicationUriNamingStrategy.java
- `M` jaxrs-server/src/main/java/io/micronaut/jaxrs/container/JaxRsFilters.java
- `M` jaxrs-server/src/main/java/io/micronaut/jaxrs/container/JaxRsHttpStatusExceptionHandler.java
- `M` jaxrs-server/src/main/java/io/micronaut/jaxrs/container/JaxRsMessageBodyReaders.java
- `M` jaxrs-server/src/main/java/io/micronaut/jaxrs/container/JaxRsOverrideStringMessageBodyReader.java
- `M` jaxrs-server/src/main/java/io/micronaut/jaxrs/container/JaxRsResourceInfo.java
- `M` jaxrs-server/src/main/java/io/micronaut/jaxrs/container/QueryParamArgumentBinder.java
- `M` jaxrs-server/src/main/java/io/micronaut/jaxrs/runtime/ext/bind/UriInfoImpl.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` jaxrs-server-security/src/test/java/io/micronaut/jaxrs/security/bind/SimpleSecurityContextTest.java
- `M` jaxrs-server/src/test/java/io/micronaut/jaxrs/container/ResponseTest.java
- `M` jaxrs-servlet/src/test/java/io/micronaut/jaxrs/servlet/PaginatedCollection.java
- `M` jaxrs-servlet/src/test/java/io/micronaut/jaxrs/servlet/PaginatedCollectionBodyWriter.java
- `M` tests/jaxrs-tck/src/main/resources/exclusions.txt

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

