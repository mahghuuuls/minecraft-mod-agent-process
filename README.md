# Minecraft Mod Agent Process

A reusable workspace for developing, adopting, and iteratively updating one Minecraft 1.12.2 mod at a time with AI agents.

The repository separates reusable instructions from ignored project documentation, temporary template files, and the independent final mod repository.

## Repository Structure

```text
minecraft-mod-agent-process/
├── AGENTS.md
├── guidelines/
├── workflows/
├── stages/
├── references/
├── setup/
└── workspace/
    ├── documentation/
    ├── artwork/
    ├── project/
    ├── project.properties
    └── template/
```

- `AGENTS.md` is the agent entry point and workflow router.
- `guidelines/` contains core rules, process control, and specialized on-demand instructions.
- `workflows/` defines scenario-specific agent behavior and stage routing.
- `stages/` contains reusable stage instructions.
- `setup/` contains configuration examples and new-project initialization.
- `references/` contains curated technical links.
- `workspace/` contains ignored, project-specific runtime data, including temporary artwork and references.

## Supported Workflows

- **Initial Development:** create and prepare the first release of a new mod.
- **Existing Project Adoption:** document and approve the baseline of an existing mod without changing it.
- **Change Cycle:** deliver an iterative feature, fix, compatibility update, or refactor against an approved baseline.

The agent selects a workflow from repository state and asks for approval before beginning it. See `guidelines/process-control.md` for status, approval, and artifact rules.

## Prerequisites

Install Git and the development environment specified by `guidelines/project-defaults.md`.

For Initial Development, create an empty GitHub repository without a README, license, `.gitignore`, or initial commit. Existing Project Adoption and Change Cycle use the existing repository with its history intact.

## Clone

```bash
git clone https://github.com/mahghuuuls/minecraft-mod-agent-process.git
cd minecraft-mod-agent-process
```

No submodules are required. Use a separate clone of this process repository for each mod project.

## Configure a Project

Create the ignored project configuration:

```bash
cp setup/project.properties.example workspace/project.properties
```

Set the GitHub repository and its local directory name:

```properties
project_repository_url=https://github.com/mahghuuuls/example-mod.git
project_directory_name=example-mod
```

For Initial Development, the repository must be empty before Initialization. For adoption or a change cycle, it is the existing mod repository.

Shared template and identity defaults remain in `setup/template-defaults.properties`. Project-specific overrides belong in `workspace/project.properties`.

## Run the Process

1. Start the agent from the process repository root.
2. Describe whether you are creating, adopting, or changing a mod.
3. Review and approve the proposed workflow.
4. Review and explicitly approve each required checkpoint and stage.
5. Open and edit only the mod repository under `workspace/project/`.
6. Publish prepared releases to CurseForge manually.

Canonical project documents remain under `workspace/documentation/`. Change-specific plans and evidence are stored under `workspace/documentation/cycles/<cycle-id>/`. These files are ignored by the process repository; preserve them separately when long-term history matters.

## Git Boundaries

The outer process repository, temporary template clone, and final mod repository have separate purposes and histories. Before running Git commands, confirm the target:

```bash
git status
git -C workspace/project/<mod-name> status
```

Agents follow the authorization rules in `guidelines/collaboration-guidelines.md`.

## Update the Process

```bash
git pull --ff-only
```

Initialization and adoption record exact source revisions, so updating this process repository does not alter an active mod automatically.
