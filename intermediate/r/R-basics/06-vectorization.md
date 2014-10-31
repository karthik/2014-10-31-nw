
# Some notes on vectorization

Many operations in R are vectorized which means that writing code is more efficient, concise and easy to read.

Idea with vectorized operations is that things can happen in parallel without needing to act on one element at a time.


```r
x <- 1:4
y <- 6:9 
```

Mathematical operations are performed element wise:


```r
x + y
```

```
## [1]  7  9 11 13
```

```r
x - y
```

```
## [1] -5 -5 -5 -5
```

```r
x * y
```

```
## [1]  6 14 24 36
```

```r
x / y
```

```
## [1] 0.1666667 0.2857143 0.3750000 0.4444444
```

Boolean comparisons return logical vectors:


```r
y == 8
```

```
## [1] FALSE FALSE  TRUE FALSE
```

```r
x > 2
```

```
## [1] FALSE FALSE  TRUE  TRUE
```

```r
x >= 2
```

```
## [1] FALSE  TRUE  TRUE  TRUE
```

A shorter vector is recycled:


```r
z <- c(1, 2)
x * z
```

```
## [1] 1 4 3 8
```

Matrix operations are also vectorized:


```r
x <- matrix(1:4, 2, 2)
y <- matrix(rep(10, 4), 2, 2)
x * y # is not matrix multiplication. It's element wise
```

```
##      [,1] [,2]
## [1,]   10   30
## [2,]   20   40
```

```r
x / y # is elementwise division.
```

```
##      [,1] [,2]
## [1,]  0.1  0.3
## [2,]  0.2  0.4
```

Element wise matrix operations are performed by column. In the example below, `y[1, 1]` is multipled by `z[1]`, followed by `y[1, 2]` multiplied by `z[2]`, and then the vector `z` is recycled for multipying the second column of `y`.


```r
y * z
```

```
##      [,1] [,2]
## [1,]   10   10
## [2,]   20   20
```

True matrix multiplication is:


```r
x %% y
```

```
##      [,1] [,2]
## [1,]    1    3
## [2,]    2    4
```

Vectorized operations make code a lot simpler.




