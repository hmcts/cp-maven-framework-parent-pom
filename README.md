# cp-maven-framework-parent-pom

`uk.gov.justice:maven-framework-parent-pom`

The Maven parent POM for all CPP framework implementation projects. It sits between `maven-parent-pom` (build tooling) and the framework code projects, adding the framework-specific build plugins and importing `maven-common-bom` so that dependency versions are available everywhere.

## Position in the hierarchy

```
maven-parent-pom
└── maven-framework-parent-pom  ← this project
    ├── cp-framework-libraries   (uk.gov.justice.framework.libraries:framework-libraries)
    ├── cp-microservice-framework (uk.gov.justice.services:microservice-framework)
    ├── cp-event-store           (uk.gov.justice.event-store:event-store)
    └── cp-cake-shop             (uk.gov.justice.services:cake-shop)
```

## What this POM adds

**Dependency import**
- Imports `maven-common-bom` so all third-party dependency versions are available to inheriting projects without re-declaring the import.

**Additional plugin management**
| Plugin | Purpose |
|---|---|
| `wildfly-maven-plugin` 4.2.2.Final | Deploy WARs to a running WildFly instance |
| `liquibase-maven-plugin` 4.10.0 | Run Liquibase migrations (skipped when `skipTests=true`) |
| `h2-maven-plugin` 1.0 | Embedded H2 database for tests |
| `exec-maven-plugin` 3.0.0 | Execute external processes during build |
| `maven-processor-plugin` (Hibernate JPA model gen) | Generates JPA metamodel classes |

**Profiles**
| Profile | Activation | Effect |
|---|---|---|
| `raml-jar` | `src/raml` exists | Packages RAML sources into a `raml` classifier JAR (plus early `generate-test-resources` phase copy for tests) |
| `liquibase-jar` | `src/main/resources/liquibase.properties` exists | Runs Liquibase plugin, creates an executable shaded JAR for migration tooling |
| `jandex-index` | `src/main/java` exists | Generates a Jandex index (`META-INF/jandex.idx`) for CDI bean discovery in WildFly |

**JaCoCo exclusions** — generated classes excluded from coverage: `*Application`, `*JmsListener`, `Remote*`, `*Resource`, `*ActionMapper`, `*MediaTypeToSchemaIdMapper`, JPA entity metamodels.

## Usage

Set this as the `<parent>` in any new framework-layer project:

```xml
<parent>
    <groupId>uk.gov.justice</groupId>
    <artifactId>maven-framework-parent-pom</artifactId>
    <version>${framework.version}</version>
</parent>
```

Context-level services (`cpp-context-*`) do **not** use this POM directly — they inherit from `cpp-platform-maven-service-parent-pom` instead.
