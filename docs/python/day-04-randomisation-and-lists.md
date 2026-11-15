# Day 4 — Randomisation and Python Lists
### Week 4 · One session · 2h 30min · Thonny or Replit

> **Language convention:** this file is the tutor plan, in English, for you. The student-facing material is the web page `day-04.html` (Greek, with English code), which is what he works from during the session.

---

## 1. Learning objectives

By the end of the session he should be able to:

1. Explain what a **module** is and bring one in with `import`; read `random.randint` as "from random, take randint".
2. Produce random integers with `randint(a, b)` (both ends inclusive) and random floats with `random()`.
3. Create a list, read items by index (positive and negative), change an item, and append with `.append()`.
4. Explain the **offset** — why the first item is `[0]` and the last is `[len - 1]` — and recognise an `IndexError` in three seconds.
5. Pick a random item with `random.choice()` and explain what it does under the hood (`randint(0, len - 1)`).
6. Read a nested list with two pairs of brackets and place something in a 3×3 grid.
7. Ship **Rock-Paper-Scissors** with his own ASCII art, built from an outcome table he drew first.

**Prerequisite check:** Day 3's `if / elif / else` and `.lower()`. The warm-up tests this. If he can't re-type the pizza order's size block from memory, spend ten minutes there — Rock-Paper-Scissors is five `elif`s in a row and will collapse without it.

---

## 2. Coverage map — this plan vs. the Udemy Day 4

| Udemy section | Covered here | Note |
|---|---|---|
| Day 4 Goals (Rock-Paper-Scissors demo) | §4 **Goals demo** | Play the finished game first |
| Random Module | web §2 | `randint`, `random`, `choice` — plus the `random.py` filename trap |
| Coding Exercise 4.1 — Heads or Tails | web §2 + exercise **Α0** | ✓ |
| Understanding the Offset and Appending Items to Lists | web §4–§5 | ✓ the index table, `append`, `extend` |
| Coding Exercise 4.2 — Banker Roulette | web §5 + exercise **Α1** | ✓ both versions: `choice`, then `randint + len - 1` |
| IndexErrors and Working with Nested Lists | web §5–§6 | ✓ "off-by-one" named explicitly |
| Coding Exercise 4.3 — Treasure Map | web §6 + exercise **Α2** | ✓ `grid` instead of `map` (don't shadow the built-in) |
| Day 4 Project — Rock Paper Scissors | web §8 | ✓ five steps, outcome table on paper first |

**Beyond the course:** the 3×3 outcome table before coding, the `randint + len - 1` reveal of what `choice` does, the input-guard step, the modulo win-check as a "for later", Magic 8-Ball (Α3), two dice (Α4), team-name generator (Α5), the generative-art turtle closer, the "dumbest language model" AI corner, the error table, the recap card, and the checklist.

**No swaps this time** — all three of Angela's exercises are good as they are.

---

## 3. Session timeline

| Time | Block | What happens |
|---|---|---|
| 0:00–0:03 | **Goals demo** | You play the finished Rock-Paper-Scissors. Win once, lose once. |
| 0:03–0:12 | **Warm-up** | Day 3 recall + pizza size block from memory |
| 0:12–0:30 | **Concept A** | `import`, the `random` module, Heads or Tails live |
| 0:30–0:34 | ✅ **Checkpoint 1** | Web quiz 1 |
| 0:34–0:56 | **Concept B** | Lists, offset, `append`, `len`, `IndexError`, Banker Roulette |
| 0:56–1:06 | **Break** | Away from the screen |
| 1:06–1:20 | **Concept C** | Nested lists, Treasure Map |
| 1:20–1:24 | ✅ **Checkpoint 2** | Web quiz 2 |
| 1:24–1:30 | **Outcome table on paper** | The 3×3 Win/Lose/Draw grid |
| 1:30–1:58 | **Guided build** | Rock-Paper-Scissors in five steps, run after each |
| 1:58–2:08 | **Independent exercises** | Α0 and Α1 mandatory, then one of his choice |
| 2:08–2:25 | **Creative closer** | Generative art — longer than usual, on purpose |
| 2:25–2:30 | **Recap & wrap-up** | Explain-back, checklist, commit, journal |

Optional **AI corner (10 min)** — the dumbest language model. Give it as homework if you're out of time; it builds directly on exercise Α5. See §10.

---

## 4. Goals demo (3 min)

Play your finished `rock_paper_scissors.py` in front of him. Pick paper, hope for rock. Play again. Say nothing about the code. Close it: *"Σήμερα φτιάχνουμε αυτό — και ο υπολογιστής δεν θα ξέρει τι θα διαλέξει μέχρι να το διαλέξει."*

That last clause is the hook. Everything he's built so far was deterministic. Today the computer surprises him.

---

## 5. Warm-up (9 min)

**Recall from Day 3 (3 min).** Three questions, no notes: What's the difference between `=` and `==`? When do you use `elif` instead of a second `if`? What does `.lower()` do and why do we put it on `input()`?

**From memory (6 min).** He re-types the pizza order's size block — `if size == "S"` / `elif` / `else` with `bill += ...` — without looking. This is the exact pattern the Rock-Paper-Scissors decision uses, so if it's shaky now, it will be shaky at 1:45 with less time to fix it.

---

## 6. Concepts — PRIMM (54 min in three parts)

### Concept A: import and random (18 min)

Work through web §2 together. The three things to land, out loud in Greek:

- A **module** is someone else's file. `import` makes it yours. `random.randint` reads "from random, take randint" — the dot is possession.
- `randint(1, 6)` includes both ends. Ask: "If it didn't include the 6, could this ever be a dice?"
- The `random.py` filename trap. Tell him about it now, before he does it. It's the single most confusing beginner error because the message makes no sense — and he will name a file `random.py` at some point if you don't.

**Predict → Run:** `random.randint(1, 6)` five times. Then ask what `random.random() * 10` gives and have him run it ten times. He should notice it never reaches 10.

Build Heads or Tails live — it's eight lines and combines today's `randint` with Day 3's `if`. That's the point: new tool, old pattern.

### ✅ Checkpoint 1 — web quiz 1 (4 min)

He wants 3/4. Question 2 (`randint` without `random.`) is the one that predicts the next hour.

### Concept B: lists and the offset (22 min)

Web §4–§5. Start from Day 2: "You already did `name[0]` for the first letter. A list is the same idea, but the items can be anything." The index table in §4 (positions 0/1/2 above, −3/−2/−1 below) is worth drawing on paper as well.

**The deliberate error:** `fruits[3]` on a three-item list. Let him hit `IndexError: list index out of range` and read it aloud. Then say the name: *off-by-one*. He's going to make this mistake for years; what matters is recognising it instantly.

**Banker Roulette, both ways.** First with `random.choice()` — three lines, magic. Then take the magic away: `random.randint(0, len(names) - 1)`. Ask: "Why `- 1`? What happens without it?" Have him remove the `- 1` and run it until it crashes. That crash is the whole lesson about offsets, delivered by Python instead of you.

**Modify (his turn, 5 min):** "Add yourself to the list after the input, with `.append()`, so you're always a candidate to pay." One line, and it tests whether he writes `names.append(...)` or the broken `names = names.append(...)`.

### Concept C: nested lists (14 min)

Web §6. "A box with boxes inside." `food[1][0]` reads left to right: second list, first item.

The Treasure Map is where it clicks. Two things to watch:

- `"ABC".index(position[0].upper())` — he's seen `.lower()` and `.count()`; `.index()` is one more string method. "Where is B inside ABC?" → 1.
- `int(position[1]) - 1` — the user counts rows from 1, Python from 0. If the X lands one row too low, he forgot the `- 1`. Let it happen once.

I used `grid` instead of Angela's `map` because `map` is a Python built-in and shadowing it is a habit worth not forming. Not worth mentioning to him unless he asks.

### ✅ Checkpoint 2 — web quiz 2 (4 min)

He wants 4/5. Question 3 (`fruits[3]` → IndexError) and question 5 (nested index) are the ones that matter.

---

## 7. Outcome table, then guided build (34 min)

### Outcome table on paper (6 min) — do not skip this

A 3×3 grid: his choice down the side (rock, paper, scissors), computer's across the top. Nine cells, each Win / Lose / Draw. This is the Day 3 flowchart discipline in table form — and for Rock-Paper-Scissors the table *is* the program. Step 4 of the build is literally reading the table row by row.

Photo for the repo.

### Guided build (28 min)

Follow web §8 steps 1–5. He types, you ask questions. **Run after every step.**

- **Step 1** — the three ASCII symbols and the list. Five minutes max on art or it eats the session; the page has placeholders. The line to point at is `choices = [rock, paper, scissors]` — three variables, one list.
- **Step 2** — user picks a number, `print(choices[user_choice])`. Stop here. This is the moment: the user's number *is* the index. No `if`. Ask: "Why does 0 mean rock?" If he says "because rock is in position 0", he's got it.
- **Step 3** — `random.randint(0, 2)`. Ask why not `(0, 3)`. If he hesitates, send him back to §5.
- **Step 4** — the decision, straight off the outcome table. Three "win" rows, one "draw", `else` for the rest. Ask: "How does `else` cover three different losing cells with one line?"
- **Step 5** — the guard. "What if the user types 7?" Let him try it first — `IndexError` — then wrap steps 2–4 in `if user_choice < 0 or user_choice > 2`. Point out it's Day 3's `or` doing the work.

Then hand it over: his art, his messages (Greek is fine), and the lava extension in the page's final note if he's quick.

**The modulo trick** (`(user - computer) % 3 == 1`) is in a callout marked "for later". Show it only if he's visibly ahead. It's a lovely piece of maths but not today's objective.

**Two traps worth walking into deliberately:**
- Type `abc` at the number prompt → `ValueError` from `int()`. He saw this on Day 2; let him recognise it.
- `fruits = fruits.append("kiwi")` → the list becomes `None`. Five seconds of confusion now saves an hour in three weeks.

---

## 8. Independent exercises (10 min)

**You do not touch the keyboard.** Five-minute struggle timer, then *read the error message out loud together* before anything else.

- **Α0 Heads or Tails** — mandatory, two minutes. Bonus: the one-line `random.choice(["Heads", "Tails"])` version.
- **Α1 Banker Roulette** — mandatory, the `randint + len - 1` version. If it runs ten times without an `IndexError`, the offset has landed.
- Then one of: **Α2** Treasure Map, **Α3** Magic 8-Ball, **Α4** two dice, **Α5** team-name generator.

**Α5 note:** steer him here if he's going to do the AI corner — it's the setup for it.

**Outside sources:** CodingBat → Python → **List-1** is today's material with instant feedback. The problems are wrapped in `def` — tell him to write his answer after `return` and ignore the rest until Day 6. `first_last6`, `same_first_last`, `make_pi`.

---

## 9. Creative closer — generative art (17 min)

Web §10. This is the visual payoff day for him specifically, which is why it gets seventeen minutes instead of twelve.

The code is a two-line block — `goto(random, random)` and `dot(random size, random colour)` — that he **copy-pastes ten times**. Yes, deliberately. Let him feel it. Then say exactly this: *"Day 5 turns those 20 lines into 3, and instead of 10 dots you'll place a thousand."* That's the entire motivation for loops, and it comes from his own hands, not from you.

Run it five times. It's different every time, and no run will ever repeat. Screenshot the best one for the README.

**If he's quick:** the random-walk variant in the same section. Different texture entirely — lines instead of dots. Change the heading list to six directions and it becomes something else again.

---

## 10. AI corner — optional 10 min

Web §11. Three lists → a sentence generator → "the dumbest language model in the world". Then the honest claim: ChatGPT does *the same thing* — picks the next word from a list — with three differences: a 100,000-token list, weighted choices, and weights learned rather than written.

`random.choices(..., weights=[60, 35, 5])` makes the second point visible in twenty runs. The cat almost never takes off.

Then the question to send him away with: ask any AI the same thing twice and compare. Different answers → there's a `random.choices()` in there somewhere, and the knob is called *temperature*. This is the most concrete intuition about generative AI a 13-year-old can get from eight lines of code, and it's built entirely from today's two concepts.

---

## 11. Recap & wrap-up (5 min — tight, so keep it moving)

1. **Explain-back (2 min).** He walks you through Rock-Paper-Scissors step 2 only: why does `choices[user_choice]` work? If he can say "the number is the position", the day landed.
2. **Checklist (1 min).** Web §13. Only what he can do without notes.
3. **Commit (1 min).** `rock_paper_scissors.py`, `random_art.py`, his exercise files, the outcome-table photo, and the best art screenshot. Message: `Day 4 - rock paper scissors and random art`.
4. **Journal (1 min).** One line: *"Σήμερα έμαθα…"*

**Score privately (1–4 each):** works · readability · independence · creativity · explanation.

**Next session opens with:** three recall questions from the recap card, and he re-types the two-line dot block from memory — because Day 5's first act is to wrap it in a `for` loop.

---

## 12. Errors to expect — and what to say

| Error | Cause | What to say |
|---|---|---|
| `NameError: name 'random' is not defined` | No `import random` | "What's the first line of every program that uses random?" |
| `NameError: name 'randint' is not defined` | Wrote `randint` without `random.` | "Where does randint live?" |
| `AttributeError: module 'random' has no attribute 'randInt'` | Capital I | "Python cares about capitals. Read it letter by letter." |
| `AttributeError` on *every* random call | File is named `random.py` | "What's your file called?" — then rename it and delete any `__pycache__` folder next to it |
| `IndexError: list index out of range` | Index ≥ `len` | "How many items? So what's the biggest index that exists?" |
| `TypeError: list indices must be integers` | `fruits["1"]` or missing `int()` on input | "Is that a number or text?" |
| List becomes `None` | `x = x.append(...)` | "Does append *give you back* a list, or *change* the one you have?" |
| `ValueError: substring not found` | `"ABC".index("D")` | "What did the user type? Is it in ABC?" — Day 3's `else` fixes it |
| `ValueError: invalid literal for int()` | Typed `abc` at a number prompt | "Day 2. What type does input give you?" |

---

## 13. Between sessions (~45 min total, 3 × 15)

- CodingBat **List-1**, first five problems (answer after `return`, ignore the `def` for now).
- Finish the generative art properly: 20 dots, his own palette, and the random-walk variant. Bring the best screenshot.
- Optional: the AI corner — the sentence generator with his own three lists, in Greek. Bring the funniest sentence it produced.
