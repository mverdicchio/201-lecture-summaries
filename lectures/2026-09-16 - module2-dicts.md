# Module 2 (cont.): Dictionaries & Tuples
**CSCI 201 — Introduction to Computer Science**
Lecture — Tuesday, September 16, 2026

---

## Logistics

- Handout distributed in class: advice from CSCI 495 seniors to younger students. Worth reading.
- **Pset 2** is open — start working on it.

---

## List Methods (recap + new)

A quick warm-up on list operations before moving to dictionaries:

| Method | What it does |
|---|---|
| `lst.append(item)` | Adds one item to the end |
| `lst.remove(item)` | Removes the first occurrence of item |
| `lst.pop()` | Removes **and returns** the last item (like popping a stack) |
| `lst.clear()` | Empties the list (same as reassigning `lst = []`) |

`pop()` is borrowed from the stack data structure: a Pez dispenser is a useful mental model — whatever went in last comes out first.

```python
stack = [1, 2, 3]
last = stack.pop()   # last = 3, stack is now [1, 2]
```

---

## Demo: History / Undo Program

The following program tracks user actions in a list, supporting undo (pop), restart (clear), and quit (break):

```python
def main():
    history = []

    while True:
        action = input("Action: ")

        if action == "undo":
            undone = history.pop()
            print(f"Undid: {undone}")
        elif action == "restart":
            history.clear()
        elif action == "quit":
            break
        else:
            history.append(action)

        print(history)

main()
```

Key observations:
- `while True` signals an indefinite loop with a `break` exit.
- `pop()` on an empty list raises an `IndexError` — in real code, guard against it.
- `history.clear()` and `history = []` are equivalent; the method is a bit more explicit.

---

## Dictionaries

### The problem with parallel lists

```python
faculty = ["Bannock", "Joshi", "Shaddy", "Verdicchio"]
ranks   = ["Colonel", "LTC",   "Captain", "LTC"]
```

These only work as long as the indexes stay aligned. Accidentally adding or deleting from one list breaks the pairing. A **dictionary** solves this by bundling the two pieces of data together as a key–value pair.

### Syntax

```python
faculty_ranks = {
    "Bannock":     "Colonel",
    "Joshi":       "LTC",
    "Shaddy":      "Captain",
    "Verdicchio":  "LTC",
}
```

Curly braces `{}` define the dictionary. Each entry is `key: value`. Keys must be **immutable** (strings and integers are common choices). A key can only appear once — adding a duplicate overwrites the existing value.

### Reading and writing entries

```python
# Read a value
print(faculty_ranks["Bannock"])   # "Colonel"

# Add a new entry (or overwrite an existing one)
faculty_ranks["Lil Bannock"] = "Captain"
```

This looks exactly like list indexing, except you put a **key** in the brackets instead of an integer index.

### Looping through a dictionary

A `for` loop over a dictionary gives you the **keys**, not the values:

```python
for professor in faculty_ranks:
    print(professor, "has rank", faculty_ranks[professor])
```

Output:
```
Bannock has rank Colonel
Joshi has rank LTC
Shaddy has rank Captain
Verdicchio has rank LTC
Lil Bannock has rank Captain
```

Use the key inside the loop to look up the corresponding value.

---

## List of Dictionaries (tabular data)

When every dictionary in a list shares the same key set, the result behaves like a spreadsheet or database table — each dictionary is a row, each key is a column.

```python
dr_bannock  = {"name": "Bannock",    "rank": "Colonel", "area": "Leadership"}
dr_joshi    = {"name": "Joshi",      "rank": "LTC",     "area": "AI/ML"}
dr_shaddy   = {"name": "Shaddy",     "rank": "Captain", "area": "Cyber Ops"}
dr_v        = {"name": "Verdicchio", "rank": "LTC",     "area": "CS Education"}

# Four separate dicts, identical key set: "name", "rank", "area"

faculty = [dr_bannock, dr_joshi, dr_shaddy, dr_v]

for prof in faculty:
    print(prof["name"], "|", prof["rank"], "|", prof["area"])
```

In this loop `prof` is a dictionary (not a string or integer), so `prof["name"]` retrieves the value for the `"name"` key. If any dictionary has a typo in a key name, the code will crash when it reaches that entry — consistent key sets matter.

In practice, packages like `csv` will build these lists of dictionaries automatically from a file, so you rarely type them by hand.

---

## Tuples

A **tuple** is an ordered, immutable sequence — like a list, but it cannot be changed after creation.

```python
point  = (3, 7)         # 2D coordinate
color  = (255, 128, 0)  # RGB value
empty  = ()             # empty tuple
single = (42,)          # singleton — trailing comma required
```

Without the trailing comma, `(42)` is just `42` in parentheses — not a tuple.

### Indexing (same as lists)

```python
point[0]    # 3
point[-1]   # 7 (negative indexing works the same way)
```

### Immutability

```python
color[1] = 255   # TypeError: 'tuple' object does not support item assignment
```

**List vs. Tuple analogy:** a list is a whiteboard (editable); a tuple is a photograph of that whiteboard (fixed).

| | List | Dict | Tuple |
|---|---|---|---|
| Syntax | `[1, 2, 3]` | `{"a": 1}` | `(1, 2, 3)` |
| Ordered / indexed | Yes | No | Yes |
| Mutable | Yes | Yes | No |
| Use when | You need to grow/shrink/change | You need key–value lookup | Structure is fixed |

### Connection to `str.split()` and multiple assignment

`split()` returns a tuple of the pieces. Combined with multiple assignment:

```python
numerator, denominator = "22/55".split("/")
# numerator = "22", denominator = "55"
```

The number of variables on the left must match the number of items in the tuple exactly.

---

*CSCI 201 · The Citadel · Fall 2026 · Generated from lecture recording & Module 2 notes*
