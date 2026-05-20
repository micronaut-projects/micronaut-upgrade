• Done. I compared in release direction mn4 -> mn5 and wrote the full report here:

  micronaut-grpc-mn4-to-mn5-comparison.md:1

  Scope: previous 4.13.x at e78c3c61b660, current 5.0.x at 78429a735bfc; both worktrees are clean. Delta: 97 commits, 103 changed files.

  Release Note Draft

  - Compatibility: Moves to the Micronaut 5 line and Protobuf 4. No breaks.adoc was present. Review candidate: deprecated server API removals for GrpcServerBuilder(), GrpcServerConfiguration.HEALTH_ENABLED, and an older
    GrpcServerConfiguration(...) constructor.
  - Features: Adds optional micronaut-grpc-inprocess for tests via grpc.server.in-process-name; it switches the embedded server and @GrpcChannel("grpc-server") to in-process transport.
  - Features: Adds grpc.server.executor so the gRPC server can use a named Executor bean.
  - Features: Adds reactive-grpc Reactor examples/docs and a Kotest greeting service example.
  - Fixes: Handles disabled gRPC client injection, fixes named gRPC target handling, and adds core ResourceResolver support when the HTTP module is absent.
  - Docs: Updates tracing docs to point new applications at OpenTelemetry gRPC integration while keeping legacy OpenTracing support documented.

  Key dependency changes: Micronaut Core 4.10.4 -> 5.0.0-RC2, Micronaut Platform 4.9.4 -> 5.0.0-M3, Gradle wrapper 8.14.3 -> 9.5.0, gRPC Java 1.75.0 -> 1.80.0, Protobuf 3.25.8 -> 4.34.1, gRPC Kotlin 1.4.3 -> 1.5.0, Micronaut
  Reactor 3.9.0 -> 4.0.0-RC1, Micronaut Tracing 7.2.0 -> 8.0.0-M1.

  Tests were not run; this was a comparison/reporting pass only.



# Release Note Comparison

Generated: 2026-05-06 15:43 UTC
Comparison: `mn4` -> `mn5`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-grpc` | `4.13.x` | `e78c3c61b660` | `git@github.com:micronaut-projects/micronaut-grpc.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-grpc` | `5.0.x` | `78429a735bfc` | `git@github.com:micronaut-projects/micronaut-grpc.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-grpc`
- Commit candidates found: 97
- File changes listed: 103
- Version values listed: 16
- File status counts: A=36, M=61, R=6

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `4.13.0-SNAPSHOT` | `5.0.0-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-discovery-client` | `io.micronaut.discovery:micronaut-discovery-client:4.7.1` | `io.micronaut.discovery:micronaut-discovery-client:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.gson` | `2.13.2` | `2.14.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.4` | `5.0.0-RC2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-discovery-client` | `4.7.1` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-kotlin` | `4.7.0` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-platform` | `4.9.4` | `5.0.0-M3` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-reactor` | `3.9.0` | `4.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `not present` | `3.0.0-RC1` | `added` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.9.0` | `5.0.0-M8` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-tracing` | `7.2.0` | `8.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.11.0` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.reactive-grpc` | `not present` | `1.2.4` | `added` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.0` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `dcf346948d1a` remove micronaut-docs (Sergio del Amo, 2026-02-12)
- `3c9af892e971` build: remove force spock version (Sergio del Amo, 2026-02-11)
- `39d3ac1b1c91` remove micronaut-docs-asciidoc-config-props (Sergio del Amo, 2026-02-11)
- `16be46b8b590` remove micronaut-docs (Sergio del Amo, 2025-12-29)

### Features

- `6decbf45256d` Add Kotest GreetingServiceTest example (#1189) (Graeme Rocher, 2026-05-05)
- `6f3c068801bb` Add optional in-process gRPC module (#1195) (Graeme Rocher, 2026-05-05)
- `98b084c32fc7` Support configuring the gRPC server executor (#1192) (Graeme Rocher, 2026-05-05)
- `cd529ab62634` Add reactive gRPC example and docs (#1191) (Graeme Rocher, 2026-04-30)

### Fixes

- `38eb59f3eae8` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m24 (#1178) (renovate[bot], 2026-04-22)
- `1dff51f0d1fa` fix(deps): update dependency io.micronaut.serde:micronaut-serde-jackson to v3.0.0-m4 (#1173) (renovate[bot], 2026-03-26)
- `38c402072bfd` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m18 (#1162) (renovate[bot], 2026-03-26)
- `66e1e33acc2e` fix(deps): update protobuf monorepo to v4 (#1017) (renovate[bot], 2026-02-12)
- `5c4ae46fefc2` fix(deps): update dependency io.grpc:grpc-kotlin-stub to v1.5.0 (#1104) (renovate[bot], 2026-02-12)
- `217a1c18cc3f` fix(deps): update dependency com.google.protobuf:protobuf-java to v4.33.5 (#1122) (renovate[bot], 2026-02-12)
- `888889bc7448` fix(deps): update grpc-java monorepo to v1.79.0 (#1126) (renovate[bot], 2026-02-12)
- `dcb2971ed0f3` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.12 (#1138) (renovate[bot], 2025-12-29)
- `3fbfccdd4b10` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#1127) (renovate[bot], 2025-12-10)
- `7c685c68a5da` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.12.0 (#1125) (renovate[bot], 2025-12-10)
- `96bdb706a010` fix(deps): update dependency io.micronaut.test:micronaut-test-bom to v4.10.2 (#1124) (renovate[bot], 2025-12-10)
- `bec61effbca3` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.1 (#1123) (renovate[bot], 2025-12-10)
- `4e8ceda3c680` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.8 (#1116) (renovate[bot], 2025-11-03)
- `4ed3fa9b9212` fix(deps): update dependency io.micronaut.reactor:micronaut-reactor-bom to v3.9.1 (#1117) (renovate[bot], 2025-11-03)

### Dependency Updates

- `e84a56ffb913` Update dependency io.micronaut.validation:micronaut-validation-bom to v5.0.0-RC1 (#1205) (renovate[bot], 2026-05-05)
- `236e3524d75c` Update Micronaut dependencies (#1202) (renovate[bot], 2026-05-05)
- `c7d359e7b7f6` Update dependency io.micronaut:micronaut-core-bom to v5.0.0-M26 (#1182) (renovate[bot], 2026-05-01)
- `35e963a0f2a0` Update dependency com.google.code.gson:gson to v2.14.0 (#1198) (renovate[bot], 2026-05-01)
- `f18702cd4ab6` Upgrade to Protobuf 4 (#1160) (renovate[bot], 2026-04-29)
- `217b45744005` chore(deps): combine Renovate dependency upgrades (#1184) (Graeme Rocher, 2026-04-29)
- `46f95a3b23a2` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#1161) (renovate[bot], 2026-03-26)
- `a3f8ba8fef3f` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-02-12)
- `5c311f56ff6b` Revert "fix(deps): update protobuf monorepo to v4 (#1017)" (Sergio del Amo, 2026-02-12)
- `c6eaad0de45a` chore(deps): update dependency com.google.protobuf to v0.9.6 (#1140) (renovate[bot], 2026-02-12)
- `c678cc339b66` chore(deps): update dependency org.apache.maven.plugins:maven-compiler-plugin to v3.15.0 (#1152) (renovate[bot], 2026-02-12)
- `6bbdfd50f6d5` chore(deps): update dependency maven to v3.9.12 (#1141) (renovate[bot], 2026-02-12)
- `14f1a5bdf4c6` chore(deps): update gradle to v9.3.1 (#1151) (renovate[bot], 2026-02-12)
- `8882de893576` chore(deps): update graalvm/setup-graalvm action to v1.4.5 (#1147) (renovate[bot], 2026-02-12)
- `1f5b87075535` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m16 (#1156) (renovate[bot], 2026-02-12)
- `cb88ce542d5f` java version 25 (Sergio del Amo, 2026-02-11)
- `2ae03556a616` chore(deps): update actions/cache action to v5 (#1139) (renovate[bot], 2025-12-29)
- `bcb98d712dca` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m13 (#1142) (renovate[bot], 2025-12-29)
- `689bcf70d55c` chore(deps): update github artifact actions (#1143) (renovate[bot], 2025-12-29)
- `ce2c49d708e3` chore(deps): update gradle to v9 (#1131) (renovate[bot], 2025-12-10)
- `0899af71e1f0` chore(deps): update actions/checkout action to v6.0.1 (#1128) (renovate[bot], 2025-12-10)
- `299cd1a2d0af` chore(deps): update softprops/action-gh-release action to v2.5.0 (#1121) (renovate[bot], 2025-12-10)
- `7d0c5e187db9` chore(deps): update plugin io.micronaut.minimal.application to v4.6.1 (#1120) (renovate[bot], 2025-12-10)
- `34aa04b72fbf` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#1118) (renovate[bot], 2025-12-10)
- `e1c605faf665` chore(deps): update dependency org.apache.maven.plugins:maven-compiler-plugin to v3.14.1 (#1108) (renovate[bot], 2025-12-10)
- `259839b4d2b2` chore(deps): update dependency org.apache.maven.plugins:maven-surefire-plugin to v3.5.4 (#1111) (renovate[bot], 2025-11-03)
- `f719ec43d717` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#1113) (renovate[bot], 2025-11-03)
- `fe8b9d9fbef6` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m8 (#1114) (renovate[bot], 2025-11-03)

### Documentation

- `1ead7765969b` docs: update gRPC tracing guide for OpenTelemetry (#1187) (Graeme Rocher, 2026-04-30)

### Internal

- `ca938c255fd2` build: micronautBuild, descriptor parentModuleId (Sergio del Amo, 2025-12-29)

### Review Candidates

- `78429a735bfc` git ingore .kotlin (Sergio del Amo, 2026-05-06)
- `917abdc88eec` micronaut-kotlin = "5.0.0-M1" (Sergio del Amo, 2026-05-06)
- `7fa2be8a1bee` micronaut-platform = "5.0.0-M3" (Sergio del Amo, 2026-05-06)
- `4833e6bb8f9c` micronaut = "5.0.0-RC2" (Sergio del Amo, 2026-05-06)
- `1da0a6bc15d8` micronaut-gradle-plugin = '5.0.0-M1' (Sergio del Amo, 2026-05-06)
- `d7573c6bfde5` Update common files (#1206) (micronaut-build, 2026-05-06)
- `2a3a0978b200` Replace YAML source blocks with configuration macro (#1204) (Graeme Rocher, 2026-05-05)
- `9a6acdcf132d` Handle disabled gRPC client injection (#1200) (Graeme Rocher, 2026-05-05)
- `e047ad01ba35` Fix named gRPC client target syntax (#1197) (Graeme Rocher, 2026-05-05)
- `bed70b864c17` Update common files (#1199) (micronaut-build, 2026-05-05)
- `a8f7133f1914` [grpc] Update common files for branch 5.0.x (#1193) (micronaut-build, 2026-05-01)
- `c8f786a879eb` Fix missing ResourceResolver for gRPC server (#1188) (Graeme Rocher, 2026-04-30)
- `4ba5fab1e1ce` Update common files (#1186) (micronaut-build, 2026-04-29)
- `dcad29bbfac1` Update common files (#1176) (micronaut-build, 2026-04-26)
- `4bff5e15ea69` Update to core M19 (#1175) (Issam Liqali, 2026-04-02)
- `cc22e6b3499e` Update common files (#1159) (micronaut-build, 2026-03-26)
- `0442d6abac99` [skip ci] Release v5.0.0-M1 (micronaut-build, 2026-02-12)
- `28c6410f21b2` Fix native build for jdk 25 (#1158) (issam liqali, 2026-02-12)
- `22d4bbf3fe20` apply directly micronaut test spock (Sergio del Amo, 2026-02-12)
- `845f673fc269` Update common files (#1146) (micronaut-build, 2026-02-12)
- `16f4f91e0f4f` micronaut-tracing = "8.0.0-M1" (Sergio del Amo, 2026-02-11)
- `b27cf9777c3d` micronaut-discovery-client = "5.0.0-M1" (Sergio del Amo, 2026-02-11)
- `5958f8a5e69e` micronaut-platform = "4.10.8" (Sergio del Amo, 2026-02-11)
- `de9187c7c596` micronaut = "5.0.0-M10" (Sergio del Amo, 2026-02-11)
- `02336c0025e1` gradle plugin 4.6.2 (Sergio del Amo, 2026-02-11)
- `0027d59e5cb6` Update to Micronaut 5 (#1150) (issam liqali, 2026-02-03)
- `dbd8a7c752ae` use source and target compatiblity to 21 (Sergio del Amo, 2025-12-29)
- `47aa771ca675` use kotlin compilerOptions not koltin jvmToolchain (Sergio del Amo, 2025-12-29)
- `079716ac9d0a` fix ExectuableMethod override (Sergio del Amo, 2025-12-29)
- `b59f2ee0f099` fix placement of JSpecify nullability annotations (Sergio del Amo, 2025-12-29)
- `223b3e82e00f` micronaut-platform = "4.10.6" (Sergio del Amo, 2025-12-29)
- `ba5ae5fe372e` test = "5.0.0-M3" (Sergio del Amo, 2025-12-29)
- `f5da98ca0864` validation = "5.0.0-M1" (Sergio del Amo, 2025-12-29)
- `41522b7f39e9` reactor = "4.0.0-M1" (Sergio del Amo, 2025-12-29)
- `e696b858150e` core M6 (Sergio del Amo, 2025-12-29)
- `d703d74a71b6` Update common files (#1137) (micronaut-build, 2025-12-29)
- `1535ceef1ba1` Fixes #1144 - replace deprecated mainClassName with application.mainClass (#1145) (Hui Qiao, 2025-12-29)
- `eb9e42f93e97` Update common files (#1119) (micronaut-build, 2025-12-10)
- `488fb49bdb83` Replace Micronaut nullability annotations with JSpecify nullability annotations (#1134) (Copilot, 2025-12-01)
- `67b230bc4e29` Update common files (#1110) (micronaut-build, 2025-11-03)
- `1be97635d97c` Update common files (#1109) (micronaut-build, 2025-10-17)
- `ca06c6454b94` Update common files (#1107) (micronaut-build, 2025-10-17)
- `c306eaf3abc7` Micronaut Gradle Build Plugin 8.0.0-M4 (Sergio del Amo, 2025-10-15)
- `0b0b60d6257a` gradle 9.1 (Sergio del Amo, 2025-10-15)
- `06f913eea75d` projectVersion=5.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-10-15)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `R052` buildSrc/build.gradle
- `R080` buildSrc/settings.gradle
- `R100` buildSrc/src/main/groovy/io.micronaut.build.internal.grpc-base.gradle
- `R060` buildSrc/src/main/groovy/io.micronaut.build.internal.grpc-minimal-test.gradle
- `R057` buildSrc/src/main/groovy/io.micronaut.build.internal.grpc-module.gradle
- `R084` buildSrc/src/main/groovy/io.micronaut.build.internal.grpc-tests.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` grpc-client-runtime/build.gradle
- `M` grpc-health/build.gradle
- `A` grpc-inprocess/build.gradle
- `M` grpc-opentracing/build.gradle
- `M` grpc-server-runtime/build.gradle
- `M` settings.gradle
- `M` test-suite-groovy/build.gradle
- `M` test-suite-java/build.gradle
- `M` test-suite-java/pom.xml
- `M` test-suite-kotlin/build.gradle
- `M` test-suite-protobuff-json-java/build.gradle
- `M` test-suite-protobuff-json-java/gradle/wrapper/gradle-wrapper.properties

### Documentation

- `A` .agents/skills/docs/SKILL.md
- `A` .agents/skills/docs/references/control-panel-patterns.md
- `A` .agents/skills/docs/references/micronaut-docs-providers.md
- `M` .github/workflows/release.yml
- `M` src/main/docs/guide/client.adoc
- `M` src/main/docs/guide/gettingStarted.adoc
- `M` src/main/docs/guide/server.adoc
- `M` src/main/docs/guide/serviceDiscovery.adoc
- `M` src/main/docs/guide/tracing.adoc

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
- `M` grpc-annotation/src/main/java/io/micronaut/grpc/annotation/GrpcRestJsonExposed.java
- `M` grpc-client-runtime/src/main/java/io/micronaut/grpc/channels/GrpcManagedChannelConfiguration.java
- `M` grpc-client-runtime/src/main/java/io/micronaut/grpc/channels/GrpcManagedChannelFactory.java
- `M` grpc-client-runtime/src/main/java/io/micronaut/grpc/discovery/GrpcNameResolverProvider.java
- `A` grpc-inprocess/src/main/java/io/micronaut/grpc/server/GrpcInProcessServerConfiguration.java
- `A` grpc-inprocess/src/main/java/io/micronaut/grpc/server/InProcessGrpcEmbeddedServer.java
- `A` grpc-inprocess/src/main/java/io/micronaut/grpc/server/InProcessGrpcServerBuilder.java
- `A` grpc-inprocess/src/main/java/io/micronaut/grpc/server/InProcessGrpcServerChannel.java
- `M` grpc-opentracing/src/main/java/io/micronaut/grpc/client/tracing/GrpcClientTracingInterceptorConfiguration.java
- `M` grpc-opentracing/src/main/java/io/micronaut/grpc/client/tracing/GrpcClientTracingInterceptorFactory.java
- `M` grpc-opentracing/src/main/java/io/micronaut/grpc/server/tracing/GrpcServerTracingInterceptorConfiguration.java
- `M` grpc-opentracing/src/main/java/io/micronaut/grpc/server/tracing/GrpcServerTracingInterceptorFactory.java
- `M` grpc-server-runtime/src/main/java/io/micronaut/grpc/server/GrpcEmbeddedServer.java
- `M` grpc-server-runtime/src/main/java/io/micronaut/grpc/server/GrpcEmbeddedServerListener.java
- `A` grpc-server-runtime/src/main/java/io/micronaut/grpc/server/GrpcResourceLoaderFactory.java
- `M` grpc-server-runtime/src/main/java/io/micronaut/grpc/server/GrpcServerBuilder.java
- `M` grpc-server-runtime/src/main/java/io/micronaut/grpc/server/GrpcServerChannel.java
- `M` grpc-server-runtime/src/main/java/io/micronaut/grpc/server/GrpcServerConfiguration.java
- `M` grpc-server-runtime/src/main/java/io/micronaut/grpc/server/GrpcServerInstance.java
- `M` grpc-server-runtime/src/main/java/io/micronaut/grpc/server/GrpcSslConfiguration.java
- `M` protobuff-json-support/src/main/java/io/micronaut/protobuf/json/GrpcProxyController.java
- `M` protobuff-json-support/src/main/java/io/micronaut/protobuf/json/ProtobufJsonTranscoder.java
- `M` protobuff-json-support/src/main/java/io/micronaut/protobuf/json/registry/GrpcServiceRegistrar.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` grpc-client-runtime/src/test/groovy/io/micronaut/grpc/GrpcNamedChannelSpec.groovy
- `A` grpc-client-runtime/src/test/groovy/io/micronaut/grpc/channels/GrpcManagedChannelConfigurationSpec.groovy
- `A` grpc-inprocess/src/test/groovy/io/micronaut/grpc/InProcessGrpcConfigurationSpec.groovy
- `A` grpc-inprocess/src/test/groovy/io/micronaut/grpc/InProcessGrpcServerChannelSpec.groovy
- `A` grpc-inprocess/src/test/groovy/io/micronaut/grpc/InProcessHelloWorldGrpcSpec.groovy
- `A` grpc-inprocess/src/test/groovy/io/micronaut/grpc/server/InProcessGrpcServerBuilderSpec.groovy
- `A` grpc-inprocess/src/test/proto/helloworld.proto
- `A` grpc-inprocess/src/test/resources/example.crt
- `A` grpc-inprocess/src/test/resources/example.key
- `M` grpc-server-runtime/src/test/groovy/io/micronaut/grpc/GrpcServerConfigurationSpec.groovy
- `M` grpc-server-runtime/src/test/groovy/io/micronaut/grpc/server/GrpcServerBuilderSpec.groovy
- `M` protobuff-support/src/test/groovy/io/micronaut/SimpleWebsocketSpec.groovy
- `M` test-suite-java/.mvn/wrapper/maven-wrapper.properties
- `M` test-suite-java/src/main/java/helloworld/HealthService.java
- `A` test-suite-java/src/main/java/helloworld/ReactiveGreetingEndpoint.java
- `M` test-suite-java/src/main/proto/helloworld.proto
- `A` test-suite-java/src/main/proto/reactivehelloworld.proto
- `A` test-suite-java/src/test/java/helloworld/ReactiveGreetingEndpointTest.java
- `A` test-suite-kotlin/src/test/kotlin/helloworld/GreetingServiceFactory.kt
- `M` test-suite-kotlin/src/test/kotlin/helloworld/GreetingServiceTest.kt
- `A` test-suite-kotlin/src/test/kotlin/helloworld/ProjectConfig.kt

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

