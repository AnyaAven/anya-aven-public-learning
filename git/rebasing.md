## Git Rebasing

Rebasing in Git is a way of integrating changes from one branch into another by 
moving or "rebasing" commits from one branch onto another. 
Unlike merging, which creates a new "merge commit" that joins two branches, 
rebasing _rewrites_ the commit history.

### Here’s how it works:

When you rebase one branch onto another, 
Git takes the changes from the base branch and applies them underneath 
the commits on your feature branch. This rewrites the commit history 
of the feature branch as if you had made your changes starting from 
the current tip of the base branch, rather than from where the branch originally diverged.

#### **Example Rebase:**
Let's say you have a main branch and a feature branch:

You commit changes A → B on main.
You create feature and commit changes X → Y on feature.
Meanwhile, someone else commits C → D on main.
If you now rebase feature onto main, Git takes the commits X and Y from feature 
and "replays" them on top of the commits A → B → C → D from main, 
making the history look like this:

```
main: A → B → C → D
feature (rebased): A → B → C → D → X → Y
```

#### **Example: Merge History (Without Rebase)**
Let’s assume the same scenario as before:

You have a main branch with commits A and B.
You create a feature branch from main and make commits X and Y on the feature branch.
Meanwhile, new commits C and D are added to the main branch.
Here’s what the branches look like:

```makefile
main:    A → B → C → D
feature: A → B → X → Y
```

Now, if you merge the feature branch into main (without rebasing), 
Git will create a merge commit that combines the histories of both branches. 
This merge commit connects the two branches, creating a point where they come together.

After the merge, the history will look something like this:
```
main:    A → B → C → D → M
                     ↘     ↗
feature:               X → Y
```

Here’s what’s happening:

M is the merge commit created by Git.
The merge commit ties together the changes from main (commits C and D) and feature (commits X and Y).
Notice that:

The history shows a divergence (where feature branch split off from main) and a convergence (where the merge happened).
This results in a non-linear history with a separate branch for feature and an extra merge commit (M).

## When should you use this?

This is just _another_ tool in the tool belt! It is not a common feature but 
something that can be used in certain scenarios.
Just another way to stay organized with Git with a more linear history.

