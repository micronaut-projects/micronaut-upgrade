
  micronaut-jms-mn4-to-mn5-comparison.md:1

  Scope: mn4 previous is 4.3.x at d0788ff65f42, clean. mn5 current is 5.0.x at 75a2b19cd7f6, clean. The comparison found 68 commit candidates and 119 changed files.

  Release-note draft:

  ## Micronaut JMS 5.0

  ### Breaking Changes

  - Unsupported broker configuration changed. Defining a custom `ConnectionFactory` is no longer enough; custom or unsupported broker integrations must define both a `ConnectionFactory` and a matching `JMSConnectionPool` bean.
  - The old generic `JMSConnectionFactoryBeanProcessor` that created a `JMSConnectionPool` for each `@JMSConnectionFactory` `ConnectionFactory` bean was removed.

  ### Compatibility

  - Updated for the Micronaut 5 baseline.
  - Replaced Micronaut nullability annotations with JSpecify annotations across JMS APIs.
  - Added explicit `JMSConnectionPool` factories for built-in ActiveMQ Classic, ActiveMQ Artemis, and SQS connection factory types.

  ### Dependency Updates

  - Updated ActiveMQ Classic from `6.1.6` to `6.2.5`.
  - Updated ActiveMQ Artemis Jakarta client from `2.41.0` to `2.53.0`.
  - Updated Apache Commons Pool from `2.12.1` to `2.13.1`.
  - Updated Micronaut AWS from `4.10.0` to `5.0.0-M3`.
  - Updated Micronaut Validation from `4.9.0` to `5.0.0-RC2`.
  - Updated Micronaut Logging from `1.4.0` to `2.0.0-RC1`.

  ### Documentation

  - Updated custom broker documentation to show separate `ConnectionFactory` and `JMSConnectionPool` bean factories.

  Key version changes:

  - Project version: 4.3.1-SNAPSHOT -> 5.0.0-SNAPSHOT
  - Micronaut Core: 4.9.12 -> 5.0.0-RC2
  - Micronaut Platform: 4.8.3 -> 5.0.0-M3
  - Micronaut Gradle plugin: 4.5.5 -> 5.0.0-M1
  - Gradle wrapper: 8.14.3 -> 9.5.0
  - GraalVM SVM: 23.1.7 -> 25.0.3

  I did not run tests; this is a static git/filesystem comparison.

# Release Note Comparison

Generated: 2026-05-07 11:11 UTC
Comparison: `mn4` -> `mn5`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-jms` | `4.3.x` | `d0788ff65f42` | `git@github.com:micronaut-projects/micronaut-jms.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-jms` | `5.0.x` | `75a2b19cd7f6` | `git@github.com:micronaut-projects/micronaut-jms.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-jms`
- Commit candidates found: 68
- File changes listed: 119
- Version values listed: 27
- File status counts: A=42, D=7, M=70

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `4.3.1-SNAPSHOT` | `5.0.0-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.graal-svm` | `org.graalvm.nativeimage:svm:23.1.7` | `org.graalvm.nativeimage:svm:25.0.3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.gradle-kotlin` | `org.jetbrains.kotlin:kotlin-gradle-plugin (version.ref=kotlin)` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.gradle-kotlin-allopen` | `org.jetbrains.kotlin:kotlin-allopen (version.ref=kotlin)` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.jsr305` | `jsr305:3.0.2` | `jsr305:3.0.2` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.micronaut-aws` | `io.micronaut.aws:micronaut-aws-bom:4.10.0` | `io.micronaut.aws:micronaut-aws-bom:5.0.0-M3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-platform` | `io.micronaut.platform:micronaut-platform-bom:4.8.3` | `io.micronaut.platform:micronaut-platform-bom:5.0.0-M3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-resources` | `io.micronaut.testresources:micronaut-test-resources-bom:2.8.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-validation` | `io.micronaut.validation:micronaut-validation-bom:4.9.0` | `io.micronaut.validation:micronaut-validation-bom:5.0.0-RC2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.spotbugs` | `com.github.spotbugs:spotbugs-annotations:4.9.3` | `com.github.spotbugs:spotbugs-annotations:4.9.8` | `changed` |
| `gradle/libs.versions.toml` | `versions.graal-svm` | `23.1.7` | `25.0.3` | `changed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.17` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.jsr305` | `3.0.2` | `3.0.2` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.9.12` | `5.0.0-RC2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-aws` | `4.10.0` | `5.0.0-M3` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `2.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.5.5` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.4.0` | `2.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-platform` | `4.8.3` | `5.0.0-M3` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.5.0` | `5.0.0-M8` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test-resources` | `2.8.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.9.0` | `5.0.0-RC2` | `changed` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.spotbugs` | `4.9.3` | `4.9.8` | `changed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.0` | `changed` |
| `settings.gradle` | `plugin.io.micronaut.build.shared.settings` | `7.6.4` | `8.0.0-M18` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Fixes

- `1a182ddfb2d6` fix(deps): update managed.activemq.jakarta to v6.2.1 (#710) (renovate[bot], 2026-02-24)
- `ac44b3193cf1` fix(deps): update dependency org.apache.activemq:artemis-jakarta-client to v2.51.0 (#713) (renovate[bot], 2026-02-24)
- `399643680bb3` fix(deps): update kotlin monorepo to v2.3.10 (#727) (renovate[bot], 2026-02-24)
- `c5c1d81e71a7` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m13 (#734) (renovate[bot], 2026-02-24)
- `c0a93d8898da` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.15 (#724) (renovate[bot], 2026-02-16)
- `820fc9eaf83a` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.2 (#733) (renovate[bot], 2026-02-16)
- `c0cb4668120d` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#716) (renovate[bot], 2025-12-10)
- `00b4bee1490a` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.12.0 (#712) (renovate[bot], 2025-12-10)
- `540612d7f671` fix(deps): update kotlin monorepo to v2.2.21 (#709) (renovate[bot], 2025-12-10)
- `1637fc20da64` fix(deps): update dependency org.graalvm.nativeimage:svm to v23.1.9 (#707) (renovate[bot], 2025-12-10)
- `f9bb2079e006` fix(deps): update dependency com.github.spotbugs:spotbugs-annotations to v4.9.8 (#703) (renovate[bot], 2025-11-03)
- `6864524769a3` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.8 (#704) (renovate[bot], 2025-11-03)
- `6cf45e0f8ad6` fix(deps): update managed.activemq.jakarta to v6.1.7 (#679) (renovate[bot], 2025-10-13)
- `b390623a5e10` fix(deps): update dependency com.github.spotbugs:spotbugs-annotations to v4.9.6 (#686) (renovate[bot], 2025-10-13)
- `4361e80c2b47` fix(deps): update dependency org.apache.activemq:artemis-jakarta-client to v2.42.0 (#685) (renovate[bot], 2025-10-13)
- `05e523bd933a` fix(deps): update dependency io.micronaut.testresources:micronaut-test-resources-bom to v2.10.1 (#683) (renovate[bot], 2025-10-13)
- `338f1a7c75ba` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.4 (#675) (renovate[bot], 2025-10-13)
- `d9ce3009057d` fix(deps): update dependency io.micronaut.aws:micronaut-aws-bom to v4.11.0 (#681) (renovate[bot], 2025-10-13)
- `beb492d4e9a1` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.11.0 (#684) (renovate[bot], 2025-10-13)

### Dependency Updates

- `93c99eba3ad1` Update Micronaut dependencies (#756) (renovate[bot], 2026-05-05)
- `331e0d4fa6b2` Update dependency org.graalvm.nativeimage:svm to v25.0.3 (#751) (renovate[bot], 2026-04-29)
- `4f1046ece66d` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-04-17)
- `b5c127466e1f` Update dependency org.apache.activemq:artemis-jakarta-client to v2.53.0 (#737) (renovate[bot], 2026-04-17)
- `0ce75adb03fc` Update dependency io.micronaut:micronaut-core-bom to v5.0.0-M22 (#745) (renovate[bot], 2026-04-17)
- `33e010385d5c` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-02-24)
- `2ca5ca7b6158` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m16 (#725) (renovate[bot], 2026-02-16)
- `f11e0cc2b935` chore(deps): update actions/checkout action to v6.0.1 (#714) (renovate[bot], 2025-12-10)
- `5bf2c3bc86f2` chore(deps): update softprops/action-gh-release action to v2.5.0 (#708) (renovate[bot], 2025-12-10)
- `c1814d871183` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#705) (renovate[bot], 2025-12-10)
- `7a3b87f9f327` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#700) (renovate[bot], 2025-11-03)
- `8cfe3a4358e2` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m8 (#702) (renovate[bot], 2025-11-03)

### Documentation

- `c8c72e072ad8` Docs: update micronaut-docs to 3.0.0 (#697) (issam liqali, 2025-10-17)

### Internal

- `55dc7d6fc248` ci: projectVersion=5.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-10-13)
- `ac5ebd58ddae` ci: projectVersion=4.4.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-10-13)

### Review Candidates

- `75a2b19cd7f6` update versions (Sergio del Amo, 2026-05-07)
- `379b64163041` Update common files (#757) (micronaut-build, 2026-05-07)
- `c90ef4a45dda` Update common files (#755) (micronaut-build, 2026-05-05)
- `1464dd8039c6` Update managed.activemq.jakarta to v6.2.5 (#752) (renovate[bot], 2026-05-02)
- `b006ac6fcb82` Update common files (#754) (micronaut-build, 2026-05-01)
- `53dededbdf91` Update common files (#753) (micronaut-build, 2026-04-29)
- `ed0543168dbc` Update common files (#747) (micronaut-build, 2026-04-26)
- `e407612d3385` [skip ci] Release v5.0.0-M2 (micronaut-build, 2026-04-17)
- `72ffd7438e8d` Update managed.activemq.jakarta to v6.2.4 (#742) (renovate[bot], 2026-04-17)
- `35269d2d0e48` Update common files (#738) (micronaut-build, 2026-04-17)
- `d3d8782d6cbc` Update softprops/action-gh-release action to v2.6.2 (#740) (renovate[bot], 2026-04-17)
- `85a84ed6d78f` Update gradle/actions action to v6 (#741) (renovate[bot], 2026-04-17)
- `fef500c304da` Use LocalStack 4.14.0 docker image (#743) (Issam Liqali, 2026-04-01)
- `af19237c39db` [skip ci] Release v5.0.0-M1 (micronaut-build, 2026-02-24)
- `465cf6cad3ca` Update to micronaut 5 (#722) (issam liqali, 2026-02-24)
- `fe056770e87a` testcontainers-junit-jupiter (Sergio del Amo, 2026-02-24)
- `f5d43e456184` M17 (Sergio del Amo, 2026-02-17)
- `ebedf432a59f` micronaut-test-resources = "3.0.0-M6" (Sergio del Amo, 2026-02-17)
- `ba56b3a5c60a` micronaut-logging = "2.0.0-M1" (Sergio del Amo, 2026-02-17)
- `16a0176279d3` micronaut-validation = "5.0.0-M1" (Sergio del Amo, 2026-02-17)
- `d83771a0222c` micronaut-test = "5.0.0-M6" (Sergio del Amo, 2026-02-17)
- `fb54ed887604` micronaut = "5.0.0-M10" (Sergio del Amo, 2026-02-17)
- `e6c16914990d` Update common files (#723) (micronaut-build, 2026-02-16)
- `32ee45bb968f` Update common files (#706) (micronaut-build, 2025-12-10)
- `19098a73b441` Replace Micronaut nullability annotations with JSpecify annotations (#720) (Copilot, 2025-12-01)
- `e96f79a3225e` Micronaut 5 compatibility (#701) (issam liqali, 2025-11-03)
- `710ef276d556` Update common files (#699) (micronaut-build, 2025-11-03)
- `94f1203a42e6` Update common files (#698) (micronaut-build, 2025-10-17)
- `860c138585b8` Micronaut Gradle build plugin 8.0.0-M4 (Sergio del Amo, 2025-10-13)
- `acc86e0bf811` gradle 9.1 (Sergio del Amo, 2025-10-13)
- `97adbec2ff75` platform 4.9.4 (Sergio del Amo, 2025-10-13)
- `359b879a625d` junit-platform-launcher (Sergio del Amo, 2025-10-13)
- `5f889510d741` logging 1.7.1 (Sergio del Amo, 2025-10-13)
- `719f27d64465` test 4.9.0 (Sergio del Amo, 2025-10-13)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` buildSrc/build.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.jms-application.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.jms-examples.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.jms-module.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.jms-tests.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` settings.gradle
- `M` tests/tasks-activemq-artemis/build.gradle.kts
- `M` tests/tasks-activemq-classic/build.gradle.kts
- `M` tests/tasks-sqs/build.gradle.kts

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
- `M` docs-examples/example-groovy/build.gradle
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/jms/docs/AbstractJmsSpec.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/jms/docs/binding/MapConsumer.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/jms/docs/binding/MapProducer.groovy
- `A` docs-examples/example-groovy/src/test/groovy/io/micronaut/jms/docs/configuration/ActiveMQXAConnectionBeanFactory.groovy
- `D` docs-examples/example-groovy/src/test/groovy/io/micronaut/jms/docs/configuration/CustomBrokerJMSConnectionPoolListener.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/jms/docs/configuration/CustomBrokerSpec.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/jms/docs/configuration/CustomizeBrokerSpec.groovy
- `A` docs-examples/example-groovy/src/test/groovy/io/micronaut/jms/docs/configuration/JmsConnectionPoolActiveMQXAConnectionFactory.groovy
- `M` docs-examples/example-java/build.gradle
- `M` docs-examples/example-java/src/test/java/io/micronaut/jms/docs/AbstractJmsSpec.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/jms/docs/binding/BindingSpec.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/jms/docs/binding/MapConsumer.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/jms/docs/binding/MapProducer.java
- `A` docs-examples/example-java/src/test/java/io/micronaut/jms/docs/configuration/ActiveMQXAConnectionBeanFactory.java
- `D` docs-examples/example-java/src/test/java/io/micronaut/jms/docs/configuration/CustomBrokerJMSConnectionPoolListener.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/jms/docs/configuration/CustomBrokerSpec.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/jms/docs/configuration/CustomizeBrokerSpec.java
- `A` docs-examples/example-java/src/test/java/io/micronaut/jms/docs/configuration/JmsConnectionPoolActiveMQXAConnectionFactory.java
- `M` docs-examples/example-kotlin/build.gradle.kts
- `D` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/jms/docs/AbstractJmsKotest.kt
- `A` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/jms/docs/AbstractJmsSpec.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/jms/docs/binding/BindingSpec.kt
- `A` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/jms/docs/configuration/ActiveMQXAConnectionBeanFactory.kt
- `D` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/jms/docs/configuration/CustomBrokerJMSConnectionPoolListener.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/jms/docs/configuration/CustomBrokerSpec.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/jms/docs/configuration/CustomizeBrokerJMSConnectionPoolListener.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/jms/docs/configuration/CustomizeBrokerSpec.kt
- `A` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/jms/docs/configuration/JmsConnectionPoolActiveMQXAConnectionFactory.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/jms/docs/exceptions/ErrorHandlingSpec.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/jms/docs/exceptions/ErrorThrowingConsumer.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/jms/docs/quickstart/QuickstartSpec.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/jms/docs/successhandler/SuccessHandlingSpec.kt
- `M` src/main/docs/guide/breaks.adoc
- `M` src/main/docs/guide/configuration/customizing.adoc
- `M` src/main/docs/guide/configuration/otherBrokers.adoc

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
- `M` jms-activemq-artemis/src/main/java/io/micronaut/jms/activemq/artemis/configuration/ActiveMqArtemisConfiguration.java
- `A` jms-activemq-artemis/src/main/java/io/micronaut/jms/activemq/artemis/configuration/JmsConnectionPoolActiveMQJMSConnectionFactory.java
- `M` jms-activemq-artemis/src/main/java/io/micronaut/jms/activemq/artemis/configuration/properties/ActiveMqArtemisConfigurationProperties.java
- `M` jms-activemq-classic/src/main/java/io/micronaut/jms/activemq/classic/configuration/ActiveMqClassicConfiguration.java
- `A` jms-activemq-classic/src/main/java/io/micronaut/jms/activemq/classic/configuration/JmsConnectionPoolActiveMQConnectionFactory.java
- `M` jms-activemq-classic/src/main/java/io/micronaut/jms/activemq/classic/configuration/properties/ActiveMqClassicConfigurationProperties.java
- `M` jms-core/src/main/java/io/micronaut/jms/configuration/AbstractJMSListenerMethodProcessor.java
- `D` jms-core/src/main/java/io/micronaut/jms/configuration/JMSConnectionFactoryBeanProcessor.java
- `M` jms-core/src/main/java/io/micronaut/jms/listener/JMSListenerErrorHandler.java
- `M` jms-core/src/main/java/io/micronaut/jms/listener/JMSListenerSuccessHandler.java
- `M` jms-core/src/main/java/io/micronaut/jms/model/JMSHeaders.java
- `M` jms-core/src/main/java/io/micronaut/jms/model/MessageType.java
- `M` jms-core/src/main/java/io/micronaut/jms/templates/JmsConsumer.java
- `M` jms-core/src/main/java/io/micronaut/jms/templates/JmsProducer.java
- `M` jms-core/src/main/java/io/micronaut/jms/util/Assert.java
- `A` jms-sqs/src/main/java/io/micronaut/jms/sqs/configuration/JmsConnectionPoolSQSConnectionFactory.java
- `M` jms-sqs/src/main/java/io/micronaut/jms/sqs/configuration/SqsConfiguration.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `D` tests/tasks-activemq-artemis/src/main/resources/application.yml
- `A` tests/tasks-activemq-artemis/src/test/java/example/ActiveMqArtemis.java
- `M` tests/tasks-activemq-artemis/src/test/java/example/TasksTest.java
- `A` tests/tasks-activemq-artemis/src/test/resources/META-INF/native-image/reflect-config.json
- `A` tests/tasks-activemq-artemis/src/test/resources/logback.xml
- `A` tests/tasks-activemq-classic/src/main/resources/META-INF/native-image/reflect-config.json
- `A` tests/tasks-activemq-classic/src/main/resources/application.properties
- `D` tests/tasks-activemq-classic/src/main/resources/application.yml
- `A` tests/tasks-activemq-classic/src/test/java/example/ActiveMq.java
- `M` tests/tasks-activemq-classic/src/test/java/example/TasksTest.java
- `M` tests/tasks-sqs/src/main/java/example/SqsClientBuilderListener.java
- `A` tests/tasks-sqs/src/test/java/example/LocalStack.java
- `M` tests/tasks-sqs/src/test/java/example/TasksTest.java

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

