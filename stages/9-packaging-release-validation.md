# Packaging and Release Validation

## Purpose

Apply the approved release presentation, build and validate the exact distributable artifact, and prepare the handoff for manual publication to the approved distribution platforms.

## Main Question

> Is the exact release artifact technically ready for the project owner to publish?

## Required Input

- `workspace/documentation/requirements.md`
- `workspace/documentation/architecture.md`
- `<artifact-root>/release-presentation.md`
- Completed issues and verification evidence under `<artifact-root>/issues/`
- The completed project under `workspace/project/<project_directory_name>/`

Release Presentation must be approved before this stage begins.

## Objectives

Establish:

- Consistent release version and metadata
- A reproducible successful release build
- The exact normal distributable JAR
- Verified JAR contents
- Clean client and dedicated-server results where applicable
- Verified compatibility and dependency claims
- Artifact identity and checksum
- A complete handoff for manual publication

## In Scope

- Apply the approved release version
- Update and validate mod and build metadata
- Confirm required and optional dependency declarations
- Build the normal release JAR
- Inspect the exact JAR
- Test the exact JAR in clean environments
- Perform release smoke tests
- Reconcile technical results with the approved presentation
- Produce the checksum and handoff record

## Out of Scope

Do not:

- Add features
- Perform unrelated refactoring
- Redesign branding or rewrite release messaging without returning to Release Presentation
- Claim unverified compatibility
- Upload a file or asset
- Create or edit a live distribution-platform project
- Publish a release
- Commit, tag, or push unless separately authorized
- Begin post-release maintenance

A release-blocking implementation defect returns to Implementation. An inaccurate presentation claim returns to Release Presentation.

## Desired AI Behavior

Act as a release-validation coordinator.

- Start from the approved implementation and presentation.
- Apply only metadata and packaging changes required for the approved release.
- Identify missing information instead of inventing it.
- Keep metadata consistent across configuration, resources, documentation, JAR name, and handoff material.
- Inspect the exact artifact intended for handoff.
- Test that exact artifact rather than a development build.
- Report failed checks honestly.
- Repeat affected checks after every relevant change.
- Never upload or publish.

## Metadata Validation

Confirm consistency across:

- Mod name and ID
- Version
- Minecraft version
- Loader and runtime
- Java runtime compatibility
- Description, authors, credits, and license
- Logo reference
- Required and optional dependencies
- Accepted dependency versions
- JAR filename
- Approved distribution-platform presentation

Do not expand compatibility claims beyond approved evidence.

## Release Build

Use the configured template's build mechanism.

The release build must:

- Start from the approved implementation state
- Complete without errors
- Produce the expected normal distributable JAR
- Exclude development-only files and dependencies
- Include required resources and metadata
- Use the approved version and filename
- Be reproducible through the documented project build process

Record the command, environment, source revision, and result.

## Artifact Inspection

Inspect the final JAR for:

- Correct metadata and version
- Required classes and resources
- Approved mod icon
- Access transformers or Mixin resources when required
- Configuration defaults
- Accidental development files
- Local paths
- Secrets or credentials
- Unexpected bundled dependencies
- Duplicate or obsolete resources

The inspected artifact must be the same file handed to the project owner.

## Clean-Instance Validation

Install the final JAR into a clean instance containing only required dependencies.

Verify as applicable:

- Minecraft starts successfully.
- The mod is discovered and loaded.
- Logs contain no unexpected errors.
- Essential features are available.
- Configuration files are created correctly.
- A world can be created or loaded.
- Relevant state survives restart.
- Dedicated-server behavior works.
- A client can connect.
- Optional dependencies are handled correctly.
- Missing required dependencies produce clear failure information.

This validation supplements rather than replaces Implementation evidence.

## Defect Routing

- **Implementation defect:** stop and return to Implementation.
- **Presentation defect:** stop and return to Release Presentation.
- **Packaging-only defect:** correct it within this stage and repeat affected checks.
- **Earlier approved decision invalidated:** follow the backward-transition rules in `guidelines/process-control.md`.

Any source-code change requires relevant implementation verification and review again.

## Process

1. Confirm Release Presentation approval.
2. Review unresolved defects and known limitations.
3. Apply the approved version and metadata.
4. Build the exact release JAR.
5. Inspect its contents.
6. Perform clean-instance and relevant server validation.
7. Route discovered defects to the owning stage.
8. Rebuild and repeat affected checks after corrections.
9. Reconcile final evidence with the approved presentation.
10. Calculate the artifact checksum.
11. Produce the release handoff record.
12. Present the complete artifact and evidence for approval.

## Output Artifacts

Prepare:

- The exact distributable JAR
- Final applied metadata
- `<artifact-root>/release-handoff.md`

The handoff record should contain:

1. Mod and version
2. Source revision
3. Artifact filename and path
4. Artifact checksum
5. Build command, environment, and result
6. Artifact inspection
7. Clean-client validation
8. Dedicated-server validation when applicable
9. Dependencies and compatibility claims
10. Approved presentation record
11. Known limitations
12. Manual publication checklist

Do not record a publication result because publication occurs after this stage.

## Manual Publication Boundary

The project owner is responsible for signing into each approved distribution platform, creating or editing live projects, uploading artifacts and assets, selecting live relationships, publishing files, and verifying published pages.

The agent may prepare text or troubleshoot when explicitly requested but must not perform those actions.

## Completion Criteria

This stage is complete when:

- Version and metadata are consistent.
- The release build succeeds.
- The exact distributable JAR is inspected.
- Clean-instance validation passes.
- Dedicated-server validation passes when applicable.
- No known release-blocking defect remains.
- Approved presentation claims match the artifact.
- The artifact checksum and handoff are recorded.
- The project owner explicitly approves the handoff for manual publication.
- Nothing was uploaded or published by the agent.
- `<artifact-root>/release-handoff.md` is generated and approved.

Completion ends agent-managed release work. Manual publication remains the project owner's responsibility.
