# Unity Conventions

Note: These conventions are currently being written and are dynamic. The project is progressively converging to these conventions as they are written.

## File Naming

- All files and folders are PascalCase, e.g., LindsayRamp.prefab, IRLMG4thFloor.fbx. One exception is for git submodule folders, which are underscored_cased, e.g., vr_assets_common

## Environments and objects

At the toplevel of the `vr_assets_common` are two folders:

### Environments

This folder only contains prefabs that are complete environments to be imported as is in scenes.

### Objects

This folder contains all the material to create the environments, or to create more complex objects. It follows this arborescence:

```
+ ObjectGroup
    |
    +-- ObjectPrefab1.prefab  <-- One object
    +-- ObjectPrefab2.prefab  <-- Another object
    +-- ...
    +-- Art              <-- Contains the meshes, materials and textures
    |     |
    |     +-- FBX        <-- FBX that contains all materials
    |     +-- Textures   <-- Texture files (jpg, png) referenced by the model
    |     +-- Materials  <-- (optional) Only if the materials are not part of the FBX
    |
    +-- Scenes           <-- (optional) Contains test scenes for these objects
    +-- Scripts          <-- (optional) Contains all the scripts for these objects
```

We always use the prefabs to instance objects, not the FBX files. This is important for different reasons:
- It allows separating the interface of the object (the prefab, which should normally stay available) and its implementation (the meshes and materials, which could completely change in subsequent versions).
- It allows adding scripts to it in subsequent versions, so that an initially static object could eventually become dynamic.

## Creating visual arts

###  Creating the object

Blender is preferred for art creation as it is open-source. Source for visual art (e.g., blend files) should be hosted in the `vr_art_source` repository. A single Blender file can inclure many related assets, especially if they share common resources. For instance, multiple sport items (cones, balls, flags) could be designed in a Sports.blend file, where each element is in its own collection.

Since materials are imported in Unity, then material names are important. For clarity, prefix material names with the object group name, for instance: SportsBasketBall, SportsCone, etc. If the material is based on a texture, the texture must be named the same as the material (e.g., SportsBasketBall.jpg). Do not save the texture images on `vr_art_source`, they belong to the `vr_assets_common` repository (as explained below).

### Exporting the object

Once an object has been designed in Blender, it must be exported as an FBX file. All FBX files must be oriented with the `y` axis upward, so that it does not need to be rotated afterward in Unity. To ensure this in Blender, in the FBX export window, use the following configuration:

- Limit to [X] Selected Objects
- Transform: Scale: 1.00
- Transform: Apply scaling: All Local
- Transform: Forward: -Z Forward
- Transform: Up: Y Up
- Transform: [X] Apply Unit
- Transform: [X] Use Space Transform
- Transform: [X] Apply Transform.

The FBX file must be saved in its corresponding `FBX` folder in the `vr_assets_common` repository, and its texture image (if any) must be saved in its corresponding `Textures` folder on the `vr_assets_common` repository.

### Making a prefab

FBX files are not imported directly in environments and scenes. Prefabs are. Therefore, before using this new object, a prefab must be made for it. In the project arborescence, create an empty object, rename it as the object name (usually the same name as the FBX file), drag the FBX to it, and then drag the empty to the object group folder. The empty is now a prefab that can be used anywhere.
