<div align="center">

# Open Source Project Starter

My personal setup for Open Source projects on Github.

</div>

<br>

## Table of Contents

- **[GitHub](#github)**
- **[Renovate](#renovate-automated-dependency-management)**
- **[Synk](#synk-automated-vulnarability-analysis)**

<br>

## GitHub

### Labels

In GitHub, we can assign labels to both issues and pull requests in order to signify their priority, category, or just assign any other
useful information. This makes understanding and organizing issues much easier, especially for bigger projects. This repository comes
with a basic label preset, placed within the `github-labels.json` file.

![GitHub Labels Preview](/docs/gihub-labels-preview.png?raw=true)

**How to load labels into GitHub project:**

1. Install **[GitHub Label Template](https://github.com/xavierchow/github-label-template)** globally by running:
``` bash
npm install -g github-label-template
```

2. Using this tool requires a **GitHub access token**. To generate one, visit the GitHub
**[Personal Access Tokens](https://github.com/settings/tokens)** page, generate a new token (at least `repo -> public_repo` must be
enabled) with a meaningful title, hit *Generate Token*, and copy the result.

3. Now, clear all existing labels by running:
``` bash
ghlbl -o <GITHUB_USER_NAME> -r <GITHUB_REPO_NAME> -t <GITHUB_TOKEN> -d
```

4. Then, import the label template by running:
``` bash
ghlbl -o <GITHUB_USER_NAME> -r <GITHUB_REPO_NAME> -t <GITHUB_TOKEN> -i github-labels.json
```

> **Warning**:<br>
> This clears all existing labels, thus also unassigning labels from all issues and pull requests! For existing projects, it's better to
> just create / update / delete the labels manually.

<br><br><br>

## [Renovate](https://renovateapp.com/): Automated dependency management

Renovate constantly **tracks our project's npm dependencies, looking for newer versions being available**. Should Renovate find a newer
version for some dependency, it will automatically create a new branch, upgrade the dependency (while also updating the npm lock file) and
open up a Pull Request containing all the information necessary to make an informed decision.

### Setup

Renovate can be setup for selective repositories using the **[Renovate GitHub app](https://github.com/apps/renovate)**. Once activated, it
will create an initial Pull Request, introducing the `renovate.json` configuration file. My custom preset can be found under
`presets/renovate.json`.

> With my configuration, renovate PRs will get the `renovate` label my default. Also, it puts me in as a reviewer by default.

<br><br><br>

## [Synk](https://snyk.io/): Automated vulnarability analysis

Synk continuously **looks for security vulnerabilities in our project's NPM dependencies**. On the one hand, Snyk notifies us about new
vulnerabilities found within our project by sending out an email. On the other hand, Snyk automatically checks every Pull Requests for
dependency security vulnerabilities.

### Setup

To set Synk up, visit the **[Synk website](https://snyk.io/)**, connect your GitHub account, and enable Synk for one or more GitHub
repositories.

> Sync can be enabled as a requirement for Pull Request to pass. Moreover, Sync provides a GitHub badge which can be embedded into the
`README.md` file.
