# regexp

GO语言正则表达式语法
---
一.要匹配的字符串


语法	说明	表达式示例	匹配结果
一般字符	匹配自身	abc	abc
.	匹配任意除换行符"\n"外的字符， 在 DOTALL 模式中也能匹配换行符	a.c	abc
\	转义字符，使后一个字符改变原来的意思；
如果字符串中有字符 * 需要匹配，可以使用 \* 或者字符集［*]。	a\.c
a\\c	a.c
a\c
[...]	字符集（字符类），对应的位置可以是字符集中任意字符。
字符集中的字符可以逐个列出，也可以给出范围，如 [abc] 或 [a-c]，
第一个字符如果是 ^ 则表示取反，如 [^abc] 表示除了abc之外的其他字符。	a[bcd]e	abe 或 ace 或 ade
\d	数字：[0-9]	a\dc	a1c
\D	非数字：[^\d]	a\Dc	abc
\s	空白字符：[<空格>\t\r\n\f\v]	a\sc	a c
\S	非空白字符：[^\s]	a\Sc	abc
\w	单词字符：[A-Za-z0-9]	a\wc	abc
\W	非单词字符：[^\w]	a\Wc	a c

二.数量词

语法	说明	表达式示例	匹配结果
*	匹配前一个字符 0 或无限次	abc*	ab 或 abccc
+	匹配前一个字符 1 次或无限次	abc+	abc 或 abccc
?	匹配前一个字符 0 次或 1 次	abc?	ab 或 abc
{m}	匹配前一个字符 m 次	ab{2}c	abbc
{m,n}	匹配前一个字符 m 至 n 次，m 和 n 可以省略，若省略 m，则匹配 0 至 n 次；
若省略 n，则匹配 m 至无限次	ab{1,2}c	abc 或 abbc

三.边界匹配
语法	说明	表达式示例	匹配结果
^	  在多行模式中匹配以该字符串开头的一行	^abc	abc
$	  在多行模式中匹配以该字符串结尾的一行	abc$	abc
\A	仅匹配字符串开头	\Aabc	abc
\Z	仅匹配字符串末尾	abc\Z	abc
\b	匹配 \w 和 \W 之间	a\b!bc	a!bc
\B	[^\b]	a\Bbc	abc


##### 贪婪匹配和非贪婪匹配  
```
当匹配的字符串后面没有?时为贪婪匹配  
当匹配的字符串后面带有?时为非贪婪匹配  
```

