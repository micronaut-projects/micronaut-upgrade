• Compared micronaut-elasticsearch as mn4 → mn5.

  Scope

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-elasticsearch, branch 5.10.x, SHA 0095be7
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-elasticsearch, branch 6.0.x, SHA 1fc68c4
  - Report: /private/tmp/micronaut-elasticsearch-5.10-to-6.0-comparison.md

  Key Findings

  - Major baseline move: project 5.10.1-SNAPSHOT → 6.0.1-SNAPSHOT, Micronaut 4.10.4 → 5.0.0, platform 4.5.1 →
    5.0.0-RC1, Gradle wrapper 8.14.3 → 9.5.1, plus .sdkmanrc pinned to java=25.0.1-graal.
  - Elasticsearch dependencies moved from 8.19.5 → 9.4.0 for both co.elastic.clients:elasticsearch-java and
    org.elasticsearch.client:elasticsearch-rest-client.
  - The client factory now uses Jackson 3 APIs: ObjectMapper/JacksonJsonpMapper changed to
    tools.jackson.databind.json.JsonMapper with Jackson3JsonpMapper.
  - Micronaut companion BOMs were moved to the 5 line: Security 4.15.0 → 5.0.0, Test 4.7.0 → 5.0.0, Logging
    1.7.0 → 2.0.0, and Validation BOM 5.0.0 was added.
  - Test setup moved away from the Micronaut Test Resources catalog dependency; test-suite-utils was added
    with a direct ElasticsearchContainer helper and native-image resource config.
  - Java test behavior changed to force index refresh with Refresh.True, remove Awaitility polling, and add
    @ReflectiveAccess to the test Movie type.
  - CI/release hardening added OSV Scanner vulnerability audit scripts/workflow, release audit enforcement,
    and Java/GraalVM 25-only workflow matrices.

  Diff size: 59 files changed, 3785 insertions(+), 185 deletions(-).

  I did not run tests; this was a folder comparison only.

# Release Note Comparison

Generated: 2026-05-19 11:01 UTC
Comparison: `5.10.x` -> `6.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-elasticsearch` | `5.10.x` | `0095be73e33a` | `git@github.com:micronaut-projects/micronaut-elasticsearch.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-elasticsearch` | `6.0.x` | `1fc68c4d06b0` | `git@github.com:micronaut-projects/micronaut-elasticsearch.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-elasticsearch`
- Commit candidates found: 68
- File changes listed: 59
- Version values listed: 30
- File status counts: A=30, M=29

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `5.10.1-SNAPSHOT` | `6.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.apache-http-async-client` | `org.apache.httpcomponents:httpasyncclient:4.1.5` | `org.apache.httpcomponents:httpasyncclient:4.1.5` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.apache-http-client` | `org.apache.httpcomponents:httpclient:4.5.14` | `org.apache.httpcomponents:httpclient:4.5.14` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.awaitility` | `org.awaitility:awaitility:4.3.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.graal-svm` | `org.graalvm.nativeimage:svm:23.1.7` | `org.graalvm.nativeimage:svm:25.0.3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.gradle-micronaut` | `io.micronaut.gradle:micronaut-gradle-plugin:4.5.5` | `io.micronaut.gradle:micronaut-gradle-plugin:5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-elasticsearch-java` | `co.elastic.clients:elasticsearch-java:8.19.5` | `co.elastic.clients:elasticsearch-java:9.4.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-elasticsearch-rest-client` | `org.elasticsearch.client:elasticsearch-rest-client:8.19.5` | `org.elasticsearch.client:elasticsearch-rest-client:9.4.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-security` | `io.micronaut.security:micronaut-security-bom:4.15.0` | `io.micronaut.security:micronaut-security-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-resources` | `io.micronaut.testresources:micronaut-test-resources-bom:2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-validation` | `not present` | `io.micronaut.validation:micronaut-validation-bom:5.0.0` | `added` |
| `gradle/libs.versions.toml` | `versions.apache-http-async-client` | `4.1.5` | `4.1.5` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.apache-http-client` | `4.5.14` | `4.5.14` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.awaitility` | `4.3.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.graal-svm` | `23.1.7` | `25.0.3` | `changed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.15` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.managed-elasticsearch` | `8.19.5` | `9.4.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.4` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-gradle-plugin` | `4.5.5` | `5.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.0` | `2.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-platform` | `4.5.1` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-security` | `4.15.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.7.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test-resources` | `2.10.1` | `3.0.0-M1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `not present` | `5.0.0` | `added` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |
| `settings.gradle` | `plugin.io.micronaut.build.shared.settings` | `7.6.4` | `8.0.0-M18` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `8dc89d67f067` build: remove mainClassName (Sergio del Amo, 2025-10-15)

### Fixes

- `5daf154dd44b` fix(deps): update micronaut dependencies to v5.0.0-rc1 (#697) (renovate[bot], 2026-05-05)
- `ddedcfd0d8df` fix(deps): update managed.elasticsearch to v9.3.4 (#686) (renovate[bot], 2026-05-01)
- `9f9bde71cb8d` fix(deps): update dependency org.graalvm.nativeimage:svm to v25.0.3 (#693) (renovate[bot], 2026-05-01)
- `8ccaa222e4bd` fix(deps): update micronaut dependencies (#694) (renovate[bot], 2026-05-01)
- `96a25a188e87` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m24 (#687) (renovate[bot], 2026-04-23)
- `6b7ecf9f9efb` fix(deps): update dependency io.micronaut.gradle:micronaut-gradle-plugin to v4.6.2 (#684) (renovate[bot], 2026-02-13)
- `c8f1d6447b19` fix(deps): update dependency org.graalvm.nativeimage:svm to v25.0.2 (#683) (renovate[bot], 2026-02-13)
- `2fa488b83239` fix(deps): update managed.elasticsearch to v9.3.0 (#679) (renovate[bot], 2026-02-13)
- `234ade89c75a` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m10 (#681) (renovate[bot], 2026-02-13)
- `0a6e242ec453` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.12 (#672) (renovate[bot], 2025-12-30)
- `6023982c09ac` fix(deps): update dependency org.graalvm.nativeimage:svm to v25 (#661) (renovate[bot], 2025-12-10)
- `cca162eedcde` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#663) (renovate[bot], 2025-12-10)
- `f7c91b224000` fix(deps): update dependency io.micronaut.security:micronaut-security-bom to v4.16.0 (#668) (renovate[bot], 2025-12-10)
- `b6d691c8ea55` fix(deps): update dependency org.graalvm.nativeimage:svm to v23.1.9 (#653) (renovate[bot], 2025-12-10)
- `8092487adf05` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.8 (#652) (renovate[bot], 2025-11-03)
- `8a9cf82ef8e0` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.6 (#646) (renovate[bot], 2025-10-17)

### Security

- `945fb68d4ada` micronaut-security = "5.0.0" (Sergio del Amo, 2026-05-18)
- `8a2938835cb4` ignore cve (Sergio del Amo, 2026-05-18)

### Dependency Updates

- `c660c4639f39` chore: Bump version to 6.0.1-SNAPSHOT (micronaut-build, 2026-05-18)
- `9a7d6d0f24d8` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2026-05-07)
- `7a9df973e6b5` chore(deps): update gradle to v9.5.0 (#698) (renovate[bot], 2026-05-07)
- `e1b6a6bdd9f4` chore(deps): update gradle to v9.5.0 (#690) (renovate[bot], 2026-05-01)
- `4aa38630a2b8` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m16 (#680) (renovate[bot], 2026-02-13)
- `525dd33136b2` chore: Bump version to 6.0.0-SNAPSHOT (micronaut-build, 2025-12-30)
- `9a621d1a7df1` chore(deps): update actions/cache action to v5 (#673) (renovate[bot], 2025-12-30)
- `93a354813862` chore(deps): update github artifact actions (#674) (renovate[bot], 2025-12-30)
- `51a12057248f` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m13 (#675) (renovate[bot], 2025-12-30)
- `1996196b571c` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#656) (renovate[bot], 2025-12-10)
- `82eedbf5d671` chore(deps): update softprops/action-gh-release action to v2.5.0 (#657) (renovate[bot], 2025-12-10)
- `9a04548fdc03` chore(deps): update gradle to v9.2.1 (#658) (renovate[bot], 2025-12-10)
- `47a944038ab2` chore(deps): update github artifact actions (#659) (renovate[bot], 2025-12-10)
- `c567ce506568` chore(deps): update mikepenz/action-junit-report action to v6 (#660) (renovate[bot], 2025-12-10)
- `5513a2e4c5a0` chore(deps): update actions/checkout action to v6 (#662) (renovate[bot], 2025-12-10)
- `edec115fa5ea` chore(deps): update graalvm/setup-graalvm action to v1.4.4 (#664) (renovate[bot], 2025-12-10)
- `d7de8befd056` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#650) (renovate[bot], 2025-11-03)
- `d1e43b53ec7d` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m8 (#651) (renovate[bot], 2025-11-03)

### Review Candidates

- `1fc68c4d06b0` Update common files (#702) (micronaut-build, 2026-05-19)
- `454ce863e1a2` [skip ci] Release v6.0.0 (micronaut-build, 2026-05-18)
- `97ab266b89d1` micronaut test 5.0.0 (Sergio del Amo, 2026-05-18)
- `a2d64bc84187` Upate versions (Sergio del Amo, 2026-05-14)
- `8ccfb5791675` Update common files (#701) (micronaut-build, 2026-05-14)
- `3cf438b894cc` micronaut-platform = "5.0.0-RC1" (Sergio del Amo, 2026-05-13)
- `cbc92cbe8104` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `46b7f76b4a43` Update common files (#700) (micronaut-build, 2026-05-09)
- `a8be6410762d` [skip ci] Release v6.0.0-RC1 (micronaut-build, 2026-05-07)
- `69d21aa11ee1` enable graalvm tests in Micronaut ElasticSearch (#676) (Sergio del Amo, 2026-05-07)
- `691e31f9626e` managed-elasticsearch = "9.4.0" (Sergio del Amo, 2026-05-07)
- `810a6717fd47` micronaut-gradle-plugin = "5.0.0-M1" (Sergio del Amo, 2026-05-07)
- `e2112fe6747e` micronaut-platform = "5.0.0-M3" (Sergio del Amo, 2026-05-07)
- `647e3d263371` update versions (Sergio del Amo, 2026-05-07)
- `9db32c66b24b` Update common files (#699) (micronaut-build, 2026-05-07)
- `b442911d3b7e` Update common files (#696) (micronaut-build, 2026-05-05)
- `440c4f0c8a7e` Update common files (#695) (micronaut-build, 2026-05-01)
- `5e885a6252fe` Update common files (#689) (micronaut-build, 2026-04-26)
- `6ba54a6ef995` Update common files (#677) (micronaut-build, 2026-02-13)
- `fbdee5c2a464` [skip ci] Release v6.0.0-M1 (micronaut-build, 2025-12-30)
- `d2933ef7192a` elasticsearch to 9.2.3 (#671) (issam liqali, 2025-12-30)
- `2f655d20bb65` update to latest milestones (Sergio del Amo, 2025-12-30)
- `6ab6a2a52c03` Update common files (#670) (micronaut-build, 2025-12-30)
- `385e92206ddf` Update common files (#655) (micronaut-build, 2025-12-10)
- `793b8e7f6618` Micronaut 5 compatibility and release prep (#648) (issam liqali, 2025-11-03)
- `f10c752f5508` Update common files (#649) (micronaut-build, 2025-11-03)
- `eee68883d427` Update common files (#647) (micronaut-build, 2025-10-20)
- `03654a49ad9c` Update common files (#645) (micronaut-build, 2025-10-17)
- `c7b1811e59fd` Micronaut Build Gradle Plugin 8.0.0-M4 (Sergio del Amo, 2025-10-15)
- `809f72cc98da` gradle 9.1 (Sergio del Amo, 2025-10-15)
- `70581e6c5639` projectVersion=6.0.0-SNAPSHOT [ci skip] (Sergio del Amo, 2025-10-15)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.elasticsearch-tests.gradle
- `M` elasticsearch/build.gradle.kts
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` settings.gradle
- `M` test-suite-groovy/build.gradle.kts
- `M` test-suite-java/build.gradle
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
- `M` elasticsearch/src/main/java/io/micronaut/elasticsearch/DefaultElasticsearchClientFactory.java
- `A` osv-scanner.toml

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` test-suite-java/src/test/java/micronaut/example/ElasticSearchTest.java
- `M` test-suite-java/src/test/java/micronaut/example/service/Movie.java
- `M` test-suite-java/src/test/java/micronaut/example/service/MovieServiceImpl.java
- `M` test-suite-java/src/test/resources/application.yml
- `A` test-suite-utils/src/main/java/io/micronaut/elasticsearch/ElasticSearch.java
- `A` test-suite-utils/src/main/resources/META-INF/native-image/io.micronaut.elasticsearch/micronaut-elasticsearch/native-image.properties
- `A` test-suite-utils/src/main/resources/META-INF/native-image/io.micronaut.elasticsearch/micronaut-elasticsearch/resource-config.json

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

