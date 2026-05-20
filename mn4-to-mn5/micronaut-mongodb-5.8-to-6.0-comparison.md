Compared micronaut-mongodb as mn4 → mn5.

  Scope

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-mongodb, branch 5.8.x, SHA a748f2c
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-mongodb, branch 6.0.x, SHA e9b6ed0
  - Report: /private/tmp/micronaut-mongodb-5.8-to-6.0-comparison.md

  Key Findings

  - projectVersion moves from 5.8.0-SNAPSHOT to 6.0.2-SNAPSHOT.
  - Core platform moves to Micronaut 5.0.0; Gradle wrapper moves 8.14.3 → 9.5.1; Java 25.0.1-graal is added
    via .sdkmanrc.
  - MongoDB Java drivers move from 4.11.5 to 5.7.0.
  - New mongo-coroutine module adds Kotlin coroutine MongoDB driver support.
  - New MongoClientSettingsBuilderCustomizer extension point supports programmatic MongoClientSettings
    customization, including CSFLE examples in docs.
  - New graceful shutdown behavior adds mongodb.shutdown-delay and client tracking/closer logic.
  - Reactive health check now uses Document("buildInfo", 1), fixing encrypted-client health checks.
  - BSON discriminator support was added for introspected types annotated with @BsonDiscriminator.
  - Test resources usage was reduced/reworked in favor of a direct Testcontainers helper module.

  Diff size: 109 files changed, 6125 insertions, 243 deletions. I did not run tests; this was a folder
  comparison only.

# Release Note Comparison

Generated: 2026-05-19 09:42 UTC
Comparison: `5.8.x` -> `6.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-mongodb` | `5.8.x` | `a748f2c6d652` | `git@github.com:micronaut-projects/micronaut-mongodb.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-mongodb` | `6.0.x` | `e9b6ed07341a` | `git@github.com:micronaut-projects/micronaut-mongodb.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-mongodb`
- Commit candidates found: 145
- File changes listed: 109
- Version values listed: 29
- File status counts: A=58, D=3, M=48

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `5.8.0-SNAPSHOT` | `6.0.2-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.gradle-micronaut` | `io.micronaut.gradle:micronaut-gradle-plugin:4.5.5` | `io.micronaut.gradle:micronaut-gradle-plugin:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-mongo-core` | `org.mongodb:mongodb-driver-core:4.11.5` | `org.mongodb:mongodb-driver-core:5.7.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-mongo-coroutine` | `not present` | `org.mongodb:mongodb-driver-kotlin-coroutine:5.7.0` | `added` |
| `gradle/libs.versions.toml` | `libraries.managed-mongo-crypt` | `not present` | `org.mongodb:mongodb-crypt:5.7.0` | `added` |
| `gradle/libs.versions.toml` | `libraries.managed-mongo-driver` | `org.mongodb:mongodb-driver-sync:4.11.5` | `org.mongodb:mongodb-driver-sync:5.7.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-mongo-reactive` | `org.mongodb:mongodb-driver-reactivestreams:4.11.5` | `org.mongodb:mongodb-driver-reactivestreams:5.7.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-logging` | `io.micronaut.logging:micronaut-logging-bom:1.7.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-micrometer` | `io.micronaut.micrometer:micronaut-micrometer-bom:5.13.0` | `io.micronaut.micrometer:micronaut-micrometer-bom:6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.15.5` | `io.micronaut.serde:micronaut-serde-bom:3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test` | `io.micronaut.test:micronaut-test-bom:4.9.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-resources` | `io.micronaut.testresources:micronaut-test-resources-bom:2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-validation` | `io.micronaut.validation:micronaut-validation-bom:4.11.0` | `io.micronaut.validation:micronaut-validation-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.27` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.managed-mongo` | `4.11.5` | `5.7.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-mongo-reactive` | `4.11.5` | `5.7.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.4` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.5.5` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-micrometer` | `5.13.0` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-platform` | `4.9.4` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.15.5` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.9.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test-resources` | `2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.11.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Features

- `84535ca16c03` Add support for the Kotlin coroutine driver (#895) (Graeme Rocher, 2026-04-29)
- `4ede838deed0` Add MongoClientSettings customization support for CSFLE (#881) (Graeme Rocher, 2026-04-16)

### Fixes

- `87b539012b17` fix(deps): update micronaut dependencies (#892) (renovate[bot], 2026-04-23)
- `eeb84cc48186` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m23 (#885) (renovate[bot], 2026-04-19)
- `0ed53c655bfe` fix(deps): update mongo-java-driver monorepo to v5.6.5 (#877) (renovate[bot], 2026-04-15)
- `f4beb82d788c` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m22 (#876) (renovate[bot], 2026-04-15)
- `3fd4152e2c93` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m6 (#874) (renovate[bot], 2026-04-03)
- `47d8d8aeb68b` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m19 (#873) (renovate[bot], 2026-04-01)
- `f8a516d56889` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m5 (#872) (renovate[bot], 2026-03-28)
- `7f6adcd76127` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m4 (#871) (renovate[bot], 2026-03-26)
- `2de64437e5e6` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m18 (#870) (renovate[bot], 2026-03-26)
- `f84663895aa9` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m3 (#868) (renovate[bot], 2026-03-25)
- `de931b19b19e` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m17 (#863) (renovate[bot], 2026-03-15)
- `e59c3f7d7f6d` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m16 (#861) (renovate[bot], 2026-03-07)
- `2d85bab6495d` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m15 (#858) (renovate[bot], 2026-03-03)
- `d541fe9a7c73` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m14 (#855) (renovate[bot], 2026-02-26)
- `343eeede87af` fix(deps): update mongo-java-driver monorepo to v5.6.4 (#854) (renovate[bot], 2026-02-23)
- `40166a8be472` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m13 (#853) (renovate[bot], 2026-02-20)
- `585bdec39ef6` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m12 (#852) (renovate[bot], 2026-02-19)
- `a47a9373a22b` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m11 (#851) (renovate[bot], 2026-02-17)
- `005ccf73b76b` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m10 (#848) (renovate[bot], 2026-02-05)
- `f2fe3fc60efd` fix(deps): update mongo-java-driver monorepo to v5.6.3 (#846) (renovate[bot], 2026-02-04)
- `ed16e1f84bb9` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.2 (#845) (renovate[bot], 2026-02-04)
- `cf6d8230ede4` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m9 (#839) (renovate[bot], 2026-01-25)
- `05c7ca168d8b` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m2 (#837) (renovate[bot], 2026-01-14)
- `b7115f1b17c1` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m8 (#836) (renovate[bot], 2026-01-13)
- `987f4665eb13` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m7 (#835) (renovate[bot], 2026-01-11)
- `4ee760df9d65` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m6 (#829) (renovate[bot], 2025-12-23)
- `91661cee5253` fix(deps): update mongo-java-driver monorepo to v5.6.2 (#828) (renovate[bot], 2025-12-21)
- `ac22a63e819d` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.10 (#825) (renovate[bot], 2025-12-12)
- `32b5a70525f7` fix(deps): update dependency io.micronaut.micrometer:micronaut-micrometer-bom to v5.13.2 (#822) (renovate[bot], 2025-12-06)
- `0acb63799855` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#814) (renovate[bot], 2025-11-25)
- `2a30f6902197` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#808) (renovate[bot], 2025-11-11)
- `98e9d3c2703e` fix(deps): update dependency io.micronaut.test:micronaut-test-bom to v4.10.2 (#803) (renovate[bot], 2025-11-10)
- `c67f678bc9bd` fix(deps): update mongo-java-driver monorepo to v5 (major) (#805) (renovate[bot], 2025-11-10)
- `6a15aca94ac9` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.12.0 (#804) (renovate[bot], 2025-11-10)
- `bbf29800d70a` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.1 (#802) (renovate[bot], 2025-11-10)
- `d76623a645eb` fix(deps): update dependency io.micronaut.micrometer:micronaut-micrometer-bom to v5.13.1 (#797) (renovate[bot], 2025-11-03)
- `dd831e97694c` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.8 (#796) (renovate[bot], 2025-11-03)
- `8abdb75c1da2` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.6 (#791) (renovate[bot], 2025-10-17)
- `8a9ebe38e34b` fix(deps): update managed.mongo to v5 (major) (#654) (renovate[bot], 2024-11-06)
- `1378bbc1ad0c` fix(deps): update dependency org.mongodb:mongodb-driver-reactivestreams to v5 (#652) (renovate[bot], 2024-11-06)
- `45f3968aa8ee` fix(deps): update dependency org.mongodb:mongodb-driver-reactivestreams to v5.1.0 (#627) (renovate[bot], 2024-05-30)
- `84e541d6601e` fix(deps): update managed.mongo to v5.1.0 (#628) (renovate[bot], 2024-05-30)
- `668adfe7cc07` fix(deps): update dependency io.micronaut.micrometer:micronaut-micrometer-bom to v5.5.0 (#623) (renovate[bot], 2024-04-11)
- `c9b224b39d82` fix(deps): update dependency org.mongodb:mongodb-driver-reactivestreams to v5 (#604) (renovate[bot], 2024-04-01)
- `bfe2a466f290` fix(deps): update managed.mongo to v5 (major) (#605) (renovate[bot], 2024-04-01)
- `4e06b36856b8` fix(deps): update dependency io.micronaut.testresources:micronaut-test-resources-bom to v2.4.0 (#609) (renovate[bot], 2024-04-01)
- `5e80d0a34140` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.8.2 (#613) (renovate[bot], 2024-04-01)
- `e2bc4e586659` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.4.0 (#610) (renovate[bot], 2024-04-01)
- `9937b88c5659` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.4.4 (#606) (renovate[bot], 2024-04-01)
- `31231ab4d81e` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.3.5 (#608) (renovate[bot], 2024-04-01)

### Dependency Updates

- `bc3f45fbb52b` chore: Bump version to 6.0.2-SNAPSHOT (micronaut-build, 2026-05-14)
- `f827b6d08b25` Update dependency micronaut to v5.0.0-RC1 (#914) (renovate[bot], 2026-05-12)
- `7e1ba7b9469f` Update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-RC3 (#913) (renovate[bot], 2026-05-11)
- `3224259fb72c` Update dependency io.micronaut.micrometer:micronaut-micrometer-bom to v6.0.0-RC1 (#912) (renovate[bot], 2026-05-10)
- `2f6d878dba45` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2026-05-07)
- `240270b72a08` Update Micronaut dependencies (#909) (renovate[bot], 2026-05-07)
- `37f9e78359ac` Update Micronaut dependencies (#905) (renovate[bot], 2026-05-05)
- `6259c6eb6c22` Update Micronaut dependencies (#903) (renovate[bot], 2026-05-04)
- `51f5faa72951` Update dependency io.micronaut:micronaut-core-bom to v5.0.0-M26 (#898) (renovate[bot], 2026-05-01)
- `207a5502dbeb` build: combine Renovate dependency upgrades for issue 897 (#899) (Graeme Rocher, 2026-04-29)
- `7b24373410fe` Update micronaut-gradle-plugin version to 5.0.0-M1 (Sergio del Amo, 2026-04-28)
- `7bb31c87e0b2` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2026-04-24)
- `d4d13d2711df` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m18 (#893) (renovate[bot], 2026-04-23)
- `7c95197e7f15` Merge pull request #889 from micronaut-projects/dependency-upgrade/issue-888 (Graeme Rocher, 2026-04-19)
- `7396f3beb372` build: combine Renovate dependency upgrades for issue 888 (Graeme Rocher, 2026-04-19)
- `6dede56d771d` chore(deps): update gradle to v9.4.1 (#865) (renovate[bot], 2026-03-20)
- `4e07c0aeab67` chore(deps): update actions/download-artifact action to v8.0.1 (#862) (renovate[bot], 2026-03-14)
- `6425a0a423a8` chore(deps): update gradle to v9.4.0 (#860) (renovate[bot], 2026-03-09)
- `51e0d442e0e7` chore(deps): update github artifact actions (#856) (renovate[bot], 2026-02-27)
- `221e347a5dd4` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#850) (renovate[bot], 2026-02-17)
- `40e015d46d78` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m16 (#849) (renovate[bot], 2026-02-10)
- `d26a20e9b4d0` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m15 (#844) (renovate[bot], 2026-01-31)
- `185646ef635e` chore(deps): update gradle to v9.3.1 (#843) (renovate[bot], 2026-01-31)
- `5517c1f03660` chore(deps): update actions/checkout action to v6.0.2 (#840) (renovate[bot], 2026-01-27)
- `a2838184f9cd` chore(deps): update gradle to v9.3.0 (#838) (renovate[bot], 2026-01-27)
- `7e13d926d026` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m14 (#834) (renovate[bot], 2026-01-10)
- `08a1a8abf802` chore(deps): update graalvm/setup-graalvm action to v1.4.5 (#833) (renovate[bot], 2026-01-06)
- `d559fba00f10` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2025-12-19)
- `90563eedd8e1` chore(deps): update softprops/action-gh-release action to v2.5.0 (#820) (renovate[bot], 2025-12-10)
- `f667214465c3` chore(deps): update actions/checkout action to v6 (#813) (renovate[bot], 2025-12-10)
- `b0fc2205fd5e` chore(deps): update graalvm/setup-graalvm action to v1.4.4 (#821) (renovate[bot], 2025-12-03)
- `4f35d18e1a95` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#817) (renovate[bot], 2025-12-01)
- `8988f2a9808c` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m11 (#816) (renovate[bot], 2025-11-27)
- `d91d44cf2d9f` chore(deps): update graalvm/setup-graalvm action to v1.4.3 (#815) (renovate[bot], 2025-11-27)
- `706eb74e9783` chore(deps): update gradle to v9.2.1 (#811) (renovate[bot], 2025-11-19)
- `7c22c9476b81` chore(deps): update actions/checkout action to v5.0.1 (#810) (renovate[bot], 2025-11-19)
- `2a96332ddd3b` chore: Bump version to 6.0.1-SNAPSHOT (micronaut-build, 2025-11-10)
- `0441f869a0f0` chore(deps): update github artifact actions (#806) (renovate[bot], 2025-11-10)
- `ad5d3db29505` chore(deps): update mikepenz/action-junit-report action to v6 (#807) (renovate[bot], 2025-11-10)
- `cfbc58e59bb8` chore(deps): update softprops/action-gh-release action to v2.4.2 (#801) (renovate[bot], 2025-11-10)
- `fa69fc00ac27` chore(deps): update gradle to v9.2.0 (#800) (renovate[bot], 2025-11-10)
- `b32e5436b518` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m9 (#798) (renovate[bot], 2025-11-10)
- `4b0fa8ec6aec` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#795) (renovate[bot], 2025-11-03)
- `44208ed98c26` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m8 (#793) (renovate[bot], 2025-11-03)
- `977137eb4f47` chore(deps): update plugin io.micronaut.build.shared.settings to v6.7.0 (#607) (renovate[bot], 2024-04-01)

### Internal

- `82bbd7760e1a` Build: Update to Micronaut 5 (#827) (issam liqali, 2025-12-19)
- `ffa785ae10b9` Build: update micronaut build and gradle plugin (#794) (issam liqali, 2025-11-03)
- `25ea2b3c6b0f` ci: projectVersion=6.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2024-04-01)

### Review Candidates

- `e9b6ed07341a` Update versions (Sergio del Amo, 2026-05-19)
- `739dfe3ae255` [skip ci] Release v6.0.1 (micronaut-build, 2026-05-14)
- `1f4facab8b28` Update versions (Sergio del Amo, 2026-05-14)
- `6071589cd61b` Update plugin io.micronaut.build.shared.settings to v8.0.0-RC1 (#916) (renovate[bot], 2026-05-14)
- `840bf764ee89` Update Gradle to v9.5.1 (#915) (renovate[bot], 2026-05-13)
- `03f13e617b50` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `767a21b83442` Update common files (#911) (micronaut-build, 2026-05-09)
- `c9c016089a98` Update common files (#910) (micronaut-build, 2026-05-08)
- `632c668a0335` [skip ci] Release v6.0.0-RC1 (micronaut-build, 2026-05-07)
- `b0123a2a8b30` Update common files (#908) (micronaut-build, 2026-05-07)
- `127a4da9f5b6` Update common files (#907) (micronaut-build, 2026-05-06)
- `6e931d6e6459` Update Gradle to v9.5.0 (#906) (renovate[bot], 2026-05-06)
- `5b79f2a8f431` Update common files (#904) (micronaut-build, 2026-05-05)
- `dcf6a0c1ef51` Update Gradle to v9.5.0 (#896) (renovate[bot], 2026-05-04)
- `e5bbf29c5bfc` Update common files (#902) (micronaut-build, 2026-05-04)
- `6bb16a7d983a` Update common files (#900) (micronaut-build, 2026-05-01)
- `af4d4e90f70e` Update mongo-java-driver monorepo to v5.7.0 (#901) (renovate[bot], 2026-05-01)
- `164385fb229c` micronaut-test = "5.0.0-M7" (Sergio del Amo, 2026-04-28)
- `f0e0e0cd5596` micronaut-micrometer = "6.0.0-M2" (Sergio del Amo, 2026-04-28)
- `8e2f16eb627f` [skip ci] Release v6.0.1-M2 (micronaut-build, 2026-04-24)
- `36ec496417d1` Update common files (#891) (micronaut-build, 2026-04-22)
- `3d6056efaac3` Delay Mongo client shutdown during graceful shutdown (#878) (Graeme Rocher, 2026-04-21)
- `19be582a770d` Merge pull request #880 from micronaut-projects/issue-10-bson-discriminator (Graeme Rocher, 2026-04-21)
- `87ca85d324b6` Update common files (#883) (micronaut-build, 2026-04-20)
- `f07368ba9e9a` Fix Mongo health check for encrypted clients (#879) (Graeme Rocher, 2026-04-16)
- `92273d2704d8` Update common files (#875) (micronaut-build, 2026-04-09)
- `f8a4a1f9434d` Update common files (#869) (micronaut-build, 2026-03-25)
- `6c615db7243e` Update common files (#859) (micronaut-build, 2026-03-18)
- `5cd903c6defc` Update common files (#857) (micronaut-build, 2026-03-03)
- `6239a0a52870` Update common files (#847) (micronaut-build, 2026-02-05)
- `026c3170bce0` Update common files (#842) (micronaut-build, 2026-02-02)
- `672ff6cfd92e` Update common files (#832) (micronaut-build, 2026-01-27)
- `ab77f0df4830` Update common files (#826) (micronaut-build, 2025-12-29)
- `5e5410a17372` [skip ci] Release v6.0.1-M1 (micronaut-build, 2025-12-19)
- `6603b249d737` Update common files (#812) (micronaut-build, 2025-12-10)
- `b1458816107a` Update common files (#809) (micronaut-build, 2025-11-13)
- `3597c5eb0e08` [skip ci] Release v6.0.0 (micronaut-build, 2025-11-10)
- `2b480f7a9b10` Update common files (#792) (micronaut-build, 2025-11-03)
- `33eb992b1a10` Update common files (#790) (micronaut-build, 2025-10-17)
- `82b6be0bd5cb` Micronaut Build Gradle Plugin 8.0.0-M4 (Sergio del Amo, 2025-10-15)
- `2db46395f8ee` gradle 9.1 (Sergio del Amo, 2025-10-15)
- `bf7e684cbf96` Merge branch '5.8.x' into 6.0.x (Sergio del Amo, 2025-10-15)
- `94e68b8137da` Merge branch '5.5.x' into 6.0.x (Sergio del Amo, 2024-11-06)
- `fcc4e86acb3a` Merge pull request #641 from micronaut-projects/sync-files-6.0.x (Chaimaa Rouai, 2024-07-05)
- `3efb37d87553` Update common files (micronaut-build, 2024-05-31)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.mongodb-functional-test.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.mongodb-module.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` mongo-core/build.gradle
- `A` mongo-coroutine/build.gradle
- `M` mongo-reactive/build.gradle
- `M` mongo-sync/build.gradle
- `M` settings.gradle
- `A` test-suite-utils/build.gradle.kts
- `M` tests/mongo-pojo/build.gradle
- `M` tests/mongo-serde/build.gradle

### Documentation

- `A` .agents/skills/docs/SKILL.md
- `A` .agents/skills/docs/references/control-panel-patterns.md
- `A` .agents/skills/docs/references/micronaut-docs-providers.md
- `A` .agents/skills/guides/SKILL.md
- `A` .agents/skills/guides/references/guide-authoring-conventions.md
- `A` .agents/skills/guides/references/guide-inventory.md
- `A` .agents/skills/guides/references/pdf-export-and-pr.md
- `A` .agents/skills/guides/references/repository-workflow.md
- `M` .clinerules/docs.md
- `M` .github/instructions/docs.instructions.md
- `M` .github/workflows/release.yml
- `A` docs-examples/csfle-groovy/src/test/groovy/io/micronaut/mongodb/docs/AutoEncryptionCustomizer.groovy
- `A` docs-examples/csfle-java/src/test/java/io/micronaut/mongodb/docs/AutoEncryptionCustomizer.java
- `A` docs-examples/csfle-kotlin/src/test/kotlin/io/micronaut/mongodb/docs/AutoEncryptionCustomizer.kt
- `M` src/main/docs/guide/config.adoc
- `M` src/main/docs/guide/introduction.adoc
- `M` src/main/docs/guide/setup.adoc

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
- `M` mongo-core/src/main/java/io/micronaut/configuration/mongo/core/AbstractMongoConfiguration.java
- `M` mongo-core/src/main/java/io/micronaut/configuration/mongo/core/DefaultCodecRegistryBuilder.java
- `M` mongo-core/src/main/java/io/micronaut/configuration/mongo/core/DefaultMongoConfiguration.java
- `A` mongo-core/src/main/java/io/micronaut/configuration/mongo/core/MongoClientCloser.java
- `A` mongo-core/src/main/java/io/micronaut/configuration/mongo/core/MongoClientSettingsBuilderCustomizer.java
- `M` mongo-core/src/main/java/io/micronaut/configuration/mongo/core/MongoSettings.java
- `M` mongo-core/src/main/java/io/micronaut/configuration/mongo/core/NamedMongoConfiguration.java
- `M` mongo-core/src/main/java/io/micronaut/configuration/mongo/core/serde/DataCodecRegistry.java
- `A` mongo-coroutine/src/main/java/io/micronaut/configuration/mongo/coroutine/CoroutineSupport.java
- `A` mongo-coroutine/src/main/java/io/micronaut/configuration/mongo/coroutine/DefaultCoroutineMongoClientFactory.java
- `A` mongo-coroutine/src/main/java/io/micronaut/configuration/mongo/coroutine/MongoClientShutdownListener.java
- `A` mongo-coroutine/src/main/java/io/micronaut/configuration/mongo/coroutine/NamedCoroutineMongoClientFactory.java
- `A` mongo-coroutine/src/main/java/io/micronaut/configuration/mongo/coroutine/condition/RequiresMongo.java
- `A` mongo-coroutine/src/main/java/io/micronaut/configuration/mongo/coroutine/condition/package-info.java
- `A` mongo-coroutine/src/main/java/io/micronaut/configuration/mongo/coroutine/health/CoroutineMongoHealthIndicator.java
- `A` mongo-coroutine/src/main/java/io/micronaut/configuration/mongo/coroutine/health/package-info.java
- `A` mongo-coroutine/src/main/java/io/micronaut/configuration/mongo/coroutine/package-info.java
- `M` mongo-reactive/src/main/java/io/micronaut/configuration/mongo/reactive/DefaultReactiveMongoClientFactory.java
- `A` mongo-reactive/src/main/java/io/micronaut/configuration/mongo/reactive/MongoClientShutdownListener.java
- `M` mongo-reactive/src/main/java/io/micronaut/configuration/mongo/reactive/NamedReactiveMongoClientFactory.java
- `M` mongo-reactive/src/main/java/io/micronaut/configuration/mongo/reactive/health/MongoHealthIndicator.java
- `M` mongo-sync/src/main/java/io/micronaut/configuration/mongo/sync/DefaultMongoClientFactory.java
- `A` mongo-sync/src/main/java/io/micronaut/configuration/mongo/sync/MongoClientShutdownListener.java
- `M` mongo-sync/src/main/java/io/micronaut/configuration/mongo/sync/NamedMongoClientFactory.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `A` mongo-core/src/test/groovy/io/micronaut/configuration/mongo/core/MongoClientCloserSpec.groovy
- `A` mongo-coroutine/src/main/resources/META-INF/native-image/io.micronaut.configuration.mongo.coroutine.test/mongo-coroutine/native-image.properties
- `A` mongo-coroutine/src/test/groovy/io/micronaut/configuration/mongo/coroutine/CoroutineMongoHealthIndicatorSpec.groovy
- `A` mongo-coroutine/src/test/groovy/io/micronaut/configuration/mongo/coroutine/CoroutineSupportSpec.groovy
- `A` mongo-coroutine/src/test/groovy/io/micronaut/configuration/mongo/coroutine/MongoClientSettingsBuilderCustomizerSpec.groovy
- `A` mongo-coroutine/src/test/groovy/io/micronaut/configuration/mongo/coroutine/MongoClientShutdownListenerSpec.groovy
- `A` mongo-coroutine/src/test/groovy/io/micronaut/configuration/mongo/coroutine/MongoCoroutineConfigurationSpec.groovy
- `A` mongo-coroutine/src/test/resources/logback-test.xml
- `A` mongo-reactive/src/test/groovy/io/micronaut/configuration/mongo/reactive/MongoClientSettingsBuilderCustomizerSpec.groovy
- `M` mongo-reactive/src/test/groovy/io/micronaut/configuration/mongo/reactive/MongoHealthIndicatorSpec.groovy
- `M` mongo-reactive/src/test/groovy/io/micronaut/configuration/mongo/reactive/MongoReactiveConfigurationSpec.groovy
- `A` mongo-sync/src/test/groovy/io/micronaut/configuration/mongo/sync/MongoClientSettingsBuilderCustomizerSpec.groovy
- `M` mongo-sync/src/test/groovy/io/micronaut/configuration/mongo/sync/MongoConfigurationSpec.groovy
- `A` test-suite-utils/src/main/java/io/micronaut/mongodb/testcontainers/MongoDb.java
- `D` tests/mongo-pojo/src/test/java/example/AbstractMongoSpec.java
- `A` tests/mongo-pojo/src/test/java/example/Animal.java
- `M` tests/mongo-pojo/src/test/java/example/BookTest.java
- `A` tests/mongo-pojo/src/test/java/example/BsonDiscriminatorTest.java
- `A` tests/mongo-pojo/src/test/java/example/Dog.java
- `D` tests/mongo-pojo/src/test/resources/application-test.yml
- `M` tests/mongo-serde/src/test/java/example/BookTest.java
- `A` tests/mongo-serde/src/test/resources/application-test.properties
- `D` tests/mongo-serde/src/test/resources/application-test.yml

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

