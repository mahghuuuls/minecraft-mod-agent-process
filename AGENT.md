# Agent Instructions

This repository defines a controlled process for developing one Minecraft mod at a time.

The repository contains reusable instructions, an external template, local project documentation, and a nested mod repository. Keep these responsibilities separate.

## Determine the Work Mode

Before taking action, determine which mode the user is requesting.

### Process Maintenance

Use this mode only when the user explicitly asks to change this process repository, including:

- `AGENTS.md`
- `README.md`
- Files under `guidelines/`
- Files under `stages/`
- Workspace structure
- The template submodule reference

In this mode:

- Work only in the outer process repository unless instructed otherwise.
- Treat existing guideline and stage files as drafts when the user says they are drafts.
- Collaborate with the user before finalizing process changes.
- Do not modify the nested mod repository.

### Mod Development

Use this mode when the user is developing a specific mod.

In this mode:

- Treat the outer process repository as read-only.
- Follow the approved guidelines and stage definitions.
- Store generated documentation under `workspace/documentation/`.
- Modify source code only inside the nested mod repository.
- Treat the template submodule as read-only.

If the work mode is ambiguous, ask the user before editing files.

## Repository Boundaries

### Process Repository

The outer repository contains reusable process material:

```text
README.md
AGENTS.md
guidelines/
stages/
template/
workspace/
```

Do not modify it during mod development.

### Template Submodule

The canonical template is located at:

```text
template/mah-mod-template/
```

Use it as a reference for expected project structure and build conventions.

Do not:

- Develop the final mod inside the submodule.
- Commit project-specific changes to the submodule.
- Update the submodule revision unless explicitly requested.

### Project Documentation

Project-specific documents belong under:

```text
workspace/documentation/
```

Unless a stage explicitly says otherwise, resolve generated document paths relative to this directory.

For example:

```text
workspace/documentation/concept-and-scope.md
workspace/documentation/requirements.md
workspace/documentation/architecture.md
workspace/documentation/issues/
```

### Mod Repository

The active mod repository must be a single Git repository located under:

```text
workspace/project/<mod-name>/
```

All mod source code, resources, tests, configuration, README changes, changelog changes, and release assets belong to that repository.

There must be exactly one active mod repository per clone of this process repository.

If no mod repository exists, ask the user to provide or clone one. If more than one exists, ask which one is active rather than guessing.

## Required Reading Order

For mod-development work, read instructions in this order:

1. `AGENTS.md`
2. Every applicable file under `guidelines/`
3. `workspace/documentation/project-status.md`, when it exists
4. The definition for the active stage under `stages/`
5. Approved outputs from previous stages
6. The relevant implementation issue, when implementing or reviewing an issue
7. Relevant source code from the active mod repository

Later documents do not override earlier project decisions silently. Report contradictions and ask for resolution.

## Shared Guidelines

The intended shared guideline files are:

```text
guidelines/project-defaults.md
guidelines/collaboration-guidelines.md
guidelines/coding-standards.md
```

- `project-defaults.md` defines stable constraints applying to every mod.
- `collaboration-guidelines.md` defines how to communicate and collaborate with the project owner.
- `coding-standards.md` defines implementation and verification conventions.

Do not duplicate these rules inside generated project documents unless a project-specific decision depends on them.

## Stage Control

The development stages are:

1. Concept and Scope
2. Feasibility Research
3. Requirements Definition
4. Architecture Definition
5. Implementation Plan
6. Implementation
7. Packaging and Release Preparation

Work on only one stage at a time.

Do not:

- Begin a later stage without explicit user approval.
- Treat a draft document as approved.
- Automatically advance after producing an artifact.
- Perform work belonging to a later stage.
- Silently revise an approved earlier-stage decision.

When evidence invalidates an earlier decision:

1. Stop the affected work.
2. Explain the conflict.
3. Identify which earlier stage must be revisited.
4. Wait for the user to approve returning to that stage.
5. Update affected documents explicitly.

The project owner is the only person who can approve a stage.

## Project Status

The active project state is stored in:

```text
workspace/documentation/project-status.md
```

Create it when beginning a new project if it does not exist.

It should identify:

- Mod name
- Mod repository path
- Current stage
- Status of every stage
- Approved output documents
- Current implementation issue
- Blocking questions or decisions

Use these stage statuses:

- **Not Started**
- **In Progress**
- **Awaiting Approval**
- **Approved**
- **Needs Revision**

Do not mark a stage **Approved** without explicit confirmation from the project owner.

Update `project-status.md` when:

- A stage begins.
- An artifact is presented for approval.
- The user approves or rejects a stage.
- The project returns to an earlier stage.
- An implementation issue begins, becomes blocked, enters review, or is completed.

## Generated Artifacts

All planning and process artifacts are written in Markdown unless another format is explicitly required.

Stage documents belong under `workspace/documentation/`.

Implementation source and release-facing repository artifacts belong in the nested mod repository.

Do not place project-specific documents in:

- `guidelines/`
- `stages/`
- The template submodule
- The root of the process repository

Do not invent missing information to fill a document. Omit nonapplicable sections or mark unresolved decisions explicitly.

## Implementation Boundaries

Do not write production code during:

- Concept and Scope
- Feasibility Research
- Requirements Definition
- Architecture Definition
- Implementation Plan

During Implementation:

- Work only on an issue with **Ready** status.
- Confirm that its blockers are complete.
- Keep changes within the issue scope.
- Follow approved requirements and architecture.
- Perform the verification required by the issue.
- Record completion evidence.
- Use a separate agent context for independent review when required by the stage.

During Packaging and Release Preparation:

- Prepare documentation, assets, metadata, and the release artifact.
- Do not introduce new features or unrelated refactoring.
- Return implementation defects to the Implementation stage.
- Never upload or publish the mod.

The project owner performs all CurseForge publication actions.

## Git Safety

The process repository, template submodule, and mod repository have separate Git histories.

Before running Git commands:

- Identify the intended repository.
- Inspect its working tree.
- Preserve unrelated user changes.
- Do not assume a clean working tree.
- Do not revert changes that were not made as part of the current task.

Never:

- Commit unless explicitly requested.
- Push unless explicitly requested.
- Open a pull request unless explicitly requested.
- Publish a release unless explicitly requested.
- Use destructive Git commands without explicit permission.
- Commit project-specific files to the process repository.
- Commit process instructions to the mod repository.

When reporting Git state, state which repository was inspected.

## Approval and External Actions

Explicit permission is required before:

- Committing
- Pushing
- Opening or merging a pull request
- Updating the template submodule
- Uploading files
- Publishing a release
- Modifying external services

Approval for one action does not imply approval for later actions.

CurseForge publication is always performed manually by the project owner.

## Completion Behavior

At the end of a task:

- State what was completed.
- Identify files created or changed.
- Report verification performed.
- Report unresolved questions, risks, or failures.
- Do not claim completion when required verification has not occurred.
- Do not begin the next stage automatically.