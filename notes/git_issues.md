## Git Issues

These are common git issues that students run into. Don't forgot to change `username` to your username and `repository` to the repo you're working with!

### Stuck in vi?

You might get stuck in a window that looks like this:

```
Merge https://github.com/username/repository

# Please enter a commit message to explain why this merge is necessary,
# especially if it merges an updated upstream into a topic branch.
#
# Lines starting with '#' will be ignored, and an empty message aborts
# the commit.
~
~
```

This is an editor called `vi`. It is automatically creating a commit for you. All you need to do is exit out of `vi` by pressing: `:q`.

### Repository not found? (Pushing to your repo if you cloned from zipfian)

If you accidentally clone from the zipfian version rather than your fork, you will get the error `Repository not found`. This is a poor error message. What they really mean is that you don't have access to edit the repo. Here's what you can do:

```
git push https://github.com/username1/repository master
```

### Pushing to your partner's github

Here, Partner 1 will refer to the partner who's fork you cloned. Partner 2 is the other partner.

1. Make sure you push to partner 1's github fork.

2. Make sure partner 2 forked the repository.

3. You can use this command to push to their github:

    ```
    git push https://github.com/username2/repository master
    ```

4. It might not let you because you each have a different version of your individual work. You would like to get the work from partner 2's fork. This is a *merge conflict*. We can resolve this by just always choosing partner 2's work when there's a conflict. `ours` would be the strategy of choosing the version that's on the computer (partner 1's) and `theirs` is choosing the version on github. Since we're pulling from partner 2's fork, this is what we want.

    ```
    git pull -X theirs https://github.com/username2/repository master
    git push https://github.com/username2/repository master
    ```

5. If you pulled the normal way, without giving a merge strategy and are told you have a merge conflict, do this first to undo the pull:

    ```
    git reset --hard
    ```

6. If your individual work includes files with different names, you will end up with both of them. This is not a huge deal, but if you'd like to not have your partner's file for the individual exercise, do this:

    ```
    git rm partner1exercise.txt
    git push https://github.com/username2/repository master
    ```

### Stop writing the long `https://github.com/username/repository`

You can make a shortcut to avoid writing this long thing if you're going to be doing it repeatedly. Here's how you can do it:

```
git remote add username https://github.com/username/repository
```

Now you can do:

```
git push username master
```

and

```
git pull username master
```

You can give it any name you want.

You can see all these shortcuts with this command:

```
git remote -v
```
