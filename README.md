<div align="center">

# Open Source Project Starter

Everything a developer needs to start an Open Source project on Github.

</div>

<br>

## Table of Contents

- **[GitHub](#github)**<br>Labels, Issue Template, ...
- **[Services](#services)**<br>Greenkeeper, Synk, ...

<br>

## GitHub

### Labels

In GitHub, we can assign labels to both issues and pull requests in order to signify their priority, category, or assign them with any other
helpful information. This makes understanding and organizing open issues much easier, especially for bigger projects. This repository comes with a label preset, placed within the `github-labels.json` file. It includes labels for the type, the implementation
state, and the issues state / issue resolution.

*TODO: Screenshot*

> See a live example on the **[labels page of this repository](https://github.com/dominique-mueller/open-source-project-starter/labels)**.

#### Upload labels into GitHub project

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

<br>

## Services

> Some tools below are able to open Pull Request; they will do so against your repository's default branch, which - by default - is the
*master branch*. Especially when using Git Flow, it often makes more sense to let Pull Request go against the *develop branch* instead.
Changing the project's default branch from the *master branch* to the *develop branch* is the solution here.

### Greenkeeper

**[Greenkeeper](https://greenkeeper.io/)** constantly **tracks our project's NPM dependencies for newer versions**. Should Greenkeeper find
a newer version for one or more dependencies defined within our `package.json` file, it automatically creates a new branch using those newer
dependencies. Then, Greenkeeper creates a Pull Request, containing all the information we need to make an informed decision about whether
there is some work for us to do or not (e.g. test results via CI process).

To set Greenkeeper up, visit the **[Greenkeeper GitHub Integration Page](https://github.com/integration/greenkeeper)**, and follow the setup
guide to enable it for one or more GitHub repositories.

### Synk

**[Synk](https://snyk.io/)** continuously **finds and fixes security vulnerabilities in our project's NPM dependencies**. On the one hand,
Snyk notifies us about new vulnerabilities for our project by email, and also by opening a Pull Request with the fix. On the other hand,
Snyk automatically checks every Pull Requests for dependency security vulnerabilities.

To set Synk up, visit the **[Synk website](https://snyk.io/)**, connect your GitHub account, and enable Synk for one or more GitHub
repositories.

> Sync can be enabled as a requirement for Pull Request to pass. Moreover, Sync provides a GitHub badge which can be embedded into the
`README.md` file.

### GitMagic

**[GitMagic](https://gitmagic.io/)** makes our repository great again - by **magically enforcing the GitHub contribution guidelines** we
defined for our project.

To set GitMagic up, visit the **[GitMagic Web App](https://app.gitmagic.io/)**, conncet your GitHub account, and enable GitMagic for one or more GitHub repository. Furthermore, a `contributing.js` file must exist in the repo - a full list of available rules is available
**[right here](https://gitmagic.io/rules/)**

> GitMagic can be enabled as a requirement for Pull Request to pass.
