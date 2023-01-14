# Testing Node Upgrade
Bumped the Node version to 18. Consider this beta. You can for it and switch it back to 12 by editing action.yml line 31.


# GitHub Automatic Release Action

This action simplifies the GitHub release process for community projects by automatically uploading assets, generating changelogs, handling pre-releases, and more. It is a fork of [marvinpinto/actions](https://github.com/marvinpinto/actions).

The original action has build steps that make it difficult to audit the code for stability and security vulnerabilities. This repository therefore, maintains a clone of the original action kept here on the `master` branch, and builds that source code in to the `stable` branch through a manually triggered GitHub action, allowing stable and secure use of the action across projects.

To update the action, rebase the `master` branch from `marvinpinto/actions`, and then run the GitHub action kept on the `stable` branch.

## Example usage:

```
name: "pre-release"

on:
  push:
    branches:
      - "master"

jobs:
  pre-release:
    name: "Release"
    runs-on: "ubuntu-latest"

      - name: Create production changeLog and release
        uses: SpuzzSomchai/automatic-release-action@stable
        with:
          repo_token: "${{ secrets.GITHUB_TOKEN }}"
          prerelease: false
          files: |
            artifacts/*
```

For more detailed instructions on how to use the features of this action, see the original [README on the `master` branch](https://github.com/balena-io-experimental/automatic-release-action/blob/master/packages/automatic-releases/README.md).
