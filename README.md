# canvasXpress R Library

<a href="http://www.canvasxpress.org"><img src="http://www.canvasxpress.org/images/brand2.png" align="left" hspace="10" vspace="6" width="100"></a>

***canvasXpress*** was developed as the core visualization component for bioinformatics and systems biology analysis
at Bristol-Myers Squibb. It supports a large number of [visualizations ](http://www.canvasxpress.org/gallery.html)to display scientific and non-scientific
data. ***canvasXpress*** also includes a standalone unobtrusive data table and a filtering widget to allow data
exploration similar to those only seen in other high-end commercial applications as well as an 'out of the box'
broadcasting capability to synchronize selected data points in all ***canvasXpress*** plots in a page. Data can
be easily sorted, grouped, transposed, transformed or clustered dynamically. The fully customizable mouse events
as well as the zooming, panning and drag'n drop capabilities are features that make this library unique in its
class.

***canvasXpress*** can be now simply used within R at the console to generate conventional plots, in R-Studio
or seamlessly embeded in [Shiny](http://shiny.rstudio.com) web applications. An full-fledged example of the ***canvasXpress*** library including the mouse events, zooming, and broadcasting capabilities is included in this package in the [shiny](shiny/example3) directory. This ***canvasXpress*** R library was created with the [htmlwidgets](https://github.com/ramnathv/htmlwidgets) package.

### Getting Started

You can install the latest version of ***canvasXpress*** from GitHub as follows:

```r
devtools::install_github('neuhausi/canvasXpress')
```
### Scatter 3D Plot Example

```r
data <- t(iris[,1:4])
varAnnot <- as.matrix(iris[,5])
colnames(varAnnot) <- "Species"
canvasXpress(t(data), varAnnot=varAnnot, graphType='Scatter3D', colorBy='Species')
```
![Scatter3D](images/R-Scatter3D.png)

### Scatter 2D Plot Example

```r
data <- t(iris[,1:4])
varAnnot <- as.matrix(iris[,5])
colnames(varAnnot) <- "Species"
canvasXpress(t(data), varAnnot=varAnnot, scatterPlotMatrix=1, colorBy='Species')
```
![Scatter2D](images/R-Scatter2D.png)

### Boxplot Example

```r
data <- t(iris[,1:4])
smpAnnot <- as.matrix(iris[,5])
colnames(smpAnnot) <- "Species"
canvasXpress(data, smpAnnot=smpAnnot, graphType='Boxplot', groupingFactors=list('Species'))
# or
canvasXpress(data, smpAnnot=smpAnnot, graphType='Boxplot', afterRender=list(list('groupSamples', list('Species'))))
```
![Boxplot](images/R-Boxplot.png)

### Heatmap Example

```r
data <- t(iris[,1:4])
smpAnnot <- as.matrix(iris[,5])
colnames(smpAnnot) <- "Species"
canvasXpress(data, smpAnnot=smpAnnot, graphType='Heatmap', smpOverlays=list('Species'), variablesClustered=TRUE, showSampleNames=FALSE)
```
![Heatmap](images/R-Heatmap.png)

### Four way Venn Diagram Example

```r
vennData <- data.frame(A=57, B=12, C=67, D=72, AB=4, AC=67, AD=25, BC=67, BD=27, CD=38, ABC=69, ABD=28, ACD=52, BCD=46, ABCD=3)
canvasXpress(vennData=vennData, graphType='Venn', vennGroups=4, vennLegend=list(A="List1", B="List2", C="List3", D="List4"))
```
![Venn](images/R-Venn.png)

Additional information and many examples with the JavaScript ***canvasXpress*** library can be found
[here](http://www.canvasxpress.org).
