# Cloning a repository

Developing WheelSims makes heavy use of Git and Git submodules. Since Git is usually complex for newcomers, and having multiple repositories is even more complex, we recommend using a good GUI to stay up to date and ease collaborative development. In these README files, we make use of SourceTree, a free git client for Mac and Windows.

## Configuring SourceTree to recurse in submodules

In SourceTree's preferences, Git pane, tick the box "Perform submodule actions recursively".

![Screenshot 2025-01-29 at 10 37 13](https://github.com/user-attachments/assets/beb813c9-1348-457a-a655-d1a230552728)


## Cloning a toplevel repository

To clone a repository locally with all its submodule, choose `New` → `Clone from URL` and fill these informations (change to the repository name you want to clone):

![Screenshot 2025-01-29 at 10 39 55](https://github.com/user-attachments/assets/55a48b99-8bd7-441e-90d1-f49860a3ad8a)

Once cloned, the project looks like this in SourceTree. Note the submodules pane: double-clicking on a submodule launches a new repository window for this specific repository.

![Screenshot 2025-01-29 at 10 41 15](https://github.com/user-attachments/assets/c3793f8d-5ce4-48e8-be86-d0ee3112959d)

## Staying updated

When someone commits changes to a submodule, open the submodule in SourceTree, ensure that you are on the correct branch (normally, this would be `main`), and **pull** its changes.

If you pulled new changes to the toplevel repository (the one that starts with `sim_`), it is possible that one or many submodules get in **headless state**, which means they are not on a branch anymore. This is a known difficulty with git submodules. To get back this submodule on track:

1. If you have local changes on this submodule, create a new branch (its name is not important, e.g., `temp`). You are not in headless state anymore.
2. Commit your local changes to this new `temp` branch. Your changes cannot be overwritten anymore.
3. Go back on your local `main` branch.
4. **Pull** the changes on `main`. You are now in sync with the latest changes.
5. Merge your `temp` branch in the local `main` branch. You now contributed your code to your local branch.
6. Delete the `temp` branch.

## Committing

In SourceTree, open each submodule and **commit** the changes to commit, if any. Then **push** the changes.

Finally, **commit** the changes to the main repository, and **push** them.
