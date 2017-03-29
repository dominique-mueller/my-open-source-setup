# Open Source Project Starter

Everything a developer needs to start an Open Source project on Github.

<br>

## GitHub: Labels

In GitHub, we can assign labels to both issues and pull requests in order to signify their priority, category, or assign them with any other
helpful information. This makes understanding and organizing open issues much easier, especially for bigger projects. This repository comes with a label preset, placed within the `github-labels.json` file. It includes labels for the type, the implementation
state, and the issues state / issue resolution.

> See a live example on the [labels page of this repository](https://github.com/dominique-mueller/open-source-project-starter/labels).

*TODO: Screenshot*

### How to use

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
