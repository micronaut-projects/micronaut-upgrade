
• Compared in release direction mn4 -> mn5.

  Full report: micronaut-toml-mn4-to-mn5-comparison.md:1

  Scope:

  - Previous: mn4/micronaut-toml, branch 2.8.x, commit 58885945988d, clean
  - Current: mn5/micronaut-toml, branch 3.0.x, commit 5a746e645c51, clean
  - Delta: 46 commit candidates, 44 changed files

  Release-note draft:

  ## Micronaut TOML 3.0

  ### Compatibility

  - Updated for the Micronaut 5 baseline.
  - Updated TOML parser source to use JSpecify nullability annotations.

  ### Internal / Build

  - Updated Gradle and Micronaut build tooling.
  - Refactored parser tests to use JUnit Jupiter assertions.
  - Simplified TOML property source loader test coverage to exercise real `application.toml` and `application-test.toml` resources.

  Important dependency/tooling changes:

  - Project version: 2.8.1-SNAPSHOT -> 3.0.0-SNAPSHOT
  - Micronaut Core: 4.10.4 -> 5.0.0-RC2
  - JetBrains annotations: 26.0.2 -> 26.1.0
  - JFlex remains 1.9.1
  - Gradle wrapper: 8.14.3 -> 9.5.0
  - Micronaut build shared settings plugin: 7.6.4 -> 8.0.0-M18
  - Local pins removed: Groovy 4.0.13, Micronaut Docs 2.0.0, Micronaut Test 4.7.0, Spock 2.3-groovy-4.0

  No repository-local breaking changes were confirmed from the source/docs diffs. Tests were not run; this was a static comparison.

# Release Note Comparison

Generated: 2026-05-07 07:31 UTC
Comparison: `mn4` -> `mn5`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-toml` | `2.8.x` | `58885945988d` | `git@github.com:micronaut-projects/micronaut-toml.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-toml` | `3.0.x` | `5a746e645c51` | `git@github.com:micronaut-projects/micronaut-toml.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-toml`
- Commit candidates found: 46
- File changes listed: 44
- Version values listed: 12
- File status counts: A=19, M=25

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `2.8.1-SNAPSHOT` | `3.0.0-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.jetbrains-annotations` | `org.jetbrains:annotations:26.0.2` | `org.jetbrains:annotations:26.1.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.jflex` | `de.jflex:jflex:1.9.1` | `de.jflex:jflex:1.9.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.13` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.jetbrains-annotations` | `26.0.2` | `26.1.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.jflex` | `1.9.1` | `1.9.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.4` | `5.0.0-RC2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `2.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.7.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.0` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Fixes

- `b27ec1c071d5` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-rc2 (#320) (renovate[bot], 2026-05-07)
- `fc0f7f7c1197` fix(deps): update micronaut dependencies (renovate[bot], 2026-04-30)
- `8e9c403dd445` fix(deps): update dependency org.jetbrains:annotations to v26.1.0 (#308) (renovate[bot], 2026-04-17)
- `6624bdc5b97a` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m20 (#312) (renovate[bot], 2026-04-07)
- `db04a42c6365` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m17 (#301) (renovate[bot], 2026-03-17)
- `9179de3c7fb8` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#292) (renovate[bot], 2025-12-10)
- `06fb732ec86e` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.8 (#277) (renovate[bot], 2025-11-03)

### Dependency Updates

- `d3e6c457ea39` Merge pull request #316 from micronaut-projects/renovate/micronaut-dependencies (Graeme Rocher, 2026-05-01)
- `cebff0c452bc` chore(deps): update gradle to v9.5.0 (renovate[bot], 2026-04-28)
- `9f211dfc3d03` chore: Bump version to 3.0.0-SNAPSHOT (micronaut-build, 2026-04-17)
- `669e58721747` chore(deps): update gradle to v9.4.1 (#307) (renovate[bot], 2026-04-17)
- `9c7f2f8cf09a` chore(deps): update gradle/actions action to v6 (#311) (renovate[bot], 2026-04-17)
- `71e5d4858c73` chore(deps): update softprops/action-gh-release action to v2.6.2 (#313) (renovate[bot], 2026-04-17)
- `c4597929954e` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#303) (renovate[bot], 2026-03-17)
- `1bb3c907f4a0` chore: Bump version to 3.0.0-SNAPSHOT (micronaut-build, 2025-12-12)
- `7e9f69c59959` chore(deps): update actions/checkout action to v6 (#291) (renovate[bot], 2025-12-10)
- `d16856f88d1e` chore(deps): update gradle to v9.2.1 (#290) (renovate[bot], 2025-12-10)
- `333ca624e672` chore(deps): update stefanzweifel/git-auto-commit-action action to v7 (#289) (renovate[bot], 2025-12-10)
- `8f7a1d0bf608` chore(deps): update softprops/action-gh-release action to v2.5.0 (#288) (renovate[bot], 2025-12-10)
- `8afda008bb03` chore(deps): update mikepenz/action-junit-report action to v6 (#287) (renovate[bot], 2025-12-10)
- `af2fd6567fe5` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#286) (renovate[bot], 2025-12-10)
- `88c77de08d23` chore(deps): update graalvm/setup-graalvm action to v1.4.4 (#293) (renovate[bot], 2025-12-10)
- `08a9d6676f49` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#280) (renovate[bot], 2025-11-03)
- `d129f08507cf` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m8 (#281) (renovate[bot], 2025-11-03)
- `0279b60ac7ac` chore(deps): update github artifact actions (#282) (renovate[bot], 2025-11-03)
- `a4b117739905` chore(deps): update gradle to v9.2.0 (#283) (renovate[bot], 2025-11-03)
- `686c7cf8b3a9` chore(deps): update gradle/actions action to v5 (#284) (renovate[bot], 2025-11-03)

### Internal

- `7e9e024a0a30` Build: Update to Micronaut 5 (#298) (issam liqali, 2025-12-12)
- `6d5b1bcce841` ci: projectVersion=3.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-10-14)

### Review Candidates

- `5a746e645c51` Update common files (#319) (micronaut-build, 2026-05-07)
- `bb20b6469a91` Merge pull request #317 from micronaut-projects/renovate/gradle-9.x (Graeme Rocher, 2026-05-01)
- `da1a6f4a631c` Merge pull request #318 from micronaut-projects/sync-files-3.0.x (Graeme Rocher, 2026-05-01)
- `b21e6b68b0bd` Update common files (micronaut-build, 2026-04-30)
- `02447ea2b54b` Merge pull request #315 from micronaut-projects/sync-files-3.0.x (Graeme Rocher, 2026-04-26)
- `e9550a3bfdb2` Update common files (micronaut-build, 2026-04-21)
- `05525baa9abc` [skip ci] Release v3.0.0-M2 (micronaut-build, 2026-04-17)
- `6b9f853ad40b` micronaut = "5.0.0-M22" (Sergio del Amo, 2026-04-17)
- `6e4d199d6cc8` Update common files (#310) (micronaut-build, 2026-04-17)
- `cd1a2def70a7` Update common files (#304) (micronaut-build, 2026-03-17)
- `21e4c0e8a682` [skip ci] Release v3.0.0-M1 (micronaut-build, 2025-12-12)
- `79816c5b8092` Refactor tests to use junit Assertions (#294) (issam liqali, 2025-12-10)
- `039d259f9a66` Update common files (#285) (micronaut-build, 2025-12-10)
- `3e47058af756` Micronaut 5 compatibility (#279) (issam liqali, 2025-11-03)
- `6d9c8b4a79f1` Update common files (#278) (micronaut-build, 2025-11-03)
- `d8d68472bf3f` Micronaut Gradle build Plugin 8.0.0-M4 (Sergio del Amo, 2025-10-14)
- `14e4d438eae8` gradle 9.1 (Sergio del Amo, 2025-10-14)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` .github/workflows/update-gradle-wrapper.yml
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` settings.gradle
- `M` toml/build.gradle

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
- `M` toml/src/main/java/io/micronaut/toml/Parser.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` toml/src/test/groovy/io/micronaut/toml/env/TomlPropertySourceLoaderSpec.groovy
- `M` toml/src/test/java/io/micronaut/toml/ParserTest.java
- `A` toml/src/test/resources/application-test.toml
- `A` toml/src/test/resources/application.toml

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

