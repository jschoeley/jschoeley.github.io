---
title  : The Age Pattern of Human Fetal- and Infant Mortality
author : Jonas Schöley
date   : 2015-10-15
tags   : science, mortality, visualization, datavis, R
layout : post
---

![](/assets/2015-10-15-the_age_pattern_of_human_fetal_and_infant_mortality/us2009_conception_cohort_gestational_age_mortality_pattern.png)
*Mortality Rates over Gestational Age for the US 2009 Conception Cohort*

Using [US microdata on fetal- and infant mortality](ftp://ftp.cdc.gov/pub/Health_Statistics/NCHS/Datasets/DVS/) I constructed a cohort of individuals who where conceived in the year 2009. I then constructed a life-table for this population with gestational age (time since last menses of the mother) in weeks as time dimension. This approach allows for an integrated view on fetal- and infant mortality age patterns.

The above plot shows the mortality rates of the US 2009 Conception Cohort over gestational age, starting with week 20. The same sharp decline in mortality rates which is known to happen over the days, weeks and months after birth is visible prior to birth, only on a higher level. Around gestational week 33--40 we can see a "birth hump". Birth itself is a risky event for the unborn child and momentarily increases the chance of dying.

See [here](https://github.com/jschoeley/fimort-agepat/tree/7dd737c44d7abc41285d09c6f0a1d177c93f19d9) for the full analysis.

cc-by Jonas Schöley