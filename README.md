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
