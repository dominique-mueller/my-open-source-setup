<div align="center">

# Open Source Project Starter

My personal setup for Open Source projects on Github.

</div>

<br>

## Table of Contents

- **[GitHub Labels](#github-labels)**
- **[Renovate](#renovate-automated-dependency-management)**
- **[Synk](#synk-automated-vulnarability-analysis)**
- **[PullApprove](#pullapprove-granular-pull-request-reviews)**
- **[Codecov](#codecov-code-coverage-as-pull-request-comment)**

<br><br><br>

## GitHub Labels

In GitHub, we can assign labels to both issues and pull requests in order to signify their priority, category, or just assign any other
useful information. This makes understanding and organizing issues much easier, especially for bigger projects. This repository comes with a
basic label preset, placed within the `github-labels.json` file.

![GitHub Labels Preview](/docs/github-labels-preview.png?raw=true)

### Setup

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
ghlbl -o <GITHUB_USER_NAME> -r <GITHUB_REPO_NAME> -t <GITHUB_TOKEN> -i ./presets/github-labels.json
```

> **Warning**:<br>
> This clears all existing labels, thus also unassigning labels from all issues and pull requests! For existing projects, it's better to
> just create / update / delete the labels manually.

<br><br><br>

## [Renovate](https://renovateapp.com/): Automated dependency management

Renovate constantly **tracks our project's npm dependencies, looking for newer versions being available**. Should Renovate find a newer
version for some dependency, it will automatically create a new branch, upgrade the dependency (while also updating the npm lock file) and
open up a Pull Request containing all the information necessary to make an informed decision.

![Renovate Preview](/docs/renovate-preview.png?raw=true)

> I've also tested **[Greenkeeper](https://greenkeeper.io/)**, but I found Renovate to be more reliable. Also, Renovate is able to correctly
> increment version numbers, meaning it keeps the `x.x.x` syntax. Also, it works with npm lock files by default.

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

> Sync can be enabled as a requirement for Pull Requests to pass. Moreover, Sync provides a GitHub badge which can be embedded into the
`README.md` file.

<br><br><br>

## [PullApprove](https://about.pullapprove.com/): Granular Pull Request reviews

Using PullApprove allows us to **define Pull Request conditions and reviewers in a more granular way**. This includes the ability to setup
reviewer groups, or declare custom conditions for pending and rejection states.

> If one just wants to handle Work in Progress Pull Requests, the **[WIP GitHub App](https://github.com/apps/wip)** is a well working
> alternative.

### Setup

To setup PullApprove, visit the **[PullApprove website](https://pullapprove.com/)**, connect your GitHub account, and enable PullApprove
for your GitHub repositories. Once done, you can customize PullApprove by adding a `.pullapprove.yml` file to your repository. My custom
preset can be found under `presets/.pullapprove.yml`.

> PullApprove can be enabled a sa requirement for Pull Requests to pass.

<br><br><br>

## [Codecov](https://codecov.io/): Code Coverage as Pull Request comment

Codecov **writes comments into Pull Requests, presenting the current code coverage and its change regarding the default branch**. This
enables reviewers to see the coverage quickly, without having to dive into the build logs. My custom preset can be found under
`presets/codecov.yml`.

> I've also tested **[Coveralls](https://coveralls.io/)**, but for me personally it wasn't very stable.

### Setup

1. Add the `codecov` package to your project's `package.json` file

2. Add a code coverage upload script to your `package.json` file, for example:
``` json
{
  "test:coverage": "codecov -f coverage/coverage-final.json"
}
```

3. *Optional:* Add the `coedecov.yml` file to your project

4. Add the script to your CI; in Travis CI, I usually put it in the test stage into the `after_success` block:

``` yml
jobs:
  include:
    - stage: test
      after_success:
        - npm run test:coverage
```

<br><br><br>

## Creator

**Dominique Müller**

- E-Mail: **[dominique.m.mueller@gmail.com](mailto:dominique.m.mueller@gmail.com)**
- Website: **[www.devdom.io](https://www.devdom.io/)**
- Twitter: **[@itsdevdom](https://twitter.com/itsdevdom)**
