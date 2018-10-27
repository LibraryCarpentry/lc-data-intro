---
title: "Regular Expressions"
teaching: 20
exercises: 25
questions:
- How can you imagine using regular expressions in your work?
objectives:
- Use regular expressions in searches
keypoints:
- Regular expressions are a language for pattern matching
- "Check your regex with: regex101 [https://regex101.com/](https://regex101.com/), rexegper [http://regexper.com/](http://regexper.com/), or myregexp [http://myregexp.com/]([http://myregexp.com/])."
- "Test yourself with: Regex Crossword [https://regexcrossword.com/](https://regexcrossword.com/) or our The Multiple Choice Quiz [https://librarycarpentry.github.io/lc-data-intro/05-quiz/](https://librarycarpentry.github.io/lc-data-intro/05-quiz/)."
---

## Regular expressions

Regular expressions are a concept and an implementation used in many different programming environments for sophisticated pattern matching. They are an incredibly powerful tool that can amplify your capacity to find, manage, and transform data and files. 

A regular expression, often abbreviated to *regex*, is a method of using a sequence of characters to define a search to match strings, i.e. "find and replace"-like operations. In computation, a 'string' is a contiguous sequence of symbols or values. For example, a word, a date, a set of numbers (e.g., a phone number), or an alphanumeric value (e.g., an identifier). In library searches, we are most familiar with a small part of regular expressions known as the "wild card character," but there are many more features to the complete regular expressions syntax. Regular expressions will let you:

- Match on types of characters (e.g. 'upper case letters', 'digits', 'spaces', etc.)
- Match patterns that repeat any number of times
- Capture the parts of the original string that match your pattern

Regular expressions rely on the use of literal characters and metacharacters. A metacharacter is any ASCII character that has a special meaning. By using metacharacters and possibly literal characters, you can construct a regex for finding strings or files that match a pattern rather than a specific string. For example, say your organization wants to change the way they display telephone numbers on their website by removing the parentheses around the area code. Rather than search for each specific phone number (that could take forever and be prone to error) or searching for every open parenthesis character (could also take forever and return many false-positives), you could search for the pattern of a phone number. 

Since regular expressions defines some ASCII characters as "metacharacters" that have more than their literal meaning, it is also important to be able to "escape" these metacharacters to use them for their normal, literal meaning. For example, the period (\.) means "match any character", but if you want to match a period (\.) then you will need to use a "\" in front of it to signal to the regular expression processor that you want to use the period as a plain old period and not a metacharacter. That notation is called "escaping" the special character. The concept of "escaping" special characters is shared across a variety of computational settings, including markdown and HTML.  

A very simple use of a regular expression would be to locate the same word spelled two different ways. For example the regular expression `organi[sz]e` matches both "organise" and "organize". But it would also match `reorganise`, `reorganize`, `organises`, `organizes`, `organised`, `organized`, etc.

### Learning common regex metacharacters
Square brackets can be used to define a list or range of characters to be found. So:

- `[ABC]` matches A or B or C
- `[A-Z]` matches any upper case letter
- `[A-Za-z]` matches any upper or lower case letter (note: this is case-sensitive)
- `[A-Za-z0-9]` matches any upper or lower case letter or any digit (note: this is case-sensitive)

Then there are:

- `.` matches any character
- `\d` matches any single digit
- `\w` matches any part of word character (equivalent to `[A-Za-z0-9]`)
- `\s` matches any space, tab, or newline
- `\` used to escape the following character when that character is a special character. So, for example, a regular expression that found `.com` would be `\.com` because `.` is a special character that matches any character.
- `^` asserts the position at the start of the line. So what you put after the caret will only match if they are the first characters of a line. The caret is also known as a circumflex.
- `$` asserts the position at the end of the line. So what you put before it will only match if they are the last characters of a line.
- `\b` adds a word boundary. Putting this either side of a word stops the regular expression matching longer variants of words. So:
	- the regular expression `foobar` will match `foobar` and find `666foobar`, `foobar777`, `8thfoobar8th` et cetera
	- the regular expression `\bfoobar` will match `foobar` and find `foobar777`
	- the regular expression `foobar\b` will match `foobar` and find `666foobar`
	- the regular expression `\bfoobar\b` will find `foobar` but not `666foobar` or `foobar777`

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
> {: .solution}
{: .challenge}

Other useful special characters are:

- `*` matches the preceding element zero or more times. For example, ab*c matches "ac", "abc", "abbbc", etc.
- `+` matches the preceding element one or more times. For example, ab+c matches "abc", "abbbc" but not "ac".
- `?` matches when the preceding character appears zero or one time.
- `{VALUE}` matches the preceding character the number of times defined by VALUE; ranges, say, 1-6, can be specified with the syntax `{VALUE,VALUE}`, e.g. `\d{1,9}` will match any number between one and nine digits in length.
- `|` means or.
- `/i` renders an expression case-insensitive (equivalent to `[A-Za-z]`)

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

This logic is useful when you have lots of files in a directory, when those files have logical file names, and when you want to isolate a selection of files. It can a be used for looking at cells in spreadsheets for certain values, or for extracting some data from a column of a spreadsheet to make  new columns. I could go on. The point is, it is useful in many contexts. To embed this knowledge we won't - however - be using computers. Instead we'll use pen and paper. 


### Exercise

Work in teams of 4-6 on the exercises below. When you think you have the right answer, check it against the solution. 

When you finish, split your team into two groups and write each other some tests. These should include a) strings you want the other team to write regex for and b) regular expressions you want the other team to work out what they would match. 

Then test each other on the answers. If you want to check your logic, use [regex101](https://regex101.com/), [myregexp](http://myregexp.com/), or [regex pal](http://www.regexpal.com/) [regexper.com](http://regexper.com/): the first three help you see what text your regular expression will match, the latter visualises the workflow of a regular expression.

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
> > This will also find words where there are characters either side of the solutions above, such as `Francer`, `foobarFrench`, and `Franch911`.
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
> > This will also find strings at the end of a line. It will find words where there were characters before these, for example `foobarFrench`.
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
> > In real life, you *should* only come across the case insensitive variations `colour`, `color`, `Colour`, `Color`, `COLOUR`, and `COLOR` (rather than, say, `coLour`). So based on what we know, the logical regular expression is `\b[Cc]olou?r\b|\bCOLOU?R\b`. An alternative more elegant option we've not discussed is to take advantage of the `/` delimiters and add an 'ignore case' flag: so `/colou?r/i` will match all case insensitive variants of `colour` and `color`.
> {: .solution}
{: .challenge}

> ## Word boundaries
> How would you find the whole word `headrest` and or `head rest` but not `head  rest` (that is, with two spaces between `head` and `rest`?
>
> > ## Solution
> > ~~~
> > \bhead ?rest\b
> > ~~~
> > Note that although `\bhead\s?rest\b` does work, it will also match zero or one tabs or newline characters between `head` and `rest`. So again, although in most real world cases it will be fine, it isn't strictly correct.
> {: .solution}
{: .challenge}

> ## Matching non-linguistic patterns
> How would you find a string that ends with 4 letters preceded by at least one zero?
>
> > ## Solution
> > ~~~
> > 0+[A-Za-z]{4}\b
> > ~~~
> {: .solution}
{: .challenge}

> ## Matching digits
> How do you match any 4-digit string anywhere?
>
> > ## Solution
> > ~~~
> > \d{4}
> > ~~~
> > Note: this will also match 4 digit strings within longer strings of numbers and letters.
> {: .solution}
{: .challenge}

> ## Matching dates
> How would you match the date format `dd-MM-yyyy`?
>
> > ## Solution
> > ~~~
> > \b\d{2}-\d{2}-\d{4}\b
> > ~~~
> > Depending on your data, you may chose to remove the word bounding.
> {: .solution}
{: .challenge}

> ## Matching multiple date formats
> How would you match the date format `dd-MM-yyyy` or `dd-MM-yy` at the end of a line only?
>
> > ## Solution
> > ~~~
> > \d{2}-\d{2}-\d{2,4}$
> > ~~~
> > Note this will also find strings such as `31-01-198` at the end of a line, so you may wish to check your data and revise the expression to exclude false positives. Depending on your data, you may chose to add word bounding at the start of the expression.
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

### Exercise Using Regex101.com

For this exercise, open a browser and go to [https://regex101.com](https://regex101.com). 

Open the [swcCoC.md file](https://github.com/LibraryCarpentry/lc-data-intro/tree/gh-pages/data/swcCoC.md), copy it, and paste it into the test string box.

For a quick test to see if it's working, type the string `community` into the regular expression box. 

If you look in the box on the right of the screen, you see that the expression matches six instances of the string 'community' (the instances are also highlighted within the text)

> ## Taking spaces into consideration
> Type `community `. You get three matches. Why not six?
> > ## Solution
> >
> > The string 'community-led' matches the first search, but drops out of this result because the space does not match the character `-`. 
> >
> {: .solution}
{: .challenge}

> ## Taking any character into consideration
> If you want to match 'community-led' by adding another regex character to the expression `community`, what would it be?
> > ## Solution
> >
> > It would be the `.` 
> >
> {: .solution}
{: .challenge}

> ## Exploring effect of expressions matching different words
> Change the expression to `communi` you get 13 full matches of several words. Why?
> > ## Solution
> >
> > Because the string 'communi' is present in all of those words, including `communi`cation and `communi`ty. Because the expression does not have a word boundary, this expression would also match in`communi`cado, were it present in this text. If you want to test this, type `incommunicado` into the text somewhere and see if it is found.
> >
> {: .solution}
{: .challenge}

> ## Taking capitalization into consideration
> Type the expression `[Cc]ommuni`. You get 14 matches. Why?
> > ## Solution
> >
> > The word Community is present in the text with a capital `C` and with a lowercase `c` 14 times.
> >
> {: .solution}
{: .challenge}

> ## Regex characters that indicate location
> Type the expression ^[Cc]ommuni. You get no matches. Why?
> > ## Solution
> >
> > There is no matching string present at the start of a line. Look at the text and replace the string after the `^` with something that matches a word at the start of a line. Does it find a match?
> >
> {: .solution}
{: .challenge}

> ## Finding plurals
> Find all of the words starting with Comm or comm that are plural.
> > ## Solution
> > ~~~
> > [Cc]omm\w+s\b
> > ~~~
> > `[Cc]` finds capital and lowercase `c`
> >
> > `omm` is straightforward character matches
> >
> > `\w+` matches the preceding element (a word character) one or more times
> >
> > `s` is a straightforward character match
> >
> > `\b` ensures the 's' is located at the end of the word.
> >
> {: .solution}
{: .challenge}

### Exercise finding Email addresses, Using regex101.com

For this exercise, open a browser and go to [https://regex101.com](https://regex101.com). 

Open the [swcCoC.md file](https://github.com/LibraryCarpentry/lc-data-intro/tree/gh-pages/data/swcCoC.md), copy it, and paste it into the test string box.

> ## Start with what you know
> What character do you know is held in common with all email addresses?
> > ## Solution
> >
> > The '@' character.
> >
> {: .solution}
{: .challenge}

> ## Add to what you know
> The string before the "@" could contain any kind of word character, special character or digit in any combination and length. How would you express this in regex? Hint: often addresses will have a dash (`-`) in them, and the dash is not included in the word character expression (`\w`). How do you capture this in the expression?
> > ## Solution
> > ~~~
> > [\w.-]+@
> > ~~~
> > `\w` matches any word character (including digits and underscore)
> >
> > `\.` matches any character
> >
> > `-` straightforward match, since it is not captured with `\.`
> >
> > `[]` the brackets enclose the boolean string that 'OR' the digits, word characters, characters and dash.
> >
> > `+` matches any word character OR digit OR character OR `-` repeated 1 or more times
> >
> {: .solution}
{: .challenge}

> ## Finish the expression
> The string after the "@" could contain any kind of word character, special character or digit in any combination and length as well as the dash. In addition, we know that it will end with two or three characters after a period (`.`) What expression would capture this. Hint: the `.` is also a regex expression, so you'll have to use the escape `\` to express a literal period. Note: for the string after the period, I did not try to match a character, since those rarely appear in the .xx or .xxx at the end of an email address.
> > ## Solution
> > ~~~
> > [\w.-]+\.[\w]{2,3}
> > ~~~
> > See the previous exercise for the explanation of the expression up to the `+`
> >
> > `\.` matches the literal periond ('.') not the regex expression `.`
> >
> > `\w` matches any word (including digits and underscore)
> >
> > `{2,4}` limits the number of word characters and/or digits to a two or three-character string.
> >
> > `[]` the brackets enclose the boolean string that 'OR' the digits, word characters, characters and dash.
> >
> > `+` matches any word character OR digit OR character OR `-` repeated 1 or more times
> >
> {: .solution}
{: .challenge}

### Exercise finding phone numbers, Using regex101.com

Does this Code of Conduct contain a phone number?

What to consider:
1. It may or may not have a country code, perhaps starting with a "+"
2. It will have an area code, potentially enclosed in parens
3. It may have the sections all separated with a "-"

> ## Start with what you know: find strings of digits
> Start with what we know, which is the most basic format of a phone number: three digits, a dash, and four digits. How would we write a regex expression that matches this?
> > ## Solution
> > ~~~
> > \d{3}-\d{4}
> > ~~~
> > `\d` matches digits
> >
> > `{3}` matches 3 digits
> > 
> > `-` matches the character '-'
> >
> > `\d` matches any digit
> >
> > `{4}` matches 4 digits.
> > 
> >This expression should find three matches in the document.
> {: .solution}
{: .challenge}

> ## Match a string that includes an area code with a dash
> Start with what we know, which is the most basic format of a phone number: three digits, a dash, and four digits. How would we expand the expression to include an area code (three digits and a dash)?
> > ## Solution
> > ~~~
> > \d{3}-\d{3}-\d{4}
> > ~~~
> > `\d` matches digits
> >
> > `{3}` matches 3 digits
> > 
> > `-` matches the character '-'
> >
> > `\d` matches any digit
> >
> > `{4}` matches 4 digits.
> >
> >This expression should find one match in the document
> {: .solution}
{: .challenge}

> ## Match a string that includes an area code within parenthesis separated from the rest of the phone number with a space or without a space
> Start with what we know, which is the most basic format of a phone number: three digits, a dash, and four digits. How would we expand the expression to include a phone number with an area code in parenthesis, separated from the phone number, with or without a space.
> > ## Solution
> > ~~~
> >\(\d{3}\) ?\d{3}-\d{4}
> > ~~~
> > `\(` escape character with the parenthesis as straightforward character match
> >
> > `\d` matches digits
> >
> > `{3}` matches 3 digits
> > 
> > `\)` escape character with the parenthesis as a straightforward character match
> >
> > ` ?` matches zero or one spaces
> > 
> > See the previous exercise for the explanation of the rest of the expression.
> > 
> > This expression should find two matches in the document.
> {: .solution}
{: .challenge}

> ## Match a phone number containing a country code.
> Country codes are preceded by a "+" and can have up to three digits. We also have to consider that there may or may not be a space between the country code and anything appearing next.
> > ## Solution
> > ~~~
> >\+\d{1,3} ?\(\d{3}\)\s?\d{3}-\d{4}
> > ~~~
> > `\+` escape character with the plus sign as straightforward character match
> >
> > `\d` matches digits
> >
> > `{1,3}` matches 1 to 3 digits
> >
> > ` ?` matches zero or one spaces
> > 
> > See the previous exercise for the explanation of the rest of the expression.
> > 
> > This expression should find one match in the document.
> {: .solution}
{: .challenge}

One of the reasons we stress the value of consistent and predictable directory and filenaming conventions is that working in this way enables you to use the computer to select files based on the characteristics of their file names. For example, if you have a bunch of files where the first four digits are the year and you only want to do something with files from '2017', then you can. Or if you have 'journal' somewhere in a filename when you have data about journals, you can use the computer to select just those files. Equally, using plain text formats means that you can go further and select files or elements of files based on characteristics of the data *within* those files.

> ## Extracting a substring in Google Sheets using regex
> 1. Export the the [2014 Public Library Survey](https://data.imls.gov/Public-Libraries-Survey/Main-Libraries-Branches-and-Bookmobiles-FY-2014-Pu/ucdn-7aur/data) from the IMLS data site as a CSV file.
> 2. Upload to Google Sheets and open as a Google Sheet if it doesn't do this by default.
> 3. Look in the `LOCATION` column and notice that the values contain the latitude and longitude in parenthesis after the library address.
> 4. Construct a regular expression to match and extract the latitude and longitude into a new column named 'latlong'. HINT: Look up the function `REGEXEXTRACT` in Google Sheets. That function expects the first argument to be a string (a cell in `LOCATION` column) and a quoted regular expression in the second.
>
>> ## Solution
> > This is one way to solve this challenge. You might have found others. Inside the cell you can use the below to extract the Latitude and Longitude into a single cell. You can then copy the formula down to the end of the column.
>>~~~
> > =REGEXEXTRACT(G2,"\d+\.\d+, -?\d+\.\d+")
> >~~~
> >{: .source}
> > Here we are using `\d+` for a one or more digit match followed by a period `\.`. Note we had to escape the period using `\`. After the period we look for one or more digits  `\d+` again followed by a literal comma `,`. We then have a literal space match followed by an optional dash `-` (there are few `0.0` Latitude/Longitudes that are probably errors, but we'd want to retain so we can deal with them). We then repeat our `\d+\.\d+` we used for the Latitude match.
> {: .solution}
{: .challenge}
