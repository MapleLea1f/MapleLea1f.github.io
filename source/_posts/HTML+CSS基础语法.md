# html基本语法：
 1. <标签名 属性="值">被标记的内容</标签名>
 2. <标签名 属性="值/>

# CSS基础语法

CSS全称层叠样式表(Cascading Style Sheets） ，主要用来定义页面内容展示效果的一门语言。

- HTML:页面骨架
- CSS:页面效果美化

CSS语法规则：
1. 通过style属性来编写样式
2. 通过style标签.然后使用选择器的形式来编写样式
3. 在css文件中编写样式，通过link引入该文件

CSS选择器(重点)
1. id选择器 #
`#a{color:pink;}`
2. 标签选择器 标签
`li{border: 1px solid red;}`
3. 类选择器 .
`<div class='a'></div>`
`.a{color:green;}`
4. 选择器分组 ,
`div,span{background:pink;}`
5. 后代选择器 空格
`ul li{color:red;}`
`#即ul中的li，包括所有嵌套后的li`
6. 子选择器 >
`ul > li{list-style:none;}`
`#仅子代一层嵌套`
7. 相邻选择器 +
`h1 + h2{color:red;}`
`#即仅和h1相邻的h2会被选择`
8. 属性选择器 [属性=值]
`<a href='#' target='xxx' rel="noopener">xxx</a>`
`a[target='xxx']{text-decoration:none;}`