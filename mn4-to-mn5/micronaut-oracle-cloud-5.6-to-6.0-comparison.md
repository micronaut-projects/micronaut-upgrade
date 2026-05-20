Compared micronaut-oracle-cloud as mn4 -> mn5.

  Scope

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-oracle-cloud, branch 5.6.x, SHA 96d77de29e51
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-oracle-cloud, branch 6.0.x, SHA bf5117799b85
  - Same remote, both clean: git@github.com:micronaut-projects/micronaut-oracle-cloud.git
  - Report: /private/tmp/micronaut-oracle-cloud-5.6-to-6.0-comparison.md

  Key Findings

  - Major line move: 5.6.3-SNAPSHOT -> 6.0.1-SNAPSHOT.
  - Platform/build upgrade: Micronaut 4.10.14 -> 5.0.0, Platform 4.10.2 -> 5.0.0-RC1, Gradle 8.14.3 -> 9.5.1,
    Java/GraalVM 25.0.1-graal.
  - OCI SDK updated 3.77.2 -> 3.86.1; Graal SVM 23.1.10 -> 25.0.3; Fn 1.0.218 -> 1.1.12.
  - Oracle Cloud Vault now supports micronaut.config.import via provider oraclecloud-vault; legacy bootstrap
    ConfigurationClient is deprecated and logs a warning.
  - Vault import supports connection-string and provider-map forms, includes/excludes, retry options, and OCI
    auth options; docs note it is startup-load only.
  - Autonomous Database docs and code add service-alias-suffix, defaulting to high; explicit service-alias
    still takes precedence.
  - Function HTTP moved away from MediaTypeCodec to MessageBodyHandlerRegistry / JsonMapper, with better
    request/response adapter behavior.
  - OciFunction now registers SerdeCoercion using Micronaut JsonMapper; the old enableSharedJackson() hook
    was removed.
  - OCI serde configuration was extracted into concrete default beans for Netty and Apache HTTP clients.
  - Oracle Cloud Logging appender behavior was stabilized around missing/deferred logId, queued events, and
    emergency appenders.
  - Common CI/template updates added vulnerability audit scripts, Sonatype workflow, Java 25 setup, and
    shared agent skill files.

  Diff size: 284 files changed, 8585 insertions(+), 2205 deletions(-).

  I did not run tests; this was a folder comparison and targeted source/build-diff review only.

# Release Note Comparison

Generated: 2026-05-19 14:32 UTC
Comparison: `5.6.x` -> `6.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-oracle-cloud` | `5.6.x` | `96d77de29e51` | `git@github.com:micronaut-projects/micronaut-oracle-cloud.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-oracle-cloud` | `6.0.x` | `bf5117799b85` | `git@github.com:micronaut-projects/micronaut-oracle-cloud.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-oracle-cloud`
- Commit candidates found: 123
- File changes listed: 284
- Version values listed: 69
- File status counts: A=69, D=16, M=199

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `5.6.3-SNAPSHOT` | `6.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.graal-svm` | `org.graalvm.nativeimage:svm:23.1.10` | `org.graalvm.nativeimage:svm:25.0.3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.groovy` | `org.apache.groovy:groovy-bom:4.0.28` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.gson` | `com.google.code.gson:gson:2.13.2` | `com.google.code.gson:gson:2.13.2` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.micronaut-discovery-client` | `io.micronaut.discovery:micronaut-discovery-client-bom:4.7.1` | `io.micronaut.discovery:micronaut-discovery-client-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-docs` | `io.micronaut.docs:micronaut-docs-asciidoc-config-props:3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-gradle-plugin` | `io.micronaut.gradle:micronaut-gradle-plugin:4.6.1` | `io.micronaut.gradle:micronaut-gradle-plugin:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-groovy` | `io.micronaut.groovy:micronaut-groovy-bom:4.7.0` | `io.micronaut.groovy:micronaut-groovy-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-kotlin` | `io.micronaut.kotlin:micronaut-kotlin-bom:4.7.0` | `io.micronaut.kotlin:micronaut-kotlin-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-kubernetes` | `io.micronaut.kubernetes:micronaut-kubernetes-bom:7.1.1` | `io.micronaut.kubernetes:micronaut-kubernetes-bom:8.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-logging` | `io.micronaut.logging:micronaut-logging-bom:1.7.2` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-micrometer` | `io.micronaut.micrometer:micronaut-micrometer-bom:5.13.2` | `io.micronaut.micrometer:micronaut-micrometer-bom:6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-reactor` | `io.micronaut.reactor:micronaut-reactor-bom:3.9.1` | `io.micronaut.reactor:micronaut-reactor-bom:4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-rxjava2` | `io.micronaut.rxjava2:micronaut-rxjava2-bom:2.9.0` | `io.micronaut.rxjava2:micronaut-rxjava2-bom:2.9.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.micronaut-security` | `io.micronaut.security:micronaut-security-bom:4.15.1` | `io.micronaut.security:micronaut-security-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.16.2` | `io.micronaut.serde:micronaut-serde-bom:3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-servlet` | `io.micronaut.servlet:micronaut-servlet-bom:5.6.0` | `io.micronaut.servlet:micronaut-servlet-bom:6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-sourcegen` | `io.micronaut.sourcegen:micronaut-sourcegen-bom:1.8.4` | `io.micronaut.sourcegen:micronaut-sourcegen-bom:2.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-sql` | `io.micronaut.sql:micronaut-sql-bom:6.3.2` | `io.micronaut.sql:micronaut-sql-bom:7.0.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test` | `io.micronaut.test:micronaut-test-bom:4.10.2` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-validation` | `io.micronaut.validation:micronaut-validation-bom:4.12.0` | `io.micronaut.validation:micronaut-validation-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.objenesis` | `not present` | `org.objenesis:objenesis:3.5` | `added` |
| `gradle/libs.versions.toml` | `libraries.oci-bom` | `com.oracle.oci.sdk:oci-java-sdk-bom:3.77.2` | `com.oracle.oci.sdk:oci-java-sdk-bom:3.86.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.oci-common` | `oci-common:3.77.2` | `oci-common:3.86.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.oci-common-httpclient` | `oci-common-httpclient:3.77.2` | `oci-common-httpclient:3.86.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.oci-common-httpclient-jersey3` | `oci-common-httpclient-jersey3:3.77.2` | `oci-common-httpclient-jersey3:3.86.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.oci-disasterrecovery` | `oci-disasterrecovery:3.77.2` | `oci-disasterrecovery:3.86.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.oci-encryption` | `oci-encryption:3.77.2` | `oci-encryption:3.86.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.oci-graalvm` | `oci-graalvm:3.77.2` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.oci-objectstorage` | `oci-objectstorage:3.77.2` | `oci-objectstorage:3.86.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.oci-oke-workload-identity` | `oci-oke-workload-identity:3.77.2` | `oci-oke-workload-identity:3.86.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.oracle-security-cert` | `com.oracle.database.security:osdt_cert:21.20.0.0` | `com.oracle.database.security:osdt_cert:21.21.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.oracle-security-core` | `com.oracle.database.security:osdt_core:21.20.0.0` | `com.oracle.database.security:osdt_core:21.21.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.protobuf-gradle-plugin` | `com.google.protobuf:protobuf-gradle-plugin (version.ref=protobuf)` | `com.google.protobuf:protobuf-gradle-plugin (version.ref=protobuf)` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.shadow-plugin` | `gradle.plugin.com.github.johnrengelman:shadow (version.ref=shadow)` | `com.gradleup.shadow:shadow-gradle-plugin (version.ref=shadow)` | `changed` |
| `gradle/libs.versions.toml` | `libraries.spock` | `org.spockframework:spock-bom:2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.commons-lang3` | `3.20.0` | `3.20.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.graal-svm` | `23.1.10` | `25.0.3` | `changed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.28` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.gson` | `2.13.2` | `2.13.2` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.jackson2` | `not present` | `2.21.3` | `added` |
| `gradle/libs.versions.toml` | `versions.managed-apache-http-core5` | `5.3.6` | `5.4.2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.14` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-discovery-client` | `4.7.1` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.6.1` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-groovy` | `4.7.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-kotlin` | `4.7.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-kubernetes` | `7.1.1` | `8.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.2` | `2.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-micrometer` | `5.13.2` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-platform` | `4.10.2` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-reactor` | `3.9.1` | `4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-rxjava2` | `2.9.0` | `2.9.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.micronaut-security` | `4.15.1` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.16.2` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-servlet` | `5.6.0` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-sourcegen` | `1.8.4` | `2.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-sql` | `6.3.2` | `7.0.1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.10.2` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.12.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.objenesis` | `not present` | `3.5` | `added` |
| `gradle/libs.versions.toml` | `versions.oci` | `3.77.2` | `3.86.1` | `changed` |
| `gradle/libs.versions.toml` | `versions.oracle-database-security` | `21.20.0.0` | `21.21.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |
| `settings.gradle.kts` | `plugin.io.micronaut.build.shared.settings` | `7.6.6` | `8.0.0-M18` | `changed` |
| `settings.gradle.kts` | `plugin.me.champeau.includegit` | `0.3.1` | `0.3.2` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `ee477b73b7ad` Remove usages of MediaTypeCodec (#1276) (Denis Stepanov, 2026-04-21)
- `cd34f5a9ea75` remove mavenLocal (Nemanja Mikic, 2026-04-07)
- `3f11187ec5a0` change core version, remove maven local and add test (Nemanja Mikic, 2026-04-03)

### Features

- `683c6d1e56f1` Add local Core snapshot wiring (Graeme Rocher, 2026-04-02)
- `5ed5fe19ca73` Add ability to configure service alias suffix (#1218) (Radovan Radic, 2025-11-13)

### Fixes

- `30715b6fd237` fix(deps): update fn to v1.1.11 (#1277) (renovate[bot], 2026-04-20)
- `df82a94e31b2` fix(deps): update dependency com.fasterxml.jackson.core:jackson-databind to v2.21.2 (#1272) (renovate[bot], 2026-04-20)
- `497f82f39cbe` fix(deps): update dependency com.google.protobuf:protobuf-gradle-plugin to v0.9.6 (#1244) (renovate[bot], 2026-02-26)
- `9e19ca30ee76` fix(deps): update fn to v1.1.7 (#1222) (renovate[bot], 2026-02-26)
- `68c24aa8795e` fix(deps): update kotlin monorepo to v2.3.10 (#1248) (renovate[bot], 2026-02-23)
- `0845a251e08c` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#1216) (renovate[bot], 2025-11-28)
- `5106bcacb403` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#1226) (renovate[bot], 2025-11-28)

### Security

- `7ba9699fec4a` micronaut-security = "5.0.0-M2" (Sergio del Amo, 2026-04-20)
- `1a961954216c` micronaut-security = "5.0.0-M2" (Sergio del Amo, 2026-04-20)
- `472fad852cca` Update oracle.database.security to v21.21.0.0 (#1266) (renovate[bot], 2026-04-20)

### Dependency Updates

- `b99043bb357c` chore: Bump version to 6.0.1-SNAPSHOT (micronaut-build, 2026-05-18)
- `95167be03c29` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2026-05-11)
- `dd8a2ec4170e` Update oci version to 3.86.1 (#1300) (Sergio del Amo, 2026-05-11)
- `1b7ba0487632` Update dependency com.fasterxml.jackson.core:jackson-databind to v2.21.3 (#1287) (renovate[bot], 2026-05-11)
- `2ac0bd8a5712` Update dependency org.graalvm.nativeimage:svm to v25.0.3 (#1286) (renovate[bot], 2026-05-11)
- `d9c5c453e5d7` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2026-05-11)
- `3edcb4b2b7dc` Update Micronaut dependencies (#1289) (renovate[bot], 2026-05-01)
- `b9f234f8ba3a` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2026-04-21)
- `db64b0c2f3e2` chore(deps): update dependency com.google.protobuf:protoc to v3.25.9 (#1275) (renovate[bot], 2026-04-20)
- `c5fe7ba5e81f` Update dependency org.graalvm.nativeimage:svm to v25 (#1268) (renovate[bot], 2026-04-20)
- `98f6783554c3` Update dependency org.objenesis:objenesis to v3.5 (#1255) (renovate[bot], 2026-04-20)
- `7c02fdda72b7` chore(deps): update gradle to v9.4.1 (#1265) (renovate[bot], 2026-04-20)
- `89bc13ee1e80` Update dependency org.apache.httpcomponents.core5:httpcore5 to v5.4.2 (#1245) (renovate[bot], 2026-04-20)
- `588e82596209` Update dependency com.gradleup.shadow:shadow-gradle-plugin to v9 (#1267) (renovate[bot], 2026-04-20)
- `8e9d97d929c3` Update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-M7 (#1274) (renovate[bot], 2026-04-20)
- `cb5f6456f8dd` Update dependency io.micronaut:micronaut-core-bom to v5.0.0-M23 (#1280) (renovate[bot], 2026-04-20)
- `44022328ef09` Update dependency io.micronaut.reactor:micronaut-reactor-bom to v4.0.0-M2 (#1281) (renovate[bot], 2026-04-20)
- `e07df3c3fc8f` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2026-02-27)
- `701dab12dbed` chore(deps): update gradle/actions digest to f29f5a9 (#1253) (renovate[bot], 2026-02-23)
- `e70ae3d6c357` chore(deps): update actions/setup-java action to v5 (#1237) (renovate[bot], 2026-02-23)
- `087db629c035` chore(deps): update softprops/action-gh-release action to v2.5.0 (#1234) (renovate[bot], 2026-02-23)
- `b61955888378` chore(deps): update mikepenz/action-junit-report action to v6 (#1241) (renovate[bot], 2026-02-23)
- `6d4b781ba070` chore(deps): update actions/cache action to v5 (#1249) (renovate[bot], 2026-02-23)
- `63f39997e66f` id("io.micronaut.build.shared.settings") version "8.0.0-M17" (Sergio del Amo, 2026-02-20)
- `3ecbac64214a` chore(deps): update graalvm/setup-graalvm action to v1.4.3 (#1213) (renovate[bot], 2025-11-28)
- `9730ca477256` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#1214) (renovate[bot], 2025-11-28)
- `7c9495c708f1` chore(deps): update softprops/action-gh-release action to v2.4.2 (#1215) (renovate[bot], 2025-11-28)
- `9034fcc7fef5` chore(deps): update gradle to v9.2.1 (#1223) (renovate[bot], 2025-11-28)
- `b1c55b2ddf67` chore(deps): update actions/checkout action to v6 (#1229) (renovate[bot], 2025-11-28)
- `15e8a786bc83` chore(deps): update actions/github-script action to v8 (#1230) (renovate[bot], 2025-11-28)
- `2ab141b52231` Update dependency io.micronaut.micrometer:micronaut-micrometer-bom to v5.13.1 (#1202) (renovate[bot], 2025-10-21)
- `8c5258545395` Update dependency io.micronaut:micronaut-core-bom to v4.10.7 (#1201) (renovate[bot], 2025-10-21)

### Internal

- `0cff867dbb35` ci: projectVersion=6.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2026-02-27)
- `ff3be041a20b` build: set kotlin compiler options (Sergio del Amo, 2026-02-26)

### Review Candidates

- `bf5117799b85` update versions (Sergio del Amo, 2026-05-19)
- `0d6ef0ff2ebe` Update common files (#1306) (micronaut-build, 2026-05-19)
- `f6255b5b68d0` Merge pull request #1294 from micronaut-projects/nmikic/issue-537-upgrade-ojdbc-docs (Nemanja Mikic, 2026-05-19)
- `50e8303c2da5` Update common files (#1302) (micronaut-build, 2026-05-18)
- `5c7b35d7ef00` [skip ci] Release v6.0.0 (micronaut-build, 2026-05-18)
- `98d5a13dd2f5` update versions (Sergio del Amo, 2026-05-17)
- `a1aa2aa4686d` micronaut-platform = "5.0.0-RC1" (Sergio del Amo, 2026-05-13)
- `9a9e3129c416` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `bbd27ced64a2` Update fn to v1.1.12 (#1301) (renovate[bot], 2026-05-13)
- `2e0252f88000` [skip ci] Release v6.0.0-RC2 (micronaut-build, 2026-05-11)
- `e73549ea8c84` [skip ci] Release v6.0.0-RC1 (micronaut-build, 2026-05-11)
- `aea3ab1e835a` [skip ci] Release v6.0.0-RC1 (micronaut-build, 2026-05-11)
- `f1be8b68b56f` Extract OCI serde configuration beans (#1299) (Sergio del Amo, 2026-05-11)
- `818cf64ed0fa` Update library versions (Sergio del Amo, 2026-05-08)
- `a4aac9cf250b` Update common files (#1298) (micronaut-build, 2026-05-10)
- `de4deea78cdf` Update common files (#1290) (micronaut-build, 2026-05-08)
- `a1d1c163d826` Address PR review feedback (Nemanja Mikic, 2026-05-08)
- `4facd8228ac0` Address PR review feedback (Nemanja Mikic, 2026-05-07)
- `cd081c82469f` Stabilize Oracle logging appender configuration (Nemanja Mikic, 2026-05-07)
- `51177afd10eb` Address OJDBC BOM docs review feedback (Nemanja Mikic, 2026-05-05)
- `b1bfc617c844` Update OJDBC BOM documentation (Nemanja Mikic, 2026-05-05)
- `6fbd6912c382` Update common files (#1288) (micronaut-build, 2026-05-01)
- `f3dd334c5062` Update common files (#1282) (micronaut-build, 2026-04-26)
- `d5c3d8371eca` [skip ci] Release v6.0.0-M2 (micronaut-build, 2026-04-21)
- `d24521fbe063` git: ignore .kotlin (Sergio del Amo, 2026-04-20)
- `aa78caa0bbe0` micronaut-validation = "5.0.0-M2" (Sergio del Amo, 2026-04-20)
- `cd7874c84501` micronaut-sql = "7.0.1-M1" (Sergio del Amo, 2026-04-20)
- `92144238b78e` micronaut-servlet = "6.0.0-M3" (Sergio del Amo, 2026-04-20)
- `8aebb83eb583` Update oci to v3.84.0 (#1264) (renovate[bot], 2026-04-20)
- `3d95e918b5fd` Update GitHub Artifact Actions (#1261) (renovate[bot], 2026-04-20)
- `3686c3218a48` Update gradle/actions action to v6 (#1273) (renovate[bot], 2026-04-20)
- `9d007117d2e3` Update common files (#1263) (micronaut-build, 2026-04-20)
- `096c0f5d13d9` Update softprops/action-gh-release action to v2.6.2 (#1271) (renovate[bot], 2026-04-20)
- `f3710a0fcb44` Update to Micronaut Core 5.0.0-M22 (#1279) (Jonas Konrad, 2026-04-20)
- `5e961c094704` Merge pull request #1278 from micronaut-projects/config-import (Nemanja Mikic, 2026-04-07)
- `93ca04af38e6` fix vault tests (Nemanja Mikic, 2026-04-07)
- `d8dd87b83724` fix vault tests (Nemanja Mikic, 2026-04-07)
- `cdb6259d1711` fix vault tests (Nemanja Mikic, 2026-04-06)
- `385b9f08d338` fix build (Nemanja Mikic, 2026-04-06)
- `07006cc66352` test build (Nemanja Mikic, 2026-04-06)
- `1c73bb9a2da1` fix issues (Nemanja Mikic, 2026-04-06)
- `fcdf0da5ee00` fix small sonar issues (Nemanja Mikic, 2026-04-06)
- `d2d7a95d6412` fix small sonar issues (Nemanja Mikic, 2026-04-06)
- `7a09ed57baf7` fix small sonar issues (Nemanja Mikic, 2026-04-06)
- `01ae0d602dd4` fix sonar issues (Nemanja Mikic, 2026-04-04)
- `aa0bc947a09b` fix tck (Nemanja Mikic, 2026-04-04)
- `f028c01d9fd9` fixes for config-api and propagation context (Nemanja Mikic, 2026-04-03)
- `21b65fe2fe2f` Oracle Cloud Vault config import support (Graeme Rocher, 2026-04-02)
- `121e4795309a` [skip ci] Release v6.0.0-M1 (micronaut-build, 2026-02-27)
- `b3293b684b94` Revert "gradle 9.4.0-rc-1 (#1257)" (Sergio del Amo, 2026-02-27)
- `ed8fb9386eeb` attempt to fix release (Sergio del Amo, 2026-02-27)
- `67b394496612` gradle 9.4.0-rc-1 (#1257) (Sergio del Amo, 2026-02-27)
- `f6c4608aac92` use micronaut-build kotlin plugin (#1258) (issam liqali, 2026-02-27)
- `103c399a40d0` java 25 (Sergio del Amo, 2026-02-27)
- `cf8ffd3466b1` 25 instead of 21 for source & target compatibility (Sergio del Amo, 2026-02-26)
- `38ae23b16ebb` Revert "build: set kotlin compiler options" (Sergio del Amo, 2026-02-26)
- `e8c862bc4842` [skip ci] Release v6.0.0-M1 (micronaut-build, 2026-02-26)
- `2e0889fa9704` Oracle cloud to core milestones (#1256) (Sergio del Amo, 2026-02-26)
- `83268e79a1c2` untrack checkout/oci-java-sdk (Sergio del Amo, 2026-02-23)
- `77360efa42d8` Update common files (#1240) (micronaut-build, 2026-02-23)
- `4b973becbb51` Merge up 5.6.x into 6.0.x (Sergio del Amo, 2026-02-20)
- `7b1379fe3a32` gradle-9.3.1 (Sergio del Amo, 2026-02-20)
- `8f60ded0debf` Replace Micronaut nullability annotations with JSpecify annotations (#1233) (Copilot, 2025-12-02)
- `ac194ef823d9` Update common files (#1208) (micronaut-build, 2025-11-28)
- `b66866e8d0be` Merge branch '5.6.x' into 6.0.x (Sergio del Amo, 2025-11-05)
- `5016034b6635` Micronaut 5 compability (#1209) (issam liqali, 2025-11-04)
- `3ca97020d0e7` Merge branch '5.5.x' into 6.0.x (Sergio del Amo, 2025-10-21)
- `3f8e7a1dab03` Update common files (#1204) (micronaut-build, 2025-10-21)
- `d09300fb5dff` Update common files (#1199) (micronaut-build, 2025-10-20)
- `7100e63e060f` Update common files (#1197) (micronaut-build, 2025-10-17)
- `47b363d28ba4` Micronaut Gradle Build Plugin 8.0.0-M4 (Sergio del Amo, 2025-10-15)
- `9aca36e578a8` gradle 9.1 (Sergio del Amo, 2025-10-15)
- `b2d97ee3014f` Merge branch '5.5.x' into 6.0.x-preparation (Sergio del Amo, 2025-10-15)
- `ef19daf5c536` gradle update (Nemanja Mikic, 2025-10-08)

## Changed Files

### Compatibility Review

- `M` oraclecloud-certificates/src/main/java/io/micronaut/oraclecloud/certificates/deprecated/OracleCloudCertificateBeanCreatedEventListener.java

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` buildSrc/build.gradle
- `M` buildSrc/settings.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.ocisdk-metadata-module.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.ocisdk-metadata-protobuf.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.ocisdk-metadata-published.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.oraclecloud-base.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.oraclecloud-bom.gradle
- `A` buildSrc/src/main/groovy/io.micronaut.build.internal.oraclecloud-example-function.gradle
- `A` buildSrc/src/main/groovy/io.micronaut.build.internal.oraclecloud-example-httpfunction.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.oraclecloud-example.gradle
- `A` buildSrc/src/main/groovy/io.micronaut.build.internal.oraclecloud-groovy-example.gradle
- `A` buildSrc/src/main/groovy/io.micronaut.build.internal.oraclecloud-java-example.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.oraclecloud-kotlin-example.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.oraclecloud-module.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.oraclecloud-native-tests.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.oraclecloud-standalone-module.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.oraclecloud-tests.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` oraclecloud-atp-hikari-test/build.gradle
- `M` oraclecloud-atp-ucp-test/build.gradle
- `M` oraclecloud-atp/build.gradle.kts
- `M` oraclecloud-bom/build.gradle
- `M` oraclecloud-certificates/build.gradle
- `M` oraclecloud-common/build.gradle
- `M` oraclecloud-function-http-test/build.gradle
- `M` oraclecloud-function-http/build.gradle
- `M` oraclecloud-function/build.gradle
- `M` oraclecloud-httpclient-apache-http-core/build.gradle
- `M` oraclecloud-httpclient-netty/build.gradle
- `M` oraclecloud-logging/build.gradle
- `M` oraclecloud-micrometer/build.gradle
- `M` oraclecloud-oke-kubernetes-client/build.gradle
- `M` oraclecloud-oke-workload-identity/build.gradle
- `M` oraclecloud-sdk-base/build.gradle
- `M` oraclecloud-sdk-processor/build.gradle
- `M` oraclecloud-sdk-reactor/build.gradle
- `M` oraclecloud-sdk-rxjava2/build.gradle
- `M` oraclecloud-sdk/build.gradle
- `M` oraclecloud-serde-internal-processor/build.gradle
- `M` oraclecloud-serde-processor/build.gradle
- `M` oraclecloud-vault/build.gradle
- `M` settings-build-logic/build.gradle.kts
- `M` settings.gradle.kts
- `M` test-suite-graal-function/build.gradle
- `M` test-suite-http-client-apache/build.gradle.kts
- `M` test-suite-http-client/build.gradle.kts
- `M` test-suite-http-server-tck-oraclecloud-function-http/build.gradle.kts
- `M` test-suite-java/build.gradle

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
- `M` docs-examples/example-function-groovy/build.gradle
- `M` docs-examples/example-function-groovy/src/test/groovy/example/ListBucketsFunctionSpec.groovy
- `M` docs-examples/example-function-java/build.gradle
- `M` docs-examples/example-function-java/src/test/java/example/ListBucketsFunctionTest.java
- `M` docs-examples/example-function-java/src/test/java/example/mock/MockTenancyIdProvider.java
- `M` docs-examples/example-function-kotlin/build.gradle
- `D` docs-examples/example-function-kotlin/src/test/kotlin/example/ListBucketsFunctionTest.java
- `A` docs-examples/example-function-kotlin/src/test/kotlin/example/ListBucketsFunctionTest.kt
- `D` docs-examples/example-function-kotlin/src/test/kotlin/example/mock/MockAuthenticationDetailsProvider.java
- `A` docs-examples/example-function-kotlin/src/test/kotlin/example/mock/MockAuthenticationDetailsProvider.kt
- `D` docs-examples/example-function-kotlin/src/test/kotlin/example/mock/MockData.java
- `A` docs-examples/example-function-kotlin/src/test/kotlin/example/mock/MockData.kt
- `D` docs-examples/example-function-kotlin/src/test/kotlin/example/mock/MockObjectStorageClient.java
- `A` docs-examples/example-function-kotlin/src/test/kotlin/example/mock/MockObjectStorageClient.kt
- `D` docs-examples/example-function-kotlin/src/test/kotlin/example/mock/MockTenancyIdProvider.java
- `A` docs-examples/example-function-kotlin/src/test/kotlin/example/mock/MockTenancyIdProvider.kt
- `M` docs-examples/example-groovy/build.gradle
- `M` docs-examples/example-http-function-groovy/build.gradle
- `M` docs-examples/example-http-function-groovy/src/main/groovy/example/Book.groovy
- `M` docs-examples/example-http-function-groovy/src/test/groovy/example/BucketControllerSpec.groovy
- `M` docs-examples/example-http-function-java/build.gradle
- `M` docs-examples/example-http-function-java/src/main/java/example/Book.java
- `M` docs-examples/example-http-function-java/src/main/java/example/BucketController.java
- `M` docs-examples/example-http-function-java/src/test/java/example/BucketControllerTest.java
- `M` docs-examples/example-http-function-java/src/test/java/example/mock/MockTenancyIdProvider.java
- `M` docs-examples/example-http-function-kotlin/build.gradle
- `M` docs-examples/example-http-function-kotlin/src/main/kotlin/example/Book.kt
- `D` docs-examples/example-http-function-kotlin/src/test/kotlin/example/BookControllerTest.java
- `A` docs-examples/example-http-function-kotlin/src/test/kotlin/example/BookControllerTest.kt
- `D` docs-examples/example-http-function-kotlin/src/test/kotlin/example/BucketControllerTest.java
- `A` docs-examples/example-http-function-kotlin/src/test/kotlin/example/BucketControllerTest.kt
- `D` docs-examples/example-http-function-kotlin/src/test/kotlin/example/mock/MockAuthenticationDetailsProvider.java
- `A` docs-examples/example-http-function-kotlin/src/test/kotlin/example/mock/MockAuthenticationDetailsProvider.kt
- `D` docs-examples/example-http-function-kotlin/src/test/kotlin/example/mock/MockData.java
- `A` docs-examples/example-http-function-kotlin/src/test/kotlin/example/mock/MockData.kt
- `D` docs-examples/example-http-function-kotlin/src/test/kotlin/example/mock/MockObjectStorageClient.java
- `A` docs-examples/example-http-function-kotlin/src/test/kotlin/example/mock/MockObjectStorageClient.kt
- `D` docs-examples/example-http-function-kotlin/src/test/kotlin/example/mock/MockTenancyIdProvider.java
- `A` docs-examples/example-http-function-kotlin/src/test/kotlin/example/mock/MockTenancyIdProvider.kt
- `M` docs-examples/example-java/build.gradle
- `M` docs-examples/example-java/src/main/java/example/BucketController.java
- `M` docs-examples/example-java/src/main/java/example/BucketOperations.java
- `M` docs-examples/example-java/src/main/java/example/DatabaseController.java
- `M` docs-examples/example-java/src/main/java/example/DatabaseOperations.java
- `M` docs-examples/example-java/src/test/java/example/mock/MockTenancyIdProvider.java
- `M` docs-examples/example-kotlin/build.gradle
- `M` docs-examples/example-kotlin/src/main/kotlin/example/BucketController.kt
- `D` docs-examples/example-kotlin/src/test/java/example/BucketControllerTest.java
- `D` docs-examples/example-kotlin/src/test/java/example/mock/MockAuthenticationDetailsProvider.java
- `D` docs-examples/example-kotlin/src/test/java/example/mock/MockData.java
- `D` docs-examples/example-kotlin/src/test/java/example/mock/MockObjectStorageAsyncClient.java
- `D` docs-examples/example-kotlin/src/test/java/example/mock/MockTenancyIdProvider.java
- `M` docs-examples/example-kotlin/src/test/kotlin/example/BucketControllerTest.kt
- `A` docs-examples/example-kotlin/src/test/kotlin/example/mock/MockAuthenticationDetailsProvider.kt
- `A` docs-examples/example-kotlin/src/test/kotlin/example/mock/MockData.kt
- `A` docs-examples/example-kotlin/src/test/kotlin/example/mock/MockObjectStorageAsyncClient.kt
- `A` docs-examples/example-kotlin/src/test/kotlin/example/mock/MockTenancyIdProvider.kt
- `M` src/main/docs/guide/autonomousDatabase.adoc
- `M` src/main/docs/guide/vault.adoc

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
- `M` .github/workflows/graalvm-oci.yml
- `M` .github/workflows/publish-snapshot.yml
- `A` .github/workflows/sonatype.yml
- `M` .gitignore
- `A` .sdkmanrc
- `M` CONTRIBUTING.md
- `M` MAINTAINING.md
- `M` config/checkstyle/checkstyle.xml
- `M` oraclecloud-atp/src/main/java/io/micronaut/oraclecloud/atp/jdbc/AutonomousDatabaseConfiguration.java
- `M` oraclecloud-atp/src/main/java/io/micronaut/oraclecloud/atp/jdbc/OracleWalletArchiveProvider.java
- `M` oraclecloud-atp/src/main/java/io/micronaut/oraclecloud/atp/jdbc/hikari/HikariPoolConfigurationListener.java
- `M` oraclecloud-atp/src/main/java/io/micronaut/oraclecloud/atp/jdbc/ucp/UcpPoolConfigurationListener.java
- `M` oraclecloud-certificates/src/main/java/io/micronaut/oraclecloud/certificates/OracleCloudCertificationsConfiguration.java
- `M` oraclecloud-certificates/src/main/java/io/micronaut/oraclecloud/certificates/config/OracleCloudCertificateConfiguration.java
- `M` oraclecloud-certificates/src/main/java/io/micronaut/oraclecloud/certificates/config/OracleCloudCertificateProperties.java
- `M` oraclecloud-certificates/src/main/java/io/micronaut/oraclecloud/certificates/events/CertificateEvent.java
- `M` oraclecloud-certificates/src/main/java/io/micronaut/oraclecloud/certificates/services/OracleCloudCertificateService.java
- `M` oraclecloud-certificates/src/main/java/io/micronaut/oraclecloud/certificates/ssl/OracleCloudCertificateProvider.java
- `M` oraclecloud-common/src/main/java/io/micronaut/oraclecloud/core/AbstractOracleCloudClientConfigurationProperties.java
- `M` oraclecloud-common/src/main/java/io/micronaut/oraclecloud/core/OracleCloudClientConfigurationProperties.java
- `M` oraclecloud-common/src/main/java/io/micronaut/oraclecloud/core/OracleCloudClientPropertyRefresher.java
- `M` oraclecloud-common/src/main/java/io/micronaut/oraclecloud/core/OracleCloudConfigFileConfigurationProperties.java
- `M` oraclecloud-common/src/main/java/io/micronaut/oraclecloud/core/OracleCloudCoreFactory.java
- `M` oraclecloud-common/src/main/java/io/micronaut/oraclecloud/core/ServiceOracleCloudClientConfigurationProperties.java
- `M` oraclecloud-common/src/main/java/io/micronaut/oraclecloud/core/TenancyIdProvider.java
- `M` oraclecloud-common/src/main/java/io/micronaut/oraclecloud/core/sdk/AbstractSdkClientFactory.java
- `M` oraclecloud-function-http/src/main/java/io/micronaut/oraclecloud/function/http/FnBinderRegistry.java
- `M` oraclecloud-function-http/src/main/java/io/micronaut/oraclecloud/function/http/FnBodyBinder.java
- `M` oraclecloud-function-http/src/main/java/io/micronaut/oraclecloud/function/http/FnMultiValueMap.java
- `M` oraclecloud-function-http/src/main/java/io/micronaut/oraclecloud/function/http/FnServletRequest.java
- `M` oraclecloud-function-http/src/main/java/io/micronaut/oraclecloud/function/http/FnServletResponse.java
- `M` oraclecloud-function-http/src/main/java/io/micronaut/oraclecloud/function/http/HttpFunction.java
- `M` oraclecloud-function/src/main/java/io/micronaut/oraclecloud/function/OciFunction.java
- `A` oraclecloud-function/src/main/java/io/micronaut/oraclecloud/function/SerdeCoercion.java
- `M` oraclecloud-function/src/main/java/io/micronaut/oraclecloud/function/nativeimage/OciFunctionFeature.java
- `M` oraclecloud-httpclient-apache-http-core/src/main/java/io/micronaut/oraclecloud/httpclient/apache/core/ApacheCoreClientConfiguration.java
- `M` oraclecloud-httpclient-apache-http-core/src/main/java/io/micronaut/oraclecloud/httpclient/apache/core/ApacheCoreHttpClient.java
- `M` oraclecloud-httpclient-apache-http-core/src/main/java/io/micronaut/oraclecloud/httpclient/apache/core/ApacheCoreHttpProvider.java
- `M` oraclecloud-httpclient-apache-http-core/src/main/java/io/micronaut/oraclecloud/httpclient/apache/core/ApacheCoreSerializer.java
- `M` oraclecloud-httpclient-apache-http-core/src/main/java/io/micronaut/oraclecloud/httpclient/apache/core/JacksonSerializer.java
- `M` oraclecloud-httpclient-apache-http-core/src/main/java/io/micronaut/oraclecloud/httpclient/apache/core/SerdeSerializer.java
- `A` oraclecloud-httpclient-apache-http-core/src/main/java/io/micronaut/oraclecloud/httpclient/apache/core/serde/DefaultOciSerdeConfiguration.java
- `A` oraclecloud-httpclient-apache-http-core/src/main/java/io/micronaut/oraclecloud/httpclient/apache/core/serde/DefaultOciSerializationConfiguration.java
- `M` oraclecloud-httpclient-apache-http-core/src/main/java/io/micronaut/oraclecloud/httpclient/apache/core/serde/OciSerdeConfiguration.java
- `M` oraclecloud-httpclient-apache-http-core/src/main/java/io/micronaut/oraclecloud/httpclient/apache/core/serde/OciSerializationConfiguration.java
- `M` oraclecloud-httpclient-apache-http-core/src/main/java/io/micronaut/oraclecloud/httpclient/apache/core/serde/serializers/EncryptionHeaderDeserializer.java
- `M` oraclecloud-httpclient-apache-http-core/src/main/java/io/micronaut/oraclecloud/httpclient/apache/core/serde/serializers/ErrorCodeAndMessageDeserializer.java
- `M` oraclecloud-httpclient-apache-http-core/src/main/java/io/micronaut/oraclecloud/httpclient/apache/core/serde/serializers/SessionTokenDeserializer.java
- `M` oraclecloud-httpclient-apache-http-core/src/main/java/io/micronaut/oraclecloud/httpclient/apache/core/serde/serializers/SessionTokenRequestSerializer.java
- `M` oraclecloud-httpclient-netty/src/main/java/io/micronaut/oraclecloud/httpclient/netty/HeaderMap.java
- `M` oraclecloud-httpclient-netty/src/main/java/io/micronaut/oraclecloud/httpclient/netty/ManagedNettyHttpProvider.java
- `M` oraclecloud-httpclient-netty/src/main/java/io/micronaut/oraclecloud/httpclient/netty/MicronautHeaderMap.java
- `M` oraclecloud-httpclient-netty/src/main/java/io/micronaut/oraclecloud/httpclient/netty/MicronautHttpRequest.java
- `M` oraclecloud-httpclient-netty/src/main/java/io/micronaut/oraclecloud/httpclient/netty/NettyHttpClient.java
- `M` oraclecloud-httpclient-netty/src/main/java/io/micronaut/oraclecloud/httpclient/netty/NettyHttpClientBuilder.java
- `M` oraclecloud-httpclient-netty/src/main/java/io/micronaut/oraclecloud/httpclient/netty/NettyHttpProvider.java
- `M` oraclecloud-httpclient-netty/src/main/java/io/micronaut/oraclecloud/httpclient/netty/OciNettyClientFilter.java
- `M` oraclecloud-httpclient-netty/src/main/java/io/micronaut/oraclecloud/httpclient/netty/StreamReadingHandler.java
- `A` oraclecloud-httpclient-netty/src/main/java/io/micronaut/oraclecloud/serde/DefaultOciSerdeConfiguration.java
- `A` oraclecloud-httpclient-netty/src/main/java/io/micronaut/oraclecloud/serde/DefaultOciSerializationConfiguration.java
- `M` oraclecloud-httpclient-netty/src/main/java/io/micronaut/oraclecloud/serde/OciSdkMicronautSerializer.java
- `M` oraclecloud-httpclient-netty/src/main/java/io/micronaut/oraclecloud/serde/OciSerdeConfiguration.java
- `M` oraclecloud-httpclient-netty/src/main/java/io/micronaut/oraclecloud/serde/OciSerializationConfiguration.java
- `M` oraclecloud-httpclient-netty/src/main/java/io/micronaut/oraclecloud/serde/serializers/EncryptionHeaderDeserializer.java
- `M` oraclecloud-httpclient-netty/src/main/java/io/micronaut/oraclecloud/serde/serializers/ErrorCodeAndMessageDeserializer.java
- `M` oraclecloud-httpclient-netty/src/main/java/io/micronaut/oraclecloud/serde/serializers/SessionTokenDeserializer.java
- `M` oraclecloud-httpclient-netty/src/main/java/io/micronaut/oraclecloud/serde/serializers/SessionTokenRequestSerializer.java
- `M` oraclecloud-logging/src/main/java/io/micronaut/oraclecloud/logging/OracleCloudAppender.java
- `M` oraclecloud-logging/src/main/java/io/micronaut/oraclecloud/logging/OracleCloudLoggingClient.java
- `M` oraclecloud-micrometer/src/main/java/io/micronaut/oraclecloud/monitoring/MonitoringIngestionClient.java
- `M` oraclecloud-micrometer/src/main/java/io/micronaut/oraclecloud/monitoring/micrometer/AbstractOracleCloudMeterRegistry.java
- `M` oraclecloud-micrometer/src/main/java/io/micronaut/oraclecloud/monitoring/micrometer/OracleCloudMeterRegistry.java
- `M` oraclecloud-micrometer/src/main/java/io/micronaut/oraclecloud/monitoring/micrometer/OracleCloudMetricsNamingConvention.java
- `M` oraclecloud-micrometer/src/main/java/io/micronaut/oraclecloud/monitoring/micrometer/OracleCloudRawMeterRegistry.java
- `M` oraclecloud-micrometer/src/main/java/io/micronaut/oraclecloud/monitoring/sdk/SdkMetricsNettyClientFilter.java
- `M` oraclecloud-oke-kubernetes-client/src/main/java/io/micronaut/oraclecloud/oke/kubernetes/client/OkeKubeConfigLoader.java
- `M` oraclecloud-oke-kubernetes-client/src/main/java/io/micronaut/oraclecloud/oke/kubernetes/client/OkeKubernetesClientConfig.java
- `M` oraclecloud-oke-kubernetes-client/src/main/java/io/micronaut/oraclecloud/oke/kubernetes/client/OkeKubernetesCredentialLoader.java
- `M` oraclecloud-oke-workload-identity/src/main/java/io/micronaut/oraclecloud/oke/workload/identity/OkeWorkloadIdentityConfiguration.java
- `M` oraclecloud-oke-workload-identity/src/main/java/io/micronaut/oraclecloud/oke/workload/identity/OkeWorkloadIdentityFactory.java
- `M` oraclecloud-oke-workload-identity/src/main/java/io/micronaut/oraclecloud/serde/serializers/TokenDeserializer.java
- `M` oraclecloud-sdk-processor/src/main/java/io/micronaut/oraclecloud/clients/processor/OracleCloudSdkProcessor.java
- `M` oraclecloud-serde-internal-processor/src/main/java/io/micronaut/oraclecloud/httpclient/netty/visitor/OciSdkModelSerdeVisitor.java
- `M` oraclecloud-serde-processor/src/main/java/io/micronaut/oraclecloud/sdk/processor/SdkImportVisitor.java
- `M` oraclecloud-vault/src/main/java/io/micronaut/oraclecloud/discovery/vault/OracleCloudVaultConfiguration.java
- `M` oraclecloud-vault/src/main/java/io/micronaut/oraclecloud/discovery/vault/OracleCloudVaultConfigurationClient.java
- `A` oraclecloud-vault/src/main/java/io/micronaut/oraclecloud/discovery/vault/OracleCloudVaultImportConfiguration.java
- `A` oraclecloud-vault/src/main/java/io/micronaut/oraclecloud/discovery/vault/OracleCloudVaultImportConfigurationBinder.java
- `A` oraclecloud-vault/src/main/java/io/micronaut/oraclecloud/discovery/vault/OracleCloudVaultImporterContextFactory.java
- `A` oraclecloud-vault/src/main/java/io/micronaut/oraclecloud/discovery/vault/OracleCloudVaultLegacyDeprecationLogger.java
- `A` oraclecloud-vault/src/main/java/io/micronaut/oraclecloud/discovery/vault/OracleCloudVaultPropertySourceImporter.java
- `A` oraclecloud-vault/src/main/java/io/micronaut/oraclecloud/discovery/vault/OracleCloudVaultPropertySourceLoader.java
- `A` oraclecloud-vault/src/main/resources/META-INF/services/io.micronaut.context.env.PropertySourceImporter

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` oraclecloud-atp-hikari-test/src/test/groovy/io/micronaut/oraclecloud/atp/jdbc/hikari/HikariPoolConfigurationListenerSpec.groovy
- `A` oraclecloud-atp/src/test/java/io/micronaut/oraclecloud/atp/jdbc/OracleWalletArchiveProviderTest.java
- `M` oraclecloud-certificates/src/test/groovy/io/micronaut/oraclecloud/certificates/OracleCloudCertificateMTLSSpec.groovy
- `M` oraclecloud-function-http-test/src/main/java/io/micronaut/oraclecloud/function/http/test/FnHttpTest.java
- `M` oraclecloud-function-http-test/src/main/java/io/micronaut/oraclecloud/function/http/test/HttpHandlerApplicationContextProvider.java
- `A` oraclecloud-function-http/src/test/groovy/io/micronaut/oraclecloud/function/http/FnServletAdaptersSpec.groovy
- `M` oraclecloud-function-http/src/test/groovy/io/micronaut/oraclecloud/function/http/HttpFunctionBufferingSpec.groovy
- `M` oraclecloud-function-http/src/test/java/io/micronaut/oraclecloud/function/http/ParametersController.java
- `M` oraclecloud-function-http/src/test/java/io/micronaut/oraclecloud/function/http/Person.java
- `M` oraclecloud-function/src/test/java/io/micronaut/oraclecloud/function/mock/MockTenancyIdProvider.java
- `M` oraclecloud-httpclient-netty/src/test/groovy/io/micronaut/oraclecloud/client/OciMonitoringSpec.groovy
- `M` oraclecloud-httpclient-netty/src/test/groovy/io/micronaut/oraclecloud/serde/NoJacksonOnClasspath.groovy
- `M` oraclecloud-httpclient-netty/src/test/groovy/io/micronaut/oraclecloud/serde/model/BaseModel.java
- `M` oraclecloud-httpclient-netty/src/test/groovy/io/micronaut/oraclecloud/serde/model/ComplexModel.java
- `M` oraclecloud-httpclient-netty/src/test/java/io/micronaut/oraclecloud/httpclient/netty/HeaderMapTest.java
- `M` oraclecloud-httpclient-netty/src/test/java/io/micronaut/oraclecloud/httpclient/netty/LargeTransferTest.java
- `M` oraclecloud-httpclient-netty/src/test/java/io/micronaut/oraclecloud/httpclient/netty/ManagedPropertyTest.java
- `M` oraclecloud-httpclient-netty/src/test/java/io/micronaut/oraclecloud/httpclient/netty/MockTenancyIdProvider.java
- `M` oraclecloud-httpclient-netty/src/test/java/io/micronaut/oraclecloud/httpclient/netty/StreamReadingHandlerTest.java
- `M` oraclecloud-logging/src/test/groovy/io/micronaut/oraclecloud/logging/OracleCloudLoggingAppenderSpec.groovy
- `M` oraclecloud-logging/src/test/groovy/io/micronaut/oraclecloud/logging/OracleCloudLoggingSpec.groovy
- `M` oraclecloud-sdk/src/test/java/io/micronaut/oraclecloud/database/DatabaseFactoryTest.java
- `M` oraclecloud-sdk/src/test/java/io/micronaut/oraclecloud/mock/MockTenancyIdProvider.java
- `A` oraclecloud-vault/src/test/groovy/io/micronaut/oraclecloud/discovery/vault/MockAuthenticationDetailsProvider.groovy
- `A` oraclecloud-vault/src/test/groovy/io/micronaut/oraclecloud/discovery/vault/MockTenancyIdProvider.groovy
- `A` oraclecloud-vault/src/test/groovy/io/micronaut/oraclecloud/discovery/vault/OracleCloudVaultConfigurationClientDeprecationSpec.groovy
- `A` oraclecloud-vault/src/test/groovy/io/micronaut/oraclecloud/discovery/vault/OracleCloudVaultConfigurationClientSpecCharacterization.groovy
- `A` oraclecloud-vault/src/test/groovy/io/micronaut/oraclecloud/discovery/vault/OracleCloudVaultConfigurationClientWarningSpec.groovy
- `M` oraclecloud-vault/src/test/groovy/io/micronaut/oraclecloud/discovery/vault/OracleCloudVaultConfigurationSpec.groovy
- `A` oraclecloud-vault/src/test/groovy/io/micronaut/oraclecloud/discovery/vault/OracleCloudVaultImporterParitySpec.groovy
- `A` oraclecloud-vault/src/test/groovy/io/micronaut/oraclecloud/discovery/vault/OracleCloudVaultPropertySourceImporterLifecycleSpec.groovy
- `A` oraclecloud-vault/src/test/groovy/io/micronaut/oraclecloud/discovery/vault/OracleCloudVaultPropertySourceImporterLiveSpec.groovy
- `A` oraclecloud-vault/src/test/groovy/io/micronaut/oraclecloud/discovery/vault/OracleCloudVaultPropertySourceImporterPositiveSpec.groovy
- `A` oraclecloud-vault/src/test/groovy/io/micronaut/oraclecloud/discovery/vault/OracleCloudVaultPropertySourceImporterSpec.groovy
- `M` oraclecloud-vault/src/test/resources/logback.xml
- `M` test-suite-graal-logging/src/main/java/example/CustomLogging.java
- `M` test-suite-http-server-tck-oraclecloud-function-http/src/test/java/io/micronaut/http/server/tck/oraclecloud/function/OracleCloudFunctionServerTestSuite.java
- `M` test-suite-http-server-tck-oraclecloud-function-http/src/test/java/io/micronaut/http/server/tck/oraclecloud/function/OracleCloudFunctionServerUnderTest.java
- `M` test-suite-http-server-tck-oraclecloud-function-http/src/test/java/io/micronaut/http/server/tck/oraclecloud/function/adapter/FnHttpGatewayContextAdapter.java
- `M` test-suite-http-server-tck-oraclecloud-function-http/src/test/java/io/micronaut/http/server/tck/oraclecloud/function/adapter/FnInputEventFactory.java
- `M` test-suite-http-server-tck-oraclecloud-function-http/src/test/java/io/micronaut/http/server/tck/oraclecloud/function/adapter/FnOutputEventAdapter.java
- `M` test-suite-java/src/test/java/example/HikariPoolAtpTest.java
- `M` test-suite-java/src/test/java/example/MicrometerTest.java
- `A` test-suite-java/src/test/java/example/VaultImportTest.java
- `M` test-suite-java/src/test/java/example/VaultSerializationTest.java
- `M` test-suite-java/src/test/java/example/VaultTest.java

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

