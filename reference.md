---
layout: reference
title: Reference
permalink: /reference/
---

## Data Intro Cheat Sheet

_____
## Regular Expression

- `[]` defines a range of characters.
- `.` matches any character.
- `\` is used to escape the following character when that character is a special character. So, for example, a regular expression that found '.com' would be `\\.com` because `.` is a special character that matches any character.
- `\d` matches any single digit.
- `\w` matches any part of word character (equivalent to `[A-Za-z0-9]`).
- `\s` matches any space, tab, or newline.
- `^` asserts the position at the start of the line. So what you put after it will only match if they are the first characters of a line.
- `$` asserts the position at the end of the line. So what you put before it will only match if they are the last characters of a line.
- `\b` adds a word boundary. Putting this either side of a stops the regular expression matching longer variants of words.
- `*` matches the preceding element zero or more times. For example, `ab*c` matches 'ac', 'abc', 'abbbc', etc.
- `+` matches the preceding element one or more times. For example, `ab+c` matches 'abc', 'abbbc' but not 'ac'.
- `?` matches when the preceding character appears zero or one time.
- `{VALUE}` matches the preceding character the number of times define by VALUE; ranges can be specified with the syntax `{VALUE,VALUE}`.
- `|` means or.

## References

James Baker , "Preserving Your Research Data," *Programming Historian* (30 April 2014), [http://programminghistorian.org/lessons/preserving-your-research-data.html](http://programminghistorian.org/lessons/preserving-your-research-data.html). The sub-sections 'Plain text formats are your friend' and 'Naming files sensible things is good for you and for your computers' are reworked from this lesson.

Owen Stephens, "Working with Data using OpenRefine", *Overdue Ideas" (19 November 2014), [http://www.meanboyfriend.com/overdue_ideas/2014/11/working-with-data-using-openrefine/](http://www.meanboyfriend.com/overdue_ideas/2014/11/working-with-data-using-openrefine/). The section on 'Regular Expressions' is reworked from this lesson developed by Owen Stephens on behalf of the British Library

Andromeda Yelton, "Coding for Librarians: Learning by Example", *Library Technology Reports* 51:3 (April 2015), doi: [10.5860/ltr.51n3](https://doi.org/10.5860/ltr.51n3)

Fiona Tweedie, "Why Code?", *The Research Bazaar* (October 2014), [http://melbourne.resbaz.edu.au/post/95320810834/why-code](http://melbourne.resbaz.edu.au/post/95320810834/why-code)
