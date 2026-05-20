# Release Note Comparison

Generated: 2026-05-06 10:58 UTC
Comparison: `mn4` -> `mn5`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-rxjava3` | `3.9.x` | `5417071a43b3` | `git@github.com:micronaut-projects/micronaut-rxjava3.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-rxjava3` | `4.0.x` | `f9f1f8e040aa` | `git@github.com:micronaut-projects/micronaut-rxjava3.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-rxjava3`
- Commit candidates found: 48
- File changes listed: 53
- Version values listed: 15
- File status counts: A=17, D=1, M=35

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `3.9.1-SNAPSHOT` | `4.0.0-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-rxjava3` | `io.reactivex.rxjava3:rxjava:3.1.12` | `io.reactivex.rxjava3:rxjava:3.1.12` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.micronaut-rxjava2` | `io.micronaut.rxjava2:micronaut-rxjava2-bom:2.8.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.rxjava3-bridge` | `com.github.akarnokd:rxjava3-bridge:3.0.2` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.managed-rxjava3` | `3.1.12` | `3.1.12` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.4` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-rxjava2` | `2.8.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.9.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.rxjava3-bridge` | `3.0.2` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.0` | `changed` |
| `settings.gradle` | `plugin.io.micronaut.build.shared.settings` | `7.6.4` | `8.0.0-M18` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `39eb47f2276d` remove rxjava2 (#497) (Sergio del Amo, 2026-04-21)
- `b787e556c442` Remove Spock version force configuration (#491) (Issam Liqali, 2026-03-13)

### Fixes

- `dec4f4672d89` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m16 (#484) (renovate[bot], 2026-03-13)
- `7f1253112c6f` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.8 (#469) (renovate[bot], 2025-11-03)
- `a6fa8371f028` fix(deps): update dependency io.micronaut.rxjava2:micronaut-rxjava2-bom to v2.9.0 (#462) (renovate[bot], 2025-10-17)

### Dependency Updates

- `f9f1f8e040aa` Update dependency io.micronaut:micronaut-core-bom to v5.0.0-RC1 (#505) (renovate[bot], 2026-05-06)
- `f23a02cad821` chore(deps): update gradle to v9.5.0 (#502) (renovate[bot], 2026-05-05)
- `c0ba231ddeaf` Update Micronaut dependencies (#501) (renovate[bot], 2026-05-02)
- `22e0c15e7651` chore(deps): update actions/cache digest to 27d5ce7 (#498) (renovate[bot], 2026-04-21)
- `db9ff547d0f4` chore(deps): update gradle to v9.4.1 (#490) (renovate[bot], 2026-04-16)
- `9f5a3cf6552a` Update dependency io.micronaut:micronaut-core-bom to v5.0.0-M22 (#492) (renovate[bot], 2026-04-16)
- `af9d6c6646b0` chore(deps): update gradle/actions action to v6 (#496) (renovate[bot], 2026-04-16)
- `ee2544f7557c` chore(deps): update actions/checkout action to v6 (#478) (renovate[bot], 2025-12-10)
- `b7100e992f10` chore(deps): update github artifact actions (#474) (renovate[bot], 2025-12-10)
- `faa16d58bf16` chore(deps): update mikepenz/action-junit-report action to v6 (#475) (renovate[bot], 2025-12-10)
- `f93afd14dc93` chore(deps): update softprops/action-gh-release action to v2.5.0 (#476) (renovate[bot], 2025-12-10)
- `9652bf719f81` chore(deps): update gradle to v9.2.1 (#477) (renovate[bot], 2025-12-10)
- `ee853e6520b8` chore(deps): update graalvm/setup-graalvm action to v1.4.4 (#480) (renovate[bot], 2025-12-10)
- `aaa7b4fbec99` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#472) (renovate[bot], 2025-12-10)
- `3bee52ccb0bc` chore: Bump version to 4.0.0-SNAPSHOT (micronaut-build, 2025-12-04)
- `83f977f97e78` del micronaut-docs version as it is supplied by MN Build (Sergio del Amo, 2025-12-04)
- `0c8414dc79c7` del groovy version as it is supplied by MN Build (Sergio del Amo, 2025-12-04)
- `41f68b0f674f` del spock version as it is supplied by MN Build (Sergio del Amo, 2025-12-04)
- `c45186f488c3` del micronaut-test version as it is supplied by MN Build (Sergio del Amo, 2025-12-04)
- `88abe33bfc98` chore(deps): update gradle to v9.2.0 (#471) (renovate[bot], 2025-11-03)
- `872b1b5734a0` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m8 (#468) (renovate[bot], 2025-11-03)
- `e7300523432f` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#467) (renovate[bot], 2025-11-03)

### Review Candidates

- `ee9e6a4ecca1` Update common files (#506) (micronaut-build, 2026-05-06)
- `9125bb032eb9` Update common files (#504) (micronaut-build, 2026-05-05)
- `9b31132a71bb` [rxjava3] Update common files for branch 4.0.x (#503) (micronaut-build, 2026-05-01)
- `82fa82695aaf` Update common files (#500) (micronaut-build, 2026-04-26)
- `3f6833031158` Update common files (#499) (micronaut-build, 2026-04-21)
- `47efa0ac42e8` Update softprops/action-gh-release action to v2.6.2 (#493) (renovate[bot], 2026-04-16)
- `b8705d6e6f57` Update common files (#494) (micronaut-build, 2026-04-16)
- `f7f3a407b101` [rxjava3] Update common files for branch 4.0.x (#483) (micronaut-build, 2026-03-13)
- `23acb79c9fdb` Update common files (#473) (micronaut-build, 2025-12-10)
- `6ac556aa9858` [skip ci] Release v4.0.0-M1 (micronaut-build, 2025-12-04)
- `d3aca8b82243` fix spock version (Sergio del Amo, 2025-12-04)
- `bb451ef68be1` set Micronaut core to 5.0.0-M2 (Sergio del Amo, 2025-12-04)
- `9f771259e6e5` [WIP] Replace Micronaut nullability annotations with JSpecify (#482) (Copilot, 2025-12-02)
- `0224954ba494` Merge branch '3.9.x' into 4.0.x (Sergio del Amo, 2025-11-03)
- `439d39c4a0c2` Update common files (#466) (micronaut-build, 2025-11-03)
- `37d4766317b1` Update common files (#465) (micronaut-build, 2025-10-20)
- `864842dee570` update graalvm workflow to use java 21 (#464) (issam liqali, 2025-10-20)
- `9b8d397a613c` Update common files (#463) (micronaut-build, 2025-10-17)
- `14b8cfe1da8f` Micronaut Gradle build plugin 8.0.0-M4 (Sergio del Amo, 2025-10-14)
- `4d5a8e8cb172` gradle 9.1 (Sergio del Amo, 2025-10-14)
- `71693ac60423` projectVersion=4.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-10-14)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` rxjava3/build.gradle
- `M` settings.gradle

### Documentation

- `A` .agents/skills/docs/SKILL.md
- `A` .agents/skills/docs/references/control-panel-patterns.md
- `A` .agents/skills/docs/references/micronaut-docs-providers.md
- `M` .github/workflows/release.yml

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
- `M` rxjava3-http-client/src/main/java/io/micronaut/rxjava3/http/client/BridgedRx3HttpClient.java
- `M` rxjava3-http-client/src/main/java/io/micronaut/rxjava3/http/client/BridgedRx3StreamingHttpClient.java
- `M` rxjava3-http-client/src/main/java/io/micronaut/rxjava3/http/client/Rx3HttpClient.java
- `M` rxjava3-http-client/src/main/java/io/micronaut/rxjava3/http/client/Rx3HttpClientFactory.java
- `M` rxjava3-http-client/src/main/java/io/micronaut/rxjava3/http/client/Rx3SseClient.java
- `M` rxjava3-http-client/src/main/java/io/micronaut/rxjava3/http/client/Rx3StreamingHttpClient.java
- `M` rxjava3-http-client/src/main/java/io/micronaut/rxjava3/http/client/proxy/BridgedProxyRx3HttpClient.java
- `M` rxjava3-http-client/src/main/java/io/micronaut/rxjava3/http/client/proxy/Rx3ProxyHttpClient.java
- `M` rxjava3-http-client/src/main/java/io/micronaut/rxjava3/http/client/proxy/Rx3ProxyHttpClientFactory.java
- `M` rxjava3-http-client/src/main/java/io/micronaut/rxjava3/http/client/sse/BridgedRx3SseClient.java
- `M` rxjava3-http-client/src/main/java/io/micronaut/rxjava3/http/client/sse/RxSseClientFactory.java
- `M` rxjava3-http-client/src/main/java/io/micronaut/rxjava3/http/client/websockets/Rx3WebSocketClient.java
- `M` rxjava3-http-client/src/main/java/io/micronaut/rxjava3/http/client/websockets/Rx3WebSocketClientFactory.java
- `D` rxjava3/src/main/java/io/micronaut/rxjava3/converters/RxJava2ToRxJava3ConveterRegistrar.java
- `M` rxjava3/src/main/java/io/micronaut/rxjava3/converters/RxJava3ConverterRegistrar.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

