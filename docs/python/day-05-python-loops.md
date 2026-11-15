# Day 5 — Python Loops
### Weeks 5–6 · Two sessions · 2 × 2h 30min · Thonny or Replit

> **Language convention:** this file is the tutor plan, in English, for you. The student-facing material is the web page `day-05.html` (Greek, with English code), which is what he works from during the session.
>
> **Why two sessions:** loops are the first abstraction where a beginner has to hold a *changing* value in his head — the loop variable is different every round. That takes more re-warm-up than anything before it. Session A lands `for`, `range` and the accumulator pattern; Session B uses them for nested loops, the project and the art. If he's visibly flying at the end of Session A, the split point is marked and you can merge — but don't plan to.

---

## 1. Learning objectives

By the end of the two sessions he should be able to:

1. Write `for item in list:` and say what the loop variable holds in *each* round — not just "it loops".
2. Use `range(a, b)` and `range(a, b, step)`, and state without hesitation that the end is **not** included (the opposite of `randint`).
3. Build the **accumulator pattern** from scratch: a variable initialised *outside* the loop, updated *inside* — for a sum, a count, a maximum, and a string.
4. Solve FizzBuzz, and explain why the "both" check goes first (Day 3's `elif` rule).
5. Write a nested loop and predict how many times the inner body runs (multiply, don't add).
6. Rewrite the Day 4 dot art as a three-line loop, and draw closed polygons knowing that sides × angle = 360.
7. Ship the **Password Generator** at the hard level (shuffled), with `random.shuffle()` used correctly.

**Prerequisite check:** Day 4's lists and `random.choice`, Day 3's `elif` and `%`. The Session A warm-up tests both. If he can't say what `fruits[-1]` is or why `15 % 5 == 0`, spend ten minutes there first.

---

## 2. Coverage map — this plan vs. the Udemy Day 5

| Udemy section | Covered here | Note |
|---|---|---|
| Day 5 Goals (Password Generator demo) | §4 **Goals demo** | Run the finished generator first |
| Using the for loop with Python Lists | web §2 | The iteration table + Thonny debugger |
| Coding Exercise 5.1 — Average Height | web §3 + exercise **Α0** | ✓ two loops, no `sum`/`len` yet |
| Coding Exercise 5.2 — High Score | web §3 + exercise **Α1** | ✓ "build a new list" conversion instead of index-based |
| for loops and the range() function | web §5 | ✓ the four `range` shapes, Gauss |
| Coding Exercise 5.3 — Adding Even Numbers | exercise **Α2** | ✓ both ways: `if %` and `step=2` |
| Coding Exercise 5.4 — The FizzBuzz Job Interview | web §6 + exercise **Α3** | ✓ solution hidden behind a reveal |
| Day 5 Project — Password Generator | web §10 | ✓ easy then hard level; strings instead of 52-item lists |

**Beyond the course:** the "inside or outside the loop" prediction, the accumulator named and drilled four times, the Thonny debugger as a loop visualiser, nested loops with the 5×5 map callback to Day 4, countdown (Α4) and vowel counter (Α5, a loop over a string), the spirograph and mandala with the sides × angle = 360 rule, the Quick Draw AI corner, the error table, the recap card, and the checklist.

**One deliberate difference from Angela:** the High Score exercise in the course converts strings to ints with `for n in range(0, len(student_scores)): student_scores[n] = int(student_scores[n])`. I replaced that with building a new list via `append` — it's a Day 4 skill, reads naturally, and avoids introducing index-based mutation before he needs it. If he meets Angela's version in the videos, both are fine.

---

## 3. Session timelines

### Session A — for, range, accumulator (Week 5)

| Time | Block | What happens |
|---|---|---|
| 0:00–0:03 | **Goals demo** | You run the finished Password Generator. Generate two passwords. |
| 0:03–0:12 | **Warm-up** | Day 4 recall + the Day 4 dot art opened on screen (don't fix it yet) |
| 0:12–0:32 | **Concept A** | `for` over a list, the iteration table, Thonny debugger stepping |
| 0:32–0:50 | **Concept B** | The accumulator: average height and high score, built live |
| 0:50–0:54 | ✅ **Checkpoint 1** | Web quiz 1 |
| 0:54–1:04 | **Break** | Away from the screen |
| 1:04–1:24 | **Concept C** | `range()`, the four shapes, Gauss |
| 1:24–1:40 | **FizzBuzz** | He attempts it blind, then the reveal and the "why they fail" |
| 1:40–1:45 | ✅ **Checkpoint 2** | Web quiz 2 — questions 1–4 only; Q5 is nested loops, next week |
| 1:45–2:10 | **Independent exercises** | Α0, Α1, Α2, Α3 — the first two mandatory |
| 2:10–2:25 | **The payoff** | Open the Day 4 dot art, wrap it in a loop, 200 dots. Then 2000. |
| 2:25–2:30 | **Wrap-up** | Checklist items 1–5, commit, journal |

### Session B — nested loops, project, art (Week 6)

| Time | Block | What happens |
|---|---|---|
| 0:00–0:10 | **Recall** | Three questions from the recap card; he re-types the Gauss loop from memory |
| 0:10–0:32 | **Concept D** | Nested loops: the multiplication table, then the 5×5 map callback |
| 0:32–0:36 | ✅ **Checkpoint** | Web quiz 2, question 5 |
| 0:36–0:50 | **Independent exercises** | Α4 countdown and Α5 vowel counter |
| 0:50–1:00 | **Break** | Away from the screen |
| 1:00–1:35 | **Guided build** | Password Generator, easy level then hard level |
| 1:35–2:15 | **Creative closer** | Spirograph, then mandala — forty minutes, on purpose |
| 2:15–2:25 | **AI corner** | Quick, Draw! — in session this time, not homework |
| 2:25–2:30 | **Recap & wrap-up** | Explain-back, checklist 6–8, commit, journal |

---

## 4. Goals demo (3 min)

Run `password_generator.py`. Ask for 6 letters, 2 symbols, 2 numbers. Run it again with the same numbers and point out the password is different. Say nothing about the code. Close it: *"Σήμερα φτιάχνουμε αυτό — και μαθαίνουμε γιατί δεν θα ξαναγράψεις ποτέ την ίδια γραμμή δέκα φορές."*

---

## 5. Warm-up — Session A (9 min)

**Recall from Day 4 (4 min).** No notes: What's `fruits[-1]`? What does `random.choice()` do under the hood? Does `randint(1, 6)` include the 6?

**Open the wound (5 min).** Open his `random_art.py` from Day 4 — the one with ten copies of the same two lines. Scroll through it. Ask: "If I wanted a thousand dots?" Let him groan. Don't fix it. *"Σε δύο ώρες αυτό γίνεται τρεις γραμμές."* That's the hook for the entire session, and it's his own pain, not an abstract promise.

---

## 6. Concepts — PRIMM

### Concept A: for over a list (20 min)

Web §2. Start from the three `print(fruits[n])` lines, then the loop. The thing to land, in Greek, out loud: **the loop variable changes value every round.** The iteration table in §2 makes it concrete; have him fill in the same table on paper for a four-item list before running anything.

**Thonny moment — don't skip.** View → Variables, then Debug (the bug icon) instead of Run, then *Step into* repeatedly. He watches `fruit` change from `"apple"` to `"banana"` to `"cherry"` in the Variables pane. For a visual learner this one minute does more than ten of explanation. If you're on Replit instead, add `print(f"round: {fruit}")` as the first line of the body — less elegant, same effect.

**Predict → Run:** the "Done!" example. Six lines then one. If he says "because Done! has no indent", he has code blocks and loops both.

**Modify (his turn, 4 min):** "Make it print each fruit twice." Two ways exist (two `print`s, or `print(fruit * 2)`); either is fine. What you're checking is that he adds the line *inside* the block.

### Concept B: the accumulator (18 min)

Web §3. This is the most important pattern of the day, and the course doesn't name it. Name it: **accumulator** — a variable that starts empty outside the loop and gathers inside. Say the shape: `total = 0` *before*, `total += x` *inside*, use `total` *after*.

Build average height live, then high score. The diagnostic question after each:

> "What happens if I move `total = 0` inside the loop?"

Make him move it and run it. The answer (you get only the last height) is the single most common accumulator bug, and he should see it with his own eyes now.

High score introduces `if` inside `for` — Day 3 inside Day 5. The "highest so far" idea is worth acting out: you read numbers aloud, he holds up fingers for the biggest heard so far.

Mention `sum()`, `len()`, `max()` exist. Not today.

### ✅ Checkpoint 1 — web quiz 1 (4 min)

He wants 3/4. Question 4 (where does `total = 0` go) is the one.

### Concept C: range() (20 min)

Web §5. The table of four shapes — `range(5)`, `range(1, 6)`, `range(0, 10, 2)`, `range(10, 0, -1)` — have him predict each before running.

**The thing he will get wrong all year:** `range(1, 11)` stops at 10. Say it, write it on paper, and then connect it to Day 4: `randint(1, 11)` *does* include 11. Python is inconsistent here and every programmer alive has been bitten. Owning that now means he'll check instead of assume.

Gauss: the story takes thirty seconds and makes `range(1, 101)` memorable. The loop is the accumulator again — third time today.

**"N times, don't care about the number":** `for i in range(50):` with `i` unused. He'll need this for the password generator and the art. Normalise it now.

### FizzBuzz (16 min)

Web §6. He attempts it **blind** first — five minutes, no hints. It combines `range`, `%`, `elif`; he has all three. Most first attempts put the `% 3` check first and get `Fizz` at 15. Let that happen, then ask: "What did Day 3 say about `elif` and the first true condition?"

Then the reveal. The story about interview candidates failing it is true and motivating: he's thirteen and he just did something that trips up adults applying for programming jobs.

### ✅ Checkpoint 2 — web quiz 2, questions 1–4 (5 min)

He wants 3/4 on those. Question 4 (FizzBuzz order) checks whether the `elif` lesson transferred.

---

## 7. Session A: exercises and the payoff (40 min)

### Independent exercises (25 min)

**You do not touch the keyboard.** Five-minute struggle timer, then *read the error message out loud together*.

- **Α0 Average Height** — mandatory. Two loops, two accumulators. Then the "rewrite with `sum()` and `len()`" step if he's quick.
- **Α1 High Score** — mandatory. If he initialises `highest = 0` ask the negative-numbers question from the solution note; don't require the fix.
- **Α2 Adding Even Numbers** — both ways. The `step=2` version is the "aha" that `range` can do the filtering.
- **Α3 FizzBuzz** — from memory, since he's seen the solution. Check 15, 30, 45.

### The payoff (15 min)

Open `random_art.py`. Delete nine of the ten copies. Wrap the survivor in `for i in range(200):`. Run it.

Then change 200 to 2000. Then add `pen.speed(0)` if he hasn't. This is the moment the whole of Day 4's frustration was engineered for; let it land without commentary. Then: *"Την επόμενη φορά, spirograph."*

**Wrap-up:** checklist items 1–5 only, commit (`Day 5A - loops, fizzbuzz and 2000 dots`), journal.

---

## 8. Session B

### Recall (10 min)

Three questions from the recap card. Then he re-types the Gauss loop from memory — `total = 0`, `for number in range(1, 101):`, `total += number`, `print(total)`. If the `total = 0` ends up inside the loop, that's your first ten minutes.

### Concept D: nested loops (22 min)

Web §9. The multiplication table first: predict the number of lines (9 and 3), then run. The `---` line is the teaching moment — it's indented at the *outer* level, so it prints once per outer round. If he can explain why there are three `---` lines, he has nested indentation.

Then the Day 4 map callback. He remembers asking "what if 5×5?" — now the answer is two lines. `end=" "` and bare `print()` are small and worth the thirty seconds.

The question to ask, and insist on an answer: "20 outer, 20 inner — how many times does the inner `print` run?" 400, not 40. If he says 40, draw it: two rows of three boxes each, count the boxes.

### ✅ Checkpoint — web quiz 2, question 5 (4 min)

### Independent exercises (14 min)

- **Α4 Countdown** — `range(10, 0, -1)`. Watch where `Liftoff!` lands; if it prints ten times, indentation.
- **Α5 Vowel counter** — a loop over a *string*. This is the bridge to the password generator (strings as sequences) and it uses Day 3's `in`. The extension question about Greek accents is a genuine Unicode rabbit hole; let him discover `ά != α` and leave it there.

### Guided build — Password Generator (35 min)

Web §10. He types, you ask. **Run after every step.**

- **Step 1** — the three "alphabets" as *strings*, not Angela's 52-item lists. Ask: "Why does `random.choice()` work on a string?" (A string is a sequence of characters, same as a list is a sequence of items — Α5 just showed that.)
- **Step 2** — easy level. Three loops, `password = ""` outside, `+=` inside. Point at it: accumulator, fourth time this day, gathering letters instead of numbers. Run with 4/2/2 and show the password always has the letters first. "Is that a problem?" Let him reason about guessing.
- **Step 3** — hard level. Build a list, `random.shuffle()`, then one more accumulator loop to join. The trap to walk into deliberately: `password_list = random.shuffle(password_list)` → `None`. Same disease as `append` on Day 4; name the pattern: *changes in place, returns nothing*.
- `"".join()` is in a "for later" callout. Show it only if he asks "isn't there a shorter way?" — and then make him write the loop version anyway.

**Extensions in the page's final note** if he's quick: five passwords at once (a loop around the whole of step 3 — nested!), and the combinatorics question: 62 characters, 8 vs 12 positions, `62 ** 8` vs `62 ** 12`. Day 2's `**` answers it and the number is viscerally large.

### Creative closer — spirograph and mandala (40 min)

Web §11. Forty minutes, deliberately — this is the day art and code become the same activity.

- **Spirograph** — `for i in range(36): circle(100); left(10)`. Run it. Then the knobs: 36×10, 18×20, 72×5 all equal 360 and close; 30×10 doesn't and leaves a gap. Let him find that by breaking it.
- **The star from Day 3** — ten lines → three. Say nothing; he'll notice.
- **Mandala** — nested: inner loop draws one polygon, outer rotates it. The rule **sides × angle = 360** is real geometry he's doing at school; here he *sees* it. Triangles 3×120, pentagons 5×72, stars 5×144 = 720 (two turns, hence the crossing).
- **Combine all three** — spirograph background, mandala on top, dots in the gaps. This is the first piece that no lesson told him how it should look. Screenshot for the README.

### AI corner — Quick, Draw! (10 min, in session)

Web §12. Two rounds of the game, then the question "how does it guess?" The pseudo-code loop in the page is the point: training is a `for` over fifty million drawings with an accumulator that gets slightly less wrong each round. He just spent two sessions on exactly that shape.

Then the data page — a hundred thousand people's cats. For him specifically: look at it as a designer. Then the κουλούρι test: draw something Greek, watch it fail, and name why — *bias in the data*. A network knows only what was in its loop.

### Recap & wrap-up (5 min)

1. **Explain-back (2 min).** He explains the hard-level password generator, in Greek, focusing on why there's a list in the middle. If he says "to shuffle it", done.
2. **Checklist (1 min).** Items 6–8.
3. **Commit (1 min).** `password_generator.py`, `spirograph.py`, `mandala.py`, exercise files, best art screenshot. Message: `Day 5B - password generator and loop art`.
4. **Journal (1 min).** *"Σήμερα έμαθα…"*

**Score privately (1–4 each):** works · readability · independence · creativity · explanation.

**Next session opens with:** three recall questions, and he re-types the mandala's nested loop from memory — because Day 6 wraps that exact block in `def draw_polygon():` and that's the whole idea of functions.

---

## 9. Errors to expect — and what to say

| Error | Cause | What to say |
|---|---|---|
| `TypeError: 'int' object is not iterable` | `for i in 10:` | "A loop needs something with items in it. What makes 0 to 9?" |
| `IndentationError: expected an indented block` | No indent after `for` | "Same rule as `if`. What belongs to the loop?" |
| Loop stops one short | `range(1, 10)` | "Does range include the end? Does randint?" |
| `TypeError: can only concatenate str (not "int")` | `total += height` on split strings | "Day 2. What type does split give you?" |
| Sum equals the last item | `total = 0` inside the loop | "What happens to total at the start of each round?" |
| `Done!` prints N times | Indented into the loop | "Is that line inside or outside? Look at the margin." |
| List becomes `None` | `x = random.shuffle(x)` | "Same as append. Does shuffle give back a list, or change yours?" |
| 15 prints `Fizz` | `% 3` check before the `% 15` check | "Which branch does `elif` stop at?" |
| Spirograph has a gap | turns × angle ≠ 360 | "How many degrees did it turn in total?" |
| Mandala looks like a mess | Inner loop's turn also at the outer level | "Which loop does each `left()` belong to? Count the spaces." |

---

## 10. Between sessions

**After Session A (~45 min, 3 × 15):**
- PracticePython exercises 10 and 14.
- Bring the 2000-dot art to Session B with a palette of his own.
- Optional: FizzBuzz in reverse — 100 down to 1.

**After Session B (~45 min, 3 × 15):**
- CodingBat **List-2**: `count_evens`, `big_diff`, `sum13` — all accumulators.
- Finish the combined art piece; screenshot into the README.
- Optional: the five-passwords-at-once extension.
