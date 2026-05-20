Compared micronaut-views as mn4 -> mn5.

  Scope

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-views, branch 5.10.x, SHA b6d1a2400d07
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-views, branch 6.0.x, SHA b7c0cb80955a
  - Same remote, both clean: git@github.com:micronaut-projects/micronaut-views.git
  - Report: /private/tmp/micronaut-views-5.10-to-6.0-comparison.md

  Key Findings

  - Baseline moved to projectVersion 5.10.0-SNAPSHOT -> 6.0.1-SNAPSHOT, Micronaut 4.10.4 -> 5.0.0,
    Micronaut Platform 4.7.6 -> 5.0.0-RC1, Gradle 8.14.3 -> 9.5.1, with .sdkmanrc adding java=25.0.1-graal.
  - views-turbo is now its own module/dependency. Turbo classes moved out of views-core, and docs now
    require io.micronaut.views:micronaut-views-turbo.
  - Breaking docs call out @TurboView renamed to @TurboStreamView.
  - The global ViewsFilter was removed and replaced by ResponseFilter/body-swapper infrastructure plus
    RawModelAndViewMessageBodyHandler.
  - New micronaut.views.filter.enabled configuration controls the replacement views response filter.
  - ViewsModelDecorator and TurboStreamRenderer now carry generic model/request types, breaking binary
    compatibility; ViewModelProcessor also now takes a request type parameter.
  - Deprecated ThymeleafViewsRenderer.render(String, IContext, Writer) was removed; use render(String,
    Set<String>, IContext, Writer).
  - HTMX response rendering was updated to Micronaut 5 body writer APIs and now delegates through the raw
    ModelAndView handler.
  - Soy moved to 2023-09-13 -> 2024-02-26; rendering now uses TemplateName.of(...), and native/Graal
    support was expanded with Soy reflect config and test-suite initialization.
  - View engine dependencies changed: Handlebars 4.3.1 -> 4.5.0, JTE 3.2.1 -> 3.2.4, Thymeleaf
    3.1.3.RELEASE -> 3.1.5.RELEASE, Pebble 3.2.4 -> 4.1.1, Graal 24.2.2 -> 25.0.3.
  - Security model processing no longer relies on SecurityService; it reads authentication from the request
    attribute set by SecurityFilter.

  Diff size: 297 files changed, 6389 insertions(+), 1529 deletions(-).

  I did not run tests; this was a folder comparison and targeted source/build-diff review only.

# Release Note Comparison

Generated: 2026-05-19 16:58 UTC
Comparison: `5.10.x` -> `6.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-views` | `5.10.x` | `b6d1a2400d07` | `git@github.com:micronaut-projects/micronaut-views.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-views` | `6.0.x` | `b7c0cb80955a` | `git@github.com:micronaut-projects/micronaut-views.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-views`
- Commit candidates found: 130
- File changes listed: 297
- Version values listed: 60
- File status counts: A=56, D=3, M=212, R=26

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `5.10.0-SNAPSHOT` | `6.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.commons-lang3` | `org.apache.commons:commons-lang3:3.19.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.graal-js` | `org.graalvm.polyglot:js:24.2.2` | `org.graalvm.polyglot:js:25.0.3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.graal-polyglot` | `org.graalvm.polyglot:polyglot:24.2.2` | `org.graalvm.polyglot:polyglot:25.0.3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.kotlin-stdlib-jdk8` | `org.jetbrains.kotlin:kotlin-stdlib-jdk8:1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.kotlinx-coroutines-core` | `org.jetbrains.kotlinx:kotlinx-coroutines-core:1.9.0` | `org.jetbrains.kotlinx:kotlinx-coroutines-core:1.9.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-freemarker` | `org.freemarker:freemarker:2.3.34` | `org.freemarker:freemarker:2.3.34` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-handlebars` | `com.github.jknack:handlebars:4.3.1` | `com.github.jknack:handlebars:4.5.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-jstachio` | `io.jstach:jstachio:1.3.7` | `io.jstach:jstachio:1.3.7` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-jstachio-apt` | `io.jstach:jstachio-apt:1.3.7` | `io.jstach:jstachio-apt:1.3.7` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-jte` | `gg.jte:jte:3.2.1` | `gg.jte:jte:3.2.4` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-jte-kotlin` | `gg.jte:jte-kotlin:3.2.1` | `gg.jte:jte-kotlin:3.2.4` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-jte-native-resources` | `gg.jte:jte-native-resources:3.2.1` | `gg.jte:jte-native-resources:3.2.4` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-rocker-runtime` | `com.fizzed:rocker-runtime:1.4.0` | `com.fizzed:rocker-runtime:1.4.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-soy` | `com.google.template:soy:2023-09-13` | `com.google.template:soy:2024-02-26` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-thymeleaf` | `org.thymeleaf:thymeleaf:3.1.3.RELEASE` | `org.thymeleaf:thymeleaf:3.1.5.RELEASE` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-velocity-engine-core` | `org.apache.velocity:velocity-engine-core:2.4.1` | `org.apache.velocity:velocity-engine-core:2.4.1` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.micronaut-data` | `io.micronaut.data:micronaut-data-bom:4.13.7` | `io.micronaut.data:micronaut-data-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-graal` | `micronaut-graal:4.10.4` | `micronaut-graal:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-gradle-plugin` | `io.micronaut.gradle:micronaut-gradle-plugin:4.5.4` | `io.micronaut.gradle:micronaut-gradle-plugin:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-grpc` | `io.micronaut.grpc:micronaut-grpc-bom:4.12.0` | `io.micronaut.grpc:micronaut-grpc-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-logging` | `io.micronaut.logging:micronaut-logging-bom:1.7.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-reactor` | `not present` | `io.micronaut.reactor:micronaut-reactor-bom:4.0.0` | `added` |
| `gradle/libs.versions.toml` | `libraries.micronaut-security` | `io.micronaut.security:micronaut-security-bom:4.15.0` | `io.micronaut.security:micronaut-security-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.15.5` | `io.micronaut.serde:micronaut-serde-bom:3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-sql` | `io.micronaut.sql:micronaut-sql-bom:6.3.1` | `io.micronaut.sql:micronaut-sql-bom:7.0.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-validation` | `io.micronaut.validation:micronaut-validation-bom:4.11.0` | `io.micronaut.validation:micronaut-validation-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.org-json` | `org.json:json:20240303` | `org.json:json:20240303` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.pebble` | `io.pebbletemplates:pebble:3.2.4` | `io.pebbletemplates:pebble:4.1.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.thymeleaf-extras-java8time` | `org.thymeleaf.extras:thymeleaf-extras-java8time:3.0.4.RELEASE` | `org.thymeleaf.extras:thymeleaf-extras-java8time:3.0.4.RELEASE` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.commons-lang3` | `3.19.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.graal` | `24.2.2` | `25.0.3` | `changed` |
| `gradle/libs.versions.toml` | `versions.kotlin` | `1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.kotlinx-coroutines` | `1.9.0` | `1.9.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-freemarker` | `2.3.34` | `2.3.34` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-handlebars` | `4.3.1` | `4.5.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-jstachio` | `1.3.7` | `1.3.7` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-jte` | `3.2.1` | `3.2.4` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-rocker` | `1.4.0` | `1.4.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-soy` | `2023-09-13` | `2024-02-26` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-thymeleaf` | `3.1.3.RELEASE` | `3.1.5.RELEASE` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-velocity` | `2.4.1` | `2.4.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.4` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-data` | `4.13.7` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.5.4` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-grpc` | `4.12.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-platform` | `4.7.6` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-reactor` | `3.9.0` | `4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-security` | `4.15.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.15.5` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-sql` | `6.3.1` | `7.0.1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.9.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.11.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.org-json` | `20240303` | `20240303` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.pebble` | `3.2.4` | `4.1.1` | `changed` |
| `gradle/libs.versions.toml` | `versions.thymeleaf-extra-java8time` | `3.0.4.RELEASE` | `3.0.4.RELEASE` | `unchanged` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |
| `settings.gradle` | `plugin.io.micronaut.build.shared.settings` | `7.6.4` | `8.0.0-M18` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `80af7e875dbb` remove micronaut-test version (Sergio del Amo, 2026-05-18)
- `0269bc368e9b` remove @Deprecated (#974) (Sergio del Amo, 2025-02-10)
- `65f5315c0408` major: remove deprecated methods (#730) (Dean Wette, 2024-03-09)
- `d3a4368c5f65` major: Remove ViewsFilter, switch to MessageBodyWriters and extract Turbo module (#712) (Tim Yates, 2024-02-23)

### Fixes

- `d9e5dff7024d` fix(deps): update graal to v25.0.3 (#1114) (renovate[bot], 2026-05-09)
- `fba4ca554946` fix(deps): update micronaut dependencies (#1119) (renovate[bot], 2026-05-04)
- `2f1c096e097d` fix(deps): update managed.jte to v3.2.4 (#1118) (renovate[bot], 2026-05-04)
- `668cdb8bcfd2` fix(deps): update dependency org.thymeleaf:thymeleaf to v3.1.5.release (#1113) (renovate[bot], 2026-04-28)
- `b63c245b8e09` fix(deps): update micronaut to v5.0.0-M20 (#1110) (renovate[bot], 2026-04-03)
- `a562ab4f3d35` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m5 (#1109) (renovate[bot], 2026-03-28)
- `84fd4d34ef96` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m4 (#1108) (renovate[bot], 2026-03-26)
- `ef62feb602c7` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m3 (#1107) (renovate[bot], 2026-03-25)
- `238f4409584e` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v5.0.0-m5 (#1106) (renovate[bot], 2026-03-24)
- `b818f9a9d3a4` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v5.0.0-m4 (#1105) (renovate[bot], 2026-03-20)
- `cbc20cea9af5` fix(deps): update micronaut to v5.0.0-m17 (#1101) (renovate[bot], 2026-03-16)
- `efc40d6f3640` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v5.0.0-m3 (#1100) (renovate[bot], 2026-03-14)
- `e1446fc363b3` fix(deps): update micronaut to v5.0.0-m16 (#1099) (renovate[bot], 2026-03-07)
- `43036b6b8cdb` fix(deps): update micronaut to v5.0.0-m15 (#1096) (renovate[bot], 2026-03-03)
- `d35ba770a200` fix(deps): update micronaut to v5.0.0-m14 (#1094) (renovate[bot], 2026-02-27)
- `05fcc67fb87b` fix(deps): update micronaut to v5.0.0-m13 (#1093) (renovate[bot], 2026-02-22)
- `eb6da19aedf7` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v5.0.0-m2 (#1092) (renovate[bot], 2026-02-21)
- `4ed7c8b83af0` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to v7.0.0 (#1091) (renovate[bot], 2026-02-18)
- `1d9aded9b711` fix(deps): update dependency com.github.jknack:handlebars to v4.5.0 (#1088) (renovate[bot], 2026-02-16)
- `f8290e11d2af` fix(deps): update dependency io.micronaut.security:micronaut-security-bom to v4.17.0 (#1089) (renovate[bot], 2026-02-16)
- `ee40b4aaea1e` fix(deps): update managed.jte to v3.2.3 (#1087) (renovate[bot], 2026-02-14)
- `e5891b3e9222` fix(deps): update dependency io.pebbletemplates:pebble to v4.1.1 (#1053) (renovate[bot], 2026-02-11)
- `fd45b37b93b2` fix(deps): update managed.jstachio to v1.3.7 (#1058) (renovate[bot], 2026-02-11)
- `ea622bae04d5` fix(deps): update dependency io.micronaut.grpc:micronaut-grpc-bom to v4.12.0 (#1065) (renovate[bot], 2026-02-11)
- `3c9e81536781` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v4.14.3 (#1063) (renovate[bot], 2026-02-11)
- `44590a5f970d` fix(deps): update dependency io.micronaut.security:micronaut-security-bom to v4.16.1 (#1068) (renovate[bot], 2026-02-11)
- `0c73fdaed9cd` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to v6.3.3 (#1070) (renovate[bot], 2026-02-11)
- `cc4b4b5c5edb` fix(deps): update micronaut to v5.0.0-m10 (#1077) (renovate[bot], 2026-02-08)
- `4a3b9469f18b` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.2 (#1064) (renovate[bot], 2026-02-08)
- `21347a5bb08d` fix(deps): update managed.jte to v3.2.2 (#1076) (renovate[bot], 2026-02-04)
- `efd37479ecd5` fix(deps): update graal to v25.0.2 (#1075) (renovate[bot], 2026-02-04)
- `6b6acc71849c` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.3.6 (#760) (renovate[bot], 2024-04-11)
- `9bd0e4dd9e3b` fix(deps): update micronaut to v4.4.1 (#762) (renovate[bot], 2024-04-11)
- `c4ff22332e66` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v4.7.0 (#763) (renovate[bot], 2024-04-11)
- `f821d467f48f` fix(deps): update micronaut to v4.4.0 (#756) (renovate[bot], 2024-04-01)
- `16bbdee50e62` fix(deps): update dependency io.micronaut.security:micronaut-security-bom to v4.6.9 (#744) (renovate[bot], 2024-03-27)
- `f5296357afe9` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to v5.5.2 (#747) (renovate[bot], 2024-03-27)
- `def989afbaa0` fix(deps): update micronaut to v4.3.12 (#753) (renovate[bot], 2024-03-27)
- `e9e719313179` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.3.5 (#746) (renovate[bot], 2024-03-22)
- `b128604acbb0` fix(deps): update micronaut to v4.3.11 (#742) (renovate[bot], 2024-03-18)
- `c73948e35bd7` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.8.2 (#737) (renovate[bot], 2024-03-14)
- `ec7596c13a1a` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.4.4 (#725) (renovate[bot], 2024-03-13)
- `51698ca74c41` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.3.4 (#727) (renovate[bot], 2024-03-13)
- `d6eb8f5f94cc` fix(deps): update managed.jstachio to v1.3.5 (#729) (renovate[bot], 2024-03-13)
- `6d18af3eb45a` fix(deps): update dependency io.micronaut.security:micronaut-security-bom to v4.6.7 (#732) (renovate[bot], 2024-03-13)
- `6f5593d9199f` fix(deps): update micronaut to v4.3.10 (#733) (renovate[bot], 2024-03-13)
- `049499a85933` fix(deps): update dependency io.micronaut.security:micronaut-security-bom to v4.6.6 (#722) (renovate[bot], 2024-02-29)
- `25f312a1719d` fix(deps): update micronaut to v4.3.9 (#723) (renovate[bot], 2024-02-29)

### Security

- `1f566116fc8b` micronaut-security = "5.0.0-M1" (Sergio del Amo, 2026-02-16)
- `8f3854f52e2f` Fix generic type bound mismatch in MockAuthenticationProvider (#1081) (issam liqali, 2026-02-04)
- `6d85130cb6bd` Don't rely on SecurityService for the SecurityViewModelProcessor (#740) (Tim Yates, 2024-03-18)

### Dependency Updates

- `d68080a5b1b3` chore: Bump version to 6.0.1-SNAPSHOT (micronaut-build, 2026-05-19)
- `3cde4f033677` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2026-05-09)
- `43bf515559ef` chore(deps): update gradle to v9.4.1 (#1098) (renovate[bot], 2026-03-20)
- `95ce30607f4e` chore(deps): update plugin nu.studer.rocker to v3.3.1 (#1104) (renovate[bot], 2026-03-19)
- `fe854bb925ca` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2026-02-17)
- `8f37c69bb4e4` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#1090) (renovate[bot], 2026-02-17)
- `bde114cd2ce5` chore(deps): update dependency io.pebbletemplates:pebble to v4.1.1 (#1082) (renovate[bot], 2026-02-11)
- `4e34ea627d99` chore(deps): update plugin nu.studer.rocker to v3.3 (#1060) (renovate[bot], 2026-02-11)
- `7cc65139959c` chore(deps): update softprops/action-gh-release action to v2.5.0 (#1062) (renovate[bot], 2026-02-11)
- `dcd7c1c7f201` chore(deps): update actions/cache action to v5 (#1084) (renovate[bot], 2026-02-11)
- `23bd7f78979a` chore(deps): update actions/checkout action to v6 (#1085) (renovate[bot], 2026-02-11)
- `aa0c19d2c3d3` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m16 (#1073) (renovate[bot], 2026-02-10)
- `ecafeb6f1352` chore(deps): update graalvm/setup-graalvm action to v1.4.5 (#1072) (renovate[bot], 2026-02-04)
- `6a4c2d4fa5fe` chore(deps): update gradle to v9.2.0 (#1059) (renovate[bot], 2025-11-06)
- `34333c58bd61` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m9 (#1057) (renovate[bot], 2025-11-06)
- `91b7db3ba002` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#1056) (renovate[bot], 2025-11-06)
- `ccb9d0a12c7f` chore(deps): update gradle/gradle-build-action action to v3.2.1 (#761) (renovate[bot], 2024-04-11)
- `059d7f2cfb4c` chore(deps): update plugin io.micronaut.build.shared.settings to v6.7.0 (#741) (renovate[bot], 2024-03-15)
- `52ceef28afb1` chore(deps): update kotlin monorepo to v1.9.23 (#731) (renovate[bot], 2024-03-13)
- `eab5769a67ae` chore(deps): update graalvm/setup-graalvm action to v1.1.9 (#736) (renovate[bot], 2024-03-13)
- `c8b51fd54264` chore(deps): update plugin io.micronaut.build.shared.settings to v6.6.4 (#726) (renovate[bot], 2024-03-13)
- `b6f8caa16869` chore(deps): update graalvm/setup-graalvm action to v1.1.8 (#718) (renovate[bot], 2024-02-23)

### Internal

- `7c19d51acf28` build: apply build.internal.parent plugin (Sergio del Amo, 2026-02-17)

### Review Candidates

- `b7c0cb80955a` micronaut-data = "5.0.0" (Sergio del Amo, 2026-05-19)
- `cecbd6e465f9` Update common files (#1123) (micronaut-build, 2026-05-19)
- `bd8427e8aea6` [skip ci] Release v6.0.0 (micronaut-build, 2026-05-19)
- `e1ccfd49081c` graal: fix soy (Sergio del Amo, 2026-05-19)
- `9259aff434e5` ignore test in CI (Sergio del Amo, 2026-05-18)
- `d25485a16509` Update common files (#1121) (micronaut-build, 2026-05-18)
- `7a88eb785015` Update Gradle to v9.5.1 (#1122) (renovate[bot], 2026-05-18)
- `fcf9b5070b1c` Merge branch '5.10.x' into 6.0.x (Sergio del Amo, 2026-05-18)
- `7465150d670c` git: ignore /buildSrc/gradle.properties (Sergio del Amo, 2026-05-18)
- `1f7efe5c5f71` update versions (Sergio del Amo, 2026-05-18)
- `70ad94536525` Update versions (Sergio del Amo, 2026-05-14)
- `90b6ff52a44f` micronaut-platform = "5.0.0-RC1" (Sergio del Amo, 2026-05-13)
- `492a016b78af` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `90e8c2511805` [skip ci] Release v6.0.0-RC1 (micronaut-build, 2026-05-09)
- `8523a8ddf556` update to soy 2024-02-26 (Sergio del Amo, 2026-05-09)
- `f1200ddc722a` update versions (Sergio del Amo, 2026-05-09)
- `30fe23495291` Update common files (#1120) (micronaut-build, 2026-05-09)
- `01b40a09f64c` Update common files (#1117) (micronaut-build, 2026-05-04)
- `7d16fa18c207` [views] Update common files for branch 6.0.x (#1116) (micronaut-build, 2026-05-01)
- `d80b0e17845f` Update common files (#1103) (micronaut-build, 2026-04-26)
- `1377000e8f4e` Update common files (#1097) (micronaut-build, 2026-03-17)
- `b3f072d2b657` [skip ci] Release v6.0.0-M1 (micronaut-build, 2026-02-17)
- `794bf997e89b` revert to snapshot (Sergio del Amo, 2026-02-17)
- `c1c21223b5b9` don’t apply sonatype scan plugin. done by MN Build (Sergio del Amo, 2026-02-17)
- `9cc5a528daea` kotlin compilation (Sergio del Amo, 2026-02-16)
- `06c3e12a1263` everything is 21 compatible (Sergio del Amo, 2026-02-16)
- `af58ada683e7` micronaut-sql = "7.0.0-M6" (Sergio del Amo, 2026-02-16)
- `d501ceb58f49` micronaut-data = "5.0.0-M1" (Sergio del Amo, 2026-02-16)
- `04dd5dab85f5` [skip ci] Release v6.0.0-M1 (micronaut-build, 2026-02-12)
- `9d3e303706a5` Fix native build for jdk 25 (#1086) (issam liqali, 2026-02-11)
- `601d7ac54763` Update common files (#1061) (micronaut-build, 2026-02-11)
- `f63de9c562f5` don’t define jakarta-validation-api (Sergio del Amo, 2026-02-11)
- `8e47c0740b02` Update to Micronaut 5 (#1079) (issam liqali, 2026-02-03)
- `063ad6ef4cbc` Update common files (#1054) (micronaut-build, 2025-11-06)
- `64b69fa4bbc2` Update common files (#1052) (micronaut-build, 2025-10-17)
- `b3fe113eefb0` Micronaut Gradle build Plugin 8.0.0-M4 (Sergio del Amo, 2025-10-15)
- `192f2a47f865` gradle 9.1 (Sergio del Amo, 2025-10-15)
- `6525f39e5b15` Merge branch '5.7.x' into 6.0.x (Sergio del Amo, 2025-02-17)
- `39c63f94c8ce` Merge branch '6.0.x' into 6.0.x.origin (Sergio del Amo, 2025-02-10)
- `919f20dda20a` Revert "Revert "Update versions in 6.0.x branch (#972)"" (Sergio del Amo, 2025-02-10)
- `038fcb4c12c4` Merge branch 5.4.x into 6.0.x (#809) (Tim Yates, 2024-05-14)
- `2020dae2acb5` Merge branch '5.3.x' into 6.0.x (Sergio del Amo, 2024-04-19)
- `556a3ce0757d` Merge branch '5.3.x' into 6.0.x (Sergio del Amo, 2024-04-19)
- `ae97fd155ff0` Merge branch '5.3.x' into 6.0.x (Sergio del Amo, 2024-04-11)
- `a43be91b692f` javadoc: missing radio param (Sergio del Amo, 2024-04-11)
- `2074541f34ce` Merge branch '5.2.x' into 6.0.x (Sergio del Amo, 2024-04-11)
- `62019592db6f` Update common files (#755) (micronaut-build, 2024-03-28)
- `f9c70aefdde7` Update common files (#748) (micronaut-build, 2024-03-27)
- `18161e705ec0` HTMX Integration (#735) (Sergio del Amo, 2024-03-22)
- `70ca776e3fe9` Merge branch '5.2.x' (Sergio del Amo, 2024-03-21)
- `8f5f82e33a8c` Update to v6.7.0 of the build plugin (#739) (Tim Yates, 2024-03-14)
- `3d8c4249d34d` Update common files (#719) (micronaut-build, 2024-02-23)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` buildSrc/build.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.views-module.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.views-tests.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` settings.gradle
- `M` test-suite-graal/test-suite-graal-rocker/build.gradle
- `M` test-suite-groovy/build.gradle.kts
- `M` test-suite-http/build.gradle
- `M` test-suite-jte-fieldset/build.gradle.kts
- `M` test-suite-kotlin/build.gradle.kts
- `M` test-suite/build.gradle.kts
- `M` views-fieldset/build.gradle.kts
- `M` views-jte/build.gradle
- `M` views-rocker/build.gradle
- `A` views-turbo/build.gradle.kts
- `M` views-velocity/build.gradle

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
- `M` src/main/docs/guide/views/turbo.adoc
- `M` src/main/docs/guide/views/turbo/turboView.adoc
- `M` test-suite-groovy/src/test/groovy/io/micronaut/views/docs/turbo/TurboFrameTest.groovy
- `R093` test-suite-groovy/src/test/groovy/io/micronaut/views/docs/turbo/TurboStreamViewTest.groovy
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/views/docs/soy/AsyncController.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/views/docs/turbo/TurboFrameTest.kt
- `R094` test-suite-kotlin/src/test/kotlin/io/micronaut/views/docs/turbo/TurboStreamViewTest.kt
- `M` test-suite/src/test/java/io/micronaut/views/docs/htmx/HtmxTest.java
- `M` test-suite/src/test/java/io/micronaut/views/docs/turbo/TurboFrameBuilderTest.java
- `M` test-suite/src/test/java/io/micronaut/views/docs/turbo/TurboFrameTest.java
- `R092` test-suite/src/test/java/io/micronaut/views/docs/turbo/TurboStreamViewTest.java
- `M` views-freemarker/src/test/groovy/io/micronaut/docs/FreemarkerViewRendererSpec.groovy
- `M` views-handlebars/src/test/groovy/io/micronaut/docs/HandlebarsViewsRendererSpec.groovy
- `M` views-jte/src/test/groovy/io/micronaut/docs/BinaryJteViewRendererSpec.groovy
- `M` views-jte/src/test/groovy/io/micronaut/docs/JteController.groovy
- `M` views-jte/src/test/groovy/io/micronaut/docs/JteViewRendererSpec.groovy
- `M` views-pebble/src/test/groovy/io/micronaut/docs/PebbleViewsRendererSpec.groovy
- `M` views-rocker/src/test/groovy/io/micronaut/docs/RockerViewRendererSpec.groovy
- `M` views-soy/src/test/groovy/io/micronaut/docs/SoySauceViewRendererSpec.groovy
- `M` views-thymeleaf/src/test/groovy/io/micronaut/docs/ThymeleafViewRendererSpec.groovy
- `M` views-velocity/src/test/groovy/io/micronaut/docs/VelocityViewRendererSpec.groovy

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
- `M` views-core/src/main/java/io/micronaut/views/DefaultModelAndViewRenderer.java
- `M` views-core/src/main/java/io/micronaut/views/DefaultViewsModelDecorator.java
- `M` views-core/src/main/java/io/micronaut/views/DefaultViewsRendererLocator.java
- `M` views-core/src/main/java/io/micronaut/views/DefaultViewsResolver.java
- `M` views-core/src/main/java/io/micronaut/views/ModelAndView.java
- `M` views-core/src/main/java/io/micronaut/views/ModelAndViewRenderer.java
- `M` views-core/src/main/java/io/micronaut/views/Renderable.java
- `M` views-core/src/main/java/io/micronaut/views/TemplatedBuilder.java
- `M` views-core/src/main/java/io/micronaut/views/ViewUtils.java
- `D` views-core/src/main/java/io/micronaut/views/ViewsFilter.java
- `M` views-core/src/main/java/io/micronaut/views/ViewsModelDecorator.java
- `M` views-core/src/main/java/io/micronaut/views/ViewsRenderer.java
- `M` views-core/src/main/java/io/micronaut/views/ViewsRendererKey.java
- `M` views-core/src/main/java/io/micronaut/views/ViewsRendererLocator.java
- `M` views-core/src/main/java/io/micronaut/views/ViewsResolver.java
- `M` views-core/src/main/java/io/micronaut/views/csp/CspConfiguration.java
- `M` views-core/src/main/java/io/micronaut/views/csp/CspFilter.java
- `A` views-core/src/main/java/io/micronaut/views/http/CompositeResponseBodySwapper.java
- `A` views-core/src/main/java/io/micronaut/views/http/ModelAndViewResponseBodySwapper.java
- `A` views-core/src/main/java/io/micronaut/views/http/RawModelAndViewMessageBodyHandler.java
- `A` views-core/src/main/java/io/micronaut/views/http/ResponseBodySwap.java
- `A` views-core/src/main/java/io/micronaut/views/http/ResponseBodySwapper.java
- `A` views-core/src/main/java/io/micronaut/views/http/ResponseBodySwapperFilter.java
- `A` views-core/src/main/java/io/micronaut/views/http/ViewsFilterConfiguration.java
- `A` views-core/src/main/java/io/micronaut/views/http/package-info.java
- `M` views-core/src/main/java/io/micronaut/views/model/ViewModelProcessor.java
- `M` views-core/src/main/java/io/micronaut/views/model/security/CsrfViewModelProcessorConfiguration.java
- `M` views-core/src/main/java/io/micronaut/views/model/security/CsrfViewModelProcessorConfigurationProperties.java
- `M` views-core/src/main/java/io/micronaut/views/model/security/MapViewModelProcessor.java
- `M` views-core/src/main/java/io/micronaut/views/model/security/SecurityViewModelProcessor.java
- `M` views-core/src/main/java/io/micronaut/views/model/security/SecurityViewModelProcessorConfiguration.java
- `M` views-core/src/main/java/io/micronaut/views/model/security/SecurityViewModelProcessorConfigurationProperties.java
- `D` views-core/src/main/java/io/micronaut/views/turbo/DefaultTurboStreamRenderer.java
- `D` views-core/src/main/java/io/micronaut/views/turbo/TurboStreamFilter.java
- `M` views-fieldset-tck/src/main/java/io/micronaut/views/fields/tck/AsssertHtmlUtils.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/CsrfFieldsetConsumer.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/DefaultFieldGenerator.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/DefaultFormGenerator.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/Fieldset.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/FieldsetGenerator.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/Form.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/FormElement.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/FormGenerator.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/HtmlAttribute.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/constraints/EnctypePostRequiredValidator.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/elements/Checkbox.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/elements/FormElementAttributes.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/elements/GlobalAttributes.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/elements/InputCheckboxFormElement.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/elements/InputDateFormElement.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/elements/InputDateTimeLocalFormElement.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/elements/InputEmailFormElement.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/elements/InputFileFormElement.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/elements/InputFormElement.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/elements/InputHiddenFormElement.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/elements/InputNumberFormElement.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/elements/InputPasswordFormElement.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/elements/InputRadioFormElement.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/elements/InputStringFormBuilder.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/elements/InputStringFormElement.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/elements/InputSubmitFormElement.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/elements/InputTelFormElement.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/elements/InputTextFormElement.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/elements/InputTimeFormElement.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/elements/InputUrlFormElement.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/elements/Option.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/elements/Radio.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/elements/SelectFormElement.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/elements/TextareaFormElement.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/elements/TrixEditorFormElement.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/fetchers/CheckboxFetcher.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/fetchers/EnumCheckboxFetcher.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/fetchers/EnumOptionFetcher.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/fetchers/EnumRadioFetcher.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/fetchers/OptionFetcher.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/fetchers/RadioFetcher.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/formelementresolvers/DefaultFormElementResolver.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/formelementresolvers/FormElementResolver.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/messages/ConstraintViolationUtils.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/messages/LocalizedMessageResolver.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/messages/Message.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/messages/MessageResolver.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/render/FormElementRenderer.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/render/secondary/InputCheckboxFormElementRenderer.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/render/secondary/InputDateFormElementRenderer.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/render/secondary/InputDateTimeLocalFormElementRenderer.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/render/secondary/InputEmailFormElementRenderer.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/render/secondary/InputHiddenFormElementRenderer.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/render/secondary/InputNumberFormElementRenderer.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/render/secondary/InputPasswordFormElementRenderer.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/render/secondary/InputRadioFormElementRenderer.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/render/secondary/InputSubmitFormElementRenderer.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/render/secondary/InputTelFormElementRenderer.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/render/secondary/InputTextFormElementRenderer.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/render/secondary/InputTimeFormElementRenderer.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/render/secondary/InputUrlFormElementRenderer.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/render/secondary/OptionFormElementRenderer.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/render/secondary/SelectFormElementRenderer.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/render/views/FormElementRendererViewsConfiguration.java
- `M` views-fieldset/src/main/java/io/micronaut/views/fields/render/views/ViewsFormElementRenderer.java
- `M` views-freemarker/src/main/java/io/micronaut/views/freemarker/FreemarkerViewsRenderer.java
- `M` views-freemarker/src/main/java/io/micronaut/views/freemarker/FreemarkerViewsRendererConfigurationProperties.java
- `M` views-handlebars/src/main/java/io/micronaut/views/handlebars/HandlebarsViewsRenderer.java
- `M` views-htmx/src/main/java/io/micronaut/views/htmx/http/HtmxRequestHeaders.java
- `M` views-htmx/src/main/java/io/micronaut/views/htmx/http/HtmxRequestUtils.java
- `M` views-htmx/src/main/java/io/micronaut/views/htmx/http/HtmxResponse.java
- `M` views-htmx/src/main/java/io/micronaut/views/htmx/http/HtmxResponseRawMessageBodyHandler.java
- `M` views-jstachio/src/main/java/io/micronaut/views/jstachio/JStachioMessageBodyWriter.java
- `M` views-jte/src/main/java/io/micronaut/views/jte/HtmlJteViewsRenderer.java
- `M` views-jte/src/main/java/io/micronaut/views/jte/JteViewsRenderer.java
- `M` views-jte/src/main/java/io/micronaut/views/jte/PlainJteViewsRenderer.java
- `M` views-pebble/src/main/java/io/micronaut/views/pebble/PebbleEngineFactory.java
- `M` views-pebble/src/main/java/io/micronaut/views/pebble/PebbleLoader.java
- `M` views-pebble/src/main/java/io/micronaut/views/pebble/PebbleViewsRenderer.java
- `M` views-react/src/main/java/io/micronaut/views/react/ReactViewsRenderer.java
- `M` views-react/src/main/java/io/micronaut/views/react/ReactViewsRendererConfiguration.java
- `M` views-react/src/main/java/io/micronaut/views/react/util/OutputStreamToSLF4J.java
- `M` views-rocker/src/main/java/io/micronaut/views/rocker/RockerViewsRenderer.java
- `M` views-soy/src/main/java/io/micronaut/views/soy/SoyFileSetProvider.java
- `M` views-soy/src/main/java/io/micronaut/views/soy/SoyNamingMapProvider.java
- `M` views-soy/src/main/java/io/micronaut/views/soy/SoySauceViewsRenderer.java
- `M` views-soy/src/main/java/io/micronaut/views/soy/SoyViewsRendererConfiguration.java
- `M` views-soy/src/main/java/io/micronaut/views/soy/SoyViewsRendererConfigurationProperties.java
- `A` views-soy/src/main/resources/META-INF/native-image/io.micronaut.views/micronaut-views-soy/reflect-config.json
- `M` views-thymeleaf/src/main/java/io/micronaut/views/thymeleaf/LinkBuilder.java
- `M` views-thymeleaf/src/main/java/io/micronaut/views/thymeleaf/ThymeleafViewsRenderer.java
- `M` views-thymeleaf/src/main/java/io/micronaut/views/thymeleaf/WebContext.java
- `M` views-thymeleaf/src/main/java/io/micronaut/views/thymeleaf/WebEngineContext.java
- `R066` views-turbo/src/main/java/io/micronaut/views/turbo/AbstractTurboRenderer.java
- `R078` views-turbo/src/main/java/io/micronaut/views/turbo/DefaultTurboFrameRenderer.java
- `A` views-turbo/src/main/java/io/micronaut/views/turbo/DefaultTurboStreamRenderer.java
- `R093` views-turbo/src/main/java/io/micronaut/views/turbo/Loading.java
- `A` views-turbo/src/main/java/io/micronaut/views/turbo/TurboConfiguration.java
- `A` views-turbo/src/main/java/io/micronaut/views/turbo/TurboConfigurationProperties.java
- `R072` views-turbo/src/main/java/io/micronaut/views/turbo/TurboFrame.java
- `R088` views-turbo/src/main/java/io/micronaut/views/turbo/TurboFrameRenderer.java
- `R100` views-turbo/src/main/java/io/micronaut/views/turbo/TurboFrameView.java
- `R080` views-turbo/src/main/java/io/micronaut/views/turbo/TurboStream.java
- `R098` views-turbo/src/main/java/io/micronaut/views/turbo/TurboStreamAction.java
- `R078` views-turbo/src/main/java/io/micronaut/views/turbo/TurboStreamRenderer.java
- `R098` views-turbo/src/main/java/io/micronaut/views/turbo/TurboStreamView.java
- `R093` views-turbo/src/main/java/io/micronaut/views/turbo/VisitAction.java
- `R100` views-turbo/src/main/java/io/micronaut/views/turbo/http/TurboHttpHeaders.java
- `R088` views-turbo/src/main/java/io/micronaut/views/turbo/http/TurboMediaType.java
- `A` views-turbo/src/main/java/io/micronaut/views/turbo/http/bodyswapper/TurboFrameResponseBodySwapper.java
- `A` views-turbo/src/main/java/io/micronaut/views/turbo/http/bodyswapper/TurboStreamResponseBodySwapper.java
- `A` views-turbo/src/main/java/io/micronaut/views/turbo/http/bodyswapper/package-info.java
- `A` views-turbo/src/main/java/io/micronaut/views/turbo/http/bodywriter/TurboFrameBuilderHtmlMessageBodyWriter.java
- `R081` views-turbo/src/main/java/io/micronaut/views/turbo/http/bodywriter/TurboStreamBuilderMessageBodyWriter.java
- `R080` views-turbo/src/main/java/io/micronaut/views/turbo/http/bodywriter/TurboStreamListOfBuilderMessageBodyWriter.java
- `R088` views-turbo/src/main/java/io/micronaut/views/turbo/http/bodywriter/TurboStreamMessageBodyWriter.java
- `R081` views-turbo/src/main/java/io/micronaut/views/turbo/http/bodywriter/package-info.java
- `A` views-turbo/src/main/java/io/micronaut/views/turbo/http/package-info.java
- `R082` views-turbo/src/main/java/io/micronaut/views/turbo/package-info.java
- `M` views-velocity/src/main/java/io/micronaut/views/velocity/VelocityViewsRenderer.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` test-suite-csrf/src/test/java/io/micronaut/views/tests/security/csrf/CsrfFormGenerationTest.java
- `M` test-suite-csrf/src/test/java/io/micronaut/views/tests/security/csrf/CsrfSessionLogingHandlerTest.java
- `M` test-suite-graal/test-suite-graal-soy/src/main/java/example/micronaut/CompiledTemplatesProvider.java
- `A` test-suite-graal/test-suite-graal-soy/src/main/java/example/micronaut/SoyTemplateBuildTimeInitializer.java
- `A` test-suite-graal/test-suite-graal-soy/src/main/resources/META-INF/native-image/soy-test-only/native-image.properties
- `M` test-suite-graal/test-suite-graal-soy/src/main/resources/META-INF/native-image/soy-test-only/reflect-config.json
- `M` test-suite-groovy/src/test/groovy/io/micronaut/views/ModelAndViewSpec.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/views/model/ConfigViewModelProcessor.groovy
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/views/ModelAndViewTest.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/views/NonHTMLViewRendererTest.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/views/UnmodifiableModelAndViewTest.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/views/model/ConfigViewModelProcessor.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/views/model/security/MockAuthenticationProvider.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/views/model/security/SecurityViewModelProcessorTest.kt
- `M` test-suite-thymeleaf-fieldset/src/test/java/io/micronaut/views/fields/thymeleaf/Author.java
- `M` test-suite-thymeleaf-fieldset/src/test/java/io/micronaut/views/fields/thymeleaf/Book.java
- `M` test-suite/src/test/java/io/micronaut/views/ModelAndViewTest.java
- `M` test-suite/src/test/java/io/micronaut/views/NonHTMLViewRendererTest.java
- `M` test-suite/src/test/java/io/micronaut/views/UnmodifiableModelAndViewTest.java
- `M` test-suite/src/test/java/io/micronaut/views/model/ConfigViewModelProcessor.java
- `M` test-suite/src/test/java/io/micronaut/views/model/security/MockAuthenticationProvider.java
- `A` views-core/src/test/groovy/io/micronaut/views/MediaTypeParseSpec.groovy
- `A` views-core/src/test/groovy/io/micronaut/views/http/FilterSpec.groovy
- `M` views-fieldset-tck/src/main/java/io/micronaut/views/fields/tck/FormDataTurboRenderTest.java
- `M` views-fieldset-tck/src/main/java/io/micronaut/views/fields/tck/InputCheckboxViewRenderTest.java
- `M` views-fieldset-tck/src/main/java/io/micronaut/views/fields/tck/InputEmailViewRenderTest.java
- `M` views-fieldset-tck/src/main/java/io/micronaut/views/fields/tck/InputHiddenViewRenderTest.java
- `M` views-fieldset-tck/src/main/java/io/micronaut/views/fields/tck/InputTelViewRenderTest.java
- `M` views-fieldset-tck/src/main/java/io/micronaut/views/fields/tck/InputTextViewRenderTest.java
- `M` views-fieldset-tck/src/main/java/io/micronaut/views/fields/tck/InputUrlViewRenderTest.java
- `M` views-fieldset-tck/src/main/java/io/micronaut/views/fields/tck/render/InputDateFormElementRendererTest.java
- `M` views-fieldset-tck/src/main/java/io/micronaut/views/fields/tck/render/OptionFormElementRenderTest.java
- `M` views-fieldset/src/test/java/io/micronaut/views/fields/FieldGeneratorTest.java
- `M` views-fieldset/src/test/java/io/micronaut/views/fields/formsexamples/AutomaticallyPopulatedTest.java
- `M` views-fieldset/src/test/java/io/micronaut/views/fields/formsexamples/EventCreateFormTest.java
- `M` views-fieldset/src/test/java/io/micronaut/views/fields/formsexamples/LoginFormTest.java
- `M` views-fieldset/src/test/java/io/micronaut/views/fields/formsexamples/SaveBoxOfficeClerkFormTest.java
- `M` views-fieldset/src/test/java/io/micronaut/views/fields/formsexamples/SignupFormTest.java
- `M` views-fieldset/src/test/java/io/micronaut/views/fields/messages/MessageTest.java
- `M` views-htmx/src/test/java/io/micronaut/views/htmx/http/HtmxRequestHeadersTypedRequestArgumentBinderTest.java
- `M` views-jstachio/src/test/java/io/micronaut/views/jstachio/PersonMessageBodyWriter.java
- `M` views-jstachio/src/test/java/io/micronaut/views/jstachio/clazz/HomeController.java
- `M` views-jstachio/src/test/java/io/micronaut/views/jstachio/clazz/HomeModel.java
- `M` views-jstachio/src/test/java/io/micronaut/views/jstachio/pkginfo/HomeModel.java
- `M` views-react/src/main/java/io/micronaut/views/react/truffle/IntrospectableToTruffleAdapter.java
- `M` views-react/src/test/java/io/micronaut/views/react/SomeBean.java
- `A` views-turbo/src/test/groovy/io/micronaut/views/TurboDisableSpec.groovy
- `R100` views-turbo/src/test/groovy/io/micronaut/views/turbo/LoadingSpec.groovy
- `A` views-turbo/src/test/groovy/io/micronaut/views/turbo/ResponseBodySwapperSpec.groovy
- `A` views-turbo/src/test/groovy/io/micronaut/views/turbo/TurboFrameRendererSpec.groovy
- `R065` views-turbo/src/test/groovy/io/micronaut/views/turbo/TurboFrameSpec.groovy
- `R100` views-turbo/src/test/groovy/io/micronaut/views/turbo/TurboStreamActionSpec.groovy
- `A` views-turbo/src/test/groovy/io/micronaut/views/turbo/TurboStreamRendererSpec.groovy
- `R093` views-turbo/src/test/groovy/io/micronaut/views/turbo/TurboStreamSpec.groovy
- `R100` views-turbo/src/test/groovy/io/micronaut/views/turbo/VisitActionSpec.groovy
- `A` views-turbo/src/test/groovy/io/micronaut/views/turbo/http/bodywriter/TurboFrameBuilderHtmlMessageBodyWriterSpec.groovy
- `A` views-turbo/src/test/groovy/io/micronaut/views/turbo/http/bodywriter/TurboStreamBuilderMessageBodyWriterSpec.groovy
- `A` views-turbo/src/test/groovy/io/micronaut/views/turbo/http/bodywriter/TurboStreamListOfBuilderMessageBodyWriterSpec.groovy
- `A` views-turbo/src/test/groovy/io/micronaut/views/turbo/http/bodywriter/TurboStreamMessageBodyWriterSpec.groovy
- `A` views-turbo/src/test/resources/logback.xml

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

