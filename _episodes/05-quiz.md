---
title: "Introduction to Data - Multiple Choice Quiz"
teaching: 0
exercises: 30
questions:
- What does `Fr[ea]nc[eh]` match?
objectives:
- Test knowledge of use of regular expressions in searches
keypoints:
- Regular expressions reference guide
---

# Multiple Choice Quiz

This multiple choice quiz is designed to embed the regex knowledge you learned during this module. We recommend you work through it sometime after class (within a week or so). Answers are on the answer sheet.

Q1. What is the special character that matches zero or more characters

- A) `^`
- B) `#`
- C) `*`

Q2. Which of the following matches any space, tab, or newline?

- A) `\s`
- B) `\b`
- C) `$`

Q3. How do you match the string `Confident` appearing at the beginning of a line?

- A) `$Confident`
- B) `^Confident`
- C) `#Confident`

Q4. How do you match the word `Confidential` appearing at the beginning of a line?

- A) `^Confidential\d`
- B) `^Confidential\b`
- C) `^Confidential\w`

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
