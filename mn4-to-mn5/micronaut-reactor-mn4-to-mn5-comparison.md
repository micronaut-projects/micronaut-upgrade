# Release Note Comparison

Generated: 2026-05-06 10:34 UTC
Comparison: `mn4` -> `mn5`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-reactor` | `3.9.x` | `bcba818ae0b6` | `git@github.com:micronaut-projects/micronaut-reactor.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-reactor` | `4.0.x` | `c0e4e067d422` | `git@github.com:micronaut-projects/micronaut-reactor.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-reactor`
- Commit candidates found: 83
- File changes listed: 60
- File status counts: A=17, D=1, M=42

## Release Notes Draft

### Highlights

- Review the categorized commit candidates and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `eef828cc8a75` update breaking changes for rxjava2 (#635) (Issam Liqali, 2026-04-30)
- `ebd0724974bf` remove micronaut-test version defined in mn build (Sergio del Amo, 2025-11-28)
- `cdec1609ec5c` remove micronaut-logging version as it is defined in micronaut build (Sergio del Amo, 2025-11-28)
- `2575de2dc2e3` remove spock version, use version from MN build (Sergio del Amo, 2025-11-28)
- `2d1682e8e760` remove groovy user version from MN build (Sergio del Amo, 2025-11-28)
- `490fd4ad9f68` remove docs (Sergio del Amo, 2025-11-28)

### Fixes

- `251db8bf0967` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.2 (#621) (renovate[bot], 2026-04-14)
- `91a9af604765` fix(deps): update dependency io.projectreactor:reactor-bom to v2025 (#606) (renovate[bot], 2025-12-04)
- `3969f9698a1f` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#590) (renovate[bot], 2025-11-28)
- `47c56a53e54e` fix(deps): update dependency io.reactivex.rxjava3:rxjava to v3.1.12 (#591) (renovate[bot], 2025-11-28)
- `b7ff263b4923` fix(deps): update dependency io.projectreactor:reactor-bom to v2024.0.12 (#595) (renovate[bot], 2025-11-28)
- `102571b675b6` fix(deps): update dependency io.micrometer:context-propagation to v1.2.0 (#596) (renovate[bot], 2025-11-28)
- `88de9637bf3f` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.1 (#597) (renovate[bot], 2025-11-28)
- `4ebeaba00216` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#598) (renovate[bot], 2025-11-28)
- `ae7e3254b795` fix(deps): update dependency io.micronaut.tracing:micronaut-tracing-bom to v7.2.0 (#599) (renovate[bot], 2025-11-28)
- `bab0a3ab5412` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.12.0 (#600) (renovate[bot], 2025-11-28)
- `82ad14ffa621` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.6 (#584) (renovate[bot], 2025-10-17)

### Dependency Updates

- `eac7939e4e8e` Update Micronaut dependencies (#638) (renovate[bot], 2026-05-06)
- `d413b598cab2` chore: Bump version to 4.0.0-SNAPSHOT (micronaut-build, 2026-05-04)
- `f59bc72cef98` Update Micronaut dependencies (#631) (renovate[bot], 2026-05-01)
- `69e71d3c5bc9` java version 25 (Sergio del Amo, 2026-04-16)
- `0b94d7ec1d6f` chore: Bump version to 4.0.0-SNAPSHOT (micronaut-build, 2026-04-14)
- `81518bd1db40` Update dependency io.projectreactor:reactor-bom to v2025.0.5 (#614) (renovate[bot], 2026-04-14)
- `647c60ceecca` Update dependency io.micrometer:context-propagation to v1.2.1 (#622) (renovate[bot], 2026-04-14)
- `555d8b81d3f0` Update dependency io.micronaut:micronaut-core-bom to v5.0.0-M22 (#612) (renovate[bot], 2026-04-14)
- `3b4f3ec3bc89` Update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-M6 (#619) (renovate[bot], 2026-04-14)
- `aca7892959ba` chore(deps): update gradle to v9.4.1 (#620) (renovate[bot], 2026-04-14)
- `a1c345a11bea` chore(deps): update gradle/actions action to v6 (#625) (renovate[bot], 2026-04-14)
- `b72152744216` chore: Bump version to 4.0.0-SNAPSHOT (micronaut-build, 2025-12-04)
- `c9d42c4e9c6b` chore(deps): update softprops/action-gh-release action to v2.5.0 (#609) (renovate[bot], 2025-12-04)
- `7be4858e0790` chore(deps): update graalvm/setup-graalvm action to v1.4.4 (#610) (renovate[bot], 2025-12-04)
- `abb22b38ad3b` chore(deps): update github artifact actions (#602) (renovate[bot], 2025-11-28)
- `29b1986e451d` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#589) (renovate[bot], 2025-11-28)
- `23b1e10c451d` chore(deps): update gradle to v9.2.1 (#593) (renovate[bot], 2025-11-28)
- `4e207112f895` chore(deps): update softprops/action-gh-release action to v2.4.2 (#594) (renovate[bot], 2025-11-28)
- `5f6830d51ab6` chore(deps): update actions/checkout action to v6 (#601) (renovate[bot], 2025-11-28)
- `417c7e38f251` chore(deps): update graalvm/setup-graalvm action to v1.4.3 (#603) (renovate[bot], 2025-11-28)
- `4c16044abcbb` chore(deps): update mikepenz/action-junit-report action to v6 (#604) (renovate[bot], 2025-11-28)
- `703e7164c77d` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#586) (renovate[bot], 2025-10-27)
- `0afa99bc7897` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m5 (#587) (renovate[bot], 2025-10-27)

### Documentation

- `88cf8cebee1f` Docs: update micronaut-docs to 3.0.0 (#583) (issam liqali, 2025-10-16)

### Internal

- `0160e1f2bb80` ci: projectVersion=4.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-10-10)

### Review Candidates

- `c0e4e067d422` Update common files (#640) (micronaut-build, 2026-05-06)
- `6813e611bd9f` Update Gradle to v9.5.0 (#639) (renovate[bot], 2026-05-06)
- `55edac3b5c08` Update common files (#637) (micronaut-build, 2026-05-05)
- `0b1e84539399` micronaut = "5.0.0-RC1" (Sergio del Amo, 2026-05-04)
- `90f5a9126b00` gradle 9.5 (Sergio del Amo, 2026-05-04)
- `6bf507aed1ab` [skip ci] Release v4.0.0-RC1 (micronaut-build, 2026-05-04)
- `c5319efe1578` Update common files (#636) (micronaut-build, 2026-05-04)
- `6db421704360` Update Gradle to v9.5.0 (#632) (renovate[bot], 2026-05-01)
- `d5458bf4d0bc` Update common files (#634) (micronaut-build, 2026-05-01)
- `c5accd83ce7c` Update common files (#633) (micronaut-build, 2026-04-29)
- `28ac491d8cb2` rxjava3 (#630) (Issam Liqali, 2026-04-29)
- `b3d1f48ffc20` Update common files (#627) (micronaut-build, 2026-04-26)
- `0534fe191f91` [skip ci] Release v4.0.0-M2 (micronaut-build, 2026-04-14)
- `03a53393dc96` don't use try with resources and PropagatedContext (#626) (Sergio del Amo, 2026-04-14)
- `d1178fc0b00f` micronaut-validation = "5.0.0-M1" (Sergio del Amo, 2026-04-14)
- `8a6c2091b8b8` micronaut-tracing = "8.0.0-M1" (Sergio del Amo, 2026-04-14)
- `8fd78af2ab58` Update plugin io.micronaut.build.shared.settings to v8.0.0-M17 (#613) (renovate[bot], 2026-04-14)
- `7d18cc2a0480` Update common files (#623) (micronaut-build, 2026-04-14)
- `45d72185cade` Update softprops/action-gh-release action to v2.6.2 (#624) (renovate[bot], 2026-04-14)
- `731cee49b348` Update common files (#617) (micronaut-build, 2026-03-12)
- `1daef084d378` [skip ci] Release v4.0.0-M1 (micronaut-build, 2025-12-04)
- `c78fe67f6d7a` serde 3.0.0-M1 (Sergio del Amo, 2025-12-04)
- `f5cc510df145` micronaut-platform = "4.10.3" (Sergio del Amo, 2025-12-04)
- `20670566a468` micronaut = "5.0.0-M2" (Sergio del Amo, 2025-12-04)
- `ef64de38e64a` Merge branch '4.0.x' into update-reactor-to-m1 (Sergio del Amo, 2025-12-04)
- `0ec3ca98f58c` [WIP] Replace Micronaut nullability annotations with JSpecify annotations (#608) (Copilot, 2025-12-02)
- `fbc1e274444b` use JSpecify annotations (Sergio del Amo, 2025-11-28)
- `ea15b926a78f` update micronaut to 5.0.0-M1 (Sergio del Amo, 2025-11-28)
- `335ba02a8609` Update common files (#592) (micronaut-build, 2025-11-28)
- `7d2024f2eef3` Micronaut Build Plugin 8.0.0-M6 (Sergio del Amo, 2025-10-27)
- `d00a3be2be1a` micronaut-platform = "4.10.0" (Sergio del Amo, 2025-10-27)
- `cb2ff788b707` micronaut-test = "4.10.2" (Sergio del Amo, 2025-10-27)
- `82bb582c0d6f` micronaut = "4.10.7" (Sergio del Amo, 2025-10-27)
- `20e7114be3bf` source target compatiblity 21 (Sergio del Amo, 2025-10-27)
- `d5a46dee195f` Merge branch '3.9.x' into 4.0.x (Sergio del Amo, 2025-10-27)
- `0365ce6e11f7` Update common files (#585) (micronaut-build, 2025-10-27)
- `82db994f9fe3` platform suite (Sergio del Amo, 2025-10-16)
- `e0de15d6c83b` Merge branch '3.9.x' into 4.0.x (Sergio del Amo, 2025-10-16)
- `d4e06b883483` Update common files (#582) (micronaut-build, 2025-10-16)
- `a2227bb1d5db` micronaut build plugin 8.0.0-M4 (Sergio del Amo, 2025-10-10)
- `2b7d28fcd3fe` gradle 9.1 (Sergio del Amo, 2025-10-10)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.reactor-test-suite.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` reactor-http-client/build.gradle
- `M` reactor-http-client/src/test/groovy/io/micronaut/reactor/http/client/ReactiveTypeConversionSpec.groovy
- `M` reactor/build.gradle
- `M` settings.gradle

### Documentation

- `A` .agents/skills/docs/SKILL.md
- `A` .agents/skills/docs/references/control-panel-patterns.md
- `A` .agents/skills/docs/references/micronaut-docs-providers.md
- `M` .github/workflows/release.yml
- `M` src/main/docs/guide/breaks.adoc

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
- `M` reactor-http-client/src/main/java/io/micronaut/reactor/http/client/BridgedReactorHttpClient.java
- `M` reactor-http-client/src/main/java/io/micronaut/reactor/http/client/BridgedReactorStreamingHttpClient.java
- `M` reactor-http-client/src/main/java/io/micronaut/reactor/http/client/ReactorHttpClient.java
- `M` reactor-http-client/src/main/java/io/micronaut/reactor/http/client/ReactorHttpClientFactory.java
- `M` reactor-http-client/src/main/java/io/micronaut/reactor/http/client/ReactorSseClient.java
- `M` reactor-http-client/src/main/java/io/micronaut/reactor/http/client/ReactorStreamingHttpClient.java
- `M` reactor-http-client/src/main/java/io/micronaut/reactor/http/client/proxy/BridgedReactorProxyHttpClient.java
- `M` reactor-http-client/src/main/java/io/micronaut/reactor/http/client/proxy/ReactorProxyHttpClient.java
- `M` reactor-http-client/src/main/java/io/micronaut/reactor/http/client/proxy/ReactorProxyHttpClientFactory.java
- `M` reactor-http-client/src/main/java/io/micronaut/reactor/http/client/sse/BridgedReactorSseClient.java
- `M` reactor-http-client/src/main/java/io/micronaut/reactor/http/client/sse/ReactorSseClientFactory.java
- `M` reactor-http-client/src/main/java/io/micronaut/reactor/http/client/websocket/ReactorWebSocketClient.java
- `M` reactor-http-client/src/main/java/io/micronaut/reactor/http/client/websocket/ReactorWebSocketClientFactory.java
- `M` reactor/src/main/java/io/micronaut/reactor/config/ReactorConfiguration.java
- `D` reactor/src/main/java/io/micronaut/reactor/convert/ReactorToRxJava2ConverterRegistrar.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` reactor-http-client/src/test/groovy/io/micronaut/reactor/http/client/StreamSpec.groovy
- `M` tests/micrometer-propagation/src/test/groovy/io/micronaut/context/propagation/MyTracingInterceptor.java
- `M` tests/simple-propagation/src/test/groovy/io/micronaut/context/propagation/MyTracingInterceptor.java

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

