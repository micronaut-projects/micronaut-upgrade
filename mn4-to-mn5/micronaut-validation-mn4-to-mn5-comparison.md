
  Full report: micronaut-validation-mn4-to-mn5-comparison.md:1

  Scope:

  - Previous: mn4/micronaut-validation, branch 4.12.x, commit e01927d40045, clean
  - Current: mn5/micronaut-validation, branch 5.0.x, commit 99c4c9386605, clean
  - Delta: 118 commit candidates, 123 changed files

  Release-note draft:

  ## Micronaut Validation 5.0

  ### Breaking Changes

  - Deprecated `DefaultValidator.requireNonNull(String, T)` and `DefaultValidator.requireNonEmpty(String, String)` are no longer public API. They are now private implementation details.
  - Deprecated `ConstraintValidator` context method `getMessageTemplate()` was removed. It was unused and has no replacement.

  ### Compatibility

  - Updated for the Micronaut 5 baseline.
  - Validation APIs and examples now use JSpecify nullability annotations instead of `io.micronaut.core.annotation.NonNull` / `Nullable`.
  - Reactive validation test support moved from Micronaut RxJava 2 to Micronaut RxJava 3.

  ### Fixes / Improvements

  - Validator initialization failures now preserve the original cause in the thrown `ValidationException`.
  - `ValidationPath.removeLast()` is now public and overrides the collection API method, aligning with newer Java collection APIs.

  ### Documentation

  - Custom validator examples were updated to JSpecify annotations.
  - The Java custom validator bean example no longer shows `@Introspected` on the validator bean.

  Important dependency/tooling changes:

  - Micronaut Core: 4.10.3 -> 5.0.0-RC2
  - Micronaut Platform: 4.9.3 -> 5.0.0-M3
  - Micronaut Gradle plugin: 4.5.4 -> 5.0.0-M1
  - Gradle wrapper: 8.14.3 -> 9.5.0
  - Micronaut Kotlin: 4.7.0 -> 5.0.0-M1
  - Micronaut Reactor: 3.9.0 -> 4.0.0-RC1
  - Micronaut RxJava2: 2.8.0 -> removed
  - Micronaut RxJava3: not present -> 4.0.0-M1
  - Jakarta Validation API remains 3.1.1
  - Jakarta Validation TCK remains 3.0.1
  - JMH added at 1.37

  Tests were not run; this was a static repository comparison.

# Release Note Comparison

Generated: 2026-05-06 16:24 UTC
Comparison: `mn4` -> `mn5`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-validation` | `4.12.x` | `e01927d40045` | `git@github.com:micronaut-projects/micronaut-validation.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-validation` | `5.0.x` | `99c4c9386605` | `git@github.com:micronaut-projects/micronaut-validation.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-validation`
- Commit candidates found: 118
- File changes listed: 123
- Version values listed: 40
- File status counts: A=22, D=1, M=100

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `4.12.1-SNAPSHOT` | `5.0.0-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.arquillian-container` | `org.jboss.arquillian.container:arquillian-container-test-spi:1.9.5.Final` | `org.jboss.arquillian.container:arquillian-container-test-spi:1.10.1.Final` | `changed` |
| `gradle/libs.versions.toml` | `libraries.gradle-kotlin` | `org.jetbrains.kotlin:kotlin-gradle-plugin:1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.gradle-kotlin-allopen` | `org.jetbrains.kotlin:kotlin-allopen:1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.gradle-kotlin-noarg` | `org.jetbrains.kotlin:kotlin-noarg:1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.gradle-ksp` | `com.google.devtools.ksp:symbol-processing-gradle-plugin:1.9.25-1.0.20` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.gradle-micronaut` | `io.micronaut.gradle:micronaut-gradle-plugin:4.5.4` | `io.micronaut.gradle:micronaut-gradle-plugin:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.groovy-bom` | `org.apache.groovy:groovy-bom:4.0.28` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.jakarta-validation-tck-tests` | `jakarta-validation-tck-tests:3.0.1` | `jakarta-validation-tck-tests:3.0.1` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.javax-annotation-api` | `javax.annotation:javax.annotation-api:1.3.2` | `javax.annotation:javax.annotation-api:1.3.2` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.jmh-core` | `not present` | `org.openjdk.jmh:jmh-core:1.37` | `added` |
| `gradle/libs.versions.toml` | `libraries.jmh-generator-annprocess` | `not present` | `org.openjdk.jmh:jmh-generator-annprocess:1.37` | `added` |
| `gradle/libs.versions.toml` | `libraries.managed-validation` | `jakarta.validation:jakarta.validation-api:3.1.1` | `jakarta.validation:jakarta.validation-api:3.1.1` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.micronaut-kotlin` | `micronaut-kotlin:4.7.0` | `micronaut-kotlin:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-reactor` | `micronaut-reactor:3.9.0` | `micronaut-reactor:4.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-rxjava2` | `micronaut-rxjava2:2.8.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-rxjava3` | `not present` | `micronaut-rxjava3:4.0.0-M1` | `added` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test` | `micronaut-test:4.9.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.spotbugs` | `com.github.spotbugs:spotbugs-annotations:4.9.5` | `com.github.spotbugs:spotbugs-annotations:4.9.8` | `changed` |
| `gradle/libs.versions.toml` | `versions.arquillian-container` | `1.9.5.Final` | `1.10.1.Final` | `changed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.28` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.jakarta-validation-tck` | `3.0.1` | `3.0.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.javax-annotation-api` | `1.3.2` | `1.3.2` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.jmh` | `not present` | `1.37` | `added` |
| `gradle/libs.versions.toml` | `versions.kotlin-gradle-plugin` | `1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.ksp-gradle-plugin` | `1.9.25-1.0.20` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.managed-validation` | `3.1.1` | `3.1.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.3` | `5.0.0-RC2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `2.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.5.4` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-kotlin` | `4.7.0` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-platform` | `4.9.3` | `5.0.0-M3` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-reactor` | `3.9.0` | `4.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-rxjava2` | `2.8.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-rxjava3` | `not present` | `4.0.0-M1` | `added` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.9.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.spotbugs` | `4.9.5` | `4.9.8` | `changed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.0` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `f59ad6a0ad4e` remove unsued gradle plugins (Sergio del Amo, 2026-05-05)
- `807240ae3c85` remove PackageConfiguratinoInjectProcessor (Sergio del Amo, 2025-12-04)
- `6a800c726b16` remove references to BeanIntrospectionModule (Sergio del Amo, 2025-12-04)
- `121b66553ae8` add public modifier and @Override to removeLast (Sergio del Amo, 2025-12-04)
- `169e0da32987` Remove Introspected from MyValidatorBean example (#336) (Jeremy Grelle, 2024-05-30)
- `bc67a1cffdbf` breaking: del deprecated code for MN 5 & doc changes. (#326) (Dean Wette, 2024-03-18)

### Fixes

- `ebc7b38933dd` fix(deps): update dependency org.openjdk.jmh:jmh-generator-annprocess to v1.37 (#547) (renovate[bot], 2026-04-17)
- `3724668879a0` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m22 (#618) (renovate[bot], 2026-04-17)
- `9258d8a19541` fix(deps): update kotlin monorepo to v2.3.20 (#615) (renovate[bot], 2026-03-30)
- `f2ef8da90434` fix(deps): update dependency org.jboss.arquillian.container:arquillian-container-test-spi to v1.10.1.final (#613) (renovate[bot], 2026-03-30)
- `1192c528efc8` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m18 (#609) (renovate[bot], 2026-03-30)
- `5f31b934c893` fix(deps): update kotlin monorepo to v2.3.10 (#597) (renovate[bot], 2026-02-23)
- `1878ac520574` fix(deps): update dependency com.google.devtools.ksp:symbol-processing-gradle-plugin to v2.3.6 (#574) (renovate[bot], 2026-02-23)
- `179e087564cb` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m13 (renovate[bot], 2026-02-20)
- `9b63e68d31bb` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.2 (#606) (renovate[bot], 2026-02-04)
- `fe3d4645bc83` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m8 (#602) (renovate[bot], 2026-01-13)
- `611b1cbeeee9` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m7 (#600) (renovate[bot], 2026-01-11)
- `2008ef2fe200` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m6 (#595) (renovate[bot], 2025-12-23)
- `97175af67bbe` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m3 (#591) (renovate[bot], 2025-12-12)
- `17bb68bebf63` fix(deps): update kotlin monorepo to v2.2.21 (#573) (renovate[bot], 2025-12-04)
- `2ff55fcc1096` fix(deps): update dependency org.jboss.arquillian.container:arquillian-container-test-spi to v1.10.0.final (renovate[bot], 2025-12-04)
- `14e903570680` fix(deps): update dependency com.github.spotbugs:spotbugs-annotations to v4.9.8 (#561) (renovate[bot], 2025-12-04)
- `ae1f2d383320` fix(deps): update dependency io.micronaut.rxjava2:micronaut-rxjava2-bom to v2.9.0 (#578) (renovate[bot], 2025-12-04)
- `8626f0d6225f` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#582) (renovate[bot], 2025-12-04)
- `bb6cc4ac779c` fix(deps): update dependency io.micronaut.reactor:micronaut-reactor-bom to v3.9.1 (#576) (renovate[bot], 2025-12-04)
- `1770019c4ddc` fix(deps): update dependency org.apache.groovy:groovy-bom to v5 (#586) (renovate[bot], 2025-12-04)
- `1386ce554d40` fix(deps): update dependency org.apache.groovy:groovy-bom to v4.0.29 (#567) (renovate[bot], 2025-11-03)
- `deeaef13ff0c` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.8 (#568) (renovate[bot], 2025-11-03)
- `3fdadf16a517` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.1 (#570) (renovate[bot], 2025-11-03)
- `c48be67d36b3` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.3.6 (#345) (renovate[bot], 2024-07-08)
- `a0b227ad2a4a` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.5.0 (#354) (renovate[bot], 2024-05-30)
- `754fa35b47a8` fix(deps): update dependency jakarta.validation:jakarta.validation-api to v3.1.0 (#362) (renovate[bot], 2024-05-30)
- `cd06b87f0799` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.4.1 (#347) (renovate[bot], 2024-04-11)
- `e960e414a49b` fix(deps): update dependency org.apache.groovy:groovy-bom to v4.0.21 (#348) (renovate[bot], 2024-04-11)
- `3b9203652d62` fix(deps): update dependency io.micronaut.kotlin:micronaut-kotlin-bom to v4.3.0 (#349) (renovate[bot], 2024-04-11)
- `88129d9f2d7f` fix(deps): update dependency io.micronaut.test:micronaut-test-bom to v4.3.0 (#350) (renovate[bot], 2024-04-11)
- `c0f2e29e2f7c` fix(deps): update dependency io.micronaut.rxjava2:micronaut-rxjava2-bom to v2.3.0 (renovate[bot], 2024-04-04)
- `fd4cb01b05ed` fix(deps): update dependency io.micronaut.reactor:micronaut-reactor-bom to v3.3.0 (renovate[bot], 2024-04-02)
- `5a73add84f40` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.4.0 (#340) (renovate[bot], 2024-04-02)
- `3bbd43c6ead0` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.3.12 (#338) (renovate[bot], 2024-03-28)
- `02fe1da581d1` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.3.5 (#335) (renovate[bot], 2024-03-27)
- `806f80c88a8e` fix(deps): update dependency org.apache.groovy:groovy-bom to v4.0.20 (#330) (renovate[bot], 2024-03-18)
- `5801258902ea` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.3.11 (#329) (renovate[bot], 2024-03-18)

### Dependency Updates

- `99c4c9386605` Update Micronaut version from RC1 to RC2 (Sergio del Amo, 2026-05-06)
- `be2ca4dc1086` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-05-05)
- `be1d077f6735` Update Micronaut dependencies (#625) (renovate[bot], 2026-05-05)
- `0a61529a8e2b` Update dependency com.google.devtools.ksp:symbol-processing-gradle-plugin to v2.3.7 (#621) (renovate[bot], 2026-05-04)
- `58aeef95d3cb` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-04-17)
- `b917ff8273fd` chore(deps): update gradle to v9.4.1 (#612) (renovate[bot], 2026-04-17)
- `668dfd87cb68` chore(deps): update softprops/action-gh-release action to v2.6.2 (#614) (renovate[bot], 2026-04-17)
- `722c9be26ccb` chore(deps): update gradle/actions action to v6 (#616) (renovate[bot], 2026-04-17)
- `14df5f006931` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#608) (renovate[bot], 2026-02-20)
- `4450e757eccb` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m16 (#607) (renovate[bot], 2026-02-10)
- `1145a0c341fb` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m15 (#605) (renovate[bot], 2026-01-31)
- `39c4657b71b1` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m14 (#599) (renovate[bot], 2026-01-10)
- `a4ab868a02e1` chore(deps): update graalvm/setup-graalvm action to v1.4.5 (#598) (renovate[bot], 2026-01-06)
- `2eea9d8d65c2` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m13 (#594) (renovate[bot], 2025-12-20)
- `69ff62d37296` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2025-12-05)
- `06c6938191b0` del groovy version as it is supplied by MN Build (Sergio del Amo, 2025-12-04)
- `4236ddd2667a` del micronaut-test version as it is supplied by MN Build (Sergio del Amo, 2025-12-04)
- `da20852cdfa1` del micronaut-logging version as it is supplied by MN Build (Sergio del Amo, 2025-12-04)
- `27b0bcc3b538` del micronaut-docs version as it is supplied by MN Build (Sergio del Amo, 2025-12-04)
- `c245632395ae` chore(deps): update github artifact actions (#581) (renovate[bot], 2025-12-04)
- `b2a38d88edc6` chore(deps): update softprops/action-gh-release action to v2.5.0 (#575) (renovate[bot], 2025-12-04)
- `2e1532eb43c7` chore(deps): update actions/checkout action to v6 (#580) (renovate[bot], 2025-12-04)
- `2b8e8f60fd91` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#571) (renovate[bot], 2025-12-04)
- `4a2a9725fcb3` chore(deps): update gradle to v9.2.1 (#577) (renovate[bot], 2025-12-04)
- `d740e6f8f8e6` chore(deps): update mikepenz/action-junit-report action to v6 (#583) (renovate[bot], 2025-12-04)
- `ebb25b2b2fb7` chore(deps): update graalvm/setup-graalvm action to v1.4.4 (#584) (renovate[bot], 2025-12-04)
- `2a9505161fc4` chore(deps): update stefanzweifel/git-auto-commit-action action to v7 (#585) (renovate[bot], 2025-12-04)
- `7f3c6db16ccd` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m8 (#565) (renovate[bot], 2025-11-03)
- `5eff40745838` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#566) (renovate[bot], 2025-11-03)
- `dd45c08abbf8` chore(deps): update gradle to v9.2.0 (#569) (renovate[bot], 2025-11-03)
- `c97117d9fc9f` chore(deps): update plugin io.micronaut.build.shared.settings to v7 (#356) (renovate[bot], 2024-05-30)
- `6ed070e56aef` chore(deps): update graalvm/setup-graalvm action to v1.2.0 (#331) (renovate[bot], 2024-03-19)
- `13503e472d3f` chore(deps): update plugin io.micronaut.build.shared.settings to v6.7.0 (#332) (renovate[bot], 2024-03-19)
- `a0bec04ae7d1` chore(deps): update graalvm/setup-graalvm action to v1.1.9 (#328) (renovate[bot], 2024-03-18)

### Documentation

- `358e51864588` Docs: update micronaut-docs to 3.0.0 (#559) (issam liqali, 2025-10-16)

### Internal

- `bee9bd4fb74a` refactor: use JSpecify nullability annotations in Groovy test (#601) (Hwang Young, 2026-04-17)

### Review Candidates

- `7cfde7808b3c` Update common files (#626) (micronaut-build, 2026-05-06)
- `8170b4fd75d6` [skip ci] Release v5.0.0-RC1 (micronaut-build, 2026-05-05)
- `9a7d631e3e7f` use kotlin-ksp internal gradle plugin (Sergio del Amo, 2026-05-05)
- `e7841e3a1b0f` micronaut-platform = "5.0.0-M3" (Sergio del Amo, 2026-05-05)
- `a0027c009054` Update kotlin monorepo to v2.3.21 (#622) (renovate[bot], 2026-05-05)
- `25926938274d` [validation] Update common files for branch 5.0.x (#624) (micronaut-build, 2026-05-04)
- `5337ed74e361` [validation] Update common files for branch 5.0.x (#623) (micronaut-build, 2026-05-01)
- `08c75eacd26a` Update common files (#619) (micronaut-build, 2026-04-26)
- `ecc60ed7d4d2` [skip ci] Release v5.0.0-M2 (micronaut-build, 2026-04-17)
- `80ee876d257d` use rxjava3 instead of rxjava2 (Sergio del Amo, 2026-04-17)
- `a053cbf32c11` micronaut-gradle-plugin = "5.0.0-M1" (Sergio del Amo, 2026-04-17)
- `6c4e892792d5` micronaut-kotlin = "5.0.0-M1" (Sergio del Amo, 2026-04-17)
- `1da01e699e27` micronaut-reactor = "4.0.0-M2" (Sergio del Amo, 2026-04-17)
- `12cf3ef2fa37` Update common files (#611) (micronaut-build, 2026-04-17)
- `8e4b93d023c0` Update to Micronaut Core M17  (#617) (Issam Liqali, 2026-03-30)
- `dc3141a3db3f` Merge pull request #596 from micronaut-projects/renovate/stefanzweifel-git-auto-commit-action-7.x (renovate[bot], 2026-02-23)
- `e4528b1d90dc` Merge pull request #604 from micronaut-projects/renovate/micronaut (Sergio del Amo, 2026-02-23)
- `19e076ef3b76` Update common files (#590) (micronaut-build, 2026-02-12)
- `dd5bf7b6ff5a` [skip ci] Release v5.0.0-M1 (micronaut-build, 2025-12-05)
- `fe51bd5f9883` Merge pull request #538 from micronaut-projects/renovate/arquillian.container (Sergio del Amo, 2025-12-04)
- `f919b8d5f082` Merge pull request #588 from micronaut-projects/validation-m1 (Sergio del Amo, 2025-12-04)
- `0798f3373bb7` use Kotlin DSL (Sergio del Amo, 2025-12-04)
- `93d49094dfac` use mn nullability annotation instead of JSpecify (Sergio del Amo, 2025-12-04)
- `6e1130bab10c` platform 4.10.3 (Sergio del Amo, 2025-12-04)
- `ca232be98ccf` microaut core 5.0.0-M2 (Sergio del Amo, 2025-12-04)
- `c1a925a09faf` JSpecify nullability annotations (Sergio del Amo, 2025-12-04)
- `a881f2415c42` Update common files (#572) (micronaut-build, 2025-12-04)
- `a941116c9519` Micronaut 5 compatibility (#562) (issam liqali, 2025-11-03)
- `b274914f1747` Update common files (#563) (micronaut-build, 2025-11-03)
- `693b520d9fe5` Update common files (#560) (micronaut-build, 2025-10-16)
- `53793a2e6883` Merge branch '4.12.x' into 5.0.x (Sergio del Amo, 2025-10-13)
- `d56b2fad69b6` Update common files (#357) (micronaut-build, 2024-05-30)
- `53255dd248ff` Update common files (#353) (micronaut-build, 2024-04-19)
- `f361e0c43d15` Merge pull request #342 from micronaut-projects/renovate/micronaut.rxjava2 (Radovan Radic, 2024-04-04)
- `c420c407c6b4` Merge pull request #341 from micronaut-projects/renovate/micronaut.reactor (Radovan Radic, 2024-04-04)
- `3f95ed1dfc97` Ensure validators accessible as beans from usingContext (#337) (Jeremy Grelle, 2024-03-28)
- `8ffe4a6a3bd6` Update common files (#339) (micronaut-build, 2024-03-28)
- `5b9d41b46283` Update common files (#333) (micronaut-build, 2024-03-27)
- `9a2d13168e64` Update common files (#327) (micronaut-build, 2024-03-18)

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
- `M` settings.gradle
- `M` test-suite-groovy/build.gradle
- `D` test-suite-kotlin/build.gradle
- `A` test-suite-kotlin/build.gradle.kts
- `M` test-suite/build.gradle
- `M` validation/build.gradle
- `A` validation/src/test/groovy/io/micronaut/validation/validator/constraints/custom/CustomValidatorDependency.java

### Documentation

- `A` .agents/skills/docs/SKILL.md
- `A` .agents/skills/docs/references/control-panel-patterns.md
- `A` .agents/skills/docs/references/micronaut-docs-providers.md
- `M` .github/workflows/release.yml
- `A` src/main/docs/guide/breaks.adoc
- `M` src/main/docs/guide/toc.yml
- `M` test-suite-groovy/src/test/groovy/io/micronaut/docs/validation/custom/DurationPatternValidator.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/docs/validation/custom/MyValidatorBean.groovy
- `M` test-suite/src/test/java/io/micronaut/docs/validation/CustomerConstraintTest.java
- `M` test-suite/src/test/java/io/micronaut/docs/validation/ListingArguments.java
- `M` test-suite/src/test/java/io/micronaut/docs/validation/custom/DurationPatternValidator.java
- `M` test-suite/src/test/java/io/micronaut/docs/validation/custom/MyValidatorBean.java
- `M` test-suite/src/test/java/io/micronaut/docs/validation/customann/Email.java
- `M` test-suite/src/test/java/io/micronaut/docs/validation/customann/EmailSender.java
- `M` test-suite/src/test/java/io/micronaut/docs/validation/customann/EmailSenderImpl.java
- `M` test-suite/src/test/java/io/micronaut/docs/validation/customann/Recipients.java
- `M` test-suite/src/test/java/io/micronaut/docs/validation/customann/RecipientsUtils.java
- `M` test-suite/src/test/java/io/micronaut/docs/validation/path/validations/validator/DagTaskValidator.java
- `M` test-suite/src/test/java/io/micronaut/docs/validation/path/validations/validator/DateTimeValidator.java
- `M` test-suite/src/test/java/io/micronaut/docs/validation/path/validations/validator/FlowValidator.java
- `M` test-suite/src/test/java/io/micronaut/docs/validation/path/validations/validator/PatternValidator.java
- `M` test-suite/src/test/java/io/micronaut/docs/validation/path/validations/validator/WorkerGroupValidator.java

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
- `M` validation-processor/src/main/java/io/micronaut/validation/visitor/ValidationVisitor.java
- `M` validation/src/main/java/io/micronaut/validation/ValidatingInterceptor.java
- `M` validation/src/main/java/io/micronaut/validation/validator/BeanValidationContext.java
- `M` validation/src/main/java/io/micronaut/validation/validator/DefaultAnnotatedElementValidator.java
- `M` validation/src/main/java/io/micronaut/validation/validator/DefaultBeanValidationContext.java
- `M` validation/src/main/java/io/micronaut/validation/validator/DefaultConstraintDescriptor.java
- `M` validation/src/main/java/io/micronaut/validation/validator/DefaultConstraintValidatorContext.java
- `M` validation/src/main/java/io/micronaut/validation/validator/DefaultConstraintViolation.java
- `M` validation/src/main/java/io/micronaut/validation/validator/DefaultConstraintViolationBuilder.java
- `M` validation/src/main/java/io/micronaut/validation/validator/DefaultValidator.java
- `M` validation/src/main/java/io/micronaut/validation/validator/DefaultValidatorConfiguration.java
- `M` validation/src/main/java/io/micronaut/validation/validator/ExecutableMethodValidator.java
- `M` validation/src/main/java/io/micronaut/validation/validator/ReactiveValidator.java
- `M` validation/src/main/java/io/micronaut/validation/validator/ValidationPath.java
- `M` validation/src/main/java/io/micronaut/validation/validator/Validator.java
- `M` validation/src/main/java/io/micronaut/validation/validator/ValidatorConfiguration.java
- `M` validation/src/main/java/io/micronaut/validation/validator/constraints/AbstractPatternValidator.java
- `M` validation/src/main/java/io/micronaut/validation/validator/constraints/ConstraintValidator.java
- `M` validation/src/main/java/io/micronaut/validation/validator/constraints/ConstraintValidatorContext.java
- `M` validation/src/main/java/io/micronaut/validation/validator/constraints/ConstraintValidatorRegistry.java
- `M` validation/src/main/java/io/micronaut/validation/validator/constraints/DecimalMaxValidator.java
- `M` validation/src/main/java/io/micronaut/validation/validator/constraints/DecimalMinValidator.java
- `M` validation/src/main/java/io/micronaut/validation/validator/constraints/DefaultConstraintValidators.java
- `M` validation/src/main/java/io/micronaut/validation/validator/constraints/DefaultInternalConstraintValidatorFactory.java
- `M` validation/src/main/java/io/micronaut/validation/validator/constraints/DigitsValidator.java
- `M` validation/src/main/java/io/micronaut/validation/validator/constraints/EmailValidator.java
- `M` validation/src/main/java/io/micronaut/validation/validator/constraints/InEnumValidator.java
- `M` validation/src/main/java/io/micronaut/validation/validator/constraints/InListValidator.java
- `M` validation/src/main/java/io/micronaut/validation/validator/constraints/InternalConstraintValidatorFactory.java
- `M` validation/src/main/java/io/micronaut/validation/validator/constraints/InternalConstraintValidators.java
- `M` validation/src/main/java/io/micronaut/validation/validator/constraints/NotInEnumValidator.java
- `M` validation/src/main/java/io/micronaut/validation/validator/constraints/NotInListValidator.java
- `M` validation/src/main/java/io/micronaut/validation/validator/constraints/PatternValidator.java
- `M` validation/src/main/java/io/micronaut/validation/validator/constraints/SizeValidator.java
- `M` validation/src/main/java/io/micronaut/validation/validator/constraints/UniqueElementsValidator.java
- `M` validation/src/main/java/io/micronaut/validation/validator/extractors/DefaultValueExtractors.java
- `M` validation/src/main/java/io/micronaut/validation/validator/extractors/ValueExtractorDefinition.java
- `M` validation/src/main/java/io/micronaut/validation/validator/extractors/ValueExtractorRegistry.java
- `M` validation/src/main/java/io/micronaut/validation/validator/messages/DefaultMessageInterpolator.java
- `M` validation/src/main/java/io/micronaut/validation/validator/messages/DefaultMessageInterpolatorContext.java
- `M` validation/src/main/java/io/micronaut/validation/validator/messages/InterpolatorLocaleResolver.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` validation-processor/src/main/java/io/micronaut/validation/visitor/IntrospectedValidationIndexesVisitor.java
- `M` validation/src/test/groovy/io/micronaut/validation/BeanIntrospectionSpec.groovy
- `M` validation/src/test/groovy/io/micronaut/validation/BookmarkController.java
- `M` validation/src/test/groovy/io/micronaut/validation/PaginationCommand.java
- `M` validation/src/test/groovy/io/micronaut/validation/ValidatedSpec.groovy
- `M` validation/src/test/groovy/io/micronaut/validation/records/Test2.java
- `M` validation/src/test/groovy/io/micronaut/validation/repo/MyRepoIntroducer.java
- `M` validation/src/test/groovy/io/micronaut/validation/validator/ValidatorSpec.groovy
- `M` validation/src/test/groovy/io/micronaut/validation/validator/ValidatorSpecClasses.java
- `M` validation/src/test/groovy/io/micronaut/validation/validator/constraints/custom/CustomMessageConstraint2Validator.java
- `A` validation/src/test/groovy/io/micronaut/validation/validator/constraints/custom/IntrospectedSingletonValidator.java
- `A` validation/src/test/groovy/io/micronaut/validation/validator/constraints/custom/MisconfiguredConstraint.java
- `M` validation/src/test/groovy/io/micronaut/validation/validator/constraints/disable/NotNullMessageFromAnnotationValidator.java
- `M` validation/src/test/groovy/io/micronaut/validation/validator/constraints/disable/NotNullMessageFromValidatorValidator.java
- `M` validation/src/test/groovy/io/micronaut/validation/validator/customwithdefaultconstraints/EmployeeValidationsSpec.groovy
- `M` validation/src/test/groovy/io/micronaut/validation/validator/pojo/PojoBodyParameterSpec.groovy
- `M` validation/src/test/groovy/io/micronaut/validation/validator/reactive/BookServiceRxJava2.java
- `M` validation/src/test/groovy/io/micronaut/validation/validator/reactive/RxJava2MethodValidationSpec.groovy
- `M` validation/src/test/java/io/micronaut/validation/validator/messages/DefaultMessageInterpolatorTest.java

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

