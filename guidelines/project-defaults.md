# Project Defaults

These defaults apply to every mod unless an approved project-specific decision overrides them.

`setup/template-defaults.properties` is the authoritative source for machine-readable default values. This document defines their meaning and the policies surrounding them. Do not duplicate literal property values in other reusable instructions.

## Platform

- Target Minecraft Forge 1.12.2.
- Cleanroom must be supported.
- Use the template repository and ref identified by `template_repository_url` and `template_repository_ref`.
- Use the versions of Forge, Gradle, RetroFuturaGradle, and related build tools supplied by the fetched template.
- Do not upgrade or replace template build components without an approved project-specific reason.

## Development Environment

- Use Java 25 to run Gradle and the development environment.
- IntelliJ IDEA is the preferred IDE.
- Use the Gradle wrapper supplied by the fetched template instead of a separately installed Gradle version.
- Use the template's build conventions and generated run configurations where applicable.
- Use `project_default_branch` for the final mod repository branch.

## Java Compatibility

- Release artifacts must remain compatible with Java 8.
- Read the default modern-syntax setting from `use_modern_java_syntax`.
- Modern syntax may be enabled only through the mechanism supplied by the configured template.
- Do not use Java APIs introduced after Java 8 unless an approved compatible dependency provides them at runtime.
- Building with Java 25 does not permit targeting a newer Java runtime.

## Project Identity

During Initialization, read shared identity values from `setup/template-defaults.properties`:

- `mod_authors` defines default author metadata and attribution.
- `root_package` defines the default root Java package.
- `minecraft_username` defines the development username.

Do not hardcode these values in initialization instructions or generated project documents.

The mod ID, display name, final package segment, description, and main class are project-specific decisions and must come from approved project documentation.

## Licensing and Attribution

- Read the default mod license from `license`.
- A project may override the license through `workspace/project.properties`.
- Preserve all license notices and attribution required by the fetched template and any reused code.
- Retain CleanroomMC attribution when ForgeDevEnv-derived build infrastructure is included.
- Attribute original mod work using the configured author metadata.

A project-specific license override does not permit removing notices required by upstream licenses.

## Distribution

- CurseForge is the only intended mod distribution platform.
- Do not prepare Modrinth or other platform-specific publication unless explicitly requested.
- Agents may prepare release artifacts, documentation, metadata, and visual assets.
- The project owner performs every upload and publication action.

## Versioning

- Use semantic versioning for mod releases unless an approved project decision requires another scheme.
- Version changes belong to release preparation and must not occur incidentally during feature work.

## Overrides

- Project-specific overrides belong in the ignored `workspace/project.properties` or approved project documentation, depending on whether they are operational or behavioral.
- Explicit project decisions take precedence over shared defaults.
- Never infer or apply an override silently.
- When an override affects compatibility, architecture, licensing, or distribution, record its consequences in the relevant project document.
