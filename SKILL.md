---
name: rails-upgrade
description: Analyze Rails application upgrade path. Checks current version, finds latest release, fetches upgrade notes and diffs, then summarizes upgrade complexity.
---

# Rails Upgrade Analyzer

Analyze the current Rails application and provide a comprehensive upgrade assessment.

## Step 1: Verify Rails Application

Check that we're in a Rails application by looking for these files:
- `Gemfile` (must exist and contain 'rails')
- `config/application.rb` (Rails application config)
- `config/environment.rb` (Rails environment)

If any of these are missing or don't indicate a Rails app, stop and inform the user this doesn't appear to be a Rails application.

## Step 2: Get Current Rails Version

Extract the current Rails version from:
1. First, check `Gemfile.lock` for the exact installed version (look for `rails (x.y.z)`)
2. If not found, check `Gemfile` for the version constraint

Report the exact current version (e.g., `7.1.3`).

## Step 3: Find Latest Rails Version

Use the GitHub CLI to fetch the latest Rails release:

```bash
gh api repos/rails/rails/releases/latest --jq '.tag_name'
```

This returns the latest stable version tag (e.g., `v8.0.1`). Strip the 'v' prefix for comparison.

Also check recent tags to understand the release landscape:

```bash
gh api repos/rails/rails/tags --jq '.[0:10] | .[].name'
```

## Step 4: Determine Upgrade Type

Compare current and latest versions to classify the upgrade:

- **Patch upgrade**: Same major.minor, different patch (e.g., 7.1.3 → 7.1.5)
- **Minor upgrade**: Same major, different minor (e.g., 7.1.3 → 7.2.0)
- **Major upgrade**: Different major version (e.g., 7.1.3 → 8.0.0)

## Step 5: Fetch Upgrade Guide

Use WebFetch to get the official Rails upgrade guide:

URL: `https://guides.rubyonrails.org/upgrading_ruby_on_rails.html`

Look for sections relevant to the version jump. The guide is organized by target version with sections like:
- "Upgrading from Rails X.Y to Rails X.Z"
- Breaking changes
- Deprecation warnings
- Configuration changes
- Required migrations

Extract and summarize the relevant sections for the user's specific upgrade path.

## Step 6: Fetch Rails Diff

Use WebFetch to get the diff between versions from railsdiff.org:

URL: `https://railsdiff.org/{current_version}/{target_version}`

For example: `https://railsdiff.org/7.1.3/8.0.0`

This shows:
- Changes to default configuration files
- New files that need to be added
- Modified initializers
- Updated dependencies
- Changes to bin/ scripts

Summarize the key file changes.

## Step 7: Generate Upgrade Summary

Provide a comprehensive summary including:

### Version Information
- Current version: X.Y.Z
- Latest version: A.B.C
- Upgrade type: [Patch/Minor/Major]

### Upgrade Complexity Assessment

Rate the upgrade as **Small**, **Medium**, or **Large** based on:

| Factor | Small | Medium | Large |
|--------|-------|--------|-------|
| Version jump | Patch only | Minor version | Major version |
| Breaking changes | None | Few, well-documented | Many, significant |
| Config changes | Minimal | Moderate | Extensive |
| Deprecations | None active | Some to address | Many requiring refactoring |
| Dependencies | Compatible | Some updates needed | Major dependency updates |

### Key Changes to Address

List the most important changes the user needs to handle:
1. Configuration file updates
2. Deprecated methods/features to update
3. New required dependencies
4. Database migrations needed
5. Breaking API changes

### Recommended Upgrade Steps

1. Update test suite and ensure passing
2. Review deprecation warnings in current version
3. Update Gemfile with new Rails version
4. Run `bundle update rails`
5. Run `rails app:update` (interactive config updater)
6. Address breaking changes
7. Run test suite
8. Review and update deprecated code

### Resources

- Rails Upgrade Guide: https://guides.rubyonrails.org/upgrading_ruby_on_rails.html
- Rails Diff: https://railsdiff.org/{current}/{target}
- Release Notes: https://github.com/rails/rails/releases/tag/v{target}

## Error Handling

- If `gh` CLI is not authenticated, instruct the user to run `gh auth login`
- If railsdiff.org doesn't have the exact versions, try with major.minor.0 versions
- If the app is already on the latest version, congratulate the user and note any upcoming releases
