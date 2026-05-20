Compared micronaut-flyway as mn4 → mn5.

  Scope

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-flyway, branch 7.9.x, SHA c7925a738a8c
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-flyway, branch 8.0.x, SHA 6afde099fdab
  - Same remote, both clean: git@github.com:micronaut-projects/micronaut-flyway.git
  - Report: /private/tmp/micronaut-flyway-7.9-to-8.0-comparison.md

  Key Findings

  - Major version move: projectVersion 7.9.3-SNAPSHOT -> 8.0.1-SNAPSHOT, Micronaut 4.10.7 -> 5.0.0, Gradle
    8.14.3 -> 9.5.1, Java SDK pin added as 25.0.1-graal.
  - Flyway was upgraded substantially: 10.22.0 -> 12.6.1 for flyway-core, MySQL, Oracle, PostgreSQL, and SQL
    Server artifacts.
  - Platform dependencies moved to Micronaut 5-era baselines: Micronaut Data 4.14.0 -> 5.0.0, SQL 6.3.1 ->
    7.0.1, Serde 2.16.1 -> 3.0.0, Validation 4.12.0 -> 5.0.0.
  - Public source changes are light: mostly migration from Micronaut nullability annotations to JSpecify
    annotations, nullable metadata on Flyway config properties, and an internal simplification of
    FlywayEndpoint.
  - Build/test infrastructure changed more than runtime code: Micronaut Build settings 7.6.4 -> 8.0.0-RC1,
    test-resources catalog removed, Testcontainers dependencies now come from Micronaut Test/Testcontainers
    coordinates, and Oracle tests use a new local OracleFree Testcontainers helper.
  - No project-specific breaking/migration docs changed in this diff; the main compatibility risk is the
    dependency baseline jump, especially Flyway 10.x -> 12.x and Micronaut 4.x -> 5.x.

  Diff size: 62 files changed, 3812 insertions(+), 251 deletions(-). I did not run tests; this was a folder
  comparison and targeted source/build-diff review only.

# Release Note Comparison

Generated: 2026-05-19 13:16 UTC
Comparison: `7.9.x` -> `8.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-flyway` | `7.9.x` | `c7925a738a8c` | `git@github.com:micronaut-projects/micronaut-flyway.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-flyway` | `8.0.x` | `6afde099fdab` | `git@github.com:micronaut-projects/micronaut-flyway.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-flyway`
- Commit candidates found: 162
- File changes listed: 62
- Version values listed: 30
- File status counts: A=26, M=36

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `7.9.3-SNAPSHOT` | `8.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.graal-svm` | `org.graalvm.nativeimage:svm:23.1.8` | `org.graalvm.nativeimage:svm:25.0.3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.gradle-micronaut` | `io.micronaut.gradle:micronaut-gradle-plugin:4.6.0` | `io.micronaut.gradle:micronaut-gradle-plugin:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-flyway` | `org.flywaydb:flyway-core:10.22.0` | `org.flywaydb:flyway-core:12.6.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-flyway-mysql` | `org.flywaydb:flyway-mysql:10.22.0` | `org.flywaydb:flyway-mysql:12.6.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-flyway-oracle` | `org.flywaydb:flyway-database-oracle:10.22.0` | `org.flywaydb:flyway-database-oracle:12.6.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-flyway-postgresql` | `org.flywaydb:flyway-database-postgresql:10.22.0` | `org.flywaydb:flyway-database-postgresql:12.6.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-flyway-sqlserver` | `org.flywaydb:flyway-sqlserver:10.22.0` | `org.flywaydb:flyway-sqlserver:12.6.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-data` | `io.micronaut.data:micronaut-data-bom:4.14.0` | `io.micronaut.data:micronaut-data-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.16.1` | `io.micronaut.serde:micronaut-serde-bom:3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-sql` | `io.micronaut.sql:micronaut-sql-bom:6.3.1` | `io.micronaut.sql:micronaut-sql-bom:7.0.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-resources` | `io.micronaut.testresources:micronaut-test-resources-bom:2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-validation` | `io.micronaut.validation:micronaut-validation-bom:4.12.0` | `io.micronaut.validation:micronaut-validation-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.graal-svm` | `23.1.8` | `25.0.3` | `changed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.24` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.managed-flyway` | `10.22.0` | `12.6.1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.7` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-data` | `4.14.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.6.0` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.1` | `2.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-platform` | `4.10.0` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.16.1` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-sql` | `6.3.1` | `7.0.1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.10.2` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test-resources` | `2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.12.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `dffff72c065a` remove test-resources dependency (#759) (Sergio del Amo, 2025-12-29)
- `fc2dac878674` remove spock supplied by MN Build plugin (Sergio del Amo, 2025-12-10)
- `eea4fc929c14` remove groovy supplied by MN Build plugin (Sergio del Amo, 2025-12-10)
- `8ec13a56a3f6` remove micronaut-test supplied by MN Build plugin (Sergio del Amo, 2025-12-10)
- `ee70fd4b47a7` remove micronaut-docs supplied by MN Build plugin (Sergio del Amo, 2025-12-10)
- `47d09feed6da` remove mainClassName (Sergio del Amo, 2025-10-28)

### Fixes

- `2c76878e41f7` fix(deps): update micronaut dependencies (#847) (renovate[bot], 2026-05-07)
- `55d6d0b752b2` fix(deps): update micronaut dependencies (#844) (renovate[bot], 2026-05-05)
- `44efe34f39c9` fix(deps): update micronaut dependencies (#841) (renovate[bot], 2026-05-04)
- `2ce75a481d3a` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m26 (#839) (renovate[bot], 2026-05-01)
- `60ba0f8b778b` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m8 (#837) (renovate[bot], 2026-04-30)
- `2154f2b03e53` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m25 (#835) (renovate[bot], 2026-04-28)
- `3c5220a1d060` fix(deps): update flyway to v12.5.0 (#834) (renovate[bot], 2026-04-28)
- `8cd5020098c5` fix(deps): update micronaut dependencies (#833) (renovate[bot], 2026-04-23)
- `e280af9b1899` fix(deps): update dependency org.graalvm.nativeimage:svm to v25.0.3 (#832) (renovate[bot], 2026-04-22)
- `6d4221198a78` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v5.0.0-m6 (#831) (renovate[bot], 2026-04-22)
- `feaec40d66fe` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to v7.0.1-m2 (#829) (renovate[bot], 2026-04-21)
- `6221082ad856` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v5.0.0-m2 (#828) (renovate[bot], 2026-04-20)
- `74486019c08b` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m7 (#827) (renovate[bot], 2026-04-19)
- `1322d870cd2c` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m23 (#826) (renovate[bot], 2026-04-19)
- `40b75851003a` fix(deps): update flyway to v12.4.0 (#822) (renovate[bot], 2026-04-15)
- `03afc7503a11` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m22 (#821) (renovate[bot], 2026-04-14)
- `34b7ac0b7297` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m6 (#819) (renovate[bot], 2026-04-03)
- `880c2550b1b2` fix(deps): update flyway to v12.3.0 (#817) (renovate[bot], 2026-04-01)
- `c4cd3026d350` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m19 (#818) (renovate[bot], 2026-04-01)
- `ebc41d6d938e` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m5 (#816) (renovate[bot], 2026-03-28)
- `6d8b4b63c871` fix(deps): update flyway to v12.2.0 (#815) (renovate[bot], 2026-03-27)
- `31112792d495` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m4 (#814) (renovate[bot], 2026-03-26)
- `6041909eae95` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m18 (#813) (renovate[bot], 2026-03-26)
- `b892df7acd37` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m3 (#811) (renovate[bot], 2026-03-25)
- `29a1e1f5f748` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v5.0.0-m5 (#809) (renovate[bot], 2026-03-23)
- `bd3daedcff0f` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to v7.0.1-M1 (#808) (renovate[bot], 2026-03-23)
- `3219146fbcdc` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v5.0.0-m4 (#807) (renovate[bot], 2026-03-20)
- `0458434a5711` fix(deps): update flyway to v12.1.1 (#804) (renovate[bot], 2026-03-18)
- `d41396b2b7d5` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m17 (#802) (renovate[bot], 2026-03-15)
- `f837620cffd1` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v5.0.0-m3 (#800) (renovate[bot], 2026-03-11)
- `61e2c95f22f1` fix(deps): update flyway to v12.1.0 (#799) (renovate[bot], 2026-03-10)
- `442f6e6c9ccd` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m16 (#798) (renovate[bot], 2026-03-08)
- `d4e8b51989d1` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m15 (#794) (renovate[bot], 2026-03-03)
- `ca4e2d90a5fa` fix(deps): update flyway to v12.0.3 (#793) (renovate[bot], 2026-02-28)
- `57b9f644c11d` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m14 (#790) (renovate[bot], 2026-02-26)
- `7745ee340a0d` fix(deps): update flyway to v12.0.2 (#788) (renovate[bot], 2026-02-20)
- `f973be2eb662` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m13 (#789) (renovate[bot], 2026-02-20)
- `477010eee3f8` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to v7.0.0 (#787) (renovate[bot], 2026-02-20)
- `f3890918967e` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m12 (#786) (renovate[bot], 2026-02-19)
- `680fb89add97` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m11 (#785) (renovate[bot], 2026-02-18)
- `26ace28fb0f0` fix(deps): update flyway to v12.0.1 (#783) (renovate[bot], 2026-02-12)
- `65b0c5c3be9a` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m10 (#781) (renovate[bot], 2026-02-05)
- `404873720077` fix(deps): update flyway to v12 (#777) (renovate[bot], 2026-02-04)
- `ea5b94ba66b7` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.2 (#779) (renovate[bot], 2026-02-04)
- `d10ea93fe705` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.5.5 (#720) (renovate[bot], 2025-10-16)
- `4a22ab43111e` fix(deps): update flyway to v11 (#644) (renovate[bot], 2025-06-17)
- `442d64f47b44` fix(deps): update flyway to v11 (major) (#631) (renovate[bot], 2024-12-18)

### Dependency Updates

- `4a7059f3f245` chore: Bump version to 8.0.1-SNAPSHOT (micronaut-build, 2026-05-18)
- `8228a4f5152b` Update Micronaut dependencies (#852) (renovate[bot], 2026-05-13)
- `fc063611d5af` Update dependency io.micronaut.data:micronaut-data-bom to v5.0.0-RC1 (#849) (renovate[bot], 2026-05-08)
- `96adc23c640c` chore: Bump version to 8.0.0-SNAPSHOT (micronaut-build, 2026-05-08)
- `210b1d165ca3` chore(deps): update gradle to v9.5.0 (#842) (renovate[bot], 2026-05-04)
- `08024a729370` chore(deps): update gradle to v9.4.1 (#805) (renovate[bot], 2026-03-20)
- `1e1da4e4604d` chore(deps): update actions/download-artifact action to v8.0.1 (#801) (renovate[bot], 2026-03-14)
- `1b6cce8d0e57` chore(deps): update gradle to v9.4.0 (#797) (renovate[bot], 2026-03-10)
- `88dd2233e978` chore(deps): update github artifact actions (#791) (renovate[bot], 2026-03-03)
- `cf887f22c9f2` chore: Bump version to 8.0.0-SNAPSHOT (micronaut-build, 2026-02-19)
- `3267651e6cec` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#784) (renovate[bot], 2026-02-17)
- `30248df48423` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m16 (#782) (renovate[bot], 2026-02-10)
- `fba1a023291a` Update dependency io.micronaut.data:micronaut-data-bom to v4.14.3 (#775) (renovate[bot], 2026-01-27)
- `48069a2c0345` Update dependency io.micronaut:micronaut-core-bom to v5.0.0-M9 (#774) (renovate[bot], 2026-01-24)
- `7a3d2448b39d` Update dependency org.graalvm.nativeimage:svm to v25.0.2 (#773) (renovate[bot], 2026-01-21)
- `d10207f594ca` Update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-M2 (#770) (renovate[bot], 2026-01-14)
- `407bd18b88b6` Update dependency io.micronaut:micronaut-core-bom to v5.0.0-M8 (#769) (renovate[bot], 2026-01-13)
- `21facb8480c8` Update dependency io.micronaut:micronaut-core-bom to v5.0.0-M7 (#765) (renovate[bot], 2026-01-10)
- `423ec6275715` chore: Bump version to 8.0.0-SNAPSHOT (micronaut-build, 2026-01-02)
- `6a6949fb6820` Update dependency io.micronaut.sql:micronaut-sql-bom to v7.0.0 (#760) (renovate[bot], 2025-12-30)
- `fbd5c912d075` chore: Bump version to 8.0.0-SNAPSHOT (micronaut-build, 2025-12-29)
- `b96dfd99d87c` Update dependency io.micronaut:micronaut-core-bom to v5.0.0-M6 (#754) (renovate[bot], 2025-12-29)
- `8fd83bffa75e` Update dependency io.micronaut.data:micronaut-data-bom to v4.14.2 (#755) (renovate[bot], 2025-12-29)
- `44cf2b0b9d9b` Update dependency org.graalvm.nativeimage:svm to v25 (#743) (renovate[bot], 2025-12-10)
- `1dd47f824dde` Update dependency io.micronaut.sql:micronaut-sql-bom to v7 (#741) (renovate[bot], 2025-12-10)
- `feea040cc454` Update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#742) (renovate[bot], 2025-11-25)
- `1c69c3aa7369` Update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#734) (renovate[bot], 2025-11-11)
- `e5d6578b08d1` Update dependency io.micronaut.data:micronaut-data-bom to v4.14.1 (#733) (renovate[bot], 2025-11-07)
- `f9c5064bde99` Update dependency org.graalvm.nativeimage:svm to v23.1.9 (#730) (renovate[bot], 2025-11-05)
- `849c4bdd5c72` Update dependency io.micronaut.sql:micronaut-sql-bom to v6.3.2 (#729) (renovate[bot], 2025-11-02)
- `58ddb3d57a3d` Update dependency io.micronaut:micronaut-core-bom to v4.10.8 (#728) (renovate[bot], 2025-11-01)
- `cf8186e82452` Update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.1 (#725) (renovate[bot], 2025-10-29)
- `ef13876f7588` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#723) (renovate[bot], 2025-10-28)

### Documentation

- `6f4c1bf97fa1` Docs: update micronaut-docs to 3.0.0 (#718) (issam liqali, 2025-10-16)

### Internal

- `c7e80dd348bd` ci: projectVersion=8.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2024-12-18)

### Review Candidates

- `6afde099fdab` micronaut-data = "5.0.0" (Sergio del Amo, 2026-05-19)
- `989a8950e25f` Update common files (#856) (micronaut-build, 2026-05-19)
- `e08c0c27ee82` [skip ci] Release v8.0.0 (micronaut-build, 2026-05-18)
- `c2c263abccbd` update versions (Sergio del Amo, 2026-05-18)
- `913a9c979e0b` Update versions (Sergio del Amo, 2026-05-14)
- `f15c4a455a91` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `669bd7804668` Update Gradle to v9.5.1 (#854) (renovate[bot], 2026-05-13)
- `bc420222c08d` Update flyway to v12.6.1 (#853) (renovate[bot], 2026-05-12)
- `85ab0432eb70` Update common files (#851) (micronaut-build, 2026-05-09)
- `9df2165fece6` Update flyway to v12.6.0 (#850) (renovate[bot], 2026-05-08)
- `5eb5179be9d1` [skip ci] Release v8.0.0-RC1 (micronaut-build, 2026-05-08)
- `d7a34c14cb1f` Update common files (#848) (micronaut-build, 2026-05-08)
- `94ae6199152c` Update common files (#846) (micronaut-build, 2026-05-07)
- `1b8b23eb3ab5` Update common files (#845) (micronaut-build, 2026-05-06)
- `c6baee6fe85e` Update common files (#840) (micronaut-build, 2026-05-04)
- `d9e449000c76` Update common files (#838) (micronaut-build, 2026-05-01)
- `43984c1aa405` Update common files (#836) (micronaut-build, 2026-04-30)
- `261a544c0815` use javax.persistence.api from data (Sergio del Amo, 2026-04-27)
- `d70829d4ecf7` micronaut-gradle-plugin = "5.0.0-M1" (Sergio del Amo, 2026-04-27)
- `6a0aeae72b5a` Update common files (#830) (micronaut-build, 2026-04-22)
- `150844736014` Update common files (#824) (micronaut-build, 2026-04-20)
- `3ae3d3342c9c` Update common files (#820) (micronaut-build, 2026-04-15)
- `1b30f5a511f7` Update common files (#812) (micronaut-build, 2026-03-25)
- `b2ebc54eb8d8` Update common files (#796) (micronaut-build, 2026-03-18)
- `cca54c7ad4ca` Update common files (#795) (micronaut-build, 2026-03-03)
- `170c4564e73a` [skip ci] Release v8.0.0-M3 (micronaut-build, 2026-02-19)
- `dfd2a64f1104` Update common files (#780) (micronaut-build, 2026-02-05)
- `c7675dd1b3b0` [flyway] Update common files for branch 8.0.x (#766) (micronaut-build, 2026-02-04)
- `258ecc314e8b` Update Gradle to v9.3.1 (#772) (renovate[bot], 2026-02-03)
- `8d8d552d973b` Update plugin io.micronaut.build.shared.settings to v8.0.0-M15 (#778) (renovate[bot], 2026-01-31)
- `3693ea00be6c` Update flyway to v11.20.3 (#776) (renovate[bot], 2026-01-29)
- `9e1c3bc03270` Update flyway to v11.20.2 (#771) (renovate[bot], 2026-01-16)
- `8580eb3fcd6f` Update plugin io.micronaut.build.shared.settings to v8.0.0-M14 (#768) (renovate[bot], 2026-01-12)
- `d3d7060748bb` Update flyway to v11.20.1 (#767) (renovate[bot], 2026-01-11)
- `67f8ebf4d5d2` Update graalvm/setup-graalvm action to v1.4.5 (#763) (renovate[bot], 2026-01-06)
- `3fbb158d63eb` [skip ci] Release v8.0.0-M2 (micronaut-build, 2026-01-02)
- `a4c00184454c` Update common files (#762) (micronaut-build, 2026-01-02)
- `a8e91b38c2f5` Update to flyway 11.20.0 (#761) (issam liqali, 2026-01-02)
- `0ce22cfa3fec` [skip ci] Release v8.0.0-M1 (micronaut-build, 2025-12-29)
- `d88775c54a51` Merge branch '7.9.x' into 8.0.x (Sergio del Amo, 2025-12-29)
- `4206606133bc` define micronaut-test version (Sergio del Amo, 2025-12-29)
- `39588bb2e565` micronaut-platform = "4.10.6" (Sergio del Amo, 2025-12-29)
- `05f7184b9c66` sql = "7.0.0-M4" (Sergio del Amo, 2025-12-29)
- `c9991d582487` Update common files (#753) (micronaut-build, 2025-12-29)
- `73f7c5f948a1` Update actions/cache action to v5 (#756) (renovate[bot], 2025-12-29)
- `df68c2a1a4ba` Update plugin io.micronaut.build.shared.settings to v8.0.0-M13 (#757) (renovate[bot], 2025-12-29)
- `aee6982a3299` Update GitHub Artifact Actions (#758) (renovate[bot], 2025-12-29)
- `c220cd4c99a3` jspecify nullability annotations (Sergio del Amo, 2025-12-10)
- `50cc831097b3` micronaut-validation = "5.0.0-M1" (Sergio del Amo, 2025-12-10)
- `fc105293cfc5` micronaut-serde = "3.0.0-M1" (Sergio del Amo, 2025-12-10)
- `6f1ece788cf2` micronaut = "5.0.0-M2" (Sergio del Amo, 2025-12-10)
- `2cb0f4be561a` Update actions/checkout action to v6.0.1 (#740) (renovate[bot], 2025-12-10)
- `3f79e181cad3` Update mikepenz/action-junit-report action to v6 (#752) (renovate[bot], 2025-12-10)
- `e5036a331fa8` Update softprops/action-gh-release action to v2.5.0 (#749) (renovate[bot], 2025-12-10)
- `a5c15856015e` Update common files (#736) (micronaut-build, 2025-12-10)
- `37408b7e7fe4` Update graalvm/setup-graalvm action to v1.4.4 (#750) (renovate[bot], 2025-12-03)
- `f1f1097b237d` Update plugin io.micronaut.build.shared.settings to v8.0.0-M12 (#746) (renovate[bot], 2025-11-29)
- `2854b94158ba` Update plugin io.micronaut.build.shared.settings to v8.0.0-M11 (#745) (renovate[bot], 2025-11-28)
- `5ae62895fdd3` Update graalvm/setup-graalvm action to v1.4.3 (#744) (renovate[bot], 2025-11-27)
- `abb60bd1067c` Update softprops/action-gh-release action to v2.4.2 (#737) (renovate[bot], 2025-11-15)
- `48b1fa51fb1a` Update plugin io.micronaut.build.shared.settings to v8.0.0-M9 (#735) (renovate[bot], 2025-11-12)
- `fb978dada6f0` Update common files (#731) (micronaut-build, 2025-11-07)
- `0cf8829cebb8` Merge branch '7.9.x' into 8.0.x (Sergio del Amo, 2025-10-28)
- `d17aa7b70b93` Merge branch '7.9.x' into 8.0.x (Sergio del Amo, 2025-10-28)
- `9d9ce05b7280` fix flyway-tests (Sergio del Amo, 2025-10-28)
- `de0d738baba5` Micronaut Build Gradle Plugin 8.0.0-M6 (Sergio del Amo, 2025-10-28)
- `d5ef719e771c` Update common files (#722) (micronaut-build, 2025-10-28)
- `51e8537063e6` Update common files (#721) (micronaut-build, 2025-10-20)
- `a55d0f3f22d9` Update common files (#719) (micronaut-build, 2025-10-16)
- `ff3ccfc3febc` micronaut build 8.0.0-M4 (Sergio del Amo, 2025-10-13)
- `2d9b088f05fd` gradle 9.1 (Sergio del Amo, 2025-10-13)
- `3f89d42cc3a3` Merge branch '7.9.x' into 8.0.x (Sergio del Amo, 2025-10-13)
- `98d1db5adce5` Merge branch '7.8.x' into 8.0.x (Sergio del Amo, 2025-06-17)
- `1e6162b6e1ae` Merge branch '7.7.x' into 8.0.x (Sergio del Amo, 2025-03-05)

## Changed Files

### Compatibility Review

- `M` flyway/src/main/java/io/micronaut/flyway/DataSourceMigrationRunner.java

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.flyway-tests.gradle
- `M` flyway/build.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` settings.gradle
- `M` test-suite-java/build.gradle
- `M` test-suite-oracle/build.gradle.kts
- `M` test-suite-serde/build.gradle.kts

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
- `M` flyway/src/main/java/io/micronaut/flyway/DefaultFlywayConfigurationCustomizer.java
- `M` flyway/src/main/java/io/micronaut/flyway/FlywayConfigurationProperties.java
- `M` flyway/src/main/java/io/micronaut/flyway/StaticResourceProvider.java
- `M` flyway/src/main/java/io/micronaut/flyway/endpoint/FlywayEndpoint.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` flyway/src/test/groovy/io/micronaut/flyway/DataSourceMigrationRunnerSpec.groovy
- `M` flyway/src/test/groovy/io/micronaut/flyway/logging/FlywayLoggingSpec.groovy
- `M` test-suite-oracle/src/main/java/example/micronaut/GenreRepository.java
- `M` test-suite-oracle/src/test/java/example/micronaut/GenreControllerTest.java
- `A` test-suite-oracle/src/test/java/example/micronaut/OracleFree.java

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

