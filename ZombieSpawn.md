Good.
Zombie spawning is where most audio-games fail.

If spawn logic is bad:

* Feels unfair
* Audio becomes chaos
* Player dies randomly
* Judges get frustrated

We’ll design a **fair, readable, scalable spawn system**.

---

# 🧟 ZOMBIE SPAWN SYSTEM

For *Echoes of the Dead*

---

# 🎯 Design Goals

Spawn system must:

* ✔ Be fair
* ✔ Be readable via audio
* ✔ Scale difficulty gradually
* ✔ Avoid random unavoidable deaths
* ✔ Support bird logic system

---

# 🧠 Core Design Decision

⚠️ Player does NOT move.

Only rotates in 360°.

So spawning must be circular around player.

---

# 1️⃣ Spawn Geometry

Imagine a circle around the player.

```
         Back
   Left         Right
         Front
```

Zombies spawn at:

* Random angle (0–360°)
* Fixed radius distance (e.g., 15 meters)

---

# 2️⃣ Basic Spawn Formula (Concept)

```
angle = Random(0, 360)
direction = Quaternion.Euler(0, angle, 0) * Vector3.forward
spawnPosition = player.position + direction * spawnRadius
```

Keep radius between:

* 12–18 meters

Never spawn inside 8 meters early game.

---

# 3️⃣ Spawn Phases (IMPORTANT FOR FAIRNESS)

Instead of random chaos, use phases.

---

## 🟢 Phase 1 – Learning Phase (First 60 seconds)

* Max 1 zombie alive
* Spawn every 6–8 seconds
* Always spawn 90° away from last zombie
* No opposite-direction spawns

Purpose:
Player learns sound direction safely.

---

## 🟡 Phase 2 – Pressure Phase

* Max 2 zombies alive
* Spawn every 4–6 seconds
* Minimum 60° separation rule

Separation rule:
If zombie A is at 30°,
Next spawn cannot be between -30° to 90°.

This avoids overlapping audio.

---

## 🔴 Phase 3 – Chaos Phase

* Max 3 zombies alive
* Spawn every 2–4 seconds
* Can spawn anywhere
* Silent Mode triggers faster

But still:
Never allow 2 zombies inside 3m at same time.

That feels unfair.

---

# 4️⃣ Fairness Rules (CRITICAL)

These are judge-saving rules.

---

## Rule 1 – Safe Reaction Window

Every zombie must give:

Minimum 2.5 seconds before first attack.

This allows player reaction.

---

## Rule 2 – No Double Back Spawn

If zombie spawns behind player,
Next zombie cannot spawn behind within 5 seconds.

Prevents cheap deaths.

---

## Rule 3 – Distance Buffer

Never spawn new zombie if:
Another zombie is within 4m.

---

## Rule 4 – Silent Mode Protection

When Silent Mode activates:

Delay next spawn by 2 seconds.

Give brain adjustment time.

---

# 5️⃣ Movement Speed Scaling

Zombie speed must scale slowly.

Example:

| Time    | Speed           |
| ------- | --------------- |
| 0–1 min | Slow walk       |
| 1–2 min | Normal          |
| 2–3 min | Slightly faster |
| 3+ min  | Aggressive      |

Never go extreme fast.
Audio tracking becomes impossible.

---

# 6️⃣ Spawn Director System (Pro-Level Design)

Instead of random spawn, use a “Spawn Director”.

Spawn Director checks:

* Player health
* Ammo count
* Current zombie count
* Recent damage taken

If player just took damage:
→ Delay next spawn slightly.

If player hasn’t been pressured:
→ Increase spawn rate.

This creates dynamic difficulty.

---

# 7️⃣ Spawn Type Variations (Optional Advanced)

Later add:

### 1️⃣ Walker

Normal speed

### 2️⃣ Runner

Faster, but louder breathing

### 3️⃣ Whisperer

Very quiet footsteps (danger type)

But introduce slowly.

---

# 8️⃣ Audio-Based Spawn Signaling (VERY IMPORTANT)

Never spawn silently.

Always give subtle cue:

When zombie spawns:
Play distant “wind growl” sound.

So player subconsciously knows:
“New threat entered world.”

Judges love subtle design.

---

# 9️⃣ Spawn Angle Bias (Smart Trick)

To avoid randomness feeling random:

Use weighted spawn:

* 40% chance front
* 30% left
* 30% right
* 10% back (early game)

Back spawns are hardest.

Increase back chance in later phases.

---

# 🔟 Handling Multiple Zombies

When 2+ zombies active:

Always ensure:

Minimum 45° difference between them.

Otherwise audio blends too much.

---

# 🧠 Silent Mode Spawn Logic

During Silent Mode:

* Max 1 zombie active early
* Later max 2
* Spawn slower
* Rely on birds

Do NOT mix:
3 silent zombies + 4 birds = chaos.

Keep readable.

---

# 🧪 Testing Method

Close eyes.

Spawn 2 zombies.

Ask:

* Can I distinguish both?
* Can I track one at a time?
* Does it feel possible?

If answer is no → reduce spawn.

---

# 🏆 What Judges Will Notice

They will subconsciously evaluate:

✔ Fairness
✔ Reaction time
✔ Audio clarity
✔ Spawn predictability
✔ Learning curve

Good spawn design = high polish score.

---

# 🎯 Final Golden Rule

In blind games:

> Difficulty must come from decision-making
> NOT from sensory overload.

---

If you want next:

* 🏆 Difficulty balancing formula (exact numbers)
* 🧠 Full Game Loop flowchart
* 🎤 Voice recording plan for birds
* 📅 6-day build execution roadmap

Tell me what you want next.
