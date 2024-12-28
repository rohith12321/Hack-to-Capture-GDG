Running the exiftool to analyze this image gave me the flag directly.

```bash
  exiftool ./Desktop/part1/math.jpg
```
```Comment : The flag for this challenge is of the form:..CTFlearn{I_Like_Math_x_y}..where x and y are the solution to these equations:..3x + 5y = 31..7x + 9y = 59...```

Now this info told me that I had to solve the equation. Gave me values 2, 5 for x, y and then got the flag.

Flag: CTFlearn{I_Like_Math_2_5}
