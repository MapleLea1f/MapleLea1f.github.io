---
title: Selenium入门笔记
date: 2024-09-02 16:46:01
tags: [python,测试工具]
---

# selenium概述

## 什么是selenium？

Selenium是一个广泛使用的Web应用程序测试工具。它通过模拟真实用户在浏览器中的操作来测试Web应用，支持多种现代Web浏览器，如IE、Mozilla Firefox、Google Chrome、Safari、Opera和Edge等 3 。

Selenium的核心功能包括：

1. **浏览器兼容性测试**：测试应用程序在不同浏览器和操作系统上的兼容性。
2. **系统功能测试**：创建回归测试来检验软件功能和用户需求。
3. **支持多种编程语言**：测试脚本可以使用Java、Python等多种语言编写。

Selenium的主要组件包括：

- **Selenium IDE**：一个Firefox插件，可以录制用户的基本操作，生成测试用例，并可以将这些测试用例转换为其他语言的自动化脚本。
- **Selenium Remote Control (RC)**：支持多种平台和浏览器，可以用多种语言编写测试用例。
- **Selenium Grid**：允许Selenium-RC针对大规模的测试案例集或需要在不同环境中运行的测试案例集进行扩展。

对于初学者，Selenium的入门步骤通常包括安装Selenium库、配置浏览器驱动程序，以及学习如何编写和执行Selenium脚本。例如，使用Python进行Selenium自动化测试时，需要先安装selenium库和对应的浏览器驱动程序，然后通过编写Python脚本来控制浏览器行为，如打开网页、模拟鼠标点击、键盘输入等操作。

## selenium入门

- Python安装selenium库
`pip install selenium`

- 安装浏览器对应驱动
	1. 查看浏览器版本
	2. 安装前一个版本驱动

```python
# selenium实操实例
from selenium import webdriver
from selenium.webdriver.chrome.service import Service
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.support.select import Select
import time

# 导入小提示(有助于快速获取该模块内的函数或类)
# from .xxx(当前文件夹的某文件) import xxx

# 设置ChromeDriver的路径
chrome_driver_path = r".\chromedriver-win64\chromedriver.exe"  # 请将此路径替换为你的ChromeDriver的实际路径

# 创建Service对象
service = Service(chrome_driver_path)

# 创建Chrome浏览器实例
driver = webdriver.Chrome(service=service)

# 打开拉钩网站
url = "https://www.lagou.com"
driver.get(url)

# 打印当前页面的标题
print(driver.title)

# 点击“Java”标签，跳转到Java相关的职位操作
# java_btn=driver.find_element("xpath", '//*[@id="__next"]/div[2]/div[1]/div[2]/div[1]/div/div[1]/div/div/a[1]')
# java_btn.click()

# 输入搜索关键字“python”并回车
search_input=driver.find_element("xpath", '//*[@id="search_input"]')
search_input.send_keys("python")
time.sleep(1)

# keys允许selenium模拟键盘输入
search_input.send_keys(Keys.ENTER)

# 数据提取
xxx_list=driver.find_element("xpath", '对应的xpath路径')

for xxx in xxx_list:
	xxx.find_element("xpath", '对应的xpath路径')

# 执行js代码，删除浏览器中某个class的标签
driver.execute_script('''
    var a=document.getElementsByClassName('un-login-banner')[0];
    a.parentNode.removeChild(a);
''')

# 切换窗口(浏览器上方的标签页)
driver.switch_to.window(driver.window_handles[-1])
job_detail=driver.find_element("xpath", '//*[@id="job_detail"]')

#获取页面文本
txt=job_detail.text

# 关闭窗口并调整selenium的窗口
driver.close()
driver.switch_to.window(driver.window_handles[0])


# 等待，以便查看页面
# 新版selenium会自动关闭
time.sleep(10000000)


# 网页嵌套iframe的处理(直接xpath定位会出错，需要先切换到iframe中再定位)

## 切换到iframe中
iframe=driver.find_element("xpath", 'iframe的xpath路径')
driver.switch_to.frame(iframe)

## 获取iframe中的标签内的内容
input=driver.find_element("xpath", '某标签的xpath路径')
placeholder=input.get_property("placeholder")

## 从iframe中切换到父级页面
driver.switch_to.parent_frame()

# 下拉列表的处理 <select>

# html中select的标签结构如下
'''
<select>
    <option value="1">选项1</option>
    <option value="2">选项2</option>
    <option value="3">选项3</option>
</select>
'''
sel=driver.find_element("xpath", 'select的xpath路径')
select=Select(sel)

## 获取所有的选项
options=select.options

## 选择某个选项
select.select_by_index(0)  # 选择第一个选项
select.select_by_value("2")  # 选择value为2的选项
select.select_by_visible_text("选项2")  # 选择显示文本为“选项2”的选项

# 获取页面代码(不是页面源代码，是F12查看页面元素的html代码)
pagesource=driver.page_source

# 无头模式(即不打开浏览器窗口，仅在后台运行selenium)
from selenium.webdriver.chrome.options import Options
options = Options()
options.add_argument('--headless')
options.add_argument('--disable-gpu')
driver = webdriver.Chrome(options=options)

# 获取网站中的图片
png = driver.find_element("xpath", '图片的xpath路径').screenshot_as_png
```

## selenium识别验证码

- 方法一：通过调用超级鹰网站的api实现验证码识别(需要付费购买服务)
- 方法二：通过调用图鉴网站的api实现验证码识别(需要付费购买服务)
- 注：滑块验证难以识别
