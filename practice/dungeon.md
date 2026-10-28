# 🗡️ The Midterm Dungeon: Save File

**Midterm:** tomorrow ~1 p.m. **Difficulty:** Week 7 lab level.

## Current state
- **Run:** 1 · **Floor:** 1 (not yet answered) · **Hearts:** ❤️❤️❤️ · **Streak:** 0 · **XP:** 0
- **Rank:** 🪵 Wooden Script-Kiddie
- **Zone:** 1 · The Matrix Crypt (Week 7 Q5 & Q7)

## Rules
- One question per floor. Answer without running code (exam conditions).
- ✅ Correct → next floor, **+10 XP**, and a 🎁 **Loot Card**.
- 🔥 3 correct in a row → **+1 ❤️** (max 5) and a ✨ **Legendary Card**.
- ❌ Wrong → **−1 ❤️**, a full explanation, and a 📜 **Scroll** (the rule you missed).
- 💡 Hint → costs half a ❤️.
- 💀 0 ❤️ → the run ends; the next run starts on the topics that beat you.
- 👹 Every 5th floor is a Boss (full lab-style program). Beating it gives **+50 XP**, a 🏆 **Trophy** and a rank up.

## Rewards
- 🎁 **Loot Card:** an exam shortcut or "aha" insight for the topic you just beat.
- ✨ **Legendary Card:** a trick that saves time on whole question types.
- 🏆 **Trophy:** a fill-in-the-blanks template of the boss pattern. It goes straight onto your aid sheet.
- **Ranks (by XP):** 🪵 Wooden Script-Kiddie (0) → 🗡️ Loop Squire (30) → 🛡️ List Knight (80) → 🧙 Dict Wizard (150) → 🐉 Matrix Dragonslayer (250) → 👑 Midterm Champion (400)

**The real reward:** every Loot Card, Legendary, Trophy and Scroll gets collected below. By noon tomorrow this file *is* your personal last-look cheat sheet.

## Zone map
1. **The Matrix Crypt:** Week 7 Q5 & Q7 (2D lists, split/map input, pad/truncate, column loops)
2. **The Nested Vaults:** Week 7 Q1 (nested dicts) + dict counting
3. **The Type Swamp:** Week 7 Q4 (mixed-type lists, `type()` vs `isinstance`, sorting)
4. **The Infirmary:** Week 7 Q3 (multi-input programs, if/elif order, accumulators, averages)
5. **The Recursion Spire:** Week 7 Q8 (Fibonacci, loop vs recursion)

## Waiting for you: Run 1 · Floor 1 · 🔍 Trace
```python
table = [[2, 4, 6],
         [1, 3, 5]]

a = []
for row in table:
    a.append(sum(row) / len(row))

b = []
for c in range(len(table[0])):
    s = 0
    for row in table:
        s += row[c]
    b.append(s / len(table))

print(a)
print(b)
print(table[1][2], len(table), len(table[0]))
```
(a) Write the three output lines exactly. (b) How many times does `s += row[c]` run in total?

---

## 🎒 Inventory
### 🎁 Loot Cards
*(none yet)*
### ✨ Legendary Cards
*(none yet)*
### 🏆 Trophies
*(none yet)*
### 📜 Scrolls (mistakes → rules)
*(none yet)*
