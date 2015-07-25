---
layout: post
title: Python Package的安装方法
date: 2015-07-21
categories: How-to
tags: [python]
---

> "Life is short, you need Python..."

<hr/>

###pip 方式

* 先进行pip工具的安装：首先下载 [get-pip.py](https://pip.pypa.io/en/latest/installing.html)  

* 然后在命令提示行中将工作目录设置在包含get-pip.py的文件夹，输入如下命令安装：`python get-pip.py`
 
* **注意:** 如果在安装或者使用 `pip`等命令时出现“permission denied”提示，则表明需要管理员权限，只需要在命令提示行中输入:  `sudo python get-pip.py`  
(即在命令前加`sudo`,根据提示输入管理员密码之后则可成功安装所需要的文件。)  

**安装 python packages**  

{% highlight python %}
pip install Somepackages # Latest Version
pip install Somepackages == 1.0.4 # Some Specific Version  
pip install Some >== 1.0.4 # Minimum Version
{% endhighlight %}


例如:  
`pip install numpy`
<br />

**更新 python packages**  
```
pip install -U Package Name
```
<br />

**移除 python packages**    
```
pip uninstall PackageName
```

**References:**  
<1> [How to install and use pip to manage python packages](http://zhonghuan.info/2014/10/01/pip介绍与使用/)







