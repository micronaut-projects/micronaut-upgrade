# Diff Report: `3.9.x` vs `4.0.x`

**Generated:** 2026-04-16
**Base (A):** `mn4/micronaut-rxjava3` — branch `3.9.x` @ `5417071a` — _chore: Bump version to 3.9.1-SNAPSHOT_
**Comparison (B):** `mn5/micronaut-rxjava3` — branch `4.0.x` @ `47efa0ac` — _Update softprops/action-gh-release action to v2.6.2 (#493)_

---

## Summary

| Category | Count |
|----------|-------|
| Files added (only in B) | 4 |
| Files removed (only in A) | 0 |
| Files modified | 30 |
| Binary files (skipped) | 2 (`gradle-wrapper.jar`, `gradlew`) |
| Generated/cached (skipped) | 4 (`.gradle/`, `build/`, `buildSrc/build/`, `buildSrc/gradle.properties`) |
| **Total** | **34** |

---

## Dependency Changes

### `gradle/libs.versions.toml`

```diff
-micronaut = "4.10.4"
-micronaut-rxjava2 = "2.8.0"
-micronaut-docs = "3.0.0"
-micronaut-test = "4.9.0"
-groovy = "4.0.25"
-spock = "2.3-groovy-4.0"
+micronaut = "5.0.0-M22"
+micronaut-rxjava2 = "2.9.0"
```

> `micronaut-docs`, `micronaut-test`, `groovy`, `spock` removed — sourced from shared settings plugin in mn5. `micronaut-rxjava2` bumped `2.8.0` → `2.9.0`.

### `gradle.properties`

```diff
-projectVersion=3.9.1-SNAPSHOT
+projectVersion=4.0.0-SNAPSHOT
```

### `settings.gradle`

```diff
-id("io.micronaut.build.shared.settings") version "7.6.4"
+id("io.micronaut.build.shared.settings") version "8.0.0-M17"
```

### `gradle/wrapper/gradle-wrapper.properties`

```diff
-distributionUrl=...gradle-8.14.3-bin.zip
+distributionUrl=...gradle-9.4.1-bin.zip
```

---

## Added Files

- `.agents/` _(directory)_
- `.github/workflows/sonatype.yml` _(new Sonatype publishing workflow)_
- `.sdkmanrc` _(SDK version pinning)_
- `.gradle/` _(generated Gradle cache — should be gitignored, present in mn5 checkout)_

---

## Removed Files

_(none)_

---

## Modified Files

### Source Code

All 15 source files have the same single change: **JSpecify migration**.

`io.micronaut.core.annotation.NonNull` / `Nullable` → `org.jspecify.annotations.NonNull` / `Nullable`

Affected files:

- `rxjava3/src/main/java/io/micronaut/rxjava3/converters/RxJava3ConverterRegistrar.java`
- `rxjava3-http-client/src/main/java/io/micronaut/rxjava3/http/client/BridgedRx3HttpClient.java`
- `rxjava3-http-client/src/main/java/io/micronaut/rxjava3/http/client/BridgedRx3StreamingHttpClient.java`
- `rxjava3-http-client/src/main/java/io/micronaut/rxjava3/http/client/Rx3HttpClient.java`
- `rxjava3-http-client/src/main/java/io/micronaut/rxjava3/http/client/Rx3HttpClientFactory.java`
- `rxjava3-http-client/src/main/java/io/micronaut/rxjava3/http/client/Rx3SseClient.java`
- `rxjava3-http-client/src/main/java/io/micronaut/rxjava3/http/client/Rx3StreamingHttpClient.java`
- `rxjava3-http-client/src/main/java/io/micronaut/rxjava3/http/client/proxy/BridgedProxyRx3HttpClient.java`
- `rxjava3-http-client/src/main/java/io/micronaut/rxjava3/http/client/proxy/Rx3ProxyHttpClient.java`
- `rxjava3-http-client/src/main/java/io/micronaut/rxjava3/http/client/proxy/Rx3ProxyHttpClientFactory.java`
- `rxjava3-http-client/src/main/java/io/micronaut/rxjava3/http/client/sse/BridgedRx3SseClient.java`
- `rxjava3-http-client/src/main/java/io/micronaut/rxjava3/http/client/sse/RxSseClientFactory.java`
- `rxjava3-http-client/src/main/java/io/micronaut/rxjava3/http/client/websockets/Rx3WebSocketClient.java`
- `rxjava3-http-client/src/main/java/io/micronaut/rxjava3/http/client/websockets/Rx3WebSocketClientFactory.java`

---

### CI / Workflows

Identical pattern to micronaut-reactor `4.0.x`:

- All GitHub Actions pinned to **commit SHAs**.
- Java matrix `['17', '21']` → `['25']` across all workflows.
- Branch trigger regex `[1-9]+` → `[0-9]+` in `gradle.yml` and `graalvm-latest.yml`.
- JVM cleanup step (`sudo rm -rf /usr/lib/jvm/*`) added before checkout in all workflows.
- Develocity/secret env vars scoped away from fork PRs.
- `graalvm-dev.yml`: `nativeTestTask` now passed to `pre-build`.
- `graalvm-latest.yml`: `gradle-java: '25'` and `nativeTestTask` added to `pre-build`.
- `gradle.yml`: removed Sonatype OSS Index audit; added optional `cleanup.sh`; Gradle actions `v4` → `v6`; freed additional disk space (`/opt/ghc`, `/usr/share/dotnet`, `/usr/local/lib/android`).
- `release.yml`: `LATEST_TAG` step added; `BETA` flag improved; `ref: ${{ github.sha }}` added to final checkout; `softprops/action-gh-release` `v2.4.1` → `v2.6.2`.
- `publish-snapshot.yml`: JVM cleanup step added.

### `.github/renovate.json`

```diff
+{
+  "matchDatasources": ["maven"],
+  "matchManagers": ["maven", "gradle"],
+  "allowedVersions": "!/.+-SNAPSHOT$/"
+},
```

---

### Tooling / Config

#### `.gitignore`

```diff
+/buildSrc/gradle.properties
+.sisyphus/
```

#### `.clineignore`

```diff
+!build/generated/
+!build/generated/**
```

#### `.clinerules/coding.md` and `.github/instructions/coding.instructions.md`

```diff
-nullability annotations (`io.micronaut.core.annotation.Nullable`, `io.micronaut.core.annotation.NonNull`)
+nullability annotations (`org.jspecify.annotations.Nullable`, `org.jspecify.annotations.NonNull`)
```

#### `MAINTAINING.md`

British → American English spelling (`categorised`, `prioritised`, `customisations` → American equivalents).

#### `gradlew.bat`

Removed `-classpath "%CLASSPATH%"` from the Java invocation line (Gradle wrapper no longer uses the classpath flag).

---

## Key Themes

1. **JSpecify migration** — identical to micronaut-rss and micronaut-reactor: all `io.micronaut.core.annotation.{NonNull,Nullable}` replaced with `org.jspecify.annotations.*` across all 15 source files. No other source changes.
2. **Micronaut 5.0.0-M22** — the only version bump in `libs.versions.toml` besides `micronaut-rxjava2` (`2.8.0` → `2.9.0`). This is a simpler dependency graph than reactor or rss — no tracing, serde, or validation BOMs.
3. **Gradle 9.4.1** — up from 8.14.3.
4. **Branch regex fix** — `[1-9]+` → `[0-9]+` to support `4.0.x`.
5. **CI hardening** — same SHA-pinning, fork PR secret isolation, and JVM cleanup pattern as micronaut-reactor.
6. **No test or build script changes** — unlike micronaut-reactor, there are no changes to test suites or `buildSrc` gradle files beyond what's generated.

---

_Report generated by git-branch-diff skill._
