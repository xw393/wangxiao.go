---
layout: post
title: Output Chinese words with Latex on Mac(Template)
date: 2015-02-03
categories: how-to
tags: [tex, Mac]
---

Latex is a powerful tools to create beautiful documents. Especially for creating files that contain a lot of mathematical symbols. When working on latex file on Mac, some problems will occur when one want to output files with chinese words. In order to display chinese words in Latex file, you can use the following template:

{% highlight latex %}
% !TEX encoding = System
% !TEX program = xelatex
\documentclass[12pt,a4paper]{article}
\usepackage{amsmath}
\usepackage{latexsym,amsfonts,amssymb}
\usepackage{cases}
\usepackage{graphicx}
\usepackage{amsmath,amsthm,amssymb}
\usepackage{pstricks}
\usepackage{delarray}
\usepackage{tabularx}
\usepackage{mathrsfs}
\usepackage{amsbsy}
\usepackage{setspace}
%\usepackage{CJK}
\usepackage{fancyhdr}

%==========================
%\usepackage{xeCJK}
%\setCJKmainfont{SimSun}
%Setting fonts of Chinese
%==========================
\topmargin=-1.5cm %设置距顶距离
\renewcommand{\baselinestretch}{1.5} %设置行距
\oddsidemargin=0truecm 
\evensidemargin=0truecm
\parindent=2em
\textwidth=165mm \textheight=230mm

%设置页边距等参数
%================specfont package==========
\usepackage{fontspec}
\setromanfont[Mapping=tex-text, %
Ligatures={Required,Common}, %
ItalicFont={Times Italic}, %
BoldFont={Apple LiGothic Medium}]%
{SimSun}
% 預設字形：這裡設內文為標楷，
% 沿用 latex 的一些標點的轉換，如 en-dash 以兩個減號表示，
% 如果此字型檔裡有 ligatures 的定義，則啟動
% 斜體字以 Times Iatlic (只有英文有斜體)
% 粗體字以黑體字表現
% 此為 fontspec 套件的指令

%%%%%%%%%===================================

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
\newcommand{\Hom}{\mbox{Hom}}
\newcommand{\End}{\mbox{End}}
\newcommand{\Ext}{\mbox{Ext}}
\newcommand{\rad}{\mbox{rad}}
\newcommand{\Mod}{\mbox{Mod}}
%\newcommand{\hei}{CJKfamily{SimHei}}
\newcommand{\moa}{\mbox{mod}{A}}
%\def\Z{\mathbb Z}
\newcommand{\Z}{{\bf Z}}
\newcommand{\C}{{\bf C}}
\newcommand{\Q}{{\bf Q}}
\newcommand{\N}{{\bf N}}
%\newcommand{\g}{{\mathfrak{g}}}
\newcommand{\g}{\bf{g}}
\newcommand{\n}{\bf{n}}
\newcommand{\h}{\bf{h}}
\newcommand{\al}{\alpha}
\newcommand{\be}{\beta}
\newcommand{\ga}{\gamma}
\newcommand{\si}{\sigma_i}
\newcommand{\sip}{\sigma_i^+}
\newcommand{\de}{\Delta}

\usepackage[linewidth=2pt]{mdframed} % 加载边框宏包

\begin{document}
$$p=\frac{I}{Q_{0}+Q}$$
$$\sip$$

\begin{equation*}
\frac{dS_{t}}{S_{t}}  = \mu dt + \sigma dW_{t}
\end{equation*}
\begin{equation*}
c(t) = S_{t}N(d_{1}) - e^{-r(T-t)}N(d_{2})
\end{equation*}
\begin{equation*}
d_{1} = \frac{ln(S/K)+ \dfrac{1}{2}\sigma^{2}(T-t)}{\sigma\sqrt{T-t}}\\
\end{equation*}

测试一下,终于都是宋体了。\\
{\fontspec{Kai} 测试一下specfont软件包}\\
{\fontspec{Times New Roman} Hello~ Latex }\\
{\fontspec{Courier} Hello~ Latex }\\
{\fontspec{Georgia} Hello~ Latex }\\

\begin{center}
\begin{tabular}{llll}
\hline
4.61 & 3.80 & 5.06 & 4.43 \\
2.15 & 2.21 & 3.03 & 2.08 \\
2.19 & 1.99 & 2.54 & 2.37 \\
1.82 & 1.79 & 1.79 & 1.95 \\
2.85 & 2.77 & 2.77 & 3.51 \\
2.35 & 2.97 & 2.97 & 3.85 \\
\hline
\end{tabular}
\end{center}

\end{document}

{% endhighlight %}
