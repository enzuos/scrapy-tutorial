# Scrapy-tutorial
## 一个简单明了的scrapy教程[点击中文教程]
## A Simple and Clear Scrapy Tutorial[Click English Tutorial]


## 中文教程

## 本教程使用的工具
IDE/编辑器：pyChram

## 安装scrapy
使用pip安装：pip install scrapy

## srcapy基础命令
| 命令           | 格式                                  | 说明                             |
|----------------|---------------------------------------|----------------------------------|
| startproject   | scrapy startproject <项目名>           | 创建一个新项目。                  |
| genspider      | scrapy genspider <爬虫文件名> <域名>   | 新建爬虫文件。                    |
| runspider      | scrapy runspider <爬虫文件>           | 运行一个爬虫文件，不需要创建项目。 |
| crawl          | scrapy crawl <spidername>             | 运行一个爬虫项目，必须要创建项目。  |
| list           | scrapy list                          | 列出项目中所有爬虫文件。           |
| view           | scrapy view <url地址>                | 从浏览器中打开 url 地址。          |
| shell          | csrapy shell <url地址>               | 命令行交互模式。                   |
| settings       | scrapy settings                      | 查看当前项目的配置信息。            |


## 示例教程

**创建一个scrapy爬虫项目**

**进入准备创建项目的文件夹**

**打开终端输入命令**

`cd C:\Users\Enzuo\Desktop\python爬虫教程文档`

我现在已经进入了python爬虫教程文档文件夹内了

**开始创建爬虫项目，输入命令**

`scrapy startproject ScrapyTutorial`

现在以及创建了一个名为ScrapyTutorial的项目文件夹，该文件夹内还有一个ScrapyTutorial文件夹，里面就是你所创建爬虫项目文件了

**下面是该文件夹的结构图**

![ScrapyTutorial](https://example.com/logo.png)

- **ScrapyTutorial**: 这是项目的根文件夹，通常是项目的名称。它包含了整个 Scrapy 项目的主要代码和配置文件。
  - **spiders**: 这是存放爬虫文件的文件夹。爬虫文件包含了用于抓取数据的规则和逻辑。
    - **__init__.py**: 这是一个空的 Python 初始化文件，用于将 `spiders` 文件夹标记为一个 Python 包。
  - **items.py**: 这个文件定义了数据项（Item）的结构，通常用于描述从网页中抓取的数据结构。
  - **middlewares.py**: 这个文件用于存放 Scrapy 中间件，中间件可以用于修改请求和响应、处理异常、添加代理等操作。
  - **pipelines.py**: 这个文件定义了数据处理的管道，管道用于处理从爬虫中抓取的数据。
  - **settings.py**: 这个文件包含了 Scrapy 项目的配置信息，如爬虫的 User-Agent、延时设置、数据存储方式等。
- **scrapy.cfg**: 这是 Scrapy 项目的配置文件，其中包含了项目的配置信息和设置。

**现在使用`cd ScrapyTutorial`进入python爬虫教程文档\ScrapyTutorial**

**再次使用`cd ScrapyTutorial`进入python爬虫教程文档\ScrapyTutorial\ScrapyTutorial**

现在已经进入python爬虫教程文档\ScrapyTutorial\ScrapyTutorial了，可以开始创建爬虫文件了

**开始创建爬虫文件，输入命令**

`scrapy genspider Baidu baidu.com`

现在创建了一个文件名为Baidu.py的爬虫文件，爬取域名baidu.com，设置域名是表示爬虫只能爬取该域名下的页面与数据

## 配置settings.py文件
**打开settings.py文件，找到`ROBOTSTXT_OBEY = True`更改为`ROBOTSTXT_OBEY = False`**

在 Scrapy 中，ROBOTSTXT_OBEY 是一个设置项，用于指定爬虫是否要遵守网站的 robots.txt 文件。robots.txt 是一个标准，用于告诉网络爬虫哪些页面可以被抓取，哪些页面不应被抓取。ROBOTSTXT_OBEY 可以设置为 True 或 False。（我才不遵守）

`ROBOTSTXT_OBEY = True`：Scrapy 爬虫会自动遵守网站的 robots.txt 规则。在发送请求之前，Scrapy 会检查网站的 robots.txt 文件，如果该页面被禁止爬取，Scrapy 将不会发送请求。

`ROBOTSTXT_OBEY = False`：Scrapy 爬虫将不会遵守网站的 robots.txt 规则。无论网站的 robots.txt 文件中的规则是什么，Scrapy 都会发送请求并进行爬取。

**打开settings.py文件，找到下面的代码，将其取消注释**
```
# ITEM_PIPELINES = {
#     "ScrapyTutorial.pipelines.ScrapytutorialPipeline": 300,
# }
```

这段代码是 Scrapy 项目中的配置项，用于设置数据处理的管道（pipelines）。在 Scrapy 中，管道用于处理从爬虫中抓取的数据，可以对数据进行清洗、转换、存储等操作。

`"ScrapyTutorial.pipelines.ScrapytutorialPipeline": 300,`表示一个位于ScrapyTutorial文件夹里pipelines文件内ScrapytutorialPipeline的类，该管道类的优先级为300，该数字越大，优先级越高

如果一个管道不够用的话还可以添加管道

```
ITEM_PIPELINES = {
    "ScrapyTutorial.pipelines.ScrapytutorialPipeline": 300,
    "ScrapyTutorial.pipelines.ScrapytutorialPipeline_text": 280
}
```

现在添加了一个管道，总共有两个管道了，根据优先级排序规则，数字越大，优先级越高，数据会先经过第一个管道`ScrapytutorialPipeline`进行数据处理，然后是第二个管道`ScrapytutorialPipeline_text`进行数据处理

## spider蜘蛛文件的编写

**打开创建好的spider文件夹里的文件Baidu.py**

Baidu.py文件内容：

```
import scrapy


class BaiduSpider(scrapy.Spider):
    name = "Baidu"
    allowed_domains = ["baidu.com"]
    start_urls = ["https://baidu.com"]

    def parse(self, response):
        pass

```

`name = "Baidu"`定义爬虫的名称为 "Baidu"，在后续操作中可以根据这个名称启动爬虫。

`allowed_domains = ["baidu.com"]`设置允许爬虫抓取的域名，这里是 "baidu.com"，表示爬虫只会抓取该域名下的页面与数据。

`start_urls = ["https://baidu.com"]`定义爬虫起始的 URL 列表，这里只有一个 URL "https://baidu.com"，表示爬虫会从这个 URL 开始抓取数据。

`def parse(self, response):`定义一个名为 parse 的方法，它会在每次抓取到页面后被调用，用解析页面的响应数据。爬虫爬取到数据后默认调用这个方法进行解析数据

**爬取`https://baidu.com`的html页面并解析**
### get()方法：
    用于获取第一个匹配的节点的数据。
    返回匹配的节点的内容作为字符串。
    如果没有匹配的节点，返回None。
### getall()方法：
    用于获取所有匹配的节点的数据。
    返回匹配的节点的内容作为列表，每个元素都是一个字符串。
    如果没有匹配的节点，返回一个空列表。

**Selector与SelectorList的区别**

当使用选择器方法（如 .xpath()、.css() 等）在 response 上进行操作时，如果返回的是单个数据，那么返回的数据类型就是 Selector 对象。而如果返回的是多个数据，那么返回的数据类型就是 SelectorList 对象。SelectorList 是一个类似于列表的对象，可以包含多个 Selector 对象，您可以对其进行遍历和操作。所以，可以简单总结为：单个数据返回 Selector 对象，多个数据返回 SelectorList 对象。

```
class BaiduSpider(scrapy.Spider):
    name = "Baidu"
    allowed_domains = ["baidu.com"]
    start_urls = ["https://baidu.com"]

    # 解析baidu.com网页，获取搜索框按钮的名称
    def parse(self, response):
        # 获取搜索框按钮的名称
        # 爬虫返回了response响应对象，可以直接对该响应对象做xpath解析，拿到搜索框按钮的名称
        input_value = response.xpath('//span[@id="s_btn_wr"]/input/@value')
        # 解析后得到input_value，用tpye看看这是什么类型
        print(type(input_value))  # <class 'scrapy.selector.unified.SelectorList'>
        # 这是SelectorList对象，而且它是一个列表，这代表response.xpath解析后返回的是一个的SelectorList对象，这个对象是一个列表，可以通过遍历列表的方式对它进行遍历操作
        print(input_value)  # [<Selector query="//input[@id='su']/@value" data='百度一下'>]
        #若想拿到Selector对象里面的内容需要拆包 get() getall()
        input_value = input_value.get()
        print(type(input_value))  # <class 'str'>
        print(input_value)  # 百度一下
        # input_value = input_value.getall()
        # print(type(input_value))  # <class 'list'>
        # print(input_value)  # ["百度一下"]
        
```


