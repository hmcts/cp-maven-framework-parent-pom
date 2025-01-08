# Change Log
All notable changes to this project will be documented in this file, which follows the guidelines
on [Keep a CHANGELOG](http://keepachangelog.com/). This project adheres to
[Semantic Versioning](http://semver.org/).

## Unreleased
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
