# Diff Report: `4.8.x` vs `5.0.x`

**Generated:** 2026-04-16
**Base (A):** `mn4/micronaut-rss` — branch `4.8.x` @ `93c9d13b` — _chore: Bump version to 4.8.2-SNAPSHOT_
**Comparison (B):** `mn5/micronaut-rss` — branch `5.0.x` @ `1b2965dd` — _[skip ci] Release v5.0.0-M2_

---

## Summary

| Category | Count |
|----------|-------|
| Files added (only in B) | 3 |
| Files removed (only in A) | 0 |
| Files modified | 42 |
| Binary files (skipped) | 2 (`gradle-wrapper.jar`, `gradlew`) |
| **Total** | **45** |

---

## Dependency Changes

### `gradle/libs.versions.toml`

```diff
-micronaut-serde = "2.16.2"
-micronaut-validation = "4.12.0"
-micronaut-logging = "1.7.1"
-micronaut-docs = "3.0.0"
-micronaut = "4.10.8"
-micronaut-test = "4.10.2"
-groovy = "4.0.27"
-spock = "2.3-groovy-4.0"
+micronaut-serde = "3.0.0-M6"
+micronaut-validation = "5.0.0-M1"
+micronaut-logging = "1.7.4"
+micronaut = "5.0.0-M20"
```

> ⚠️ Several version entries removed: `micronaut-docs`, `micronaut-test`, `groovy`, `spock` — likely moved to the shared settings plugin.

### `gradle.properties`

```diff
-projectVersion=4.8.2-SNAPSHOT
+projectVersion=5.0.0-M2
```

### `settings.gradle`

```diff
-id("io.micronaut.build.shared.settings") version "7.6.6"
+id("io.micronaut.build.shared.settings") version "8.0.0-M17"
```

### `gradle/wrapper/gradle-wrapper.properties`

```diff
-distributionUrl=https\://services.gradle.org/distributions/gradle-8.14.3-bin.zip
+distributionUrl=https\://services.gradle.org/distributions/gradle-9.4.1-bin.zip
```

### `buildSrc/src/main/groovy/io.micronaut.build.internal.rss-module.gradle`

```diff
-
 dependencies {
     annotationProcessor mn.micronaut.inject.java
```

> Minor: blank line removed before `dependencies` block.

---

## Added Files

- `.agents/` _(directory — contents not diffed)_
- `.github/workflows/sonatype.yml` _(new Sonatype publishing workflow)_
- `.sdkmanrc` _(SDK version pinning for sdkman)_

---

## Removed Files

_(none)_

---

## Modified Files

### Source Code

#### `rss-core/src/main/java/io/micronaut/rss/RssChannel.java`

```diff
-import io.micronaut.core.annotation.NonNull;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.NonNull;
+import org.jspecify.annotations.Nullable;
```

#### `rss-core/src/main/java/io/micronaut/rss/RssChannelImage.java`

```diff
-import io.micronaut.core.annotation.NonNull;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.NonNull;
+import org.jspecify.annotations.Nullable;
```

#### `rss-core/src/main/java/io/micronaut/rss/RssItem.java`

```diff
-import io.micronaut.core.annotation.NonNull;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.NonNull;
+import org.jspecify.annotations.Nullable;
```

#### `rss-core/src/main/java/io/micronaut/rss/RssItemEnclosure.java`

```diff
-import io.micronaut.core.annotation.NonNull;
+import org.jspecify.annotations.NonNull;
```

#### `rss-core/src/main/java/io/micronaut/rss/DefaultRssFeedRenderer.java`

```diff
-import io.micronaut.core.annotation.NonNull;
+import org.jspecify.annotations.NonNull;
```

#### `rss/src/main/java/io/micronaut/rss/http/FeedController.java`

```diff
-import io.micronaut.core.annotation.NonNull;
+import org.jspecify.annotations.NonNull;
```

#### `rss-language/src/main/java/io/micronaut/rss/language/RssLanguage.java`

```diff
-import io.micronaut.core.annotation.NonNull;
+import org.jspecify.annotations.NonNull;
```

#### `itunespodcast/src/main/java/io/micronaut/rss/itunespodcast/ItunesPodcast.java`

```diff
-import io.micronaut.core.annotation.NonNull;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.NonNull;
+import org.jspecify.annotations.Nullable;
```

#### `itunespodcast/src/main/java/io/micronaut/rss/itunespodcast/ItunesPodcastEpisode.java`

```diff
-import io.micronaut.core.annotation.NonNull;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.NonNull;
+import org.jspecify.annotations.Nullable;
```

#### `itunespodcast/src/main/java/io/micronaut/rss/itunespodcast/ItunesPodcastOwner.java`

```diff
-import io.micronaut.core.annotation.NonNull;
+import org.jspecify.annotations.NonNull;
```

#### `jsonfeed-core/src/main/java/io/micronaut/rss/jsonfeed/JsonFeed.java`

```diff
-import io.micronaut.core.annotation.NonNull;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.NonNull;
+import org.jspecify.annotations.Nullable;
```

#### `jsonfeed-core/src/main/java/io/micronaut/rss/jsonfeed/JsonFeedAttachment.java`

```diff
-import io.micronaut.core.annotation.NonNull;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.NonNull;
+import org.jspecify.annotations.Nullable;
```

#### `jsonfeed-core/src/main/java/io/micronaut/rss/jsonfeed/JsonFeedAuthor.java`

```diff
-import io.micronaut.core.annotation.NonNull;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.NonNull;
+import org.jspecify.annotations.Nullable;

-@Introspected
+@Introspected(excludes = "empty")
```

> ⚠️ Notable: `@Introspected` now excludes the `"empty"` property to prevent it from leaking into JSON serialization.

#### `jsonfeed-core/src/main/java/io/micronaut/rss/jsonfeed/JsonFeedItem.java`

```diff
-import io.micronaut.core.annotation.NonNull;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.NonNull;
+import org.jspecify.annotations.Nullable;
```

#### `jsonfeed-core/src/main/java/io/micronaut/rss/jsonfeed/JsonHub.java`

```diff
-import io.micronaut.core.annotation.NonNull;
+import org.jspecify.annotations.NonNull;
```

#### `jsonfeed/src/main/java/io/micronaut/rss/jsonfeed/http/JsonFeedController.java`

```diff
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
```

#### `jsonfeed/src/main/java/io/micronaut/rss/jsonfeed/http/JsonFeedControllerConfiguration.java`

```diff
-import io.micronaut.core.annotation.NonNull;
+import org.jspecify.annotations.NonNull;
```

#### `jsonfeed/src/main/java/io/micronaut/rss/jsonfeed/http/JsonFeedControllerConfigurationProperties.java`

```diff
-import io.micronaut.core.annotation.NonNull;
+import org.jspecify.annotations.NonNull;
```

#### `jsonfeed/src/main/java/io/micronaut/rss/jsonfeed/http/JsonFeedProvider.java`

```diff
-import io.micronaut.core.annotation.NonNull;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.NonNull;
+import org.jspecify.annotations.Nullable;
```

---

### Tests

#### `jsonfeed/src/test/java/io/micronaut/rss/jsonfeed/http/ExampleJsonFeedProvider.java`

```diff
-import io.micronaut.core.annotation.NonNull;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.NonNull;
+import org.jspecify.annotations.Nullable;
+import io.micronaut.rss.jsonfeed.JsonFeedAuthor;

 .feedUrl("https://example.org/feed.json")
+.author(JsonFeedAuthor.builder()
+        .name("Feed Author")
+        .url("mailto:feed@example.org")
+        .build())
 .item(JsonFeedItem.builder()
     .id("2")
     .contentText("This is a second item.")
+    .author(JsonFeedAuthor.builder()
+            .name("Item Author")
+            .build())
```

> ⚠️ Notable: test provider now populates `author` at both feed and item level.

#### `jsonfeed/src/test/groovy/io/micronaut/rss/jsonfeed/http/JsonFeedControllerSpec.groovy`

```diff
+    "authors": [{ "name": "Feed Author", "url": "mailto:feed@example.org" }],
     "items": [{
         "id": "2",
+        "authors": [{ "name": "Item Author" }],
     ...
+    m['authors'][0]['name'] == result['authors'][0]['name']
+    !result['authors'][0].containsKey('empty')
+    m['items'][0]['authors'][0]['name'] == result['items'][0]['authors'][0]['name']
+    !result['items'][0]['authors'][0].containsKey('empty')
```

> Tests now assert that `empty` is not serialized in `authors`.

#### `jsonfeed-core/src/test/groovy/io/micronaut/rss/jsonfeed/JsonFeedAuthorSpec.groovy`

```diff
+import groovy.json.JsonSlurper

-BeanIntrospection.getIntrospection(JsonFeedAuthor)
+BeanIntrospection<JsonFeedAuthor> introspection = BeanIntrospection.getIntrospection(JsonFeedAuthor)
+!introspection.propertyNames.contains("empty")

+void "json serialization does not include empty property"() {
+    // verifies empty is not in serialized output
+}
```

#### `jsonfeed-core/src/test/groovy/io/micronaut/rss/jsonfeed/JsonFeedItemSpec.groovy`

```diff
+void "serialized feed authors do not include empty property"() {
+    // verifies authors[].empty not in serialized JsonFeed/JsonFeedItem output
+}
```

---

### CI / Workflows

#### Key changes across all workflow files

- All `actions/checkout`, `actions/setup-java`, `actions/upload-artifact`, `actions/download-artifact`, `gradle/actions/*`, `graalvm/setup-graalvm`, `micronaut-projects/github-actions/*`, and `micronaut-projects/github-pages-deploy-action` references pinned to **commit SHAs** (supply-chain security hardening).
- Java version matrix changed from `['17', '21']` → `['25']` across `gradle.yml`, `graalvm-latest.yml`, `central-sync.yml`, `release.yml`, `publish-snapshot.yml`.
- Develocity / secret env vars now use `github.event.pull_request == null && secrets.X || ''` pattern to avoid exposing secrets on PRs from forks.
- `gradle.yml`: removed Sonatype OSS Index audit step; Sonar/binary-compat/publish steps updated from `java == '17'` to `java == '25'`; Gradle wrapper from `v5` → `v6`.
- `release.yml`: `LATEST_TAG` curl no longer passes `GH_TOKEN_PUBLIC_REPOS_READONLY`; added `ref: ${{ github.sha }}` to final checkout; `sonatype.yml` added as new workflow.

#### `.github/renovate.json`

```diff
+{
+  "matchDatasources": ["maven"],
+  "matchManagers": ["maven", "gradle"],
+  "allowedVersions": "!/.+-SNAPSHOT$/"
+},
```

> Renovate now blocks SNAPSHOT versions for maven/gradle dependencies.

---

### Tooling / Config

#### `.gitignore`

```diff
+# Ignore gradle.properties generated by micronaut-build
+/buildSrc/gradle.properties
+
+# OpenCode files
+.sisyphus/
```

#### `.clineignore`

```diff
+!build/generated/
+!build/generated/**
```

#### `.clinerules/coding.md` and `.github/instructions/coding.instructions.md`

```diff
-You MUST annotate the code with nullability annotations (`io.micronaut.core.annotation.Nullable`, `io.micronaut.core.annotation.NonNull`).
+You MUST annotate the code with nullability annotations (`org.jspecify.annotations.Nullable`, `org.jspecify.annotations.NonNull`).
```

#### `MAINTAINING.md`

Minor: British → American English spelling (`categorised` → `categorized`, `customisations` → `customizations`).

---

## Key Themes

1. **JSpecify migration** — all `io.micronaut.core.annotation.{NonNull,Nullable}` imports replaced with `org.jspecify.annotations.{NonNull,Nullable}` across the entire codebase.
2. **Java 25** — CI matrix drops Java 17 and 21 in favour of Java 25 only.
3. **Gradle 9.4.1** — wrapper bumped from 8.14.3.
4. **Micronaut 5 milestone** — core `5.0.0-M20`, serde `3.0.0-M6`, validation `5.0.0-M1`.
5. **`@Introspected(excludes = "empty")`** — bug fix in `JsonFeedAuthor` to prevent `empty` getter from appearing in JSON output; covered by new tests.
6. **Author support in JSON Feed** — `ExampleJsonFeedProvider` and its tests now exercise `author` at both feed and item level.
7. **Supply-chain security** — all GitHub Actions pinned to commit SHAs; secrets scoped away from fork PRs.

---

_Report generated by git-branch-diff skill._
