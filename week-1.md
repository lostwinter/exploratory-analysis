## Week One
Principles of Exploration: show comparisons, show causality, show multivariate, integrate words, numbers, images and diagrams, tell a complete and credible story, content is king.

Exploratory graphs: What do my data look like?

#### One-Dimensional Summaries
5-n summary: `summary(df$var)`
boxplot: `boxplot(df$var)` and add `abline(v = 2, lwd = 1)`
histogram: `hist(df$var); rug(df$var)`  
density plot: 
barplot:`barplot(table(df$var), col="Variable", main="Title")`

#### Two-Dimensional Summaries
Multiple boxplot: `boxplot(var1 ~ var2, data=df, col="color")`
Scatterplot: `with(df, plot(var1, var2)) color="factor" to add variable`

#### Plotting Systems
Base: start blank, make plot, and build up. Can't go 'back.' ex. `with(df, plot(var1, var2))`
Lattice: Plot made wiht single function call. Good for many plots needed on one screen.
Ggplot2: 

###### Base Plotting System 
Initialize new plot. Then annotate. 
Functions
  `plot; lines; points; text; title; axis`
  
  example:
  ```r
  with(airquality, plot(Wind, Ozone, main="Title"))
  with(subset(airquality, Month ==5), points(Wind, Ozone, col="blue")
  with(subset(airquality, Month !=5), points(Wind, Ozone, col="red")
  legend("topright", pch = 1, col=c("blue", "red"), legend = c("May","Other Months"))
  model <- lm(Ozone ~ Wind, airquality)
  abline(model, lwd=2)
  ```
  
  Multiple plot ex
 ```r 
  par(mfrow = c(1,2))
  with(airquality, {
      plot(Wind, Ozone, main="Title 1")
      plot(Solar.R, Ozone, main="Title 2")
      mtext("Main Title", outer=T)
  })
```
Many parameters! Check: ?par 
  `pch ; lty ; lwd ; col ; xlab ; ylab ;` 
For global graphics: par()
  `las ; bg #backgrond color ; mar #margin size ; oma #outer margin size ; mfrow #n plots per row ; mfcol`
  
##### Graphics Devices 
1. Screen Device
  Copy screen plot to PDF: `dev.copy2pdf; dev.off()`
2. Files
*Vectors: pdf; svg
*Bitmap: png; jpg; tiff; bmp
  
  1. `pdf(file="myplot.pdf")` Makes myplot file in working directory
  2. then make plot
  3. `dev.off()` Then view myplot from computer
