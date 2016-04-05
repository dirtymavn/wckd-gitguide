# gmv-gitguide

There's gotta be reminder for slow-learner like me. Read this everytime before committing progress, until you remember it like the back of your hand.

---
#### Status flow
Stage it (git add .) --> commit it locally (git commit) --> push it (git push)

#### Crap, I shouldn't have done that
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
#### rebase instead of pull & push
```
$ git fetch \\fetch newest from repo, but not merge
$ git rebase \\do rebase. If there's conflict, use --continue after you fix it
```
## Misc
Prettify your log : because it's cool
```
$ git config --global alias.past "log --graph --decorate --pretty=oneline --abbrev-commit --all"
```




