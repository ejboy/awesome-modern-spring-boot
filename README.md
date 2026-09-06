# Awesome Modern Spring Boot

An opinionated, actively maintained collection of **modern, lightweight tools and practices for Spring Boot 4.x and beyond**.

**Updated for the Spring Boot 4.x era:** Spring Boot now provides first-class support for capabilities such as structured logging, Docker Compose integration, Testcontainers support, observability, and modern container packaging. This list reflects those newer defaults instead of carrying forward years of historical recommendations.

This is a curated list, not an exhaustive directory. Lightweight is a preference, not a strict admission requirement.

## Philosophy

* **Spring Boot 4.x+ first.** Older versions are not the focus.
* **Lightweight by default.** Prefer simple tools, fewer moving parts, and proportional infrastructure.
* **Use Spring Boot itself first.** Do not add dependencies or infrastructure when Boot already provides a good solution.
* **One strong recommendation is better than ten alternatives.**
* **Actively maintained projects only.**
* **Production usefulness over popularity.**
* **Categories do not need to be complete.** Missing alternatives are intentional.
* Specialized tools are welcome when they solve a concrete problem especially well.

## Project setup

### [Spring Initializr](https://start.spring.io/)

The standard minimal starting point for a Spring Boot application. Start with the dependencies actually needed rather than a large template.

## Architecture

### [Spring Modulith](https://spring.io/projects/spring-modulith)

Tooling for structuring modular Spring applications and verifying module boundaries. A modular application is often worth considering before splitting an application into distributed services.

## Database migrations and data

### [Flyway](https://github.com/flyway/flyway)

A straightforward default for version-controlled database schema migrations.

### [Scriptella](https://github.com/scriptella/scriptella-etl)

For repeatable database scripting, data migration, data transformations, cross-database migration, imports and exports, and ETL-style operational jobs.

## Testing

### [Testcontainers](https://java.testcontainers.org/)

Test against actual infrastructure such as PostgreSQL where practical instead of substituting behaviorally different in-memory implementations. Spring Boot provides first-class Testcontainers integration and support; Testcontainers itself remains an external project.

### [WireMock](https://wiremock.org/)

Useful for testing applications that integrate with external HTTP services.

### [ArchUnit](https://www.archunit.org/)

A way to express and enforce architectural rules in code.

## APIs

### [springdoc-openapi](https://springdoc.org/)

A practical option for OpenAPI documentation and Swagger UI in modern Spring Boot applications.

## Metrics, health and monitoring

Spring Boot uses Micrometer as its standard metrics abstraction, while Actuator provides production health and management endpoints. Production metrics should use an appropriate Micrometer registry or export path for the monitoring system in use. The generic `/actuator/metrics` endpoint is primarily useful for diagnostics and inspection, rather than as the preferred production metrics collection interface.

### Spring Boot Actuator

Spring Boot's production-ready foundation for application health and management. Use it for health and other operational endpoints, exposing only the endpoints actually needed in production.

### [Micrometer](https://micrometer.io/)

Spring Boot's standard metrics facade and the basis for its built-in application, JVM, system, HTTP, and other metrics. Instrument and report metrics through Micrometer, using the appropriate registry or export mechanism for the monitoring system in use.

### [StatLite](https://github.com/PVRLabs/statlite)

Lightweight, self-hosted monitoring for a small number of Spring Boot applications and hosts, without requiring a larger monitoring stack. Focused on application health, latency, errors, JVM metrics, and basic host monitoring.

## Logging

### Spring Boot structured logging

Consider Boot's built-in structured logging before adding another dependency or logging system purely to obtain structured output.

## Local development

### Spring Boot Docker Compose support

Built-in Spring Boot functionality for integrating with Compose-based development services and reducing custom local-development configuration and startup glue.

## Packaging and deployment

### Spring Boot + Cloud Native Buildpacks

Spring Boot's Maven and Gradle plugins can create OCI-compatible container images using Cloud Native Buildpacks. This can avoid maintaining a custom Dockerfile for straightforward deployments, while Dockerfiles remain useful when a deployment needs more control.

## Upgrades and maintenance

### [OpenRewrite](https://docs.openrewrite.org/)

Automated source transformation and migration tooling with strong usefulness for major Spring and Spring Boot upgrades.

## Practices

### Prefer Spring Boot defaults

Start with Boot's defaults and dependency management. Override them when there is a concrete reason.

### Prefer built-in functionality over another dependency

Modern Spring Boot already covers many development and operational concerns. A new dependency should have a clear reason to exist.

### Keep Actuator exposure intentional

Expose the operational endpoints that are actually required rather than everything available.

### Test against real infrastructure

Where practical, use real infrastructure through Testcontainers rather than behaviorally different substitutes.

### Version database changes

Production schema changes should be repeatable and tracked alongside application changes.

### Start with a modular application

Prefer keeping clear boundaries inside the application before introducing distributed-service complexity without a concrete reason.

### Keep production infrastructure proportional

A small Spring Boot application should not automatically require a large operational stack. Start with the simplest setup that provides the reliability and visibility actually needed.

### Prefer structured logs

Prefer machine-readable production logs where appropriate.

### Measure before tuning

Use actual CPU, memory, allocation, latency, and workload measurements before adding JVM tuning or increasing infrastructure.

### Keep dependencies current

Use Spring Boot's dependency management where possible. Avoid unnecessary version overrides and keep applications on maintained Spring Boot releases.

## Contributing

This list has a high inclusion bar and is editorial rather than exhaustive. Self-submissions are welcome; please disclose any affiliation. Missing alternatives are intentional. See [CONTRIBUTING.md](CONTRIBUTING.md) for details.

## Related

For broader lightweight and efficiency-focused developer tooling, see [Awesome Efficient Devtools](https://github.com/ejboy/awesome-efficient-devtools).

## Maintainer note

The maintainer builds some of the listed tools through [PVR Labs](https://pvrlabs.xyz/). Those tools are included under the same editorial criteria as every other project here.
