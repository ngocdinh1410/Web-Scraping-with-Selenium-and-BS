# Web-Scraping-with-Selenium-and-BS-Amazon
I hope to scrape some data off Amazon with Selenium and BeautifulSoup


[**Full code file for review page**](https://github.com/ngocdinh1410/Web-Scraping-with-Selenium-and-BS/blob/master/Amazon_Alexa_Comments_Selenium_05012020%20.ipynb)


[**Full code file for general page**](https://github.com/ngocdinh1410/Web-Scraping-with-Selenium-and-BS/blob/master/Amazon_Skills_Comment_03192020.ipynb)

The amazon alexa page consisted of the general page:

![alt text](https://github.com/ngocdinh1410/Web-Scraping-with-Selenium-and-BS/blob/master/Skills_General.PNG "General Page")


The amazon alexa page also consisted of a page that has only reviews:


![alt text](https://github.com/ngocdinh1410/Web-Scraping-with-Selenium-and-BS/blob/master/Skills_Comment.PNG "Skill Comments Page")


**To scrape data, we need to import the following:**


```
import urllib.request, urllib.parse, urllib.error
from bs4 import BeautifulSoup
import re
import ssl
import pdb
import requests
import time
from random import randint
import csv
```

To scrape the comments page, I opted to use selenium to automate the process:

```
from selenium import webdriver
import time
from bs4 import BeautifulSoup
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from selenium.common.exceptions import TimeoutException
import csv
import pandas as pd
MAX_PAGE_NUM=3
with open('amazon_selenium.csv','w') as f:
    f.write("username,title,date,comment,skillname,totalrating,avgrating\n")
for i in range(1,MAX_PAGE_NUM+1):
    page_num=i
    print(page_num)
    url='https://www.amazon.com/Voxion-Mutter-Nonsense/product-reviews/B086Q3LWW7/ref=cm_cr_getr_d_paging_btm_prev_1?ie=UTF8&reviewerType=all_reviews&pageNumber='+str(page_num)
    browser = webdriver.Chrome("/Users/baongocdinh/downloads/chromedriver" )
    browser.get(url)
    time.sleep(10)
    html=browser.page_source
    soup=BeautifulSoup(html, 'html.parser')
    reviews=soup.find_all("div",{"data-hook":"review"})
    data=[]
 ```
