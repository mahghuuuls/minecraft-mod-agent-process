# Initialize Mod Project

## Purpose

Personalize a newly created ForgeDevEnv repository using the standard Mahghuuuls project defaults.

This is a mechanical setup operation. It must not implement mod features or make product decisions.

## Main Question

> Is the ForgeDevEnv repository correctly personalized and ready for development?

## Required Input

- `guidelines/project-defaults.md`
- The active repository under `workspace/project/`
- Mod ID
- Mod display name
- Main mod class name
- Short description
- Initial version

Read the current ForgeDevEnv structure before making changes. Do not assume it still matches an older version.

## Preconditions

Before initialization:

- Exactly one mod repository must exist under `workspace/project/`.
- The repository must have been created from the current ForgeDevEnv template.
- The working tree must not contain unexplained changes.
- Required project values must be confirmed by the project owner.

If the repository appears previously initialized or contains unrelated work, stop and ask before continuing.

## Project Defaults

Unless explicitly overridden:

- Root package: `com.mahghuuuls`
- Author: `Mahghuuuls`
- Development username: `Mahghuuuls`
- Initial version: `1.0.0`
- License: MIT
- Modern Java syntax: disabled
- Java 25 is used for the development environment.
- Release artifacts remain compatible with Java 8.
- Cleanroom compatibility is required.
- CurseForge is the intended distribution platform.
- Publication is performed manually by the project owner.

## Desired AI Behavior

Act as a careful project initializer.

- Inspect the actual repository before changing it.
- Compare it with the current ForgeDevEnv template when necessary.
- Ask for missing project values one question at a time.
- Do not invent names, IDs, descriptions, or class names.
- Preserve upstream properties and capabilities that do not require customization.
- Modify property values by key instead of replacing the entire file.
- Avoid broad global replacements.
- Do not implement gameplay behavior.
- Do not introduce architecture or dependencies.
- Report unexpected upstream changes.
- Do not commit or push.
- Record every modified, moved, created, or removed file.
- Run verification after initialization.

## Initialization Changes

### Gradle Properties

Update the applicable values in `gradle.properties`:

```properties
mod_version = <initial-version>
root_package = com.mahghuuuls
mod_id = <mod-id>
mod_name = <mod-name>
mod_description = <description>
mod_authors = Mahghuuuls
minecraft_username = Mahghuuuls
use_modern_java_syntax = false
publish_to_curseforge = false
publish_to_modrinth = false
```

Preserve other upstream properties unless a project default explicitly overrides them.

Do not remove newly introduced ForgeDevEnv properties merely because they were absent from an older template version.

### Java Package

Move the starter source package from:

```text
src/main/java/com/example/modid/
```

to:

```text
src/main/java/com/mahghuuuls/<mod-id>/
```

Adapt to the actual upstream path if ForgeDevEnv has changed.

Update:

- Package declarations
- Main class name
- Main class filename
- References to the starter class
- Starter log message

The final package should be:

```text
com.mahghuuuls.<mod-id>
```

The mod ID must also be valid as a Java package segment. If it is not, ask the project owner to define the package segment separately.

### Mixin Configuration

When the template contains a Mixin configuration, set its package to:

```text
com.mahghuuuls.<mod-id>.mixin
```

Do not enable Mixins unless the project explicitly requires them.

### License

Use the MIT License.

Preserve the CleanroomMC copyright and license notice inherited from ForgeDevEnv.

Add Mahghuuuls attribution for original project work without removing upstream attribution.

### Template Documentation

Remove the ForgeDevEnv-specific README so it is not mistaken for the mod's user documentation.

Do not create the final mod README during initialization. It will be written during Packaging and Release Preparation.

Remove or reset the template changelog so ForgeDevEnv example entries are not presented as mod history.

### Publishing Configuration

Keep automated publishing disabled.

Do not:

- Add publication credentials.
- Configure Modrinth publication.
- Upload to CurseForge.
- Publish a release.

The project owner performs publication manually.

## Placeholder Validation

After making changes, check relevant project files for unresolved template placeholders, including:

```text
com.example
ExampleMod
root_package = com.example
mod_id = modid
mod_name = Mod Name
minecraft_username = Developer
```

Evaluate matches in context. Placeholder words appearing only in explanatory comments do not necessarily require modification.

Do not declare initialization complete while functional placeholder values remain.

## Verification

Use the Gradle wrapper provided by the project.

Run the environment-appropriate equivalent of:

```bash
./gradlew clean build
```

On Windows:

```powershell
.\gradlew.bat clean build
```

Verify that:

- Gradle uses the expected development environment.
- Source packages match their directories.
- The main mod class compiles.
- Generated metadata contains the configured values.
- Tests pass when present.
- The build produces the expected reobfuscated JAR.
- No unresolved functional placeholders remain.

A successful build does not authorize a commit, push, or release.

## Process

1. Locate the active mod repository.
2. Inspect its Git status.
3. Confirm that it is an uninitialized ForgeDevEnv project.
4. Inspect the current ForgeDevEnv structure.
5. Read `guidelines/project-defaults.md`.
6. Collect missing project values from the project owner.
7. Present the intended changes for confirmation.
8. Update `gradle.properties`.
9. Move and rename the starter Java source.
10. Update package declarations and class references.
11. Update the Mixin package without enabling Mixins.
12. update license attribution.
13. Remove upstream template documentation that does not describe the mod.
14. Check for unresolved placeholders.
15. Run the Gradle build.
16. Report changes and verification results.
17. Generate the initialization record.

## Output

Produce:

```text
workspace/documentation/project-initialization.md
```

The document should contain:

1. Mod name
2. Mod ID
3. Root package
4. Main mod class
5. Initial version
6. ForgeDevEnv revision used
7. Applied project defaults
8. Changed and moved files
9. Placeholder validation
10. Build command and result
11. Unresolved problems

Create `workspace/documentation/project-status.md` if it does not already exist and record that initialization is complete.

## Completion Criteria

Initialization is complete when:

- All required project values are confirmed.
- Project metadata contains the confirmed values.
- Source files use the final package and main class.
- Mixin configuration uses the correct package when present.
- Required license attribution is present.
- Upstream template documentation cannot be mistaken for mod documentation.
- Automated publishing remains disabled.
- No functional template placeholders remain.
- The Gradle build passes.
- Initialization results are documented.
- No commit or push has occurred.

Initialization does not approve Concept and Scope or begin implementation.