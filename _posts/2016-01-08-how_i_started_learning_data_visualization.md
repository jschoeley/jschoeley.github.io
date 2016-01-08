---
title  : How I Started Learning Data Visualization
author : Jonas Schöley
date   : 2016-01-08
tags   : visualization, datavis, R, ggplot
layout : post
excerpt_separator: "\n\n\n"
---

To learn the craft of data visualization one has to know where to start. The following list is comprised of items which helped *me* in gaining *some* skills, namely:

* Advanced knowledge of the visualization library `ggplot2`,
* best practices on visualizing data, and
* an overview of data visualization as a scientific field.



However, while I visualize data daily as part of my scientific work I am still in the early years of my training as a vis-practitioner. The list mirrors my personal journey of getting accustomed with the field and practice of visualizing data so far...

Learning ggplot2
----------------

Learning datavis by practising it is a good idea. There are tons of tools out there which help you build visualizations. If you are comfortable programming `ggplot2` is a good framework to learn first because it is widely used, flexible, follows a coherent logic of visualization and is integrated into the powerful `R` language for statistical computing. Note however, that it is mainly used to produce static graphs for print.

* [**`ggplot` Solutions for Some Common Visualization Tasks**](http://www.cookbook-r.com/Graphs/): This is based on the [*R Graphics Cookbook* by Winston Chang](http://shop.oreilly.com/product/0636920023135.do) and gets you started quickly with `ggplot`.
* [**Elegant Graphics for Data Analysis**](https://www.springer.com/us/book/9780387981406): The book by the author of `ggplot` himself and despite being quite outdated it is still a good place to learn the general idea as well as the deeper functionalities of the library. An updated version is about to get published (as of January 2016). If you have patience and some skills in `LaTeX` and `R` you can compile the new version of the book yourself. All the source files are publicly available [here](https://github.com/hadley/ggplot2-book).
* [**The Official and Illustrated `ggplot2` Documentation**](http://docs.ggplot2.org/current/): This is the technical documentation of all the functions in the `ggplot2` package. It is up to date and contains many illustrated examples on how to use each function.
* [**Tidy Data**](http://www.jstatsoft.org/v59/i10/paper): A lot of confusion about `ggplot` stems from the data being in an unsuitable format. `ggplot` works with what Hadley Wickham calls *"tidy data"*. Look at the [data wrangling cheat sheet](https://www.rstudio.com/wp-content/uploads/2015/02/data-wrangling-cheatsheet.pdf) to find out how to get your data into tidy format using `R`.
* [`ggplot2` Cheat-Sheet](https://www.rstudio.com/wp-content/uploads/2015/03/ggplot2-cheatsheet.pdf): A handy reference sheet, not only compressing most of the `ggplot` functionality into 2 pages, but also outlining its underlying logic.
* [The EDSD 2015 `ggplot` Seminar](https://github.com/jschoeley/2015-edsd-ggplot): A  five day seminar I gave last year. The [lecture notes](https://github.com/jschoeley/2015-edsd-ggplot/tree/master/lesson) contain many examples on how to work with `ggplot`.
* [The Grammar of Graphics](https://www.springer.com/us/book/9780387245447): `ggplot` is modelled after the framework for describing visualizations introduced in this book. If you are eager to learn where the underlying logic of `ggplot` comes from, look here.

Learning Shiny
--------------

If you already know `R` and want to create interactive visualizations hosted on the web `Shiny` gets you there really quick. Get inspired [here](http://www.showmeshiny.com/) and start learning [here](http://shiny.rstudio.com/tutorial/). [This](http://www.oeaw.ac.at/vid/dataexplorer/) is an example of Shiny used in a professional research environment.

Learning Information Visualization
----------------------------------

Information visualization is in the process of establishing itself as a science, meaning it generates and tests theories. These theories enable the visualization practitioner to make informed design choices.

* [**Visualization Analysis and Design**](http://www.cs.ubc.ca/~tmm/vadbook/): This textbook is both comprehensive and approachable. It introduces visualization as a task driven *design process* as opposed to a set of ready-made techniques and teaches the knowledge necessary to design effective visualizations.
* [**The Visual Display of Quantitative Information**](http://amzn.com/0961392142): In this classic the virtues of clarity, minimalism and beauty are demonstrated by example. It's a good start to get a feeling for *good design* and to learn some *best practices*. Note however that the book covers only static visualizations.
* [The Syllabus of Tamara Munzners Seminar on Information Visualization](http://www.cs.ubc.ca/~tmm/courses/547-15/): Based on the textbook *Visualization Analysis and Design* this syllabus covers a wide range of topics with detailed literature suggestions. Slides are provided and most of the literature is publicly available as well.
* [Information Visualization](http://amzn.com/0123814642 ): Everything about human perception and cognitive processing in relation to information visualization. Other books teach you best practices and techniques, this book explains why they work.
* [Datavis Milestones](http://datavis.ca/milestones/): An illustrated history of data visualization (starting 6200 BC!).

Joining the Public Discourse
----------------------------

Currently *vis* is quite hyped and a lot of people talk about it. This is to the advantage of everyone trying to learn it: To build knowledge, just immerse yourself in the discourse.

* [**The Data Stories Podcast**](http://datastori.es/): A professional quality podcast discussing trends and news in data visualization and interviewing vis-practitioners in-depth.
* [Twitter](https://twitter.com/search-home): A lot of infovis is discussed on twitter the moment it goes public. Search for example: `#datavis`, `@albertocairo`, `@visualisingdata`, `@nytgraphics`, `@mbostock`...

cc-by Jonas Schöley