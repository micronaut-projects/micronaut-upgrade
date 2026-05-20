
• Generated the comparison in release direction mn4 -> mn5.

  Full report: micronaut-kotlin-mn4-to-mn5-comparison.md:1

  Scope: previous 4.8.x at 8e45ea19bf68, current 5.0.x at af51307cc1d1; both worktrees are clean. Delta: 72 commits, 71 changed files.

  Release Note Draft

  - Breaking: micronaut-ktor now targets Ktor 3.x. The docs call out Ktor’s environment/server bootstrap redesign: ApplicationEngineEnvironmentBuilder -> ApplicationEnvironmentBuilder, new ServerConfig, and embeddedServer()
    returning EmbeddedServer.
  - Breaking/Compatibility: Ktor Jetty and Tomcat dependencies moved to Jakarta artifacts: ktor-server-jetty -> ktor-server-jetty-jakarta, ktor-server-tomcat -> ktor-server-tomcat-jakarta.
  - Breaking/Compatibility: kotlin-extension-functions no longer brings Jackson Kotlin/databind dependencies transitively. Consumers relying on those transitives should add explicit dependencies or use micronaut-kotlin-runtime.
  - Compatibility: Kotlin extension APIs were tightened with non-null generic bounds, and some property maps changed from Map<String, Any?> to Map<String, Any>.
  - Compatibility: Kotlin runtime Jackson integration now uses Jackson 3 tools.jackson.* packages.
  - Fix/Internal: HOCON property loading and Ktor environment config were updated for Micronaut 5 and Ktor 3 APIs, with new test coverage.

  Dependency/Tooling Changes

  - Project version 4.8.0-SNAPSHOT -> 5.0.0-SNAPSHOT
  - Micronaut Core 4.10.4 -> 5.0.0-RC2
  - Micronaut Platform 4.9.4 -> 5.0.0-M3
  - Ktor 2.3.13 -> 3.4.3
  - Dokka 1.9.20 -> 2.2.0
  - Micronaut Gradle plugin 4.5.5 -> 5.0.0-M1
  - Micronaut Reactor 3.9.0 -> 4.0.0-RC1
  - Micronaut Serde 2.15.5 -> 3.0.0-RC1
  - Typesafe Config 1.4.5 -> 1.4.7
  - Gradle wrapper 8.14.3 -> 9.5.0
  - Local Kotlin stdlib/reflect pins 1.9.25 -> not present because versions are no longer locally cataloged.

  I did not run tests; this was a comparison/reporting pass only.

# Release Note Comparison

Generated: 2026-05-06 16:14 UTC
Comparison: `mn4` -> `mn5`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-kotlin` | `4.8.x` | `8e45ea19bf68` | `git@github.com:micronaut-projects/micronaut-kotlin.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-kotlin` | `5.0.x` | `af51307cc1d1` | `git@github.com:micronaut-projects/micronaut-kotlin.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-kotlin`
- Commit candidates found: 72
- File changes listed: 71
- Version values listed: 31
- File status counts: A=18, M=53

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `4.8.0-SNAPSHOT` | `5.0.0-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.boms-ktor` | `io.ktor:ktor-bom:2.3.13` | `io.ktor:ktor-bom:3.4.3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.gradle-micronaut` | `io.micronaut.gradle:micronaut-gradle-plugin:4.5.5` | `io.micronaut.gradle:micronaut-gradle-plugin:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.kotlin-reflect` | `org.jetbrains.kotlin:kotlin-reflect:1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.kotlin-stdlib-jdk8` | `org.jetbrains.kotlin:kotlin-stdlib-jdk8:1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.ktor-serialization-jackson` | `io.ktor:ktor-serialization-jackson:2.3.13` | `io.ktor:ktor-serialization-jackson:3.4.3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.ktor-server-auth` | `io.ktor:ktor-server-auth:2.3.13` | `io.ktor:ktor-server-auth:3.4.3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.ktor-server-content-negotiation` | `io.ktor:ktor-server-content-negotiation:2.3.13` | `io.ktor:ktor-server-content-negotiation:3.4.3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.ktor-server-jetty` | `io.ktor:ktor-server-jetty:2.3.13` | `io.ktor:ktor-server-jetty-jakarta:3.4.3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.ktor-server-netty` | `io.ktor:ktor-server-netty:2.3.13` | `io.ktor:ktor-server-netty:3.4.3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.ktor-server-tomcat` | `io.ktor:ktor-server-tomcat:2.3.13` | `io.ktor:ktor-server-tomcat-jakarta:3.4.3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-reactor` | `io.micronaut.reactor:micronaut-reactor-bom:3.9.0` | `io.micronaut.reactor:micronaut-reactor-bom:4.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.15.5` | `io.micronaut.serde:micronaut-serde-bom:3.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.mockito-kotlin` | `com.nhaarman.mockitokotlin2:mockito-kotlin:2.2.0` | `com.nhaarman.mockitokotlin2:mockito-kotlin:2.2.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.typesafe-config` | `com.typesafe:config:1.4.5` | `com.typesafe:config:1.4.7` | `changed` |
| `gradle/libs.versions.toml` | `versions.dokka` | `1.9.20` | `2.2.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.kotlin` | `1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.managed-ktor` | `2.3.13` | `3.4.3` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.4` | `5.0.0-RC2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.5.5` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-platform` | `4.9.4` | `5.0.0-M3` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-reactor` | `3.9.0` | `4.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.15.5` | `3.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.7.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.mockito-kotlin` | `2.2.0` | `2.2.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.typesafe-config` | `1.4.5` | `1.4.7` | `changed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.0` | `changed` |
| `settings.gradle` | `plugin.io.micronaut.build.shared.settings` | `7.6.4` | `8.0.0-M18` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `036a63ef49b3` Remove Jackson dependencies from extensions module (#760) (Marius Volkhart, 2026-04-29)
- `0013f2b62d77` remove micronaut-docs, micronaut-test and micronaut-logging versions (Sergio del Amo, 2025-11-26)

### Fixes

- `e4c4cbbde944` fix(deps): update micronaut dependencies (#844) (renovate[bot], 2026-04-29)
- `272819fe98e8` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m4 (#837) (renovate[bot], 2026-03-27)
- `311f3b63fad4` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m18 (#831) (renovate[bot], 2026-03-27)
- `df5a9c1aafbd` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m16 (#830) (renovate[bot], 2026-03-08)
- `50c0d77395aa` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m15 (#823) (renovate[bot], 2026-03-06)
- `c97a243de0c3` fix(deps): update kotlin monorepo to v2.3.10 (#821) (renovate[bot], 2026-02-17)
- `2166797b5fa0` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.15 (#811) (renovate[bot], 2026-02-17)
- `5070b9e849dd` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.2 (#820) (renovate[bot], 2026-02-12)
- `e72461ff49b6` fix(deps): update kotlin monorepo to v2.3.0 (#804) (renovate[bot], 2026-01-09)
- `fb2d2b04510a` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.12 (#803) (renovate[bot], 2026-01-09)
- `4459b7eddfe9` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#777) (renovate[bot], 2025-11-26)
- `ab9ed37b4971` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.1 (#779) (renovate[bot], 2025-11-26)
- `984e4fe558d0` fix(deps): update dependency io.micronaut.reactor:micronaut-reactor-bom to v3.9.1 (#784) (renovate[bot], 2025-11-26)
- `e980d5bdba1f` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#787) (renovate[bot], 2025-11-26)
- `c030cec5b07a` fix(deps): update kotlin monorepo to v2.2.21 (#785) (renovate[bot], 2025-11-26)
- `d67fe3c034db` fix(deps): update kotlin monorepo to v2 (#685) (renovate[bot], 2025-01-15)

### Dependency Updates

- `5f5fad57c751` Update dependency org.apache.tomcat:tomcat-catalina to v9.0.117 (#849) (renovate[bot], 2026-05-06)
- `68ddc1a4af7d` Update Micronaut dependencies (#848) (renovate[bot], 2026-05-04)
- `0d7dc7692465` Update dependency org.apache.tomcat:tomcat-juli to v11 (#824) (renovate[bot], 2026-05-04)
- `e478bdd6d238` Update dependency com.typesafe:config to v1.4.7 (#826) (renovate[bot], 2026-05-04)
- `6bc9f430247d` Update dependency org.jetbrains.dokka to v2.2.0 (#839) (renovate[bot], 2026-05-04)
- `b060125561f2` chore(deps): update jetty monorepo (#825) (renovate[bot], 2026-05-04)
- `649de1491163` chore(deps): update gradle to v9.5.0 (#829) (renovate[bot], 2026-04-29)
- `3bfb01270f94` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-02-17)
- `351161fb812b` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#809) (renovate[bot], 2026-02-17)
- `c7e3f35ad361` chore(deps): update gradle to v9.3.1 (#814) (renovate[bot], 2026-02-12)
- `697c75f81050` chore(deps): update gradle to v8.14.4 (#818) (renovate[bot], 2026-02-12)
- `5a226982efde` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m13 (#802) (renovate[bot], 2026-01-09)
- `cfda01cf1bf9` chore(deps): update actions/cache action to v5 (#805) (renovate[bot], 2026-01-09)
- `cc221ca974c3` chore(deps): update github artifact actions (#806) (renovate[bot], 2026-01-09)
- `19728d542fc0` chore(deps): update graalvm/setup-graalvm action to v1.4.5 (#807) (renovate[bot], 2026-01-09)
- `68efb1748443` chore(deps): update graalvm/setup-graalvm action to v1.4.4 (#789) (renovate[bot], 2025-12-10)
- `438132086817` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#793) (renovate[bot], 2025-12-10)
- `8efa55a9c449` chore(deps): update softprops/action-gh-release action to v2.5.0 (#794) (renovate[bot], 2025-12-10)
- `54079f3d3cb5` chore(deps): update actions/checkout action to v6 (#795) (renovate[bot], 2025-12-10)
- `84fc11a2d2b0` chore(deps): update dependency org.apache.tomcat:tomcat-coyote to v9.0.112 (#782) (renovate[bot], 2025-11-26)
- `403bdbb29182` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m9 (#776) (renovate[bot], 2025-11-26)
- `7e6176aeec39` chore(deps): update softprops/action-gh-release action to v2.4.2 (#780) (renovate[bot], 2025-11-26)
- `3697dd79879d` chore(deps): update dependency org.apache.tomcat:tomcat-catalina to v9.0.112 (#781) (renovate[bot], 2025-11-26)
- `02dbced8548b` chore(deps): update dependency org.apache.tomcat.embed:tomcat-embed-core to v9.0.112 (#783) (renovate[bot], 2025-11-26)
- `8100724f2d91` chore(deps): update dependency org.jetbrains.dokka to v2.1.0 (#786) (renovate[bot], 2025-11-26)
- `7b1b520edbae` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#775) (renovate[bot], 2025-11-03)
- `85d4357f7fe7` chore(deps): update dependency org.jetbrains.dokka to v2 (#688) (renovate[bot], 2025-01-15)

### Internal

- `d482dc4b867e` Build: Update to Micronaut 5 (#808) (issam liqali, 2026-02-17)
- `0228f8abc12e` ci: projectVersion=5.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-01-15)

### Review Candidates

- `af51307cc1d1` git: ignore .kotlin (Sergio del Amo, 2026-05-06)
- `03d11a0347a6` micronaut-platform = "5.0.0-M3" (Sergio del Amo, 2026-05-06)
- `60549d74f72a` micronaut = "5.0.0-RC2" (Sergio del Amo, 2026-05-06)
- `569adfcb29b3` Update common files (#851) (micronaut-build, 2026-05-06)
- `73c834ecfcaf` Update common files (#850) (micronaut-build, 2026-05-05)
- `e4f643bc44c0` Migrate Micronaut ktor integration to Ktor 3 (#840) (Issam Liqali, 2026-05-04)
- `b397851d91c6` Update common files (#846) (micronaut-build, 2026-05-04)
- `d8e74d5f409a` micronaut-gradle-plugin = "5.0.0-M1" (Sergio del Amo, 2026-04-29)
- `7700733fe098` micronaut-platform = "5.0.0-M2" (Sergio del Amo, 2026-04-29)
- `daccd3a87cbe` Update common files (#845) (micronaut-build, 2026-04-29)
- `0a91a905ee53` Update common files (#828) (micronaut-build, 2026-04-26)
- `557c7509aa9d` [skip ci] Release v5.0.0-M1 (micronaut-build, 2026-02-17)
- `6bbd9f09776e` micronaut-serde = "3.0.0-M2" (Sergio del Amo, 2026-02-17)
- `8302cb585fc7` micronaut-reactor = "4.0.0-M1" (Sergio del Amo, 2026-02-17)
- `466b51360103` micronaut = "5.0.0-M10" (Sergio del Amo, 2026-02-17)
- `c1f28dfb420d` Update common files (#810) (micronaut-build, 2026-02-17)
- `931b45bd622b` Update common files (#799) (micronaut-build, 2026-01-09)
- `6f61e5ede862` Replace Micronaut nullability annotations with JSpecify annotations (#791) (Copilot, 2025-12-01)
- `198c82f425f6` platform 4.10.2 (Sergio del Amo, 2025-11-26)
- `d38241f77d6f` Update common files (#778) (micronaut-build, 2025-11-26)
- `0527279c9d46` Micronaut 5 compatibility (#774) (issam liqali, 2025-11-03)
- `60f14ab55684` Update common files (#773) (micronaut-build, 2025-11-03)
- `9ddca6410a58` Micronaut Gradle build plugin 8.0.0-M4 (Sergio del Amo, 2025-10-15)
- `07aba80e8926` gradle 9.1 (Sergio del Amo, 2025-10-15)
- `9cec59c2ac88` Merge branch '4.8.x' into 5.0.x (Sergio del Amo, 2025-10-15)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` build.gradle
- `M` buildSrc/build.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.kotlin-base.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.kotlin-module.gradle
- `M` examples/greeting/build.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` kotlin-extension-functions/build.gradle
- `M` kotlin-runtime/build.gradle
- `M` ktor/build.gradle
- `M` ktor/gradle/wrapper/gradle-wrapper.properties
- `M` settings.gradle
- `M` test-suite-graal-databind/build.gradle.kts

### Documentation

- `A` .agents/skills/docs/SKILL.md
- `A` .agents/skills/docs/references/control-panel-patterns.md
- `A` .agents/skills/docs/references/micronaut-docs-providers.md
- `M` .github/workflows/release.yml
- `M` src/main/docs/guide/breaks.adoc
- `M` src/main/docs/guide/ktor/ktorApplication.adoc
- `M` src/main/docs/guide/ktorModules.adoc

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
- `M` kotlin-extension-functions/src/main/kotlin/io/micronaut/kotlin/context/ApplicationContextExtensions.kt
- `M` kotlin-extension-functions/src/main/kotlin/io/micronaut/kotlin/context/BeanContextExtensions.kt
- `M` kotlin-extension-functions/src/main/kotlin/io/micronaut/kotlin/context/BeanDefinitionRegistryExtensions.kt
- `M` kotlin-extension-functions/src/main/kotlin/io/micronaut/kotlin/context/BeanLocatorExtensions.kt
- `M` kotlin-extension-functions/src/main/kotlin/io/micronaut/kotlin/context/QualifierExtensions.kt
- `M` kotlin-extension-functions/src/main/kotlin/io/micronaut/kotlin/inject/QualifiersExtensions.kt
- `M` kotlin-extension-functions/src/main/kotlin/io/micronaut/kotlin/scheduling/TaskSchedulerExtensions.kt
- `M` kotlin-runtime/src/main/kotlin/io/micronaut/context/env/hocon/HoconPropertySourceLoader.kt
- `M` kotlin-runtime/src/main/kotlin/io/micronaut/jackson/kotlin/KotlinModuleFactory.kt
- `M` ktor/src/main/kotlin/io/micronaut/ktor/KtorApplication.kt
- `M` ktor/src/main/kotlin/io/micronaut/ktor/env/MicronautKtorEnvironmentConfig.kt
- `M` ktor/src/main/kotlin/io/micronaut/ktor/factory/MicronautKtorApplicationFactory.kt
- `M` ktor/src/main/kotlin/io/micronaut/ktor/server/AbstractKtorEmbeddedServer.kt
- `M` ktor/src/main/kotlin/io/micronaut/ktor/server/KtorJettyEmbeddedServer.kt
- `M` ktor/src/main/kotlin/io/micronaut/ktor/server/KtorNettyEmbeddedServer.kt
- `M` ktor/src/main/kotlin/io/micronaut/ktor/server/KtorTomcatEmbeddedServer.kt

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` kotlin-extension-functions/src/test/kotlin/io/micronaut/kotlin/runtime/MicronautExtensionsTest.kt
- `M` kotlin-runtime/src/test/kotlin/io/micronaut/context/env/hocon/HoconPropertySourceLoaderTest.kt
- `M` kotlin-runtime/src/test/kotlin/io/micronaut/jackson/kotlin/KotlinModuleFactoryTest.kt
- `M` ktor/src/test/kotlin/io/micronaut/ktor/env/MicronautKtorEnvironmentConfigTest.kt
- `A` ktor/src/test/kotlin/io/micronaut/ktor/factory/KtorMicronautApplicationFactoryTest.kt

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

