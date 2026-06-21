# Project Initialization

## Purpose

Create a clean, independent final mod repository from the configured compatible template and the approved project documents.

Initialization prepares the real codebase for implementation planning. It does not implement gameplay features.

## Main Question

> Is the independent project repository correctly initialized and ready for implementation planning?

## Required Input

- `guidelines/project-defaults.md`
- `guidelines/collaboration-guidelines.md`
- `guidelines/coding-standards.md`
- `setup/template-defaults.properties`
- `workspace/project.properties`
- `setup/initialize-project.md`
- `workspace/documentation/concept-and-scope.md`
- `workspace/documentation/feasibility-research.md`
- `workspace/documentation/requirements.md`
- `workspace/documentation/architecture.md`

Concept and Scope, Feasibility Research, Requirements Definition, and Architecture Definition must be approved before this stage begins.

## Objectives

Establish:

- The exact template repository and revision used
- A local clone of the empty final repository
- An independent `main` branch for the final project
- A copy of the template without its Git history
- Project metadata and structure derived from approved documents
- Shared defaults derived from the configured properties
- Required upstream license attribution
- Disabled automatic publication
- A verified, buildable baseline
- The first approved local commit
- A project-initialization record for later stages

## Compatible Template Contract

Initialization may use any configured template that:

- Is accessible through Git
- Permits reuse under its license
- Represents a Minecraft Forge 1.12.2 mod project
- Supports the required Java 25 development environment and Java 8 release target
- Includes a Gradle wrapper or another clearly documented build mechanism
- Exposes enough structure to identify source code, metadata, resources, and configuration
- Can be copied without requiring its Git history

If the configured repository does not satisfy this contract, stop and report the incompatibility. Do not force an unrelated repository into the workflow.

## Preconditions

Before initialization:

- Exactly one active project configuration exists at `workspace/project.properties`.
- The configured final GitHub repository exists.
- The final GitHub repository contains no commits.
- The configured project directory is not already occupied by unrelated files.
- The configured template repository and ref are accessible.
- All required project identity and architecture decisions are present in approved documents.
- No unexplained changes exist in the outer process repository.

If a precondition fails, mark the stage blocked and identify the required correction.

## In Scope

- Resolve template and project configuration
- Clone the configured template into `workspace/template/`
- Clone the empty final repository into `workspace/project/`
- Establish the final local branch
- Copy template files without Git metadata
- Apply approved project values and shared defaults
- Preserve required license notices
- Remove or reset template-specific user documentation
- Disable automatic publication behavior
- Check for unresolved functional placeholders
- Build and inspect the initialized project
- Create the first approved local commit
- Generate `workspace/documentation/project-initialization.md`

## Out of Scope

Do not:

- Implement gameplay features
- Change approved requirements or architecture
- Add speculative dependencies or infrastructure
- Redesign the fetched template
- Upgrade template dependencies independently
- Create final user-facing documentation
- Push the final project repository
- Create a pull request
- Upload or publish a release
- Modify the outer process repository

## Desired AI Behavior

Act as a careful project initializer.

- Follow `setup/initialize-project.md`.
- Treat the configured template as input, not as the final project.
- Inspect the fetched template instead of assuming specific filenames or placeholders.
- Use approved documents as the source of project-specific decisions.
- Use the properties files as the source of operational and shared defaults.
- Preserve template capabilities that do not conflict with approved decisions.
- Do not copy Git metadata or template commit history.
- Do not invent missing project values.
- Stop when the template, documentation, or repository state is incompatible.
- Report every created, copied, modified, moved, and removed file.
- Run meaningful verification before requesting commit approval.
- Never push.

## Source Precedence

When values conflict, use this order:

1. Explicit project-owner decision recorded in an approved project document
2. Approved project-specific documents
3. Overrides in `workspace/project.properties`
4. Defaults in `setup/template-defaults.properties`
5. Existing values from the fetched template

Do not resolve contradictions silently. Operational overrides must not change approved behavior.

## Process

1. Read all required inputs.
2. Resolve template defaults and project-specific overrides.
3. Validate the compatible-template contract.
4. Confirm that the final GitHub repository is empty.
5. Clone the configured template into the ignored template workspace.
6. Record the exact resolved template commit.
7. Clone the empty final repository into the configured project directory.
8. Establish the configured final branch, normally `main`.
9. Copy template contents without Git metadata.
10. Apply shared defaults and approved project values.
11. Preserve license notices and remove misleading template documentation.
12. Disable automatic publication without removing useful build-only automation.
13. Validate placeholders, repository identity, branch, and remote.
14. Determine and run the appropriate build.
15. Inspect the generated baseline artifact.
16. Generate a draft `workspace/documentation/project-initialization.md`.
17. Present the changes and verification evidence.
18. Obtain explicit approval for the first local commit.
19. Create the local initial commit.
20. Record its SHA in `workspace/documentation/project-initialization.md`.
21. Present the completed stage for approval.

## Output Artifact

Produce:

```text
workspace/documentation/project-initialization.md
```

It must contain:

1. **Final Project Repository**
2. **Final Project Branch**
3. **Template Repository**
4. **Requested Template Ref**
5. **Resolved Template Commit**
6. **Applied Shared Defaults**
7. **Applied Project Values**
8. **Copied and Removed Template Content**
9. **License and Attribution**
10. **Publication Safety**
11. **Placeholder Validation**
12. **Build Command and Result**
13. **Generated Baseline Artifact**
14. **Initial Commit SHA**
15. **Remaining Limitations**

Do not include credentials, tokens, or other secrets.

## Commit Approval

Before committing, present:

- Final repository path
- Git status
- Complete change summary
- Placeholder validation
- Build result
- Known limitations
- Proposed commit message

Create the first commit only after explicit project-owner approval.

The commit must:

- Be created in the final project repository
- Be created on the configured final branch
- Contain only the initialized baseline
- Use a clear message such as `Initialize <mod-name> from configured template`
- Remain local

Approval to create the commit does not authorize pushing it.

## Stage Approval

- Treat this stage and its artifacts as **In Progress** while work is being developed.
- When the output is ready for review, update `workspace/documentation/project-status.md` to **Awaiting Approval** and present the complete result.
- Only the project owner may mark the stage **Approved**.
- Do not begin the next stage automatically.
- If new evidence invalidates an earlier approved stage, stop, mark the affected stages **Needs Revision**, identify the conflict, and resume only after the earlier stage is corrected and approved again.

## Completion Criteria

This stage is complete when:

- The configured template satisfied the compatibility contract.
- The exact template commit is recorded.
- The final repository has its own `.git` metadata and `origin`.
- The final repository contains no template Git history or template remote.
- The final branch matches the configured project branch.
- Shared defaults and approved project values are applied.
- Required upstream attribution is preserved.
- Automatic publication is disabled.
- No unresolved functional template placeholders remain.
- The initialized project builds successfully.
- The baseline artifact has been inspected.
- The first local commit was explicitly approved and created.
- The initial commit SHA is recorded.
- Nothing was pushed.
- The project owner explicitly approves the stage.

Completion makes the initialized codebase available to Implementation Plan. It does not authorize feature implementation.
