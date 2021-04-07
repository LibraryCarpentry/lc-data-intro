---
title: "Regular Expressions"
teaching: 20
exercises: 15
questions:
- How can you imagine using regular expressions in your work?
objectives:
- Use regular expressions in searches
keypoints:
- Regular expressions are a language for pattern matching.
---

## Regular expressions

Regular expressions are a concept and an implementation used in many different programming environments for sophisticated pattern matching. They are an incredibly powerful tool that can amplify your capacity to find, manage, and transform data and files. 

A regular expression, often abbreviated to *regex*, is a method of using a sequence of characters to define a search to match strings, i.e. "find and replace"-like operations. In computation, a 'string' is a contiguous sequence of symbols or values. For example, a word, a date, a set of numbers (e.g., a phone number), or an alphanumeric value (e.g., an identifier). A string could be any length, ranging from empty (zero characters) to one that spans many lines of text (including line break characters). The terms 'string' and 'line' are sometimes used interchangeably, even when they are not strictly the same thing.

In library searches, we are most familiar with a small part of regular expressions known as the "wild card character," but there are many more features to the complete regular expressions syntax. Regular expressions will let you:

- Match on types of characters (e.g. 'upper case letters', 'digits', 'spaces', etc.).
- Match patterns that repeat any number of times.
- Capture the parts of the original string that match your pattern.

Regular expressions rely on the use of literal characters and metacharacters. A metacharacter is any American Standard Code for Information Interchange (ASCII) character that has a special meaning. By using metacharacters and possibly literal characters, you can construct a regex for finding strings or files that match a pattern rather than a specific string. For example, say your organization wants to change the way they display telephone numbers on their website by removing the parentheses around the area code. Rather than search for each specific phone number (that could take forever and be prone to error) or searching for every open parenthesis character (could also take forever and return many false-positives), you could search for the pattern of a phone number. 

Since regular expressions defines some ASCII characters as "metacharacters" that have more than their literal meaning, it is also important to be able to "escape" these metacharacters to use them for their normal, literal meaning. For example, the period `.` means "match any character", but if you want to match a period then you will need to use a `\` in front of it to signal to the regular expression processor that you want to use the period as a plain old period and not a metacharacter. That notation is called "escaping" the special character. The concept of "escaping" special characters is shared across a variety of computational settings, including markdown and Hypertext Markup Language (HTML).


> ## Regex Syntax and interoperability
>  Most regular expression implementations employ similar syntaxes and metacharacters (generally influenced by the regex syntax of a programming language called Perl), and they behave similarly for most pattern-matching in this lesson. But there are differences, often subtle, in each, so it's always a good practice to read the application or language's documentation whenever available, especially when you start using more advanced regex features. Some programs, notably many UNIX command line programs (for more on UNIX see our '[Shell Lesson](https://librarycarpentry.org/lc-shell/)'), use an older regex standard (called 'POSIX regular expressions') which is less feature-rich and uses different metacharacters than Perl-influenced implementations. For the purposes of our lesson, you don't need to worry too much about all this, but if you want to follow up on this see [this detailed syntax comparison](https://gist.github.com/CMCDragonkai/6c933f4a7d713ef712145c5eb94a1816).
{: .callout}

A very simple use of a regular expression would be to locate the same word spelled two different ways. For example the regular expression `organi[sz]e` matches both `organise` and `organize`. But because it locates all matches for the pattern in the file, not just for that word, it would also match `reorganise`, `reorganize`, `organises`, `organizes`, `organised`, `organized`, etc.

### Learning common regex metacharacters
Square brackets can be used to define a list or range of characters to be found. So:

- `[ABC]` matches A or B or C.
- `[A-Z]` matches any upper case letter.
- `[A-Za-z]` matches any upper or lower case letter.
- `[A-Za-z0-9]` matches any upper or lower case letter or any digit.

Then there are:

- `.` matches any character.
- `\d` matches any single digit.
- `\w` matches any part of word character (equivalent to `[A-Za-z0-9]`).
- `\s` matches any space, tab, or newline.
- `\` used to escape the following character when that character is a special character. So, for example, a regular expression that found `.com` would be `\.com` because `.` is a special character that matches any character.
- `^` is an "anchor" which asserts the position at the start of the line. So what you put after the caret will only match if they are the first characters of a line. The caret is also known as a circumflex.
- `$` is an "anchor" which asserts the position at the end of the line. So what you put before it will only match if they are the last characters of a line.
- `\b` asserts that the pattern must match at a word boundary. Putting this either side of a word stops the regular expression matching longer variants of words. So:
	- the regular expression `mark` will match not only `mark` but also find `marking`, `market`, `unremarkable`, and so on.
	- the regular expression `\bword` will match `word`, `wordless`, and `wordlessly`.
	- the regular expression `comb\b` will match `comb` and `honeycomb` but not `combine`.
	- the regular expression `\brespect\b` will match `respect` but not `respectable` or `disrespectful`.

So, what is `^[Oo]rgani.e\b` going to match?

> ## Using special characters in regular expression matches
> What will the regular expression `^[Oo]rgani.e\b` match?
>
> > ## Solution
> > ~~~
> > organise
> > organize
> > Organise
> > Organize
> > organife
> > Organike
> > ~~~
> > Or, any other string that starts a line, begins with a letter `o` in lower or capital case, proceeds with `rgani`, has any character in the 7th position, and ends with the letter `e`.
> > [See solution visualised on Regexper.com](https://regexper.com/#%5E%5BOo%5Drgani.e)
> {: .solution}
{: .challenge}

Other useful special characters are:

- `*` matches the preceding element zero or more times. For example, ab*c matches "ac", "abc", "abbbc", etc.
- `+` matches the preceding element one or more times. For example, ab+c matches "abc", "abbbc" but not "ac".
- `?` matches when the preceding character appears zero or one time.
- `{VALUE}` matches the preceding character the number of times defined by VALUE; ranges, say, 1-6, can be specified with the syntax `{VALUE,VALUE}`, e.g. `\d{1,9}` will match any number between one and nine digits in length.
- `|` means **or**.
- `/i` renders an expression case-insensitive (equivalent to `[A-Za-z]`).

So, what are these going to match?

> ## ^[Oo]rgani.e\w*
> What will the regular expression `^[Oo]rgani.e\w*` match?
>
> > ## Solution
> > ~~~
> > organise
> > Organize
> > organifer
> > Organi2ed111
> > ~~~
> > Or, any other string that starts a line, begins with a letter `o` in lower or capital case, proceeds with `rgani`, has any character in the 7th position, follows with letter `e` and zero or more characters from the range `[A-Za-z0-9]`.
> {: .solution}
{: .challenge}

> ## [Oo]rgani.e\w+$
> What will the regular expression `[Oo]rgani.e\w+$` match?
>
> > ## Solution
> > ~~~
> > organiser
> > Organized
> > organifer
> > Organi2ed111
> > ~~~
> > Or, any other string that ends a line, begins with a letter `o` in lower or capital case, proceeds with `rgani`, has any character in the 7th position, follows with letter `e` and **at least one or more** characters from the range `[A-Za-z0-9]`.
> {: .solution}
{: .challenge}

> ## ^[Oo]rgani.e\w?\b
> What will the regular expression `^[Oo]rgani.e\w?\b` match?
>
> > ## Solution
> > ~~~
> > organise
> > Organized
> > organifer
> > Organi2ek
> > ~~~
> > Or, any other string that starts a line, begins with a letter `o` in lower or capital case, proceeds with `rgani`, has any character in the 7th position, follows with letter `e`, and ends with **zero or one** characters from the range `[A-Za-z0-9]`.
> {: .solution}
{: .challenge}

> ## ^[Oo]rgani.e\w?$
> What will the regular expression `^[Oo]rgani.e\w?$` match?
>
> > ## Solution
> > ~~~
> > organise
> > Organized
> > organifer
> > Organi2ek
> > ~~~
> > Or, any other string that starts and ends a line, begins with a letter `o` in lower or capital case, proceeds with `rgani`, has any character in the 7th position, follows with letter `e` and **zero or one characters** from the range `[A-Za-z0-9]`.
> {: .solution}
{: .challenge}

> ## \b[Oo]rgani.e\w{2}\b
> What will the regular expression `\b[Oo]rgani.e\w{2}\b` match?
>
> > ## Solution
> > ~~~
> > organisers
> > Organizers
> > organifers
> > Organi2ek1
> > ~~~
> > Or, any other string that begins with a letter `o` in lower or capital case after a word boundary, proceeds with `rgani`, has any character in the 7th position, follows with letter `e`, and ends with **two** characters from the range `[A-Za-z0-9]`.
> {: .solution}
{: .challenge}

> ## \b[Oo]rgani.e\b|\b[Oo]rgani.e\w{1}\b
> What will the regular expression `\b[Oo]rgani.e\b|\b[Oo]rgani.e\w{1}\b` match?
>
> > ## Solution
> > ~~~
> > organise
> > Organi1e
> > Organizer
> > organifed
> > ~~~
> > Or, any other string that begins with a letter `o` in lower or capital case after a word boundary, proceeds with `rgani`, has any character in the 7th position, and end with letter `e`, or any other string that begins with a letter `o` in lower or capital case after a word boundary, proceeds with `rgani`, has any character in the 7th position, follows with letter `e`, and ends with a single character from the range `[A-Za-z0-9]`.
> {: .solution}
{: .challenge}

This logic is useful when you have lots of files in a directory, when those files have logical file names, and when you want to isolate a selection of files. It can be used for looking at cells in spreadsheets for certain values, or for extracting some data from a column of a spreadsheet to make new columns. There are many other contexts in which regex is useful when using a computer to search through a document, spreadsheet, or file structure. Some real-world use cases for regex are included on an [ACRL Tech Connect blog](https://acrl.ala.org/techconnect/post/fear-no-longer-regular-expressions/) .


To embed this knowledge we won't - however - be using computers. Instead we'll use pen and paper for now. 


### Exercise

Work in teams of four to six on the exercises below. When you think you have the right answer, check it against the solution. 

When you finish, split your team into two groups and write each other some tests. These should include a) strings you want the other team to write regex for and b) regular expressions you want the other team to work out what they would match. 

Then test each other on the answers. If you want to check your logic use [regex101](https://regex101.com/), [myregexp](http://myregexp.com/), [regex pal](http://www.regexpal.com/) or [regexper.com](http://regexper.com/): the first three help you see what text your regular expression will match, the latter visualises the workflow of a regular expression.

> ## Using square brackets
> What will the regular expression `Fr[ea]nc[eh]` match?
>
> > ## Solution
> > ~~~
> > French
> > France
> > Frence
> > Franch
> > ~~~
> > Note that the way this regular expression is constructed, it will match misspellings such as `Franch` and `Frence`. Lacking an "anchor" such as `^` or `\b`, this will also find strings where there are characters to either side of the regular expression, such as `in French`, `France's`, `French-fried`.
> {: .solution}
{: .challenge}

> ## Using dollar signs
> What will the regular expression `Fr[ea]nc[eh]$` match?
>
> > ## Solution
> > ~~~
> > French
> > France
> > Frence
> > Franch
> > ~~~
> > This will match the pattern only when it appears at the end of a line. It will also find strings with other characters coming _before_ the pattern, for example, `in French` or `faux-French`.
> {: .solution}
{: .challenge}

> ## Introducing options
> What would match the strings `French` and `France` that appear at the beginning of a line?
>
> > ## Solution
> > ~~~
> > ^France|^French
> > ~~~
> > This will also find words where there were characters after `French` such as `Frenchness`.
> {: .solution}
{: .challenge}

> ## Case insensitivity
> How do you match the whole words `colour` and `color` (case insensitive)?
>
> > ## Solutions
> > ~~~
> > \b[Cc]olou?r\b|\bCOLOU?R\b
> > /colou?r/i
> > ~~~
> > In real life, you *should* only come across the case insensitive variations `colour`, `color`, `Colour`, `Color`, `COLOUR`, and `COLOR` (rather than, say, `coLour`). So based on what we know, the logical regular expression is `\b[Cc]olou?r\b|\bCOLOU?R\b`. 
> > 
> > An alternative more elegant option we've not discussed is to take advantage of the `/` delimiters and add an 'ignore case' flag.
> > To use these flags, include `/` delimiters before and after the expression then letters after to raise each flag (where `i` is
> > 'ignore case'): 
> > so `/colou?r/i` will match all case insensitive variants of `colour` and `color`.
> {: .solution}
{: .challenge}

> ## Word boundaries
> How would you find the whole word `headrest` and or `head rest` but not <code>head&nbsp;&nbsp;rest</code> (that is, with two spaces between `head` and `rest`?
>
> > ## Solution
> > ~~~
> > \bhead ?rest\b
> > ~~~
> > Note that although `\bhead\s?rest\b` does work, it will also match zero or one tabs or newline characters between `head` and `rest`. So again, although in most real world cases it will be fine, it isn't strictly correct.
> {: .solution}
{: .challenge}

> ## Matching non-linguistic patterns
> How would you find a string that ends with four letters preceded by at least one zero?
>
> > ## Solution
> > ~~~
> > 0+[A-Za-z]{4}\b
> > ~~~
> {: .solution}
{: .challenge}

> ## Matching digits
> How do you match any four-digit string anywhere?
>
> > ## Solution
> > ~~~
> > \d{4}
> > ~~~
> > Note: this will also match four-digit strings within longer strings of numbers and letters.
> {: .solution}
{: .challenge}

> ## Matching dates
> How would you match the date format `dd-MM-yyyy`?
>
> > ## Solution
> > ~~~
> > \b\d{2}-\d{2}-\d{4}\b
> > ~~~
> > Depending on your data, you may choose to remove the word bounding.
> {: .solution}
{: .challenge}

> ## Matching multiple date formats
> How would you match the date format `dd-MM-yyyy` or `dd-MM-yy` at the end of a line only?
>
> > ## Solution
> > ~~~
> > \d{2}-\d{2}-\d{2,4}$
> > ~~~
> > Note this will also find strings such as `31-01-198` at the end of a line, so you may wish to check your data and revise the expression to exclude false positives. Depending on your data, you may choose to add word bounding at the start of the expression.
> {: .solution}
{: .challenge}

> ## Matching publication formats
> How would you match publication formats such as `British Library : London, 2015` and `Manchester University Press: Manchester, 1999`?
>
> > ## Solution
> > ~~~
> > .* ?: .*, \d{4}
> > ~~~
> > Without word boundaries you will find that this matches any text you put before `British` or `Manchester`. Nevertheless, the regular expression does a good job on the first look up and may be need to be refined on a second, depending on your data.
> {: .solution}
{: .challenge}

