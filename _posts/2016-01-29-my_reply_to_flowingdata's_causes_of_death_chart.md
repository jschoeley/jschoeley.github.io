---
title  : My Reply to flowingdata's Causes of Death Chart
author : Jonas Schöley
date   : 2016-01-29
tags   : mortality vis R
layout : post
---

![My Reply to flowingdata's Causes of Death Chart](/assets/2016-01-29-my_reply_to_flowingdata's_causes_of_death_chart/codus2014_150dpi.png)
*My Reply to flowingdata's Causes of Death Chart*

Complementing [flowingdata's graph on causes of death](http://flowingdata.com/2016/01/05/causes-of-death/) I visualize US deaths by cause taking age-specific mortality into account.

*Causes of Death by Overall Incidence*: Circulatory diseases are the most common cause of death in the US 2014, accounting for nearly a third of all observed deaths in females and males. Cancer is second with 22.6 % of all female deaths and 24.4 % of all male deaths. Suicides and accidents are more common with males while females die more often from mental diseases and diseases of the nervous system.

*The Number of Deaths by Cause and Age*: Death comes with age. 9 out of 10 deaths in the US 2014 happen after age 50, half of all deaths in ages 77 and older. The age with the highest count of deaths is 89 for females and 84 for males. Deaths in infancy are rare but still visible as an outlier. They are mostly due to perinatal and congenital conditions. Deaths during childhood are extremely rate. Deaths in adolescence and early adulthood are rare and predominantly the result of external causes, with accidents being numerically more important than suicides. We see substantially more adolescent and early deaths in males than in females. At any age male suicides are observed more often than female suicides. Deaths by accident are counted much more often for adolescent and young adult males than for young females. Around age 60 mortality is driven by cancer first and circulatory diseases second. Circulatory diseases become the leading cause of death during ages 70--80 while cancer gradually declines in importance. Mental diseases and diseases of the nervous system contribute heavily to mortality at ages 80+.

*The Age Pattern of Deaths by Cause*: While we learned that death in an adolescent age is most likely due to accident, accidents are just as often observed in old age. Most suicides are observed around ages 50 to 60. Only few suicides happen at ages 80+. Perinatal & congenital conditions result almost exclusively in infant deaths. Circulatory diseases, cancer, respiratory diseases, diseases of the nervous system, mental diseases, infections & parasites are causes of death that are more likely to occur during advanced ages.

Motivation
----------

Earlier this year [flowingdata](http://flowingdata.com/) published an interactive visualization showing the distribution of different [causes of death](http://flowingdata.com/2016/01/05/causes-of-death/) along the age axis.

![Causes of Death by Nathan Yau posted on flowingdata.com](/assets/2016-01-29-my_reply_to_flowingdata's_causes_of_death_chart/flowingdata.png)
*Causes of Death by Nathan Yau posted on flowingdata.com*

Nathan Yau plotted shares *conditioned on age*: For those who died at age x, what share of them died of a given cause? This is a reasonable choice and makes for an informative chart **but** one has to keep in mind that more people die in old age than in young ages. This information is not given by the chart and can lead to misinterpretations. An example: External causes (Suicide, Accident) are visually *very* prominent in the flowingdata plot whereas they only add up to 5% of *all* Female deaths registered in the US 2005 to 2014. Likewise cancer seems to be just as important as circulatory diseases when it comes to fatal outcomes whereas actually the latter is the leading cause of death among females and males.

Some of the Twitter audience wished for a version of that chart using absolute numbers. This is where my chart comes in, *complementing* Nathan Yau's visualization. I plot US causes of death taking into account *absolute numbers of deaths* and therefore *varying mortality by age*.

Technical Background
--------------------

The *Causes of Death in the US 2014* chart has been created using open data and open software.

- Data: [National Center for Health Statistics -- Mortality Multiple Cause File US 2014](ftp://ftp.cdc.gov/pub/Health_Statistics/NCHS/Datasets/DVS/mortality/mort2014us.zip)
- Analysis: reproducible `R` code is available on [github](https://github.com/jschoeley/codus2014); all plots have been created using the [`ggplot2`](http://docs.ggplot2.org/current/) library; my thanks to the [Hadleyverse](http://adolfoalvarez.cl/the-hitchhikers-guide-to-the-hadleyverse/)
- Poster Layout: [Inkscape](https://inkscape.org/en/)

cc-by Jonas Schöley