# UTF-8 and UTF-16

UTF-8 and UTF-16 are the two most common encodings that turn Unicode code points into bytes. UTF-8 uses one to four bytes per character and is backward compatible with ASCII, which makes it the default for the web and for files. UTF-16 uses two or four bytes per character and appears mostly inside certain programming platforms and older systems. UTF-8 is the one you should reach for.

## How UTF-8 works

UTF-8 is a variable-width encoding: it uses as few bytes as a character needs, from one to four. Code points 0 through 127 (all of ASCII) encode as a single byte identical to their ASCII value, so any plain ASCII file is already valid UTF-8. Code points above that use two, three, or four bytes, with the leading bits of each byte signaling how many bytes the character spans. This design is self-synchronizing (you can tell where a character starts by looking at the byte pattern) and space-efficient for text dominated by ASCII, which is most of the web.

## A concrete multi-byte example

Take the euro sign, code point U+20AC. In UTF-8 it encodes as three bytes: E2 82 AC (in decimal, 226 130 172). So the single character a human sees occupies three bytes of storage. Compare the string "A euro" versus "A euro sign here": the letters are one byte each, but that euro glyph is three. Another example: the face emoji U+1F600 encodes in UTF-8 as four bytes, F0 9F 98 80. This is exactly why byte count and character count differ. One visible character, three or four stored bytes.

## How UTF-16 differs

UTF-16 encodes most common characters in exactly two bytes and less common ones (like emoji) in four bytes using a mechanism called surrogate pairs. It is not backward compatible with ASCII: the letter A, one byte in ASCII and UTF-8, becomes two bytes in UTF-16. UTF-16 shows up inside some language runtimes and file formats for historical reasons, but for files, network transfer, and web pages it wastes space on ASCII-heavy text and introduces byte-order complications. Unless a platform forces UTF-16 on you internally, prefer UTF-8 for anything you store or send.
