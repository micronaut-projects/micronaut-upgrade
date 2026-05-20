Compared micronaut-discovery-client as mn4 -> mn5.

  Scope

  - Base: /Users/sdelamo/github/micronaut/mn4/micronaut-discovery-client, branch 4.8.x, SHA 18421ca03357
  - Target: /Users/sdelamo/github/micronaut/mn5/micronaut-discovery-client, branch 5.0.x, SHA 641cb5236865
  - Same remote, both clean: git@github.com:micronaut-projects/micronaut-discovery-client.git
  - Report: /private/tmp/micronaut-discovery-client-4.8-to-5.0-comparison.md

  Key Findings

  - Release line moves from 4.8.0-SNAPSHOT to 5.0.1-SNAPSHOT.
  - Major baseline update: Micronaut 4.10.4 -> 5.0.0, Micronaut Platform 4.8.3 -> 5.0.0-RC1, Gradle 8.14.3
    -> 9.5.1, Java SDKMAN default added as 25.0.1-graal.
  - New micronaut.config.import support was added for distributed config: consul://..., vault://..., and
    springcloud://..., registered through PropertySourceImporter.
  - Legacy bootstrap ConfigurationClient distributed configuration remains, but now logs deprecation
    warnings recommending config import.
  - Spring Cloud and Vault legacy clients are now gated by micronaut.config-client.enabled=true.
  - Documented breaking removals include deprecated Consul API classes such as CatalogEntry, Check,
    CheckEntry, HealthEntry, HTTPCheck, NewCheck, ServiceEntry, and TTLCheck, plus related deprecated
    ConsulOperations methods.
  - Consul APIs now use the newer Consul* model types more consistently, including NewServiceEntry checks
    as List<ConsulCheck>.
  - Consul config watch gained importer-aware support for explicit imported paths and native-format refresh
    handling.
  - Consul ACL token spelling was corrected from asl to acl; deprecated getAslToken / setAslToken aliases
    remain.
  - Consul service-discovery docs were split into focused pages, and new distributed configuration docs
    were added for Consul, Vault, and Spring Cloud Config.

  Diff size: 193 files changed, 9810 insertions(+), 1797 deletions(-).

  I did not run tests; this was a folder comparison and targeted source/build-diff review only.
# Release Note Comparison

Generated: 2026-05-19 15:09 UTC
Comparison: `4.8.x` -> `5.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-discovery-client` | `4.8.x` | `18421ca03357` | `git@github.com:micronaut-projects/micronaut-discovery-client.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-discovery-client` | `5.0.x` | `641cb5236865` | `git@github.com:micronaut-projects/micronaut-discovery-client.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-discovery-client`
- Commit candidates found: 100
- File changes listed: 193
- Version values listed: 30
- File status counts: A=79, D=10, M=103, R=1

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `projectVersion` | `4.8.0-SNAPSHOT` | `5.0.1-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.awaitility` | `org.awaitility:awaitility:4.3.0` | `org.awaitility:awaitility:4.3.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.commons-lang3` | `org.apache.commons:commons-lang3:3.17.0` | `org.apache.commons:commons-lang3:3.20.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.jsonassert` | `org.skyscreamer:jsonassert:1.5.3` | `org.skyscreamer:jsonassert:1.5.3` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.micronaut-docs-asciidoc-config-props` | `io.micronaut.docs:micronaut-docs-asciidoc-config-props:3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-reactor` | `io.micronaut.reactor:micronaut-reactor-bom:3.9.0` | `io.micronaut.reactor:micronaut-reactor-bom:4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-serde` | `io.micronaut.serde:micronaut-serde-bom:2.15.5` | `io.micronaut.serde:micronaut-serde-bom:3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test` | `io.micronaut.test:micronaut-test-bom:4.9.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-resources` | `io.micronaut.testresources:micronaut-test-resources-bom:2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-validation` | `io.micronaut.validation:micronaut-validation-bom:4.11.0` | `io.micronaut.validation:micronaut-validation-bom:5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.sonatype-scan` | `org.sonatype.gradle.plugins:scan-gradle-plugin:3.1.4` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.spock` | `spock:2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.awaitility` | `4.3.0` | `4.3.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.commons-lang3` | `3.17.0` | `3.20.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.groovy` | `4.0.17` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.jsonassert` | `1.5.3` | `1.5.3` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.micronaut` | `4.10.4` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-logging` | `1.7.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-platform` | `4.8.3` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-reactor` | `3.9.0` | `4.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-serde` | `2.15.5` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.9.0` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test-resources` | `2.10.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.11.0` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.sonatype-scan` | `3.1.4` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.1` | `changed` |
| `settings.gradle` | `plugin.io.micronaut.build.shared.settings` | `7.6.4` | `8.0.0-M18` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `f0699d512ba9` remove micronaut-jackson-databind (#807) (Sergio del Amo, 2026-04-27)

### Features

- `bfa3e3e9bd3a` Add distributed config import support (#829) (Graeme Rocher, 2026-04-18)

### Fixes

- `e884a31dbe4f` fix(deps): update dependency org.apache.commons:commons-lang3 to v3.20.0 (#759) (renovate[bot], 2026-04-27)
- `534f7f71f92d` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m22 (#820) (renovate[bot], 2026-04-15)
- `db362820a0ef` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m6 (#826) (renovate[bot], 2026-04-15)
- `9cfab0004fe0` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m10 (#811) (renovate[bot], 2026-02-16)
- `de22aaeb6845` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v3.0.0-m2 (#812) (renovate[bot], 2026-02-16)
- `9f134425b2be` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.12 (#798) (renovate[bot], 2025-12-31)
- `44557e90bfe3` fix(deps): update dependency org.spockframework:spock-core to v2.4-groovy-5.0 (#800) (renovate[bot], 2025-12-31)
- `f3baf124fb40` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.10.9 (#784) (renovate[bot], 2025-12-10)
- `169877f1a165` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v4.12.0 (#790) (renovate[bot], 2025-12-10)
- `d1efe864e0af` fix(deps): update dependency io.micronaut.reactor:micronaut-reactor-bom to v3.9.1 (#785) (renovate[bot], 2025-12-10)
- `c5ed91405d5c` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.16.2 (#786) (renovate[bot], 2025-12-10)
- `1e4c12b787ff` fix(deps): update dependency io.micronaut.test:micronaut-test-bom to v4.10.2 (#787) (renovate[bot], 2025-12-10)
- `28550361ed78` fix(deps): update dependency io.micronaut.testresources:micronaut-test-resources-bom to v2.10.1 (#788) (renovate[bot], 2025-12-10)
- `88450309500f` fix(deps): update dependency io.micronaut:micronaut-core-bom to v4.3.12 (#593) (renovate[bot], 2024-03-27)
- `924df9650359` fix(deps): update dependency org.awaitility:awaitility to v4.2.1 (#594) (renovate[bot], 2024-03-27)
- `150fb00b61bc` fix(deps): update dependency io.micronaut.serde:micronaut-serde-bom to v2.8.2 (#589) (renovate[bot], 2024-03-14)

### Dependency Updates

- `e33a897bab9b` chore: Bump version to 5.0.1-SNAPSHOT (micronaut-build, 2026-05-14)
- `e6771f04dd77` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-05-08)
- `aad2cb97e452` Update dependency io.micronaut:micronaut-core-bom to v5.0.0-M26 (#841) (renovate[bot], 2026-05-01)
- `242239dfaa45` Update Micronaut dependencies (#836) (renovate[bot], 2026-04-29)
- `2f3b7bc994bd` chore(deps): update actions/cache digest to 27d5ce7 (#832) (renovate[bot], 2026-04-17)
- `5de5b66e1df4` chore(deps): update plugin org.graalvm.buildtools.native to v1 (#828) (renovate[bot], 2026-04-15)
- `d5d25189f144` chore(deps): update plugin org.graalvm.buildtools.native to v0.11.5 (#815) (renovate[bot], 2026-04-15)
- `cce67d5b957a` chore(deps): update gradle to v9.4.1 (#823) (renovate[bot], 2026-04-15)
- `99f5e981fce2` chore(deps): update softprops/action-gh-release action to v2.6.2 (#824) (renovate[bot], 2026-04-15)
- `971172fd392c` chore(deps): update gradle/actions action to v6 (#825) (renovate[bot], 2026-04-15)
- `1c499edb3660` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#819) (renovate[bot], 2026-03-25)
- `e8a0edeea82f` chore(deps): update gradle to v9.3.1 (#814) (renovate[bot], 2026-02-16)
- `90d00fbef788` chore(deps): update plugin io.micronaut.library to v4.6.2 (#816) (renovate[bot], 2026-02-16)
- `94af7a9a7fdc` chore(deps): update plugin io.micronaut.minimal.library to v4.6.2 (#817) (renovate[bot], 2026-02-16)
- `baa9a87af800` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m16 (#810) (renovate[bot], 2026-02-16)
- `08630527aa03` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2025-12-31)
- `c4d0286916e4` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m13 (#799) (renovate[bot], 2025-12-31)
- `7bce9cb7b76c` chore(deps): update actions/cache action to v5 (#802) (renovate[bot], 2025-12-31)
- `e84fa9080f6f` chore(deps): update github artifact actions (#803) (renovate[bot], 2025-12-31)
- `c1895345c220` chore(deps): update plugin org.graalvm.buildtools.native to v0.11.3 (#754) (renovate[bot], 2025-12-10)
- `8ce5fd9f419c` chore(deps): update actions/checkout action to v6.0.1 (#791) (renovate[bot], 2025-12-10)
- `cf6c074fe36d` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#777) (renovate[bot], 2025-12-10)
- `d7b9a047e4d8` chore(deps): update softprops/action-gh-release action to v2.5.0 (#780) (renovate[bot], 2025-12-10)
- `ee8783d89ba5` chore(deps): update plugin io.micronaut.library to v4.6.1 (#781) (renovate[bot], 2025-12-10)
- `24fba034fc5c` chore(deps): update plugin io.micronaut.minimal.library to v4.6.1 (#782) (renovate[bot], 2025-12-10)
- `bb0db19c82cd` chore(deps): update plugin io.micronaut.test-resources to v4.6.1 (#783) (renovate[bot], 2025-12-10)
- `f7493fdcde5e` chore(deps): update graalvm/setup-graalvm action to v1.4.4 (#789) (renovate[bot], 2025-12-10)
- `9d0f6348157a` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#773) (renovate[bot], 2025-10-27)
- `01649f47a326` chore(deps): update plugin io.micronaut.minimal.library to v4.5.5 (#768) (renovate[bot], 2025-10-16)
- `4b3987de8413` chore(deps): update plugin io.micronaut.library to v4.3.6 (#606) (renovate[bot], 2024-04-07)
- `ec84386539e1` chore(deps): update plugin io.micronaut.build.shared.settings to v6.7.0 (#591) (renovate[bot], 2024-03-27)
- `2ed95882b892` chore(deps): update graalvm/setup-graalvm action to v1.2.1 (#595) (renovate[bot], 2024-03-27)
- `85517b153ace` chore(deps): update plugin io.micronaut.library to v4.3.5 (#596) (renovate[bot], 2024-03-27)
- `3dd13f211fbd` chore(deps): update plugin io.micronaut.test-resources to v4.3.5 (#597) (renovate[bot], 2024-03-27)
- `e623997ab03e` chore(deps): update dependency gradle to v8.7 (#598) (renovate[bot], 2024-03-27)
- `d8ec8ac72af1` chore(deps): update slsa-framework/slsa-github-generator action to v1.10.0 (#599) (renovate[bot], 2024-03-27)

### Documentation

- `071e092eb88f` doc: split consul docs (#835) (Issam Liqali, 2026-04-27)

### Internal

- `c314b73a2663` Build: Update to micronaut 5 (#801) (issam liqali, 2025-12-31)

### Review Candidates

- `641cb5236865` Update common files (#847) (micronaut-build, 2026-05-19)
- `e0c617c8beb3` [skip ci] Release v5.0.0 (micronaut-build, 2026-05-14)
- `437fa178d01a` Update versions (Sergio del Amo, 2026-05-14)
- `d01de2148d1b` Update common files (#846) (micronaut-build, 2026-05-14)
- `72ad7ef7d478` micronaut-serde = "3.0.0-RC3" (Sergio del Amo, 2026-05-13)
- `eb5603896e50` micronaut-platform = "5.0.0-RC1" (Sergio del Amo, 2026-05-13)
- `5264ff9fcb87` micronaut = "5.0.0" (Sergio del Amo, 2026-05-13)
- `260a0ae23065` Update common files (#845) (micronaut-build, 2026-05-09)
- `d62a942ebce5` [skip ci] Release v5.0.0-RC1 (micronaut-build, 2026-05-08)
- `074791a8fe72` Enable GraalVM tests for Micronaut Discovery Client (#805) (Sergio del Amo, 2026-05-08)
- `f417655a19e9` Update plugin org.graalvm.buildtools.native to v1 (#839) (renovate[bot], 2026-05-08)
- `3c7467c974c1` Update common files (#844) (micronaut-build, 2026-05-08)
- `a0c34c6ece42` update versions (Sergio del Amo, 2026-05-07)
- `047078f58f36` Update common files (#843) (micronaut-build, 2026-05-07)
- `f091718d9d02` Update common files (#842) (micronaut-build, 2026-05-05)
- `41f151cd5882` [discovery-client] Update common files for branch 5.0.x (#840) (micronaut-build, 2026-05-01)
- `5838fcd76db7` Update common files (#838) (micronaut-build, 2026-04-29)
- `7496b5f360a5` Change basePriority in ConsultConfigurationClient (#806) (Sergio del Amo, 2026-04-29)
- `cbaf917be0a8` Update Gradle to v9.5.0 (#837) (renovate[bot], 2026-04-29)
- `2300be69d05d` micronaut-validation = "5.0.0-M2" (Sergio del Amo, 2026-04-27)
- `d659581bac72` micronaut-test = "5.0.0-M8" (Sergio del Amo, 2026-04-27)
- `707f58b99135` micronaut-serde = "3.0.0-M7" (Sergio del Amo, 2026-04-27)
- `1cc8b074389c` micronaut = "5.0.0-M24" (Sergio del Amo, 2026-04-27)
- `739c0f678d39` Update common files (#834) (micronaut-build, 2026-04-26)
- `d0718486f94e` Update common files (#831) (micronaut-build, 2026-04-17)
- `5d9b26685944` Update to micronaut 5.0.0-M22 (#830) (Issam Liqali, 2026-04-16)
- `d817ca850d72` Update common files (#822) (micronaut-build, 2026-04-15)
- `f709cde8b566` Update common files (#809) (micronaut-build, 2026-02-16)
- `07c62f59a2e2` Update common files (#804) (micronaut-build, 2025-12-31)
- `35e0d7396270` [skip ci] Release v5.0.0-M1 (micronaut-build, 2025-12-31)
- `34f21670085b` Update common files (#797) (micronaut-build, 2025-12-31)
- `1366c934d67c` Update common files (#778) (micronaut-build, 2025-12-10)
- `55dcbb7f27fc` Replace Micronaut nullability annotations with JSpecify annotations (#793) (Copilot, 2025-12-01)
- `b40052222837` io.micronaut.build.shared.settings 8.0.0-M6 (Sergio del Amo, 2025-10-27)
- `4d407c20151d` Update common files (#772) (micronaut-build, 2025-10-27)
- `6e15d349fd85` Update common files (#771) (micronaut-build, 2025-10-20)
- `3c0eb26684ca` Micronaut 5 compatibility and release prep (#770) (issam liqali, 2025-10-16)
- `c81d3f37dd46` Update common files (#769) (micronaut-build, 2025-10-16)
- `5a10ead178ce` Micronaut Build Gradle Plugin 8.0.0-M4 (Sergio del Amo, 2025-10-14)
- `18c810699bf6` gradle 9.1 (Sergio del Amo, 2025-10-14)
- `b2672f7ad497` Merge branch '4.8.x' into 5.0.x (Sergio del Amo, 2025-10-14)
- `9048d8c47d38` Merge branch '4.4.x' into 5.0.x (Sergio del Amo, 2024-04-07)
- `47005c3e6825` Update common files (#602) (micronaut-build, 2024-04-01)
- `dcc3f5d2561d` breaks: del deprecations for MN 5 & doc breaks. (#588) (Dean Wette, 2024-03-14)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` build.gradle
- `M` buildSrc/build.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.discovery-client-base.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.discovery-client-module.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.discovery-client-tests-consul.gradle
- `M` discovery-client-tests/build.gradle
- `M` discovery-client/build.gradle
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` settings.gradle
- `M` test-suite-consul-graal-jacksondatabind/build.gradle.kts
- `M` test-suite-consul-graal-serde/build.gradle.kts
- `M` test-suite-consul-graal/build.gradle.kts
- `A` test-suite-consul-utils/build.gradle.kts
- `M` test-suite-consul-watch/build.gradle.kts
- `M` test-suite-spring-cloud-config-server/build.gradle.kts

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
- `M` README.md
- `A` src/main/docs/guide/breaks.adoc
- `A` src/main/docs/guide/distributedConfiguration.adoc
- `A` src/main/docs/guide/distributedConfigurationConsul.adoc
- `A` src/main/docs/guide/distributedConfigurationConsulConsulImportUriReference.adoc
- `A` src/main/docs/guide/distributedConfigurationConsulImportingConsulConfiguration.adoc
- `A` src/main/docs/guide/distributedConfigurationConsulLegacyBootstrapConfiguration.adoc
- `A` src/main/docs/guide/distributedConfigurationConsulLegacyBootstrapConfigurationStoringConfigurationAsFileReferences.adoc
- `A` src/main/docs/guide/distributedConfigurationConsulLegacyBootstrapConfigurationStoringConfigurationAsKeyValuePairs.adoc
- `A` src/main/docs/guide/distributedConfigurationConsulLegacyBootstrapConfigurationStoringConfigurationInYamlJsonOrPropertiesFormat.adoc
- `A` src/main/docs/guide/distributedConfigurationVault.adoc
- `M` src/main/docs/guide/introduction.adoc
- `M` src/main/docs/guide/serviceDiscoveryConsul.adoc
- `A` src/main/docs/guide/serviceDiscoveryConsulAutoRegisteringWithConsul.adoc
- `A` src/main/docs/guide/serviceDiscoveryConsulConsulHealthChecks.adoc
- `A` src/main/docs/guide/serviceDiscoveryConsulConsulWatch.adoc
- `A` src/main/docs/guide/serviceDiscoveryConsulControllingIpHostRegistration.adoc
- `A` src/main/docs/guide/serviceDiscoveryConsulCustomizingConsulServiceRegistration.adoc
- `A` src/main/docs/guide/serviceDiscoveryConsulDiscoveryServicesFromConsul.adoc
- `A` src/main/docs/guide/serviceDiscoveryConsulStartingConsul.adoc
- `M` src/main/docs/guide/springCloudConfigServer.adoc
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
- `M` config/accepted-api-changes.json
- `M` config/checkstyle/checkstyle.xml
- `M` discovery-client/src/main/java/io/micronaut/discovery/client/ClientUtil.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/client/DiscoveryClientConfiguration.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/client/EndpointUtil.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/client/config/DistributedPropertySourceLocator.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/consul/ConsulConfiguration.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/consul/ConsulServiceInstance.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/consul/client/v1/AbstractConsulClient.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/consul/client/v1/AbstractServiceEntry.java
- `D` discovery-client/src/main/java/io/micronaut/discovery/consul/client/v1/CatalogEntry.java
- `D` discovery-client/src/main/java/io/micronaut/discovery/consul/client/v1/Check.java
- `D` discovery-client/src/main/java/io/micronaut/discovery/consul/client/v1/CheckEntry.java
- `R089` discovery-client/src/main/java/io/micronaut/discovery/consul/client/v1/ConsulAclTokenFilter.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/consul/client/v1/ConsulCatalogEntry.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/consul/client/v1/ConsulCheck.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/consul/client/v1/ConsulNewServiceEntry.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/consul/client/v1/ConsulOperations.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/consul/client/v1/ConsulServiceEntry.java
- `D` discovery-client/src/main/java/io/micronaut/discovery/consul/client/v1/HTTPCheck.java
- `D` discovery-client/src/main/java/io/micronaut/discovery/consul/client/v1/HealthEntry.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/consul/client/v1/KeyValue.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/consul/client/v1/LocalAgentConfiguration.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/consul/client/v1/MemberEntry.java
- `D` discovery-client/src/main/java/io/micronaut/discovery/consul/client/v1/NewCheck.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/consul/client/v1/NewServiceEntry.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/consul/client/v1/NodeEntry.java
- `D` discovery-client/src/main/java/io/micronaut/discovery/consul/client/v1/ServiceEntry.java
- `D` discovery-client/src/main/java/io/micronaut/discovery/consul/client/v1/TTLCheck.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/consul/client/v1/blockingqueries/BlockedQueriesConsulClient.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/consul/client/v1/blockingqueries/BlockingQueriesConfiguration.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/consul/config/ConsulConfigurationClient.java
- `A` discovery-client/src/main/java/io/micronaut/discovery/consul/imports/ConsulImportSupport.java
- `A` discovery-client/src/main/java/io/micronaut/discovery/consul/imports/ConsulPropertySourceImporter.java
- `A` discovery-client/src/main/java/io/micronaut/discovery/consul/imports/package-info.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/consul/registration/ConsulAutoRegistration.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/consul/watch/AbstractWatcher.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/consul/watch/NativeWatcher.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/consul/watch/PropertiesChangeHandler.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/consul/watch/WatchConfiguration.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/consul/watch/WatchFactory.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/eureka/EurekaConfiguration.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/eureka/client/v2/AbstractEurekaClient.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/eureka/client/v2/DataCenterInfo.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/eureka/client/v2/DataCenterTypeInfoResolver.java
- `A` discovery-client/src/main/java/io/micronaut/discovery/imports/LegacyConfigurationClientDeprecationLogger.java
- `A` discovery-client/src/main/java/io/micronaut/discovery/imports/RemoteConfigImportMetadata.java
- `A` discovery-client/src/main/java/io/micronaut/discovery/imports/RemoteConfigImportOptionBinder.java
- `A` discovery-client/src/main/java/io/micronaut/discovery/imports/RemoteConfigImporterContextFactory.java
- `A` discovery-client/src/main/java/io/micronaut/discovery/imports/package-info.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/spring/config/SpringCloudClientConfiguration.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/spring/config/SpringCloudConfigurationClient.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/spring/config/client/ConfigServerPropertySource.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/spring/config/client/SpringCloudConfigClient.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/spring/config/package-info.java
- `A` discovery-client/src/main/java/io/micronaut/discovery/spring/imports/SpringCloudImportSupport.java
- `A` discovery-client/src/main/java/io/micronaut/discovery/spring/imports/SpringCloudPropertySourceImporter.java
- `A` discovery-client/src/main/java/io/micronaut/discovery/spring/imports/package-info.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/vault/config/VaultConfigHttpClient.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/vault/config/VaultConfigurationClient.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/vault/config/package-info.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/vault/config/v1/VaultConfigHttpClientV1.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/vault/config/v1/VaultResponseV1.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/vault/config/v2/VaultConfigHttpClientV2.java
- `M` discovery-client/src/main/java/io/micronaut/discovery/vault/config/v2/VaultResponseV2.java
- `A` discovery-client/src/main/java/io/micronaut/discovery/vault/imports/VaultImportSupport.java
- `A` discovery-client/src/main/java/io/micronaut/discovery/vault/imports/VaultPropertySourceImporter.java
- `A` discovery-client/src/main/java/io/micronaut/discovery/vault/imports/package-info.java
- `A` discovery-client/src/main/resources/META-INF/native-image/io.micronaut.discovery/client/reflect-config.json
- `A` discovery-client/src/main/resources/META-INF/services/io.micronaut.context.env.PropertySourceImporter

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `M` discovery-client/src/test/groovy/io/micronaut/discovery/cloud/DigitalOceanMetadataResolverSpec.groovy
- `A` discovery-client/src/test/groovy/io/micronaut/discovery/consul/ConsulConfigurationClientCharacterizationSpec.groovy
- `A` discovery-client/src/test/groovy/io/micronaut/discovery/consul/ConsulPropertySourceImporterIntegrationSpec.groovy
- `A` discovery-client/src/test/groovy/io/micronaut/discovery/consul/ConsulPropertySourceImporterSpec.groovy
- `M` discovery-client/src/test/groovy/io/micronaut/discovery/consul/MockConsulAuth.groovy
- `M` discovery-client/src/test/groovy/io/micronaut/discovery/consul/MockConsulServer.groovy
- `A` discovery-client/src/test/groovy/io/micronaut/discovery/consul/imports/ConsulImportSupportSpec.groovy
- `M` discovery-client/src/test/groovy/io/micronaut/discovery/consul/watch/PropertiesChangeHandlerSpec.groovy
- `M` discovery-client/src/test/groovy/io/micronaut/discovery/consul/watch/WatchFactorySpec.groovy
- `M` discovery-client/src/test/groovy/io/micronaut/discovery/consul/watch/WatcherSpec.groovy
- `M` discovery-client/src/test/groovy/io/micronaut/discovery/eureka/EurekaAutoRegistrationSpec.groovy
- `M` discovery-client/src/test/groovy/io/micronaut/discovery/eureka/EurekaClientSpec.groovy
- `M` discovery-client/src/test/groovy/io/micronaut/discovery/eureka/EurekaContextPathSpec.groovy
- `M` discovery-client/src/test/groovy/io/micronaut/discovery/eureka/EurekaInstanceInfoSpec.groovy
- `M` discovery-client/src/test/groovy/io/micronaut/discovery/eureka/EurekaMockAutoRegistrationSpec.groovy
- `M` discovery-client/src/test/groovy/io/micronaut/discovery/eureka/EurekaMockBasicAuthSpec.groovy
- `M` discovery-client/src/test/groovy/io/micronaut/discovery/eureka/EurekaMockHeartbeatSpec.groovy
- `M` discovery-client/src/test/groovy/io/micronaut/discovery/eureka/health/EurekaHealthIndicatorSpec.groovy
- `A` discovery-client/src/test/groovy/io/micronaut/discovery/imports/ConfigurationClientDeprecationAndCoexistenceSpec.groovy
- `A` discovery-client/src/test/groovy/io/micronaut/discovery/imports/ConnectionStringImportContractSpec.groovy
- `A` discovery-client/src/test/groovy/io/micronaut/discovery/imports/RemoteConfigImportOptionsSpec.groovy
- `A` discovery-client/src/test/groovy/io/micronaut/discovery/imports/RemoteConfigImporterBeanActivationSpec.groovy
- `A` discovery-client/src/test/groovy/io/micronaut/discovery/imports/RemoteConfigImporterCommonSettingsSpec.groovy
- `A` discovery-client/src/test/groovy/io/micronaut/discovery/imports/RemoteConfigImporterContextFactorySpec.groovy
- `M` discovery-client/src/test/groovy/io/micronaut/discovery/spring/MockSpringCloudConfigSecuredServer.java
- `M` discovery-client/src/test/groovy/io/micronaut/discovery/spring/MockSpringCloudConfigServer.java
- `A` discovery-client/src/test/groovy/io/micronaut/discovery/spring/SpringCloudConfigurationClientCharacterizationSpec.groovy
- `A` discovery-client/src/test/groovy/io/micronaut/discovery/spring/SpringCloudPropertySourceImporterSpec.groovy
- `A` discovery-client/src/test/groovy/io/micronaut/discovery/spring/imports/SpringCloudImportSupportSpec.groovy
- `M` discovery-client/src/test/groovy/io/micronaut/discovery/vault/MockingVaultServerV1Controller.java
- `M` discovery-client/src/test/groovy/io/micronaut/discovery/vault/MockingVaultServerV2Controller.java
- `A` discovery-client/src/test/groovy/io/micronaut/discovery/vault/VaultConfigurationClientCharacterizationSpec.groovy
- `A` discovery-client/src/test/groovy/io/micronaut/discovery/vault/VaultPropertySourceImporterIntegrationSpec.groovy
- `A` discovery-client/src/test/groovy/io/micronaut/discovery/vault/VaultPropertySourceImporterSpec.groovy
- `A` discovery-client/src/test/groovy/io/micronaut/discovery/vault/imports/VaultImportSupportSpec.groovy
- `A` discovery-client/src/test/resources/application-eureka.properties
- `D` test-suite-consul-graal-jacksondatabind/src/test/resources/application.yml
- `D` test-suite-consul-graal-serde/src/test/resources/application.yml
- `M` test-suite-consul-graal/src/main/java/io/micronaut/consul/graal/ConsulTest.java
- `M` test-suite-consul-graal/src/main/java/io/micronaut/consul/graal/KeyValueTest.java
- `M` test-suite-consul-graal/src/main/resources/application.yml
- `A` test-suite-consul-utils/src/main/java/io/micronaut/discovery/consul/testcontainers/Consul.java
- `A` test-suite-consul-utils/src/main/resources/META-INF/native-image/io.micronaut.elasticsearch/micronaut-elasticsearch/native-image.properties
- `M` test-suite-consul-watch/src/main/java/io/micronaut/discovery/consul/watch/watcher/BaseWatcherIntegrationTest.java

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

