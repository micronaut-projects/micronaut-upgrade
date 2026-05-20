────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────

• Compared as mn4 -> mn5.

  Full report: micronaut-spring-mn4-to-mn5-comparison.md:1

  Scope

  - Previous: mn4/micronaut-spring, branch 5.12.x, commit da30421f082d, clean
  - Current: mn5/micronaut-spring, branch 6.0.x, commit 8f07a83387c4, clean
  - Delta: 96 commits, 94 changed files

  Release Note Draft

  Breaking / Compatibility

  - Removed deprecated internal method SpringAwareListener.onBeanCreated(Object, Object); use onBeanCreated(BeanDefinition, Object, String) instead. See mn5/micronaut-spring/src/main/docs/guide/breaks.adoc:3.
  - MicronautBeanProcessor.micronautContext changed from DefaultBeanContext to ApplicationContext for Micronaut 5 compatibility. This may affect subclasses accessing the protected field. See mn5/micronaut-spring/config/
    accepted-api-changes.json:187.
  - Updated source nullability annotations to JSpecify across Spring integration modules.

  Compatibility / Integration

  - Updated for Micronaut Framework 5, Spring Framework 7, and Spring Boot 4.
  - MicronautApplicationContext now implements newer Spring context contract methods such as pause(), restart(), and getBeanProvider(ParameterizedTypeReference<T>). See mn5/micronaut-spring/spring-context/src/main/java/io/
    micronaut/spring/context/MicronautApplicationContext.java:168.
  - MicronautBeanProcessor now builds a standard Micronaut ApplicationContext and maps Spring ConfigurableEnvironment property sources into it instead of subclassing Micronaut internals. See mn5/micronaut-spring/spring/src/
    main/java/io/micronaut/spring/beans/MicronautBeanProcessor.java:70.
  - MicronautBeanFactory now exposes the full class hierarchy when registering Spring bean definitions into Micronaut. See mn5/micronaut-spring/spring-context/src/main/java/io/micronaut/spring/context/factory/
    MicronautBeanFactory.java:850.

  Documentation

  - Added a Breaking Changes guide page.
  - Clarified that Spring parent context and related Spring integration features require io.micronaut.spring:micronaut-spring-context. See mn5/micronaut-spring/src/main/docs/guide/micronautInsideSpring/
    springParentContext.adoc:9.

  Dependency / Platform Changes

  - Project version: 5.12.2-SNAPSHOT -> 6.0.0-SNAPSHOT
  - Micronaut Core: 4.10.15 -> 5.0.0-RC2
  - Spring Framework: 6.2.16 -> 7.0.7
  - Spring Boot: 3.5.11 -> 4.0.6
  - Micronaut Cache: 5.3.0 -> 6.0.0-M3
  - Micronaut Servlet: 5.6.0 -> 6.0.0-M3
  - Micronaut SQL: 6.3.3 -> 7.0.1-M3
  - Micronaut Validation: 4.12.0 -> 5.0.0-RC1
  - Micronaut Views: 5.9.0 -> 6.0.0-M1
  - Gradle wrapper: 8.14.3 -> 9.5.0
  - .sdkmanrc adds Java 25.0.1-graal

  I did not run the test suite; this was a static git/folder comparison plus targeted source and docs inspection.


# Release Note Comparison

Generated: 2026-05-06 15:27 UTC
Comparison: `mn4` -> `mn5`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-spring` | `5.12.x` | `da30421f082d` | `git@github.com:micronaut-projects/micronaut-spring.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-spring` | `6.0.x` | `8f07a83387c4` | `git@github.com:micronaut-projects/micronaut-spring.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-spring`
- Commit candidates found: 96
- File changes listed: 94
- Version values listed: 21
- File status counts: A=18, M=70, R=6

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `5.12.2-SNAPSHOT` | `6.0.0-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-cache` | `io.micronaut.cache:micronaut-cache-bom:5.3.0` | `io.micronaut.cache:micronaut-cache-bom:6.0.0-M3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-servlet` | `io.micronaut.servlet:micronaut-servlet-bom:5.6.0` | `io.micronaut.servlet:micronaut-servlet-bom:6.0.0-M3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-shared-settings` | `io.micronaut.build.shared.settings:io.micronaut.build.shared.settings.gradle.plugin:7.6.6` | `io.micronaut.build.shared.settings:io.micronaut.build.shared.settings.gradle.plugin:8.0.0-M18` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-sql` | `io.micronaut.sql:micronaut-sql-bom:6.3.3` | `io.micronaut.sql:micronaut-sql-bom:7.0.1-M3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-validation` | `io.micronaut.validation:micronaut-validation-bom:4.12.0` | `io.micronaut.validation:micronaut-validation-bom:5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-views` | `io.micronaut.views:micronaut-views-bom:5.9.0` | `io.micronaut.views:micronaut-views-bom:6.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-spring` | `6.2.16` | `7.0.7` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-spring-boot` | `3.5.11` | `4.0.6` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.15` | `5.0.0-RC2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-cache` | `5.3.0` | `6.0.0-M3` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-servlet` | `5.6.0` | `6.0.0-M3` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-shared-settings` | `7.6.6` | `8.0.0-M18` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-sql` | `6.3.3` | `7.0.1-M3` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.10.2` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.12.0` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-views` | `5.9.0` | `6.0.0-M1` | `changed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.0` | `changed` |
| `settings.gradle.kts` | `plugin.io.micronaut.build.shared.settings` | `7.6.6` | `8.0.0-M18` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Features

- `9d9413a0930e` add juni.platform.launcher (Sergio del Amo, 2026-04-21)

### Fixes

- `c2f878f82b55` fix(deps): update spring boot to v4.0.5 (#817) (renovate[bot], 2026-04-03)
- `7b773659f8d2` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m15 (#808) (renovate[bot], 2026-03-03)
- `7f890af864e0` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m14 (#806) (renovate[bot], 2026-03-02)
- `b6b00397bec9` fix(deps): update dependency io.micronaut.servlet:micronaut-servlet-bom to v6.0.0-m2 (#802) (renovate[bot], 2026-02-23)
- `47f933323a6a` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m13 (#800) (renovate[bot], 2026-02-20)
- `209d316def6e` fix(deps): update dependency io.micronaut.cache:micronaut-cache-bom to v6.0.0-m2 (#801) (renovate[bot], 2026-02-20)
- `ede248b52685` fix(deps): update spring core to v6.2.16 (#786) (renovate[bot], 2026-02-17)
- `08d46b59bd36` fix(deps): update spring boot to v3.5.10 (#790) (renovate[bot], 2026-02-17)
- `834d7edc0e1d` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.15 (#796) (renovate[bot], 2026-02-17)
- `be39a514d6e4` fix(deps): update dependency io.micronaut.build.shared.settings:io.micronaut.build.shared.settings.gradle.plugin to v8.0.0-m17 (#797) (renovate[bot], 2026-02-17)
- `1de6666ca4e3` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.12 (#785) (renovate[bot], 2025-12-31)
- `7fda62b1db9a` fix(deps): update dependency io.micronaut.build.shared.settings:io.micronaut.build.shared.settings.gradle.plugin to v8.0.0-m13 (#789) (renovate[bot], 2025-12-31)
- `4fe04a08e4e9` fix(deps): update spring boot to v3.5.8 (#764) (renovate[bot], 2025-12-10)
- `cfbb5e31dd62` fix(deps): update dependency io.micronaut.build.shared.settings:io.micronaut.build.shared.settings.gradle.plugin to v8.0.0-m12 (#780) (renovate[bot], 2025-12-10)
- `f173b7cd7fe1` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to v7 (#781) (renovate[bot], 2025-12-10)
- `b9958c370a13` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#774) (renovate[bot], 2025-12-10)
- `0b8c871c963e` fix(deps): update spring core to v6.2.14 (#770) (renovate[bot], 2025-12-10)
- `3789eaac815d` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to v6.3.2 (#763) (renovate[bot], 2025-12-10)
- `d978af2bf7ee` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.8 (#760) (renovate[bot], 2025-11-06)
- `6d6c33b95935` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.6 (#754) (renovate[bot], 2025-10-17)
- `21348b0a859e` fix(deps): update dependency io.micronaut.cache:micronaut-cache-bom to v4.3.0 (#569) (renovate[bot], 2024-04-11)
- `bc82f422bc0c` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.5.0 (#566) (renovate[bot], 2024-04-11)
- `b2e4804bfeb5` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.4.1 (#568) (renovate[bot], 2024-04-11)
- `b34375b7db39` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.4.0 (#564) (renovate[bot], 2024-04-01)
- `4c2f8e9e222b` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.4.4 (#554) (renovate[bot], 2024-03-27)
- `ad2518861e6d` fix(deps): update dependency io.micronaut.servlet:micronaut-servlet-bom to v4.6.0 (#551) (renovate[bot], 2024-03-27)
- `61cafbfa18df` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.3.12 (#550) (renovate[bot], 2024-03-27)

### Dependency Updates

- `91e7d6d42fef` fix #766 mention micronaut-spring-context dependency in micronaut spring docs (#767) (araysse, 2026-05-06)
- `3d0737e0f9be` Update Micronaut dependencies (#829) (renovate[bot], 2026-05-05)
- `b5793958c6e9` Update dependency io.micronaut:micronaut-core-bom to v5.0.0-M26 (#828) (renovate[bot], 2026-05-01)
- `a310d5ac1e99` Update Micronaut dependencies (#824) (renovate[bot], 2026-04-29)
- `a471121ea5dc` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2026-04-21)
- `b1b3f83a591a` Update dependency io.micronaut.sql:micronaut-sql-bom to v7.0.1-M2 (#821) (renovate[bot], 2026-04-21)
- `1ef5c5ca1ef8` Update Micronaut version to 5.0.0-M20 (#820) (Issam Liqali, 2026-04-03)
- `7f5bdfe53311` chore(deps): update gradle to v9.4.1 (#813) (renovate[bot], 2026-03-27)
- `65fe8cf90590` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2026-03-03)
- `8acbc108be72` Micronaut 5 upgrade (#799) (Ayoub Ait Abdellah, 2026-03-03)
- `0587ffc64aa0` chore(deps): update github artifact actions (#807) (renovate[bot], 2026-03-02)
- `df6d4d6712e1` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#795) (renovate[bot], 2026-02-17)
- `1426cd62ba00` chore(deps): update graalvm/setup-graalvm action to v1.4.5 (#793) (renovate[bot], 2026-02-17)
- `41d36d913ee1` chore(deps): update gradle to v9.3.1 (#798) (renovate[bot], 2026-02-17)
- `6760a5108955` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m13 (#788) (renovate[bot], 2025-12-31)
- `e72336577fd3` chore(deps): update actions/cache action to v5 (#791) (renovate[bot], 2025-12-31)
- `f2e326d82fc3` chore(deps): update github artifact actions (#792) (renovate[bot], 2025-12-31)
- `7797f58808a7` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#777) (renovate[bot], 2025-12-10)
- `bfc3455fd55f` chore(deps): update mikepenz/action-junit-report action to v6 (#775) (renovate[bot], 2025-12-10)
- `bc4dc0ec5a6b` chore(deps): update github artifact actions (#773) (renovate[bot], 2025-12-10)
- `e1cb4ded8332` chore(deps): update actions/checkout action to v6 (#772) (renovate[bot], 2025-12-10)
- `69918b1a22dc` chore(deps): update gradle to v9.2.1 (#771) (renovate[bot], 2025-12-10)
- `6d86dc73e845` chore(deps): update softprops/action-gh-release action to v2.5.0 (#762) (renovate[bot], 2025-12-10)
- `8664f65e7910` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m9 (#759) (renovate[bot], 2025-11-06)
- `f690a55780fa` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#758) (renovate[bot], 2025-11-06)
- `df80a4af928c` chore(deps): update gradle/gradle-build-action action to v3.2.1 (#567) (renovate[bot], 2024-04-11)

### Review Candidates

- `8f07a83387c4` micronaut = "5.0.0-RC2" (Sergio del Amo, 2026-05-06)
- `c75fde7eb901` Update Gradle to v9.5.0 (#830) (renovate[bot], 2026-05-06)
- `3a77177b683d` Update common files (#831) (micronaut-build, 2026-05-06)
- `5dc737d88445` [spring] Update common files for branch 6.0.x (#827) (micronaut-build, 2026-05-05)
- `3131f783e3e0` Update common files (#826) (micronaut-build, 2026-04-29)
- `19af3be5476a` Update spring boot to v4.0.6 (#825) (renovate[bot], 2026-04-29)
- `95b439b9714f` Update common files (#823) (micronaut-build, 2026-04-22)
- `029d58d65d91` [skip ci] Release v6.0.0-M2 (micronaut-build, 2026-04-21)
- `a1cfa83873d8` git: ignore .kotlin (Sergio del Amo, 2026-04-21)
- `d6e1e742bbf4` servlet 6.0.0-M3 (Sergio del Amo, 2026-04-21)
- `9e3289f195b2` validation 5.0.0-M2 (Sergio del Amo, 2026-04-21)
- `626d58cfa184` micronaut-cache 6.0.0-M3 (Sergio del Amo, 2026-04-21)
- `dd65bf4e32ff` micronaut 5.0.0-M23 (Sergio del Amo, 2026-04-21)
- `dbff854b96b3` Update spring core to v7.0.7 (#822) (renovate[bot], 2026-04-21)
- `1890ece46666` Update common files (#812) (micronaut-build, 2026-04-21)
- `48a82e7f4549` Update Micronaut to M18 and Spring to 7.0.6 (#819) (Issam Liqali, 2026-03-27)
- `109b665dbc9f` [skip ci] Release v6.0.0-M1 (micronaut-build, 2026-03-03)
- `abd0d48d14de` Update to Spring 7 and Spring Boot 4.0.3 (#810) (Sergio del Amo, 2026-03-03)
- `789509cb53a5` Update common files (#809) (micronaut-build, 2026-03-03)
- `2d30709e9592` micronaut-servlet = "6.0.0-M1" (Sergio del Amo, 2026-02-17)
- `a2f16f436ab2` micronaut-validation = "5.0.0-M1" (Sergio del Amo, 2026-02-17)
- `05513507c52b` micronaut-cache = "6.0.0-M1" (Sergio del Amo, 2026-02-17)
- `ce536fc10385` micronaut-sql = "7.0.0-M6" (Sergio del Amo, 2026-02-17)
- `6320e916b848` micronaut-test = "5.0.0-M6" (Sergio del Amo, 2026-02-17)
- `3eaff788eaeb` micronaut = "5.0.0-M10" (Sergio del Amo, 2026-02-17)
- `e1ed4f19e02f` Update common files (#794) (micronaut-build, 2026-02-17)
- `e0d463ad2d21` Update common files (#784) (micronaut-build, 2025-12-31)
- `f4217e473af0` Update common files (#765) (micronaut-build, 2025-12-10)
- `ae602faa56ea` [WIP] Replace Micronaut nullability annotations with JSpecify ones (#779) (Copilot, 2025-12-02)
- `22ca1e83d916` Micronaut 5 compatibility and release prep (#756) (issam liqali, 2025-11-06)
- `dbb0a2136d3b` 8.0.0-M9 (Sergio del Amo, 2025-11-06)
- `32e9999bf6b7` Update common files (#757) (micronaut-build, 2025-11-06)
- `353528b5ddb8` Update common files (#755) (micronaut-build, 2025-10-20)
- `f0b063ca423e` Update common files (#753) (micronaut-build, 2025-10-17)
- `548a27a234ee` micronaut gradle build plugin 8.0.0-M4 (Sergio del Amo, 2025-10-14)
- `38b419b0f968` gradle 9.1 (Sergio del Amo, 2025-10-14)
- `03d3c5d06700` Merge branch '5.12.x' into 6.0.x (Sergio del Amo, 2025-10-14)
- `7adfd0ee5593` Merge branch '5.7.x' into 6.0.x (Sergio del Amo, 2024-04-11)
- `7d980cd94262` Revert "[skip ci] Release v5.6.0" (Sergio del Amo, 2024-04-02)
- `b39f291f1404` [skip ci] Release v5.6.0 (micronaut-build, 2024-04-02)
- `391624ffbf85` Update common files (#563) (micronaut-build, 2024-03-28)
- `c7a7fb35eb50` breaks: del and doc deprecated code for MN5 (#561) (Dean Wette, 2024-03-27)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` settings.gradle.kts
- `M` spring-boot-starter/build.gradle.kts
- `M` spring-web/build.gradle.kts
- `M` test-suite/build.gradle.kts

### Documentation

- `A` .agents/skills/docs/SKILL.md
- `A` .agents/skills/docs/references/control-panel-patterns.md
- `A` .agents/skills/docs/references/micronaut-docs-providers.md
- `M` .clinerules/docs.md
- `M` .github/instructions/docs.instructions.md
- `M` .github/workflows/release.yml
- `A` src/main/docs/guide/breaks.adoc
- `M` src/main/docs/guide/micronautInsideSpring/beanPostProcessor.adoc
- `M` src/main/docs/guide/micronautInsideSpring/springParentContext.adoc
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
- `M` config/accepted-api-changes.json
- `M` config/checkstyle/checkstyle.xml
- `M` spring-annotation/src/main/java/io/micronaut/spring/annotation/AbstractSpringAnnotationMapper.java
- `M` spring-annotation/src/main/java/io/micronaut/spring/annotation/beans/ImportAnnotationVisitor.java
- `M` spring-annotation/src/main/java/io/micronaut/spring/annotation/cache/CacheEvictAnnotationMapper.java
- `M` spring-annotation/src/main/java/io/micronaut/spring/annotation/cache/CachePutAnnotationMapper.java
- `M` spring-annotation/src/main/java/io/micronaut/spring/annotation/cache/CacheableAnnotationMapper.java
- `M` spring-annotation/src/main/java/io/micronaut/spring/annotation/context/AutowiredAnnotationMapper.java
- `M` spring-boot-annotation/src/main/java/io/micronaut/spring/boot/annotation/ConditionalOnBeanAnnotationMapper.java
- `M` spring-boot-annotation/src/main/java/io/micronaut/spring/boot/annotation/ConditionalOnClassAnnotationMapper.java
- `M` spring-boot-annotation/src/main/java/io/micronaut/spring/boot/annotation/ConditionalOnMissingBeanAnnotationMapper.java
- `M` spring-boot-annotation/src/main/java/io/micronaut/spring/boot/annotation/ConditionalOnMissingClassAnnotationMapper.java
- `M` spring-boot-annotation/src/main/java/io/micronaut/spring/boot/annotation/DeleteOperationAnnotationMapper.java
- `M` spring-boot-annotation/src/main/java/io/micronaut/spring/boot/annotation/ReadOperationAnnotationMapper.java
- `M` spring-boot-annotation/src/main/java/io/micronaut/spring/boot/annotation/WriteOperationAnnotationMapper.java
- `M` spring-boot-starter/src/main/java/io/micronaut/spring/boot/starter/MicronautBeanFilter.java
- `M` spring-boot-starter/src/main/java/io/micronaut/spring/boot/starter/MicronautImportRegistrar.java
- `M` spring-boot/src/main/java/io/micronaut/spring/boot/condition/RequiresSingleCandidate.java
- `M` spring-context/src/main/java/io/micronaut/spring/context/MicronautApplicationContext.java
- `M` spring-context/src/main/java/io/micronaut/spring/context/aware/SpringAwareListener.java
- `M` spring-context/src/main/java/io/micronaut/spring/context/env/MicronautEnvironment.java
- `M` spring-context/src/main/java/io/micronaut/spring/context/factory/MicronautBeanFactory.java
- `M` spring-context/src/main/java/io/micronaut/spring/context/factory/MicronautBeanFactoryConfiguration.java
- `M` spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/CookieValueAnnotationMapper.java
- `M` spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/PathVariableAnnotationMapper.java
- `M` spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/RequestAttributeAnnotationMapper.java
- `M` spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/RequestBodyAnnotationMapper.java
- `M` spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/RequestHeaderAnnotationMapper.java
- `M` spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/RequestMappingAnnotationTransformer.java
- `M` spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/RequestParamAnnotationMapper.java
- `M` spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/RequestPartAnnotationMapper.java
- `M` spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/WebBindAnnotationMapper.java
- `M` spring-web-annotation/src/main/java/io/micronaut/spring/web/annotation/exchange/HttpExchangeAnnotationTransformer.java
- `M` spring-web/src/main/java/io/micronaut/spring/web/ModelAndViewServerFilter.java
- `M` spring-web/src/main/java/io/micronaut/spring/web/ResponseEntityServerFilter.java
- `M` spring/src/main/java/io/micronaut/spring/beans/MicronautBeanProcessor.java
- `M` spring/src/main/java/io/micronaut/spring/beans/MicronautSpringBeanFactory.java
- `M` spring/src/main/java/io/micronaut/spring/beans/ObjectProviderBeanDefinition.java
- `M` spring/src/main/java/io/micronaut/spring/tx/annotation/TransactionInterceptor.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` spring-boot-starter/src/test/java/io/micronaut/spring/boot/customautoconfigure/CustomAutoConfigureMicronautTest.java
- `M` spring-context/src/test/groovy/io/micronaut/spring/annotation/context/MicronautBeanFactoryConfigurationSpec.groovy
- `M` spring-web/src/test/java/io/micronaut/spring/web/annotation/GreetingController.java
- `M` spring-web/src/test/java/io/micronaut/spring/web/annotation/exchange/ExchangeGreetingController.java
- `R095` test-suite/src/test/java/io/micronaut/spring/tx/FakeEvent.java
- `R100` test-suite/src/test/java/io/micronaut/spring/tx/MetaAnnotation.java
- `R100` test-suite/src/test/java/io/micronaut/spring/tx/MetaTransactionalBean.java
- `R100` test-suite/src/test/java/io/micronaut/spring/tx/MockTransactionManager.java
- `R100` test-suite/src/test/java/io/micronaut/spring/tx/TransactionalBean.java
- `R100` test-suite/src/test/java/io/micronaut/spring/tx/TransactionalListener.java

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

