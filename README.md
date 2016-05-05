# ue4-vive-modular-pawn
A modular pawn setup and interactivity library for using the [HTC Vive](https://www.htcvive.com/uk/), and it's Motion Controllers, in the Unreal Engine.

**IMPORTANT: This isn't ready for production use yet and so shouldn't really be used..**

## Overview
There are a number of different input approaches used with the HTC Vive motion controller.  This project is to provide a modular system which will allow a pawn to support these approaches, along with a set of utility functions to allow simple implementation of interactive items in the environment.

Ultimately there are to be two parallel versions, one in pure Blueprint and one using C++ as a base, and each of which will have a series of simple VR demos showing the interactivity principles being implemented.

## Current Status
I'm migrating my existing work over to this repository.

## Interactivity Approaches
The different interactivity mechanisms which are to be supported by the system are:

### Controller Mesh (** Not yet implemented**)
Indicating the position and rotation of the component by the use of a static mesh component.
* Pretty much every motion controller game ever..

### Collision Volume (** Not yet implemented**)
The controller has a volume attached which triggers events on interactive object.
* Moving the controller near an object and allowing you to move it about (Dragging the drawers about in *The Lab*)
* Acting as a non-physics blocking volume (The shields in *Audioshield*)

### Gesture Recognition (** Not yet implemented **)
Moving the controller round in a preset gesture to trigger a special event.
* Writing letters in the air, and using text gesture recognition.
* Drawing 'Magical symbols' in the air to cast spells.

### Laser Gun (**Not yet implemented**)
A special implementation of *Ray* interaction which allows an easy implementation of beam weapons.
* Weapons which travel in straight lines. (Firing lasers in *Space Pirates*)

### Physics Handle (** Not yet implemented**)
Attaching physics items to the controller so that you can either carry them about.
* Moving, and throwing, props. (Many of the interactions in *Job Simulator*)
* Using both controllers together for greater control over object positioning (The VR editor part of *Unreal Engine 4*)

### Physics Mesh (**Not yet implemented**)
An attached physics-based collision volume allow you to hit physics items in the game environment.
* Hitting baseballs with a bat.
* Pushing over props. (Shoving items around in *Job Simulator*)

### Projectile Gun (**Not yet implemented**)
Firing a projectile from the controller.
* Weapons which are subject to gravity.  (Firing bows in both *Holopoint* and *The Lab*)

### Projectile Ray (**Not yet implemented**)
A modified version of *Ray* where instead of using a straight ray the interaction uses a 'drooping' line.  This can be useful for *Teleport* as it makes it easier to target areas on the ground.
* Selecting a teleport location. (Choosing targets in *Budget Cuts*)

### Ray (**Not yet implemented**)
Interacting with elements by firing a 'beam' in the direction of the controller.
* Selecting items from a menu. (The game loader in *SteamVR*, Choosing tools in *TiltBrush*)

### Spatial (**Not yet implemented**)
Using the location and rotation of the controller as raw driving features for an interaction.
* Tracing curves through space (Drawing in *TiltBrush*)

## Interactive Utilities
The following features will be written as helpful functions for implementing interactive elements.

### Damage Actor (** Not yet implemented **)
Applying damage to an item, and destroying it when it takes too much.
* Damaging opponents and targets in 'non-instakill' methods. (Weapon results in *Space Pirates*, *Brookhaven Experiment* or *Arizona Sunshine*)

### Destroy Actor (** Not yet implemented **)
Destroying an interactive target instantly.
* Destroying targets which only need one hit. (Simple test targets)
* Editor tools. (Deleting objects in the VR editor for *Unreal Engine 4*)

### Grab Actor (** Not yet implemented **)
Carrying an object round with you using the controller.
* Moving props in a physics-based manner. (Moving props in *Job Simulator*)
* Moving props in a non-physics environment. (Moving props in the VR editor for *Unreal Engine 4*)

### Key Intersection (** Not yet implemented **)
Carry a specific object to a particular place, and having it trigger a reaction automatically.
* Used for key/lock interactions. (Putting a disk in the drive in *Job Simulator*)

### Physics Drag (** Not yet implemented **)
Moving an interactive object round in the environment using physics but without fixing it to the controller.
* Dragging and rotating items in the world. (Opening draws, and rotating components in the Robot Repair portion of *The Lab*)

### Physics Forces (** Not yet implemented **)
Applying forces to objects in the world.

### Menu (**Not yet implemented**)
Using the controller to select options from a standard UI, inserted onto a mesh in the environment.
* Selecting from a fixed-place menu. (The main menu in *StartVR*)
* Selecting from a mobile menu (Choosing tools in *TiltBrush*)

### Scripted Response (** Not yet implemented **)
Allowing simple events to be fired in order to allow items to have their own custom behaviors written for them.

### Selection Indicator, Audio (** Not yet implemented**)
Indicating the currently selected objects by making them have spatialized 3d audio cues.

### Selection Indicator, Generic (** Not yet implemented **)
Methods for indicating currently selected objects, handling both selecting multiple objects with a single controller, and selecting a single object with multiple controllers.

### Selection Indicator, Ghosting (**Not yet implemented**)
Indicating the currently selected objects by making them translucent and ghostly.

### Selection Indicator, Haptic (** Not yet implemented**)
Indicating selections, deselections, and status by using the controller's haptic feedback.

### Selection Indicator, Material Parameter (** Not yet implemented**)
Indicating selections and status by using parameters in [dynamic material instances](https://docs.unrealengine.com/latest/INT/Engine/Rendering/Materials/MaterialInstances/).

### Selection Indicator, Outline (**Not yet implemented**)
Indicating selections by outlining them in a cel-shader like manner.

### Selection Indicator, Light (** Not yet implemented**)
Indicating selections by activating a light at the target location.

### Spawn Actor (** Not yet implemented **)
Allowing events to easy spawn new items.

### Subscriber (** Not yet implemented **)
Allows actors other than the interaction target to be notifed when an interaction occurs.

### Teleport (** Not yet implemented**)
Moving the player's pawn to the location of the interaction, including basic collision/validity testing both for indication and confirmation.
* Moving the player around (Teleport methods in *The Lab*)
 
### Trigger (** Not yet implemented**)
Events triggered simply by moving the controller into the trigger volume.

## License
The MIT License (MIT)
Copyright (c) 2016, Paul Golds

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
