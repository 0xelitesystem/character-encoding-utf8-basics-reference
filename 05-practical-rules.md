# Practical rules

The single practical rule that prevents nearly all text problems is: use UTF-8 everywhere, and declare it explicitly. UTF-8 covers every character in Unicode, is backward compatible with ASCII, is the dominant encoding of the web, and removes byte-order questions. The remaining work is making sure every layer that touches your text (files, databases, network, code) agrees on UTF-8 and says so, rather than leaving it to chance.

## Use UTF-8 for everything you control

Save source files, config files, and documents as UTF-8. Set your database and its tables and columns to a full UTF-8 collation so stored text is not silently truncated or mangled. Configure your editor and terminal to read and write UTF-8. When you generate a file or a response programmatically, specify UTF-8 rather than accepting a platform default that might differ between machines. One encoding, chosen deliberately and applied consistently, is the whole strategy.

## Declare the encoding explicitly

Where a format lets you state the encoding, state it. For web pages, send the HTTP header `Content-Type: text/html; charset=utf-8` and include `<meta charset="utf-8">` near the top of the HTML. For APIs, set the charset on the JSON content type. In code, pass the encoding explicitly when opening files (for example, specifying `encoding="utf-8"`) instead of relying on the operating system default, which can vary. Explicit declarations remove the guessing that causes mojibake.

## Handle length and slicing carefully

Because one character can span multiple bytes, be deliberate about what you are counting or cutting. Measuring string length, truncating to fit a limit, or slicing a substring must operate on characters (or code points), not raw bytes, or you risk splitting a multi-byte character in half and producing invalid text. Use your language's Unicode-aware string operations rather than byte operations for anything user-facing. And when comparing or storing user input, normalize it, since some characters can be represented by more than one code point sequence. Respect the byte-versus-character distinction and these edge cases stop surprising you.
