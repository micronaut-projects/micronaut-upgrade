# Diff Report: `2.8.x` vs `3.0.x`

**Generated:** 2026-04-17
**Base (A):** `/Users/sdelamo/github/micronaut/mn4/micronaut-toml` — branch `2.8.x` @ `58885945`
**Comparison (B):** `/Users/sdelamo/github/micronaut/mn5/micronaut-toml` — branch `3.0.x` @ `6b9f853a`

---

## Summary

| Category | Count |
|----------|-------|
| Files added (only in B) | 6 |
| Files removed (only in A) | 0 |
| Files modified | 24 |
| Total changes | 30 |

> Build artifact directories (`.gradle/`, `build/`) excluded — not source changes.

---

## Dependency Changes

### Third-Party Upgrades

- `org.jetbrains:annotations`: `26.0.2` → `26.1.0` — [Release notes](https://github.com/JetBrains/java-annotations/releases/tag/26.1.0)
- Gradle wrapper: `8.14.3` → `9.4.1` — [Release notes](https://github.com/gradle/gradle/releases/tag/v9.4.1)

### Micronaut Version Bumps

| Dependency | 2.8.x | 3.0.x |
|---|---|---|
| `micronaut` (BOM) | `4.10.4` | `5.0.0-M22` |
| `micronaut-build` shared settings | `7.6.4` | `8.0.0-M17` |

### Removed from `libs.versions.toml`

- `micronaut-docs` — removed
- `micronaut-test` — removed (available via `mnTest` BOM)
- `groovy` / `spock` — removed
- `junit-jupiter-engine` entry — removed (moved to `mnTest` catalog)

### `gradle/libs.versions.toml`

```diff
--- a/gradle/libs.versions.toml
+++ b/gradle/libs.versions.toml
@@ -1,11 +1,7 @@
 [versions]
-micronaut-docs = "2.0.0"
-micronaut = "4.10.4"
-micronaut-test = "4.7.0"
-groovy = "4.0.13"
-spock = "2.3-groovy-4.0"
+micronaut = "5.0.0-M22"

-jetbrains-annotations = "26.0.2"
+jetbrains-annotations = "26.1.0"
 jflex = "1.9.1"

 [libraries]
-junit-jupiter-engine = { module = "org.junit.jupiter:junit-jupiter-engine" }
```

### `gradle.properties`

```diff
-projectVersion=2.8.1-SNAPSHOT
+projectVersion=3.0.0-SNAPSHOT
```

### `gradle/wrapper/gradle-wrapper.properties`

```diff
-distributionUrl=https\://services.gradle.org/distributions/gradle-8.14.3-bin.zip
+distributionUrl=https\://services.gradle.org/distributions/gradle-9.4.1-bin.zip
```

### `settings.gradle`

```diff
-    id 'io.micronaut.build.shared.settings' version '7.6.4'
+    id 'io.micronaut.build.shared.settings' version '8.0.0-M17'
```

---

## Added Files

- `.agents/` _(directory — content not inspected)_
- `.github/workflows/sonatype.yml`
- `.sdkmanrc`
- `buildSrc/gradle.properties`
- `toml/src/test/resources/application.toml`
- `toml/src/test/resources/application-test.toml`

---

## Removed Files

_(none)_

---

## Modified Files

### `toml/src/main/java/io/micronaut/toml/Parser.java`

Two changes: jspecify migration + inner classes made `final`:

```diff
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;

-    private static class TomlObjectBuilder implements TomlNodeBuilder {
+    private static final class TomlObjectBuilder implements TomlNodeBuilder {

-    private static class TomlArrayBuilder implements TomlNodeBuilder {
+    private static final class TomlArrayBuilder implements TomlNodeBuilder {
```

---

### `toml/src/test/java/io/micronaut/toml/ParserTest.java`

_Large file: 61 lines removed, 60 added. Two pervasive changes:_

**1. Jackson 3 package migration** — `com.fasterxml.jackson` → `tools.jackson` (Jackson 3.x changed base package):

```diff
-import com.fasterxml.jackson.core.JsonFactory;
-import com.fasterxml.jackson.core.json.JsonReadFeature;
+import tools.jackson.core.json.JsonFactory;
+import tools.jackson.core.json.JsonReadFeature;
```

**2. JUnit 4 `Assert` → JUnit 5 `Assertions`** throughout:

```diff
-import org.junit.Assert;
 import org.junit.jupiter.api.Assertions;

-        Assert.assertEquals(...)
+        Assertions.assertEquals(...)

-        Assert.assertThrows(...)
+        Assertions.assertThrows(...)
```

---

### `toml/src/test/groovy/io/micronaut/toml/env/TomlPropertySourceLoaderSpec.groovy`

Completely rewritten. The old test used manual `DefaultEnvironment` wiring with in-memory TOML strings. The new test uses `ApplicationContext` directly, relying on actual TOML files on the classpath (the two new test resources added in `toml/src/test/resources/`):

```diff
-import io.micronaut.context.ApplicationContextConfiguration
-import io.micronaut.context.env.DefaultEnvironment
-...
+import io.micronaut.context.ApplicationContext

-    void "test toml property source loader"() {
-        given:
-        Environment env = new DefaultEnvironment(...) {
-            @Override
-            protected SoftServiceLoader<PropertySourceLoader> readPropertySourceLoaders() { ... }
-
-            @Override
-            Optional<InputStream> getResourceAsStream(String path) {
-                // inline TOML strings
-            }
-        }
+    void "test TOML file is automatically loaded via environment"() {
         when:
-        env.start()
+        ApplicationContext ctx = ApplicationContext.builder()
+                .environments("test")
+                .start()
         then:
-        !env.get("hibernate.cache.queries", Boolean).get()
-        ...
+        !ctx.environment.get("hibernate.cache.queries", Boolean).get()
+        ...
+        cleanup:
+        ctx.close()
     }
```

#### Added test resources

`toml/src/test/resources/application.toml`:
```toml
[hibernate]
cache.queries = false

[dataSource]
pooled = true
driverClassName = "org.h2.Driver"
username = "sa"
password = "test"
something = [1, 2]
```

`toml/src/test/resources/application-test.toml`:
```toml
[dataSource]
jmxExport = true
username = "sa"
password = "test"
```

---

### `toml/build.gradle`

```diff
-    testImplementation libs.junit.jupiter.engine
+    testImplementation mnTest.junit.jupiter.engine
```

---

### `buildSrc/gradle.properties` _(added)_

```
micronaut-build-version=8.0.0-M17
```

---

### `.sdkmanrc` _(added)_

```
java=25.0.1-graal
```

---

### `.gitignore`

```diff
+# Ignore gradle.properties generated by micronaut-build
+/buildSrc/gradle.properties
+
+# OpenCode files
+.sisyphus/
```

---

### `.clineignore`

```diff
+!build/generated/
+!build/generated/**
```

---

### `.github/renovate.json`

Added SNAPSHOT exclusion rule (same pattern as other mn5 repos).

---

### GitHub Actions: CI / Workflow Changes

Same mn5 pattern as other repos — identical to `micronaut-session` and `micronaut-guice`:

- Java matrix: `['17', '21']` → `['25']`
- Branch pattern: `'[1-9]+.[0-9]+.x'` → `'[0-9]+.[0-9]+.x'`
- All action refs SHA-pinned
- "Remove system JDKs" step added to all build jobs
- Develocity/secrets withheld on PRs
- Sonatype scan extracted to `sonatype.yml`
- `gradle.yml`: `jacocoReport check` → `check jacocoReport`, optional `cleanup.sh` step added

---

### `MAINTAINING.md`

Spelling: `categorised` → `categorized`, `customisations` → `customizations`, `prioritised` → `prioritized`.

---

### Binary files (diff not shown)

- `gradle/wrapper/gradle-wrapper.jar` — binary differs
- `gradlew` — differs
- `gradlew.bat` — differs

---

_Report generated by git-branch-diff skill._
