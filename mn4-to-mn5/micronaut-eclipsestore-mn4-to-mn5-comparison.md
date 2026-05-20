• Generated the comparison report here:

  micronaut-eclipsestore-mn4-to-mn5-comparison.md:1

  Scope: mn4 previous is 1.11.x at 93dd81e8e9d1, clean. mn5 current is 2.0.x at 6c76684137f0, dirty because gradle/libs.versions.toml has local edits. The comparison found 82 commit candidates and 147 changed files.

  Release-note draft:

  ## Micronaut EclipseStore 2.0

  ### Breaking Changes

  - Annotation mappers moved from `micronaut-eclipsestore-annotations` to the new `micronaut-eclipsestore-processor` module. Replace `micronaut-eclipsestore-annotations` annotation processor usage, or Groovy `compileOnly`
  usage, with `micronaut-eclipsestore-processor`.

  ### Features

  - Added Google Cloud Firestore storage target support.
  - Firestore storage can be configured under `eclipsestore.firestore.storage.*`. The storage manager looks for a named `Firestore` bean matching the storage manager name, then falls back to the default `Firestore` bean. A
  specific client can be selected with `firestore-client-name`.

  ### Compatibility

  - Updated for the Micronaut 5 baseline.
  - Updated EclipseStore from `1.4.0` to `4.0.1`.
  - Replaced Micronaut nullability annotations with JSpecify annotations across the EclipseStore APIs.

  ### Internal / Build

  - Converted build settings to Kotlin DSL and added the `eclipsestore-processor` module.
  - Removed Micronaut Test Resources wiring in favor of direct Testcontainers-based test utilities.

  Key version changes:

  - Project version: 1.11.0-SNAPSHOT -> 2.0.0-SNAPSHOT
  - Micronaut Core: 4.10.4 -> 5.0.0-RC2
  - EclipseStore: 1.4.0 -> 4.0.1
  - Micronaut AWS: 4.11.0 -> 5.0.0-M3
  - Micronaut Azure: 5.12.0 -> 6.0.0-RC1
  - Micronaut SQL: 6.3.1 -> 7.0.1-M3
  - Micronaut Serialization: 2.15.5 -> 3.0.0-RC2
  - Micronaut Validation: 4.11.0 -> 5.0.0-RC2
  - Gradle wrapper: 8.14.3 -> 9.5.0

  I did not run tests; this is a static git/filesystem comparison.

# Release Note Comparison

Generated: 2026-05-07 08:15 UTC
Comparison: `mn4` -> `mn5`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-eclipsestore` | `1.11.x` | `93dd81e8e9d1` | `git@github.com:micronaut-projects/micronaut-eclipsestore.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-eclipsestore` | `2.0.x` | `6c76684137f0` | `git@github.com:micronaut-projects/micronaut-eclipsestore.git` | `True` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-eclipsestore`
- Commit candidates found: 82
- File changes listed: 147
- Version values listed: 28
- File status counts: A=40, D=2, M=95, R=10

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `1.11.0-SNAPSHOT` | `2.0.0-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.gradle-kotlin` | `org.jetbrains.kotlin:kotlin-gradle-plugin (version.ref=kotlin)` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-aws` | `io.micronaut.aws:micronaut-aws-bom:4.11.0` | `io.micronaut.aws:micronaut-aws-bom:5.0.0-M3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-azure` | `io.micronaut.azure:micronaut-azure-bom:5.12.0` | `io.micronaut.azure:micronaut-azure-bom:6.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-cache` | `io.micronaut.cache:micronaut-cache-bom:5.3.0` | `io.micronaut.cache:micronaut-cache-bom:6.0.0-M3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-micrometer` | `io.micronaut.micrometer:micronaut-micrometer-bom:5.13.0` | `io.micronaut.micrometer:micronaut-micrometer-bom:6.0.1-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.15.5` | `io.micronaut.serde:micronaut-serde-bom:3.0.0-RC2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-sql` | `io.micronaut.sql:micronaut-sql-bom:6.3.1` | `io.micronaut.sql:micronaut-sql-bom:7.0.1-M3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-resources` | `io.micronaut.testresources:micronaut-test-resources-bom:2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-validation` | `io.micronaut.validation:micronaut-validation-bom:4.11.0` | `io.micronaut.validation:micronaut-validation-bom:5.0.0-RC2` | `changed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.27` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.managed-eclipsestore` | `not present` | `4.0.1` | `added` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.4` | `5.0.0-RC2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-aws` | `4.11.0` | `5.0.0-M3` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-azure` | `5.12.0` | `6.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-cache` | `5.3.0` | `6.0.0-M3` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.6.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-micrometer` | `5.13.0` | `6.0.1-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.15.5` | `3.0.0-RC2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-sql` | `6.3.1` | `7.0.1-M3` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.7.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test-resources` | `2.10.1` | `4.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.11.0` | `5.0.0-RC2` | `changed` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.0` | `changed` |
| `settings.gradle.kts` | `plugin.io.micronaut.build.shared.settings` | `not present` | `8.0.0-M18` | `added` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `e82242134426` Remove test resources (#256) (Sergio del Amo, 2026-01-02)
- `594395abefe9` remove nullability annotations (Sergio del Amo, 2026-01-02)

### Fixes

- `2740fe904d34` fix(deps): update micronaut dependencies (#273) (renovate[bot], 2026-04-29)
- `83fa9a5bed14` fix(deps): update managed.eclipsestore to v4 (#267) (renovate[bot], 2026-04-29)
- `994f2fde7669` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m5 (#262) (renovate[bot], 2026-04-02)
- `7862fee8b0d5` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m19 (#271) (renovate[bot], 2026-04-02)
- `b9358163e63f` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m17 (#261) (renovate[bot], 2026-03-17)
- `971edb4b30a0` fix(deps): update managed.eclipsestore to v3.1.0 (#245) (renovate[bot], 2026-01-02)
- `563012250419` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m6 (#249) (renovate[bot], 2026-01-02)
- `deb77c4f05b9` fix(deps): update dependency io.micronaut.micrometer:micronaut-micrometer-bom to v5.13.2 (#246) (renovate[bot], 2025-12-10)
- `70cfa67e22fc` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to v7 (#239) (renovate[bot], 2025-12-10)
- `4c287bc2e97c` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#238) (renovate[bot], 2025-12-10)
- `041544300cc2` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#229) (renovate[bot], 2025-11-11)
- `b84a6378f0da` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.12.0 (#231) (renovate[bot], 2025-11-11)
- `d7f3085880ce` fix(deps): update dependency io.micronaut.micrometer:micronaut-micrometer-bom to v5.13.1 (#222) (renovate[bot], 2025-11-07)
- `5d799f7ac8a0` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to v6.3.2 (#223) (renovate[bot], 2025-11-07)
- `2f8134020361` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.8 (#221) (renovate[bot], 2025-11-07)
- `39ff281b9552` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.6 (#217) (renovate[bot], 2025-10-17)
- `8d06e9b06323` fix(deps): update managed.eclipsestore to v2 (#112) (renovate[bot], 2024-11-06)
- `405e42e91be3` fix(deps): update kotlin monorepo to v1.9.23 (#21) (renovate[bot], 2024-04-05)
- `0f80b394fa6c` fix(deps): update dependency io.micronaut.cache:micronaut-cache-bom to v4.2.2 (#20) (renovate[bot], 2024-04-01)

### Dependency Updates

- `6d79a4c6d89c` Merge pull request #276 from micronaut-projects/renovate/micronaut-dependencies (Graeme Rocher, 2026-05-01)
- `7eadd7bce6c1` Update dependency io.micronaut:micronaut-core-bom to v5.0.0-M26 (renovate[bot], 2026-04-30)
- `72e3f2464b4b` chore: Bump version to 2.0.0-SNAPSHOT (micronaut-build, 2026-04-29)
- `c50c62576187` chore(deps): update gradle to v9.5.0 (#263) (renovate[bot], 2026-04-29)
- `293b33d51dc7` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#260) (renovate[bot], 2026-03-17)
- `e582be02e4a6` chore: Bump version to 2.0.0-SNAPSHOT (micronaut-build, 2026-01-02)
- `6acf85ab6c57` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m13 (#252) (renovate[bot], 2026-01-02)
- `313df993fcd5` chore(deps): update stefanzweifel/git-auto-commit-action action to v7.1.0 (#253) (renovate[bot], 2026-01-02)
- `62ef17babdaa` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#241) (renovate[bot], 2025-12-10)
- `e4728246f00f` chore(deps): update stefanzweifel/git-auto-commit-action action to v7 (#237) (renovate[bot], 2025-12-10)
- `114d42869b0a` chore(deps): update actions/checkout action to v6 (#236) (renovate[bot], 2025-12-10)
- `fd97eb7bcbca` chore(deps): update gradle to v9.2.1 (#235) (renovate[bot], 2025-12-10)
- `d3c4371e9a00` chore(deps): update mikepenz/action-junit-report action to v6 (#234) (renovate[bot], 2025-12-10)
- `054028f0118c` chore(deps): update github artifact actions (#232) (renovate[bot], 2025-12-10)
- `f171de3e2bad` chore(deps): update softprops/action-gh-release action to v2.4.2 (#228) (renovate[bot], 2025-11-11)
- `064764615af3` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m9 (#220) (renovate[bot], 2025-11-07)
- `e8bae44cd751` chore(deps): update gradle to v9.2.0 (#224) (renovate[bot], 2025-11-07)
- `d401dd9af987` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#219) (renovate[bot], 2025-11-07)
- `180357df40e2` chore(deps): update plugin io.micronaut.test-resources to v4.6.1 (#226) (renovate[bot], 2025-11-07)
- `ef1fd94c2cbf` chore(deps): update gradle/gradle-build-action action to v3.2.1 (#22) (renovate[bot], 2024-04-11)
- `28a7208b8b32` chore(deps): update plugin io.micronaut.build.shared.settings to v6.7.0 (#23) (renovate[bot], 2024-04-11)
- `147c8a50b20e` chore(deps): update plugin io.micronaut.test-resources to v4.3.6 (#24) (renovate[bot], 2024-04-11)
- `1cdb5b46efcc` Update dependency io.micronaut.aws:micronaut-aws-bom to v4.4.3 (#19) (renovate[bot], 2024-04-01)

### Internal

- `0226a4b96147` build: enable binary compatibility (#13) (Sergio del Amo, 2024-02-12)

### Review Candidates

- `6c76684137f0` update versions (Sergio del Amo, 2026-05-07)
- `c95c7c799b74` Update common files (#277) (micronaut-build, 2026-05-07)
- `c84d34eb5ef3` Update common files (#275) (micronaut-build, 2026-05-01)
- `98d36f01700c` Merge remote-tracking branch 'origin/1.7.x' into 2.0.x (Graeme Rocher, 2026-05-01)
- `3eee3575ca55` Feat/add google cloud firestore support (#85) (Simon Frauenschuh, 2026-05-01)
- `be45103d7bb2` [skip ci] Release v2.0.0-M2 (micronaut-build, 2026-04-29)
- `8fd9447a5305` update azurite (Sergio del Amo, 2026-04-29)
- `03cf8a5eb14c` use double quotes (Sergio del Amo, 2026-04-29)
- `bf586602ea38` micronaut-micrometer = "6.0.0-M2" (Sergio del Amo, 2026-04-29)
- `c69ec85b60ca` micronaut-sql = "7.0.1-M2" (Sergio del Amo, 2026-04-29)
- `06470f2ff53a` micronaut-azure = "6.0.0-M2" (Sergio del Amo, 2026-04-29)
- `be45350a9ddb` micronaut-aws = "5.0.0-M3" (Sergio del Amo, 2026-04-29)
- `1b3e4050a126` micronaut-test = "5.0.0-M7" (Sergio del Amo, 2026-04-29)
- `56f59f534caf` Update common files (#274) (micronaut-build, 2026-04-29)
- `61276a52aabc` Merge pull request #269 from micronaut-projects/sync-files-2.0.x (Graeme Rocher, 2026-04-26)
- `2d7f33fbb72f` Update common files (micronaut-build, 2026-04-21)
- `d9741628cb78` Update common files (#259) (micronaut-build, 2026-03-17)
- `28ccbbd1727a` [skip ci] Release v2.0.0-M1 (micronaut-build, 2026-01-02)
- `e44ce9d24067` sql 7.0.0-M4 (Sergio del Amo, 2026-01-02)
- `e870ba52b921` Update common files (#255) (micronaut-build, 2026-01-02)
- `402e84a36f90` update to micronaut 5 (#250) (issam liqali, 2025-12-16)
- `0eadc77c8927` Update common files (#233) (micronaut-build, 2025-12-10)
- `5a0a1743c34c` Replace Micronaut nullability annotations with JSpecify annotations (#243) (Copilot, 2025-12-01)
- `b99fe074d26d` Micronaut 5 prep (#230) (araysse, 2025-11-11)
- `f474367f895d` update to 8.0.0-M9 (#225) (araysse, 2025-11-07)
- `2782c0071889` Update common files (#218) (micronaut-build, 2025-11-07)
- `50df61f49612` Update common files (#216) (micronaut-build, 2025-10-17)
- `9c23f1314ef7` eclipsestore 3.0.1 (Sergio del Amo, 2025-10-15)
- `2ff665ad62a8` gradle 9.1 (Sergio del Amo, 2025-10-15)
- `67b7bb1a99f3` Merge branch '1.11.x' into 2.0.x (Sergio del Amo, 2025-10-15)
- `a5b9d3e3c5fb` Merge branch '1.8.x' into 2.0.x (Sergio del Amo, 2024-11-06)
- `e3abfc955cbd` Merge branch '1.6.x' into 2.0.x (Sergio del Amo, 2024-08-07)
- `14f1bb12d9a5` Merge branch '1.6.x' into 2.0.x (Sergio del Amo, 2024-08-07)
- `e3345da2aea9` Merge branch '1.5.x' into 2.0.x (Sergio del Amo, 2024-04-11)
- `8910e7fab3bb` Update common files (#9) (micronaut-build, 2024-04-01)
- `4d2aed036b5d` Merge branch '1.4.x' (Sergio del Amo, 2024-03-14)
- `659bb30a37a2` breaks: eclipsestore-processor module (#15) (Tim Yates, 2024-02-29)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` .github/workflows/update-gradle-wrapper.yml
- `A` build.gradle.kts
- `M` buildSrc/build.gradle.kts
- `M` buildSrc/src/main/groovy/io.micronaut.internal.build.eclipsestore-base.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.internal.build.eclipsestore-testsuite.gradle
- `M` eclipsestore-annotations/build.gradle.kts
- `M` eclipsestore-bom/build.gradle.kts
- `M` eclipsestore-cache/build.gradle.kts
- `A` eclipsestore-processor/build.gradle.kts
- `M` eclipsestore/build.gradle.kts
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `D` settings.gradle
- `A` settings.gradle.kts
- `R076` test-suite-groovy/build.gradle.kts
- `R073` test-suite-kotlin/build.gradle.kts
- `M` test-suite-utils/build.gradle.kts
- `R077` test-suite/build.gradle.kts

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
- `M` src/main/docs/guide/dependency.adoc
- `A` src/main/docs/guide/storageTargets/firestore.adoc
- `M` src/main/docs/guide/toc.yml
- `M` test-suite-groovy/src/test/groovy/io/micronaut/eclipsestore/docs/Customer.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/eclipsestore/docs/CustomerController.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/eclipsestore/docs/CustomerRepository.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/eclipsestore/docs/CustomerRepositoryImpl.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/eclipsestore/docs/CustomerRepositoryStoreImpl.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/eclipsestore/docs/CustomerSave.groovy
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/eclipsestore/docs/CustomerRepositoryImpl.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/eclipsestore/docs/CustomerRepositoryStoreImpl.kt
- `M` test-suite/src/test/java/io/micronaut/eclipsestore/docs/AzureBlobLocalClient.java
- `M` test-suite/src/test/java/io/micronaut/eclipsestore/docs/BlobCustomerControllerTest.java
- `M` test-suite/src/test/java/io/micronaut/eclipsestore/docs/CrmCustomerService.java
- `M` test-suite/src/test/java/io/micronaut/eclipsestore/docs/CrmCustomerServiceImpl.java
- `M` test-suite/src/test/java/io/micronaut/eclipsestore/docs/CrmCustomerServiceStoreReturnImpl.java
- `M` test-suite/src/test/java/io/micronaut/eclipsestore/docs/Customer.java
- `M` test-suite/src/test/java/io/micronaut/eclipsestore/docs/CustomerController.java
- `M` test-suite/src/test/java/io/micronaut/eclipsestore/docs/CustomerRepository.java
- `M` test-suite/src/test/java/io/micronaut/eclipsestore/docs/CustomerRepositoryImpl.java
- `M` test-suite/src/test/java/io/micronaut/eclipsestore/docs/CustomerRepositoryRootEagerImpl.java
- `M` test-suite/src/test/java/io/micronaut/eclipsestore/docs/CustomerRepositoryStoreAnnotationImpl.java
- `M` test-suite/src/test/java/io/micronaut/eclipsestore/docs/CustomerRepositoryStoreImpl.java
- `M` test-suite/src/test/java/io/micronaut/eclipsestore/docs/CustomerRepositoryStoreRootEagerImpl.java
- `M` test-suite/src/test/java/io/micronaut/eclipsestore/docs/CustomerRepositoryStoreWithNameQualifierImpl.java
- `M` test-suite/src/test/java/io/micronaut/eclipsestore/docs/CustomerSave.java
- `M` test-suite/src/test/java/io/micronaut/eclipsestore/docs/Customers.java
- `M` test-suite/src/test/java/io/micronaut/eclipsestore/docs/Data.java
- `A` test-suite/src/test/java/io/micronaut/eclipsestore/docs/FirebaseCustomerControllerTest.java
- `A` test-suite/src/test/java/io/micronaut/eclipsestore/docs/FirestoreLocalClient.java
- `M` test-suite/src/test/java/io/micronaut/eclipsestore/docs/PostgresCustomerControllerTest.java
- `M` test-suite/src/test/java/io/micronaut/eclipsestore/docs/PostgresPersistentCacheTest.java
- `M` test-suite/src/test/java/io/micronaut/eclipsestore/docs/StoreReturnOptional.java

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
- `M` config/checkstyle/checkstyle.xml
- `D` eclipsestore-annotations/src/main/resources/META-INF/services/io.micronaut.inject.annotation.AnnotationMapper
- `M` eclipsestore-cache/src/main/java/io/micronaut/eclipsestore/cache/CacheConfigurationFactory.java
- `M` eclipsestore-cache/src/main/java/io/micronaut/eclipsestore/cache/EclipseStoreCacheConfiguration.java
- `M` eclipsestore-cache/src/main/java/io/micronaut/eclipsestore/cache/EclipseStoreCacheConfigurationProperties.java
- `R081` eclipsestore-processor/src/main/java/io/micronaut/eclipsestore/processor/StoreAnnotationMapperUtils.java
- `R088` eclipsestore-processor/src/main/java/io/micronaut/eclipsestore/processor/StoreParamsAnnotationMapper.java
- `R087` eclipsestore-processor/src/main/java/io/micronaut/eclipsestore/processor/StoreReturnAnnotationMapper.java
- `R087` eclipsestore-processor/src/main/java/io/micronaut/eclipsestore/processor/StoreRootAnnotationMapper.java
- `A` eclipsestore-processor/src/main/resources/META-INF/services/io.micronaut.inject.annotation.AnnotationMapper
- `M` eclipsestore-rest/src/main/java/io/micronaut/eclipsestore/rest/DefaultEclipseStoreRestService.java
- `M` eclipsestore-rest/src/main/java/io/micronaut/eclipsestore/rest/EclipseStoreRestController.java
- `M` eclipsestore-rest/src/main/java/io/micronaut/eclipsestore/rest/EclipseStoreRestControllerConfiguration.java
- `M` eclipsestore-rest/src/main/java/io/micronaut/eclipsestore/rest/EclipseStoreRestControllerConfigurationProperties.java
- `M` eclipsestore-rest/src/main/java/io/micronaut/eclipsestore/rest/EclipseStoreRestService.java
- `M` eclipsestore-rest/src/main/java/io/micronaut/eclipsestore/rest/RootObject.java
- `M` eclipsestore/src/main/java/io/micronaut/eclipsestore/azure/BlobStorageConfigurationProvider.java
- `M` eclipsestore/src/main/java/io/micronaut/eclipsestore/azure/DefaultBlobStorageConfigurationProvider.java
- `M` eclipsestore/src/main/java/io/micronaut/eclipsestore/conf/DefaultEmbeddedStorageConfigurationProvider.java
- `M` eclipsestore/src/main/java/io/micronaut/eclipsestore/conf/EmbeddedStorageConfigurationProvider.java
- `M` eclipsestore/src/main/java/io/micronaut/eclipsestore/conf/RootClassConfigurationProvider.java
- `M` eclipsestore/src/main/java/io/micronaut/eclipsestore/conf/StorageManagerFactory.java
- `M` eclipsestore/src/main/java/io/micronaut/eclipsestore/dynamodb/DefaultDynamoDBStorageConfigurationProvider.java
- `M` eclipsestore/src/main/java/io/micronaut/eclipsestore/dynamodb/DynamoDbStorageConfigurationProvider.java
- `A` eclipsestore/src/main/java/io/micronaut/eclipsestore/firestore/DefaultFirestoreStorageConfigurationProvider.java
- `A` eclipsestore/src/main/java/io/micronaut/eclipsestore/firestore/FirestoreStorageConfigurationProvider.java
- `A` eclipsestore/src/main/java/io/micronaut/eclipsestore/firestore/FirestoreStorageFoundationFactory.java
- `A` eclipsestore/src/main/java/io/micronaut/eclipsestore/firestore/package-info.java
- `M` eclipsestore/src/main/java/io/micronaut/eclipsestore/health/EclipseStoreHealthIndicator.java
- `M` eclipsestore/src/main/java/io/micronaut/eclipsestore/interceptors/StoreInterceptor.java
- `M` eclipsestore/src/main/java/io/micronaut/eclipsestore/metrics/EclipseStoreMetricsBinder.java
- `M` eclipsestore/src/main/java/io/micronaut/eclipsestore/postgres/DefaultPostgresStorageConfigurationProvider.java
- `M` eclipsestore/src/main/java/io/micronaut/eclipsestore/postgres/PostgresStorageConfigurationProvider.java
- `M` eclipsestore/src/main/java/io/micronaut/eclipsestore/s3/DefaultS3StorageConfigurationProvider.java
- `M` eclipsestore/src/main/java/io/micronaut/eclipsestore/s3/S3StorageConfigurationProvider.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `R086` eclipsestore-processor/src/test/groovy/io/micronaut/eclipsestore/processor/StoreParamsAnnotationMapperSpec.groovy
- `R086` eclipsestore-processor/src/test/groovy/io/micronaut/eclipsestore/processor/StoreReturnAnnotationMapperSpec.groovy
- `R086` eclipsestore-processor/src/test/groovy/io/micronaut/eclipsestore/processor/StoreRootAnnotationMapperSpec.groovy
- `M` eclipsestore-rest/src/test/groovy/io/micronaut/eclipsestore/rest/EclipseStoreRestControllerSingleStorageSpec.groovy
- `M` eclipsestore-rest/src/test/groovy/io/micronaut/eclipsestore/rest/EclipseStoreRestControllerSpec.groovy
- `M` eclipsestore-rest/src/test/groovy/io/micronaut/eclipsestore/rest/EclipseStoreRestStartupWarningSpec.groovy
- `M` eclipsestore-rest/src/test/groovy/io/micronaut/eclipsestore/rest/People.groovy
- `M` eclipsestore-rest/src/test/groovy/io/micronaut/eclipsestore/rest/RestConfigurationSpec.groovy
- `M` eclipsestore-rest/src/test/groovy/io/micronaut/eclipsestore/rest/Towns.groovy
- `M` eclipsestore/src/test/groovy/io/micronaut/eclipsestore/dynamodb/DynamoDbStorageConfigurationProviderSpec.groovy
- `M` eclipsestore/src/test/groovy/io/micronaut/eclipsestore/dynamodb/DynamoDbStorageSpec.groovy
- `A` eclipsestore/src/test/groovy/io/micronaut/eclipsestore/firestore/FirestoreStorageSpec.groovy
- `M` eclipsestore/src/test/groovy/io/micronaut/eclipsestore/postgres/NamedPostgresStorageSpec.groovy
- `M` eclipsestore/src/test/groovy/io/micronaut/eclipsestore/postgres/PostgresStorageSpec.groovy
- `M` eclipsestore/src/test/groovy/io/micronaut/eclipsestore/s3/NamedS3StorageSpec.groovy
- `M` eclipsestore/src/test/groovy/io/micronaut/eclipsestore/s3/S3StorageSpec.groovy
- `M` test-suite-utils/src/main/java/io/micronaut/eclipsestore/testutils/AzureBlobLocal.java
- `A` test-suite-utils/src/main/java/io/micronaut/eclipsestore/testutils/FirestoreLocal.java
- `A` test-suite-utils/src/main/java/io/micronaut/eclipsestore/testutils/Postgresql.java

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

