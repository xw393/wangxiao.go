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


<h2>Examples of ggvis graphics</h2>
</ul>
</nav>
</div>
</div>
<script type="text/javascript">
var plot_id383717576_spec = {
    "data": [
        {
            "name": "faithful0/bin1/stack2",
            "format": {
                "type": "csv",
                "parse": {
                    "xmin_": "number",
                    "xmax_": "number",
                    "stack_upr_": "number",
                    "stack_lwr_": "number"
                }
            },
            "values": "\"xmin_\",\"xmax_\",\"stack_upr_\",\"stack_lwr_\"\n1.5,1.7,3,0\n1.7,1.9,37,0\n1.9,2.1,26,0\n2.1,2.3,16,0\n2.3,2.5,10,0\n2.5,2.7,2,0\n2.7,2.9,3,0\n2.9,3.1,1,0\n3.1,3.3,0,0\n3.3,3.5,8,0\n3.5,3.7,7,0\n3.7,3.9,14,0\n3.9,4.1,25,0\n4.1,4.3,27,0\n4.3,4.5,36,0\n4.5,4.7,31,0\n4.7,4.9,19,0\n4.9,5.1,7,0"
        },
        {
            "name": "scale/x",
            "format": {
                "type": "csv",
                "parse": {
                    "domain": "number"
                }
            },
            "values": "\"domain\"\n1.32\n5.28"
        },
        {
            "name": "scale/y",
            "format": {
                "type": "csv",
                "parse": {
                    "domain": "number"
                }
            },
            "values": "\"domain\"\n0\n38.85"
        }
    ],
    "scales": [
        {
            "name": "x",
            "domain": {
                "data": "scale/x",
                "field": "data.domain"
            },
            "zero": false,
            "nice": false,
            "clamp": false,
            "range": "width"
        },
        {
            "name": "y",
            "domain": {
                "data": "scale/y",
                "field": "data.domain"
            },
            "zero": false,
            "nice": false,
            "clamp": false,
            "range": "height"
        }
    ],
    "marks": [
        {
            "type": "rect",
            "properties": {
                "update": {
                    "stroke": {
                        "value": "#000000"
                    },
                    "fill": {
                        "value": "#ffffdd"
                    },
                    "x": {
                        "scale": "x",
                        "field": "data.xmin_"
                    },
                    "x2": {
                        "scale": "x",
                        "field": "data.xmax_"
                    },
                    "y": {
                        "scale": "y",
                        "field": "data.stack_upr_"
                    },
                    "y2": {
                        "scale": "y",
                        "field": "data.stack_lwr_"
                    }
                },
                "hover": {
                    "fill": {
                        "value": "#eebbbb"
                    }
                },
                "ggvis": {
                    "data": {
                        "value": "faithful0/bin1/stack2"
                    }
                }
            },
            "from": {
                "data": "faithful0/bin1/stack2"
            }
        }
    ],
    "width": 400,
    "height": 150,
    "legends": [

    ],
    "axes": [
        {
            "type": "x",
            "scale": "x",
            "orient": "bottom",
            "title": "eruptions",
            "layer": "back",
            "grid": true
        },
        {
            "type": "y",
            "scale": "y",
            "orient": "left",
            "title": "count",
            "layer": "back",
            "grid": true
        }
    ],
    "padding": null,
    "ggvis_opts": {
        "keep_aspect": false,
        "resizable": true,
        "padding": {

        },
        "duration": 250,
        "renderer": "svg",
        "hover_duration": 0,
        "width": 400,
        "height": 150
    },
    "handlers": null
}
;
ggvis.getPlot("plot_id383717576").parseSpec(plot_id383717576_spec);
</script></p>
<p>Scatterplot with smooth curve and interactive control:</p>
<iframe id="histogram" src="https://winston.shinyapps.io/ggvis-quick-examples-smooth-span/?viewer_pane=1" style="border: none; width: 400px; height: 400px"></iframe>


*Source:* [RStudio](www.rstudio.com)

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

