# Owner information

![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/cylc/language-cylc?logo=github)
![APM version](https://img.shields.io/apm/v/language-cylc?logo=atom)

## Deploying

Publishing updates to the Atom package registry is done automatically by GitHub Actions when a release is published. The suggested process is:
1. Merge the pull request(s) with changes
1. Bump the `package.json` version, update the changelog and create a PR (1 reviewer is fine)
1. Publish a release on GitHub with a tag matching the version number

If the Deploy workflow fails because you forgot to bump the `package.json` version, the tag associated with the release will be automatically deleted and the release will become a draft. Simply bump the `package.json` version as appropriate and re-publish the release to trigger the workflow again.


### Information on publishing Atom packages

Publishing is done by `apm`. See https://flight-manual.atom.io/behind-atom/sections/maintaining-your-packages/. The Atom token of a member of the Cylc organization (gotten from signing in at [atom.io](https://atom.io)) needs to be [stored as a repository secret](https://help.github.com/en/actions/configuring-and-managing-workflows/creating-and-storing-encrypted-secrets). The token of any member of the organization (with push access) will do.

The Deploy workflow also replaces the symlink `grammars/cylc.json` with a hard copy of `cylc-textmate-grammar/cylc.tmLanguage.json` in a tag that dangles off master, because `apm` doesn't pull submodules - see [#3](https://github.com/cylc/language-cylc/pull/3).
