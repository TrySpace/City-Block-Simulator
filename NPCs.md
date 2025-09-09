# NPCs
NPCs are defined in a list with an ID, their name, gender, home, workplace, and close other profile data.
Their schedule is in a mster NPC schedule file, created based on their personal profile. Each NPC id


## Classes

### Scheduler
Read out current schedule from master NPC schedule file, determines which chronological events to follow at current time.
Handles schedule updates when player interferes, overwrites hardcoded initial master NPC scheduling.


### State
Current NPC states

Basic
- Position
- Vector / Direction
- Moving & Speed

Schedule
- Next Destination
- Last Interaction Cause -- (Player, NPC, Object)-ID & Type of interaction
- Last Cycle Interaction -- Which cycle player interacted

State
- Last Touched/Untouched - Was last interacted with or is following pure schedule, hasn't been interacted with or interfered with by player, other NPCs or objects.
- Physical Condition -- Healthy, Injured
- Mental Condition -- Normal, Startled, Stunned, Scared, Angry

### Profile
Returns response based on personality parameters from master NPC file.
Properties like:
- Name - First & Last name
- Gender - M/F
- Home - Coords of entry
- Workplace - Coords of entry
- Relationships (Lists of, Partner, Friends, Acquaintance)-IDs