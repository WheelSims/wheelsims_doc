# Software overview

The project uses a git-based versioning system, with heavy use of git submodules. All toplevel repositories start with `sim_`:

- [`sim_generic`](https://github.com/WheelSims/sim_generic): A generic repository not tied to specific hardware. This "simulator" includes every available submodule and is mainly for testing and developing the submodules.
- [`sim_irglm`](https://github.com/WheelSims/sim_irglm): The IRGLM high-realism simulator.
- [`sim_racing`](https://github.com/WheelSims/sim_racing): A wheelchair racing simulator with user-power biofeedback.

New simulators normally use [`sim_generic`](https://github.com/WheelSims/sim_generic) as a template, which folder/submodule hierarchy is presented below.

```
sim_generic
+-- Unity
|   +-- Assets
|   |   +-- vr_assets_common   # A git submodule that includes all shared objects and scripts, from the smallest object to whole environments, available as drag-drop prefabs.
|   |   |   +-- Environments   # A folder that include prefabs of complete navigable environments, including pedestrians and cars, to be imported into a scene.
|   |   |   +-- Objects        # A folder that include the available objects and prefabs to create environments.
|   |   |
|   |   +-- Scenes             # A folder that includes the specific scenes for a given simulator. A scene normally consists in at least an environment from vr_assets_common, and a user from the User folder.
|   |   +-- User               # A folder that includes a set of colliders, cameras and scripts that represents the user. It also includes the scripts to communicate with the haptics system (if present), the incline system (if present), and other instruments.
|   |
|   +-- vr_art_source          # A git submodule of construction material for the assets and scenes, such as Blender files. Texture images are stored in vr_assets_common, not here.
|   +-- ...
|
+-- Haptics
|   +-- haptics_common         # A git submodule of Simulink blocks that are shared between simulators, such as the dynamical model of a wheelchair, motor controllers, etc.
|   +-- ...
|
+-- ...
```

## Links to the git submodules:

- [`vr_assets_common`](https://github.com/WheelSims/vr_assets_common)
- [`vr_art_source`](https://github.com/WheelSims/vr_art_source)
- [`haptics_common`](https://github.com/WheelSims/haptics_common)

