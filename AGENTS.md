# Agent Instructions

This repository provides a reusable process for developing one Minecraft mod at a time with AI agents.

## Work Mode

Determine the requested mode before changing files.

### Process Maintenance

Use this mode when the user asks to change this process repository. Work only in the outer repository unless instructed otherwise. Do not modify a nested mod repository.

### Mod Development

Use this mode when working on a specific mod:

- Treat the outer process repository as read-only.
- Follow the shared guidelines, selected workflow, and active stage.
- Store generated process documents under `workspace/documentation/`.
- Modify mod files only in the active repository under `workspace/project/`.
- Treat `workspace/template/` as disposable source material.

If the mode is ambiguous, ask before editing.

## Repository Boundaries

- **Process repository:** reusable instructions, setup material, and workspace structure.
- **Template workspace:** an ignored clone under `workspace/template/`; never the development target.
- **Project documentation:** ignored, project-specific artifacts under `workspace/documentation/`.
- **Mod repository:** exactly one independent Git repository under `workspace/project/<mod-name>/`.

Do not copy template Git metadata into the mod repository. If there is no active mod repository, use the selected workflow to determine whether to initialize or clone one. If more than one exists, ask which one is active.

## Workflow Selection

Before beginning new mod-development work, inspect `workspace/documentation/project-status.md`, the configured repository, and existing approved artifacts.

Select exactly one workflow:

| Condition | Workflow |
| --- | --- |
| An active workflow is recorded | Resume that workflow |
| No implementation or approved baseline exists | `workflows/initial-development.md` |
| An existing implementation has no approved process baseline | `workflows/existing-project-adoption.md` |
| An approved baseline exists and a change is requested | `workflows/change-cycle.md` |

Present the selection and evidence to the project owner before starting a new workflow. Do not classify an existing repository as empty initialization input or treat unapproved documents as a baseline. Ask when the repository state is ambiguous.

Record the approved workflow in `project-status.md`.

## Required Reading

For mod-development work, read in this order:

1. `AGENTS.md`
2. The core guideline files listed under **Instruction Ownership**
3. `workspace/documentation/project-status.md`, when present
4. The selected file under `workflows/`
5. The active stage under `stages/`, when the workflow invokes one
6. Any specialized guideline explicitly referenced by the active workflow or stage
7. The approved artifacts referenced by the workflow or stage
8. The relevant implementation issue and source code, when applicable

Do not silently resolve contradictions between sources. Follow the precedence and revision rules in `guidelines/process-control.md`.

## Instruction Ownership

- `guidelines/project-defaults.md`: stable defaults for every mod.
- `guidelines/process-control.md`: workflow and stage status, approval, artifacts, and backward transitions.
- `guidelines/collaboration-guidelines.md`: communication, editing, Git authorization, and completion reporting.
- `guidelines/coding-standards.md`: implementation and verification conventions.
- Specialized guideline files under `guidelines/`: task-specific instructions read only when an active workflow or stage references them.
- `workflows/*.md`: scenario selection consequences, routing, and workflow-specific behavior.
- `setup/initialize-project.md`: operational initialization procedure for a new repository.
- `stages/*.md`: concerns, outputs, and completion criteria unique to reusable stages.

When instructions overlap, the file that owns the subject is authoritative. Other files should reference it instead of restating it.

## Execution

Resume the active workflow or obtain approval for a new workflow selection. Follow its route one checkpoint or stage at a time, update `project-status.md`, and stop whenever owner approval is required. Never advance to another stage, workflow, or change cycle automatically.
