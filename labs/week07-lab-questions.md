# Week 07 Lab Practice Questions

Try each one **on paper or in an editor first**, then open the solution.
Solutions are the instructor's, copied from the lab sheet.

---

## Q1: Nested dictionary access
Write **one line** that puts Sam's **second assignment** mark (92) into `value`.

```python
a = {
    "Sam": {"Labs": [90, 95, 84], "Exams": [78, 99], "Assignments": [76, 92, 78, 61]},
    "Snorlex": {"Labs": [0, 0, 0], "Exams": [0, 0], "Assignments": [0, 0, 0, 0]},
}
```

<details><summary>Solution</summary>

```python
value = a['Sam']['Assignments'][1]
```
Read it left to right: dict → dict → list → index 1 (second item).
</details>

---

## Q2: Count spaces and underscores
1. Prompt the user for a string.
2. Display it, then print each character on its own line.
3. Count spaces `' '` and underscores `'_'`.
4. Print: `The string has xxx space(s) and xxx underscore(s).`

Sample run:
```
Enter your string:
Hello I'm a DIGT1101A Student.
Your entered string is " Hello I'm a DIGT1101A Student. " .
The entered string consisted of the below characters.

H
e
...
.
The string has 4 space(s) and 0 underscore(s).
```

<details><summary>Solution</summary>

```python
X = input('Enter your string: \n')
i=0;s=0;u=0
print('Your entered string is "',X,'"','.')
print('The entered string consisted of the below characters.\n')
while i<len(X):
   print(X[i])
   if X[i]==' ':
      s=s+1
   elif X[i]=='_':
      u=u+1
   i=i+1
print(f'The string has {s} space(s) and {u} underscore(s).')
```
Note: the odd spacing in `" Hello ... "` comes from `print` putting a space between each comma-separated item.
</details>

---

## Q3: Patient risk score
Read data for N patients: age (int), temperature °C (float), heart rate (int), systolic BP (int).

**Risk formula:**
`risk = 0.02·age + 0.8·(tempC − 37.0) + 0.03·|heartRate − 75| + 0.04·|120 − systolicBP|`

**Category rules** (checked in this order):
- `tempC >= 39.0` OR `systolicBP < 90` OR `heartRate > 130` → **URGENT (vital sign trigger)**
- `risk >= 4.0` → **HIGH**
- `risk >= 2.0` → **MEDIUM**
- otherwise → **LOW**

At the end, print: the count of URGENT, the count of HIGH (non-urgent), and the average risk (2 decimals).

Sample run:
```
Enter number of patients: 3

Patient 1
 Age (years): 70
 Temperature (C): 38.5
 Heart rate (bpm): 110
 Systolic BP (mmHg): 135
 Risk = 4.25   Category: HIGH

Patient 2
 Age (years): 50
 Temperature (C): 39.2
 Heart rate (bpm): 90
 Systolic BP (mmHg): 118
 Risk = 3.29   Category: URGENT (vital sign trigger)

Patient 3
 Age (years): 45
 Temperature (C): 37.2
 Heart rate (bpm): 87
 Systolic BP (mmHg): 140
 Risk = 2.22   Category: MEDIUM

Summary:
 Urgent: 1
 High (non-urgent): 1
 Average risk: 3.25
```

<details><summary>Solution</summary>

```python
n = int(input("Enter number of patients: "))
urgent_count = 0
high_nonurgent_count = 0
risk_sum = 0.0
for i in range(1, n + 1):
  print(f"\nPatient {i}")
  age = int(input(" Age (years): "))
  tempC = float(input(" Temperature (C): "))
  heartRate = int(input(" Heart rate (bpm): "))
  systolicBP = int(input(" Systolic BP (mmHg): "))

  risk = (0.02 * age
          + 0.8 * (tempC - 37.0)
          + 0.03 * abs(heartRate - 75)
          + 0.04 * abs(120 - systolicBP))
  risk_sum += risk
  if tempC >= 39.0 or systolicBP < 90 or heartRate > 130:
     category = "URGENT (vital sign trigger)"
     urgent_count += 1
  else:
     if risk >= 4.0:
          category = "HIGH"
          high_nonurgent_count += 1
     elif risk >= 2.0:
          category = "MEDIUM"
     else:
          category = "LOW"

  print(f" Risk = {risk:.2f} Category: {category}")

avg_risk = risk_sum / n if n > 0 else 0.0

print("\nSummary:")
print(f" Urgent: {urgent_count}")
print(f" High (non-urgent): {high_nonurgent_count}")
print(f" Average risk: {avg_risk:.2f}")
```
</details>

---

## Q4: Separate numbers and strings
Split a mixed list into a numbers list (sorted high → low) and a strings list (sorted A → Z).
Booleans (`True`/`False`) belong in **neither** list.

```python
given_list = [0,1,-2,'hello',True,3.14,'world','apple',321.5,45.2,False,'DIGT1101A',22]
```
Expected output:
```
[321.5, 45.2, 22, 3.14, 1, 0, -2]
['DIGT1101A', 'apple', 'hello', 'world']
```

<details><summary>Solution</summary>

```python
num_list = []; str_list = []
for item in given_list:
   check = str(type(item)) == "<class 'int'>" or str(type(item)) == "<class 'float'>"
   if check:
      num_list.append(item)
   elif str(type(item)) == "<class 'str'>":
      str_list.append(item)
num_list.sort(reverse=True), str_list.sort()
print(num_list)
print(str_list)
```
Gotcha: `isinstance(True, int)` is `True` in Python, so `isinstance` would wrongly let booleans in. Checking `type(item)` exactly keeps them out.
Uppercase letters sort before lowercase, which is why `'DIGT1101A'` comes first.
</details>

---

## Q5: Matrix input + column sum
1. Ask for rows and columns.
2. Read each row (comma-separated). If a row is too short, pad it with 0. If it's too long, ignore the extra values.
3. Display the matrix.
4. Ask for a column number and print that column's sum rounded to 2 decimals. If the column is invalid, use the **last** column.

Sample run:
```
Enter rows and cols (comma-separated): 3,4
Enter elements for row 1 (comma-separated): 1.1,1.2,1.3,1.4
Enter elements for row 2 (comma-separated): 2.1,2.2
Enter elements for row 3 (comma-separated): 3.1,3.2,3.3
The entered matrix is:
[1.1, 1.2, 1.3, 1.4]
[2.1, 2.2, 0.0, 0.0]
[3.1, 3.2, 3.3, 0.0]
Sum of which column are you interested to be calculated? 3
The sum of elements in column 3 is: 4.6
```

<details><summary>Solution</summary>

```python
rows, cols = map(int, input("Enter rows and cols (comma-separated): ").split(','))
matrix=[]
for i in range(rows):
  row = list(map(float, input(f"Enter elements for row {i+1} (comma-separated): ").split(',')))
  row = row + [0.0] * (cols - len(row))   # pad short rows with 0
  matrix.append(row[:cols])               # cut long rows to cols
print("\nThe entered matrix is:")
for row in matrix:
  print(row)
col = int(input('Sum of which column are you intrested to be calculated? '))
if col > cols or col <= 0:
  col = cols
sumCol = round(sum([matrix[i][col-1] for i in range(rows)]),2)
print(f'The sum of elements in colmun {col} is: {sumCol}')
```
User's "column 3" = index 2 → `col-1`.
</details>

---

## Q6: `remove_duplicates(numbers)`
Return a **new** list with each integer once, in order of first appearance. Leave the original list unchanged. `[]` → `[]`.
Example: `[4, 2, 4, 7, 2, 1]` → `[4, 2, 7, 1]`

<details><summary>Solution</summary>

```python
def remove_duplicates(numbers):
  result = []
  for number in numbers:
        if number not in result:
          result.append(number)
  return result
```
</details>

---

## Q7: `calculate_averages(table)`
Return a tuple: `(row_averages, column_averages)` for a 2D list (non-empty, all rows the same length).
`[[1,2],[3,4],[5,6]]` → `([1.5, 3.5, 5.5], [3.0, 4.0])`

<details><summary>Solution</summary>

```python
def calculate_averages(table):
  row_averages = []
  col_averages = []
  for row in table:
     row_averages.append(sum(row) / len(row))
  num_cols = len(table[0])
  for col in range(num_cols):
     col_sum = 0
     for row in table:
        col_sum += row[col]
     col_averages.append(col_sum / len(table))
  return row_averages, col_averages
```
</details>

---

## Q8: `fib(n)`
Fibonacci numbers are 1, 1, 2, 3, 5, 8, … numbered F₁, F₂, … with Fₙ = Fₙ₋₁ + Fₙ₋₂.
Write `fib(n)` that returns Fₙ.

<details><summary>Solution (recursive, from the lab)</summary>

```python
def fib(n):
  if n <= 1:
     return n
  else:
     return fib(n - 1) + fib(n - 2)
```
</details>

<details><summary>Solution (loop version, from the midterm review)</summary>

```python
def fib(n):
    a = 1
    b = 1
    for i in range(n - 2):
        c = a + b
        a = b
        b = c
    return b
```
</details>
