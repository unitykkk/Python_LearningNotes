### Scrapy基础0

```python
# -*- coding: utf-8 -*-
import scrapy
import json

class DoubanTestSpider(scrapy.Spider):
    name = 'douban_test'
    # allowed_domains = ['https://book.douban.com/']
    start_urls = ['https://book.douban.com/tag/%E6%95%A3%E6%96%87/']
    # 浏览器用户代理
    headers = {
        'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/70.0.3538.77 Safari/537.36'
    }

    def start_requests(self):
        urls = ['https://book.douban.com/tag/%E6%95%A3%E6%96%87/']
        for url in urls:
            yield scrapy.Request(url=url, headers=self.headers)

    def parse(self, response):
        # print(response.text)
        items = response.xpath('//ul[@class="subject-list"]/li[@class="subject-item"]')
        with open('books.json', 'a', encoding="utf-8") as f:
            for item in items:
                bookinfo = {
                    'name':item.xpath('./div[@class="info"]/h2/a/text()').extract_first().strip(),
                    'pub':item.xpath('./div[@class="info"]/div[@class="pub"]/text()').extract_first().strip()
                }
                print(bookinfo)
                f.write(json.dumps(bookinfo, ensure_ascii=False))
                f.write('\n')

        nextpage_url = response.xpath('//div[@class="paginator"]/span[@class="next"]/a/@href').extract_first()
        # 只爬取前5页,每页有20项
        if '100' in nextpage_url:
            return
        return scrapy.Request("https://book.douban.com%s" % nextpage_url, headers=self.headers)
```