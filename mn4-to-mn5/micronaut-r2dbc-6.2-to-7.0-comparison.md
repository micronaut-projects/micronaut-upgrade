Compared micronaut-r2dbc as mn4 → mn5.

  Scope

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-r2dbc, branch 6.2.x, SHA 7157838
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-r2dbc, branch 7.0.x, SHA 410a328
  - Report: /private/tmp/micronaut-r2dbc-6.2-to-7.0-comparison.md

  Key Findings

  - projectVersion moves from 6.2.1-SNAPSHOT to 7.0.2-SNAPSHOT.
  - Core platform moves to Micronaut 5.0.0; Gradle wrapper moves 8.14.3 → 9.5.1; Java 25.0.1-graal is added
    via .sdkmanrc.
  - Major Micronaut integrations move forward: Data 4.13.8 → 5.0.0-RC1, SQL 6.3.1 → 7.0.1, Flyway 7.8.0 →
    8.0.0-RC1, Reactor 3.9.1 → 4.0.0, Serde 2.15.5 → 3.0.0.
  - R2DBC drivers were updated, including H2 1.0.0 → 1.1.0, MariaDB 1.3.0 → 1.4.0, MSSQL 1.0.3 → 1.0.4, MySQL
    1.4.1 → 1.4.2, PostgreSQL 1.1.0 → 1.1.1.
  - Google Cloud SQL R2DBC PostgreSQL support was added via cloud-sql-connector-r2dbc-postgres 1.28.3, with
    docs and tests for r2dbc:gcp:postgres and pooled r2dbc:pool:gcp:postgres URLs.
  - R2DBC option keys now normalize kebab-case to camelCase before building ConnectionFactoryOptions.
  - r2dbc-pool is now included at runtime by r2dbc-core, fixing startup when apps do not declare the pool
    dependency explicitly.
  - Oracle R2DBC health checks were fixed to avoid dropped late publisher errors.
  - RxJava test/catalog usage moved from RxJava2 to RxJava3.
  - Docs clarify PostgreSQL native-image driver requirements and Docker/container host/port configuration.

  Diff size: 97 files changed, 4173 insertions, 281 deletions. I did not run tests; this was a folder
  comparison only.

# Release Note Comparison

Generated: 2026-05-19 10:05 UTC
Comparison: `6.2.x` -> `7.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-r2dbc` | `6.2.x` | `71578387d03b` | `git@github.com:micronaut-projects/micronaut-r2dbc.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-r2dbc` | `7.0.x` | `410a32830ba9` | `git@github.com:micronaut-projects/micronaut-r2dbc.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-r2dbc`
- Commit candidates found: 153
- File changes listed: 97
- Version values listed: 57
- File status counts: A=33, M=64

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `6.2.1-SNAPSHOT` | `7.0.2-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.gradle-kotlin` | `org.jetbrains.kotlin:kotlin-gradle-plugin:1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.gradle-kotlin-allopen` | `org.jetbrains.kotlin:kotlin-allopen:1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.gradle-kotlin-noarg` | `org.jetbrains.kotlin:kotlin-noarg:1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.gradle-micronaut` | `io.micronaut.gradle:micronaut-gradle-plugin:4.6.0` | `io.micronaut.gradle:micronaut-gradle-plugin:4.6.2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-cloud-sql-connector-r2dbc-postgres` | `not present` | `com.google.cloud.sql:cloud-sql-connector-r2dbc-postgres:1.28.3` | `added` |
| `gradle/libs.versions.toml` | `libraries.managed-r2dbc-h2` | `io.r2dbc:r2dbc-h2:1.0.0.RELEASE` | `io.r2dbc:r2dbc-h2:1.1.0.RELEASE` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-r2dbc-mariadb` | `org.mariadb:r2dbc-mariadb:1.3.0` | `org.mariadb:r2dbc-mariadb:1.4.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-r2dbc-mssql` | `io.r2dbc:r2dbc-mssql:1.0.3.RELEASE` | `io.r2dbc:r2dbc-mssql:1.0.4.RELEASE` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-r2dbc-mysql` | `io.asyncer:r2dbc-mysql:1.4.1` | `io.asyncer:r2dbc-mysql:1.4.2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-r2dbc-oracle` | `com.oracle.database.r2dbc:oracle-r2dbc:1.3.0` | `com.oracle.database.r2dbc:oracle-r2dbc:1.3.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-r2dbc-pool` | `io.r2dbc:r2dbc-pool:1.0.2.RELEASE` | `io.r2dbc:r2dbc-pool:1.0.2.RELEASE` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-r2dbc-postgresql` | `org.postgresql:r2dbc-postgresql:1.1.0.RELEASE` | `org.postgresql:r2dbc-postgresql:1.1.1.RELEASE` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-r2dbc-spi` | `io.r2dbc:r2dbc-spi:1.0.0.RELEASE` | `io.r2dbc:r2dbc-spi:1.0.0.RELEASE` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.micronaut-data` | `io.micronaut.data:micronaut-data-bom:4.13.8` | `io.micronaut.data:micronaut-data-bom:5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-flyway` | `io.micronaut.flyway:micronaut-flyway-bom:7.8.0` | `io.micronaut.flyway:micronaut-flyway-bom:8.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-kotlin` | `micronaut-kotlin:4.7.0` | `micronaut-kotlin:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-logging` | `io.micronaut.logging:micronaut-logging-bom:1.7.1` | `io.micronaut.logging:micronaut-logging-bom:2.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-micrometer` | `not present` | `io.micronaut.micrometer:micronaut-micrometer-core:6.0.0` | `added` |
| `gradle/libs.versions.toml` | `libraries.micronaut-reactor` | `micronaut-reactor:3.9.1` | `micronaut-reactor:4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-rxjava2` | `micronaut-rxjava2:2.9.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-rxjava3` | `not present` | `micronaut-rxjava3:4.0.0` | `added` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.15.5` | `io.micronaut.serde:micronaut-serde-bom:3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-sql` | `io.micronaut.sql:micronaut-sql-bom:6.3.1` | `io.micronaut.sql:micronaut-sql-bom:7.0.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-resources` | `io.micronaut.testresources:micronaut-test-resources-bom:2.10.1` | `io.micronaut.testresources:micronaut-test-resources-bom:4.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-testresources-client` | `micronaut-testresources-client:2.10.1` | `micronaut-testresources-client:4.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-validation` | `io.micronaut.validation:micronaut-validation-bom:4.12.0` | `io.micronaut.validation:micronaut-validation-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.18` | `5.0.3` | `changed` |
| `gradle/libs.versions.toml` | `versions.kotlin-gradle-plugin` | `1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.managed-cloud-sql-connector` | `not present` | `1.28.3` | `added` |
| `gradle/libs.versions.toml` | `versions.managed-r2dbc` | `1.0.0.RELEASE` | `1.0.0.RELEASE` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-r2dbc-h2` | `1.0.0.RELEASE` | `1.1.0.RELEASE` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-r2dbc-mariadb` | `1.3.0` | `1.4.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-r2dbc-mssql` | `1.0.3.RELEASE` | `1.0.4.RELEASE` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-r2dbc-mysql` | `1.4.1` | `1.4.2` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-r2dbc-oracle` | `1.3.0` | `1.3.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-r2dbc-pool` | `1.0.2.RELEASE` | `1.0.2.RELEASE` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-r2dbc-postgresql` | `1.1.0.RELEASE` | `1.1.1.RELEASE` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.6` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-data` | `4.13.8` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `3.0.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.micronaut-flyway` | `7.8.0` | `8.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.6.0` | `4.6.2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-kotlin` | `4.7.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.1` | `2.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-micrometer` | `not present` | `6.0.0` | `added` |
| `gradle/libs.versions.toml` | `versions.micronaut-platform` | `4.9.4` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-reactor` | `3.9.1` | `4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-rxjava2` | `2.9.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-rxjava3` | `not present` | `4.0.0` | `added` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.15.5` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-sql` | `6.3.1` | `7.0.1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.7.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test-resources` | `2.10.1` | `4.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.12.0` | `5.0.0` | `changed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `f751b09cb41b` Remove SharedArenaSupport flag since it is done in gradle plugin. (radovanradic, 2026-05-12)
- `e8451a9b90eb` Fix Oracle R2DBC health check dropped errors (#909) (Graeme Rocher, 2026-04-16)

### Features

- `70a5a4051926` Add Kotlin native repository regression test (#912) (Graeme Rocher, 2026-04-17)

### Fixes

- `e5d6795bb8bf` fix(deps): update kotlin monorepo to v2.3.21 (#929) (renovate[bot], 2026-04-24)
- `08dbcb7164d9` fix(deps): update micronaut dependencies (#927) (renovate[bot], 2026-04-22)
- `0a4b4ea8d365` fix(deps): update dependency org.graalvm.sdk:graal-sdk to v25.0.3 (#926) (renovate[bot], 2026-04-22)
- `c2a2f7d4e104` fix(deps): update dependency com.google.cloud.sql:cloud-sql-connector-r2dbc-postgres to v1.28.3 (#922) (renovate[bot], 2026-04-22)
- `cf12f3a544c1` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v5.0.0-m6 (#925) (renovate[bot], 2026-04-22)
- `0fd81ed29fc3` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to v7.0.1-m2 (#923) (renovate[bot], 2026-04-21)
- `eaa97c282a88` fix(deps): update dependency io.micronaut.reactor:micronaut-reactor-bom to v4.0.0-m2 (#906) (renovate[bot], 2026-04-15)
- `c43b515ed842` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m6 (#903) (renovate[bot], 2026-04-15)
- `ec4b7221633d` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m22 (#905) (renovate[bot], 2026-04-15)
- `3f820ff7d02a` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m5 (#902) (renovate[bot], 2026-04-01)
- `cd6464f72cc8` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m4 (#901) (renovate[bot], 2026-03-27)
- `710884610a37` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m18 (#900) (renovate[bot], 2026-03-26)
- `97117fdab43d` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m3 (#898) (renovate[bot], 2026-03-25)
- `c5cde227ff19` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v5.0.0-m5 (#896) (renovate[bot], 2026-03-24)
- `9b23e0b10d70` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to v7.0.1-M1 (#895) (renovate[bot], 2026-03-23)
- `1c809c74f613` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v5.0.0-m4 (#893) (renovate[bot], 2026-03-20)
- `55dec2409182` fix(deps): update kotlin monorepo to v2.3.20 (#891) (renovate[bot], 2026-03-17)
- `6a419a996044` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m17 (#889) (renovate[bot], 2026-03-16)
- `e008b7d5a830` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v5.0.0-m3 (#887) (renovate[bot], 2026-03-12)
- `08f82b1da180` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m16 (#886) (renovate[bot], 2026-03-09)
- `8d575961df32` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m15 (#883) (renovate[bot], 2026-03-03)
- `73327de3e874` fix(deps): update micronaut.test.resources to v4.0.0-M1 (#880) (renovate[bot], 2026-02-26)
- `1ebd62240170` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m14 (#879) (renovate[bot], 2026-02-26)
- `c2526c450766` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m13 (#877) (renovate[bot], 2026-02-23)
- `9b1699f311c7` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to v7.0.0-M7 (#875) (renovate[bot], 2026-02-19)
- `47d105ebc870` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v5.0.0-m2 (#876) (renovate[bot], 2026-02-19)
- `1ca00a8d6d1e` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m12 (#874) (renovate[bot], 2026-02-19)
- `862b335161f7` fix(deps): update dependency org.mariadb:r2dbc-mariadb to v1.4.0 (#873) (renovate[bot], 2026-02-18)
- `4dc905f3e430` fix(deps): update dependency io.micronaut.logging:micronaut-logging-bom to v2.0.0-m2 (#872) (renovate[bot], 2026-02-18)
- `933b8fa70be7` fix(deps): update micronaut.test.resources to v3.0.0-m6 (#869) (renovate[bot], 2026-02-18)
- `05aba65cc9c6` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m11 (#871) (renovate[bot], 2026-02-18)
- `fc425910293d` fix(deps): update kotlin monorepo to v2.3.10 (#867) (renovate[bot], 2026-02-05)
- `a62529b1272b` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m10 (#866) (renovate[bot], 2026-02-05)
- `465501864763` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.2 (#864) (renovate[bot], 2026-02-04)
- `51c7f36a7e32` fix(deps): update micronaut.test.resources to v3.0.0-m5 (#863) (renovate[bot], 2026-02-03)
- `f1c202401a8f` fix(deps): update kotlin monorepo to v2.3.0 (#852) (renovate[bot], 2026-01-27)
- `7e668943168d` fix(deps): update dependency io.micronaut.flyway:micronaut-flyway-bom to v8.0.0-m2 (#857) (renovate[bot], 2026-01-27)
- `37d588852270` fix(deps): update micronaut.test.resources to v3.0.0-m4 (#858) (renovate[bot], 2026-01-27)
- `d4e6e838ff8b` fix(deps): update dependency org.graalvm.sdk:graal-sdk to v25.0.2 (#856) (renovate[bot], 2026-01-27)
- `be0e601a78c1` fix(deps): update dependency io.r2dbc:r2dbc-mssql to v1.0.4.release (#855) (renovate[bot], 2026-01-27)
- `800acd012274` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m9 (#843) (renovate[bot], 2026-01-27)
- `4f17cd74f2ab` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to 7.0.0-M4 (#837) (renovate[bot], 2025-11-21)
- `24680c1bdbd4` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#836) (renovate[bot], 2025-11-12)
- `8b76c9040f0a` fix(deps): update dependency org.graalvm.sdk:graal-sdk to v25 (#834) (renovate[bot], 2025-11-10)
- `bd04375036b3` fix(deps): update dependency org.postgresql:r2dbc-postgresql to v1.1.1.release (#824) (renovate[bot], 2025-11-10)
- `c3f33b92bc65` fix(deps): update dependency io.r2dbc:r2dbc-h2 to v1.1.0.release (#820) (renovate[bot], 2025-11-10)
- `742acebc1893` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.1 (#822) (renovate[bot], 2025-11-10)
- `44fb0730138c` fix(deps): update kotlin monorepo to v2.2.21 (#825) (renovate[bot], 2025-11-10)
- `74f40a639ab4` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to v6.3.2 (#823) (renovate[bot], 2025-11-10)
- `cf96278ee70d` fix(deps): update dependency io.micronaut.flyway:micronaut-flyway-bom to v7.9.2 (#826) (renovate[bot], 2025-11-10)
- `c70249f4ed72` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v4.14.1 (#828) (renovate[bot], 2025-11-10)
- `2290e9be5960` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.8 (#819) (renovate[bot], 2025-11-03)
- `0c8dd32a4ea3` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.1 (#813) (renovate[bot], 2025-10-21)
- `60585950e792` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.7 (#812) (renovate[bot], 2025-10-21)
- `6e94c07a6417` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v4.14.0 (#810) (renovate[bot], 2025-10-21)
- `0a8da940c911` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.6 (#807) (renovate[bot], 2025-10-17)
- `e55466f83322` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.0 (#797) (renovate[bot], 2025-10-17)

### Dependency Updates

- `410a32830ba9` chore: Bump version to 7.0.2-SNAPSHOT (micronaut-build, 2026-05-18)
- `880964bdc989` Update Micronaut dependencies (#959) (renovate[bot], 2026-05-18)
- `4610e3070c23` Update Micronaut dependencies (#957) (renovate[bot], 2026-05-15)
- `fc71b95bbf63` Update Micronaut dependencies (#956) (renovate[bot], 2026-05-14)
- `6d87c753a7aa` Update dependency io.micronaut:micronaut-core-bom to v5.0.0 (#955) (renovate[bot], 2026-05-13)
- `7929ea57f9da` Update dependency micronaut to v5.0.0-RC1 (#951) (renovate[bot], 2026-05-12)
- `2a6c2da66f8e` Update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-RC3 (#950) (renovate[bot], 2026-05-11)
- `186e86da7649` Update Micronaut dependencies (#949) (renovate[bot], 2026-05-10)
- `8520d7f9ec0a` Update Micronaut dependencies (#947) (renovate[bot], 2026-05-08)
- `99941d9697c3` chore: Bump version to 7.0.0-SNAPSHOT (micronaut-build, 2026-05-07)
- `31445908fd05` Update Micronaut dependencies (#944) (renovate[bot], 2026-05-07)
- `add42948a2c1` Update Micronaut dependencies (#942) (renovate[bot], 2026-05-05)
- `a4efa0676029` Update Micronaut dependencies (#939) (renovate[bot], 2026-05-04)
- `1333f9548bc2` Update dependency io.asyncer:r2dbc-mysql to v1.4.2 (#933) (renovate[bot], 2026-05-01)
- `b2f16e8081b8` Update Micronaut dependencies (#934) (renovate[bot], 2026-05-01)
- `0db20a35f510` chore: Bump version to 7.0.0-SNAPSHOT (micronaut-build, 2026-04-24)
- `07652c58e4dd` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m18 (#928) (renovate[bot], 2026-04-24)
- `a284afc9864e` build(deps): combine Renovate batch upgrades (#920) (Graeme Rocher, 2026-04-19)
- `f0b351708b78` chore: Bump version to 7.0.0-SNAPSHOT (micronaut-build, 2026-03-23)
- `0f00216bbeec` chore(deps): update gradle to v9.4.0 (#885) (renovate[bot], 2026-03-09)
- `e7fd25402c7d` chore(deps): update github artifact actions (#881) (renovate[bot], 2026-02-27)
- `d17eafd58a03` chore: Bump version to 7.0.0-SNAPSHOT (micronaut-build, 2026-02-19)
- `5e4d7c62f218` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#870) (renovate[bot], 2026-02-18)
- `6d03973823d4` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m16 (#868) (renovate[bot], 2026-02-10)
- `8d218bcaaacb` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m15 (#861) (renovate[bot], 2026-02-02)
- `0acebacb1c47` chore: Bump version to 7.0.0-SNAPSHOT (micronaut-build, 2026-01-27)
- `e156192f7402` chore(deps): update actions/checkout action to v6.0.2 (#840) (renovate[bot], 2026-01-27)
- `e58506da88eb` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m14 (#846) (renovate[bot], 2026-01-27)
- `97516ab73c93` chore: Bump version to 7.0.1-SNAPSHOT (micronaut-build, 2025-11-13)
- `831a2286d99b` chore(deps): update mikepenz/action-junit-report action to v6 (#833) (renovate[bot], 2025-11-10)
- `17cfa4e9f59d` chore(deps): update github artifact actions (#832) (renovate[bot], 2025-11-10)
- `edf3f61fa7a1` chore: Bump version to 7.0.0-SNAPSHOT (micronaut-build, 2025-11-10)
- `65c7c1431aad` chore(deps): update gradle to v9.2.0 (#831) (renovate[bot], 2025-11-10)
- `1f8300299764` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m9 (#821) (renovate[bot], 2025-11-10)
- `076bb6ad2059` chore(deps): update softprops/action-gh-release action to v2.4.2 (#829) (renovate[bot], 2025-11-10)
- `067139bebf30` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#817) (renovate[bot], 2025-11-03)
- `4a4c9f3539da` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m8 (#818) (renovate[bot], 2025-11-03)
- `f06f5046763b` Update dependencies for 4.10 (#805) (Radovan Radic, 2025-10-17)

### Documentation

- `4ff056f7c0bc` docs: clarify PostgreSQL native-image driver requirement (#911) (Graeme Rocher, 2026-04-17)

### Review Candidates

- `a6022072d77e` [skip ci] Release v7.0.1 (micronaut-build, 2026-05-18)
- `a6774da359f8` Update mikepenz/action-junit-report digest to 3a81627 (#958) (renovate[bot], 2026-05-18)
- `8b9d056670de` update versions (Sergio del Amo, 2026-05-18)
- `072b40b88539` Update Gradle to v9.5.1 (#953) (renovate[bot], 2026-05-13)
- `258b09acf3f7` Update plugin io.micronaut.build.shared.settings to v8.0.0-RC1 (#954) (renovate[bot], 2026-05-13)
- `b16f6870bae6` Merge pull request #952 from micronaut-projects/update-native-gradle-build (Álvaro Sánchez-Mariscal, 2026-05-12)
- `13d90d39efeb` Update common files (#948) (micronaut-build, 2026-05-09)
- `5f6b859651a0` Update common files (#946) (micronaut-build, 2026-05-08)
- `143c03343f50` [skip ci] Release v7.0.1-RC1 (micronaut-build, 2026-05-07)
- `0e2df2bfa2af` micronaut-micrometer = "6.0.0-M2" (Sergio del Amo, 2026-05-07)
- `e7a320c7a002` micronaut-logging = "2.0.0-RC1" (Sergio del Amo, 2026-05-07)
- `c54f9f9a4809` Update common files (#945) (micronaut-build, 2026-05-07)
- `81854fbe965e` Update common files (#943) (micronaut-build, 2026-05-06)
- `843ac88ff222` Update Gradle to v9.5.0 (#940) (renovate[bot], 2026-05-04)
- `5fc8c5da1e17` Update common files (#938) (micronaut-build, 2026-05-04)
- `4f11e5b1f38a` Update Gradle to v9.5.0 (#937) (renovate[bot], 2026-05-01)
- `737fa6790a0b` Update common files (#936) (micronaut-build, 2026-04-30)
- `07c2acdf1701` Update common files (#935) (micronaut-build, 2026-04-29)
- `06728e4138ed` use micronaut kotlin plugin (#931) (Issam Liqali, 2026-04-29)
- `56ce3870b9f6` Migrate RxJava2 to RxJava3 (#932) (Issam Liqali, 2026-04-29)
- `2d404ea3c771` Clarify Docker R2DBC host configuration (#930) (Graeme Rocher, 2026-04-24)
- `6849b00232e4` Fix ConnectionPool CNFE when r2dbc-pool is undeclared (#907) (Graeme Rocher, 2026-04-24)
- `68f992676651` [skip ci] Release v7.0.1-M2 (micronaut-build, 2026-04-24)
- `1235f3bf7e4d` Update common files (#924) (micronaut-build, 2026-04-22)
- `02a10629135f` Clarify Cloud SQL R2DBC configuration for Cloud Run (#908) (Graeme Rocher, 2026-04-21)
- `b6e72220379f` Update common files (#914) (micronaut-build, 2026-04-20)
- `0d24ae2456d0` Normalize kebab-case R2DBC options (#910) (Graeme Rocher, 2026-04-16)
- `0e0b4c5a32ce` Update common files (#904) (micronaut-build, 2026-04-15)
- `d33f62d3c356` Update common files (#899) (micronaut-build, 2026-03-25)
- `1a70e945aeb0` [skip ci] Release v7.0.1-M1 (micronaut-build, 2026-03-23)
- `3c79c09ad664` Update common files (#894) (micronaut-build, 2026-03-23)
- `0be1c50153ef` Update common files (#884) (micronaut-build, 2026-03-18)
- `c51274510ff7` Update common files (#882) (micronaut-build, 2026-03-03)
- `e1208e16a925` [skip ci] Release v7.0.0-M3 (micronaut-build, 2026-02-19)
- `6f524253efe9` Update common files (#865) (micronaut-build, 2026-02-05)
- `e527c9c28725` Update common files (#862) (micronaut-build, 2026-02-02)
- `1ca26d950bbc` Update common files (#860) (micronaut-build, 2026-01-30)
- `0d4eb4845fc6` [skip ci] Release v7.0.0-M2 (micronaut-build, 2026-01-27)
- `8d402be5589a` Update common files (#841) (micronaut-build, 2026-01-27)
- `8b2bb33bc150` [WIP] Replace Micronaut nullability annotations with JSpecify (#848) (Copilot, 2025-12-02)
- `03a69b81d49f` [skip ci] Release v7.0.0 (micronaut-build, 2025-11-13)
- `b5e2d4cb9c66` Update common files (#835) (micronaut-build, 2025-11-13)
- `73526a2ae42f` [skip ci] Release v7.0.0-M1 (micronaut-build, 2025-11-10)
- `ae4c88ae6c3a` Update common files (#827) (micronaut-build, 2025-11-10)
- `a8742ba1e902` update micronaut build and java baseline (#816) (issam liqali, 2025-11-03)
- `2fc93486ed7e` Update common files (#815) (micronaut-build, 2025-11-03)
- `cbedf01419a4` Update common files (#814) (micronaut-build, 2025-10-21)
- `b58841dcae2c` [r2dbc] Update common files for branch 7.0.x (#811) (micronaut-build, 2025-10-20)
- `fd0eb50a6f60` Release prep (#808) (issam liqali, 2025-10-17)
- `521ecca4402d` micronaut platform 4.9.4 (Sergio del Amo, 2025-10-15)
- `3ff69a327b04` Update common files (#804) (micronaut-build, 2025-10-17)
- `49847de6eedb` Micronaut build gradle plugin 8.0.0-M4 (Sergio del Amo, 2025-10-15)
- `976f7d642e4e` gradle 9.1 (Sergio del Amo, 2025-10-15)
- `c8278c258464` projectVersion=7.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-10-15)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` buildSrc/build.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.r2dbc-example.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.r2dbc-kotlin-example.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.r2dbc-kotlin.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.r2dbc-testproject-library.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.r2dbc-testproject.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` r2dbc-core/build.gradle
- `A` r2dbc-core/src/test/groovy/io/micronaut/r2dbc/config/R2dbcPoolOptionalDependencySpec.groovy
- `M` settings.gradle
- `M` test-graalvm/common-tests/build.gradle
- `M` test-graalvm/common/build.gradle
- `M` test-graalvm/h2/build.gradle.kts
- `M` test-graalvm/mysql/build.gradle

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
- `M` doc-examples/example-groovy/build.gradle.kts
- `M` doc-examples/example-groovy/src/main/groovy/example/AuthorRepository.groovy
- `M` doc-examples/example-groovy/src/main/groovy/example/BookRepository.groovy
- `M` doc-examples/example-java/build.gradle
- `M` doc-examples/example-java/src/main/java/example/AuthorRepository.java
- `M` doc-examples/example-java/src/main/java/example/BookRepository.java
- `M` doc-examples/example-kotlin/build.gradle
- `M` doc-examples/example-kotlin/src/main/kotlin/example/BookRepository.kt
- `M` src/main/docs/guide/availableDrivers.adoc
- `M` src/main/docs/guide/quickStart.adoc

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
- `M` r2dbc-core/src/main/java/io/micronaut/r2dbc/BasicR2dbcProperties.java
- `M` r2dbc-core/src/main/java/io/micronaut/r2dbc/DefaultBasicR2dbcProperties.java
- `M` r2dbc-core/src/main/java/io/micronaut/r2dbc/health/R2dbcHealthIndicator.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `A` r2dbc-core/src/test/groovy/io/micronaut/r2dbc/DefaultBasicR2dbcPropertiesSpec.groovy
- `M` r2dbc-core/src/test/groovy/io/micronaut/r2dbc/h2/H2ConnectionFactoryConfigurationSpec.groovy
- `M` r2dbc-core/src/test/groovy/io/micronaut/r2dbc/h2/H2ConnectionSpec.groovy
- `A` r2dbc-core/src/test/groovy/io/micronaut/r2dbc/health/R2dbcHealthIndicatorSpec.groovy
- `M` r2dbc-core/src/test/groovy/io/micronaut/r2dbc/mariadb/MariadbConnectionSpec.groovy
- `M` r2dbc-core/src/test/groovy/io/micronaut/r2dbc/mariadb/MariadbHealthIndicatorSpec.groovy
- `M` r2dbc-core/src/test/groovy/io/micronaut/r2dbc/mariadb/MariadbMultipleHealthIndicatorSpec.groovy
- `M` r2dbc-core/src/test/groovy/io/micronaut/r2dbc/mssql/MssqlConnectionSpec.groovy
- `M` r2dbc-core/src/test/groovy/io/micronaut/r2dbc/mssql/MssqlHealthIndicatorSpec.groovy
- `M` r2dbc-core/src/test/groovy/io/micronaut/r2dbc/mysql/MySqlConnectionSpec.groovy
- `M` r2dbc-core/src/test/groovy/io/micronaut/r2dbc/mysql/MySqlHealthIndicatorSpec.groovy
- `M` r2dbc-core/src/test/groovy/io/micronaut/r2dbc/oracle/OracleConnectionSpec.groovy
- `M` r2dbc-core/src/test/groovy/io/micronaut/r2dbc/oracle/OracleDatabaseContainerProvider.java
- `M` r2dbc-core/src/test/groovy/io/micronaut/r2dbc/oracle/OracleHealthIndicatorSpec.groovy
- `M` r2dbc-core/src/test/groovy/io/micronaut/r2dbc/oracle/OracleR2DBCDatabaseContainer.java
- `M` r2dbc-core/src/test/groovy/io/micronaut/r2dbc/oracle/OracleTestPropertyProvider.groovy
- `A` r2dbc-core/src/test/groovy/io/micronaut/r2dbc/postgresql/GcpPostgresConnectionFactoryConfigurationSpec.groovy
- `A` r2dbc-core/src/test/groovy/io/micronaut/r2dbc/postgresql/PostgresConnectionFactoryConfigurationSpec.groovy
- `M` r2dbc-core/src/test/groovy/io/micronaut/r2dbc/postgresql/PostgresConnectionSpec.groovy
- `M` r2dbc-core/src/test/groovy/io/micronaut/r2dbc/postgresql/PostgresHealthIndicatorSpec.groovy
- `M` test-graalvm/common-tests/src/main/java/example/controllers/TestApp.java
- `M` test-graalvm/common/src/main/java/testgraalvm/controllers/dto/OwnerDto.java
- `A` test-graalvm/common/src/main/resources/META-INF/native-image/io.micronaut.r2dbc/micronaut-r2dbc/test-graalvm/common/native-image.properties
- `A` test-graalvm/h2/src/test/kotlin/example/kotlin/KotlinOwnerRepository.kt
- `A` test-graalvm/h2/src/test/kotlin/example/kotlin/KotlinRepositoryNativeImageTest.kt

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

