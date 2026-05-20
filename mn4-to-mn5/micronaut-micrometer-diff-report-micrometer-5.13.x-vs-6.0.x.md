# Diff Report: `5.13.x` vs `6.0.x` (micronaut-micrometer)

**Generated:** 2026-04-22
**Base (A):** `/Users/sdelamo/github/micronaut/mn4/micronaut-micrometer` — branch `5.13.x` @ `79c23958`
**Comparison (B):** `/Users/sdelamo/github/micronaut/mn5/micronaut-micrometer` — branch `6.0.x` @ `52027f71`

---

## Summary

| Category | Count |
|----------|-------|
| Top-level added entries (only in B) | 11 |
| Top-level removed entries (only in A) | 2 |
| Files modified | 57 |

> Notes:
> - `.agents/` directory (14 skill files) added in B.
> - Netty event loop group factories added in B (`InstrumentedEpollEventLoopGroupFactory`, `InstrumentedKQueueEventLoopGroupFactory`, `InstrumentedNioEventLoopGroupFactory`, `InstrumentedEventLoopTaskQueueFactory`) replacing the removed `InstrumentedTaskQueueInterceptor`.
> - `ReactorSchedulersMicrometerTest` removed in B.
> - `test-suite:micronaut-serialization` and `test-suite:test-observation-datasource` are now commented out in `settings.gradle` (modules kept in tree but not included in the build).
> - RxJava2 integration replaced by RxJava3 (`micronaut-rxjava2` → `micronaut-rxjava3`).
> - `gradle/wrapper/gradle-wrapper.jar` binary differs; content not shown.

---

## Dependency Changes

### Third-Party Upgrades

- `gradle`: `8.14.3` → `9.4.1` — [Release notes](https://docs.gradle.org/9.4.1/release-notes.html)
- `io.micrometer:micrometer-*` (managed-micrometer): `1.15.4` → `1.16.5` — [Release notes](https://github.com/micrometer-metrics/micrometer/releases/tag/v1.16.5)
- `io.micrometer:micrometer-tracing-*` (managed-micrometer-tracing): `1.5.4` → `1.6.5` — [Release notes](https://github.com/micrometer-metrics/tracing/releases/tag/v1.6.5)
- `io.dropwizard.metrics:metrics-core` (managed-metrics-core): `4.2.37` → `4.2.38` — [Release notes](https://github.com/dropwizard/metrics/releases/tag/v4.2.38)
- `io.prometheus:prometheus-metrics-exporter-pushgateway` (managed-prometheus-metrics-exporter-pushgateway): `1.4.1` → `1.5.1` — [Release notes](https://github.com/prometheus/client_java/releases)
- `net.ttddyy.observation:datasource-micrometer` (managed-datasource-micrometer): `1.2.0` → `2.2.1` — [Release notes](https://github.com/jdbc-observations/datasource-micrometer/releases/tag/2.2.1)

### Micronaut Version Bumps

- `micronaut-platform`: `4.9.4` → `5.0.0-M2`
- `micronaut`: `4.10.9` → `5.0.0-M23`
- `micronaut-gradle-plugin`: `4.5.5` → `5.0.0-M1`
- `micronaut-aws`: `4.11.0` → `5.0.0-M3`
- `micronaut-cache`: `5.3.0` → `6.0.0-M3`
- `micronaut-grpc`: `4.12.0` → `5.0.0-M1`
- `micronaut-r2dbc`: `6.1.0` → `7.0.1-M1`
- `micronaut-reactor`: `3.9.0` → `4.0.0-M2`
- `micronaut-serde`: `2.15.5` → `3.0.0-M7`
- `micronaut-sql`: `6.3.0` → `7.0.1-M2`
- `micronaut-data`: `4.13.7` → `5.0.0-M6`
- `micronaut-validation`: `4.11.0` → `5.0.0-M2`
- `micronaut-logging`: `1.7.1` → `2.0.0-M2`
- `io.micronaut.build.shared.settings` plugin: `7.6.4` → `8.0.0-M17`
- `micronaut-test` (`4.9.0`): **removed** from versions
- `micronaut-docs` (`3.0.0`): **removed** from versions
- `groovy` (`4.0.26`) / `spock` (`2.3-groovy-4.0`) version pins: **removed**

### RxJava Migration

- `micronaut-rxjava2` `2.8.0` **replaced** by `micronaut-rxjava3` `4.0.0-M1` (catalog import and bom).

### Project Version

- `projectVersion`: `5.13.3-SNAPSHOT` → `6.0.0-SNAPSHOT`

### Removed

- `micronautSerializationVersion=1.3.2` removed from `gradle.properties`.

### `gradle/libs.versions.toml`
```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/gradle/libs.versions.toml	2026-04-22 08:03:55.465006753 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/gradle/libs.versions.toml	2026-04-22 08:06:30.295151440 +0000
@@ -1,34 +1,30 @@
 [versions]
-micronaut-platform = "4.9.4"
-micronaut = "4.10.9"
-micronaut-docs = "3.0.0"
-micronaut-gradle-plugin = "4.5.5"
-micronaut-test = "4.9.0"
-groovy = "4.0.26"
-spock = "2.3-groovy-4.0"
+micronaut-platform = "5.0.0-M2"
+micronaut = "5.0.0-M23"
+micronaut-gradle-plugin = "5.0.0-M1"
 
-managed-metrics-core = '4.2.37'
-managed-micrometer = '1.15.4'
-managed-micrometer-tracing = '1.5.4'
+managed-metrics-core = '4.2.38'
+managed-micrometer = '1.16.5'
+managed-micrometer-tracing = '1.6.5'
 managed-new-relic-registry = '0.10.0'
-managed-prometheus-metrics-exporter-pushgateway = '1.4.1'
-managed-datasource-micrometer = '1.2.0'
+managed-prometheus-metrics-exporter-pushgateway = '1.5.1'
+managed-datasource-micrometer = '2.2.1'
 reflections = '0.10.2'
 
 jcache = "1.1.1"
 hdr-histogram = '2.2.2'
 
-micronaut-aws = "4.11.0"
-micronaut-cache = "5.3.0"
-micronaut-grpc = "4.12.0"
-micronaut-logging = "1.7.1"
-micronaut-r2dbc = "6.1.0"
-micronaut-rxjava2 = "2.8.0"
-micronaut-reactor = "3.9.0"
-micronaut-serde = "2.15.5"
-micronaut-sql = "6.3.0"
-micronaut-data = "4.13.7"
-micronaut-validation = "4.11.0"
+micronaut-aws = "5.0.0-M3"
+micronaut-cache = "6.0.0-M3"
+micronaut-grpc = "5.0.0-M1"
+micronaut-r2dbc = "7.0.1-M1"
+micronaut-rxjava3 = "4.0.0-M1"
+micronaut-reactor = "4.0.0-M2"
+micronaut-serde = "3.0.0-M7"
+micronaut-sql = "7.0.1-M2"
+micronaut-data = "5.0.0-M6"
+micronaut-validation = "5.0.0-M2"
+micronaut-logging = "2.0.0-M2"
 
 [libraries]
 # Core
@@ -40,7 +36,7 @@
 micronaut-cache = { module = "io.micronaut.cache:micronaut-cache-bom", version.ref = "micronaut-cache" }
 micronaut-grpc = { module = "io.micronaut.grpc:micronaut-grpc-bom", version.ref = "micronaut-grpc" }
 micronaut-r2dbc = { module = "io.micronaut.r2dbc:micronaut-r2dbc-bom", version.ref = "micronaut-r2dbc" }
-micronaut-rxjava2 = { module = "io.micronaut.rxjava2:micronaut-rxjava2-bom", version.ref = "micronaut-rxjava2" }
+micronaut-rxjava3 = { module = "io.micronaut.rxjava3:micronaut-rxjava3-bom", version.ref = "micronaut-rxjava3" }
 micronaut-reactor = { module = 'io.micronaut.reactor:micronaut-reactor-bom', version.ref = 'micronaut-reactor'}
 micronaut-serde = { module = "io.micronaut.serde:micronaut-serde-bom", version.ref = "micronaut-serde" }
 micronaut-sql = { module = "io.micronaut.sql:micronaut-sql-bom", version.ref = "micronaut-sql" }
```

### `gradle/wrapper/gradle-wrapper.properties`
```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/gradle/wrapper/gradle-wrapper.properties	2026-04-22 08:03:55.465400381 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/gradle/wrapper/gradle-wrapper.properties	2026-04-22 08:03:40.253439635 +0000
@@ -1,6 +1,6 @@
 distributionBase=GRADLE_USER_HOME
 distributionPath=wrapper/dists
-distributionUrl=https\://services.gradle.org/distributions/gradle-8.14.3-bin.zip
+distributionUrl=https\://services.gradle.org/distributions/gradle-9.4.1-bin.zip
 networkTimeout=10000
 validateDistributionUrl=true
 zipStoreBase=GRADLE_USER_HOME
```

### `gradle.properties`
```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/gradle.properties	2026-04-22 08:03:55.464870210 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/gradle.properties	2026-04-22 08:03:40.252910506 +0000
@@ -1,8 +1,6 @@
-projectVersion=5.13.3-SNAPSHOT
+projectVersion=6.0.0-SNAPSHOT
 projectGroup=io.micronaut.micrometer
 
-micronautSerializationVersion=1.3.2
-
 title=Micronaut Micrometer
 projectDesc=Provides integration between Micronaut and Micrometer
 projectUrl=https://micronaut.io
```

### `settings.gradle`
```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/settings.gradle	2026-04-22 08:03:55.512786718 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/settings.gradle	2026-04-22 08:03:40.310386590 +0000
@@ -6,7 +6,7 @@
 }
 
 plugins {
-    id('io.micronaut.build.shared.settings') version '7.6.4'
+    id('io.micronaut.build.shared.settings') version '8.0.0-M17'
 }
 
 rootProject.name = 'micrometer-parent'
@@ -39,8 +39,8 @@
 include 'micrometer-registry-stackdriver'
 include 'micrometer-registry-statsd'
 include 'micrometer-registry-wavefront'
-include 'test-suite:micronaut-serialization'
-include 'test-suite:test-observation-datasource'
+//include 'test-suite:micronaut-serialization'
+//include 'test-suite:test-observation-datasource'
 
 enableFeaturePreview 'TYPESAFE_PROJECT_ACCESSORS'
 
@@ -51,7 +51,7 @@
     importMicronautCatalog("micronaut-cache")
     importMicronautCatalog("micronaut-grpc")
     importMicronautCatalog("micronaut-r2dbc")
-    importMicronautCatalog("micronaut-rxjava2")
+    importMicronautCatalog("micronaut-rxjava3")
     importMicronautCatalog("micronaut-serde")
     importMicronautCatalog("micronaut-sql")
     importMicronautCatalog("micronaut-data")
```

---

## Added Files / Directories (only in B)

- `.agents/` (14 skill files under `agent-md-refactor`, `coding`, `docs`, `gradle`, `skill-creator`)
- `.github/workflows/sonatype.yml`
- `.sdkmanrc`
- `buildSrc/gradle.properties`
- `micrometer-core/src/main/java/io/micronaut/configuration/metrics/binder/netty/InstrumentedEpollEventLoopGroupFactory.java`
- `micrometer-core/src/main/java/io/micronaut/configuration/metrics/binder/netty/InstrumentedEventLoopTaskQueueFactory.java`
- `micrometer-core/src/main/java/io/micronaut/configuration/metrics/binder/netty/InstrumentedKQueueEventLoopGroupFactory.java`
- `micrometer-core/src/main/java/io/micronaut/configuration/metrics/binder/netty/InstrumentedNioEventLoopGroupFactory.java`
- `src/main/docs/guide/breaks.adoc`
- `test-suite/micronaut-serialization/src/test/resources/META-INF/native-image/.../native-image.properties`
- `test-suite/test-observation-datasource/src/test/resources/META-INF/native-image/.../native-image.properties`

## Removed Files / Directories (only in A)

- `micrometer-core/src/main/java/io/micronaut/configuration/metrics/binder/netty/InstrumentedTaskQueueInterceptor.java` (replaced by the new event-loop-group factories)
- `micrometer-core/src/test/java/io/micronaut/configuration/metrics/micrometer/` (`ReactorSchedulersMicrometerTest.java`)

---

## Modified Files

### `.clineignore`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/.clineignore	2026-04-22 08:03:55.461598309 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/.clineignore	2026-04-22 08:03:40.249468062 +0000
@@ -6,6 +6,8 @@
 */build/
 !build/docs/
 !build/docs/**
+!build/generated/
+!build/generated/**
 
 # === Dependency/Cache directories ===
 .gradle/
```

### `.clinerules/coding.md`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/.clinerules/coding.md	2026-04-22 08:03:55.461780269 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/.clinerules/coding.md	2026-04-22 08:03:40.249605729 +0000
@@ -41,7 +41,7 @@
 
 You SHOULD prefer modern Java idioms: records, pattern matching, sealed interfaces/classes, `var` for local variables.
 You MUST NOT use fully qualified class names unless there is a conflict between 2 class names in different packages.
-You MUST annotate the code with nullability annotations (`io.micronaut.core.annotation.Nullable`, `io.micronaut.core.annotation.NonNull`).
+You MUST annotate the code with nullability annotations (`org.jspecify.annotations.Nullable`, `org.jspecify.annotations.NonNull`).
 You MUST NOT use reflection: Micronaut is a reflection-free framework tailored for integration with GraalVM.
 You MUST use `jakarta.inject` for dependency injection, NOT `javax.inject`.
 
```

### `.github/instructions/coding.instructions.md`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/.github/instructions/coding.instructions.md	2026-04-22 08:03:55.462456191 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/.github/instructions/coding.instructions.md	2026-04-22 08:03:40.250262610 +0000
@@ -41,7 +41,7 @@
 
 You SHOULD prefer modern Java idioms: records, pattern matching, sealed interfaces/classes, `var` for local variables.
 You MUST NOT use fully qualified class names unless there is a conflict between 2 class names in different packages.
-You MUST annotate the code with nullability annotations (`io.micronaut.core.annotation.Nullable`, `io.micronaut.core.annotation.NonNull`).
+You MUST annotate the code with nullability annotations (`org.jspecify.annotations.Nullable`, `org.jspecify.annotations.NonNull`).
 You MUST NOT use reflection: Micronaut is a reflection-free framework tailored for integration with GraalVM.
 You MUST use `jakarta.inject` for dependency injection, NOT `javax.inject`.
 
```

### `.github/renovate.json`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/.github/renovate.json	2026-04-22 08:03:55.462639526 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/.github/renovate.json	2026-04-22 08:03:40.250464611 +0000
@@ -19,9 +19,18 @@
       ],
       "matchCurrentVersion": "!/^0/",
       "automerge": true,
-      "matchPackageNames": [
-        "/actions.*/"
-      ]
+      "matchManagers": ["github-actions"],
+      "groupName": "GitHub Actions dependencies"
+    },
+    {
+      "matchDatasources": [
+        "maven"
+      ],
+      "matchManagers": [
+        "maven",
+        "gradle"
+      ],
+      "allowedVersions": "!/.+-SNAPSHOT$/"
     },
     {
       "matchUpdateTypes": [
@@ -29,6 +38,12 @@
       ],
       "matchCurrentVersion": "!/^0/",
       "automerge": true
+    },
+    {
+      "matchPackageNames": [
+        "/.*micronaut.*/"
+      ],
+      "groupName": "Micronaut dependencies"
     }
   ]
 }
```

### `.github/workflows/central-sync.yml`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/.github/workflows/central-sync.yml	2026-04-22 08:03:55.462752610 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/.github/workflows/central-sync.yml	2026-04-22 08:03:40.250581279 +0000
@@ -14,18 +14,22 @@
   central-sync:
     runs-on: ubuntu-latest
     steps:
+      - name: Remove system JDKs
+        run: |
+          sudo rm -rf /usr/lib/jvm/*
+          unset JAVA_HOME
+          export PATH=$(echo "$PATH" | tr ':' '\n' | grep -v '/usr/lib/jvm' | paste -sd:)
       - name: Checkout repository
-        uses: actions/checkout@v5
+        uses: actions/checkout@de0fac2e4500dabe0009e67214ff5f5447ce83dd # v6
         with:
           ref: v${{ github.event.inputs.release_version }}
-      - uses: gradle/actions/wrapper-validation@v4
+      - uses: gradle/actions/wrapper-validation@50e97c2cd7a37755bbfafc9c5b7cafaece252f6e # v6
       - name: Set up JDK
-        uses: actions/setup-java@v5
+        uses: actions/setup-java@be666c2fcd27ec809703dec50e508c2fdc7f6654 # v5
         with:
           distribution: 'temurin'
           java-version: |
-            17
-            21
+            25
       - name: Publish to Sonatype OSSRH
         env:
           SONATYPE_USERNAME: ${{ secrets.SONATYPE_USERNAME }}
```

### `.github/workflows/graalvm-dev.yml`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/.github/workflows/graalvm-dev.yml	2026-04-22 08:03:55.462818610 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/.github/workflows/graalvm-dev.yml	2026-04-22 08:03:40.250657738 +0000
@@ -18,9 +18,9 @@
     outputs:
       matrix: ${{ steps.build-matrix.outputs.matrix }}
     steps:
-      - uses: actions/checkout@v5
+      - uses: actions/checkout@de0fac2e4500dabe0009e67214ff5f5447ce83dd # v6
       - name: Build Matrix
-        uses: micronaut-projects/github-actions/graalvm/build-matrix@master
+        uses: micronaut-projects/github-actions/graalvm/build-matrix@300bf6db7c062dcba77c90bb90e475df31b2acab # master
         id: build-matrix
   build:
     needs: build_matrix
@@ -42,15 +42,21 @@
       DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
       DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
     steps:
-      - uses: actions/checkout@v5
+      - name: Remove system JDKs
+        run: |
+          sudo rm -rf /usr/lib/jvm/*
+          unset JAVA_HOME
+          export PATH=$(echo "$PATH" | tr ':' '\n' | grep -v '/usr/lib/jvm' | paste -sd:)
+      - uses: actions/checkout@de0fac2e4500dabe0009e67214ff5f5447ce83dd # v6
       - name: Pre-Build Steps
-        uses: micronaut-projects/github-actions/graalvm/pre-build@master
+        uses: micronaut-projects/github-actions/graalvm/pre-build@300bf6db7c062dcba77c90bb90e475df31b2acab # master
         id: pre-build
         with:
           java: ${{ matrix.java }}
           distribution: ${{ matrix.distribution }}
+          nativeTestTask: ${{ matrix.native_test_task }}
       - name: Build Steps
-        uses: micronaut-projects/github-actions/graalvm/build@master
+        uses: micronaut-projects/github-actions/graalvm/build@300bf6db7c062dcba77c90bb90e475df31b2acab # master
         id: build
         env:
           GH_TOKEN_PUBLIC_REPOS_READONLY: ${{ secrets.GH_TOKEN_PUBLIC_REPOS_READONLY }}
@@ -59,7 +65,7 @@
         with:
           nativeTestTask: ${{ matrix.native_test_task }}
       - name: Post-Build Steps
-        uses: micronaut-projects/github-actions/graalvm/post-build@master
+        uses: micronaut-projects/github-actions/graalvm/post-build@300bf6db7c062dcba77c90bb90e475df31b2acab # master
         id: post-build
         with:
           java: ${{ matrix.java }}
```

### `.github/workflows/graalvm-latest.yml`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/.github/workflows/graalvm-latest.yml	2026-04-22 08:03:55.462878069 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/.github/workflows/graalvm-latest.yml	2026-04-22 08:03:40.250722030 +0000
@@ -8,26 +8,28 @@
   push:
     branches:
       - master
-      - '[1-9]+.[0-9]+.x'
+      - '[0-9]+.[0-9]+.x'
   pull_request:
     branches:
       - master
-      - '[1-9]+.[0-9]+.x'
+      - '[0-9]+.[0-9]+.x'
 jobs:
   build_matrix:
     if: github.repository != 'micronaut-projects/micronaut-project-template'
     runs-on: ubuntu-latest
-    env:
-      DEVELOCITY_ACCESS_KEY: ${{ secrets.GRADLE_ENTERPRISE_ACCESS_KEY }}
-      DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
-      DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
     outputs:
       matrix: ${{ steps.build-matrix.outputs.matrix }}
     steps:
-      - uses: actions/checkout@v5
+      - uses: actions/checkout@de0fac2e4500dabe0009e67214ff5f5447ce83dd # v6
       - name: Build Matrix
-        uses: micronaut-projects/github-actions/graalvm/build-matrix@master
+        uses: micronaut-projects/github-actions/graalvm/build-matrix@300bf6db7c062dcba77c90bb90e475df31b2acab # master
         id: build-matrix
+        env:
+          DEVELOCITY_ACCESS_KEY: ${{ secrets.GRADLE_ENTERPRISE_ACCESS_KEY }}
+          DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
+          DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
+        with:
+          java-version: '25'
   build:
     needs: build_matrix
     if: github.repository != 'micronaut-projects/micronaut-project-template'
@@ -35,31 +37,45 @@
     strategy:
       max-parallel: 6
       matrix:
-        java: ['17', '21']
+        java: ['25']
         native_test_task: ${{ fromJson(needs.build_matrix.outputs.matrix).native_test_task }}
-    env:
-      DEVELOCITY_ACCESS_KEY: ${{ secrets.GRADLE_ENTERPRISE_ACCESS_KEY }}
-      DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
-      DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
     steps:
-      - uses: actions/checkout@v5
+      - name: Remove system JDKs
+        run: |
+          sudo rm -rf /usr/lib/jvm/*
+          unset JAVA_HOME
+          export PATH=$(echo "$PATH" | tr ':' '\n' | grep -v '/usr/lib/jvm' | paste -sd:)
+      - uses: actions/checkout@de0fac2e4500dabe0009e67214ff5f5447ce83dd # v6
       - name: Pre-Build Steps
-        uses: micronaut-projects/github-actions/graalvm/pre-build@master
+        uses: micronaut-projects/github-actions/graalvm/pre-build@300bf6db7c062dcba77c90bb90e475df31b2acab # master
         id: pre-build
+        env:
+          DEVELOCITY_ACCESS_KEY: ${{ secrets.GRADLE_ENTERPRISE_ACCESS_KEY }}
+          DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
+          DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
         with:
           distribution: 'graalvm'
+          gradle-java: '25'
           java: ${{ matrix.java }}
+          nativeTestTask: ${{ matrix.native_test_task }}
       - name: Build Steps
-        uses: micronaut-projects/github-actions/graalvm/build@master
+        uses: micronaut-projects/github-actions/graalvm/build@300bf6db7c062dcba77c90bb90e475df31b2acab # master
         id: build
         env:
+          DEVELOCITY_ACCESS_KEY: ${{ secrets.GRADLE_ENTERPRISE_ACCESS_KEY }}
+          DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
+          DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
           GH_TOKEN_PUBLIC_REPOS_READONLY: ${{ secrets.GH_TOKEN_PUBLIC_REPOS_READONLY }}
           GH_USERNAME: ${{ secrets.GH_USERNAME }}
           GRAALVM_QUICK_BUILD: true
         with:
           nativeTestTask: ${{ matrix.native_test_task }}
       - name: Post-Build Steps
-        uses: micronaut-projects/github-actions/graalvm/post-build@master
+        uses: micronaut-projects/github-actions/graalvm/post-build@300bf6db7c062dcba77c90bb90e475df31b2acab # master
         id: post-build
+        env:
+          DEVELOCITY_ACCESS_KEY: ${{ secrets.GRADLE_ENTERPRISE_ACCESS_KEY }}
+          DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
+          DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
         with:
           java: ${{ matrix.java }}
```

### `.github/workflows/gradle.yml`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/.github/workflows/gradle.yml	2026-04-22 08:03:55.462956320 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/.github/workflows/gradle.yml	2026-04-22 08:03:40.250815739 +0000
@@ -8,98 +8,107 @@
   push:
     branches:
       - master
-      - '[1-9]+.[0-9]+.x'
+      - '[0-9]+.[0-9]+.x'
   pull_request:
     branches:
       - master
-      - '[1-9]+.[0-9]+.x'
+      - '[0-9]+.[0-9]+.x'
 jobs:
   build:
     if: github.repository != 'micronaut-projects/micronaut-project-template'
     runs-on: ubuntu-latest
     strategy:
       matrix:
-        java: ['17', '21']
+        java: ['25']
     env:
-      DEVELOCITY_ACCESS_KEY: ${{ secrets.GRADLE_ENTERPRISE_ACCESS_KEY }}
-      DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
-      DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
-      GH_TOKEN_PUBLIC_REPOS_READONLY: ${{ secrets.GH_TOKEN_PUBLIC_REPOS_READONLY }}
-      GH_USERNAME: ${{ secrets.GH_USERNAME }}
       TESTCONTAINERS_RYUK_DISABLED: true
-      PREDICTIVE_TEST_SELECTION: "${{ github.event_name == 'pull_request' && 'true' || 'false' }}"
-      SONAR_TOKEN: ${{ secrets.SONAR_TOKEN }}
-      GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
-      OSS_INDEX_USERNAME: ${{ secrets.OSS_INDEX_USERNAME }}
-      OSS_INDEX_PASSWORD: ${{ secrets.OSS_INDEX_PASSWORD }}
+      SONAR_TOKEN_AVAILABLE: ${{ secrets.SONAR_TOKEN != '' }}
     steps:
        # https://github.com/actions/virtual-environments/issues/709
+      - name: Remove system JDKs
+        run: |
+          sudo rm -rf /usr/lib/jvm/*
+          unset JAVA_HOME
+          export PATH=$(echo "$PATH" | tr ':' '\n' | grep -v '/usr/lib/jvm' | paste -sd:)
       - name: "🗑 Free disk space"
         run: |
          sudo rm -rf "/usr/local/share/boost"
          sudo rm -rf "$AGENT_TOOLSDIRECTORY"
+         sudo rm -rf "/opt/ghc"
+         sudo rm -rf "/usr/share/dotnet"
+         sudo rm -rf "/usr/local/lib/android"
          sudo apt-get clean
          df -h
 
       - name: "📥 Checkout repository"
-        uses: actions/checkout@v5
+        uses: actions/checkout@de0fac2e4500dabe0009e67214ff5f5447ce83dd # v6
         with:
           fetch-depth: 0
 
       - name: "🔧 Setup GraalVM CE"
-        uses: graalvm/setup-graalvm@v1.4.1
+        uses: graalvm/setup-graalvm@60c26726de13f8b90771df4bc1641a52a3159994 # v1
         with:
           distribution: 'graalvm'
           java-version: ${{ matrix.java }}
           github-token: ${{ secrets.GITHUB_TOKEN }}
 
       - name: "🔧 Setup Gradle"
-        uses: gradle/actions/setup-gradle@v4
+        uses: gradle/actions/setup-gradle@50e97c2cd7a37755bbfafc9c5b7cafaece252f6e # v6
 
       - name: "❓ Optional setup step"
         run: |
           [ -f ./setup.sh ] && ./setup.sh || [ ! -f ./setup.sh ]
 
-      - name: "🚔 Sonatype Scan"
-        if: env.OSS_INDEX_PASSWORD != '' && matrix.java == '17'
-        id: sonatypescan
-        run: |
-          ./gradlew ossIndexAudit --no-parallel --info
-
       - name: "🛠 Build with Gradle"
         id: gradle
+        env:
+          DEVELOCITY_ACCESS_KEY: ${{ secrets.GRADLE_ENTERPRISE_ACCESS_KEY }}
+          DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
+          DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
+          GH_TOKEN_PUBLIC_REPOS_READONLY: ${{ secrets.GH_TOKEN_PUBLIC_REPOS_READONLY }}
+          GH_USERNAME: ${{ secrets.GH_USERNAME }}
+          OSS_INDEX_USERNAME: ${{ secrets.OSS_INDEX_USERNAME }}
+          OSS_INDEX_PASSWORD: ${{ secrets.OSS_INDEX_PASSWORD }}
         run: |
-          ./gradlew jacocoReport check --no-daemon --continue
+          ./gradlew check jacocoReport --no-daemon --continue
 
       - name: "🔎 Run static analysis"
-        if: env.SONAR_TOKEN != '' && matrix.java == '17'
+        if: env.SONAR_TOKEN_AVAILABLE == 'true' && matrix.java == '25'
+        env:
+          DEVELOCITY_ACCESS_KEY: ${{ secrets.GRADLE_ENTERPRISE_ACCESS_KEY }}
+          DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
+          DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
+          SONAR_TOKEN: ${{ secrets.SONAR_TOKEN }}
         run: |
           ./gradlew sonar --no-parallel --continue
 
       - name: "📊 Publish Test Report"
         if: always()
-        uses: mikepenz/action-junit-report@v5
+        uses: mikepenz/action-junit-report@bccf2e31636835cf0874589931c4116687171386 # v6
         with:
           check_name: Java CI / Test Report (${{ matrix.java }})
           report_paths: '**/build/test-results/test/TEST-*.xml'
           check_retries: 'true'
 
       - name: "📜 Upload binary compatibility check results"
-        if: matrix.java == '17'
-        uses: actions/upload-artifact@65c4c4a1ddee5b72f698fdd19549f0f0fb45cf08 # v4.6.0
+        if: matrix.java == '25'
+        uses: actions/upload-artifact@043fb46d1a93c77aae656e7c1c64a875d1fc6a0a # v7
         with:
           name: binary-compatibility-reports
           path: "**/build/reports/binary-compatibility-*.html"
 
       - name: "📦 Publish to Sonatype Snapshots"
-        if: success() && github.event_name == 'push' && matrix.java == '17'
+        if: success() && github.event_name == 'push' && matrix.java == '25'
         env:
+          DEVELOCITY_ACCESS_KEY: ${{ secrets.GRADLE_ENTERPRISE_ACCESS_KEY }}
+          DEVELOCITY_CACHE_USERNAME: ${{ secrets.GRADLE_ENTERPRISE_CACHE_USERNAME }}
+          DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
           SONATYPE_USERNAME: ${{ secrets.SONATYPE_USERNAME }}
           SONATYPE_PASSWORD: ${{ secrets.SONATYPE_PASSWORD }}
         run: ./gradlew publishToSonatype docs --no-daemon
 
       - name: "❓ Determine docs target repository"
-        uses: haya14busa/action-cond@v1
+        uses: haya14busa/action-cond@94f77f7a80cd666cb3155084e428254fea4281fd # v1
         id: docs_target
         with:
           cond: ${{ github.repository == 'micronaut-projects/micronaut-core' }}
@@ -107,10 +116,14 @@
           if_false: ${{ github.repository }}
 
       - name: "📑 Publish to Github Pages"
-        if: success() && github.event_name == 'push' && matrix.java == '17'
-        uses: micronaut-projects/github-pages-deploy-action@master
+        if: success() && github.event_name == 'push' && matrix.java == '25'
+        uses: micronaut-projects/github-pages-deploy-action@76d63aafbab7108d74e83be4e5b3b0501382e829 # master
         env:
           TARGET_REPOSITORY: ${{ steps.docs_target.outputs.value }}
           GH_TOKEN: ${{ secrets.GH_TOKEN }}
           BRANCH: gh-pages
           FOLDER: build/docs
+
+      - name: "❓ Optional cleanup step"
+        run: |
+          [ -f ./cleanup.sh ] && ./cleanup.sh || [ ! -f ./cleanup.sh ]
```

### `.github/workflows/publish-snapshot.yml`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/.github/workflows/publish-snapshot.yml	2026-04-22 08:03:55.463022279 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/.github/workflows/publish-snapshot.yml	2026-04-22 08:03:40.250880990 +0000
@@ -10,20 +10,24 @@
     if: github.repository != 'micronaut-projects/micronaut-project-template'
     runs-on: ubuntu-latest
     steps:
-      - uses: actions/checkout@v5
-      - uses: actions/cache@v4
+      - name: Remove system JDKs
+        run: |
+          sudo rm -rf /usr/lib/jvm/*
+          unset JAVA_HOME
+          export PATH=$(echo "$PATH" | tr ':' '\n' | grep -v '/usr/lib/jvm' | paste -sd:)
+      - uses: actions/checkout@de0fac2e4500dabe0009e67214ff5f5447ce83dd # v6
+      - uses: actions/cache@27d5ce7f107fe9357f9df03efb73ab90386fccae # v5
         with:
           path: ~/.gradle/caches
           key: ${{ runner.os }}-gradle-${{ hashFiles('**/*.gradle') }}
           restore-keys: |
             ${{ runner.os }}-gradle-
       - name: Set up JDK
-        uses: actions/setup-java@v5
+        uses: actions/setup-java@be666c2fcd27ec809703dec50e508c2fdc7f6654 # v5
         with:
           distribution: 'temurin'
           java-version: |
-            17
-            21
+            25
       - name: Publish to Sonatype Snapshots
         if: success()
         env:
```

### `.github/workflows/release.yml`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/.github/workflows/release.yml	2026-04-22 08:03:55.463120863 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/.github/workflows/release.yml	2026-04-22 08:03:40.250963365 +0000
@@ -13,23 +13,27 @@
       artifacts-sha256: ${{ steps.hash.outputs.artifacts-sha256 }} # Computed hashes for build artifacts.
     runs-on: ubuntu-latest
     steps:
+      - name: Remove system JDKs
+        run: |
+          sudo rm -rf /usr/lib/jvm/*
+          unset JAVA_HOME
+          export PATH=$(echo "$PATH" | tr ':' '\n' | grep -v '/usr/lib/jvm' | paste -sd:)
       - name: Checkout repository
-        uses: actions/checkout@v5
+        uses: actions/checkout@de0fac2e4500dabe0009e67214ff5f5447ce83dd # v6
         with:
           token: ${{ secrets.GH_TOKEN }}
-      - uses: gradle/actions/wrapper-validation@v4
+      - uses: gradle/actions/wrapper-validation@50e97c2cd7a37755bbfafc9c5b7cafaece252f6e # v6
       - name: Set up JDK
-        uses: actions/setup-java@v5
+        uses: actions/setup-java@be666c2fcd27ec809703dec50e508c2fdc7f6654 # v5
         with:
           distribution: 'temurin'
           java-version: |
-            17
-            21
+            25
       - name: Set the current release version
         id: release_version
         run: echo "release_version=${GITHUB_REF:11}" >> $GITHUB_OUTPUT
       - name: Run pre-release
-        uses: micronaut-projects/github-actions/pre-release@master
+        uses: micronaut-projects/github-actions/pre-release@300bf6db7c062dcba77c90bb90e475df31b2acab # master
         env:
           MICRONAUT_BUILD_EMAIL: ${{ secrets.MICRONAUT_BUILD_EMAIL }}
         with:
@@ -68,13 +72,13 @@
           # Store the hash in a file, which is uploaded as a workflow artifact.
           sha256sum $ARTIFACTS | base64 -w0 > artifacts-sha256
       - name: Upload build artifacts
-        uses: actions/upload-artifact@65c4c4a1ddee5b72f698fdd19549f0f0fb45cf08 # v4.6.0
+        uses: actions/upload-artifact@043fb46d1a93c77aae656e7c1c64a875d1fc6a0a # v7.0.1
         with:
           name: gradle-build-outputs
           path: build/repo/${{ steps.publish.outputs.group }}/*/${{ steps.publish.outputs.version }}/*
           retention-days: 5
       - name: Upload artifacts-sha256
-        uses: actions/upload-artifact@65c4c4a1ddee5b72f698fdd19549f0f0fb45cf08 # v4.6.0
+        uses: actions/upload-artifact@043fb46d1a93c77aae656e7c1c64a875d1fc6a0a # v7.0.1
         with:
           name: artifacts-sha256
           path: artifacts-sha256
@@ -88,12 +92,15 @@
           GH_TOKEN_PUBLIC_REPOS_READONLY: ${{ secrets.GH_TOKEN_PUBLIC_REPOS_READONLY }}
           GH_USERNAME: ${{ secrets.GH_USERNAME }}
       - name: Export Gradle Properties
-        uses: micronaut-projects/github-actions/export-gradle-properties@master
+        uses: micronaut-projects/github-actions/export-gradle-properties@300bf6db7c062dcba77c90bb90e475df31b2acab # master
+      - name: LATEST_TAG
+        run: |
+          echo "LATEST_TAG=$(curl -s -L -H 'Accept: application/vnd.github+json' -H 'X-GitHub-Api-Version: 2022-11-28' https://api.github.com/repos/${{ github.repository }}/releases/latest | jq -r '.tag_name')" >> $GITHUB_ENV
       - name: Publish to Github Pages
         if: success()
-        uses: micronaut-projects/github-pages-deploy-action@master
+        uses: micronaut-projects/github-pages-deploy-action@76d63aafbab7108d74e83be4e5b3b0501382e829 # master
         env:
-          BETA: ${{ !(github.event.release.target_commitish == github.event.repository.default_branch) || contains(steps.release_version.outputs.release_version, 'M') || contains(steps.release_version.outputs.release_version, 'RC') }}
+          BETA: ${{ !(github.event.release.tag_name == env.LATEST_TAG) || github.event.release.draft || github.event.release.prerelease || contains(steps.release_version.outputs.release_version, 'M') || contains(steps.release_version.outputs.release_version, 'RC') }}
           GH_TOKEN: ${{ secrets.GH_TOKEN }}
           BRANCH: gh-pages
           FOLDER: build/docs
@@ -104,7 +111,7 @@
           DEVELOCITY_CACHE_PASSWORD: ${{ secrets.GRADLE_ENTERPRISE_CACHE_PASSWORD }}
       - name: Run post-release
         if: success()
-        uses: micronaut-projects/github-actions/post-release@master
+        uses: micronaut-projects/github-actions/post-release@300bf6db7c062dcba77c90bb90e475df31b2acab # master
         env:
           MICRONAUT_BUILD_EMAIL: ${{ secrets.MICRONAUT_BUILD_EMAIL }}
         with:
@@ -117,7 +124,7 @@
       artifacts-sha256: ${{ steps.set-hash.outputs.artifacts-sha256 }}
     steps:
       - name: Download artifacts-sha256
-        uses: actions/download-artifact@634f93cb2916e3fdff6788551b99b062d0335ce0 # v5.0.0
+        uses: actions/download-artifact@3e5f45b2cfb9172054b4087a40e8e0b5a5461e7c # v8.0.1
         with:
           name: artifacts-sha256
       # The SLSA provenance generator expects the hash digest of artifacts to be passed as a job
@@ -136,7 +143,7 @@
       actions: read # To read the workflow path.
       id-token: write # To sign the provenance.
       contents: write # To add assets to a release.
-    uses: slsa-framework/slsa-github-generator/.github/workflows/generator_generic_slsa3.yml@v2.1.0
+    uses: slsa-framework/slsa-github-generator/.github/workflows/generator_generic_slsa3.yml@f7dd8c54c2067bafc12ca7a55595d5ee9b75204a # v2.1.0
     with:
       base64-subjects: "${{ needs.provenance-subject.outputs.artifacts-sha256 }}"
       upload-assets: true # Upload to a new release.
@@ -148,9 +155,11 @@
     if: startsWith(github.ref, 'refs/tags/')
     steps:
       - name: Checkout repository
-        uses: actions/checkout@08c6903cd8c0fde910a37f88322edcfb5dd907a8 # v5.0.0
+        uses: actions/checkout@de0fac2e4500dabe0009e67214ff5f5447ce83dd # v6.0.2
+        with:
+          ref: ${{ github.sha }}
       - name: Download artifacts
-        uses: actions/download-artifact@634f93cb2916e3fdff6788551b99b062d0335ce0 # v5.0.0
+        uses: actions/download-artifact@3e5f45b2cfb9172054b4087a40e8e0b5a5461e7c # v8.0.1
         with:
           name: gradle-build-outputs
           path: build/repo
@@ -162,6 +171,6 @@
       - name: Upload assets
         # Upload the artifacts to the existing release. Note that the SLSA provenance will
         # attest to each artifact file and not the aggregated ZIP file.
-        uses: softprops/action-gh-release@6da8fa9354ddfdc4aeace5fc48d7f679b5214090 # v2.4.1
+        uses: softprops/action-gh-release@b4309332981a82ec1c5618f44dd2e27cc8bfbfda # v3.0.0
         with:
           files: artifacts.zip
```

### `.gitignore`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/.gitignore	2026-04-22 08:03:55.463177822 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/.gitignore	2026-04-22 08:03:40.251083741 +0000
@@ -34,3 +34,9 @@
 
 # Ignore files generated by test-resources
 **/.micronaut/test-resources/
+
+# Ignore gradle.properties generated by micronaut-build
+/buildSrc/gradle.properties
+
+# OpenCode files
+.sisyphus/
```

### `MAINTAINING.md`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/MAINTAINING.md	2026-04-22 08:03:55.463486782 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/MAINTAINING.md	2026-04-22 08:03:40.251511828 +0000
@@ -2,7 +2,7 @@
 
 ## Triage incoming issues
 
-New issues need to be categorised. At least with one of the following labels:
+New issues need to be categorized. At least with one of the following labels:
 
 * `type: bug`: when something is not working as designed.
 * `type: improvement`: a minor improvement over an existing feature.
@@ -38,7 +38,7 @@
   revisited in the future.
 * `status: next major version`: it is a breaking change and therefore needs to be implemented in the next major version.
 
-There are also a bunch of `relates-to` labels that can be used to further categorise issues. This is helpful in projects
+There are also a bunch of `relates-to` labels that can be used to further categorize issues. This is helpful in projects
 with a lot of issues, or projects where different people work on different parts or modules.
 
 The majority of the issues are defined in the
@@ -48,7 +48,7 @@
 * If they can be beneficial to several repos, send a pull request to the management repo.
 * If they are repo-specific, just go ahead and create them with the GitHub UI.
 
-Finally, issues (especially bugs) should be prioritised with either `priority: high`, `priority: medium` or
+Finally, issues (especially bugs) should be prioritized with either `priority: high`, `priority: medium` or
 `priority: low`. Checkout the
 [Issue Priority Labels](https://github.com/micronaut-projects/micronaut-core/wiki/Issue-Priority-Labels) document for
 guidelines about when to use each of them.
@@ -146,8 +146,8 @@
 The "Java CI" (`gradle.yml`) workflow does have the ability to have an optional setup step, though. If there is a `setup.sh`
 file in the project root, it will be executed before invoking Gradle.
 
-There are projects, such as micronaut-gcp and micronaut-kubernetes, that have made customisations to sync'ed workflows
-because it's absolutely necessary. In those projects, the sync pull requests are manually merged so that the customisations
+There are projects, such as micronaut-gcp and micronaut-kubernetes, that have made customizations to sync'ed workflows
+because it's absolutely necessary. In those projects, the sync pull requests are manually merged so that the customizations
 aren't lost.
 
 Note that it is perfectly possible to have new workflows that aren't part of the sync process.
```

### `buildSrc/src/main/groovy/io.micronaut.build.internal.micrometer-module.gradle`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/buildSrc/src/main/groovy/io.micronaut.build.internal.micrometer-module.gradle	2026-04-22 08:03:55.464187372 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/buildSrc/src/main/groovy/io.micronaut.build.internal.micrometer-module.gradle	2026-04-22 08:03:40.252233459 +0000
@@ -6,16 +6,6 @@
     id 'io.micronaut.build.internal.module'
 }
 
-ossIndexAudit {
-        excludeVulnerabilityIds = [
-                'CVE-2024-23082', // disputed / false position. See https://www.threeten.org/threetenbp/security.html
-                'CVE-2024-23081' // disputed / false position. See https://www.threeten.org/threetenbp/security.html
-        ]
-        excludeCoordinates = [
-                "org.threeten:threetenbp:1.7.2", // no version patched https://ossindex.sonatype.org/component/pkg:maven/org.threeten/threetenbp
-        ]
-}
-
 dependencies {
     api libs.managed.micrometer.core
 }
```

### `config/accepted-api-changes.json`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/config/accepted-api-changes.json	2026-04-22 08:03:55.464497082 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/config/accepted-api-changes.json	2026-04-22 08:03:40.252547670 +0000
@@ -258,5 +258,20 @@
     "type": "io.micronaut.configuration.metrics.micrometer.cloudwatch.$CloudWatchMeterRegistryFactory$CloudWatchMeterRegistry2$Definition$Reference",
     "member": "Implemented interface io.micronaut.inject.BeanDefinitionReference",
     "reason": "use AWS cloud watch client instead of default one"
+  },
+  {
+    "type": "io.micronaut.configuration.metrics.micrometer.cloudwatch.CloudWatchMeterRegistryFactory",
+    "member": "Constructor io.micronaut.configuration.metrics.micrometer.cloudwatch.CloudWatchMeterRegistryFactory()",
+    "reason": "Removed deprecated code for Micronaut Framework 5"
+  },
+  {
+    "type": "io.micronaut.configuration.metrics.micrometer.intercept.CountedInterceptor",
+    "member": "Constructor io.micronaut.configuration.metrics.micrometer.intercept.CountedInterceptor(io.micrometer.core.instrument.MeterRegistry)",
+    "reason": "Removed deprecated code for Micronaut Framework 5"
+  },
+  {
+    "type": "io.micronaut.configuration.metrics.micrometer.intercept.TimedInterceptor",
+    "member": "Constructor io.micronaut.configuration.metrics.micrometer.intercept.TimedInterceptor(io.micrometer.core.instrument.MeterRegistry)",
+    "reason": "Removed deprecated code for Micronaut Framework 5"
   }
 ]
```

### `gradle/wrapper/gradle-wrapper.jar`

_Binary file differs._

### `gradlew`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/gradlew	2026-04-22 08:03:55.465513924 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/gradlew	2026-04-22 08:03:40.253554303 +0000
@@ -1,7 +1,7 @@
 #!/bin/sh
 
 #
-# Copyright © 2015-2021 the original authors.
+# Copyright © 2015 the original authors.
 #
 # Licensed under the Apache License, Version 2.0 (the "License");
 # you may not use this file except in compliance with the License.
@@ -57,7 +57,7 @@
 #       Darwin, MinGW, and NonStop.
 #
 #   (3) This script is generated from the Groovy template
-#       https://github.com/gradle/gradle/blob/HEAD/platforms/jvm/plugins-application/src/main/resources/org/gradle/api/internal/plugins/unixStartScript.txt
+#       https://github.com/gradle/gradle/blob/2d6327017519d23b96af35865dc997fcb544fb40/platforms/jvm/plugins-application/src/main/resources/org/gradle/api/internal/plugins/unixStartScript.txt
 #       within the Gradle project.
 #
 #       You can find Gradle at https://github.com/gradle/gradle/.
@@ -114,7 +114,6 @@
   NONSTOP* )        nonstop=true ;;
 esac
 
-CLASSPATH="\\\"\\\""
 
 
 # Determine the Java command to use to start the JVM.
@@ -172,7 +171,6 @@
 # For Cygwin or MSYS, switch paths to Windows format before running java
 if "$cygwin" || "$msys" ; then
     APP_HOME=$( cygpath --path --mixed "$APP_HOME" )
-    CLASSPATH=$( cygpath --path --mixed "$CLASSPATH" )
 
     JAVACMD=$( cygpath --unix "$JAVACMD" )
 
@@ -212,7 +210,6 @@
 
 set -- \
         "-Dorg.gradle.appname=$APP_BASE_NAME" \
-        -classpath "$CLASSPATH" \
         -jar "$APP_HOME/gradle/wrapper/gradle-wrapper.jar" \
         "$@"
 
```

### `gradlew.bat`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/gradlew.bat	2026-04-22 08:03:55.465600883 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/gradlew.bat	2026-04-22 08:03:40.253638012 +0000
@@ -70,11 +70,10 @@
 :execute
 @rem Setup the command line
 
-set CLASSPATH=
 
 
 @rem Execute Gradle
-"%JAVA_EXE%" %DEFAULT_JVM_OPTS% %JAVA_OPTS% %GRADLE_OPTS% "-Dorg.gradle.appname=%APP_BASE_NAME%" -classpath "%CLASSPATH%" -jar "%APP_HOME%\gradle\wrapper\gradle-wrapper.jar" %*
+"%JAVA_EXE%" %DEFAULT_JVM_OPTS% %JAVA_OPTS% %GRADLE_OPTS% "-Dorg.gradle.appname=%APP_BASE_NAME%" -jar "%APP_HOME%\gradle\wrapper\gradle-wrapper.jar" %*
 
 :end
 @rem End local scope for the variables with windows NT shell
```

### `micrometer-core/build.gradle.kts`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/micrometer-core/build.gradle.kts	2026-04-22 08:03:55.467219062 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/micrometer-core/build.gradle.kts	2026-04-22 08:03:40.255355317 +0000
@@ -37,7 +37,7 @@
     testImplementation(mnSql.micronaut.jdbc)
     testImplementation(mn.micronaut.management)
     testImplementation(mn.micronaut.http.validation)
-    testImplementation(mnRxjava2.micronaut.rxjava2)
+    testImplementation(mnRxjava3.micronaut.rxjava3)
     testImplementation(mnSerde.micronaut.serde.jackson)
     testImplementation(mn.netty.buffer)
     testImplementation(mn.netty.transport.native.epoll)
```

### `micrometer-core/src/main/java/io/micronaut/configuration/metrics/aggregator/AbstractMethodTagger.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/micrometer-core/src/main/java/io/micronaut/configuration/metrics/aggregator/AbstractMethodTagger.java	2026-04-22 08:03:55.467623607 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/micrometer-core/src/main/java/io/micronaut/configuration/metrics/aggregator/AbstractMethodTagger.java	2026-04-22 08:03:40.255801612 +0000
@@ -18,7 +18,7 @@
 import io.micrometer.core.instrument.Tag;
 import io.micronaut.aop.MethodInvocationContext;
 import io.micronaut.core.annotation.Indexed;
-import io.micronaut.core.annotation.NonNull;
+import org.jspecify.annotations.NonNull;
 import io.micronaut.core.order.Ordered;
 import org.slf4j.Logger;
 import org.slf4j.LoggerFactory;
```

### `micrometer-core/src/main/java/io/micronaut/configuration/metrics/aggregator/CompositeMeterRegistryConfigurer.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/micrometer-core/src/main/java/io/micronaut/configuration/metrics/aggregator/CompositeMeterRegistryConfigurer.java	2026-04-22 08:03:55.467735775 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/micrometer-core/src/main/java/io/micronaut/configuration/metrics/aggregator/CompositeMeterRegistryConfigurer.java	2026-04-22 08:03:40.255889738 +0000
@@ -19,7 +19,7 @@
 import io.micrometer.core.instrument.binder.MeterBinder;
 import io.micrometer.core.instrument.composite.CompositeMeterRegistry;
 import io.micrometer.core.instrument.config.MeterFilter;
-import io.micronaut.core.annotation.NonNull;
+import org.jspecify.annotations.NonNull;
 
 import java.util.Collection;
 
```

### `micrometer-core/src/main/java/io/micronaut/configuration/metrics/binder/datasource/DataSourcePoolMetricsBinder.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/micrometer-core/src/main/java/io/micronaut/configuration/metrics/binder/datasource/DataSourcePoolMetricsBinder.java	2026-04-22 08:03:55.468605240 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/micrometer-core/src/main/java/io/micronaut/configuration/metrics/binder/datasource/DataSourcePoolMetricsBinder.java	2026-04-22 08:03:40.256862371 +0000
@@ -19,7 +19,7 @@
 import io.micrometer.core.instrument.Tag;
 import io.micrometer.core.instrument.Tags;
 import io.micrometer.core.instrument.binder.MeterBinder;
-import io.micronaut.core.annotation.NonNull;
+import org.jspecify.annotations.NonNull;
 import io.micronaut.jdbc.metadata.DataSourcePoolMetadata;
 
 import javax.sql.DataSource;
```

### `micrometer-core/src/main/java/io/micronaut/configuration/metrics/binder/executor/ExecutorServiceMetricsBinder.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/micrometer-core/src/main/java/io/micronaut/configuration/metrics/binder/executor/ExecutorServiceMetricsBinder.java	2026-04-22 08:03:55.468859325 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/micrometer-core/src/main/java/io/micronaut/configuration/metrics/binder/executor/ExecutorServiceMetricsBinder.java	2026-04-22 08:03:40.257149498 +0000
@@ -70,12 +70,11 @@
             unwrapped = ((InstrumentedExecutorService) unwrapped).getTarget();
         }
         // Netty EventLoopGroups require separate instrumentation.
-        if (isEventLoop(unwrapped)) {
+        if (unwrapped.getClass().getName().startsWith("io.netty")) {
             return unwrapped;
         }
         // ExecutorServiceMetrics does not provide metrics for virtual threads
-        if (unwrapped.getClass().getName().equals(THREAD_PER_TASK_EXECUTOR) ||
-            unwrapped.getClass().getName().equals("io.micronaut.scheduling.executor.FastThreadPerTaskExecutor")) {
+        if (unwrapped.getClass().getName().equals(THREAD_PER_TASK_EXECUTOR)) {
             return executorService;
         }
 
@@ -126,15 +125,4 @@
             };
         }
     }
-
-    private static boolean isEventLoop(Object o) {
-        Class<?> c = o.getClass();
-        while (c != null) {
-            if (c.getName().startsWith("io.netty.")) {
-                return true;
-            }
-            c = c.getSuperclass();
-        }
-        return false;
-    }
 }
```

### `micrometer-core/src/main/java/io/micronaut/configuration/metrics/binder/netty/NettyMetrics.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/micrometer-core/src/main/java/io/micronaut/configuration/metrics/binder/netty/NettyMetrics.java	2026-04-22 08:03:55.469858167 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/micrometer-core/src/main/java/io/micronaut/configuration/metrics/binder/netty/NettyMetrics.java	2026-04-22 08:03:40.258752553 +0000
@@ -73,6 +73,8 @@
     static final String TIME = "time";
 
     static final String GROUP = "group";
+    static final String PARENT = "parent";
+    static final String WORKER = "worker";
 
     static final String READ = "read";
     static final String WRITTEN = "written";
```

### `micrometer-core/src/main/java/io/micronaut/configuration/metrics/binder/r2dbc/R2dbcPoolMetricsBinder.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/micrometer-core/src/main/java/io/micronaut/configuration/metrics/binder/r2dbc/R2dbcPoolMetricsBinder.java	2026-04-22 08:03:55.470123044 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/micrometer-core/src/main/java/io/micronaut/configuration/metrics/binder/r2dbc/R2dbcPoolMetricsBinder.java	2026-04-22 08:03:40.259011138 +0000
@@ -19,7 +19,7 @@
 import io.micrometer.core.instrument.Tag;
 import io.micrometer.core.instrument.Tags;
 import io.micrometer.core.instrument.binder.MeterBinder;
-import io.micronaut.core.annotation.NonNull;
+import org.jspecify.annotations.NonNull;
 import io.r2dbc.pool.PoolMetrics;
 
 import java.util.function.Function;
```

### `micrometer-core/src/main/java/io/micronaut/configuration/metrics/binder/web/WebMetricsHelper.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/micrometer-core/src/main/java/io/micronaut/configuration/metrics/binder/web/WebMetricsHelper.java	2026-04-22 08:03:55.471202136 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/micrometer-core/src/main/java/io/micronaut/configuration/metrics/binder/web/WebMetricsHelper.java	2026-04-22 08:03:40.260026896 +0000
@@ -18,8 +18,8 @@
 import io.micrometer.core.instrument.MeterRegistry;
 import io.micrometer.core.instrument.Tag;
 import io.micronaut.core.annotation.Internal;
-import io.micronaut.core.annotation.NonNull;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.NonNull;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.http.HttpAttributes;
 import io.micronaut.http.HttpResponse;
 import io.micronaut.http.HttpResponseProvider;
```

### `micrometer-core/src/main/java/io/micronaut/configuration/metrics/management/endpoint/MetricsEndpoint.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/micrometer-core/src/main/java/io/micronaut/configuration/metrics/management/endpoint/MetricsEndpoint.java	2026-04-22 08:03:55.472155102 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/micrometer-core/src/main/java/io/micronaut/configuration/metrics/management/endpoint/MetricsEndpoint.java	2026-04-22 08:03:40.260897903 +0000
@@ -22,7 +22,7 @@
 import io.micrometer.core.instrument.Tag;
 import io.micronaut.configuration.metrics.annotation.RequiresMetrics;
 import io.micronaut.core.annotation.Introspected;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.core.annotation.TypeHint;
 import io.micronaut.core.bind.exceptions.UnsatisfiedArgumentException;
 import io.micronaut.core.type.Argument;
```

### `micrometer-core/src/main/java/io/micronaut/configuration/metrics/micrometer/MeterRegistryFactory.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/micrometer-core/src/main/java/io/micronaut/configuration/metrics/micrometer/MeterRegistryFactory.java	2026-04-22 08:03:55.472480729 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/micrometer-core/src/main/java/io/micronaut/configuration/metrics/micrometer/MeterRegistryFactory.java	2026-04-22 08:03:40.261179530 +0000
@@ -16,7 +16,6 @@
 package io.micronaut.configuration.metrics.micrometer;
 
 import io.micrometer.core.instrument.MeterRegistry;
-import io.micrometer.core.instrument.Metrics;
 import io.micrometer.core.instrument.binder.MeterBinder;
 import io.micrometer.core.instrument.composite.CompositeMeterRegistry;
 import io.micrometer.core.instrument.config.MeterFilter;
@@ -27,10 +26,8 @@
 import io.micronaut.context.annotation.Bean;
 import io.micronaut.context.annotation.Factory;
 import io.micronaut.context.annotation.Primary;
-import io.micronaut.context.event.ShutdownEvent;
 import io.micronaut.core.annotation.TypeHint;
 import io.micronaut.core.util.CollectionUtils;
-import io.micronaut.runtime.event.annotation.EventListener;
 import jakarta.inject.Singleton;
 
 import java.util.Collection;
@@ -51,7 +48,6 @@
     public static final String MICRONAUT_METRICS_COMMON_TAGS = MICRONAUT_METRICS + "tags";
     public static final String MICRONAUT_METRICS_ENABLED = MICRONAUT_METRICS + "enabled";
     public static final String MICRONAUT_METRICS_EXPORT = MICRONAUT_METRICS + "export";
-    private MeterRegistry meterRegistry;
 
     /**
      * Create a CompositeMeterRegistry bean if metrics are enabled, true by default.
@@ -84,8 +80,7 @@
                 }
             }
         }
-        meterRegistry = compositeMeterRegistry;
-        Metrics.addRegistry(meterRegistry);
+
         return compositeMeterRegistry;
     }
 
@@ -105,13 +100,4 @@
                                                     Collection<MeterFilter> filters) {
         return new CompositeMeterRegistryConfigurer(binders, filters);
     }
-
-    /**
-     * Removes the registry from the global {@link Metrics}.
-     */
-    @EventListener
-    void onShutdown(ShutdownEvent shutdown) {
-        Metrics.removeRegistry(meterRegistry);
-    }
-
 }
```

### `micrometer-core/src/main/java/io/micronaut/configuration/metrics/micrometer/intercept/CountedInterceptor.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/micrometer-core/src/main/java/io/micronaut/configuration/metrics/micrometer/intercept/CountedInterceptor.java	2026-04-22 08:03:55.472671481 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/micrometer-core/src/main/java/io/micronaut/configuration/metrics/micrometer/intercept/CountedInterceptor.java	2026-04-22 08:03:40.261320240 +0000
@@ -27,12 +27,11 @@
 import io.micronaut.configuration.metrics.annotation.RequiresMetrics;
 import io.micronaut.configuration.metrics.util.MetricOptionsUtil;
 import io.micronaut.core.annotation.AnnotationMetadata;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.core.async.publisher.Publishers;
 import io.micronaut.core.convert.ConversionService;
 import io.micronaut.core.order.OrderUtil;
 import io.micronaut.core.util.StringUtils;
-import jakarta.inject.Inject;
 import org.reactivestreams.Publisher;
 import reactor.core.publisher.Flux;
 import reactor.core.publisher.Mono;
@@ -61,31 +60,6 @@
     private final ConversionService conversionService;
     private final List<AbstractMethodTagger> methodTaggers;
 
-    /**
-     * @param meterRegistry The meter registry
-     * @deprecated Pass conversion service in new constructor
-     */
-    @Deprecated
-    public CountedInterceptor(MeterRegistry meterRegistry) {
-        this(meterRegistry, ConversionService.SHARED);
-    }
-
-    /**
-     * @param meterRegistry The meter registry
-     * @param conversionService The conversion service
-     * @deprecated Pass list of AbstractMethodTagger in new constructor
-     */
-    @Deprecated
-    public CountedInterceptor(MeterRegistry meterRegistry, ConversionService conversionService) {
-        this(meterRegistry, conversionService, Collections.emptyList());
-    }
-
-    /**
-     * @param meterRegistry The meter registry
-     * @param conversionService The conversion service
-     * @param methodTaggers Additional tag builders
-     */
-    @Inject
     public CountedInterceptor(MeterRegistry meterRegistry, ConversionService conversionService, List<AbstractMethodTagger> methodTaggers) {
         this.meterRegistry = meterRegistry;
         this.conversionService = conversionService;
```

### `micrometer-core/src/main/java/io/micronaut/configuration/metrics/micrometer/intercept/TimedInterceptor.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/micrometer-core/src/main/java/io/micronaut/configuration/metrics/micrometer/intercept/TimedInterceptor.java	2026-04-22 08:03:55.472784815 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/micrometer-core/src/main/java/io/micronaut/configuration/metrics/micrometer/intercept/TimedInterceptor.java	2026-04-22 08:03:40.261402990 +0000
@@ -35,7 +35,6 @@
 import io.micronaut.core.convert.ConversionService;
 import io.micronaut.core.order.OrderUtil;
 import io.micronaut.core.util.CollectionUtils;
-import jakarta.inject.Inject;
 import jakarta.inject.Singleton;
 import org.HdrHistogram.ConcurrentHistogram;
 import org.HdrHistogram.Histogram;
@@ -90,29 +89,9 @@
 
     /**
      * @param meterRegistry The meter registry
-     * @deprecated Pass conversion service in new constructor
-     */
-    @Deprecated
-    protected TimedInterceptor(MeterRegistry meterRegistry) {
-        this(meterRegistry, ConversionService.SHARED, Collections.emptyList());
-    }
-
-    /**
-     * @param meterRegistry The meter registry
-     * @param conversionService The conversion service
-     * @deprecated Pass list of AbstractMethodTaggers in new constructor
-     */
-    @Deprecated
-    protected TimedInterceptor(MeterRegistry meterRegistry, ConversionService conversionService) {
-        this(meterRegistry, conversionService, Collections.emptyList());
-    }
-
-    /**
-     * @param meterRegistry The meter registry
      * @param conversionService The conversion service
      * @param methodTaggers Additional tag builders
      */
-    @Inject
     protected TimedInterceptor(MeterRegistry meterRegistry, ConversionService conversionService, List<AbstractMethodTagger> methodTaggers) {
         this.meterRegistry = meterRegistry;
         this.conversionService = conversionService;
```

### `micrometer-core/src/test/groovy/io/micronaut/configuration/metrics/binder/netty/MicronautNettyQueuesMetricsBinderSpec.groovy`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/micrometer-core/src/test/groovy/io/micronaut/configuration/metrics/binder/netty/MicronautNettyQueuesMetricsBinderSpec.groovy	2026-04-22 08:03:55.475358086 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/micrometer-core/src/test/groovy/io/micronaut/configuration/metrics/binder/netty/MicronautNettyQueuesMetricsBinderSpec.groovy	2026-04-22 08:03:40.263873802 +0000
@@ -9,7 +9,11 @@
 import io.micronaut.http.annotation.Controller
 import io.micronaut.http.annotation.Get
 import io.micronaut.http.client.annotation.Client
+import io.micronaut.http.netty.channel.EventLoopGroupFactory
+import io.micronaut.http.netty.channel.NettyChannelType
 import io.micronaut.runtime.server.EmbeddedServer
+import spock.lang.Unroll
+import spock.lang.Ignore
 import spock.lang.Specification
 
 import static io.micronaut.configuration.metrics.binder.netty.NettyMetrics.COUNT
@@ -18,40 +22,133 @@
 import static io.micronaut.configuration.metrics.binder.netty.NettyMetrics.GLOBAL
 import static io.micronaut.configuration.metrics.binder.netty.NettyMetrics.GROUP
 import static io.micronaut.configuration.metrics.binder.netty.NettyMetrics.NETTY
+import static io.micronaut.configuration.metrics.binder.netty.NettyMetrics.PARENT
 import static io.micronaut.configuration.metrics.binder.netty.NettyMetrics.QUEUE
 import static io.micronaut.configuration.metrics.binder.netty.NettyMetrics.WAIT_TIME
+import static io.micronaut.configuration.metrics.binder.netty.NettyMetrics.WORKER
 import static io.micronaut.configuration.metrics.binder.netty.NettyMetrics.dot
 import static io.micronaut.configuration.metrics.micrometer.MeterRegistryFactory.MICRONAUT_METRICS_BINDERS
+import static io.micronaut.configuration.metrics.micrometer.MeterRegistryFactory.MICRONAUT_METRICS_ENABLED
 
 class MicronautNettyQueuesMetricsBinderSpec extends Specification {
 
+    private static List<Class> eventLoopGroupFactoryInstrumentedClasses = [
+            InstrumentedNioEventLoopGroupFactory,
+            InstrumentedEpollEventLoopGroupFactory,
+            InstrumentedKQueueEventLoopGroupFactory
+    ]
+
+    @Unroll
+    void "test getting the beans #cfg #setting"() {
+        when:
+        ApplicationContext context = ApplicationContext.run([(cfg): setting])
+
+        then:
+        eventLoopGroupFactoryInstrumentedClasses
+                .collect { context.findBean(it).isPresent() }
+                .any() == result
+
+        cleanup:
+        context.close()
+
+        where:
+        cfg                                                 | setting | result
+        MICRONAUT_METRICS_ENABLED                           | true    | false
+        MICRONAUT_METRICS_ENABLED                           | false   | false
+        MICRONAUT_METRICS_BINDERS + ".netty.queues.enabled" | true    | true
+        MICRONAUT_METRICS_BINDERS + ".netty.queues.enabled" | false   | false
+    }
+
+    @Unroll("test getting #channelType channel class from #eventLoopGroupFactory.getClass().getSimpleName()")
+    void "test getting channel class from instrumented event loop group factory"(
+            NettyChannelType channelType,
+            EventLoopGroupFactory eventLoopGroupFactory
+    ) {
+        when:
+        Class channelClass = eventLoopGroupFactory.channelClass(channelType)
+
+        then:
+        noExceptionThrown()
+        channelClass != null
+
+        where:
+        [channelType, eventLoopGroupFactory] << [
+                NettyChannelType.values(),
+                [
+                        new InstrumentedNioEventLoopGroupFactory(null),
+                        new InstrumentedEpollEventLoopGroupFactory(null),
+                        new InstrumentedKQueueEventLoopGroupFactory(null)
+                ]
+        ].combinations()
+    }
+
+    @Unroll("test if #eventLoopGroupFactory.getClass().getSimpleName() is native")
+    void "test if instrumented event loop group factory is native"() {
+        when:
+        boolean isNative = eventLoopGroupFactory.isNative()
+
+        then:
+        isNative == result
+
+        where:
+        eventLoopGroupFactory                             | result
+        new InstrumentedNioEventLoopGroupFactory(null)    | false
+        new InstrumentedEpollEventLoopGroupFactory(null)  | true
+        new InstrumentedKQueueEventLoopGroupFactory(null) | true
+    }
+
+    @Ignore
     void "test queue metrics are present"() {
-        given:
+        when:
         ApplicationContext context = ApplicationContext.run(
                 [MICRONAUT_METRICS_ENABLED                            : true,
                  (MICRONAUT_METRICS_BINDERS + ".netty.queues.enabled"): true]
         )
         context.getBean(EmbeddedServer).start()
 
+        then:
+        eventLoopGroupFactoryInstrumentedClasses
+                .collect { context.findBean(it).isPresent() }
+                .any()
+
         when:
         MeterRegistry registry = context.getBean(MeterRegistry)
         RequiredSearch search = registry.get(dot(NETTY, QUEUE, GLOBAL, WAIT_TIME))
-        search.tags(Tags.of(GROUP, "default"))
+        search.tags(Tags.of(GROUP, PARENT))
         Timer globalParentWaitTimer = search.timer()
 
         search = registry.get(dot(NETTY, QUEUE, GLOBAL, EXECUTION_TIME))
-        search.tags(Tags.of(GROUP, "default"))
+        search.tags(Tags.of(GROUP, PARENT))
         Timer globalParentExecutionTime = search.timer()
 
         search = registry.get(dot(NETTY, QUEUE, GLOBAL, ELEMENT, COUNT))
-        search.tags(Tags.of(GROUP, "default"))
+        search.tags(Tags.of(GROUP, PARENT))
         Counter globalParentTaskCounter = search.counter()
 
+        search = registry.get(dot(NETTY, QUEUE, GLOBAL, WAIT_TIME))
+        search.tags(Tags.of(GROUP, WORKER))
+        Timer globalWorkerWaitTimer = search.timer()
+
+        search = registry.get(dot(NETTY, QUEUE, GLOBAL, EXECUTION_TIME))
+        search.tags(Tags.of(GROUP, WORKER))
+        Timer globalWorkerExecutionTimer = search.timer()
+
+        search = registry.get(dot(NETTY, QUEUE, GLOBAL, ELEMENT, COUNT))
+        search.tags(Tags.of(GROUP, WORKER))
+        Counter globalWorkerTaskCounter = search.counter()
+
         then:
         globalParentWaitTimer
         globalParentExecutionTime
         globalParentTaskCounter
 
+        globalWorkerWaitTimer
+        globalWorkerWaitTimer.count() == 0
+        globalWorkerExecutionTimer
+        globalWorkerExecutionTimer.count() == 0
+        globalWorkerTaskCounter
+        globalWorkerTaskCounter.count() == 0
+
         when:
         DummyClient client = context.getBean(DummyClient)
 
@@ -64,7 +161,10 @@
         client.test() == 'root'
         globalParentWaitTimer.count() > 0
         globalParentExecutionTime.count() > 0
+        globalWorkerWaitTimer.count() > 0
+        globalWorkerExecutionTimer.count() > 0
         globalParentTaskCounter.count() > 0
+        globalWorkerTaskCounter.count() > 0
 
         cleanup:
         context.close()
```

### `micrometer-core/src/test/groovy/io/micronaut/configuration/metrics/binder/retry/RetryMetricsBinderSpec.groovy`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/micrometer-core/src/test/groovy/io/micronaut/configuration/metrics/binder/retry/RetryMetricsBinderSpec.groovy	2026-04-22 08:03:55.475706672 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/micrometer-core/src/test/groovy/io/micronaut/configuration/metrics/binder/retry/RetryMetricsBinderSpec.groovy	2026-04-22 08:03:40.264345014 +0000
@@ -11,7 +11,7 @@
 
 import static io.micronaut.configuration.metrics.binder.retry.RetryMetricsBinder.RETRY_METRICS_ENABLED
 import static io.micronaut.configuration.metrics.micrometer.MeterRegistryFactory.MICRONAUT_METRICS_ENABLED
-import static org.junit.Assert.assertThrows
+import static org.junit.jupiter.api.Assertions.assertThrows
 
 class RetryMetricsBinderSpec extends Specification {
 
```

### `micrometer-core/src/test/groovy/io/micronaut/configuration/metrics/management/endpoint/FilteredMetricsEndpointSpec.groovy`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/micrometer-core/src/test/groovy/io/micronaut/configuration/metrics/management/endpoint/FilteredMetricsEndpointSpec.groovy	2026-04-22 08:03:55.476499178 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/micrometer-core/src/test/groovy/io/micronaut/configuration/metrics/management/endpoint/FilteredMetricsEndpointSpec.groovy	2026-04-22 08:03:40.265183187 +0000
@@ -18,7 +18,7 @@
 import io.micronaut.http.annotation.Get
 import io.micronaut.http.client.HttpClient
 import io.micronaut.runtime.server.EmbeddedServer
-import io.reactivex.Single
+import io.reactivex.rxjava3.core.Single
 import jakarta.inject.Singleton
 import jakarta.validation.constraints.NotBlank
 import reactor.core.publisher.Mono
@@ -55,7 +55,7 @@
 
         expect:
         client.toBlocking().exchange(HttpRequest.GET('/filtered/hello/fred'), String).body() == "Hello Fred"
-        client.toBlocking().exchange(HttpRequest.GET('/filtered/rxjava2/fred'), String).body() == "Hello Fred"
+        client.toBlocking().exchange(HttpRequest.GET('/filtered/rxjava3/fred'), String).body() == "Hello Fred"
     }
 
     void "test the filter beans are available"() {
@@ -122,7 +122,7 @@
 
         @Timed
         @Counted
-        @Get("/filtered/rxjava2/{name}")
+        @Get("/filtered/rxjava3/{name}")
         Single<String> rxjava(@NotBlank String name) {
             return Single.just('Hello ' + name.capitalize())
         }
```

### `micrometer-observation/src/main/java/io/micronaut/micrometer/observation/ObservationProperties.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/micrometer-observation/src/main/java/io/micronaut/micrometer/observation/ObservationProperties.java	2026-04-22 08:03:55.484070655 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/micrometer-observation/src/main/java/io/micronaut/micrometer/observation/ObservationProperties.java	2026-04-22 08:03:40.273327544 +0000
@@ -17,7 +17,7 @@
 
 
 import io.micronaut.context.annotation.ConfigurationProperties;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 
 import java.util.Map;
 
```

### `micrometer-observation/src/main/java/io/micronaut/micrometer/observation/interceptor/ObservedInterceptor.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/micrometer-observation/src/main/java/io/micronaut/micrometer/observation/interceptor/ObservedInterceptor.java	2026-04-22 08:03:55.484204531 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/micrometer-observation/src/main/java/io/micronaut/micrometer/observation/interceptor/ObservedInterceptor.java	2026-04-22 08:03:40.273476253 +0000
@@ -26,7 +26,7 @@
 import io.micronaut.context.annotation.Requires;
 import io.micronaut.core.annotation.AnnotationValue;
 import io.micronaut.core.annotation.Internal;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.core.convert.ConversionService;
 import io.micronaut.core.propagation.PropagatedContext;
 import jakarta.inject.Singleton;
```

### `micrometer-observation-datasource/src/main/java/io/micronaut/micrometer/observation/datasource/DataSourceBeanCreatedEventListener.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/micrometer-observation-datasource/src/main/java/io/micronaut/micrometer/observation/datasource/DataSourceBeanCreatedEventListener.java	2026-04-22 08:03:55.479586244 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/micrometer-observation-datasource/src/main/java/io/micronaut/micrometer/observation/datasource/DataSourceBeanCreatedEventListener.java	2026-04-22 08:03:40.268604881 +0000
@@ -20,7 +20,7 @@
 import io.micronaut.context.event.BeanCreatedEvent;
 import io.micronaut.context.event.BeanCreatedEventListener;
 import io.micronaut.core.annotation.Internal;
-import io.micronaut.core.annotation.NonNull;
+import org.jspecify.annotations.NonNull;
 import io.micronaut.core.order.Ordered;
 import jakarta.inject.Singleton;
 import net.ttddyy.dsproxy.support.ProxyDataSourceBuilder;
```

### `micrometer-observation-datasource/src/main/java/io/micronaut/micrometer/observation/datasource/ProxyDataSourceResolver.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/micrometer-observation-datasource/src/main/java/io/micronaut/micrometer/observation/datasource/ProxyDataSourceResolver.java	2026-04-22 08:03:55.479828246 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/micrometer-observation-datasource/src/main/java/io/micronaut/micrometer/observation/datasource/ProxyDataSourceResolver.java	2026-04-22 08:03:40.268864217 +0000
@@ -15,13 +15,12 @@
  */
 package io.micronaut.micrometer.observation.datasource;
 
-import io.micronaut.context.annotation.Primary;
+import io.micronaut.core.order.Ordered;
 import io.micronaut.jdbc.DataSourceResolver;
 import jakarta.inject.Singleton;
 import net.ttddyy.dsproxy.support.ProxyDataSource;
 
 import javax.sql.DataSource;
-import java.util.List;
 
 /**
  * A custom implementation of {@link DataSourceResolver} that resolves the underlying target data source
@@ -34,25 +33,19 @@
  * @since 5.10
  */
 @Singleton
-@Primary
-final class ProxyDataSourceResolver implements DataSourceResolver {
-
-    private final List<DataSourceResolver> dataSourceResolvers;
-
-    ProxyDataSourceResolver(List<DataSourceResolver> dataSourceResolvers) {
-        this.dataSourceResolvers = dataSourceResolvers;
-    }
+final class ProxyDataSourceResolver implements DataSourceResolver, Ordered {
 
     @Override
     public DataSource resolve(DataSource dataSource) {
-        // The list of resolvers can be empty
-        for (DataSourceResolver dataSourceResolver : dataSourceResolvers) {
-            dataSource = dataSourceResolver.resolve(dataSource);
-        }
         // Unwrap ProxyDataSource if needed
         if (dataSource instanceof ProxyDataSource proxyDataSource) {
             dataSource = proxyDataSource.getDataSource();
         }
         return dataSource;
     }
+
+    @Override
+    public int getOrder() {
+        return Ordered.LOWEST_PRECEDENCE;
+    }
 }
```

### `micrometer-observation-http/build.gradle`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/micrometer-observation-http/build.gradle	2026-04-22 08:03:55.480857129 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/micrometer-observation-http/build.gradle	2026-04-22 08:03:40.269922308 +0000
@@ -19,8 +19,8 @@
     testImplementation mn.micronaut.http.server.netty
     testImplementation mnReactor.micronaut.reactor
     testImplementation mnReactor.micronaut.reactor.http.client
-    testImplementation mnRxjava2.micronaut.rxjava2
-    testImplementation mnRxjava2.micronaut.rxjava2.http.client
+    testImplementation(mnRxjava3.micronaut.rxjava3)
+    testImplementation(mnRxjava3.micronaut.rxjava3.http.client)
     testImplementation mnSerde.micronaut.serde.jackson
     testImplementation(libs.managed.micrometer.observation.test) {
         exclude group: 'org.junit.jupiter', module: 'junit-jupiter'
```

### `micrometer-observation-http/src/main/java/io/micronaut/micrometer/observation/http/AbstractObservationFilter.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/micrometer-observation-http/src/main/java/io/micronaut/micrometer/observation/http/AbstractObservationFilter.java	2026-04-22 08:03:55.481395009 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/micrometer-observation-http/src/main/java/io/micronaut/micrometer/observation/http/AbstractObservationFilter.java	2026-04-22 08:03:40.270369354 +0000
@@ -16,7 +16,7 @@
 package io.micronaut.micrometer.observation.http;
 
 import io.micronaut.core.annotation.Internal;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 
 import java.util.function.Predicate;
 
```

### `micrometer-observation-http/src/main/java/io/micronaut/micrometer/observation/http/ObservationHttpExclusionsConfiguration.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/micrometer-observation-http/src/main/java/io/micronaut/micrometer/observation/http/ObservationHttpExclusionsConfiguration.java	2026-04-22 08:03:55.481482509 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/micrometer-observation-http/src/main/java/io/micronaut/micrometer/observation/http/ObservationHttpExclusionsConfiguration.java	2026-04-22 08:03:40.270453479 +0000
@@ -16,7 +16,7 @@
 package io.micronaut.micrometer.observation.http;
 
 import io.micronaut.context.annotation.ConfigurationProperties;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.core.util.CollectionUtils;
 
 import java.util.List;
```

### `micrometer-observation-http/src/main/java/io/micronaut/micrometer/observation/http/client/ObservationClientFilter.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/micrometer-observation-http/src/main/java/io/micronaut/micrometer/observation/http/client/ObservationClientFilter.java	2026-04-22 08:03:55.481637469 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/micrometer-observation-http/src/main/java/io/micronaut/micrometer/observation/http/client/ObservationClientFilter.java	2026-04-22 08:03:40.270609647 +0000
@@ -19,7 +19,7 @@
 import io.micrometer.observation.ObservationRegistry;
 import io.micronaut.context.annotation.Requires;
 import io.micronaut.core.annotation.Internal;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.core.propagation.MutablePropagatedContext;
 import io.micronaut.http.HttpResponse;
 import io.micronaut.http.MutableHttpRequest;
```

### `micrometer-observation-http/src/main/java/io/micronaut/micrometer/observation/http/client/instrumentation/ClientRequestObservationContext.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/micrometer-observation-http/src/main/java/io/micronaut/micrometer/observation/http/client/instrumentation/ClientRequestObservationContext.java	2026-04-22 08:03:55.481869138 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/micrometer-observation-http/src/main/java/io/micronaut/micrometer/observation/http/client/instrumentation/ClientRequestObservationContext.java	2026-04-22 08:03:40.270898733 +0000
@@ -17,7 +17,7 @@
 
 import io.micrometer.observation.transport.RequestReplySenderContext;
 import io.micronaut.core.annotation.Internal;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.http.HttpResponse;
 import io.micronaut.http.MutableHttpRequest;
 
```

### `micrometer-observation-http/src/main/java/io/micronaut/micrometer/observation/http/server/ObservationServerFilter.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/micrometer-observation-http/src/main/java/io/micronaut/micrometer/observation/http/server/ObservationServerFilter.java	2026-04-22 08:03:55.482210307 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/micrometer-observation-http/src/main/java/io/micronaut/micrometer/observation/http/server/ObservationServerFilter.java	2026-04-22 08:03:40.271349653 +0000
@@ -19,7 +19,7 @@
 import io.micrometer.observation.ObservationRegistry;
 import io.micronaut.context.annotation.Requires;
 import io.micronaut.core.annotation.Internal;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.core.propagation.MutablePropagatedContext;
 import io.micronaut.http.HttpRequest;
 import io.micronaut.http.MutableHttpResponse;
```

### `micrometer-observation-http/src/main/java/io/micronaut/micrometer/observation/http/server/instrumentation/ServerRequestObservationContext.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/micrometer-observation-http/src/main/java/io/micronaut/micrometer/observation/http/server/instrumentation/ServerRequestObservationContext.java	2026-04-22 08:03:55.482550685 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/micrometer-observation-http/src/main/java/io/micronaut/micrometer/observation/http/server/instrumentation/ServerRequestObservationContext.java	2026-04-22 08:03:40.271704239 +0000
@@ -17,7 +17,7 @@
 
 import io.micrometer.observation.transport.RequestReplyReceiverContext;
 import io.micronaut.core.annotation.Internal;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.http.HttpRequest;
 import io.micronaut.http.MutableHttpResponse;
 
```

### `micrometer-observation-http/src/test/groovy/io/micronaut/micrometer/observation/ObservationHttpSpec.groovy`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/micrometer-observation-http/src/test/groovy/io/micronaut/micrometer/observation/ObservationHttpSpec.groovy	2026-04-22 08:03:55.483166231 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/micrometer-observation-http/src/test/groovy/io/micronaut/micrometer/observation/ObservationHttpSpec.groovy	2026-04-22 08:03:40.272280952 +0000
@@ -25,9 +25,10 @@
 import io.micronaut.micrometer.observation.utils.ObservedReactorPropagation
 import io.micronaut.reactor.http.client.ReactorHttpClient
 import io.micronaut.runtime.server.EmbeddedServer
-import io.micronaut.rxjava2.http.client.RxHttpClient
+import io.micronaut.rxjava3.http.client.Rx3HttpClient
+import io.micronaut.scheduling.TaskExecutors
 import io.micronaut.scheduling.annotation.ExecuteOn
-import io.reactivex.Single
+import io.reactivex.rxjava3.core.Single
 import jakarta.inject.Inject
 import jakarta.inject.Singleton
 import org.reactivestreams.Publisher
@@ -42,7 +43,6 @@
 import java.util.concurrent.CompletableFuture
 import java.util.concurrent.CompletionStage
 
-import static io.micronaut.scheduling.TaskExecutors.IO
 
 @Slf4j("LOG")
 class ObservationHttpSpec extends Specification {
@@ -172,10 +172,10 @@
         testObservationRegistry.clear()
     }
 
-    void 'test observation rxjava2'() {
+    void 'test observation rxjava3'() {
 
         when:
-        HttpResponse<String> response = reactorHttpClient.toBlocking().exchange('/rxjava2/test', String)
+        HttpResponse<String> response = reactorHttpClient.toBlocking().exchange('/rxjava3/test', String)
 
         then:
         conditions.eventually {
@@ -331,8 +331,8 @@
             TestObservationRegistryAssert.assertThat(testObservationRegistry).hasAnObservation {
                 it.hasContextualNameEqualTo("http get /propagate/nestedReactive/{name}")
                 it.hasNameEqualTo("http.server.requests")
-                it.hasLowCardinalityKeyValue("foo", "bar")
-                it.hasLowCardinalityKeyValue("foo2", "bar2")
+                it.hasHighCardinalityKeyValue("foo", "bar")
+                it.hasHighCardinalityKeyValue("foo2", "bar2")
             }
         }
 
@@ -354,8 +354,8 @@
             TestObservationRegistryAssert.assertThat(testObservationRegistry).hasAnObservation {
                 it.hasContextualNameEqualTo("http get /propagate/nestedReactive2/{name}")
                 it.hasNameEqualTo("http.server.requests")
-                it.hasLowCardinalityKeyValue("foo", "bar")
-                it.hasLowCardinalityKeyValue("foo3", "bar3")
+                it.hasHighCardinalityKeyValue("foo", "bar")
+                it.hasHighCardinalityKeyValue("foo3", "bar3")
             }
         }
 
@@ -377,7 +377,7 @@
         @Inject
         ObservationRegistry observationRegistry
 
-        @ExecuteOn(IO)
+        @ExecuteOn(TaskExecutors.BLOCKING)
         @Post("/enter")
         @Observed(name = "enter")
         Mono<String> enter(@Header("X-TrackingId") String tracingId, @Body SomeBody body) {
@@ -389,7 +389,7 @@
             )
         }
 
-        @ExecuteOn(IO)
+        @ExecuteOn(TaskExecutors.BLOCKING)
         @Get("/test")
         @Observed
         Mono<String> test(@Header("X-TrackingId") String tracingId) {
@@ -407,7 +407,7 @@
 
         }
 
-        @ExecuteOn(IO)
+        @ExecuteOn(TaskExecutors.BLOCKING)
         @Get("/test2")
         Mono<String> test2(@Header("X-TrackingId") String tracingId) {
             LOG.debug("test2")
@@ -455,13 +455,13 @@
         Publisher<String> nestedReactive(String name) {
 
             def current = observationRegistry.getCurrentObservation()
-            current.lowCardinalityKeyValue('foo', 'bar')
+            current.highCardinalityKeyValue('foo', 'bar')
             return Flux.deferContextual { contextView ->
                 Flux.from(propagateClient.continuedRx(name))
                         .flatMap({ String res ->
                             // Here thread switch can occur,
                             // that means the thread might be different and Span.current() wouldn't work
-                            current.lowCardinalityKeyValue('foo2', 'bar2')
+                            current.highCardinalityKeyValue('foo2', 'bar2')
                             // NOTE: the span needs to be not closed for this attribute setting to work
                             return Mono.just(name)
                         })
@@ -472,7 +472,7 @@
         @SingleResult
         Publisher<String> nestedReactive2(String name) {
             def current = observationRegistry.getCurrentObservation()
-            current.lowCardinalityKeyValue('foo', 'bar')
+            current.highCardinalityKeyValue('foo', 'bar')
             return Flux.deferContextual { contextView ->
                 {
                         Flux.from(propagateClient.continuedRx(name))
@@ -481,7 +481,7 @@
                                     // that means the thread might be different and Span.current() wouldn't work
                                     // We need can retrieve the current span from the Reactor context
                                     def currentInnerSpan = ObservedReactorPropagation.currentObservation(contextView)
-                                    currentInnerSpan.lowCardinalityKeyValue('foo3', 'bar3')
+                                    currentInnerSpan.highCardinalityKeyValue('foo3', 'bar3')
                                     return Mono.just(name)
                                 }).contextWrite(contextView)
                     }
@@ -559,18 +559,18 @@
         void excludeTest() {}
     }
 
-    @Controller('/rxjava2')
-    static class RxJava2 {
+    @Controller('/rxjava3')
+    static class RxJava {
 
         @Inject
         @Client("/")
-        RxHttpClient rxHttpClient
+        Rx3HttpClient rxHttpClient
 
         @Get("/test")
         Single<String> test() {
             return Single.fromPublisher(
                     rxHttpClient.retrieve(HttpRequest
-                            .GET("/rxjava2/test2"), String)
+                            .GET("/rxjava3/test2"), String)
             )
         }
 
```

### `micrometer-registry-cloudwatch/src/main/java/io/micronaut/configuration/metrics/micrometer/cloudwatch/CloudWatchMeterRegistryFactory.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/micrometer-registry-cloudwatch/src/main/java/io/micronaut/configuration/metrics/micrometer/cloudwatch/CloudWatchMeterRegistryFactory.java	2026-04-22 08:03:55.489181571 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/micrometer-registry-cloudwatch/src/main/java/io/micronaut/configuration/metrics/micrometer/cloudwatch/CloudWatchMeterRegistryFactory.java	2026-04-22 08:03:40.279748220 +0000
@@ -23,8 +23,7 @@
 import io.micronaut.context.annotation.Bean;
 import io.micronaut.context.annotation.Factory;
 import io.micronaut.context.annotation.Requires;
-import io.micronaut.core.annotation.Nullable;
-import jakarta.inject.Inject;
+import org.jspecify.annotations.Nullable;
 import jakarta.inject.Named;
 import jakarta.inject.Singleton;
 import software.amazon.awssdk.auth.credentials.AwsCredentialsProviderChain;
@@ -51,7 +50,6 @@
     public static final String CLOUDWATCH_ENABLED = CLOUDWATCH_CONFIG + ".enabled";
     public static final String CLOUDWATCH_DEFAULT_NAMESPACE = "micronaut";
 
-    @Inject
     protected CloudWatchMeterRegistryFactory(AwsCredentialsProviderChain credentialsProvider,
                                           AwsRegionProviderChain regionProvider,
                                           @Nullable UserAgentProvider userAgentProvider,
@@ -59,23 +57,6 @@
         super(credentialsProvider, regionProvider, userAgentProvider, awsServiceConfiguration);
     }
 
-    /**
-     * @deprecated Use {@link CloudWatchMeterRegistryFactory(AwsCredentialsProviderChain, AwsRegionProviderChain, UserAgentProvider, AWSServiceConfiguration)} instead.
-     */
-    @Deprecated(since = "5.2.0", forRemoval = true)
-    public CloudWatchMeterRegistryFactory() {
-        this(AwsCredentialsProviderChain.builder().build(), new AwsRegionProviderChain(), null, null);
-    }
-
-    /**
-     *
-     * @deprecated Use {@link #createAsyncBuilder()} instead.
-     */
-    @Deprecated(since = "5.2.0", forRemoval = true)
-    CloudWatchAsyncClientBuilder cloudWatchAsyncClientBuilder() {
-        return createAsyncBuilder();
-    }
-
     @Override
     protected CloudWatchClientBuilder createSyncBuilder() {
         return CloudWatchClient.builder();
@@ -115,26 +96,14 @@
     }
 
     /**
+     * Create a CloudWatchMeterRegistry bean if global metrics are enabled
+     * and CloudWatch is enabled. Will be true by default when this
+     * configuration is included in project.
      *
-     * @param builder A {@link CloudWatchAsyncClient} builder.
-     * @return A {@link CloudWatchAsyncClient}
-     * @deprecated Use {{@link #asyncClient(CloudWatchAsyncClientBuilder)}} instead.
+     * @param exportConfigurationProperties The export configuration
+     * @param cloudWatchAsyncClient  The CloudWatch async client
+     * @return A CloudWatchMeterRegistry
      */
-    @Deprecated(since = "5.2.0", forRemoval = true)
-    CloudWatchAsyncClient cloudWatchAsyncClient(CloudWatchAsyncClientBuilder builder) {
-       return asyncClient(builder);
-    }
-
-
-        /**
-         * Create a CloudWatchMeterRegistry bean if global metrics are enabled
-         * and CloudWatch is enabled. Will be true by default when this
-         * configuration is included in project.
-         *
-         * @param exportConfigurationProperties The export configuration
-         * @param cloudWatchAsyncClient  The CloudWatch async client
-         * @return A CloudWatchMeterRegistry
-         */
     @Singleton
     CloudWatchMeterRegistry cloudWatchMeterRegistry(ExportConfigurationProperties exportConfigurationProperties,
                                                     CloudWatchAsyncClient cloudWatchAsyncClient) {
```

### `micrometer-registry-graphite/src/main/java/io/micronaut/configuration/metrics/micrometer/graphite/GraphiteMeterRegistryFactory.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/micrometer-registry-graphite/src/main/java/io/micronaut/configuration/metrics/micrometer/graphite/GraphiteMeterRegistryFactory.java	2026-04-22 08:03:55.495075035 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/micrometer-registry-graphite/src/main/java/io/micronaut/configuration/metrics/micrometer/graphite/GraphiteMeterRegistryFactory.java	2026-04-22 08:03:40.287394740 +0000
@@ -20,7 +20,7 @@
 import io.micronaut.configuration.metrics.micrometer.ExportConfigurationProperties;
 import io.micronaut.context.annotation.Factory;
 import io.micronaut.context.annotation.Property;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import jakarta.inject.Singleton;
 
 import java.util.List;
```

### `micrometer-registry-prometheus/src/test/groovy/io/micronaut/configuration/metrics/micrometer/prometheus/management/PrometheusEndpointSpec.groovy`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/micrometer-registry-prometheus/src/test/groovy/io/micronaut/configuration/metrics/micrometer/prometheus/management/PrometheusEndpointSpec.groovy	2026-04-22 08:03:55.507789845 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/micrometer-registry-prometheus/src/test/groovy/io/micronaut/configuration/metrics/micrometer/prometheus/management/PrometheusEndpointSpec.groovy	2026-04-22 08:03:40.304429876 +0000
@@ -1,16 +1,25 @@
 package io.micronaut.configuration.metrics.micrometer.prometheus.management
 
+import io.micrometer.core.instrument.MeterRegistry
+import io.micrometer.core.instrument.binder.jvm.JvmMemoryMetrics
+import io.micrometer.core.instrument.binder.system.ProcessorMetrics
 import io.micronaut.context.ApplicationContext
 import io.micronaut.http.client.HttpClient
 import io.micronaut.runtime.server.EmbeddedServer
 import spock.lang.AutoCleanup
-import spock.lang.IgnoreIf
 import spock.lang.PendingFeature
 import spock.lang.Shared
 import spock.lang.Specification
 
 class PrometheusEndpointSpec extends Specification {
 
+    def setup() {
+        def registry = embeddedServer.applicationContext.getBean(MeterRegistry)
+
+        new JvmMemoryMetrics().bindTo(registry)
+        new ProcessorMetrics().bindTo(registry)
+    }
+
     @Shared
     @AutoCleanup
     EmbeddedServer embeddedServer = ApplicationContext.run(EmbeddedServer, [
@@ -22,7 +31,6 @@
     @AutoCleanup
     HttpClient client = embeddedServer.applicationContext.createBean(HttpClient, embeddedServer.URL)
 
-    @IgnoreIf({ jvm.isJava21() })
     void "test prometheus scrape"() {
         expect:
         client.toBlocking().retrieve('/prometheus').contains('jvm_memory_used')
```

### `micrometer-registry-prometheus-pushgateway/src/main/java/io/micronaut/configuration/metrics/micrometer/prometheus/pushgateway/PrometheusPushGatewayConfig.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/micrometer-registry-prometheus-pushgateway/src/main/java/io/micronaut/configuration/metrics/micrometer/prometheus/pushgateway/PrometheusPushGatewayConfig.java	2026-04-22 08:03:55.505384950 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/micrometer-registry-prometheus-pushgateway/src/main/java/io/micronaut/configuration/metrics/micrometer/prometheus/pushgateway/PrometheusPushGatewayConfig.java	2026-04-22 08:03:40.301243308 +0000
@@ -21,7 +21,7 @@
 import io.micronaut.context.annotation.ConfigurationProperties;
 import io.micronaut.context.annotation.Requires;
 import io.micronaut.core.annotation.Internal;
-import io.micronaut.core.annotation.Nullable;
+import org.jspecify.annotations.Nullable;
 import io.micronaut.core.util.StringUtils;
 import io.prometheus.metrics.exporter.pushgateway.PushGateway;
 
```

### `src/main/docs/guide/toc.yml`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/src/main/docs/guide/toc.yml	2026-04-22 08:03:55.515368030 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/src/main/docs/guide/toc.yml	2026-04-22 08:03:40.314304830 +0000
@@ -32,4 +32,5 @@
   title: Observation
   datasourceObservation: Datasource Observation
 metricsGuides: Guides
+breaks: Breaking Changes
 repository: Repository
```

### `test-suite/micronaut-serialization/build.gradle`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/test-suite/micronaut-serialization/build.gradle	2026-04-22 08:03:55.515527281 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/test-suite/micronaut-serialization/build.gradle	2026-04-22 08:03:40.314496831 +0000
@@ -23,7 +23,6 @@
 }
 
 graalvmNative.toolchainDetection = false
-
 micronaut {
     version.set(libs.versions.micronaut.platform)
     runtime("netty")
```

### `test-suite/micronaut-serialization/src/test/java/io/micronaut/configuration/metrics/serialization/MetricsMicronautSerializationTest.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/test-suite/micronaut-serialization/src/test/java/io/micronaut/configuration/metrics/serialization/MetricsMicronautSerializationTest.java	2026-04-22 08:03:55.516037702 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/test-suite/micronaut-serialization/src/test/java/io/micronaut/configuration/metrics/serialization/MetricsMicronautSerializationTest.java	2026-04-22 08:03:40.315023877 +0000
@@ -8,7 +8,9 @@
 import io.micronaut.test.extensions.junit5.annotation.MicronautTest;
 import org.junit.jupiter.api.Assertions;
 import org.junit.jupiter.api.Test;
+import org.junit.jupiter.api.condition.DisabledInNativeImage;
 
+@DisabledInNativeImage
 @MicronautTest
 class MetricsMicronautSerializationTest {
 
```

### `test-suite/test-observation-datasource/build.gradle`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/test-suite/test-observation-datasource/build.gradle	2026-04-22 08:03:55.516378371 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/test-suite/test-observation-datasource/build.gradle	2026-04-22 08:03:40.315885550 +0000
@@ -27,7 +27,6 @@
 }
 
 graalvmNative.toolchainDetection = false
-
 micronaut {
     version.set(libs.versions.micronaut.platform)
     runtime("netty")
```

### `test-suite/test-observation-datasource/src/test/java/io/micronaut/micrometer/observation/datasource/MicronautObservationDataSourceTest.java`

```diff
--- /sessions/trusting-serene-planck/mnt/micronaut-micrometer/test-suite/test-observation-datasource/src/test/java/io/micronaut/micrometer/observation/datasource/MicronautObservationDataSourceTest.java	2026-04-22 08:03:55.516943668 +0000
+++ /sessions/trusting-serene-planck/mnt/mn5--micronaut-micrometer/test-suite/test-observation-datasource/src/test/java/io/micronaut/micrometer/observation/datasource/MicronautObservationDataSourceTest.java	2026-04-22 08:03:40.316544472 +0000
@@ -17,10 +17,11 @@
 import net.ttddyy.observation.tracing.DataSourceBaseObservationHandler;
 import org.junit.jupiter.api.Assertions;
 import org.junit.jupiter.api.Test;
+import org.junit.jupiter.api.condition.DisabledInNativeImage;
 
 import java.util.List;
 
-
+@DisabledInNativeImage
 @MicronautTest
 @Property(name = "spec.name", value = "micrometer-ds-native-test")
 class MicronautObservationDataSourceTest {
```

---

_Report generated by git-branch-diff skill._
