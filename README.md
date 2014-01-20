# iAdvize Git Convention

## <a name='TOC'>Table of Contents</a>

  1. [Rules](#rules)
  1. [Workflow](#workflow)
  1. [Resources](#resources)


  - Branche `master` is always production-like and deployable.

## <a name='rules'>Rules</a>


 Good :)
 
  - https://github.com/reenhanced/gitreflow ? (to study)

  - Rebase during feature development.

    With a `git rebase`, or `git pull --rebase`, you simply replay those commits on top of the new head. Now, if you push, you have linear history, rather than a divergence/merge.
  

  - Explicit (non fast-forward) merge when done.
- Release are tracked by tag

  - Open a Pull Request as early as possible
  
Pull Requests are a great way to start a conversation of a feature, so start one as soon as possible - even before you are finished with the code. The team can comment on the feature as it evolves, instead of providing all their feedback at the very end.

Bad :(
- Don't rebase people's branch until it's ready to be merged
- Don't rebase collaborative branch

## GitHub notes

- Don't fork. Push feature branches directly to main repo.



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
  
  7. Perform a final rebase cleanup after the Pull Request has been approved
  

## <a name='credits'>Resources</a>  

  - http://blogs.atlassian.com/2014/01/simple-git-workflow-simple/
  - https://gist.github.com/jbenet/ee6c9ac48068889b0912
  - https://github.com/blog/1124-how-we-use-pull-requests-to-build-github
  - http://scottchacon.com/2011/08/31/github-flow.html
  
