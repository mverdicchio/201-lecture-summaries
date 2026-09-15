# Module 2 (cont.): Lists & Dictionaries Intro
**CSCI 201 — Introduction to Computer Science**
Lecture — Monday, September 14, 2026

---

## Logistics

- **Cyber Club** meets Thursday at 6:15 PM in room 215.
- **Tutoring** Sunday through Thursday, 8–10 PM, room 215.
- **Course Resources** module added to the top of Canvas — written lecture notes, lecture summaries, tutoring/office hours all in one place.
- **Pset 0:** Graded. One-time mercy rule — late submissions accepted for half credit, this pset only.
- **Pset 1:** Due last night. 5% late penalty per day — get it in today if you haven't.
- **Wednesday:** Exit quiz on Pset 1 material at the start of class.

---

## Loop Practice

### Multiples of 3 from 0 to 100

Two equivalent approaches:

**Approach 1 — check every number with modulo:**
```python
i = 0
while i <= 100:
    if i % 3 == 0:
        print(i)
    i += 1
```

**Approach 2 — skip-count by 3 (no if needed):**
```python
i = 0
while i <= 100:
    print(i)
    i += 3
```

Use approach 1 when the selection condition involves a function or complex test. Use approach 2 when you can just step by the right amount.

### Count down from 87 to 47

```python
i = 87
while i >= 47:
    print(i)
    i -= 1
```

The loop variable can start anywhere, count in any direction, and step by any amount.

### Same countdown with a for loop

`range()` takes up to three arguments: `range(start, stop, step)`. Stop is **exclusive** — go one past the target. For counting down, use a negative step:

```python
for i in range(87, 46, -1):
    print(i)
```

| `range()` call | Sequence produced |
|---|---|
| `range(n)` | 0, 1, ..., n−1 |
| `range(start, stop)` | start, start+1, ..., stop−1 |
| `range(start, stop, step)` | start, start+step, ..., up to (not including) stop |

---

## Lists (continued)

### Read and write by index

```python
faculty = ["Banik", "Joshi", "Zareen", "Sedeghpour", "Verdicchio"]

print(faculty[1])       # Joshi
faculty[4] = "Dr. V"    # overwrites last item
```

### Iterating by value

```python
for name in faculty:
    print(name)
```

### Iterating by index

```python
for i in range(len(faculty)):
    print(i + 1, faculty[i])   # 1-based numbering for display
```

Use this form when you need the index for something — arithmetic, display, comparison. Use the value form when you just need each item.

### Negative indexing

| Index | Equivalent |
|---|---|
| `faculty[-1]` | last item |
| `faculty[-2]` | second-to-last |
| `faculty[-n]` | `faculty[len(faculty) - n]` |

### `IndexError`

Accessing an index outside the list's bounds — positive or negative — raises an `IndexError`. Always validate user-supplied indexes before using them.

### Checking membership with `in`

```python
if "Dr. Hayne" in faculty:
    location = faculty.index("Dr. Hayne")
    print(location)
else:
    print("Not found")
```

Use `in` before calling `index()` on something that might not be there.

---

## List Methods

| Method | What it does |
|---|---|
| `lst.append(item)` | Adds one item to the end |
| `lst.extend(other_list)` | Unpacks and adds all items from another list |
| `lst.remove(item)` | Removes the first occurrence of item (error if not found) |
| `lst.insert(index, item)` | Inserts item at the given index; existing items shift right |
| `lst.index(item)` | Returns the index of item (`ValueError` if not found) |
| `lst.reverse()` | Reverses the list **in place** (returns `None`) |

**`append` vs `extend`:**
```python
faculty.append(["Zareen", "Sadeghpour"])  # adds one sub-list — length grows by 1
faculty.extend(["Zareen", "Sadeghpour"])  # unpacks — length grows by 2
```

**`reverse()` returns `None`** — don't try to print its return value. Call it, then print the list:
```python
faculty.reverse()
print(faculty)   # correct
print(faculty.reverse())  # prints None — wrong
```

---

## Dictionaries (preview)

A **dictionary** (`dict`) stores **key–value pairs** instead of a flat sequence of items.

Analogies:
- A real dictionary: the **word** is the key, the **definition** is the value.
- DNS: the **domain name** (google.com) is the key, the **IP address** is the value.

Full syntax and examples on Wednesday.

---

*CSCI 201 · The Citadel · Fall 2026 · Generated from lecture recording & Module 2 notes*
