# Developing new playable scenes

For a scene to be selectable and playable in the user interface, it needs to:
- Include the player object;
- Be saved into the `res://playable_scenes` folder;
- Optionally, include a screenshot as a PNG image with the same name, in the same folder.

## Creating the playable scene in Godot

We close all scenes and we create a new 3D Scene:

![](images/developing_new_terrains_create_3d_scene.png)

Then, we drag both the player and environment we want to navigate into the new 3D Scene. We give it a short name (no need to add `scene` at the end as with `terrain` or `environment`, since this is the entry point in the user interface. Here, we create a playable scene from the `irglm_4th_floor_environment.tscn` that we build [previously](developing_new_environments.md), and we save it as `res://playable_scenes/irglm_4th_floor.tscn`.

From this point, we can launch the user interface and the scene will appear with every other available scenes in the scene list. However it won't have a thumbnail yet. To generate this thumbnail, we navigate to a visually interesting point of view, make a screenshot and save it with the same name, as `res://playable_scenes/irglm_4th_floor.png`.

The scene is now playable and fully part of the user interface.
