# Useful R Packages for Regression Models

## library(ggplot2)

**Plotting a fitted regression line with a confidence band**

```
ggplot(data, aes(x=x, y=y)) + geom_point() + geom_smooth(method=lm, col='magenta')
```

**Examining the predictor variable, X, with a boxplot**

```
ggplot(data, aes(x=x)) + geom_boxplot()
```

**Examining the predictor variable with a histogram**

```
ggplot(data, aes(x=x)) + geom_histogram(aes(y=..desnity..), binwidth=7) + geom_density(alpha=0.2)
```

## library(olsrr)

Produces nice graphics for ordinary linear regression OLS. 

**Residual qq-plot**

```
ols_plot_resid_qq(model1) 
```

**Residual vs. fitted values**

```
ols_plot_resid_fit(model1)
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

**Testing for Constant Variance**

```
levenTest(model1)
```

## library(alr3)

This package consists of data files and a few functions used in the textbook S. Weisberg (2005), 'Applied Linear Regression,' 3rd edition, Wiley. This package depends on the car package. Many functions formerly in alr3 have been renamed and now reside in car.

**lack of fit test**

```
pureErrorAnova(model1) # to get a regular anova table just call anova, not in alr3 package
```

## library(corrplot)

```
# plot with correlation coefficients
corr.matrix <- cor(Data)
corrplot(cor.matrix)
```

## library(psych)

```
pairs.panels(data[,-5], method="pearson", hist.col="darkorchid", density=T)
```
---

# Other

## Linear Regression Assumption: Are the error terms normally distributed? 

1. Testing normality of error terms via Shapiro Wilk.

We want to fail to reject the null to conclude errors are normally distributed. 

```
shapiro.test(residuals(model1))
```

2. Residual qq-plot.

```
library(olsrr)
ols_plot_resid_qq(model1) 
```

3. Histograms, box plots, dot plots.

## Linear Regression Assumption: Do the error terms have constant variance?

1. The Breusch-Pagan test.

```
library(car)
ncvTest(model1)
```

2. residual vs. fitted or predictor (megaphone trend).

```
library(olsrr)
ols_plot_resid_fit(model1)
```

## Linear Regression Assumption: Are the error terms independent?

1. residual vs. fitted or predictor (pattern?)

```
library(olsrr)
ols_plot_resid_fit(model1)
```

2. Durbin-Watson Test. 

We want to fail to reject the null to conclude independence.

```
library(car)
durbinWatsonTest(model1)
```

## Lack of Fit Test

We want to fail to reject the null hypothesis.

```
library(alr3)
pureErrorAnova(model1)
```
## Transformations on Y: Box Cox Power Transformation

```
library("EnvStats")
boxcox(model1, lambda, optimize=FALSE)
```
