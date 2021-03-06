# SublimePHPNinJaManual
Sublime中的函数手册提示，中文，其他语言的可以通过命令生成

## 由来
自己因为sublime中没有一个好的php函数提示所苦恼。曾经在Sublime的thinkphp插件里实现过一次，![](https://camo.githubusercontent.com/759b876842251b13854ff35267cc005b39d0ddb8/687474703a2f2f7777772e7468696e6b7068702e636e2f55706c6f6164732f7370656563682f323031332d30382d30342f353166653061613430636134302e706e67) ![](https://camo.githubusercontent.com/4749d5a82cd9e4cba79622833f3e0c7699bf5ba7/687474703a2f2f7777772e7468696e6b7068702e636e2f55706c6f6164732f7370656563682f323031332d30382d30342f353166653062646361333036632e706e67) 那个时候用的是netbeans 里 php提示的文件库，然后显示也不大好看。一直以为sublime 没法做到好看的ui 因为api少。

前几天发现了国人的自己做的[Ctranslator tool](https://packagecontrol.io/packages/Ctranslator%20tool) ![](https://packagecontrol.io/readmes/img/927f757b88e0448227a2db8f9e312a9686eea391.gif) 这不就是我想要的吗？看源码发现是用了一个开源的库 [StyledPopup](https://github.com/huot25/StyledPopup)。 用html灵活多了。

而后，自己其实一直用的chrome 浏览器的插件，PHP NanJa Manual。支持各种语言，也有示列，就是每次写代码开浏览器太麻烦了。由于他提供一个开源库[PHP doc parser](https://github.com/martinsik/php-doc-parser)，可以将php官方手册转换成json文件，自己就有了移植的想法。
![](https://raw.githubusercontent.com/martinsik/php-doc-parser/master/doc/animation.gif)
所以名字就参考了他的，希望不要告侵权。
由于son文件过于大，python没有缓存机制（或许我不知道），我就用thinkphp 转成了一个db。2个表 fun、funlist  fun存 函数名， funlist存 函数名和对应son数据。
## 安装
使用Sublime Text 3 Package Control 插件(http://wbond.net/sublime\_packages/package\_control) 按 CTRL + SHIFT + P 后 找到 _Package Control: Install Package_ 然后回车。列表中找到**PhpNinJaManual**这个插件（等审核过了会有）。

或者直接 git clone 到你的 Sublime Text 3 packages 目录 (usually located at /Sublime Text 3/Packages/)。记得把SublimePHPNinJaManual 改为PhpNinJaManual。pac 安装的应该没这个问题。

## 使用说明
选中要查看的php函数名，然后右键会发现 “查看函数说明”菜单![](http://ww3.sinaimg.cn/mw1024/50075709gw1eweqa43989j20c40e077h.jpg) ，点击后，
会弹出函数说明浮层 ![](http://ww3.sinaimg.cn/mw1024/50075709gw1eweqagrellj20dn08e40j.jpg)
## 关于手册其他语言的生成
拿英文 en 举例。
先到 手册解析器主页：https://github.com/martinsik/php-doc-parser
找一个目录 写上composer.json 
内容：

{
“require”: {
  ...
  "martinsik/php-doc-parser": "~2.0"
}
}

然后 `composer.phar install` 也可能 composer install
装好后， 当前目录vendor/bin 下会有![](http://ww3.sinaimg.cn/mw1024/50075709gw1eweqbqozgtj208c03w0sq.jpg) 执行文件，然后 

`vendor/bin/doc-parser help parser:run`
![](https://raw.githubusercontent.com/martinsik/php-doc-parser/master/doc/animation.gif)
生成好这2个json文件后， 复制到，插件目录的 App/Runtime/Data里，![](http://ww1.sinaimg.cn/mw1024/50075709gw1eweqeagv1bj208503dglk.jpg) 到时候就不是zh 而是en。
然后 命令行切换到插件目录里执行 

![](http://ww4.sinaimg.cn/mw1024/50075709gw1eweqevv5xpj20fy01lwex.jpg)

会提示多少函数导入了。我没生成英文的，所以是0。
## 未来特性
可能会用PHPConnector 重构下
## 注意点
- 有的函数因为返回了&$count 这类Sublime插件语言中的关键字导致解析不了向后的html字符串![](http://ww1.sinaimg.cn/mw1024/50075709gw1eweqfm5h0tj20az04a0to.jpg)。暂时不知道怎么修复
- 由于那个浮层组件不支持设定宽高，目前长内容会出现滚动条，只能等作者解决了，我会向他提Issue的。
- 解析手册用的是PHP，需要你们的 命令行里php 可用，所有， 最好检查下自己的系统环境变量或者聪明的里 php -v 能不能用
- 
- 
- 
## 有问题反馈
在使用中有任何问题，欢迎反馈给我，可以用以下联系方式跟我交流

* 邮件(yangweijiest#gmail.com, 把#换成@)
* QQ: 917647288
* weibo: [@黑白世界4648](http://weibo.com/1342658313)
* 人人: [@杨维杰](http://www.renren.com/247050624)
## 关于作者

	var code-tech = {
	    nickName  : "杨维杰",
	    site : "http://code-tech.diandian.com"
	}
