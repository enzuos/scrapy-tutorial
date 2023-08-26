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

创建一个scrapy爬虫项目

进入准备创建项目的文件夹

打开终端输入命令

`cd C:\Users\Enzuo\Desktop\python爬虫教程文档`

我现在已经进入了python爬虫教程文档文件夹内了

开始创建爬虫项目，输入命令

`scrapy startproject ScrapyTutorial`

现在以及创建了一个名为ScrapyTutorial的文件夹

下面是该文件夹的结构图

![ScrapyTutorial](https://example.com/logo.png)

