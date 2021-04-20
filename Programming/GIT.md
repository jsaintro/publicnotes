# GIT
## Creating a branch
### Create the branch in the local copy
```
git checkout -b <<branchname>>
```
Note this is the combination of `git branch` and `git checkout`
### Commit to github
```
git push -u origin <<branchname>>

## Resync Branch with Master

git checkout master
git pull
git branch -v
git checkout VREX-5940
git merge master
git branch -v
git status
git commit -am "merge with latest master"
git status
git push

## Merging a branch into another branch
git checkout targetbranch
git merge sourcebranch

## Different ssh keys (I.E. jsaintrocc) for different repos
vi ~/.ssh/config
Host gitjsaintrocc
    Hostname github.com
    IdentityFile ~/.ssh/id_rsa_jsaintrocc
    IdentitiesOnly yes

Replace github.com with gitjsaintrocc

<!--stackedit_data:
eyJoaXN0b3J5IjpbNTU1NjM0NTkwLC02MjM0NzgyNSwtMTEwOT
MxOTYwLDI4MDIzOTQxMSwxOTY1ODc5MDg5XX0=
-->