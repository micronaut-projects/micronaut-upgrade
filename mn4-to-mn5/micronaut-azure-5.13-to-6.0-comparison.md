 Compared micronaut-azure as mn4 -> mn5.

  Scope

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-azure, branch 5.13.x, SHA 0966f1b1e7ba
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-azure, branch 6.0.x, SHA 5f2e74c3296d
  - Same remote, both clean: git@github.com:micronaut-projects/micronaut-azure.git
  - Report: /private/tmp/micronaut-azure-5.13-to-6.0-comparison.md

  Key Findings

  - Release line moves from 5.13.1-SNAPSHOT to 6.0.1-SNAPSHOT.
  - Major build/runtime baseline update: Micronaut 4.10.4 -> 5.0.0, Micronaut Platform 4.9.4 -> 5.0.0-RC1,
    Gradle 8.14.3 -> 9.5.1, Java SDKMAN default added as 25.0.1-graal.
  - Azure dependency updates include Azure SDK BOM 1.3.0 -> 1.3.6, Azure Cosmos 4.74.0 -> 4.80.0, and Azure
    Functions Java library 3.2.0 -> 3.3.0.
  - New Azure Key Vault config import support was added through micronaut.config.import=azure-key-
    vault://..., with importer/settings/materializer classes, service registration, docs, and focused tests.
  - Legacy bootstrap/config-client Azure Key Vault support remains, but is now deprecated and bypasses itself
    when the new config import path is configured.
  - Azure Function HTTP moved off MediaTypeCodec toward Micronaut 5 message body APIs, including updated
    request serialization, binder registry changes, and adjusted JSON error expectations.
  - Azure Function HTTP test support now skips Content-Length and Transfer-Encoding headers managed by
    HttpExchange; CORS expectations changed so Access-Control-Allow-Credentials is absent/null in the covered
    cases.
  - Docs examples were moved from test sources to main sources, with docs snippets updated to use
    source="main".
  - Added osv-scanner.toml with an ignore for GHSA-rcgg-9c38-7xpx.

  Diff size: 116 files changed, 5319 insertions(+), 327 deletions(-).

  I did not run tests; this was a folder comparison and targeted source/build-diff review only.

# Release Note Comparison

Generated: 2026-05-19 14:36 UTC
Comparison: `5.13.x` -> `6.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-azure` | `5.13.x` | `0966f1b1e7ba` | `git@github.com:micronaut-projects/micronaut-azure.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-azure` | `6.0.x` | `5f2e74c3296d` | `git@github.com:micronaut-projects/micronaut-azure.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-azure`
- Commit candidates found: 118
- File changes listed: 116
- Version values listed: 48
- File status counts: A=43, M=67, R=6

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `5.13.1-SNAPSHOT` | `6.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.boms-azure-sdk` | `com.azure:azure-sdk-bom:1.3.0` | `com.azure:azure-sdk-bom:1.3.6` | `changed` |
| `gradle/libs.versions.toml` | `libraries.commons-codec` | `commons-codec:commons-codec:1.19.0` | `commons-codec:commons-codec:1.22.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.gradle-micronaut` | `io.micronaut.gradle:micronaut-gradle-plugin:4.5.5` | `io.micronaut.gradle:micronaut-gradle-plugin:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.groovy-all` | `org.apache.groovy:groovy-all:4.0.28` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.jackson-core` | `not present` | `com.fasterxml.jackson.core:jackson-core:2.18.6` | `added` |
| `gradle/libs.versions.toml` | `libraries.jakarta-inject-api` | `jakarta.inject:jakarta.inject-api:2.0.1` | `jakarta.inject:jakarta.inject-api:2.0.1` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.json-smart` | `net.minidev:json-smart:2.6.0` | `net.minidev:json-smart:2.6.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.kotlin-reflect` | `org.jetbrains.kotlin:kotlin-reflect:2.1.21` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.kotlin-stdlib-jdk8` | `org.jetbrains.kotlin:kotlin-stdlib-jdk8:2.1.21` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.managed-azure-cosmos` | `com.azure:azure-cosmos:4.74.0` | `com.azure:azure-cosmos:4.80.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-azure-functions-java-library` | `com.microsoft.azure.functions:azure-functions-java-library:3.2.0` | `com.microsoft.azure.functions:azure-functions-java-library:3.3.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-opentelemetry-autoconfigure` | `com.azure:azure-monitor-opentelemetry-autoconfigure:1.4.0` | `com.azure:azure-monitor-opentelemetry-autoconfigure:1.4.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.micronaut-reactor` | `io.micronaut.reactor:micronaut-reactor-bom:3.9.0` | `io.micronaut.reactor:micronaut-reactor-bom:4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.15.5` | `io.micronaut.serde:micronaut-serde-bom:3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-servlet` | `io.micronaut.servlet:micronaut-servlet-bom:5.5.1` | `io.micronaut.servlet:micronaut-servlet-bom:6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-resources` | `io.micronaut.testresources:micronaut-test-resources-bom:2.10.1` | `io.micronaut.testresources:micronaut-test-resources-bom:4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-tracing` | `io.micronaut.tracing:micronaut-tracing-bom:7.2.0` | `io.micronaut.tracing:micronaut-tracing-bom:8.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-validation` | `io.micronaut.validation:micronaut-validation-bom:4.11.0` | `io.micronaut.validation:micronaut-validation-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.system-lambda` | `com.github.stefanbirkner:system-lambda:1.2.1` | `com.github.stefanbirkner:system-lambda:1.2.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.azurefunctions-plugin` | `1.16.1` | `1.16.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.commons-codec` | `1.19.0` | `1.22.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.28` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.jackson-core` | `not present` | `2.18.6` | `added` |
| `gradle/libs.versions.toml` | `versions.jakarta-inject-api` | `2.0.1` | `2.0.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.json-smart` | `2.6.0` | `2.6.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.kotlin` | `2.1.21` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.logback-json-classic` | `0.1.5` | `0.1.5` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-azure-cosmos` | `4.74.0` | `4.80.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-azure-functions-java-library` | `3.2.0` | `3.3.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-azure-sdk` | `1.3.0` | `1.3.6` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-opentelemetry-autoconfigure` | `1.4.0` | `1.4.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.4` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `2.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.5.5` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.1` | `2.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-platform` | `4.9.4` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-reactor` | `3.9.0` | `4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.15.5` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-servlet` | `5.5.1` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.9.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test-resources` | `2.10.1` | `4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-tracing` | `7.2.0` | `8.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.11.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.system-lambda` | `1.2.1` | `1.2.1` | `unchanged` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `a6489f92b2cd` Remove usage of MediaTypeCodec (#944) (Denis Stepanov, 2026-04-20)
- `a236e4f6213f` remove spock (Sergio del Amo, 2025-12-10)
- `e65a970d2c14` remove micronaut-test (Sergio del Amo, 2025-12-10)
- `d9d7d11e8c4d` remove groovy-all (Sergio del Amo, 2025-12-10)
- `abaa5378c4ce` remove micronaut-docs included by Micronaut Build plugin (Sergio del Amo, 2025-12-10)
- `338d2419e5b4` remove groovy include by Micronaut Build Gradle Plugin (Sergio del Amo, 2025-12-10)

### Features

- `4c4519c56837` Add Azure Key Vault config import support (#945) (Graeme Rocher, 2026-04-17)
- `45edd18a8d4d` add @JsonProperty annotation for jackson 3 (Sergio del Amo, 2026-02-19)

### Fixes

- `edb1a61d6da2` fix(deps): update azure-sdk-for-java monorepo (#901) (renovate[bot], 2026-02-19)
- `3882de0fb5f8` fix(deps): update dependency com.microsoft.azure.functions:azure-functions-java-library to v3.2.3 (#930) (renovate[bot], 2026-02-19)
- `416ac9d15a45` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.2 (#931) (renovate[bot], 2026-02-12)
- `89247a798e66` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m10 (#918) (renovate[bot], 2026-02-12)
- `1b54c4336f8f` fix(deps): update dependency io.micronaut.platform:micronaut-platform to v4.10.8 (#919) (renovate[bot], 2026-02-12)
- `86d881c8b779` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m2 (#926) (renovate[bot], 2026-02-12)
- `94d44e29bd50` fix(deps): update dependency io.micronaut.servlet:micronaut-servlet-bom to v5.6.0 (#906) (renovate[bot], 2025-12-10)
- `65b4250a82e3` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.12.0 (#907) (renovate[bot], 2025-12-10)
- `281ca072bf7e` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#908) (renovate[bot], 2025-12-10)
- `c98ffc381c4a` fix(deps): update kotlin monorepo to v2.2.21 (#909) (renovate[bot], 2025-12-10)
- `377dd760e16d` fix(deps): update dependency org.apache.groovy:groovy-all to v5 (#916) (renovate[bot], 2025-12-10)
- `022ed470c5f9` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#905) (renovate[bot], 2025-12-10)
- `18480ea1add2` fix(deps): update dependency io.micronaut.platform:micronaut-platform to v4.10.3 (#904) (renovate[bot], 2025-12-10)
- `4fb63259a9f7` fix(deps): update dependency com.microsoft.azure.functions:azure-functions-java-library to v3.2.2 (#892) (renovate[bot], 2025-11-03)
- `7d75e0a3e71f` fix(deps): update dependency io.micronaut.reactor:micronaut-reactor-bom to v3.9.1 (#895) (renovate[bot], 2025-11-03)
- `29eceb0962b5` fix(deps): update dependency org.apache.groovy:groovy-all to v4.0.29 (#896) (renovate[bot], 2025-11-03)
- `70f66d5b0aa8` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.8 (#894) (renovate[bot], 2025-11-03)
- `70a8998c6693` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.6 (#888) (renovate[bot], 2025-10-17)

### Security

- `385bdbdbfbbb` security ignore GHSA-rcgg-9c38-7xpx" (Sergio del Amo, 2026-05-18)

### Dependency Updates

- `5dc8d16f0563` chore: Bump version to 6.0.1-SNAPSHOT (micronaut-build, 2026-05-18)
- `26434ed88f9b` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2026-05-08)
- `fab2ff169e6b` Update dependency io.micronaut.validation:micronaut-validation-bom to v5.0.0-RC1 - abandoned (#962) (renovate[bot], 2026-05-08)
- `bb7d913c0ea3` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2026-05-05)
- `d3dead06592d` Update dependency com.azure:azure-cosmos to v4.80.0 (#958) (renovate[bot], 2026-05-05)
- `828dd328a45d` Update Micronaut dependencies (#957) (renovate[bot], 2026-05-05)
- `b2423c3437e9` Update dependency commons-codec:commons-codec to v1.22.0 (#952) (renovate[bot], 2026-05-01)
- `7badd48926d7` Update Micronaut dependencies (#951) (renovate[bot], 2026-05-01)
- `4e6b4e6e527a` Update dependency com.microsoft.azure.functions:azure-functions-java-library to v3.3.0 (#954) (renovate[bot], 2026-05-01)
- `008d8949f9bd` Update dependency commons-codec:commons-codec to v1.21.0 (#949) (renovate[bot], 2026-04-21)
- `17040a3a01fd` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2026-04-20)
- `b09026af0e74` Update dependency com.microsoft.azure.functions:azure-functions-java-library to v3.2.4 (#940) (renovate[bot], 2026-04-20)
- `ea024a2b6a63` Update dependency io.micronaut.servlet:micronaut-servlet-bom to v6.0.0-M3 (#932) (renovate[bot], 2026-04-20)
- `c6aad98e6800` Update dependency io.micronaut.platform:micronaut-platform to v4.10.12 (#934) (renovate[bot], 2026-04-20)
- `a65eb71d9177` chore(deps): update gradle to v9.4.1 (#938) (renovate[bot], 2026-04-20)
- `4d6e0f10113f` Update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-M7 (#943) (renovate[bot], 2026-04-20)
- `fe883d252be3` Update dependency io.micronaut.reactor:micronaut-reactor-bom to v4.0.0-M2 (#947) (renovate[bot], 2026-04-20)
- `a56da23994ca` Update dependency io.micronaut.validation:micronaut-validation-bom to v5.0.0-M2 (#948) (renovate[bot], 2026-04-20)
- `e9f842d6fc04` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2026-02-19)
- `63cda9a65421` chore(deps): update actions/cache action to v5 (#922) (renovate[bot], 2026-02-12)
- `45f77b51f1fd` chore(deps): update gradle to v9.3.1 (#927) (renovate[bot], 2026-02-12)
- `a4dd9981d229` chore(deps): update graalvm/setup-graalvm action to v1.4.5 (#924) (renovate[bot], 2026-02-12)
- `c7b55f15b887` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m16 (#920) (renovate[bot], 2026-02-12)
- `c4568415e5e3` chore(deps): update graalvm/setup-graalvm action to v1.4.4 (#910) (renovate[bot], 2025-12-10)
- `e025994fb50a` chore(deps): update actions/checkout action to v6.0.1 (#911) (renovate[bot], 2025-12-10)
- `d39a6e0e18fa` chore(deps): update github artifact actions (#914) (renovate[bot], 2025-12-10)
- `3500c9e58cf1` chore(deps): update mikepenz/action-junit-report action to v6 (#915) (renovate[bot], 2025-12-10)
- `e724b966748d` chore(deps): update softprops/action-gh-release action to v2.5.0 (#900) (renovate[bot], 2025-12-10)
- `1fb0941d67db` chore(deps): update gradle to v9.2.1 (#899) (renovate[bot], 2025-12-10)
- `f28c3ab04c01` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#897) (renovate[bot], 2025-12-10)
- `6e85dee57759` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m8 (#890) (renovate[bot], 2025-11-03)
- `a1be30f25484` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#891) (renovate[bot], 2025-11-03)

### Internal

- `0cce6f5bb74a` Build: Update to micronaut 5 (#928) (issam liqali, 2026-02-19)

### Review Candidates

- `5f2e74c3296d` update versions (Sergio del Amo, 2026-05-19)
- `99f85a8296c9` Update common files (#967) (micronaut-build, 2026-05-19)
- `f5b6d38b343f` [skip ci] Release v6.0.0 (micronaut-build, 2026-05-18)
- `064ed634b12a` micronaut-servlet = "6.0.0" (Sergio del Amo, 2026-05-14)
- `a931d9dfe365` Update versions (Sergio del Amo, 2026-05-14)
- `27d9474124f5` micronaut-platform = "5.0.0-RC1" (Sergio del Amo, 2026-05-13)
- `5aa1ea682773` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `90969c61728d` Update Gradle to v9.5.1 (#965) (renovate[bot], 2026-05-13)
- `d6c60a5156fd` Update common files (#964) (micronaut-build, 2026-05-09)
- `a26f66da9b84` [skip ci] Release v6.0.0-RC2 (micronaut-build, 2026-05-08)
- `68d626941517` platform m3 (Sergio del Amo, 2026-05-08)
- `e59f21ef70c6` git ignore .kotlin (Sergio del Amo, 2026-05-08)
- `c5627f99224b` update versions (Sergio del Amo, 2026-05-08)
- `ff02c1b563a1` Update common files (#963) (micronaut-build, 2026-05-08)
- `0471c9c4e968` [skip ci] Release v6.0.0-RC1 (micronaut-build, 2026-05-05)
- `758917a66181` Update Gradle to v9.5.0 (#959) (renovate[bot], 2026-05-05)
- `c4937aee7d0e` Update common files (#956) (micronaut-build, 2026-05-05)
- `aa48ba6f6b7f` [azure] Update common files for branch 6.0.x (#953) (micronaut-build, 2026-05-04)
- `256bf2b237b6` Update Gradle to v9.5.0 (#955) (renovate[bot], 2026-05-01)
- `f548c2a8ffbc` Update common files (#950) (micronaut-build, 2026-04-26)
- `7e34f45ad85a` [skip ci] Release v6.0.0-M2 (micronaut-build, 2026-04-20)
- `26ec28bfcf7a` ACCESS_CONTROL_ALLOW_CREDENTIALS is header null (Sergio del Amo, 2026-04-20)
- `b60217e643fd` fix constructor (Sergio del Amo, 2026-04-20)
- `f7499b14c1f7` micronaut-platform = "5.0.0-M1" (Sergio del Amo, 2026-04-20)
- `d66ff94d5127` test-resources 4.0.0-M1 (Sergio del Amo, 2026-04-20)
- `35357ab992cd` core 5.0.0-M23 (Sergio del Amo, 2026-04-20)
- `ba4c77ec350d` Update GitHub Artifact Actions (#936) (renovate[bot], 2026-04-20)
- `d1dd26a13ef7` Update azure-sdk-for-java monorepo (#939) (renovate[bot], 2026-04-20)
- `fdb7d0799a15` Update common files (#937) (micronaut-build, 2026-04-20)
- `429bf04385a4` Update softprops/action-gh-release action to v2.6.2 (#941) (renovate[bot], 2026-04-20)
- `07c0f1297ad7` [skip ci] Release v6.0.0-M1 (micronaut-build, 2026-02-19)
- `0f6b15e75e92` use test resources bom from micronaut-test (Sergio del Amo, 2026-02-19)
- `77c6a6097222` artifactId testcontainers-azure (Sergio del Amo, 2026-02-19)
- `4fea74d7c8fe` micronaut = "5.0.0-M12" (Sergio del Amo, 2026-02-19)
- `4e35ad42d6ac` TestFramework.JUNIT6 (Sergio del Amo, 2026-02-19)
- `1fc8212916d1` JavaVersion.toVersion("25") (Sergio del Amo, 2026-02-19)
- `6bd287d46fc8` io.micronaut.build.shared.settings 8.0.0-M17 (Sergio del Amo, 2026-02-19)
- `b08d5d203ecc` micronaut-logging = "2.0.0-M2" (Sergio del Amo, 2026-02-19)
- `4f0a54719c8e` micronaut-tracing = "8.0.0-M1" (Sergio del Amo, 2026-02-19)
- `ccddaac4fc0e` micronaut-test-resources = "3.0.0-M6" (Sergio del Amo, 2026-02-19)
- `167ac7446d2a` micronaut-logging = "2.0.0-M1" (Sergio del Amo, 2026-02-19)
- `e3df3c7e353c` micronaut = "5.0.0-M11" (Sergio del Amo, 2026-02-19)
- `ed5c859577bd` Merge branch '5.13.x' into 6.0.x (Sergio del Amo, 2026-02-19)
- `78972b3f1037` Update common files (#917) (micronaut-build, 2026-02-12)
- `9a14d61fb2fa` micronaut-azure-sdk as micronautBuild descriptor (Sergio del Amo, 2025-12-10)
- `b23f5f19f674` micronaut-validation = "5.0.0-M1" (Sergio del Amo, 2025-12-10)
- `e38e9ca94123` micronaut-servlet = "6.0.0-M1" (Sergio del Amo, 2025-12-10)
- `41f6900949bf` micronaut-reactor = "4.0.0-M1" (Sergio del Amo, 2025-12-10)
- `e4ce09c0b1cd` micronaut-serde = "3.0.0-M1" (Sergio del Amo, 2025-12-10)
- `8d60ea2ae4ee` micronaut = "5.0.0-M2" (Sergio del Amo, 2025-12-10)
- `0bb38a85f09f` Update common files (#898) (micronaut-build, 2025-12-10)
- `c99364ef1d91` Replace Micronaut nullability annotations with JSpecify nullability annotations (#913) (Copilot, 2025-12-01)
- `c4296fb841f2` Micronaut 5 compatibility (#893) (issam liqali, 2025-11-03)
- `62bbc2394960` Update common files (#889) (micronaut-build, 2025-11-03)
- `5a7701b17a5b` Update common files (#887) (micronaut-build, 2025-10-17)
- `5f4b1df21d02` Micronaut Gradle Build Plugin 8.0.0-M4 (Sergio del Amo, 2025-10-15)
- `c7a4bcfd2b05` gradle 9.1 (Sergio del Amo, 2025-10-15)
- `798f1a7267aa` projectVersion=6.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-10-15)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` azure-cosmos/build.gradle
- `M` azure-tracing/build.gradle.kts
- `M` buildSrc/build.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.azure-base.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.azure-module.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.http-server-tck-module.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.http-test-module.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` settings.gradle
- `M` test-suite-azure-function-http-context-path/build.gradle.kts

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
- `M` doc-examples/example-groovy/build.gradle.kts
- `R100` doc-examples/example-groovy/src/main/groovy/example/BlobFunction.groovy
- `R100` doc-examples/example-groovy/src/main/groovy/example/MyHttpFunction.groovy
- `M` doc-examples/example-java/build.gradle.kts
- `R100` doc-examples/example-java/src/main/java/example/BlobFunction.java
- `R100` doc-examples/example-java/src/main/java/example/MyHttpFunction.java
- `M` doc-examples/example-kotlin/build.gradle.kts
- `R100` doc-examples/example-kotlin/src/main/kotlin/example/BlobFunction.kt
- `R100` doc-examples/example-kotlin/src/main/kotlin/example/MyHttpFunction.kt
- `M` src/main/docs/guide/azureFunction/azureHttpFunctions.adoc
- `M` src/main/docs/guide/azureFunction/simpleAzureFunctions.adoc
- `M` src/main/docs/guide/azureKeyVault.adoc
- `M` src/main/docs/guide/azureKeyVault/distributedConfiguration.adoc
- `M` test-suite-dockerised/build.gradle.kts

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
- `M` azure-cosmos/src/main/java/io/micronaut/azure/cosmos/client/CosmosClientConfiguration.java
- `M` azure-function-http/src/main/java/io/micronaut/azure/function/http/AzureBinderRegistry.java
- `M` azure-function-http/src/main/java/io/micronaut/azure/function/http/AzureFunctionHttpRequest.java
- `M` azure-function-http/src/main/java/io/micronaut/azure/function/http/AzureFunctionHttpResponse.java
- `M` azure-function-http/src/main/java/io/micronaut/azure/function/http/AzureHttpFunction.java
- `M` azure-function-http/src/main/java/io/micronaut/azure/function/http/DefaultHttpRequestMessageBuilder.java
- `M` azure-function-http/src/main/java/io/micronaut/azure/function/http/HttpRequestMessageBuilder.java
- `M` azure-function/src/main/java/io/micronaut/azure/function/AzureFunction.java
- `M` azure-logging/src/main/java/io/micronaut/azure/logging/ClientWrapper.java
- `M` azure-logging/src/main/java/io/micronaut/azure/logging/DefaultClientWrapper.java
- `M` azure-sdk/src/main/java/io/micronaut/azure/condition/EnvironmentCredentialsCondition.java
- `M` azure-sdk/src/main/java/io/micronaut/azure/credentials/AzureCredentialFactory.java
- `M` azure-sdk/src/main/java/io/micronaut/azure/credentials/AzureCredentialsConfiguration.java
- `A` azure-secret-manager/src/main/java/io/micronaut/azure/secretmanager/AzureKeyVaultImportSettings.java
- `A` azure-secret-manager/src/main/java/io/micronaut/azure/secretmanager/AzureKeyVaultLegacyMode.java
- `A` azure-secret-manager/src/main/java/io/micronaut/azure/secretmanager/AzureKeyVaultPropertySourceImporter.java
- `A` azure-secret-manager/src/main/java/io/micronaut/azure/secretmanager/AzureKeyVaultPropertySourceMaterializer.java
- `A` azure-secret-manager/src/main/java/io/micronaut/azure/secretmanager/AzureSecretManagerSupport.java
- `M` azure-secret-manager/src/main/java/io/micronaut/azure/secretmanager/AzureVaultConfigurationClient.java
- `M` azure-secret-manager/src/main/java/io/micronaut/azure/secretmanager/SecretManagerFactory.java
- `A` azure-secret-manager/src/main/resources/META-INF/services/io.micronaut.context.env.PropertySourceImporter
- `M` config/accepted-api-changes.json
- `M` config/checkstyle/checkstyle.xml
- `A` osv-scanner.toml

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `A` azure-cosmos/src/test/resources/logback.xml
- `M` azure-function-http-test/src/main/java/io/micronaut/azure/function/http/test/AzureFunctionHttpHandler.java
- `M` azure-function-http-test/src/test/groovy/io/micronaut/azure/function/http/test/AzureFunctionCorsSpec.groovy
- `M` azure-function-http/src/test/groovy/io/micronaut/azure/function/http/ParameterBindingSpec.groovy
- `M` azure-function-http/src/test/java/io/micronaut/azure/function/http/Person.java
- `M` azure-logging/src/test/groovy/io/micronaut/azure/logging/AzureLoggingSpec.groovy
- `M` azure-sdk/src/test/groovy/io/micronaut/azure/condition/ClientCertificateCredentialsConditionSpec.groovy
- `M` azure-sdk/src/test/java/io/micronaut/azure/BlobServiceFactory.java
- `A` azure-secret-manager/src/test/groovy/io/micronaut/azure/secretmanager/AzureKeyVaultConfigImportSpec.groovy
- `A` azure-secret-manager/src/test/groovy/io/micronaut/azure/secretmanager/AzureKeyVaultImportActivationSpec.groovy
- `A` azure-secret-manager/src/test/groovy/io/micronaut/azure/secretmanager/AzureKeyVaultImportSettingsSpec.groovy
- `A` azure-secret-manager/src/test/groovy/io/micronaut/azure/secretmanager/AzureKeyVaultLegacyModeSpec.groovy
- `A` azure-secret-manager/src/test/groovy/io/micronaut/azure/secretmanager/AzureKeyVaultPropertySourceImporterCoverageSpec.groovy
- `A` azure-secret-manager/src/test/groovy/io/micronaut/azure/secretmanager/AzureKeyVaultPropertySourceImporterSpec.groovy
- `A` azure-secret-manager/src/test/groovy/io/micronaut/azure/secretmanager/AzureKeyVaultPropertySourceMaterializerSpec.groovy
- `A` azure-secret-manager/src/test/groovy/io/micronaut/azure/secretmanager/AzureKeyVaultRefreshSemanticsSpec.groovy
- `M` azure-secret-manager/src/test/groovy/io/micronaut/azure/secretmanager/AzureSecretKeyVaultClientSpec.groovy
- `A` azure-secret-manager/src/test/groovy/io/micronaut/azure/secretmanager/AzureSecretManagerSupportSpec.groovy
- `A` azure-secret-manager/src/test/groovy/io/micronaut/azure/secretmanager/SecretManagerFactorySpec.groovy
- `M` test-suite-http-server-tck-azure-function-http-test/src/test/java/io/micronaut/http/server/tck/azurehttpfunction/tests/AzureFunctionHttpTestHttpServerTestSuite.java
- `M` test-suite-http-server-tck-azure-function-http/src/test/java/io/micronaut/http/server/tck/azurehttpfunction/AzureFunctionHttpServerUnderTest.java
- `M` test-suite-http-server-tck-azure-function-http/src/test/java/io/micronaut/http/server/tck/azurehttpfunction/AzureFunctionHttpServerUnderTestProvider.java
- `M` test-suite-http-server-tck-azure-function-http/src/test/java/io/micronaut/http/server/tck/azurehttpfunction/AzureRequestEventFactory.java
- `M` test-suite-http-server-tck-azure-function-http/src/test/java/io/micronaut/http/server/tck/azurehttpfunction/BodyUtils.java
- `M` test-suite-http-server-tck-azure-function-http/src/test/java/io/micronaut/http/server/tck/azurehttpfunction/HttpResponseMessageAdapter.java
- `M` test-suite-http-server-tck-azure-function-http/src/test/java/io/micronaut/http/server/tck/azurehttpfunction/tests/AzureFunctionHttpHttpServerTestSuite.java

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

