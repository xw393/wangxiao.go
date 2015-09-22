---
layout: post
title: How to install Python Package
date: 2015-02-08
categories: How-to
tags: [python]
---

> "Life is short, you need Python..."

<hr/>

###pip Method

* First, install `pip`：one can download the tools from [get-pip.py](https://pip.pypa.io/en/latest/installing.html)  

* In the terminal, set the working directory that contains the `get-pip.py` file, and then type the command `python get-pip.py`. Then the tool will be successfully installed.
 
* **Note:** When you are installing the `pip`, there is a warning like `permission denied`, which means you need the administrator's right to install the tool. Don't worry, just typing `sudo python get-pip.py` and providing your password of the computer, then the tool will be install successfully.

**Install python packages**  

{% highlight python %}
pip install Somepackages # Latest Version
pip install Somepackages == 1.0.4 # Some Specific Version  
pip install Some >== 1.0.4 # Minimum Version
{% endhighlight %}


For example:  
`pip install numpy`
<br />

**Update python packages**  
```
pip install -U Package Name
```
<br />

**Remove python packages**    
```
pip uninstall PackageName
```

**References:**  
<1> [How to install and use pip to manage python packages](http://zhonghuan.info/2014/10/01/pip介绍与使用/)







