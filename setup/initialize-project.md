# Initialize Project

## Purpose

Define the mechanical procedure for creating an independent mod repository from the configured compatible template.

This procedure is executed only during the Project Initialization stage.

## Inputs

### Shared Defaults

Read:

```text
setup/template-defaults.properties
```

This file defines shared Minecraft, Java, distribution, branch, syntax, and license preferences. Loader, template, and project identity are project-specific.

### Project Configuration

Read:

```text
workspace/project.properties
```

This ignored file defines the approved repository, loader, runtimes, distribution platforms, template, project identity, and any operational overrides.

### Approved Project Documents

Read:

- `workspace/documentation/concept-and-scope.md`
- `workspace/documentation/feasibility-research.md`
- `workspace/documentation/requirements.md`
- `workspace/documentation/architecture.md`

These documents provide the mod name, purpose, description, mod ID, package structure, main class, dependencies, integrations, and architectural constraints.

## Resolve Configuration

Resolve operational values before cloning anything.

At minimum, establish:

```text
minecraft_version
mod_loader
supported_runtimes
distribution_platforms
template_repository_url
template_repository_ref
project_repository_url
project_directory_name
project_default_branch
root_package
mod_authors
minecraft_username
preferred_development_java_version
target_java_version
use_modern_java_syntax
license
```

Project configuration supplies project-specific values and may override shared preferences. Every required value must be nonempty and consistent with approved documents before cloning.

Do not permit an operational override to silently contradict approved project documentation.

Do not log credentials or embed authentication tokens in generated documents.

## Validate the Template

Inspect the configured template repository and ref.

Confirm that it:

- Is cloneable
- Has a compatible reuse license
- Represents a Minecraft 1.12.2 project for the approved loader and runtimes
- Supports the required development and release Java versions
- Provides a usable build mechanism
- Contains identifiable source and metadata structures

Do not assume loader-specific filenames, properties, packages, starter classes, or placeholders.

When compatibility cannot be established through repository inspection, stop and report the missing evidence.

## Validate the Final Repository

The final repository must already exist on GitHub and contain no commits.

Confirm that:

- The URL identifies the intended repository.
- The authenticated user has the required access.
- The repository has no branch history or initial commit.
- No README, license, or `.gitignore` was created on GitHub.
- The configured local destination does not contain unrelated files.

Do not overwrite or repurpose a nonempty repository.

## Prepare Runtime Directories

Use:

```text
workspace/template/source/
workspace/project/<project_directory_name>/
```

Both locations are ignored by the process repository.

If either location already exists:

- Inspect it before taking action.
- Reuse it only when its identity and state match the current configuration.
- Never delete unknown or user-created files automatically.
- Stop and ask when safe reuse cannot be established.

## Clone the Template

Clone the configured template into:

```text
workspace/template/source/
```

Resolve the configured ref as a branch, tag, or commit.

After checkout, record:

- Repository URL
- Requested ref
- Resolved commit SHA
- Whether required submodules exist
- Template license

If the template requires submodules, initialize only those required by its documented build and verify their licenses. Their Git metadata must also be excluded from the final project.

Do not modify or commit inside the runtime template clone.

## Clone the Final Repository

Clone the empty final repository into:

```text
workspace/project/<project_directory_name>/
```

The clone must retain:

- Its own `.git` directory
- Its own `origin` pointing to `project_repository_url`

It must not receive:

- The template's `.git`
- A remote pointing to the template
- The template's commits, branches, tags, hooks, or reflogs

Establish the branch named by `project_default_branch`, normally `main`.

Before copying files, verify:

- The final repository has no commits.
- The current local branch is correct.
- `origin` points only to the final repository.

## Copy Template Content

Copy the template working tree into the final repository.

The copy must:

- Include hidden project files such as `.gitignore` and `.github/`
- Exclude every template `.git` directory or `.git` file
- Exclude template Git hooks, refs, logs, objects, and configuration
- Avoid copying generated build output, IDE caches, or runtime directories
- Preserve file permissions required by scripts such as the Gradle wrapper

When required template submodules were materialized, copy only their working content and exclude their Git metadata.

After copying, verify that the only Git metadata in the final project belongs to its own repository.

## Apply Shared Defaults

Read values from `setup/template-defaults.properties` instead of hardcoding them.

Map applicable shared preferences to the fetched template's actual structure:

- Minecraft version
- Preferred development Java version when supported
- Target Java version
- Modern Java syntax setting when supported
- Default license
- Final project branch

The template may use different filenames or configuration formats. Inspect and edit the appropriate structured files instead of assuming a particular property name exists.

Preserve unrelated template settings.

## Apply Approved Project Values

Read project-specific values from `workspace/project.properties` and approved documents, including:

- Selected loader and supported runtimes
- Approved distribution platforms
- Root package
- Author metadata
- Development username when used
- Mod display name
- Mod ID
- Description
- Final package
- Main class
- Required dependencies
- Required integrations
- Client, server, and shared-code constraints

Update the template's actual:

- Build metadata
- Mod metadata
- Package directories
- Package declarations
- Starter class
- Resource paths
- Mixin or coremod configuration when approved
- Dependency configuration when required for the baseline

Do not enable optional template capabilities unless the approved architecture requires them.

Do not add gameplay implementation.

## Preserve Licensing

Apply the configured project license while preserving all upstream obligations.

- Keep required template copyright and license notices.
- Keep notices required by copied dependencies or source.
- Attribute original project work using the configured author metadata.
- If the project license differs from the template license, preserve the upstream license separately and document which content it covers.
- Never treat a project license override as permission to remove upstream attribution.

Record all retained notices in the initialization artifact.

## Remove Misleading Template Content

Inspect README files, changelogs, example descriptions, sample assets, placeholder classes, and comments.

Remove or reset content that describes the template rather than the mod.

Do not create the final user-facing README or changelog during Initialization. Those belong to Release Presentation.

Retain technical documentation only when it remains accurate and useful for developing the initialized project.

## Disable Automatic Publication

Inspect:

- GitHub workflows
- Gradle publishing configuration
- Maven publication configuration
- Distribution-platform publishing tasks
- Scripts triggered by tags or pushes
- Credential and token references

Ensure that no push, tag, build, or workflow can automatically publish the mod.

- Disable or remove publication-only automation.
- Preserve useful build-only validation when it does not publish.
- Keep publication flags false when the template provides them.
- Never add credentials or tokens.
- Never upload or publish during Initialization.

Document what was disabled, removed, or preserved.

## Validate Template Placeholders

Discover placeholder values from the fetched template instead of relying only on a fixed list.

Check:

- Source packages
- Class names
- Mod IDs
- Display names
- Descriptions
- Author metadata
- Development usernames
- Resource paths
- Mixin packages
- Build properties
- Example assets
- Update URLs
- Repository URLs

Search for common markers such as `example`, `modid`, `placeholder`, and `TODO`, but evaluate every match in context.

Do not declare success while functional placeholders remain. Example text in explanatory comments may remain when it cannot affect the project.

## Verify Repository Independence

In the final repository, verify:

- The current branch matches `project_default_branch`.
- `origin` points to `project_repository_url`.
- No template remote exists.
- No template commits exist.
- No template tags or branches were copied.
- The repository has no commit before the approved initial commit.
- Git status includes only expected initialized files.

Record the results.

## Build and Inspect

Determine the correct build command from the fetched template's documentation and build files.

Prefer the supplied Gradle wrapper when present.

For a Gradle template, the expected verification is generally equivalent to:

```bash
./gradlew clean build
```

On Windows:

```powershell
.\gradlew.bat clean build
```

Do not assume those commands apply to a non-Gradle compatible template.

Verify:

- The build completes.
- Tests pass when present.
- Processed mod metadata contains the approved values.
- The main mod class and package compile.
- The produced artifact is the expected normal distributable mod artifact for the selected loader.
- The artifact targets the approved Java runtime version.
- No development, sources, or Javadoc artifact is mistaken for the release artifact.

Record the command, environment, output result, and produced artifact.

## Prepare Commit Review

Before staging or committing:

- Inspect Git status.
- Review the complete diff.
- Confirm no template Git metadata exists.
- Confirm no secrets or local paths were copied.
- Summarize all changed and removed files.
- Present placeholder and build results.
- Present known limitations.
- Propose the initial commit message.

Do not stage or commit until the project owner explicitly approves the first local commit.

## Create the Initial Commit

After explicit approval:

1. Stage only the initialized project baseline.
2. Review the staged diff.
3. Create the first commit on `project_default_branch`.
4. Use a clear message such as:

```text
Initialize <mod-name> from configured template
```

5. Record the resulting commit SHA.

Do not push.

The final repository must have exactly one local commit when Initialization completes.

## Produce the Initialization Record

Create:

```text
workspace/documentation/project-initialization.md
```

Record:

- Final repository URL and directory
- Final branch
- Template repository URL
- Requested template ref
- Resolved template commit SHA
- Applied defaults and project values
- Template content removed or preserved
- License notices
- Publication safety changes
- Placeholder validation
- Build command and result
- Generated baseline artifact
- Initial commit SHA
- Remaining limitations

Do not include secrets.

## Failure Handling

Stop without committing when:

- The template is incompatible.
- The final repository is not empty.
- Required values are missing or contradictory.
- Template content cannot be copied without Git history.
- Required license obligations cannot be satisfied.
- Functional placeholders remain.
- Automatic publication cannot be confidently disabled.
- The baseline build fails.
- Repository identity, branch, or remote verification fails.

Report the failure, preserve evidence, and identify the earlier decision or configuration that must change.
