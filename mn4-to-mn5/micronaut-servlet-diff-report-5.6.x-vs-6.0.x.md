# Diff Report: `5.6.x` vs `6.0.x` — micronaut-servlet

**Generated:** 2026-04-17
**Base (A):** `mn4/micronaut-servlet` — branch `5.6.x` @ `35f37be6`
**Comparison (B):** `mn5/micronaut-servlet` — branch `6.0.x` @ `19b32743`

---

## Summary

| Category | Count |
|----------|-------|
| Files added (only in B) | 3 (source) |
| Files removed (only in A) | 1 (`ServletCompletedFileUpload.java`) |
| Files modified | ~114 |
| Total changes | Large migration |

---

## Dependency Changes

### Third-Party Upgrades

- `kotest-runner`: `5.9.1` → `6.1.11`
- `undertow`: `2.3.19.Final` → `2.3.24.Final`
- `tomcat`: `11.0.11` → `11.0.21`
- `managed-apache-http-core5`: `5.3.6` → `5.4.2`
- `managed-jetty`: `12.1.2` → `12.1.8`
- `google-cloud-functions`: `1.1.4` → `2.0.0`
- `logback-access`: `2.0.6` → `2.0.12`

### Micronaut Upgrades

- `micronaut` (BOM): `4.10.6` → `5.0.0-M22`
- `micronaut-reactor`: `3.8.0` → `4.0.0-M2`
- `micronaut-security`: `4.15.0` → `5.0.0-M1`
- `micronaut-serde`: `2.15.4` → `3.0.0-M7`
- `micronaut-session`: `4.7.0` → `5.0.0-M2`
- `micronaut-validation`: `4.11.0` → `5.0.0-M2`
- `micronaut-logging`: `1.7.1` → `2.0.0-M2`
- `micronaut-gradle-plugin`: `4.6.0` → `4.6.2`

### Removed from `libs.versions.toml`

- `groovy`, `spock`, `micronaut-docs` — Groovy/Spock test infrastructure dropped (Groovy tests remain but now use inline versions or removed)
- `kotlin`, `gradle-kotlin` — Kotlin Gradle plugin removed from `libs.versions.toml` (plugin now applied via micronaut-kotlin plugin)

### Build

- Gradle: `8.14.3` → `9.4.1`
- `micronaut-build.shared.settings`: `7.6.6` → `8.0.0-M17`

### `gradle/libs.versions.toml`

```diff
-micronaut = "4.10.6"
-micronaut-docs = "3.0.0"
-micronaut-test = "4.9.0"
-groovy = "4.0.27"
-spock = "2.3-groovy-4.0"
+micronaut = "5.0.0-M22"
 managed-servlet-api = '6.1.0'
-kotest-runner = '5.9.1'
-undertow = '2.3.19.Final'
-tomcat = '11.0.11'
+kotest-runner = '6.1.11'
+undertow = '2.3.24.Final'
+tomcat = '11.0.21'
-managed-apache-http-core5 = "5.3.6"
-managed-jetty = '12.1.2'
-micronaut-reactor = "3.8.0"
-micronaut-security = "4.15.0"
-micronaut-serde = "2.15.4"
-micronaut-session = "4.7.0"
-micronaut-validation = "4.11.0"
-google-cloud-functions = '1.1.4'
-micronaut-logging = "1.7.1"
-micronaut-gradle-plugin = "4.6.0"
-logback-access = "2.0.6"
-kotlin = "1.9.25"
+managed-apache-http-core5 = "5.4.2"
+managed-jetty = '12.1.8'
+micronaut-reactor = "4.0.0-M2"
+micronaut-security = "5.0.0-M1"
+micronaut-serde = "3.0.0-M7"
+micronaut-session = "5.0.0-M2"
+micronaut-validation = "5.0.0-M2"
+google-cloud-functions = '2.0.0'
+micronaut-logging = "2.0.0-M2"
+micronaut-gradle-plugin = "4.6.2"
+logback-access = "2.0.12"
# gradle-kotlin entry removed
```

---

## Added Files

- `.github/workflows/sonatype.yml` — Sonatype scan extracted to dedicated workflow
- `http-server-jdk/src/test/java/io/micronaut/servlet/http/server/jdk/QuotedQueryParameterTest.java` — new test for raw query string preservation
- `servlet-engine/src/main/java/io/micronaut/servlet/engine/bind/ServletCompletedFileUploadFactory.java` — factory replacing `ServletCompletedFileUpload` constructor
- `config/checkstyle/custom-suppressions.xml`
- `buildSrc/gradle.properties`

## Removed Files

- `servlet-engine/src/main/java/io/micronaut/servlet/engine/ServletCompletedFileUpload.java` — replaced by `ServletCompletedFileUploadFactory` + Micronaut sealed `CompletedFileUpload`

---

## Key Source Changes

### `DefaultServletHttpRequest` — major refactor

- Implements `FormCapableHttpRequest<B>` (new interface)
- `MediaTypeCodecRegistry` replaced with `MessageBodyHandlerRegistry`
- Added `ByteBodyFactory`, `Executor ioExecutor`, `disposalResources` fields
- jspecify `@NonNull`/`@Nullable` replacing `io.micronaut.core.annotation.*`
- New imports: `FormCapableHttpRequest`, `FormFieldMetadata`, `RawFormField`, `AvailableByteArrayBody`, `Flux`

### `DefaultServletHttpResponse` — codec removed

- `MediaTypeCodec` replaced with `MessageBodyHandlerRegistry` + `MessageBodyWriter`
- jspecify annotations
- Content-type subtype check changed: `contentType.getSubtype().equals("json")` → `"json".equalsIgnoreCase(contentType.getSubtype())`
- Streaming logic refactored (early `return` after raw byte write, `ByteArrayOutputStream` added)

### `DefaultServletBinderRegistry` — codec removed

- `MediaTypeCodecRegistry` replaced with `MessageBodyHandlerRegistry`
- `MapperMediaTypeCodec` replaced with `JsonMapper`
- `FormFactory`, `HttpServerConfiguration`, `BeanProvider` added
- Removed: `Publishers`, `AvailableByteBody`, `Processor`, `CompletableFuture`, `CompletionStage`

### `CompletedPartRequestArgumentBinder` — disposal lifecycle

- `ServletCompletedFileUpload` instantiation replaced with `ServletCompletedFileUploadFactory.create(configuration, part)`
- Adds disposal resource to `LifecycleHttpRequest` for proper cleanup
- `IOException | ServletException` → catches generic `Exception`
- `HttpServerConfiguration` injected via constructor

### `MicronautServletConfiguration` — jspecify

```diff
-import io.micronaut.core.annotation.NonNull;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.NonNull;
+import org.jspecify.annotations.Nullable;
```

### `HttpExchangeHttpServletRequest` — bug fix

```diff
-return exchange.getRequestURI().getQuery();
+return exchange.getRequestURI().getRawQuery();
```
Preserves raw (percent-encoded) query string instead of decoded form.

### `ServletCompletedFileUpload` — breaking API changes

`CompletedFileUpload` became sealed in mn5. `ServletCompletedFileUpload` can no longer implement it directly. New factory `ServletCompletedFileUploadFactory` adapts to Micronaut's sealed type. Documented in `accepted-api-changes.json`.

### Undertow/Jetty/Tomcat server classes

- jspecify annotations throughout
- Minor API alignment with mn5 core (`HttpServerConfiguration`, `MessageBodyHandlerRegistry`)

### buildSrc `module.gradle`

```diff
-"io.undertow:undertow-core:2.3.19.Final"
+"io.undertow:undertow-core:2.3.24.Final"
```

---

## GitHub Actions / CI

Standard mn5 CI migration (same pattern as all other mn5 repos):

- JDK matrix: `['17', '21']` → `['25']`
- SHA-pinned action refs (supply-chain hardening)
- Secrets withheld on PRs: `${{ secrets.X }}` → `${{ github.event.pull_request == null && secrets.X || '' }}`
- `actions/checkout` v5 → v6 (SHA-pinned)
- `gradle/actions/setup-gradle` v4 → v6 (SHA-pinned)
- `graalvm/setup-graalvm` v1.4.1 → v1 (SHA-pinned)
- `mikepenz/action-junit-report` v5 → v6 (SHA-pinned)
- `actions/upload-artifact` v4.6.0 → v7 (SHA-pinned)
- "Remove system JDKs" step added
- Additional disk cleanup paths added (`/opt/ghc`, `/usr/share/dotnet`, `/usr/local/lib/android`)
- Sonatype scan moved to dedicated `sonatype.yml`
- Optional `cleanup.sh` step added
- Branch pattern: `'[1-9]+.[0-9]+.x'` → `'[0-9]+.[0-9]+.x'`

### Renovate

SNAPSHOT exclusion rule added:
```json
{
  "matchDatasources": ["maven"],
  "matchManagers": ["maven", "gradle"],
  "allowedVersions": "!/.+-SNAPSHOT$/"
}
```

---

_Report generated by git-branch-diff skill._
