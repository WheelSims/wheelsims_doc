# Cloning a repository

Developing WheelSims makes heavy use of Git and Git submodules. Since Git is usually complex for newcomers, and having multiple repositories is even more complex, we recommend using a good GUI to stay up to date and ease collaborative development. In these README files, we make use of SourceTree, a free git client for Mac and Windows.

## Configuring SourceTree to recurse in submodules

In SourceTree's preferences, Git pane, tick the box "Perform submodule actions recursively".

![Screen Shot 2024-03-21 at 16 14 23](https://github.com/WheelSims/wheelsims_doc/assets/34967663/47ad5c9c-622d-44c5-8715-bf5c17a2cba4)


## Cloning a toplevel repository

!FIXME These screenshots are not up to date. But we still get the main idea.

To clone a repository locally with all its submodule, choose `New` → `Clone from URL` and fill these informations (change to the repository name you want to clone):

![image](https://github.com/WheelSims/sim_generic_vr/assets/34967663/d9d2e243-29f7-4dea-994a-e5b46fa4fef7)

Once cloned, the project looks like this in SourceTree. Note the submodules pane: double-clicking on a submodule launches a new repository window for this specific repository.

![Screen Shot 2024-02-16 at 09 50 35](https://github.com/WheelSims/.github/assets/34967663/d60469de-92e6-4135-8061-1caa2177867d)

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
