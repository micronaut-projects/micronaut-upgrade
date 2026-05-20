 Compared micronaut-data as mn4 → mn5.

  Scope

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-data, branch 4.15.x, SHA 88d0e08d09e0
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-data, branch 5.0.x, SHA 56c975daa56c
  - Same remote, both clean: git@github.com:micronaut-projects/micronaut-data.git
  - Report: /private/tmp/micronaut-data-4.15-to-5.0-comparison.md

  Key Findings

  - Major version move: projectVersion 4.15.0-SNAPSHOT -> 5.0.1-SNAPSHOT, Micronaut 4.10.6 -> 5.0.0, Gradle
    8.14.3 -> 9.5.1, Java SDK pin added as 25.0.1-graal.
  - Confirmed breaking notes: repository save/saveAll now do save-or-update instead of always insert;
    explicit insert/insertAll methods and micronaut.data.save-as-insert=true are documented migration paths.
  - Synchronous transaction/connection managers no longer automatically propagate status into
    PropagatedContext; manual code must use TransactionStatus#propagate or ConnectionStatus#propagate.
  - Embedded field naming changed to the new standard behavior, with
    micronaut.data.embedded.naming.strategy=LEGACY available for compatibility.
  - RxJava support moved from RxJava 2 to RxJava 3: micronaut-rxjava2:2.8.0 removed, micronaut-rxjava3:4.0.0
    added, and repository APIs now import io.reactivex.rxjava3.
  - Kotlin repository APIs were expanded with new blocking KotlinCrudRepository /
    KotlinPageableCrudRepository, while coroutine repositories gained explicit insert / insertAll.
  - New or expanded features include ConnectionCapabilities SPI, JDBC/R2DBC returning support, Oracle
    RETURNING INTO, MongoDB update-returning/find-one-and-update support, SQL vector support, SQL geospatial
    docs/examples, UUID array support, Jackson annotation handling, @JsonView work, and Hibernate streaming
    @Fetch(number).
  - Large dependency/platform uplift: Kotlin 1.9.25 -> 2.3.21, Groovy 4.0.28 -> 5.0.6, Spring Boot 3.5.6 ->
    4.0.6, Spring Data 3.5.4 -> 4.0.5, Micronaut SQL 6.3.1 -> 7.0.1, R2DBC 6.1.0 -> 7.0.1, Mongo 5.7.0 ->
    6.0.1, Serde 2.15.4 -> 3.0.0.

  Diff size: 2113 files changed, 73709 insertions(+), 35800 deletions(-). I did not run tests; this was a
  folder comparison and targeted source/build-diff review only.


# Release Note Comparison

Generated: 2026-05-19 11:49 UTC
Comparison: `4.15.x` -> `5.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-data` | `4.15.x` | `88d0e08d09e0` | `git@github.com:micronaut-projects/micronaut-data.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-data` | `5.0.x` | `56c975daa56c` | `git@github.com:micronaut-projects/micronaut-data.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-data`
- Commit candidates found: 424
- File changes listed: 1200
- Version values listed: 98
- File status counts: A=365, D=103, M=719, R=13

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `4.15.0-SNAPSHOT` | `5.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.antlr` | `org.antlr:antlr4:4.13.2` | `org.antlr:antlr4:4.13.2` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.antlr-runtime` | `org.antlr:antlr4-runtime:4.13.2` | `org.antlr:antlr4-runtime:4.13.2` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.benchmark-spring-data-bom` | `org.springframework.data:spring-data-bom:2024.1.10` | `org.springframework.data:spring-data-bom:2025.1.5` | `changed` |
| `gradle/libs.versions.toml` | `libraries.error-prone-core` | `not present` | `com.google.errorprone:error_prone_core:2.49.0` | `added` |
| `gradle/libs.versions.toml` | `libraries.gradle-errorprone` | `not present` | `net.ltgt.errorprone:net.ltgt.errorprone.gradle.plugin:5.1.0` | `added` |
| `gradle/libs.versions.toml` | `libraries.gradle-jmh` | `me.champeau.jmh:jmh-gradle-plugin:0.7.3` | `me.champeau.jmh:jmh-gradle-plugin:0.7.3` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.gradle-kotlin` | `org.jetbrains.kotlin:kotlin-gradle-plugin:1.9.25` | `org.jetbrains.kotlin:kotlin-gradle-plugin:2.3.21` | `changed` |
| `gradle/libs.versions.toml` | `libraries.gradle-kotlin-allopen` | `org.jetbrains.kotlin:kotlin-allopen:1.9.25` | `org.jetbrains.kotlin:kotlin-allopen:2.3.21` | `changed` |
| `gradle/libs.versions.toml` | `libraries.gradle-kotlin-noarg` | `org.jetbrains.kotlin:kotlin-noarg:1.9.25` | `org.jetbrains.kotlin:kotlin-noarg:2.3.21` | `changed` |
| `gradle/libs.versions.toml` | `libraries.gradle-ksp` | `com.google.devtools.ksp:symbol-processing-gradle-plugin:1.9.25-1.0.20` | `com.google.devtools.ksp:symbol-processing-gradle-plugin:2.3.8` | `changed` |
| `gradle/libs.versions.toml` | `libraries.gradle-micronaut` | `io.micronaut.gradle:micronaut-gradle-plugin:4.6.0` | `io.micronaut.gradle:micronaut-gradle-plugin:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.gradle-nullaway` | `not present` | `net.ltgt.errorprone:net.ltgt.errorprone.gradle.plugin:5.1.0` | `added` |
| `gradle/libs.versions.toml` | `libraries.gradle-shadow` | `gradle.plugin.com.github.johnrengelman:shadow:8.0.0` | `com.gradleup.shadow:shadow-gradle-plugin:9.4.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.gradle-spring-boot` | `org.springframework.boot:spring-boot-gradle-plugin:3.5.6` | `org.springframework.boot:spring-boot-gradle-plugin:4.0.6` | `changed` |
| `gradle/libs.versions.toml` | `libraries.gradle-spring-dependencies` | `io.spring.gradle:dependency-management-plugin:1.1.7` | `io.spring.gradle:dependency-management-plugin:1.1.7` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.groovy-dateutil` | `org.apache.groovy:groovy-dateutil:4.0.28` | `org.apache.groovy:groovy-dateutil:5.0.6` | `changed` |
| `gradle/libs.versions.toml` | `libraries.groovy-yaml` | `not present` | `org.apache.groovy:groovy-yaml:5.0.6` | `added` |
| `gradle/libs.versions.toml` | `libraries.h2gis` | `not present` | `org.orbisgis:h2gis:2.2.5` | `added` |
| `gradle/libs.versions.toml` | `libraries.jakarta-data-tck` | `jakarta-data-tck:1.0.1` | `jakarta-data-tck:1.1.0-M3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.jmh-annprocess` | `org.openjdk.jmh:jmh-generator-annprocess:1.37` | `org.openjdk.jmh:jmh-generator-annprocess:1.37` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.jmh-core` | `org.openjdk.jmh:jmh-core:1.37` | `org.openjdk.jmh:jmh-core:1.37` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.kotlin-coroutines` | `org.jetbrains.kotlinx:kotlinx-coroutines-core:1.9.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.kotlin-coroutines-reactive` | `org.jetbrains.kotlinx:kotlinx-coroutines-reactive:1.9.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.kotlin-coroutines-reactor` | `org.jetbrains.kotlinx:kotlinx-coroutines-reactor:1.9.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.lombok` | `org.projectlombok:lombok:1.18.42` | `org.projectlombok:lombok:1.18.46` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-jakarta-data-api` | `managed-jakarta-data-api:1.0.1` | `managed-jakarta-data-api:1.1.0-M3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-jakarta-data-stateful` | `not present` | `managed-jakarta-data-stateful:1.1.0-M3` | `added` |
| `gradle/libs.versions.toml` | `libraries.managed-javax-persistence-api` | `javax.persistence:javax.persistence-api:2.2` | `javax.persistence:javax.persistence-api:2.2` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-pg-vector` | `not present` | `managed-pg-vector:0.1.6` | `added` |
| `gradle/libs.versions.toml` | `libraries.micronaut-azure-cosmos` | `io.micronaut.azure:micronaut-azure-cosmos:5.12.0` | `io.micronaut.azure:micronaut-azure-cosmos:6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-coherence` | `io.micronaut.coherence:micronaut-coherence-bom:5.0.6` | `io.micronaut.coherence:micronaut-coherence-bom:6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-docs` | `io.micronaut.docs:micronaut-docs-asciidoc-config-props:3.0.0` | `io.micronaut.docs:micronaut-docs-asciidoc-config-props:3.0.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.micronaut-flyway` | `io.micronaut.flyway:micronaut-flyway-bom:7.8.0` | `io.micronaut.flyway:micronaut-flyway-bom:8.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-kotlin` | `micronaut-kotlin:4.7.0` | `micronaut-kotlin:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-logging` | `io.micronaut.logging:micronaut-logging-bom:1.7.1` | `io.micronaut.logging:micronaut-logging-bom:2.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-mongo` | `io.micronaut.mongodb:micronaut-mongo-bom:5.7.0` | `io.micronaut.mongodb:micronaut-mongo-bom:6.0.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-multitenancy` | `micronaut-multitenancy:5.7.0` | `micronaut-multitenancy:6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-r2dbc` | `io.micronaut.r2dbc:micronaut-r2dbc-bom:6.1.0` | `io.micronaut.r2dbc:micronaut-r2dbc-bom:7.0.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-reactor` | `micronaut-reactor:3.8.0` | `micronaut-reactor:4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-rxjava2` | `micronaut-rxjava2:2.8.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-rxjava3` | `not present` | `micronaut-rxjava3:4.0.0` | `added` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.15.4` | `io.micronaut.serde:micronaut-serde-bom:3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-spring` | `io.micronaut.spring:micronaut-spring-bom:5.11.2` | `io.micronaut.spring:micronaut-spring-bom:6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-sql` | `io.micronaut.sql:micronaut-sql-bom:6.3.1` | `io.micronaut.sql:micronaut-sql-bom:7.0.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-testresources` | `micronaut-testresources:2.10.1` | `micronaut-testresources:4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-testresources-client` | `micronaut-testresources-client:2.10.1` | `micronaut-testresources-client:4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-testresources-extensions-junit-platform` | `micronaut-testresources-extensions-junit-platform:2.10.1` | `micronaut-testresources-extensions-junit-platform:4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-validation` | `micronaut-validation:4.11.0` | `micronaut-validation:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.nullaway` | `not present` | `com.uber.nullaway:nullaway:0.13.4` | `added` |
| `gradle/libs.versions.toml` | `libraries.spring-data-commons` | `org.springframework.data:spring-data-commons:3.5.4` | `org.springframework.data:spring-data-commons:4.0.5` | `changed` |
| `gradle/libs.versions.toml` | `libraries.spring-data-jpa` | `org.springframework.data:spring-data-jpa:3.5.4` | `org.springframework.data:spring-data-jpa:4.0.5` | `changed` |
| `gradle/libs.versions.toml` | `versions.antlr` | `4.13.2` | `4.13.2` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.benchmark-spring-data` | `2024.1.10` | `2025.1.5` | `changed` |
| `gradle/libs.versions.toml` | `versions.error_prone_core` | `not present` | `2.49.0` | `added` |
| `gradle/libs.versions.toml` | `versions.errorprone-gradle-plugin` | `not present` | `5.1.0` | `added` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.28` | `5.0.6` | `changed` |
| `gradle/libs.versions.toml` | `versions.groovy_yaml` | `not present` | `5.0.6` | `added` |
| `gradle/libs.versions.toml` | `versions.h2gis` | `not present` | `2.2.5` | `added` |
| `gradle/libs.versions.toml` | `versions.jmh` | `1.37` | `1.37` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.jmh-gradle-plugin` | `0.7.3` | `0.7.3` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.kotlin-coroutines` | `1.9.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.kotlin-gradle-plugin` | `1.9.25` | `2.3.21` | `changed` |
| `gradle/libs.versions.toml` | `versions.ksp-gradle-plugin` | `1.9.25-1.0.20` | `2.3.8` | `changed` |
| `gradle/libs.versions.toml` | `versions.lombok` | `1.18.42` | `1.18.46` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-jakarta-data` | `1.0.1` | `1.1.0-M3` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-javax-persistence` | `2.2` | `2.2` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-pg-vector` | `not present` | `0.1.6` | `added` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.6` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-azure` | `5.12.0` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-coherence` | `5.0.6` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `3.0.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.micronaut-flyway` | `7.8.0` | `8.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.6.0` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-kotlin` | `4.7.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.1` | `2.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-mongo` | `5.7.0` | `6.0.1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-multitenancy` | `5.7.0` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-platform` | `4.9.4` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-r2dbc` | `6.1.0` | `7.0.1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-reactor` | `3.8.0` | `4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-rxjava2` | `2.8.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-rxjava3` | `not present` | `4.0.0` | `added` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.15.4` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-spring` | `5.11.2` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-sql` | `6.3.1` | `7.0.1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.9.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-testresources` | `2.10.1` | `4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.11.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.nullaway` | `not present` | `0.13.4` | `added` |
| `gradle/libs.versions.toml` | `versions.shadow-gradle-plugin` | `8.0.0` | `9.4.1` | `changed` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.2-groovy-4.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.spring-boot-gradle-plugin` | `3.5.6` | `4.0.6` | `changed` |
| `gradle/libs.versions.toml` | `versions.spring-data` | `3.5.4` | `4.0.5` | `changed` |
| `gradle/libs.versions.toml` | `versions.spring-dependency-management-gradle-plugin` | `1.1.7` | `1.1.7` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.testcontainers` | `1.19.4` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `e00774b49476` Create KotlinCrudRepository that does not suspend. Removes need for Optional 5.0.x (#3570) (Charlie Harvey, 2026-05-18)
- `37f073a9c0b6` remove testcontainers version (Sergio del Amo, 2026-05-07)
- `88f6f6f2a7df` remove spock version (Sergio del Amo, 2026-05-07)
- `30fae3c46d54` remove unsused import (Dimitrije Zdravkovic, 2026-02-05)
- `28c7ac079099` remove unsused address property (Dimitrije Zdravkovic, 2026-02-05)
- `076e713db9eb` remove flyway (Dimitrije Zdravkovic, 2026-02-03)
- `90d7a0beebf4` fix buildingViewTest and remove star imports (Dimitrije Zdravkovic, 2026-01-21)
- `946cd1ba7a18` Remove NullUnmarked in JDBC (#3687) (Denis Stepanov, 2026-01-15)
- `119be09a8bf3` Remove build trigger for branches (radovanradic, 2025-12-22)
- `1e74cfd8030c` remove star imports (Dimitrije Zdravkovic, 2025-12-19)
- `691409582180` remove star imports (Dimitrije Zdravkovic, 2025-12-19)
- `806f0aeb892a` remove flyway from build.gradle (Dimitrije Zdravkovic, 2025-12-17)
- `f732d38c83dd` remove address methods (Dimitrije Zdravkovic, 2025-12-16)
- `01f80b6e0d59` remove default entity value (Dimitrije Zdravkovic, 2025-12-16)
- `265024b4d684` remove buildForJsonView and flyway (Dimitrije Zdravkovic, 2025-12-15)
- `63cf34110942` remove buildForJsonView parameter (Dimitrije Zdravkovic, 2025-12-15)
- `5d8a4bd18b3b` remove flyway (Dimitrije Zdravkovic, 2025-12-11)
- `faae96562e6d` Remove star import (Dimitrije Zdravkovic, 2025-12-09)
- `e62a75e60d11` Remove star import (Dimitrije Zdravkovic, 2025-12-08)
- `0b424746d4bc` remove old approach (Dimitrije Zdravkovic, 2025-12-05)
- `9c35503fdf7b` Remove 'paginate-embeddedid' branch from workflow (Radovan Radic, 2025-11-18)
- `dd321def1f6f` Remove 'paginate-embeddedid' branch from workflow (Radovan Radic, 2025-11-18)
- `71734286fd80` Remove build trigger (radovanradic, 2025-11-10)
- `75e44eda85d6` Remove deprecated specifications (#3583) (Denis Stepanov, 2025-11-07)
- `03d9c8fe8ea5` Remove deprecated query builder, stored query methods (#3571) (Denis Stepanov, 2025-11-05)

### Features

- `596025260072` Add support for Jackson annotations (#3736) (Dimitrije Zdravkovic, 2026-05-18)
- `fd55001491bd` Support setting transaction priority for the Oracle database (#3835) (Radovan Radic, 2026-05-18)
- `d5afd0021b66` Add compatibility option for legacy embedded naming (#3850) (Radovan Radic, 2026-05-07)
- `5961aed49d63` Add UUID array data type support for JDBC and R2DBC (#3846) (Radovan Radic, 2026-05-05)
- `b0e2b11b2bfe` Add ConnectionCapabilities API (#3821) (Sergio del Amo, 2026-04-23)
- `ef32af88367b` Support Mongo DB findOneAndUpdate (#3777) (Radovan Radic, 2026-04-21)
- `756bebf1b4c2` Support "RETURNING INTO" clause for INSERT/UPDATE/DELETE in Oracle database (#3669) (Radovan Radic, 2026-04-20)
- `9377d5aea39a` Support R2dbc INSERT/UPDATE/DELETE returning (#3790) (Radovan Radic, 2026-04-02)
- `11e7fdb33d4e` Add Relation.unique property to mark relations that should not be repeated (Andriy Dmytruk, 2026-02-10)
- `64cbc131755f` add table_name field for @JsonView annotation (Dimitrije Zdravkovic, 2026-02-09)
- `d015491f1904` Add address subview (Dimitrije Zdravkovic, 2026-02-06)
- `3baf06d7e154` add compile time checks (Dimitrije Zdravkovic, 2026-02-03)
- `3803ea256318` Introduce @Fetch(number) annotation to specify the fetch size for streaming repository methods (#3683) (Radovan Radic, 2026-01-19)
- `787c343f1a6e` support json view creation for composite ids (Dimitrije Zdravkovic, 2026-01-19)
- `7d3aa850216e` Introduce NullAway and eliminate null errors (#3674) (Denis Stepanov, 2026-01-09)
- `67e3fd3a1f9b` Add Java 25 to GraalVM workflow matrix (Radovan Radic, 2025-12-22)
- `9c5642bccb08` add imports (Dimitrije Zdravkovic, 2025-12-19)
- `78146b8069ce` add r2dbc jsonview support (Dimitrije Zdravkovic, 2025-12-11)
- `5ced0fa3d95f` Add changes needed for mongo 6 (radovanradic, 2025-11-12)
- `ea6a96778186` Add back MongoDB upgrade and fix for failing tests. (radovanradic, 2025-11-10)

### Fixes

- `dcef9c666ef0` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to v7.0.1-m2 (#3818) (renovate[bot], 2026-04-21)
- `4872a3547cd1` fix(deps): update dependency com.google.errorprone:error_prone_core to v2.49.0 (#3814) (renovate[bot], 2026-04-20)
- `955bc26121c9` fix(deps): update spring data (#3813) (renovate[bot], 2026-04-20)
- `eb75a7fae254` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v5.0.0-m2 (#3812) (renovate[bot], 2026-04-20)
- `cbb8cea30bf9` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m23 (#3810) (renovate[bot], 2026-04-19)
- `9573cb80dd25` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m7 (#3811) (renovate[bot], 2026-04-19)
- `81f91b87811e` fix(deps): update dependency io.micronaut.reactor:micronaut-reactor-bom to v4.0.0-m2 (#3806) (renovate[bot], 2026-04-15)
- `401133d42edc` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m22 (#3804) (renovate[bot], 2026-04-14)
- `e0675fc03108` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m6 (#3796) (renovate[bot], 2026-04-03)
- `f87b1b2b1424` fix(deps): update groovy monorepo to v5.0.5 (#3793) (renovate[bot], 2026-04-02)
- `25195dbdd807` fix(deps): update dependency com.gradleup.shadow:shadow-gradle-plugin to v9.4.1 (#3787) (renovate[bot], 2026-04-01)
- `d83c17d3d4cf` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m5 (#3789) (renovate[bot], 2026-04-01)
- `d671fc89c298` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m19 (#3782) (renovate[bot], 2026-04-01)
- `e05923984ac5` fix(deps): update dependency org.springframework.boot:spring-boot-gradle-plugin to v4.0.5 (#3786) (renovate[bot], 2026-03-26)
- `c55e61e0ec3b` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m4 (#3785) (renovate[bot], 2026-03-26)
- `f0c3c1bb0c72` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m3 (#3775) (renovate[bot], 2026-03-25)
- `91e7429ef4ff` fix(deps): update dependency io.micronaut.r2dbc:micronaut-r2dbc-bom to v7.0.1-M1 (#3772) (renovate[bot], 2026-03-23)
- `729d44e1f6ae` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to v7.0.1-M1 (#3771) (renovate[bot], 2026-03-23)
- `faf3c0d432da` fix(deps): update dependency org.springframework.boot:spring-boot-gradle-plugin to v4.0.4 (#3763) (renovate[bot], 2026-03-19)
- `78545869fba7` fix(deps): update kotlin monorepo to v2.3.20 (#3755) (renovate[bot], 2026-03-16)
- `228fa0de8a12` fix(deps): update dependency com.gradleup.shadow:shadow-gradle-plugin to v9.4.0 (#3754) (renovate[bot], 2026-03-16)
- `ce3ca085a844` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m17 (#3751) (renovate[bot], 2026-03-15)
- `6b08a9ed7d12` fix(deps): update spring data (#3750) (renovate[bot], 2026-03-14)
- `9923de0a7668` fix(deps): update micronaut.testresources to v4.0.0-M1 (#3724) (renovate[bot], 2026-03-11)
- `1d8840f5a512` fix(deps): update dependency org.projectlombok:lombok to v1.18.44 (#3747) (renovate[bot], 2026-03-11)
- `ba2cc942a13c` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m16 (#3746) (renovate[bot], 2026-03-08)
- `917890554ec8` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m15 (#3741) (renovate[bot], 2026-03-03)
- `594fdf5c1043` fix(deps): update managed.jakarta.data to v1.1.0-m2 (#3716) (renovate[bot], 2026-03-02)
- `de013a8e0d4f` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m14 (#3697) (renovate[bot], 2026-03-02)
- `a8cbf4999fa0` fix(deps): update dependency net.ltgt.errorprone:net.ltgt.errorprone.gradle.plugin to v5.1.0 (#3740) (renovate[bot], 2026-03-02)
- `a6bae699633c` fix(deps): update dependency com.google.errorprone:error_prone_core to v2.48.0 (#3739) (renovate[bot], 2026-03-02)
- `bec97083dca0` fix(deps): update dependency com.gradleup.shadow:shadow-gradle-plugin to v9.3.2 (#3737) (renovate[bot], 2026-02-28)
- `d1c0c945b03e` fix(deps): update dependency org.springframework.boot:spring-boot-gradle-plugin to v4.0.3 (#3731) (renovate[bot], 2026-02-20)
- `5b03a3db3aa9` fix(deps): update dependency io.micronaut.flyway:micronaut-flyway-bom to v8.0.0-m3 (#3732) (renovate[bot], 2026-02-19)
- `7fcae609198e` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to v7.0.0-M7 (#3729) (renovate[bot], 2026-02-19)
- `9265d89ff2e8` fix(deps): update dependency io.micronaut.spring:micronaut-spring-bom to v5.12.1 (#3728) (renovate[bot], 2026-02-18)
- `fd94f59140fa` fix(deps): update dependency com.google.devtools.ksp:symbol-processing-gradle-plugin to v2.3.6 (#3726) (renovate[bot], 2026-02-18)
- `b478fc7feb55` fix(deps): update dependency io.micronaut.logging:micronaut-logging-bom to v2.0.0-m2 (#3727) (renovate[bot], 2026-02-18)
- `49a9308e47b8` fix(deps): update spring data (#3723) (renovate[bot], 2026-02-14)
- `b8d80bb5b4bf` Resolve failures (Andriy Dmytruk, 2026-02-10)
- `38ed0ba73ed8` fix(deps): update dependency io.micronaut.azure:micronaut-azure-cosmos to v5.13.0 (#3717) (renovate[bot], 2026-02-09)
- `88a16d567c02` fix(deps): update dependency io.micronaut.r2dbc:micronaut-r2dbc-bom to v7.0.0 (#3715) (renovate[bot], 2026-02-07)
- `13804f3b0063` fix(deps): update dependency com.google.errorprone:error_prone_core to v2.47.0 (#3714) (renovate[bot], 2026-02-05)
- `8c76ee246e3f` fix(deps): update kotlin monorepo to v2.3.10 (#3713) (renovate[bot], 2026-02-05)
- `99308b16f850` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.2 (#3711) (renovate[bot], 2026-02-04)
- `b6e564ec2031` fix(deps): update micronaut.testresources to v3.0.0-m5 (#3710) (renovate[bot], 2026-02-03)
- `7668e8e55cae` fix(deps): update dependency com.uber.nullaway:nullaway to v0.13.1 (#3703) (renovate[bot], 2026-01-29)
- `260df07f2aa3` fix(deps): update dependency net.ltgt.errorprone:net.ltgt.errorprone.gradle.plugin to v5 (#3706) (renovate[bot], 2026-01-29)
- `ff9a05a8be2c` fix(deps): update dependency com.google.devtools.ksp:symbol-processing-gradle-plugin to v2.3.5 (#3704) (renovate[bot], 2026-01-29)
- `3ea6412559d6` fix(deps): update micronaut.testresources to v3.0.0-m4 (#3701) (renovate[bot], 2026-01-27)
- `deeb121a91b5` fix(deps): update micronaut.testresources to v3.0.0-m3 (#3695) (renovate[bot], 2026-01-23)
- `b5dfd4cd8562` fix(deps): update dependency org.springframework.boot:spring-boot-gradle-plugin to v4.0.2 (#3694) (renovate[bot], 2026-01-23)
- `26e4fbb05e39` fix(deps): update dependency org.apache.groovy:groovy-dateutil to v5.0.4 (#3693) (renovate[bot], 2026-01-22)
- `0ba6fda13357` fix(deps): update dependency com.uber.nullaway:nullaway to v0.13.0 (#3691) (renovate[bot], 2026-01-21)
- `9c3ae4b1642c` fix(deps): update dependency com.google.errorprone:error_prone_core to v2.46.0 (#3677) (renovate[bot], 2026-01-19)
- `21505675bcfd` resolve merge conflict (Dimitrije Zdravkovic, 2026-01-19)
- `b96833e8c640` fix(deps): update spring data (#3689) (renovate[bot], 2026-01-17)
- `639ecf40d910` fix(deps): update micronaut.testresources to v3.0.0-m2 (#3685) (renovate[bot], 2026-01-15)
- `6ba8fd566d79` fix(deps): update dependency net.ltgt.errorprone:net.ltgt.errorprone.gradle.plugin to v4.4.0 (#3686) (renovate[bot], 2026-01-15)
- `7e3485ba7d93` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m2 (#3684) (renovate[bot], 2026-01-14)
- `1aadf3b12d13` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m8 (#3680) (renovate[bot], 2026-01-13)
- `f1fc3bac8e7f` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m7 (#3676) (renovate[bot], 2026-01-11)
- `2429f09966dc` fix(deps): update dependency com.gradleup.shadow:shadow-gradle-plugin to v9.3.1 (#3673) (renovate[bot], 2026-01-07)
- `0d7aaca7123c` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m6 (#3658) (renovate[bot], 2025-12-23)
- `6514f398a264` fix(deps): update dependency org.springframework.boot:spring-boot-gradle-plugin to v4.0.1 (#3654) (renovate[bot], 2025-12-21)
- `92351ab59d51` fix(deps): update dependency com.google.devtools.ksp:symbol-processing-gradle-plugin to v2.3.4 (#3652) (renovate[bot], 2025-12-20)
- `f3abe40db871` fix(deps): update dependency org.apache.groovy:groovy-dateutil to v5.0.3 (#3645) (renovate[bot], 2025-12-18)
- `406ca2a58e4d` fix(deps): update dependency io.micronaut.coherence:micronaut-coherence-bom to v5.1.0 (renovate[bot], 2025-12-18)
- `b19c39a5f308` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m5 (#3644) (renovate[bot], 2025-12-18)
- `5b4f9e133e98` fix(deps): update kotlin monorepo to v2.3.0 (renovate[bot], 2025-12-17)
- `5db28c203d56` fix(deps): update spring data (#3640) (renovate[bot], 2025-12-13)
- `d71c25cfc959` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.10 (#3638) (renovate[bot], 2025-12-12)
- `8da715c44a6b` fix(deps): update dependency com.gradleup.shadow:shadow-gradle-plugin to v9.3.0 (renovate[bot], 2025-12-05)
- `14dccac45d75` resolve merge conflict (Dimitrije Zdravkovic, 2025-12-01)
- `1e6a089f40a7` Resolve Sonar warning (radovanradic, 2025-11-29)
- `b34bf0002d67` Resolve Sonar warning (radovanradic, 2025-11-29)
- `d57d6d6ae770` Resolve Sonar warning (radovanradic, 2025-11-29)
- `4107bd5d5a87` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#3618) (renovate[bot], 2025-11-25)
- `d17496d5e616` fix(deps): update dependency org.springframework.boot:spring-boot-gradle-plugin to v4 (renovate[bot], 2025-11-21)
- `6aa32297334d` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to v7.0.0 (renovate[bot], 2025-11-21)
- `28df96100905` fix(deps): update dependency com.google.devtools.ksp:symbol-processing-gradle-plugin to v2.3.3 (#3613) (renovate[bot], 2025-11-21)
- `024920c49902` fix(deps): update dependency org.springframework.boot:spring-boot-gradle-plugin to v3.5.8 (#3612) (renovate[bot], 2025-11-20)
- `b74e1abca5dd` fix(deps): update spring data to v4 (renovate[bot], 2025-11-14)
- `2be9c3cbcc81` fix(deps): update spring data (renovate[bot], 2025-11-14)
- `e040d8631987` fix(deps): update dependency io.micronaut.r2dbc:micronaut-r2dbc-bom to v7 (renovate[bot], 2025-11-13)
- `6a6384617d6b` fix(deps): update dependency io.micronaut.mongodb:micronaut-mongo-bom to v6 (renovate[bot], 2025-11-12)
- `3ff230a6fe65` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#3600) (renovate[bot], 2025-11-11)
- `d3b59d567cf6` fix(deps): update dependency com.google.devtools.ksp:symbol-processing-gradle-plugin to v2.3.2 (renovate[bot], 2025-11-10)
- `7e7ec67df501` fix(deps): update dependency io.projectreactor.netty:reactor-netty-http to v1.3.0 (renovate[bot], 2025-11-10)
- `9be27759afe3` fix(deps): update dependency org.springframework.data:spring-data-bom to v2025 (#3589) (renovate[bot], 2025-11-10)
- `b75f6870947e` fix(deps): update dependency io.micronaut.flyway:micronaut-flyway-bom to v7.9.2 (#3585) (renovate[bot], 2025-11-10)
- `1d5472aed33a` fix(deps): update kotlin monorepo to v2.2.21 (#3588) (renovate[bot], 2025-11-08)
- `89a5ec3bf1d2` fix(deps): update dependency org.springframework.boot:spring-boot-gradle-plugin to v3.5.7 (#3584) (renovate[bot], 2025-11-07)
- `65fcee906d00` fix(deps): update spring data (#3565) (renovate[bot], 2025-11-05)
- `c05189fbb609` fix(deps): update dependency org.apache.groovy:groovy-dateutil to v4.0.29 (#3580) (renovate[bot], 2025-11-05)
- `3efbf535f261` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.6 (#3563) (renovate[bot], 2025-10-17)
- `3628f3ce7ba4` fix(deps): update dependency com.google.devtools.ksp:symbol-processing-gradle-plugin to v2 (#3473) (renovate[bot], 2025-10-16)

### Security

- `34eef42e5e72` Disable ossIndexAudit check for CVE (Radovan Radic, 2025-11-10)

### Dependency Updates

- `c707767e7790` Update Micronaut dependencies (#3867) (renovate[bot], 2026-05-18)
- `0ea910634bdf` chore: Bump version to 5.0.1-SNAPSHOT (micronaut-build, 2026-05-18)
- `b201b93d7b23` Update Micronaut dependencies (#3864) (renovate[bot], 2026-05-15)
- `f7e339a6f314` Update dependency com.google.devtools.ksp:symbol-processing-gradle-plugin to v2.3.8 (#3862) (renovate[bot], 2026-05-14)
- `7e6f337ca527` Update Micronaut dependencies (#3857) (renovate[bot], 2026-05-11)
- `c9f9aeb7a884` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-05-08)
- `06ef9dbf10ef` Update Micronaut dependencies (#3838) (renovate[bot], 2026-05-06)
- `3543c77519ec` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-05-01)
- `45539aea9df0` Fix existence-aware SQL readers to preserve configured conversion service (#3840) (Radovan Radic, 2026-04-29)
- `18edeacf7cc9` Update dependency io.micronaut:micronaut-core-bom to v5.0.0-M25 (#3836) (renovate[bot], 2026-04-28)
- `1d1315df4ded` Update Micronaut dependencies (#3828) (renovate[bot], 2026-04-24)
- `54f53d30d1a3` Update dependency org.springframework.boot:spring-boot-gradle-plugin to v4.0.6 (#3825) (renovate[bot], 2026-04-23)
- `91643d42c563` Update dependency org.projectlombok:lombok to v1.18.46 (#3823) (renovate[bot], 2026-04-23)
- `b1e202c34bae` Update dependency com.google.devtools.ksp:symbol-processing-gradle-plugin to v2.3.7 (#3822) (renovate[bot], 2026-04-23)
- `0be983a49db6` Update dependency com.uber.nullaway:nullaway to v0.13.4 (#3809) (renovate[bot], 2026-04-23)
- `49d54394acfd` Update Micronaut dependencies (#3819) (renovate[bot], 2026-04-23)
- `8a22e51b47ca` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-04-21)
- `b30ec6706654` chore(deps): update softprops/action-gh-release action to v2.6.2 (#3808) (renovate[bot], 2026-04-17)
- `7651beba3beb` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-03-23)
- `414c73ebcab4` chore(deps): update gradle to v9.4.1 (#3765) (renovate[bot], 2026-03-20)
- `40ab8bb11a4d` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-03-19)
- `ed4d8ef53650` chore(deps): update softprops/action-gh-release action to v2.6.1 (#3753) (renovate[bot], 2026-03-16)
- `6f13c3e49252` chore(deps): update actions/download-artifact action to v8.0.1 (#3749) (renovate[bot], 2026-03-13)
- `29fe9fd8ec1a` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-03-11)
- `b6982df93c73` chore(deps): update gradle to v9.4.0 (#3745) (renovate[bot], 2026-03-09)
- `0232ddbdd511` chore(deps): update github artifact actions (#3734) (renovate[bot], 2026-02-27)
- `e3a27d974a6d` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-02-19)
- `634be2e3524c` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#3725) (renovate[bot], 2026-02-17)
- `78555c021d08` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m16 (#3720) (renovate[bot], 2026-02-10)
- `2b564d99738a` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m15 (#3709) (renovate[bot], 2026-02-02)
- `22d2f595a1ea` chore(deps): update gradle to v9.3.1 (#3707) (renovate[bot], 2026-01-30)
- `67aa7f3f3e42` chore(deps): update gradle to v9.3.0 (#3690) (renovate[bot], 2026-01-21)
- `42702df8f599` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m14 (#3675) (renovate[bot], 2026-01-10)
- `7b27e44c5ada` chore(deps): update graalvm/setup-graalvm action to v1.4.5 (#3671) (renovate[bot], 2026-01-06)
- `df60cc82d3fe` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2025-12-30)
- `238f7dcd7b78` chore(deps): update actions/checkout action to v6.0.1 (#3617) (renovate[bot], 2025-12-23)
- `13c3a6a376a7` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m13 (#3643) (renovate[bot], 2025-12-18)
- `11fa2f9a2014` chore(deps): update graalvm/setup-graalvm action to v1.4.4 (#3631) (renovate[bot], 2025-12-03)
- `4629b17abcdb` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#3630) (renovate[bot], 2025-12-02)
- `fedaff99ea00` chore(deps): update graalvm/setup-graalvm action to v1.4.4 (#3631) (renovate[bot], 2025-12-03)
- `519dbe8ec878` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#3630) (renovate[bot], 2025-12-02)
- `073b2dbb68ef` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m11 (#3624) (renovate[bot], 2025-11-27)
- `f354995a2bfe` chore(deps): update graalvm/setup-graalvm action to v1.4.3 (#3623) (renovate[bot], 2025-11-27)
- `da99dc5d505f` Fix spring boot dependencies and update spring mongodb uri (radovanradic, 2025-11-21)
- `498700edb82e` chore(deps): update gradle to v9.2.1 (#3611) (renovate[bot], 2025-11-20)
- `39a1b6193b17` Merge pull request #3593 from micronaut-projects/update-deps (Radovan Radic, 2025-11-14)
- `8065a80daef8` Merge remote-tracking branch 'origin/5.0.x' into update-deps (radovanradic, 2025-11-13)
- `6cf20bd7e990` Merge remote-tracking branch 'origin/5.0.x' into update-deps (radovanradic, 2025-11-13)
- `f1f0c521c631` Merge remote-tracking branch 'origin/5.0.x' into update-deps (radovanradic, 2025-11-12)
- `abc31a811131` chore(deps): update mikepenz/action-junit-report action to v6 (renovate[bot], 2025-11-10)
- `895ce49d064c` chore(deps): update github artifact actions (renovate[bot], 2025-11-10)
- `5a0b64c17911` Merge remote-tracking branch 'origin/5.0.x' into update-deps (radovanradic, 2025-11-10)
- `7fe6c6a13192` Update micronaut-flyway version to 7.9.2 (Radovan Radic, 2025-11-10)
- `251eaead5fa5` Update mongo module to the latest version and fix H2 datetime column (radovanradic, 2025-11-10)
- `eb1fd127bbbc` chore(deps): update gradle to v9.2.0 (#3591) (renovate[bot], 2025-11-10)
- `53a6aa7f325f` Hibernate7 upgrade (#3587) (Radovan Radic, 2025-11-10)
- `e5fe9b515d40` chore(deps): update softprops/action-gh-release action to v2.4.2 (#3590) (renovate[bot], 2025-11-09)
- `9755c9378674` chore: Bump version to 4.14.2-SNAPSHOT (micronaut-build, 2025-11-06)
- `b92147b1150e` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m9 (#3576) (renovate[bot], 2025-11-04)
- `05a34d217dbe` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#3575) (renovate[bot], 2025-11-04)
- `08190b642c3b` chore(deps): update softprops/action-gh-release action to v2.4.1 (#3556) (renovate[bot], 2025-10-16)

### Documentation

- `edb486c0a9d8` Docs: update micronaut-docs to 3.0.0 (#3553) (issam liqali, 2025-10-16)

### Internal

- `ddc7aeb26a2d` ci: projectVersion=5.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2024-04-09)

### Review Candidates

- `56c975daa56c` Fix Jackson duality view review issues (#3866) (Graeme Rocher, 2026-05-19)
- `cd2fed976920` Update common files (#3869) (micronaut-build, 2026-05-19)
- `e2e32c4f88bc` [skip ci] Release v5.0.0 (micronaut-build, 2026-05-18)
- `ec596abbc0e3` Vector type support (#3637) (Nemanja Mikic, 2026-05-18)
- `9bbec73d5a4e` micronaut-flyway = "8.0.0" (Sergio del Amo, 2026-05-18)
- `e23623b29d92` GeoSpatial predicates implementation (#3863) (Milenko Supic, 2026-05-18)
- `5f27879452a3` micronaut-sql = "7.0.1" (Sergio del Amo, 2026-05-18)
- `fa96282ae4f2` micronaut-mongo = "6.0.1" (Sergio del Amo, 2026-05-14)
- `1fbfa88f5918` micronaut-test = "5.0.0" (Sergio del Amo, 2026-05-14)
- `189a05422943` Update Micronaut build plugin (#3858) (renovate[bot], 2026-05-14)
- `c3d89f08ef41` Update versions (Sergio del Amo, 2026-05-14)
- `1875d7629352` micronaut-platform = "5.0.0-RC1" (Sergio del Amo, 2026-05-13)
- `9eb292533564` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `25c014ddb70d` Update Gradle to v9.5.1 (#3861) (renovate[bot], 2026-05-13)
- `bd651d739d89` Make save to choose between insert and update based on entity identity (Denis Stepanov, 2026-05-12)
- `4669bbd30c44` Fix executor lifecycle ownership in repository operations (#3847) (Radovan Radic, 2026-05-11)
- `df132ed565c8` Update groovy monorepo to v5.0.6 (#3856) (renovate[bot], 2026-05-11)
- `959ed234e051` Update common files (#3855) (micronaut-build, 2026-05-09)
- `f9ceddf4a859` Update common files (#3853) (micronaut-build, 2026-05-08)
- `bee27ddce0a9` [skip ci] Release v5.0.0-RC1 (micronaut-build, 2026-05-08)
- `e5688ad8b25f` git ignore .kotlin (Sergio del Amo, 2026-05-07)
- `6662f51a0144` update versions (Sergio del Amo, 2026-05-07)
- `2701391107ba` Update common files (#3848) (micronaut-build, 2026-05-07)
- `0d0d6f64cd3a` [data] Update common files for branch 5.0.x (#3843) (micronaut-build, 2026-05-05)
- `dd6b29b78d25` [skip ci] Release v5.0.0-M7 (micronaut-build, 2026-05-01)
- `fab7def63560` [data] Update common files for branch 5.0.x (#3842) (micronaut-build, 2026-05-01)
- `07a05e2f39b2` Update Gradle to v9.5.0 (#3841) (renovate[bot], 2026-04-30)
- `a2bbff1fa1bd` Merge pull request #3839 from micronaut-projects/merge-from-4x (Denis Stepanov, 2026-04-30)
- `ab8219848051` Update data-tx-jdbc/src/test/groovy/io/micronaut/transaction/jdbc/NestedTransactionSpec.groovy (Radovan Radic, 2026-04-29)
- `21504a1fcd69` Merge remote-tracking branch 'origin/5.0.x' into merge-from-4x (radovanradic, 2026-04-29)
- `4fc4b8a56657` Fix formatting and tests (radovanradic, 2026-04-29)
- `dbf51ba05714` Fix doRollbackOnCommitException dispatching to wrong rollback method (Marius Volkhart, 2026-02-25)
- `21bc6c786b91` Fix NESTED propagation not creating JDBC savepoints (#3334) (Marius Volkhart, 2026-02-24)
- `632174f20f05` Update common files (#3826) (micronaut-build, 2026-04-29)
- `6ce04303ceab` replace rxjava2 with rxjava3 (#3832) (Sergio del Amo, 2026-04-29)
- `1579d7fb1a50` Fix async over reactive specifications (#3834) (Denis Stepanov, 2026-04-28)
- `60576ef9fd90` GeoSpatial - CRUD Implementation (#3792) (Milenko Supic, 2026-04-28)
- `8547319ecd61` Rename Jakarta Data Query to Jakarta Query  (#3833) (Denis Stepanov, 2026-04-28)
- `5a23c366b9a5` AUTO_INCREMENT is MySQL/MariaDB only (#3827) (Sergio del Amo, 2026-04-24)
- `f869e208b199` Allow @AutoPopulated fields to preserve supplied values (#3721) (Radovan Radic, 2026-04-24)
- `43d82fe3edf2` Update kotlin monorepo to v2.3.21 (#3824) (renovate[bot], 2026-04-23)
- `dd19f9cf22cf` [data] Update common files for branch 5.0.x (#3817) (micronaut-build, 2026-04-22)
- `59987872a325` [skip ci] Release v5.0.0-M6 (micronaut-build, 2026-04-21)
- `ee7004449e4a` Update to latest (#3816) (Sergio del Amo, 2026-04-21)
- `d794d3fa5d9a` Experiment with renovate groups (#3815) (Denis Stepanov, 2026-04-21)
- `b424613b0936` Update common files (#3798) (micronaut-build, 2026-04-20)
- `f778ab10b596` Fix insert/update/delete returning Optional (#3805) (Radovan Radic, 2026-04-15)
- `7e25eba9ca7f` Jakarta Data M3 (#3800) (Denis Stepanov, 2026-04-15)
- `e0bbdb63ae14` Oracle Test Pilot integration phase 2 (#3799) (Loïc LEFEVRE, 2026-04-10)
- `3e928b8fbc02` Update SQL reference to use 'dbc' instead of 'sql' (#3788) (Mohammed CHBANI, 2026-04-01)
- `9fb058523ade` Oracle Test Pilot integration phase 1 (#3781) (Loïc LEFEVRE, 2026-03-30)
- `d9032c56b3e1` Using Criteria with Pageable containing sort ignore case is failing (#3559) (Radovan Radic, 2026-03-26)
- `cda4e2674d25` Update common files (#3776) (micronaut-build, 2026-03-25)
- `94c0f52f53c7` [skip ci] Release v5.0.0-M5 (micronaut-build, 2026-03-23)
- `fd756ad05032` Test for retrieval of single column of type byte array and fix for R2dbc (#3766) (Radovan Radic, 2026-03-23)
- `2da23a604b83` Update common files (#3744) (micronaut-build, 2026-03-23)
- `f3eccd1e30f5` Fixed creating of database index when @Index used in embedded entities (#3764) (Milenko Supic, 2026-03-20)
- `3c1e601efa92` [skip ci] Release v5.0.0-M4 (micronaut-build, 2026-03-19)
- `81edeac2fc18` Update to micronaut-sql (jakarta persistence 3.2.0) (#3759) (Radovan Radic, 2026-03-19)
- `370017c279f4` [skip ci] Release v5.0.0-M3 (micronaut-build, 2026-03-11)
- `ce66db7e318d` Update MethodMatcher loading with class loader (#3748) (Graeme Rocher, 2026-03-11)
- `7752a3d7451e` Added mapping between Java time types and Oracle database INTERVAL types (#3626) (Milenko Supic, 2026-03-03)
- `f1b88c1e6ad0` Update common files (#3738) (micronaut-build, 2026-03-03)
- `8fc174bb8b4e` [skip ci] Release v5.0.0-M2 (micronaut-build, 2026-02-19)
- `2d638477f60d` Merge pull request #3632 from ZdravDimOracle/Dimitrije/json-view-sql (Andriy Dmytruk, 2026-02-11)
- `166da9702f62` Mark failing test with pending feature and explanation (Andriy Dmytruk, 2026-02-11)
- `3de51b33df53` Revert "Add Relation.unique property to mark relations that should not be repeated" (Andriy Dmytruk, 2026-02-11)
- `4afd3bdc03c2` Merge branch '5.0.x' into Dimitrije/json-view-sql (Andriy Dmytruk, 2026-02-10)
- `b35483468264` Do not add delete operation for StudentSubView as it cannot be deleted recursively (Andriy Dmytruk, 2026-02-09)
- `4083a235b91e` Fix column naming strategy for embedded fields (for next major version) (#3410) (Radovan Radic, 2026-02-10)
- `021b460a29c7` Fix delete matcher (#3719) (Radovan Radic, 2026-02-10)
- `de2b8553d1e6` Merge recent 4.14.x changes (#3700) (Radovan Radic, 2026-02-10)
- `1d611bac8b9b` revert table_name (Dimitrije Zdravkovic, 2026-02-10)
- `94b25606f799` Merge remote-tracking branch 'ZdravDim/Dimitrije/json-view-sql' into Dimitrije/json-view-sql (Andriy Dmytruk, 2026-02-09)
- `f8f29dae1dfe` Fix handling of Kind.Embedded associations with JsonViews (Andriy Dmytruk, 2026-02-06)
- `da1d5dafff65` Revert to use embedded entity address (Andriy Dmytruk, 2026-02-06)
- `c27e16081abc` Merge branch 'refs/heads/5.0.x' into Dimitrije/json-view-sql (Andriy Dmytruk, 2026-02-06)
- `aa8bc07b7528` Merge branch 'Dimitrije/json-view-sql' of https://github.com/ZdravDimOracle/micronaut-data into Dimitrije/json-view-sql (Dimitrije Zdravkovic, 2026-02-05)
- `0eeabe6e1695` Merge branch '5.0.x' of https://github.com/micronaut-projects/micronaut-data into Dimitrije/json-view-sql (Dimitrije Zdravkovic, 2026-02-05)
- `530cfdd51bd7` merge branch '5.0.x' of https://github.com/micronaut-projects/micronaut-data into Dimitrije/json-view-sql (Dimitrije Zdravkovic, 2026-02-05)
- `6a2177302507` Update common files (#3712) (micronaut-build, 2026-02-05)
- `2bf248a4f767` Merge branch '5.0.x' of https://github.com/micronaut-projects/micronaut-data into Dimitrije/json-view-sql (Dimitrije Zdravkovic, 2026-02-04)
- `ee058e2468b4` Improve MappedEntityVisitor changes to resolve the build errors (Andriy Dmytruk, 2026-02-04)
- `8388c59a91ea` fix checkstyle (Dimitrije Zdravkovic, 2026-02-03)
- `522f3cd635d6` merge (Dimitrije Zdravkovic, 2026-02-03)
- `84aa3d616a0b` Update common files (#3708) (micronaut-build, 2026-02-02)
- `ea965e42ed56` [data] Update common files for branch 5.0.x (#3705) (micronaut-build, 2026-01-29)
- `cbf18dcc182b` feature/issue-3619-kotlin-coroutine-null-value-5.0.x into 5.0.x (#3657) (stevenlmcgraw, 2026-01-23)
- `d4d867e2d63c` fix function naming (Dimitrije Zdravkovic, 2026-01-21)
- `778b1a7ef7e2` throw exceptions instead of just returning (Dimitrije Zdravkovic, 2026-01-21)
- `c0b7c4848288` update docs (Dimitrije Zdravkovic, 2026-01-21)
- `fbbb4fb53147` fix join table primary keys (Dimitrije Zdravkovic, 2026-01-20)
- `302d941e6f53` fix join table primary keys (Dimitrije Zdravkovic, 2026-01-20)
- `e500a4f87301` fix checkstyle errors (Dimitrije Zdravkovic, 2026-01-19)
- `9b8c2f03830f` fix checkstyle errors (Dimitrije Zdravkovic, 2026-01-19)
- `bda36a079c90` fix @Nullable errors (Dimitrije Zdravkovic, 2026-01-19)
- `cf048d6a1989` Update common files (#3670) (micronaut-build, 2026-01-15)
- `7148fee6d82d` Merge 4.14.x recent changes into 5.0.x (#3682) (Radovan Radic, 2026-01-13)
- `130df461e321` Eliminate more NonNull (#3672) (Denis Stepanov, 2026-01-07)
- `96be9a92a551` Update updates.adoc (#3633) (Jorge, 2025-12-31)
- `16db11f2f39d` Merge branch '5.0.x' of https://github.com/micronaut-projects/micronaut-data into Dimitrije/json-view-sql (Dimitrije Zdravkovic, 2025-12-31)
- `1902c1ea629e` [data] Update common files for branch 5.0.x (#3666) (micronaut-build, 2025-12-31)
- `0fe2d3555667` [skip ci] Release v5.0.0-M1 (micronaut-build, 2025-12-30)
- `34810a65b94b` fix composite ids (Dimitrije Zdravkovic, 2025-12-30)
- `e50dc49daec0` [data] Update common files for branch 5.0.x (#3664) (micronaut-build, 2025-12-25)
- `7b0e2613008d` fix many to many joins (Dimitrije Zdravkovic, 2025-12-23)
- `66597308e47f` Fix azure cosmos jackson serde (#3650) (Radovan Radic, 2025-12-22)
- `aa5f6dd10b3d` update documentation (Dimitrije Zdravkovic, 2025-12-22)
- `b52cbe694ea0` Fix Javadoc warnings (#3656) (Denis Stepanov, 2025-12-22)
- `537be63eebfc` Merge pull request #3653 from micronaut-projects/sync-files-5.0.x (Radovan Radic, 2025-12-22)
- `0361cafb929a` Merge pull request #3655 from micronaut-projects/cursored-pageable-suspend (Radovan Radic, 2025-12-22)
- `19e40b02f2d1` Update mongo (radovanradic, 2025-12-22)
- `a38eddb9c99e` Merge remote-tracking branch 'origin/5.0.x' into cursored-pageable-suspend (radovanradic, 2025-12-22)
- `a5327403fc5a` Update common files (micronaut-build, 2025-12-22)
- `3c7b4a3fde46` Merge remote-tracking branch 'origin/5.0.x' into cursored-pageable-suspend (radovanradic, 2025-12-21)
- `98fe4cf90c17` Investigate cursored pageable issue (radovanradic, 2025-12-21)
- `a2390ad144cf` Investigate cursored pageable issue (radovanradic, 2025-12-20)
- `a40e406a4e89` Investigate cursored pageable issue (radovanradic, 2025-12-20)
- `095e0e18d5c2` Investigate cursored pageable issue (radovanradic, 2025-12-19)
- `da699556b925` Investigate cursored pageable issue (radovanradic, 2025-12-19)
- `a9e7b1aaccd4` Investigate cursored pageable issue (radovanradic, 2025-12-19)
- `3b5271b4ed7e` Update src/main/docs/guide/dbc/sqlMapping/sqlJsonView.adoc (Dimitrije Zdravkovic, 2025-12-19)
- `be7f2e61afab` merge conflict (Dimitrije Zdravkovic, 2025-12-19)
- `2886a03d3a6c` Jakarta Data - correct recognition of the root entity (#3651) (Denis Stepanov, 2025-12-19)
- `df17e5553a6a` Jspecify - Use NullMarked (#3648) (Denis Stepanov, 2025-12-19)
- `65f59b7d1597` Merge pull request #3646 from micronaut-projects/renovate/kotlin-monorepo (Radovan Radic, 2025-12-19)
- `63af105ffd3d` Merge pull request #3635 from micronaut-projects/renovate/shadow.gradle.plugin (Radovan Radic, 2025-12-19)
- `b6cdccf34c49` Merge pull request #3647 from micronaut-projects/renovate/micronaut.coherence (Radovan Radic, 2025-12-19)
- `70f24007f6e7` Update micronaut-coherence version (Radovan Radic, 2025-12-19)
- `70c30dd9de2e` update documentation (Dimitrije Zdravkovic, 2025-12-18)
- `a13e3b675884` Jspecify (#3642) (Denis Stepanov, 2025-12-18)
- `68a718221fc6` Coherence tests now can have netty runtime (radovanradic, 2025-12-18)
- `92fbad0a1e87` Update to micronaut 5 (#3627) (Radovan Radic, 2025-12-17)
- `4ef3376c2a1b` revert Address.java (Dimitrije Zdravkovic, 2025-12-16)
- `dd4886252b42` check schema configured (Dimitrije Zdravkovic, 2025-12-15)
- `c24f6593c6b8` forgot to revert (Dimitrije Zdravkovic, 2025-12-13)
- `f728b2adab21` merge conflict and pr iteration (Dimitrije Zdravkovic, 2025-12-13)
- `ec07df07c98d` Merge pull request #3639 from micronaut-projects/merge-414x (Denis Stepanov, 2025-12-12)
- `84e13ee43455` Merge remote-tracking branch 'origin/4.14.x' into merge-414x (radovanradic, 2025-12-12)
- `8dd8f5154b4e` log error instead of throwing (Dimitrije Zdravkovic, 2025-12-11)
- `07be2a8e7007` Polish out code (Dimitrije Zdravkovic, 2025-12-10)
- `9dbfa427e4d7` update documentation (Dimitrije Zdravkovic, 2025-12-10)
- `03b349e9f574` update documentation (Dimitrije Zdravkovic, 2025-12-09)
- `0ec44d3cc194` pr iteration (Dimitrije Zdravkovic, 2025-12-08)
- `d308babd39d2` fix style check (Dimitrije Zdravkovic, 2025-12-05)
- `5be6228afd31` generate sql create json view statement (Dimitrije Zdravkovic, 2025-12-01)
- `c10889df68b0` Merge pull request #3607 from micronaut-projects/date-embedded (Radovan Radic, 2025-12-01)
- `3bc60e774986` Merge remote-tracking branch 'origin/4.14.x' into date-embedded (radovanradic, 2025-11-29)
- `fcb788871e69` Reduce code duplication (radovanradic, 2025-11-29)
- `c897dd2ac8fc` Jakarta Data 1.1 M1 Support stateful annotations (#3625) (Denis Stepanov, 2025-11-27)
- `2a102a49e8e7` Merge pull request #3622 from micronaut-projects/skip-javadoc-tests (Radovan Radic, 2025-11-26)
- `5745698acdd4` Skip javadoc for io/micronaut/data/tck/tests/AbstractJakartaDataTest.java (radovanradic, 2025-11-26)
- `b38610019018` Merge pull request #3606 from micronaut-projects/renovate/major-spring-data (Radovan Radic, 2025-11-25)
- `97299e017f90` Merge remote-tracking branch 'origin/5.0.x' into renovate/major-spring-data (radovanradic, 2025-11-25)
- `a51df1b06bd3` No longer propagate synchronous transaction / connection by default (#3615) (Denis Stepanov, 2025-11-25)
- `4f77f162d793` Jakarta Data 1.1 M1 (#3610) (Denis Stepanov, 2025-11-25)
- `cef873fec84a` Catch exception when there is no default constructor for embedded entity with auto populate fields (radovanradic, 2025-11-24)
- `7a216d2700e6` Minor improvements and test with inner embeddable as record (radovanradic, 2025-11-24)
- `5bda1fedfd0e` Minor reusability improvement (radovanradic, 2025-11-24)
- `a5ddb3778467` Handle recursively embedded fields (radovanradic, 2025-11-24)
- `75f0fcc12a0e` Merge remote-tracking branch 'origin/5.0.x' into renovate/major-spring-data (radovanradic, 2025-11-21)
- `a7e2695dd87f` Merge pull request #3614 from micronaut-projects/renovate/major-spring-boot (Radovan Radic, 2025-11-21)
- `dd2ca909ef8e` Merge branch '5.0.x' into renovate/major-spring-boot (Radovan Radic, 2025-11-21)
- `6a8a715637c5` Merge pull request #3605 from micronaut-projects/renovate/spring-data (Radovan Radic, 2025-11-21)
- `4370a086dc52` Merge pull request #3586 from micronaut-projects/renovate/micronaut.sql (Radovan Radic, 2025-11-21)
- `431c4bdadf54` Update to micronaut-sql milestone 7.0.0-M4 (radovanradic, 2025-11-21)
- `374a1a714520` Merge pull request #3609 from micronaut-projects/paginate-embeddedid (Radovan Radic, 2025-11-20)
- `7ae8a912b6d5` Trigger build (radovanradic, 2025-11-18)
- `736287bdc581` Fix pagination with EmbeddedId criteria (radovanradic, 2025-11-18)
- `b154ce38d60d` Revert change in DefaultRuntimeEntityRegistry (radovanradic, 2025-11-17)
- `6559fffca103` Try to avoid recursive update error with DefaultRuntimeEntityRegistry entities concurrent hash map (radovanradic, 2025-11-17)
- `c031e1cbee11` Fix auto population of UUID fields when embedded. (radovanradic, 2025-11-16)
- `826649457991` Fix auto population of timestamp fields when embedded. (radovanradic, 2025-11-16)
- `0f67cc934ae0` Fix build for benchmark spring modules (radovanradic, 2025-11-14)
- `dcead9fbe859` Simplify changes to match spring 4 changes (radovanradic, 2025-11-14)
- `af034927eed1` Fix build after spring changes (radovanradic, 2025-11-14)
- `a18abad463b3` Update spring boot plugin (radovanradic, 2025-11-14)
- `d37c7b636cfc` generate sql create json view statement (Dimitrije Zdravkovic, 2025-11-14)
- `895779788b5a` Changes for spring-jpa 4 (radovanradic, 2025-11-14)
- `7f65c16281b0` Merge pull request #3604 from micronaut-projects/renovate/major-micronaut.r2dbc (Radovan Radic, 2025-11-13)
- `d058552b4d6a` Use micronaut-r2dbc release version (radovanradic, 2025-11-13)
- `b8a8c7e13072` Merge pull request #3603 from micronaut-projects/renovate/major-micronaut.mongo (Radovan Radic, 2025-11-13)
- `06d4199dc1f9` Enable SharedArenaSupport for GraalVM 25 (radovanradic, 2025-11-12)
- `8e9ceaf8473b` Try enabling graalvm 25 (radovanradic, 2025-11-12)
- `5a56a8ff94ba` Merge pull request #3594 from micronaut-projects/renovate/ksp-monorepo (Radovan Radic, 2025-11-10)
- `964a6134d3c5` Merge pull request #3595 from micronaut-projects/renovate/io.projectreactor.netty-reactor-netty-http-1.x (Radovan Radic, 2025-11-10)
- `d3aa7996d272` Merge pull request #3597 from micronaut-projects/renovate/mikepenz-action-junit-report-6.x (Radovan Radic, 2025-11-10)
- `22f29fb9539a` Merge pull request #3596 from micronaut-projects/renovate/major-github-artifact-actions (Radovan Radic, 2025-11-10)
- `7997b6dc0ac9` Fix checkstyle (radovanradic, 2025-11-10)
- `99cc55a3700a` Merge pull request #3592 from micronaut-projects/merge-4x (Radovan Radic, 2025-11-10)
- `b0b883472307` Configure mongo codes class for native build initialization (radovanradic, 2025-11-10)
- `30796c96b318` Merge branch '5.0.x' into merge-4x (Radovan Radic, 2025-11-10)
- `100236d9c252` Fix failing test (radovanradic, 2025-11-10)
- `4d734c0993fb` Revert mongo upgrade (radovanradic, 2025-11-10)
- `e79f1c46a3fd` Test latest sql and r2dbc modules with micronaut-data (radovanradic, 2025-11-10)
- `4d5849ebc4ba` Merge remote-tracking branch 'origin/5.0.x' into merge-4x (radovanradic, 2025-11-10)
- `24cb7c2f24db` Merge remote-tracking branch 'origin/4.14.x' into merge-4x (radovanradic, 2025-11-10)
- `e0d70540c319` [skip ci] Release v4.14.1 (micronaut-build, 2025-11-06)
- `75d200595543` groovy = "4.0.29" (Sergio del Amo, 2025-11-06)
- `0cfe7c7f2574` micronaut-gradle-plugin = "4.6.1" (Sergio del Amo, 2025-11-06)
- `9e7f8e8dbe06` micronaut-platform = "4.10.1" (Sergio del Amo, 2025-11-06)
- `28cadc672660` micronaut-flyway = "7.9.1" (Sergio del Amo, 2025-11-06)
- `71ec7a7fa1f3` micronaut-validation = "4.12.0" (Sergio del Amo, 2025-11-06)
- `7647fb994d03` micronaut-multitenancy = "5.8.0" (Sergio del Amo, 2025-11-06)
- `49b6111a11c8` micronaut-spring = "5.12.0" (Sergio del Amo, 2025-11-06)
- `cc22fceb96e8` micronaut-test = "4.10.2" (Sergio del Amo, 2025-11-06)
- `2d208fb20a34` micronaut-serde = "2.16.1" (Sergio del Amo, 2025-11-06)
- `cfdae27a8001` micronaut-r2dbc = "6.2.0" (Sergio del Amo, 2025-11-06)
- `b9022079930d` micronaut-rxjava2 = "2.9.0" (Sergio del Amo, 2025-11-06)
- `bb0d8b4189a8` micronaut-reactor = "3.9.1" (Sergio del Amo, 2025-11-06)
- `11f76d3e065d` core 4.10.8 (Sergio del Amo, 2025-11-06)
- `78e5d4007eda` Micronaut build gradle plugin 7.6.6 (Sergio del Amo, 2025-11-06)
- `2c4e97b8cdfa` Micronaut 5 compatibility (#3574) (issam liqali, 2025-11-04)
- `f599c4e9cb12` Update common files (#3564) (micronaut-build, 2025-10-17)
- `e709f26a9075` Update common files (#3550) (micronaut-build, 2025-10-16)
- `2e17d3b47745` Micronatu gradle build plugin 8.0.0-M4 (Sergio del Amo, 2025-10-10)
- `06fb470349a5` gradle 9.1 (Sergio del Amo, 2025-10-10)
- `4d9df94dcbb8` Merge branch '4.14.x' into 5.0.x (Sergio del Amo, 2025-10-10)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` build.gradle
- `M` buildSrc/build.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.data-base.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.data-benchmark.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.data-example.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.data-kotlin-example.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.data-kotlin-ksp-example.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.data-kotlin.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.data-micronaut-benchmark.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.data-module.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.data-native-example.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.data-spring-benchmark.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.data-tck.gradle
- `M` data-azure-cosmos/build.gradle
- `M` data-connection-jdbc/build.gradle
- `M` data-connection/build.gradle
- `M` data-hibernate-jpa/build.gradle
- `M` data-hibernate-reactive/build.gradle
- `M` data-jdbc/build.gradle
- `M` data-jdbc/src/main/java/io/micronaut/data/jdbc/convert/JdbcConversionContext.java
- `A` data-jdbc/src/main/java/io/micronaut/data/jdbc/operations/JdbcDatabaseConversionContextFactory.java
- `M` data-model/build.gradle
- `A` data-model/src/main/java/io/micronaut/data/model/runtime/convert/DatabaseTypeConversionContext.java
- `M` data-mongodb/build.gradle
- `M` data-processor/build.gradle
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jakarta/VersionAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jx/VersionAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/spring/SpringVersionMapper.java
- `M` data-r2dbc/build.gradle
- `M` data-r2dbc/src/main/java/io/micronaut/data/r2dbc/convert/R2dbcConversionContext.java
- `A` data-r2dbc/src/main/java/io/micronaut/data/r2dbc/operations/R2dbcDatabaseConversionContextFactory.java

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
- `M` README.md
- `M` data-document-model/src/main/java/io/micronaut/data/document/model/query/builder/CosmosSqlQueryBuilder.java
- `D` data-document-model/src/main/java/io/micronaut/data/document/model/query/builder/CosmosSqlQueryBuilder2.java
- `M` data-document-model/src/main/java/io/micronaut/data/document/model/query/builder/MongoQueryBuilder.java
- `D` data-document-model/src/main/java/io/micronaut/data/document/model/query/builder/MongoQueryBuilder2.java
- `M` data-document-model/src/main/java/io/micronaut/data/document/mongo/MongoAnnotations.java
- `M` data-document-model/src/main/java/io/micronaut/data/document/serde/defaults/DefaultCustomConverterDeserializer.java
- `M` data-document-model/src/main/java/io/micronaut/data/document/serde/defaults/DefaultCustomConverterSerializer.java
- `M` data-document-processor/src/main/java/io/micronaut/data/document/processor/matchers/MongoExecutorQueryMethodMatcher.java
- `M` data-document-processor/src/main/java/io/micronaut/data/document/processor/matchers/MongoRawQueryMethodMatcher.java
- `M` data-document-processor/src/test/groovy/io/micronaut/data/document/processor/BuildMongoQuerySpec.groovy
- `M` data-document-tck/src/main/groovy/io/micronaut/data/document/tck/AbstractDocumentRepositorySpec.groovy
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/entities/Author.java
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/entities/AuthorBooksDto.java
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/entities/BasicTypes.java
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/entities/Book.java
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/entities/BookDto.java
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/entities/Citizen.java
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/entities/County.java
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/entities/CountyPk.java
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/entities/Customer.java
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/entities/Document.java
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/entities/DomainEvents.java
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/entities/Owner.java
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/entities/Page.java
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/entities/Person.java
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/entities/Pet.java
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/entities/Publisher.java
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/entities/QuantityAttributeConverter.java
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/entities/Restaurant.java
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/entities/Sale.java
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/entities/Settlement.java
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/entities/SettlementPk.java
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/entities/SettlementType.java
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/entities/Shipment.java
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/entities/ShipmentId.java
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/entities/State.java
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/entities/Student.java
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/entities/Zone.java
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/repositories/AuthorRepository.java
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/repositories/BookRepository.java
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/repositories/CitizenRepository.java
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/repositories/PersonRepository.java
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/repositories/SettlementRepository.java
- `M` data-document-tck/src/main/java/io/micronaut/data/document/tck/services/TxEventsService.java
- `M` data-mongodb/src/test/groovy/io/micronaut/data/document/mongodb/MongoCompositeSpec.groovy
- `M` data-mongodb/src/test/groovy/io/micronaut/data/document/mongodb/MongoCriteriaSpec.groovy
- `M` data-mongodb/src/test/groovy/io/micronaut/data/document/mongodb/MongoDocumentRepositorySpec.groovy
- `M` data-mongodb/src/test/groovy/io/micronaut/data/document/mongodb/MongoEmbeddedIdSpec.groovy
- `M` data-mongodb/src/test/groovy/io/micronaut/data/document/mongodb/MongoEmbeddedSpec.groovy
- `M` data-mongodb/src/test/groovy/io/micronaut/data/document/mongodb/MongoEmbeddedSpec2.groovy
- `A` data-mongodb/src/test/groovy/io/micronaut/data/document/mongodb/MongoGeoSpec.groovy
- `M` data-mongodb/src/test/groovy/io/micronaut/data/document/mongodb/MongoIdsSpec.groovy
- `M` data-mongodb/src/test/groovy/io/micronaut/data/document/mongodb/MongoManyToManySpec.groovy
- `M` data-mongodb/src/test/groovy/io/micronaut/data/document/mongodb/MongoRuntimeSpec.groovy
- `M` data-mongodb/src/test/groovy/io/micronaut/data/document/mongodb/reactive/MongoReactiveDocumentRepositorySpec.groovy
- `M` data-mongodb/src/test/groovy/io/micronaut/data/document/mongodb/upsert/SimpleSongSpec.groovy
- `M` data-mongodb/src/test/groovy/io/micronaut/data/document/mongodb/upsert/SimpleSongSpec2.groovy
- `M` data-mongodb/src/test/java/io/micronaut/data/document/mongodb/MongoTestService.java
- `A` data-mongodb/src/test/java/io/micronaut/data/document/mongodb/entities/GeoEntity.java
- `M` data-mongodb/src/test/java/io/micronaut/data/document/mongodb/repositories/MongoBookRepository.java
- `A` data-mongodb/src/test/java/io/micronaut/data/document/mongodb/repositories/MongoGeoEntityRepository.java
- `M` data-mongodb/src/test/java/io/micronaut/data/document/mongodb/repositories/MongoOwnerRepository.java
- `M` data-mongodb/src/test/java/io/micronaut/data/document/mongodb/repositories/MongoPersonRepository.java
- `M` data-mongodb/src/test/java/io/micronaut/data/document/mongodb/repositories/MongoReactiveExecutorPersonRepository.java

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
- `M` benchmarks/benchmark-spring-data-mongodb/src/jmh/java/example/SimpleQuery.java
- `M` config/checkstyle/checkstyle.xml
- `M` config/checkstyle/custom-suppressions.xml
- `M` data-azure-cosmos/src/main/java/io/micronaut/data/cosmos/common/CosmosDatabaseInitializer.java
- `M` data-azure-cosmos/src/main/java/io/micronaut/data/cosmos/common/CosmosEntity.java
- `M` data-azure-cosmos/src/main/java/io/micronaut/data/cosmos/common/CosmosUtils.java
- `M` data-azure-cosmos/src/main/java/io/micronaut/data/cosmos/config/CosmosDatabaseConfiguration.java
- `M` data-azure-cosmos/src/main/java/io/micronaut/data/cosmos/config/ThroughputSettings.java
- `M` data-azure-cosmos/src/main/java/io/micronaut/data/cosmos/operations/CosmosBinder.java
- `M` data-azure-cosmos/src/main/java/io/micronaut/data/cosmos/operations/CosmosDiagnosticsProcessor.java
- `M` data-azure-cosmos/src/main/java/io/micronaut/data/cosmos/operations/CosmosSerde.java
- `M` data-azure-cosmos/src/main/java/io/micronaut/data/cosmos/operations/CosmosSqlPreparedQuery.java
- `M` data-azure-cosmos/src/main/java/io/micronaut/data/cosmos/operations/CosmosSqlStoredQuery.java
- `M` data-azure-cosmos/src/main/java/io/micronaut/data/cosmos/operations/DefaultReactiveCosmosRepositoryOperations.java
- `A` data-azure-cosmos/src/main/java/io/micronaut/data/cosmos/operations/JacksonNodeConverter.java
- `M` data-azure-cosmos/src/main/java/io/micronaut/data/cosmos/operations/SyncCosmosRepositoryOperations.java
- `M` data-connection-hibernate/src/main/java/io/micronaut/data/hibernate/connection/HibernateConnectionConnectionOperations.java
- `M` data-connection-hibernate/src/main/java/io/micronaut/data/hibernate/connection/HibernateConnectionOperations.java
- `M` data-connection-jdbc/src/main/java/io/micronaut/data/connection/jdbc/advice/ContextualAwareDataSource.java
- `M` data-connection-jdbc/src/main/java/io/micronaut/data/connection/jdbc/advice/ContextualConnectionInterceptor.java
- `M` data-connection-jdbc/src/main/java/io/micronaut/data/connection/jdbc/advice/DelegatingDataSource.java
- `M` data-connection-jdbc/src/main/java/io/micronaut/data/connection/jdbc/oracle/OracleClientInfoConnectionCustomizer.java
- `A` data-connection/src/main/java/io/micronaut/data/connection/ConnectionCapabilities.java
- `M` data-connection/src/main/java/io/micronaut/data/connection/ConnectionDefinition.java
- `M` data-connection/src/main/java/io/micronaut/data/connection/ConnectionOperations.java
- `M` data-connection/src/main/java/io/micronaut/data/connection/ConnectionOperationsRegistry.java
- `M` data-connection/src/main/java/io/micronaut/data/connection/ConnectionStatus.java
- `A` data-connection/src/main/java/io/micronaut/data/connection/DefaultConnectionCapabilities.java
- `M` data-connection/src/main/java/io/micronaut/data/connection/DefaultConnectionDefinition.java
- `M` data-connection/src/main/java/io/micronaut/data/connection/DefaultConnectionOperationsRegistry.java
- `M` data-connection/src/main/java/io/micronaut/data/connection/SynchronousConnectionManager.java
- `M` data-connection/src/main/java/io/micronaut/data/connection/async/AsyncConnectionOperations.java
- `M` data-connection/src/main/java/io/micronaut/data/connection/async/AsyncUsingReactiveConnectionOperations.java
- `M` data-connection/src/main/java/io/micronaut/data/connection/interceptor/ConnectableInterceptor.java
- `M` data-connection/src/main/java/io/micronaut/data/connection/interceptor/ConnectionDataSourceTenantResolver.java
- `M` data-connection/src/main/java/io/micronaut/data/connection/reactive/DefaultReactiveConnectionStatus.java
- `M` data-connection/src/main/java/io/micronaut/data/connection/reactive/ReactiveConnectionStatus.java
- `M` data-connection/src/main/java/io/micronaut/data/connection/reactive/ReactiveStreamsConnectionOperations.java
- `M` data-connection/src/main/java/io/micronaut/data/connection/reactive/ReactorConnectionOperations.java
- `M` data-connection/src/main/java/io/micronaut/data/connection/support/AbstractConnectionOperations.java
- `M` data-connection/src/main/java/io/micronaut/data/connection/support/AbstractReactorConnectionOperations.java
- `M` data-connection/src/main/java/io/micronaut/data/connection/support/DefaultConnectionStatus.java
- `M` data-connection/src/main/java/io/micronaut/data/connection/support/JdbcConnectionUtils.java
- `M` data-connection/src/main/java/io/micronaut/data/connection/sync/SynchronousConnectionOperationsFromReactiveConnectionOperations.java
- `M` data-hibernate-jpa/src/main/java/io/micronaut/data/hibernate/event/EventIntegrator.java
- `M` data-hibernate-jpa/src/main/java/io/micronaut/data/hibernate/jakarta/data/HibernateJakartaDataPersistExceptionConverter.java
- `M` data-hibernate-jpa/src/main/java/io/micronaut/data/hibernate/naming/DefaultPhysicalNamingStrategy.java
- `M` data-hibernate-jpa/src/main/java/io/micronaut/data/hibernate/operations/AbstractHibernateOperations.java
- `M` data-hibernate-jpa/src/main/java/io/micronaut/data/hibernate/operations/HibernateJpaOperations.java
- `M` data-hibernate-jpa/src/main/resources/META-INF/native-image/io.micronaut.data/data-hibernate-jpa-graal/reflect-config.json
- `M` data-hibernate-reactive/src/main/java/io/micronaut/data/hibernate/reactive/operations/DefaultHibernateReactiveRepositoryOperations.java
- `M` data-hibernate-reactive/src/main/java/io/micronaut/data/hibernate/reactive/operations/DefaultHibernateReactiveSynchronousRepositoryOperations.java
- `M` data-hibernate-reactive/src/main/java/io/micronaut/data/hibernate/reactive/operations/DefaultHibernateReactorTransactionOperations.java
- `M` data-hibernate-reactive/src/main/java/io/micronaut/data/hibernate/reactive/operations/HibernateReactorRepositoryOperations.java
- `M` data-jdbc/src/main/java/io/micronaut/data/jdbc/annotation/JdbcRepository.java
- `M` data-jdbc/src/main/java/io/micronaut/data/jdbc/config/DataJdbcConfiguration.java
- `M` data-jdbc/src/main/java/io/micronaut/data/jdbc/config/SchemaGenerator.java
- `A` data-jdbc/src/main/java/io/micronaut/data/jdbc/convert/vendor/AbstractJdbcVectorConverter.java
- `A` data-jdbc/src/main/java/io/micronaut/data/jdbc/convert/vendor/MySqlJdbcVectorConverter.java
- `A` data-jdbc/src/main/java/io/micronaut/data/jdbc/convert/vendor/MySqlTypeConvertersFactory.java
- `A` data-jdbc/src/main/java/io/micronaut/data/jdbc/convert/vendor/OracleJdbcVectorConverter.java
- `M` data-jdbc/src/main/java/io/micronaut/data/jdbc/convert/vendor/OracleTypeConvertersFactory.java
- `A` data-jdbc/src/main/java/io/micronaut/data/jdbc/convert/vendor/PostgresJdbcSparseVectorConverter.java
- `A` data-jdbc/src/main/java/io/micronaut/data/jdbc/convert/vendor/PostgresJdbcVectorConverter.java
- `A` data-jdbc/src/main/java/io/micronaut/data/jdbc/convert/vendor/PostgresTypeConvertersFactory.java
- `A` data-jdbc/src/main/java/io/micronaut/data/jdbc/exceptions/jakarta/data/JdbcJakartaDataExceptionConverter.java
- `A` data-jdbc/src/main/java/io/micronaut/data/jdbc/mapper/CallableStatementTupleMapper.java
- `M` data-jdbc/src/main/java/io/micronaut/data/jdbc/mapper/ColumnIndexCallableResultReader.java
- `M` data-jdbc/src/main/java/io/micronaut/data/jdbc/mapper/ColumnIndexResultSetReader.java
- `A` data-jdbc/src/main/java/io/micronaut/data/jdbc/mapper/ColumnNameByIndexCallableResultReader.java
- `M` data-jdbc/src/main/java/io/micronaut/data/jdbc/mapper/ColumnNameCallableResultReader.java
- `A` data-jdbc/src/main/java/io/micronaut/data/jdbc/mapper/ColumnNameExistenceAwareCallableResultReader.java
- `M` data-jdbc/src/main/java/io/micronaut/data/jdbc/mapper/ColumnNameExistenceAwareResultSetReader.java
- `M` data-jdbc/src/main/java/io/micronaut/data/jdbc/mapper/ColumnNameResultSetReader.java
- `M` data-jdbc/src/main/java/io/micronaut/data/jdbc/mapper/JdbcQueryStatement.java
- `M` data-jdbc/src/main/java/io/micronaut/data/jdbc/mapper/JdbcTuple.java
- `M` data-jdbc/src/main/java/io/micronaut/data/jdbc/mapper/OracleJdbcJsonColumnMapper.java
- `M` data-jdbc/src/main/java/io/micronaut/data/jdbc/mapper/package-info.java
- `M` data-jdbc/src/main/java/io/micronaut/data/jdbc/operations/DefaultJdbcRepositoryOperations.java
- `A` data-jdbc/src/main/java/io/micronaut/data/jdbc/operations/OracleReturningSupport.java
- `M` data-jdbc/src/main/java/io/micronaut/data/jdbc/operations/OracleSqlExceptionMapper.java
- `M` data-jdbc/src/main/java/io/micronaut/data/jdbc/operations/SqlExceptionMapper.java
- `M` data-jdbc/src/main/java/io/micronaut/data/jdbc/runtime/ConnectionCallback.java
- `M` data-jdbc/src/main/java/io/micronaut/data/jdbc/runtime/JdbcOperations.java
- `M` data-jdbc/src/main/java/io/micronaut/data/jdbc/runtime/PreparedStatementCallback.java
- `M` data-jpa/src/main/java/io/micronaut/data/jpa/annotation/EntityGraph.java
- `M` data-jpa/src/main/java/io/micronaut/data/jpa/operations/JpaRepositoryOperations.java
- `M` data-jpa/src/main/java/io/micronaut/data/jpa/repository/JpaRepository.java
- `A` data-jpa/src/main/java/io/micronaut/data/jpa/repository/intercept/DetachInterceptor.java
- `M` data-jpa/src/main/java/io/micronaut/data/jpa/repository/intercept/FlushInterceptor.java
- `M` data-jpa/src/main/java/io/micronaut/data/jpa/repository/intercept/LoadInterceptor.java
- `M` data-jpa/src/main/java/io/micronaut/data/jpa/repository/intercept/MergeInterceptor.java
- `A` data-jpa/src/main/java/io/micronaut/data/jpa/repository/intercept/PersistInterceptor.java
- `A` data-jpa/src/main/java/io/micronaut/data/jpa/repository/intercept/RefreshInterceptor.java
- `A` data-jpa/src/main/java/io/micronaut/data/jpa/repository/intercept/RemoveInterceptor.java
- `M` data-model/src/main/java/io/micronaut/data/annotation/AutoPopulated.java
- `M` data-model/src/main/java/io/micronaut/data/annotation/By.java
- `M` data-model/src/main/java/io/micronaut/data/annotation/DataAnnotationUtils.java
- `M` data-model/src/main/java/io/micronaut/data/annotation/DateCreated.java
- `M` data-model/src/main/java/io/micronaut/data/annotation/DateUpdated.java
- `M` data-model/src/main/java/io/micronaut/data/annotation/EmbeddedId.java
- `A` data-model/src/main/java/io/micronaut/data/annotation/EmbeddedNaming.java
- `A` data-model/src/main/java/io/micronaut/data/annotation/Fetch.java
- `M` data-model/src/main/java/io/micronaut/data/annotation/Find.java
- `A` data-model/src/main/java/io/micronaut/data/annotation/First.java
- `A` data-model/src/main/java/io/micronaut/data/annotation/GenerateJakartaDataMetamodel.java
- `M` data-model/src/main/java/io/micronaut/data/annotation/GeneratedValue.java
- `M` data-model/src/main/java/io/micronaut/data/annotation/Id.java
- `M` data-model/src/main/java/io/micronaut/data/annotation/IgnoreWhere.java
- `M` data-model/src/main/java/io/micronaut/data/annotation/Index.java
- `M` data-model/src/main/java/io/micronaut/data/annotation/Indexes.java
- `M` data-model/src/main/java/io/micronaut/data/annotation/Join.java
- `A` data-model/src/main/java/io/micronaut/data/annotation/JsonSubView.java
- `M` data-model/src/main/java/io/micronaut/data/annotation/JsonView.java
- `M` data-model/src/main/java/io/micronaut/data/annotation/MappedEntity.java
- `M` data-model/src/main/java/io/micronaut/data/annotation/MappedProperty.java
- `M` data-model/src/main/java/io/micronaut/data/annotation/OrderBy.java
- `A` data-model/src/main/java/io/micronaut/data/annotation/Projection.java
- `M` data-model/src/main/java/io/micronaut/data/annotation/Query.java
- `M` data-model/src/main/java/io/micronaut/data/annotation/QueryHint.java
- `M` data-model/src/main/java/io/micronaut/data/annotation/Relation.java
- `M` data-model/src/main/java/io/micronaut/data/annotation/RepositoryConfiguration.java
- `A` data-model/src/main/java/io/micronaut/data/annotation/Srid.java
- `M` data-model/src/main/java/io/micronaut/data/annotation/Transient.java
- `M` data-model/src/main/java/io/micronaut/data/annotation/TypeDef.java
- `M` data-model/src/main/java/io/micronaut/data/annotation/TypeRole.java
- `A` data-model/src/main/java/io/micronaut/data/annotation/VectorIndex.java
- `A` data-model/src/main/java/io/micronaut/data/annotation/VectorIndexType.java
- `A` data-model/src/main/java/io/micronaut/data/annotation/VectorShape.java
- `A` data-model/src/main/java/io/micronaut/data/annotation/VectorStorage.java
- `M` data-model/src/main/java/io/micronaut/data/annotation/Where.java
- `A` data-model/src/main/java/io/micronaut/data/annotation/event/package-info.java
- `M` data-model/src/main/java/io/micronaut/data/annotation/package-info.java
- `M` data-model/src/main/java/io/micronaut/data/annotation/repeatable/QueryHints.java
- `M` data-model/src/main/java/io/micronaut/data/annotation/repeatable/TypeDefinitions.java
- `M` data-model/src/main/java/io/micronaut/data/annotation/repeatable/package-info.java
- `M` data-model/src/main/java/io/micronaut/data/annotation/sql/package-info.java
- `M` data-model/src/main/java/io/micronaut/data/event/EntityEventContext.java
- `M` data-model/src/main/java/io/micronaut/data/event/EntityEventListener.java
- `M` data-model/src/main/java/io/micronaut/data/event/listeners/PostPersistEventListener.java
- `M` data-model/src/main/java/io/micronaut/data/event/listeners/PostRemoveEventListener.java
- `M` data-model/src/main/java/io/micronaut/data/event/listeners/PostUpdateEventListener.java
- `M` data-model/src/main/java/io/micronaut/data/event/listeners/PrePersistEventListener.java
- `M` data-model/src/main/java/io/micronaut/data/event/listeners/PreRemoveEventListener.java
- `M` data-model/src/main/java/io/micronaut/data/event/listeners/PreUpdateEventListener.java
- `R083` data-model/src/main/java/io/micronaut/data/event/listeners/package-info.java
- `A` data-model/src/main/java/io/micronaut/data/event/package-info.java
- `A` data-model/src/main/java/io/micronaut/data/exceptions/EntityExistsException.java
- `M` data-model/src/main/java/io/micronaut/data/exceptions/ExceptionConverter.java
- `M` data-model/src/main/java/io/micronaut/data/exceptions/package-info.java
- `M` data-model/src/main/java/io/micronaut/data/intercept/DataInterceptor.java
- `A` data-model/src/main/java/io/micronaut/data/intercept/InsertAllInterceptor.java
- `A` data-model/src/main/java/io/micronaut/data/intercept/InsertEntityInterceptor.java
- `A` data-model/src/main/java/io/micronaut/data/intercept/InsertOneInterceptor.java
- `M` data-model/src/main/java/io/micronaut/data/intercept/UpdateInterceptor.java
- `M` data-model/src/main/java/io/micronaut/data/intercept/annotation/DataMethod.java
- `M` data-model/src/main/java/io/micronaut/data/intercept/annotation/DataMethodQuery.java
- `A` data-model/src/main/java/io/micronaut/data/intercept/annotation/DataMethodQueryOutParameter.java
- `M` data-model/src/main/java/io/micronaut/data/intercept/annotation/package-info.java
- `A` data-model/src/main/java/io/micronaut/data/intercept/async/DeleteReturningManyAsyncInterceptor.java
- `A` data-model/src/main/java/io/micronaut/data/intercept/async/DeleteReturningOneAsyncInterceptor.java
- `M` data-model/src/main/java/io/micronaut/data/intercept/async/FindOneAsyncInterceptor.java
- `A` data-model/src/main/java/io/micronaut/data/intercept/async/InsertAllAsyncInterceptor.java
- `A` data-model/src/main/java/io/micronaut/data/intercept/async/InsertEntityAsyncInterceptor.java
- `A` data-model/src/main/java/io/micronaut/data/intercept/async/InsertOneAsyncInterceptor.java
- `A` data-model/src/main/java/io/micronaut/data/intercept/async/InsertReturningManyAsyncInterceptor.java
- `A` data-model/src/main/java/io/micronaut/data/intercept/async/InsertReturningOneAsyncInterceptor.java
- `A` data-model/src/main/java/io/micronaut/data/intercept/async/UpdateReturningManyAsyncInterceptor.java
- `A` data-model/src/main/java/io/micronaut/data/intercept/async/UpdateReturningOneAsyncInterceptor.java
- `M` data-model/src/main/java/io/micronaut/data/intercept/async/package-info.java
- `M` data-model/src/main/java/io/micronaut/data/intercept/package-info.java
- `A` data-model/src/main/java/io/micronaut/data/intercept/reactive/DeleteReturningManyReactiveInterceptor.java
- `A` data-model/src/main/java/io/micronaut/data/intercept/reactive/DeleteReturningOneReactiveInterceptor.java
- `A` data-model/src/main/java/io/micronaut/data/intercept/reactive/InsertAllReactiveInterceptor.java
- `A` data-model/src/main/java/io/micronaut/data/intercept/reactive/InsertEntityReactiveInterceptor.java
- `A` data-model/src/main/java/io/micronaut/data/intercept/reactive/InsertOneReactiveInterceptor.java
- `A` data-model/src/main/java/io/micronaut/data/intercept/reactive/InsertReturningManyReactiveInterceptor.java
- `A` data-model/src/main/java/io/micronaut/data/intercept/reactive/InsertReturningOneReactiveInterceptor.java
- `A` data-model/src/main/java/io/micronaut/data/intercept/reactive/UpdateReturningManyReactiveInterceptor.java
- `A` data-model/src/main/java/io/micronaut/data/intercept/reactive/UpdateReturningOneReactiveInterceptor.java
- `M` data-model/src/main/java/io/micronaut/data/model/AbstractPersistentEntity.java
- `M` data-model/src/main/java/io/micronaut/data/model/Association.java
- `M` data-model/src/main/java/io/micronaut/data/model/CursoredPage.java
- `M` data-model/src/main/java/io/micronaut/data/model/CursoredPageable.java
- `M` data-model/src/main/java/io/micronaut/data/model/DataType.java
- `M` data-model/src/main/java/io/micronaut/data/model/DefaultCursoredPage.java
- `M` data-model/src/main/java/io/micronaut/data/model/DefaultCursoredPageable.java
- `M` data-model/src/main/java/io/micronaut/data/model/DefaultPage.java
- `M` data-model/src/main/java/io/micronaut/data/model/DefaultPageable.java
- `M` data-model/src/main/java/io/micronaut/data/model/DefaultSlice.java
- `M` data-model/src/main/java/io/micronaut/data/model/DefaultSort.java
- `M` data-model/src/main/java/io/micronaut/data/model/Page.java
- `M` data-model/src/main/java/io/micronaut/data/model/Pageable.java
- `M` data-model/src/main/java/io/micronaut/data/model/PersistentAssociationPath.java
- `M` data-model/src/main/java/io/micronaut/data/model/PersistentElement.java
- `M` data-model/src/main/java/io/micronaut/data/model/PersistentEntity.java
- `M` data-model/src/main/java/io/micronaut/data/model/PersistentEntityUtils.java
- `M` data-model/src/main/java/io/micronaut/data/model/PersistentProperty.java
- `M` data-model/src/main/java/io/micronaut/data/model/PersistentPropertyPath.java
- `M` data-model/src/main/java/io/micronaut/data/model/Slice.java
- `M` data-model/src/main/java/io/micronaut/data/model/Sort.java
- `A` data-model/src/main/java/io/micronaut/data/model/geo/Geometry.java
- `A` data-model/src/main/java/io/micronaut/data/model/geo/GeometryCollection.java
- `A` data-model/src/main/java/io/micronaut/data/model/geo/LineString.java
- `A` data-model/src/main/java/io/micronaut/data/model/geo/MultiLineString.java
- `A` data-model/src/main/java/io/micronaut/data/model/geo/MultiPoint.java
- `A` data-model/src/main/java/io/micronaut/data/model/geo/MultiPolygon.java
- `A` data-model/src/main/java/io/micronaut/data/model/geo/Point.java
- `A` data-model/src/main/java/io/micronaut/data/model/geo/Polygon.java
- `A` data-model/src/main/java/io/micronaut/data/model/geo/package-info.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/IExpression.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/ISelection.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/PersistentAssociationPath.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/PersistentEntityCommonAbstractCriteria.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/PersistentEntityCriteriaBuilder.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/PersistentEntityCriteriaDelete.java
- `A` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/PersistentEntityCriteriaInsert.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/PersistentEntityCriteriaQuery.java
- `A` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/PersistentEntityCriteriaQueryBuilder.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/PersistentEntityCriteriaUpdate.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/PersistentEntityFrom.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/PersistentEntityPath.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/PersistentEntityQuery.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/PersistentEntityRoot.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/PersistentEntitySubquery.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/PersistentPropertyPath.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/AbstractCriteriaBuilder.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/AbstractPersistentEntityCriteriaDelete.java
- `A` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/AbstractPersistentEntityCriteriaInsert.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/AbstractPersistentEntityCriteriaQuery.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/AbstractPersistentEntityCriteriaUpdate.java
- `R073` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/AbstractPersistentEntityFrom.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/AbstractPersistentEntityQuery.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/AbstractPersistentEntitySubquery.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/CriteriaUtils.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/DefaultEmbeddedPersistentPropertyPath.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/DefaultOrder.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/DefaultParameterExpression.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/DefaultPersistentPropertyPath.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/ExpressionVisitor.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/IParameterExpression.java
- `D` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/LegacyQueryModelQueryBuilder.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/PredicateVisitor.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/PropertyPathParameterBinding.java
- `D` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/QueryResultPersistentEntityCriteriaQuery.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/SimpleParameterBinding.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/expression/AbstractExpression.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/expression/BinaryExpression.java
- `A` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/expression/CastExpression.java
- `A` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/expression/CurrentTemporalExpression.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/expression/FunctionExpression.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/expression/LiteralExpression.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/expression/SubqueryExpression.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/expression/UnaryExpression.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/predicate/AbstractPredicate.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/predicate/InPredicate.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/predicate/LikePredicate.java
- `A` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/predicate/NearPredicate.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/predicate/PredicateBinaryOp.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/predicate/PredicateUnaryOp.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/predicate/UnaryPredicate.java
- `D` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/query/QueryModelPredicateVisitor.java
- `D` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/query/QueryModelSelectionVisitor.java
- `M` data-model/src/main/java/io/micronaut/data/model/jpa/criteria/impl/util/Joiner.java
- `M` data-model/src/main/java/io/micronaut/data/model/naming/NamingStrategies.java
- `M` data-model/src/main/java/io/micronaut/data/model/naming/NamingStrategy.java
- `M` data-model/src/main/java/io/micronaut/data/model/package-info.java
- `D` data-model/src/main/java/io/micronaut/data/model/query/AssociationQuery.java
- `M` data-model/src/main/java/io/micronaut/data/model/query/BindingContextImpl.java
- `M` data-model/src/main/java/io/micronaut/data/model/query/BindingParameter.java
- `D` data-model/src/main/java/io/micronaut/data/model/query/Criteria.java
- `D` data-model/src/main/java/io/micronaut/data/model/query/DefaultProjectionList.java
- `D` data-model/src/main/java/io/micronaut/data/model/query/DefaultQuery.java
- `M` data-model/src/main/java/io/micronaut/data/model/query/JoinPath.java
- `D` data-model/src/main/java/io/micronaut/data/model/query/ProjectionList.java
- `D` data-model/src/main/java/io/micronaut/data/model/query/QueryModel.java
- `D` data-model/src/main/java/io/micronaut/data/model/query/QueryParameter.java
- `D` data-model/src/main/java/io/micronaut/data/model/query/builder/AbstractSqlLikeQueryBuilder.java
- `M` data-model/src/main/java/io/micronaut/data/model/query/builder/AdditionalParameterBinding.java
- `M` data-model/src/main/java/io/micronaut/data/model/query/builder/QueryBuilder.java
- `D` data-model/src/main/java/io/micronaut/data/model/query/builder/QueryBuilder2.java
- `A` data-model/src/main/java/io/micronaut/data/model/query/builder/QueryOutParameterBinding.java
- `M` data-model/src/main/java/io/micronaut/data/model/query/builder/QueryParameterBinding.java
- `M` data-model/src/main/java/io/micronaut/data/model/query/builder/QueryResult.java
- `M` data-model/src/main/java/io/micronaut/data/model/query/builder/jpa/JpaQueryBuilder.java
- `D` data-model/src/main/java/io/micronaut/data/model/query/builder/jpa/JpaQueryBuilder2.java
- `R076` data-model/src/main/java/io/micronaut/data/model/query/builder/sql/AbstractSqlLikeQueryBuilder.java
- `M` data-model/src/main/java/io/micronaut/data/model/query/builder/sql/Dialect.java
- `M` data-model/src/main/java/io/micronaut/data/model/query/builder/sql/PropertyParameterCreator.java
- `M` data-model/src/main/java/io/micronaut/data/model/query/builder/sql/SqlQueryBuilder.java
- `D` data-model/src/main/java/io/micronaut/data/model/query/builder/sql/SqlQueryBuilder2.java
- `M` data-model/src/main/java/io/micronaut/data/model/query/builder/sql/SqlQueryBuilderUtils.java
- `M` data-model/src/main/java/io/micronaut/data/model/query/builder/sql/SqlQueryConfiguration.java
- `M` data-model/src/main/java/io/micronaut/data/model/query/builder/sql/SqlSchemaUtils.java
- `A` data-model/src/main/java/io/micronaut/data/model/query/builder/sql/VectorScoringDialectSupport.java
- `A` data-model/src/main/java/io/micronaut/data/model/query/builder/sql/VectorSimilarityDialect.java
- `M` data-model/src/main/java/io/micronaut/data/model/query/builder/sql/validation/SqlServerTableMappingValidator.java
- `M` data-model/src/main/java/io/micronaut/data/model/query/builder/sql/validation/SqlTableMappingValidator.java
- `D` data-model/src/main/java/io/micronaut/data/model/query/factory/Projections.java
- `D` data-model/src/main/java/io/micronaut/data/model/query/factory/Restrictions.java
- `M` data-model/src/main/java/io/micronaut/data/model/query/impl/AdvancedPredicateVisitor.java
- `M` data-model/src/main/java/io/micronaut/data/model/runtime/AbstractPreparedDataOperation.java
- `M` data-model/src/main/java/io/micronaut/data/model/runtime/AttributeConverterRegistry.java
- `M` data-model/src/main/java/io/micronaut/data/model/runtime/BeanPropertyWithAnnotationMetadata.java
- `M` data-model/src/main/java/io/micronaut/data/model/runtime/DefaultStoredDataOperation.java
- `M` data-model/src/main/java/io/micronaut/data/model/runtime/DelegatingQueryParameterBinding.java
- `M` data-model/src/main/java/io/micronaut/data/model/runtime/DeleteReturningBatchOperation.java
- `M` data-model/src/main/java/io/micronaut/data/model/runtime/DeleteReturningOperation.java
- `M` data-model/src/main/java/io/micronaut/data/model/runtime/EntityInstanceOperation.java
- `M` data-model/src/main/java/io/micronaut/data/model/runtime/EntityOperation.java
- `M` data-model/src/main/java/io/micronaut/data/model/runtime/PagedQuery.java
- `M` data-model/src/main/java/io/micronaut/data/model/runtime/PreparedDataOperation.java
- `M` data-model/src/main/java/io/micronaut/data/model/runtime/PreparedQuery.java
- `M` data-model/src/main/java/io/micronaut/data/model/runtime/PropertyAutoPopulator.java
- `A` data-model/src/main/java/io/micronaut/data/model/runtime/QueryOutParameterBinding.java
- `M` data-model/src/main/java/io/micronaut/data/model/runtime/QueryParameterBinding.java
- `M` data-model/src/main/java/io/micronaut/data/model/runtime/QueryResultInfo.java
- `M` data-model/src/main/java/io/micronaut/data/model/runtime/RuntimeAssociation.java
- `M` data-model/src/main/java/io/micronaut/data/model/runtime/RuntimeEntityRegistry.java
- `M` data-model/src/main/java/io/micronaut/data/model/runtime/RuntimePersistentEntity.java
- `M` data-model/src/main/java/io/micronaut/data/model/runtime/RuntimePersistentProperty.java
- `M` data-model/src/main/java/io/micronaut/data/model/runtime/StoredDataOperation.java
- `M` data-model/src/main/java/io/micronaut/data/model/runtime/StoredQuery.java
- `M` data-model/src/main/java/io/micronaut/data/model/runtime/convert/AttributeConverter.java
- `A` data-model/src/main/java/io/micronaut/data/model/runtime/convert/DatabaseType.java
- `A` data-model/src/main/java/io/micronaut/data/model/runtime/convert/DefinitionProvider.java
- `A` data-model/src/main/java/io/micronaut/data/model/runtime/convert/GeometryJsonConverter.java
- `A` data-model/src/main/java/io/micronaut/data/model/runtime/convert/GeometryWktConverter.java
- `A` data-model/src/main/java/io/micronaut/data/model/runtime/convert/OracleJsonMapper.java
- `A` data-model/src/main/java/io/micronaut/data/model/runtime/convert/SqlColumnDefinitionProvider.java
- `A` data-model/src/main/java/io/micronaut/data/model/runtime/convert/SqlIndexDefinitionProvider.java
- `A` data-model/src/main/java/io/micronaut/data/model/runtime/convert/vector/ByteVectorAttributeConverter.java
- `A` data-model/src/main/java/io/micronaut/data/model/runtime/convert/vector/DoubleVectorAttributeConverter.java
- `A` data-model/src/main/java/io/micronaut/data/model/runtime/convert/vector/FloatVectorAttributeConverter.java
- `A` data-model/src/main/java/io/micronaut/data/model/runtime/convert/vector/SparseByteVectorAttributeConverter.java
- `A` data-model/src/main/java/io/micronaut/data/model/runtime/convert/vector/SparseDoubleVectorAttributeConverter.java
- `A` data-model/src/main/java/io/micronaut/data/model/runtime/convert/vector/SparseFloatVectorAttributeConverter.java
- `A` data-model/src/main/java/io/micronaut/data/model/runtime/convert/vector/VectorAttributeConverter.java
- `A` data-model/src/main/java/io/micronaut/data/model/runtime/convert/vector/VectorTypeConverter.java
- `A` data-model/src/main/java/io/micronaut/data/model/runtime/convert/vector/package-info.java
- `M` data-model/src/main/java/io/micronaut/data/model/schema/sql/SqlColumnMapping.java
- `M` data-model/src/main/java/io/micronaut/data/model/schema/sql/SqlDbType.java
- `M` data-model/src/main/java/io/micronaut/data/model/schema/sql/SqlIndexMapping.java
- `M` data-model/src/main/java/io/micronaut/data/model/schema/sql/SqlSequenceMapping.java
- `M` data-model/src/main/java/io/micronaut/data/model/schema/sql/SqlTableMapping.java
- `M` data-model/src/main/java/io/micronaut/data/model/schema/sql/metadata/SqlColumnMetadata.java
- `M` data-model/src/main/java/io/micronaut/data/model/schema/sql/metadata/SqlTableMetadata.java
- `A` data-model/src/main/java/io/micronaut/data/model/schema/sql/metadata/VectorIndexMetadata.java
- `A` data-model/src/main/java/io/micronaut/data/model/vector/ByteVector.java
- `A` data-model/src/main/java/io/micronaut/data/model/vector/DoubleVector.java
- `A` data-model/src/main/java/io/micronaut/data/model/vector/FloatVector.java
- `A` data-model/src/main/java/io/micronaut/data/model/vector/SparseByteVector.java
- `A` data-model/src/main/java/io/micronaut/data/model/vector/SparseDoubleVector.java
- `A` data-model/src/main/java/io/micronaut/data/model/vector/SparseFloatVector.java
- `A` data-model/src/main/java/io/micronaut/data/model/vector/SparseVector.java
- `A` data-model/src/main/java/io/micronaut/data/model/vector/Vector.java
- `A` data-model/src/main/java/io/micronaut/data/model/vector/VectorArrays.java
- `R076` data-model/src/main/java/io/micronaut/data/model/vector/package-info.java
- `A` data-model/src/main/java/io/micronaut/data/model/vector/search/DefaultSearchResults.java
- `A` data-model/src/main/java/io/micronaut/data/model/vector/search/Score.java
- `A` data-model/src/main/java/io/micronaut/data/model/vector/search/ScoringFunction.java
- `A` data-model/src/main/java/io/micronaut/data/model/vector/search/SearchResult.java
- `A` data-model/src/main/java/io/micronaut/data/model/vector/search/SearchResults.java
- `A` data-model/src/main/java/io/micronaut/data/model/vector/search/Similarity.java
- `A` data-model/src/main/java/io/micronaut/data/model/vector/search/package-info.java
- `M` data-model/src/main/java/io/micronaut/data/operations/BlockingCriteriaCapableRepository.java
- `M` data-model/src/main/java/io/micronaut/data/operations/CriteriaRepositoryOperations.java
- `M` data-model/src/main/java/io/micronaut/data/operations/DeleteReturningRepositoryOperations.java
- `M` data-model/src/main/java/io/micronaut/data/operations/HintsCapableRepository.java
- `M` data-model/src/main/java/io/micronaut/data/operations/RepositoryOperations.java
- `M` data-model/src/main/java/io/micronaut/data/operations/RepositoryOperationsRegistry.java
- `M` data-model/src/main/java/io/micronaut/data/operations/async/AsyncCapableRepository.java
- `M` data-model/src/main/java/io/micronaut/data/operations/async/AsyncCriteriaCapableRepository.java
- `M` data-model/src/main/java/io/micronaut/data/operations/async/AsyncCriteriaRepositoryOperations.java
- `M` data-model/src/main/java/io/micronaut/data/operations/async/AsyncRepositoryOperations.java
- `M` data-model/src/main/java/io/micronaut/data/operations/async/package-info.java
- `M` data-model/src/main/java/io/micronaut/data/operations/package-info.java
- `M` data-model/src/main/java/io/micronaut/data/operations/reactive/BlockingExecutorReactorRepositoryOperations.java
- `M` data-model/src/main/java/io/micronaut/data/operations/reactive/BlockingReactorCriteriaRepositoryOperations.java
- `M` data-model/src/main/java/io/micronaut/data/operations/reactive/BlockingReactorRepositoryOperations.java
- `M` data-model/src/main/java/io/micronaut/data/operations/reactive/ReactiveCapableRepository.java
- `M` data-model/src/main/java/io/micronaut/data/operations/reactive/ReactiveCriteriaCapableRepository.java
- `M` data-model/src/main/java/io/micronaut/data/operations/reactive/ReactiveCriteriaRepositoryOperations.java
- `M` data-model/src/main/java/io/micronaut/data/operations/reactive/ReactiveRepositoryOperations.java
- `M` data-model/src/main/java/io/micronaut/data/operations/reactive/ReactorCriteriaCapableRepository.java
- `M` data-model/src/main/java/io/micronaut/data/operations/reactive/ReactorCriteriaRepositoryOperations.java
- `M` data-model/src/main/java/io/micronaut/data/operations/reactive/ReactorReactiveCapableRepository.java
- `M` data-model/src/main/java/io/micronaut/data/operations/reactive/ReactorReactiveRepositoryOperations.java
- `M` data-model/src/main/java/io/micronaut/data/operations/reactive/package-info.java
- `M` data-model/src/main/java/io/micronaut/data/repository/CrudRepository.java
- `M` data-model/src/main/java/io/micronaut/data/repository/PageableRepository.java
- `M` data-model/src/main/java/io/micronaut/data/repository/async/AsyncCrudRepository.java
- `M` data-model/src/main/java/io/micronaut/data/repository/async/AsyncPageableRepository.java
- `M` data-model/src/main/java/io/micronaut/data/repository/async/package-info.java
- `M` data-model/src/main/java/io/micronaut/data/repository/jpa/criteria/CriteriaDeleteBuilder.java
- `M` data-model/src/main/java/io/micronaut/data/repository/jpa/criteria/CriteriaQueryBuilder.java
- `M` data-model/src/main/java/io/micronaut/data/repository/jpa/criteria/CriteriaUpdateBuilder.java
- `R086` data-model/src/main/java/io/micronaut/data/repository/jpa/package-info.java
- `M` data-model/src/main/java/io/micronaut/data/repository/package-info.java
- `M` data-model/src/main/java/io/micronaut/data/repository/reactive/ReactiveStreamsCrudRepository.java
- `M` data-model/src/main/java/io/micronaut/data/repository/reactive/ReactiveStreamsPageableRepository.java
- `M` data-model/src/main/java/io/micronaut/data/repository/reactive/ReactorCrudRepository.java
- `M` data-model/src/main/java/io/micronaut/data/repository/reactive/ReactorPageableRepository.java
- `M` data-model/src/main/java/io/micronaut/data/repository/reactive/RxJavaCrudRepository.java
- `M` data-model/src/main/java/io/micronaut/data/repository/reactive/package-info.java
- `M` data-model/src/main/kotlin/io/micronaut/data/repository/kotlin/CoroutineCrudRepository.kt
- `A` data-model/src/main/kotlin/io/micronaut/data/repository/kotlin/KotlinCrudRepository.kt
- `A` data-model/src/main/kotlin/io/micronaut/data/repository/kotlin/KotlinPageableCrudRepository.kt
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/advice/ContexualClientSessionInterceptor.java
- `A` data-mongodb/src/main/java/io/micronaut/data/mongodb/annotation/MongoUpdateReturningQuery.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/conf/MongoDataConfiguration.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/database/MongoDatabaseNameProviderFactory.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/database/MongoReactiveFactory.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/operations/AbstractMongoRepositoryOperations.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/operations/DefaultMongoCollectionNameProvider.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/operations/DefaultMongoDatabaseNameProvider.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/operations/DefaultMongoPreparedQuery.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/operations/DefaultMongoRepositoryOperations.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/operations/DefaultMongoStoredQuery.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/operations/DefaultReactiveMongoRepositoryOperations.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/operations/MongoAggregation.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/operations/MongoCollectionNameProvider.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/operations/MongoDatabaseNameProvider.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/operations/MongoDelete.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/operations/MongoFind.java
- `A` data-mongodb/src/main/java/io/micronaut/data/mongodb/operations/MongoFindOneAndUpdate.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/operations/MongoPreparedQuery.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/operations/MongoRoles.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/operations/MongoStoredQuery.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/operations/MongoUpdate.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/operations/MongoUtils.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/operations/options/MongoAggregationOptions.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/operations/options/MongoFindOptions.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/operations/options/MongoOptionsUtils.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/repository/MongoQueryExecutor.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/repository/MongoReactiveQueryExecutor.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/serde/DataCodecRegistry.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/serde/DataDecoderContext.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/serde/DataEncoderContext.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/serde/DataSerdeRegistry.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/serde/DefaultDecoderContext.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/serde/DefaultEncoderContext.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/serde/MappedCodec.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/serde/MappedEntityCodec.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/session/DefaultMongoReactorConnectionOperations.java
- `M` data-mongodb/src/main/java/io/micronaut/data/mongodb/transaction/MongoTransactionOperationsImpl.java
- `M` data-mongodb/src/main/resources/META-INF/native-image/io.micronaut.data/micronaut-data-mongodb/native-image.properties
- `D` data-processor/src/main/antlr/JDQL.g4
- `A` data-processor/src/main/antlr/JQ.g4
- `D` data-processor/src/main/java/io/micronaut/data/processor/jdql/JDQLCriteriaBuilderUtils.java
- `A` data-processor/src/main/java/io/micronaut/data/processor/jq/JQCriteriaBuilderUtils.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/MappedEntityMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jakarta/data/JakartaDataByMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jakarta/data/JakartaDataDeleteMapper.java
- `A` data-processor/src/main/java/io/micronaut/data/processor/mappers/jakarta/data/JakartaDataDetachMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jakarta/data/JakartaDataFindMapper.java
- `A` data-processor/src/main/java/io/micronaut/data/processor/mappers/jakarta/data/JakartaDataFirstByMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jakarta/data/JakartaDataInsertMapper.java
- `A` data-processor/src/main/java/io/micronaut/data/processor/mappers/jakarta/data/JakartaDataMergeStatefulMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jakarta/data/JakartaDataOrderByListMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jakarta/data/JakartaDataOrderByMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jakarta/data/JakartaDataParamsMapper.java
- `A` data-processor/src/main/java/io/micronaut/data/processor/mappers/jakarta/data/JakartaDataPersistMapper.java
- `A` data-processor/src/main/java/io/micronaut/data/processor/mappers/jakarta/data/JakartaDataRefreshMapper.java
- `A` data-processor/src/main/java/io/micronaut/data/processor/mappers/jakarta/data/JakartaDataRemoveMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jakarta/data/JakartaDataRepositoryMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jakarta/data/JakartaDataSaveMapper.java
- `A` data-processor/src/main/java/io/micronaut/data/processor/mappers/jakarta/data/JakartaDataSelectListMapper.java
- `A` data-processor/src/main/java/io/micronaut/data/processor/mappers/jakarta/data/JakartaDataSelectMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jakarta/data/JakartaDataUpdateMapper.java
- `A` data-processor/src/main/java/io/micronaut/data/processor/mappers/jakarta/data/package-info.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jakarta/ColumnAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jakarta/ConvertAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jakarta/ConverterAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jakarta/EmbeddableAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jakarta/EmbeddedAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jakarta/EmbeddedIdAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jakarta/EntityAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jakarta/EnumeratedAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jakarta/GeneratedValueMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jakarta/IdAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jakarta/IndexAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jakarta/JoinColumnAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jakarta/JoinTableAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jakarta/ManyToManyMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jakarta/ManyToOneMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jakarta/OneToManyMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jakarta/OneToOneMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jakarta/TableAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jakarta/TransientAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jakarta/event/PostLoadAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jakarta/event/PostPersistAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jakarta/event/PostRemoveAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jakarta/event/PostUpdateAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jakarta/event/PrePersistAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jakarta/event/PreRemoveAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jakarta/event/PreUpdateAnnotationMapper.java
- `A` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jakarta/event/package-info.java
- `A` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jakarta/package-info.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jx/ColumnAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jx/ConvertAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jx/ConverterAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jx/EmbeddableAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jx/EmbeddedAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jx/EmbeddedIdAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jx/EntityAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jx/EnumeratedAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jx/GeneratedValueMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jx/IdAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jx/IndexAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jx/JoinColumnAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jx/JoinTableAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jx/ManyToManyMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jx/ManyToOneMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jx/OneToManyMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jx/OneToOneMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jx/TableAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jx/TransientAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jx/event/PostLoadAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jx/event/PostPersistAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jx/event/PostRemoveAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jx/event/PostUpdateAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jx/event/PrePersistAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jx/event/PreRemoveAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jx/event/PreUpdateAnnotationMapper.java
- `A` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jx/event/package-info.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jpa/jx/package-info.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jta/JakartaTransactionalMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jta/JtaTransactionalMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/jta/package-info.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/spring/SpringCreatedDateMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/spring/SpringIdMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/spring/SpringLastModifiedDateMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/spring/SpringPersistenceConstructorMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/spring/SpringPersistentAnnotationMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/spring/SpringRepositoryMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/spring/SpringTransactionalEventListenerMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/spring/SpringTransientMapper.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/mappers/spring/package-info.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/model/SourceAssociation.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/model/SourceEmbedded.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/model/SourcePersistentEntity.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/model/SourcePersistentProperty.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/model/criteria/SourcePersistentEntityCriteriaBuilder.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/model/criteria/SourcePersistentEntityCriteriaDelete.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/model/criteria/SourcePersistentEntityCriteriaQuery.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/model/criteria/SourcePersistentEntityCriteriaUpdate.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/model/criteria/SourcePersistentEntitySubquery.java
- `R090` data-processor/src/main/java/io/micronaut/data/processor/model/criteria/impl/AbstractSourcePersistentEntityFrom.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/model/criteria/impl/ClassElementExpressionType.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/model/criteria/impl/MethodMatchSourcePersistentEntityCriteriaBuilderImpl.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/model/criteria/impl/QueryResultAnalyzer.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/model/criteria/impl/SourceParameterExpressionImpl.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/model/criteria/impl/SourceParameterStringExpressionImpl.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/model/criteria/impl/SourcePersistentAssociationPath.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/model/criteria/impl/SourcePersistentEntityCriteriaBuilderImpl.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/model/criteria/impl/SourcePersistentEntityCriteriaDeleteImpl.java
- `A` data-processor/src/main/java/io/micronaut/data/processor/model/criteria/impl/SourcePersistentEntityCriteriaInsertImpl.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/model/criteria/impl/SourcePersistentEntityCriteriaQueryImpl.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/model/criteria/impl/SourcePersistentEntityCriteriaUpdateImpl.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/model/criteria/impl/SourcePersistentEntityRoot.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/model/criteria/impl/SourcePersistentEntitySubqueryImpl.java
- `A` data-processor/src/main/java/io/micronaut/data/processor/model/criteria/impl/package-info.java
- `A` data-processor/src/main/java/io/micronaut/data/processor/model/criteria/package-info.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/model/package-info.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/EmbeddableVisitor.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/EntityEventVisitor.java
- `A` data-processor/src/main/java/io/micronaut/data/processor/visitors/GenerateJakartaDataMetamodelVisitor.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/MappedEntityVisitor.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/MatchContext.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/MatchFailedException.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/MethodMatchContext.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/RepositoryTypeElementVisitor.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/Utils.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/AbstractCriteriaMethodMatch.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/AbstractMethodMatcher.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/AbstractPatternMethodMatcher.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/AbstractPrefixPatternMethodMatcher.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/CountMethodMatcher.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/DeleteMethodMatcher.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/ExistsMethodMatcher.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/FindMethodMatcher.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/FindersUtils.java
- `R074` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/JakartaDataQueryMethodMatcher.java
- `A` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/MatchUtils.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/MethodCandidate.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/MethodMatchInfo.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/MethodMatcher.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/MethodNameParser.java
- `A` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/MethodResult.java
- `A` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/OracleRawQueryReturningSupport.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/ProcedureMethodMatcher.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/Projections.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/RawQueryMethodMatcher.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/Restrictions.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/SaveMethodMatcher.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/TypeUtils.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/UpdateMethodMatcher.java
- `A` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/VectorSearchMethodMatcher.java
- `D` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/annotated/DeleteAnnotatedMethodMatcher.java
- `D` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/annotated/FindAnnotatedMethodMatcher.java
- `D` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/annotated/InsertAnnotatedMethodMatcher.java
- `D` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/annotated/SaveAnnotatedMethodMatcher.java
- `D` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/annotated/UpdateAnnotatedMethodMatcher.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/criteria/DeleteCriteriaMethodMatch.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/criteria/QueryCriteriaMethodMatch.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/criteria/UpdateCriteriaMethodMatch.java
- `A` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/criteria/package-info.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/package-info.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/package-info.java
- `M` data-processor/src/main/resources/META-INF/services/io.micronaut.data.processor.visitors.finders.MethodMatcher
- `M` data-processor/src/main/resources/META-INF/services/io.micronaut.inject.annotation.AnnotationMapper
- `A` data-processor/src/main/resources/META-INF/services/io.micronaut.inject.visitor.PackageElementVisitor
- `M` data-processor/src/main/resources/META-INF/services/io.micronaut.inject.visitor.TypeElementVisitor
- `M` data-r2dbc/src/main/java/io/micronaut/data/r2dbc/annotation/R2dbcRepository.java
- `M` data-r2dbc/src/main/java/io/micronaut/data/r2dbc/config/DataR2dbcConfiguration.java
- `M` data-r2dbc/src/main/java/io/micronaut/data/r2dbc/config/R2dbcSchemaGenerator.java
- `M` data-r2dbc/src/main/java/io/micronaut/data/r2dbc/connection/DefaultR2dbcReactorConnectionOperations.java
- `A` data-r2dbc/src/main/java/io/micronaut/data/r2dbc/convert/vendor/AbstractR2dbcVectorConverter.java
- `A` data-r2dbc/src/main/java/io/micronaut/data/r2dbc/convert/vendor/OracleR2dbcVectorConverter.java
- `A` data-r2dbc/src/main/java/io/micronaut/data/r2dbc/convert/vendor/OracleTypeConvertersFactory.java
- `A` data-r2dbc/src/main/java/io/micronaut/data/r2dbc/convert/vendor/PostgresR2dbcVectorConverter.java
- `A` data-r2dbc/src/main/java/io/micronaut/data/r2dbc/convert/vendor/PostgresTypeConvertersFactory.java
- `A` data-r2dbc/src/main/java/io/micronaut/data/r2dbc/exceptions/jakarta/data/R2dbcJakartaDataExceptionConverter.java
- `M` data-r2dbc/src/main/java/io/micronaut/data/r2dbc/mapper/ColumnIndexR2dbcResultReader.java
- `A` data-r2dbc/src/main/java/io/micronaut/data/r2dbc/mapper/ColumnIndexReadableResultReader.java
- `A` data-r2dbc/src/main/java/io/micronaut/data/r2dbc/mapper/ColumnNameByIndexR2dbcResultReader.java
- `M` data-r2dbc/src/main/java/io/micronaut/data/r2dbc/mapper/ColumnNameExistenceAwareR2dbcResultSetReader.java
- `A` data-r2dbc/src/main/java/io/micronaut/data/r2dbc/mapper/ColumnNameExistenceAwareReadableR2dbcResultReader.java
- `M` data-r2dbc/src/main/java/io/micronaut/data/r2dbc/mapper/ColumnNameR2dbcResultReader.java
- `M` data-r2dbc/src/main/java/io/micronaut/data/r2dbc/mapper/OracleR2dbcJsonColumnMapper.java
- `A` data-r2dbc/src/main/java/io/micronaut/data/r2dbc/mapper/R2dbcBytesReader.java
- `M` data-r2dbc/src/main/java/io/micronaut/data/r2dbc/mapper/R2dbcQueryStatement.java
- `M` data-r2dbc/src/main/java/io/micronaut/data/r2dbc/mapper/R2dbcTuple.java
- `A` data-r2dbc/src/main/java/io/micronaut/data/r2dbc/mapper/ReadableTupleMapper.java
- `M` data-r2dbc/src/main/java/io/micronaut/data/r2dbc/operations/DefaultR2dbcRepositoryOperations.java
- `M` data-r2dbc/src/main/java/io/micronaut/data/r2dbc/operations/OracleR2dbcExceptionMapper.java
- `A` data-r2dbc/src/main/java/io/micronaut/data/r2dbc/operations/OracleR2dbcVectorBindSupport.java
- `M` data-r2dbc/src/main/java/io/micronaut/data/r2dbc/operations/R2dbcExceptionMapper.java
- `M` data-r2dbc/src/main/java/io/micronaut/data/r2dbc/operations/R2dbcOperations.java
- `M` data-r2dbc/src/main/java/io/micronaut/data/r2dbc/operations/ReactorReactiveCapableRepository.java
- `R062` data-r2dbc/src/main/java/io/micronaut/data/r2dbc/operations/VectorBindSupport.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `A` .github/workflows/oracle-test-pilot.yml
- `M` benchmarks/benchmark-spring-data-mongodb/src/test/java/example/BookRepositoryTest.java
- `M` data-azure-cosmos/src/test/groovy/io/micronaut/data/azure/BuildCosmosQuerySpec.groovy
- `M` data-azure-cosmos/src/test/groovy/io/micronaut/data/azure/CosmosBasicSpec.groovy
- `M` data-azure-cosmos/src/test/groovy/io/micronaut/data/azure/CosmosCriteriaSpec.groovy
- `M` data-azure-cosmos/src/test/groovy/io/micronaut/data/azure/NoPartitionKeyCosmosDbSpec.groovy
- `A` data-azure-cosmos/src/test/groovy/io/micronaut/data/cosmos/operations/JacksonNodeConverterSpec.groovy
- `A` data-azure-cosmos/src/test/groovy/io/micronaut/data/cosmos/operations/SyncCosmosRepositoryOperationsSpec.groovy
- `M` data-azure-cosmos/src/test/java/io/micronaut/data/azure/repositories/CosmosBookRepository.java
- `M` data-azure-cosmos/src/test/java/io/micronaut/data/azure/repositories/FamilyRepository.java
- `A` data-connection-jdbc/src/test/groovy/io/micronaut/data/connection/reactive/ReactiveConnManager.java
- `A` data-connection-jdbc/src/test/groovy/io/micronaut/data/connection/reactive/ReactiveConnectionSynchronizationSpec.groovy
- `M` data-connection-jdbc/src/test/groovy/io/micronaut/data/jdbc/TestResourcesDatabaseTestPropertyProvider.groovy
- `M` data-connection-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/H2TestPropertyProvider.groovy
- `A` data-connection/src/test/java/example/ConnectionCapabilitiesTest.java
- `A` data-connection/src/test/java/example/CustomConnectionCapabilities.java
- `A` data-connection/src/test/resources/META-INF/services/io.micronaut.data.connection.ConnectionCapabilities
- `A` data-connection/src/test/resources/logback.xml
- `M` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/AbstractHibernateQuerySpec.groovy
- `M` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/DtoAssociationsSpec.groovy
- `M` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/DtoSpec.groovy
- `M` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/HibernatePostgresQuerySpec.groovy
- `A` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/HibernatePostgresStreamingSpec.groovy
- `M` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/HibernateQuerySpec.groovy
- `M` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/JpaEmbeddedIdSpec.groovy
- `M` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/JpaSpecificationCrudRepositorySpec.groovy
- `M` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/LoadSpec.groovy
- `M` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/MultipleDataSourceSpec.groovy
- `M` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/PersonRepository.groovy
- `M` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/ScalarProjectionSpec.groovy
- `M` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/async/AsyncSpec.groovy
- `D` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/jakarta_data/entity/Box.java
- `D` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/jakarta_data/entity/Boxes.java
- `D` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/jakarta_data/entity/Coordinate.java
- `D` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/jakarta_data/entity/EntityTests.java
- `D` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/jakarta_data/entity/MultipleEntityRepo.java
- `D` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/jakarta_data/persistence/Catalog.java
- `D` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/jakarta_data/persistence/CatalogProduct.java
- `D` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/jakarta_data/persistence/PersistenceEntityTests.java
- `D` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/jakarta_data/read/only/AsciiCharacter.java
- `D` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/jakarta_data/read/only/AsciiCharacters.java
- `D` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/jakarta_data/read/only/AsciiCharactersPopulator.java
- `D` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/jakarta_data/read/only/CustomRepository.java
- `D` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/jakarta_data/read/only/IdOperations.java
- `D` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/jakarta_data/read/only/NaturalNumber.java
- `D` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/jakarta_data/read/only/NaturalNumbers.java
- `D` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/jakarta_data/read/only/NaturalNumbersPopulator.java
- `D` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/jakarta_data/read/only/Populator.java
- `D` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/jakarta_data/read/only/PositiveIntegers.java
- `D` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/jakarta_data/read/only/ReadOnlyRepository.java
- `D` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/jakarta_data/read/only/_AsciiChar.java
- `D` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/jakarta_data/read/only/_AsciiCharacter.java
- `D` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/jakarta_data/utilities/DatabaseType.java
- `D` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/jakarta_data/utilities/TestProperty.java
- `D` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/jakarta_data/utilities/TestPropertyHandler.java
- `A` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/operations/HibernateJpaOperationsSpec.groovy
- `M` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/reactive/ReactorSpec.groovy
- `R093` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/reactive/RxJavaSpec.groovy
- `M` data-hibernate-jpa/src/test/groovy/io/micronaut/data/hibernate/sort/Level1Repository.java
- `M` data-hibernate-jpa/src/test/java/io/micronaut/data/hibernate/AuthorRepository.java
- `M` data-hibernate-jpa/src/test/java/io/micronaut/data/hibernate/BookRepository.java
- `M` data-hibernate-jpa/src/test/java/io/micronaut/data/hibernate/ChildrenRepository.java
- `R090` data-hibernate-jpa/src/test/java/io/micronaut/data/hibernate/H2DBProperties.java
- `A` data-hibernate-jpa/src/test/java/io/micronaut/data/hibernate/HibernateJakartaDataTest.java
- `A` data-hibernate-jpa/src/test/java/io/micronaut/data/hibernate/HibernateTrainRepository.java
- `A` data-hibernate-jpa/src/test/java/io/micronaut/data/hibernate/HibernateTrainsRepository.java
- `M` data-hibernate-jpa/src/test/java/io/micronaut/data/hibernate/JpaSpecificationCrudRepository.java
- `M` data-hibernate-jpa/src/test/java/io/micronaut/data/hibernate/RelPersonRepository.java
- `M` data-hibernate-jpa/src/test/java/io/micronaut/data/hibernate/UserWithWhereRepository.java
- `M` data-hibernate-jpa/src/test/java/io/micronaut/data/hibernate/entities/Children.java
- `M` data-hibernate-jpa/src/test/java/io/micronaut/data/hibernate/entities/ChildrenId.java
- `A` data-hibernate-jpa/src/test/java/io/micronaut/data/hibernate/nativepostgresql/PostgresStreamingPersonRepository.java
- `M` data-hibernate-jpa/src/test/java/io/micronaut/data/hibernate/reactive/RxJavaPersonRepo.java
- `D` data-hibernate-reactive/src/main/java/io/micronaut/data/hibernate/reactive/repository/jpa/ReactiveStreamsJpaSpecificationExecutor.java
- `D` data-hibernate-reactive/src/main/java/io/micronaut/data/hibernate/reactive/repository/jpa/ReactorJpaSpecificationExecutor.java
- `D` data-hibernate-reactive/src/main/java/io/micronaut/data/hibernate/reactive/repository/jpa/intercept/AbstractSpecificationInterceptor.java
- `D` data-hibernate-reactive/src/main/java/io/micronaut/data/hibernate/reactive/repository/jpa/intercept/ReactiveCountSpecificationInterceptor.java
- `D` data-hibernate-reactive/src/main/java/io/micronaut/data/hibernate/reactive/repository/jpa/intercept/ReactiveFindAllSpecificationInterceptor.java
- `D` data-hibernate-reactive/src/main/java/io/micronaut/data/hibernate/reactive/repository/jpa/intercept/ReactiveFindOneSpecificationInterceptor.java
- `D` data-hibernate-reactive/src/main/java/io/micronaut/data/hibernate/reactive/repository/jpa/intercept/ReactiveFindPageSpecificationInterceptor.java
- `M` data-hibernate-reactive/src/test/groovy/io/micronaut/data/hibernate/reactive/DtoAssociationsSpec.groovy
- `M` data-hibernate-reactive/src/test/groovy/io/micronaut/data/hibernate/reactive/HibernateQuerySpec.groovy
- `M` data-hibernate-reactive/src/test/groovy/io/micronaut/data/hibernate/reactive/JpaEmbeddedIdSpec.groovy
- `M` data-hibernate-reactive/src/test/groovy/io/micronaut/data/hibernate/reactive/JpaSpecificationCrudRepositorySpec.groovy
- `M` data-hibernate-reactive/src/test/groovy/io/micronaut/data/hibernate/reactive/ScalarProjectionSpec.groovy
- `M` data-hibernate-reactive/src/test/groovy/io/micronaut/data/hibernate/reactive/async/AsyncSpec.groovy
- `M` data-hibernate-reactive/src/test/groovy/io/micronaut/data/hibernate/reactive/propagate/FooService.java
- `M` data-hibernate-reactive/src/test/groovy/io/micronaut/data/hibernate/reactive/reactive/HibernateReactiveSpec.groovy
- `R092` data-hibernate-reactive/src/test/groovy/io/micronaut/data/hibernate/reactive/reactive/RxJavaSpec.groovy
- `M` data-hibernate-reactive/src/test/groovy/io/micronaut/data/hibernate/reactive/sort/Level1Repository.java
- `M` data-hibernate-reactive/src/test/java/io/micronaut/data/hibernate/reactive/AuthorRepository.java
- `M` data-hibernate-reactive/src/test/java/io/micronaut/data/hibernate/reactive/BookRepository.java
- `M` data-hibernate-reactive/src/test/java/io/micronaut/data/hibernate/reactive/JpaSpecificationCrudRepository.java
- `M` data-hibernate-reactive/src/test/java/io/micronaut/data/hibernate/reactive/MySqlHibernateReactiveProperties.java
- `M` data-hibernate-reactive/src/test/java/io/micronaut/data/hibernate/reactive/entities/Children.java
- `M` data-hibernate-reactive/src/test/java/io/micronaut/data/hibernate/reactive/reactive/RxJavaPersonRepo.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/CallableStatementTupleMapperSpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/ColumnNameExistenceAwareResultSetReaderSpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/DefaultJdbcRepositoryOperationsSpec.groovy
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/TestResourcesDatabaseTestPropertyProvider.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/convert/vendor/MySqlTypeConvertersFactorySpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/convert/vendor/OracleJdbcVectorConverterSparseSpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/convert/vendor/PostgresTypeConvertersFactorySpec.groovy
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/H2CascadeSpec.groovy
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/H2CompositePrimaryKeySpec.groovy
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/H2CursoredPaginationSpec.groovy
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/H2DBProperties.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/H2DBPropertiesTestPropertyProviderFactory.groovy
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/H2Embedded2Spec.groovy
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/H2EmbeddedCascadeSpec.groovy
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/H2EmbeddedIdSpec.groovy
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/H2EmbeddedSpec.groovy
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/H2EnumsMappingSpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/H2GeoSpec.groovy
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/H2RepositorySpec.groovy
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/H2TestPropertyProvider.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/assignedid/AssignedUuidCascadePersistSpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/assignedid/AssignedUuidManyToManyPersistSpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/assignedid/SaveAsInsertSpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/assignedid/SaveAssignedIdFallbackToUpdateSpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/autopopulate/AutoPopulateEmbeddedSpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/autopopulate/AutoPopulateSkipIfPresentSpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/autopopulate/AutoTimestampSkipIfPresentSpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/autopopulate/ImmutableAuditTimestamps.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/autopopulate/ImmutableCustomer.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/autopopulate/ImmutableEmbedWithUUID.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/autopopulate/ImmutableEntityWithEmbedUUID.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/autopopulate/ImmutableTimestampedEntity.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/autopopulate/InnerFields.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/autopopulate/TSEntity.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/autopopulate/package-info.java
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/composite/CompositeSpec.groovy
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/embeddedAssociation/EmbeddedAssociationJoinSpec.groovy
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/embeddedNameMapping/CustomEmbeddedNameMapping.groovy
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/identity/SameIdentityRepositorySpec.groovy
- `D` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/jakarta_data/entity/Box.java
- `D` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/jakarta_data/entity/Boxes.java
- `D` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/jakarta_data/entity/Coordinate.java
- `D` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/jakarta_data/entity/EntityTests.java
- `D` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/jakarta_data/entity/MultipleEntityRepo.java
- `D` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/jakarta_data/persistence/Catalog.java
- `D` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/jakarta_data/persistence/CatalogProduct.java
- `D` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/jakarta_data/persistence/PersistenceEntityTests.java
- `D` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/jakarta_data/read/only/AsciiCharacter.java
- `D` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/jakarta_data/read/only/AsciiCharacters.java
- `D` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/jakarta_data/read/only/AsciiCharactersPopulator.java
- `D` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/jakarta_data/read/only/CustomRepository.java
- `D` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/jakarta_data/read/only/IdOperations.java
- `D` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/jakarta_data/read/only/NaturalNumber.java
- `D` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/jakarta_data/read/only/NaturalNumbers.java
- `D` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/jakarta_data/read/only/NaturalNumbersPopulator.java
- `D` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/jakarta_data/read/only/Populator.java
- `D` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/jakarta_data/read/only/PositiveIntegers.java
- `D` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/jakarta_data/read/only/ReadOnlyRepository.java
- `D` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/jakarta_data/read/only/_AsciiChar.java
- `D` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/jakarta_data/read/only/_AsciiCharacter.java
- `D` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/jakarta_data/simple/Address.java
- `D` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/jakarta_data/simple/Customer.java
- `D` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/jakarta_data/simple/CustomerDaoTest.java
- `D` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/jakarta_data/simple/CustomerOnlyDeleteQueryRepository.java
- `D` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/jakarta_data/simple/CustomerRepository.java
- `D` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/jakarta_data/simple/CustomerRepository2.java
- `D` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/jakarta_data/utilities/DatabaseType.java
- `D` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/jakarta_data/utilities/TestProperty.java
- `D` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/jakarta_data/utilities/TestPropertyHandler.java
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/joinissue/Book.java
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/joinissue/Director.java
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/joinissue/Movie.java
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/many2many/ManyToManyJoinTableSpec.groovy
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/many2one/MultiManyToOneJoinSpec.groovy
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/multitenancy/TenancyBook.java
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/multitenancy/TenancyBookControllerSpec.groovy
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/multitenancy/TenancyPersonService.java
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/one2many/DoubleOneToManyJoinSpec.groovy
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/one2many/OneToManyHierarchicalSpec.groovy
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/one2one/OneToOneSpec.groovy
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/one2one/select/MyOrder.java
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/one2one/select/MyOrderRepository.java
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/h2/remap/ManyToManyAttributeSpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/mapper/JdbcQueryStatementSpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/mariadb/MariaGeoSpec.groovy
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/mariadb/MariaRepositorySpec.groovy
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/mariadb/MariaSchemaSpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/mysql/MySqlGeoSpec.groovy
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/mysql/MySqlRepositorySpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/mysql/vector/MySqlJdbcByteVectorEntitySpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/mysql/vector/MySqlJdbcDoubleVectorEntitySpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/mysql/vector/MySqlJdbcFloatVectorEntitySpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/mysql/vector/MySqlJdbcVectorColumnLengthSpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/mysql/vector/MySqlJdbcVectorEntitySpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/mysql/vector/MySqlJdbcVectorLengthSpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/mysql/vector/MySqlVectorTestPropertyProvider.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/mysql/vector/MysqlVectorIndexDdlSpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/OracleStreamingSpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/OracleTransactionPrioritySpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/OracleXE21TestPropertyProvider.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/OracleXEGeoSpec.groovy
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/OracleXEJSONSpec.groovy
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/OracleXERepositorySpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/OracleXETransactionPrioritySpec.groovy
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/bool/BooleanTest.java
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/Address.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/AddressSubView.java
- `D` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/AddressView.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/Airplane.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/AirplaneDetails.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/AirplaneView.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/AirplaneViewRepository.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/Apartment.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/ApartmentId.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/ApartmentSubView.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/ApartmentView.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/ApartmentViewRepository.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/Building.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/BuildingView.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/BuildingViewRepository.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/Car.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/CarDetails.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/CarDetailsRepository.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/CarDetailsSubView.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/CarView.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/CarViewRepository.java
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/Class.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/Crocodile.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/CrocodileView.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/CrocodileViewRepository.java
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/OracleJdbcJsonViewSpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/Person.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/PersonView.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/PersonViewRepository.java
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/Student.java
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/StudentClass.java
- `R069` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/StudentScheduleClassSubView.java
- `R064` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/StudentScheduleSubView.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/StudentSubView.java
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/StudentView.java
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/StudentViewRepository.java
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/Teacher.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/TeacherScheduleSubView.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/TeacherStudentSubView.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/TeacherSubView.java
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/TeacherView.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/jsonview/TeacherViewRepository.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/vector/OracleJdbcByteVectorEntitySpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/vector/OracleJdbcDoubleVectorEntitySpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/vector/OracleJdbcFloatVectorEntitySpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/vector/OracleJdbcVectorColumnLengthSpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/vector/OracleJdbcVectorEntitySpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/vector/OracleJdbcVectorLengthSpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/vector/OracleJdbcVectorNegativeSpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/vector/OracleJdbcVectorSpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/vector/OracleJdbcVectorTypeMismatchSpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/oraclexe/vector/OracleXeVectorIndexDdlSpec.groovy
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/postgres/PostgresArraysSpec.groovy
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/postgres/PostgresDbInit.java
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/postgres/PostgresGeoSpec.groovy
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/postgres/PostgresRepositorySpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/postgres/PostgresStreamingSpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/postgres/vector/PostgresJdbcDoubleVectorEntitySpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/postgres/vector/PostgresJdbcFloatVectorEntitySpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/postgres/vector/PostgresJdbcSparseVectorEntitySpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/postgres/vector/PostgresJdbcVectorColumnLengthSpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/postgres/vector/PostgresVectorIndexDdlSpec.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/postgres/vector/PostgresVectorTestPropertyProvider.groovy
- `A` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/sqlserver/SqlServerGeoSpec.groovy
- `M` data-jdbc/src/test/groovy/io/micronaut/data/jdbc/sqlserver/SqlServerRepositorySpec.groovy
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/exceptions/jakarta/data/JdbcJakartaDataExceptionConverterTest.java
- `M` data-jdbc/src/test/java/io/micronaut/data/jdbc/h2/CascadeSubEntityA.java
- `M` data-jdbc/src/test/java/io/micronaut/data/jdbc/h2/CascadeSubEntityB.java
- `M` data-jdbc/src/test/java/io/micronaut/data/jdbc/h2/ChallengeRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/h2/H2GeometryEntityJsonRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/h2/H2GeometryEntityWktRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/h2/H2HotelJsonRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/h2/H2HotelWktRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/h2/H2IntervalRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/h2/H2JakartaDataTest.java
- `M` data-jdbc/src/test/java/io/micronaut/data/jdbc/h2/H2RestaurantRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/h2/H2SchoolRepository.java
- `M` data-jdbc/src/test/java/io/micronaut/data/jdbc/h2/H2TableRatingsRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/h2/H2TestingPropertyProvider.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/h2/H2TrainRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/h2/H2TrainsRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/mysql/MySqlGeometryEntityJsonRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/mysql/MySqlGeometryEntityWktRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/mysql/MySqlHotelJsonRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/mysql/MySqlHotelWktRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/mysql/MySqlIntervalRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/mysql/MySqlSchoolRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/oraclexe/OracleBookMappedPropertyDto.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/oraclexe/OracleBookMethodProjectionDto.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/oraclexe/OracleRestaurantRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/oraclexe/OracleStreamingPersonRepository.java
- `M` data-jdbc/src/test/java/io/micronaut/data/jdbc/oraclexe/OracleXEBookRepository.java
- `M` data-jdbc/src/test/java/io/micronaut/data/jdbc/oraclexe/OracleXEFaceRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/oraclexe/OracleXEGeometryEntityJsonRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/oraclexe/OracleXEGeometryEntityWktRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/oraclexe/OracleXEHotelJsonRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/oraclexe/OracleXEHotelWktRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/oraclexe/OracleXEIntervalRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/oraclexe/OracleXESchoolRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/postgres/GeographyEntityJson.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/postgres/GeographyEntityWkt.java
- `M` data-jdbc/src/test/java/io/micronaut/data/jdbc/postgres/PostgresBookRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/postgres/PostgresGeographyEntityJsonRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/postgres/PostgresGeographyEntityWktRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/postgres/PostgresGeometryEntityJsonRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/postgres/PostgresGeometryEntityWktRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/postgres/PostgresHotelJsonRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/postgres/PostgresHotelWktRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/postgres/PostgresIntervalRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/postgres/PostgresSchoolRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/postgres/PostgresStreamingPersonRepository.java
- `M` data-jdbc/src/test/java/io/micronaut/data/jdbc/postgres/PostgresUuidRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/sqlserver/GeographyEntityWkt.java
- `M` data-jdbc/src/test/java/io/micronaut/data/jdbc/sqlserver/MSBookRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/sqlserver/MSGeographyEntityWktRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/sqlserver/MSGeometryEntityJsonRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/sqlserver/MSGeometryEntityWktRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/sqlserver/MSHotelJsonRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/sqlserver/MSHotelWktRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/sqlserver/MSIntervalRepository.java
- `A` data-jdbc/src/test/java/io/micronaut/data/jdbc/sqlserver/MSSchoolRepository.java
- `A` data-jdbc/src/test/resources/META-INF/services/io.micronaut.test.support.TestPropertyProviderFactory
- `M` data-jdbc/src/test/resources/application-oracle-jsonview.yml
- `M` data-jdbc/src/test/resources/application.yml
- `D` data-jdbc/src/test/resources/oracle-jsonview-migrations/V1__Create_Schema.sql
- `D` data-jpa/src/main/java/io/micronaut/data/jpa/repository/JpaSpecificationExecutor.java
- `D` data-jpa/src/main/java/io/micronaut/data/jpa/repository/criteria/Specification.java
- `D` data-jpa/src/main/java/io/micronaut/data/jpa/repository/criteria/SpecificationComposition.java
- `D` data-jpa/src/main/java/io/micronaut/data/jpa/repository/intercept/AbstractSpecificationInterceptor.java
- `D` data-jpa/src/main/java/io/micronaut/data/jpa/repository/intercept/CountSpecificationInterceptor.java
- `D` data-jpa/src/main/java/io/micronaut/data/jpa/repository/intercept/DeleteSpecificationInterceptor.java
- `D` data-jpa/src/main/java/io/micronaut/data/jpa/repository/intercept/FindAllSpecificationInterceptor.java
- `D` data-jpa/src/main/java/io/micronaut/data/jpa/repository/intercept/FindOneSpecificationInterceptor.java
- `D` data-jpa/src/main/java/io/micronaut/data/jpa/repository/intercept/FindPageSpecificationInterceptor.java
- `M` data-model/src/main/java/io/micronaut/data/annotation/repeatable/WhereSpecifications.java
- `A` data-model/src/main/java/io/micronaut/data/model/jd/SpecificationConstraint.java
- `M` data-model/src/main/java/io/micronaut/data/repository/jpa/JpaSpecificationExecutor.java
- `M` data-model/src/main/java/io/micronaut/data/repository/jpa/async/AsyncJpaSpecificationExecutor.java
- `M` data-model/src/main/java/io/micronaut/data/repository/jpa/criteria/DeleteSpecification.java
- `M` data-model/src/main/java/io/micronaut/data/repository/jpa/criteria/PredicateSpecification.java
- `M` data-model/src/main/java/io/micronaut/data/repository/jpa/criteria/QuerySpecification.java
- `M` data-model/src/main/java/io/micronaut/data/repository/jpa/criteria/SpecificationComposition.java
- `M` data-model/src/main/java/io/micronaut/data/repository/jpa/criteria/UpdateSpecification.java
- `M` data-model/src/main/java/io/micronaut/data/repository/jpa/reactive/ReactiveStreamsJpaSpecificationExecutor.java
- `M` data-model/src/main/java/io/micronaut/data/repository/jpa/reactive/ReactorJpaSpecificationExecutor.java
- `A` data-model/src/main/kotlin/io/micronaut/data/repository/jpa/kotlin/KotlinJpaSpecificationExecutor.kt
- `M` data-model/src/test/groovy/io/micronaut/data/model/PageSpec.groovy
- `A` data-model/src/test/groovy/io/micronaut/data/model/geo/GeometryCollectionSpec.groovy
- `A` data-model/src/test/groovy/io/micronaut/data/model/geo/GeometrySpec.groovy
- `A` data-model/src/test/groovy/io/micronaut/data/model/geo/LineStringSpec.groovy
- `A` data-model/src/test/groovy/io/micronaut/data/model/geo/MultiLineStringSpec.groovy
- `A` data-model/src/test/groovy/io/micronaut/data/model/geo/MultiPointSpec.groovy
- `A` data-model/src/test/groovy/io/micronaut/data/model/geo/MultiPolygonSpec.groovy
- `A` data-model/src/test/groovy/io/micronaut/data/model/geo/PointSpec.groovy
- `A` data-model/src/test/groovy/io/micronaut/data/model/geo/PolygonSpec.groovy
- `A` data-model/src/test/groovy/io/micronaut/data/model/runtime/convert/GeometryJsonConverterSpec.groovy
- `A` data-model/src/test/groovy/io/micronaut/data/model/runtime/convert/GeometryWktConverterSpec.groovy
- `A` data-model/src/test/groovy/io/micronaut/data/model/runtime/convert/vector/impl/AbstractOracleTypeConvertersFactorySpec.groovy
- `A` data-model/src/test/groovy/io/micronaut/data/model/schema/sql/SqlColumnMappingSpec.groovy
- `A` data-model/src/test/groovy/io/micronaut/data/model/schema/sql/SqlIndexMappingSpec.groovy
- `A` data-model/src/test/groovy/io/micronaut/data/model/vector/SparseVectorSpec.groovy
- `A` data-model/src/test/groovy/io/micronaut/data/model/vector/VectorBasicsSpec.groovy
- `A` data-model/src/test/groovy/io/micronaut/data/model/vector/VectorEmptySpec.groovy
- `A` data-model/src/test/groovy/io/micronaut/data/model/vector/search/SearchResultsSpec.groovy
- `A` data-model/src/test/groovy/io/micronaut/data/operations/reactive/ReactiveRepositoryOperationsSpec.groovy
- `A` data-mongodb/src/test/groovy/io/micronaut/data/mongodb/database/MongoReactiveFactorySpec.groovy
- `A` data-mongodb/src/test/groovy/io/micronaut/data/mongodb/operations/DefaultMongoRepositoryOperationsSpec.groovy
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/AbstractSpecificationMethodMatcher.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/spec/CountSpecificationMethodMatcher.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/spec/DeleteAllSpecificationMethodMatcher.java
- `D` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/spec/DeleteSpecificationMethodMatcher.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/spec/ExistsSpecificationMethodMatcher.java
- `D` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/spec/FindAllSpecificationMethodMatcher.java
- `D` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/spec/FindOneSpecificationMethodMatcher.java
- `D` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/spec/FindPageSpecificationMethodMatcher.java
- `A` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/spec/FindSpecificationMethodMatcher.java
- `M` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/spec/UpdateAllSpecificationMethodMatcher.java
- `A` data-processor/src/main/java/io/micronaut/data/processor/visitors/finders/spec/package-info.java
- `A` data-processor/src/test/groovy/io/micronaut/data/model/entities/GeogEntityJson.groovy
- `A` data-processor/src/test/groovy/io/micronaut/data/model/entities/GeogEntityWkt.groovy
- `A` data-processor/src/test/groovy/io/micronaut/data/model/entities/GeomEntityCompositeIndex.groovy
- `A` data-processor/src/test/groovy/io/micronaut/data/model/entities/GeomEntityJson.groovy
- `A` data-processor/src/test/groovy/io/micronaut/data/model/entities/GeomEntityWGS84.groovy
- `A` data-processor/src/test/groovy/io/micronaut/data/model/entities/GeomEntityWkt.groovy
- `M` data-processor/src/test/groovy/io/micronaut/data/model/entities/MappedEntityCar.java
- `M` data-processor/src/test/groovy/io/micronaut/data/model/jpa/criteria/CriteriaSpec.groovy
- `M` data-processor/src/test/groovy/io/micronaut/data/model/query/builder/JpaQueryBuilderSpec.groovy
- `M` data-processor/src/test/groovy/io/micronaut/data/model/query/builder/SqlQueryBuilderSpec.groovy
- `M` data-processor/src/test/groovy/io/micronaut/data/processor/groovy/GroovyBuildInsertSpec.groovy
- `D` data-processor/src/test/groovy/io/micronaut/data/processor/jdql/JakartaDataQueryLanguageBuilderSpec.groovy
- `A` data-processor/src/test/groovy/io/micronaut/data/processor/jq/JakartaQueryBuilderSpec.groovy
- `A` data-processor/src/test/groovy/io/micronaut/data/processor/metamodel/JakartaDataMetamodelSpec.groovy
- `M` data-processor/src/test/groovy/io/micronaut/data/processor/sql/BuildDeleteSpec.groovy
- `M` data-processor/src/test/groovy/io/micronaut/data/processor/sql/BuildInsertSpec.groovy
- `M` data-processor/src/test/groovy/io/micronaut/data/processor/sql/BuildQuerySpec.groovy
- `M` data-processor/src/test/groovy/io/micronaut/data/processor/sql/BuildTableSpec.groovy
- `M` data-processor/src/test/groovy/io/micronaut/data/processor/sql/BuildUpdateSpec.groovy
- `M` data-processor/src/test/groovy/io/micronaut/data/processor/sql/ColumnTransformerSpec.groovy
- `M` data-processor/src/test/groovy/io/micronaut/data/processor/sql/CompositePrimaryKeySpec.groovy
- `A` data-processor/src/test/groovy/io/micronaut/data/processor/sql/JakartaDataBuildQuerySpec.groovy
- `M` data-processor/src/test/groovy/io/micronaut/data/processor/sql/JsonViewSpec.groovy
- `M` data-processor/src/test/groovy/io/micronaut/data/processor/visitors/AbstractDataSpec.groovy
- `M` data-processor/src/test/groovy/io/micronaut/data/processor/visitors/AsyncSpec.groovy
- `M` data-processor/src/test/groovy/io/micronaut/data/processor/visitors/CountSpec.groovy
- `M` data-processor/src/test/groovy/io/micronaut/data/processor/visitors/CrudRepositorySpec.groovy
- `M` data-processor/src/test/groovy/io/micronaut/data/processor/visitors/EmbeddedSpec.groovy
- `M` data-processor/src/test/groovy/io/micronaut/data/processor/visitors/EqualsSpec.groovy
- `M` data-processor/src/test/groovy/io/micronaut/data/processor/visitors/FindSpec.groovy
- `M` data-processor/src/test/groovy/io/micronaut/data/processor/visitors/JoinPathSpec.groovy
- `M` data-processor/src/test/groovy/io/micronaut/data/processor/visitors/JpaJoinSpec.groovy
- `M` data-processor/src/test/groovy/io/micronaut/data/processor/visitors/OrderBySpec.groovy
- `M` data-processor/src/test/groovy/io/micronaut/data/processor/visitors/PageSpec.groovy
- `A` data-processor/src/test/groovy/io/micronaut/data/processor/visitors/ParameterTypeDefConverterFallbackSpec.groovy
- `M` data-processor/src/test/groovy/io/micronaut/data/processor/visitors/ParameterTypeDefSpec.groovy
- `A` data-processor/src/test/groovy/io/micronaut/data/processor/visitors/PeriodSpec.groovy
- `M` data-processor/src/test/groovy/io/micronaut/data/processor/visitors/ReactiveSpec.groovy
- `M` data-processor/src/test/groovy/io/micronaut/data/processor/visitors/RecordsSpec.groovy
- `M` data-processor/src/test/groovy/io/micronaut/data/processor/visitors/RelationshipSpec.groovy
- `M` data-processor/src/test/groovy/io/micronaut/data/processor/visitors/TestUtils.groovy
- `M` data-processor/src/test/groovy/io/micronaut/data/processor/visitors/TypeRoleSpec.groovy
- `A` data-processor/src/test/java/io/micronaut/data/processor/entity/OtherEntity.java
- `A` data-processor/src/test/java/io/micronaut/data/processor/entity/SomeEntity.java

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

