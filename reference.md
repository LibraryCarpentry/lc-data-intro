---
title: 'Regular Expression Cheat Sheet'
---

## Regular Expression Cheat Sheet

- `[]` defines a range of characters.
- `.` matches any character.
- `\` is used to escape the following character when that character is a special character. So, for example, a regular expression that found '.com' would be `\\.com` because `.` is a special character that matches any character.
- `\d` matches any single digit.
- `\w` matches any part of word character (equivalent to `[A-Za-z0-9]`).
- `\s` matches any space, tab, or newline.
- `^` asserts the position at the start of the line. So what you put after it will only match if they are the first characters of a line.
- `$` asserts the position at the end of the line. So what you put before it will only match if they are the last characters of a line.
- `\b` adds a word boundary. Putting this either side of a word stops the regular expression matching longer variants of words.
- `*` matches the preceding element zero or more times. For example, `ab*c` matches 'ac', 'abc', 'abbbc', etc.
- `+` matches the preceding element one or more times. For example, `ab+c` matches 'abc', 'abbbc' but not 'ac'.
- `?` matches when the preceding character appears zero or one time.
- `{VALUE}` matches the preceding character the number of times define by VALUE; ranges can be specified with the syntax `{VALUE,VALUE}`.
- `|` means or.


