# Release Note Comparison

Generated: 2026-05-06 14:53 UTC
Comparison: `mn4` -> `mn5`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-serialization` | `2.16.x` | `c39983fddc04` | `git@github.com:micronaut-projects/micronaut-serialization.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-serialization` | `3.0.x` | `38ac6001b557` | `git@github.com:micronaut-projects/micronaut-serialization.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-serialization`
- Commit candidates found: 143
- File changes listed: 524
- Version values listed: 66
- File status counts: A=147, D=6, M=371

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `2.16.3-SNAPSHOT` | `3.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.aws-lambda-events` | `com.amazonaws:aws-lambda-java-events:3.16.1` | `com.amazonaws:aws-lambda-java-events:3.16.1` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.aws-lambda-serialization` | `com.amazonaws:aws-lambda-java-serialization:1.1.6` | `com.amazonaws:aws-lambda-java-serialization:1.3.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.error-prone-core` | `not present` | `com.google.errorprone:error_prone_core:2.49.0` | `added` |
| `gradle/libs.versions.toml` | `libraries.graal-svm` | `org.graalvm.sdk:nativeimage:23.1.8` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.gradle-errorprone` | `not present` | `net.ltgt.errorprone:net.ltgt.errorprone.gradle.plugin:5.1.0` | `added` |
| `gradle/libs.versions.toml` | `libraries.gradle-micronaut` | `io.micronaut.gradle:micronaut-gradle-plugin:4.5.4` | `io.micronaut.gradle:micronaut-gradle-plugin:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.jetbrains-annotations` | `org.jetbrains:annotations:24.1.0` | `org.jetbrains:annotations:26.1.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.jmh-core` | `org.openjdk.jmh:jmh-core:1.37` | `org.openjdk.jmh:jmh-core:1.37` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.jmh-generator-annprocess` | `org.openjdk.jmh:jmh-generator-annprocess:1.37` | `org.openjdk.jmh:jmh-generator-annprocess:1.37` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.kotlin-gradle-allopen` | `org.jetbrains.kotlin:kotlin-allopen:1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.kotlin-gradle-ksp` | `com.google.devtools.ksp:com.google.devtools.ksp.gradle.plugin:1.9.25-1.0.20` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.kotlin-gradle-plugin` | `org.jetbrains.kotlin:kotlin-gradle-plugin:1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.lombok` | `org.projectlombok:lombok:1.18.38` | `org.projectlombok:lombok:1.18.46` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-bson` | `org.mongodb:bson:4.11.5` | `org.mongodb:bson:5.7.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-eclipse-parsson` | `org.eclipse.parsson:parsson:1.1.7` | `org.eclipse.parsson:parsson:1.1.7` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-jakarta-json-api` | `jakarta.json:jakarta.json-api:2.1.3` | `jakarta.json:jakarta.json-api:2.1.3` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-jakarta-json-bindApi` | `jakarta.json.bind:jakarta.json.bind-api:3.0.1` | `jakarta.json.bind:jakarta.json.bind-api:3.0.1` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.micronaut-core` | `io.micronaut:micronaut-core-bom:4.9.11` | `io.micronaut:micronaut-core-bom:5.0.0-RC2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-discovery` | `io.micronaut.discovery:micronaut-discovery-client:4.7.1` | `io.micronaut.discovery:micronaut-discovery-client:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-logging` | `io.micronaut.logging:micronaut-logging-bom:1.7.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-platform` | `io.micronaut.platform:micronaut-platform:4.9.3` | `io.micronaut.platform:micronaut-platform:5.0.0-M3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-reactor` | `io.micronaut.reactor:micronaut-reactor-bom:3.8.0` | `io.micronaut.reactor:micronaut-reactor-bom:4.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-sourcegen-generator` | `not present` | `io.micronaut.sourcegen:micronaut-sourcegen-generator:2.0.0-RC1` | `added` |
| `gradle/libs.versions.toml` | `libraries.micronaut-sourcegen-generator-java` | `not present` | `io.micronaut.sourcegen:micronaut-sourcegen-generator-java:2.0.0-RC1` | `added` |
| `gradle/libs.versions.toml` | `libraries.micronaut-sourcegen-model` | `not present` | `io.micronaut.sourcegen:micronaut-sourcegen-model:2.0.0-RC1` | `added` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test` | `io.micronaut.test:micronaut-test-bom:4.7.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-validation` | `io.micronaut.validation:micronaut-validation-bom:4.10.0` | `io.micronaut.validation:micronaut-validation-bom:5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.microstream-storage-restclient` | `one.microstream:microstream-storage-restclient:08.01.02-MS-GA` | `one.microstream:microstream-storage-restclient:08.01.02-MS-GA` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.nullaway` | `not present` | `com.uber.nullaway:nullaway:0.13.4` | `added` |
| `gradle/libs.versions.toml` | `libraries.oracle-jdbc-driver` | `com.oracle.database.jdbc:ojdbc8:23.7.0.25.01` | `com.oracle.database.jdbc:ojdbc8:23.26.1.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.sonatype-scan` | `org.sonatype.gradle.plugins:scan-gradle-plugin:3.1.3` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.aws-lambda-events` | `3.16.1` | `3.16.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.aws-lambda-serialization` | `1.1.6` | `1.3.1` | `changed` |
| `gradle/libs.versions.toml` | `versions.error_prone_core` | `not present` | `2.49.0` | `added` |
| `gradle/libs.versions.toml` | `versions.errorprone-gradle-plugin` | `not present` | `5.1.0` | `added` |
| `gradle/libs.versions.toml` | `versions.graal-svm` | `23.1.8` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.22` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.jetbrains-annotations` | `24.1.0` | `26.1.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.jmh` | `1.37` | `1.37` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.jsonassert` | `not present` | `1.5.3` | `added` |
| `gradle/libs.versions.toml` | `versions.kotlin` | `1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.ksp` | `1.9.25-1.0.20` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.lombok` | `1.18.38` | `1.18.46` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-bson` | `4.11.5` | `5.7.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-eclipse-parsson` | `1.1.7` | `1.1.7` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-jakarta-json-api` | `2.1.3` | `2.1.3` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-jakarta-json-bindApi` | `3.0.1` | `3.0.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.9.11` | `5.0.0-RC2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-discovery` | `4.7.1` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.5.4` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-oracle-cloud` | `5.2.1` | `6.0.0-M2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-platform` | `4.9.3` | `5.0.0-M3` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-reactor` | `3.8.0` | `4.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-sourcegen` | `not present` | `2.0.0-RC1` | `added` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.7.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.10.0` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.microstream-storage-restclient` | `08.01.02-MS-GA` | `08.01.02-MS-GA` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.nullaway` | `not present` | `0.13.4` | `added` |
| `gradle/libs.versions.toml` | `versions.oracle-jdbc-driver` | `23.7.0.25.01` | `23.26.1.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.sonatype-scan` | `3.1.3` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.0` | `changed` |
| `settings.gradle.kts` | `plugin.io.micronaut.build.shared.settings` | `7.6.4` | `8.0.0-M18` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `d4916f165991` removed the two duplicate TCK package-info files (Sergio del Amo, 2026-05-04)
- `6cc2164d859f` remove method no longer overriding parent (Sergio del Amo, 2025-10-14)
- `71529c59eb26` remove sonatype scan (Sergio del Amo, 2025-10-14)

### Fixes

- `7cc871f6af0b` fix(deps): update dependency com.amazonaws:aws-lambda-java-serialization to v1.3.1 (#1263) (renovate[bot], 2026-04-02)
- `0768979a3a68` fix(deps): update dependency org.projectlombok:lombok to v1.18.44 (#1260) (renovate[bot], 2026-03-25)
- `4819a09abda4` fix(deps): update dependency io.micronaut.platform:micronaut-platform to v4.10.10 (#1257) (renovate[bot], 2026-03-25)
- `31fc5aeb1037` fix(deps): update dependency io.micronaut.platform:micronaut-platform to v4.10.9 (#1251) (renovate[bot], 2026-02-27)
- `3d26c456dbe4` fix(deps): update dependency io.micronaut.platform:micronaut-platform to v4.10.8 (#1249) (renovate[bot], 2026-02-16)
- `56f44ad33026` fix(deps): update dependency io.micronaut.oraclecloud:micronaut-oraclecloud-bom to v5.6.2 (#1248) (renovate[bot], 2026-02-15)
- `e0e3ac68ac67` fix(deps): update dependency io.micronaut.logging:micronaut-logging-bom to v1.7.3 (#1247) (renovate[bot], 2026-02-14)
- `716484a14cec` fix(deps): update dependency io.micronaut.logging:micronaut-logging-bom to v1.7.2 (#1246) (renovate[bot], 2026-02-10)
- `e2794429a34a` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.2 (#1245) (renovate[bot], 2026-02-09)
- `b82b43a91413` fix(deps): update dependency io.micronaut.discovery:micronaut-discovery-client to v4.7.2 (#1244) (renovate[bot], 2026-02-08)
- `2b4f13c96f18` fix(deps): update dependency com.oracle.database.jdbc:ojdbc8 to v23.26.1.0.0 (#1242) (renovate[bot], 2026-02-06)
- `52859dbc04a2` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m9 (#1240) (renovate[bot], 2026-01-24)
- `fa4ffbcbd18b` fix(deps): update dependency org.graalvm.sdk:nativeimage to v23.1.10 (#1239) (renovate[bot], 2026-01-21)
- `eb66a42327ec` fix(deps): update dependency com.oracle.database.jdbc:ojdbc8 to v23.26.0.0.0 (#1153) (renovate[bot], 2026-01-13)
- `261188e6dee0` fix(deps): update dependency com.amazonaws:aws-lambda-java-serialization to v1.2.0 (#1232) (renovate[bot], 2026-01-13)
- `7cdd96f51980` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m8 (#1235) (renovate[bot], 2026-01-13)
- `9abf2ad2a1fd` fix(deps): update dependency io.micronaut.platform:micronaut-platform to v4.10.7 (#1234) (renovate[bot], 2026-01-12)
- `3f7b263b1225` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m7 (#1233) (renovate[bot], 2026-01-10)
- `b807ccf8cafe` fix(deps): update dependency org.spockframework:spock-core to v2.4-groovy-5.0 (#1228) (renovate[bot], 2025-12-25)
- `24366c97e6c7` fix(deps): update dependency io.micronaut.platform:micronaut-platform to v4.10.6 (#1227) (renovate[bot], 2025-12-24)
- `cbd181cf5c03` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m6 (#1226) (renovate[bot], 2025-12-23)
- `2846b7332d32` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m5 (#1225) (renovate[bot], 2025-12-20)
- `67a18ee9a68d` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m3 (#1222) (renovate[bot], 2025-12-14)
- `16fb91a9f3a2` fix(deps): update dependency io.micronaut.platform:micronaut-platform to v4.10.4 (#1223) (renovate[bot], 2025-12-14)
- `aa892a47da78` fix(deps): update dependency org.projectlombok:lombok to v1.18.42 (#1182) (renovate[bot], 2025-12-04)
- `b8087803df3d` fix(deps): update dependency io.micronaut.oraclecloud:micronaut-oraclecloud-bom to v5.6.1 (#1210) (renovate[bot], 2025-12-04)
- `e7e17e6f8449` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#1192) (renovate[bot], 2025-11-28)
- `b785df313b5a` fix(deps): update dependency io.micronaut.oraclecloud:micronaut-oraclecloud-bom to v5.5.2 (#1193) (renovate[bot], 2025-11-28)
- `f40f52ea1643` fix(deps): update dependency io.micronaut.reactor:micronaut-reactor-bom to v3.9.1 (#1194) (renovate[bot], 2025-11-28)
- `805f902143f2` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.1 (#1201) (renovate[bot], 2025-11-28)
- `5298bcbcb158` fix(deps): update dependency io.micronaut.platform:micronaut-platform to v4.10.2 (#1202) (renovate[bot], 2025-11-28)
- `213ed75a2659` fix(deps): update dependency io.micronaut.test:micronaut-test-bom to v4.10.2 (#1203) (renovate[bot], 2025-11-28)
- `c7fd0977dba3` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.12.0 (#1204) (renovate[bot], 2025-11-28)
- `9afab5ade336` fix(deps): update dependency io.micronaut.oraclecloud:micronaut-oraclecloud-bom to v5.5.1 (#1160) (renovate[bot], 2025-10-16)
- `67b2ceebb52f` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.5.5 (#1179) (renovate[bot], 2025-10-16)
- `9e3698a3bd83` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.3.6 (#816) (renovate[bot], 2024-04-09)
- `edeb1d52a28f` fix(deps): update dependency org.mongodb:bson to v5 (#784) (renovate[bot], 2024-04-09)

### Dependency Updates

- `265aa8f99b8c` Update Micronaut dependencies (#1310) (renovate[bot], 2026-05-05)
- `9ab4ae306bf5` Update Micronaut dependencies (#1300) (renovate[bot], 2026-05-04)
- `b9f5030ff249` Update dependency com.google.errorprone:error_prone_core to v2.49.0 (#1301) (renovate[bot], 2026-05-04)
- `a8e19454e75d` Update dependency com.uber.nullaway:nullaway to v0.13.4 (#1302) (renovate[bot], 2026-05-04)
- `5c7b2bec4039` Update dependency net.ltgt.errorprone:net.ltgt.errorprone.gradle.plugin to v5 (#1305) (renovate[bot], 2026-05-04)
- `897efc3fcfd6` Update dependency org.jetbrains:annotations to v26 (#1306) (renovate[bot], 2026-05-04)
- `7a5d11982008` Update dependency org.mongodb:bson to v5.7.0 (#1303) (renovate[bot], 2026-05-04)
- `2762cfd7e1f6` Update dependency io.micronaut:micronaut-core-bom to v5.0.0-M26 (#1299) (renovate[bot], 2026-05-01)
- `07c170707c81` Update Micronaut dependencies (#1295) (renovate[bot], 2026-04-29)
- `51ac1c4e08f4` chore: Bump version to 3.0.0-SNAPSHOT (micronaut-build, 2026-04-28)
- `95a3566e1b1b` Update managed-bson version to 5.6.5 (#1293) (Sergio del Amo, 2026-04-28)
- `3c61859fce7c` use jackson databind from version catalogue (Sergio del Amo, 2026-04-28)
- `19dc257fd7f2` Update dependency org.projectlombok:lombok to v1.18.46 (#1291) (renovate[bot], 2026-04-28)
- `7f61309c5963` chore: Bump version to 3.0.0-SNAPSHOT (micronaut-build, 2026-04-17)
- `8f6b346511ff` Update dependency io.micronaut.platform:micronaut-platform to v4.10.11 (#1287) (renovate[bot], 2026-04-17)
- `b4867467e6bf` Update dependency io.micronaut:micronaut-core-bom to v5.0.0-M22 (#1243) (renovate[bot], 2026-04-13)
- `b57f347bbbf1` chore: Bump version to 3.0.0-SNAPSHOT (micronaut-build, 2026-04-02)
- `b9aff5532374` chore(deps): update plugin com.gradleup.shadow to v9.4.1 (#1273) (renovate[bot], 2026-03-28)
- `8780dac7d9e7` chore: Bump version to 3.0.0-SNAPSHOT (micronaut-build, 2026-03-27)
- `57e963471ed1` chore: Bump version to 3.0.0-SNAPSHOT (micronaut-build, 2026-03-25)
- `033ebeefa325` chore(deps): update plugin com.gradleup.shadow to v9.4.0 (#1265) (renovate[bot], 2026-03-25)
- `49b0d357a76e` chore(deps): update gradle/actions action to v6 (#1266) (renovate[bot], 2026-03-25)
- `2aa67e594cfb` chore: Bump version to 3.0.0-SNAPSHOT (micronaut-build, 2026-03-24)
- `ad2ff239ed60` chore: Bump version to 3.0.0-SNAPSHOT (micronaut-build, 2026-01-13)
- `85044c188d6a` chore(deps): update graalvm/setup-graalvm action to v1.4.5 (#1231) (renovate[bot], 2026-01-06)
- `50e6d78fae2b` chore: Bump version to 3.0.0-SNAPSHOT (micronaut-build, 2025-12-04)
- `7b9265fcbdd0` chore(deps): update graalvm/setup-graalvm action to v1.4.4 (#1213) (renovate[bot], 2025-12-04)
- `581dafc32d5d` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#1191) (renovate[bot], 2025-11-28)
- `249973eeba5f` chore(deps): update graalvm/setup-graalvm action to v1.4.3 (#1190) (renovate[bot], 2025-11-28)
- `453c12e60ba5` chore(deps): update softprops/action-gh-release action to v2.4.2 (#1197) (renovate[bot], 2025-11-28)
- `99e71822c784` chore(deps): update gradle to v9.2.1 (#1200) (renovate[bot], 2025-11-28)
- `8823fdbe04fa` chore(deps): update actions/checkout action to v6 (#1205) (renovate[bot], 2025-11-28)
- `3fd33a54b058` chore(deps): update github artifact actions (#1206) (renovate[bot], 2025-11-28)
- `d5de5c57af87` chore(deps): update gradle/actions action to v5 (#1207) (renovate[bot], 2025-11-28)

### Internal

- `5005a913bda3` ci: projectVersion=2.16.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-10-14)
- `b61c73b6a73c` test: :junit-platform-launcher (Sergio del Amo, 2025-10-14)
- `9c28d742bd7e` test: junit-platform-launcher (Sergio del Amo, 2025-10-14)
- `fb675bdad834` ci: projectVersion=3.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2024-04-09)

### Review Candidates

- `38ac6001b557` git: ignore .kotlin (Sergio del Amo, 2026-05-06)
- `62eff20d149d` micronaut = "5.0.0-RC2" (Sergio del Amo, 2026-05-06)
- `59f806fc5656` Update common files (#1311) (micronaut-build, 2026-05-06)
- `14204701b53a` Update common files (#1309) (micronaut-build, 2026-05-05)
- `df82fa058c13` [skip ci] Release v3.0.0-RC1 (micronaut-build, 2026-05-04)
- `6d95f1b6364d` git: ignore .oca (Sergio del Amo, 2026-05-04)
- `5e0677c7c64b` tck: ignore jackson Class Level JSON Format Propagation (Sergio del Amo, 2026-05-04)
- `be9b0bffbf59` Update Gradle to v9.5.0 (#1304) (renovate[bot], 2026-05-04)
- `58691c8fc11b` Update common files (#1297) (micronaut-build, 2026-05-04)
- `b59a26c88b6f` Improve and add more tests for compile-time serdes (#1307) (Denis Stepanov, 2026-05-04)
- `d116c217f3c4` Nullaway, Jspecify integration (#1298) (Denis Stepanov, 2026-05-01)
- `a9afe90daa2c` Implement JsonFormat, Serialization/Deserialization features, JsonEnumDefaultValue (#1294) (Denis Stepanov, 2026-04-30)
- `1c9d4841797a` Update common files (#1296) (micronaut-build, 2026-04-29)
- `bc26d690a951` [skip ci] Release v3.0.0-M8 (micronaut-build, 2026-04-28)
- `712cecd8c6fc` micronaut = "5.0.0-M25" (Sergio del Amo, 2026-04-28)
- `1940ebb61ad6` bson 5.6.5 (Sergio del Amo, 2026-04-28)
- `76354776ca3a` micronaut-gradle-plugin = "5.0.0-M1" (Sergio del Amo, 2026-04-28)
- `d48007fe59de` micronaut-validation = "5.0.0-M2" (Sergio del Amo, 2026-04-28)
- `96cbc87cb316` micronaut-reactor = "4.0.0-M2" (Sergio del Amo, 2026-04-28)
- `c13b1096e74e` micronaut = "5.0.0-M24" (Sergio del Amo, 2026-04-28)
- `a38307174f0e` micronaut-platform = "5.0.0-M2" (Sergio del Amo, 2026-04-28)
- `c0db06371ae1` Fix NullAway compatibility for generated lazy serde references (records serde) (#1292) (Milenko Supic, 2026-04-28)
- `08c331a1658d` Update common files (#1289) (micronaut-build, 2026-04-26)
- `53def8c5aa7c` Fix missing deserializer NPE on retry (#1280) (Graeme Rocher, 2026-04-24)
- `eea88cd14a20` [skip ci] Release v3.0.0-M7 (micronaut-build, 2026-04-17)
- `ad44a2f7e592` Update stefanzweifel/git-auto-commit-action action to v7 (#1220) (renovate[bot], 2026-04-17)
- `18565debe7c0` Update common files (#1271) (micronaut-build, 2026-04-17)
- `16c635cdc8ad` Show example of using micronaut-serialization's ObjectMapper + Jackson without micronaut itself. (#1250) (Jake 'Donkey" Torrance, 2026-04-08)
- `3f0c8c5b905a` Sourcegen fallback for jackson dataformat annotations (#1277) (Hamza Mousrij, 2026-04-08)
- `1810743ad8a2` [skip ci] Release v3.0.0-M6 (micronaut-build, 2026-04-02)
- `25f3509bae99` Fix NullAway compatibility for generated lazy serde references (#1275) (Graeme Rocher, 2026-04-02)
- `389c7136e77f` [skip ci] Release v3.0.0-M5 (micronaut-build, 2026-03-27)
- `b2797f2797fe` use context loader if available for default object mapper loading (#1272) (Graeme Rocher, 2026-03-27)
- `982b0274a7f8` [skip ci] Release v3.0.0-M4 (micronaut-build, 2026-03-25)
- `6aa73c0c6d9d` Update to micronaut M17 (#1258) (Issam Liqali, 2026-03-25)
- `8bfc0ca9dda9` Update common files (#1261) (micronaut-build, 2026-03-25)
- `25084057ac53` Skip duplicates / move annotation constants to api module (#1270) (Graeme Rocher, 2026-03-25)
- `1e37dc9a7749` [skip ci] Release v3.0.0-M3 (micronaut-build, 2026-03-24)
- `0a310e52a155` Implement source-generated serializers and deserializers for simple cases (#1259) (Graeme Rocher, 2026-03-23)
- `5678513f7ed2` Update common files (#1219) (micronaut-build, 2026-03-16)
- `da3035f3a884` Merge pull request #1252 from micronaut-projects/andriy/oracle-data-serialization (Andriy Dmytruk, 2026-03-03)
- `9f13531154e9` Revert changing the date encoding function (Andriy Dmytruk, 2026-03-02)
- `48b46ba94391` Make sure decode arbitrary works for raw type (Andriy Dmytruk, 2026-02-27)
- `b1fbdb33187c` Improve date serialization for Oracle JDBC encoder (Andriy Dmytruk, 2026-02-27)
- `483aef539e82` [skip ci] Release v3.0.0-M2 (micronaut-build, 2026-01-13)
- `7d7c0ff9084b` SerdeJsonSubtypesKotlinSpec fails (#1216) (Sergio del Amo, 2026-01-13)
- `2686ebd37507` Filter bean configurations based on the packages included (#1236) (Denis Stepanov, 2026-01-13)
- `214c8c570c9e` [skip ci] Release v3.0.0-M1 (micronaut-build, 2025-12-04)
- `58f64046066a` Update Serialization to Core M1 (#1208) (Sergio del Amo, 2025-12-04)
- `6fa2da52847a` Micronaut 5 compatibility and release prep (#1189) (issam liqali, 2025-11-28)
- `c750c25e33b6` Update common files (#1188) (micronaut-build, 2025-11-28)
- `e746f8d941fa` Merge branch '2.16.x' into 3.0.x (Sergio del Amo, 2025-10-16)
- `22a133c4036f` Update common files (#1185) (micronaut-build, 2025-10-16)
- `49a22da4ef38` Micronaut Gradle Build Plugin 8.0.0-M4 (Sergio del Amo, 2025-10-15)
- `7de3123e1f7e` gradel 9.1 (Sergio del Amo, 2025-10-15)
- `db8db76d6867` Update common files (#1183) (micronaut-build, 2025-10-15)
- `f9bba42a07ac` Merge branch '2.16.x' into 3.0.x (Sergio del Amo, 2025-10-14)
- `d556bd4a8c37` platform 4.9.4 (Sergio del Amo, 2025-10-14)
- `8a3d59c44d76` validation 4.11.0 (Sergio del Amo, 2025-10-14)
- `6e070b9fed47` reactor 3.9.0 (Sergio del Amo, 2025-10-14)
- `4784927c4a5f` oraclecloud 5.5.0 (Sergio del Amo, 2025-10-14)
- `5391bb323d9c` micronaut logging 1.7.1 (Sergio del Amo, 2025-10-14)
- `8f5859689e24` micronaut test 4.9.0 (Sergio del Amo, 2025-10-14)
- `9a6856fc8734` micronaut core 4.10.4 (Sergio del Amo, 2025-10-14)
- `d16d51963ae0` breaks: delete and doc deprecated code for MN5 (#811) (Dean Wette, 2024-04-09)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` .github/workflows/update-gradle-wrapper.yml
- `M` benchmarks/build.gradle
- `M` build.gradle.kts
- `M` buildSrc/build.gradle
- `A` buildSrc/src/main/groovy/io.micronaut.build.internal.convention-nullaway.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.serde-examples.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.serde-module.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.serde-native-examples.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.serde-tck-suite.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` serde-jackson-tck/build.gradle.kts
- `M` serde-jackson-tck/src/main/java/io/micronaut/serde/jackson/jsonvalue/JdkVersion.java
- `M` serde-jackson/build.gradle.kts
- `M` serde-jsonp/build.gradle.kts
- `M` serde-oracle-jdbc-json/build.gradle.kts
- `M` serde-processor/build.gradle.kts
- `M` serde-support/build.gradle.kts
- `M` settings.gradle.kts
- `M` test-suite-http-server-tck-netty/build.gradle.kts

### Documentation

- `A` .agents/skills/docs/SKILL.md
- `A` .agents/skills/docs/references/control-panel-patterns.md
- `A` .agents/skills/docs/references/micronaut-docs-providers.md
- `M` .github/workflows/release.yml
- `A` benchmarks/README.md
- `A` doc-examples/example-bson-java/src/main/java/example/package-info.java
- `M` doc-examples/example-groovy/build.gradle
- `A` doc-examples/example-java/src/main/java/example/package-info.java
- `M` doc-examples/example-java/src/test/java/example/form/FormTest.java
- `A` doc-examples/example-jsonb-java/src/main/java/example/package-info.java
- `M` doc-examples/example-kotlin-ksp/build.gradle.kts
- `M` doc-examples/example-kotlin-ksp/src/test/kotlin/example/BookTest.kt
- `M` doc-examples/example-kotlin-ksp/src/test/kotlin/example/DefaultsTest.kt
- `M` doc-examples/example-kotlin-ksp/src/test/kotlin/example/LocationTest.kt
- `M` doc-examples/example-kotlin-ksp/src/test/kotlin/example/PlaceTest.kt
- `M` doc-examples/example-kotlin-ksp/src/test/kotlin/example/PointTest.kt
- `M` doc-examples/example-kotlin-ksp/src/test/kotlin/example/SerdeNullableFailOnMissingTest.kt
- `M` doc-examples/example-kotlin-ksp/src/test/kotlin/example/SerdeNullableTest.kt
- `M` doc-examples/example-kotlin/build.gradle.kts
- `M` doc-examples/example-kotlin/src/test/kotlin/example/BookTest.kt
- `M` doc-examples/example-kotlin/src/test/kotlin/example/LocationTest.kt
- `M` doc-examples/example-kotlin/src/test/kotlin/example/PlaceTest.kt
- `M` doc-examples/example-kotlin/src/test/kotlin/example/PointTest.kt
- `A` doc-examples/example-standalone-java-jackson/build.gradle.kts
- `A` doc-examples/example-standalone-java-jackson/src/main/java/example/Book.java
- `A` doc-examples/example-standalone-java-jackson/src/main/java/example/package-info.java
- `A` doc-examples/example-standalone-java-jackson/src/test/java/example/TestSerialization.java
- `A` src/main/docs/guide/breaks.adoc
- `M` src/main/docs/guide/jacksonAnnotations.adoc
- `M` src/main/docs/guide/toc.yml

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
- `A` benchmarks/src/jmh/java/io/micronaut/serde/SourceGenRoutingBenchmark.java
- `M` benchmarks/src/jmh/java/io/micronaut/serde/data/InputConstructor.java
- `M` benchmarks/src/jmh/java/io/micronaut/serde/data/InputSetter.java
- `M` benchmarks/src/jmh/java/io/micronaut/serde/data/IntArrayConstructor.java
- `M` benchmarks/src/jmh/java/io/micronaut/serde/data/IntConstructor.java
- `M` benchmarks/src/jmh/java/io/micronaut/serde/data/IntegerConstructor.java
- `M` benchmarks/src/jmh/java/io/micronaut/serde/data/Name.java
- `M` benchmarks/src/jmh/java/io/micronaut/serde/data/SimpleBean.java
- `M` benchmarks/src/jmh/java/io/micronaut/serde/data/StringArrayConstructor.java
- `M` benchmarks/src/jmh/java/io/micronaut/serde/data/StringConstructor.java
- `M` benchmarks/src/jmh/java/io/micronaut/serde/data/StringListConstructor.java
- `M` config/accepted-api-changes.json
- `M` config/checkstyle/checkstyle.xml
- `M` serde-api/src/main/java/io/micronaut/serde/Decoder.java
- `M` serde-api/src/main/java/io/micronaut/serde/DelegatingDecoder.java
- `M` serde-api/src/main/java/io/micronaut/serde/Deserializer.java
- `M` serde-api/src/main/java/io/micronaut/serde/DeserializerLocator.java
- `M` serde-api/src/main/java/io/micronaut/serde/Encoder.java
- `A` serde-api/src/main/java/io/micronaut/serde/FeatureDecoderContext.java
- `A` serde-api/src/main/java/io/micronaut/serde/FeatureEncoderContext.java
- `A` serde-api/src/main/java/io/micronaut/serde/FormatConfiguration.java
- `A` serde-api/src/main/java/io/micronaut/serde/FormattedDeserializer.java
- `A` serde-api/src/main/java/io/micronaut/serde/FormattedSerde.java
- `A` serde-api/src/main/java/io/micronaut/serde/FormattedSerializer.java
- `M` serde-api/src/main/java/io/micronaut/serde/LimitingStream.java
- `M` serde-api/src/main/java/io/micronaut/serde/NamingStrategyLocator.java
- `M` serde-api/src/main/java/io/micronaut/serde/ObjectMapper.java
- `M` serde-api/src/main/java/io/micronaut/serde/ObjectMappers.java
- `M` serde-api/src/main/java/io/micronaut/serde/ObjectSerializer.java
- `M` serde-api/src/main/java/io/micronaut/serde/PropertyFilter.java
- `M` serde-api/src/main/java/io/micronaut/serde/SerdeRegistry.java
- `M` serde-api/src/main/java/io/micronaut/serde/Serializer.java
- `M` serde-api/src/main/java/io/micronaut/serde/SerializerLocator.java
- `M` serde-api/src/main/java/io/micronaut/serde/UpdatingDeserializer.java
- `M` serde-api/src/main/java/io/micronaut/serde/annotation/Serdeable.java
- `A` serde-api/src/main/java/io/micronaut/serde/annotation/SerdeableGenerated.java
- `A` serde-api/src/main/java/io/micronaut/serde/annotation/package-info.java
- `M` serde-api/src/main/java/io/micronaut/serde/config/DefaultDeserializationConfiguration.java
- `M` serde-api/src/main/java/io/micronaut/serde/config/DefaultSerdeConfiguration.java
- `M` serde-api/src/main/java/io/micronaut/serde/config/DefaultSerializationConfiguration.java
- `M` serde-api/src/main/java/io/micronaut/serde/config/DeserializationConfiguration.java
- `M` serde-api/src/main/java/io/micronaut/serde/config/SerdeConfiguration.java
- `M` serde-api/src/main/java/io/micronaut/serde/config/SerializationConfiguration.java
- `M` serde-api/src/main/java/io/micronaut/serde/config/annotation/SerdeConfig.java
- `A` serde-api/src/main/java/io/micronaut/serde/config/annotation/package-info.java
- `M` serde-api/src/main/java/io/micronaut/serde/config/naming/KebabCaseStrategy.java
- `M` serde-api/src/main/java/io/micronaut/serde/config/naming/PropertyNamingStrategy.java
- `A` serde-api/src/main/java/io/micronaut/serde/config/naming/package-info.java
- `A` serde-api/src/main/java/io/micronaut/serde/config/package-info.java
- `M` serde-api/src/main/java/io/micronaut/serde/exceptions/InvalidFormatException.java
- `M` serde-api/src/main/java/io/micronaut/serde/exceptions/InvalidPropertyFormatException.java
- `M` serde-api/src/main/java/io/micronaut/serde/exceptions/RuntimeSerdeException.java
- `A` serde-api/src/main/java/io/micronaut/serde/exceptions/package-info.java
- `M` serde-api/src/main/java/io/micronaut/serde/exceptions/path/DefaultPropertyReferencePath.java
- `A` serde-api/src/main/java/io/micronaut/serde/exceptions/path/package-info.java
- `A` serde-api/src/main/java/io/micronaut/serde/package-info.java
- `M` serde-api/src/main/java/io/micronaut/serde/reference/AbstractPropertyReferenceManager.java
- `M` serde-api/src/main/java/io/micronaut/serde/reference/PropertyReference.java
- `M` serde-api/src/main/java/io/micronaut/serde/reference/PropertyReferenceManager.java
- `M` serde-api/src/main/java/io/micronaut/serde/reference/SerializationReference.java
- `A` serde-api/src/main/java/io/micronaut/serde/reference/package-info.java
- `M` serde-api/src/main/java/io/micronaut/serde/util/CustomizableDeserializer.java
- `M` serde-api/src/main/java/io/micronaut/serde/util/CustomizableSerializer.java
- `A` serde-api/src/main/java/io/micronaut/serde/util/GeneratedSerdeEnumUtil.java
- `A` serde-api/src/main/java/io/micronaut/serde/util/GeneratedSerdeExceptionUtil.java
- `A` serde-api/src/main/java/io/micronaut/serde/util/GeneratedSerdeFallbackUtil.java
- `M` serde-api/src/main/java/io/micronaut/serde/util/NullableDeserializer.java
- `A` serde-api/src/main/java/io/micronaut/serde/util/SerdeArgumentConstants.java
- `A` serde-api/src/main/java/io/micronaut/serde/util/package-info.java
- `M` serde-bson/src/main/java/io/micronaut/serde/bson/AbstractBsonMapper.java
- `M` serde-bson/src/main/java/io/micronaut/serde/bson/BsonBinaryMapper.java
- `M` serde-bson/src/main/java/io/micronaut/serde/bson/BsonJsonMapper.java
- `M` serde-bson/src/main/java/io/micronaut/serde/bson/BsonReaderDecoder.java
- `M` serde-bson/src/main/java/io/micronaut/serde/bson/BsonWriterEncoder.java
- `M` serde-bson/src/main/java/io/micronaut/serde/bson/custom/BsonRepresentationSerde.java
- `M` serde-bson/src/main/java/io/micronaut/serde/bson/custom/CustomBsonSerdes.java
- `A` serde-bson/src/main/java/io/micronaut/serde/bson/custom/package-info.java
- `A` serde-bson/src/main/java/io/micronaut/serde/bson/package-info.java
- `M` serde-jackson-tck/src/main/java/io/micronaut/serde/jackson/MyBeanConstructorWithUnwrappedAlwaysInclude.java
- `M` serde-jackson-tck/src/main/java/io/micronaut/serde/jackson/MyBeanWithUnwrappedAlwaysInclude.java
- `A` serde-jackson-tck/src/main/java/io/micronaut/serde/jackson/builder/package-info.java
- `A` serde-jackson-tck/src/main/java/io/micronaut/serde/jackson/jsonvalue/package-info.java
- `A` serde-jackson-tck/src/main/java/io/micronaut/serde/jackson/maps/package-info.java
- `A` serde-jackson-tck/src/main/java/io/micronaut/serde/jackson/outerinterface/package-info.java
- `A` serde-jackson-tck/src/main/java/io/micronaut/serde/jackson/shape/EnumObjectShapeBean.java
- `A` serde-jackson-tck/src/main/java/io/micronaut/serde/jackson/shape/package-info.java
- `A` serde-jackson-tck/src/main/java/io/micronaut/serde/jackson/tst/package-info.java
- `M` serde-jackson/src/main/java/io/micronaut/serde/jackson/JacksonDecoder.java
- `M` serde-jackson/src/main/java/io/micronaut/serde/jackson/JacksonEncoder.java
- `M` serde-jackson/src/main/java/io/micronaut/serde/jackson/JacksonJsonMapper.java
- `M` serde-jackson/src/main/java/io/micronaut/serde/jackson/JacksonObjectMapper.java
- `M` serde-jackson/src/main/java/io/micronaut/serde/jackson/SerdeJacksonConfiguration.java
- `A` serde-jackson/src/main/java/io/micronaut/serde/jackson/package-info.java
- `M` serde-jsonp/src/main/java/io/micronaut/serde/json/stream/JsonParserDecoder.java
- `M` serde-jsonp/src/main/java/io/micronaut/serde/json/stream/JsonStreamEncoder.java
- `M` serde-jsonp/src/main/java/io/micronaut/serde/json/stream/JsonStreamMapper.java
- `A` serde-jsonp/src/main/java/io/micronaut/serde/json/stream/graalvm/package-info.java
- `A` serde-jsonp/src/main/java/io/micronaut/serde/json/stream/package-info.java
- `M` serde-oracle-jdbc-json/src/main/java/io/micronaut/serde/oracle/jdbc/json/AbstractOracleJdbcJsonObjectMapper.java
- `M` serde-oracle-jdbc-json/src/main/java/io/micronaut/serde/oracle/jdbc/json/OracleJdbcJsonBinaryObjectMapper.java
- `M` serde-oracle-jdbc-json/src/main/java/io/micronaut/serde/oracle/jdbc/json/OracleJdbcJsonGeneratorEncoder.java
- `M` serde-oracle-jdbc-json/src/main/java/io/micronaut/serde/oracle/jdbc/json/OracleJdbcJsonParserDecoder.java
- `M` serde-oracle-jdbc-json/src/main/java/io/micronaut/serde/oracle/jdbc/json/OracleJdbcJsonTextObjectMapper.java
- `A` serde-oracle-jdbc-json/src/main/java/io/micronaut/serde/oracle/jdbc/json/package-info.java
- `M` serde-oracle-jdbc-json/src/main/java/io/micronaut/serde/oracle/jdbc/json/serde/AbstractOracleJsonSerde.java
- `M` serde-oracle-jdbc-json/src/main/java/io/micronaut/serde/oracle/jdbc/json/serde/OracleJsonBinarySerde.java
- `M` serde-oracle-jdbc-json/src/main/java/io/micronaut/serde/oracle/jdbc/json/serde/OracleJsonDurationSerde.java
- `M` serde-oracle-jdbc-json/src/main/java/io/micronaut/serde/oracle/jdbc/json/serde/OracleJsonLocaleDateSerde.java
- `M` serde-oracle-jdbc-json/src/main/java/io/micronaut/serde/oracle/jdbc/json/serde/OracleJsonLocaleTimeSerde.java
- `M` serde-oracle-jdbc-json/src/main/java/io/micronaut/serde/oracle/jdbc/json/serde/package-info.java
- `M` serde-processor/src/main/java/io/micronaut/serde/processor/SerdeAnnotationVisitor.java
- `A` serde-processor/src/main/java/io/micronaut/serde/processor/bson/package-info.java
- `A` serde-processor/src/main/java/io/micronaut/serde/processor/jackson/JsonEnumDefaultValueMapper.java
- `M` serde-processor/src/main/java/io/micronaut/serde/processor/jackson/JsonFormatMapper.java
- `M` serde-processor/src/main/java/io/micronaut/serde/processor/jackson/JsonTypeInfoMapper.java
- `M` serde-processor/src/main/java/io/micronaut/serde/processor/jackson/ValidatingAnnotationMapper.java
- `M` serde-processor/src/main/java/io/micronaut/serde/processor/jackson/databind/JsonDeserializeMapper.java
- `M` serde-processor/src/main/java/io/micronaut/serde/processor/jackson/databind/JsonNamingMapper.java
- `M` serde-processor/src/main/java/io/micronaut/serde/processor/jackson/databind/JsonSerializeMapper.java
- `A` serde-processor/src/main/java/io/micronaut/serde/processor/jackson/databind/package-info.java
- `A` serde-processor/src/main/java/io/micronaut/serde/processor/jackson/package-info.java
- `A` serde-processor/src/main/java/io/micronaut/serde/processor/jsonb/package-info.java
- `A` serde-processor/src/main/java/io/micronaut/serde/processor/package-info.java
- `M` serde-processor/src/main/java/io/micronaut/serde/processor/serde/DeserializableMapper.java
- `M` serde-processor/src/main/java/io/micronaut/serde/processor/serde/SerdeableMapper.java
- `M` serde-processor/src/main/java/io/micronaut/serde/processor/serde/SerializableMapper.java
- `A` serde-processor/src/main/java/io/micronaut/serde/processor/serde/package-info.java
- `A` serde-processor/src/main/java/io/micronaut/serde/processor/sourcegen/SerdeSourceGenClassNaming.java
- `A` serde-processor/src/main/java/io/micronaut/serde/processor/sourcegen/SerdeSourceGenVisitor.java
- `A` serde-processor/src/main/java/io/micronaut/serde/processor/sourcegen/SimpleSerdeShapeAnalyzer.java
- `A` serde-processor/src/main/java/io/micronaut/serde/processor/sourcegen/SimpleSerdeShapeDecision.java
- `A` serde-processor/src/main/java/io/micronaut/serde/processor/sourcegen/beans/BeanDeserializerSourceGen.java
- `A` serde-processor/src/main/java/io/micronaut/serde/processor/sourcegen/beans/BeanSerdeShape.java
- `A` serde-processor/src/main/java/io/micronaut/serde/processor/sourcegen/beans/BeanSerdeShapeResolver.java
- `A` serde-processor/src/main/java/io/micronaut/serde/processor/sourcegen/beans/BeanSerdeSourceGenUtils.java
- `A` serde-processor/src/main/java/io/micronaut/serde/processor/sourcegen/beans/BeanSerializerSourceGen.java
- `A` serde-processor/src/main/java/io/micronaut/serde/processor/sourcegen/beans/package-info.java
- `A` serde-processor/src/main/java/io/micronaut/serde/processor/sourcegen/enums/EnumDeserializerSourceGen.java
- `A` serde-processor/src/main/java/io/micronaut/serde/processor/sourcegen/enums/EnumSerdeShape.java
- `A` serde-processor/src/main/java/io/micronaut/serde/processor/sourcegen/enums/EnumSerdeShapeResolver.java
- `A` serde-processor/src/main/java/io/micronaut/serde/processor/sourcegen/enums/EnumSerdeSourceGenUtils.java
- `A` serde-processor/src/main/java/io/micronaut/serde/processor/sourcegen/enums/EnumSerializerSourceGen.java
- `A` serde-processor/src/main/java/io/micronaut/serde/processor/sourcegen/enums/package-info.java
- `A` serde-processor/src/main/java/io/micronaut/serde/processor/sourcegen/package-info.java
- `A` serde-processor/src/main/java/io/micronaut/serde/processor/sourcegen/records/RecordDeserializerSourceGen.java
- `A` serde-processor/src/main/java/io/micronaut/serde/processor/sourcegen/records/RecordSerdeShape.java
- `A` serde-processor/src/main/java/io/micronaut/serde/processor/sourcegen/records/RecordSerdeShapeResolver.java
- `A` serde-processor/src/main/java/io/micronaut/serde/processor/sourcegen/records/RecordSerdeSourceGenUtils.java
- `A` serde-processor/src/main/java/io/micronaut/serde/processor/sourcegen/records/RecordSerializerSourceGen.java
- `A` serde-processor/src/main/java/io/micronaut/serde/processor/sourcegen/records/package-info.java
- `M` serde-processor/src/main/resources/META-INF/services/io.micronaut.inject.annotation.AnnotationMapper
- `M` serde-processor/src/main/resources/META-INF/services/io.micronaut.inject.visitor.TypeElementVisitor
- `M` serde-support/src/main/java/io/micronaut/serde/support/AbstractDecoderPerStructureStreamDecoder.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/AbstractStreamDecoder.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/DefaultEncoderContext.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/DefaultSerdeRegistry.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/DeserializerRegistrar.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/LegacyBeansFactory.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/SerdeRegistrar.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/SerializerRegistrar.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/bind/SerdeJsonBeanPropertyBinderExceptionHandler.java
- `A` serde-support/src/main/java/io/micronaut/serde/support/bind/package-info.java
- `A` serde-support/src/main/java/io/micronaut/serde/support/config/package-info.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/DelegatingObjectDeserializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/DemuxingObjectDecoder.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/DeserBean.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/DeserBeanKey.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/DeserBeanRegistry.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/DeserBeanSubtypeInfo.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/DeserializerSubtypeInfo.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/ErrorCatchingDeserializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/HealthResultDeserializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/JsonValueDeserializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/ObjectDeserializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/PropertiesBag.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/ResolvedDeserializerSubtypeInfo.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/SimpleObjectDeserializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/SimpleRecordLikeObjectDeserializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/SubtypedDeductionDeserializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/SubtypedExternalPropertyObjectDeserializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/SubtypedPropertyObjectDeserializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/WrappedArraySubtypedDeserializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/WrappedObjectDeserializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/WrappedObjectSubtypedDeserializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/collect/ArrayDequeDeserializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/collect/ArrayListDeserializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/collect/CollectionDeserializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/collect/ConvertibleValuesDeserializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/collect/CoreCollectionsDeserializers.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/collect/EnumMapDeserializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/collect/HashMapDeserializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/collect/HashSetDeserializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/collect/LinkedHashMapDeserializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/collect/LinkedHashSetDeserializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/collect/LinkedListDeserializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/collect/MapDeserializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/collect/StringListDeserializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/collect/TreeMapDeserializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/collect/TreeSetDeserializer.java
- `A` serde-support/src/main/java/io/micronaut/serde/support/deserializers/collect/package-info.java
- `A` serde-support/src/main/java/io/micronaut/serde/support/deserializers/package-info.java
- `A` serde-support/src/main/java/io/micronaut/serde/support/package-info.java
- `A` serde-support/src/main/java/io/micronaut/serde/support/serdes/AbstractArraySerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/BigDecimalSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/BigIntegerSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/BooleanArraySerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/BooleanSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/ByteArraySerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/ByteBufferSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/ByteSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/CharArraySerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/CharSequenceSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/CharSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/CharsetSerde.java
- `D` serde-support/src/main/java/io/micronaut/serde/support/serdes/CoreSerdes.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/CustomizedObjectArraySerializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/DateSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/DefaultFormattedTemporalSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/DoubleArraySerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/DoubleSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/EnumSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/FloatArraySerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/FloatSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/FormattedNumberSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/FormattedTemporalSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/InetAddressSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/InstantSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/IntArraySerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/IntegerSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/JacksonJsonNodeSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/JsonNodeSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/LocalDateSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/LocalDateTimeSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/LocalTimeSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/LocaleSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/LongArraySerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/LongSerde.java
- `A` serde-support/src/main/java/io/micronaut/serde/support/serdes/MapEntrySerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/NumberSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/NumberTypeSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/NumericSupportTemporalSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/ObjectArraySerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/OffsetDateTimeSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/OptionalDoubleSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/OptionalIntSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/OptionalLongSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/OptionalSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/Serdes.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/ShortArraySerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/ShortSerde.java
- `A` serde-support/src/main/java/io/micronaut/serde/support/serdes/SingleElementArraySerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/SqlDateSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/SqlTimestampSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/StringArraySerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/StringSerde.java
- `A` serde-support/src/main/java/io/micronaut/serde/support/serdes/TemporalArrayShapeSupport.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/TemporalSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/TimeZoneSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/URISerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/URLSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/UUIDSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/YearSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/ZoneIdSerde.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serdes/ZonedDateTimeSerde.java
- `A` serde-support/src/main/java/io/micronaut/serde/support/serdes/package-info.java
- `A` serde-support/src/main/java/io/micronaut/serde/support/serializers/AbstractIterableSerializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serializers/AbstractMapObjectSerializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serializers/CustomizedIterableSerializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serializers/CustomizedObjectSerializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serializers/ErrorCatchingSerializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serializers/IterableSerializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serializers/JsonValueSerializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serializers/ObjectSerializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serializers/OptionalMultiValuesSerializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serializers/OptionalValuesSerializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serializers/RuntimeMapSerializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serializers/RuntimeTypeSerializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serializers/RuntimeValueIterableSerializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serializers/SerBean.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serializers/SerBeanKey.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serializers/SimpleObjectSerializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/serializers/StringIterableSerializer.java
- `A` serde-support/src/main/java/io/micronaut/serde/support/serializers/package-info.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/util/BeanDefKey.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/util/BufferingJsonNodeProcessor.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/util/JsonArrayNodeDecoder.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/util/JsonNodeDecoder.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/util/JsonNodeEncoder.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/util/JsonObjectNodeDecoder.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/util/JsonViewUtil.java
- `A` serde-support/src/main/java/io/micronaut/serde/support/util/ObjectShapeSerdeHelper.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/util/SerdeAnnotationUtil.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/util/SerdeArgumentConf.java
- `A` serde-support/src/main/java/io/micronaut/serde/support/util/SerdeFeatures.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/util/SpreadProcessor.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/util/SubtypeInfo.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/util/TypeKey.java
- `A` serde-support/src/main/java/io/micronaut/serde/support/util/package-info.java
- `M` serde-tck/src/main/java/io/micronaut/serde/AllTypesBean.java
- `M` serde-tck/src/main/java/io/micronaut/serde/ObjectWithArray.java
- `M` serde-tck/src/main/java/io/micronaut/serde/ObjectWithArrayConstructor.java
- `M` serde-tck/src/main/java/io/micronaut/serde/ObjectWithArrayRecord.java
- `M` serde-tck/src/main/java/io/micronaut/serde/ObjectWithArrayRecordNotNull.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `D` benchmarks/src/typeCheckTest/java/io/micronaut/serde/TypeThrashingTest.java
- `M` serde-api/src/main/java/io/micronaut/serde/SerdeIntrospections.java
- `M` serde-api/src/test/groovy/io/micronaut/serde/config/SerdeConfigurationSpec.groovy
- `M` serde-bson/src/test/groovy/io/micronaut/serde/bson/BsonCompileSpec.groovy
- `M` serde-bson/src/test/groovy/io/micronaut/serde/bson/BsonHttpCrudSpec.groovy
- `M` serde-bson/src/test/java/io/micronaut/serde/bson/BookWithConstructor.java
- `M` serde-bson/src/test/java/io/micronaut/serde/bson/DefaultNonNullCollectionsObj.java
- `M` serde-bson/src/test/java/io/micronaut/serde/bson/DefaultNullableCollectionsObj.java
- `M` serde-bson/src/test/java/io/micronaut/serde/bson/Sale1.java
- `A` serde-jackson-tck/src/main/groovy/io/micronaut/serde/jackson/GlobalFeaturesSpec.groovy
- `M` serde-jackson-tck/src/main/groovy/io/micronaut/serde/jackson/JsonCompileSpec.groovy
- `M` serde-jackson-tck/src/main/groovy/io/micronaut/serde/jackson/JsonEnumSpec.groovy
- `M` serde-jackson-tck/src/main/groovy/io/micronaut/serde/jackson/JsonExceptionSpec.groovy
- `M` serde-jackson-tck/src/main/groovy/io/micronaut/serde/jackson/JsonFormatSpec.groovy
- `M` serde-jackson-tck/src/main/groovy/io/micronaut/serde/jackson/JsonGetterSetterSpec.groovy
- `M` serde-jackson-tck/src/main/groovy/io/micronaut/serde/jackson/JsonIgnoreAllowSpec.groovy
- `M` serde-jackson-tck/src/main/groovy/io/micronaut/serde/jackson/JsonIgnoreSpec.groovy
- `M` serde-jackson-tck/src/main/groovy/io/micronaut/serde/jackson/JsonIncludeSpec.groovy
- `M` serde-jackson-tck/src/main/groovy/io/micronaut/serde/jackson/JsonNamingSpec.groovy
- `M` serde-jackson-tck/src/main/groovy/io/micronaut/serde/jackson/JsonPropertyOrderSpec.groovy
- `M` serde-jackson-tck/src/main/groovy/io/micronaut/serde/jackson/JsonPropertySpec.groovy
- `M` serde-jackson-tck/src/main/groovy/io/micronaut/serde/jackson/JsonSerializeDeserializeSpec.groovy
- `M` serde-jackson-tck/src/main/groovy/io/micronaut/serde/jackson/JsonSubtypesSpec.groovy
- `M` serde-jackson-tck/src/main/groovy/io/micronaut/serde/jackson/JsonTypeInfoSpec.groovy
- `M` serde-jackson-tck/src/main/groovy/io/micronaut/serde/jackson/JsonUnwrappedSpec.groovy
- `M` serde-jackson-tck/src/main/groovy/io/micronaut/serde/jackson/JsonValueSpec.groovy
- `M` serde-jackson-tck/src/main/groovy/io/micronaut/serde/jackson/JsonViewSpec.groovy
- `M` serde-jackson-tck/src/main/java/io/micronaut/serde/jackson/builder/TestBuildMe.java
- `M` serde-jackson-tck/src/main/java/io/micronaut/serde/jackson/builder/TestBuildMe2.java
- `M` serde-jackson-tck/src/main/java/io/micronaut/serde/jackson/builder/TestBuildName.java
- `M` serde-jackson-tck/src/main/java/io/micronaut/serde/jackson/builder/TestBuildSubtype.java
- `M` serde-jackson-tck/src/main/java/io/micronaut/serde/jackson/builder/TestBuildSubtype2.java
- `M` serde-jackson-tck/src/main/java/io/micronaut/serde/jackson/builder/TestBuildSupertype2.java
- `A` serde-jackson-tck/src/main/java/io/micronaut/serde/jackson/builder/introspected/package-info.java
- `M` serde-jackson/src/test/groovy/custom/serde/Simple2Serializer.groovy
- `M` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/ConfigCloneSpec.groovy
- `M` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/CustomPrimitiveSerdeSpec.groovy
- `M` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/CustomStringSerdeSpec.groovy
- `M` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/JacksonDecoderSpec.groovy
- `M` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/JacksonJsonNodeSerdeSpec.groovy
- `M` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/JsonAnyGetterSpec.groovy
- `M` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/JsonCompileSpec.groovy
- `M` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/MyBeanWithMap.java
- `M` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/MyBeanWithNestedObject.java
- `M` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/SerdeImportSpec.groovy
- `M` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/annotation/JacksonConfigurationSpec.groovy
- `A` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/annotation/SerdeGlobalFeaturesSpec.groovy
- `M` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/annotation/SerdeJsonFormatSpec.groovy
- `M` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/annotation/SerdeJsonIgnoreSpec.groovy
- `M` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/annotation/SerdeJsonPropertySpec.groovy
- `M` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/annotation/SerdeJsonSerializeDeserializeSpec.groovy
- `M` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/annotation/SerdeJsonSubtypesKotlinSpec.groovy
- `M` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/annotation/SerdeJsonSubtypesSpec.groovy
- `M` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/annotation/SerdeJsonUnwrappedSpec.groovy
- `M` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/annotation/SerdeJsonValueSpec.groovy
- `A` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/annotation/SerdeRuntimeSelectionSpec.groovy
- `A` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/annotation/SerdeSourceGenBeanSpec.groovy
- `A` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/annotation/SerdeSourceGenEligibilitySpec.groovy
- `A` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/annotation/SerdeSourceGenEnumSpec.groovy
- `A` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/annotation/SerdeSourceGenRecordSpec.groovy
- `A` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/annotation/SerdeSourceGenRoutingSpec.groovy
- `M` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/builder/BuilderSpec.groovy
- `A` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/compiletime/CompileTimeDeserializerBehaviorSpec.groovy
- `A` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/compiletime/CompileTimeSourceGenSpec.groovy
- `A` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/compiletime/SerdeableGeneratedSpec.groovy
- `M` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/generic/scenario1/DeleteResponse.java
- `M` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/generic/scenario1/V1Namespace.java
- `M` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/generic/scenario1/V1Status.java
- `M` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/generic/scenario2/DeleteResponse.java
- `M` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/generic/scenario2/V1Namespace.java
- `M` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/generic/scenario2/V1Status.java
- `M` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/generic/scenario3/V1Namespace.java
- `M` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/generic/scenario3/V1Status.java
- `M` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/mixin/MessageMixin.java
- `M` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/object/ObjectSerdeSpec.groovy
- `M` serde-jackson/src/test/groovy/io/micronaut/serde/jackson/serdeimport/JodaDateTimeSerde.java
- `D` serde-jackson/src/test/java/io/micronaut/serde/jackson/builder/ComputeInstanceDetails.java
- `D` serde-jackson/src/test/java/io/micronaut/serde/jackson/builder/ComputeInstanceOptions.java
- `D` serde-jackson/src/test/java/io/micronaut/serde/jackson/builder/InstanceConfiguration.java
- `D` serde-jackson/src/test/java/io/micronaut/serde/jackson/builder/InstanceConfigurationInstanceDetails.java
- `M` serde-jackson/src/test/java/io/micronaut/serde/jackson/builder/TestBuildMe.java
- `M` serde-jackson/src/test/java/io/micronaut/serde/jackson/builder/TestBuildMe2.java
- `M` serde-jackson/src/test/java/io/micronaut/serde/jackson/builder/TestBuildName.java
- `M` serde-jackson/src/test/java/io/micronaut/serde/jackson/builder/TestBuildSubtype.java
- `M` serde-jackson/src/test/java/io/micronaut/serde/jackson/builder/TestBuildSubtype2.java
- `M` serde-jackson/src/test/java/io/micronaut/serde/jackson/builder/TestBuildSupertype2.java
- `A` serde-jackson/src/test/java/io/micronaut/serde/jackson/compiletime/SourceGenAnyGetterSkipSerializerShape.java
- `A` serde-jackson/src/test/java/io/micronaut/serde/jackson/compiletime/SourceGenBoundaryDispatchBean.java
- `A` serde-jackson/src/test/java/io/micronaut/serde/jackson/compiletime/SourceGenBoundaryDispatchRecord.java
- `A` serde-jackson/src/test/java/io/micronaut/serde/jackson/compiletime/SourceGenGeneratedConstructorDefaults.java
- `A` serde-jackson/src/test/java/io/micronaut/serde/jackson/compiletime/SourceGenGeneratedPropertyDefaults.java
- `A` serde-jackson/src/test/java/io/micronaut/serde/jackson/compiletime/SourceGenGeneratedShape.java
- `A` serde-jackson/src/test/java/io/micronaut/serde/jackson/compiletime/SourceGenIndexedShapeBean.java
- `A` serde-jackson/src/test/java/io/micronaut/serde/jackson/compiletime/SourceGenIndexedShapeRecord.java
- `A` serde-jackson/src/test/java/io/micronaut/serde/jackson/compiletime/SourceGenLargeDispatchBean.java
- `A` serde-jackson/src/test/java/io/micronaut/serde/jackson/compiletime/SourceGenLargeDispatchNonNullRecord.java
- `A` serde-jackson/src/test/java/io/micronaut/serde/jackson/compiletime/SourceGenLargeDispatchRecord.java
- `A` serde-jackson/src/test/java/io/micronaut/serde/jackson/compiletime/SourceGenRequiredFalseUnsupportedShape.java
- `A` serde-jackson/src/test/java/io/micronaut/serde/jackson/compiletime/SourceGenRuntimeConstructorDefaults.java
- `A` serde-jackson/src/test/java/io/micronaut/serde/jackson/compiletime/SourceGenRuntimeLargeDispatchNonNullRecord.java
- `A` serde-jackson/src/test/java/io/micronaut/serde/jackson/compiletime/SourceGenRuntimePropertyDefaults.java
- `A` serde-jackson/src/test/java/io/micronaut/serde/jackson/compiletime/SourceGenRuntimeSmallDispatchNonNullRecord.java
- `A` serde-jackson/src/test/java/io/micronaut/serde/jackson/compiletime/SourceGenSkipDeserializerShape.java
- `A` serde-jackson/src/test/java/io/micronaut/serde/jackson/compiletime/SourceGenSkipSerializerShape.java
- `A` serde-jackson/src/test/java/io/micronaut/serde/jackson/compiletime/SourceGenSkippedShape.java
- `A` serde-jackson/src/test/java/io/micronaut/serde/jackson/compiletime/SourceGenSmallDispatchBean.java
- `A` serde-jackson/src/test/java/io/micronaut/serde/jackson/compiletime/SourceGenSmallDispatchNonNullRecord.java
- `A` serde-jackson/src/test/java/io/micronaut/serde/jackson/compiletime/SourceGenSmallDispatchRecord.java
- `M` serde-oracle-jdbc-json/src/test/groovy/io/micronaut/serde/oracle/jdbc/json/OracleJsonMappingSpec.groovy
- `A` serde-oracle-jdbc-json/src/test/java/io/micronaut/serde/bson/Library.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/DefaultSerdeIntrospections.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/SpecificObjectDeserializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/collect/SpecificOnlyCollectionDeserializer.java
- `M` serde-support/src/main/java/io/micronaut/serde/support/deserializers/collect/SpecificOnlyMapDeserializer.java
- `M` serde-support/src/test/groovy/io/micronaut/serde/support/deserializers/DeserializeSpec.groovy
- `M` serde-support/src/test/groovy/io/micronaut/serde/util/BufferingJsonNodeProcessorSpec.groovy
- `A` serde-support/src/test/java/io/micronaut/serde/support/MissingCustomDeserializerRetryTest.java
- `A` serde-support/src/test/java/io/micronaut/serde/support/MissingCustomDeserializerTest.java
- `M` serde-support/src/test/java/io/micronaut/serde/support/TestStatus.java
- `M` serde-tck-tests/src/main/java/io/micronaut/serde/tck/tests/bytebuffer/package-info.java
- `A` serde-tck-tests/src/main/java/io/micronaut/serde/tck/tests/package-info.java
- `M` serde-tck/src/main/groovy/io/micronaut/serde/AbstractBasicSerdeCompileSpec.groovy
- `M` serde-tck/src/main/groovy/io/micronaut/serde/AbstractJsonCompileSpec.groovy
- `M` serde-tck/src/main/groovy/io/micronaut/serde/MockSerdeIntrospections.groovy
- `M` test-suite-http-server-tck-netty/src/test/java/io/micronaut/serde/http/server/tck/netty/NettyHttpServerTestSuite.java
- `M` test-suite-tck-jackson-databind/src/test/groovy/io/micronaut/serde/tck/jackson/databind/DatabindBasicSerdeSpec.groovy
- `M` test-suite-tck-jackson-databind/src/test/groovy/io/micronaut/serde/tck/jackson/databind/DatabindFiltersRegistrar.java
- `A` test-suite-tck-jackson-databind/src/test/groovy/io/micronaut/serde/tck/jackson/databind/DatabindGlobalFeaturesSpec.groovy
- `M` test-suite-tck-jackson-databind/src/test/groovy/io/micronaut/serde/tck/jackson/databind/DatabindJsonEnumSpec.groovy
- `M` test-suite-tck-jackson-databind/src/test/groovy/io/micronaut/serde/tck/jackson/databind/DatabindJsonExceptionSpec.groovy
- `M` test-suite-tck-jackson-databind/src/test/groovy/io/micronaut/serde/tck/jackson/databind/DatabindJsonFilterSpec.groovy
- `M` test-suite-tck-jackson-databind/src/test/groovy/io/micronaut/serde/tck/jackson/databind/DatabindJsonFormatSpec.groovy
- `M` test-suite-tck-jackson-databind/src/test/groovy/io/micronaut/serde/tck/jackson/databind/DatabindJsonIgnoreAllowSpec.groovy
- `M` test-suite-tck-jackson-databind/src/test/groovy/io/micronaut/serde/tck/jackson/databind/DatabindJsonIgnoreSpec.groovy
- `M` test-suite-tck-jackson-databind/src/test/groovy/io/micronaut/serde/tck/jackson/databind/DatabindJsonPropertyOrderSpec.groovy
- `M` test-suite-tck-jackson-databind/src/test/groovy/io/micronaut/serde/tck/jackson/databind/DatabindJsonPropertySpec.groovy
- `M` test-suite-tck-jackson-databind/src/test/groovy/io/micronaut/serde/tck/jackson/databind/DatabindJsonRootNameSpec.groovy
- `M` test-suite-tck-jackson-databind/src/test/groovy/io/micronaut/serde/tck/jackson/databind/DatabindJsonTypeInfoSpec.groovy
- `M` test-suite-tck-jackson-databind/src/test/groovy/io/micronaut/serde/tck/jackson/databind/DatabindJsonValueSpec.groovy
- `M` test-suite-tck-jackson-databind/src/test/groovy/io/micronaut/serde/tck/jackson/databind/DatabindPredicateFilter.java
- `A` test-suite-tck-jackson-databind/src/test/java/io/micronaut/serde/tck/jackson/databind/CompoundLocaleObjectMapperListener.java
- `A` test-suite-tck-jackson-databind/src/test/resources/application.properties

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

