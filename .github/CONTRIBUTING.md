# Contributing

When contributing to this repository, please first discuss the change you wish to make via issue,
email, or any other method with the owners of this repository before making a change.

## Pull Request Process

1.  Add [sementics prefix](#semantic-pull-requests) to your PR.
2.  Ensure any install or build dependencies are removed or ignored before the end of the layer when doing a build.
3.  Update the README.md with details of changes to the module, take into account that the following sections are generated automatically: Requirements, Providers, Inputs, Outputs.
4.  Once all CI test have been passed, your contribution will be merged via [Squash and Merge](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-request-merges#squash-and-merge-your-pull-request-commits)!. Merged PRs will be included in the next release.

## Semantic Pull Requests

To generate changelog in releases, pull requests must have sementic name prefix and must follow conventional specs below:

- `feat:` for new features
- `fix:` for bug fixes
- `improvement:` for enhancements
- `docs:` for documentation and examples
- `refactor:` for code refactoring
- `chore:` for chores stuff, e.g: this can be used for `chore: update changelog`.

A [Probot app](https://github.com/zeke/semantic-pull-requests) checks PR name prefix to ensure your pull requests are semantic before you merge them.  
The file configuration in under `.github/semantic.yml`

## Changelog

The changelog is kept on Github Release notes of each version and is automatically generated with [Draft Release](#draft-release-generation).

## Pull Requests auto labeling

The repository has a Github Action workflow `ci-prlabeler` that automatically label your pull requests based on the [semantic name prefix](#semantic-pull-requests) they have.  
You can see the labels and semantic name prefix relationship in the config file: `.github/pr-prefix-labeler.yml`.

## Draft Release generation

The repository has a Github Action workflow `ci-release` that generates and updates the [Release Drafts](https://github.com/release-drafter/release-drafter) with your next release notes as pull requests are merged into master. The PR are categorized based on the labels they have, you can see the labels and category relationship in the config file: `.github/release-drafter.yml`.  
For example, the labels 'feature', 'improvement' and 'refactor' are categorized as a Feature in the Release Draft notes.

## Full workflow

1.  Create a pull request with [sementic name prefix](#semantic-pull-requests).
2.  The [Probot app](https://github.com/zeke/semantic-pull-requests) checks sementic name prefix.
3.  Depending on sementic name prefix, [ci-prlabel](#pull-requests-auto-labeling) labels the PR automatically.
4.  Depending PR labels, [ci-release](#draft-release-generation) create or update the Release Draft.
