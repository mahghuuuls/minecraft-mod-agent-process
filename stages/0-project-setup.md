# Project Setup

## Purpose

Prepare the process workspace, establish the project scenario, and guide the project owner through the operational decisions required to begin the correct workflow.

This stage is interactive onboarding. It does not define mod behavior, prove technical feasibility, initialize a final codebase, or implement features.

## Main Question

> Is the workspace sufficiently configured to begin the correct workflow, with later prerequisites understood and assigned?

## Required Input

- The project owner's initial request
- `guidelines/project-defaults.md`
- `setup/template-defaults.properties`
- `setup/project.properties.example`
- Existing `workspace/project.properties`, when present
- Existing workspace documents and repositories, when present

## Objectives

Establish:

- Whether the user is creating, adopting, or changing a mod
- The proposed workflow
- The current tool and workspace state
- The project repository state or the stage by which it must exist
- A provisional template choice for Initial Development
- Known operational overrides
- Deferred prerequisites and their deadlines
- A clear starting point requiring no README knowledge

## In Scope

- Explain the workspace and agent-guided process briefly
- Inspect existing configuration and repositories
- Check available Git and Java installations
- Record IntelliJ IDEA availability or installation as a pending prerequisite
- Create required ignored runtime directories
- Create or update `workspace/project.properties` when enough real values are known
- Explain the configured default template
- Research template alternatives when requested
- Record a provisional template candidate or defer final validation to Feasibility Research
- Explain repository requirements for the selected scenario
- Propose the applicable workflow
- Produce `workspace/documentation/project-setup.md`

## Out of Scope

Do not:

- Define features or detailed mod behavior
- Conclude that the concept is technically feasible
- Perform architecture design
- Clone or copy a template into the final project
- Initialize the final mod repository
- Modify existing mod source
- Create commits or push
- Create a GitHub repository or modify an external service without separate explicit authorization
- Require a new-mod repository before Concept and Scope begins
- Write fake placeholder values into machine-readable configuration

## Desired AI Behavior

Act as an onboarding coordinator.

- Inspect before asking questions.
- Do not direct the user back to the README.
- Explain only the immediate setup decision.
- Ask one focused question at a time.
- Distinguish required-now values from prerequisites that may be deferred.
- Offer the configured default before researching alternatives.
- Explain trade-offs when presenting template candidates.
- Record uncertainty instead of guessing.
- Preserve existing repositories and unrelated workspace content.
- Present the setup result and proposed workflow for explicit approval.

## Scenario Classification

Classify exactly one scenario:

### New Mod

Use when no implementation or approved baseline exists.

- Propose Initial Development.
- Explain that an empty final GitHub repository is required before Project Initialization, not before Concept and Scope.
- Collect repository URL and directory name now only when the owner already has them.
- Otherwise record them as deferred prerequisites due before Project Initialization.

### Existing Mod Adoption

Use when implementation or release history exists without an approved process baseline.

- Propose Existing Project Adoption.
- Require the existing repository identity before adoption begins.
- Preserve its history and never apply the empty-repository rule.

### Change to an Approved Mod

Use when an approved baseline exists and another feature, fix, compatibility update, or refactor is requested.

- Propose Change Cycle.
- Confirm that the configured repository and baseline still identify the intended mod.
- Reuse approved setup unless operational configuration changed.

If evidence is insufficient to classify the scenario, ask rather than choosing silently.

## Environment Inspection

Inspect and record:

- Operating system
- Git availability and version
- Java availability and version
- IntelliJ IDEA availability when it can be determined
- Existing process-repository status
- Existing runtime directories
- Existing nested repositories
- Existing configuration and setup artifacts

Project defaults define the intended environment. Missing tools may be installed later when they are not needed by the first stage, but record the stage by which each is required.

Do not install software without explicit authorization.

## Template Guidance

For Initial Development:

1. Read the configured default template repository and ref.
2. Explain briefly why it is the default.
3. Ask whether to accept it provisionally or investigate alternatives.
4. If alternatives are requested, research current candidates using authoritative, version-specific evidence.
5. Compare Minecraft 1.12.2 support, Cleanroom compatibility, Java development and runtime targets, build tooling, license, reuse conditions, and maintenance state.
6. Recommend a provisional candidate with trade-offs.
7. Store approved project-specific overrides in `workspace/project.properties`.

Template choice during setup is provisional. Feasibility Research validates that it fits the approved concept and technical constraints. Do not clone or prototype templates during this stage.

Existing Project Adoption and Change Cycle use the existing repository's build system unless later approved work changes it.

## Project Configuration

Use:

```text
workspace/project.properties
```

Only write values that are known and approved.

Relevant values may include:

- `project_repository_url`
- `project_directory_name`
- `template_repository_url`
- `template_repository_ref`
- `project_default_branch`
- `license`

Shared defaults remain in `setup/template-defaults.properties`. Do not edit shared defaults during mod development.

If a new mod's repository or directory name is deferred, do not create an invalid properties file merely to complete the stage. Record the missing values and their deadline in the setup artifact.

## Process

1. Read the shared defaults and inspect the workspace.
2. Explain that setup can be completed interactively.
3. Identify the scenario.
4. Inspect available environment tools and repositories.
5. Resolve known repository configuration.
6. For a new mod, resolve or provisionally defer template selection.
7. Write only approved known operational values.
8. Record deferred prerequisites and the stage by which each is required.
9. Propose the applicable workflow.
10. Produce the setup artifact.
11. Present the artifact and workflow selection for separate explicit approval.

## Output Artifact

Produce:

```text
workspace/documentation/project-setup.md
```

It should contain:

1. Setup date
2. Classified scenario and evidence
3. Proposed workflow
4. Environment inspection
5. Repository state
6. Configuration written
7. Provisional template decision and evidence
8. Deferred prerequisites and deadlines
9. Blocking problems
10. Owner approvals

Do not include credentials or secrets.

## Completion Criteria

This stage is complete when:

- The scenario is supported by inspected evidence and owner confirmation.
- The proposed workflow is explicit.
- Required-now operational values are configured.
- Future prerequisites have explicit deadlines.
- The template decision is recorded or legitimately not applicable.
- No unresolved blocker prevents the selected workflow's first stage.
- `project-setup.md` is approved.
- The project owner separately approves the proposed workflow.

Completion permits the selected workflow to begin. It does not approve any development stage.
