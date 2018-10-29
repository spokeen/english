##### scrapy控制台命令

```
#创建项目
scrapy startproject projectName
#创建spider
scrapy genspider spiderName "http://www.baidu.com"
scrapy genspider -l    #查看模板类型
#开始爬取网页
scrapy crawl spiderName
#列出所有可用的spider
scrapy list
```

