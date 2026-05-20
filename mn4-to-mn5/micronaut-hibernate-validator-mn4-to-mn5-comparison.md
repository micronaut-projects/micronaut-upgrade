• I compared the matching existing module micronaut-hibernate-validator because the requested micronaut-hibernate-validation paths do not exist.

  Full report: micronaut-hibernate-validator-mn4-to-mn5-comparison.md:1

  Scope:

  - Previous: mn4/micronaut-hibernate-validator, branch 4.9.x, commit 17ba2ae96126, clean
  - Current: mn5/micronaut-hibernate-validator, branch 5.0.x, commit 3e37a4044036, clean
  - Delta: 47 commit candidates, 42 changed files

  Release-note draft:

  ## Micronaut Hibernate Validator 5.0

  ### Features

  - Custom `ValueExtractor` beans are now registered with Hibernate Validator through `ValidatorFactoryProvider`, including executable validation use cases.

  ### Compatibility

  - Updated for the Micronaut 5 baseline.
  - Updated Hibernate Validator from `org.hibernate:hibernate-validator:8.0.2.Final` to `org.hibernate.validator:hibernate-validator:9.1.0.Final`.
  - Replaced Micronaut nullability annotations with JSpecify annotations in the integration source.

  ### Configuration

  - Added a typed `HibernateValidatorConfiguration` bean for `hibernate.validator.*` settings.
  - `hibernate.validator.ignore-xml-configuration` remains supported and defaults to `true`.

  ### Breaking Changes

  - No explicit repository-local breaking change document was found. Review Hibernate Validator `8.x -> 9.1.x` compatibility before publishing final notes.

  Important dependency/tooling changes:

  - Project version: 4.9.0-SNAPSHOT -> 5.0.0-SNAPSHOT
  - Micronaut Core: 4.10.4 -> 5.0.0-RC2
  - Micronaut Validation: 4.11.0 -> 5.0.0-M2
  - Micronaut Serde: 2.15.5 -> 3.0.0-RC2
  - Hibernate Validator: 8.0.2.Final -> 9.1.0.Final
  - Gradle wrapper: 8.14.3 -> 9.5.0

# Release Note Comparison

Generated: 2026-05-06 16:31 UTC
Comparison: `mn4` -> `mn5`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-hibernate-validator` | `4.9.x` | `17ba2ae96126` | `git@github.com:micronaut-projects/micronaut-hibernate-validator.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-hibernate-validator` | `5.0.x` | `3e37a4044036` | `git@github.com:micronaut-projects/micronaut-hibernate-validator.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-hibernate-validator`
- Commit candidates found: 47
- File changes listed: 42
- Version values listed: 10
- File status counts: A=20, M=22

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `4.9.0-SNAPSHOT` | `5.0.0-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.15.5` | `io.micronaut.serde:micronaut-serde-bom:3.0.0-RC2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-validation` | `io.micronaut.validation:micronaut-validation-bom:4.11.0` | `io.micronaut.validation:micronaut-validation-bom:5.0.0-M2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.4` | `5.0.0-RC2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.15.5` | `3.0.0-RC2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.9.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.11.0` | `5.0.0-M2` | `changed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.0` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Fixes

- `d76386f99cf9` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m7 (#551) (renovate[bot], 2026-04-24)
- `918e89911165` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m24 (#557) (renovate[bot], 2026-04-23)
- `008232068de9` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m17 (#545) (renovate[bot], 2026-03-18)
- `19759a090e74` fix(deps): update dependency org.hibernate:hibernate-validator to v8.0.3.final (#528) (renovate[bot], 2025-12-09)
- `505028208edd` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#532) (renovate[bot], 2025-12-09)
- `a82d8435e56c` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.12.0 (#534) (renovate[bot], 2025-12-09)
- `84d72af443c1` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#539) (renovate[bot], 2025-12-09)
- `87fdcfd4f240` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.8 (#527) (renovate[bot], 2025-11-03)

### Dependency Updates

- `629a17518409` Update Micronaut dependencies (#562) (renovate[bot], 2026-05-01)
- `a9fdcc9d0784` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-04-27)
- `bad79bdfd125` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#547) (renovate[bot], 2026-03-18)
- `0463a589b6f7` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2025-12-09)
- `997ede37e17c` chore(deps): update github artifact actions (#535) (renovate[bot], 2025-12-09)
- `3d61610695c1` chore(deps): update actions/checkout action to v6 (#537) (renovate[bot], 2025-12-09)
- `9837bdfb3a20` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#531) (renovate[bot], 2025-12-09)
- `08478072f973` chore(deps): update softprops/action-gh-release action to v2.5.0 (#533) (renovate[bot], 2025-12-09)
- `64e0cf9fe7b6` chore(deps): update gradle to v9.2.1 (#536) (renovate[bot], 2025-12-09)
- `a781bec90f3d` chore(deps): update mikepenz/action-junit-report action to v6 (#538) (renovate[bot], 2025-12-09)
- `02ef86e05a14` chore(deps): update graalvm/setup-graalvm action to v1.4.4 (#540) (renovate[bot], 2025-12-09)
- `0ef8589bc040` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#524) (renovate[bot], 2025-11-03)
- `6122a6dd77d2` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m8 (#525) (renovate[bot], 2025-11-03)
- `373497b140fa` chore(deps): update gradle to v9.2.0 (#529) (renovate[bot], 2025-11-03)

### Internal

- `832de04359ed` ci: projectVersion=5.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-10-15)

### Review Candidates

- `3e37a4044036` Update Micronaut and Micronaut Serde versions (Sergio del Amo, 2026-05-06)
- `fab1a2b1468c` Update common files (#566) (micronaut-build, 2026-05-06)
- `4c5d83067f26` Update common files (#565) (micronaut-build, 2026-05-05)
- `b17598110ee1` Update common files (#564) (micronaut-build, 2026-05-02)
- `4b2aee98edfa` Register custom ValueExtractor beans in ValidatorFactoryProvider (#558) (Issam Liqali, 2026-05-02)
- `392205820170` Update Gradle to v9.5.0 (#552) (renovate[bot], 2026-05-01)
- `6efeef633c3f` Update common files (#563) (micronaut-build, 2026-05-01)
- `0c1f7e518181` [skip ci] Release v5.0.0-M2 (micronaut-build, 2026-04-27)
- `84639d496cb9` micronaut-validation = "5.0.0-M2" (Sergio del Amo, 2026-04-27)
- `b7501f50e733` Update common files (#555) (micronaut-build, 2026-04-26)
- `c8968e6b3889` Update common files (#549) (micronaut-build, 2026-03-18)
- `ab3fecd1986b` [skip ci] Release v5.0.0-M1 (micronaut-build, 2025-12-09)
- `fb0bf46e453d` micronaut-validation = "5.0.0-M1" (Sergio del Amo, 2025-12-09)
- `89d49e849ba3` micronaut-serde = "3.0.0-M1" (Sergio del Amo, 2025-12-09)
- `79df063c965b` micronaut = "5.0.0-M2" (Sergio del Amo, 2025-12-09)
- `30bb6fa28098` Update hibernate validator to 9.1.0.Final (#541) (issam liqali, 2025-12-09)
- `0db2bce7f548` Update common files (#530) (micronaut-build, 2025-12-09)
- `37c05986f758` Replace Micronaut nullability annotations with JSpecify annotations (#543) (Copilot, 2025-12-01)
- `b1b4b714e02b` Micronaut 5 compatibility (#526) (issam liqali, 2025-11-03)
- `a5b7c0b78ca6` Update common files (#523) (micronaut-build, 2025-11-03)
- `9bcf154999e1` Update common files (#522) (micronaut-build, 2025-10-20)
- `d5b307e41234` Update common files (#521) (micronaut-build, 2025-10-17)
- `2df5c61b0804` Micronaut Gradle build plugin 8.0.0-M4 (Sergio del Amo, 2025-10-15)
- `657bb76ef795` gradle 9.1 (Sergio del Amo, 2025-10-15)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` settings.gradle

### Documentation

- `A` .agents/skills/docs/SKILL.md
- `A` .agents/skills/docs/references/control-panel-patterns.md
- `A` .agents/skills/docs/references/micronaut-docs-providers.md
- `M` .github/workflows/release.yml

### Source

- `A` .agents/skills/agent-md-refactor/SKILL.md
- `A` .agents/skills/agent-md-refactor/references/examples-and-anti-patterns.md
- `A` .agents/skills/agent-md-refactor/references/refactor-playbook.md
- `A` .agents/skills/coding/SKILL.md
- `A` .agents/skills/skill-creator/SKILL.md
- `A` .agents/skills/skill-creator/references/research-synthesis.md
- `A` .agents/skills/skill-creator/references/templates.md
- `M` .clineignore
- `M` .clinerules/coding.md
- `M` .github/instructions/coding.instructions.md
- `M` .github/renovate.json
- `A` .github/scripts/vulnerability-audit.sh
- `M` .github/workflows/central-sync.yml
- `M` .github/workflows/graalvm-dev.yml
- `M` .github/workflows/publish-snapshot.yml
- `A` .github/workflows/sonatype.yml
- `M` .gitignore
- `A` .sdkmanrc
- `M` MAINTAINING.md
- `M` config/checkstyle/checkstyle.xml
- `A` hibernate-validator/src/main/java/io/micronaut/configuration/hibernate/validator/HibernateValidatorConfiguration.java
- `M` hibernate-validator/src/main/java/io/micronaut/configuration/hibernate/validator/MicronautHibernateValidator.java
- `M` hibernate-validator/src/main/java/io/micronaut/configuration/hibernate/validator/ValidatorFactoryProvider.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `A` hibernate-validator/src/test/groovy/io/micronaut/configuration/hibernate/validator/CustomValueExtractorSpec.groovy
- `A` hibernate-validator/src/test/groovy/io/micronaut/configuration/hibernate/validator/HibernateValidatorConfigurationSpec.groovy

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

