Compared micronaut-langchain4j as mn4 → mn5.

  Scope

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-langchain4j, branch 1.5.x, SHA dc95813845c2
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-langchain4j, branch 2.0.x, SHA fea2c0065232
  - Same remote, both clean: git@github.com:micronaut-projects/micronaut-langchain4j.git
  - Report: /private/tmp/micronaut-langchain4j-1.5-to-2.0-comparison.md

  Key Findings

  - Major version move: projectVersion 1.5.1-SNAPSHOT -> 2.0.1-SNAPSHOT, Micronaut 4.10.15 -> 5.0.0,
    Micronaut Platform 4.10.8 -> 5.0.0-RC1, Gradle 8.14.3 -> 9.5.0, Java build target 21 -> 25, and .sdkmanrc
    adds 25.0.1-graal.
  - LangChain4j managed versions moved from 1.11.0 -> 1.15.0; community BOM moved from 1.11.0-beta19 ->
    1.15.0-beta25.
  - The LangChain4j BOM aliases were renamed from langchain4j-bom / langchain4j-community-bom to boms-
    langchain4j / boms-langchain4j-community.
  - Public source changes are mostly compatibility work: Micronaut nullability annotations were replaced with
    JSpecify in core/store configuration APIs.
  - Source generation was updated for Micronaut SourceGen 1.8.4 -> 2.0.0, including duplicate generated-class
    protection and builder-method handling.
  - Chat memory behavior has new regression coverage for disabling in-memory chat memory; when
    langchain4j.chat-memory-store.inmemory.enabled=false, the in-memory provider/store beans are absent and
    @MemoryId requires another ChatMemoryProvider.
  - PGVector store creation now resolves proxied/contextual DataSource instances through DataSourceResolver
    before constructing PgVectorEmbeddingStore.
  - Qdrant test-resource support was refactored around a new Qdrant helper and now uses
    org.testcontainers:testcontainers-qdrant.
  - Jlama is now included unconditionally in settings, aligned with the Java 25 baseline.

  Diff size: 128 files changed, 4506 insertions(+), 651 deletions(-). I did not run tests; this was a folder
  comparison and targeted source/build-diff review only.


# Release Note Comparison

Generated: 2026-05-19 13:27 UTC
Comparison: `1.5.x` -> `2.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-langchain4j` | `1.5.x` | `dc95813845c2` | `git@github.com:micronaut-projects/micronaut-langchain4j.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-langchain4j` | `2.0.x` | `fea2c0065232` | `git@github.com:micronaut-projects/micronaut-langchain4j.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-langchain4j`
- Commit candidates found: 165
- File changes listed: 128
- Version values listed: 46
- File status counts: A=30, D=3, M=95

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `1.5.1-SNAPSHOT` | `2.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.astra-db-client` | `com.datastax.astra:astra-db-client:1.2.7` | `com.datastax.astra:astra-db-client:1.2.7` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.awaitility` | `awaitility:4.3.0` | `awaitility:4.3.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.boms-langchain4j` | `not present` | `dev.langchain4j:langchain4j-bom:1.15.0` | `added` |
| `gradle/libs.versions.toml` | `libraries.boms-langchain4j-community` | `not present` | `dev.langchain4j:langchain4j-community-bom:1.15.0-beta25` | `added` |
| `gradle/libs.versions.toml` | `libraries.gradle-micronaut` | `io.micronaut.gradle:micronaut-gradle-plugin:4.6.2` | `io.micronaut.gradle:micronaut-gradle-plugin:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.jinjava` | `com.hubspot.jinjava:jinjava:2.8.1` | `com.hubspot.jinjava:jinjava:2.8.3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.langchain4j-bom` | `dev.langchain4j:langchain4j-bom:1.11.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.langchain4j-community-bom` | `dev.langchain4j:langchain4j-community-bom:1.11.0-beta19` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.testcontainers-redis` | `com.redis:testcontainers-redis:2.2.4` | `com.redis:testcontainers-redis:2.2.4` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.astra-db-client` | `1.2.7` | `1.2.7` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.awaitility` | `4.3.0` | `4.3.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.commons-compress` | `1.27.1` | `1.28.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.commons-lang3` | `3.18.0` | `3.20.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.29` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.grpc-netty-shaded` | `not present` | `1.75.0` | `added` |
| `gradle/libs.versions.toml` | `versions.gson` | `2.12.0` | `2.14.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.jinjava` | `2.8.1` | `2.8.3` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-langchain4j` | `1.11.0` | `1.15.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-langchain4j-community` | `1.11.0-beta19` | `1.15.0-beta25` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.15` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-elasticsearch` | `5.10.0` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.6.2` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-groovy` | `4.7.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-grpc` | `4.12.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-kotlin` | `4.7.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.3` | `2.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-mongodb` | `5.7.0` | `6.0.1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-neo4j` | `7.0.0` | `8.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-opensearch` | `1.6.0` | `2.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-oraclecloud` | `5.5.2` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-platform` | `4.10.8` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-reactor` | `3.9.1` | `4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-redis` | `6.9.0` | `7.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.16.2` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-sourcegen` | `1.8.4` | `2.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-sql` | `6.3.3` | `7.0.1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.10.2` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test-resources` | `2.10.1` | `4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.testcontainers-redis` | `2.2.4` | `2.2.4` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.tools-jackson-core` | `not present` | `3.1.3` | `added` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.0` | `changed` |
| `settings.gradle.kts` | `plugin.io.micronaut.build.shared.settings` | `7.6.6` | `8.0.0-M18` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `1f07311deaf0` remove unused imports (Sergio del Amo, 2026-03-04)
- `1f3855ac08cb` remove public modifier (Sergio del Amo, 2026-03-04)
- `dbc3f26b7397` remove duplicated application.properties file (Sergio del Amo, 2026-03-03)
- `a44845479a8f` build: remove langchain4j-java-library (Sergio del Amo, 2026-03-03)
- `4dcbf03d823e` remove kotlin version (Sergio del Amo, 2025-12-09)
- `a2b22230972a` remove micronaut-test (Sergio del Amo, 2025-12-09)
- `434783bac493` Build: remove sonatype plugin (#207) (issam liqali, 2025-10-14)

### Features

- `d59c309e957b` Add regression coverage for disabled in-memory chat (#319) (Graeme Rocher, 2026-05-07)

### Fixes

- `b3aeabb99e3e` Correct sourcegen (#298) (Denis Stepanov, 2026-03-04)
- `87c254f12af5` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m14 (#294) (renovate[bot], 2026-03-02)
- `15c6b29efcd3` fix(deps): update dependency org.junit:junit-bom to v6.0.3 (#293) (renovate[bot], 2026-02-23)
- `66173f52a3f8` fix(deps): update dependency io.micronaut.sourcegen:micronaut-sourcegen-bom to v2.0.0-m2 (#292) (renovate[bot], 2026-02-23)
- `460a7e35c501` fix(deps): update dependency io.micronaut.logging:micronaut-logging-bom to v2.0.0-m2 (#291) (renovate[bot], 2026-02-23)
- `da2ae09a26ed` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m13 (#290) (renovate[bot], 2026-02-20)
- `eec05383cbf0` fix(deps): update dependency io.micronaut.oraclecloud:micronaut-oraclecloud-bom to v5.6.2 (#286) (renovate[bot], 2026-02-16)
- `bac5ca431969` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.2 (#282) (renovate[bot], 2026-02-12)
- `da02f275a558` fix(deps): update dependency org.apache.commons:commons-compress to v1.28.0 (#251) (renovate[bot], 2026-02-09)
- `d54801e93950` fix(deps): update dependency org.apache.commons:commons-lang3 to v3.20.0 (#252) (renovate[bot], 2026-02-09)
- `898b48acd22f` fix(deps): update dependency com.hubspot.jinjava:jinjava to v2.8.3 (#277) (renovate[bot], 2026-02-09)
- `d68d8f245a2d` fix(deps): update dependency io.micronaut.mongodb:micronaut-mongo-bom to v6 (#262) (renovate[bot], 2026-02-09)
- `9845fc49709e` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to v7 (#263) (renovate[bot], 2026-02-09)
- `09480bbc29d4` fix(deps): update dependency org.postgresql:postgresql to v42.7.9 (#269) (renovate[bot], 2026-02-09)
- `d053238b457c` fix(deps): update dependency io.micronaut.sourcegen:micronaut-sourcegen-bom to v1.8.4 (#256) (renovate[bot], 2026-02-09)
- `f05afa937564` fix(deps): update dependency org.junit:junit-bom to v6 (#264) (renovate[bot], 2026-02-09)
- `633c36f8071d` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to v6.3.3 (#271) (renovate[bot], 2026-02-09)
- `63f833cc70b8` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m2 (#267) (renovate[bot], 2026-02-09)
- `5dd3db1f3d1f` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m10 (#250) (renovate[bot], 2026-02-09)
- `b82ed56d33de` fix(deps): update dependency dev.langchain4j:langchain4j-bom to v1.11.0 (#257) (renovate[bot], 2026-02-09)
- `60987cb23ba0` fix(deps): update dependency org.junit:junit-bom to v5.14.2 (#254) (renovate[bot], 2026-02-09)
- `ff4d636b39ba` fix(deps): update dependency com.hubspot.jinjava:jinjava to v2.8.2 (#225) (renovate[bot], 2025-12-09)
- `d01df622e8d8` fix(deps): update dependency org.postgresql:postgresql to v42.7.8 (#231) (renovate[bot], 2025-12-09)
- `7ed7a64ccc61` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#238) (renovate[bot], 2025-12-09)
- `bb5311ecb757` fix(deps): update dependency dev.langchain4j:langchain4j-bom to v1.9.1 (#247) (renovate[bot], 2025-12-09)
- `63fdd24735d4` fix(deps): update dependency com.google.code.gson:gson to v2.13.2 (#246) (renovate[bot], 2025-12-09)
- `e045fdd0ebda` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.1 (#248) (renovate[bot], 2025-12-09)
- `7a5a5913c21b` fix(deps): update dependency io.micronaut.oraclecloud:micronaut-oraclecloud-bom to v5.6.1 (#249) (renovate[bot], 2025-12-09)
- `2bba616a4ce5` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#227) (renovate[bot], 2025-11-24)
- `fbf0c8970072` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to v6.3.2 (#230) (renovate[bot], 2025-11-24)
- `577f42ed4d0a` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.6 (#215) (renovate[bot], 2025-10-17)
- `b5dc0e60ce6b` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.5.5 (#206) (renovate[bot], 2025-10-14)

### Security

- `c7598ef74ddc` security ignore GHSA-rcgg-9c38-7xpx (Sergio del Amo, 2026-05-18)

### Dependency Updates

- `1dc47ce43c4a` chore: Bump version to 2.0.1-SNAPSHOT (micronaut-build, 2026-05-18)
- `cd0df539dd71` Bump LangChain4j managed versions (Sergio del Amo, 2026-05-18)
- `5d7cc8053cb6` chore: Bump version to 2.0.0-SNAPSHOT (micronaut-build, 2026-05-07)
- `d7cfde871a64` Update dependency tools.jackson.core:jackson-core to v3.1.3 (#329) (renovate[bot], 2026-05-04)
- `1526e6d587ce` Update dependency com.google.code.gson:gson to v2.14.0 (#317) (renovate[bot], 2026-04-30)
- `a1dbb03b6860` Update dependency dev.langchain4j:langchain4j-bom to v1.13.1 (#305) (renovate[bot], 2026-04-30)
- `c70042a29980` Update Micronaut dependencies (#316) (renovate[bot], 2026-04-30)
- `58d93b2597fd` Update dependency io.micronaut:micronaut-core-bom to v5.0.0-M24 (#312) (renovate[bot], 2026-04-22)
- `46a338405510` Update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-M6 (#311) (renovate[bot], 2026-04-10)
- `ff87260fae50` Update dependency io.micronaut:micronaut-core-bom to v5.0.0-M20 (#307) (renovate[bot], 2026-04-10)
- `bc690c3da44b` Update dependency io.micronaut:micronaut-core-bom to v5.0.0-M16 (#304) (renovate[bot], 2026-03-09)
- `8f7b93ed29fd` chore: Bump version to 2.0.0-SNAPSHOT (micronaut-build, 2026-03-06)
- `2eee81f21a29` Update dependency org.postgresql:postgresql to v42.7.10 (#296) (renovate[bot], 2026-03-05)
- `43634ff4a72f` chore(deps): update actions/checkout action to v6 (#297) (renovate[bot], 2026-03-03)
- `13482a464c0a` chore(deps): update plugin micronaut-build-shared-settings to v8.0.0-m17 (#289) (renovate[bot], 2026-02-20)
- `b7f04623c165` java version 25 (Sergio del Amo, 2026-02-16)
- `0b8d9f3b3589` chore(deps): update plugin micronaut-build-shared-settings to v8.0.0-m16 (#280) (renovate[bot], 2026-02-12)
- `35885476ac63` chore(deps): update gradle to v9.3.1 (#270) (renovate[bot], 2026-02-09)
- `bff7f2b7822b` chore(deps): update graalvm/setup-graalvm action to v1.4.5 (#265) (renovate[bot], 2026-02-09)
- `5ad7928d0030` chore(deps): update stefanzweifel/git-auto-commit-action action to v7 (#261) (renovate[bot], 2026-02-09)
- `f9b3d71f8df0` chore(deps): update gradle/actions action to v5 (#260) (renovate[bot], 2026-02-09)
- `21d5047fea68` chore(deps): update plugin micronaut-build-shared-settings to v8.0.0-m15 (#253) (renovate[bot], 2026-02-09)
- `f78087172c91` chore(deps): update plugin micronaut-build-shared-settings to v8.0.0-m12 (#241) (renovate[bot], 2025-12-09)
- `f824768e6435` chore(deps): update graalvm/setup-graalvm action to v1.4.4 (#240) (renovate[bot], 2025-12-09)
- `a59fb202be78` chore(deps): update dependency com.google.devtools.ksp to v2.3.3 (#244) (renovate[bot], 2025-12-09)
- `af065860c633` chore(deps): update softprops/action-gh-release action to v2.5.0 (#245) (renovate[bot], 2025-12-09)
- `def1056764d1` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#222) (renovate[bot], 2025-11-24)
- `45779c14b768` chore(deps): update softprops/action-gh-release action to v2.4.2 (#226) (renovate[bot], 2025-11-24)
- `868a4402db21` chore(deps): update plugin micronaut-build-shared-settings to v8.0.0-m9 (#223) (renovate[bot], 2025-11-24)
- `73ebc68da2bd` chore(deps): update plugin micronaut-build-shared-settings to v8.0.0-m4 (#213) (renovate[bot], 2025-10-16)
- `9bb2aadb4db5` chore(deps): update graalvm/setup-graalvm action to v1.4.1 (#199) (renovate[bot], 2025-10-14)
- `aee2de75b27f` chore(deps): update softprops/action-gh-release action to v2.3.3 (#204) (renovate[bot], 2025-10-01)

### Documentation

- `0bd6e000aa70` Docs: update micronaut-docs to 3.0.0 (#210) (issam liqali, 2025-10-14)

### Internal

- `269b48a16a40` ci: delete ISSUE_TEMPLATE (Sergio del Amo, 2025-10-14)
- `55bb6071a282` ci: projectVersion=2.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-09-29)

### Review Candidates

- `fea2c0065232` update versions (Sergio del Amo, 2026-05-19)
- `16ca5dadf767` [skip ci] Release v2.0.0 (micronaut-build, 2026-05-18)
- `c9176c0761ee` micronaut-oraclecloud = "6.0.0" (Sergio del Amo, 2026-05-18)
- `d18505ceb08d` update versions (Sergio del Amo, 2026-05-18)
- `da38b2f1b076` update versions (Sergio del Amo, 2026-05-17)
- `f5e97f76e698` update versions (Sergio del Amo, 2026-05-14)
- `fb87f1d844b8` Update common files (#335) (micronaut-build, 2026-05-13)
- `2a1c52666d60` Update (Sergio del Amo, 2026-05-13)
- `e01e87356189` [skip ci] Release v2.0.0-RC1 (micronaut-build, 2026-05-07)
- `fb3f084784c9` ignore .kotlin (Sergio del Amo, 2026-05-07)
- `fe124b858115` micronaut-platform = "5.0.0-M3" (Sergio del Amo, 2026-05-07)
- `2a376cd3a5f4` update versions (Sergio del Amo, 2026-05-07)
- `251e5c220387` Update langchain4j 1.14.0 (#334) (Sergio del Amo, 2026-05-07)
- `d022f63d7246` Update gradle/actions action to v6 (#310) (renovate[bot], 2026-05-07)
- `d1f37f44097e` Update common files (#333) (micronaut-build, 2026-05-07)
- `7b67873cecb0` Update common files (#331) (micronaut-build, 2026-05-05)
- `b23b26989309` [langchain4j] Update common files for branch 2.0.x (#327) (micronaut-build, 2026-05-04)
- `5d69e7e3c0b1` Fix PGVector store creation with proxied data sources (#324) (Graeme Rocher, 2026-05-01)
- `b2e8afb20bdc` Update common files (#321) (micronaut-build, 2026-05-01)
- `babe1c23ad11` Update Gradle to v9.5.0 (#308) (renovate[bot], 2026-04-30)
- `274651889467` Update common files (#318) (micronaut-build, 2026-04-30)
- `244a1b33dbf9` Update common files (#306) (micronaut-build, 2026-04-26)
- `e9e5002b82e7` [skip ci] Release v2.0.0-M1 (micronaut-build, 2026-03-06)
- `101311d21bd5` enable micronaut-langchain4j-store-elasticsearch module (#300) (Sergio del Amo, 2026-03-06)
- `e40aff99b250` expose langchain4j boms with boms- (#288) (Sergio del Amo, 2026-03-05)
- `8adf9a0bfa84` Update common files (#302) (micronaut-build, 2026-03-05)
- `7532bbba8f67` Enable neo4j tests (#301) (Sergio del Amo, 2026-03-04)
- `74d4646a9e3f` don’t use test resources for Qdrant tests (Sergio del Amo, 2026-03-04)
- `e1d30dd39a21` don’t define JUnit BOM (Sergio del Amo, 2026-03-04)
- `f0e13bbf10e8` use junit jupiter from mnTest (Sergio del Amo, 2026-03-04)
- `6943500f7df1` change regex pattern for EnabledIfEnvironmentVariable (Sergio del Amo, 2026-03-04)
- `93c50a69a13d` use mnTest.junit.platform.launcher (Sergio del Amo, 2026-03-04)
- `d05375038c11` disable tests in CI (Sergio del Amo, 2026-03-04)
- `db204e9d54cd` temporarily disable module micronaut-langchain4j-store-elasticsearch (Sergio del Amo, 2026-03-03)
- `7c5342f7a968` del test-resources from langchain4j-store-opensearch (Sergio del Amo, 2026-03-03)
- `80eb8bd138b0` disable neo4j tests (Sergio del Amo, 2026-03-03)
- `bf9f28f469ce` del test-resources from langchain4j-store-neo4j (Sergio del Amo, 2026-03-03)
- `82973c85da89` del test resources from langchain4j-store-mongodb (Sergio del Amo, 2026-03-03)
- `ef81f764d4aa` disabled ocigenai tests (Sergio del Amo, 2026-03-03)
- `4f3607022b61` del testResources from micronaut-langchain4j-core (Sergio del Amo, 2026-03-03)
- `82c5fb3fd42b` Update common files (#299) (micronaut-build, 2026-03-03)
- `4ad5b8d1b05a` Revert "micronaut Build java 25" (Sergio del Amo, 2026-03-03)
- `055872ca60a0` use java base for test-suite-utils (Sergio del Amo, 2026-03-03)
- `310f264e326f` micronaut-test-resources = "4.0.0-M1" (Sergio del Amo, 2026-03-03)
- `b7fe14db6aa3` micronaut Build java 25 (Sergio del Amo, 2026-03-02)
- `797c98d9697a` java 25 not 21 (Sergio del Amo, 2026-03-02)
- `dfbadae157a4` micronaut-oraclecloud = "6.0.0-M1" (Sergio del Amo, 2026-03-02)
- `a892e27fae02` micronaut-redis = "7.0.0-M1" (Sergio del Amo, 2026-03-02)
- `502dcb5bd915` micronaut-grpc = "5.0.0-M1" (Sergio del Amo, 2026-03-02)
- `ad8c9ad551e4` micronaut-kotlin = "5.0.0-M1" (Sergio del Amo, 2026-03-02)
- `34d9330376da` micronaut-sql = "7.0.0-M7" (Sergio del Amo, 2026-03-02)
- `b7ad12812548` micronaut-groovy = "5.0.0-M1" (Sergio del Amo, 2026-03-02)
- `ba2bf4c4b0e0` micronaut = "5.0.0-M15" (Sergio del Amo, 2026-03-02)
- `a13fee26ce08` micronaut-platform = "4.10.9" (Sergio del Amo, 2026-03-02)
- `35e9936d7e5c` Merge branch '1.5.x' into 2.0.x (Sergio del Amo, 2026-03-02)
- `e778522f88a5` use testcontainers bom from mnTest (Sergio del Amo, 2026-02-16)
- `4cf37ed2b91b` testcontainers (Sergio del Amo, 2026-02-16)
- `edfce80bd610` micronaut reactor (Sergio del Amo, 2026-02-16)
- `8cf41dab4a11` micronaut-test-resources = "3.0.0-M6" (Sergio del Amo, 2026-02-16)
- `1eb260c13386` micronaut-sql = "7.0.0-M6" (Sergio del Amo, 2026-02-16)
- `05a9fffce472` micronaut-sql = "7.0.0-M6" (Sergio del Amo, 2026-02-16)
- `d385d6bfb153` micronaut-sql = "7.0.0-M6" (Sergio del Amo, 2026-02-16)
- `a81ddcde07c9` micronaut-reactor (Sergio del Amo, 2026-02-16)
- `125433b13fc4` langchain4j community 1.11.0-beta19 (Sergio del Amo, 2026-02-16)
- `ed68846afa4e` Merge branch '1.5.x' into 2.0.x (Sergio del Amo, 2026-02-16)
- `f11ac00e57c5` Update common files (#281) (micronaut-build, 2026-02-12)
- `36a1cea5f4d6` micronaut-test-resources = "3.0.0-M2" (Sergio del Amo, 2026-02-09)
- `6bd31535d1f6` micronaut-sourcegen = "2.0.0-M1" (Sergio del Amo, 2026-02-09)
- `66ab1be1a3d4` micronaut-elasticsearch = "6.0.0-M1" (Sergio del Amo, 2026-02-09)
- `2acdeb395b17` micronaut-mongodb = "6.0.1-M1" (Sergio del Amo, 2026-02-09)
- `baf7545ea5e3` micronaut-neo4j = "8.0.0-M1" (Sergio del Amo, 2026-02-09)
- `02548c08b7ea` micronaut-sql = "7.0.0-M4" (Sergio del Amo, 2026-02-09)
- `b035ff826b42` micronaut-platform = "4.10.7" (Sergio del Amo, 2026-02-09)
- `dc14518da4c3` Update common files (#258) (micronaut-build, 2026-02-09)
- `21866e80f28d` Merge branch '1.5.x' into 2.0.x (Sergio del Amo, 2025-12-09)
- `c99067018f9f` fix ExecuteableMethodProcessor::process overrid (Sergio del Amo, 2025-12-09)
- `75112f1c2d12` use JSpecify nullability annotations (Sergio del Amo, 2025-12-09)
- `41732ee134f3` micronaut-serde = "3.0.0-M1" (Sergio del Amo, 2025-12-09)
- `b4582cbec950` micronaut = "5.0.0-M2" (Sergio del Amo, 2025-12-09)
- `b4ce583128c2` Update common files (#239) (micronaut-build, 2025-12-09)
- `1631f4fa4397` Replace Micronaut nullability annotations with JSpecify annotations (#243) (Copilot, 2025-12-02)
- `2cdb1a124f49` Update common files (#221) (micronaut-build, 2025-11-24)
- `fe0faed51ee7` Merge branch '1.4.x' into 2.0.x (Sergio del Amo, 2025-11-24)
- `bd23eeb7806c` Update common files (#216) (micronaut-build, 2025-10-21)
- `183aa5f87435` Update common files (#214) (micronaut-build, 2025-10-16)
- `7868268ee561` Merge branch '1.4.x' into 2.0.x (Sergio del Amo, 2025-10-14)
- `e21eade65129` build micronaut langchain4j with gradle 9.1.0 (#209) (araysse, 2025-10-14)
- `584803cc0834` Update common files (#203) (micronaut-build, 2025-10-14)
- `8880383cd39e` update micronaut-langchain4j to gradle v9.1.0 (#205) (araysse, 2025-10-14)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` .github/workflows/update-gradle-wrapper.yml
- `M` build.gradle.kts
- `M` buildSrc/build.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.langchain4j-example.gradle
- `D` buildSrc/src/main/groovy/io.micronaut.build.internal.langchain4j-java-library.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.langchain4j-module.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` micronaut-langchain4j-core/build.gradle.kts
- `M` micronaut-langchain4j-jlama/build.gradle.kts
- `M` micronaut-langchain4j-oci-genai/build.gradle.kts
- `M` micronaut-langchain4j-ollama-testresource/build.gradle.kts
- `M` micronaut-langchain4j-openai/build.gradle.kts
- `M` micronaut-langchain4j-qdrant-testresource/build.gradle.kts
- `M` micronaut-langchain4j-store-elasticsearch/build.gradle.kts
- `M` micronaut-langchain4j-store-mongodb/build.gradle.kts
- `M` micronaut-langchain4j-store-neo4j/build.gradle.kts
- `M` micronaut-langchain4j-store-opensearch/build.gradle.kts
- `M` micronaut-langchain4j-store-pgvector/build.gradle.kts
- `M` micronaut-langchain4j-store-redis/build.gradle.kts
- `M` micronaut-langchain4j-vertexai-gemini/build.gradle.kts
- `M` micronaut-langchain4j-vertexai/build.gradle.kts
- `M` settings.gradle.kts
- `M` test-suite-chatmodel-tck/build.gradle.kts
- `M` test-suite-groovy/build.gradle.kts
- `M` test-suite-kotlin/build.gradle.kts
- `M` test-suite-utils/build.gradle.kts
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
- `M` .clinerules/docs.md
- `M` .github/instructions/docs.instructions.md
- `M` .github/workflows/release.yml
- `M` doc-examples/example-java/build.gradle.kts
- `M` doc-examples/example-openai-java/build.gradle.kts
- `M` doc-examples/example-openai-java/src/main/resources/application.properties
- `M` doc-examples/example-openai-java/src/test/java/example/openai/RAGTest.java
- `M` doc-examples/example-openai-java/src/test/java/example/openai/ToolTest.java

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
- `M` .github/workflows/.rsync-filter
- `M` .github/workflows/central-sync.yml
- `D` .github/workflows/files-sync.yml
- `M` .github/workflows/graalvm-dev.yml
- `M` .github/workflows/publish-snapshot.yml
- `A` .github/workflows/sonatype.yml
- `M` .gitignore
- `A` .sdkmanrc
- `M` MAINTAINING.md
- `M` config/checkstyle/checkstyle.xml
- `M` micronaut-langchain4j-cassandra/src/main/java/io/micronaut/langchain4j/cassandra/memory/CassandraChatMemoryStoreConfiguration.java
- `M` micronaut-langchain4j-cassandra/src/main/java/io/micronaut/langchain4j/cassandra/memory/CassandraChatMemoryStoreConfigurationProperties.java
- `M` micronaut-langchain4j-core/src/main/java/io/micronaut/langchain4j/aiservices/AiServiceCustomizer.java
- `M` micronaut-langchain4j-core/src/main/java/io/micronaut/langchain4j/aiservices/AiServiceDef.java
- `M` micronaut-langchain4j-core/src/main/java/io/micronaut/langchain4j/aiservices/AiServiceFactory.java
- `M` micronaut-langchain4j-core/src/main/java/io/micronaut/langchain4j/embedding/InMemoryEmbeddingStoreConfig.java
- `M` micronaut-langchain4j-core/src/main/java/io/micronaut/langchain4j/interceptor/AiServiceInterceptor.java
- `M` micronaut-langchain4j-core/src/main/java/io/micronaut/langchain4j/store/memory/chat/MessageWindowChatMemoryConfiguration.java
- `M` micronaut-langchain4j-core/src/main/java/io/micronaut/langchain4j/store/memory/chat/MessageWindowChatMemoryConfigurationProperties.java
- `M` micronaut-langchain4j-core/src/main/java/io/micronaut/langchain4j/store/memory/chat/MessageWindowChatMemoryFactory.java
- `M` micronaut-langchain4j-core/src/main/java/io/micronaut/langchain4j/tools/ToolRegistry.java
- `M` micronaut-langchain4j-openai/src/main/java/io/micronaut/langchain4j/openai/OpenAiModule.java
- `M` micronaut-langchain4j-processor/src/main/java/io/micronaut/langchain4j/processor/Langchain4jConfigVisitor.java
- `M` micronaut-langchain4j-store-mongodb/src/main/java/io/micronaut/langchain4j/mongodb/atlas/NamedMongoDbAtlasEmbeddingStoreConfig.java
- `M` micronaut-langchain4j-store-neo4j/src/main/java/io/micronaut/langchain4j/neo4j/memory/Neo4jChatMemoryStoreConfiguration.java
- `M` micronaut-langchain4j-store-neo4j/src/main/java/io/micronaut/langchain4j/neo4j/memory/Neo4jChatMemoryStoreConfigurationProperties.java
- `M` micronaut-langchain4j-store-pgvector/src/main/java/io/micronaut/langchain4j/pgvector/PgVectorEmbeddingStoreConfig.java
- `M` micronaut-langchain4j-store-pgvector/src/main/java/io/micronaut/langchain4j/pgvector/PgVectorEmbeddingStoreFactory.java
- `M` micronaut-langchain4j-store-redis/src/main/java/io/micronaut/langchain4j/redis/memory/RedisChatMemoryStoreConfiguration.java
- `A` osv-scanner.toml

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `A` micronaut-langchain4j-core/src/test/java/io/micronaut/langchain4j/aiservices/DisabledInMemoryAiServiceMemoryIdTest.java
- `A` micronaut-langchain4j-core/src/test/java/io/micronaut/langchain4j/store/memory/chat/inmemorytests/DisabledInMemoryMessageWindowChatMemoryProviderTest.java
- `M` micronaut-langchain4j-oci-genai/src/test/java/io/micronaut/langchain4j/ocigenai/OciGenAiTest.java
- `A` micronaut-langchain4j-qdrant-testresource/src/main/java/io/micronaut/langchain4j/testresources/qdrant/Qdrant.java
- `M` micronaut-langchain4j-qdrant-testresource/src/main/java/io/micronaut/langchain4j/testresources/qdrant/QdrantTestContainerProvider.java
- `M` micronaut-langchain4j-store-neo4j/src/test/java/io/micronaut/langchain4j/neo4j/Neo4jTest.java
- `M` micronaut-langchain4j-store-neo4j/src/test/java/io/micronaut/langchain4j/neo4j/memory/Neo4jChatMemoryStoreConfigurationTest.java
- `A` micronaut-langchain4j-store-pgvector/src/test/java/io/micronaut/langchain4j/pgvector/PgVectorEmbeddingStoreFactoryTest.java
- `M` test-suite-groovy/src/test/groovy/example/micronaut/InMemoryAssistantWithMemoryTest.groovy
- `M` test-suite-groovy/src/test/groovy/example/micronaut/MusicianAssistantTest.groovy
- `M` test-suite-groovy/src/test/groovy/example/micronaut/OllamaChatModelBuilderListener.groovy
- `M` test-suite-groovy/src/test/groovy/example/micronaut/aiservice/AiServiceTest.groovy
- `M` test-suite-kotlin/src/test/kotlin/example/micronaut/InMemoryAssistantWithMemoryTest.kt
- `M` test-suite-kotlin/src/test/kotlin/example/micronaut/MusicianAssistantTest.kt
- `M` test-suite-kotlin/src/test/kotlin/example/micronaut/OllamaChatModelBuilderListener.kt
- `M` test-suite-kotlin/src/test/kotlin/example/micronaut/aiservice/AiServiceTest.kt
- `M` test-suite-utils/src/main/java/io/micronaut/langchain4j/testutils/Neo4jUtils.java
- `M` test-suite-utils/src/main/java/io/micronaut/langchain4j/testutils/OllamaTestPropertyProvider.java
- `D` test-suite-utils/src/main/resources/application.properties
- `M` test-suite/src/test/java/example/micronaut/AssistantWithoutMemoryTest.java
- `M` test-suite/src/test/java/example/micronaut/CassandraAssistantWithMemoryTest.java
- `M` test-suite/src/test/java/example/micronaut/InMemoryAssistantWithMemoryTest.java
- `M` test-suite/src/test/java/example/micronaut/MusicianAssistantTest.java
- `M` test-suite/src/test/java/example/micronaut/Neo4jAssistantWithMemoryTest.java
- `M` test-suite/src/test/java/example/micronaut/OllamaChatModelBuilderListener.java
- `M` test-suite/src/test/java/example/micronaut/RedisAssistantWithMemoryTest.java
- `M` test-suite/src/test/java/example/micronaut/aiservice/AiServiceMemoryIdTest.java
- `M` test-suite/src/test/java/example/micronaut/aiservice/AiServiceTest.java
- `M` test-suite/src/test/java/example/micronaut/aiservice/tools/OllamaToolTest.java

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

