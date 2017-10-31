# Github Flow - useful commands

### Start a new unit of work
```
git checkout master
git pull origin master
git checkout -b feature-123 origin/master
```

### WIP commits
If you save part-way through an atomic piece of work, save a WIP commit. But always undo it again before picking it up again. 
`git reset HEAD~1`

### Ensure branch is up to date with latest on master branch
```
git fetch origin
git rebase origin/master
```

### Merge branch back into master
```
git checkout master
git merge feature-123             // creates merge commit
git merge feature-123 --ff-only   // doesn't create merge commit
```

### Other useful commands
```
git add -p           // add changes to staging interactively - a chance to review changes
git reset --hard     // removes changes to modified files from the index
git log --oneline    // more succinct git log output
```
