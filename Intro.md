
### A super brief intro to R  

This is not meant to be a thorough summary of all the wonderful features R can do but a simple way to get started. Up front, I want to summarize some best practices when using R, inspired by Dan Rabosky's presentation at a NESCent Academy a few years ago. A detailed introduction can be found here: https://cran.r-project.org/doc/manuals/r-release/R-intro.pdf or https://cran.r-project.org/doc/manuals/R-intro.html

When executing R code, always use an editor like the built-in R editor or other apps such as Sublime. It's OK to use the console for the simplest 1-line statements, but really, for anything else, please use the editor. This saves your work, and it doesn't choke when executing multiple lines

On a Mac, you can simply execute code from the R editor by highlighting code in the editor window and pressing "command + return". If executing code line-by-line, "command+return"" will execute the line of code indicated by your cursor in the editor window. On a PC, Ctrl+R will do the same.

Also, please don't copy and paste code from an editor into the R console as that completely beats the purpose of the editor

Another big advantage that comes with writing your code in the editor is your ability to annotate and comment your work. Every segment of your code should be commented as it will be super helpful when you return to your work a few weeks later. Your future self will be quite thankful for your annotations, reminders, and explanations... From my own experience, it's quite frustrating when you look at your old scripts and you have no idea what the code actually does.

The "equals" sign in R is the assignment operator: '<-' consisiting of the '<' and '-' symbols.
This must always go the same direction:

```{r}
a <- 10 #demonstrating the use of the arrow operator
```
and never
```{r}
10 -> a #don't do it this way, please
```
While the latter will work, it will make for virtually unreadable code and you really don't want that. In most cases the assignment operator can also be the '=' sign, but that may cause problems in some instances. Let's stick to the assignment operator using the arrow symbol. Looks cooler, anyway.

Finally, if you need more details on a function, you can always call the help file by typing '?function'. For example, today you may want to type '?mean' to find out how to use this function.
```{r, message=FALSE}
?mean
```

All the entities generated in R are known as *objects*. These can be a variety of things, such as array of numbers, simple variables, strings of characters, among others. Above, we defined *a* as 10, and hence *a* would be considered an *object*. When you carry out your analyses in R you'll end up with a long list of different *objects*, which altogether make up your *workspace*. By the way, the name of the *object* is completely arbitrary, but it should not be the name of an already existing *object*, including *functions*.

Let's briefly talk about some of the different types of *objects* that you will typically encounter when working with R. We will start with vectors, factors, and dataframes, other types follow soon.

I would say the simplest *object* in R is probably a *vector*, which is an ordered collection of numbers. For example, with the 'c()' function, we can combine multiple values into a vector.

```{r}
x <- c(102.1, 98.7, 88.9, 110.2, 93.7, 43.4, 102.5, 120.8) #assigning numbers to a vector object called x
x #show the vector
```

*factors* provide a convenient way to handle categorical data, e.g., information about the diet of organisms. We can combine such categorical information with the 'c()' function to create a string variable, but need to take care to place double quote marks around each categorical value. Then, we create the factor with the 'factor()' function.

```{r}
dietinfo <- c("zooplankton", "zooplankton", "zooplankton", "fish", "zooplankton", "zooplankton", "fish", "zooplankton") #combining diet preference into a character string
diet <- factor(dietinfo) #convert into factor
is.factor(diet) #check if it actually is recognized as a factor
```

Another useful command in dealing with factors is the 'levels()' function, which displays the different categories found in the data. You can easily see that we only have two different categories (fish and zooplankton) in our little example, but this will come in useful when you are dealing with larger datasets.

```{r}
levels(diet) #check what categories are found in your factor
```
Next up are *dataframes*. These *objects* are multidimensional, i.e., they have more than one column and each column may contain different *object* types. For example, we may have a *dataframe* consisting of a mix of *vectors* and *factors*. 

```{r}
all.data <- data.frame(x, diet)
class(all.data) #what object are we dealing with? Better be a data.frame...
all.data #show your data
```

That's good enough with respect to different *objects* in R for now. As I mentioned, more will follow later. Let's move on to some basic descriptive functions that allow you to explore your data.

```{r}
min(x)
max(x)
range(x)
mean(x)
var(x) #variance
sd(x) #standard deviation
```

You can also carry out arithmetic operations with your *vectors*, which are done element by element. For example, you can divide all elements of your *vector* by 100 or do other transformations such as a log10 transformation.

```{r}
x1 <- x/100 #divide by 100
x1

x2 <- log10(x) #base 10 logarithm
x2

```

To round out this first brief intro to R, let's plot something. Visualization is one of the big benefits of R. We already have one *vector* with numerical data (*x*), but let's make another one so we can make a bivariate scatter plot. We'll call that *vector *y*.

```{r}
y <- c(105.9, 92.9, 82.1, 117.5, 90.1, 54.7, 109.3, 102.4)

plot(x, y, pch=19) #plotting x and y using filled circles
```

Alright, that looks pretty good already but there is much more we can do. For example, what about different axis labels? Or larger dots? Or a title for the entire chart? Or different colors, maybe? All this can be done. Now that you have made it thus far, open up the help for the 'plot()' function and determine what you need to do to modify the plot to your liking. I will assist, of course, and continue this tutorial once you have done some initial exploring. 

```{r}
?plot
```

