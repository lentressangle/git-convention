# iAdvize Git Convention

## <a name='TOC'>Table of Contents</a>

  1. [Rules](#rules)
  1. [Branching](#branching)
  1. [Start a feature](#start-feature)
  1. [Commit message](#commit-message)
  1. [Submission guidelines](#submission-guidelines)
  1. [Tips and Tricks](#tips-tricks)
  1. [Credits](#credits)

## <a name='rules'>Rules</a>

  - Branche `master` is always production-like and deployable.

  - Rebase during feature development.

  - Explicit (non fast-forward) merge when done.

  - Open a Pull Request as early as possible

Pull Requests are a great way to start a conversation of a feature, so start one as soon as possible - even before you are finished with the code. The team can comment on the feature as it evolves, instead of providing all their feedback at the very end.

## <a name='branching'>Branching</a>

You should always create a new branch when working on a new feature.

  - **master**: Should be exactly the same as production.
  - **ABC-XXX-Description**: Feature branches
        > ABC-XXX is the issue identifier (ex: IDZ-4332)
        > Description is a short introduction about the feature (IDZ-4332-addSomeCrazyFeature)

## <a name='start-feature'>Start a feature</a>

```bash
# Fetch commits from remote
$ git fetch origin

# Create feature branch
$ git checkout -b ABC-XXX-Description origin/master

# Push your branch early to get feedback
# Use `rebase` if you need to fresh up your branch
# Follow convention for commit message
$ git push -u origin IDZ-XXX-Description

# When you're ready, create a pull request following convention
```

## <a name='commit-message'>Commit message conventions</a>

Commit message must be readable and understandable.

### Commit message Format

```php
// Simple
<type>(<scope...>): <Description>

// Simple with issue
<type>(<scope...>): <Description>
#ABC-XXX

// Full description
<type>(<scope...>): <Short description>

<Explain more...>

#ABC-XXX

```

### Type

##### Example

```text
feat(RestApiController, Route): add constraint to user profile

Now, each request must provided an email to be correctly executed.

ABC-XXX #closed
```

- **feature**: `feat(ApiController): Add post method for feature A`
    > Should represent a feature commit

- **fix**: `fix(MessageService): fix wrong status code on GET request`
    > Should represent a bug fix

- **style**: `style(ApiController): :lipstick:`
    > Changes that don't affect meaning of the code only white-space, formatting

- **documentation**: `doc(ApiController, MessageService): add documentation in controller + Reword class description for  Service`
    > Should represent a documentation changes

- **refactor**: `refacto(MessageService): change message generation process`
    > A change for better readablilty (Don't add feature or fix bug)

- **performance**: `perf(UrlGenerator): Replace libA for libB`
    > Should represent a performance improvement

- **test**: `test(MessageService): Implement message service test for GET request`
    > Should represent a test implementation


## <a name='submission-guidelines'>Submission guidelines</a>

- Create a PR (Pull Request) on github
- Use a title like: `ABC-XXX Some awesome description`
- Use a template for PR description:

    ```
        #### What's this PR purpose?
        > Ticket link [#XXXX](url)

        Little description
        #### PR Dependencies
        #XXX
        #XXX
    ```
### Bookmarklet
```javascript
javascript:(function() {var e = document.getElementById('pull_request_body');if (e) {e.value += '#### What\'s this PR pupose?\n> Ticket link []()\n\n DESCRIPTION\n#### PR Dependencies\n#XXX\n#XXX';}})();
```

## <a name='tips-tricks'>Tips and tricks</a>

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

