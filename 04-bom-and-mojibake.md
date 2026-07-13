# BOM and mojibake

A byte order mark (BOM) is an optional invisible marker at the very start of a text file that signals the encoding and, for UTF-16, the byte order. Mojibake is the garbled text you see when bytes written in one encoding are read as though they were another. Both are symptoms of the same underlying issue: uncertainty or disagreement about which encoding a stream of bytes uses.

## What a BOM is

The byte order mark is the code point U+FEFF placed at the start of a file. In UTF-16 it serves a real purpose: it tells the reader whether the two-byte units are stored big-endian or little-endian, which changes how the bytes pair up. In UTF-8 there is no byte-order ambiguity, so a UTF-8 BOM (the bytes EF BB BF) is optional and usually unnecessary. It can even cause trouble, because tools that do not expect it may treat those three bytes as visible garbage at the start of the file or break scripts that must begin with an exact character. Default to writing UTF-8 without a BOM.

## Why mojibake happens

Mojibake is what you get when text is written with one encoding and read with a different one. The bytes are intact, but the reader applies the wrong rulebook, so multi-byte characters get split apart and reinterpreted as unrelated symbols. The classic example: a word containing an accented letter, saved as UTF-8, then opened by a program assuming an older single-byte encoding. The accented character's two UTF-8 bytes get shown as two separate strange characters. The data was never corrupted; only the interpretation was wrong.

## How to prevent it

Mojibake is prevented by making the encoding explicit and consistent end to end. Declare the encoding wherever the format allows it: a charset in an HTTP header, a meta charset tag in HTML, an encoding declaration when opening a file in code. Never rely on the reader guessing, because guessing is exactly what goes wrong. If everything that writes and everything that reads a given piece of text agrees it is UTF-8, and says so explicitly, mojibake does not occur. The fix is agreement, declared plainly, not detection after the fact.
