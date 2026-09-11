# Change Log
All notable changes to this project will be documented in this file, which follows the guidelines
on [Keep a CHANGELOG](http://keepachangelog.com/). This project adheres to
[Semantic Versioning](http://semver.org/).

## [25.104.1] - 2026-09-11
### Changed
- Updated the parent `maven-parent-pom` to 25.104.1 to take the changes from it
- Updated `maven-common-bom` to 25.104.1

## [25.104.0] - 2026-09-07
First official (non-milestone) release of the Java 25 / WildFly 40 / Jakarta EE 11 line,
consolidating milestones `25.104.0-M1` to `25.104.0-M9` and the never-released Java 21 /
Jakarta EE 10 step that preceded them.

### Added
- `maven-common-bom` as an imported BOM in `dependencyManagement`; the `maven.common.bom.version` property controls the imported version
- `jandex-index` profile: auto-generates `META-INF/jandex.idx` via `io.smallrye:jandex:3.1.6` during `process-classes` for all modules with `src/main/java` — required for WildFly 32 and later to scan CDI annotations in `WEB-INF/lib` JARs
- `exec-maven-plugin` `3.0.0` to `pluginManagement`
- `jakarta.xml.bind-api.raml.version` (`2.3.2`), centralised here after being duplicated in the `cp-framework-libraries`, `cp-microservice-framework` and `cp-event-store` root poms. The RAML parser (`org.raml:raml-parser`) and `coveralls-maven-plugin` `4.3.0` use `javax.xml.bind.*` internally, which only exists in the 2.x line — any plugin using either must pin its runtime classpath to this version, so it must NOT be upgraded to 3.x or 4.x
- `snakeyaml.liquibase.version` (`2.3`), used to pin snakeyaml inside the Liquibase fat JAR only; the project classpath stays on snakeyaml `1.33` to keep the RAML parser working
- `maven-shade-plugin` configuration for the Liquibase fat JAR: an `artifactSet` exclusion of `org.liquibase:liquibase-commercial` (only open-source Liquibase operations are used), and relocation of `org.yaml.snakeyaml` to `uk.gov.justice.shaded.snakeyaml` so the bundled snakeyaml cannot shadow the `liquibase-maven-plugin`'s own snakeyaml 2.x — without it, snakeyaml 1.x hides `TagInspector` and Liquibase fails with `ServiceConfigurationError` on `ChecksCreateCommandStep`

### Changed
- Upgraded to Java 25 / WildFly 40 / Jakarta EE 11 (`25.104.x` release line)
- Upgraded `wildfly-maven-plugin` from `1.2.0.Final` to `6.0.0.Final`
- Bumped parent `maven-parent-pom` to the released `25.104.0` — Java 25 / Jakarta EE 11 targeting (`java.major.version=25`, `enforcer.java.version.range=[25,)`), `liquibase.version=5.0.3`, and the `buildnumber-maven-plugin` / `build-helper-maven-plugin` build-warning fixes
- Bumped `maven.common.bom.version` to the released `25.104.0` — Jakarta EE 11 API set, WildFly `40.0.0.Final`, Weld 6, RESTEasy 7, Apache Artemis `2.54.0` under the new `org.apache.artemis` groupId, Jackson `2.21.5` (**CVE-2026-54515**) and the `org.junit:junit-bom` import

### Fixed
- Declared `io.smallrye:jandex` as an explicit dependency of the `exec-maven-plugin` in the `jandex-index` profile — previously the plugin assumed jandex was already in the local Maven repository, causing `Error: Unable to access jarfile .../jandex-3.1.6.jar` failures on CI agents with a fresh Maven cache

## [17.103.0] - 2025-07-11
### Changed
- Github migration to HMCTS Organisation
- Update maven-parent-pom to 17.103.0

## [17.101.0] - 2025-01-08
### Changed
- Update maven-parent-pom to 17.101.0
- Update postgresql.driver.version to 42.3.2 (through maven-parent-pom)

## [17.1.1] - 2024-06-12
### Added
- Add maven-sonar-plugin to pluginManagement (through maven-parent-pom)

## [17.1.0] - 2023-05-05
### Changed
- Update maven-parent-pom to 17.1.0

## [17.0.0] - 2023-05-05
### Changed
- Update to Java 17
- Remove illegal-access argument from surefire plugin from plugin management (through maven-parent-pom 17.0.0-M6)
- Remove illegal-access argument (not valid for java 17) from sure fire plugin (through maven-parent-pom)

## [11.0.1] - 2023-02-01
### Changed
- Downgraded maven minimum version to 3.3.9 until the pipeline maven version is updated

## [11.0.0] - 2023-01-25
### Changed
- Bumped the version number to 11.0.0 to match the java 11 versions of the framework
- Update to Java 11
- Update to JEE 8
- Bumped version to 11.0.0 to match new framework version
- Moved liquibase dependency versions to maven-parent-pom

## [2.0.0] - 2020-09-22
### Changed
- Updated parent maven-parent-pom to version 2.0.0
- Moved to new Cloudsmith.io repository for hosting maven artifacts
- Updated encrypted properties in travis.yaml to point to cloudsmith

## [1.13.0] - 2018-07-05
### Removed
- generator-maven-plugin.version maven property
- json-schema-catalog.version maven property

## [1.12.3] - 2018-06-21
### Changed
- Updated generator-maven-plugin version to 2.5.1 to fix apache tika security issues
- Updated json-schema-catalog version to 1.2.3 to fix apache tika security issues

## [1.12.2] - 2018-05-18
### Changed
- Fix upgrade Jackson to 2.8.11

## [1.12.1] - 2018-05-17
###Changed
- Upgrade Jackson to 2.8.11 to fix Jackson security issues 

## [1.12.0] - 2018-04-11
### Changed
- Schema catalog version to 1.2.1

## [1.11.0] - 2018-01-25
### Removed
- Schema generator plugin from framework parent pom

## [1.10.1] - 2018-01-08
### Fixed
- Wrong Json Schema Catalog property name 

## [1.10.0] - 2018-01-08 
### Changed
- Json Schema Catalog version to 1.1.0

## [1.9.0] - 2017-12-19
### Added
- Schema catalog generation for RAML jar

### Changed
- Maven parent pom version to 1.7.1
- Json schema catalog version to 1.0.1

## [1.8.0] - 2017-12-15
### Added
- Schema catalog generation plugin

## [1.7.0] - 2017-11-28
### Added
- Jacoco exclude uk/gov/justice/api/mapper/*MediaTypeToSchemaIdMapper.class

### Changed
 - wildfly-maven-plugin 1.2.0.Alpha6 -> 1.2.0.Final

## [1.6.1] - 2017-07-31
### Changed
 - Don't add the wildfly plugin to the build process in "skipped" mode. Leave it out entirely

## [1.6.0] - 2017-07-28
### Changed
 - Upgrade to use parent POM [1.6.0](https://github.com/CJSCommonPlatform/maven-parent-pom/releases/tag/release-1.6.0)
 - Improved Travis CI Build
 - Switched to Bintray for binaries

## [1.4.0] - 2017-06-14
### Changed
 - Upgrade to use parent POM [1.5.0](https://github.com/CJSCommonPlatform/maven-parent-pom/releases/tag/release-1.5.0)

## [1.3.0] - 2017-04-28

### Changed
 - Upgrade to use parent POM [1.4.1](https://github.com/CJSCommonPlatform/maven-parent-pom/releases/tag/release-1.4.1)

## [1.2.0] - 2016-11-15

### Changed
 - Upgrade to use parent POM [1.2.0](https://github.com/CJSCommonPlatform/maven-parent-pom/releases/tag/release-1.2.0)

## [1.1.0] - 2016-11-01

### Changed
 - Upgrade to use parent POM [1.1.0](https://github.com/CJSCommonPlatform/maven-parent-pom/releases/tag/release-1.1.0)

### Removed
 - Common plugin configuration from POM as this is now held in parent

## [1.0.0] - 2016-07-28

### Added

- Initial release of parent POM for framework components

[Unreleased]: https://github.com/CJSCommonPlatform/maven-framework-parent-pom/compare/release-1.3.0...HEAD
[1.3.0]: https://github.com/CJSCommonPlatform/maven-framework-parent-pom/compare/release-1.2.0...release-1.3.0
[1.2.0]: https://github.com/CJSCommonPlatform/maven-framework-parent-pom/compare/release-1.1.0...release-1.2.0
[1.1.0]: https://github.com/CJSCommonPlatform/maven-framework-parent-pom/compare/release-1.0.0...release-1.1.0
[1.0.0]: https://github.com/CJSCommonPlatform/maven-framework-parent-pom/commits/release-1.0.0
