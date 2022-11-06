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
