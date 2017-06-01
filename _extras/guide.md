---
layout: page
title: "Instructor Notes"
permalink: /guide/
---

____
# Making a handout

Librarians like handouts. To make a handout for the [Regular Expressions episode](http://data-lessons.github.io/library-data-intro/04-regular-expressions/) do the following:

- download the reference.md page for this lesson from https://raw.githubusercontent.com/data-lessons/library-data-intro/gh-pages/reference.md (right click, save page as). 
- open the reference.md in a text editor and remove the header (the first five lines). Note for Windows users: if '.txt' has been added to the filename, resave without the '.txt'. 
- you now have a markdown file ready to convert to .docx or .pdf for printing. Now either:
  - *either* head to a webservice like [Dillinger](http://dillinger.io/), paste your markdown in the left hand columns, and use the 'Export As' dropdown to create a pdf document.
  - *or* download and install [pandoc], open the shell, and from the directory the markdown file is in run `pandoc reference.md -f markdown -t docx -s -o reference.md`

____
# Potential Slides for Instructor

If you want, use the below as a basis for slides

## Where go to for help

*There are many places!*

### Stickers

### Helpers

### Sticky notes

### github.com/???

## Jargon Busting

### Teams of 5 or 6

### Write terms you want busting on stickies

### Cluster (retaining duplicates)

### Discuss and explain

### Note resolved terms

### Note unresolved terms

### Report back

## Foundations

### The Computer is Stupid

### Why automate

### Keyboard shortcuts are your friend

### Plain text formats are your friend

### Structuring files and folders

## Foundations

### The Computer is Stupid

#### ERROR

## Foundations

### Why automate?

#### Borrow, borrow, borrow

#### There is no correct language

#### Professional development

#### Knowing some code \~ evaluating software

#### Making time to do fun stuff!

#### Andromeda Yelton, "Coding for Librarians: Learning by Example", *Library Technology Reports* 51:3 (April 2015), [doi: 10.5860/ltr.51n3](http://dx.doi.org/10.5860/ltr.51n3)

## Foundations

### Why automate?

Credit: [Andy Kirk](https://twitter.com/visualisingdata/statuses/621957383464599552?tw_i=621957383464599552&tw_e=media&tw_p=archive)

## Foundations

### Keyboard shortcuts are your friend

### Efficiency and control

## Foundations

### Plain text formats are your friend

#### Computers process them better

#### Platform agnostic

#### Display orientated files aren't your friend

#### Markdown

## Foundations

### Structuring files and folders

#### Consistent and predictable data structure

#### Semantic-data hybrid directory names

#### Your own system is fine

#### Links files and directories with names

## You are the most likely person to forget what you once did!

## Regular Expressions

### Match on types of character

### Match patterns

### Capture the parts that match your pattern

## Regular Expressions

### `organi[sz]e`

#### organise (match)

#### organize (match)

#### reorganise (match part so will also find)

#### reorganize (match part so will also find)

## Regular Expressions

### `[ABC]` matches A or B or C.

### `[A-Z]` matches any upper case letter.

### `[A-Za-z0-9]` matches any upper or lower case letter or any digit.

## Regular Expressions

### `.` matches any character at all.

### `\d` matches any single digit.

### `\w` matches any part of word character.

### `\s` matches any space, tab, or newline.

### `\b` matches a word boundary.

### `^` asserts start of the line.

### `$` asserts end of the line

## Regular Expressions

### `^\[Oo\]rgani.e\b`

## Regular Expressions

### `*` matches proceeding character any number of times including zero.

### `+` matches proceeding character any number of times excluding zero.

### `?` matches the proceeding character one or zero times.

### `{VALUE,VALUE}` matches proceeding character a defined number of times.

### `|` simply means or.

## Regular Expressions

### `^[Oo]rgani.e\w\*`

## Regular Expressions

### `[Oo]rgani.e\w+$`

## Regular Expressions

### `^[Oo]rgani.e\w?\b`

## Regular Expressions

### `^[Oo]rgani.e\w?$`

## Regular Expressions

### `\b[Oo]rgani.e\w{2}\b`

## Regular Expressions

### `\b[Oo]rgani.e\b|\b[Oo]rgani.e\w{1}\b`
