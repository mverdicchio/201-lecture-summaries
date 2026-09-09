# Module 1 (fin.): Match Statements & Workshop
**CSCI 201 — Introduction to Computer Science**
Lecture — Wednesday, September 9, 2026

---

## Logistics

- **Pset 1 due:** Sunday evening.
- **Tutoring:** Tonight and tomorrow (not Friday or Saturday). Also Sunday, but don't wait — most people procrastinate and swarm tutoring Sunday night. Go earlier.
  - Room 215, Sunday through Thursday, 8–10 PM.
  - Find them on Ed Discussion under the "201 Tutors" thread.
- **Ed Discussion tip:** Go to edstem.org directly (after logging in once via Canvas). On mobile, you can install it as an app from the browser menu and enable push notifications.
- **Lecture summaries** are being posted on Ed Discussion — generated from audio recordings. Use them if you miss class or want to check your notes.

---

## Finishing Match Statements

### Review: if / elif / else

```python
name = input("Name: ")

if name == "Harry" or name == "Hermione" or name == "Ron":
    print("Gryffindor")
elif name == "Draco":
    print("Slytherin")
else:
    print("Who?")
```

This works fine. The `or` operator lets you chain conditions, but long chains on one line can get hard to read.

### Match statement: long form

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

- `match name:` — the variable to match against.
- Each `case "value":` runs when `name` equals that value.
- `case _:` is the catch-all, equivalent to `else`.
- Works well for strings and integers; avoid matching floats (exact equality is unreliable with floating point).

### Combining cases with `|`

```python
match name:
    case "Harry" | "Hermione" | "Ron":
        print("Gryffindor")
    case "Draco":
        print("Slytherin")
    case _:
        print("Who?")
```

The `|` (vertical bar, above the Enter key) combines cases the way `or` combines Boolean expressions — but the syntax is more compact because you don't have to repeat `name ==` each time. Think of it as a list of allowed matches.

### When to use which

| | if / elif / else | match |
|---|---|---|
| Works for | Any Boolean condition | Exact value matching |
| Combine branches | `or` keyword | `\|` symbol |
| Catch-all | `else:` | `case _:` |
| Readability | Better for complex conditions | Better for lists of specific values |

Functionally equivalent at runtime. Use whichever reads more clearly. Unless a quiz or test asks for a specific syntax, the choice is yours.

> **Tip:** To comment/uncomment a block of code in VS Code: highlight the lines, then press `Ctrl + /`. Toggles all selected lines at once.

---

## Module 1 Workshop

The rest of class is workshop time. These are collaborative practice problems — work with the people around you, post questions on Ed, or ask for help.

### Approach

- Write a `main()` function that acts as a **software tester**, not a user-friendly app.
- **Hard-code test values** — don't waste time on `input()` prompts and welcome messages.
- Focus on writing and testing the functions themselves.

Example structure:

```python
def is_even(x):
    return x % 2 == 0

def main():
    print(is_even(22))   # Expected: True
    print(is_even(23))   # Expected: False

main()
```

### Problems to work on (pick what's most interesting)

- **Even/odd** — function that returns a string `"even"` or `"odd"` given an integer.
- **Grade percentage** — pass two numbers (score, total), return a string describing the letter grade.
- **Leap year** — reuse or adapt the function from Monday's notes.
- Additional problems on the workshop handout — more than can be finished in class, so keep them as study material.

> **Workshop tip:** When you're studying for a test later, these workshop solutions are ideal. And when working on psets, you can borrow patterns from your own workshop code.

### Python interactive interpreter

If you see `>>>` in your terminal, Python is running in interactive mode. Type `exit()` to get back to the normal terminal.

---

## Module 1 Complete

That's everything for Module 1. You now have: Boolean expressions, relational and logical operators, `if / elif / else`, modulo/divisibility, Boolean helper functions, and `match` statements.

---

*CSCI 201 · The Citadel · Fall 2026 · Generated from lecture recording & Module 1 notes*
