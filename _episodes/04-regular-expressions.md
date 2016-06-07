---
title: "Introduction to Data"
teaching: 20
exercises: 25
questions:
- 
objectives:
- use regular expressions in searches
keypoints:
- 
---

## Regular Expressions

**SLIDE** One of the reason why I have stressed the value of consistent and predictable directory and filenaming conventions is that working in this way enables you to use the computer to select files based on the characteristics of their file name. So, for example, if you have a bunch of files where the first four digits are the year and you only want to do something with files from '2014', then you can. Or if you have 'journal' somewhere in a filename when you have data about journals, you can use the computer to select just those files then do something with them. Equally, using plain text formats means that you can go further and select files or elements of files based on characteristics of the data *within* files.

A powerful means of doing this selecting based on file characteristics is to use regular expressions, often abbreviated to regex. A regular expression is a sequence of characters that define a search pattern, mainly for use in pattern matching with strings, or string matching, i.e. "find and replace"-like operations. Regular expressions are typically surrounded by `/` characters, though we will (mostly) ignore those for ease of comprehension. Regular expressions will let you:

- Match on types of character (e.g. 'upper case letters', 'digits', 'spaces', etc.)
- Match patterns that repeat any number of times
- Capture the parts of the original string that match your pattern

As most computational software has regular expression functionality built in and as many computational tasks in libraries are built around complex matching, it is good place for Library Carpentry to start in earnest.

**SLIDE** A very simple use of a regular expression would be to locate the same word spelled two different ways. For example the regular expression `organi[sz]e` matches both "organise" and "organize".

A very simple use of a regular expression would be to locate the same word spelled two different ways. For example the regular expression `organi[sz]e` matches both "organise" and "organize".

But it would also find `reorganise`. So there are a bunch of special syntax that help us be more precise.

The first we've seen: square brackets can be used to define a list or range of characters to be found. So: **SLIDE**

- `[ABC]` matches A or B or C
- `[A-Z]` matches any upper case letter
- `[A-Za-z0-9]` matches any upper or lower case letter or any digit (note: this is case-sensitive)

Then there are: **SLIDE**

- `.` matches any character
- `\d` matches any single digit
- `\w` matches any part of word character (equivalent to `[A-Za-z0-9]`)
- `\s` matches any space, tab, or newline
- `\` NB: this is also used to escape the following character when that character is a special character. So, for example, a regular expression that found `.com` would be `\.com` because `.` is a special character that matches any character.
- `^` asserts the position at the start of the line. So what you put after it will only match the first characters of a line or contents of a cell.
- `$` asserts the position at the end of the line. So what you put after it will only match the last character of a line of contents of a cell.
- `\b` adds a word boundary. Putting this either side of a stops the regular expression matching longer variants of words. So:
	- the regular expression `foobar` will match `foobar` and find `666foobar`, `foobar777`, `8thfoobar8th` et cetera
	- the regular expression `\bfoobar` will match `foobar` and find `foobar777`
	- the regular expression `foobar\b` will match `foobar` and find `666foobar`
	- the regular expression `\bfoobar\b` will find `foobar`

**SLIDE** {**Question**}: So, what is `^[Oo]rgani.e\b` going to match.

Other useful special characters are **SLIDE**:

- `*` matches when the preceding character appears any number of times including zero
- `+` matches when the preceding character appears any number of times excluding zero
- `?` matches when the preceding character appears one or zero times
- `{VALUE}` matches the preceding character the number of times define by VALUE; ranges can be specified with the syntax `{VALUE,VALUE}`
- `|` means or.

{**Questions**}: So, what are these going to match?

- **SLIDE** `^[Oo]rgani.e\w*`
- **SLIDE** `[Oo]rgani.e\w+$`
- **SLIDE** `^[Oo]rgani.e\w?\b`
- **SLIDE** `^[Oo]rgani.e\w?$`
- **SLIDE** `\b[Oo]rgani.e\w{2}\b`
- **SLIDE** `\b[Oo]rgani.e\b|\b[Oo]rgani.e\w{1}\b`

**SLIDE** This logic is super useful when you have lots of files in a directory, when those files have logical file names, and when you want to isolate a selection of files. Or for looking at cells in spreadsheets for certain values. Or for extracting some data from a column of a spreadsheet to make  new columns. I could go on. The point is, it is super useful in many contexts. To embed this knowledge we won't - however - be using computers. Instead we'll use pen and paper. I want you to work in teams of 4 to work through the exercises in the handout. I have an answer sheet over here if you want to check where you've gone wrong. When you finish, I'd like you to split your team into two groups and write each other some tests. These should include a) strings you want the other team to write regex for and b) regular expressions you want the other team to work out what they would match. Then test each other on the answers. If you want to check your logic, use [regex101](https://regex101.com/), [myregexp](http://myregexp.com/) or [regexper.com](http://regexper.com/): the first two help you see what text your regular expression will match, the latter visualises the workflow of a regular expression.

### Exercise

What does `Fr[ea]nc[eh]` match?

- this matches `France`, `French`, `Frence`, and `Franch`. It would find words where there were characters either side of these so `Francer`, `foobarFrench`, or `Franch911`.

What does `Fr[ea]nc[eh]$` match?

- this matches `France`, `French`, `Frence`, and `Franch` at the end of a line. It would find words where there were characters before these so `foobarFrench`.

What would match the strings `French` and `France` only that appear at the beginning of a line?

- `^France|^French` This would also find words where there were characters after `French` such as `Frenchness`.

How do you match the whole words `colour` and `color` (case insensitive)?

- In real life, you *should* only come across the case insensitive variations `colour`, `color`, `Colour`, `Color`, `COLOUR`, and `COLOR` (rather than, say, `coLour`. So one option would be `\b[Cc]olou?r\b|\bCOLOU?R\b`. This can, however, get quickly quite complex. An option we've not discussed is to take advantage of the `/` delimiters and add an ignore case flag: so `/colou?r/i` will match all case insensitive variants of `colour` and `color`.

How would you find the whole-word `headrest` and or the 2-gram `head rest` but not `head  rest` (that is, with two spaces between `head` and `rest`?

- `\bhead ?rest\b`. Note that although `\bhead\s?rest\b` does work, it would also match zero or one tabs or newline characters between `head` and `rest`. In most real world cases it should, however, be fine :)

How would you find a 4 letter word that ends a string and is preceded by at least one zero?

- `0+[a-z]{4}\b`

How do you match any 4 digit string anywhere?

- `\d{4}`. Note this will match 4 digit strings only but will find them within longer strings of numbers.

How would you match the date format `dd-MM-yyyy`?

- `\b\d{2}-\d{2}-\d{4}\b` In most real world situations, you are likely to want word bounding here (but it may depend on your data).

How would you match the date format `dd-MM-yyyy` or `dd-MM-yy` at the end of a string only?

- `\d{2}-\d{2}-\d{2,4}$`

How would you match publication formats such as `British Library : London, 2015` and `Manchester University Press: Manchester, 1999`?

- `.* : .*, \d{4}` You will find that this matches any text you put before `British` or `Manchester`. In this case, this regular expression does a good job on the first look up and may be need to be refined on a second depending on your real world application.

## Next module

**SLIDE**

Shell. Instructions of what to install per operating system on the Github page.

## References

James Baker , "Preserving Your Research Data," *Programming Historian* (30 April 2014), [http://programminghistorian.org/lessons/preserving-your-research-data.html](http://programminghistorian.org/lessons/preserving-your-research-data.html). The sub-sections 'Plain text formats are your friend' and 'Naming files sensible things is good for you and for your computers' are reworked from this lesson.

Owen Stephens, "Working with Data using OpenRefine", *Overdue Ideas" (19 November 2014), [http://www.meanboyfriend.com/overdue_ideas/2014/11/working-with-data-using-openrefine/](http://www.meanboyfriend.com/overdue_ideas/2014/11/working-with-data-using-openrefine/). The section on 'Regular Expressions' is reworked from this lesson developed by Owen Stephens on behalf of the British Library

Andromeda Yelton, "Coding for Librarians: Learning by Example", *Library Technology Reports* 51:3 (April 2015), doi: [10.5860/ltr.51n3](http://dx.doi.org/10.5860/ltr.51n3)

Fiona Tweedie, "Why Code?", *The Research Bazaar* (October 2014), [http://melbourne.resbaz.edu.au/post/95320810834/why-code](http://melbourne.resbaz.edu.au/post/95320810834/why-code)
