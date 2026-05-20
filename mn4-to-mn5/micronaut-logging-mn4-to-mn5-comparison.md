# Release Note Comparison

Generated: 2026-05-07 07:38 UTC
Comparison: `mn4` -> `mn5`
Mode: filesystem

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-logging` | `1.7.x` | `68d416e43858` | `git@github.com:micronaut-projects/micronaut-logging.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-logging` | `2.0.x` | `6de17a24c81e` | `git@github.com:micronaut-projects/micronaut-logging.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: not available
- Commit candidates found: 0
- File changes listed: 47
- Version values listed: 25
- File status counts: A=25, M=22

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `1.7.5-SNAPSHOT` | `2.0.0-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.boms-log4j` | `org.apache.logging.log4j:log4j-bom:2.25.3` | `org.apache.logging.log4j:log4j-bom:2.25.4` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-log4j` | `org.apache.logging.log4j:log4j-core:2.25.3` | `org.apache.logging.log4j:log4j-core:2.25.4` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-logback-access` | `ch.qos.logback:logback-access:1.5.32` | `ch.qos.logback:logback-access:1.5.32` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-logback-classic` | `ch.qos.logback:logback-classic:1.5.32` | `ch.qos.logback:logback-classic:1.5.32` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-logback-core` | `ch.qos.logback:logback-core:1.5.32` | `ch.qos.logback:logback-core:1.5.32` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-slf4j-api` | `org.slf4j:slf4j-api:2.0.17` | `org.slf4j:slf4j-api:2.0.17` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-slf4j-ext` | `org.slf4j:slf4j-ext:2.0.17` | `org.slf4j:slf4j-ext:2.0.17` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-slf4j-jcl-over-slf4j` | `org.slf4j:jcl-over-slf4j:2.0.17` | `org.slf4j:jcl-over-slf4j:2.0.17` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-slf4j-jul-to-slf4j` | `org.slf4j:jul-to-slf4j:2.0.17` | `org.slf4j:jul-to-slf4j:2.0.17` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-slf4j-log4j-over-slf4j` | `org.slf4j:log4j-over-slf4j:2.0.17` | `org.slf4j:log4j-over-slf4j:2.0.17` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-slf4j-log4j12` | `org.slf4j:slf4j-log4j12:2.0.17` | `org.slf4j:slf4j-log4j12:2.0.17` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-slf4j-nop` | `org.slf4j:slf4j-nop:2.0.17` | `org.slf4j:slf4j-nop:2.0.17` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-slf4j-osgi-over-slf4j` | `org.slf4j:osgi-over-slf4j:2.0.17` | `org.slf4j:osgi-over-slf4j:2.0.17` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-slf4j-reload4j` | `org.slf4j:slf4j-reload4j:2.0.17` | `org.slf4j:slf4j-reload4j:2.0.17` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-slf4j-simple` | `org.slf4j:slf4j-simple:2.0.17` | `org.slf4j:slf4j-simple:2.0.17` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.micronaut-core` | `io.micronaut:micronaut-core-bom:4.10.15` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.managed-log4j` | `2.25.3` | `2.25.4` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-logback` | `1.5.32` | `1.5.32` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-logback-access` | `1.5.32` | `1.5.32` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-slf4j` | `2.0.17` | `2.0.17` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.15` | `5.0.0-RC2` | `changed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.0` | `changed` |
| `settings.gradle.kts` | `plugin.io.micronaut.build.shared.settings` | `7.6.6` | `8.0.0-M18` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Review Candidates

- Git commit range was unavailable. Use the changed-file sections below and inspect diffs manually before drafting release notes.

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
- `M` settings.gradle.kts
- `M` test-suite/build.gradle.kts

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
- `A` .github/scripts/vulnerability-audit-filter.py
- `A` .github/scripts/vulnerability-audit.sh
- `A` .github/workflows/sonatype.yml
- `A` .sdkmanrc
- `M` .clineignore
- `M` .clinerules/coding.md
- `M` .github/instructions/coding.instructions.md
- `M` .github/renovate.json
- `M` .github/workflows/central-sync.yml
- `M` .github/workflows/graalvm-dev.yml
- `M` .github/workflows/publish-snapshot.yml
- `M` .gitignore
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

