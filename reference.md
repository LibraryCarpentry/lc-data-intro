---
layout: reference
title: Reference
permalink: /reference/
---

# Regular Expressions cheat cheet

- `[]` defines a range of characters
- `.` matches any character
- `\` is used to escape the following character when that character is a special character. So, for example, a regular expression that found `.com` would be `\.com` because `.` is a special character that matches any character.
- `\d` matches any single digit
- `\w` matches any part of word character (equivalent to `[A-Za-z0-9]`)
- `\s` matches any space, tab, or newline
- `^` asserts the position at the start of the line. So what you put after it will only match if they are the first characters of a line.
- `$` asserts the position at the end of the line. So what you put before it will only match if they are the last characters of a line.
- `\b` adds a word boundary. Putting this either side of a stops the regular expression matching longer variants of words. 
- `*` matches when the preceding character appears any number of times including zero
- `+` matches when the preceding character appears any number of times excluding zero
- `?` matches when the preceding character appears one or zero times
- `{VALUE}` matches the preceding character the number of times define by VALUE; ranges can be specified with the syntax `{VALUE,VALUE}`
- `|` means or
- Check your regex with: regex101 [https://regex101.com/](https://regex101.com/), rexegper [http://regexper.com/](http://regexper.com/), or myregexp [http://myregexp.com/]([http://myregexp.com/])
- Test yourself with: Regex Crossword https://regexcrossword.com/ or our The Multiple Choice Quiz [http://data-lessons.github.io/library-data-intro/05-quiz/](http://data-lessons.github.io/library-data-intro/05-quiz/)
