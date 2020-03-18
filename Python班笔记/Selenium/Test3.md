### Test3

```python
from selenium import webdriver
from selenium.webdriver.common.action_chains import ActionChains
import time
url = 'https://passport.bilibili.com/login'
driver = webdriver.Chrome()
driver.get(url)

driver.find_element_by_id('login-username').send_keys('15118167777')
driver.find_element_by_id('login-passwd').send_keys('xxxxxxxx')

#双击登录   用xpath更可靠,有时用类名找但找不到
element = driver.find_element_by_xpath('//*[@id="geetest-wrap"]/div/div[5]/a[1]')
ActionChains(driver).double_click(element).perform()

#设置延吋，否则会导致操作过快
time.sleep(3)
#拖拉滑条         这个拖动的距离不好确定，因为每个生成的不一样
element = driver.find_element_by_class_name('geetest_slider_button')
ActionChains(driver).drag_and_drop_by_offset(element, 95, 0).perform()
```