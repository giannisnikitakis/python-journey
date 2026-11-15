# Day 6 — Python Functions & Karel
### Week 7 · One session · 2h 30min · Thonny or Replit + Reeborg's World (browser)

> **Language convention:** this file is the tutor plan, in English, for you. The student-facing material is the web page `day-06.html` (Greek, with English code), which is what he works from during the session.
>
> **New dependency:** [Reeborg's World](https://reeborg.ca/world.html) — free, browser-based, no account, no data stored on their server. Open it on your own machine the day before to confirm the Hurdle and Maze worlds load. The course's direct links are in the page; if they ever break, the worlds are in the *World* menu by name.

---

## 1. Learning objectives

By the end of the session he should be able to:

1. Define a function with `def name():` and call it with `name()` — and say clearly that the definition runs nothing.
2. Explain the difference between `greet` (the name) and `greet()` (the call), and why writing the first alone does nothing.
3. Build functions out of functions: `turn_right()` from three `turn_left()`, `jump()` from `turn_right()`.
4. State the general indentation rule — every line ending in `:` opens a block — and say which level any line is on.
5. Write a `while` loop, explain what stops it, and recognise an infinite loop as "nothing inside changed".
6. Choose between `for` (known count / each item) and `while` (until a condition changes).
7. Get Reeborg out of any maze with the right-hand rule, including the open-start edge case.

**Prerequisite check:** Day 5's `for` and the accumulator, Day 3's `if / elif`. The warm-up re-types the mandala loop from memory — that exact block becomes `def mandala():` today, so it needs to be solid.

---

## 2. Coverage map — this plan vs. the Udemy Day 6

| Udemy section | Covered here | Note |
|---|---|---|
| Day 6 Goals (Reeborg maze demo) | §4 **Goals demo** | Run the finished maze first |
| Defining and Calling Python Functions | web §2 | ✓ definition vs call, the "recipe in a drawer" framing |
| The Hurdles Loop Challenge (Reeborg) | web §3 + exercise **Α0** | ✓ `turn_right()` then `jump()`, six times with `for` |
| Indentation in Python | web §5 | ✓ promoted to a general rule with a level-by-level walkthrough |
| While Loops | web §6 | ✓ `for` vs `while` table, infinite loop named and defused |
| Hurdles Challenge using While Loops | web §6 + exercises **Α1**, **Α2** | ✓ Hurdle 2 (random goal) and Hurdle 3 (random hurdles) |
| Jumping over Hurdles with Variable Heights | web §7 + exercise **Α3** | ✓ Hurdle 4, with a paper-tracing instruction |
| Final Project: Escaping the Maze | web §9 | ✓ right-hand rule, then the open-start edge case fixed |

**Beyond the course:** the explicit *definition vs. call* table, the "why bother" three reasons, the `for`/`while` decision table, `while` with plain numbers (Α4 "until stop"), the turtle house (Α5) and flower "brushes", the AI corner (training as `while not good_enough`, binary-search guesser), the error table, the recap card and the checklist. The `edge case` and `tracing` vocabulary is introduced here on purpose — Day 13 (Debugging) builds on both.

---

## 3. Session timeline

| Time | Block | What happens |
|---|---|---|
| 0:00–0:03 | **Goals demo** | You run the finished maze in Reeborg. Hit Play three times; the maze changes, the robot escapes. |
| 0:03–0:12 | **Warm-up** | Day 5 recall + mandala loop from memory |
| 0:12–0:30 | **Concept A** | `def`, definition vs call, the Predict → Run on ordering |
| 0:30–0:48 | **Reeborg Hurdle 1** | `turn_right()`, `jump()`, six jumps with `for` |
| 0:48–0:52 | ✅ **Checkpoint 1** | Web quiz 1 |
| 0:52–1:02 | **Break** | Away from the screen |
| 1:02–1:12 | **Concept B** | The indentation rule, levels, the finger-on-the-margin read |
| 1:12–1:35 | **Concept C** | `while`: Hurdle 2, the numbers version, infinite loop, Hurdle 3 |
| 1:35–1:50 | **Hurdle 4** | Paper trace first, then the two-`while` jump |
| 1:50–1:55 | ✅ **Checkpoint 2** | Web quiz 2 |
| 1:55–2:12 | **Project** | The maze: right-hand rule, then the open-start trap |
| 2:12–2:25 | **Creative closer** | Turtle brushes — petal, flower, garden |
| 2:25–2:30 | **Recap & wrap-up** | Explain-back, checklist, commit, journal |

**AI corner** (binary-search guesser) — 10 minutes if ahead, otherwise homework; it's self-contained and he'll enjoy it alone.

**If time runs short:** Hurdle 4 is the one to cut. It's the hardest Reeborg task and it's fully specified in the page for him to do between sessions. Don't cut the maze or the turtle closer.

---

## 4. Goals demo (3 min)

Open the Maze world in Reeborg, paste your finished solution, hit Play. Hit Play again — different maze, still escapes. A third time. Say nothing about the code. Close with: *"Σήμερα του μαθαίνουμε να βγαίνει από οποιονδήποτε λαβύρινθο — χωρίς να του δείξουμε κανέναν."*

That's the hook: he's going to write a rule, not a solution.

---

## 5. Warm-up (9 min)

**Recall from Day 5 (3 min).** No notes: What does `range(1, 11)` give? Where does `total = 0` go — inside or outside the loop? How many times does the inner body of a 3×4 nested loop run?

**From memory (6 min).** He re-types the mandala's nested loop from Day 5:

```python
for i in range(12):
    for side in range(5):
        pen.forward(90)
        pen.left(72)
    pen.left(30)
```

Keep it on screen. At 2:12 today, the inner loop becomes `def pentagon():` and the whole thing becomes `def mandala():`. Seeing his own code get a name is the cleanest motivation for functions there is.

---

## 6. Concepts — PRIMM

### Concept A: def and call (18 min)

Web §2. The one idea to land, in Greek, said several ways: **the definition runs nothing.** Recipe in a drawer; nothing cooks until you call it. The table in §2 makes definition and call two rows; have him point at each.

**Predict → Run:** the `Start / greet / greet / End` example. The question that matters: "The definition is at the top of the file — why does `Start` print first?" If he says "because def doesn't run", done.

**The trap, walked into on purpose:** have him type `greet` without parentheses and run it. In Thonny's shell it prints `<function greet at 0x…>`; in a script, nothing. Either way: "What did you ask Python to do?" The parentheses are the button.

**Modify (his turn, 4 min):** "Make a second function `goodbye()` and call them in the order goodbye, greet, goodbye." Checks: he writes both `def`s, both calls, and the calls are below the defs.

### Reeborg Hurdle 1 (18 min)

Web §3. He opens the world; you don't touch his mouse. Let him try `move()` a few times to see the robot respond — the immediacy matters.

Then the problem: there's no `turn_right()`. Let him discover that `turn_right()` gives a `NameError` before you say anything. Then: "How many lefts make a right?" He stands up and turns if needed.

`turn_right()` first, then `jump()` built from it. The stacking is the lesson: point at `jump()` calling `turn_right()` calling `turn_left()`. Three storeys.

Then `for step in range(6): jump()` — Day 5 doing the counting. Watch the ordering: if he puts the `for` above the `def`s, Reeborg gives `NameError: jump` and the §3 callout explains why.

### ✅ Checkpoint 1 — web quiz 1 (4 min)

He wants 3/4. Question 2 ("defined it, nothing printed") is the one that predicts the rest of the day.

### Concept B: the indentation rule (10 min)

Web §5. He's seen indentation three times now (if, for, def); this is where it becomes one rule: *every line ending in `:` opens a block.* The Hurdle-4 `jump()` in §5 is annotated level by level — read it together with a finger on the left margin. "Finger moves right, you went in. Finger moves left, you came out."

The diagnostic: cover the comments and ask him to say the level of each line. If he can, he will not have an indentation bug he can't explain for the rest of the year.

Mention Tab vs spaces briefly — Thonny and Replit both convert Tab to four spaces, so it's only a copy-paste risk. Don't dwell.

### Concept C: while (23 min)

Web §6. Start from the problem: Hurdle 2's goal is at a random distance. "How many jumps?" — "I don't know." — "Then you can't use `for`." That gap is the reason `while` exists.

`while not at_goal(): jump()`. Read it aloud in Greek: *όσο δεν είσαι στον στόχο, πήδα.* Run it in Reeborg several times.

**Then take Reeborg away** and show the numbers version — `n = 0; while n < 3: ...; n += 1`. The thing to make him see: the `n += 1` is what ends the loop. **Delete it and run.** Thonny hangs; he presses Stop. Name it: *infinite loop*. The question for the rest of the year is always "what was supposed to change in here, and didn't?" On Reeborg the same bug looks like the robot circling forever — same question.

The `for`/`while` table in §6 — have him add a row of his own ("until the player types stop", "for each name in the list").

Hurdle 3 closes the block: `while` outside, `if wall_in_front()` inside. Day 3 inside Day 6.

### Hurdle 4 (15 min)

Web §7. **Paper first.** He draws Reeborg in front of a height-2 hurdle and traces the code with a finger, writing the robot's position after each line. This is *tracing*, and it's the first time he debugs without running anything. Five minutes.

Then type it and run. The two `while`s inside `jump()` — "climb while there's wall on your right", "descend while the front is clear" — are the first loops he's written inside a function. Point at the indentation levels one more time: the `move()` inside the first `while` is at level 2, and so is the `jump()` call at the bottom of the program, but they belong to different blocks.

### ✅ Checkpoint 2 — web quiz 2 (5 min)

He wants 4/5. Question 3 (what happens without `n += 1`) and question 5 (the maze loop) are the ones.

---

## 7. Project — the maze (17 min)

Web §9. **Paper first, again:** draw a tiny maze, put a finger on the right wall, walk it. Then write the rule as a flowchart — three diamonds in a fixed order.

Type the right-hand rule. Play, play, play. Different maze every time; it works. Say the word: **algorithm** — a procedure that works for every case, not a solution to one. Eleven lines, infinite mazes.

**Then let him find the bug.** Keep pressing Play; within a few tries Reeborg starts in open space and spins in a circle forever. Ask "when does it happen?" — he'll notice it's when there's no wall on the right at the start. The fix (walk forward until a wall, turn left, then start the rule) is in §9 step 2.

Name what he just did: found an **edge case**, understood it, handled it. That's half of programming, and Day 13 makes it systematic.

**If he's quick:** left-hand rule (one word changes — which?), and the island question in the page's final note. The island — an exit not connected to the outer wall — is the one maze the hand rule cannot solve, and drawing one is a genuinely good ten minutes.

---

## 8. Independent exercises

There's no separate exercise block today — Α0–Α3 *are* the four Hurdles and are done in the session above. **Α4 and Α5 are for between sessions** unless he's well ahead:

- **Α4 "until stop"** — a `while answer != "stop":` loop with an accumulator. The thing to check: does he initialise `answer = ""` before the loop? Without it `while` has nothing to test and gives `NameError`. This is the skeleton of every "play again?" loop from Hangman onward.
- **Α5 the house** — `square()`, `triangle()`, `house()`, a street of five. The pedagogically important bit is `house()` calling the other two: three storeys of functions, drawn. The trap is getting the turtle back to its starting position after the triangle; the solution comments show the return moves.

**Outside sources:** Reeborg's own *World* menu has dozens more — *Around 1–4* and *Center 1–3* are the right difficulty. CodingBat Warmup-1 now makes sense: every problem there is a `def` he fills in.

---

## 9. Creative closer — turtle brushes (13 min)

Web §11. `petal()` from two arcs, `flower()` from twelve petals, three flowers via `jump_to()`. The climb is the point — point at it: `circle` → `petal` → `flower` → garden. "When you write `flower()`, are you thinking about arcs?" No. That's what functions buy you.

`pen.circle(60, 60)` is new (second argument = degrees of arc); it's one line of explanation.

`jump_to(x, y)` takes arguments — Day 8's material, shown two days early without ceremony. If he asks what the `x, y` are, say "that's next week; for now, use it." If he doesn't ask, don't bring it up.

**Then the callback:** open his Day 5 `mandala.py` and wrap the inner loop in `def pentagon():` and the outer in `def mandala():`. Same picture, now one word. Save both files side by side; that comparison goes in the README.

---

## 10. AI corner — optional 10 min

Web §12. Two things, in order:

**The refinement of Day 5:** training isn't really `for drawing in millions` — it's `while not good_enough()`. Nobody knows how many rounds; only what "done" means. He just spent an hour on exactly that shape with Reeborg.

**The ten-line guesser:** he thinks of a number 1–100, the computer finds it in ≤7 guesses by halving. He plays it five times and the "always seven" lands. Then the question: 1 to a million? `2 ** 20 ≈ 1,000,000`, so twenty. From 7 to 20 while the range went from a hundred to a million — that's the whole reason computers find things fast, and it's Day 2's `**` doing the explaining.

The connection to AI is one sentence: a network being trained is doing something like this guesser, but for millions of numbers at once, with "warmer/colder" coming from its own mistakes. Don't push it further than that today.

---

## 11. Recap & wrap-up (5 min)

1. **Explain-back (2 min).** He explains the maze rule in Greek, including why the open-start fix is needed. If he says "because the right hand has nothing to touch", done.
2. **Checklist (1 min).** Web §14.
3. **Commit (1 min).** `house.py`, `flower.py`, the refactored `mandala.py`, and a text file `reeborg_solutions.py` with the four hurdles and the maze (Reeborg doesn't save to GitHub; he copies the code out). Message: `Day 6 - functions, reeborg maze and turtle brushes`.
4. **Journal (1 min).** *"Σήμερα έμαθα…"*

**Score privately (1–4 each):** works · readability · independence · creativity · explanation.

**Next session opens with:** three recall questions, and he re-types `turn_right()` and `jump()` from memory — then Hangman, where he builds his first whole game from a blank file using everything so far.

---

## 12. Errors to expect — and what to say

| Error | Cause | What to say |
|---|---|---|
| Defined, nothing happens | No call | "Where's the line that says *do it*?" |
| `<function greet at 0x…>` | `greet` without `()` | "What are the parentheses for?" |
| `NameError: name 'jump' is not defined` | Call above the def | "Which line does Python read first?" |
| `SyntaxError` at `def` | Missing `()` or `:` | "`def name():` — count the pieces." |
| `IndentationError: expected an indented block` | No indent after `def`/`while` | "What does every `:` open?" |
| `TabError` | Mixed tabs/spaces from a paste | "Delete the indent on that line and re-Tab it." |
| Thonny hangs / Reeborg circles | Infinite loop | "Stop it. What was supposed to change in there?" |
| Reeborg hits a wall | A wrong turn in `jump()` | "Trace it on paper. Where is he after line 3?" |
| `NameError: turn_right` in Reeborg | Not defined (or defined below use) | "Reeborg doesn't have that one. Who makes it?" |
| `NameError: answer` in Α4 | `while answer != "stop"` before `answer` exists | "What's `answer` the first time the `while` checks it?" |

---

## 13. Between sessions (~45 min total, 3 × 15)

- Hurdle 4 if it was cut; otherwise Reeborg *Around 1–2*.
- Α4 "until stop" and Α5 the house.
- The AI-corner guesser, played against a sibling — bring the number of tries.
- Optional: three more brushes (`star()`, `leaf()`, `spiral()`) and one picture that uses all of them.
