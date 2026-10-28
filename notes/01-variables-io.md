# Step 01: Variables, Data Types, Input & Output

## 1. Variables
A **variable** is a name that refers to a value. `=` means "store the right side under the left name".
It does **not** mean "equals" in the math sense.

```python
x = 10          # x now refers to 10
x = x + 1       # read x (10), add 1, store 11 back in x
```

**Naming rules:** letters, digits and `_` only; can't start with a digit; no spaces; case-sensitive (`Age` ≠ `age`).
**My rule:** never use a built-in's name (`min`, `max`, `sum`, `list`, `str`, `type`, `len`).
If you write `sum = 0`, then `sum(row)` crashes later, because `sum` is now a number, not the function.

## 2. The four basic types

| Type | Example | What it is |
|---|---|---|
| `int` | `10`, `-3` | whole number |
| `float` | `3.14`, `5.0` | decimal number |
| `str` | `'Sam'`, `"12"` | text (always in quotes) |
| `bool` | `True`, `False` | yes/no (capital T/F) |

`type(x)` tells you the type → `<class 'int'>`.

⚠️ `"12"` is a **string**, not a number. `"12" + 1` is an error.

## 3. Casting (converting types)
```python
int('12')      # 12
float('3.5')   # 3.5
str(123)       # '123'
int(3.9)       # 3   (cuts off the decimal, does NOT round)
int('3.5')     # ERROR: int() can't read a decimal string
```

## 4. Input
```python
name = input('Your name: ')            # ALWAYS a string
age  = int(input('Age: '))             # convert immediately for math
temp = float(input('Temp: '))
```
**Rule:** `input()` *always* gives text. Wrap it in `int()` / `float()` before doing math.

## 5. Output: `print` and f-strings
```python
print('Hi', name)              # commas add ONE space between items → Hi Sam
print('a', 'b', sep='')        # sep='' removes that space → ab
print(f'{name} is {age}')      # f-string: put variables inside {}
print(f'{temp:.2f}')           # 2 decimal places → 36.60
```
⚠️ The commas-add-spaces rule is why the Week 7 lab prints `" Hello ... "` with extra spaces.
**Exam tip:** match the sample output *exactly*: spacing, order, decimals.

---

## Quick check
1. What is `type(input('Enter: '))` if the user types `42`?
2. What does `int(7.99)` give?
3. What does `print('a', 'b', 'c')` print?
4. Spot the bug:
   ```python
   price = input('Price: ')
   total = price * 2
   print(f'Total: {total}')
   ```
   If the user types `5`, what is printed, and how do you fix it?

### My answers
*(to fill in together)*
