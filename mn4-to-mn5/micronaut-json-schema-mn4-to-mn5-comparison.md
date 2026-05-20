# Release Note Comparison

Generated: 2026-05-06 13:59 UTC
Comparison: `mn4` -> `mn5`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-json-schema` | `1.8.x` | `4f3e0af862c2` | `git@github.com:micronaut-projects/micronaut-json-schema.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-json-schema` | `2.0.x` | `33d50ad74265` | `git@github.com:micronaut-projects/micronaut-json-schema.git` | `True` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-json-schema`
- Commit candidates found: 139
- File changes listed: 245
- Version values listed: 27
- File status counts: A=183, M=62

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `1.8.0-SNAPSHOT` | `2.0.0-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.java-parser` | `com.github.javaparser:javaparser-core:3.27.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.managed-json-schema-validator` | `com.networknt:json-schema-validator:1.5.8` | `com.networknt:json-schema-validator:3.0.2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-logging` | `io.micronaut.logging:micronaut-logging-bom:1.7.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.15.5` | `io.micronaut.serde:micronaut-serde-bom:3.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-sourcegen` | `io.micronaut.sourcegen:micronaut-sourcegen-bom:1.8.2` | `io.micronaut.sourcegen:micronaut-sourcegen-bom:2.0.0-M3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-sql-jdbc-hikari` | `not present` | `io.micronaut.sql:micronaut-jdbc-hikari:7.0.1-M2` | `added` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test` | `io.micronaut.test:micronaut-test-bom:4.9.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-toml` | `not present` | `io.micronaut.toml:micronaut-toml:3.0.0-M2` | `added` |
| `gradle/libs.versions.toml` | `libraries.micronaut-validation` | `io.micronaut.validation:micronaut-validation-bom:4.11.0` | `io.micronaut.validation:micronaut-validation-bom:5.0.0-M2` | `changed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.24` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.java-parser` | `3.27.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.kotlin` | `1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.ksp` | `1.9.25-1.0.20` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.managed-json-schema-validator` | `1.5.8` | `3.0.2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.4` | `5.0.0-RC2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `2.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.15.5` | `3.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-sourcegen` | `1.8.2` | `2.0.0-M3` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-sql` | `not present` | `7.0.1-M2` | `added` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.9.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-toml` | `not present` | `3.0.0-M2` | `added` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.11.0` | `5.0.0-M2` | `changed` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.0` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `87346fff88fb` checkstyle: remove * imports (Sergio del Amo, 2026-05-05)
- `c6df62563ba3` Fix docs build: remove invalid EndpointConfiguration include (#291) (Graeme Rocher, 2026-02-12)

### Features

- `524583b65f82` Add micronaut.processing to default suppressions (Graeme Rocher, 2026-04-30)
- `409414fda662` Add default test resources suppression pattern (Graeme Rocher, 2026-04-28)
- `9289ef039ee3` add junit platform launcher (#317) (Issam Liqali, 2026-03-17)
- `d4e88f2a3cff` feat: add DI validation strategies and refresh schema fixtures (#303) (Graeme Rocher, 2026-03-05)
- `bfc21db3913a` feat: add metadata-based dependency injection validation and reporting (#297) (Graeme Rocher, 2026-03-03)
- `0fcb6fee7f33` Support for validating Micronaut Configuration with JSON Schema (#283) (Graeme Rocher, 2026-02-12)

### Fixes

- `64c73f5b9f8c` test: add regression coverage for issue #322 (#338) (Graeme Rocher, 2026-04-20)
- `421fc70691a4` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m5 (#336) (renovate[bot], 2026-03-28)
- `b1d245002e26` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m4 (#334) (renovate[bot], 2026-03-27)
- `16d6339beeaf` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m3 (#332) (renovate[bot], 2026-03-25)
- `c79fee62814a` fix(deps): update dependency io.micronaut.sql:micronaut-jdbc-hikari to v7.0.0 (renovate[bot], 2026-03-19)
- `d6b76bf66991` fix(deps): update dependency io.micronaut.sql:micronaut-jdbc-hikari to v7.0.0 (#320) (renovate[bot], 2026-03-18)
- `86be6b577b59` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m17 (#310) (renovate[bot], 2026-03-16)
- `56e6730e3eb9` fix: honor schema defaults for required config properties (#308) (Graeme Rocher, 2026-03-13)
- `1a863479f691` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m16 (#306) (renovate[bot], 2026-03-07)
- `5d0cc19311a4` fix(deps): update dependency io.micronaut.toml:micronaut-toml to v2.8.0 (#292) (renovate[bot], 2026-03-03)
- `d57a3d22add8` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m15 (#302) (renovate[bot], 2026-03-03)
- `2796a105c117` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m14 (#299) (renovate[bot], 2026-02-28)
- `3bba5de4248a` fix(deps): update dependency io.micronaut.sourcegen:micronaut-sourcegen-bom to v2.0.0-m2 (#296) (renovate[bot], 2026-02-22)
- `9ee9996c0dd7` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m13 (#295) (renovate[bot], 2026-02-21)
- `69f55418b56d` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m12 (#294) (renovate[bot], 2026-02-20)
- `f995a43c7358` fix(deps): update dependency com.github.javaparser:javaparser-core to v3.28.0 (#275) (renovate[bot], 2026-02-10)
- `eb8d58d57625` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m9 (#280) (renovate[bot], 2026-01-24)
- `e06fd009ed25` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m2 (#277) (renovate[bot], 2026-01-14)
- `8436104fab58` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m8 (#276) (renovate[bot], 2026-01-13)
- `872b911be56f` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m7 (#274) (renovate[bot], 2026-01-11)
- `e69c0b3cbf0f` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.12 (#259) (renovate[bot], 2026-01-07)
- `93f1a376ed66` fix(deps): update dependency io.micronaut.sourcegen:micronaut-sourcegen-bom to v1.8.3 (#262) (renovate[bot], 2026-01-07)
- `bcee930e8d74` fix(deps): update dependency io.micronaut.test:micronaut-test-bom to v4.10.2 (#243) (renovate[bot], 2025-12-10)
- `2f784bd065c0` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.12.0 (#247) (renovate[bot], 2025-12-10)
- `d1450cca240c` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#246) (renovate[bot], 2025-12-10)
- `ac4b3737cb5e` fix(deps): update dependency io.micronaut.logging:micronaut-logging-bom to v1.7.1 (#242) (renovate[bot], 2025-12-10)
- `3608842c5302` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#240) (renovate[bot], 2025-12-10)
- `c7d82536ce83` fix(deps): update dependency com.networknt:json-schema-validator to v1.5.9 (#232) (renovate[bot], 2025-12-10)

### Dependency Updates

- `63d7f12e8d43` chore: Bump version to 2.0.0-SNAPSHOT (micronaut-build, 2026-05-05)
- `a799984b0f67` chore: Bump version to 2.0.0-SNAPSHOT (micronaut-build, 2026-04-30)
- `6eae3fea0504` Merge pull request #350 from micronaut-projects/renovate/micronaut-dependencies (Graeme Rocher, 2026-04-30)
- `302513d3ae88` Update Micronaut dependencies (renovate[bot], 2026-04-29)
- `6ba31816e76e` chore: Bump version to 2.0.0-SNAPSHOT (micronaut-build, 2026-04-28)
- `1f3ce84eb72c` Update Micronaut dependencies (#348) (renovate[bot], 2026-04-24)
- `d75841d68cdd` chore: Bump version to 2.0.0-SNAPSHOT (micronaut-build, 2026-04-24)
- `89290e4594af` chore: Bump version to 2.0.0-SNAPSHOT (micronaut-build, 2026-04-20)
- `ec9cb72f5acc` Update dependency com.networknt:json-schema-validator to v3.0.2 (#340) (renovate[bot], 2026-04-17)
- `f65b49b4e73a` chore: Bump version to 2.0.0-SNAPSHOT (micronaut-build, 2026-03-27)
- `40e97d63fa47` Bump micronaut-sql version to 7.0.1-M1 (Radovan Radic, 2026-03-24)
- `8a599b40e0c1` chore: Bump version to 2.0.0-SNAPSHOT (micronaut-build, 2026-03-24)
- `d59b43b6c0d9` chore(deps): update gradle/actions action to v6 (#331) (renovate[bot], 2026-03-24)
- `f7940ad902ab` chore: Bump version to 2.0.0-SNAPSHOT (micronaut-build, 2026-03-20)
- `34560076d54e` chore(deps): update gradle to v9.4.1 (#304) (renovate[bot], 2026-03-20)
- `7b08504857bb` chore: Bump version to 2.0.0-SNAPSHOT (micronaut-build, 2026-03-17)
- `a468146b8fcb` chore(deps): update softprops/action-gh-release action to v2.6.1 (#312) (renovate[bot], 2026-03-17)
- `fde8292671f9` chore: Bump version to 2.0.0-SNAPSHOT (micronaut-build, 2026-03-13)
- `e7836f88c410` chore: Bump version to 2.0.0-SNAPSHOT (micronaut-build, 2026-03-03)
- `d1caf93f56d5` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#293) (renovate[bot], 2026-02-17)
- `1568cc86a079` chore(deps): update gradle to v9.3.1 (#278) (renovate[bot], 2026-02-10)
- `3cf081c569a5` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m16 (#285) (renovate[bot], 2026-02-10)
- `30a7e56d3060` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m15 (#281) (renovate[bot], 2026-01-31)
- `2442cfde2537` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m14 (#272) (renovate[bot], 2026-01-10)
- `60c2969d8251` chore: Bump version to 2.0.0-SNAPSHOT (micronaut-build, 2026-01-09)
- `03c1310aab49` chore(deps): update dependency com.google.devtools.ksp to v2.3.4 (#260) (renovate[bot], 2026-01-07)
- `99755a92188a` chore(deps): update kotlin monorepo to v2.3.0 (#263) (renovate[bot], 2026-01-07)
- `8bf71f1d426e` chore(deps): update actions/cache action to v5 (#265) (renovate[bot], 2026-01-07)
- `319b39c0fc26` chore(deps): update github artifact actions (#267) (renovate[bot], 2026-01-07)
- `f57b4b5cdead` chore(deps): update peter-evans/create-pull-request action to v8 (#268) (renovate[bot], 2026-01-07)
- `99a9673df92e` chore(deps): update graalvm/setup-graalvm action to v1.4.5 (#269) (renovate[bot], 2026-01-07)
- `2b12818cd8f4` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m13 (#261) (renovate[bot], 2026-01-07)
- `ed89c2b701ec` chore(deps): update gradle/actions action to v5 (#250) (renovate[bot], 2025-12-10)
- `c585d1f572fa` chore(deps): update actions/checkout action (#248) (renovate[bot], 2025-12-10)
- `c94fa2c6637c` chore(deps): update gradle to v9.2.1 (#245) (renovate[bot], 2025-12-10)
- `b4c743c76fc6` chore(deps): update dependency com.google.devtools.ksp to v2.3.3 (#244) (renovate[bot], 2025-12-10)
- `e2604d90c521` chore(deps): update softprops/action-gh-release action to v2.5.0 (#241) (renovate[bot], 2025-12-10)
- `2850cfeacdd7` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#238) (renovate[bot], 2025-12-10)
- `a15dbb70c9d7` chore(deps): update stefanzweifel/git-auto-commit-action action to v7 (#253) (renovate[bot], 2025-12-10)
- `2daea56a66d8` chore(deps): update kotlin monorepo to v2.2.21 (#236) (renovate[bot], 2025-11-03)
- `93673ff853d7` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#234) (renovate[bot], 2025-11-03)
- `160013a12f90` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m8 (#237) (renovate[bot], 2025-11-03)
- `4f62b8196026` Update ksp version to 2.2.20-2.0.4 (#231) (Sergio del Amo, 2025-10-16)

### Documentation

- `74077daf5bf7` Docs: update micronaut-docs to 3.0.0 (#227) (issam liqali, 2025-10-16)

### Internal

- `6708d262c887` Build: Update to micronaut 5 (#266) (issam liqali, 2026-01-09)
- `53ed90d318b3` build: micronaut build plugin 8.0.0-M4 (Sergio del Amo, 2025-10-13)
- `5ed79bc321fa` ci: projectVersion=2.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-10-13)

### Review Candidates

- `33d50ad74265` micronaut = "5.0.0-RC2” (Sergio del Amo, 2026-05-06)
- `f37a89d647c2` Update common files (#352) (micronaut-build, 2026-05-06)
- `ebc0c660eff2` [skip ci] Release v2.0.0-RC1 (micronaut-build, 2026-05-05)
- `fcb93bbd7e27` supress warnings method name and parameter name (Sergio del Amo, 2026-05-05)
- `154116832f2e` use java parser from core (Sergio del Amo, 2026-05-05)
- `5255958eb0a3` toml 3.0.0-M2 (Sergio del Amo, 2026-05-05)
- `31ea076c8519` micronaut-sourcegen = "2.0.0-M3" (Sergio del Amo, 2026-05-05)
- `e49d7b50e7e8` micronaut-serde = "3.0.0-RC1" (Sergio del Amo, 2026-05-05)
- `8e6c3c9cfee6` micronaut = "5.0.0-RC1" (Sergio del Amo, 2026-05-05)
- `3aba7d283de6` Update common files (#347) (micronaut-build, 2026-05-05)
- `b8441b8e4d9a` [skip ci] Release v2.0.0-M12 (micronaut-build, 2026-04-30)
- `24b63d5584d3` Merge pull request #351 from micronaut-projects/micronaut-processing-supression (Graeme Rocher, 2026-04-30)
- `0e3ee0f8fec9` [skip ci] Release v2.0.0-M11 (micronaut-build, 2026-04-28)
- `f4ce30d54ee1` Merge pull request #349 from micronaut-projects/test-resources-supressions (Graeme Rocher, 2026-04-28)
- `cc221f4fe359` [skip ci] Release v2.0.0-M10 (micronaut-build, 2026-04-24)
- `5d60183bb22e` Update to Micronaut 5.0.0-M24 (#346) (Sergio del Amo, 2026-04-24)
- `98b0c2a0becd` [json-schema] Update common files for branch 2.0.x (#321) (micronaut-build, 2026-04-24)
- `1b63308fd15b` [skip ci] Release v2.0.0-M9 (micronaut-build, 2026-04-20)
- `0c614bd827eb` Handle default configuration suppressions silently (#343) (Graeme Rocher, 2026-04-20)
- `48f451a7a637` Merge pull request #325 from micronaut-projects/renovate/micronaut.sql (Graeme Rocher, 2026-04-17)
- `328d6cd221df` Revert "Fix generated schema classpath discovery" (Graeme Rocher, 2026-04-13)
- `8f16f64e4b73` Revert "Embed generated schemas for classpath loading" (Graeme Rocher, 2026-04-13)
- `403958fcf9c6` Merge pull request #339 from micronaut-projects/fix-264-generated-schema-loader (Graeme Rocher, 2026-04-13)
- `9eda6f6373b8` Embed generated schemas for classpath loading (Graeme Rocher, 2026-04-13)
- `4cb870b37690` Fix generated schema classpath discovery (Graeme Rocher, 2026-04-13)
- `771c6854eb87` Update to micronaut M20 (#337) (Issam Liqali, 2026-04-07)
- `79376bc16f83` [skip ci] Release v2.0.0-M8 (micronaut-build, 2026-03-27)
- `4c908ed410d3` Ensure datasource suppressions are always applied (#335) (Graeme Rocher, 2026-03-27)
- `f9672a563ac4` [skip ci] Release v2.0.0-M7 (micronaut-build, 2026-03-24)
- `506dcef9352c` Fix DI validation discovery and default suppressions (#330) (Graeme Rocher, 2026-03-24)
- `a4f9302c2ed0` Handle unresolved placeholders gracefully in configuration validator (#328) (Copilot, 2026-03-23)
- `b0ef20edd065` [skip ci] Release v2.0.0-M6 (micronaut-build, 2026-03-20)
- `d2621b456862` Update to json-schema-validator 3.0.1 (#323) (Issam Liqali, 2026-03-20)
- `e91504f2a20c` update to micronaut sql 7.0.0-M8 (#324) (Issam Liqali, 2026-03-19)
- `b9903adacbd5` [skip ci] Release v2.0.0-M5 (micronaut-build, 2026-03-17)
- `8d1c0560a3f6` Fix datasource false positives for overlapping each-property schemas (#319) (Graeme Rocher, 2026-03-17)
- `28b86ad50278` Fix NullPointerException when using @JsonUnwrapped in JSON schema generation (#309) (Copilot, 2026-03-17)
- `59de5cdb3b46` Fix auto.test.resources placeholder resolution in config validator (#318) (Graeme Rocher, 2026-03-17)
- `c60b0b13cc5e` Update common files (#313) (micronaut-build, 2026-03-17)
- `829a0fed0845` use suppressions.xml (#311) (Issam Liqali, 2026-03-17)
- `40a4cb18763a` [json-schema] Update common files for branch 2.0.x (#286) (micronaut-build, 2026-03-16)
- `b312c22ca8f8` [skip ci] Release v2.0.0-M4 (micronaut-build, 2026-03-13)
- `25baefbfee4c` [skip ci] Release v2.0.0-M3 (micronaut-build, 2026-03-03)
- `1654979eb891` [skip ci] Release v2.0.0-M2 (micronaut-build, 2026-02-12)
- `f7d155fc9bae` [json-schema] Update common files for branch 2.0.x (#273) (micronaut-build, 2026-02-10)
- `474d59f452fe` Improve support for JSON schema loading (#282) (Graeme Rocher, 2026-02-06)
- `ba0e388a53ce` [skip ci] Release v2.0.0-M1 (micronaut-build, 2026-01-09)
- `04f5af3f46b9` Merge branch '1.8.x' into 2.0.x (Sergio del Amo, 2026-01-09)
- `3b6cc3670a7f` [json-schema] Update common files for branch 2.0.x (#258) (micronaut-build, 2026-01-07)
- `61f2393a146a` [json-schema] Update common files for branch 2.0.x (#239) (micronaut-build, 2025-12-10)
- `bec95ad3872b` Replace Micronaut nullability annotations with JSpecify nullability annotations (#256) (Copilot, 2025-12-01)
- `b1270e2714b2` Micronaut 5 compatibility (#235) (issam liqali, 2025-11-03)
- `6bd7d532ffb2` [json-schema] Update common files for branch 2.0.x (#233) (micronaut-build, 2025-11-03)
- `8aab87cae5c1` [json-schema] Update common files for branch 2.0.x (#228) (micronaut-build, 2025-10-16)
- `93fbfadf5b16` build micronaut-json-schema with gradle 9.1.0 (#230) (araysse, 2025-10-16)
- `ee109764cdef` gradle 9.1.0 (Sergio del Amo, 2025-10-13)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` .github/workflows/update-gradle-wrapper.yml
- `M` buildSrc/build.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` json-schema-annotations/build.gradle
- `M` json-schema-common/build.gradle
- `A` json-schema-configuration-validator/build.gradle.kts
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/DefaultDependencyInjectionErrors.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/DefaultDependencyInjectionValidator.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/DependencyInjectionError.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/DependencyInjectionErrors.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/DependencyInjectionValidationStrategy.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/DependencyInjectionValidator.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/cli/DependencyInjectionConfigurationValidator.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/DependencyInjectionConfigurationValidatorConfigurerTest.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/DependencyInjectionValidatorTest.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureConditionalDependency.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureMissingDependency.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureNestedDependencyA.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureNestedDependencyB.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/TestDependencyInjectionApplicationContextConfigurer.java
- `M` json-schema-generator/build.gradle
- `M` json-schema-processor/build.gradle
- `M` json-schema-utils/build.gradle.kts
- `M` json-schema-validation/build.gradle.kts
- `M` settings.gradle
- `M` test-suite-generator-java/build.gradle
- `M` test-suite-groovy/build.gradle
- `M` test-suite-kotlin/build.gradle
- `M` test-suite/build.gradle

### Documentation

- `A` .agents/skills/docs/SKILL.md
- `A` .agents/skills/docs/references/control-panel-patterns.md
- `A` .agents/skills/docs/references/micronaut-docs-providers.md
- `M` .github/workflows/release.yml
- `M` json-schema-processor/src/main/java/io/micronaut/jsonschema/visitor/aggregator/DocumentationInfoAggregator.java
- `A` src/main/docs/guide/configurationValidator.adoc
- `M` src/main/docs/guide/introduction.adoc
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
- `M` .github/workflows/files-sync.yml
- `M` .github/workflows/graalvm-dev.yml
- `M` .github/workflows/publish-snapshot.yml
- `A` .github/workflows/sonatype.yml
- `M` .gitignore
- `A` .sdkmanrc
- `M` MAINTAINING.md
- `M` config/checkstyle/checkstyle.xml
- `M` config/checkstyle/suppressions.xml
- `M` json-schema-common/src/main/java/io/micronaut/jsonschema/model/Schema.java
- `M` json-schema-common/src/main/java/io/micronaut/jsonschema/model/TypeListSerializer.java
- `M` json-schema-common/src/main/java/io/micronaut/jsonschema/serialization/JsonSchemaMapperFactory.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/ConfigurationError.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/ConfigurationErrors.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/ConfigurationJsonSchemaValidator.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/ConfigurationRule.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/ConfigurationRules.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/ConfigurationSchemaPropertyAdapter.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/ConfigurationValidationContext.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/ConfigurationValidator.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/ConfigurationValidatorConfiguration.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/ConfigurationValidatorFactory.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/DefaultConfigurationErrors.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/HealthConfiguration.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/JsonPointer.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/NestedPropertyMapBuilder.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/SchemaContext.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/SchemaTypes.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/SchemaValidator.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/ValueCoercer.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/cli/ConfigurationJsonSchemaValidatorCli.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/cli/ConfigurationJsonSchemaValidatorCliBootstrap.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/cli/JsonSchemaConfigurationValidator.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/cli/package-info.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/management/ConfigurationEndpoint.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/management/ConfigurationHealthIndicator.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/management/InjectErrorsEndpoint.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/management/InjectErrorsHealthIndicator.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/management/package-info.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/model/ConfigurationSchema.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/model/ConfigurationSchemaProperty.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/model/ConfigurationSchemaType.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/model/MicronautMetadata.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/model/package-info.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/package-info.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/report/ConfigurationErrorReporter.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/report/HtmlConfigurationErrorReporter.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/report/JsonConfigurationErrorReporter.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/report/SystemErrConfigurationErrorReporter.java
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/report/package-info.java
- `A` json-schema-configuration-validator/src/main/resources/META-INF/services/io.micronaut.context.env.PropertyExpressionResolver
- `M` json-schema-generator/src/main/java/io/micronaut/jsonschema/generator/SourceGenerator.java
- `M` json-schema-generator/src/main/java/io/micronaut/jsonschema/generator/aggregator/AnnotationsAggregator.java
- `M` json-schema-generator/src/main/java/io/micronaut/jsonschema/generator/aggregator/TypeAggregator.java
- `M` json-schema-generator/src/main/java/io/micronaut/jsonschema/generator/loaders/FileLoader.java
- `M` json-schema-generator/src/main/java/io/micronaut/jsonschema/generator/loaders/SchemaLoader.java
- `M` json-schema-processor/src/main/java/io/micronaut/jsonschema/visitor/JsonSchemaVisitor.java
- `M` json-schema-processor/src/main/java/io/micronaut/jsonschema/visitor/aggregator/JacksonInfoAggregator.java
- `A` json-schema-utils/src/main/java/io/micronaut/jsonschema/utils/CompositeJsonSchemaClassPathResourceLoader.java
- `A` json-schema-utils/src/main/java/io/micronaut/jsonschema/utils/ConfigurationJsonSchemaClassPathResourceLoader.java
- `M` json-schema-utils/src/main/java/io/micronaut/jsonschema/utils/DefaultJsonSchemaClassPathResourceLoader.java
- `M` json-schema-utils/src/main/java/io/micronaut/jsonschema/utils/JsonSchemaClassPathResourceLoader.java
- `A` json-schema-utils/src/main/java/io/micronaut/jsonschema/utils/JsonSchemaResourceUtils.java
- `A` json-schema-utils/src/main/java/io/micronaut/jsonschema/utils/LazyJsonSchemaReadable.java
- `M` json-schema-validation/src/main/java/io/micronaut/jsonschema/validation/DefaultJsonSchemaValidator.java
- `M` json-schema-validation/src/main/java/io/micronaut/jsonschema/validation/JsonSchemaValidationFactory.java
- `M` json-schema-validation/src/main/java/io/micronaut/jsonschema/validation/JsonSchemaValidator.java
- `M` json-schema-validation/src/main/java/io/micronaut/jsonschema/validation/ValidationMessageAdapter.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` json-schema-common/src/test/groovy/io/micronaut/jsonschema/serialization/SchemaSerializationSpec.groovy
- `M` json-schema-common/src/test/groovy/model/TypeListSerializerSpec.groovy
- `A` json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/AutoTestResourcesPropertyExpressionResolver.java
- `A` json-schema-configuration-validator/src/main/resources/META-INF/micronaut/io.micronaut.context.env.PropertyExpressionResolver/io.micronaut.jsonschema.configuration.validator.AutoTestResourcesPropertyExpressionResolver
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/AutoTestResourcesPropertyExpressionResolverTest.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/ConfigurationJsonSchemaValidatorTest.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/ConfigurationRuleIntegrationTest.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureCircularBeanA.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureCircularBeanB.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureCliDisabledCandidateBean.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureCliDisabledCandidateProperty.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureCliDisabledConsumer.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureCliDisabledService.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureConditionalBeanRequiredCandidate.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureConditionalMultiBeanRequiredCandidate.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureConditionalMultiConsumer.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureConditionalPropertyRequiredCandidate.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureConditionalService.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureConditionalSingleConsumer.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureConfigurationPropertiesConsumer.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureConfigurationPropertiesRecord.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureConstructorInjectionBean.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureContextBean.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureControllerBean.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureDataSource.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureDataSourceBean.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureDataSourceConfiguration.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureDataSourceConfigurer.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureDataSourceConfigurerBean.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureEachBeanChainNamedConsumer.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureEachBeanChainPrimaryConsumer.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureEachBeanNamedConsumer.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureEachBeanPrimaryConsumer.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureEachBeanTarget.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureEachConfig.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureFactoryMethodMissingArgConsumer.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureFactoryMethodMissingArgFactory.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureFactoryMethodMissingArgGreeter.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureFieldInjectionBean.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureImplicitInfrastructureBean.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureMethodInjectionBean.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureMultipleCandidateConsumer.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureMultipleCandidateOne.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureMultipleCandidateOrderConsumer.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureMultipleCandidateOrderHighPrecedence.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureMultipleCandidateOrderLowPrecedence.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureMultipleCandidatePrimaryBean.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureMultipleCandidatePrimaryConsumer.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureMultipleCandidatePrimaryFallback.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureMultipleCandidateSecondaryBean.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureMultipleCandidateSecondaryConsumer.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureMultipleCandidateSecondaryPreferred.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureMultipleCandidateService.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureMultipleCandidateTwo.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixturePropertyInjectionBean.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureQualifierInjectionBean.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureScheduledBean.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureStartupListenerBean.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureStrategySingletonOnlyBean.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/FixtureValueInjectionBean.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/GeneratedConfigurationSchemasTest.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/InvalidConfigurationSupressionsTest.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/InvalidConfigurationTest.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/JsonSchemaConfigurationValidatorConfigurerTest.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/JsonSchemaConfigurationValidatorDeduceEnvironmentTest.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/MicronautShippedSchemasTest.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/TestApplicationContextConfigurer.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/TestConfigurationRule.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/ValidConfigurationTest.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/ValueCoercerTest.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/cli/ConfigurationJsonSchemaValidatorCliTest.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/cli/package-info.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/management/ConfigurationEndpointDisabledTest.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/management/ConfigurationEndpointTest.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/management/ConfigurationHealthIndicatorDisabledTest.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/management/ConfigurationHealthIndicatorTest.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/management/InjectErrorsEndpointDisabledTest.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/management/InjectErrorsEndpointTest.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/management/InjectErrorsHealthIndicatorDisabledTest.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/management/InjectErrorsHealthIndicatorTest.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/management/package-info.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/package-info.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/report/ConfigurationErrorReporterTest.java
- `A` json-schema-configuration-validator/src/test/java/io/micronaut/jsonschema/configuration/validator/report/package-info.java
- `A` json-schema-configuration-validator/src/test/resources/META-INF/micronaut-configuration-schemas/io.micronaut.data.jdbc.config.DataJdbcConfiguration.json
- `A` json-schema-configuration-validator/src/test/resources/META-INF/micronaut-configuration-schemas/test.bindable.BindableDefaultsConfig.json
- `A` json-schema-configuration-validator/src/test/resources/META-INF/micronaut-configuration-schemas/test.config.TestConfig.json
- `A` json-schema-configuration-validator/src/test/resources/META-INF/micronaut-configuration-schemas/test.edge.EdgeCases.json
- `A` json-schema-configuration-validator/src/test/resources/META-INF/micronaut-configuration-schemas/test.enum.EnumConfig.json
- `A` json-schema-configuration-validator/src/test/resources/META-INF/micronaut-configuration-schemas/test.executors.UserExecutorConfiguration.json
- `A` json-schema-configuration-validator/src/test/resources/META-INF/micronaut-configuration-schemas/test.overlap.OverlapA.json
- `A` json-schema-configuration-validator/src/test/resources/META-INF/micronaut-configuration-schemas/test.overlap.OverlapB.json
- `A` json-schema-configuration-validator/src/test/resources/META-INF/micronaut-configuration-schemas/test.pattern.PatternConfig.json
- `A` json-schema-configuration-validator/src/test/resources/META-INF/micronaut-configuration-schemas/test.rules.JpaRulesSchema.json
- `A` json-schema-configuration-validator/src/test/resources/META-INF/micronaut-configuration-schemas/test.suggest.SuggestConfig.json
- `A` json-schema-configuration-validator/src/test/resources/META-INF/micronaut-configuration-schemas/test.url.UrlConfig.json
- `A` json-schema-configuration-validator/src/test/resources/META-INF/services/io.micronaut.context.ApplicationContextConfigurer
- `A` json-schema-configuration-validator/src/test/resources/META-INF/services/io.micronaut.jsonschema.configuration.validator.ConfigurationRule
- `A` json-schema-configuration-validator/src/test/resources/logback.xml
- `A` json-schema-configuration-validator/src/test/resources/origin-test.properties
- `M` json-schema-processor/src/test/groovy/io/micronaut/jsonschema/visitor/AbstractJsonSchemaSpec.groovy
- `M` json-schema-processor/src/test/groovy/io/micronaut/jsonschema/visitor/JacksonJsonSchemaVisitorSpec.groovy
- `M` json-schema-processor/src/test/groovy/io/micronaut/jsonschema/visitor/JsonSchemaVisitorSpec.groovy
- `A` json-schema-utils/src/test/java/io/micronaut/jsonschema/utils/CompositeJsonSchemaClassPathResourceLoaderTest.java
- `A` json-schema-utils/src/test/java/io/micronaut/jsonschema/utils/ConfigurationJsonSchemaClassPathResourceLoaderTest.java
- `A` json-schema-utils/src/test/java/io/micronaut/jsonschema/utils/JsonSchemaClassPathResourceLoaderCompositeFactoryTest.java
- `M` json-schema-utils/src/test/java/io/micronaut/jsonschema/utils/JsonSchemaClassPathResourceLoaderTest.java
- `M` test-suite-generator-java/src/test/java/io/micronaut/jsonschema/generator/FoodTest.java
- `M` test-suite-generator-java/src/test/java/io/micronaut/jsonschema/generator/animals/AnimalTest.java
- `M` test-suite-generator-java/src/test/java/io/micronaut/jsonschema/serialization/SerializationTest.java
- `A` test-suite-groovy/src/test/groovy/io/micronaut/jsonschema/test/ConfigurationErrorsExample.groovy
- `A` test-suite-groovy/src/test/groovy/io/micronaut/jsonschema/test/ConfigurationRuleExample.groovy
- `A` test-suite-kotlin/src/test/kotlin/io/micronaut/jsonschema/test/ConfigurationErrorsExample.kt
- `A` test-suite-kotlin/src/test/kotlin/io/micronaut/jsonschema/test/ConfigurationRuleExample.kt
- `A` test-suite/src/test/java/io/micronaut/jsonschema/test/ConfigurationErrorsExample.java
- `A` test-suite/src/test/java/io/micronaut/jsonschema/test/ConfigurationRuleExample.java

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

