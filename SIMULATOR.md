# Simulator
The player travels back in time at the end of a certain time period, and then is respawned to the start of that time and space. Thus they start a new interation where their past versions of themselves are doing the things again that they did before they traveled back in time.
This creates an endless loop or opportunities where more and more versions of the player are added to the already determined events by the past playthroughs of the set time-period.
The simulator records a deterministic record of events, maintaining pure causality.
Past events cannot be changed, you cannot interact with your past self or with the things your past self has already interacted with.

The simulator consists of:
- A Recording system that records the player movements.
- A NPC scheduling system with deterministic outcomes, but the player can change their predestined outcomes and the simulator records these for replay.
- A playback system that records previous player playthroughs of the same time-period.



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
- Conflicts (e.g., two ghosts interacting with the same object) must be resolved definitively, like via rules like last state wins or priority.

## Ghost Replays as Autonomous Entities
- Each restart of the time-period instantiates a new ghost player entity that runs their respective recorded data like position and their interactions.
- Recorded ghosts cannot be interacted with directly, and their past actions are marked as touched causing the new playthrought to be unable to interact with that thing.
- Recorded ghosts leave behind a bubble-trail of where they have been, which limits the current player's scope of interference. The player can still penetrate the bubble but changes the extent of interactions to avoid incompatible causality with past versions.