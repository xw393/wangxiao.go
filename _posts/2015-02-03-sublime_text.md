---
layout: post
title: Sublime Text Packages
date: 2015-02-06
categories: how-to
tags: [sublime text, packages]
---

[Sublime Text](http://www.sublimetext.com) is a sphisicated text editor for codes which is availabe for OS X, Windows and Linux. Its user interface is very simple and gorgeous. You'll love the extraordinary features and fantasitic performance of this text editor. One can really improve their work efficiency with this tool. 

######You can download at；[Sublime Text](http://www.sublimetext.com)

----
First of all, one need to install `Package Control` package, and utilizing this package to install other plugins for Sublime Text.

The installation methods are as follow:

######方法一
1. Click `Preference/Browse Packages`;
2. Go back to parent directory and enter in the folder `Installed Packages/`;
3. Download `Control.sublime-package` and unarchived the files into `Installed Packages/`;
4. Reopen Sublime Text.  

######Method 2
1. Click `View`, and find `show console` option (or shortcut```Ctrl +	` ```);
2. Under the bottom of `Sublime Text` there will be a box that you can type codes in it, and then input the codes as follows:
 
For Sublime Text 3:
{% highlight python %}

import urllib.request,os,hashlib; h = 'eb2297e1a458f27d836c04bb0cbaf282' + 'd0e7a3098092775ccb37ca9d6b2e4b7d'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)

{% endhighlight %}

For Sublime Text 2:

{% highlight python %}
import urllib2,os,hashlib; h = 'eb2297e1a458f27d836c04bb0cbaf282' + 'd0e7a3098092775ccb37ca9d6b2e4b7d'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); os.makedirs( ipp ) if not os.path.exists(ipp) else None; urllib2.install_opener( urllib2.build_opener( urllib2.ProxyHandler()) ); by = urllib2.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); open( os.path.join( ipp, pf), 'wb' ).write(by) if dh == h else None; print('Error validating download (got %s instead of %s), please try manual install' % (dh, h) if dh != h else 'Please restart Sublime Text to finish installation')
{% endhighlight %}

This code will automatically download and install `package control`. After installation, reopen the Sublime Text, then the package is installed successfully.

So far, under the `Preference` option, one can see the button of `Package Control`, then using `Ctrl + Shift + p` to open `Command Palette`, typing `package control`, and you can see all the functions this package has. The `Command Palette` will bring a lot surprises if you use it frequently.

_(Note：a very nice [BLOG](http://liam0205.me/Sublime-elegant/) about `Sublime Text`)_



2> LatexTools 

This plugin can connect Latex with Sublime Text, and one can directly compile latex files in the Sublime Text, which can be really efficient.

（1）If your operating system is Windows and have already installed CTex on your computer, the PDF browser in CTex can be directly used as the default viewer.

（2）For MacOS X, one can use SKIM for viewing the PDF files you have written with Latex. After some basic setttings in the SKIM, you can connect Sublime Text with SKIM.


<3>LatexTab

This plugin can help people save a lot time when insert tables into Latex files. One can just copy the tables in the Excel and copy into the Latex file, then this plugin will automatically create the table codes for you. It is really awesome.








