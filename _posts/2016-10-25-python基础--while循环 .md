---
layout: post
title: python基础--while循环 
date: 2016-10-25 
tags: python基础--while循环 
---

一、永不停止的循环

 

已经有了for循环，为何还要再学习while循环呢，莫非while循环有什么特别之处。





现在请你思考一个问题，能否用for循环写一个永远不会退出的循环呢？答案是不能的，即便你用什么古怪的手段做到了，也不是编程语言设计for循环的本意。

但是while循环就可以做得到，在while循环过程中，除非符合了某个条件使得程序执行了break语句或者return语句，否则，while循环可以一直循环



示例代码： 
#coding=utf-8
while True:
   name = raw_input('input an name:')
   if name == 'stop':
       break

   msg = u'你输入的名字长度为{length}'
   msg = msg.format(length=len(name))
   print msg


while 语句的后面是一个表达式，只要表达式为真，循环就会一直进行下去，永不停止。在上面的例子中，程序要求你输入一个名字，
你输入一个名字后，它会输出这个名字的长度，除非你输入一个stop，否则它会一直提示你输入。


 二、while循环更加灵活



实际上while循环相比于for循环更加的灵活，请考虑这样一个题目，现有一个list，其内容为：

lst = [1,4,2,9,5,4,6,11,13,15,6,3]

请逐个输出lst中的元素，如果元素值为偶数则下一次输出时要间隔一个元素，比如输出lst[1]时，lst[1]为偶数，那么下一次输出时
就不能输出lst[2]，而是要输出lst[3],以此类推。

如果是用for循环来做，是很难做得到的，但使用while循环就很简单。




示例代码：

 
#coding=utf-8
lst = [1,4,2,9,5,4,6,11,13,15,6,3]
index = 0
while index < len(lst):
   print lst[index]
   if lst[index] % 2 == 0:
       index += 2
   else:
       index += 1

代码解析

•index < len(lst) 如果成立，则进入循环


•index += 2 等价于 index = index + 2 ，但写起来更方便


•只要控制了index的变化，就可以控制循环何时结束了

三、for循环与while循环比较


•大部分情况下，两者可以互换


•涉及到永久循环时，要用while True 这种方式的循环


•涉及到对某个序列进行遍历时，使用for循环


•想对循环有更加灵活的控制，使用while循环

