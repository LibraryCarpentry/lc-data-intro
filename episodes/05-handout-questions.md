---
title: "Introduction to Data - Handout and Quiz"
teaching: 0
exercises: 30
questions:
- what does `Fr[ea]nc[eh]` match?
objectives:
- understand terms, phrases, and concepts in software development and data science
- identify and use best practice in data structures
- use regular expressions in searches
keypoints:
- regular expressions reference guide
---

# Regular Expressions

- `[]` define a list or range of characters to be found
- `.` matches any character at all
- `\d` matches any single digit
- `\w` matches and part of word character (equivalent to [A-Za-z0-9_] )
- `\s` matches any space, tab, or newline
- `\b` adds a word boundary
- `^` asserts the position at the start of the line. So what you put after it will only match the first characters of a line or contents of a cell.
- `$` asserts the position at the end of the line. So what you put after it will only match the last character of a line of contents of a cell.
- `*` matches when the preceding character appears any number of times including zero
- `+` matches when the preceding character appears any number of times excluding zero
- `?` matches when the preceding character appears one or zero times
- `{VALUE}` matches the preceding character the number of times define by VALUE; ranges can be specified with the syntax `{VALUE,VALUE}`
- `|` simply means or

## Check your regex with:
- regex101 [https://regex101.com/](https://regex101.com/)
- rexegper [http://regexper.com/](http://regexper.com/)
- myregexp [http://myregexp.com/]([http://myregexp.com/])

## Test yourself with:
- Regex Crossword https://regexcrossword.com/
- The Multiple Choice Quiz (below)

# Multiple Choice Quiz

This multiple choice quiz is designed to embed the regex knowledge you learned during this module. We recommend you work through it someone after class (within a week or so). Answers are on the answer sheet.

Q1. What is the special character that matches zero or more characters

- A) `^`
- B) `#`
- C) `*`

Q2. Which of the following matches any space, tab, or newline?

- A) `\s`
- B) `\b`
- C) `$`

Q3. How do you match the string `Foobar` appearing at the beginning of a line?

- A) `$Foobar`
- B) `^Foobar`
- C) `#Foobar`

Q4. How do you match the word `Foobar` appearing at the beginning of a line?

- A) `^Foobar\d`
- B) `^Foobar\b`
- C) `^Foobar\w`

Q5. What does the regular expression `[a-z]` match?

- A) The characters a and z only
- B) All characters between the ranges a to z and A to Z
- C) All characters between the range a to z

Q6. Which of these will match the strings `revolution`, `revolutionary`, and `revolutionaries`?

- A) `revolution[a-z]?`
- B) `revolution[a-z]*`
- C) `revolution[a-z]+`

Q7. Which of these will match the strings `revolution`, `Revolution`, and their plural variants only?

- A) `[rR]evolution[s]+`
- B) `revolution[s]?`
- C) `[rR]evolution[s]?`

Q8. What regular expression matches the strings `dog` or `cat`?

- A) `dog|cat`
- B) `dog,cat`
- C) `dog | cat`

Q9. What regular expression matches the whole words `dog` or `cat`?

- A) `\bdog|cat\b`
- B) `\bdog\b | \bcat\b`
- C) `\bdog\b|\bcat\b`

Q10. What do we put after a character to match strings where that character appears 2 to 4 times in sequence?

- A) `{2,4}`
- B) `{2-4}`
- C) `[2,4]`

Q11. The regular expression `\d{4}` will match what?

- A) Any four character sequence?
- B) Any four digit sequence?
- C) The letter `d` four times?

Q12. If brackets are used to define a group, what would match the regular expression `(,\s[0-9]{1,4}){4},\s[0-9]{1,3}\.[0-9]`?

- A) , 135, 1155, 915, 513, 18.8
- B) , 135, 11557, 915, 513, 18.8
- C) , 135, 1155, 915, 513, 188
