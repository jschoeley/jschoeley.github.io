---
title  : Bubble-grid versus choropleth maps
author : Jonas Schöley
date   : 2018-07-03
tags   : maps vis R
layout : post
---

![](/assets/2018-07-03-bubble-grid_vs_choropleth/compare.png)

*Bubble-grid map versus choropleth map of population change in Europe 2012 to 2017. Data: Eurostat ([demo_r_pjanaggr3](http://appsso.eurostat.ec.europa.eu/nui/show.do?dataset=demo_r_pjanaggr3&lang=en))*

One of the things that strike me when reading Jacques Bertins [Semiology of Graphics](https://www.amazon.com/Semiology-Graphics-Diagrams-Networks-Maps/dp/1589482611) are the demonstrations of how different the same data can look when mapped in different styles. This connects directly to the realization by [Cleveland](https://www.jstor.org/stable/2981473) and others that not all visual channels are equally fit for the same task.

Bertins work continues to inspire me to try out alternative visual mappings. The bubble-grid idea is such an experiment in perception. While color as used in choropleth maps is a great way to show spacial patterns, its hard to get a feeling for the relative magnitudes of the depicted quantities from color alone. Area however is a more effective magnitude encoding. So why not show magnitudes on a map via the size of a symbol? However, if we draw a single symbol for each statistical region we will have dense clusters of symbols wherever regions are small, and sparse symbols wherever they are large -- visually this will confound region area with whatever attribute we wish to visualize. This problem is solved by spatially interpolating the attribute of interest over a regular grid and drawing a scaled bubble at the centroid of each grid cell.

Is the bubble-grid map a good alternative to the choropleth map? I believe that magnitude differences are clearer with the bubble-map in this particular example. But I'm not sure how well it generalizes. Keep on experimenting!

<script src="https://gist.github.com/jschoeley/876aef3b9162516de451b2e8befc13f2.js"></script>

cc-by Jonas Schöley
