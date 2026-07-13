# Bytes vs characters

A character is a unit of written language that a human reads, such as the letter A, the digit 7, or the symbol yen. A byte is a unit of computer storage holding a number from 0 to 255. These are not the same thing, and character encoding exists precisely to bridge them: it is the rulebook that decides which byte or bytes stand for which character. Confusing the two is the root of almost every text-handling bug.

## Why they differ

Computers store and transmit only numbers, ultimately bytes. Humans want to read letters, digits, punctuation, and symbols from many writing systems. There is no natural, universal law that says the byte 65 means A; that meaning is a convention someone had to define. Early computing had many competing conventions, which is why text created on one system could look like nonsense on another. A byte is raw storage; a character is meaning; an encoding is the agreement that connects them.

## One character is not always one byte

A tempting but wrong assumption is that one character equals one byte. That held for early English-only systems, but it fails the moment you include accented letters, characters from other scripts, or emoji. In a modern encoding, a single character can occupy one, two, three, or four bytes. This means the number of characters a human sees and the number of bytes stored are different quantities. Length in bytes and length in characters are separate measurements, and treating them as identical breaks the moment text leaves the English alphabet.

## The mental model

Keep three layers separate in your mind. At the top are characters, the abstract letters and symbols. In the middle are code points, the unique numbers a standard assigns to each character. At the bottom are bytes, the actual storage. Encoding is the transformation between code points and bytes; a character set like Unicode is the mapping between characters and code points. When you know which layer you are working at, most confusing text behavior becomes predictable rather than mysterious.
