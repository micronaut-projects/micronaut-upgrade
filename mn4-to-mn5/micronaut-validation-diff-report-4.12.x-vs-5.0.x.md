# Diff Report: `4.12.x` vs `5.0.x`

**Generated:** 2026-04-17
**Base (A):** `/Users/sdelamo/github/micronaut/mn4/micronaut-validation` — branch `4.12.x` @ `e01927d4`
**Comparison (B):** `/Users/sdelamo/github/micronaut/mn5/micronaut-validation` — branch `5.0.x` @ `ebc7b389`

---

## Summary

| Category | Count |
|----------|-------|
| Files added (only in B) | 8 |
| Files removed (only in A) | 0 |
| Files modified | ~90 |
| Total changes | ~98 |

> Build artifact directories (`.gradle/`, `build/`) excluded. This is the largest diff of the mn4→mn5 series reviewed so far — the majority of modified files are jspecify annotation migrations.

---

## Dependency Changes

### Third-Party Upgrades

- `spotbugs`: `4.9.5` → `4.9.8` — [Release notes](https://github.com/spotbugs/spotbugs/releases/tag/4.9.8)
- `arquillian-container`: `1.9.5.Final` → `1.10.1.Final` — [Release notes](https://github.com/arquillian/arquillian-core/releases/tag/1.10.1.Final)
- `kotlin-gradle-plugin`: `1.9.25` → `2.3.20` — [Release notes](https://github.com/JetBrains/kotlin/releases/tag/v2.3.20)
- `ksp-gradle-plugin`: `1.9.25-1.0.20` → `2.3.6` — [Release notes](https://github.com/google/ksp/releases)
- `jmh-generator-annprocess`: `1.36` → `1.37` (pinned in `validation/build.gradle`)
- Gradle wrapper: `8.14.3` → `9.4.1` — [Release notes](https://github.com/gradle/gradle/releases/tag/v9.4.1)

### Micronaut Version Bumps

| Dependency | 4.12.x | 5.0.x |
|---|---|---|
| `micronaut` (BOM) | `4.10.3` | `5.0.0-M22` |
| `micronaut-platform` | `4.9.3` | `4.10.10` |
| `micronaut-reactor` | `3.9.0` | `4.0.0-M2` |
| `micronaut-rxjava2` | `2.8.0` | **removed** → replaced by `micronaut-rxjava3 4.0.0-M1` |
| `micronaut-kotlin` | `4.7.0` | `5.0.0-M1` |
| `micronaut-logging` | `1.7.1` | removed (available via BOM) |
| `micronaut-gradle-plugin` | `4.5.4` | `5.0.0-M1` |
| `micronaut-build` shared settings | `7.6.4` | `8.0.0-M17` |

### `gradle/libs.versions.toml`

```diff
 [versions]
-groovy = "4.0.28"
-spotbugs = "4.9.5"
-arquillian-container = "1.9.5.Final"
+spotbugs = "4.9.8"
+arquillian-container = "1.10.1.Final"

-micronaut = "4.10.3"
-micronaut-platform = "4.9.3"
-micronaut-docs = "2.0.0"
-micronaut-test = "4.9.0"
-micronaut-reactor = "3.9.0"
-micronaut-rxjava2 = "2.8.0"
-micronaut-kotlin = "4.7.0"
-micronaut-logging = "1.7.1"
+micronaut = "5.0.0-M22"
+micronaut-platform = "4.10.10"
+micronaut-reactor = "4.0.0-M2"
+micronaut-rxjava3 = "4.0.0-M1"
+micronaut-kotlin = "5.0.0-M1"

-micronaut-gradle-plugin = "4.5.4"
-kotlin-gradle-plugin = "1.9.25"
-ksp-gradle-plugin = "1.9.25-1.0.20"
+micronaut-gradle-plugin = "5.0.0-M1"
+kotlin-gradle-plugin = "2.3.20"
+ksp-gradle-plugin = "2.3.6"

-micronaut-rxjava2 = { module = 'io.micronaut.rxjava2:micronaut-rxjava2-bom', ...}
+micronaut-rxjava3 = { module = 'io.micronaut.rxjava3:micronaut-rxjava3-bom', ...}

-groovy-bom = { module = "org.apache.groovy:groovy-bom", version.ref = "groovy" }
-junit-jupiter-engine = { module = "org.junit.jupiter:junit-jupiter-engine" }
```

### `settings.gradle`

```diff
-    id 'io.micronaut.build.shared.settings' version '7.6.4'
+    id 'io.micronaut.build.shared.settings' version '8.0.0-M17'

-    importMicronautCatalog("micronaut-rxjava2")
-    importMicronautCatalog("micronaut-test")
+    importMicronautCatalog("micronaut-rxjava3")
```

---

## Added Files

- `.agents/` _(directory — content not inspected)_
- `.github/workflows/sonatype.yml`
- `.sdkmanrc`
- `buildSrc/gradle.properties`
- `src/main/docs/guide/breaks.adoc` _(new breaking changes page)_
- `validation/src/test/groovy/io/micronaut/validation/validator/constraints/custom/CustomValidatorDependency.java`
- `validation/src/test/groovy/io/micronaut/validation/validator/constraints/custom/IntrospectedSingletonValidator.java`
- `validation/src/test/groovy/io/micronaut/validation/validator/constraints/custom/MisconfiguredConstraint.java`

---

## Removed Files

_(none)_

---

## Modified Files

### Nullability annotation migration (pervasive — ~50+ files)

All main source files and most test files have `io.micronaut.core.annotation.{NonNull,Nullable}` replaced by `org.jspecify.annotations.{NonNull,Nullable}`. This affects the entire `validation/`, `validation-processor/`, `test-suite/`, and `test-suite-groovy/` modules. Not individually listed below — treat as a baseline change across the board.

---

### Breaking changes: `DefaultValidator.java`

Two previously-deprecated public static methods are now `private` (breaking API change):

```diff
-    @Deprecated(since = "4.3.0")
-    public static <T> T requireNonNull(String name, T value) {
+    private static <T> T requireNonNull(String name, T value) {

-    @Deprecated(since = "4.3.0")
-    public static String requireNonEmpty(String name, String value) {
+    private static String requireNonEmpty(String name, String value) {
```

Also fixes for generic type-safety (explicit `Argument<Object>` casts replacing unchecked `Argument<Object>[]` usages):

```diff
-        Argument<Object> typeParameter = returnType.getTypeParameters()[0];
+        Argument<Object> typeParameter = (Argument<Object>) returnType.getTypeParameters()[0];

-        Argument<Object>[] typeParameters = publisherArgument.getTypeParameters();
+        Argument<?>[] typeParameters = publisherArgument.getTypeParameters();
```

---

### Breaking changes: `ConstraintValidator.java`

Removes `getMessageTemplate()` (deprecated since 4.3.0, marked `forRemoval = true`):

```diff
-            @Deprecated(since = "4.3.0", forRemoval = true)
-            public Optional<String> getMessageTemplate() {
-                return Optional.empty();
-            }
```

---

### `src/main/docs/guide/breaks.adoc` _(added)_

New breaking changes documentation page listing:

- `DefaultValidator.requireNonNull(String, T)` and `requireNonEmpty(String, String)` no longer part of the public API
- `ConstraintValidator.getMessageTemplate()` removed (was unused, no replacement)

---

### RxJava2 → RxJava3 migration

`BookServiceRxJava2` class renamed to `BookServiceRxJava3` with all reactive imports updated:

```diff
-import io.reactivex.Completable;
-import io.reactivex.Flowable;
-import io.reactivex.Maybe;
-import io.reactivex.Observable;
-import io.reactivex.Single;
+import io.reactivex.rxjava3.core.Completable;
+import io.reactivex.rxjava3.core.Flowable;
+import io.reactivex.rxjava3.core.Maybe;
+import io.reactivex.rxjava3.core.Observable;
+import io.reactivex.rxjava3.core.Single;

-class BookServiceRxJava2 {
+class BookServiceRxJava3 {
```

---

### New test files: misconfigured constraint scenario

Three new test classes added to verify behavior when a `ConstraintValidator` is misconfigured as an `@Introspected @Singleton` bean (which conflicts with the validator factory mechanism):

- `MisconfiguredConstraint.java` — constraint annotation with `@Constraint(validatedBy = IntrospectedSingletonValidator.class)`
- `IntrospectedSingletonValidator.java` — `@Singleton @Introspected` validator with a constructor dependency, demonstrating the misconfiguration
- `CustomValidatorDependency.java` — singleton injected into the above validator

---

### `validation/build.gradle`

```diff
-    testImplementation platform(libs.groovy.bom)
-    testImplementation mnRxjava2.micronaut.rxjava2
+    testImplementation mnRxjava3.micronaut.rxjava3
+    testImplementation(platform(mn.boms.groovy))

-    testRuntimeOnly(libs.junit.jupiter.engine)
+    testRuntimeOnly(mnTest.junit.jupiter.engine)

-    jmhAnnotationProcessor("org.openjdk.jmh:jmh-generator-annprocess:1.36")
+    jmhAnnotationProcessor("org.openjdk.jmh:jmh-generator-annprocess:1.37")
```

Groovy BOM now sourced from `mn.boms.groovy` (Micronaut BOM) instead of an explicit `groovy.bom` catalog entry.

---

### `test-suite/build.gradle` and `test-suite-groovy/build.gradle`

```diff
-    testRuntimeOnly libs.junit.jupiter.engine
+    testRuntimeOnly mnTest.junit.jupiter.engine
```

---

### GitHub Actions: CI / Workflow Changes

Same mn5 pattern as other repos (JDK 25, SHA-pinned actions, Sonatype scan extracted, "Remove system JDKs" step added, secrets withheld on PRs).

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
