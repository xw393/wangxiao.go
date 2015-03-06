---
layout: post
title: Useful R Packages
categories:
- blog
---

#### Software  
[**Revolution R Open**](http://mran.revolutionanalytics.com/documents/rro/installation/#sysreq): High-performance version of R.  
[**RStudio**](http://www.rstudio.com/products/rstudio/): extremely wonderful IDE of R.


#### Packages

(1) **[devtools](https://github.com/hadley/devtools)**: help to install packages hosted on the github.   
{% highlight python %}  
devtools::install_github(c("ramnathv/htmlwidgets", "rstudio/dygraphs"))  
{% endhighlight %}

(2) **[pipeR](http://renkun.me/pipeR/)**: provides various styles of function chaining methods. Designed to make pipeline more readable and friendly to a wide variety of operations. 

It is natural to perform bootstrap and plot its density function as follows. However, the code is deeply nested and very hard to read. With package **pipeR**, the code can be rewritten in a more human readable ways.

  
{% highlight python %}  
plot(density(sample(rnorm(10),size = 100, replace = TRUE),kernel = "gaussian"),
     type = "l", main = "density of a sample (bootstrap)",col = "red")
{% endhighlight %}   

- Operator-based pipeline (`%>>%`).  
{% highlight python %}  
data <- rnorm(10) %>>%
  sample(size = 100, replace = TRUE) %>>%
  density(kernel = "gaussian") %>>%
  plot(type = "l",main = "density of a sample (bootstrap)", col = "red")
{% endhighlight %} 

- Objected-based pipeline function (`Pipe()`)
{% highlight python %}    
data <- rnorm(10)
Pipe(data)$
  sample(size = 100, replace = TRUE)$
  density(kernel = "gaussian")$
  plot(type = "l",main = "density of a sample (bootstrap)", col = "red")
{% endhighlight %} 

All these three pieces of codes all do exactly the same thing. For more detailed description of the powerful package, people can reference [ken's blog.](http://renkun.me/pipeR/) 


#### Data Visualization:
(1) **[dygraphs](http://rstudio.github.io/dygraphs/)**: Javascript-based plot tools, elegant and powerful.   

{% highlight python %}  
install.packages("dygraphs")  
devtools::install_github(c("ramnathv/htmlwidgets", "rstudio/dygraphs"))  
{% endhighlight %}

(2) **[ggvis](http://ggvis.rstudio.com)**  
gigs is a data visualization package for R which lets you:  
- Declarativly describe data graphics with a syntax similar in spirit to ggplot2.  
- Create rich interactive graphics that you can play with locally in RStuido. [1]

*Source:* [RStudio](www.rstudio.com)  
*[1]*[Detailed descriptions and examples](http://ggvis.rstudio.com)


(3) **[DiagrammeR](http://rich-iannone.github.io/DiagrammeR/docs.html)**  
Note: [DiagrammeR Tutorial](https://github.com/rich-iannone/DiagrammeR)
  
{% highlight python %}  
devtools::install_github('rich-iannone/DiagrammeR')
install.packages('DiagrammeR') 
{% endhighlight %}
  
(4) **ggplot2**:


#### Statistics 
**tseries**: packages for time series analysis.

#### Quantitative Finance  
**quantmod**  

#### HTML Tools

**htmltools**  
**rvest**

