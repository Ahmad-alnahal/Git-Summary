# Git
## From Master to Main

>Cultural sensitivity [source](https://www.theserverside.com/feature/Why-GitHub-renamed-its-master-branch-to-main)
- The computer industry's use of the terms ~~master and slave~~  caught everyone's attention in the summer of 2020. Amid the many protests and the growing social unrest, these harmful and antiquated terms were no longer considered appropriate.
-  Software Freedom Conservancy ->=="Both Conservancy and the Git project are aware that the initial branch name, 'master,' is offensive to some people and we empathize with those hurt by the use of that term,"==
-  GitHub took action based on the [Conservancy's suggestion](https://sfconservancy.org/news/2020/jun/23/gitbranchname/) and moved away from the term master when a Git repository is initialized -> =="We support and encourage projects to switch to branch names that are meaningful and inclusive, and we'll be adding features to Git to make it even easier to use a different default for new projects."==  As a result, GitHub renamed the master branch to main branch.
>[source](www.zdnet.com/article/github-to-replace-master-with-main-starting-next-month/)
- after the brutal death of George Floyd and Black Lives Matter Protests in 2019, tech companies wanted to show their support for the black community by abandoning non-inclusive terms such as (==master==,==slave==,==blacklist==,==whitelist==).
## Remote

-  to see your remote name to your git 
```shell
git remote -v
```
## Branche

>[!note]- About Merge
>> You can allow contributors with push access to your repository to merge their pull requests on GitHub.com with different merge options or enforce a specific merge method for all of your repository's pull requests.
>>>- ## [Squashing merge](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/about-merge-methods-on-github#squashing-your-merge-commits)
>>>the pull request's commits are squashed into a single commit. Instead of seeing all of a contributor's individual commits from a topic branch, the commits are combined into one commit and merged into the default branch.![Squashing merge](https://docs.github.com/assets/cb-5742/mw-1440/images/help/pull_requests/commit-squashing-diagram.webp) 
>>>
>>> ==disadvantages :==
>>>1. You lose information about when specific changes were originally made and who authored the squashed commits.
>>>2. If you continue working on the head branch of a pull request after squashing and merging, and then create a new pull request between the same branches, commits that you previously squashed and merged will be listed in the new pull request. You may also have conflicts that you have to repeatedly resolve in each successive pull request.
>>>- ## [Rebasing merge](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/about-merge-methods-on-github#rebasing-and-merging-your-commits)
>>> all commits from the topic branch (or head branch) are added onto the base branch individually without a merge commit.
>>>- ## [fast-forward merge](https://www.atlassian.com/git/tutorials/using-branches/git-merge)
>>>A fast-forward merge can occur when there is a linear path from the current branch tip to the target branch. Instead of “actually” merging the branches, all Git has to do to integrate the histories is move the current branch tip up to the target branch tip This effectively combines the histories, since all of the commits reachable from the target branch are now available through the current one.
>>>![fast-forward marge](https://www.w3docs.com/uploads/media/default/0001/03/4f3db14561c7045ff3375e3d8087d6b3b981a359.png)

-  To See All Branches  In Your Git 
```shell
git branch
```

-  To Create New Branch
```shell
 git branch (your new branch name)
```

-  to switch to another branch 
```shell
 git checkout (branch name)
```

-  to delete branch  
```shell
git branch -d (branch name)
```

-  to create new branch and  switch to it
```shell
git checkout -b  (your new branch name)
```

-  to rename branch -> log to branch then => 
```shell
git branch -m (new branch name)
```

-  to merge other branch with master branch -> log to master then => 
```shell
git merge (other branch name)
```
## Workflows

- There is no one-size-fits-all Git workflow.
- A workflow should be simple and enhance the productivity of your team
- Your business requirements should help shape your Git workflow
>==**some Workflows :**==
>>**Centralized Workflow**
>>>- the Centralized Workflow uses a central repository to serve as the single point-of-entry for all changes to the project.
>>>- This Centralized workflow doesn’t require any other branches besides `main`.
>>**Feature branching**
>>>- Feature Branching is a logical extension of Centralized Workflow.
>>>- all feature development should take place in a dedicated branch instead of the `main` branch.
>>>- It also means the `main` branch should never contain broken code
>>>- advantage for continuous integration environments.
>> **Forking Workflow**
>>>- it gives every developer a server-side repository.
>>>- each contributor has not one, but two Git repositories: a private local one and a public server-side one.
>>**Gitflow Workflow**
>>>- The Gitflow Workflow defines a strict branching model designed around the project release.
>>>- This workflow doesn’t add any new concepts or commands beyond what’s required for the Feature Branch Workflow.
>>>- it assigns very specific roles to different branches and defines how and when they should interact.

[For More](https://www.atlassian.com/git/tutorials/comparing-workflows)

## Cherry Pick

- a powerful command that enables arbitrary Git commits to be picked by reference and appended to the current working HEAD. Cherry picking is the act of picking a commit from a branch and applying it to another.

- can be useful for undoing changes.

- if commit is accidently made to the wrong branch. You can switch to the correct branch and cherry-pick the commit to where it should belong.

- Bug hotfixes : When a bug is discovered it is important to deliver a fix to end users as quickly as possible.

- Undoing changes and restoring lost commits.

>[!note]- How to use git cherry pick
>> - First we ensure that we are working on the `main` branch.
>> ```shell
>> git checkout main
>> ```
>> - Then we execute the cherry-pick with the following command:
>> ```shell
>> git cherry-pick f
>> ```
>> - option will execute the cherry pick but instead of making a new commit it will move the contents of the target commit into the working directory of the current branch.
>> ```shell 
>> git cherry-pick --no-commit
>> ```
>> - Passing the `-edit` option will cause git to prompt for a commit message before applying the cherry-pick operation.
>> ```shell
>> git cherry-pick -edit
>> ```
>> 
## Clone

- To Clone Project Form GitHub
```shell
git clone (URL)
```
## Status

-  To Check Files That Have Not Been Pushed To Git
```shell 
git status
```
## Staging Area

-  To Track Not Pushed Files To Staging Area
```shell
git add (file-name)
```
==OR==
```shell
git add *
```

-  To Untrack File From Staging Area  
```Shell
git reset head (file-name)
```

-  To Untrack All File From Staging Area  
```Shell
git restore --staged *
```

- To Delete All Untracked Files 
```shell
git clean -f
```

- To Show All Untracked Files That Can Be Deleted 
```shell
git clean -n
```

-  To Commit Files To Local 
```shell
 git commit -m "(your commit description)"
```

## Push

-  to push commits to your repo
```shell
 git push (remote) (branch)
```

-  to do push request from other branch to Origin remote -> log to other branch do your changes and commit changes then => 
```shell
git push origin (other branch) 
```
## Git Revert

- command can be considered an 'undo' type command, however, it is not a traditional undo operation. Instead of removing the commit from the project history, it figures out how to invert the changes introduced by the commit and appends a new commit with the resulting inverse content.

- Reverting should be used when you want to apply the ==inverse== of a commit from your project history.

```shell
git revert HEAD
```

>[!note]- Resetting vs. reverting
>- It's important to understand that `git revert` undoes a single commit—it does not "revert" back to the previous state of a project by removing all subsequent commits, this is actually called a reset, not a revert.
>- ==Reverting== has two important advantages over resetting:
>> 1. it doesn’t change the project history, which makes it a “safe” operation for commits that have already been published to a shared repository.
>> 2.  is able to target an individual commit at an arbitrary point in the history
>- ==Reset== can only work backward from the current commit.
>```shell
>git reset HEAD~
>```

## Pull

-  to get changes from git
```shell
git pull (remote)
``` 
## Configurations

-  to get all configurations of your git  
```shell
git config -L
```

-  to get (something) from config 
```shell
 git config --global (something)
```

-  to set value to (something) in config 
```shell
 git config (something) "(your new value)"
```
## Create Security Key

- to create security key for your git 
```shell
 ssh-keygen -t rsa -b 4096 -c "(your Email)"
```
 ==then== fill required labels ==and== ask for your key
```shell
cat ~/ssh/id_rsa.pub
```
 ==then== add the key to your GitHub

-  to connect to your git using security key   
```shell
ssh -T git@github.com
```
==then== Enter your key
## Shortcuts

-  to create shortcut for (something in git code)  
```shell
git confg --global alias.(your shortcut) (something in git code)
```

## Stash

-  to hide changes after add to staging area
```shell
git stash
```
==OR==
```shell
git stash "(notes about changes)"
```

-  to get hide changes and delete stash box
```shell
git stash pop
```

-  to get hide changes with out deleting stash box
```shell
 git stash apply
```

-  to show how many item's are in your stash list
```shell
 git stash list
```

-  to show what some stash item contains with out get it
```shell
git stash show stash@{(item index)}
```

-  to delete item from stash
```shell
git stash drop stash@{(item index)}
```

-  to delete all stash list item's
```shell
git stash clear
```
## Log

- To Show All Git Changes 
```shell
git log
```
==Note== To Close Log Type The Letter (q)
## Tag(version)

- To Show Git All Tags 
```shell
git tag
```

-  To Create New Tag 
```shell
git tag (tag name)
```

-  To Create New Tag With Your Comment
```shell
git tag -a (tag name) -m "(your comment)"
```

- To Push Tag To Git 
```shell
git push (remote) (tag name)
```

- To Delete Tag From Local 
```shell
git tag -d (tag name)
```

- To Delete Tag From repo 
```shell
git push (remote) --delete (tag name)
```
## Questions

>[!question]- how to get code from others branch that i dont have accses to to my branch with out changeing mycode in my branch
> 1. Fetch the remote branch
> ```shell
> git fetch origin remote_branch_name
> ```
 > 2. Create a new branch
> ```shell
>git branch new_branch_name
> ```
 > 3. Switch to the new branch
> ```shell
>git checkout new_branch_name
> ```
> 4. Merge the remote branch
> ```shell
>git merge origin/remote_branch_name
> ```
> 5. Resolve conflicts (if any)
> 6. Commit the changes:
> 7. Push the new branch

>[!question]- how to get code from others branch to my branch with out changing myCode
>1. Switch to your branch
>```shell
>git checkout <your_branch>
>```
>2.Create a new branch to hold the code from the other branch
>```shell 
>git checkout <source_branch>
>```
>3.Switch to the branch from which you want to get the code
>```shell
>git checkout <source_branch>
>```
>4.Merge the source branch into the temporary branch
>```shell
>git merge <source_branch> --strategy=ours
>```
>5.Switch back to your branch
>```shell
>git checkout <your_branch>
>```
>6.Merge the temporary branch into your branch
>```shell
>git merge <temp_branch>
>```
>7.Delete the temporary branch
>```shell 
>git branch -D <temp_branch>
>```

>[!question]- What is pull request
>- feature that makes it easier for developers to collaborate using **Bitbucket**.
>- They provide a user-friendly web interface for discussing proposed changes before integrating them into the official project.
>- **pull requests are a mechanism for a developer to notify team members that they have completed a feature.**
>![pull request](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTuO585kblpHNFU1Lf5tDatV3weMmd0UK-50kfT_w7bog&s)
>- provide 4 pieces of information to file a pull request:
>>1. **the source repository**
>>2. **the source branch**
>>3. **the destination repository**
>>4. **the destination branch**
>>![pull request](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcStlFwRPnph8jN3QbjiNejZ6cn8cnrnPBR5-znhrV9M4A&s)
>- pull request requires either two distinct branches or two distinct repositories

## Best Git GUI’s
- [GitHub Desktop](https://desktop.github.com/)
- [GitKraken](https://www.gitkraken.com/)
- [Sourcetree](https://www.sourcetreeapp.com/)
- [Tortoise Git](https://tortoisegit.org/)
- [SmartGit](https://www.syntevo.com/smartgit/)*
- [GitForce](https://github.com/gdevic/GitForce)
- [Git Cola](https://git-cola.github.io/)
- [Fork](https://git-fork.com/)

# Random
- To Create Folder using CMD
```shell
mkdir folder-name
```
- To Create New File using CMD
```shell
touch (file-name)
```