Compared micronaut-security as mn4 → mn5.

  Scope:

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-security, branch 4.15.x, SHA c5a61da5e49d, clean
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-security, branch 5.0.x, SHA bb8e63002d52, clean
  - Report: /private/tmp/micronaut-security-4.15-to-5.0-comparison.md
  - Diff size: 590 files changed, 7152 insertions(+), 5564 deletions(-)

  Key findings:

  - Major baseline move: projectVersion 4.15.3-SNAPSHOT -> 5.0.1-SNAPSHOT, Micronaut 4.9.11 -> 5.0.0,
    Platform 4.9.3 -> 5.0.0-RC1, Gradle 8.14.3 -> 9.5.1, settings plugin 7.6.4 -> 8.0.0-M18, and .sdkmanrc
    adds java=25.0.1-graal.
  - New security-processor module owns the Jakarta JSR-250 annotation mappers. Users of @RolesAllowed,
    @PermitAll, or @DenyAll now need micronaut-security-processor instead of relying on micronaut-security-
    annotations.
  - Deprecated JWT/OIDC APIs were removed, including old JwtTokenValidator, JwtValidator, JwksSignature, old
    OpenID provider metadata builder/constructor paths, old blocking JWKS fetch methods, and old OAuth2
    password/token response validator classes.
  - New security context API/SPI was added: SecurityContext, SecurityContextHolder, and
    SecurityContextSupplier, with request-backed behavior wired through SecurityFilter.
  - JWT/JWKS handling changed: secret encryption supports a base64 flag, reactive JWKS validation tracks
    whether a token was already verified, and JWKS read-timeout logging is downgraded when another validator
    already succeeded.
  - OAuth2 Keycloak logout now uses RP-initiated logout parameters: post_logout_redirect_uri, id_token_hint,
    and client_id.
  - WebSocket support now includes AuthenticationWebSocketStateBinder for binding Authentication from the
    originating request.
  - Broad maintenance migration: many APIs switch to JSpecify nullability annotations; Micronaut BOMs move to
    their 5/6/7-era versions; Nimbus JOSE JWT changes 10.5 -> 10.9; JJWT remains 0.13.0; BouncyCastle remains
    1.70.

  I did not run tests; this was a folder comparison and targeted source-diff review only.

# Release Note Comparison

Generated: 2026-05-19 11:28 UTC
Comparison: `4.15.x` -> `5.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-security` | `4.15.x` | `c5a61da5e49d` | `git@github.com:micronaut-projects/micronaut-security.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-security` | `5.0.x` | `bb8e63002d52` | `git@github.com:micronaut-projects/micronaut-security.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-security`
- Commit candidates found: 307
- File changes listed: 590
- Version values listed: 67
- File status counts: A=60, D=16, M=510, R=4

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `micronautAotVersion` | `2.0.1` | `2.0.1` | `unchanged` |
| `gradle.properties` | `micronautDocsVersion` | `2.0.0` | `2.0.0` | `unchanged` |
| `gradle.properties` | `micronautGradlePluginVersion` | `4.5.5` | `4.6.2` | `changed` |
| `gradle.properties` | `projectVersion` | `4.15.3-SNAPSHOT` | `5.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.bcpkix` | `org.bouncycastle:bcpkix-jdk15on:1.70` | `org.bouncycastle:bcpkix-jdk15on:1.70` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.bcpkix-jdk15on` | `org.bouncycastle:bcpkix-jdk15on:1.70` | `org.bouncycastle:bcpkix-jdk15on:1.70` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.bcprov-jdk15on` | `org.bouncycastle:bcprov-jdk15on:1.70` | `org.bouncycastle:bcprov-jdk15on:1.70` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.geb-spock` | `org.apache.groovy.geb:geb-spock:8.0.0` | `org.apache.groovy.geb:geb-spock:8.0.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.graalvm-native-buildtools` | `org.graalvm.buildtools.native:org.graalvm.buildtools.native.gradle.plugin:0.10.6` | `org.graalvm.buildtools.native:org.graalvm.buildtools.native.gradle.plugin:1.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.kotlin-stdlib-jdk8` | `org.jetbrains.kotlin:kotlin-stdlib-jdk8:2.1.21` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.managed-jjwt-api` | `io.jsonwebtoken:jjwt-api:0.13.0` | `io.jsonwebtoken:jjwt-api:0.13.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-jjwt-impl` | `io.jsonwebtoken:jjwt-impl:0.13.0` | `io.jsonwebtoken:jjwt-impl:0.13.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-jjwt-jackson` | `io.jsonwebtoken:jjwt-jackson:0.13.0` | `io.jsonwebtoken:jjwt-jackson:0.13.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-nimbus-jose-jwt` | `com.nimbusds:nimbus-jose-jwt:10.5` | `com.nimbusds:nimbus-jose-jwt:10.9` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-cache` | `io.micronaut.cache:micronaut-cache-bom:5.3.0` | `io.micronaut.cache:micronaut-cache-bom:6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-data` | `io.micronaut.data:micronaut-data-bom:4.12.2` | `io.micronaut.data:micronaut-data-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-hibernate-validator` | `io.micronaut.beanvalidation:micronaut-hibernate-validator-bom:4.8.0` | `io.micronaut.beanvalidation:micronaut-hibernate-validator-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-multitenancy` | `io.micronaut.multitenancy:micronaut-multitenancy-bom:5.6.0` | `io.micronaut.multitenancy:micronaut-multitenancy-bom:6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-reactor` | `io.micronaut.reactor:micronaut-reactor-bom:3.7.0` | `io.micronaut.reactor:micronaut-reactor-bom:4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.14.1` | `io.micronaut.serde:micronaut-serde-bom:3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-servlet` | `io.micronaut.servlet:micronaut-servlet-bom:5.3.1` | `io.micronaut.servlet:micronaut-servlet-bom:6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-session` | `io.micronaut.session:micronaut-session-bom:4.6.0` | `io.micronaut.session:micronaut-session-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-sql` | `io.micronaut.sql:micronaut-sql-bom:6.1.1` | `io.micronaut.sql:micronaut-sql-bom:7.0.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test` | `io.micronaut.test:micronaut-test-bom:4.7.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-resources` | `io.micronaut.testresources:micronaut-test-resources-bom:2.8.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-validation` | `io.micronaut.validation:micronaut-validation-bom:4.9.0` | `io.micronaut.validation:micronaut-validation-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-views` | `io.micronaut.views:micronaut-views-bom:5.7.0` | `io.micronaut.views:micronaut-views-bom:6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.selenium-api` | `org.seleniumhq.selenium:selenium-api:4.34.0` | `org.seleniumhq.selenium:selenium-api:4.41.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.selenium-chrome-driver` | `org.seleniumhq.selenium:selenium-chrome-driver:4.34.0` | `org.seleniumhq.selenium:selenium-chrome-driver:4.41.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.selenium-firefox-driver` | `org.seleniumhq.selenium:selenium-firefox-driver:4.34.0` | `org.seleniumhq.selenium:selenium-firefox-driver:4.41.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.selenium-remote-driver` | `org.seleniumhq.selenium:selenium-remote-driver:4.34.0` | `org.seleniumhq.selenium:selenium-remote-driver:4.41.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.selenium-support` | `org.seleniumhq.selenium:selenium-support:4.34.0` | `org.seleniumhq.selenium:selenium-support:4.41.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.system-stubs-core` | `uk.org.webcompere:system-stubs-core:2.1.8` | `uk.org.webcompere:system-stubs-core:2.1.8` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.unboundid-ldapsdk` | `com.unboundid:unboundid-ldapsdk:7.0.3` | `com.unboundid:unboundid-ldapsdk:7.0.4` | `changed` |
| `gradle/libs.versions.toml` | `versions.awaitility` | `not present` | `4.3.0` | `added` |
| `gradle/libs.versions.toml` | `versions.bcpkix` | `1.70` | `1.70` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.bouncycastle` | `1.70` | `1.70` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.commons-codec` | `not present` | `1.20.0` | `added` |
| `gradle/libs.versions.toml` | `versions.geb` | `8.0.0` | `8.0.1` | `changed` |
| `gradle/libs.versions.toml` | `versions.graalvm-native-buildtools` | `0.10.6` | `1.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.jsonassert` | `1.5.3` | `1.5.3` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.kotlin` | `2.1.21` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.managed-jjwt` | `0.13.0` | `0.13.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-nimbus-jose-jwt` | `10.5` | `10.9` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.9.11` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-cache` | `5.3.0` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-data` | `4.12.2` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-hibernate-validator` | `4.8.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-multitenancy` | `5.6.0` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-platform` | `4.9.3` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-reactor` | `3.7.0` | `4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.14.1` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-servlet` | `5.3.1` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-session` | `4.6.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-sql` | `6.1.1` | `7.0.1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.7.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test-resources` | `2.8.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.9.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-views` | `5.7.0` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.selenium` | `4.34.0` | `4.41.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.system-stubs-core` | `2.1.8` | `2.1.8` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.unboundid-ldapsdk` | `7.0.3` | `7.0.4` | `changed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |
| `settings.gradle` | `plugin.io.micronaut.build.shared.settings` | `7.6.4` | `8.0.0-M18` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `148c349665f3` Remove nonexistent dependency from security docs (#2175) (Sergio del Amo, 2026-04-15)
- `03a63c8bfedc` Remove nonexistent dependency from security docs (#2175) (Sergio del Amo, 2026-04-15)
- `72f4164afbf5` remove extra blank line (Sergio del Amo, 2026-03-19)
- `dbcb40af9acb` remove spock version pin (Sergio del Amo, 2025-12-30)
- `c03ec5287c7a` remove junit-jupiter-params (Sergio del Amo, 2025-12-16)
- `ce6ccb5b4f42` remove junit-platform-engine (Sergio del Amo, 2025-12-16)
- `f499aab0a9ff` remove test-resources dependency (#2086) (Sergio del Amo, 2025-12-16)
- `36435cbe0a95` test: remove junit.framework.TestCase (Sergio del Amo, 2025-10-27)
- `cd5a2faf8399` test: remove junit.framework.TestCase (Sergio del Amo, 2025-10-27)
- `662c2a9d2434` checkstyle: remove unused imports (Sergio del Amo, 2024-09-12)
- `3e0a5b9add14` remove deprecated code (Sergio del Amo, 2024-09-11)

### Features

- `fbcbb55bedff` Add SecurityContextSupplier which can be set via SPI (#2169) (Sergio del Amo, 2026-04-14)
- `476e21d8077e` add micronaut.propagation=thread-local (Sergio del Amo, 2026-04-09)
- `42fba3508a9b` add agents (Sergio del Amo, 2026-03-18)
- `761dc81dc6d5` Add Base64 encoding support for SecretEncryptionConfiguration (#2125) (Marius Volkhart, 2026-02-13)
- `77cf0e32ded1` Add WebSocketStateBinder<Authentication>  (#2128) (Sergio del Amo, 2026-02-13)
- `1bdd25637497` add back deprecated constructor (Sergio del Amo, 2025-12-30)
- `fcbbdfef7cc8` add junit platform suite (Sergio del Amo, 2025-12-30)
- `bab759bd5904` feat(oauth2): add CREATE to Prompt enum for OIDC registration support (#2062) (Knut Olav Bøhmer, 2025-11-30)
- `06ac076ad9db` add @Requires ResourcemetadataWwwAuthenticateChallengeProvider (#2055) (Sergio del Amo, 2025-11-17)

### Fixes

- `5c3249638f7e` fix(deps): update dependency org.graalvm.buildtools.native:org.graalvm.buildtools.native.gradle.plugin to v1 (#2163) (renovate[bot], 2026-04-09)
- `d184f3bde68d` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m5 (#2161) (renovate[bot], 2026-03-29)
- `85c5420dbb2b` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m4 (#2158) (renovate[bot], 2026-03-27)
- `fc8686512f02` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m3 (#2155) (renovate[bot], 2026-03-25)
- `5b42533948a6` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v5.0.0-m5 (#2154) (renovate[bot], 2026-03-24)
- `d5275852a3d6` fix(#2146): Preserve token validator order (#2148) (Boris Wauters, 2026-03-19)
- `4e52afadac90` fix(#2146): Preserve token validator order (#2148) (Boris Wauters, 2026-03-19)
- `f1c10fe0e051` fix(deps): update dependency com.nimbusds:nimbus-jose-jwt to v10.8 (#2136) (renovate[bot], 2026-03-19)
- `4a73d57dba04` fix(deps): update selenium to v4.41.0 (#2138) (renovate[bot], 2026-03-19)
- `332f85f6bcb3` fix(deps): update dependency org.graalvm.buildtools.native:org.graalvm.buildtools.native.gradle.plugin to v0.11.5 (#2141) (renovate[bot], 2026-03-18)
- `e0c242df6888` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m17 (#2132) (renovate[bot], 2026-03-18)
- `1fd748c3ebf5` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v5.0.0-m3 (#2133) (renovate[bot], 2026-03-18)
- `2b834eab99db` fix(deps): update dependency io.micronaut.servlet:micronaut-servlet-bom to v6.0.0-m2 (#2134) (renovate[bot], 2026-03-18)
- `7306626e4b78` fix(jwt): downgrade unused JWKS read-timeout logging (#2129) (Graeme Rocher, 2026-02-16)
- `4368b66d51f8` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v4.14.3 (#2121) (renovate[bot], 2026-01-31)
- `47b96b4c6549` fix(deps): update selenium to v4.40.0 (#2117) (renovate[bot], 2026-02-12)
- `7a74eaa0b02f` fix(deps): update dependency com.nimbusds:nimbus-jose-jwt to v10.7 (#2110) (renovate[bot], 2026-02-12)
- `17765aaea9e7` fix(deps): update dependency com.nimbusds:nimbus-jose-jwt to v10.7 (#2110) (renovate[bot], 2026-02-12)
- `8153bfd2dcad` fix(deps): update selenium to v4.40.0 (#2117) (renovate[bot], 2026-02-12)
- `9a7851b15bae` fix(deps): update dependency org.graalvm.buildtools.native:org.graalvm.buildtools.native.gradle.plugin to v0.11.4 (#2118) (renovate[bot], 2026-02-12)
- `731c4c73ff94` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m10 (#2111) (renovate[bot], 2026-02-12)
- `1fd9b466174d` fix(deps): update dependency io.micronaut.cache:micronaut-cache-bom to v6.0.0-m2 (#2124) (renovate[bot], 2026-02-01)
- `653720744987` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m2 (#2112) (renovate[bot], 2026-01-31)
- `822c43117425` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v4.14.3 (#2121) (renovate[bot], 2026-01-31)
- `4b0c81fee297` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m7 (#2109) (renovate[bot], 2026-01-11)
- `9a7888549ef9` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to v7.0.0 (#2104) (renovate[bot], 2026-01-03)
- `38c75820ea37` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m6 (#2091) (renovate[bot], 2025-12-29)
- `c1271b53c6e4` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v4.14.2 (#2092) (renovate[bot], 2025-12-29)
- `3bda886e6e3c` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to v7 (#2098) (renovate[bot], 2025-12-29)
- `2d89c225d8b7` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m3 (#2083) (renovate[bot], 2025-12-16)
- `4533676e432a` fix(deps): update dependency org.graalvm.buildtools.native:org.graalvm.buildtools.native.gradle.plugin to v0.11.3 (#2075) (renovate[bot], 2025-12-10)
- `d1468dbcb617` fix(deps): update dependency com.unboundid:unboundid-ldapsdk to v7.0.4 (#2073) (renovate[bot], 2025-12-10)
- `391b6f7b4714` fix(deps): update dependency commons-codec:commons-codec to v1.20.0 (#2059) (renovate[bot], 2025-11-30)
- `72907e837077` fix(deps): update dependency io.micronaut.data:micronaut-data-bom to v4.14.1 (#2060) (renovate[bot], 2025-11-30)
- `f31c6c912345` fix(deps): update dependency io.micronaut.multitenancy:micronaut-multitenancy-bom to v5.8.0 (#2063) (renovate[bot], 2025-11-30)
- `960c9e695d21` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#2061) (renovate[bot], 2025-11-25)
- `05ecb0395f85` fix(deps): update dependency org.apache.groovy.geb:geb-spock to v8.0.1 (#2058) (renovate[bot], 2025-11-21)
- `425ad4228662` fix(deps): update dependency io.micronaut.reactor:micronaut-reactor-bom to v3.9.1 (#2051) (renovate[bot], 2025-11-17)
- `5cfe97288038` fix(deps): update dependency com.nimbusds:nimbus-jose-jwt to v10.6 (#2053) (renovate[bot], 2025-11-17)
- `75cca09b0ab9` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.8 (#2043) (renovate[bot], 2025-11-03)
- `dbb6ed50f3aa` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.7 (#2038) (renovate[bot], 2025-10-27)
- `043afa0d2b67` fix(deps): update dependency com.nimbusds:nimbus-jose-jwt to v10 (#1902) (renovate[bot], 2025-01-08)
- `893b2ddf2888` fix: blockOptional with publishOn Blocking ExecutorService::. (#1663) (Sergio del Amo, 2024-04-05)
- `3fed80bf3997` fix(deps): update dependency io.micronaut.multitenancy:micronaut-multitenancy-bom to v5.3.0 (#1658) (renovate[bot], 2024-04-04)
- `6a5a1c0dffd8` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.3.12 (#1654) (renovate[bot], 2024-03-27)
- `e376a54935e7` fix(deps): update dependency io.micronaut.sql:micronaut-sql-bom to v5.5.2 (#1653) (renovate[bot], 2024-03-27)
- `c9fa1379a438` fix(deps): update dependency com.unboundid:unboundid-ldapsdk to v7 (#1650) (renovate[bot], 2024-03-21)
- `d83b6049184d` fix: `file:` prefix is not working for static jwks configurations (#1635) (Jonathan, 2024-03-18)
- `ccf1bfce457f` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.8.2 (#1638) (renovate[bot], 2024-03-18)
- `00782c175e81` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.4.4 (#1642) (renovate[bot], 2024-03-18)
- `5cfdfcc20d5b` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.3.11 (#1643) (renovate[bot], 2024-03-18)
- `03431ae6f90e` fix(deps): update dependency io.micronaut.servlet:micronaut-servlet-bom to v4.6.0 (#1632) (renovate[bot], 2024-03-14)
- `3fe407285088` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.3.10 (#1631) (renovate[bot], 2024-03-14)
- `0b9b5d80162e` fix(deps): update dependency io.micronaut.testresources:micronaut-test-resources-bom to v2.4.0 (#1627) (renovate[bot], 2024-03-08)
- `6726137c6418` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.4.3 (#1624) (renovate[bot], 2024-03-05)

### Security

- `95760812bf23` fix test-suite-aot.sh adding security processor (Sergio del Amo, 2026-05-08)
- `0e0313c311a8` [security] Update common files for branch 5.0.x (#2185) (micronaut-build, 2026-05-08)
- `2e0abfdeed79` SecurityContext and SecurityContextHolder APIs (#2168) (Sergio del Amo, 2026-04-13)
- `d423eb3a5ed0` initialize at build time AuthenticationMode in native-image.properties (#2150) (Sergio del Amo, 2026-03-19)
- `2e3221819164` docs: correct section title and align content with authentication strategies (#2081) (issam liqali, 2025-12-10)
- `b68d99f54332` [security] Update common files for branch 5.0.x (#2049) (micronaut-build, 2025-11-17)
- `741c4aaf647b` imp: Oauth2 not coupled to HTTP [ci skip] (#1396) (Sergio del Amo, 2024-03-08)

### Dependency Updates

- `cf956b0f507c` chore: Bump version to 5.0.1-SNAPSHOT (micronaut-build, 2026-05-18)
- `1a514c837732` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-05-08)
- `97341f730e20` Update Micronaut dependencies (#2180) (renovate[bot], 2026-05-02)
- `2293c968af33` Update dependency com.nimbusds:nimbus-jose-jwt to v10.9 (#2181) (renovate[bot], 2026-05-02)
- `c48a3c20458c` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-04-17)
- `565d778ca161` chore: Bump version to 4.17.3-SNAPSHOT (micronaut-build, 2026-04-16)
- `107f0ad81b29` chore: Bump version to 4.18.1-SNAPSHOT (micronaut-build, 2026-04-16)
- `fe3697b16b6b` chore: Bump version to 4.17.3-SNAPSHOT (micronaut-build, 2026-04-16)
- `7461735f1157` chore: Bump version to 4.16.3-SNAPSHOT (micronaut-build, 2026-04-15)
- `0fc88df8b529` Update dependency io.micronaut:micronaut-core-bom to v5.0.0-M20 (renovate[bot], 2026-04-09)
- `a203309824f9` Update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-M6 (#2165) (renovate[bot], 2026-04-09)
- `2d091a4ee760` chore(deps): update plugin com.gradleup.shadow to v9.4.1 (#2159) (renovate[bot], 2026-03-28)
- `75a075e3bf3e` chore(deps): update gradle to v9.4.1 (#2152) (renovate[bot], 2026-03-20)
- `510a3d5925c8` chore(deps): update plugin com.gradleup.shadow to v9.4.0 (#2137) (renovate[bot], 2026-03-18)
- `c6a2980981e5` chore(deps): update gradle to v9.4.0 (#2142) (renovate[bot], 2026-03-18)
- `4df9d8f34651` chore(deps): update softprops/action-gh-release action to v2.6.1 (#2144) (renovate[bot], 2026-03-18)
- `358d3e5c74a8` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#2131) (renovate[bot], 2026-02-17)
- `23cda5383849` chore: Bump version to 4.17.2-SNAPSHOT (micronaut-build, 2026-02-16)
- `a8901d4f5468` chore: Bump version to 4.17.1-SNAPSHOT (micronaut-build, 2026-02-13)
- `5b001b6ede1d` chore(deps): update gradle to v9.3.1 (#2115) (renovate[bot], 2026-02-12)
- `9372a3c2e324` chore(deps): update actions/setup-java action to v5.2.0 (#2120) (renovate[bot], 2026-02-12)
- `8b541c124258` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m16 (#2127) (renovate[bot], 2026-02-12)
- `d6f36a0f9c36` chore(deps): update micronautgradlepluginversion to v4.6.2 (#2126) (renovate[bot], 2026-02-07)
- `1bc2f0e09db9` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m15 (#2123) (renovate[bot], 2026-01-31)
- `ee7888ee0cfb` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m14 (#2108) (renovate[bot], 2026-01-10)
- `35476b19a92b` chore(deps): update plugin com.gradleup.shadow to v9.3.1 (#2106) (renovate[bot], 2026-01-07)
- `08136210ab93` chore(deps): update graalvm/setup-graalvm action to v1.4.5 (#2105) (renovate[bot], 2026-01-06)
- `94357b27fb01` chore: Bump version to 4.16.2-SNAPSHOT (micronaut-build, 2025-12-30)
- `b1516501a08b` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2025-12-30)
- `6e92b16b024b` chore(deps): update plugin com.gradleup.shadow to v9 (#2096) (renovate[bot], 2025-12-30)
- `8fa97148ba00` spock version from micronaut not from geb-spock (Sergio del Amo, 2025-12-30)
- `3abe684dc31c` chore(deps): update actions/checkout action to v6 (#2099) (renovate[bot], 2025-12-30)
- `b0eb3059b9e9` chore(deps): update actions/cache action to v5 (#2093) (renovate[bot], 2025-12-29)
- `7feb2e130316` chore(deps): update stefanzweifel/git-auto-commit-action action to v7 (#2097) (renovate[bot], 2025-12-29)
- `acf44a0b5038` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m13 (#2088) (renovate[bot], 2025-12-29)
- `d3c70832be83` chore(deps): update actions/setup-java action to v5 (#2078) (renovate[bot], 2025-12-10)
- `08239d47896a` chore(deps): update actions/setup-java action to v4.8.0 (#2074) (renovate[bot], 2025-12-10)
- `793065641cb3` chore(deps): update graalvm/setup-graalvm action to v1.4.4 (#2072) (renovate[bot], 2025-12-10)
- `fa4aaf53b3a0` chore(deps): update softprops/action-gh-release action to v2.5.0 (#2071) (renovate[bot], 2025-12-10)
- `2b5b7611c017` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#2067) (renovate[bot], 2025-12-01)
- `cd94c7e671f0` chore: Bump version to 4.16.1-SNAPSHOT (micronaut-build, 2025-11-28)
- `e152ed92183d` chore(deps): update graalvm/setup-graalvm action to v1.4.3 (#2066) (renovate[bot], 2025-11-28)
- `71c1f7e967bd` chore(deps): update gradle to v9.2.1 (#2057) (renovate[bot], 2025-11-20)
- `7b1b718f5bd3` chore(deps): update micronautgradlepluginversion to v4.6.1 (#2052) (renovate[bot], 2025-11-17)
- `09e08240be99` chore(deps): update softprops/action-gh-release action to v2.4.2 (#2050) (renovate[bot], 2025-11-10)
- `e3e130329c3e` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m9 (#2046) (renovate[bot], 2025-11-07)
- `a798c6c62c84` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m8 (#2041) (renovate[bot], 2025-11-03)
- `5d6e7e36e525` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#2039) (renovate[bot], 2025-10-27)
- `198c08b807c1` chore(deps): update gradle/gradle-build-action action to v3.2.1 (#1668) (renovate[bot], 2024-04-12)
- `8f231273a569` chore(deps): update micronautgradlepluginversion to v4.3.6 (#1669) (renovate[bot], 2024-04-12)
- `58085418bf1c` chore(deps): update gradle/gradle-build-action action to v3.2.0 (#1664) (renovate[bot], 2024-04-05)
- `abde357610b3` chore(deps): update dependency gradle to v8.7 (#1655) (renovate[bot], 2024-03-27)
- `1ab4d7c29429` chore(deps): update graalvm/setup-graalvm action to v1.2.1 (#1651) (renovate[bot], 2024-03-27)
- `1c22adcd137b` chore(deps): update micronautgradlepluginversion to v4.3.5 (#1652) (renovate[bot], 2024-03-27)
- `1ed53e748d65` chore(deps): update graalvm/setup-graalvm action to v1.2.0 (#1647) (renovate[bot], 2024-03-19)
- `6537848a25bf` chore(deps): update kotlin monorepo to v1.9.23 (#1628) (renovate[bot], 2024-03-18)
- `a0ec82e35b9c` chore(deps): update graalvm/setup-graalvm action to v1.1.9 (#1636) (renovate[bot], 2024-03-18)
- `8746356068ab` chore(deps): update plugin io.micronaut.build.shared.settings to v6.7.0 (#1644) (renovate[bot], 2024-03-18)
- `f93878b2f86b` chore(deps): update micronautgradlepluginversion to v4.3.4 (#1620) (renovate[bot], 2024-03-04)
- `c3dd80ef26de` chore(deps): update plugin io.micronaut.build.shared.settings to v6.6.4 (#1621) (renovate[bot], 2024-03-04)

### Documentation

- `335c7517d81b` Docs: fix wrong package reference for ReactiveJwksSignature (#2107) (issam liqali, 2026-01-08)
- `d59608be8bb4` Docs: fix wrong package reference for ReactiveJwksSignature (#2107) (issam liqali, 2026-01-08)
- `3f2a333ca249` doc: Mention io.micrometer:context-propagation on Token Propagation (#1630) (Arnau Aregall, 2024-03-15)
- `2fdf31def993` doc: fix artifact id (#1616) (Sergio del Amo, 2024-02-27)

### Internal

- `fc776514bdb2` build: add micronaut router (Sergio del Amo, 2026-05-08)
- `23e7b7046aaf` build: prefer project modules (Sergio del Amo, 2026-04-14)
- `2c1f959f9e82` build: exclude geb-implicit-assertions (Sergio del Amo, 2026-03-19)
- `4495b1b95874` ci: projectVersion=4.18.0-SNAPSHOT [ci skip] (Sergio del Amo, 2026-03-18)
- `93c1627d06be` ci: projectVersion=4.17.0-SNAPSHOT [ci skip] (sdelamo, 2026-02-12)
- `d1029a0c813b` Build: Update to Micronaut 5 (#2084) (issam liqali, 2025-12-15)
- `20382201af12` test: make eventLoop assertion case insensitive (Sergio del Amo, 2025-11-17)
- `1c4815ee22cb` test: add test 405 for /mcp and reject-not-found (#2048) (Sergio del Amo, 2025-11-17)
- `3efa70b5cf4f` test: add junit-platform-launcher (Sergio del Amo, 2025-10-14)
- `460f11424972` ci: projectVersion=5.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2024-09-11)
- `c648015ec133` refactor: extract methods (#1659) (Sergio del Amo, 2024-04-04)

### Review Candidates

- `bb8e63002d52` update versions (Sergio del Amo, 2026-05-19)
- `8562a23dd21c` [skip ci] Release v5.0.0 (micronaut-build, 2026-05-18)
- `64c658bd39b8` Update common files (#2187) (micronaut-build, 2026-05-14)
- `e29f0645b716` update versions (Sergio del Amo, 2026-05-14)
- `969fd6c4692b` micronaut-platform = "5.0.0-RC1" (Sergio del Amo, 2026-05-13)
- `62aae89a0211` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `4256d9673648` Update common files (#2186) (micronaut-build, 2026-05-09)
- `63bc699977b9` [skip ci] Release v5.0.0-RC1 (micronaut-build, 2026-05-08)
- `4673577ae919` git: ignore .kotlin (Sergio del Amo, 2026-05-08)
- `5c12a442d7a6` update versions (Sergio del Amo, 2026-05-08)
- `1513abcc7f7c` Update common files (#2184) (micronaut-build, 2026-05-06)
- `4626c6ac1244` replace start import (Sergio del Amo, 2026-05-03)
- `851a2f6b0020` Update common files (#2182) (micronaut-build, 2026-05-02)
- `66c4c846e730` Update common files (#2178) (micronaut-build, 2026-04-26)
- `ec9da66b6a8c` [skip ci] Release v5.0.0-M2 (micronaut-build, 2026-04-17)
- `7624f91f9f6f` Merge branch '4.18.x' into 5.0.x (Sergio del Amo, 2026-04-17)
- `f33029106bd4` micronaut-test = "5.0.0-M8" (Sergio del Amo, 2026-04-17)
- `4412b6f2d40a` micronaut-validation = "5.0.0-M2" (Sergio del Amo, 2026-04-17)
- `9293cab41b45` micronaut-session = "5.0.0-M2" (Sergio del Amo, 2026-04-17)
- `3068d3610d33` micronaut-serde = "3.0.0-M7" (Sergio del Amo, 2026-04-17)
- `bca6f2fbf689` micronaut-cache = "6.0.0-M3" (Sergio del Amo, 2026-04-17)
- `3f98a4bb899b` [skip ci] Release v4.17.2 (micronaut-build, 2026-04-16)
- `0b921f46c9ff` Update common files (#2176) (micronaut-build, 2026-04-17)
- `e077552db4cc` [skip ci] Release v4.18.0 (micronaut-build, 2026-04-16)
- `fc2b6c91aa81` Merge branch '4.17.x' into 4.18.x (Sergio del Amo, 2026-04-16)
- `78521956c2bc` [skip ci] Release v4.17.2 (micronaut-build, 2026-04-16)
- `d459d583153d` Merge branch '4.18.x' into 5.0.x (Sergio del Amo, 2026-04-15)
- `7e08767d7f2c` Merge branch '4.17.x' into 4.18.x (Sergio del Amo, 2026-04-15)
- `ce4f3cf8f45c` Merge branch '4.16.x' into 4.17.x (Sergio del Amo, 2026-04-15)
- `6d45c180b84e` [skip ci] Release v4.16.2 (micronaut-build, 2026-04-15)
- `5dccf74600e2` Merge branch '4.15.x' into 4.16.x (Sergio del Amo, 2026-04-15)
- `52a20ebfa35c` enable test-suite-groovy (#2167) (Sergio del Amo, 2026-04-15)
- `639273045b90` use parameterized test (Sergio del Amo, 2026-04-15)
- `e22aa8de0e61` use Jspecify nullability annotations (Sergio del Amo, 2026-04-14)
- `cd8d508e796f` Merge branch '4.18.x' into 5.0.x (Sergio del Amo, 2026-04-14)
- `771bcf7f165d` sql 7.0.1-M1 (Sergio del Amo, 2026-04-14)
- `e16c77f17bad` micronaut-test = "5.0.0-M7" (Sergio del Amo, 2026-04-14)
- `9e4f430a7f45` micronaut-reactor = "4.0.0-M2" (Sergio del Amo, 2026-04-14)
- `4e0631e56e07` micronaut = "5.0.0-M22" (Sergio del Amo, 2026-04-14)
- `584096a73b2d` disable test-suite-groovy (Sergio del Amo, 2026-04-10)
- `72fca352df6d` avoid PropagatedContext with try with resources (Sergio del Amo, 2026-04-09)
- `851aeea24762` platform 5.0.0-M1 (Sergio del Amo, 2026-04-09)
- `065888125225` use properties instead of yaml config (Sergio del Amo, 2026-04-09)
- `faaa3e872bd7` Update common files (#2164) (micronaut-build, 2026-04-09)
- `2da5ee9e8f66` Update common files (#2156) (micronaut-build, 2026-03-25)
- `fec1c74945d3` micronaut-sql = "6.3.3" (Sergio del Amo, 2026-03-19)
- `9e8d140ac112` micronaut-data = "4.14.3" (Sergio del Amo, 2026-03-19)
- `304fddb92970` micronaut-servlet = "5.6.1" (Sergio del Amo, 2026-03-19)
- `936c5564ba7e` micronaut-logging = "1.7.3" (Sergio del Amo, 2026-03-19)
- `07c2644fead3` micronaut-test = "4.10.3" (Sergio del Amo, 2026-03-19)
- `d7bb14934002` micronaut = "4.10.18" (Sergio del Amo, 2026-03-19)
- `39c8bd2ee375` Revert "don’t run aot tests" (#2087) (Sergio del Amo, 2026-03-19)
- `c6f9db0a0ad8` enable test (Sergio del Amo, 2026-03-19)
- `d8c2fb4ac185` sql 7.0.0-M8 (Sergio del Amo, 2026-03-19)
- `d1d56b7798d8` data 5.0.0-M4 (Sergio del Amo, 2026-03-19)
- `c9210bdc691b` re-enable tests (Sergio del Amo, 2026-03-19)
- `d6676b296e28` Use RouteAttributes::getRouteMatch (#2149) (Sergio del Amo, 2026-03-19)
- `9100760ee76f` micronaut-platform = "4.10.10" (Sergio del Amo, 2026-03-19)
- `01e9d1f24cc3` micronaut platform 4.10.9 (Sergio del Amo, 2026-03-19)
- `2c6864b05d9b` micronaut-views = "6.0.0-M1" (Sergio del Amo, 2026-03-19)
- `12163a24898c` git: ignore .oca folder (Sergio del Amo, 2026-03-18)
- `fe35fbbc696a` Update common files (#2140) (micronaut-build, 2026-03-18)
- `9b7765ad9b11` Merge branch '4.17.x' into 5.0.x (sdelamo, 2026-02-16)
- `912ade287f33` [skip ci] Release v4.17.1 (micronaut-build, 2026-02-16)
- `f880b974b770` disable SecuredExpressionsSpec (sdelamo, 2026-02-16)
- `096ca2faf18a` fix kotlin compilation (sdelamo, 2026-02-16)
- `cd9e8db939e0` use updatable not updateable (sdelamo, 2026-02-16)
- `fff69ad81d91` Merge branch '4.17.x' into 5.0.x (sdelamo, 2026-02-16)
- `0a3d518c51eb` [skip ci] Release v4.17.0 (micronaut-build, 2026-02-13)
- `c729c877b8ef` Update common files (#2103) (micronaut-build, 2026-02-12)
- `39d4c07c1ad4` [skip ci] Release v4.16.1 (micronaut-build, 2025-12-30)
- `4563ec62bfde` [skip ci] Release v5.0.0-M1 (micronaut-build, 2025-12-30)
- `73bd329b0f70` Uncomment test-suite-kotlin inclusion in settings (#2047) (Sergio del Amo, 2025-12-30)
- `f81d2dfc44ad` disable test (Sergio del Amo, 2025-12-30)
- `ef18ea8eaace` qualifier not quailfier (Sergio del Amo, 2025-12-30)
- `2b48f6c95c35` Merge branch '4.16.x' into 5.0.x (Sergio del Amo, 2025-12-30)
- `30bde1a0a5d2` Revert "test: ignore keycloack tests on CI (#2021)" (#2101) (Sergio del Amo, 2025-12-30)
- `a06233fb0247` Merge branch '4.16.x' into 5.0.x (Sergio del Amo, 2025-12-30)
- `5f7f5d22ad64` Keycloak: switch to RP-initiated logout (post_logout_redirect_uri + id_token_hint)  (#2100) (Sergio del Amo, 2025-12-30)
- `d5694911dd1d` enable binary compatibility (Sergio del Amo, 2025-12-30)
- `21061f6943a2` platform = "4.10.6" (Sergio del Amo, 2025-12-30)
- `e8390a1924ba` latest milestones (Sergio del Amo, 2025-12-30)
- `268313bb2260` Update common files (#2095) (micronaut-build, 2025-12-29)
- `1a9cff03446d` fix jackson 3 import (Sergio del Amo, 2025-12-16)
- `b6d249b3e98c` don’t run aot tests (Sergio del Amo, 2025-12-16)
- `ebec09c4cfa7` micronaut-servlet = "6.0.0-M1" (Sergio del Amo, 2025-12-15)
- `44a5523d273f` Fix claim validator property name in documentation (#2085) (issam liqali, 2025-12-15)
- `e96d20ccd599` Fix claim validator property name in documentation (#2085) (issam liqali, 2025-12-15)
- `d0b99149b65b` Update common files (#2076) (micronaut-build, 2025-12-10)
- `d918b5d131bc` Merge branch '4.16.x' into 5.0.x (Sergio del Amo, 2025-12-01)
- `58fef77a7a09` Merge branch '4.15.x' into 4.16.x (Sergio del Amo, 2025-12-01)
- `f7a955ec87e8` Replace Micronaut nullability annotations with JSpecify annotations (#2069) (Copilot, 2025-12-01)
- `60f4078bb837` Update common files (#2056) (micronaut-build, 2025-11-30)
- `77e98663971e` [skip ci] Release v4.16.0 (micronaut-build, 2025-11-28)
- `93f14d69b2b5` git: ignore .kotlin (Sergio del Amo, 2025-11-17)
- `be51de08cd15` Micronaut Gradle Build Plugin 7.6.6 (Sergio del Amo, 2025-11-17)
- `2276c8abef9e` micronaut-validation = "4.12.0" (Sergio del Amo, 2025-11-17)
- `48610ca7a9c5` micronaut-data = "4.14.1" (Sergio del Amo, 2025-11-17)
- `9dbadb48485f` micronaut-session = "4.8.0" (Sergio del Amo, 2025-11-17)
- `b1de7fb507b2` micronaut-servlet = "5.6.0" (Sergio del Amo, 2025-11-17)
- `808f05a029a1` micronaut-serde = "2.16.2" (Sergio del Amo, 2025-11-17)
- `bddf872afc20` micronaut-sql = "6.3.2" (Sergio del Amo, 2025-11-17)
- `1c9281f1845f` micronaut-multitenancy = "5.8.0" (Sergio del Amo, 2025-11-17)
- `1f4c186c91dc` micronaut-reactor = "3.9.1" (Sergio del Amo, 2025-11-17)
- `0f945201eef5` micronaut-test = "4.10.2" (Sergio del Amo, 2025-11-17)
- `9cf9ee0814a9` micronaut = "4.10.8" (Sergio del Amo, 2025-11-17)
- `cdd42426597d` sync github actions (Sergio del Amo, 2025-11-17)
- `3937bf4447e1` Update common files (#2045) (micronaut-build, 2025-11-07)
- `96eb6271197b` Update to 8 0 0 m9 (#2044) (Sergio del Amo, 2025-11-07)
- `9f310eadc520` 8.0.0-M6 (Sergio del Amo, 2025-10-27)
- `2f65a820ee03` test 4.10.2 (Sergio del Amo, 2025-10-27)
- `ad3e66cbb815` platform 4.10.0 (Sergio del Amo, 2025-10-27)
- `5d94c682d09a` use kotlin compilerOptions intead of jvmToolchain (Sergio del Amo, 2025-10-27)
- `76b7e6486db1` update to Kotlin 2.2.20 and 8.0.0-M5 (#2036) (araysse, 2025-10-22)
- `3c142e6b50b5` Update common files (#2037) (micronaut-build, 2025-10-22)
- `6c83a830a822` Update common files (#2035) (micronaut-build, 2025-10-21)
- `7ed44b1dde8b` Micronaut 5 compatibility and release prep (#2034) (issam liqali, 2025-10-16)
- `81e4bd8b48d0` Update common files (#2033) (micronaut-build, 2025-10-16)
- `7ff0d243a0dc` micronaut gradle build plugin 8.0.0-M4 (Sergio del Amo, 2025-10-14)
- `f54ebde1fe0d` annotate UserInfoClientFactory  with @Requires (Sergio del Amo, 2025-10-14)
- `2e0ecc3888e5` Merge branch '4.16.x' into 5.0.x (Sergio del Amo, 2025-10-14)
- `0161ff373713` Merge branch '4.15.x' into 4.16.x (Sergio del Amo, 2025-10-14)
- `0d3a68bfdbd4` micronaut-platform = "4.9.4" (Sergio del Amo, 2025-10-14)
- `599bcd386bb6` sql 6.2.2 (Sergio del Amo, 2025-10-14)
- `2612543033d7` data 4.13.7 (Sergio del Amo, 2025-10-14)
- `41c7aa0c7ec5` validation 4.11.0 (Sergio del Amo, 2025-10-14)
- `f663b764a3b2` views 5.9.0 (Sergio del Amo, 2025-10-14)
- `d9c0fdecadeb` session 4.7.0 (Sergio del Amo, 2025-10-14)
- `6fe2822f4d09` servlet 5.5.1 (Sergio del Amo, 2025-10-14)
- `8637ee92d39c` serde 2.15.5 (Sergio del Amo, 2025-10-14)
- `d5c967c561b1` test resources 2.10.1 (Sergio del Amo, 2025-10-14)
- `931bd1bdcdb6` logging 1.7.1 (Sergio del Amo, 2025-10-14)
- `aac8bf407c53` multi-tenancy 5.7.0 (Sergio del Amo, 2025-10-14)
- `e819fe874ea5` reactor 3.9.0 (Sergio del Amo, 2025-10-14)
- `7c03d6cf18ed` test 4.9.0 (Sergio del Amo, 2025-10-14)
- `c27874433c7f` micronaut core 4.10.4 (Sergio del Amo, 2025-10-14)
- `187eaca8e6d4` projectVersion=4.16.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-10-14)
- `b0e93e373345` Merge branch '4.12.x' into 5.0.x (sdelamo, 2025-01-08)
- `6b6e61ac9416` set org.gradle.jvmargs=-Xmx2g (Sergio del Amo, 2024-09-11)
- `825a42ca7268` Merge branch '4.11.x' into 5.0.x (Sergio del Amo, 2024-09-11)
- `830018ffa7fd` breaks: delete deprecated code (#1665) (Sergio del Amo, 2024-04-06)
- `206d1346bbf5` Update common files (#1649) (micronaut-build, 2024-03-27)
- `42da577b826f` breaks: Delete @Deprecated code (#1626) (Sergio del Amo, 2024-03-21)
- `16e47467e86f` Merge branch '4.7.x' (Sergio del Amo, 2024-03-18)
- `0fd119de0691` Merge branch '4.7.x' (Sergio del Amo, 2024-03-18)
- `e26f642fce2f` Update common files (#1639) (micronaut-build, 2024-03-18)
- `d9cdf56b5db0` Merge branch '4.7.x' (Sergio del Amo, 2024-03-18)
- `ec06386a690d` Merge branch '4.7.x' into master (Sergio del Amo, 2024-03-05)
- `4e0f57e07b4a` Clarify non-blocking requirements in TokenValidator#validateToken javadoc (#1617) (Dmitry Spikhalskiy, 2024-03-04)
- `ec078699cfe1` breaks: Move processors to separate module (#1611) (Tim Yates, 2024-02-27)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` .github/workflows/update-gradle-wrapper.yml
- `M` buildSrc/build.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.security-module.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.security-tests.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` security-csrf/build.gradle.kts
- `M` security-jwt/build.gradle.kts
- `M` security-oauth2/build.gradle.kts
- `A` security-processor/build.gradle.kts
- `M` security-session/build.gradle.kts
- `M` security/build.gradle.kts
- `M` settings.gradle
- `M` test-suite-aot-authserver/build.gradle
- `M` test-suite-aot/build.gradle
- `M` test-suite-geb/build.gradle.kts
- `M` test-suite-graal/build.gradle
- `M` test-suite-groovy/build.gradle
- `M` test-suite-hibernate-validator/build.gradle.kts
- `M` test-suite-http/build.gradle
- `M` test-suite-jackson-databind-bean-introspection-module-false/build.gradle.kts
- `M` test-suite-jwks-cache/build.gradle.kts
- `M` test-suite-jwt-nimbus/build.gradle.kts
- `R063` test-suite-kotlin/build.gradle.kts
- `M` test-suite-ldap/build.gradle
- `A` test-suite-security-context/build.gradle.kts
- `M` test-suite-security-service/build.gradle.kts
- `M` test-suite-tomcat/build.gradle
- `M` test-suite-utils-security/build.gradle
- `M` test-suite-utils/build.gradle
- `M` test-suite/build.gradle

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
- `A` security-jwt/src/test/groovy/io/micronaut/docs/encryptionbase64/JwtEncryptionBase64Spec.groovy
- `M` security-jwt/src/test/groovy/io/micronaut/docs/rejection/MyRejectionHandler.java
- `M` security-session/src/test/groovy/io/micronaut/docs/security/session/HomeController.groovy
- `M` security-session/src/test/groovy/io/micronaut/docs/security/session/SessionAuthenticationNoRedirectSpec.groovy
- `M` security/src/test/groovy/io/micronaut/docs/security/authentication/UserController.groovy
- `M` security/src/test/groovy/io/micronaut/docs/security/authorization/X509AuthenticationFetcher.java
- `M` security/src/test/groovy/io/micronaut/docs/security/principalparam/UserController.groovy
- `M` security/src/test/groovy/io/micronaut/docs/security/securityRule/IpPatternSpec.groovy
- `M` security/src/test/groovy/io/micronaut/docs/security/token/basicauth/BasicAuthSpec.groovy
- `M` src/main/docs/guide/authenticationStrategies/custom.adoc
- `M` src/main/docs/guide/authenticationStrategies/jwt.adoc
- `A` src/main/docs/guide/authenticationStrategies/jwt/jwtEncryption/jwtEncryptionSecret.adoc
- `M` src/main/docs/guide/authenticationStrategies/jwt/jwtValidation/jwks.adoc
- `M` src/main/docs/guide/authenticationStrategies/session.adoc
- `M` src/main/docs/guide/breaks.adoc
- `M` src/main/docs/guide/retrievingAuthenticatedUser/securityService.adoc
- `A` src/main/docs/guide/retrievingAuthenticatedUser/websocket.adoc
- `M` src/main/docs/guide/security-installation.adoc
- `M` src/main/docs/guide/securityFilter/securityRule/secured/jakartaAnnotations.adoc
- `M` src/main/docs/guide/toc.yml
- `M` src/main/docs/guide/tokenPropagation.adoc
- `M` test-suite-groovy/src/test/groovy/io/micronaut/security/audit/docs/createdby/Book.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/security/docs/blockingauthenticationprovider/CustomAuthenticationProvider.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/security/docs/managementendpoints/SensitiveEndpointRuleReplacement.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/security/docs/reactiveauthenticationprovider/CustomAuthenticationProvider.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/security/docs/sensitiveendpointrule/SensitiveEndpointRuleReplacement.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/security/oauth2/docs/endpoint/CsrfFilterSpec.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/security/oauth2/docs/github/GithubAuthenticationMapper.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/security/oauth2/docs/github/GithubUser.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/security/oauth2/docs/openid/GlobalOpenIdAuthenticationMapper.groovy
- `M` test-suite-groovy/src/test/groovy/io/micronaut/security/oauth2/docs/openid/OktaAuthenticationMapper.groovy
- `M` test-suite-keycloak-docker/build.gradle
- `M` test-suite-keycloak-docker/src/main/java/io/micronaut/security/oauth2/keycloak/docker/Keycloak.java
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/security/audit/docs/createdby/UserAuditingTest.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/security/audit/docs/customconverter/CustomPrincipalConverterTest.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/security/docs/customauthentication/CustomAuthenticationTest.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/security/docs/managementendpoints/LoggersTest.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/security/docs/reactiveauthenticationprovider/CustomAuthenticationProvider.kt
- `M` test-suite-kotlin/src/test/kotlin/io/micronaut/security/oauth2/docs/github/GithubUser.kt
- `M` test-suite/src/test/java/io/micronaut/security/audit/docs/createdby/Book.java
- `M` test-suite/src/test/java/io/micronaut/security/docs/managementendpoints/SensitiveEndpointRuleReplacement.java
- `M` test-suite/src/test/java/io/micronaut/security/docs/sensitiveendpointrule/SensitiveEndpointRuleReplacement.java
- `M` test-suite/src/test/java/io/micronaut/security/oauth2/docs/github/GithubAuthenticationMapper.java
- `M` test-suite/src/test/java/io/micronaut/security/oauth2/docs/github/GithubUser.java
- `M` test-suite/src/test/java/io/micronaut/security/oauth2/docs/openid/GlobalOpenIdAuthenticationMapper.java
- `M` test-suite/src/test/java/io/micronaut/security/oauth2/docs/openid/OktaAuthenticationMapper.java

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
- `M` .github/workflows/aot.yml
- `M` .github/workflows/central-sync.yml
- `M` .github/workflows/graalvm-dev.yml
- `M` .github/workflows/publish-snapshot.yml
- `A` .github/workflows/sonatype.yml
- `M` .gitignore
- `A` .sdkmanrc
- `M` MAINTAINING.md
- `M` config/accepted-api-changes.json
- `M` config/checkstyle/checkstyle.xml
- `M` security-annotations/src/main/java/io/micronaut/security/annotation/CreatedBy.java
- `D` security-annotations/src/main/resources/META-INF/services/io.micronaut.inject.annotation.AnnotationMapper
- `M` security-aot/src/main/java/io/micronaut/security/aot/AOTContextUtils.java
- `M` security-aot/src/main/java/io/micronaut/security/aot/GeneratedFile.java
- `M` security-aot/src/main/java/io/micronaut/security/aot/JwksFetcherCodeGenerator.java
- `M` security-aot/src/main/java/io/micronaut/security/aot/OpenIdProviderMetadataFetcherCodeGenerator.java
- `M` security-csrf/src/main/java/io/micronaut/security/csrf/CsrfConfiguration.java
- `M` security-csrf/src/main/java/io/micronaut/security/csrf/CsrfConfigurationProperties.java
- `M` security-csrf/src/main/java/io/micronaut/security/csrf/filter/CsrfFilter.java
- `M` security-csrf/src/main/java/io/micronaut/security/csrf/filter/CsrfFilterConfiguration.java
- `M` security-csrf/src/main/java/io/micronaut/security/csrf/filter/CsrfFilterConfigurationProperties.java
- `M` security-csrf/src/main/java/io/micronaut/security/csrf/generator/CsrfHmacTokenGenerator.java
- `M` security-csrf/src/main/java/io/micronaut/security/csrf/generator/CsrfTokenGenerator.java
- `M` security-csrf/src/main/java/io/micronaut/security/csrf/generator/DefaultCsrfTokenGenerator.java
- `M` security-csrf/src/main/java/io/micronaut/security/csrf/repository/CompositeCsrfTokenRepository.java
- `M` security-csrf/src/main/java/io/micronaut/security/csrf/repository/CookieCsrfTokenRepository.java
- `M` security-csrf/src/main/java/io/micronaut/security/csrf/repository/CsrfLoginCookieProvider.java
- `M` security-csrf/src/main/java/io/micronaut/security/csrf/repository/CsrfTokenRepository.java
- `M` security-csrf/src/main/java/io/micronaut/security/csrf/resolver/CsrfTokenResolver.java
- `M` security-csrf/src/main/java/io/micronaut/security/csrf/resolver/FieldCsrfTokenResolver.java
- `M` security-csrf/src/main/java/io/micronaut/security/csrf/resolver/FutureCsrfTokenResolver.java
- `M` security-csrf/src/main/java/io/micronaut/security/csrf/resolver/FutureCsrfTokenResolverAdapter.java
- `M` security-csrf/src/main/java/io/micronaut/security/csrf/resolver/HttpHeaderCsrfTokenResolver.java
- `M` security-csrf/src/main/java/io/micronaut/security/csrf/session/SessionCsrfTokenRepository.java
- `M` security-csrf/src/main/java/io/micronaut/security/csrf/validator/CsrfTokenValidator.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/encryption/ec/ECEncryption.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/encryption/rsa/RSAEncryption.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/encryption/secret/SecretEncryption.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/encryption/secret/SecretEncryptionConfiguration.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/endpoints/KeysControllerConfigurationProperties.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/generator/JwtTokenGenerator.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/generator/RefreshTokenConfiguration.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/generator/RefreshTokenConfigurationProperties.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/generator/SignedRefreshTokenGenerator.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/generator/claims/JWTClaimsSetGenerator.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/generator/claims/JwtClaimsSetAdapter.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/nimbus/NimbusJsonWebTokenEncryption.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/nimbus/NimbusJsonWebTokenParser.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/nimbus/NimbusJsonWebTokenSignatureValidator.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/nimbus/NimbusJsonWebTokenValidator.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/nimbus/NimbusReactiveJsonWebTokenSignatureValidator.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/nimbus/NimbusReactiveJsonWebTokenValidator.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/nimbus/NimbusReactiveSignatureConfigurationAdapter.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/signature/ReactiveSignatureConfiguration.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/signature/ec/ECSignatureGenerator.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/signature/ec/ECSignatureGeneratorConfiguration.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/signature/jwks/DefaultJwkSetFetcher.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/signature/jwks/HttpClientJwksClient.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/signature/jwks/JwkSetFetcher.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/signature/jwks/JwksCache.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/signature/jwks/JwksClient.java
- `A` security-jwt/src/main/java/io/micronaut/security/token/jwt/signature/jwks/JwksClientReactorContext.java
- `D` security-jwt/src/main/java/io/micronaut/security/token/jwt/signature/jwks/JwksSignature.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/signature/jwks/JwksSignatureConfiguration.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/signature/jwks/JwksSignatureConfigurationProperties.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/signature/jwks/JwksSignatureUtils.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/signature/jwks/ReactorCacheJwkSetFetcher.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/signature/jwks/StaticJwksSignature.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/signature/jwks/StaticJwksSignatureConfiguration.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/signature/jwks/StaticJwksSignatureConfigurationProperties.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/signature/rsa/RSASignature.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/signature/rsa/RSASignatureGenerator.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/signature/secret/SecretSignatureConfiguration.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/validator/AudienceJwtClaimsValidator.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/validator/AuthenticationJWTClaimsSetAdapter.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/validator/DefaultJwtAuthenticationFactory.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/validator/ExpirationJwtClaimsValidator.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/validator/GenericJwtClaimsValidator.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/validator/IssuerJwtClaimsValidator.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/validator/JsonWebTokenEncryption.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/validator/JsonWebTokenIdSessionIdResolver.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/validator/JsonWebTokenParser.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/validator/JsonWebTokenSignatureValidator.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/validator/JsonWebTokenValidator.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/validator/JwtClaimsValidator.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/validator/JwtClaimsValidatorConfiguration.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/validator/JwtClaimsValidatorConfigurationProperties.java
- `D` security-jwt/src/main/java/io/micronaut/security/token/jwt/validator/JwtTokenValidator.java
- `D` security-jwt/src/main/java/io/micronaut/security/token/jwt/validator/JwtValidator.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/validator/NotBeforeJwtClaimsValidator.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/validator/ReactiveJsonWebTokenSignatureValidator.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/validator/ReactiveJsonWebTokenValidator.java
- `M` security-jwt/src/main/java/io/micronaut/security/token/jwt/validator/SubjectNotNullJwtClaimsValidator.java
- `M` security-ldap/src/main/java/io/micronaut/security/ldap/LdapAuthenticationProvider.java
- `M` security-ldap/src/main/java/io/micronaut/security/ldap/context/ContextBuilder.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/DefaultProviderResolver.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/client/DefaultOauthClient.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/client/DefaultOpenIdClient.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/client/DefaultOpenIdProviderMetadata.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/client/DefaultOpenIdProviderMetadataFetcher.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/client/IdTokenClaimsValidator.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/client/OpenIdClientFactory.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/client/OpenIdProviderMetadata.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/client/OpenIdProviderMetadataFetcher.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/client/OpenIdProviderMetadataFetcherFactory.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/client/clientcredentials/AbstractClientCredentialsClient.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/client/clientcredentials/ClientCredentialsClient.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/client/clientcredentials/ClientCredentialsConfiguration.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/client/clientcredentials/ClientCredentialsFactory.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/client/clientcredentials/DefaultClientCredentialsClient.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/client/clientcredentials/DefaultClientCredentialsOpenIdClient.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/client/clientcredentials/propagation/ClientCredentialsHeaderTokenPropagator.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/client/clientcredentials/propagation/ClientCredentialsHttpClientFilter.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/client/clientcredentials/propagation/ClientCredentialsTokenPropagator.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/client/condition/AbstractCondition.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/client/condition/OauthClientCondition.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/configuration/OauthClientConfiguration.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/configuration/OauthClientConfigurationProperties.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/configuration/OauthConfiguration.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/configuration/OauthConfigurationProperties.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/configuration/OpenIdClientConfiguration.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/configuration/endpoints/AuthorizationEndpointConfiguration.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/configuration/endpoints/DefaultSecureEndpointConfiguration.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/configuration/endpoints/EndSessionConfiguration.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/configuration/endpoints/OauthAuthorizationEndpointConfiguration.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/configuration/endpoints/SecureEndpointConfiguration.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/configuration/endpoints/TokenEndpointConfiguration.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/AbstractCookieConfiguration.java
- `D` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/AuthenticationMethod.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/DefaultSecureEndpoint.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/Endpoint.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/PersistableConfiguration.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/SecureEndpoint.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/CookiePersistence.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/pkce/CodeVerifierGenerator.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/pkce/DefaultCodeVerifierGenerator.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/pkce/DefaultPkceFactory.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/pkce/Pkce.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/pkce/PkceChallenge.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/pkce/PkceFactory.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/pkce/PkceGenerator.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/pkce/PlainPkceGenerator.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/pkce/S256PkceGenerator.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/pkce/persistence/PkcePersistence.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/pkce/persistence/cookie/CookiePkcePersistence.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/pkce/persistence/cookie/CookiePkcePersistenceConfiguration.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/pkce/persistence/session/SessionPkcePersistence.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/request/AuthorizationRequest.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/request/DefaultAuthorizationRedirectHandler.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/request/DefaultOauthAuthorizationRequest.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/request/DefaultOpenIdAuthorizationRequest.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/request/IdTokenHintResolver.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/request/LoginHintResolver.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/response/AbstractAuthorizationResponse.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/response/AuthorizationErrorResponse.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/response/AuthorizationErrorResponseExceptionHandler.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/response/AuthorizationResponse.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/response/DefaultAuthorizationErrorResponse.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/response/DefaultOauthAuthorizationResponseHandler.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/response/DefaultOpenIdAuthorizationResponse.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/response/DefaultOpenIdAuthorizationResponseHandler.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/response/OpenIdAuthorizationResponse.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/response/OpenIdAuthorizationResponseHandler.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/response/StateAware.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/response/StateAwareAuthorizationCallback.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/state/DefaultState.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/state/DefaultStateFactory.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/state/JacksonStateSerDes.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/state/State.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/state/StateFactory.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/state/StateSerDes.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/state/persistence/cookie/CookieStatePersistence.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/state/persistence/cookie/CookieStatePersistenceConfiguration.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/state/validation/DefaultStateValidator.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/authorization/state/validation/StateValidator.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/endsession/request/AbstractEndSessionRequest.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/endsession/request/AuthorizationServer.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/endsession/request/AuthorizationServerResolver.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/endsession/request/DefaultAuthorizationServerResolver.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/endsession/request/EndSessionEndpoint.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/endsession/request/EndSessionEndpointResolver.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/endsession/request/KeycloakEndSessionEndpoint.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/nonce/DefaultNonceFactory.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/nonce/NonceFactory.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/nonce/persistence/cookie/CookieNoncePersistence.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/nonce/persistence/cookie/CookieNoncePersistenceConfiguration.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/token/request/DefaultTokenEndpointClient.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/token/request/TokenEndpointClient.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/token/request/context/OauthCodeTokenRequestContext.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/token/request/context/OpenIdCodeTokenRequestContext.java
- `D` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/token/request/password/OauthPasswordAuthenticationProvider.java
- `D` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/token/request/password/OpenIdPasswordAuthenticationProvider.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/token/request/password/PasswordGrantCondition.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/token/request/password/PasswordGrantFactory.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/token/response/Address.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/token/response/DefaultOpenIdAuthenticationMapper.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/token/response/IdTokenLoginHandler.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/token/response/JWTOpenIdClaims.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/token/response/OauthAuthenticationMapper.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/token/response/OpenIdAuthenticationMapper.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/token/response/OpenIdClaims.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/token/response/OpenIdTokenResponse.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/token/response/TokenErrorResponse.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/token/response/TokenResponse.java
- `D` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/token/response/validation/DefaultOpenIdTokenResponseValidator.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/token/response/validation/DefaultReactiveOpenIdTokenResponseValidator.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/token/response/validation/NonceClaimValidator.java
- `D` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/token/response/validation/OpenIdTokenResponseValidator.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/token/response/validation/ReactiveOpenIdTokenResponseValidator.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/userinfo/UserInfoClientFactory.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/userinfo/UserInfoClientTokenValidator.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/endpoint/userinfo/UserInfoClientTokenValidatorConfiguration.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/grants/AbstractClientSecureGrant.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/grants/AsMap.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/grants/AuthorizationCodeGrant.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/grants/ClientCredentialsGrant.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/grants/JwtBearerAssertionGrant.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/grants/PasswordGrant.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/grants/RefreshTokenGrant.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/grants/SamlBearerAssertionGrant.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/metadata/DefaultProtectedResourceMetadataProvider.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/metadata/ProtectedResourceMetadata.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/metadata/ProtectedResourceMetadataController.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/metadata/ProtectedResourceMetadataProvider.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/metadata/ResourceMetadataWwwAuthenticateChallengeProvider.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/proxy/WellKnownProxyFilter.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/proxy/WellKnownProxyFilterCondition.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/proxy/WellKnownProxySecurityRule.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/proxy/WellKnownProxySettings.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/routes/DefaultEndSessionController.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/routes/DefaultOauthController.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/url/AbsoluteUrlBuilder.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/url/DefaultOauthRouteUrlBuilder.java
- `M` security-oauth2/src/main/java/io/micronaut/security/oauth2/url/OauthRouteUrlBuilder.java
- `R092` security-processor/src/main/java/io/micronaut/security/processor/JakartaDenyAllAnnotationMapper.java
- `R092` security-processor/src/main/java/io/micronaut/security/processor/JakartaPermitAllAnnotationMapper.java
- `R092` security-processor/src/main/java/io/micronaut/security/processor/JakartaRolesAllowedAnnotationMapper.java
- `A` security-processor/src/main/java/io/micronaut/security/processor/package-info.java
- `A` security-processor/src/main/resources/META-INF/services/io.micronaut.inject.annotation.AnnotationMapper
- `M` security-session/src/main/java/io/micronaut/security/session/DefaultSessionPopulator.java
- `M` security-session/src/main/java/io/micronaut/security/session/HttpSessionSessionIdResolver.java
- `M` security-session/src/main/java/io/micronaut/security/session/SessionLoginHandler.java
- `M` security-session/src/main/java/io/micronaut/security/session/SessionLogoutHandler.java
- `M` security-session/src/main/java/io/micronaut/security/session/SessionPopulator.java
- `M` security/src/main/java/io/micronaut/security/audit/UserAuditingEntityEventListener.java
- `M` security/src/main/java/io/micronaut/security/authentication/AbstractPrincipalArgumentBinder.java
- `M` security/src/main/java/io/micronaut/security/authentication/Authentication.java
- `M` security/src/main/java/io/micronaut/security/authentication/AuthenticationException.java
- `M` security/src/main/java/io/micronaut/security/authentication/AuthenticationMode.java
- `D` security/src/main/java/io/micronaut/security/authentication/AuthenticationProvider.java
- `M` security/src/main/java/io/micronaut/security/authentication/AuthenticationProviderAdapter.java
- `M` security/src/main/java/io/micronaut/security/authentication/AuthenticationResponse.java
- `M` security/src/main/java/io/micronaut/security/authentication/Authenticator.java
- `M` security/src/main/java/io/micronaut/security/authentication/AuthenticatorCondition.java
- `M` security/src/main/java/io/micronaut/security/authentication/AuthorizationException.java
- `M` security/src/main/java/io/micronaut/security/authentication/BasicAuthUtils.java
- `M` security/src/main/java/io/micronaut/security/authentication/BasicAuthWwwAuthenticateChallengeProvider.java
- `M` security/src/main/java/io/micronaut/security/authentication/ClientAuthentication.java
- `M` security/src/main/java/io/micronaut/security/authentication/DefaultAuthorizationExceptionHandler.java
- `M` security/src/main/java/io/micronaut/security/authentication/ServerAuthentication.java
- `M` security/src/main/java/io/micronaut/security/authentication/UsernamePasswordCredentials.java
- `M` security/src/main/java/io/micronaut/security/authentication/WwwAuthenticateChallenge.java
- `M` security/src/main/java/io/micronaut/security/authentication/WwwAuthenticateChallengeProvider.java
- `M` security/src/main/java/io/micronaut/security/authentication/provider/AuthenticationProvider.java
- `M` security/src/main/java/io/micronaut/security/authentication/provider/ReactiveAuthenticationProvider.java
- `D` security/src/main/java/io/micronaut/security/authentication/provider/ReactiveAuthenticationProviderAdapter.java
- `M` security/src/main/java/io/micronaut/security/config/AuthenticationModeConfiguration.java
- `M` security/src/main/java/io/micronaut/security/config/DefaultInterceptUrlPatternModifier.java
- `M` security/src/main/java/io/micronaut/security/config/DefaultRedirectService.java
- `M` security/src/main/java/io/micronaut/security/config/ForbiddenRedirectConfiguration.java
- `M` security/src/main/java/io/micronaut/security/config/InterceptUrlMapPattern.java
- `M` security/src/main/java/io/micronaut/security/config/InterceptUrlPatternModifier.java
- `M` security/src/main/java/io/micronaut/security/config/RedirectConfiguration.java
- `M` security/src/main/java/io/micronaut/security/config/RedirectConfigurationProperties.java
- `M` security/src/main/java/io/micronaut/security/config/RedirectService.java
- `M` security/src/main/java/io/micronaut/security/config/RefreshRedirectConfiguration.java
- `M` security/src/main/java/io/micronaut/security/config/SecurityConfigurationProperties.java
- `M` security/src/main/java/io/micronaut/security/config/ServerContextPathProviderUtils.java
- `M` security/src/main/java/io/micronaut/security/config/UnauthorizedRedirectConfiguration.java
- `A` security/src/main/java/io/micronaut/security/context/MutableAttributeHolderSecurityContext.java
- `A` security/src/main/java/io/micronaut/security/context/SecurityContext.java
- `A` security/src/main/java/io/micronaut/security/context/SecurityContextHolder.java
- `A` security/src/main/java/io/micronaut/security/context/SecurityContextSupplier.java
- `A` security/src/main/java/io/micronaut/security/context/ServerRequestContextSecurityContextSupplier.java
- `A` security/src/main/java/io/micronaut/security/context/package-info.java
- `M` security/src/main/java/io/micronaut/security/endpoints/ControllerConfiguration.java
- `M` security/src/main/java/io/micronaut/security/endpoints/ControllerConfigurationProperties.java
- `M` security/src/main/java/io/micronaut/security/endpoints/LoginController.java
- `M` security/src/main/java/io/micronaut/security/endpoints/LogoutController.java
- `M` security/src/main/java/io/micronaut/security/endpoints/OauthController.java
- `M` security/src/main/java/io/micronaut/security/endpoints/TokenRefreshRequest.java
- `M` security/src/main/java/io/micronaut/security/errors/CookiePriorToLoginPersistence.java
- `M` security/src/main/java/io/micronaut/security/errors/ErrorResponse.java
- `M` security/src/main/java/io/micronaut/security/errors/OauthErrorResponseException.java
- `M` security/src/main/java/io/micronaut/security/event/LoginFailedEvent.java
- `M` security/src/main/java/io/micronaut/security/event/LoginSuccessfulEvent.java
- `M` security/src/main/java/io/micronaut/security/event/LogoutEvent.java
- `M` security/src/main/java/io/micronaut/security/event/SecurityEvent.java
- `M` security/src/main/java/io/micronaut/security/event/TokenValidatedEvent.java
- `M` security/src/main/java/io/micronaut/security/expressions/SecuredEvaluationContext.java
- `M` security/src/main/java/io/micronaut/security/filters/SecurityFilter.java
- `M` security/src/main/java/io/micronaut/security/filters/SecurityFilterConfiguration.java
- `M` security/src/main/java/io/micronaut/security/filters/SecurityFilterConfigurationProperties.java
- `M` security/src/main/java/io/micronaut/security/rules/InterceptUrlMapRule.java
- `M` security/src/main/java/io/micronaut/security/rules/IpPatternsRule.java
- `M` security/src/main/java/io/micronaut/security/rules/SecuredAnnotationRule.java
- `M` security/src/main/java/io/micronaut/security/rules/SecurityRule.java
- `M` security/src/main/java/io/micronaut/security/rules/SensitiveEndpointRule.java
- `M` security/src/main/java/io/micronaut/security/session/CompositeSessionIdResolver.java
- `M` security/src/main/java/io/micronaut/security/session/SessionIdResolver.java
- `M` security/src/main/java/io/micronaut/security/token/AbstractTokenAuthenticationFactory.java
- `M` security/src/main/java/io/micronaut/security/token/Claims.java
- `M` security/src/main/java/io/micronaut/security/token/ClaimsUtils.java
- `M` security/src/main/java/io/micronaut/security/token/DefaultRolesFinder.java
- `M` security/src/main/java/io/micronaut/security/token/MapClaims.java
- `M` security/src/main/java/io/micronaut/security/token/RolesFinder.java
- `M` security/src/main/java/io/micronaut/security/token/TokenAuthenticationFetcher.java
- `M` security/src/main/java/io/micronaut/security/token/config/TokenConfiguration.java
- `M` security/src/main/java/io/micronaut/security/token/config/TokenConfigurationProperties.java
- `M` security/src/main/java/io/micronaut/security/token/cookie/AbstractAccessTokenCookieConfigurationProperties.java
- `M` security/src/main/java/io/micronaut/security/token/cookie/CookieLoginHandler.java
- `M` security/src/main/java/io/micronaut/security/token/cookie/LoginCookieProvider.java
- `M` security/src/main/java/io/micronaut/security/token/cookie/RefreshTokenCookieConfigurationProperties.java
- `M` security/src/main/java/io/micronaut/security/token/cookie/TokenCookieClearerLogoutHandler.java
- `M` security/src/main/java/io/micronaut/security/token/cookie/TokenCookieConfigurationProperties.java
- `M` security/src/main/java/io/micronaut/security/token/cookie/TokenCookieLoginHandler.java
- `M` security/src/main/java/io/micronaut/security/token/generator/AccessRefreshTokenGenerator.java
- `M` security/src/main/java/io/micronaut/security/token/generator/AccessTokenConfiguration.java
- `M` security/src/main/java/io/micronaut/security/token/generator/AccessTokenConfigurationProperties.java
- `M` security/src/main/java/io/micronaut/security/token/generator/DefaultAccessRefreshTokenGenerator.java
- `M` security/src/main/java/io/micronaut/security/token/generator/RefreshTokenGenerator.java
- `M` security/src/main/java/io/micronaut/security/token/generator/TokenGenerator.java
- `M` security/src/main/java/io/micronaut/security/token/propagation/AbstractOutgoingRequestProcessorMatcher.java
- `M` security/src/main/java/io/micronaut/security/token/reader/DefaultTokenResolver.java
- `M` security/src/main/java/io/micronaut/security/token/reader/TokenResolver.java
- `M` security/src/main/java/io/micronaut/security/token/render/AccessRefreshToken.java
- `M` security/src/main/java/io/micronaut/security/token/render/BearerAccessRefreshToken.java
- `M` security/src/main/java/io/micronaut/security/token/render/BearerTokenRenderer.java
- `M` security/src/main/java/io/micronaut/security/token/render/TokenRenderer.java
- `M` security/src/main/java/io/micronaut/security/token/validator/RefreshTokenValidator.java
- `M` security/src/main/java/io/micronaut/security/token/validator/TokenValidator.java
- `M` security/src/main/java/io/micronaut/security/utils/DefaultSecurityService.java
- `M` security/src/main/java/io/micronaut/security/utils/HMacUtils.java
- `M` security/src/main/java/io/micronaut/security/utils/QualifierUtils.java
- `A` security/src/main/java/io/micronaut/security/utils/SecurityBindingResultUtils.java
- `A` security/src/main/java/io/micronaut/security/websockets/AuthenticationWebSocketStateBinder.java
- `A` security/src/main/java/io/micronaut/security/websockets/package-info.java
- `M` security/src/main/java/io/micronaut/security/x509/X509Authentication.java
- `M` security/src/main/java/io/micronaut/security/x509/X509AuthenticationFetcher.java
- `M` security/src/main/java/io/micronaut/security/x509/X509Configuration.java
- `M` security/src/main/java/io/micronaut/security/x509/X509ConfigurationProperties.java
- `M` security/src/main/resources/META-INF/native-image/io.micronaut.security/micronaut-security/native-image.properties

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` security-csrf/src/test/java/io/micronaut/security/csrf/filter/CsrfFilterTest.java
- `M` security-csrf/src/test/java/io/micronaut/security/csrf/generator/CsrfDoubleSubmitCookiePatternTest.java
- `M` security-csrf/src/test/java/io/micronaut/security/csrf/generator/CsrfDoubleSubmitCookiePatternWithHeaderTest.java
- `M` security-csrf/src/test/java/io/micronaut/security/csrf/resolver/FieldCsrfTokenResolverTest.java
- `M` security-jwt/src/test/groovy/io/micronaut/security/SensitiveEndpointRuleReplacement.groovy
- `M` security-jwt/src/test/groovy/io/micronaut/security/authentication/provider/HttpRequestAuthenticationProviderAuthenticationExceptionSpec.groovy
- `M` security-jwt/src/test/groovy/io/micronaut/security/authentication/provider/HttpRequestAuthenticationProviderAuthenticationResponseFailureSpec.groovy
- `M` security-jwt/src/test/groovy/io/micronaut/security/authentication/provider/MultipleAuthenticationProviderAuthenticationResponseFailureSpec.groovy
- `M` security-jwt/src/test/groovy/io/micronaut/security/token/jwt/cookie/JwtCookieAuthenticationNoRedirectSpec.groovy
- `M` security-jwt/src/test/groovy/io/micronaut/security/token/jwt/cookie/JwtCookiePathAndDomainSpec.groovy
- `M` security-jwt/src/test/groovy/io/micronaut/security/token/jwt/encryption/secret/SecretEncryptionSpec.groovy
- `M` security-jwt/src/test/groovy/io/micronaut/security/token/jwt/roles/CustomRolesParser.groovy
- `M` security-jwt/src/test/groovy/io/micronaut/security/token/jwt/signature/ec/TestECSignatureGeneratorConfigurationWithKid.java
- `A` security-jwt/src/test/groovy/io/micronaut/security/token/jwt/signature/jwks/JwksReadTimeoutUnusedSourcesLoggingSpec.groovy
- `M` security-jwt/src/test/groovy/io/micronaut/security/token/jwt/validator/AudienceJwtClaimsValidatorSpec.groovy
- `M` security-jwt/src/test/groovy/io/micronaut/security/token/jwt/validator/IssuerJwtClaimsValidatorSpec.groovy
- `M` security-jwt/src/test/groovy/io/micronaut/security/token/jwt/validator/JwtClaimsValidatorRequestPassedSpec.groovy
- `M` security-jwt/src/test/groovy/io/micronaut/security/token/jwt/validator/NotBeforeJwtClaimsValidatorSpec.groovy
- `M` security-jwt/src/test/groovy/io/micronaut/security/token/validator/TokenValidatorSpec.groovy
- `M` security-jwt/src/test/groovy/io/micronaut/security/token/websockets/EchoServerWebSocket.java
- `M` security-ldap/src/test/groovy/io/micronaut/security/ldap/InMemoryLdapSpec.groovy
- `M` security-ldap/src/test/groovy/io/micronaut/security/ldap/LdapAuthenticationSpec.groovy
- `M` security-ldap/src/test/groovy/io/micronaut/security/ldap/context/AttributesConvertibleValuesSpec.groovy
- `M` security-oauth2/src/test/groovy/io/micronaut/security/oauth2/DefaultProviderResolverSpec.groovy
- `M` security-oauth2/src/test/groovy/io/micronaut/security/oauth2/DefaultSecureEndpointTest.java
- `M` security-oauth2/src/test/groovy/io/micronaut/security/oauth2/client/DefaultOpenIdProviderMetadataSpec.groovy
- `M` security-oauth2/src/test/groovy/io/micronaut/security/oauth2/client/JwksUriSignatureProxySpec.groovy
- `M` security-oauth2/src/test/groovy/io/micronaut/security/oauth2/client/JwksUriSignatureSpec.groovy
- `M` security-oauth2/src/test/groovy/io/micronaut/security/oauth2/client/JwksUriSignatureTimeoutSpec.groovy
- `M` security-oauth2/src/test/groovy/io/micronaut/security/oauth2/client/OpenIdClientFactorySpec.groovy
- `M` security-oauth2/src/test/groovy/io/micronaut/security/oauth2/client/clientcredentials/ClientCredentialsConcurrentSpec.groovy
- `M` security-oauth2/src/test/groovy/io/micronaut/security/oauth2/client/clientcredentials/ClientCredentialsSpec.groovy
- `M` security-oauth2/src/test/groovy/io/micronaut/security/oauth2/client/condition/PasswordGrantConditionSpec.groovy
- `M` security-oauth2/src/test/groovy/io/micronaut/security/oauth2/endpoint/authorization/pkce/PkceCookieCodeChallengeNotSupportedSpec.groovy
- `M` security-oauth2/src/test/groovy/io/micronaut/security/oauth2/endpoint/authorization/pkce/PkceCookieWithPlainSpec.groovy
- `M` security-oauth2/src/test/groovy/io/micronaut/security/oauth2/endpoint/authorization/pkce/PkceCookieWithS256NoOpenIdNoChallengeMethodSpec.groovy
- `M` security-oauth2/src/test/groovy/io/micronaut/security/oauth2/endpoint/authorization/pkce/PkceCookieWithS256NoOpenIdSpec.groovy
- `M` security-oauth2/src/test/groovy/io/micronaut/security/oauth2/endpoint/authorization/pkce/PkceCookieWithS256Spec.groovy
- `M` security-oauth2/src/test/groovy/io/micronaut/security/oauth2/endpoint/authorization/pkce/PkceSessionWithS256Spec.groovy
- `M` security-oauth2/src/test/groovy/io/micronaut/security/oauth2/endpoint/authorization/request/OpenIdAuthorizationRedirectOauthDisabledSpec.groovy
- `M` security-oauth2/src/test/groovy/io/micronaut/security/oauth2/endpoint/authorization/request/OpenIdAuthorizationRedirectSpec.groovy
- `M` security-oauth2/src/test/groovy/io/micronaut/security/oauth2/endpoint/authorization/request/OpenIdAuthorizationRedirectWithJustOpenIdSpec.groovy
- `M` security-oauth2/src/test/groovy/io/micronaut/security/oauth2/endpoint/authorization/request/pkce/OpenIdAuthorizationPkceSpec.groovy
- `M` security-oauth2/src/test/groovy/io/micronaut/security/oauth2/endpoint/authorization/request/pkce/OpenIdAuthorizationRedirectPkceSpec.groovy
- `M` security-oauth2/src/test/groovy/io/micronaut/security/oauth2/endpoint/authorization/request/pkce/OpenIdAuthorizationRedirectWithJustOpenIdPkceSpec.groovy
- `M` security-oauth2/src/test/groovy/io/micronaut/security/oauth2/endpoint/endsession/request/KeycloakEndSessionEndpointSpec.groovy
- `M` security-oauth2/src/test/java/io/micronaut/security/oauth2/configuration/OauthClientConfigurationTest.java
- `M` security-oauth2/src/test/java/io/micronaut/security/oauth2/metadata/ProtectedResourceMetadataControllerTest.java
- `M` security-oauth2/src/test/java/io/micronaut/security/oauth2/metadata/ProtectedResourceMetadataProviderPathComponentTest.java
- `M` security-session/src/test/groovy/io/micronaut/security/handlers/LoginFailedHttpRequestAuthenticationProviderSpec.groovy
- `M` security-session/src/test/groovy/io/micronaut/security/handlers/LoginFailedHttpRequestExecutorAuthenticationProviderSpec.groovy
- `M` security-session/src/test/groovy/io/micronaut/security/handlers/LoginFailedHttpRequestReactiveAuthenticationProviderSpec.groovy
- `M` security/src/main/java/io/micronaut/security/endpoints/introspection/DefaultIntrospectionProcessor.java
- `M` security/src/main/java/io/micronaut/security/endpoints/introspection/IntrospectionConfiguration.java
- `M` security/src/main/java/io/micronaut/security/endpoints/introspection/IntrospectionConfigurationProperties.java
- `M` security/src/main/java/io/micronaut/security/endpoints/introspection/IntrospectionController.java
- `M` security/src/main/java/io/micronaut/security/endpoints/introspection/IntrospectionProcessor.java
- `M` security/src/main/java/io/micronaut/security/endpoints/introspection/IntrospectionRequest.java
- `M` security/src/main/java/io/micronaut/security/endpoints/introspection/IntrospectionResponse.java
- `M` security/src/test/groovy/io/micronaut/security/HealthSensitivitySpec.groovy
- `M` security/src/test/groovy/io/micronaut/security/audit/CreatedByUpdatedByPlusNullableSpec.groovy
- `M` security/src/test/groovy/io/micronaut/security/audit/CreatedByUpdatedByTypeNoConverterSpec.groovy
- `M` security/src/test/groovy/io/micronaut/security/audit/Message.groovy
- `M` security/src/test/groovy/io/micronaut/security/authentication/AuthenticationProviderSpec.groovy
- `M` security/src/test/groovy/io/micronaut/security/authentication/AuthenticatorAllImperativeSpec.groovy
- `M` security/src/test/groovy/io/micronaut/security/authentication/AuthenticatorImperativeSpec.groovy
- `M` security/src/test/groovy/io/micronaut/security/authentication/AuthenticatorSpec.groovy
- `D` security/src/test/groovy/io/micronaut/security/authentication/DeprecatedAuthenticationProviderStillWorksSpec.groovy
- `M` security/src/test/groovy/io/micronaut/security/authentication/provider/HttpRequestAuthenticationProviderSpec.groovy
- `M` security/src/test/groovy/io/micronaut/security/authentication/provider/HttpRequestReactiveAuthenticationProviderSpec.groovy
- `M` security/src/test/groovy/io/micronaut/security/authorization/AuthorizationSpec.groovy
- `M` security/src/test/groovy/io/micronaut/security/authorization/AuthorizationWithoutInterceptUrlMapSpec.groovy
- `M` security/src/test/groovy/io/micronaut/security/authorization/SecuredRolesCaseInsensitiveViaRolesFinderReplacementSpec.groovy
- `M` security/src/test/groovy/io/micronaut/security/endpoints/introspection/IntrospectionAuthorizerSpec.groovy
- `M` security/src/test/groovy/io/micronaut/security/endpoints/introspection/IntrospectionControllerPathConfigurableSpec.groovy
- `M` security/src/test/groovy/io/micronaut/security/endpoints/introspection/IntrospectionControllerSpec.groovy
- `M` security/src/test/groovy/io/micronaut/security/events/EventListenerSpec.groovy
- `M` security/src/test/groovy/io/micronaut/security/filters/SecurityFilterSpec.groovy
- `M` security/src/test/groovy/io/micronaut/security/propagation/TokenPropagationHttpClientFilterSpec.groovy
- `M` security/src/test/groovy/io/micronaut/security/rules/ConfigurationInterceptUrlMapRuleSpec.groovy
- `M` security/src/test/groovy/io/micronaut/security/rules/sensitive/EndpointWithPrincipalAndSensitivityOverrideSpec.groovy
- `M` security/src/test/groovy/io/micronaut/security/token/basicauth/BasicAuthSpec.groovy
- `M` security/src/test/groovy/io/micronaut/security/token/generator/RefreshTokenGeneratorSpec.groovy
- `M` security/src/test/groovy/io/micronaut/security/token/reader/DefaultTokenResolverSpec.groovy
- `D` security/src/test/groovy/io/micronaut/security/token/reader/TokenResolverSpec.groovy
- `M` security/src/test/groovy/io/micronaut/security/token/validator/RefreshTokenValidatorSpec.groovy
- `M` security/src/test/groovy/io/micronaut/security/utils/SecurityServiceSpec.groovy
- `M` security/src/test/java/io/micronaut/security/FailedAuthenticationScenario.java
- `M` security/src/test/java/io/micronaut/security/SuccessAuthenticationScenario.java
- `A` security/src/test/java/io/micronaut/security/config/RejectMethodNotAllowedTest.java
- `A` security/src/test/java/io/micronaut/security/context/MutableAttributeHolderSecurityContextTest.java
- `A` security/src/test/java/io/micronaut/security/context/SecurityContextHolderTest.java
- `M` security/src/test/java/io/micronaut/security/token/ClaimsUtilsTest.java
- `A` test-suite-aot-authserver/src/main/resources/application.properties
- `D` test-suite-aot-authserver/src/main/resources/application.yml
- `M` test-suite-aot/src/main/java/io/micronaut/security/test/aot/HomeController.java
- `A` test-suite-aot/src/main/resources/application.properties
- `D` test-suite-aot/src/main/resources/application.yml
- `M` test-suite-geb/src/test/groovy/io/micronaut/security/oauth2/e2e/AuthenticationModeIdTokenSpec.groovy
- `M` test-suite-geb/src/test/groovy/io/micronaut/security/oauth2/e2e/OpenIdAuthorizationCodeSpec.groovy
- `A` test-suite-geb/src/test/groovy/io/micronaut/security/pages/KeycloakLogoutConfirmPage.groovy
- `M` test-suite-geb/src/test/groovy/io/micronaut/security/session/HomeController.groovy
- `M` test-suite-geb/src/test/groovy/io/micronaut/security/token/jwt/cookie/JwtCookieAuthenticationSpec.groovy
- `M` test-suite-geb/src/test/groovy/io/micronaut/security/token/jwt/cookie/JwtCookiePriorLoginSpec.groovy
- `M` test-suite-geb/src/test/groovy/io/micronaut/security/token/jwt/cookie/JwtCookieRefreshSpec.groovy
- `M` test-suite-geb/src/test/groovy/io/micronaut/security/websockets/HomePageSpec.groovy
- `M` test-suite-geb/src/test/groovy/io/micronaut/security/websockets/WebsocketsHtmlProvider.groovy
- `A` test-suite-groovy/src/test/groovy/io/micronaut/security/websockets/AuthenticationWebSocketStateBinderSpec.groovy
- `M` test-suite-keycloak/src/main/java/io/micronaut/security/oauth2/keycloak/KeycloakAuthorizationRedirectHandler.java
- `D` test-suite-keycloak/src/main/java/io/micronaut/security/oauth2/keycloak/KeycloakEndSessionEndpoint.java
- `A` test-suite-kotlin/src/test/kotlin/io/micronaut/security/websocket/AuthenticationWebSocketStateBinderSpec.kt
- `M` test-suite-ldap/src/main/java/example/LdapController.java
- `A` test-suite-security-context/src/test/java/io/micronaut/security/context/CustomSecurityContext.java
- `A` test-suite-security-context/src/test/java/io/micronaut/security/context/CustomSecurityContextSupplier.java
- `A` test-suite-security-context/src/test/java/io/micronaut/security/context/SecurityContextSupplierSpiTest.java
- `A` test-suite-security-context/src/test/resources/META-INF/services/io.micronaut.security.context.SecurityContextSupplier
- `A` test-suite-security-context/src/test/resources/logback.xml
- `A` test-suite-security-service/src/test/java/io/micronaut/security/tests/MySQL.java
- `M` test-suite-security-service/src/test/java/io/micronaut/security/tests/TestSuiteSecurityServiceTest.java
- `A` test-suite-tomcat-groovy/src/test/resources/application-test.properties
- `A` test-suite-tomcat/src/test/resources/application-test.properties
- `M` test-suite-utils-security/src/main/java/io/micronaut/security/testutils/authprovider/FailedAuthenticationScenario.java
- `M` test-suite-utils-security/src/main/java/io/micronaut/security/testutils/authprovider/SuccessAuthenticationScenario.java
- `M` test-suite-utils/src/main/groovy/io/micronaut/security/testutils/ApplicationContextSpecification.groovy
- `M` test-suite-utils/src/main/groovy/io/micronaut/security/testutils/ConfigurationFixture.groovy
- `M` test-suite-utils/src/main/groovy/io/micronaut/security/testutils/EmbeddedServerSpecification.groovy
- `A` test-suite/src/test/java/io/micronaut/security/websocket/AuthenticationWebSocketStateBinderSpec.java

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

