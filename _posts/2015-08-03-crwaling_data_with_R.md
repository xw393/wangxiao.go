---
layout: post
title: Crwaling and Storing Data with R and MySQL
date: 2015-08-15
categories: how-to
tags: [crawling data, R, MySQL]
---

In this article, I am going to talk about how to crawl data from Internet with R, and then store the data into MySQL database.

When someone conducts quantitative analysis on financial markets, data is an imperative element. Beside using Bloomberg, DataStream or some other tools to get data, we can also crawl data from various website, especially when the data you need are displayed on different pages, e.g, daily closed prices of stocks contained in the **S&P 500** from 2001-01-01 to 2015-08-01, which are often displayed on multi pages. Stock prices can be easily found on the [Yahoo Finance](http://finance.yahoo.com). However, if downloading data from stock to stock, one needs to open more 500 pages and copy these data repetitively. If this work is finished manually, it will be very time-consuming. Therefore, crawling technique can be very efficient.

Taking crawling trading information of stocks contained in the **S&P 500** as the example:


{% highlight r%}
library(rvest)
library(pipeR)
library(sqldf)

html <- html('https://en.wikipedia.org/wiki/List_of_S%26P_500_companies')

title = html_nodes(html,xpath = '//table/tr[1]/th')
title_text = html_text(title)[1:7]
title_text
# 
# [1] "Ticker symbol"           "Security"               
# [3] "SEC filings"             "GICS Sector"            
# [5] "GICS Sub Industry"       "Address of Headquarters"
# [7] "Date first added" 
# 

# Calculate the number of stocks contained in S&P 500
number = length(html_nodes(html,xpath = '//table[1]/tr/td[1]'))
sp500_stocks = data.frame(number = c(1:number))

# extract info from the table in wiki website.
sp500_stocks['Ticker_Symbol'] = html_nodes(html,xpath = '//table[1]/tr/td[1]') %>>%
  html_text()

sp500_stocks[,'Security'] = html_nodes(html,xpath = '//table[1]/tr/td[2]') %>>%
  html_text()

sp500_stocks['SEC_filings'] = html_nodes(html,xpath = '//table[1]/tr/td[3]') %>>%
  html_text()

sp500_stocks['GICS_Sector'] = html_nodes(html,xpath = '//table[1]/tr/td[4]') %>>%
  html_text()

sp500_stocks['GICS_Sub_Industry'] = html_nodes(html,xpath = '//table[1]/tr/td[5]') %>>%
  html_text()
  
sp500_stocks['Address_of_Headquarters'] = html_nodes(html,xpath = '//table[1]/tr/td[6]') %>>%
  html_text()

sql = "SELECT * FROM sp500_stocks
ORDER BY Ticker_Symbol"

sp500_stocks = sqldf(sql)

{% endhighlight %}

Since we have already get all the symbols of stocks listed in S\&P500 index, the next step is to find the data we need on the Internet and parse the websites then crawling all the information we need. Taking crawling stock price data from Yahoo Finance as exmaple:

{% highlight r %}
setwd("~/Desktop/Data")

library(rvest)
library(stringr)
library(pipeR)
library(data.table)


sp500_stocks <- read.csv('sp500_stock_list.csv')
stockList <- sp500_stocks[,3:4]

# Create a data frame to hold all the stock data.
allStockData <- data.frame(Date = 0, Open = 0,
                           High = 0, Low = 0,
                           Close = 0, Volume = 0,
                           Adj_Close = 0, Symbol = 'a',
                           Security = 'a')

for(i in 1:length(stockList[,1])){
  
  html <- sprintf("http://real-chart.finance.yahoo.com/table.csv?s=%s&a=00&b=2&c=1962&d=06&e=23&f=2015&g=d&ignore=.csv",stockList[i,1])
  stockData <- html(html) %>>%
    html_node(xpath = "//p") %>%
    html_text() %>%
    strsplit("\n") %>%
    unlist()
  
  # Create a data frame to store the data.
  n = length(stockData)
  temp_df <- data.frame(Date = rep(0,n), Open = rep(0,n),
                        High = rep(0,n), Low = rep(0,n),
                        Close = rep(0,n), Volume = rep(0,n),
                        Adj_Close = rep(0,n))
  for (j in 2:n){
    temp_df[j,] = unlist(strsplit(stockData[j],','))
    #     temp_df[i,1] = unlist(strsplit(temp[i],','))[1]
    #     temp_df[i,2] = unlist(strsplit(temp[i],','))[7]
  }
  temp_df = temp_df[-1,]
  temp_df['Symbol'] = stockList[i,1]  # First column is symbol
  temp_df['Security'] = stockList[i,2] # Second column is security name
  
  allStockData = rbind(temp_df, allStockData)
}


write.csv(allStockData, file = 'SP500_All_Stock_Data.csv')

{% endhighlight %}


After crawling all the data required, one can try to connect database with R. `RMySQL` is a powerful package that can connect R with database and manipulate data directly in R. Followings are some basic instructions of using MySQL in R. 

{% highlight r %}

library(RMySQL)
library(pipeR)

conn <- dbConnect(MySQL(),
                  dbname = "stockdb",
                  username = "stockdata",
                  password = "testpassword")

# write data frame into database.
dbWriteTable(conn, 'sp500_stockdata', allStockData, row.names=F, append=F, overwrite = T)

sql2 <-"SELECT * FROM stockdb.sp500_stockdata
WHERE symbol = 'AAPL'
limit 50"

# execute a simple query statement. And all the fetched data are stored as a data frame.
queryTable2 <- dbSendQuery(conn, sql2) %>>%
  dbFetch()

queryTable


dbListTables(conn)
dbSendQuery(conn, 'drop table sp500_stockdata2;')
dbDisconnect(conn)

dbClearResult()

{% endhighlight %}