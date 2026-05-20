# Release Note Comparison

Generated: 2026-05-06 13:50 UTC
Comparison: `mn4` -> `mn5`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-jackson-xml` | `4.8.x` | `a00a55125ccb` | `git@github.com:micronaut-projects/micronaut-jackson-xml.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-jackson-xml` | `5.0.x` | `fee1d071add6` | `git@github.com:micronaut-projects/micronaut-jackson-xml.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-jackson-xml`
- Commit candidates found: 55
- File changes listed: 64
- Version values listed: 16
- File status counts: A=18, D=3, M=43

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `4.8.1-SNAPSHOT` | `5.0.0-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.gradle-micronaut` | `io.micronaut.gradle:micronaut-gradle-plugin:4.5.5` | `io.micronaut.gradle:micronaut-gradle-plugin:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.jaxb-api` | `javax.xml.bind:jaxb-api:2.3.1` | `javax.xml.bind:jaxb-api:2.3.1` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.kotlin-stdlib-jdk8` | `org.jetbrains.kotlin:kotlin-stdlib-jdk8:1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.13` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.jaxb-api` | `2.3.1` | `2.3.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.kotlin` | `1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.5` | `5.0.0-RC2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `2.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.5.5` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.9.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.0` | `changed` |
| `settings.gradle` | `plugin.io.micronaut.build.shared.settings` | `7.6.4` | `8.0.0-M18` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `e506b9500d10` Remove MediaTypeCodec usage (Denis Stepanov, 2026-03-19)

### Fixes

- `39ee25332ac0` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-rc1 (#524) (renovate[bot], 2026-05-06)
- `43b13fafa20f` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m26 (#521) (renovate[bot], 2026-05-01)
- `cf7f3629d0d6` fix(deps): update micronaut dependencies (#520) (renovate[bot], 2026-04-26)
- `fe07844ea940` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m20 (#518) (renovate[bot], 2026-04-03)
- `02937347401c` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m17 (renovate[bot], 2026-03-14)
- `5cc53b4b220f` fix(deps): update kotlin monorepo to v2.3.10 (#509) (renovate[bot], 2026-02-16)
- `f6970e68827a` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.15 (#505) (renovate[bot], 2026-02-16)
- `4ce95afb19c9` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.2 (#507) (renovate[bot], 2026-02-16)
- `a1a6c6531242` fix(deps): update kotlin monorepo to v2.3.0 (#499) (renovate[bot], 2025-12-31)
- `d0775c6c0296` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.12 (#498) (renovate[bot], 2025-12-31)
- `1fb38b0d7adc` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.10 (#494) (renovate[bot], 2025-12-15)
- `b957b4e40261` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#489) (renovate[bot], 2025-12-10)
- `8bd334852770` fix(deps): update kotlin monorepo to v2.2.21 (#483) (renovate[bot], 2025-12-10)
- `443f3c1aa376` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.8 (#478) (renovate[bot], 2025-11-03)
- `f94f38a3aa11` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.1 (#480) (renovate[bot], 2025-11-03)
- `9cd1560fc07c` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.6 (#472) (renovate[bot], 2025-10-17)

### Dependency Updates

- `5b4be2b062ff` chore(deps): update gradle to v9.5.0 (#523) (renovate[bot], 2026-05-01)
- `f28f0ef35378` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-04-22)
- `9504c69d2032` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-02-19)
- `b1ec31a48cdc` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#510) (renovate[bot], 2026-02-19)
- `8dae4e0bb91b` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m16 (#504) (renovate[bot], 2026-02-16)
- `f3ab3855d503` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m13 (#497) (renovate[bot], 2025-12-31)
- `05fed4d8d980` chore(deps): update actions/cache action to v5 (#500) (renovate[bot], 2025-12-31)
- `0bf1ea222331` chore(deps): update github artifact actions (#501) (renovate[bot], 2025-12-31)
- `6143310dd9fc` chore(deps): update actions/checkout action (#488) (renovate[bot], 2025-12-10)
- `5176979b437e` chore(deps): update github artifact actions (#484) (renovate[bot], 2025-12-10)
- `8a34124a6569` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#481) (renovate[bot], 2025-12-10)
- `a9dd1092356b` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#476) (renovate[bot], 2025-11-03)
- `8e6f928a1ece` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m8 (#477) (renovate[bot], 2025-11-03)
- `f09ac7546109` chore(deps): update gradle to v9.2.0 (#479) (renovate[bot], 2025-11-03)

### Documentation

- `619a4d5efa50` Docs: update micronaut-docs to 3.0.0 (#470) (issam liqali, 2025-10-16)

### Internal

- `373cad394eef` ci: projectVersion=5.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-10-13)

### Review Candidates

- `fee1d071add6` replace * imports (Sergio del Amo, 2026-05-06)
- `51be97d461be` micronaut = "5.0.0-RC2" (Sergio del Amo, 2026-05-06)
- `878805b4df63` micronaut-gradle-plugin = "5.0.0-M1" (Sergio del Amo, 2026-05-06)
- `ccd43480ad89` Update common files (#522) (micronaut-build, 2026-05-06)
- `8aca5e4a190a` [skip ci] Release v5.0.0-M2 (micronaut-build, 2026-04-22)
- `7ca558746410` Update common files (#519) (micronaut-build, 2026-04-22)
- `c3aaf5e42e26` Update common files (#513) (micronaut-build, 2026-04-17)
- `8a932d4046c0` Merge pull request #516 from micronaut-projects/messagebody (Denis Stepanov, 2026-03-25)
- `281ac76ca143` Merge pull request #511 from micronaut-projects/renovate/micronaut (Denis Stepanov, 2026-03-25)
- `382bd273a54b` [skip ci] Release v5.0.0-M1 (micronaut-build, 2026-02-19)
- `fcd0b0dc98ea` Update to Micronaut 5 (#508) (issam liqali, 2026-02-19)
- `e61181b56547` Update common files (#503) (micronaut-build, 2026-02-16)
- `ee6a3815cb20` Update common files (#496) (micronaut-build, 2025-12-31)
- `27f40d5b99c6` Update common files (#482) (micronaut-build, 2025-12-10)
- `d1b0634fda86` Replace Micronaut nullability annotations with JSpecify nullability annotations (#492) (Copilot, 2025-12-01)
- `1ae3606644bc` Micronaut 5 compatibility and release prep (#474) (issam liqali, 2025-11-03)
- `14f67348dc02` Update common files (#475) (micronaut-build, 2025-11-03)
- `e776382f6e87` Update common files (#473) (micronaut-build, 2025-10-20)
- `4d318491bf90` Merge branch '4.8.x' into 5.0.x (Sergio del Amo, 2025-10-16)
- `de25051e77d2` Update common files (#471) (micronaut-build, 2025-10-16)
- `2f1389d31282` micronaut build plugin 8.0.0-M4 (Sergio del Amo, 2025-10-13)
- `bc25b33fdd22` gradle 9.1 (Sergio del Amo, 2025-10-13)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` buildSrc/build.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` jackson-xml/build.gradle.kts
- `M` settings.gradle
- `M` test-suite-groovy/build.gradle.kts
- `M` test-suite-kotlin/build.gradle.kts
- `M` test-suite/build.gradle.kts

### Documentation

- `A` .agents/skills/docs/SKILL.md
- `A` .agents/skills/docs/references/control-panel-patterns.md
- `A` .agents/skills/docs/references/micronaut-docs-providers.md
- `M` .github/workflows/release.yml
- `M` test-suite-groovy/src/test/groovy/io/micronaut/xml/jackson/docs/Book.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/xml/jackson/docs/BookSaved.groovy
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/xml/jackson/docs/Book.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/xml/jackson/docs/BookControllerTest.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/xml/jackson/docs/BookSaved.kt
- `M` test-suite/src/test/java/io/micronaut/xml/jackson/docs/Book.java
- `M` test-suite/src/test/java/io/micronaut/xml/jackson/docs/BookSaved.java

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
- `M` jackson-xml/src/main/java/io/micronaut/xml/jackson/JacksonXmlConfiguration.java
- `D` jackson-xml/src/main/java/io/micronaut/xml/jackson/codec/XmlMediaTypeCodec.java
- `D` jackson-xml/src/main/java/io/micronaut/xml/jackson/codec/package-info.java
- `M` jackson-xml/src/main/java/io/micronaut/xml/jackson/server/XmlMessageHandler.java
- `M` jackson-xml/src/main/java/io/micronaut/xml/jackson/server/convert/XmlMapperFactory.java
- `M` jackson-xml/src/main/java/io/micronaut/xml/jackson/server/convert/XmlStreamConvertibleValues.java
- `M` jackson-xml/src/main/java/io/micronaut/xml/jackson/server/convert/XmlStreamToObjectConverter.java
- `M` jackson-xml/src/main/resources/META-INF/native-image/micronaut-jackson-xml/native-image.properties

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` jackson-xml/src/test/groovy/io/micronaut/xml/jackson/XmlRequestResponseSpec.groovy
- `D` jackson-xml/src/test/groovy/io/micronaut/xml/jackson/codec/XmlMediaTypeCodecSpec.groovy
- `M` jackson-xml/src/test/groovy/io/micronaut/xml/jackson/server/XmlMapperSetupSpec.groovy
- `A` jackson-xml/src/test/groovy/io/micronaut/xml/jackson/server/XmlMessageHandlerSpec.groovy
- `M` test-suite-graal/src/main/java/io/micronaut/xml/jackson/graal/Book.java
- `M` test-suite-graal/src/main/java/io/micronaut/xml/jackson/graal/BookSaved.java
- `M` test-suite-graal/src/main/resources/META-INF/native-image/jackson-xml-test-only/reflect-config.json

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

