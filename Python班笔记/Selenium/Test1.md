### Test1

```python
from selenium import webdriver

url = "https://movie.douban.com/"
driver = webdriver.Chrome()
driver.get(url)
# driver.find_element_by_id('inp-query').send_keys('红海行动')
driver.find_element_by_name('search_text').send_keys('我不是药神')
# 选出第一个class名为nav-items的标签
class_name = driver.find_element_by_class_name('nav-items').text
print("由class_name定位:", class_name)
# 选出第一个名为div的标签
tag_name = driver.find_element_by_tag_name('div').text
print("由tag_name定位:", tag_name)
link_text = driver.find_element_by_link_text('排行榜').text
print("由link_text定位:", link_text)
partial_text = driver.find_element_by_partial_link_text('部正在热映').text
print("由partial_text定位:", partial_text)
xpath = driver.find_element_by_xpath('//*[@id="db-nav-movie"]/div[1]/div/div[1]/a').text
print("由xpath定位:", xpath)
selector = driver.find_element_by_css_selector("#db-nav-movie > div.nav-wrap > div > div.nav-logo > a").text
print("由selector定位:", selector)
```