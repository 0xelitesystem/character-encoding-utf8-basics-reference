# ASCII and Unicode

ASCII is an early encoding that maps 128 characters (English letters, digits, punctuation, and control codes) to the numbers 0 through 127, each fitting in a single byte. Unicode is the modern standard that assigns a unique number, called a code point, to every character in every writing system, tens of thousands of them and growing. Unicode is the character set; encodings like UTF-8 are how its code points become bytes.

## ASCII, the starting point

ASCII (the American Standard Code for Information Interchange) defined 128 characters: uppercase and lowercase English letters, the digits 0 through 9, common punctuation, the space, and a set of non-printing control codes. Each fits in seven bits, comfortably within one byte, so in ASCII one character is always exactly one byte. The letter A is 65, a is 97, the digit 0 is 48. ASCII was enough for English text, but it has no room for accented letters, other alphabets, or symbols, which is exactly the limitation Unicode was created to remove.

## Unicode and code points

Unicode gives every character its own permanent number called a code point, written as U+ followed by a hexadecimal value. The letter A is U+0041 (that is 65, the same as ASCII, kept deliberately for compatibility). The euro sign is U+20AC. A face emoji is U+1F600. Unicode currently defines well over a hundred thousand code points covering Latin, Greek, Cyrillic, Arabic, Chinese, emoji, mathematical symbols, and much more. Crucially, a code point is just a number identifying a character. It says nothing yet about how that number is stored as bytes.

## Character set versus encoding

The distinction that trips people up: Unicode is a character set (a numbered catalog of characters), while UTF-8 and UTF-16 are encodings (rules for turning those numbers into bytes). Unicode says the euro sign is U+20AC; UTF-8 says that code point is stored as the three bytes E2 82 AC. You can hold the same Unicode code point and encode it into different byte sequences depending on the encoding chosen. Keeping these two ideas separate, the number versus the bytes, is the key to understanding everything that follows.
