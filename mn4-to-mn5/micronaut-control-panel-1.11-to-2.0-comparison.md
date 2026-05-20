Compared micronaut-control-panel as mn4 -> mn5.

  Scope

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-control-panel, branch 1.11.x, SHA ac555806cd09
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-control-panel, branch 2.0.x, SHA e588f7c16974
  - Same remote, both clean: git@github.com:micronaut-projects/micronaut-control-panel.git
  - Report: /private/tmp/micronaut-control-panel-1.11-to-2.0-comparison.md

  Key Findings

  - Version line moves 1.10.1-SNAPSHOT -> 2.0.1-SNAPSHOT.
  - Baseline updates include Micronaut 4.10.4 -> 5.0.0, Micronaut Platform 4.9.4 -> 5.0.0-RC1, Gradle
    8.14.3 -> 9.5.1, Kotlin Gradle plugin 1.9.25 -> 2.3.21, and Java SDKMAN pin 25.0.1-graal.
  - New modules/panels were added for Cache, Datasource, Hibernate, and Kafka Streams.
  - Management panels expanded with Application Info, Metrics, Disabled Beans, and logger writes routed
    through control-panel-owned helper routes.
  - Control Panel security is now first-class: when Micronaut Security is active, access defaults to
    AUTHORIZED with ROLE_CONTROL_PANEL; write operations have separate micronaut.control-
    panel.security.write-access and optional write-role support.
  - Refresh, stop, logger changes, cache invalidation, datasource SQL, Hibernate operations, and object-
    storage writes are now governed by control panel write-access rules instead of requiring raw management
    endpoints to be non-sensitive.
  - UI was rewritten from AdminLTE-style assets to a shadcn/ui-inspired server-rendered dashboard with
    local CSS/JS, light/dark theme support, sidebar state, category badges, and new screenshots.
  - Core panel infrastructure now supports dynamic panels through ControlPanelLoader and per-bean panels
    through AbstractEachBeanControlPanel; the old DefaultControlPanelRepository(List<ControlPanel>)
    constructor is deprecated and throws if used.
  - handlebars-humanize was removed; the used helpers are now implemented locally.
  - Routes panel gained OpenAPI viewer detection and merged GET/HEAD route display.

  Diff size: 361 files changed, 33145 insertions(+), 2521 deletions(-).

  I did not run tests; this was a folder comparison and targeted source/build-diff review only.


# Release Note Comparison

Generated: 2026-05-19 15:37 UTC
Comparison: `1.11.x` -> `2.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-control-panel` | `1.11.x` | `ac555806cd09` | `git@github.com:micronaut-projects/micronaut-control-panel.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-control-panel` | `2.0.x` | `e588f7c16974` | `git@github.com:micronaut-projects/micronaut-control-panel.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-control-panel`
- Commit candidates found: 186
- File changes listed: 361
- Version values listed: 54
- File status counts: A=251, D=16, M=93, R=1

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `1.10.1-SNAPSHOT` | `2.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.avro` | `not present` | `org.apache.avro:avro:1.12.1` | `added` |
| `gradle/libs.versions.toml` | `libraries.avro-serde` | `not present` | `io.confluent:kafka-streams-avro-serde:8.2.0` | `added` |
| `gradle/libs.versions.toml` | `libraries.groovy` | `org.apache.groovy:groovy-bom (version.ref=groovy)` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-cache` | `not present` | `io.micronaut.cache:micronaut-cache-bom:6.0.0` | `added` |
| `gradle/libs.versions.toml` | `libraries.micronaut-data` | `not present` | `io.micronaut.data:micronaut-data-bom:5.0.0` | `added` |
| `gradle/libs.versions.toml` | `libraries.micronaut-kafka` | `not present` | `io.micronaut.kafka:micronaut-kafka-bom:6.0.0` | `added` |
| `gradle/libs.versions.toml` | `libraries.micronaut-logging` | `io.micronaut.logging:micronaut-logging-bom:1.7.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-micrometer` | `not present` | `io.micronaut.micrometer:micronaut-micrometer-bom:6.0.0` | `added` |
| `gradle/libs.versions.toml` | `libraries.micronaut-object-storage` | `io.micronaut.objectstorage:micronaut-object-storage-bom:2.9.0` | `io.micronaut.objectstorage:micronaut-object-storage-bom:3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-openapi` | `not present` | `io.micronaut.openapi:micronaut-openapi-bom:7.0.0` | `added` |
| `gradle/libs.versions.toml` | `libraries.micronaut-platform` | `io.micronaut.platform:micronaut-platform:4.9.4` | `io.micronaut.platform:micronaut-platform:5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.15.5` | `io.micronaut.serde:micronaut-serde-bom:3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-shared-settings` | `io.micronaut.build.shared.settings:io.micronaut.build.shared.settings.gradle.plugin:7.6.4` | `io.micronaut.build.shared.settings:io.micronaut.build.shared.settings.gradle.plugin:8.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-sql` | `not present` | `io.micronaut.sql:micronaut-sql-bom:7.0.1` | `added` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test` | `io.micronaut.test:micronaut-test-bom:4.9.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-testresources` | `not present` | `micronaut-testresources:4.0.0` | `added` |
| `gradle/libs.versions.toml` | `libraries.node-gradle-plugin` | `not present` | `com.github.node-gradle:gradle-node-plugin:7.1.0` | `added` |
| `gradle/libs.versions.toml` | `libraries.playwright` | `com.microsoft.playwright:playwright:1.55.0` | `com.microsoft.playwright:playwright:1.59.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.shadow-plugin` | `com.gradleup.shadow:com.gradleup.shadow.gradle.plugin:9.2.2` | `com.gradleup.shadow:com.gradleup.shadow.gradle.plugin:9.3.2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.sonatype-scan` | `org.sonatype.gradle.plugins:scan-gradle-plugin:3.1.4` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.spock` | `org.spockframework:spock-bom (version.ref=spock)` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.test-logger-plugin` | `com.adarshr.test-logger:com.adarshr.test-logger.gradle.plugin:4.0.0` | `com.adarshr.test-logger:com.adarshr.test-logger.gradle.plugin:4.0.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.avro` | `not present` | `1.12.1` | `added` |
| `gradle/libs.versions.toml` | `versions.avro-serde` | `not present` | `8.2.0` | `added` |
| `gradle/libs.versions.toml` | `versions.gradle-node-plugin` | `not present` | `7.1.0` | `added` |
| `gradle/libs.versions.toml` | `versions.handlebars-humanize` | `not present` | `4.3.1` | `added` |
| `gradle/libs.versions.toml` | `versions.kotlin-gradle-plugin` | `1.9.25` | `2.3.21` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.4` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-cache` | `not present` | `6.0.0` | `added` |
| `gradle/libs.versions.toml` | `versions.micronaut-data` | `not present` | `5.0.0` | `added` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.5.5` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-kafka` | `not present` | `6.0.0` | `added` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-micrometer` | `not present` | `6.0.0` | `added` |
| `gradle/libs.versions.toml` | `versions.micronaut-object-storage` | `2.9.0` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-openapi` | `not present` | `7.0.0` | `added` |
| `gradle/libs.versions.toml` | `versions.micronaut-platform` | `4.9.4` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-reactor` | `not present` | `4.0.0` | `added` |
| `gradle/libs.versions.toml` | `versions.micronaut-security` | `not present` | `5.0.0` | `added` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.15.5` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-shared-settings` | `7.6.4` | `8.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-sql` | `not present` | `7.0.1` | `added` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.9.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-testresources` | `not present` | `4.0.0` | `added` |
| `gradle/libs.versions.toml` | `versions.micronaut-views` | `not present` | `6.0.0` | `added` |
| `gradle/libs.versions.toml` | `versions.playwright` | `1.55.0` | `1.59.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.shadow-plugin` | `9.2.2` | `9.3.2` | `changed` |
| `gradle/libs.versions.toml` | `versions.sonatype-scan` | `3.1.4` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.test-logger-plugin` | `4.0.0` | `4.0.0` | `unchanged` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |
| `settings.gradle.kts` | `plugin.io.micronaut.build.shared.settings` | `7.6.4` | `8.0.0` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `6754d8b2e189` Remove handlebars-humanize and inline used helpers (#490) (Álvaro Sánchez-Mariscal, 2026-03-11)
- `20c913d37386` build: remove sonatype plugin config (Sergio del Amo, 2026-02-20)

### Features

- `0d76b1f43e17` Add read/write control panel permissions (#580) (Álvaro Sánchez-Mariscal, 2026-05-13)
- `f47b6f2db75b` Add application info control panel (#544) (Álvaro Sánchez-Mariscal, 2026-05-12)
- `39b723851d6f` Add Metrics control panel (#543) (Álvaro Sánchez-Mariscal, 2026-05-11)
- `3e16f90a4ada` Add authenticated control panel access support (#526) (Álvaro Sánchez-Mariscal, 2026-05-05)
- `f48c9fefe7e4` Add native-image reflection config for BeanInfo.getBeanType() (#501) (Copilot, 2026-03-20)
- `ab9756812245` feat(kafka): Introduce a Kafka Streams panel (#459) (Álvaro Sánchez-Mariscal, 2026-02-02)
- `177abd2960bd` Add an OpenAPI viewer link if there is one (#452) (Álvaro Sánchez-Mariscal, 2026-01-16)
- `13f93b647fe7` feat(java25): adopt GA Java 21–25 features and safe modernizations (#447) (Álvaro Sánchez-Mariscal, 2026-01-15)
- `89617868b7a6` Introduce a new Data Source control panel (#439) (Álvaro Sánchez-Mariscal, 2026-01-13)
- `e18548da8d22` Introduce a new Disabled Beans control panel (#420) (Álvaro Sánchez-Mariscal, 2025-12-15)
- `a8beb961964b` Introduce a new Cache Control Panel module (#411) (Álvaro Sánchez-Mariscal, 2025-12-05)

### Fixes

- `5dcc00dee298` fix: prefer project modules in control panel builds (#547) (Álvaro Sánchez-Mariscal, 2026-05-11)
- `69a9c8a99056` Correct layout (Denis Stepanov, 2026-05-04)
- `07f4a5391aaa` Correct layout (Denis Stepanov, 2026-05-04)
- `6d87c61b9172` Correct layout (Denis Stepanov, 2026-05-04)
- `789a81d405a5` Correct layout (Denis Stepanov, 2026-05-04)
- `1950d73d3a94` fix(deps): update dependency org.jetbrains.kotlin:kotlin-gradle-plugin to v2.3.21 (#520) (renovate[bot], 2026-04-29)
- `c74b773c56d3` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m6 (#507) (renovate[bot], 2026-04-15)
- `a86c0bcfa952` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m18 (#506) (renovate[bot], 2026-03-26)
- `0a7348c5babc` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m3 (#505) (renovate[bot], 2026-03-25)
- `d0835cf3ebff` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v5.0.0-m5 (#504) (renovate[bot], 2026-03-24)
- `34aabaab6496` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v5.0.0-m4 (#499) (renovate[bot], 2026-03-20)
- `cc117e5ffc00` fix(deps): update dependency org.jetbrains.kotlin:kotlin-gradle-plugin to v2.3.20 (#497) (renovate[bot], 2026-03-18)
- `69a724b465e4` fix(deps): update dependency io.micronaut.platform:micronaut-platform to v4.10.10 (#496) (renovate[bot], 2026-03-17)
- `0eff35794465` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m17 (#495) (renovate[bot], 2026-03-16)
- `1c7ca37100b5` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v5.0.0-m3 (#492) (renovate[bot], 2026-03-13)
- `c7e905c3b2dd` fix(deps): update dependency com.gradleup.shadow:com.gradleup.shadow.gradle.plugin to v9.3.2 (#484) (renovate[bot], 2026-03-11)
- `deba6f6934fc` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m16 (#486) (renovate[bot], 2026-03-11)
- `0b6bf0eefbcf` fix(deps): update dependency io.micronaut.openapi:micronaut-openapi-bom to v6.20.0 (#488) (renovate[bot], 2026-03-11)
- `552b8eec54d7` fix(deps): update dependency io.micronaut.platform:micronaut-platform to v4.10.9 (#483) (renovate[bot], 2026-03-11)
- `a63703ff6065` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m14 (#481) (renovate[bot], 2026-02-27)
- `f00e80a779df` fix(deps): update dependency org.jetbrains.kotlin:kotlin-gradle-plugin to v2.3.10 (#478) (renovate[bot], 2026-02-23)
- `d0ef716a9194` fix(deps): update dependency com.microsoft.playwright:playwright to v1.58.0 (#463) (renovate[bot], 2026-02-20)
- `44269f8cf45f` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m13 (#468) (renovate[bot], 2026-02-20)
- `a96893157abc` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v5.0.0-m2 (#477) (renovate[bot], 2026-02-20)
- `5b49268ab3f4` fix(deps): update dependency io.micronaut.build.shared.settings:io.micronaut.build.shared.settings.gradle.plugin to v8.0.0-m17 (#476) (renovate[bot], 2026-02-17)
- `6d402be51a80` fix(deps): update dependency io.micronaut.testresources:micronaut-test-resources-bom to v3.0.0-m6 (#475) (renovate[bot], 2026-02-16)
- `55c2ac32947b` fix(deps): update dependency io.micronaut.platform:micronaut-platform to v4.10.8 (#473) (renovate[bot], 2026-02-14)
- `63f13452d0e6` fix(deps): update dependency io.micronaut.build.shared.settings:io.micronaut.build.shared.settings.gradle.plugin to v8.0.0-m16 (#472) (renovate[bot], 2026-02-11)
- `99329d51858d` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.2 (#470) (renovate[bot], 2026-02-09)
- `511a204d3aea` fix(deps): update dependency io.micronaut.cache:micronaut-cache-bom to v6.0.0-m2 (#469) (renovate[bot], 2026-02-08)
- `56968e746778` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v4.14.3 (#461) (renovate[bot], 2026-01-27)
- `de679880c41c` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to v7.0.0 (#454) (renovate[bot], 2026-01-18)
- `7237b440354f` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.14 (#453) (renovate[bot], 2026-01-17)
- `b312ba7da2b9` fix(deps): update dependency io.micronaut.platform:micronaut-platform to v4.10.7 (#442) (renovate[bot], 2026-01-12)
- `9232d55f5c5a` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.13 (#441) (renovate[bot], 2026-01-11)
- `0c3908edf648` fix(deps): update dependency com.gradleup.shadow:com.gradleup.shadow.gradle.plugin to v9.3.1 (#436) (renovate[bot], 2026-01-07)
- `339af4f805d9` fix(deps): update dependency io.micronaut.platform:micronaut-platform to v4.10.6 (#433) (renovate[bot], 2025-12-24)
- `2cedab820e86` fix(deps): update dependency io.micronaut.platform:micronaut-platform to v4.10.5 (#432) (renovate[bot], 2025-12-20)
- `b8c20fd7e477` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.12 (#431) (renovate[bot], 2025-12-18)
- `a30223cba1c7` fix(deps): update dependency io.micronaut.platform:micronaut-platform to v4.10.4 (#425) (renovate[bot], 2025-12-16)
- `7de24477211d` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.10 (#424) (renovate[bot], 2025-12-16)
- `3e92d457786f` fix(deps): update dependency org.jetbrains.kotlin:kotlin-gradle-plugin to v2.3.0 (#426) (renovate[bot], 2025-12-16)
- `9e4619510634` fix(deps): update dependency com.gradleup.shadow:com.gradleup.shadow.gradle.plugin to v9.3.0 (#414) (renovate[bot], 2025-12-10)
- `84f93264cad9` fix(deps): update dependency com.microsoft.playwright:playwright to v1.57.0 (#415) (renovate[bot], 2025-12-10)
- `e7c69bb3905f` fix(deps): update dependency org.jetbrains.kotlin:kotlin-gradle-plugin to v2.2.21 (#412) (renovate[bot], 2025-12-06)
- `ccaef56704b8` fix(deps): update dependency io.micronaut.platform:micronaut-platform to v4.10.3 (#407) (renovate[bot], 2025-12-05)
- `f4f9ac91b169` fix(deps): update dependency io.micronaut.platform:micronaut-platform to v4.10.2 (#399) (renovate[bot], 2025-11-27)
- `ecb21251c9f6` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#398) (renovate[bot], 2025-11-25)
- `6c02a1d053c0` fix(deps): update dependency com.microsoft.playwright:playwright to v1.56.0 (#397) (renovate[bot], 2025-11-24)
- `e2bcd921d27a` fix(deps): update dependency org.apache.groovy:groovy-bom to v4.0.29 (#395) (renovate[bot], 2025-11-21)
- `49667ccc43d3` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#394) (renovate[bot], 2025-11-20)
- `4d84e4609c61` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.1 (#393) (renovate[bot], 2025-11-12)
- `84e0e0465580` fix(deps): update dependency io.micronaut.build.shared.settings:io.micronaut.build.shared.settings.gradle.plugin to v7.6.6 (#392) (renovate[bot], 2025-11-11)
- `c5078c0f6a7b` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.8 (#391) (renovate[bot], 2025-11-10)
- `c91c65d19533` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.1 (#383) (renovate[bot], 2025-10-20)
- `65f4c8c57f76` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.0 (#381) (renovate[bot], 2025-10-20)
- `90a7c54fef4b` fix(deps): update dependency io.micronaut.objectstorage:micronaut-object-storage-bom to v2.10.0 (#382) (renovate[bot], 2025-10-20)
- `046c693abf95` fix(deps): update dependency io.micronaut.reactor:micronaut-reactor-bom to v3.9.1 (#379) (renovate[bot], 2025-10-20)

### Security

- `2dbc0c671383` micronaut-security = "5.0.0" (Sergio del Amo, 2026-05-18)
- `4032dac1b61e` Route loggers writes through control panel security (#540) (Álvaro Sánchez-Mariscal, 2026-05-11)
- `373ccea1b758` Enable authorized control panel access by default (#537) (Álvaro Sánchez-Mariscal, 2026-05-05)

### Dependency Updates

- `e588f7c16974` Update Micronaut dependencies (#558) (renovate[bot], 2026-05-19)
- `1193d4031fc9` chore: Bump version to 2.0.1-SNAPSHOT (micronaut-build, 2026-05-18)
- `3d57fbb976ca` chore: Bump version to 2.0.0-SNAPSHOT (micronaut-build, 2026-05-08)
- `362f98658fd1` Exclude unused native image test dependencies (#539) (Álvaro Sánchez-Mariscal, 2026-05-06)
- `cc88a5d96426` Update dependency com.microsoft.playwright:playwright to v1.59.0 (#532) (renovate[bot], 2026-05-05)
- `cbad21552419` Update Micronaut dependencies (#531) (renovate[bot], 2026-05-04)
- `874e84be0375` chore: Bump version to 2.0.0-SNAPSHOT (micronaut-build, 2026-04-30)
- `9febe2288a59` chore(deps): update softprops/action-gh-release action to v2.6.2 (#502) (renovate[bot], 2026-04-15)
- `296c454f5934` Upgrade Micronaut OpenAPI to 7.0.0-M1 and restore example OpenAPI wiring (#491) (Álvaro Sánchez-Mariscal, 2026-03-11)
- `3d5248837ea7` Update Micronaut dependencies to newer versions (#482) (Sergio del Amo, 2026-03-11)
- `00fd50ecd225` chore(deps): update actions/checkout action to v6 (#443) (renovate[bot], 2026-02-20)
- `0b92e364bb49` chore(deps): update stefanzweifel/git-auto-commit-action action to v7 (#429) (renovate[bot], 2026-02-20)
- `9b4dfbdbe59a` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#471) (renovate[bot], 2026-02-20)
- `7075eb9ec47d` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m15 (#464) (renovate[bot], 2026-02-02)
- `2cf5483d993f` chore(deps): update gradle to v9.3.1 (#456) (renovate[bot], 2026-01-30)
- `6fb91c8dac79` chore(deps): update dependency @rollup/plugin-node-resolve to v16 (#458) (renovate[bot], 2026-01-23)
- `d4ac4905a81b` chore(deps): update dependency @rollup/plugin-commonjs to v29 (#457) (renovate[bot], 2026-01-23)
- `75df5622a5ee` chore(deps): update dependency io.projectreactor.netty:reactor-netty-http to v1.3.2 (#444) (renovate[bot], 2026-01-14)
- `1e19dc435c1d` chore(deps): update graalvm/setup-graalvm action to v1.4.5 (#435) (renovate[bot], 2026-01-06)
- `7130566f1ddc` chore(deps): update dependency io.projectreactor.netty:reactor-netty-http to v1.3.1 (#417) (renovate[bot], 2025-12-12)
- `d400f30c8445` chore(deps): update graalvm/setup-graalvm action to v1.4.4 (#408) (renovate[bot], 2025-12-05)
- `db718192125a` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#404) (renovate[bot], 2025-12-01)
- `fe3fd278bb2b` chore(deps): update graalvm/setup-graalvm action to v1.4.3 (#402) (renovate[bot], 2025-11-28)
- `d3a152aa7970` chore(deps): update dependency io.projectreactor.netty:reactor-netty-http to v1.3.0 (#380) (renovate[bot], 2025-11-24)
- `925d515381ef` chore(deps): update softprops/action-gh-release action to v2.4.2 (#390) (renovate[bot], 2025-11-09)
- `221472bd4998` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m9 (#389) (renovate[bot], 2025-11-07)
- `35408c39be72` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m8 (#388) (renovate[bot], 2025-11-01)
- `433a565ff578` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#387) (renovate[bot], 2025-10-25)
- `7e8d67712945` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m5 (#386) (renovate[bot], 2025-10-22)

### Documentation

- `f1539b5234aa` docs: check contributing guidelines before PR handoff (#546) (Álvaro Sánchez-Mariscal, 2026-05-10)
- `07fe8ea2c049` docs: fix control panel guide details (#541) (Álvaro Sánchez-Mariscal, 2026-05-07)
- `e1679d7dc74e` docs: require screenshots for UI changes (#523) (Álvaro Sánchez-Mariscal, 2026-04-28)

### Review Candidates

- `611872c0e2ad` Fix control panel compilation with build plugin 8.0.0 (#588) (Álvaro Sánchez-Mariscal, 2026-05-19)
- `43d04316bd09` Update common files (#589) (micronaut-build, 2026-05-19)
- `f166c84f4861` [skip ci] Release v2.0.0 (micronaut-build, 2026-05-18)
- `919d427c639a` Revert "micronaut-shared-settings = "8.0.0"" (Sergio del Amo, 2026-05-18)
- `04cea65cdea3` git ignore buildSrc/.kotlin (Sergio del Amo, 2026-05-18)
- `0d805fa774d7` micronaut-shared-settings = "8.0.0" (Sergio del Amo, 2026-05-18)
- `1d80cd371572` micronaut-object-storage = "3.0.0" (Sergio del Amo, 2026-05-18)
- `91e9ef867e19` Fix Oracle UCP datasource inspector compile (#586) (Álvaro Sánchez-Mariscal, 2026-05-18)
- `f06eddea18c6` micronaut-sql = "7.0.1" (Sergio del Amo, 2026-05-18)
- `73c7aec17eb3` micronaut-kafka = "6.0.0" (Sergio del Amo, 2026-05-18)
- `188f87887d4b` micronaut-micrometer = "6.0.0" (Sergio del Amo, 2026-05-18)
- `fa368f7dff38` Update common files (#584) (micronaut-build, 2026-05-15)
- `c155f0a84413` Align platform BOM with 2.0.x RC (#585) (Álvaro Sánchez-Mariscal, 2026-05-15)
- `8ed1638e9e9d` micronaut-cache = "6.0.0" (Sergio del Amo, 2026-05-14)
- `51481f6b75c1` Update versions (Sergio del Amo, 2026-05-14)
- `cbfc428d7c37` micronaut-platform = "5.0.0-RC1" (Sergio del Amo, 2026-05-13)
- `efa675048733` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `83a8bf15fd32` Update common files (#583) (micronaut-build, 2026-05-13)
- `dcf752c45c0f` Update Gradle to v9.5.1 (#582) (renovate[bot], 2026-05-13)
- `3417386f02bc` Disable binary compatibility checks until 2.0.0 (#581) (Álvaro Sánchez-Mariscal, 2026-05-12)
- `f881a256c1f1` Improve datasource panel (#549) (Denis Stepanov, 2026-05-12)
- `e835eac254d9` Refine Kafka Streams runtime state UI (#551) (Álvaro Sánchez-Mariscal, 2026-05-12)
- `d601b36defd6` Show Kafka Streams runtime state (#548) (Álvaro Sánchez-Mariscal, 2026-05-11)
- `76c0f37d623d` Update common files (#545) (micronaut-build, 2026-05-11)
- `203efa235c76` [skip ci] Release v2.0.0-RC1 (micronaut-build, 2026-05-08)
- `88b0a2287955` udpate to latest versions (Sergio del Amo, 2026-05-08)
- `e4be14742e9e` [control-panel] Update common files for branch 2.0.x (#542) (micronaut-build, 2026-05-08)
- `1fe70598c301` Update common files (#538) (micronaut-build, 2026-05-07)
- `472fec3c83ad` Hibernate control panel (#534) (Denis Stepanov, 2026-05-06)
- `2db40c5133db` [control-panel] Update common files for branch 2.0.x (#535) (micronaut-build, 2026-05-05)
- `1d66cf6dfd04` Merge pull request #533 from micronaut-projects/shad (Denis Stepanov, 2026-05-04)
- `300be94b92de` Sonar (Denis Stepanov, 2026-05-04)
- `48876ad940e5` Correct (Denis Stepanov, 2026-05-04)
- `fe62bf9359ca` Correct (Denis Stepanov, 2026-05-04)
- `3f9bc5230df5` Improve styles (Denis Stepanov, 2026-05-04)
- `8925b4462e82` Fix tests (Denis Stepanov, 2026-05-04)
- `692324998aaf` Implement UI using shadcn (Denis Stepanov, 2026-05-04)
- `5e46a3eabbd5` [control-panel] Update common files for branch 2.0.x (#530) (micronaut-build, 2026-05-03)
- `2c6b198e9369` Merge pull request #525 from micronaut-projects/sync-files-2.0.x (Graeme Rocher, 2026-05-01)
- `21630c2aae84` Grant release asset upload permission (AI on behalf of Álvaro Sánchez-Mariscal, 2026-04-30)
- `8a9a7d9d7b93` [skip ci] Release v2.0.0-M2 (micronaut-build, 2026-04-30)
- `901189b0b13d` Align release artifact provenance subjects (#529) (Álvaro Sánchez-Mariscal, 2026-04-30)
- `fe3c25f37650` [skip ci] Release v2.0.0-M1 (micronaut-build, 2026-04-30)
- `aa70b65cf7bc` Include publication metadata in release artifact ZIP (#528) (Álvaro Sánchez-Mariscal, 2026-04-30)
- `418c358c5444` Fix Control Panel contributing guidance (#527) (Álvaro Sánchez-Mariscal, 2026-04-30)
- `a3663965a477` Update common files (micronaut-build, 2026-04-30)
- `be2bff8bdfc0` [control-panel] Update common files for branch 2.0.x (#524) (micronaut-build, 2026-04-29)
- `a65d9d5b27cd` Refresh agent guidance (#521) (Álvaro Sánchez-Mariscal, 2026-04-28)
- `0c94f1cb10c1` [control-panel] Update common files for branch 2.0.x (#513) (micronaut-build, 2026-04-24)
- `0572cc8c09af` Merge pull request #512 from micronaut-projects/sync-files-2.0.x (Álvaro Sánchez-Mariscal, 2026-04-16)
- `1e37c7659dd3` Update common files (micronaut-build, 2026-04-16)
- `aeb609d47f3d` Update common files (#493) (micronaut-build, 2026-04-15)
- `9280fef5843d` Fix GraalVM dev native reflection for control panel templates (#494) (Álvaro Sánchez-Mariscal, 2026-03-13)
- `27e318ca6d29` Update common files (#487) (micronaut-build, 2026-03-11)
- `0fad1c286d17` micronaut-views = "6.0.0-M1" (Sergio del Amo, 2026-02-20)
- `dbd868596b82` micronaut-sql = "7.0.0-M7" (Sergio del Amo, 2026-02-20)
- `79fbc32b7244` Update common files (#467) (micronaut-build, 2026-02-06)
- `8eb9bfbd57b7` Use new Infinispan and Hazelcast test resources modules (#466) (Álvaro Sánchez-Mariscal, 2026-02-02)
- `d9823f60ff20` Update common files (#465) (micronaut-build, 2026-02-02)
- `7524353ee34f` Update common files (#462) (micronaut-build, 2026-01-30)
- `3f83e2a29e51` Update common files (#460) (micronaut-build, 2026-01-23)
- `56d053965bca` Condense HTTP method display (#455) (Álvaro Sánchez-Mariscal, 2026-01-19)
- `85753905767c` Update common files (#446) (micronaut-build, 2026-01-15)
- `22de153321b1` Use JUnit for consistency (#445) (Álvaro Sánchez-Mariscal, 2026-01-15)
- `ae09c36b1a2b` Init AGENTS.md (Álvaro Sánchez-Mariscal, 2026-01-14)
- `d5ed20dbee22` [control-panel] Update common files for branch 2.0.x (#438) (micronaut-build, 2026-01-14)
- `00851b433d4e` Update common files (#434) (micronaut-build, 2026-01-08)
- `85b56c206ee3` Include a badge count for categories in the menu (#421) (Álvaro Sánchez-Mariscal, 2025-12-16)
- `4d48a769ad2b` Test Resources control panel (#419) (Álvaro Sánchez-Mariscal, 2025-12-12)
- `e08d6cf769da` Print Control Panel URL for easy access (#418) (Álvaro Sánchez-Mariscal, 2025-12-12)
- `af487c8f2ecf` Update common files (#413) (micronaut-build, 2025-12-10)
- `d815fcc7f957` Replace Micronaut nullability annotations with JSpecify nullability annotations (#406) (Copilot, 2025-12-01)
- `e654e8b68ac8` Update common files (#401) (micronaut-build, 2025-11-27)
- `dd022af8a407` Update common files (#400) (micronaut-build, 2025-11-26)
- `f455b84afc9d` Update common files (#385) (micronaut-build, 2025-11-24)
- `4dbafbede9de` Update common files (#384) (micronaut-build, 2025-10-20)
- `b42cebb5c109` Update common files (#377) (micronaut-build, 2025-10-17)
- `f592e700f0bb` micronaut build gradle plugin 8.0.0-M4 (Sergio del Amo, 2025-10-15)
- `b00eaab848c3` gradle 9.1 (Sergio del Amo, 2025-10-15)
- `b171875fb8b6` projectVersion=2.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-10-15)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` .github/workflows/update-gradle-wrapper.yml
- `M` buildSrc/build.gradle.kts
- `M` buildSrc/src/main/kotlin/io.micronaut.build.internal.control-panel-example.gradle.kts
- `M` buildSrc/src/main/kotlin/io.micronaut.build.internal.control-panel-module.gradle.kts
- `A` buildSrc/src/main/kotlin/io.micronaut.build.internal.control-panel-ui.gradle.kts
- `M` control-panel-bom/build.gradle.kts
- `A` control-panel-cache/build.gradle.kts
- `M` control-panel-core/build.gradle.kts
- `A` control-panel-datasource/build.gradle.kts
- `A` control-panel-hibernate/build.gradle.kts
- `A` control-panel-kafka/build.gradle.kts
- `M` control-panel-management/build.gradle.kts
- `M` control-panel-object-storage/build.gradle.kts
- `M` control-panel-ui/build.gradle.kts
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` settings.gradle.kts

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
- `M` README.md
- `A` control-panel-ui/src/main/javascript/README.md
- `A` doc-examples/example-java/AGENTS.md
- `M` doc-examples/example-java/build.gradle.kts
- `A` doc-examples/example-java/openapi.properties
- `A` doc-examples/example-java/src/main/avro/ecommerce/Intermediate.avsc
- `A` doc-examples/example-java/src/main/avro/ecommerce/ProductAttribute.avsc
- `A` doc-examples/example-java/src/main/avro/ecommerce/ProductDescription.avsc
- `A` doc-examples/example-java/src/main/avro/ecommerce/ProductFullContext.avsc
- `A` doc-examples/example-java/src/main/avro/ecommerce/ProductVariant.avsc
- `A` doc-examples/example-java/src/main/avro/ecommerce/ProductVariantDetail.avsc
- `A` doc-examples/example-java/src/main/avro/ecommerce/ProductVariantPrice.avsc
- `A` doc-examples/example-java/src/main/avro/ecommerce/ProductVariantStock.avsc
- `A` doc-examples/example-java/src/main/avro/ecommerce/README.md
- `M` doc-examples/example-java/src/main/java/example/Application.java
- `M` doc-examples/example-java/src/main/java/example/DemoController.java
- `A` doc-examples/example-java/src/main/java/example/DemoMetrics.java
- `A` doc-examples/example-java/src/main/java/example/HibernateAuthor.java
- `A` doc-examples/example-java/src/main/java/example/HibernateBook.java
- `A` doc-examples/example-java/src/main/java/example/HibernateDemoController.java
- `M` doc-examples/example-java/src/main/java/example/MyApplicationControlPanel.java
- `A` doc-examples/example-java/src/main/java/example/SampleDataLoader.java
- `A` doc-examples/example-java/src/main/java/example/kafka/AvroToJsonMapper.java
- `A` doc-examples/example-java/src/main/java/example/kafka/Consumer.java
- `A` doc-examples/example-java/src/main/java/example/kafka/FullContextJoiner.java
- `A` doc-examples/example-java/src/main/java/example/kafka/KafkaTopicsFactory.java
- `A` doc-examples/example-java/src/main/java/example/kafka/Producer.java
- `A` doc-examples/example-java/src/main/java/example/kafka/ProductDescriptionToAttributesJoiner.java
- `A` doc-examples/example-java/src/main/java/example/kafka/ProductVariantJoiner.java
- `A` doc-examples/example-java/src/main/java/example/kafka/StreamsTopologyFactory.java
- `M` doc-examples/example-java/src/main/resources/META-INF/native-image/com.microsoft.playwright/playwright/reflect-config.json
- `M` doc-examples/example-java/src/main/resources/META-INF/native-image/native-image.properties
- `A` doc-examples/example-java/src/main/resources/application-hazelcast.yml
- `A` doc-examples/example-java/src/main/resources/application-hibernate.yml
- `A` doc-examples/example-java/src/main/resources/application-infinispan.yml
- `A` doc-examples/example-java/src/main/resources/application-kafka.yml
- `A` doc-examples/example-java/src/main/resources/application-oracle.yml
- `A` doc-examples/example-java/src/main/resources/application-secured.yml
- `M` doc-examples/example-java/src/main/resources/application.yml
- `M` doc-examples/example-java/src/main/resources/logback.xml
- `A` doc-examples/example-java/src/main/resources/sql/my-oracle/create_1.sql
- `A` doc-examples/example-java/src/main/resources/sql/my-oracle/create_2.sql
- `A` doc-examples/example-java/src/main/resources/sql/my-oracle/data_1.sql
- `A` doc-examples/example-java/src/main/resources/sql/my-oracle/data_2.sql
- `A` doc-examples/example-java/src/main/resources/sql/my-postgres/create.sql
- `A` doc-examples/example-java/src/main/resources/sql/my-postgres/data.sql
- `M` doc-examples/example-java/src/main/resources/views/my-application/detail.hbs
- `A` doc-examples/example-java/src/test/java/example/ControlPanelRenderingTest.java
- `A` doc-examples/example-java/src/test/java/example/HibernateDemoControllerTest.java
- `M` doc-examples/example-java/src/test/java/example/MyApplicationControlPanelTest.java
- `M` doc-examples/example-java/src/test/java/example/e2e/AbstractE2ETest.java
- `A` doc-examples/example-java/src/test/java/example/e2e/ControlPanelBrowserOptions.java
- `A` doc-examples/example-java/src/test/java/example/e2e/ControlPanelBrowserOptionsTest.java
- `M` doc-examples/example-java/src/test/java/example/e2e/ControlPanelE2ETest.java
- `M` doc-examples/example-java/src/test/java/example/e2e/ControlPanelShutdownE2ETest.java
- `M` doc-examples/example-java/src/test/resources/logback-test.xml
- `M` src/main/docs/guide/controlPanels.adoc
- `M` src/main/docs/guide/controlPanels/builtIn.adoc
- `A` src/main/docs/guide/controlPanels/cache.adoc
- `A` src/main/docs/guide/controlPanels/datasource.adoc
- `A` src/main/docs/guide/controlPanels/hibernate.adoc
- `A` src/main/docs/guide/controlPanels/kafka.adoc
- `M` src/main/docs/guide/controlPanels/management.adoc
- `M` src/main/docs/guide/controlPanels/objectStorage.adoc
- `M` src/main/docs/guide/custom.adoc
- `M` src/main/docs/guide/introduction.adoc
- `M` src/main/docs/guide/quickStart.adoc
- `M` src/main/docs/guide/toc.yml
- `A` src/main/docs/resources/img/control-panel-dark.png
- `A` src/main/docs/resources/img/control-panel-light.png
- `D` src/main/docs/resources/img/control-panel.png
- `A` src/main/docs/resources/img/datasource-pool.png
- `A` src/main/docs/resources/img/datasource-query.png
- `A` src/main/docs/resources/img/datasource.png
- `A` src/main/docs/resources/img/hibernate-query-statistics.png
- `A` src/main/docs/resources/img/hibernate-session-details.png

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
- `A` AGENTS.md
- `M` CONTRIBUTING.md
- `M` MAINTAINING.md
- `M` config/checkstyle/checkstyle.xml
- `A` control-panel-cache/AGENTS.md
- `A` control-panel-cache/src/main/java/io/micronaut/controlpanel/panels/cache/AbstractCacheControlPanel.java
- `A` control-panel-cache/src/main/java/io/micronaut/controlpanel/panels/cache/CacheController.java
- `A` control-panel-cache/src/main/java/io/micronaut/controlpanel/panels/cache/CaffeineCacheControlPanel.java
- `A` control-panel-cache/src/main/java/io/micronaut/controlpanel/panels/cache/EhcacheControlPanel.java
- `A` control-panel-cache/src/main/java/io/micronaut/controlpanel/panels/cache/hazelcast/HazelcastControlPanelRegistrar.java
- `A` control-panel-cache/src/main/java/io/micronaut/controlpanel/panels/cache/hazelcast/HazelcastSyncCacheControlPanel.java
- `A` control-panel-cache/src/main/java/io/micronaut/controlpanel/panels/cache/infinispan/InfinispanControlPanelLoader.java
- `A` control-panel-cache/src/main/java/io/micronaut/controlpanel/panels/cache/infinispan/InfinispanSyncCacheControlPanel.java
- `A` control-panel-cache/src/main/java/io/micronaut/controlpanel/panels/cache/package-info.java
- `A` control-panel-cache/src/main/resources/micronaut-control-panel/micronaut-control-panel.properties
- `A` control-panel-cache/src/main/resources/views/cache/body.hbs
- `A` control-panel-cache/src/main/resources/views/cache/detail.hbs
- `A` control-panel-core/AGENTS.md
- `M` control-panel-core/src/main/java/io/micronaut/controlpanel/core/AbstractControlPanel.java
- `A` control-panel-core/src/main/java/io/micronaut/controlpanel/core/AbstractEachBeanControlPanel.java
- `M` control-panel-core/src/main/java/io/micronaut/controlpanel/core/ConfigurableControlPanel.java
- `M` control-panel-core/src/main/java/io/micronaut/controlpanel/core/ControlPanel.java
- `A` control-panel-core/src/main/java/io/micronaut/controlpanel/core/ControlPanelLoader.java
- `M` control-panel-core/src/main/java/io/micronaut/controlpanel/core/ControlPanelRepository.java
- `A` control-panel-core/src/main/java/io/micronaut/controlpanel/core/ControlPanelUrlLogger.java
- `M` control-panel-core/src/main/java/io/micronaut/controlpanel/core/DefaultControlPanelRepository.java
- `M` control-panel-core/src/main/java/io/micronaut/controlpanel/core/config/ControlPanelConfiguration.java
- `M` control-panel-core/src/main/java/io/micronaut/controlpanel/core/config/ControlPanelContextConfigurer.java
- `M` control-panel-core/src/main/java/io/micronaut/controlpanel/core/config/ControlPanelModuleConfiguration.java
- `M` control-panel-core/src/main/java/io/micronaut/controlpanel/core/panels/RoutesControlPanel.java
- `A` control-panel-core/src/main/java/io/micronaut/controlpanel/core/security/ControlPanelSecurityConfiguration.java
- `A` control-panel-core/src/main/java/io/micronaut/controlpanel/core/security/ControlPanelSecurityPaths.java
- `A` control-panel-core/src/main/java/io/micronaut/controlpanel/core/security/ControlPanelSecurityRule.java
- `A` control-panel-core/src/main/java/io/micronaut/controlpanel/core/security/ControlPanelSecurityWriteAccessFilter.java
- `A` control-panel-core/src/main/java/io/micronaut/controlpanel/core/security/ControlPanelWriteAccess.java
- `A` control-panel-core/src/main/java/io/micronaut/controlpanel/core/security/ControlPanelWriteAccessEvaluator.java
- `A` control-panel-core/src/main/java/io/micronaut/controlpanel/core/security/ControlPanelWriteAccessFilter.java
- `A` control-panel-core/src/main/java/io/micronaut/controlpanel/core/security/DefaultControlPanelWriteAccessEvaluator.java
- `A` control-panel-core/src/main/java/io/micronaut/controlpanel/core/security/MissingSecurityFilterCondition.java
- `A` control-panel-core/src/main/java/io/micronaut/controlpanel/core/security/SecurityControlPanelWriteAccessEvaluator.java
- `A` control-panel-core/src/main/java/io/micronaut/controlpanel/core/security/package-info.java
- `M` control-panel-core/src/main/java/io/micronaut/controlpanel/util/ControlPanelUtils.java
- `M` control-panel-core/src/main/resources/META-INF/native-image/io.micronaut.controlpanel/micronaut-control-panel-core/reflect-config.json
- `M` control-panel-core/src/main/resources/micronaut-control-panel/micronaut-control-panel.properties
- `M` control-panel-core/src/main/resources/views/routes/body.hbs
- `M` control-panel-core/src/main/resources/views/routes/detail.hbs
- `M` control-panel-core/src/main/resources/views/routes/routes.hbs
- `A` control-panel-datasource/AGENTS.md
- `A` control-panel-datasource/src/main/java/io/micronaut/controlpanel/panels/datasource/DataSourceControlPanel.java
- `A` control-panel-datasource/src/main/java/io/micronaut/controlpanel/panels/datasource/DataSourceController.java
- `A` control-panel-datasource/src/main/java/io/micronaut/controlpanel/panels/datasource/DataSourceService.java
- `A` control-panel-datasource/src/main/java/io/micronaut/controlpanel/panels/datasource/MermaidUtils.java
- `A` control-panel-datasource/src/main/java/io/micronaut/controlpanel/panels/datasource/PoolInfoSupport.java
- `A` control-panel-datasource/src/main/java/io/micronaut/controlpanel/panels/datasource/model/Body.java
- `A` control-panel-datasource/src/main/java/io/micronaut/controlpanel/panels/datasource/model/Column.java
- `A` control-panel-datasource/src/main/java/io/micronaut/controlpanel/panels/datasource/model/ColumnType.java
- `A` control-panel-datasource/src/main/java/io/micronaut/controlpanel/panels/datasource/model/DataSourceInfo.java
- `A` control-panel-datasource/src/main/java/io/micronaut/controlpanel/panels/datasource/model/DatabaseType.java
- `A` control-panel-datasource/src/main/java/io/micronaut/controlpanel/panels/datasource/model/ForeignKey.java
- `A` control-panel-datasource/src/main/java/io/micronaut/controlpanel/panels/datasource/model/JdbcInfo.java
- `A` control-panel-datasource/src/main/java/io/micronaut/controlpanel/panels/datasource/model/PoolInfo.java
- `A` control-panel-datasource/src/main/java/io/micronaut/controlpanel/panels/datasource/model/Table.java
- `A` control-panel-datasource/src/main/resources/micronaut-control-panel/micronaut-control-panel.properties
- `A` control-panel-datasource/src/main/resources/views/datasource/body.hbs
- `A` control-panel-datasource/src/main/resources/views/datasource/detail-pool-panel.hbs
- `A` control-panel-datasource/src/main/resources/views/datasource/detail-pool-scripts.hbs
- `A` control-panel-datasource/src/main/resources/views/datasource/detail-pool-status-card.hbs
- `A` control-panel-datasource/src/main/resources/views/datasource/detail-query-panel.hbs
- `A` control-panel-datasource/src/main/resources/views/datasource/detail-query-scripts.hbs
- `A` control-panel-datasource/src/main/resources/views/datasource/detail-scripts.hbs
- `A` control-panel-datasource/src/main/resources/views/datasource/detail-table-browser-scripts.hbs
- `A` control-panel-datasource/src/main/resources/views/datasource/detail-table-detail.hbs
- `A` control-panel-datasource/src/main/resources/views/datasource/detail-tables-page.hbs
- `A` control-panel-datasource/src/main/resources/views/datasource/detail-tables-panel.hbs
- `A` control-panel-datasource/src/main/resources/views/datasource/detail-tabs.hbs
- `A` control-panel-datasource/src/main/resources/views/datasource/detail.hbs
- `A` control-panel-hibernate/src/main/java/io/micronaut/controlpanel/panels/hibernate/HibernateControlPanel.java
- `A` control-panel-hibernate/src/main/java/io/micronaut/controlpanel/panels/hibernate/HibernateController.java
- `A` control-panel-hibernate/src/main/java/io/micronaut/controlpanel/panels/hibernate/HibernateRuntimeService.java
- `A` control-panel-hibernate/src/main/java/io/micronaut/controlpanel/panels/hibernate/model/HibernateBody.java
- `A` control-panel-hibernate/src/main/java/io/micronaut/controlpanel/panels/hibernate/model/HibernateCacheRegionInfo.java
- `A` control-panel-hibernate/src/main/java/io/micronaut/controlpanel/panels/hibernate/model/HibernateCollectionInfo.java
- `A` control-panel-hibernate/src/main/java/io/micronaut/controlpanel/panels/hibernate/model/HibernateCollectionStatisticsInfo.java
- `A` control-panel-hibernate/src/main/java/io/micronaut/controlpanel/panels/hibernate/model/HibernateDataSourceInfo.java
- `A` control-panel-hibernate/src/main/java/io/micronaut/controlpanel/panels/hibernate/model/HibernateEntityAttributeInfo.java
- `A` control-panel-hibernate/src/main/java/io/micronaut/controlpanel/panels/hibernate/model/HibernateEntityInfo.java
- `A` control-panel-hibernate/src/main/java/io/micronaut/controlpanel/panels/hibernate/model/HibernateEntityStatisticsInfo.java
- `A` control-panel-hibernate/src/main/java/io/micronaut/controlpanel/panels/hibernate/model/HibernateNamedQueryInfo.java
- `A` control-panel-hibernate/src/main/java/io/micronaut/controlpanel/panels/hibernate/model/HibernateQueryInfo.java
- `A` control-panel-hibernate/src/main/java/io/micronaut/controlpanel/panels/hibernate/model/HibernateSessionFactoryInfo.java
- `A` control-panel-hibernate/src/main/java/io/micronaut/controlpanel/panels/hibernate/package-info.java
- `A` control-panel-hibernate/src/main/resources/micronaut-control-panel/micronaut-control-panel.properties
- `A` control-panel-hibernate/src/main/resources/views/hibernate/body.hbs
- `A` control-panel-hibernate/src/main/resources/views/hibernate/detail-cache.hbs
- `A` control-panel-hibernate/src/main/resources/views/hibernate/detail-data-sources.hbs
- `A` control-panel-hibernate/src/main/resources/views/hibernate/detail-delete-dialog.hbs
- `A` control-panel-hibernate/src/main/resources/views/hibernate/detail-entity-types.hbs
- `A` control-panel-hibernate/src/main/resources/views/hibernate/detail-hql-console.hbs
- `A` control-panel-hibernate/src/main/resources/views/hibernate/detail-named-queries.hbs
- `A` control-panel-hibernate/src/main/resources/views/hibernate/detail-scripts.hbs
- `A` control-panel-hibernate/src/main/resources/views/hibernate/detail-session-details.hbs
- `A` control-panel-hibernate/src/main/resources/views/hibernate/detail-statistics.hbs
- `A` control-panel-hibernate/src/main/resources/views/hibernate/detail-tabs.hbs
- `A` control-panel-hibernate/src/main/resources/views/hibernate/detail.hbs
- `A` control-panel-kafka/AGENTS.md
- `A` control-panel-kafka/src/main/java/io/micronaut/controlpanel/panels/kafka/HealthKafkaStreamsRuntimeStateResolver.java
- `A` control-panel-kafka/src/main/java/io/micronaut/controlpanel/panels/kafka/KafkaStreamsControlPanel.java
- `A` control-panel-kafka/src/main/java/io/micronaut/controlpanel/panels/kafka/KafkaStreamsRuntimeState.java
- `A` control-panel-kafka/src/main/java/io/micronaut/controlpanel/panels/kafka/KafkaStreamsRuntimeStateResolver.java
- `A` control-panel-kafka/src/main/java/io/micronaut/controlpanel/panels/kafka/UnavailableKafkaStreamsRuntimeStateResolver.java
- `A` control-panel-kafka/src/main/resources/micronaut-control-panel/micronaut-control-panel.properties
- `A` control-panel-kafka/src/main/resources/views/health/kafkaStreams.hbs
- `A` control-panel-kafka/src/main/resources/views/kafka-streams/body.hbs
- `A` control-panel-kafka/src/main/resources/views/kafka-streams/detail.hbs
- `A` control-panel-management/AGENTS.md
- `M` control-panel-management/src/main/java/io/micronaut/controlpanel/panels/management/AllPlainEnvironmentEndpointFilter.java
- `M` control-panel-management/src/main/java/io/micronaut/controlpanel/panels/management/EnvironmentControlPanel.java
- `M` control-panel-management/src/main/java/io/micronaut/controlpanel/panels/management/HealthControlPanel.java
- `A` control-panel-management/src/main/java/io/micronaut/controlpanel/panels/management/InfoControlPanel.java
- `M` control-panel-management/src/main/java/io/micronaut/controlpanel/panels/management/LoggersControlPanel.java
- `A` control-panel-management/src/main/java/io/micronaut/controlpanel/panels/management/LoggersController.java
- `A` control-panel-management/src/main/java/io/micronaut/controlpanel/panels/management/MetricsControlPanel.java
- `A` control-panel-management/src/main/java/io/micronaut/controlpanel/panels/management/MetricsControlPanelController.java
- `R088` control-panel-management/src/main/java/io/micronaut/controlpanel/panels/management/beans/BeansControlPanel.java
- `A` control-panel-management/src/main/java/io/micronaut/controlpanel/panels/management/beans/DisabledBeansControlPanel.java
- `A` control-panel-management/src/main/resources/META-INF/native-image/io.micronaut.controlpanel/micronaut-control-panel-management/reflect-config.json
- `M` control-panel-management/src/main/resources/micronaut-control-panel/micronaut-control-panel.properties
- `M` control-panel-management/src/main/resources/views/beans/body.hbs
- `M` control-panel-management/src/main/resources/views/beans/detail.hbs
- `M` control-panel-management/src/main/resources/views/beans/package.hbs
- `A` control-panel-management/src/main/resources/views/disabled-beans/body.hbs
- `A` control-panel-management/src/main/resources/views/disabled-beans/detail.hbs
- `M` control-panel-management/src/main/resources/views/env/body.hbs
- `M` control-panel-management/src/main/resources/views/env/detail.hbs
- `M` control-panel-management/src/main/resources/views/health/detail.hbs
- `A` control-panel-management/src/main/resources/views/info/body.hbs
- `A` control-panel-management/src/main/resources/views/info/detail.hbs
- `M` control-panel-management/src/main/resources/views/loggers/body.hbs
- `M` control-panel-management/src/main/resources/views/loggers/detail.hbs
- `A` control-panel-management/src/main/resources/views/metrics/body.hbs
- `A` control-panel-management/src/main/resources/views/metrics/detail.hbs
- `A` control-panel-object-storage/AGENTS.md
- `M` control-panel-object-storage/src/main/java/io/micronaut/controlpanel/panels/objectstorage/ObjectStorageControlPanel.java
- `M` control-panel-object-storage/src/main/java/io/micronaut/controlpanel/panels/objectstorage/ObjectStorageController.java
- `M` control-panel-object-storage/src/main/resources/views/object-storage/body.hbs
- `M` control-panel-object-storage/src/main/resources/views/object-storage/detail.hbs
- `A` control-panel-ui/.gitignore
- `A` control-panel-ui/AGENTS.md
- `M` control-panel-ui/src/main/java/io/micronaut/controlpanel/ui/ControlPanelApi.java
- `M` control-panel-ui/src/main/java/io/micronaut/controlpanel/ui/ControlPanelController.java
- `M` control-panel-ui/src/main/java/io/micronaut/controlpanel/ui/handlebars/HandlebarsHelperRegistrar.java
- `A` control-panel-ui/src/main/java/io/micronaut/controlpanel/ui/package-info.java
- `M` control-panel-ui/src/main/java/io/micronaut/controlpanel/ui/util/EndpointUtils.java
- `A` control-panel-ui/src/main/javascript/.gitignore
- `A` control-panel-ui/src/main/javascript/editor.mjs
- `A` control-panel-ui/src/main/javascript/package.json
- `A` control-panel-ui/src/main/javascript/rollup.config.mjs
- `A` control-panel-ui/src/main/resources/micronaut-control-panel/micronaut-control-panel.properties
- `M` control-panel-ui/src/main/resources/static/css/dashboard.css
- `A` control-panel-ui/src/main/resources/static/img/micronaut-logo-dark.svg
- `A` control-panel-ui/src/main/resources/static/img/micronaut-logo-white.svg
- `A` control-panel-ui/src/main/resources/static/img/micronaut-sally.svg
- `A` control-panel-ui/src/main/resources/static/js/dashboard.js
- `M` control-panel-ui/src/main/resources/views/detail.hbs
- `M` control-panel-ui/src/main/resources/views/index.hbs
- `M` control-panel-ui/src/main/resources/views/layout.hbs

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `A` control-panel-cache/src/test/java/io/micronaut/controlpanel/panels/cache/AbstractCacheControlPanelTest.java
- `A` control-panel-cache/src/test/java/io/micronaut/controlpanel/panels/cache/CaffeineCacheControlPanelTest.java
- `A` control-panel-cache/src/test/java/io/micronaut/controlpanel/panels/cache/EhcacheControlPanelTest.java
- `A` control-panel-cache/src/test/java/io/micronaut/controlpanel/panels/cache/HazelcastSyncCacheControlPanelTest.java
- `A` control-panel-cache/src/test/java/io/micronaut/controlpanel/panels/cache/InfinispanSyncCacheControlPanelTest.java
- `A` control-panel-cache/src/test/resources/application-infinispan.yml
- `A` control-panel-cache/src/test/resources/logback-test.xml
- `A` control-panel-core/src/main/java/io/micronaut/controlpanel/core/panels/TestResourcesControlPanel.java
- `A` control-panel-core/src/main/resources/views/test-resources/body.hbs
- `D` control-panel-core/src/test/groovy/io/micronaut/controlpanel/core/DefaultControlPanelRepositorySpec.groovy
- `D` control-panel-core/src/test/groovy/io/micronaut/controlpanel/core/config/ControlPanelModuleConfigurationSpec.groovy
- `D` control-panel-core/src/test/groovy/io/micronaut/controlpanel/core/panels/RoutesControlPanelSpec.groovy
- `A` control-panel-core/src/test/java/example/app/DummyController.java
- `A` control-panel-core/src/test/java/io/micronaut/controlpanel/core/DefaultControlPanelRepositoryTest.java
- `A` control-panel-core/src/test/java/io/micronaut/controlpanel/core/config/ControlPanelModuleConfigurationTest.java
- `A` control-panel-core/src/test/java/io/micronaut/controlpanel/core/panels/RoutesControlPanelTest.java
- `A` control-panel-core/src/test/java/io/micronaut/controlpanel/core/security/ControlPanelSecurityConfigurationTest.java
- `A` control-panel-core/src/test/java/io/micronaut/controlpanel/core/security/ControlPanelSecurityRuleTest.java
- `A` control-panel-datasource/src/main/java/io/micronaut/controlpanel/panels/datasource/ConnectionPoolInspector.java
- `A` control-panel-datasource/src/main/java/io/micronaut/controlpanel/panels/datasource/HikariConnectionPoolInspector.java
- `A` control-panel-datasource/src/main/java/io/micronaut/controlpanel/panels/datasource/OracleUcpConnectionPoolInspector.java
- `A` control-panel-datasource/src/test/java/io/micronaut/controlpanel/panels/datasource/DataSourceControlPanelTest.java
- `A` control-panel-datasource/src/test/java/io/micronaut/controlpanel/panels/datasource/DataSourceControllerTest.java
- `A` control-panel-datasource/src/test/java/io/micronaut/controlpanel/panels/datasource/DataSourceOracleRelationshipJsonQueryIntegrationTest.java
- `A` control-panel-datasource/src/test/java/io/micronaut/controlpanel/panels/datasource/DataSourceRelationshipJsonQueryIntegrationTest.java
- `A` control-panel-datasource/src/test/java/io/micronaut/controlpanel/panels/datasource/DataSourceServiceTest.java
- `A` control-panel-datasource/src/test/java/io/micronaut/controlpanel/panels/datasource/DataSourceTemplatesTest.java
- `A` control-panel-datasource/src/test/resources/logback-test.xml
- `A` control-panel-hibernate/src/main/java/io/micronaut/controlpanel/panels/hibernate/model/HibernateStatisticsInfo.java
- `A` control-panel-hibernate/src/test/java/io/micronaut/controlpanel/panels/hibernate/HibernateControlPanelTest.java
- `A` control-panel-hibernate/src/test/java/io/micronaut/controlpanel/panels/hibernate/HibernateControllerTest.java
- `A` control-panel-hibernate/src/test/java/io/micronaut/controlpanel/panels/hibernate/HibernateRuntimeServiceTest.java
- `A` control-panel-hibernate/src/test/resources/logback-test.xml
- `A` control-panel-kafka/src/test/java/io/micronaut/controlpanel/panels/kafka/KafkaStreamsControlPanelTest.java
- `D` control-panel-management/src/test/groovy/io/micronaut/controlpanel/panels/management/AllPlainEnvironmentEndpointFilterSpec.groovy
- `D` control-panel-management/src/test/groovy/io/micronaut/controlpanel/panels/management/BeansControlPanelSpec.groovy
- `D` control-panel-management/src/test/groovy/io/micronaut/controlpanel/panels/management/EnvironmentControlPanelSpec.groovy
- `D` control-panel-management/src/test/groovy/io/micronaut/controlpanel/panels/management/HealthControlPanelSpec.groovy
- `D` control-panel-management/src/test/groovy/io/micronaut/controlpanel/panels/management/LoggersControlPanelSpec.groovy
- `A` control-panel-management/src/test/java/io/micronaut/controlpanel/panels/management/AllPlainEnvironmentEndpointFilterTest.java
- `A` control-panel-management/src/test/java/io/micronaut/controlpanel/panels/management/EnvironmentControlPanelTest.java
- `A` control-panel-management/src/test/java/io/micronaut/controlpanel/panels/management/HealthControlPanelTest.java
- `A` control-panel-management/src/test/java/io/micronaut/controlpanel/panels/management/InfoControlPanelTest.java
- `A` control-panel-management/src/test/java/io/micronaut/controlpanel/panels/management/LoggersControlPanelTest.java
- `A` control-panel-management/src/test/java/io/micronaut/controlpanel/panels/management/MetricsControlPanelTest.java
- `A` control-panel-management/src/test/java/io/micronaut/controlpanel/panels/management/beans/BeansControlPanelTest.java
- `D` control-panel-object-storage/src/test/groovy/io/micronaut/controlpanel/panels/objectstorage/ObjectStorageControlPanelSpec.groovy
- `A` control-panel-object-storage/src/test/java/io/micronaut/controlpanel/panels/objectstorage/ObjectStorageControlPanelAdditionalTest.java
- `A` control-panel-object-storage/src/test/java/io/micronaut/controlpanel/panels/objectstorage/ObjectStorageControlPanelTest.java
- `D` control-panel-ui/src/test/groovy/io/micronaut/controlpanel/ui/ControlPanelControllerPathSpec.groovy
- `D` control-panel-ui/src/test/groovy/io/micronaut/controlpanel/ui/ControlPanelControllerSpec.groovy
- `D` control-panel-ui/src/test/groovy/io/micronaut/controlpanel/ui/handlebars/HandlebarsCacheConfigSpec.groovy
- `D` control-panel-ui/src/test/groovy/io/micronaut/controlpanel/ui/handlebars/HandlebarsHelperRegistrarSpec.groovy
- `D` control-panel-ui/src/test/groovy/io/micronaut/controlpanel/ui/handlebars/HandlebarsPrecompileSpec.groovy
- `D` control-panel-ui/src/test/groovy/io/micronaut/controlpanel/ui/util/EndpointUtilsSpec.groovy
- `A` control-panel-ui/src/test/java/io/micronaut/controlpanel/ui/ControlPanelControllerPathTest.java
- `A` control-panel-ui/src/test/java/io/micronaut/controlpanel/ui/ControlPanelControllerTest.java
- `A` control-panel-ui/src/test/java/io/micronaut/controlpanel/ui/ControlPanelSecurityTest.java
- `A` control-panel-ui/src/test/java/io/micronaut/controlpanel/ui/handlebars/HandlebarsCacheConfigTest.java
- `A` control-panel-ui/src/test/java/io/micronaut/controlpanel/ui/handlebars/HandlebarsHelperRegistrarTest.java
- `A` control-panel-ui/src/test/java/io/micronaut/controlpanel/ui/handlebars/HandlebarsPrecompileTest.java
- `A` control-panel-ui/src/test/java/io/micronaut/controlpanel/ui/util/EndpointUtilsTest.java

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

