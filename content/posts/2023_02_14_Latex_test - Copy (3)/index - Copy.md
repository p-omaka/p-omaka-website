---
title: "Test post please ignore"
author: "RR"
date: 2023-02-11T22:13:14-05:00
categories: [statistika]
tags: [test, plačna vrzel]
---



# Testing LaTeX functions

only fooling around

Tole je skopirano s faksa nekej :taps_head:

$$
L(\beta_0, \beta) = \prod_{i=1}^{n}P(x_i)^{y_i}(1-P(x_i))^{1-y_i}
$$


```r

set.seed(8)

st_ur = rnorm(1000, 5)      # st ur
st_dn_tock = rnorm(1000, 4)       # st tock pri domacih nalogah
z = -31 + 3*st_ur + 4*st_dn_tock       # linearna kombinacija z \beta_0
pr = 1/(1+exp(-z))  
y = rbinom(1000,1,pr)                # bernoulli odziv glede na \pi=pr

#pošlji v glm:
df = data.frame(y = y, 
                st_ur = st_ur, 
                st_dn_tock = st_dn_tock)
fit <- glm(y ~ st_ur + st_dn_tock,
           data = df,
           family = "binomial")

# predict3d(fit,radius=0.08)

ggplot(df, aes(x = st_ur, y = y)) +
    geom_point(alpha = 0.5) +
    stat_smooth(method = "glm", 
                se = F, 
                method.args = list(family="binomial"))
## `geom_smooth()` using formula = 'y ~ x'
```

<img src="/posts/2023_02_14_Latex_test - Copy (3)/index - Copy_files/figure-html/unnamed-chunk-1-1.png" width="672" style="display: block; margin: auto;" />

```r

ggplot(df, aes(x = st_dn_tock, y = y)) +
    geom_point(alpha = 0.5) +
    stat_smooth(method = "glm", 
                se = F, 
                method.args = list(family="binomial"))
## `geom_smooth()` using formula = 'y ~ x'
```

<img src="/posts/2023_02_14_Latex_test - Copy (3)/index - Copy_files/figure-html/unnamed-chunk-1-2.png" width="672" style="display: block; margin: auto;" />
