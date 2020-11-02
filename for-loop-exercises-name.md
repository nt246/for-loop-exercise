`for loop` exercises
================

<br>

## Gapminder data

Today, we’ll be using a subset of the [Gapminder
dataset](https://www.gapminder.org/tools/?from=world#$chart-type=bubbles),
which represents the health and wealth of nations. It was pioneered by
[Hans Rosling](https://www.ted.com/speakers/hans_rosling), who is famous
for describing the prosperity of nations over time through famines, wars
and other historic events with this beautiful data visualization in his
[2006 TED Talk: The best stats you’ve ever
seen](https://www.ted.com/talks/hans_rosling_shows_the_best_stats_you_ve_ever_seen).

INSERT THE IMAGE FOUND AT THIS URL:
<https://s3-eu-west-1.amazonaws.com/static.gapminder.org/GapminderMedia/wp-uploads/20180914115336/Screen-Shot-2018-09-14-at-12.51.17-1024x557.png>

<br>

We will use a subset of the gapminder data included in the R package
`gapminder`. So first we need to install that package and load it, along
with the tidyverse. Then have a look at the data in `gapminder`

``` r
library(tidyverse)
library(gapminder) #install.packages("gapminder")

gapminder
```

<br>

Here is the for loop we created together to save plots of gdpPercap
vs. year for all countries in the dataset:

``` r
dir.create("figures") 

## create a list of countries
country_list <- unique(gapminder$country) # ?unique() returns the unique values

for (cntry in country_list) {
  
  ## filter the country to plot
  gap_to_plot <- gapminder %>%
    filter(country == cntry)
  
  ## plot
  my_plot <- ggplot(data = gap_to_plot, aes(x = year, y = gdpPercap)) + 
    geom_point() +
    ## add title and save
    labs(title = paste(cntry, "GDP per capita", sep = " "))
  
  ## add the figures/ folder
  ggsave(filename = paste("figures/", cntry, "_gdpPercap.png", sep = ""), plot = my_plot)
} 
```

This code has been copied to the code chunk below.

### Your task:

1.  Modify our `for` loop so that it:
      - loops through countries in Europe only
      - plots the sum of gdpPercap and population size per year (should
        approximate the total GDP)
      - saves them to a new subfolder inside the (recreated) figures
        folder called “Europe”.
2.  Sync to GitHub

<br>

``` r
dir.create("figures") 

## create a list of countries
country_list <- unique(gapminder$country) # ?unique() returns the unique values

for (cntry in country_list) {
  
  ## filter the country to plot
  gap_to_plot <- gapminder %>%
    filter(country == cntry)
  
  ## plot
  my_plot <- ggplot(data = gap_to_plot, aes(x = year, y = gdpPercap)) + 
    geom_point() +
    ## add title and save
    labs(title = paste(cntry, "GDP per capita", sep = " "))
  
  ## add the figures/ folder
  ggsave(filename = paste("figures/", cntry, "_gdpPercap.png", sep = ""), plot = my_plot)
} 
```

<br>
