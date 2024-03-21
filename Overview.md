---
id: Overview
title: Overview
---
# Overview

The WheelSims system combines:

- haptics - so that the user feels realistic forces at the wheels
- virtual reality - so that the user feels where they navigate
- an incline platform - so that the user feels the difference between ascending, descending or crossing a slope.

These three systems are independent. For example, it is not required to have an haptic system to navigate in virtual reality. They are complementary, they add realism to the simulation.

This figure illustrates the data flow between the different systems:


```mermaid
flowchart TD

force_sensor["<b>Force Sensor</b><br/>(AMTI force cell)"]
haptics["<b>Haptics System</b><br/>(Simulink Real-Time)"]
unity["<b>Virtual Reality System</b><br/>(Unity3D)"]
motors["<b>Motors</b><br/>(attached to rollers)"]
rollers["<b>Rollers</b>"]
projectors["<b>Projectors</b>"]
dbox["<b>Incline platform</b><br/>(D-Box System)"]

force_sensor -->|Force| haptics
haptics -->|Torque command| motors
motors --> rollers
rollers -->|Speed| haptics
rollers -->|Speed| unity
unity -->|Visual| projectors
unity -->|Incline| dbox
unity -->|Rolling Resistance| haptics

```


The project uses a git-based versioning system, with heavy use of git submodules. Any simulator is derived from the `sim_generic` repository, which is a toplevel repository that includes every available submodule. The folder/submodule hierarchy in this repository is:

```mermaid
flowchart LR

sim_generic["sim_generic<br/>(main repository)"]

unity("Unity<br/>(folder)")
assets("Assets<br/>(folder)")
unity2("Library<br/>(folder)")
unity3("Packages<br/>(folder)")
unity4("etc.")

vr_scenes["vr_scenes<br/>(git submodule)"]
vr_static_objects["vr_static_objects<br/>(git submodule)"]
vr_dynamic_objects["vr_dynamic_objects<br/>(git submodule)"]
vr_street_lights["vr_street_lights<br/>(git submodule)"]
vr_user["vr_user<br/>(git submodule)"]
vr_art_src["vr_art_src<br/>(git submodule)"]

haptics("Haptics<br/>(folder)")

haptics_common["haptics_common<br/>(git submodule)"]


sim_generic --> unity
unity --> assets
unity --> vr_art_src
unity --> unity2
unity --> unity3
unity --> unity4

assets --> vr_scenes
assets --> vr_static_objects
assets --> vr_dynamic_objects
assets --> vr_street_lights
assets --> vr_user


sim_generic --> haptics

haptics --> haptics_common


```
with:

- `Unity` folder: The Unity project to open in Unity Hub. Apart from the git submodules, the contents of this folder is specific to this simulator.
- `Assets` folder: A folder that contains the asset submodules, shared between every simulators.
- `vr_scenes` submodule: An asset submodule that includes all available scenes.
- `vr_static_objects` submodule: An asset submodule that includes static objects such as bins, trees, building facades, etc.
- `vr_dynamic_objects` submodule: An asset submodule that includes dynamic objects such as pedestrians and cars.
- `vr_street_lights` submodule: An asset submodule that includes automated, configurable street lights, streets and sidewalks.
- `vr_user` submodule: An asset submodule that includes a set of colliders, cameras and scripts that represents the user in its environment. This also includes code to communicate with the haptics system (if present) and the incline system (if present).
- `vr_art_src` submodule: A repository of construction material for the assets and scenes, such as Blender files.
- `Haptics` folder: A folder that contains the Simulink Real-Time material for the haptics system. Apart from the git submodule, the contents of this folder is specific to this simulator.
- `haptics_common` submodule: A submodule of Simulink blocks that are shared between simulators, such as the dynamical model of a wheelchair, motor controllers, etc.

