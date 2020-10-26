# Kottans Front-End 2020/2021 reflections
Repository for my personal reflections, code and notes about [Front-End Course](https://github.com/kottans/frontend) (version 2020-2021) provided by [Kottans community](https://kottans.org/) :cat2:<hr>
# Stage 0
<details>
<summary>00. Git Basics</summary>

## Git Basics
- [Udacity course: "Version Control with Git"](README.md#udacity-version-control-with-git)
- [Visual interactive course: Learn Git Branching (Main 1st section, Remote 1st section)](README.md#learn-git-branching)

<hr>

### [Udacity: Version Control with Git](https://www.udacity.com/course/version-control-with-git--ud123)
<details>
<summary>Screenshots</summary>
![Udacity Version control with Git](task_git_basics/udacity-version-control-with-git.jpg)
</details>

#### :key: Key takeaways
**VSC** Version control system is the same as **SCM** Source code manager.
#### Why to use version control system?
 VSC tracks changes into a project (a set of files) as separate steps. By this a historical roadmap of how we get to the current state of a project is written. It is possible to describes each change separately: what was done and why it was done. Main features of VCS are:
- let us understand where is some specific copy of a project vs. other copies on overall project's roadmap
- les us work with a project on any arbitrary stage of a roadmap
- work with each change separately:
  - appply it
  - review it later
  - change back with out effecting other changes including next one
  - resolve conflicts with other changes
#### Cetralized vs. Distributed VCS
Centralized VCS has single place to store all information (Subversion for example)

Distributed VCS provides each user with full project information on its own computer (Git, Mercurial).

Distributed VCS advantages:
- fast to move between versions (all data is local, it is done by copying files from repository to working tree)
- independent work with changes:
  - physically as no internet connection is required
  - team workflow as changes could be done only with personal version at first

Distributed VCS disadvantages:
- work with binary files is costy in terms of space to store all versions
- project with long history of changes requires time to download and space to store
- all project files available to each member thats increase exposure risks
#### Git project places
All local Git operations are done between three places:
- *Working tree* (**tree**) - files in project directory that are available for user to edit
- *Staging Index* (**index**) - freezed version of changed files ready to be committed into repository
- *Repository* (**repo**) - hidden folder that contains history of all committed changes
#### Git branches merge
There are two types of merges:
- *fast-forward merge* - if merging branch is directly ahead of current branch (current branch does not have any commits that are not in merging branch). Just moves the pointer of current branch to the pointer of merging branch
- *regular merge* - creates new commit that joins all different commits in both branches. If conflicts occur they should be resolved manually (files with conflict description will be added to working tree for editing and then staging)
#### Absolute Commit Reference
Commits could be referenced by
- branch pointers
- special pointer HEAD
- tags
- SHA (Secure Hash Algorithm)
#### Relative Commit Reference
Merge commit (in case of regular merge) has two parents:
- *first* parent the last commit of current branch in merge
- *second* parent the last commit of merged branch
Ancestry References:
- `^` - indicates the parent commit. `^` is single or *first* parent, `^2` - *second* parent
- `~` - indicates the *first* parent commit. Used as shorthand for number of *first* parent commits: `~3` equals `^^^`
Ancestry reference could be combined: `HEAD~4^2` - 4 parents back and then second parent in the merge
#### Git corrections
**Edit** only the last commit: `git commit --amend` - edit message of the last commit. And if files added to staging index, they will be added or replace the same files in repository for the last commit

**Change back** commit: `git revert` - creates new commit with opposite changes

**Delete** commits after specified one: `git reset` (set commits for deletion after ~30 days, they could be viewed with `git reflog`). Branch head is set to choosen commit. Possible impact on tree and index is defined by flag:
- `--soft` tree and index are unchagned
- `--mixed` (default) resets the index but not the working tree
- `--hard` resets the index and tree
#### Git cheatsheet and reference
Cheatsheet from basic to rebase: [Atlassin Bitbucket](https://www.atlassian.com/git/tutorials/atlassian-git-cheatsheet)

Not covered in the cheatsheet:
- `git tag` - create/delete special commit reference
- `git show` - show full information about commit (by default the last one)
- `git log --all` - all flag to show log from all branches in the repository, not only the current one

Git full reference and book: [git-scm](https://git-scm.com/doc)
#### :+1: Pros
Introduction to Git local usage without remote complication. Good structure of lessons by actions to perform: review, commit, branch, edit.
#### :-1: Cons
Rebase is not covered. Changes in Git v2.14 and later reflected only with notes but not incorporated into the course itself.
#### :bulb: New
Udoing changes in Git
#### :gift: Suprising
Google docs revision history
#### :hammer: Useful
First of all run command `git status` in every git directory

`git add .` adds all modified files from working tree into staging index except listed in `.gitignore` file 

Navigation in unix command line pager program: **less**
- down: j, d (*down* half page), f (*full* page down)
- up: k, u (*up* half page), b (*back* full page up)
- quit: q

Commit message body describes why change was done. To add it leave a blank line after commit message in editor.

Always put newline as last character of the file is a good style. It is possible to add this into preferences of a code editor.

[:arrow_up_small: Back to this task content](README.md#git-basics)
<hr>

### [Learn Git Branching](https://learngitbranching.js.org/)
Main: Introduction Sequence

Remote: Push&Pull -- Git Remotes!
<details>
<summary>Screenshots</summary>
![Learn Git branching Introduction](task_git_basics/learninggitbranching-main-introduction-sequence.jpg)
![Learn Git branching Push and Pull](task_git_basics/learninggitbranching-remote-push-and-pull.jpg)
</details>

#### :key: Key takeaways
#### Remote repository
Remote repositories provide two advantages:
- backup of your local repository
- synchronize team work on the same project
#### Remote branch
When cloning git creates special branch: `<remote repo name>/<branch name>`. Usually remote is called origin. This branch work in HEAD detached mode: branch pointer does not move with new commits, only fetching from remote updates branch pointer. Commits in detached mode could be used for experimantal changes.
#### Remote git commands
`git fetch` - only updates remote branch to their state at the moment, does not perform changes to local branches

`git pull` - shorthand for two commands `git fetch; git merge remote/branch`

`git pull --rebase` - shorthand for two commands `git fetch; git rebase remote/branch`

`git push` - allowed only after updating state of remote in local repository
#### :+1: Pros
Good visualization of git graph to play with:
- Shows difference between merge and rebase
- Shows work with remote branches
#### :-1: Cons
It does not fully replace practice with real git repositories. You still need to train all commands with real repository.
#### :bulb: New
`git rebase` to make project history straightforward.
#### :gift: Suprising
git HEAD detached mode for experimenting
#### :hammer: Useful
`git checkout -b <branch name> <commit>` creating branch and checking it out at specific commit

[:arrow_up_small: Back to this task content](README.md#git-basics)
<hr>
</details>
