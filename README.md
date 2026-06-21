# Minecraft Mod Agent Process

A reusable workspace for developing one Minecraft 1.12.2 mod at a time with AI agents through an approved, stage-based process.

The repository separates reusable instructions from ignored project documentation, temporary template files, and the independent final mod repository.

## Repository Structure

```text
minecraft-mod-agent-process/
├── AGENTS.md
├── guidelines/
├── references/
├── setup/
├── stages/
└── workspace/
    ├── documentation/
    ├── project/
    ├── project.properties
    └── template/
```

- `AGENTS.md` is the agent entry point.
- `guidelines/` contains shared rules, including the authoritative process definition.
- `stages/` contains stage-specific instructions.
- `setup/` contains configuration examples and the initialization procedure.
- `references/` contains curated technical links.
- `workspace/` contains ignored, project-specific runtime data.

See `guidelines/process-control.md` for the stage sequence, statuses, approval flow, and expected outputs.

## Prerequisites

Install Git, Java 25, and IntelliJ IDEA. Create an empty GitHub repository for the final mod without a README, license, `.gitignore`, or initial commit.

The exact platform, compatibility, tooling, distribution, and license defaults are defined in `guidelines/project-defaults.md` and `setup/template-defaults.properties`.

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

Set the empty final repository and its local directory name:

```properties
project_repository_url=https://github.com/mahghuuuls/example-mod.git
project_directory_name=example-mod
```

Shared template and identity defaults remain in `setup/template-defaults.properties`. Project-specific overrides belong in `workspace/project.properties`.

## Run the Process

1. Start the agent from the process repository root.
2. Tell it which stage to begin.
3. Review and explicitly approve each stage output.
4. During Initialization, allow it to prepare the independent final repository.
5. During Implementation, open and edit only the repository under `workspace/project/`.
6. During release preparation, review the handoff and publish to CurseForge manually.

Generated process artifacts are stored under `workspace/documentation/` and ignored by this repository. Preserve them separately when long-term history matters.

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

Initialization records the exact template revision used, so updating this process repository does not alter an already initialized mod automatically.
