# R Introduction

## Simple R commands

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
![image](https://github.com/marcocutraro/DMSL/assets/105051608/6a8002c4-fe1f-46b7-968a-d89450530168)

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
z <- (z - t(z)) / 2
```
```
contour(x, y, z,
        nlevels = 15)
```
image() produces a color-coded plot whose colors depends on the z value, also known as a heat-map
```
image(x, y, z,
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
persp(x, y, z)
```
![image](https://github.com/marcocutraro/DMSL/assets/105051608/316a8e2e-5d0a-4574-b8eb-e5d3cdbd1187)

```
persp(x, y, z,
      theta = 30,
      phi = 0)
```
![image](https://github.com/marcocutraro/DMSL/assets/105051608/f645fb89-6e8b-4870-a333-5489ea396e6d)

```
persp(x, y, z,
      theta = 30,
      phi = 40)
```
![image](https://github.com/marcocutraro/DMSL/assets/105051608/99a2b274-7e7e-4b2a-998a-ef1e57d54470)

## Loading Data

read.table() for importing a data set into R

write.table() to export data
```
Auto <- read.table(".../Auto.data",
                   header = T,
                   na.strings = '?',
                   stringsAsFactors = T)
View(Auto)
head(Auto)
```
![image](https://github.com/marcocutraro/DMSL/assets/105051608/59cf2c6e-ba20-40bf-98a7-8bd89b422580)
```
dim(Auto)
```
![image](https://github.com/marcocutraro/DMSL/assets/105051608/6835ec3f-365f-4841-a532-8856c27def89)
```
names(Auto)
```
![image](https://github.com/marcocutraro/DMSL/assets/105051608/a077ed04-377c-429a-8ff8-affa5feaced0)


## Graphical and numerical summaries
```
Auto$cylinders <- as.factor(Auto$cylinders)

plot(Auto$cylinders, Auto$mpg,
     xlab = "cylinders",
     ylab = "mpg",
     col = "lightblue",
     varwidth = T,
     horizontal = T)
```
![image](https://github.com/marcocutraro/DMSL/assets/105051608/7fb28b23-1e9e-4ea2-ae0a-f7ca7d54cb67)

hist() can be used to plot an histogram
```
hist(mpg, 
     col ="orange", 
     breaks = 15)
```
![image](https://github.com/marcocutraro/DMSL/assets/105051608/06db83c4-b928-441b-baa5-47cacdc125ac)

```
pairs(Auto)

pairs(
  ~ mpg + 
    displacement + 
    horsepower + 
    weight + 
    acceleration,
  data = Auto,
  col = "purple"
)
```
![image](https://github.com/marcocutraro/DMSL/assets/105051608/613a6c2f-52ba-4a1f-a264-ad90926431f3)

summary function produces a numerical summary of each variable

```
summary(Auto)
```
![image](https://github.com/marcocutraro/DMSL/assets/105051608/da1cc47b-87ce-44ed-b625-aa262270df2c)

For qualitative variables such as name, R will list the number of observations that fall in each category. We can also produce a summary of just a singlevariable.
