# Release Note Comparison

Generated: 2026-05-13 10:26 UTC
Comparison: `mn4-4.10.x` -> `mn5-5.0.x`
Mode: git

## Scope

| Side | Path | Branch | Commit | Remote | Dirty |
| --- | --- | --- | --- | --- | --- |
| Previous | `/Users/sdelamo/github/micronaut/mn4/micronaut-core` | `4.10.x` | `c2b22742d650` | `git@github.com:micronaut-projects/micronaut-core.git` | `False` |
| Current | `/Users/sdelamo/github/micronaut/mn5/micronaut-core` | `5.0.x` | `54d1ebd157bf` | `git@github.com:micronaut-projects/micronaut-core.git` | `False` |

## Summary Signals

- Same remote: `True`
- Diff repository: `/Users/sdelamo/github/micronaut/mn5/micronaut-core`
- Commit candidates found: 338
- File changes listed: 1000
- Version values listed: 265
- File status counts: A=133, D=8, M=850, R=9

## Version Comparison

| Source | Name | Previous | Current | Status |
| --- | --- | --- | --- | --- |
| `.sdkmanrc` | `java` | `not present` | `25.0.1-graal` | `added` |
| `gradle.properties` | `graalVersion` | `23.1.8` | `25.0.2` | `changed` |
| `gradle.properties` | `projectVersion` | `4.10.24-SNAPSHOT` | `5.0.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.awaitility` | `org.awaitility:awaitility:4.3.0` | `org.awaitility:awaitility:4.3.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.bcpkix` | `org.bouncycastle:bcpkix-jdk15on:1.70` | `org.bouncycastle:bcpkix-jdk18on:1.84` | `changed` |
| `gradle/libs.versions.toml` | `libraries.blaze-persistence-core` | `com.blazebit:blaze-persistence-core-impl:1.6.17` | `com.blazebit:blaze-persistence-core-impl:1.6.18` | `changed` |
| `gradle/libs.versions.toml` | `libraries.boms-groovy` | `org.apache.groovy:groovy-bom:4.0.28` | `org.apache.groovy:groovy-bom:5.0.6` | `changed` |
| `gradle/libs.versions.toml` | `libraries.boms-jackson` | `com.fasterxml.jackson:jackson-bom:2.21.2` | `tools.jackson:jackson-bom:3.1.3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.boms-kotlin` | `org.jetbrains.kotlin:kotlin-bom:1.9.25` | `org.jetbrains.kotlin:kotlin-bom:2.3.21` | `changed` |
| `gradle/libs.versions.toml` | `libraries.boms-kotlin-coroutines` | `org.jetbrains.kotlinx:kotlinx-coroutines-bom:1.8.1` | `org.jetbrains.kotlinx:kotlinx-coroutines-bom:1.10.2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.boms-micronaut-sourcegen` | `io.micronaut.sourcegen:micronaut-sourcegen-bom:1.8.2` | `io.micronaut.sourcegen:micronaut-sourcegen-bom:2.0.0-RC4` | `changed` |
| `gradle/libs.versions.toml` | `libraries.boms-netty` | `io.netty:netty-bom:4.2.13.Final` | `io.netty:netty-bom:4.2.13.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.brotli4j` | `com.aayushatharva.brotli4j:brotli4j:1.18.0` | `com.aayushatharva.brotli4j:brotli4j:1.18.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.bytebuddy` | `net.bytebuddy:byte-buddy:1.17.8` | `net.bytebuddy:byte-buddy:1.18.8` | `changed` |
| `gradle/libs.versions.toml` | `libraries.bytebuddy-agent` | `net.bytebuddy:byte-buddy-agent:1.17.8` | `net.bytebuddy:byte-buddy-agent:1.18.8` | `changed` |
| `gradle/libs.versions.toml` | `libraries.caffeine` | `com.github.ben-manes.caffeine:caffeine:2.9.3` | `com.github.ben-manes.caffeine:caffeine:2.9.3` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.classgraph` | `io.github.classgraph:classgraph:4.8.181` | `io.github.classgraph:classgraph:4.8.184` | `changed` |
| `gradle/libs.versions.toml` | `libraries.compile-testing` | `com.google.testing.compile:compile-testing:0.21.0` | `com.google.testing.compile:compile-testing:0.21.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.error-prone-core` | `not present` | `com.google.errorprone:error_prone_core:2.48.0` | `added` |
| `gradle/libs.versions.toml` | `libraries.geb-spock` | `org.gebish:geb-spock:7.0` | `org.gebish:geb-spock:7.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.graal` | `org.graalvm.sdk:nativeimage:23.1.8` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.gradle-errorprone` | `not present` | `net.ltgt.errorprone:net.ltgt.errorprone.gradle.plugin:4.4.0` | `added` |
| `gradle/libs.versions.toml` | `libraries.groovy-test-junit5` | `org.apache.groovy:groovy-test-junit5:4.0.28` | `org.apache.groovy:groovy-test-junit5:5.0.6` | `changed` |
| `gradle/libs.versions.toml` | `libraries.h2` | `com.h2database:h2:2.2.224` | `com.h2database:h2:2.4.240` | `changed` |
| `gradle/libs.versions.toml` | `libraries.hibernate` | `org.hibernate:hibernate-core:5.5.9.Final` | `org.hibernate:hibernate-core:5.5.9.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.htmlsanitycheck` | `org.aim42:htmlSanityCheck:1.1.6` | `org.aim42:htmlSanityCheck:1.1.6` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.htmlunit` | `net.sourceforge.htmlunit:htmlunit:2.70.0` | `net.sourceforge.htmlunit:htmlunit:2.70.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.httpcomponents-client` | `org.apache.httpcomponents:httpclient:4.5.14` | `org.apache.httpcomponents:httpclient:4.5.14` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.httpcomponents-mime` | `org.apache.httpcomponents:httpmime:4.5.14` | `org.apache.httpcomponents:httpmime:4.5.14` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.icu4j` | `com.ibm.icu:icu4j:76.1` | `com.ibm.icu:icu4j:76.1` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.jackson2-databind` | `not present` | `com.fasterxml.jackson.core:jackson-databind:2.21.3` | `added` |
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
| `gradle/libs.versions.toml` | `libraries.junit4` | `not present` | `junit:junit:4.13.2` | `added` |
| `gradle/libs.versions.toml` | `libraries.kotlin2-annotation-processing-embeddable` | `org.jetbrains.kotlin:kotlin-annotation-processing-embeddable:2.1.21` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.kotlin2-compiler-embeddable` | `org.jetbrains.kotlin:kotlin-compiler-embeddable:2.1.21` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.kotlin2-reflect` | `org.jetbrains.kotlin:kotlin-reflect:2.1.21` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.kotlin2-stdlib` | `org.jetbrains.kotlin:kotlin-stdlib:2.1.21` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.kotlin2-stdlib-jdk8` | `org.jetbrains.kotlin:kotlin-stdlib-jdk8:2.1.21` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.kotlin2-test` | `org.jetbrains.kotlin:kotlin-test:2.1.21` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.ksp-aaEmbeddable` | `not present` | `com.google.devtools.ksp:symbol-processing-aa-embeddable:2.3.6` | `added` |
| `gradle/libs.versions.toml` | `libraries.ksp-commonDeps` | `not present` | `com.google.devtools.ksp:symbol-processing-common-deps:2.3.6` | `added` |
| `gradle/libs.versions.toml` | `libraries.ksp2` | `com.google.devtools.ksp:symbol-processing:2.1.21-2.0.2` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.ksp2-aaEmbeddable` | `com.google.devtools.ksp:symbol-processing-aa-embeddable:2.1.21-2.0.2` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.ksp2-api` | `com.google.devtools.ksp:symbol-processing-api:2.1.21-2.0.2` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.ksp2-commonDeps` | `com.google.devtools.ksp:symbol-processing-common-deps:2.1.21-2.0.2` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.log4j` | `org.apache.logging.log4j:log4j-core:2.25.4` | `org.apache.logging.log4j:log4j-core:2.25.4` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.logback-classic` | `ch.qos.logback:logback-classic:1.5.29` | `ch.qos.logback:logback-classic:1.5.32` | `changed` |
| `gradle/libs.versions.toml` | `libraries.logbook-netty` | `org.zalando:logbook-netty:3.12.2` | `org.zalando:logbook-netty:3.12.3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.lombok` | `org.projectlombok:lombok:1.18.40` | `org.projectlombok:lombok:1.18.46` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-graalvm-nativeimage` | `not present` | `org.graalvm.sdk:nativeimage:25.0.3` | `added` |
| `gradle/libs.versions.toml` | `libraries.managed-groovy` | `org.apache.groovy:groovy:4.0.28` | `org.apache.groovy:groovy:5.0.6` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-groovy-json` | `org.apache.groovy:groovy-json:4.0.28` | `org.apache.groovy:groovy-json:5.0.6` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-groovy-sql` | `org.apache.groovy:groovy-sql:4.0.28` | `org.apache.groovy:groovy-sql:5.0.6` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-groovy-templates` | `org.apache.groovy:groovy-templates:4.0.28` | `org.apache.groovy:groovy-templates:5.0.6` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-jackson-annotations` | `com.fasterxml.jackson.core:jackson-annotations:2.21` | `com.fasterxml.jackson.core:jackson-annotations:2.21` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-jackson-core` | `com.fasterxml.jackson.core:jackson-core:2.21.2` | `tools.jackson.core:jackson-core:3.1.3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-jackson-databind` | `com.fasterxml.jackson.core:jackson-databind:2.21.2` | `tools.jackson.core:jackson-databind:3.1.3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-jackson-dataformat-xml` | `com.fasterxml.jackson.dataformat:jackson-dataformat-xml:2.21.2` | `tools.jackson.dataformat:jackson-dataformat-xml:3.1.3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-jackson-dataformat-yaml` | `com.fasterxml.jackson.dataformat:jackson-dataformat-yaml:2.21.2` | `tools.jackson.dataformat:jackson-dataformat-yaml:3.1.3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-jackson-datatype-jdk8` | `com.fasterxml.jackson.datatype:jackson-datatype-jdk8:2.21.2` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.managed-jackson-datatype-jsr310` | `com.fasterxml.jackson.datatype:jackson-datatype-jsr310:2.21.2` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.managed-jackson-module-afterburner` | `com.fasterxml.jackson.module:jackson-module-afterburner:2.21.2` | `tools.jackson.module:jackson-module-afterburner:3.1.3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-jackson-module-kotlin` | `com.fasterxml.jackson.module:jackson-module-kotlin:2.21.2` | `tools.jackson.module:jackson-module-kotlin:3.1.3` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-jackson-module-parameterNames` | `com.fasterxml.jackson.module:jackson-module-parameter-names:2.21.2` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.managed-jakarta-annotation-api` | `jakarta.annotation:jakarta.annotation-api:2.1.1` | `jakarta.annotation:jakarta.annotation-api:2.1.1` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-java-parser-core` | `com.github.javaparser:javaparser-symbol-solver-core:3.27.0` | `com.github.javaparser:javaparser-symbol-solver-core:3.28.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-jspecify` | `org.jspecify:jspecify:1.0.0` | `org.jspecify:jspecify:1.0.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-kotlin-annotation-processing-embeddable` | `org.jetbrains.kotlin:kotlin-annotation-processing-embeddable:1.9.25` | `org.jetbrains.kotlin:kotlin-annotation-processing-embeddable:2.3.21` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-kotlin-compiler-embeddable` | `org.jetbrains.kotlin:kotlin-compiler-embeddable:1.9.25` | `org.jetbrains.kotlin:kotlin-compiler-embeddable:2.3.21` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-kotlin-reflect` | `org.jetbrains.kotlin:kotlin-reflect:1.9.25` | `org.jetbrains.kotlin:kotlin-reflect:2.3.21` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-kotlin-stdlib` | `org.jetbrains.kotlin:kotlin-stdlib:1.9.25` | `org.jetbrains.kotlin:kotlin-stdlib:2.3.21` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-kotlin-stdlib-jdk8` | `org.jetbrains.kotlin:kotlin-stdlib-jdk8:1.9.25` | `org.jetbrains.kotlin:kotlin-stdlib-jdk8:2.3.21` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-kotlin-test` | `org.jetbrains.kotlin:kotlin-test:1.9.25` | `org.jetbrains.kotlin:kotlin-test:2.3.21` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-kotlinx-coroutines-core` | `org.jetbrains.kotlinx:kotlinx-coroutines-core:1.8.1` | `org.jetbrains.kotlinx:kotlinx-coroutines-core:1.10.2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-kotlinx-coroutines-jdk8` | `org.jetbrains.kotlinx:kotlinx-coroutines-jdk8:1.8.1` | `org.jetbrains.kotlinx:kotlinx-coroutines-jdk8:1.10.2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-kotlinx-coroutines-reactive` | `org.jetbrains.kotlinx:kotlinx-coroutines-reactive:1.8.1` | `org.jetbrains.kotlinx:kotlinx-coroutines-reactive:1.10.2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-kotlinx-coroutines-reactor` | `org.jetbrains.kotlinx:kotlinx-coroutines-reactor:1.8.1` | `org.jetbrains.kotlinx:kotlinx-coroutines-reactor:1.10.2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-kotlinx-coroutines-rx2` | `org.jetbrains.kotlinx:kotlinx-coroutines-rx2:1.8.1` | `org.jetbrains.kotlinx:kotlinx-coroutines-rx2:1.10.2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-kotlinx-coroutines-slf4j` | `org.jetbrains.kotlinx:kotlinx-coroutines-slf4j:1.8.1` | `org.jetbrains.kotlinx:kotlinx-coroutines-slf4j:1.10.2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-ksp` | `com.google.devtools.ksp:symbol-processing:1.9.25-1.0.20` | `com.google.devtools.ksp:symbol-processing:2.3.6` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-ksp-api` | `com.google.devtools.ksp:symbol-processing-api:1.9.25-1.0.20` | `com.google.devtools.ksp:symbol-processing-api:2.3.6` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-methvin-directoryWatcher` | `io.methvin:directory-watcher:0.19.1` | `io.methvin:directory-watcher:0.19.1` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-buffer` | `io.netty:netty-buffer:4.2.13.Final` | `io.netty:netty-buffer:4.2.13.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-codec-classes-quic` | `io.netty:netty-codec-classes-quic:4.2.13.Final` | `io.netty:netty-codec-classes-quic:4.2.13.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-codec-http` | `io.netty:netty-codec-http:4.2.13.Final` | `io.netty:netty-codec-http:4.2.13.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-codec-http2` | `io.netty:netty-codec-http2:4.2.13.Final` | `io.netty:netty-codec-http2:4.2.13.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-codec-http3` | `io.netty:netty-codec-http3:4.2.13.Final` | `io.netty:netty-codec-http3:4.2.13.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-codec-native-quic` | `io.netty:netty-codec-native-quic:4.2.13.Final` | `io.netty:netty-codec-native-quic:4.2.13.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-common` | `io.netty:netty-common:4.2.13.Final` | `io.netty:netty-common:4.2.13.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-contrib-multipart-core` | `not present` | `io.netty.contrib:netty-codec-multipart-core:1.0.0.Final` | `added` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-contrib-multipart-vintage` | `io.netty.contrib:netty-codec-multipart-vintage:1.0.0.Final` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-handler` | `io.netty:netty-handler:4.2.13.Final` | `io.netty:netty-handler:4.2.13.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-handler-proxy` | `io.netty:netty-handler-proxy:4.2.13.Final` | `io.netty:netty-handler-proxy:4.2.13.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-pkitesting` | `io.netty:netty-pkitesting:4.2.13.Final` | `io.netty:netty-pkitesting:4.2.13.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-tcnative-boringssl-static` | `io.netty:netty-tcnative-boringssl-static:2.0.75.Final` | `io.netty:netty-tcnative-boringssl-static:2.0.77.Final` | `changed` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-transport-native-epoll` | `io.netty:netty-transport-native-epoll:4.2.13.Final` | `io.netty:netty-transport-native-epoll:4.2.13.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-transport-native-iouring` | `io.netty:netty-transport-native-io_uring:4.2.13.Final` | `io.netty:netty-transport-native-io_uring:4.2.13.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-transport-native-kqueue` | `io.netty:netty-transport-native-kqueue:4.2.13.Final` | `io.netty:netty-transport-native-kqueue:4.2.13.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-netty-transport-native-unix-common` | `io.netty:netty-transport-native-unix-common:4.2.13.Final` | `io.netty:netty-transport-native-unix-common:4.2.13.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-reactive-streams` | `org.reactivestreams:reactive-streams:1.0.4` | `org.reactivestreams:reactive-streams:1.0.4` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-reactor` | `io.projectreactor:reactor-core:3.7.12` | `io.projectreactor:reactor-core:3.7.12` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-reactor-test` | `io.projectreactor:reactor-test:3.7.12` | `io.projectreactor:reactor-test:3.7.12` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.managed-snakeyaml` | `org.yaml:snakeyaml:2.4` | `org.yaml:snakeyaml:2.4` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.micronaut-build-plugins` | `io.micronaut.build.internal:micronaut-gradle-plugins:7.6.4` | `io.micronaut.build.internal:micronaut-gradle-plugins:8.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-docs` | `io.micronaut.docs:micronaut-docs-asciidoc-config-props:3.0.0` | `io.micronaut.docs:micronaut-docs-asciidoc-config-props:3.0.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.micronaut-runtime-groovy` | `io.micronaut.groovy:micronaut-runtime-groovy:4.7.0` | `io.micronaut.groovy:micronaut-runtime-groovy:4.7.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.micronaut-session` | `io.micronaut.session:micronaut-session:4.6.0` | `io.micronaut.session:micronaut-session:4.6.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.micronaut-sql-jdbc` | `io.micronaut.sql:micronaut-jdbc:5.3.0` | `io.micronaut.sql:micronaut-jdbc:7.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-sql-jdbc-tomcat` | `io.micronaut.sql:micronaut-jdbc-tomcat:5.3.0` | `io.micronaut.sql:micronaut-jdbc-tomcat:7.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-bom` | `io.micronaut.test:micronaut-test-bom:4.10.2` | `io.micronaut.test:micronaut-test-bom:5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-core` | `io.micronaut.test:micronaut-test-core:4.10.2` | `io.micronaut.test:micronaut-test-core:5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-junit5` | `io.micronaut.test:micronaut-test-junit5:4.10.2` | `io.micronaut.test:micronaut-test-junit5:5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-kotest5` | `io.micronaut.test:micronaut-test-kotest5:4.10.2` | `io.micronaut.test:micronaut-test-kotest5:5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-netty-leak` | `io.micronaut.test:micronaut-test-netty-leak:4.10.2` | `io.micronaut.test:micronaut-test-netty-leak:5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-spock` | `io.micronaut.test:micronaut-test-spock:4.10.2` | `io.micronaut.test:micronaut-test-spock:5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.micronaut-test-type-pollution` | `io.micronaut.test:micronaut-test-type-pollution:4.10.2` | `io.micronaut.test:micronaut-test-type-pollution:5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.mimepull` | `org.jvnet.mimepull:mimepull:1.10.0` | `org.jvnet.mimepull:mimepull:1.10.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.native-gradle-plugin` | `org.graalvm.buildtools.native:org.graalvm.buildtools.native.gradle.plugin:0.11.2` | `org.graalvm.buildtools.native:org.graalvm.buildtools.native.gradle.plugin:0.11.4` | `changed` |
| `gradle/libs.versions.toml` | `libraries.neo4j-bolt` | `org.neo4j.driver:neo4j-java-driver:5.17.0` | `org.neo4j.driver:neo4j-java-driver:5.17.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.nullaway` | `not present` | `com.uber.nullaway:nullaway:0.13.1` | `added` |
| `gradle/libs.versions.toml` | `libraries.okio` | `com.squareup.okio:okio:3.9.1` | `com.squareup.okio:okio:3.9.1` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.selenium-api` | `org.seleniumhq.selenium:selenium-api:4.27.0` | `org.seleniumhq.selenium:selenium-api:4.27.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.selenium-driver-chrome` | `org.seleniumhq.selenium:selenium-chrome-driver:4.27.0` | `org.seleniumhq.selenium:selenium-chrome-driver:4.27.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.selenium-driver-firefox` | `org.seleniumhq.selenium:selenium-firefox-driver:4.27.0` | `org.seleniumhq.selenium:selenium-firefox-driver:4.27.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.selenium-driver-htmlunit` | `org.seleniumhq.selenium:htmlunit-driver:4.27.0` | `org.seleniumhq.selenium:htmlunit-driver:4.27.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.selenium-remote-driver` | `org.seleniumhq.selenium:selenium-remote-driver:4.27.0` | `org.seleniumhq.selenium:selenium-remote-driver:4.27.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.selenium-support` | `org.seleniumhq.selenium:selenium-support:4.27.0` | `org.seleniumhq.selenium:selenium-support:4.27.0` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.slf4j-api` | `org.slf4j:slf4j-api:2.0.17` | `org.slf4j:slf4j-api:2.0.17` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.smallrye` | `io.smallrye:smallrye-fault-tolerance:6.9.2` | `io.smallrye:smallrye-fault-tolerance:6.9.2` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.sonatype-scan` | `org.sonatype.gradle.plugins:scan-gradle-plugin:3.0.0` | `org.sonatype.gradle.plugins:scan-gradle-plugin:3.1.5` | `changed` |
| `gradle/libs.versions.toml` | `libraries.spock` | `org.spockframework:spock-core:2.3-groovy-4.0` | `org.spockframework:spock-core:2.4-groovy-5.0` | `changed` |
| `gradle/libs.versions.toml` | `libraries.spotbugs` | `com.github.spotbugs:spotbugs-annotations:4.9.6` | `com.github.spotbugs:spotbugs-annotations:4.9.8` | `changed` |
| `gradle/libs.versions.toml` | `libraries.systemlambda` | `com.github.stefanbirkner:system-lambda:1.2.1` | `com.github.stefanbirkner:system-lambda:1.2.1` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.test-boms-micronaut-aws` | `io.micronaut.aws:micronaut-aws-bom:4.11.0` | `io.micronaut.aws:micronaut-aws-bom:5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.test-boms-micronaut-kotlin` | `io.micronaut.kotlin:micronaut-kotlin-bom:4.6.0` | `io.micronaut.kotlin:micronaut-kotlin-bom:5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.test-boms-micronaut-reactor` | `io.micronaut.reactor:micronaut-reactor-bom:3.7.0` | `io.micronaut.reactor:micronaut-reactor-bom:4.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.test-boms-micronaut-rxjava2` | `io.micronaut.rxjava2:micronaut-rxjava2-bom:2.7.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `libraries.test-boms-micronaut-rxjava3` | `io.micronaut.rxjava3:micronaut-rxjava3-bom:3.7.0` | `io.micronaut.rxjava3:micronaut-rxjava3-bom:4.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.test-boms-micronaut-sql` | `io.micronaut.sql:micronaut-sql-bom:5.3.0` | `io.micronaut.sql:micronaut-sql-bom:7.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `libraries.test-boms-micronaut-validation` | `io.micronaut.validation:micronaut-validation-bom:4.9.0` | `io.micronaut.validation:micronaut-validation-bom:5.0.0-RC2` | `changed` |
| `gradle/libs.versions.toml` | `libraries.testcontainers-spock` | `org.testcontainers:spock:1.21.3` | `org.testcontainers:spock:1.21.4` | `changed` |
| `gradle/libs.versions.toml` | `libraries.tomlj` | `org.tomlj:tomlj:1.1.1` | `org.tomlj:tomlj:1.1.1` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.vertx` | `io.vertx:vertx-core:4.5.17` | `io.vertx:vertx-core:4.5.26` | `changed` |
| `gradle/libs.versions.toml` | `libraries.vertx-webclient` | `io.vertx:vertx-web-client:4.5.17` | `io.vertx:vertx-web-client:4.5.26` | `changed` |
| `gradle/libs.versions.toml` | `libraries.wiremock` | `com.github.tomakehurst:wiremock-jre8:2.33.2` | `com.github.tomakehurst:wiremock-jre8:2.33.2` | `unchanged` |
| `gradle/libs.versions.toml` | `libraries.zacsweers-kct-ksp` | `not present` | `dev.zacsweers.kctfork:ksp:0.12.1` | `added` |
| `gradle/libs.versions.toml` | `versions.awaitility` | `4.3.0` | `4.3.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.bcpkix` | `1.70` | `1.84` | `changed` |
| `gradle/libs.versions.toml` | `versions.blaze` | `1.6.17` | `1.6.18` | `changed` |
| `gradle/libs.versions.toml` | `versions.brotli4j` | `1.18.0` | `1.18.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.bytebuddy` | `1.17.8` | `1.18.8` | `changed` |
| `gradle/libs.versions.toml` | `versions.caffeine` | `2.9.3` | `2.9.3` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.classgraph` | `4.8.181` | `4.8.184` | `changed` |
| `gradle/libs.versions.toml` | `versions.compile-testing` | `0.21.0` | `0.21.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.error_prone_core` | `not present` | `2.48.0` | `added` |
| `gradle/libs.versions.toml` | `versions.errorprone-gradle-plugin` | `not present` | `4.4.0` | `added` |
| `gradle/libs.versions.toml` | `versions.geb` | `7.0` | `7.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.graal-svm` | `23.1.8` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.h2` | `2.2.224` | `2.4.240` | `changed` |
| `gradle/libs.versions.toml` | `versions.hibernate` | `5.5.9.Final` | `5.5.9.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.htmlsanitycheck` | `1.1.6` | `1.1.6` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.htmlunit` | `2.70.0` | `2.70.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.httpcomponents-client` | `4.5.14` | `4.5.14` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.icu4j` | `76.1` | `76.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.jackson2` | `not present` | `2.21.3` | `added` |
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
| `gradle/libs.versions.toml` | `versions.junit4` | `not present` | `4.13.2` | `added` |
| `gradle/libs.versions.toml` | `versions.junit5` | `5.12.2` | `5.12.2` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.log4j` | `2.25.4` | `2.25.4` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.logback` | `1.5.29` | `1.5.32` | `changed` |
| `gradle/libs.versions.toml` | `versions.logbook-netty` | `3.12.2` | `3.12.3` | `changed` |
| `gradle/libs.versions.toml` | `versions.lombok` | `1.18.40` | `1.18.46` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-graal` | `not present` | `25.0.3` | `added` |
| `gradle/libs.versions.toml` | `versions.managed-groovy` | `4.0.28` | `5.0.6` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-jackson` | `2.21.2` | `3.1.3` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-jackson-annotations` | `2.21` | `2.21` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-jackson-databind` | `2.21.2` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.managed-jakarta-annotation-api` | `2.1.1` | `2.1.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-java-parser-core` | `3.27.0` | `3.28.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-jspecify` | `1.0.0` | `1.0.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-kotlin` | `1.9.25` | `2.3.21` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-kotlin-coroutines` | `1.8.1` | `1.10.2` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-kotlin2` | `2.1.21` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.managed-ksp` | `1.9.25-1.0.20` | `2.3.6` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-ksp2` | `2.1.21-2.0.2` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.managed-methvin-directory-watcher` | `0.19.1` | `0.19.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-netty` | `4.2.13.Final` | `4.2.13.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-netty-contrib-multipart` | `1.0.0.Final` | `1.0.0.Final` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-netty-tcnative` | `2.0.75.Final` | `2.0.77.Final` | `changed` |
| `gradle/libs.versions.toml` | `versions.managed-reactive-streams` | `1.0.4` | `1.0.4` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-reactor` | `3.7.12` | `3.7.12` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.managed-snakeyaml` | `2.4` | `2.4` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.micronaut-aws` | `4.11.0` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-build-plugins` | `7.6.4` | `8.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-docs` | `3.0.0` | `3.0.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.micronaut-groovy` | `4.7.0` | `4.7.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.micronaut-kotlin` | `4.6.0` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-reactor` | `3.7.0` | `4.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-rxjava2` | `2.7.0` | `not present` | `removed` |
| `gradle/libs.versions.toml` | `versions.micronaut-rxjava3` | `3.7.0` | `4.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-session` | `4.6.0` | `4.6.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.micronaut-sourcegen` | `1.8.2` | `2.0.0-RC4` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-sql` | `5.3.0` | `7.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-test` | `4.10.2` | `5.0.0-RC1` | `changed` |
| `gradle/libs.versions.toml` | `versions.micronaut-validation` | `4.9.0` | `5.0.0-RC2` | `changed` |
| `gradle/libs.versions.toml` | `versions.mimepull` | `1.10.0` | `1.10.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.native-gradle-plugin` | `0.11.2` | `0.11.4` | `changed` |
| `gradle/libs.versions.toml` | `versions.neo4j-java-driver` | `5.17.0` | `5.17.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.nullaway` | `not present` | `0.13.1` | `added` |
| `gradle/libs.versions.toml` | `versions.okio` | `3.9.1` | `3.9.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.selenium` | `4.27.0` | `4.27.0` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.slf4j` | `2.0.17` | `2.0.17` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.smallrye` | `6.9.2` | `6.9.2` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.sonatype-scan` | `3.0.0` | `3.1.5` | `changed` |
| `gradle/libs.versions.toml` | `versions.spock` | `2.3-groovy-4.0` | `2.4-groovy-5.0` | `changed` |
| `gradle/libs.versions.toml` | `versions.spotbugs` | `4.9.6` | `4.9.8` | `changed` |
| `gradle/libs.versions.toml` | `versions.systemlambda` | `1.2.1` | `1.2.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.testcontainers` | `1.21.3` | `1.21.4` | `changed` |
| `gradle/libs.versions.toml` | `versions.tomlj` | `1.1.1` | `1.1.1` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.vertx` | `4.5.17` | `4.5.26` | `changed` |
| `gradle/libs.versions.toml` | `versions.wiremock` | `2.33.2` | `2.33.2` | `unchanged` |
| `gradle/libs.versions.toml` | `versions.zacsweers-kotlin-compile-testing` | `not present` | `0.12.1` | `added` |
| `gradle/wrapper/gradle-wrapper.properties` | `gradle-wrapper` | `8.14.3` | `9.5.0` | `changed` |

## Release Notes Draft

### Highlights

- Review the categorized commit candidates, version comparison, and high-signal file changes below; promote confirmed user-visible changes here.

### Breaking Changes

- `dbe079493319` Remove dependency to micronaut-rxjava2 (#12489) (Sergio del Amo, 2026-03-14)
- `a38453d5a102` Remove incorrect SafeVarargs (#12420) (Denis Stepanov, 2026-03-02)
- `92aabdb03712` Remove remaining NonNull on NullMarked packages (#12369) (Denis Stepanov, 2026-01-29)
- `2e754096cb2d` Remove TypeThrashingTest (#12199) (Jonas Konrad, 2025-11-19)
- `ba975c3ca78d` Drop support for Kotlin 1.9 (#12164) (Cédric Champeau, 2025-11-04)

### Features

- `d1bed7f7ad8b` Add h2c prior-knowledge client support (#12555) (Jonas Konrad, 2026-05-08)
- `cfa82d22642c` Add jakarta Priority annotation mapper (#12592) (Graeme Rocher, 2026-04-06)
- `3db7caf1594e` Add config import support and importer SPI (#12571) (Graeme Rocher, 2026-04-03)
- `e3256f481f10` Add programmatic retry and circuit breaker APIs (#12585) (Graeme Rocher, 2026-04-01)
- `d5e5caf12d5d` Add regression test for declarative Mono<Void> no-content response (#12550) (Jonas Konrad, 2026-03-28)
- `d993d34f8223` Add regression coverage for blank form request bean values (#12533) (Jonas Konrad, 2026-03-24)
- `49174c950870` Add regression test for zero-length MultipartBody part (#12505) (Jonas Konrad, 2026-03-17)
- `bc0199d6aa28` Add FileCustomizableResponseType body writer (#12481) (Jonas Konrad, 2026-03-14)
- `24a90b52671b` feat(http3): promote HTTP/3 support to stable (#12466) (Jonas Konrad, 2026-03-11)
- `519986e716ac` Add %q and %U access log elements for Netty (#12456) (Jonas Konrad, 2026-03-10)
- `a2d0f71c7fa0` Add @NullMarked to all packages in core-processor (#12345) (Denis Stepanov, 2026-01-15)
- `c6a4d7c57c0d` Add `@NullMarked` to all packages in websocket, router (#12348) (Denis Stepanov, 2026-01-15)
- `b3893d5d269c` Add `@NullMarked` to all packages in `aop` (#12347) (Denis Stepanov, 2026-01-15)
- `d1cd32a78d93` Add `@NullMarked` to all packages in tck modules (#12344) (Denis Stepanov, 2026-01-15)
- `a72ee1b24fa9` Add `@NullMarked` to all packages in context (#12346) (Denis Stepanov, 2026-01-15)
- `0f59c2d21e0a` Add `@NullMarked` to all packages in `http-netty` (#12339) (Denis Stepanov, 2026-01-14)
- `7b5dea7ba817` Add `@NullMarked` to all packages in `http-server-netty` (#12340) (Denis Stepanov, 2026-01-14)
- `368d6610a49e` Add `@NullMarked` to all packages in json/jackson (#12341) (Denis Stepanov, 2026-01-14)
- `9783b1e6d72f` Add `@NullMarked` to all packages in more modules (#12342) (Denis Stepanov, 2026-01-14)
- `25032dca648e` Add `@NullMarked` to all packages in `http-client` (#12338) (Denis Stepanov, 2026-01-13)
- `686adf953ad8` Add `@NullMarked` to all packages in `inject` (#12336) (Denis Stepanov, 2026-01-13)
- `1a64f1859d50` Add `@NullMarked` to all packages in core (#12331) (Denis Stepanov, 2026-01-13)
- `5a48da308a6f` Add `@NullMarked` to all packages in `http` (#12333) (Denis Stepanov, 2026-01-13)
- `11ae717771db` Add explicit @Target to @Internal annotation (#12314) (Ayoub Ait Abdellah, 2026-01-09)
- `29db13455c5b` adds a contract to isEmpty and isNotEmpty methods, so static checkers such as NullAway will know that the methods check for nullability (#12264) (Vladimir Orany, 2026-01-09)
- `ec8ae3ca9cd9` Add bean configurations predicate support (#12277) (Denis Stepanov, 2025-12-17)
- `7bb88cdce009` Support for creating AOP proxies at Runtime if necessary (#12223) (Denis Stepanov, 2025-11-27)
- `db43e2152456` Introduce a Micronaut module descriptor (#12192) (Cédric Champeau, 2025-11-18)
- `77a1b84b5f9e` Add API to access SSL session (#10792) (Jonas Konrad, 2024-05-06)

### Fixes

- `efa14f1a2b08` fix(deps): update dependency com.uber.nullaway:nullaway to v0.13.1 (#12554) (renovate[bot], 2026-05-12)
- `34685fafadac` fix: checkout using github.sha in github_release to avoid tag-moved error (Sergio del Amo, 2026-04-28)
- `a027677c8df6` Correct FormsJacksonAnnotationsTest TCK (#12602) (Denis Stepanov, 2026-04-13)
- `91be869dedeb` fix(deps): update dependency com.google.errorprone:error_prone_core to v2.48.0 (#12552) (renovate[bot], 2026-04-06)
- `07e061d0177e` fix(deps): update dependency net.ltgt.errorprone:net.ltgt.errorprone.gradle.plugin to v4.4.0 (#12562) (renovate[bot], 2026-04-06)
- `08f12219b50b` fix(deps): update vertx to v4.5.26 (#12569) (renovate[bot], 2026-04-01)
- `62defda9c79e` fix(deps): update dependency org.sonatype.gradle.plugins:scan-gradle-plugin to v3.1.5 (#12580) (renovate[bot], 2026-04-01)
- `94d95bb2a8a5` fix(deps): update dependency org.apache.logging.log4j:log4j-core to v2.25.4 (#12584) (renovate[bot], 2026-03-31)
- `2a65d94353be` Correct ScopedValues changes (#12561) (Denis Stepanov, 2026-03-25)
- `4dc4299f8dd0` fix(deps): update dependency com.fasterxml.jackson.core:jackson-databind to v2.21.2 (#12551) (renovate[bot], 2026-03-21)
- `99f175d39270` test: add non-security HttpStatusException regression guard (#12507) (Jonas Konrad, 2026-03-17)
- `603a12d62b45` fix(deps): update kotlin monorepo to v2.3.20 (#12503) (renovate[bot], 2026-03-17)
- `7d1ae0426c53` Fix: Relative redirects not resolved against request URI (#12395) (Artem Likhitskiy, 2026-03-11)
- `acb683550ba2` fix: preserve ssl state on netty client refresh (#12434) (Jonas Konrad, 2026-03-06)
- `b36217758ffe` fix: avoid Path @QueryValue StackOverflow in declarative clients (#12421) (Jonas Konrad, 2026-03-02)
- `f3ebc259db46` test: add regression for @Bindable defaults on config interfaces (#12484) (Graeme Rocher, 2026-03-13)
- `74d209343218` test: add GOAWAY next-request connection regression (#12478) (Jonas Konrad, 2026-03-13)
- `fff04fe4e0cd` fix(deps): update dependency org.projectlombok:lombok to v1.18.44 (#12480) (renovate[bot], 2026-03-13)
- `eb60c6c35f35` fix(http-client-jdk): apply service SSL settings for named JDK clients (#12473) (Jonas Konrad, 2026-03-11)
- `b50709bfbc38` fix(inject-kotlin): preserve boxed getter signature for overridden primitive properties (#12469) (Jonas Konrad, 2026-03-11)
- `70fde380acd6` fix: avoid containsBean cache race during concurrent cache clears (#12462) (Jonas Konrad, 2026-03-11)
- `07c6e7493665` test: add /beans runtime definition collision regression (#12465) (Jonas Konrad, 2026-03-11)
- `0943c09b6aa1` fix(deps): update vertx to v4.5.25 (#12464) (renovate[bot], 2026-03-11)
- `ef3040f16c6e` test: add regression coverage for optional query value multipart streaming (#12454) (Jonas Konrad, 2026-03-10)
- `41451bfa2a43` test: add RequestBean record path-variable regression to HTTP server TCK (#12436) (Jonas Konrad, 2026-03-09)
- `896e3471d8ae` fix: avoid wildcard default content type for responses (#12452) (Jonas Konrad, 2026-03-09)
- `aabc2d6aa730` fix(deps): update netty monorepo to v4.2.10.final (#12448) (renovate[bot], 2026-03-09)
- `a5e04dfb3d7a` fix(deps): update jackson monorepo (#12286) (renovate[bot], 2026-03-06)
- `5378816b4ada` fix(deps): update dependency io.micronaut.sourcegen:micronaut-sourcegen-bom to v2.0.0-m2 (#12349) (renovate[bot], 2026-03-05)
- `f5cc6c222494` fix(deps): update micronaut.test to v5.0.0-snapshot (#12426) (renovate[bot], 2026-03-03)
- `a43dc1677834` fix(deps): update bytebuddy to v1.18.7 (#12417) (renovate[bot], 2026-03-02)
- `107559c0a2dd` fix(deps): update bytebuddy to v1.18.6-jdk6-jdk5 (#12415) (renovate[bot], 2026-03-01)
- `0b9f1cf38f25` fix(deps): update ksp monorepo to v2.3.6 (#12414) (renovate[bot], 2026-02-28)
- `dab3516cf740` fix: prevent denial of service submitting form-url-encoded payload (#12410) (Sergio del Amo, 2026-02-25)
- `192b5523620f` fix(deps): update kotlin monorepo to v2.3.10 (#12404) (renovate[bot], 2026-02-23)
- `411d68324b28` fix(deps): update groovy monorepo to v5.0.4 (#12403) (renovate[bot], 2026-02-22)
- `ae02421bbea5` fix(deps): update dependency org.graalvm.sdk:nativeimage to v23.1.10 (#12402) (renovate[bot], 2026-02-21)
- `f682620104e8` fix(deps): update dependency ch.qos.logback:logback-classic to v1.5.32 (#12392) (renovate[bot], 2026-02-20)
- `e043fa381148` fix(deps): update dependency io.netty:netty-tcnative-boringssl-static to v2.0.75.final (#12400) (renovate[bot], 2026-02-20)
- `f7c3e4447fb4` fix(deps): update bytebuddy to v1.18.5 (#12391) (renovate[bot], 2026-02-17)
- `026f777c3efd` fix(deps): update micronaut.sql to v7.0.0 (#10876) (renovate[bot], 2026-02-12)
- `27e25a2aedf7` fix(deps): update dependency io.micronaut.validation:micronaut-validation-bom to v5.0.0-snapshot (#12307) (renovate[bot], 2026-02-12)
- `d9ab6a848528` fix(deps): update dependency io.micronaut.rxjava3:micronaut-rxjava3-bom to v4.0.0-snapshot (#12304) (renovate[bot], 2026-02-12)
- `f510397c66e2` fix(deps): update dependency io.micronaut.reactor:micronaut-reactor-bom to v4.0.0-snapshot (#12300) (renovate[bot], 2026-02-12)
- `382b56034163` fix(deps): update dependency com.blazebit:blaze-persistence-core-impl to v1.6.18 (#12387) (renovate[bot], 2026-02-11)
- `5f4b1302e642` fix(deps): update bytebuddy to v1.18.4 (#12355) (renovate[bot], 2026-02-11)
- `6c292391ccce` Correct nullability of ConversionService#convertRequired (#12388) (Denis Stepanov, 2026-02-11)
- `f77450d9efbe` Correct "post construct" generation in bean definition writer (#12372) (Denis Stepanov, 2026-01-30)
- `9441472c51c9` fix(deps): update dependency org.sonatype.gradle.plugins:scan-gradle-plugin to v3.1.4 (#12343) (renovate[bot], 2026-01-14)
- `45b7e2350bd0` Correct `@Nullable` and `@NonNull` on arrays (#12320) (Denis Stepanov, 2026-01-13)
- `519b2af17f90` fix(deps): update dependency io.micronaut.sourcegen:micronaut-sourcegen-bom to v1.8.4 (#12291) (renovate[bot], 2026-01-09)
- `6370c6d4e8c0` fix(deps): update vertx to v4.5.23 (#12293) (renovate[bot], 2026-01-09)
- `dd0fb6faf630` fix(deps): update dependency ch.qos.logback:logback-classic to v1.5.24 (#12290) (renovate[bot], 2026-01-09)
- `5b795028c100` fix(deps): update bytebuddy to v1.18.3 (#12284) (renovate[bot], 2025-12-20)
- `0d0d79cac8be` fix(deps): update dependency org.zalando:logbook-netty to v3.12.3 (#12282) (renovate[bot], 2025-12-18)
- `69454791c954` fix(deps): update dependency org.testcontainers:spock to v1.21.4 (#12281) (renovate[bot], 2025-12-18)
- `2a53b7e4bbb6` fix(deps): update dependency ch.qos.logback:logback-classic to v1.5.22 (#12263) (renovate[bot], 2025-12-12)
- `7a985cfe5987` fix(deps): update dependency org.spockframework:spock-core to v2.4-groovy-5.0-snapshot (#12257) (renovate[bot], 2025-12-08)
- `83fcb8bbabd1` fix(deps): update dependency org.projectlombok:lombok to v1.18.42 (#12253) (renovate[bot], 2025-12-07)
- `9feac10c5730` fix(deps): update dependency org.graalvm.sdk:nativeimage to v23.1.9 (#12248) (renovate[bot], 2025-12-06)
- `64bf792729f4` fix(deps): update bytebuddy to v1.18.2 (#12233) (renovate[bot], 2025-12-02)
- `430b813d4bc9` fix(deps): update dependency org.graalvm.buildtools.native:org.graalvm.buildtools.native.gradle.plugin to v0.11.3 (#12221) (renovate[bot], 2025-11-26)
- `46e17753e5c0` fix(deps): update dependency io.micronaut.build.internal:micronaut-gradle-plugins to v7.6.6 (#12214) (renovate[bot], 2025-11-25)
- `619ce140e45e` fix(deps): update dependency io.github.classgraph:classgraph to v4.8.184 (#12213) (renovate[bot], 2025-11-23)
- `1715890a0f77` fix(deps): update dependency com.github.spotbugs:spotbugs-annotations to v4.9.8 (#12212) (renovate[bot], 2025-11-22)
- `ed73acf95111` fix(deps): update dependency com.github.javaparser:javaparser-symbol-solver-core to v3.27.1 (#12210) (renovate[bot], 2025-11-21)
- `18bc29d3a39a` fix(deps): update dependency ch.qos.logback:logback-classic to v1.5.21 (#12186) (renovate[bot], 2025-11-18)
- `5f8441e8cf01` fix(deps): update dependency ch.qos.logback:logback-classic to v1.5.20 (#12162) (renovate[bot], 2025-10-27)
- `850cc27f2f73` fix: Re-add Try-Catch for ConfigurationExceptions To DefaultPropertyPlaceholderResolver (#10798) (Andrew Johnson, 2024-05-08)
- `b23a2e905915` fix(deps): update dependency org.apache.logging.log4j:log4j-core to v2.23.1 (#10791) (renovate[bot], 2024-05-03)

### Security

- `b655c7b11437` Allow `Authentication` as a valid parameter (#12357) (zManu3k, 2026-02-03)
- `8ba85ab6fe51` [CVE-2025-67735] Update managed-netty version to 4.2.9.Final (#12274) (Álvaro Sánchez-Mariscal, 2025-12-16)

### Dependency Updates

- `f47688eafe00` Update managed-groovy version to 5.0.6 (#12669) (Sergio del Amo, 2026-05-12)
- `7bb771aa4428` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-05-06)
- `0302d8500ee6` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-05-03)
- `8a19f5593c2a` Update dependency com.h2database:h2 to v2.4.240 (#11014) (renovate[bot], 2026-05-02)
- `2be67e1550ab` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-04-30)
- `00c44292ca91` Update dependency io.netty:netty-tcnative-boringssl-static to v2.0.77.Final (#12635) (renovate[bot], 2026-04-28)
- `0f1642bdda4d` Update dependency io.micronaut.validation:micronaut-validation-bom to v5.0.0-M2 (#12622) (renovate[bot], 2026-04-23)
- `a0f4e7a3fb25` Update dependency io.micronaut.reactor:micronaut-reactor-bom to v4.0.0-M2 (#12616) (renovate[bot], 2026-04-22)
- `076358f8d9cd` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-04-22)
- `f403651de815` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-04-17)
- `0362d7c90bd1` Update dependency com.github.javaparser:javaparser-symbol-solver-core to v3.28.0 (#12325) (renovate[bot], 2026-04-17)
- `5bdfe757c1e0` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-04-13)
- `8e29c9169b4d` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-04-13)
- `a1a3ac37b4d2` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-04-03)
- `d43aa532941e` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-04-01)
- `77f87a6ffa6d` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-03-25)
- `8e418f75dd7a` chore(deps): update gradle to v9.4.1 (#12536) (renovate[bot], 2026-03-20)
- `5b26943ab107` chore(deps): update gradle to v9.4.0 (#12521) (renovate[bot], 2026-03-19)
- `f1b33d644cc2` chore(deps): update softprops/action-gh-release action to v2.6.1 (#12531) (renovate[bot], 2026-03-19)
- `92a0d59a559a` Run websocket upgrade completion on event loop (#12528) (Jonas Konrad, 2026-03-19)
- `f4ffa365f342` Return 400 for malformed WebSocket upgrade URIs (#12519) (Jonas Konrad, 2026-03-18)
- `0d14882520ee` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-03-14)
- `977658f8e05c` build: graal & graalvm native dependency managed (#12490) (Sergio del Amo, 2026-03-13)
- `900250b8556d` Update graal version to 25.0.2 (#12468) (Sergio del Amo, 2026-03-13)
- `88a7f50d4cc7` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-03-06)
- `5f3dde87193e` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-03-02)
- `efcd058a1095` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-02-25)
- `88c9151e72e1` chore: Bump version to 4.10.17-SNAPSHOT (micronaut-build, 2026-02-25)
- `c454e108dc7b` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-02-20)
- `cf1fa4f50ac4` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-02-19)
- `d0fdbdcf2f3c` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-02-17)
- `ca3009c8fb40` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m17 (#12390) (renovate[bot], 2026-02-17)
- `a896d1a527e3` Update dependency ch.qos.logback:logback-classic to v1.5.29 (#12382) (renovate[bot], 2026-02-10)
- `4381cf51c6e8` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-02-04)
- `d4a56ca5123a` Update native-gradle-plugin version (#12378) (Graeme Rocher, 2026-02-04)
- `e44c2b394ed1` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-01-12)
- `b08000728e99` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m14 (#12324) (renovate[bot], 2026-01-11)
- `d4d5750c7ac6` chore(deps): update graalvm/setup-graalvm action to v1.4.5 (#12322) (renovate[bot], 2026-01-10)
- `9142c0360550` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2026-01-09)
- `e56b9d827283` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2025-12-22)
- `eb56844185fe` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2025-12-17)
- `906e3ea79e1f` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m13 (#12278) (renovate[bot], 2025-12-17)
- `03567ae95f4b` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2025-12-16)
- `f1c426ebb87a` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2025-12-11)
- `5ffdf3a0d50c` Revert "fix(deps): update dependency org.spockframework:spock-core to v2.4-gr…" (#12261) (Denis Stepanov, 2025-12-11)
- `afa766906de7` chore(deps): update graalvm/setup-graalvm action to v1.4.4 (#12245) (renovate[bot], 2025-12-05)
- `1ca0fc980a6a` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2025-12-03)
- `9004770b3376` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m12 (#12230) (renovate[bot], 2025-12-01)
- `d60e98caefc7` chore: Bump version to 5.0.0-SNAPSHOT (micronaut-build, 2025-11-28)
- `e1b7f14138c3` chore(deps): update graalvm/setup-graalvm action to v1.4.3 (#12228) (renovate[bot], 2025-11-28)
- `b712c3b36dd5` Upgrade to Groovy 5 (#12170) (Cédric Champeau, 2025-11-25)
- `614b89a90cf0` build: accept version and library regiression from netty-contrib-multipart (#12219) (Sergio del Amo, 2025-11-25)
- `d0077ad74811` chore(deps): update gradle to v9.2.1 (#12204) (renovate[bot], 2025-11-20)
- `8aba75abbefd` chore(deps): update softprops/action-gh-release action to v2.4.2 (#12174) (renovate[bot], 2025-11-11)
- `85e15a891cae` chore(deps): update plugin io.micronaut.build.shared.settings to v8.0.0-m9 (#12166) (renovate[bot], 2025-11-06)
- `9ded33c6b752` chore(deps): update plugin io.micronaut.build.shared.settings to v7.6.6 (#12155) (renovate[bot], 2025-10-28)
- `5e34abedf2a9` chore(deps): update graalvm/setup-graalvm action to v1.4.2 (#12160) (renovate[bot], 2025-10-25)
- `7a072167cf35` chore: Bump version to 4.4.10-SNAPSHOT (micronaut-build, 2024-05-09)
- `0227c0d73416` build: Use only one jackson version (#10795) (Sergio del Amo, 2024-05-03)

### Documentation

- `39c74acd625c` docs: clarify JsonMapper and ObjectMapper guidance (#12525) (Jonas Konrad, 2026-03-19)
- `234bd7a69d14` docs: add address resolver group snippet examples (#12474) (Jonas Konrad, 2026-03-13)
- `141801d51f78` Docs: Add note about YAML reserved words in ConfigurationProperties (#12427) (Nikita Nagar, 2026-03-05)

### Internal

- `19974d9d2c92` test: close dual-protocol http client in NettyHttpServerSpec (#12424) (Jonas Konrad, 2026-03-02)
- `5d65047a3d05` test: reduce test pollution with spec.name (#12208) (Sergio del Amo, 2025-11-20)
- `13904177bb29` build: disable htmlSanityCheck (#12198) (Sergio del Amo, 2025-11-18)
- `cee37a20f0eb` test: ignore LoomCarrierSpec for MacOS (#12197) (Sergio del Amo, 2025-11-18)
- `7dc245eb6bad` test: ProxyBackpressureTest run localy reduced cvssource (#12196) (Sergio del Amo, 2025-11-18)
- `67aa0d98b0e9` test: isolate ConstantPropertySourceSpec in its own module (#12195) (Sergio del Amo, 2025-11-18)
- `e983985db0fb` ci: projectVersion=5.0.0-SNAPSHOT [ci skip] cici (Sergio del Amo, 2024-02-06)

### Review Candidates

- `54d1ebd157bf` [skip ci] Release v5.0.0 (micronaut-build, 2026-05-13)
- `568335afba64` Update core to latest versions (#12675) (Sergio del Amo, 2026-05-13)
- `55d886312292` git ignore .kotlin (Sergio del Amo, 2026-05-13)
- `bf6728cdcf03` Fix Kotlin default dispatch for inherited methods (#12670) (Issam Liqali, 2026-05-12)
- `01dfdbbe6763` Fix KSP not visiting inner classes (#12673) (Denis Stepanov, 2026-05-12)
- `a4e3e2e83c8b` sync .agents and workflows (Sergio del Amo, 2026-05-11)
- `7eab107eb6c2` [skip ci] Release v5.0.0-RC2 (micronaut-build, 2026-05-06)
- `aa85b75e2341` Update common files (#12660) # Conflicts: #	MAINTAINING.md (micronaut-build, 2026-05-06)
- `ad34b7469f15` Update Netty to 4.2.13.Final (#12662)	http/build.gradle.kts (Jonas Konrad, 2026-05-06)
- `9b00f087a4e1` Update groovy monorepo to v5.0.5 (#12647) (renovate[bot], 2026-05-06)
- `b220135b2f78` Update kotlin monorepo to v2.3.21 (#12656) (renovate[bot], 2026-05-04)
- `a99429daf14e` [core] Update common files for branch 5.0.x (#12657) (micronaut-build, 2026-05-04)
- `1021f648c0f7` fix #12651: reuse underlying HttpClient in toBlocking() to prevent thread leak (#12652) (Alexey Naborshchikov, 2026-05-03)
- `92dc78aa18cb` [skip ci] Release v5.0.0-RC1 (micronaut-build, 2026-05-03)
- `027b09b9485a` Update jackson monorepo (#12648) (renovate[bot], 2026-05-02)
- `546aafaab86c` [core] Update common files for branch 5.0.x (#12643) (micronaut-build, 2026-05-02)
- `b673cdd4c5b8` [skip ci] Release v5.0.0-M26 (micronaut-build, 2026-04-30)
- `8b03ad300b78` Raise test-library baseline to Java 25 (#12644) (Graeme Rocher, 2026-04-30)
- `666f7f2f0d4c` Fix recursive ConcurrentHashMap.computeIfAbsent in RefreshScope.getOrCreate() (#12582) (Copilot, 2026-04-29)
- `556b9ef0bb0b` Merge commit from fork (Sergio del Amo, 2026-04-28)
- `4194d81b05e1` Merge commit from fork (Sergio del Amo, 2026-04-28)
- `1be5f8cefb80` Async Http Client (#12629) (Denis Stepanov, 2026-04-27)
- `b2dbfa632ec1` Update bcpkix to jdk18on (#12624) (Jonas Konrad, 2026-04-22)
- `c54a3975063e` [skip ci] Release v5.0.0-M24 (micronaut-build, 2026-04-22)
- `b92c19824840` Avoid iterating lazy property sources for config imports (#12628) (Graeme Rocher, 2026-04-22)
- `357eb4816829` [skip ci] Release v5.0.0-M23 (micronaut-build, 2026-04-17)
- `1dbb7d5d59d2` Expand thread-selection behavior (#12439) (Jonas Konrad, 2026-04-17)
- `6ec2e242eb38` Change default for CrossOrigin.allowCredentials (#12614) (Jonas Konrad, 2026-04-17)
- `5e575365a54c` Update bytebuddy to v1.18.8 (#12613) (renovate[bot], 2026-04-17)
- `c1733e1c5e6c` Make @Retryable capture Exception by default (#12141) (Shreyank Bhat, 2026-04-14)
- `b3898761d380` [skip ci] Release v5.0.0-M22 (micronaut-build, 2026-04-13)
- `922f389a8bf2` [skip ci] Release v5.0.0-M21 (micronaut-build, 2026-04-13)
- `851c00bd0149` Fix whatsNew.adoc section heading levels and "scoped values" terminology (#12603) (Graeme Rocher, 2026-04-09)
- `2792e2bf9fba` Change propagated context default to thread local (#12605) (Graeme Rocher, 2026-04-09)
- `947533f08fdb` [skip ci] Release v5.0.0-M20 (micronaut-build, 2026-04-03)
- `b8570dc5e675` [skip ci] Release v5.0.0-M19 (micronaut-build, 2026-04-01)
- `3ab3ebd447e5` Merge branch '4.10.x' into 5.0.x (Sergio del Amo, 2026-03-31)
- `c9efb634a0bc` [skip ci] Release v5.0.0-M18 (micronaut-build, 2026-03-25)
- `9b993a00d065` Clarify MutableHttpMessage header semantics (#12566) (Jonas Konrad, 2026-03-24)
- `241bc0d78459` Preserve BeanRegistration identifier qualifiers on singleton reuse (#12564) (Jonas Konrad, 2026-03-24)
- `8d64f7827296` Preserve HEAD content-length for proxied responses (#12563) (Jonas Konrad, 2026-03-24)
- `91ae2ec3bf68` Preserve runtime annotations on intercepted proxy methods (#12544) (Jonas Konrad, 2026-03-24)
- `157f4b2d3013` Guard Jackson constructType against incomplete generics (#12558) (Jonas Konrad, 2026-03-24)
- `7564f54bacb5` Clarify @Controller port javadoc (#12534) (Jonas Konrad, 2026-03-24)
- `8d5492aad7d8` Clarify AnnotationMapper classpath requirements (#12542) (Jonas Konrad, 2026-03-24)
- `a7955f4cc502` Preserve empty string elements when binding string query lists (#12546) (Jonas Konrad, 2026-03-23)
- `53af04a2bdea` Clarify bootstrap requirements for custom config clients (#12538) (Jonas Konrad, 2026-03-23)
- `6a11a05950f3` Propagation context - scope values (#12509) (Denis Stepanov, 2026-03-19)
- `822d150d79c5` Expose additional Netty HTTP client parser limits (#12529) (Jonas Konrad, 2026-03-18)
- `6a021ec3c793` Handle long Lombok builder introspection names (#12526) (Jonas Konrad, 2026-03-18)
- `6c2a3bdd3738` Handle health monitor scheduler rejection during shutdown (#12527) (Jonas Konrad, 2026-03-18)
- `e6683da13a9e` Preserve order for EachBean delegates (#12520) (Jonas Konrad, 2026-03-18)
- `2ef785d83251` Clarify Retryable capturedException Javadoc (#11750) (#12508) (Jonas Konrad, 2026-03-17)
- `54a5fc84fc81` Clarify max header size documentation (#11626) (#12511) (Jonas Konrad, 2026-03-17)
- `8169f7f68e30` Relax FormBindingDeadlockTest JSON assertion (#12499) (Jonas Konrad, 2026-03-17)
- `37df660d1746` Fix checkstyle errors and warnings (#12497) (Copilot, 2026-03-16)
- `ad5409603fb7` [skip ci] Release v5.0.0-M17 (micronaut-build, 2026-03-14)
- `cfae408836fe` Fix loom carrier native image startup on GraalVM 25 (#12418) (Jonas Konrad, 2026-03-02)
- `45c481af3226` Make ClassImport repeatable (#12485) (Jonas Konrad, 2026-03-13)
- `d274f5315cb8` Propagate context for default error fallback logging (#12471) (Jonas Konrad, 2026-03-13)
- `302138ad2755` Fix reactor http client retry resubscription (#12470) (Jonas Konrad, 2026-03-11)
- `ccd79fef650c` Stabilize JsonStreamSpec streaming request tests (#12458) (Jonas Konrad, 2026-03-11)
- `fd5e1cb6e0d9` Fix request context availability in coroutine context factories (#12461) (Jonas Konrad, 2026-03-11)
- `c0b2f345121c` Changes to support Micronaut processors as a Native Image (#12449) (Graeme Rocher, 2026-03-09)
- `25f3ba8ad85a` Fix flaky HttpClientTraceLoggingSpec log assertion (#12442) (Jonas Konrad, 2026-03-06)
- `3d5eae218bc1` [skip ci] Release v5.0.0-M16 (micronaut-build, 2026-03-06)
- `e7dc0080bd65` Minor Changes to support Truffle polyglot languages (#12435) (Graeme Rocher, 2026-03-06)
- `a6c7d4764ac6` Fix identification getters / setters for properties with second upper case symbol. For example eTemperature (#10130) (altro3, 2026-03-06)
- `3f70a15ae1b9` Document @RouteCondition annotation for conditional routing (#12428) (Copilot, 2026-03-05)
- `29c68cc5851c` Merge commit from fork (Sergio del Amo, 2026-03-04)
- `de8d160e1383` fix @EachProperty env entry lookup for hyphenated prefixes (#12419) (Jonas Konrad, 2026-03-03)
- `d2c9531de98e` [skip ci] Release v5.0.0-M15 (micronaut-build, 2026-03-02)
- `c47adf7da045` Fail fast on duplicate configuration resources (with configurable merge/first-match) (#12383) (Graeme Rocher, 2026-03-02)
- `32d8a6ce5767` [skip ci] Release v5.0.0-M14 (micronaut-build, 2026-02-25)
- `8e573277d43e` [skip ci] Release v4.10.16 (micronaut-build, 2026-02-25)
- `76ab67dcea5f` Jackson2 annotation support (#12408) (Jonas Konrad, 2026-02-25)
- `07fe46f08e49` application/x-yaml -> application/yaml (#10613) (altro3, 2026-02-23)
- `9b0a2e4ae7f4` [skip ci] Release v5.0.0-M13 (micronaut-build, 2026-02-20)
- `bc08a43e0ace` Fix executor fallback by allowing null-named UserExecutorConfiguration (#12401) (issam liqali, 2026-02-20)
- `eaedb2b726f1` Refactor multipart (#12246) (Jonas Konrad, 2026-02-20)
- `cdf7883de4eb` [skip ci] Release v5.0.0-M12 (micronaut-build, 2026-02-19)
- `accfa6878cf6` don’t cache failures until the context is running (#12397) (Sergio del Amo, 2026-02-19)
- `094f031ae658` [skip ci] Release v5.0.0-M11 (micronaut-build, 2026-02-17)
- `a884c6459366` annotation valueMapper can return null (#12393) (Sergio del Amo, 2026-02-17)
- `a8af7d8e6230` Merge branch '4.10.x' into 5.0.x (Sergio del Amo, 2026-02-11)
- `a6996b5abbd6` [skip ci] Release v5.0.0-M10 (micronaut-build, 2026-02-04)
- `a3f9cb91d6f4` Generation of JSON schema from Micronaut Configuration Properties (#12377) (Graeme Rocher, 2026-02-04)
- `a8eff7843a54` fix javadoc (Graeme Rocher, 2026-02-04)
- `302cd2bc418b` Integrate NullAway for whole project (#12368) (Denis Stepanov, 2026-01-28)
- `1d3eb67a3a17` Integrate NullAway for http-server, http-netty (#12367) (Denis Stepanov, 2026-01-26)
- `9a57293acba4` Integrate NullAway and Jspecify NullMarked for http-client-core (#12365) (Denis Stepanov, 2026-01-24)
- `fe50e0fd3c7f` Integrate NullAway for http-client (#12363) (Denis Stepanov, 2026-01-23)
- `faf6ff0c8827` [skip ci] Release v5.0.0-M9 (micronaut-build, 2026-01-23)
- `d5ee4fa0699c` Fix environment missing in configuration packages require conditions (#12362) (Denis Stepanov, 2026-01-23)
- `c33464f2df6c` Integrate NullAway for context, http, inject router (#12360) (Denis Stepanov, 2026-01-22)
- `d47002ad0b6c` Integrate NullAway for core module only (#12354) (Denis Stepanov, 2026-01-17)
- `4d94b9d37460` micronaut-sourcegen = "2.0.0-M1" (Sergio del Amo, 2026-01-14)
- `ce99bd6e9fd7` micronaut-kotlin = "4.7.0" (Sergio del Amo, 2026-01-14)
- `43268aa34378` micronaut-reactor = "4.0.0-M1" (Sergio del Amo, 2026-01-14)
- `bfd1c99b5550` micronaut-rxjava3 = "4.0.0-M1" (Sergio del Amo, 2026-01-14)
- `353c6a97d628` micronaut-rxjava2 = "2.9.0" (Sergio del Amo, 2026-01-14)
- `8ac4eb07ed92` micronaut-validation = "5.0.0-M1" (Sergio del Amo, 2026-01-14)
- `a4b8b54f5a43` micronaut-test = "5.0.0-M3" (Sergio del Amo, 2026-01-14)
- `96da29ea296f` micronaut-sql = "7.0.0-M4" (Sergio del Amo, 2026-01-14)
- `cc97ae3e3725` Merge branch '4.10.x' into 5.0.x (Sergio del Amo, 2026-01-14)
- `76246d7053ec` [skip ci] Release v5.0.0-M8 (micronaut-build, 2026-01-12)
- `8d229d7c1b49` Fixed refresh of bootstrap property sources (#12289) (Milenko Supic, 2026-01-12)
- `610bf9cfcb68` [skip ci] Release v5.0.0-M7 (micronaut-build, 2026-01-09)
- `aac0b74a9066` Update to Kotlin 2.3 and use ZacSweers' kotlin-compile-testing (#12318) (Sergio del Amo, 2026-01-09)
- `b6cd031fc742` [skip ci] Release v5.0.0-M6 (micronaut-build, 2025-12-22)
- `353945d1519d` Fixed usage of custom environments in the bootstrap context (#12287) (Milenko Supic, 2025-12-22)
- `c16c8be43d70` [skip ci] Release v5.0.0-M5 (micronaut-build, 2025-12-17)
- `db65cd022ec4` Fix context beans are not singleton in some cases (#12276) (Denis Stepanov, 2025-12-16)
- `8cefb384dee2` [skip ci] Release v5.0.0-M4 (micronaut-build, 2025-12-16)
- `ff3ab6f0f684` Spock 2.4 (#12269) (Sergio del Amo, 2025-12-15)
- `c2293fb97f5d` [skip ci] Release v5.0.0-M3 (micronaut-build, 2025-12-11)
- `200695d334aa` Application context improvements (#12259) (Denis Stepanov, 2025-12-11)
- `4c87700a2875` Update common files (#12249) (micronaut-build, 2025-12-09)
- `ce4f6e91bdbb` create JsonMapper.Builder as prototype bean (#12239) (Sergio del Amo, 2025-12-04)
- `6093fb235535` Groovy 5.0.3 (#12241) (Sergio del Amo, 2025-12-04)
- `e57a127b7dd3` [skip ci] Release v5.0.0-M2 (micronaut-build, 2025-12-03)
- `b01f693b4226` Match jackson feature names and add config for remaining features (#12237) (Jonas Konrad, 2025-12-03)
- `df4c75e92740` Prepare JsonMapper for Jackson 3 and ReadBuffer (#12236) (Jonas Konrad, 2025-12-02)
- `25783953daf2` Pass HttpRequest to getLoadBalancerDiscriminator() (#12173) (Shreyank Bhat, 2025-12-02)
- `3b05c00e3568` [skip ci] Release v5.0.0-M1 (micronaut-build, 2025-11-28)
- `495090547e16` `RuntimeProxy` can be `@Retention(SOURCE)` to eliminate the annotation (#12227) (Denis Stepanov, 2025-11-27)
- `24bf66a0d4ac` Update common files (#12225) (micronaut-build, 2025-11-27)
- `fbbcac9e7566` Update to jackson 3 (#12165) (Shreyank Bhat, 2025-11-26)
- `cec2b9889871` JSpecify @Nullable with @QueryValue constructor parameter (#12216) (Sergio del Amo, 2025-11-26)
- `6d221cfc8e32` Refactor `InterceptorRegistry` to use `@NullMarked` (#12224) (Denis Stepanov, 2025-11-26)
- `94a81175a023` breaks: del BeanIntrospectionModule (#12207) (Jonas Konrad, 2025-11-26)
- `ff4cbf12fb80` executable method processor and eager initialization (#12180) (Sergio del Amo, 2025-11-26)
- `a638f98eda2f` use Jspecify annotations in APIs (#12200) (Sergio del Amo, 2025-11-24)
- `95d68716b8d2` Improvements to runtime annotation processors (#12068) (Denis Stepanov, 2025-11-20)
- `9f70586cf35e` Fix missing annotations with `RECORD_COMPONENT` target (#12184) (Denis Stepanov, 2025-11-19)
- `c83900013bee` Update common files (#12178) (micronaut-build, 2025-11-18)
- `38821dd39bd9` Fix lookup of annotation processors in Java 25 (#12175) (Cédric Champeau, 2025-11-11)
- `ac6e45bebada` Update common files (#12169) (micronaut-build, 2025-11-06)
- `510698db8c7d` replace kotlinOptions with compilerOptions (Sergio del Amo, 2025-10-29)
- `cc9f8754fc37` Java 21 instead of Java 17 (Sergio del Amo, 2025-10-29)
- `ef50412ef9ba` JavaVersion.VERSION_21 instead of JavaVersion.VERSION_17 (Sergio del Amo, 2025-10-29)
- `da62873dbec7` JvmTarget.JVM_21 instead of JvmTarget.JVM_17 (Sergio del Amo, 2025-10-29)
- `861d25408451` Merge branch '4.10.x' into 5.0.x (Sergio del Amo, 2025-10-29)
- `6ef884a0cb6b` Update common files (#12156) (micronaut-build, 2025-10-28)
- `03d4eab47abc` javadoc: since not see (Sergio del Amo, 2025-10-22)
- `dd5a043da1c0` Merge branch '4.10.x' into 5.0.x (Sergio del Amo, 2025-10-22)
- `b44aa99bbb42` Precalculate replaces at compilation time (#12086) (Denis Stepanov, 2025-10-07)
- `f6f2f432f07e` Isolate tests + fix looking for all beans (#12076) (Denis Stepanov, 2025-10-01)
- `269961f5a755` Bean context improvements (#12066) (Denis Stepanov, 2025-09-28)
- `a446d2452dab` Avoid using service loading accessible classes (#12067) (Denis Stepanov, 2025-09-25)
- `5f8c01c7333b` Improvements to bean context qualifiers (#12053) (Denis Stepanov, 2025-09-17)
- `e79318e97cca` Precalculate indexes and isParallel for beans (#12050) (Denis Stepanov, 2025-09-15)
- `3f2c85cbd360` Improvements to the bean context in v5 (#12045) (Denis Stepanov, 2025-09-12)
- `83290c6af556` Merge branch '4.10.x' into 5.0.x (Sergio del Amo, 2025-09-12)
- `b0a07f9a0f31` Merge branch '4.7.x' into 5.0.x (Sergio del Amo, 2024-08-16)
- `c115c931725c` [skip ci] Release v4.4.9 (micronaut-build, 2024-05-09)
- `3c11e5d9fdd1` Fix file uploads beyond MMAP_SEGMENT_SIZE (#10793) (Jonas Konrad, 2024-05-06)
- `d03d492704c2` allow registering bean definitions prior to startup (#10800) (Graeme Rocher, 2024-05-07)
- `6ef098e0fc7d` Merge branch '4.5.x' into 5.0.x (Sergio del Amo, 2024-05-03)
- `e8e32111dd5c` Merge branch '4.5.x' into 5.0.x (Sergio del Amo, 2024-04-30)
- `fc1473cd3597` Merge branch '4.5.x' into 5.0.x (Sergio del Amo, 2024-04-22)
- `3894cebaa376` Merge branch '4.5.x' into 5.0.x (Sergio del Amo, 2024-04-18)
- `9a8389a7a338` Merge branch '4.5.x' into 5.0.x (Sergio del Amo, 2024-04-07)

## Changed Files

### Build and Dependencies

- `A` .agents/skills/gradle/SKILL.md
- `A` .agents/skills/gradle/references/gradle-best-practices.md
- `A` .agents/skills/gradle/references/micronaut-build-plugins.md
- `M` .github/workflows/gradle.yml
- `M` aop/build.gradle.kts
- `M` benchmarks/build.gradle.kts
- `M` buffer-netty/build.gradle.kts
- `M` build.gradle
- `M` buildSrc/build.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.convention-base.gradle
- `M` buildSrc/src/main/groovy/io.micronaut.build.internal.convention-library.gradle
- `A` buildSrc/src/main/groovy/io.micronaut.build.internal.convention-nullaway.gradle
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
- `A` core/src/main/java/io/micronaut/core/version/annotation/package-info.java
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

- `A` .agents/skills/docs/SKILL.md
- `A` .agents/skills/docs/references/control-panel-patterns.md
- `A` .agents/skills/docs/references/micronaut-docs-providers.md
- `A` .agents/skills/guides/SKILL.md
- `A` .agents/skills/guides/references/guide-authoring-conventions.md
- `A` .agents/skills/guides/references/guide-inventory.md
- `A` .agents/skills/guides/references/pdf-export-and-pr.md
- `A` .agents/skills/guides/references/repository-workflow.md
- `M` .github/workflows/release.yml

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
- `M` .github/workflows/sonatype.yml
- `M` .gitignore
- `A` .sdkmanrc
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
- `A` aop/src/main/java/io/micronaut/aop/internal/intercepted/package-info.java
- `R078` aop/src/main/java/io/micronaut/aop/internal/package-info.java
- `M` aop/src/main/java/io/micronaut/aop/kotlin/KotlinInterceptedMethod.java
- `R078` aop/src/main/java/io/micronaut/aop/kotlin/package-info.java
- `M` aop/src/main/java/io/micronaut/aop/package-info.java
- `A` aop/src/main/java/io/micronaut/aop/runtime/DefaultRuntimeProxyDefinition.java
- `A` aop/src/main/java/io/micronaut/aop/runtime/RuntimeProxy.java
- `R051` aop/src/main/java/io/micronaut/aop/runtime/RuntimeProxyCreator.java
- `A` aop/src/main/java/io/micronaut/aop/runtime/RuntimeProxyDefinition.java
- `A` aop/src/main/java/io/micronaut/aop/runtime/package-info.java
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
- `A` context-propagation/src/main/java/io/micronaut/context/propagation/instrument/execution/package-info.java
- `M` context-propagation/src/main/java/io/micronaut/context/propagation/slf4j/MdcPropagationContext.java
- `A` context-propagation/src/main/java/io/micronaut/context/propagation/slf4j/package-info.java
- `A` context/src/main/java/io/micronaut/context/propagation/PropagatedContextConfigurationProperties.java
- `A` context/src/main/java/io/micronaut/context/time/package-info.java
- `M` context/src/main/java/io/micronaut/logging/PropertiesLoggingLevelsConfigurer.java
- `M` context/src/main/java/io/micronaut/logging/impl/Log4jLoggingSystem.java
- `M` context/src/main/java/io/micronaut/logging/impl/LogbackLoggingSystem.java
- `M` context/src/main/java/io/micronaut/logging/impl/LogbackUtils.java
- `A` context/src/main/java/io/micronaut/logging/impl/package-info.java
- `R078` context/src/main/java/io/micronaut/logging/package-info.java
- `M` context/src/main/java/io/micronaut/runtime/ApplicationConfiguration.java
- `M` context/src/main/java/io/micronaut/runtime/EmbeddedApplication.java
- `M` context/src/main/java/io/micronaut/runtime/Micronaut.java
- `M` context/src/main/java/io/micronaut/runtime/beans/MapperIntroduction.java
- `M` context/src/main/java/io/micronaut/runtime/beans/MapperMethodProcessor.java
- `A` context/src/main/java/io/micronaut/runtime/beans/package-info.java
- `M` context/src/main/java/io/micronaut/runtime/context/CompositeMessageSource.java
- `M` context/src/main/java/io/micronaut/runtime/context/env/ConfigurationIntroductionAdvice.java
- `M` context/src/main/java/io/micronaut/runtime/context/env/package-info.java
- `A` context/src/main/java/io/micronaut/runtime/context/package-info.java
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
- `A` context/src/main/java/io/micronaut/runtime/graceful/package-info.java
- `M` context/src/main/java/io/micronaut/runtime/package-info.java
- `M` context/src/main/java/io/micronaut/runtime/server/event/package-info.java
- `M` context/src/main/java/io/micronaut/runtime/server/package-info.java
- `A` context/src/main/java/io/micronaut/runtime/server/watch/event/package-info.java
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
- `A` context/src/main/java/io/micronaut/scheduling/executor/ThreadSelectionConfiguration.java
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
- `A` core-processor/src/main/java/io/micronaut/aop/mapper/package-info.java
- `M` core-processor/src/main/java/io/micronaut/aop/writer/AopProxyWriter.java
- `A` core-processor/src/main/java/io/micronaut/aop/writer/ProxyingBeanDefinitionWriter.java
- `A` core-processor/src/main/java/io/micronaut/aop/writer/RuntimeProxyBeanDefinitionWriter.java
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
- `A` core-processor/src/main/java/io/micronaut/expressions/context/package-info.java
- `A` core-processor/src/main/java/io/micronaut/expressions/package-info.java
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
- `A` core-processor/src/main/java/io/micronaut/expressions/parser/ast/access/package-info.java
- `A` core-processor/src/main/java/io/micronaut/expressions/parser/ast/collection/package-info.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/conditional/TernaryExpression.java
- `A` core-processor/src/main/java/io/micronaut/expressions/parser/ast/conditional/package-info.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/literal/BoolLiteral.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/literal/DoubleLiteral.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/literal/FloatLiteral.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/literal/IntLiteral.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/literal/LongLiteral.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/literal/NullLiteral.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/literal/StringLiteral.java
- `A` core-processor/src/main/java/io/micronaut/expressions/parser/ast/literal/package-info.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/operator/binary/BinaryOperator.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/operator/binary/ComparablesComparisonOperation.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/operator/binary/InstanceofOperator.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/operator/binary/MatchesOperator.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/operator/binary/NumericComparisonOperation.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/operator/binary/RelationalOperator.java
- `A` core-processor/src/main/java/io/micronaut/expressions/parser/ast/operator/binary/package-info.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/operator/unary/EmptyOperator.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/operator/unary/NegOperator.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/operator/unary/NotOperator.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/operator/unary/PosOperator.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/operator/unary/UnaryOperator.java
- `A` core-processor/src/main/java/io/micronaut/expressions/parser/ast/operator/unary/package-info.java
- `A` core-processor/src/main/java/io/micronaut/expressions/parser/ast/package-info.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/types/TypeIdentifier.java
- `A` core-processor/src/main/java/io/micronaut/expressions/parser/ast/types/package-info.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/util/EvaluatedExpressionCompilationUtils.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/ast/util/TypeDescriptors.java
- `A` core-processor/src/main/java/io/micronaut/expressions/parser/ast/util/package-info.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/compilation/ExpressionCompilationContext.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/compilation/ExpressionVisitorContext.java
- `A` core-processor/src/main/java/io/micronaut/expressions/parser/compilation/package-info.java
- `A` core-processor/src/main/java/io/micronaut/expressions/parser/exception/package-info.java
- `A` core-processor/src/main/java/io/micronaut/expressions/parser/package-info.java
- `M` core-processor/src/main/java/io/micronaut/expressions/parser/token/Tokenizer.java
- `A` core-processor/src/main/java/io/micronaut/expressions/parser/token/package-info.java
- `A` core-processor/src/main/java/io/micronaut/expressions/util/package-info.java
- `M` core-processor/src/main/java/io/micronaut/inject/annotation/AbstractAnnotationMetadataBuilder.java
- `M` core-processor/src/main/java/io/micronaut/inject/annotation/AnnotationMetadataGenUtils.java
- `M` core-processor/src/main/java/io/micronaut/inject/annotation/AnnotationMetadataWriter.java
- `M` core-processor/src/main/java/io/micronaut/inject/annotation/AnnotationRemapper.java
- `M` core-processor/src/main/java/io/micronaut/inject/annotation/PackageRenameRemapper.java
- `M` core-processor/src/main/java/io/micronaut/inject/annotation/internal/AndroidxNullableTransformer.java
- `M` core-processor/src/main/java/io/micronaut/inject/annotation/internal/FindBugsRemapper.java
- `A` core-processor/src/main/java/io/micronaut/inject/annotation/internal/JakartaPriorityAnnotationMapper.java
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
- `R083` core-processor/src/main/java/io/micronaut/inject/annotation/package-info.java
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
- `A` core-processor/src/main/java/io/micronaut/inject/ast/beans/package-info.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/package-info.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/utils/AstBeanPropertiesUtils.java
- `M` core-processor/src/main/java/io/micronaut/inject/ast/utils/EnclosedElementsQuery.java
- `A` core-processor/src/main/java/io/micronaut/inject/ast/utils/package-info.java
- `M` core-processor/src/main/java/io/micronaut/inject/beans/visitor/EntityReflectiveAccessAnnotationMapper.java
- `M` core-processor/src/main/java/io/micronaut/inject/beans/visitor/JsonCreatorAnnotationMapper.java
- `M` core-processor/src/main/java/io/micronaut/inject/beans/visitor/MapperAnnotationMapper.java
- `M` core-processor/src/main/java/io/micronaut/inject/beans/visitor/MapperVisitor.java
- `M` core-processor/src/main/java/io/micronaut/inject/beans/visitor/package-info.java
- `A` core-processor/src/main/java/io/micronaut/inject/beans/visitor/persistence/package-info.java
- `M` core-processor/src/main/java/io/micronaut/inject/configuration/ConfigurationMetadata.java
- `M` core-processor/src/main/java/io/micronaut/inject/configuration/ConfigurationMetadataBuilder.java
- `M` core-processor/src/main/java/io/micronaut/inject/configuration/ConfigurationUtils.java
- `A` core-processor/src/main/java/io/micronaut/inject/configuration/JsonSchemaConfigurationMetadataWriter.java
- `M` core-processor/src/main/java/io/micronaut/inject/configuration/PropertyMetadata.java
- `M` core-processor/src/main/java/io/micronaut/inject/configuration/builder/ConfigurationBuilderPropertyDefinition.java
- `A` core-processor/src/main/java/io/micronaut/inject/configuration/builder/package-info.java
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
- `A` core-processor/src/main/java/io/micronaut/inject/utils/package-info.java
- `M` core-processor/src/main/java/io/micronaut/inject/visitor/BeanElementVisitor.java
- `M` core-processor/src/main/java/io/micronaut/inject/visitor/BeanElementVisitorLoader.java
- `M` core-processor/src/main/java/io/micronaut/inject/visitor/ElementPostponedToNextRoundException.java
- `M` core-processor/src/main/java/io/micronaut/inject/visitor/PackageElementVisitor.java
- `M` core-processor/src/main/java/io/micronaut/inject/visitor/TypeElementVisitor.java
- `M` core-processor/src/main/java/io/micronaut/inject/visitor/VisitorContext.java
- `M` core-processor/src/main/java/io/micronaut/inject/visitor/package-info.java
- `A` core-processor/src/main/java/io/micronaut/inject/visitor/util/package-info.java
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
- `A` core-processor/src/main/java/io/micronaut/validation/visitor/async/package-info.java
- `M` core-processor/src/main/java/io/micronaut/validation/visitor/package-info.java
- `M` core-processor/src/main/resources/META-INF/services/io.micronaut.inject.annotation.AnnotationMapper
- `M` core-processor/src/main/resources/META-INF/services/io.micronaut.inject.configuration.ConfigurationMetadataWriter
- `M` core-reactive/src/main/java/io/micronaut/core/async/ReactiveStreamsTypeInformationProvider.java
- `R071` core-reactive/src/main/java/io/micronaut/core/async/converters/package-info.java
- `M` core-reactive/src/main/java/io/micronaut/core/async/package-info.java
- `M` core-reactive/src/main/java/io/micronaut/core/async/processor/SingleSubscriberProcessor.java
- `M` core-reactive/src/main/java/io/micronaut/core/async/processor/package-info.java
- `M` core-reactive/src/main/java/io/micronaut/core/async/propagation/ReactivePropagation.java
- `M` core-reactive/src/main/java/io/micronaut/core/async/propagation/ReactorPropagation.java
- `A` core-reactive/src/main/java/io/micronaut/core/async/propagation/package-info.java
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
- `A` core/src/main/java/io/micronaut/core/beans/exceptions/package-info.java
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
- `A` core/src/main/java/io/micronaut/core/convert/converters/package-info.java
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
- `A` core/src/main/java/io/micronaut/core/execution/ConditionalExecutionExecutor.java
- `M` core/src/main/java/io/micronaut/core/execution/DelayedExecutionFlow.java
- `M` core/src/main/java/io/micronaut/core/execution/DelayedExecutionFlowImpl.java
- `M` core/src/main/java/io/micronaut/core/execution/ExecutionFlow.java
- `A` core/src/main/java/io/micronaut/core/execution/ImmediateExecutor.java
- `M` core/src/main/java/io/micronaut/core/execution/ImperativeExecutionFlow.java
- `M` core/src/main/java/io/micronaut/core/execution/ImperativeExecutionFlowImpl.java
- `A` core/src/main/java/io/micronaut/core/execution/package-info.java
- `M` core/src/main/java/io/micronaut/core/expressions/EvaluatedExpressionReference.java
- `M` core/src/main/java/io/micronaut/core/expressions/ExpressionEvaluationContext.java
- `A` core/src/main/java/io/micronaut/core/expressions/package-info.java
- `A` core/src/main/java/io/micronaut/core/graal/Boxed.java
- `M` core/src/main/java/io/micronaut/core/graal/GraalReflectionConfigurer.java
- `A` core/src/main/java/io/micronaut/core/graal/package-info.java
- `M` core/src/main/java/io/micronaut/core/io/FileReadable.java
- `M` core/src/main/java/io/micronaut/core/io/IOUtils.java
- `M` core/src/main/java/io/micronaut/core/io/Readable.java
- `A` core/src/main/java/io/micronaut/core/io/ResourceConflictException.java
- `A` core/src/main/java/io/micronaut/core/io/ResourceDuplicateException.java
- `A` core/src/main/java/io/micronaut/core/io/ResourceLoadStrategy.java
- `R053` core/src/main/java/io/micronaut/core/io/ResourceLoadStrategyType.java
- `M` core/src/main/java/io/micronaut/core/io/ResourceLoader.java
- `M` core/src/main/java/io/micronaut/core/io/ResourceResolver.java
- `M` core/src/main/java/io/micronaut/core/io/Streamable.java
- `M` core/src/main/java/io/micronaut/core/io/UrlReadable.java
- `M` core/src/main/java/io/micronaut/core/io/Writable.java
- `A` core/src/main/java/io/micronaut/core/io/buffer/LeakTracker.java
- `M` core/src/main/java/io/micronaut/core/io/buffer/NioReadBuffer.java
- `M` core/src/main/java/io/micronaut/core/io/buffer/ReadBuffer.java
- `M` core/src/main/java/io/micronaut/core/io/buffer/ReadBufferFactory.java
- `M` core/src/main/java/io/micronaut/core/io/buffer/package-info.java
- `M` core/src/main/java/io/micronaut/core/io/file/DefaultFileSystemResourceLoader.java
- `A` core/src/main/java/io/micronaut/core/io/file/TemporaryFileResource.java
- `M` core/src/main/java/io/micronaut/core/io/file/package-info.java
- `M` core/src/main/java/io/micronaut/core/io/package-info.java
- `M` core/src/main/java/io/micronaut/core/io/scan/AnnotationScanner.java
- `A` core/src/main/java/io/micronaut/core/io/scan/ClassClassPathResourceLoader.java
- `A` core/src/main/java/io/micronaut/core/io/scan/ClassLoaderClassPathResourceLoader.java
- `M` core/src/main/java/io/micronaut/core/io/scan/ClassPathResourceLoader.java
- `A` core/src/main/java/io/micronaut/core/io/scan/CombinedClassPathResourceLoader.java
- `M` core/src/main/java/io/micronaut/core/io/scan/DefaultClassPathResourceLoader.java
- `M` core/src/main/java/io/micronaut/core/io/scan/package-info.java
- `M` core/src/main/java/io/micronaut/core/io/service/DefaultServiceDefinition.java
- `M` core/src/main/java/io/micronaut/core/io/service/MicronautMetaServiceLoaderUtils.java
- `M` core/src/main/java/io/micronaut/core/io/service/ServiceLoaderFeature.java
- `M` core/src/main/java/io/micronaut/core/io/service/ServiceScanner.java
- `M` core/src/main/java/io/micronaut/core/io/service/SoftServiceLoader.java
- `M` core/src/main/java/io/micronaut/core/io/service/package-info.java
- `M` core/src/main/java/io/micronaut/core/io/socket/package-info.java
- `A` core/src/main/java/io/micronaut/core/io/value/package-info.java
- `M` core/src/main/java/io/micronaut/core/naming/Described.java
- `M` core/src/main/java/io/micronaut/core/naming/NameUtils.java
- `M` core/src/main/java/io/micronaut/core/naming/Named.java
- `M` core/src/main/java/io/micronaut/core/naming/conventions/package-info.java
- `M` core/src/main/java/io/micronaut/core/naming/package-info.java
- `M` core/src/main/java/io/micronaut/core/optim/StaticOptimizations.java
- `A` core/src/main/java/io/micronaut/core/optim/package-info.java
- `M` core/src/main/java/io/micronaut/core/order/OrderUtil.java
- `M` core/src/main/java/io/micronaut/core/order/package-info.java
- `M` core/src/main/java/io/micronaut/core/propagation/MutablePropagatedContext.java
- `M` core/src/main/java/io/micronaut/core/propagation/PropagatedContext.java
- `A` core/src/main/java/io/micronaut/core/propagation/PropagatedContextConfiguration.java
- `M` core/src/main/java/io/micronaut/core/propagation/PropagatedContextImpl.java
- `A` core/src/main/java/io/micronaut/core/propagation/ScopedValuePropagatedContextElement.java
- `A` core/src/main/java/io/micronaut/core/propagation/ScopedValues.java
- `M` core/src/main/java/io/micronaut/core/propagation/ThreadContext.java
- `M` core/src/main/java/io/micronaut/core/propagation/ThreadPropagatedContextElement.java
- `A` core/src/main/java/io/micronaut/core/propagation/package-info.java
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
- `A` core/src/main/java/io/micronaut/core/util/ConnectionString.java
- `M` core/src/main/java/io/micronaut/core/util/CopyOnWriteMap.java
- `M` core/src/main/java/io/micronaut/core/util/EnvironmentProperties.java
- `A` core/src/main/java/io/micronaut/core/util/ExceptionUtils.java
- `M` core/src/main/java/io/micronaut/core/util/KotlinUtils.java
- `M` core/src/main/java/io/micronaut/core/util/LocaleResolver.java
- `M` core/src/main/java/io/micronaut/core/util/ObjectUtils.java
- `M` core/src/main/java/io/micronaut/core/util/StreamUtils.java
- `M` core/src/main/java/io/micronaut/core/util/StringUtils.java
- `M` core/src/main/java/io/micronaut/core/util/SupplierUtil.java
- `M` core/src/main/java/io/micronaut/core/util/clhm/ConcurrentLinkedHashMap.java
- `M` core/src/main/java/io/micronaut/core/util/clhm/LinkedDeque.java
- `M` core/src/main/java/io/micronaut/core/util/clhm/package-info.java
- `A` core/src/main/java/io/micronaut/core/util/functional/package-info.java
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
- `A` discovery-core/src/main/java/io/micronaut/discovery/cloud/digitalocean/package-info.java
- `M` discovery-core/src/main/java/io/micronaut/discovery/cloud/package-info.java
- `M` discovery-core/src/main/java/io/micronaut/discovery/config/ConfigDiscoveryConfiguration.java
- `M` discovery-core/src/main/java/io/micronaut/discovery/config/DefaultCompositeConfigurationClient.java
- `A` discovery-core/src/main/java/io/micronaut/discovery/config/RetryablePropertySourceImporter.java
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
- `A` http-client-core/src/main/java/io/micronaut/http/client/AsyncHttpClient.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/BlockingHttpClient.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/ClientAttributes.java
- `A` http-client-core/src/main/java/io/micronaut/http/client/DefaultAsyncOverReactiveHttpClient.java
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
- `A` http-client-core/src/main/java/io/micronaut/http/client/bind/binders/package-info.java
- `A` http-client-core/src/main/java/io/micronaut/http/client/bind/package-info.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/exceptions/HttpClientException.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/exceptions/HttpClientExceptionUtils.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/exceptions/HttpClientResponseException.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/exceptions/package-info.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/filter/ClientFilterResolutionContext.java
- `M` http-client-core/src/main/java/io/micronaut/http/client/filter/DefaultHttpClientFilterResolver.java
- `A` http-client-core/src/main/java/io/micronaut/http/client/filter/package-info.java
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
- `A` http-client-jdk/src/main/java/io/micronaut/http/client/jdk/cookie/package-info.java
- `A` http-client-jdk/src/main/java/io/micronaut/http/client/jdk/package-info.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/BlockHint.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/CancellableMonoSink.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/CompositeNettyClientCustomizer.java
- `M` http-client/src/main/java/io/micronaut/http/client/netty/ConnectionManager.java
- `A` http-client/src/main/java/io/micronaut/http/client/netty/DefaultAsyncHttpClient.java
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
- `A` http-client/src/main/java/io/micronaut/http/client/netty/NettyHttpClient.java
- `A` http-client/src/main/java/io/micronaut/http/client/netty/NettyHttpClientBuilder.java
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
- `D` http-netty/src/main/java/io/micronaut/http/netty/body/AvailableNettyByteBody.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/body/JsonChunkedProcessor.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/body/JsonCounter.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/body/NettyBodyAdapter.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/body/NettyByteBodyFactory.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/body/NettyByteBufMessageBodyHandler.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/body/NettyJsonHandler.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/body/NettyJsonStreamHandler.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/body/NettyWriteContext.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/body/StreamingNettyByteBody.java
- `A` http-netty/src/main/java/io/micronaut/http/netty/body/package-info.java
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
- `A` http-netty/src/main/java/io/micronaut/http/netty/channel/converters/package-info.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/channel/loom/EventLoopVirtualThreadScheduler.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/channel/loom/LoomBranchSupport.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/channel/loom/LoomCarrierGroup.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/channel/loom/PrivateLoomSupport.java
- `A` http-netty/src/main/java/io/micronaut/http/netty/channel/loom/package-info.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/channel/package-info.java
- `M` http-netty/src/main/java/io/micronaut/http/netty/configuration/NettyGlobalConfiguration.java
- `A` http-netty/src/main/java/io/micronaut/http/netty/configuration/package-info.java
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
- `D` http-server-netty/src/main/java/io/micronaut/http/server/netty/FormDataHttpContentProcessor.java
- `D` http-server-netty/src/main/java/io/micronaut/http/server/netty/FormRouteCompleter.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/HttpContentProcessor.java
- `D` http-server-netty/src/main/java/io/micronaut/http/server/netty/HttpContentProcessorAsReactiveProcessor.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/HttpPipelineBuilder.java
- `M` http-server-netty/src/main/java/io/micronaut/http/server/netty/IdentityWrapper.java
- `D` http-server-netty/src/main/java/io/micronaut/http/server/netty/MicronautHttpData.java
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
- `A` http-server-netty/src/main/java/io/micronaut/http/server/netty/discovery/package-info.java
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

### Tests

- `A` .agents/skills/skill-creator/references/spec-checklist.md
- `M` .github/workflows/graalvm-latest.yml
- `D` benchmarks/src/typeCheckTest/java/example/TypeThrashingTest.java
- `M` buffer-netty/src/test/java/io/micronaut/buffer/netty/AbstractReadBufferTest.java
- `M` context-propagation/src/test/groovy/io/micronaut/context/AnnotationReflectionUtilsSpec.groovy
- `M` context-propagation/src/test/groovy/io/micronaut/context/propagation/MDCReactorSpec.groovy
- `D` context-propagation/src/test/groovy/io/micronaut/context/propagation/MDCRxJava2Spec.groovy
- `M` context-propagation/src/test/groovy/io/micronaut/context/propagation/MDCRxJava3Spec.groovy
- `M` context-propagation/src/test/groovy/io/micronaut/context/propagation/MDCSpec.groovy
- `M` context-propagation/src/test/groovy/io/micronaut/context/propagation/MDCSpec2.groovy
- `M` context-propagation/src/test/groovy/io/micronaut/context/propagation/MDCSpec3.groovy
- `R076` context-propagation/src/test/groovy/io/micronaut/context/propagation/ReactorRxJavaSpec.groovy
- `M` context-propagation/src/test/groovy/io/micronaut/context/propagation/SimpleTraceInterceptorSpec.groovy
- `M` context-propagation/src/test/groovy/io/micronaut/context/propagation/ThreadLocalPropagatedTraceInterceptorSpec.groovy
- `M` context-propagation/src/test/kotlin/io/micronaut/context/propagation/mdc/MdcPropagationSpec.kt
- `A` context/src/test/java/io/micronaut/context/propagation/PropagatedContextConfigurationPropertiesTest.java
- `A` context/src/test/java/io/micronaut/runtime/MicronautConfigurationLoadingStrategyTest.java
- `M` context/src/test/java/io/micronaut/runtime/context/CompositeMessageSourceTest.java
- `A` context/src/test/java/io/micronaut/runtime/context/scope/refresh/RefreshScopeGetOrCreateTest.java
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
- `D` core/src/test/groovy/io/micronaut/core/propagation/PropagatedContextSpec.groovy
- `M` core/src/test/java/io/micronaut/core/io/service/SoftServiceLoaderTest.java
- `A` core/src/test/java/io/micronaut/core/propagation/MixedPropagatedContextTest.java
- `A` core/src/test/java/io/micronaut/core/propagation/PropagatedContextConfigurationTest.java
- `A` core/src/test/java/io/micronaut/core/propagation/PropagatedContextLambdaTest.java
- `A` core/src/test/java/io/micronaut/core/propagation/PropagatedContextTryResourcesTest.java
- `A` core/src/test/java/io/micronaut/core/propagation/ScopedValuePropagatedContextElementTest.java
- `A` core/src/test/java/io/micronaut/core/propagation/ScopedValuesPropagatedContextTest.java
- `A` core/src/test/java/io/micronaut/core/propagation/ThreadLocalPropagatedContextLambdaTest.java
- `A` core/src/test/java/io/micronaut/core/propagation/ThreadLocalPropagatedContextTryResourcesTest.java
- `A` core/src/test/java/io/micronaut/core/util/ConnectionStringTest.java
- `A` discovery-core/src/test/java/io/micronaut/discovery/config/RetryablePropertySourceImporterTest.java
- `M` function-web/src/test/groovy/io/micronaut/function/web/JavaLambdaFunctionSpec.groovy
- `A` http-client-jdk/src/test/groovy/io/micronaut/http/client/jdk/Issue12244Spec.groovy
- `A` http-client-jdk/src/test/groovy/io/micronaut/http/client/jdk/JdkBlockingHttpClientReuseSpec.groovy
- `A` http-client-jdk/src/test/groovy/io/micronaut/http/client/jdk/JdkBlockingHttpClientThreadLeakSpec.groovy
- `M` http-client-jdk/src/test/groovy/io/micronaut/http/client/jdk/RequestAttributeBindingSpec.groovy
- `M` http-client-tck/src/main/java/io/micronaut/http/client/tck/tests/DecompressionConfigTest.java
- `M` http-client-tck/src/main/java/io/micronaut/http/client/tck/tests/FormUrlEncodedTest.java
- `M` http-client-tck/src/main/java/io/micronaut/http/client/tck/tests/HeadersTest.java
- `M` http-client-tck/src/main/java/io/micronaut/http/client/tck/tests/Person.java
- `M` http-client-tck/src/main/java/io/micronaut/http/client/tck/tests/RedirectTest.java
- `M` http-client-tck/src/main/java/io/micronaut/http/client/tck/tests/filter/ClientRequestFilterTest.java
- `M` http-client-tck/src/main/java/io/micronaut/http/client/tck/tests/filter/ClientResponseFilterTest.java
- `A` http-client-tck/src/main/java/io/micronaut/http/client/tck/tests/filter/package-info.java
- `A` http-client-tck/src/main/java/io/micronaut/http/client/tck/tests/package-info.java
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
- `A` http-client/src/test/groovy/io/micronaut/http/client/ReactorHttpClientRetrySpec.groovy
- `R089` http-client/src/test/groovy/io/micronaut/http/client/SslRefreshMacSpec.groovy
- `M` http-client/src/test/groovy/io/micronaut/http/client/SslSpec.groovy
- `M` http-client/src/test/groovy/io/micronaut/http/client/aop/NullableCrudSpec.groovy
- `M` http-client/src/test/groovy/io/micronaut/http/client/bootstrap/ClientBootstrapSpec.groovy
- `M` http-client/src/test/groovy/io/micronaut/http/client/config/DefaultHttpClientConfigurationSpec.groovy
- `M` http-client/src/test/groovy/io/micronaut/http/client/netty/ConnectionManagerSpec.groovy
- `M` http-client/src/test/groovy/io/micronaut/http/client/netty/EmbeddedConnectionManager.java
- `M` http-client/src/test/groovy/io/micronaut/http/client/netty/EmbeddedTestUtil.groovy
- `M` http-client/src/test/groovy/io/micronaut/http/client/netty/Http1ResponseHandlerSpec.groovy
- `A` http-client/src/test/groovy/io/micronaut/http/client/netty/HttpClientToAsyncSpec.groovy
- `M` http-client/src/test/groovy/io/micronaut/http/client/retry/HttpClientRetrySpec.groovy
- `M` http-client/src/test/groovy/io/micronaut/http/client/retry/HttpClientWithCircuitBreakerSpec.groovy
- `M` http-client/src/test/groovy/io/micronaut/http/client/stream/StreamPostSpec.groovy
- `M` http-client/src/test/java/io/micronaut/http/client/ProxyBackpressureTest.java
- `A` http-client/src/test/resources/application-test.properties
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

