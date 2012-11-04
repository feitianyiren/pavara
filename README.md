pavara
======

A game inspired by the classic Mac game.

* * *
how to install dependencies
===========================

Pavara depends on Panda3D which can be downloaded here: http://www.panda3d.org/download.php?sdk&version=1.8.0

For Windows: http://www.panda3d.org/download/panda3d-1.8.0/Panda3D-1.8.0.exe

For Macs: http://www.panda3d.org/download/panda3d-1.8.0/Panda3D-1.8.0.dmg

Mac users also need: https://developer.nvidia.com/cg-toolkit

For Ubuntu: http://www.panda3d.org/download.php?platform=ubuntu&version=1.8.0&sdk

For Ubuntu 12.04, you can install the oneiric version, but it will complain about 2 unmet dependencies.

You can download those dependencies from here: http://packages.ubuntu.com/oneiric/allpackages. Then it will install.

running it
==========

Windows: navigate to the source code directory with cmd and run ppython map_test.py

Macs: navigate to the source code directory in a terminal and run ppython map_test.py

Linux: navigate to the source code directory in a terminal and run python map_test.py

* * *
roadmap
=======

Maps
----
###high priority
*   **legacy map converter**
	*   add conversion for
		*   domes
		*   rounded rects
		*	fields
		*	walldoors
		*	goodies
		*	teleporters
		*	etc.

###low priority
*	**map loading**
	*	honor yaw/pitch/roll attributes for all objects, not just blocks
*   **map syntax**
	*   need definitions/implementation for
		*   per-level logic/scripting
		*	assign ids to objects for scripting
		*	assign mass to objects to make freeSolids
		*   fields/areas
		*   goodies
		*   custom shapes

Graphics
--------
###high priority
*   **walking animation**
	*	use `LerpInterval`s to move hector model rigging
	*	work with colliision character to stop feet on terrain

###low priority
*	**multiple colors for models**
	*	Avara could only allow you to override two colors on a model, using the arc fill and line colors in cw4. No need for this limitation anymore, but how should we assign these multiple color values via the XML?
		*	Single color attribute, containing multiple colors?
		*	Multiple color attributes, with an another arbitrary limit on color "slots"?
		*	What about alpha? Set per color, or per object?
	*	look at geom group naming with `egg-optchar`
	*	see https://www.panda3d.org/manual/index.php/Egg_Syntax
	*	also see https://www.panda3d.org/manual/index.php/Manipulating_a_Piece_of_a_Model
*   **updated assets**
    *   walker(s) (export bobski's model)
	*   missile/grenade/plasma
	*   unigoody
*   **shadows**
    *   directional soft shadow mapping
*   **particle effects**
	*	explosions
	*	missle/lazer trails
	*	environmental, e.g. precipitation?

Networking
----------
###high priority
*   **game object distribution and sync**

###low priority
*   **server tracking**
*   **game metadata distribution (chat/level and asset distribution)**

Logic
-----
*	**player data**
	*	shield/plasma recharge rates based on energy level
	*	ammo and boosters
	*	respawns
	*	incarnator selection
		*	random order, unless order attribute explicitly set on incarnator objects
		*	if multiple incarnators exist with same order value, select randomly within that subset
		*	do allow for team masking
		*	if number of players exceeds the number of incarnators, split players into "batches" and spawn them in ten second waves?
	*	position, speed, velocity
*	**game data**: setup, types, start/end conditions
*	**messages**: triggering and listening for simple events, both in XML and whatever scripting set up we use

Sound
-----
###low priority
*	**doppler effect/stereo positioned playback**
*	**updated assets**
	*	plasma/missle/grenade loop
	*	kArticWind etc. replacements
	*	footstep sounds, goody sounds
	*	incarnator and teleporter sounds
	*	xplosions

Physics (ODE)
-------
###higher priority
*	**kinematic character controller**
	*	apply forces after physics tick for movement
	*	keep collision shape upright
	*	send messages to hector object for animation
	*	update position and rotation of hector object
*	**ballistics**
	*	grenade lobbing
	*	"smart" missle tracking
	*	lazers
	*	damage

###lower priority
*	**other collidables**
	*	goodies
	*	fields/areas
	*	kinematic map objects

User Interface
--------------
###lowest priority
*	**preliminary designs**
