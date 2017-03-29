# Open Source Project Starter

Everything a developer needs to start an Open Source project on Github.

<br>

## GitHub

### Labels

In GitHub, we can assign labels to both issues and pull requests in order to signify their priority, category, or assign them with any other
helpful information. This makes understanding and organizing open issues much easier, especially for bigger projects.

#### Information

This repository comes with a label preset, placed within the `github-labels.json` file. It includes labels for the type, the implementation
state, and the issues state / issue resolution.

> See a live example on the [labels page of this repository](https://github.com/dominique-mueller/open-source-project-starter/labels).

*TODO: Screenshot*

#### How to use

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

### Greenkeeper

**[Greenkeeper](https://greenkeeper.io/)** constantly tracks our project's NPM dependencies for newer versions. Should Greenkeeper find a
newer version for one or more dependencies defined within our `package.json` file, it automatically creates a new branch using those newer
dependencies. Then, Greenkeeper creates a Pull Request, containing all the information we need to make an informed decision about whether
there is some work for us to do or not (e.g. test results via CI process).

#### How to use

1. Visit the **[Greenkeeper GitHub Integration Page](https://github.com/integration/greenkeeper)**, and follow the setup guide to enable it
for one or more GitHub repositories.

2. Greenkeeper will make Pull Requests against your repository's default branch, which - by default - is the *master branch*. Especially
when using Git Flow, it often makes more sense to let Pull Request go against the *develop branch* instead. Changing the project's default
branch from the *master branch* to the *develop branch* is recommended here.
