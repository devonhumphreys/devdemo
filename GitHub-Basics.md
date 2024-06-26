
<!-- README.md is generated from README.Rmd. Please edit that file -->

## Introduction

This document provides a step-by-step guide to getting set up with
GitHub and using it to collaborate on code development.

## GitHub

GitHub is an online version control and collaboration system. It runs
based on Git (a local version control system) but allows for code
sharing, peer review, editing, and all versions to be tracked across
multiple team members.

Old versions of code may be checked out if needed.

The Git model is tree-like, where “main” is the trunk of the tree and
serves as the the production-level, public-facing version of code.
Branches are produced when someone would like to edit the code without
affecting the production version until all the work (i.e., revisions,
QC) has been completed and confidence in the updates is high.

Once complete, these branches may be merged with the main branch via a
Pull request. This signals to the lead developer to review the changes
in a given branch and merge them with the production version for a new,
updated public-facing version.

GitHub requires a bit of a high learning curve, but once understood can
dramatically improve programming efficiency, collaboration, and
versioning.

## Best Practices

**Note:** repo = repository

When working with Git, it is a best practice to always **PULL** the most
up-to-date version of the project first thing as you sit down to work on
it yourself. This will bring in any important updates to your local git
repo, so that you are working off of the most recent version.

At the end of your own updates, always **COMMIT** your changes to git
first, then **PUSH** them to the GitHub repository. Committing saves the
changes to local git, whereas pushing takes those committed changes and
sends them to the shared repository.

Following these steps in this order will save you a lot of trouble.

1.  **PULL** the repo from GitHub
2.  **Edit/add/delete** files as appropriate
3.  **COMMIT** your updates to local git
4.  **PUSH** your committed updates to GitHub

## Gitting Started

### 1. Create Github Account

1.  Go to <https://github.com/> to register an account.

*I recommend you use your personal email address for this, as your
account should follow you beyond your time at any one company. Don’t
worry, corporate-sponsored work will be held in **private** repositories
only visible to those with permissions.*

### 2. Confirm or Install Git

#### Check for Existing Git

``` r
shell("which git")
```

If the above command fails with error code 1, then git is not available
and needs to be installed.

#### Install Git

Download and install Git for Windows: <https://gitforwindows.org/>

**NOTE:** When asked about “Adjusting your PATH environment”, make sure
to select “Git from the command line and also from 3rd-party software.
Otherwise accept all defaults.

### 3. Install and load “usethis”

We will use the R package “usethis”, so first we make sure it is
installed and loaded into the current R session.

``` r
# Define a function to check and install the package if needed
check_and_load_package <- function(package) {
  if (!require(package, character.only = TRUE)) {
    # If the package is not installed, install it
    install.packages(package)
    # Load the package after installation
    library(package, character.only = TRUE)
  }
  else{
    library(package, character.only = TRUE)
  }
}


check_and_load_package("usethis")
```

### 4. Add credentials to .gitconfig

``` r
# Example from my own .gitconfig - do not copy exactly ;)
use_git_config(user.name = 'Devon Humphreys', 
               user.email = 'dev.humphreys@gmail.com')
```

**Note:** your email must be the same as the email you used to register
on GitHub.

### 5. Connect Github to RStudio

Create a personal access token (PAT) to link Github to RStudio:

``` r
create_github_token()
```

This will launch Github in a browser. Give the token a simple, specific
name and click “Generate Token”.

Copy this token to the clipboard and save in a Password manager.

Next, save these credentials within RStudio:

``` r
library(gitcreds)
gitcreds_set()
```

Paste your copied PAT when prompted. Click Enter.

You’re all set!
