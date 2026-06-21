# Project Defaults

These defaults apply to every mod unless an approved project-specific decision overrides them.

Machine-readable values are stored in `setup/template-defaults.properties`. This document explains their meaning and the policies surrounding them. Keep both sources consistent.

## Platform

- Target Minecraft Forge 1.12.2.
- Cleanroom must be supported.
- Use the template repository configured in `setup/template-defaults.properties`.
- Use the versions of Forge, Gradle, RetroFuturaGradle, and related build tools supplied by the fetched template.
- Do not upgrade or replace template build components without an approved project-specific reason.

## Development Environment

- Use Java 25 to run Gradle and the development environment.
- IntelliJ IDEA is the preferred IDE.
- Use the Gradle wrapper supplied by the fetched template instead of a separately installed Gradle version.
- Use the template's build conventions and generated run configurations where applicable.
- Final mod repositories use `main` as their primary branch.

## Java Compatibility

- Release artifacts must remain compatible with Java 8.
- Modern Java syntax support is disabled by default.
- It may be enabled only through the mechanism supplied by the configured template.
- Do not use Java APIs introduced after Java 8 unless an approved compatible dependency provides them at runtime.
- Building with Java 25 does not permit targeting a newer Java runtime.

## Project Identity

Unless explicitly overridden:

- Author metadata is `Mahghuuuls`.
- The root Java package is `com.mahghuuuls`.
- The development username is `Mahghuuuls`.

The mod ID, display name, final package segment, description, and main class are project-specific decisions and must come from approved project documentation.

## Licensing and Attribution

- The default license for new mods is MIT.
- A project may override the license through `workspace/project.properties`.
- Preserve all license notices and attribution required by the fetched template and any reused code.
- Retain CleanroomMC attribution when ForgeDevEnv-derived build infrastructure is included.
- Attribute original mod work to Mahghuuuls.

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
