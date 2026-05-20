Compared as mn4/3.8.x -> mn5/4.0.x based on branch metadata.

  Scope:

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-mqtt, branch 3.8.x, commit
    9e8f5053016cd7afad34e22c1da675850997a1f4
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-mqtt, branch 4.0.x, commit
    54f0fa27ef7dc329143d4ffce7f32d533c348cde
  - Both worktrees are clean and use the same remote.

  Full report: /private/tmp/micronaut-mqtt-3.8-to-4.0-comparison.md:1

  Key findings:

  - 175 files changed: 43 added, 11 deleted, 114 modified, 7 renamed; 5,260 insertions, 1,401 deletions.
  - Main platform moves to Micronaut 5: projectVersion 3.8.0-SNAPSHOT -> 4.0.1-SNAPSHOT, micronaut 4.10.4 ->
    5.0.0.
  - Build baseline changes: Gradle 8.14.3 -> 9.5.1, shared settings plugin 7.6.4 -> 8.0.0-M18, Micronaut Gradle
    plugin 4.5.5 -> 5.0.0-M1, .sdkmanrc adds java=25.0.1-graal.
  - MQTT client deps: HiveMQ client 1.3.10 -> 1.3.14; Paho MQTT v3 and v5 stay at 1.2.5.
  - Crypto dependency changes from org.bouncycastle:bcpkix-jdk15on:1.70 to org.bouncycastle:bcpkix-
    jdk18on:1.84.
  - Production source changes are mostly Micronaut 5 compatibility: JSpecify nullability annotations, explicit
    Java imports, and ExecutableMethodProcessor.process generic signature update. I did not find documented
    breaking changes or public MQTT API removals in main source.
  - Test resources usage is removed in favor of direct Testcontainers dependencies and new Java HiveMQ/
    Mosquitto test helpers.
  - Sonatype scan plugin wiring was removed; new OSV/CycloneDX vulnerability audit script and workflow were
    added.
  - Review candidate: mqttv5/build.gradle adds Testcontainers as implementation, while nearby modules use
    testImplementation; verify whether that published dependency exposure is intentional.

# Release Note Comparison

Generated: 2026-05-19 09:38 UTC
Comparison: `3.8.x` -> `4.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-mqtt` | `3.8.x` | `9e8f5053016c` | `git@github.com:micronaut-projects/micronaut-mqtt.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-mqtt` | `4.0.x` | `54f0fa27ef7d` | `git@github.com:micronaut-projects/micronaut-mqtt.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-mqtt`
- Commit candidates found: 54
- File changes listed: 175
- Version values listed: 39
- File status counts: A=43, D=11, M=114, R=7

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `3.8.0-SNAPSHOT` | `4.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.awaitility` | `org.awaitility:awaitility:4.3.0` | `org.awaitility:awaitility:4.3.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.bcpkix-jdk15on` | `org.bouncycastle:bcpkix-jdk15on:1.70` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.bcpkix-jdk18on` | `not present` | `org.bouncycastle:bcpkix-jdk18on:1.84` | `added` |
| `gradle/libs.versions.toml` | `libraries.gradle-kotlin` | `org.jetbrains.kotlin:kotlin-gradle-plugin:1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.gradle-kotlin-allopen` | `org.jetbrains.kotlin:kotlin-allopen:1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.gradle-kotlin-noarg` | `org.jetbrains.kotlin:kotlin-noarg:1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.kotlin-stdlib-jdk8` | `org.jetbrains.kotlin:kotlin-stdlib-jdk8:1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.managed-hivemq-client` | `com.hivemq:hivemq-mqtt-client:1.3.10` | `com.hivemq:hivemq-mqtt-client:1.3.14` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-paho-mqttv3-client` | `org.eclipse.paho:org.eclipse.paho.client.mqttv3:1.2.5` | `org.eclipse.paho:org.eclipse.paho.client.mqttv3:1.2.5` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-paho-mqttv5-client` | `org.eclipse.paho:org.eclipse.paho.mqttv5.client:1.2.5` | `org.eclipse.paho:org.eclipse.paho.mqttv5.client:1.2.5` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.micronaut-gradle-plugin` | `io.micronaut.gradle:micronaut-gradle-plugin:4.5.5` | `io.micronaut.gradle:micronaut-gradle-plugin:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-reactor` | `io.micronaut.reactor:micronaut-reactor-bom:3.9.0` | `io.micronaut.reactor:micronaut-reactor-bom:4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.15.5` | `io.micronaut.serde:micronaut-serde-bom:3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-resources` | `io.micronaut.testresources:micronaut-test-resources-bom:2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-validation` | `io.micronaut.validation:micronaut-validation-bom:4.11.0` | `io.micronaut.validation:micronaut-validation-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.sonatype-scan` | `org.sonatype.gradle.plugins:scan-gradle-plugin:3.1.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.awaitility` | `4.3.0` | `4.3.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.bcpkix-jdk15on` | `1.70` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.bcpkix-jdk18on` | `not present` | `1.84` | `added` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.24` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.kotlin` | `1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.managed-hivemq-client` | `1.3.10` | `1.3.14` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-mqttv3` | `1.2.5` | `1.2.5` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-mqttv5` | `1.2.5` | `1.2.5` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.4` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.5.5` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-reactor` | `3.9.0` | `4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.15.5` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.7.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test-resources` | `2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.11.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.sonatype-scan` | `3.1.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |
| `settings.gradle` | `plugin.io.micronaut.build.shared.settings` | `7.6.4` | `8.0.0-M18` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Fixes

- `b767a6d65946` fix(deps): update dependency com.hivemq:hivemq-mqtt-client to v1.3.14 (#605) (renovate[bot], 2026-05-07)
- `6d6f20381847` fix(deps): update micronaut dependencies (#600) (renovate[bot], 2026-05-01)
- `163f2ea1e98b` fix(deps): update dependency com.hivemq:hivemq-mqtt-client to v1.3.13 (#579) (renovate[bot], 2026-04-27)
- `6fb5b780c1df` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.15 (#576) (renovate[bot], 2026-02-17)
- `325938ec6406` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.2 (#586) (renovate[bot], 2026-02-17)
- `a952412f6ccd` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#566) (renovate[bot], 2025-12-10)
- `fa301aa9cf5f` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.12.0 (#565) (renovate[bot], 2025-12-10)
- `ba64e092b168` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#564) (renovate[bot], 2025-12-10)
- `ee3cba9017f1` fix(deps): update kotlin monorepo to v2.2.21 (#561) (renovate[bot], 2025-12-10)
- `69eab3e2098a` fix(deps): update dependency io.micronaut.reactor:micronaut-reactor-bom to v3.9.1 (#559) (renovate[bot], 2025-12-10)
- `6d2fb58c25c7` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.8 (#555) (renovate[bot], 2025-11-03)
- `9796211b47ec` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.6 (#550) (renovate[bot], 2025-10-17)

### Dependency Updates

- `54f0fa27ef7d` chore: Bump version to 4.0.1-SNAPSHOT (micronaut-build, 2026-05-14)
- `f6f353e32020` chore: Bump version to 4.0.0-SNAPSHOT (micronaut-build, 2026-05-07)
- `ce14903e5ca7` chore(deps): combine safe Renovate dependency upgrades (#603) (Sergio del Amo, 2026-05-01)
- `57cea8d91bda` chore(deps): update dependency org.graalvm.buildtools.native:org.graalvm.buildtools.native.gradle.plugin to v0.11.5 (#592) (renovate[bot], 2026-04-27)
- `3c13cb29e0d2` chore: Bump version to 4.0.0-SNAPSHOT (micronaut-build, 2026-03-02)
- `0306d1c7f334` chore(deps): update github artifact actions (#588) (renovate[bot], 2026-03-02)
- `abd503b3e6d2` chore(deps): update github artifact actions (#582) (renovate[bot], 2026-02-17)
- `c02324bb1cde` chore(deps): update actions/cache action to v5 (#581) (renovate[bot], 2026-02-17)
- `6e62b0ac448c` chore(deps): update dependency org.graalvm.buildtools.native:org.graalvm.buildtools.native.gradle.plugin to v0.11.4 (#585) (renovate[bot], 2026-02-17)
- `38627bf201eb` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#578) (renovate[bot], 2026-02-17)
- `aae769389dcb` chore(deps): update graalvm/setup-graalvm action to v1.4.5 (#583) (renovate[bot], 2026-02-17)
- `f98193703890` chore(deps): update gradle to v9.3.1 (#584) (renovate[bot], 2026-02-17)
- `c6acc17e6fbb` chore(deps): update stefanzweifel/git-auto-commit-action action to v7 (#573) (renovate[bot], 2025-12-10)
- `c783e5cd50bc` chore(deps): update actions/checkout action (#567) (renovate[bot], 2025-12-10)
- `e26c4a347291` chore(deps): update dependency org.graalvm.buildtools.native:org.graalvm.buildtools.native.gradle.plugin to v0.11.3 (#562) (renovate[bot], 2025-12-10)
- `436ec8d36d56` chore(deps): update softprops/action-gh-release action to v2.5.0 (#558) (renovate[bot], 2025-12-10)
- `21ccfe200d14` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#557) (renovate[bot], 2025-12-10)
- `18f13459b855` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#553) (renovate[bot], 2025-11-03)
- `f695357ee976` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m8 (#554) (renovate[bot], 2025-11-03)

### Internal

- `a6483d77afe5` ci: projectVersion=4.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-10-14)

### Review Candidates

- `773fcac41318` [skip ci] Release v4.0.0 (micronaut-build, 2026-05-14)
- `e7b21692f314` Update common files (#608) (micronaut-build, 2026-05-14)
- `3020a66df896` Update versions (Sergio del Amo, 2026-05-14)
- `9cd95ec4f3b7` micronaut-gradle-plugin = "5.0.0-M1" (Sergio del Amo, 2026-05-13)
- `274261920f53` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `7c9004c3aed6` Update common files (#607) (micronaut-build, 2026-05-09)
- `3d698100c667` [skip ci] Release v4.0.0-RC1 (micronaut-build, 2026-05-07)
- `03c697dfd34a` upate to latest versions (Sergio del Amo, 2026-05-07)
- `2bc2f2e7d319` Update common files (#606) (micronaut-build, 2026-05-07)
- `4c69309f908c` [mqtt] Update common files for branch 4.0.x (#604) (micronaut-build, 2026-05-05)
- `93ead4390d32` [mqtt] Update common files for branch 4.0.x (#601) (micronaut-build, 2026-05-01)
- `63a823396073` Update common files (#591) (micronaut-build, 2026-04-26)
- `1a8a1d976309` [skip ci] Release v4.0.0-M1 (micronaut-build, 2026-03-02)
- `fb91a04a5bed` Update to micronaut 5 (#577) (Issam Liqali, 2026-03-02)
- `bb3aadfc9df3` Update common files (#575) (micronaut-build, 2026-02-27)
- `841259b412b5` Update common files (#556) (micronaut-build, 2025-12-10)
- `c63fc1e1d950` [WIP] Replace Micronaut nullability annotations with JSpecify (#572) (Copilot, 2025-12-02)
- `a3105042cc7e` Micronaut 5 compability (#552) (issam liqali, 2025-11-03)
- `c461c859277d` Update common files (#551) (micronaut-build, 2025-11-03)
- `22bfe66c06f2` Update common files (#549) (micronaut-build, 2025-10-17)
- `db57203b16d5` Micronaut Gradle build plugin 8.0.0-M4 (Sergio del Amo, 2025-10-14)
- `bb6a62156a8a` gradle 9.1 (Sergio del Amo, 2025-10-14)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` .github/workflows/update-gradle-wrapper.yml
- `M` buildSrc/build.gradle.kts
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.graal-test.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.mqtt-module.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` mqtt-core/build.gradle
- `M` mqtt-hivemq/build.gradle.kts
- `M` mqtt-ssl/build.gradle
- `M` mqttv3/build.gradle
- `M` mqttv5/build.gradle
- `M` settings.gradle
- `M` test-suite-groovy/build.gradle
- `M` test-suite-hivemq-mqttv3-graal/build.gradle.kts
- `M` test-suite-hivemq-mqttv5-graal-mtls/build.gradle.kts
- `M` test-suite-hivemq-mqttv5-graal-no-mtls/build.gradle.kts
- `M` test-suite-hivemq-mqttv5-graal/build.gradle.kts
- `M` test-suite-jackson/build.gradle
- `M` test-suite-kotlin/build.gradle
- `M` test-suite-mqttv3-graal/build.gradle.kts
- `M` test-suite-mqttv5-graal-ssl/build.gradle.kts
- `M` test-suite-mqttv5-graal/build.gradle.kts
- `M` test-suite-utils/build.gradle
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
- `M` test-suite-groovy/src/test/groovy/io/micronaut/mqtt/docs/consumer/acknowledge/type/AcknowledgeSpec.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/mqtt/docs/custom/annotation/CorrelationSpec.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/mqtt/docs/custom/type/ProductInfo.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/mqtt/docs/custom/type/ProductInfoSpec.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/mqtt/docs/parameters/BindingSpec.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/mqtt/docs/properties/ProductListener.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/mqtt/docs/properties/PropertiesSpec.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/mqtt/docs/publisher/acknowledge/PublisherAcknowledgeSpec.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/mqtt/docs/quickstart/QuickstartSpec.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/mqtt/docs/serdes/ProductInfo.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/mqtt/docs/serdes/ProductInfoSerDes.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/mqtt/docs/serdes/ProductInfoSerDesSpec.groovy
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/mqtt/docs/consumer/acknowledge/type/AcknowledgeSpec.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/mqtt/docs/custom/annotation/CorrelationSpec.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/mqtt/docs/custom/type/ProductInfoSpec.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/mqtt/docs/parameters/BindingSpec.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/mqtt/docs/properties/PropertiesSpec.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/mqtt/docs/publisher/acknowledge/PublisherAcknowledgeSpec.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/mqtt/docs/quickstart/QuickstartSpec.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/mqtt/docs/serdes/ProductInfoSerDesSpec.kt
- `M` test-suite/src/test/java/io/micronaut/mqtt/docs/consumer/acknowledge/type/AcknowledgeSpec.java
- `M` test-suite/src/test/java/io/micronaut/mqtt/docs/custom/annotation/CorrelationSpec.java
- `M` test-suite/src/test/java/io/micronaut/mqtt/docs/custom/type/ProductInfo.java
- `M` test-suite/src/test/java/io/micronaut/mqtt/docs/custom/type/ProductInfoSpec.java
- `M` test-suite/src/test/java/io/micronaut/mqtt/docs/parameters/BindingSpec.java
- `M` test-suite/src/test/java/io/micronaut/mqtt/docs/properties/ProductListener.java
- `M` test-suite/src/test/java/io/micronaut/mqtt/docs/properties/PropertiesSpec.java
- `M` test-suite/src/test/java/io/micronaut/mqtt/docs/publisher/acknowledge/PublisherAcknowledgeSpec.java
- `M` test-suite/src/test/java/io/micronaut/mqtt/docs/quickstart/QuickstartSpec.java
- `M` test-suite/src/test/java/io/micronaut/mqtt/docs/serdes/ProductInfo.java
- `M` test-suite/src/test/java/io/micronaut/mqtt/docs/serdes/ProductInfoSerDes.java
- `M` test-suite/src/test/java/io/micronaut/mqtt/docs/serdes/ProductInfoSerDesSpec.java

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
- `M` config/checkstyle/checkstyle.xml
- `M` mqtt-core/src/main/java/io/micronaut/mqtt/annotation/Id.java
- `M` mqtt-core/src/main/java/io/micronaut/mqtt/annotation/Qos.java
- `M` mqtt-core/src/main/java/io/micronaut/mqtt/annotation/Retained.java
- `M` mqtt-core/src/main/java/io/micronaut/mqtt/annotation/Topic.java
- `M` mqtt-core/src/main/java/io/micronaut/mqtt/annotation/Topics.java
- `M` mqtt-core/src/main/java/io/micronaut/mqtt/intercept/AbstractMqttSubscriberAdvice.java
- `M` mqtt-core/src/main/java/io/micronaut/mqtt/serdes/JavaLangMqttPayloadSerDes.java
- `M` mqtt-core/src/main/java/io/micronaut/mqtt/serdes/MqttPayloadSerDes.java
- `M` mqtt-hivemq/src/main/java/io/micronaut/mqtt/hivemq/client/MqttClientFactory.java
- `M` mqtt-hivemq/src/main/java/io/micronaut/mqtt/hivemq/config/MqttClientConfigurationProperties.java
- `M` mqtt-hivemq/src/main/java/io/micronaut/mqtt/hivemq/v3/client/Mqtt3ClientFactory.java
- `M` mqtt-hivemq/src/main/java/io/micronaut/mqtt/hivemq/v5/client/Mqtt5ClientFactory.java
- `M` mqttv3/src/main/java/io/micronaut/mqtt/v3/client/MqttClientFactory.java
- `M` mqttv5/src/main/java/io/micronaut/mqtt/v5/client/MqttClientFactory.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` mqtt-hivemq/src/test/groovy/io/micronaut/mqtt/hivemq/v3/annotation/V3TopicAnnotationSpec.groovy
- `M` mqtt-hivemq/src/test/groovy/io/micronaut/mqtt/hivemq/v3/health/V3HealthIndicatorSpec.groovy
- `M` mqtt-hivemq/src/test/groovy/io/micronaut/mqtt/hivemq/v5/bind/property/V5PropertyBindingSpec.groovy
- `M` mqtt-hivemq/src/test/groovy/io/micronaut/mqtt/hivemq/v5/client/V5EnhancedAuthenticationSpec.groovy
- `M` mqtt-hivemq/src/test/groovy/io/micronaut/mqtt/hivemq/v5/client/V5WillMessageSpec.groovy
- `M` mqtt-hivemq/src/test/groovy/io/micronaut/mqtt/hivemq/v5/health/V5HealthIndicatorSpec.groovy
- `M` mqtt-ssl/src/test/groovy/io/micronaut/mqtt/ssl/AbstractMQTTTest.groovy
- `M` mqtt-ssl/src/test/groovy/io/micronaut/mqtt/ssl/SslAuthenticationSpec.groovy
- `M` mqttv3/src/test/groovy/io/micronaut/mqtt/annotation/V3TopicAnnotationSpec.groovy
- `M` mqttv3/src/test/groovy/io/micronaut/mqtt/health/V3HealthIndicatorSpec.groovy
- `M` mqttv5/src/test/groovy/io/micronaut/mqtt/annotation/V5TopicAnnotationSpec.groovy
- `M` mqttv5/src/test/groovy/io/micronaut/mqtt/bind/property/V5PropertyBindingSpec.groovy
- `M` mqttv5/src/test/groovy/io/micronaut/mqtt/health/V5HealthIndicatorSpec.groovy
- `M` test-suite-hivemq-mqttv3-graal/src/test/java/io/micronaut/mqtt3/graal/MqttTest.java
- `A` test-suite-hivemq-mqttv5-graal-mtls/src/test/java/io/micronaut/mqtt5/graal/Mosquitto.java
- `M` test-suite-hivemq-mqttv5-graal-mtls/src/test/java/io/micronaut/mqtt5/graal/MqttHivemqMutualTlsTest.java
- `A` test-suite-hivemq-mqttv5-graal-mtls/src/test/resources/META-INF/native-image/resource-config.json
- `M` test-suite-hivemq-mqttv5-graal-mtls/src/test/resources/application.yml
- `A` test-suite-hivemq-mqttv5-graal-no-mtls/src/test/java/io/micronaut/mqtt5/graal/Mosquitto.java
- `M` test-suite-hivemq-mqttv5-graal-no-mtls/src/test/java/io/micronaut/mqtt5/graal/MqttHivemqNoMutualTlsTest.java
- `A` test-suite-hivemq-mqttv5-graal-no-mtls/src/test/resources/META-INF/native-image/resource-config.json
- `M` test-suite-hivemq-mqttv5-graal-no-mtls/src/test/resources/application.yml
- `M` test-suite-hivemq-mqttv5-graal/src/test/java/io/micronaut/mqtt5/graal/MqttTest.java
- `M` test-suite-jackson/src/main/java/example/micronaut/Odour.java
- `M` test-suite-jackson/src/main/java/example/micronaut/SmellListener.java
- `M` test-suite-jackson/src/test/java/example/micronaut/AbstractMQTTTest.java
- `M` test-suite-jackson/src/test/java/example/micronaut/SubscriptionTest.java
- `R100` test-suite-jackson/src/test/resources/mosquitto.conf
- `A` test-suite-kotlin/src/test/kotlin/io/micronaut/mqtt/AbstractMQTTTest.kt
- `D` test-suite-kotlin/src/test/kotlin/io/micronaut/mqtt/AbstractMqttKotest.kt
- `M` test-suite-mqttv3-graal/src/test/java/io/micronaut/mqtt3/graal/MqttTest.java
- `A` test-suite-mqttv5-graal-ssl/src/test/java/io/micronaut/mqtt5/graal/Mosquitto.java
- `M` test-suite-mqttv5-graal-ssl/src/test/java/io/micronaut/mqtt5/graal/MqttTest.java
- `A` test-suite-mqttv5-graal-ssl/src/test/resources/META-INF/native-image/resource-config.json
- `M` test-suite-mqttv5-graal-ssl/src/test/resources/application.yml
- `M` test-suite-mqttv5-graal/src/test/java/io/micronaut/mqtt5/graal/MqttTest.java
- `D` test-suite-utils/src/main/groovy/io/micronaut/mqtt/test/AbstractMQTTTest.groovy
- `D` test-suite-utils/src/main/groovy/io/micronaut/mqtt/test/MQTT3Test.groovy
- `D` test-suite-utils/src/main/groovy/io/micronaut/mqtt/test/MQTT5Test.groovy
- `D` test-suite-utils/src/main/groovy/io/micronaut/mqtt/test/bind/id/IdBindingSpec.groovy
- `D` test-suite-utils/src/main/groovy/io/micronaut/mqtt/test/bind/qos/QosBindingSpec.groovy
- `D` test-suite-utils/src/main/groovy/io/micronaut/mqtt/test/bind/retained/RetainedBindingSpec.groovy
- `D` test-suite-utils/src/main/groovy/io/micronaut/mqtt/test/bind/topic/TopicBindingSpec.groovy
- `D` test-suite-utils/src/main/groovy/io/micronaut/mqtt/test/intercept/MultipleTopicsSpec.groovy
- `D` test-suite-utils/src/main/groovy/io/micronaut/mqtt/test/intercept/SimplePubSubSpec.groovy
- `A` test-suite-utils/src/main/java/io/micronaut/mqtt/HiveMQ.java
- `A` test-suite-utils/src/main/java/io/micronaut/mqtt/Mosquitto.java
- `A` test-suite-utils/src/main/java/io/micronaut/mqtt/test/AbstractMQTTTest.java
- `A` test-suite-utils/src/main/java/io/micronaut/mqtt/test/MQTT3Test.java
- `A` test-suite-utils/src/main/java/io/micronaut/mqtt/test/MQTT5Test.java
- `R080` test-suite-utils/src/main/java/io/micronaut/mqtt/test/bind/id/IdBindingClient.java
- `A` test-suite-utils/src/main/java/io/micronaut/mqtt/test/bind/id/IdBindingSpec.java
- `R072` test-suite-utils/src/main/java/io/micronaut/mqtt/test/bind/qos/QosBindingClient.java
- `A` test-suite-utils/src/main/java/io/micronaut/mqtt/test/bind/qos/QosBindingSpec.java
- `R069` test-suite-utils/src/main/java/io/micronaut/mqtt/test/bind/retained/RetainedBindingClient.java
- `A` test-suite-utils/src/main/java/io/micronaut/mqtt/test/bind/retained/RetainedBindingSpec.java
- `R075` test-suite-utils/src/main/java/io/micronaut/mqtt/test/bind/topic/TopicBindingClient.java
- `A` test-suite-utils/src/main/java/io/micronaut/mqtt/test/bind/topic/TopicBindingSpec.java
- `R078` test-suite-utils/src/main/java/io/micronaut/mqtt/test/intercept/MultipleTopicsClient.java
- `A` test-suite-utils/src/main/java/io/micronaut/mqtt/test/intercept/MultipleTopicsSpec.java
- `R080` test-suite-utils/src/main/java/io/micronaut/mqtt/test/intercept/SimplePubSubClient.java
- `A` test-suite-utils/src/main/java/io/micronaut/mqtt/test/intercept/SimplePubSubSpec.java
- `D` test-suite/src/test/java/io/micronaut/mqtt/AbstractMQTTTest.java

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

