Compared micronaut-redis as mn4 → mn5.

  Scope

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-redis, branch 6.10.x, SHA 47a9109
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-redis, branch 7.0.x, SHA 273b73c
  - Report: /private/tmp/micronaut-redis-6.10-to-7.0-comparison.md

  Key Findings

  - projectVersion moves from 6.9.1-SNAPSHOT to 7.0.1-SNAPSHOT.
  - Core platform moves to Micronaut 5.0.0; Lettuce moves 6.7.1.RELEASE → 7.5.1.RELEASE; Gradle wrapper moves
    8.14.3 → 9.5.1; Java 25.0.1-graal is added via .sdkmanrc.
  - Redis Lettuce was modularized into redis-lettuce-core, redis-lettuce-cache, redis-lettuce-session, and new
    redis-lettuce-pubsub; micronaut-redis-lettuce remains as a compatibility module for core/cache/session.
  - New Redis Pub/Sub support adds @RedisListener, @MessageChannel, @RedisPubSubClient, RedisPubSubPublisher,
    listener exception handling, and docs/examples.
  - Cache support adds namespace configuration, bulk getAll / putAll / multi-key invalidation, and retry
    settings for reads/inserts.
  - Connection/configuration fixes include redis.password support alongside redis.uri, propagation of auth and
    timeout settings into configured URIs, and pooled Lettuce connections for parallel reactive work.
  - Health checks can now reuse an existing managed Redis connection via redis.health.reuse-connection.
  - Breaking changes documented for 7.0.0: removed deprecated RedisHealthIndicator constructor and deprecated
    DefaultRedisClusterClientFactory.redisClient(AbstractRedisConfiguration, ClientResources) overload.

  Diff size: 217 files changed, 12331 insertions, 891 deletions. I did not run tests; this was a folder
  comparison only.

# Release Note Comparison

Generated: 2026-05-19 09:48 UTC
Comparison: `6.10.x` -> `7.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-redis` | `6.10.x` | `47a910972c6e` | `git@github.com:micronaut-projects/micronaut-redis.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-redis` | `7.0.x` | `273b73c954e6` | `git@github.com:micronaut-projects/micronaut-redis.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-redis`
- Commit candidates found: 130
- File changes listed: 217
- Version values listed: 26
- File status counts: A=125, D=4, M=33, R=55

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `6.9.1-SNAPSHOT` | `7.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.gradle-micronaut` | `io.micronaut.gradle:micronaut-gradle-plugin:4.5.4` | `io.micronaut.gradle:micronaut-gradle-plugin:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-lettuce` | `io.lettuce:lettuce-core:6.7.1.RELEASE` | `io.lettuce:lettuce-core:7.5.1.RELEASE` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-cache` | `io.micronaut.cache:micronaut-cache-bom:5.3.0` | `io.micronaut.cache:micronaut-cache-bom:6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-micrometer` | `io.micronaut.micrometer:micronaut-micrometer-bom:5.13.0` | `io.micronaut.micrometer:micronaut-micrometer-bom:6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.15.5` | `io.micronaut.serde:micronaut-serde-bom:3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-session` | `io.micronaut.session:micronaut-session-bom:4.7.0` | `io.micronaut.session:micronaut-session-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-resources` | `io.micronaut.testresources:micronaut-test-resources-bom:2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.testcontainers-redis` | `not present` | `com.redis.testcontainers:testcontainers-redis:1.6.4` | `added` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.23` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.managed-lettuce` | `6.7.1.RELEASE` | `7.5.1.RELEASE` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.4` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-cache` | `5.3.0` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.5.4` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.1` | `2.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-micrometer` | `5.13.0` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.15.5` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-session` | `4.7.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.9.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test-resources` | `2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.testcontainers-redis` | `not present` | `1.6.4` | `added` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |
| `settings.gradle` | `plugin.io.micronaut.build.shared.settings` | `7.6.4` | `8.0.0-M18` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `ce8e96ea3e39` Apply review feedback: eagerly compute merged URIs; remove brittle private-field access in test (copilot-swe-agent[bot], 2026-04-14)
- `50cdb2766db8` build: remove mainClassName (Sergio del Amo, 2025-10-14)
- `69fb2438b383` Remove deprecated methods for Micronaut Framework 5 and document breaking changes. (#500) (Dean Wette, 2024-03-07)

### Features

- `e3d9bb3247f4` Support redis.password alongside redis.uri (#760) (Graeme Rocher, 2026-04-28)
- `678de559522a` Support Redis Pub/Sub as message broker (#761) (Graeme Rocher, 2026-04-28)
- `247c939c74c7` Add configurable Redis cache namespace (#757) (Graeme Rocher, 2026-04-23)
- `e17a39f8a69b` Support top-level Redis codecs (#747) (Graeme Rocher, 2026-04-23)
- `b1cae74cc86c` Add pooled Lettuce connections for parallel reactive work (#741) (Graeme Rocher, 2026-04-23)
- `02cdc032025c` Support bulk get, put, and invalidate (#746) (Graeme Rocher, 2026-04-17)
- `b2915a416830` Add volatile to merged URI fields for safe publication across threads (copilot-swe-agent[bot], 2026-04-14)

### Fixes

- `836822fb53d7` fix(deps): update dependency io.micronaut.cache:micronaut-cache-bom to v6.0.0-m2 (renovate[bot], 2026-04-16)
- `37ebf4d10dbf` fix(deps): update dependency io.lettuce:lettuce-core to v7.5.1.release (renovate[bot], 2026-04-11)
- `77882e8e0a73` fix(deps): update dependency micronaut to v4.10.11 (renovate[bot], 2026-04-16)
- `2de86d4c662a` fix(deps): update dependency io.micronaut.test:micronaut-test-bom to v5.0.0-m8 (renovate[bot], 2026-04-16)
- `18604f2965d6` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m6 (#737) (renovate[bot], 2026-04-11)
- `d6e2c9d1caff` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m20 (#738) (renovate[bot], 2026-04-11)
- `941452f9a9c2` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m19 (#725) (renovate[bot], 2026-04-02)
- `937efb32630a` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.15 (#718) (renovate[bot], 2026-02-16)
- `aa7037241a43` fix(deps): update dependency micronaut to v4.10.8 (#719) (renovate[bot], 2026-02-16)
- `0828c4797551` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.2 (#722) (renovate[bot], 2026-02-16)
- `285cbc32972c` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.12 (#709) (renovate[bot], 2025-12-31)
- `1eb0bb1da13a` fix(deps): update dependency micronaut to v4.10.6 (#710) (renovate[bot], 2025-12-31)
- `9a65e00ebb57` fix(deps): update dependency micronaut to v4.10.3 (#698) (renovate[bot], 2025-12-10)
- `695fb4e6c1e5` fix(deps): update dependency io.micronaut.session:micronaut-session-bom to v4.8.0 (#697) (renovate[bot], 2025-12-10)
- `1f2ed084637f` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#696) (renovate[bot], 2025-12-10)
- `7396101eaf74` fix(deps): update dependency io.micronaut.micrometer:micronaut-micrometer-bom to v5.13.2 (#693) (renovate[bot], 2025-12-10)
- `fe24b0a32cf0` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.1 (#691) (renovate[bot], 2025-12-10)
- `023c8f09a244` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#690) (renovate[bot], 2025-12-10)
- `4828580a1468` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.0 (#682) (renovate[bot], 2025-10-17)
- `e415818c550e` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.6 (#684) (renovate[bot], 2025-10-17)
- `a626e3543032` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.9.0 (#512) (renovate[bot], 2024-04-11)
- `ec87463756e0` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.4.1 (#515) (renovate[bot], 2024-04-11)
- `32d5d0ae9922` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.3.6 (#513) (renovate[bot], 2024-04-11)
- `c25dd735979b` fix(deps): update dependency io.micronaut.cache:micronaut-cache-bom to v4.3.0 (#516) (renovate[bot], 2024-04-11)
- `fca4c4562b81` fix(deps): update dependency io.micronaut.micrometer:micronaut-micrometer-bom to v5.5.0 (#517) (renovate[bot], 2024-04-11)
- `8ae373d7bf5d` fix(deps): update dependency io.micronaut.session:micronaut-session-bom to v4.3.0 (#518) (renovate[bot], 2024-04-11)
- `37d4a07f07f8` fix(deps): update dependency micronaut to v4.3.8 (#519) (renovate[bot], 2024-04-11)
- `61862d3ac130` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.4.0 (#501) (renovate[bot], 2024-04-01)
- `f5049bea8663` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.8.2 (#506) (renovate[bot], 2024-04-01)
- `c50d29898eea` fix(deps): update dependency io.lettuce:lettuce-core to v6.3.2.release (#505) (renovate[bot], 2024-04-01)
- `9d9a2a6f37c1` fix(deps): update dependency micronaut to v4.3.7 (#503) (renovate[bot], 2024-04-01)
- `9c72ccd59b7b` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.3.5 (#509) (renovate[bot], 2024-04-01)

### Security

- `09ee7839cf09` Propagate redis authentication into configured URIs (#762) (Graeme Rocher, 2026-04-28)

### Dependency Updates

- `a251283b8e7e` chore: Bump version to 7.0.1-SNAPSHOT (micronaut-build, 2026-05-14)
- `6c17909bd0ff` chore: Bump version to 7.0.0-SNAPSHOT (micronaut-build, 2026-05-07)
- `a1cf6a5c0545` Update dependency io.micronaut:micronaut-core-bom to v5.0.0-M26 (#771) (renovate[bot], 2026-05-01)
- `97d4ce809abe` Update Micronaut dependencies (#767) (renovate[bot], 2026-04-29)
- `81d7232e8678` chore: Bump version to 7.0.0-SNAPSHOT (micronaut-build, 2026-04-24)
- `e941f339e785` Update Micronaut dependencies (#759) (renovate[bot], 2026-04-24)
- `54ed0f2a7d6a` chore(deps): update gradle/actions action to v6 (#736) (renovate[bot], 2026-04-17)
- `334d9c3d0ad5` chore(deps): update gradle to v9.4.1 (renovate[bot], 2026-03-19)
- `f0825c01bbc7` chore(deps): update softprops/action-gh-release action to v2.6.2 (renovate[bot], 2026-04-12)
- `f0e75d18e092` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#724) (renovate[bot], 2026-04-10)
- `2bf5b8033a8f` chore: Bump version to 7.0.0-SNAPSHOT (micronaut-build, 2026-02-17)
- `fe0f0b2b06ff` chore(deps): update gradle to v9.3.1 (#721) (renovate[bot], 2026-02-16)
- `8865a0485d3e` chore(deps): update graalvm/setup-graalvm action to v1.4.5 (#715) (renovate[bot], 2026-02-16)
- `4fabd454f52c` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m16 (#717) (renovate[bot], 2026-02-16)
- `c60f2435aca3` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m13 (#711) (renovate[bot], 2025-12-31)
- `46a1b4082a56` chore(deps): update actions/cache action to v5 (#713) (renovate[bot], 2025-12-31)
- `b6b7930a216e` chore(deps): update github artifact actions (#714) (renovate[bot], 2025-12-31)
- `3cc3cc24e05d` chore(deps): update actions/checkout action to v6.0.1 (#699) (renovate[bot], 2025-12-10)
- `2304fffdbaae` chore(deps): update gradle to v9.2.1 (#694) (renovate[bot], 2025-12-10)
- `eacc8cfca0bf` chore(deps): update softprops/action-gh-release action to v2.5.0 (#692) (renovate[bot], 2025-12-10)
- `4704100ae1d3` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#688) (renovate[bot], 2025-12-10)
- `946790b0b035` chore(deps): update graalvm/setup-graalvm action to v1.4.4 (#687) (renovate[bot], 2025-12-10)
- `7c676f5dd96d` chore(deps): update mikepenz/action-junit-report action to v6 (#702) (renovate[bot], 2025-12-10)
- `af0b044e817e` chore(deps): update gradle/gradle-build-action action to v3.2.1 (#514) (renovate[bot], 2024-04-11)
- `dd3d0ec83150` chore(deps): update plugin io.micronaut.build.shared.settings to v6.7.0 (#508) (renovate[bot], 2024-04-01)
- `0e9e7145e5b1` chore(deps): update dependency gradle to v8.7 (#510) (renovate[bot], 2024-03-27)
- `f52359552283` chore(deps): update slsa-framework/slsa-github-generator action to v1.10.0 (#511) (renovate[bot], 2024-03-27)

### Internal

- `279cc461109f` chore: trigger CI for PR #735 (Graeme Rocher, 2026-04-16)

### Review Candidates

- `273b73c954e6` micronaut-micrometer = "6.0.0" (Sergio del Amo, 2026-05-19)
- `f4eaa671392e` micronaut-session = "5.0.0" (Sergio del Amo, 2026-05-19)
- `322f9bafb774` [skip ci] Release v7.0.0 (micronaut-build, 2026-05-14)
- `bf334e892c08` Update versions (Sergio del Amo, 2026-05-14)
- `d4210305fdaa` Update common files (#775) (micronaut-build, 2026-05-14)
- `490b2052628c` micronaut-gradle-plugin = "5.0.0-M1" (Sergio del Amo, 2026-05-13)
- `893d6197c16b` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `c78eaa22c353` Update common files (#774) (micronaut-build, 2026-05-09)
- `28fcd1852a2c` [skip ci] Release v7.0.0-RC1 (micronaut-build, 2026-05-07)
- `d02c86de798e` update versions (Sergio del Amo, 2026-05-07)
- `bdac2bd727a9` Update common files (#773) (micronaut-build, 2026-05-07)
- `b228803d37ed` Update common files (#772) (micronaut-build, 2026-05-05)
- `7f50650baa22` Update common files (#770) (micronaut-build, 2026-05-01)
- `0d5d0405c181` Update common files (#769) (micronaut-build, 2026-04-29)
- `588801064915` Modularize Redis Lettuce into granular subprojects (#766) (Graeme Rocher, 2026-04-29)
- `18c7198bdec5` Fix cache bean instantiation when Redis is disabled (#764) (Graeme Rocher, 2026-04-28)
- `d270577e3aba` [skip ci] Release v7.0.0-M2 (micronaut-build, 2026-04-24)
- `2286eba88cac` Reuse existing Redis connection in RedisHealthIndicator (#756) (Graeme Rocher, 2026-04-24)
- `2f3bd463ee6d` Make lettuce histogram configurable via YAML (#743) (Graeme Rocher, 2026-04-23)
- `479c96beaaad` Update common files (#758) (micronaut-build, 2026-04-22)
- `af2c76f5ceed` Update common files (#755) (micronaut-build, 2026-04-21)
- `16d6057de7ae` Provide retry options for Redis cache reads and inserts (#745) (Graeme Rocher, 2026-04-21)
- `55a6ba98a147` Fix cluster codec test coverage (#739) (Graeme Rocher, 2026-04-17)
- `ccf195cd1c9d` Fix missing cluster pubsub bean exposure (#744) (Graeme Rocher, 2026-04-17)
- `597cfb4c6837` Fix session namespace derived Redis keys (#742) (Graeme Rocher, 2026-04-17)
- `33f0b54f2d52` Merge pull request #740 from micronaut-projects/fix-issue-649-redis-timeout (Graeme Rocher, 2026-04-17)
- `1590d7b27faf` micronaut-logging = "2.0.0-M2" (Sergio del Amo, 2026-04-17)
- `c81e2a7ee20e` micronaut = "5.0.0-M22" (Sergio del Amo, 2026-04-17)
- `d0e44a954d70` Update common files (#731) (micronaut-build, 2026-04-17)
- `0dede6cb977d` Update redis-lettuce/src/main/java/io/micronaut/configuration/lettuce/RedisConfigurationWithUriSettings.java (Sergio del Amo, 2026-04-17)
- `f3844b411ece` Update redis-lettuce/src/main/java/io/micronaut/configuration/lettuce/RedisConfigurationWithUriSettings.java (Sergio del Amo, 2026-04-17)
- `08df7f9403f7` Merge pull request #748 from micronaut-projects/fix-issue-194-graal-cache-serializer (Graeme Rocher, 2026-04-16)
- `22e9791249af` Merge pull request #727 from micronaut-projects/renovate/micronaut.cache (Graeme Rocher, 2026-04-16)
- `37ae7f44778e` Merge pull request #728 from micronaut-projects/renovate/managed.lettuce (Graeme Rocher, 2026-04-16)
- `44f909ad3076` Merge pull request #729 from micronaut-projects/renovate/micronaut-4.x (Graeme Rocher, 2026-04-16)
- `4fe50b6f7b94` Merge pull request #732 from micronaut-projects/renovate/gradle-9.x (Graeme Rocher, 2026-04-16)
- `1f1b78508492` Merge pull request #734 from micronaut-projects/renovate/micronaut.test (Graeme Rocher, 2026-04-16)
- `5bdbf9f51ed6` Merge pull request #735 from micronaut-projects/renovate/softprops-action-gh-release-2.x (Graeme Rocher, 2026-04-16)
- `c41a9e6abf82` Move Graal cache test bean to test sources (Graeme Rocher, 2026-04-16)
- `e852660fa650` Increase coverage for native serializer fix (Graeme Rocher, 2026-04-16)
- `490e41364846` Fix Redis cache serializer binding for native images (Graeme Rocher, 2026-04-15)
- `943cd5095b0b` Refine redis URI setting overrides (Graeme Rocher, 2026-04-14)
- `ef8ec0c5daf3` Fix redis.timeout when redis.uri is configured (Graeme Rocher, 2026-04-13)
- `eddecb7d8b3a` [skip ci] Release v7.0.0-M1 (micronaut-build, 2026-02-17)
- `6380738b3725` Update common files (#723) (micronaut-build, 2026-02-17)
- `aa2a5e8ceb62` Build : Update to micronaut 5 (#707) (issam liqali, 2026-02-17)
- `9d5687618ef3` update to milestones (Sergio del Amo, 2026-02-16)
- `586969b1527a` Update common files (#716) (micronaut-build, 2026-02-16)
- `e59fb9c1e174` Update common files (#708) (micronaut-build, 2025-12-31)
- `d0ceaf122f4f` Update common files (#686) (micronaut-build, 2025-12-10)
- `dc081fa2d49f` Replace Micronaut nullability annotations with JSpecify (#704) (Copilot, 2025-12-02)
- `0e4094871483` Update common files (#685) (micronaut-build, 2025-10-20)
- `c8c72013fdeb` Update common files (#683) (micronaut-build, 2025-10-17)
- `c1a933f6ace2` checkstyle: add empty space after if (Sergio del Amo, 2025-10-14)
- `f1e84d63a743` Micronaut Gradle Build Plugin 8.0.0-M4 (Sergio del Amo, 2025-10-14)
- `ec887bb4ac7d` gradle 9.1 (Sergio del Amo, 2025-10-14)
- `7d04dfa3b1f5` Merge branch '6.10.x' into 7.0.x (Sergio del Amo, 2025-10-14)
- `6adb83509623` Merge branch '6.4.x' into 7.0.x (Sergio del Amo, 2024-04-11)
- `16be315d6f8b` Update common files (#507) (micronaut-build, 2024-03-27)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.redis-native-tests.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `A` redis-lettuce-cache/build.gradle
- `A` redis-lettuce-core/build.gradle
- `A` redis-lettuce-pubsub/build.gradle
- `A` redis-lettuce-session/build.gradle
- `M` redis-lettuce/build.gradle
- `M` settings.gradle
- `M` test-suite-graal/build.gradle
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
- `A` buildSrc/src/main/groovy/micronaut-redis.docs-examples-conventions.gradle
- `A` docs-examples/codecs-groovy/build.gradle
- `A` docs-examples/codecs-groovy/src/test/groovy/io/micronaut/configuration/lettuce/docs/ByteArrayCodecFactory.groovy
- `A` docs-examples/codecs-groovy/src/test/groovy/io/micronaut/configuration/lettuce/docs/NamedCodecFactory.groovy
- `A` docs-examples/codecs-groovy/src/test/groovy/io/micronaut/configuration/lettuce/docs/RedisClientCommands.groovy
- `A` docs-examples/codecs-java/build.gradle
- `A` docs-examples/codecs-java/src/test/java/io/micronaut/configuration/lettuce/docs/ByteArrayCodecFactory.java
- `A` docs-examples/codecs-java/src/test/java/io/micronaut/configuration/lettuce/docs/NamedCodecFactory.java
- `A` docs-examples/codecs-java/src/test/java/io/micronaut/configuration/lettuce/docs/RedisClientCommands.java
- `A` docs-examples/codecs-kotlin/build.gradle
- `A` docs-examples/codecs-kotlin/src/test/kotlin/io/micronaut/configuration/lettuce/docs/ByteArrayCodecFactory.kt
- `A` docs-examples/codecs-kotlin/src/test/kotlin/io/micronaut/configuration/lettuce/docs/NamedCodecFactory.kt
- `A` docs-examples/codecs-kotlin/src/test/kotlin/io/micronaut/configuration/lettuce/docs/RedisClientCommands.kt
- `A` docs-examples/pubsub-groovy/build.gradle
- `A` docs-examples/pubsub-groovy/src/test/groovy/io/micronaut/configuration/lettuce/docs/pubsub/BookAuditExceptionHandler.groovy
- `A` docs-examples/pubsub-groovy/src/test/groovy/io/micronaut/configuration/lettuce/docs/pubsub/BookAuditListener.groovy
- `A` docs-examples/pubsub-groovy/src/test/groovy/io/micronaut/configuration/lettuce/docs/pubsub/BookClient.groovy
- `A` docs-examples/pubsub-groovy/src/test/groovy/io/micronaut/configuration/lettuce/docs/pubsub/BookCreated.groovy
- `A` docs-examples/pubsub-groovy/src/test/groovy/io/micronaut/configuration/lettuce/docs/pubsub/BookCreatedListener.groovy
- `A` docs-examples/pubsub-groovy/src/test/groovy/io/micronaut/configuration/lettuce/docs/pubsub/BookPublisher.groovy
- `A` docs-examples/pubsub-groovy/src/test/groovy/io/micronaut/configuration/lettuce/docs/pubsub/PlainTextBookListener.groovy
- `A` docs-examples/pubsub-java/build.gradle
- `A` docs-examples/pubsub-java/src/test/java/io/micronaut/configuration/lettuce/docs/pubsub/BookAuditExceptionHandler.java
- `A` docs-examples/pubsub-java/src/test/java/io/micronaut/configuration/lettuce/docs/pubsub/BookAuditListener.java
- `A` docs-examples/pubsub-java/src/test/java/io/micronaut/configuration/lettuce/docs/pubsub/BookClient.java
- `A` docs-examples/pubsub-java/src/test/java/io/micronaut/configuration/lettuce/docs/pubsub/BookCreated.java
- `A` docs-examples/pubsub-java/src/test/java/io/micronaut/configuration/lettuce/docs/pubsub/BookCreatedListener.java
- `A` docs-examples/pubsub-java/src/test/java/io/micronaut/configuration/lettuce/docs/pubsub/BookPublisher.java
- `A` docs-examples/pubsub-java/src/test/java/io/micronaut/configuration/lettuce/docs/pubsub/PlainTextBookListener.java
- `A` docs-examples/pubsub-kotlin/build.gradle
- `A` docs-examples/pubsub-kotlin/src/test/kotlin/io/micronaut/configuration/lettuce/docs/pubsub/BookAuditExceptionHandler.kt
- `A` docs-examples/pubsub-kotlin/src/test/kotlin/io/micronaut/configuration/lettuce/docs/pubsub/BookAuditListener.kt
- `A` docs-examples/pubsub-kotlin/src/test/kotlin/io/micronaut/configuration/lettuce/docs/pubsub/BookClient.kt
- `A` docs-examples/pubsub-kotlin/src/test/kotlin/io/micronaut/configuration/lettuce/docs/pubsub/BookCreated.kt
- `A` docs-examples/pubsub-kotlin/src/test/kotlin/io/micronaut/configuration/lettuce/docs/pubsub/BookCreatedListener.kt
- `A` docs-examples/pubsub-kotlin/src/test/kotlin/io/micronaut/configuration/lettuce/docs/pubsub/BookPublisher.kt
- `A` docs-examples/pubsub-kotlin/src/test/kotlin/io/micronaut/configuration/lettuce/docs/pubsub/PlainTextBookListener.kt
- `M` src/main/docs/guide/appendix/breaks.adoc
- `M` src/main/docs/guide/cache.adoc
- `M` src/main/docs/guide/config.adoc
- `M` src/main/docs/guide/introduction.adoc
- `A` src/main/docs/guide/pubsub.adoc
- `M` src/main/docs/guide/sessions.adoc
- `M` src/main/docs/guide/setup.adoc
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
- `A` redis-lettuce-cache/src/main/java/io/micronaut/configuration/lettuce/cache/AbstractRedisCache.java
- `R068` redis-lettuce-cache/src/main/java/io/micronaut/configuration/lettuce/cache/AbstractRedisCacheConfiguration.java
- `R100` redis-lettuce-cache/src/main/java/io/micronaut/configuration/lettuce/cache/DefaultRedisCacheConfiguration.java
- `R097` redis-lettuce-cache/src/main/java/io/micronaut/configuration/lettuce/cache/RedisAsyncConnectionPoolFactory.java
- `R076` redis-lettuce-cache/src/main/java/io/micronaut/configuration/lettuce/cache/RedisCache.java
- `R100` redis-lettuce-cache/src/main/java/io/micronaut/configuration/lettuce/cache/RedisCacheConfiguration.java
- `R070` redis-lettuce-cache/src/main/java/io/micronaut/configuration/lettuce/cache/RedisConnectionPoolCache.java
- `R100` redis-lettuce-cache/src/main/java/io/micronaut/configuration/lettuce/cache/expiration/ConstantExpirationAfterWritePolicy.java
- `R100` redis-lettuce-cache/src/main/java/io/micronaut/configuration/lettuce/cache/expiration/ExpirationAfterWritePolicy.java
- `R100` redis-lettuce-cache/src/main/java/io/micronaut/configuration/lettuce/cache/package-info.java
- `R098` redis-lettuce-core/src/main/java/io/micronaut/configuration/lettuce/AbstractRedisClientFactory.java
- `R057` redis-lettuce-core/src/main/java/io/micronaut/configuration/lettuce/AbstractRedisConfiguration.java
- `R097` redis-lettuce-core/src/main/java/io/micronaut/configuration/lettuce/AbstractRedisConnectionPoolConfiguration.java
- `R100` redis-lettuce-core/src/main/java/io/micronaut/configuration/lettuce/ClientResourcesMutator.java
- `R098` redis-lettuce-core/src/main/java/io/micronaut/configuration/lettuce/DefaultRedisClientFactory.java
- `R083` redis-lettuce-core/src/main/java/io/micronaut/configuration/lettuce/DefaultRedisClusterClientFactory.java
- `R100` redis-lettuce-core/src/main/java/io/micronaut/configuration/lettuce/DefaultRedisCodecFactory.java
- `R076` redis-lettuce-core/src/main/java/io/micronaut/configuration/lettuce/DefaultRedisConfiguration.java
- `R090` redis-lettuce-core/src/main/java/io/micronaut/configuration/lettuce/DefaultRedisConnectionPoolConfiguration.java
- `R057` redis-lettuce-core/src/main/java/io/micronaut/configuration/lettuce/MetricsClientResourceMutator.java
- `R099` redis-lettuce-core/src/main/java/io/micronaut/configuration/lettuce/NamedRedisClientFactory.java
- `R072` redis-lettuce-core/src/main/java/io/micronaut/configuration/lettuce/NamedRedisServersConfiguration.java
- `A` redis-lettuce-core/src/main/java/io/micronaut/configuration/lettuce/RedisConfigurationWithUriSettings.java
- `A` redis-lettuce-core/src/main/java/io/micronaut/configuration/lettuce/RedisConnectionPoolFactory.java
- `R074` redis-lettuce-core/src/main/java/io/micronaut/configuration/lettuce/RedisConnectionUtil.java
- `R100` redis-lettuce-core/src/main/java/io/micronaut/configuration/lettuce/RedisSetting.java
- `R100` redis-lettuce-core/src/main/java/io/micronaut/configuration/lettuce/ThreadPoolClientResourceMutator.java
- `A` redis-lettuce-core/src/main/java/io/micronaut/configuration/lettuce/TopLevelRedisClusterConnectionRegistrar.java
- `A` redis-lettuce-core/src/main/java/io/micronaut/configuration/lettuce/TopLevelRedisConnectionRegistrar.java
- `R072` redis-lettuce-core/src/main/java/io/micronaut/configuration/lettuce/health/RedisHealthIndicator.java
- `A` redis-lettuce-core/src/main/java/io/micronaut/configuration/lettuce/health/RedisHealthIndicatorConfiguration.java
- `R100` redis-lettuce-core/src/main/java/io/micronaut/configuration/lettuce/health/package-info.java
- `R100` redis-lettuce-core/src/main/java/io/micronaut/configuration/lettuce/package-info.java
- `R100` redis-lettuce-core/src/main/resources/META-INF/native-image/io.micronaut.redis/redis-lettuce/native-image.properties
- `A` redis-lettuce-pubsub/src/main/java/io/micronaut/configuration/lettuce/pubsub/RedisListenerMessage.java
- `A` redis-lettuce-pubsub/src/main/java/io/micronaut/configuration/lettuce/pubsub/RedisMessage.java
- `A` redis-lettuce-pubsub/src/main/java/io/micronaut/configuration/lettuce/pubsub/RedisMessageBodyHandler.java
- `A` redis-lettuce-pubsub/src/main/java/io/micronaut/configuration/lettuce/pubsub/RedisPubSubConfiguration.java
- `A` redis-lettuce-pubsub/src/main/java/io/micronaut/configuration/lettuce/pubsub/RedisPubSubListenerRegistry.java
- `A` redis-lettuce-pubsub/src/main/java/io/micronaut/configuration/lettuce/pubsub/RedisPubSubPublisher.java
- `A` redis-lettuce-pubsub/src/main/java/io/micronaut/configuration/lettuce/pubsub/annotation/MessageChannel.java
- `A` redis-lettuce-pubsub/src/main/java/io/micronaut/configuration/lettuce/pubsub/annotation/RedisListener.java
- `A` redis-lettuce-pubsub/src/main/java/io/micronaut/configuration/lettuce/pubsub/annotation/RedisPubSubClient.java
- `A` redis-lettuce-pubsub/src/main/java/io/micronaut/configuration/lettuce/pubsub/bind/RedisBinderRegistry.java
- `A` redis-lettuce-pubsub/src/main/java/io/micronaut/configuration/lettuce/pubsub/bind/RedisBodyBinder.java
- `A` redis-lettuce-pubsub/src/main/java/io/micronaut/configuration/lettuce/pubsub/bind/RedisChannelBinder.java
- `A` redis-lettuce-pubsub/src/main/java/io/micronaut/configuration/lettuce/pubsub/bind/RedisMessageBinder.java
- `A` redis-lettuce-pubsub/src/main/java/io/micronaut/configuration/lettuce/pubsub/exception/DefaultRedisListenerExceptionHandler.java
- `A` redis-lettuce-pubsub/src/main/java/io/micronaut/configuration/lettuce/pubsub/exception/RedisListenerException.java
- `A` redis-lettuce-pubsub/src/main/java/io/micronaut/configuration/lettuce/pubsub/exception/RedisListenerExceptionHandler.java
- `A` redis-lettuce-pubsub/src/main/java/io/micronaut/configuration/lettuce/pubsub/intercept/RedisPubSubClientIntroductionAdvice.java
- `A` redis-lettuce-pubsub/src/main/java/io/micronaut/configuration/lettuce/pubsub/processor/RedisListenerMethodProcessor.java
- `R093` redis-lettuce-session/src/main/java/io/micronaut/configuration/lettuce/session/RedisHttpSessionConfiguration.java
- `R100` redis-lettuce-session/src/main/java/io/micronaut/configuration/lettuce/session/RedisSessionStore.java
- `R100` redis-lettuce-session/src/main/java/io/micronaut/configuration/lettuce/session/package-info.java
- `D` redis-lettuce/src/main/java/io/micronaut/configuration/lettuce/cache/AbstractRedisCache.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `A` redis-lettuce-cache/src/test/groovy/io/micronaut/configuration/lettuce/RedisClusterSpec.groovy
- `R100` redis-lettuce-cache/src/test/groovy/io/micronaut/configuration/lettuce/RedisSpec.groovy
- `A` redis-lettuce-cache/src/test/groovy/io/micronaut/configuration/lettuce/cache/AbstractRedisCacheSpec.groovy
- `R100` redis-lettuce-cache/src/test/groovy/io/micronaut/configuration/lettuce/cache/CounterService.java
- `R100` redis-lettuce-cache/src/test/groovy/io/micronaut/configuration/lettuce/cache/ExpirationSpec.groovy
- `A` redis-lettuce-cache/src/test/groovy/io/micronaut/configuration/lettuce/cache/RedisAsyncConnectionPoolFactorySpec.groovy
- `A` redis-lettuce-cache/src/test/groovy/io/micronaut/configuration/lettuce/cache/RedisCacheConfigurationBindingSpec.groovy
- `A` redis-lettuce-cache/src/test/groovy/io/micronaut/configuration/lettuce/cache/RedisCacheNamespaceSpec.groovy
- `A` redis-lettuce-cache/src/test/groovy/io/micronaut/configuration/lettuce/cache/RedisCacheRetrySpec.groovy
- `R072` redis-lettuce-cache/src/test/groovy/io/micronaut/configuration/lettuce/cache/RedisCacheSpec.groovy
- `R100` redis-lettuce-cache/src/test/groovy/io/micronaut/configuration/lettuce/cache/RedisClusterCacheSpec.groovy
- `R100` redis-lettuce-cache/src/test/groovy/io/micronaut/configuration/lettuce/cache/RedisJsonDeserializerCacheSpec.groovy
- `R079` redis-lettuce-cache/src/test/groovy/io/micronaut/configuration/lettuce/cache/RedisPoolCacheSpec.groovy
- `R100` redis-lettuce-cache/src/test/groovy/io/micronaut/configuration/lettuce/cache/SyncCacheSpec.groovy
- `R100` redis-lettuce-cache/src/test/groovy/io/micronaut/configuration/lettuce/cache/TestExpirationPolicy.java
- `R100` redis-lettuce-cache/src/test/groovy/io/micronaut/configuration/lettuce/cache/TimeService.java
- `A` redis-lettuce-cache/src/test/java/io/micronaut/redis/test/RedisClusterContainerUtils.java
- `R090` redis-lettuce-cache/src/test/java/io/micronaut/redis/test/RedisContainerUtils.java
- `R100` redis-lettuce-cache/src/test/resources/logback.xml
- `A` redis-lettuce-core/src/test/groovy/io/micronaut/configuration/lettuce/ByteArrayCodecFactory.groovy
- `R100` redis-lettuce-core/src/test/groovy/io/micronaut/configuration/lettuce/ByteArrayCodecReplacementFactory.groovy
- `A` redis-lettuce-core/src/test/groovy/io/micronaut/configuration/lettuce/DefaultRedisClusterClientFactoryCodecSpec.groovy
- `R074` redis-lettuce-core/src/test/groovy/io/micronaut/configuration/lettuce/DefaultRedisClusterClientFactorySpec.groovy
- `R100` redis-lettuce-core/src/test/groovy/io/micronaut/configuration/lettuce/NamedCodecFactory.groovy
- `A` redis-lettuce-core/src/test/groovy/io/micronaut/configuration/lettuce/NamedRedisClientFactorySpec.groovy
- `R061` redis-lettuce-core/src/test/groovy/io/micronaut/configuration/lettuce/RedisClientFactorySpec.groovy
- `A` redis-lettuce-core/src/test/groovy/io/micronaut/configuration/lettuce/RedisClusterSpec.groovy
- `R069` redis-lettuce-core/src/test/groovy/io/micronaut/configuration/lettuce/RedisCodecFactorySpec.groovy
- `A` redis-lettuce-core/src/test/groovy/io/micronaut/configuration/lettuce/RedisConfigurationSpec.groovy
- `A` redis-lettuce-core/src/test/groovy/io/micronaut/configuration/lettuce/RedisConnectionPoolFactorySpec.groovy
- `R100` redis-lettuce-core/src/test/groovy/io/micronaut/configuration/lettuce/RedisReplicaClientFactorySpec.groovy
- `R100` redis-lettuce-core/src/test/groovy/io/micronaut/configuration/lettuce/RedisReplicaSpec.groovy
- `A` redis-lettuce-core/src/test/groovy/io/micronaut/configuration/lettuce/RedisSpec.groovy
- `A` redis-lettuce-core/src/test/groovy/io/micronaut/configuration/lettuce/TopLevelRedisConnectionRegistrarSpec.groovy
- `A` redis-lettuce-core/src/test/groovy/io/micronaut/configuration/lettuce/health/RedisHealthIndicatorConnectionReuseSpec.groovy
- `A` redis-lettuce-core/src/test/groovy/io/micronaut/configuration/lettuce/health/RedisHealthIndicatorSpec.groovy
- `R098` redis-lettuce-core/src/test/java/io/micronaut/redis/test/RedisClusterContainerUtils.java
- `A` redis-lettuce-core/src/test/java/io/micronaut/redis/test/RedisContainerUtils.java
- `R100` redis-lettuce-core/src/test/java/io/micronaut/redis/test/RedisReplicaContainerUtils.java
- `A` redis-lettuce-core/src/test/resources/logback.xml
- `A` redis-lettuce-pubsub/src/test/groovy/io/micronaut/configuration/lettuce/RedisSpec.groovy
- `A` redis-lettuce-pubsub/src/test/groovy/io/micronaut/configuration/lettuce/pubsub/RedisBinderRegistrySpec.groovy
- `A` redis-lettuce-pubsub/src/test/groovy/io/micronaut/configuration/lettuce/pubsub/RedisMessageBodyHandlerSpec.groovy
- `A` redis-lettuce-pubsub/src/test/groovy/io/micronaut/configuration/lettuce/pubsub/RedisMessageSpec.groovy
- `A` redis-lettuce-pubsub/src/test/groovy/io/micronaut/configuration/lettuce/pubsub/RedisPubSubSpec.groovy
- `A` redis-lettuce-pubsub/src/test/groovy/io/micronaut/configuration/lettuce/pubsub/processor/RedisListenerMethodProcessorSpec.groovy
- `A` redis-lettuce-pubsub/src/test/java/io/micronaut/redis/test/RedisContainerUtils.java
- `A` redis-lettuce-session/src/test/groovy/io/micronaut/configuration/lettuce/RedisSpec.groovy
- `A` redis-lettuce-session/src/test/groovy/io/micronaut/configuration/lettuce/session/RedisHttpSessionConfigurationSpec.groovy
- `R100` redis-lettuce-session/src/test/groovy/io/micronaut/configuration/lettuce/session/RedisSessionSpec.groovy
- `R100` redis-lettuce-session/src/test/groovy/io/micronaut/configuration/lettuce/session/SessionBindingSpec.groovy
- `R100` redis-lettuce-session/src/test/groovy/io/micronaut/configuration/lettuce/session/SessionSpec.groovy
- `A` redis-lettuce-session/src/test/java/io/micronaut/redis/test/RedisContainerUtils.java
- `A` redis-lettuce-session/src/test/resources/logback.xml
- `D` redis-lettuce/src/test/groovy/io/micronaut/configuration/lettuce/RedisClusterSpec.groovy
- `D` redis-lettuce/src/test/groovy/io/micronaut/configuration/lettuce/RedisConfigurationSpec.groovy
- `D` redis-lettuce/src/test/groovy/io/micronaut/configuration/lettuce/health/RedisHealthIndicatorSpec.groovy
- `M` test-suite-graal/src/main/java/example/RedisController.java
- `A` test-suite-graal/src/test/java/example/CachedStringListService.java
- `A` test-suite-graal/src/test/java/example/CachedStringListServiceTest.java
- `M` test-suite-graal/src/test/java/example/RedisTest.java
- `A` test-suite-utils/src/main/java/io/micronaut/redis/testcontainers/Redis.java

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

