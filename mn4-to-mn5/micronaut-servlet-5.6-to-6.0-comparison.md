Compared micronaut-servlet as mn4 → mn5.

  Scope

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-servlet, branch 5.6.x, SHA 35f37be
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-servlet, branch 6.0.x, SHA e7df066
  - Report: /private/tmp/micronaut-servlet-5.6-to-6.0-comparison.md

  Key Findings

  - Major baseline move: project 5.6.2-SNAPSHOT → 6.0.1-SNAPSHOT, Micronaut 4.10.6 → 5.0.0, Gradle wrapper
    8.14.3 → 9.5.1, plus .sdkmanrc pinned to java=25.0.1-graal.
  - Servlet runtime dependencies moved forward: Jetty 12.1.2 → 12.1.8, Tomcat 11.0.11 → 11.0.21, Undertow
    2.3.19.Final → 2.3.24.Final, HttpCore5 5.3.6 → 5.4.2, Logback Access 2.0.6 → 2.0.12.
  - Runtime selection was added for servlet engines: micronaut.server.jdk.enabled,
    micronaut.server.jetty.enabled, micronaut.server.tomcat.enabled, micronaut.server.undertow.enabled, and
    poja.apache.enabled.
  - POJA now defaults blocking work to the current request thread via CurrentThreadExecutorService, unless an
    explicit blocking executor is configured.
  - Servlet multipart handling changed: ServletCompletedFileUpload was removed because CompletedFileUpload
    became sealed; servlet support now adapts parts through CompletedFileUpload.ofFile / ofMemory.
  - Servlet internals moved from MediaTypeCodecRegistry toward MessageBodyHandlerRegistry, and nullability
    annotations moved broadly from Micronaut annotations to JSpecify.
  - Fixes include preserving raw query strings in JDK HttpExchange requests, Jetty static-resource CORS
    allowed-origin handling, default servlet mapping with eager singleton init, and WAR lifecycle startup/
    shutdown events via ServletContextEmbeddedServer.
  - CI/release hardening added OSV vulnerability audit scripts/workflow; osv-scanner.toml documents an
    Undertow GHSA-3x3v-w654-m28m ignore because no patched Undertow version is available.

  Diff size: 194 files changed, 7206 insertions(+), 1148 deletions(-).

  I did not run tests; this was a folder comparison only.

# Release Note Comparison

Generated: 2026-05-19 11:21 UTC
Comparison: `5.6.x` -> `6.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-servlet` | `5.6.x` | `35f37be6bc05` | `git@github.com:micronaut-projects/micronaut-servlet.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-servlet` | `6.0.x` | `e7df066126f6` | `git@github.com:micronaut-projects/micronaut-servlet.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-servlet`
- Commit candidates found: 134
- File changes listed: 194
- Version values listed: 29
- File status counts: A=57, D=1, M=136

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `5.6.2-SNAPSHOT` | `6.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.bcpkix` | `org.bouncycastle:bcpkix-jdk15on:1.70` | `org.bouncycastle:bcpkix-jdk15on:1.70` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.gradle-kotlin` | `org.jetbrains.kotlin:kotlin-gradle-plugin:1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.gradle-micronaut` | `io.micronaut.gradle:micronaut-gradle-plugin:4.6.0` | `io.micronaut.gradle:micronaut-gradle-plugin:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.logback-access-jetty12` | `ch.qos.logback.access:logback-access-jetty12:2.0.6` | `ch.qos.logback.access:logback-access-jetty12:2.0.12` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-logging` | `io.micronaut.logging:micronaut-logging-bom:1.7.1` | `io.micronaut.logging:micronaut-logging-bom:2.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-reactor` | `io.micronaut.reactor:micronaut-reactor-bom:3.8.0` | `io.micronaut.reactor:micronaut-reactor-bom:4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-security` | `io.micronaut.security:micronaut-security-bom:4.15.0` | `io.micronaut.security:micronaut-security-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.15.4` | `io.micronaut.serde:micronaut-serde-bom:3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-session` | `io.micronaut.session:micronaut-session-bom:4.7.0` | `io.micronaut.session:micronaut-session-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-validation` | `io.micronaut.validation:micronaut-validation-bom:4.11.0` | `io.micronaut.validation:micronaut-validation-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.bcpkix` | `1.70` | `1.70` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.27` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.kotlin` | `1.9.25` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.logback-access` | `2.0.6` | `2.0.12` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-apache-http-core5` | `5.3.6` | `5.4.2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.6` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.6.0` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.1` | `2.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-reactor` | `3.8.0` | `4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-security` | `4.15.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.15.4` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-session` | `4.7.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.9.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.11.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `27e258274699` remove unused dep google-cloud-functions (Sergio del Amo, 2026-04-17)
- `baf1d2cc2355` remove workaround for bug already fixed in Micronaut core (Sergio del Amo, 2025-12-05)
- `5906c9777b61` remove micronaut-test provided by MN Build (Sergio del Amo, 2025-12-05)
- `105bfaf0631d` remove spock included by MN Build Plugin (Sergio del Amo, 2025-12-05)
- `055fbd2d8d49` remove Groovy included by MN Build Plugin (Sergio del Amo, 2025-12-05)
- `2be06748f578` remove micronaut-docs included by MN Build Plugin (Sergio del Amo, 2025-12-05)

### Features

- `982e94c00e06` Add multipart @Body UTF-8 regression test (#1065) (Graeme Rocher, 2026-04-30)
- `ce832d1f8ebb` Add configurable servlet runtime selection (#1067) (Graeme Rocher, 2026-04-30)

### Fixes

- `1d7d1795618a` fix(deps): update dependency org.apache.httpcomponents.core5:httpcore5 to v5.4.2 (#1033) (renovate[bot], 2026-04-17)
- `2c23a6951065` fix(deps): update dependency io.kotest:kotest-runner-junit5 to v6.1.11 (#1036) (renovate[bot], 2026-04-15)
- `8d84ce79c82e` fix(deps): update dependency org.jetbrains.kotlin:kotlin-gradle-plugin to v2.3.20 (#1039) (renovate[bot], 2026-04-15)
- `de57d176ad82` fix(deps): update jetty monorepo to v12.1.8 (#1034) (renovate[bot], 2026-04-15)
- `98819dbb3fd6` fix(deps): update dependency org.apache.tomcat.embed:tomcat-embed-core to v11.0.21 (#1040) (renovate[bot], 2026-04-15)
- `6a711dc6b3ce` fix(deps): update dependency io.undertow:undertow-servlet to v2.3.24.final (#1042) (renovate[bot], 2026-04-15)
- `a2a85eebc49e` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m6 (#1044) (renovate[bot], 2026-04-15)
- `212665847872` fix: preserve raw query in JDK HttpExchange requests (#1037) (Jonas Konrad, 2026-03-13)
- `d8dc40723c26` fix(deps): update dependency io.kotest:kotest-runner-junit5 to v6.1.4 (#1030) (renovate[bot], 2026-02-28)
- `4abe9c7dde09` fix(deps): update dependency io.micronaut.logging:micronaut-logging-bom to v2.0.0-m2 (#1029) (renovate[bot], 2026-02-22)
- `5c50a99cde9e` fix(deps): update dependency ch.qos.logback.access:logback-access-jetty12 to v2.0.12 (#1027) (renovate[bot], 2026-02-20)
- `2012eb4688de` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.12.0 (#999) (renovate[bot], 2026-02-18)
- `dc1639d6f579` fix(deps): update dependency ch.qos.logback.access:logback-access-jetty12 to v2.0.11 (#1025) (renovate[bot], 2026-02-15)
- `7022f72ea15d` fix(deps): update dependency org.apache.httpcomponents.core5:httpcore5 to v5.4.1 (#1024) (renovate[bot], 2026-02-11)
- `9fc48f6363e4` fix(deps): update dependency io.undertow:undertow-servlet to v2.3.23.final (#1023) (renovate[bot], 2026-02-09)
- `11cee884597e` fix(deps): update dependency org.jetbrains.kotlin:kotlin-gradle-plugin to v2.3.10 (#1021) (renovate[bot], 2026-02-06)
- `44ecef9882f0` fix(deps): update dependency io.kotest:kotest-runner-junit5 to v6.1.3 (#1022) (renovate[bot], 2026-02-05)
- `2958980c7037` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.2 (#1019) (renovate[bot], 2026-02-05)
- `8470eb0db35f` fix(deps): update dependency org.jetbrains.kotlin:kotlin-gradle-plugin to v2.3.0 (#1001) (renovate[bot], 2026-02-04)
- `b172ce0e0ee2` fix(deps): update dependency org.apache.httpcomponents.core5:httpcore5 to v5.4 (#1000) (renovate[bot], 2026-02-03)
- `5a7e02b463df` fix(deps): update dependency com.google.cloud.functions:functions-framework-api to v2 (#1004) (renovate[bot], 2026-02-03)
- `cd4d21dfe0d8` fix(deps): update dependency io.kotest:kotest-runner-junit5 to v6 (#1005) (renovate[bot], 2026-02-03)
- `92151a9e316d` fix(deps): update dependency io.undertow:undertow-servlet to v2.3.22.final (#1013) (renovate[bot], 2026-02-02)
- `1050d497f0bd` fix(deps): update jetty monorepo to v12.1.6 (#1018) (renovate[bot], 2026-02-02)
- `7a5e1e8080ae` fix(deps): update dependency org.apache.tomcat.embed:tomcat-embed-core to v11.0.18 (#1017) (renovate[bot], 2026-01-30)
- `6b13a203288c` fix(deps): update dependency ch.qos.logback.access:logback-access-jetty12 to v2.0.9 (#1016) (renovate[bot], 2026-01-30)
- `f0086fce9930` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m2 (#1011) (renovate[bot], 2026-01-14)
- `ef3bf46141d9` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m8 (#1010) (renovate[bot], 2026-01-13)
- `61cf35abfa2a` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m7 (#1009) (renovate[bot], 2026-01-11)
- `a6797f0c4d7d` fix(deps): update dependency ch.qos.logback.access:logback-access-jetty12 to v2.0.8 (#1008) (renovate[bot], 2026-01-10)
- `37e934eec02a` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m6 (#998) (renovate[bot], 2025-12-24)
- `f246643f984f` fix(deps): update dependency org.apache.tomcat.embed:tomcat-embed-core to v11.0.15 (#996) (renovate[bot], 2025-12-14)
- `dfa4b699280b` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m3 (#995) (renovate[bot], 2025-12-12)
- `79114e26519c` fix(deps): update jetty monorepo to v12.1.5 (#991) (renovate[bot], 2025-12-06)
- `478f95d312d7` fix(deps): update jetty monorepo to v12.1.4 (#981) (renovate[bot], 2025-11-26)
- `d7d9f5eda88d` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#980) (renovate[bot], 2025-11-25)
- `a8aaf3c662f2` fix(deps): update dependency org.apache.tomcat.embed:tomcat-embed-core to v11.0.14 (#979) (renovate[bot], 2025-11-24)
- `9b57c859051e` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.1 (#977) (renovate[bot], 2025-11-21)
- `160a322d83fa` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.8 (#975) (renovate[bot], 2025-11-12)
- `1743bda0b5ac` fix(deps): update dependency ch.qos.logback.access:logback-access-jetty12 to v2.0.7 (#973) (renovate[bot], 2025-11-07)

### Security

- `1da7cf96330d` update to use HttpRequestAuthenticationProvider (Sergio del Amo, 2026-02-18)

### Dependency Updates

- `bb3fe185cc7a` chore: Bump version to 6.0.1-SNAPSHOT (micronaut-build, 2026-05-14)
- `70855d924ea8` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2026-05-07)
- `b1a8acd12a59` Revert "Update dependency org.apache.tomcat.embed:tomcat-embed-core to v11.0.22 (#1072)" (Sergio del Amo, 2026-05-06)
- `f0bf56178d46` Update dependency org.apache.tomcat.embed:tomcat-embed-core to v11.0.22 (#1072) (renovate[bot], 2026-05-06)
- `74ba6ed378e6` Update Micronaut dependencies (#1052) (renovate[bot], 2026-05-05)
- `255d1bae78bf` Combine Renovate dependency upgrades for issue #1056 (#1057) (Graeme Rocher, 2026-05-01)
- `f3aaf6285290` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2026-04-17)
- `b1b6f484ea90` chore(deps): update dependency io.undertow:undertow-core to v2.3.24.final (#1041) (renovate[bot], 2026-04-15)
- `df4f62d1292a` chore(deps): update gradle to v9.4.1 (#1035) (renovate[bot], 2026-04-15)
- `1f1bf6328448` chore(deps): update softprops/action-gh-release action to v2.6.2 (#1038) (renovate[bot], 2026-04-15)
- `2f6e5fd354c9` chore(deps): update github artifact actions (#1031) (renovate[bot], 2026-04-15)
- `d0f99a9f439b` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2026-02-18)
- `0f2c64e42c1e` Fix Cors and conversion tests (#1026) (Sergio del Amo, 2026-02-18)
- `fd8ba068dcb5` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m15 (#997) (renovate[bot], 2026-02-18)
- `5bbc3d0868ba` chore(deps): update actions/checkout action to v6.0.2 (#1020) (renovate[bot], 2026-02-05)
- `85fe1830d0c1` chore(deps): update actions/cache action to v5 (#1002) (renovate[bot], 2026-02-04)
- `fa845ea06ded` chore(deps): update github artifact actions (major) (#1003) (renovate[bot], 2026-02-04)
- `1f990b3d419a` chore(deps): update gradle to v9.3.1 (#1014) (renovate[bot], 2026-02-02)
- `d47d0fed2021` chore(deps): update graalvm/setup-graalvm action to v1.4.5 (#1007) (renovate[bot], 2026-01-06)
- `d843dcd8dbf0` chore(deps): update dependency io.undertow:undertow-core to v2.3.20.final (#968) (renovate[bot], 2025-12-05)
- `3e84c4232230` chore(deps): update gradle to v9.2.1 (#988) (renovate[bot], 2025-12-05)
- `df88fbc3b7dc` chore(deps): update graalvm/setup-graalvm action to v1.4.4 (#989) (renovate[bot], 2025-12-05)
- `fefdaa2da481` chore(deps): update softprops/action-gh-release action to v2.5.0 (#990) (renovate[bot], 2025-12-05)
- `7c34b306ed7d` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#985) (renovate[bot], 2025-12-01)
- `e0cccf75a60e` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m11 (#983) (renovate[bot], 2025-11-28)
- `d4d7abe450f6` chore(deps): update graalvm/setup-graalvm action to v1.4.3 (#982) (renovate[bot], 2025-11-27)
- `d1b8a8fbc591` chore(deps): update softprops/action-gh-release action to v2.4.2 (#974) (renovate[bot], 2025-11-10)
- `0dd71650a020` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m9 (#972) (renovate[bot], 2025-11-05)
- `75ad69e7c6ac` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m8 (#971) (renovate[bot], 2025-11-01)
- `a491a1647614` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#969) (renovate[bot], 2025-10-27)
- `b770b10703cf` upgrade to Gradle 9.1 (Sergio del Amo, 2025-10-10)

### Documentation

- `94eb89a9189b` Docs: update micronaut-docs to 3.0.0 (#961) (issam liqali, 2025-10-16)

### Review Candidates

- `e7df066126f6` Update versions (Sergio del Amo, 2026-05-19)
- `c0cd0ac5a5bc` Update common files (#1075) (micronaut-build, 2026-05-14)
- `9847ef78b364` [skip ci] Release v6.0.0 (micronaut-build, 2026-05-14)
- `84fc47b65974` update versions (Sergio del Amo, 2026-05-14)
- `8ac1c208a8bb` micronaut core 5.0.0 (Sergio del Amo, 2026-05-13)
- `1a17fb03593f` Update common files (#1074) (micronaut-build, 2026-05-09)
- `f5538b023ea5` [skip ci] Release v6.0.0-RC1 (micronaut-build, 2026-05-07)
- `d423c3123b4f` sec: ignore GHSA-3x3v-w654-m28m (Sergio del Amo, 2026-05-07)
- `cac9028f0f14` Document Payara deployment workaround (#1069) (Graeme Rocher, 2026-05-06)
- `7194da5d0fa9` micronaut-gradle-plugin = "5.0.0-M1" (Sergio del Amo, 2026-05-06)
- `e7dd96410696` micronaut = "5.0.0-RC2" (Sergio del Amo, 2026-05-06)
- `e55c1e437b4a` Update common files (#1071) (micronaut-build, 2026-05-06)
- `91a93ccadfa1` Use current thread for POJA blocking work (#1070) (Graeme Rocher, 2026-05-05)
- `2a3d00b09643` [servlet] Update common files for branch 6.0.x (#1066) (micronaut-build, 2026-05-01)
- `e48692b002a5` Fix eagerInitSingletons default servlet mapping (#1064) (Graeme Rocher, 2026-04-30)
- `cd9aba40b989` Fix WAR servlet server lifecycle events (#1059) (Graeme Rocher, 2026-04-30)
- `12c4df2c31c8` Fix Jetty static resource CORS allowed origins (#1058) (Radovan Radic, 2026-04-30)
- `99fbae8a7603` Update common files (#1055) (micronaut-build, 2026-04-29)
- `11d68ebbec23` Update common files (#1051) (micronaut-build, 2026-04-26)
- `b0d2e869554f` [skip ci] Release v6.0.0-M3 (micronaut-build, 2026-04-17)
- `19b327434227` micronaut-validation = "5.0.0-M2" (Sergio del Amo, 2026-04-17)
- `1029d855a3ec` micronaut-session = "5.0.0-M2" (Sergio del Amo, 2026-04-17)
- `1437f12797e3` micronaut-serde = "3.0.0-M7" (Sergio del Amo, 2026-04-17)
- `5ed477cdd309` micronaut-reactor = "4.0.0-M2" (Sergio del Amo, 2026-04-17)
- `b4523fede644` Update common files (#1049) (micronaut-build, 2026-04-17)
- `e94abf6eea44` M5 changes (#1046) (Denis Stepanov, 2026-04-17)
- `84f682e0cb56` Use micronaut kotlin plugin (#1048) (Issam Liqali, 2026-04-16)
- `3569aa7ac2b7` micronaut = "5.0.0-M20" (Sergio del Amo, 2026-04-15)
- `4a07e731019f` Update common files (#1032) (micronaut-build, 2026-04-15)
- `5990e7973404` [skip ci] Release v6.0.0-M2 (micronaut-build, 2026-02-18)
- `8e12dcb6b5ca` use  RouteAttributes.getRouteMatch (Sergio del Amo, 2026-02-18)
- `9adabe646404` Merge branch '5.6.x' into 6.0.x (Sergio del Amo, 2026-02-18)
- `eca3571242e6` micronaut core 5.0.0-M11 (Sergio del Amo, 2026-02-18)
- `6796fc4e2da5` Update common files (#992) (micronaut-build, 2026-02-18)
- `e530af4b1849` undertow = '2.3.20.Final' (Sergio del Amo, 2025-12-05)
- `874f3af5eefb` [skip ci] Release v6.0.0-M1 (micronaut-build, 2025-12-05)
- `2c7b9376445b` use JSPecify annotations (Sergio del Amo, 2025-12-05)
- `c1d28822e28d` micronaut-serde = "3.0.0-M1" (Sergio del Amo, 2025-12-05)
- `0b758120e95a` reactor 4.0.0-M1 (Sergio del Amo, 2025-12-05)
- `6816a2f20cd6` micronaut = "5.0.0-M2" (Sergio del Amo, 2025-12-05)
- `be1d92dbb2cd` [servlet] Update common files for branch 6.0.x (#970) (micronaut-build, 2025-12-05)
- `1ff20722bf80` [WIP] Replace Micronaut nullability annotations with JSpecify (#987) (Copilot, 2025-12-02)
- `a03d12bbeb58` checkstyle: make classes final (Sergio del Amo, 2025-10-27)
- `6759fd97224b` kotlin = "2.2.21" (Sergio del Amo, 2025-10-27)
- `0f45505d783c` Update micronaut build and configure target JVM (#967) (issam liqali, 2025-10-27)
- `83b0ba7e0737` [servlet] Update common files for branch 6.0.x (#966) (micronaut-build, 2025-10-27)
- `c06f90312654` [servlet] Update common files for branch 6.0.x (#965) (micronaut-build, 2025-10-21)
- `056154ac1696` Merge branch '5.6.x' into 6.0.x (Sergio del Amo, 2025-10-17)
- `44972d0d9646` Micronaut 5 compatibility and release prep (#964) (issam liqali, 2025-10-16)
- `ee1a25868dcc` [servlet] Update common files for branch 6.0.x (#960) (micronaut-build, 2025-10-16)
- `11e8f3646630` Micronatu build plugin 8.0.0-M4 (Sergio del Amo, 2025-10-10)
- `777f06743fed` Merge branch '5.6.x' into 6.0.x (Sergio del Amo, 2025-10-10)
- `0c1283ee4373` projectVersion=6.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-10-10)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` buildSrc/build.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.servlet.http-server-tck-module.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.servlet.module.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` http-server-jdk/build.gradle.kts
- `M` http-server-jetty/build.gradle.kts
- `M` servlet-engine/build.gradle.kts
- `M` settings.gradle
- `M` test-sample-poja/build.gradle
- `M` test-suite-kotlin-jetty/build.gradle

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
- `M` http-server-jetty/src/test/java/io/micronaut/servlet/jetty/docs/DocsController.java
- `M` src/main/docs/guide/httpPoja.adoc
- `M` src/main/docs/guide/httpServer.adoc
- `M` src/main/docs/guide/jetty.adoc
- `M` src/main/docs/guide/knownIssues.adoc
- `M` src/main/docs/guide/toc.yml
- `M` src/main/docs/guide/tomcat.adoc
- `M` src/main/docs/guide/undertow.adoc
- `A` src/main/docs/guide/warDeployment/payara.adoc

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
- `A` config/checkstyle/custom-suppressions.xml
- `M` config/checkstyle/suppressions.xml
- `A` http-poja-apache/src/main/java/io/micronaut/http/poja/apache/ApacheExecutorServiceFactory.java
- `A` http-poja-apache/src/main/java/io/micronaut/http/poja/apache/ApacheRuntimeConfiguration.java
- `M` http-poja-apache/src/main/java/io/micronaut/http/poja/apache/ApacheServerlessApplication.java
- `M` http-poja-apache/src/main/java/io/micronaut/http/poja/apache/ApacheServletHttpRequest.java
- `M` http-poja-apache/src/main/java/io/micronaut/http/poja/apache/ApacheServletHttpResponse.java
- `A` http-poja-apache/src/main/java/io/micronaut/http/poja/apache/CurrentThreadExecutorService.java
- `A` http-poja-apache/src/main/java/io/micronaut/http/poja/apache/package-info.java
- `M` http-poja-common/src/main/java/io/micronaut/http/poja/PojaBinderRegistry.java
- `M` http-poja-common/src/main/java/io/micronaut/http/poja/PojaBodyBinder.java
- `M` http-poja-common/src/main/java/io/micronaut/http/poja/PojaHttpRequest.java
- `M` http-poja-common/src/main/java/io/micronaut/http/poja/PojaHttpServerlessApplication.java
- `M` http-poja-common/src/main/java/io/micronaut/http/poja/PojaHttpServlerlessApplicationContextConfigurer.java
- `A` http-poja-common/src/main/java/io/micronaut/http/poja/package-info.java
- `M` http-poja-common/src/main/java/io/micronaut/http/poja/util/MultiValueHeaders.java
- `M` http-poja-common/src/main/java/io/micronaut/http/poja/util/MultiValuesQueryParameters.java
- `M` http-server-jdk/src/main/java/io/micronaut/servlet/http/server/jdk/HttpExchangeHttpServletRequest.java
- `A` http-server-jdk/src/main/java/io/micronaut/servlet/http/server/jdk/JdkHttpServerConfiguration.java
- `M` http-server-jdk/src/main/java/io/micronaut/servlet/http/server/jdk/OutputStreamRequestedCallback.java
- `A` http-server-jdk/src/main/java/io/micronaut/servlet/http/server/jdk/package-info.java
- `M` http-server-jetty/src/main/java/io/micronaut/servlet/jetty/JettyConfiguration.java
- `M` http-server-jetty/src/main/java/io/micronaut/servlet/jetty/JettyFactory.java
- `M` http-server-jetty/src/main/java/io/micronaut/servlet/jetty/JettySSLSessionProvider.java
- `M` http-server-jetty/src/main/java/io/micronaut/servlet/jetty/JettyServer.java
- `M` http-server-jetty/src/main/java/io/micronaut/servlet/jetty/JettySslContextReload.java
- `A` http-server-jetty/src/main/java/io/micronaut/servlet/jetty/package-info.java
- `M` http-server-tomcat/src/main/java/io/micronaut/servlet/tomcat/TomcatConfiguration.java
- `M` http-server-tomcat/src/main/java/io/micronaut/servlet/tomcat/TomcatFactory.java
- `M` http-server-tomcat/src/main/java/io/micronaut/servlet/tomcat/TomcatServer.java
- `M` http-server-tomcat/src/main/java/io/micronaut/servlet/tomcat/TomcatVirtualThreadEnabler.java
- `A` http-server-tomcat/src/main/java/io/micronaut/servlet/tomcat/package-info.java
- `M` http-server-undertow/src/main/java/io/micronaut/servlet/undertow/UndertowConfiguration.java
- `M` http-server-undertow/src/main/java/io/micronaut/servlet/undertow/UndertowFactory.java
- `M` http-server-undertow/src/main/java/io/micronaut/servlet/undertow/UndertowServer.java
- `A` http-server-undertow/src/main/java/io/micronaut/servlet/undertow/package-info.java
- `A` osv-scanner.toml
- `M` servlet-api/src/main/java/io/micronaut/servlet/api/ServletAttributes.java
- `M` servlet-core/src/main/java/io/micronaut/servlet/http/BodyBuilder.java
- `M` servlet-core/src/main/java/io/micronaut/servlet/http/DefaultBodyBuilder.java
- `M` servlet-core/src/main/java/io/micronaut/servlet/http/SSLSessionProvider.java
- `M` servlet-core/src/main/java/io/micronaut/servlet/http/ServletBinderRegistry.java
- `M` servlet-core/src/main/java/io/micronaut/servlet/http/ServletBodyBinder.java
- `M` servlet-core/src/main/java/io/micronaut/servlet/http/ServletExchange.java
- `M` servlet-core/src/main/java/io/micronaut/servlet/http/ServletHttpHandler.java
- `M` servlet-core/src/main/java/io/micronaut/servlet/http/ServletHttpResponse.java
- `M` servlet-core/src/main/java/io/micronaut/servlet/http/ServletRequestBinder.java
- `M` servlet-core/src/main/java/io/micronaut/servlet/http/ServletResponseEncoder.java
- `M` servlet-core/src/main/java/io/micronaut/servlet/http/body/ExtendedInputStream.java
- `M` servlet-core/src/main/java/io/micronaut/servlet/http/encoders/AbstractFileEncoder.java
- `M` servlet-core/src/main/java/io/micronaut/servlet/http/encoders/FileEncoder.java
- `M` servlet-core/src/main/java/io/micronaut/servlet/http/encoders/StreamFileEncoder.java
- `M` servlet-core/src/main/java/io/micronaut/servlet/http/encoders/SystemFileEncoder.java
- `M` servlet-core/src/main/java/io/micronaut/servlet/http/server/AbstractServletServer.java
- `M` servlet-core/src/main/java/io/micronaut/servlet/http/server/HttpServerEmbeddedServer.java
- `M` servlet-core/src/main/java/io/micronaut/servlet/http/server/HttpServerFactory.java
- `M` servlet-core/src/main/java/io/micronaut/servlet/http/server/RootHttpHandlerPath.java
- `M` servlet-core/src/main/java/io/micronaut/servlet/http/server/ServletServerFactory.java
- `M` servlet-engine/src/main/java/io/micronaut/servlet/engine/DefaultServletHttpHandler.java
- `M` servlet-engine/src/main/java/io/micronaut/servlet/engine/DefaultServletHttpRequest.java
- `M` servlet-engine/src/main/java/io/micronaut/servlet/engine/DefaultServletHttpResponse.java
- `M` servlet-engine/src/main/java/io/micronaut/servlet/engine/MicronautServletConfiguration.java
- `D` servlet-engine/src/main/java/io/micronaut/servlet/engine/ServletCompletedFileUpload.java
- `M` servlet-engine/src/main/java/io/micronaut/servlet/engine/ServletCookieAdapter.java
- `M` servlet-engine/src/main/java/io/micronaut/servlet/engine/bind/CompletedPartRequestArgumentBinder.java
- `M` servlet-engine/src/main/java/io/micronaut/servlet/engine/bind/DefaultServletBinderRegistry.java
- `A` servlet-engine/src/main/java/io/micronaut/servlet/engine/bind/ServletCompletedFileUploadFactory.java
- `M` servlet-engine/src/main/java/io/micronaut/servlet/engine/bind/ServletConfigBinder.java
- `M` servlet-engine/src/main/java/io/micronaut/servlet/engine/bind/ServletContextBinder.java
- `M` servlet-engine/src/main/java/io/micronaut/servlet/engine/bind/ServletPartBinder.java
- `M` servlet-engine/src/main/java/io/micronaut/servlet/engine/initializer/MicronautServletInitializer.java
- `A` servlet-engine/src/main/java/io/micronaut/servlet/engine/server/ServletContextEmbeddedServer.java
- `M` servlet-engine/src/main/java/io/micronaut/servlet/engine/server/ServletServerFactory.java
- `M` servlet-processor/src/main/java/io/micronaut/servlet/annotation/processor/ServletAnnotationVisitor.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `A` http-poja-apache/src/test/groovy/io/micronaut/http/poja/ApacheBlockingExecutorSpec.groovy
- `A` http-poja-apache/src/test/groovy/io/micronaut/http/poja/ApacheEnablementSpec.groovy
- `M` http-poja-apache/src/test/groovy/io/micronaut/http/poja/SimpleServerSpec.groovy
- `A` http-poja-apache/src/test/groovy/io/micronaut/http/poja/apache/CurrentThreadExecutorServiceSpec.groovy
- `M` http-poja-test/src/main/java/io/micronaut/http/poja/test/TestingServerlessEmbeddedApplication.java
- `M` http-poja-test/src/test/groovy/io/micronaut/http/poja/test/SimpleServerSpec.groovy
- `M` http-server-jdk/src/test/java/io/micronaut/servlet/http/server/jdk/FormSubmissionTest.java
- `A` http-server-jdk/src/test/java/io/micronaut/servlet/http/server/jdk/JdkEnablementTest.java
- `A` http-server-jdk/src/test/java/io/micronaut/servlet/http/server/jdk/QuotedQueryParameterTest.java
- `M` http-server-jdk/src/test/java/io/micronaut/servlet/http/server/jdk/StatusTest.java
- `M` http-server-jetty/src/test/groovy/io/micronaut/servlet/jetty/JettyControllerConstraintHandlerSpec.groovy
- `M` http-server-jetty/src/test/groovy/io/micronaut/servlet/jetty/JettyCorsSpec.groovy
- `A` http-server-jetty/src/test/groovy/io/micronaut/servlet/jetty/JettyEagerInitSingletonsSpec.groovy
- `A` http-server-jetty/src/test/groovy/io/micronaut/servlet/jetty/JettyEnablementSpec.groovy
- `M` http-server-jetty/src/test/groovy/io/micronaut/servlet/jetty/JettyHttpPutSpec.groovy
- `M` http-server-jetty/src/test/groovy/io/micronaut/servlet/jetty/JettyJsonBodyBindingSpec.groovy
- `M` http-server-jetty/src/test/groovy/io/micronaut/servlet/jetty/JettyNullableCrudSpec.groovy
- `M` http-server-jetty/src/test/groovy/io/micronaut/servlet/jetty/JettyParameterBindingSpec.groovy
- `M` http-server-jetty/src/test/groovy/io/micronaut/servlet/jetty/JettyPrincipalBindingSpec.groovy
- `M` http-server-jetty/src/test/groovy/io/micronaut/servlet/jetty/JettyResponseEncoderSpec.groovy
- `M` http-server-jetty/src/test/groovy/io/micronaut/servlet/jetty/JettySessionSpec.groovy
- `M` http-server-jetty/src/test/groovy/io/micronaut/servlet/jetty/JettyStaticResourceResolutionSpec.groovy
- `M` http-server-jetty/src/test/groovy/io/micronaut/servlet/jetty/JettyStreamSpec.groovy
- `M` http-server-jetty/src/test/groovy/io/micronaut/servlet/jetty/filters/RequestFilterBodySpec.groovy
- `M` http-server-jetty/src/test/groovy/io/micronaut/servlet/jetty/servlet/ServletBodyTest.groovy
- `M` http-server-jetty/src/test/java/io/micronaut/servlet/jetty/ParametersController.java
- `A` http-server-tomcat/src/test/groovy/io/micronaut/servlet/tomcat/TomcatEnablementSpec.groovy
- `M` http-server-tomcat/src/test/groovy/io/micronaut/servlet/tomcat/TomcatParameterBinding2Spec.groovy
- `M` http-server-tomcat/src/test/groovy/io/micronaut/servlet/tomcat/TomcatParameterBindingSpec.groovy
- `M` http-server-tomcat/src/test/groovy/io/micronaut/servlet/tomcat/TomcatPrincipalBindingSpec.groovy
- `M` http-server-tomcat/src/test/groovy/io/micronaut/servlet/tomcat/TomcatResponseEncoderSpec.groovy
- `M` http-server-tomcat/src/test/groovy/io/micronaut/servlet/tomcat/TomcatSessionSpec.groovy
- `M` http-server-tomcat/src/test/java/io/micronaut/servlet/tomcat/ParametersController.java
- `A` http-server-undertow/src/test/groovy/io/micronaut/servlet/undertow/UndertowEnablementSpec.groovy
- `M` http-server-undertow/src/test/groovy/io/micronaut/servlet/undertow/UndertowParameterBindingSpec.groovy
- `M` http-server-undertow/src/test/groovy/io/micronaut/servlet/undertow/UndertowPrincipalBindingSpec.groovy
- `M` http-server-undertow/src/test/groovy/io/micronaut/servlet/undertow/UndertowResponseEncoderSpec.groovy
- `M` http-server-undertow/src/test/groovy/io/micronaut/servlet/undertow/UndertowSessionSpec.groovy
- `M` http-server-undertow/src/test/java/io/micronaut/servlet/undertow/ParametersController.java
- `A` servlet-engine/src/test/groovy/io/micronaut/servlet/engine/DefaultServletHttpRequestSpec.groovy
- `A` servlet-engine/src/test/groovy/io/micronaut/servlet/engine/initializer/MicronautServletInitializerSpec.groovy
- `A` servlet-engine/src/test/java/io/micronaut/servlet/engine/initializer/MicronautServletInitializerTest.java
- `A` servlet-engine/src/test/java/io/micronaut/servlet/engine/server/ServletContextEmbeddedServerTest.java
- `M` test-sample-poja/src/main/java/io/micronaut/http/poja/sample/TestController.java
- `A` test-sample-poja/src/test/java/io/micronaut/http/poja/sample/KeepAliveConnectionTest.java
- `A` test-sample-poja/src/test/java/io/micronaut/http/poja/sample/RuntimeSelectionTest.java
- `A` test-sample-poja/src/test/resources/application-test.yml
- `A` test-suite-http-server-tck-jdk/src/test/java/io/micronaut/servlet/http/server/jdk/tests/HttpHostResolverReplacement.java
- `M` test-suite-http-server-tck-jdk/src/test/java/io/micronaut/servlet/http/server/jdk/tests/HttpServerEmbeddedServerSuite.java
- `M` test-suite-http-server-tck-jetty/src/test/java/io/micronaut/http/server/tck/jetty/tests/HttpHostResolverReplacement.java
- `M` test-suite-http-server-tck-jetty/src/test/java/io/micronaut/http/server/tck/jetty/tests/JettyHttpServerTestSuite.java
- `M` test-suite-http-server-tck-poja-apache/src/test/java/io/micronaut/http/server/tck/poja/PojaApacheServerTestSuite.java
- `M` test-suite-http-server-tck-tomcat/src/test/java/io/micronaut/http/server/tck/tomcat/tests/HttpHostResolverReplacement.java
- `M` test-suite-http-server-tck-tomcat/src/test/java/io/micronaut/http/server/tck/tomcat/tests/TomcatHttpServerTestSuite.java
- `M` test-suite-http-server-tck-undertow/src/test/java/io/micronaut/http/server/tck/undertow/tests/HttpHostResolverReplacement.java
- `M` test-suite-http-server-tck-undertow/src/test/java/io/micronaut/http/server/tck/undertow/tests/UndertowHttpServerTestSuite.java
- `M` test-suite-kotlin-jetty/src/test/resources/application-test.yml

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

