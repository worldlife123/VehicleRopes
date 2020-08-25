# VehicleRopes
This is a Squad mod that enables vehicle towing and helicopter sling loading using a physics-base rope component. 

## Description

To connect vehicles with ropes:

1. Find attach points on towing-enabled vehicles. Attach points are marked with 3D icons of a green ammo icon.

2. Approach attach points until you see a "Get Rope!" message. A rope will spawn between you and the attach point. Note that the rope length is 10m by default and you will lose your rope if your distance to the attach point exceeds the rope length.

3. Approach attach points on another towing-enabled vehicle. The rope will automatically attach to the vehicle.

To detach connected vehicle, just approach either attach point.

## Technical Information

### Core Classes

- RopePhysicsComponent: Rope physics. Contains momentum calculation and spring-like force calculation for connected primitive components.
- TowingRopeComponent: Scene Component added to vehicles to imply the position on a vehicle mesh to attach a rope.
- BP_RopeAttachPoint: Spawned by TowingRopeComponent. This actor acts like a trigger to spawn ropes, and has an icon to show the position of attach points to players.
- BP_GenericTowingRope: A CableActor derived rope actor with the rope mesh(CableComponent) and rope physics(RopePhysicsComponent).
- BP_SoldierHeldRope: A CableActor derived rope actor, just display a CableComponent between BP_RopeAttachPoint and the soldier pawn. This type of object will be attached to a soldier as owner with a TowingRopeComponent variable that stored the TowingRopeComponent that spawns it, and BP_RopeAttachPoint will search the triggered soldier's child actors to find another TowingRopeComponent.

### Maps
Currently we've only created a test version on Jensens Range map. 

Mapnames:
- Jensens_Range_v2_ropes

## Usage
Use AdminChangeMap [mapname] to play with Mobile Spawn Vehicles.
