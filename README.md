# Roman Numeral Kata

## Problem
How can we add and subtract roman numeral numbers?

## Overview
Roman numeral values are defined as: <br/>
`I  = 1`<br/>
`IV = 4`<br/>
`V  = 5`<br/>
`IX = 9`<br/>
`X  = 10`<br/>
`XL = 40`<br/>
`L  = 50`<br/>
`XC = 90`<br/>
`C  = 100`<br/>
`CD = 400`<br/>
`D  = 500`<br/>
`CM = 900`<br/>
`M  = 1000`<br/>

Some rules when adding or subtracting roman numerals are:<br/>
	1.) I, X, C, and M may not appear more than three times. (`II + II is not IIII`, instead `II + II is IV`)<br/>
	2.) V, L, and D my only appear once. (`D + D is not DD`, instead `D + D is M`)<br/>
	3.) The max roman numeral is `3999` (`MMMCMXCIX`)<br/>

## Examples
Some examples of addtion and subraction cases are below:

### Addition
`III + I = IV`<br/>
`IX + I = X`<br/>

### Subtraction
`IV - I = III`<br/>
`C - I = XCIX`<br/>

## Error Codes
This library will return error codes in the `errno` value. The error codes can be found in the [roman_error_codes.h](src/roman_error_codes.h) and [roman_error_codes.c](src/roman_error_codes.c). The meaning of each is also denoted below:<br/>

| Name                     | Value | Description                                                                                  |
| ------------------------ | ----- | -------------------------------------------------------------------------------------------- |
| ROMAN_NUMERAL_LIMIT      | 4     | The input contained too many of one character, for instance XXXX would have too many X's     |
| ROMAN_NEGATIVE_NOT_VALID | 5     | The input provided was negative or would result in a negative roman numeral which is invalid | 
| ROMAN_NUMERAL_TOO_LARGE  | 6     | The input provided would result in a roman numeral wich is larger than 3999                  |
| ROMAN_ZERO_IS_NOT_VALID  | 7     | The input provided would result in zero which is not a valid roman numeral                   |

## Important
This library relies on the caller to free memory when calling arabic_to_roman.h's `to_roman` method and roman_calculator.h's `add_roman_numerals` and `subtract_roman_numerals` methods. 
These methods will allocate memory internally to create the resulting roman numeral string.
<br/>
<br/>
This library also uses `errno.h` to report error codes. When calling a method that returns strings you 
will get back a description of the error in the resulting string and errno will be set to one of the 
above error codes. However when a method returns an integer the library will return -1 and set the errno to 
one of the above error codes.  