# Release Note Comparison

Generated: 2026-05-06 16:42 UTC
Comparison: `mn4` -> `mn5`
Mode: filesystem

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-picocli` | `5.9.x` | `9f7e0b8e3506` | `git@github.com:micronaut-projects/micronaut-picocli.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-picocli` | `6.0.x` | `1a15dc19f971` | `git@github.com:micronaut-projects/micronaut-picocli.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: not available
- Commit candidates found: 0
- File changes listed: 49
- Version values listed: 13
- File status counts: A=19, M=30

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `5.9.1-SNAPSHOT` | `6.0.0-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-picocli` | `info.picocli:picocli:4.7.7` | `info.picocli:picocli:4.7.7` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-picocli-codegen` | `info.picocli:picocli-codegen:4.7.7` | `info.picocli:picocli-codegen:4.7.7` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.13` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.kotlin` | `1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.managed-picocli` | `4.7.7` | `4.7.7` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.4` | `5.0.0-RC2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `2.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.9.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.0` | `changed` |

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
- `A` buildSrc/gradle.properties
- `A` buildSrc/src/main/groovy/io.micronaut.build.internal.picocli-testsuite-kotlin.gradle
- `M` .github/workflows/gradle.yml
- `M` buildSrc/build.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.picocli-testsuite.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` picocli/build.gradle
- `M` settings.gradle
- `M` test-suite-kotlin/build.gradle
- `M` test-suite/build.gradle

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
- `M` picocli/src/main/java/io/micronaut/configuration/picocli/MicronautFactory.java
- `M` picocli/src/main/java/io/micronaut/configuration/picocli/PicocliRunner.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` picocli/src/test/java/io/micronaut/configuration/picocli/MicronautFactoryCommandTest.java
- `M` picocli/src/test/java/io/micronaut/configuration/picocli/MicronautFactoryTest.java
- `M` picocli/src/test/java/io/micronaut/configuration/picocli/PicocliRunnerTest.java

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

