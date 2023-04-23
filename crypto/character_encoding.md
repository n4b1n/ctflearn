## Character Encoding

In the computing industry, standards are established to facilitate information interchanges among American coders. Unfortunately, I've made communication a little bit more difficult. Can you figure this one out? 

cipherText: 41 42 43 54 46 7B 34 35 43 31 31 5F 31 35 5F 55 35 33 46 55 4C 7D

Flag: ABCTF{45C11_15_U53FUL}

Solved date: 2023-04-23

----------------------------------

Note: I used CyberChef to convert hex to plaintext but there are some other methods too.

### xxd

xxd creates a hex dump of a given file or standard input.

echo <hex value> | xxd -r -p

-r (revert) converts the hexdump into binary.
-r -p (revert and plain) using this combination we can read plain hexadecimal dumps without line number information and without a particular column layout.

--------------------------------------

### Python

print(*[chr(int(i, base=16)) for i in ['41', '42', '43', '54', '46', '7B', '34', '35', '43', '31', '31', '5F', '31', '35', '5F', '55', '35', '33', '46', '55', '4C', '7D']], sep='')

- chr(int(i, base=16)) -> this converts each hexadecimal value in the list to its corresponding Unicode character.
- for i in ['41', '42', '43', '54', '46', '7B', '34', '35', '43', '31', '31', '5F', '31', '35', '5F', '55', '35', '33', '46', '55', '4C', '7D'] -> this iterates over each hexadecimal value in the list.
- *[...] -> this unpacks the list of characters into separate arguments for the print() function.
- sep='' -> this specifies that there should be no separator between each character when they are printed.
