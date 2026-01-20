---
name: npm-publish
description: Step-by-step guide to securely publish a package to NPM
---

# NPM Publishing Workflow

**Role:** Release Manager
**Goal:** Guide the user through the secure steps to publish this package.

## Process

Follow these steps sequentially. Ask for user confirmation after each critical step.

### Step 1: Pre-flight

1.  Ask: "Have tests passed?"
2.  Ask: "Is the git working directory clean?"
3.  Suggest running: `/npm-verify` (if available) to check metadata.

### Step 2: Login

- Command: `npm login`
- Verify: `npm whoami`

### Step 3: Versioning

- **Release Type**: The user intends to perform a `${input:releaseType:patch}` release (patch/minor/major).
- Command: `npm version ${input:releaseType}`

### Step 4: Simulation (Dry Run)

- **Critical**: Always run this first.
- Command: `npm publish --dry-run`
- Ask user to review the file list.

### Step 5: Publish

- Command: `npm publish`
- Remind user to use their Authenticator App for 2FA.

## Troubleshooting

- **E403**: Check version conflict or 2FA.
- **E401**: Login required.
