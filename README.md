# Quantum Mirror

A puzzle game for university course that implements basic ideas of quantum physics and superpositions.

Game is developed solo without a team.

## About the Game 

### Core Concept

**Quantum Mirror** is a level based 2d puzzle platformer that uses superposition as the core element of the gameplay.

The screen is split into 2 parts, each showing the same level with small deviations. Player's goal is to reach the exit while using quantum gates X, Z and H as a resource through out, but gates usages are limited and can be replenished by finding and collecting representations of gates in the level.

### Quantum Game mechanics

This game implements a **simplified state-based model inspired by single-qubit quantum mechanics** with a small bias to make it more playable:

- Superposition: This is a state system acting as a qubit. Reflected as same level being mirrored with some deviations and shown on the lower part of the screen. 
  - |0\mirrored> means single instance exists in the upper version of the level.
  - |1\mirrored> means single instance exists in the lower version of the level.
  - |+> represents a superposition where the two manifestations have positive relative phase. For gameplay purposes, this corresponds to the |0> exit phase.
  - |−> represents a superposition where the two manifestations have negative relative phase. For gameplay purposes, this corresponds to the |1> exit phase.

- Z, X, H Gates: Used as state and phase changers same as quantum physics. Those gates initially are not available for player's use, but their representation can be collected and later used to complete the level.

- Measurement & Collapse: The game uses an intentionally simplified interpretation of measurement. Certain in-game objects are treated as observers and cause the game state to collapse when they interact with the player's quantum state. This is a gameplay abstraction rather than a physically accurate simulation of quantum measurement.

- Entanglement: Although multiple manifestations may appear on screen, they represent a single underlying player entity. When in superposition, player input is applied to all manifestations simultaneously, while their coordinates may differ due to interactions with the environment. Additionally when an observer measures a superposition, both manifestations are removed and the underlying state collapses into one of the two basis states controlled by initial entered state and Z gate usage.

How it goes beyond classical probabilistical model:

- Superposition allows simultaneous exploration and interaction of the both level instances.
- Controlled measurement, gates triggering and phase manipulation can give deterministic results, not just complete randomness.
- Correlation between player instances allows puzzle mechanics that cannot be achieved with independent random events.

### Game Mechanics and rules

- Regular platforming movement, that includes moving left and right as well as jumping. If player's character is in superposition, then player controls both instances simultaneously. 
- Doors that can be unlocked by powering them on.
- Pressure plates that can be activated to power doors.
- Small inventory like system that allows to pick up and use gates.
- Gates usage:
  - H gate: initially splits player into 2 instances one in each level version, thus entering superposition. Using gate again collapses instances resulting in a single instance exiting in its entering phase (H|0> = |+>; H|+> = |0>) unless underlying phase wasn't changed with Z gate.
  - Z gate: swap phase (exit state) of player in superposition.
  - X gate: swaps the player's basis state while outside superposition, allowing the player to travel between the two level versions.
- Hazards such as spikes can damage or kill the player's manifestation. If the underlying player entity is killed, the level restarts.
- Certain objects, such as surveillance cameras, act as measurement devices and cause the player's quantum state to collapse.

### Winning and Losing Conditions

Goal of each level is to reach the end. If exit exists in both versions of the level, both instances must reach the exit trigger, whilst if only a single version of the level has an exit, than player's character must exit superposition in the correct phase before reaching the exit trigger.

If destination is not reachable any more and/or player's character is killed (e.g. fallen into spikes) then it counts as a loss and level restarts.

## Platform and Development tools

**Platform:** PC/Desktop (Windows and Linux)

### Development Tools

**Game Engine:** Godot

**Programming Language:** GDScript (Godot's built-in scripting language)

**Tool for Art Assets:** Aseprite
