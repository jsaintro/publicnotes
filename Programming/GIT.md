# GIT
## Creating a branch
```
git checkout -b <<branchname>>
```
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
eyJoaXN0b3J5IjpbLTIwOTI3NDk5NjUsLTYyMzQ3ODI1LC0xMT
A5MzE5NjAsMjgwMjM5NDExLDE5NjU4NzkwODldfQ==
-->