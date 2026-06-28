# Collaboration Guidelines

This file is the authoritative source for collaboration, file-editing discipline, Git authorization, external actions, and completion reporting.

## Accuracy

- Prefer correctness over agreement or speed.
- Identify ambiguity, contradictions, missing information, hidden assumptions, and unrealistic expectations.
- Distinguish confirmed facts, reasonable inferences, and unresolved questions.
- Do not invent information.
- State uncertainty and what evidence would resolve it.
- Use primary, authoritative, and version-specific sources when research is required.
- Do not assume guidance for newer Minecraft versions applies to Minecraft 1.12.2.

## Questioning and Decisions

- Ask one focused question at a time when project-owner input is required.
- Do not ask questions that approved artifacts, repository inspection, or research can answer.
- Present materially different interpretations rather than choosing silently.
- Challenge feature creep and conflicts with approved scope.
- Present meaningful alternatives with trade-offs and make a recommendation.
- Follow `guidelines/process-control.md` when new evidence invalidates an approved decision.

## Communication

- Keep responses concise, direct, and technically precise.
- Explain unfamiliar terminology when it affects a decision.
- During troubleshooting, prefer short steps and wait for results.
- Periodically summarize shared understanding during alignment-heavy work.
- Report mistakes, uncertainty, and failed checks plainly.
- Do not claim completion while required work or verification remains.

## Workflow Feedback

When the project owner corrects the agent, identifies friction, rejects a default, asks why the process is doing something, or points out a better way to run future mods, consider whether the interaction should be recorded in:

```text
workspace/documentation/workflow-feedback.md
```

Follow the workflow feedback log rules in `guidelines/process-control.md`.

Do not let feedback logging derail the active task. Update the log at a natural checkpoint unless the process issue is blocking the current work.

Do not edit versioned process files during mod development just because a feedback entry exists. Process file changes require Process Maintenance mode.

## File Changes

- Inspect existing files and repository state before editing.
- Explain the intended scope before making changes.
- Preserve unrelated user changes.
- Never revert work outside the current task.
- Keep edits within the active repository, stage, issue, or approved maintenance scope.
- Follow existing conventions unless an approved decision changes them.

## Git and External Actions

Before a Git operation, identify the target repository and inspect its working tree. The process repository, runtime template, and mod repository have separate histories.

Explicit authorization is required for each of these actions:

- Commit
- Push
- Create or merge a pull request
- Change the configured template source or ref
- Upload a file
- Modify an external service
- Publish a release

Authorization for one action does not authorize another. Do not use destructive Git operations without explicit permission. Preserve unrelated changes and report which repository was inspected or changed.

During Implementation, after each completed issue or approved vertical slice, ask the project owner whether to create a commit before moving to the next issue. Follow the commit checkpoint rules in `stages/7-implementation.md`.

Commit messages must be repo-facing by default:

- Describe the actual repository change.
- Do not reference workflow issue IDs, internal issue names, stage documents, or process-only context unless explicitly requested.
- Assume a future reader has access to the Git repository but not the workflow artifacts.

Publication to every approved distribution platform is performed manually by the project owner. Agents may prepare handoffs but may not upload or publish the mod.

## Completion Reporting

At the end of work:

- Summarize what was completed.
- Identify changed files and relevant commits.
- Report verification and its result.
- Report unresolved questions, limitations, failures, or risks.
- Stop without beginning another stage or unrelated task.
