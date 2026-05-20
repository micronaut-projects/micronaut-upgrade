Compared micronaut-kafka as mn4 → mn5.

  Scope:

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-kafka, branch 5.10.x, SHA a614282e8f03
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-kafka, branch 6.0.x, SHA 8a933ba97319
  - Report: /private/tmp/micronaut-kafka-5.10-to-6.0-comparison.md

  Key findings:

  - Major baseline move: Micronaut 4.10.21 → 5.0.0, project version 5.10.1-SNAPSHOT → 6.0.1-SNAPSHOT, managed
    Kafka 3.9.2 → 4.2.0; docs declare Micronaut 5, Kafka 4, Java 25.
  - Build stack changed: Gradle 8.14.3 → 9.5.1, Micronaut Gradle plugin 4.6.2 → 5.0.0-M1, shared settings
    plugin 7.6.4 → 8.0.0-M18, .sdkmanrc now pins 25.0.1-graal.
  - New listener capabilities: @KafkaListener.id, ConsumerCreationStrategy.PER_CLASS, topic-aware deserializer
    routing, and new @KafkaScope listener-invocation scope.
  - Error handling adds LOG_AND_RESUME_AT_NEXT_RECORD with dlq support for dead-letter publishing.
  - Kafka Streams gained global disable config via kafka.streams.enabled=false, better KTable/GlobalKTable
    support, graceful shutdown handling, and Kafka 4.x health fixes.
  - Metrics changed materially: consumer/producer metrics now default to Micrometer-style names, with
    micronaut.metrics.binders.kafka.metric-name-style=legacy for migration.
  - Security/dependency hardening: jackson-core is forced to 2.21.1 to avoid the vulnerable transitive 2.19.1
    from Kafka clients.
  - Runtime fixes include optional AdminClient via kafka.admin.enabled=false, SSL protocol inference from SSL
    config, async @KafkaClient methods defaulting to the blocking executor, graceful consumer shutdown, and
    transactional producer recovery.

  Diff size: 269 files changed, 12128 insertions(+), 993 deletions(-). I did not run tests; this was a folder
  comparison only.

# Release Note Comparison

Generated: 2026-05-19 10:22 UTC
Comparison: `5.10.x` -> `6.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-kafka` | `5.10.x` | `a614282e8f03` | `git@github.com:micronaut-projects/micronaut-kafka.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-kafka` | `6.0.x` | `8a933ba97319` | `git@github.com:micronaut-projects/micronaut-kafka.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-kafka`
- Commit candidates found: 120
- File changes listed: 269
- Version values listed: 25
- File status counts: A=86, D=1, M=181, R=1

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `5.10.1-SNAPSHOT` | `6.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-cache` | `io.micronaut.cache:micronaut-cache-bom:5.3.0` | `io.micronaut.cache:micronaut-cache-bom:6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-gradle-plugin` | `io.micronaut.gradle:micronaut-gradle-plugin:4.6.2` | `io.micronaut.gradle:micronaut-gradle-plugin:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-micrometer` | `io.micronaut.micrometer:micronaut-micrometer-bom:5.13.0` | `io.micronaut.micrometer:micronaut-micrometer-bom:6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-reactor` | `io.micronaut.reactor:micronaut-reactor-bom:3.9.0` | `io.micronaut.reactor:micronaut-reactor-bom:4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.15.5` | `io.micronaut.serde:micronaut-serde-bom:3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test` | `not present` | `io.micronaut.test:micronaut-test-bom:5.0.0` | `added` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-resources` | `io.micronaut.testresources:micronaut-test-resources-bom:2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-tracing` | `io.micronaut.tracing:micronaut-tracing-bom:7.2.0` | `io.micronaut.tracing:micronaut-tracing-bom:8.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.27` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.21` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-cache` | `5.3.0` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.6.2` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-micrometer` | `5.13.0` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-platform` | `4.10.12` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-reactor` | `3.9.0` | `4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.15.5` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.10.3` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test-resources` | `2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-tracing` | `7.2.0` | `8.0.0` | `changed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |
| `settings.gradle` | `plugin.io.micronaut.build.shared.settings` | `7.6.4` | `8.0.0-M18` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `d1dac573f1ec` remove groovy version (Sergio del Amo, 2026-05-09)

### Features

- `4764a6c9408d` Add global Kafka Streams disable configuration (#1346) (Graeme Rocher, 2026-05-05)
- `fd785be8767b` Add Kafka listener invocation scope (#1336) (Graeme Rocher, 2026-04-30)
- `84c12cdd6dbd` Introduce id for KafkaListener (#1347) (Graeme Rocher, 2026-04-30)
- `a9191ee64db2` Add per-class Kafka listener consumer strategy (#1305) (Graeme Rocher, 2026-04-30)
- `3d9ef28be883` Add regression coverage for deserialization consumer records (#1339) (Graeme Rocher, 2026-04-28)
- `639caac121c5` Add guide for Avro and Protobuf serialization (#1335) (Graeme Rocher, 2026-04-28)
- `3f086391d2a7` Add LOG_AND_RESUME_AT_NEXT_RECORD DLQ support (#1317) (Graeme Rocher, 2026-04-24)
- `b5c31971ac2a` Support GlobalKTable-only Kafka Streams topologies (#1304) (Graeme Rocher, 2026-04-17)
- `789d6e218cc6` Add Control Panel section and documentation link [skip ci] (#1280) (Álvaro Sánchez-Mariscal, 2026-02-02)

### Fixes

- `108497ad3905` Fix Kafka Streams health endpoint regression on Kafka 4.x (#1302) (Graeme Rocher, 2026-04-29)
- `b028537c0802` Fix KafkaConfigurationSpec CI regression on 6.0.x (#1324) (Graeme Rocher, 2026-04-23)
- `6a73c4294e8e` fix(deps): update dependency io.zipkin.brave:brave-instrumentation-kafka-clients to v6.3.1 (#1316) (Graeme Rocher, 2026-04-17)
- `07ebfde4b0ad` fix(deps): update dependency org.graalvm.sdk:graal-sdk to v25.0.2 (#1273) (renovate[bot], 2026-04-13)
- `52048a78c7a8` fix(deps): update dependency io.micronaut.platform:micronaut-platform to v4.10.11 (#1263) (renovate[bot], 2026-04-13)
- `dd03121b4f48` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m6 (#1276) (renovate[bot], 2026-04-13)
- `cbd3fdf930de` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m19 (#1294) (renovate[bot], 2026-04-02)
- `e56b20f19be7` fix(deps): update dependency io.micronaut.test:micronaut-test-bom to v5.0.0-m7 (#1290) (renovate[bot], 2026-03-24)
- `7fe07a682c50` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m17 (#1262) (renovate[bot], 2026-03-24)
- `d238fd4cb5ee` fix(deps): update dependency io.micronaut.platform:micronaut-platform to v4.10.3 (#1248) (renovate[bot], 2025-12-10)
- `a1a3ebee3d1d` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#1249) (renovate[bot], 2025-12-10)
- `021b8798a299` fix(deps): update dependency micronaut to v4.10.3 (#1250) (renovate[bot], 2025-12-10)
- `892156541757` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#1254) (renovate[bot], 2025-12-10)
- `a04bd5a21d96` fix(deps): update dependency org.graalvm.sdk:graal-sdk to v25 (#1255) (renovate[bot], 2025-12-10)
- `6d3fb8484492` fix(deps): update dependency io.micronaut.micrometer:micronaut-micrometer-bom to v5.13.2 (#1259) (renovate[bot], 2025-12-10)
- `ff1bd12ef763` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.8 (#1240) (renovate[bot], 2025-11-03)
- `15f4f0c4266a` fix(deps): update dependency io.micronaut.micrometer:micronaut-micrometer-bom to v5.13.1 (#1241) (renovate[bot], 2025-11-03)
- `39f6aa3d82e0` fix(deps): update dependency io.micronaut.reactor:micronaut-reactor-bom to v3.9.1 (#1242) (renovate[bot], 2025-11-03)
- `b729f8afbe8b` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.6 (#1233) (renovate[bot], 2025-10-17)

### Security

- `e0f1516d9217` security: force upgrade jackson-core (Sergio del Amo, 2026-05-09)
- `0c8ca29d69aa` Infer SSL security protocol from ssl config (#1301) (Graeme Rocher, 2026-04-22)

### Dependency Updates

- `3a5ee8f9b380` chore: Bump version to 6.0.1-SNAPSHOT (micronaut-build, 2026-05-18)
- `b964ad8fb788` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2026-05-09)
- `4d83d3bb83fe` Update dependency io.micronaut:micronaut-core-bom to v5.0.0-M26 (#1353) (renovate[bot], 2026-05-01)
- `2ba8d5366698` Update Micronaut dependencies (#1342) (renovate[bot], 2026-04-29)
- `ebca0febc229` Update dependency org.lz4:lz4-java to v1.8.1 (renovate[bot], 2026-04-28)
- `079bc5e34536` Update dependency org.graalvm.sdk:graal-sdk to v25.0.3 (#1331) (renovate[bot], 2026-04-25)
- `bfab9859d1c3` Update dependency org.apache.groovy:groovy to v4.0.31 (#1325) (renovate[bot], 2026-04-24)
- `b4a78be56c34` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2026-04-22)
- `e0936211f91e` Upgrade to Kafka 4.1.1 (#1282) (Ayoub Bouria, 2026-02-23)
- `5806ed4893b3` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2026-01-22)
- `3915ab44931a` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#1245) (renovate[bot], 2025-12-10)
- `f1acf3a11602` chore(deps): update kotlin monorepo to v2.2.21 (#1244) (renovate[bot], 2025-12-10)
- `651180c0ad91` chore(deps): update softprops/action-gh-release action to v2.5.0 (#1246) (renovate[bot], 2025-12-10)
- `fb71092075d1` chore(deps): update gradle to v9.2.1 (#1247) (renovate[bot], 2025-12-10)
- `2e7a7cf5a6b9` chore(deps): update actions/checkout action to v6 (#1251) (renovate[bot], 2025-12-10)
- `44c0e412bdd7` chore(deps): update github artifact actions (#1252) (renovate[bot], 2025-12-10)
- `8b892d2e3239` chore(deps): update mikepenz/action-junit-report action to v6 (#1253) (renovate[bot], 2025-12-10)
- `3b41ef8fbaae` chore(deps): update graalvm/setup-graalvm action to v1.4.4 (#1256) (renovate[bot], 2025-12-10)
- `29086150402e` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m8 (#1239) (renovate[bot], 2025-11-03)
- `1aed2763200e` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#1237) (renovate[bot], 2025-11-03)

### Internal

- `2a9aec975bdc` Build: Update to Micronaut 5 (#1265) (issam liqali, 2026-01-22)
- `b4102fd7cff4` ci: projectVersion=6.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2024-04-11)

### Review Candidates

- `8a933ba97319` micronaut-tracing = "8.0.0" (Sergio del Amo, 2026-05-19)
- `c469f3e009b8` Update common files (#1364) (micronaut-build, 2026-05-19)
- `dadea212ffc7` micronaut-micrometer = "6.0.0" (Sergio del Amo, 2026-05-18)
- `ec9258df6ae5` [skip ci] Release v6.0.0 (micronaut-build, 2026-05-18)
- `5285a9c9238a` micronaut-test = "5.0.0" (Sergio del Amo, 2026-05-14)
- `8ff73cecbf9d` Update versions (Sergio del Amo, 2026-05-14)
- `7276ec3d723e` Update common files (#1363) (micronaut-build, 2026-05-14)
- `51d19704a8bd` micronaut-platform = "5.0.0-RC1" (Sergio del Amo, 2026-05-13)
- `3d56c12af75f` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `59f0c4af7fb0` Update common files (#1362) (micronaut-build, 2026-05-10)
- `fd66163ed065` [skip ci] Release v6.0.0-RC1 (micronaut-build, 2026-05-09)
- `f95cb754e0f6` git ignore .kotlin (Sergio del Amo, 2026-05-09)
- `04bce12b45f4` :micronaut-platform:5.0.0-M3 (Sergio del Amo, 2026-05-09)
- `2fb4e0ab9897` Update common files (#1361) (micronaut-build, 2026-05-09)
- `87f630b92d00` update to latest versions (Sergio del Amo, 2026-05-08)
- `1221bce3d671` Update common files (#1360) (micronaut-build, 2026-05-08)
- `09b4a3fbe6d5` git ignore .kotlin (Sergio del Amo, 2026-05-07)
- `4a1898683b38` update versions (Sergio del Amo, 2026-05-07)
- `b4a621c78771` Update common files (#1359) (micronaut-build, 2026-05-07)
- `9bcd2c4fc828` Update 6.0 release history (#1358) (Graeme Rocher, 2026-05-05)
- `1c47a2d8afcb` Align Kafka metrics with Micrometer naming (#1349) (Graeme Rocher, 2026-05-05)
- `ef16e0552a14` Document schema registry overrides for named clients (#1352) (Graeme Rocher, 2026-05-05)
- `45a8356fec90` Fix Kafka Streams SHUTDOWN_APPLICATION shutdown (#1351) (Graeme Rocher, 2026-05-05)
- `7a1ff2a66b76` Fix missing imports for compilation (#1357) (Graeme Rocher, 2026-05-05)
- `33bcfe46277d` [kafka] Update common files for branch 6.0.x (#1350) (micronaut-build, 2026-05-05)
- `4f42e78c1bdd` Default async KafkaClient methods to TaskExecutors.BLOCKING (#1354) (Graeme Rocher, 2026-05-05)
- `ef1e09714cc0` Update common files (#1345) (micronaut-build, 2026-04-29)
- `d3e7be540e69` Make AdminClient optional (#1343) (Graeme Rocher, 2026-04-29)
- `e0c0d0fb35d8` Document multiple Kafka Streams configuration (#1334) (Graeme Rocher, 2026-04-28)
- `23c7a18198a1` Fix recovery for expired transactional producers (#1328) (Graeme Rocher, 2026-04-28)
- `021da4de43a2` Fix Prometheus consumer metric tag stability (#1329) (Graeme Rocher, 2026-04-28)
- `5ababe049e8e` Merge pull request #1340 from micronaut-projects/renovate/org.lz4-lz4-java-1.x (Graeme Rocher, 2026-04-28)
- `0c77dd5fba17` Document same-topic multi-type Kafka listeners (#1337) (Graeme Rocher, 2026-04-28)
- `6877b3e0f412` Document runtime Kafka bootstrap configuration (#1332) (Graeme Rocher, 2026-04-28)
- `d043d3e0e5f8` Clarify SYNC_PER_RECORD commit behavior (#1330) (Graeme Rocher, 2026-04-28)
- `1786bde4849b` Change log level for Kafka offset commit errors when using CooperativeSticky assignment strategy (#1312) (Graeme Rocher, 2026-04-24)
- `516f6ceef35e` Clarify KafkaClient executor ordering with CompletableFuture (#1326) (Graeme Rocher, 2026-04-24)
- `fc8c95594c94` Fix Prometheus warnings from optional Kafka node-id tags (#1298) (Graeme Rocher, 2026-04-23)
- `5d6feb538563` Refactor tests to not use KafkaConsumer internals (#1322) (Graeme Rocher, 2026-04-23)
- `2a5e212b5013` Make null kafka config errors explicit (#1318) (Graeme Rocher, 2026-04-23)
- `0f0d4473f785` Fix Kafka Streams metric naming collisions (#1306) (Graeme Rocher, 2026-04-23)
- `d63e72ec5e3a` Fix batch deserialization seek with disabled offsets (#1300) (Graeme Rocher, 2026-04-22)
- `982e801a96d5` [skip ci] Release v6.0.0-M2 (micronaut-build, 2026-04-22)
- `db51b65d2dc7` Update common files (#1313) (micronaut-build, 2026-04-22)
- `2e52a6135e82` Update actions/cache digest to 27d5ce7 (#1319) (renovate[bot], 2026-04-22)
- `93625a977c91` Update actions/upload-artifact digest to 043fb46 (#1321) (renovate[bot], 2026-04-22)
- `fb5997ee2dc8` Implement graceful shutdown for Kafka consumers (#1314) (Graeme Rocher, 2026-04-21)
- `f57021802966` Fix multi-topic listener retry partition resets (#1307) (Graeme Rocher, 2026-04-21)
- `a09d08cc412a` Fix native-image Kafka consumer assignor reflection (#1311) (Graeme Rocher, 2026-04-21)
- `5f6283e66de6` Fix stale consumer records-lag meters (#1310) (Graeme Rocher, 2026-04-17)
- `58038b4ef145` Fix ConsumerState shutdown loop (#1308) (Graeme Rocher, 2026-04-17)
- `e3c5b8e1fe26` Fix Kafka metrics meter cleanup (#1303) (Graeme Rocher, 2026-04-16)
- `97274aaeaafa` Fix ConsumerStateBatch retry NPE when offsets are missing (#1309) (Graeme Rocher, 2026-04-16)
- `6b7afdd750d9` Update common files (#1297) (micronaut-build, 2026-04-13)
- `7c0679c2052d` Update micronaut to M20 and kafka 4.2.0 (#1296) (Issam Liqali, 2026-04-06)
- `3edce2663958` Update common files (#1287) (micronaut-build, 2026-04-03)
- `3516cf8f995b` use spock groovy from micronaut-test (#1286) (issam liqali, 2026-02-26)
- `1d49b5ed4f04` [kafka] Update common files for branch 6.0.x (#1261) (micronaut-build, 2026-02-26)
- `171fdb0b9de0` [skip ci] Release v6.0.0-M1 (micronaut-build, 2026-01-22)
- `c9318312c8a3` Update common files (#1243) (micronaut-build, 2025-12-10)
- `e9b6f7d388d2` Replace Micronaut nullability annotations with JSpecify nullability annotations (#1258) (Copilot, 2025-12-01)
- `a5f6d1d37e4d` Micronaut 5 compatibility (#1238) (issam liqali, 2025-11-03)
- `ad5c2a2c59cb` Update common files (#1234) (micronaut-build, 2025-11-03)
- `a0a8aab2ecf1` Update common files (#1231) (micronaut-build, 2025-10-17)
- `bd08e0f001c6` Micronaut Gralde build plugin 8.0.0-M4 (Sergio del Amo, 2025-10-15)
- `34df0cd88099` gradle 9.1 (Sergio del Amo, 2025-10-15)
- `5430d0dd6b95` Merge branch '5.10.x' into 6.0.x (Sergio del Amo, 2025-10-15)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` buildSrc/build.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.kafka-base.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.kafka-module.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.kafka-tests.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.internal.build.kafka-testsuite.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` kafka-streams/build.gradle
- `M` kafka/build.gradle
- `M` settings.gradle
- `M` test-suite-groovy/build.gradle.kts
- `A` test-suite-kafka-utils/build.gradle
- `M` test-suite-kotlin/build.gradle.kts
- `M` test-suite/build.gradle.kts
- `M` tests/tasks-sasl-plaintext/build.gradle

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
- `A` src/main/docs/guide/controlPanel.adoc
- `M` src/main/docs/guide/kafkaApplications/kafkaMetrics.adoc
- `M` src/main/docs/guide/kafkaClient/kafkaClientConfiguration.adoc
- `M` src/main/docs/guide/kafkaClient/kafkaClientMethods.adoc
- `M` src/main/docs/guide/kafkaListener.adoc
- `M` src/main/docs/guide/kafkaListener/kafkaErrors.adoc
- `M` src/main/docs/guide/kafkaListener/kafkaListenerConfiguration.adoc
- `M` src/main/docs/guide/kafkaListener/kafkaListenerMethods.adoc
- `A` src/main/docs/guide/kafkaListener/kafkaListenerScope.adoc
- `M` src/main/docs/guide/kafkaListener/kafkaOffsets.adoc
- `M` src/main/docs/guide/kafkaQuickStart.adoc
- `A` src/main/docs/guide/kafkaSerialization.adoc
- `M` src/main/docs/guide/kafkaStreams.adoc
- `M` src/main/docs/guide/kafkaStreams/kafkaStreamExceptions.adoc
- `M` src/main/docs/guide/releaseHistory.adoc
- `M` src/main/docs/guide/toc.yml
- `M` test-suite-groovy/src/test/groovy/io/micronaut/kafka/docs/AbstractKafkaTest.groovy
- `A` test-suite-groovy/src/test/groovy/io/micronaut/kafka/docs/KafkaProperties.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/kafka/docs/admin/MyTopicFactoryTest.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/kafka/docs/consumer/config/ConfigProductListenerTest.groovy
- `A` test-suite-groovy/src/test/groovy/io/micronaut/kafka/docs/consumer/scope/ProductListener.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/kafka/docs/consumer/sendto/SendToProductListenerTest.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/kafka/docs/consumer/sendto/WordCounterTest.groovy
- `A` test-suite-groovy/src/test/groovy/io/micronaut/kafka/docs/consumer/topics/FavoriteEventListener.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/kafka/docs/producer/inject/BookSenderTest.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/kafka/docs/quickstart/QuickStartTest.groovy
- `A` test-suite-groovy/src/test/groovy/io/micronaut/kafka/docs/quickstart/RuntimeBootstrapServers.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/kafka/docs/seek/aware/ConsumerSeekAwareSpec.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/kafka/docs/seek/ops/KafkaSeekOperationsSpec.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/kafka/docs/seek/rebalance/ConsumerRebalanceListenerSpec.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/kafka/docs/streams/WordCountStream.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/kafka/docs/streams/WordCountStreamTest.groovy
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/kafka/docs/AbstractKafkaTest.kt
- `A` test-suite-kotlin/src/test/kotlin/io/micronaut/kafka/docs/KafkaProperties.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/kafka/docs/KotlinCoroutinesTest.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/kafka/docs/MyTest.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/kafka/docs/admin/MyTopicFactoryTest.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/kafka/docs/consumer/config/ConfigProductListenerTest.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/kafka/docs/consumer/reactive/ProductListener.kt
- `A` test-suite-kotlin/src/test/kotlin/io/micronaut/kafka/docs/consumer/scope/ProductListener.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/kafka/docs/consumer/sendto/SendToProductListenerTest.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/kafka/docs/consumer/sendto/WordCounterTest.kt
- `A` test-suite-kotlin/src/test/kotlin/io/micronaut/kafka/docs/consumer/topics/FavoriteEventListener.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/kafka/docs/producer/inject/BookSenderTest.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/kafka/docs/producer/methods/BookClient.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/kafka/docs/quickstart/QuickstartTest.kt
- `A` test-suite-kotlin/src/test/kotlin/io/micronaut/kafka/docs/quickstart/RuntimeBootstrapServers.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/kafka/docs/seek/aware/ConsumerSeekAwareTest.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/kafka/docs/seek/ops/KafkaSeekOperationsTest.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/kafka/docs/seek/rebalance/ConsumerRebalanceListenerTest.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/kafka/docs/seek/rebalance/ProductListener.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/kafka/docs/streams/WordCountStream.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/kafka/docs/streams/WordCountStreamTest.kt
- `D` test-suite/src/test/java/io/micronaut/kafka/docs/AbstractKafkaTest.java
- `M` test-suite/src/test/java/io/micronaut/kafka/docs/MyTest.java
- `M` test-suite/src/test/java/io/micronaut/kafka/docs/admin/MyTopicFactoryTest.java
- `M` test-suite/src/test/java/io/micronaut/kafka/docs/consumer/config/ConfigProductListenerTest.java
- `A` test-suite/src/test/java/io/micronaut/kafka/docs/consumer/scope/ProductListener.java
- `M` test-suite/src/test/java/io/micronaut/kafka/docs/consumer/sendto/SendToProductListenerTest.java
- `M` test-suite/src/test/java/io/micronaut/kafka/docs/consumer/sendto/WordCounterTest.java
- `A` test-suite/src/test/java/io/micronaut/kafka/docs/consumer/topics/FavoriteEventListener.java
- `M` test-suite/src/test/java/io/micronaut/kafka/docs/producer/inject/BookSenderTest.java
- `M` test-suite/src/test/java/io/micronaut/kafka/docs/quickstart/QuickstartTest.java
- `A` test-suite/src/test/java/io/micronaut/kafka/docs/quickstart/RuntimeBootstrapServers.java
- `M` test-suite/src/test/java/io/micronaut/kafka/docs/seek/aware/ConsumerSeekAwareTest.java
- `M` test-suite/src/test/java/io/micronaut/kafka/docs/seek/aware/ProductListener.java
- `M` test-suite/src/test/java/io/micronaut/kafka/docs/seek/ops/KafkaSeekOperationsTest.java
- `M` test-suite/src/test/java/io/micronaut/kafka/docs/seek/ops/ProductListener.java
- `M` test-suite/src/test/java/io/micronaut/kafka/docs/seek/rebalance/ConsumerRebalanceListenerTest.java
- `M` test-suite/src/test/java/io/micronaut/kafka/docs/seek/rebalance/ProductListener.java
- `M` test-suite/src/test/java/io/micronaut/kafka/docs/streams/WordCountStream.java
- `M` test-suite/src/test/java/io/micronaut/kafka/docs/streams/WordCountStreamTest.java

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
- `M` MAINTAINING.md
- `A` buildSrc/AGENTS.md
- `M` config/checkstyle/checkstyle.xml
- `A` kafka-streams/AGENTS.md
- `M` kafka-streams/src/main/java/io/micronaut/configuration/kafka/streams/AbstractKafkaStreamsConfiguration.java
- `M` kafka-streams/src/main/java/io/micronaut/configuration/kafka/streams/ConfiguredStreamBuilder.java
- `M` kafka-streams/src/main/java/io/micronaut/configuration/kafka/streams/DefaultKafkaStreamsConfiguration.java
- `M` kafka-streams/src/main/java/io/micronaut/configuration/kafka/streams/KafkaStreamsConfiguration.java
- `M` kafka-streams/src/main/java/io/micronaut/configuration/kafka/streams/KafkaStreamsFactory.java
- `M` kafka-streams/src/main/java/io/micronaut/configuration/kafka/streams/health/KafkaStreamsHealth.java
- `M` kafka-streams/src/main/java/io/micronaut/configuration/kafka/streams/health/serde/TaskIdSerde.java
- `M` kafka-streams/src/main/java/io/micronaut/configuration/kafka/streams/metrics/KafkaStreamsMetricsReporter.java
- `A` kafka/AGENTS.md
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/ConsumerAware.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/ConsumerRegistry.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/ConsumerSeekAware.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/DefaultProducerFactory.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/KafkaConsumerFactory.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/KafkaHeaders.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/KafkaMessage.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/KafkaProducerFactory.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/ProducerFactory.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/ProducerRegistry.java
- `A` kafka/src/main/java/io/micronaut/configuration/kafka/RecoveringTransactionalProducer.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/TransactionalProducerRegistry.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/admin/AdminClientFactory.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/admin/KafkaNewTopics.java
- `A` kafka/src/main/java/io/micronaut/configuration/kafka/annotation/ConsumerCreationStrategy.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/annotation/ErrorStrategy.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/annotation/ErrorStrategyValue.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/annotation/KafkaClient.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/annotation/KafkaKey.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/annotation/KafkaListener.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/annotation/KafkaPartition.java
- `A` kafka/src/main/java/io/micronaut/configuration/kafka/annotation/KafkaScope.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/annotation/KafkaTimestamp.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/annotation/Topic.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/annotation/Topics.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/config/AbstractKafkaConfiguration.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/config/AbstractKafkaConsumerConfiguration.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/config/AbstractKafkaProducerConfiguration.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/config/KafkaDefaultConfiguration.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/exceptions/DefaultKafkaListenerExceptionHandler.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/exceptions/KafkaListenerException.java
- `A` kafka/src/main/java/io/micronaut/configuration/kafka/exceptions/OffsetCommitExceptionLogger.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/health/DefaultNetworkClientCreator.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/health/KafkaHealthIndicator.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/health/NetworkClientCreator.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/intercept/KafkaClientIntroductionAdvice.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/metrics/AbstractKafkaMetrics.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/metrics/AbstractKafkaMetricsReporter.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/metrics/ConsumerKafkaMetricsReporter.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/metrics/KafkaConsumerMetrics.java
- `A` kafka/src/main/java/io/micronaut/configuration/kafka/metrics/KafkaMetricsConfigurationProperties.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/metrics/KafkaProducerMetrics.java
- `A` kafka/src/main/java/io/micronaut/configuration/kafka/metrics/MetricNameStyle.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/metrics/ProducerKafkaMetricsReporter.java
- `A` kafka/src/main/java/io/micronaut/configuration/kafka/metrics/PrometheusRegistryUtils.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/metrics/builder/KafkaMetricMeterType.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/metrics/builder/KafkaMetricMeterTypeBuilder.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/processor/ConsumerInfo.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/processor/ConsumerSeekAwareAdapter.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/processor/ConsumerState.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/processor/ConsumerStateBatch.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/processor/ConsumerStateSingle.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/processor/KafkaConsumerProcessor.java
- `A` kafka/src/main/java/io/micronaut/configuration/kafka/processor/TopicAwareDeserializer.java
- `A` kafka/src/main/java/io/micronaut/configuration/kafka/processor/TopicRouter.java
- `A` kafka/src/main/java/io/micronaut/configuration/kafka/scope/KafkaCustomScope.java
- `A` kafka/src/main/java/io/micronaut/configuration/kafka/scope/package-info.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/seek/DefaultKafkaSeekOperation.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/seek/DefaultKafkaSeekOperations.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/seek/DefaultKafkaSeeker.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/seek/KafkaSeekOperation.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/seek/KafkaSeekOperations.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/seek/KafkaSeeker.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/serde/CompositeSerdeRegistry.java
- `M` kafka/src/main/java/io/micronaut/configuration/kafka/tracing/brave/BraveKafkaTracingFactory.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` kafka-streams/src/test/groovy/io/micronaut/configuration/kafka/streams/AbstractKafkaContainerSpec.groovy
- `M` kafka-streams/src/test/groovy/io/micronaut/configuration/kafka/streams/AbstractTestContainersSpec.groovy
- `A` kafka-streams/src/test/groovy/io/micronaut/configuration/kafka/streams/GlobalKTableOnlySpec.groovy
- `A` kafka-streams/src/test/groovy/io/micronaut/configuration/kafka/streams/KafkaStreamsConfigurationSpec.groovy
- `A` kafka-streams/src/test/groovy/io/micronaut/configuration/kafka/streams/KafkaStreamsDisabledSpec.groovy
- `M` kafka-streams/src/test/groovy/io/micronaut/configuration/kafka/streams/KafkaStreamsFactorySpec.groovy
- `M` kafka-streams/src/test/groovy/io/micronaut/configuration/kafka/streams/KafkaTestInitializer.java
- `M` kafka-streams/src/test/groovy/io/micronaut/configuration/kafka/streams/UncaughtExceptionsSpec.groovy
- `A` kafka-streams/src/test/groovy/io/micronaut/configuration/kafka/streams/health/KafkaStreamsHealthTaskMetadataSpec.groovy
- `M` kafka-streams/src/test/groovy/io/micronaut/configuration/kafka/streams/metrics/KafkaStreamsMetricsDisabledSpec.groovy
- `A` kafka-streams/src/test/groovy/io/micronaut/configuration/kafka/streams/metrics/KafkaStreamsMetricsReporterSpec.groovy
- `M` kafka-streams/src/test/groovy/io/micronaut/configuration/kafka/streams/metrics/KafkaStreamsMetricsSpec.groovy
- `M` kafka-streams/src/test/groovy/io/micronaut/configuration/kafka/streams/optimization/OptimizationStream.java
- `M` kafka-streams/src/test/groovy/io/micronaut/configuration/kafka/streams/startkafkastreams/StartKafkaStreamsOff.java
- `M` kafka-streams/src/test/groovy/io/micronaut/configuration/kafka/streams/uncaught/OnErrorStreamFactory.java
- `M` kafka-streams/src/test/groovy/io/micronaut/configuration/kafka/streams/wordcount/WordCountStream.java
- `M` kafka/src/test/groovy/io/micronaut/configuration/kafka/AbstractKafkaContainerSpec.groovy
- `M` kafka/src/test/groovy/io/micronaut/configuration/kafka/KafkaConfigurationSpec.groovy
- `A` kafka/src/test/groovy/io/micronaut/configuration/kafka/KafkaConsumerFactoryTypeHintSpec.groovy
- `A` kafka/src/test/groovy/io/micronaut/configuration/kafka/KafkaListenerIdSpec.groovy
- `M` kafka/src/test/groovy/io/micronaut/configuration/kafka/KafkaTxSpec.groovy
- `A` kafka/src/test/groovy/io/micronaut/configuration/kafka/annotation/ConsumerCreationStrategySpec.groovy
- `M` kafka/src/test/groovy/io/micronaut/configuration/kafka/annotation/KafkaClientWithExecutorSpec.groovy
- `M` kafka/src/test/groovy/io/micronaut/configuration/kafka/annotation/KafkaConsumerAutoStartupSpec.groovy
- `A` kafka/src/test/groovy/io/micronaut/configuration/kafka/annotation/KafkaGracefulShutdownSpec.groovy
- `M` kafka/src/test/groovy/io/micronaut/configuration/kafka/annotation/KafkaListenerSpec.groovy
- `M` kafka/src/test/groovy/io/micronaut/configuration/kafka/errors/KafkaBatchErrorStrategySpec.groovy
- `M` kafka/src/test/groovy/io/micronaut/configuration/kafka/errors/KafkaErrorStrategySpec.groovy
- `M` kafka/src/test/groovy/io/micronaut/configuration/kafka/event/KafkaConsumerEventSpec.groovy
- `A` kafka/src/test/groovy/io/micronaut/configuration/kafka/exceptions/DefaultKafkaListenerExceptionHandlerLoggingSpec.groovy
- `M` kafka/src/test/groovy/io/micronaut/configuration/kafka/exceptions/DefaultKafkaListenerExceptionHandlerSpec.groovy
- `A` kafka/src/test/groovy/io/micronaut/configuration/kafka/exceptions/OffsetCommitExceptionLoggerSpec.groovy
- `M` kafka/src/test/groovy/io/micronaut/configuration/kafka/health/KafkaConsumerMetricsSpec.groovy
- `M` kafka/src/test/groovy/io/micronaut/configuration/kafka/health/KafkaHealthIndicatorSpec.groovy
- `M` kafka/src/test/groovy/io/micronaut/configuration/kafka/health/KafkaProducerMetricsSpec.groovy
- `M` kafka/src/test/groovy/io/micronaut/configuration/kafka/health/RestrictedKafkaHealthIndicatorSpec.groovy
- `A` kafka/src/test/groovy/io/micronaut/configuration/kafka/metrics/AbstractKafkaMetricsReporterSpec.groovy
- `A` kafka/src/test/groovy/io/micronaut/configuration/kafka/metrics/KafkaMetricsConfigurationSpec.groovy
- `M` kafka/src/test/groovy/io/micronaut/configuration/kafka/metrics/builder/KafkaMetricMeterTypeBuilderSpec.groovy
- `M` kafka/src/test/groovy/io/micronaut/configuration/kafka/offsets/PerRecordOffsetCommitSpec.groovy
- `A` kafka/src/test/groovy/io/micronaut/configuration/kafka/processor/ConsumerCreationStrategyStateSpec.groovy
- `A` kafka/src/test/groovy/io/micronaut/configuration/kafka/processor/ConsumerCreationStrategySupportSpec.groovy
- `A` kafka/src/test/groovy/io/micronaut/configuration/kafka/processor/ConsumerStateBatchSpec.groovy
- `A` kafka/src/test/groovy/io/micronaut/configuration/kafka/processor/ConsumerStateSingleSpec.groovy
- `A` kafka/src/test/groovy/io/micronaut/configuration/kafka/processor/ConsumerStateSpec.groovy
- `A` kafka/src/test/groovy/io/micronaut/configuration/kafka/processor/InvalidPatternPerClassListener.groovy
- `A` kafka/src/test/groovy/io/micronaut/configuration/kafka/processor/KafkaConsumerProcessorGracefulShutdownSpec.groovy
- `A` kafka/src/test/groovy/io/micronaut/configuration/kafka/processor/KafkaScopeConsumerStateSpec.groovy
- `A` kafka/src/test/groovy/io/micronaut/configuration/kafka/processor/MethodTopicOverridesClassTopicListener.groovy
- `A` kafka/src/test/groovy/io/micronaut/configuration/kafka/processor/TestBatchMultiTopicListener.groovy
- `A` kafka/src/test/groovy/io/micronaut/configuration/kafka/processor/TestPerClassMultiTopicBatchListener.groovy
- `A` kafka/src/test/groovy/io/micronaut/configuration/kafka/processor/TestPerClassMultiTopicListener.groovy
- `A` kafka/src/test/groovy/io/micronaut/configuration/kafka/scope/KafkaScopeSpec.groovy
- `M` kafka/src/test/groovy/io/micronaut/configuration/kafka/seek/ConsumerSeekAwareSpec.groovy
- `A` kafka/src/test/java/io/micronaut/configuration/kafka/RecoveringTransactionalProducerTest.java
- `A` kafka/src/test/java/io/micronaut/configuration/kafka/TransactionalProducerExpirationReproducerTest.java
- `A` kafka/src/test/java/io/micronaut/configuration/kafka/processor/ConsumerStateSpecListener.java
- `A` test-suite-kafka-utils/src/main/java/io/micronaut/testcontainers/kafka/Kafka.java
- `M` test-suite/src/test/resources/logback.xml
- `M` tests/tasks-sasl-plaintext/src/test/java/example/TasksTest.java
- `A` tests/tasks-sasl-plaintext/src/test/resources/META-INF/native-image/reflect-config.json
- `R100` tests/tasks-sasl-plaintext/src/test/resources/kafka_server_jaas.conf
- `M` tests/tasks-sasl-plaintext/src/testResources/resources/application.yml

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

