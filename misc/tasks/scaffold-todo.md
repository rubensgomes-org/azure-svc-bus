# Scaffold TODO

## Goal

`azure-svc-bus` was scaffolded from `spring-blueprint` as build/CI/release machinery
only. This file records what was deliberately left outstanding so the scaffold
could be handed over green.

## Outstanding

- [ ] Add the Azure dependency — spring-cloud-azure-starter-servicebus — to `app/build.gradle.kts`,
      sourced from the shared `com.rubensgomes:gradle-catalog`.
- [ ] Add `app/src/main/resources/application-azure.yml` with the connection
      and credential configuration for the service.
- [ ] Build the real endpoint that demonstrates Azure Service Bus.
- [ ] Remove the placeholder `HelloWorld*` classes and their tests once that
      endpoint exists. They are kept for now because deleting them drops line
      and branch coverage below the 90% JaCoCo gate in `app/build.gradle.kts`,
      which would make `./gradlew build` fail.
- [ ] Regenerate the lock files once the dependencies above have landed:
      `./gradlew :app:dependencies --write-locks`, then commit
      `app/gradle.lockfile` and `app/buildscript-gradle.lockfile`.
- [ ] Create the SonarCloud project `rubensgomes-org_azure-svc-bus` in the
      `rubensgomes-org` organization. Until it exists, `build-verify.yml`
      fails at `:app:sonar` because `sonar.qualitygate.wait=true`.

## Notes

The lock files carried over from `spring-blueprint` verbatim: they contain no
project identifiers and the dependency set is unchanged, so they stay valid
until the first Azure dependency is added.
