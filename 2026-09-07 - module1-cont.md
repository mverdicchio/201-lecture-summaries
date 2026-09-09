# Module 1 (cont.): Modulo, Boolean Functions, Match
**CSCI 201 — Introduction to Computer Science**
Lecture — Monday, September 7, 2026

---

## Pset 0 Exit Quiz Review

A few key takeaways from the quiz:

- `input()` always returns a **string** — cast it with `int()` or `float()` when you need a number.
- `check50` and `submit50` both require a **slug** argument (e.g., `citadelcs/problems/main/honor`).
- If output doesn't match the spec (e.g., wrong capitalization), the code may run without errors but still fail `check50`. A program with no syntax errors can still be wrong.
- For multi-blank questions: keep answers short. If you feel like you need to write up the side of the page, you're probably overthinking it.

---

## Quick Review: Module 1 So Far

- **Boolean / bool** — a new data type that is binary: `True` or `False`.
- **Relational operators** — `>`, `<`, `>=`, `<=`, `==`, `!=` — produce a Boolean result.
- **Logical operators** — `and`, `or`, `not` — chain Boolean expressions together.
- **if / elif / else** — executes different blocks depending on which condition is true. Use `elif` and `else` (not separate `if` statements) when conditions are mutually exclusive.

---

## The `not` Operator

`not` is a **unary** operator — it takes only one operand (like a unicycle has one wheel). It simply inverts a Boolean value.

| A | not A |
|---|---|
| True | False |
| False | True |

```python
if not is_even(x):
    print("x is odd")
```

There's often more than one way to write a logical condition. When a negated version is clearer, use it; when it makes your head hurt, flip the question.

---

## Integer Division and the Modulo Operator

When you divide two integers in Python, you can get two distinct pieces:

| Operation | Symbol | Example (`27 / 5`) | Result |
|---|---|---|---|
| Floating point division | `/` | `27 / 5` | `5.4` |
| Integer division (quotient) | `//` | `27 // 5` | `5` |
| Remainder (modulo) | `%` | `27 % 5` | `2` |

Integer division is a blunt instrument — it **truncates**, never rounds. `29 // 5` is `5`, not `6`, even though `29 / 5 = 5.8`.

### Testing divisibility

The key pattern: **a number is evenly divisible by n if its remainder is 0**.

```python
if x % 2 == 0:
    print("even")
else:
    print("odd")
```

> **Common mistake:** Writing `if x % 2:` alone is not a Boolean expression — `%` gives you an integer, not `True`/`False`. You have to ask a question about that integer: `x % 2 == 0`.

---

## Worked Example: Leap Year

Leap year rules:
1. Divisible by 4 — usually a leap year.
2. **Except** divisible by 100 (century years) — not a leap year.
3. **Except** divisible by 400 — leap year again.

Examples: 2000 ✓ (÷400), 2100 ✗ (÷100 but not ÷400), 2024 ✓ (÷4, not ÷100).

### The condition in one expression

```python
year % 400 == 0 or (year % 4 == 0 and year % 100 != 0)
```

Read it as: "divisible by 400, OR (divisible by 4 AND not a century year)."

### Full program with a Boolean helper function

```python
def is_leap_year(year):
    return year % 400 == 0 or (year % 4 == 0 and year % 100 != 0)

def main():
    year = int(input("Year: "))
    if is_leap_year(year):
        print("Leap year")
    else:
        print("Not a leap year")

main()
```

**Why a helper function?** It isolates the computation so you can test it independently. `main()` handles input/output; other functions do the work. This pattern will matter more as programs grow.

> **Naming convention:** Functions that return a Boolean are often named with a verb like `is_` (e.g., `is_leap_year`, `is_even`) so the call reads like a yes/no question: `if is_leap_year(year):`

---

## Pythonic Style: Returning Boolean Expressions Directly

A common beginner pattern (works, but verbose):

```python
def is_even(x):
    if x % 2 == 0:
        return True
    else:
        return False
```

Shorter — return the expression itself:

```python
def is_even(x):
    return x % 2 == 0
```

If the expression evaluates to `True`, `True` is returned; if `False`, `False` is returned. No `if` needed.

Python also allows a **conditional expression** (ternary style) on one line:

```python
def is_even(x):
    return True if x % 2 == 0 else False
```

All three are logically equivalent. Pick the style you're most comfortable reading. The one-liner `return expression` is the most common in practice.

---

## Intro to Match Statements

A `match` statement is an alternative to a long `if / elif / else` chain when you're comparing one variable against several specific values. The goal is readability — Python's interpreter doesn't care which you use.

### if / elif / else version

```python
name = input("Name: ")

if name == "Harry" or name == "Hermione" or name == "Ron":
    print("Gryffindor")
elif name == "Draco":
    print("Slytherin")
else:
    print("Who?")
```

### match version (intro — to be continued Wednesday)

```python
match name:
    case "Harry":
        print("Gryffindor")
    case "Hermione":
        print("Gryffindor")
    case "Ron":
        print("Gryffindor")
    case "Draco":
        print("Slytherin")
    case _:
        print("Who?")
```

`case _:` is the catch-all, equivalent to `else`. Next class: how to combine multiple cases with `|` (vertical bar) to avoid repeating `print("Gryffindor")` three times.

---

## Key Vocabulary

| Term | Meaning |
|---|---|
| **Unary operator** | An operator with only one operand. `not` is the main one here. |
| **Integer division (`//`)** | Division that discards the fractional part and returns only the quotient. |
| **Modulo (`%`)** | Returns the remainder of integer division. Has nothing to do with percentages. |
| **Divisibility test** | `x % n == 0` — true when `x` is evenly divisible by `n`. |
| **Boolean function** | A function that returns `True` or `False`, typically named with `is_`. |
| **Pythonic** | Code written in a style idiomatic to Python — concise, readable, using language features naturally. |
| **Match statement** | A multi-way branch that compares one variable against specific values; an alternative to long `if/elif/else` chains. |

---

## Logistics

- **Tutoring:** Every night Sunday through Thursday, 8–10 PM, room 215. Sometimes starts a few minutes early.
- **Pset 1:** Three problems using conditionals — *Nav*, *Knowledge*, *What Time Is It?* You have enough tools to start now.
- Wednesday: finish `match` statement (combining cases with `|`).

---

*CSCI 201 · The Citadel · Fall 2026 · Generated from lecture recording & Module 1 notes*
