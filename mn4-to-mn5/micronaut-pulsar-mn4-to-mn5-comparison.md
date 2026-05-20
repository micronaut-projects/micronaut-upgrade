• Generated the comparison report here:

  micronaut-pulsar-mn4-to-mn5-comparison.md:1

  Scope: mn4 previous is 2.7.x at 394e7753c15b, clean. mn5 current is 3.0.x at 0a2c2f8ee563, clean. The comparison found 78 commit candidates and 93 changed files.

  Release-note draft:

  ## Micronaut Pulsar 3.0

  ### Compatibility

  - Updated for the Micronaut 5 baseline.
  - Updated Apache Pulsar Java client from `3.3.9` to `4.2.1`.
  - Replaced Micronaut nullability annotations with JSpecify annotations across Pulsar APIs.

  ### Features

  - Added Pulsar client proxy support hooks. When a proxy URL is supplied through `PulsarClientConfiguration`, the client builder applies `proxyServiceUrl`, defaulting the proxy protocol to `SNI`.
  - Updated Protobuf schema handling to use schema metadata compatible with the newer Pulsar/protobuf stack.

  ### Documentation

  - Moved Java, Groovy, and Kotlin documentation examples from test sources to main sources and updated snippets accordingly.

  ### Internal / Build

  - Updated Gradle from `8.14.3` to `9.5.0`.
  - Updated the Micronaut build shared settings plugin from `7.6.4` to `8.0.0-M18`.
  - Converted `pulsar-multitenant` build configuration to Kotlin DSL.

  Key version changes:

  - Project version: 2.7.1-SNAPSHOT -> 3.0.0-SNAPSHOT
  - Micronaut Core: 4.10.4 -> 5.0.0-RC2
  - Apache Pulsar Java client: 3.3.9 -> 4.2.1
  - Micronaut gRPC: 4.12.0 -> 5.0.0-RC1
  - Micronaut Multitenancy: 5.8.0 -> 6.0.0-RC1
  - Micronaut Reactor: 3.9.0 -> 4.0.0-RC1
  - Micronaut Serialization: 2.15.5 -> 3.0.0-RC2
  - Micronaut Validation: 4.11.0 -> 5.0.0-RC2

  I did not run tests; this is a static git/filesystem comparison.

# Release Note Comparison

Generated: 2026-05-07 09:42 UTC
Comparison: `mn4` -> `mn5`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-pulsar` | `2.7.x` | `394e7753c15b` | `git@github.com:micronaut-projects/micronaut-pulsar.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-pulsar` | `3.0.x` | `0a2c2f8ee563` | `git@github.com:micronaut-projects/micronaut-pulsar.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-pulsar`
- Commit candidates found: 78
- File changes listed: 93
- Version values listed: 26
- File status counts: A=20, D=3, M=58, R=12

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `2.7.1-SNAPSHOT` | `3.0.0-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.conscrypt-openjdk` | `org.conscrypt:conscrypt-openjdk-uber:2.5.2` | `org.conscrypt:conscrypt-openjdk-uber (version.ref=conscrypt-openjdk)` | `changed` |
| `gradle/libs.versions.toml` | `libraries.gradle-kotlin` | `org.jetbrains.kotlin:kotlin-gradle-plugin:2.1.21` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.gradle-micronaut` | `io.micronaut.gradle:micronaut-gradle-plugin (version.ref=micronaut-gradle-plugin)` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-docs` | `io.micronaut.docs:micronaut-docs-asciidoc-config-props (version.ref=micronaut-docs)` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-grpc` | `io.micronaut.grpc:micronaut-grpc-bom:4.12.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-multitenancy` | `io.micronaut.multitenancy:micronaut-multitenancy-bom:5.8.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-reactor` | `io.micronaut.reactor:micronaut-reactor-bom:3.9.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.15.5` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-resources` | `io.micronaut.testresources:micronaut-test-resources-bom:2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-validation` | `io.micronaut.validation:micronaut-validation-bom:4.11.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.conscrypt-openjdk` | `2.5.2` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.22` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.kotlin` | `2.1.21` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.4` | `5.0.0-RC2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-grpc` | `4.12.0` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-multitenancy` | `5.8.0` | `6.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-reactor` | `3.9.0` | `4.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.15.5` | `3.0.0-RC2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.9.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test-resources` | `2.10.1` | `4.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.11.0` | `5.0.0-RC2` | `changed` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.0` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `9607fe875fdf` remove unused kotest-runner version (Sergio del Amo, 2026-05-07)
- `a4247d51e529` Removed the Spock version force configuration from build (#784) (Issam Liqali, 2026-03-12)

### Fixes

- `160b8bb42691` fix(deps): update dependency io.kotest:kotest-runner-junit5 to v6 (#754) (renovate[bot], 2026-05-02)
- `f9fcc5550a7d` fix(deps): update dependency com.fasterxml.jackson.core:jackson-core to v2.21.3 (#789) (renovate[bot], 2026-05-02)
- `36b771421d37` fix(deps): update dependency io.grpc:protoc-gen-grpc-java to v1.81.0 (#788) (renovate[bot], 2026-05-02)
- `e981d9a0a196` fix(deps): update dependency io.airlift:aircompressor to v2.0.3 (#778) (renovate[bot], 2026-05-02)
- `43e9bb0dc1c2` fix(deps): update dependency org.asynchttpclient:async-http-client to v3.0.9 (#793) (renovate[bot], 2026-05-02)
- `2f9a497a450e` fix(deps): update protobuf monorepo to v4.34.1 (#790) (renovate[bot], 2026-05-02)
- `ceeffff15af4` fix(deps): update netty monorepo to v4.2.12.final (#780) (renovate[bot], 2026-05-02)
- `c2ba339b47dd` fix(deps): update dependency com.google.code.gson:gson to v2.14.0 (#799) (renovate[bot], 2026-05-01)
- `d21bb626bec2` fix(deps): update micronaut dependencies (#796) (renovate[bot], 2026-05-01)
- `71f32bfdca86` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m20 (#786) (renovate[bot], 2026-04-10)
- `7f76141cc9b7` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m16 (#782) (renovate[bot], 2026-03-12)
- `bb3205225b58` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m15 (#781) (renovate[bot], 2026-03-05)
- `59e597052d0c` fix(deps): update dependency org.apache.pulsar:pulsar-client-original to v4.1.3 (#779) (renovate[bot], 2026-03-05)
- `b5a5a38a6366` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m14 (#766) (renovate[bot], 2026-03-02)
- `626640da8263` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m2 (#770) (renovate[bot], 2026-03-01)
- `dcbcf823d8e9` fix(deps): update dependency com.fasterxml.jackson.core:jackson-core to v2.21.1 (#772) (renovate[bot], 2026-02-28)
- `0aa6cae79e4e` fix(deps): update dependency io.grpc:protoc-gen-grpc-java to v1.79.0 (#776) (renovate[bot], 2026-02-28)
- `af3969d2d525` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.2 (#773) (renovate[bot], 2026-02-28)
- `4d2604945008` fix(deps): update dependency org.asynchttpclient:async-http-client to v3.0.7 (#767) (renovate[bot], 2026-02-28)
- `d2c298cfd5e4` fix(deps): update protobuf monorepo to v4.34.0 (#747) (renovate[bot], 2026-02-28)
- `b44c76a3d4aa` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.10 (#761) (renovate[bot], 2025-12-15)
- `4928169241a8` fix(deps): update dependency org.asynchttpclient:async-http-client to v3.0.4 (#758) (renovate[bot], 2025-12-10)
- `b85463c137ae` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#748) (renovate[bot], 2025-12-10)
- `db138f05676d` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.12.0 (#749) (renovate[bot], 2025-12-10)
- `da0e103521ff` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#750) (renovate[bot], 2025-12-10)
- `83da635cabf5` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.8 (#738) (renovate[bot], 2025-11-03)
- `692712d33310` fix(deps): update dependency io.micronaut.reactor:micronaut-reactor-bom to v3.9.1 (#739) (renovate[bot], 2025-11-03)
- `45f5dacbc24d` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.6 (#733) (renovate[bot], 2025-10-17)
- `2d033cc72391` fix(deps): update dependency org.apache.pulsar:pulsar-client-original to v4 (#597) (renovate[bot], 2024-11-06)

### Dependency Updates

- `e4b8418bd7d4` chore(deps): update gradle to v9.5.0 (#783) (renovate[bot], 2026-05-01)
- `b607f8f7018b` chore(deps): update plugin com.google.protobuf to v0.10.0 (#797) (renovate[bot], 2026-05-01)
- `cf6659b4e0b7` chore: Bump version to 3.0.0-SNAPSHOT (micronaut-build, 2026-04-22)
- `554ad716a4c3` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#765) (renovate[bot], 2026-03-02)
- `cc4482380835` chore(deps): update graalvm/setup-graalvm action to v1.4.5 (#769) (renovate[bot], 2026-02-28)
- `a1e6b20792c5` chore(deps): update github artifact actions (#768) (renovate[bot], 2026-02-28)
- `f09550d33d53` chore(deps): update gradle to v9.3.1 (#771) (renovate[bot], 2026-02-28)
- `9f41f7be6f93` chore(deps): update plugin com.google.protobuf to v0.9.6 (#775) (renovate[bot], 2026-02-28)
- `e819149b238f` bump pulsar client to 4.1.2, add proxy sni support (#774) (Haris Secic, 2026-02-28)
- `073f72ce7d68` chore: Bump version to 3.0.0-SNAPSHOT (micronaut-build, 2025-12-15)
- `87a51d8db172` chore(deps): update actions/cache action to v5 (#762) (renovate[bot], 2025-12-15)
- `a4b4c4630087` chore(deps): update gradle to v9.2.1 (#746) (renovate[bot], 2025-12-10)
- `f3fff506adf7` chore(deps): update actions/checkout action to v6 (#751) (renovate[bot], 2025-12-10)
- `dfd07e6e177d` chore(deps): update graalvm/setup-graalvm action to v1.4.4 (#752) (renovate[bot], 2025-12-10)
- `270e06ffcc92` chore(deps): update softprops/action-gh-release action to v2.5.0 (#757) (renovate[bot], 2025-12-10)
- `7a70748de33b` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#753) (renovate[bot], 2025-12-10)
- `edced29f3a2b` chore(deps): update softprops/action-gh-release action to v2.4.2 (#742) (renovate[bot], 2025-11-12)
- `9e2a8410e6c8` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#736) (renovate[bot], 2025-11-03)
- `5c0984a6ff7d` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m8 (#737) (renovate[bot], 2025-11-03)

### Internal

- `7f03ec473d27` Build: Update to Micronaut 5 (#763) (issam liqali, 2025-12-15)
- `7c3fe213f0c4` ci: projectVersion=3.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2024-11-06)

### Review Candidates

- `0a2c2f8ee563` remvoe constraints (Sergio del Amo, 2026-05-07)
- `8b992bb2e5cc` update pulsar client to 4.2.1 (Sergio del Amo, 2026-05-07)
- `e9f645573700` use grpc and protobuf versions from grpc (Sergio del Amo, 2026-05-07)
- `cbdaebd30ef1` use kotlin gradle dsl (Sergio del Amo, 2026-05-07)
- `03139668a26c` move docs-examples sources to src/main (Sergio del Amo, 2026-05-07)
- `f5db8f1ee4ca` testcontainers artifact id prefix (Sergio del Amo, 2026-05-07)
- `ada4b0f8e533` use protobuf.java from grpc (Sergio del Amo, 2026-05-07)
- `f9a4ade14dd2` update to latest versions (Sergio del Amo, 2026-05-07)
- `a8f80460cd40` Update common files (#800) (micronaut-build, 2026-05-07)
- `f6d9c0e76286` [pulsar] Update common files for branch 3.0.x (#798) (micronaut-build, 2026-05-02)
- `b3051ca47c54` Update common files (#785) (micronaut-build, 2026-04-26)
- `0074896a8bec` [skip ci] Release v3.0.0-M2 (micronaut-build, 2026-04-22)
- `69d3495a4940` Update common files (#764) (micronaut-build, 2026-03-12)
- `d23f9f66750d` fix #699 #685, build cleanup (#743) (Haris Secic, 2026-02-17)
- `4ff88d0abaa7` test switch form hostname skip verify to allow insecure (#744) (Haris Secic, 2026-02-17)
- `8853bb5b13fe` [skip ci] Release v3.0.0-M1 (micronaut-build, 2025-12-15)
- `4d837139d303` Merge branch '2.7.x' into 3.0.x (Sergio del Amo, 2025-12-15)
- `5af41e63a221` Update common files (#745) (micronaut-build, 2025-12-10)
- `ecc7bde8eb3d` Replace Micronaut nullability annotations with JSpecify (#756) (Copilot, 2025-12-02)
- `f23fa1b7d016` Update common files (#741) (micronaut-build, 2025-11-12)
- `ec1403138f3a` Micronaut 5 compatibility (#735) (issam liqali, 2025-11-06)
- `a848902ee105` Update common files (#734) (micronaut-build, 2025-11-03)
- `5ca82545da9a` Update common files (#732) (micronaut-build, 2025-10-17)
- `37fc88e16552` micronaut build Gradle plugin 8.0.0-M4 (Sergio del Amo, 2025-10-15)
- `dd3b52131101` gradle 9.1 (Sergio del Amo, 2025-10-15)
- `abf09192100c` Merge branch '2.7.x' into 3.0.x (Sergio del Amo, 2025-10-15)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` build.gradle
- `M` buildSrc/build.gradle
- `A` buildSrc/src/main/groovy/io.micronaut.build.internal.pulsar-example.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.pulsar-module.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.pulsar-multitenant-module.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.test-pulsar-module.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `D` pulsar-multitenant/build.gradle
- `A` pulsar-multitenant/build.gradle.kts
- `M` pulsar/build.gradle
- `M` settings.gradle
- `M` test-suite/test-pulsar-module/build.gradle

### Documentation

- `A` .agents/skills/docs/SKILL.md
- `A` .agents/skills/docs/references/control-panel-patterns.md
- `A` .agents/skills/docs/references/micronaut-docs-providers.md
- `M` .github/workflows/release.yml
- `M` doc-examples/example-groovy/build.gradle
- `R100` doc-examples/example-groovy/src/main/groovy/example/ConsumerProducer.groovy
- `R100` doc-examples/example-groovy/src/main/groovy/example/Producer.groovy
- `R100` doc-examples/example-groovy/src/main/groovy/example/ReaderExample.groovy
- `R097` doc-examples/example-groovy/src/main/resources/logback.xml
- `M` doc-examples/example-java/build.gradle
- `R100` doc-examples/example-java/src/main/java/example/ConsumerProducer.java
- `R100` doc-examples/example-java/src/main/java/example/Producer.java
- `R100` doc-examples/example-java/src/main/java/example/ReaderExample.java
- `R097` doc-examples/example-java/src/main/resources/logback.xml
- `M` doc-examples/example-kotlin/build.gradle
- `R100` doc-examples/example-kotlin/src/main/kotlin/example/ConsumerProducer.kt
- `R100` doc-examples/example-kotlin/src/main/kotlin/example/Producer.kt
- `R100` doc-examples/example-kotlin/src/main/kotlin/example/ReaderExample.kt
- `R097` doc-examples/example-kotlin/src/main/resources/logback.xml
- `M` src/main/docs/guide/consumer.adoc
- `M` src/main/docs/guide/producer.adoc
- `M` src/main/docs/guide/reader.adoc

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
- `M` config/checkstyle/checkstyle.xml
- `M` pulsar-multitenant/src/main/java/io/micronaut/pulsar/events/PulsarTenantDiscoveredEvent.java
- `M` pulsar-multitenant/src/main/java/io/micronaut/pulsar/intercept/PulsarMultitenantProducerAdvice.java
- `M` pulsar-multitenant/src/main/java/io/micronaut/pulsar/processor/PulsarMultiTenantConsumerProcessor.java
- `M` pulsar/src/main/java/io/micronaut/pulsar/MessageSchema.java
- `M` pulsar/src/main/java/io/micronaut/pulsar/PulsarClientFactory.java
- `M` pulsar/src/main/java/io/micronaut/pulsar/PulsarConsumerRegistry.java
- `M` pulsar/src/main/java/io/micronaut/pulsar/PulsarProducerFactory.java
- `M` pulsar/src/main/java/io/micronaut/pulsar/PulsarProducerRegistry.java
- `M` pulsar/src/main/java/io/micronaut/pulsar/PulsarReaderFactory.java
- `M` pulsar/src/main/java/io/micronaut/pulsar/annotation/MessageKey.java
- `M` pulsar/src/main/java/io/micronaut/pulsar/annotation/MessageProperties.java
- `M` pulsar/src/main/java/io/micronaut/pulsar/annotation/PulsarReader.java
- `M` pulsar/src/main/java/io/micronaut/pulsar/config/AbstractPulsarConfiguration.java
- `M` pulsar/src/main/java/io/micronaut/pulsar/config/DefaultPulsarClientConfiguration.java
- `M` pulsar/src/main/java/io/micronaut/pulsar/config/PulsarClientConfiguration.java
- `M` pulsar/src/main/java/io/micronaut/pulsar/intercept/PulsarProducerAdvice.java
- `M` pulsar/src/main/java/io/micronaut/pulsar/processor/DefaultSchemaHandler.java
- `M` pulsar/src/main/java/io/micronaut/pulsar/processor/PulsarArgumentHandler.java
- `M` pulsar/src/main/java/io/micronaut/pulsar/processor/PulsarConsumerProcessor.java
- `M` pulsar/src/main/java/io/micronaut/pulsar/processor/TopicResolver.java
- `M` pulsar/src/main/java/io/micronaut/pulsar/schemas/protobuf/ProtobufSchema.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` test-suite/test-pulsar-module/src/test/groovy/io/micronaut/pulsar/PulsarConfigurationTest.groovy
- `M` test-suite/test-pulsar-module/src/test/groovy/io/micronaut/pulsar/PulsarSchemaSpec.groovy
- `M` test-suite/test-pulsar-module/src/test/groovy/io/micronaut/pulsar/TlsAwareClientTest.groovy
- `D` test-suite/test-pulsar-module/src/test/java/io/micronaut/pulsar/ProtoMessages.java
- `A` test-suite/test-pulsar-module/src/test/proto/message.proto
- `D` test-suite/test-pulsar-module/src/test/protobuf/message.proto
- `M` test-suite/test-pulsar-shared-module/src/main/groovy/io/micronaut/pulsar/shared/PulsarTls.groovy

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

