# JavaScript基础入门

## DOM基础

1.1 DOM常见的节点        

| 节点类型 | nodeType值 |
| -------- | ---------- |
| 元素节点 | 1          |
| 属性节点 | 2          |
| 文本节点 | 3          |

1.2 DOM获取元素

```
getElementById('id名');
getElementsByTagName('标签名');   //This is Array
getElementsByClassName('类名');   //ditto
querySelector('选择器');    //满足条件的第一个
querySelectAll('选择器');
getElementsByName('name名');   //only for form element radio checkbox
document.title;
document.body;
```

1.3 DOM创建元素

```
var e1 = document.createElement('元素名'); //创建元素节点
var txt = document.createTextNode('文本文档');  //创建文本节点
e1.appendChild(txt);
document.body.appendChild(e1);
```

1.4 DOM插入元素

```
A.appendChild(B);
A.insertBefore(B,ref);
```

1.5 DOM删除、复制、替换元素

```
A.removeChild(B);  //删除父元素下的子元素
obj.cloneNode(bool);  //obj被复制元素 bool true 为复制其子元素
A.replaceChild(new,old);  //A父元素  new old两为子元素 
```

## DOM进阶

2.1 HTML属性操作

- 获取HTML属性值
- 设置HTML属性值

2.1.1 通过对象属性 进行操作

```
//change the input(text) value to 111
var oTxt = document.getElementById('txt');
oTxt = '111';

//obtain the input(radio) value
var oFruit = document.getElementsByName('fruit');
for(var i =0;i<oFruit.length;i++){
	if(oFruit[i].checked){
		alert(oFruit[i].value);
	}
}

//obtain the input(checkbox) value
var oFruit = document.getElementsByName('fruit');
for(var i =0;i<oFruit.length;i++){
	if(oFruit[i].checked){
		str += oFruit[i].value;
	}
}
alert(oFruit[i].value);

//obtain the select(option) value
var oSelect = document.getElementById('select');
alert(oSelect.value);
```

2.1.2 通过对象方法 进行操作

```
//obtain the data of custom(自定义) input(button) value
var data = oBtn.getAttribute('data');

//set the data to the custom input(button)
oBtn.setAttribute('data','what you want to input');

//delet the the input of attribute value
oBtn.removeAttribute('data');

//judge the input whether has the attribute
oBtn.hasAttribute('data');
```

2.2 CSS属性操作

- 获取CSS属性值
- 设置CSS属性值

```
//obtain the CSS value
getComputedStyle(oBtn).backgroundColor  //attribute中用首字母大写 代替 ‘-’

//set the CSS value
oBtn.style.backgroundColor = 'red';
or
oDiv.style.cssText = "width:100px;height:100px;border:1px solid gray;";
```

2.3 DOM遍历

2.3.1 查找父、子元素

- childNodes、firstChild、lastChild           =>     元素节点 + 文本节点
- children、firstElementChild、lastElementChild          =>           元素节点

```
firstElementChild
children[1];
children[2];
lastElementChild
```

2.3.2 查找兄弟元素

- previousSibling、nextSibling
- previousElementSibling、nextElementSibling

2.3.3 innerHTML 和 innerText

![1571392351762](C:\Users\JiaoLibra\AppData\Roaming\Typora\typora-user-images\1571392351762.png)

## 事件基础

3.1 鼠标事件

```
oBtn.onclick = function(){}
oBtn.onmouseover = function(){}
oBtn.onmouseout = function(){}
oBtn.onmousedown = function(){}
oBtn.onmouseup = function(){}
```

3.2 键盘事件

```
oTxt.onkeydown = function(){}
oTxt.onkeyup = function(){}
```

3.3 表单事件

```
oTxt.focus();
oTxt.onfocus = function(){}
oTxt.onblur = function(){}

oTxt.select(); //full selection form element
oTxt.onselect();

oFruit[i].onchange = function(){}
```

3.4 编辑事件

```
document.body.oncopy = fuction(){return false}  //forbid copy
document.body.onselectstart = function(){return false}   //forbid select
document.body.oncontextmenu = function(){return false}   //forbid 鼠标右键
```

3.5 页面事件

```
window.onload = function(){}
window.onbeforeunload = function(){}
```

## 事件进阶

4.1 事件监听器

​			监听元素某事件的执行 并实现某种功能 如现在onclick只第一次有效

```
//add the listener
oBtn.addEventListener('click',alertMes,false) //alertMes为函数 
//remove the listen
oDiv.removeEventListener('click',changeColor,false)
```

4.2 event对象

​															event对象的属性

| 属性     | 说明            |
| -------- | --------------- |
| type     | 事件类型        |
| keyCode  | 键码值          |
| shiftKey | 是否按下shift键 |
| ctrlKey  | 是否按下ctrl键  |
| altKey   | 是否按下alt键   |

4.3 this

​		哪个DOM对象(元素节点)调用了this所在的喊声，那么this指向的就是哪个DOM对象

## window对象

5.1 window对象

​																window对象下的子对象

| 子对象    | 说明                               |
| --------- | ---------------------------------- |
| document  | 文档对象，用于操作页面元素         |
| location  | 地址对象，用于操作URL地址          |
| navigator | 浏览器对象，用于获取浏览器版本信息 |
| history   | 历史对象，用于操作浏览历史         |
| screen    | 屏幕对象，用于操作屏幕宽度高度     |



5.2 window对象常用方法

​															window对象常用方法

| 方法            | 说明             |
| --------------- | ---------------- |
| alert()         | 提示对话框       |
| confirm()       | 判断对话框       |
| prompt()        | 输入对话框       |
| open()          | 打开窗口         |
| close()         | 关闭窗口         |
| setTimeout()    | 开启一次性定时器 |
| clearTimeout()  | 关闭一次性定时器 |
| setInterval()   | 开启重复性定时器 |
| clearInterval() | 关闭重复性定时器 |

5.3 location对象

​															location对象的属性

| 属性   | 说明                    |
| ------ | ----------------------- |
| href   | 当前页面地址            |
| search | 当前页面地址"?"后的内容 |
| hash   | 当前页面地址"#"后的内容 |

5.4 document对象

​															document对象常用属性

| 属性              | 说明                          |
| ----------------- | ----------------------------- |
| document.title    | 获取文档的title               |
| document.body     | 获取文档的body                |
| document.forms    | 获取所有的form元素            |
| document.images   | 获取所有的img元素             |
| document.links    | 获取所有的a元素               |
| document.cookie   | 文档的cookie                  |
| document.URL      | 当前文档的URL                 |
| document.referrer | 返回使浏览者到达当前文档的URL |

