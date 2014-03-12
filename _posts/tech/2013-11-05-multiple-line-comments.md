---
layout: post
title:  "正则表达式匹配多行注释"
date:   2013-11-05
comments: true
categories: 
tags: ["regex"]
---

#### 我的尝试 ####

```java
/\*.*\*/
```

但是这只能识别单行注释，在Java中，有两种方法识别多行注释：

```java
Pattern.compile("(?s)/\\*.*\\*/")
Pattern.compile("/\\*.*\\*/", Pattern.DOTALL)
```

但是这会吞并两个注释间的所有的代码：

```
start_code();
/* First comment */
more_code();
/* Second comment */
end_code();
```

#### Solutions ####

1. 正则表达式中的`*`是贪婪匹配，而`*?`是非贪婪匹配，下面的正则使用非贪婪匹配（需添加`Pattern.DOTALL`选项）

```
`/\*.*?\*/`
```

2. 有的正则实现不支持非贪婪匹配，则可以使用下面的正则：

```
`/\*([^*]|[\r\n]|(\*+([^*/]|[\r\n])))*\*+/`
```

3. 无意间发现的一个Trick，既可以多行，又是非贪婪匹配

```
`/\*[\w\W]*?\*/`
```

这里的\w\W可以使用任意相反的字符类，比如`\d\D`, `\s\S`等

#### 存在问题 ####

被双引号包括的注释同样会被识别，所以在实际使用时应当注意这点。

#### 参考链接 ####

<http://stackoverflow.com/questions/13014947/regex-to-match-a-c-style-multiline-comment>

<http://ostermiller.org/findcomment.html>
