---
layout: post
title: 关于设置形参缺省值的问题和解决方案
category: 技术
keywords: 技术,Javascript,缺省值,JSON
---

## 形式参数缺省

假设我们在开发中需要先封装一个函数

```javascript

function tool( x , y , z )

```
有三个参数，分别对应三个不同的功能

但是如果在一些情况下
这个函数我们只需要它其中两个功能
其他的功能不需要

那么在没有设置形参缺省的情况下
我们只能这样调用函数
tool( 2 , '' , 1)

(这里假设我使用y功能 并给y传递1这么一个参数)

那么如果需要大量的在不同的情况下使用tool 函数
这种调用方法 显然用的很繁琐(每次都需要传递长长的一串空参数)

可能有人会想，直接不传行不行
也就是这样

```javascript
tool( 2 , 1 )
```

这样的结果导致的就是
不需要的参数y = 1
而需要的参数z = '';


所以我们这里需要设置形参缺省值


## 使用JSON对象解决形式参数缺省问题


```javascript

假设我这里只要填x 和 z的值

tool({ x : 123 , z : ["owen","Brown"]});

function tool( obj )
{
  //这里 '' 可以 替换成其他缺省值
  obj.x = x || '';
  obj.y = y || '';
  obj.z = z || '';
  
  ...

  //如果使用了'' 要实现某一功能 
  //加一个判断语句就好了
  if(x)
  {
    ...
  }
  else
  {
    return;
  }


}
```

## 缺省值

这里解释一下
缺省值也就是默认值的意思(系统默认状态 default)
至于为什么叫缺省值呢
是由于当年学者们翻译default这个词的时候的翻译问题
大家就理解成默认值就行了
