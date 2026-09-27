# Day 3 — Control Flow and Logical Operators
### Week 3 · One session · 2h 30min · Thonny or Replit

> **Language convention:** this file is the tutor plan, in English, for you. The student-facing material is the web page `day-03.html` (Greek, with English code), which is what he works from during the session.
>
> **Swap in his name** wherever the examples use `"Odysseas"`.

---

## 1. Learning objectives

By the end of the session he should be able to:

1. Write `if` / `else` with the colon and four-space indentation, and explain what a **code block** is.
2. Use all six comparison operators and explain why `=` and `==` are different things.
3. Test divisibility with `%` and explain `x % 2 == 0` in plain words.
4. Choose correctly between `if / elif / else` (one outcome from several) and successive independent `if` statements (several independent checks) — this is the conceptual heart of the day.
5. Combine conditions with `and`, `or`, `not`, and avoid the `x == 3 or 5` trap.
6. **Draw a flowchart on paper before writing code** with more than two branches.
7. Ship a **Treasure Island** with his own story, his own ASCII art, and at least one path nobody expects.

**Prerequisite check:** Day 2's `int(input())` and f-strings. The warm-up tests this. If he writes `if height > 120` with a string `height` and doesn't recognise the `TypeError`, spend ten minutes on Day 2 recall before moving on.

---

## 2. Coverage map — this plan vs. the Udemy Day 3

| Udemy section | Covered here | Note |
|---|---|---|
| Day 3 Goals (Treasure Island demo) | §3 **Goals demo** | Run the finished game first |
| Control Flow with if/else and Conditional Operators | web §2 | Rollercoaster v1 |
| Coding Exercise 3.1 — Odd or Even | web §3 + exercise **Α0** | ✓ |
| Nested if statements and elif | web §5 | Rollercoaster v2/v3 |
| Coding Exercise 3.2 — BMI 2.0 | exercise **Α1 — Water state** | Swapped, same shape (see note) |
| Coding Exercise 3.3 — Leap Year | exercise **Α2** | ✓ three nested ifs + one-liner for later |
| Multiple If Statements in Succession | web §6 | Pizza as the worked example |
| Coding Exercise 3.4 — Pizza Order | exercise **Α3** | ✓ |
| Logical Operators | web §7 | Rollercoaster "midlife crisis" |
| Coding Exercise 3.5 — Love Calculator | exercise **Α4** | ✓ introduces `.lower()` and `.count()` |
| Day 3 Project — Treasure Island | web §9 | ✓ built in four steps, flowchart first |
| Share and show off your project | §9 wrap-up | Commit + show someone at home |

**Beyond the course:** the flowchart-first discipline, the `elif` vs. multiple-`if` decision table, the zoo ticket exercise (Α5), the Turtle shape picker, the ELIZA AI corner, the error table, the recap card, and the checklist.

**On BMI 2.0 (Α1):** it's a three-band `if / elif / else` on a computed number — mechanically identical to classifying water by temperature. Same reason as Day 2: I'd rather he not classify his own body at 13. The water version also links to your Chemistry Week 2 (states of matter), which is a nice bit of glue between the courses.

---

## 3. Session timeline

| Time | Block | What happens |
|---|---|---|
| 0:00–0:03 | **Goals demo** | You play the finished Treasure Island in front of him. Lose on purpose once. |
| 0:03–0:12 | **Warm-up** | Day 2 recall + the deliberate `TypeError` from comparing `str` to `int` |
| 0:12–0:30 | **Concept A** | `if / else`, comparison operators, code blocks, `%` |
| 0:30–0:34 | ✅ **Checkpoint 1** | Web quiz 1 |
| 0:34–0:55 | **Concept B** | Nested if, `elif`, multiple ifs, logical operators |
| 0:55–0:59 | ✅ **Checkpoint 2** | Web quiz 2 |
| 0:59–1:09 | **Break** | Away from the screen |
| 1:09–1:19 | **Flowchart on paper** | He designs his Treasure Island story before touching the keyboard |
| 1:19–1:52 | **Guided build** | Treasure Island in four steps, run after each |
| 1:52–2:08 | **Independent exercises** | Α0 and Α2 mandatory, then two of his choice |
| 2:08–2:20 | **Creative closer** | Turtle shape picker — his shapes, his colours |
| 2:20–2:30 | **Recap & wrap-up** | Explain-back, checklist, commit, journal |

Optional **AI corner (10 min)** — ELIZA. Drop it in before the recap if you're ahead, or give it as homework. See §8.

---

## 4. Goals demo (3 min)

Play your finished `treasure_island.py` in front of him. Go left, wait, pick yellow — win. Then play again and pick red — lose. Say nothing about the code. Close it: *"Σήμερα φτιάχνουμε αυτό, αλλά με δική σου ιστορία."*

The "with your own story" matters. It's the difference between typing Angela's game and making his.

---

## 5. Warm-up (9 min)

**Recall from Day 2 (3 min).** Three questions, no notes: What does `input()` always return? What does `7 // 2` give? What's the difference between `round(x, 2)` and `f"{x:.2f}"`?

**The deliberate error (6 min).** Have him type this and predict:

```python
height = input("Height in cm: ")
if height > 120:
    print("Ride!")
```

He'll get `TypeError: '>' not supported between instances of 'str' and 'int'`. **Do not fix it.** Ask: "What type is `height` right now?" He should reach for `int()` himself. This connects Day 2 directly to Day 3 and is the single most common bug he'll write today.

---

## 6. Concepts — PRIMM (43 min in two halves)

### Concept A: if / else, comparison, modulo (18 min)

Work through web §2 and §3 together. The three things to land, out loud in Greek:

- The **colon** and the **indentation** aren't decoration — they *are* the syntax. Python has no `{ }`.
- `=` assigns, `==` compares. Have him say the difference in his own words.
- `x % 2 == 0` reads as "nothing is left over when you divide by 2".

**Predict → Run:** the `Thanks for visiting` example in web §2. Ask why it prints in both cases. If he says "because it's not indented", he's got code blocks.

### ✅ Checkpoint 1 — web quiz 1 (4 min)

He wants 3/4. If he misses the `IndentationError` question or the `=` vs `==` question, redo Concept A's examples before continuing — those two errors will otherwise eat half the guided build.

### Concept B: elif, multiple ifs, logical operators (21 min)

The idea that matters most today, and the one the Udemy course spends least time on explicitly: **`elif` stops at the first true branch; successive `if`s all run.**

Use the pizza order (web §6) as the contrast case. Size is one choice → `elif`. Pepperoni and cheese are independent → separate `if`s. Then ask the diagnostic question:

> "If I want to charge for *both* pepperoni and cheese, why can't I use `elif` for the cheese?"

If he can answer that, he understands the distinction. If he can't, act it out: you're the waiter, he orders, you only listen to the first thing he says (elif) vs. you listen to everything (multiple ifs).

**Logical operators** — the `or` trap is the one to hit. In Greek you say «3 ή 5», so he will write `x == 3 or 5`. Show that `5` on its own is always truthy. This is worth two minutes now and will save twenty later.

**Modify (his turn, 6 min):** "Change the rollercoaster so that anyone under 3 rides free, and under 12 pays €5." Two edits, one of which requires him to think about the *order* of the `elif`s.

### ✅ Checkpoint 2 — web quiz 2 (4 min)

He wants 3/4. Question 1 (two ifs vs elif) is the one that matters.

---

## 7. Flowchart, then guided build (43 min)

### Flowchart on paper (10 min) — do not skip this

Give him an A4 sheet. The rule: diamonds for questions, arrows labelled yes/no, rectangles for outcomes. His story must have at least three decisions deep, at least one win, at least three losses.

For him specifically: this is where the drawing habit becomes a programming tool. The flowchart is not preparation for the real work — it *is* the design. When he later gets a bug, the fix is usually "look at the flowchart".

Take a photo of the flowchart for the repo.

### Guided build (33 min)

Follow web §9 steps 1–4. He types, you ask questions. **Run after every step.**

- **Step 1** — the intro and ASCII art. Show him `r'''` and why the `r` is there (backslashes). Let him draw his own art; five minutes maximum or it eats the session.
- **Step 2** — first decision. Run it with `left`, `Left`, `LEFT`. Ask why `.lower()` is there.
- **Step 3** — nest the second decision. The moment to watch: does he indent the second `if` under the first? If the second `if` is at the left margin, stop and ask "when should this question be asked?"
- **Step 4** — `elif` for the three doors, plus the catch-all `else`. Ask: "What happens if the player types 'green'?" — and make him test it.

Then hand it over: **his story replaces the skeleton.** Keep the structure, change every string. Greek messages are fine — the code stays English, the story is his.

**Two traps worth walking into deliberately:**
- Forget the colon after an `if`. Read the `SyntaxError` together — Python points at the line, and the fix is one character.
- Put an `elif` after the `else`. `SyntaxError: invalid syntax`. "Which one is always last?"

---

## 8. Independent exercises (16 min)

**You do not touch the keyboard.** Five-minute struggle timer, then *read the error message out loud together* before anything else.

- **Α0 Odd or Even** — mandatory, two minutes.
- **Α2 Leap Year** — mandatory. Flowchart first. Test with 2024, 1900, 2000. If he gets 1900 wrong, his nesting is wrong, and the flowchart will show him where.
- Then two of: **Α1** water state, **Α3** pizza, **Α4** love calculator, **Α5** zoo ticket.

**Α4 note:** the Love Calculator is Angela's; it's the one that introduces `.lower()` and `.count()`, which is why it's here. "Angela Yu" + "Jack Bauer" → 53. Suggest he try two characters from a game instead of real people.

**Outside sources:** CodingBat → Python → **Logic-1** is exactly today's material with instant feedback. `cigar_party`, `date_fashion`, `squirrel_play`. No login.

---

## 9. Creative closer — Turtle shape picker (12 min)

Web §11. The user picks a shape and a colour; the turtle decides with `if / elif`.

Type it, run it, then **hand it over.** A fourth shape, a size parameter, "both". The bit to point at: the star is the same two lines five times. Say "Day 5 will fix that" and nothing more — it's the hook for loops.

**Wrap-up for the project:** commit, and get him to show the Treasure Island to someone at home tonight and watch them play it. That's the "share and show off" step from the course, and it matters more than it looks — it's the first time his code has a user.

---

## 10. AI corner — optional 10 min

Web §12. ELIZA, 1966, a pile of `if`s. He builds a five-rule chatbot with `in` (new operator, small, worth having). Then the real question: *how many `elif`s would you need to understand any sentence?* The answer — "never enough" — is why modern AI isn't rules written by hand but rules **learned from examples**. That's the cleanest one-sentence definition of machine learning he'll get, and it comes out of his own frustration with the chatbot.

Akinator (five minutes, in Greek at el.akinator.com) is a decision tree with millions of diamonds — literally today's flowchart at scale.

---

## 11. Recap & wrap-up (10 min)

1. **Explain-back (4 min).** He walks you through his Treasure Island, in Greek, decision by decision, with the flowchart next to him. Any branch he can't explain becomes a journal question.
2. **Checklist (2 min).** Web §14. He ticks only what he can do without notes. Note which ones stay unticked — that's next week's recall.
3. **Commit (2 min).** `treasure_island.py`, `shape_picker.py`, his exercise files, and the flowchart photo. Message: `Day 3 - treasure island and shape picker`.
4. **Journal (2 min).** One line: *"Σήμερα έμαθα…"*

**Score privately (1–4 each):** works · readability · independence · creativity · explanation. Creativity should score high today if the story is his.

**Next session opens with:** three recall questions from the recap card, and he re-types the pizza order's size block from memory — it's the `elif` pattern he'll use for the rest of the year.

---

## 12. Errors to expect — and what to say

| Error | Cause | What to say |
|---|---|---|
| `SyntaxError` at the `if` line | Missing `:` or used `=` | "What's the last character on that line?" / "Are you giving a value or asking a question?" |
| `IndentationError: expected an indented block` | No indent after `if` | "How does Python know what belongs to the if?" |
| `IndentationError: unindent does not match` | Mixed 3 and 4 spaces | "Count the spaces on this line and the one above." |
| `TypeError: '>' not supported between 'str' and 'int'` | Forgot `int()` | "What type is that variable right now?" |
| The `else` runs on correct input | `"Left"` vs `"left"` | "What exactly did the user type? Print it and look." |
| `or` always true | `x == 3 or 5` | "Is `5` on its own true or false? Try `print(bool(5))`." |
| Two messages print | Two `if`s where he wanted `elif` | "Did you want one answer, or all the answers that fit?" |
| `SyntaxError` at `elif` | `elif` after `else` | "Which branch is always last?" |

---

## 13. Between sessions (~45 min total, 3 × 15)

- CodingBat **Logic-1**, first five problems.
- Finish the Treasure Island story properly — at least five endings.
- Optional: the ELIZA chatbot with ten rules. Bring the sentence that broke it.
