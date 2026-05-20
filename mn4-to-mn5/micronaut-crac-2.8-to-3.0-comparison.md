# Release Note Comparison

Generated: 2026-05-19 11:39 UTC
Comparison: `2.8.x` -> `3.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-crac` | `2.8.x` | `16c1ed51fd6d` | `git@github.com:micronaut-projects/micronaut-crac.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-crac` | `3.0.x` | `92c936276af2` | `git@github.com:micronaut-projects/micronaut-crac.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-crac`
- Commit candidates found: 66
- File changes listed: 70
- Version values listed: 29
- File status counts: A=26, M=44

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `2.8.0-SNAPSHOT` | `3.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-crac` | `org.crac:crac:1.5.0` | `org.crac:crac:1.5.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-testcontainers-redis` | `not present` | `com.redis.testcontainers:testcontainers-redis:1.6.4` | `added` |
| `gradle/libs.versions.toml` | `libraries.micronaut-cache` | `io.micronaut.cache:micronaut-cache-bom:5.3.0` | `io.micronaut.cache:micronaut-cache-bom:6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-data` | `io.micronaut.data:micronaut-data-bom:4.13.7` | `io.micronaut.data:micronaut-data-bom:5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-redis` | `io.micronaut.redis:micronaut-redis-bom:6.9.0` | `io.micronaut.redis:micronaut-redis-bom:7.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.15.5` | `io.micronaut.serde:micronaut-serde-bom:3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-sql` | `io.micronaut.sql:micronaut-sql-bom:6.3.1` | `io.micronaut.sql:micronaut-sql-bom:7.0.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-resources` | `io.micronaut.testresources:micronaut-test-resources-bom:2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.sonatype-scan` | `org.sonatype.gradle.plugins:scan-gradle-plugin:3.1.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.13` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.managed-crac` | `1.5.0` | `1.5.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-testcontainers-redis` | `not present` | `1.6.4` | `added` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.4` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-cache` | `5.3.0` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-data` | `4.13.7` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.5.5` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-platform` | `4.9.4` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-redis` | `6.9.0` | `7.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serialization` | `2.15.5` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-sql` | `6.3.1` | `7.0.1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.9.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test-resources` | `2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.sonatype-scan` | `3.1.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Fixes

- `ccef86b92ad7` fix(deps): update micronaut dependencies (#505) (renovate[bot], 2026-05-07)
- `39c4dada7e64` fix(deps): update micronaut dependencies (#500) (renovate[bot], 2026-04-29)
- `0e41352d3ba4` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m7 (#488) (renovate[bot], 2026-04-22)
- `91f10ae874db` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v4.14.3 (#490) (renovate[bot], 2026-04-22)
- `701a472e16f5` fix(deps): update dependency io.micronaut.cache:micronaut-cache-bom to v6.0.0-m3 (#491) (renovate[bot], 2026-04-22)
- `11394dc48e4d` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m22 (#497) (renovate[bot], 2026-04-16)
- `8eb61c39c7e8` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m17 (#486) (renovate[bot], 2026-03-19)
- `0cfbd069f934` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.12 (#475) (renovate[bot], 2025-12-29)
- `79d9c28b3aee` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v4.14.2 (#476) (renovate[bot], 2025-12-29)
- `7e090f95add2` fix(deps): update dependency io.micronaut.platform:micronaut-platform to v4.10.6 (#477) (renovate[bot], 2025-12-29)
- `ba5854537fa9` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to v7 (#472) (renovate[bot], 2025-12-10)
- `dbac309932ab` fix(deps): update micronaut.gradle.plugin to v4.6.1 (#464) (renovate[bot], 2025-12-10)
- `9abbd298fac8` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#463) (renovate[bot], 2025-12-10)
- `4176c2906c2f` fix(deps): update dependency io.micronaut.platform:micronaut-platform to v4.10.3 (#462) (renovate[bot], 2025-12-10)
- `3f1db509aa2b` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v4.14.1 (#461) (renovate[bot], 2025-12-10)
- `1377cbac3d87` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to v6.3.2 (#459) (renovate[bot], 2025-12-10)
- `24b1c02b43a3` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#458) (renovate[bot], 2025-12-10)
- `41fa9308134a` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.6 (#450) (renovate[bot], 2025-10-17)

### Dependency Updates

- `a47c78f34402` chore: Bump version to 3.0.1-SNAPSHOT (micronaut-build, 2026-05-18)
- `f4d64135b0a2` chore: Bump version to 4.0.0-SNAPSHOT (micronaut-build, 2026-05-07)
- `c05bb9221cf3` chore(deps): update gradle to v9.5.0 (#489) (renovate[bot], 2026-04-29)
- `a3ae0b57946c` chore(deps): combine renovate dependency updates (#503) (Sergio del Amo, 2026-04-29)
- `72d67d09285e` chore(deps): update gradle/actions action to v6 (#496) (renovate[bot], 2026-04-22)
- `6a0c815e0abe` chore(deps): update softprops/action-gh-release action to v3 (#499) (renovate[bot], 2026-04-22)
- `8204c263493a` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#485) (renovate[bot], 2026-03-19)
- `06b1b12be5aa` chore: Bump version to 3.0.0-SNAPSHOT (micronaut-build, 2025-12-29)
- `13c4ca5697eb` chore(deps): update github artifact actions (#481) (renovate[bot], 2025-12-29)
- `58e0c89fa5b6` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m13 (#479) (renovate[bot], 2025-12-29)
- `0e871be6435b` chore(deps): update actions/cache action to v5 (#480) (renovate[bot], 2025-12-29)
- `d6a969914b72` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#456) (renovate[bot], 2025-12-10)
- `9a7125e466b1` chore(deps): update stefanzweifel/git-auto-commit-action action to v7 (#469) (renovate[bot], 2025-12-10)
- `2097410f1463` chore(deps): update actions/checkout action (#465) (renovate[bot], 2025-12-10)
- `4be619dcdadc` chore(deps): update gradle to v9.2.1 (#460) (renovate[bot], 2025-12-10)
- `5d19ab271b59` chore(deps): update softprops/action-gh-release action to v2.5.0 (#457) (renovate[bot], 2025-12-10)
- `34aa0bd3c293` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m7 (#452) (renovate[bot], 2025-10-29)
- `d9b3a05ccaf4` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#453) (renovate[bot], 2025-10-29)
- `014c3982e0a2` ci: projectVersion 3.0.0-SNAPSHOT [ci skip] (Tim Yates, 2024-04-18)

### Internal

- `bc87f466528a` Build: Update to Micronaut 5 (#478) (issam liqali, 2025-12-29)

### Review Candidates

- `92c936276af2` Update common files (#508) (micronaut-build, 2026-05-19)
- `d5ee4be41819` micronaut.build.shared.settings 8.0.0 (Sergio del Amo, 2026-05-18)
- `e98cdf6e657f` micronaut-sql = "7.0.1" (Sergio del Amo, 2026-05-18)
- `5fb4c4d248cf` [skip ci] Release v3.0.0 (micronaut-build, 2026-05-18)
- `cdbc91e458b4` Update common files (#507) (micronaut-build, 2026-05-15)
- `174127554e4e` micronaut-platform = "5.0.0-RC1" (Sergio del Amo, 2026-05-14)
- `eceac740768c` micronaut-redis = "7.0.0" (Sergio del Amo, 2026-05-14)
- `2b28438e2cc4` micronaut-cache = "6.0.0" (Sergio del Amo, 2026-05-14)
- `c730ef5201e5` Update versions (Sergio del Amo, 2026-05-14)
- `291a8f3ff9ec` micronaut-platform = "5.0.0-RC1" (Sergio del Amo, 2026-05-13)
- `281734e685c7` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `8a8f70638ad0` Update common files (#506) (micronaut-build, 2026-05-09)
- `4ea22698d2e9` [skip ci] Release v4.0.0-RC1 (micronaut-build, 2026-05-07)
- `435bc354fa49` micronaut-test = "5.0.0-M8" (Sergio del Amo, 2026-05-07)
- `f7ef7c8a8d79` Update common files (#504) (micronaut-build, 2026-05-07)
- `3ec264f64bfb` Update common files (#501) (micronaut-build, 2026-04-29)
- `9f1e6891e9de` Update common files (#495) (micronaut-build, 2026-04-22)
- `222ba97fa553` Update common files (#483) (micronaut-build, 2026-03-19)
- `2c8cd784c351` [skip ci] Release v3.0.0-M1 (micronaut-build, 2025-12-29)
- `7ad0523181e2` Update common files (#474) (micronaut-build, 2025-12-29)
- `d795b89da4df` fix gradle build error for micronaut 5 release (#454) (araysse, 2025-12-10)
- `87ab65075bb5` Update common files (#455) (micronaut-build, 2025-12-10)
- `b23db8cdb36e` Replace Micronaut nullability annotations with JSpecify annotations (#471) (Copilot, 2025-12-01)
- `70edfc78cc69` Update common files (#451) (micronaut-build, 2025-10-29)
- `b388c96f4828` Update common files (#449) (micronaut-build, 2025-10-17)
- `4b745bd366d9` Micronaut Build gradle plugin 8.0.0-M4 (Sergio del Amo, 2025-10-15)
- `22436d9b25b4` gradle 9.1 (Sergio del Amo, 2025-10-15)
- `dd387c93eeeb` Merge branch '2.8.x' into 3.0.x (Sergio del Amo, 2025-10-15)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` .github/workflows/update-gradle-wrapper.yml
- `M` buildSrc/build.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.crac-library-test-suite.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.crac-module.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.crac-test-suite.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` settings.gradle
- `M` test-suite-kotlin-ksp/build.gradle.kts
- `M` test-suite-kotlin/build.gradle.kts
- `M` test-suite-redis/build.gradle.kts

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
- `M` test-suite-docker/build.gradle.kts

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
- `M` crac/src/main/java/io/micronaut/crac/CracConfiguration.java
- `M` crac/src/main/java/io/micronaut/crac/CracConfigurationProperties.java
- `M` crac/src/main/java/io/micronaut/crac/CracContextProvider.java
- `M` crac/src/main/java/io/micronaut/crac/CracEventPublisher.java
- `M` crac/src/main/java/io/micronaut/crac/GlobalCracContextProvider.java
- `M` crac/src/main/java/io/micronaut/crac/resources/datasources/resolver/CompositeDataSourceResolver.java
- `M` crac/src/main/java/io/micronaut/crac/resources/datasources/resolver/DataSourceResourceResolver.java
- `M` crac/src/main/java/io/micronaut/crac/resources/datasources/resolver/HikariDataSourceResolver.java
- `M` crac/src/main/java/io/micronaut/crac/resources/datasources/resolver/HikariDelegatingDataSourceResolver.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` test-suite-redis/src/test/groovy/io/micronaut/crac/BaseCacheSpecification.groovy
- `M` test-suite-redis/src/test/groovy/io/micronaut/crac/BothRedisConnectionSpec.groovy
- `M` test-suite-redis/src/test/groovy/io/micronaut/crac/CracRedisConfigurationSpec.groovy
- `M` test-suite-redis/src/test/groovy/io/micronaut/crac/ExplicitCacheSpec.groovy
- `M` test-suite-redis/src/test/groovy/io/micronaut/crac/RedisStatefulPubSubConnectionSpec.groovy
- `M` test-suite-redis/src/test/groovy/io/micronaut/crac/TwoServerRedisSpec.groovy
- `A` test-suite-redis/src/test/java/io/micronaut/crac/testcontainers/Redis.java

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

