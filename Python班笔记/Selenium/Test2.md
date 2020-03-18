### Test2

```python
from selenium import webdriver
url = "https://ssl.zc.qq.com/v3/index-chs.html?from-pt"
driver = webdriver.Chrome()
driver.get(url)
driver.find_element_by_id('nickname').send_keys('myqqmusic_name')
driver.find_element_by_id('password').send_keys('myqqmusic_pw')
tips_value = driver.find_element_by_xpath('/html/body/div[3]/div[2]/div[1]/form/div[5]/div').text
print(tips_value)
driver.find_element_by_class_name('checkbox').click()
driver.find_element_by_id('get_acc').submit()

"""
#清空X标签的内容
driver.find_element_by_id('X').clear()
#获取元素在网页中的坐标位置，坐标格式：{'y': 19, 'x’： 498}
location = driver.find_element_by_id('X').location
#获取元素的某个属性值，如获取x标签的id属性值
attribute = driver.find_element_by_id('X').get_attribute('id')
#判断X元素在网页上是否可见，返回值士 True或False
result = driver.find_element_by_id('X').is_displayed()
#判断X兀素是否被选，通常用于checkbox和radio标签，返回值为True或False
result = driver.find_element_by_id ('X').is_selected ()
#select标签的选值
from selenium.webdriver.support.select import Select
#根据下拉框的索引来选取
Select(driver.find_element_by_id('X')).select_by_index(121)
#根据下拉框的value属性来选取
Select(driver.find_element_by_id('X')).select一by_index('Python')
#根据下拉框的值来选取
Select(driver.find_element_by_id('X')).select_by_visible_text('Python')
"""
```