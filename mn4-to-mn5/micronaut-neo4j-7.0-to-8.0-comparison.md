• Compared as mn4/7.0.x -> mn5/8.0.x based on branch metadata.

  Scope:

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-neo4j, branch 7.0.x, commit
    9254ce5d997a6ff5c3369a1e1b6436cee6ec4107
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-neo4j, branch 8.0.x, commit
    5ff72ef0450c2886d0dbd3e32b50ce25ccf3661c
  - Both worktrees are clean and use the same remote.

  Full report: /private/tmp/micronaut-neo4j-7.0-to-8.0-comparison.md:1

  Key findings:

  - 49 files changed: 25 added, 24 modified; 3,662 insertions, 153 deletions.
  - Main platform moves to Micronaut 5: projectVersion 7.0.1-SNAPSHOT -> 8.0.1-SNAPSHOT, micronaut 4.10.8 ->
    5.0.0.
  - Build/runtime baseline shifts: Gradle 8.14.3 -> 9.5.1, shared settings plugin 7.6.6 -> 8.0.0-M18, .sdkmanrc
    adds java=25.0.1-graal, CI matrix changes from Java 17/21 to Java 25.
  - Neo4j driver changes: org.neo4j.driver:neo4j-java-driver 6.0.2 -> 6.1.0.
  - Other dependency updates: Micronaut Test 4.10.2 -> 5.0.0, Validation 4.12.0 -> 5.0.0, gRPC 4.12.0 -> 5.0.0.
  - Production source impact is very small: only Neo4jBoltConfiguration.java changed, replacing Micronaut
    nullability annotations with JSpecify annotations and adjusting Config.TrustStrategy nullability syntax. I
    did not see public Neo4j APIs removed.
  - Test dependency wiring changed from micronaut-test-resources to direct Testcontainers Neo4j usage via
    org.testcontainers:testcontainers-neo4j.
  - CI/release adds the same newer vulnerability audit flow and Sonatype audit workflow pattern seen in the
    other MN5 repos.

  I did not run tests; this was a folder comparison and targeted diff inspection.

# Release Note Comparison

Generated: 2026-05-19 09:19 UTC
Comparison: `7.0.x` -> `8.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-neo4j` | `7.0.x` | `9254ce5d997a` | `git@github.com:micronaut-projects/micronaut-neo4j.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-neo4j` | `8.0.x` | `5ff72ef0450c` | `git@github.com:micronaut-projects/micronaut-neo4j.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-neo4j`
- Commit candidates found: 45
- File changes listed: 49
- Version values listed: 17
- File status counts: A=25, M=24

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `7.0.1-SNAPSHOT` | `8.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-neo4j-java-driver` | `org.neo4j.driver:neo4j-java-driver:6.0.2` | `org.neo4j.driver:neo4j-java-driver:6.1.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-grpc` | `io.micronaut.grpc:micronaut-grpc-bom:4.12.0` | `io.micronaut.grpc:micronaut-grpc-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-resources` | `io.micronaut.testresources:micronaut-test-resources-bom:2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-validation` | `io.micronaut.validation:micronaut-validation-bom:4.12.0` | `io.micronaut.validation:micronaut-validation-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.29` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.managed-neo4j-driver` | `6.0.2` | `6.1.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.8` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-grpc` | `4.12.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.10.2` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test-resources` | `2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.12.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |
| `settings.gradle` | `plugin.io.micronaut.build.shared.settings` | `7.6.6` | `8.0.0-M18` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Fixes

- `41b8107104de` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m26 (#630) (renovate[bot], 2026-05-01)
- `75291fe4487a` fix(deps): update micronaut dependencies (#625) (renovate[bot], 2026-04-29)
- `05fa9e398262` fix(deps): update dependency org.neo4j.driver:neo4j-java-driver to v6.0.5 (#617) (renovate[bot], 2026-04-26)
- `50a15182fbf9` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m22 (#622) (renovate[bot], 2026-04-16)
- `f8df1830b22e` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m17 (#615) (renovate[bot], 2026-03-18)
- `43d608a61747` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.12 (#604) (renovate[bot], 2025-12-31)

### Dependency Updates

- `f228dcdccb35` chore: Bump version to 8.0.1-SNAPSHOT (micronaut-build, 2026-05-14)
- `7e5c9fcb28b3` chore: Bump version to 8.0.0-SNAPSHOT (micronaut-build, 2026-05-07)
- `b4508c71a3ac` chore(deps): update gradle to v9.5.0 (#616) (renovate[bot], 2026-04-29)
- `736a7277efae` chore(deps): combine dependency upgrades (#628) (Sergio del Amo, 2026-04-29)
- `0384e1e43b4b` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#614) (renovate[bot], 2026-03-18)
- `183b50812111` chore: Bump version to 8.0.0-SNAPSHOT (micronaut-build, 2025-12-31)
- `ad5e53e6fe7e` chore(deps): update github artifact actions (#599) (renovate[bot], 2025-12-31)
- `b02c3930230f` chore(deps): update mikepenz/action-junit-report action to v6 (#601) (renovate[bot], 2025-12-31)
- `e42fb4ebf3d6` chore(deps): update gradle to v9.2.1 (#602) (renovate[bot], 2025-12-31)
- `66801f90ec77` chore(deps): update actions/checkout action to v6 (#603) (renovate[bot], 2025-12-31)
- `2c176220adc5` chore(deps): update graalvm/setup-graalvm action to v1.4.4 (#605) (renovate[bot], 2025-12-31)
- `d6659b939e4f` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m13 (#606) (renovate[bot], 2025-12-31)
- `a311d5cf8721` chore(deps): update softprops/action-gh-release action to v2.5.0 (#609) (renovate[bot], 2025-12-31)
- `62f1e002dbfd` chore(deps): update actions/cache action to v5 (#610) (renovate[bot], 2025-12-31)
- `d19934ba4ea7` chore(deps): update softprops/action-gh-release action to v2.4.2 (#600) (renovate[bot], 2025-11-11)

### Review Candidates

- `5ff72ef0450c` update versions (Sergio del Amo, 2026-05-19)
- `2bff9f153255` [skip ci] Release v8.0.0 (micronaut-build, 2026-05-14)
- `4352034dea8f` update versions (Sergio del Amo, 2026-05-14)
- `f496b19cece6` Update common files (#634) (micronaut-build, 2026-05-14)
- `e6aa9eb3c239` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `624138c15c50` Update common files (#633) (micronaut-build, 2026-05-09)
- `75396aecd607` [skip ci] Release v8.0.0-RC1 (micronaut-build, 2026-05-07)
- `a7cc1a61f5fe` Neo4j 6.1.0 (Sergio del Amo, 2026-05-07)
- `21e377a83df4` update versions (Sergio del Amo, 2026-05-07)
- `a5eadadec570` Update common files (#632) (micronaut-build, 2026-05-07)
- `88215776490b` Update common files (#631) (micronaut-build, 2026-05-05)
- `6c9755c37d8f` Update common files (#629) (micronaut-build, 2026-05-01)
- `cf429ebc51d5` Update common files (#627) (micronaut-build, 2026-04-29)
- `8f440e58f7ea` Update common files (#620) (micronaut-build, 2026-04-26)
- `de9ba7933926` Update common files (#613) (micronaut-build, 2026-03-18)
- `b1669e591e81` [skip ci] Release v8.0.0-M1 (micronaut-build, 2025-12-31)
- `5e18cde7e916` Update to Core Milestone (#611) (Sergio del Amo, 2025-12-31)
- `f241245a3378` Update common files (#598) (micronaut-build, 2025-12-31)
- `2de85f1f427f` Replace Micronaut nullability annotations with JSpecify annotations (#608) (Copilot, 2025-12-02)
- `7ddc0f7a71e5` Merge branch '7.0.x' into 8.0.x (Sergio del Amo, 2025-11-05)
- `2b5a9badb526` revert changes (Sergio del Amo, 2025-11-05)
- `340f32adee51` git: ignore buildSrc/gradle.properties (Sergio del Amo, 2025-11-05)
- `4f387334cab5` Merge branch '7.0.x' into 8.0.x (Sergio del Amo, 2025-11-05)
- `df0ee55ae1c0` projectVersion=8.0.0-SNAPSHOT (Sergio del Amo, 2025-11-05)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.neo4j-module.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` neo4j-bolt/build.gradle
- `M` neo4j-bom/build.gradle
- `M` settings.gradle

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
- `M` config/checkstyle/checkstyle.xml
- `M` neo4j-bolt/src/main/java/io/micronaut/neo4j/bolt/Neo4jBoltConfiguration.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

