# Markdown语法

## 1.标题

### 1.1 示例

```javascript
# 这是一级标题
## 这是二级标题
### 这是三级标题
#### 这是四级标题
##### 这是五级标题
###### 这是六级标题
```

### 1.2 效果

- # 这是一级标题
  ## 这是二级标题
  ### 这是三级标题
  #### 这是四级标题
  ##### 这是五级标题
  ###### 这是六级标题

## 2.字体

### 2.1 示例

```javascript
**这是加粗的文字**
*这是倾斜的文字*
***这是斜体加粗的文字***
~~这是加删除线的文字~~
```

### 2.2 效果

**这是加粗的文字**
*这是倾斜的文字*
***这是斜体加粗的文字***
~~这是加删除线的文字~~

## 3.引用

### 3.1 示例

```javascript
>这是引用的内容
>>这是引用的内容
>>>>>>>>>>这是引用的内容
```

### 3.2 效果

>这是引用的内容
>>这是引用的内容
>>
>>>>>>>>>>这是引用的内容

## 4.分割线

### 4.1 示例

```javascript
---
----
***
*****
```

### 4.2 效果

---
----
***
*****

## 5.图片

### 5.1语法

```javascript
![图片alt](图片地址 "图片title")

图片alt就是显示在图片下面的文字，相当于对图片内容的解释。
图片title是图片的标题，当鼠标移到图片上时显示的内容。title可加可不加
```

### 5.2 示例

```javascript
![blockchain](https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=702257389,1274025419&fm=27&gp=0.jpg
"区块链")
```

### 5.3 效果

![blockchain](https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=702257389,1274025419&fm=27&gp=0.jpg
"区块链")

## 6.超链接

### 6.1 语法

```javascript
[超链接名](超链接地址 "超链接title")
title可加可不加
```

### 6.2 示例

```javascript
[简书](http://jianshu.com)
[百度](http://baidu.com)
```

### 6.3 效果

[简书](http://jianshu.com)
[百度](http://baidu.com)

### 6.4 注

Markdown本身语法不支持链接在新页面中打开，如果想要在新页面中打开的话可以用html语言的a标签代替。

```javascript
<a href="超链接地址" target="_blank">超链接名</a>
<a href="https://www.google.com/" target="_blank">谷歌</a>
```

## 7.列表

## 8.表格

### 8.1 语法

```javascript
表头|表头|表头
---|:--:|---:
内容|内容|内容
内容|内容|内容

第二行分割表头和内容。
- 有一个就行，为了对齐，多加了几个
文字默认居左
- 两边加：表示文字居中
- 右边加：表示文字居右
注：原生的语法两边都要用 | 包起来。此处省略
```

### 8.2 示例

```javascript
姓名|技能|排行
-|:-:|-:
刘备|哭|大哥
关羽|打|二哥
张飞|骂|三弟
```

### 8.3 效果

| 姓名 | 技能 | 排行 |
| ---- | :--: | ---: |
| 刘备 |  哭  | 大哥 |
| 关羽 |  打  | 二哥 |
| 张飞 |  骂  | 三弟 |

## 9.代码

### 9.1 语法

#### 9.1.1 单行代码

```javascript
`console.log('code')`
```

#### 9.1.12 代码块

```javascript
​```
	fucntion func(){
		console.log('code')
	}
	func()
​```
```

### 9.2 效果

#### 9.2.1 单行效果

`console.log('code')`

#### 9.2.2 代码块效果

```javascript
fucntion func(){
	console.log('code')
}
func()
```

## 10.流程图

### 10.1 示例

~~~markdown
```flow
st=>start: 开始
op=>operation: My Operation
cond=>condition: Yes or No?
e=>end
st->op->cond
cond(yes)->e
cond(no)->op
&```
~~~

### 10.2 效果

```flow
st=>start: 开始
op=>operation: My Operation
cond=>condition: Yes or No?
e=>end
st->op->cond
cond(yes)->e
cond(no)->op
```

