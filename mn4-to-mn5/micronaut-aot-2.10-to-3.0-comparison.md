Compared micronaut-aot as mn4 -> mn5.

  Scope

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-aot, branch 2.10.x, SHA 100946334d17
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-aot, branch 3.0.x, SHA dd132eb7210a
  - Same remote, both clean: git@github.com:micronaut-projects/micronaut-aot.git
  - Report: /private/tmp/micronaut-aot-2.10-to-3.0-comparison.md

  Key Findings

  - Version line moves 2.10.0-SNAPSHOT -> 3.0.1-SNAPSHOT.
  - Baseline updates include Micronaut 4.10.4 -> 5.0.0, Micronaut Picocli 5.8.0 -> 6.0.0, Gradle 8.14.3 ->
    9.5.1, settings plugin 7.6.4 -> 8.0.0-M18, and new .sdkmanrc Java 25.0.1-graal.
  - New opt-in AOT diagnostics report support: config keys under micronaut.aot.report.*, CLI flags
    --report, --report-output, --report-format, JSON/HTML output, and redacted option values.
  - Breaking change: static service loading optimization was removed, including JIT/native static service
    loader generators, tests, and service registration entries.
  - Source generator loading now records enabled/disabled selections and disabled reasons, feeding
    diagnostics reporting.
  - CLI now configures the SLF4J provider to Logback when system properties are not already set.
  - Fixes include Logback AOT conversion skipping cleanly when no Logback config is present, and YAML
    property-source generation compatibility for the deprecated yaml.to.java.config path.
  - Docs added/updated for diagnostics reports, standard optimizers, quick start module naming, optimizer
    source layout, service loader registration, and current APIs.

  Diff size: 93 files changed, 5208 insertions(+), 1291 deletions(-).

  I did not run tests; this was a folder comparison and targeted source/build-diff review only.

# Release Note Comparison

Generated: 2026-05-19 15:12 UTC
Comparison: `2.10.x` -> `3.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-aot` | `2.10.x` | `100946334d17` | `git@github.com:micronaut-projects/micronaut-aot.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-aot` | `3.0.x` | `dd132eb7210a` | `git@github.com:micronaut-projects/micronaut-aot.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-aot`
- Commit candidates found: 55
- File changes listed: 93
- Version values listed: 13
- File status counts: A=33, D=5, M=55

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `groovyVersion` | `4.0.13` | `4.0.13` | `unchanged` |
| `gradle.properties` | `projectVersion` | `2.10.0-SNAPSHOT` | `3.0.1-SNAPSHOT` | `changed` |
| `gradle.properties` | `spockVersion` | `2.3-groovy-4.0` | `2.3-groovy-4.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.javapoet` | `com.squareup:javapoet:1.13.0` | `com.squareup:javapoet:1.13.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.micronaut-picocli` | `io.micronaut.picocli:micronaut-picocli-bom:5.8.0` | `io.micronaut.picocli:micronaut-picocli-bom:6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.javapoet` | `1.13.0` | `1.13.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.4` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-picocli` | `5.8.0` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.9.0` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |
| `settings.gradle` | `plugin.io.micronaut.build.shared.settings` | `7.6.4` | `8.0.0-M18` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `2f6e146e0343` Remove service loading optimization (#423) (Cédric Champeau, 2026-02-16)

### Features

- `b2cd6b496b15` Add AOT diagnostics report (#451) (Álvaro Sánchez-Mariscal, 2026-05-12)
- `512e287ddd6c` Add root agent guidance (#440) (Álvaro Sánchez-Mariscal, 2026-04-30)

### Fixes

- `30fc8e754681` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m17 (#425) (renovate[bot], 2026-03-25)
- `86b22328479d` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m10 (#414) (renovate[bot], 2026-02-13)
- `79b597a9f04d` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.8 (#403) (renovate[bot], 2025-11-04)

### Dependency Updates

- `dae96f400a82` chore: Bump version to 3.0.1-SNAPSHOT (micronaut-build, 2026-05-14)
- `07de67455192` chore: Bump version to 3.0.0-SNAPSHOT (micronaut-build, 2026-05-08)
- `a31cd2f22ab2` Update dependency io.micronaut:micronaut-core-bom to v5.0.0-RC1 (#445) (renovate[bot], 2026-05-04)
- `b6fc974a95fb` Update dependency io.micronaut:micronaut-core-bom to v5.0.0-M26 (#443) (renovate[bot], 2026-05-02)
- `8939145f6a8f` Fix logback AOT conversion without logback config (#437) (Álvaro Sánchez-Mariscal, 2026-04-29)
- `17e07204f37b` Update Micronaut dependencies (#434) (renovate[bot], 2026-04-29)
- `c6fe17191f0b` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#424) (renovate[bot], 2026-03-25)
- `78af69c23772` chore: Bump version to 3.0.0-SNAPSHOT (micronaut-build, 2026-02-16)
- `39a7a48f6e88` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m16 (#416) (renovate[bot], 2026-02-13)
- `e5b3f20043ac` chore: Bump version to 3.0.0-SNAPSHOT (micronaut-build, 2026-02-04)
- `33f85e07334e` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#401) (renovate[bot], 2025-11-04)
- `777b04995ae9` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m9 (#402) (renovate[bot], 2025-11-04)

### Documentation

- `cc3b1c37e290` docs: check contributing guidelines before PR handoff (#453) (Álvaro Sánchez-Mariscal, 2026-05-10)
- `42bb9d1250c1` docs: clarify AOT code generator source layout (#436) (Álvaro Sánchez-Mariscal, 2026-04-29)

### Internal

- `7bc2e2575589` ci: projectVersion=3.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-10-15)

### Review Candidates

- `dd132eb7210a` Update common files (#456) (micronaut-build, 2026-05-19)
- `999387e94e67` Fix yaml generation compatability (#441) (Álvaro Sánchez-Mariscal, 2026-05-18)
- `c44dc5053e0f` [skip ci] Release v3.0.0 (micronaut-build, 2026-05-14)
- `40d5070b0e23` micronaut-picocli = "6.0.0" (Sergio del Amo, 2026-05-14)
- `f7f87ecf3d5d` Update common files (#454) (micronaut-build, 2026-05-14)
- `ba6708d76d61` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `2a988d0d4f57` Update common files (#452) (micronaut-build, 2026-05-09)
- `1401aa6977fa` [skip ci] Release v3.0.0-RC1 (micronaut-build, 2026-05-08)
- `d986abdbaa5d` Update actions/checkout action to v6 (#411) (renovate[bot], 2026-05-08)
- `c9d3215404bc` update latest versions (Sergio del Amo, 2026-05-08)
- `e7100eb19663` Update stefanzweifel/git-auto-commit-action action to v7 (#413) (renovate[bot], 2026-05-08)
- `972a15bd3118` Update gradle/actions action to v6 (#430) (renovate[bot], 2026-05-08)
- `7eef06246c04` [aot] Update common files for branch 3.0.x (#450) (micronaut-build, 2026-05-08)
- `dd76724883b0` [aot] Update common files for branch 3.0.x (#448) (micronaut-build, 2026-05-07)
- `4b93f8c11cb7` Fix AOT optimizer guide example (#449) (Álvaro Sánchez-Mariscal, 2026-05-07)
- `e8f4df69982d` [aot] Update common files for branch 3.0.x (#447) (micronaut-build, 2026-05-06)
- `53a39fda381e` [aot] Update common files for branch 3.0.x (#446) (micronaut-build, 2026-05-05)
- `f33846feb3fb` [aot] Update common files for branch 3.0.x (#444) (micronaut-build, 2026-05-04)
- `45dcacdb69af` Document standard AOT optimizers (#435) (Álvaro Sánchez-Mariscal, 2026-05-03)
- `c54f7bd85eb0` [aot] Update common files for branch 3.0.x (#442) (micronaut-build, 2026-04-30)
- `e6cb0bd4f1ac` Configure SLF4J provider for AOT CLI (#438) (Álvaro Sánchez-Mariscal, 2026-04-29)
- `ab35e2b2e1ed` [aot] Update common files for branch 3.0.x (#439) (micronaut-build, 2026-04-29)
- `22686506dda2` Merge pull request #427 from micronaut-projects/sync-files-3.0.x (Graeme Rocher, 2026-04-26)
- `7b660e86708c` Update common files (micronaut-build, 2026-04-21)
- `0ed246ec408b` [skip ci] Release v3.0.0-M2 (micronaut-build, 2026-02-16)
- `4610704a2130` Update common files (#422) (micronaut-build, 2026-02-13)
- `bf9ac30c096b` [skip ci] Release v3.0.0-M1 (micronaut-build, 2026-02-04)
- `93b656c14693` Update common files (#404) (micronaut-build, 2026-02-04)
- `09b4bc196c29` Update to micronaut 5 (#421) (issam liqali, 2026-02-04)
- `bdce142fc626` Replace Micronaut nullability annotations with JSpecify nullability annotations (#418) (Copilot, 2025-12-01)
- `1f2566d73b24` Update common files (#399) (micronaut-build, 2025-11-04)
- `1863f95ab4c2` Update common files (#397) (micronaut-build, 2025-10-17)
- `f613e0a4e91a` Micronaut Gradle build Plugin 8.0.0-M4 (Sergio del Amo, 2025-10-15)
- `2378d9aa3622` gradle 9.1 (Sergio del Amo, 2025-10-15)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` .github/workflows/update-gradle-wrapper.yml
- `M` build-logic/src/main/groovy/io.micronaut.build.internal.aot-project.gradle
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
- `A` src/main/docs/guide/diagnosticsReport.adoc
- `M` src/main/docs/guide/quickStart.adoc
- `A` src/main/docs/guide/standardOptimizers.adoc
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
- `A` AGENTS.md
- `M` CONTRIBUTING.md
- `M` MAINTAINING.md
- `M` aot-api/src/main/java/io/micronaut/aot/ConfigKeys.java
- `M` aot-api/src/main/java/io/micronaut/aot/MicronautAotOptimizer.java
- `M` aot-cli/src/main/java/io/micronaut/aot/cli/Main.java
- `M` aot-core/src/main/java/io/micronaut/aot/core/AOTCodeGenerator.java
- `M` aot-core/src/main/java/io/micronaut/aot/core/AOTContext.java
- `M` aot-core/src/main/java/io/micronaut/aot/core/Configuration.java
- `M` aot-core/src/main/java/io/micronaut/aot/core/codegen/AbstractSingleClassFileGenerator.java
- `M` aot-core/src/main/java/io/micronaut/aot/core/codegen/ApplicationContextConfigurerGenerator.java
- `M` aot-core/src/main/java/io/micronaut/aot/core/codegen/DelegatingSourceGenerationContext.java
- `M` aot-core/src/main/java/io/micronaut/aot/core/config/DefaultConfiguration.java
- `M` aot-core/src/main/java/io/micronaut/aot/core/config/SourceGeneratorLoader.java
- `A` aot-core/src/main/java/io/micronaut/aot/core/config/SourceGeneratorSelection.java
- `M` aot-core/src/main/java/io/micronaut/aot/core/context/ApplicationContextAnalyzer.java
- `M` aot-core/src/main/java/io/micronaut/aot/core/context/DefaultSourceGenerationContext.java
- `A` aot-core/src/main/java/io/micronaut/aot/core/report/AotDiagnosticReportWriter.java
- `D` aot-std-optimizers/src/main/java/io/micronaut/aot/std/sourcegen/AbstractStaticServiceLoaderSourceGenerator.java
- `M` aot-std-optimizers/src/main/java/io/micronaut/aot/std/sourcegen/CachedEnvironmentSourceGenerator.java
- `M` aot-std-optimizers/src/main/java/io/micronaut/aot/std/sourcegen/ConstantPropertySourcesSourceGenerator.java
- `M` aot-std-optimizers/src/main/java/io/micronaut/aot/std/sourcegen/EnvironmentPropertiesSourceGenerator.java
- `M` aot-std-optimizers/src/main/java/io/micronaut/aot/std/sourcegen/GenericPropertySourceGenerator.java
- `M` aot-std-optimizers/src/main/java/io/micronaut/aot/std/sourcegen/GraalVMOptimizationFeatureSourceGenerator.java
- `D` aot-std-optimizers/src/main/java/io/micronaut/aot/std/sourcegen/JitStaticServiceLoaderSourceGenerator.java
- `M` aot-std-optimizers/src/main/java/io/micronaut/aot/std/sourcegen/KnownMissingTypesSourceGenerator.java
- `M` aot-std-optimizers/src/main/java/io/micronaut/aot/std/sourcegen/LogbackConfigurationSourceGenerator.java
- `M` aot-std-optimizers/src/main/java/io/micronaut/aot/std/sourcegen/MapPropertySourceGenerator.java
- `D` aot-std-optimizers/src/main/java/io/micronaut/aot/std/sourcegen/NativeStaticServiceLoaderSourceGenerator.java
- `M` aot-std-optimizers/src/main/java/io/micronaut/aot/std/sourcegen/NettyPropertiesSourceGenerator.java
- `M` aot-std-optimizers/src/main/java/io/micronaut/aot/std/sourcegen/PublishersSourceGenerator.java
- `M` aot-std-optimizers/src/main/resources/META-INF/services/io.micronaut.aot.core.AOTCodeGenerator
- `M` config/checkstyle/checkstyle.xml

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` aot-cli/src/test/groovy/io/micronaut/aot/cli/CliTest.groovy
- `A` aot-core/src/test/groovy/io/micronaut/aot/core/config/SourceGeneratorLoaderTest.groovy
- `M` aot-core/src/test/groovy/io/micronaut/aot/core/context/DefaultSourceGenerationContextTest.groovy
- `A` aot-core/src/test/groovy/io/micronaut/aot/core/report/AotDiagnosticReportWriterTest.groovy
- `A` aot-core/src/test/resources/META-INF/services/io.micronaut.aot.core.AOTCodeGenerator
- `M` aot-std-optimizers/src/test/groovy/io/micronaut/aot/std/sourcegen/ConstantPropertySourcesSourceGeneratorTest.groovy
- `M` aot-std-optimizers/src/test/groovy/io/micronaut/aot/std/sourcegen/GraalVMOptimizationFeatureSourceGeneratorTest.groovy
- `D` aot-std-optimizers/src/test/groovy/io/micronaut/aot/std/sourcegen/JitStaticServiceLoaderSourceGeneratorTest.groovy
- `M` aot-std-optimizers/src/test/groovy/io/micronaut/aot/std/sourcegen/LogbackConfigurationSourceGeneratorTest.groovy
- `D` aot-std-optimizers/src/test/groovy/io/micronaut/aot/std/sourcegen/NativeStaticServiceLoaderSourceGeneratorTest.groovy
- `M` aot-std-optimizers/src/test/groovy/io/micronaut/aot/std/sourcegen/YamlPropertySourceGeneratorTest.groovy

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

