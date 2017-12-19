# Java signed number representation

## Introduction

Before we dive into how java represents signed numbers, let's be clear on certain things.

In Java, all the primitive data types which are used to represent numbers are signed.

A 4-bit number means a number that can be represented by 4 bits. This can range from 0000 - 1111. The same goes for 8 bit, 16 bit, 32 bit...

## Additional points to remember

- Notations like 0xff, 0b1100 represents numbers in their respective bases. 0x represents hexadecimal numbers which have base 16. 0b represents binary numbers which have base 2. 0xff is equal to 255 and 0b1100 is 12 in the decimal system.

- A one's complement is obtained by inverting all the bits. Eg. One's complement of 1010 is 0101.

- Two's complement is obtained by adding 1 to the one's complement of a number. Eg. Two's complement of 1010 is 0101 + 0001 which is 0110.

## Numbers in memory

In Java, all numbers are signed data types. MSB or the Most Significant Bit represents the sign of the number. Check the below code fragment.

```
byte b = (byte) 0b11111111;
// b is initialised with -1
```

How this happens is, since byte stores 8-bit numbers and the MSB represents the sign, the decimal representation of 111111111 can be calculated as -(1 * 2^8) + (1 * 2^7) + ... (1 * 2^0).

Let's look at byte data type which can store 8 bit. This means it can store numbers from 00000000 to 11111111. This means byte can store numbers from -128 to 127. Similarly, int is a 32-bit data type and can store numbers from -(2^31) to (2^31) - 1.

To make things more clear let's have a new signed data type called min which is a 4-bit data type. sin can store numbers from -8 to 7.

```
min m = (min) 0x1111
// m is initialised with -1
```

The binary of 2 is 0010, and that of -2 is 1110. 2 can be converted to binary as 0 * 2^3 + 0 * 2^2 + 1 * 2^1 + 0 * 2^0. -2's conversion is -(1 * 2^3) + 1 * 2^2 + 1 * 2^1 + 0 * 2^0. Since MSB represents the sign, whenever it's 1 the number is negative.

This is the same with all the data types in Java. int is a 32 bit data type and stores numbers from -2,147,483,648 to 2,147,483,647. Check the below code.

```
int i = -1;
String s = Integer.toBinaryString(i)
// m is assigned with 11111111111111111111111111111111 
```

## What happens when number overflow

Let's get back to the byte data type. The maximum positive value byte can store is 127 which is 01111111. So what happens when you add 1 to it. 

```
byte b = 127;
b = b + 1
```

Here we have a situation where number overflows. 127 is 01111111 and adding 00000001 to it leaves us with 10000000. Now the decimal conversion of the above number is -(1 * 2^7) + 0 * 2^6 + ... + 0 * 2^0 which is -128.

## Further links

[https://stackoverflow.com/a/13422442/2356570](https://stackoverflow.com/a/13422442/2356570)

[http://www.cs.grin.edu/~walker/courses/161.sp10/readings/reading-binary.shtml](http://www.cs.grin.edu/~walker/courses/161.sp10/readings/reading-binary.shtml)
