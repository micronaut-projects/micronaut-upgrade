 Compared micronaut-aws as mn4 -> mn5.

  Scope

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-aws, branch 4.12.x, SHA ed71c74c9457
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-aws, branch 5.0.x, SHA c299c806d95a
  - Same remote, both clean: git@github.com:micronaut-projects/micronaut-aws.git
  - Report: /private/tmp/micronaut-aws-4.12-to-5.0-comparison.md

  Key Findings

  - Version line moves 4.12.0-SNAPSHOT -> 5.0.1-SNAPSHOT.
  - Baseline updates include Micronaut 4.10.15 -> 5.0.0, Gradle 8.14.3 -> 9.5.1, settings plugin 7.6.6 ->
    8.0.0-M18, Kotlin 1.9.25 -> 2.3.21, Graal SDK 23.1.8 -> 25.0.3, and new .sdkmanrc Java 25.0.1-graal.
  - AWS dependency updates include AWS SDK v2 2.41.30 -> 2.44.7, aws-lambda-java-serialization 1.2.0 ->
    1.4.0, and runtime interface client 2.9.0 -> 2.10.1.
  - Breaking change documented: deprecated io.micronaut.function.aws.proxy.MicronautLambdaHandler was
    removed. Replacements are the payload v1/v2 and ALB handler classes.
  - New micronaut.config.import support was added for AWS Parameter Store and Secrets Manager, including
    connection-string and structured declarations, credential/region options, retry options, and service
    loader registration.
  - Legacy bootstrap/context distributed configuration clients for Parameter Store and Secrets Manager are
    now deprecated, with migration docs pointing to micronaut.config.import.
  - Lambda API proxy handlers now clean up registered shutdown hooks when closed.
  - @MicronautLambdaTest adds deduceEnvironment, allowing Lambda tests to disable environment deduction.
  - Function client Lambda invocation code moved from JsonMediaTypeCodec to JsonMapper, with explicit
    encode/decode error wrapping and empty payload handling.
  - Docs were expanded for breaking changes, Parameter Store imports, Secrets Manager imports, and legacy
    search behavior.

  Diff size: 209 files changed, 6642 insertions(+), 571 deletions(-).

  I did not run tests; this was a folder comparison and targeted source/build-diff review only.

# Release Note Comparison

Generated: 2026-05-19 15:27 UTC
Comparison: `4.12.x` -> `5.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-aws` | `4.12.x` | `ed71c74c9457` | `git@github.com:micronaut-projects/micronaut-aws.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-aws` | `5.0.x` | `c299c806d95a` | `git@github.com:micronaut-projects/micronaut-aws.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-aws`
- Commit candidates found: 197
- File changes listed: 209
- Version values listed: 41
- File status counts: A=46, D=1, M=162

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `4.12.0-SNAPSHOT` | `5.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.gradle-kotlin` | `org.jetbrains.kotlin:kotlin-gradle-plugin:1.9.25` | `org.jetbrains.kotlin:kotlin-gradle-plugin:2.3.21` | `changed` |
| `gradle/libs.versions.toml` | `libraries.gradle-micronaut` | `io.micronaut.gradle:micronaut-gradle-plugin:4.6.1` | `io.micronaut.gradle:micronaut-gradle-plugin:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.javapoet` | `com.squareup:javapoet:1.13.0` | `com.squareup:javapoet:1.13.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.micronaut-discovery-client` | `io.micronaut.discovery:micronaut-discovery-client-bom:4.7.2` | `io.micronaut.discovery:micronaut-discovery-client-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-groovy` | `io.micronaut.groovy:micronaut-groovy-bom:4.7.0` | `io.micronaut.groovy:micronaut-groovy-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-mongodb` | `io.micronaut.mongodb:micronaut-mongo-bom:5.7.0` | `io.micronaut.mongodb:micronaut-mongo-bom:6.0.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-reactor` | `io.micronaut.reactor:micronaut-reactor-bom:3.9.1` | `io.micronaut.reactor:micronaut-reactor-bom:4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-security` | `io.micronaut.security:micronaut-security-bom:4.16.0` | `io.micronaut.security:micronaut-security-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.16.2` | `io.micronaut.serde:micronaut-serde-bom:3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-servlet` | `io.micronaut.servlet:micronaut-servlet-bom:5.6.0` | `io.micronaut.servlet:micronaut-servlet-bom:6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-resources` | `io.micronaut.testresources:micronaut-test-resources-bom:2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-validation` | `io.micronaut.validation:micronaut-validation-bom:4.12.0` | `io.micronaut.validation:micronaut-validation-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-views` | `io.micronaut.views:micronaut-views-bom:5.9.0` | `io.micronaut.views:micronaut-views-bom:6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.graal` | `23.1.8` | `25.0.3` | `changed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.29` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.javapoet` | `1.13.0` | `1.13.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.kotlin` | `1.9.25` | `2.3.21` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-alexa-ask-sdk` | `2.86.0` | `2.86.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.15` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-discovery` | `4.7.2` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.6.1` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-groovy` | `4.7.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.3` | `2.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-mongodb` | `5.7.0` | `6.0.1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-reactor` | `3.9.1` | `4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-security` | `4.16.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.16.2` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-servlet` | `5.6.0` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-starter` | `3.9.2` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.10.2` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test-resources` | `2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.12.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-views` | `5.9.0` | `6.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.servlet-api` | `2.5` | `2.5` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.slf4j` | `2.0.17` | `2.0.17` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |
| `settings.gradle.kts` | `plugin.io.micronaut.build.shared.settings` | `7.6.6` | `8.0.0-M18` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `10fcb4034978` remove spock version defined in Micronaut Build Gradle Plugin (Sergio del Amo, 2026-01-02)
- `f3c45fd0f084` Remove deprecated code for Micronaut Framework 5 and document breaking changes. (#2091) (Dean Wette, 2024-03-21)

### Features

- `8572cff6d5da` add deduceEnvironment (Sergio del Amo, 2026-04-17)
- `125afd8f2345` Add config import support for AWS Parameter Store and Secrets Manager (#2497) (Graeme Rocher, 2026-04-17)

### Fixes

- `172de8a376d4` fix(deps): update dependency com.amazonaws:aws-lambda-java-runtime-interface-client to v2.10.1 (#2492) (renovate[bot], 2026-04-17)
- `1537bc318789` fix(deps): update dependency com.amazonaws:aws-lambda-java-serialization to v1.3.1 (#2491) (renovate[bot], 2026-04-17)
- `b76a2cdb95a1` fix(deps): update aws-java-sdk-v2 monorepo to v2.42.29 (#2485) (renovate[bot], 2026-04-08)
- `dc903f54e101` fix(deps): update kotlin monorepo to v2.3.20 (#2490) (renovate[bot], 2026-04-08)
- `9e86d9d98bbf` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m6 (#2494) (renovate[bot], 2026-04-08)
- `432d1c58d5aa` fix(deps): update aws-java-sdk-v2 monorepo to v2.41.34 (#2483) (renovate[bot], 2026-02-22)
- `bad5faa3a884` fix(deps): update dependency io.micronaut.servlet:micronaut-servlet-bom to v6.0.0-m2 (#2482) (renovate[bot], 2026-02-21)
- `121bf35f5759` fix(deps): update aws-java-sdk-v2 monorepo to v2.41.33 (#2481) (renovate[bot], 2026-02-20)
- `acc4c79fd0fd` fix(deps): update dependency org.graalvm.sdk:graal-sdk to v25.0.2 (#2473) (renovate[bot], 2026-02-17)
- `f17a3e7ae476` fix(deps): update kotlin monorepo to v2.3.10 (#2477) (renovate[bot], 2026-02-17)
- `be049be5f186` fix(deps): update aws-java-sdk-v2 monorepo to v2.41.30 (#2463) (renovate[bot], 2026-02-17)
- `8a0a8bbffffb` fix(deps): update dependency com.amazonaws:aws-lambda-java-serialization to v1.2.0 (#2465) (renovate[bot], 2026-02-17)
- `6210bb0e94ea` fix(deps): update dependency com.amazonaws:aws-lambda-java-runtime-interface-client to v2.9.0 (#2466) (renovate[bot], 2026-02-17)
- `1b1470db263c` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.2 (#2476) (renovate[bot], 2026-02-17)
- `474fcbeb51b6` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m2 (#2470) (renovate[bot], 2026-02-17)
- `927e0be02a45` correct artifactid is testcontainers-junit-jupiter (Sergio del Amo, 2026-01-02)
- `0c53a1885820` correct artifact id is testcontainers-spock (Sergio del Amo, 2026-01-02)
- `97f45e8236af` fix(deps): update aws-java-sdk monorepo to v1.12.797 (#2453) (renovate[bot], 2026-01-02)
- `862fac92ea24` fix(deps): update aws-java-sdk-v2 monorepo to v2.41.0 (#2456) (renovate[bot], 2026-01-02)
- `0b5fec37e36b` fix(deps): update kotlin monorepo to v2.3.0 (#2457) (renovate[bot], 2026-01-02)
- `cb3220e7df6e` fix(deps): update dependency io.micronaut.security:micronaut-security-bom to v4.16.1 (#2460) (renovate[bot], 2026-01-02)
- `6e89e074b887` fix(deps): update aws-java-sdk-v2 monorepo to v2.40.5 (#2447) (renovate[bot], 2025-12-10)
- `2b102cf45075` fix(deps): update dependency io.micronaut.mongodb:micronaut-mongo-bom to v6 (#2449) (renovate[bot], 2025-12-10)
- `a9d745bd5ac8` fix(deps): update dependency org.graalvm.sdk:graal-sdk to v25 (#2450) (renovate[bot], 2025-12-10)
- `1ab03f807beb` fix(deps): update kotlin monorepo to v2.2.21 (#2419) (renovate[bot], 2025-12-10)
- `4a1f45f9f5fb` fix(deps): update dependency com.amazonaws:aws-lambda-java-core to v1.4.0 (#2439) (renovate[bot], 2025-12-02)
- `cf0659f0c3e7` fix(deps): update aws-java-sdk monorepo to v1.12.794 (#2438) (renovate[bot], 2025-12-02)
- `67f7060a721d` fix(deps): update aws-java-sdk-v2 monorepo to v2.39.6 (#2436) (renovate[bot], 2025-12-02)
- `21f76d51bcd2` fix(deps): update dependency io.micronaut.security:micronaut-security-bom to v4.16.0 (#2442) (renovate[bot], 2025-12-02)
- `a482dcc6ebe0` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#2435) (renovate[bot], 2025-12-02)
- `fb74f0a8a34d` fix(deps): update aws-java-sdk-v2 monorepo to v2.38.9 (#2412) (renovate[bot], 2025-11-19)
- `1c39e97e6d58` fix(deps): update aws-java-sdk monorepo to v1.12.793 (#2420) (renovate[bot], 2025-11-19)
- `bb8410b025cd` fix(deps): update dependency org.graalvm.sdk:graal-sdk to v24 (#2090) (renovate[bot], 2024-04-12)
- `2811093a58d7` fix(deps): update aws-java-sdk monorepo to v1.12.696 (#2102) (renovate[bot], 2024-04-06)
- `e7f3cef6ce0a` fix(deps): update aws-java-sdk monorepo to v1.12.693 (#2100) (renovate[bot], 2024-04-03)
- `650432328338` fix(deps): update dependency com.amazonaws:aws-lambda-java-runtime-interface-client to v2.5.0 (#2099) (renovate[bot], 2024-04-01)
- `08fccacb8ad9` fix(deps): update aws-java-sdk monorepo to v1.12.691 (#2098) (renovate[bot], 2024-04-01)
- `fe06c07a010d` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.3.5 (#2095) (renovate[bot], 2024-03-27)
- `7a35cf482f6e` fix(deps): update aws-java-sdk monorepo to v1.12.688 (#2094) (renovate[bot], 2024-03-27)
- `247f543c2361` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.8.2 (#2085) (renovate[bot], 2024-03-21)
- `7f55c1159bef` fix(deps): update dependency io.micronaut.security:micronaut-security-bom to v4.6.9 (#2081) (renovate[bot], 2024-03-21)
- `4b46b469abc4` fix(deps): update kotlin monorepo to v1.9.23 (#2083) (renovate[bot], 2024-03-21)
- `7fbc770ce13e` fix(deps): update aws-java-sdk monorepo to v1.12.683 (#2082) (renovate[bot], 2024-03-21)
- `0ba0c8a63363` fix(deps): update dependency com.amazonaws:aws-lambda-java-runtime-interface-client to v2.4.2 (#2072) (renovate[bot], 2024-03-08)
- `6e0f1836914d` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.3.4 (#2073) (renovate[bot], 2024-03-08)
- `c87f7953ae92` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.4.3 (#2074) (renovate[bot], 2024-03-08)
- `dfe032611ed3` fix(deps): update dependency io.micronaut.testresources:micronaut-test-resources-bom to v2.4.0 (#2076) (renovate[bot], 2024-03-08)
- `5e0105e436ac` fix(deps): update aws-java-sdk monorepo to v1.12.675 (#2069) (renovate[bot], 2024-03-08)
- `d654b61c9c02` fix(deps): update dependency org.eclipse.jetty:jetty-server to v12 (#1900) (renovate[bot], 2024-03-08)
- `55954aa8d4f8` fix(deps): update aws-java-sdk monorepo to v1.12.668 (#2066) (renovate[bot], 2024-02-28)
- `dabd26504275` fix(deps): update dependency io.micronaut.security:micronaut-security-bom to v4.6.6 (#2063) (renovate[bot], 2024-02-27)
- `e8451b17cdc9` fix(deps): update aws-java-sdk-v2 monorepo to v2.24.10 (#2046) (renovate[bot], 2024-02-26)

### Security

- `c9d062c6a1b4` micronaut-security = "5.0.0" (Sergio del Amo, 2026-05-18)
- `795e967f6ca0` security: upgrade versions of jackson and commons-io (Sergio del Amo, 2026-05-10)
- `5dbb71b5e61d` micronaut-security = "5.0.0-M2" (Sergio del Amo, 2026-04-20)
- `a015ed5c8e17` security = "5.0.0-M1" (Sergio del Amo, 2026-01-02)

### Dependency Updates

- `f1675c39a7ce` chore: Bump version to 5.0.1-SNAPSHOT (micronaut-build, 2026-05-18)
- `6bcb1d91e51f` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-05-10)
- `11e99c32ecb6` Update Micronaut dependencies (#2509) (renovate[bot], 2026-05-01)
- `2c7ba1ff7c67` Update dependency org.graalvm.sdk:graal-sdk to v25.0.3 (#2506) (renovate[bot], 2026-04-30)
- `c0fb6025590e` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-04-20)
- `ee1ae2d35ada` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-04-17)
- `8b2a24db93fe` chore(deps): update actions/cache digest to 27d5ce7 (#2500) (renovate[bot], 2026-04-17)
- `6b1330a35a7a` chore(deps): update gradle to v9.4.1 (#2488) (renovate[bot], 2026-04-08)
- `b576a3e22d53` chore(deps): update softprops/action-gh-release action to v2.6.1 (#2489) (renovate[bot], 2026-04-08)
- `88547dfbddc1` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-02-19)
- `de32490acbe3` build: JavaVersion 25 (Sergio del Amo, 2026-02-18)
- `9d381b3ce70e` chore(deps): update gradle to v9.3.1 (#2472) (renovate[bot], 2026-02-17)
- `fdfa9e015a10` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#2469) (renovate[bot], 2026-02-17)
- `0c63e0252718` chore(deps): update graalvm/setup-graalvm action to v1.4.5 (#2464) (renovate[bot], 2026-02-17)
- `0e2b49b2cbb5` Revert "chore(deps): update dependency commons-io:commons-io to v2.21.0 (#2429)" (Sergio del Amo, 2026-01-02)
- `a45e95d81f53` chore(deps): update dependency commons-io:commons-io to v2.21.0 (#2429) (renovate[bot], 2026-01-02)
- `d3d28603ed07` chore(deps): update dependency org.spockframework:spock-core to v2.4-groovy-5.0 (#2452) (renovate[bot], 2026-01-02)
- `79228753f973` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m13 (#2455) (renovate[bot], 2026-01-02)
- `d4021f63d088` chore(deps): update actions/cache action to v5 (#2458) (renovate[bot], 2026-01-02)
- `db1911ccda7c` chore(deps): update github artifact actions (#2459) (renovate[bot], 2026-01-02)
- `0e74bcb4d12d` chore(deps): update actions/checkout action to v6 (#2448) (renovate[bot], 2025-12-10)
- `202a071dde0d` chore(deps): update gradle to v9.2.1 (#2432) (renovate[bot], 2025-12-02)
- `6c516a3bdf41` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#2441) (renovate[bot], 2025-12-02)
- `7f2248374a51` chore(deps): update softprops/action-gh-release action to v2.5.0 (#2445) (renovate[bot], 2025-12-02)
- `6bc45247cd13` chore(deps): update graalvm/setup-graalvm action to v1.4.4 (#2440) (renovate[bot], 2025-12-02)
- `ca7bc66a5ff5` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m9 (#2425) (renovate[bot], 2025-11-19)
- `82ea48041cdc` chore(deps): update softprops/action-gh-release action to v2.4.2 (#2426) (renovate[bot], 2025-11-19)
- `fff8122f054d` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#2418) (renovate[bot], 2025-11-03)
- `bfbc352156b3` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m8 (#2417) (renovate[bot], 2025-11-03)
- `e651f9b70b95` chore(deps): update graalvm/setup-graalvm action to v1.2.1 (#2093) (renovate[bot], 2024-03-27)
- `5f9b93f5cd97` chore(deps): update dependency gradle to v8.7 (#2096) (renovate[bot], 2024-03-27)
- `0ef8a834bbe6` chore(deps): update graalvm/setup-graalvm action to v1.2.0 (#2084) (renovate[bot], 2024-03-21)
- `332a54f078b8` chore(deps): update plugin io.micronaut.build.shared.settings to v6.7.0 (#2088) (renovate[bot], 2024-03-21)
- `90425dabb72c` chore(deps): update plugin io.micronaut.build.shared.settings to v6.6.4 (#2071) (renovate[bot], 2024-03-08)
- `e08b69ea9e51` chore(deps): update graalvm/setup-graalvm action to v1.1.8 (#2068) (renovate[bot], 2024-03-08)

### Documentation

- `b3a8a2afa2ed` Docs: update micronaut-docs to 3.0.0 (#2410) (issam liqali, 2025-10-16)

### Internal

- `a9b0bf084012` test: enable CacheControlTest (Sergio del Amo, 2026-04-17)
- `77e2c6cc4085` ci: projectVersion=4.5.0-SNAPSHOT [ci skip] (Sergio del Amo, 2024-02-26)

### Review Candidates

- `c299c806d95a` micronaut-views = "6.0.0" (Sergio del Amo, 2026-05-19)
- `590ea098dd6d` Update common files (#2514) (micronaut-build, 2026-05-19)
- `e63571233d40` [skip ci] Release v5.0.0 (micronaut-build, 2026-05-18)
- `98df2c1f7f0d` del micronaut-starter (Sergio del Amo, 2026-05-18)
- `ac685894f8ab` del managed-aws-serverless-core (Sergio del Amo, 2026-05-18)
- `7acc1732faba` micronaut-gradle-plugin = "5.0.0-M1" (Sergio del Amo, 2026-05-18)
- `923e146e8abd` managed-aws-lambda-java-serialization = '1.4.0' (Sergio del Amo, 2026-05-18)
- `1adfd9e2f76b` managed-aws-java-sdk-v2 = '2.44.7' (Sergio del Amo, 2026-05-18)
- `174480fe6b2c` Update common files (#2513) (micronaut-build, 2026-05-18)
- `c524ee60bce5` micronaut-discovery = "5.0.0" (Sergio del Amo, 2026-05-18)
- `600bb64c0f25` micronaut-mongodb = "6.0.1" (Sergio del Amo, 2026-05-14)
- `a2f1b96e0117` micronaut-test = "5.0.0" (Sergio del Amo, 2026-05-14)
- `ef29b001f7cc` Update versions (Sergio del Amo, 2026-05-14)
- `0c5a4f378744` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `114f0ebd4b55` [skip ci] Release v5.0.0-RC1 (micronaut-build, 2026-05-10)
- `2eb1e24c616c` Clean up API proxy shutdown hooks on close (Sergio del Amo, 2026-05-10)
- `6ca3fe70165c` Allow disabling proxy test embedded server factory (Sergio del Amo, 2026-05-10)
- `008337b4c605` Skip Content-Length header in proxy test handler (Sergio del Amo, 2026-05-10)
- `238996b99f7f` Update common files (#2512) (micronaut-build, 2026-05-10)
- `f39401f1dba7` update versions (Sergio del Amo, 2026-05-08)
- `28d4e3273902` Update common files (#2510) (micronaut-build, 2026-05-08)
- `0b6bdc344ca7` [aws] Update common files for branch 5.0.x (#2507) (micronaut-build, 2026-05-02)
- `736872c20340` Update aws-java-sdk-v2 monorepo to v2.44.0 (#2505) (renovate[bot], 2026-05-02)
- `ecac5f0147b2` Update kotlin monorepo to v2.3.21 (#2508) (renovate[bot], 2026-04-30)
- `2457ae70341b` Update common files (#2503) (micronaut-build, 2026-04-26)
- `0f044ca4781e` [skip ci] Release v5.0.0-M3 (micronaut-build, 2026-04-20)
- `fb553634a88b` Replace usage of MediaTypeCodec (#2496) (Denis Stepanov, 2026-04-20)
- `e44fb31b8c9e` micronaut-validation = "5.0.0-M2" (Sergio del Amo, 2026-04-20)
- `987b181af54e` micronaut-servlet = "6.0.0-M3" (Sergio del Amo, 2026-04-20)
- `4cd8f233c353` micronaut-serde = "3.0.0-M7" (Sergio del Amo, 2026-04-20)
- `2ee120e0c54b` micronaut = "5.0.0-M23" (Sergio del Amo, 2026-04-20)
- `9ae99390d7d0` Update common files (#2502) (micronaut-build, 2026-04-20)
- `9a528aaccf7a` [skip ci] Release v5.0.0-M2 (micronaut-build, 2026-04-17)
- `09e27d8ad861` ignore test (Sergio del Amo, 2026-04-17)
- `74cf0feb022a` del micronaut.propagation=thread-local (Sergio del Amo, 2026-04-17)
- `3f41167f09e7` micronaut-reactor = "4.0.0-M2" (Sergio del Amo, 2026-04-17)
- `d86442957660` micronaut-test = "5.0.0-M8" (Sergio del Amo, 2026-04-17)
- `b446255596c2` Update to Micronaut Core 5.0.0-M22 (#2499) (Jonas Konrad, 2026-04-17)
- `c59f849daeb3` Update common files (#2501) (micronaut-build, 2026-04-17)
- `04b7475293f3` Update common files (#2498) (micronaut-build, 2026-04-15)
- `b029c3cbe68a` tck: exclude FormsJacksonAnnotationsTest (Sergio del Amo, 2026-04-08)
- `09e7578c34db` tck: exclude test FormBindingDeadlockTest (Sergio del Amo, 2026-04-08)
- `f70c3a288ee8` set micronaut.propagation=thread-local (Sergio del Amo, 2026-04-08)
- `0dd491b45ed3` micronaut-test = "5.0.0-M7" (Sergio del Amo, 2026-04-08)
- `92f7221f4343` micronaut = "5.0.0-M20" (Sergio del Amo, 2026-04-08)
- `0360de67685c` Update common files (#2487) (micronaut-build, 2026-04-08)
- `093ce6305e55` [skip ci] Release v5.0.0-M1 (micronaut-build, 2026-02-19)
- `39f6f15592f4` Revert "revert changes to S3BucketTest" (Sergio del Amo, 2026-02-19)
- `824032711aa9` revert changes to S3BucketTest (Sergio del Amo, 2026-02-19)
- `a64c12d9e39a` Fix AWS Module with Micronaut 5 Milestones (#2480) (Sergio del Amo, 2026-02-19)
- `c9a6c6974fc5` micronaut-groovy = "5.0.0-M1" (Sergio del Amo, 2026-02-18)
- `43045d0fb637` micronaut = "5.0.0-M11" (Sergio del Amo, 2026-02-18)
- `e144f000935e` testcontainers-localstack correct artifact id (Sergio del Amo, 2026-01-02)
- `dc46f92cd522` use testcontainers bom from MN test (Sergio del Amo, 2026-01-02)
- `2528c682298a` micronaut-views = "6.0.0-M1" (Sergio del Amo, 2026-02-17)
- `de45ee93dbf7` micronaut-test-resources = "3.0.0-M6" (Sergio del Amo, 2026-02-17)
- `746a503ab589` micronaut-logging = "2.0.0-M1" (Sergio del Amo, 2026-02-17)
- `22c7d37586be` micronaut-test = "5.0.0-M6" (Sergio del Amo, 2026-02-17)
- `e26716ab984f` micronaut = "5.0.0-M10" (Sergio del Amo, 2026-02-17)
- `72e2058629ae` Update common files (#2468) (micronaut-build, 2026-02-17)
- `6c93d7c84478` don’t define groovy version (Sergio del Amo, 2026-01-02)
- `028c83b0a741` don’t define micronaut-docs (Sergio del Amo, 2026-01-02)
- `1f310388af6b` spock compatible with Groovy 5 already in MN test (Sergio del Amo, 2026-01-02)
- `0261b55ecc36` mongodb = "6.0.1-M1" (Sergio del Amo, 2026-01-02)
- `316b2fd8fd06` discovery = "5.0.0-M1" (Sergio del Amo, 2026-01-02)
- `c4a887adca37` micronaut-test = "5.0.0-M3" (Sergio del Amo, 2026-01-02)
- `da232e565484` micronaut = "5.0.0-M6" (Sergio del Amo, 2026-01-02)
- `7da0fc5aaa6c` Update common files (#2451) (micronaut-build, 2026-01-02)
- `43c17d19fdda` fix configuration fixture (Sergio del Amo, 2025-12-10)
- `b8baca7b0b8d` force spock version (Sergio del Amo, 2025-12-10)
- `7f5073e8633f` use aws-module (Sergio del Amo, 2025-12-10)
- `838e2c879ed3` Update to Jackson 3 imports (Sergio del Amo, 2025-12-10)
- `7ad1e7cb3b98` fix JSpecify nullability annotations (Sergio del Amo, 2025-12-10)
- `97fb73acf66d` micronautBuild description (Sergio del Amo, 2025-12-10)
- `5a3e4eaff371` micronaut = "5.0.0-M2" (Sergio del Amo, 2025-12-10)
- `f75d35b7b388` micronaut-serde = "3.0.0-M1" (Sergio del Amo, 2025-12-10)
- `a6de237f86df` micronaut-servlet = "6.0.0-M1" (Sergio del Amo, 2025-12-10)
- `21a02d447bd8` micronaut-validation = "5.0.0-M1" (Sergio del Amo, 2025-12-10)
- `d51266ec0c00` Update common files (#2433) (micronaut-build, 2025-12-10)
- `c950dfbce99d` Replace Micronaut nullability annotations with JSpecify nullability annotations (#2444) (Copilot, 2025-12-01)
- `7537fc0ba020` Merge branch '4.12.x' into 5.0.x (Sergio del Amo, 2025-11-19)
- `bdaeea25e46b` Update common files (#2424) (micronaut-build, 2025-11-19)
- `20d2151e896d` use spock null assertion (Sergio del Amo, 2025-11-03)
- `d41d367ccce3` Update micronaut build (#2421) (issam liqali, 2025-11-03)
- `35f662bf4d52` Update common files (#2416) (micronaut-build, 2025-11-03)
- `0bcc8bf2eb8b` Merge branch '4.12.x' into 5.0.x (Sergio del Amo, 2025-10-22)
- `079e61e31f1d` Micronaut 5 compatibility and release prep (#2414) (issam liqali, 2025-10-21)
- `c1980b527a7e` Update common files (#2415) (micronaut-build, 2025-10-21)
- `e07a948162bc` Update common files (#2413) (micronaut-build, 2025-10-17)
- `b5fc6007e582` Update common files (#2409) (micronaut-build, 2025-10-16)
- `1812a10f46c0` micronaut build plugin 8.0.0-M4 (Sergio del Amo, 2025-10-10)
- `3b74fbca1bbc` gradle 9.1 (Sergio del Amo, 2025-10-10)
- `c107497ace61` Merge branch '4.12.x' into 5.0.x (Sergio del Amo, 2025-10-10)
- `5e08737e654b` Merge branch '4.9.x' into 5.0.x (Sergio del Amo, 2024-12-23)
- `f04c3f902cb8` Merge branch '4.5.x' into 5.0.x (Sergio del Amo, 2024-04-06)
- `5d2f0f9bab0b` Update common files (#2092) (micronaut-build, 2024-03-27)
- `e00fde814b60` Merge branch '4.4.x' (Sergio del Amo, 2024-03-08)
- `8ebed2bd88f8` Update common files (#2070) (micronaut-build, 2024-03-08)
- `f2f53c432c43` Update common files (#2064) (micronaut-build, 2024-02-28)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` aws-alexa-httpserver/build.gradle.kts
- `M` aws-alexa/build.gradle.kts
- `M` aws-lambda-events-serde/build.gradle.kts
- `M` aws-parameter-store/build.gradle.kts
- `M` aws-sdk-v1/build.gradle.kts
- `M` aws-secretsmanager/build.gradle.kts
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.aws-base.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.aws-module.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.aws-native-tests.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.aws-tests-java.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.aws-tests.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.aws.http-server-tck-module.gradle
- `M` function-aws-alexa/build.gradle.kts
- `M` function-aws-test/build.gradle.kts
- `M` function-aws/build.gradle.kts
- `M` function-client-aws-v2/build.gradle.kts
- `M` function-client-aws/build.gradle.kts
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` settings.gradle.kts
- `M` test-suite-function-client-aws-groovy/build.gradle.kts
- `M` test-suite-function-client-aws-kotlin/build.gradle.kts
- `M` test-suite-groovy/build.gradle.kts
- `M` test-suite-kotlin/build.gradle.kts
- `M` test-suite-s3/build.gradle.kts
- `A` test-suite-utils/build.gradle.kts

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
- `M` function-aws-custom-runtime/src/test/java/io/micronaut/docs/Book.java
- `M` function-aws-custom-runtime/src/test/java/io/micronaut/docs/BookSaved.java
- `A` src/main/docs/guide/breaks.adoc
- `M` src/main/docs/guide/distributedconfiguration/distributedconfigurationsecretsmanager.adoc
- `M` src/main/docs/guide/distributedconfiguration/distributedconfigurationsecretsmanagersearch.adoc
- `M` src/main/docs/guide/distributedconfiguration/parametersStore.adoc
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
- `M` .github/workflows/central-sync.yml
- `M` .github/workflows/graalvm-dev.yml
- `M` .github/workflows/publish-snapshot.yml
- `A` .github/workflows/sonatype.yml
- `M` .gitignore
- `A` .sdkmanrc
- `M` MAINTAINING.md
- `M` aws-alexa-httpserver/src/main/java/io/micronaut/aws/alexa/httpserver/conf/AlexaControllerConfiguration.java
- `M` aws-alexa-httpserver/src/main/java/io/micronaut/aws/alexa/httpserver/conf/AlexaControllerConfigurationProperties.java
- `M` aws-alexa-httpserver/src/main/java/io/micronaut/aws/alexa/httpserver/controllers/SkillController.java
- `M` aws-alexa-httpserver/src/main/java/io/micronaut/aws/alexa/httpserver/services/DefaultRequestEnvelopeService.java
- `M` aws-alexa-httpserver/src/main/java/io/micronaut/aws/alexa/httpserver/services/RequestEnvelopeService.java
- `M` aws-alexa/src/main/java/io/micronaut/aws/alexa/builders/AlexaSkillBuilder.java
- `M` aws-alexa/src/main/java/io/micronaut/aws/alexa/builders/DefaultAlexaSkillBuilder.java
- `M` aws-alexa/src/main/java/io/micronaut/aws/alexa/builders/SkillBuilderProvider.java
- `M` aws-alexa/src/main/java/io/micronaut/aws/alexa/builders/StandardSkillBuilderProvider.java
- `M` aws-alexa/src/main/java/io/micronaut/aws/alexa/conf/AlexaSkillConfiguration.java
- `M` aws-alexa/src/main/java/io/micronaut/aws/alexa/conf/AlexaSkillConfigurationProperties.java
- `M` aws-alexa/src/main/java/io/micronaut/aws/alexa/flashbriefing/FlashBriefingItem.java
- `M` aws-alexa/src/main/java/io/micronaut/aws/alexa/locale/CompositeHandlerInputLocaleResolver.java
- `M` aws-alexa/src/main/java/io/micronaut/aws/alexa/locale/DefaultHandlerInputLocaleResolver.java
- `M` aws-alexa/src/main/java/io/micronaut/aws/alexa/locale/HandlerInputLocaleResolutionConfigurationProperties.java
- `M` aws-alexa/src/main/java/io/micronaut/aws/alexa/ssml/Ssml.java
- `M` aws-apigateway/src/main/java/io/micronaut/aws/apigateway/APIGatewayProxyRequestEventStageResolver.java
- `M` aws-apigateway/src/main/java/io/micronaut/aws/apigateway/AmazonApiGatewayUtils.java
- `M` aws-apigateway/src/main/java/io/micronaut/aws/apigateway/HttpRequestStageResolver.java
- `M` aws-apigateway/src/main/java/io/micronaut/aws/apigateway/StageResolver.java
- `M` aws-cloudwatch-logging/src/main/java/io/micronaut/aws/cloudwatch/logging/CloudWatchLoggingClient.java
- `M` aws-common/src/main/java/io/micronaut/discovery/cloud/aws/AmazonComputeInstanceMetadataResolver.java
- `M` aws-distributed-configuration/src/main/java/io/micronaut/aws/distributedconfiguration/AwsDistributedConfiguration.java
- `M` aws-distributed-configuration/src/main/java/io/micronaut/aws/distributedconfiguration/AwsDistributedConfigurationClient.java
- `M` aws-distributed-configuration/src/main/java/io/micronaut/aws/distributedconfiguration/AwsDistributedConfigurationProperties.java
- `M` aws-distributed-configuration/src/main/java/io/micronaut/aws/distributedconfiguration/KeyValueFetcher.java
- `A` aws-distributed-configuration/src/main/java/io/micronaut/aws/distributedconfiguration/imports/AwsConfigImportContextFactory.java
- `A` aws-distributed-configuration/src/main/java/io/micronaut/aws/distributedconfiguration/imports/LegacyConfigClientDeprecationLogger.java
- `M` aws-lambda-events-serde/src/main/java/io/micronaut/aws/lambda/events/serde/JodaDateTimeSerde.java
- `M` aws-lambda-events-serde/src/main/java/io/micronaut/aws/lambda/events/serde/ResponseElementsEntitySerde.java
- `M` aws-lambda-events-serde/src/main/java/io/micronaut/aws/lambda/events/serde/S3EventSerde.java
- `M` aws-lambda-events-serde/src/main/java/io/micronaut/aws/lambda/events/serde/S3ObjectEntitySerde.java
- `M` aws-lambda-events-serde/src/main/java/io/micronaut/aws/lambda/events/serde/SerdeCustomPojoSerializer.java
- `M` aws-parameter-store/src/main/java/io/micronaut/discovery/aws/parameterstore/AWSParameterQueryProvider.java
- `M` aws-parameter-store/src/main/java/io/micronaut/discovery/aws/parameterstore/AWSParameterStoreConfigClient.java
- `M` aws-parameter-store/src/main/java/io/micronaut/discovery/aws/parameterstore/AWSParameterStoreConfiguration.java
- `M` aws-parameter-store/src/main/java/io/micronaut/discovery/aws/parameterstore/DefaultParameterQueryProvider.java
- `A` aws-parameter-store/src/main/java/io/micronaut/discovery/aws/parameterstore/imports/ParameterStorePropertySourceImporter.java
- `A` aws-parameter-store/src/main/resources/META-INF/services/io.micronaut.context.env.PropertySourceImporter
- `M` aws-sdk-v2/src/main/java/io/micronaut/aws/sdk/v2/service/AWSServiceConfiguration.java
- `M` aws-sdk-v2/src/main/java/io/micronaut/aws/sdk/v2/service/AWSServiceConfigurationProperties.java
- `M` aws-sdk-v2/src/main/java/io/micronaut/aws/sdk/v2/service/AwsClientFactory.java
- `M` aws-sdk-v2/src/main/java/io/micronaut/aws/sdk/v2/service/cloudwatchlogs/CloudwatchLogsClientFactory.java
- `M` aws-sdk-v2/src/main/java/io/micronaut/aws/sdk/v2/service/dynamodb/DynamoDbClientFactory.java
- `M` aws-sdk-v2/src/main/java/io/micronaut/aws/sdk/v2/service/gatewaymanagement/ApiGatewayManagementApiClientFactory.java
- `M` aws-sdk-v2/src/main/java/io/micronaut/aws/sdk/v2/service/lambda/LambdaClientFactory.java
- `M` aws-sdk-v2/src/main/java/io/micronaut/aws/sdk/v2/service/s3/S3ClientFactory.java
- `M` aws-sdk-v2/src/main/java/io/micronaut/aws/sdk/v2/service/secretsmanager/SecretsManagerClientFactory.java
- `M` aws-sdk-v2/src/main/java/io/micronaut/aws/sdk/v2/service/servicediscovery/ServiceDiscoveryAsyncClientFactory.java
- `M` aws-sdk-v2/src/main/java/io/micronaut/aws/sdk/v2/service/ses/SesClientFactory.java
- `M` aws-sdk-v2/src/main/java/io/micronaut/aws/sdk/v2/service/sns/SnsClientFactory.java
- `M` aws-sdk-v2/src/main/java/io/micronaut/aws/sdk/v2/service/sqs/SqsClientFactory.java
- `M` aws-sdk-v2/src/main/java/io/micronaut/aws/sdk/v2/service/ssm/SsmClientFactory.java
- `M` aws-secretsmanager/src/main/java/io/micronaut/aws/secretsmanager/SecretsManagerConfigurationClient.java
- `M` aws-secretsmanager/src/main/java/io/micronaut/aws/secretsmanager/SecretsManagerGroupNameAwareKeyValueFetcher.java
- `M` aws-secretsmanager/src/main/java/io/micronaut/aws/secretsmanager/SecretsManagerKeyValueFetcher.java
- `A` aws-secretsmanager/src/main/java/io/micronaut/aws/secretsmanager/imports/SecretsManagerPropertySourceImporter.java
- `A` aws-secretsmanager/src/main/resources/META-INF/services/io.micronaut.context.env.PropertySourceImporter
- `M` aws-service-discovery/src/main/java/io/micronaut/discovery/aws/servicediscovery/AwsServiceDiscoveryClientConfiguration.java
- `M` aws-ua/src/main/java/io/micronaut/aws/ua/UserAgentProvider.java
- `M` config/accepted-api-changes.json
- `M` config/checkstyle/checkstyle.xml
- `M` function-aws-alexa/src/main/java/io/micronaut/function/aws/alexa/AlexaFunction.java
- `M` function-aws-api-proxy/src/main/java/io/micronaut/function/aws/proxy/AbstractServletHttpResponse.java
- `M` function-aws-api-proxy/src/main/java/io/micronaut/function/aws/proxy/ApiGatewayBinderRegistry.java
- `M` function-aws-api-proxy/src/main/java/io/micronaut/function/aws/proxy/ApiGatewayServletRequest.java
- `M` function-aws-api-proxy/src/main/java/io/micronaut/function/aws/proxy/MapListOfStringAndMapStringConvertibleMultiValue.java
- `D` function-aws-api-proxy/src/main/java/io/micronaut/function/aws/proxy/MicronautLambdaHandler.java
- `M` function-aws-api-proxy/src/main/java/io/micronaut/function/aws/proxy/alb/ApplicationLoadBalancerFunction.java
- `M` function-aws-api-proxy/src/main/java/io/micronaut/function/aws/proxy/payload1/ApiGatewayProxyRequestEventFunction.java
- `M` function-aws-api-proxy/src/main/java/io/micronaut/function/aws/proxy/payload2/APIGatewayV2HTTPEventFunction.java
- `M` function-aws-api-proxy/src/main/java/io/micronaut/function/aws/proxy/security/MicronautLambdaAuthenticationFetcher.java
- `M` function-aws-custom-runtime/src/main/java/io/micronaut/function/aws/runtime/AbstractMicronautLambdaRuntime.java
- `M` function-aws-custom-runtime/src/main/java/io/micronaut/function/aws/runtime/AwsLambdaRuntimeApi.java
- `M` function-aws-custom-runtime/src/main/java/io/micronaut/function/aws/runtime/AwsLambdaRuntimeApiError.java
- `M` function-aws/src/main/java/io/micronaut/function/aws/DefaultDiagnosticInfoPopulator.java
- `M` function-aws/src/main/java/io/micronaut/function/aws/DefaultLambdaContextFactory.java
- `M` function-aws/src/main/java/io/micronaut/function/aws/DiagnosticInfoPopulator.java
- `M` function-aws/src/main/java/io/micronaut/function/aws/HandlerUtils.java
- `M` function-aws/src/main/java/io/micronaut/function/aws/JsonMapperCustomPojoSerializer.java
- `M` function-aws/src/main/java/io/micronaut/function/aws/LambdaContextFactory.java
- `M` function-aws/src/main/java/io/micronaut/function/aws/MicronautRequestHandler.java
- `M` function-aws/src/main/java/io/micronaut/function/aws/MicronautRequestStreamHandler.java
- `M` function-aws/src/main/java/io/micronaut/function/aws/XRayUtils.java
- `M` function-aws/src/main/java/io/micronaut/function/aws/event/AfterExecutionEvent.java
- `M` function-client-aws-v2/src/main/java/io/micronaut/function/client/aws/v2/AwsLambdaFunctionExecutor.java
- `M` function-client-aws/src/main/java/io/micronaut/function/client/aws/AWSLambdaConfiguration.java
- `M` function-client-aws/src/main/java/io/micronaut/function/client/aws/AWSLambdaFunctionExecutor.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` aws-alexa/src/test/groovy/io/micronaut/aws/alexa/flashbriefing/FlashBriefingItemSpec.groovy
- `M` aws-cloudwatch-logging/src/test/groovy/io/micronaut/aws/cloudwatch/logging/CloudwatchLoggingSpec.groovy
- `M` aws-common/src/test/groovy/io/micronaut/discovery/cloud/AmazonEC2InstanceResolverSpec.groovy
- `A` aws-distributed-configuration/src/test/groovy/io/micronaut/aws/distributedconfiguration/imports/AwsConfigImportContextFactorySpec.groovy
- `A` aws-parameter-store/src/test/groovy/io/micronaut/discovery/aws/parameterstore/AWSParameterStoreDeprecationAndCoexistenceSpec.groovy
- `A` aws-parameter-store/src/test/groovy/io/micronaut/discovery/aws/parameterstore/AWSParameterStoreLegacyCharacterizationSpec.groovy
- `A` aws-parameter-store/src/test/groovy/io/micronaut/discovery/aws/parameterstore/AWSParameterStorePropertySourceImporterSpec.groovy
- `M` aws-sdk-v2/src/test/java/io/micronaut/aws/sdk/v2/RekognitionClientFactory.java
- `M` aws-secretsmanager/src/test/groovy/io/micronaut/aws/secretsmanager/ConfigurationFixture.groovy
- `A` aws-secretsmanager/src/test/groovy/io/micronaut/aws/secretsmanager/SecretsManagerConfigImportAwsIntegrationSpec.groovy
- `A` aws-secretsmanager/src/test/groovy/io/micronaut/aws/secretsmanager/SecretsManagerDeprecationAndCoexistenceSpec.groovy
- `A` aws-secretsmanager/src/test/groovy/io/micronaut/aws/secretsmanager/SecretsManagerLegacyCharacterizationSpec.groovy
- `A` aws-secretsmanager/src/test/groovy/io/micronaut/aws/secretsmanager/SecretsManagerPropertySourceImporterSpec.groovy
- `M` function-aws-api-proxy-test/src/main/java/io/micronaut/function/aws/proxy/test/AwsProxyHttpHandler.java
- `M` function-aws-api-proxy-test/src/main/java/io/micronaut/function/aws/proxy/test/BodyUtils.java
- `M` function-aws-api-proxy-test/src/main/java/io/micronaut/function/aws/proxy/test/ContextProvider.java
- `M` function-aws-api-proxy-test/src/main/java/io/micronaut/function/aws/proxy/test/EmbeddedServerFactory.java
- `M` function-aws-api-proxy-test/src/main/java/io/micronaut/function/aws/proxy/test/MockContextProvider.java
- `M` function-aws-custom-runtime/src/test/groovy/io/micronaut/function/aws/runtime/CustomRuntimeForMicronautRequestHandlerSpec.groovy
- `M` function-aws-custom-runtime/src/test/groovy/io/micronaut/function/aws/runtime/RuntimeApiSpec.groovy
- `M` function-aws-test/src/main/java/io/micronaut/function/aws/test/MicronautLambdaJunit5Extension.java
- `M` function-aws-test/src/main/java/io/micronaut/function/aws/test/annotation/MicronautLambdaTest.java
- `A` function-aws-test/src/test/java/io/micronaut/function/aws/test/DeduceEnvironmentDisabledTest.java
- `M` function-aws/src/test/groovy/io/micronaut/function/aws/MicronautRequestStreamHandlerDontCloseCtxSpec.groovy
- `M` function-client-aws-v2/src/test/groovy/io/micronaut/function/client/aws/v2/ComplexType.java
- `M` function-client-aws-v2/src/test/groovy/io/micronaut/function/client/aws/v2/TestFunctionClientRequest.java
- `M` function-client-aws-v2/src/test/groovy/io/micronaut/function/client/aws/v2/TestFunctionClientResponse.java
- `M` function-client-aws-v2/src/test/groovy/io/micronaut/function/client/aws/v2/TestFunctionSpec.groovy
- `M` test-suite-aws-lambda-events-serde/src/test/java/io/micronaut/aws/lambda/events/serde/tests/Issue2056Test.java
- `M` test-suite-http-server-tck-function-aws-api-gateway-proxy-alb/src/test/java/io/micronaut/http/server/tck/lambda/ApplicationLoadBalancerRequestEventFactory.java
- `M` test-suite-http-server-tck-function-aws-api-gateway-proxy-alb/src/test/java/io/micronaut/http/server/tck/lambda/GatewayLambdaServerUnderTest.java
- `M` test-suite-http-server-tck-function-aws-api-gateway-proxy-alb/src/test/java/io/micronaut/http/server/tck/lambda/HttpHostResolverReplacement.java
- `M` test-suite-http-server-tck-function-aws-api-gateway-proxy-alb/src/test/java/io/micronaut/http/server/tck/lambda/tests/ApplicationLoadBalancerTckTestSuite.java
- `M` test-suite-http-server-tck-function-aws-api-gateway-proxy-payloadv1/src/test/java/io/micronaut/http/server/tck/lambda/APIGatewayProxyRequestEventFactory.java
- `M` test-suite-http-server-tck-function-aws-api-gateway-proxy-payloadv1/src/test/java/io/micronaut/http/server/tck/lambda/GatewayLambdaServerUnderTest.java
- `M` test-suite-http-server-tck-function-aws-api-gateway-proxy-payloadv1/src/test/java/io/micronaut/http/server/tck/lambda/HttpHostResolverReplacement.java
- `M` test-suite-http-server-tck-function-aws-api-gateway-proxy-payloadv1/src/test/java/io/micronaut/http/server/tck/lambda/tests/FunctionAwsApiGatewayProxyV1HttpServerTestSuite.java
- `M` test-suite-http-server-tck-function-aws-api-gateway-proxy-payloadv2/src/test/java/io/micronaut/http/server/tck/lambda/GatewayLambdaServerUnderTest.java
- `M` test-suite-http-server-tck-function-aws-api-gateway-proxy-payloadv2/src/test/java/io/micronaut/http/server/tck/lambda/HttpHostResolverReplacement.java
- `M` test-suite-http-server-tck-function-aws-api-gateway-proxy-payloadv2/src/test/java/io/micronaut/http/server/tck/lambda/tests/FunctionAwsApiGatewayProxyV2HttpServerTestSuite.java
- `M` test-suite-http-server-tck-function-aws-api-proxy-test/src/test/java/io/micronaut/http/server/tck/lambda/HttpHostResolverReplacement.java
- `M` test-suite-http-server-tck-function-aws-api-proxy-test/src/test/java/io/micronaut/http/server/tck/lambda/tests/MicronautLambdaHandlerHttpServerTestSuite.java
- `A` test-suite-s3/src/test/java/example/S3AsyncClientBeanCreatedEventListener.java
- `M` test-suite-s3/src/test/java/example/S3BucketTest.java
- `A` test-suite-s3/src/test/java/example/S3ClientBeanCreatedEventListener.java
- `A` test-suite-utils/src/main/java/io/micronaut/localstack/testcontainers/Localstack.java
- `A` test-suite-utils/src/main/java/io/micronaut/mongodb/testcontainers/MongoDb.java

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

