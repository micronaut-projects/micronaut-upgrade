 Compared micronaut-cassandra as mn4 → mn5.

  Scope

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-cassandra, branch 6.9.x, SHA 79c3bc3
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-cassandra, branch 7.0.x, SHA 31a0108
  - Report: /private/tmp/micronaut-cassandra-6.9-to-7.0-comparison.md

  Key Findings

  - Major baseline move: project 6.9.0-SNAPSHOT → 7.0.1-SNAPSHOT, Micronaut 4.10.4 → 5.0.0, platform 4.8.3 →
    5.0.0-RC1, Gradle wrapper 8.14.3 → 9.5.1, plus .sdkmanrc pinned to java=25.0.1-graal.
  - Breaking API cleanup: deprecated CassandraHealthIndicator(CqlSession) was removed;
    CassandraHealthIndicator(List<CqlSession>) is the supported constructor. This is documented in new
    breaks.adoc.
  - Datastax Cassandra driver stayed on 4.17.0; related ecosystem BOMs moved forward: Micrometer 5.13.0 →
    6.0.0, Reactor 3.9.0 → 4.0.0, Micronaut Test 4.9.0 → 5.0.0.
  - Security/dependency hardening: BouncyCastle bcpkix-jdk18on 1.81 → 1.84, and cassandra/build.gradle.kts
    adds a jackson-core:2.21.3 constraint for CVE-2022-42003.
  - Nullability annotations changed from Micronaut annotations to JSpecify in CassandraMetricsBinder.
  - Test Resources usage was removed from Cassandra test suites; tests now use explicit CassandraContainer
    helpers via TestPropertyProvider, and Testcontainers imports moved to
    org.testcontainers.cassandra.CassandraContainer.
  - Native image support was moved/added under the Cassandra module with build-time initialization for the
    Datastax shaded Guava comparator.
  - CI/release hardening added OSV vulnerability audit scripts/workflow and Java/GraalVM 25-oriented workflow
    updates.

  Diff size: 68 files changed, 3820 insertions(+), 212 deletions(-).

  I did not run tests; this was a folder comparison only.

# Release Note Comparison

Generated: 2026-05-19 11:16 UTC
Comparison: `6.9.x` -> `7.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-cassandra` | `6.9.x` | `79c3bc3f73a6` | `git@github.com:micronaut-projects/micronaut-cassandra.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-cassandra` | `7.0.x` | `31a01088bad3` | `git@github.com:micronaut-projects/micronaut-cassandra.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-cassandra`
- Commit candidates found: 83
- File changes listed: 68
- Version values listed: 27
- File status counts: A=29, M=39

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `6.9.0-SNAPSHOT` | `7.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.bcpkix` | `org.bouncycastle:bcpkix-jdk18on:1.81` | `org.bouncycastle:bcpkix-jdk18on:1.84` | `changed` |
| `gradle/libs.versions.toml` | `libraries.gradle-micronaut` | `io.micronaut.gradle:micronaut-gradle-plugin:4.5.3` | `io.micronaut.gradle:micronaut-gradle-plugin:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-datastax-cassandra-driver-core` | `com.datastax.oss:java-driver-core:4.17.0` | `com.datastax.oss:java-driver-core:4.17.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-datastax-cassandra-driver-mapper-processor` | `com.datastax.oss:java-driver-mapper-processor:4.17.0` | `com.datastax.oss:java-driver-mapper-processor:4.17.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-datastax-cassandra-driver-metrics-micrometer` | `com.datastax.oss:java-driver-metrics-micrometer:4.17.0` | `com.datastax.oss:java-driver-metrics-micrometer:4.17.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.micronaut-micrometer` | `io.micronaut.micrometer:micronaut-micrometer-bom:5.13.0` | `io.micronaut.micrometer:micronaut-micrometer-bom:6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-reactor` | `io.micronaut.reactor:micronaut-reactor-bom:3.9.0` | `io.micronaut.reactor:micronaut-reactor-bom:4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-resources` | `io.micronaut.testresources:micronaut-test-resources-bom:2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.system-stubs` | `uk.org.webcompere:system-stubs-core:2.1.8` | `uk.org.webcompere:system-stubs-core:2.1.8` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.bcpkix` | `1.81` | `1.84` | `changed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.27` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.managed-datastax-cassandra-driver` | `4.17.0` | `4.17.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.4` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.5.3` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-micrometer` | `5.13.0` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-platform` | `4.8.3` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-reactor` | `3.9.0` | `4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.9.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test-resources` | `2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.system-stubs` | `2.1.8` | `2.1.8` | `unchanged` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |
| `settings.gradle` | `plugin.io.micronaut.build.shared.settings` | `7.6.4` | `8.0.0-M18` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Features

- `2fbdf532b687` add build arguments for native image (#603) (issam liqali, 2026-02-12)

### Fixes

- `0e22b0d68b49` fix(deps): update dependency org.bouncycastle:bcpkix-jdk18on to v1.84 (#565) (renovate[bot], 2026-04-30)
- `42bc9396be41` fix(deps): update dependency com.fasterxml.jackson.core:jackson-core to v2.21.2 (#600) (renovate[bot], 2026-04-27)
- `7d705f882fbd` fix(deps): update dependency io.micronaut.reactor:micronaut-reactor-bom to v4.0.0-m2 (#611) (renovate[bot], 2026-04-22)
- `63e4aae1086d` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m22 (#605) (renovate[bot], 2026-04-16)
- `46ace82c97da` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m10 (#597) (renovate[bot], 2026-02-10)
- `15e408c0c854` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.2 (#599) (renovate[bot], 2026-02-10)
- `c48b5b3584f3` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.12 (#588) (renovate[bot], 2025-12-29)
- `b3a9aa75b588` fix(deps): update dependency io.micronaut.reactor:micronaut-reactor-bom to v3.9.1 (#577) (renovate[bot], 2025-12-10)
- `66a526b0ff7d` fix(deps): update dependency io.micronaut.micrometer:micronaut-micrometer-bom to v5.13.2 (#575) (renovate[bot], 2025-12-10)
- `d0026ec35024` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.1 (#573) (renovate[bot], 2025-12-10)
- `071367964743` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#572) (renovate[bot], 2025-12-10)
- `468815a7827a` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.0 (#547) (renovate[bot], 2025-10-17)
- `05d29c8108bf` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.6 (#567) (renovate[bot], 2025-10-17)
- `af363dc3ceb3` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.3.6 (#445) (renovate[bot], 2024-04-12)
- `f6d705fb267c` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.4.1 (#446) (renovate[bot], 2024-04-12)
- `af3075e703bf` fix(deps): update dependency io.micronaut.reactor:micronaut-reactor-bom to v3.3.0 (#443) (renovate[bot], 2024-04-02)
- `e8679e458001` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.4.0 (#441) (renovate[bot], 2024-04-01)
- `993a868c305d` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.3.5 (#436) (renovate[bot], 2024-03-27)
- `89479af0de70` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.3.12 (#437) (renovate[bot], 2024-03-27)
- `bfe6986a6249` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.3.11 (#426) (renovate[bot], 2024-03-18)

### Dependency Updates

- `cb721c7fae62` chore: Bump version to 7.0.1-SNAPSHOT (micronaut-build, 2026-05-14)
- `bfbe76d593ad` chore: Bump version to 7.0.0-SNAPSHOT (micronaut-build, 2026-05-07)
- `e52ebdcd43f8` Update dependency io.micronaut:micronaut-core-bom to v5.0.0-M26 (#617) (renovate[bot], 2026-05-01)
- `0181ad4d414a` Update dependency com.fasterxml.jackson.core:jackson-core to v2.21.3 (#614) (renovate[bot], 2026-04-30)
- `34aee6fccbba` Update Micronaut dependencies (#613) (renovate[bot], 2026-04-30)
- `9207bae1fdf2` chore(deps): update softprops/action-gh-release action to v2.6.2 (#609) (renovate[bot], 2026-04-22)
- `ba97bdae5f11` chore(deps): update gradle/actions action to v6 (#610) (renovate[bot], 2026-04-22)
- `6731f29a85c7` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#604) (renovate[bot], 2026-04-16)
- `2034e24f590e` chore: Bump version to 7.0.0-SNAPSHOT (micronaut-build, 2026-02-11)
- `6f92bb8595a5` Update Micronaut plugin version to 8.0.0-M16 (#601) (issam liqali, 2026-02-10)
- `4fb6fd2da6a4` chore(deps): update actions/cache action to v5 (#589) (renovate[bot], 2025-12-29)
- `6024800e6aa7` chore(deps): update github artifact actions (#592) (renovate[bot], 2025-12-29)
- `eca3a1319508` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m13 (#590) (renovate[bot], 2025-12-29)
- `807c9e681985` chore(deps): update stefanzweifel/git-auto-commit-action action to v7 (#583) (renovate[bot], 2025-12-10)
- `5eb3b68b6ee4` chore(deps): update gradle/actions action to v5 (#581) (renovate[bot], 2025-12-10)
- `4bea7b38301d` chore(deps): update actions/checkout action (#580) (renovate[bot], 2025-12-10)
- `7e923a4229a2` chore(deps): update softprops/action-gh-release action to v2.5.0 (#576) (renovate[bot], 2025-12-10)
- `62e05035f2d8` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#571) (renovate[bot], 2025-12-10)
- `893f91b830be` chore(deps): update gradle/gradle-build-action action to v3.2.1 (#444) (renovate[bot], 2024-04-12)
- `1eb1d9dc9ae1` chore(deps): update graalvm/setup-graalvm action to v1.2.1 (#435) (renovate[bot], 2024-03-27)
- `1668c6386997` chore(deps): update dependency gradle to v8.7 (#438) (renovate[bot], 2024-03-27)
- `dd20e94e3cf0` chore(deps): update slsa-framework/slsa-github-generator action to v1.10.0 (#439) (renovate[bot], 2024-03-27)
- `3cf8ae393c2f` chore(deps): update graalvm/setup-graalvm action to v1.2.0 (#432) (renovate[bot], 2024-03-19)
- `27c30a40f18c` chore(deps): update plugin io.micronaut.build.shared.settings to v6.7.0 (#430) (renovate[bot], 2024-03-18)
- `c9f18eae94eb` chore(deps): update softprops/action-gh-release action to v2 (#427) (renovate[bot], 2024-03-18)
- `59f4cc6cd9e1` chore(deps): update graalvm/setup-graalvm action to v1.1.9 (#428) (renovate[bot], 2024-03-18)

### Review Candidates

- `31a01088bad3` Update common files (#621) (micronaut-build, 2026-05-19)
- `78bc80297683` micronaut-micrometer = "6.0.0" (Sergio del Amo, 2026-05-18)
- `969120a4b323` micronaut-test = "5.0.0" (Sergio del Amo, 2026-05-18)
- `da13108bf8f9` [skip ci] Release v7.0.0 (micronaut-build, 2026-05-14)
- `ae7f9dee5baf` Update versions (Sergio del Amo, 2026-05-14)
- `42fa58a4a766` Update common files (#620) (micronaut-build, 2026-05-14)
- `508bf30e0b4f` micronaut-platform = "5.0.0-RC1" (Sergio del Amo, 2026-05-13)
- `088d50fcea55` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `951cc95a2e6c` Update common files (#619) (micronaut-build, 2026-05-09)
- `f3545891236f` [skip ci] Release v7.0.0-RC1 (micronaut-build, 2026-05-07)
- `8987d1a30405` micronaut = "5.0.0-RC2" (Sergio del Amo, 2026-05-07)
- `08ac687a02de` Update common files (#618) (micronaut-build, 2026-05-07)
- `f2611e63eaf4` Update common files (#616) (micronaut-build, 2026-05-01)
- `4df73cea54e5` Update Gradle to v9.5.0 (#608) (renovate[bot], 2026-04-30)
- `e8481375e1c8` Update common files (#615) (micronaut-build, 2026-04-30)
- `b364ca9a5f0c` micronaut-platform = "5.0.0-M2" (Sergio del Amo, 2026-04-27)
- `8a871462b61c` micronaut-gradle-plugin = "5.0.0-M1" (Sergio del Amo, 2026-04-27)
- `5adcdb30bd6b` micronaut-micrometer = "6.0.1-M1" (Sergio del Amo, 2026-04-27)
- `a7b709e6a6dd` micronaut-test = "5.0.0-M8" (Sergio del Amo, 2026-04-27)
- `3ee764589779` micronaut = "5.0.0-M24" (Sergio del Amo, 2026-04-27)
- `d338c25c4c18` Update common files (#607) (micronaut-build, 2026-04-26)
- `3de3431e8f25` [skip ci] Release v7.0.0-M1 (micronaut-build, 2026-02-11)
- `521d4ebae559` Fix native build for jdk 25 (#602) (issam liqali, 2026-02-10)
- `25a31b45480c` Update to Micronaut 5 (#593) (issam liqali, 2026-02-03)
- `db1b5d0842fe` Update common files (#591) (micronaut-build, 2025-12-29)
- `da6eee2ef1e8` Update common files (#569) (micronaut-build, 2025-12-10)
- `3d7cb36919bd` Replace Micronaut nullability annotations with JSpecify nullability annotations (#585) (Copilot, 2025-12-01)
- `74cd22f07064` Update common files (#568) (micronaut-build, 2025-10-20)
- `24b7b0524ff2` Update common files (#566) (micronaut-build, 2025-10-17)
- `5fc3c966a289` micronaut gradle build plugin 8.0.0-M4 (Sergio del Amo, 2025-10-14)
- `f3a707b88fe3` gradle 9.1 (Sergio del Amo, 2025-10-14)
- `247517aaa966` Merge branch '6.9.x' into 7.0.x (Sergio del Amo, 2025-10-14)
- `e071b454817f` Merge branch '6.4.x' into 7.0.x (Sergio del Amo, 2024-04-12)
- `5fcc0e4ba7c4` Update common files (#440) (micronaut-build, 2024-03-28)
- `5535b201d8d5` breaks: delete and doc deprecated code for MN 5 (Dean Wette, 2024-03-19)
- `cbe9875f9012` Update common files (#429) (micronaut-build, 2024-03-18)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` .github/workflows/update-gradle-wrapper.yml
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.cassandra-native-tests.gradle
- `M` cassandra/build.gradle.kts
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` settings.gradle
- `M` test-suite-cassandra-micrometer/build.gradle.kts
- `M` test-suite-graal/build.gradle.kts
- `M` tests/cassandra-jackson/build.gradle.kts
- `M` tests/cassandra-ssl/build.gradle.kts

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
- `A` src/main/docs/guide/breaks.adoc
- `M` src/main/docs/guide/toc.yml

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
- `M` cassandra/src/main/java/io/micronaut/cassandra/health/CassandraHealthIndicator.java
- `M` cassandra/src/main/java/io/micronaut/cassandra/metrics/CassandraMetricsBinder.java
- `A` cassandra/src/main/resources/META-INF/native-image/io.micronaut.cassandra/micronaut-cassandra/native-image.properties
- `M` config/checkstyle/checkstyle.xml

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` cassandra/src/test/groovy/io/micronaut/cassandra/CassandraConfigurationSpec.groovy
- `M` cassandra/src/test/groovy/io/micronaut/cassandra/health/CassandraHealthIndicatorSpec.groovy
- `M` cassandra/src/test/groovy/io/micronaut/cassandra/metrics/CassandraMetricsSpec.groovy
- `M` test-suite-cassandra-micrometer/src/test/groovy/io/micronaut/cassandra/micrometertest/CassandraMetricsSpec.groovy
- `A` test-suite-cassandra-micrometer/src/test/java/io/micronaut/cassandra/micrometertest/Cassandra.java
- `M` test-suite-cassandra-micrometer/src/test/resources/application-test.properties
- `A` test-suite-graal/src/test/java/io/micronaut/cassandra/graaltest/Cassandra.java
- `M` test-suite-graal/src/test/java/io/micronaut/cassandra/graaltest/CassandraTest.java
- `M` test-suite-graal/src/test/resources/application.yml
- `M` tests/cassandra-jackson/src/test/groovy/io/micronaut/cassandra/jacksontest/CassandraHealthEndpointJacksonSpec.groovy
- `M` tests/cassandra-ssl/src/test/groovy/io/micronaut/cassandra/ssltest/CassandraSSLConfigSpec.groovy

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

