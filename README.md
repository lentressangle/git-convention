# iAdvize Git Convention

## <a name='TOC'>Table of Contents</a>

  1. [Rules](#rules)
  1. [Workflow](#workflow)
  1. [Credits](#credits)

## <a name='rules'>Rules</a>

  - Branche `master` is always production-like and deployable.

  - Rebase during feature development.

  - Explicit (non fast-forward) merge when done.

  - Open a Pull Request as early as possible
  
Pull Requests are a great way to start a conversation of a feature, so start one as soon as possible - even before you are finished with the code. The team can comment on the feature as it evolves, instead of providing all their feedback at the very end.



## <a name='workflow'>Workflow</a>

  1. Pull down the latest changes from `master`

```sh
git fetch origin
```

  2. Create a new branch

```sh
git checkout -b feat-myAwesomeFeature-1234 origin/master
```

Branch name structure is composed of 3 parts separated by `-`:

  - Type of the changes: `feat` for a new feature or `fix` for a bug-fix
  - Short but explicit name in camelCase describing the changes
  - ID of the corresponding JIRA ticket (no need for the `IDZ-` part)
  
  3. Work on the feature

  - Commit early, commit often.
  - Make sure your commits are meaningful.
  - Do not cluster separate changes together.

  4. Use `rebase` when you need to fresh up your branch with the latest changes in `master`


  
  5. When ready for feedback push your branch remotely

```sh
git push -u origin feat-myAwesomeFeature-1234
```
  
  6. Create a Pull Request via github
  
  
  
  

## <a name='credits'>Credits</a>

  - http://blogs.atlassian.com/2014/01/simple-git-workflow-simple/
  - https://gist.github.com/jbenet/ee6c9ac48068889b0912
  - https://github.com/blog/1124-how-we-use-pull-requests-to-build-github
  
