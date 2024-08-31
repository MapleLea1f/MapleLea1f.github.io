<h1>re模块</h1>
<p><strong>re(regular expression),正则表达式</strong></p>
<pre><code class="language-python">import re

#返回包含所有匹配结果的一个列表
result=re.findall(r&quot;\d+&quot;，&quot;我今年18岁，我有200000000块&quot;)
print(result)

#爬虫常用
result=re.finditer(r&quot;\d+&quot;，&quot;我今年18岁，我有200000000块&quot;)
for item in result:#从选代器中拿到内容
    print(item.group())#从匹配到的结果中拿到数据

#search只会匹配到第一次匹配的内容
result=re.search(r&quot;\d+&quot;，&quot;我叫周杰伦，今年32岁，我的班级是5年4班&quot;)
print(result)

#match在匹配，从字符串的开头匹配，即在正则前加上^
result=re.search(r&quot;\d+&quot;，&quot;我叫周杰伦，今年32岁，我的班级是5年4班&quot;)
print(result)

#预加载，提前把正则对象加载完毕
obj=re.compile(r&quot;\d+&quot;)
#直接使用加载好的正则表达式
result=obj.findall(&quot;我叫周杰伦，今年32岁，我的班级是5年4班&quot;)
print(result)

#目标是提取10010、10086和中国联通、中国移动
s=&#039;&#039;&#039;
&lt;div class=&#039;西游记&#039;&gt;span id=&#039;10010&#039;&gt;中国联通&lt;/span&gt;&lt;/div&gt;
&lt;div class=&#039;西游记&#039;&gt;&lt;span id=&#039;10086&#039;&gt;中国移动&lt;/span&gt;&lt;/div&gt;
&#039;&#039;&#039;
obj=re.compile(r&quot;&lt;span id=&#039;(?P&lt;id&gt;\d+)&#039;&gt;(?P&lt;name&gt;.*?)&lt;/span&gt;&quot;)
#()用来提取正则表达式搜索后需要的内容
#?P&lt;xxx&gt;负责将提取后的数据分类进标签内的组别中
result = obj.finditer(s)
for item in result:
    id = item.group(&quot;id&quot;)
    print(id)

#re.S可以让正则中的.匹配换行符
obj =re.compile(r&#039;&lt;div class=&quot;item&quot;&gt;.*?&lt;span class=&quot;title&quot;&gt;(?P&lt;name&gt;.*?)&lt;/span&gt;&#039;,re.S)</code></pre>
<h1>bs4模块</h1>
<p><strong>BeautifulSoup,对标签和属性单步查找</strong></p>
<pre><code class="language-python">pip install bs4
from bs4 import BeautifulSoup

#1.初始化BeautifulSoup对象
page=BeautifulSoup(html,&quot;html.parser&quot;)

#查找某个元素，只会找到一个结果
page.find(&quot;标签名&quot;,attrs={&quot;属性&quot;:&quot;值&quot;})

#获取对应属性的标签
li= page.find(&quot;li&quot;,attrs={&quot;id&quot;:&quot;abc&quot;})
a=li.find(&#039;a&#039;)
print(a.text) #获取标签中的文本
print(a.get(&#039;href&#039;)) #获取标签中的对应属性

#查询所有结果
page.find_all(&quot;标签名&quot;,attrs={&quot;属性&quot;：&quot;值&quot;})

li_list=page.find_all(&#039;li&#039;)
for li in li_list:
    a=li.find(&#039;a&#039;)

#通过img_src下载图片
img_src=div.find(&#039;img&#039;).get(&#039;src&#039;)
img=requests.get(img_src)
#通过二进制写入将图片数据存入文件
with open(f&quot;{img_name}.jpg&quot;,mode=&#039;wb&#039;) as f:
    f.write(img.content)</code></pre>
<h1>XPath解析</h1>
<p>XPath是一门在XML文档中查找信息的语言。XPath可用来在XML文档中对元素和属性进行遍历。而我们熟知的HTML恰巧属于XML的一个子集。所以完全可以用xpath去查找html中的内容。</p>
<pre><code class="language-python">pip install lxml

from lxml import etree

#如果报错，可以考虑这种导入方式
from lxml import html
etree=html.etree

#xpath解析xml
et=etree.XML(str)
result=et.xpath(&#039;/book&#039;) #表示根节点
result=et.xpath(&#039;/book/name&#039;) #xpath中间的/类似与文件路径，表示其子分支
result=et.xpath(&#039;/book/name/text()&#039;) #取对应节点文本内容
result=et.xpath(&#039;/book//nick&#039;) #//表示所有子代与嵌套子代
result=et.xpath(&#039;/book/*/nick&#039;) #*表示任意book的子代，最终取book的孙代nick节点
result=et.xpath(&#039;/book/author/nick[@class=&#039;jay&#039;]/text()&#039;) #[]表示属性筛选 @属性名=值
result=et.xpath(&#039;/book/author/nick[2]/text()&#039;) #[n]同时也对应同一节点下的第n项同名节点
result=et.xpath(&#039;/book/partner/nick/@id&#039;) #获取对应的nick中的id属性值

#xpath解析HTML
et=etree.HTML(str)
li_list=et.xpath(&#039;//li&#039;)
for li in li_list:
    href=li.xpath(&#039;./a/@href&#039;) #./表示当前节点
    text=li.xpath(&#039;./a/text()&#039;)</code></pre>
<h1>pyquery模块</h1>
<p><strong>pyquery主要通过css选择器的方式处理数据
pyquery能改变HTML中的结构</strong></p>
<pre><code class="language-python">pip install pyquery
from pyquery import PyQuery

#加载html内容
p=PyQuery(html)

li=p(&#039;li&#039;)
#获取的对象为a标签时
a=p(&#039;li&#039;)(&#039;a&#039;) #链式选择
a=p(&#039;li a&#039;) #后代选择
a=p(&#039;.aaa a&#039;) #class=&#039;aaa&#039;
a=p(&#039;#qq a&#039;) #id=&#039;qq&#039;

href=p(&#039;#qq a&#039;).attr(&#039;href&#039;) #获取属性
text=p(&#039;#qq a&#039;).text() #获取文本

#注：如果多个标签同时获取属性，只能拿到第一个
href=p(&#039;li a&#039;).attr(&#039;href&#039;)

#多个标签获取属性
it=p(&#039;li a&#039;).items()
for item in it:
    href=item.attr(&#039;href&#039;)
    text=item.text() #获取文字
    html=item.html() #获取全部内容

#对HTML内容进行修改
p(&#039;div.aaa&#039;).after(&#039;&#039;&#039;xxx&#039;&#039;&#039;) #在标签后方添加
p(&#039;div.aaa&#039;).append(&#039;&#039;&#039;xxx&#039;&#039;&#039;) #在标签内容中添加
p(&#039;div.bbb&#039;).attr(&#039;class&#039;,&#039;aaa&#039;) #更改标签的属性
p(&#039;div.bbb&#039;).remove_attr(&#039;class&#039;)#删除标签属性
p(&#039;div.bbb&#039;).remove() #删除该标签</code></pre>