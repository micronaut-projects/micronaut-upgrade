Compared micronaut-graal-languages as mn4 → mn5.

  Scope

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-graal-languages, branch 1.3.x, SHA c46ac3fd1191
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-graal-languages, branch 2.0.x, SHA aca39b219070
  - Same remote, both clean: git@github.com:micronaut-projects/micronaut-graal-languages.git
  - Report: /private/tmp/micronaut-graal-languages-1.3-to-2.0-comparison.md

  Key Findings

  - Major line move: projectVersion 1.3.0-SNAPSHOT → 2.0.1-SNAPSHOT.
  - Platform/build upgrade: Micronaut 4.10.3 → 5.0.0, Gradle wrapper 8.14.3 → 9.5.1, shared settings plugin
    7.6.4 → 8.0.0-M18, and .sdkmanrc adds java=25.0.1-graal.
  - GraalPy upgraded 24.2.2 → 25.0.3; python-embedding is now separately versioned at 25.0.3.
  - GraalPy API adaptation: imports moved from org.graalvm.python.embedding.utils.GraalPyResources to
    org.graalvm.python.embedding.GraalPyResources.
  - Micronaut Serde 3.0.0-RC3 was added for the test suite, with a new nested @Serdeable record regression
    test.
  - Bouncy Castle bcpkix-jdk18on constraint changed 1.82 → 1.84 due older-version security vulnerabilities.
  - Build metadata cleanup: root project renamed to micronaut-graal-languages-parent, micronaut-test, groovy,
    and micronaut-docs catalog entries were removed, and graalpy now sets a descriptor parentModuleId.
  - CI/common files moved to Java 25/GraalVM, pinned newer actions, and added OSV/CycloneDX vulnerability
    audit scripts/workflow.

  Diff size: 56 files changed, 3751 insertions(+), 161 deletions(-).

  I did not run tests; this was a folder comparison and targeted source/build-diff review only.



# Release Note Comparison

Generated: 2026-05-19 13:43 UTC
Comparison: `1.3.x` -> `2.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-graal-languages` | `1.3.x` | `c46ac3fd1191` | `git@github.com:micronaut-projects/micronaut-graal-languages.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-graal-languages` | `2.0.x` | `aca39b219070` | `git@github.com:micronaut-projects/micronaut-graal-languages.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-graal-languages`
- Commit candidates found: 76
- File changes listed: 56
- Version values listed: 11
- File status counts: A=26, M=30

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `1.3.0-SNAPSHOT` | `2.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test` | `io.micronaut.test:micronaut-test-bom:4.9.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.22` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.managed-graalpy` | `24.2.2` | `25.0.3` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-graalpy-embedding` | `not present` | `25.0.3` | `added` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.3` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `2.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `not present` | `3.0.0-RC3` | `added` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.9.0` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `c54272fa1899` remove empty depdendencies block (Sergio del Amo, 2025-12-19)
- `b331251d79c5` remove groovy supplied by MN Build Plugin (Sergio del Amo, 2025-12-19)
- `2a9c4b81e8ac` remove micronaut-docs (Sergio del Amo, 2025-12-19)

### Features

- `0e7d910ecaa7` Add serde regression test (Álvaro Sánchez-Mariscal, 2026-05-14)

### Fixes

- `0e6eb1948ab6` fix(deps): update dependency org.graalvm.python:python to v25.0.3 (#138) (renovate[bot], 2026-05-08)
- `663a6c75623c` fix(deps): update micronaut dependencies (renovate[bot], 2026-04-30)
- `e255f0eed547` fix(deps): update dependency org.bouncycastle:bcpkix-jdk18on to v1.84 (renovate[bot], 2026-04-21)
- `b58f5cdb28ff` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m22 (#135) (renovate[bot], 2026-04-15)
- `1f74c80451a9` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m19 (#131) (renovate[bot], 2026-04-02)
- `73c4524645c8` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m16 (#125) (renovate[bot], 2026-03-13)
- `013d1e13455c` fix(deps): update managed.graalpy to v25.0.2 (#122) (renovate[bot], 2026-02-16)
- `128777ef4658` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m10 (#120) (renovate[bot], 2026-02-16)
- `4c8571b763f3` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.12 (#111) (renovate[bot], 2025-12-19)
- `73d7571f642b` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#104) (renovate[bot], 2025-12-10)
- `f6a194aea4a4` fix(deps): update managed.graalpy to v25 (#100) (renovate[bot], 2025-12-10)
- `a950791fdbfb` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.8 (#91) (renovate[bot], 2025-11-03)
- `c3ae0d3fcab3` fix(deps): update dependency io.micronaut.test:micronaut-test-bom to v4.10.2 (#93) (renovate[bot], 2025-11-03)
- `5065d0d21008` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.6 (#85) (renovate[bot], 2025-10-17)

### Dependency Updates

- `288e200235ee` chore: Bump version to 2.0.1-SNAPSHOT (micronaut-build, 2026-05-14)
- `06be81f7c5aa` chore: Bump version to 2.0.0-SNAPSHOT (micronaut-build, 2026-05-11)
- `97fbbb2375e0` chore: Bump version to 2.0.0-SNAPSHOT (micronaut-build, 2026-05-08)
- `98668c644acf` chore(deps): update gradle to v9.5.0 (#128) (renovate[bot], 2026-05-06)
- `a3211485f52a` Merge pull request #139 from micronaut-projects/renovate/micronaut-dependencies (Graeme Rocher, 2026-05-01)
- `cbc82d57af4c` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#123) (renovate[bot], 2026-02-17)
- `c8346dccc281` chore: Bump version to 2.0.0-SNAPSHOT (micronaut-build, 2026-02-16)
- `6a0b00ec2839` chore(deps): update peter-evans/create-pull-request action to v8 (#117) (renovate[bot], 2026-02-16)
- `11829c5d7532` chore(deps): update graalvm/setup-graalvm action to v1.4.5 (#118) (renovate[bot], 2026-02-16)
- `62d95539e90a` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m16 (#119) (renovate[bot], 2026-02-16)
- `8fd1dad12ec3` chore(deps): update gradle to v9.3.1 (#121) (renovate[bot], 2026-02-16)
- `e03f818c2791` build.shared.settings' version '8.0.0-M13' (Sergio del Amo, 2025-12-19)
- `1fc923650b63` chore(deps): update actions/cache action to v5 (#113) (renovate[bot], 2025-12-19)
- `5cb5a431fd87` chore(deps): update graalvm/setup-graalvm action to v1.4.4 (#105) (renovate[bot], 2025-12-10)
- `be4719dd3775` chore(deps): update actions/checkout action to v6 (#102) (renovate[bot], 2025-12-10)
- `826a193ab12f` chore(deps): update gradle to v9.2.1 (#101) (renovate[bot], 2025-12-10)
- `f84ac57faafb` chore(deps): update stefanzweifel/git-auto-commit-action action to v7 (#99) (renovate[bot], 2025-12-10)
- `dbfda9d278a1` chore(deps): update softprops/action-gh-release action to v2.5.0 (#98) (renovate[bot], 2025-12-10)
- `ee6f730356b9` chore(deps): update mikepenz/action-junit-report action to v6 (#97) (renovate[bot], 2025-12-10)
- `77853e2b8015` chore(deps): update github artifact actions (#96) (renovate[bot], 2025-12-10)
- `876bd231f169` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#94) (renovate[bot], 2025-12-10)
- `58573230058f` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m8 (#89) (renovate[bot], 2025-11-03)
- `29ac8bbd8ed9` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#88) (renovate[bot], 2025-11-03)
- `0dc4a7da6a8c` chore(deps): update gradle to v9.2.0 (#92) (renovate[bot], 2025-11-03)

### Documentation

- `8129fb3f0e95` Docs: update micronaut-docs to 3.0.0 (#83) (issam liqali, 2025-10-20)

### Internal

- `e371b101dcb3` build: Micronaut build plugin 8.0.0-M4 (Sergio del Amo, 2025-10-13)
- `c77fa2cd0be7` ci: projectVersion=2.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-10-13)

### Review Candidates

- `aca39b219070` Update common files (#149) (micronaut-build, 2026-05-19)
- `f714908b62c3` Merge pull request #148 from micronaut-projects/fix-147-serde-version-alignment (Álvaro Sánchez-Mariscal, 2026-05-15)
- `694cbc02415d` Update common files (#146) (micronaut-build, 2026-05-14)
- `5f970260712f` [skip ci] Release v2.0.0 (micronaut-build, 2026-05-14)
- `ec1fabad22ed` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `f4611c5a64d5` [skip ci] Release v2.0.0-RC2 (micronaut-build, 2026-05-11)
- `d3fbce7fbe98` Update libs.versions.toml (#145) (Sergio del Amo, 2026-05-11)
- `cc749c93444d` Update common files (#144) (micronaut-build, 2026-05-09)
- `c9e20e9970ec` [skip ci] Release v2.0.0-RC1 (micronaut-build, 2026-05-08)
- `f682661b7ca9` Update common files (#143) (micronaut-build, 2026-05-08)
- `93dd88fa7f88` Update common files (#142) (micronaut-build, 2026-05-07)
- `461ff2cee0cf` Update common files (#141) (micronaut-build, 2026-05-06)
- `2b5c90025db5` Merge pull request #106 from micronaut-projects/renovate/org.bouncycastle-bcpkix-jdk18on-1.x (Graeme Rocher, 2026-05-01)
- `f06779ff6362` Merge pull request #140 from micronaut-projects/sync-files-2.0.x (Graeme Rocher, 2026-05-01)
- `dea7f6eb19b5` Update common files (micronaut-build, 2026-04-30)
- `e8b30eca627f` Merge pull request #133 from micronaut-projects/sync-files-2.0.x (Graeme Rocher, 2026-04-26)
- `05d17ec12c0c` Update common files (micronaut-build, 2026-04-21)
- `e961773de543` Update common files (#127) (micronaut-build, 2026-03-13)
- `031664fe31e1` Update common files (#124) (micronaut-build, 2026-02-17)
- `42cadc9025ac` [skip ci] Release v2.0.0-M1 (micronaut-build, 2026-02-16)
- `8e35d36c4a02` Update common files (#116) (micronaut-build, 2026-02-16)
- `f608415f5c84` Update to Micronaut 5 (#114) (issam liqali, 2026-02-03)
- `0e2bccddaaab` micronaut-test supplied by MN build plugin (Sergio del Amo, 2025-12-19)
- `534719ac5c25` pkg: org.graalvm.python.embedding.GraalPyResources (Sergio del Amo, 2025-12-19)
- `37ce2b752f10` junit.platform.launcher (Sergio del Amo, 2025-12-19)
- `86a79a2f11da` Update common files (#95) (micronaut-build, 2025-12-10)
- `a75edf4afbbb` Micronaut 5 compatibility (#90) (issam liqali, 2025-11-03)
- `881e21449bab` Update common files (#87) (micronaut-build, 2025-11-03)
- `7afdd444f230` Update common files (#86) (micronaut-build, 2025-10-20)
- `2b27ee7d0319` Update common files (#84) (micronaut-build, 2025-10-17)
- `a1a2b38840fe` gradle 9.1 (Sergio del Amo, 2025-10-13)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` .github/workflows/update-gradle-wrapper.yml
- `M` buildSrc/build.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.graal-languages-base.gradle
- `M` graalpy/build.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` settings.gradle
- `M` test-suite-graalpy/build.gradle

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
- `M` .github/workflows/files-sync.yml
- `M` .github/workflows/graalvm-dev.yml
- `M` .github/workflows/publish-snapshot.yml
- `A` .github/workflows/sonatype.yml
- `M` .gitignore
- `A` .sdkmanrc
- `M` MAINTAINING.md
- `M` config/checkstyle/checkstyle.xml
- `M` graalpy/src/main/java/io/micronaut/graal/graalpy/DefaultGraalPyContextBuilderFactory.java
- `M` graalpy/src/main/java/io/micronaut/graal/graalpy/GraalPyContextBuilderFactory.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` test-suite-graalpy/src/test/java/io/micronaut/graal/graalpy/ExampleTest.java
- `A` test-suite-graalpy/src/test/java/io/micronaut/graal/graalpy/SentimentAnalysis.java
- `M` test-suite-graalpy/src/test/java/io/micronaut/graal/graalpy/TestContextFactory.java

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

