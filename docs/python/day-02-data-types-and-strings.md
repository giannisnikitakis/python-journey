# Day 2 — Understanding Data Types & Manipulating Strings
### Week 2 · One session · 2h 30min · Thonny

> **Language convention:** Part A (the tutor plan) is in English, for you. Part B (the student handout, from §7 onward) is in Greek with English code and technical terms, ready to print or paste into a doc for him.
>
> **Swap in his name** wherever the examples use `"Odysseas"`.

---

## 1. Learning objectives

By the end of the session he should be able to:

1. Name and recognise the four primitive types: `str`, `int`, `float`, `bool`.
2. Use `type()` to inspect a value, and explain *why* `input()` always gives back a `str`.
3. Convert between types with `int()`, `float()`, `str()` — and predict when a `TypeError` or `ValueError` will happen.
4. Access individual characters with subscripting (`name[0]`, `name[-1]`) and get length with `len()`.
5. Use `+ - * / // % **` and know the order of operations.
6. Format numbers with `round()` and produce clean output with **f-strings**.
7. Ship a working **Tip Calculator** and a **Turtle poster** that he chose the look of.

**Prerequisite check:** he needs Day 1 (variables, `input()`, `print()`, string concatenation). The warm-up tests this — if it collapses, spend 25 minutes re-doing Day 1 and push Day 2's project to next week. That is a fine outcome, not a failure.

---

## 2. Coverage map — this plan vs. the Udemy Day 2

| Udemy section | Covered here | Note |
|---|---|---|
| 13. Day 2 Goals (2min) | §3 **Goals demo** | Added — show the finished product first |
| 14. Python Primitive Data Types (8min) | §5 Predict/Run/Investigate | ✓ |
| **Quiz 2: Data Types Quiz** | §5.4 **Checkpoint 1** | Added — 6 questions |
| 15. Type Error, Type Checking, Type Conversion (14min) | §5.2 The casting fix | ✓ + `ValueError` vs `TypeError` |
| 16. Mathematical Operations (10min) | §5.5 | ✓ |
| **Coding Exercise 4: BMI Calculator** | §7 **E0 — Average Speed** | Swapped, same skill |
| 17. Number Manipulation & F-Strings (8min) | §5.6 | ✓ + `:.2f` for money |
| **Quiz 3: Mathematical Operations Quiz** | §5.7 **Checkpoint 2** | Added — 5 questions |
| 18. Day 2 Project: Tip Calculator (15min) | §6 | ✓ built in 4 stages |
| 19. You are already in the top 50% (1min) | §11 Recap, progress marker | ✓ |

**Beyond the course:** Parson's warm-up, subscripting practice, the turtle poster, the AI corner, the error table, and the recap sheet.

**On the BMI exercise (E0):** it's a two-float-input, one-division, `round()` problem — mechanically identical to average speed. I'd rather he not spend his second-ever lesson computing his own body metrics at 13. Nothing lost technically; use whichever you prefer.

---

## 3. Session timeline

| Time | Block | What happens |
|---|---|---|
| 0:00–0:03 | **Goals demo** | You run the finished Tip Calculator — "this is what we build today" |
| 0:03–0:15 | **Warm-up** | Parson's problem + the deliberate `TypeError` |
| 0:15–0:33 | **Concept A** | Types, `type()`, subscripting |
| 0:33–0:37 | ✅ **Checkpoint 1** | Data Types quiz |
| 0:37–0:52 | **Concept B** | Casting, maths operators, `round()`, f-strings |
| 0:52–0:56 | ✅ **Checkpoint 2** | Maths quiz |
| 0:56–1:06 | **Break** | Away from the screen |
| 1:06–1:48 | **Guided build** | Tip Calculator, in four stages |
| 1:48–2:06 | **Independent challenge** | He works alone; you coach only |
| 2:06–2:20 | **Creative closer** | Turtle poster — his design |
| 2:20–2:30 | **Recap & wrap-up** | Recap sheet, explain-back, commit, journal |

Optional **AI corner (10 min)** — drop it in before the recap if you're running ahead. See §9.

---

## 3b. Goals demo (3 min)

Before any theory, **you** run the finished `tip_calculator.py` in front of him. Type in a bill of €47.50, 12%, 3 people. Let it print the answer.

Then close it and say: *"Σήμερα το φτιάχνουμε αυτό."*

Angela Yu opens every day this way and it's the right instinct — a 13-year-old will sit through fifteen minutes of type conversion much more willingly once he knows what it's *for*. Do not explain any of the code. Just show it working.

---

## 4. Warm-up (12 min)

**Parson's problem.** Give him these lines on paper, jumbled, and ask him to put them in the right order *before* touching the keyboard:

```python
print("Hello " + name + "!")
name = input("What is your name? ")
print("Welcome to Day 2.")
```

Then, one prediction question — ask him to say the answer out loud before running it:

```python
a = "7"
b = 3
print(a + b)
```

He will probably say `10`. Let him run it and meet his first deliberate `TypeError`. **Do not explain it yet** — say "hold that thought, that's exactly what today is about." This is the hook for the whole session.

---

## 5. New concept — PRIMM (37 min, in two halves)

### Predict → Run → Investigate

Type this in together, but have him **predict each line's output** before you run the file:

```python
name = "Odysseas"
age = 13
height = 1.62
is_student = True

print(type(name))
print(type(age))
print(type(height))
print(type(is_student))

print(len(name))
print(name[0])
print(name[3])
print(name[-1])
```

**Investigate — the four points to land (in Greek, out loud):**

- `str` is text and always lives inside quotes. `"13"` is *not* the number 13.
- `int` is a whole number, `float` has a decimal point. `7 / 3` always gives a `float`, even `6 / 3` → `2.0`.
- `bool` is only ever `True` or `False` — capital letter, no quotes.
- Subscripting counts **from zero**. `name[0]` is the first letter. Negative numbers count backwards from the end.

### ✅ Checkpoint 1 — Data Types quiz (4 min)

Ask these out loud. No keyboard, no notes. He should get 5/6 before you move on.

1. What type is `"13"`? → `str` (it's in quotes)
2. What type is `7 / 3`? → `float` — division **always** gives a float
3. What type does `input()` always return? → `str`, always
4. What is `name[0]` if `name = "Python"`? → `"P"`
5. `True` or `true` — which one works? → `True`, capital T, no quotes
6. What type is `3.0`? → `float`, even though it looks whole

**If he misses 3 or more, re-do the Predict/Run block before continuing.** Getting `input()` → `str` wrong will wreck the Tip Calculator later.

---

### The casting fix

Go back to the warm-up error and fix it properly:

```python
two_digit_number = input("Type a two-digit number: ")
first_digit = int(two_digit_number[0])
second_digit = int(two_digit_number[1])
total = first_digit + second_digit
print(total)
```

Ask him to break it deliberately: what happens if he types `abc`? That's a `ValueError`, and it's a different animal from a `TypeError`. Knowing the difference is a real skill.

### Modify (his turn, 8 min)

Give him one instruction only: *"Change it so it works with a three-digit number and also prints the middle digit on its own line."*

### Maths and formatting

```python
print(7 + 3)
print(7 - 3)
print(7 * 3)
print(7 / 3)     # 2.3333333333333335  → always a float
print(7 // 3)    # 2   floor division
print(7 % 3)     # 1   modulo (the remainder)
print(7 ** 3)    # 343 exponent

print(3 * 3 + 3 / 3 - 3)   # ask him to predict this one
```

That last line is `7.0`. Multiplication and division happen before addition and subtraction — same rule as maths class.

Then rounding and f-strings:

```python
score = 8 / 3
print(score)
print(round(score, 2))
print(f"Your score is {score:.2f} points")
print(f"{name} is {age} years old and {height}m tall")
```

**The f-string is the single most useful thing in this session.** Make sure he notices the `f` before the quote — forgetting it is the most common error he'll hit for the next month.

### ✅ Checkpoint 2 — Maths quiz (4 min)

Predict, then verify in the shell together:

1. `print(6 / 3)` → `2.0` (not `2` — it's a float)
2. `print(7 // 2)` → `3`
3. `print(7 % 2)` → `1`
4. `print(2 ** 5)` → `32`
5. `print(2 + 3 * 4)` → `14`, not `20`
6. `print(round(3.14159, 3))` → `3.142`

**Bonus, worth asking:** what's the difference between `round(x, 2)` and `f"{x:.2f}"`? (One changes the *number*, the other changes how it's *displayed*.) If he can answer that, he's ahead of most adults learning Python.

---

## 6. Guided build — the Tip Calculator (42 min)

He types, you explain. Build it in four stages and **run it after every stage** so it's never broken for more than five minutes.

**Stage 1 — collect the inputs.**

```python
print("Welcome to the tip calculator!")
bill = float(input("What was the total bill? €"))
tip = int(input("What percentage tip would you like to give? 10, 12, or 15? "))
people = int(input("How many people to split the bill? "))
```

Ask: why `float()` for the bill but `int()` for the number of people? (Because a bill can be €47.50, but you can't have 2.5 people.)

**Stage 2 — do the maths.**

```python
tip_as_percent = tip / 100
total_tip_amount = bill * tip_as_percent
total_bill = bill + total_tip_amount
```

**Stage 3 — split it.**

```python
bill_per_person = total_bill / people
print(bill_per_person)
```

Let him see the ugly `15.333333333333334`. *Then* ask him how to fix it. He should reach for `round()` himself.

**Stage 4 — clean output.**

```python
final_amount = round(bill_per_person, 2)
print(f"Each person should pay: €{final_amount}")
```

**Two traps worth walking into deliberately:**
- `round(15.5)` gives `16`, but `round(2.5)` gives `2`. Python rounds half-to-even. Worth thirty seconds of "computers are weird sometimes."
- `round(15.30, 2)` prints `15.3`, not `15.30`. Show him `f"€{bill_per_person:.2f}"` as the proper fix for money.

---

## 7. Independent challenge (18 min)

**You do not touch the keyboard for these.** Set a five-minute struggle timer: if he's stuck, first step is *read the error message out loud together*, not "let me see."

**E0 — Average Speed** *(do this one; it's the course's coding-exercise slot).* Ask for a distance in kilometres and a time in hours, both as decimals. Print the average speed rounded to 1 decimal place.
*Target output:* `Your average speed is 12.4 km/h.`
*Skills: two `float()` casts, one division, `round()`, one f-string — exactly the shape of the Udemy exercise.*

Then pick two more:

**E1 — Life in Weeks.** Ask for his age, then print how many days, weeks and months he has left if he lives to 90.
*Target output:* `You have 28105 days, 4004 weeks, and 924 months left.`

**E2 — Pizza night.** A pizza costs €8.50, each extra topping €1.20, delivery €2.50. Ask how many pizzas and how many toppings, then print the total, split between the number of people ordering, rounded to 2 decimals.

**E3 — Initials.** Ask for his full name (first and last), then print just the initials, e.g. `O.N.` *Hint: subscripting.*

**E4 — Seconds alive.** Ask for age in years and print roughly how many seconds he's been alive, formatted with a comma separator: `f"{seconds:,}"`.

**E5 — Century club.** Ask for his name and age, then print the year he'll turn 100.

**Outside sources, if you want more (all free):**
- **CodingBat → Python → String-1**: `hello_name`, `first_two`, `last_two`, `make_abba`, `make_tags`. Instant feedback, no login. https://codingbat.com/python
- **PracticePython.org → Exercise 1 (Character Input)**. https://www.practicepython.org
- **futurecoder.io** — the strings chapter, if he wants to potter about alone during the week.

---

## 8. Creative closer — Turtle poster (14 min)

This is the payoff. Everything he learned today, but the output is something he designed.

```python
import turtle

name = input("What is your name? ")
favourite_number = int(input("What is your favourite number (1-20)? "))

side = favourite_number * 10

pen = turtle.Turtle()
pen.pensize(4)
pen.color("purple")

pen.forward(side)
pen.left(90)
pen.forward(side)
pen.left(90)
pen.forward(side)
pen.left(90)
pen.forward(side)
pen.left(90)

pen.penup()
pen.goto(-100, -120)
pen.pendown()
pen.write(f"{name} · {side}px", font=("Arial", 18, "normal"))

turtle.done()
```

**Then hand it over completely.** His choices: the colour, the shape, the font, the message, what the number controls. Let him break it. This is where the artistic side gets to lead, and it's the bit he'll want to show someone.

---

## 9. AI corner — optional 10 min

Connects today's material to the AI thread without any code.

Open a tokenizer visualiser (e.g. https://tiktokenizer.vercel.app) and type his name, then a Greek sentence, then a made-up word.

**The conversation:** today we learned Python breaks a string into individual characters — `name[0]`, `name[1]`. AI language models do something similar, but they cut the text into bigger chunks called **tokens**, and each token becomes a number. That's the whole trick: the model never sees letters, only numbers.

**Ask him:** why does Greek use more tokens than English for the same sentence? (Because these models saw far more English text while training.) That's a first, concrete taste of what "bias in the training data" actually means — and it's a much better hook than an abstract definition.

---

## 10. Recap & wrap-up (10 min)

Run these four in order. Don't skip the first one — it's the part that makes the lesson stick.

1. **Explain-back (4 min).** He explains the Tip Calculator to you line by line, in Greek, as if you'd never seen it. Any line he can't explain goes straight into the journal as a question for next week.
2. **Hand him the recap sheet (2 min).** The one-pager at the end of Part B. Read the three "big ideas" together, out loud. He keeps it — it's his reference for Days 3–5, which all build on this.
3. **Commit (2 min).** `day02_tip_calculator.py`, `day02_poster.py` and his exercise files into the repo. Commit message in plain words: `Day 2 - tip calculator and poster`.
4. **Journal + progress marker (2 min).** One line: *"Σήμερα έμαθα…"* Then the motivational beat the course does at this point — tell him plainly: most people who start learning to code stop before they finish a second project. He now has two, and they both work.

**Score the session privately on the rubric (1–4 each):** works · readability · independence · creativity · explanation. Don't show him the scores — they're your tracking, not his grade.

**Next session opens with a 5-minute recall:** hand back the recap sheet, ask three questions from it, and get him to re-type the tip calculator's first three lines from memory. Spaced recall a week later is what moves this from "we did that" to "I know that."

---

## 11. Errors to expect — and what to say

| Error | Cause | What to say (don't fix it for him) |
|---|---|---|
| `TypeError: can only concatenate str (not "int") to str` | Adding a number to text | "What type is each side of that `+`?" |
| `ValueError: invalid literal for int()` | `int("abc")` or `int("4.5")` | "Read what it says it got. Can that be a whole number?" |
| Prints `15.3` not `15.30` | `round()` drops trailing zeros | "Round is for maths. What tool do we have for *display*?" |
| `IndexError: string index out of range` | `name[8]` on a 5-letter name | "How long is that string? What's the biggest index that exists?" |
| Prints `{name}` literally | Missing the `f` | Just point at the quote mark and wait. |
| `SyntaxError` at `print` | Missing closing bracket on the line *above* | "Python points at where it noticed. Look one line up." |

---

## 12. Between sessions (~45 min total, 3 × 15)

- CodingBat **String-1**, first five problems.
- Finish any unfinished exercise from §6.
- Optional: redesign the turtle poster properly. No rules.

---
---

# ΜΕΡΟΣ Β — Φύλλο Εργασίας Μαθητή
## Ημέρα 2: Τύποι Δεδομένων & Strings

### Οι τέσσερις βασικοί τύποι δεδομένων

| Type | Τι είναι | Παράδειγμα |
|---|---|---|
| `str` | **String** — κείμενο, πάντα μέσα σε εισαγωγικά | `"Οδυσσέας"` |
| `int` | **Integer** — ακέραιος αριθμός | `13` |
| `float` | Δεκαδικός αριθμός | `1.62` |
| `bool` | **Boolean** — μόνο `True` ή `False` | `True` |

Με τη συνάρτηση `type()` ρωτάς την Python τι τύπος είναι κάτι:

```python
print(type("Οδυσσέας"))   # <class 'str'>
print(type(13))           # <class 'int'>
```

> ⚠️ Το `"13"` **δεν** είναι ο αριθμός 13. Είναι κείμενο. Δεν μπορείς να κάνεις πράξεις μαζί του.

### Type conversion (casting)

Η `input()` σου δίνει **πάντα** `str`, ακόμα κι αν πληκτρολογήσεις αριθμό. Γι' αυτό πρέπει να τον μετατρέψεις:

```python
age = input("Πόσων χρονών είσαι; ")   # αυτό είναι str!
age = int(age)                        # τώρα είναι int
```

Οι τρεις μετατροπές που θα χρησιμοποιείς: `int()`, `float()`, `str()`.

### Subscripting — πιάνω ένα γράμμα

Η αρίθμηση **ξεκινάει από το 0**, όχι από το 1.

```python
name = "Odysseas"
print(name[0])    # O   (το πρώτο γράμμα)
print(name[3])    # s
print(name[-1])   # s   (το τελευταίο)
print(len(name))  # 8   (πόσα γράμματα έχει)
```

### Μαθηματικές πράξεις

```python
7 + 3     # 10
7 - 3     # 4
7 * 3     # 21
7 / 3     # 2.3333...  → δίνει ΠΑΝΤΑ float
7 // 3    # 2          → floor division, κόβει τα δεκαδικά
7 % 3     # 1          → modulo, το υπόλοιπο
7 ** 3    # 343        → δύναμη
```

**Σειρά πράξεων:** πρώτα `**`, μετά `*` και `/`, στο τέλος `+` και `-`. Όπως στα μαθηματικά. Οι παρενθέσεις έχουν πάντα προτεραιότητα.

### Στρογγυλοποίηση & f-strings

```python
score = 8 / 3

print(round(score, 2))            # 2.67
print(f"Έχεις {score:.2f} πόντους")   # Έχεις 2.67 πόντους
```

Το **f-string** είναι ο εύκολος τρόπος να βάλεις μεταβλητές μέσα σε κείμενο. Μην ξεχάσεις το `f` πριν από τα εισαγωγικά — είναι το πιο συχνό λάθος!

```python
name = "Odysseas"
age = 13
print(f"Ο {name} είναι {age} χρονών")
```

### Οι ασκήσεις σου

1. **Life in Weeks** — Ρώτα την ηλικία και τύπωσε πόσες μέρες, εβδομάδες και μήνες μένουν μέχρι τα 90.
2. **Pizza night** — Πίτσα €8.50, κάθε extra topping €1.20, delivery €2.50. Ρώτα πόσες πίτσες, πόσα toppings και πόσα άτομα. Τύπωσε πόσα πληρώνει ο καθένας, με 2 δεκαδικά.
3. **Initials** — Ρώτα το ονοματεπώνυμο και τύπωσε μόνο τα αρχικά, π.χ. `Ο.Ν.`
4. **Seconds alive** — Πόσα δευτερόλεπτα ζεις περίπου; Τύπωσέ τα με κόμματα: `f"{seconds:,}"`.
5. **Century club** — Ρώτα όνομα και ηλικία, τύπωσε τη χρονιά που θα γίνει 100.

### Το project της ημέρας: Tip Calculator

Ένας λογαριασμός σε ταβέρνα, ένα ποσοστό tip, και X άτομα να τον μοιραστούν. Πόσα πληρώνει ο καθένας;

### Το poster σου 🎨

Με `turtle`, φτιάξε ένα σχήμα που το μέγεθός του βγαίνει από τον αγαπημένο σου αριθμό, και γράψε το όνομά σου από κάτω. **Χρώματα, σχήμα, γραμματοσειρά: δικές σου αποφάσεις.**

---

---
---

# 📋 ΑΝΑΚΕΦΑΛΑΙΩΣΗ — Ημέρα 2
### *Κράτησέ το. Θα το χρειαστείς στις Ημέρες 3, 4 και 5.*

## Οι 3 μεγάλες ιδέες της ημέρας

**1️⃣ Κάθε τιμή στην Python έχει έναν τύπο (type).**
Ο τύπος καθορίζει τι μπορείς να κάνεις μαζί της. Δεν προσθέτεις κείμενο σε αριθμό.

**2️⃣ Η `input()` δίνει ΠΑΝΤΑ `str`.**
Αν θέλεις να κάνεις πράξεις, πρέπει πρώτα να μετατρέψεις: `int()` ή `float()`.

**3️⃣ Το `round()` αλλάζει τον αριθμό. Το `f"{x:.2f}"` αλλάζει μόνο το πώς φαίνεται.**
Για χρήματα, θέλεις το δεύτερο.

---

## Κάρτα αναφοράς

```python
# ΤΥΠΟΙ
"κείμενο"    # str
42           # int
3.14         # float
True         # bool

type(42)     # μου λέει τον τύπο

# ΜΕΤΑΤΡΟΠΗ (casting)
int("42")      # 42
float("3.14")  # 3.14
str(42)        # "42"

# STRINGS
name = "Python"
name[0]      # "P"   ← ξεκινάει από το 0!
name[-1]     # "n"   ← το τελευταίο
len(name)    # 6

# ΠΡΑΞΕΙΣ
10 / 3    # 3.333...  πάντα float
10 // 3   # 3         χωρίς δεκαδικά
10 % 3    # 1         το υπόλοιπο
10 ** 3   # 1000      δύναμη

# ΕΜΦΑΝΙΣΗ
round(3.14159, 2)        # 3.14
f"Έχω {n} πόντους"       # μην ξεχάσεις το f !
f"€{price:.2f}"          # 2 δεκαδικά, πάντα
```

---

## ✔️ Έλεγχος: μπορώ να…

Βάλε ✓ μόνο αν μπορείς να το κάνεις **χωρίς** να κοιτάξεις σημειώσεις.

- [ ] …πω τους 4 βασικούς τύπους δεδομένων
- [ ] …εξηγήσω γιατί το `"5" + 5` δίνει error
- [ ] …μετατρέψω ένα `input()` σε αριθμό
- [ ] …πάρω το πρώτο και το τελευταίο γράμμα μιας λέξης
- [ ] …εξηγήσω τη διαφορά `/` και `//`
- [ ] …γράψω ένα f-string με μια μεταβλητή μέσα
- [ ] …στρογγυλοποιήσω ένα ποσό σε 2 δεκαδικά
- [ ] …φτιάξω τον Tip Calculator από την αρχή, μόνος μου

*Όσα δεν έχουν ✓ → αυτά κάνουμε recall την επόμενη φορά.*

---

## Μίνι τεστ (απαντήσεις παρακάτω)

1. Τι τυπώνει το `print(type(4.0))`;
2. Τι τυπώνει το `print(9 // 4)`;
3. Γιατί σκάει αυτό; `age = input("Ηλικία: ")` και μετά `print(age + 1)`
4. `word = "Python"` — τι είναι το `word[2]`;
5. Τι τυπώνει το `print(f"{7/2:.1f}")`;

<details>
<summary>Απαντήσεις</summary>

1. `<class 'float'>` — έχει τελεία, άρα float
2. `2` — floor division, κόβει το δεκαδικό
3. `TypeError` — η `input()` δίνει `str`, δεν προσθέτεις `int` σε `str`. Λύση: `int(age) + 1`
4. `"t"` — μετράμε P=0, y=1, **t=2**
5. `3.5`

</details>

---

## 🗣️ Λέξεις που έμαθα σήμερα

`data type` · `str` · `int` · `float` · `bool` · `type()` · `casting` · `type conversion` · `subscripting` · `index` · `len()` · `floor division` · `modulo` · `exponent` · `round()` · `f-string` · `TypeError` · `ValueError` · `IndexError`

---

## Σήμερα έμαθα…

*(μία γραμμή, δική σου)*

`_______________________________________________`

**Έφτιαξα:** ☐ Tip Calculator  ☐ Turtle poster  ☐ ______________
