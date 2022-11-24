# Filling blanks in marge cell in Google Sheets

![example](https://user-images.githubusercontent.com/114103377/200196117-57e57050-44cb-4f8a-b3e5-2c6882b3fc90.png)

## Solution

```
=SCAN("",wanted_column/row,LAMBDA(accumulator, current_value, IF(current_value="",accumulator,current_value)))
```

example:
```
=SCAN("",A1:J1,LAMBDA(accumulator, current_value, IF(current_value="",accumulator,current_value)))
```

## Explanation

<img src="https://user-images.githubusercontent.com/114103377/200265998-5c36e045-3039-48bb-85bd-7b512f96f2d1.png" align="right" width="50%" />

### Merge cells
When we merge cells, the merged cell becomes the value of the first nonblank cell. If more than one combined cell contains data, only the first is kept. The rest of the value is deleted. Value is carried over to the first cell and the rest goes blank. Therefore, getting data from a cell other than the first one returns blank.

### SCAN function

**Syntax:**
```
SCAN(initial_value, initial_array_or_range, LAMBDA)
  initial_value: The initial accumulator value.
  initial_array_or_range: An array or range to be scanned.
  LAMBDA: A LAMBDA that’s applied to each value in array_or_range for scanning it.
    Syntax: LAMBDA(accumulator, current_value, formula_expression)
```
The SCAN function is one of the LAMBDA helper functions in Google Sheets that returns an array or range by applying a custom LAMBDA formula.
- At the beginning, the initial_value goes to the accumulator and the first element of the initial_array to the current_value.
- Then the formula_expression is calculated.
- The result of the calculation goes to the output_array and replaces the accumulator.
- Next element of the initial_array is taken and formula_expression is calculated again.
- When the formula_expression is evaluated for the entire initial_array, the output_array is returned.

In our example when the current_value is empty if statement is true. The output becomes the accumulator and the accumulator remains unchanged. When the value is not empty if statement is false. The output becomes the current_value and the accumulator is overwritten by the current_value.

![example_gif](https://user-images.githubusercontent.com/114103377/203515913-ca127bde-6c39-41a9-b98a-8e3d2c8509a6.gif)
