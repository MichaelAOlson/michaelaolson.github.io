# A Small Git Mystery

At this point in my career, I am pretty comfortable using git. I will still sanity check myself renaming branches or trying to remove anything from history, but I comfortably manage changes from stash to remote and across branches. As such, it was particularly surprising when my common commands left me in an unexpected state.

---

```bash
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   my_file
$ git add my_file
$ git commit -m "Updating my_file"
[main hash] Updating my_file
 1 file changed, X insertions(+), Y deletions(-)
$ git push
Counting objects: 1, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (1/1), X bytes | 0 bytes/s, done.
Total 1 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local objects.
To https://wouldntyouliketo.com/know.git
 ! [remote rejected] main -> main (permission denied)
error: failed to push some refs to 'https://wouldntyouliketo.com/know.git'
```

Whoops! I thought I was on a branch. Fortunately, I was rejected from pushing directly to main. Fixing...

```bash
$ git checkout -b new_branch
Switched to a new branch 'new_branch'
$ git checkout main
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)
$ git reset HEAD~1
Unstaged changes after reset:
M       my_file
$ git stash
Saved working directory and index state WIP on main: hash Last commit message
$ git stash list
stash@{0}: WIP on main: hash Last commit message
$ git checkout new_branch
Switched to branch 'new_branch'
$ git stash pop
On branch new_branch
nothing to commit, working tree clean
Dropped refs/stash@{0} (hash)
```

Huh? Nothing to commit? Where are my changes?

```bash
$ git status
On branch new_branch
nothing to commit, working tree clean
$ git stash list
$
```

...What? Where did my changes go? Time to Google change recovery using this dropped stash hash...

---

Did you see the mistake as it happened? I was scratching my head, but looking back, I find it glaringly obvious. It is not that I learned anything new about how git commands work, but it was certainly an edge case that I typically don't encounter.

When my push was rejected, I had a commit on my local master. This carried over with `git checkout -b new_branch` and contained all of the changes that I had `reset` and `stash`ed. When I then `pop`ped these changes, they successfully applied, dropping from the stash and resulting in no change on the branch.

**Understand alternative means to achieve your goal in case your tools catch you off guard.**

In this case, using the hash of the dropped stash entry to apply my changes to a clean new branch.
