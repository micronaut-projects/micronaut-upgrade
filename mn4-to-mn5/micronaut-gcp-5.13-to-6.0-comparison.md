Compared micronaut-gcp as mn4 -> mn5.

  Scope

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-gcp, branch 5.13.x, SHA 9eede624fec0
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-gcp, branch 6.0.x, SHA 82e0afa99892
  - Same remote, both clean: git@github.com:micronaut-projects/micronaut-gcp.git
  - Report: /private/tmp/micronaut-gcp-5.13-to-6.0-comparison.md

  Key Findings

  - Release line moves from 5.13.2-SNAPSHOT to 6.0.1-SNAPSHOT.
  - Major baseline update: Micronaut 4.10.7 -> 5.0.0, Gradle 8.14.3 -> 9.5.1, Micronaut Gradle plugin 4.5.5
    -> 5.0.0-M1, Java SDKMAN default added as 25.0.1-graal.
  - Google dependency updates include Functions Framework API 1.1.4 -> 2.0.1, function invoker 1.4.1 ->
    2.0.1, Pub/Sub 1.142.0 -> 1.150.1, Secret Manager 2.76.0 -> 2.91.0, GAX 2.70.3 -> 2.79.0, and Google
    Auth 1.39.1 -> 1.46.0.
  - New Google Secret Manager config import support via micronaut.config.import=gcp-secret-manager://...,
    including project/location/version/format/credential options and retry support.
  - Legacy Secret Manager bootstrap/config-client integration remains, but docs now prefer explicit config
    import for new applications.
  - Documented breaking removals: deprecated constructors for GoogleCredentialsFactory, PubSubBodyBinder,
    and PubSubMessageReceiverException.
  - GCP HTTP function support migrated off MediaTypeCodec to Micronaut 5 message body reader/writer APIs.
  - CloudEvents SDK moved 2.5.0 -> 4.0.2; CloudEvent type serde now uses protobuf JsonFormat based serde
    beans instead of the previous large @SerdeImport list.
  - Stackdriver tracing was adapted for newer sender APIs and keeps Stackdriver V2 encoding compatibility.
  - Added osv-scanner.toml ignore for GHSA-rcgg-9c38-7xpx.

  Diff size: 181 files changed, 5673 insertions(+), 1068 deletions(-).

  I did not run tests; this was a folder comparison and targeted source/build-diff review only.


# Release Note Comparison

Generated: 2026-05-19 14:42 UTC
Comparison: `5.13.x` -> `6.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-gcp` | `5.13.x` | `9eede624fec0` | `git@github.com:micronaut-projects/micronaut-gcp.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-gcp` | `6.0.x` | `82e0afa99892` | `git@github.com:micronaut-projects/micronaut-gcp.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-gcp`
- Commit candidates found: 142
- File changes listed: 181
- Version values listed: 66
- File status counts: A=44, D=5, M=132

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `5.13.2-SNAPSHOT` | `6.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.brave-opentracing` | `io.opentracing.brave:brave-opentracing:1.0.1` | `io.opentracing.brave:brave-opentracing:1.0.1` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.brave-propagation-stackdriver` | `io.zipkin.gcp:brave-propagation-stackdriver:2.3.0` | `io.zipkin.gcp:brave-propagation-stackdriver:2.3.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.cloudevents-api` | `io.cloudevents:cloudevents-api:2.5.0` | `io.cloudevents:cloudevents-api:4.0.2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.cloudevents-core` | `io.cloudevents:cloudevents-core:2.5.0` | `io.cloudevents:cloudevents-core:4.0.2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.google-auth-library-credentials` | `com.google.auth:google-auth-library-credentials:1.39.1` | `com.google.auth:google-auth-library-credentials:1.46.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.gradle-micronaut` | `io.micronaut.gradle:micronaut-gradle-plugin:4.5.5` | `io.micronaut.gradle:micronaut-gradle-plugin:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.kotlin-reflect` | `org.jetbrains.kotlin:kotlin-reflect (version.ref=kotlin)` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.kotlin-stdlib-jdk8` | `org.jetbrains.kotlin:kotlin-stdlib-jdk8 (version.ref=kotlin)` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.logback-json-classic` | `ch.qos.logback.contrib:logback-json-classic:0.1.5` | `ch.qos.logback.contrib:logback-json-classic:0.1.5` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-functions-framework-api` | `com.google.cloud.functions:functions-framework-api:1.1.4` | `com.google.cloud.functions:functions-framework-api:2.0.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-google-auth-library-oauth2-http` | `com.google.auth:google-auth-library-oauth2-http:1.39.1` | `com.google.auth:google-auth-library-oauth2-http:1.46.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-google-cloud-core` | `com.google.cloud:google-cloud-core:2.60.3` | `com.google.cloud:google-cloud-core:2.69.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-google-cloud-pubsub` | `com.google.cloud:google-cloud-pubsub:1.142.0` | `com.google.cloud:google-cloud-pubsub:1.150.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-google-cloud-secretmanager` | `com.google.cloud:google-cloud-secretmanager:2.76.0` | `com.google.cloud:google-cloud-secretmanager:2.91.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-google-cloudevent-types` | `com.google.cloud:google-cloudevent-types:0.3.0` | `com.google.cloud:google-cloudevent-types:0.17.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-google-function-invoker` | `com.google.cloud.functions.invoker:java-function-invoker:1.4.1` | `com.google.cloud.functions.invoker:java-function-invoker:2.0.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-discovery-client` | `io.micronaut.discovery:micronaut-discovery-client:4.7.1` | `io.micronaut.discovery:micronaut-discovery-client:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-grpc` | `io.micronaut.grpc:micronaut-grpc-bom:4.12.0` | `io.micronaut.grpc:micronaut-grpc-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-jackson-xml` | `io.micronaut.xml:micronaut-jackson-xml-bom:4.8.0` | `io.micronaut.xml:micronaut-jackson-xml-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-reactor` | `io.micronaut.reactor:micronaut-reactor-bom:3.9.1` | `io.micronaut.reactor:micronaut-reactor-bom:4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-rxjava3` | `io.micronaut.rxjava3:micronaut-rxjava3-bom:3.9.0` | `io.micronaut.rxjava3:micronaut-rxjava3-bom:4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.16.1` | `io.micronaut.serde:micronaut-serde-bom:3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-servlet` | `io.micronaut.servlet:micronaut-servlet-bom:5.6.0` | `io.micronaut.servlet:micronaut-servlet-bom:6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-resources` | `io.micronaut.testresources:micronaut-test-resources-bom:2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-tracing` | `io.micronaut.tracing:micronaut-tracing-bom:7.2.0` | `io.micronaut.tracing:micronaut-tracing-bom:8.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-validation` | `micronaut-validation:4.12.0` | `micronaut-validation:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.system-stubs-core` | `uk.org.webcompere:system-stubs-core:2.1.8` | `uk.org.webcompere:system-stubs-core:2.1.8` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.zipkin-encoder-stackdriver` | `io.zipkin.gcp:zipkin-encoder-stackdriver:2.1.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.zipkin-sender-stackdriver` | `io.zipkin.gcp:zipkin-sender-stackdriver:2.1.1` | `io.zipkin.gcp:zipkin-sender-stackdriver:2.3.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.zipkin-stackdriver-encoder` | `not present` | `io.zipkin.gcp:zipkin-encoder-stackdriver:2.3.1` | `added` |
| `gradle/libs.versions.toml` | `versions.brave-opentracing` | `1.0.1` | `1.0.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.brave-propagation-stackdriver` | `2.3.0` | `2.3.1` | `changed` |
| `gradle/libs.versions.toml` | `versions.cloudevents-api` | `2.5.0` | `4.0.2` | `changed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.logback-json-classic` | `0.1.5` | `0.1.5` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-gax` | `2.70.3` | `2.79.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-google-auth-library-oauth2http` | `1.39.1` | `1.46.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-google-cloud-core` | `2.60.3` | `2.69.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-google-cloud-pubsub` | `1.142.0` | `1.150.1` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-google-cloud-secretmanager` | `2.76.0` | `2.91.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-google-cloudevent-types` | `0.3.0` | `0.17.1` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-google-function-invoker` | `1.4.1` | `2.0.1` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-google-functions-framework-api` | `1.1.4` | `2.0.1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.7` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-discovery` | `4.7.1` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.5.5` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-grpc` | `4.12.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-jackson-xml` | `4.8.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.1` | `2.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-reactor` | `3.9.1` | `4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-rxjava3` | `3.9.0` | `4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.16.1` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-servlet` | `5.6.0` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.10.2` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test-resources` | `2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-tracing` | `7.2.0` | `8.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.12.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.netty` | `not present` | `4.2.13.Final` | `added` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.system-stubs-core` | `2.1.8` | `2.1.8` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.zipkin-sender-stackdriver` | `2.1.1` | `2.3.1` | `changed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |
| `settings.gradle` | `plugin.io.micronaut.build.shared.settings` | `7.6.6` | `8.0.0-M18` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `5a9e0586e999` remove kotlin (Sergio del Amo, 2025-12-10)
- `d39394ff4b27` remove mironaut-test included by Micronaut Build Gradle plugin (Sergio del Amo, 2025-12-10)
- `e910abe8330b` remove spock included by Micronaut Build Gradle plugin (Sergio del Amo, 2025-12-10)
- `f60cde5a2aab` remove groovy included by Micronaut Build Gradle plugin (Sergio del Amo, 2025-12-10)
- `89c90031f1ec` remove micronaut-docs included by Micronaut Build Gradle plugin (Sergio del Amo, 2025-12-10)
- `86321d9be312` Remove deprecations for Micronaut Framework 5 and document breaking changes (#1078) (Dean Wette, 2024-03-18)

### Features

- `bfedcdfeadef` Add Google Secret Manager config importer (#1452) (Graeme Rocher, 2026-04-18)
- `ddab03c698e6` add micronautBuild descriptor parentModuleId (Sergio del Amo, 2025-12-10)

### Fixes

- `cede11791e66` fix: address checkstyle failures (FinalClass, DesignForExtension) (#1462) (Copilot, 2026-05-02)
- `74451a9b1327` fix(deps): update managed.gax to v2.79.0 (#1447) (renovate[bot], 2026-04-20)
- `59f34dffa4ea` fix(deps): update dependency com.google.cloud:google-cloud-pubsub to v1.150.1 (#1441) (renovate[bot], 2026-04-20)
- `929beb32a136` fix(deps): update dependency com.google.cloud:google-cloud-core to v2.69.0 (#1446) (renovate[bot], 2026-04-20)
- `6846eae51ce2` fix(deps): update dependency com.google.cloud:google-cloud-secretmanager to v2.91.0 (#1440) (renovate[bot], 2026-04-20)
- `31494d76ab84` fix(deps): update managed.gax to v2.75.0 (#1418) (renovate[bot], 2026-02-20)
- `942bb0ad8099` fix(deps): update dependency com.google.cloud:google-cloud-pubsub to v1.148.0 (#1398) (renovate[bot], 2026-02-20)
- `f6e8b35a6595` fix(deps): update dependency com.google.cloud.functions.invoker:java-function-invoker to v1.4.3 (#1385) (renovate[bot], 2026-02-20)
- `326d3db5d9f1` fix(deps): update managed.google.auth.library.oauth2http to v1.43.0 (#1419) (renovate[bot], 2026-02-20)
- `4e56b52cb63f` fix(deps): update dependency com.google.cloud:google-cloud-core to v2.65.0 (#1394) (renovate[bot], 2026-02-20)
- `19a14058eff8` fix(deps): update dependency com.google.cloud:google-cloud-secretmanager to v2.85.0 (#1399) (renovate[bot], 2026-02-20)
- `0db53b48b904` fix(deps): update dependency io.micronaut.servlet:micronaut-servlet-bom to v6.0.0-m2 (#1436) (renovate[bot], 2026-02-20)
- `c5e15f096fa7` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m12 (#1416) (renovate[bot], 2026-02-19)
- `b4d8172fd255` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m2 (#1429) (renovate[bot], 2026-02-19)
- `f8fb47263099` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.2 (#1434) (renovate[bot], 2026-02-19)
- `39ffa84c8fa1` fix(deps): update dependency io.micronaut.discovery:micronaut-discovery-client to v4.7.2 (#1435) (renovate[bot], 2026-02-19)
- `795dc0acee28` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#1409) (renovate[bot], 2025-12-10)
- `8ba7c698188f` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.1 (#1401) (renovate[bot], 2025-12-10)
- `cb60a55157bc` fix(deps): update dependency io.micronaut.reactor:micronaut-reactor-bom to v3.9.1 (#1404) (renovate[bot], 2025-12-10)
- `5e3cc57c74a0` fix(deps): update dependency io.micronaut.rxjava3:micronaut-rxjava3-bom to v3.9.0 (#1408) (renovate[bot], 2025-12-10)
- `9355c8e68542` fix(deps): update dependency io.micronaut.tracing:micronaut-tracing-bom to v7.2.0 (#1411) (renovate[bot], 2025-12-10)
- `17206edaa6e1` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.12.0 (#1412) (renovate[bot], 2025-12-10)
- `b737224eaf79` fix(deps): update dependency io.micronaut.xml:micronaut-jackson-xml-bom to v4.8.0 (#1415) (renovate[bot], 2025-12-10)
- `608b9ec95b43` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#1400) (renovate[bot], 2025-12-10)
- `822ec9037bc8` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.8 (#1386) (renovate[bot], 2025-11-07)
- `0b938f8000dd` fix(deps): update dependency org.awaitility:awaitility to v4.2.1 (#1082) (renovate[bot], 2024-04-07)
- `d866f9b06ccc` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.3.6 (#1098) (renovate[bot], 2024-04-07)
- `89e23a8909df` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.5.0 (#1080) (renovate[bot], 2024-04-07)
- `338cda384b49` fix(deps): update dependency com.google.cloud:google-cloud-core to v2.36.1 (#1092) (renovate[bot], 2024-04-07)
- `1ab0262ef8f7` fix(deps): update dependency com.google.cloud:google-cloud-secretmanager to v2.41.0 (#1093) (renovate[bot], 2024-04-07)
- `b168084bc893` fix(deps): update dependency io.micronaut.reactor:micronaut-reactor-bom to v3.3.0 (#1094) (renovate[bot], 2024-04-07)
- `b20e7f3d0650` fix(deps): update dependency io.micronaut.rxjava3:micronaut-rxjava3-bom to v3.3.0 (#1096) (renovate[bot], 2024-04-07)
- `436ae17c26fa` fix(deps): update dependency com.google.cloud:google-cloud-pubsub to v1.128.0 (#1086) (renovate[bot], 2024-04-07)
- `b9c5f290ad37` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.4.0 (#1090) (renovate[bot], 2024-04-01)
- `69f93462f499` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.3.12 (#1088) (renovate[bot], 2024-03-28)
- `dda8187fcb27` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.3.5 (#1087) (renovate[bot], 2024-03-27)
- `995f2081e427` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.3.11 (#1071) (renovate[bot], 2024-03-21)

### Security

- `cab323cf3e5a` Update managed.google.auth.library.oauth2http to v1.46.0 (#1461) (renovate[bot], 2026-05-02)

### Dependency Updates

- `3e11e95cc5b2` chore: Bump version to 6.0.1-SNAPSHOT (micronaut-build, 2026-05-18)
- `de9cf3c475be` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2026-05-08)
- `e3e29bc8752a` Combine Renovate dependency upgrades (#1470) (Graeme Rocher, 2026-05-06)
- `d9a3dd780e73` Update Micronaut dependencies (#1457) (renovate[bot], 2026-05-02)
- `9905ea1760cf` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2026-04-20)
- `880c54d2f3e1` Update dependency com.google.cloud.functions:functions-framework-api to v2.0.1 (#1454) (renovate[bot], 2026-04-20)
- `1a5083cee5c9` Update dependency io.zipkin.gcp:brave-propagation-stackdriver to v2.3.1 (#1450) (renovate[bot], 2026-04-20)
- `c2735467a4d7` chore(deps): update gradle to v9.4.1 (#1444) (renovate[bot], 2026-04-20)
- `3059ebafd63b` Update dependency io.micronaut:micronaut-core-bom to v5.0.0-M23 (#1439) (renovate[bot], 2026-04-20)
- `29fb11f6771e` Update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-M7 (#1449) (renovate[bot], 2026-04-20)
- `55ee8c438af3` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2026-02-20)
- `ce6437a5aba1` chore(deps): update actions/cache action to v5 (#1420) (renovate[bot], 2026-02-19)
- `d0374f5b9260` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#1417) (renovate[bot], 2026-02-19)
- `59781eabcf1f` chore(deps): update graalvm/setup-graalvm action to v1.4.5 (#1427) (renovate[bot], 2026-02-19)
- `5ac046d0e3d2` chore(deps): update gradle to v9.3.1 (#1431) (renovate[bot], 2026-02-19)
- `7aa12faa0d78` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#1403) (renovate[bot], 2025-12-10)
- `29d30ed48016` chore(deps): update gradle to v9.2.1 (#1397) (renovate[bot], 2025-12-10)
- `cb2de0c21c40` chore(deps): update softprops/action-gh-release action to v2.4.2 (#1393) (renovate[bot], 2025-11-11)
- `fbabb7031492` chore(deps): update gradle to v9.2.0 (#1388) (renovate[bot], 2025-11-07)
- `4100091a63e9` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m9 (#1383) (renovate[bot], 2025-11-07)
- `ba3d0815d203` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#1380) (renovate[bot], 2025-10-27)
- `a4c29e4cc68c` chore(deps): update gradle/gradle-build-action action to v3.2.0 (#1097) (renovate[bot], 2024-04-07)
- `481e02673401` chore(deps): update plugin io.micronaut.build.shared.settings to v6.7.0 (#1091) (renovate[bot], 2024-04-01)
- `c6fafecede07` chore(deps): update graalvm/setup-graalvm action to v1.2.1 (#1085) (renovate[bot], 2024-03-27)
- `7504905a8a10` chore(deps): update graalvm/setup-graalvm action to v1.2.0 (#1083) (renovate[bot], 2024-03-21)

### Review Candidates

- `82e0afa99892` micronaut-tracing = "8.0.0" (Sergio del Amo, 2026-05-19)
- `ddeaf2c8f8b5` Update common files (#1483) (micronaut-build, 2026-05-19)
- `1ff59de13b2a` [skip ci] Release v6.0.0 (micronaut-build, 2026-05-18)
- `724d04f9aae2` ignore GHSA-rcgg-9c38-7xpx (Sergio del Amo, 2026-05-18)
- `6315ab5e638e` micronaut-grpc = "5.0.0" (Sergio del Amo, 2026-05-18)
- `e46150dbf513` Update common files (#1480) (micronaut-build, 2026-05-15)
- `1f8329c522be` micronaut-test = "5.0.0" (Sergio del Amo, 2026-05-14)
- `5fbad5b835aa` Update versions (Sergio del Amo, 2026-05-14)
- `2c47f8f3bc85` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `cdae947da45f` Update common files (#1479) (micronaut-build, 2026-05-09)
- `f2650c02aca3` [skip ci] Release v6.0.0-RC1 (micronaut-build, 2026-05-08)
- `16bd92465c2a` update versions (Sergio del Amo, 2026-05-08)
- `152feacf7781` Update common files (#1478) (micronaut-build, 2026-05-08)
- `9fa006b138ab` Update CloudEvents SDK to v4 (#1475) (Graeme Rocher, 2026-05-06)
- `fa3ccf7770b7` Update CloudEvents SDK to v4 (Graeme Rocher, 2026-05-06)
- `31eb2d67e191` Reapply Stackdriver sender v2 compatibility (#1471) (Graeme Rocher, 2026-05-06)
- `49f3ef428184` managed-google-function-invoker = "2.0.1" (Sergio del Amo, 2026-05-06)
- `01c2aadea418` import static org.mockito.Mockito.spy (Sergio del Amo, 2026-05-06)
- `33942f83ff14` Update common files (#1463) (micronaut-build, 2026-05-06)
- `c730ffced4eb` micronaut-validation = "5.0.0-RC1" (Sergio del Amo, 2026-05-06)
- `efd2cf245ae5` micronaut-serde = "3.0.0-RC1" (Sergio del Amo, 2026-05-06)
- `3b14d32009bf` micronaut-reactor = "4.0.0-RC1" (Sergio del Amo, 2026-05-06)
- `241ead58ab1f` micronaut = "5.0.0-RC1" (Sergio del Amo, 2026-05-06)
- `1e2f9b6f667e` gradle 9.5 (Sergio del Amo, 2026-05-06)
- `1e3c868059f8` wilcard imports (Sergio del Amo, 2026-05-06)
- `9ac201b42ad8` Update common files (#1459) (micronaut-build, 2026-05-02)
- `feafcc105ec4` Update Gradle to v9.5.0 (#1460) (renovate[bot], 2026-05-02)
- `1b0bf761c850` Update common files (#1456) (micronaut-build, 2026-04-26)
- `daf97e2320c7` [skip ci] Release v6.0.0-M2 (micronaut-build, 2026-04-20)
- `a696164d97df` Replace usage of MediaTypeCodec (#1451) (Denis Stepanov, 2026-04-20)
- `8c891726076a` micronaut-gradle-plugin = "5.0.0-M1" (Sergio del Amo, 2026-04-20)
- `8b7feee75103` micronaut-validation = "5.0.0-M2" (Sergio del Amo, 2026-04-20)
- `5599fe8d8769` micronaut-servlet = "6.0.0-M3" (Sergio del Amo, 2026-04-20)
- `a885148af89a` micronaut-reactor = "4.0.0-M2" (Sergio del Amo, 2026-04-20)
- `fcbb2ca37011` micronaut-test = "5.0.0-M8" (Sergio del Amo, 2026-04-20)
- `758a17cb6f6e` Update gradle/actions action to v6 (#1448) (renovate[bot], 2026-04-20)
- `a3a8f2f1e8ae` Update GitHub Artifact Actions (#1442) (renovate[bot], 2026-04-20)
- `0ed1cb632e5f` Update common files (#1443) (micronaut-build, 2026-04-20)
- `7198b7a89d02` Update softprops/action-gh-release action to v2.6.2 (#1445) (renovate[bot], 2026-04-20)
- `1a9727041ad4` [skip ci] Release v6.0.0-M1 (micronaut-build, 2026-02-20)
- `116bd16c6a34` Update to Functions Frameworks v2 (#1391) (issam liqali, 2026-02-20)
- `e12856c552df` GCP for Micronaut 5 (#1432) (dhavalbhensdadiya-crest, 2026-02-20)
- `9e19db270f8e` Update common files (#1437) (micronaut-build, 2026-02-20)
- `e6ef7f864b8d` micronaut-discovery = "5.0.0-M1" (Sergio del Amo, 2026-02-19)
- `04b43963756b` micronaut-test-resources = "3.0.0-M6" (Sergio del Amo, 2026-02-19)
- `3ec76ee9d255` micronaut-tracing 8.0.0-M1 (Sergio del Amo, 2026-02-19)
- `bce96d295129` logging 2.0.0-M2 (Sergio del Amo, 2026-02-19)
- `83fc6b73269f` Update common files (#1421) (micronaut-build, 2026-02-19)
- `1d595f862d10` change ObjectMapper import (Sergio del Amo, 2025-12-10)
- `f1643d908d9c` def setBeanIntrospectionModule no longer exist (Sergio del Amo, 2025-12-10)
- `654b9cc6a7ff` fix override (Sergio del Amo, 2025-12-10)
- `2e11827f1356` use mnTest (Sergio del Amo, 2025-12-10)
- `ed7d693c9ab2` source and target compatibility 21 (Sergio del Amo, 2025-12-10)
- `c976225556df` micronaut-validation = "5.0.0-M1" (Sergio del Amo, 2025-12-10)
- `d5fd64165d20` micronaut-test = "4.10.2" (Sergio del Amo, 2025-12-10)
- `4737cce7e460` micronaut-servlet = "6.0.0-M1" micronaut-tracing = "7.2.0" (Sergio del Amo, 2025-12-10)
- `2a5182a56d55` micronaut-serde = "3.0.0-M1" (Sergio del Amo, 2025-12-10)
- `2d2a6ef03518` micronaut-rxjava3 = "4.0.0-M1" (Sergio del Amo, 2025-12-10)
- `ef88261aa3bb` micronaut-reactor = "4.0.0-M1" (Sergio del Amo, 2025-12-10)
- `4225ccfba854` micronaut = "5.0.0-M2" (Sergio del Amo, 2025-12-10)
- `bcbec20748da` Update common files (#1395) (micronaut-build, 2025-12-10)
- `c422cb3f7c3c` Replace Micronaut nullability annotations with JSpecify annotations (#1406) (Copilot, 2025-12-01)
- `faf601584478` Update common files (#1387) (micronaut-build, 2025-11-07)
- `66d42abfc524` Update common files (#1377) (micronaut-build, 2025-10-27)
- `c2e5deed4d4c` Update common files (#1376) (micronaut-build, 2025-10-17)
- `70ea53c26e31` Micronaut Gradle build plugin 8.0.0-M4 (Sergio del Amo, 2025-10-15)
- `36d233f260af` gradle 9.1 (Sergio del Amo, 2025-10-15)
- `2d92642a8f29` Merge branch '5.13.x' into 6.0.x (Sergio del Amo, 2025-10-15)
- `a3ca2a00af29` Merge branch '5.6.x' into 6.0.x (Sergio del Amo, 2024-04-12)
- `be71c278d102` Update common files (#1089) (micronaut-build, 2024-03-28)
- `50e0b6566edb` Update common files (#1084) (micronaut-build, 2024-03-27)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` build.gradle
- `M` buildSrc/build.gradle.kts
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.gcp-module.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.gcp-tests.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.gcp-testsuite.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.http-server-tck-module.gradle
- `M` gcp-bom/build.gradle
- `M` gcp-logging/build.gradle.kts
- `M` gcp-pubsub/build.gradle
- `M` gcp-secret-manager/build.gradle
- `M` gcp-secret-manager/src/main/java/io/micronaut/gcp/secretmanager/client/VersionedSecret.java
- `M` gcp-tracing/build.gradle.kts
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` settings.gradle
- `M` test-suite-groovy/build.gradle
- `M` test-suite-kotlin/build.gradle
- `A` test-suite-utils/build.gradle.kts
- `M` test-suite/build.gradle

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
- `A` src/main/docs/guide/breaks.adoc
- `M` src/main/docs/guide/secretManager.adoc
- `M` src/main/docs/guide/secretManager/distributedConfiguration.adoc
- `M` src/main/docs/guide/secretManager/secretManagerClient.adoc
- `M` src/main/docs/guide/toc.yml

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
- `M` config/accepted-api-changes.json
- `M` config/checkstyle/checkstyle.xml
- `M` gcp-common/src/main/java/io/micronaut/discovery/cloud/gcp/GoogleComputeInstanceMetadataResolverUtils.java
- `M` gcp-common/src/main/java/io/micronaut/gcp/GoogleCloudConfiguration.java
- `M` gcp-common/src/main/java/io/micronaut/gcp/condition/RequiresGoogleProjectId.java
- `M` gcp-common/src/main/java/io/micronaut/gcp/credentials/DefaultOAuth2HttpTransportFactory.java
- `M` gcp-common/src/main/java/io/micronaut/gcp/credentials/GoogleCredentialsConfiguration.java
- `M` gcp-common/src/main/java/io/micronaut/gcp/credentials/GoogleCredentialsFactory.java
- `M` gcp-common/src/main/java/io/micronaut/gcp/credentials/OAuth2MessageBodyWriter.java
- `M` gcp-function-cloudevents/src/main/java/io/micronaut/gcp/function/cloudevents/GoogleCloudEventsFunction.java
- `M` gcp-function-http/src/main/java/io/micronaut/gcp/function/http/BodyUtils.java
- `M` gcp-function-http/src/main/java/io/micronaut/gcp/function/http/GoogleBinderRegistry.java
- `M` gcp-function-http/src/main/java/io/micronaut/gcp/function/http/GoogleCookies.java
- `M` gcp-function-http/src/main/java/io/micronaut/gcp/function/http/GoogleFunctionHttpRequest.java
- `M` gcp-function-http/src/main/java/io/micronaut/gcp/function/http/GoogleFunctionHttpResponse.java
- `M` gcp-function-http/src/main/java/io/micronaut/gcp/function/http/GoogleHttpResponse.java
- `M` gcp-function-http/src/main/java/io/micronaut/gcp/function/http/GoogleMultiValueMap.java
- `M` gcp-function-http/src/main/java/io/micronaut/gcp/function/http/GooglePartBinder.java
- `M` gcp-function-http/src/main/java/io/micronaut/gcp/function/http/HttpFunction.java
- `M` gcp-function-http/src/main/java/io/micronaut/gcp/function/http/jackson/GoogleJacksonConfiguration.java
- `D` gcp-function-http/src/main/java/io/micronaut/gcp/function/http/jackson/ObjectMapperCustomizer.java
- `M` gcp-function/src/main/java/io/micronaut/gcp/function/GoogleFunctionInitializer.java
- `M` gcp-logging/src/main/java/io/micronaut/gcp/logging/StackdriverJsonLayout.java
- `M` gcp-pubsub/src/main/java/io/micronaut/gcp/pubsub/annotation/MessageId.java
- `M` gcp-pubsub/src/main/java/io/micronaut/gcp/pubsub/annotation/OrderingKey.java
- `M` gcp-pubsub/src/main/java/io/micronaut/gcp/pubsub/annotation/PubSubClient.java
- `M` gcp-pubsub/src/main/java/io/micronaut/gcp/pubsub/annotation/PubSubListener.java
- `M` gcp-pubsub/src/main/java/io/micronaut/gcp/pubsub/annotation/PushSubscription.java
- `M` gcp-pubsub/src/main/java/io/micronaut/gcp/pubsub/annotation/Subscription.java
- `M` gcp-pubsub/src/main/java/io/micronaut/gcp/pubsub/annotation/Topic.java
- `M` gcp-pubsub/src/main/java/io/micronaut/gcp/pubsub/bind/DefaultSubscriberFactory.java
- `M` gcp-pubsub/src/main/java/io/micronaut/gcp/pubsub/bind/PubSubAttributesConvertibleValues.java
- `M` gcp-pubsub/src/main/java/io/micronaut/gcp/pubsub/bind/PubSubBodyBinder.java
- `M` gcp-pubsub/src/main/java/io/micronaut/gcp/pubsub/exception/PubSubMessageReceiverException.java
- `M` gcp-pubsub/src/main/java/io/micronaut/gcp/pubsub/intercept/AbstractPubSubConsumerMethodProcessor.java
- `M` gcp-pubsub/src/main/java/io/micronaut/gcp/pubsub/intercept/PubSubPushConsumerAdvice.java
- `M` gcp-pubsub/src/main/java/io/micronaut/gcp/pubsub/push/PubSubPushConfigurationProperties.java
- `M` gcp-pubsub/src/main/java/io/micronaut/gcp/pubsub/push/PushControllerConfiguration.java
- `M` gcp-pubsub/src/main/java/io/micronaut/gcp/pubsub/push/PushSubscriberHandler.java
- `M` gcp-pubsub/src/main/java/io/micronaut/gcp/pubsub/support/DefaultPublisherFactory.java
- `M` gcp-pubsub/src/main/java/io/micronaut/gcp/pubsub/support/PubSubConfigurationFactory.java
- `M` gcp-pubsub/src/main/java/io/micronaut/gcp/pubsub/support/PubSubSubscriptionUtils.java
- `M` gcp-pubsub/src/main/java/io/micronaut/gcp/pubsub/support/PubSubTopicUtils.java
- `M` gcp-pubsub/src/main/java/io/micronaut/gcp/pubsub/validation/PushMessageValidator.java
- `M` gcp-secret-manager/src/main/java/io/micronaut/gcp/secretmanager/SecretManagerConfigurationClient.java
- `M` gcp-secret-manager/src/main/java/io/micronaut/gcp/secretmanager/client/DefaultSecretManagerClient.java
- `A` gcp-secret-manager/src/main/java/io/micronaut/gcp/secretmanager/client/SecretManagerSecretAccessor.java
- `M` gcp-secret-manager/src/main/java/io/micronaut/gcp/secretmanager/configuration/SecretManagerConfigurationProperties.java
- `A` gcp-secret-manager/src/main/java/io/micronaut/gcp/secretmanager/imports/SecretManagerImportDeclaration.java
- `A` gcp-secret-manager/src/main/java/io/micronaut/gcp/secretmanager/imports/SecretManagerImporterClientFactory.java
- `A` gcp-secret-manager/src/main/java/io/micronaut/gcp/secretmanager/imports/SecretManagerPropertySourceImporter.java
- `A` gcp-secret-manager/src/main/java/io/micronaut/gcp/secretmanager/imports/SecretManagerPropertySourceReader.java
- `A` gcp-secret-manager/src/main/resources/META-INF/services/io.micronaut.context.env.PropertySourceImporter
- `M` gcp-serde-cloudevents/src/main/java/io/micronaut/gcp/serde/cloudevents/CloudEventTypesSerde.java
- `M` gcp-tracing/src/main/java/io/micronaut/gcp/tracing/zipkin/StackdriverSenderFactory.java
- `A` osv-scanner.toml

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` gcp-common/src/test/groovy/io/micronaut/gcp/credentials/GoogleCredentialsFactorySpec.groovy
- `M` gcp-common/src/testFixtures/java/io/micronaut/gcp/credentials/fixture/ServiceAccountCredentialsTestHelper.java
- `M` gcp-function-cloudevents/src/test/groovy/io/micronaut/gcp/function/cloudevents/GoogleCloudStorageFunctionSpec.groovy
- `M` gcp-function-cloudevents/src/test/groovy/io/micronaut/gcp/function/cloudevents/StorageObjectDataMapperSpec.groovy
- `M` gcp-function-http-test/src/main/java/io/micronaut/gcp/function/http/test/GoogleCloudFunctionHttpHandler.java
- `M` gcp-function-http-test/src/main/java/io/micronaut/gcp/function/http/test/HttpExchangeHttpRequest.java
- `M` gcp-function-http-test/src/main/java/io/micronaut/gcp/function/http/test/HttpExchangeHttpResponse.java
- `M` gcp-function-http/src/test/groovy/io/micronaut/gcp/function/http/ReactiveBindingSpec.groovy
- `M` gcp-pubsub/src/test/groovy/io/micronaut/gcp/pubsub/bind/AcknowledgementSpec.groovy
- `M` gcp-pubsub/src/test/groovy/io/micronaut/gcp/pubsub/integration/IntegrationTestSpec.groovy
- `M` gcp-secret-manager/src/test/groovy/io/micronaut/gcp/secretmanager/LocationSecretManagerConfigSpec.groovy
- `A` gcp-secret-manager/src/test/groovy/io/micronaut/gcp/secretmanager/SecretManagerClientIntegrationSpec.groovy
- `M` gcp-secret-manager/src/test/groovy/io/micronaut/gcp/secretmanager/SecretManagerConfigSpec.groovy
- `A` gcp-secret-manager/src/test/groovy/io/micronaut/gcp/secretmanager/imports/SecretManagerImporterClientFactory.groovy
- `A` gcp-secret-manager/src/test/groovy/io/micronaut/gcp/secretmanager/imports/SecretManagerPropertySourceImporterEndToEndSpec.groovy
- `A` gcp-secret-manager/src/test/groovy/io/micronaut/gcp/secretmanager/imports/SecretManagerPropertySourceImporterIntegrationSpec.groovy
- `A` gcp-secret-manager/src/test/groovy/io/micronaut/gcp/secretmanager/imports/SecretManagerPropertySourceImporterSpec.groovy
- `M` gcp-secret-manager/src/test/groovy/io/micronaut/gcp/utils/LocalSecretManagerServiceClientFactory.groovy
- `M` gcp-serde-cloudevents/src/test/groovy/io/micronaut/gcp/serde/cloudevents/CloudEventTypesSerdeSpec.groovy
- `D` gcp-tracing/src/test/groovy/io/micronaut/gcp/tracing/zipkin/StackdriverAsyncReporterIntegrationSpec.groovy
- `M` test-suite-groovy/src/main/groovy/io/micronaut/gcp/pubsub/bind/MessagePublishTime.groovy
- `M` test-suite-groovy/src/main/groovy/io/micronaut/gcp/pubsub/serdes/JavaMessageSerDes.groovy
- `M` test-suite-groovy/src/main/groovy/io/micronaut/gcp/pubsub/serdes/XmlMessageSerDes.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/gcp/pubsub/subscriber/AcknowledgementPushSubscriberSpec.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/gcp/pubsub/subscriber/AcknowledgementSubscriberSpec.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/gcp/pubsub/subscriber/ContentTypePushSubscriberSpec.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/gcp/pubsub/subscriber/ContentTypeSubscriberSpec.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/gcp/pubsub/subscriber/ReactivePushSubscriberSpec.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/gcp/pubsub/subscriber/ReactiveSubscriberSpec.groovy
- `A` test-suite-groovy/src/test/resources/application-test.properties
- `D` test-suite-groovy/src/test/resources/application-test.yml
- `M` test-suite-http-server-tck-gcp-function-http-test/src/test/java/io/micronaut/http/server/tck/gcp/function/tests/GcpFunctionHttpTestServerTestSuite.java
- `A` test-suite-http-server-tck-gcp-function-http-test/src/test/java/io/micronaut/http/server/tck/gcp/function/tests/GcpFunctionHttpTestServerUnderTestProvider.java
- `M` test-suite-http-server-tck-gcp-function-http-test/src/test/resources/META-INF/services/io.micronaut.http.tck.ServerUnderTestProvider
- `M` test-suite-http-server-tck-gcp-function-http/src/test/java/io/micronaut/http/server/tck/gcp/function/GcpFunctionHttpServerUnderTest.java
- `M` test-suite-http-server-tck-gcp-function-http/src/test/java/io/micronaut/http/server/tck/gcp/function/GcpFunctionHttpServerUnderTestProvider.java
- `M` test-suite-http-server-tck-gcp-function-http/src/test/java/io/micronaut/http/server/tck/gcp/function/tests/GcpFunctionHttpServerTestSuite.java
- `M` test-suite-kotlin/src/main/kotlin/io/micronaut/gcp/pubsub/serdes/XmlMessageSerDes.kt
- `M` test-suite-kotlin/src/main/kotlin/io/micronaut/gcp/pubsub/support/Animal.kt
- `M` test-suite-kotlin/src/test/groovy/subscriber/AcknowledgementPushSubscriberSpec.groovy
- `M` test-suite-kotlin/src/test/groovy/subscriber/AcknowledgementSubscriberSpec.groovy
- `M` test-suite-kotlin/src/test/groovy/subscriber/ContentTypePushSubscriberSpec.groovy
- `M` test-suite-kotlin/src/test/groovy/subscriber/ContentTypeSubscriberSpec.groovy
- `M` test-suite-kotlin/src/test/groovy/subscriber/ReactivePushSubscriberSpec.groovy
- `M` test-suite-kotlin/src/test/groovy/subscriber/ReactiveSubscriberSpec.groovy
- `A` test-suite-kotlin/src/test/resources/application-test.properties
- `D` test-suite-kotlin/src/test/resources/application-test.yml
- `A` test-suite-utils/src/main/java/io/micronaut/pubsub/testcontainers/PubSubEmulator.java
- `M` test-suite/src/main/java/example/background/Example.java
- `M` test-suite/src/main/java/io/micronaut/gcp/pubsub/bind/MessagePublishTime.java
- `M` test-suite/src/main/java/io/micronaut/gcp/pubsub/serdes/JavaMessageSerDes.java
- `M` test-suite/src/main/java/io/micronaut/gcp/pubsub/serdes/XmlMessageSerDes.java
- `M` test-suite/src/test/java/io/micronaut/gcp/pubsub/subscriber/AcknowledgementPushSubscriberTest.java
- `M` test-suite/src/test/java/io/micronaut/gcp/pubsub/subscriber/AcknowledgementSubscriberTest.java
- `M` test-suite/src/test/java/io/micronaut/gcp/pubsub/subscriber/ContentTypePushSubscriberSpec.java
- `M` test-suite/src/test/java/io/micronaut/gcp/pubsub/subscriber/ContentTypeSubscriberTest.java
- `M` test-suite/src/test/java/io/micronaut/gcp/pubsub/subscriber/ReactivePushSubscriberTest.java
- `M` test-suite/src/test/java/io/micronaut/gcp/pubsub/subscriber/ReactiveSubscriberTest.java
- `A` test-suite/src/test/resources/application-test.properties
- `D` test-suite/src/test/resources/application-test.yml

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

