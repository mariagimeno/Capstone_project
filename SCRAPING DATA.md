

# SCRAPING DATA

It was the first process of the project. The data was scraping on this website: https://www.winemag.com/?s=&drink_type=wine&page=1

```python
import numpy as np
import pandas as pd
import requests
import bs4
from bs4 import BeautifulSoup
from tqdm import tqdm_notebook
import re
import time
from fake_useragent import UserAgent 
```
Scrap the url of all the wines and create a list with them: url_1000

```python
ua=UserAgent()
url_1000 = []
for page in tqdm_notebook(range(1, 1000)):
    url = 'https://www.winemag.com/?s=&drink_type=wine&page={}'.format(page)
    r = requests.get(url, headers={"User-Agent" : ua.random})
    soup = BeautifulSoup(r.text, 'html.parser')
try:
    for i in soup.find_all('a', attrs={'class':"review-listing row"}):
        url_10.append(i["href"])
except:
    None
```

Loop through this list to get the informacion from each of the pages. 

```python
ua=UserAgent()
title = []
description = []
points = []
taster = []
variety = []
location = []
country = []

for x in url_1000:
    url = x
    r = requests.get(url, headers={"User-Agent" : ua.random})
    soup = BeautifulSoup(r.text, 'html.parser') 
    
    for i in soup.find_all('section', attrs={'id':"review"}):
        try:
            title.append(i.find('div',attrs={'class':'article-title'}).text.strip())
        except:
            title.append(np.nan)
    for i in soup.find_all('section', attrs={'id':"review"}):
        try:
            description.append(i.find("p",attrs={'class':'description'}).text.strip())
        except:
            None
    for i in soup.find_all('section', attrs={'id':"review"}):    
        try:
            taster.append(i.find("span",attrs={'class':'taster-area'}).text.strip())
        except:
            None
    for i in soup.find_all('section', attrs={'id':"review"}):   
        try:
            points.append(i.find("span",attrs={'class':'rating'}).text.strip())
        except:
            None

    try: 
        wine_variety = []
        for i in soup.find('ul', {'class': 'primary-info'}).find_all('li', {'class': 'row'}):
            try:
                y = i.find('div', {'class': 'info'}).span.findChildren()[0].contents[0]
                wine_variety.append(y.strip())
            except:
                None
        if len(wine_variety) == 3:
            wine_variety.insert(1,np.nan)
        variety.extend(wine_variety)
        
    except:
        pass
    
    try:
        wine_location = []
        for i in soup.find('ul', {'class': 'primary-info'}).find_all('li', {'class': 'row'}):
            try:
                y = i.find('div', {'class': 'info'}).span.findChildren()[1].contents[0]
                wine_location.append(y.strip())
            except:
                None
        if len(wine_location) == 3:
            wine_location.insert(2,np.nan)
        location.extend(wine_location)
        
    except:
        pass
    
    try:
        temp = []
        for i in soup.find('ul', {'class': 'primary-info'}).find_all('li', {'class': 'row'}):
            try:
                y = i.find('div', {'class': 'info'}).span.findChildren()[2].contents[0]
                temp.append(y.strip())
            except:
                pass
        if len(temp) == 0:
            temp.append(np.nan)
        
        country.extend(temp)
    except:
        pass

    
```
DataFrame with all the features and their values. 

```python
df_1000 = pd.DataFrame({'country': country, 
                        'description':description, 
                        'designation':variety[1:len(variety):4], 
                        'points':points, 
                        'price':variety[0:len(variety):4], 
                        'province':variety[3:len(variety):4], 
                        'region_1':location[1:len(location):4], 
                        'region_2':location[2:len(location):4], 
                        'taster_name':taster,
                        'taster_twitter_handle':None, 
                        'title': title, 
                        'variety':variety[2:len(variety):4],
                        'winery': location[3:len(location):4]})
```



This is an Image: !![image-20200102172858310](/Users/Mariagimenoperez/Library/Application Support/typora-user-images/image-20200102172858310.png)





csv file with all of the data

```python
df_1000.to_csv('wine1000.csv', index=False)
```
