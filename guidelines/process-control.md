# Process Control

This file is the authoritative source for stage order, stage status, approvals, generated process artifacts, and backward transitions.

## Stage Sequence

| Stage | Definition | Primary Output |
| --- | --- | --- |
| 1. Concept and Scope | `stages/1-concept-and-scope.md` | `concept-and-scope.md` |
| 2. Feasibility Research | `stages/2-feasibility-research.md` | `feasibility-research.md` |
| 3. Requirements Definition | `stages/3-requirements-definition.md` | `requirements.md` |
| 4. Architecture Definition | `stages/4-architecture-definition.md` | `architecture.md` |
| 5. Project Initialization | `stages/5-initialization.md` | `project-initialization.md` |
| 6. Implementation Plan | `stages/6-implementation-plan.md` | `implementation-plan.md` and `issues/` |
| 7. Implementation | `stages/7-implementation.md` | Completed code and issue evidence |
| 8. Packaging and Release Preparation | `stages/8-packaging-release-preparation.md` | `release-preparation.md` and release handoff |

Work on one stage at a time. A later stage may begin only after the project owner approves every preceding stage.

## Project Status

Track the project in:

```text
workspace/documentation/project-status.md
```

Create it when the first stage begins. Record:

- Mod name and active repository path
- Current stage
- Status of every stage
- Approved output artifacts
- Current implementation issue, when applicable
- Blocking questions or decisions

Use only these stage statuses:

- **Not Started**
- **In Progress**
- **Awaiting Approval**
- **Approved**
- **Needs Revision**

Implementation issue statuses are defined by the Implementation Plan stage.

## Stage Lifecycle

1. Confirm that required preceding stages are **Approved**.
2. Mark the active stage **In Progress**.
3. Perform only that stage's work.
4. Create or update its draft artifacts.
5. When the complete result is ready, mark the stage **Awaiting Approval** and present it.
6. Revise the result in response to review.
7. Mark the stage **Approved** only after explicit confirmation from the project owner.
8. Stop. Do not begin the next stage automatically.

A generated artifact, completed check, or approval of a separate action does not constitute stage approval.

## Backward Transitions

When new evidence invalidates an approved decision:

1. Stop affected work.
2. Identify the conflicting evidence and every affected artifact.
3. Mark the earliest affected stage and dependent stages **Needs Revision**.
4. Ask the project owner to approve returning to that stage.
5. Revise and reapprove affected artifacts in stage order.
6. Resume later work only when its prerequisites are approved again.

Do not conceal an upstream problem with an implementation workaround or a downstream document change.

## Artifact Rules

All reusable process artifacts are Markdown unless another format is explicitly required. Store them under:

```text
workspace/documentation/
```

Paths written without a directory in the stage table are relative to that directory. Mod source, repository documentation, release assets, and build outputs belong in the nested mod repository.

Approved artifacts are authoritative for project-specific decisions. Do not duplicate their full content in later artifacts; reference stable requirement, architecture, or issue identifiers instead. Record a derived detail again only when the later artifact must establish traceability or provide self-contained execution context.

Omit nonapplicable sections and identify unresolved decisions explicitly. Never invent information to make an artifact appear complete.

## Change Control

A stage may refine only decisions it owns. Changes affecting an earlier stage follow the backward-transition procedure. Operational properties may override reusable defaults but may not silently override approved behavior, architecture, compatibility, licensing, or distribution decisions.
