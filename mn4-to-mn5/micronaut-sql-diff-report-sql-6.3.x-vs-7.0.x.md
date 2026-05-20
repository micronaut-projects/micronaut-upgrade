# Diff Report: `6.3.x` vs `7.0.x` (micronaut-sql)

**Generated:** 2026-04-22
**Base (A):** `/Users/sdelamo/github/micronaut/mn4/micronaut-sql` — branch `6.3.x` @ `d0ad65f0`
**Comparison (B):** `/Users/sdelamo/github/micronaut/mn5/micronaut-sql` — branch `7.0.x` @ `baf1aed2`

---

## Summary

| Category | Count |
|----------|-------|
| Top-level added entries (only in B) | 30 |
| Top-level removed entries (only in A) | 4 |
| Files modified | 99 |

> Notes:
> - `tests/hibernate6/*` (51 files) in A was renamed to `tests/hibernate/*` (51 files) in B, with package path `example.hibernate6` → `example.hibernate`.
> - `.agents/` directory (14 skill files) added in B.
> - New top-level module `jdbc-unpooled` added in B.
> - New test modules added in B: `tests/vertx-pg-client-native`, `tests/jdbc-hikari-tests/jdbc-hikari-sqlite`.
> - `gradle/wrapper/gradle-wrapper.jar` binary differs; content not shown.
> - `hibernate-jpa/src/main/resources/META-INF/native-image/io.micronaut.sql/hibernate-jpa-graal/reflect-config.json` is large (371 line changes); truncated to first 50 lines.

---

## Dependency Changes

### Third-Party Upgrades

- `gradle`: `8.14.3` → `9.4.1` — [Release notes](https://docs.gradle.org/9.4.1/release-notes.html)
- `io.vertx:vertx-*` (managed-vertx): `4.5.24` → `5.0.11` — [Release notes](https://github.com/eclipse-vertx/vert.x/releases/tag/5.0.11)
- `org.jooq:jooq` (managed-jooq): `3.19.18` → `3.21.2` — [Release notes](https://www.jooq.org/notes)
- `org.hibernate.orm:hibernate-core` (managed-hibernate): `6.6.49.Final` → `7.3.2.Final` — [Release notes](https://hibernate.org/orm/releases/7.3/)
- `org.hibernate.reactive:hibernate-reactive-core` (managed-hibernate-reactive): `2.4.17.Final` → `4.3.3.Final` — [Release notes](https://github.com/hibernate/hibernate-reactive/releases/tag/4.3.3.Final)
- `org.jdbi:jdbi3-core` (managed-jdbi): `3.49.6` → `3.52.1` — [Release notes](https://github.com/jdbi/jdbi/releases/tag/v3.52.1)
- `com.oracle.database.jdbc:ojdbc*` (managed-ojdbc): `23.9.0.25.07` → `23.26.1.0.0` — [Release notes](https://www.oracle.com/database/technologies/appdev/jdbc-downloads.html)
- `com.oracle.database.jdbc:ojdbc*dms` (managed-ojdbcdms): `21.19.0.0` → `21.21.0.0` — [Release notes](https://www.oracle.com/database/technologies/appdev/jdbc-downloads.html)
- `org.postgresql:postgresql` (managed-postgres-driver): `42.7.8` → `42.7.10` — [Release notes](https://jdbc.postgresql.org/changelogs/)
- `org.mariadb.jdbc:mariadb-java-client` (managed-mariadb-driver): `3.5.6` → `3.5.8` — [Release notes](https://github.com/mariadb-corporation/mariadb-connector-j/releases/tag/3.5.8)
- `com.microsoft.sqlserver:mssql-jdbc` (managed-mssql-driver): `12.10.1.jre11` → `13.4.0.jre11` — [Release notes](https://github.com/microsoft/mssql-jdbc/releases/tag/v13.4.0)
- `com.mysql:mysql-connector-j` (managed-mysql-connector-j): `9.4.0` → `9.6.0` — [Release notes](https://dev.mysql.com/doc/relnotes/connector-j/en/)
- `com.zaxxer:HikariCP` (managed-hikari): `6.3.3` → `7.0.2` — [Release notes](https://github.com/brettwooldridge/HikariCP/releases/tag/HikariCP-7.0.2)
- `org.apache.commons:commons-dbcp2` (managed-commons-dbcp): `2.13.0` → `2.14.0` — [Release notes](https://commons.apache.org/proper/commons-dbcp/changes.html)
- `org.apache.tomcat:tomcat-jdbc` (managed-tomcat-jdbc): `11.0.12` → `11.0.21` — [Release notes](https://tomcat.apache.org/tomcat-11.0-doc/changelog.html)
- `jakarta.persistence:jakarta.persistence-api` (managed-jakarta-persistence-api): `3.1.0` → `3.2.0` — [Release notes](https://jakarta.ee/specifications/persistence/3.2/)
- `com.h2database:h2` (managed-h2): `2.3.232` → `2.4.240` — [Release notes](https://h2database.com/html/changelog.html)
- `org.sonarsource.scanner.gradle:sonarqube-gradle-plugin` (sonar-gradle-plugin): `6.3.1.5724` → `7.2.3.7755` — [Release notes](https://github.com/SonarSource/sonar-scanner-gradle/releases/tag/7.2.3.7755)
- **New:** `org.xerial:sqlite-jdbc` (managed-sqlite-jdbc) `3.53.0.0`

### Micronaut Version Bumps

- `micronaut`: `4.10.21` → `5.0.0-M23`
- `micronaut-gradle-plugin`: `4.5.5` → `4.6.2`
- `micronaut-test-resources`: `2.10.1` → `4.0.0-M1`
- `micronaut-cache`: `5.3.0` → `6.0.0-M3`
- `micronaut-data`: `4.13.5` → `5.0.0-M6`
- `micronaut-hibernate-validator`: `4.8.0` → `5.0.0-M1`
- `micronaut-logging`: `1.7.1` → `2.0.0-M2`
- `micronaut-micrometer`: `5.12.0` → `6.0.1-M1`
- `micronaut-r2dbc`: `6.1.0` → `7.0.1-M1`
- `micronaut-reactor`: `3.8.0` → `4.0.0-M2`
- `micronaut-serde`: `2.15.4` → `3.0.0-M7`
- `micronaut-spring`: `5.11.2` → `6.0.0-M2`
- `micronaut-test`: `4.9.0` → `5.0.0-M8`
- `micronaut-validation`: `4.11.0` → `5.0.0-M2`
- `micronaut-docs` (`3.0.0`): **removed** from versions
- `io.micronaut.build.shared.settings` plugin: `7.6.4` → `8.0.0-M17`

### Project Version

- `projectVersion`: `6.3.5-SNAPSHOT` → `7.0.0-SNAPSHOT`

### New Library Entries

- Added `managed-vertx-rx-java3`, `boms-jooq`, `managed-sqlite-jdbc` in `libs.versions.toml`.

### Removed

- `groovy = "4.0.11"` version pin removed from `libs.versions.toml`.

### `gradle/libs.versions.toml`
```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/gradle/libs.versions.toml	2026-04-22 07:32:32.130263640 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/gradle/libs.versions.toml	2026-04-22 07:29:45.030155989 +0000
@@ -1,57 +1,56 @@
 [versions]
 
 # Micronaut
-
-micronaut = "4.10.21"
-micronaut-docs = "3.0.0"
-micronaut-gradle-plugin = "4.5.5"
-micronaut-test-resources = "2.10.1"
+micronaut = "5.0.0-M23"
+micronaut-gradle-plugin = "4.6.2"
+micronaut-test-resources = "4.0.0-M1"
 
 # Platform dependencies
-micronaut-cache = "5.3.0"
-micronaut-data = "4.13.5"
-micronaut-hibernate-validator = "4.8.0"
-micronaut-logging = "1.7.1"
-micronaut-micrometer = "5.12.0"
-micronaut-r2dbc = "6.1.0"
-micronaut-reactor = "3.8.0"
-micronaut-serde = "2.15.4"
-micronaut-spring = "5.11.2"
-micronaut-test = "4.9.0"
-micronaut-validation = "4.11.0"
+micronaut-cache = "6.0.0-M3"
+micronaut-data = "5.0.0-M6"
+micronaut-hibernate-validator = "5.0.0-M1"
+micronaut-logging = "2.0.0-M2"
+micronaut-micrometer = "6.0.1-M1"
+micronaut-r2dbc = "7.0.1-M1"
+micronaut-reactor = "4.0.0-M2"
+micronaut-serde = "3.0.0-M7"
+micronaut-spring = "6.0.0-M2"
+micronaut-test = "5.0.0-M8"
+micronaut-validation = "5.0.0-M2"
 
 # Frameworks
 
-managed-vertx = "4.5.24"
-managed-jooq = "3.19.18"
-managed-hibernate = "6.6.49.Final"
-managed-hibernate-reactive = "2.4.17.Final"
+managed-vertx = "5.0.11"
+managed-jooq = "3.21.2"
+managed-hibernate = "7.3.2.Final"
+managed-hibernate-reactive = "4.3.3.Final"
 managed-jasync = "2.2.4"
-managed-jdbi = "3.49.6"
+managed-jdbi = "3.52.1"
 
 # JDBC Drivers
 
-managed-ojdbc = "23.9.0.25.07"
-managed-ojdbcdms = "21.19.0.0"
+managed-ojdbc = "23.26.1.0.0"
+managed-ojdbcdms = "21.21.0.0"
 managed-dms = "23.3.0.23.09"
-managed-postgres-driver = "42.7.8"
-managed-mariadb-driver = "3.5.6"
-managed-mssql-driver = "12.10.1.jre11"
+managed-postgres-driver = "42.7.10"
+managed-mariadb-driver = "3.5.8"
+managed-mssql-driver = "13.4.0.jre11"
 managed-mysql-driver = "8.0.33"
-managed-mysql-connector-j = "9.4.0"
+managed-mysql-connector-j = "9.6.0"
+managed-sqlite-jdbc = "3.53.0.0"
 
 # JDBC Pools
 
-managed-hikari = "6.3.3"
-managed-commons-dbcp = "2.13.0"
-managed-tomcat-jdbc = "11.0.12"
+managed-hikari = "7.0.2"
+managed-commons-dbcp = "2.14.0"
+managed-tomcat-jdbc = "11.0.21"
 
 # JPA
 
-managed-jakarta-persistence-api = "3.1.0"
+managed-jakarta-persistence-api = "3.2.0"
 managed-jakarta-transaction-api = "2.0.1"
 
-managed-h2 = "2.3.232"
+managed-h2 = "2.4.240"
 
 # Other
 
@@ -60,9 +59,7 @@
 managed-ongres-scram = "3.2"
 
 # Testing
-
-groovy = "4.0.11"
-sonar-gradle-plugin = "6.3.1.5724"
+sonar-gradle-plugin = "7.2.3.7755"
 
 [libraries]
 # Core
@@ -93,7 +90,9 @@
 managed-vertx-mssql-client = { module = "io.vertx:vertx-mssql-client", version.ref = "managed-vertx" }
 managed-vertx-oracle-client = { module = "io.vertx:vertx-oracle-client", version.ref = "managed-vertx" }
 managed-vertx-rx-java2 = { module = "io.vertx:vertx-rx-java2", version.ref = "managed-vertx" }
+managed-vertx-rx-java3 = { module = "io.vertx:vertx-rx-java3", version.ref = "managed-vertx" }
 
+boms-jooq = { module = "org.jooq:jooq-bom", version.ref = "managed-jooq" }
 managed-jooq = { module = "org.jooq:jooq", version.ref = "managed-jooq" }
 
 # Hibernate
@@ -135,6 +134,7 @@
 managed-mssql-jdbc = { module = "com.microsoft.sqlserver:mssql-jdbc", version.ref = "managed-mssql-driver" }
 managed-mysql-connector-java = { module = "mysql:mysql-connector-java", version.ref = "managed-mysql-driver" }
 managed-mysql-connector-j = { module = "com.mysql:mysql-connector-j", version.ref = "managed-mysql-connector-j" }
+managed-sqlite-jdbc = { module = "org.xerial:sqlite-jdbc", version.ref = "managed-sqlite-jdbc" }
 
 managed-ojdbc8 = { module = "com.oracle.database.jdbc:ojdbc8", version.ref = "managed-ojdbc" }
 managed-ojdbc11 = { module = "com.oracle.database.jdbc:ojdbc11", version.ref = "managed-ojdbc" }
```

### `gradle/wrapper/gradle-wrapper.properties`
```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/gradle/wrapper/gradle-wrapper.properties	2026-04-22 07:32:32.130595851 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/gradle/wrapper/gradle-wrapper.properties	2026-04-22 07:29:45.030497284 +0000
@@ -1,6 +1,6 @@
 distributionBase=GRADLE_USER_HOME
 distributionPath=wrapper/dists
-distributionUrl=https\://services.gradle.org/distributions/gradle-8.14.3-bin.zip
+distributionUrl=https\://services.gradle.org/distributions/gradle-9.4.1-bin.zip
 networkTimeout=10000
 validateDistributionUrl=true
 zipStoreBase=GRADLE_USER_HOME
```

### `gradle.properties`
```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/gradle.properties	2026-04-22 07:32:32.130121222 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/gradle.properties	2026-04-22 07:29:45.030031196 +0000
@@ -1,4 +1,4 @@
-projectVersion=6.3.5-SNAPSHOT
+projectVersion=7.0.0-SNAPSHOT
 projectGroup=io.micronaut.sql
 
 title=Micronaut SQL Libraries
@@ -7,6 +7,7 @@
 githubSlug=micronaut-projects/micronaut-sql
 developers=Graeme Rocher
 
+
 hibernateapi=https://docs.hibernate.org/orm/current/javadocs
 jdkapi=https://docs.oracle.com/en/java/javase/17/docs/api
 jooqapi=https://www.jooq.org/javadoc/latest
```

### `settings.gradle`
```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/settings.gradle	2026-04-22 07:32:32.166001044 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/settings.gradle	2026-04-22 07:29:45.072884997 +0000
@@ -6,7 +6,7 @@
 }
 
 plugins {
-    id 'io.micronaut.build.shared.settings' version '7.6.4'
+    id 'io.micronaut.build.shared.settings' version '8.0.0-M17'
 }
 
 enableFeaturePreview("TYPESAFE_PROJECT_ACCESSORS")
@@ -32,6 +32,7 @@
 include 'jdbc-dbcp'
 include 'jdbc-hikari'
 include 'jdbc-tomcat'
+include 'jdbc-unpooled'
 include 'jdbc-ucp'
 include 'jasync-sql'
 include 'hibernate-jpa'
@@ -48,25 +49,27 @@
 include 'tests:common-sync'
 include 'tests:common-tests'
 
-include 'tests:hibernate6:hibernate6-sync-common'
-include 'tests:hibernate6:hibernate6-h2'
-include 'tests:hibernate6:hibernate6-mariadb'
-include 'tests:hibernate6:hibernate6-mysql'
-include 'tests:hibernate6:hibernate6-mysql-disabled'
-include 'tests:hibernate6:hibernate6-mssql'
-include 'tests:hibernate6:hibernate6-oracle'
-include 'tests:hibernate6:hibernate6-postgres'
-
-include 'tests:hibernate6:hibernate6-reactive-common'
-include 'tests:hibernate6:hibernate6-reactive-mssql'
-include 'tests:hibernate6:hibernate6-reactive-mysql'
-include 'tests:hibernate6:hibernate6-reactive-oracle'
-include 'tests:hibernate6:hibernate6-reactive-postgres'
+include 'tests:hibernate:hibernate-sync-common'
+include 'tests:hibernate:hibernate-h2'
+include 'tests:hibernate:hibernate-mariadb'
+include 'tests:hibernate:hibernate-mysql'
+include 'tests:hibernate:hibernate-mysql-disabled'
+include 'tests:hibernate:hibernate-mssql'
+include 'tests:hibernate:hibernate-oracle'
+include 'tests:hibernate:hibernate-postgres'
+
+include 'tests:hibernate:hibernate-reactive-common'
+include 'tests:hibernate:hibernate-reactive-mssql'
+include 'tests:hibernate:hibernate-reactive-mysql'
+include 'tests:hibernate:hibernate-reactive-oracle'
+include 'tests:hibernate:hibernate-reactive-postgres'
 
 include 'tests:jooq-tests:jooq-jdbc-postgres'
 include 'tests:jooq-tests:jooq-r2dbc-postgres'
+include 'tests:vertx-pg-client-native'
 
 include 'tests:jdbc-ucp-tests:jdbc-ucp-oracle'
 include 'tests:jdbc-dbcp-tests:jdbc-dbcp-postgres'
-include 'tests:jdbc-tomcat-tests:jdbc-tomcat-mysql'
 include 'tests:jdbc-hikari-tests:jdbc-hikari-h2'
+include 'tests:jdbc-hikari-tests:jdbc-hikari-sqlite'
+include 'tests:jdbc-tomcat-tests:jdbc-tomcat-mysql'
```

---

## Added Files / Directories (only in B)

- `.agents/` (14 skill files under `agent-md-refactor`, `coding`, `docs`, `gradle`, `skill-creator`)
- `.github/workflows/sonatype.yml`
- `.sdkmanrc`
- `buildSrc/src/main/groovy/io.micronaut.build.internal.test-application-hibernate.gradle`
- `jdbc-unpooled/` (new module — `DatasourceFactory.java`, `DatasourceConfiguration.java`, `DriverManagerDataSource.java`, `package-info.java`, + 2 specs, build.gradle)
- `jdbc/src/main/java/io/micronaut/jdbc/CompositeDataSourceResolver.java`
- `jdbc/src/main/java/io/micronaut/jdbc/OracleSessionProgramHelper.java`
- `jdbc/src/test/groovy/io/micronaut/jdbc/CompositeDataSourceResolverSpec.groovy`
- `jdbc-dbcp/src/test/groovy/io/micronaut/configuration/jdbc/dbcp/OracleSessionProgramSpec.groovy`
- `jdbc-hikari/src/test/groovy/io/micronaut/configuration/jdbc/hikari/OracleSessionProgramSpec.groovy`
- `jdbc-tomcat/src/test/groovy/io/micronaut/configuration/jdbc/tomcat/OracleSessionProgramSpec.groovy`
- `jdbc-ucp/src/main/java/io/micronaut/configuration/jdbc/ucp/metadata/` (`OracleUcpDataSourcePoolMetadata.java`, `package-info.java`)
- `jdbc-ucp/src/test/groovy/io/micronaut/configuration/jdbc/ucp/ConnectionPoolManagerListenerSpec.groovy`
- `jdbc-ucp/src/test/groovy/io/micronaut/configuration/jdbc/ucp/OracleSessionProgramSpec.groovy`
- `jdbc-ucp/src/test/groovy/io/micronaut/configuration/jdbc/ucp/metadata/` (3 specs)
- `jdbc-ucp/src/test/groovy/io/micronaut/configuration/jdbc/ucp/test/` (`DataSourceWrapperBeanEventListener.java`, `TransactionAwareDataSourceProxyResolver.java`)
- `jooq/src/test/groovy/io/micronaut/configuration/jooq/R2dbcDslContextSpec.groovy`
- `src/main/docs/guide/jdbc/jdbc-runtime-password-update.adoc`
- `src/main/docs/guide/jooq/jooq-r2dbc.adoc`
- `tests/common/src/main/resources/META-INF/native-image/.../native-image.properties`
- `tests/hibernate/` (51 files — renamed from `tests/hibernate6/`, with package `example.hibernate6` → `example.hibernate`)
- `tests/jdbc-hikari-tests/jdbc-hikari-h2/src/main/java/example/jdbc/hikari/sync/CustomDataSourceFactory.java`
- `tests/jdbc-hikari-tests/jdbc-hikari-h2/src/main/java/example/jdbc/hikari/sync/CustomHikariUrlDataSource.java`
- `tests/jdbc-hikari-tests/jdbc-hikari-h2/src/test/java/example/jdbc/hikari/sync/CustomDataSourceFactoryTest.java`
- `tests/jdbc-hikari-tests/jdbc-hikari-h2/src/test/resources/logback-test.xml`
- `tests/jdbc-hikari-tests/jdbc-hikari-sqlite/` (new test module)
- `tests/vertx-pg-client-native/` (new native test module)
- `vertx-pg-client/src/main/java/io/micronaut/configuration/vertx/pg/client/PgClientRxJava3Factory.java`
- `vertx-pg-client/src/main/java/io/micronaut/configuration/vertx/pg/client/PgConnectOptionsResolver.java`
- `vertx-pg-client/src/main/java/io/micronaut/configuration/vertx/pg/client/PgPemTrustOptionsConfiguration.java`

## Removed Files / Directories (only in A)

- `buildSrc/src/main/groovy/io.micronaut.build.internal.test-application-hibernate6.gradle` (renamed to `…-test-application-hibernate.gradle`)
- `tests/common/src/main/resources/application.yml`
- `tests/hibernate6/` (51 files — renamed to `tests/hibernate/`)
- `tests/jdbc-hikari-tests/jdbc-hikari-h2/src/test/resources/logback.xml` (replaced by `logback-test.xml`)

---

## Modified Files

### `.clineignore`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/.clineignore	2026-04-22 07:32:32.126591065 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/.clineignore	2026-04-22 07:29:45.026717083 +0000
@@ -6,6 +6,8 @@
 */build/
 !build/docs/
 !build/docs/**
+!build/generated/
+!build/generated/**
 
 # === Dependency/Cache directories ===
 .gradle/
```

### `.clinerules/coding.md`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/.clinerules/coding.md	2026-04-22 07:32:32.126802400 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/.clinerules/coding.md	2026-04-22 07:29:45.026834876 +0000
@@ -41,7 +41,7 @@
 
 You SHOULD prefer modern Java idioms: records, pattern matching, sealed interfaces/classes, `var` for local variables.
 You MUST NOT use fully qualified class names unless there is a conflict between 2 class names in different packages.
-You MUST annotate the code with nullability annotations (`io.micronaut.core.annotation.Nullable`, `io.micronaut.core.annotation.NonNull`).
+You MUST annotate the code with nullability annotations (`org.jspecify.annotations.Nullable`, `org.jspecify.annotations.NonNull`).
 You MUST NOT use reflection: Micronaut is a reflection-free framework tailored for integration with GraalVM.
 You MUST use `jakarta.inject` for dependency injection, NOT `javax.inject`.
 
@@ -50,7 +50,7 @@
 Micronaut projects are intended to be used in consumer applications and therefore follow semantic versioning. As a consequence:
 - You MUST NOT break any public facing API without explicit consent
 - You SHOULD run the `./gradlew japiCmp` task to get a report about binary breaking changes
-- You SHOULD reduce the visibility of members for non user-facing APIs.
+- You SHOULD reduce the visibility of members for non-user-facing APIs.
 - You MUST annotate non-user facing APIs with `@io.micronaut.core.annotation.Internal`
 
 ## Implementation Workflow (Required Checklist)
@@ -71,9 +71,9 @@
     - Checkstyle: `./gradlew -q cM`
 
 5) (Optional) If, and only if you have created new files, you SHOULD run
-  - Spotless check: `./gradlew -q spotlessCheck`
-  - If Spotless fails: `./gradlew -q spotlessApply` then re-run `spotlessCheck`
-  - You MUST NOT add new license headers on existing files: only focus on files you have added
+    - Spotless check: `./gradlew -q spotlessCheck`
+    - If Spotless fails: `./gradlew -q spotlessApply` then re-run `spotlessCheck`
+    - You MUST NOT add new license headers on existing files: only focus on files you have added
 
 6) Verify a clean working tree
     - You SHOULD ensure no unrelated changes are pending before proposing changes.
@@ -165,7 +165,7 @@
 
 ## Key Requirements
 
-You MUST confirm all of the following BEFORE using `attempt_completion`:
+You MUST confirm all the following BEFORE using `attempt_completion`:
 
 - Changes compile successfully (affected modules)
 - Targeted tests pass
```

### `.clinerules/docs.md`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/.clinerules/docs.md	2026-04-22 07:32:32.126902943 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/.clinerules/docs.md	2026-04-22 07:29:45.026908293 +0000
@@ -1,9 +1,9 @@
 ## Brief overview
-- Documentation for the Micronaut modules is primarily written in Asciidoc format, focusing on user guides, API references, and integration examples. The documentation emphasizes clarity, completeness, and practical examples to help developers integrate Micronaut modules effectively. Insights from the codebase show a focus on modular documentation aligned with subprojects, including setup instructions, usage examples, and troubleshooting tips.
+- Documentation for the Micronaut modules is primarily written in AsciiDoc format, focusing on user guides, API references, and integration examples. The documentation emphasizes clarity, completeness, and practical examples to help developers integrate Micronaut modules effectively. Insights from the codebase show a focus on modular documentation aligned with subprojects, including setup instructions, usage examples, and troubleshooting tips.
 - All the files are within `src/main/docs/guide`. In that directory, there is a `toc.yml` file that is used to generate the table of contents and decide which `.adoc` files are to be included.
 
 ## Development workflow
-- Write documentation in Asciidoc: Place source files in the appropriate `src/main/docs` directory.
+- Write documentation in AsciiDoc: Place source files in the appropriate `src/main/docs` directory.
 - Build and assemble the documentation guide: Use `./gradlew docs` from the root directory to generate HTML documentation. Since the output of this task may be huge, ignore the output and check the last process exit code to tell if it works. Otherwise, ask the user. If it works, verify the output for formatting and content accuracy.
 - Once assembled, the guide will be at `build/docs/`.
 - Include examples: Create and reference code examples from the doc-examples/ directory, ensuring they are testable and up-to-date with the latest service versions.
@@ -11,7 +11,7 @@
 - Review and update: Conduct peer reviews for new documentation or changes, ensuring alignment with coding standards and project updates.
 
 ## Documentation best practices
-- Follow Asciidoc conventions: Use consistent headings, lists, code blocks, and admonitions (e.g., NOTE, TIP, WARNING) for better readability.
+- Follow AsciiDoc conventions: Use consistent headings, lists, code blocks, and admonitions (e.g., NOTE, TIP, WARNING) for better readability.
 - Provide comprehensive coverage: Include installation instructions, configuration details, usage examples, error handling, and performance tips for each service.
 - Use practical examples: Incorporate runnable code snippets from doc-examples/ to demonstrate real-world usage, with clear explanations and expected outputs.
 - Ensure accessibility: Use descriptive alt text for images, maintain logical structure, and avoid jargon without explanations.
```

### `.github/instructions/coding.instructions.md`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/.github/instructions/coding.instructions.md	2026-04-22 07:32:32.127719159 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/.github/instructions/coding.instructions.md	2026-04-22 07:29:45.027488799 +0000
@@ -41,7 +41,7 @@
 
 You SHOULD prefer modern Java idioms: records, pattern matching, sealed interfaces/classes, `var` for local variables.
 You MUST NOT use fully qualified class names unless there is a conflict between 2 class names in different packages.
-You MUST annotate the code with nullability annotations (`io.micronaut.core.annotation.Nullable`, `io.micronaut.core.annotation.NonNull`).
+You MUST annotate the code with nullability annotations (`org.jspecify.annotations.Nullable`, `org.jspecify.annotations.NonNull`).
 You MUST NOT use reflection: Micronaut is a reflection-free framework tailored for integration with GraalVM.
 You MUST use `jakarta.inject` for dependency injection, NOT `javax.inject`.
 
@@ -50,7 +50,7 @@
 Micronaut projects are intended to be used in consumer applications and therefore follow semantic versioning. As a consequence:
 - You MUST NOT break any public facing API without explicit consent
 - You SHOULD run the `./gradlew japiCmp` task to get a report about binary breaking changes
-- You SHOULD reduce the visibility of members for non user-facing APIs.
+- You SHOULD reduce the visibility of members for non-user-facing APIs.
 - You MUST annotate non-user facing APIs with `@io.micronaut.core.annotation.Internal`
 
 ## Implementation Workflow (Required Checklist)
@@ -71,9 +71,9 @@
     - Checkstyle: `./gradlew -q cM`
 
 5) (Optional) If, and only if you have created new files, you SHOULD run
-  - Spotless check: `./gradlew -q spotlessCheck`
-  - If Spotless fails: `./gradlew -q spotlessApply` then re-run `spotlessCheck`
-  - You MUST NOT add new license headers on existing files: only focus on files you have added
+    - Spotless check: `./gradlew -q spotlessCheck`
+    - If Spotless fails: `./gradlew -q spotlessApply` then re-run `spotlessCheck`
+    - You MUST NOT add new license headers on existing files: only focus on files you have added
 
 6) Verify a clean working tree
     - You SHOULD ensure no unrelated changes are pending before proposing changes.
@@ -165,7 +165,7 @@
 
 ## Key Requirements
 
-You MUST confirm all of the following BEFORE using `attempt_completion`:
+You MUST confirm all the following BEFORE using `attempt_completion`:
 
 - Changes compile successfully (affected modules)
 - Targeted tests pass
```

### `.github/instructions/docs.instructions.md`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/.github/instructions/docs.instructions.md	2026-04-22 07:32:32.127814951 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/.github/instructions/docs.instructions.md	2026-04-22 07:29:45.027563299 +0000
@@ -1,9 +1,9 @@
 ## Brief overview
-- Documentation for the Micronaut modules is primarily written in Asciidoc format, focusing on user guides, API references, and integration examples. The documentation emphasizes clarity, completeness, and practical examples to help developers integrate Micronaut modules effectively. Insights from the codebase show a focus on modular documentation aligned with subprojects, including setup instructions, usage examples, and troubleshooting tips.
+- Documentation for the Micronaut modules is primarily written in AsciiDoc format, focusing on user guides, API references, and integration examples. The documentation emphasizes clarity, completeness, and practical examples to help developers integrate Micronaut modules effectively. Insights from the codebase show a focus on modular documentation aligned with subprojects, including setup instructions, usage examples, and troubleshooting tips.
 - All the files are within `src/main/docs/guide`. In that directory, there is a `toc.yml` file that is used to generate the table of contents and decide which `.adoc` files are to be included.
 
 ## Development workflow
-- Write documentation in Asciidoc: Place source files in the appropriate `src/main/docs` directory.
+- Write documentation in AsciiDoc: Place source files in the appropriate `src/main/docs` directory.
 - Build and assemble the documentation guide: Use `./gradlew docs` from the root directory to generate HTML documentation. Since the output of this task may be huge, ignore the output and check the last process exit code to tell if it works. Otherwise, ask the user. If it works, verify the output for formatting and content accuracy.
 - Once assembled, the guide will be at `build/docs/`.
 - Include examples: Create and reference code examples from the doc-examples/ directory, ensuring they are testable and up-to-date with the latest service versions.
@@ -11,7 +11,7 @@
 - Review and update: Conduct peer reviews for new documentation or changes, ensuring alignment with coding standards and project updates.
 
 ## Documentation best practices
-- Follow Asciidoc conventions: Use consistent headings, lists, code blocks, and admonitions (e.g., NOTE, TIP, WARNING) for better readability.
+- Follow AsciiDoc conventions: Use consistent headings, lists, code blocks, and admonitions (e.g., NOTE, TIP, WARNING) for better readability.
 - Provide comprehensive coverage: Include installation instructions, configuration details, usage examples, error handling, and performance tips for each service.
 - Use practical examples: Incorporate runnable code snippets from doc-examples/ to demonstrate real-world usage, with clear explanations and expected outputs.
 - Ensure accessibility: Use descriptive alt text for images, maintain logical structure, and avoid jargon without explanations.
```

### `.github/renovate.json`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/.github/renovate.json	2026-04-22 07:32:32.127979828 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/.github/renovate.json	2026-04-22 07:29:45.027689759 +0000
@@ -19,9 +19,18 @@
       ],
       "matchCurrentVersion": "!/^0/",
       "automerge": true,
-      "matchPackageNames": [
-        "/actions.*/"
-      ]
+      "matchManagers": ["github-actions"],
+      "groupName": "GitHub Actions dependencies"
+    },
+    {
+      "matchDatasources": [
+        "maven"
+      ],
+      "matchManagers": [
+        "maven",
+        "gradle"
+      ],
+      "allowedVersions": "!/.+-SNAPSHOT$/"
     },
     {
       "matchUpdateTypes": [
@@ -29,6 +38,12 @@
       ],
       "matchCurrentVersion": "!/^0/",
       "automerge": true
+    },
+    {
+      "matchPackageNames": [
+        "/.*micronaut.*/"
+      ],
+      "groupName": "Micronaut dependencies"
     }
   ]
 }
```

### `.github/workflows/central-sync.yml`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/.github/workflows/central-sync.yml	2026-04-22 07:32:32.128131204 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/.github/workflows/central-sync.yml	2026-04-22 07:29:45.027806176 +0000
@@ -14,18 +14,22 @@
   central-sync:
     runs-on: ubuntu-latest
     steps:
+      - name: Remove system JDKs
+        run: |
+          sudo rm -rf /usr/lib/jvm/*
+          unset JAVA_HOME
+          export PATH=$(echo "$PATH" | tr ':' '\n' | grep -v '/usr/lib/jvm' | paste -sd:)
       - name: Checkout repository
-        uses: actions/checkout@v5
+        uses: actions/checkout@de0fac2e4500dabe0009e67214ff5f5447ce83dd # v6
         with:
           ref: v${{ github.event.inputs.release_version }}
-      - uses: gradle/actions/wrapper-validation@v4
+      - uses: gradle/actions/wrapper-validation@50e97c2cd7a37755bbfafc9c5b7cafaece252f6e # v6
       - name: Set up JDK
-        uses: actions/setup-java@v5
+        uses: actions/setup-java@be666c2fcd27ec809703dec50e508c2fdc7f6654 # v5
         with:
           distribution: 'temurin'
           java-version: |
-            17
-            21
+            25
       - name: Publish to Sonatype OSSRH
         env:
           SONATYPE_USERNAME: ${{ secrets.SONATYPE_USERNAME }}
```

### `.github/workflows/graalvm-dev.yml`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/.github/workflows/graalvm-dev.yml	2026-04-22 07:32:32.128214871 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/.github/workflows/graalvm-dev.yml	2026-04-22 07:29:45.027886385 +0000
@@ -18,9 +18,9 @@
     outputs:
       matrix: ${{ steps.build-matrix.outputs.matrix }}
     steps:
-      - uses: actions/checkout@v5
+      - uses: actions/checkout@de0fac2e4500dabe0009e67214ff5f5447ce83dd # v6
       - name: Build Matrix
-        uses: micronaut-projects/github-actions/graalvm/build-matrix@master
+        uses: micronaut-projects/github-actions/graalvm/build-matrix@300bf6db7c062dcba77c90bb90e475df31b2acab # master
         id: build-matrix
   build:
     needs: build_matrix
@@ -42,15 +42,21 @@
       DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
       DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
     steps:
-      - uses: actions/checkout@v5
+      - name: Remove system JDKs
+        run: |
+          sudo rm -rf /usr/lib/jvm/*
+          unset JAVA_HOME
+          export PATH=$(echo "$PATH" | tr ':' '\n' | grep -v '/usr/lib/jvm' | paste -sd:)
+      - uses: actions/checkout@de0fac2e4500dabe0009e67214ff5f5447ce83dd # v6
       - name: Pre-Build Steps
-        uses: micronaut-projects/github-actions/graalvm/pre-build@master
+        uses: micronaut-projects/github-actions/graalvm/pre-build@300bf6db7c062dcba77c90bb90e475df31b2acab # master
         id: pre-build
         with:
           java: ${{ matrix.java }}
           distribution: ${{ matrix.distribution }}
+          nativeTestTask: ${{ matrix.native_test_task }}
       - name: Build Steps
-        uses: micronaut-projects/github-actions/graalvm/build@master
+        uses: micronaut-projects/github-actions/graalvm/build@300bf6db7c062dcba77c90bb90e475df31b2acab # master
         id: build
         env:
           GH_TOKEN_PUBLIC_REPOS_READONLY: ${{ secrets.GH_TOKEN_PUBLIC_REPOS_READONLY }}
@@ -59,7 +65,7 @@
         with:
           nativeTestTask: ${{ matrix.native_test_task }}
       - name: Post-Build Steps
-        uses: micronaut-projects/github-actions/graalvm/post-build@master
+        uses: micronaut-projects/github-actions/graalvm/post-build@300bf6db7c062dcba77c90bb90e475df31b2acab # master
         id: post-build
         with:
           java: ${{ matrix.java }}
```

### `.github/workflows/graalvm-latest.yml`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/.github/workflows/graalvm-latest.yml	2026-04-22 07:32:32.128284955 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/.github/workflows/graalvm-latest.yml	2026-04-22 07:29:45.027944969 +0000
@@ -8,26 +8,28 @@
   push:
     branches:
       - master
-      - '[1-9]+.[0-9]+.x'
+      - '[0-9]+.[0-9]+.x'
   pull_request:
     branches:
       - master
-      - '[1-9]+.[0-9]+.x'
+      - '[0-9]+.[0-9]+.x'
 jobs:
   build_matrix:
     if: github.repository != 'micronaut-projects/micronaut-project-template'
     runs-on: ubuntu-latest
-    env:
-      DEVELOCITY_ACCESS_KEY: ${{ secrets.GRADLE_ENTERPRISE_ACCESS_KEY }}
-      DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
-      DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
     outputs:
       matrix: ${{ steps.build-matrix.outputs.matrix }}
     steps:
-      - uses: actions/checkout@v5
+      - uses: actions/checkout@de0fac2e4500dabe0009e67214ff5f5447ce83dd # v6
       - name: Build Matrix
-        uses: micronaut-projects/github-actions/graalvm/build-matrix@master
+        uses: micronaut-projects/github-actions/graalvm/build-matrix@300bf6db7c062dcba77c90bb90e475df31b2acab # master
         id: build-matrix
+        env:
+          DEVELOCITY_ACCESS_KEY: ${{ secrets.GRADLE_ENTERPRISE_ACCESS_KEY }}
+          DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
+          DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
+        with:
+          java-version: '25'
   build:
     needs: build_matrix
     if: github.repository != 'micronaut-projects/micronaut-project-template'
@@ -35,31 +37,45 @@
     strategy:
       max-parallel: 6
       matrix:
-        java: ['17', '21']
+        java: ['25']
         native_test_task: ${{ fromJson(needs.build_matrix.outputs.matrix).native_test_task }}
-    env:
-      DEVELOCITY_ACCESS_KEY: ${{ secrets.GRADLE_ENTERPRISE_ACCESS_KEY }}
-      DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
-      DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
     steps:
-      - uses: actions/checkout@v5
+      - name: Remove system JDKs
+        run: |
+          sudo rm -rf /usr/lib/jvm/*
+          unset JAVA_HOME
+          export PATH=$(echo "$PATH" | tr ':' '\n' | grep -v '/usr/lib/jvm' | paste -sd:)
+      - uses: actions/checkout@de0fac2e4500dabe0009e67214ff5f5447ce83dd # v6
       - name: Pre-Build Steps
-        uses: micronaut-projects/github-actions/graalvm/pre-build@master
+        uses: micronaut-projects/github-actions/graalvm/pre-build@300bf6db7c062dcba77c90bb90e475df31b2acab # master
         id: pre-build
+        env:
+          DEVELOCITY_ACCESS_KEY: ${{ secrets.GRADLE_ENTERPRISE_ACCESS_KEY }}
+          DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
+          DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
         with:
           distribution: 'graalvm'
+          gradle-java: '25'
           java: ${{ matrix.java }}
+          nativeTestTask: ${{ matrix.native_test_task }}
       - name: Build Steps
-        uses: micronaut-projects/github-actions/graalvm/build@master
+        uses: micronaut-projects/github-actions/graalvm/build@300bf6db7c062dcba77c90bb90e475df31b2acab # master
         id: build
         env:
+          DEVELOCITY_ACCESS_KEY: ${{ secrets.GRADLE_ENTERPRISE_ACCESS_KEY }}
+          DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
+          DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
           GH_TOKEN_PUBLIC_REPOS_READONLY: ${{ secrets.GH_TOKEN_PUBLIC_REPOS_READONLY }}
           GH_USERNAME: ${{ secrets.GH_USERNAME }}
           GRAALVM_QUICK_BUILD: true
         with:
           nativeTestTask: ${{ matrix.native_test_task }}
       - name: Post-Build Steps
-        uses: micronaut-projects/github-actions/graalvm/post-build@master
+        uses: micronaut-projects/github-actions/graalvm/post-build@300bf6db7c062dcba77c90bb90e475df31b2acab # master
         id: post-build
+        env:
+          DEVELOCITY_ACCESS_KEY: ${{ secrets.GRADLE_ENTERPRISE_ACCESS_KEY }}
+          DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
+          DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
         with:
           java: ${{ matrix.java }}
```

### `.github/workflows/gradle.yml`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/.github/workflows/gradle.yml	2026-04-22 07:32:32.128357706 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/.github/workflows/gradle.yml	2026-04-22 07:29:45.028021970 +0000
@@ -8,98 +8,107 @@
   push:
     branches:
       - master
-      - '[1-9]+.[0-9]+.x'
+      - '[0-9]+.[0-9]+.x'
   pull_request:
     branches:
       - master
-      - '[1-9]+.[0-9]+.x'
+      - '[0-9]+.[0-9]+.x'
 jobs:
   build:
     if: github.repository != 'micronaut-projects/micronaut-project-template'
     runs-on: ubuntu-latest
     strategy:
       matrix:
-        java: ['17', '21']
+        java: ['25']
     env:
-      DEVELOCITY_ACCESS_KEY: ${{ secrets.GRADLE_ENTERPRISE_ACCESS_KEY }}
-      DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
-      DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
-      GH_TOKEN_PUBLIC_REPOS_READONLY: ${{ secrets.GH_TOKEN_PUBLIC_REPOS_READONLY }}
-      GH_USERNAME: ${{ secrets.GH_USERNAME }}
       TESTCONTAINERS_RYUK_DISABLED: true
-      PREDICTIVE_TEST_SELECTION: "${{ github.event_name == 'pull_request' && 'true' || 'false' }}"
-      SONAR_TOKEN: ${{ secrets.SONAR_TOKEN }}
-      GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
-      OSS_INDEX_USERNAME: ${{ secrets.OSS_INDEX_USERNAME }}
-      OSS_INDEX_PASSWORD: ${{ secrets.OSS_INDEX_PASSWORD }}
+      SONAR_TOKEN_AVAILABLE: ${{ secrets.SONAR_TOKEN != '' }}
     steps:
        # https://github.com/actions/virtual-environments/issues/709
+      - name: Remove system JDKs
+        run: |
+          sudo rm -rf /usr/lib/jvm/*
+          unset JAVA_HOME
+          export PATH=$(echo "$PATH" | tr ':' '\n' | grep -v '/usr/lib/jvm' | paste -sd:)
       - name: "🗑 Free disk space"
         run: |
          sudo rm -rf "/usr/local/share/boost"
          sudo rm -rf "$AGENT_TOOLSDIRECTORY"
+         sudo rm -rf "/opt/ghc"
+         sudo rm -rf "/usr/share/dotnet"
+         sudo rm -rf "/usr/local/lib/android"
          sudo apt-get clean
          df -h
 
       - name: "📥 Checkout repository"
-        uses: actions/checkout@v5
+        uses: actions/checkout@de0fac2e4500dabe0009e67214ff5f5447ce83dd # v6
         with:
           fetch-depth: 0
 
       - name: "🔧 Setup GraalVM CE"
-        uses: graalvm/setup-graalvm@v1.4.1
+        uses: graalvm/setup-graalvm@60c26726de13f8b90771df4bc1641a52a3159994 # v1
         with:
           distribution: 'graalvm'
           java-version: ${{ matrix.java }}
           github-token: ${{ secrets.GITHUB_TOKEN }}
 
       - name: "🔧 Setup Gradle"
-        uses: gradle/actions/setup-gradle@v4
+        uses: gradle/actions/setup-gradle@50e97c2cd7a37755bbfafc9c5b7cafaece252f6e # v6
 
       - name: "❓ Optional setup step"
         run: |
           [ -f ./setup.sh ] && ./setup.sh || [ ! -f ./setup.sh ]
 
-      - name: "🚔 Sonatype Scan"
-        if: env.OSS_INDEX_PASSWORD != '' && matrix.java == '17'
-        id: sonatypescan
-        run: |
-          ./gradlew ossIndexAudit --no-parallel --info
-
       - name: "🛠 Build with Gradle"
         id: gradle
+        env:
+          DEVELOCITY_ACCESS_KEY: ${{ secrets.GRADLE_ENTERPRISE_ACCESS_KEY }}
+          DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
+          DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
+          GH_TOKEN_PUBLIC_REPOS_READONLY: ${{ secrets.GH_TOKEN_PUBLIC_REPOS_READONLY }}
+          GH_USERNAME: ${{ secrets.GH_USERNAME }}
+          OSS_INDEX_USERNAME: ${{ secrets.OSS_INDEX_USERNAME }}
+          OSS_INDEX_PASSWORD: ${{ secrets.OSS_INDEX_PASSWORD }}
         run: |
-          ./gradlew jacocoReport check --no-daemon --continue
+          ./gradlew check jacocoReport --no-daemon --continue
 
       - name: "🔎 Run static analysis"
-        if: env.SONAR_TOKEN != '' && matrix.java == '17'
+        if: env.SONAR_TOKEN_AVAILABLE == 'true' && matrix.java == '25'
+        env:
+          DEVELOCITY_ACCESS_KEY: ${{ secrets.GRADLE_ENTERPRISE_ACCESS_KEY }}
+          DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
+          DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
+          SONAR_TOKEN: ${{ secrets.SONAR_TOKEN }}
         run: |
           ./gradlew sonar --no-parallel --continue
 
       - name: "📊 Publish Test Report"
         if: always()
-        uses: mikepenz/action-junit-report@v5
+        uses: mikepenz/action-junit-report@bccf2e31636835cf0874589931c4116687171386 # v6
         with:
           check_name: Java CI / Test Report (${{ matrix.java }})
           report_paths: '**/build/test-results/test/TEST-*.xml'
           check_retries: 'true'
 
       - name: "📜 Upload binary compatibility check results"
-        if: matrix.java == '17'
-        uses: actions/upload-artifact@65c4c4a1ddee5b72f698fdd19549f0f0fb45cf08 # v4.6.0
+        if: matrix.java == '25'
+        uses: actions/upload-artifact@043fb46d1a93c77aae656e7c1c64a875d1fc6a0a # v7
         with:
           name: binary-compatibility-reports
           path: "**/build/reports/binary-compatibility-*.html"
 
       - name: "📦 Publish to Sonatype Snapshots"
-        if: success() && github.event_name == 'push' && matrix.java == '17'
+        if: success() && github.event_name == 'push' && matrix.java == '25'
         env:
+          DEVELOCITY_ACCESS_KEY: ${{ secrets.GRADLE_ENTERPRISE_ACCESS_KEY }}
+          DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
+          DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
           SONATYPE_USERNAME: ${{ secrets.SONATYPE_USERNAME }}
           SONATYPE_PASSWORD: ${{ secrets.SONATYPE_PASSWORD }}
         run: ./gradlew publishToSonatype docs --no-daemon
 
       - name: "❓ Determine docs target repository"
-        uses: haya14busa/action-cond@v1
+        uses: haya14busa/action-cond@94f77f7a80cd666cb3155084e428254fea4281fd # v1
         id: docs_target
         with:
           cond: ${{ github.repository == 'micronaut-projects/micronaut-core' }}
@@ -107,10 +116,14 @@
           if_false: ${{ github.repository }}
 
       - name: "📑 Publish to Github Pages"
-        if: success() && github.event_name == 'push' && matrix.java == '17'
-        uses: micronaut-projects/github-pages-deploy-action@master
+        if: success() && github.event_name == 'push' && matrix.java == '25'
+        uses: micronaut-projects/github-pages-deploy-action@76d63aafbab7108d74e83be4e5b3b0501382e829 # master
         env:
           TARGET_REPOSITORY: ${{ steps.docs_target.outputs.value }}
           GH_TOKEN: ${{ secrets.GH_TOKEN }}
           BRANCH: gh-pages
           FOLDER: build/docs
+
+      - name: "❓ Optional cleanup step"
+        run: |
+          [ -f ./cleanup.sh ] && ./cleanup.sh || [ ! -f ./cleanup.sh ]
```

### `.github/workflows/publish-snapshot.yml`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/.github/workflows/publish-snapshot.yml	2026-04-22 07:32:32.128425082 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/.github/workflows/publish-snapshot.yml	2026-04-22 07:29:45.028095637 +0000
@@ -10,20 +10,24 @@
     if: github.repository != 'micronaut-projects/micronaut-project-template'
     runs-on: ubuntu-latest
     steps:
-      - uses: actions/checkout@v5
-      - uses: actions/cache@v4
+      - name: Remove system JDKs
+        run: |
+          sudo rm -rf /usr/lib/jvm/*
+          unset JAVA_HOME
+          export PATH=$(echo "$PATH" | tr ':' '\n' | grep -v '/usr/lib/jvm' | paste -sd:)
+      - uses: actions/checkout@de0fac2e4500dabe0009e67214ff5f5447ce83dd # v6
+      - uses: actions/cache@27d5ce7f107fe9357f9df03efb73ab90386fccae # v5
         with:
           path: ~/.gradle/caches
           key: ${{ runner.os }}-gradle-${{ hashFiles('**/*.gradle') }}
           restore-keys: |
             ${{ runner.os }}-gradle-
       - name: Set up JDK
-        uses: actions/setup-java@v5
+        uses: actions/setup-java@be666c2fcd27ec809703dec50e508c2fdc7f6654 # v5
         with:
           distribution: 'temurin'
           java-version: |
-            17
-            21
+            25
       - name: Publish to Sonatype Snapshots
         if: success()
         env:
```

### `.github/workflows/release.yml`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/.github/workflows/release.yml	2026-04-22 07:32:32.128489041 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/.github/workflows/release.yml	2026-04-22 07:29:45.028181346 +0000
@@ -13,23 +13,27 @@
       artifacts-sha256: ${{ steps.hash.outputs.artifacts-sha256 }} # Computed hashes for build artifacts.
     runs-on: ubuntu-latest
     steps:
+      - name: Remove system JDKs
+        run: |
+          sudo rm -rf /usr/lib/jvm/*
+          unset JAVA_HOME
+          export PATH=$(echo "$PATH" | tr ':' '\n' | grep -v '/usr/lib/jvm' | paste -sd:)
       - name: Checkout repository
-        uses: actions/checkout@v5
+        uses: actions/checkout@de0fac2e4500dabe0009e67214ff5f5447ce83dd # v6
         with:
           token: ${{ secrets.GH_TOKEN }}
-      - uses: gradle/actions/wrapper-validation@v4
+      - uses: gradle/actions/wrapper-validation@50e97c2cd7a37755bbfafc9c5b7cafaece252f6e # v6
       - name: Set up JDK
-        uses: actions/setup-java@v5
+        uses: actions/setup-java@be666c2fcd27ec809703dec50e508c2fdc7f6654 # v5
         with:
           distribution: 'temurin'
           java-version: |
-            17
-            21
+            25
       - name: Set the current release version
         id: release_version
         run: echo "release_version=${GITHUB_REF:11}" >> $GITHUB_OUTPUT
       - name: Run pre-release
-        uses: micronaut-projects/github-actions/pre-release@master
+        uses: micronaut-projects/github-actions/pre-release@300bf6db7c062dcba77c90bb90e475df31b2acab # master
         env:
           MICRONAUT_BUILD_EMAIL: ${{ secrets.MICRONAUT_BUILD_EMAIL }}
         with:
@@ -68,13 +72,13 @@
           # Store the hash in a file, which is uploaded as a workflow artifact.
           sha256sum $ARTIFACTS | base64 -w0 > artifacts-sha256
       - name: Upload build artifacts
-        uses: actions/upload-artifact@65c4c4a1ddee5b72f698fdd19549f0f0fb45cf08 # v4.6.0
+        uses: actions/upload-artifact@043fb46d1a93c77aae656e7c1c64a875d1fc6a0a # v7.0.1
         with:
           name: gradle-build-outputs
           path: build/repo/${{ steps.publish.outputs.group }}/*/${{ steps.publish.outputs.version }}/*
           retention-days: 5
       - name: Upload artifacts-sha256
-        uses: actions/upload-artifact@65c4c4a1ddee5b72f698fdd19549f0f0fb45cf08 # v4.6.0
+        uses: actions/upload-artifact@043fb46d1a93c77aae656e7c1c64a875d1fc6a0a # v7.0.1
         with:
           name: artifacts-sha256
           path: artifacts-sha256
@@ -88,12 +92,15 @@
           GH_TOKEN_PUBLIC_REPOS_READONLY: ${{ secrets.GH_TOKEN_PUBLIC_REPOS_READONLY }}
           GH_USERNAME: ${{ secrets.GH_USERNAME }}
       - name: Export Gradle Properties
-        uses: micronaut-projects/github-actions/export-gradle-properties@master
+        uses: micronaut-projects/github-actions/export-gradle-properties@300bf6db7c062dcba77c90bb90e475df31b2acab # master
+      - name: LATEST_TAG
+        run: |
+          echo "LATEST_TAG=$(curl -s -L -H 'Accept: application/vnd.github+json' -H 'X-GitHub-Api-Version: 2022-11-28' https://api.github.com/repos/${{ github.repository }}/releases/latest | jq -r '.tag_name')" >> $GITHUB_ENV
       - name: Publish to Github Pages
         if: success()
-        uses: micronaut-projects/github-pages-deploy-action@master
+        uses: micronaut-projects/github-pages-deploy-action@76d63aafbab7108d74e83be4e5b3b0501382e829 # master
         env:
-          BETA: ${{ !(github.event.release.target_commitish == github.event.repository.default_branch) || contains(steps.release_version.outputs.release_version, 'M') || contains(steps.release_version.outputs.release_version, 'RC') }}
+          BETA: ${{ !(github.event.release.tag_name == env.LATEST_TAG) || github.event.release.draft || github.event.release.prerelease || contains(steps.release_version.outputs.release_version, 'M') || contains(steps.release_version.outputs.release_version, 'RC') }}
           GH_TOKEN: ${{ secrets.GH_TOKEN }}
           BRANCH: gh-pages
           FOLDER: build/docs
@@ -104,7 +111,7 @@
           DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
       - name: Run post-release
         if: success()
-        uses: micronaut-projects/github-actions/post-release@master
+        uses: micronaut-projects/github-actions/post-release@300bf6db7c062dcba77c90bb90e475df31b2acab # master
         env:
           MICRONAUT_BUILD_EMAIL: ${{ secrets.MICRONAUT_BUILD_EMAIL }}
         with:
@@ -117,7 +124,7 @@
       artifacts-sha256: ${{ steps.set-hash.outputs.artifacts-sha256 }}
     steps:
       - name: Download artifacts-sha256
-        uses: actions/download-artifact@634f93cb2916e3fdff6788551b99b062d0335ce0 # v5.0.0
+        uses: actions/download-artifact@3e5f45b2cfb9172054b4087a40e8e0b5a5461e7c # v8.0.1
         with:
           name: artifacts-sha256
       # The SLSA provenance generator expects the hash digest of artifacts to be passed as a job
@@ -136,7 +143,7 @@
       actions: read # To read the workflow path.
       id-token: write # To sign the provenance.
       contents: write # To add assets to a release.
-    uses: slsa-framework/slsa-github-generator/.github/workflows/generator_generic_slsa3.yml@v2.1.0
+    uses: slsa-framework/slsa-github-generator/.github/workflows/generator_generic_slsa3.yml@f7dd8c54c2067bafc12ca7a55595d5ee9b75204a # v2.1.0
     with:
       base64-subjects: "${{ needs.provenance-subject.outputs.artifacts-sha256 }}"
       upload-assets: true # Upload to a new release.
@@ -148,9 +155,11 @@
     if: startsWith(github.ref, 'refs/tags/')
     steps:
       - name: Checkout repository
-        uses: actions/checkout@08c6903cd8c0fde910a37f88322edcfb5dd907a8 # v5.0.0
+        uses: actions/checkout@de0fac2e4500dabe0009e67214ff5f5447ce83dd # v6.0.2
+        with:
+          ref: ${{ github.sha }}
       - name: Download artifacts
-        uses: actions/download-artifact@634f93cb2916e3fdff6788551b99b062d0335ce0 # v5.0.0
+        uses: actions/download-artifact@3e5f45b2cfb9172054b4087a40e8e0b5a5461e7c # v8.0.1
         with:
           name: gradle-build-outputs
           path: build/repo
@@ -162,6 +171,6 @@
       - name: Upload assets
         # Upload the artifacts to the existing release. Note that the SLSA provenance will
         # attest to each artifact file and not the aggregated ZIP file.
-        uses: softprops/action-gh-release@72f2c25fcb47643c292f7107632f7a47c1df5cd8 # v2.3.2
+        uses: softprops/action-gh-release@b4309332981a82ec1c5618f44dd2e27cc8bfbfda # v3.0.0
         with:
           files: artifacts.zip
```

### `.gitignore`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/.gitignore	2026-04-22 07:32:32.128547333 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/.gitignore	2026-04-22 07:29:45.028304222 +0000
@@ -34,3 +34,9 @@
 
 # Ignore files generated by test-resources
 **/.micronaut/test-resources/
+
+# Ignore gradle.properties generated by micronaut-build
+/buildSrc/gradle.properties
+
+# OpenCode files
+.sisyphus/
```

### `MAINTAINING.md`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/MAINTAINING.md	2026-04-22 07:32:32.128796502 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/MAINTAINING.md	2026-04-22 07:29:45.028623017 +0000
@@ -2,7 +2,7 @@
 
 ## Triage incoming issues
 
-New issues need to be categorised. At least with one of the following labels:
+New issues need to be categorized. At least with one of the following labels:
 
 * `type: bug`: when something is not working as designed.
 * `type: improvement`: a minor improvement over an existing feature.
@@ -38,7 +38,7 @@
   revisited in the future.
 * `status: next major version`: it is a breaking change and therefore needs to be implemented in the next major version.
 
-There are also a bunch of `relates-to` labels that can be used to further categorise issues. This is helpful in projects
+There are also a bunch of `relates-to` labels that can be used to further categorize issues. This is helpful in projects
 with a lot of issues, or projects where different people work on different parts or modules.
 
 The majority of the issues are defined in the
@@ -48,7 +48,7 @@
 * If they can be beneficial to several repos, send a pull request to the management repo.
 * If they are repo-specific, just go ahead and create them with the GitHub UI.
 
-Finally, issues (especially bugs) should be prioritised with either `priority: high`, `priority: medium` or
+Finally, issues (especially bugs) should be prioritized with either `priority: high`, `priority: medium` or
 `priority: low`. Checkout the
 [Issue Priority Labels](https://github.com/micronaut-projects/micronaut-core/wiki/Issue-Priority-Labels) document for
 guidelines about when to use each of them.
@@ -146,8 +146,8 @@
 The "Java CI" (`gradle.yml`) workflow does have the ability to have an optional setup step, though. If there is a `setup.sh`
 file in the project root, it will be executed before invoking Gradle.
 
-There are projects, such as micronaut-gcp and micronaut-kubernetes, that have made customisations to sync'ed workflows
-because it's absolutely necessary. In those projects, the sync pull requests are manually merged so that the customisations
+There are projects, such as micronaut-gcp and micronaut-kubernetes, that have made customizations to sync'ed workflows
+because it's absolutely necessary. In those projects, the sync pull requests are manually merged so that the customizations
 aren't lost.
 
 Note that it is perfectly possible to have new workflows that aren't part of the sync process.
```

### `buildSrc/src/main/groovy/io.micronaut.build.internal.sql-module.gradle`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/buildSrc/src/main/groovy/io.micronaut.build.internal.sql-module.gradle	2026-04-22 07:32:32.129391257 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/buildSrc/src/main/groovy/io.micronaut.build.internal.sql-module.gradle	2026-04-22 07:29:45.029255356 +0000
@@ -5,7 +5,12 @@
 
 ossIndexAudit {
     excludeCoordinates = [
-            "org.hibernate.reactive:hibernate-reactive-core:2.4.17.Final", // no 2.14.x version patched https://ossindex.sonatype.org/component/pkg:maven/org.hibernate.reactive/hibernate-reactive-core
-            "com.h2database:h2:2.3.232" // no version patched https://ossindex.sonatype.org/component/pkg:maven/com.h2database/h2
+            "com.h2database:h2:2.4.240" // no version patched https://ossindex.sonatype.org/component/pkg:maven/com.h2database/h2
     ]
 }
+
+micronautBuild {
+    descriptor {
+        parentModuleId = "io.micronaut.sql:micronaut-sql-jdbc"
+    }
+}
```

### `buildSrc/src/main/groovy/io.micronaut.build.internal.testing-base.gradle`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/buildSrc/src/main/groovy/io.micronaut.build.internal.testing-base.gradle	2026-04-22 07:32:32.129652801 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/buildSrc/src/main/groovy/io.micronaut.build.internal.testing-base.gradle	2026-04-22 07:29:45.029522233 +0000
@@ -6,11 +6,6 @@
 
 group "io.micronaut.example"
 
-java {
-    sourceCompatibility = "17"
-    targetCompatibility = "17"
-}
-
 tasks.register("testExamples") {
     dependsOn "test"
 }
```

### `gradle/wrapper/gradle-wrapper.jar`

_Binary file differs._

### `gradlew`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/gradlew	2026-04-22 07:32:32.130690393 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/gradlew	2026-04-22 07:29:45.030592035 +0000
@@ -1,7 +1,7 @@
 #!/bin/sh
 
 #
-# Copyright © 2015-2021 the original authors.
+# Copyright © 2015 the original authors.
 #
 # Licensed under the Apache License, Version 2.0 (the "License");
 # you may not use this file except in compliance with the License.
@@ -57,7 +57,7 @@
 #       Darwin, MinGW, and NonStop.
 #
 #   (3) This script is generated from the Groovy template
-#       https://github.com/gradle/gradle/blob/HEAD/platforms/jvm/plugins-application/src/main/resources/org/gradle/api/internal/plugins/unixStartScript.txt
+#       https://github.com/gradle/gradle/blob/2d6327017519d23b96af35865dc997fcb544fb40/platforms/jvm/plugins-application/src/main/resources/org/gradle/api/internal/plugins/unixStartScript.txt
 #       within the Gradle project.
 #
 #       You can find Gradle at https://github.com/gradle/gradle/.
@@ -114,7 +114,6 @@
   NONSTOP* )        nonstop=true ;;
 esac
 
-CLASSPATH="\\\"\\\""
 
 
 # Determine the Java command to use to start the JVM.
@@ -172,7 +171,6 @@
 # For Cygwin or MSYS, switch paths to Windows format before running java
 if "$cygwin" || "$msys" ; then
     APP_HOME=$( cygpath --path --mixed "$APP_HOME" )
-    CLASSPATH=$( cygpath --path --mixed "$CLASSPATH" )
 
     JAVACMD=$( cygpath --unix "$JAVACMD" )
 
@@ -212,7 +210,6 @@
 
 set -- \
         "-Dorg.gradle.appname=$APP_BASE_NAME" \
-        -classpath "$CLASSPATH" \
         -jar "$APP_HOME/gradle/wrapper/gradle-wrapper.jar" \
         "$@"
 
```

### `gradlew.bat`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/gradlew.bat	2026-04-22 07:32:32.130763144 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/gradlew.bat	2026-04-22 07:29:45.030669744 +0000
@@ -70,11 +70,10 @@
 :execute
 @rem Setup the command line
 
-set CLASSPATH=
 
 
 @rem Execute Gradle
-"%JAVA_EXE%" %DEFAULT_JVM_OPTS% %JAVA_OPTS% %GRADLE_OPTS% "-Dorg.gradle.appname=%APP_BASE_NAME%" -classpath "%CLASSPATH%" -jar "%APP_HOME%\gradle\wrapper\gradle-wrapper.jar" %*
+"%JAVA_EXE%" %DEFAULT_JVM_OPTS% %JAVA_OPTS% %GRADLE_OPTS% "-Dorg.gradle.appname=%APP_BASE_NAME%" -jar "%APP_HOME%\gradle\wrapper\gradle-wrapper.jar" %*
 
 :end
 @rem End local scope for the variables with windows NT shell
```

### `hibernate-jpa/build.gradle`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/hibernate-jpa/build.gradle	2026-04-22 07:32:32.130874395 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/hibernate-jpa/build.gradle	2026-04-22 07:29:45.030777161 +0000
@@ -8,8 +8,12 @@
     api(libs.managed.hibernate.core)
     api(libs.managed.jakarta.transaction.api)
     api(mnValidation.micronaut.validation)
-    compileOnly(mnData.micronaut.data.tx.hibernate)
-    testImplementation(mnData.micronaut.data.tx.hibernate)
+    compileOnly(mnData.micronaut.data.tx.hibernate) {
+        exclude(group: "org.hibernate.orm")
+    }
+    testImplementation(mnData.micronaut.data.tx.hibernate) {
+        exclude(group: "org.hibernate.orm")
+    }
     api(mn.micronaut.aop)
     api projects.micronautJdbc
 
```

### `hibernate-jpa/src/main/java/io/micronaut/configuration/hibernate/jpa/JpaConfiguration.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/hibernate-jpa/src/main/java/io/micronaut/configuration/hibernate/jpa/JpaConfiguration.java	2026-04-22 07:32:32.131396525 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/hibernate-jpa/src/main/java/io/micronaut/configuration/hibernate/jpa/JpaConfiguration.java	2026-04-22 07:29:45.031309791 +0000
@@ -20,8 +20,8 @@
 import io.micronaut.context.annotation.EachProperty;
 import io.micronaut.context.annotation.Parameter;
 import io.micronaut.context.env.Environment;
-import io.micronaut.core.annotation.NonNull;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.NonNull;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.core.beans.BeanIntrospection;
 import io.micronaut.core.beans.BeanIntrospector;
 import io.micronaut.core.convert.format.MapFormat;
```

### `hibernate-jpa/src/main/java/io/micronaut/configuration/hibernate/jpa/conf/SessionFactoryPerDataSourceFactory.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/hibernate-jpa/src/main/java/io/micronaut/configuration/hibernate/jpa/conf/SessionFactoryPerDataSourceFactory.java	2026-04-22 07:32:32.131817862 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/hibernate-jpa/src/main/java/io/micronaut/configuration/hibernate/jpa/conf/SessionFactoryPerDataSourceFactory.java	2026-04-22 07:29:45.031743503 +0000
@@ -30,7 +30,7 @@
 import io.micronaut.context.env.Environment;
 import io.micronaut.context.exceptions.DisabledBeanException;
 import io.micronaut.core.annotation.Internal;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.core.annotation.TypeHint;
 import org.hibernate.SessionFactory;
 import org.hibernate.boot.Metadata;
```

### `hibernate-jpa/src/main/java/io/micronaut/configuration/hibernate/jpa/conf/serviceregistry/builder/configures/StandardServiceRegistryBuilderConfigurer.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/hibernate-jpa/src/main/java/io/micronaut/configuration/hibernate/jpa/conf/serviceregistry/builder/configures/StandardServiceRegistryBuilderConfigurer.java	2026-04-22 07:32:32.132082781 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/hibernate-jpa/src/main/java/io/micronaut/configuration/hibernate/jpa/conf/serviceregistry/builder/configures/StandardServiceRegistryBuilderConfigurer.java	2026-04-22 07:29:45.032008089 +0000
@@ -17,7 +17,7 @@
 
 import io.micronaut.configuration.hibernate.jpa.JpaConfiguration;
 import io.micronaut.core.annotation.Indexed;
-import io.micronaut.core.annotation.NonNull;
+import org.jspecify.annotations.NonNull;
 import io.micronaut.core.order.Ordered;
 import org.hibernate.boot.registry.StandardServiceRegistryBuilder;
 
```

### `hibernate-jpa/src/main/java/io/micronaut/configuration/hibernate/jpa/conf/serviceregistry/builder/supplier/StandardServiceRegistryBuilderCreator.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/hibernate-jpa/src/main/java/io/micronaut/configuration/hibernate/jpa/conf/serviceregistry/builder/supplier/StandardServiceRegistryBuilderCreator.java	2026-04-22 07:32:32.132405409 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/hibernate-jpa/src/main/java/io/micronaut/configuration/hibernate/jpa/conf/serviceregistry/builder/supplier/StandardServiceRegistryBuilderCreator.java	2026-04-22 07:29:45.032331300 +0000
@@ -17,7 +17,7 @@
 
 import io.micronaut.configuration.hibernate.jpa.JpaConfiguration;
 import io.micronaut.core.annotation.Indexed;
-import io.micronaut.core.annotation.NonNull;
+import org.jspecify.annotations.NonNull;
 import org.hibernate.boot.registry.StandardServiceRegistryBuilder;
 
 /**
```

### `hibernate-jpa/src/main/java/io/micronaut/configuration/hibernate/jpa/conf/serviceregistry/builder/supplier/internal/DefaultStandardServiceRegistryBuilderCreatorCreator.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/hibernate-jpa/src/main/java/io/micronaut/configuration/hibernate/jpa/conf/serviceregistry/builder/supplier/internal/DefaultStandardServiceRegistryBuilderCreatorCreator.java	2026-04-22 07:32:32.132520493 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/hibernate-jpa/src/main/java/io/micronaut/configuration/hibernate/jpa/conf/serviceregistry/builder/supplier/internal/DefaultStandardServiceRegistryBuilderCreatorCreator.java	2026-04-22 07:29:45.032439135 +0000
@@ -22,15 +22,12 @@
 import io.micronaut.context.annotation.Prototype;
 import io.micronaut.context.annotation.Requires;
 import io.micronaut.core.annotation.Internal;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import org.hibernate.boot.registry.BootstrapServiceRegistry;
 import org.hibernate.boot.registry.BootstrapServiceRegistryBuilder;
 import org.hibernate.boot.registry.StandardServiceRegistryBuilder;
 import org.hibernate.integrator.spi.Integrator;
 
-import static org.hibernate.bytecode.internal.BytecodeProviderInitiator.BYTECODE_PROVIDER_NAME_NONE;
-import static org.hibernate.cfg.AvailableSettings.BYTECODE_PROVIDER;
-
 /**
  * Default supplier of {@link StandardServiceRegistryBuilderCreator}.
  *
@@ -55,9 +52,6 @@
 
     @Override
     public StandardServiceRegistryBuilder create(JpaConfiguration jpaConfiguration) {
-        if (jpaConfiguration.isCompileTimeHibernateProxies()) {
-            System.setProperty(BYTECODE_PROVIDER, BYTECODE_PROVIDER_NAME_NONE);
-        }
         if (jpaConfiguration.isReactive()) {
             throw new IllegalStateException("Hibernate Reactive not found on classpath!");
         }
```

### `hibernate-jpa/src/main/java/io/micronaut/configuration/hibernate/jpa/conf/settings/internal/DataSourceSettingSupplier.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/hibernate-jpa/src/main/java/io/micronaut/configuration/hibernate/jpa/conf/settings/internal/DataSourceSettingSupplier.java	2026-04-22 07:32:32.133500252 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/hibernate-jpa/src/main/java/io/micronaut/configuration/hibernate/jpa/conf/settings/internal/DataSourceSettingSupplier.java	2026-04-22 07:29:45.033366268 +0000
@@ -22,7 +22,7 @@
 import io.micronaut.context.annotation.Prototype;
 import io.micronaut.context.annotation.Requires;
 import io.micronaut.core.annotation.Internal;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.inject.qualifiers.Qualifiers;
 import io.micronaut.jdbc.DataSourceResolver;
 import org.hibernate.cfg.AvailableSettings;
```

### `hibernate-jpa/src/main/java/io/micronaut/configuration/hibernate/jpa/conf/settings/internal/MicronautContainerSettingsSupplier.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/hibernate-jpa/src/main/java/io/micronaut/configuration/hibernate/jpa/conf/settings/internal/MicronautContainerSettingsSupplier.java	2026-04-22 07:32:32.133658462 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/hibernate-jpa/src/main/java/io/micronaut/configuration/hibernate/jpa/conf/settings/internal/MicronautContainerSettingsSupplier.java	2026-04-22 07:29:45.033548186 +0000
@@ -21,7 +21,7 @@
 import io.micronaut.context.annotation.Prototype;
 import io.micronaut.core.annotation.Internal;
 import io.micronaut.inject.qualifiers.Qualifiers;
-import org.hibernate.cfg.AvailableSettings;
+import org.hibernate.cfg.ManagedBeanSettings;
 import org.hibernate.resource.beans.container.spi.BeanContainer;
 import org.hibernate.resource.beans.container.spi.ContainedBean;
 import org.hibernate.resource.beans.spi.BeanInstanceProducer;
@@ -49,21 +49,42 @@
     public Map<String, Object> supply(JpaConfiguration jpaConfiguration) {
         BeanContainer beanContainer = new BeanContainer() {
             @Override
-            public <B> ContainedBean<B> getBean(Class<B> beanType, LifecycleOptions lifecycleOptions, BeanInstanceProducer fallbackProducer) {
+            public <B> ContainedBean<B> getBean(Class<B> beanType,
+                                                    LifecycleOptions lifecycleOptions,
+                                                    BeanInstanceProducer fallbackProducer) {
                 B bean = applicationContext.findBean(beanType)
-                        .orElseGet(() -> fallbackProducer.produceBeanInstance(beanType));
-                return () -> bean;
+                    .orElseGet(() -> fallbackProducer.produceBeanInstance(beanType));
+                return new ContainedBean<>() {
+                    @Override
+                    public Class<B> getBeanClass() {
+                        return beanType;
+                    }
+
+                    @Override
+                    public B getBeanInstance() {
+                        return bean;
+                    }
+                };
             }
 
             @Override
-            public <B> ContainedBean<B> getBean(
-                    String name,
-                    Class<B> beanType,
-                    LifecycleOptions lifecycleOptions,
-                    BeanInstanceProducer fallbackProducer) {
+            public <B> ContainedBean<B> getBean(String name,
+                                                    Class<B> beanType,
+                                                    LifecycleOptions lifecycleOptions,
+                                                    BeanInstanceProducer fallbackProducer) {
                 B bean = applicationContext.findBean(beanType, Qualifiers.byName(name))
-                        .orElseGet(() -> fallbackProducer.produceBeanInstance(name, beanType));
-                return () -> bean;
+                    .orElseGet(() -> fallbackProducer.produceBeanInstance(name, beanType));
+                return new ContainedBean<>() {
+                    @Override
+                    public Class<B> getBeanClass() {
+                        return beanType;
+                    }
+
+                    @Override
+                    public B getBeanInstance() {
+                        return bean;
+                    }
+                };
             }
 
             @Override
@@ -71,6 +92,7 @@
                 // no-op, managed externally
             }
         };
-        return Collections.singletonMap(AvailableSettings.BEAN_CONTAINER, beanContainer);
+
+        return Collections.singletonMap(ManagedBeanSettings.BEAN_CONTAINER, beanContainer);
     }
 }
```

### `hibernate-jpa/src/main/resources/META-INF/native-image/io.micronaut.sql/hibernate-jpa-graal/reflect-config.json`

_Large file: 369 lines added, 2 lines removed. Showing first 50 diff lines:_

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/hibernate-jpa/src/main/resources/META-INF/native-image/io.micronaut.sql/hibernate-jpa-graal/reflect-config.json	2026-04-22 07:32:32.135086475 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/hibernate-jpa/src/main/resources/META-INF/native-image/io.micronaut.sql/hibernate-jpa-graal/reflect-config.json	2026-04-22 07:29:45.034870448 +0000
@@ -11,9 +11,376 @@
     ]
   },
   {
-    "name": "[Lorg.hibernate.event.spi.PostUpsertEventListener;"
+    "name": "org.hibernate.action.internal.ActionLogging_$logger",
+    "methods": [
+      {
+        "name": "<init>",
+        "parameterTypes": [
+          "org.jboss.logging.Logger"
+        ]
+      }
+    ]
+  },
+  {
+    "name": "org.hibernate.boot.BootLogging_$logger",
+    "methods": [
+      {
+        "name": "<init>",
+        "parameterTypes": [
+          "org.jboss.logging.Logger"
+        ]
+      }
+    ]
+  },
+  {
+    "name": "org.hibernate.cache.spi.SecondLevelCacheLogger_$logger",
+    "methods": [
+      {
+        "name": "<init>",
+        "parameterTypes": [
+          "org.jboss.logging.Logger"
+        ]
+      }
+    ]
+  },
+  {
+    "name": "org.hibernate.dialect.DialectLogging_$logger",
+    "methods": [
+      {
+        "name": "<init>",
+        "parameterTypes": [
+          "org.jboss.logging.Logger"
+        ]
+      }
+    ]
+  },
... (truncated)
```

### `hibernate-jpa/src/test/groovy/io/micronaut/configuration/hibernate/jpa/mapping/AccountRepository.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/hibernate-jpa/src/test/groovy/io/micronaut/configuration/hibernate/jpa/mapping/AccountRepository.java	2026-04-22 07:32:32.137146702 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/hibernate-jpa/src/test/groovy/io/micronaut/configuration/hibernate/jpa/mapping/AccountRepository.java	2026-04-22 07:29:45.036803965 +0000
@@ -15,7 +15,7 @@
  */
 package io.micronaut.configuration.hibernate.jpa.mapping;
 
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.transaction.annotation.Transactional;
 import jakarta.inject.Singleton;
 
```

### `hibernate-reactive/build.gradle`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/hibernate-reactive/build.gradle	2026-04-22 07:32:32.138646465 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/hibernate-reactive/build.gradle	2026-04-22 07:29:45.038256062 +0000
@@ -9,11 +9,7 @@
         exclude module: 'jdbc'
         exclude group: 'micronaut-data'
     }
-    api (libs.managed.hibernate.reactive.core) {
-        // TODO: Temp exclude since hibernate-reactive brings in vert-sql-client 4.5.22
-        // which has vulnerability and we will use 4.5.24 override from the catalog
-        exclude group: 'io.vertx', module: 'vertx-sql-client'
-    }
+    api libs.managed.hibernate.reactive.core
     api mn.micronaut.runtime
 
     compileOnly libs.managed.vertx.sql.client
@@ -25,9 +21,11 @@
     testImplementation projects.micronautJdbc
     testRuntimeOnly projects.micronautJdbcTomcat
     testRuntimeOnly(libs.managed.h2)
+    testRuntimeOnly libs.managed.ongres.scram.client
 
     testImplementation(mnTestResources.testcontainers.jdbc)
     testImplementation(mnTestResources.testcontainers.postgres)
     testImplementation libs.managed.vertx.pg.client
     testImplementation(mnData.micronaut.data.tx.hibernate)
 }
+
```

### `hibernate-reactive/src/main/java/io/micronaut/configuration/hibernate/reactive/conf/ReactiveRegistryCreator.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/hibernate-reactive/src/main/java/io/micronaut/configuration/hibernate/reactive/conf/ReactiveRegistryCreator.java	2026-04-22 07:32:32.139293012 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/hibernate-reactive/src/main/java/io/micronaut/configuration/hibernate/reactive/conf/ReactiveRegistryCreator.java	2026-04-22 07:29:45.038988777 +0000
@@ -21,7 +21,7 @@
 import io.micronaut.context.annotation.Primary;
 import io.micronaut.context.annotation.Prototype;
 import io.micronaut.context.annotation.Requires;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import org.hibernate.boot.registry.BootstrapServiceRegistry;
 import org.hibernate.boot.registry.BootstrapServiceRegistryBuilder;
 import org.hibernate.boot.registry.StandardServiceRegistryBuilder;
```

### `jasync-sql/src/main/java/io/micronaut/configuration/jasync/JasyncPoolConfiguration.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jasync-sql/src/main/java/io/micronaut/configuration/jasync/JasyncPoolConfiguration.java	2026-04-22 07:32:32.141728784 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jasync-sql/src/main/java/io/micronaut/configuration/jasync/JasyncPoolConfiguration.java	2026-04-22 07:29:45.041622259 +0000
@@ -23,8 +23,8 @@
 import io.micronaut.context.annotation.ConfigurationInject;
 import io.micronaut.context.annotation.ConfigurationProperties;
 import io.micronaut.context.annotation.Requires;
-import io.micronaut.core.annotation.NonNull;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.NonNull;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.core.bind.annotation.Bindable;
 
 import java.io.File;
```

### `jdbc/build.gradle`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jdbc/build.gradle	2026-04-22 07:32:32.152045627 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jdbc/build.gradle	2026-04-22 07:29:45.058342908 +0000
@@ -7,4 +7,6 @@
 
     api(mn.micronaut.inject)
     api(mn.micronaut.context)
+
+    testImplementation(libs.managed.sqlite.jdbc)
 }
```

### `jdbc/src/main/java/io/micronaut/jdbc/BaseDatasourceFactory.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jdbc/src/main/java/io/micronaut/jdbc/BaseDatasourceFactory.java	2026-04-22 07:32:32.152392255 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jdbc/src/main/java/io/micronaut/jdbc/BaseDatasourceFactory.java	2026-04-22 07:29:45.058746787 +0000
@@ -17,8 +17,8 @@
 
 import io.micronaut.context.ApplicationContext;
 import io.micronaut.core.annotation.Internal;
-import io.micronaut.core.annotation.NonNull;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.NonNull;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.core.util.CollectionUtils;
 import io.micronaut.core.util.StringUtils;
 import io.micronaut.runtime.context.scope.refresh.RefreshEvent;
```

### `jdbc/src/main/java/io/micronaut/jdbc/CalculatedSettings.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jdbc/src/main/java/io/micronaut/jdbc/CalculatedSettings.java	2026-04-22 07:32:32.152544965 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jdbc/src/main/java/io/micronaut/jdbc/CalculatedSettings.java	2026-04-22 07:29:45.058919414 +0000
@@ -124,8 +124,10 @@
         final String username = basicJdbcConfiguration.getConfiguredUsername();
         if (calculatedUsername == null || StringUtils.hasText(username)) {
             calculatedUsername = username;
-            if (!StringUtils.hasText(calculatedUsername) && JdbcDatabaseManager.isEmbedded(basicJdbcConfiguration.getDriverClassName())) {
-                calculatedUsername = "sa";
+            if (!StringUtils.hasText(calculatedUsername)) {
+                calculatedUsername = JdbcDatabaseManager.findEmbeddedDatabase(basicJdbcConfiguration.getDriverClassName())
+                    .map(JdbcDatabaseManager.EmbeddedJdbcDatabase::getDefaultUsername)
+                    .orElse(null);
             }
         }
 
@@ -143,8 +145,10 @@
         final String password = basicJdbcConfiguration.getConfiguredPassword();
         if (calculatedPassword == null || StringUtils.hasText(password)) {
             calculatedPassword = password;
-            if (!StringUtils.hasText(calculatedPassword) && JdbcDatabaseManager.isEmbedded(basicJdbcConfiguration.getDriverClassName())) {
-                calculatedPassword = "";
+            if (!StringUtils.hasText(calculatedPassword)) {
+                calculatedPassword = JdbcDatabaseManager.findEmbeddedDatabase(basicJdbcConfiguration.getDriverClassName())
+                    .map(JdbcDatabaseManager.EmbeddedJdbcDatabase::getDefaultPassword)
+                    .orElse(null);
             }
         }
 
```

### `jdbc/src/main/java/io/micronaut/jdbc/JdbcDatabaseManager.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jdbc/src/main/java/io/micronaut/jdbc/JdbcDatabaseManager.java	2026-04-22 07:32:32.152772300 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jdbc/src/main/java/io/micronaut/jdbc/JdbcDatabaseManager.java	2026-04-22 07:29:45.059257625 +0000
@@ -38,12 +38,12 @@
         databases.add(new EmbeddedJdbcDatabase("org.h2.Driver", "h2", "jdbc:h2:mem:%s;DB_CLOSE_DELAY=-1;DB_CLOSE_ON_EXIT=FALSE"));
         databases.add(new EmbeddedJdbcDatabase("org.apache.derby.jdbc.EmbeddedDriver", "SELECT 1 FROM SYSIBM.SYSDUMMY1", new String[]{"derby"}, "jdbc:derby:memory:%s;create=true"));
         databases.add(new EmbeddedJdbcDatabase("org.hsqldb.jdbc.JDBCDriver", "select 1 from INFORMATION_SCHEMA.SYSTEM_USERS", new String[]{"hsqldb"}, "jdbc:hsqldb:mem:%s"));
+        databases.add(new EmbeddedJdbcDatabase("org.sqlite.JDBC", "sqlite", "jdbc:sqlite:file:%s?mode=memory&cache=shared", null, null));
 
         databases.add(new JdbcDatabase("com.mysql.cj.jdbc.Driver", "mysql"));
         databases.add(new JdbcDatabase("oracle.jdbc.OracleDriver", "SELECT 1 FROM DUAL", new String[]{"oracle"}));
         databases.add(new JdbcDatabase("org.postgresql.Driver", "postgresql"));
         databases.add(new JdbcDatabase("com.microsoft.sqlserver.jdbc.SQLServerDriver", "sqlserver"));
-        databases.add(new JdbcDatabase("org.sqlite.JDBC", "sqlite"));
         databases.add(new JdbcDatabase("org.mariadb.jdbc.Driver", "mariadb"));
         databases.add(new JdbcDatabase("com.google.appengine.api.rdbms.AppEngineDriver", "gae"));
         databases.add(new JdbcDatabase("net.sourceforge.jtds.jdbc.Driver", "jtds"));
@@ -106,6 +106,21 @@
     }
 
     /**
+     * Searches embedded databases where the driver matches the argument.
+     *
+     * @param driverClassName The driver class name to search on
+     * @return An optional embedded database definition
+     */
+    public static Optional<EmbeddedJdbcDatabase> findEmbeddedDatabase(String driverClassName) {
+        return databases
+            .stream()
+            .filter(JdbcDatabase::isEmbedded)
+            .map(EmbeddedJdbcDatabase.class::cast)
+            .filter(db -> db.getDriverClassName().equals(driverClassName))
+            .findFirst();
+    }
+
+    /**
      * Provides the required information in order to connect toa JDBC database, including the necessary driver and
      * validation query.
      */
@@ -180,6 +195,8 @@
 
         private String defaultUrl;
         private String defaultName = "devDb";
+        private String defaultUsername = "sa";
+        private String defaultPassword = "";
 
         /**
          * @param driverClassName The jdbc driver class name
@@ -213,6 +230,19 @@
         }
 
         /**
+         * @param driverClassName The jdbc driver class name
+         * @param urlPrefix       The url prefix
+         * @param defaultUrl      The default url
+         * @param defaultUsername The default username
+         * @param defaultPassword The default password
+         */
+        EmbeddedJdbcDatabase(String driverClassName, String urlPrefix, String defaultUrl, String defaultUsername, String defaultPassword) {
+            this(driverClassName, urlPrefix, defaultUrl);
+            this.defaultUsername = defaultUsername;
+            this.defaultPassword = defaultPassword;
+        }
+
+        /**
          * Obtain an embedded database URL for the given database name.
          *
          * @param databaseName The database name
@@ -225,6 +255,20 @@
             return String.format(this.defaultUrl, databaseName);
         }
 
+        /**
+         * @return The default username, or {@code null} if the driver does not use one
+         */
+        public String getDefaultUsername() {
+            return defaultUsername;
+        }
+
+        /**
+         * @return The default password, or {@code null} if the driver does not use one
+         */
+        public String getDefaultPassword() {
+            return defaultPassword;
+        }
+
         @Override
         protected boolean isEmbedded() {
             return Boolean.TRUE;
```

### `jdbc/src/test/groovy/io/micronaut/jdbc/CalculatedSettingsSpec.groovy`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jdbc/src/test/groovy/io/micronaut/jdbc/CalculatedSettingsSpec.groovy	2026-04-22 07:32:32.153755726 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jdbc/src/test/groovy/io/micronaut/jdbc/CalculatedSettingsSpec.groovy	2026-04-22 07:29:45.060497469 +0000
@@ -16,6 +16,7 @@
 package io.micronaut.jdbc
 
 import io.micronaut.context.exceptions.ConfigurationException
+import org.sqlite.JDBC
 import spock.lang.Specification
 
 class CalculatedSettingsSpec extends Specification {
@@ -58,7 +59,7 @@
             1 * getUrl() >> null
         }
         URL h2Jar = this.class.classLoader.getResource("h2.jar")
-        CalculatedSettings settings = new CalculatedSettings(basicConfiguration, new URLClassLoader(h2Jar))
+        CalculatedSettings settings = new CalculatedSettings(basicConfiguration, new URLClassLoader([h2Jar] as URL[], ClassLoader.getPlatformClassLoader()))
 
         when:
         String driverClassName = settings.getDriverClassName()
@@ -75,7 +76,7 @@
             1 * getName() >> "bar"
         }
         URL mysqlJar = this.class.classLoader.getResource("mysql.jar") //mysql is not embedded
-        CalculatedSettings settings = new CalculatedSettings(basicConfiguration, new URLClassLoader(mysqlJar))
+        CalculatedSettings settings = new CalculatedSettings(basicConfiguration, new URLClassLoader([mysqlJar] as URL[], ClassLoader.getPlatformClassLoader()))
 
         when:
         settings.getDriverClassName()
@@ -106,7 +107,7 @@
             1 * getName() >> "bar"
         }
         URL h2Jar = this.class.classLoader.getResource("h2.jar")
-        CalculatedSettings settings = new CalculatedSettings(basicConfiguration, new URLClassLoader(h2Jar))
+        CalculatedSettings settings = new CalculatedSettings(basicConfiguration, new URLClassLoader([h2Jar] as URL[], ClassLoader.getPlatformClassLoader()))
 
         when:
         String url = settings.getUrl()
@@ -122,7 +123,7 @@
             1 * getName() >> null
         }
         URL h2Jar = this.class.classLoader.getResource("h2.jar")
-        CalculatedSettings settings = new CalculatedSettings(basicConfiguration, new URLClassLoader(h2Jar))
+        CalculatedSettings settings = new CalculatedSettings(basicConfiguration, new URLClassLoader([h2Jar] as URL[], ClassLoader.getPlatformClassLoader()))
 
         when:
         String url = settings.getUrl()
@@ -131,13 +132,30 @@
         url == "jdbc:h2:mem:devDb;DB_CLOSE_DELAY=-1;DB_CLOSE_ON_EXIT=FALSE"
     }
 
-    void "test getUrl will throw an exception if its not configured and a driver can't be found"() {
+    void "test getUrl will use a sqlite shared in-memory URL when sqlite is the embedded driver"() {
         given:
         BasicJdbcConfiguration basicConfiguration = Mock(BasicJdbcConfiguration) {
             1 * getConfiguredUrl() >> null
             1 * getName() >> "bar"
         }
-        CalculatedSettings settings = new CalculatedSettings(basicConfiguration)
+        URL sqliteJar = JDBC.protectionDomain.codeSource.location
+        CalculatedSettings settings = new CalculatedSettings(basicConfiguration, new URLClassLoader([sqliteJar] as URL[], ClassLoader.getPlatformClassLoader()))
+
+        when:
+        String url = settings.getUrl()
+
+        then:
+        url == "jdbc:sqlite:file:bar?mode=memory&cache=shared"
+    }
+
+    void "test getUrl will throw an exception if its not configured and the driver is not embedded"() {
+        given:
+        BasicJdbcConfiguration basicConfiguration = Mock(BasicJdbcConfiguration) {
+            1 * getConfiguredUrl() >> null
+            1 * getName() >> "bar"
+        }
+        URL mysqlJar = this.class.classLoader.getResource("mysql.jar") //mysql is not embedded
+        CalculatedSettings settings = new CalculatedSettings(basicConfiguration, new URLClassLoader([mysqlJar] as URL[], ClassLoader.getPlatformClassLoader()))
 
         when:
         settings.getUrl()
@@ -180,6 +198,20 @@
         "org.hsqldb.jdbc.JDBCDriver"           | _
     }
 
+    void "test getUsername returns null if the embedded driver does not use credentials"() {
+        BasicJdbcConfiguration basicConfiguration = Mock(BasicJdbcConfiguration) {
+            1 * getConfiguredUsername() >> null
+            1 * getDriverClassName() >> "org.sqlite.JDBC"
+        }
+        CalculatedSettings settings = new CalculatedSettings(basicConfiguration)
+
+        when:
+        String username = settings.getUsername()
+
+        then:
+        username == null
+    }
+
     void "test getPassword returns the configured password"() {
         BasicJdbcConfiguration basicConfiguration = Mock(BasicJdbcConfiguration) {
             1 * getConfiguredPassword() >> "pw"
@@ -213,6 +245,20 @@
         "org.hsqldb.jdbc.JDBCDriver"           | _
     }
 
+    void "test getPassword returns null if the embedded driver does not use credentials"() {
+        BasicJdbcConfiguration basicConfiguration = Mock(BasicJdbcConfiguration) {
+            1 * getConfiguredPassword() >> null
+            1 * getDriverClassName() >> "org.sqlite.JDBC"
+        }
+        CalculatedSettings settings = new CalculatedSettings(basicConfiguration)
+
+        when:
+        String password = settings.getPassword()
+
+        then:
+        password == null
+    }
+
     void "test getValidationQuery returns the configured value"() {
         BasicJdbcConfiguration basicConfiguration = Mock(BasicJdbcConfiguration) {
             1 * getConfiguredValidationQuery() >> "x"
@@ -244,5 +290,6 @@
         "jdbc:as400:x"   | "SELECT 1 FROM SYSIBM.SYSDUMMY1"
         "jdbc:mariadb:x" | "SELECT 1"
         "jdbc:oracle:x"  | "SELECT 1 FROM DUAL"
+        "jdbc:sqlite:x"  | "SELECT 1"
     }
 }
```

### `jdbc-dbcp/src/main/java/io/micronaut/configuration/jdbc/dbcp/DatasourceConfiguration.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jdbc-dbcp/src/main/java/io/micronaut/configuration/jdbc/dbcp/DatasourceConfiguration.java	2026-04-22 07:32:32.144003971 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jdbc-dbcp/src/main/java/io/micronaut/configuration/jdbc/dbcp/DatasourceConfiguration.java	2026-04-22 07:29:45.043960113 +0000
@@ -19,12 +19,14 @@
 import io.micronaut.context.annotation.EachProperty;
 import io.micronaut.context.annotation.Parameter;
 import io.micronaut.context.annotation.Property;
+import io.micronaut.context.env.Environment;
 import io.micronaut.context.exceptions.DisabledBeanException;
 import io.micronaut.core.annotation.Internal;
 import io.micronaut.core.convert.format.MapFormat;
 import io.micronaut.core.naming.conventions.StringConvention;
 import io.micronaut.jdbc.BasicJdbcConfiguration;
 import io.micronaut.jdbc.CalculatedSettings;
+import io.micronaut.jdbc.OracleSessionProgramHelper;
 import org.apache.commons.dbcp2.BasicDataSource;
 import org.slf4j.Logger;
 import org.slf4j.LoggerFactory;
@@ -49,17 +51,23 @@
 @EachProperty(value = BasicJdbcConfiguration.PREFIX, primary = "default")
 public class DatasourceConfiguration extends BasicDataSource implements BasicJdbcConfiguration {
 
+    private static final String ORACLE_VSESSION_PROGRAM = "v$session.program";
+
     private static final Logger LOG = LoggerFactory.getLogger(DatasourceConfiguration.class);
     private final CalculatedSettings calculatedSettings;
     private final String name;
+    private final Environment environment;
+    private boolean oracleProgramProvided;
 
     /**
      * Constructor.
      * @param name name configured from properties
+     * @param environment The environment
      */
-    public DatasourceConfiguration(@Parameter String name) {
+    public DatasourceConfiguration(@Parameter String name, Environment environment) {
         super();
         this.name = name;
+        this.environment = environment;
         this.calculatedSettings = new CalculatedSettings(this);
     }
 
@@ -85,6 +93,23 @@
         if (getConfiguredValidationQuery() == null) {
             setValidationQuery(getValidationQuery());
         }
+        try {
+            boolean provided = OracleSessionProgramHelper.apply(
+                    getName(),
+                    getUrl(),
+                    environment.getProperty("datasources." + getName() + ".dialect", String.class).orElse(null),
+                    environment,
+                    this::addConnectionProperty,
+                    () -> oracleProgramProvided
+            );
+            if (provided) {
+                oracleProgramProvided = true;
+            }
+        } catch (Exception e) {
+            if (LOG.isDebugEnabled()) {
+                LOG.debug("Skipping Oracle session program auto-config due to: {}", e.getMessage());
+            }
+        }
     }
 
     /**
@@ -168,6 +193,9 @@
         if (dsProperties != null) {
             dsProperties.forEach((s, o) -> {
                 if (o != null) {
+                    if (ORACLE_VSESSION_PROGRAM.equalsIgnoreCase(s)) {
+                        oracleProgramProvided = true;
+                    }
                     addConnectionProperty(s, o.toString());
                 }
             });
@@ -194,4 +222,18 @@
             throw new DisabledBeanException("The datasource \"" + name + "\" is disabled");
         }
     }
+
+    /**
+     * Checks if the Oracle program has been provided.
+     *
+     * The Oracle program is considered provided if it has been explicitly set
+     * through the 'datasources.*.data-source-properties' or 'datasources.*.oracle.session.enabled'
+     * configuration properties (using Micronaut Application as value).
+     * Currently used for testing purposes.
+     *
+     * @return true if the Oracle program has been provided, false otherwise
+     */
+    public boolean isOracleProgramProvided() {
+        return oracleProgramProvided;
+    }
 }
```

### `jdbc-dbcp/src/main/java/io/micronaut/configuration/jdbc/dbcp/DatasourceFactory.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jdbc-dbcp/src/main/java/io/micronaut/configuration/jdbc/dbcp/DatasourceFactory.java	2026-04-22 07:32:32.144125431 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jdbc-dbcp/src/main/java/io/micronaut/configuration/jdbc/dbcp/DatasourceFactory.java	2026-04-22 07:29:45.044124614 +0000
@@ -19,12 +19,12 @@
 import io.micronaut.context.ApplicationContext;
 import io.micronaut.context.annotation.EachBean;
 import io.micronaut.context.annotation.Factory;
-import io.micronaut.core.annotation.Nullable;
 import io.micronaut.inject.qualifiers.Qualifiers;
 import io.micronaut.jdbc.BaseDatasourceFactory;
 import io.micronaut.jdbc.DataSourceResolver;
 import io.micronaut.jdbc.metadata.DataSourcePoolMetadata;
 import org.apache.commons.dbcp2.BasicDataSource;
+import org.jspecify.annotations.Nullable;
 import org.slf4j.Logger;
 import org.slf4j.LoggerFactory;
 
@@ -44,6 +44,7 @@
     private static final Logger LOG = LoggerFactory.getLogger(DatasourceFactory.class);
 
     private final DataSourceResolver dataSourceResolver;
+
     /**
      * Default constructor.
      * @param dataSourceResolver The data source resolver
```

### `jdbc-dbcp/src/test/groovy/io/micronaut/configuration/jdbc/dbcp/DatasourceConfigurationSpec.groovy`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jdbc-dbcp/src/test/groovy/io/micronaut/configuration/jdbc/dbcp/DatasourceConfigurationSpec.groovy	2026-04-22 07:32:32.145210024 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jdbc-dbcp/src/test/groovy/io/micronaut/configuration/jdbc/dbcp/DatasourceConfigurationSpec.groovy	2026-04-22 07:29:45.045928881 +0000
@@ -216,7 +216,7 @@
         String version = resultSet.getString(1)
 
         then:
-        version == '2.3.232'
+        version == '2.4.240'
 
         cleanup:
         applicationContext.close()
@@ -244,8 +244,6 @@
 
         then:
         dataSource.maxWaitMillis == 5000
-        dataSource.connectionProperties.getProperty('prop1') == 'value1'
-        dataSource.connectionProperties.getProperty('prop2') == 'value2'
         dataSource.defaultAutoCommit
         dataSource.defaultCatalog == 'catalog'
 
```

### `jdbc-hikari/build.gradle`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jdbc-hikari/build.gradle	2026-04-22 07:32:32.145835904 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jdbc-hikari/build.gradle	2026-04-22 07:29:45.047337893 +0000
@@ -9,7 +9,6 @@
 
     compileOnly(mnMicrometer.micronaut.micrometer.core)
 
-    testRuntimeOnly(libs.managed.tomcat.jdbc)
     testRuntimeOnly(libs.managed.h2)
 
     testAnnotationProcessor(mn.micronaut.inject.java)
```

### `jdbc-hikari/src/main/java/io/micronaut/configuration/jdbc/hikari/DatasourceFactory.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jdbc-hikari/src/main/java/io/micronaut/configuration/jdbc/hikari/DatasourceFactory.java	2026-04-22 07:32:32.146311242 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jdbc-hikari/src/main/java/io/micronaut/configuration/jdbc/hikari/DatasourceFactory.java	2026-04-22 07:29:45.048372403 +0000
@@ -23,6 +23,7 @@
 import io.micronaut.context.annotation.Requires;
 import io.micronaut.jdbc.BaseDatasourceFactory;
 import io.micronaut.jdbc.JdbcDataSourceEnabled;
+import io.micronaut.jdbc.OracleSessionProgramHelper;
 import org.slf4j.Logger;
 import org.slf4j.LoggerFactory;
 
@@ -65,6 +66,20 @@
     @EachBean(DatasourceConfiguration.class)
     @Requires(condition = JdbcDataSourceEnabled.class)
     public DataSource dataSource(DatasourceConfiguration datasourceConfiguration) {
+        try {
+            OracleSessionProgramHelper.apply(
+                    datasourceConfiguration.getName(),
+                    datasourceConfiguration.getUrl(),
+                    applicationContext.getProperty("datasources." + datasourceConfiguration.getName() + ".dialect", String.class).orElse(null),
+                    applicationContext.getEnvironment(),
+                    datasourceConfiguration::addDataSourceProperty,
+                    () -> datasourceConfiguration.getDataSourceProperties() != null && datasourceConfiguration.getDataSourceProperties().containsKey("v$session.program")
+            );
+        } catch (Exception e) {
+            if (LOG.isDebugEnabled()) {
+                LOG.debug("Skipping Oracle session program auto-config due to: {}", e.getMessage());
+            }
+        }
         HikariUrlDataSource ds = new HikariUrlDataSource(datasourceConfiguration);
         addMeterRegistry(ds);
         dataSources.put(datasourceConfiguration.getName(), ds);
```

### `jdbc-hikari/src/main/resources/META-INF/native-image/io.micronaut.sql/jdbc-hikari-graal/reflect-config.json`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jdbc-hikari/src/main/resources/META-INF/native-image/io.micronaut.sql/jdbc-hikari-graal/reflect-config.json	2026-04-22 07:32:32.146700496 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jdbc-hikari/src/main/resources/META-INF/native-image/io.micronaut.sql/jdbc-hikari-graal/reflect-config.json	2026-04-22 07:29:45.049121284 +0000
@@ -4,7 +4,7 @@
     "name":"com.zaxxer.hikari.HikariConfig",
     "allDeclaredFields":true,
     "queryAllPublicMethods":true,
-    "methods":[{"name":"getCatalog","parameterTypes":[] }, {"name":"getConnectionInitSql","parameterTypes":[] }, {"name":"getConnectionTestQuery","parameterTypes":[] }, {"name":"getConnectionTimeout","parameterTypes":[] }, {"name":"getCredentials","parameterTypes":[] }, {"name":"getDataSource","parameterTypes":[] }, {"name":"getDataSourceClassName","parameterTypes":[] }, {"name":"getDataSourceJNDI","parameterTypes":[] }, {"name":"getDataSourceProperties","parameterTypes":[] }, {"name":"getExceptionOverride","parameterTypes":[] }, {"name":"getExceptionOverrideClassName","parameterTypes":[] }, {"name":"getHealthCheckProperties","parameterTypes":[] }, {"name":"getHealthCheckRegistry","parameterTypes":[] }, {"name":"getIdleTimeout","parameterTypes":[] }, {"name":"getInitializationFailTimeout","parameterTypes":[] }, {"name":"getJdbcUrl","parameterTypes":[] }, {"name":"getKeepaliveTime","parameterTypes":[] }, {"name":"getLeakDetectionThreshold","parameterTypes":[] }, {"name":"getMaxLifetime","parameterTypes":[] }, {"name":"getMaximumPoolSize","parameterTypes":[] }, {"name":"getMetricRegistry","parameterTypes":[] }, {"name":"getMetricsTrackerFactory","parameterTypes":[] }, {"name":"getMinimumIdle","parameterTypes":[] }, {"name":"getPoolName","parameterTypes":[] }, {"name":"getScheduledExecutor","parameterTypes":[] }, {"name":"getSchema","parameterTypes":[] }, {"name":"getThreadFactory","parameterTypes":[] }, {"name":"getTransactionIsolation","parameterTypes":[] }, {"name":"getValidationTimeout","parameterTypes":[] }, {"name":"isAllowPoolSuspension","parameterTypes":[] }, {"name":"isAutoCommit","parameterTypes":[] }, {"name":"isIsolateInternalQueries","parameterTypes":[] }, {"name":"isReadOnly","parameterTypes":[] }, {"name":"isRegisterMbeans","parameterTypes":[] }, {"name":"setAllowPoolSuspension","parameterTypes":["boolean"] }, {"name":"setAutoCommit","parameterTypes":["boolean"] }, {"name":"setCatalog","parameterTypes":["java.lang.String"] }, {"name":"setClass","parameterTypes":["java.lang.Class"] }, {"name":"setConnectionInitSql","parameterTypes":["java.lang.String"] }, {"name":"setConnectionTestQuery","parameterTypes":["java.lang.String"] }, {"name":"setConnectionTimeout","parameterTypes":["long"] }, {"name":"setCredentials","parameterTypes":["com.zaxxer.hikari.util.Credentials"] }, {"name":"setDataSource","parameterTypes":["javax.sql.DataSource"] }, {"name":"setDataSourceClassName","parameterTypes":["java.lang.String"] }, {"name":"setDataSourceJNDI","parameterTypes":["java.lang.String"] }, {"name":"setDataSourceProperties","parameterTypes":["java.util.Properties"] }, {"name":"setDriverClassName","parameterTypes":["java.lang.String"] }, {"name":"setExceptionOverride","parameterTypes":["com.zaxxer.hikari.SQLExceptionOverride"] }, {"name":"setExceptionOverrideClassName","parameterTypes":["java.lang.String"] }, {"name":"setHealthCheckProperties","parameterTypes":["java.util.Properties"] }, {"name":"setHealthCheckRegistry","parameterTypes":["java.lang.Object"] }, {"name":"setIdleTimeout","parameterTypes":["long"] }, {"name":"setInitializationFailTimeout","parameterTypes":["long"] }, {"name":"setIsolateInternalQueries","parameterTypes":["boolean"] }, {"name":"setJdbcUrl","parameterTypes":["java.lang.String"] }, {"name":"setKeepaliveTime","parameterTypes":["long"] }, {"name":"setLeakDetectionThreshold","parameterTypes":["long"] }, {"name":"setMaxLifetime","parameterTypes":["long"] }, {"name":"setMaximumPoolSize","parameterTypes":["int"] }, {"name":"setMetricRegistry","parameterTypes":["java.lang.Object"] }, {"name":"setMetricsTrackerFactory","parameterTypes":["com.zaxxer.hikari.metrics.MetricsTrackerFactory"] }, {"name":"setMinimumIdle","parameterTypes":["int"] }, {"name":"setPassword","parameterTypes":["java.lang.String"] }, {"name":"setPoolName","parameterTypes":["java.lang.String"] }, {"name":"setReadOnly","parameterTypes":["boolean"] }, {"name":"setRegisterMbeans","parameterTypes":["boolean"] }, {"name":"setScheduledExecutor","parameterTypes":["java.util.concurrent.ScheduledExecutorService"] }, {"name":"setSchema","parameterTypes":["java.lang.String"] }, {"name":"setThreadFactory","parameterTypes":["java.util.concurrent.ThreadFactory"] }, {"name":"setTransactionIsolation","parameterTypes":["java.lang.String"] }, {"name":"setUsername","parameterTypes":["java.lang.String"] }, {"name":"setValidationTimeout","parameterTypes":["long"] }]
+    "methods":[{"name":"getCatalog","parameterTypes":[] }, {"name":"getConnectionInitSql","parameterTypes":[] }, {"name":"getConnectionTestQuery","parameterTypes":[] }, {"name":"getConnectionTimeout","parameterTypes":[] }, {"name":"getCredentials","parameterTypes":[] }, {"name":"getCredentialsProvider","parameterTypes":[] }, {"name":"getCredentialsProviderClassName","parameterTypes":[] }, {"name":"getDataSource","parameterTypes":[] }, {"name":"getDataSourceClassName","parameterTypes":[] }, {"name":"getDataSourceJNDI","parameterTypes":[] }, {"name":"getDataSourceProperties","parameterTypes":[] }, {"name":"getDriverClassName","parameterTypes":[] }, {"name":"getExceptionOverride","parameterTypes":[] }, {"name":"getExceptionOverrideClassName","parameterTypes":[] }, {"name":"getHealthCheckProperties","parameterTypes":[] }, {"name":"getHealthCheckRegistry","parameterTypes":[] }, {"name":"getIdleTimeout","parameterTypes":[] }, {"name":"getInitializationFailTimeout","parameterTypes":[] }, {"name":"getJdbcUrl","parameterTypes":[] }, {"name":"getKeepaliveTime","parameterTypes":[] }, {"name":"getLeakDetectionThreshold","parameterTypes":[] }, {"name":"getMaxLifetime","parameterTypes":[] }, {"name":"getMaximumPoolSize","parameterTypes":[] }, {"name":"getMetricRegistry","parameterTypes":[] }, {"name":"getMetricsTrackerFactory","parameterTypes":[] }, {"name":"getMinimumIdle","parameterTypes":[] }, {"name":"getPassword","parameterTypes":[] }, {"name":"getPoolName","parameterTypes":[] }, {"name":"getScheduledExecutor","parameterTypes":[] }, {"name":"getSchema","parameterTypes":[] }, {"name":"getThreadFactory","parameterTypes":[] }, {"name":"getTransactionIsolation","parameterTypes":[] }, {"name":"getUsername","parameterTypes":[] }, {"name":"getValidationTimeout","parameterTypes":[] }, {"name":"isAllowPoolSuspension","parameterTypes":[] }, {"name":"isAutoCommit","parameterTypes":[] }, {"name":"isIsolateInternalQueries","parameterTypes":[] }, {"name":"isReadOnly","parameterTypes":[] }, {"name":"isRegisterMbeans","parameterTypes":[] }, {"name":"setAllowPoolSuspension","parameterTypes":["boolean"] }, {"name":"setAutoCommit","parameterTypes":["boolean"] }, {"name":"setCatalog","parameterTypes":["java.lang.String"] }, {"name":"setClass","parameterTypes":["java.lang.Class"] }, {"name":"setConnectionInitSql","parameterTypes":["java.lang.String"] }, {"name":"setConnectionTestQuery","parameterTypes":["java.lang.String"] }, {"name":"setConnectionTimeout","parameterTypes":["long"] }, {"name":"setCredentials","parameterTypes":["com.zaxxer.hikari.util.Credentials"] }, {"name":"setCredentialsProvider","parameterTypes":["com.zaxxer.hikari.HikariCredentialsProvider"] }, {"name":"setCredentialsProviderClassName","parameterTypes":["java.lang.String"] }, {"name":"setDataSource","parameterTypes":["javax.sql.DataSource"] }, {"name":"setDataSourceClassName","parameterTypes":["java.lang.String"] }, {"name":"setDataSourceJNDI","parameterTypes":["java.lang.String"] }, {"name":"setDataSourceProperties","parameterTypes":["java.util.Properties"] }, {"name":"setDriverClassName","parameterTypes":["java.lang.String"] }, {"name":"setExceptionOverride","parameterTypes":["com.zaxxer.hikari.SQLExceptionOverride"] }, {"name":"setExceptionOverrideClassName","parameterTypes":["java.lang.String"] }, {"name":"setHealthCheckProperties","parameterTypes":["java.util.Properties"] }, {"name":"setHealthCheckRegistry","parameterTypes":["java.lang.Object"] }, {"name":"setIdleTimeout","parameterTypes":["long"] }, {"name":"setInitializationFailTimeout","parameterTypes":["long"] }, {"name":"setIsolateInternalQueries","parameterTypes":["boolean"] }, {"name":"setJdbcUrl","parameterTypes":["java.lang.String"] }, {"name":"setKeepaliveTime","parameterTypes":["long"] }, {"name":"setLeakDetectionThreshold","parameterTypes":["long"] }, {"name":"setMaxLifetime","parameterTypes":["long"] }, {"name":"setMaximumPoolSize","parameterTypes":["int"] }, {"name":"setMetricRegistry","parameterTypes":["java.lang.Object"] }, {"name":"setMetricsTrackerFactory","parameterTypes":["com.zaxxer.hikari.metrics.MetricsTrackerFactory"] }, {"name":"setMinimumIdle","parameterTypes":["int"] }, {"name":"setPassword","parameterTypes":["java.lang.String"] }, {"name":"setPoolName","parameterTypes":["java.lang.String"] }, {"name":"setReadOnly","parameterTypes":["boolean"] }, {"name":"setRegisterMbeans","parameterTypes":["boolean"] }, {"name":"setScheduledExecutor","parameterTypes":["java.util.concurrent.ScheduledExecutorService"] }, {"name":"setSchema","parameterTypes":["java.lang.String"] }, {"name":"setThreadFactory","parameterTypes":["java.util.concurrent.ThreadFactory"] }, {"name":"setTransactionIsolation","parameterTypes":["java.lang.String"] }, {"name":"setUsername","parameterTypes":["java.lang.String"] }, {"name":"setValidationTimeout","parameterTypes":["long"] }]
   },
   {
     "name":"com.zaxxer.hikari.metrics.micrometer.MicrometerMetricsTrackerFactory",
```

### `jdbc-hikari/src/test/groovy/io/micronaut/configuration/jdbc/hikari/DatasourceConfigurationSpec.groovy`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jdbc-hikari/src/test/groovy/io/micronaut/configuration/jdbc/hikari/DatasourceConfigurationSpec.groovy	2026-04-22 07:32:32.147107833 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jdbc-hikari/src/test/groovy/io/micronaut/configuration/jdbc/hikari/DatasourceConfigurationSpec.groovy	2026-04-22 07:29:45.049869999 +0000
@@ -225,7 +225,7 @@
         String version = resultSet.getString(1)
 
         then:
-        version == '2.3.232'
+        version == '2.4.240'
 
         cleanup:
         applicationContext.close()
```

### `jdbc-tomcat/src/main/java/io/micronaut/configuration/jdbc/tomcat/DatasourceFactory.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jdbc-tomcat/src/main/java/io/micronaut/configuration/jdbc/tomcat/DatasourceFactory.java	2026-04-22 07:32:32.148481762 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jdbc-tomcat/src/main/java/io/micronaut/configuration/jdbc/tomcat/DatasourceFactory.java	2026-04-22 07:29:45.051553681 +0000
@@ -21,17 +21,19 @@
 import io.micronaut.context.annotation.EachBean;
 import io.micronaut.context.annotation.Factory;
 import io.micronaut.context.annotation.Requires;
-import io.micronaut.core.annotation.Nullable;
 import io.micronaut.jdbc.BaseDatasourceFactory;
 import io.micronaut.jdbc.DataSourceResolver;
 import io.micronaut.jdbc.JdbcDataSourceEnabled;
+import io.micronaut.jdbc.OracleSessionProgramHelper;
 import jakarta.annotation.PreDestroy;
+import org.jspecify.annotations.Nullable;
 import org.slf4j.Logger;
 import org.slf4j.LoggerFactory;
 
 import javax.sql.DataSource;
 import java.util.LinkedHashMap;
 import java.util.Map;
+import java.util.Properties;
 
 /**
  * Creates a tomcat data source for each configuration bean.
@@ -50,7 +52,9 @@
 
     /**
      * Default constructor.
+     *
      * @param dataSourceResolver The data source resolver
+     * @param applicationContext The application context
      */
     public DatasourceFactory(@Nullable DataSourceResolver dataSourceResolver,
                              ApplicationContext applicationContext) {
@@ -67,6 +71,27 @@
     @Requires(condition = JdbcDataSourceEnabled.class)
     public DataSource dataSource(DatasourceConfiguration datasourceConfiguration) {
         org.apache.tomcat.jdbc.pool.DataSource ds = new org.apache.tomcat.jdbc.pool.DataSource(datasourceConfiguration);
+        try {
+            OracleSessionProgramHelper.apply(
+                    datasourceConfiguration.getName(),
+                    datasourceConfiguration.getUrl(),
+                    applicationContext.getProperty("datasources." + datasourceConfiguration.getName() + ".dialect", String.class).orElse(null),
+                    applicationContext.getEnvironment(),
+                    (k, v) -> {
+                        Properties p = ds.getDbProperties();
+                        if (p == null) {
+                            p = new Properties();
+                            ds.setDbProperties(p);
+                        }
+                        p.setProperty(k, v);
+                    },
+                    () -> ds.getDbProperties() != null && ds.getDbProperties().containsKey("v$session.program")
+            );
+        } catch (Exception e) {
+            if (LOG.isDebugEnabled()) {
+                LOG.debug("Skipping Oracle session program auto-config due to: {}", e.getMessage());
+            }
+        }
         dataSources.put(datasourceConfiguration.getName(), ds);
         return ds;
     }
```

### `jdbc-tomcat/src/test/groovy/io/micronaut/configuration/jdbc/tomcat/DatasourceConfigurationSpec.groovy`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jdbc-tomcat/src/test/groovy/io/micronaut/configuration/jdbc/tomcat/DatasourceConfigurationSpec.groovy	2026-04-22 07:32:32.149589896 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jdbc-tomcat/src/test/groovy/io/micronaut/configuration/jdbc/tomcat/DatasourceConfigurationSpec.groovy	2026-04-22 07:29:45.052607482 +0000
@@ -226,7 +226,7 @@
         String version = resultSet.getString(1)
 
         then:
-        version == '2.3.232'
+        version == '2.4.240'
 
         cleanup:
         applicationContext.close()
```

### `jdbc-ucp/src/main/java/io/micronaut/configuration/jdbc/ucp/ConnectionPoolManagerListener.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jdbc-ucp/src/main/java/io/micronaut/configuration/jdbc/ucp/ConnectionPoolManagerListener.java	2026-04-22 07:32:32.150611864 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jdbc-ucp/src/main/java/io/micronaut/configuration/jdbc/ucp/ConnectionPoolManagerListener.java	2026-04-22 07:29:45.054094704 +0000
@@ -20,8 +20,10 @@
 import io.micronaut.context.event.BeanCreatedEventListener;
 import io.micronaut.context.exceptions.ConfigurationException;
 import io.micronaut.core.annotation.Internal;
+import io.micronaut.core.annotation.Nullable;
 import io.micronaut.core.order.Ordered;
 import io.micronaut.core.util.StringUtils;
+import io.micronaut.jdbc.DataSourceResolver;
 import jakarta.inject.Singleton;
 import oracle.ucp.UniversalConnectionPoolAdapter;
 import oracle.ucp.UniversalConnectionPoolException;
@@ -31,6 +33,7 @@
 import org.slf4j.LoggerFactory;
 
 import javax.sql.DataSource;
+import java.sql.SQLException;
 
 
 /**
@@ -49,35 +52,52 @@
 
     private final UniversalConnectionPoolManager connectionPoolManager;
 
-    public ConnectionPoolManagerListener(UniversalConnectionPoolManager connectionPoolManager) {
+    private final DataSourceResolver dataSourceResolver;
+
+    public ConnectionPoolManagerListener(UniversalConnectionPoolManager connectionPoolManager,
+                                         @Nullable DataSourceResolver dataSourceResolver) {
         this.connectionPoolManager = connectionPoolManager;
+        this.dataSourceResolver = dataSourceResolver == null ? DataSourceResolver.DEFAULT : dataSourceResolver;
     }
 
     @Override
     public DataSource onCreated(BeanCreatedEvent<DataSource> event) {
-        final DataSource dataSource = event.getBean();
-        if (dataSource instanceof PoolDataSource) {
-            final PoolDataSource poolDataSource = (PoolDataSource) dataSource;
-            final String poolName = poolDataSource.getConnectionPoolName();
+        final DataSource dataSource = dataSourceResolver.resolve(event.getBean());
+
+        if (dataSource instanceof PoolDataSource poolDataSource) {
+            createAndStartConnectionPool(poolDataSource);
+        } else {
             try {
-                if (LOG.isDebugEnabled()) {
-                    LOG.debug("Creating connection pool named: {}", poolName);
+                if (dataSource.isWrapperFor(PoolDataSource.class)) {
+                    createAndStartConnectionPool(dataSource.unwrap(PoolDataSource.class));
                 }
-                connectionPoolManager.createConnectionPool((UniversalConnectionPoolAdapter) dataSource);
+            } catch (SQLException e) {
+                throw new ConfigurationException(String.format("Failed to unwrap PoolDataSource from DataSource bean: %s", event.getBeanIdentifier()), e);
+            }
+        }
 
-                if (LOG.isDebugEnabled()) {
-                    LOG.debug("Starting connection pool named: {}", poolName);
-                }
-                connectionPoolManager.startConnectionPool(poolName);
-                if (LOG.isInfoEnabled()) {
-                    LOG.info("Connection pool named: {} started", poolName);
-                }
+        return event.getBean();
+    }
+
+    private void createAndStartConnectionPool(PoolDataSource poolDataSource) {
+        final String poolName = poolDataSource.getConnectionPoolName();
+        try {
+            if (LOG.isDebugEnabled()) {
+                LOG.debug("Creating connection pool named: {}", poolName);
+            }
+            connectionPoolManager.createConnectionPool((UniversalConnectionPoolAdapter) poolDataSource);
 
-            } catch (UniversalConnectionPoolException e) {
-                throw new ConfigurationException(String.format("Failed to start connection pool named: %s", poolName), e);
+            if (LOG.isDebugEnabled()) {
+                LOG.debug("Starting connection pool named: {}", poolName);
             }
+            connectionPoolManager.startConnectionPool(poolName);
+            if (LOG.isInfoEnabled()) {
+                LOG.info("Connection pool named: {} started", poolName);
+            }
+
+        } catch (UniversalConnectionPoolException e) {
+            throw new ConfigurationException(String.format("Failed to start connection pool named: %s", poolName), e);
         }
-        return event.getBean();
     }
 
     @Override
```

### `jdbc-ucp/src/main/java/io/micronaut/configuration/jdbc/ucp/DatasourceConfiguration.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jdbc-ucp/src/main/java/io/micronaut/configuration/jdbc/ucp/DatasourceConfiguration.java	2026-04-22 07:32:32.150702823 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jdbc-ucp/src/main/java/io/micronaut/configuration/jdbc/ucp/DatasourceConfiguration.java	2026-04-22 07:29:45.054201746 +0000
@@ -20,9 +20,11 @@
 import io.micronaut.context.annotation.EachProperty;
 import io.micronaut.context.annotation.Parameter;
 import io.micronaut.context.exceptions.ConfigurationException;
+import io.micronaut.context.env.Environment;
 import io.micronaut.core.util.StringUtils;
 import io.micronaut.jdbc.BasicJdbcConfiguration;
 import io.micronaut.jdbc.CalculatedSettings;
+import io.micronaut.jdbc.OracleSessionProgramHelper;
 import jakarta.annotation.PostConstruct;
 import oracle.ucp.jdbc.PoolDataSource;
 import oracle.ucp.jdbc.PoolDataSourceFactory;
@@ -50,6 +52,10 @@
 @EachProperty(value = BasicJdbcConfiguration.PREFIX, primary = "default")
 @Context
 public class DatasourceConfiguration implements BasicJdbcConfiguration {
+
+    private static final String ORACLE_VSESSION_PROGRAM = "v$session.program";
+    private static final String DATASOURCES_PREFIX = "datasources.";
+
     private static final Logger LOG = LoggerFactory.getLogger(DatasourceConfiguration.class);
 
     @ConfigurationBuilder(allowZeroArgs = true, excludes = {"connectionFactoryProperties", "URL", "username", "password"})
@@ -58,15 +64,19 @@
     private String name;
     private String username;
     private String password;
+    private final Properties dataSourceProperties = new Properties();
+    private final Environment environment;
 
     /**
      * Constructor.
      *
      * @param name name that comes from properties
+     * @param environment The Micronaut {@link Environment}
      */
-    public DatasourceConfiguration(@Parameter String name) throws SQLException {
+    public DatasourceConfiguration(@Parameter String name, Environment environment) throws SQLException {
         super();
         this.name = name;
+        this.environment = environment;
         this.delegate.setConnectionPoolName(name);
         this.calculatedSettings = new CalculatedSettings(this);
     }
@@ -200,18 +210,11 @@
     @Override
     public void setDataSourceProperties(Map<String, ?> dsProperties) {
         if (dsProperties != null) {
-            Properties properties = new Properties();
             dsProperties.forEach((key, value) -> {
                 if (value != null) {
-                    properties.put(key, value.toString());
+                    dataSourceProperties.put(key, value.toString());
                 }
             });
-
-            try {
-                this.delegate.setConnectionProperties(properties);
-            } catch (SQLException e) {
-                throw new ConfigurationException("Unable to set datasource properties: " + e.getMessage(), e);
-            }
         }
     }
 
@@ -220,7 +223,6 @@
         return delegate.getSQLForValidateConnection();
     }
 
-
     /**
      * Configures the missing properties of the data source from the calculated settings.
      *
@@ -228,13 +230,24 @@
      */
     @PostConstruct
     public void initialize() {
+        initializeDriverClassName();
+        initializeUrl();
+        initializeValidationQuery();
+        initializeUsername();
+        initializePassword();
+        initializeDataSourceProperties();
+    }
+
+    private void initializeDriverClassName() {
         if (StringUtils.isEmpty(getConfiguredDriverClassName()) && !StringUtils.isEmpty(getDriverClassName())) {
             if (LOG.isDebugEnabled()) {
                 LOG.debug("Configuring calculated driver class name: {}", getDriverClassName());
             }
             setDriverClassName(getDriverClassName());
         }
+    }
 
+    private void initializeUrl() {
         if (StringUtils.isEmpty(getConfiguredUrl())) {
             String url = null;
             try {
@@ -252,7 +265,9 @@
                 setUrl(url);
             }
         }
+    }
 
+    private void initializeValidationQuery() {
         if (StringUtils.isEmpty(getConfiguredValidationQuery())) {
             String validationQuery = null;
             try {
@@ -270,14 +285,18 @@
                 setValidationQuery(validationQuery);
             }
         }
+    }
 
+    private void initializeUsername() {
         if (StringUtils.isEmpty(getConfiguredUsername()) && !StringUtils.isEmpty(calculatedSettings.getUsername())) {
             if (LOG.isDebugEnabled()) {
                 LOG.debug("Configuring calculated username: {}", calculatedSettings.getUsername());
             }
             setUsername(calculatedSettings.getUsername());
         }
+    }
 
+    private void initializePassword() {
         if (StringUtils.isEmpty(getConfiguredPassword())) {
             if (LOG.isDebugEnabled()) {
                 LOG.debug("Configuring calculated password: *****");
@@ -285,4 +304,28 @@
             setPassword(getPassword());
         }
     }
+
+    private void initializeDataSourceProperties() {
+        try {
+            OracleSessionProgramHelper.apply(
+                getName(),
+                getConfiguredUrl(),
+                environment.getProperty(DATASOURCES_PREFIX + getName() + ".dialect", String.class).orElse(null),
+                environment,
+                dataSourceProperties::put,
+                () -> dataSourceProperties.containsKey(ORACLE_VSESSION_PROGRAM)
+            );
+        } catch (Exception e) {
+            if (LOG.isDebugEnabled()) {
+                LOG.debug("Skipping Oracle session program auto-config due to: {}", e.getMessage());
+            }
+        }
+        if (!dataSourceProperties.isEmpty()) {
+            try {
+                this.delegate.setConnectionProperties(dataSourceProperties);
+            } catch (SQLException e) {
+                throw new ConfigurationException("Unable to set datasource properties: " + e.getMessage(), e);
+            }
+        }
+    }
 }
```

### `jdbc-ucp/src/main/java/io/micronaut/configuration/jdbc/ucp/DatasourceFactory.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jdbc-ucp/src/main/java/io/micronaut/configuration/jdbc/ucp/DatasourceFactory.java	2026-04-22 07:32:32.150826408 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jdbc-ucp/src/main/java/io/micronaut/configuration/jdbc/ucp/DatasourceFactory.java	2026-04-22 07:29:45.054312497 +0000
@@ -15,6 +15,7 @@
  */
 package io.micronaut.configuration.jdbc.ucp;
 
+import io.micronaut.configuration.jdbc.ucp.metadata.OracleUcpDataSourcePoolMetadata;
 import io.micronaut.context.ApplicationContext;
 import io.micronaut.context.annotation.Context;
 import io.micronaut.context.annotation.EachBean;
@@ -22,14 +23,17 @@
 import io.micronaut.context.annotation.Requires;
 import io.micronaut.context.exceptions.NoSuchBeanException;
 import io.micronaut.jdbc.BaseDatasourceFactory;
+import io.micronaut.jdbc.DataSourceResolver;
 import io.micronaut.jdbc.JdbcDataSourceEnabled;
 import oracle.ucp.admin.UniversalConnectionPoolManager;
 import oracle.ucp.jdbc.PoolDataSource;
+import org.jspecify.annotations.Nullable;
 import org.slf4j.Logger;
 import org.slf4j.LoggerFactory;
 
 import jakarta.annotation.PreDestroy;
 
+import javax.sql.DataSource;
 import java.sql.SQLException;
 import java.util.LinkedHashMap;
 import java.util.Map;
@@ -48,13 +52,16 @@
 
     private final Map<String, PoolDataSource> dataSources = new LinkedHashMap<>(2);
     private UniversalConnectionPoolManager connectionPoolManager;
+    private final DataSourceResolver dataSourceResolver;
 
     /**
      * Default constructor.
      *
+     * @param dataSourceResolver The data source resolver
      * @param applicationContext The application context
      */
-    public DatasourceFactory(ApplicationContext applicationContext) {
+    public DatasourceFactory(@Nullable DataSourceResolver dataSourceResolver,
+                             ApplicationContext applicationContext) {
         super(applicationContext);
         this.configuration = applicationContext.getBean(UniversalConnectionPoolManagerConfiguration.class);
         try {
@@ -62,6 +69,7 @@
         } catch (NoSuchBeanException e) {
             // no-op
         }
+        this.dataSourceResolver = dataSourceResolver == null ? DataSourceResolver.DEFAULT : dataSourceResolver;
     }
 
     /**
@@ -80,6 +88,23 @@
         return ds;
     }
 
+    /**
+     * Method to create a metadata object that allows pool value lookup for each datasource object.
+     *
+     * @param dataSource The actual datasource
+     * @return a {@link OracleUcpDataSourcePoolMetadata}
+     */
+    @EachBean(DataSource.class)
+    @Requires(beans = {DatasourceConfiguration.class})
+    public OracleUcpDataSourcePoolMetadata ucpDataSourcePoolMetadata(DataSource dataSource) {
+        OracleUcpDataSourcePoolMetadata ucpDataSourcePoolMetadata = null;
+
+        if (dataSourceResolver.resolve(dataSource) instanceof PoolDataSource resolved) {
+            ucpDataSourcePoolMetadata = new OracleUcpDataSourcePoolMetadata(resolved, connectionPoolManager);
+        }
+        return ucpDataSourcePoolMetadata;
+    }
+
     @Override
     @PreDestroy
     public void close() {
```

### `jdbc-ucp/src/main/java/io/micronaut/configuration/jdbc/ucp/OracleUcpConfiguration.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jdbc-ucp/src/main/java/io/micronaut/configuration/jdbc/ucp/OracleUcpConfiguration.java	2026-04-22 07:32:32.150912992 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jdbc-ucp/src/main/java/io/micronaut/configuration/jdbc/ucp/OracleUcpConfiguration.java	2026-04-22 07:29:45.054408373 +0000
@@ -17,7 +17,7 @@
 
 import io.micronaut.context.annotation.ConfigurationProperties;
 import io.micronaut.context.annotation.Requires;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 
 import static io.micronaut.configuration.jdbc.ucp.OracleUcpConfiguration.PREFIX;
 
```

### `jdbc-ucp/src/main/java/io/micronaut/configuration/jdbc/ucp/OracleUcpConfigurator.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jdbc-ucp/src/main/java/io/micronaut/configuration/jdbc/ucp/OracleUcpConfigurator.java	2026-04-22 07:32:32.150993409 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jdbc-ucp/src/main/java/io/micronaut/configuration/jdbc/ucp/OracleUcpConfigurator.java	2026-04-22 07:29:45.054502291 +0000
@@ -18,7 +18,7 @@
 import io.micronaut.context.annotation.Context;
 import io.micronaut.context.annotation.Requires;
 import io.micronaut.core.annotation.Internal;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import jakarta.annotation.PostConstruct;
 import oracle.ucp.jdbc.PoolDataSource;
 
```

### `jdbc-ucp/src/test/groovy/io/micronaut/configuration/jdbc/ucp/DatasourceConfigurationSpec.groovy`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jdbc-ucp/src/test/groovy/io/micronaut/configuration/jdbc/ucp/DatasourceConfigurationSpec.groovy	2026-04-22 07:32:32.151653707 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jdbc-ucp/src/test/groovy/io/micronaut/configuration/jdbc/ucp/DatasourceConfigurationSpec.groovy	2026-04-22 07:29:45.055741260 +0000
@@ -15,6 +15,7 @@
  */
 package io.micronaut.configuration.jdbc.ucp
 
+import io.micronaut.configuration.jdbc.ucp.metadata.OracleUcpDataSourcePoolMetadata
 import io.micronaut.context.ApplicationContext
 import io.micronaut.context.DefaultApplicationContext
 import io.micronaut.context.env.MapPropertySource
@@ -40,6 +41,7 @@
         expect: "No beans are created"
         !applicationContext.containsBean(PoolDataSource)
         !applicationContext.containsBean(DatasourceConfiguration)
+        !applicationContext.containsBean(OracleUcpDataSourcePoolMetadata)
 
         cleanup:
         applicationContext.close()
@@ -65,6 +67,7 @@
         expect:
         applicationContext.containsBean(PoolDataSource)
         applicationContext.containsBean(DatasourceConfiguration)
+        applicationContext.containsBean(OracleUcpDataSourcePoolMetadata)
 
         when:
         PoolDataSource dataSource = dataSourceResolver.resolve(applicationContext.getBean(DataSource))
@@ -94,6 +97,7 @@
         expect:
         applicationContext.containsBean(PoolDataSource)
         applicationContext.containsBean(DatasourceConfiguration)
+        applicationContext.containsBean(OracleUcpDataSourcePoolMetadata)
 
         when:
         PoolDataSource dataSource = dataSourceResolver.resolve(applicationContext.getBean(DataSource))
@@ -182,6 +186,11 @@
         then:
         thrown(NoSuchBeanException)
 
+        when:
+        applicationContext.getBean(OracleUcpDataSourcePoolMetadata, Qualifiers.byName('default'))
+        then:
+        thrown(NoSuchBeanException)
+
         cleanup:
         applicationContext.close()
     }
@@ -364,6 +373,47 @@
 
         cleanup:
         applicationContext.close()
+    }
+
+    void "test multiple datasources metadata props"() {
+        given:
+        String context = UUID.randomUUID().toString()
+        ApplicationContext applicationContext = new DefaultApplicationContext(context)
+        applicationContext.environment.addPropertySource(MapPropertySource.of(
+                context,
+                [
+                        'datasources.default.initialPoolSize'          : 5,
+                        'datasources.default.minPoolSize'              : 5,
+                        'datasources.default.maxPoolSize'              : 20,
+
+                        'datasources.person.initialPoolSize'           : 1,
+                        'datasources.person.minPoolSize'               : 1,
+                        'datasources.person.maxPoolSize'               : 10,
+                ]
+        ))
+        applicationContext.start()
+
+        def metadataDefault = applicationContext.getBean(OracleUcpDataSourcePoolMetadata, Qualifiers.byName("default"))
+        def metadataPerson = applicationContext.getBean(OracleUcpDataSourcePoolMetadata, Qualifiers.byName("person"))
+
+        expect:
+        verifyAll {
+            applicationContext.getBeansOfType(DataSource).size() == 2
+            applicationContext.getBeansOfType(DatasourceConfiguration).size() == 2
+
+            metadataDefault.max == 20
+            metadataDefault.min == 5
+            metadataDefault.active == 0
+            metadataDefault.idle >= 0
+
+            metadataPerson.max == 10
+            metadataPerson.min == 1
+            metadataPerson.active == 0
+            metadataPerson.idle >= 0
+        }
+
+        cleanup:
+        applicationContext.close()
     }
 
     void "test pool is created without dupe properties"() {
```

### `jdbi/build.gradle`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jdbi/build.gradle	2026-04-22 07:32:32.158853146 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jdbi/build.gradle	2026-04-22 07:29:45.065636057 +0000
@@ -54,6 +54,8 @@
     txTestImplementation(mnTest.micronaut.test.spock)
 
     txTestImplementation(mnData.micronaut.data.tx.jdbc)
+
+    txTestRuntimeOnly(mnTest.junit.platform.launcher)
 }
 
 
```

### `jdbi/src/main/java/io/micronaut/configuration/jdbi/JdbiFactory.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jdbi/src/main/java/io/micronaut/configuration/jdbi/JdbiFactory.java	2026-04-22 07:32:32.159265567 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jdbi/src/main/java/io/micronaut/configuration/jdbi/JdbiFactory.java	2026-04-22 07:29:45.066148312 +0000
@@ -18,7 +18,7 @@
 import io.micronaut.context.annotation.EachBean;
 import io.micronaut.context.annotation.Factory;
 import io.micronaut.context.annotation.Parameter;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.core.reflect.ClassUtils;
 import org.jdbi.v3.core.Jdbi;
 import org.jdbi.v3.core.h2.H2DatabasePlugin;
```

### `jdbi/src/main/java/io/micronaut/configuration/jdbi/transaction/micronaut/MicronautDataTransactionHandler.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jdbi/src/main/java/io/micronaut/configuration/jdbi/transaction/micronaut/MicronautDataTransactionHandler.java	2026-04-22 07:32:32.159541194 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jdbi/src/main/java/io/micronaut/configuration/jdbi/transaction/micronaut/MicronautDataTransactionHandler.java	2026-04-22 07:29:45.066489607 +0000
@@ -77,7 +77,7 @@
     }
 
     @Override
-    public <R, X extends Exception> R inTransaction(Handle handle, TransactionIsolationLevel level, HandleCallback<R, X> callback) throws X {
+    public <R, X extends Exception> R inTransaction(Handle handle, TransactionIsolationLevel level, HandleCallback<R, X> callback) {
         DefaultTransactionDefinition transactionDefinition = new DefaultTransactionDefinition(TransactionDefinition.Propagation.REQUIRED);
         transactionDefinition.setIsolationLevel(switch (level) {
             case NONE, UNKNOWN -> TransactionDefinition.Isolation.DEFAULT;
@@ -121,7 +121,7 @@
     }
 
     private DefaultTransactionStatus<Connection> getRequiredTxStatus() {
-        return transactionManager.findTransactionStatus()
+        return transactionManager.findTransactionStatusInternal()
             .orElseThrow(() -> new IllegalStateException("No transaction status found"));
     }
 
```

### `jooq/build.gradle`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jooq/build.gradle	2026-04-22 07:32:32.161990174 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jooq/build.gradle	2026-04-22 07:29:45.069070088 +0000
@@ -26,6 +26,7 @@
 
     api projects.micronautJdbc
     api(mn.micronaut.inject)
+    api(platform(libs.boms.jooq))
     api(libs.managed.jooq)
 
     compileOnly(mnSpring.spring.jdbc)
@@ -55,6 +56,8 @@
     txTestImplementation(mnData.micronaut.data.tx.jdbc)
     txTestImplementation(mn.micronaut.inject.groovy)
     txTestImplementation(mnTest.micronaut.test.spock)
+
+    txTestRuntimeOnly(mnTest.junit.platform.launcher)
 }
 
 task txTest(type: Test) {
```

### `jooq/src/main/java/io/micronaut/configuration/jooq/AbstractJooqConfigurationFactory.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jooq/src/main/java/io/micronaut/configuration/jooq/AbstractJooqConfigurationFactory.java	2026-04-22 07:32:32.162460970 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jooq/src/main/java/io/micronaut/configuration/jooq/AbstractJooqConfigurationFactory.java	2026-04-22 07:29:45.069473925 +0000
@@ -18,7 +18,7 @@
 import io.micronaut.context.ApplicationContext;
 import io.micronaut.context.annotation.Parameter;
 import io.micronaut.core.annotation.Internal;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.inject.qualifiers.Qualifiers;
 import org.jooq.ConverterProvider;
 import org.jooq.DiagnosticsListenerProvider;
```

### `jooq/src/main/java/io/micronaut/configuration/jooq/DSLContextFactory.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jooq/src/main/java/io/micronaut/configuration/jooq/DSLContextFactory.java	2026-04-22 07:32:32.162616472 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jooq/src/main/java/io/micronaut/configuration/jooq/DSLContextFactory.java	2026-04-22 07:29:45.069630343 +0000
@@ -18,8 +18,13 @@
 import io.micronaut.context.annotation.EachBean;
 import io.micronaut.context.annotation.Factory;
 import io.micronaut.core.annotation.Internal;
+import io.micronaut.transaction.TransactionStatus;
+import io.micronaut.transaction.support.ExceptionUtil;
 import org.jooq.Configuration;
 import org.jooq.DSLContext;
+import org.jooq.TransactionProperty;
+import org.jooq.TransactionalCallable;
+import org.jooq.TransactionalRunnable;
 import org.jooq.impl.DefaultDSLContext;
 
 /**
@@ -40,7 +45,59 @@
      */
     @EachBean(Configuration.class)
     DSLContext dslContext(Configuration configuration) {
-        return new DefaultDSLContext(configuration);
+        return new DefaultDSLContext(configuration) {
+
+            @Override
+            public <T> T transactionResult(TransactionalCallable<T> transactional) {
+                return super.transactionResult(propagateTransaction(transactional));
+            }
+
+            @Override
+            public <T> T transactionResult(TransactionalCallable<T> transactional, TransactionProperty... properties) {
+                return super.transactionResult(propagateTransaction(transactional), properties);
+            }
+
+            @Override
+            public void transaction(TransactionalRunnable transactional) {
+                super.transaction(propagateTransaction(transactional));
+            }
+
+            @Override
+            public void transaction(TransactionalRunnable transactional, TransactionProperty... properties) {
+                super.transaction(propagateTransaction(transactional), properties);
+            }
+
+            private <T> TransactionalCallable<T> propagateTransaction(TransactionalCallable<T> transactional) {
+                return new TransactionalCallable<>() {
+                    @Override
+                    public T run(Configuration configuration) throws Throwable {
+                        TransactionStatus<?> transactionStatus = (TransactionStatus<?>) configuration.data().get(MicronautTransactionProvider.TX_KEY);
+                        if (transactionStatus != null) {
+                            return transactionStatus.propagate(() -> {
+                                try {
+                                    return transactional.run(configuration);
+                                } catch (Throwable e) {
+                                    return ExceptionUtil.sneakyThrow(e);
+                                }
+                            });
+                        }
+                        return transactional.run(configuration);
+                    }
+                };
+            }
+
+            private TransactionalRunnable propagateTransaction(TransactionalRunnable transactional) {
+                return new TransactionalRunnable() {
+                    @Override
+                    public void run(Configuration configuration) throws Throwable {
+                        propagateTransaction((TransactionalCallable<Void>) innerConfiguration -> {
+                            transactional.run(innerConfiguration);
+                            return null;
+                        }).run(configuration);
+                    }
+                };
+            }
+        };
     }
 
 }
```

### `jooq/src/main/java/io/micronaut/configuration/jooq/JooqConfigurationFactory.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jooq/src/main/java/io/micronaut/configuration/jooq/JooqConfigurationFactory.java	2026-04-22 07:32:32.162710848 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jooq/src/main/java/io/micronaut/configuration/jooq/JooqConfigurationFactory.java	2026-04-22 07:29:45.069714844 +0000
@@ -20,7 +20,7 @@
 import io.micronaut.context.annotation.Factory;
 import io.micronaut.context.annotation.Parameter;
 import io.micronaut.core.annotation.Internal;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.jdbc.DataSourceResolver;
 import org.jooq.Configuration;
 import org.jooq.ConnectionProvider;
```

### `jooq/src/main/java/io/micronaut/configuration/jooq/JsonConverterProvider.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jooq/src/main/java/io/micronaut/configuration/jooq/JsonConverterProvider.java	2026-04-22 07:32:32.162898891 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jooq/src/main/java/io/micronaut/configuration/jooq/JsonConverterProvider.java	2026-04-22 07:29:45.069894887 +0000
@@ -16,7 +16,7 @@
 package io.micronaut.configuration.jooq;
 
 import io.micronaut.context.annotation.Requires;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.core.type.Argument;
 import io.micronaut.json.JsonMapper;
 import jakarta.inject.Singleton;
```

### `jooq/src/main/java/io/micronaut/configuration/jooq/MicronautTransactionProvider.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jooq/src/main/java/io/micronaut/configuration/jooq/MicronautTransactionProvider.java	2026-04-22 07:32:32.163075351 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jooq/src/main/java/io/micronaut/configuration/jooq/MicronautTransactionProvider.java	2026-04-22 07:29:45.070080764 +0000
@@ -39,6 +39,11 @@
 @EachBean(DataSourceTransactionManager.class)
 public class MicronautTransactionProvider implements TransactionProvider {
 
+    /**
+     * The key to store the transaction.
+     */
+    static final String TX_KEY = "io.micronaut.transaction";
+
     private final DataSourceTransactionManager transactionManager;
 
     /**
@@ -55,6 +60,7 @@
         TransactionDefinition definition = TransactionDefinition.DEFAULT;
         TransactionStatus<Connection> status = transactionManager.getTransaction(definition);
         context.transaction(new MicronautTransaction(status));
+        context.configuration().data().put(TX_KEY, status);
     }
 
     @Override
```

### `jooq/src/main/java/io/micronaut/configuration/jooq/R2dbcJooqConfigurationFactory.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jooq/src/main/java/io/micronaut/configuration/jooq/R2dbcJooqConfigurationFactory.java	2026-04-22 07:32:32.163153810 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jooq/src/main/java/io/micronaut/configuration/jooq/R2dbcJooqConfigurationFactory.java	2026-04-22 07:29:45.070168473 +0000
@@ -21,7 +21,7 @@
 import io.micronaut.context.annotation.Parameter;
 import io.micronaut.context.annotation.Requires;
 import io.micronaut.core.annotation.Internal;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.r2dbc.spi.ConnectionFactory;
 import org.jooq.Configuration;
 import org.jooq.ConverterProvider;
```

### `jooq/src/main/resources/META-INF/native-image/io.micronaut.sql/jooq-graal/native-image.properties`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jooq/src/main/resources/META-INF/native-image/io.micronaut.sql/jooq-graal/native-image.properties	2026-04-22 07:32:32.164127360 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jooq/src/main/resources/META-INF/native-image/io.micronaut.sql/jooq-graal/native-image.properties	2026-04-22 07:29:45.071212232 +0000
@@ -16,4 +16,8 @@
 
 Args = -H:ClassInitialization=org.jooq.SQLDialect$ThirdParty:build_time \
        --initialize-at-run-time=io.micronaut.configuration.jooq.spring.SpringTransactionProvider,io.micronaut.configuration.jooq.spring.JooqExceptionTranslator \
-       --initialize-at-build-time=org.simpleflatmapper.reflect.DefaultReflectionService
+       --initialize-at-build-time=org.simpleflatmapper.reflect.DefaultReflectionService \
+       --initialize-at-build-time=org.jooq.impl.DefaultDataType,org.jooq.impl.SQLDataType,org.jooq.impl.BuiltInDataType,org.jooq.impl.ArrayDataType,org.jooq.impl.AbstractDataType,org.jooq.SQLDialect,org.jooq.impl.DefaultBinding,org.jooq.impl.BlobBinding,org.jooq.conf.SettingsTools,org.jooq.impl.DefaultBinding$DefaultTimeBinding,org.jooq.impl.DefaultBinding$DefaultYearToSecondBinding,org.jooq.impl.DefaultBinding$DefaultBigIntegerBinding,org.jooq.impl.DefaultBinding$DefaultRecordBinding,org.jooq.impl.DefaultBinding$DefaultBigDecimalBinding,org.jooq.impl.DefaultConfiguration,org.jooq.impl.DefaultBinding$DefaultArrayBinding,org.jooq.impl.DefaultBinding$DefaultDayToSecondBinding,org.jooq.XMLFormat,org.jooq.impl.DefaultBinding$DefaultResultBinding,org.jooq.impl.Tools,org.jooq.SchemaMapping,org.jooq.impl.AbstractConfiguration,org.jooq.impl.DefaultBinding$DefaultYearToMonthBinding,org.jooq.impl.DefaultBinding$DefaultOffsetDateTimeBinding,org.jooq.impl.DefaultBinding$DefaultJSONBBinding,org.jooq.JSONFormat,org.jooq.impl.DefaultBinding$DefaultDateBinding,org.jooq.tools.JooqLogger,org.jooq.impl.AbstractName,org.jooq.impl.DefaultBinding$DefaultTimestampBinding,org.jooq.impl.UnqualifiedName,org.jooq.impl.DefaultBinding$DefaultBooleanBinding,org.jooq.impl.DefaultBinding$DefaultInstantBinding,org.jooq.impl.Internal,org.jooq.impl.InternalConfiguration,ch.qos.logback.core.subst.NodeToStringTransformer$1,org.jooq.impl.AbstractDataType$1,org.jooq.impl.DefaultBinding$DefaultDoubleBinding,org.jooq.util.mariadb.MariaDBDataType,org.jooq.util.mysql.MySQLDataType,org.jooq.util.firebird.FirebirdDataType,org.jooq.util.h2.H2DataType,org.jooq.util.yugabytedb.YugabyteDBDataType,org.jooq.util.postgres.PostgresDataType,org.jooq.util.ignite.IgniteDataType,org.jooq.util.derby.DerbyDataType,org.jooq.util.cubrid.CUBRIDDataType,org.jooq.util.hsqldb.HSQLDBDataType,org.jooq.util.sqlite.SQLiteDataType \
+       --initialize-at-build-time=ch.qos.logback.core.status.InfoStatus,ch.qos.logback.core.util.Duration,ch.qos.logback.classic.Level,org.slf4j.helpers.Reporter,ch.qos.logback.core.pattern.parser.Parser,ch.qos.logback.classic.PatternLayout,ch.qos.logback.core.status.StatusBase,ch.qos.logback.core.subst.Token,ch.qos.logback.core.util.StatusPrinter,ch.qos.logback.core.util.StatusPrinter2,org.slf4j.LoggerFactory,ch.qos.logback.core.model.processor.DefaultProcessor$1,ch.qos.logback.core.model.processor.ChainedModelFilter$1,ch.qos.logback.core.joran.JoranConstants,ch.qos.logback.classic.Logger,ch.qos.logback.core.model.processor.ImplicitModelHandler$1,ch.qos.logback.core.util.Loader,ch.qos.logback.classic.model.processor.LogbackClassicDefaultNestedComponentRules,ch.qos.logback.core.CoreConstants,ch.qos.logback.core.subst.Parser$1 \
+       --initialize-at-build-time=org.jooq,org.jooq.impl,org.jooq.conf \
+       --initialize-at-build-time=org.xml.sax.helpers,ch.qos.logback.core,ch.qos.logback.core.joran.spi,ch.qos.logback.core.model,ch.qos.logback.classic,ch.qos.logback.classic.model,ch.qos.logback.classic.spi,ch.qos.logback.core.spi,ch.qos.logback.core.util,org.slf4j.helpers
```

### `jooq/src/test/groovy/io/micronaut/configuration/jooq/CustomConverterProvider.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jooq/src/test/groovy/io/micronaut/configuration/jooq/CustomConverterProvider.java	2026-04-22 07:32:32.164565739 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jooq/src/test/groovy/io/micronaut/configuration/jooq/CustomConverterProvider.java	2026-04-22 07:29:45.071652236 +0000
@@ -15,7 +15,7 @@
  */
 package io.micronaut.configuration.jooq;
 
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import org.jooq.Converter;
 import org.jooq.ConverterProvider;
 import org.jooq.impl.DefaultConverterProvider;
```

### `jooq/src/txTest/groovy/io/micronaut/configuration/jooq/TxDslContextSpec.groovy`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/jooq/src/txTest/groovy/io/micronaut/configuration/jooq/TxDslContextSpec.groovy	2026-04-22 07:32:32.165701374 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/jooq/src/txTest/groovy/io/micronaut/configuration/jooq/TxDslContextSpec.groovy	2026-04-22 07:29:45.072619578 +0000
@@ -21,6 +21,7 @@
 import org.jooq.Configuration
 import org.jooq.DSLContext
 import org.jooq.SQLDialect
+import org.jooq.TransactionProperty
 import org.jooq.TransactionalCallable
 import org.jooq.TransactionalRunnable
 import org.jooq.impl.DSL
@@ -153,4 +154,34 @@
         applicationContext.close()
     }
 
+    void "test transaction sql with properties"() {
+        given:
+        ApplicationContext applicationContext = new DefaultApplicationContext("test")
+        applicationContext.environment.addPropertySource(MapPropertySource.of(
+                'test',
+                ['datasources.default': [:]]
+        ))
+        applicationContext.start()
+        DSLContext db = applicationContext.getBean(DSLContext)
+        TxTestService service = applicationContext.getBean(TxTestService)
+        TransactionProperty property = new TransactionProperty() { }
+        int countBefore = service.count()
+
+        when:
+        db.transaction((TransactionalRunnable) { conf ->
+            DSL.using(conf).execute("DELETE FROM foo;")
+            def count = DSL.using(conf).fetchCount(DSL.table("foo"))
+            throw new RuntimeException("count=" + count)
+        }, property)
+
+        then:
+        RuntimeException ex = thrown()
+        ex.message == "count=0"
+        service.count() == countBefore
+
+        cleanup:
+        applicationContext.close()
+    }
+
+
 }
```

### `sql-bom/build.gradle`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/sql-bom/build.gradle	2026-04-22 07:32:32.166139795 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/sql-bom/build.gradle	2026-04-22 07:29:45.073315835 +0000
@@ -11,6 +11,7 @@
 micronautBom {
     suppressions {
         acceptedLibraryRegressions.add("micronaut-hibernate-jpa-spring")
+        acceptedLibraryRegressions.add("micronaut-jdbc-unpooled")
         acceptedVersionRegressions.add("commons-dbcp-compat")
         acceptedLibraryRegressions.add("commons-dbcp")
     }
```

### `src/main/docs/guide/hibernate/hibernate-inject-session.adoc`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/src/main/docs/guide/hibernate/hibernate-inject-session.adoc	2026-04-22 07:32:32.166921469 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/src/main/docs/guide/hibernate/hibernate-inject-session.adoc	2026-04-22 07:29:45.073981215 +0000
@@ -1,4 +1,4 @@
-You can use the `javax.persistence.PersistenceContext` annotation to inject an `EntityManager` (or Hibernate `Session`). To do so you need to make sure the JPA annotations are on the `annotationProcessor` path in your build:
+You can use the `jakarta.persistence.PersistenceContext` annotation to inject an `EntityManager` (or Hibernate `Session`). To do so you need to make sure the JPA annotations are on the `annotationProcessor` path in your build:
 
 [source,groovy]
 .Adding the JPA dependency to `annotationProcessor` in Gradle
@@ -17,13 +17,3 @@
 ----
 
 Micronaut will inject a compile time scoped proxy that retrieves the `EntityManager` associated with the current transaction when using https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/transaction/annotation/Transactional.html[@Transactional] (see "Using Spring Transaction Management" below).
-
-Note the examples above use field injection, since the `@PersistenceContext` annotation does not support declaration on a parameter of a constructor or method argument. Therefore if you wish to instead use constructor or method injection you must use the ann:configuration.hibernate.jpa.scope.CurrentSession[] instead:
-
-[source,java]
-.Using `@CurrentSession` for constructor injection
-----
-public MyService(@CurrentSession EntityManager entityManager) {
-     this.entityManager = entityManager;
-}
-----
```

### `src/main/docs/guide/jdbc/jdbc-connection-pools.adoc`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/src/main/docs/guide/jdbc/jdbc-connection-pools.adoc	2026-04-22 07:32:32.167728059 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/src/main/docs/guide/jdbc/jdbc-connection-pools.adoc	2026-04-22 07:29:45.075152976 +0000
@@ -1,5 +1,7 @@
 All of the implementation specific parameters can be configured. Effort was made to allow basic configuration to be consistent across the implementations.
 
+If you want Micronaut to avoid connection pooling entirely, add the `micronaut-jdbc-unpooled` module instead. It uses the same common datasource settings, creates a new physical JDBC connection for each `getConnection()` call, and closes that physical connection when the caller closes it.
+
 * Hikari: The URL is able to be configured through `url` in addition to `jdbcUrl`. The JNDI name can be configured through `jndiName` in addition to `dataSourceJNDI`.
 * Tomcat: The JNDI name can be configured through `jndiName` in addition to `dataSourceJNDI`.
 
@@ -61,17 +63,17 @@
 |=======
 |Connection Pool |Javadoc |Configuration |Pool Documentation
 
-|Tomcat 
+|Tomcat
 |link:https://tomcat.apache.org/tomcat-9.0-doc/api/org/apache/tomcat/jdbc/pool/PoolProperties.html[PoolProperties]
 |https://micronaut-projects.github.io/micronaut-sql/latest/guide/configurationreference.html#io.micronaut.configuration.jdbc.tomcat.DatasourceConfiguration[DatasourceConfiguration]
 |https://tomcat.apache.org/tomcat-7.0-doc/jdbc-pool.html[Tomcat Connection Pool]
 
-|Hikari 
+|Hikari
 |link:http://static.javadoc.io/com.zaxxer/HikariCP/2.7.1/com/zaxxer/hikari/HikariConfig.html[HikariConfig]
 |https://micronaut-projects.github.io/micronaut-sql/latest/guide/configurationreference.html#io.micronaut.configuration.jdbc.hikari.DatasourceConfiguration[DatasourceConfiguration]
 |https://github.com/brettwooldridge/HikariCP?tab=readme-ov-file#gear-configuration-knobs-baby[Hikari Docs]
 
-|Apache DBCP 
+|Apache DBCP
 |link:http://commons.apache.org/proper/commons-dbcp/api-2.1.1/org/apache/commons/dbcp2/BasicDataSource.html[BasicDataSource]
 |https://micronaut-projects.github.io/micronaut-sql/latest/guide/configurationreference.html#io.micronaut.configuration.jdbc.dbcp.DatasourceConfiguration[DatasourceConfiguration]
 |https://commons.apache.org/proper/commons-dbcp/configuration.html[Apache DBCP Configuration]
@@ -83,3 +85,58 @@
 |https://docs.oracle.com/en/database/oracle/oracle-database/21/jjucp/intro.html#GUID-197BA5D3-86DA-43BE-AFC6-E8CBED4883EF[Oracle UCP]
 
 |=======
+
+=== Oracle Session Program Auto-Configuration
+
+Micronaut SQL can automatically set the Oracle `v$session.program` connection property so your application's sessions are easily identifiable in Oracle tools (such as `v$session`).
+
+- Applied only to Oracle datasources (when `dialect: ORACLE` is set or the JDBC URL starts with `jdbc:oracle`).
+- The value is taken from `micronaut.application.name`.
+- Does not override a user-provided `v$session.program`.
+- Supported for HikariCP, Tomcat JDBC, Apache DBCP2, and Oracle UCP.
+- Scope limited to `v$session.program` only (it does not set ClientId/Module/Action).
+
+Configure per datasource:
+
+[configuration]
+----
+micronaut:
+  application:
+    name: my-app
+
+datasources:
+  default:
+    url: jdbc:oracle:thin:@localhost:1521/orcl
+    username: user
+    password: pass
+    dialect: ORACLE
+
+  other:
+    url: jdbc:oracle:thin:@localhost:1521/orcl
+    username: user
+    password: pass
+    dialect: ORACLE
+    oracle:
+      session:
+        enabled: false
+----
+<1> The `default` data source auto-sets v$session.program = "my-app"
+<2> The `other` data source v$session.program not auto-set because `datasources.other.oracle.session.enabled` is set to `false`
+
+Alternatively, this configuration will set "My Program" as session name for the Oracle connection and Micronaut
+will not try to use application name for it:
+
+[configuration]
+----
+micronaut:
+  application:
+    name: my-app
+datasources:
+  default:
+    url: jdbc:oracle:thin:@localhost:1521/orcl
+    username: user
+    password: pass
+    dialect: ORACLE
+    data-source-properties:
+      v$session.program: "My Program"
+----
```

### `src/main/docs/guide/jdbc.adoc`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/src/main/docs/guide/jdbc.adoc	2026-04-22 07:32:32.167589308 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/src/main/docs/guide/jdbc.adoc	2026-04-22 07:29:45.074624388 +0000
@@ -1,4 +1,4 @@
-Java data sources can be configured for one of four currently provided implementations. Apache DBCP2, Hikari, Tomcat, and Oracle Universal Connection Pool are supported by default.
+Java data sources can be configured for one of five currently provided implementations. Apache DBCP2, Hikari, Tomcat, Oracle Universal Connection Pool, and an unpooled DriverManager-backed datasource are supported by default.
 
 [TIP]
 .Using the CLI
@@ -19,7 +19,14 @@
 
 dependency:micronaut-jdbc-ucp[groupId="io.micronaut.sql", scope="runtime"]
 
+dependency:micronaut-jdbc-unpooled[groupId="io.micronaut.sql", scope="runtime"]
+
 You also need to add a JDBC driver dependency to your classpath. For example to add the http://www.h2database.com[H2 In-Memory Database]:
 
 dependency:h2[groupId="com.h2database", scope="runtime"]
 
+To use SQLite, add the Xerial JDBC driver:
+
+dependency:sqlite-jdbc[groupId="org.xerial", scope="runtime"]
+
+When the SQLite driver is present, Micronaut can automatically configure an embedded shared in-memory datasource for `db-type: sqlite` if you do not provide an explicit JDBC URL.
```

### `src/main/docs/guide/jooq.adoc`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/src/main/docs/guide/jooq.adoc	2026-04-22 07:32:32.168215605 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/src/main/docs/guide/jooq.adoc	2026-04-22 07:29:45.075674481 +0000
@@ -4,8 +4,8 @@
 
 dependency:micronaut-jooq[groupId="io.micronaut.sql"]
 
-You should then <<jdbc, configure one or many DataSources>>.
-For each registered `DataSource`, Micronaut will configure the following jOOQ beans using api:configuration.jooq.JooqConfigurationFactory[]:
+You should then either <<jdbc, configure one or many DataSources>> or <<jooq-r2dbc, configure one or many R2DBC ConnectionFactory instances>>.
+For each registered `DataSource` or `ConnectionFactory`, Micronaut will configure the following jOOQ beans using api:configuration.jooq.JooqConfigurationFactory[] or api:configuration.jooq.R2dbcJooqConfigurationFactory[]:
 
 * link:{jooqapi}/org/jooq/Configuration.html[Configuration] - jOOQ `Configuration`
 * link:{jooqapi}/org/jooq/DSLContext.html[DSLContext] - jOOQ `DSLContext`
@@ -14,4 +14,3 @@
 
 * api:configuration.jooq.JooqExceptionTranslatorProvider[] for each `DataSource`
 * api:configuration.jooq.SpringTransactionProvider[] for each Spring `PlatformTransactionManager`
-
```

### `src/main/docs/guide/toc.yml`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/src/main/docs/guide/toc.yml	2026-04-22 07:32:32.168815111 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/src/main/docs/guide/toc.yml	2026-04-22 07:29:45.076319820 +0000
@@ -7,6 +7,7 @@
   jdbc-connection-pools: Configuring JDBC Connection Pools
   jdbc-multiple-datasources: Configuring Multiple Data Sources
   jdbc-healthchecks: JDBC Health Checks
+  jdbc-runtime-password-update: Data Source Runtime Password Change
 hibernate:
   title: Configuring Hibernate
   hibernate-disable: Disable Micronaut Hibernate JPA
@@ -22,6 +23,7 @@
   jasync-healthchecks: Database Health Checks
 jooq:
   title: Configuring jOOQ
+  jooq-r2dbc: Configuring R2DBC connection factories
   jooq-dialect: Configuring SQL dialect
   jooq-provider-beans: Configuring additional provider beans
   jooq-jsonb: Using JsonMapper to convert JSON(B) types
```

### `src/main/docs/guide/vertxpgclient.adoc`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/src/main/docs/guide/vertxpgclient.adoc	2026-04-22 07:32:32.169077655 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/src/main/docs/guide/vertxpgclient.adoc	2026-04-22 07:29:45.076624198 +0000
@@ -30,13 +30,27 @@
 
 TIP: You can also connect to PostgreSQL using `uri` instead of the other properties.
 
-Once you have the above configuration in place then you can inject the `io.vertx.reactivex.pgclient.PgPool` bean. The following is the simplest way to connect:
+When you need to trust a PostgreSQL or CockroachDB CA certificate for SSL connections, configure PEM trust certificates with `pem-trust-options`:
+
+[configuration]
+----
+vertx:
+  pg:
+    client:
+      ssl: true
+      ssl-mode: VERIFY_CA
+      pem-trust-options:
+        cert-paths:
+          - certs/ca.crt
+----
+
+Once you have the above configuration in place then you can inject the core `io.vertx.sqlclient.Pool` bean. If `io.vertx:vertx-rx-java3` is on the classpath, Micronaut also exposes the RxJava3 `io.vertx.rxjava3.sqlclient.Pool` wrapper bean. The following is the simplest way to connect:
 
 [source,groovy]
 ----
 include::vertx-pg-client/src/test/groovy/io/micronaut/configuration/vertx/pg/client/PgClientSpec.groovy[tags=query,indent=0]
 ----
 
-<1> `client` is an instance of the `io.vertx.reactivex.pgclient.PgPool` bean.
+<1> `client` is an instance of the `io.vertx.sqlclient.Pool` bean.
 
 For more information on running queries on Postgres using the reactive client please read the "Running queries" section in the documentation of https://vertx.io/docs/vertx-pg-client/java/[vertx-pg-client].
```

### `tests/jdbc-dbcp-tests/jdbc-dbcp-postgres/src/main/java/example/jdbc/dbcp/sync/Pet.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/tests/jdbc-dbcp-tests/jdbc-dbcp-postgres/src/main/java/example/jdbc/dbcp/sync/Pet.java	2026-04-22 07:32:32.182244064 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/tests/jdbc-dbcp-tests/jdbc-dbcp-postgres/src/main/java/example/jdbc/dbcp/sync/Pet.java	2026-04-22 07:29:45.091412872 +0000
@@ -3,7 +3,7 @@
 import example.domain.IOwner;
 import example.domain.IPet;
 import io.micronaut.core.annotation.Creator;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.serde.annotation.Serdeable;
 
 @Serdeable
```

### `tests/jdbc-hikari-tests/jdbc-hikari-h2/src/main/java/example/jdbc/hikari/sync/Pet.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/tests/jdbc-hikari-tests/jdbc-hikari-h2/src/main/java/example/jdbc/hikari/sync/Pet.java	2026-04-22 07:32:32.183707536 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/tests/jdbc-hikari-tests/jdbc-hikari-h2/src/main/java/example/jdbc/hikari/sync/Pet.java	2026-04-22 07:29:45.092946552 +0000
@@ -3,7 +3,7 @@
 import example.domain.IOwner;
 import example.domain.IPet;
 import io.micronaut.core.annotation.Creator;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.serde.annotation.Serdeable;
 
 @Serdeable
```

### `tests/jdbc-hikari-tests/jdbc-hikari-h2/src/test/java/example/jdbc/hikari/sync/H2App.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/tests/jdbc-hikari-tests/jdbc-hikari-h2/src/test/java/example/jdbc/hikari/sync/H2App.java	2026-04-22 07:32:32.184218707 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/tests/jdbc-hikari-tests/jdbc-hikari-h2/src/test/java/example/jdbc/hikari/sync/H2App.java	2026-04-22 07:29:45.093495807 +0000
@@ -29,6 +29,7 @@
 @MicronautTest
 @Property(name = "datasources.default.db-type", value = "h2")
 @Property(name = "datasources.default.pool-name", value = H2App.POOL_NAME)
+@Property(name = "custom-ds-factory", value = "false")
 public class H2App extends AbstractApp {
 
     static final String POOL_NAME = "H2Pool";
```

### `tests/jdbc-tomcat-tests/jdbc-tomcat-mysql/src/main/java/example/jdbc/tomcat/sync/Pet.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/tests/jdbc-tomcat-tests/jdbc-tomcat-mysql/src/main/java/example/jdbc/tomcat/sync/Pet.java	2026-04-22 07:32:32.185126007 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/tests/jdbc-tomcat-tests/jdbc-tomcat-mysql/src/main/java/example/jdbc/tomcat/sync/Pet.java	2026-04-22 07:29:45.095518825 +0000
@@ -3,7 +3,7 @@
 import example.domain.IOwner;
 import example.domain.IPet;
 import io.micronaut.core.annotation.Creator;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.serde.annotation.Serdeable;
 
 @Serdeable
```

### `tests/jdbc-ucp-tests/jdbc-ucp-oracle/src/main/java/example/jdbc/ucp/sync/Pet.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/tests/jdbc-ucp-tests/jdbc-ucp-oracle/src/main/java/example/jdbc/ucp/sync/Pet.java	2026-04-22 07:32:32.186336101 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/tests/jdbc-ucp-tests/jdbc-ucp-oracle/src/main/java/example/jdbc/ucp/sync/Pet.java	2026-04-22 07:29:45.096923380 +0000
@@ -3,7 +3,7 @@
 import example.domain.IOwner;
 import example.domain.IPet;
 import io.micronaut.core.annotation.Creator;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.serde.annotation.Serdeable;
 
 @Serdeable
```

### `tests/jooq-tests/jooq-jdbc-postgres/src/main/java/example/jooq/sync/Pet.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/tests/jooq-tests/jooq-jdbc-postgres/src/main/java/example/jooq/sync/Pet.java	2026-04-22 07:32:32.187876532 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/tests/jooq-tests/jooq-jdbc-postgres/src/main/java/example/jooq/sync/Pet.java	2026-04-22 07:29:45.098450268 +0000
@@ -3,7 +3,7 @@
 import example.domain.IOwner;
 import example.domain.IPet;
 import io.micronaut.core.annotation.Creator;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.serde.annotation.Serdeable;
 
 @Serdeable
```

### `tests/jooq-tests/jooq-r2dbc-postgres/src/main/java/example/jooq/reactive/Pet.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/tests/jooq-tests/jooq-r2dbc-postgres/src/main/java/example/jooq/reactive/Pet.java	2026-04-22 07:32:32.189289003 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/tests/jooq-tests/jooq-r2dbc-postgres/src/main/java/example/jooq/reactive/Pet.java	2026-04-22 07:29:45.099889906 +0000
@@ -2,7 +2,7 @@
 
 import example.domain.IOwner;
 import example.domain.IPet;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.serde.annotation.Serdeable;
 
 @Serdeable
```

### `tests/jooq-tests/jooq-r2dbc-postgres/src/main/java/example/jooq/reactive/PetRepository.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/tests/jooq-tests/jooq-r2dbc-postgres/src/main/java/example/jooq/reactive/PetRepository.java	2026-04-22 07:32:32.189358212 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/tests/jooq-tests/jooq-r2dbc-postgres/src/main/java/example/jooq/reactive/PetRepository.java	2026-04-22 07:29:45.099973740 +0000
@@ -55,7 +55,7 @@
     @Transactional(Transactional.TxType.MANDATORY)
     @Override
     public Mono<Void> save(IPet pet) {
-        return withDSLContextMono(dslContext -> ctx.insertInto(PET_TABLE)
+        return withDSLContextMono(dslContext -> dslContext.insertInto(PET_TABLE)
             .columns(PET_NAME, PET_TYPE, PET_OWNER)
             .values(pet.getName(), pet.getType() == null ? null : pet.getType().name(), pet.getOwner().getId())
             .returning(PET_ID)).map(q -> q.get(PET_ID))
```

### `vertx-mysql-client/build.gradle`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/vertx-mysql-client/build.gradle	2026-04-22 07:32:32.189912008 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/vertx-mysql-client/build.gradle	2026-04-22 07:29:45.101875049 +0000
@@ -5,9 +5,9 @@
 dependencies {
     api(mn.micronaut.inject)
     api(libs.managed.vertx.mysql.client)
-    api(libs.managed.vertx.rx.java2)
 
     implementation(libs.managed.vertx.codegen)
+    implementation(mnReactor.micronaut.reactor)
 
     compileOnly(mn.micronaut.management)
 
```

### `vertx-mysql-client/src/main/java/io/micronaut/configuration/vertx/mysql/client/MySQLClientConfiguration.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/vertx-mysql-client/src/main/java/io/micronaut/configuration/vertx/mysql/client/MySQLClientConfiguration.java	2026-04-22 07:32:32.190424096 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/vertx-mysql-client/src/main/java/io/micronaut/configuration/vertx/mysql/client/MySQLClientConfiguration.java	2026-04-22 07:29:45.102493305 +0000
@@ -17,6 +17,7 @@
 
 import io.micronaut.context.annotation.ConfigurationBuilder;
 import io.micronaut.context.annotation.ConfigurationProperties;
+import io.vertx.core.net.NetClientOptions;
 import io.vertx.mysqlclient.MySQLConnectOptions;
 import io.vertx.sqlclient.PoolOptions;
 
@@ -33,6 +34,9 @@
     @ConfigurationBuilder
     protected PoolOptions poolOptions = new PoolOptions();
 
+    @ConfigurationBuilder
+    protected NetClientOptions netClientOptions = new NetClientOptions();
+
     protected String uri;
 
     /**
@@ -57,4 +61,12 @@
     public PoolOptions getPoolOptions() {
         return poolOptions;
     }
+
+    /**
+     *
+     * @return The net client options for configuring client.
+     */
+    public NetClientOptions getNetClientOptions() {
+        return netClientOptions;
+    }
 }
```

### `vertx-mysql-client/src/main/java/io/micronaut/configuration/vertx/mysql/client/MySQLClientFactory.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/vertx-mysql-client/src/main/java/io/micronaut/configuration/vertx/mysql/client/MySQLClientFactory.java	2026-04-22 07:32:32.190511555 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/vertx-mysql-client/src/main/java/io/micronaut/configuration/vertx/mysql/client/MySQLClientFactory.java	2026-04-22 07:29:45.102611639 +0000
@@ -17,10 +17,14 @@
 
 import io.micronaut.context.annotation.Bean;
 import io.micronaut.context.annotation.Factory;
-import io.micronaut.core.annotation.Nullable;
+import io.micronaut.context.annotation.Requires;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.core.util.StringUtils;
-import io.vertx.reactivex.core.Vertx;
-import io.vertx.reactivex.mysqlclient.MySQLPool;
+import io.vertx.core.Vertx;
+import io.vertx.core.Future;
+import io.vertx.mysqlclient.MySQLConnectOptions;
+import io.vertx.mysqlclient.spi.MySQLDriver;
+import io.vertx.sqlclient.Pool;
 import jakarta.inject.Singleton;
 
 /**
@@ -51,13 +55,10 @@
      * @return client A pool of connections.
      */
     @Singleton
+    @Requires(missingBeans = Pool.class)
     @Bean(preDestroy = "close")
-    public MySQLPool client() {
-        if (this.vertx == null) {
-            return createClient();
-        } else {
-            return createClient(vertx);
-        }
+    public Pool client() {
+        return createClient();
     }
 
     /**
@@ -65,28 +66,16 @@
      * {@link MySQLClientConfiguration}.
      * @return A pool of connections.
      */
-    private MySQLPool createClient() {
+    private Pool createClient() {
         MySQLClientConfiguration configuration = this.connectionConfiguration;
         String connectionUri = configuration.getUri();
+        Vertx v = this.vertx != null ? this.vertx : Vertx.vertx();
         if (StringUtils.isNotEmpty(connectionUri)) {
-            return MySQLPool.pool(connectionUri, configuration.poolOptions);
+            MySQLConnectOptions options = MySQLDriver.INSTANCE.parseConnectionUri(connectionUri);
+            return MySQLDriver.INSTANCE.createPool(v, () -> Future.succeededFuture(options), configuration.poolOptions, configuration.netClientOptions, null);
         } else {
-            return MySQLPool.pool(configuration.connectOptions, configuration.poolOptions);
+            return MySQLDriver.INSTANCE.createPool(v, () -> Future.succeededFuture(configuration.connectOptions), configuration.poolOptions, configuration.netClientOptions, null);
         }
     }
 
-    /**
-     * Create a connection pool to the database configured with the {@link MySQLClientConfiguration }.
-     * @param vertx The Vertx instance.
-     * @return A pool of connections.
-     */
-    private MySQLPool createClient(Vertx vertx) {
-        MySQLClientConfiguration configuration = this.connectionConfiguration;
-        String connectionUri = configuration.getUri();
-        if (StringUtils.isNotEmpty(connectionUri)) {
-            return MySQLPool.pool(vertx, connectionUri, configuration.poolOptions);
-        } else {
-            return MySQLPool.pool(vertx, configuration.connectOptions, configuration.poolOptions);
-        }
-    }
 }
```

### `vertx-mysql-client/src/main/java/io/micronaut/configuration/vertx/mysql/client/MySQLDriverFactory.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/vertx-mysql-client/src/main/java/io/micronaut/configuration/vertx/mysql/client/MySQLDriverFactory.java	2026-04-22 07:32:32.190680390 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/vertx-mysql-client/src/main/java/io/micronaut/configuration/vertx/mysql/client/MySQLDriverFactory.java	2026-04-22 07:29:45.102784099 +0000
@@ -17,16 +17,15 @@
 
 import io.micronaut.context.annotation.Bean;
 import io.micronaut.context.annotation.Factory;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.core.util.StringUtils;
 import io.vertx.core.Vertx;
+import io.vertx.core.Future;
 import io.vertx.mysqlclient.MySQLConnectOptions;
 import io.vertx.mysqlclient.spi.MySQLDriver;
 import io.vertx.sqlclient.Pool;
 import jakarta.inject.Singleton;
 
-import java.util.Collections;
-
 /**
  * The Factory for creating Vertx MySQL client.
  *
@@ -62,8 +61,8 @@
         String connectionUri = connectionConfiguration.getUri();
         if (StringUtils.isNotEmpty(connectionUri)) {
             MySQLConnectOptions pgConnectOptions = MySQLDriver.INSTANCE.parseConnectionUri(connectionUri);
-            return MySQLDriver.INSTANCE.createPool(vertx, Collections.singletonList(pgConnectOptions), connectionConfiguration.poolOptions);
+            return MySQLDriver.INSTANCE.createPool(vertx, () -> Future.succeededFuture(pgConnectOptions), connectionConfiguration.poolOptions, connectionConfiguration.netClientOptions, null);
         }
-        return MySQLDriver.INSTANCE.createPool(vertx, Collections.singletonList(connectionConfiguration.connectOptions), connectionConfiguration.poolOptions);
+        return MySQLDriver.INSTANCE.createPool(vertx, () -> Future.succeededFuture(connectionConfiguration.connectOptions), connectionConfiguration.poolOptions, connectionConfiguration.netClientOptions, null);
     }
 }
```

### `vertx-mysql-client/src/main/java/io/micronaut/configuration/vertx/mysql/client/health/MySQLHealthIndicator.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/vertx-mysql-client/src/main/java/io/micronaut/configuration/vertx/mysql/client/health/MySQLHealthIndicator.java	2026-04-22 07:32:32.190996685 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/vertx-mysql-client/src/main/java/io/micronaut/configuration/vertx/mysql/client/health/MySQLHealthIndicator.java	2026-04-22 07:29:45.103127102 +0000
@@ -21,10 +21,12 @@
 import io.micronaut.management.endpoint.health.HealthEndpoint;
 import io.micronaut.management.health.indicator.HealthIndicator;
 import io.micronaut.management.health.indicator.HealthResult;
-import io.vertx.reactivex.mysqlclient.MySQLPool;
-import io.vertx.reactivex.sqlclient.Row;
+import io.vertx.sqlclient.Pool;
+import io.vertx.sqlclient.Row;
 import jakarta.inject.Singleton;
 import org.reactivestreams.Publisher;
+import reactor.core.publisher.Mono;
+
 
 import java.util.Collections;
 
@@ -37,25 +39,30 @@
 public class MySQLHealthIndicator implements HealthIndicator {
     public static final String NAME = "vertx-mysql-client";
     public static final String QUERY = "SELECT version();";
-    private final MySQLPool client;
+    private final Pool client;
 
     /**
      * Constructor.
      *
      * @param client A pool of connections.
      */
-    public MySQLHealthIndicator(MySQLPool client) {
+    public MySQLHealthIndicator(Pool client) {
         this.client = client;
     }
 
     @Override
     public Publisher<HealthResult> getResult() {
-        return client.query(QUERY).rxExecute().map(rows -> {
-            HealthResult.Builder status = HealthResult.builder(NAME, HealthStatus.UP);
-            Row row = rows.iterator().next();
-            status.details(Collections.singletonMap("version", row.getString(0)));
-            return status.build();
-        }).onErrorReturn(this::buildErrorResult).toFlowable();
+        return Mono.fromCompletionStage(
+            client.query(QUERY).execute()
+                .toCompletionStage()
+                .thenApply(rows -> {
+                    HealthResult.Builder status = HealthResult.builder(NAME, HealthStatus.UP);
+                    Row row = rows.iterator().next();
+                    status.details(Collections.singletonMap("version", row.getString(0)));
+                    return status.build();
+                })
+                .exceptionally(this::buildErrorResult)
+        );
     }
 
     private HealthResult buildErrorResult(Throwable throwable) {
```

### `vertx-mysql-client/src/test/groovy/io/micronaut/configuration/vertx/mysql/client/MySQLClientSpec.groovy`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/vertx-mysql-client/src/test/groovy/io/micronaut/configuration/vertx/mysql/client/MySQLClientSpec.groovy	2026-04-22 07:32:32.191713024 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/vertx-mysql-client/src/test/groovy/io/micronaut/configuration/vertx/mysql/client/MySQLClientSpec.groovy	2026-04-22 07:29:45.103900609 +0000
@@ -19,10 +19,10 @@
 import io.micronaut.context.ApplicationContext
 //end::appcontext-import[]
 
-import io.vertx.reactivex.mysqlclient.MySQLPool
-import io.vertx.reactivex.sqlclient.Row
-import io.vertx.reactivex.sqlclient.RowIterator
-import io.vertx.reactivex.sqlclient.RowSet
+import io.vertx.sqlclient.Pool
+import io.vertx.sqlclient.Row
+import io.vertx.sqlclient.RowIterator
+import io.vertx.sqlclient.RowSet
 
 //tag::mysql-testcontainer-import[]
 import org.testcontainers.containers.MySQLContainer
@@ -58,19 +58,18 @@
         when:
 
         // tag::mysqlPool-bean[]
-        MySQLPool client = applicationContext.getBean(MySQLPool)
+        Pool client = applicationContext.getBean(Pool)
         // end::mysqlPool-bean[]
 
         //
-        client.query("CREATE TABLE IF NOT EXISTS foo(id INTEGER)").rxExecute().blockingGet()
-        client.query("INSERT INTO foo(id) VALUES (0);").rxExecute().blockingGet()
+        client.query("CREATE TABLE IF NOT EXISTS foo(id INTEGER)").execute().toCompletionStage().toCompletableFuture().get()
+        client.query("INSERT INTO foo(id) VALUES (0);").execute().toCompletionStage().toCompletableFuture().get()
 
         // tag::query[]
-        result = client.query('SELECT * FROM foo').rxExecute().map({ RowSet<Row> rowSet -> // <1>
-            RowIterator<Row> iterator = rowSet.iterator()
-            int id = iterator.next().getInteger("id")
-            return "id: ${id}"
-        }).blockingGet()
+        RowSet<Row> rowSet = client.query('SELECT * FROM foo').execute().toCompletionStage().toCompletableFuture().get() // <1>
+        RowIterator<Row> iterator = rowSet.iterator()
+        int id = iterator.next().getInteger("id")
+        result = "id: ${id}"
         // end::query[]
 
         then:
```

### `vertx-mysql-client/src/test/groovy/io/micronaut/configuration/vertx/mysql/client/health/MySQLPoolHealthIndicatorSpec.groovy`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/vertx-mysql-client/src/test/groovy/io/micronaut/configuration/vertx/mysql/client/health/MySQLPoolHealthIndicatorSpec.groovy	2026-04-22 07:32:32.191937776 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/vertx-mysql-client/src/test/groovy/io/micronaut/configuration/vertx/mysql/client/health/MySQLPoolHealthIndicatorSpec.groovy	2026-04-22 07:29:45.104180195 +0000
@@ -18,8 +18,8 @@
 import io.micronaut.context.ApplicationContext
 import io.micronaut.health.HealthStatus
 import io.micronaut.management.health.indicator.HealthResult
-import io.reactivex.Flowable
 import org.testcontainers.containers.MySQLContainer
+import reactor.core.publisher.Mono
 import spock.lang.Specification
 
 class MySQLPoolHealthIndicatorSpec extends Specification{
@@ -38,7 +38,7 @@
 
         when:
         MySQLHealthIndicator indicator = applicationContext.getBean(MySQLHealthIndicator)
-        HealthResult result = Flowable.fromPublisher(indicator.getResult()).blockingFirst()
+        HealthResult result = Mono.from(indicator.getResult()).block()
 
         then:
         result.status == HealthStatus.UP
@@ -46,12 +46,11 @@
 
         when:
         mysql.stop()
-        result = Flowable.fromPublisher(indicator.getResult()).blockingFirst()
+        result = Mono.from(indicator.getResult()).block()
 
         then:
         result.status == HealthStatus.DOWN
 
-
         cleanup:
         applicationContext?.stop()
     }
```

### `vertx-pg-client/build.gradle`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/vertx-pg-client/build.gradle	2026-04-22 07:32:32.192201529 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/vertx-pg-client/build.gradle	2026-04-22 07:29:45.104494989 +0000
@@ -5,13 +5,16 @@
 dependencies {
     api(mn.micronaut.inject)
     api(libs.managed.vertx.pg.client)
-    api(libs.managed.vertx.rx.java2)
 
     implementation(libs.managed.vertx.codegen)
+    implementation(mnReactor.micronaut.reactor)
+
+    compileOnly(libs.managed.vertx.rx.java3)
 
     compileOnly(mn.micronaut.management)
     runtimeOnly libs.managed.ongres.scram.client
 
     testImplementation(mn.micronaut.management)
+    testImplementation(libs.managed.vertx.rx.java3)
     testImplementation(mnTestResources.testcontainers.postgres)
 }
```

### `vertx-pg-client/src/main/java/io/micronaut/configuration/vertx/pg/client/PgClientConfiguration.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/vertx-pg-client/src/main/java/io/micronaut/configuration/vertx/pg/client/PgClientConfiguration.java	2026-04-22 07:32:32.192694408 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/vertx-pg-client/src/main/java/io/micronaut/configuration/vertx/pg/client/PgClientConfiguration.java	2026-04-22 07:29:45.105076245 +0000
@@ -17,6 +17,7 @@
 
 import io.micronaut.context.annotation.ConfigurationBuilder;
 import io.micronaut.context.annotation.ConfigurationProperties;
+import io.vertx.core.net.NetClientOptions;
 import io.vertx.pgclient.PgConnectOptions;
 import io.vertx.sqlclient.PoolOptions;
 
@@ -33,6 +34,9 @@
     @ConfigurationBuilder
     protected PoolOptions poolOptions = new PoolOptions();
 
+    @ConfigurationBuilder
+    protected NetClientOptions netClientOptions = new NetClientOptions();
+
     protected String uri;
 
     /**
@@ -57,4 +61,12 @@
     public PoolOptions getPoolOptions() {
         return poolOptions;
     }
+
+    /**
+     * @return The net client options for configuring the client.
+     */
+    public NetClientOptions getNetClientOptions() {
+        return netClientOptions;
+    }
+
 }
```

### `vertx-pg-client/src/main/java/io/micronaut/configuration/vertx/pg/client/PgClientFactory.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/vertx-pg-client/src/main/java/io/micronaut/configuration/vertx/pg/client/PgClientFactory.java	2026-04-22 07:32:32.192767700 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/vertx-pg-client/src/main/java/io/micronaut/configuration/vertx/pg/client/PgClientFactory.java	2026-04-22 07:29:45.105173870 +0000
@@ -17,76 +17,64 @@
 
 import io.micronaut.context.annotation.Bean;
 import io.micronaut.context.annotation.Factory;
-import io.micronaut.core.annotation.Nullable;
-import io.micronaut.core.util.StringUtils;
-import io.vertx.reactivex.core.Vertx;
-import io.vertx.reactivex.pgclient.PgPool;
+import io.micronaut.context.annotation.Requires;
+import org.jspecify.annotations.Nullable;
+import io.vertx.core.Vertx;
+import io.vertx.pgclient.PgConnectOptions;
+import io.vertx.pgclient.spi.PgDriver;
+import io.vertx.sqlclient.Pool;
 import jakarta.inject.Singleton;
 
+import io.vertx.core.Future;
+
 /**
- * The Factory for creating Vertx Pg client.
- *
+ * The Factory for creating Vert.x Pg client.
  */
 @Factory
 public class PgClientFactory {
     private final PgClientConfiguration connectionConfiguration;
+    private final PgPemTrustOptionsConfiguration pemTrustOptionsConfiguration;
 
     /**
-     * The Vertx instance if you are running with Vert.x.
+     * The Vert.x instance if you are running with Vert.x.
      */
     private final Vertx vertx;
 
     /**
      * Create the factory with given Pg Client configuration.
      *
-     * @param connectionConfiguration The  Pg ClientOption configurations
-     * @param vertx  The vertx instance
+     * @param connectionConfiguration The Pg client configuration
+     * @param vertx                   The Vert.x instance
+     * @param pemTrustOptionsConfiguration The PEM trust options configuration
      */
-    public PgClientFactory(PgClientConfiguration connectionConfiguration, @Nullable Vertx vertx) {
+    public PgClientFactory(PgClientConfiguration connectionConfiguration,
+                           @Nullable Vertx vertx,
+                           @Nullable PgPemTrustOptionsConfiguration pemTrustOptionsConfiguration) {
         this.connectionConfiguration = connectionConfiguration;
         this.vertx = vertx;
+        this.pemTrustOptionsConfiguration = pemTrustOptionsConfiguration;
     }
 
     /**
      * @return client A pool of connections.
      */
     @Singleton
+    @Requires(missingBeans = Pool.class)
     @Bean(preDestroy = "close")
-    public PgPool client() {
-        if (this.vertx == null) {
-            return createClient();
-        } else {
-            return createClient(vertx);
-        }
+    public Pool client() {
+        return createClient();
     }
 
     /**
      * Create a connection pool to the database configured with the
      * {@link PgClientConfiguration}.
+     *
      * @return A pool of connections.
      */
-    private PgPool createClient() {
-        PgClientConfiguration configuration = this.connectionConfiguration;
-        String connectionUri = configuration.getUri();
-        if (StringUtils.isNotEmpty(connectionUri)) {
-            return PgPool.pool(connectionUri, configuration.poolOptions);
-        } else {
-            return PgPool.pool(configuration.connectOptions, configuration.poolOptions);
-        }
-    }
-
-    /**
-     * Create a connection pool to the database configured with the {@link PgClientConfiguration }.
-     * @param vertx The Vertx instance.
-     * @return A pool of connections.
-     */
-    private PgPool createClient(Vertx vertx) {
+    private Pool createClient() {
         PgClientConfiguration configuration = this.connectionConfiguration;
-        String connectionUri = configuration.getUri();
-        if (StringUtils.isNotEmpty(connectionUri)) {
-            return PgPool.pool(vertx, connectionUri, configuration.poolOptions);
-        } else {
-            return PgPool.pool(vertx, configuration.connectOptions, configuration.poolOptions);
-        }
+        Vertx v = this.vertx != null ? this.vertx : Vertx.vertx();
+        PgConnectOptions options = PgConnectOptionsResolver.resolve(configuration, pemTrustOptionsConfiguration);
+        return PgDriver.INSTANCE.createPool(v, () -> Future.succeededFuture(options), configuration.poolOptions, configuration.netClientOptions, null);
     }
 }
```

### `vertx-pg-client/src/main/java/io/micronaut/configuration/vertx/pg/client/PgDriverFactory.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/vertx-pg-client/src/main/java/io/micronaut/configuration/vertx/pg/client/PgDriverFactory.java	2026-04-22 07:32:32.192951494 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/vertx-pg-client/src/main/java/io/micronaut/configuration/vertx/pg/client/PgDriverFactory.java	2026-04-22 07:29:45.105543415 +0000
@@ -17,15 +17,14 @@
 
 import io.micronaut.context.annotation.Bean;
 import io.micronaut.context.annotation.Factory;
-import io.micronaut.core.annotation.Nullable;
-import io.micronaut.core.util.StringUtils;
+import org.jspecify.annotations.Nullable;
 import io.vertx.core.Vertx;
 import io.vertx.pgclient.PgConnectOptions;
 import io.vertx.pgclient.spi.PgDriver;
 import io.vertx.sqlclient.Pool;
 import jakarta.inject.Singleton;
 
-import java.util.Collections;
+import io.vertx.core.Future;
 
 /**
  * The Factory for creating Vertx Pg client.
@@ -36,6 +35,7 @@
 @Factory
 class PgDriverFactory {
     private final PgClientConfiguration connectionConfiguration;
+    private final PgPemTrustOptionsConfiguration pemTrustOptionsConfiguration;
 
     /**
      * The Vertx instance if you are running with Vert.x.
@@ -47,10 +47,14 @@
      *
      * @param connectionConfiguration The  Pg ClientOption configurations
      * @param vertx                   The vertx instance
+     * @param pemTrustOptionsConfiguration The PEM trust options configuration
      */
-    PgDriverFactory(PgClientConfiguration connectionConfiguration, @Nullable Vertx vertx) {
+    PgDriverFactory(PgClientConfiguration connectionConfiguration,
+                    @Nullable Vertx vertx,
+                    @Nullable PgPemTrustOptionsConfiguration pemTrustOptionsConfiguration) {
         this.connectionConfiguration = connectionConfiguration;
         this.vertx = vertx;
+        this.pemTrustOptionsConfiguration = pemTrustOptionsConfiguration;
     }
 
     /**
@@ -59,11 +63,7 @@
     @Singleton
     @Bean(preDestroy = "close")
     Pool build() {
-        String connectionUri = connectionConfiguration.getUri();
-        if (StringUtils.isNotEmpty(connectionUri)) {
-            PgConnectOptions pgConnectOptions = PgDriver.INSTANCE.parseConnectionUri(connectionUri);
-            return PgDriver.INSTANCE.createPool(vertx, Collections.singletonList(pgConnectOptions), connectionConfiguration.poolOptions);
-        }
-        return PgDriver.INSTANCE.createPool(vertx, Collections.singletonList(connectionConfiguration.connectOptions), connectionConfiguration.poolOptions);
+        PgConnectOptions pgConnectOptions = PgConnectOptionsResolver.resolve(connectionConfiguration, pemTrustOptionsConfiguration);
+        return PgDriver.INSTANCE.createPool(vertx, () -> Future.succeededFuture(pgConnectOptions), connectionConfiguration.poolOptions, connectionConfiguration.netClientOptions, null);
     }
 }
```

### `vertx-pg-client/src/main/java/io/micronaut/configuration/vertx/pg/client/health/PgHealthIndicator.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/vertx-pg-client/src/main/java/io/micronaut/configuration/vertx/pg/client/health/PgHealthIndicator.java	2026-04-22 07:32:32.193205954 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/vertx-pg-client/src/main/java/io/micronaut/configuration/vertx/pg/client/health/PgHealthIndicator.java	2026-04-22 07:29:45.105932294 +0000
@@ -21,16 +21,16 @@
 import io.micronaut.management.endpoint.health.HealthEndpoint;
 import io.micronaut.management.health.indicator.HealthIndicator;
 import io.micronaut.management.health.indicator.HealthResult;
-import io.vertx.reactivex.pgclient.PgPool;
-import io.vertx.reactivex.sqlclient.Row;
+import io.vertx.sqlclient.Pool;
+import io.vertx.sqlclient.Row;
 import jakarta.inject.Singleton;
 import org.reactivestreams.Publisher;
+import reactor.core.publisher.Mono;
 
 import java.util.Collections;
 
 /**
  * A  {@link HealthIndicator} for Vertx Pg client.
- *
  */
 @Requires(beans = HealthEndpoint.class)
 @Requires(property = HealthEndpoint.PREFIX + ".vertx.pg.client.enabled", notEquals = StringUtils.FALSE)
@@ -38,25 +38,30 @@
 public class PgHealthIndicator implements HealthIndicator {
     public static final String NAME = "vertx-pg-client";
     public static final String QUERY = "SELECT version();";
-    private final PgPool client;
+    private final Pool client;
 
     /**
      * Constructor.
      *
      * @param client A pool of connections.
      */
-    public PgHealthIndicator(PgPool client) {
+    public PgHealthIndicator(Pool client) {
         this.client = client;
     }
 
     @Override
     public Publisher<HealthResult> getResult() {
-        return client.query(QUERY).rxExecute().map(rows -> {
-            HealthResult.Builder status = HealthResult.builder(NAME, HealthStatus.UP);
-            Row row = rows.iterator().next();
-            status.details(Collections.singletonMap("version", row.getString(0)));
-            return status.build();
-        }).onErrorReturn(this::buildErrorResult).toFlowable();
+        return Mono.fromCompletionStage(
+            client.query(QUERY).execute()
+                .toCompletionStage()
+                .thenApply(rows -> {
+                    HealthResult.Builder status = HealthResult.builder(NAME, HealthStatus.UP);
+                    Row row = rows.iterator().next();
+                    status.details(Collections.singletonMap("version", row.getString(0)));
+                    return status.build();
+                })
+                .exceptionally(this::buildErrorResult)
+        );
     }
 
     private HealthResult buildErrorResult(Throwable throwable) {
```

### `vertx-pg-client/src/test/groovy/io/micronaut/configuration/vertx/pg/client/PgClientConfigurationSpec.groovy`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/vertx-pg-client/src/test/groovy/io/micronaut/configuration/vertx/pg/client/PgClientConfigurationSpec.groovy	2026-04-22 07:32:32.193910127 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/vertx-pg-client/src/test/groovy/io/micronaut/configuration/vertx/pg/client/PgClientConfigurationSpec.groovy	2026-04-22 07:29:45.106598258 +0000
@@ -17,6 +17,10 @@
 
 
 import io.micronaut.context.ApplicationContext
+import io.vertx.core.net.PemTrustOptions
+import io.vertx.pgclient.PgConnectOptions
+import io.vertx.pgclient.SslMode
+import io.vertx.sqlclient.Pool
 import spock.lang.Specification
 
 
@@ -48,6 +52,89 @@
         applicationContext?.stop()
     }
 
+    void "test rxjava3 sql client pool bean is exposed when rxjava3 is on the classpath"() {
+        given:
+        ApplicationContext applicationContext = ApplicationContext.run(
+                'vertx.pg.client.port': '5432',
+                'vertx.pg.client.host': 'the-host',
+                'vertx.pg.client.database': 'the-db',
+                'vertx.pg.client.user': 'user',
+                'vertx.pg.client.password': 'secret',
+                'vertx.pg.client.maxSize': '5'
+        )
+
+        when:
+        Pool pool = applicationContext.getBean(Pool)
+
+        then:
+        applicationContext.containsBean(io.vertx.rxjava3.sqlclient.Pool)
+        applicationContext.getBean(io.vertx.rxjava3.sqlclient.Pool).delegate.is(pool)
+
+        cleanup:
+        applicationContext?.stop()
+    }
+
+    void "test vertx-pg-client connects with direct options when verify-ca trust options are configured"() {
+        given:
+        int port = findFreePort()
+
+        when:
+        ApplicationContext applicationContext = ApplicationContext.run(
+                'vertx.pg.client.host': 'localhost',
+                'vertx.pg.client.port': port,
+                'vertx.pg.client.ssl': true,
+                'vertx.pg.client.ssl-mode': 'VERIFY_CA',
+                'vertx.pg.client.pem-trust-options.cert-paths[0]': 'certs/ca.crt'
+        )
+        PgConnectOptions options = PgConnectOptionsResolver.resolve(
+                applicationContext.getBean(PgClientConfiguration),
+                applicationContext.getBean(PgPemTrustOptionsConfiguration)
+        )
+        PemTrustOptions trustOptions = (PemTrustOptions) options.sslOptions.trustOptions
+
+        then:
+        options.host == 'localhost'
+        options.port == port
+        options.sslMode == SslMode.VERIFY_CA
+        options.sslOptions != null
+        trustOptions.certPaths == ['certs/ca.crt']
+
+        cleanup:
+        applicationContext?.stop()
+    }
+
+    void "test vertx-pg-client uri mode keeps verify-ca trust options during connect"() {
+        given:
+        int port = findFreePort()
+
+        when:
+        ApplicationContext applicationContext = ApplicationContext.run(
+                'vertx.pg.client.uri': "postgresql://user:secret@localhost:${port}/the-db",
+                'vertx.pg.client.ssl': true,
+                'vertx.pg.client.ssl-mode': 'VERIFY_CA',
+                'vertx.pg.client.pem-trust-options.cert-paths[0]': 'certs/ca.crt'
+        )
+        PgConnectOptions options = PgConnectOptionsResolver.resolve(
+                applicationContext.getBean(PgClientConfiguration),
+                applicationContext.getBean(PgPemTrustOptionsConfiguration)
+        )
+        PemTrustOptions trustOptions = (PemTrustOptions) options.sslOptions.trustOptions
+
+        then:
+        options.host == 'localhost'
+        options.port == port
+        options.database == 'the-db'
+        options.user == 'user'
+        options.password == 'secret'
+        options.sslMode == SslMode.VERIFY_CA
+        options.sslOptions != null
+        trustOptions.certPaths == ['certs/ca.crt']
 
+        cleanup:
+        applicationContext?.stop()
+    }
 
+    private static int findFreePort() {
+        new ServerSocket(0).withCloseable { it.localPort }
+    }
 }
```

### `vertx-pg-client/src/test/groovy/io/micronaut/configuration/vertx/pg/client/PgClientSpec.groovy`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/vertx-pg-client/src/test/groovy/io/micronaut/configuration/vertx/pg/client/PgClientSpec.groovy	2026-04-22 07:32:32.194011878 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/vertx-pg-client/src/test/groovy/io/micronaut/configuration/vertx/pg/client/PgClientSpec.groovy	2026-04-22 07:29:45.106682884 +0000
@@ -37,10 +37,10 @@
 
 //end::appcontext-import[]
 
-import io.vertx.reactivex.pgclient.PgPool
-import io.vertx.reactivex.sqlclient.Row
-import io.vertx.reactivex.sqlclient.RowIterator
-import io.vertx.reactivex.sqlclient.RowSet
+import io.vertx.sqlclient.Pool
+import io.vertx.sqlclient.Row
+import io.vertx.sqlclient.RowIterator
+import io.vertx.sqlclient.RowSet
 import org.testcontainers.containers.PostgreSQLContainer
 
 //tag::pg-testcontainer-import[]
@@ -81,19 +81,18 @@
         when:
 
         // tag::pgPool-bean[]
-        PgPool client = applicationContext.getBean(PgPool)
+        Pool client = applicationContext.getBean(Pool)
         // end::pgPool-bean[]
 
         // tag::query[]
-        result = client.query('SELECT * FROM pg_stat_database').rxExecute().map({ RowSet<Row> rowSet -> // <1>
-            int size = 0
-            RowIterator<Row> iterator = rowSet.iterator()
-            while (iterator.hasNext()) {
-                iterator.next()
-                size++
-            }
-            return "Size: ${size}"
-        }).blockingGet()
+        RowSet<Row> rowSet = client.query('SELECT * FROM pg_stat_database').execute().toCompletionStage().toCompletableFuture().get() // <1>
+        int size = 0
+        RowIterator<Row> iterator = rowSet.iterator()
+        while (iterator.hasNext()) {
+            iterator.next()
+            size++
+        }
+        result = "Size: ${size}"
         // end::query[]
 
         then:
```

### `vertx-pg-client/src/test/groovy/io/micronaut/configuration/vertx/pg/client/health/PgClientHealthIndicatorSpec.groovy`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-sql/vertx-pg-client/src/test/groovy/io/micronaut/configuration/vertx/pg/client/health/PgClientHealthIndicatorSpec.groovy	2026-04-22 07:32:32.194176838 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-sql/vertx-pg-client/src/test/groovy/io/micronaut/configuration/vertx/pg/client/health/PgClientHealthIndicatorSpec.groovy	2026-04-22 07:29:45.106808260 +0000
@@ -18,8 +18,9 @@
 import io.micronaut.context.ApplicationContext
 import io.micronaut.health.HealthStatus
 import io.micronaut.management.health.indicator.HealthResult
-import io.reactivex.Flowable
+
 import org.testcontainers.containers.PostgreSQLContainer
+import reactor.core.publisher.Mono
 import spock.lang.Specification
 
 
@@ -40,7 +41,7 @@
 
         when:
         PgHealthIndicator indicator = applicationContext.getBean(PgHealthIndicator)
-        HealthResult result = Flowable.fromPublisher(indicator.getResult()).blockingFirst()
+        HealthResult result = Mono.from(indicator.getResult()).block()
 
         then:
         result.status == HealthStatus.UP
@@ -48,12 +49,11 @@
 
         when:
         postgres.stop()
-        result = Flowable.fromPublisher(indicator.getResult()).blockingFirst()
+        result = Mono.from(indicator.getResult()).block()
 
         then:
         result.status == HealthStatus.DOWN
 
-
         cleanup:
         applicationContext?.stop()
     }
```

---

_Report generated by git-branch-diff skill._
