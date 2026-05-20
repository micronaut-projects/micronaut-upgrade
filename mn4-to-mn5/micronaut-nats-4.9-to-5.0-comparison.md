Compared as mn4/4.9.x -> mn5/5.0.x based on branch metadata.

  Scope:

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-nats, branch 4.9.x, commit
    d001e072eb4fc765d7198e439ccd808c9de62abe
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-nats, branch 5.0.x, commit
    af5419124f6b21b8086db753a8a71ba752895521
  - Both are clean and use the same remote: micronaut-projects/micronaut-nats

  Generated full report: /private/tmp/micronaut-nats-4.9-to-5.0-comparison.md:1

  Key findings:

  - 120 files changed: 27 added, 93 modified; 4,397 insertions, 533 deletions.
  - Main platform moves to Micronaut 5: projectVersion 4.9.1-SNAPSHOT -> 5.0.1-SNAPSHOT, micronaut 4.10.4 ->
    5.0.0, micronaut-platform 4.9.4 -> 5.0.0-RC1.
  - Build tooling moves substantially: Gradle 8.14.3 -> 9.5.1, Micronaut Gradle plugin 4.5.5 -> 5.0.0-M1,
    shared settings plugin 7.6.4 -> 8.0.0-M18, .sdkmanrc adds java=25.0.1-graal.
  - Runtime source changes are mostly Micronaut 5 compatibility: nullability annotations move from
    io.micronaut.core.annotation.* to org.jspecify.annotations.*, and ExecutableMethodProcessor.process
    signatures are updated for newer generics. I did not see public NATS classes or methods removed in nats/
    src/main/java.
  - Dependency updates include jnats 2.23.0 -> 2.25.3, Micrometer 5.13.0 -> 6.0.0, Reactor 3.9.0 -> 4.0.0,
    RxJava3 3.8.0 -> 4.0.0-RC1, Serde 2.15.5 -> 3.0.0.
  - Test resources usage was replaced in examples with a new test-suite-nats-utils module using Testcontainers
    directly.
  - CI/release changes move builds to Java 25, pin or update GitHub Actions, add a vulnerability audit
    workflow/script, and adjust release artifact/provenance handling.

  I did not run tests; this was a folder comparison and diff inspection pass.

# Release Note Comparison

Generated: 2026-05-19 09:14 UTC
Comparison: `4.9.x` -> `5.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-nats` | `4.9.x` | `d001e072eb4f` | `git@github.com:micronaut-projects/micronaut-nats.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-nats` | `5.0.x` | `af5419124f6b` | `git@github.com:micronaut-projects/micronaut-nats.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-nats`
- Commit candidates found: 58
- File changes listed: 120
- Version values listed: 27
- File status counts: A=27, M=93

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `4.9.1-SNAPSHOT` | `5.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.gradle-kotlin` | `org.jetbrains.kotlin:kotlin-gradle-plugin (version.ref=kotlin)` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.gradle-kotlin-allopen` | `org.jetbrains.kotlin:kotlin-allopen (version.ref=kotlin)` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.gradle-kotlin-noarg` | `org.jetbrains.kotlin:kotlin-noarg (version.ref=kotlin)` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.gradle-micronaut` | `io.micronaut.gradle:micronaut-gradle-plugin:4.5.5` | `io.micronaut.gradle:micronaut-gradle-plugin:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-logging` | `io.micronaut.logging:micronaut-logging-bom:1.7.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-micrometer` | `io.micronaut.micrometer:micronaut-micrometer-bom:5.13.0` | `io.micronaut.micrometer:micronaut-micrometer-bom:6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-reactor` | `micronaut-reactor:3.9.0` | `micronaut-reactor:4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-rxjava3` | `micronaut-rxjava3:3.8.0` | `micronaut-rxjava3:4.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.15.5` | `io.micronaut.serde:micronaut-serde-bom:3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-resources` | `io.micronaut.testresources:micronaut-test-resources-bom:2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.24` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.4` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.5.5` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-micrometer` | `5.13.0` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-platform` | `4.9.4` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-reactor` | `3.9.0` | `4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-rxjava3` | `3.8.0` | `4.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.15.5` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.9.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test-resources` | `2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |
| `settings.gradle` | `plugin.io.micronaut.build.shared.settings` | `7.6.4` | `8.0.0-M18` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Fixes

- `3502a0e2bac9` fix(deps): update dependency io.nats:jnats to v2.25.3 (#661) (renovate[bot], 2026-05-08)
- `85695f9874ae` fix(deps): update micronaut dependencies (renovate[bot], 2026-04-30)
- `90775ef0abb6` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m24 (#669) (renovate[bot], 2026-04-22)
- `90f9a86d4132` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m17 (#660) (renovate[bot], 2026-03-17)
- `163e2e892d88` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.12 (#651) (renovate[bot], 2025-12-31)
- `2e9ea4ebe980` fix(deps): update dependency io.micronaut.rxjava3:micronaut-rxjava3 to v3.9.0 (#640) (renovate[bot], 2025-12-10)
- `e7dea1860d22` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#642) (renovate[bot], 2025-12-10)
- `ba826af03721` fix(deps): update dependency io.micronaut.reactor:micronaut-reactor-bom to v3.9.1 (#639) (renovate[bot], 2025-12-10)
- `61f041215d91` fix(deps): update dependency io.micronaut.micrometer:micronaut-micrometer-bom to v5.13.2 (#637) (renovate[bot], 2025-12-10)
- `0b473444155e` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#636) (renovate[bot], 2025-12-10)
- `3ca1a28a10d2` fix(deps): update kotlin monorepo to v2.2.21 (#634) (renovate[bot], 2025-12-10)
- `f3e3a2eac615` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.1 (#624) (renovate[bot], 2025-11-03)
- `db8b6150858b` fix(deps): update dependency io.micronaut.logging:micronaut-logging-bom to v1.7.1 (#619) (renovate[bot], 2025-10-14)

### Dependency Updates

- `af5419124f6b` chore: Bump version to 5.0.1-SNAPSHOT (micronaut-build, 2026-05-18)
- `45f9c5debeb5` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-05-08)
- `4ee86e1fe415` chore(deps): update gradle to v9.5.0 (#663) (renovate[bot], 2026-05-08)
- `a5e1822b01e1` Merge pull request #673 from micronaut-projects/renovate/micronaut-dependencies (Graeme Rocher, 2026-05-01)
- `80bf5ec75f00` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#659) (renovate[bot], 2026-03-17)
- `d71a3b2f63e4` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2025-12-31)
- `23f03a349edb` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m13 (#653) (renovate[bot], 2025-12-31)
- `7f6436aed111` chore(deps): update actions/cache action to v5 (#655) (renovate[bot], 2025-12-31)
- `305022bddac7` chore(deps): update github artifact actions (#656) (renovate[bot], 2025-12-31)
- `690285d6cddf` chore(deps): update actions/checkout action to v6.0.1 (#643) (renovate[bot], 2025-12-10)
- `2ad2c2f10f39` chore(deps): update gradle to v9.2.1 (#638) (renovate[bot], 2025-12-10)
- `de71ff559bc2` chore(deps): update softprops/action-gh-release action to v2.5.0 (#635) (renovate[bot], 2025-12-10)
- `68501f28f11d` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#633) (renovate[bot], 2025-12-10)
- `e8e383ca3097` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#629) (renovate[bot], 2025-11-03)
- `c048e6d3e1cd` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m8 (#630) (renovate[bot], 2025-11-03)
- `f0c37d20ecb8` chore(deps): update gradle to v9.2.0 (#631) (renovate[bot], 2025-11-03)
- `92d33e870786` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m4 (#622) (renovate[bot], 2025-10-14)
- `d32b91d5e488` ci: projectVersion 5.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-10-07)

### Documentation

- `a966c89e905d` Docs: update micronaut-docs to 3.0.0 (#623) (issam liqali, 2025-10-14)

### Internal

- `17aff67180cd` Build: Update to Micronaut 5 (#652) (issam liqali, 2025-12-31)
- `dccd4960b960` build: Micronaut gradle Build plugin 8.0.0-M3 (Sergio del Amo, 2025-10-07)

### Review Candidates

- `131cdd7ca08c` [skip ci] Release v5.0.0 (micronaut-build, 2026-05-18)
- `e5ed0767352b` fix kotlin compilation (Sergio del Amo, 2026-05-18)
- `5527e3faae5c` micronaut-micrometer = "6.0.0" (Sergio del Amo, 2026-05-18)
- `1717079ac477` Update common files (#677) (micronaut-build, 2026-05-18)
- `c7a937ced2dc` Update versions (Sergio del Amo, 2026-05-14)
- `ace0b62ace36` micronaut-platform = "5.0.0-RC1" (Sergio del Amo, 2026-05-13)
- `3fbfc01a2e9e` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `6dd694ab2668` update versions (Sergio del Amo, 2026-05-08)
- `7a58fe360a47` Update common files (#676) (micronaut-build, 2026-05-13)
- `d0bb4982e4c2` [skip ci] Release v5.0.0-RC1 (micronaut-build, 2026-05-08)
- `a2defb824bf6` Update common files (#675) (micronaut-build, 2026-05-08)
- `05667c1cb46d` Merge pull request #674 from micronaut-projects/sync-files-5.0.x (Graeme Rocher, 2026-05-01)
- `ad15155a6c1f` Update common files (micronaut-build, 2026-04-30)
- `20cbe70ce545` Merge pull request #667 from micronaut-projects/sync-files-5.0.x (Graeme Rocher, 2026-04-26)
- `d149eb0b3175` Update common files (micronaut-build, 2026-04-23)
- `9888f1cd3c9e` [nats] Update common files for branch 5.0.x (#658) (micronaut-build, 2026-03-17)
- `06cb3d76aa4e` [skip ci] Release v5.0.0-M1 (micronaut-build, 2025-12-31)
- `8455797efd17` Update common files (#650) (micronaut-build, 2025-12-31)
- `006713040a62` Update common files (#632) (micronaut-build, 2025-12-10)
- `57ee303e23a7` Replace Micronaut nullability annotations with JSpecify (#647) (Copilot, 2025-12-02)
- `437267a4afde` Micronaut 5 compatibility (#628) (issam liqali, 2025-11-03)
- `49f23809a928` Update common files (#627) (micronaut-build, 2025-11-03)
- `6653d58a6b65` Update common files (#625) (micronaut-build, 2025-10-17)
- `0988e0f748f5` gradle 9.1.0 (Sergio del Amo, 2025-10-07)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` buildSrc/build.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.nats-examples.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` nats/build.gradle
- `M` settings.gradle
- `A` test-suite-nats-utils/build.gradle

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
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/nats/docs/consumer/connection/ConnectionSpec.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/nats/docs/consumer/custom/annotation/SIDSpec.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/nats/docs/consumer/custom/type/ProductInfoSpec.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/nats/docs/consumer/queue/QueueSpec.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/nats/docs/consumer/types/TypeBindingSpec.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/nats/docs/headers/HeadersSpec.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/nats/docs/jetstream/JetstreamSpec.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/nats/docs/jetstream/kv/KeyValueSpec.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/nats/docs/jetstream/os/ObjectStoreSpec.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/nats/docs/parameters/BindingSpec.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/nats/docs/quickstart/QuickstartSpec.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/nats/docs/rpc/RpcUppercaseSpec.groovy
- `M` docs-examples/example-groovy/src/test/groovy/io/micronaut/nats/docs/serdes/ProductInfoSerDesSpec.groovy
- `M` docs-examples/example-groovy/src/test/resources/application.yml
- `M` docs-examples/example-java/build.gradle
- `M` docs-examples/example-java/src/test/java/io/micronaut/nats/docs/consumer/connection/ConnectionSpec.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/nats/docs/consumer/custom/annotation/SIDSpec.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/nats/docs/consumer/custom/type/ProductInfo.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/nats/docs/consumer/custom/type/ProductInfoSpec.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/nats/docs/consumer/queue/QueueSpec.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/nats/docs/consumer/types/TypeBindingSpec.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/nats/docs/headers/HeadersSpec.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/nats/docs/headers/ProductListener.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/nats/docs/jetstream/JetstreamTest.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/nats/docs/jetstream/kv/KeyValueTest.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/nats/docs/jetstream/os/ObjectStoreTest.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/nats/docs/parameters/BindingSpec.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/nats/docs/quickstart/QuickstartSpec.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/nats/docs/rpc/RpcUppercaseSpec.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/nats/docs/serdes/ProductInfo.java
- `M` docs-examples/example-java/src/test/java/io/micronaut/nats/docs/serdes/ProductInfoSerDesSpec.java
- `M` docs-examples/example-java/src/test/resources/application.yml
- `M` docs-examples/example-kotlin/build.gradle
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/nats/docs/ProjectConfig.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/nats/docs/consumer/connection/ConnectionSpec.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/nats/docs/consumer/custom/annotation/SIDSpec.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/nats/docs/consumer/custom/type/ProductInfoSpec.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/nats/docs/consumer/queue/QueueSpec.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/nats/docs/consumer/types/ProductListener.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/nats/docs/consumer/types/TypeBindingSpec.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/nats/docs/headers/HeadersSpec.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/nats/docs/headers/ProductListener.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/nats/docs/jetstream/JetstreamSpec.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/nats/docs/jetstream/kv/KeyValueSpec.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/nats/docs/jetstream/os/ObjectStoreSpec.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/nats/docs/parameters/BindingSpec.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/nats/docs/quickstart/QuickstartSpec.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/nats/docs/rpc/RpcUppercaseSpec.kt
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/nats/docs/serdes/ProductInfoSerDesSpec.kt
- `M` docs-examples/example-kotlin/src/test/resources/application.yml

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
- `M` nats/src/main/java/io/micronaut/nats/ConsumerRegistry.java
- `M` nats/src/main/java/io/micronaut/nats/connect/NatsConnectionFactoryConfig.java
- `M` nats/src/main/java/io/micronaut/nats/exception/NatsListenerException.java
- `M` nats/src/main/java/io/micronaut/nats/intercept/NatsConsumerAdvice.java
- `M` nats/src/main/java/io/micronaut/nats/jetstream/KeyValueFactory.java
- `M` nats/src/main/java/io/micronaut/nats/jetstream/ObjectStoreFactory.java
- `M` nats/src/main/java/io/micronaut/nats/jetstream/PullConsumerRegistry.java
- `M` nats/src/main/java/io/micronaut/nats/jetstream/PushConsumerRegistry.java
- `M` nats/src/main/java/io/micronaut/nats/jetstream/bind/AcknowledgementBinder.java
- `M` nats/src/main/java/io/micronaut/nats/jetstream/bind/NatsAcknowledgement.java
- `M` nats/src/main/java/io/micronaut/nats/jetstream/exception/JetStreamListenerException.java
- `M` nats/src/main/java/io/micronaut/nats/jetstream/intercept/JetStreamPushConsumerAdvice.java
- `M` nats/src/main/java/io/micronaut/nats/serdes/JavaLangNatsMessageSerDes.java
- `M` nats/src/main/java/io/micronaut/nats/serdes/JsonNatsMessageSerDes.java
- `M` nats/src/main/java/io/micronaut/nats/serdes/NatsMessageSerDes.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` nats/src/test/groovy/io/micronaut/nats/AbstractNatsTest.groovy
- `M` nats/src/test/groovy/io/micronaut/nats/connect/BasicAuthenticationSpec.groovy
- `M` nats/src/test/groovy/io/micronaut/nats/connect/MultipleServerSpec.groovy
- `M` nats/src/test/groovy/io/micronaut/nats/jetstream/AbstractJetstreamTest.groovy
- `A` test-suite-nats-utils/src/main/java/io/micronaut/nats/testcontainers/Nats.java

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

