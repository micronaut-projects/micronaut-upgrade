Compared micronaut-chatbots as mn4 -> mn5.

  Scope

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-chatbots, branch 1.6.x, SHA 629e713f0b3c
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-chatbots, branch 2.0.x, SHA 096cae31d7c5
  - Same remote, both clean: git@github.com:micronaut-projects/micronaut-chatbots.git
  - Report: /private/tmp/micronaut-chatbots-1.6-to-2.0-comparison.md

  Key Findings

  - Version line moves 1.6.0-SNAPSHOT -> 2.0.1-SNAPSHOT.
  - Baseline updates include Micronaut 4.10.4 -> 5.0.0, Gradle 8.14.3 -> 9.5.1, settings plugin 7.6.4 ->
    8.0.0-M18, and new .sdkmanrc Java 25.0.1-graal.
  - Platform BOMs move to Micronaut 5-compatible lines: AWS 4.11.0 -> 5.0.0, Azure 5.12.0 -> 6.0.0, GCP
    5.13.0 -> 6.0.0, Serde 2.15.5 -> 3.0.0, Validation 4.11.0 -> 5.0.0.
  - Breaking change documented: io.micronaut.chatbots.google.api.Space.type was removed, along with
    getType() and setType(Type). Use singleUserBotDm or spaceType instead.
  - Public APIs broadly replace Micronaut nullability annotations with JSpecify annotations.
  - Google Cloud Function build support updates com.google.cloud.functions:functions-framework-api from
    1.1.4 to 2.0.1.
  - Kotlin/test build wiring now uses Micronaut build Kotlin plugins instead of directly applying Kotlin
    Gradle plugin entries.

  Diff size: 184 files changed, 3896 insertions(+), 376 deletions(-).

  I did not run tests; this was a folder comparison and targeted source/build-diff review only.

# Release Note Comparison

Generated: 2026-05-19 15:32 UTC
Comparison: `1.6.x` -> `2.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-chatbots` | `1.6.x` | `629e713f0b3c` | `git@github.com:micronaut-projects/micronaut-chatbots.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-chatbots` | `2.0.x` | `096cae31d7c5` | `git@github.com:micronaut-projects/micronaut-chatbots.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-chatbots`
- Commit candidates found: 71
- File changes listed: 184
- Version values listed: 23
- File status counts: A=25, M=159

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `1.6.0-SNAPSHOT` | `2.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.gradle-kotlin` | `org.jetbrains.kotlin:kotlin-gradle-plugin:1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-aws` | `io.micronaut.aws:micronaut-aws-bom:4.11.0` | `io.micronaut.aws:micronaut-aws-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-azure` | `io.micronaut.azure:micronaut-azure-bom:5.12.0` | `io.micronaut.azure:micronaut-azure-bom:6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-gcp` | `io.micronaut.gcp:micronaut-gcp-bom:5.13.0` | `io.micronaut.gcp:micronaut-gcp-bom:6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-logging` | `io.micronaut.logging:micronaut-logging-bom:1.7.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.15.5` | `io.micronaut.serde:micronaut-serde-bom:3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-validation` | `io.micronaut.validation:micronaut-validation-bom:4.11.0` | `io.micronaut.validation:micronaut-validation-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.17` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.kotlin` | `1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.4` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-aws` | `4.11.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-azure` | `5.12.0` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gcp` | `5.13.0` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.15.5` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.9.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.11.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |
| `settings.gradle.kts` | `plugin.io.micronaut.build.shared.settings` | `7.6.4` | `8.0.0-M18` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `50c7a7e3eeb5` remove Micronaut Build fix to 21 (Sergio del Amo, 2026-05-07)
- `e9b0e91dc6a0` Remove Spock version force configuration (#367) (Issam Liqali, 2026-03-16)
- `e9b2f667d48b` Remove deprecated code for Micronaut Framework 5 and document breaking changes. (#196) (Dean Wette, 2024-04-01)

### Fixes

- `226cc919432f` fix(deps): update dependency io.micronaut.azure:micronaut-azure-bom to v5.13.0 (#366) (renovate[bot], 2026-04-22)
- `64e81a154f2e` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m6 (#364) (renovate[bot], 2026-04-15)
- `ddc5307a3fa2` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m22 (#371) (renovate[bot], 2026-04-15)
- `7a840dae440c` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m17 (#358) (renovate[bot], 2026-03-16)
- `547b9660fea4` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.12.0 (#346) (renovate[bot], 2025-12-10)
- `5d5b41b43073` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#345) (renovate[bot], 2025-12-10)
- `439072c282c6` fix(deps): update kotlin monorepo to v2.2.21 (#343) (renovate[bot], 2025-12-10)
- `76c4215d97fb` fix(deps): update dependency io.micronaut.gcp:micronaut-gcp-bom to v5.13.1 (#342) (renovate[bot], 2025-12-10)
- `03ae7e11f030` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#341) (renovate[bot], 2025-12-10)
- `e1fde0364ecb` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.6 (#333) (renovate[bot], 2025-10-17)
- `685ae9b5522b` fix(deps): update dependency io.micronaut.logging:micronaut-logging-bom to v1.3.0 (#201) (renovate[bot], 2024-04-11)

### Dependency Updates

- `13363022151c` chore: Bump version to 2.0.1-SNAPSHOT (micronaut-build, 2026-05-14)
- `2e31575adc9e` chore: Bump version to 2.0.0-SNAPSHOT (micronaut-build, 2026-05-07)
- `1831801d0e7d` Update Micronaut dependencies (#373) (renovate[bot], 2026-05-07)
- `29e33c69227d` chore(deps): update gradle to v9.4.1 (#365) (renovate[bot], 2026-04-22)
- `43b14cb5a946` chore(deps): update gradle/actions action to v6 (#370) (renovate[bot], 2026-04-22)
- `f7c44de3eb09` chore(deps): update softprops/action-gh-release action to v3 (#372) (renovate[bot], 2026-04-22)
- `8e8659d73a84` chore(deps): update dependency com.google.cloud.functions:functions-framework-api to v2 (renovate[bot], 2026-04-21)
- `75fae93a98b9` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#361) (renovate[bot], 2026-03-16)
- `1dd03ba42aa2` chore: Bump version to 2.0.0-SNAPSHOT (micronaut-build, 2025-12-15)
- `335dfc9ccfa8` chore(deps): update stefanzweifel/git-auto-commit-action action to v7 (#355) (renovate[bot], 2025-12-10)
- `4522ed8a6c21` chore(deps): update mikepenz/action-junit-report action to v6 (#354) (renovate[bot], 2025-12-10)
- `0bfef8976531` chore(deps): update gradle/actions action to v5 (#353) (renovate[bot], 2025-12-10)
- `d80bf1057e99` chore(deps): update github artifact actions (#352) (renovate[bot], 2025-12-10)
- `74eedc13f4b8` chore(deps): update graalvm/setup-graalvm action to v1.4.4 (#348) (renovate[bot], 2025-12-10)
- `bdc1bdf325a6` chore(deps): update actions/checkout action to v6 (#347) (renovate[bot], 2025-12-10)
- `0f0bfeae8153` chore(deps): update gradle to v9.2.1 (#344) (renovate[bot], 2025-12-10)
- `c53b027a70ed` chore(deps): update softprops/action-gh-release action to v2.5.0 (#340) (renovate[bot], 2025-12-10)
- `925b243c471b` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#339) (renovate[bot], 2025-12-10)
- `1a5b81c1b6b5` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#336) (renovate[bot], 2025-10-29)
- `d348a8d75eb7` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m7 (#337) (renovate[bot], 2025-10-29)
- `741866a41e6c` chore(deps): update gradle/gradle-build-action action to v3.2.1 (#204) (renovate[bot], 2024-04-11)
- `2e82f2a1d85f` chore(deps): update gradle/gradle-build-action action to v3.2.0 (#200) (renovate[bot], 2024-04-05)

### Internal

- `7df334893b46` Build: Update to Micronaut 5 (#359) (issam liqali, 2025-12-15)

### Review Candidates

- `096cae31d7c5` micronaut-aws = "5.0.0" (Sergio del Amo, 2026-05-19)
- `0e7d31c0569a` Update common files (#380) (micronaut-build, 2026-05-19)
- `b6865582db00` update versions (Sergio del Amo, 2026-05-18)
- `861cdcecbc9d` [skip ci] Release v2.0.0 (micronaut-build, 2026-05-14)
- `0f474017f79d` Update versions (Sergio del Amo, 2026-05-14)
- `fc2d78f477c3` Update common files (#378) (micronaut-build, 2026-05-14)
- `62523cab188a` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `338c5ad7d589` Update common files (#377) (micronaut-build, 2026-05-09)
- `6e42052f011e` [skip ci] Release v2.0.0-RC2 (micronaut-build, 2026-05-07)
- `330d0b83cfd5` git ignore .kotlin (Sergio del Amo, 2026-05-07)
- `cfb9ede12d25` [skip ci] Release v2.0.0-RC1 (micronaut-build, 2026-05-07)
- `0112fe84aaf2` Update common files (#376) (micronaut-build, 2026-05-07)
- `9dade7f866cd` Merge pull request #374 from micronaut-projects/renovate/gradle-9.x (Graeme Rocher, 2026-05-01)
- `94614c0b42b1` Merge pull request #349 from micronaut-projects/renovate/com.google.cloud.functions-functions-framework-api-2.x (Graeme Rocher, 2026-05-01)
- `f5b3bf2a5cb7` Merge pull request #375 from micronaut-projects/sync-files-2.0.x (Graeme Rocher, 2026-05-01)
- `167c9223e6a6` Update common files (micronaut-build, 2026-04-30)
- `32ea7f10aaf3` Update Gradle to v9.5.0 (renovate[bot], 2026-04-28)
- `4a233503f345` micronaut-validation = "5.0.0-M2" (Sergio del Amo, 2026-04-22)
- `6fcd871bce5d` micronaut-serde = "3.0.0-M7" (Sergio del Amo, 2026-04-22)
- `95639539b0df` micronaut-gcp = "6.0.0-M2" (Sergio del Amo, 2026-04-22)
- `771ed2c9f8de` micronaut-aws = "5.0.0-M3" (Sergio del Amo, 2026-04-22)
- `d0fef0704e93` micronaut-azure = "6.0.0-M2" (Sergio del Amo, 2026-04-22)
- `ef47eae55874` micronaut = "5.0.0-M23" (Sergio del Amo, 2026-04-22)
- `d477a70709d5` Update common files (#369) (micronaut-build, 2026-04-22)
- `3193f66757dc` Update common files (#357) (micronaut-build, 2026-03-16)
- `65bdb735cf45` [skip ci] Release v2.0.0-M7 (micronaut-build, 2025-12-15)
- `81261737ea06` Update common files (#338) (micronaut-build, 2025-12-10)
- `5df6757c5cef` Replace Micronaut nullability annotations with JSpecify nullability annotations (#351) (Copilot, 2025-12-01)
- `f695ac95955a` build project with gradle 9.1 and apply changes for micronaut 5 release (#335) (araysse, 2025-11-03)
- `d256028ec7fa` Update common files (#334) (micronaut-build, 2025-10-29)
- `ac240a29db4a` Update common files (#332) (micronaut-build, 2025-10-17)
- `1eee38a39232` Micronaut build gradle plugin 8.0.0-M4 (Sergio del Amo, 2025-10-15)
- `282c0380a46e` gradle 9.1 (Sergio del Amo, 2025-10-15)
- `77c945c9b438` Merge branch '1.6.x' into 2.0.x (Sergio del Amo, 2025-10-15)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` .github/workflows/update-gradle-wrapper.yml
- `M` buildSrc/build.gradle.kts
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.chatbots-google-cloud-function.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` settings.gradle.kts
- `M` test-suite-groovy/build.gradle.kts
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
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/Document.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/InputMediaDocument.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/send/SendDocument.java

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
- `M` chatbots-basecamp-api/src/main/java/io/micronaut/chatbots/basecamp/api/Company.java
- `M` chatbots-basecamp-api/src/main/java/io/micronaut/chatbots/basecamp/api/Creator.java
- `M` chatbots-basecamp-api/src/main/java/io/micronaut/chatbots/basecamp/api/Query.java
- `M` chatbots-basecamp-core/src/main/java/io/micronaut/chatbots/basecamp/core/BasecampBotConfigurationProperties.java
- `M` chatbots-basecamp-core/src/main/java/io/micronaut/chatbots/basecamp/core/BasecampUserAgentValidator.java
- `M` chatbots-basecamp-lambda/src/main/java/io/micronaut/chatbots/basecamp/lambda/Handler.java
- `M` chatbots-core/src/main/java/io/micronaut/chatbots/core/ChatbotsConfiguration.java
- `M` chatbots-core/src/main/java/io/micronaut/chatbots/core/ChatbotsConfigurationProperties.java
- `M` chatbots-core/src/main/java/io/micronaut/chatbots/core/CommandResponse.java
- `M` chatbots-core/src/main/java/io/micronaut/chatbots/core/DefaultDispatcher.java
- `M` chatbots-core/src/main/java/io/micronaut/chatbots/core/DefaultTextResourceLoader.java
- `M` chatbots-core/src/main/java/io/micronaut/chatbots/core/Dispatcher.java
- `M` chatbots-core/src/main/java/io/micronaut/chatbots/core/FileExtension.java
- `M` chatbots-core/src/main/java/io/micronaut/chatbots/core/Handler.java
- `M` chatbots-core/src/main/java/io/micronaut/chatbots/core/SlashCommandParser.java
- `M` chatbots-core/src/main/java/io/micronaut/chatbots/core/SpaceParser.java
- `M` chatbots-core/src/main/java/io/micronaut/chatbots/core/TextResourceLoader.java
- `M` chatbots-google-api/src/main/java/io/micronaut/chatbots/google/api/ActionParameter.java
- `M` chatbots-google-api/src/main/java/io/micronaut/chatbots/google/api/FormAction.java
- `M` chatbots-google-api/src/main/java/io/micronaut/chatbots/google/api/MatchedUrl.java
- `M` chatbots-google-api/src/main/java/io/micronaut/chatbots/google/api/SlashCommand.java
- `M` chatbots-google-api/src/main/java/io/micronaut/chatbots/google/api/Space.java
- `M` chatbots-google-api/src/main/java/io/micronaut/chatbots/google/api/SpaceDetails.java
- `M` chatbots-google-api/src/main/java/io/micronaut/chatbots/google/api/User.java
- `M` chatbots-http/src/main/java/io/micronaut/chatbots/http/ControllerConfiguration.java
- `M` chatbots-http/src/main/java/io/micronaut/chatbots/http/ControllerConfigurationProperties.java
- `M` chatbots-lambda/src/main/java/io/micronaut/chatbots/lambda/AbstractHandler.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/AbstractFile.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/AbstractFileWithDimensions.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/Animation.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/Audio.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/BotCommand.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/CallbackQuery.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/Chat.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/ChatAdministratorRights.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/ChatInviteLink.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/ChatLocation.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/ChatMember.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/ChatPermissions.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/ChatPhoto.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/ChosenInlineResult.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/Contact.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/Dice.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/EncryptedCredentials.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/EncryptedPassportElement.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/File.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/ForceReply.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/Game.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/InlineKeyboardButton.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/InlineKeyboardMarkup.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/InlineQuery.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/InputMedia.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/InputMediaAnimation.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/InputMediaAudio.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/InputMediaVideo.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/Invoice.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/KeyboardButton.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/KeyboardButtonPollType.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/Location.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/LoginUrl.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/MaskPosition.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/Message.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/MessageAutoDeleteTimerChanged.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/MessageEntity.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/MessageId.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/OrderInfo.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/PassportData.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/PhotoSize.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/Poll.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/PollAnswer.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/PollOption.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/PreCheckoutQuery.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/ProximityAlertTriggered.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/ReplyKeyboardMarkup.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/ReplyKeyboardRemove.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/ResponseParameters.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/ShippingAddress.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/ShippingQuery.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/Sticker.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/StickerSet.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/SuccessfulPayment.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/Update.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/User.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/UserProfilePhotos.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/Venue.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/Video.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/VideoChatEnded.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/VideoChatParticipantsInvited.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/VideoChatScheduled.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/VideoNote.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/Voice.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/WebAppData.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/WebAppInfo.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/send/Send.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/send/SendAnimation.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/send/SendAudio.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/send/SendCaption.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/send/SendChatAction.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/send/SendContact.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/send/SendCoordinates.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/send/SendLocation.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/send/SendMessage.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/send/SendPhoto.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/send/SendPoll.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/send/SendText.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/send/SendVenue.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/send/SendVideo.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/send/SendVideoNote.java
- `M` chatbots-telegram-api/src/main/java/io/micronaut/chatbots/telegram/api/send/SendVoice.java
- `M` chatbots-telegram-core/src/main/java/io/micronaut/chatbots/telegram/core/CommandHandler.java
- `M` chatbots-telegram-core/src/main/java/io/micronaut/chatbots/telegram/core/DefaultTokenValidator.java
- `M` chatbots-telegram-core/src/main/java/io/micronaut/chatbots/telegram/core/ParseModeUtils.java
- `M` chatbots-telegram-core/src/main/java/io/micronaut/chatbots/telegram/core/SendMessageUtils.java
- `M` chatbots-telegram-core/src/main/java/io/micronaut/chatbots/telegram/core/TelegramBotConfiguration.java
- `M` chatbots-telegram-core/src/main/java/io/micronaut/chatbots/telegram/core/TelegramBotConfigurationProperties.java
- `M` chatbots-telegram-core/src/main/java/io/micronaut/chatbots/telegram/core/TelegramSlashCommandParser.java
- `M` chatbots-telegram-core/src/main/java/io/micronaut/chatbots/telegram/core/TelegramSpaceParser.java
- `M` chatbots-telegram-core/src/main/java/io/micronaut/chatbots/telegram/core/TokenValidator.java
- `M` chatbots-telegram-gcp-function/src/main/java/io/micronaut/chatbots/telegram/googlecloud/Handler.java
- `M` chatbots-telegram-lambda/src/main/java/io/micronaut/chatbots/telegram/lambda/Handler.java
- `M` config/checkstyle/checkstyle.xml

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/chatbots/basecamp/HelloWorldHandlerTest.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/chatbots/telegram/HelloWorldHandler.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/chatbots/telegram/HelloWorldHandlerTest.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/chatbots/telegram/UnknownCommandHandler.kt
- `M` test-suite/src/test/java/io/micronaut/chatbots/basecamp/AboutCommandHandler.java
- `M` test-suite/src/test/java/io/micronaut/chatbots/basecamp/HelloWorldHandler.java
- `M` test-suite/src/test/java/io/micronaut/chatbots/basecamp/UnknownCommandHandler.java
- `M` test-suite/src/test/java/io/micronaut/chatbots/telegram/AboutCommandHandler.java
- `M` test-suite/src/test/java/io/micronaut/chatbots/telegram/HelloWorldHandler.java
- `M` test-suite/src/test/java/io/micronaut/chatbots/telegram/UnknownCommandHandler.java

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

