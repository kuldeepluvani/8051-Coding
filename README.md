# 8051-Coding

16 bit multiplication program in 8051
This is 16 bit multiplication program in assembly language in 8051 micro controller with easiest algorithm. Each number is divided in two 8 bit words and they are called MSB1,LSB1 and MSB2,LSB2.

Suppose we have two hex numbers "ABCD" & "EFGH". Here each alphabet is 4 bit binary number. In 8051 we can multiply 8 bit numbers using MUL instruction.

Here AB = MSB1 (most significant 4 bits of 1st number)
         CD = LSB1 (least significant 4 bits of 1st number)
         EF = MSB2 (most significant 4 bits of 2nd number)
         GH = LSB2 (least significant 4 bits of 2nd number)


MOV R1,MSB1
MOV R2,MSB2
MOV R3,LSB1
MOV R4,LSB2

MOV A,R3
MOV B,R4
MUL AB
MOV 20H,A
MOV 21H,B

MOV A,R3
MOV B R2
MUL AB
MOV 22H,B
ADDC A,21H
MOV 21H,A

MOV A,R1
MOV B,R4
MUL AB
ADDC A,21H
MOV 21H,A
MOV A,B
ADDC A,22H
MOV 22H,A

MOV A,R1
MOV B,R2
MUL AB
ADDC A,22H
MO 22H,A
MOV A,B
ADDC A,#00H
MOV 23H,A


The answer would be in following address, (23H 22H 21H 20H).

Example:

You have two 16 bit Hex number. FFFF & EF9D.

So here,

AB = FF(In Hex)
CD = FF(In Hex)
EF = EF (In Hex)
GH = 9D (In Hex)

After simulating this program with following values, you will find following values in below mention addresses,

On 23H address values is EF (In Hex).
On 22H address values is 9C (In Hex).
On 21H address values is 10 (In Hex).
On 20H address values is 63 (In Hex).

So your answer would be EF9C1063 (In Hex)
