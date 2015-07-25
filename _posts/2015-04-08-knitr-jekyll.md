---
layout: post
title: Blog with Knitr and Jekyll
date: 2015-04-08
categories: how-to
tags: [knitr, R, Jekyll]
---

### Step
Open the R Console and process the source file:

{% highlight python %}
KnitPost <- function(input, base.url = "/") {
  require(knitr)
  opts_knit$set(base.url = base.url)
  fig.path <- paste0("figs/", sub(".Rmd$", "", basename(input)), "/")
  opts_chunk$set(fig.path = fig.path)
  opts_chunk$set(fig.cap = "center")
  render_jekyll()
  knit(input, envir = parent.frame())
}
KnitPost("2012-07-03-knitr-jekyll.Rmd")
{% endhighlight %}


###Implement MathJax in Jekyll.
When using Jekyll to create the blog, sometimes we need to type mathematical formula in the articles. MathJax is a powerful tool to display beautiful formulas on the website. To load the MathJax javascript, we can add the following lines in the `post.html`, which is located in the folder `_layouts`.

### A Couple of Examples
If you are familiar with **LaTex**, the behavior of **MathJax** is very similar with **LaTex**, but not all the same.

To display in-line math, `\\( ...\\)` can achieve this goal:

If one want to display \\( sin(x)\\), just use the code `\\(sin(x)\\)`.

`\\[...\\]` and  `$$ .. $$` can be used for displaying equations, such as:

    \\[ \mathbf{X} = \mathbf{Z} \mathbf{P^\mathsf{T}} \\]

\\[ \mathbf{X} = \mathbf{Z} \mathbf{P^\mathsf{T}} \\]

Or, one can also use LaTex delimiters **Double Dollar** signs

    $$ \mathbf{X_{n,p}} = \mathbf{A_{n,k}} \mathbf{B_{k,p}}$$

which we can get formula like:

$$ \mathbf{X_{n,p}} = \mathbf{A_{n,k}} \mathbf{B_{k,p}}$$

However, the LaTex delimiter `$ .. $` is not defined in this case, so one can not use code like `$ \mathbf{X_{t}} $` to get formula \\(\mathbf{X_{t}}\\).
