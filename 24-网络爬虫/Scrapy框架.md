# Scrapy框架

Scrapy，Python开发的一个快速,高层次的屏幕抓取和web抓取框架，用于抓取web站点并从页面中提取结构化的数据。Scrapy用途广泛，可以用于数据挖掘、监测和自动化测试

整体架构大致如下

![img](img/scrapy_structure.jpg)

Scrapy运行流程大概如下：

（1）调度器(Scheduler)从 待下载链接 中取出一个链接(URL)

（2）调度器启动 采集模块Spiders模块

（3）采集模块把URL传给下载器（Downloader），下载器把资源下载下来

（4）提取目标数据，抽取出目标对象（Item）,则交给实体管道（item pipeline）进行进一步的处理；比如存入数据库、文本

（5）若是解析出的是链接（URL）,则把URL插入到待爬取队列当中