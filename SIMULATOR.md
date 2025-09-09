# Simulator
Player is ethereal and cannot directly interact with physical objects or NPCs, only through specific acquired skills can they interact.
The player travels back in time at the end of a certain time period, and then is respawned to the start of that time and space. Thus they start a new interation where their past versions of themselves are doing the things again that they did before they traveled back in time.
This creates an endless loop or opportunities where more and more versions of the player are added to the already determined events by the past playthroughs of the set time-period.
The simulator records a deterministic record of events, maintaining pure causality.
Past events cannot be changed by default, you cannot interact with your past self or with the things your past self has already interacted with.
You can only potentially change a past action when a simple reconcilliation would correct that past version, but if the cascading consequences are too big, it is not possible.

The simulator consists of:
- A Recording system that records the player movements.
- A NPC scheduling system with deterministic outcomes, but the player can change their predestined outcomes and the simulator records these for replay.
- A playback system that records previous player playthroughs of the same time-period.

## Gameplay Emergence
Cooperative self-chaining: set up objects that your future iterations can use.


## State Recording
Record all relevant state each frame or at fixed intervals per playable and interactive object:
- Player Transforms (position, rotation)
- Object Physics states (velocity, forces, vectors)
- Interaction states (doors opened, items picked up)
- NPC schedule state and player interactions that modify it

## Semi-Deterministic NPC Scheduler
- Supports multiple overlapping playbacks of player influencing the world.
  - Simulation logic is deterministic unless interfered with explicitly by player, or by and indirect action the player initiated.
- Each "ghost" playback acts as an active agent updating the world through recorded inputs/states.
- Conflicts (e.g., two ghosts interacting with the same object) are resolved definitively, like via rules like last state persists:
  - For booleans like lightswitch: state reflects whatever player set it to (no toggle)
  - For a button like a dispenser: objects are dispensed at whatever time they are pressed
  - When an object was already collected, it cannot be collected again.
- NPC can react to certain events that the player caused to change their pathing or scheduling altogether, causing in some cases cascading consequences that are played out in real-time.

## Ghost Replays as Autonomous Entities
- Each restart of the time-period instantiates a new ghost player entity that runs their respective recorded data like position and their interactions.
- Recorded ghosts cannot be interacted with directly, and their past actions are marked as touched causing the new playthrought to be unable to interact with that thing.
- Recorded ghosts leave behind a bubble-trail of where they have been, which limits the current player's scope of interference. The player can still penetrate the bubble but changes the extent of interactions to avoid incompatible causality with past versions.