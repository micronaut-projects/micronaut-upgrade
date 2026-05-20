Compared micronaut-rabbitmq as mn4 → mn5.

  Scope

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-rabbitmq, branch 4.9.x, SHA cc426a2
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-rabbitmq, branch 5.0.x, SHA 37aa7ec
  - Report: /private/tmp/micronaut-rabbitmq-4.9-to-5.0-comparison.md

  Key Findings

  - projectVersion moves from 4.9.0-SNAPSHOT to 5.0.1-SNAPSHOT.
  - Core platform moves to Micronaut 5.0.0; Gradle wrapper moves 8.14.3 → 9.5.1; Java 25.0.1-graal is added
    via .sdkmanrc.
  - RabbitMQ Java client moves 5.26.0 → 5.30.0.
  - Micrometer moves 5.13.0 → 6.0.0; Serde moves 2.15.5 → 3.0.0; Micronaut Test moves 4.9.0 → 5.0.0.
  - Caffeine is now brought through the Micronaut Cache BOM, adding micronaut-cache 6.0.0.
  - Deprecated APIs were removed and documented: RabbitMessageCloseable.withAcknowledge(Boolean), old
    RabbitConnectionFactory.connection(...), old RabbitMQConsumerAdvice constructor, and old RabbitPublishState
    constructor.
  - Nullability annotations moved from Micronaut annotations to JSpecify.
  - Connection recovery now also treats SocketTimeoutException like ConnectException for temporary-down
    automatic recovery handling.
  - Test resources usage was removed in favor of direct Testcontainers RabbitMQ support via a new test-suite-
    utils helper module.
  - CI/release common files were refreshed, including Java 25 CI and OSV/CycloneDX vulnerability audit scripts.

  Diff size: 135 files changed, 4610 insertions, 749 deletions. I did not run tests; this was a folder
  comparison only.


# Release Note Comparison

Generated: 2026-05-19 09:59 UTC
Comparison: `4.9.x` -> `5.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-rabbitmq` | `4.9.x` | `cc426a253f49` | `git@github.com:micronaut-projects/micronaut-rabbitmq.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-rabbitmq` | `5.0.x` | `37aa7ec5bf16` | `git@github.com:micronaut-projects/micronaut-rabbitmq.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-rabbitmq`
- Commit candidates found: 79
- File changes listed: 135
- Version values listed: 23
- File status counts: A=28, M=107

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `4.9.0-SNAPSHOT` | `5.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.gradle-kotlin` | `org.jetbrains.kotlin:kotlin-gradle-plugin (version.ref=kotlin)` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.gradle-kotlin-allopen` | `org.jetbrains.kotlin:kotlin-allopen (version.ref=kotlin)` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.gradle-kotlin-noarg` | `org.jetbrains.kotlin:kotlin-noarg (version.ref=kotlin)` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.gradle-micronaut` | `io.micronaut.gradle:micronaut-gradle-plugin:4.5.5` | `io.micronaut.gradle:micronaut-gradle-plugin:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.jsr305` | `jsr305:3.0.2` | `jsr305:3.0.2` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.micronaut-cache` | `not present` | `io.micronaut.cache:micronaut-cache-bom:6.0.0` | `added` |
| `gradle/libs.versions.toml` | `libraries.micronaut-micrometer` | `io.micronaut.micrometer:micronaut-micrometer-bom:5.13.0` | `io.micronaut.micrometer:micronaut-micrometer-bom:6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.15.5` | `io.micronaut.serde:micronaut-serde-bom:3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-resources` | `io.micronaut.testresources:micronaut-test-resources-bom:2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.18` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.jsr305` | `3.0.2` | `3.0.2` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.4` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-cache` | `not present` | `6.0.0` | `added` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.5.5` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-micrometer` | `5.13.0` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-platform` | `4.3.4` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.15.5` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.9.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test-resources` | `2.10.1` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `6e1608392801` remove unused rabbit (Sergio del Amo, 2026-05-07)
- `96c3f8849796` remove unused kotest (Sergio del Amo, 2026-05-07)
- `11f8adf27658` Removed the Spock version force configuration from build (#809) (Issam Liqali, 2026-03-13)
- `392366058076` Remove test resources dependency from rabbitMQ (#789) (Sergio del Amo, 2025-12-15)

### Fixes

- `9b754b086a37` fix(deps): update dependency com.rabbitmq:amqp-client to v5.30.0 (#805) (renovate[bot], 2026-04-28)
- `5dadca81029c` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m23 (#815) (renovate[bot], 2026-04-21)
- `81df6e6e93d9` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m6 (#814) (renovate[bot], 2026-04-16)
- `c557287f25e0` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m20 (#810) (renovate[bot], 2026-04-10)
- `d7099596e16b` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m16 (#804) (renovate[bot], 2026-03-13)
- `0da6a389f221` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m13 (#803) (renovate[bot], 2026-02-23)
- `acd66aa7026e` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m10 (#792) (renovate[bot], 2026-02-12)
- `c1e32c2aa3fc` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m2 (#798) (renovate[bot], 2026-02-12)
- `feafa37b5009` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.2 (#800) (renovate[bot], 2026-02-12)
- `503d714d1f6e` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m3 (#788) (renovate[bot], 2025-12-15)
- `d7112bd0c195` fix(deps): update dependency org.awaitility:awaitility to v4.3.0 (#778) (renovate[bot], 2025-12-10)
- `888b00258af9` fix(deps): update dependency io.micronaut.testresources:micronaut-test-resources-bom to v2.10.1 (#777) (renovate[bot], 2025-12-10)
- `a81fd461382e` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#775) (renovate[bot], 2025-12-10)
- `a56da092822f` fix(deps): update dependency io.micronaut.micrometer:micronaut-micrometer-bom to v5.13.2 (#774) (renovate[bot], 2025-12-10)
- `7d1e182cf375` fix(deps): update dependency io.kotest:kotest-runner-junit5 to v5.9.1 (#773) (renovate[bot], 2025-12-10)
- `7bb36f8e2dc4` fix(deps): update kotlin monorepo to v2.2.21 (#769) (renovate[bot], 2025-12-10)
- `e584ca4a515a` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.1 (#768) (renovate[bot], 2025-12-10)
- `a96d42554ad6` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#766) (renovate[bot], 2025-12-10)
- `77f43d88556c` fix(deps): update kotlin monorepo to v1.9.25 (#762) (renovate[bot], 2025-11-03)
- `fa6338752dc0` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.3.6 (#611) (renovate[bot], 2024-04-13)
- `65024f1f73a1` fix(deps): update dependency com.rabbitmq:amqp-client to v5.21.0 (#614) (renovate[bot], 2024-04-13)
- `c59ade57d7c7` fix(deps): update dependency io.micronaut.testresources:micronaut-test-resources-bom to v2.5.0 (#616) (renovate[bot], 2024-04-13)
- `9055e51dfa50` fix(deps): update dependency io.micronaut.testresources:micronaut-test-resources-bom to v2.4.0 (#601) (renovate[bot], 2024-04-01)
- `f3261df27fd5` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.4.0 (#608) (renovate[bot], 2024-04-01)

### Dependency Updates

- `ca4e580ae017` chore: Bump version to 5.0.1-SNAPSHOT (micronaut-build, 2026-05-18)
- `960b0876cfce` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-05-07)
- `66bdaf1b089a` chore(deps): combine dependency upgrades (#821) (Graeme Rocher, 2026-05-05)
- `70d175f5a343` replace caffeine dependency with micronaut-cache (#795) (issam liqali, 2026-02-27)
- `afd1c23d6a67` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#802) (renovate[bot], 2026-02-23)
- `41a064026d54` chore(deps): update github artifact actions (#794) (renovate[bot], 2026-02-12)
- `5132145311be` chore(deps): update actions/cache action to v5 (#793) (renovate[bot], 2026-02-12)
- `48d61b203f7d` chore(deps): update graalvm/setup-graalvm action to v1.4.5 (#796) (renovate[bot], 2026-02-12)
- `783a0502147f` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m16 (#797) (renovate[bot], 2026-02-12)
- `73009a17b757` chore(deps): update gradle to v9.3.1 (#799) (renovate[bot], 2026-02-12)
- `a1e10ac93a1f` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2025-12-16)
- `bc55ca24c7c0` chore(deps): update dependency org.spockframework:spock-core to v2.4-groovy-5.0 (#790) (renovate[bot], 2025-12-15)
- `9eaa71df9b0e` chore(deps): update actions/checkout action to v6.0.1 (#782) (renovate[bot], 2025-12-10)
- `a906ea2d0185` chore(deps): update softprops/action-gh-release action to v2.5.0 (#767) (renovate[bot], 2025-12-10)
- `9f7ea972cef1` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#765) (renovate[bot], 2025-12-10)
- `04ad411d7e33` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#760) (renovate[bot], 2025-11-03)
- `171a3f9b7bf2` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m8 (#761) (renovate[bot], 2025-11-03)
- `848f3c25465c` chore(deps): update gradle to v9.2.0 (#763) (renovate[bot], 2025-11-03)
- `568e569f9a55` Update Micronaut plugin version to 8.0.0-M4 (#757) (Sergio del Amo, 2025-10-17)
- `8462ec97932d` chore(deps): update plugin io.micronaut.build.shared.settings to v6.7.1 (#755) (renovate[bot], 2025-10-17)
- `0ec0ef1d50e2` chore(deps): update gradle/gradle-build-action action to v3.3.0 (#610) (renovate[bot], 2024-04-13)

### Documentation

- `2a6b048e408c` Docs: update micronaut-docs to 3.0.0 (#752) (issam liqali, 2025-10-17)

### Internal

- `2778ac0ac84d` Build: Update to Micronaut 5 (#787) (issam liqali, 2025-12-12)

### Review Candidates

- `37aa7ec5bf16` update versions (Sergio del Amo, 2026-05-19)
- `06826e624810` [skip ci] Release v5.0.0 (micronaut-build, 2026-05-18)
- `0a9612f9b23a` Update common files (#827) (micronaut-build, 2026-05-14)
- `0d702f99e96b` micronaut-platform = "5.0.0-RC1" (Sergio del Amo, 2026-05-13)
- `5bc5d8e4214d` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `37c2a46d4a0d` Update common files (#826) (micronaut-build, 2026-05-09)
- `810163596b06` [skip ci] Release v5.0.0-RC1 (micronaut-build, 2026-05-07)
- `fac46a42a9b9` git ignore .kotlin (Sergio del Amo, 2026-05-07)
- `8643f7ebc605` fix kotlin compilation (Sergio del Amo, 2026-05-07)
- `46d8a098ea93` replace * imports (Sergio del Amo, 2026-05-07)
- `4cf8671e5d4e` update versions (Sergio del Amo, 2026-05-07)
- `918595c1ff99` Update common files (#824) (micronaut-build, 2026-05-07)
- `8ce441049283` Update common files (#818) (micronaut-build, 2026-05-05)
- `9420f4ae2b2f` Update common files (#812) (micronaut-build, 2026-04-26)
- `0b9e7512b7e2` Update common files (#807) (micronaut-build, 2026-03-13)
- `721dde06917d` Update common files (#791) (micronaut-build, 2026-02-12)
- `218af58987cd` [skip ci] Release v5.0.0-M1 (micronaut-build, 2025-12-16)
- `b8e699ef597b` use build.internal.parent (Sergio del Amo, 2025-12-16)
- `5747baee9fbe` Micronaut Build Gradle Plugin 8.0.0-M13 (Sergio del Amo, 2025-12-16)
- `c2f653886ea9` Revert "[skip ci] Release v5.0.0-M1" (Sergio del Amo, 2025-12-16)
- `3c2f027dd550` [skip ci] Release v5.0.0-M1 (micronaut-build, 2025-12-15)
- `8f140aef9906` Update common files (#764) (micronaut-build, 2025-12-10)
- `7faa44ebf135` Replace Micronaut nullability annotations with JSpecify annotations (#780) (Copilot, 2025-12-02)
- `01a91b146f02` Micronaut 5 compatibility (#759) (issam liqali, 2025-11-03)
- `514ab0cfb4d7` Update common files (#758) (micronaut-build, 2025-11-03)
- `f10952e439c8` Update common files (#753) (micronaut-build, 2025-10-17)
- `af72a83b14f5` Update common files (#607) (micronaut-build, 2024-03-28)
- `de8bb333b22d` breaks: del and document deprecated code for MN5 (#605) (Dean Wette, 2024-03-27)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` build.gradle
- `M` buildSrc/build.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.rabbitmq-examples.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` rabbitmq/build.gradle.kts
- `M` settings.gradle
- `A` test-suite-utils/build.gradle.kts

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
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/rabbitmq/docs/consumer/acknowledge/type/AcknowledgeSpec.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/rabbitmq/docs/consumer/concurrent/ConcurrentSpec.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/rabbitmq/docs/consumer/connection/ConnectionSpec.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/rabbitmq/docs/consumer/custom/annotation/DeliveryTagSpec.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/rabbitmq/docs/consumer/custom/type/ProductInfo.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/rabbitmq/docs/consumer/custom/type/ProductInfoSpec.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/rabbitmq/docs/consumer/executor/CustomExecutorSpec.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/rabbitmq/docs/consumer/types/TypeBindingSpec.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/rabbitmq/docs/exchange/CustomExchangeSpec.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/rabbitmq/docs/headers/HeadersSpec.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/rabbitmq/docs/headers/ProductListener.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/rabbitmq/docs/parameters/BindingSpec.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/rabbitmq/docs/properties/ProductListener.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/rabbitmq/docs/properties/PropertiesSpec.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/rabbitmq/docs/publisher/acknowledge/PublisherAcknowledgeSpec.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/rabbitmq/docs/quickstart/QuickstartSpec.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/rabbitmq/docs/rpc/RpcUppercaseSpec.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/rabbitmq/docs/serdes/ProductInfo.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/rabbitmq/docs/serdes/ProductInfoSerDesSpec.groovy
- `M` docs-examples/example-java/src/test/java/io/micronaut/rabbitmq/docs/consumer/acknowledge/type/AcknowledgeSpec.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/rabbitmq/docs/consumer/concurrent/ConcurrentSpec.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/rabbitmq/docs/consumer/connection/ConnectionSpec.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/rabbitmq/docs/consumer/custom/annotation/DeliveryTagSpec.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/rabbitmq/docs/consumer/custom/type/ProductInfo.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/rabbitmq/docs/consumer/custom/type/ProductInfoSpec.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/rabbitmq/docs/consumer/executor/CustomExecutorSpec.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/rabbitmq/docs/consumer/types/TypeBindingSpec.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/rabbitmq/docs/exchange/CustomExchangeSpec.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/rabbitmq/docs/headers/HeadersSpec.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/rabbitmq/docs/headers/ProductListener.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/rabbitmq/docs/parameters/BindingSpec.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/rabbitmq/docs/properties/ProductListener.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/rabbitmq/docs/properties/PropertiesSpec.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/rabbitmq/docs/publisher/acknowledge/PublisherAcknowledgeSpec.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/rabbitmq/docs/quickstart/QuickstartSpec.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/rabbitmq/docs/rpc/RpcUppercaseSpec.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/rabbitmq/docs/serdes/ProductInfo.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/rabbitmq/docs/serdes/ProductInfoSerDesSpec.java
- `M` docs-examples/example-kotlin/build.gradle
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/rabbitmq/docs/ProjectConfig.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/rabbitmq/docs/config/ConnectionFactoryInterceptor.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/rabbitmq/docs/consumer/acknowledge/type/AcknowledgeSpec.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/rabbitmq/docs/consumer/concurrent/ConcurrentSpec.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/rabbitmq/docs/consumer/connection/ConnectionSpec.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/rabbitmq/docs/consumer/custom/annotation/DeliveryTagSpec.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/rabbitmq/docs/consumer/custom/type/ProductInfoSpec.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/rabbitmq/docs/consumer/executor/CustomExecutorSpec.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/rabbitmq/docs/consumer/types/TypeBindingSpec.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/rabbitmq/docs/exchange/CustomExchangeSpec.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/rabbitmq/docs/headers/HeadersSpec.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/rabbitmq/docs/parameters/BindingSpec.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/rabbitmq/docs/properties/PropertiesSpec.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/rabbitmq/docs/publisher/acknowledge/PublisherAcknowledgeSpec.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/rabbitmq/docs/quickstart/QuickstartSpec.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/rabbitmq/docs/rpc/RpcUppercaseSpec.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/rabbitmq/docs/serdes/ProductInfoSerDesSpec.kt
- `A` src/main/docs/guide/breaks.adoc
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
- `M` rabbitmq/src/main/java/io/micronaut/rabbitmq/annotation/Mandatory.java
- `M` rabbitmq/src/main/java/io/micronaut/rabbitmq/bind/RabbitConsumerState.java
- `M` rabbitmq/src/main/java/io/micronaut/rabbitmq/bind/RabbitMessageCloseable.java
- `M` rabbitmq/src/main/java/io/micronaut/rabbitmq/connect/ClusterRabbitConnectionFactoryConfig.java
- `M` rabbitmq/src/main/java/io/micronaut/rabbitmq/connect/RabbitConnectionFactory.java
- `M` rabbitmq/src/main/java/io/micronaut/rabbitmq/connect/RabbitConnectionFactoryConfig.java
- `M` rabbitmq/src/main/java/io/micronaut/rabbitmq/connect/SingleRabbitConnectionFactoryConfig.java
- `M` rabbitmq/src/main/java/io/micronaut/rabbitmq/connect/recovery/TemporarilyDownAutorecoveringConnection.java
- `M` rabbitmq/src/main/java/io/micronaut/rabbitmq/exception/RabbitListenerException.java
- `M` rabbitmq/src/main/java/io/micronaut/rabbitmq/intercept/RabbitMQConsumerAdvice.java
- `M` rabbitmq/src/main/java/io/micronaut/rabbitmq/intercept/StaticPublisherState.java
- `M` rabbitmq/src/main/java/io/micronaut/rabbitmq/metrics/RabbitMetricsInterceptor.java
- `M` rabbitmq/src/main/java/io/micronaut/rabbitmq/reactive/RabbitPublishState.java
- `M` rabbitmq/src/main/java/io/micronaut/rabbitmq/serdes/JavaLangRabbitMessageSerDes.java
- `M` rabbitmq/src/main/java/io/micronaut/rabbitmq/serdes/RabbitMessageSerDes.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` rabbitmq/src/test/groovy/io/micronaut/rabbitmq/AbstractRabbitMQClusterTest.groovy
- `M` rabbitmq/src/test/groovy/io/micronaut/rabbitmq/AbstractRabbitMQTest.groovy
- `M` rabbitmq/src/test/groovy/io/micronaut/rabbitmq/annotation/SimpleBindingSpec.groovy
- `M` rabbitmq/src/test/groovy/io/micronaut/rabbitmq/connect/FailOverConnectionSpec.groovy
- `M` rabbitmq/src/test/groovy/io/micronaut/rabbitmq/connect/MultipleServersSpec.groovy
- `M` rabbitmq/src/test/groovy/io/micronaut/rabbitmq/connect/TemporarilyDownConsumersSpec.groovy
- `M` rabbitmq/src/test/groovy/io/micronaut/rabbitmq/health/RabbitHealthIndicatorSpec.groovy
- `M` rabbitmq/src/test/groovy/io/micronaut/rabbitmq/listener/ConsumerRecoverySpec.groovy
- `M` rabbitmq/src/test/groovy/io/micronaut/rabbitmq/listener/MissingHeaderSpec.groovy
- `M` rabbitmq/src/test/groovy/io/micronaut/rabbitmq/rpc/RpcConsumer.groovy
- `A` test-suite-utils/src/main/java/io/micronaut/rabbitmq/testcontainers/RabbitMQ.java

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

