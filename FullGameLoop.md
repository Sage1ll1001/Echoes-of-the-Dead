Perfect 🔥
Now we design the **FULL GAME LOOP DIAGRAM** — from launching the game → to death → to restart.

This ensures:

* No missing systems
* Clean state transitions
* No logic conflicts
* Smooth experience for blind players

---

# 🎮 FULL GAME LOOP – *Echoes of the Dead*

---

# 🧭 0️⃣ Game States Overview

Your entire game runs on this state machine:

```text
Main Menu
   ↓
Playing (Normal Mode)
   ↓
Silent Mode (Bird Phase)
   ↓
Playing (Normal Mode)
   ↓
Game Over
   ↓
Main Menu / Restart
```

Everything must move through these states cleanly.

---

# 🏠 1️⃣ MAIN MENU LOOP

### On Launch:

* Narration:
  “Echoes of the Dead.”
* Ambient background sound
* Menu options spoken

### Player Input:

* Arrow keys navigate
* Enter selects

Options:

* Start Game
* Instructions
* Volume Settings
* Exit

---

### Flow:

```text
Highlight Option → Speak Option → Wait for Input → Confirm Sound → Execute
```

If Start Game:

→ Transition to Playing State

---

# 🟢 2️⃣ PLAYING – NORMAL MODE LOOP

This is the core survival loop.

---

## 🔁 Normal Mode Cycle

```text
Spawn Zombie
   ↓
Zombie Moves Toward Player
   ↓
Zombie Makes 3D Sound
   ↓
Player Rotates & Shoots
   ↓
Zombie Dies → +Score
OR
Zombie Reaches Player → Damage
   ↓
Check Player Health
```

---

### System Interactions

* SpawnSystem spawns zombie
* ZombieSystem moves it
* AudioManager plays spatial sound
* PlayerSystem handles shooting
* ScoreManager updates score

---

# 🔕 3️⃣ SILENT MODE TRIGGER

After certain time OR danger threshold:

GameManager triggers:

```text
Enter Silent Mode
```

### Transition:

* Fade out zombie audio (0.5 sec)
* Play subtle tension cue
* Activate BirdSystem

---

# 🐦 4️⃣ SILENT MODE LOOP

This is psychological mode.

---

## 🔁 Silent Cycle

```text
Find Nearest Zombie
   ↓
Calculate Real Direction + Distance
   ↓
Select Active Bird
   ↓
Bird Modifies Info
   ↓
Bird Speaks Direction + Urgency
   ↓
Player Decides & Shoots
   ↓
Zombie Dies OR Player Takes Damage
```

Important:
Only 1 zombie early silent phase.

Later:
Max 2.

---

### End Silent Mode

After silentDuration:

```text
Exit Silent Mode
→ Fade in zombie sounds
→ Return to Normal Mode
```

---

# ❤️ DAMAGE & SURVIVAL LOOP

When zombie reaches attack range:

```text
Play Attack Sound
   ↓
Reduce Player Health
   ↓
Increase Heartbeat Speed
   ↓
Check Health
```

If Health > 0:
Continue loop.

If Health ≤ 0:
Go to Game Over.

---

# 🔥 DIFFICULTY ESCALATION LOOP

Running continuously in background:

```text
Increase dangerLevel over time
   ↓
Reduce spawnInterval
   ↓
Increase zombieSpeed
   ↓
Increase silentChance
   ↓
Unlock more birds
```

This loop runs independent of player actions.

---

# 💀 5️⃣ GAME OVER LOOP

Triggered when health ≤ 0.

---

### Flow:

```text
Stop Zombie Movement
Fade Audio
Play Death Sound
Announce Final Score
Check High Score
```

If new high score:
“New high score.”

Menu options spoken:

* Restart
* Main Menu

---

# 🔁 6️⃣ RESTART FLOW

If Restart:

```text
Reset:
Score
Health
DangerLevel
Zombie List
Bird States
Silent Mode
```

Then:

→ Enter Playing State

---

# 🔄 FULL LOOP DIAGRAM (COMPLETE FLOW)

```text
[Main Menu]
      ↓
[Playing - Normal Mode]
      ↓
Spawn → Move → Shoot → Score/Damage
      ↓
DangerLevel Increases
      ↓
[Silent Mode Trigger]
      ↓
Bird Speaks → Player Shoots → Score/Damage
      ↓
Exit Silent Mode
      ↓
Back to Normal Mode
      ↓
Repeat until Health ≤ 0
      ↓
[Game Over]
      ↓
Restart OR Main Menu
```

---

# 🧠 Micro Loop (Moment-to-Moment Gameplay)

Every 3–6 seconds:

```text
Hear sound →
Identify direction →
Decide trust (bird or instinct) →
Rotate →
Shoot →
Evaluate result
```

This micro loop is what creates tension.

---

# 🎧 Audio Priority Order (During Loop)

If multiple sounds compete:

1️⃣ Zombie Attack
2️⃣ Bird Voice
3️⃣ Gunshot
4️⃣ Zombie Movement
5️⃣ Ambient

Never let important sound get masked.

---

# ⚖️ Emotional Curve Design

Minute 0–1:
Learning, clarity, low stress

Minute 1–2:
Confidence builds

Minute 2–3:
Silent mode appears

Minute 3–4:
Split bird introduced

Minute 4+:
Mimic chaos begins

Confidence → Doubt → Pressure → Mistake → Death

Perfect “Confidently Wrong” arc.

---

# 🏆 Why This Loop Wins Judges

It ensures:

✔ Clear structure
✔ Fair escalation
✔ Learnable deception
✔ No chaotic randomness
✔ Strong tension arc
✔ Replayability

---

# 🎯 Final Design Rule

Every system must answer:

> Does this help the player make a decision?

If not, remove it.

Blind-first design means:
No useless mechanics.

---

If you want next:

* 📅 6-day final execution sprint plan
* 🧪 Blind accessibility testing checklist
* 🏆 Strategy to maximize Judges + Community score
* 🎮 Minimal feature version (MVP for safety)

Tell me what you want next.
