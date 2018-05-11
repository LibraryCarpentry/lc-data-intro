---
title: "Foundations"
teaching: 45
exercises: 0
questions:
- What best practices and generic skills can be used to successfully use and create library related programs?
objectives:
- Identify best practices in using software and data
- Identify best practices in saving files
- Identify best practices in naming files
keypoints:
- Data structures should be consistent and predictable
- Consider using semantic elements or data identifiers to data directories
- Fit and adapt your data structure to your work
- Apply naming conventions to directories and file names to identify them, to create associations between data elements, and to assist  
  with the long term readability and comprehension of your data structures
---

## Foundations

Before we crack on with using the computational tools at our disposal, let's spend some time building a foundation that will help frame what you'll encounter in Library Carpentry. This lesson covers a few principles and behaviors that are useful to know when beginning to develop computational approaches to your work. 

### The computer is stupid

It is true: The computer is stupid. However, the computer is also useful. Given a repetitive task, an enumerative task, or a task that relies on memory, it can produce results faster, more accurately, and less grudgingly than a person might. A computer only does what you tell it to. If you get an error message, it is often not your fault! In most cases the computer has failed to interpret what you mean because it can only work with what it knows. 

### Why take an automated or computational approach?

Otherwise known as the 'why not do it manually?' question. There are plenty of times when manual work is the easiest, fastest and most efficient approach. Here are two conditions that should make you consider using automation: 
 - You know how to automate the task
 - You think this is a task you will do over and over again

Main lessons:

- **Borrow, borrow, and borrow again**. This is a mainstay of programming and a practice common to all skill levels, from professional programmers to people like us hacking around in libraries;
- **The correct language to learn is the one that works in your local context**. There truly isn't a best language, just languages with different strengths and weaknesses, all of which incorporate the same fundamental principles;
- **Consider the role of programming in professional development**. Computational skills improve your efficiency and effectivness. Stay alert to skills you want to learn, and be aware of what skills you can make sure your staff learn, as well. 
- **Knowing (even a little) code helps you evaluate projects that use code**. Programming can seem alien. Knowing some code makes you better at judging the quality of software development or planning activities that include software development.
- **Automate to make the time to do something else!** Taking the time to gather together even the most simple programming skills can save time to do more interesting stuff! (even if often that more interesting stuff is learning more programming skills ...)

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">Just added two annotations to <a href="https://twitter.com/nthelitz">@nthelitz</a> graphic about the geek/non-geek <a href="http://t.co/KpsRYW8zD2">pic.twitter.com/KpsRYW8zD2</a></p>&mdash; Andy Kirk (@visualisingdata) <a href="https://twitter.com/visualisingdata/status/621957383464599552">July 17, 2015</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

Why Automate?: see [Geeks and repetitive tasks image](https://pbs.twimg.com/media/CKGi8bpW8AQPzOr.png).

### Keyboard shortcuts are your friend

Though we will get more computational over the course of the programme, we can start our adventure into programming - as many of you will have already - with very simple things like keyboard shortcuts. We all have our favourites, that are labour saving but also allow us to use this stupid machine in the best possible way. {**Trainer note**: ask other helpers what their favourites are}. You can do all the lessons in Library Carpentry without keyboard shortcuts, but note that they'll likely come up a lot.

Action | Windows | Mac | + keystroke
--- | --- | --- | --- |
Save | Ctrl | Cmd | + s
Copy | Ctrl | Cmd | + c
Cut | Ctrl | Cmd | + x
Paste | Ctrl | Cmd | + v
Switch Applications | Ctrl | Cmd | Tab | 

### Plain text formats are your friend

Why? Because computers can process them!

If you want computers to be able to process your stuff, try to get in the habit where possible of using platform-agnostic formats such as .txt for notes and .csv (comma-separated values) or .tsv (tab-separated values) for tabular data. TSV and CSV files are both spreadsheet formats. These plain text formats are preferable to the proprietary formats (e.g., Microsoft Word)  because they can be opened by many software packages and have a strong chance of remaining viewable and editable in the future. Most standard office suites include the option to save files in .txt, .csv and .tsv formats, meaning you can continue to work with familiar software and save your files in the more perennial formats. Compared to .doc or .xls, these formats have the additional benefit of containing only machine-readable elements. 

When working with files for automation or computational purposes, it is more important to focus on meaningful transmission of data as opposed to fancy formatting. Whilst using bold, italics, and colouring to signify headings or to make a visual connection between data elements is common practice, these display-orientated annotations are not (easily) machine-readable and hence can neither be queried and searched nor are appropriate for large quantities of information. One rule of thumb is if you can't find it by CTRL+F/cmd-F it isn't machine readable. Preferable are simple notation schemes such as using a double-asterisk or three hashes to represent a data feature: for example, we could use three question marks to indicate something that needs follow up, chosen because `???` can easily be found with a CTRL+F/cmd-F search.

`???` is also a good choice because it doesn't clash with existing schemes or systems of notation. Though it is likely that notation schemes will emerge from existing individual practice, existing schemes are available to represent formatting such as headers, line breaks, and so on. One such scheme is Markdown, a lightweight markup language. Markdown files, named as .md, are machine readable, human readable, and used in many contexts - for example, GitHub renders text via Markdown. An excellent [Markdown cheat sheet is available on GitHub](https://github.com/adam-p/markdown-here) for those who wish to follow – or adapt – this existing schema. Notepad++ http://notepad-plus-plus.org/ is recommended for Windows users as a tool to write Markdown text in, though it is by no means essential for working with .md files. Mac or Unix users may find Komodo Edit, Text Wrangler, Kate, or Atom helpful. Combined with [pandoc](http://pandoc.org/), a Markdown file can be exported to PDF, HTML, a formatted Word document, LaTeX or other formats, so it is a great way to create machine-readable, easily searchable documents that can be repurposed in many ways. It is a universal document converter.

### Naming files sensible things is good for you and for your computers

Working with data is made easier by structuring your stuff in a consistent and predictable manner.

Why?

Without structured information, our lives would be much poorer. As library and archive people we know this. But let's linger on this a little longer because for working with data it is especially important.

Examining URLs is a good way of thinking about why structuring research data in a consistent and predictable manner might be useful in your work. Good URLs represent with clarity the content of the page they identify, either by containing semantic elements or by using a single data element found across a set or majority of pages.

A typical example of the former are the URLs used by news websites or blogging services. WordPress URLs follow the format:

-   `ROOT/YYYY/MM/DD/words-of-title-separated-by-hyphens`
-   <http://cradledincaricature.com/2015/07/24/code-control-and-making-the-argument-in-the-humanities/>

A similar style is used by news agencies such as a *The Guardian* newspaper:

-   `ROOT/SUB_ROOT/YYYY/MMM/DD/words-describing-content-separated-by-hyphens`
-   <http://www.theguardian.com/uk-news/2014/feb/20/rebekah-brooks-rupert-murdoch-phone-hacking-trial>

In data repositories, URLs structured by a single data element are often used. The NLA's TROVE structures its online archive using the format:

-   `ROOT/record-type/REF`
-   <http://trove.nla.gov.au/work/6315568>

And the Old Bailey Online uses the format:

-   `ROOT/browse.jsp?ref=REF`
-   <http://www.oldbaileyonline.org/browse.jsp?ref=OA16780417>

What we learn from these examples is that a combination of semantic description and data elements make for consistent and predictable data structures that are readable both by humans and machines. Transferring this kind of pattern to your own files makes it easier to browse, to search, and to query using both the standard tools provided by operating systems and by the more advanced tools Library Carpentry will cover.

In practice, the structure of a good archive might look something like this:

- A base or root directory, perhaps called 'work'.
- A series of sub-directories such as 'events', 'data', ' projects' et cetera
- Within these directories are series of directories for each event, dataset or project. Introducing a naming convention here that includes a date element keeps the information organised without the need for subdirectories by, say, year or month.

All this should help you remember something you were working on when you come back to it later (call it real world preservation).

The crucial bit for our purposes, however, is the file naming convention you choose. The name of a file is important to ensuring it and its contents are easy to identify. 'Data.xslx' doesn't fulfil this purpose. A title that describes the data does. And adding dating convention to the file name, associating derived data with base data through file names, and using directory structures to aid comprehension strengthens those connections.

## For further reading

Andromeda Yelton, a US-based librarian, closely involved in the Code4Lib movement, put together an excellent American Library Association Library Technology Report called ["Coding for Librarians: Learning by Example."](https://thatandromeda.github.io/ltr/). In it, Yelton describes scenarios in which library professionals developed and shared code that made a difference to their work, to the work of their colleagues, and to the work of their library.
