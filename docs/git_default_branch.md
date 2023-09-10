# How to change your default branch in git

Q. Why should I change my default, I'm okay with the current name.
A. It's true that you are ok with the current name. By changing the name you can explore other names (e.g your name) to better fit your `brand'

## What is a branch in git

In git, a branch is like the 'reality' that your code lives in.
If you have used git, you would have come across branches.
The most common branch names are `master` and `main`.
This in most times are labelled as `default branch` in github.

It is not a must that the `default branch` be named between the two names.

## How to change a git branch name

You can change any git branch name by using `git branch -m <old name> <new name>`.
If you are on the branch you are trying to change you can simply run `git branch -m <new name>`

## Set a certain name as the default

To set a default branch name you can run:

```bash
git config --global init.defaultBranch branch_name # Replace branch_name with your preferred name
```

This will set the default branch globally.
You can check out the announcement here on introduction of `init.defaultBranch` <https://github.blog/2020-07-27-highlights-from-git-2-28/>
