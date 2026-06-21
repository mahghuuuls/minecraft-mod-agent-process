# Project Defaults

These defaults apply to every mod unless an approved project-specific decision overrides them.

`setup/template-defaults.properties` is the authoritative source for machine-readable shared preferences. Project identity, loader, compatible runtimes, distribution targets, and template selection belong in `workspace/project.properties` and approved project documents.

## Fixed Scope

- Target Minecraft 1.12.2.
- Use the selected loader and compatible runtimes approved during Project Setup and Feasibility Research.
- Do not assume Forge, Cleanroom, LiteLoader, or another loader applies until selected.
- Use loader-specific APIs, metadata, build tooling, and lifecycle rules only when applicable to the selected project.
- Do not change Minecraft version or loader during implementation without returning to the stages that own those decisions.

## Template and Build Tooling

- Project Setup selects a provisional loader and template; Feasibility Research validates them.
- Initialization uses the approved template repository and exact ref recorded in project configuration.
- Use the build tools and wrapper supplied by the approved template or existing project.
- Do not upgrade or replace build components without an approved project-specific reason.
- Record the exact fetched template commit during Initialization.

## Development Environment

- Treat `preferred_development_java_version` as a preference, not a guarantee that every template supports it.
- Determine the actual development JDK from the approved loader, template, and build tooling.
- IntelliJ IDEA is the preferred IDE.
- Use the project's wrapper instead of a separately installed build-tool version.
- Use `project_default_branch` for a newly initialized mod repository.

## Runtime Compatibility

- Treat `target_java_version` as the default release target.
- Validate the actual Java target against the selected loader, runtimes, dependencies, and template.
- Do not use runtime APIs newer than the approved target unless an approved compatible dependency supplies them.
- A newer development JDK does not authorize a newer release target.
- Record supported runtime environments explicitly rather than inferring them from the loader name.

## Project Identity

Project Setup or approved project documents must establish:

- Root Java package
- Author metadata
- Development username when the toolchain uses one
- Mod ID and display name
- Description and main entry point

Do not use repository-owner identity as a default for generated mods. Do not leave example values in initialized project files.

## Licensing and Attribution

- Read the default project license from `license`.
- A project may override it through `workspace/project.properties`.
- Preserve notices and attribution required by the selected template, loader, dependencies, and reused code.
- Attribute original mod work using approved project author metadata.
- A project license override does not permit removing upstream obligations.

## Distribution

- Treat `preferred_distribution_platform` as the suggested primary destination.
- Project Setup asks the owner to approve one or more distribution platforms.
- CurseForge should be offered as the default recommendation, but it is not mandatory or exclusive.
- Research and follow the current requirements of every selected platform.
- Agents may prepare artifacts, documentation, metadata, and visual assets for approved platforms.
- The project owner performs every upload and publication action.

## Versioning

- Use semantic versioning unless an approved decision requires another scheme.
- Version changes belong to release work and must not occur incidentally during feature implementation.

## Overrides

- Operational overrides belong in the ignored `workspace/project.properties`.
- Behavioral and architectural decisions belong in approved project documents.
- Explicit project decisions take precedence over shared preferences.
- Never infer or apply an override silently.
- Record consequences when an override affects compatibility, architecture, licensing, or distribution.
