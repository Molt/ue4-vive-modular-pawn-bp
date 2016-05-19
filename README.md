# ue4-vive-modular-pawn-bp
A modular pawn setup and interactivity library for using the [HTC Vive](https://www.htcvive.com/uk/), and it's Motion Controllers, in the Unreal Engine.

**IMPORTANT: This isn't ready for production use yet and so shouldn't really be used..**

## Overview
There are a number of different input approaches used with the HTC Vive motion controller.  This project is to provide a modular system which will allow a pawn to support these approaches, along with a set of utility functions to allow simple implementation of interactive items in the environment.

There are two parallel versions of this project, one using pure Blueprints and one using C++. This is the Blueprint version, the C++ version is available [here](https://github.com/Molt/ue4-vive-modular-pawn-cpp/).

## Current Status
The basic structure now seems sound, and I'm working on implementing all of the interaction models and getting demos working for all of them.

When this is done I'll go through, tidying the Blueprints, and writing the documentation for all of it.

## Interactivity Approaches
The different interactivity mechanisms which are to be supported by the system are:

### Controller Mesh
Indicating the position and rotation of the component by the use of a static mesh component.
* Pretty much every motion controller game ever..

### Gesture Recognition (**Not yet implemented**)
Moving the controller round in a preset gesture to trigger a special event.

* Writing letters in the air, and using text gesture recognition.
* Drawing 'Magical symbols' in the air to cast spells.

**Note: It's possible this may not be supported in the Blueprint version.  Writing a gesture recognition system there doesn't sound like fun.**

### Laser Gun
A special use of *Ray* interaction which allows an easy implementation of beam weapons.

This is actually just done by using the ```OnTriggerPressed``` event with a *Ray* interaction.

* Weapons which travel in straight lines. (Firing lasers in *Space Pirates*)

### Overlap Volume
The controller has a volume attached which triggers events on interactive object.
* Moving the controller near an object and allowing you to move it about (Dragging the drawers about in *The Lab*)
* Acting as a non-physics blocking volume (The shields in *Audioshield*)

### Physics Handle (**Not yet implemented**)
Attaching physics items to the controller so that you can either carry them about.
* Moving, and throwing, props. (Many of the interactions in *Job Simulator*)
* Using both controllers together for greater control over object positioning (The VR editor part of *Unreal Engine 4*)

### Physics Mesh (**Not yet implemented**)
An attached physics-based collision volume allow you to hit physics items in the game environment.
* Hitting baseballs with a bat.
* Pushing over props. (Shoving items around in *Job Simulator*)

### Projectile Gun (**Not yet implemented**)
Firing a projectile from the controller.
* Weapons which are subject to gravity.  (Firing bows in both *Holopoint* and *The Lab*, some of the weapons in *Space Pirate Trainer*)

### Parabolic Ray (**Currently in progress**)
A modified version of *Ray* where instead of using a straight ray the interaction uses a 'drooping' parabolic curve.

This can be useful for *Teleport* as it makes it easier to target areas on the ground.
* Selecting a teleport location. (Choosing targets in *Budget Cuts*)

### Ray
Interacting with elements by firing a 'beam' in the direction of the controller.
* Selecting items from a menu. (The game loader in *SteamVR*, Choosing tools in *TiltBrush*)

### Spatial (**Not yet implemented**)
Using the location and rotation of the controller as raw driving features for an interaction.
* Tracing curves through space (Drawing in *TiltBrush*)


## Interactive Utilities
The following features will be written as helpful functions for implementing interactive elements.

### Damage Actor (**Not yet implemented**)
Applying damage to an item, and destroying it when it takes too much.
* Damaging opponents and targets in 'non-instakill' methods. (Weapon results in *Space Pirates*, *Brookhaven Experiment* or *Arizona Sunshine*)

### Destroy Actor
Destroying an interactive target instantly.  This isn't actually a custom trick as UE4 provides the Destroy Actor Blueprint node.
* Destroying targets which only need one hit. (Simple test targets)
* Editor tools. (Deleting objects in the VR editor for *Unreal Engine 4*)

### Grab Actor (**Not yet implemented**)
Carrying an object round with you using the controller.
* Moving props in a physics-based manner. (Moving props in *Job Simulator*)
* Moving props in a non-physics environment. (Moving props in the VR editor for *Unreal Engine 4*)

### Key Intersection (**Not yet implemented**)
Carry a specific object to a particular place, and having it trigger a reaction automatically.
* Used for key/lock interactions. (Putting a disk in the drive in *Job Simulator*)

### Physics Drag (**Not yet implemented**)
Moving an interactive object round in the environment using physics but without fixing it to the controller.
* Dragging and rotating items in the world. (Opening draws, and rotating components in the Robot Repair portion of *The Lab*)

### Physics Forces (**Not yet implemented**)
Applying forces to objects in the world.

### Menu (**Not yet implemented**)
Using the controller to select options from a standard UI, inserted onto a mesh in the environment.
* Selecting from a fixed-place menu. (The main menu in *StartVR*)
* Selecting from a mobile menu (Choosing tools in *TiltBrush*)

### Scripted Response (**Partly implemented**)
Allowing simple events to be fired in order to allow items to have their own custom behaviors written for them.

### Selection Indicator, Audio (**Not yet implemented**)
Indicating the currently selected objects by making them have spatialized 3d audio cues.

### Selection Indicator, Tinted Decal (**Not yet implemented**)
Mark the location on an interaction by use of a [decal](https://docs.unrealengine.com/latest/INT/Engine/Actors/DecalActor/), which can optionally be coloured to indicate a status.
* Selecting a region on the ground to teleport to (The motion system in *The Lab*)

### Selection Indicator, Generic (**Not yet implemented**)
Methods for indicating currently selected objects, handling both selecting multiple objects with a single controller, and selecting a single object with multiple controllers.

### Selection Indicator, Ghosting (**Not yet implemented**)
Indicating the currently selected objects by making them translucent and ghostly.

### Selection Indicator, Haptic (**Not yet implemented**)
Indicating selections, deselections, and status by using the controller's haptic feedback.

### Selection Indicator, Material Parameter (**Not yet implemented**)
Indicating selections and status by using parameters in [dynamic material instances](https://docs.unrealengine.com/latest/INT/Engine/Rendering/Materials/MaterialInstances/).

### Selection Indicator, Outline (**Not yet implemented**)
Indicating selections by outlining them in a cel-shader like manner.

### Selection Indicator, Light (**Not yet implemented**)
Indicating selections by activating a light at the target location.

### Spawn Actor (**Not yet implemented**)
Allowing events to easy spawn new items.

### Subscriber (**Not yet implemented**)
Allows actors other than the interaction target to be notifed when an interaction occurs.

### Teleport
Moving the player's pawn to the location of the interaction, including basic collision/validity testing both for indication and confirmation.

This can be easily done using existing Blueprint mechanisms by calling ```SetActorLocation``` on the Pawn.

Need to add support for checking the navmesh to make sure the area targetted is actually walkable.

* Moving the player around (Teleport methods in *The Lab*)

### Trigger (**Not yet implemented**)
Events triggered simply by moving the controller into the trigger volume.

## Current Demo Scenes

### 01_RayInteraction
Both controllers fire coloured lines from them, impacts are marked with a sphere mesh.

Spheres lying round the map light up with a controller activates them, and dim when no longer selected.  Pulling the trigger of one Controller will attract the sphere to the player, pulling the other will repel it.

Rings line the corners of the level, one Controller's trigger will turn then clockwise and the other anti-clockwise.

### 02_InputValues
Obtains the input values (Thumbstick, Trigger) for each Controller and uses text components to display them alongside the controller.

Text is coloured based on whether the selected item is beyond it's deadzone or not.

**NOTE: Currently cannot detect the Grip, or whether the thumbstick is actually being pressed**.

### 03_RayTriggerEvents
Both Controllers fire coloured lines, and lining up with one of the blue spheres and pulling the trigger will quickly shrink and destroy the ball.

### 04_OverlapLights
A control board with bright-coloured controls is in front of the player, and the controls light up when a Controller touches them.

Pressing a trigger will cause the control to do a quick rotate animation.

### 05_BasicTeleport
Both Controllers have coloured lines firing from the, and a target decal marking their position on the floor.

Pulling the trigger on a valid piece of floor will teleport the player's pawn to the location.

**Note: Does not check anything about the location other than the ray has hit a floor.  This needs to be extended with navmesh support for proper use**

### 06_RepulsorShield
A cannon fires physics-based projectiles that can be blocked by the Controller, with the collision detection using overlap events rather than physics.

### 07_ParabolicRayInteraction
A verstion of *01_RayInteraction*, but the straight ray is replaced by a parabolic curve.

## To Do
* Track when both controllers are active on an object so the ```On Out``` event doesn't fire the same way.
* Find out how to access the grip and thumbstick press events.
* Navmesh support for teleport checks.
* Implement a 'Path Drawing' set of components to allow the rays/parabola to be drawn in different ways.

# License
The MIT License (MIT)
Copyright (c) 2016, Paul Golds

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
