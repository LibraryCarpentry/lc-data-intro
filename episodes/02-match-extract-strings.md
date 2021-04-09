---
title: "Matching & Extracting Strings"
teaching: 0
exercises: 30
questions:
- How can you use regular expressions to match and extract strings?
objectives:
- Use regular expressions to match words, email addresses, and phone numbers.
- Use regular expressions to extract substrings from strings (e.g. addresses).
keypoints:
- Regular expressions are useful for searching and cleaning data.
- Test regular expressions interactively with [regex101.com](https://regex101.com/) or [RegExr.com](http://www.regexr.com/), and visualise them with [regexper.com](https://regexper.com/).
- Test yourself with [RegexCrossword.com](https://regexcrossword.com/) or via the quiz and exercises in this lesson.
---

# Exercise Using Regex101.com

For this exercise, open a browser and go to [https://regex101.com](https://regex101.com). Regex101.com is a free regular expression debugger with real time explanation, error detection, and highlighting.

Open the [swcCoC.md file](https://github.com/LibraryCarpentry/lc-data-intro/tree/gh-pages/data/swcCoC.md), copy the text, and paste that into the test string box.

For a quick test to see if it is working, type the string `community` into the regular expression box. 

If you look in the box on the right of the screen, you see that the expression matches six instances of the string 'community' (the instances are also highlighted within the text).

> ## Taking spaces into consideration
> Type `community `. You get three matches. Why not six?
> > ## Solution
> >
> > The string 'community-led' matches the first search, but drops out of this result because the space does not match the character `-`. 
> >
> {: .solution}
{: .challenge}

> ## Taking any character into consideration
> If you want to match 'community-led' by adding other regex characters to the expression `community`, what would they be?
> > ## Solution
> >
> > For instance, `\S+\b`. This would match one or more non-space characters followed by a word boundary. 
> >
> {: .solution}
{: .challenge}

> ## Exploring effect of expressions matching different words
> Change the expression to `communi` and you get 15 full matches of several words. Why?
> > ## Solution
> >
> > Because the string 'communi' is present in all of those words, including `communi`cation and `communi`ty. Because the expression does not have a word boundary, this expression would also match in`communi`cado, were it present in this text. If you want to test this, type `incommunicado` into the text somewhere and see if it is found.
> >
> {: .solution}
{: .challenge}

> ## Taking capitalization into consideration
> Type the expression `[Cc]ommuni`. You get 16 matches. Why?
> > ## Solution
> >
> > The word Community is present in the text with a capital `C` and with a lowercase `c` 16 times.
> >
> {: .solution}
{: .challenge}

> ## Regex characters that indicate location
> Type the expression `^[Cc]ommuni`. You get no matches. Why?
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

# Exercise finding email addresses using regex101.com

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
> The string before the “@” could contain any kind of word character, special character or digit in any combination and length. How would you express this in regex? Hint: often addresses will have a dash (-) or dot (.) in them, and neither of these are included in the word character expression (\w). How do you capture this in the expression?
> > ## Solution
> > ~~~
> > [\w.-]+@
> > ~~~
> > `\w` matches any word character (including digits and underscore)
> >
> > `.` matches a literal period (when used in between square brackets, `.` does not mean "any character", it literally means ".")
> >
> > `-` matches a dash
> >
> > `[]` the brackets enclose the boolean string that 'OR' the word characters, dot, and dash.
> >
> > `+` matches any word character OR digit OR character OR `-` repeated 1 or more times
> >
> {: .solution}
{: .challenge}

> ## Finish the expression
> The string after the "@" could contain any kind of word character, special character or digit in any combination and length as well as the dash. In addition, we know that it will with some characters after a period (`.`). Most common domain names have two or three characters, but many more are now possible. Find the latest list [here](http://stats.research.icann.org/dns/tld_report/). What expression would capture this? Hint: the `.` is also a regex expression, so you'll have to use the escape `\` to express a literal period. Note: for the string after the period, we did not try to match a character, since those rarely appear in the characters after the period at the end of an email address.
> > ## Solution
> > ~~~
> >   [\w.-]+\.[\w]{2,3} OR [\w.-]+\.[\w]
> > ~~~
> > See the previous exercise for the explanation of the expression up to the `+`
> >
> > `\.` matches the literal period ('.') not the regex expression `.`
> >
> > `\w` matches any word (including digits and underscore)
> >
> > `+` matches any word character OR digit OR character OR `-` repeated 1 or more times.
> > 
> > `{2,3}` limits the number of word characters and/or digits to a two or three-character string.
> >
> > `[]` the brackets enclose the boolean string that 'OR' the digits, word characters, characters and dash.
> >
> > `+` matches any word character OR digit OR character OR `-` repeated 1 or more times
> >
> {: .solution}
{: .challenge}

# Exercise finding phone numbers, Using regex101.com

Does this Code of Conduct contain a phone number?

What to consider:
1. It may or may not have a country code, perhaps starting with a "+".
2. It will have an area code, potentially enclosed in parentheses.
3. It may have the sections all separated with a "-".

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


> ## Using regular expressions when working with files and directories
> 
> One of the reasons we stress the value of consistent and predictable directory and filenaming conventions is that working in this way enables you to use the computer to select files based on the characteristics of their file names. For example, if you have a bunch of files where the first four digits are the year and you only want to do something with files from '2017', then you can. Or if you have 'journal' somewhere in a filename when you have data about journals, you can use the computer to select just those files. Equally, using plain text formats means that you can go further and select files or elements of files based on characteristics of the data *within* those files. See Workshop Overview: [File Naming & Formatting](https://librarycarpentry.org/lc-overview/06-file-naming-formatting/index.html) for further background. 
> 
{: .callout}

# Extracting a substring in Google Sheets using regex

> ## Extracting a substring in Google Sheets using regex
> 1. Export and unzip the [2017 Public Library Survey](https://github.com/LibraryCarpentry/lc-data-intro/blob/gh-pages/files/PLS_FY17.zip) (originally from the IMLS data site) as a CSV file.
> 2. Upload the CSV file to Google Sheets and open as a Google Sheet if it does not do this by default.
> 3. Look in the `ADDRESS` column and notice that the values contain the latitude and longitude in parenthesis after the library address.
> 4. Construct a regular expression to match and extract the latitude and longitude into a new column named 'latlong'. HINT: Look up the function `REGEXEXTRACT` in Google Sheets. That function expects the first argument to be a string (a cell in `ADDRESS` column) and a quoted regular expression in the second.
>
>> ## Solution
> > This is one way to solve this challenge. You might have found others. Inside the cell you can use the below to extract the latitude and longitude into a single cell. You can then copy the formula down to the end of the column.
>>~~~
> > =REGEXEXTRACT(G2,"-?\d+\.\d+, -?\d+\.\d+")
> >~~~
> >{: .source}
> > Latitude and longitude are in decimal degree format and can be positive or negative, so we start with an optional dash for negative values then use `\d+` for a one or more digit match followed by a period `\.`. Note we had to escape the period using `\`. After the period we look for one or more digits  `\d+` again followed by a literal comma `,`. We then have a literal space match followed by an optional dash `-` (there are few `0.0` latitude/longitudes that are probably errors, but we'd want to retain so we can deal with them). We then repeat our `\d+\.\d+` we used for the latitude match.
> {: .solution}
{: .challenge}
