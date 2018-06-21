---
layout: post
title: python基础---循环中的break和cotinue
date: 2016-10-14 
tags: python基础---循环中的break和cotinue 
---



内容要点：

•for循环
•break终止循环
•continue跳过本轮循环
•isinstance判断变量
 一、break

请思考
lst = [1,4,5,7,2,7,34,23,67]

从索引号0开始，请找出lst中第一个大于20的元素的索引号。
常规处理手段

如果不是写程序，而是观察，很快就找得到34，34所在索引号是6。前一篇公众号文章已经提了一个要求，想进入编程的世
界，就必须放弃观察者的身份，考虑使用程序来处理，你可以遍历这个lst，你可能会想到这样的代码：
for i in range(len(lst)):
    if lst[i] > 20:
        print i

 

这段代码确实输出了索引号6，可是也把7，8也输出了。怎么才能不让7 和 8 也输出呢？如果程序知道已经输出过一次了就好了，修改一下程序：

 
bPrint = False

for i in range(len(lst)):
    if lst[i] > 20 and not bPrint:
        print i
        bPrint = True

 

创建一个变量bPrint并赋值为False，当遍历到34时，进入到if语句块，这时输出了6，同时修改bPrint的值为True，bPrint标识
已经输出过一次了，这样当遍历到23的时候，由于not bPrint为False，因此整个 条件判断结果为Flase，就不会再进入到if 语句块了。





使用break






可这个程序还是存在一个瑕疵，尽管只是输出了34的索引号，可是还是遍历了整个lst，如果34后面还有1亿个数怎么办呢，明明已经找
到了第一个大于20的元素的索引号，为什么还要继续遍历呢，再遍历下去已经没有任何意义，完全是在浪费时间，为何不停下来呢?在循
环过程中，如果我们希望循环终止，可以使用break语句，来看例子：
for i in range(len(lst)):

  print u'当前索引号是{index}'.format(index=i)
    if lst[i] > 20:
        print i
        break

 

break语句会跳出整个循环，第二行的语句只是为了让你明白，程序真的一共只循环了7次。

 二、continue

isinstance
lst = [1,4,'sdf',5,7,2,'oiu',7,34.9,23,67]

请输出lst中的元素，字符串除外，我这里直接给出代码：
for i in range(len(lst)):
    if not isinstance(lst[i],str):
        print lst[i]

 

isinstance是python内置函数，它和我之前讲过的type一样，可以用于判断变量类型，你或许有一种
既生瑜何生亮的疑惑，关于他们的不同，在讲到类时再进行讲解。


使用continue

除了上面这种写法，还可以使用continue，看例子：

 
for i in range(len(lst)):

    if isinstance(lst[i],str):
        continue
    print lst[i]

continue只是跳出本次循环，急迫的想要开始下一轮循环，而continue后面的代码则不执行，在本例中，当lst[i]是字
符串时，进入到if语句块，执行了continue，后面的print lst[i]就不会被执行了，但没有破坏整个循环，这就是说，循环
的次数没有减少，这是continue与break不同之处。
使用continue的好处



你会注意到，上面的两个例子，实现了相同的功能，其实所有用continue的地方都可以把continue去掉，用if条件语句来进行逻
辑控制，但continue有它特别的好处，来看一个稍微复杂点的例子： 
lst = [1,4,'sdf',5,7,2,'oiu',7,34.9,23,67]



现在要求你输出lst中的int类型的数和float类型的数，如果不用continue，可以这样写，例子1：

 
for i in range(len(lst)):
    if not isinstance(lst[i],str):
        if isinstance(lst[i],int):
            print u'{item}是一个int类型数据'.format(item=lst[i])
        if isinstance(lst[i],float):
            print u'{item}是一个float类型数据'.format(item=lst[i])

 

使用continue可以写成这样，例子2:

 
for i in range(len(lst)):

    if isinstance(lst[i],str):
        continue

    if isinstance(lst[i],int):
        print u'{item}是一个int类型数据'.format(item=lst[i])

    if isinstance(lst[i],float):
        print u'{item}是一个float类型数据'.format(item=lst[i])

 

仔细比较一下这两份代码，例子2的代码更容易阅读，而例子1的代码阅读起来就稍微费力，原因在于：

•在于例子2中for循环中的的代码缩进量相同且只有2层，而例子1的缩进层次则有3层。


•例子2使用continue，逻辑上明确指明遇到字符串时不做任何处理，而例子1则是在逻辑上指明只处理那些类型不是字符串的数据。
当逻辑非常复杂时，continue会非常有用，因为它很少破坏代码的缩进层次。









