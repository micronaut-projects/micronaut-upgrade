Compared micronaut-mcp as mn4 → mn5.

  Scope

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-mcp, branch 0.0.x, SHA 67a78c509a68
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-mcp, branch 1.0.x, SHA d391171b187a
  - Same remote, both clean: git@github.com:micronaut-projects/micronaut-mcp.git
  - Report: /private/tmp/micronaut-mcp-0.0-to-1.0-comparison.md

  Key Findings

  - Major line move: projectVersion 0.0.21-SNAPSHOT → 1.0.1-SNAPSHOT.
  - Platform upgrade: Micronaut 4.10.16 → 5.0.0, Micronaut Platform 4.10.8 → 5.0.0-RC1, Gradle wrapper 8.14.3
    → 9.5.1, Micronaut Gradle plugin 4.5.5 → 5.0.0-M1.
  - MCP Java SDK moved from io.modelcontextprotocol.sdk:mcp-core 0.17.0 → 1.1.2; code adapts to newer SDK
    APIs such as CallToolResult.builder().
  - Jackson/Micronaut Serde migration is visible: Jackson 3 package/API changes, JsonProcessingException
    replaced with JacksonException, and extra MCP schema serde imports added.
  - JSpecify annotations replace Micronaut nullability annotations across many public/internal classes.
  - Eager singleton support improved: the disabled eager singleton annotation test is enabled, and docs
    removed warnings saying annotated prompts/resources/resource templates/tools do not work with eager
    singleton initialization.
  - HTTP behavior coverage added: authenticated GET /mcp is now tested to return 405 METHOD_NOT_ALLOWED.
  - Build/test cleanup includes JUnit 6 selection and a new shared buildSrc mcp-test-java test plugin for
    TCK-style suites.
  - Remaining churn is mostly common files, CI/workflow updates, package-info additions, checkstyle
    suppressions, and .agents/skills additions.

  Diff size: 129 files changed, 3876 insertions(+), 291 deletions(-).

  I did not run tests; this was a folder comparison and targeted source/build-diff review only.

# Release Note Comparison

Generated: 2026-05-19 13:33 UTC
Comparison: `0.0.x` -> `1.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-mcp` | `0.0.x` | `67a78c509a68` | `git@github.com:micronaut-projects/micronaut-mcp.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-mcp` | `1.0.x` | `d391171b187a` | `git@github.com:micronaut-projects/micronaut-mcp.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-mcp`
- Commit candidates found: 135
- File changes listed: 129
- Version values listed: 22
- File status counts: A=29, M=100

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `0.0.21-SNAPSHOT` | `1.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.gradle-micronaut` | `io.micronaut.gradle:micronaut-gradle-plugin:4.5.5` | `io.micronaut.gradle:micronaut-gradle-plugin:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-mcp-java-sdk` | `io.modelcontextprotocol.sdk:mcp-core:0.17.0` | `io.modelcontextprotocol.sdk:mcp-core:1.1.2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test` | `not present` | `micronaut-test:5.0.0` | `added` |
| `gradle/libs.versions.toml` | `libraries.micronaut-validation` | `io.micronaut.validation:micronaut-validation-bom:4.12.0` | `io.micronaut.validation:micronaut-validation-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.27` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.jsonassert` | `1.5.3` | `1.5.3` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-mcp-java-sdk` | `0.17.0` | `1.1.2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.16` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.5.5` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-json-schema` | `1.7.4` | `2.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-langchain4j` | `1.4.2` | `2.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.3` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-platform` | `4.10.8` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-security` | `4.16.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.16.2` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.10.2` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.12.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `b4cccd9b5544` checkstyle: remove extra blank line (Sergio del Amo, 2026-04-08)
- `3559e70eeba8` remove micronaut-docs supplied by MN Build Gradle (Sergio del Amo, 2025-12-09)
- `b84158861ba8` remove micronaut-test supplied by MN Build Gradle (Sergio del Amo, 2025-12-09)
- `d4bb21948189` remove groovy supplied by MN Build Gradle (Sergio del Amo, 2025-12-09)
- `69b21aa261ed` remove spock supplied by MN Build Gradle (Sergio del Amo, 2025-12-09)
- `a3572328e1fd` remove micronaut-docs, micronaut-test, groovy and spock (Sergio del Amo, 2025-11-07)

### Features

- `8108c04fccd1` add suppresions back (Sergio del Amo, 2026-05-18)
- `1ce84725f756` add checkstyle suppressions back (Sergio del Amo, 2026-05-07)
- `b3721e760dfa` add supressions back (Sergio del Amo, 2026-04-29)
- `1feae24dde0e` add package info files (Sergio del Amo, 2025-11-07)
- `5b55c39c39a1` add ack suppressions (Sergio del Amo, 2025-10-28)

### Fixes

- `c15bbd216ee6` fix(deps): update micronaut dependencies (#182) (renovate[bot], 2026-05-01)
- `17dc3ce34d67` fix(deps): update dependency io.modelcontextprotocol.sdk:mcp-core to v1.1.2 (#177) (renovate[bot], 2026-04-29)
- `748fa52d6d43` fix(deps): update micronaut dependencies (#178) (renovate[bot], 2026-04-29)
- `bfe684ab300c` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m20 (#169) (renovate[bot], 2026-04-08)
- `f4e3170ef52b` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m6 (#171) (renovate[bot], 2026-04-08)
- `2449f95a22b7` fix(deps): update dependency io.micronaut.jsonschema:micronaut-json-schema-bom to v2.0.0-m8 (#172) (renovate[bot], 2026-04-08)
- `feee5dd45fda` fix(deps): update dependency io.modelcontextprotocol.sdk:mcp-core to v1.1.1 (#173) (renovate[bot], 2026-04-08)
- `d57e785d778c` fix(deps): update dependency io.modelcontextprotocol.sdk:mcp-core to v1.1.0 (#164) (renovate[bot], 2026-03-25)
- `6f5aea96eff9` fix(deps): update dependency io.micronaut.langchain4j:micronaut-langchain4j-bom to v1.5.0 (#157) (renovate[bot], 2026-03-25)
- `f3be848275f4` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m17 (#156) (renovate[bot], 2026-03-25)
- `66bdc5716044` fix(deps): update dependency io.micronaut.test:micronaut-test-bom to v5.0.0-m7 (#161) (renovate[bot], 2026-03-25)
- `5c9548f96580` fix(deps): update dependency io.micronaut.jsonschema:micronaut-json-schema-bom to v2.0.0-m7 (#159) (renovate[bot], 2026-03-25)
- `57663d13afdf` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m3 (#166) (renovate[bot], 2026-03-25)
- `12032b0196c5` fix(mcp-server): uses correct argumentType for toolarg (#145) (Aliaksei, 2026-02-25)
- `d642bb9b4f3a` fix(build): update testFramework to JUnit 6 (#144) (Aliaksei, 2026-02-20)
- `5bccff57a2d0` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m2 (#139) (renovate[bot], 2026-02-20)
- `b14fd03d00a5` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m13 (#143) (renovate[bot], 2026-02-20)
- `61074be6ce7e` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.2 (#147) (renovate[bot], 2026-02-20)
- `38dc76aa37c6` fix(deps): update dependency io.micronaut.logging:micronaut-logging-bom to v1.7.3 (#148) (renovate[bot], 2026-02-20)
- `e36efbe86d67` fix(deps): update dependency io.micronaut.security:micronaut-security-bom to v4.17.1 (#149) (renovate[bot], 2026-02-20)
- `6207eeae7ca5` fix(deps): update dependency io.micronaut.langchain4j:micronaut-langchain4j-bom to v1.5.0 (#151) (renovate[bot], 2026-02-20)
- `d1b26f567cf4` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m8 (#129) (renovate[bot], 2026-01-13)
- `ed2880c8bee4` fix(deps): update dependency io.micronaut.security:micronaut-security-bom to v4.16.1 (#134) (renovate[bot], 2026-01-13)
- `8d994ae9673a` fix(deps): update dependency io.micronaut.jsonschema:micronaut-json-schema-bom to v1.7.4 (#136) (renovate[bot], 2026-01-13)
- `72a99007391d` fix(deps): update dependency io.modelcontextprotocol.sdk:mcp-core to v0.17.1 (#137) (renovate[bot], 2026-01-13)
- `2a4135c911c2` fix(deps): update dependency io.modelcontextprotocol.sdk:mcp-core to v0.17.0 (#115) (renovate[bot], 2025-12-09)
- `174591bb078e` fix(deps): update dependency io.micronaut.langchain4j:micronaut-langchain4j-bom to v1.4.2 (#114) (renovate[bot], 2025-12-09)
- `37edba329ca1` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#117) (renovate[bot], 2025-12-09)
- `1d3989f7316c` fix(deps): update dependency io.micronaut.security:micronaut-security-bom to v4.16.0 (#124) (renovate[bot], 2025-12-09)
- `66f485038b92` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#108) (renovate[bot], 2025-11-12)
- `4c5f639647fd` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.8 (#102) (renovate[bot], 2025-11-07)
- `77e09389719f` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.6 (#92) (renovate[bot], 2025-10-17)

### Security

- `2a36cdd8fb79` test: 405 /mcp GET authenticated (#105) (Sergio del Amo, 2025-11-12)

### Dependency Updates

- `d391171b187a` chore: Bump version to 1.0.1-SNAPSHOT (micronaut-build, 2026-05-18)
- `7292d64fb3ff` chore: Bump version to 1.0.0-SNAPSHOT (micronaut-build, 2026-05-07)
- `7d6a6fdcd18b` chore(deps): update gradle to v9.5.0 (#179) (renovate[bot], 2026-04-29)
- `9c28d14f62b7` chore(deps): update actions/cache digest to 27d5ce7 (#176) (renovate[bot], 2026-04-22)
- `8564bbd442c4` chore: Bump version to 1.0.0-SNAPSHOT (micronaut-build, 2026-04-08)
- `c607dd291501` chore(deps): update github artifact actions (#158) (renovate[bot], 2026-03-25)
- `5b62fb204cd4` chore(deps): update gradle to v9.4.1 (#160) (renovate[bot], 2026-03-25)
- `ee3a5edcbd8f` chore(deps): update softprops/action-gh-release action to v2.6.1 (#162) (renovate[bot], 2026-03-25)
- `ac94a306842e` chore(deps): update gradle/actions action to v6 (#165) (renovate[bot], 2026-03-25)
- `45f2f59d9ba7` chore: Bump version to 1.0.0-SNAPSHOT (micronaut-build, 2026-02-25)
- `ea514ff901e9` chore(deps): update gradle to v9.3.1 (#141) (renovate[bot], 2026-02-20)
- `fcf44079f8b9` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#146) (renovate[bot], 2026-02-20)
- `a758c9495caf` chore(deps): update github artifact actions (#132) (renovate[bot], 2026-01-13)
- `8d0c95939ddd` chore(deps): update actions/cache action to v5 (#130) (renovate[bot], 2026-01-13)
- `32d459ed573a` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m14 (#131) (renovate[bot], 2026-01-13)
- `de8f1b8e348b` chore(deps): update graalvm/setup-graalvm action to v1.4.5 (#135) (renovate[bot], 2026-01-13)
- `f2f2ba3ceb25` chore: Bump version to 1.0.0-SNAPSHOT (micronaut-build, 2025-12-09)
- `7177f879ef24` chore(deps): update gradle to v9.2.1 (#113) (renovate[bot], 2025-12-09)
- `79c3d672b7fb` chore(deps): update actions/checkout action to v6 (#116) (renovate[bot], 2025-12-09)
- `c1001be22185` chore(deps): update gradle/actions action to v5 (#118) (renovate[bot], 2025-12-09)
- `c21c2ec94a0b` chore(deps): update graalvm/setup-graalvm action to v1.4.4 (#119) (renovate[bot], 2025-12-09)
- `f86db9e1ad00` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#120) (renovate[bot], 2025-12-09)
- `25f324110c04` chore(deps): update softprops/action-gh-release action to v2.5.0 (#123) (renovate[bot], 2025-12-09)
- `70966eb3ad0d` chore(deps): update stefanzweifel/git-auto-commit-action action to v7 (#125) (renovate[bot], 2025-12-09)
- `dee2f7d593d1` chore(deps): update softprops/action-gh-release action to v2.4.2 (#107) (renovate[bot], 2025-11-12)
- `4c7e0cc68248` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m9 (#100) (renovate[bot], 2025-11-07)
- `ad53a8c2513e` chore(deps): update gradle to v9.2.0 (#103) (renovate[bot], 2025-11-07)
- `cca2e4ca859f` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#98) (renovate[bot], 2025-10-28)

### Internal

- `ad7ed843b4d3` build: io.micronaut.build.internal.java-base (Sergio del Amo, 2025-10-28)

### Review Candidates

- `180abda7e24a` [skip ci] Release v1.0.0 (micronaut-build, 2026-05-18)
- `674e4caf4104` micronaut-langchain4j = "2.0.0" (Sergio del Amo, 2026-05-18)
- `56aa7bd3e4a0` update versions (Sergio del Amo, 2026-05-18)
- `e779e9411307` micronaut-test = "5.0.0" (Sergio del Amo, 2026-05-17)
- `4ca67be3c3fb` Update common files (#185) (micronaut-build, 2026-05-14)
- `563e930f223e` Update versions (Sergio del Amo, 2026-05-14)
- `4b1d3c1660c6` micronaut-platform = "5.0.0-RC1" (Sergio del Amo, 2026-05-13)
- `fb4f505a1e08` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `4675f18da08a` Update common files (#184) (micronaut-build, 2026-05-13)
- `183ead4fe872` [skip ci] Release v1.0.0-RC1 (micronaut-build, 2026-05-07)
- `61748302e1cc` micronaut-langchain4j = "2.0.0-RC1" (Sergio del Amo, 2026-05-07)
- `55769121a7ec` update to latest versions (Sergio del Amo, 2026-05-07)
- `7a328fe183d8` Update common files (#181) (micronaut-build, 2026-05-07)
- `9a040f314b60` micronaut-gradle-plugin = "5.0.0-M1" (Sergio del Amo, 2026-04-29)
- `2a6b35a825f2` micronaut-platform = "5.0.0-M2" (Sergio del Amo, 2026-04-29)
- `75c28733cde7` Update common files (#180) (micronaut-build, 2026-04-29)
- `86e949cbe391` Update common files (#175) (micronaut-build, 2026-04-22)
- `024dc9076852` [skip ci] Release v1.0.0-M3 (micronaut-build, 2026-04-08)
- `5ffc21dcfff6` javadoc: add Javadoc in McpIntrospection (Sergio del Amo, 2026-04-08)
- `6ee4584aa1e2` javadoc: add return (Sergio del Amo, 2026-04-08)
- `0c0b82db59e5` checkstyle: StdioServerTransportProviderReplacement.java (Sergio del Amo, 2026-04-08)
- `05b2c581c867` Update to Micronaut M20 (#174) (Issam Liqali, 2026-04-08)
- `91b9aa59a8aa` Update common files (#170) (micronaut-build, 2026-04-08)
- `77d44d677021` Jackson 3 API break getFieldName → getPropertyName (Sergio del Amo, 2026-03-25)
- `268726e18719` change package for InvalidFormatException (Sergio del Amo, 2026-03-25)
- `e7aa0e7adbab` replace JsonProcessingException (Sergio del Amo, 2026-03-25)
- `4194d0fac7df` micronaut-langchain4j = "2.0.0-M1" (Sergio del Amo, 2026-03-25)
- `1e3ed09c0891` [mcp] Update common files for branch 1.0.x (#155) (micronaut-build, 2026-03-25)
- `8f488f22e1f6` [skip ci] Release v1.0.0-M2 (micronaut-build, 2026-02-25)
- `851050f7ca6e` Java MCP SDK 1.0.0 (#154) (Sergio del Amo, 2026-02-25)
- `46f2e56053b9` eager initialization of singletons now works (Sergio del Amo, 2026-02-25)
- `16291912e896` Merge branch '0.0.x' into 1.0.x (Sergio del Amo, 2026-02-25)
- `7c18ec339a33` Update to micronaut 5 (#150) (issam liqali, 2026-02-25)
- `1b2ff910bc96` [mcp] Update common files for branch 1.0.x (#140) (micronaut-build, 2026-02-20)
- `a3a5633a4fcb` [mcp] Update common files for branch 1.0.x (#128) (micronaut-build, 2026-01-13)
- `8035f4415cc7` [skip ci] Release v1.0.0-M1 (micronaut-build, 2025-12-09)
- `fd09e961035b` disabled test (Sergio del Amo, 2025-12-09)
- `7a5f1d02cb34` tool execution result (Sergio del Amo, 2025-12-09)
- `7b3af8acafe6` use emoji in assertion (Sergio del Amo, 2025-12-09)
- `ad7435d0df1c` use micronaut nullability annoation (Sergio del Amo, 2025-12-09)
- `3bc234e54242` fix override (Sergio del Amo, 2025-12-09)
- `99f937afbfbd` jspecify nullability annotations (Sergio del Amo, 2025-12-09)
- `ac49ab9d0a40` micronaut = "5.0.0-M2" (Sergio del Amo, 2025-12-09)
- `0d67f81d35b4` micronaut-serde = "3.0.0-M1" (Sergio del Amo, 2025-12-09)
- `37725e2bc674` buildSrc/gradle.properties (Sergio del Amo, 2025-12-09)
- `b414a33e9039` micronaut-validation = "5.0.0-M1" (Sergio del Amo, 2025-12-09)
- `abb77fbec2c6` [mcp] Update common files for branch 1.0.x (#112) (micronaut-build, 2025-12-09)
- `57b351a0ef44` [WIP] Replace Micronaut nullability annotations with JSpecify annotations (#122) (Copilot, 2025-12-02)
- `6de2313bc3b2` [mcp] Update common files for branch 1.0.x (#106) (micronaut-build, 2025-11-12)
- `921667b6da0d` Merge branch '0.0.x' into 1.0.x (Sergio del Amo, 2025-11-07)
- `46664ad63ccc` micronaut gradle plugin 4.6.1 (Sergio del Amo, 2025-11-07)
- `afe09a55b422` micronaut-platform = "4.10.1" (Sergio del Amo, 2025-11-07)
- `874fcbde7603` [mcp] Update common files for branch 1.0.x (#101) (micronaut-build, 2025-11-07)
- `4e8cef6f7024` extract mcp-test-java (Sergio del Amo, 2025-10-28)
- `0c42631ad7b2` 8.0.0-M6 (Sergio del Amo, 2025-10-28)
- `50b78afeab50` Merge branch '0.0.x' into 1.0.x (Sergio del Amo, 2025-10-28)
- `36786daf08da` Update common files (#96) (micronaut-build, 2025-10-28)
- `b4685a49340b` Update common files (#93) (micronaut-build, 2025-10-20)
- `2e037b52ffa6` Update common files (#90) (micronaut-build, 2025-10-16)
- `71f0bcf324f1` Micronaut Gradle Build Plugin 8.0.0-M4 (Sergio del Amo, 2025-10-15)
- `6bcfa2af76ae` use 1-9 pattern (Sergio del Amo, 2025-10-15)
- `33c919c47562` gradle 9.1 (Sergio del Amo, 2025-10-15)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` .github/workflows/update-gradle-wrapper.yml
- `A` buildSrc/src/main/groovy/io.micronaut.build.internal.mcp-test-java.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` micronaut-mcp-client-java-sdk/build.gradle.kts
- `M` micronaut-mcp-client-langchain4j/build.gradle.kts
- `M` micronaut-mcp-server-java-sdk/build.gradle.kts
- `M` micronaut-mcp/build.gradle.kts
- `M` settings.gradle
- `M` test-suite-graal/build.gradle.kts
- `M` test-suite-jackson-databind/build.gradle.kts
- `M` test-suite-mcp-http-tck-async/build.gradle.kts
- `M` test-suite-mcp-http-tck-common/build.gradle.kts
- `M` test-suite-mcp-http-tck-sync/build.gradle.kts
- `M` test-suite-mcp-http-tck/build.gradle.kts
- `M` test-suite-moon/build.gradle.kts

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
- `M` src/main/docs/guide/server/primitives/prompts/promptAnnotation.adoc
- `M` src/main/docs/guide/server/primitives/resources/resourceAnnotation.adoc
- `M` src/main/docs/guide/server/primitives/resources/resourcesTemplates/resourceTemplateAnnotation.adoc
- `M` src/main/docs/guide/server/primitives/tools/toolAnnotation.adoc

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
- `M` config/checkstyle/suppressions.xml
- `M` micronaut-mcp-annotations/src/main/java/io/micronaut/mcp/annotations/Prompt.java
- `M` micronaut-mcp-client-java-sdk/src/main/java/io/micronaut/mcp/client/javasdk/McpClientHttpFactory.java
- `A` micronaut-mcp-client-java-sdk/src/main/java/io/micronaut/mcp/client/javasdk/package-info.java
- `A` micronaut-mcp-client-langchain4j/src/main/java/io/micronaut/mcp/client/langchain4j/package-info.java
- `M` micronaut-mcp-server-java-sdk/src/main/java/io/micronaut/mcp/server/AbstractMcpServerFactory.java
- `M` micronaut-mcp-server-java-sdk/src/main/java/io/micronaut/mcp/server/context/MicronautMcpTransportContext.java
- `M` micronaut-mcp-server-java-sdk/src/main/java/io/micronaut/mcp/server/context/MicronautMcpTransportContextAdapter.java
- `M` micronaut-mcp-server-java-sdk/src/main/java/io/micronaut/mcp/server/exceptions/InvalidFormatExceptionMcpErrorMapper.java
- `M` micronaut-mcp-server-java-sdk/src/main/java/io/micronaut/mcp/server/exceptions/JsonRrpcResponseUtils.java
- `M` micronaut-mcp-server-java-sdk/src/main/java/io/micronaut/mcp/server/json/McpSchemaSerdeImport.java
- `M` micronaut-mcp-server-java-sdk/src/main/java/io/micronaut/mcp/server/json/MicronautJsonSchemaValidator.java
- `M` micronaut-mcp-server-java-sdk/src/main/java/io/micronaut/mcp/server/registry/AbstractMcpMethodRegistry.java
- `M` micronaut-mcp-server-java-sdk/src/main/java/io/micronaut/mcp/server/registry/AbstractMcpPrimitiveArgumentBinder.java
- `M` micronaut-mcp-server-java-sdk/src/main/java/io/micronaut/mcp/server/registry/McpExecutableMethodProcessor.java
- `M` micronaut-mcp-server-java-sdk/src/main/java/io/micronaut/mcp/server/registry/McpPrimitiveRegistry.java
- `M` micronaut-mcp-server-java-sdk/src/main/java/io/micronaut/mcp/server/registry/ToolRegistry.java
- `M` micronaut-mcp-server-java-sdk/src/main/java/io/micronaut/mcp/server/stateless/McpController.java
- `M` micronaut-mcp-server-java-sdk/src/main/java/io/micronaut/mcp/server/stateless/McpStatelessServerFactory.java
- `M` micronaut-mcp-server-java-sdk/src/main/java/io/micronaut/mcp/server/stateless/async/McpStatelessAsyncServerFactory.java
- `M` micronaut-mcp-server-java-sdk/src/main/java/io/micronaut/mcp/server/stateless/sync/McpStatelessSyncServerFactory.java
- `M` micronaut-mcp-server-java-sdk/src/main/java/io/micronaut/mcp/server/stdio/McpStdioApplication.java
- `M` micronaut-mcp-server-java-sdk/src/main/java/io/micronaut/mcp/server/stdio/StdioServerTransportProviderReplacement.java
- `M` micronaut-mcp-server-java-sdk/src/main/java/io/micronaut/mcp/server/stdio/async/McpServerAsyncFactory.java
- `M` micronaut-mcp-server-java-sdk/src/main/java/io/micronaut/mcp/server/stdio/sync/McpServerSyncFactory.java
- `M` micronaut-mcp-server-java-sdk/src/main/java/io/micronaut/mcp/server/tools/ClasspathPromptFactory.java
- `M` micronaut-mcp-server-java-sdk/src/main/java/io/micronaut/mcp/server/tools/fetch/FetchRequest.java
- `M` micronaut-mcp-server-java-sdk/src/main/java/io/micronaut/mcp/server/tools/fetch/FetchResponse.java
- `M` micronaut-mcp-server-java-sdk/src/main/java/io/micronaut/mcp/server/tools/fetch/FetchTool.java
- `M` micronaut-mcp-server-java-sdk/src/main/java/io/micronaut/mcp/server/tools/search/SearchRequest.java
- `M` micronaut-mcp-server-java-sdk/src/main/java/io/micronaut/mcp/server/tools/search/SearchResponse.java
- `M` micronaut-mcp-server-java-sdk/src/main/java/io/micronaut/mcp/server/tools/search/SearchResult.java
- `M` micronaut-mcp-server-java-sdk/src/main/java/io/micronaut/mcp/server/tools/search/SearchTool.java
- `M` micronaut-mcp/src/main/java/io/micronaut/mcp/conf/client/McpClientConfiguration.java
- `M` micronaut-mcp/src/main/java/io/micronaut/mcp/conf/client/McpClientHttpConfiguration.java
- `M` micronaut-mcp/src/main/java/io/micronaut/mcp/conf/client/McpClientHttpConfigurationEmbeddedServerFactory.java
- `M` micronaut-mcp/src/main/java/io/micronaut/mcp/conf/client/McpClientHtttpConfigurationProperties.java
- `M` micronaut-mcp/src/main/java/io/micronaut/mcp/conf/server/McpServerConfiguration.java
- `M` micronaut-mcp/src/main/java/io/micronaut/mcp/conf/server/McpServerInfoConfiguration.java
- `M` micronaut-mcp/src/main/java/io/micronaut/mcp/primitives/utils/StringInterpolator.java

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` micronaut-mcp-client-java-sdk/src/test/java/io/micronaut/mcp/client/javasdk/McpSyncClientTest.java
- `M` micronaut-mcp-server-java-sdk/src/main/java/io/micronaut/mcp/server/McpIntrospection.java
- `M` micronaut-mcp-server-java-sdk/src/test/java/io/micronaut/mcp/server/context/MicronautMcpTransportContextPromptsTest.java
- `M` micronaut-mcp-server-java-sdk/src/test/java/io/micronaut/mcp/server/context/MicronautMcpTransportContextResourcesTest.java
- `M` micronaut-mcp-server-java-sdk/src/test/java/io/micronaut/mcp/server/exceptions/JsonRrpcResponseUtilsTest.java
- `M` micronaut-mcp-server-java-sdk/src/test/java/io/micronaut/mcp/server/json/MicronautMcpJsonMapperSupplierTest.java
- `M` micronaut-mcp-server-java-sdk/src/test/java/io/micronaut/mcp/server/stateless/async/StatelessAsyncToolsTest.java
- `A` micronaut-mcp-server-java-sdk/src/test/java/io/micronaut/mcp/server/stateless/sync/McpGetMethodNotAllowedAuthenticatedTest.java
- `M` micronaut-mcp-server-java-sdk/src/test/java/io/micronaut/mcp/server/stateless/sync/completions/prompts/StatelessSyncCompletionResultTest.java
- `M` micronaut-mcp-server-java-sdk/src/test/java/io/micronaut/mcp/server/stateless/sync/completions/prompts/StatelessSyncCompletionsTest.java
- `M` micronaut-mcp-server-java-sdk/src/test/java/io/micronaut/mcp/server/stateless/sync/completions/resources/StatelessSyncResourceCompletionsTest.java
- `M` micronaut-mcp-server-java-sdk/src/test/java/io/micronaut/mcp/server/stateless/sync/tools/ToolAnnotationsEagerSingletonTest.java
- `M` micronaut-mcp-server-java-sdk/src/test/java/io/micronaut/mcp/server/stateless/sync/tools/ToolFactoryEagerSingletonTest.java
- `M` micronaut-mcp-server-java-sdk/src/test/java/io/micronaut/mcp/server/stateless/sync/tools/ToolsFactory.java
- `M` micronaut-mcp-server-java-sdk/src/test/java/io/micronaut/mcp/server/stateless/sync/tools/jsonschema/output/FenEvaluationResponse.java
- `M` micronaut-mcp-server-java-sdk/src/test/java/io/micronaut/mcp/server/stdio/async/AsyncToolsTest.java
- `M` micronaut-mcp-server-java-sdk/src/test/java/io/micronaut/mcp/server/stdio/sync/SyncToolsTest.java
- `M` micronaut-mcp-server-java-sdk/src/test/java/io/micronaut/mcp/server/utils/PgnLoader.java
- `M` test-suite-graal/src/test/java/example/micronaut/moon/mcp/MoonToolsHttpTest.java
- `M` test-suite-jackson-databind/src/main/java/example/micronaut/moon/MoonPhaseRequest.java
- `M` test-suite-jackson-databind/src/main/java/example/micronaut/moon/mcp/MoonTools.java
- `M` test-suite-jackson-databind/src/test/java/example/micronaut/moon/mcp/MoonToolsHttpTest.java
- `M` test-suite-mcp-http-tck-common/src/main/java/io/modelcontextprotocol/server/http/tck/async/GetWeatherInput.java
- `M` test-suite-mcp-http-tck-common/src/main/java/io/modelcontextprotocol/server/http/tck/async/Prompts.java
- `M` test-suite-mcp-http-tck-common/src/main/java/io/modelcontextprotocol/server/http/tck/async/Tools.java
- `M` test-suite-moon/src/main/java/example/micronaut/moon/MoonPhaseRequest.java
- `M` test-suite-moon/src/main/java/example/micronaut/moon/mcp/MoonTools.java

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

