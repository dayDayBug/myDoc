



## html（hyper text mark language）

### 3、表单：收集用户信息

- 表单域：这一个大区域

- 表单控件（表单元素）：一些控件

- 提示信息：控件的提示信息，比如 用户名后面有一个文本框，输入文本设计用户名

#### 3.1、表单域

主要作用：将表单域里的值记录下来，以 $method$ 的方法把 $name$ 送入 $action$ 网页进行处理。

```html
<form action="demo.php" method="post" name="name1"></form>
```

#### 3.2、表单控件

这些表单元素就是允许用户输入或者选择的内容控件

- input 输入表单元素
- select 下拉表单元素
- textarea 文本域元素

##### 3.2.1  \<input> 表单元素

\<input> 标签用于收集用户信息，是一个单标签，如下代码表示的就是用户输入一个 $type$ 类型的数据：

```html
<form action="demp.php" method="post" name="name1"> 
    <!-- 表单控件（表单元素）里的 name 是表单控件的名字  value 是表单控件的默认值 只有在文本模式下才会显示 -->
    <!-- name 和 value 是每个表单元素都有的属性值，只要供后台开发人员使用 -->
    <!-- 表单控件里的单选框和复选框要有相同的 name 值 -->

    <!-- text  文本框  用户输入文本内容 -->
    用户名: <input type="text" name="username" value="请输入用户名"> <br>
    <!-- password  密码框  用户看不见输入的密码 -->
    密码: <input type="password" name="pwd" value="111"> <br>
    <!-- radio   单选框  这里的性别单选必须要有相同的name才可以实现多选一 -->
    性别: 男<input type="radio" name="sex" value="男"> 女: <input type="radio" name="sex" value="sex">
    <!-- checkbox  复选框  可以实现多选一 -->
    爱好: 跑步<input type="checkbox" name="hobby" value="running">
          跑步<input type="checkbox" name="hobby" value="running">
          跑步<input type="checkbox" name="hobby" value="running">

</form>
```



type属性表：

| type属性 |                           说明                           |
| :------: | :------------------------------------------------------: |
|   text   |                         输入文本                         |
|  radio   |       一个单选框，加上name才会实现真正意义上的单选       |
| checkbox |                 一个复选框，可以实现多选                 |
| password |            实现输入的隐藏，一般用在密码输入上            |
|  submit  |      定义提交按钮，提交之后会把表单数据发送到服务器      |
|  reset   | 定义重置按钮，清除表单中所有设定好的的数据，回到初始状态 |
|  button  |               普通按钮，后期结合js实现使用               |
|   file   |                   文件域，上传文件使用                   |

input 输入属性表：

| input属性 |    属性值    |          描述          |
| :-------: | :----------: | :--------------------: |
|   name    | 由用户自定义 |   定义表单控件的名称   |
|   value   | 由用户自定义 |  规定表单控件的默认值  |
|  checked  |   checked    | 单选框或复选框的默认值 |
| maxlength |    正整数    | 规定输入字段的最大长度 |

##### 3.2.2 \<label> 标签

作用：提升用户体验

\<label> 在 input 元素之后标注

\<label> 标签用于绑定一个表单控件，当点击 \<label> 标签内文本时，浏览器就会将光标定位到绑定的表单控件上

```html
<form action="demp.php" method="post" name="name1"> 
    性别: <input type="radio" name="sex" id="male"> <label for="male">男</label> 
          <input type="radio" name="sex" id="female"> <label for="female">女</label> 
</form>
```

##### 3.2.3 \<select> 表单元素

作用：下拉列表

```html
<form action="demp.php" method="post" name="name1"> 
    籍贯:
    <select>
        <option selected="selected">江苏</option>
        <option>山东</option>
        <option>安徽</option>
    </select>
</form>
```

注意：

- \<select> 中至少包含一个 \<option> 选项；
- 设定下拉列表默认选项时，\<option> 中定义一个 selected="selected" 即可。

##### 3.2.4 \<textarea> 文本域标签

当用户输入的内容较多的时候，不能再使用文本框表单了，此时可以使用 \<textarea> 标签

其支持多行文本的输入，该表单控件多见于留言板，评论。



## CSS

### 选择器

- 单项选择器
- 复合选择器

### 复合选择器

#### 1.6、链接伪类选择器

```css
a: link    			/*选择所有未被访问的链接*/
a: visited			/*选择所有已经被访问的链接*/
a: hover			/*选择鼠标指针位于其上方的链接*/
a: active			/*选择活动链接（鼠标按下未弹起的），*/
```

注意事项：

- 为了确保生效，按照 $link-vistied-hover-active$ 顺序去定义
- 需要给链接单独指定样式，因为a链接在浏览器中有默认样式
- 通常的链接样式是：一个链接平时的样式，一个是hover时的样式

#### 1.7、focus伪类选择器

用于选取获得焦点的表单元素

焦点就是光标，一般情况\<input>类表单元素才能获取，因此这个选择器也主要针对表单元素而言

```css
/*将光标所在的表单控件背景色设置为黄色*/
input:focus {
	background-color: yellow;
}
```



#### 1.8、复合选择器总结

| 选择器         | 作用               | 特征             | 使用情况 | 用法                       |
| -------------- | ------------------ | ---------------- | -------- | -------------------------- |
| 后代选择器     | 选择后代元素       | 可以是子孙的后代 | 较多     | 符号是 **空格** .nav a     |
| 子类选择器     | 选择嫡子元素       | 只选嫡子         | 较少     | 符号是 **>**.nav > p       |
| 并集选择器     | 选择某些相同的元素 | 可以集体声明     | 较多     | 符号是**逗号** .nav, .head |
| 链接伪类选择器 | 选择不同状态的链接 | 链接相关         | 较多     | a{} 和 a:hover 开发最常用  |
| :focus选择器   | 选择获得光标的表单 | 表单相关         | 较少     | input:focus 记住这个写法   |

