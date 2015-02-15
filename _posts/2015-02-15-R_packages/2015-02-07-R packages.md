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


(2) **[pipeR](http://renkun.me/pipeR/)**: provides various styles of function chaining methods. Designed to make pipeline more readable and friendly to a wide variety of operations.
**rlist**  



#### Data Visualization:
(1) **[dygraphs](http://rstudio.github.io/dygraphs/)**: Javascript-based plot tools, elegant and powerful.   

{% highlight R %}  
install.packages("dygraphs")  
devtools::install_github(c("ramnathv/htmlwidgets", "rstudio/dygraphs"))  
{% endhighlight %}

(2) **[ggvis](http://ggvis.rstudio.com)**  
gigs is a data visualization package for R which lets you:  
- Declarativly describe data graphics with a syntax similar in spirit to ggplot2.  
- Create rich interactive graphics that you can play with locally in RStuido. [1]

[1]- [Detailed descriptions and examples](http://ggvis.rstudio.com)

(3) **[DiagrammeR](http://rich-iannone.github.io/DiagrammeR/docs.html)**  
Note: [DiagrammeR Tutorial](https://github.com/rich-iannone/DiagrammeR)
  
{% highlight R %}  
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

