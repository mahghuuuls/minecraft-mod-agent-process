# Agent Instructions

This repository provides a reusable process for developing one Minecraft mod at a time with AI agents.

## Work Mode

Determine the requested mode before changing files.

### Process Maintenance

Use this mode when the user asks to change this process repository. Work only in the outer repository unless instructed otherwise. Do not modify a nested mod repository.

### Mod Development

Use this mode when working on a specific mod:

- Treat the outer process repository as read-only.
- Follow the shared guidelines and active stage definition.
- Store generated process documents under `workspace/documentation/`.
- Modify mod files only in the active repository under `workspace/project/`.
- Treat `workspace/template/` as disposable source material.

If the mode is ambiguous, ask before editing.

## Repository Boundaries

- **Process repository:** reusable instructions, setup material, and workspace structure.
- **Template workspace:** an ignored clone under `workspace/template/`; never the development target.
- **Project documentation:** ignored, project-specific artifacts under `workspace/documentation/`.
- **Mod repository:** exactly one independent Git repository under `workspace/project/<mod-name>/`.

Do not copy template Git metadata into the mod repository. If there is no active mod repository, request its configuration. If more than one exists, ask which one is active.

## Required Reading

For mod-development work, read in this order:

1. `AGENTS.md`
2. Every file under `guidelines/`
3. `workspace/documentation/project-status.md`, when present
4. The active stage under `stages/`
5. The approved artifacts referenced by that stage
6. The relevant implementation issue and source code, when applicable

Do not silently resolve contradictions between sources. Follow the precedence and revision rules in `guidelines/process-control.md`.

## Instruction Ownership

- `guidelines/project-defaults.md`: stable defaults for every mod.
- `guidelines/process-control.md`: stage order, status, approval, artifacts, and backward transitions.
- `guidelines/collaboration-guidelines.md`: communication, editing, Git authorization, and completion reporting.
- `guidelines/coding-standards.md`: implementation and verification conventions.
- `setup/initialize-project.md`: operational initialization procedure.
- `stages/*.md`: concerns, outputs, and completion criteria unique to each stage.

When instructions overlap, the file that owns the subject is authoritative. Other files should reference it instead of restating it.

## Execution

Identify the active stage from `project-status.md` or ask the project owner. Perform only work allowed by that stage, update its artifacts and status as required by `process-control.md`, and stop after presenting the stage result for approval.
