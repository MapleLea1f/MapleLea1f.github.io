<h1>1、django的安装</h1>
<h2>1-1 安装django</h2>
<p><code>pip install django</code>
c:\python</p>
<ul>
<li>python.exe</li>
<li>Scripts</li>
<li>
<ul>
<li>pip.exe</li>
</ul>
</li>
<li>
<ul>
<li>django-admin.exe[工具，创建django项目中的文件和文件夹]</li>
</ul>
</li>
<li>Lib</li>
<li>
<ul>
<li>内置模块</li>
</ul>
</li>
<li>
<ul>
<li>site-packages</li>
</ul>
</li>
<li>
<ul>
<li>
<ul>
<li>openpyxl</li>
</ul>
</li>
</ul>
</li>
<li>
<ul>
<li>
<ul>
<li>python-docx</li>
</ul>
</li>
</ul>
</li>
<li>
<ul>
<li>
<ul>
<li>flask</li>
</ul>
</li>
</ul>
</li>
<li>
<ul>
<li>
<ul>
<li>django  [框架的源码]</li>
</ul>
</li>
</ul>
</li>
</ul>
<h1>2、创建项目</h1>
<h2>2-1 命令行创建项目</h2>
<p><code>django中项目会有一些默认的文件和默认的文件夹</code></p>
<p><code>&quot;C:\Users\20405\AppData\Local\Programs\Python\Python311\Scripts\django-admin.exe&quot; startproject 项目名称</code></p>
<h2>2-2 Pycharm创建项目</h2>
<p>略</p>
<h2>2-3 对比两种方式</h2>
<ul>
<li>命令行
<ul>
<li>创建的项目是标准的</li>
</ul></li>
<li>pycharm
<ul>
<li>在标准的基础上增加了templates目录</li>
<li>在settings.py中增添&quot;DIR:{...}&quot;</li>
</ul></li>
</ul>
<h1>3、创建app</h1>
<h2>3-1 默认文件介绍</h2>
<p>补充：<code>tree [drive:][path] [/f] [/a]</code>
其中/f显示所有文件和目录，即file;/a列出所有文件，包括隐藏文件和文件</p>
<pre><code>D:new
    │  manage.py  [项目的管理，启动项目、创建app、数据管理]
    │
    └─new
            asgi.py [接收网络请求][不用动]
            wsgi.py [接收网络请求][不用动]
            settings.py [项目配置] [例如：链接数据库][经常操作]
            urls.py [URL和函数的对应关系][经常操作]
            __init__.py</code></pre>
<h2>3-2 app的创建和说明</h2>
<pre><code>-项目(即app中相互独立)
    - app,用户管理[表结构、函数、HTML模板、CSS]
    - app,订单管理[表结构、函数、HTML模板、CSS]
    - app,后台管理[表结构、函数、HTML模板、CSS]
    - app,网站[表结构、函数、HTML模板、CSS]
    - app,API[表结构、函数、HTML模板、CSS]

注：开发简洁的情况下，一个app即可</code></pre>
<p>在相应目录中<code>python manage.py startapp app01</code></p>
<pre><code>├─app01
│  │  admin.py [django默认提供admin后台管理][不用动]
│  │  apps.py [app启动类][不用动]
│  │  models.py [对数据库操作][重要]
│  │  tests.py [单元测试][不用动]
│  │  views.py [视图函数，与url的函数变动相关][重要]
│  │  __init__.py
│  │
│  └─migrations [数据库变更记录][不用动]
│          __init__.py
</code></pre>
<h1>4、快速上手</h1>
<h2>4-1 启动并返回页面</h2>
<ul>
<li>确保app已注册
将apps.py中定义的类放在settings.py中的INSTALLED_APPS中
<code>&#039;app01.apps.App01Config&#039;</code></li>
<li>编写URL和视图函数对应关系[urls.py]</li>
</ul>
<pre><code>from app01 import views

urlpatterns = [
    # path(&#039;admin/&#039;, admin.site.urls),
    #www.xxx.com/index/ -&gt; 函数
    path(&#039;index/&#039;, views.index),
]
即用户访问对应域名时会去执行views里的index函数</code></pre>
<ul>
<li>编写视图函数[views.py]</li>
</ul>
<pre><code>
from django.shortcuts import render

# Create your views here.
def index(request):
    return render(request, &#039;app01/index.html&#039;)
其中request是默认参数</code></pre>
<ul>
<li>启动django项目
<ul>
<li>命令行启动
<code>python manage.py runserver</code></li>
</ul></li>
</ul>
<h2>4-2 templates模板</h2>
<p>增添页面：
注：<code>return HttpResponse(&quot;用户列表&quot;)</code>即返回http响应，仅有文字(非提示框)</p>
<p><code>path(&#039;users/list/&#039;, views.users_list)-&gt;def users_list(request)</code>
对应运行网址：<code>http://127.0.0.1:8000/users/list/</code></p>
<p><code>path(&#039;users/add/&#039;, views.add_user)-&gt;def add_user(request)</code>
对应运行网址：<code>http://127.0.0.1:8000/users/add/</code></p>
<p>总结：path即对应路径，后面是对应函数。</p>
<p><code>return render(request, &#039;index.html&#039;)</code>
Q：render会在哪个目录下寻找文件？
A：优先在settings.py中设置的DIR中寻找，若无则默认在app实例的目录下的templates目录寻找index.html(根据app的注册顺序，逐一在它们的templates目录中寻找)</p>
<h2>4-3 静态文件</h2>
<p>在开发过程中一般将：</p>
<ul>
<li>图片</li>
<li>CSS</li>
<li>js</li>
</ul>
<p>都会当做静态文件处理</p>
<p>常规情况下编写路径：
<code>&quot;src=/static/img/xxx.png&quot;</code></p>
<p>但在django中：</p>
<pre><code>{% load static %}
src=&quot;{% static &quot;img/xxx.png&quot;%}&quot;</code></pre>
<p>Q:为什么要这样编写？
A:因为在settings.py中可以设置static的路径</p>
<h1>5、模板语法</h1>
<p>本质上：在HTML中写一些占位符，由数据对这些占位符进行替换和处理</p>
<pre><code>#数据替换HTML对应模板
def tpl(request):
    name=&quot;John&quot;
    roles=[&quot;admin&quot;,&quot;user&quot;]
    user_info={&#039;name&#039;:&#039;zhangsan&#039;,&#039;salary&#039;:10000,&#039;age&#039;:25}
    data=[
        {&#039;name&#039;:&#039;zhangsan&#039;,&#039;salary&#039;:10000,&#039;age&#039;:25},
        {&#039;name&#039;:&#039;lisi&#039;,&#039;salary&#039;:20000,&#039;age&#039;:30},
        {&#039;name&#039;:&#039;wangwu&#039;,&#039;salary&#039;:30000,&#039;age&#039;:40},
    ]

    return render(request, &#039;tpl.html&#039;, {&#039;name&#039;:name, &#039;roles&#039;:roles,&#039;user_info&#039;:user_info,data:data})

&lt;div&gt;{{name}}&lt;/div&gt;
&lt;div&gt;{{roles}}&lt;/div&gt;
#{{?}}这种形式会原封不动返回传进去的元素，如传入列表则显示为[?]
&lt;div&gt;{{roles.0}}&lt;/div&gt;
#此处.0指索引项
&lt;div&gt;
    {% for item in roles%}
        &lt;span&gt;{{ item }}&lt;/span&gt;
    {% endfor %}
&lt;/div&gt;
#对元素进行循环的方法，span是为迭代的元素生成空白格来存放
{{userinfo.name}}
{{userinfo.salary}}
#获取字典对应键的值
&lt;ul&gt;
{% for item in userinfo.keys %}
{% for item in userinfo.values %}
    &lt;li&gt;{{ item }}&lt;/li&gt;
{% for k,v in userinfo.items %}
    &lt;li&gt;key:{{ k }};value:{{ v }}&lt;/li&gt;
{% endfor %}
&lt;/ul&gt;
#对字典的键或值或键值对进行循环
{{data.1}}
{{data.1.name}}
#列表嵌套字典
{%if name=&#039;zhangsan&#039;%}
    &lt;h1&gt;y&lt;/h1&gt;
{%elif name=&#039;lisi&#039;%}
    &lt;h1&gt;what?&lt;/h1&gt;
{%else%}
    &lt;h1&gt;n&lt;/h1&gt;
{%endif%}
总结：
1、 .代表对应索引
2、 {{?}}指变量
3、 {%%}指语法</code></pre>
<h1>6、请求与响应</h1>
<p>request是一个对象，封装了用户发送过来的所有请求相关数据</p>
<ul>
<li>获取请求方式：GET/POST
<code>request.method</code>
<code>GET</code>/<code>POST</code></li>
<li>在URL上传递的值(GET) <code>/index/?n1=1&amp;n2=2</code>
<code>request.GET</code>
<code>&lt;QueryDict:{&#039;n1&#039;:[&#039;1&#039;],&#039;n2&#039;:[&#039;2&#039;]}&gt;</code></li>
<li>在请求体中提交数据(POST)
<code>request.POST(.get(&#039;user&#039;))</code></li>
<li>[响应]HttpResponse(&quot;返回内容&quot;),将内容字符串返回请求者
<code>return HttpResponse(&quot;返回内容&quot;)</code></li>
<li>[响应]读取HTML的内容+渲染（替换）
<code>return render(request,&#039;xxx.html&#039;,&#039;{xxx:xxx}&#039;)</code></li>
<li>[响应]浏览器重定向到其他页面
<code>return redirect(&#039;xxx&#039;)</code>
注：关于重定向
<ul>
1、Django获取重定向页面后返回用户 ×
</ul>
<ul>
2、Django告知浏览器重定向 √
</ul></li>
</ul>
<h2>案例：用户登录</h2>
<pre><code>#html
&lt;form method=&quot;post&quot; action=&quot;/Login/&quot;&gt;

   {% csrf_token %}

   &lt;input type=&quot;text&quot; name=&quot;user&quot; placeholder=&quot;用户名&quot;&gt;
   &lt;input type=&quot;password&quot; name=&quot;pwd&quot; placeholder=&quot;密码&quot;&gt;
   &lt;input type=&quot;submit&quot; value=&quot;提交&quot;/&gt;
&lt;/form&gt;</code></pre>
<pre><code>#django
def login(request):
   if request.method ==&quot;GET&quot;:
      return render(request,&quot;login.htm&quot;)
   else:
      #如果是POST请求，获取用户提交的数据
      print(request.POST)
      return HttpResponse(&quot;登录成功）</code></pre>
<p><code>&lt;QueryDict:{&#039;csrfmiddlewaretoken&#039;:[&#039;xxx&#039;],&#039;user&#039;:[&#039;xxx&#039;},&#039;pwd&#039;:[&#039;xxx&#039;]&gt;</code></p>
<p>注:<strong>当未加入{% csrf_token %}时会出现403错误。</strong>403错误是一种在网站访问过程中，常见的错误提示，表示资源不可用。服务器理解客户的请求，但拒绝处理它，通常由于服务器上文件或目录的权限设置导致的WEB访问错误。</p>
<p>Q:登陆失败时如何仍然显示当前login页面并返回失败提示？
A:
<code>#html</code>
<code>&lt;input type=&quot;submit&quot; value=&quot;提交&quot;/&gt; {{error_msg}}</code>
<code>&lt;span styLe=&quot;color: red;&quot;&gt;{{error_msg}}&lt;/span&gt;</code></p>
<p><code>#django</code>
<code>return render(request,&#039;login.html&#039;，{&quot;error_msg&quot;：&#039;用户名或密码错误&#039;})</code></p>
<p><strong>注：若是if直接return，那么其else则可以省略，使代码更简洁</strong></p>
<h1>7、数据库操作</h1>
<ul>
<li>MySQL数据库 + pymysql
<pre><code class="language-python">import pymysql
#1.连接MySQL
conn = pymysql.connect(host&quot;127.0.0.1&quot;,port=3306, user=&#039;root&#039;,
passwd=&quot;root123&quot;，charset=&#039;utf8&#039;,db=&#039;unicom&#039;)
cursor = conn.cursor(cursor=pymysql.cursors.Dictcursor)
#2.发送指令
cursor.execute(&quot;insert into admin(username,password,mobile)
values(&#039;wupeiqi&#039;，&#039;qwe123&#039;，&#039;15155555555&#039;)&quot;)
conn.commit()
#3.关闭
cursor.close()
conn.close()</code></pre></li>
</ul>
<p><code>即：代码-&gt;pymysql-&gt;数据库</code></p>
<ul>
<li>Django开发操作数据库,内部提供了ORM框架</li>
</ul>
<p><code>即：代码-&gt;ORM-&gt;pymysql/MySQLdb/mysqlclient-&gt;数据库</code></p>
<h2>7-1 安装第三方模块</h2>
<p>注:Django新版对pymysql兼容会有问题
<code>pip install mysqlclient</code></p>
<h2>7-2 ORM</h2>
<h3>7-2-1 Django创建并连接数据库</h3>
<p>ORM的功能：</p>
<ul>
<li>创建、修改、删除数据库中的表(无法创建数据库)</li>
<li>操作表中的数据</li>
</ul>
<p>Q：Django如何连接数据库？
A:settings.py对DATABASES进行修改</p>
<pre><code class="language-python">DATABASES={
    &#039;default&#039;:{ 
        &#039;ENGINE&#039;:&#039;django.db.backends.mysql&#039;,
        &#039;NAME&#039;:&#039;dbname&#039;,#数据库名称
        &#039;USER&#039;:&#039;root&#039;,
        &#039;PASSWORD&#039;:&#039;XXX&#039;,
        &#039;HOST&#039;:&#039;localhost/127.0.0.1&#039;,#哪台机器安装了MySQL
        &#039;PORT&#039;:3306,
    }
}</code></pre>
<p><strong>注：Django默认创建并连接db.sqlite3</strong></p>
<h3>7-2-2 Django操作表</h3>
<ul>
<li>表的创建
<pre><code class="language-python">#在app实例中的models.py文件中
class UserInfo(models.Model):
name=models.CharField(max_length=32)
password=models.CharField(max_length=64)
age=models.IntegerField(default=18)
#Django自动将类转换成表，且创建自增主键id</code></pre></li>
<li>执行创建操作
<code>python manage.py makemigrations</code>
<code>python manage.py migrate</code></li>
</ul>
<p><strong>注1:将models.py中的类删除后再执行MySQL中也会执行删除表操作</strong>
<strong>注2:新增列时可能需要指定对应列的数据，在终端会有提示，选择需要的选项</strong></p>
<h3>7-2-3 表中数据的增删改查</h3>
<pre><code class="language-python">#表中数据创建
UserInfo.objects.create(name=&#039;xxx&#039;,password=&#039;xxx&#039;,age=&#039;xxx&#039;)
#表中数据筛选删除
UserInfo.objects.filter(name=&#039;xxx&#039;).delete()
#表中数据全部删除
UserInfo.objects.all().delete()
#获取数据
#data_list=[行(对象),行,行] QuerySet类型
data_list=UserInfo.objects.all()
for obj in data_list:
    print(obj.id)
#获取第一行的对象
obj=UserInfo.objects.filter(id=1).first()
print(obj.id)
#更新数据
UserInfo.objects.all().update(name=&#039;xxx&#039;)
UserInfo.objects.filter(id=xxx).update(name=&#039;xxx&#039;)</code></pre>
<h2>案例：用户管理</h2>
<ol>
<li>
<p>展示用户列表</p>
<pre><code class="language-html">&lt;table border=&#039;1&#039;&gt;
&lt;thead&gt;
&lt;tr&gt;
    &lt;th&gt;ID&lt;/th&gt;
    &lt;th&gt;姓名&lt;/th&gt;
    &lt;th&gt;密码&lt;/th&gt;
&lt;/tr&gt;
&lt;/thead&gt;
&lt;tbody&gt;
{%for obj in data_list%}
&lt;tr&gt;
    &lt;td&gt;{{obj.id}}&lt;/td&gt;
    &lt;td&gt;{{obj.name}}&lt;/td&gt;
    &lt;td&gt;{{obj.password}}&lt;/td&gt;
&lt;/tr&gt;
{%endfor%}
&lt;/tbody&gt;
&lt;/table&gt;</code></pre>
</li>
<li>
<p>添加用户</p>
<pre><code class="language-python">#获取用户提交的数据
name=request.POST.get(user)
password=request.POST.get(pwd)
#将数据提交到数据库
UserInfo.objects.create(name=user,password=password)
注:获取数据的HTML页面不要忘记{%csrf_token%}</code></pre>
</li>
<li>
<p>删除用户
<code>&lt;a href=&#039;/info/delete/?nid={{request.GET.get(nid)}}&#039;&gt;删除&lt;/a&gt;</code></p>
</li>
</ol>
<p><strong>补充:在HTML中，<a> 标签定义了一个超链接，它可以用来从一个页面链接到另一个页面，或网站的不同部分，邮件地址，文件等等。<a> 是 “anchor”（锚点）的缩写。