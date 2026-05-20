• Compared in release direction mn4 -> mn5.

  Full report: micronaut-session-mn4-to-mn5-comparison.md:1

  Scope:

  - Previous: mn4/micronaut-session, branch 4.8.x, commit 22aa84b4c482, clean
  - Current: mn5/micronaut-session, branch 5.0.x, commit acf443e2da0e, clean
  - Delta: 67 commit candidates, 63 changed files

  Release-note draft:

  ## Micronaut Session 5.0

  ### Breaking Changes

  - `HttpSessionFilter` is now a method-based `@ServerFilter` and no longer implements `HttpServerFilter`. Code that depends on `HttpSessionFilter` being assignable to `HttpServerFilter`, or that calls `doFilter`, must migrate
  to the new filter-method API.

  ### Fixes

  - Fixed `HttpSessionFilter` so it applies correctly when the server uses a custom context path.
  - Fixed in-memory session event publishing so concrete session event listeners and `@EventListener` methods receive `SessionCreatedEvent` and related session events.

  ### Compatibility

  - Updated for the Micronaut 5 baseline.
  - Replaced Micronaut nullability annotations with JSpecify annotations across session APIs and docs examples.

  ### Review Candidate

  - `InMemorySessionStore` now injects typed `ApplicationEventPublisher` instances for each concrete session event type. Direct constructor calls may need updating.

  Important dependency/tooling changes:

  - Project version: 4.8.1-SNAPSHOT -> 5.0.0-SNAPSHOT
  - Micronaut Core: 4.10.3 -> 5.0.0-RC2
  - Micronaut Cache: 5.3.0 -> 6.0.0-M3
  - Micronaut Serialization: 2.15.5 -> 3.0.0-RC2
  - Micronaut Logging: 1.7.0 -> 2.0.0-M2
  - Gradle wrapper: 8.14.3 -> 9.5.0
  - GraalVM native Gradle plugin: 0.10.6 -> 1.1.0

  Tests were not run; this was a static repository comparison.


# Release Note Comparison

Generated: 2026-05-07 08:00 UTC
Comparison: `mn4` -> `mn5`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-session` | `4.8.x` | `22aa84b4c482` | `git@github.com:micronaut-projects/micronaut-session.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-session` | `5.0.x` | `acf443e2da0e` | `git@github.com:micronaut-projects/micronaut-session.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-session`
- Commit candidates found: 67
- File changes listed: 63
- Version values listed: 13
- File status counts: A=21, M=42

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `4.8.1-SNAPSHOT` | `5.0.0-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.kotlin-test` | `org.jetbrains.kotlin:kotlin-test (version.ref=kotlin)` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-cache` | `io.micronaut.cache:micronaut-cache-bom:5.3.0` | `io.micronaut.cache:micronaut-cache-bom:6.0.0-M3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.15.5` | `io.micronaut.serde:micronaut-serde-bom:3.0.0-RC2` | `changed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.18` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.3` | `5.0.0-RC2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-cache` | `5.3.0` | `6.0.0-M3` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `2.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.0` | `2.0.0-M2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.15.5` | `3.0.0-RC2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.7.0` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.0` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `912fcb22fdd9` remove groovy included by Micronaut Build Gradle Plugin (Sergio del Amo, 2025-12-09)
- `33b073dd87e1` remove micronaut-test included by Micronaut Build Gradle Plugin (Sergio del Amo, 2025-12-09)
- `afb14dde028c` remove micronaut-docs included by Micronaut Build Gradle Plugin (Sergio del Amo, 2025-12-09)

### Fixes

- `1c7a38b3d9e4` fix: apply HttpSessionFilter under custom context path (#335) (Sergio del Amo, 2026-05-01)
- `78630fa7d9d8` fix(deps): update kotlin monorepo to v2.3.20 (#316) (renovate[bot], 2026-04-15)
- `a0322a32c531` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m6 (#320) (renovate[bot], 2026-04-06)
- `8c95a63cea55` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m20 (#313) (renovate[bot], 2026-04-06)
- `bcab379c24ce` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#298) (renovate[bot], 2025-12-09)
- `4f6fa9cdd378` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#302) (renovate[bot], 2025-12-09)
- `5c3ceb053312` fix(deps): update kotlin monorepo to v2.2.21 (#303) (renovate[bot], 2025-12-09)
- `528dee932636` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.6 (#294) (renovate[bot], 2025-10-17)

### Dependency Updates

- `d7246c35128e` Update Micronaut dependencies (#338) (renovate[bot], 2026-05-01)
- `6f7a8d6aba0c` Update dependency org.graalvm.buildtools.native:org.graalvm.buildtools.native.gradle.plugin to v1.1.0 (renovate[bot], 2026-04-27)
- `f3bacc605dfa` Merge pull request #336 from micronaut-projects/renovate/micronaut-dependencies (Graeme Rocher, 2026-04-26)
- `295b17c2280c` Update Micronaut dependencies (renovate[bot], 2026-04-24)
- `071e88bb9b08` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-04-17)
- `102bb49a6e17` Update dependency org.graalvm.buildtools.native:org.graalvm.buildtools.native.gradle.plugin to v1 (#327) (renovate[bot], 2026-04-15)
- `17b22a8cd935` chore(deps): update gradle to v9.4.1 (#321) (renovate[bot], 2026-04-15)
- `38c109335232` Update dependency org.graalvm.buildtools.native:org.graalvm.buildtools.native.gradle.plugin to v0.11.5 (#322) (renovate[bot], 2026-04-15)
- `08b456917252` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2025-12-09)
- `ffef0020f34c` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#296) (renovate[bot], 2025-12-09)
- `934d4689224f` chore(deps): update gradle to v9.2.1 (#301) (renovate[bot], 2025-12-09)
- `f88917e2e352` chore(deps): update gradle/actions action to v5 (#305) (renovate[bot], 2025-12-09)
- `71ea186c907f` chore(deps): update dependency org.graalvm.buildtools.native:org.graalvm.buildtools.native.gradle.plugin to v0.11.3 (#300) (renovate[bot], 2025-12-09)
- `41af558c2426` chore(deps): update github artifact actions (#304) (renovate[bot], 2025-12-09)
- `c237f1a09785` chore(deps): update softprops/action-gh-release action to v2.5.0 (#306) (renovate[bot], 2025-12-09)
- `3509d5f155f2` chore(deps): update mikepenz/action-junit-report action to v6 (#307) (renovate[bot], 2025-12-09)
- `bd69b103b6b7` chore(deps): update stefanzweifel/git-auto-commit-action action to v7 (#308) (renovate[bot], 2025-12-09)
- `7f6d99ccd0fa` chore(deps): update graalvm/setup-graalvm action to v1.4.4 (#299) (renovate[bot], 2025-12-09)
- `805fef6403cd` chore(deps): update actions/checkout action to v6 (#309) (renovate[bot], 2025-12-09)

### Documentation

- `9071d434bfaf` Docs: update micronaut-docs to 3.0.0 (#292) (issam liqali, 2025-10-14)

### Internal

- `7eb3ba973999` test: use platform.launcher (Sergio del Amo, 2025-12-09)
- `09dd25f96121` test: use junit-jupiter-engine from mnTest (Sergio del Amo, 2025-12-09)
- `24ebd23291b0` ci: projectVersion=5.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-10-13)

### Review Candidates

- `acf443e2da0e` micronaut-serde = "3.0.0-RC2" (Sergio del Amo, 2026-05-07)
- `621ca264be3a` micronaut = "5.0.0-RC2" (Sergio del Amo, 2026-05-07)
- `00c3583ac62f` Update common files (#341) (micronaut-build, 2026-05-07)
- `b57471d375e4` Update Gradle to v9.5.0 (#340) (renovate[bot], 2026-05-01)
- `cd56ab08a9b7` Merge pull request #337 from micronaut-projects/renovate/org.graalvm.buildtools.native-org.graalvm.buildtools.native.gradle.plugin-1.x (Graeme Rocher, 2026-05-01)
- `2dc36dbed5f0` Merge pull request #339 from micronaut-projects/sync-files-5.0.x (Graeme Rocher, 2026-05-01)
- `52f9b4dcc23e` Update common files (micronaut-build, 2026-04-30)
- `2978c4b7cc70` Update actions/upload-artifact digest to 043fb46 (#334) (renovate[bot], 2026-04-24)
- `ba46a499b720` Update common files (#333) (micronaut-build, 2026-04-24)
- `b8aa3a19d749` Rewrite Session Filter to use request/response filter methods (#330) (Sergio del Amo, 2026-04-24)
- `7cf6c8d68447` [skip ci] Release v5.0.0-M2 (micronaut-build, 2026-04-17)
- `141a7ca4f4a4` micronaut = "5.0.0-M22" (Sergio del Amo, 2026-04-17)
- `638e61a8f116` Fix session event listener registration (#329) (Sergio del Amo, 2026-04-17)
- `8cbf84bfbccf` Update actions/cache digest to 27d5ce7 (#332) (renovate[bot], 2026-04-17)
- `47286b051f4f` Use micronaut kotlin plugin (#328) (Issam Liqali, 2026-04-15)
- `1520c62b6fcf` micronaut-logging = "2.0.0-M2" (Sergio del Amo, 2026-04-15)
- `a897f023feb4` micronaut-cache = "6.0.0-M2" (Sergio del Amo, 2026-04-15)
- `fb436fae5dc0` Update common files (#324) (micronaut-build, 2026-04-15)
- `80e4012baff2` Update softprops/action-gh-release action to v2.6.2 (#325) (renovate[bot], 2026-04-15)
- `a50135638f46` Update gradle/actions action to v6 (#326) (renovate[bot], 2026-04-15)
- `a5bad6e1f91f` Update common files (#312) (micronaut-build, 2026-03-12)
- `a05ff34b6359` Update to micronaut core M16 (#323) (Issam Liqali, 2026-03-12)
- `d459bd67adbf` [skip ci] Release v5.0.0-M1 (micronaut-build, 2025-12-09)
- `864a38bb6392` fix spock (Sergio del Amo, 2025-12-09)
- `bfabc0a0ed1f` target 21 (Sergio del Amo, 2025-12-09)
- `ceabc3c8a1b5` use jspecify nullability annotations (Sergio del Amo, 2025-12-09)
- `e69c123c17df` micronaut-serde = "3.0.0-M1" (Sergio del Amo, 2025-12-09)
- `42c6fbfba64e` micronaut = "5.0.0-M2" (Sergio del Amo, 2025-12-09)
- `4aef2e74f95b` Update common files (#295) (micronaut-build, 2025-12-09)
- `f66ebae0a8fb` [WIP] Replace Micronaut nullability annotations with JSpecify (#311) (Copilot, 2025-12-02)
- `26802ec2c332` Update common files (#293) (micronaut-build, 2025-10-16)
- `6e6d2d00e151` settings 8.0.0-M4 (Sergio del Amo, 2025-10-13)
- `f93dd55e18b1` gradle 9.1 (Sergio del Amo, 2025-10-13)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` .github/workflows/update-gradle-wrapper.yml
- `M` buildSrc/build.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.session-examples.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` session/build.gradle.kts
- `M` settings.gradle
- `M` test-suite-graal/build.gradle

### Documentation

- `A` .agents/skills/docs/SKILL.md
- `A` .agents/skills/docs/references/control-panel-patterns.md
- `A` .agents/skills/docs/references/micronaut-docs-providers.md
- `M` .github/workflows/release.yml
- `M` docs-examples/example-java/build.gradle
- `M` docs-examples/example-java/src/test/java/io/micronaut/docs/session/ShoppingController.java
- `M` docs-examples/example-kotlin/build.gradle
- `M` docs-examples/example-kotlin/src/test/kotlin/io/micronaut/docs/session/ShoppingControllerTest.kt
- `M` session/src/test/groovy/io/micronaut/session/docs/ShoppingController.java
- `A` src/main/docs/guide/breaks.adoc
- `M` src/main/docs/guide/sessions/sessionFilter.adoc
- `M` src/main/docs/guide/toc.yml

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
- `M` session/src/main/java/io/micronaut/session/InMemorySession.java
- `M` session/src/main/java/io/micronaut/session/InMemorySessionStore.java
- `M` session/src/main/java/io/micronaut/session/Session.java
- `M` session/src/main/java/io/micronaut/session/SessionConfiguration.java
- `M` session/src/main/java/io/micronaut/session/http/CookieHttpSessionIdGenerator.java
- `M` session/src/main/java/io/micronaut/session/http/HttpSessionFilter.java
- `M` session/src/main/java/io/micronaut/session/http/HttpSessionFilterConfiguration.java
- `M` session/src/main/java/io/micronaut/session/http/HttpSessionFilterConfigurationProperties.java
- `M` session/src/main/java/io/micronaut/session/http/SessionLocaleResolver.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` session/src/test/groovy/io/micronaut/session/http/SessionBindingSpec.groovy
- `A` session/src/test/java/io/micronaut/session/HttpSessionFilterApiTest.java
- `A` session/src/test/java/io/micronaut/session/HttpSessionFilterContextPathTest.java
- `A` session/src/test/java/io/micronaut/session/SessionEventListenerRegistrationTest.java

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

