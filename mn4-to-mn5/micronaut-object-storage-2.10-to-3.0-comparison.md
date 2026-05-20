 Compared micronaut-object-storage as mn4 -> mn5.

  Scope

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-object-storage, branch 2.10.x, SHA 9c5dd1b84b46
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-object-storage, branch 3.0.x, SHA f5da8e4c8c65
  - Same remote, both clean: git@github.com:micronaut-projects/micronaut-object-storage.git
  - Report: /private/tmp/micronaut-object-storage-2.10-to-3.0-comparison.md

  Key Findings

  - Baseline moved to projectVersion 2.10.1-SNAPSHOT -> 3.0.1-SNAPSHOT, Micronaut 4.10.4 -> 5.0.0,
    Micronaut Platform 4.9.4 -> 5.0.0-RC1, Gradle 8.14.3 -> 9.5.1, with .sdkmanrc adding java=25.0.1-graal.
  - Provider BOMs moved to major lines: AWS 4.11.0 -> 5.0.0, Azure 5.12.0 -> 6.0.0, GCP 5.13.0 -> 6.0.0,
    Oracle Cloud 5.5.1 -> 6.0.0.
  - New paginated listing API: ListObjectsRequest, ListObjectsResponse, and
    ObjectStorageOperations#listObjects(ListObjectsRequest), with provider implementations and tests.
  - New bucket/container lifecycle API: BucketOperations, ReactiveBucketOperations, BucketEntry, plus AWS,
    Azure, GCP, Oracle Cloud, and local implementations.
  - New reactive object-storage API: ReactiveObjectStorageOperations and provider reactive operation beans.
    Docs note this is reactive at operation level while payloads still use the existing InputStream
    abstractions.
  - Pre-signed API changed substantially: old PresignRequest, PresignResponse, presign(...), and
    invalidatePresignedRequest(...) were removed; new upload-only API uses CreatePresignedUploadRequest,
    PresignedUpload, and createPresignedUpload(...).
  - Local pre-sign support was removed: LocalPresignController, LocalPresignStore, micronaut.object-
    storage.local-presigned-request-controller, and object-storage.default-presign-expiration are gone.
  - Documented removals: deprecated AzureBlobStorageEntry(String, BinaryData) constructor and deprecated
    OracleCloudStorageOperations(OracleCloudStorageConfiguration, ObjectStorage) constructor were removed.
  - New ResourceLoader support was added for object-storage URIs, including provider schemes like s3, gs,
    azb, os, and named storage URIs.
  - Local storage was hardened around path traversal, reserved .metadata keys/paths, symlink resolution,
    and owner-only POSIX permissions.
  - Fixes include preserving Azure Blob simple-upload tags/options and using Oracle Cloud UploadManager for
    known-length uploads.
  - Docs/examples were expanded for reactive operations, pre-signed uploads, paginated listing, bucket
    management, control panel integration, and breaking changes.

  Diff size: 263 files changed, 15284 insertions(+), 1786 deletions(-).

  I did not run tests; this was a folder comparison and targeted source/build-diff review only.

# Release Note Comparison

Generated: 2026-05-19 16:14 UTC
Comparison: `2.10.x` -> `3.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-object-storage` | `2.10.x` | `9c5dd1b84b46` | `git@github.com:micronaut-projects/micronaut-object-storage.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-object-storage` | `3.0.x` | `f5da8e4c8c65` | `git@github.com:micronaut-projects/micronaut-object-storage.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-object-storage`
- Commit candidates found: 125
- File changes listed: 263
- Version values listed: 21
- File status counts: A=139, D=6, M=118

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `2.10.1-SNAPSHOT` | `3.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-logging` | `io.micronaut.logging:micronaut-logging-bom:1.7.1` | `io.micronaut.logging:micronaut-logging-bom:2.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-resources` | `io.micronaut.testresources:micronaut-test-resources-bom:2.10.1` | `io.micronaut.testresources:micronaut-test-resources-bom:4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-validation` | `io.micronaut.validation:micronaut-validation-bom:4.11.0` | `io.micronaut.validation:micronaut-validation-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.kotlin-gradle-ksp-plugin` | `1.9.25-1.0.20` | `2.3.7` | `changed` |
| `gradle/libs.versions.toml` | `versions.kotlin-gradle-plugin` | `1.9.25` | `2.3.21` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.4` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-aws` | `4.11.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-azure` | `5.12.0` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gcp` | `5.13.0` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.5.5` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.1` | `2.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-oracle-cloud` | `5.5.1` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-platform` | `4.9.4` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.9.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test-resources` | `2.10.1` | `4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.11.0` | `5.0.0` | `changed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |
| `settings.gradle.kts` | `plugin.io.micronaut.build.shared.settings` | `7.6.4` | `8.0.0-M18` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `68e4df43a929` remove oracle cloud docs (Sergio del Amo, 2026-02-23)
- `9c0f608ba149` sec: remove unnecessary coordinate exclusion (Sergio del Amo, 2026-02-20)
- `c29667df16a1` remove micronaut-docs (Sergio del Amo, 2026-02-20)
- `3e94c76e4d3f` remove spock (Sergio del Amo, 2026-02-20)
- `b2c9536fd438` remove groovy defined in Micronaut Build (Sergio del Amo, 2026-02-20)

### Features

- `892ba316d729` feat: abstract pre-signed upload request creation (#742) (Álvaro Sánchez-Mariscal, 2026-04-07)
- `b600283c9723` feat: add reactive object storage operations (#743) (Álvaro Sánchez-Mariscal, 2026-04-07)
- `410bdc512847` feat: add bucket management operations (#730) (Álvaro Sánchez-Mariscal, 2026-04-07)
- `ba305c2321cb` Add ResourceLoader support for object storage URIs (#741) (Álvaro Sánchez-Mariscal, 2026-04-04)
- `cb871382bb7d` feat(oracle-cloud): use UploadManager for known-length uploads (#739) (Álvaro Sánchez-Mariscal, 2026-04-04)
- `7876a408dcc1` feat: finish streaming upload support (#740) (Álvaro Sánchez-Mariscal, 2026-04-04)
- `dfaff1e535d4` Add paginated object listing with prefix filtering (#719) (Álvaro Sánchez-Mariscal, 2026-03-24)

### Fixes

- `f6ef354a30c9` fix(deps): update dependency com.google.devtools.ksp:com.google.devtools.ksp.gradle.plugin to v2.3.7 (#771) (renovate[bot], 2026-05-08)
- `441205d2a627` fix(deps): update dependency org.jetbrains.kotlin:kotlin-gradle-plugin to v2.3.21 (#772) (renovate[bot], 2026-05-08)
- `a172f505d00d` fix(deps): update micronaut dependencies (#774) (renovate[bot], 2026-05-01)
- `8669c2de2de0` fix: reject normalized local storage .metadata paths (#750) (Álvaro Sánchez-Mariscal, 2026-04-08)
- `90620e6e1bda` fix: confine rebased resource loader paths (#752) (Álvaro Sánchez-Mariscal, 2026-04-08)
- `5be5b3d08eb9` fix: harden local storage symlink path resolution (#747) (Álvaro Sánchez-Mariscal, 2026-04-07)
- `f04fc5c7642f` fix: reject reserved local storage metadata keys (#746) (Álvaro Sánchez-Mariscal, 2026-04-06)
- `051faf73927a` fix: restrict local storage file permissions (#748) (Álvaro Sánchez-Mariscal, 2026-04-06)
- `df63774a2236` fix: wire native image test suite (#735) (Álvaro Sánchez-Mariscal, 2026-04-04)
- `007c0f0fc8b8` fix: supplement Azure native image metadata for Logback (#738) (Álvaro Sánchez-Mariscal, 2026-04-04)
- `67ff6f944a71` fix: avoid malformed object storage each-property beans (#736) (Álvaro Sánchez-Mariscal, 2026-04-04)
- `969da884bbe5` fix: preserve Azure Blob index tags for simple uploads (#737) (Álvaro Sánchez-Mariscal, 2026-04-04)
- `d445bf69a6e5` fix(deps): update dependency net.bytebuddy:byte-buddy to v1.18.8 (#744) (renovate[bot], 2026-04-04)
- `0cb6f8d5c058` fix(deps): unblock junit-report upgrade by remediating Netty CVE (#727) (Álvaro Sánchez-Mariscal, 2026-04-03)
- `4e63b777d40d` fix(deps): update dependency com.google.cloud:libraries-bom to v26.79.0 (#725) (renovate[bot], 2026-04-03)
- `b6b3ea6d735e` fix(deps): update dependency io.micronaut.platform:micronaut-platform to v4.10.11 (#726) (renovate[bot], 2026-04-03)
- `b58a6e94e9ef` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m20 (#723) (renovate[bot], 2026-04-03)
- `63357bfeb906` fix(deps): update dependency net.bytebuddy:byte-buddy to v1.18.7 (#696) (renovate[bot], 2026-03-17)
- `1d4c4d9ea118` fix(deps): update dependency com.google.cloud:libraries-bom to v26.78.0 (#687) (renovate[bot], 2026-03-17)
- `8e407848f521` fix(deps): update dependency org.jetbrains.kotlin:kotlin-gradle-plugin to v2.3.20 (#715) (renovate[bot], 2026-03-17)
- `bf55b092af5f` fix(deps): update dependency io.micronaut.platform:micronaut-platform to v4.10.10 (#706) (renovate[bot], 2026-03-17)
- `d55d76a68209` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m17 (#709) (renovate[bot], 2026-03-17)
- `1e188cd55b37` fix(deps): update dependency com.google.devtools.ksp:com.google.devtools.ksp.gradle.plugin to v2.3.6 (#688) (renovate[bot], 2026-02-20)
- `4c9e2ad2195a` fix(deps): update dependency io.micronaut.oraclecloud:micronaut-oraclecloud-bom to v5.6.2 (#683) (renovate[bot], 2026-02-20)
- `485d3b7633b8` fix(deps): update dependency io.micronaut.gcp:micronaut-gcp-bom to v5.13.1 (#681) (renovate[bot], 2026-02-20)
- `15ec3e359b7d` fix(deps): update dependency io.micronaut.platform:micronaut-platform to v4.10.8 (#690) (renovate[bot], 2026-02-20)
- `6772c12d6781` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.12.0 (#692) (renovate[bot], 2026-02-20)
- `cfa4f0e90697` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.15 (#691) (renovate[bot], 2026-02-20)
- `431d11b00146` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.2 (#689) (renovate[bot], 2026-02-20)
- `93a4029579af` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.8 (#678) (renovate[bot], 2025-11-03)
- `7537ff154766` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.6 (#671) (renovate[bot], 2025-10-17)
- `bc873a637488` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.5.0 (#453) (renovate[bot], 2024-04-07)
- `7bf0fe13b9b0` fix(deps): update dependency com.google.devtools.ksp:com.google.devtools.ksp.gradle.plugin to v1.9.23-1.0.20 (#454) (renovate[bot], 2024-04-07)
- `9ee514a1f0f8` fix(deps): update dependency com.google.cloud:libraries-bom to v26.35.0 (#451) (renovate[bot], 2024-04-02)
- `134aaecdb4bd` fix(deps): update dependency net.bytebuddy:byte-buddy to v1.14.13 (#450) (renovate[bot], 2024-04-01)
- `f631fed12880` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.4.0 (#449) (renovate[bot], 2024-04-01)

### Security

- `84da0b458405` security: ignore GHSA-rcgg-9c38-7xpx (Sergio del Amo, 2026-05-18)

### Dependency Updates

- `2fae0a05aef4` chore: Bump version to 3.0.1-SNAPSHOT (micronaut-build, 2026-05-18)
- `2cd5205c92b0` chore: Bump version to 3.0.0-SNAPSHOT (micronaut-build, 2026-05-09)
- `fe3d013ba423` chore(deps): update actions/setup-java action to v5.2.0 (#775) (renovate[bot], 2026-05-08)
- `48f08af7e74b` chore(deps): update gradle/actions action to v6 (#721) (renovate[bot], 2026-04-08)
- `12d5418f70d4` chore: Bump version to 3.0.0-SNAPSHOT (micronaut-build, 2026-02-27)
- `d714296fd2aa` chore(deps): update actions/cache action to v5 (#702) (renovate[bot], 2026-02-23)
- `bfa189fb29c0` chore(deps): update dependency io.projectreactor.netty:reactor-netty-http to v1.3.3 (#685) (renovate[bot], 2026-02-20)
- `7018db393fee` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#679) (renovate[bot], 2026-02-20)
- `15886b7c8c91` chore(deps): update gradle to v9.3.1 (#686) (renovate[bot], 2026-02-20)
- `3e7c8c3d3390` chore(deps): update actions/checkout action to v6 (#697) (renovate[bot], 2026-02-20)
- `bbd07550b062` chore(deps): update softprops/action-gh-release action to v2.5.0 (#682) (renovate[bot], 2026-02-20)
- `2e1d6208da76` chore(deps): update graalvm/setup-graalvm action to v1.4.5 (#693) (renovate[bot], 2026-02-20)
- `4c9b3e7aaacc` chore(deps): update github artifact actions (#698) (renovate[bot], 2026-02-20)
- `4f8b44dc4b30` chore(deps): update gradle/actions action to v5 (#699) (renovate[bot], 2026-02-20)
- `6359d137b93a` chore(deps): update mikepenz/action-junit-report action to v6 (#700) (renovate[bot], 2026-02-20)
- `fa128a1d842a` chore(deps): update stefanzweifel/git-auto-commit-action action to v7 (#701) (renovate[bot], 2026-02-20)
- `bcd345942fea` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#676) (renovate[bot], 2025-11-03)
- `e1d37bf54319` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m8 (#677) (renovate[bot], 2025-11-03)

### Documentation

- `e0d7fcda9818` docs: clarify stale worktree checks in agent guidance (#745) (Álvaro Sánchez-Mariscal, 2026-04-04)
- `ce784fa8d0bb` docs: refresh contributor and agent guidance (#733) (Álvaro Sánchez-Mariscal, 2026-04-04)

### Internal

- `c04afd94a6e6` ci: rebase PR #729 workflow hardening (#729) (Álvaro Sánchez-Mariscal, 2026-04-04)
- `404b59955761` ci: pin GitHub Action refs to immutable SHAs (#734) (Álvaro Sánchez-Mariscal, 2026-04-04)
- `4c53916d8948` ci: java 25 in workflows (Sergio del Amo, 2026-02-20)

### Review Candidates

- `f5da8e4c8c65` update versions (Sergio del Amo, 2026-05-19)
- `51e622d1fe50` [skip ci] Release v3.0.0 (micronaut-build, 2026-05-18)
- `9e36e0a60be8` micronaut-test = "5.0.0" (Sergio del Amo, 2026-05-18)
- `dd4ce8216735` Update mikepenz/action-junit-report digest to 3a81627 (#780) (renovate[bot], 2026-05-18)
- `f264e5cc1a31` update versions (Sergio del Amo, 2026-05-17)
- `dd5106fcb1ea` Update common files (#779) (micronaut-build, 2026-05-14)
- `a2ae348278cb` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `88933a52c0b1` micronaut-platform = "5.0.0-RC1" (Sergio del Amo, 2026-05-13)
- `a8b1b912e6cf` [skip ci] Release v3.0.0-RC1 (micronaut-build, 2026-05-09)
- `26978f873d6a` Update versions to latest (#777) (Sergio del Amo, 2026-05-09)
- `280f7bd56cba` Update common files (#778) (micronaut-build, 2026-05-09)
- `6c6bf5d39a21` Update common files (#776) (micronaut-build, 2026-05-08)
- `23a15edeaaa6` Update common files (#773) (micronaut-build, 2026-05-01)
- `4a8da0a15375` Update common files (#769) (micronaut-build, 2026-04-26)
- `62537ae11b09` Update common files (#760) (micronaut-build, 2026-04-09)
- `00e06b4a8948` [object-storage] Update common files for branch 3.0.x (#749) (micronaut-build, 2026-04-08)
- `0041f93bcb7e` Pin floating emulator images used by integration tests (#732) (Álvaro Sánchez-Mariscal, 2026-04-03)
- `bbeef5a210fe` Stop exposing cloud test credentials to pull request workflows (#728) (Álvaro Sánchez-Mariscal, 2026-04-03)
- `1641a5c4b9b0` Migrates LocalStack integration away from the deprecated Testcontainers LocalStack API to the newer org.testcontainers.localstack.LocalStackContainer API (#724) (Issam Liqali, 2026-03-27)
- `80f327ee0407` [object-storage] Update common files for branch 3.0.x (#722) (micronaut-build, 2026-03-25)
- `ba1edff41524` [object-storage] Update common files for branch 3.0.x (#720) (micronaut-build, 2026-03-24)
- `f51dc85a6020` [object-storage] Update common files for branch 3.0.x (#717) (micronaut-build, 2026-03-19)
- `409647d4c27f` Update common files (#710) (micronaut-build, 2026-03-17)
- `e7e11b62315f` Migrate StreamingFileUploadRequest to the new API (#711) (Jonas Konrad, 2026-03-12)
- `a0d6d86dd175` [skip ci] Release v3.0.0-M2 (micronaut-build, 2026-02-27)
- `e469b54ef31a` enable oracle cloud module in object storage (#705) (Sergio del Amo, 2026-02-27)
- `bec87b6856f4` [skip ci] Release v3.0.0-M1 (micronaut-build, 2026-02-23)
- `f7339e0e46aa` Revert "[skip ci] Release v3.0.0-M1" (Sergio del Amo, 2026-02-23)
- `3380d0d4ebaa` [skip ci] Release v3.0.0-M1 (micronaut-build, 2026-02-23)
- `aad244ac9951` Migrate StreamingFileUploadRequest to the new API (#704) (Jonas Konrad, 2026-02-23)
- `dfc108474695` Update common files (#703) (micronaut-build, 2026-02-23)
- `032521eba115` kotlin-gradle-plugin = "2.3.10" (Sergio del Amo, 2026-02-20)
- `ac85c5844f1b` micronaut-logging = "2.0.0-M2" (Sergio del Amo, 2026-02-20)
- `020f00c78206` micronaut-validation = "5.0.0-M1" (Sergio del Amo, 2026-02-20)
- `daf418c7bbe6` micronaut-test-resources = "3.0.0-M6" (Sergio del Amo, 2026-02-20)
- `c6040a3208d2` micronaut-gcp = "6.0.0-M1" (Sergio del Amo, 2026-02-20)
- `39d802136bd8` micronaut-azure = "6.0.0-M1" (Sergio del Amo, 2026-02-20)
- `ea64f6162378` micronaut-aws = "5.0.0-M1" (Sergio del Amo, 2026-02-20)
- `b4de9e936b5a` micronaut-test = "5.0.0-M6" (Sergio del Amo, 2026-02-20)
- `ddba32c922c4` micronaut = "5.0.0-M13" (Sergio del Amo, 2026-02-20)
- `1f2428459e20` Update common files (#680) (micronaut-build, 2026-02-20)
- `dfa924c4806b` Link to Control Panel [skip ci] (Álvaro Sánchez-Mariscal, 2025-12-11)
- `bdb40508735b` [WIP] Replace Micronaut nullability annotations with JSpecify (#695) (Copilot, 2025-12-02)
- `369e09c317b2` Micronaut 5 compatibility and release prep (#673) (issam liqali, 2025-11-03)
- `9879341ae972` Update common files (#675) (micronaut-build, 2025-11-03)
- `2d66965e0262` Update common files (#674) (micronaut-build, 2025-10-21)
- `0603953b674b` Update common files (#672) (micronaut-build, 2025-10-20)
- `717152a170e2` Update common files (#670) (micronaut-build, 2025-10-17)
- `3a04a901d6c9` Micronaut Gradle build plugin 8.0.0-M4 (Sergio del Amo, 2025-10-15)
- `ac5736394faa` gradle 9.1 (Sergio del Amo, 2025-10-15)
- `6df50acd747e` Merge branch '2.10.x' into 3.0.x (Sergio del Amo, 2025-10-15)
- `52eb8314ab89` Update common files (#448) (micronaut-build, 2024-03-28)
- `84f2f3fe3e3b` breaks: del and doc deprecations for MN 5 (#445) (Dean Wette, 2024-03-27)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` .github/workflows/update-gradle-wrapper.yml
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.objectstorage-base.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.objectstorage-example.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.objectstorage-module.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` object-storage-aws/build.gradle.kts
- `M` object-storage-azure/build.gradle.kts
- `M` object-storage-core/build.gradle.kts
- `M` object-storage-gcp/build.gradle.kts
- `M` object-storage-local/build.gradle.kts
- `M` object-storage-oracle-cloud/build.gradle.kts
- `M` object-storage-tck/build.gradle.kts
- `M` settings.gradle.kts
- `A` test-suite-graal/build.gradle.kts
- `M` test-suite-utils/build.gradle.kts

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
- `A` doc-examples/example-groovy/src/main/groovy/example/BucketService.groovy
- `A` doc-examples/example-groovy/src/main/groovy/example/PresignedUploadController.groovy
- `M` doc-examples/example-groovy/src/main/groovy/example/ProfileService.groovy
- `M` doc-examples/example-groovy/src/main/groovy/example/UploadController.groovy
- `M` doc-examples/example-groovy/src/test/groovy/example/ProfileServiceSpec.groovy
- `M` doc-examples/example-groovy/src/test/groovy/example/UploadControllerSpec.groovy
- `M` doc-examples/example-java/build.gradle.kts
- `A` doc-examples/example-java/src/main/java/example/BucketService.java
- `A` doc-examples/example-java/src/main/java/example/PresignedUploadController.java
- `M` doc-examples/example-java/src/main/java/example/ProfileService.java
- `M` doc-examples/example-java/src/main/java/example/UploadController.java
- `M` doc-examples/example-java/src/main/java/example/aws/S3ClientBuilderCustomizer.java
- `M` doc-examples/example-java/src/main/java/example/azure/BlobServiceClientBuilderCustomizer.java
- `M` doc-examples/example-java/src/main/java/example/gcp/StorageOptionsBuilderCustomizer.java
- `M` doc-examples/example-java/src/main/java/example/oraclecloud/ObjectStorageClientBuilderCustomizer.java
- `M` doc-examples/example-java/src/test/groovy/example/ProfileServiceSpec.groovy
- `M` doc-examples/example-java/src/test/groovy/example/UploadControllerSpec.groovy
- `M` doc-examples/example-kotlin/build.gradle.kts
- `A` doc-examples/example-kotlin/src/main/kotlin/example/BucketService.kt
- `A` doc-examples/example-kotlin/src/main/kotlin/example/PresignedUploadController.kt
- `M` doc-examples/example-kotlin/src/main/kotlin/example/ProfileService.kt
- `M` doc-examples/example-kotlin/src/main/kotlin/example/UploadController.kt
- `M` doc-examples/example-kotlin/src/test/groovy/example/ProfileServiceSpec.groovy
- `M` doc-examples/example-kotlin/src/test/groovy/example/UploadControllerSpec.groovy
- `M` src/main/docs/guide/aws.adoc
- `M` src/main/docs/guide/azure.adoc
- `A` src/main/docs/guide/breaks.adoc
- `A` src/main/docs/guide/bucketManagement.adoc
- `A` src/main/docs/guide/control-panel.adoc
- `M` src/main/docs/guide/gcp.adoc
- `M` src/main/docs/guide/introduction.adoc
- `M` src/main/docs/guide/local.adoc
- `M` src/main/docs/guide/oracleCloud.adoc
- `A` src/main/docs/guide/paginatedListing.adoc
- `A` src/main/docs/guide/preSignedUploads.adoc
- `M` src/main/docs/guide/quickStart.adoc
- `A` src/main/docs/guide/reactiveOperations.adoc
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
- `M` .github/workflows/aws.yml
- `M` .github/workflows/azure.yml
- `M` .github/workflows/central-sync.yml
- `M` .github/workflows/gcp.yml
- `M` .github/workflows/graalvm-dev.yml
- `M` .github/workflows/oci.yml
- `M` .github/workflows/publish-snapshot.yml
- `A` .github/workflows/sonatype.yml
- `M` .gitignore
- `A` .sdkmanrc
- `A` AGENTS.md
- `M` CONTRIBUTING.md
- `M` MAINTAINING.md
- `M` config/accepted-api-changes.json
- `M` config/checkstyle/checkstyle.xml
- `A` object-storage-aws/src/main/java/io/micronaut/objectstorage/aws/AwsS3BucketOperations.java
- `M` object-storage-aws/src/main/java/io/micronaut/objectstorage/aws/AwsS3Configuration.java
- `M` object-storage-aws/src/main/java/io/micronaut/objectstorage/aws/AwsS3ObjectStorageEntry.java
- `M` object-storage-aws/src/main/java/io/micronaut/objectstorage/aws/AwsS3Operations.java
- `A` object-storage-aws/src/main/java/io/micronaut/objectstorage/aws/AwsS3ReactiveBucketOperations.java
- `A` object-storage-aws/src/main/java/io/micronaut/objectstorage/aws/AwsS3ReactiveOperations.java
- `A` object-storage-aws/src/main/java/io/micronaut/objectstorage/aws/AwsS3ResourceLoader.java
- `A` object-storage-aws/src/main/java/io/micronaut/objectstorage/aws/AwsS3ResourceLoaderFactory.java
- `A` object-storage-azure/src/main/java/io/micronaut/objectstorage/azure/AzureBlobBucketOperations.java
- `A` object-storage-azure/src/main/java/io/micronaut/objectstorage/azure/AzureBlobReactiveBucketOperations.java
- `M` object-storage-azure/src/main/java/io/micronaut/objectstorage/azure/AzureBlobStorageConfiguration.java
- `M` object-storage-azure/src/main/java/io/micronaut/objectstorage/azure/AzureBlobStorageEntry.java
- `M` object-storage-azure/src/main/java/io/micronaut/objectstorage/azure/AzureBlobStorageFactory.java
- `M` object-storage-azure/src/main/java/io/micronaut/objectstorage/azure/AzureBlobStorageOperations.java
- `A` object-storage-azure/src/main/java/io/micronaut/objectstorage/azure/AzureBlobStorageReactiveOperations.java
- `A` object-storage-azure/src/main/java/io/micronaut/objectstorage/azure/AzureBlobStorageResourceLoader.java
- `A` object-storage-azure/src/main/java/io/micronaut/objectstorage/azure/AzureBlobStorageResourceLoaderFactory.java
- `A` object-storage-azure/src/main/resources/META-INF/native-image/io.micronaut.objectstorage/micronaut-object-storage-azure/native-image.properties
- `M` object-storage-core/src/main/java/io/micronaut/objectstorage/DefaultInputStreamMapper.java
- `M` object-storage-core/src/main/java/io/micronaut/objectstorage/InputStreamMapper.java
- `M` object-storage-core/src/main/java/io/micronaut/objectstorage/ObjectStorageEntry.java
- `M` object-storage-core/src/main/java/io/micronaut/objectstorage/ObjectStorageOperations.java
- `A` object-storage-core/src/main/java/io/micronaut/objectstorage/ReactiveObjectStorageOperations.java
- `A` object-storage-core/src/main/java/io/micronaut/objectstorage/bucket/BucketEntry.java
- `A` object-storage-core/src/main/java/io/micronaut/objectstorage/bucket/BucketOperations.java
- `A` object-storage-core/src/main/java/io/micronaut/objectstorage/bucket/ReactiveBucketOperations.java
- `M` object-storage-core/src/main/java/io/micronaut/objectstorage/configuration/AbstractObjectStorageConfiguration.java
- `M` object-storage-core/src/main/java/io/micronaut/objectstorage/configuration/AbstractObjectStorageModuleConfiguration.java
- `A` object-storage-core/src/main/java/io/micronaut/objectstorage/configuration/EachPropertyContainsEntriesCondition.java
- `M` object-storage-core/src/main/java/io/micronaut/objectstorage/configuration/ToggeableCondition.java
- `A` object-storage-core/src/main/java/io/micronaut/objectstorage/internal/DefaultReactiveBucketOperations.java
- `A` object-storage-core/src/main/java/io/micronaut/objectstorage/internal/DefaultReactiveObjectStorageOperations.java
- `M` object-storage-core/src/main/java/io/micronaut/objectstorage/request/AbstractUploadRequest.java
- `M` object-storage-core/src/main/java/io/micronaut/objectstorage/request/BytesUploadRequest.java
- `M` object-storage-core/src/main/java/io/micronaut/objectstorage/request/CompletedFileUploadRequest.java
- `A` object-storage-core/src/main/java/io/micronaut/objectstorage/request/CreatePresignedUploadRequest.java
- `M` object-storage-core/src/main/java/io/micronaut/objectstorage/request/FileUploadRequest.java
- `A` object-storage-core/src/main/java/io/micronaut/objectstorage/request/ListObjectsRequest.java
- `D` object-storage-core/src/main/java/io/micronaut/objectstorage/request/PresignRequest.java
- `M` object-storage-core/src/main/java/io/micronaut/objectstorage/request/StreamingFileUploadRequest.java
- `M` object-storage-core/src/main/java/io/micronaut/objectstorage/request/UploadRequest.java
- `A` object-storage-core/src/main/java/io/micronaut/objectstorage/resource/AbstractObjectStorageResourceLoader.java
- `A` object-storage-core/src/main/java/io/micronaut/objectstorage/resource/NamedObjectStorageResourceLoader.java
- `A` object-storage-core/src/main/java/io/micronaut/objectstorage/resource/ObjectStorageNamedResourceLoaderFactory.java
- `A` object-storage-core/src/main/java/io/micronaut/objectstorage/resource/ObjectStorageResourceParser.java
- `M` object-storage-core/src/main/java/io/micronaut/objectstorage/response/DefaultUploadResponse.java
- `A` object-storage-core/src/main/java/io/micronaut/objectstorage/response/ListObjectsResponse.java
- `D` object-storage-core/src/main/java/io/micronaut/objectstorage/response/PresignResponse.java
- `A` object-storage-core/src/main/java/io/micronaut/objectstorage/response/PresignedUpload.java
- `M` object-storage-core/src/main/java/io/micronaut/objectstorage/response/UploadResponse.java
- `A` object-storage-gcp/src/main/java/io/micronaut/objectstorage/googlecloud/GoogleCloudBucketOperations.java
- `A` object-storage-gcp/src/main/java/io/micronaut/objectstorage/googlecloud/GoogleCloudReactiveBucketOperations.java
- `M` object-storage-gcp/src/main/java/io/micronaut/objectstorage/googlecloud/GoogleCloudStorageConfiguration.java
- `M` object-storage-gcp/src/main/java/io/micronaut/objectstorage/googlecloud/GoogleCloudStorageEntry.java
- `M` object-storage-gcp/src/main/java/io/micronaut/objectstorage/googlecloud/GoogleCloudStorageFactory.java
- `M` object-storage-gcp/src/main/java/io/micronaut/objectstorage/googlecloud/GoogleCloudStorageOperations.java
- `A` object-storage-gcp/src/main/java/io/micronaut/objectstorage/googlecloud/GoogleCloudStorageReactiveOperations.java
- `A` object-storage-gcp/src/main/java/io/micronaut/objectstorage/googlecloud/GoogleCloudStorageResourceLoader.java
- `A` object-storage-gcp/src/main/java/io/micronaut/objectstorage/googlecloud/GoogleCloudStorageResourceLoaderFactory.java
- `D` object-storage-local/src/main/java/io/micronaut/objectstorage/local/LocalPresignController.java
- `D` object-storage-local/src/main/java/io/micronaut/objectstorage/local/LocalPresignStore.java
- `A` object-storage-local/src/main/java/io/micronaut/objectstorage/local/LocalStorageBucketOperations.java
- `M` object-storage-local/src/main/java/io/micronaut/objectstorage/local/LocalStorageConfiguration.java
- `M` object-storage-local/src/main/java/io/micronaut/objectstorage/local/LocalStorageEntry.java
- `M` object-storage-local/src/main/java/io/micronaut/objectstorage/local/LocalStorageModuleConfiguration.java
- `M` object-storage-local/src/main/java/io/micronaut/objectstorage/local/LocalStorageOperations.java
- `A` object-storage-local/src/main/java/io/micronaut/objectstorage/local/LocalStorageReactiveBucketOperations.java
- `A` object-storage-local/src/main/java/io/micronaut/objectstorage/local/LocalStorageReactiveOperations.java
- `A` object-storage-oracle-cloud/src/main/java/io/micronaut/objectstorage/oraclecloud/OracleCloudBucketOperations.java
- `A` object-storage-oracle-cloud/src/main/java/io/micronaut/objectstorage/oraclecloud/OracleCloudReactiveBucketOperations.java
- `M` object-storage-oracle-cloud/src/main/java/io/micronaut/objectstorage/oraclecloud/OracleCloudStorageConfiguration.java
- `M` object-storage-oracle-cloud/src/main/java/io/micronaut/objectstorage/oraclecloud/OracleCloudStorageEntry.java
- `M` object-storage-oracle-cloud/src/main/java/io/micronaut/objectstorage/oraclecloud/OracleCloudStorageOperations.java
- `A` object-storage-oracle-cloud/src/main/java/io/micronaut/objectstorage/oraclecloud/OracleCloudStorageReactiveOperations.java
- `A` object-storage-oracle-cloud/src/main/java/io/micronaut/objectstorage/oraclecloud/OracleCloudStorageResourceLoader.java
- `A` object-storage-oracle-cloud/src/main/java/io/micronaut/objectstorage/oraclecloud/OracleCloudStorageResourceLoaderFactory.java
- `A` osv-scanner.toml

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `A` object-storage-aws/src/test/groovy/io/micronaut/objectstorage/aws/AbstractAwsS3BucketSpec.groovy
- `A` object-storage-aws/src/test/groovy/io/micronaut/objectstorage/aws/AbstractAwsS3ReactiveSpec.groovy
- `M` object-storage-aws/src/test/groovy/io/micronaut/objectstorage/aws/AbstractAwsS3Spec.groovy
- `A` object-storage-aws/src/test/groovy/io/micronaut/objectstorage/aws/AwsS3BucketCloudSpec.groovy
- `A` object-storage-aws/src/test/groovy/io/micronaut/objectstorage/aws/AwsS3BucketLocalStackSpec.groovy
- `M` object-storage-aws/src/test/groovy/io/micronaut/objectstorage/aws/AwsS3ConfigurationSpec.groovy
- `A` object-storage-aws/src/test/groovy/io/micronaut/objectstorage/aws/AwsS3LegacyListObjectsSpec.groovy
- `M` object-storage-aws/src/test/groovy/io/micronaut/objectstorage/aws/AwsS3OperationsCloudSpec.groovy
- `M` object-storage-aws/src/test/groovy/io/micronaut/objectstorage/aws/AwsS3OperationsLocalstackSpec.groovy
- `M` object-storage-aws/src/test/groovy/io/micronaut/objectstorage/aws/AwsS3OperationsUploadWithConsumerSpec.groovy
- `A` object-storage-aws/src/test/groovy/io/micronaut/objectstorage/aws/AwsS3PaginationSpec.groovy
- `A` object-storage-aws/src/test/groovy/io/micronaut/objectstorage/aws/AwsS3PresignedUploadSpec.groovy
- `A` object-storage-aws/src/test/groovy/io/micronaut/objectstorage/aws/AwsS3ReactiveBucketOperationsSpec.groovy
- `A` object-storage-aws/src/test/groovy/io/micronaut/objectstorage/aws/AwsS3ReactiveOperationsLocalstackSpec.groovy
- `A` object-storage-aws/src/test/groovy/io/micronaut/objectstorage/aws/AwsS3ResourceLoaderSpec.groovy
- `A` object-storage-azure/src/test/groovy/io/micronaut/objectstorage/azure/AbstractAzureBlobStorageReactiveSpec.groovy
- `M` object-storage-azure/src/test/groovy/io/micronaut/objectstorage/azure/AbstractAzureBlobStorageSpec.groovy
- `A` object-storage-azure/src/test/groovy/io/micronaut/objectstorage/azure/AbstractAzureBucketSpec.groovy
- `A` object-storage-azure/src/test/groovy/io/micronaut/objectstorage/azure/AzureBlobReactiveBucketOperationsSpec.groovy
- `M` object-storage-azure/src/test/groovy/io/micronaut/objectstorage/azure/AzureBlobStorageAzuriteSpec.groovy
- `M` object-storage-azure/src/test/groovy/io/micronaut/objectstorage/azure/AzureBlobStorageCloudSpec.groovy
- `A` object-storage-azure/src/test/groovy/io/micronaut/objectstorage/azure/AzureBlobStorageFactorySpec.groovy
- `A` object-storage-azure/src/test/groovy/io/micronaut/objectstorage/azure/AzureBlobStoragePaginationSpec.groovy
- `A` object-storage-azure/src/test/groovy/io/micronaut/objectstorage/azure/AzureBlobStoragePresignedUploadSpec.groovy
- `A` object-storage-azure/src/test/groovy/io/micronaut/objectstorage/azure/AzureBlobStorageReactiveAzuriteSpec.groovy
- `A` object-storage-azure/src/test/groovy/io/micronaut/objectstorage/azure/AzureBlobStorageResourceLoaderSpec.groovy
- `A` object-storage-azure/src/test/groovy/io/micronaut/objectstorage/azure/AzureBlobStorageUploadOptionsSpec.groovy
- `A` object-storage-azure/src/test/groovy/io/micronaut/objectstorage/azure/AzureBucketAzuriteSpec.groovy
- `A` object-storage-azure/src/test/groovy/io/micronaut/objectstorage/azure/AzureBucketCloudSpec.groovy
- `A` object-storage-azure/src/test/groovy/io/micronaut/objectstorage/azure/AzureNativeImageConfigurationSpec.groovy
- `A` object-storage-core/src/test/groovy/io/micronaut/objectstorage/ObjectStorageOperationsPaginationFallbackSpec.groovy
- `A` object-storage-core/src/test/groovy/io/micronaut/objectstorage/ObjectStorageOperationsPresignedUploadFallbackSpec.groovy
- `A` object-storage-core/src/test/groovy/io/micronaut/objectstorage/internal/DefaultReactiveBucketOperationsSpec.groovy
- `A` object-storage-core/src/test/groovy/io/micronaut/objectstorage/internal/DefaultReactiveObjectStorageOperationsSpec.groovy
- `D` object-storage-core/src/test/groovy/io/micronaut/objectstorage/request/CompletedFileUploadSpec.groovy
- `A` object-storage-core/src/test/groovy/io/micronaut/objectstorage/request/CreatePresignedUploadRequestSpec.groovy
- `A` object-storage-core/src/test/groovy/io/micronaut/objectstorage/request/ListObjectsRequestSpec.groovy
- `A` object-storage-core/src/test/groovy/io/micronaut/objectstorage/request/StreamingFileUploadRequestSpec.groovy
- `D` object-storage-core/src/test/groovy/io/micronaut/objectstorage/request/StreamingFileUploadSpec.groovy
- `A` object-storage-core/src/test/groovy/io/micronaut/objectstorage/resource/NamedObjectStorageResourceLoaderSpec.groovy
- `A` object-storage-core/src/test/groovy/io/micronaut/objectstorage/response/ListObjectsResponseSpec.groovy
- `A` object-storage-gcp/src/test/groovy/io/micronaut/objectstorage/googlecloud/AbstractGoogleCloudBucketSpec.groovy
- `A` object-storage-gcp/src/test/groovy/io/micronaut/objectstorage/googlecloud/AbstractGoogleCloudStorageReactiveSpec.groovy
- `M` object-storage-gcp/src/test/groovy/io/micronaut/objectstorage/googlecloud/AbstractGoogleCloudStorageSpec.groovy
- `A` object-storage-gcp/src/test/groovy/io/micronaut/objectstorage/googlecloud/GoogleCloudBucketCloudSpec.groovy
- `A` object-storage-gcp/src/test/groovy/io/micronaut/objectstorage/googlecloud/GoogleCloudBucketFakeGcsServerSpec.groovy
- `M` object-storage-gcp/src/test/groovy/io/micronaut/objectstorage/googlecloud/GoogleCloudStorageCloudSpec.groovy
- `M` object-storage-gcp/src/test/groovy/io/micronaut/objectstorage/googlecloud/GoogleCloudStorageFakeGcsServerSpec.groovy
- `M` object-storage-gcp/src/test/groovy/io/micronaut/objectstorage/googlecloud/GoogleCloudStorageOperationsUploadWithConsumerSpec.groovy
- `A` object-storage-gcp/src/test/groovy/io/micronaut/objectstorage/googlecloud/GoogleCloudStoragePaginationSpec.groovy
- `A` object-storage-gcp/src/test/groovy/io/micronaut/objectstorage/googlecloud/GoogleCloudStoragePresignedUploadSpec.groovy
- `A` object-storage-gcp/src/test/groovy/io/micronaut/objectstorage/googlecloud/GoogleCloudStorageReactiveFakeGcsServerSpec.groovy
- `A` object-storage-gcp/src/test/groovy/io/micronaut/objectstorage/googlecloud/GoogleCloudStorageResourceLoaderSpec.groovy
- `A` object-storage-local/src/test/groovy/io/micronaut/objectstorage/local/LocalStorageBucketOperationsSpec.groovy
- `M` object-storage-local/src/test/groovy/io/micronaut/objectstorage/local/LocalStorageConfigurationSpec.groovy
- `A` object-storage-local/src/test/groovy/io/micronaut/objectstorage/local/LocalStorageFilePermissionsSpec.groovy
- `A` object-storage-local/src/test/groovy/io/micronaut/objectstorage/local/LocalStoragePaginationSpec.groovy
- `M` object-storage-local/src/test/groovy/io/micronaut/objectstorage/local/LocalStoragePathTraversalSpec.groovy
- `A` object-storage-local/src/test/groovy/io/micronaut/objectstorage/local/LocalStorageReactiveNamedSpec.groovy
- `A` object-storage-local/src/test/groovy/io/micronaut/objectstorage/local/LocalStorageReactivePrimarySpec.groovy
- `A` object-storage-local/src/test/groovy/io/micronaut/objectstorage/local/LocalStorageReactiveSpec.groovy
- `A` object-storage-local/src/test/groovy/io/micronaut/objectstorage/local/LocalStorageReservedMetadataSpec.groovy
- `A` object-storage-local/src/test/groovy/io/micronaut/objectstorage/local/LocalStorageResourceLoaderSpec.groovy
- `M` object-storage-local/src/test/groovy/io/micronaut/objectstorage/local/LocalStorageSpec.groovy
- `A` object-storage-oracle-cloud/src/test/groovy/io/micronaut/objectstorage/oraclecloud/AbstractOracleCloudBucketSpec.groovy
- `A` object-storage-oracle-cloud/src/test/groovy/io/micronaut/objectstorage/oraclecloud/AbstractOracleCloudStorageReactiveSpec.groovy
- `M` object-storage-oracle-cloud/src/test/groovy/io/micronaut/objectstorage/oraclecloud/AbstractOracleCloudStorageSpec.groovy
- `A` object-storage-oracle-cloud/src/test/groovy/io/micronaut/objectstorage/oraclecloud/OracleCloudBucketCloudSpec.groovy
- `A` object-storage-oracle-cloud/src/test/groovy/io/micronaut/objectstorage/oraclecloud/OracleCloudBucketOperationsSpec.groovy
- `A` object-storage-oracle-cloud/src/test/groovy/io/micronaut/objectstorage/oraclecloud/OracleCloudReactiveBucketOperationsSpec.groovy
- `M` object-storage-oracle-cloud/src/test/groovy/io/micronaut/objectstorage/oraclecloud/OracleCloudStorageCloudSpec.groovy
- `M` object-storage-oracle-cloud/src/test/groovy/io/micronaut/objectstorage/oraclecloud/OracleCloudStorageOciEmulatorSpec.groovy
- `M` object-storage-oracle-cloud/src/test/groovy/io/micronaut/objectstorage/oraclecloud/OracleCloudStorageOperationsUploadWithConsumerSpec.groovy
- `A` object-storage-oracle-cloud/src/test/groovy/io/micronaut/objectstorage/oraclecloud/OracleCloudStoragePaginationSpec.groovy
- `A` object-storage-oracle-cloud/src/test/groovy/io/micronaut/objectstorage/oraclecloud/OracleCloudStoragePresignedUploadSpec.groovy
- `A` object-storage-oracle-cloud/src/test/groovy/io/micronaut/objectstorage/oraclecloud/OracleCloudStorageReactiveOciEmulatorSpec.groovy
- `A` object-storage-oracle-cloud/src/test/groovy/io/micronaut/objectstorage/oraclecloud/OracleCloudStorageReactiveOperationsSpec.groovy
- `A` object-storage-oracle-cloud/src/test/groovy/io/micronaut/objectstorage/oraclecloud/OracleCloudStorageResourceLoaderSpec.groovy
- `A` object-storage-tck/src/main/groovy/io/micronaut/objectstorage/BucketOperationsSpecification.groovy
- `M` object-storage-tck/src/main/groovy/io/micronaut/objectstorage/ObjectStorageOperationsSpecification.groovy
- `A` object-storage-tck/src/main/groovy/io/micronaut/objectstorage/ReactiveObjectStorageOperationsSpecification.groovy
- `A` test-suite-graal/src/test/java/io/micronaut/objectstorage/graal/LocalStorageNativeTest.java
- `M` test-suite-utils/src/main/java/io/micronaut/objectstorage/test/ObjectStorageTestConstants.java

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

