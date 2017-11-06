```
git cat-file -t 980a0
blob

git cat-file -p 980a0
Hello, World!

git ls-files -s
100644 8ab686eafeb1f44702738c8b0f24f2567c36da6d 0	hello.txt

git add <file>
git rm <file>
git mv <file>

// stage commit in chunks
git add -p                              // interactively add hunks

// stashes
git stash
git stash -p                            // interactively stash hunks
git stash list
git stash show stash@{0}
git stash apply
git stash apply stash@{0}
git stash --include-untracked           // include untracked files
git stash --all                         // be careful - even ignored files!!!
git stash save "WIP: some message..."   // name a stash
git stash branch <optional stash name>  // start a new branch from stash
git checkout <stash name> -- <filename> // grab a sinlge file from a stash
git stash pop                           // remove last stash and apply changes
git stash drop                          // remove the last stash
git stash drop stash@{0}                // remove the nth stash
git stash clear                         // remove ALL stashes
git stash list
git stash show stash@{0}
```


## Blobs
Git blobs are found in .git/objects in subdirs which are named for the first two chars of the sha1 for the blob.
Git blobs have a key sha1. You can manually generate: 
```
echo 'Hello, World!' | git hash-object --stdin
8ab686eafeb1f44702738c8b0f24f2567c36da6d
```

## Trees
Trees describe the directory structure.
Trees can point to blobs or to other (sub) trees.
Trees are stored in .git/objects as compressed blobs in the same way as file blobs.

## Packfiles, Deltas
Git stores deltas along with original file as a compressed single file - packfile.
Packfiles are generated when there are too many objects, during gc, or during push to a remote.

## Commits
Commit points to a tree, and has metadata and point to parent commits. Initial commits do not have parents.
Commit is a code snapshot of changes in staging area and parent commit.

## References
Pointers to commits.
HEAD is usually a pointer to the most recent commit on the current branch.
There can only be one HEAD in a git repo.
.git/refs contains pointers to heads, remotes, and tags.
```
git cat-file -t HEAD
commit
git cat-file -p HEAD
tree d90cbcbaf0b7f54380757d9f48220cd2f95b0533
parent e9806af4caab5a0f96d9bbda931b574eb3eeb892
author Nina Zakharenko <nzakharenko@gmail.com> 1507306931 -0500
committer GitHub <noreply@github.com> 1507306931 -0500

Fix Link in Ex2

cat .git/refs/heads/master
76e0330e59cd46999452e20d08bc1b73fb16d083
```
