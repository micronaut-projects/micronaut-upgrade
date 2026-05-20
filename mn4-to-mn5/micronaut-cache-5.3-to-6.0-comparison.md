 Compared micronaut-cache as mn4 → mn5.

  Scope

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-cache, branch 5.3.x, SHA 9551c48
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-cache, branch 6.0.x, SHA e404758
  - Report: /private/tmp/micronaut-cache-5.3-to-6.0-comparison.md

  Key Findings

  - Major baseline move: project 5.3.1-SNAPSHOT → 6.0.1-SNAPSHOT, Micronaut 4.9.4 → 5.0.0, Gradle wrapper
    8.14.2 → 9.5.1, plus .sdkmanrc pinned to java=25.0.1-graal.
  - Managed cache dependencies were upgraded: Caffeine 3.2.1 → 3.2.4, Ehcache 3.10.8 → 3.12.0, Hazelcast
    5.3.7 → 5.6.0, Infinispan 15.2.4.Final → 16.1.4. JCache stayed on javax.cache:cache-api:1.1.1.
  - Public/cache integration APIs moved nullability annotations from io.micronaut.core.annotation to
    org.jspecify.annotations across cache core, Caffeine, Hazelcast, Infinispan, Ehcache, JCache, and no-op
    modules.
  - Companion Micronaut BOMs were moved to the 5/6 line: Micrometer 5.11.0 → 6.0.0, Serde 2.15.4 → 3.0.0,
    Test Resources 2.8.0 → 4.0.0, Validation 4.9.0 → 5.0.0.
  - Build/test infrastructure was modernized: new shared cache test-suite Gradle plugins, Kotlin test suites
    using Micronaut build Kotlin plugins, cache-tck migrated to Kotlin DSL, and native-image test metadata
    added for the Caffeine native suite.
  - CI/release hardening added OSV vulnerability audit scripts/workflow and release audit enforcement; old
    Sonatype scan plugin wiring was removed.
  - Docs now include a Control Panel page for micronaut-control-panel-cache.

  Diff size: 104 files changed, 4270 insertions(+), 288 deletions(-).

  I did not run tests; this was a folder comparison only.

# Release Note Comparison

Generated: 2026-05-19 11:12 UTC
Comparison: `5.3.x` -> `6.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-cache` | `5.3.x` | `9551c48f88f5` | `git@github.com:micronaut-projects/micronaut-cache.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-cache` | `6.0.x` | `e404758ce3d1` | `git@github.com:micronaut-projects/micronaut-cache.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-cache`
- Commit candidates found: 105
- File changes listed: 104
- Version values listed: 41
- File status counts: A=35, D=1, M=68

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `5.3.1-SNAPSHOT` | `6.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.cache-api` | `javax.cache:cache-api:1.1.1` | `javax.cache:cache-api:1.1.1` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.cache-ri-impl` | `org.jsr107.ri:cache-ri-impl:1.1.1` | `org.jsr107.ri:cache-ri-impl:1.1.1` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.graal-svm` | `org.graalvm.nativeimage:svm:23.1.7` | `org.graalvm.nativeimage:svm:25.0.3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.gradle-graal` | `org.graalvm.buildtools.native:org.graalvm.buildtools.native.gradle.plugin:0.10.6` | `org.graalvm.buildtools.native:org.graalvm.buildtools.native.gradle.plugin:1.1.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.gradle-kotlin` | `org.jetbrains.kotlin:kotlin-gradle-plugin:1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.managed-caffeine` | `com.github.ben-manes.caffeine:caffeine:3.2.1` | `com.github.ben-manes.caffeine:caffeine:3.2.4` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-ehcache` | `org.ehcache:ehcache:3.10.8` | `org.ehcache:ehcache:3.12.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-ehcache-clustered` | `org.ehcache:ehcache-clustered:3.10.8` | `org.ehcache:ehcache-clustered:3.12.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-hazelcast` | `com.hazelcast:hazelcast:5.3.7` | `com.hazelcast:hazelcast:5.6.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-infinispan-client-hotrod` | `org.infinispan:infinispan-client-hotrod:15.2.4.Final` | `org.infinispan:infinispan-client-hotrod:16.1.4` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-infinispan-core` | `org.infinispan:infinispan-core:15.2.4.Final` | `org.infinispan:infinispan-core:16.1.4` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-jcache` | `javax.cache:cache-api:1.1.1` | `javax.cache:cache-api:1.1.1` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.micronaut-micrometer` | `io.micronaut.micrometer:micronaut-micrometer-bom:5.11.0` | `io.micronaut.micrometer:micronaut-micrometer-bom:6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.15.4` | `io.micronaut.serde:micronaut-serde-bom:3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-resources` | `io.micronaut.testresources:micronaut-test-resources-bom:2.8.0` | `io.micronaut.testresources:micronaut-test-resources-bom:4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-validation` | `io.micronaut.validation:micronaut-validation-bom:4.9.0` | `io.micronaut.validation:micronaut-validation-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.sonatype-scan` | `org.sonatype.gradle.plugins:scan-gradle-plugin:3.1.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.spock-core` | `org.spockframework:spock-core:2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.cache-ri-impl` | `1.1.1` | `1.1.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.graal-plugin` | `0.10.6` | `1.1.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.graal-svm` | `23.1.7` | `25.0.3` | `changed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.12` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.kotlin` | `1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.managed-caffeine` | `3.2.1` | `3.2.4` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-ehcache` | `3.10.8` | `3.12.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-hazelcast` | `5.3.7` | `5.6.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-infinispan` | `15.2.4.Final` | `16.1.4` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-jcache` | `1.1.1` | `1.1.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.9.4` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `2.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-micrometer` | `5.11.0` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.15.4` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.7.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test-resources` | `2.8.0` | `4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.9.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.sonatype-scan` | `3.1.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.2` | `9.5.1` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `6c73833de711` Build: remove sonatype plugin (#934) (issam liqali, 2025-10-13)

### Fixes

- `2ff13238b62d` fix(deps): update managed.infinispan to v16.1.3 (#984) (renovate[bot], 2026-04-17)
- `c0581c701fc4` fix(deps): update dependency org.graalvm.buildtools.native:org.graalvm.buildtools.native.gradle.plugin to v0.11.5 (#986) (renovate[bot], 2026-04-17)
- `fb485e4403dc` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m22 (#1001) (renovate[bot], 2026-04-17)
- `af2b4bf4b844` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m20 (#999) (renovate[bot], 2026-04-06)
- `427c9421ca60` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m17 (#981) (renovate[bot], 2026-03-16)
- `9a23ed1f18e4` fix(deps): update dependency org.graalvm.nativeimage:svm to v23.1.10 (#978) (renovate[bot], 2026-01-30)
- `7e65e767a7a3` fix(deps): update dependency io.micronaut.micrometer:micronaut-micrometer-bom to v5.13.2 (#965) (renovate[bot], 2026-01-30)
- `ce142beb976d` fix(deps): update dependency org.jetbrains.kotlin:kotlin-gradle-plugin to v2.3.0 (#971) (renovate[bot], 2026-01-30)
- `57de250aa215` fix(deps): update dependency org.spockframework:spock-core to v2.4-groovy-5.0 (#968) (renovate[bot], 2026-01-30)
- `bedfc38d0885` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m9 (#967) (renovate[bot], 2026-01-30)
- `2166010f32e4` fix(deps): update managed.infinispan to v16.0.5 (#970) (renovate[bot], 2026-01-29)
- `55081bf159c5` fix(deps): update dependency com.hazelcast:hazelcast to v5.6.0 (#954) (renovate[bot], 2025-12-03)
- `b907c4f80112` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.12.0 (#956) (renovate[bot], 2025-12-03)
- `13f7276c66ad` fix(deps): update dependency io.micronaut.micrometer:micronaut-micrometer-bom to v5.13.1 (#947) (renovate[bot], 2025-12-03)
- `6691d83c5a3d` fix(deps): update managed.infinispan to v16 (#960) (renovate[bot], 2025-12-03)
- `d5e72fd1c0a6` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#955) (renovate[bot], 2025-12-03)
- `9e73eb64b0a1` fix(deps): update dependency org.jetbrains.kotlin:kotlin-gradle-plugin to v2.2.21 (#952) (renovate[bot], 2025-12-03)
- `d78a1de9cbcb` fix(deps): update dependency org.graalvm.nativeimage:svm to v23.1.9 (#951) (renovate[bot], 2025-12-03)
- `041864265962` fix(deps): update dependency com.github.ben-manes.caffeine:caffeine to v3.2.3 (#945) (renovate[bot], 2025-12-03)
- `daef2152d80b` fix(deps): update dependency org.graalvm.buildtools.native:org.graalvm.buildtools.native.gradle.plugin to v0.11.3 (#949) (renovate[bot], 2025-12-03)
- `d05af746daaf` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.6 (#939) (renovate[bot], 2025-10-17)
- `d40ffeb5bdb3` fix(deps): update managed.ehcache to v3.11.1 (#928) (renovate[bot], 2025-10-10)
- `d95d4728e0e4` fix(deps): update managed.infinispan to v15.2.6.final (#920) (renovate[bot], 2025-10-10)
- `842caa7ce4c1` fix(deps): update dependency org.graalvm.nativeimage:svm to v23.1.8 (#919) (renovate[bot], 2025-10-10)
- `b5425e02192f` fix(deps): update dependency com.github.ben-manes.caffeine:caffeine to v3.2.2 (#918) (renovate[bot], 2025-10-10)
- `92974071de3a` fix(deps): update dependency org.graalvm.buildtools.native:org.graalvm.buildtools.native.gradle.plugin to v0.11.1 (#921) (renovate[bot], 2025-10-10)
- `483fd1c49722` fix(deps): update dependency io.micronaut.micrometer:micronaut-micrometer-bom to v5.13.0 (#911) (renovate[bot], 2025-10-10)
- `7eb0866cdbf2` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.3 (#914) (renovate[bot], 2025-10-10)
- `fe0aa9d7c510` fix(deps): update dependency io.micronaut.testresources:micronaut-test-resources-bom to v2.10.1 (#915) (renovate[bot], 2025-10-10)
- `109b91a79811` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.11.0 (#916) (renovate[bot], 2025-10-10)
- `bfe7c0e58206` fix(deps): update dependency org.sonatype.gradle.plugins:scan-gradle-plugin to v3.1.4 (#923) (renovate[bot], 2025-10-10)

### Dependency Updates

- `c4a2b170c414` chore: Bump version to 6.0.1-SNAPSHOT (micronaut-build, 2026-05-14)
- `3b99bca1e297` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2026-05-08)
- `e264dbae13cf` Update dependency org.graalvm.buildtools.native:org.graalvm.buildtools.native.gradle.plugin to v1 (#1015) (renovate[bot], 2026-05-08)
- `0e65346deccb` Update dependency org.graalvm.nativeimage:svm to v25 (#1016) (renovate[bot], 2026-05-07)
- `e8eb315d18b8` Update dependency com.github.ben-manes.caffeine:caffeine to v3.2.4 (#1012) (renovate[bot], 2026-05-07)
- `9c0b1803bc86` Update Micronaut dependencies (#1013) (renovate[bot], 2026-05-07)
- `8214d34b9efc` Update dependency io.micronaut:micronaut-core-bom to v5.0.0-M26 (#1004) (renovate[bot], 2026-05-01)
- `f9b3300f09e2` Update dependencies for Renovate batch (#1008) (Sergio del Amo, 2026-04-29)
- `20de7a04b7f9` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2026-04-17)
- `3cde208ab3ae` chore(deps): update gradle to v9.4.1 (#987) (renovate[bot], 2026-04-17)
- `5cef6ef7f52a` chore(deps): update softprops/action-gh-release action to v2.6.2 (#990) (renovate[bot], 2026-04-17)
- `bfc7763800ab` chore(deps): update gradle/actions action to v6 (#995) (renovate[bot], 2026-04-17)
- `613ba7a130ec` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#979) (renovate[bot], 2026-03-16)
- `d0e18f4fca78` use spock version from micronaut-test (#988) (Issam Liqali, 2026-03-09)
- `4d26e1ec4eff` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2026-01-30)
- `46a2c962ec4c` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m14 (#969) (renovate[bot], 2026-01-30)
- `83107fae0891` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2025-12-05)
- `1134df0af0ca` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#942) (renovate[bot], 2025-10-27)
- `59eb3189f86d` chore(deps): update softprops/action-gh-release action to v2.4.1 (#937) (renovate[bot], 2025-10-16)
- `d867f118d491` chore(deps): update actions/download-artifact action to v5 (#924) (renovate[bot], 2025-10-10)
- `8c3505b44e06` chore(deps): update graalvm/setup-graalvm action to v1.4.1 (#913) (renovate[bot], 2025-10-10)
- `10f46fa67bda` chore(deps): update gradle to v8.14.3 (#917) (renovate[bot], 2025-10-10)
- `7aa746cb9381` chore(deps): update actions/checkout action to v5 (#929) (renovate[bot], 2025-10-10)
- `526471662ef3` chore(deps): update actions/setup-java action to v5 (#930) (renovate[bot], 2025-10-10)
- `f13c6f0bc8d6` chore(deps): update softprops/action-gh-release action to v2.4.0 (#932) (renovate[bot], 2025-10-10)

### Documentation

- `0ebcc209ca70` Docs: update micronaut-docs to 3.0.0 (#936) (issam liqali, 2025-10-16)

### Internal

- `d5ba959f0514` ci: projectVersion=6.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-10-10)
- `968c08bebb27` ci: projectVersion=5.4.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-10-10)

### Review Candidates

- `e404758ce3d1` micronaut-test-resources = "4.0.0" (Sergio del Amo, 2026-05-19)
- `6b39b878c124` Update common files (#1021) (micronaut-build, 2026-05-19)
- `6c0de5f76dd2` micronaut-micrometer = "6.0.0" (Sergio del Amo, 2026-05-18)
- `11a46c360129` [skip ci] Release v6.0.0 (micronaut-build, 2026-05-14)
- `d9266f79e2b3` Update versions (Sergio del Amo, 2026-05-14)
- `a15674b602b6` Update common files (#1020) (micronaut-build, 2026-05-14)
- `73d9bc06b636` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `69f39060faf0` Update common files (#1019) (micronaut-build, 2026-05-09)
- `9b7205893ded` [skip ci] Release v6.0.0-RC1 (micronaut-build, 2026-05-08)
- `4bd7a88d4468` Update common files (#1018) (micronaut-build, 2026-05-08)
- `052b1eb8f688` git ignore .kotlin (Sergio del Amo, 2026-05-07)
- `c824b2e22a06` Update Gradle to v9.5.0 (#1005) (renovate[bot], 2026-05-07)
- `d3e8e5a6937e` Update common files (#1017) (micronaut-build, 2026-05-07)
- `a04e72792f2d` Update managed.ehcache to v3.12.0 (#1014) (renovate[bot], 2026-05-07)
- `5d09f00eb839` Update common files (#1011) (micronaut-build, 2026-05-05)
- `167a833f2d6e` Update common files (#1010) (micronaut-build, 2026-05-04)
- `663c7abf1304` Update common files (#1006) (micronaut-build, 2026-05-01)
- `a3a0d7568106` Update managed.infinispan to v16.1.4 (#1009) (renovate[bot], 2026-05-01)
- `cfee364c5a40` Update common files (#1002) (micronaut-build, 2026-04-22)
- `1303d8a30f0d` [skip ci] Release v6.0.0-M3 (micronaut-build, 2026-04-17)
- `1523608b8693` micronaut-validation = "5.0.0-M2" (Sergio del Amo, 2026-04-17)
- `09bca00b936a` use DIGEST-SHA-256 in tests (Sergio del Amo, 2026-04-17)
- `d32d10f2ba05` micronaut-test-resources = "4.0.0-M1" (Sergio del Amo, 2026-04-17)
- `f599df3928f4` micronaut-micrometer = "6.0.1-M1" (Sergio del Amo, 2026-04-17)
- `7383ed39e576` Update common files (#991) (micronaut-build, 2026-04-17)
- `9036af6ffee4` use micronaut build kotlin plugin (#992) (Issam Liqali, 2026-04-15)
- `2a4e987100a5` Update common files (#980) (micronaut-build, 2026-03-16)
- `8e08652243cb` [skip ci] Release v6.0.0-M2 (micronaut-build, 2026-01-30)
- `6ab130015316` [cache] Update common files for branch 6.0.x (#966) (micronaut-build, 2026-01-30)
- `caffed14d25e` Link to Control Panel docs (#964) (Álvaro Sánchez-Mariscal, 2025-12-05)
- `32d07a56bf70` [skip ci] Release v6.0.0-M1 (micronaut-build, 2025-12-05)
- `745b7491bab7` git: ignore .kotlin (Sergio del Amo, 2025-12-05)
- `f012515ccae4` jspecify nullability annotations (Sergio del Amo, 2025-12-05)
- `2409b5ca637f` force spock version (Sergio del Amo, 2025-12-05)
- `daf5dee5b9f7` micronaut serde 3.0.0-M1 (Sergio del Amo, 2025-12-05)
- `78a9c0f38055` micronaut core 5.0.0-M2 (Sergio del Amo, 2025-12-05)
- `afd57fda94f3` [cache] Update common files for branch 6.0.x (#948) (micronaut-build, 2025-12-03)
- `238054bd22a1` Replace Micronaut nullability annotations with JSpecify annotations (#963) (Copilot, 2025-12-01)
- `1f3bd87542b6` Update common files (#941) (micronaut-build, 2025-10-27)
- `f44d8b30b66e` Micronaut 5 compatibility and release prep (#938) (issam liqali, 2025-10-17)
- `bc765e4989bb` Update common files (#940) (micronaut-build, 2025-10-17)
- `e66726318080` Update common files (#935) (micronaut-build, 2025-10-16)
- `5b6383dd8b23` Micronatu gradle build plugin 8.0.0-M4 (Sergio del Amo, 2025-10-10)
- `c14b5ddcfc36` gradle 9.1 (Sergio del Amo, 2025-10-10)
- `99cabb62c9d1` Update common files (#908) (micronaut-build, 2025-10-10)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` buildSrc/build.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.cache-base.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.cache-module.gradle
- `A` buildSrc/src/main/groovy/io.micronaut.build.internal.cache-test-suite-kotlin.gradle
- `A` buildSrc/src/main/groovy/io.micronaut.build.internal.cache-test-suite.gradle
- `M` cache-ehcache/build.gradle
- `D` cache-tck/build.gradle
- `A` cache-tck/build.gradle.kts
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` settings.gradle
- `M` test-suite-caffeine-groovy/build.gradle.kts
- `M` test-suite-caffeine-java/build.gradle.kts
- `M` test-suite-caffeine-kotlin/build.gradle.kts
- `M` test-suite-caffeine-native/build.gradle
- `M` test-suite-hazelcast-groovy/build.gradle.kts
- `M` test-suite-hazelcast-java/build.gradle.kts
- `M` test-suite-hazelcast-kotlin/build.gradle.kts

### Documentation

- `A` .agents/skills/docs/SKILL.md
- `A` .agents/skills/docs/references/control-panel-patterns.md
- `A` .agents/skills/docs/references/micronaut-docs-providers.md
- `A` .agents/skills/guides/SKILL.md
- `A` .agents/skills/guides/references/guide-authoring-conventions.md
- `A` .agents/skills/guides/references/guide-inventory.md
- `A` .agents/skills/guides/references/pdf-export-and-pr.md
- `A` .agents/skills/guides/references/repository-workflow.md
- `A` .clinerules/docs.md
- `A` .github/instructions/docs.instructions.md
- `M` .github/workflows/release.yml
- `A` src/main/docs/guide/control-panel.adoc
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
- `A` .clineignore
- `A` .clinerules/coding.md
- `A` .github/instructions/coding.instructions.md
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
- `M` cache-caffeine/src/main/java/io/micronaut/cache/caffeine/DefaultDynamicCacheManager.java
- `M` cache-caffeine/src/main/java/io/micronaut/cache/caffeine/DefaultSyncCache.java
- `M` cache-core/src/main/java/io/micronaut/cache/AbstractMapBasedSyncCache.java
- `M` cache-core/src/main/java/io/micronaut/cache/CacheInfo.java
- `M` cache-core/src/main/java/io/micronaut/cache/CacheManager.java
- `M` cache-core/src/main/java/io/micronaut/cache/DefaultCacheManager.java
- `M` cache-core/src/main/java/io/micronaut/cache/DynamicCacheManager.java
- `M` cache-core/src/main/java/io/micronaut/cache/SyncCache.java
- `M` cache-core/src/main/java/io/micronaut/cache/interceptor/CacheInterceptor.java
- `M` cache-core/src/main/java/io/micronaut/cache/jcache/JCacheManager.java
- `M` cache-core/src/main/java/io/micronaut/cache/jcache/JCacheSyncCache.java
- `M` cache-ehcache/src/main/java/io/micronaut/cache/ehcache/EhcacheSyncCache.java
- `M` cache-ehcache/src/main/java/io/micronaut/cache/ehcache/configuration/EhcacheClusterResourcePoolConfiguration.java
- `M` cache-ehcache/src/main/java/io/micronaut/cache/ehcache/configuration/EhcacheConfiguration.java
- `M` cache-hazelcast/src/main/java/io/micronaut/cache/hazelcast/HazelcastAsyncCache.java
- `M` cache-hazelcast/src/main/java/io/micronaut/cache/hazelcast/HazelcastCacheManager.java
- `M` cache-hazelcast/src/main/java/io/micronaut/cache/hazelcast/HazelcastClientConfiguration.java
- `M` cache-hazelcast/src/main/java/io/micronaut/cache/hazelcast/HazelcastMemberConfiguration.java
- `M` cache-hazelcast/src/main/java/io/micronaut/cache/hazelcast/HazelcastSyncCache.java
- `M` cache-infinispan/src/main/java/io/micronaut/cache/infinispan/InfinispanAsyncCache.java
- `M` cache-infinispan/src/main/java/io/micronaut/cache/infinispan/InfinispanCacheInfo.java
- `M` cache-infinispan/src/main/java/io/micronaut/cache/infinispan/InfinispanCacheManager.java
- `M` cache-infinispan/src/main/java/io/micronaut/cache/infinispan/InfinispanSyncCache.java
- `M` cache-noop/src/main/java/io/micronaut/cache/noop/NoOpCacheManager.java
- `M` cache-noop/src/main/java/io/micronaut/cache/noop/NoOpSyncCache.java
- `M` config/checkstyle/checkstyle.xml

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` cache-caffeine/src/test/java/io/micronaut/cache/DynamicCache.java
- `M` cache-caffeine/src/test/java/io/micronaut/cache/RemovalListenerImpl.java
- `M` cache-ehcache/src/test/groovy/io/micronaut/cache/ehcache/EhcacheClusteredSpec.groovy
- `M` cache-hazelcast/src/test/groovy/io/micronaut/cache/hazelcast/HazelcastClientConfigurationSpec.groovy
- `M` cache-infinispan/src/test/groovy/io/micronaut/cache/infinispan/InfinispanAsyncCacheSpec.groovy
- `M` cache-infinispan/src/test/groovy/io/micronaut/cache/infinispan/InfinispanCacheInfoSpec.groovy
- `M` cache-infinispan/src/test/groovy/io/micronaut/cache/infinispan/InfinispanSyncCacheSpec.groovy
- `M` test-suite-caffeine-groovy/src/test/groovy/io/micronaut/cache/RemovalListenerImpl.groovy
- `M` test-suite-caffeine-java/src/test/java/io/micronaut/cache/RemovalListenerImpl.java
- `M` test-suite-caffeine-kotlin/src/test/kotlin/io/micronaut/cache/RemovalListenerImpl.kt
- `M` test-suite-caffeine-native/src/test/java/io/micronaut/cache/RemovalListenerImpl.java
- `A` test-suite-caffeine-native/src/test/resources/META-INF/native-image/io.micronaut.cache/test-suite-caffeine-native/native-image.properties
- `M` test-suite-hazelcast-groovy/src/test/groovy/io/micronaut/cache/HazelcastAdditionalSettings.groovy
- `M` test-suite-hazelcast-java/src/test/java/io/micronaut/cache/HazelcastAdditionalSettings.java
- `M` test-suite-hazelcast-java/src/test/java/io/micronaut/cache/HazelcastTest.java

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

