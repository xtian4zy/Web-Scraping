# Implementing Web-Scraping Using Python - Lab

## Introduction

In this lab you'll carry out pratical implementation of web scraping using the Python programming language. You will install and import (load) the required libraries for web scraping and then scrape data from a wikipedia website. Finally, you will convert the scraped data from raw html table into pandas dataframe that can now be used easily for any further analysis. Let's get started!

## Objectives

You will be able to:

- Gather data from online sources using web scraping.
- Make practical application of Python libraries used for web scraping.
- Extract data from a given format (raw html) into a destired format (dataframe).
- Export the extracted data for further use.

## What is Web Scraping?

The task of extracting data from websites is called web scraping. It is one of the most popular methods of collecting data from the internet for websites that do not provide APIs to collect their data.

## Data to Scrape

For this lab, we'll scrape data from wikipedia, which contains a list of Nigerian cities by population. The data is available on wikipedia url https://en.wikipedia.org/wiki/List_of_Nigerian_cities_by_population. Let's get started.

## Project Process

- Task 1: Install packages and libraries.
- Task 2: Import libraries.
- Task 3: Request for the HTML response using the URL.
- Task 4: Inspect page.
- Task 5: Parse data from the HTML.
- Task 6: Convert Wikipedia Table into a Python Dataframe.
- Task 7: Export extracted data.

## Install packages and libraries:
To perform web scraping using Python, there are several packages and libraries that are useful. We will install these libraries (if not currently installed).

```Python
#Go to the terminal and use this pip command to install BeautifulSoup
pip install beautifulsoup4 
```

## Import Libraries
```
import pandas as pd # library used for data analysis (but will be used to extract raw data into a dataframe)
import requests # library used to handle requests from the website.
from bs4 import BeautifulSoup # library used to parse HTML documents
```
## Request for the HTML response using the URL
We will send a GET request to the Wikipedia URL whose table we want to scrape and store the HTML response in a variable. To be sure we can legally scrape the website, so check for the status code. A 200 status code shows that we can go ahead and scrape the webpage.
```
## get the response in the form of html
scraping_url="https://en.wikipedia.org/wiki/List_of_Nigerian_cities_by_population"
table_class="wikitable sortable jquery-tablesorter"
response=requests.get(scraping_url)
print(response.status_code)
```

## Inspect page
To scrape the right data from our target webpage, we need to inspect the webpage in order to identify where the required data is located. To do this, place your cursor on the data (while on the webpage) ,right click and select Inspect. This gives the HTML content through which we can find the tags inside which our data is stored. 


![This is an image](https://github.com/xtian4zy/Web-Scraping/blob/main/inspect%20nigeria%20cities.png)

## Parse data from the HTML
Good job so far. Next we will create a BeautifulSoup object and use the find() method to extract the relevant information from the webpage which is resident in the table tag. Because wikipedia pages can have multiple tables, we need to specify the particular table we want to scrape by passing the “class” or the “id” attribute of the target table tag.

```
# parse data from the html into a beautifulsoup object
soup = BeautifulSoup(response.text, 'html.parser')
data_to_get=soup.find('table',{'class':"scraping_url"})
data_to_get
```

## Convert Wikipedia Table into a Python Dataframe
```
df=pd.read_html(str(data_to_get))
# convert list to dataframe
df=pd.DataFrame(df[0])
df.head()
```

## Export Dataframe

```
#Export the extracted data as csv file for future analysis

df.to_csv('list_of_nigeria_cities.csv')
```
## Summary
In this lab, we implemented basic web scraping using the BeautifulSoap library in Python. We scraped the list of Nigerian cities from wikipedia and converted the raw HTML data into a pandas dataframe that was exported for any future use. While this lab covers scraping data from a single webpage, subsequent lab will cover how to scrape data from multiple pages of the same website.

Thanks for going through this work. For comment and contribution (including collaboration opportunities) reach me via [Twitter](https://twitter.com/xtian4zy) or on [Linkedin](https://www.linkedin.com/in/idemudiachristianuwa/).
