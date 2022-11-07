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
When we merge cells, the cell becomes the value of the first nonblank cell. If more than one combined cell contains data, only the first is kept. The rest of the value is deleted. Value is carried over to the first cell and the rest goes blank. Therefore, getting data from a cell other than the first one returns blank.

### SCAN function

**Syntax:**
```
SCAN(initial_value, array_or_range, LAMBDA)
  initial_value: The initial accumulator value.
  array_or_range: An array or range to be scanned.
  LAMBDA: A LAMBDA that’s applied to each value in array_or_range for scanning it.
    Syntax: LAMBDA(accumulator, current_value, formula_expression)
```
The SCAN function is one of the LAMBDA helper functions in Google Sheets that returns an array or range by applying a custom LAMBDA formula
