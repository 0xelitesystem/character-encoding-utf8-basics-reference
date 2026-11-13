# Character Encoding and UTF-8 Basics

A plain-language reference on character encoding: how text, which humans read as characters, is stored and transmitted as bytes, which machines actually handle. It covers the difference between bytes and characters, ASCII, Unicode code points, the UTF-8 and UTF-16 encodings, the byte order mark, why garbled text (mojibake) happens, and the practical rule that saves you from all of it: use UTF-8 everywhere.

## The core idea

Character encoding is the agreed mapping between the characters humans read and the bytes computers store. A character like the letter A is an abstract idea; a byte is a number from 0 to 255; an encoding is the rulebook that says which bytes represent which characters. Unicode gives every character a unique number called a code point, and an encoding like UTF-8 defines how to turn those code points into actual bytes. When the software that writes text and the software that reads it use the same encoding, text survives intact; when they disagree, you get garbled output.

## What is inside

- [01-bytes-vs-characters.md](01-bytes-vs-characters.md) the core distinction encoding exists to bridge.
- [02-ascii-and-unicode.md](02-ascii-and-unicode.md) from 128 characters to every character, via code points.
- [03-utf8-and-utf16.md](03-utf8-and-utf16.md) how code points become bytes, with a multi-byte example.
- [04-bom-and-mojibake.md](04-bom-and-mojibake.md) the byte order mark and why text turns to garbage.
- [05-practical-rules.md](05-practical-rules.md) use UTF-8 everywhere, and how to actually do it.

## The stance

This reference treats encoding as a solved problem with one right default: UTF-8 for storage, transmission, and interchange, declared explicitly everywhere it can be. Nearly every encoding bug comes from a mismatch between what wrote the bytes and what read them. Pick UTF-8, declare it, and the whole class of problems mostly disappears.

## More

Part of a catalog of single-file browser tools and plain-language references, all MIT licensed and dependency-free: [0xelitesystem.github.io](https://0xelitesystem.github.io/). Built by [elitesystem.ai](https://elitesystem.ai).

## License

MIT. Copyright RBL Industries LLC 2026.
