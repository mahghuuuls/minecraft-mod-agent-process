# Packaging and Release Preparation

## Purpose

Prepare the completed mod for manual publication by finalizing user-facing documentation, branding, metadata, and the exact distributable artifact.

The agent prepares and validates the release package. The project owner performs every upload and publication action.

## Main Question

> Is the completed mod ready for the project owner to publish on CurseForge?

## Required Input

- `workspace/documentation/requirements.md`
- `<artifact-root>/implementation-plan.md`
- Completed issues under `<artifact-root>/issues/`
- The completed project under `workspace/project/<project_directory_name>/`
- Implementation verification evidence

## Objectives

Establish:

- The intended release version
- Accurate user-facing documentation
- An accurate changelog
- Approved mod branding and icon
- Correct mod and dependency metadata
- A reproducible release build
- A validated distributable JAR
- Prepared CurseForge listing content
- A complete handoff package for manual publication

## In Scope

- Select and apply the approved release version
- Create or update `README.md`
- Create or update `CHANGELOG.md`
- Create or finalize the mod icon and approved listing assets
- Update mod metadata
- Confirm required and optional dependency declarations
- Confirm Minecraft, Forge, Cleanroom, and Java compatibility claims
- Build the release JAR
- Inspect the exact release JAR
- Test the exact release JAR in a clean instance
- Perform release smoke tests
- Prepare CurseForge project text, file description, and release notes
- Prepare required and optional dependency information
- Record the release-preparation evidence
- Present the complete handoff package to the project owner

## Out of Scope

Do not:

- Add new features
- Perform unrelated refactoring
- Redesign the architecture
- Change approved behavior
- Claim unverified compatibility
- Upload a file to CurseForge
- Create or edit the live CurseForge project
- Publish a release
- Publish to another platform
- Commit, tag, or push unless separately authorized
- Begin post-release maintenance

When a release-blocking implementation defect is discovered, stop release preparation and return it to Implementation.

## Desired AI Behavior

Act as a release-preparation coordinator.

- Describe only behavior that was actually implemented and verified.
- Do not present deferred or incomplete features as available.
- Review implementation evidence before preparing release material.
- Identify missing release information instead of inventing it.
- Ask one focused question at a time when naming, versioning, branding, or release classification requires project-owner input.
- Keep README content useful to players and modpack authors.
- Write changelog entries for users rather than as an internal engineering history.
- Keep metadata consistent across configuration, mod files, documentation, JAR name, and prepared CurseForge content.
- Confirm dependency declarations and version ranges.
- Inspect the artifact for development files, secrets, local paths, unintended bundled dependencies, and missing resources.
- Test the exact JAR intended for handoff.
- Report failed checks honestly.
- Never upload or publish.

## README Content

The final project README should contain relevant sections such as:

1. **Mod Name and Summary**
2. **Features**
3. **Requirements**
4. **Installation**
5. **Configuration**
6. **Usage**
7. **Compatibility**
8. **Known Limitations**
9. **Credits**
10. **License**
11. **Issue Reporting**

Omit sections that do not apply. Do not describe the earlier development process or internal architecture unless it is relevant to users.

## Changelog Content

Create or update `CHANGELOG.md` for the prepared version.

Use relevant user-facing categories:

- Added
- Changed
- Fixed
- Performance
- Compatibility
- Removed
- Known Issues

Exclude internal refactors, documentation-only edits, and fixes to behavior that was never publicly released unless users need to know about them.

## Branding and Assets

Prepare:

- The in-game mod icon
- The CurseForge project icon
- Any approved screenshots or description images

Assets must:

- Represent the mod accurately
- Meet the current destination requirements
- Remain readable at their displayed size
- Avoid unlicensed material
- Be approved by the project owner
- Be stored in the correct repository location when required by mod metadata

Verify current CurseForge asset requirements during this stage.

## Metadata Validation

Confirm consistency across:

- Mod name
- Mod ID
- Version
- Minecraft version
- Supported loader and runtime
- Java runtime compatibility
- Description
- Authors and credits
- License
- Logo reference
- Required dependencies
- Optional dependencies
- Accepted dependency versions
- JAR filename
- Prepared CurseForge information

Do not claim compatibility that was not established during Implementation.

## Release Build

Use the configured template's build mechanism.

The release build must:

- Start from the approved implementation state
- Complete without errors
- Produce the expected normal distributable JAR
- Exclude development-only files and dependencies
- Include required resources and metadata
- Use the approved version and filename
- Remain reproducible through the documented project build process

Record the exact command, environment, and result.

## Artifact Inspection

Inspect the final JAR for:

- Correct metadata and version
- Required classes and resources
- Mod icon
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

Verify:

- Minecraft starts successfully.
- The mod is discovered and loaded.
- No unexpected errors appear in logs.
- Essential features are available.
- Configuration files are created correctly.
- A world can be created or loaded.
- Relevant state survives restart.
- Dedicated-server behavior works when applicable.
- A client can connect when applicable.
- Missing optional dependencies are handled correctly.
- Missing required dependencies produce clear failure information.

This is release validation, not a replacement for Implementation verification.

## CurseForge Handoff

Prepare, but do not publish:

- Project name
- Summary
- Description
- Categories
- Supported Minecraft version
- Supported loader and runtime information
- Required and optional dependencies
- Project icon and images
- License information
- Source and issue links when applicable
- File display name
- Release version and channel
- File changelog
- Supported environment information
- Known limitations
- Exact JAR path and checksum

The project owner uses this material to publish manually.

## Process

1. Confirm that all earlier stages are approved.
2. Review unresolved defects and known limitations.
3. Select and approve the intended release version.
4. Create or update README and changelog.
5. Create or approve branding assets.
6. Update and validate metadata.
7. Build the exact release JAR.
8. Inspect the JAR contents.
9. Perform clean-instance and relevant server validation.
10. Return implementation defects to Implementation.
11. Rebuild and repeat affected checks after any code change.
12. Prepare CurseForge listing and file information.
13. Generate the release-preparation artifact.
14. Present the complete package for review.
15. Revise it until explicitly approved for manual publication.

## Output Artifacts

### Final Project Repository

Prepare:

- `README.md`
- `CHANGELOG.md`
- Mod icon and approved assets
- Updated mod and build metadata
- Final distributable JAR

### Release Preparation Record

Produce:

```text
<artifact-root>/release-preparation.md
```

It should contain:

1. **Mod and Version**
2. **Source Revision**
3. **Artifact Filename and Path**
4. **Artifact Checksum**
5. **Build Command and Result**
6. **Artifact Inspection**
7. **Clean-Instance Validation**
8. **Dedicated-Server Validation**
9. **Dependencies**
10. **Compatibility Claims**
11. **Known Limitations**
12. **Approved Documentation and Assets**
13. **Prepared CurseForge Listing**
14. **Manual Publication Checklist**

Do not record a publication result because publication occurs outside this agent stage.

## Manual Publication Boundary

The stage ends with an approved handoff package.

The project owner is responsible for:

- Signing into CurseForge
- Creating or editing the live project
- Uploading the JAR
- Selecting the live dependency relationships
- Publishing the file
- Verifying the published page

The agent may assist with text or troubleshooting when explicitly requested, but must not perform these actions.

## Completion Criteria

This stage is complete when:

- The intended release version is approved and consistent.
- README accurately describes the prepared mod.
- Changelog accurately describes the prepared release.
- Branding and assets are approved.
- Mod and dependency metadata are correct.
- The release build succeeds.
- The exact distributable JAR is inspected.
- Clean-instance validation passes.
- Dedicated-server validation passes when applicable.
- No known release-blocking defect remains.
- Known limitations are documented.
- CurseForge listing material is complete.
- The handoff artifact and checksum are recorded.
- The project owner explicitly approves the package for manual publication.
- Nothing was uploaded or published by the agent.
- `<artifact-root>/release-preparation.md` has been generated and approved.

Completion ends the agent-managed development process. Manual CurseForge publication remains the project owner's responsibility.
