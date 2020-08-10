# GIT
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
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExMDkzMTk2MCwyODAyMzk0MTEsMTk2NT
g3OTA4OV19
-->