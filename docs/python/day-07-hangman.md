# Day 7 — Hangman
### Weeks 8–9 · Two sessions · 2 × 2h 30min · Thonny or Replit

> **Language convention:** this file is the tutor plan, in English, for you. The student-facing material is the web page `day-07.html` (Greek, with English code), which is what he works from during the session.
>
> **What kind of day this is:** the first *project day* — no new syntax at all. Everything in Hangman is Days 2–6 material. That is the point and you should say so at the start: today is about assembling, not learning. It is harder than it sounds, which is why it gets two sessions. Session A ends with a game that can be won (Steps 0–3). Session B ends with a game worth showing someone (Steps 4–5, turtle, AI corner).

---

## 1. Learning objectives

By the end of the two sessions he should be able to:

1. Turn a game's rules into a flowchart, and the flowchart into a five-step build plan — **before** typing.
2. Build in increments of at most ten lines and run after each; say why that keeps bugs findable.
3. Keep game *state* in variables outside the loop (`display`, `lives`, `end_of_game`) and explain what goes before the loop vs inside it.
4. Use a **flag** (`end_of_game`) to end a `while` loop, and say what flips it.
5. Use **parallel lists** — `chosen_word[position]` and `display[position]` — and explain why the loop runs over positions, not letters.
6. Create his **own module** (`hangman_words.py`) and `from … import` it; fix `ModuleNotFoundError` by checking folder and filename.
7. Draw the gallows with turtle, one function per lost life, and explain the `if lives == 5 / 4 / 3…` chain.

**Prerequisite check:** Day 6's `while` with a flag, Day 4's list indexing, Day 3's `in`. The Session A warm-up re-types the "until stop" loop from Day 6 Α4 — it is structurally identical to Hangman's game loop.

---

## 2. Coverage map — this plan vs. the Udemy Day 7

| Udemy section | Covered here | Note |
|---|---|---|
| Day 7 Goals (Hangman demo) | §4 **Goals demo** | You play the finished game; lose once |
| Flowchart / how to break the problem down | web §2 **Βήμα 0** | ✓ rules → flowchart → five steps |
| Step 1 — random word, check guess | web §3 + exercise **Α0** | ✓ with the `Pssst` debug print named as a technique |
| Step 2 — replace blanks with guessed letters | web §4 + exercise **Α1** | ✓ parallel lists, the positions table |
| Step 3 — check if the player has won | web §6 + exercise **Α2** | ✓ `while not end_of_game`, `"_" not in display` |
| Step 4 — keep track of lives | web §7 + exercise **Α3** | ✓ `lives -= 1`, the nested `if lives == 0` |
| Step 5 — improve the UI (ASCII art, word list, already-guessed) | web §9 | ✓ split into 5α–5δ: stages, own modules, already-guessed, `join` |

**Beyond the course:** the explicit flowchart step, the "run after every step" rule stated as the day's discipline, the "before vs inside the loop" distinction tied back to Day 5's accumulator bug, parallel lists named and tabled, the hint exercise (Α4) that previews dictionaries, the Greek variant (Α5) and its accent problem, the turtle gallows built from Day 6 functions, the letter-frequency AI corner with its English-vs-Greek comparison and the self-playing computer, the error table, recap card and checklist.

**On the game itself:** Hangman is the course's project and it's a classic for a reason — the state is small, every rule maps to one `if`, and the ASCII stages give visible progress. The turtle section explicitly invites him to replace the figure with anything in six stages (a flower losing petals, a rocket). If you'd rather not use the gallows imagery at all, start from the turtle section with his own six-stage figure and skip 5α; nothing else depends on it.

---

## 3. Session timelines

### Session A — a game that can be won (Week 8)

| Time | Block | What happens |
|---|---|---|
| 0:00–0:03 | **Goals demo** | You play the finished game. Win one, lose one. |
| 0:03–0:12 | **Warm-up** | Day 6 recall + the "until stop" loop from memory |
| 0:12–0:30 | **Βήμα 0** | Rules → flowchart on A4 → the five steps written as a list |
| 0:30–0:45 | **Βήμα 1** | Random word, one guess, Right/Wrong per letter. Run. |
| 0:45–1:08 | **Βήμα 2** | `display` list, the positions loop, the table on paper. Run. |
| 1:08–1:12 | ✅ **Checkpoint 1** | Web quiz 1 |
| 1:12–1:22 | **Break** | Away from the screen |
| 1:22–1:50 | **Βήμα 3** | `while not end_of_game`, win check. Run, play, win. |
| 1:50–2:15 | **Independent** | Α0 → Α1 → Α2 from a blank file, page closed |
| 2:15–2:25 | **Play-test** | He plays his own game three times; you play it once and try to break it |
| 2:25–2:30 | **Wrap-up** | Checklist items 1–4, commit, journal |

### Session B — a game worth showing (Week 9)

| Time | Block | What happens |
|---|---|---|
| 0:00–0:12 | **Recall** | Three questions from the recap card; he re-types Βήμα 3's loop from memory |
| 0:12–0:35 | **Βήμα 4** | Lives, lose condition, deliberate loss. Run. |
| 0:35–0:40 | ✅ **Checkpoint 2** | Web quiz 2 |
| 0:40–1:15 | **Βήμα 5** | 5α stages → 5β own modules → 5γ already-guessed → 5δ `join`, delete `Pssst` |
| 1:15–1:25 | **Break** | Away from the screen |
| 1:25–1:45 | **Independent** | Α4 hint (parallel lists again) or Α5 Greek variant — his choice |
| 1:45–2:10 | **Creative closer** | Turtle gallows: `hangman_turtle.py`, six functions, the `elif` chain |
| 2:10–2:22 | **AI corner** | Letter frequency, English vs Greek, the self-playing computer |
| 2:22–2:30 | **Recap & wrap-up** | Explain-back, checklist 5–8, commit, journal, show someone tonight |

---

## 4. Goals demo (3 min)

Play your finished `hangman.py` — with stages, with the word list in its own file. Win one. Then lose one on purpose so he sees the full figure and the "You lose. The word was…" line. Say nothing about the code. Close with: *"Σήμερα το φτιάχνεις από το μηδέν. Και δεν θα μάθεις τίποτα καινούριο — τα ξέρεις ήδη όλα."*

That last sentence does two things: it lowers the anxiety and it raises the bar.

---

## 5. Warm-up — Session A (9 min)

**Recall from Day 6 (3 min).** No notes: What's the difference between `greet` and `greet()`? What stops a `while` loop? What was wrong when Reeborg circled forever?

**From memory (6 min).** He re-types Day 6's Α4:

```python
answer = ""
while answer != "stop":
    answer = input("...")
```

Keep it visible. In an hour, `answer != "stop"` becomes `not end_of_game` and this is the game loop. If he can't produce this, do it together now — Βήμα 3 depends on it entirely.

---

## 6. The build — Session A

### Βήμα 0: the plan (18 min) — do not skip, do not shorten

Web §2. He writes the rules of Hangman in his own words (Greek). Then the flowchart on A4 — the "όσο δεν έχει τελειώσει" diamond, with two diamonds inside it. Then, under the flowchart, five numbered steps.

Then the translation exercise, out loud: "What is this diamond in Python?" — `while`. "These two?" — `if`. "The blanks?" — a list. "Pick a word?" — `random.choice`. **The program is already written on the paper.** Say exactly that. Photo for the repo.

State the day's rule and write it at the top of the paper: *run after every step; never more than ten lines without pressing Run.*

### Βήμα 1 (15 min)

Web §3. Twelve lines. The `Pssst` debug print — name it as a technique: "a `print` that shows you what's inside, so you can check the program is behaving. You'll delete it at the end." This is his first deliberate debugging tool and it's worth the thirty seconds.

Run with `python` and guess `o` → `Wrong Wrong Wrong Wrong Right Wrong`. "Does it know *where* the `o` is?" It does — the fifth answer. That's Βήμα 2's whole idea.

### Βήμα 2 (23 min)

Web §4. This is the conceptual centre of the day. The `display` list, built with one `append("_")` per letter — then the replacement loop.

**The question to ask before showing the code:** "To put the `o` in the right place in `display`, what do you need to know?" — *where it is.* "Does `for letter in chosen_word` tell you where?" — no. "What does?" — the position. That's why the loop becomes `for position in range(word_length)`.

Fill in the §4 table on paper together for `python` / `o`. Then for `turtle` / `t` — two hits. The point: the positions loop finds *all* occurrences because it checks every position; it doesn't stop at the first.

**Modify (his turn, 5 min):** "Make it work for a word with a repeated letter." He runs `turtle`, guesses `t`, sees both. If only one shows, he compared the wrong thing — look at it together.

### ✅ Checkpoint 1 — web quiz 1 (4 min)

He wants 3/4. Question 3 (why `position` not `letter`) is the one.

### Βήμα 3 (28 min)

Web §6. Wrap it in `while not end_of_game`. Three things to land, in order:

1. **The flag.** `end_of_game = False` before; something inside flips it to `True`; the `while` checks it every round. Same shape as `answer != "stop"`.
2. **The win check.** `"_" not in display` — "is there any blank left?" If not, win, flag flips.
3. **Before vs inside.** The word and the blanks are made *once*. The guess and the replacement happen *every round*. Have him move `display = []` inside the loop and play — the blanks reset every guess. "Where did you see this bug before?" — Day 5, `total = 0` inside the loop. Same disease.

Then he plays it to a win. **That's a game.** Point it out. If this is where the session ends, it ends on a working product — commit it.

### Independent (25 min) — page closed

**You do not touch the keyboard.** He rebuilds Α0 → Α1 → Α2 in a fresh file with the page closed. Five-minute struggle timer, then *read the error aloud together*. He may look at his own flowchart as much as he wants — that's what it's for.

### Play-test (10 min)

He plays three times. Then you play once and **try to break it**: guess a letter twice, guess a capital letter, guess two letters at once, guess a number. Note what happens — don't fix anything. These are tomorrow's Βήμα 5 and the error table.

**Wrap-up:** checklist 1–4, commit (`Day 7A - hangman core`), journal.

---

## 7. The build — Session B

### Recall (12 min)

Three questions from the recap card. Then he re-types Βήμα 3's loop from memory. If `end_of_game` or the win check is missing, that's the first ten minutes.

### Βήμα 4: lives (23 min)

Web §7. `lives = 6`, `lives -= 1` on a wrong guess, lose at zero. The structural point: `if lives == 0` lives *inside* `if guess not in chosen_word` — lives can only hit zero on the turn you lose one. Ask "do we need to check for zero on every turn?" and let him reason to no.

**Walk into the bug on purpose:** put `if guess not in chosen_word` *inside* the positions `for`. Now a correct guess costs five lives (one per non-matching position). Let him see it, then ask which level it belongs at. This is the indentation rule from Day 6 §5 with real consequences.

He plays to lose, then to win, then guesses the same correct letter twice — nothing bad happens, nothing useful either. That's 5γ.

### ✅ Checkpoint 2 — web quiz 2 (5 min)

He wants 4/5. Question 4 (`stages[lives]` with lives=6) and 5 (`in display` vs `in chosen_word`) are the ones.

### Βήμα 5: finishing (35 min)

Web §9, four sub-steps, each a few lines:

- **5α stages.** The list is backwards on purpose — index 6 is the empty gallows, index 0 the full figure — so `stages[lives]` works with no arithmetic. Ask "why not put them in order and write `stages[6 - lives]`?" Both work; the backwards list is simpler to *read*. The `\\` in the art: one sentence, callback to Day 3's `r'''`.
- **5β own modules.** The first time he *makes* a module. New file `hangman_words.py` in the same folder, `from hangman_words import word_list`. Then the same for `hangman_art.py`. The main file shrinks to one screen — point at it. The two errors to expect are in §13: wrong folder, or a hyphen in the filename.
- **5γ already-guessed.** `if guess in display:` — and the question *why `display` and not `chosen_word`* is quiz 2 Q5. If he can answer it, he understands what `display` represents.
- **5δ `join`.** Day 5's "for later" — now. `" ".join(display)`. Then **delete `Pssst`**. The game is finished.

Have him open the Βήμα 1 file next to the final one. Twelve lines to a game with modules, never more than ten lines at a time. That's the lesson of the day.

### Independent (20 min)

His choice of **Α4** (hint via parallel lists — `randint` for the index so both lists line up; a genuine preview of why dictionaries exist) or **Α5** (Greek word list — the accent problem is real and he should hit it: `ή` ≠ `η`. The fix, words without tonos, is one sentence; the discovery is worth more than the fix).

### Creative closer: the turtle gallows (25 min)

Web §11. `hangman_turtle.py` with `draw_gallows()` and six part-functions, imported into the game; the `elif lives == 5 / 4 / 3 / 2 / 1 / 0` chain where lives are lost. Day 6's brushes, Day 3's `elif`, Day 7's game — three days in one file.

The Thonny gotcha: the turtle window and the shell are separate; the window looks "frozen" while `input()` waits in the shell. One sentence saves confusion.

**Then hand it over:** the figure doesn't have to be a person. The page suggests a flower losing petals, a rocket assembled in reverse, a turtle retreating into its shell. Six stages, six functions, his theme. If there's time, `display` as `pen.write()` under the picture.

### AI corner (12 min)

Web §12. Two loops and an accumulator — Day 5 — count each letter across the word list. With the page's fifteen words: `t`, `r`, `o`, `e`, `a` lead. Say the word: **model** — a summary of data that tells you what to expect, measured, not told.

Then the same code with the Greek list and Greek alphabet: `α` far ahead, then `τ`, `ρ`, `ο`, `λ`. "If a computer player had only ever seen English words and played Greek, what would it guess first?" — `e`, which doesn't exist. Day 5's κουλούρι, now with numbers.

**The self-playing computer** (page's final note): replace `input()` with a frequency-ordered string and a counter. The game plays itself and usually wins. He just built a player that learned from data — the simplest AI there is. If he's engaged, let this run over; it's the best ten minutes of the two sessions.

---

## 8. Recap & wrap-up (8 min)

1. **Explain-back (3 min).** He explains Βήμα 2 — why positions, not letters — and Βήμα 5β — what `from hangman_words import word_list` does. In Greek, with the flowchart next to him.
2. **Checklist (1 min).** Items 5–8.
3. **Commit (2 min).** `hangman.py`, `hangman_words.py`, `hangman_art.py`, `hangman_turtle.py`, `hangman_words_gr.py` if done, the flowchart photo. Message: `Day 7B - hangman with lives, modules and turtle`.
4. **Journal (1 min).** *"Σήμερα έμαθα…"*
5. **Show someone tonight.** This is the course's "share and show off" step and it matters more here than on any previous day — it's the first thing he's made that someone else can *play* without him explaining it. Watch them play; note what confuses them. That's user testing.

**Score privately (1–4 each):** works · readability · independence · creativity · explanation. Independence should be the high score today.

**Next session opens with:** three recall questions, and he re-types the game loop skeleton (flag, `while`, win/lose flips) — Day 8 adds parameters, and `jump_to(x, y)` from Day 6 finally gets explained.

---

## 9. Errors to expect — and what to say

| Error | Cause | What to say |
|---|---|---|
| Blanks reset every guess | `display = []` inside the `while` | "Day 5. Where does the accumulator live?" |
| Only the first of two same letters found | Loop over letters, not positions | "Which position are you writing to?" |
| `IndexError: list assignment index out of range` | `display` shorter than the word | "How many blanks did you make? Count the appends." |
| Game never ends | Flag never flips / win check missing | "What flips `end_of_game`? Is that line ever reached?" |
| Correct guess costs lives | `if guess not in chosen_word` inside the positions `for` | "Which level does that `if` belong at? Trace one round." |
| `ModuleNotFoundError` | Wrong folder or hyphen/space in filename | "Same folder? Underscore, not hyphen?" |
| `ImportError: cannot import name` | Variable in the module named differently | "What's the list called *inside* `hangman_words.py`?" |
| Wrong stage shown | List in forward order | "With 6 lives, which index do you want? What's at index 6?" |
| Greek letter not found | Tonos: `ή` ≠ `η` | "Are those the same character? Print `ord()` of each if he's curious." |
| Turtle window frozen | Waiting for `input()` in the shell | "It's not frozen — who's it waiting for?" |
| `print(display)` shows brackets | Needs `join` | "Day 5's 'for later'. It's later." |

---

## 10. Between sessions

**After Session A (~45 min, 3 × 15):**
- Rebuild Βήματα 1–3 from the flowchart alone, page closed, in a fresh file. Time it.
- Write ten more words into a list for next week; think of a theme.
- Optional: play the game with someone and write down one thing they found confusing.

**After Session B (~45 min, 3 × 15):**
- "Play again?" loop around the whole game (Day 6 Α4 shape) — five lines.
- The six-stage turtle figure with his own theme, finished and screenshotted for the README.
- Optional: the self-playing computer with the Greek frequency order and Greek words. Does it still win?
