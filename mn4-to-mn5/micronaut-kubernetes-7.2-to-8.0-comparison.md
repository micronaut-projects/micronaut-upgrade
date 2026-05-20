Compared micronaut-kubernetes as mn4 -> mn5.

  Scope

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-kubernetes, branch 7.2.x, SHA 033495a3de30
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-kubernetes, branch 8.0.x, SHA 12c3647fbba1
  - Same remote, both clean: git@github.com:micronaut-projects/micronaut-kubernetes.git
  - Report: /private/tmp/micronaut-kubernetes-7.2-to-8.0-comparison.md

  Key Findings

  - Major line move: 7.2.2-SNAPSHOT -> 8.0.1-SNAPSHOT.
  - Platform/build upgrade: Micronaut 4.10.12 -> 5.0.0, Platform 4.8.3 -> 5.0.0-RC1, Gradle 8.14.3 -> 9.5.0,
    Java/GraalVM 25.
  - Official Kubernetes Java client upgraded 22.0.1 -> 26.0.0; OpenAPI generation updated for Kubernetes v26.
  - micronaut-kubernetes-client-rxjava2 was removed; RxJava3 remains.
  - Kubernetes Configuration Client is deprecated in favor of micronaut.config.import for ConfigMaps/Secrets,
    implemented for both official and OpenAPI clients.
  - OpenAPI delete methods now return DeleteResponse<T> with StatusDeleteResponse / ResourceDeleteResponse.
  - OpenAPI client gained Kubernetes int-or-string support via IntOrString and custom serde.
  - Fabric8 dependency was removed; OpenAPI HTTP client factory avoids real MediaTypeCodec usage.
  - KubernetesUtils.configMapAsPropertySource now requires Collection<PropertySourceLoader>.
  - Expanded examples/tests, including config-import examples and a new test-utils-openapi module.

  Diff size: 387 files changed, 16258 insertions(+), 4136 deletions(-).

  I did not run tests; this was a folder comparison and targeted source/build-diff review only.

# Release Note Comparison

Generated: 2026-05-19 14:10 UTC
Comparison: `7.2.x` -> `8.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-kubernetes` | `7.2.x` | `033495a3de30` | `git@github.com:micronaut-projects/micronaut-kubernetes.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-kubernetes` | `8.0.x` | `12c3647fbba1` | `git@github.com:micronaut-projects/micronaut-kubernetes.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-kubernetes`
- Commit candidates found: 152
- File changes listed: 387
- Version values listed: 35
- File status counts: A=133, D=14, M=237, R=3

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `7.2.2-SNAPSHOT` | `8.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.awaitility` | `not present` | `org.awaitility:awaitility (version.ref=awaitility)` | `added` |
| `gradle/libs.versions.toml` | `libraries.bucket4j` | `com.bucket4j:bucket4j-core (version.ref=bucket4j)` | `com.bucket4j:bucket4j-core (version.ref=bucket4j)` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.graal-svm` | `org.graalvm.nativeimage:svm:24.2.1` | `org.graalvm.nativeimage:svm:25.0.3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.io-fabric8-kubernetes-client` | `io.fabric8:kubernetes-client (version.ref=io-fabric8-kubernetes-client)` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.io-kubernetes-client-java` | `io.kubernetes:client-java (version.ref=io-kubernetes-client-java)` | `io.kubernetes:client-java (version.ref=io-kubernetes-client-java)` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.io-kubernetes-client-java-extended` | `io.kubernetes:client-java-extended (version.ref=io-kubernetes-client-java)` | `io.kubernetes:client-java-extended (version.ref=io-kubernetes-client-java)` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.javapoet` | `com.squareup:javapoet (version.ref=javapoet)` | `com.squareup:javapoet (version.ref=javapoet)` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.micronaut-discovery-client` | `io.micronaut.discovery:micronaut-discovery-client:4.6.0` | `io.micronaut.discovery:micronaut-discovery-client:5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-gradle-plugin` | `io.micronaut.gradle:micronaut-gradle-plugin:4.5.4` | `io.micronaut.gradle:micronaut-gradle-plugin:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-micrometer` | `io.micronaut.micrometer:micronaut-micrometer-bom:5.13.0` | `io.micronaut.micrometer:micronaut-micrometer-bom:6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-reactor` | `micronaut-reactor:3.9.0` | `micronaut-reactor:4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.netty-incubator-codec-http3` | `io.netty.incubator:netty-incubator-codec-http3 (version.ref=netty-incubator-codec-http3)` | `io.netty.incubator:netty-incubator-codec-http3 (version.ref=netty-incubator-codec-http3)` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.rxjava2` | `io.reactivex.rxjava2:rxjava (version.ref=rxjava2)` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.rxjava3` | `io.reactivex.rxjava3:rxjava (version.ref=rxjava3)` | `io.reactivex.rxjava3:rxjava (version.ref=rxjava3)` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.shadow-plugin` | `gradle.plugin.com.github.johnrengelman:shadow (version.ref=shadow)` | `com.gradleup.shadow:shadow-gradle-plugin (version.ref=shadow)` | `changed` |
| `gradle/libs.versions.toml` | `libraries.sonatype-scan` | `org.sonatype.gradle.plugins:scan-gradle-plugin:3.1.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.system-lambda` | `com.github.stefanbirkner:system-lambda (version.ref=system-lambda)` | `com.github.stefanbirkner:system-lambda (version.ref=system-lambda)` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.testcontainers-k3s` | `org.testcontainers:k3s (version.ref=testcontainers-k3s)` | `org.testcontainers:k3s (version.ref=testcontainers-k3s)` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.graal-svm` | `24.2.1` | `25.0.3` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.12` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-discovery` | `4.6.0` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `2.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.5.4` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-micrometer` | `5.13.0` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-openapi` | `6.19.0` | `7.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-platform` | `4.8.3` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-reactor` | `3.9.0` | `4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.15.5` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.9.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.11.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.sonatype-scan` | `3.1.1` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.0` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `b89e89a4634a` Removed kubernetes-client-rxjava2 module since rxjava2 is not supported in micronaut 5 (#1063) (Milenko Supic, 2026-04-28)
- `f4e5b8b0699b` Remove usages of MediaTypeCodec (#1051) (Denis Stepanov, 2026-04-28)
- `6f2484a55991` Removed io.fabric8:kubernetes-client dependency (#947) (Milenko Supic, 2025-10-30)
- `4b69237ee06a` Build: remove sonatype plugin (#940) (issam liqali, 2025-10-14)

### Fixes

- `28ab5d87be51` fix(deps): update micronaut dependencies (#1069) (renovate[bot], 2026-05-04)
- `c607610b0b81` fix(deps): update micronaut dependencies (#1066) (renovate[bot], 2026-05-01)
- `967dfc4c78ab` fix(deps): update dependency org.graalvm.nativeimage:svm to v25.0.3 (#1062) (renovate[bot], 2026-04-28)
- `ce747a3ef4a4` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m23 (#1060) (renovate[bot], 2026-04-21)
- `295c0ea7620f` fix(deps): update dependency io.micronaut.reactor:micronaut-reactor-bom to v4.0.0-m2 (#1059) (renovate[bot], 2026-04-20)
- `6c138e32540f` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m22 (#1057) (renovate[bot], 2026-04-16)
- `06b8e8cf8bfa` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m20 (#1056) (renovate[bot], 2026-04-09)
- `ec724094a45d` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m5 (#1049) (renovate[bot], 2026-04-02)
- `47ec75c3b521` fix(deps): update dependency io.micronaut.platform:micronaut-platform to v4.10.11 (#1053) (renovate[bot], 2026-04-02)
- `f1d52259e9f8` fix(deps): update dependency com.gradleup.shadow:shadow-gradle-plugin to v9.4.1 (#1048) (renovate[bot], 2026-04-02)
- `7fcb641bc92d` fix(deps): update dependency org.apache.groovy:groovy to v5.0.5 (#1050) (renovate[bot], 2026-04-01)
- `cffc01c6a178` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m19 (#1052) (renovate[bot], 2026-04-01)
- `e2ad667fcef1` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m18 (#1047) (renovate[bot], 2026-03-26)
- `efb88024fdc9` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m3 (#1045) (renovate[bot], 2026-03-25)
- `fed3031239cc` fix(deps): update dependency com.gradleup.shadow:shadow-gradle-plugin to v9.4.0 (#1040) (renovate[bot], 2026-03-20)
- `aa26b0b857f9` fix(deps): update dependency io.micronaut.platform:micronaut-platform to v4.10.10 (#1037) (renovate[bot], 2026-03-17)
- `39af0d4e3af1` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m17 (#1036) (renovate[bot], 2026-03-16)
- `c4e60617988f` fix(deps): update dependency io.micronaut.test:micronaut-test-bom to v5.0.0-m7 (#1035) (renovate[bot], 2026-03-14)
- `aa8691ccb3ea` fix(deps): update dependency io.micronaut.openapi:micronaut-openapi-bom to v6.20.0 (#1032) (renovate[bot], 2026-03-11)
- `05c1db2d6a29` fix(deps): update dependency org.yaml:snakeyaml to v2.6 (#1033) (renovate[bot], 2026-03-09)
- `a6aaf2d4ff98` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m16 (#1031) (renovate[bot], 2026-03-07)
- `33d5fe4729e6` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m15 (#1027) (renovate[bot], 2026-03-03)
- `2c15fda8ecf2` fix(deps): update dependency io.micronaut.platform:micronaut-platform to v4.10.9 (#1026) (renovate[bot], 2026-03-02)
- `356608f9cece` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m14 (#1025) (renovate[bot], 2026-03-01)
- `d31906156287` fix(deps): update dependency com.gradleup.shadow:shadow-gradle-plugin to v9.3.2 (#1024) (renovate[bot], 2026-02-28)
- `307732ae7cb4` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m13 (#1023) (renovate[bot], 2026-02-21)
- `db95596a0e81` fix(deps): update dependency io.micronaut.platform:micronaut-platform to v4.10.8 (#1021) (renovate[bot], 2026-02-12)
- `66cab78d75ef` fix(deps): update dependency io.micronaut.test:micronaut-test-bom to v5.0.0-m6 (#1020) (renovate[bot], 2026-02-11)
- `420741d7ea79` fix(deps): update dependency io.micronaut.test:micronaut-test-bom to v5.0.0-m4 (#1017) (renovate[bot], 2026-02-08)
- `ddec50e1eef0` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m10 (#1016) (renovate[bot], 2026-02-07)
- `d78b63a7c2ef` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.2 (#1014) (renovate[bot], 2026-02-04)
- `7aed38f84057` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m9 (#1009) (renovate[bot], 2026-01-27)
- `9cc18479f7e0` fix(deps): update dependency org.apache.groovy:groovy to v5.0.4 (#1007) (renovate[bot], 2026-01-23)
- `3c7aec1fbff9` fix(deps): update dependency org.graalvm.nativeimage:svm to v25.0.2 (#1005) (renovate[bot], 2026-01-21)
- `51b480465601` fix(deps): update spock monorepo to v2.4-groovy-5.0 (#992) (renovate[bot], 2026-01-19)
- `40eb161dacc0` fix(deps): update io.kubernetes.client.java to v25 (major) (#998) (renovate[bot], 2026-01-19)
- `dab60c6abfd1` fix(deps): update dependency org.graalvm.nativeimage:svm to v25 (#997) (renovate[bot], 2026-01-14)
- `ddf64be20e77` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m2 (#982) (renovate[bot], 2026-01-14)
- `3684aa6ce049` fix(deps): update dependency org.graalvm.nativeimage:svm to v24.2.2 (#968) (renovate[bot], 2026-01-13)
- `d9411459ba3d` fix(deps): update dependency com.gradleup.shadow:shadow-gradle-plugin to v9.3.1 (#979) (renovate[bot], 2026-01-13)
- `c4a452b7d073` fix(deps): update dependency io.reactivex.rxjava3:rxjava to v3.1.12 (#966) (renovate[bot], 2026-01-13)
- `a5cbfee6d381` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.12.0 (#986) (renovate[bot], 2026-01-13)
- `7c8eac36e68f` fix(deps): update dependency io.micronaut.discovery:micronaut-discovery-client to v4.7.1 (#980) (renovate[bot], 2026-01-13)
- `fccae36ae4e0` fix(deps): update dependency org.testcontainers:k3s to v1.21.4 (#983) (renovate[bot], 2026-01-13)
- `2fbb863d9334` fix(deps): update dependency io.micronaut.micrometer:micronaut-micrometer-bom to v5.13.2 (#978) (renovate[bot], 2026-01-13)
- `c91d863a4cdb` fix(deps): update dependency io.micronaut.platform:micronaut-platform to v4.10.7 (#976) (renovate[bot], 2026-01-13)
- `f7114902f08d` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#967) (renovate[bot], 2025-11-25)
- `b745c28f1319` fix(deps): update dependency io.micronaut.platform:micronaut-platform to v4.10.2 (#965) (renovate[bot], 2025-11-23)
- `ae22e5020d10` fix(deps): update dependency io.micronaut.platform:micronaut-platform to v4.10.1 (#961) (renovate[bot], 2025-11-13)
- `74749ada3b90` fix(deps): update dependency io.micronaut.reactor:micronaut-reactor-bom to v3.9.1 (#958) (renovate[bot], 2025-11-12)
- `fc1e20cd71de` fix(deps): update dependency io.micronaut.openapi:micronaut-openapi-bom to v6.19.3 (#956) (renovate[bot], 2025-11-10)
- `85136750cec2` fix(deps): update dependency io.micronaut.micrometer:micronaut-micrometer-bom to v5.13.1 (#954) (renovate[bot], 2025-11-07)
- `f13ae32a2619` fix(deps): update dependency io.micronaut.micrometer:micronaut-micrometer-bom to v5.13.0 (#907) (renovate[bot], 2025-10-10)
- `f34223b4e7ed` fix(deps): update dependency io.micronaut.reactor:micronaut-reactor-bom to v3.8.0 (#922) (renovate[bot], 2025-10-09)
- `a1c507e7c033` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.11.0 (#925) (renovate[bot], 2025-10-09)
- `f23321fc0fa7` fix(deps): update dependency org.graalvm.nativeimage:svm to v24.2.2 (#916) (renovate[bot], 2025-10-09)
- `9394721599db` fix(deps): update dependency io.reactivex.rxjava3:rxjava to v3.1.12 (#913) (renovate[bot], 2025-10-09)
- `64f105fba98c` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.15.4 (#918) (renovate[bot], 2025-10-08)
- `d30caab3ac85` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.5.5 (#935) (renovate[bot], 2025-10-08)
- `49e97602a38a` fix(deps): update io.kubernetes.client.java to v24 (major) (#870) (renovate[bot], 2025-10-08)

### Dependency Updates

- `9abb77aa1477` chore: Bump version to 8.0.1-SNAPSHOT (micronaut-build, 2026-05-18)
- `ffb8a91c759b` chore: Bump version to 8.0.0-SNAPSHOT (micronaut-build, 2026-05-10)
- `aacd5d82edff` Update Micronaut dependencies (#1071) (renovate[bot], 2026-05-09)
- `292cffd6a8b2` chore(deps): update mikepenz/action-junit-report action to v6.4.0 (#1073) (renovate[bot], 2026-05-08)
- `99727f7b9b19` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m18 (#1061) (renovate[bot], 2026-04-24)
- `c942c381afae` chore(deps): update softprops/action-gh-release action to v2.6.2 (#1058) (renovate[bot], 2026-04-17)
- `15f3a692239b` chore(deps): update actions/upload-artifact action to v7 (#1043) (renovate[bot], 2026-03-23)
- `2abbee2e2aec` chore(deps): update gradle to v9.4.1 (#1041) (renovate[bot], 2026-03-20)
- `d41988d304bd` chore(deps): update gradle to v9.4.0 (#1030) (renovate[bot], 2026-03-11)
- `4563037becb8` chore(deps): update mikepenz/action-junit-report action to v6.3.1 (#1029) (renovate[bot], 2026-03-11)
- `6e03b2669186` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#1022) (renovate[bot], 2026-02-20)
- `e365322a2d7a` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m16 (#1019) (renovate[bot], 2026-02-10)
- `592ed7909134` chore(deps): update mikepenz/action-junit-report action to v6.2.0 (#1013) (renovate[bot], 2026-02-02)
- `1744584c6e10` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m15 (#1011) (renovate[bot], 2026-01-31)
- `835668ef2ac6` chore: Bump version to 8.0.0-SNAPSHOT (micronaut-build, 2026-01-21)
- `461d27bf20bd` Upgrade micronaut dependencies to micronaut 5 pre-releases (#1003) (Milenko Supic, 2026-01-21)
- `9450b7b4b424` chore(deps): update gradle to v9.3.0 (#1002) (renovate[bot], 2026-01-19)
- `102149cc1345` chore(deps): update mikepenz/action-junit-report action to v6 (#996) (renovate[bot], 2026-01-14)
- `251eb7416cee` chore(deps): update actions/upload-artifact action to v6 (#995) (renovate[bot], 2026-01-14)
- `7d60b9559807` chore(deps): update actions/cache action to v5 (#993) (renovate[bot], 2026-01-13)
- `1631aeb37130` chore(deps): update actions/checkout action to v6 (#994) (renovate[bot], 2026-01-13)
- `dbf99affcafe` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m14 (#974) (renovate[bot], 2026-01-13)
- `c4616c3d4e4f` chore(deps): update graalvm/setup-graalvm action to v1.4.5 (#975) (renovate[bot], 2026-01-12)
- `d1766bae7c24` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m11 (#971) (renovate[bot], 2025-11-28)
- `60dc2a3173ae` chore(deps): update graalvm/setup-graalvm action to v1.4.3 (#970) (renovate[bot], 2025-11-27)
- `d3d0fda08508` chore(deps): update gradle to v9.2.1 (#963) (renovate[bot], 2025-11-20)
- `44fb98ee645c` chore(deps): update softprops/action-gh-release action to v2.4.2 (#957) (renovate[bot], 2025-11-12)
- `b169744bd5b8` chore(deps): update softprops/action-gh-release action to v2.4.2 (#955) (renovate[bot], 2025-11-09)
- `b78d5204f675` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m9 (#951) (renovate[bot], 2025-11-05)
- `774f22a0a9fc` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m8 (#948) (renovate[bot], 2025-11-01)
- `c475218419d9` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#946) (renovate[bot], 2025-10-27)
- `86b790356a98` chore(deps): update softprops/action-gh-release action to v2.4.1 (#939) (renovate[bot], 2025-10-14)
- `99affb9dad9a` chore(deps): update actions/setup-java action to v5 (#929) (renovate[bot], 2025-10-10)
- `8726ba5f5418` chore(deps): update actions/checkout action to v5 (#926) (renovate[bot], 2025-10-10)

### Documentation

- `2802b017ca0d` Docs: update micronaut-docs to 3.0.0 (#941) (issam liqali, 2025-10-14)

### Review Candidates

- `12c3647fbba1` micronaut-openapi = "7.0.0" (Sergio del Amo, 2026-05-19)
- `15834bb27c31` update versions (Sergio del Amo, 2026-05-18)
- `b3bc2079e98d` [skip ci] Release v8.0.0 (micronaut-build, 2026-05-18)
- `448421706fc1` update versions (Sergio del Amo, 2026-05-14)
- `02614debcbe7` micronaut-platform = "5.0.0-RC1" (Sergio del Amo, 2026-05-13)
- `d6491986b65a` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `3d69d0e4670c` [skip ci] Release v8.0.0-RC1 (micronaut-build, 2026-05-10)
- `685ef18503b5` Fix tests (#1076) (Sergio del Amo, 2026-05-10)
- `83a1b6e6c844` upate versions (Sergio del Amo, 2026-05-09)
- `1f2d2d938698` Update common files (#1075) (micronaut-build, 2026-05-09)
- `dc8e4050da1a` Update common files (#1074) (micronaut-build, 2026-05-08)
- `6789554a7f62` Update common files (#1070) (micronaut-build, 2026-05-05)
- `d49df46fe040` Upgraded official kubernetes client to 26.0.0 (#1068) (Milenko Supic, 2026-05-04)
- `e88ba14f9951` Update common files (#1067) (micronaut-build, 2026-05-04)
- `6a4c0d9ffe20` Update common files (#1065) (micronaut-build, 2026-05-01)
- `22aba207600f` Config import support in Kubernetes (#1054) (Graeme Rocher, 2026-05-01)
- `60048ad32a56` Update common files (#1064) (micronaut-build, 2026-04-29)
- `e727e2f437f4` Update common files (#1055) (micronaut-build, 2026-04-26)
- `2d80c6cf30b8` Update common files (#1046) (micronaut-build, 2026-03-27)
- `83741984d1ab` Update common files (#1038) (micronaut-build, 2026-03-19)
- `a3b955c8b41b` Update common files (#1028) (micronaut-build, 2026-03-09)
- `84fe8e341487` Update common files (#1015) (micronaut-build, 2026-02-06)
- `7eec6b14706b` Update common files (#1012) (micronaut-build, 2026-02-02)
- `493af98eae27` Update common files (#1010) (micronaut-build, 2026-01-30)
- `18b9d8345203` Update common files (#1008) (micronaut-build, 2026-01-23)
- `106f31d3e93b` [skip ci] Release v8.0.0-M1 (micronaut-build, 2026-01-21)
- `4b7fda1cc74f` Update common files (#1004) (micronaut-build, 2026-01-20)
- `1ea229192776` Fixed race condition issue in kubernetes discovery client (#990) (#999) (Milenko Supic, 2026-01-19)
- `57bd8c5f0dc7` Modified example-kubernetes-informer to use existing cache of secrets (#1001) (Milenko Supic, 2026-01-19)
- `5837a939ef58` Update common files (#1000) (micronaut-build, 2026-01-14)
- `905d0d91b875` [kubernetes] Update common files for branch 8.0.x (#969) (micronaut-build, 2026-01-13)
- `7a48b5e270a2` Micronaut 5 related changes (#985) (Milenko Supic, 2026-01-12)
- `82d3023c9e9b` Replace Micronaut nullability annotations with JSpecify nullability annotations (#973) (Copilot, 2025-12-01)
- `93f06359d0e2` Added native tests for openapi kubernetes client modules (#962) (Milenko Supic, 2025-11-17)
- `4616d06157c7` Added support for 'int-or-string' type from kubernetes openapi spec (#960) (Milenko Supic, 2025-11-14)
- `1041e2a57afb` Update common files (#959) (micronaut-build, 2025-11-14)
- `ab6766c59799` Fixed native tests that are run for example modules (#952) (Milenko Supic, 2025-11-12)
- `25f3b5f7f180` Changed log level from ERROR to INFO for expected http gone status code (#950) (Milenko Supic, 2025-11-10)
- `7a091c2d0cbf` Update common files (#953) (micronaut-build, 2025-11-10)
- `b8c3883af891` Micronaut 5 compatibility  (#945) (issam liqali, 2025-11-03)
- `a506abb29cae` Update common files (#944) (micronaut-build, 2025-11-03)
- `20394feffa17` Micronaut 5 related changes (#943) (Milenko Supic, 2025-10-16)
- `75b978b30e43` netty-incubator-codec-http3 = '0.0.30.Final' (Sergio del Amo, 2025-10-16)
- `4c7337c8fc60` io-fabric8-kubernetes-client = '7.4.0' (Sergio del Amo, 2025-10-16)
- `bb8292122b37` k8s client 24.0.0 (Sergio del Amo, 2025-10-16)
- `22f4c6003b3e` Update common files (#942) (micronaut-build, 2025-10-16)
- `67b1ffc92030` gradle 9.1 (Sergio del Amo, 2025-10-15)
- `23476c21d4b3` micronaut gradle build plugin 8.0.0-M4 (Sergio del Amo, 2025-10-15)
- `e0a7f8978b7f` projectVersion=8.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-10-15)
- `615e2440352f` Merge branch '7.2.x' into 8.0.x (Sergio del Amo, 2025-10-15)
- `8c1d869a1a98` Modified response of delete methods in Kubernetes Client OpenAPI blocking and reactive client (#937) (Milenko Supic, 2025-10-10)
- `4b1e369cef9f` Update common files (#936) (micronaut-build, 2025-10-10)
- `0db9be84bc66` Upgraded libs in single PR (#938) (Milenko Supic, 2025-10-10)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/actions/gradle-post-build/action.yml
- `M` .github/actions/gradle-pre-build/action.yml
- `M` .github/workflows/gradle.yml
- `M` build-logic/build.gradle
- `M` buildSrc/build.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.kubernetes-examples.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.kubernetes-module.gradle
- `A` examples/example-client-openapi/build.gradle
- `M` examples/example-client/build.gradle
- `M` examples/example-kubernetes-client-openapi-informer-java/build.gradle
- `M` examples/example-kubernetes-client-openapi-operator-java/build.gradle
- `M` examples/example-kubernetes-informer/build.gradle
- `M` examples/example-kubernetes-operator/build.gradle
- `A` examples/example-service-config-import/build.gradle
- `A` examples/example-service-openapi-config-import/build.gradle
- `A` examples/example-service-openapi/build.gradle
- `M` examples/example-service/build.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` kubernetes-bom/build.gradle
- `M` kubernetes-client-openapi-common/build.gradle
- `M` kubernetes-client-openapi-discovery/build.gradle
- `M` kubernetes-client-openapi-informer/build.gradle
- `M` kubernetes-client-openapi-operator/build.gradle
- `M` kubernetes-client-openapi-reactor/build.gradle
- `M` kubernetes-client-openapi-watcher/build.gradle
- `M` kubernetes-client-openapi/build.gradle
- `D` kubernetes-client-rxjava2/build.gradle
- `M` kubernetes-client/build.gradle
- `M` settings.gradle
- `A` test-utils-openapi/build.gradle
- `M` test-utils/build.gradle

### Documentation

- `A` .agents/skills/docs/SKILL.md
- `A` .agents/skills/docs/references/control-panel-patterns.md
- `A` .agents/skills/docs/references/micronaut-docs-providers.md
- `A` .agents/skills/guides/SKILL.md
- `A` .agents/skills/guides/references/guide-authoring-conventions.md
- `A` .agents/skills/guides/references/guide-inventory.md
- `A` .agents/skills/guides/references/pdf-export-and-pr.md
- `A` .agents/skills/guides/references/repository-workflow.md
- `A` .clinerules/docs.md
- `A` .github/instructions/docs.instructions.md
- `M` .github/workflows/release.yml
- `M` src/main/docs/guide/breaking.adoc
- `A` src/main/docs/guide/config-import.adoc
- `M` src/main/docs/guide/kubernetes-client-openapi/kubernetes-client-openapi-config-client.adoc
- `M` src/main/docs/guide/kubernetes-client-openapi/kubernetes-client-openapi-informer.adoc
- `M` src/main/docs/guide/kubernetes-client.adoc
- `M` src/main/docs/guide/kubernetes-client/config-client.adoc
- `M` src/main/docs/guide/toc.yml
- `M` src/main/docs/guide/whatsNew.adoc

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
- `A` .clineignore
- `A` .clinerules/coding.md
- `M` .github/actions/graalvm-post-build/action.yml
- `M` .github/actions/graalvm-pre-build/action.yml
- `A` .github/instructions/coding.instructions.md
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
- `M` build-logic/src/main/java/io/micronaut/kubernetes/client/openapi/KubernetesClientOpenApiPlugin.java
- `A` build-logic/src/main/java/io/micronaut/kubernetes/client/openapi/tasks/TaskUtils.java
- `R072` cleanup.sh
- `M` config/checkstyle/checkstyle.xml
- `A` examples/example-client-openapi/src/main/java/micronaut/openapi/client/Application.java
- `A` examples/example-client-openapi/src/main/java/micronaut/openapi/client/ExampleClient.java
- `A` examples/example-client-openapi/src/main/java/micronaut/openapi/client/HelloController.java
- `A` examples/example-client-openapi/src/main/resources/application.yml
- `A` examples/example-client-openapi/src/main/resources/logback.xml
- `M` examples/example-client/src/main/java/micronaut/client/ExampleClient.java
- `M` examples/example-kubernetes-client-openapi-informer-java/src/main/java/micronaut/client/configmap/ConfigMapController.java
- `M` examples/example-kubernetes-client-openapi-informer-java/src/main/java/micronaut/client/configmap/ConfigMapInformer.java
- `A` examples/example-kubernetes-client-openapi-informer-java/src/main/java/micronaut/client/package-info.java
- `M` examples/example-kubernetes-client-openapi-informer-java/src/main/java/micronaut/client/secret/SecretController.java
- `M` examples/example-kubernetes-client-openapi-informer-java/src/main/java/micronaut/client/secret/SecretResourceEventHandler.java
- `M` examples/example-kubernetes-client-openapi-informer-java/src/main/resources/application.yml
- `M` examples/example-kubernetes-client-openapi-operator-java/src/main/java/micronaut/operator/ConfigMapReconciler.java
- `M` examples/example-kubernetes-client-openapi-operator-java/src/main/java/micronaut/operator/SecretOperator.java
- `A` examples/example-kubernetes-client-openapi-operator-java/src/main/java/micronaut/operator/package-info.java
- `M` examples/example-kubernetes-client-openapi-operator-java/src/main/resources/application.yml
- `M` examples/example-kubernetes-informer/src/main/java/micronaut/informer/SecretInformerController.java
- `M` examples/example-kubernetes-informer/src/main/java/micronaut/informer/SecretResourceEventHandler.java
- `M` examples/example-kubernetes-operator/src/main/java/micronaut/operator/ConfigMapReconciler.java
- `A` examples/example-service-config-import/src/main/java/micronaut/service/Application.java
- `A` examples/example-service-config-import/src/main/java/micronaut/service/ConfigImportController.java
- `A` examples/example-service-config-import/src/main/resources/application.yml
- `R050` examples/example-service-config-import/src/main/resources/logback.xml
- `A` examples/example-service-openapi-config-import/src/main/java/micronaut/service/Application.java
- `A` examples/example-service-openapi-config-import/src/main/java/micronaut/service/ConfigImportController.java
- `A` examples/example-service-openapi-config-import/src/main/resources/application.yml
- `A` examples/example-service-openapi-config-import/src/main/resources/logback.xml
- `A` examples/example-service-openapi/src/main/java/micronaut/openapi/service/Application.java
- `A` examples/example-service-openapi/src/main/java/micronaut/openapi/service/HelloController.java
- `A` examples/example-service-openapi/src/main/resources/application.yml
- `A` examples/example-service-openapi/src/main/resources/bootstrap.yml
- `A` examples/example-service-openapi/src/main/resources/logback.xml
- `M` kubernetes-client-openapi-common/src/main/java/io/micronaut/kubernetes/client/openapi/KubernetesHttpClientConfiguration.java
- `M` kubernetes-client-openapi-common/src/main/java/io/micronaut/kubernetes/client/openapi/KubernetesHttpClientFactory.java
- `M` kubernetes-client-openapi-common/src/main/java/io/micronaut/kubernetes/client/openapi/KubernetesHttpClientFilter.java
- `M` kubernetes-client-openapi-common/src/main/java/io/micronaut/kubernetes/client/openapi/config/AbstractKubeConfigLoader.java
- `M` kubernetes-client-openapi-common/src/main/java/io/micronaut/kubernetes/client/openapi/config/KubeConfigLoader.java
- `M` kubernetes-client-openapi-common/src/main/java/io/micronaut/kubernetes/client/openapi/config/model/AuthInfo.java
- `M` kubernetes-client-openapi-common/src/main/java/io/micronaut/kubernetes/client/openapi/config/model/Cluster.java
- `M` kubernetes-client-openapi-common/src/main/java/io/micronaut/kubernetes/client/openapi/config/model/Context.java
- `M` kubernetes-client-openapi-common/src/main/java/io/micronaut/kubernetes/client/openapi/config/model/ExecConfig.java
- `M` kubernetes-client-openapi-common/src/main/java/io/micronaut/kubernetes/client/openapi/config/model/ExecEnvVar.java
- `M` kubernetes-client-openapi-common/src/main/java/io/micronaut/kubernetes/client/openapi/credential/ExecCommandCredentialLoader.java
- `M` kubernetes-client-openapi-common/src/main/java/io/micronaut/kubernetes/client/openapi/credential/ServiceAccountTokenLoader.java
- `M` kubernetes-client-openapi-common/src/main/java/io/micronaut/kubernetes/client/openapi/credential/model/ExecCredential.java
- `M` kubernetes-client-openapi-common/src/main/java/io/micronaut/kubernetes/client/openapi/credential/model/ExecCredentialStatus.java
- `M` kubernetes-client-openapi-common/src/main/java/io/micronaut/kubernetes/client/openapi/resolver/DefaultNamespaceResolver.java
- `A` kubernetes-client-openapi-common/src/main/java/io/micronaut/kubernetes/client/openapi/response/DeleteResponse.java
- `A` kubernetes-client-openapi-common/src/main/java/io/micronaut/kubernetes/client/openapi/response/ResourceDeleteResponse.java
- `A` kubernetes-client-openapi-common/src/main/java/io/micronaut/kubernetes/client/openapi/response/StatusDeleteResponse.java
- `M` kubernetes-client-openapi-common/src/main/java/io/micronaut/kubernetes/client/openapi/ssl/KubernetesPrivateKeyLoader.java
- `A` kubernetes-client-openapi-common/src/main/java/io/micronaut/kubernetes/client/openapi/type/IntOrString.java
- `A` kubernetes-client-openapi-common/src/main/java/io/micronaut/kubernetes/client/openapi/type/IntOrStringSerde.java
- `M` kubernetes-client-openapi-discovery/src/main/java/io/micronaut/kubernetes/client/openapi/KubernetesConfiguration.java
- `M` kubernetes-client-openapi-discovery/src/main/java/io/micronaut/kubernetes/client/openapi/configuration/AbstractKubernetesConfigLabelSupplier.java
- `M` kubernetes-client-openapi-discovery/src/main/java/io/micronaut/kubernetes/client/openapi/configuration/AbstractKubernetesConfigWatcher.java
- `M` kubernetes-client-openapi-discovery/src/main/java/io/micronaut/kubernetes/client/openapi/configuration/AbstractKubernetesConfigWatcherCondition.java
- `M` kubernetes-client-openapi-discovery/src/main/java/io/micronaut/kubernetes/client/openapi/configuration/KubernetesConfigMapLabelSupplier.java
- `M` kubernetes-client-openapi-discovery/src/main/java/io/micronaut/kubernetes/client/openapi/configuration/KubernetesConfigMapWatcher.java
- `M` kubernetes-client-openapi-discovery/src/main/java/io/micronaut/kubernetes/client/openapi/configuration/KubernetesConfigMapWatcherCondition.java
- `M` kubernetes-client-openapi-discovery/src/main/java/io/micronaut/kubernetes/client/openapi/configuration/KubernetesConfigUtils.java
- `M` kubernetes-client-openapi-discovery/src/main/java/io/micronaut/kubernetes/client/openapi/configuration/KubernetesConfigurationClient.java
- `M` kubernetes-client-openapi-discovery/src/main/java/io/micronaut/kubernetes/client/openapi/configuration/KubernetesSecretLabelSupplier.java
- `M` kubernetes-client-openapi-discovery/src/main/java/io/micronaut/kubernetes/client/openapi/configuration/KubernetesSecretWatcher.java
- `M` kubernetes-client-openapi-discovery/src/main/java/io/micronaut/kubernetes/client/openapi/configuration/KubernetesSecretWatcherCondition.java
- `A` kubernetes-client-openapi-discovery/src/main/java/io/micronaut/kubernetes/client/openapi/configuration/imports/AbstractKubernetesConfigWatcher.java
- `A` kubernetes-client-openapi-discovery/src/main/java/io/micronaut/kubernetes/client/openapi/configuration/imports/AbstractKubernetesConfigWatcherCondition.java
- `A` kubernetes-client-openapi-discovery/src/main/java/io/micronaut/kubernetes/client/openapi/configuration/imports/ImportDeclaration.java
- `A` kubernetes-client-openapi-discovery/src/main/java/io/micronaut/kubernetes/client/openapi/configuration/imports/ImportDeclarationWatchIndex.java
- `A` kubernetes-client-openapi-discovery/src/main/java/io/micronaut/kubernetes/client/openapi/configuration/imports/KubernetesConfigMapImportSupport.java
- `A` kubernetes-client-openapi-discovery/src/main/java/io/micronaut/kubernetes/client/openapi/configuration/imports/KubernetesConfigMapWatcher.java
- `A` kubernetes-client-openapi-discovery/src/main/java/io/micronaut/kubernetes/client/openapi/configuration/imports/KubernetesConfigMapWatcherCondition.java
- `A` kubernetes-client-openapi-discovery/src/main/java/io/micronaut/kubernetes/client/openapi/configuration/imports/KubernetesLegacyImportMode.java
- `A` kubernetes-client-openapi-discovery/src/main/java/io/micronaut/kubernetes/client/openapi/configuration/imports/KubernetesObjectImportSupport.java
- `A` kubernetes-client-openapi-discovery/src/main/java/io/micronaut/kubernetes/client/openapi/configuration/imports/KubernetesPropertySourceImporter.java
- `A` kubernetes-client-openapi-discovery/src/main/java/io/micronaut/kubernetes/client/openapi/configuration/imports/KubernetesSecretImportSupport.java
- `A` kubernetes-client-openapi-discovery/src/main/java/io/micronaut/kubernetes/client/openapi/configuration/imports/KubernetesSecretWatcher.java
- `A` kubernetes-client-openapi-discovery/src/main/java/io/micronaut/kubernetes/client/openapi/configuration/imports/KubernetesSecretWatcherCondition.java
- `A` kubernetes-client-openapi-discovery/src/main/java/io/micronaut/kubernetes/client/openapi/configuration/imports/PropertySourceCache.java
- `M` kubernetes-client-openapi-discovery/src/main/java/io/micronaut/kubernetes/client/openapi/discovery/KubernetesServiceInstanceProvider.java
- `A` kubernetes-client-openapi-discovery/src/main/resources/META-INF/services/io.micronaut.context.env.PropertySourceImporter
- `M` kubernetes-client-openapi-informer/src/main/java/io/micronaut/kubernetes/client/openapi/informer/ApiExecMethodProcessor.java
- `M` kubernetes-client-openapi-informer/src/main/java/io/micronaut/kubernetes/client/openapi/informer/ApiReactorExecMethodProcessor.java
- `M` kubernetes-client-openapi-informer/src/main/java/io/micronaut/kubernetes/client/openapi/informer/DefaultSharedIndexInformerFactory.java
- `M` kubernetes-client-openapi-informer/src/main/java/io/micronaut/kubernetes/client/openapi/informer/DeletedFinalStateUnknown.java
- `M` kubernetes-client-openapi-informer/src/main/java/io/micronaut/kubernetes/client/openapi/informer/InformerApiCall.java
- `M` kubernetes-client-openapi-informer/src/main/java/io/micronaut/kubernetes/client/openapi/informer/InformerApiCallFactory.java
- `M` kubernetes-client-openapi-informer/src/main/java/io/micronaut/kubernetes/client/openapi/informer/ProcessorListener.java
- `M` kubernetes-client-openapi-informer/src/main/java/io/micronaut/kubernetes/client/openapi/informer/SharedIndexInformer.java
- `M` kubernetes-client-openapi-informer/src/main/java/io/micronaut/kubernetes/client/openapi/informer/SharedIndexInformerFactory.java
- `M` kubernetes-client-openapi-informer/src/main/java/io/micronaut/kubernetes/client/openapi/informer/SharedInformer.java
- `M` kubernetes-client-openapi-informer/src/main/java/io/micronaut/kubernetes/client/openapi/informer/TransformFunc.java
- `M` kubernetes-client-openapi-informer/src/main/java/io/micronaut/kubernetes/client/openapi/informer/cache/Indexer.java
- `M` kubernetes-client-openapi-informer/src/main/java/io/micronaut/kubernetes/client/openapi/informer/cache/Store.java
- `M` kubernetes-client-openapi-informer/src/main/java/io/micronaut/kubernetes/client/openapi/informer/handler/DefaultInformerLabelSelectorResolver.java
- `M` kubernetes-client-openapi-informer/src/main/java/io/micronaut/kubernetes/client/openapi/informer/handler/DefaultInformerNamespaceResolver.java
- `M` kubernetes-client-openapi-informer/src/main/java/io/micronaut/kubernetes/client/openapi/informer/handler/InformerLabelSelectorResolver.java
- `M` kubernetes-client-openapi-informer/src/main/java/io/micronaut/kubernetes/client/openapi/informer/handler/InformerNamespaceResolver.java
- `M` kubernetes-client-openapi-informer/src/main/java/io/micronaut/kubernetes/client/openapi/informer/handler/ResourceEventHandler.java
- `M` kubernetes-client-openapi-operator/src/main/java/io/micronaut/kubernetes/client/openapi/operator/OperatorResourceLister.java
- `M` kubernetes-client-openapi-operator/src/main/java/io/micronaut/kubernetes/client/openapi/operator/configuration/LeaderElectionConfiguration.java
- `M` kubernetes-client-openapi-operator/src/main/java/io/micronaut/kubernetes/client/openapi/operator/controller/Controller.java
- `M` kubernetes-client-openapi-operator/src/main/java/io/micronaut/kubernetes/client/openapi/operator/controller/ControllerFactory.java
- `M` kubernetes-client-openapi-operator/src/main/java/io/micronaut/kubernetes/client/openapi/operator/controller/ControllerResourceEventHandler.java
- `M` kubernetes-client-openapi-operator/src/main/java/io/micronaut/kubernetes/client/openapi/operator/controller/DefaultControllerFactory.java
- `M` kubernetes-client-openapi-operator/src/main/java/io/micronaut/kubernetes/client/openapi/operator/controller/reconciler/Request.java
- `M` kubernetes-client-openapi-operator/src/main/java/io/micronaut/kubernetes/client/openapi/operator/controller/reconciler/ResourceReconciler.java
- `M` kubernetes-client-openapi-operator/src/main/java/io/micronaut/kubernetes/client/openapi/operator/controller/reconciler/Result.java
- `M` kubernetes-client-openapi-operator/src/main/java/io/micronaut/kubernetes/client/openapi/operator/leaderelection/LeaderElectionRecord.java
- `M` kubernetes-client-openapi-operator/src/main/java/io/micronaut/kubernetes/client/openapi/operator/leaderelection/LockIdentityProvider.java
- `M` kubernetes-client-openapi-operator/src/main/java/io/micronaut/kubernetes/client/openapi/operator/leaderelection/event/LeaderChangedEvent.java
- `M` kubernetes-client-openapi-operator/src/main/java/io/micronaut/kubernetes/client/openapi/operator/leaderelection/event/LeaseAcquiredEvent.java
- `M` kubernetes-client-openapi-operator/src/main/java/io/micronaut/kubernetes/client/openapi/operator/leaderelection/event/LeaseLostEvent.java
- `M` kubernetes-client-openapi-operator/src/main/java/io/micronaut/kubernetes/client/openapi/operator/workqueue/DelayingQueue.java
- `M` kubernetes-client-openapi-operator/src/main/java/io/micronaut/kubernetes/client/openapi/operator/workqueue/RateLimitingQueue.java
- `M` kubernetes-client-openapi-operator/src/main/java/io/micronaut/kubernetes/client/openapi/operator/workqueue/WorkQueue.java
- `M` kubernetes-client-openapi-operator/src/main/java/io/micronaut/kubernetes/client/openapi/operator/workqueue/ratelimiter/RateLimiter.java
- `M` kubernetes-client-openapi-watcher/src/main/java/io/micronaut/kubernetes/client/openapi/watcher/WatchEvent.java
- `M` kubernetes-client-openapi-watcher/src/main/java/io/micronaut/kubernetes/client/openapi/watcher/WatchEventDeserializer.java
- `A` kubernetes-client-openapi-watcher/src/main/java/io/micronaut/kubernetes/client/openapi/watcher/mapper/TypeNameMapper.java
- `A` kubernetes-client-openapi-watcher/src/main/java/io/micronaut/kubernetes/client/openapi/watcher/mapper/TypeNameResolver.java
- `M` kubernetes-client-processor/src/main/java/io/micronaut/kubernetes/client/processor/KubernetesApisProcessor.java
- `D` kubernetes-client-rxjava2/src/main/java/io/micronaut/kubernetes/client/rxjava2/ApiCallbackEmitter.java
- `M` kubernetes-client/src/main/java/io/micronaut/kubernetes/client/ApiClientFactory.java
- `M` kubernetes-client/src/main/java/io/micronaut/kubernetes/client/Apis.java
- `M` kubernetes-client/src/main/java/io/micronaut/kubernetes/client/OkHttpClientLogging.java
- `M` kubernetes-discovery-client/src/main/java/io/micronaut/kubernetes/KubernetesConfiguration.java
- `M` kubernetes-discovery-client/src/main/java/io/micronaut/kubernetes/configuration/AbstractKubernetesConfigLabelSupplier.java
- `M` kubernetes-discovery-client/src/main/java/io/micronaut/kubernetes/configuration/AbstractKubernetesConfigWatcher.java
- `M` kubernetes-discovery-client/src/main/java/io/micronaut/kubernetes/configuration/AbstractKubernetesConfigWatcherCondition.java
- `M` kubernetes-discovery-client/src/main/java/io/micronaut/kubernetes/configuration/KubernetesConfigMapLabelSupplier.java
- `M` kubernetes-discovery-client/src/main/java/io/micronaut/kubernetes/configuration/KubernetesConfigMapWatcher.java
- `M` kubernetes-discovery-client/src/main/java/io/micronaut/kubernetes/configuration/KubernetesConfigMapWatcherCondition.java
- `M` kubernetes-discovery-client/src/main/java/io/micronaut/kubernetes/configuration/KubernetesConfigurationClient.java
- `M` kubernetes-discovery-client/src/main/java/io/micronaut/kubernetes/configuration/KubernetesSecretLabelSupplier.java
- `M` kubernetes-discovery-client/src/main/java/io/micronaut/kubernetes/configuration/KubernetesSecretWatcher.java
- `M` kubernetes-discovery-client/src/main/java/io/micronaut/kubernetes/configuration/KubernetesSecretWatcherCondition.java
- `A` kubernetes-discovery-client/src/main/java/io/micronaut/kubernetes/configuration/imports/AbstractKubernetesConfigWatcher.java
- `A` kubernetes-discovery-client/src/main/java/io/micronaut/kubernetes/configuration/imports/AbstractKubernetesConfigWatcherCondition.java
- `A` kubernetes-discovery-client/src/main/java/io/micronaut/kubernetes/configuration/imports/ImportDeclaration.java
- `A` kubernetes-discovery-client/src/main/java/io/micronaut/kubernetes/configuration/imports/ImportDeclarationWatchIndex.java
- `A` kubernetes-discovery-client/src/main/java/io/micronaut/kubernetes/configuration/imports/KubernetesConfigMapImportSupport.java
- `A` kubernetes-discovery-client/src/main/java/io/micronaut/kubernetes/configuration/imports/KubernetesConfigMapWatcher.java
- `A` kubernetes-discovery-client/src/main/java/io/micronaut/kubernetes/configuration/imports/KubernetesConfigMapWatcherCondition.java
- `A` kubernetes-discovery-client/src/main/java/io/micronaut/kubernetes/configuration/imports/KubernetesLegacyImportMode.java
- `A` kubernetes-discovery-client/src/main/java/io/micronaut/kubernetes/configuration/imports/KubernetesObjectImportSupport.java
- `A` kubernetes-discovery-client/src/main/java/io/micronaut/kubernetes/configuration/imports/KubernetesPropertySourceImporter.java
- `A` kubernetes-discovery-client/src/main/java/io/micronaut/kubernetes/configuration/imports/KubernetesSecretImportSupport.java
- `A` kubernetes-discovery-client/src/main/java/io/micronaut/kubernetes/configuration/imports/KubernetesSecretWatcher.java
- `A` kubernetes-discovery-client/src/main/java/io/micronaut/kubernetes/configuration/imports/KubernetesSecretWatcherCondition.java
- `A` kubernetes-discovery-client/src/main/java/io/micronaut/kubernetes/configuration/imports/PropertySourceCache.java
- `M` kubernetes-discovery-client/src/main/java/io/micronaut/kubernetes/discovery/KubernetesDiscoveryClient.java
- `M` kubernetes-discovery-client/src/main/java/io/micronaut/kubernetes/discovery/informer/IndexerComposite.java
- `M` kubernetes-discovery-client/src/main/java/io/micronaut/kubernetes/util/KubernetesUtils.java
- `A` kubernetes-discovery-client/src/main/resources/META-INF/services/io.micronaut.context.env.PropertySourceImporter
- `M` kubernetes-informer/src/main/java/io/micronaut/kubernetes/client/informer/DefaultSharedIndexInformerFactory.java
- `M` kubernetes-informer/src/main/java/io/micronaut/kubernetes/client/informer/SharedIndexInformerFactory.java
- `M` kubernetes-informer/src/main/java/io/micronaut/kubernetes/client/informer/resolvers/DefaultInformerApiGroupResolver.java
- `M` kubernetes-informer/src/main/java/io/micronaut/kubernetes/client/informer/resolvers/DefaultInformerLabelSelectorResolver.java
- `M` kubernetes-informer/src/main/java/io/micronaut/kubernetes/client/informer/resolvers/DefaultInformerNamespaceResolver.java
- `M` kubernetes-informer/src/main/java/io/micronaut/kubernetes/client/informer/resolvers/DefaultInformerResourcePluralResolver.java
- `M` kubernetes-informer/src/main/java/io/micronaut/kubernetes/client/informer/resolvers/InformerApiGroupResolver.java
- `M` kubernetes-informer/src/main/java/io/micronaut/kubernetes/client/informer/resolvers/InformerLabelSelectorResolver.java
- `M` kubernetes-informer/src/main/java/io/micronaut/kubernetes/client/informer/resolvers/InformerNamespaceResolver.java
- `M` kubernetes-informer/src/main/java/io/micronaut/kubernetes/client/informer/resolvers/InformerResourcePluralResolver.java
- `M` kubernetes-operator/src/main/java/io/micronaut/kubernetes/client/operator/ControllerConfiguration.java
- `M` kubernetes-operator/src/main/java/io/micronaut/kubernetes/client/operator/ControllerConfigurationFactory.java
- `M` kubernetes-operator/src/main/java/io/micronaut/kubernetes/client/operator/ControllerConfigurationImpl.java
- `M` kubernetes-operator/src/main/java/io/micronaut/kubernetes/client/operator/ControllerFactory.java
- `M` kubernetes-operator/src/main/java/io/micronaut/kubernetes/client/operator/OperatorResourceLister.java
- `M` kubernetes-operator/src/main/java/io/micronaut/kubernetes/client/operator/ResourceReconciler.java
- `M` kubernetes-operator/src/main/java/io/micronaut/kubernetes/client/operator/ResourceReconcilerCreatedListener.java
- `M` kubernetes-operator/src/main/java/io/micronaut/kubernetes/client/operator/configuration/LeaderElectionConfiguration.java
- `M` kubernetes-operator/src/main/java/io/micronaut/kubernetes/client/operator/configuration/LeaderElectionConfigurationProperties.java
- `M` kubernetes-operator/src/main/java/io/micronaut/kubernetes/client/operator/controller/ControllerBuilder.java
- `M` kubernetes-operator/src/main/java/io/micronaut/kubernetes/client/operator/controller/ControllerManagerBuilder.java
- `M` kubernetes-operator/src/main/java/io/micronaut/kubernetes/client/operator/controller/ControllerWatchBuilder.java
- `M` kubernetes-operator/src/main/java/io/micronaut/kubernetes/client/operator/controller/DefaultControllerBuilder.java
- `M` kubernetes-operator/src/main/java/io/micronaut/kubernetes/client/operator/controller/DefaultControllerManagerBuilder.java
- `M` kubernetes-operator/src/main/java/io/micronaut/kubernetes/client/operator/controller/DefaultLeaderElectingControllerBuilder.java
- `M` kubernetes-operator/src/main/java/io/micronaut/kubernetes/client/operator/controller/LeaderElectingControllerBuilder.java
- `M` kubernetes-operator/src/main/java/io/micronaut/kubernetes/client/operator/leaderelection/DefaultLockIdentityProvider.java
- `M` kubernetes-operator/src/main/java/io/micronaut/kubernetes/client/operator/leaderelection/LeaderElectionConfigFactory.java
- `A` setup-images.sh
- `M` setup-kubernetes.sh
- `M` setup.sh

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` build-logic/src/main/java/io/micronaut/kubernetes/client/openapi/tasks/CreateWatcherSpec.java
- `A` build-logic/src/main/java/io/micronaut/kubernetes/client/openapi/tasks/ModifySpec.java
- `M` build-logic/src/test/groovy/io/micronaut/kubernetes/client/openapi/KubernetesClientOpenApiPluginSpec.groovy
- `M` build-logic/src/test/resources/openapi-input-2.yaml
- `M` build-logic/src/test/resources/openapi-output-1.yaml
- `A` examples/example-client-openapi/src/test/groovy/micronaut/openapi/client/HelloControllerSpec.groovy
- `A` examples/example-client-openapi/src/test/groovy/micronaut/openapi/client/KubernetesHealthIndicatorSpec.groovy
- `M` examples/example-client/src/test/groovy/micronaut/client/HelloControllerSpec.groovy
- `M` examples/example-client/src/test/groovy/micronaut/client/KubernetesHealthIndicatorSpec.groovy
- `D` examples/example-client/src/test/groovy/micronaut/client/utils/KubernetesSpecification.groovy
- `A` examples/example-kubernetes-client-openapi-informer-java/src/test/groovy/micronaut/test/InformerSpec.groovy
- `A` examples/example-kubernetes-client-openapi-operator-java/src/test/groovy/micronaut/test/OperatorSpec.groovy
- `M` examples/example-kubernetes-informer/src/test/groovy/micronaut/informer/SecretInformerControllerSpec.groovy
- `M` examples/example-kubernetes-operator/src/test/groovy/micronaut/operator/ConfigMapOperatorControllerSpec.groovy
- `D` examples/example-kubernetes-operator/src/test/groovy/micronaut/operator/utils/KubernetesSpecification.groovy
- `A` examples/example-service-config-import/src/test/groovy/micronaut/service/ConfigImportSpec.groovy
- `A` examples/example-service-config-import/src/test/resources/k8s/example-service-config-import-deployment.yml
- `A` examples/example-service-openapi-config-import/src/test/groovy/micronaut/service/OpenApiConfigImportSpec.groovy
- `M` kubernetes-client-openapi-common/src/main/java/io/micronaut/kubernetes/client/openapi/credential/KubernetesTokenLoader.java
- `M` kubernetes-client-openapi-common/src/main/java/io/micronaut/kubernetes/client/openapi/credential/ReactiveKubernetesTokenLoader.java
- `A` kubernetes-client-openapi-common/src/test/groovy/io/micronaut/kubernetes/client/openapi/OffsetDateTimeSerdeSpec.groovy
- `A` kubernetes-client-openapi-common/src/test/groovy/io/micronaut/kubernetes/client/openapi/type/IntOrStringSerdeTest.groovy
- `A` kubernetes-client-openapi-common/src/test/groovy/io/micronaut/kubernetes/client/openapi/type/IntOrStringTest.groovy
- `D` kubernetes-client-openapi-discovery/src/test/groovy/io/micronaut/kubernetes/client/openapi/K3sContainerSpec.groovy
- `M` kubernetes-client-openapi-discovery/src/test/groovy/io/micronaut/kubernetes/client/openapi/configuration/KubernetesConfigurationClientSpec.groovy
- `A` kubernetes-client-openapi-discovery/src/test/groovy/io/micronaut/kubernetes/client/openapi/configuration/imports/ImportDeclarationWatchIndexSpec.groovy
- `A` kubernetes-client-openapi-discovery/src/test/groovy/io/micronaut/kubernetes/client/openapi/configuration/imports/KubernetesConfigImportSpec.groovy
- `A` kubernetes-client-openapi-discovery/src/test/groovy/io/micronaut/kubernetes/client/openapi/configuration/imports/KubernetesPropertySourceImporterSpec.groovy
- `M` kubernetes-client-openapi-discovery/src/test/groovy/io/micronaut/kubernetes/client/openapi/discovery/KubernetesDiscoveryClientSpec.groovy
- `M` kubernetes-client-openapi-discovery/src/test/groovy/io/micronaut/kubernetes/client/openapi/discovery/provider/KubernetesServiceInstanceEndpointProviderSpec.groovy
- `M` kubernetes-client-openapi-discovery/src/test/groovy/io/micronaut/kubernetes/client/openapi/discovery/provider/KubernetesServiceInstanceServiceProviderSpec.groovy
- `D` kubernetes-client-openapi-discovery/src/test/groovy/io/micronaut/kubernetes/client/openapi/utils/ModelUtils.groovy
- `D` kubernetes-client-openapi-discovery/src/test/groovy/io/micronaut/kubernetes/client/openapi/utils/OperationUtils.groovy
- `A` kubernetes-client-openapi-informer/src/test/groovy/io/micronaut/kubernetes/client/openapi/informer/CustomObjectInformer1Spec.groovy
- `A` kubernetes-client-openapi-informer/src/test/groovy/io/micronaut/kubernetes/client/openapi/informer/CustomObjectInformer2Spec.groovy
- `A` kubernetes-client-openapi-informer/src/test/groovy/io/micronaut/kubernetes/client/openapi/informer/CustomTypeMappingSpec.groovy
- `M` kubernetes-client-openapi-informer/src/test/groovy/io/micronaut/kubernetes/client/openapi/informer/DefaultSharedIndexInformerSpec.groovy
- `M` kubernetes-client-openapi-informer/src/test/groovy/io/micronaut/kubernetes/client/openapi/informer/InformerSpec.groovy
- `A` kubernetes-client-openapi-informer/src/test/java/io/micronaut/kubernetes/client/openapi/informer/example1/CustomObject.java
- `A` kubernetes-client-openapi-informer/src/test/java/io/micronaut/kubernetes/client/openapi/informer/example1/CustomObjectApiReactor.java
- `A` kubernetes-client-openapi-informer/src/test/java/io/micronaut/kubernetes/client/openapi/informer/example1/CustomObjectApiWatcher.java
- `A` kubernetes-client-openapi-informer/src/test/java/io/micronaut/kubernetes/client/openapi/informer/example1/CustomObjectList.java
- `A` kubernetes-client-openapi-informer/src/test/java/io/micronaut/kubernetes/client/openapi/informer/example2/CustomObject.java
- `A` kubernetes-client-openapi-informer/src/test/java/io/micronaut/kubernetes/client/openapi/informer/example2/CustomObjectApiReactor.java
- `A` kubernetes-client-openapi-informer/src/test/java/io/micronaut/kubernetes/client/openapi/informer/example2/CustomObjectApiWatcher.java
- `A` kubernetes-client-openapi-informer/src/test/java/io/micronaut/kubernetes/client/openapi/informer/example2/CustomObjectCollection.java
- `A` kubernetes-client-openapi-informer/src/test/java/io/micronaut/kubernetes/client/openapi/informer/example2/CustomTypeNameMapper.java
- `M` kubernetes-client-openapi-operator/src/test/groovy/io/micronaut/kubernetes/client/openapi/operator/OperatorSpec.groovy
- `M` kubernetes-client-openapi-operator/src/test/groovy/io/micronaut/kubernetes/client/openapi/operator/leaderelection/LeaderElectorSpec.groovy
- `M` kubernetes-client-openapi-operator/src/test/groovy/io/micronaut/kubernetes/client/openapi/operator/util/ConfigMapOperation.groovy
- `D` kubernetes-client-openapi-operator/src/test/groovy/io/micronaut/kubernetes/client/openapi/operator/util/NamespaceOperation.groovy
- `M` kubernetes-client-openapi-operator/src/test/groovy/io/micronaut/kubernetes/client/openapi/operator/util/SecretOperation.groovy
- `A` kubernetes-client-openapi-reactor/src/test/groovy/io/micronaut/kubernetes/client/openapi/reactor/DeleteObjectSpec.groovy
- `M` kubernetes-client-openapi-reactor/src/test/groovy/io/micronaut/kubernetes/client/openapi/reactor/KubernetesClientCertAuthSpec.groovy
- `M` kubernetes-client-openapi-watcher/src/test/groovy/io/micronaut/kubernetes/client/openapi/watcher/WatchCustomObjectEventSpec.groovy
- `M` kubernetes-client-openapi-watcher/src/test/groovy/io/micronaut/kubernetes/client/openapi/watcher/WatchEventsSpec.groovy
- `M` kubernetes-client-openapi/src/test/groovy/io/micronaut/kubernetes/client/openapi/ClientConfigLoaderSpec.groovy
- `M` kubernetes-client-openapi/src/test/groovy/io/micronaut/kubernetes/client/openapi/ClientCredentialLoaderSpec.groovy
- `A` kubernetes-client-openapi/src/test/groovy/io/micronaut/kubernetes/client/openapi/DeleteObjectSpec.groovy
- `M` kubernetes-client-openapi/src/test/groovy/io/micronaut/kubernetes/client/openapi/ExecCommandTokenAuthSpec.groovy
- `M` kubernetes-client-openapi/src/test/groovy/io/micronaut/kubernetes/client/openapi/KubeConfigTokenAuthSpec.groovy
- `M` kubernetes-client-openapi/src/test/groovy/io/micronaut/kubernetes/client/openapi/KubernetesBasicAuthSpec.groovy
- `M` kubernetes-client-openapi/src/test/groovy/io/micronaut/kubernetes/client/openapi/KubernetesClientCertAuthSpec.groovy
- `D` kubernetes-client-rxjava2/src/test/groovy/io/micronaut/kubernetes/client/rxjava2/CoreV1ApiRxClientSpec.groovy
- `M` kubernetes-client/src/test/groovy/io/micronaut/kubernetes/client/ApiClientFactorySpec.groovy
- `M` kubernetes-client/src/test/groovy/io/micronaut/kubernetes/client/DiscoveryCacheSpec.groovy
- `D` kubernetes-client/src/test/groovy/io/micronaut/kubernetes/client/utils/KubernetesSpecification.groovy
- `M` kubernetes-discovery-client/src/test/groovy/io/micronaut/kubernetes/KubernetesConfigurationSpec.groovy
- `M` kubernetes-discovery-client/src/test/groovy/io/micronaut/kubernetes/configuration/KubernetesConfigMapWatcherSpec.groovy
- `M` kubernetes-discovery-client/src/test/groovy/io/micronaut/kubernetes/configuration/KubernetesConfigurationClientFilterSpec.groovy
- `M` kubernetes-discovery-client/src/test/groovy/io/micronaut/kubernetes/configuration/KubernetesConfigurationClientLabelsSpec.groovy
- `M` kubernetes-discovery-client/src/test/groovy/io/micronaut/kubernetes/configuration/KubernetesConfigurationClientSecretSpec.groovy
- `M` kubernetes-discovery-client/src/test/groovy/io/micronaut/kubernetes/configuration/KubernetesConfigurationClientSpec.groovy
- `M` kubernetes-discovery-client/src/test/groovy/io/micronaut/kubernetes/configuration/KubernetesSecretWatcherSpec.groovy
- `A` kubernetes-discovery-client/src/test/groovy/io/micronaut/kubernetes/configuration/imports/ImportDeclarationWatchIndexSpec.groovy
- `A` kubernetes-discovery-client/src/test/groovy/io/micronaut/kubernetes/configuration/imports/KubernetesConfigImportSpec.groovy
- `A` kubernetes-discovery-client/src/test/groovy/io/micronaut/kubernetes/configuration/imports/KubernetesLegacyImportModeSpec.groovy
- `A` kubernetes-discovery-client/src/test/groovy/io/micronaut/kubernetes/configuration/imports/KubernetesPropertySourceImporterSpec.groovy
- `M` kubernetes-discovery-client/src/test/groovy/io/micronaut/kubernetes/discovery/KubernetesDiscoveryClientFilterSpec.groovy
- `M` kubernetes-discovery-client/src/test/groovy/io/micronaut/kubernetes/discovery/KubernetesDiscoveryClientLabelsSpec.groovy
- `M` kubernetes-discovery-client/src/test/groovy/io/micronaut/kubernetes/discovery/KubernetesDiscoveryClientSpec.groovy
- `M` kubernetes-discovery-client/src/test/groovy/io/micronaut/kubernetes/discovery/provider/KubernetesServiceInstanceEndpointProviderSpec.groovy
- `M` kubernetes-discovery-client/src/test/groovy/io/micronaut/kubernetes/discovery/provider/KubernetesServiceInstanceServiceProviderSpec.groovy
- `D` kubernetes-discovery-client/src/test/groovy/io/micronaut/kubernetes/utils/KubernetesSpecification.groovy
- `M` kubernetes-informer/src/test/groovy/io/micronaut/kubernetes/client/informer/ApiClientCreationListenerSpec.groovy
- `M` kubernetes-informer/src/test/groovy/io/micronaut/kubernetes/client/informer/ClusterRoleInformerSpec.groovy
- `M` kubernetes-informer/src/test/groovy/io/micronaut/kubernetes/client/informer/ConfigMapInformerSpec.groovy
- `M` kubernetes-informer/src/test/groovy/io/micronaut/kubernetes/client/informer/ConfigMapLabelSelectorInformerSpec.groovy
- `M` kubernetes-informer/src/test/groovy/io/micronaut/kubernetes/client/informer/DefaultSharedIndexInformerFactorySpec.groovy
- `M` kubernetes-informer/src/test/groovy/io/micronaut/kubernetes/client/informer/DuplicitConfigMapInformerSpec.groovy
- `D` kubernetes-informer/src/test/groovy/io/micronaut/kubernetes/client/informer/utils/KubernetesSpecification.groovy
- `M` kubernetes-operator/src/test/groovy/io/micronaut/kubernetes/client/operator/ConfigMapResourceReconcilerSpec.groovy
- `M` kubernetes-operator/src/test/groovy/io/micronaut/kubernetes/client/operator/ConfigMapResourceReconcilerWithFiltersSpec.groovy
- `M` kubernetes-operator/src/test/groovy/io/micronaut/kubernetes/client/operator/controller/DefaultControllerBuilderSpec.groovy
- `M` kubernetes-operator/src/test/groovy/io/micronaut/kubernetes/client/operator/leaderelection/ResourceLockFactorySpec.groovy
- `D` kubernetes-operator/src/test/groovy/io/micronaut/kubernetes/client/operator/utils/KubernetesSpecification.groovy
- `M` kubernetes-operator/src/test/java/io/micronaut/kubernetes/client/operator/ConfigMapResourceReconciler.java
- `M` kubernetes-operator/src/test/java/io/micronaut/kubernetes/client/operator/ConfigMapResourceReconcilerWithFilters.java
- `R066` test-utils-openapi/src/main/groovy/io/micronaut/kubernetes/openapi/test/K3sContainerSpec.groovy
- `A` test-utils-openapi/src/main/groovy/io/micronaut/kubernetes/openapi/test/KubectlPortForward.groovy
- `A` test-utils-openapi/src/main/groovy/io/micronaut/kubernetes/openapi/test/KubernetesModels.groovy
- `A` test-utils-openapi/src/main/groovy/io/micronaut/kubernetes/openapi/test/KubernetesOperations.groovy
- `A` test-utils-openapi/src/main/groovy/io/micronaut/kubernetes/openapi/test/KubernetesSpecification.groovy
- `A` test-utils-openapi/src/main/groovy/io/micronaut/kubernetes/openapi/test/TestUtils.groovy
- `M` test-utils/src/main/groovy/io/micronaut/kubernetes/test/K3sContainerSpec.groovy
- `D` test-utils/src/main/groovy/io/micronaut/kubernetes/test/KubectlCommands.groovy
- `A` test-utils/src/main/groovy/io/micronaut/kubernetes/test/KubectlPortForward.groovy
- `A` test-utils/src/main/groovy/io/micronaut/kubernetes/test/KubernetesModels.groovy
- `M` test-utils/src/main/groovy/io/micronaut/kubernetes/test/KubernetesOperations.groovy
- `M` test-utils/src/main/groovy/io/micronaut/kubernetes/test/KubernetesSpecification.groovy
- `M` test-utils/src/main/groovy/io/micronaut/kubernetes/test/TestUtils.groovy
- `M` test-utils/src/test/groovy/io/micronaut/kubernetes/test/KubernetesOperationsSpec.groovy
- `M` test-utils/src/test/groovy/io/micronaut/kubernetes/test/KubernetesSpecificationSpec.groovy

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

