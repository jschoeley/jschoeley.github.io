---
title  : The Unknown Pleasures of Demography
author : Jonas Schöley
date   : 2017-06-28
tags   : mortality vis R
layout : post
---

![Joy Division - Unknown Pleasures](/assets/2017-06-28-the_unknown_pleasures_of_demography/folder.jpg)

Did you know that the cover of Joy Divisions classic "Unknown Pleasures" [shows the radio frequency spectrum of the first discovered pulsar over time?](https://blogs.scientificamerican.com/sa-visual/pop-culture-pulsar-origin-story-of-joy-division-s-unknown-pleasures-album-cover-video/) I always loved this visualization. It's a poor man's perspective plot but because of its limitations full of charm. Also, unlike true 3D plots it does not feature visual compression towards a vanishing point. Each line is just offset by some value along the y-axis but not otherwise rescaled, i.e. differences in magnitude don't appear more striking in the foreground and get squished towards the "horizon", they remain constant.

And who's to say Swedish mortality isn't as interesting as cosmic pulsars? Let me show you the unknown pleasures of demography. Swedish life-tables by period.

```
library(HMDHFDplus)
lt <- readHMDweb(CNTRY = "RUS", item = "bltper_1x1",
                 username = "***", password = "***")
```

Below you find a small function taking in three vectors and spitting out superimposed curves Joy Division Style. You can even change viewing direction and angle...

```
MakeJoy <- function(x, y, z, angle = 1, reverse = FALSE) {
  require(ggplot2)
  Normalize <- function (x) {(x-min(x))/(max(x)-min(x))}
  df = data.frame(x = x, y = Normalize(y), z = z)
  p <- ggplot(NULL, aes(x = x, y = y+z/angle)) +
    theme_void() +
    theme(plot.background = element_rect(fill = "black"), aspect.ratio = 1,
          text = element_text(colour = "grey"))
  for (i in sort(unique(df$y), decreasing = reverse)) {
    dat = df[df$y == i, ]; dat$z = Normalize(dat$z)
    if (identical(reverse, FALSE)) { dat$y = -dat$y }
    dat0 = rbind(data.frame(x = min(dat$x), y = dat$y[1], z = 0), dat)
    dat0 = rbind(dat0, data.frame(x = max(dat$x), y = dat$y[1], z = 0))
    p <- p +
      geom_polygon(color = NA, fill = "black", show.legend = FALSE, data = dat0) +
      geom_line(color = "white", data = dat)
  }
  return(p)
}

MakeJoy(x = lt$Age, y = lt$Year, z = lt$dx)
```

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-2-1.png)

The `angle` argument changes a global scaling factor which is the same for all the lines and simulates the effect of a pseudo-perspective change.

```
MakeJoy(x = lt$Age, y = lt$Year, z = lt$dx, angle = 4)
```

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-3-1.png)

We can also look at the plot from the opposite side.

```
MakeJoy(x = lt$Age, y = lt$Year, z = lt$dx, reverse = TRUE)
```

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-4-1.png)

What are we actually looking at? A series of filled polygons occluding each other.

```
MakeJoy(x = lt$Age, y = lt$Year, z = lt$dx) + theme_classic()
```

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-5-1.png)

Using lines as primary visual encoding allows us to see small details in the data such as cohort artefacts...

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/deuw.png)

...age-heaping...

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/esp.png)

...smooting...

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/isl.png)

Let's get serious...

```
library(tidyverse)
library(gridExtra)

walk(getHMDcountries(), function (x) {
  lt <- readHMDweb(CNTRY = x, item = "bltper_1x1",
                   username = "***", password = "***")
  lt <- filter(lt, dx != 0)
  pl <- MakeJoy(x = lt$Age, y = lt$Year, z = lt$dx, angle = 3) +
    ggtitle(paste(x, min(lt$Year), "to", max(lt$Year)),
            subtitle = "time flows back to front | cc-by Jonas Schöley | Data: mortality.org")
  print(pl)
})
```

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-1.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-2.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-3.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-4.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-5.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-6.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-7.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-8.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-9.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-10.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-11.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-12.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-13.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-14.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-15.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-16.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-17.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-18.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-19.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-20.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-21.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-22.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-23.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-24.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-25.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-26.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-27.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-28.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-29.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-30.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-31.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-32.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-33.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-34.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-35.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-36.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-37.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-38.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-39.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-40.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-41.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-42.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-43.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-44.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-45.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-46.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-47.png)

![](/assets/2017-06-28-the_unknown_pleasures_of_demography/unnamed-chunk-6-48.png)
