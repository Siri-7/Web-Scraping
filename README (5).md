
# Webscraping Kaggle API and beautifulsoup

## Authors

- [@Siri-7](https://www.github.com/Siri-7)


## Installation and Code

```bash
#import packages to scrape
from bs4 import BeautifulSoup
import requests
import urllib
import csv
import pandas as pd
import numpy as np
from selenium import webdriver
from kaggle.api.kaggle_api_extended import KaggleApi
api = KaggleApi()
api.authenticate()

#load URLs to scrape data
url = 'https://www.kaggle.com/kaggle/meta-kaggle'
#Ask hosting server to fetch url
requests.get(url)

pages = requests.get(url)
pages.text

soup = BeautifulSoup(pages.text, 'lxml')
soup

table = soup.find('div', {"class": "sc-ckGLlx sc-dEQshG cpEKGC iKdeAv"})
print(table)

#Using webdriver for Chrome

driver = webdriver.Chrome()
driver.get('https://www.kaggle.com/kaggle/meta-kaggle')

html = driver.page_source
soup = BeautifulSoup(html,'lxml')
print(soup.find('span', {'class': 'sc-iJCRrE sc-giAqHp iDwXPD bYgUJS'}))

#Using Kaggle API

competitions = api.competitions_list()
print(competitions)
len(competitions)

api.competitions_list(search='Google Landmark')
```
    