<!-- wp:paragraph -->
<p>转载于：<a href="https://blog.csdn.net/clearloe/article/details/139879493">Hexo 博客搭建并部署到 GitHub Pages(2024最新详细版)-CSDN博客</a>（略有删改-适合纯小白）</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":4} -->
<h4 class="wp-block-heading"><a></a><a></a>前置条件</h4>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>本机已安装好 Git 和 Node.js ，Node 版本一定不要最新的22版本(会出现各种奇怪的问题)，建议16和18稳定版本。</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p><a href="https://git-scm.com/">Git 安装</a></p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p><a href="https://nodejs.org/zh-cn">Node.js 安装</a></p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>补充：安装完后可以输入以下代码来查询对应版本号，以便检查git与nodejs是否成功安装。</p>
<!-- /wp:paragraph -->

<!-- wp:code -->
<pre class="wp-block-code"><code>git -v
node -v</code></pre>
<!-- /wp:code -->

<!-- wp:image {"id":23,"sizeSlug":"full","linkDestination":"none"} -->
<figure class="wp-block-image size-full"><img src="http://mfazr47fernyco.kltu.top/wp-content/uploads/2024/06/image-2.png" alt="" class="wp-image-23"/></figure>
<!-- /wp:image -->

<!-- wp:heading {"level":4} -->
<h4 class="wp-block-heading"><a></a><a></a>1.安装 Hexo</h4>
<!-- /wp:heading -->

<!-- wp:code -->
<pre class="wp-block-code"><code>npm install hexo-cli -g
</code></pre>
<!-- /wp:code -->

<!-- wp:paragraph -->
<p>终端执行<code>hexo -version</code>出现 Hexo 版本号，说明安装成功</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":44,"sizeSlug":"full","linkDestination":"none"} -->
<figure class="wp-block-image size-full"><img src="http://mfazr47fernyco.kltu.top/wp-content/uploads/2024/06/image-3.png" alt="" class="wp-image-44"/></figure>
<!-- /wp:image -->

<!-- wp:heading {"level":4} -->
<h4 class="wp-block-heading"><a></a><a></a>2.本地建站</h4>
<!-- /wp:heading -->

<!-- wp:heading {"level":5} -->
<h5 class="wp-block-heading">2.1 初始化</h5>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>自建文件夹后在需要创建博客的位置右键选择Open Git Bash here:</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":21,"width":"643px","height":"auto","sizeSlug":"full","linkDestination":"none"} -->
<figure class="wp-block-image size-full is-resized"><img src="http://mfazr47fernyco.kltu.top/wp-content/uploads/2024/06/2024-06-27.png" alt="" class="wp-image-21" style="width:643px;height:auto"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>找到要存放博客的目录，进入终端执行：</p>
<!-- /wp:paragraph -->

<!-- wp:code -->
<pre class="wp-block-code"><code> hexo init myblog
 cd myblog
 npm install
</code></pre>
<!-- /wp:code -->

<!-- wp:paragraph -->
<p>初始化成功显示：</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":46,"sizeSlug":"large","linkDestination":"none"} -->
<figure class="wp-block-image size-large"><img src="http://mfazr47fernyco.kltu.top/wp-content/uploads/2024/06/image-4-1024x115.png" alt="" class="wp-image-46"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>vscode 打开 myblog，项目目录如下：<br></p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":48,"sizeSlug":"full","linkDestination":"none"} -->
<figure class="wp-block-image size-full"><img src="http://mfazr47fernyco.kltu.top/wp-content/uploads/2024/06/image-5.png" alt="" class="wp-image-48"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p><code>_config.yml</code>&nbsp;存放的是博客配置信息，&nbsp;<code>source/_posts</code>&nbsp;是存放文章的地方。</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":5} -->
<h5 class="wp-block-heading"><a></a>2.2预览</h5>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>打开终端，进入项目根目录执行：</p>
<!-- /wp:paragraph -->

<!-- wp:code -->
<pre class="wp-block-code"><code>hexo clean <em># 清除缓存文件，建议写完文章后执行一次</em>
hexo g		<em># 生成 public 文件夹，写完文章执行</em>
hexo s		<em># 启动 hexo 服务</em>
</code></pre>
<!-- /wp:code -->

<!-- wp:image {"id":49,"width":"913px","height":"auto","sizeSlug":"large","linkDestination":"none"} -->
<figure class="wp-block-image size-large is-resized"><img src="http://mfazr47fernyco.kltu.top/wp-content/uploads/2024/06/g7a41mz8-1024x111.png" alt="" class="wp-image-49" style="width:913px;height:auto"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph {"fontSize":"medium"} -->
<p class="has-medium-font-size">浏览器访问 http://localhost:4000/ 出现下图说明启动成功<br></p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":18,"width":"917px","height":"auto","sizeSlug":"large","linkDestination":"none"} -->
<figure class="wp-block-image size-large is-resized"><img src="http://mfazr47fernyco.kltu.top/wp-content/uploads/2024/06/image-1024x576.png" alt="" class="wp-image-18" style="width:917px;height:auto"/></figure>
<!-- /wp:image -->

<!-- wp:heading {"level":4} -->
<h4 class="wp-block-heading"><a></a><a></a>3.更换主题</h4>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>去<a>主题官网</a>，里面有上百种主题，这里选择&nbsp;<a href="https://github.com/fluid-dev/hexo-theme-fluid">Fluid 主题</a>，也是我个人在用的。</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>执行命令，将主题安装到<code>myblog</code>根目录</p>
<!-- /wp:paragraph -->

<!-- wp:code -->
<pre class="wp-block-code"><code>npm install --save hexo-theme-fluid
</code></pre>
<!-- /wp:code -->

<!-- wp:paragraph -->
<p>然后在博客目录下创建&nbsp;<code>_config.fluid.yml</code>，将 Fluid 主题的&nbsp;<a href="https://github.com/fluid-dev/hexo-theme-fluid/blob/master/_config.yml">_config.yml</a>&nbsp;内容复制进去(打开链接复制)。</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":50,"sizeSlug":"large","linkDestination":"none"} -->
<figure class="wp-block-image size-large"><img src="http://mfazr47fernyco.kltu.top/wp-content/uploads/2024/06/image-6-1024x342.png" alt="" class="wp-image-50"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>后续修改博客的配置，例如标题，头像，评论等等只需要在&nbsp;<code>_config.fluid.yml</code>文件中配置就行。</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":5} -->
<h5 class="wp-block-heading"><a></a>3.1指定主题</h5>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>如下修改<code>myblog</code>博客目录中的&nbsp;<code>_config.yml</code>：</p>
<!-- /wp:paragraph -->

<!-- wp:code -->
<pre class="wp-block-code"><code>theme: fluid  <em># 指定主题</em>
language: zh-CN  <em># 指定语言，会影响主题显示的语言，按需修改</em>
</code></pre>
<!-- /wp:code -->

<!-- wp:heading {"level":5} -->
<h5 class="wp-block-heading"><a></a>3.2创建关于页面</h5>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>首次使用主题的「关于页」需要手动创建：</p>
<!-- /wp:paragraph -->

<!-- wp:code -->
<pre class="wp-block-code"><code>hexo new page about
</code></pre>
<!-- /wp:code -->

<!-- wp:paragraph -->
<p>创建成功后，编辑博客目录下&nbsp;<code>/source/about/index.md</code>，添加&nbsp;<code>layout</code>&nbsp;属性。</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>修改后的文件示例如下：</p>
<!-- /wp:paragraph -->

<!-- wp:code -->
<pre class="wp-block-code"><code>---
title: about
layout: about
---

这是关于页面
</code></pre>
<!-- /wp:code -->

<!-- wp:heading {"level":5} -->
<h5 class="wp-block-heading"><a></a>3.3启动</h5>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>终端执行：</p>
<!-- /wp:paragraph -->

<!-- wp:code -->
<pre class="wp-block-code"><code>hexo clean <em># 清除缓存文件，建议写完文章后执行一次</em>
hexo g		<em># 生成 public 文件夹，写完文章执行</em>
hexo s		<em># 启动 hexo 服务</em>
</code></pre>
<!-- /wp:code -->

<!-- wp:paragraph -->
<p>浏览器访问 http://localhost:4000/ 出现下图说明主题启动成功</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":51,"width":"919px","height":"auto","sizeSlug":"large","linkDestination":"none"} -->
<figure class="wp-block-image size-large is-resized"><img src="http://mfazr47fernyco.kltu.top/wp-content/uploads/2024/06/image-7-1024x577.png" alt="" class="wp-image-51" style="width:919px;height:auto"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>至此本地搭建全部完成，下面介绍如何部署到 GitHub Pages 上，让别人看到你的博客。</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":4} -->
<h4 class="wp-block-heading"><a></a><a></a>4.部署到 GitHub Pages</h4>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>登录 GitHub，新建一个 Repository，<code>Repository name</code>一定要是<code>你的用户名</code>.github.io</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":52,"width":"692px","height":"auto","sizeSlug":"large","linkDestination":"none"} -->
<figure class="wp-block-image size-large is-resized"><img src="http://mfazr47fernyco.kltu.top/wp-content/uploads/2024/06/image-8-1024x716.png" alt="" class="wp-image-52" style="width:692px;height:auto"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>打开博客目录下的<code>_config.yml</code>，拉到最后，填写<code>deploy</code>模块：<code>repository</code>&nbsp;填写你的仓库的链接（注：仓库名格式为"你的github用户名.github.io"）<br></p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":19,"width":"786px","height":"auto","sizeSlug":"large","linkDestination":"none"} -->
<figure class="wp-block-image size-large is-resized"><img src="http://mfazr47fernyco.kltu.top/wp-content/uploads/2024/06/image-1-1024x404.png" alt="" class="wp-image-19" style="width:786px;height:auto"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>一定要安装 Git 插件：</p>
<!-- /wp:paragraph -->

<!-- wp:code -->
<pre class="wp-block-code"><code> npm install hexo-deployer-git --save
</code></pre>
<!-- /wp:code -->

<!-- wp:paragraph -->
<p>现在可以将博客部署上去了，执行</p>
<!-- /wp:paragraph -->

<!-- wp:code -->
<pre class="wp-block-code"><code> hexo c &amp;&amp; hexo g &amp;&amp; hexo d  <em># hexo d 表示执行部署</em>
</code></pre>
<!-- /wp:code -->

<!-- wp:paragraph -->
<p>补充：hexo d的时候可能会出现错误，请确认你已完成过如下操作</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2 class="wp-block-heading"><strong>四、设置ssh</strong></h2>
<!-- /wp:heading -->

<!-- wp:heading {"level":4} -->
<h4 class="wp-block-heading"><a></a><strong>1.生成sshkey</strong></h4>
<!-- /wp:heading -->

<!-- wp:quote -->
<blockquote class="wp-block-quote"><!-- wp:paragraph -->
<p><strong>首先在git下</strong><br><strong>输入命令：cd ~/.ssh进入.ssh文件</strong><br><strong>输入命令：ssh-keygen -t rsa -C ‘注册时的邮箱地址’</strong></p>
<!-- /wp:paragraph --></blockquote>
<!-- /wp:quote -->

<!-- wp:paragraph -->
<p><strong>接着去查看C盘目录(此文件夹所在C:\用户\用户名目录下)，</strong><strong>然后在记事本中打开</strong><strong>id_rsa.put</strong><strong>文件并复制生成的key</strong></p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":4} -->
<h4 class="wp-block-heading"><a></a><strong>2.将key配置到GitHub中</strong></h4>
<!-- /wp:heading -->

<!-- wp:quote -->
<blockquote class="wp-block-quote"><!-- wp:paragraph -->
<p><strong>在GitHub主页的头像下找到seething</strong></p>
<!-- /wp:paragraph --></blockquote>
<!-- /wp:quote -->

<!-- wp:quote -->
<blockquote class="wp-block-quote"><!-- wp:paragraph -->
<p><strong>&nbsp;然后点击SSH and GPG keys，点击New SSH key</strong></p>
<!-- /wp:paragraph --></blockquote>
<!-- /wp:quote -->

<!-- wp:quote -->
<blockquote class="wp-block-quote"><!-- wp:paragraph -->
<p>&nbsp;<strong>将刚刚在.ssh目录下所复制的id_rsa.put文件中的信息复制进key(注意空格)（名字随意）</strong></p>
<!-- /wp:paragraph --></blockquote>
<!-- /wp:quote -->

<!-- wp:heading {"level":3} -->
<h3 class="wp-block-heading"><a></a><strong>验证：</strong>&nbsp;</h3>
<!-- /wp:heading -->

<!-- wp:quote -->
<blockquote class="wp-block-quote"><!-- wp:paragraph -->
<p><strong>输入命令（git）：ssh -T git@github.com 并且输入yes之后，行末尾会显示你的用户名</strong></p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p><strong>（绑定成功邮箱会收到邮件提醒）</strong></p>
<!-- /wp:paragraph --></blockquote>
<!-- /wp:quote -->

<!-- wp:quote -->
<blockquote class="wp-block-quote"><!-- wp:paragraph -->
<p><strong>接着在本地绑定与Github的用户名和邮箱（git）</strong><br><strong>输入命令：git config --global user.name “注册时用户名”</strong><br><strong>输入命令：git config --global user.email “注册时邮箱”</strong></p>
<!-- /wp:paragraph --></blockquote>
<!-- /wp:quote -->

<!-- wp:paragraph -->
<p>执行成功可以通过&nbsp;<code>你的用户名</code>.github.io 来访问博客了，例如：maplelea1f.github.io。</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>至此搭建博客并部署已全部完成。</p>
<!-- /wp:paragraph -->