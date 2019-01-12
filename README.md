<h1 align="center"> Pull </h1> <br/>
<p align="center">
 <a href="https://github.com/apps/pull">
   <img width="200" height="200" alt="Pull App" src="https://prod.download/pull-svg" />
 </a>
</p>
<p align="center">
  Keep your forks up-to-date.
</p>
<p align="center">
 <a href="https://github.com/apps/pull">
   <img alt="Installations" src="https://pull.now.sh/badge/installed" />
 </a>
 <a href="https://github.com/apps/pull">
   <img alt="Managing" src="https://pull.now.sh/badge/managing" />
 </a>
 <a href="https://github.com/issues?q=author%3Aapp%2Fpull">
   <img alt="Triggered #" src="https://pull.now.sh/badge/triggered" />
 </a>
</p>

<h2>Table of contents</h2>
<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Introduction](#introduction)
- [Features](#features)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Basic setup](#basic-setup)
  - [Advanced setup (with config)](#advanced-setup-with-config)
    - [Most common](#most-common)
    - [Advanced usage](#advanced-usage)
- [For Repository Owners](#for-repository-owners)
- [Author](#author)
- [License](#license)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


## Introduction

[![TravisCI](https://travis-ci.com/wei/pull.svg?branch=master)](https://travis-ci.com/wei/pull)
[![Codecov](https://codecov.io/gh/wei/pull/branch/master/graph/badge.svg)](https://codecov.io/gh/wei/pull)
[![Depfu](https://badges.depfu.com/badges/4a6fdae34a957e6c1ac11a83f6491162/overview.svg)](https://depfu.com/github/wei/pull)
[![Probot](https://pull.now.sh/badge/built_with)](https://probot.github.io/)
[![JavaScript Style Guide](https://pull.now.sh/badge/code_style)](https://standardjs.com)
[![jest](https://facebook.github.io/jest/img/jest-badge.svg)](https://github.com/facebook/jest)
[![MIT License](https://pull.now.sh/badge/license)](https://wei.mit-license.org)

> 🤖 a GitHub App built with [probot](https://github.com/probot/probot) that keeps your repository up-to-date with upstream changes via automated pull requests.

Incorporate new changes as they happen, not in 6 months. 

Trusted by [![Repository Count](https://pull.now.sh/badge/installed?plain)](https://probot.github.io/apps/pull/) repositories, triggered [![Triggered #](https://pull.now.sh/badge/triggered?plain)](https://github.com/issues?q=author%3Aapp%2Fpull) times.

## Features

 - Ensure forks are updated.
 - Automatically integrate new changes from upstream.
 - Pull requests are created when upstreams are updated.
 - Automatically merge or hard reset pull requests to match upstream.
 - Add assignees and reviewers to pull requests.
 - Customize pull request label.
 - Honor branch protection rules.
 - Work well with pull request checks and reviews.


## Getting Started

### Prerequisites
 - Upstream must be in the same fork network.
 - :warning: _Make a backup if you've made changes._

### Basic setup

 - Just install **[<img src="https://prod.download/pull-18h-svg" valign="bottom"/> Pull app](https://github.com/apps/pull)**.

Pull app will automatically watch and pull in upstream's default (master) branch to yours with **hard reset**.

### Advanced setup (with config)

 1. Create a new branch.
 2. Setup the new branch as default branch under repository Settings > Branches.
 3. Add `.github/pull.yml` to your default branch.

#### Most common
(behaves the same as basic setup)

```yaml
version: "1"
rules:
  - base: master
    upstream: wei:master      # change `wei` to the owner of upstream repo
    autoMerge: true
    autoMergeHardReset: true
```

#### Advanced usage
```yaml
version: "1"
rules:                        # Array of rules
  - base: master              # Required. Target branch
    upstream: wei:master      # Required. Must be in the same fork network.
    autoMerge: true           # Optional, Default: false
    autoMergeHardReset: true  # Optional, Default: false DANGEROUS
  - base: dev
    upstream: master          # Required. Can be a branch in the same forked repo.
    assignees:                # Optional
      - wei
    reviewers:                # Optional
      - wei
label: ":arrow_heading_down: pull"  # Optional
```

 4. Go to `https://pull.now.sh/check/${owner}/${repo}` to validate your `.github/pull.yml`.
 5. Install **[![<img src="https://prod.download/pull-18h-svg" valign="bottom"/> Pull](https://prod.download/pull-18h-svg) Pull app](https://github.com/apps/pull)**.


## For Repository Owners

For the most common use case (a single `master` branch), you can just direct users to install Pull with no configurations.
If you need a more advanced setup (such as a `docs` branch in addition to `master`), consider adding `.github/pull.yml` to your repository pointing to yourself (see example). This will allow forks to install Pull and stay updated automatically.

Example (assuming `owner` is your user or organization name):
```yaml
version: "1"
rules:
  - base: master
    upstream: owner:master
    autoMerge: true
    autoMergeHardReset: true
  - base: docs
    upstream: owner:docs
    autoMerge: true
    autoMergeHardReset: true
```


## Author
[Wei He](https://github.com/wei) _github@weispot.com_


## License
[MIT](https://wei.mit-license.org)