### Test0

```python
from selenium import webdriver

url = "https://www.baidu.com/"
# path = r"D:\E_Soft\Anaconda3\chromedriver_win32\chromedriver.exe"
# browser = webdriver.Chrome(executable_path=path)

# 与Python.exe同目录的话就不需要指定driver路径
browser = webdriver.Chrome()
browser.get(url)
```

