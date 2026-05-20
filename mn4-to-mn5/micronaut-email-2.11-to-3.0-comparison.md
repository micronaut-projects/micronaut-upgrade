Compared micronaut-email as mn4 -> mn5.

  Scope

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-email, branch 2.11.x, SHA ef01ff96d366
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-email, branch 3.0.x, SHA 6f76caecc274
  - Same remote, both clean: git@github.com:micronaut-projects/micronaut-email.git
  - Report: /private/tmp/micronaut-email-2.11-to-3.0-comparison.md

  Key Findings

  - Version line moved from 2.11.1-SNAPSHOT to 3.0.1-SNAPSHOT, with Micronaut upgraded from 4.10.4 to
    5.0.0.
  - Build baseline changed substantially: Gradle wrapper 8.14.3 -> 9.5.1, Micronaut Gradle plugin 4.5.5
    -> 5.0.0-M1, and .sdkmanrc now pins java=25.0.1-graal.
  - Documented breaking removals include the deprecated 4-arg Attachment constructor and deprecated
    AnyRecipientConstraintValidationFactory.
  - AbstractTransactionalEmailSender(ExecutorService) is now protected, matching the accepted API changes
    for the major release.
  - Source nullability annotations were migrated from Micronaut annotations to JSpecify across the
    modules.
  - JavaMail composition now handles inline attachments correctly using related multipart content, and
    address header encoding was fixed for named contacts.
  - SendGrid integration now exposes SendGrid as a bean, allowing customization through a
    BeanCreatedEventListener<SendGrid>.
  - Provider/library updates include Mailjet 5.2.6 -> 6.0.1, Mailtrap 1.1.0 -> 1.2.0, and Postmark 1.11.1
    -> 1.13.0; SendGrid, Jakarta Mail, Eclipse Angus, and POI OOXML stayed on the same versions.

  Diff size: 115 files changed, 3831 insertions(+), 351 deletions(-).

  I did not run tests; this was a folder comparison and targeted source/build-diff review only.


# Release Note Comparison

Generated: 2026-05-20 05:05 UTC
Comparison: `2.11.x` -> `3.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-email` | `2.11.x` | `ef01ff96d366` | `git@github.com:micronaut-projects/micronaut-email.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-email` | `3.0.x` | `6f76caecc274` | `git@github.com:micronaut-projects/micronaut-email.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-email`
- Commit candidates found: 83
- File changes listed: 115
- Version values listed: 48
- File status counts: A=25, D=1, M=89

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `2.11.1-SNAPSHOT` | `3.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.commons-io` | `commons-io:commons-io:2.20.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.gradle-kotlin` | `org.jetbrains.kotlin:kotlin-gradle-plugin:1.9.24` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.gradle-kotlin-allopen` | `org.jetbrains.kotlin:kotlin-allopen:1.9.24` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.gradle-kotlin-noarg` | `org.jetbrains.kotlin:kotlin-noarg:1.9.24` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.kotlin-stdlib-jdk8` | `org.jetbrains.kotlin:kotlin-stdlib-jdk8:1.9.24` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.managed-eclipse-angus` | `org.eclipse.angus:angus-mail:2.0.5` | `org.eclipse.angus:angus-mail:2.0.5` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-jakarta-mail` | `jakarta.mail:jakarta.mail-api:2.1.5` | `jakarta.mail:jakarta.mail-api:2.1.5` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-mailjet-client` | `com.mailjet:mailjet-client:5.2.6` | `com.mailjet:mailjet-client:6.0.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-mailtrap` | `io.mailtrap:mailtrap-java:1.1.0` | `io.mailtrap:mailtrap-java:1.2.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-postmark` | `com.postmarkapp:postmark:1.11.1` | `com.postmarkapp:postmark:1.13.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-sendgrid-java` | `com.sendgrid:sendgrid-java:4.10.3` | `com.sendgrid:sendgrid-java:4.10.3` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.micronaut-aws` | `io.micronaut.aws:micronaut-aws-bom:4.11.0` | `io.micronaut.aws:micronaut-aws-bom:5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-gradle-plugin` | `io.micronaut.gradle:micronaut-gradle-plugin:4.5.5` | `io.micronaut.gradle:micronaut-gradle-plugin:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-hibernate-validator` | `io.micronaut.beanvalidation:micronaut-hibernate-validator-bom:4.8.0` | `io.micronaut.beanvalidation:micronaut-hibernate-validator-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-reactor` | `micronaut-reactor:3.9.0` | `micronaut-reactor:4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.15.5` | `io.micronaut.serde:micronaut-serde-bom:3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-resources` | `io.micronaut.testresources:micronaut-test-resources-bom:2.10.1` | `io.micronaut.testresources:micronaut-test-resources-bom:4.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-validation` | `io.micronaut.validation:micronaut-validation-bom:4.11.0` | `io.micronaut.validation:micronaut-validation-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-views` | `io.micronaut.views:micronaut-views-bom:5.9.0` | `io.micronaut.views:micronaut-views-bom:6.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.poi-ooxml` | `org.apache.poi:poi-ooxml:5.5.1` | `org.apache.poi:poi-ooxml:5.5.1` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.spock-core` | `org.spockframework:spock-core:2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.commons-io` | `2.20.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.18` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.kotlin` | `1.9.24` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.managed-eclipse-angus` | `2.0.5` | `2.0.5` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-jakarta-mail` | `2.1.5` | `2.1.5` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-mailjet` | `5.2.6` | `6.0.1` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-mailtrap` | `1.1.0` | `1.2.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-postmark` | `1.11.1` | `1.13.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-sendgrid` | `4.10.3` | `4.10.3` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.4` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-aws` | `4.11.0` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `2.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.5.5` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-hibernate-validator` | `4.8.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-reactor` | `3.9.0` | `4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.15.5` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.9.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test-resources` | `2.10.1` | `4.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.11.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-views` | `5.9.0` | `6.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.poi-ooxml` | `5.5.1` | `5.5.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |
| `settings.gradle` | `plugin.io.micronaut.build.shared.settings` | `7.6.4` | `8.0.0-M18` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `2c956476ca39` Removed the Spock version force configuration from build (#592) (Issam Liqali, 2026-03-12)
- `850640484992` Remove deprecated code for Micronaut Framework 5 and document breaking changes. (#364) (Dean Wette, 2024-03-12)

### Fixes

- `6257bc17578e` fix(deps): update dependency com.postmarkapp:postmark to v1.13.0 (#585) (renovate[bot], 2026-04-30)
- `d03fc9fc1a85` fix(deps): update dependency io.mailtrap:mailtrap-java to v1.2.0 (#597) (renovate[bot], 2026-04-30)
- `6c44159f0db4` fix(deps): update dependency org.apache.tika:tika-core to v3.3.0 (#598) (renovate[bot], 2026-04-30)
- `aa278a42049e` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m16 (#578) (renovate[bot], 2026-03-12)
- `c4e84453776a` fix(deps): update dependency org.apache.poi:poi-ooxml to v5.5.1 (#572) (renovate[bot], 2025-12-02)
- `767b8231c8a5` fix: Inline attachments are not properly represented (#552) (#553) (Daniel Muhra, 2025-11-28)
- `303fab870d80` fix: email header encoding issue (#550) (#551) (Daniel Muhra, 2025-11-27)
- `acb27fe78438` fix(deps): update dependency commons-io:commons-io to v2.21.0 (#556) (renovate[bot], 2025-11-27)
- `d9cbfea47dd9` fix(deps): update kotlin monorepo to v2.2.21 (#549) (renovate[bot], 2025-11-27)
- `6ac568e9a479` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.12.0 (#559) (renovate[bot], 2025-11-27)
- `3e11c150783c` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#558) (renovate[bot], 2025-11-27)
- `40894307e287` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#560) (renovate[bot], 2025-11-27)
- `df061537ade9` fix(deps): update dependency org.apache.poi:poi-ooxml to v5.5.0 (#561) (renovate[bot], 2025-11-27)
- `0b4e27f55221` fix(deps): update dependency io.micronaut.reactor:micronaut-reactor-bom to v3.9.1 (#546) (renovate[bot], 2025-11-19)
- `260b96d8a5e6` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.8 (#543) (renovate[bot], 2025-11-03)
- `345cfd7166c4` fix(deps): update dependency com.mailjet:mailjet-client to v6 (#517) (renovate[bot], 2025-10-13)
- `8fe16f6b62b5` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.3.6 (#376) (renovate[bot], 2024-04-07)
- `59471a52eafa` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.8.2 (#366) (renovate[bot], 2024-04-01)
- `d2593a826dc7` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.3.5 (#372) (renovate[bot], 2024-04-01)
- `fb8b98402a21` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.4.4 (#367) (renovate[bot], 2024-04-01)
- `52e8d5a96410` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.4.0 (#369) (renovate[bot], 2024-04-01)

### Dependency Updates

- `77320e84a09c` chore: Bump version to 3.0.1-SNAPSHOT (micronaut-build, 2026-05-18)
- `068f1b16632b` chore: Bump version to 3.0.0-SNAPSHOT (micronaut-build, 2026-05-08)
- `8362795611d9` Update Micronaut dependencies (#609) (renovate[bot], 2026-05-08)
- `66fecc6d89d4` Update dependency io.micronaut:micronaut-core-bom to v5.0.0-M26 (#607) (renovate[bot], 2026-05-01)
- `b97694048826` Update Micronaut dependencies (#602) (renovate[bot], 2026-04-30)
- `0ddb915895b7` Update dependency io.micronaut.testresources:micronaut-test-resources-bom to v3 (#605) (renovate[bot], 2026-04-30)
- `814b0f57475b` Update dependency com.google.code.gson:gson to v2.14.0 (#603) (renovate[bot], 2026-04-30)
- `1d0c9697074c` Update dependency com.fasterxml.jackson.core:jackson-core to v2.21.3 (#581) (renovate[bot], 2026-04-30)
- `60e255654f3e` chore(deps): update actions/checkout action to v6 (#596) (renovate[bot], 2026-04-27)
- `bc34e124dbd6` chore: Bump version to 3.0.0-SNAPSHOT (micronaut-build, 2025-12-09)
- `27b20d982642` chore(deps): update gradle/actions action to v5 (#575) (renovate[bot], 2025-12-09)
- `14d1a83ddae3` chore(deps): update stefanzweifel/git-auto-commit-action action to v7 (#577) (renovate[bot], 2025-12-09)
- `0d3b92734df3` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#569) (renovate[bot], 2025-12-02)
- `00f296486ed6` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m11 (#565) (renovate[bot], 2025-11-28)
- `3cf258756be2` chore(deps): update gradle to v9.2.1 (#555) (renovate[bot], 2025-11-27)
- `59a56f9e3b1c` chore(deps): update graalvm/setup-graalvm action to v1.4.3 (#562) (renovate[bot], 2025-11-27)
- `562074579baa` chore(deps): update softprops/action-gh-release action to v2.4.2 (#548) (renovate[bot], 2025-11-19)
- `672d3e4111a2` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m9 (#544) (renovate[bot], 2025-11-19)
- `d401bf675a49` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#540) (renovate[bot], 2025-11-03)
- `3e15c8bde1c2` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m8 (#542) (renovate[bot], 2025-11-03)
- `621b138dc562` chore(deps): update gradle/gradle-build-action action to v3.2.0 (#375) (renovate[bot], 2024-04-07)
- `b57f7aa30921` chore(deps): update plugin io.micronaut.build.shared.settings to v6.7.0 (#370) (renovate[bot], 2024-04-01)
- `57ec3d93091b` chore(deps): update dependency gradle to v8.7 (#373) (renovate[bot], 2024-03-27)
- `9a8c92631919` chore(deps): update slsa-framework/slsa-github-generator action to v1.10.0 (#374) (renovate[bot], 2024-03-27)

### Documentation

- `d190fd410bac` Docs: update micronaut-docs to 3.0.0 (#537) (issam liqali, 2025-10-16)

### Internal

- `172ee8564ceb` build: del micronaut-docs test spock, groovy versions (Sergio del Amo, 2025-11-27)

### Review Candidates

- `6f76caecc274` Update common files (#614) (micronaut-build, 2026-05-19)
- `edf3f99d3214` [skip ci] Release v3.0.0 (micronaut-build, 2026-05-18)
- `bbe4231b2da0` micronaut-hibernate-validator = "5.0.0" (Sergio del Amo, 2026-05-14)
- `2bcbed03a554` Update versions (Sergio del Amo, 2026-05-14)
- `ad51ae42059b` Update common files (#612) (micronaut-build, 2026-05-14)
- `76500dc75447` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `6cdaa3c5672d` Update common files (#611) (micronaut-build, 2026-05-09)
- `845247747baa` [skip ci] Release v3.0.0-RC1 (micronaut-build, 2026-05-08)
- `cd067a59a933` update versions (Sergio del Amo, 2026-05-08)
- `a7ad8ff40d29` Update common files (#608) (micronaut-build, 2026-05-08)
- `f3e6436da462` Update Gradle to v9.5.0 (#610) (renovate[bot], 2026-05-08)
- `57542262b76d` Update common files (#606) (micronaut-build, 2026-05-01)
- `e91e937d0e16` Update Gradle to v9.5.0 (#588) (renovate[bot], 2026-04-30)
- `8958aeb84d5b` Update common files (#604) (micronaut-build, 2026-04-30)
- `266bc4f71d00` Update gradle/actions action to v6 (#599) (renovate[bot], 2026-04-27)
- `76ea08cf0f60` Update common files (#593) (micronaut-build, 2026-04-26)
- `8e9838fbbe8b` Update common files (#583) (micronaut-build, 2026-03-12)
- `f3f1cc8db75f` Update to micronaut build 8.0.0-M17 (#591) (Issam Liqali, 2026-03-12)
- `e6f0b1d2868c` [skip ci] Release v3.0.0-M1 (micronaut-build, 2025-12-09)
- `e504f3bc9722` Update to m1 (#567) (Sergio del Amo, 2025-12-09)
- `98bd0f0229d1` Update common files (#576) (micronaut-build, 2025-12-09)
- `2635d03af7d9` Replace Micronaut nullability annotations with JSpecify annotations (#571) (Copilot, 2025-12-01)
- `f97e637dbf22` Merge branch '2.11.x' into 3.0.x (Sergio del Amo, 2025-11-28)
- `db0ac53dd72e` Merge branch '2.11.x' into 3.0.x (Sergio del Amo, 2025-11-28)
- `c4153fc04a7e` imp: SendGrid as bean (#547) (Daniel Muhra, 2025-11-27)
- `65f443f2da94` Update common files (#557) (micronaut-build, 2025-11-27)
- `4df30deacfb9` Update common files (#545) (micronaut-build, 2025-11-19)
- `75d755ef972d` Micronaut 5 compatibility (#541) (issam liqali, 2025-11-03)
- `cd6db3177d82` Update common files (#539) (micronaut-build, 2025-11-03)
- `1ddc29520113` Update common files (#538) (micronaut-build, 2025-10-16)
- `b6baad0f7884` Micornaut build plugin 8.0.0-M4 (Sergio del Amo, 2025-10-13)
- `d17efbc79a7d` gradel 9.1 (Sergio del Amo, 2025-10-13)
- `835f465f2c37` Merge branch '2.10.x' into 3.0.x (Sergio del Amo, 2025-10-13)
- `57bbedfdf9f4` Update common files (#368) (micronaut-build, 2024-03-27)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` .github/workflows/update-gradle-wrapper.yml
- `M` buildSrc/build.gradle
- `M` email-mailjet/build.gradle.kts
- `M` email-mailtrap/build.gradle.kts
- `M` email-postmark/build.gradle.kts
- `M` email-sendgrid/build.gradle.kts
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` settings.gradle
- `M` test-suite-groovy/build.gradle
- `M` test-suite-kotlin/build.gradle
- `M` test-suite-utils/build.gradle

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
- `M` src/main/docs/guide/breaks.adoc
- `M` test-suite/src/test/java/io/micronaut/email/docs/MockEmailSender.java

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
- `M` email-amazon-ses/src/main/java/io/micronaut/email/ses/AsyncSesEmailSender.java
- `M` email-amazon-ses/src/main/java/io/micronaut/email/ses/SesEmailComposer.java
- `M` email-amazon-ses/src/main/java/io/micronaut/email/ses/SesEmailSender.java
- `M` email-javamail-composer/src/main/java/io/micronaut/email/javamail/composer/DefaultMessageComposer.java
- `M` email-javamail-composer/src/main/java/io/micronaut/email/javamail/composer/MessageComposer.java
- `M` email-javamail/src/main/java/io/micronaut/email/javamail/sender/DefaultSessionProvider.java
- `M` email-javamail/src/main/java/io/micronaut/email/javamail/sender/JavaMailConfiguration.java
- `M` email-javamail/src/main/java/io/micronaut/email/javamail/sender/JavaMailConfigurationProperties.java
- `M` email-javamail/src/main/java/io/micronaut/email/javamail/sender/JavaxEmailComposer.java
- `M` email-javamail/src/main/java/io/micronaut/email/javamail/sender/JavaxEmailSender.java
- `M` email-javamail/src/main/java/io/micronaut/email/javamail/sender/MailPropertiesProvider.java
- `M` email-javamail/src/main/java/io/micronaut/email/javamail/sender/MailPropertiesProviderFactory.java
- `M` email-javamail/src/main/java/io/micronaut/email/javamail/sender/SessionProvider.java
- `M` email-javamail/src/main/java/io/micronaut/email/javamail/sender/authentication/AuthenticatorFactory.java
- `M` email-javamail/src/main/java/io/micronaut/email/javamail/sender/authentication/JavaMailAuthenticationConfiguration.java
- `M` email-javamail/src/main/java/io/micronaut/email/javamail/sender/authentication/JavaMailAuthenticationConfigurationProperties.java
- `M` email-mailjet/src/main/java/io/micronaut/email/mailjet/MailjetConfiguration.java
- `M` email-mailjet/src/main/java/io/micronaut/email/mailjet/MailjetConfigurationProperties.java
- `M` email-mailjet/src/main/java/io/micronaut/email/mailjet/MailjetEmailComposer.java
- `M` email-mailjet/src/main/java/io/micronaut/email/mailjet/MailjetEmailSender.java
- `M` email-mailtrap/src/main/java/io/micronaut/email/mailtrap/MailtrapConfiguration.java
- `M` email-mailtrap/src/main/java/io/micronaut/email/mailtrap/MailtrapConfigurationProperties.java
- `M` email-mailtrap/src/main/java/io/micronaut/email/mailtrap/MailtrapEmailComposer.java
- `M` email-mailtrap/src/main/java/io/micronaut/email/mailtrap/MailtrapEmailSender.java
- `M` email-postmark/src/main/java/io/micronaut/email/postmark/PostmarkConfiguration.java
- `M` email-postmark/src/main/java/io/micronaut/email/postmark/PostmarkConfigurationProperties.java
- `M` email-postmark/src/main/java/io/micronaut/email/postmark/PostmarkEmailComposer.java
- `M` email-postmark/src/main/java/io/micronaut/email/postmark/PostmarkEmailSender.java
- `M` email-sendgrid/src/main/java/io/micronaut/email/sendgrid/SendGridConfiguration.java
- `M` email-sendgrid/src/main/java/io/micronaut/email/sendgrid/SendGridConfigurationProperties.java
- `M` email-sendgrid/src/main/java/io/micronaut/email/sendgrid/SendGridFactory.java
- `M` email-sendgrid/src/main/java/io/micronaut/email/sendgrid/SendgridEmailComposer.java
- `M` email-sendgrid/src/main/java/io/micronaut/email/sendgrid/SendgridEmailSender.java
- `M` email-template/src/main/java/io/micronaut/email/template/DefaultTemplateBodyDecorator.java
- `M` email-template/src/main/java/io/micronaut/email/template/TemplateBody.java
- `M` email-template/src/main/java/io/micronaut/email/template/TemplateBodyDecorator.java
- `M` email/src/main/java/io/micronaut/email/AbstractTransactionalEmailSender.java
- `M` email/src/main/java/io/micronaut/email/AsyncEmailSender.java
- `M` email/src/main/java/io/micronaut/email/AsyncTransactionalEmailSender.java
- `M` email/src/main/java/io/micronaut/email/Attachment.java
- `M` email/src/main/java/io/micronaut/email/Body.java
- `M` email/src/main/java/io/micronaut/email/Contact.java
- `M` email/src/main/java/io/micronaut/email/DefaultAsyncEmailSender.java
- `M` email/src/main/java/io/micronaut/email/DefaultEmailSender.java
- `M` email/src/main/java/io/micronaut/email/Email.java
- `M` email/src/main/java/io/micronaut/email/EmailComposer.java
- `M` email/src/main/java/io/micronaut/email/EmailDecorator.java
- `M` email/src/main/java/io/micronaut/email/EmailSender.java
- `M` email/src/main/java/io/micronaut/email/FromDecorator.java
- `M` email/src/main/java/io/micronaut/email/MultipartBody.java
- `M` email/src/main/java/io/micronaut/email/StringBody.java
- `M` email/src/main/java/io/micronaut/email/TransactionalEmailSender.java
- `M` email/src/main/java/io/micronaut/email/configuration/FromConfiguration.java
- `M` email/src/main/java/io/micronaut/email/configuration/FromConfigurationProperties.java
- `D` email/src/main/java/io/micronaut/email/validation/AnyRecipientConstraintValidationFactory.java
- `M` email/src/main/java/io/micronaut/email/validation/Recipients.java
- `M` email/src/main/java/io/micronaut/email/validation/RecipientsUtils.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` email-sendgrid/src/test/java/io/micronaut/email/sendgrid/SendGridBeanCreatedEventListener.java

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

