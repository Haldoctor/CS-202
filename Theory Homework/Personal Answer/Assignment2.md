# CS202 Theory Assignment 2
12312109
## Problem 1
### Question A
Calculation of the a's cycles:

$4 * 5 * 10^8 + 10 * 3 * 10^8 + 3 * 2 * 10^8$

$= 2 * 10^9 + 3 * 10^9 + 0.6 * 10^9$

$= 5.6 * 10^9$

Calculation of the a's global CPI:

$\frac{5.6 * 10^9}{5 * 10^8 + 3 * 10^8 + 2 * 10^8}$

$=\frac{5.6 * 10^9}{1 * 10^9}$

$= 5.6$

Calculation of the b's cycles:

$1 * 5 * 10^8 + 20 * 3 * 10^8 + 2 * 2 * 10^8$

$= 0.5 * 10^9 + 6 * 10^9 + 0.4 * 10^9$

$= 6.9 * 10^9$

Calculation of the b's instruction number:

$\frac{6.9 * 10^9}{5 * 10^8 + 3 * 10^8 + 2 * 10^8}$

$= \frac{6.9 * 10^9}{1 * 10^9}$

$= 6.9$

So the global CPI of a is $5.6$, the global CPI of b is $6.9$

### Question B
According to the `Question A`, we have the total cycles of implementation a and b.

For implementaion a:

$\frac{5.6 * 10^9}{5 * 10^9} = 1.12 s$

For implementation b:

$\frac{6.9 * 10^9}{5 * 10^9} = 1.38 s$

So the execution time of implementation a is $1.12s$ and the execution time of b is $1.38s$

### Question C
We can figure out the time comsumption of the new instruction to see whether this is a good design for the implementation.

Calculation of the a's cycles:

$4 * 5 * 10^8 * 0.75 + 10 * 3 * 10^8 + 3 * 2 * 10^8$

$= 1.5 * 10^9 + 3 * 10^9 + 0.6 * 10^9$

$= 5.1 * 10^9$

Calculation of the a's execution time:

$\frac{5.1 * 10^9}{\frac{5 * 10^9}{1.1}} = 1.122s$

Calculation of the b's cycles:

$1 * 5 * 10^8 *0.75 + 20 * 3 * 10^8 + 2 * 2 * 10^8$

$=0.375 * 10^9 + 6 * 10^9 + 0.4 * 10^9$

$= 6.775 * 10^9$

Calculation of the b's execution time:

$\frac{6.775 * 10^9}{\frac{5 * 10^9}{1.1}} = 1.491s$

Compared to the previous design, the new design will cost more time to execute, so the new design is not a good design for both implementations.
## Problem 2
### Question A
First we trans $-40$ and $100$ from decimal into binary

$(40)_{10} = (00101000)_{2}$ 

So the binary of $-40$ is: $(-40)_{10} = (11011000)_2$

The binary of $100$ is: $(100)_{10} = (01100100)_2$

Add up the two binary numbers: $01100100 + 11011000 = 100111100$

We take out the least 8 digits and we get: $00111100$

$-40 + 100 = 60$ and $(00111100)_2 = (60)_{10}$ and $60$ is between $-128$ to $127$

So the answer in the decimal type is $60$
### Problem B
We already have the binary form of two numbers:

$(-40)_{10} = (11011000)_2, (100)_{10} = (01100100)_2$

Because we need to calculate $-40 - 100$

So we need to find the binary form of $-100$: $(-100)_{10} = (10011100)_2$

Add two binary number together: $11011000 + 10011100 = 101110100$

We only keep 8 digits: $01110100$

Considering $-40 - 100 = -140$ and this is a number which didn't locate in the region between $-128$ to $127$

So the answer of the calculation should be $-128$ in decimal form.
## Problem 3
### Step 1
We first trans the hexadecimal number into binary number:

$(0x34)_{16} = (00110100)_{2}$

$(0x1A)_{16} = (00011010)_{2}$
### Step 2
Second, we initialized the registers:

Multiplicand Register: Fixed at $00110100$

Product Register:

&nbsp;&nbsp; Right 8 digits: Initialized with the multiplier $00011010$
&nbsp;&nbsp; Left 8 digits: Initialized this part into $00000000$
&nbsp;&nbsp; Total: Initialized this part into $00000000 00011010$
### Step 3
Third, we iterative the multiplication process. In this part I follow with the table form in the figure 3.6

|Iteration|Step|Multiplier|Multiplicand|Product|
|:----:|:----:|:----:|:----:|:----:|
|0|Initial values|00011010|00110100|00000000 00011010|
|1|1a: LSB = 0 -> No add|00011010|00110100|00000000 00011010|
||2: Shift right Product|00001101|00110100|00000000 00001101|
|2|1a: LSB = 1 -> Add multiplicand |00001101|00110100|00110100 00001101|
||2: Shift right product|00000110|00110100|00011010 00000110|
|3|1a: LSB = 0 -> No add|00000110|00110100|00011010 00000110|
||2: Shift right product|00000011|00110100|00001101 00000011|
|4|1a: LSB = 1 -> Add multiplicand|00000011|00110100|01000001 00000011|
||2: Shift right product|00000001|00110100|00100000 10000001|
|5|1a: LSB = 1 -> Add multiplicand|00000001|00110100|01010100 10000001|
||2: Shift right product|00000000|00110100|00101010 01000000|
|6|1a: LSB = 0 -> No add|00000000|00110100|00101010 01000000|
||2: Shift right product|00000000|00110100|00010101 00100000|
|7|1a: LSB = 0 -> No add|00000000|00110100|00010101 00100000|
||2: Shift right product|00000000|00110100|00001010 10010000|
|8|1a: LSB = 0 -> No add|00000000|00110100|00001010 10010000|
||2: Shift right product|00000000|00110100|00000101 01001000|
### Step 4
Thus we can have the product of the register: $00000101$ $01001000$

Combined together we get: $0000010101001000$

We convert the formation of the product to see whether the result is correct.

$(0000010101001000)_2 = (0x0548)_{16} = (1352)_{10}$

$(0x34)_{16} = (52)_{10}$

$(0x1A)_{16} = (26)_{10}$

$52 * 26 = 1352$

So the result is

## Problem 4
### Step 1
Trans the data from decimal form into binary form:

$(54)_{10} = (110110)_2$

$(17)_{10} = (010001)_2$
### Step 2
Initial the registers:
&nbsp;&nbsp;Divisor: $010001000000$
&nbsp;&nbsp;Remainder: $000000110110$
&nbsp;&nbsp;Quotient: 000000
### Step 3
| Iteration | Step | Quotient | Divisor | Remainder |
|-----------|------|----------|---------|-----------|
| 0         | Initial values | 000000   | 010001000000 | 000000110110 |
| 1         | 1: Rem = Rem - Div   | 000000   | 010001000000 | 101111110110 |
|           | 2b: Rem < 0 -> recover Rem, Shift left Q, Q[0] = 0   | 000000   | 010001000000 | 000000110110 |
|           | 3: Shift right divisor    | 000000   | 001000100000 | 000000110110 |
| 2         | 1: Rem = Rem - Div    | 000000   | 001000100000 | 111000010110 |
|           | 2b: Rem < 0 -> recover Rem, Shift left Q, Q[0] = 0 | 000000   | 001000100000 | 000000110110 |
|           | 3: Shift right divisor    | 000000   | 000100010000 | 000000110110 |
| 3         | 1: Rem = Rem - Div    | 000000   | 000100010000 | 111100100110 |
|           | 2b: Rem < 0 -> recover Rem, Shift left Q, Q[0] = 0 | 000000   | 000100010000 | 000000110110 |
|           | 3: Shift right divisor | 000000   | 000010001000 | 000000110110 |
| 4         | 1: Rem = Rem - Div | 000000   | 000010001000 | 111110101110 |
|           | 2b: Rem < 0 -> recover Rem, Shift left Q, Q[0] = 0 | 000000   | 000010001000 | 000000110110 |
|           | 3: Shift right divisor | 000000   | 000001000100 | 000000110110 |
| 5         | 1: Rem = Rem - Div | 000000   | 000001000100 | 111111110010 |
|           | 2b: Rem < 0 -> recover Rem, Shift left Q, Q[0] = 0 | 000000   | 000001000100 | 000000110110 |
|           | 3: Shift right divisor | 000000   | 000000100010 | 000000110110 |
| 6         | 1: Rem = Rem - Div    | 000000   | 000000100010 | 000000010100 |
|           | 2b: Rem >= 0 -> Shift left Q, Q[0] = 1  | 000001   | 000000100010 | 000000010100 |
|           | 3: Shift right divisor  | 000001   | 000000010001 | 000000010100 |
| 7         | 1: Rem = Rem - Div   | 000001   | 000000010001 | 000000000011 |
|           | 2b: Rem >= 0 -> Shift left Q, Q[0] = 1 | 000011   | 000000010001 | 000000000011 |
|           | 3: Shift right divisor | 000011   | 000000001000 | 000000000011 |
### Step 4
According to the table above we have the Quotient is $000011$ and the Remainder is $000000000011$

We trans them into decimal format:

$(000011)_2 = (3)_{10}$

$(000000000011)_2 = (3)_{10}$

We can test whether the result is correct:

$54 \div 17 = 3 ··· 3$

So it is correct.
## Problem 5
### Question A
#### Step 1 Binary Representation
$(0x3e800000)_{16} = (0011 1110 1000 0000 0000 0000 0000 0000)_{2}$
#### Step 2 Transform 
Signs: $0$ -> Positive number

Exponent: $(01111101)_2 = (125)_{10}$

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;$125-127=-2$

Fraction: `000 0000 0000 0000 0000 0000` (23bits)

#### Step 3 Calculate
$1 * 1.0 * 2^{-2} = 0.25$

So the value is $0.25$
### Question B
#### Step 1 Binary Representation
$(12.5)_{10} = (1100.1)_2 = (1.1001 * 2^3)_{2}$
#### Step 2 Transform
Signs: $0$ Because $12.5$ is a positive number.

Exponent: $3 + 127 = 130$

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;$(130)_{10} = (10000010)_2$

Fraction: `100 1000 0000 0000 0000 0000` (23bits)
#### Step 3 Combination
|Signs|Exponent|Fraction|
|:----:|:----:|:----:|
|$0$|$10000010$|$100 1000 0000 0000 0000 0000$|

So the answer is `0100 0001 0100 1000 0000 0000 0000 0000`
### Question C
#### Step 1 Binary Representation
|Number|Hex|Binary|Binary(Breakdown)|
|:----:|:----:|:----:|:----:|
|A|$0x3F800000$|`0011 1111 1000 0000 0000 0000 0000 0000`|`0 01111111 00000000000000000000000`|
|B|$0xBF400000$|`1011 1111 0100 0000 0000 0000 0000 0000`|`1 01111110 10000000000000000000000`|

A = $1.0 * 2^0$ , B = $-1.5 * 2^{-1}$
#### Step 2 Align Exponents
Calculate the difference of two exponents:
$0-(-1)=1$

Shift the smaller exponent right by 1 bit

So, $A=(1*2^0)_2$ , $B=(-0.11*2^0)_2$

#### Step 3 Add Significands
$1.000 * 2^0 + (-0.110 8 2^0) = 0.010 * 2^0$

#### Step 4 Normalize Results
$0.010 * 2^0 = 1.0 * 2^{-2}$

$-2 + 127 = 125$

#### Step 5 Packed Results
Signs: $0$

Exponents: $(125)_{10} = (01111101)_2$

Fraction: `000 0000 0000 0000 0000 0000 0000` (23 bits)

So the binary form of the result is:
`0 01111101 00000000000000000000000`

And the Hex form is:
`0x3E800000`

#### Verification
This is not a step, is just a test to see whether the result is correct.

$1 * 10^{-2} = 0.25$

$A-B = 1.0 * 2^0 - 1.5 * 2^{-1} = 1 - 0.75 = 0.25$

So we can see the result is $0.25$

