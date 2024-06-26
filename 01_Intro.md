## simple R commands

```
x <- c(1,2,3)
y <- c(4,5,6)
```
```
length(x)
length(y)
```
```
x + y
```
ls() allows us to look at a list of all objects
```
ls()
```
rm() can be used to delete any objects we don't want
```
rm(x, y)
```
delete all object at once
```
rm(list = ls())
```
create a matrix
```
x <- matrix(data = c(1,2,3,4), nrow = 2, ncol = 2)
```
x <- matrix(c(1,2,3,4), 2, 2)

byrow = TRUE to populate the matrix in order of the rows

x <- matrix(c(1,2,3,4), 2, 2, byrow = TRUE)

```
sqrt(x)
x^2
```

rnorm() generates a vector of random normal variables, with first argument the the sample size "n", if mean and sd are no specified, rnorm() creates standard normal random variables by default
```
x <- rnorm(50)
y <- x + rnorm(50, mean = 10, sd = .1)
cor(x, y)
```
set.seed reproduce the exact same set of random numbers
```
set.seed(12345678)
rnorm(50)
```
```
set.seed(3)
y <- rnorm(50)
mean(y)
var(y)
sd(y)
```

## Graphics

plot() is the primary way to plot data in R.
plot(x, y) produces a scatterplot of x vs y
?plot to find out more information
```
x <- rnorm(100)
y <- rnorm(100)
```
```
plot(x, y,
     xlab = "x-axis",
     ylab = "y-axis",
     main = "x vs y",
     col = "blue")
```
![image](https://github.com/marcocutraro/DMSL/assets/105051608/bdd73d6e-d26d-4499-ae27-87942a7f2b80)


pdf() or jpeg() to save th output of an R plot

```
x <- seq(1, 10)
x
x <- 1:10
x
x <- seq(0, 1, length = 5)
x
x <- seq(-pi, pi, length = 50)
x
```

contour() produces a contour plot in order to represent 3d data, like a topographical map. Arguments:
1. A vector of the x values
2. A vector of the y values
3. A matrix that correspond to the z values for each pair of (x, y)

```
y <- x
z <- outer(x, y, function(x, y) cos(y) / (1 + x^2))
```
```
contour(x, y, z,
        nlevels = 45,
        add = T)
```
```
za <- (z - t(z)) / 2
```
```
contour(x, y, za,
        nlevels = 15)
```
image() produces a color-coded plot whose colors depends on the z value, also known as a heat-map
```
image(x, y, za,
        nlevels = 15,
        add = T)
```
re-running contour() after image() for overlapping

![image](https://github.com/marcocutraro/DMSL/assets/105051608/2a803e5e-5b15-4b54-bf47-51f8455cf1d8)

persp() can be used to produce a 3d plot

arguments theta and phi control the angles at which the plot is viewed
```
image(x, y, z)
```
```
persp(x, y, za)
persp(x, y, za,
      theta = 30,
      phi = 0)
```
![image](https://github.com/marcocutraro/DMSL/assets/105051608/ea347765-18a2-4ab5-9bc0-1dceac34ac45)

```
persp(x, y, za,
      theta = 30,
      phi = 40)
```
![image](https://github.com/marcocutraro/DMSL/assets/105051608/18464524-5827-4958-abda-95a5ec3ee5a3)


