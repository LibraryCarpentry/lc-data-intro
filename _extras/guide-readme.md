# Converting guide-pandoc.md to html with Pandoc

To convert guide-pandoc.md to html with Pandoc, first install [Pandoc]http://pandoc.org/ then in your terminal type `pandoc -s --mathml -i -t slidy guide-pandoc.md -f markdown -o guide-pandoc.html`.