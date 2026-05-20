Compared micronaut-acme as mn4 → mn5.

  Scope

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-acme, branch 5.6.x, SHA 760e38dc2fa3
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-acme, branch 6.0.x, SHA 73131c69c9ac
  - Same remote, both clean: git@github.com:micronaut-projects/micronaut-acme.git
  - Report: /private/tmp/micronaut-acme-5.6-to-6.0-comparison.md

  Key Findings

  - Major line move: projectVersion 5.6.0-SNAPSHOT → 6.0.1-SNAPSHOT.
  - Platform upgrade: Micronaut 4.10.4 → 5.0.0, Micronaut Platform 4.9.4 → 5.0.0-RC1, Gradle wrapper 8.14.3 →
    9.5.1, Micronaut Gradle plugin 4.5.5 → 5.0.0-M1.
  - ACME4J upgraded 3.5.1 → 5.1.0; AcmeService now uses the ACME4J 5 fetch() API for order/challenge polling
    and handles retry-after from Optional<Instant>.
  - Bouncy Castle 1.84 was added and constrained for bcpkix-jdk18on and bcprov-jdk18on, with comments tying
    it to GHSA-wg6q-6289-32hp and GHSA-c3fc-8qff-9hwx.
  - JSpecify annotations replace Micronaut nullability annotations in touched public classes.
  - Test infrastructure changed around Pebble/Testcontainers: HTTPS /dir ACME endpoint,
    ghcr.io/letsencrypt/pebble, explicit trust-all SSL context in tests, and SAN-based certificate assertion
    s.
  - CI/common files moved to Java 25/GraalVM, pinned newer actions, added OSV/CycloneDX vulnerability audit
    scripts/workflow, and removed the old inline OSS Index scan.
  - Remaining churn is mostly common repository template files and .agents/skills additions.

  Diff size: 62 files changed, 3849 insertions(+), 194 deletions(-).

  I did not run tests; this was a folder comparison and targeted source/build-diff review only.

# Release Note Comparison

Generated: 2026-05-19 13:39 UTC
Comparison: `5.6.x` -> `6.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-acme` | `5.6.x` | `760e38dc2fa3` | `git@github.com:micronaut-projects/micronaut-acme.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-acme` | `6.0.x` | `73131c69c9ac` | `git@github.com:micronaut-projects/micronaut-acme.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-acme`
- Commit candidates found: 48
- File changes listed: 62
- Version values listed: 16
- File status counts: A=25, M=37

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `5.6.0-SNAPSHOT` | `6.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.gradle-micronaut` | `io.micronaut.gradle:micronaut-gradle-plugin:4.5.5` | `io.micronaut.gradle:micronaut-gradle-plugin:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-resources` | `io.micronaut.testresources:micronaut-test-resources-bom:2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-validation` | `io.micronaut.validation:micronaut-validation-bom:4.11.0` | `io.micronaut.validation:micronaut-validation-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.bouncycastle` | `not present` | `1.84` | `added` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.27` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.managed-acme4j` | `3.5.1` | `5.1.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.4` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.5.5` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-platform` | `4.9.4` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.15.5` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.7.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test-resources` | `2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.11.0` | `5.0.0` | `changed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Fixes

- `a8f306cc24a6` fix(deps): update micronaut dependencies (#572) (renovate[bot], 2026-05-01)
- `15986bae6dbd` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m10 (#551) (renovate[bot], 2026-02-12)
- `78a782b380cc` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#542) (renovate[bot], 2025-12-10)
- `2dc75ae2df1e` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.12.0 (#538) (renovate[bot], 2025-12-10)
- `3a0bc2692ec1` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#537) (renovate[bot], 2025-12-10)
- `4046621d6c9b` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.6 (#524) (renovate[bot], 2025-10-17)

### Dependency Updates

- `7b43f432abc4` chore: Bump version to 6.0.1-SNAPSHOT (micronaut-build, 2026-05-14)
- `1473f3d3cfc0` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2026-05-07)
- `5e006432d4bd` Upgrade to ACME4J 5 (#577) (Graeme Rocher, 2026-05-06)
- `067c679ed31e` chore(deps): update gradle to v9.5.0 (#567) (renovate[bot], 2026-05-01)
- `263101276085` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m16 (#557) (renovate[bot], 2026-02-12)
- `67593188e085` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2026-02-04)
- `742fe09da33a` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m13 (#554) (renovate[bot], 2025-12-19)
- `87a8cb48e86d` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#544) (renovate[bot], 2025-12-10)
- `1acc52107748` chore(deps): update actions/checkout action to v6.0.1 (#539) (renovate[bot], 2025-12-10)
- `b04fc5b2cf5b` chore(deps): update softprops/action-gh-release action to v2.5.0 (#535) (renovate[bot], 2025-12-10)
- `0903f944a3be` chore(deps): update gradle to v9.2.1 (#536) (renovate[bot], 2025-12-10)
- `cffa82408591` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m9 (#531) (renovate[bot], 2025-11-04)
- `a09cb5a222dd` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m8 (#529) (renovate[bot], 2025-11-03)

### Internal

- `a7ad7540dd0d` Build: Update to Micronaut 5 (#555) (issam liqali, 2026-02-03)

### Review Candidates

- `73131c69c9ac` Update common files (#586) (micronaut-build, 2026-05-19)
- `f5151c3169f3` [skip ci] Release v6.0.0 (micronaut-build, 2026-05-14)
- `d461b6829ecf` Update common files (#585) (micronaut-build, 2026-05-14)
- `9ffcc4f228ac` Update versions (Sergio del Amo, 2026-05-14)
- `09587171eaf4` Update common files (#584) (micronaut-build, 2026-05-13)
- `a426d59facbb` micronaut-platform = "5.0.0-RC1" (Sergio del Amo, 2026-05-13)
- `ed2af88acc24` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `20b0601b6006` [skip ci] Release v6.0.0-RC1 (micronaut-build, 2026-05-07)
- `1587e8a67ffa` update versions (Sergio del Amo, 2026-05-07)
- `6ca5515fa318` Update common files (#583) (micronaut-build, 2026-05-07)
- `bee72036371a` Update common files (#576) (micronaut-build, 2026-05-06)
- `5a98461d702e` [acme] Update common files for branch 6.0.x (#575) (micronaut-build, 2026-05-04)
- `5aac85bbefbb` [acme] Update common files for branch 6.0.x (#573) (micronaut-build, 2026-05-02)
- `99b56210394a` Update common files (#566) (micronaut-build, 2026-04-26)
- `9e72039c3f84` Update common files (#560) (micronaut-build, 2026-02-12)
- `83706de7d027` [skip ci] Release v6.0.0-M1 (micronaut-build, 2026-02-04)
- `dab51591dffc` Update common files (#553) (micronaut-build, 2026-02-04)
- `834557cc6dea` Update common files (#533) (micronaut-build, 2025-12-10)
- `e40dfda64037` Replace Micronaut nullability annotations with JSpecify annotations (#548) (Copilot, 2025-12-01)
- `1f6bca1da11b` Update to m9 (#532) (Sergio del Amo, 2025-11-12)
- `2e98f9cdeea6` Update micronaut build (#528) (issam liqali, 2025-11-03)
- `9b1066e5df43` Update common files (#530) (micronaut-build, 2025-11-03)
- `c11a10d11f30` Update common files (#525) (micronaut-build, 2025-10-23)
- `c507a252162a` update io.micronaut.build.shared.settings to 8.0.0-M5 (#526) (araysse, 2025-10-23)
- `0fac83ba96cf` Update common files (#523) (micronaut-build, 2025-10-17)
- `622478da4f05` Micronaut Gradle Build Plugin 8.0.0-M4 (Sergio del Amo, 2025-10-15)
- `0264e7800f20` gradle 9.1 (Sergio del Amo, 2025-10-15)
- `6f4e1d2a423c` projectVersion=6.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-10-15)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` acme/build.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
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
- `M` acme/src/main/java/io/micronaut/acme/AcmeConfiguration.java
- `M` acme/src/main/java/io/micronaut/acme/events/CertificateEvent.java
- `M` acme/src/main/java/io/micronaut/acme/services/AcmeService.java
- `M` acme/src/main/java/io/micronaut/acme/ssl/AcmeSSLContextBuilder.java
- `M` config/checkstyle/checkstyle.xml

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` acme/src/test/groovy/io/micronaut/acme/AcmeBaseSpec.groovy
- `M` acme/src/test/groovy/io/micronaut/acme/AcmeCertRefresherMultiDomainsTaskSpec.groovy
- `M` acme/src/test/groovy/io/micronaut/acme/AcmeCertRefresherTaskSetsTimeoutSpec.groovy
- `M` acme/src/test/groovy/io/micronaut/acme/AcmeCertRefresherTaskSpec.groovy
- `M` acme/src/test/groovy/io/micronaut/acme/AcmeCertRefresherTaskUnitSpec.groovy
- `M` acme/src/test/groovy/io/micronaut/acme/AcmeCertRefresherTaskWithClasspathKeysSpec.groovy
- `M` acme/src/test/groovy/io/micronaut/acme/AcmeCertRefresherTaskWithFileKeysSpec.groovy
- `M` acme/src/test/groovy/io/micronaut/acme/AcmeCertWildcardRefresherTaskSpec.groovy
- `M` acme/src/test/groovy/io/micronaut/acme/challenge/http/endpoint/WellKnownTokenControllerSpec.groovy
- `M` acme/src/test/groovy/io/micronaut/acme/challenges/AcmeCertRefresherTaskDns01ChallengeSpec.groovy
- `M` acme/src/test/groovy/io/micronaut/acme/challenges/AcmeCertRefresherTaskHttp01ChallengeSpec.groovy
- `M` acme/src/test/groovy/io/micronaut/acme/challenges/AcmeCertRefresherTaskTlsApln01ChallengeSpec.groovy

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

