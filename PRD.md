Alright 🔥
Here is your **copy-ready PRD** for the jam submission.

---

# 📄 PRODUCT REQUIREMENTS DOCUMENT (PRD)

## Game Title (Working)

**Echoes of the Dead**

---

## 1. Overview

**Echoes of the Dead** is a high-pressure, audio-based survival game designed for blind and sighted players.

The player is a blind survivor in a zombie apocalypse who relies entirely on sound to detect and eliminate approaching threats.

When zombies suddenly go silent, four mysterious birds begin giving directional hints — but not all of them are truthful.

The game is built for submission to **Games for Blind Gamers Jam 5 (2026)**.

---

## 2. Objectives

### Primary Goal

Create a fully blind-accessible, audio-first survival game that:

* Can be played without visuals
* Is tense and high-score driven
* Encourages pattern recognition and strategic thinking

### Secondary Goal

Align with optional theme:
**“Confidently Wrong”**

* Player often trusts the wrong bird.
* Overconfidence leads to failure.

---

## 3. Target Audience

### Primary

* Blind gamers
* Low-vision players

### Secondary

* Sighted players interested in accessibility
* Audio-game enthusiasts
* Jam community voters

---

## 4. Platform

* Windows Build (Required)
* Web Build (Optional if feasible)
* Developed in Unity

---

## 5. Core Gameplay Loop

1. Zombies spawn around the player (360° space).
2. Player detects them using 3D spatial audio.
3. After a time threshold, zombies go silent.
4. Birds begin giving directional hints.
5. Player rotates and shoots.
6. If correct → zombie killed → score increases.
7. If wrong → zombie damages player.
8. Difficulty gradually increases.

---

## 6. Core Mechanics

### 6.1 Player Mechanics

* Rotate Left / Right
* Shoot
* Reload
* Sound Pulse Ability (optional)
* Health System
* Ammo System

---

### 6.2 Zombie Behavior

Phase 1 – Audible Mode

* Footsteps
* Growls
* Distance-based volume

Phase 2 – Silent Mode

* No zombie audio
* Only birds provide information
* Higher tension

---

## 7. The Four Bird System

Each bird speaks one at a time during Silent Mode.

### Bird 1 – Truth Seeker

* Always gives correct direction.

Example:
"Zombie on your left."

---

### Bird 2 – Inverter

* Always gives opposite direction.

If zombie is right → says left.

---

### Bird 3 – Splitter

* Half true, half false.
  Options:
* Correct direction, wrong distance
  OR
* Wrong direction, correct urgency

---

### Bird 4 – Mimic

* Copies one of the other birds randomly.
* Changes behavior each round.

---

## 8. Accessibility Requirements

### 8.1 Mandatory

* Full gameplay possible with monitor off
* All menus narrated
* No reliance on visual UI
* Clear stereo 3D spatial audio
* Distinct bird voice tones
* Clear weapon audio feedback
* Damage indication via heartbeat sound

---

### 8.2 Menu Accessibility

Keyboard-only navigation:

* Arrow keys → Navigate
* Enter → Select
* Escape → Back

Each menu item must:

* Speak its label when highlighted
* Confirm selection audibly

Example:
“Start Game”
“Instructions”
“Volume Settings”
“Exit”

---

## 9. Controls (Keyboard)

* A → Rotate Left
* D → Rotate Right
* W → Shoot
* S → Reload
* Space → Sound Pulse (optional)
* Esc → Pause

---

## 10. Audio Design Requirements

### 10.1 3D Spatial Audio

* Zombies use Unity 3D audio (Spatial Blend = 1)
* Volume scales with distance
* Left/right ear separation must be clear

---

### 10.2 Distance Layers

Far → Low volume + light reverb
Medium → Clear footsteps
Close → Heavy breathing + attack warning

---

### 10.3 Feedback Sounds

* Gunshot sound
* Empty magazine click
* Reload sound
* Zombie death sound
* Damage heartbeat
* Low health warning tone

---

## 11. Scoring System

* +1 per zombie kill
* Combo bonus for quick kills
* Survival time multiplier
* Accuracy bonus (optional)

Leaderboard:

* High score stored locally

---

## 12. Difficulty Scaling

As score increases:

* Zombie spawn rate increases
* Silent mode activates faster
* Multiple zombies at once
* Bird speaking speed increases
* Ammo becomes more limited

---

## 13. Game Modes (Optional Stretch)

### Classic Mode

Standard survival

### Chaos Mode

Bird personalities switch more frequently

---

## 14. Technical Requirements (Unity)

### Systems Needed

* Audio Manager
* Bird Logic System
* Zombie Spawn Manager
* Player Rotation Controller
* High Score Manager
* Accessible Menu System

---

## 15. UI Policy

Visual UI allowed for sighted players BUT:

* Must not be required to play.
* All information must be duplicated via audio.

---

## 16. Win / Lose Conditions

Lose:

* Health reaches zero

Win:

* Endless mode (high score focus)

---

## 17. Monetization

None (Jam Submission)

---

## 18. Risks

* Over-randomization may feel unfair
* Audio clutter if too many sounds overlap
* Birds must be clearly distinguishable
* Difficulty must scale fairly

---

## 19. Success Metrics

* Fully playable by blind tester
* Clear differentiation between birds
* High replayability
* Strong immersion
* Positive feedback from blind judges

---

## 20. Development Timeline (6 Days Remaining)

Day 1 – Core shooting + rotation + 3D audio
Day 2 – Zombie spawn + distance scaling
Day 3 – Bird system logic
Day 4 – Silent mode + balancing
Day 5 – Accessible menu + narration
Day 6 – Polish + testing with eyes closed

---

# Final Vision Statement

Echoes of the Dead is a tense, audio-first survival experience where trust is dangerous, confidence is fragile, and listening is the only way to survive.

In a world without sight, certainty can kill you.

---

If you want next:

* 🎮 Full Unity architecture breakdown
* 🧠 Bird logic pseudocode
* 🔊 Audio layering blueprint
* 🏆 Strategy to win Judges Choice

Tell me and we’ll build it properly.
