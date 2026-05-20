
• There is an existing breaks.adoc, but it only covers an older BOM-coordinate change, not the XmlMediaTypeCodec removal. I’m collecting line references for the final summary now.

• Explored
  └ Read XmlMediaTypeCodec.java, XmlMessageHandler.java, libs.versions.toml, JacksonXmlConfiguration.java

───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────

• Compared mn4 -> mn5 for release-note direction.

  Scope:

  - Previous: mn4/micronaut-jackson-xml, branch 4.8.x, commit a00a55125ccb, clean
  - Current: mn5/micronaut-jackson-xml, branch 5.0.x, commit fee1d071add6, clean
  - Delta: 55 commits, 64 changed files, 18 added, 3 deleted, 43 modified
  - Full report: micronaut-jackson-xml-mn4-to-mn5-comparison.md:1

  Release Note Draft

  Breaking Changes

  - Removed XmlMediaTypeCodec, the old XML MediaTypeCodec implementation. The previous class extended JacksonMediaTypeCodec and was named xml; it is gone in mn5. See old class at mn4/micronaut-jackson-xml/jackson-xml/src/main/
    java/io/micronaut/xml/jackson/codec/XmlMediaTypeCodec.java:30.
  - XML handling now uses Micronaut’s MessageBodyHandler infrastructure via XmlMessageHandler. See mn5/micronaut-jackson-xml/jackson-xml/src/main/java/io/micronaut/xml/jackson/server/XmlMessageHandler.java:49.
  - Jackson XML public/configuration types moved to tools.jackson.* types. For example, JacksonXmlConfiguration now uses XmlReadFeature and XmlWriteFeature instead of the previous Jackson XML parser/generator feature types. See
    mn5/micronaut-jackson-xml/jackson-xml/src/main/java/io/micronaut/xml/jackson/JacksonXmlConfiguration.java:18.

  Dependency And Platform Updates

  - Micronaut Core BOM: 4.10.5 -> 5.0.0-RC2.
  - Micronaut Gradle plugin: 4.5.5 -> 5.0.0-M1.
  - Gradle wrapper: 8.14.3 -> 9.5.0.
  - Project version: 4.8.1-SNAPSHOT -> 5.0.0-SNAPSHOT.
  - jaxb-api remains unchanged at 2.3.1. See mn5/micronaut-jackson-xml/gradle/libs.versions.toml:1.

  Build And Tooling

  - Added .sdkmanrc with java=25.0.1-graal.
  - Micronaut shared settings plugin: 7.6.4 -> 8.0.0-M18.
  - CI/release/common files were refreshed, including Sonatype publishing and vulnerability audit support.

  Documentation Gap

  - I found an existing breaks.adoc, but no new breakage note for the XmlMediaTypeCodec removal or the tools.jackson.* migration. That should probably be added before release.

  Mostly Internal

  - Added .agents/skills/* guidance files.
  - Updated test-suite examples and native-image reflection config.

