• Generated the comparison in release direction mn4 -> mn5.

  Full report: micronaut-groovy-mn4-to-mn5-comparison.md:1

  Scope: previous 4.8.x at 93d217fbbd1b, current 5.0.x at 664ae4ac15a9; both worktrees are clean. Delta: 50 commits, 41 changed files.

  Release Note Draft

  - Compatibility: Updated the module line to Micronaut 5. No repository-specific breaks.adoc or source-level breaking change was found in this comparison.
  - Build/BOM: groovy-bom now resolves the Groovy BOM version from the imported Micronaut catalog instead of a local groovy = "4.0.18" catalog entry.
  - Build: function-groovy and runtime-groovy now set explicit Micronaut module descriptor parentModuleId values.
  - Internal: JavaParser documentation dependency now comes from the Micronaut catalog instead of the local javaparser = 3.27.1 version.

  Dependency/Tooling Changes

  - Project version 4.8.0-SNAPSHOT -> 5.0.0-SNAPSHOT
  - Micronaut Core 4.10.4 -> 5.0.0-RC2
  - Gradle wrapper 8.14.3 -> 9.5.0
  - Micronaut shared settings plugin 7.6.4 -> 8.0.0-M18
  - .sdkmanrc Java not present -> 25.0.1-graal
  - Local catalog pins removed: Groovy 4.0.18 -> not present, Spock 2.3-groovy-4.0 -> not present, Micronaut Test 4.9.0 -> not present, Micronaut Docs 3.0.0 -> not present

  I did not run tests; this was a comparison/reporting pass only.


# Release Note Comparison

Generated: 2026-05-06 16:00 UTC
Comparison: `mn4` -> `mn5`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-groovy` | `4.8.x` | `93d217fbbd1b` | `git@github.com:micronaut-projects/micronaut-groovy.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-groovy` | `5.0.x` | `664ae4ac15a9` | `git@github.com:micronaut-projects/micronaut-groovy.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-groovy`
- Commit candidates found: 50
- File changes listed: 41
- Version values listed: 9
- File status counts: A=17, M=24

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `graphqlJavaVersion` | `14.1` | `14.1` | `unchanged` |
| `gradle.properties` | `projectVersion` | `4.8.0-SNAPSHOT` | `5.0.0-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.18` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.4` | `5.0.0-RC2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.9.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.0` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Fixes

- `a8f8e334d02e` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m26 (#715) (renovate[bot], 2026-05-01)
- `2769993d0e9a` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m25 (#711) (renovate[bot], 2026-04-30)
- `e677786e5975` fix(deps): update dependency com.github.javaparser:javaparser-core to v3.28.0 (#698) (renovate[bot], 2026-04-22)
- `4afbac61b010` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m24 (#703) (renovate[bot], 2026-04-22)
- `07342267b5c3` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m10 (#697) (renovate[bot], 2026-02-12)
- `b372462061cc` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.12 (#688) (renovate[bot], 2025-12-29)
- `9c51ad2f8357` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#682) (renovate[bot], 2025-12-10)
- `6f6cf71c124c` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.8 (#673) (renovate[bot], 2025-11-03)
- `671470cc7e98` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.6 (#666) (renovate[bot], 2025-10-17)

### Dependency Updates

- `664ae4ac15a9` Update Micronaut version to 5.0.0-RC2 (Sergio del Amo, 2026-05-06)
- `257e81269f8f` chore(deps): update gradle to v9.5.0 (#713) (renovate[bot], 2026-04-30)
- `1a5f50c91505` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-04-27)
- `1235d4883844` don’t define javaparser version use from core (Sergio del Amo, 2026-04-27)
- `2bb2a581aea1` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m18 (#710) (renovate[bot], 2026-04-27)
- `c7c9c7a9a39b` chore(deps): update gradle to v9.4.1 (#706) (renovate[bot], 2026-04-22)
- `3f351cf30e18` chore(deps): update gradle/actions action to v6 (#708) (renovate[bot], 2026-04-22)
- `d4831a8de668` chore(deps): update softprops/action-gh-release action to v3 (#709) (renovate[bot], 2026-04-22)
- `13371f67b580` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#702) (renovate[bot], 2026-04-22)
- `f988c89d3ece` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m16 (#701) (renovate[bot], 2026-02-12)
- `31bbd0caa3e8` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-02-04)
- `380d89bea293` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m15 (#696) (renovate[bot], 2026-02-04)
- `69e24fa9cb4d` Upgrade micronaut to v5 (#694) (Ayoub Ait Abdellah, 2026-02-03)
- `34c072a929d9` chore(deps): update github artifact actions (#691) (renovate[bot], 2025-12-29)
- `dde98ea53d03` chore(deps): update actions/cache action to v5 (#690) (renovate[bot], 2025-12-29)
- `a085ff909a12` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m13 (#689) (renovate[bot], 2025-12-29)
- `605debaf50bc` chore(deps): update actions/checkout action to v6.0.1 (#681) (renovate[bot], 2025-12-10)
- `7a70ead20e53` chore(deps): update mikepenz/action-junit-report action to v6 (#679) (renovate[bot], 2025-12-10)
- `9ce21fa4082c` chore(deps): update softprops/action-gh-release action to v2.5.0 (#678) (renovate[bot], 2025-12-10)
- `7a35ff770978` chore(deps): update github artifact actions (#677) (renovate[bot], 2025-12-10)
- `57f80614a978` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#676) (renovate[bot], 2025-12-10)
- `639089e41e16` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#670) (renovate[bot], 2025-11-03)
- `e68aeeb7995f` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m8 (#672) (renovate[bot], 2025-11-03)
- `8edb826d2d10` chore(deps): update gradle to v9.2.0 (#674) (renovate[bot], 2025-11-03)

### Review Candidates

- `cc6e09fa1127` Update common files (#716) (micronaut-build, 2026-05-06)
- `dde83b1e2660` Update common files (#714) (micronaut-build, 2026-05-01)
- `ec7a496dbd6a` Update common files (#712) (micronaut-build, 2026-04-30)
- `4464bc718bf4` [skip ci] Release v5.0.0-M2 (micronaut-build, 2026-04-27)
- `302051839741` Update common files (#705) (micronaut-build, 2026-04-22)
- `00ae382de182` Update common files (#700) (micronaut-build, 2026-02-12)
- `d1115a8781ba` [skip ci] Release v5.0.0-M1 (micronaut-build, 2026-02-04)
- `a38bcb1d9e26` Update common files (#693) (micronaut-build, 2026-02-04)
- `988ccbd29b7c` Update common files (#687) (micronaut-build, 2025-12-29)
- `88ebac5f1cd9` Update common files (#675) (micronaut-build, 2025-12-10)
- `63625e98e49a` Micronaut 5 compatibility  (#671) (issam liqali, 2025-11-03)
- `772bd7c716d5` Update common files (#669) (micronaut-build, 2025-11-03)
- `74bcdf7309f5` Update common files (#667) (micronaut-build, 2025-10-17)
- `dadaee3d0106` Update common files (#665) (micronaut-build, 2025-10-17)
- `764037b31131` Micronaut Gradle Build Plugin 8.0.0-M4 (Sergio del Amo, 2025-10-15)
- `56a43560931b` gradle 9.1 (Sergio del Amo, 2025-10-15)
- `a81ce81a857c` projectVersion=5.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-10-15)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.groovy-module.gradle
- `M` function-groovy/build.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` groovy-bom/build.gradle
- `M` runtime-groovy/build.gradle
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

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

