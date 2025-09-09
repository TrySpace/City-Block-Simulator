
# Core Components
Game Manager - Manages main simulation loop, schedules deterministic steps
Replay Manager -	Stores initial game state, records & replays inputs for each playthrough
Input Recorder - Captures player input (frame by frame)
Ghost Controller - Plays back past inputs as autonomous ghost players
Game State Manager - Applies deterministic updates and enforces immutable past states (bubbles)


# State Recording System
Player state recording is precise, while general NPC schedule is predetermined and can be interpolated when precise location is needed, or when NPC schedule is interfered with, a more precise record is kept of specific responses and new pathing or scheduling.
- Player state: transform (position, rotation), current animation, velocity, held items.
- Objects: physics state (rigidbody position/velocity), toggled states (doors, switches, etc.).
- NPCs: global schedule clock, current position, state machine state (walking to target, idling, sleeping).
- Interactions: specific one-off events, e.g., "player pulled lever at t=125.4s.", or "NPC tripped over rake at t=123s"


# NPC response to interference
- An interference in an NPCs schedule triggers a response according to the type or severity of interference. If they are startled or distracted, their schedule is simply slightly delayed, having minimal impact on their further actions and schedule. But getting injured could have a modifying impact on their schedule, instead of going (back) to work they will go home or call the hospital etc.
- Each interference is recorded and overwrites the predetermined schedule