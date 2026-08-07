#!/usr/bin/env python
# coding: utf-8

# In[1]:


from selenium import webdriver
from selenium.webdriver.common.by import By
import pandas as pd
import time

driver=webdriver.Chrome()

titles=[]
prices=[]
ratings=[]
for page in range(1,51):
    url=f"https://books.toscrape.com/catalogue/page-{page}.html"
    driver.get(url)
    time.sleep(1)
    books=driver.find_elements(By.CLASS_NAME,"product_pod")
    for book in books:
        h3=book.find_element(By.TAG_NAME,"h3")
        a_tag=h3.find_element(By.TAG_NAME,"a")
        title=a_tag.get_attribute("title")
        price=book.find_element(By.CLASS_NAME,"price_color").text
        rating=book.find_element(By.CLASS_NAME,"star-rating").get_attribute("class")
        titles.append(title)
        prices.append(price)
        ratings.append(rating)

        print("Total Books:",len(titles))

df=pd.DataFrame({"Title":titles,"Price":prices,"Rating":ratings})
df.to_csv("books_pagination.csv",index=False)
driver.quit()


# In[ ]:




