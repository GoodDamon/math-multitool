# Multitool
A collection of simple, handy JavaScript functions, objects, prototypes, etc.

## Usage
Right now, the only multitool available is math-multitool.js. It provides an array prototype that allows you to sum, multiply, average, and get the median of arrays of numbers accurately, including decimals, up to fifteen decimal digits. It also provides two functions, `mm.fractionalize()` and `mm.decimalize()`.

The syntax for the math-multitool prototype is:
`array.mm(options);`

...where *options* is one or more of:
* "sum"
* "multiply"
* "average"
* "median"
* "mode"
* "max"
* "min"
* "all" (Performs all calculations)

The syntax for the fractionalize and decimalize functions are:
```javascript
mm.fractionalize(number);
mm.decimalize(numerator, denominator);
```

#### Example
In plain JavaScript, decimal calculations can be inaccurate:

```javascript
var x = [0.1,0.2];

console.log(x[0] + x[1]);			// Returns 0.30000000000000004
console.log(x[0] * x[1]);			// Returns 0.020000000000000004
```

With math-multitool, decimal calculations will be accurate up to 15 digits:

```javascript
x.mm("all");

console.log(x.sum);					// Returns 0.3
console.log(x.product);				// Returns 0.02
console.log(x.mean);				// Returns 0.15
console.log(x.median);				// Returns 0.15
console.log(x.mode);				// If the array contains more instances of one number than any
									// other, mode returns that number. If more than one number
									// is tied for most entries, all such numbers are returned in
									// an array.
```

Arrays can be updated and the calculations can be rerun:

```javascript
x[2] = 0.4;
x.mm("all");

console.log(x.sum);					// Returns 0.7
console.log(x.product);				// Returns 0.008
console.log(x.mean);				// Returns 0.23333333333333334
									// For repeating decimals, the number of digits returned
									// is determined by JavaScript rounding

console.log(x.median);				// Returns 0.2
```

**Note**: Be careful how you add members! If you add a new member to the wrong place in the array - for example, with `x[3] = 0.4;` - you will create an object instead of a number. Math Multitool only supports JavaScript numbers and strings that can be converted to JavaScript numbers.

```javascript
mm.fractionalize(0.24);				// Returns an array of [ 24, 100 ]
mm.decimalize(3,17);				// Returns 0.17647058823529413
```

**Note**: Fractionalize is designed to return fractions with denominators equal to a power of 10. That is to say, rather than returning a fraction of 1/2, it will always return a fraction of 5/10. An option to return the lowest common denominator is planned for a future version.

## Plans
I'll add more math functions to math-multitool.js as I can, and other non-math utilities that take new developers far too long to figure out will be added whenever possible.
