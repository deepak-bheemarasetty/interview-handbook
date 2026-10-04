## Overview

Spring Boot reduces setup through starter dependencies and auto-configuration. Auto-configuration creates sensible beans conditionally based on the classpath, properties, and beans already defined; it can be overridden.

## Configuration and Profiles

Use `application.properties` or YAML for external configuration. Profiles select environment-specific configuration, for example `application-dev.yml` or `application-prod.yml`. Keep secrets outside source control and inject them through secure environment/deployment configuration.

## Configuration Properties

Bind related, typed settings with `@ConfigurationProperties` rather than scattered `@Value` expressions. Validate configuration on startup to fail early for invalid required settings.

## Interview Takeaway

Auto-configuration is conditional convention, not hidden magic. Starters add a curated dependency set; profiles and external configuration keep environment differences out of code.

```table-of-contents
```
