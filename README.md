# Naoned Git Convention

## <a name='TOC'>Table of Contents</a>

  1. [Repositories](#repositories)
  1. [Branching](#branching)
  1. [Start a feature](#start-feature)
  1. [Commit message](#commit-message)
  1. [Tips and Tricks](#tips-tricks)
  1. [Credits](#credits)

**You shall in english write your repositories, commit message and branch names.**
## <a name='repositories'>Repositories</a>
### Naming

  ```
# The repo name is in snake-case (dash separator and lowercase)
<project?>-<techno?>-<name?>-<type>
  ```
[More information about snake-case](https://en.wikipedia.org/wiki/Snake_case) :snake:

- **Project**: The top level project (upnao, inao, vanao, mediator, naopal, etc...)
- **Techno**: The techno can be either a language or a framework (php, js, symfony, angular, etc... cf stack)
- **Name**: Choose a name with your team but you are free to choose whatever you want
- **Type**: Main concern of the repo
  - ***App***: A complete application (meant to disappear in favor of API/client).
  - ***Library***: A library...
  - ***API***: An API...
  - ***Client***: A client for an API. Might be web or native.
  - ***Cli***: A command line tool.
  - ***Deploy***: Anything related to deployments (cf exploitation).
  - ***Convention***: Rules or usage of a technology or guideline.
  - ***Theme***: A drupal theme
  - ***Module***: A drupal module
  - @todo: complete this list based on real life usage

### Examples
```
# <project>-<type>
inao-app
upnao-api
mediator-api
mediator-client
synchronizer-cli

# <project>-<techno>-<type>
upnao-ng-client

# <techno>-<type>
git-convention

# <techno>-<name>-<type>
php-toolbox-library

# <product>-<techno>-<name>-<type>
naopal-php-blog-module
```

## <a name='branching'>Branching</a>

You must create a new branch when working on a new feature. 

  - **master**: The production branch. Must always be stable and deployable.
  - **hotfix**: A tempory branch from master to make hotfix
  - **IterationName**: Specific branch for an iteration
  - **US-xxxxx**: Where *xxxxx* is the name of the User Story of the iteration 
  - **develop**: This branch can contains many iterations
  - **release**: When there are enough iterations in branch 'develop' , pass it on branch 'release' to be checked (before to be put on the master branch)

:warning: All **US_xxxxx** branches must be created in same time from the IterationName branch, because **US_xxxxx** must be independent.

Follow the Git-flow works : 

<img src="http://nvie.com/img/git-model@2x.png" align="center" height="500"/ >

## <a name='start-feature'>Start an iteration</a>

```bash
# Fetch commits from remote
$ git fetch origin

# Create an iteration branch 
$ git checkout -b IterationName origin/master

# Create an new branch for an user story 
$ git checkout -b US_xxxxxx origin/master

# When you're ready, create a pull request following convention
```

## <a name='commit-message'>Commit message conventions</a>

Commit message must be readable, understandable and write in english.

### Commit message Format

```php
// Simple
<type>(<scope...>): <Description>

// Simple with issue
<type>(<scope...>): <Description>

// Full description
<type>(<scope...>): <Short description>

<Explain more...>
```
For more "fun" use [emojis](http://www.emoji-cheat-sheet.com/) :+1:.

### Type

##### Example

```text
feat(RestApiController, Route): add constraint to user profile

Now, each request must provided an email to be correctly executed.

ABC-XXX #closed
```

- **feature**: `feat(ApiController): Add post method for feature A`
    > Should represent a feature commit

- **fix**: `fix(MessageService): fix #12 wrong status code on GET request`
    > Should represent a bug fix<br>
    > Must reference an issue ID

- **style**: `style(ApiController): :lipstick:`
    > Changes that don't affect meaning of the code only white-space, formatting

- **documentation**: `docs(ApiController, MessageService): add documentation in controller + Reword class description for  Service`
    > Should represent a documentation changes

- **refactor**: `refact(MessageService): change message generation process`
    > A change for better readablilty (Don't add feature or fix bug)

- **performance**: `perf(UrlGenerator): Replace libA for libB`
    > Should represent a performance improvement

- **test**: `test(MessageService): Implement message service test for GET request`
    > Should represent a test implementation

- **misc**: `misc(Dockerfile): Change node version to 0.12`
    > Changes that didn't match any other categories



## <a name='tips-tricks'>Tips and tricks</a>


### Use Gitg :bulb:

[Gitg](https://wiki.gnome.org/Apps/Gitg) is a graphical user interface for git. It aims at being a small,
fast and convenient tool to visualize the history of git repositories.
Besides visualization, [gitg](https://wiki.gnome.org/Apps/Gitg) also provides several utilities to manage your
repository and commit your work.

### Select hunks for better commit

Sometime, in development process you fix bug when creating feature. And this bug fix isn't really a part of the feature.

```bash
# For example you made changes on ApiController.php
# One for the feature and one for a bug fix
$ git status
    modified:   ApiController.php

# use git commit -pm to select which part to commit
$ git commit -pm 'fix(ApiController): fix a hilarious bug'

You can use many options on every hunk

y - stage this hunk
n - do not stage this hunk
q - quit; do not stage this hunk or any of the remaining ones
a - stage this hunk and all later hunks in the file
d - do not stage this hunk or any of the later hunks in the file
g - select a hunk to go to
/ - search for a hunk matching the given regex
j - leave this hunk undecided, see next undecided hunk
J - leave this hunk undecided, see next hunk
k - leave this hunk undecided, see previous undecided hunk
K - leave this hunk undecided, see previous hunk
s - split the current hunk into smaller hunks
e - manually edit the current hunk

# You can now commit your feature
# Now you can cherry-pick the bug fix to share it with other branch
# without sending feature part

```

## <a name='credits'>Credits</a>

  - http://blogs.atlassian.com/2014/01/simple-git-workflow-simple/
  - https://gist.github.com/jbenet/ee6c9ac48068889b0912
  - https://github.com/blog/1124-how-we-use-pull-requests-to-build-github
