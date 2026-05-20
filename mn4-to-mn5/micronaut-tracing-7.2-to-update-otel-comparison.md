Compared micronaut-tracing as mn4 -> mn5.

  Scope

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-tracing, branch 7.2.x, SHA 13e45402133f
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-tracing, branch update-otel, SHA 8888c5509920
  - Same remote, both clean: git@github.com:micronaut-projects/micronaut-tracing.git
  - Report: /private/tmp/micronaut-tracing-7.2-to-update-otel-comparison.md

  Key Findings

  - Major line move: 7.2.1-SNAPSHOT -> 8.0.0-SNAPSHOT.
  - Platform/build upgrade: Micronaut 4.10.4 -> 5.0.0, Platform 4.9.4 -> 5.0.0-RC1, Gradle 8.14.3 -> 9.5.1,
    Java/GraalVM 25.0.1-graal.
  - OpenTelemetry stack updated: core 1.54.1 -> 1.62.0, instrumentation 2.20.1 -> 2.27.0, Brave 6.3.0 ->
    6.3.1, Zipkin 3.5.1 -> 3.6.1.
  - New tracing-opentelemetry-r2dbc module instruments ConnectionFactory beans; toggle is
    otel.instrumentation.r2dbc.enabled.
  - Added OpenTelemetry Logback appender integration and docs for Logback MDC correlation.
  - OpenTelemetry now supports otel.resource.attributes / OTEL_RESOURCE_ATTRIBUTES.
  - OpenTelemetryBuilderCustomizer is now a functional interface and has new SDK customization docs.
  - @NewSpan can now be declared on classes and interfaces, not just methods/annotation types.
  - Zipkin exporter excludes the OkHttp sender transitive dependency.
  - RxJava2 catalog usage was replaced with RxJava3 for tests and catalogs.
  - OpenTracing HTTP filters now set span-kind tags and improve parent selection for nested HTTP requests.
  - Added common vulnerability-audit/OSV files, including an ignore for GHSA-7pwc-h2j2-rjgj.

  Diff size: 115 files changed, 5306 insertions(+), 366 deletions(-).

  I did not run tests; this was a folder comparison and targeted source/build-diff review only.
# Release Note Comparison

Generated: 2026-05-19 14:26 UTC
Comparison: `7.2.x` -> `update-otel`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-tracing` | `7.2.x` | `13e45402133f` | `git@github.com:micronaut-projects/micronaut-tracing.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-tracing` | `update-otel` | `8888c5509920` | `git@github.com:micronaut-projects/micronaut-tracing.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-tracing`
- Commit candidates found: 52
- File changes listed: 115
- Version values listed: 23
- File status counts: A=49, M=66

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `7.2.1-SNAPSHOT` | `8.0.0-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-gradle-plugin` | `io.micronaut.gradle:micronaut-gradle-plugin:4.5.5` | `io.micronaut.gradle:micronaut-gradle-plugin:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-resources` | `io.micronaut.testresources:micronaut-test-resources-bom:2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.27` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.4` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-aws` | `4.11.0` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-data` | `4.13.5` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.5.5` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-grpc` | `4.12.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-kafka` | `not present` | `6.0.0` | `added` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-platform` | `4.9.4` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-r2dbc` | `not present` | `7.0.1-RC1` | `added` |
| `gradle/libs.versions.toml` | `versions.micronaut-reactor` | `3.8.0` | `4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-rxjava2` | `2.8.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-rxjava3` | `not present` | `4.0.0` | `added` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.15.4` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-sql` | `6.2.2` | `7.0.1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.9.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test-resources` | `2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `7094522a91e8` Remove OkHttp sender from Zipkin exporter dependencies (#879) (Nemanja Mikic, 2026-04-28)

### Features

- `ce64e01f6de0` Support OpenTelemetry resource attributes (#867) (Nemanja Mikic, 2026-05-06)
- `0e0123a93a00` Add OpenTelemetry Logback appender integration (#864) (Nemanja Mikic, 2026-04-28)
- `c739e066eb19` Add OpenTelemetry R2DBC instrumentation (#863) (Nemanja Mikic, 2026-04-27)

### Fixes

- `b1670602005d` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.6 (#812) (renovate[bot], 2025-10-17)

### Security

- `8888c5509920` security ignore GHSA-7pwc-h2j2-rjgj (Sergio del Amo, 2026-05-18)

### Dependency Updates

- `cd91de37e983` Update tracing dependency versions (Sergio del Amo, 2026-05-18)
- `0fdb669963be` chore: Bump version to 8.0.0-SNAPSHOT (micronaut-build, 2026-05-08)
- `1f8ad10a5bbc` Update dependency com.squareup.okio:okio to v3 (#849) (renovate[bot], 2026-05-01)
- `1be9cf6cda0a` Update dependency io.zipkin.reporter2:zipkin-reporter-bom to v3.5.3 (#886) (renovate[bot], 2026-05-01)
- `6cfadba19233` Document OpenTelemetry dependency alignment (#874) (Nemanja Mikic, 2026-04-28)
- `14c51cb11e77` Update dependency io.zipkin.brave:brave-bom to v6.3.1 (renovate[bot], 2026-04-28)
- `1b7002ab4929` Update tracing dependencies (Nemanja Mikic, 2026-04-27)
- `d5b793222fbf` chore: Bump version to 8.0.0-SNAPSHOT (micronaut-build, 2026-02-05)

### Internal

- `56460ad1cc46` ci: projectVersion=8.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-10-15)

### Review Candidates

- `129d6d8178c5` micronaut-kafka = "6.0.0" (Sergio del Amo, 2026-05-18)
- `0edad781c735` micronaut-sql = "7.0.1" (Sergio del Amo, 2026-05-18)
- `dbbf7e18df52` micronaut-grpc = "5.0.0" (Sergio del Amo, 2026-05-18)
- `2c80a5408548` Update common files (#893) (micronaut-build, 2026-05-14)
- `3bfd9e56c5c6` Update versions (Sergio del Amo, 2026-05-14)
- `9912f666dd0d` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `59b48641cc58` Fix OpenTracing parent selection for nested HTTP requests (#857) (Nemanja Mikic, 2026-05-12)
- `6a25cc02969f` Document OpenTelemetry SDK customization (#876) (Nemanja Mikic, 2026-05-12)
- `ceaa0df568a2` Avoid NPE when HTTP client telemetry context is missing (#858) (Nemanja Mikic, 2026-05-12)
- `0e99dbb8a2fc` Document OpenTelemetry Logback MDC usage (#878) (Nemanja Mikic, 2026-05-12)
- `2251720f8efb` Update common files (#892) (micronaut-build, 2026-05-09)
- `96654e6a45a6` [skip ci] Release v8.0.0-RC1 (micronaut-build, 2026-05-08)
- `39ec6a4459df` Update versions (#891) (Sergio del Amo, 2026-05-08)
- `d4ac5a946c43` Update actions/checkout action to v6 (#836) (renovate[bot], 2026-05-08)
- `871d20586b0f` Update common files (#890) (micronaut-build, 2026-05-08)
- `a3d650331b91` Update common files (#889) (micronaut-build, 2026-05-05)
- `762c0492bb94` [tracing] Update common files for branch 8.0.x (#888) (micronaut-build, 2026-05-05)
- `4c441dfccabe` Update common files (#887) (micronaut-build, 2026-05-01)
- `45466667f61a` rxjava3 (#875) (Issam Liqali, 2026-04-29)
- `d0399c5c6a91` Assert OpenTelemetry HTTP server span kind (#871) (Nemanja Mikic, 2026-04-28)
- `7f1c0228a9fb` Set OpenTracing HTTP span kind tags (#873) (Nemanja Mikic, 2026-04-28)
- `368b7cf8a9a3` Allow NewSpan on classes and interfaces (#877) (Nemanja Mikic, 2026-04-28)
- `732f3257cca9` Address OpenTelemetry global reuse review feedback (#861) (Nemanja Mikic, 2026-04-28)
- `eb98b86e6424` Merge pull request #854 from micronaut-projects/task-853-renovate-batch (Nemanja Mikic, 2026-04-27)
- `eaae4d2acd40` Update grpc-java to 1.80.0 (Nemanja Mikic, 2026-04-27)
- `46c71054aeff` Merge pull request #835 from micronaut-projects/renovate/opentelemetry-java-monorepo (Nemanja Mikic, 2026-04-27)
- `912968167525` Align OpenTelemetry alpha BOM (Nemanja Mikic, 2026-04-27)
- `87d0a54b610e` Update opentelemetry-java monorepo to v1.61.0 (renovate[bot], 2026-04-27)
- `4b4f65f0983f` Clarify OpenTelemetry annotation import changes (#865) (Nemanja Mikic, 2026-04-27)
- `30688b9d60b6` Update common files (#850) (micronaut-build, 2026-04-26)
- `4b343f4c7c0e` Update common files (#845) (micronaut-build, 2026-02-12)
- `a18304ea4f85` [skip ci] Release v8.0.0-M1 (micronaut-build, 2026-02-05)
- `850882bd9c28` [tracing] Update common files for branch 8.0.x (#813) (micronaut-build, 2026-02-04)
- `32a19731f689` Update to micronaut 5 (#842) (issam liqali, 2026-02-03)
- `6b1bc9850a5d` Update common files (#811) (micronaut-build, 2025-10-17)
- `a9f9014ffae7` Micronaut Gradle build plugin 8.0.0-M4 (Sergio del Amo, 2025-10-15)
- `af5eeca8a2d4` gradle 9.1 (Sergio del Amo, 2025-10-15)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` .github/workflows/update-gradle-wrapper.yml
- `M` buildSrc/build.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.tracing-module.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` settings.gradle
- `M` test-suite-java/build.gradle
- `M` tests/kotlin-tests/build.gradle
- `M` tracing-bom/build.gradle
- `M` tracing-core/build.gradle
- `M` tracing-jaeger/build.gradle
- `M` tracing-opentelemetry-grpc/build.gradle
- `M` tracing-opentelemetry-http/build.gradle
- `M` tracing-opentelemetry-kafka/build.gradle
- `A` tracing-opentelemetry-r2dbc/build.gradle
- `M` tracing-opentelemetry-zipkin-exporter/build.gradle
- `M` tracing-opentelemetry/build.gradle
- `M` tracing-opentracing/build.gradle

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
- `M` src/main/docs/guide/introduction.adoc
- `M` src/main/docs/guide/opentelemetry.adoc
- `M` src/main/docs/guide/opentelemetry/annotations.adoc
- `A` src/main/docs/guide/opentelemetry/customization.adoc
- `M` src/main/docs/guide/opentelemetry/exporters.adoc
- `A` src/main/docs/guide/opentelemetry/logback-mdc.xml
- `A` src/main/docs/guide/opentelemetry/logback.adoc
- `A` src/main/docs/guide/opentelemetry/mdc.adoc
- `A` src/main/docs/guide/opentelemetry/r2dbc.adoc
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
- `M` config/checkstyle/checkstyle.xml
- `A` osv-scanner.toml
- `M` tracing-annotation/src/main/java/io/micronaut/tracing/annotation/NewSpan.java
- `M` tracing-opentelemetry-grpc/src/main/java/io/micronaut/tracing/opentelemetry/instrument/grpc/GrpcClientTracingInterceptorFactory.java
- `M` tracing-opentelemetry-grpc/src/main/java/io/micronaut/tracing/opentelemetry/instrument/grpc/GrpcServerTracingInterceptorFactory.java
- `M` tracing-opentelemetry-http/src/main/java/io/micronaut/tracing/opentelemetry/instrument/http/client/MicronautHttpClientTelemetryFactory.java
- `M` tracing-opentelemetry-http/src/main/java/io/micronaut/tracing/opentelemetry/instrument/http/client/OpenTelemetryClientFilter.java
- `M` tracing-opentelemetry-jdbc/src/main/java/io/micronaut/tracing/opentelemetry/instrument/jdbc/JdbcTelemetryConfiguration.java
- `M` tracing-opentelemetry-kafka/src/main/java/io/micronaut/tracing/opentelemetry/instrument/kafka/MicronautOtelKafkaConsumer.java
- `M` tracing-opentelemetry-kafka/src/main/java/io/micronaut/tracing/opentelemetry/instrument/kafka/MicronautOtelKafkaProducer.java
- `A` tracing-opentelemetry-r2dbc/src/main/java/io/micronaut/tracing/opentelemetry/instrument/r2dbc/R2dbcConnectionFactoryFactory.java
- `A` tracing-opentelemetry-r2dbc/src/main/java/io/micronaut/tracing/opentelemetry/instrument/r2dbc/R2dbcTelemetryConfiguration.java
- `A` tracing-opentelemetry-r2dbc/src/main/java/io/micronaut/tracing/opentelemetry/instrument/r2dbc/package-info.java
- `M` tracing-opentelemetry/src/main/java/io/micronaut/tracing/opentelemetry/DefaultOpenTelemetryFactory.java
- `M` tracing-opentelemetry/src/main/java/io/micronaut/tracing/opentelemetry/OpenTelemetryBuilderCustomizer.java
- `A` tracing-opentelemetry/src/main/java/io/micronaut/tracing/opentelemetry/log/OpenTelemetryLogbackAppenderInstaller.java
- `M` tracing-opentelemetry/src/main/java/io/micronaut/tracing/opentelemetry/xray/SdkClientBuilderListener.java
- `M` tracing-opentracing/src/main/java/io/micronaut/tracing/opentracing/instrument/http/AbstractOpenTracingFilter.java
- `M` tracing-opentracing/src/main/java/io/micronaut/tracing/opentracing/instrument/http/OpenTracingClientFilter.java
- `M` tracing-opentracing/src/main/java/io/micronaut/tracing/opentracing/instrument/http/OpenTracingServerFilter.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `A` test-suite-java/src/test/java/io/micronaut/tracing/opentelemetry/OpenTelemetryBuilderCustomizerExample.java
- `M` test-suite-java/src/test/java/opentelemetry/HttpTracingTest.java
- `A` test-suite-java/src/test/resources/META-INF/native-image/native-image.properties
- `A` tests/kotlin-tests/src/test/kotlin/reactor/OpenTelemetryCoroutineHttpClientSpec.kt
- `M` tracing-brave/src/test/groovy/io/micronaut/tracing/brave/TraceInterceptorSpec.groovy
- `M` tracing-jaeger/src/test/groovy/io/micronaut/tracing/jaeger/HttpTracingSpec.groovy
- `M` tracing-opentelemetry-http/src/test/groovy/io/micronaut/tracing/opentelemetry/instrument/http/OpenTelemetryHttpSpec.groovy
- `A` tracing-opentelemetry-http/src/test/groovy/io/micronaut/tracing/opentelemetry/instrument/http/client/OpenTelemetryClientFilterSpec.groovy
- `M` tracing-opentelemetry-jdbc/src/test/groovy/io/micronaut/tracing/opentelemetry/instrument/jdbc/JdbcTelemetrySpanSpec.groovy
- `M` tracing-opentelemetry-kafka/src/test/groovy/io/micronaut/tracing/opentelemetry/instrument/kafka/KafkaTelemetryIntegrationSpec.groovy
- `M` tracing-opentelemetry-kafka/src/test/groovy/io/micronaut/tracing/opentelemetry/instrument/kafka/MicronautOtelKafkaConsumerSpec.groovy
- `M` tracing-opentelemetry-kafka/src/test/groovy/io/micronaut/tracing/opentelemetry/instrument/kafka/MicronautOtelKafkaProducerSpec.groovy
- `M` tracing-opentelemetry-kafka/src/test/groovy/io/micronaut/tracing/util/KafkaSetup.groovy
- `A` tracing-opentelemetry-r2dbc/src/test/groovy/io/micronaut/tracing/opentelemetry/instrument/r2dbc/R2dbcTelemetryBeanCreationSpec.groovy
- `A` tracing-opentelemetry-r2dbc/src/test/groovy/io/micronaut/tracing/opentelemetry/instrument/r2dbc/R2dbcTelemetrySpanSpec.groovy
- `A` tracing-opentelemetry-r2dbc/src/test/java/io/micronaut/tracing/util/TestDefaultOpenTelemetryFactory.java
- `A` tracing-opentelemetry-r2dbc/src/test/resources/logback-test.xml
- `M` tracing-opentelemetry-zipkin-exporter/src/test/groovy/io/micronaut/tracing/opentelemetry/exporter/zipkin/OtelHttpClientSenderFactorySpec.groovy
- `A` tracing-opentelemetry/src/test/groovy/io/micronaut/tracing/opentelemetry/DefaultOpenTelemetryFactorySpec.groovy
- `A` tracing-opentelemetry/src/test/groovy/io/micronaut/tracing/opentelemetry/OpenTelemetryBuilderCustomizerSpec.groovy
- `A` tracing-opentelemetry/src/test/groovy/io/micronaut/tracing/opentelemetry/OpenTelemetryResourceAttributesSpec.groovy
- `A` tracing-opentelemetry/src/test/groovy/io/micronaut/tracing/opentelemetry/log/OpenTelemetryLogbackAppenderInstallerSpec.groovy
- `M` tracing-opentelemetry/src/test/groovy/io/micronaut/tracing/opentracing/instrument/util/AnnotationMappingSpec.groovy
- `M` tracing-opentelemetry/src/test/groovy/io/micronaut/tracing/opentracing/instrument/util/HttpClientResetForTestSpec.groovy
- `A` tracing-opentracing/src/test/groovy/io/micronaut/tracing/opentracing/instrument/http/OpenTracingServerFilterSpec.groovy

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

