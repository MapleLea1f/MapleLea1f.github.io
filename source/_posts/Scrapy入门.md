# Scrapy入门

## 什么是scrapy?

Scrapy 是一个用于爬取网站数据的开源和协作框架。它使用 Python 编写，广泛用于数据挖掘、监控和自动化测试。以下是一些关于 Scrapy 的基本信息和使用步骤：

### 整体工作流程
1. 爬虫中起始的url构造成request对象，并传递给调度器.
2. 引擎从调度器中获取到request对象.然后交给下载器
3. 由下载器来获取到页面源代码，并封装成response对象.并回馈给引擎
4. 引擎将获取到的response对象传递给spider，由spider对数据进行解析(parse).并回馈给引擎
5. 引擎将数据传递给pipeline进行数据持久化保存或进一步的数据处理.
6. 在此期间如果spider中提取到的并不是数据.而是子页面url.可以进一步提交给调度器，进而重复步骤2的过程

### 安装 Scrapy

首先，你需要安装 Scrapy。你可以使用 pip 来安装：

```bash
pip install scrapy
```

### 创建一个 Scrapy 项目

安装完成后，你可以创建一个新的 Scrapy 项目：

```bash
scrapy startproject myproject
```

这将会创建一个名为 `myproject` 的目录，其中包含 Scrapy 项目的基本结构。

### 创建一个爬虫

在项目目录中，你可以创建一个新的爬虫：

```bash
cd myproject
scrapy genspider example(名字) example.com(域名)
```

这将会在 `spiders` 目录下创建一个名为 `example.py` 的爬虫文件。

``

### 编写爬虫代码

打开 `example.py` 文件，你会看到一个基本的爬虫模板。你可以根据需要修改它来抓取你想要的数据。例如：

```python
import scrapy

class ExampleSpider(scrapy.Spider):
    name = 'example'
    allowed_domains = ['example.com']
    start_urls = ['http://example.com/'] #此项为需要抓取的页面，按需修改

    def parse(self, response):
    	#xpath进行数据解析
        txt=response.xpath('xpath解析路径').extract() #提取内容
		
		#分块提取数据
		li_list=response.xpath('xpath解析路径').extract() #返回列表
		for li in li_list:
			name=li.xpath('xpath解析路径').extract_first() #返回一个数据，若没有则返回None
            dic={
                'name':name
            }
            #需要用yield将数据传递给管道
            yield dic
```

### 运行爬虫

编写好爬虫后，你可以运行它来抓取数据：

```bash
scrapy crawl example(爬虫名---name)
```

### 保存数据

你可以将抓取的数据保存到文件中。例如，保存为 JSON 文件(一般完整的项目通过管道存储的数据库)：

```bash
scrapy crawl example -o items.json
```

`pipelines.py`默认是不生效的，需要去`settings.py`中进行设置

```python
# settings中对日志输出级别的处理
LOG_LEVEL='WARNING'
# 日志的级别：DEBUG,INFO,WARNING,ERROR,CRITICAL

ITEM_PIPELINES = {
	# key 就是管道的路径
	# value 是管道的优先级 值越小，优先级越高
   "myproject.pipelines.MyprojectPipeline": 300,
}
```
在`pipelines.py`中对数据进行处理
```python
class MyprojectPipeline:
    def process_item(self, item, spider):
        return item #必须return，保证下一个管道能收到数据
        
#允许设置多个pipeline，在ITEM_PIPELINES中添加即可
class NewPipeline:
    def process_item(self, item, spider):
        return item
```

### 进阶功能

Scrapy 还提供了许多进阶功能，如：

- **中间件**：用于处理请求和响应。
- **管道**：用于处理和存储抓取的数据。
- **调度器**：用于管理请求队列。
- **下载器**：用于下载网页内容。

你可以根据需要配置这些功能来优化你的爬虫。

### 示例项目结构

一个典型的 Scrapy 项目结构如下：

```
myproject/
    scrapy.cfg            # 部署配置文件
    myproject/            # 项目Python模块，之后将在此加入代码
        __init__.py
        items.py          # 项目items定义文件
        middlewares.py    # 项目中间件文件
        pipelines.py      # 项目管道文件
        settings.py       # 项目设置文件
        spiders/          # 爬虫目录
            __init__.py
            example.py    # 爬虫文件
```

通过这些步骤，你可以开始使用 Scrapy 来抓取和处理网页数据。Scrapy 的功能非常强大，适合各种规模的爬虫项目。



