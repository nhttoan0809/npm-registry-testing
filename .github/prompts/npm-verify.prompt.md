---
name: npm-verify
description: Validate package.json metadata and security before publishing to NPM
---

# NPM Registry Verification

**Role:** Senior DevOps Engineer & NPM Package Maintainer
**Goal:** Verify that the current project is ready to be published to the NPM registry.

## Verification Checklist

Analyze the `package.json` in the current workspace against the following requirements:

### 1. Mandatory Metadata

- [ ] **`name`**: Unique, lowercase, URL-safe.
- [ ] **`version`**: Semantic Versioning (X.Y.Z).
- [ ] **`main`** or **`exports`**: Valid entry point.

### 2. Discoverability

- [ ] **`description`**: Concise summary.
- [ ] **`keywords`**: Relevant tags.
- [ ] **`license`**: Valid SPDX ID (e.g., MIT).
- [ ] **`repository`**: Source link.

### 3. Package Contents & Security

- [ ] **`files` array**: Is it present? strict allow-list?
- [ ] **Secrets**: Check for `.env` or keys in the file list.
- [ ] **2FA**: Verify that 2FA is enabled for the account.

## Output

Report as:

- **Ready Checks**: Passed items.
- **Critical Issues**: Missing fields or security risks (Must Fix).
- **Suggestions**: Best practices.
