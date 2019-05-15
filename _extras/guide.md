---
layout: page
title: "Instructor Notes"
permalink: /guide/
---

____
# Tips and Tricks, Common Problems, Items of Note

____
## Making a handout

To make a handout for this lesson, adapt/print from [https://librarycarpentry.org/lc-data-intro/reference](https://librarycarpentry.org/lc-data-intro/reference).

____
## Jargon Busting

Requirements for this task are:

- boards/pads
- pens

The purpose of this task is threefold. First, it is an icebreaker. Second, it helps learners find their confidence level and situate their experience and knowledge in the context of fellow learners. Third, it helps manage expectation as the instructor can explain to learners which terms, phrases, or ideas will be covered by this Library Carpentry workshop, which terms, phrases, or ideas are covered by other Library Carpentry lessons, and which terms, phrases, or ideas are covered elsewhere.

It is important to note that no one is an expert in everything and the instructor will need help with describing certain terms. The instructor is encouraged to invite workshop attendees, instructors, and helpers to join in describing terms, phrases, or ideas as well.

When collating feedback on the main board/pad (if none are available, consider using the workshop Etherpad), one strategy is to organise the board from sad (on the left) to happy (on the right), then to locate the terms, phrases, or ideas offered by learners on that spectrum. This performs three functions. First, it opens space to discuss which terms, phrases, or ideas people find or perceive to be easy to understand and what they find or perceive to be hard to understand. Second, it helps identify expertise in the room that learners may turn to for questions during breaks. Third, the instructor can return to the board/pad at the end of the workshop to judge whether learners are more or less confident with some of the terms, phrases, or ideas identified at the outset.

____
## Foundations

Learning to program is like learning another language.
You have to speak the computer's language.

Use inclusive language when programming to create a welcoming environment. 

Workshop attendees usually want to jump in right away and start learning a tool or approach. Intro to Data provides step by step foundational training to prepare learners for further Library Carpentry lessons. 

Some tips as you learn...
- Borrow, borrow, borrow (Stack Overflow)
- Use what is used in your local context (sometimes it is easier to ask your colleague in the next office for help)
- Ask, can it help you in your professional development? 
- Knowing a little bit about programing helps you talk to IT/researchers 
- Can it free up your time? Something you do repeatedly?

Keyboard shortcuts are your friend. Sometimes using a shortcut vs programming is the best approach. Shortcuts allow you to save time in some cases. Using the Etherpad, the instructor can ask workshop attendees to list their favorite shortcuts and/or shortcuts that are not widely known.

Most of Library, Data, and Software Carpentry lessons are based on open source tools with the exception of MATLAB. This is also the case with open formats vs proprietary formats. The instructor can use this as an opportunity to quiz the workshop attendees what is an open format/source tool vs proprietary and to list examples (e.g. PDF, DOC).

Markdown or .md files are example of machine readable files that are also human readable. Markdown is a markup language that allows you to format content using notation which can be read by certain tools and services such as GitHub. HackMD [https://hackmd.io/](https://hackmd.io/) is a helpful tool to explore Markdown together with a cheatsheet [https://commonmark.org/help/](https://commonmark.org/help/). In some cases, there are online tools that help you generate Markdown like this CSV to Markdown table generator [https://donatstudios.com/CsvToMarkdownTable](https://donatstudios.com/CsvToMarkdownTable). Pandoc [https://pandoc.org/](https://pandoc.org/) is a helpful tool for converting Markdown to other formats like PDF.
    
When you start a project, how do you organize your files?
Recommendations:
- Folder structure (data, code, results)
- File formats (CamelCase, Snake_Case, Kebab-Case)
- Date formats (ISO 8601 YYYY-MM-DD)
Further reading:
[https://datadryad.org/pages/reusabilityBestPractices](https://datadryad.org/pages/reusabilityBestPractices)

_____
## Regular Expressions

You may find it useful to use [slides](https://github.com/LibraryCarpentry/lc-data-intro/blob/gh-pages/files/regexslides.pdf) to work through episode four. Before starting the exercise, encourage learners to work with pen and paper, explain that with regex there are sometimes multiple answers to the same question (that is, some regex is perfect and some does the job given the likely data structures we use) and point them towards places to test their regex. Regxr is a regular expression tester with syntax highlighting, PHP / PCRE & JS Support, contextual help, cheat sheet, reference, and searchable community patterns: [https://regexr.com/](https://regexr.com/). Other regular expression tools include regex101 [https://regex101.com/](https://regex101.com/), rexegper [http://regexper.com/](http://regexper.com/), myregexp [http://myregexp.com/]([http://myregexp.com/]), or whichever service you prefer. Also point them towards the quiz (episode five and six or this [quiz](https://github.com/LibraryCarpentry/lc-data-intro/blob/gh-pages/files/quiz.docx?raw=true) and [answers](https://github.com/LibraryCarpentry/lc-data-intro/blob/gh-pages/files/quizAnswers.docx?raw=true)) as something they may move onto if they they finish the exercises early or look at after the workshop.
  
____
# General notes on Introduction to Data

Two sets of sticky notes (ideally one red and one green) are required to run a Library Carpentry workshop. Learners should be encouraged to put a red sticky note on the back of their laptop (raised like a flag) if they need help, and to put the green sticky note on the back of their laptop if they don't need help.

At each break, ask learners to provide feedback on their learning experience since the last break. They should do this by writing one thing that didn't go well on their red sticky note and and one thing that did go well on their green sticky note. Collect these sticky notes, keep them organised so you know which section of the lesson their pertain to, and collate them after the workshop. Matters arising should be raised as Github issues for the relevant lesson.

Note that whilst red and green sticky notes are a common combination in The Carpentries (with the green sticky note used to indicate that the attendee is fine and for positive feedback), this is the worst colour combination for colourblind/deficient instructors and helpers scanning a room to see who needs help (1 in 12 men are colour blind/deficient, 1 in 200 women). An alternative to using two colours is to use a white sticky note to indicate an attendee needs help (like a white flag) and a sticky note of any other colour to indicate that they don't need help. For more information on designing for colourblindness/defiency see [Oliver Daddow, 'It’s time designing for the colour blind became a more integrated component of academic and media training', LSE Impact Blog (2017)](http://blogs.lse.ac.uk/impactofsocialsciences/2017/07/31/its-time-designing-for-the-colour-blind-became-a-more-integrated-component-of-academic-and-media-training/).
