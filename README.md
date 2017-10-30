<!-- README.md is generated from README.Rmd. Please edit that file -->
shadow text grob: `shadowtextGrob` and `grid.shadowtext`
--------------------------------------------------------

``` r
library(shadowtext)
grid.shadowtext("grid is awesome", gp=gpar(cex=3, col="white"), rot=45)
grid.shadowtext("hello world", y=0.85, gp=gpar(cex=5, col="steelblue"), bg.color="firebrick")
grid.shadowtext("R you ready!!!", y=.1, gp=gpar(cex=4, col="firebrick"))
```

![](Figs/unnamed-chunk-2-1.png)

ggplot2 layer: `geom_shadowtext`
--------------------------------

``` r
library(ggplot2)

random_text <- function(n=1, length=10) {
    d <- data.frame(n=1:n, length=length)
    sapply(1:nrow(d), function(i) {
        paste(sample(c(0:9, letters, LETTERS),
                     d$length[i], replace=TRUE),
              collapse="")
    })
}

n <- 10
set.seed(2017-10-27)
d <- data.frame(x = rnorm(n), y=rnorm(n),
                label = random_text(n),
                angle = sample(0:360, 10))
p <- ggplot(d, aes(x, y)) + xlim(-2, 2.2) + ylim(-2, 2.4)

p + geom_shadowtext(aes(label=label, angle=angle), size=5)
```

![](Figs/unnamed-chunk-3-1.png)

``` r
p + geom_shadowtext(aes(label=label, angle=angle, color=label),
                    bg.color='firebrick', size=5) +
    theme(legend.position="none")
```

![](Figs/unnamed-chunk-3-2.png)
