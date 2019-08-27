---
title: A computational approach
teaching: 45
exercises: 0
questions:
- What best practices and generic skills can be used to successfully use and create library related programs?
objectives:
- Identify best practices in using software and data.
- Identify best practices in saving files.
- Identify best practices in naming files.
keypoints:
- Data structures should be consistent and predictable.
- Consider using semantic elements or data identifiers to data directories.
- Fit and adapt your data structure to your work.
- Apply naming conventions to directories and file names to identify them, to create associations between data elements, and to assist with the long term readability and comprehension of your data structures.
---

### Why take an automated or computational approach?

Otherwise known as the 'why not do it manually?' question. There are plenty of times when manual work is the easiest, fastest and most efficient approach. Here are two conditions that should make you consider using automation: 
 - You know how to automate the task.
 - You think this is a task you will do over and over again.

Main lessons:

- **Borrow, borrow, and borrow again**. This is a mainstay of programming and a practice common to all skill levels, from professional programmers to people like us hacking around in libraries;
- **The correct language to learn is the one that works in your local context**. There truly isn't a best language, just languages with different strengths and weaknesses, all of which incorporate the same fundamental principles;
- **Consider the role of programming in professional development**. Computational skills improve your efficiency and effectiveness. Stay alert to skills you want to learn, and be aware of what skills you can make sure your staff learn, as well. 
- **Knowing (even a little) code helps you evaluate projects that use code**. Programming can seem alien. Knowing some code makes you better at judging the quality of software development or planning activities that include software development.
- **Automate to make the time to do something else!** Taking the time to gather together even the most simple programming skills can save time to do more interesting stuff! (even if often that more interesting stuff is learning more programming skills ...)

**Why automate?**

![Is it worth the time](../assets/img/is_it_worth_the_time.png)

'Is it worth the time?' by Randall Munroe available at [https://xkcd.com/1205/](https://xkcd.com/1205/) under a Creative Commons Attribution-NonCommercial 2.5 License.

### Keyboard shortcuts are your friend

Though we will get more computational over the course of the programme, we can start our adventure into programming - as many of you will have already - with very simple things like keyboard shortcuts. We all have our favourites that are labour saving but also allow us to use this machine in the best possible way. You can do all the lessons in Library Carpentry without keyboard shortcuts, but note that they'll likely come up a lot.

Action | Windows | Mac | + Keystroke
--- | --- | --- | --- |
Save | <kbd>Ctrl</kbd> | <kbd>Command</kbd> | + <kbd>S</kbd>
Copy | <kbd>Ctrl</kbd> | <kbd>Command</kbd> | + <kbd>C</kbd>
Cut | <kbd>Ctrl</kbd> | <kbd>Command</kbd> | + <kbd>X</kbd>
Paste | <kbd>Ctrl</kbd> | <kbd>Command</kbd> | + <kbd>V</kbd>
Switch Applications | <kbd>Alt</kbd> | <kbd>Command</kbd> | <kbd>Tab</kbd> | 

### Plain text formats are your friend

Why? Because computers can process them!

If you want computers to be able to process your stuff, try to get in the habit where possible of using platform-agnostic formats such as `.txt` for notes and `.csv` (comma-separated values) or `.tsv` (tab-separated values) for tabular data. TSV and CSV files are both spreadsheet formats. These plain text formats are preferable to the proprietary formats (e.g., Microsoft Word)  because they can be opened by many software packages and have a strong chance of remaining viewable and editable in the future. Most standard office suites include the option to save files in `.txt`, `.csv`, and `.tsv` formats, meaning you can continue to work with familiar software and save your files in the more perennial formats. Compared to `.doc` or `.xls`, these formats have the additional benefit of containing only machine-readable elements. 

When working with files for automation or computational purposes, it is more important to focus on meaningful transmission of data as opposed to fancy formatting. Whilst using bold, italics, and colouring to signify headings or to make a visual connection between data elements is common practice, these display-orientated annotations are not (easily) machine-readable and hence can neither be queried and searched nor are appropriate for large quantities of information. One rule of thumb is if you can't find it by <kbd>Ctrl</kbd>+<kbd>F</kbd>/<kbd>Command</kbd>+<kbd>F</kbd> it isn't machine readable. Preferable are simple notation schemes such as using a double-asterisk or three hashes to represent a data feature: for example, we could use three question marks to indicate something that needs follow up, chosen because `???` can easily be found with a <kbd>Ctrl</kbd>+<kbd>F</kbd>/<kbd>Command</kbd>+<kbd>F</kbd> search.

### Use machine readable plain text notation for formatting
There are some simple notation schemes that are also plain text and machine readable, but can be used to render simple formatting. One such scheme is called Markdown, a lightweight markup language. A markup language is a metadata language that uses notation to distinguish between the content and the formatting of the content. Markdown files, which use the file extension `.md`, are machine and human readable. Markdown applications can be disparate, from simple to-do lists, to extensive manual pages. For example, GitHub renders text via Markdown.  

For those who wish to follow – or adapt – this existing schema, you can try Markdown formatting interactively by following [CommonMark's guide](https://commonmark.org/help/), or using [TailorDev's Monod editor](https://github.com/TailorDev/monod). An excellent [Markdown cheat sheet is available on GitHub](https://github.com/adam-p/markdown-here).  

### Applications for writing, reading and outputting plain text files

We've already discussed why plain text formats are needed for working with data, and it's also important to understand that you need different tools to work with these formats. Word processors like Microsoft Word, LibreOffice Writer, and Google Docs will explicitly _not_ work for this purpose -- those tools are meant to optimize how documents appear to humans, not to computers. They add many hidden characters and generally are unsuitable for working with plain text files. The category of tool you'll want to use for data is called a _text editor_. Text editors save only the text that you type -- there is no hidden formatting or metadata. What you see in a text editor is what a computer will see when it tries to process that data.       

Two free, cross-platform editors that work well for handling plain text files are [Visual Studio Code](https://code.visualstudio.com/) and [Atom](https://atom.io/). For Windows users, [Notepad++](http://notepad-plus-plus.org/) is recommended. Mac or Unix users may find [Komodo Edit](https://www.activestate.com/products/komodo-ide/downloads/edit/), [Kate](https://kate-editor.org/) or [Gedit](https://wiki.gnome.org/Apps/Gedit) useful.
Combined with [pandoc](http://pandoc.org/), a Markdown file can be exported to PDF, HTML, a formatted Word document, LaTeX or other formats, so it is a great way to create machine-readable, easily searchable documents that can be repurposed in many ways. This [Programming Historian](https://programminghistorian.org/) [tutorial](https://programminghistorian.org/en/lessons/sustainable-authorship-in-plain-text-using-pandoc-and-markdown) spells out what to do.

### Naming files sensible things is good for you and for your computers

Working with data is made easier by structuring your files in a consistent and predictable manner. Without structured information, our lives would be much poorer. As library and archive people, we know this. But let's linger on this a little longer because for working with data it is especially important.

Examining URLs is a good way of thinking about why structuring data in a consistent and predictable manner might be useful in your work. Good URLs represent with clarity the content of the page they identify, either by containing semantic elements or by using a single data element found across a set or majority of pages.

A typical example of the former are the URLs used by news websites or blogging services. WordPress URLs follow the format:

-   `ROOT/YYYY/MM/DD/words-of-title-separated-by-hyphens`
-   <https://cradledincaricature.com/2015/07/24/code-control-and-making-the-argument-in-the-humanities/>

A similar style is used by news agencies such as *The Guardian* newspaper:

-   `ROOT/SUB_ROOT/YYYY/MMM/DD/words-describing-content-separated-by-hyphens`
-   <https://www.theguardian.com/uk-news/2014/feb/20/rebekah-brooks-rupert-murdoch-phone-hacking-trial>

In data repositories, URLs structured by a single data element are often used. The National Library of Australia's TROVE uses this format:

-   `ROOT/record-type/REF`
-   <https://trove.nla.gov.au/work/6315568>

The Old Bailey Online uses the format:

-   `ROOT/browse.jsp?ref=REF`
-   <https://www.oldbaileyonline.org/browse.jsp?ref=OA16780417>

What we learn from these examples is that a combination of semantic description and data elements make for consistent and predictable data structures that are readable both by humans and machines. Transferring this kind of pattern to your own files makes it easier to browse, to search, and to query using both the standard tools provided by operating systems and by the more advanced tools Library Carpentry will cover.

In practice, the structure of a good archive might look something like this:

- A base or root directory, perhaps called 'work'.
- A series of sub-directories such as 'events', 'data', 'projects' etc.
- Within these directories are series of directories for each event, dataset or project. Introducing a naming convention here that includes a date element keeps the information organised without the need for subdirectories by, say, year or month.

All this should help you remember something you were working on when you come back to it later (call it real world preservation).

The crucial bit for our purposes, however, is the file naming convention you choose. The name of a file is important to ensuring it and its contents are easy to identify. `Data.xslx` doesn't fulfil this purpose. A title that describes the data does. And adding dating convention to the file name, associating derived data with base data through file names, and using directory structures to aid comprehension strengthens those connections.

## For further reading

Andromeda Yelton, a US-based librarian closely involved in the [Code4Lib] (https://code4lib.org/about/) movement, put together an excellent American Library Association Library Technology Report called ["Coding for Librarians: Learning by Example"](https://thatandromeda.github.io/ltr/). In it, Yelton describes scenarios in which library professionals developed and shared code that made a difference to their work, to the work of their colleagues, and to the work of their library.


