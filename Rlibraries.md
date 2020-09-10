# Useful R Packages for Regression Models

## library(ggplot2)

**Plotting a fitted regression line with a confidence band**

```
ggplot(data, aes(x=x, y=y)) + geom_point() + geom_smooth(method=lm, col='magenta')
```

**Examining the predictor variable with a boxplot**

```
ggplot(data, aes(x=x, y=y)) + geom_boxplot()
```

**Examining the predictor variable with a histogram**

```
ggplot(data, aes(x=x)) + geom_histogram(aes(y=..desnity..), binwidth=7) + geom_density(alpha=0.2)
```

## library(olsrr)

Produces nice graphics 

**Residual qq-plot**

```
ols_plot_resid_qq(model1) 
```

**Residual vs. fitted values**

```
ols_plot_resid_fit(model1)
```

**Testing normality of residuals**

```
shapiro.test(residuals(model1))
```

## library(car)

**Testing non-constant variance of residual**

```
ncvTest(model1)
```

**Test for non-independence of residuals**

```
durbinWatsonTest(model1)
```

## library(alr3)

This package consists of data files and a few functions used in the textbook S. Weisberg (2005), 'Applied Linear Regression,' 3rd edition, Wiley. This package depends on the car package. Many functions formerly in alr3 have been renamed and now reside in car.

**lack of fit test**

```
pureErrorAnova(model1) # to get a regular anova table just call anova, not in alr3 package
```

