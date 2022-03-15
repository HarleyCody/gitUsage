## Delete irrelevant file from PR [Link](https://stackoverflow.com/questions/39459467/remove-a-modified-file-from-pull-request)

Switch to the branch to working branch:
```
$ git checkout pull-request-branch
```
Overwrite the modified file(s) with the file in another branch, let's consider it's master:
```
$git checkout origin/master -- src/main/java/HelloWorld.java
```
Commit and push it to the remote:
```
git commit -m "Removed a modified file from pull request"
git push origin pull-request-branch
```
## Squash commits into first commit [Link](https://stackoverflow.com/questions/6934752/combining-multiple-commits-before-pushing-in-git)

Rebase the working branch to the first commit
```
git rebase -i origin/master
```
This will prompt a history file of git log like
```
pick 16b5fcc Code in, tests not passing
pick c964dea Getting closer
pick 06cf8ee Something changed
pick 396b4a3 Tests pass
pick 9be7fdb Better comments
pick 7dba9cb All done
```
Press i to be in a insert mode
Change all the pick to squash (or s) except the first one:
```
pick 16b5fcc Code in, tests not passing
squash c964dea Getting closer
squash 06cf8ee Something changed
squash 396b4a3 Tests pass
squash 9be7fdb Better comments
squash 7dba9cb All done
```
Press ESC + wq to save and quit editor

Then the editor of git comments will appear like:
```
#1st commit
All done
#2nd commit
Better comments
#3rd commit
Tests pass
#4th commit
Something changed
#5th commit
Getting closer
#6th commit
tests not passing
```
Press i to be in a insert mode
Comment out the commit message after first one 
```
#1st commit
All done
#2nd commit
#Better comments
#3rd commit
#Tests pass
#4th commit
#Something changed
#5th commit
#Getting closer
#6th commit
#tests not passing
```
Press ESC + wq to save and quit editor

Push the head forcely by:
```
git push -f
```
We might need rebase the head before push
```
git rebase origin master
```
and then do forcily push again
```
git push -f
```
