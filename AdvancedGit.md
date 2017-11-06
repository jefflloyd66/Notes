```
git cat-file -t 980a0
blob

git cat-file -p 980a0
Hello, World!
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
