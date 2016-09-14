# browser-compatible-
关于前端遇到的浏览器兼容性的问题

## 为什么会有兼容性问题
为什么会有兼容问题？
由于市场上浏览器种类众多，而不同浏览器其内核亦不尽相同，所以各个浏览器对网页的解析就有一定出入，这也是导致浏览器兼容问题出现的主要原因，我们的网页需要在主流浏览器上正常运行，就需要做好浏览器兼容。

```
使用Trident内核的浏览器：IE、Maxthon、TT；

使用Gecko内核的浏览器：Netcape6及以上版本、FireFox；

使用Presto内核的浏览器：Opera7及以上版本；

使用Webkit内核的浏览器：Safari、Chrome。
```

兼容性问题，关于兼容性问题，主要是说IE与几个主流浏览器如firefox，google等

### javascript兼容性问题
① 在标准的事件绑定中绑定事件的方法函数为 addEventListener，而IE使用的是attachEvent。

② 标准浏览器采用事件捕获的方式对应IE的事件冒泡机制（即标准由最外元素至最内元素或者IE由最内元素到最外元素）最后标准方亦觉得IE这方

面的比较合理，所以便将事件冒泡纳入了标准，这也是addEventListener第三个参数的由来，而且事件冒泡作为了默认值。

③ 事件处理中非常有用的event属性获得亦不相同，标准浏览器是作为参数带人，而ie是window.event方式获得，获得目标元素ie为e.srcElement

标准浏览器为e.target。

④ 然后在ie中是不能操作tr的innerHtml的

⑤ 然后ie日期函数处理与其它浏览器不大一致，比如： var year= new Date().getYear();

在IE中会获得当前年，但是在firefox中则会获得当前年与1900的差值。

⑥  获得DOM节点的方法有所差异，其获得子节点方法不一致。

IE：parentElement parentElement.children ； Firefox：parentNode parentNode.childNodes

childNodes的下标的含义在IE和Firefox中不同，Firefox使用DOM规范，childNodes中会插入空白文本节点。一般可以通过node.getElementsByTagName()来回避这个问题。

当html中节点缺失时，IE和Firefox对parentNode的解释不同。例如:

<form>  <table>   <input/>  </table> </form> IE：input.parentNode的值为空节点； Firefox：input.parentNode的值为form

解决方法：Firefox中节点没有removeNode方法，必须使用如下方法 node.parentNode.removeChild(node)

⑦ 关于AJAX的实现上亦有所不同；

我们开发过程中一般都会使用类库，若是不使用，都会自己积累形成一个类库，所以就js而言，兼容性问题基本解决了。

### CSS兼容
CSS Hack的知识，水平高的人可以不用这种方式
```
/* CSS属性级Hack */ 
 
color:red; /* 所有浏览器可识别*/ 
 
_color:red; /* 仅IE6 识别 */ 
 
*color:red; /* IE6、IE7 识别 */ 
 
+color:red; /* IE6、IE7 识别 */ 
 
*+color:red; /* IE6、IE7 识别 */ 
 
[color:red; /* IE6、IE7 识别 */ 
 
color:red\9; /* IE6、IE7、IE8、IE9 识别 */ 
 
color:red\0; /* IE8、IE9 识别*/ 
 
color:red\9\0; /* 仅IE9识别 */ 
 
color:red \0; /* 仅IE9识别 */ 
 
color:red!important; /* IE6 不识别!important 有危险*/
 
/* CSS选择符级Hack */ 
 
*html #demo { color:red;} /* 仅IE6 识别 */ 
 
*+html #demo { color:red;} /* 仅IE7 识别 */ 
 
body:nth-of-type(1) #demo { color:red;} /* IE9+、FF3.5+、Chrome、Safari、Opera 可以识别 */ 
 
head:first-child+body #demo { color:red; } /* IE7+、FF、Chrome、Safari、Opera 可以识别 */ 
 
:root #demo { color:red\9; } : /* 仅IE9识别 */
 
/* IE条件注释Hack */ 
 
<!--[if IE 6]>此处内容只有IE6.0可见<![endif]--> 
 
<!--[if IE 7]>此处内容只有IE7.0可见<![endif]-->
```

待后续更新···
