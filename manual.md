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
