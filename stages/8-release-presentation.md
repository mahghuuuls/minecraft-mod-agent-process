# Release Presentation

## Purpose

Prepare and approve the release's user-facing identity, documentation, visual assets, and distribution-platform presentation before technical packaging begins.

This stage describes only behavior that has been implemented and verified. It does not build or validate the release JAR.

## Main Question

> Does the proposed presentation accurately and clearly represent the mod and this release?

## Required Input

- `workspace/documentation/concept-and-scope.md`
- `workspace/documentation/requirements.md`
- `<artifact-root>/implementation-plan.md`
- Completed issues under `<artifact-root>/issues/`
- The completed project under `workspace/project/<project_directory_name>/`
- Implementation verification evidence
- Existing approved branding and release materials, when present

Implementation must be approved before this stage begins.

## Objectives

Establish:

- The proposed release identity and classification
- Accurate player-facing documentation
- An accurate changelog
- An approved decision to carry forward, revise, or create the mod icon
- Approved visual assets and screenshots when applicable
- Accurate project and file text for the approved distribution platforms
- User-facing compatibility, dependency, and limitation statements
- An approved presentation record for technical release validation

## In Scope

- Propose the release version and channel
- Create or update `README.md`
- Create or update `CHANGELOG.md`
- Decide whether existing branding remains appropriate
- Create or revise the mod icon when required
- Prepare approved screenshots or description images
- Prepare summary, description, categories, dependency information, and file changelog for each approved platform
- Confirm that every user-facing claim is supported by implementation evidence
- Produce `<artifact-root>/release-presentation.md`

## Out of Scope

Do not:

- Add or change mod behavior
- Perform unrelated refactoring
- Apply unapproved version or metadata changes
- Build the final release JAR
- Inspect or test the final release JAR
- Upload assets or files to a distribution platform
- Publish a release
- Claim compatibility that was not verified

An implementation defect returns to Implementation. An unresolved product claim returns to the stage that owns the underlying decision.

## Desired AI Behavior

Act as a release editor and visual-design coordinator.

- Use concise, player-facing language.
- Describe only implemented and verified behavior.
- Do not present deferred features as available.
- Keep names, version proposals, compatibility statements, and dependencies consistent.
- Ask one focused question at a time when release identity or artistic direction requires owner input.
- Treat existing approved branding as reusable; do not regenerate it automatically.
- Separate factual accuracy from artistic preference.
- Present documentation and visual assets for explicit approval.
- Never upload or publish.

## Documentation

The final project README should contain applicable sections such as:

1. Mod name and summary
2. Features
3. Requirements
4. Installation
5. Configuration
6. Usage
7. Compatibility
8. Known limitations
9. Credits
10. License
11. Issue reporting

The changelog should use relevant user-facing categories such as Added, Changed, Fixed, Performance, Compatibility, Removed, and Known Issues.

Exclude internal refactors and development history unless users need the information.

## Icon Decision

Record one decision:

- **Carry Forward:** Existing approved icon remains accurate, legible, original, and technically suitable.
- **Revise:** Existing visual identity remains valid but the asset needs a focused change.
- **Create:** No approved suitable icon exists.

When the decision is **Revise** or **Create**, follow:

```text
guidelines/mod-icon-creation.md
```

The AI must create the artwork workspace and explicitly ask the project owner to add reference images there or attach them in chat. Do not assume the owner has read repository documentation.

When the decision is **Carry Forward**, do not request references or generate alternatives.

## Visual Assets

Approved assets must:

- Represent the mod accurately
- Remain recognizable at their displayed sizes
- Use original or properly licensed material
- Avoid Minecraft, a distribution platform, another project, or another creator's branding as the primary artwork
- Meet current destination requirements
- Be approved by the project owner

Screenshots should show actual implemented behavior. Do not substitute generated imagery for evidence of gameplay or UI behavior.

## Distribution-Platform Presentation

Prepare, but do not publish:

- Project name
- Summary
- Description
- Categories
- Supported Minecraft, loader, runtime, and environment information
- Required and optional dependencies
- License, source, and issue links
- Project icon and approved images
- Proposed file display name and release channel
- File changelog
- Known limitations

Verify current distribution-platform presentation and asset requirements during this stage.

## Process

1. Confirm that Implementation is approved.
2. Review completed issues, verification evidence, and known limitations.
3. Propose the release identity and channel.
4. Update README and changelog drafts.
5. Decide whether branding is carried forward, revised, or created.
6. Run the icon guide only when revision or creation is approved.
7. Prepare screenshots and additional images when applicable.
8. Prepare project and file text for the approved distribution platforms.
9. Cross-check every claim against requirements and implementation evidence.
10. Produce the presentation record.
11. Present the complete documentation, assets, and listing material for approval.
12. Revise until explicitly approved.

## Output Artifacts

### Final Project Repository

Prepare applicable user-facing files and assets:

- `README.md`
- `CHANGELOG.md`
- Approved mod icon
- Approved screenshots or description images stored in the repository only when appropriate

### Presentation Record

Produce:

```text
<artifact-root>/release-presentation.md
```

It should contain:

1. Proposed release version and channel
2. README and changelog status
3. Branding decision
4. Approved icon and asset paths
5. Reference-source record when artwork was created or revised
6. Prepared distribution-platform presentation
7. User-facing compatibility and dependency claims
8. Known limitations
9. Owner approvals

## Completion Criteria

This stage is complete when:

- The release identity and channel are approved.
- README and changelog accurately describe the implemented mod.
- The branding decision is recorded.
- Required visual assets are approved and technically suitable.
- distribution-platform presentation material is complete.
- Every user-facing claim is supported by evidence.
- No unresolved presentation defect remains.
- `<artifact-root>/release-presentation.md` is generated and approved.

Completion authorizes Packaging and Release Validation. It does not authorize publication.
