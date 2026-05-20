# Diff Report: micronaut-logging 1.7.x vs 2.0.x

| Property | mn4 (1.7.x) | mn5 (2.0.x) |
|---|---|---|
| Branch | `1.7.x` | `2.0.x` |
| Latest commit | `68d416e` chore: Bump version to 1.7.5-SNAPSHOT | `d1a5409` fix(deps): update dependency io.micronaut:micronaut-core-bom to v5.0.0-m22 (#303) |
| Project version | 1.7.5-SNAPSHOT | 2.0.0-SNAPSHOT |
| Micronaut | 4.10.15 | 5.0.0-M22 |
| Gradle | 8.14.3 | 9.4.1 |
| Shared settings plugin | 7.6.6 | 8.0.0-M17 |
| Java matrix | `['17', '21']` | `['25']` |

**Total changes: 23** (2 added, 21 modified, 1 binary skipped)

> **Notable:** No source file changes — micronaut-logging requires no JSpecify migration. All changes are infrastructure/build.

---

## Summary Table

| File | Change |
|---|---|
| `.sdkmanrc` | Added |
| `.github/workflows/sonatype.yml` | Added |
| `.agents/` | Added (directory) |
| `.clineignore` | Modified |
| `.clinerules/coding.md` | Modified |
| `.github/instructions/coding.instructions.md` | Modified |
| `.github/renovate.json` | Modified |
| `.github/workflows/central-sync.yml` | Modified |
| `.github/workflows/graalvm-dev.yml` | Modified |
| `.github/workflows/graalvm-latest.yml` | Modified |
| `.github/workflows/gradle.yml` | Modified |
| `.github/workflows/publish-snapshot.yml` | Modified |
| `.github/workflows/release.yml` | Modified |
| `.github/workflows/update-gradle-wrapper.yml` | Modified |
| `.gitignore` | Modified |
| `MAINTAINING.md` | Modified |
| `gradle/libs.versions.toml` | Modified |
| `gradle/wrapper/gradle-wrapper.jar` | Modified (binary, skipped) |
| `gradle/wrapper/gradle-wrapper.properties` | Modified |
| `gradle.properties` | Modified |
| `gradlew` | Modified |
| `gradlew.bat` | Modified |
| `settings.gradle.kts` | Modified |
| `test-suite/build.gradle.kts` | Modified |

---

## Dependency Changes

### `gradle/libs.versions.toml`

```diff
-micronaut = "4.10.15"
+micronaut = "5.0.0-M22"

-managed-log4j = "2.25.3"
+managed-log4j = "2.25.4"
```

Quote style also changed from `"` to `'` for the `micronaut-core` library entry.

### `settings.gradle.kts`

```diff
-id("io.micronaut.build.shared.settings") version "7.6.6"
+id("io.micronaut.build.shared.settings") version "8.0.0-M17"
```

### `gradle/wrapper/gradle-wrapper.properties`

```diff
-distributionUrl=https\://services.gradle.org/distributions/gradle-8.14.3-bin.zip
+distributionUrl=https\://services.gradle.org/distributions/gradle-9.4.1-bin.zip
```

---

## Added Files

### `.sdkmanrc`

```
java=25.0.1-graal
```

Pins the GraalVM JDK 25 via SDKMAN for local dev.

### `.github/workflows/sonatype.yml` (new workflow)

Dedicated Sonatype OSS Index vulnerability scan workflow, extracted from `gradle.yml`. Runs on push/PR to `master` and `[0-9]+.[0-9]+.x`. Executes `./gradlew ossIndexAudit` when `OSS_INDEX_PASSWORD` is set.

---

## Modified Files

### `.clineignore`

```diff
+!build/generated/
+!build/generated/**
```

Allows generated sources in build output.

### `.clinerules/coding.md` / `.github/instructions/coding.instructions.md`

JSpecify reference update (documentation only, no source changes needed in this repo):

```diff
-You MUST annotate the code with nullability annotations (`io.micronaut.core.annotation.Nullable`, `io.micronaut.core.annotation.NonNull`).
+You MUST annotate the code with nullability annotations (`org.jspecify.annotations.Nullable`, `org.jspecify.annotations.NonNull`).
```

### `.github/renovate.json`

Added rule to block SNAPSHOT versions from being auto-updated:

```diff
+    {
+      "matchDatasources": ["maven"],
+      "matchManagers": ["maven", "gradle"],
+      "allowedVersions": "!/.+-SNAPSHOT$/"
+    },
```

### `.github/workflows/gradle.yml`

- Branch regex: `[1-9]+.[0-9]+.x` → `[0-9]+.[0-9]+.x`
- Java matrix: `['17', '21']` → `['25']`
- Fork PR secret isolation (all secrets via `github.event.pull_request == null && secrets.X || ''`)
- SHA-pinned action references
- `PREDICTIVE_TEST_SELECTION` env var removed
- `OSS_INDEX_PASSWORD` secret added (fork-isolated)
- Sonatype scan step removed (moved to `sonatype.yml`)
- Build task: `./gradlew check` → `./gradlew check jacocoReport`
- Sonar condition: `matrix.java == '17'` → `matrix.java == '25'`
- Binary compatibility upload condition: `matrix.java == '17'` → `matrix.java == '25'`
- Snapshot publish condition: `matrix.java == '17'` → `matrix.java == '25'`
- Docs publish condition: `matrix.java == '17'` → `matrix.java == '25'`
- Added "Remove system JDKs" step
- Added extended disk cleanup (`/opt/ghc`, `/usr/share/dotnet`, `/usr/local/lib/android`)
- Added optional `cleanup.sh` step at end

### `.github/workflows/graalvm-latest.yml`

- Branch regex: `[1-9]+` → `[0-9]+`
- Java matrix: `['17', '21']` → `['25']`
- Fork PR secret isolation
- SHA-pinned actions
- Added `java-version: '25'` param to build-matrix step
- Added `gradle-java: '25'` and `nativeTestTask` params to pre-build step
- `GH_TOKEN_PUBLIC_REPOS_READONLY` and `GH_USERNAME` fork-isolated
- Added "Remove system JDKs" step

### `.github/workflows/graalvm-dev.yml`

- SHA-pinned `micronaut-projects/github-actions` actions (SHA `300bf6db`)
- SHA-pinned `actions/checkout@v6`
- Added `nativeTestTask` param to pre-build step
- Added "Remove system JDKs" step

### `.github/workflows/central-sync.yml` / `publish-snapshot.yml`

- SHA-pinned actions
- Java: `17\n21` → `25`
- Added "Remove system JDKs" step

### `.github/workflows/release.yml`

- SHA-pinned actions (`upload-artifact` v4→v7, `download-artifact` v5→v8, `checkout` v5→v6)
- Java: `17\n21` → `25`
- Added "Remove system JDKs" step
- BETA detection reworked:

```diff
-BETA: ${{ !(github.event.release.target_commitish == github.event.repository.default_branch) || contains(...) }}
+BETA: ${{ !(github.event.release.tag_name == env.LATEST_TAG) || github.event.release.draft || github.event.release.prerelease || contains(...) }}
```

New step fetches `LATEST_TAG` from GitHub API before the pages deploy step.

- Added `ref: ${{ github.sha }}` to checkout in the `central-publish` job.
- `slsa-github-generator` pinned by SHA.

### `.github/workflows/update-gradle-wrapper.yml`

```diff
-uses: actions/checkout@v5
+uses: actions/checkout@v6
-uses: stefanzweifel/git-auto-commit-action@v5
+uses: stefanzweifel/git-auto-commit-action@v7
```

### `.gitignore`

```diff
+# Ignore gradle.properties generated by micronaut-build
+/buildSrc/gradle.properties
+
+# OpenCode files
+.sisyphus/
```

### `MAINTAINING.md`

British → American English spelling: `categorised` → `categorized`, `customisations` → `customizations` (3 occurrences).

### `gradle.properties`

```diff
-projectVersion=1.7.5-SNAPSHOT
+projectVersion=2.0.0-SNAPSHOT
```

### `gradlew` / `gradlew.bat`

Gradle 9 wrapper: `CLASSPATH` argument removed from JVM invocation (wrapper JAR no longer needs `-classpath` flag). Script template URL pinned to specific commit.

### `test-suite/build.gradle.kts`

Added Sonatype OSS Index Audit plugin with conditional configuration:

```kotlin
plugins {
    `java-library`
    id("org.sonatype.gradle.plugins.scan")
}

val ossIndexUsername = System.getenv("OSS_INDEX_USERNAME") ?: project.properties["ossIndexUsername"] as String?
val ossIndexPassword = System.getenv("OSS_INDEX_PASSWORD") ?: project.properties["ossIndexPassword"] as String?
val sonatypePluginConfigured = ossIndexUsername != null && ossIndexPassword != null

ossIndexAudit {
    if (sonatypePluginConfigured) {
        username = ossIndexUsername
        password = ossIndexPassword
    } else {
        tasks.named("ossIndexAudit").configure { enabled = false }
    }
}
```
