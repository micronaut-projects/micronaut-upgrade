• I’m treating the generated “Breaking Changes” section as review signals, not facts; the two commits it flagged are not obviously end-user breaking by themselves. The actual release-note items are the new configuration
  validator, Micronaut 5/dependency updates, validator behavior changes, schema-loader/API additions, and a dirty-worktree warning.

• Explored
  └ Read JsonSchemaClassPathResourceLoader.java, JsonSchemaValidationFactory.java, Schema.java, JsonSchemaValidator.java

───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────

• Compared mn4 -> mn5 for release-note direction.

  Scope:

  - Previous: mn4/micronaut-json-schema, branch 1.8.x, commit 4f3e0af862c2, clean
  - Current: mn5/micronaut-json-schema, branch 2.0.x, commit 33d50ad74265
  - Current worktree is dirty because of untracked json-schema-generator/output/
  - Delta: 139 commits, 245 changed files, 183 added, 62 modified
  - Full report: micronaut-json-schema-mn4-to-mn5-comparison.md:1

  Release Note Draft

  Features

  - Added a new micronaut-json-schema-configuration-validator module. It validates Micronaut application configuration against JSON Schemas discovered on the classpath and is included as a new Gradle module. See mn5/micronaut-
    json-schema/settings.gradle:23 and mn5/micronaut-json-schema/src/main/docs/guide/configurationValidator.adoc:3.
  - Added configuration validator CLI support with JSON/HTML reports, environment selection, suppressions, and optional DI validation. See mn5/micronaut-json-schema/src/main/docs/guide/configurationValidator.adoc:42 and mn5/
    micronaut-json-schema/json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/cli/ConfigurationJsonSchemaValidatorCli.java:44.
  - Added metadata-based dependency injection validation for missing beans, circular dependencies, disabled candidates, ambiguous candidates, and factory-method dependencies. See mn5/micronaut-json-schema/src/main/docs/guide/
    configurationValidator.adoc:57.
  - Added optional runtime integration: ConfigurationErrors API, configurationerrors management endpoint, health indicator, and injecterrors DI endpoint/health support. See mn5/micronaut-json-schema/src/main/docs/guide/
    configurationValidator.adoc:135 and mn5/micronaut-json-schema/json-schema-configuration-validator/src/main/java/io/micronaut/jsonschema/configuration/validator/management/ConfigurationEndpoint.java:40.
  - Added custom configuration validation rules via ConfigurationRule and ServiceLoader. See mn5/micronaut-json-schema/src/main/docs/guide/configurationValidator.adoc:191.

  Compatibility Notes

  - Micronaut baseline changed from 4.10.4 -> 5.0.0-RC2.
  - json-schema-validator changed from 1.5.8 -> 3.0.2; validation now uses SchemaRegistryConfig with JSON Pointer paths and format assertions enabled. See mn5/micronaut-json-schema/json-schema-validation/src/main/java/io/
    micronaut/jsonschema/validation/JsonSchemaValidationFactory.java:33.
  - Public nullability annotations moved to JSpecify in validation APIs. See mn5/micronaut-json-schema/json-schema-validation/src/main/java/io/micronaut/jsonschema/validation/JsonSchemaValidator.java:18.
  - Internal ValidationMessageAdapter now wraps com.networknt.schema.Error and exposes getError() instead of the old getValidationMessage(). See mn5/micronaut-json-schema/json-schema-validation/src/main/java/io/micronaut/
    jsonschema/validation/ValidationMessageAdapter.java:18.

  Dependency And Platform Updates

  - Project version: 1.8.0-SNAPSHOT -> 2.0.0-SNAPSHOT.
  - Micronaut Serde: 2.15.5 -> 3.0.0-RC1.
  - Micronaut SourceGen: 1.8.2 -> 2.0.0-M3.
  - Micronaut Validation: 4.11.0 -> 5.0.0-M2.
  - Gradle wrapper: 8.14.3 -> 9.5.0.
  - Added Micronaut TOML 3.0.0-M2 and Micronaut SQL 7.0.1-M2. See mn5/micronaut-json-schema/gradle/libs.versions.toml:18.

  Other Notable Changes

  - JsonSchemaClassPathResourceLoader gained createDefault(ClassLoader) and jsonSchemas() bulk discovery support. See mn5/micronaut-json-schema/json-schema-utils/src/main/java/io/micronaut/jsonschema/utils/
    JsonSchemaClassPathResourceLoader.java:39.
  - Schema serialization explicitly maps $schema, $id, and $ref. See mn5/micronaut-json-schema/json-schema-common/src/main/java/io/micronaut/jsonschema/model/Schema.java:54.
  - Added docs for configuration validation and wired it into the guide TOC.
  - I did not run the test suite; this is a source/history comparison only.

