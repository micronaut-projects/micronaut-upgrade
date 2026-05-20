• Generated the comparison in release direction mn4 -> mn5.

  Full report: micronaut-graphql-mn4-to-mn5-comparison.md:1

  Scope: previous 4.9.x at b63159ef72ba, current 5.0.x at e68efca5bc2f; both worktrees are clean. Delta: 55 commits, 85 changed files.

  Release Note Draft

  - Breaking: Removed deprecated Apollo subscriptions-transport-ws support, including io.micronaut.configuration.graphql.ws.apollo.* classes and graphql.graphql-apollo-ws configuration. Users should migrate to the current
    graphql-ws protocol with graphql.graphql-ws.enabled.
  - Breaking: GraphiQLController no longer uses the deprecated GraphQLApolloWsConfiguration; it now uses the current GraphQL websocket configuration.
  - Breaking candidate: Removed deprecated JacksonGraphQLJsonSerializer(ObjectMapper) constructor.
  - Fix: Malformed GraphQL JSON request bodies and malformed variables JSON now return HTTP 400 Bad Request.
  - Docs: Websocket docs now describe only the current graphql-ws protocol; Apollo websocket docs were removed.

  Dependency Updates

  - GraphQL Java 22.4 -> 26.0
  - GraphQL Java Extended Scalars 22.0 -> 24.0
  - Micronaut Core 4.10.4 -> 5.0.0-RC2
  - Micronaut Platform 4.9.4 -> 5.0.0-M3
  - Micronaut Security 4.15.0 -> 5.0.0-M2
  - Micronaut Serde 2.15.5 -> 3.0.0-RC1
  - Micronaut Reactor 3.9.0 -> 4.0.0-RC1
  - Gradle wrapper 8.14.3 -> 9.5.0
  - Micronaut Gradle plugin 4.5.5 -> 5.0.0-M1
  - Shadow plugin 8.3.7 -> 9.4.1
  - Graal SVM 24.2.1 -> 25.0.3

  I did not run tests; this was a comparison/reporting pass only.


# Release Note Comparison

Generated: 2026-05-06 15:56 UTC
Comparison: `mn4` -> `mn5`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-graphql` | `4.9.x` | `b63159ef72ba` | `git@github.com:micronaut-projects/micronaut-graphql.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-graphql` | `5.0.x` | `e68efca5bc2f` | `git@github.com:micronaut-projects/micronaut-graphql.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-graphql`
- Commit candidates found: 55
- File changes listed: 85
- Version values listed: 26
- File status counts: A=17, D=21, M=46, R=1

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `4.9.0-SNAPSHOT` | `5.0.0-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.graal-svm` | `org.graalvm.nativeimage:svm:24.2.1` | `org.graalvm.nativeimage:svm:25.0.3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-gradle-plugin` | `io.micronaut.gradle:micronaut-gradle-plugin:4.5.5` | `io.micronaut.gradle:micronaut-gradle-plugin:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-kotlin` | `io.micronaut.kotlin:micronaut-kotlin-bom:4.7.0` | `io.micronaut.kotlin:micronaut-kotlin-bom:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-reactor` | `io.micronaut.reactor:micronaut-reactor-bom:3.9.0` | `io.micronaut.reactor:micronaut-reactor-bom:4.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-security` | `io.micronaut.security:micronaut-security-bom:4.15.0` | `io.micronaut.security:micronaut-security-bom:5.0.0-M2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.15.5` | `io.micronaut.serde:micronaut-serde-bom:3.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.shadow-plugin` | `com.gradleup.shadow:com.gradleup.shadow.gradle.plugin (version.ref=shadow)` | `com.gradleup.shadow:com.gradleup.shadow.gradle.plugin (version.ref=shadow)` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.graal-svm` | `24.2.1` | `25.0.3` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-graphql-java` | `22.4` | `26.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-graphql-java-extended-scalars` | `22.0` | `24.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-graphql-java-tools` | `14.0.1` | `14.0.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-graphql-spqr` | `0.12.4` | `0.12.4` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.4` | `5.0.0-RC2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.5.5` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-kotlin` | `4.7.0` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-platform` | `4.9.4` | `5.0.0-M3` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-reactor` | `3.9.0` | `4.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-security` | `4.15.0` | `5.0.0-M2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.15.5` | `3.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.9.0` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.0` | `changed` |
| `settings.gradle` | `plugin.io.micronaut.build.shared.settings` | `7.6.4` | `8.0.0-M18` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `17390de94f05` Remove Spock version force configuration (#689) (Issam Liqali, 2026-04-29)

### Fixes

- `300325d0beae` fix(deps): update dependency com.graphql-java:graphql-java to v26 (#710) (renovate[bot], 2026-04-30)
- `172cd15780d2` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m24 (#694) (renovate[bot], 2026-04-23)
- `3b162cdf18f0` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m17 (#691) (renovate[bot], 2026-03-16)
- `82e6482c0a07` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m16 (#684) (renovate[bot], 2026-03-12)
- `f7c40627f319` fix(deps): update dependency org.graalvm.nativeimage:svm to v25.0.2 (#680) (renovate[bot], 2026-02-12)
- `eb34ec19a9d4` fix(deps): update dependency io.micronaut.security:micronaut-security-bom to v4.16.1 (#675) (renovate[bot], 2026-02-12)
- `cbffebb986f6` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.2 (#681) (renovate[bot], 2026-02-09)
- `e70f8ff204f6` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m2 (#678) (renovate[bot], 2026-02-09)
- `ebca1260c5e1` fix(deps): update dependency com.gradleup.shadow:com.gradleup.shadow.gradle.plugin to v9.3.1 (#677) (renovate[bot], 2026-02-09)
- `b61f3a711d2b` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m10 (#671) (renovate[bot], 2026-02-09)
- `6e7af9bdb085` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m3 (#667) (renovate[bot], 2025-12-15)
- `cb2a6a2eb2ec` fix(deps): update dependency io.micronaut.security:micronaut-security-bom to v4.16.0 (#663) (renovate[bot], 2025-12-10)
- `49db7fa39e61` fix(deps): update dependency com.gradleup.shadow:com.gradleup.shadow.gradle.plugin to v9 (#655) (renovate[bot], 2025-12-10)
- `7544d7e0ea6b` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#654) (renovate[bot], 2025-12-10)
- `cfa8a8108fbc` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.1 (#653) (renovate[bot], 2025-12-10)
- `bcfa8a26cb5b` fix(deps): update dependency io.micronaut.reactor:micronaut-reactor-bom to v3.9.1 (#652) (renovate[bot], 2025-12-10)
- `6028486d97f4` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#651) (renovate[bot], 2025-12-10)
- `5f28346b1c9b` fix(deps): update dependency com.gradleup.shadow:com.gradleup.shadow.gradle.plugin to v8.3.9 (#650) (renovate[bot], 2025-12-10)
- `84ac02354262` fix(deps): update dependency org.graalvm.nativeimage:svm to v25 (#645) (renovate[bot], 2025-12-10)

### Security

- `6d049684aa65` micronaut-security = "5.0.0-M2" (Sergio del Amo, 2026-05-06)

### Dependency Updates

- `191183cc06fe` chore(deps): combine renovate dependency batch (#721) (Graeme Rocher, 2026-05-04)
- `013d2f82705b` chore(deps): combine renovate dependency batch (#713) (Graeme Rocher, 2026-04-30)
- `bd7e6ef08369` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#683) (renovate[bot], 2026-03-12)
- `3c63b183ad94` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-02-10)
- `5fe479b92244` chore(deps): update gradle to v9.2.1 (#659) (renovate[bot], 2025-12-10)
- `37f974b36914` chore(deps): update softprops/action-gh-release action to v2.5.0 (#661) (renovate[bot], 2025-12-10)
- `2be719409297` chore(deps): update mikepenz/action-junit-report action to v6 (#660) (renovate[bot], 2025-12-10)
- `3f056726731f` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#658) (renovate[bot], 2025-12-10)
- `a625d0512658` chore(deps): update graalvm/setup-graalvm action to v1.4.4 (#657) (renovate[bot], 2025-12-10)

### Internal

- `ef74b7d664fc` Build: Update to Micronaut 5 (#668) (issam liqali, 2025-12-15)

### Review Candidates

- `e68efca5bc2f` update shadow plugin (Sergio del Amo, 2026-05-06)
- `09e863822941` micronaut-serde = "3.0.0-RC1" (Sergio del Amo, 2026-05-06)
- `7cc0d1a7f8ae` micronaut-reactor = "4.0.0-RC1" (Sergio del Amo, 2026-05-06)
- `68643863c51b` micronaut-kotlin = "5.0.0-M1" (Sergio del Amo, 2026-05-06)
- `f76161695177` micronaut-gradle-plugin = "5.0.0-M1" (Sergio del Amo, 2026-05-06)
- `45b2e5f4573b` micronaut-platform = "5.0.0-M3" (Sergio del Amo, 2026-05-06)
- `c46ad8d70b94` micronaut = "5.0.0-RC2" (Sergio del Amo, 2026-05-06)
- `575958dda7db` Update common files (#722) (micronaut-build, 2026-05-06)
- `e06dfe30385c` Update common files (#717) (micronaut-build, 2026-05-04)
- `e1d0ef2532a4` Update common files (#715) (micronaut-build, 2026-05-01)
- `cba086bf13ce` Update common files (#690) (micronaut-build, 2026-04-30)
- `3584662ea192`  Return 400 for malformed GraphQL JSON requests (#699) (Issam Liqali, 2026-04-30)
- `f22b9b79c14a` Update common files (#687) (micronaut-build, 2026-03-12)
- `2595abfc6eb8` [skip ci] Release v5.0.0-M1 (micronaut-build, 2026-02-10)
- `16be30d97864` [graphql] Update common files for branch 5.0.x (#672) (micronaut-build, 2026-02-09)
- `4c8163d0fbbc` update graphql java to 25.0 (#674) (issam liqali, 2026-02-03)
- `ca723c87af85` Update common files (#649) (micronaut-build, 2025-12-10)
- `15a3a96908c9` Replace Micronaut nullability annotations with JSpecify nullability annotations (#665) (Copilot, 2025-12-01)
- `8dcc54effe0b` Update common files (#648) (micronaut-build, 2025-10-17)
- `4a4364f25d04` Micronaut Build Gradle Plugin 8.0.0-M4 (Sergio del Amo, 2025-10-15)
- `e4d21f55406f` gradle 9.1 (Sergio del Amo, 2025-10-15)
- `900366b16ea8` Merge branch '4.9.x' into 5.0.x (Sergio del Amo, 2025-10-15)
- `448bc70cdfc5` Merge branch '4.8.x' into 5.0.x (Sergio del Amo, 2025-06-17)
- `6f27d9b48881` breaks: del and doc deprecations for MN5 (#517) (Dean Wette, 2024-04-10)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` buildSrc/build.gradle
- `M` buildSrc/src/main/groovy/micronaut-graphql.example-conventions.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` settings.gradle

### Documentation

- `A` .agents/skills/docs/SKILL.md
- `A` .agents/skills/docs/references/control-panel-patterns.md
- `A` .agents/skills/docs/references/micronaut-docs-providers.md
- `M` .github/workflows/release.yml
- `M` docs-examples/hello-world-groovy/build.gradle
- `M` docs-examples/hello-world-kotlin/build.gradle
- `M` src/main/docs/guide/breaks.adoc
- `M` src/main/docs/guide/configuration/graphql-ws.adoc

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
- `M` examples/chat/src/main/java/example/graphql/FromCustomizer.java
- `M` examples/chat/src/main/resources/application.yml
- `M` examples/jwt-security/src/main/java/example/graphql/CurrentUserDataFetcher.java
- `M` examples/jwt-security/src/main/java/example/graphql/LoginPayload.java
- `M` examples/jwt-security/src/main/java/example/graphql/RequestResponseCustomizer.java
- `M` examples/jwt-security/src/main/java/example/security/AuthenticationProviderUserPassword.java
- `M` graphql/src/main/java/io/micronaut/configuration/graphql/DefaultGraphQLExecutionInputCustomizer.java
- `M` graphql/src/main/java/io/micronaut/configuration/graphql/DefaultGraphQLInvocation.java
- `M` graphql/src/main/java/io/micronaut/configuration/graphql/GraphQLController.java
- `M` graphql/src/main/java/io/micronaut/configuration/graphql/GraphQLExecutionInputCustomizer.java
- `M` graphql/src/main/java/io/micronaut/configuration/graphql/GraphQLInvocation.java
- `M` graphql/src/main/java/io/micronaut/configuration/graphql/GraphQLInvocationData.java
- `M` graphql/src/main/java/io/micronaut/configuration/graphql/GraphQLResponseBodyDeserializer.java
- `M` graphql/src/main/java/io/micronaut/configuration/graphql/GraphiQLController.java
- `M` graphql/src/main/java/io/micronaut/configuration/graphql/ws/Message.java
- `D` graphql/src/main/java/io/micronaut/configuration/graphql/ws/apollo/GraphQLApolloWsConfiguration.java
- `D` graphql/src/main/java/io/micronaut/configuration/graphql/ws/apollo/GraphQLApolloWsController.java
- `D` graphql/src/main/java/io/micronaut/configuration/graphql/ws/apollo/GraphQLApolloWsKeepAlive.java
- `D` graphql/src/main/java/io/micronaut/configuration/graphql/ws/apollo/GraphQLApolloWsMessageHandler.java
- `D` graphql/src/main/java/io/micronaut/configuration/graphql/ws/apollo/GraphQLApolloWsOperations.java
- `D` graphql/src/main/java/io/micronaut/configuration/graphql/ws/apollo/GraphQLApolloWsRequest.java
- `D` graphql/src/main/java/io/micronaut/configuration/graphql/ws/apollo/GraphQLApolloWsResponse.java
- `D` graphql/src/main/java/io/micronaut/configuration/graphql/ws/apollo/GraphQLApolloWsSender.java
- `D` graphql/src/main/java/io/micronaut/configuration/graphql/ws/apollo/GraphQLApolloWsState.java
- `D` graphql/src/main/java/io/micronaut/configuration/graphql/ws/apollo/RequiresGraphQLApolloWs.java
- `D` graphql/src/main/java/io/micronaut/configuration/graphql/ws/apollo/package-info.java
- `M` graphql/src/main/resources/META-INF/native-image/io.micronaut.graphql/micronaut-graphql/reflect-config.json

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` graphql/src/test/groovy/io/micronaut/configuration/graphql/GraphQLControllerSpec.groovy
- `R095` graphql/src/test/groovy/io/micronaut/configuration/graphql/ws/GraphQLWsFactory.groovy
- `M` graphql/src/test/groovy/io/micronaut/configuration/graphql/ws/GraphQLWsHandlerSpec.groovy
- `M` graphql/src/test/groovy/io/micronaut/configuration/graphql/ws/MessageSpec.groovy
- `D` graphql/src/test/groovy/io/micronaut/configuration/graphql/ws/apollo/GraphQLApolloWsClient.groovy
- `D` graphql/src/test/groovy/io/micronaut/configuration/graphql/ws/apollo/GraphQLApolloWsConfigurationSpec.groovy
- `D` graphql/src/test/groovy/io/micronaut/configuration/graphql/ws/apollo/GraphQLApolloWsControllerSpec.groovy
- `D` graphql/src/test/groovy/io/micronaut/configuration/graphql/ws/apollo/GraphQLApolloWsKeepAliveSpec.groovy
- `D` graphql/src/test/groovy/io/micronaut/configuration/graphql/ws/apollo/GraphQLApolloWsRequestSpec.groovy
- `D` graphql/src/test/groovy/io/micronaut/configuration/graphql/ws/apollo/GraphQLApolloWsResponseSpec.groovy
- `D` graphql/src/test/groovy/io/micronaut/configuration/graphql/ws/apollo/GraphQLApolloWsSerializationSpec.groovy
- `D` graphql/src/test/resources/application-apollows.yml
- `D` graphql/src/test/resources/application-keepalive.yml
- `M` test-suite-graal/src/test/java/example/micronaut/BookTest.java
- `D` test-suite-graal/src/test/java/example/micronaut/apollo/ws/GraphQLApolloWsClient.java

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

