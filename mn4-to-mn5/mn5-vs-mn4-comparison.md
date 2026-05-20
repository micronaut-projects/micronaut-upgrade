# Release Note Comparison

Generated: 2026-05-13 10:25 UTC
Comparison: `mn5-5.0.x` -> `mn4-4.10.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn5/micronaut-core` | `5.0.x` | `54d1ebd157bf` | `git@github.com:micronaut-projects/micronaut-core.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn4/micronaut-core` | `4.10.x` | `c2b22742d650` | `git@github.com:micronaut-projects/micronaut-core.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn4/micronaut-core`
- Commit candidates found: 19
- File changes listed: 1000
- Version values listed: 265
- File status counts: A=8, D=130, M=859, R=3

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `25.0.1-graal` | `not present` | `removed` |
| `gradle.properties` | `graalVersion` | `25.0.2` | `23.1.8` | `changed` |
| `gradle.properties` | `projectVersion` | `5.0.0` | `4.10.24-SNAPSHOT` | `changed` |
| `gradle/libs.versions.toml` | `libraries.awaitility` | `org.awaitility:awaitility:4.3.0` | `org.awaitility:awaitility:4.3.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.bcpkix` | `org.bouncycastle:bcpkix-jdk18on:1.84` | `org.bouncycastle:bcpkix-jdk15on:1.70` | `changed` |
| `gradle/libs.versions.toml` | `libraries.blaze-persistence-core` | `com.blazebit:blaze-persistence-core-impl:1.6.18` | `com.blazebit:blaze-persistence-core-impl:1.6.17` | `changed` |
| `gradle/libs.versions.toml` | `libraries.boms-groovy` | `org.apache.groovy:groovy-bom:5.0.6` | `org.apache.groovy:groovy-bom:4.0.28` | `changed` |
| `gradle/libs.versions.toml` | `libraries.boms-jackson` | `tools.jackson:jackson-bom:3.1.3` | `com.fasterxml.jackson:jackson-bom:2.21.2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.boms-kotlin` | `org.jetbrains.kotlin:kotlin-bom:2.3.21` | `org.jetbrains.kotlin:kotlin-bom:1.9.25` | `changed` |
| `gradle/libs.versions.toml` | `libraries.boms-kotlin-coroutines` | `org.jetbrains.kotlinx:kotlinx-coroutines-bom:1.10.2` | `org.jetbrains.kotlinx:kotlinx-coroutines-bom:1.8.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.boms-micronaut-sourcegen` | `io.micronaut.sourcegen:micronaut-sourcegen-bom:2.0.0-RC4` | `io.micronaut.sourcegen:micronaut-sourcegen-bom:1.8.2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.boms-netty` | `io.netty:netty-bom:4.2.13.Final` | `io.netty:netty-bom:4.2.13.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.brotli4j` | `com.aayushatharva.brotli4j:brotli4j:1.18.0` | `com.aayushatharva.brotli4j:brotli4j:1.18.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.bytebuddy` | `net.bytebuddy:byte-buddy:1.18.8` | `net.bytebuddy:byte-buddy:1.17.8` | `changed` |
| `gradle/libs.versions.toml` | `libraries.bytebuddy-agent` | `net.bytebuddy:byte-buddy-agent:1.18.8` | `net.bytebuddy:byte-buddy-agent:1.17.8` | `changed` |
| `gradle/libs.versions.toml` | `libraries.caffeine` | `com.github.ben-manes.caffeine:caffeine:2.9.3` | `com.github.ben-manes.caffeine:caffeine:2.9.3` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.classgraph` | `io.github.classgraph:classgraph:4.8.184` | `io.github.classgraph:classgraph:4.8.181` | `changed` |
| `gradle/libs.versions.toml` | `libraries.compile-testing` | `com.google.testing.compile:compile-testing:0.21.0` | `com.google.testing.compile:compile-testing:0.21.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.error-prone-core` | `com.google.errorprone:error_prone_core:2.48.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.geb-spock` | `org.gebish:geb-spock:7.0` | `org.gebish:geb-spock:7.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.graal` | `not present` | `org.graalvm.sdk:nativeimage:23.1.8` | `added` |
| `gradle/libs.versions.toml` | `libraries.gradle-errorprone` | `net.ltgt.errorprone:net.ltgt.errorprone.gradle.plugin:4.4.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.groovy-test-junit5` | `org.apache.groovy:groovy-test-junit5:5.0.6` | `org.apache.groovy:groovy-test-junit5:4.0.28` | `changed` |
| `gradle/libs.versions.toml` | `libraries.h2` | `com.h2database:h2:2.4.240` | `com.h2database:h2:2.2.224` | `changed` |
| `gradle/libs.versions.toml` | `libraries.hibernate` | `org.hibernate:hibernate-core:5.5.9.Final` | `org.hibernate:hibernate-core:5.5.9.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.htmlsanitycheck` | `org.aim42:htmlSanityCheck:1.1.6` | `org.aim42:htmlSanityCheck:1.1.6` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.htmlunit` | `net.sourceforge.htmlunit:htmlunit:2.70.0` | `net.sourceforge.htmlunit:htmlunit:2.70.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.httpcomponents-client` | `org.apache.httpcomponents:httpclient:4.5.14` | `org.apache.httpcomponents:httpclient:4.5.14` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.httpcomponents-mime` | `org.apache.httpcomponents:httpmime:4.5.14` | `org.apache.httpcomponents:httpmime:4.5.14` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.icu4j` | `com.ibm.icu:icu4j:76.1` | `com.ibm.icu:icu4j:76.1` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.jackson2-databind` | `com.fasterxml.jackson.core:jackson-databind:2.21.3` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.jakarta-el` | `jakarta.el:jakarta.el-api:5.0.1` | `jakarta.el:jakarta.el-api:5.0.1` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.jakarta-el-impl` | `org.glassfish:jakarta.el:5.0.0-M1` | `org.glassfish:jakarta.el:5.0.0-M1` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.jakarta-inject-api` | `jakarta.inject:jakarta.inject-api:2.0.1` | `jakarta.inject:jakarta.inject-api:2.0.1` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.jakarta-inject-tck` | `jakarta.inject:jakarta.inject-tck:2.0.1` | `jakarta.inject:jakarta.inject-tck:2.0.1` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.jakarta-persistence` | `jakarta.persistence:jakarta.persistence-api:3.2.0` | `jakarta.persistence:jakarta.persistence-api:3.2.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.japicmp-gradle-plugin` | `me.champeau.gradle:japicmp-gradle-plugin:0.4.6` | `me.champeau.gradle:japicmp-gradle-plugin:0.4.6` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.javax-annotation-api` | `javax.annotation:javax.annotation-api:1.3.2` | `javax.annotation:javax.annotation-api:1.3.2` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.javax-inject` | `javax.inject:javax.inject:1` | `javax.inject:javax.inject:1` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.javax-persistence` | `javax.persistence:javax.persistence-api:2.2` | `javax.persistence:javax.persistence-api:2.2` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.jazzer-api` | `com.code-intelligence:jazzer-api:0.24.0` | `com.code-intelligence:jazzer-api:0.24.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.jazzer-junit` | `com.code-intelligence:jazzer-junit:0.24.0` | `com.code-intelligence:jazzer-junit:0.24.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.jcache` | `javax.cache:cache-api:1.1.1` | `javax.cache:cache-api:1.1.1` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.jetbrains-annotations` | `org.jetbrains:annotations:23.1.0` | `org.jetbrains:annotations:23.1.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.jetty-alpn-openjdk8-client` | `org.eclipse.jetty:jetty-alpn-openjdk8-client:9.4.58.v20250814` | `org.eclipse.jetty:jetty-alpn-openjdk8-client:9.4.58.v20250814` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.jfrunit-core` | `org.moditect.jfrunit:jfrunit-core:1.0.0.Alpha2` | `org.moditect.jfrunit:jfrunit-core:1.0.0.Alpha2` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.jmh-core` | `org.openjdk.jmh:jmh-core:1.37` | `org.openjdk.jmh:jmh-core:1.37` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.jmh-generator-annprocess` | `org.openjdk.jmh:jmh-generator-annprocess:1.37` | `org.openjdk.jmh:jmh-generator-annprocess:1.37` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.jsr107` | `org.jsr107.ri:cache-ri-impl:1.1.1` | `org.jsr107.ri:cache-ri-impl:1.1.1` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.jsr305` | `com.google.code.findbugs:jsr305:3.0.2` | `com.google.code.findbugs:jsr305:3.0.2` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.junit-jupiter` | `org.junit.jupiter:junit-jupiter:5.12.2` | `org.junit.jupiter:junit-jupiter:5.12.2` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.junit-jupiter-api` | `org.junit.jupiter:junit-jupiter-api:5.12.2` | `org.junit.jupiter:junit-jupiter-api:5.12.2` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.junit-jupiter-engine` | `org.junit.jupiter:junit-jupiter-engine:5.12.2` | `org.junit.jupiter:junit-jupiter-engine:5.12.2` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.junit-jupiter-params` | `org.junit.jupiter:junit-jupiter-params:5.12.2` | `org.junit.jupiter:junit-jupiter-params:5.12.2` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.junit-platform-engine` | `org.junit.platform:junit-platform-suite-engine:1.12.2` | `org.junit.platform:junit-platform-suite-engine:1.12.2` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.junit-platform-launcher` | `org.junit.platform:junit-platform-launcher:1.12.2` | `org.junit.platform:junit-platform-launcher:1.12.2` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.junit-vintage` | `org.junit.vintage:junit-vintage-engine:5.12.2` | `org.junit.vintage:junit-vintage-engine:5.12.2` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.junit4` | `junit:junit:4.13.2` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.kotlin2-annotation-processing-embeddable` | `not present` | `org.jetbrains.kotlin:kotlin-annotation-processing-embeddable:2.1.21` | `added` |
| `gradle/libs.versions.toml` | `libraries.kotlin2-compiler-embeddable` | `not present` | `org.jetbrains.kotlin:kotlin-compiler-embeddable:2.1.21` | `added` |
| `gradle/libs.versions.toml` | `libraries.kotlin2-reflect` | `not present` | `org.jetbrains.kotlin:kotlin-reflect:2.1.21` | `added` |
| `gradle/libs.versions.toml` | `libraries.kotlin2-stdlib` | `not present` | `org.jetbrains.kotlin:kotlin-stdlib:2.1.21` | `added` |
| `gradle/libs.versions.toml` | `libraries.kotlin2-stdlib-jdk8` | `not present` | `org.jetbrains.kotlin:kotlin-stdlib-jdk8:2.1.21` | `added` |
| `gradle/libs.versions.toml` | `libraries.kotlin2-test` | `not present` | `org.jetbrains.kotlin:kotlin-test:2.1.21` | `added` |
| `gradle/libs.versions.toml` | `libraries.ksp-aaEmbeddable` | `com.google.devtools.ksp:symbol-processing-aa-embeddable:2.3.6` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.ksp-commonDeps` | `com.google.devtools.ksp:symbol-processing-common-deps:2.3.6` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.ksp2` | `not present` | `com.google.devtools.ksp:symbol-processing:2.1.21-2.0.2` | `added` |
| `gradle/libs.versions.toml` | `libraries.ksp2-aaEmbeddable` | `not present` | `com.google.devtools.ksp:symbol-processing-aa-embeddable:2.1.21-2.0.2` | `added` |
| `gradle/libs.versions.toml` | `libraries.ksp2-api` | `not present` | `com.google.devtools.ksp:symbol-processing-api:2.1.21-2.0.2` | `added` |
| `gradle/libs.versions.toml` | `libraries.ksp2-commonDeps` | `not present` | `com.google.devtools.ksp:symbol-processing-common-deps:2.1.21-2.0.2` | `added` |
| `gradle/libs.versions.toml` | `libraries.log4j` | `org.apache.logging.log4j:log4j-core:2.25.4` | `org.apache.logging.log4j:log4j-core:2.25.4` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.logback-classic` | `ch.qos.logback:logback-classic:1.5.32` | `ch.qos.logback:logback-classic:1.5.29` | `changed` |
| `gradle/libs.versions.toml` | `libraries.logbook-netty` | `org.zalando:logbook-netty:3.12.3` | `org.zalando:logbook-netty:3.12.2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.lombok` | `org.projectlombok:lombok:1.18.46` | `org.projectlombok:lombok:1.18.40` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-graalvm-nativeimage` | `org.graalvm.sdk:nativeimage:25.0.3` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.managed-groovy` | `org.apache.groovy:groovy:5.0.6` | `org.apache.groovy:groovy:4.0.28` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-groovy-json` | `org.apache.groovy:groovy-json:5.0.6` | `org.apache.groovy:groovy-json:4.0.28` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-groovy-sql` | `org.apache.groovy:groovy-sql:5.0.6` | `org.apache.groovy:groovy-sql:4.0.28` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-groovy-templates` | `org.apache.groovy:groovy-templates:5.0.6` | `org.apache.groovy:groovy-templates:4.0.28` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-jackson-annotations` | `com.fasterxml.jackson.core:jackson-annotations:2.21` | `com.fasterxml.jackson.core:jackson-annotations:2.21` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-jackson-core` | `tools.jackson.core:jackson-core:3.1.3` | `com.fasterxml.jackson.core:jackson-core:2.21.2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-jackson-databind` | `tools.jackson.core:jackson-databind:3.1.3` | `com.fasterxml.jackson.core:jackson-databind:2.21.2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-jackson-dataformat-xml` | `tools.jackson.dataformat:jackson-dataformat-xml:3.1.3` | `com.fasterxml.jackson.dataformat:jackson-dataformat-xml:2.21.2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-jackson-dataformat-yaml` | `tools.jackson.dataformat:jackson-dataformat-yaml:3.1.3` | `com.fasterxml.jackson.dataformat:jackson-dataformat-yaml:2.21.2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-jackson-datatype-jdk8` | `not present` | `com.fasterxml.jackson.datatype:jackson-datatype-jdk8:2.21.2` | `added` |
| `gradle/libs.versions.toml` | `libraries.managed-jackson-datatype-jsr310` | `not present` | `com.fasterxml.jackson.datatype:jackson-datatype-jsr310:2.21.2` | `added` |
| `gradle/libs.versions.toml` | `libraries.managed-jackson-module-afterburner` | `tools.jackson.module:jackson-module-afterburner:3.1.3` | `com.fasterxml.jackson.module:jackson-module-afterburner:2.21.2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-jackson-module-kotlin` | `tools.jackson.module:jackson-module-kotlin:3.1.3` | `com.fasterxml.jackson.module:jackson-module-kotlin:2.21.2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-jackson-module-parameterNames` | `not present` | `com.fasterxml.jackson.module:jackson-module-parameter-names:2.21.2` | `added` |
| `gradle/libs.versions.toml` | `libraries.managed-jakarta-annotation-api` | `jakarta.annotation:jakarta.annotation-api:2.1.1` | `jakarta.annotation:jakarta.annotation-api:2.1.1` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-java-parser-core` | `com.github.javaparser:javaparser-symbol-solver-core:3.28.0` | `com.github.javaparser:javaparser-symbol-solver-core:3.27.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-jspecify` | `org.jspecify:jspecify:1.0.0` | `org.jspecify:jspecify:1.0.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-kotlin-annotation-processing-embeddable` | `org.jetbrains.kotlin:kotlin-annotation-processing-embeddable:2.3.21` | `org.jetbrains.kotlin:kotlin-annotation-processing-embeddable:1.9.25` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-kotlin-compiler-embeddable` | `org.jetbrains.kotlin:kotlin-compiler-embeddable:2.3.21` | `org.jetbrains.kotlin:kotlin-compiler-embeddable:1.9.25` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-kotlin-reflect` | `org.jetbrains.kotlin:kotlin-reflect:2.3.21` | `org.jetbrains.kotlin:kotlin-reflect:1.9.25` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-kotlin-stdlib` | `org.jetbrains.kotlin:kotlin-stdlib:2.3.21` | `org.jetbrains.kotlin:kotlin-stdlib:1.9.25` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-kotlin-stdlib-jdk8` | `org.jetbrains.kotlin:kotlin-stdlib-jdk8:2.3.21` | `org.jetbrains.kotlin:kotlin-stdlib-jdk8:1.9.25` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-kotlin-test` | `org.jetbrains.kotlin:kotlin-test:2.3.21` | `org.jetbrains.kotlin:kotlin-test:1.9.25` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-kotlinx-coroutines-core` | `org.jetbrains.kotlinx:kotlinx-coroutines-core:1.10.2` | `org.jetbrains.kotlinx:kotlinx-coroutines-core:1.8.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-kotlinx-coroutines-jdk8` | `org.jetbrains.kotlinx:kotlinx-coroutines-jdk8:1.10.2` | `org.jetbrains.kotlinx:kotlinx-coroutines-jdk8:1.8.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-kotlinx-coroutines-reactive` | `org.jetbrains.kotlinx:kotlinx-coroutines-reactive:1.10.2` | `org.jetbrains.kotlinx:kotlinx-coroutines-reactive:1.8.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-kotlinx-coroutines-reactor` | `org.jetbrains.kotlinx:kotlinx-coroutines-reactor:1.10.2` | `org.jetbrains.kotlinx:kotlinx-coroutines-reactor:1.8.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-kotlinx-coroutines-rx2` | `org.jetbrains.kotlinx:kotlinx-coroutines-rx2:1.10.2` | `org.jetbrains.kotlinx:kotlinx-coroutines-rx2:1.8.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-kotlinx-coroutines-slf4j` | `org.jetbrains.kotlinx:kotlinx-coroutines-slf4j:1.10.2` | `org.jetbrains.kotlinx:kotlinx-coroutines-slf4j:1.8.1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-ksp` | `com.google.devtools.ksp:symbol-processing:2.3.6` | `com.google.devtools.ksp:symbol-processing:1.9.25-1.0.20` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-ksp-api` | `com.google.devtools.ksp:symbol-processing-api:2.3.6` | `com.google.devtools.ksp:symbol-processing-api:1.9.25-1.0.20` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-methvin-directoryWatcher` | `io.methvin:directory-watcher:0.19.1` | `io.methvin:directory-watcher:0.19.1` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-buffer` | `io.netty:netty-buffer:4.2.13.Final` | `io.netty:netty-buffer:4.2.13.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-codec-classes-quic` | `io.netty:netty-codec-classes-quic:4.2.13.Final` | `io.netty:netty-codec-classes-quic:4.2.13.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-codec-http` | `io.netty:netty-codec-http:4.2.13.Final` | `io.netty:netty-codec-http:4.2.13.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-codec-http2` | `io.netty:netty-codec-http2:4.2.13.Final` | `io.netty:netty-codec-http2:4.2.13.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-codec-http3` | `io.netty:netty-codec-http3:4.2.13.Final` | `io.netty:netty-codec-http3:4.2.13.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-codec-native-quic` | `io.netty:netty-codec-native-quic:4.2.13.Final` | `io.netty:netty-codec-native-quic:4.2.13.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-common` | `io.netty:netty-common:4.2.13.Final` | `io.netty:netty-common:4.2.13.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-contrib-multipart-core` | `io.netty.contrib:netty-codec-multipart-core:1.0.0.Final` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-contrib-multipart-vintage` | `not present` | `io.netty.contrib:netty-codec-multipart-vintage:1.0.0.Final` | `added` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-handler` | `io.netty:netty-handler:4.2.13.Final` | `io.netty:netty-handler:4.2.13.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-handler-proxy` | `io.netty:netty-handler-proxy:4.2.13.Final` | `io.netty:netty-handler-proxy:4.2.13.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-pkitesting` | `io.netty:netty-pkitesting:4.2.13.Final` | `io.netty:netty-pkitesting:4.2.13.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-tcnative-boringssl-static` | `io.netty:netty-tcnative-boringssl-static:2.0.77.Final` | `io.netty:netty-tcnative-boringssl-static:2.0.75.Final` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-transport-native-epoll` | `io.netty:netty-transport-native-epoll:4.2.13.Final` | `io.netty:netty-transport-native-epoll:4.2.13.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-transport-native-iouring` | `io.netty:netty-transport-native-io_uring:4.2.13.Final` | `io.netty:netty-transport-native-io_uring:4.2.13.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-transport-native-kqueue` | `io.netty:netty-transport-native-kqueue:4.2.13.Final` | `io.netty:netty-transport-native-kqueue:4.2.13.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-transport-native-unix-common` | `io.netty:netty-transport-native-unix-common:4.2.13.Final` | `io.netty:netty-transport-native-unix-common:4.2.13.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-reactive-streams` | `org.reactivestreams:reactive-streams:1.0.4` | `org.reactivestreams:reactive-streams:1.0.4` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-reactor` | `io.projectreactor:reactor-core:3.7.12` | `io.projectreactor:reactor-core:3.7.12` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-reactor-test` | `io.projectreactor:reactor-test:3.7.12` | `io.projectreactor:reactor-test:3.7.12` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-snakeyaml` | `org.yaml:snakeyaml:2.4` | `org.yaml:snakeyaml:2.4` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.micronaut-build-plugins` | `io.micronaut.build.internal:micronaut-gradle-plugins:8.0.0-RC1` | `io.micronaut.build.internal:micronaut-gradle-plugins:7.6.4` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-docs` | `io.micronaut.docs:micronaut-docs-asciidoc-config-props:3.0.0` | `io.micronaut.docs:micronaut-docs-asciidoc-config-props:3.0.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.micronaut-runtime-groovy` | `io.micronaut.groovy:micronaut-runtime-groovy:4.7.0` | `io.micronaut.groovy:micronaut-runtime-groovy:4.7.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.micronaut-session` | `io.micronaut.session:micronaut-session:4.6.0` | `io.micronaut.session:micronaut-session:4.6.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.micronaut-sql-jdbc` | `io.micronaut.sql:micronaut-jdbc:7.0.0-RC1` | `io.micronaut.sql:micronaut-jdbc:5.3.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-sql-jdbc-tomcat` | `io.micronaut.sql:micronaut-jdbc-tomcat:7.0.0-RC1` | `io.micronaut.sql:micronaut-jdbc-tomcat:5.3.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-bom` | `io.micronaut.test:micronaut-test-bom:5.0.0-RC1` | `io.micronaut.test:micronaut-test-bom:4.10.2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-core` | `io.micronaut.test:micronaut-test-core:5.0.0-RC1` | `io.micronaut.test:micronaut-test-core:4.10.2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-junit5` | `io.micronaut.test:micronaut-test-junit5:5.0.0-RC1` | `io.micronaut.test:micronaut-test-junit5:4.10.2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-kotest5` | `io.micronaut.test:micronaut-test-kotest5:5.0.0-RC1` | `io.micronaut.test:micronaut-test-kotest5:4.10.2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-netty-leak` | `io.micronaut.test:micronaut-test-netty-leak:5.0.0-RC1` | `io.micronaut.test:micronaut-test-netty-leak:4.10.2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-spock` | `io.micronaut.test:micronaut-test-spock:5.0.0-RC1` | `io.micronaut.test:micronaut-test-spock:4.10.2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-type-pollution` | `io.micronaut.test:micronaut-test-type-pollution:5.0.0-RC1` | `io.micronaut.test:micronaut-test-type-pollution:4.10.2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.mimepull` | `org.jvnet.mimepull:mimepull:1.10.0` | `org.jvnet.mimepull:mimepull:1.10.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.native-gradle-plugin` | `org.graalvm.buildtools.native:org.graalvm.buildtools.native.gradle.plugin:0.11.4` | `org.graalvm.buildtools.native:org.graalvm.buildtools.native.gradle.plugin:0.11.2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.neo4j-bolt` | `org.neo4j.driver:neo4j-java-driver:5.17.0` | `org.neo4j.driver:neo4j-java-driver:5.17.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.nullaway` | `com.uber.nullaway:nullaway:0.13.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.okio` | `com.squareup.okio:okio:3.9.1` | `com.squareup.okio:okio:3.9.1` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.selenium-api` | `org.seleniumhq.selenium:selenium-api:4.27.0` | `org.seleniumhq.selenium:selenium-api:4.27.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.selenium-driver-chrome` | `org.seleniumhq.selenium:selenium-chrome-driver:4.27.0` | `org.seleniumhq.selenium:selenium-chrome-driver:4.27.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.selenium-driver-firefox` | `org.seleniumhq.selenium:selenium-firefox-driver:4.27.0` | `org.seleniumhq.selenium:selenium-firefox-driver:4.27.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.selenium-driver-htmlunit` | `org.seleniumhq.selenium:htmlunit-driver:4.27.0` | `org.seleniumhq.selenium:htmlunit-driver:4.27.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.selenium-remote-driver` | `org.seleniumhq.selenium:selenium-remote-driver:4.27.0` | `org.seleniumhq.selenium:selenium-remote-driver:4.27.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.selenium-support` | `org.seleniumhq.selenium:selenium-support:4.27.0` | `org.seleniumhq.selenium:selenium-support:4.27.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.slf4j-api` | `org.slf4j:slf4j-api:2.0.17` | `org.slf4j:slf4j-api:2.0.17` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.smallrye` | `io.smallrye:smallrye-fault-tolerance:6.9.2` | `io.smallrye:smallrye-fault-tolerance:6.9.2` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.sonatype-scan` | `org.sonatype.gradle.plugins:scan-gradle-plugin:3.1.5` | `org.sonatype.gradle.plugins:scan-gradle-plugin:3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.spock` | `org.spockframework:spock-core:2.4-groovy-5.0` | `org.spockframework:spock-core:2.3-groovy-4.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.spotbugs` | `com.github.spotbugs:spotbugs-annotations:4.9.8` | `com.github.spotbugs:spotbugs-annotations:4.9.6` | `changed` |
| `gradle/libs.versions.toml` | `libraries.systemlambda` | `com.github.stefanbirkner:system-lambda:1.2.1` | `com.github.stefanbirkner:system-lambda:1.2.1` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.test-boms-micronaut-aws` | `io.micronaut.aws:micronaut-aws-bom:5.0.0-RC1` | `io.micronaut.aws:micronaut-aws-bom:4.11.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.test-boms-micronaut-kotlin` | `io.micronaut.kotlin:micronaut-kotlin-bom:5.0.0-RC1` | `io.micronaut.kotlin:micronaut-kotlin-bom:4.6.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.test-boms-micronaut-reactor` | `io.micronaut.reactor:micronaut-reactor-bom:4.0.0-RC1` | `io.micronaut.reactor:micronaut-reactor-bom:3.7.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.test-boms-micronaut-rxjava2` | `not present` | `io.micronaut.rxjava2:micronaut-rxjava2-bom:2.7.0` | `added` |
| `gradle/libs.versions.toml` | `libraries.test-boms-micronaut-rxjava3` | `io.micronaut.rxjava3:micronaut-rxjava3-bom:4.0.0-RC1` | `io.micronaut.rxjava3:micronaut-rxjava3-bom:3.7.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.test-boms-micronaut-sql` | `io.micronaut.sql:micronaut-sql-bom:7.0.0-RC1` | `io.micronaut.sql:micronaut-sql-bom:5.3.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.test-boms-micronaut-validation` | `io.micronaut.validation:micronaut-validation-bom:5.0.0-RC2` | `io.micronaut.validation:micronaut-validation-bom:4.9.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.testcontainers-spock` | `org.testcontainers:spock:1.21.4` | `org.testcontainers:spock:1.21.3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.tomlj` | `org.tomlj:tomlj:1.1.1` | `org.tomlj:tomlj:1.1.1` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.vertx` | `io.vertx:vertx-core:4.5.26` | `io.vertx:vertx-core:4.5.17` | `changed` |
| `gradle/libs.versions.toml` | `libraries.vertx-webclient` | `io.vertx:vertx-web-client:4.5.26` | `io.vertx:vertx-web-client:4.5.17` | `changed` |
| `gradle/libs.versions.toml` | `libraries.wiremock` | `com.github.tomakehurst:wiremock-jre8:2.33.2` | `com.github.tomakehurst:wiremock-jre8:2.33.2` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.zacsweers-kct-ksp` | `dev.zacsweers.kctfork:ksp:0.12.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.awaitility` | `4.3.0` | `4.3.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.bcpkix` | `1.84` | `1.70` | `changed` |
| `gradle/libs.versions.toml` | `versions.blaze` | `1.6.18` | `1.6.17` | `changed` |
| `gradle/libs.versions.toml` | `versions.brotli4j` | `1.18.0` | `1.18.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.bytebuddy` | `1.18.8` | `1.17.8` | `changed` |
| `gradle/libs.versions.toml` | `versions.caffeine` | `2.9.3` | `2.9.3` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.classgraph` | `4.8.184` | `4.8.181` | `changed` |
| `gradle/libs.versions.toml` | `versions.compile-testing` | `0.21.0` | `0.21.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.error_prone_core` | `2.48.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.errorprone-gradle-plugin` | `4.4.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.geb` | `7.0` | `7.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.graal-svm` | `not present` | `23.1.8` | `added` |
| `gradle/libs.versions.toml` | `versions.h2` | `2.4.240` | `2.2.224` | `changed` |
| `gradle/libs.versions.toml` | `versions.hibernate` | `5.5.9.Final` | `5.5.9.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.htmlsanitycheck` | `1.1.6` | `1.1.6` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.htmlunit` | `2.70.0` | `2.70.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.httpcomponents-client` | `4.5.14` | `4.5.14` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.icu4j` | `76.1` | `76.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.jackson2` | `2.21.3` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.jakarta-el` | `5.0.1` | `5.0.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.jakarta-el-impl` | `5.0.0-M1` | `5.0.0-M1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.jakarta-inject-api` | `2.0.1` | `2.0.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.jakarta-inject-tck` | `2.0.1` | `2.0.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.jakarta-persistence` | `3.2.0` | `3.2.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.japicmp-gradle-plugin` | `0.4.6` | `0.4.6` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.javax-annotation-api` | `1.3.2` | `1.3.2` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.javax-inject` | `1` | `1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.javax-persistence` | `2.2` | `2.2` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.jazzer` | `0.24.0` | `0.24.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.jcache` | `1.1.1` | `1.1.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.jetbrains-annotations` | `23.1.0` | `23.1.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.jetty` | `9.4.58.v20250814` | `9.4.58.v20250814` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.jfrunit` | `1.0.0.Alpha2` | `1.0.0.Alpha2` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.jmh` | `1.37` | `1.37` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.jsr107` | `1.1.1` | `1.1.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.jsr305` | `3.0.2` | `3.0.2` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.junit-platform` | `1.12.2` | `1.12.2` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.junit4` | `4.13.2` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.junit5` | `5.12.2` | `5.12.2` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.log4j` | `2.25.4` | `2.25.4` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.logback` | `1.5.32` | `1.5.29` | `changed` |
| `gradle/libs.versions.toml` | `versions.logbook-netty` | `3.12.3` | `3.12.2` | `changed` |
| `gradle/libs.versions.toml` | `versions.lombok` | `1.18.46` | `1.18.40` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-graal` | `25.0.3` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.managed-groovy` | `5.0.6` | `4.0.28` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-jackson` | `3.1.3` | `2.21.2` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-jackson-annotations` | `2.21` | `2.21` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-jackson-databind` | `not present` | `2.21.2` | `added` |
| `gradle/libs.versions.toml` | `versions.managed-jakarta-annotation-api` | `2.1.1` | `2.1.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-java-parser-core` | `3.28.0` | `3.27.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-jspecify` | `1.0.0` | `1.0.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-kotlin` | `2.3.21` | `1.9.25` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-kotlin-coroutines` | `1.10.2` | `1.8.1` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-kotlin2` | `not present` | `2.1.21` | `added` |
| `gradle/libs.versions.toml` | `versions.managed-ksp` | `2.3.6` | `1.9.25-1.0.20` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-ksp2` | `not present` | `2.1.21-2.0.2` | `added` |
| `gradle/libs.versions.toml` | `versions.managed-methvin-directory-watcher` | `0.19.1` | `0.19.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-netty` | `4.2.13.Final` | `4.2.13.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-netty-contrib-multipart` | `1.0.0.Final` | `1.0.0.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-netty-tcnative` | `2.0.77.Final` | `2.0.75.Final` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-reactive-streams` | `1.0.4` | `1.0.4` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-reactor` | `3.7.12` | `3.7.12` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-snakeyaml` | `2.4` | `2.4` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.micronaut-aws` | `5.0.0-RC1` | `4.11.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-build-plugins` | `8.0.0-RC1` | `7.6.4` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `3.0.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.micronaut-groovy` | `4.7.0` | `4.7.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.micronaut-kotlin` | `5.0.0-RC1` | `4.6.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-reactor` | `4.0.0-RC1` | `3.7.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-rxjava2` | `not present` | `2.7.0` | `added` |
| `gradle/libs.versions.toml` | `versions.micronaut-rxjava3` | `4.0.0-RC1` | `3.7.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-session` | `4.6.0` | `4.6.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.micronaut-sourcegen` | `2.0.0-RC4` | `1.8.2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-sql` | `7.0.0-RC1` | `5.3.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `5.0.0-RC1` | `4.10.2` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `5.0.0-RC2` | `4.9.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.mimepull` | `1.10.0` | `1.10.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.native-gradle-plugin` | `0.11.4` | `0.11.2` | `changed` |
| `gradle/libs.versions.toml` | `versions.neo4j-java-driver` | `5.17.0` | `5.17.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.nullaway` | `0.13.1` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.okio` | `3.9.1` | `3.9.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.selenium` | `4.27.0` | `4.27.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.slf4j` | `2.0.17` | `2.0.17` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.smallrye` | `6.9.2` | `6.9.2` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.sonatype-scan` | `3.1.5` | `3.0.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.4-groovy-5.0` | `2.3-groovy-4.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.spotbugs` | `4.9.8` | `4.9.6` | `changed` |
| `gradle/libs.versions.toml` | `versions.systemlambda` | `1.2.1` | `1.2.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.testcontainers` | `1.21.4` | `1.21.3` | `changed` |
| `gradle/libs.versions.toml` | `versions.tomlj` | `1.1.1` | `1.1.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.vertx` | `4.5.26` | `4.5.17` | `changed` |
| `gradle/libs.versions.toml` | `versions.wiremock` | `2.33.2` | `2.33.2` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.zacsweers-kotlin-compile-testing` | `0.12.1` | `not present` | `removed` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `9.5.0` | `8.14.3` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Fixes

- `8bb0ffd794cf` fix: checkout using github.sha in github_release to avoid tag-moved error (Sergio del Amo, 2026-04-28)

### Security

- `c95ce9454210` security: bouncy castle 1.84 (Sergio del Amo, 2026-04-28)

### Dependency Updates

- `c2b22742d650` chore: Bump version to 4.10.24-SNAPSHOT (micronaut-build, 2026-05-06)
- `d807b54cef14` chore: Bump version to 4.10.23-SNAPSHOT (micronaut-build, 2026-04-28)
- `362275a6beaf` chore: Bump version to 4.10.22-SNAPSHOT (micronaut-build, 2026-04-10)
- `b1e9f1f69d29` Update GraalVM version to 23.1.8 (Sergio del Amo, 2026-04-08)
- `f009b8897987` chore: Bump version to 4.10.21-SNAPSHOT (micronaut-build, 2026-03-31)

### Review Candidates

- `86880d4ede41` [skip ci] Release v4.10.23 (micronaut-build, 2026-05-06)
- `72b40df8a735` Fix full body subscribers on 4.10.x (#12646) (Jonas Konrad, 2026-05-06)
- `e83c259eef26` Update Netty to 4.2.13.Final (#12662) (Jonas Konrad, 2026-05-06)
- `074f5f2acd9a` Fix HTTP server TCK on 4.10.x (#12645) (Jonas Konrad, 2026-05-01)
- `b8c9ecd4f52e` [skip ci] Release v4.10.22 (micronaut-build, 2026-04-28)
- `2e5871098d8b` log4j = "2.25.4" (Sergio del Amo, 2026-04-28)
- `48f05ae8dc41` Merge commit from fork (Sergio del Amo, 2026-04-28)
- `be6789b46812` Merge commit from fork (Sergio del Amo, 2026-04-28)
- `f777bd478115` Fix locale converter throwing IllegalArgumentException for invalid input (#12609) (Asmaa Knidar, 2026-04-20)
- `3a5e6cecd4b9` [skip ci] Release v4.10.21 (micronaut-build, 2026-04-10)
- `ed1dd7813b42` Access log support for %U (#12595) (Nemanja Mikic, 2026-04-06)
- `4c456a166963` [skip ci] Release v4.10.20 (micronaut-build, 2026-03-31)

## Changed Files

### Build and Dependencies

- `D` .agents/skills/gradle/SKILL.md
- `D` .agents/skills/gradle/references/gradle-best-practices.md
- `D` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` aop/build.gradle.kts
- `M` benchmarks/build.gradle.kts
- `M` buffer-netty/build.gradle.kts
- `M` build.gradle
- `M` buildSrc/build.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.convention-base.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.convention-library.gradle
- `D` buildSrc/src/main/groovy/io.micronaut.build.internal.convention-nullaway.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.convention-quality.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.convention-test-library.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.functional-test.gradle
- `M` context-propagation/build.gradle.kts
- `M` context/build.gradle.kts
- `M` core-bom/build.gradle.kts
- `M` core-reactive/build.gradle.kts
- `M` core/build.gradle.kts
- `M` core/src/main/java/io/micronaut/core/convert/ConversionContext.java
- `M` core/src/main/java/io/micronaut/core/convert/ConversionService.java
- `M` core/src/main/java/io/micronaut/core/convert/ConversionServiceAware.java
- `M` core/src/main/java/io/micronaut/core/convert/ConversionServiceProvider.java
- `M` core/src/main/java/io/micronaut/core/convert/DefaultArgumentConversionContext.java
- `M` core/src/main/java/io/micronaut/core/convert/DefaultMutableConversionService.java
- `M` core/src/main/java/io/micronaut/core/convert/MutableConversionService.java
- `M` core/src/main/java/io/micronaut/core/convert/exceptions/ConversionErrorException.java
- `M` core/src/main/java/io/micronaut/core/version/SemanticVersion.java
- `M` core/src/main/java/io/micronaut/core/version/VersionUtils.java
- `D` core/src/main/java/io/micronaut/core/version/annotation/package-info.java
- `M` core/src/main/java/io/micronaut/core/version/package-info.java
- `M` core/src/test/groovy/io/micronaut/core/convert/DefaultConversionServiceSpec.groovy
- `M` discovery-core/build.gradle.kts
- `M` gradle.properties
- `M` gradle/libs.versions.toml
- `M` gradle/wrapper/gradle-wrapper.jar
- `M` gradle/wrapper/gradle-wrapper.properties
- `M` gradlew
- `M` gradlew.bat
- `M` http-client-core/src/main/java/io/micronaut/http/client/HttpVersionSelection.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/bind/binders/VersionClientRequestBinder.java
- `M` http-client-tck/build.gradle.kts
- `M` http-netty/build.gradle.kts
- `M` http-server-netty/build.gradle.kts

### Documentation

- `D` .agents/skills/docs/SKILL.md
- `D` .agents/skills/docs/references/control-panel-patterns.md
- `D` .agents/skills/docs/references/micronaut-docs-providers.md
- `D` .agents/skills/guides/SKILL.md
- `D` .agents/skills/guides/references/guide-authoring-conventions.md
- `D` .agents/skills/guides/references/guide-inventory.md
- `D` .agents/skills/guides/references/pdf-export-and-pr.md
- `D` .agents/skills/guides/references/repository-workflow.md
- `M` .github/workflows/release.yml

### Source

- `D` .agents/skills/agent-md-refactor/SKILL.md
- `D` .agents/skills/agent-md-refactor/references/examples-and-anti-patterns.md
- `D` .agents/skills/agent-md-refactor/references/refactor-playbook.md
- `D` .agents/skills/coding/SKILL.md
- `D` .agents/skills/micronaut-sourcegen/SKILL.md
- `D` .agents/skills/micronaut-sourcegen/references/sourcegen-cookbook.md
- `D` .agents/skills/skill-creator/SKILL.md
- `D` .agents/skills/skill-creator/references/research-synthesis.md
- `D` .agents/skills/skill-creator/references/templates.md
- `M` .clineignore
- `M` .clinerules/coding.md
- `M` .github/instructions/coding.instructions.md
- `M` .github/renovate.json
- `D` .github/scripts/vulnerability-audit-filter.py
- `D` .github/scripts/vulnerability-audit.sh
- `M` .github/workflows/central-sync.yml
- `M` .github/workflows/graalvm-dev.yml
- `M` .github/workflows/publish-snapshot.yml
- `M` .github/workflows/sonatype.yml
- `M` .gitignore
- `D` .sdkmanrc
- `M` MAINTAINING.md
- `M` aop/src/main/java/io/micronaut/aop/Adapter.java
- `M` aop/src/main/java/io/micronaut/aop/ConstructorInterceptor.java
- `M` aop/src/main/java/io/micronaut/aop/ConstructorInvocationContext.java
- `M` aop/src/main/java/io/micronaut/aop/InterceptedMethod.java
- `M` aop/src/main/java/io/micronaut/aop/Interceptor.java
- `M` aop/src/main/java/io/micronaut/aop/InterceptorRegistry.java
- `M` aop/src/main/java/io/micronaut/aop/InvocationContext.java
- `M` aop/src/main/java/io/micronaut/aop/MethodInterceptor.java
- `M` aop/src/main/java/io/micronaut/aop/MethodInvocationContext.java
- `M` aop/src/main/java/io/micronaut/aop/chain/AbstractInterceptorChain.java
- `M` aop/src/main/java/io/micronaut/aop/chain/AdapterIntroduction.java
- `M` aop/src/main/java/io/micronaut/aop/chain/ConstructorInterceptorChain.java
- `M` aop/src/main/java/io/micronaut/aop/chain/DefaultInterceptorRegistry.java
- `M` aop/src/main/java/io/micronaut/aop/chain/InterceptorChain.java
- `M` aop/src/main/java/io/micronaut/aop/chain/MethodInterceptorChain.java
- `M` aop/src/main/java/io/micronaut/aop/chain/package-info.java
- `M` aop/src/main/java/io/micronaut/aop/exceptions/package-info.java
- `M` aop/src/main/java/io/micronaut/aop/internal/InterceptorRegistryBean.java
- `M` aop/src/main/java/io/micronaut/aop/internal/intercepted/CompletionStageInterceptedMethod.java
- `M` aop/src/main/java/io/micronaut/aop/internal/intercepted/InterceptedMethodUtil.java
- `M` aop/src/main/java/io/micronaut/aop/internal/intercepted/KotlinInterceptedMethodImpl.java
- `M` aop/src/main/java/io/micronaut/aop/internal/intercepted/PublisherInterceptedMethod.java
- `M` aop/src/main/java/io/micronaut/aop/internal/intercepted/ReactorInterceptedMethod.java
- `M` aop/src/main/java/io/micronaut/aop/internal/intercepted/SynchronousInterceptedMethod.java
- `M` aop/src/main/java/io/micronaut/aop/kotlin/KotlinInterceptedMethod.java
- `M` aop/src/main/java/io/micronaut/aop/package-info.java
- `D` aop/src/main/java/io/micronaut/aop/runtime/DefaultRuntimeProxyDefinition.java
- `D` aop/src/main/java/io/micronaut/aop/runtime/RuntimeProxy.java
- `D` aop/src/main/java/io/micronaut/aop/runtime/RuntimeProxyCreator.java
- `D` aop/src/main/java/io/micronaut/aop/runtime/RuntimeProxyDefinition.java
- `M` benchmarks/src/jmh/java/io/micronaut/context/env/PropertySourcePropertyResolverBenchmark.java
- `M` benchmarks/src/jmh/java/io/micronaut/http/server/StartupBenchmark.java
- `M` benchmarks/src/jmh/java/io/micronaut/http/server/stack/ControllersBenchmark.java
- `M` benchmarks/src/jmh/java/io/micronaut/http/server/stack/JmhFastThreadLocalExecutor.java
- `M` benchmarks/src/jmh/java/io/micronaut/http/server/stack/RawClientBenchmark.java
- `M` benchmarks/src/jmh/java/io/micronaut/http/server/stack/RequestHandler.java
- `M` buffer-netty/src/main/java/io/micronaut/buffer/netty/ByteBufAllocatorConfiguration.java
- `M` buffer-netty/src/main/java/io/micronaut/buffer/netty/DefaultByteBufAllocatorConfiguration.java
- `M` buffer-netty/src/main/java/io/micronaut/buffer/netty/NettyReadBuffer.java
- `M` buffer-netty/src/main/java/io/micronaut/buffer/netty/NettyReadBufferFactory.java
- `M` buffer-netty/src/main/java/io/micronaut/buffer/netty/package-info.java
- `M` config/accepted-api-changes.json
- `M` config/checkstyle/checkstyle.xml
- `M` context-propagation/src/main/java/io/micronaut/context/propagation/instrument/execution/ContextPropagatingExecutorService.java
- `M` context-propagation/src/main/java/io/micronaut/context/propagation/instrument/execution/ContextPropagatingScheduledExecutorService.java
- `M` context-propagation/src/main/java/io/micronaut/context/propagation/instrument/execution/ExecutorServiceInstrumenter.java
- `D` context-propagation/src/main/java/io/micronaut/context/propagation/instrument/execution/package-info.java
- `M` context-propagation/src/main/java/io/micronaut/context/propagation/slf4j/MdcPropagationContext.java
- `D` context-propagation/src/main/java/io/micronaut/context/propagation/slf4j/package-info.java
- `D` context/src/main/java/io/micronaut/context/propagation/PropagatedContextConfigurationProperties.java
- `M` context/src/main/java/io/micronaut/logging/PropertiesLoggingLevelsConfigurer.java
- `M` context/src/main/java/io/micronaut/logging/impl/Log4jLoggingSystem.java
- `M` context/src/main/java/io/micronaut/logging/impl/LogbackLoggingSystem.java
- `M` context/src/main/java/io/micronaut/logging/impl/LogbackUtils.java
- `D` context/src/main/java/io/micronaut/logging/impl/package-info.java
- `M` context/src/main/java/io/micronaut/runtime/ApplicationConfiguration.java
- `M` context/src/main/java/io/micronaut/runtime/EmbeddedApplication.java
- `M` context/src/main/java/io/micronaut/runtime/Micronaut.java
- `M` context/src/main/java/io/micronaut/runtime/beans/MapperIntroduction.java
- `M` context/src/main/java/io/micronaut/runtime/beans/MapperMethodProcessor.java
- `D` context/src/main/java/io/micronaut/runtime/beans/package-info.java
- `M` context/src/main/java/io/micronaut/runtime/context/CompositeMessageSource.java
- `M` context/src/main/java/io/micronaut/runtime/context/env/ConfigurationIntroductionAdvice.java
- `M` context/src/main/java/io/micronaut/runtime/context/env/package-info.java
- `D` context/src/main/java/io/micronaut/runtime/context/package-info.java
- `M` context/src/main/java/io/micronaut/runtime/context/scope/ThreadLocalCustomScope.java
- `M` context/src/main/java/io/micronaut/runtime/context/scope/package-info.java
- `M` context/src/main/java/io/micronaut/runtime/context/scope/refresh/RefreshEventListener.java
- `M` context/src/main/java/io/micronaut/runtime/context/scope/refresh/RefreshInterceptor.java
- `M` context/src/main/java/io/micronaut/runtime/context/scope/refresh/RefreshScope.java
- `M` context/src/main/java/io/micronaut/runtime/context/scope/refresh/package-info.java
- `M` context/src/main/java/io/micronaut/runtime/converters/time/TimeConverterRegistrar.java
- `M` context/src/main/java/io/micronaut/runtime/converters/time/package-info.java
- `M` context/src/main/java/io/micronaut/runtime/event/annotation/EventListener.java
- `M` context/src/main/java/io/micronaut/runtime/event/annotation/package-info.java
- `M` context/src/main/java/io/micronaut/runtime/event/package-info.java
- `M` context/src/main/java/io/micronaut/runtime/exceptions/package-info.java
- `M` context/src/main/java/io/micronaut/runtime/graceful/GracefulShutdownCapable.java
- `M` context/src/main/java/io/micronaut/runtime/graceful/GracefulShutdownConfiguration.java
- `M` context/src/main/java/io/micronaut/runtime/graceful/GracefulShutdownManager.java
- `D` context/src/main/java/io/micronaut/runtime/graceful/package-info.java
- `M` context/src/main/java/io/micronaut/runtime/package-info.java
- `M` context/src/main/java/io/micronaut/runtime/server/event/package-info.java
- `M` context/src/main/java/io/micronaut/runtime/server/package-info.java
- `D` context/src/main/java/io/micronaut/runtime/server/watch/event/package-info.java
- `M` context/src/main/java/io/micronaut/scheduling/DefaultTaskExceptionHandler.java
- `M` context/src/main/java/io/micronaut/scheduling/LoomSupport.java
- `M` context/src/main/java/io/micronaut/scheduling/NextFireTime.java
- `M` context/src/main/java/io/micronaut/scheduling/ScheduledExecutorTaskScheduler.java
- `M` context/src/main/java/io/micronaut/scheduling/TaskScheduler.java
- `M` context/src/main/java/io/micronaut/scheduling/annotation/package-info.java
- `M` context/src/main/java/io/micronaut/scheduling/async/AsyncInterceptor.java
- `M` context/src/main/java/io/micronaut/scheduling/async/package-info.java
- `M` context/src/main/java/io/micronaut/scheduling/cron/CronExpression.java
- `M` context/src/main/java/io/micronaut/scheduling/cron/package-info.java
- `M` context/src/main/java/io/micronaut/scheduling/exceptions/package-info.java
- `M` context/src/main/java/io/micronaut/scheduling/executor/DefaultExecutorSelector.java
- `M` context/src/main/java/io/micronaut/scheduling/executor/ExecutorConfiguration.java
- `M` context/src/main/java/io/micronaut/scheduling/executor/ExecutorFactory.java
- `M` context/src/main/java/io/micronaut/scheduling/executor/ExecutorSelector.java
- `M` context/src/main/java/io/micronaut/scheduling/executor/GracefulShutdownCapableScheduledThreadPoolExecutor.java
- `D` context/src/main/java/io/micronaut/scheduling/executor/ThreadSelectionConfiguration.java
- `M` context/src/main/java/io/micronaut/scheduling/executor/UserExecutorConfiguration.java
- `M` context/src/main/java/io/micronaut/scheduling/executor/package-info.java
- `M` context/src/main/java/io/micronaut/scheduling/instrument/InstrumentedExecutor.java
- `M` context/src/main/java/io/micronaut/scheduling/instrument/InstrumentedExecutorService.java
- `M` context/src/main/java/io/micronaut/scheduling/instrument/InstrumentedScheduledExecutorService.java
- `M` context/src/main/java/io/micronaut/scheduling/instrument/package-info.java
- `M` context/src/main/java/io/micronaut/scheduling/io/watch/DefaultWatchThread.java
- `M` context/src/main/java/io/micronaut/scheduling/io/watch/FileWatchConfiguration.java
- `M` context/src/main/java/io/micronaut/scheduling/io/watch/WatchServiceFactory.java
- `M` context/src/main/java/io/micronaut/scheduling/io/watch/event/FileChangedEvent.java
- `M` context/src/main/java/io/micronaut/scheduling/io/watch/event/package-info.java
- `M` context/src/main/java/io/micronaut/scheduling/io/watch/package-info.java
- `M` context/src/main/java/io/micronaut/scheduling/package-info.java
- `M` context/src/main/java/io/micronaut/scheduling/processor/ScheduledMethodProcessor.java
- `M` context/src/main/java/io/micronaut/scheduling/processor/package-info.java
- `M` core-processor/src/main/java/io/micronaut/aop/writer/AopProxyWriter.java
- `D` core-processor/src/main/java/io/micronaut/aop/writer/ProxyingBeanDefinitionWriter.java
- `D` core-processor/src/main/java/io/micronaut/aop/writer/RuntimeProxyBeanDefinitionWriter.java
- `M` core-processor/src/main/java/io/micronaut/aop/writer/package-info.java
- `M` core-processor/src/main/java/io/micronaut/context/visitor/BeanImportHandler.java
- `M` core-processor/src/main/java/io/micronaut/context/visitor/BeanImportVisitor.java
- `M` core-processor/src/main/java/io/micronaut/context/visitor/ConfigurationMetadataWriterVisitor.java
- `M` core-processor/src/main/java/io/micronaut/context/visitor/ConfigurationReaderVisitor.java
- `M` core-processor/src/main/java/io/micronaut/context/visitor/ContextConfigurerVisitor.java
- `M` core-processor/src/main/java/io/micronaut/context/visitor/ExecutableVisitor.java
- `M` core-processor/src/main/java/io/micronaut/context/visitor/InternalApiTypeElementVisitor.java
- `M` core-processor/src/main/java/io/micronaut/context/visitor/PackageConfigurationImportVisitor.java
- `M` core-processor/src/main/java/io/micronaut/context/visitor/VisitorUtils.java
- `M` core-processor/src/main/java/io/micronaut/context/visitor/package-info.java
- `M` core-processor/src/main/java/io/micronaut/expressions/EvaluatedExpressionWriter.java
- `M` core-processor/src/main/java/io/micronaut/expressions/context/DefaultExpressionCompilationContextFactory.java
- `M` core-processor/src/main/java/io/micronaut/expressions/context/DefaultExpressionEvaluationContext.java
- `M` core-processor/src/main/java/io/micronaut/expressions/context/ExpressionCompilationContextFactory.java
- `M` core-processor/src/main/java/io/micronaut/expressions/context/ExpressionEvaluationContext.java
- `M` core-processor/src/main/java/io/micronaut/expressions/context/ExpressionEvaluationContextRegistrar.java
- `M` core-processor/src/main/java/io/micronaut/expressions/context/ExpressionWithContext.java
- `M` core-processor/src/main/java/io/micronaut/expressions/context/ExtensibleExpressionEvaluationContext.java
- `D` core-processor/src/main/java/io/micronaut/expressions/context/package-info.java
- `D` core-processor/src/main/java/io/micronaut/expressions/package-info.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/CompoundEvaluatedExpressionParser.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/EvaluatedExpressionParser.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/SingleEvaluatedExpressionParser.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/ExpressionNode.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/access/AbstractMethodCall.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/access/BeanContextAccess.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/access/CandidateMethod.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/access/ContextElementAccess.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/access/ContextMethodParameterAccess.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/access/EnvironmentAccess.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/access/SubscriptOperator.java
- `D` core-processor/src/main/java/io/micronaut/expressions/parser/ast/access/package-info.java
- `D` core-processor/src/main/java/io/micronaut/expressions/parser/ast/collection/package-info.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/conditional/TernaryExpression.java
- `D` core-processor/src/main/java/io/micronaut/expressions/parser/ast/conditional/package-info.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/literal/BoolLiteral.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/literal/DoubleLiteral.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/literal/FloatLiteral.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/literal/IntLiteral.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/literal/LongLiteral.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/literal/NullLiteral.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/literal/StringLiteral.java
- `D` core-processor/src/main/java/io/micronaut/expressions/parser/ast/literal/package-info.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/operator/binary/BinaryOperator.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/operator/binary/ComparablesComparisonOperation.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/operator/binary/InstanceofOperator.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/operator/binary/MatchesOperator.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/operator/binary/NumericComparisonOperation.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/operator/binary/RelationalOperator.java
- `D` core-processor/src/main/java/io/micronaut/expressions/parser/ast/operator/binary/package-info.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/operator/unary/EmptyOperator.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/operator/unary/NegOperator.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/operator/unary/NotOperator.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/operator/unary/PosOperator.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/operator/unary/UnaryOperator.java
- `D` core-processor/src/main/java/io/micronaut/expressions/parser/ast/operator/unary/package-info.java
- `D` core-processor/src/main/java/io/micronaut/expressions/parser/ast/package-info.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/types/TypeIdentifier.java
- `D` core-processor/src/main/java/io/micronaut/expressions/parser/ast/types/package-info.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/util/EvaluatedExpressionCompilationUtils.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/util/TypeDescriptors.java
- `D` core-processor/src/main/java/io/micronaut/expressions/parser/ast/util/package-info.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/compilation/ExpressionCompilationContext.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/compilation/ExpressionVisitorContext.java
- `D` core-processor/src/main/java/io/micronaut/expressions/parser/compilation/package-info.java
- `D` core-processor/src/main/java/io/micronaut/expressions/parser/exception/package-info.java
- `D` core-processor/src/main/java/io/micronaut/expressions/parser/package-info.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/token/Tokenizer.java
- `D` core-processor/src/main/java/io/micronaut/expressions/parser/token/package-info.java
- `D` core-processor/src/main/java/io/micronaut/expressions/util/package-info.java
- `M` core-processor/src/main/java/io/micronaut/inject/annotation/AbstractAnnotationMetadataBuilder.java
- `M` core-processor/src/main/java/io/micronaut/inject/annotation/AnnotationMetadataGenUtils.java
- `M` core-processor/src/main/java/io/micronaut/inject/annotation/AnnotationMetadataWriter.java
- `M` core-processor/src/main/java/io/micronaut/inject/annotation/AnnotationRemapper.java
- `M` core-processor/src/main/java/io/micronaut/inject/annotation/PackageRenameRemapper.java
- `M` core-processor/src/main/java/io/micronaut/inject/annotation/internal/AndroidxNullableTransformer.java
- `M` core-processor/src/main/java/io/micronaut/inject/annotation/internal/FindBugsRemapper.java
- `D` core-processor/src/main/java/io/micronaut/inject/annotation/internal/JakartaPriorityAnnotationMapper.java
- `M` core-processor/src/main/java/io/micronaut/inject/annotation/internal/JavaxNonnullTransformer.java
- `M` core-processor/src/main/java/io/micronaut/inject/annotation/internal/JavaxNullableTransformer.java
- `M` core-processor/src/main/java/io/micronaut/inject/annotation/internal/JavaxPostConstructTransformer.java
- `M` core-processor/src/main/java/io/micronaut/inject/annotation/internal/JavaxPreDestroyTransformer.java
- `M` core-processor/src/main/java/io/micronaut/inject/annotation/internal/JavaxRemapper.java
- `M` core-processor/src/main/java/io/micronaut/inject/annotation/internal/JdtNullableTransformer.java
- `M` core-processor/src/main/java/io/micronaut/inject/annotation/internal/KotlinNotNullMapper.java
- `M` core-processor/src/main/java/io/micronaut/inject/annotation/internal/KotlinNullableMapper.java
- `M` core-processor/src/main/java/io/micronaut/inject/annotation/internal/ReactivexNullableTransformer.java
- `M` core-processor/src/main/java/io/micronaut/inject/annotation/internal/ReactorNullableTransformer.java
- `M` core-processor/src/main/java/io/micronaut/inject/annotation/internal/Rxjava3NullableTransformer.java
- `M` core-processor/src/main/java/io/micronaut/inject/annotation/internal/SpotbugsNullableTransformer.java
- `M` core-processor/src/main/java/io/micronaut/inject/annotation/internal/package-info.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/ClassElement.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/ConstructorElement.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/DefaultElementQuery.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/Element.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/ElementFactory.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/ElementQuery.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/FieldElement.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/GenericElement.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/GenericPlaceholderElement.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/MemberElement.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/MethodElement.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/PackageElement.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/ParameterElement.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/PrimitiveElement.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/PropertyElement.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/PropertyElementQuery.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/ReflectClassElement.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/ReflectGenericPlaceholderElement.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/ReflectParameterElement.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/ReflectTypeElement.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/ReflectWildcardElement.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/SimpleClassElement.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/TypedElement.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/WildcardElement.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/annotation/AbstractAnnotationElement.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/annotation/AbstractElementAnnotationMetadataFactory.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/annotation/AbstractMutableAnnotationMetadata.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/annotation/ElementAnnotationMetadataFactory.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/annotation/ElementMutableAnnotationMetadataDelegate.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/annotation/GenericPlaceholderElementAnnotationMetadata.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/annotation/MethodElementAnnotationMetadata.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/annotation/MethodElementAnnotationsHelper.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/annotation/MutableAnnotationMetadataDelegate.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/annotation/MutatedMethodElementAnnotationMetadata.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/annotation/PropertyElementAnnotationMetadata.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/annotation/WildcardElementAnnotationMetadata.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/annotation/package-info.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/beans/BeanConstructorElement.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/beans/BeanElement.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/beans/BeanElementBuilder.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/beans/BeanFieldElement.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/beans/BeanMethodElement.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/beans/BeanParameterElement.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/beans/ConfigurableElement.java
- `D` core-processor/src/main/java/io/micronaut/inject/ast/beans/package-info.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/package-info.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/utils/AstBeanPropertiesUtils.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/utils/EnclosedElementsQuery.java
- `D` core-processor/src/main/java/io/micronaut/inject/ast/utils/package-info.java
- `M` core-processor/src/main/java/io/micronaut/inject/beans/visitor/EntityReflectiveAccessAnnotationMapper.java
- `M` core-processor/src/main/java/io/micronaut/inject/beans/visitor/JsonCreatorAnnotationMapper.java
- `M` core-processor/src/main/java/io/micronaut/inject/beans/visitor/MapperAnnotationMapper.java
- `M` core-processor/src/main/java/io/micronaut/inject/beans/visitor/MapperVisitor.java
- `M` core-processor/src/main/java/io/micronaut/inject/beans/visitor/package-info.java
- `D` core-processor/src/main/java/io/micronaut/inject/beans/visitor/persistence/package-info.java
- `M` core-processor/src/main/java/io/micronaut/inject/configuration/ConfigurationMetadata.java
- `M` core-processor/src/main/java/io/micronaut/inject/configuration/ConfigurationMetadataBuilder.java
- `M` core-processor/src/main/java/io/micronaut/inject/configuration/ConfigurationUtils.java
- `D` core-processor/src/main/java/io/micronaut/inject/configuration/JsonSchemaConfigurationMetadataWriter.java
- `M` core-processor/src/main/java/io/micronaut/inject/configuration/PropertyMetadata.java
- `M` core-processor/src/main/java/io/micronaut/inject/configuration/builder/ConfigurationBuilderPropertyDefinition.java
- `D` core-processor/src/main/java/io/micronaut/inject/configuration/builder/package-info.java
- `M` core-processor/src/main/java/io/micronaut/inject/configuration/package-info.java
- `M` core-processor/src/main/java/io/micronaut/inject/processing/AbstractBeanElementCreator.java
- `M` core-processor/src/main/java/io/micronaut/inject/processing/AopIntroductionProxySupportedBeanElementCreator.java
- `M` core-processor/src/main/java/io/micronaut/inject/processing/BeanDefinitionCreatorFactory.java
- `M` core-processor/src/main/java/io/micronaut/inject/processing/DeclaredBeanElementCreator.java
- `M` core-processor/src/main/java/io/micronaut/inject/processing/FactoryBeanElementCreator.java
- `M` core-processor/src/main/java/io/micronaut/inject/processing/IntroductionInterfaceBeanElementCreator.java
- `M` core-processor/src/main/java/io/micronaut/inject/processing/JavaModelUtils.java
- `M` core-processor/src/main/java/io/micronaut/inject/processing/ProcessingException.java
- `M` core-processor/src/main/java/io/micronaut/inject/processing/package-info.java
- `M` core-processor/src/main/java/io/micronaut/inject/utils/NativeElementsHelper.java
- `D` core-processor/src/main/java/io/micronaut/inject/utils/package-info.java
- `M` core-processor/src/main/java/io/micronaut/inject/visitor/BeanElementVisitor.java
- `M` core-processor/src/main/java/io/micronaut/inject/visitor/BeanElementVisitorLoader.java
- `M` core-processor/src/main/java/io/micronaut/inject/visitor/ElementPostponedToNextRoundException.java
- `M` core-processor/src/main/java/io/micronaut/inject/visitor/PackageElementVisitor.java
- `M` core-processor/src/main/java/io/micronaut/inject/visitor/TypeElementVisitor.java
- `M` core-processor/src/main/java/io/micronaut/inject/visitor/VisitorContext.java
- `M` core-processor/src/main/java/io/micronaut/inject/visitor/package-info.java
- `D` core-processor/src/main/java/io/micronaut/inject/visitor/util/package-info.java
- `M` core-processor/src/main/java/io/micronaut/inject/writer/AbstractBeanDefinitionBuilder.java
- `M` core-processor/src/main/java/io/micronaut/inject/writer/AbstractClassWriterOutputVisitor.java
- `M` core-processor/src/main/java/io/micronaut/inject/writer/ArgumentExpUtils.java
- `M` core-processor/src/main/java/io/micronaut/inject/writer/BeanClassWriter.java
- `M` core-processor/src/main/java/io/micronaut/inject/writer/BeanConfigurationWriter.java
- `M` core-processor/src/main/java/io/micronaut/inject/writer/BeanDefinitionVisitor.java
- `M` core-processor/src/main/java/io/micronaut/inject/writer/BeanDefinitionWriter.java
- `M` core-processor/src/main/java/io/micronaut/inject/writer/ByteCodeWriterUtils.java
- `M` core-processor/src/main/java/io/micronaut/inject/writer/ClassWriterOutputVisitor.java
- `M` core-processor/src/main/java/io/micronaut/inject/writer/DefaultOriginatingElements.java
- `M` core-processor/src/main/java/io/micronaut/inject/writer/DirectoryClassWriterOutputVisitor.java
- `M` core-processor/src/main/java/io/micronaut/inject/writer/DispatchWriter.java
- `M` core-processor/src/main/java/io/micronaut/inject/writer/EvaluatedExpressionProcessor.java
- `M` core-processor/src/main/java/io/micronaut/inject/writer/ExecutableMethodsDefinitionWriter.java
- `M` core-processor/src/main/java/io/micronaut/inject/writer/FileBackedGeneratedFile.java
- `M` core-processor/src/main/java/io/micronaut/inject/writer/GenUtils.java
- `M` core-processor/src/main/java/io/micronaut/inject/writer/MethodGenUtils.java
- `M` core-processor/src/main/java/io/micronaut/inject/writer/OriginatingElements.java
- `M` core-processor/src/main/java/io/micronaut/inject/writer/ProxyingBeanDefinitionVisitor.java
- `M` core-processor/src/main/java/io/micronaut/inject/writer/StaticOriginatingElements.java
- `M` core-processor/src/main/java/io/micronaut/inject/writer/package-info.java
- `M` core-processor/src/main/java/io/micronaut/validation/visitor/async/AsyncTypeElementVisitor.java
- `D` core-processor/src/main/java/io/micronaut/validation/visitor/async/package-info.java
- `M` core-processor/src/main/java/io/micronaut/validation/visitor/package-info.java
- `M` core-processor/src/main/resources/META-INF/services/io.micronaut.inject.annotation.AnnotationMapper
- `M` core-processor/src/main/resources/META-INF/services/io.micronaut.inject.configuration.ConfigurationMetadataWriter
- `M` core-reactive/src/main/java/io/micronaut/core/async/ReactiveStreamsTypeInformationProvider.java
- `M` core-reactive/src/main/java/io/micronaut/core/async/package-info.java
- `M` core-reactive/src/main/java/io/micronaut/core/async/processor/SingleSubscriberProcessor.java
- `M` core-reactive/src/main/java/io/micronaut/core/async/processor/package-info.java
- `M` core-reactive/src/main/java/io/micronaut/core/async/propagation/ReactivePropagation.java
- `M` core-reactive/src/main/java/io/micronaut/core/async/propagation/ReactorPropagation.java
- `D` core-reactive/src/main/java/io/micronaut/core/async/propagation/package-info.java
- `M` core-reactive/src/main/java/io/micronaut/core/async/publisher/AsyncSingleResultPublisher.java
- `M` core-reactive/src/main/java/io/micronaut/core/async/publisher/CompletableFuturePublisher.java
- `M` core-reactive/src/main/java/io/micronaut/core/async/publisher/DelayedSubscriber.java
- `M` core-reactive/src/main/java/io/micronaut/core/async/publisher/Publishers.java
- `M` core-reactive/src/main/java/io/micronaut/core/async/publisher/package-info.java
- `M` core-reactive/src/main/java/io/micronaut/core/async/subscriber/CompletionAwareSubscriber.java
- `M` core-reactive/src/main/java/io/micronaut/core/async/subscriber/LazySendingSubscriber.java
- `M` core-reactive/src/main/java/io/micronaut/core/async/subscriber/SingleThreadedBufferingSubscriber.java
- `M` core-reactive/src/main/java/io/micronaut/core/async/subscriber/package-info.java
- `M` core-reactive/src/main/kotlin/io/micronaut/core/async/propagation/KotlinCoroutinePropagation.kt
- `M` core/src/main/java/io/micronaut/core/annotation/AnnotationClassValue.java
- `M` core/src/main/java/io/micronaut/core/annotation/AnnotationDefaultValuesProvider.java
- `M` core/src/main/java/io/micronaut/core/annotation/AnnotationMetadata.java
- `M` core/src/main/java/io/micronaut/core/annotation/AnnotationMetadataDelegate.java
- `M` core/src/main/java/io/micronaut/core/annotation/AnnotationMetadataProvider.java
- `M` core/src/main/java/io/micronaut/core/annotation/AnnotationMetadataResolver.java
- `M` core/src/main/java/io/micronaut/core/annotation/AnnotationSource.java
- `M` core/src/main/java/io/micronaut/core/annotation/AnnotationUtil.java
- `M` core/src/main/java/io/micronaut/core/annotation/AnnotationValue.java
- `M` core/src/main/java/io/micronaut/core/annotation/AnnotationValueBuilder.java
- `M` core/src/main/java/io/micronaut/core/annotation/AnnotationValueProvider.java
- `M` core/src/main/java/io/micronaut/core/annotation/AnnotationValueResolver.java
- `M` core/src/main/java/io/micronaut/core/annotation/EmptyAnnotationMetadata.java
- `M` core/src/main/java/io/micronaut/core/annotation/ImmutableSortedStringsArrayMap.java
- `M` core/src/main/java/io/micronaut/core/annotation/Indexed.java
- `M` core/src/main/java/io/micronaut/core/annotation/Indexes.java
- `M` core/src/main/java/io/micronaut/core/annotation/Internal.java
- `M` core/src/main/java/io/micronaut/core/annotation/NonNull.java
- `M` core/src/main/java/io/micronaut/core/annotation/package-info.java
- `M` core/src/main/java/io/micronaut/core/attr/AttributeHolder.java
- `M` core/src/main/java/io/micronaut/core/attr/MutableAttributeHolder.java
- `M` core/src/main/java/io/micronaut/core/attr/package-info.java
- `M` core/src/main/java/io/micronaut/core/beans/AbstractBeanConstructor.java
- `M` core/src/main/java/io/micronaut/core/beans/AbstractBeanMethod.java
- `M` core/src/main/java/io/micronaut/core/beans/AbstractBeanProperty.java
- `M` core/src/main/java/io/micronaut/core/beans/BeanConstructor.java
- `M` core/src/main/java/io/micronaut/core/beans/BeanInfo.java
- `M` core/src/main/java/io/micronaut/core/beans/BeanMap.java
- `M` core/src/main/java/io/micronaut/core/beans/BeanMethod.java
- `M` core/src/main/java/io/micronaut/core/beans/BeanProperty.java
- `M` core/src/main/java/io/micronaut/core/beans/BeanReadProperty.java
- `M` core/src/main/java/io/micronaut/core/beans/BeanWrapper.java
- `M` core/src/main/java/io/micronaut/core/beans/BeanWriteProperty.java
- `M` core/src/main/java/io/micronaut/core/beans/DefaultBeanWrapper.java
- `M` core/src/main/java/io/micronaut/core/beans/UnsafeBeanProperty.java
- `M` core/src/main/java/io/micronaut/core/beans/UnsafeBeanReadProperty.java
- `M` core/src/main/java/io/micronaut/core/beans/UnsafeBeanWriteProperty.java
- `D` core/src/main/java/io/micronaut/core/beans/exceptions/package-info.java
- `M` core/src/main/java/io/micronaut/core/beans/package-info.java
- `M` core/src/main/java/io/micronaut/core/bind/ArgumentBinder.java
- `M` core/src/main/java/io/micronaut/core/bind/BeanPropertyBinder.java
- `M` core/src/main/java/io/micronaut/core/bind/BoundExecutable.java
- `M` core/src/main/java/io/micronaut/core/bind/DefaultExecutableBinder.java
- `M` core/src/main/java/io/micronaut/core/bind/MappedBindingResult.java
- `M` core/src/main/java/io/micronaut/core/bind/annotation/AbstractArgumentBinder.java
- `M` core/src/main/java/io/micronaut/core/bind/annotation/Bindable.java
- `M` core/src/main/java/io/micronaut/core/bind/annotation/package-info.java
- `M` core/src/main/java/io/micronaut/core/bind/exceptions/UnsatisfiedArgumentException.java
- `M` core/src/main/java/io/micronaut/core/bind/exceptions/package-info.java
- `M` core/src/main/java/io/micronaut/core/bind/package-info.java
- `M` core/src/main/java/io/micronaut/core/cli/CommandLine.java
- `M` core/src/main/java/io/micronaut/core/cli/CommandLineParser.java
- `M` core/src/main/java/io/micronaut/core/cli/DefaultCommandLine.java
- `M` core/src/main/java/io/micronaut/core/cli/Option.java
- `M` core/src/main/java/io/micronaut/core/cli/exceptions/package-info.java
- `M` core/src/main/java/io/micronaut/core/cli/package-info.java
- `M` core/src/main/java/io/micronaut/core/convert/converters/MultiValuesConverterFactory.java
- `D` core/src/main/java/io/micronaut/core/convert/converters/package-info.java
- `M` core/src/main/java/io/micronaut/core/convert/exceptions/package-info.java
- `M` core/src/main/java/io/micronaut/core/convert/format/package-info.java
- `M` core/src/main/java/io/micronaut/core/convert/package-info.java
- `M` core/src/main/java/io/micronaut/core/convert/value/ConvertibleMultiValues.java
- `M` core/src/main/java/io/micronaut/core/convert/value/ConvertibleMultiValuesMap.java
- `M` core/src/main/java/io/micronaut/core/convert/value/ConvertibleValues.java
- `M` core/src/main/java/io/micronaut/core/convert/value/ConvertibleValuesMap.java
- `M` core/src/main/java/io/micronaut/core/convert/value/MutableConvertibleMultiValuesMap.java
- `M` core/src/main/java/io/micronaut/core/convert/value/MutableConvertibleValues.java
- `M` core/src/main/java/io/micronaut/core/convert/value/MutableConvertibleValuesMap.java
- `M` core/src/main/java/io/micronaut/core/convert/value/package-info.java
- `M` core/src/main/java/io/micronaut/core/exceptions/BeanExceptionHandler.java
- `M` core/src/main/java/io/micronaut/core/exceptions/package-info.java
- `M` core/src/main/java/io/micronaut/core/execution/CompletableFutureExecutionFlow.java
- `M` core/src/main/java/io/micronaut/core/execution/CompletableFutureExecutionFlowImpl.java
- `D` core/src/main/java/io/micronaut/core/execution/ConditionalExecutionExecutor.java
- `M` core/src/main/java/io/micronaut/core/execution/DelayedExecutionFlow.java
- `M` core/src/main/java/io/micronaut/core/execution/DelayedExecutionFlowImpl.java
- `M` core/src/main/java/io/micronaut/core/execution/ExecutionFlow.java
- `D` core/src/main/java/io/micronaut/core/execution/ImmediateExecutor.java
- `M` core/src/main/java/io/micronaut/core/execution/ImperativeExecutionFlow.java
- `M` core/src/main/java/io/micronaut/core/execution/ImperativeExecutionFlowImpl.java
- `D` core/src/main/java/io/micronaut/core/execution/package-info.java
- `M` core/src/main/java/io/micronaut/core/expressions/EvaluatedExpressionReference.java
- `M` core/src/main/java/io/micronaut/core/expressions/ExpressionEvaluationContext.java
- `D` core/src/main/java/io/micronaut/core/expressions/package-info.java
- `M` core/src/main/java/io/micronaut/core/graal/GraalReflectionConfigurer.java
- `M` core/src/main/java/io/micronaut/core/io/FileReadable.java
- `M` core/src/main/java/io/micronaut/core/io/IOUtils.java
- `M` core/src/main/java/io/micronaut/core/io/Readable.java
- `D` core/src/main/java/io/micronaut/core/io/ResourceConflictException.java
- `D` core/src/main/java/io/micronaut/core/io/ResourceDuplicateException.java
- `D` core/src/main/java/io/micronaut/core/io/ResourceLoadStrategy.java
- `D` core/src/main/java/io/micronaut/core/io/ResourceLoadStrategyType.java
- `M` core/src/main/java/io/micronaut/core/io/ResourceLoader.java
- `M` core/src/main/java/io/micronaut/core/io/ResourceResolver.java
- `M` core/src/main/java/io/micronaut/core/io/Streamable.java
- `M` core/src/main/java/io/micronaut/core/io/UrlReadable.java
- `M` core/src/main/java/io/micronaut/core/io/Writable.java
- `D` core/src/main/java/io/micronaut/core/io/buffer/LeakTracker.java
- `M` core/src/main/java/io/micronaut/core/io/buffer/NioReadBuffer.java
- `M` core/src/main/java/io/micronaut/core/io/buffer/ReadBuffer.java
- `M` core/src/main/java/io/micronaut/core/io/buffer/ReadBufferFactory.java
- `M` core/src/main/java/io/micronaut/core/io/buffer/package-info.java
- `M` core/src/main/java/io/micronaut/core/io/file/DefaultFileSystemResourceLoader.java
- `D` core/src/main/java/io/micronaut/core/io/file/TemporaryFileResource.java
- `M` core/src/main/java/io/micronaut/core/io/file/package-info.java
- `M` core/src/main/java/io/micronaut/core/io/package-info.java
- `M` core/src/main/java/io/micronaut/core/io/scan/AnnotationScanner.java
- `D` core/src/main/java/io/micronaut/core/io/scan/ClassClassPathResourceLoader.java
- `D` core/src/main/java/io/micronaut/core/io/scan/ClassLoaderClassPathResourceLoader.java
- `M` core/src/main/java/io/micronaut/core/io/scan/ClassPathResourceLoader.java
- `D` core/src/main/java/io/micronaut/core/io/scan/CombinedClassPathResourceLoader.java
- `M` core/src/main/java/io/micronaut/core/io/scan/DefaultClassPathResourceLoader.java
- `M` core/src/main/java/io/micronaut/core/io/scan/package-info.java
- `M` core/src/main/java/io/micronaut/core/io/service/DefaultServiceDefinition.java
- `M` core/src/main/java/io/micronaut/core/io/service/MicronautMetaServiceLoaderUtils.java
- `M` core/src/main/java/io/micronaut/core/io/service/ServiceLoaderFeature.java
- `M` core/src/main/java/io/micronaut/core/io/service/ServiceScanner.java
- `M` core/src/main/java/io/micronaut/core/io/service/SoftServiceLoader.java
- `M` core/src/main/java/io/micronaut/core/io/service/package-info.java
- `M` core/src/main/java/io/micronaut/core/io/socket/package-info.java
- `D` core/src/main/java/io/micronaut/core/io/value/package-info.java
- `M` core/src/main/java/io/micronaut/core/naming/Described.java
- `M` core/src/main/java/io/micronaut/core/naming/NameUtils.java
- `M` core/src/main/java/io/micronaut/core/naming/Named.java
- `M` core/src/main/java/io/micronaut/core/naming/conventions/package-info.java
- `M` core/src/main/java/io/micronaut/core/naming/package-info.java
- `M` core/src/main/java/io/micronaut/core/optim/StaticOptimizations.java
- `D` core/src/main/java/io/micronaut/core/optim/package-info.java
- `M` core/src/main/java/io/micronaut/core/order/OrderUtil.java
- `M` core/src/main/java/io/micronaut/core/order/package-info.java
- `M` core/src/main/java/io/micronaut/core/propagation/MutablePropagatedContext.java
- `M` core/src/main/java/io/micronaut/core/propagation/PropagatedContext.java
- `D` core/src/main/java/io/micronaut/core/propagation/PropagatedContextConfiguration.java
- `M` core/src/main/java/io/micronaut/core/propagation/PropagatedContextImpl.java
- `D` core/src/main/java/io/micronaut/core/propagation/ScopedValuePropagatedContextElement.java
- `D` core/src/main/java/io/micronaut/core/propagation/ScopedValues.java
- `M` core/src/main/java/io/micronaut/core/propagation/ThreadContext.java
- `M` core/src/main/java/io/micronaut/core/propagation/ThreadPropagatedContextElement.java
- `D` core/src/main/java/io/micronaut/core/propagation/package-info.java
- `M` core/src/main/java/io/micronaut/core/reflect/ClassUtils.java
- `M` core/src/main/java/io/micronaut/core/reflect/InstantiationUtils.java
- `M` core/src/main/java/io/micronaut/core/reflect/ReflectionUtils.java
- `M` core/src/main/java/io/micronaut/core/reflect/exception/package-info.java
- `M` core/src/main/java/io/micronaut/core/reflect/package-info.java
- `M` core/src/main/java/io/micronaut/core/serialize/JdkSerializer.java
- `M` core/src/main/java/io/micronaut/core/serialize/ObjectSerializer.java
- `M` core/src/main/java/io/micronaut/core/serialize/exceptions/package-info.java
- `M` core/src/main/java/io/micronaut/core/serialize/package-info.java
- `M` core/src/main/java/io/micronaut/core/type/Argument.java
- `M` core/src/main/java/io/micronaut/core/type/ArgumentCoercible.java
- `M` core/src/main/java/io/micronaut/core/type/ArgumentValue.java
- `M` core/src/main/java/io/micronaut/core/type/DefaultArgument.java
- `M` core/src/main/java/io/micronaut/core/type/DefaultArgumentValue.java
- `M` core/src/main/java/io/micronaut/core/type/DefaultGenericPlaceholder.java
- `M` core/src/main/java/io/micronaut/core/type/DefaultMutableArgumentValue.java
- `M` core/src/main/java/io/micronaut/core/type/Executable.java
- `M` core/src/main/java/io/micronaut/core/type/GenericPlaceholder.java
- `M` core/src/main/java/io/micronaut/core/type/MutableArgumentValue.java
- `M` core/src/main/java/io/micronaut/core/type/MutableHeaders.java
- `M` core/src/main/java/io/micronaut/core/type/ReturnType.java
- `M` core/src/main/java/io/micronaut/core/type/RuntimeTypeInformation.java
- `M` core/src/main/java/io/micronaut/core/type/TypeInformation.java
- `M` core/src/main/java/io/micronaut/core/type/TypeInformationProvider.java
- `M` core/src/main/java/io/micronaut/core/type/TypeVariableResolver.java
- `M` core/src/main/java/io/micronaut/core/type/UnsafeExecutable.java
- `M` core/src/main/java/io/micronaut/core/type/package-info.java
- `M` core/src/main/java/io/micronaut/core/util/AnsiColour.java
- `M` core/src/main/java/io/micronaut/core/util/ArgumentUtils.java
- `M` core/src/main/java/io/micronaut/core/util/ArrayUtils.java
- `M` core/src/main/java/io/micronaut/core/util/CollectionUtils.java
- `D` core/src/main/java/io/micronaut/core/util/ConnectionString.java
- `M` core/src/main/java/io/micronaut/core/util/CopyOnWriteMap.java
- `M` core/src/main/java/io/micronaut/core/util/EnvironmentProperties.java
- `D` core/src/main/java/io/micronaut/core/util/ExceptionUtils.java
- `M` core/src/main/java/io/micronaut/core/util/KotlinUtils.java
- `M` core/src/main/java/io/micronaut/core/util/LocaleResolver.java
- `M` core/src/main/java/io/micronaut/core/util/ObjectUtils.java
- `M` core/src/main/java/io/micronaut/core/util/StreamUtils.java
- `M` core/src/main/java/io/micronaut/core/util/StringUtils.java
- `M` core/src/main/java/io/micronaut/core/util/SupplierUtil.java
- `M` core/src/main/java/io/micronaut/core/util/clhm/ConcurrentLinkedHashMap.java
- `M` core/src/main/java/io/micronaut/core/util/clhm/LinkedDeque.java
- `M` core/src/main/java/io/micronaut/core/util/clhm/package-info.java
- `D` core/src/main/java/io/micronaut/core/util/functional/package-info.java
- `M` core/src/main/java/io/micronaut/core/util/locale/AbstractLocaleResolver.java
- `M` core/src/main/java/io/micronaut/core/util/locale/FixedLocaleResolver.java
- `M` core/src/main/java/io/micronaut/core/util/locale/LocaleResolutionConfiguration.java
- `M` core/src/main/java/io/micronaut/core/util/locale/package-info.java
- `M` core/src/main/java/io/micronaut/core/util/package-info.java
- `M` core/src/main/java/io/micronaut/core/value/MapPropertyResolver.java
- `M` core/src/main/java/io/micronaut/core/value/OptionalValues.java
- `M` core/src/main/java/io/micronaut/core/value/PropertyResolver.java
- `M` core/src/main/java/io/micronaut/core/value/package-info.java
- `M` discovery-core/src/main/java/io/micronaut/discovery/CompositeDiscoveryClient.java
- `M` discovery-core/src/main/java/io/micronaut/discovery/DefaultServiceInstance.java
- `M` discovery-core/src/main/java/io/micronaut/discovery/DefaultServiceInstanceIdGenerator.java
- `M` discovery-core/src/main/java/io/micronaut/discovery/ServiceInstanceIdGenerator.java
- `M` discovery-core/src/main/java/io/micronaut/discovery/StaticServiceInstanceList.java
- `M` discovery-core/src/main/java/io/micronaut/discovery/cloud/AbstractComputeInstanceMetadata.java
- `M` discovery-core/src/main/java/io/micronaut/discovery/cloud/ComputeInstanceMetadataResolverUtils.java
- `M` discovery-core/src/main/java/io/micronaut/discovery/cloud/NetworkInterface.java
- `M` discovery-core/src/main/java/io/micronaut/discovery/cloud/digitalocean/DigitalOceanInstanceMetadata.java
- `M` discovery-core/src/main/java/io/micronaut/discovery/cloud/digitalocean/DigitalOceanMetadataResolver.java
- `M` discovery-core/src/main/java/io/micronaut/discovery/cloud/digitalocean/DigitalOceanNetworkInterface.java
- `D` discovery-core/src/main/java/io/micronaut/discovery/cloud/digitalocean/package-info.java
- `M` discovery-core/src/main/java/io/micronaut/discovery/cloud/package-info.java
- `M` discovery-core/src/main/java/io/micronaut/discovery/config/ConfigDiscoveryConfiguration.java
- `M` discovery-core/src/main/java/io/micronaut/discovery/config/DefaultCompositeConfigurationClient.java
- `D` discovery-core/src/main/java/io/micronaut/discovery/config/RetryablePropertySourceImporter.java
- `M` discovery-core/src/main/java/io/micronaut/discovery/config/package-info.java
- `M` discovery-core/src/main/java/io/micronaut/discovery/event/package-info.java
- `M` discovery-core/src/main/java/io/micronaut/discovery/exceptions/package-info.java
- `M` discovery-core/src/main/java/io/micronaut/discovery/metadata/package-info.java
- `M` discovery-core/src/main/java/io/micronaut/discovery/package-info.java
- `M` discovery-core/src/main/java/io/micronaut/discovery/registration/RegistrationConfiguration.java
- `M` discovery-core/src/main/java/io/micronaut/discovery/registration/package-info.java
- `M` discovery-core/src/main/java/io/micronaut/health/DefaultCurrentHealthStatus.java
- `M` discovery-core/src/main/java/io/micronaut/health/HealthStatus.java
- `M` discovery-core/src/main/java/io/micronaut/health/package-info.java
- `M` function-client/src/main/java/io/micronaut/function/client/FunctionInvoker.java
- `M` function-client/src/main/java/io/micronaut/function/client/aop/FunctionClientAdvice.java
- `M` function-client/src/main/java/io/micronaut/function/client/aop/package-info.java
- `M` function-client/src/main/java/io/micronaut/function/client/exceptions/package-info.java
- `M` function-client/src/main/java/io/micronaut/function/client/http/HttpFunctionExecutor.java
- `M` function-client/src/main/java/io/micronaut/function/client/http/package-info.java
- `M` function-client/src/main/java/io/micronaut/function/client/local/package-info.java
- `M` function-client/src/main/java/io/micronaut/function/client/package-info.java
- `M` function-web/src/main/java/io/micronaut/function/web/AnnotatedFunctionRouteBuilder.java
- `M` function-web/src/main/java/io/micronaut/function/web/package-info.java
- `M` function/src/main/java/io/micronaut/function/BinaryTypeConfiguration.java
- `M` function/src/main/java/io/micronaut/function/DefaultLocalFunctionRegistry.java
- `M` function/src/main/java/io/micronaut/function/executor/AbstractExecutor.java
- `M` function/src/main/java/io/micronaut/function/executor/FunctionInitializer.java
- `M` function/src/main/java/io/micronaut/function/executor/StreamFunctionExecutor.java
- `M` function/src/main/java/io/micronaut/function/executor/package-info.java
- `M` function/src/main/java/io/micronaut/function/package-info.java
- `M` graal/src/main/java/io/micronaut/graal/reflect/GraalTypeElementVisitor.java
- `M` graal/src/main/java/io/micronaut/graal/reflect/package-info.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/AbstractHttpClientFactory.java
- `D` http-client-core/src/main/java/io/micronaut/http/client/AsyncHttpClient.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/BlockingHttpClient.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/ClientAttributes.java
- `D` http-client-core/src/main/java/io/micronaut/http/client/DefaultAsyncOverReactiveHttpClient.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/DefaultHttpClientConfiguration.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/HttpClient.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/HttpClientConfiguration.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/HttpClientFactory.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/HttpClientFactoryResolver.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/HttpClientRegistry.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/LoadBalancer.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/ProxyHttpClient.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/ProxyHttpClientFactory.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/ProxyHttpClientFactoryResolver.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/ProxyHttpClientRegistry.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/RawHttpClient.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/RawHttpClientFactory.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/RawHttpClientFactoryResolver.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/RawHttpClientRegistry.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/ServiceHttpClientConfiguration.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/StreamingHttpClient.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/StreamingHttpClientFactory.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/StreamingHttpClientFactoryResolver.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/StreamingHttpClientRegistry.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/annotation/Client.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/annotation/package-info.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/bind/AnnotatedClientArgumentRequestBinder.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/bind/AnnotatedClientRequestBinder.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/bind/ClientArgumentRequestBinder.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/bind/DefaultHttpClientBinderRegistry.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/bind/HttpClientBinderRegistry.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/bind/TypedClientArgumentRequestBinder.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/bind/binders/AttributeClientRequestBinder.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/bind/binders/HeaderClientRequestBinder.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/bind/binders/QueryValueClientArgumentRequestBinder.java
- `D` http-client-core/src/main/java/io/micronaut/http/client/bind/binders/package-info.java
- `D` http-client-core/src/main/java/io/micronaut/http/client/bind/package-info.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/exceptions/HttpClientException.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/exceptions/HttpClientExceptionUtils.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/exceptions/HttpClientResponseException.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/exceptions/package-info.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/filter/ClientFilterResolutionContext.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/filter/DefaultHttpClientFilterResolver.java
- `D` http-client-core/src/main/java/io/micronaut/http/client/filter/package-info.java
- `R078` http-client-core/src/main/java/io/micronaut/http/client/filters/package-info.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/interceptor/HttpClientIntroductionAdvice.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/interceptor/configuration/package-info.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/interceptor/package-info.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/loadbalance/DiscoveryClientRoundRobinLoadBalancer.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/loadbalance/FixedLoadBalancer.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/loadbalance/ServiceInstanceListRoundRobinLoadBalancer.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/loadbalance/package-info.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/multipart/AbstractFilePart.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/multipart/BytePart.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/multipart/FilePart.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/multipart/InputStreamPart.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/multipart/MultipartBody.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/multipart/MultipartDataFactory.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/multipart/Part.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/multipart/StringPart.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/multipart/package-info.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/package-info.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/sse/SseClient.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/sse/SseClientFactory.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/sse/SseClientFactoryResolver.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/sse/SseClientRegistry.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/sse/package-info.java
- `M` http-client-jdk/src/main/java/io/micronaut/http/client/jdk/AbstractJdkHttpClient.java
- `M` http-client-jdk/src/main/java/io/micronaut/http/client/jdk/DefaultJdkHttpClient.java
- `M` http-client-jdk/src/main/java/io/micronaut/http/client/jdk/DefaultJdkHttpClientRegistry.java
- `M` http-client-jdk/src/main/java/io/micronaut/http/client/jdk/HttpHeadersAdapter.java
- `M` http-client-jdk/src/main/java/io/micronaut/http/client/jdk/HttpRequestFactory.java
- `M` http-client-jdk/src/main/java/io/micronaut/http/client/jdk/HttpResponseAdapter.java
- `M` http-client-jdk/src/main/java/io/micronaut/http/client/jdk/JdkBlockingHttpClient.java
- `M` http-client-jdk/src/main/java/io/micronaut/http/client/jdk/JdkClientSslBuilder.java
- `M` http-client-jdk/src/main/java/io/micronaut/http/client/jdk/JdkHttpClientFactory.java
- `M` http-client-jdk/src/main/java/io/micronaut/http/client/jdk/JdkRawHttpClient.java
- `M` http-client-jdk/src/main/java/io/micronaut/http/client/jdk/RawHttpRequestWrapper.java
- `M` http-client-jdk/src/main/java/io/micronaut/http/client/jdk/cookie/CookieDecoder.java
- `M` http-client-jdk/src/main/java/io/micronaut/http/client/jdk/cookie/NettyCookieDecoder.java
- `D` http-client-jdk/src/main/java/io/micronaut/http/client/jdk/cookie/package-info.java
- `D` http-client-jdk/src/main/java/io/micronaut/http/client/jdk/package-info.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/BlockHint.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/CancellableMonoSink.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/CompositeNettyClientCustomizer.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/ConnectionManager.java
- `D` http-client/src/main/java/io/micronaut/http/client/netty/DefaultAsyncHttpClient.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/DefaultHttpClient.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/DefaultHttpClientBuilder.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/DefaultNettyHttpClientRegistry.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/FullNettyClientHttpResponse.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/Http1ResponseHandler.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/InitialConnectionErrorHandler.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/NettyClientByteBodyResponse.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/NettyClientCustomizer.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/NettyClientHttpRequest.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/NettyClientHttpRequestFactory.java
- `D` http-client/src/main/java/io/micronaut/http/client/netty/NettyHttpClient.java
- `D` http-client/src/main/java/io/micronaut/http/client/netty/NettyHttpClientBuilder.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/NettyHttpClientFactory.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/NettyStreamedHttpResponse.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/Pool.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/Pool40.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/Pool49.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/PoolSink.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/RawHttpRequestWrapper.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/SimpleChannelInboundHandlerInstrumented.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/SseSplitter.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/StreamWriter.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/converters/package-info.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/package-info.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/ssl/ClientSslBuilder.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/ssl/NettyClientSslBuilder.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/ssl/NettyClientSslFactory.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/ssl/package-info.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/websocket/NettyWebSocketClientHandler.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/websocket/package-info.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/AbstractCompositeCustomizer.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/NettyHttpHeaders.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/NettyHttpParameters.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/NettyHttpRequestBuilder.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/NettyHttpResponseBuilder.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/NettyMutableHttpResponse.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/NettySslContextBuilder.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/NettyTlsUtils.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/SslContextAutoLoader.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/SslContextHolder.java
- `A` http-netty/src/main/java/io/micronaut/http/netty/body/AvailableNettyByteBody.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/body/JsonChunkedProcessor.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/body/JsonCounter.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/body/NettyBodyAdapter.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/body/NettyByteBodyFactory.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/body/NettyByteBufMessageBodyHandler.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/body/NettyJsonHandler.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/body/NettyJsonStreamHandler.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/body/NettyWriteContext.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/body/StreamingNettyByteBody.java
- `D` http-netty/src/main/java/io/micronaut/http/netty/body/package-info.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/channel/ChannelPipelineCustomizer.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/channel/ChannelPipelineListener.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/channel/DefaultEventLoopGroupConfiguration.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/channel/DefaultEventLoopGroupFactory.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/channel/DefaultEventLoopGroupRegistry.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/channel/EpollEventLoopGroupFactory.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/channel/EventLoopGroupConfiguration.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/channel/EventLoopGroupFactory.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/channel/EventLoopGroupRegistry.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/channel/IoUringEventLoopGroupFactory.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/channel/KQueueEventLoopGroupFactory.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/channel/NioEventLoopGroupFactory.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/channel/TaskQueueInterceptor.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/channel/converters/DefaultChannelOptionFactory.java
- `D` http-netty/src/main/java/io/micronaut/http/netty/channel/converters/package-info.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/channel/loom/EventLoopVirtualThreadScheduler.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/channel/loom/LoomBranchSupport.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/channel/loom/LoomCarrierGroup.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/channel/loom/PrivateLoomSupport.java
- `D` http-netty/src/main/java/io/micronaut/http/netty/channel/loom/package-info.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/channel/package-info.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/configuration/NettyGlobalConfiguration.java
- `D` http-netty/src/main/java/io/micronaut/http/netty/configuration/package-info.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/content/package-info.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/cookies/NettyCookie.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/cookies/NettyLaxServerCookieDecoder.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/cookies/NettyServerCookieEncoder.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/cookies/package-info.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/package-info.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/reactive/HandlerSubscriber.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/reactive/package-info.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/stream/package-info.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/websocket/AbstractNettyWebSocketHandler.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/websocket/NettyServerWebSocketBroadcaster.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/websocket/NettyWebSocketSession.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/websocket/WebSocketMessageEncoder.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/websocket/package-info.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/AbstractNettyHttpRequest.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/DefaultNettyEmbeddedServerFactory.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/DelegateNettyEmbeddedServices.java
- `A` http-server-netty/src/main/java/io/micronaut/http/server/netty/FormDataHttpContentProcessor.java
- `A` http-server-netty/src/main/java/io/micronaut/http/server/netty/FormRouteCompleter.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/HttpContentProcessor.java
- `A` http-server-netty/src/main/java/io/micronaut/http/server/netty/HttpContentProcessorAsReactiveProcessor.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/HttpPipelineBuilder.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/IdentityWrapper.java
- `A` http-server-netty/src/main/java/io/micronaut/http/server/netty/MicronautHttpData.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/NettyEmbeddedServer.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/NettyEmbeddedServerFactory.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/NettyEmbeddedServices.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/NettyHttpRequest.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/NettyHttpResponseFactory.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/NettyHttpServer.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/NettyRequestLifecycle.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/NettyResponseLifecycle.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/NettyServerCustomizer.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/NonReentrantLock.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/RoutingInBoundHandler.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/async/package-info.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/binders/NettyBodyAnnotationBinder.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/binders/NettyCompletableFutureBodyBinder.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/binders/NettyCompletedFileUploadBinder.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/binders/NettyPartUploadAnnotationBinder.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/binders/NettyPublisherBodyBinder.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/binders/NettyPublisherPartUploadBinder.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/binders/NettyServerRequestBinderRegistry.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/binders/NettyStreamingFileUploadBinder.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/binders/package-info.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/configuration/NettyHttpServerConfiguration.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/configuration/package-info.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/converters/NettyConverters.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/converters/NettyConvertersSpi.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/converters/package-info.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/decoders/package-info.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/discovery/NettyEmbeddedServerInstance.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/discovery/NettyServiceDiscovery.java
- `D` http-server-netty/src/main/java/io/micronaut/http/server/netty/discovery/package-info.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/encoders/package-info.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/Compressor.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/Http2ServerHandler.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/HttpRequestEvent.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/MultiplexedServerHandler.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/PipeliningServerHandler.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/RequestHandler.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/accesslog/Http2AccessLogManager.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/accesslog/HttpAccessLogHandler.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/accesslog/element/AbstractHttpMessageLogElement.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/accesslog/element/AccessLogFormatParser.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/accesslog/element/BytesSentElementBuilder.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/accesslog/element/ConnectionMetadata.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/accesslog/element/ConnectionMetadataImpl.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/accesslog/element/ConstantElement.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/accesslog/element/CookieElementBuilder.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/accesslog/element/DateTimeElement.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/accesslog/element/DateTimeElementBuilder.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/accesslog/element/ElapseTimeElement.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/accesslog/element/ElapseTimeElementBuilder.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/accesslog/element/HeaderElementBuilder.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/accesslog/element/LocalHostElement.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/accesslog/element/LocalHostElementBuilder.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/accesslog/element/LocalIpElement.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/accesslog/element/LocalIpElementBuilder.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/accesslog/element/LocalPortElement.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/accesslog/element/LocalPortElementBuilder.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/accesslog/element/LogElement.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/accesslog/element/LogElementBuilder.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/accesslog/element/NotImplementedElementBuilder.java
- `D` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/accesslog/element/QueryStringElement.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/accesslog/element/RemoteHostElement.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/accesslog/element/RemoteHostElementBuilder.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/accesslog/element/RemoteIpElement.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/accesslog/element/RemoteIpElementBuilder.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/handler/accesslog/element/RequestLineElement.java

### Tests

- `D` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `A` benchmarks/src/typeCheckTest/java/example/TypeThrashingTest.java
- `M` buffer-netty/src/test/java/io/micronaut/buffer/netty/AbstractReadBufferTest.java
- `M` context-propagation/src/test/groovy/io/micronaut/context/AnnotationReflectionUtilsSpec.groovy
- `M` context-propagation/src/test/groovy/io/micronaut/context/propagation/MDCReactorSpec.groovy
- `A` context-propagation/src/test/groovy/io/micronaut/context/propagation/MDCRxJava2Spec.groovy
- `M` context-propagation/src/test/groovy/io/micronaut/context/propagation/MDCRxJava3Spec.groovy
- `M` context-propagation/src/test/groovy/io/micronaut/context/propagation/MDCSpec.groovy
- `M` context-propagation/src/test/groovy/io/micronaut/context/propagation/MDCSpec2.groovy
- `M` context-propagation/src/test/groovy/io/micronaut/context/propagation/MDCSpec3.groovy
- `R076` context-propagation/src/test/groovy/io/micronaut/context/propagation/ReactorRx2JavaSpec.groovy
- `M` context-propagation/src/test/groovy/io/micronaut/context/propagation/SimpleTraceInterceptorSpec.groovy
- `M` context-propagation/src/test/groovy/io/micronaut/context/propagation/ThreadLocalPropagatedTraceInterceptorSpec.groovy
- `M` context-propagation/src/test/kotlin/io/micronaut/context/propagation/mdc/MdcPropagationSpec.kt
- `D` context/src/test/java/io/micronaut/context/propagation/PropagatedContextConfigurationPropertiesTest.java
- `D` context/src/test/java/io/micronaut/runtime/MicronautConfigurationLoadingStrategyTest.java
- `M` context/src/test/java/io/micronaut/runtime/context/CompositeMessageSourceTest.java
- `D` context/src/test/java/io/micronaut/runtime/context/scope/refresh/RefreshScopeGetOrCreateTest.java
- `M` core-processor/src/main/java/io/micronaut/inject/annotation/internal/JspecifyNotNullTransformer.java
- `M` core-processor/src/main/java/io/micronaut/inject/annotation/internal/JspecifyNullMarkedTransformer.java
- `M` core-processor/src/main/java/io/micronaut/inject/annotation/internal/JspecifyNullableTransformer.java
- `M` core-processor/src/main/java/io/micronaut/inject/beans/visitor/BeanIntrospectionWriter.java
- `M` core-processor/src/main/java/io/micronaut/inject/beans/visitor/EntityIntrospectedAnnotationMapper.java
- `M` core-processor/src/main/java/io/micronaut/inject/beans/visitor/IntrospectedPackageElementVisitor.java
- `M` core-processor/src/main/java/io/micronaut/inject/beans/visitor/IntrospectedTypeElementVisitor.java
- `M` core-processor/src/main/java/io/micronaut/inject/beans/visitor/MappedSuperClassIntrospectionMapper.java
- `M` core-processor/src/main/java/io/micronaut/inject/beans/visitor/persistence/JakartaEntityIntrospectedAnnotationMapper.java
- `M` core-processor/src/main/java/io/micronaut/inject/beans/visitor/persistence/JakartaMappedSuperClassIntrospectionMapper.java
- `M` core-reactive/src/test/groovy/io/micronaut/core/async/propagation/ReactivePropagationSpec.groovy
- `M` core/src/main/java/io/micronaut/core/beans/AbstractBeanIntrospectionReference.java
- `M` core/src/main/java/io/micronaut/core/beans/BeanIntrospection.java
- `M` core/src/main/java/io/micronaut/core/beans/BeanIntrospectionMap.java
- `M` core/src/main/java/io/micronaut/core/beans/BeanIntrospectionReference.java
- `M` core/src/main/java/io/micronaut/core/beans/BeanIntrospector.java
- `M` core/src/main/java/io/micronaut/core/beans/DefaultBeanIntrospector.java
- `M` core/src/main/java/io/micronaut/core/beans/UnsafeBeanInstantiationIntrospection.java
- `M` core/src/main/java/io/micronaut/core/io/scan/BeanIntrospectionScanner.java
- `M` core/src/test/groovy/io/micronaut/core/naming/NameUtilsSpec.groovy
- `A` core/src/test/groovy/io/micronaut/core/propagation/PropagatedContextSpec.groovy
- `M` core/src/test/java/io/micronaut/core/io/service/SoftServiceLoaderTest.java
- `D` core/src/test/java/io/micronaut/core/propagation/MixedPropagatedContextTest.java
- `D` core/src/test/java/io/micronaut/core/propagation/PropagatedContextConfigurationTest.java
- `D` core/src/test/java/io/micronaut/core/propagation/PropagatedContextLambdaTest.java
- `D` core/src/test/java/io/micronaut/core/propagation/PropagatedContextTryResourcesTest.java
- `D` core/src/test/java/io/micronaut/core/propagation/ScopedValuePropagatedContextElementTest.java
- `D` core/src/test/java/io/micronaut/core/propagation/ScopedValuesPropagatedContextTest.java
- `D` core/src/test/java/io/micronaut/core/propagation/ThreadLocalPropagatedContextLambdaTest.java
- `D` core/src/test/java/io/micronaut/core/propagation/ThreadLocalPropagatedContextTryResourcesTest.java
- `D` core/src/test/java/io/micronaut/core/util/ConnectionStringTest.java
- `D` discovery-core/src/test/java/io/micronaut/discovery/config/RetryablePropertySourceImporterTest.java
- `M` function-web/src/test/groovy/io/micronaut/function/web/JavaLambdaFunctionSpec.groovy
- `D` http-client-jdk/src/test/groovy/io/micronaut/http/client/jdk/Issue12244Spec.groovy
- `D` http-client-jdk/src/test/groovy/io/micronaut/http/client/jdk/JdkBlockingHttpClientReuseSpec.groovy
- `D` http-client-jdk/src/test/groovy/io/micronaut/http/client/jdk/JdkBlockingHttpClientThreadLeakSpec.groovy
- `M` http-client-jdk/src/test/groovy/io/micronaut/http/client/jdk/RequestAttributeBindingSpec.groovy
- `M` http-client-tck/src/main/java/io/micronaut/http/client/tck/tests/DecompressionConfigTest.java
- `M` http-client-tck/src/main/java/io/micronaut/http/client/tck/tests/FormUrlEncodedTest.java
- `M` http-client-tck/src/main/java/io/micronaut/http/client/tck/tests/HeadersTest.java
- `M` http-client-tck/src/main/java/io/micronaut/http/client/tck/tests/Person.java
- `M` http-client-tck/src/main/java/io/micronaut/http/client/tck/tests/RedirectTest.java
- `M` http-client-tck/src/main/java/io/micronaut/http/client/tck/tests/filter/ClientRequestFilterTest.java
- `M` http-client-tck/src/main/java/io/micronaut/http/client/tck/tests/filter/ClientResponseFilterTest.java
- `D` http-client-tck/src/main/java/io/micronaut/http/client/tck/tests/filter/package-info.java
- `D` http-client-tck/src/main/java/io/micronaut/http/client/tck/tests/package-info.java
- `M` http-client/src/test/groovy/io/micronaut/http/client/ClientIntroductionAdviceSpec.groovy
- `M` http-client/src/test/groovy/io/micronaut/http/client/ClientRedirectSpec.groovy
- `M` http-client/src/test/groovy/io/micronaut/http/client/ClientScopeSpec.groovy
- `M` http-client/src/test/groovy/io/micronaut/http/client/DataStreamSpec.groovy
- `M` http-client/src/test/groovy/io/micronaut/http/client/HttpClientTraceLoggingSpec.groovy
- `M` http-client/src/test/groovy/io/micronaut/http/client/HttpGetSpec.groovy
- `M` http-client/src/test/groovy/io/micronaut/http/client/HttpPostSpec.groovy
- `M` http-client/src/test/groovy/io/micronaut/http/client/HttpPutSpec.groovy
- `M` http-client/src/test/groovy/io/micronaut/http/client/JsonSpec.groovy
- `M` http-client/src/test/groovy/io/micronaut/http/client/JsonStreamSpec.groovy
- `D` http-client/src/test/groovy/io/micronaut/http/client/ReactorHttpClientRetrySpec.groovy
- `R089` http-client/src/test/groovy/io/micronaut/http/client/SslRefreshSpec.groovy
- `M` http-client/src/test/groovy/io/micronaut/http/client/SslSpec.groovy
- `M` http-client/src/test/groovy/io/micronaut/http/client/aop/NullableCrudSpec.groovy
- `M` http-client/src/test/groovy/io/micronaut/http/client/bootstrap/ClientBootstrapSpec.groovy
- `M` http-client/src/test/groovy/io/micronaut/http/client/config/DefaultHttpClientConfigurationSpec.groovy
- `M` http-client/src/test/groovy/io/micronaut/http/client/netty/ConnectionManagerSpec.groovy
- `M` http-client/src/test/groovy/io/micronaut/http/client/netty/EmbeddedConnectionManager.java
- `M` http-client/src/test/groovy/io/micronaut/http/client/netty/EmbeddedTestUtil.groovy
- `M` http-client/src/test/groovy/io/micronaut/http/client/netty/Http1ResponseHandlerSpec.groovy
- `D` http-client/src/test/groovy/io/micronaut/http/client/netty/HttpClientToAsyncSpec.groovy
- `M` http-client/src/test/groovy/io/micronaut/http/client/retry/HttpClientRetrySpec.groovy
- `M` http-client/src/test/groovy/io/micronaut/http/client/retry/HttpClientWithCircuitBreakerSpec.groovy
- `M` http-client/src/test/groovy/io/micronaut/http/client/stream/StreamPostSpec.groovy
- `M` http-client/src/test/java/io/micronaut/http/client/ProxyBackpressureTest.java
- `D` http-client/src/test/resources/application-test.properties
- `M` http-netty/src/test/groovy/io/micronaut/http/netty/EventLoopFlowSpec.groovy
- `M` http-netty/src/test/groovy/io/micronaut/http/netty/body/CustomBodyReaderSpec.groovy
- `M` http-netty/src/test/groovy/io/micronaut/http/netty/body/CustomBodyWriterSpec.groovy
- `M` http-netty/src/test/groovy/io/micronaut/http/netty/body/DefaultHandlerSpec.groovy
- `M` http-netty/src/test/groovy/io/micronaut/http/netty/body/JsonCounterSpec.groovy
- `M` http-netty/src/test/groovy/io/micronaut/http/netty/channel/EventLoopGroupSpec.groovy

## Suggested Manual Checks

- Inspect commits and diffs with breaking-change or migration keywords before publishing.
- Verify dependency updates against supported runtime and compatibility policy.
- Collapse internal-only changes unless this repository's release notes normally include them.
- Confirm dirty worktrees are intentional before treating this report as final.

