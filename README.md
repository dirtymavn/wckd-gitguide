# gmv-gitguide

There's gotta be reminder for slow-learner like me.

---
#### Overall git flow
Stage it (git add .) ---> commit it locally (git commit) ---> push it (git push)

#### When you need to flush thing and start over
```
$ git reset --soft HEAD^  \\undo last commit, back to last staging
$ git commit --amend -m "a proper commit message" \\because it always happens
$ git reset --hard HEAD^ \\time lapse one step back. Increase the ^ to do more step back
```
#### Remotes what? which?
```
$ git remote -v \\list that all remotes
$ git remote add (alias) (remote-url) \\add new one
$ git push -u (remote-repo) (local-branch) \\the -u is to make it default next time
```
## On new feature, bug fix, and branching
Separate major and minor milestone through versioning. As a rule of thumb, use x.y.z where :
x = Major milestone
y = Minor milestone
z = bug fix

V1.1.5 = I got 1 major milestone, 1 minor, 5 bug fix. Rad!

#### Branch it

```
$ git checkout -b nu_branch \\create and checkout da nu branch
$ git merge (branch_to_merge) \\will merge to your existing branch
$ git branch -d unwanted_branch \\remove that unwanted branch. Use -D to force unmerged ones 

$ git push origin :unwanted_branch \\even further: erase the unwanted branch on online repo
```
Hint : fast-forward is just a cool name to describe nothing's happening on your current branch so we'll just merge with another and copy it to your branch. Sad, so much sadness.

#### Tag it
Tag each of your version release. Depends on how you do versioning of course
```
$ git tag -a v1.2.3 -m "Version 1.2.3" \\add new tag
$ git push --tags \\push all the tags
```
#### Rebase instead of pull & push
```
$ git fetch \\fetch newest from repo, but not merge
$ git rebase \\do rebase. If there's conflict, use --continue after you fix it
```
#### Altering commits in the same branch?
```
$ git rebase -i HEAD~3 \\start interactive rebase 3 heads back
```
+ pick : reorder things
+ reword : duh. for rewording
+ edit : edit a commit. Do whatever you want. Soft reset it, make it 3 commits etc. Just remember to rebase --continue
+ squash : merge with previous commit

#### Cherry picking
When you need that one commit only from another feature or branch
```
$ git cherry-pick (hashes) \\will 'pick' that commit only and add it on top of your branch
```
+ --edit : lets you change the commit messages
+ --no-commit : add it only, no commit

## Rewriting History
Only use if it's really necessary. Like when you do something disgraceful that can never be erased from your memory. That necessary.
```
\\check every each commits and do whatever you told it to do.
$ git filter-branch --tree-filter <command> \\add -f to remove the backup

\\ditto. Except it's in index
$ git filter-branch --index-filter <command> \\add -f to remove the backup

\\drops commits that doesn't change anything
$ git filter-branch -f --prune-empty -- --all
```

## Accidentally hard reset a commit?
Reflog it. Git stores double log file and you can restore from it.
```
$ git reflog \\list the secondary log
$ git reset --hard (sha|reflog_names) \\resurrect it from the darkness

\\what if we accidentally remove a branch?
$ git log --walk-reflogs

\\create new branch on the first commit of the dead branch
$ git branch (branch_name) (sha|reflog_names)
$ git checkout (branch_name) \\voila!
```

## Misc
####Prettify your log
```
$ git config --global alias.past "log --graph --decorate --pretty=oneline --abbrev-commit --all"
```
#### Stash it rather than commit and put WIP
```
$ git stash save "msgs" \\save it. Use --keep-index to prevent staging are to be stashed
$ git stash list \\list it
$ git stash apply \\restore it
$ git stash drop \\removes it

OR just do

$ git stash pop \\apply and drop
```
#### on Windows vs Linux collaboration
```
$ git config --global core.autocrlf input \\set on linux
$ git config --global core.autocrlf true \\set on windows
```
## External sources
read : things that you should read to make your Git skill better
+ [The Git Cheatsheet](http://ndpsoftware.com/git-cheatsheet.html)
+ [Git Branching Model](http://nvie.com/posts/a-successful-git-branching-model/)


