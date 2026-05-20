Compared micronaut-liquibase as mn4 → mn5.

  Scope

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-liquibase, branch 6.9.x, SHA a032d68a22ec
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-liquibase, branch 7.0.x, SHA 5034f7cc195a
  - Same remote, both clean: git@github.com:micronaut-projects/micronaut-liquibase.git
  - Report: /private/tmp/micronaut-liquibase-6.9-to-7.0-comparison.md

  Key Findings

  - Major version move: projectVersion 6.9.1-SNAPSHOT -> 7.0.1-SNAPSHOT, Micronaut 4.9.10 -> 5.0.0, Gradle
    8.14.3 -> 9.5.1, Java SDK pin added as 25.0.1-graal.
  - Liquibase was upgraded from 4.33.0 -> 5.0.2.
  - Platform dependencies moved to Micronaut 5 baselines: Data 4.13.4 -> 5.0.0, SQL 6.2.1 -> 7.0.1, Serde
    2.15.1 -> 3.0.0, Validation 4.10.0 -> 5.0.0, Groovy 4.7.0 -> 5.0.0.
  - Runtime source changes are limited: optional Liquibase configuration getters are now annotated nullable,
    closeDatabase and endpoint datasource resolver handling were made nullable-aware, and
    LiquibaseMigrator.run now explicitly overrides the parent method.
  - Native-image metadata was expanded: reflection config now includes InsertDataChange, and a new resource-
    config.json includes Liquibase XML namespace XSD resources.
  - Build/test infrastructure changed more than product code: Micronaut Build settings 7.6.4 -> 8.0.0-RC1,
    Micronaut Test Resources catalog removed, explicit Testcontainers dependencies added for MariaDB/
    PostgreSQL native test suites, and the Sonatype scan plugin was removed.
  - No product migration/breaking docs changed in this diff; the main compatibility risk is the baseline jump
    to Liquibase 5 and Micronaut 5.

  Diff size: 68 files changed, 4369 insertions(+), 206 deletions(-). I did not run tests; this was a folder
  comparison and targeted source/build-diff review only.

# Release Note Comparison

Generated: 2026-05-19 13:21 UTC
Comparison: `6.9.x` -> `7.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-liquibase` | `6.9.x` | `a032d68a22ec` | `git@github.com:micronaut-projects/micronaut-liquibase.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-liquibase` | `7.0.x` | `5034f7cc195a` | `git@github.com:micronaut-projects/micronaut-liquibase.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-liquibase`
- Commit candidates found: 131
- File changes listed: 68
- Version values listed: 29
- File status counts: A=33, M=35

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `6.9.1-SNAPSHOT` | `7.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.commons-lang3` | `org.apache.commons:commons-lang3:3.18.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.gradle-micronaut` | `io.micronaut.gradle:micronaut-gradle-plugin:4.5.4` | `io.micronaut.gradle:micronaut-gradle-plugin:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-liquibase` | `org.liquibase:liquibase-core:4.33.0` | `org.liquibase:liquibase-core:5.0.2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-data` | `io.micronaut.data:micronaut-data-bom:4.13.4` | `io.micronaut.data:micronaut-data-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-groovy` | `io.micronaut.groovy:micronaut-groovy-bom:4.7.0` | `io.micronaut.groovy:micronaut-groovy-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.15.1` | `io.micronaut.serde:micronaut-serde-bom:3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-sql` | `io.micronaut.sql:micronaut-sql-bom:6.2.1` | `io.micronaut.sql:micronaut-sql-bom:7.0.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-testresources` | `micronaut-testresources:2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-validation` | `io.micronaut.validation:micronaut-validation-bom:4.10.0` | `io.micronaut.validation:micronaut-validation-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.sonatype-scan` | `org.sonatype.gradle.plugins:scan-gradle-plugin:3.1.3` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.commons-lang3` | `3.18.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.24` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.managed-liquibase` | `4.33.0` | `5.0.2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.9.10` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-data` | `4.13.4` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `2.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.5.4` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-groovy` | `4.7.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.0` | `2.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.15.1` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-sql` | `6.2.1` | `7.0.1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.7.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-testresources` | `2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.10.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.sonatype-scan` | `3.1.3` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `69557668d38b` remove test-resources dependency (#731) (Sergio del Amo, 2025-12-29)
- `2eeef86a41f2` remove spock (Sergio del Amo, 2025-12-29)
- `13eb1615e6a4` remove micronaut-docs version (Sergio del Amo, 2025-12-29)
- `2c320c2a2d7f` remove groovy version (Sergio del Amo, 2025-12-29)
- `b1fd7f417368` Build: remove sonatype plugin (#694) (issam liqali, 2025-10-13)

### Fixes

- `250d0bd83ebc` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m26 (#788) (renovate[bot], 2026-05-01)
- `c48730ae1a5c` fix(deps): update micronaut dependencies (#784) (renovate[bot], 2026-04-30)
- `0892af7a79ae` fix(deps): update dependency io.micronaut.groovy:micronaut-groovy-bom to v5.0.0-m2 (#783) (renovate[bot], 2026-04-28)
- `07225d6e2f90` fix(deps): update micronaut dependencies (#782) (renovate[bot], 2026-04-23)
- `d5e11995fa96` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v5.0.0-m6 (#781) (renovate[bot], 2026-04-22)
- `942def214af1` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to v7.0.1-m2 (#779) (renovate[bot], 2026-04-21)
- `5682ecfa6848` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m23 (#776) (renovate[bot], 2026-04-20)
- `4b486c7e9fe7` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m6 (#771) (renovate[bot], 2026-04-15)
- `ae115f583bb0` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m22 (#773) (renovate[bot], 2026-04-15)
- `e93bbc56d46d` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m5 (#770) (renovate[bot], 2026-04-01)
- `3b3d80366d57` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m4 (#769) (renovate[bot], 2026-03-27)
- `6496903e1902` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m18 (#768) (renovate[bot], 2026-03-26)
- `1209ee691549` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m3 (#766) (renovate[bot], 2026-03-25)
- `52347971f409` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v5.0.0-m5 (#764) (renovate[bot], 2026-03-23)
- `c14266ffd8b7` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to v7.0.1-M1 (#763) (renovate[bot], 2026-03-23)
- `1f364dc49467` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v5.0.0-m4 (#761) (renovate[bot], 2026-03-20)
- `f7aec701fd87` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m17 (#758) (renovate[bot], 2026-03-16)
- `f25cc44ab55f` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v5.0.0-m3 (#756) (renovate[bot], 2026-03-12)
- `113b11d338c4` fix(deps): update dependency org.liquibase:liquibase-core to v5.0.2 (#753) (renovate[bot], 2026-03-10)
- `bb1f618d516a` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m16 (#754) (renovate[bot], 2026-03-10)
- `aa4a5ce84a06` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m15 (#751) (renovate[bot], 2026-03-03)
- `b50c2e9ca7c0` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m14 (#749) (renovate[bot], 2026-02-26)
- `819f1e7a05fe` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m13 (#748) (renovate[bot], 2026-02-23)
- `59f1c0696dae` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to v7.0.0-M7 (#747) (renovate[bot], 2026-02-19)
- `1769f6c07482` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m12 (#746) (renovate[bot], 2026-02-19)
- `ee3f269db907` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m10 (#743) (renovate[bot], 2026-02-05)
- `40bf2f49a829` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.2 (#741) (renovate[bot], 2026-02-04)
- `b8eac508cbd9` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m9 (#737) (renovate[bot], 2026-02-03)
- `7b9168123bf1` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m2 (#738) (renovate[bot], 2026-02-03)
- `92f5a3b039dc` fix(deps): update dependency org.liquibase:liquibase-core to v5 (#718) (renovate[bot], 2025-12-29)
- `eb4c6821d70e` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.12 (#728) (renovate[bot], 2025-12-29)
- `b181d2d58f6d` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to v7 (#717) (renovate[bot], 2025-12-16)
- `1cd317d7828f` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.10 (#719) (renovate[bot], 2025-12-16)
- `102c41200eca` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v4.14.2 (#726) (renovate[bot], 2025-12-16)
- `c9e643052e31` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.8 (#705) (renovate[bot], 2025-11-12)
- `5a61e944ef19` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.1 (#706) (renovate[bot], 2025-11-12)
- `2a5fe09dafdb` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v4.14.1 (#708) (renovate[bot], 2025-11-12)
- `448d4fa6430e` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#709) (renovate[bot], 2025-11-12)
- `d048bd1f1996` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to v6.3.2 (#710) (renovate[bot], 2025-11-12)
- `f2ba9aef8220` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.12.0 (#712) (renovate[bot], 2025-11-12)
- `af5a00f3d7e6` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.0 (#697) (renovate[bot], 2025-10-17)
- `2c3feb474502` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.6 (#700) (renovate[bot], 2025-10-17)

### Dependency Updates

- `9ba0e1474c0f` chore: Bump version to 7.0.1-SNAPSHOT (micronaut-build, 2026-05-18)
- `fde8a3a8d5c3` Update Micronaut dependencies (#801) (renovate[bot], 2026-05-13)
- `71db5e6acc0d` Update dependency io.micronaut.data:micronaut-data-bom to v5.0.0-RC1 (#798) (renovate[bot], 2026-05-08)
- `4ae5b463cc17` chore: Bump version to 7.0.0-SNAPSHOT (micronaut-build, 2026-05-08)
- `8bf81e7548b8` Update Micronaut dependencies (#795) (renovate[bot], 2026-05-07)
- `27b242a44ad7` Update dependency io.micronaut.validation:micronaut-validation-bom to v5.0.0-RC1 (#794) (renovate[bot], 2026-05-06)
- `d9b00edb3018` Update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-RC1 (#792) (renovate[bot], 2026-05-05)
- `20c48c52ecdd` Update Micronaut dependencies (#789) (renovate[bot], 2026-05-04)
- `a8358ddc132f` chore(deps): update gradle to v9.5.0 (#786) (renovate[bot], 2026-04-30)
- `67acc48925bf` chore(deps): update gradle to v9.4.0 (#755) (renovate[bot], 2026-03-10)
- `14b43fee18e3` chore(deps): update github artifact actions (#750) (renovate[bot], 2026-03-02)
- `3dcec4a516ea` chore: Bump version to 7.0.0-SNAPSHOT (micronaut-build, 2026-02-19)
- `9a3a098f12fb` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#745) (renovate[bot], 2026-02-19)
- `cfe5576e3c4e` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m16 (#744) (renovate[bot], 2026-02-10)
- `88cf8767c9c7` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m15 (#736) (renovate[bot], 2026-02-03)
- `be6d08922479` chore(deps): update gradle to v9.3.1 (renovate[bot], 2026-01-29)
- `45ebc94d4dcf` chore: Bump version to 7.0.0-SNAPSHOT (micronaut-build, 2025-12-29)
- `21b3ae3a82e8` chore: Bump version to 6.9.1-SNAPSHOT (micronaut-build, 2025-09-04)
- `cd78b0de3cf7` chore(deps): update actions/cache action to v5 (#729) (renovate[bot], 2025-12-29)
- `5482dbf0e060` chore(deps): update github artifact actions (#730) (renovate[bot], 2025-12-29)
- `cf064f102547` chore(deps): update gradle to v9.2.1 (#715) (renovate[bot], 2025-12-16)
- `678ae23c4d9c` chore(deps): update actions/checkout action to v6 (#716) (renovate[bot], 2025-12-16)
- `e08f6983e878` chore(deps): update graalvm/setup-graalvm action to v1.4.4 (#720) (renovate[bot], 2025-12-16)
- `ae42bfa1ccd6` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m13 (#721) (renovate[bot], 2025-12-16)
- `d946e5ed9ee3` chore(deps): update softprops/action-gh-release action to v2.5.0 (#724) (renovate[bot], 2025-12-16)
- `1abce04428bf` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#703) (renovate[bot], 2025-11-12)
- `fef81907f99e` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m9 (#704) (renovate[bot], 2025-11-12)
- `73b432f957c1` chore(deps): update softprops/action-gh-release action to v2.4.2 (#711) (renovate[bot], 2025-11-12)
- `4f9c786a96a7` chore(deps): update gradle to v9.2.0 (#707) (renovate[bot], 2025-11-12)
- `c294a0e2b068` chore(deps): update graalvm/setup-graalvm action to v1.4.1 (#693) (renovate[bot], 2025-10-13)
- `3be0c25ba0bd` chore(deps): update graalvm/setup-graalvm action to v1.3.6 (#691) (renovate[bot], 2025-09-09)

### Documentation

- `ad0b5ced615e` Docs: update micronaut-docs to 3.0.0 (#695) (issam liqali, 2025-10-13)

### Review Candidates

- `5034f7cc195a` micronaut-data = "5.0.0" (Sergio del Amo, 2026-05-19)
- `640df17e8f76` Update common files (#803) (micronaut-build, 2026-05-19)
- `c707178f458a` update versions (Sergio del Amo, 2026-05-18)
- `ca88f5230df1` [skip ci] Release v7.0.0 (micronaut-build, 2026-05-18)
- `7e14de77a0ed` Update versions (Sergio del Amo, 2026-05-14)
- `9de29041b793` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `1711799152f6` Update Gradle to v9.5.1 (#800) (renovate[bot], 2026-05-13)
- `cac58b7eeaec` Update common files (#799) (micronaut-build, 2026-05-09)
- `63751ffc701c` [skip ci] Release v7.0.0-RC1 (micronaut-build, 2026-05-08)
- `2a20c6c63d0d` Update common files (#797) (micronaut-build, 2026-05-08)
- `e3694ca4cfb4` Update common files (#796) (micronaut-build, 2026-05-07)
- `5d520f2f6bda` Update common files (#793) (micronaut-build, 2026-05-06)
- `810c1b9c8ad4` Update Gradle to v9.5.0 (#790) (renovate[bot], 2026-05-04)
- `1a0c56ccd419` [liquibase] Update common files for branch 7.0.x (#787) (micronaut-build, 2026-05-04)
- `edfbf5f9bb35` Update common files (#785) (micronaut-build, 2026-04-30)
- `244468e2aec9` enable native image tests in Micronaut Liquibase (#732) (Sergio del Amo, 2026-04-28)
- `54bbd54a5c09` done define commons-lang3 dep (Sergio del Amo, 2026-04-27)
- `e0c4d99cd491` micronaut-logging = "2.0.0-M2" (Sergio del Amo, 2026-04-27)
- `cc690c712847` micronaut-gradle-plugin = "5.0.0-M1 (Sergio del Amo, 2026-04-27)
- `9a62d701a81c` use persistence.api from mnData (Sergio del Amo, 2026-04-27)
- `eaa1f0aa84e2` Update common files (#780) (micronaut-build, 2026-04-22)
- `c87184f08b6d` Update common files (#774) (micronaut-build, 2026-04-20)
- `fb23a30bef38` Update common files (#772) (micronaut-build, 2026-04-15)
- `dbb295ce8963` Update common files (#767) (micronaut-build, 2026-03-25)
- `7dbff8d16adc` Update common files (#762) (micronaut-build, 2026-03-23)
- `13a941e2cccc` Update common files (#752) (micronaut-build, 2026-03-18)
- `032bfcf7ab8f` [skip ci] Release v7.0.0-M2 (micronaut-build, 2026-02-19)
- `dd9db6c4f65b` Update common files (#742) (micronaut-build, 2026-02-05)
- `4f9942826a82` [liquibase] Update common files for branch 7.0.x (#734) (micronaut-build, 2026-02-03)
- `dcde231269c5` Merge pull request #739 from micronaut-projects/renovate/gradle-9.x (Radovan Radic, 2026-02-03)
- `b9a937ead643` [skip ci] Release v7.0.0-M1 (micronaut-build, 2025-12-29)
- `8468fddbef2d` [skip ci] Release v6.9.0 (micronaut-build, 2025-09-04)
- `68e3f4684b8e` micronaut-validation = "5.0.0-M1" (Sergio del Amo, 2025-12-29)
- `4ade74c374f6` micronaut-sql = "7.0.0-M4" (Sergio del Amo, 2025-12-29)
- `b1f95a1002c2` micronaut-serde = "3.0.0-M1" (Sergio del Amo, 2025-12-29)
- `255c142d5857` micronaut-test = "5.0.0-M3" (Sergio del Amo, 2025-12-29)
- `6847b7fabd76` micronaut = "5.0.0-M6" (Sergio del Amo, 2025-12-29)
- `b1e64c4ac17d` Update common files (#727) (micronaut-build, 2025-12-29)
- `d47d90b6af0e` Update common files (#714) (micronaut-build, 2025-12-16)
- `bf3468705430` Update common files (#702) (micronaut-build, 2025-11-12)
- `8618716b4a0f` Update common files (#699) (micronaut-build, 2025-10-17)
- `5ad0540db4cc` Micronaut Gradle Build Plugin 8.0.0-M4 (Sergio del Amo, 2025-10-13)
- `7dfad0a45cf4` gradle 9.1 (Sergio del Amo, 2025-10-13)
- `b21f239c01d1` logging 1.7.1 (Sergio del Amo, 2025-10-13)
- `a0adf38e55a6` validation 4.11.0 (Sergio del Amo, 2025-10-13)
- `4060a6197c66` data 4.13.7 (Sergio del Amo, 2025-10-13)
- `ee11a1eee8c1` sql 6.2.2 (Sergio del Amo, 2025-10-13)
- `961ebbc908f5` serde 2.15.5 (Sergio del Amo, 2025-10-13)
- `12e9c802ec06` test 4.9.0 (Sergio del Amo, 2025-10-13)
- `c6326fc9990a` core 4.10.4 (Sergio del Amo, 2025-10-13)
- `e1ff640802ba` Update common files (#692) (micronaut-build, 2025-10-13)
- `f63755ff1fa4` projectVersion=7.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-09-04)

## Changed Files

### Compatibility Review

- `M` liquibase/src/main/java/io/micronaut/liquibase/AbstractLiquibaseMigration.java

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` buildSrc/build.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.liquibase-module.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.liquibase.test-suite-graal.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.liquibase.test-suite-module.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` liquibase/build.gradle
- `M` settings.gradle
- `M` test-suite-graal-mariadb/build.gradle.kts
- `M` test-suite-graal-postgres/build.gradle.kts
- `M` test-suite-graal/build.gradle.kts

### Documentation

- `A` .agents/skills/docs/SKILL.md
- `A` .agents/skills/docs/references/control-panel-patterns.md
- `A` .agents/skills/docs/references/micronaut-docs-providers.md
- `A` .agents/skills/guides/SKILL.md
- `A` .agents/skills/guides/references/guide-authoring-conventions.md
- `A` .agents/skills/guides/references/guide-inventory.md
- `A` .agents/skills/guides/references/pdf-export-and-pr.md
- `A` .agents/skills/guides/references/repository-workflow.md
- `A` .clinerules/docs.md
- `A` .github/instructions/docs.instructions.md
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
- `A` .clineignore
- `A` .clinerules/coding.md
- `A` .github/instructions/coding.instructions.md
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
- `M` liquibase/src/main/java/io/micronaut/liquibase/LiquibaseConfigurationProperties.java
- `M` liquibase/src/main/java/io/micronaut/liquibase/LiquibaseMigrator.java
- `M` liquibase/src/main/java/io/micronaut/liquibase/endpoint/LiquibaseEndpoint.java
- `M` liquibase/src/main/java/io/micronaut/liquibase/endpoint/RanChangeSetWrapper.java
- `M` liquibase/src/main/resources/META-INF/native-image/io.micronaut.liquibase/micronaut-liquibase/reflect-config.json
- `A` liquibase/src/main/resources/META-INF/native-image/io.micronaut.liquibase/micronaut-liquibase/resource-config.json

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` liquibase/src/test/groovy/io/micronaut/liquibase/LiquibaseMigrationRunnerSpec.groovy
- `A` test-suite-graal-mariadb/src/test/java/micronaut/example/MariaDb.java
- `M` test-suite-graal-mariadb/src/test/java/micronaut/example/UserControllerTest.java
- `A` test-suite-graal-postgres/src/test/java/micronaut/example/Postgresql.java
- `M` test-suite-graal-postgres/src/test/java/micronaut/example/UserControllerTest.java
- `M` test-suite-graal/src/main/java/micronaut/example/User.java

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

