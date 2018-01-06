HTML属性链接


HTML链接<a>标签定义。链接的地址在href属性中指定
<a href="http://a210.club">我的博客</a>
在所有浏览器中，链接的默认外观如下：
  ●未被访问的链接带有下划线而且是蓝色的
  ●已被访问的链接带有下划线而且是紫色的
  ●活动链接带有下划线而且是红色的

将图像作为链接
<p>图像作为链接
<a href="http://a210.club"><img border="0" alt="a210" src="图片地址:" width="100" height="100"></a>
</p>


target属性设置_blank----链接在新窗口打开
<a href="http://a210.club" target="_blank" >访问a210.club</a>

属性 	        描述
class 	为html元素定义一个或多个类名（classname）(类名从样式文件引入)
id 	        定义元素的唯一id
style 	        规定元素的行内样式（inline style）
title 	        描述了元素的额外信息 (作为工具条使用)

<!DOCTYPE>声明位于文档中的最前面的位置，处于<HTML>标签之前
<!DOCTYPE>声明不是一个HTML标签，它是用来告知web浏览器页面使用了哪种HTML版本
在HTML 4.01中，<!DOCTYPE>声明需引用DTD（document type definition），因为HTML 4.01是基于
SGML（standard Generalized markup language标准通用标记语言）。DTD（文档类型声明）指定了标记语言的规
则，确保了浏览器能够正确的渲染内容。

HTML5不是基于SGML，因此不要求引用DTD（文档类型声明）