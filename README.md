<div align="center">

# Open Source Project Starter

My personal setup for Open Source projects on Github.

</div>

<br>

## Table of Contents

- **[GitHub Labels](#github-labels)**<br>Setup all GitHub labels automatically
- **[Codecov](#codecov-code-coverage-as-pull-request-comment)**<br>Code Coverage service integration (CI)

<br><br><br>

## GitHub Labels

In GitHub, we can assign labels to both issues and pull requests in order to signify their priority, category, or just assign any other
useful information. This makes understanding and organizing issues much easier, especially for bigger projects. This repository comes with a
basic label preset, placed within the `github-labels.json` file.

![GitHub Labels Preview](/docs/github-labels-preview.png?raw=true)

### Setup

The following describes how to quickly setup my personal list of labels.

> **WARNING**:<br>This process clears all existing labels, thus also unassigning labels from all issues and pull requests! For existing
> projects, it's better to just create / update / delete the labels manually.

1. Install **[GitHub Label Template](https://github.com/xavierchow/github-label-template)** globally by running:

```bash
npm install -g github-label-template
```

2. Using this tool requires a **GitHub access token**. To generate one, visit the GitHub
   **[Personal Access Tokens](https://github.com/settings/tokens)** page, generate a new token (at least `repo -> public_repo` must be
   enabled) with a meaningful title, hit _Generate Token_, and copy the result.

3. Now, clear all existing labels by running:

```bash
ghlbl -o <GITHUB_USER_NAME> -r <GITHUB_REPO_NAME> -t <GITHUB_TOKEN> -d
```

4. Then, import the label template by running:

```bash
ghlbl -o <GITHUB_USER_NAME> -r <GITHUB_REPO_NAME> -t <GITHUB_TOKEN> -i ./presets/github-labels.json
```

<br><br><br>

## [Codecov](https://codecov.io/): Code Coverage as Pull Request comment

Codecov **writes comments into Pull Requests, presenting the current code coverage and its change regarding the default branch**. This
enables reviewers to see the coverage quickly, without having to dive into the build logs. My custom preset can be found under
`presets/codecov.yml`.

![Codecov Preview](/docs/codecov-preview.png?raw=true)

> I've also tested **[Coveralls](https://coveralls.io/)**, but for me personally it wasn't very stable.

### Setup

1. Add the `codecov` package to your project's `package.json` file

2. Add a code coverage upload script to your `package.json` file, for example:

```json
{
  "test:coverage": "codecov -f coverage/coverage-final.json"
}
```

3. _Optional:_ Add the `coedecov.yml` file to your project

4. Add the script to your CI; in Travis CI, I usually put it in the test stage into the `after_success` block:

```yml
jobs:
  include:
    - stage: test
      after_success:
        - npm run test:coverage
```
