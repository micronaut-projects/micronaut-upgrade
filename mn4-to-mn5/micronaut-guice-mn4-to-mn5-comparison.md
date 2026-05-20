Generated the comparison in release direction mn4 -> mn5.

  Full report: micronaut-guice-mn4-to-mn5-comparison.md:1

  Scope: previous 1.3.x at ffe0b133b331, current 2.0.x at 2478a90c75e4; both worktrees are clean. Delta: 51 commits, 43 changed files.

  Release Note Draft

  - Compatibility: Updated the project line from 1.3.1-SNAPSHOT -> 2.0.0-SNAPSHOT and moved to the Micronaut 5 baseline.
  - Breaking: No repository-specific breaking-change guide or confirmed user-facing API removal was found. The only production source diffs are JSpecify nullability import updates and a field ordering cleanup.
  - Dependencies: Guice remains 7.0.0; Guava updates 33.4.8-jre -> 33.6.0-jre.
  - Build: Gradle wrapper updates 8.14.3 -> 9.5.0; Micronaut shared settings plugin updates 7.6.4 -> 8.0.0-M18.
  - Internal: Local catalog pins for Groovy 4.0.27, Spock 2.3-groovy-4.0, Micronaut Docs 2.0.0, and Micronaut Test 4.9.0 were removed.

  Tests were not run; this was a comparison/reporting pass only.

# Release Note Comparison

Generated: 2026-05-06 16:18 UTC
Comparison: `mn4` -> `mn5`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-guice` | `1.3.x` | `ffe0b133b331` | `git@github.com:micronaut-projects/micronaut-guice.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-guice` | `2.0.x` | `2478a90c75e4` | `git@github.com:micronaut-projects/micronaut-guice.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-guice`
- Commit candidates found: 51
- File changes listed: 43
- Version values listed: 13
- File status counts: A=17, M=26

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `1.3.1-SNAPSHOT` | `2.0.0-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-guava` | `com.google.guava:guava:33.4.8-jre` | `com.google.guava:guava:33.6.0-jre` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-guice` | `com.google.inject:guice:7.0.0` | `com.google.inject:guice:7.0.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.27` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.managed-guava` | `33.4.8-jre` | `33.6.0-jre` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-guice` | `7.0.0` | `7.0.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.3` | `5.0.0-RC2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `2.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.9.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.0` | `changed` |
| `settings.gradle.kts` | `plugin.io.micronaut.build.shared.settings` | `7.6.4` | `8.0.0-M18` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `a5aa4a7351de` remove unused dependency (Sergio del Amo, 2026-04-17)

### Fixes

- `b4c569cfd0b2` fix(deps): update micronaut dependencies (renovate[bot], 2026-04-30)
- `7595094f8a5f` fix(deps): update dependency com.google.guava:guava to v33.6.0-jre (renovate[bot], 2026-04-29)
- `aa24360574de` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m22 (#115) (renovate[bot], 2026-04-17)
- `8042a5e5014e` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m17 (#104) (renovate[bot], 2026-03-19)
- `3b83b71b0753` fix(deps): update dependency com.google.guava:guava to v33.5.0-jre (#87) (renovate[bot], 2025-12-10)
- `37eb0f770977` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#93) (renovate[bot], 2025-12-10)
- `ece8c18f59fa` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.6 (#81) (renovate[bot], 2025-10-16)

### Dependency Updates

- `2478a90c75e4` Update Micronaut version to 5.0.0-RC2 (Sergio del Amo, 2026-05-06)
- `6db09a564292` Merge pull request #118 from micronaut-projects/renovate/micronaut-dependencies (Graeme Rocher, 2026-05-01)
- `26e0147c5f0e` chore(deps): update gradle to v9.5.0 (renovate[bot], 2026-04-28)
- `3986af90409f` chore: Bump version to 2.0.0-SNAPSHOT (micronaut-build, 2026-04-17)
- `5b00a0a30ef4` chore(deps): update peter-evans/create-pull-request action to v8 (#109) (renovate[bot], 2026-04-17)
- `62e58e815328` chore(deps): update gradle to v9.4.1 (#111) (renovate[bot], 2026-04-17)
- `ad7bfdc7a9ee` chore(deps): update gradle/actions action to v6 (#114) (renovate[bot], 2026-04-17)
- `aba78cdb54f3` chore(deps): update softprops/action-gh-release action to v2.6.2 (#116) (renovate[bot], 2026-04-17)
- `ca34a8a500f0` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#107) (renovate[bot], 2026-03-19)
- `c5c05264a3fd` chore: Bump version to 2.0.0-SNAPSHOT (micronaut-build, 2025-12-10)
- `529502ed6313` chore(deps): update gradle to v9.2.1 (#95) (renovate[bot], 2025-12-10)
- `ce8ada42e5e8` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#92) (renovate[bot], 2025-12-10)
- `49fc12dc2919` chore(deps): update github artifact actions (#97) (renovate[bot], 2025-12-10)
- `ff41628b7e77` chore(deps): update softprops/action-gh-release action to v2.5.0 (#96) (renovate[bot], 2025-12-10)
- `d17e2ea80322` chore(deps): update mikepenz/action-junit-report action to v6 (#98) (renovate[bot], 2025-12-10)
- `5236a3e6f2bb` chore(deps): update stefanzweifel/git-auto-commit-action action to v7 (#99) (renovate[bot], 2025-12-10)
- `137d10077b4b` chore(deps): update actions/checkout action to v6 (#100) (renovate[bot], 2025-12-10)
- `878cf15cc575` chore(deps): update graalvm/setup-graalvm action to v1.4.4 (#101) (renovate[bot], 2025-12-10)
- `66aa41d55c84` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#89) (renovate[bot], 2025-10-27)
- `0041c06bb499` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m5 (#90) (renovate[bot], 2025-10-27)

### Documentation

- `a06fd84a2c5f` Docs: update micronaut-docs to 3.0.0 (#84) (issam liqali, 2025-10-16)

### Internal

- `a3f56a6bc0fd` ci: projectVersion=2.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-10-13)

### Review Candidates

- `74bfab2bd192` Update common files (#122) (micronaut-build, 2026-05-06)
- `617cdad0dc24` Merge pull request #121 from micronaut-projects/renovate/guava-monorepo (Graeme Rocher, 2026-05-01)
- `9d3be134638a` Merge pull request #119 from micronaut-projects/renovate/gradle-9.x (Graeme Rocher, 2026-05-01)
- `c275d720ed5a` Merge pull request #120 from micronaut-projects/sync-files-2.0.x (Graeme Rocher, 2026-05-01)
- `b132a27044ab` Update common files (micronaut-build, 2026-04-30)
- `24fe268340bf` Merge pull request #117 from micronaut-projects/sync-files-2.0.x (Graeme Rocher, 2026-04-26)
- `7df4b6149bde` Update common files (micronaut-build, 2026-04-21)
- `c9517ee3be34` [skip ci] Release v2.0.0-M2 (micronaut-build, 2026-04-17)
- `08f9d5b4935e` Update common files (#113) (micronaut-build, 2026-04-17)
- `b1a7d9473b8a` Update common files (#105) (micronaut-build, 2026-03-19)
- `bb27605c9127` [skip ci] Release v2.0.0-M1 (micronaut-build, 2025-12-10)
- `2f80d289711e` micronaut = "5.0.0-M2" (Sergio del Amo, 2025-12-10)
- `0fdfe331a47b` Update common files (#94) (micronaut-build, 2025-12-10)
- `8d4e3648faa3` Replace Micronaut nullability annotations with JSpecify nullability annotations (#103) (Copilot, 2025-12-01)
- `d888abeb631e` Micronaut build gradle plugin 8.0.0-M6 (Sergio del Amo, 2025-10-27)
- `ffebcc579fa0` Update common files (#88) (micronaut-build, 2025-10-27)
- `95b81933acc3` Merge branch '1.3.x' into 2.0.x (Sergio del Amo, 2025-10-27)
- `15b76837d591` Micronaut 5 compatibility and release prep (#86) (issam liqali, 2025-10-16)
- `da4fa7c6db6a` Update common files (#85) (micronaut-build, 2025-10-16)
- `d845cfebb516` Micronatu build plugin  8.0.0-M4 (Sergio del Amo, 2025-10-13)
- `9497c23ab428` gradel 9.1 (Sergio del Amo, 2025-10-13)

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
- `M` micronaut-guice/build.gradle.kts
- `M` settings.gradle.kts

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
- `M` .github/workflows/files-sync.yml
- `M` .github/workflows/graalvm-dev.yml
- `M` .github/workflows/publish-snapshot.yml
- `A` .github/workflows/sonatype.yml
- `M` .gitignore
- `A` .sdkmanrc
- `M` MAINTAINING.md
- `M` config/checkstyle/checkstyle.xml
- `M` micronaut-guice-annotation/src/main/java/io/micronaut/guice/annotation/internal/GuiceAnnotation.java
- `M` micronaut-guice-processor/src/main/java/io/micronaut/guice/processor/ImportModuleVisitor.java
- `M` micronaut-guice/src/main/java/io/micronaut/guice/GuiceModuleBinder.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

