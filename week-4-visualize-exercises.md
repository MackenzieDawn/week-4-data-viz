# Visualize Data
Mackenzie Eckles

<!-- If you get the error "Error in list2(na.rm = na.rm, ...) : object 'ffi_list2' not found" do the following in the Console run:  
&#10;    remove.packages("rlang")
&#10;Then Restart R to be safe. Then run:
&#10;    install.packages("rlang")
&#10;and again restart R to be safe. That should fix the problem (which is a package dependency issue).   -->

Try your code again

## Your Turn 0

Add a setup chunk that loads the tidyverse packages.

``` r
head(mpg)
```

    # A tibble: 6 × 11
      manufacturer model displ  year   cyl trans      drv     cty   hwy fl    class 
      <chr>        <chr> <dbl> <int> <int> <chr>      <chr> <int> <int> <chr> <chr> 
    1 audi         a4      1.8  1999     4 auto(l5)   f        18    29 p     compa…
    2 audi         a4      1.8  1999     4 manual(m5) f        21    29 p     compa…
    3 audi         a4      2    2008     4 manual(m6) f        20    31 p     compa…
    4 audi         a4      2    2008     4 auto(av)   f        21    30 p     compa…
    5 audi         a4      2.8  1999     6 auto(l5)   f        16    26 p     compa…
    6 audi         a4      2.8  1999     6 manual(m5) f        18    26 p     compa…

## Your Turn 1

Run the code on the slide to make a graph. Pay strict attention to
spelling, capitalization, and parentheses!

``` r
# creating a scatterplot
ggplot(mpg) +
  geom_point(aes(x = displ, 
                 y = hwy))
```

![](week-4-visualize-exercises_files/figure-commonmark/Making-a-graph-1.png)

## Your Turn 2

Replace this scatterplot with one that draws boxplots. Use the
cheatsheet. Try your best guess.

``` r
# altering code to make a boxplot
ggplot(data = mpg) +
  geom_boxplot(mapping = aes(x = class, y = hwy))
```

![](week-4-visualize-exercises_files/figure-commonmark/Creating-a-Boxplot-1.png)

## Your Turn 3

Make a histogram of the `hwy` variable from `mpg`. Hint: do not supply a
y variable.

``` r
# Make a histogram

ggplot(data = mpg) +
  geom_histogram(mapping = aes(x = hwy))
```

    `stat_bin()` using `bins = 30`. Pick better value `binwidth`.

![](week-4-visualize-exercises_files/figure-commonmark/Creating-a-histogram-1.png)

## Your Turn 4

Use the help page for `geom_histogram` to make the bins 2 units wide.

``` r
# Make bins 2 units wide
ggplot(data = mpg) +
  geom_histogram(mapping = aes(x = hwy), binwidth = 2)
```

![](week-4-visualize-exercises_files/figure-commonmark/Changing-Bin-Width-1.png)

## Your Turn 5

Add `color`, `size`, `alpha`, and `shape` aesthetics to your graph.
Experiment.

``` r
# add color, size, alpha, and shape

ggplot(data = mpg) +
  geom_point(mapping = aes(x = displ, 
                           y = hwy),
             color = "magenta",
             size = 2,
             alpha = 0.5,
             shape = "square")
```

![](week-4-visualize-exercises_files/figure-commonmark/Change-Graph-Aesthetics-1.png)

## Help Me

What do `facet_grid()` and `facet_wrap()` do? (run the code, interpret,
convince your group)

``` r
# Makes a plot that the commands below will modify
q <- ggplot(mpg) + geom_point(aes(x = displ, y = hwy))

q + facet_grid(. ~ cyl)
```

![](week-4-visualize-exercises_files/figure-commonmark/Using-Facets-1.png)

``` r
q + facet_grid(drv ~ .)
```

![](week-4-visualize-exercises_files/figure-commonmark/Using-Facets-2.png)

``` r
q + facet_grid(drv ~ cyl)
```

![](week-4-visualize-exercises_files/figure-commonmark/Using-Facets-3.png)

``` r
q + facet_wrap(~ class)
```

![](week-4-visualize-exercises_files/figure-commonmark/Using-Facets-4.png)

## Your Turn 6

Make a bar chart `class` colored by `class`. Use the help page for
`geom_bar` to choose a “color” aesthetic for class.

``` r
# fill for bars

ggplot(data = mpg) +
  geom_bar(mapping = aes(x = class, fill = class)) +
  guides(fill = "none")+
  labs(x = "Class of Vehicle",
       y = "Number of Vehicles in Sample")+
  theme_classic()
```

![](week-4-visualize-exercises_files/figure-commonmark/Making-a-Barchart-1.png)

## Quiz

What will this code do?

This will add multiple geometries to the same plot.

``` r
ggplot(mpg) + 
  geom_point(aes(displ, hwy)) +
  geom_smooth(aes(displ, hwy)) 
```

    `geom_smooth()` using method = 'loess' and formula = 'y ~ x'

![](week-4-visualize-exercises_files/figure-commonmark/Multiple-Geometries-1.png)

``` r
# saving graphs:
# ggsave("example.jpg", width = _, height = _)
```

------------------------------------------------------------------------

# Take aways

You can use this starter code template to make thousands of graphs with
**ggplot2**.

``` r
ggplot(data = <DATA>) +
  <GEOM_FUNCTION>(mapping = aes(<MAPPINGS>))
```
