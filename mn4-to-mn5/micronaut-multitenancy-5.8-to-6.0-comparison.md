 Compared as mn4/5.8.x -> mn5/6.0.x based on branch metadata.

  Scope:

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-multitenancy, branch 5.8.x, commit
    eb9e1188b261d9345199a6d4a93971230cb24dd9
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-multitenancy, branch 6.0.x, commit
    a29c5d904b9d8342ad86d62fbe3225c279c10f6a
  - Both worktrees are clean and use the same remote.

  Full report: /private/tmp/micronaut-multitenancy-5.8-to-6.0-comparison.md:1

  Key findings:

  - 75 files changed: 26 added, 49 modified; 3,735 insertions, 214 deletions.
  - Main platform moves to Micronaut 5: projectVersion 5.8.1-SNAPSHOT -> 6.0.1-SNAPSHOT, micronaut 4.10.4 ->
    5.0.0.
  - Confirmed breaking change: deprecated no-arg SubdomainTenantResolver() was removed. The documented
    replacement is SubdomainTenantResolver(HttpHostResolver).
  - Most production source changes are nullability migration from io.micronaut.core.annotation.* to
    org.jspecify.annotations.*.
  - Dependency updates include Security 4.15.0 -> 5.0.0, Session 4.7.0 -> 5.0.0, Serde 2.15.5 -> 3.0.0, Reactor
    3.9.0 -> 4.0.0, Validation 4.11.0 -> 5.0.0, Guava 33.4.8-jre -> 33.6.0-jre, and public suffix list 2.2.0 ->
    2.2.4.
  - Build baseline changes: Gradle 8.14.3 -> 9.5.1, shared settings plugin 7.6.4 -> 8.0.0-M18, .sdkmanrc adds
    java=25.0.1-graal, CI matrix moves from Java 17/21 to Java 25.
  - Sonatype scan plugin wiring was removed from buildSrc; new OSV/CycloneDX vulnerability audit scripts and
    workflow were added.
  - Kotlin test suite build now uses Micronaut internal Kotlin build plugins instead of direct Kotlin Gradle
    plugins.

  I did not run tests; this was a folder comparison and targeted diff inspection.

# Release Note Comparison

Generated: 2026-05-19 09:24 UTC
Comparison: `5.8.x` -> `6.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-multitenancy` | `5.8.x` | `eb9e1188b261` | `git@github.com:micronaut-projects/micronaut-multitenancy.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-multitenancy` | `6.0.x` | `a29c5d904b9d` | `git@github.com:micronaut-projects/micronaut-multitenancy.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-multitenancy`
- Commit candidates found: 74
- File changes listed: 75
- Version values listed: 26
- File status counts: A=26, M=49

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `5.8.1-SNAPSHOT` | `6.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.gradle-kotlin` | `org.jetbrains.kotlin:kotlin-gradle-plugin:1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-reactor` | `io.micronaut.reactor:micronaut-reactor-bom:3.9.0` | `io.micronaut.reactor:micronaut-reactor-bom:4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-security` | `io.micronaut.security:micronaut-security-bom:4.15.0` | `io.micronaut.security:micronaut-security-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.15.5` | `io.micronaut.serde:micronaut-serde-bom:3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-session` | `io.micronaut.session:micronaut-session-bom:4.7.0` | `io.micronaut.session:micronaut-session-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-validation` | `io.micronaut.validation:micronaut-validation-bom:4.11.0` | `io.micronaut.validation:micronaut-validation-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.sonatype-scan` | `org.sonatype.gradle.plugins:scan-gradle-plugin:3.1.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.24` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.guava` | `33.4.8-jre` | `33.6.0-jre` | `changed` |
| `gradle/libs.versions.toml` | `versions.kotlin-gradle-plugin` | `1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.managed-publicsuffixlist` | `2.2.0` | `2.2.4` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.4` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-reactor` | `3.9.0` | `4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-security` | `4.15.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.15.5` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-session` | `4.7.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.7.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.11.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.sonatype-scan` | `3.1.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |
| `settings.gradle` | `plugin.io.micronaut.build.shared.settings` | `7.6.4` | `8.0.0-M18` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `aadbaf43c15d` Removed the Spock version force configuration from build (#484) (Issam Liqali, 2026-03-12)
- `d79a674eff62` remove kotlin version (Sergio del Amo, 2025-12-10)
- `027cecf1829d` remove groovy version (Sergio del Amo, 2025-12-10)
- `655f66792643` Remove deprecations for Micronaut Framework 5 and document breaking changes. (#288) (Dean Wette, 2024-03-18)

### Fixes

- `02f8631f2474` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m17 (#474) (renovate[bot], 2026-03-17)
- `74db9933f395` fix(deps): update dependency org.apache.commons:commons-lang3 to v3.20.0 (#464) (renovate[bot], 2025-12-10)
- `97c52f1cb22d` fix(deps): update dependency com.google.guava:guava to v33.5.0-jre (#460) (renovate[bot], 2025-12-10)
- `cbff0d0538cc` fix(deps): update dependency org.jetbrains.kotlin:kotlin-gradle-plugin to v2.2.21 (#457) (renovate[bot], 2025-12-10)
- `ab9d1b84ab8c` fix(deps): update dependency io.micronaut.session:micronaut-session-bom to v4.8.0 (#462) (renovate[bot], 2025-12-10)
- `f33b881918c3` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#461) (renovate[bot], 2025-12-10)
- `346e98263e4a` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.12.0 (#463) (renovate[bot], 2025-12-10)
- `7a2b301561ba` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#465) (renovate[bot], 2025-12-10)
- `4aaddded7c19` fix(deps): update dependency io.micronaut.security:micronaut-security-bom to v4.16.0 (#468) (renovate[bot], 2025-12-10)
- `b794557c22f8` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.8 (#453) (renovate[bot], 2025-11-03)
- `d56429e58893` fix(deps): update dependency io.micronaut.reactor:micronaut-reactor-bom to v3.9.1 (#454) (renovate[bot], 2025-11-03)
- `3d5fd24f9403` fix(deps): update dependency io.micronaut.reactor:micronaut-reactor-bom to v3.3.0 (#303) (renovate[bot], 2024-04-11)
- `d65dda21e3ed` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.4.1 (#304) (renovate[bot], 2024-04-11)
- `e121af5678bc` fix(deps): update dependency io.micronaut.security:micronaut-security-bom to v4.7.0 (#305) (renovate[bot], 2024-04-11)
- `707daf80c459` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.4.0 (#300) (renovate[bot], 2024-04-01)
- `9d748dbee52e` fix(deps): update dependency io.micronaut.security:micronaut-security-bom to v4.6.9 (#293) (renovate[bot], 2024-04-01)
- `43aff9ea32d9` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.3.12 (#296) (renovate[bot], 2024-03-27)
- `5ac2f164386b` fix(deps): update dependency com.google.guava:guava to v33.1.0-jre (#289) (renovate[bot], 2024-03-18)

### Security

- `a29c5d904b9d` update security and session (Sergio del Amo, 2026-05-18)

### Dependency Updates

- `3f6ab575c696` chore: Bump version to 6.0.1-SNAPSHOT (micronaut-build, 2026-05-14)
- `f30a5951f907` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2026-05-06)
- `96a9f73812b7` Update Micronaut version to 5.0.0-RC2 (Sergio del Amo, 2026-05-06)
- `cb48a3704548` Update dependency de.malkusch.whois-server-list:public-suffix-list to v2.2.4 (renovate[bot], 2026-05-01)
- `e991681bc790` Merge pull request #492 from micronaut-projects/renovate/micronaut-dependencies (Graeme Rocher, 2026-05-01)
- `02be3f5861d9` Update Micronaut dependencies (renovate[bot], 2026-04-30)
- `025a11b48c22` Update dependency io.micronaut:micronaut-core-bom to v5.0.0-M22 (#488) (renovate[bot], 2026-04-17)
- `5400c8332316` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2025-12-10)
- `3fd1651a2f20` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#455) (renovate[bot], 2025-12-10)
- `ca475a0ac4ba` chore(deps): update gradle to v9.2.1 (#459) (renovate[bot], 2025-12-10)
- `9e640e64234b` chore(deps): update softprops/action-gh-release action to v2.5.0 (#458) (renovate[bot], 2025-12-10)
- `e6ce9cd0e5ee` chore(deps): update actions/checkout action to v6 (#466) (renovate[bot], 2025-12-10)
- `b48f343287ad` chore(deps): update github artifact actions (#471) (renovate[bot], 2025-12-10)
- `0a96e5a2ef3a` chore(deps): update graalvm/setup-graalvm action to v1.4.4 (#467) (renovate[bot], 2025-12-10)
- `d752620e7778` chore(deps): update mikepenz/action-junit-report action to v6 (#472) (renovate[bot], 2025-12-10)
- `432aa137193c` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m8 (#450) (renovate[bot], 2025-11-03)
- `bcf5b54134ab` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#452) (renovate[bot], 2025-11-03)
- `bb17cc3dc6ad` chore(deps): update gradle/gradle-build-action action to v3.2.1 (#302) (renovate[bot], 2024-04-11)
- `c511c46fba8c` chore(deps): update dependency gradle to v8.7 (#297) (renovate[bot], 2024-03-27)
- `e6126089e42b` chore(deps): update slsa-framework/slsa-github-generator action to v1.10.0 (#298) (renovate[bot], 2024-03-27)

### Review Candidates

- `a2887975f0c8` [skip ci] Release v6.0.0 (micronaut-build, 2026-05-14)
- `92b8b1280a0f` update versions (Sergio del Amo, 2026-05-14)
- `9580554139b0` Update common files (#496) (micronaut-build, 2026-05-14)
- `bd604455def0` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `bed456bd683a` Update common files (#495) (micronaut-build, 2026-05-09)
- `c31c1d614b51` [skip ci] Release v6.0.0-RC1 (micronaut-build, 2026-05-06)
- `92b5c8d9949f` Update common files (#494) (micronaut-build, 2026-05-06)
- `02013f213b74` Merge pull request #477 from micronaut-projects/renovate/managed.publicsuffixlist (Graeme Rocher, 2026-05-01)
- `cff63661961c` Merge pull request #483 from micronaut-projects/renovate/gradle-9.x (Graeme Rocher, 2026-05-01)
- `1e8bdf4d415c` Merge pull request #493 from micronaut-projects/sync-files-6.0.x (Graeme Rocher, 2026-05-01)
- `3ebf0311c62d` Update common files (micronaut-build, 2026-04-30)
- `d11e5093db62` Update Gradle to v9.5.0 (renovate[bot], 2026-04-28)
- `a44e61b8c0d0` Merge pull request #486 from micronaut-projects/sync-files-6.0.x (Graeme Rocher, 2026-04-26)
- `5a852d9e5ad9` Update common files (micronaut-build, 2026-04-21)
- `78a270c56314` update to micronaut 5.0.0-M23 (#491) (Issam Liqali, 2026-04-21)
- `ab665bb9718b` Update common files (#473) (micronaut-build, 2026-03-17)
- `7f84c2500920` [skip ci] Release v6.0.0-M1 (micronaut-build, 2025-12-10)
- `dc8022fb9d7b` fix spock (Sergio del Amo, 2025-12-10)
- `01f7ac382637` jspecify nullability annotations (Sergio del Amo, 2025-12-10)
- `41c61d96ce93` micronaut-validation = "5.0.0-M1" (Sergio del Amo, 2025-12-10)
- `6e96233fd535` micronaut-serde = "3.0.0-M1" (Sergio del Amo, 2025-12-10)
- `855ff6a0a652` micronaut = "5.0.0-M2" (Sergio del Amo, 2025-12-10)
- `8b9ef874ada4` Update common files (#456) (micronaut-build, 2025-12-10)
- `893b591442fd` Update common files (#449) (micronaut-build, 2025-11-03)
- `bbea8dd927a8` Micronaut 5 compatibility and release prep (#448) (issam liqali, 2025-10-17)
- `fa1c3f2c74f7` Update common files (#446) (micronaut-build, 2025-10-16)
- `982fdd63f46c` Micronaut gradle build plugin 8.0.0-M4 (Sergio del Amo, 2025-10-14)
- `676f52440eba` gradle 9.1 (Sergio del Amo, 2025-10-14)
- `0071394c1558` Merge branch '5.8.x' into 6.0.x (Sergio del Amo, 2025-10-14)
- `3984b3ee59fa` Merge branch '5.3.x' into 6.0.x (Sergio del Amo, 2024-04-11)
- `e5d7e1b3204b` Update common files (#299) (micronaut-build, 2024-03-28)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` buildSrc/build.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.multitenancy-module.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` multitenancy/build.gradle.kts
- `M` settings.gradle
- `M` test-suite-groovy/build.gradle.kts
- `M` test-suite-http/build.gradle.kts
- `M` test-suite-kotlin/build.gradle.kts
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
- `A` src/main/docs/guide/breaks.adoc
- `M` src/main/docs/guide/toc.yml

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
- `M` config/accepted-api-changes.json
- `M` config/checkstyle/checkstyle.xml
- `M` multitenancy/src/main/java/io/micronaut/multitenancy/expression/TenantEvaluationContext.java
- `M` multitenancy/src/main/java/io/micronaut/multitenancy/filter/TenantResolverFilter.java
- `M` multitenancy/src/main/java/io/micronaut/multitenancy/filter/TenantResolverFilterConfiguration.java
- `M` multitenancy/src/main/java/io/micronaut/multitenancy/tenantresolver/AbstractSubdomainTenantResolver.java
- `M` multitenancy/src/main/java/io/micronaut/multitenancy/tenantresolver/CookieTenantResolver.java
- `M` multitenancy/src/main/java/io/micronaut/multitenancy/tenantresolver/FixedTenantResolver.java
- `M` multitenancy/src/main/java/io/micronaut/multitenancy/tenantresolver/HttpHeaderTenantResolver.java
- `M` multitenancy/src/main/java/io/micronaut/multitenancy/tenantresolver/HttpRequestTenantResolver.java
- `M` multitenancy/src/main/java/io/micronaut/multitenancy/tenantresolver/InternetDomainNameSubdomainTenantResolver.java
- `M` multitenancy/src/main/java/io/micronaut/multitenancy/tenantresolver/PrincipalTenantResolver.java
- `M` multitenancy/src/main/java/io/micronaut/multitenancy/tenantresolver/PublicSuffixListSubdomainTenantResolver.java
- `M` multitenancy/src/main/java/io/micronaut/multitenancy/tenantresolver/SessionTenantResolver.java
- `M` multitenancy/src/main/java/io/micronaut/multitenancy/tenantresolver/SubdomainTenantResolver.java
- `M` multitenancy/src/main/java/io/micronaut/multitenancy/tenantresolver/SystemPropertyTenantResolver.java
- `M` multitenancy/src/main/java/io/micronaut/multitenancy/tenantresolver/TenantResolver.java
- `M` multitenancy/src/main/java/io/micronaut/multitenancy/writer/CookieTenantWriterConfigurationProperties.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` multitenancy/src/test/groovy/io/micronaut/multitenancy/expression/TenantEvaluationContextSpec.groovy
- `M` multitenancy/src/test/groovy/io/micronaut/multitenancy/tenantresolver/MockHttpHeaders.java
- `M` multitenancy/src/test/java/io/micronaut/multitenancy/filter/TenantResolverFilterPatternTest.java
- `M` multitenancy/src/test/java/io/micronaut/multitenancy/filter/TenantTypedRequestArgumentBinderNoBindingTest.java

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

