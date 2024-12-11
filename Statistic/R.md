## Example

```R
Z <- read.csv("XXX.csv")
text = "Hello, World!"
print(text)
# [1] "Hello, World!"
a = c(1, 2, 3)
print(a)
# [1] 1 2 3
b = c(4, 5, 6)
print(b)
# [1] 4 5 6
print(b == a)
# [1] FALSE FALSE FALSE
print(b == a + 3)
# [1] TRUE TRUE TRUE

d = matrix(c(a, b, c(7, 8, 9)), nrow=3, ncol=3)
print(d)
#      [,1] [,2] [,3]
# [1,]    1    4    7
# [2,]    2    5    8
# [3,]    3    6    9

d1 = matrix(c(a, b, c(7, 8, 9)), nrow=3, ncol=3, byrow=TRUE)
print(d1)
#     [,1] [,2] [,3]
# [1,]    1    2    3
# [2,]    4    5    6
# [3,]    7    8    9

print(is.matrix(d1))
# [1] TRUE
```

## Types
- numeric
- character
- logical
## Data structures
- [[R#Vector|vectors]]
- [[R#Lists|lists]]
- matrices
- data frames

### Vector
```R
# this is a comment
num.var <- c(1,2,3,4)
char.var <- c("1", "2", "3")
log.var <- c(TRUE, TRUE)
```
### Lists
```R
# create a list - a collection of vectors
employees <- c("John", "Sunil", "Anna")
years <- c(3, 2, 6)
emp <- list(employees, years)
print(emp)
# [[1]]
# [1] "John" "Sunil" "Anna"
# [[2]]
# [1] 3 2 6
```
### Dataframes
A data.frame is a list of vectors, each of the same length
```R
DF <- data.frame(x=1:5, y=letters[1:5], z=letters[6:10])
print(DF)
# data.frame with 3 columns and 5 rows
#   x y z
# 1 1 a f
# 2 2 b g
# 3 3 c h
# 4 4 d i
# 5 5 e j
```

For structures:
- how many elements? `length(x)`
- <i>i</i>th element                 `x[2] (i = 2)`   (R is 1-based)
- all but <i>i</i>th element      `x[-2] (i = 2)`
- first k elements           `x[1:5] (k = 5)`
- last k elements            `n=length(x); x[n-5:n]  (k = 5)`
- specific elements         `x[c(1, 3, 5)]`
- condition                     `x[x>3], x[x<=2], x[x<0 | x>3]` or `which(x > 3)`

## R Library
```R
# Install
install.packages("XX")
# Use
library(XXX)
```
## Basic Functions

### length()

Get or set the length of vectors (including lists) and factors, and of any other R object for which a method has been defined.

```R
x <- c(1, 2, 3, 4, 5)
length(x)
# [1] 5
```

### sum()

returns the sum of all the values present in its arguments

```R
x <- c(1, 2, 3, 4, 5)
sum(x)
# [1] 15
```

### max, min
```R
x <- c(1, 2, 3, 4, 5)
max(x)
# [1] 5
min(x)
# [1] 1
```

### range()

returns a vector containing the minimum and maximum of all the given arguments.

```R
x <- c(1, 1, 2, 3, 5)
range(x)
# [1] 1 5
```

### mean()

Generic function for the (trimmed) arithmetic mean.

```R
x <- c(1, 2, 3, 4, 5)
mean(x)
# [1] 3
```

### sin(), cos(), tan(), asin(), acos(), atan(), atan2(), acosh(), asinh(), atanh()

trigonometric functions

### any()

Given a set of logical vectors, is at least one of the values true?

```R
x <- c(1, 2, 3, 4, 5)
y <- c(1, 2, 3, 4, 5)
any(x == y)
# [1] TRUE
```

### all()

Given a set of logical vectors, are all of the values true?

```R
x <- c(1, 2, 3, 4, 5)
y <- c(1, 2, 3, 4, 5)
all(x == y)
# [1] TRUE
```

### append()

appends elements to a vector.

```R
x <- c(1, 2, 3, 4, 5)
append(x, 6)
# [1] 1 2 3 4 5 6
append(x, c(6, 7, 8), after=3)
# [1] 1 2 3 6 7 8 4 5
```

### summary()

a generic function used to produce result summaries of the results of various model fitting functions. The function invokes particular methods which depend on the class of the first argument.

```R
x <- c(1, 1, 2, 3, 5)
summary(x)
#   Min. 1st Qu.  Median    Mean 3rd Qu.    Max.
# 1.000   1.000   2.000   2.400   3.000   5.000
```

## Library: stats

### median()

returns the median of the values present in its arguments.

```R
x <- c(1, 1, 2, 3, 5)
median(x)
# [1] 2
```

### var()
```R
x <- c(1, 2, 3, 4, 5)
var(x)
# [1] 2.5
```

### sd()
```R
x <- c(1, 2, 3, 4, 5)
sd(x)
# [1] 1.581139
```

### cor()
```R
x <- c(1, 2, 3, 4, 5)
y <- c(2, 3, 4, 5, 6)
cor(x, y)
# [1] 1
```

### cov()
```R
x <- c(1, 2, 3, 4, 5)
y <- c(2, 3, 4, 5, 6)
cov(x, y)
# [1] 2.5
```

