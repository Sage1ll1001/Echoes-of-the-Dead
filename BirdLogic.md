Perfect.
This is the **brain of your game**. If Bird Logic is weak → game feels unfair.
If Bird Logic is clean → judges will LOVE it.

Let’s design this properly.

---

# 🐦 BIRD LOGIC SYSTEM

For **Echoes of the Dead**

---

# 🎯 Design Goals

Bird system must:

* ✔ Be consistent (not pure random chaos)
* ✔ Be learnable
* ✔ Feel tricky but fair
* ✔ Support “Confidently Wrong” theme
* ✔ Work fully via audio

---

# 🧠 Core Concept

When Silent Mode activates:

1. Find nearest zombie.
2. Calculate real direction relative to player.
3. Active bird modifies that information.
4. Bird speaks modified result.
5. Player reacts.

---

# 📐 Step 1 – Direction Model (Important)

Do NOT use raw Vector3 for speaking.

Instead convert direction into **4 zones**:

```text
Front
Right
Back
Left
```

You calculate angle:

```
angle = SignedAngle(playerForward, zombieDirection)
```

Then:

| Angle Range | Direction |
| ----------- | --------- |
| -45 to 45   | Front     |
| 45 to 135   | Right     |
| 135 to -135 | Back      |
| -135 to -45 | Left      |

This keeps voice lines clean and understandable.

---

# 🐦 Bird Architecture Pattern

Use interface-based system:

```
IBirdBehavior
    GetDirection(realDirection)
    GetUrgency(realDistance)
```

Then implement 4 birds.

---

# 🟢 1️⃣ Truth Bird

### Behavior:

* Always returns correct direction
* Always returns correct urgency

```
return realDirection;
return realUrgency;
```

Voice examples:

* “Zombie on your left.”
* “Very close!”

This is the player’s safe anchor.

---

# 🔴 2️⃣ Inverter Bird

### Behavior:

* Always opposite direction
* Urgency is correct

Opposites:

| Real  | Fake  |
| ----- | ----- |
| Front | Back  |
| Back  | Front |
| Left  | Right |
| Right | Left  |

```
return Opposite(realDirection);
return realUrgency;
```

This creates confident mistakes.

---

# 🟡 3️⃣ Split Bird (Half True / Half Lie)

IMPORTANT: Must feel logical.

Two modes (choose per spawn):

Mode A:

* Correct direction
* Wrong urgency

Mode B:

* Wrong direction
* Correct urgency

Example:

Zombie is:
Left + Very Close

Split Mode A:
Left + “Far away”

Split Mode B:
Right + “Very close”

This creates doubt without chaos.

---

# 🟣 4️⃣ Mimic Bird

Most interesting one.

Behavior:

* At beginning of each Silent Mode, randomly selects:

  * Truth
  * Inverter
  * Split
* Copies that logic for entire Silent session.

IMPORTANT:
Do NOT change every sentence.
Change per session.

This makes it learnable.

---

# 🔄 Bird Selection System

Now big question:

Do all 4 speak?
Or one active at a time?

Best design for fairness:

👉 Only ONE bird speaks per zombie.

Randomly select which bird speaks.

But…

To avoid chaos:

### Memory Rule

Bird identity stays consistent per game session.

Example:

* Bird 1 always truth
* Bird 2 always inverter
* etc.

Do NOT reshuffle mid-game.

That would feel unfair.

---

# 🎚 Urgency System

Instead of raw distance, classify into:

```
Far
Medium
Close
Very Close
```

Distance logic:

| Distance | Urgency    |
| -------- | ---------- |
| >15m     | Far        |
| 8–15m    | Medium     |
| 3–8m     | Close      |
| <3m      | Very Close |

Bird modifies this based on logic.

---

# 🧮 Full Logical Flow

When bird speaks:

```
1. Get nearest zombie
2. Calculate realDirection
3. Calculate realUrgency
4. Select active bird
5. fakeDirection = bird.GetDirection(realDirection)
6. fakeUrgency = bird.GetUrgency(realUrgency)
7. Generate voice line
8. Play audio
```

---

# 🎤 Voice Line Construction

Instead of recording 100 clips,
Use modular system:

Clip types:

* Direction clips:

  * "Front"
  * "Left"
  * "Right"
  * "Behind you"

* Urgency clips:

  * "Far away"
  * "Getting closer"
  * "Very close"

Combine:

"Left... very close."

Pause between them.

This reduces asset workload.

---

# ⚖️ Fairness Rules (CRITICAL)

To avoid frustration:

### Rule 1:

If zombie is VERY CLOSE,
Bird cannot lie about direction twice in a row.

Prevents unfair deaths.

---

### Rule 2:

Never spawn two zombies in opposite directions during early game.

Let player build trust first.

---

### Rule 3:

First Silent Mode always uses Truth Bird.

Teaches player system.

---

# 🎮 Advanced Mind-Game Layer (Optional)

Add subtle personality tones:

Truth Bird → Calm voice
Inverter → Confident aggressive voice
Split → Uncertain voice
Mimic → Neutral

Blind players will pick up tone patterns.

Judges LOVE this detail.

---

# 🧠 Psychological Layer

What makes this genius:

Player starts to:

* Identify patterns
* Trust one bird
* Distrust another
* Second-guess decisions

This is EXACTLY “Confidently Wrong”.

---

# 🚀 Difficulty Scaling for Birds

As difficulty increases:

Level 1:

* Only Truth + Inverter

Level 2:

* Add Split

Level 3:

* Add Mimic

Do not overwhelm early.

---

# 🏆 Why This Will Impress Judges

Blind judges will check:

* Is logic consistent?
* Can I learn patterns?
* Does it feel fair?
* Is sound clear?
* Can I strategize?

Your bird system now:
✔ Is structured
✔ Is learnable
✔ Is psychological
✔ Is fair
✔ Fits theme

---

If you want next:

* 🎧 Exact 3D audio setup settings in Unity
* 🧟 Zombie spawn fairness algorithm
* 🏆 How to balance difficulty so it’s intense but not rage-quit
* 📅 6-day execution blueprint

Tell me what you want next.
