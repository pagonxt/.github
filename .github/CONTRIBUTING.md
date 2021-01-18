# Contributing

When contributing to this repository, please first discuss the change you wish to make via issue,
email, or any other method with the owners of this repository before making a change.

## Semantic Branch

- `feature-` for new features
- `fix-` for bug fixes
- `improvement-` for enhancements
- `docs-` for documentation and examples
- `refactor-` for code refactoring
- `chore-` for chores stuff

## Semantic Pull Requests

To generate changelog in releases, pull requests must have sementic name prefix and must follow conventional specs below:

- `feat:` for new features
- `fix:` for bug fixes
- `improvement:` for enhancements
- `docs:` for documentation and examples
- `refactor:` for code refactoring
- `chore:` for chores stuff, e.g: this can be used for `chore: update changelog`.

## Pull Request Process

1.  Add [sementics prefix](#semantic-pull-requests) to your PR.
2.  Ensure any install or build dependencies are removed or ignored before the end of the layer when doing a build.
3.  Update the `README.md` with details of changes to the module, take into account that the following sections are generated automatically: Requirements, Providers, Inputs, Outputs.
4.  Once all CI test have been passed, your contribution will be merged via [Squash and Merge](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-request-merges#squash-and-merge-your-pull-request-commits)!. Merged PRs will be included in the next release.

## Pull Requests Auto Labeling

The repository has a Github Action workflow `ci-prlabeler.yml` that automatically label your pull requests based on the [semantic branch name prefix](#semantic-branch) they have.  
You can see the labels and semantic name prefix relationship in the config file (of templates repositories): `.github/pr-labeler.yml`.

## Draft Release Generation

The repository has a Github Action workflow `ci-release.yml` that generates and updates the [Release Drafts](https://github.com/release-drafter/release-drafter) with your next release notes as pull requests are merged into master. The PR are categorized based on the labels they have, you can see the labels and category relationship in the config file : `.github/release-drafter.yml`.  
For example, the labels 'feature', 'improvement' and 'refactor' are categorized as a Feature in the Release Draft notes.

## Changelog

The changelog is kept on Github Release notes of each version and is automatically generated with [Draft Release](#draft-release-generation).

## Semantic Relesae Version

TO DO

## Full Workflow

1.  Create a branch with [sementic name prefix](#semantic-branch).
2.  Create a pull request with [sementic name prefix](#semantic-pull-requests).
3.  Depending on sementic branch name prefix, [ci-prlabel](#pull-requests-auto-labeling) labels the PR automatically.
4.  Depending PR labels, [ci-release](#draft-release-generation) create or update the Release Draft.
