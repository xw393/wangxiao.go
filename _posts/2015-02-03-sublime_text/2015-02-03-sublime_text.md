---
layout: post
title: Sublime Text Packages (持续更新)
categories:

- blog
---

偶然的一次机会，看到朋友用Emacs在酷炫的代码编辑页面中娴熟的使用着各种快捷键写代码的时候，那种感觉真是清爽舒畅，写代码的体验以及工作效率得到了相当大的提高。在朋友的推荐下，自己也兴高采烈的安装了Emacs, 也想体验一下在Emacs中写代码的感觉。但是，当在进行工作环境搭建的时候，以及记忆各种快捷键的时，我深深的鄙视了自己的智商，于是乎毫不犹豫的删除了Emacs。只得到有朝一日，道行更高一些的时候再来使用传说中得神器Emacs了。在找Emacs的替代品的时候，发现了Sublime Text。由于Sublime Text中拥有各种插件可以使用，使得工作效率有了提升，写代码时候的心情也倍感舒畅。因此，在这篇文章中就简单地介绍一下Sublime Text中比较常用的Package以及自己的使用心得。

######下载地址请戳；[Sublime Text](http://www.sublimetext.com)

----
首先需要安装Package Control, 通过Package Control 安装ST的插件
安装方法如下：

######方法一
1. 点击 `Preference/Browse Packages`;
2. 跳转到上一级目录，并进入 `Installed Packages/`;
3. 下载 `Control.sublime-package` 并置于 `Installed Packages/`;
4. 重启 ST.  

######方法二
1. 点击 `View`之后，找到`show console`选项(或者快捷键```Ctrl +	` ```);
2. 在Sublime Text最下方会出现输入命令的窗口，复制如下代码:

对于Sublime Text 3:
{% highlight python %}

import urllib.request,os,hashlib; h = 'eb2297e1a458f27d836c04bb0cbaf282' + 'd0e7a3098092775ccb37ca9d6b2e4b7d'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)

{% endhighlight %}

对于Sublime Text 2:

{% highlight python %}
import urllib2,os,hashlib; h = 'eb2297e1a458f27d836c04bb0cbaf282' + 'd0e7a3098092775ccb37ca9d6b2e4b7d'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); os.makedirs( ipp ) if not os.path.exists(ipp) else None; urllib2.install_opener( urllib2.build_opener( urllib2.ProxyHandler()) ); by = urllib2.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); open( os.path.join( ipp, pf), 'wb' ).write(by) if dh == h else None; print('Error validating download (got %s instead of %s), please try manual install' % (dh, h) if dh != h else 'Please restart Sublime Text to finish installation')
{% endhighlight %}

程序运行之后会自动下载并安装`Package Control`, 运行完成之后关闭Sublime Text 然后重启该软件即可。

至此，在 `Preferences` 下就能看到 `Package Control` 的按钮了，使用`Ctrl + Shift + p (C-S-p for Short)` 调出命令面板，输入 `Package Control:` 即可看到它的全部功能。这一命令面板在你今后的使用中会不断给你带来惊喜。  
（注：一个不错的关于Sublime Text的[BLOG](http://liam0205.me/Sublime-elegant/)）



2> LatexTools 

该插件可以将Latex和Sublime Text 链接起来，直接在ST中编辑代码之后编译即可。

（1）在Windows系统中如果已经安装Ctex，则直接使用Ctex自带的PDF浏览器即可

（2）在MacOS系统中，SKIM是一个非常好的PDF阅读软件，可以通过设置链接到ST



<3>LatexTab

该插件可以节省在Latex中编辑表格的时间。只需要将Excel中的表格复制，然后直接在Sublime Text中黏贴，则会自动生成Latex的表格代码。（非常好用！）









