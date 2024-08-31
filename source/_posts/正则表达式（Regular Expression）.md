```yaml
---
title: 正则表达式学习笔记
tags: [re,正则]
index_img: /img/example.jpg
date: 2019-10-10 10:00:00
---
```

<h2 class="wp-block-heading">正则表达式知识点：</h2>
<p>笔记整理于教程：<a href="https://www.bilibili.com/video/BV1da4y1p7iZ/?spm_id_from=333.337.search-card.all.click&amp;vd_source=2534f27c272e6223a9b16472095383f4">10分钟快速掌握正则表达式_哔哩哔哩_bilibili</a></p>

<h3 class="wp-block-heading">限定符(Qualifiers)</h3>
<p>?--前面的字符出现1次或者0次</p>
<p>eg:used?--&gt;use/used</p>

<p>*--匹配0个或多个字符</p>
<p>eg:ab*c--&gt;ac/abc/abbbbbc</p>
<p></p>
<p>+--匹配出现1次及以上的字符</p>
<p>eg:ab+c--&gt;abc/abbbbbc</p>

<p>{}--精确匹配出现次数或出现次数的范围</p>
<p>eg:ab{6}c--&gt;abbbbbbc,即b出现6次</p>
<p>eg:ab{2,6}--&gt;abbbc,即b出现2~6次</p>
<p>eg:ab{2,}--&gt;abbc,即b出现2次及以上</p>


<p>()--匹配多字符重复</p>
<p>eg:(ab)+--&gt;ababab</p>


<h3 class="wp-block-heading">“或”运算(OR Operator)</h3>
<p>|--或</p>
<p>eg:a (cat|dog)--&gt;a cat/a dog</p>
<p>eg:a cat|dog--&gt;a cat/dog</p>
<p></p>
<h3 class="wp-block-heading">字符类(Character Classes)</h3>
<p>[]--匹配的字符只能取自于[]中的内容</p>
<p>eg:[abc]+--&gt;abc/aabbcc</p>
<p>eg:[a-zA-Z0-9]+--&gt;所有的英文字符和数字</p>
<p>eg:[^0-9]+--&gt;所有的非数字字符（包括换行符）</p>
<p></p>
<p>[^]--匹配的字符全部不取自于[^]中的内容</p>
<p>eg:[^a-z]+--&gt;所有不是a-z的内容</p>

<h3 class="wp-block-heading">元字符(Meta-characters)</h3>
<p>\d--数字字符(digit)</p>
<p>\w--单词字符：英文、数字及下划线(word)</p>
<p>\s--空白符：Tab和换行符(space)</p>
<p>\D--非数字字符</p>
<p>\W--非单词字符</p>
<p>\S--非空白字符</p>
<p>.--任意字符(除换行符)</p>


<p>^--匹配行首</p>
<p>eg:^a--&gt;匹配行首的a,即<mark style="background-color:rgba(0, 0, 0, 0)" class="has-inline-color has-vivid-red-color"><strong><em>a</em></strong></mark>213y19239812aduag1</p>

<p>$--匹配行尾</p>
<p>eg:a$--&gt;匹配行尾的a，即a8231hsaasd<mark style="background-color:rgba(0, 0, 0, 0)" class="has-inline-color has-vivid-red-color"><strong><em>a</em></strong></mark></p>


<h3 class="wp-block-heading">贪婪与懒惰匹配(Greedy vs Lazy Match)</h3>
<p>*+{}在匹配字符串时默认会匹配尽可能多的字符</p>


<p>贪婪eg:&lt;.+&gt; --&gt; <strong><em>&lt;span&gt;&lt;b&gt;This is a simple text&lt;/b&gt;&lt;/span&gt;</em></strong></p>
<p>懒惰eg:&lt;.+?&gt; --&gt; <strong><em>&lt;span&gt;&lt;b&gt;</em></strong>This is a simple text<strong><em>&lt;/b&gt;&lt;/span&gt;</em></strong></p>

<h3 class="wp-block-heading">正则表达式实例问题：</h3>

<h4 class="wp-block-heading">实例1——RGB颜色值匹配(匹配文本中出现的所有十六进制RGB颜色值)</h4>
<p><em>补充：十六进制RGB颜色系统中#FFFFFF表示白色(最大红色R、最大绿色G、最大蓝色B)</em></p>
<p>#00</p>
<p>#fffff</p>
<p>#ffaaff</p>
<p>#00hh00</p>
<p>#aabbcc</p>
<p>#000000</p>
<p>#ffffffff</p>


<p>answer:#[a-fA-F0-9]{6}\b </p>
<p><strong>注：\b表示单词字符的边界</strong></p>

<h4 class="wp-block-heading">实例2——IPv4地址匹配</h4>
<p><em>补充：IPv4(Internet Protocol version 4)是一个32位的数字，有四个由点分隔的十进制数，每个数的范围是0到255，形如：192.168.1.1</em></p>
<p>123</p>
<p>255.255.255.0</p>
<p>192.168.0.1</p>
<p>0.0.0.0</p>
<p>256.1.1.1</p>
<p>This is a string.</p>
<p>123.123.0</p>

<p>answer1: \d+\.\d+\.\d+\.\d+ --&gt;基础答案:只能匹配数字字符和.</p>
<p>answer2: \b(25[0-5]|2[0-4]\d|[01]?\d\d?\.){3}25[0-5]|2[0-4]\d|[01]?\d\d?\b</p>
<p><strong>注：\.中的\表示转义符号，因为.本身表示任意字符</strong></p>

<h2 class="wp-block-heading">END</h2>