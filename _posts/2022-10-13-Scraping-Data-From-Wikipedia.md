---
layout: post
title:  "Scraping Data From Wikipedia"
date:   2022-10-18
author: Zayne Kirkham
description: A simple Wikipedia scraping tutorial
image: /assets/images/wikipedia-logo-D8F03B93A7-seeklogo.com.jpg
---

# Introduction
One of the most dificult parts of statistical analysis is gathering data. While the best way to get data is to produce it yourself, this is not always practical, nor possible. Such is the case when studying historical events. This data must be obtained from a source. I, for one, have always had a fascination with the two World Wars. They were springboards for invention and innovation. They inspired millions of men into great acts of courage ans sacrifice. Unfortunately, they were also causes of much devastation and pain. There are few places in world that did not feel their effects. 

One of the best ways to investigate this effect is to examine the loss of life for each nation involved. Luckily, Wikipedia has compiled data sets for the casualty count for both [World War One]("https://en.wikipedia.org/wiki/World_War_II_casualties") and [World War Two]("https://en.wikipedia.org/wiki/World_War_I_casualties").

# Method
The simplest way to gather data from the internet is to use an API. While Wikipedia does have an API, I could not find an easy way to gather information from tables using it. Fortunately, gathering data from Wikipedia tables is a breeze with Python's [Pandas](https://pypi.org/project/pandas/) and [BeautifulSoup](https://pypi.org/project/beautifulsoup4/) modules. 

Beautifulsoup is the quintessential tool in python used to scrape web data. However, it can be difficult and confusing to use. Luckily, pandas has a function that is a wrapper for using beautifulsoup to scrape tables. 

## An aside on ethics
While it is [legal to web scrape publically available data](https://techcrunch.com/2022/04/18/web-scraping-legal-court/#:~:text=In%20its%20second%20ruling%20on,computer%20hacking%20under%20U.S.%20law.), it is not always ethical to do so. Many companpanies have made public requests to not scrape data from sites. In many cases, collecting and using this data undermind how these companies are able to remain profitable. It is still legal to do scrape their data, but it is wrong to undermine their business and endanger their jobs. As a general rule of thumb, if a company's terms of service or [robots.txt](https://www.cloudflare.com/learning/bots/what-is-robots.txt/) disallow scraping, it is best to avoid scraping their data. 

Fortunately for us, Wikipedia all but encourages people to scrape data and use it for themselves. 

## How to
First, install the necessary modules using the following command line arguments.
``` 
pip install pandas
pip intall beautifulsoup4
```
Once installed, the pandas.read_html() function retrieves all of the table data from a specified url and stores the data in a list of tables.  
``` python
# Get links
ww2_url= "https://en.wikipedia.org/wiki/World_War_II_casualties"
ww1_url= "https://en.wikipedia.org/wiki/World_War_I_casualties"

#Read tables and select specified one
ww2_df = pd.read_html(ww2_url)[0]
ww1_df = pd.read_html(ww1_url)[0]
ww1_df.columns = ww1_df.columns.droplevel(1)  #remove multi-index layer
```
After a little cleaning after merging the tables, we are left with a data set similar to the following:

![FIGURE](https://raw.githubusercontent.com/zayne-kirkham/stat386-projects/main/assets/images/raw_messy_WW_data.png)

You can find the full table at this [link](https://github.com/zayne-kirkham/World-War-Casualties/blob/main/Uncleaned_data.csv). As you can see, this data requires a bit more cleaning in order to be usable for statistical analysis. Beautifulsoup and pandas scrape the data, but it is up to the user to clean it. 

# Conclusion
I hope that this helps you in your web scraping adventures, and I encourage you to explore more with scraping Wikipedia. Who knows, maybe one of you will figure out how to use the Wikipedia API to get table data! If you do, please reach out and let me know how. ;) 

In the next few posts, I will be taking this data through the cleaning process and analyzing it. By studying the past, we can learn much more about ourselves and our future. Stay tuned through this blog or through [this repository!](https://github.com/zayne-kirkham/World-War-Casualties)

