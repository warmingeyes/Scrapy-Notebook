# Python3 网络爬虫开发实战 第1章 开发环境配置



## 1. Python3的安装

安装方式：直接使用Anaconda集成环境

## 2. 请求库的安装

爬虫可以简单分为几步：抓取页面、分析页面和存储数据。在抓取页面的过程中，我们需要模拟浏览器向服务器发出请求，所以需要用到一些Python库来实现HTTP请求操作。在本书中，我们用到的第三方库有requests，Selenium和aiohttp等。

### 2.1 requests的安装

```shell
$ pip install requests
```

### 2.2 Selenium的安装

Selenium是一个自动化测试工具，利用它我们可以驱动浏览器执行特定的动作，如点击、下拉等操作。对于一些JavaScript渲染的页面来说，这种抓取方式非常有效。

安装方式：直接使用Anaconda集成环境

### 2.3 Chrome Driver的安装与测试

Selenium是一个自动化测试工具，需要浏览器来配合使用，因此Chrome Driver驱动的配置才能保证有效地使用Selenium。

#### 2.3.1 Chrome Driver的安装

1. 首先查询Chrome安装版本，在Chrome的地址栏输入`chrome://version/`
2. 根据查询到的版本号下载对应的Chrome Driver的版本，将下载下来的Zip文件进行解压得到**chromedriver.exe**
3. 将拷贝**chromedriver.exe**至 Anaconda的Scripts目录下

#### 2.3.2 Chrome Driver的测试

```python
from selenium import webdriver
driver = webdriver.Chrome()
```

如果输入以上代码后，自动跳出Chrome的空白页面，则配置正常

### 2.4 PhantomJS的安装与测试

PhantomJS是一个无界面的、可脚本编程的WebKit浏览器引擎，它原生支持多种Web标准：DOM操作、CSS选择器、JSON，Canvas以及SVG。Selenium支持PhantomJs，这样在运行的时候就不会再弹出一个浏览器了。

#### 2.4.1 PhantomJS的安装

1. 下载PhantomJS，将下载下来的Zip文件进行解压，在文件夹中找到**PhantomJS.exe**
2. 将拷贝**PhantomJS.exe**至 Anaconda的Scripts目录下

#### 2.4.2 PhantomJS的测试

```python
from selenium import webdriver
browser = webdriver.PhantomJS()
browser.get("https://www.baidu.com")
print(browser.current_url)
```

如果输入以上代码后，输出www.baiduc.om则是正常的

## 2.5 aiohttp的安装

之前介绍的requests库是一个阻塞式HTTP请求库，当我们发出一个请求后，程序会一直等待服务器响应，直到得到响应后，程序才会进行下一步处理。其实，这个过程比较耗费时间。如果程序可以在这个等待过程中做一些其他的事情，如进行请求的调度、响应的处理等，那么爬取效率一定会大大提高。aiohttp就是这样一个提供异步web服务的库，从Python 3.5版本开始，Python中加入了`async/await`关键字，使得回调的写法更加直观和人性化。aiohttp的异步操作借助于`async/await`关键字的写法变得更加简洁，架构更加清晰。

```shell
$ pip install aiohttp
```

# 3. 解析库的安装

## 3.1 lxml的安装

lxml是Python的一个解析库，支持HTML和XML的解析，支持XPath解析方式，而且解析效率非常高。本节中，我们了解一下lxml的安装方式。

安装方式：直接使用Anaconda集成环境

## 3.2 Beautiful Soup的安装

Beautiful Soup是Python的一个HTML或XML的解析库，我们可以用它来方便地从网页中提取数据。它拥有强大的API和多样的解析方式。

安装方式：直接使用Anaconda集成环境

注意，这里我们虽然安装的是beautifulsoup4这个包，但是在引入的时候却是bs4，这是因为这个包源代码本身的库文件夹名称就是bs4，所以安装完成之后，这个库文件夹就被移入到本机Python3的lib库里，所以识别到的库文件名就叫作bs4因此，包本身的名称和我们使用时导入的包的名称并不一定是一致的。

## 3.3 pyquery的安装

pyquery同样是一个强大的网页解析工具，它提供了和jQuery类似的语法来解析HTML文档，支持CSS选择器，使用非常方便。

```shell
$ pip install pyquery
```

## 3.4 tesserocr的安装

在爬虫过程中，难免会遇到各种各样的验证码，而大多数验证码还是图形验证码，这时候我们可以直接用OCR来识别。

