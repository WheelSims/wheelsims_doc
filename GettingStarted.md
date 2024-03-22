[Home](.)

# Getting Started

The WheelSims project is a set of blocks distributed on different repositories, that can be shared among wheelchair simulators to accelerate the development of virtual reality in wheelchair training.

Since `git` is already complex for newcomers, having multiple repositories is yet more complex. For this reason, we recommend to use a good GUI to stay up to date and ease collaborative development. In these README files, we make use of [SourceTree](https://www.sourcetreeapp.com/), a free `git` client for Mac and Windows.


## Configuring SourceTree to recurse in submodules

In SourceTree's preferences, Git pane, tick the box "Perform submodule actions recursively".

![Screen Shot 2024-03-21 at 16 14 23](https://github.com/WheelSims/wheelsims_doc/assets/34967663/47ad5c9c-622d-44c5-8715-bf5c17a2cba4)


## Toplevel repositories

Only the repositories that start by `sim` are toplevel repositories and are meant to be cloned. The others are submodules. Currently, we have:

- `sim_generic_vr` : A generic Unity project that contains every Unity element available for the simulators. Use this repository to develop virtual reality material that is not related to one given simulator.
- `sim_irglm_vr` : The IRGLM simulator. It contains every submodules of `sim_generic_vr`, but will also contain other elements such as Matlab/Simulink stuff for the electromechanical components.
- Others to come.

## Cloning a repository

To clone a repository locally with all its submodule, choose `New` → `Clone from URL` and fill these informations (change to the repository name you want to clone):

![image](https://github.com/WheelSims/sim_generic_vr/assets/34967663/d9d2e243-29f7-4dea-994a-e5b46fa4fef7)

Once cloned, the project looks like this in SourceTree. Note the submodules pane: double-clicking on a submodule launches a new repository window for this specific repository.

![Screen Shot 2024-02-16 at 09 50 35](https://github.com/WheelSims/.github/assets/34967663/d60469de-92e6-4135-8061-1caa2177867d)

## Staying updated

When someone commits changes to a submodule, open the submodule in SourceTree, ensure that you are on the correct branch (normally, this would be `main`), and **pull** its changes.

If you pulled new changes to the toplevel repository (the one that starts with `sim_`), it is possible that one or many subrepositories are not on a branch anymore (they would be in headless state). This is a known difficulty with git submodules. To get back this submodule on track:

1. If you have local changes on this submodule, create a new branch (its name is not important, e.g., `temp`). You are not in headless state anymore.
2. Commit your local changes to this new `temp` branch.
3. Go back on the local `main` branch.
4. **Pull** the changes on `main`.
5. Merge your `temp` branch in the local `main` branch.
6. Delete the `temp` branch.

## Editing

When working on the game, one must make sure that the new files (scripts, textures, etc.) added to a scene are placed in the correct folder, so that they will be added to the right repository.

## Committing

In SourceTree, open each submodule and **commit** the changes to commit, if any. Then **push** the changes.

Finally, **commit** the changes to the main repository, then **push** them.
