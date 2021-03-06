# Java based

[TOC]

##### - [Can a ".java "source file contain multiple classes (not inner classes)? What are the limitations?](https://github.com/duyangs/interview/blob/master/javaBase/Can%20a%20%22.java%20%22source%20file%20contain%20multiple%20classes%20(not%20inner%20classes)%3F%20What%20are%20the%20limitations%3F.md)

> 一个“.java”源文件中是否可以包含多个类（不是内部类）？有什么限制？



##### -  [Does Java have a "goto"?](https://github.com/duyangs/interview/blob/master/javaBase/Does%20Java%20have%20a%20%22goto%22%3F.md)

> Java有没有goto?



##### - [Tell the difference between “&&” & “&”.](https://github.com/duyangs/interview/blob/master/javaBase/Tell%20the%20difference%20between%20%E2%80%9C%26%26%E2%80%9D%20%26%20%E2%80%9C%26%E2%80%9D..md)

> 说说&和&&的区别。



##### - [How to jump out of the current multi-nested loop in Java.](http://www.jianshu.com/p/55a604a3d7bc)

> 在Java中如何跳出当前的多重嵌套循环.



##### 5. Switch语句能否作用在byte上，能否作用在long上，能否作用在String上？

```
在switch(e)中，e只能是一个整数表达式或者枚举常量(更大字体),整数表达式可以是Int基本类型或integer包装类型，由于byte，short，char都可以隐式转换为int，所以这些类型以及这些类型的包装类型也是可以的。显然long不符合switch的语法规定，并且不能隐式的转换成int类型，所以不能作用于switch语句中。
jdk1.7中switch语句可以支持String。但不建议用String，效率不高，编译中最终会转换成hashcode，实质上还是编译成了整型，case分支内又做了字符串比较。
```

##### 6. short s1 = 1；s1=s1+1;有什么错？short s1=1; s1 += 1；有什么错？

```
	对于short s1=1;s1=s1+1;由于s1+1运算时会自动提升表达式的类型，所以结果是int型，再赋值给short类型的s1时，编译器将报告需要强制类型转换的错误。
	对于short s1=1;s1+=1;由于 += 是java语言规定的运算符，java编译器会对它进行特殊处理，因此正确编译。
```

##### 7. char型变量中能不能存储一个中文汉字？为什么？

```
char型变量是用来存储Unicode编码的字符，Unicode编码字符集中包含了汉字，所以，char型变量中当然可以存储汉子。不过，如果某个特殊汉字没有被包含在Unicode编码字符集中，那么，这个char型变量中就不能存储这个特殊汉字。补充说明：Unicode编码占用两字节，所以char型变量也是占用两字节。
备注：后面一部分回答虽然不是在正面回答题目，但是，为了展现自己的学识和表现自己对问题理解的透彻深入，可以回答一些相关的知识，做到知无不言，言无不尽。
```

##### 8. 用最有效率的方法算出2乘以8等于几？

```
2<<3
因为将一个数左移n位，就是相当于乘以2的n次方，那么，一个数乘以8只要将其左移3位即可，而位运算符cpu直接支持的，效率最高，所以，2乘以8等于几的最效率的方法就是 2<<3。
```

##### 9. [请设计一个一百亿的计算器](http://www.cnblogs.com/fthjane/p/4732418.html)

##### 10. 使用final关键字修饰一个变量时，是引用不能变，还是引用的对象不能变？

```
使用final关键字修饰一个变量时，是指引用不能变，引用变量所指向的对象中的内容还是可以变的。例如，对于如下语句：
	final StringBuffer a = new StringBuffer("immutable");
	执行如下语句将报告编译器错误：
	a=new StringBuffer("");
	但是，执行如下语句则可以通过编译：
	a.append("broken!");
有人在定义方法的参数时，可能想采用如下形式来阻止方法内部修改传进来的参数对象：
public void method(final StringBuffer param){}
实际上，这是办不到的，在该方法内部仍然可以增加如下代码来修改参数对象：
	param.append("a");
```

##### 11. ["=="和equals方法究竟有什么区别？](http://www.cnblogs.com/findumars/p/3746878.html)

##### 12. [静态变量和实例变量的区别？](http://blog.csdn.net/u012110719/article/details/46334419)

##### 13. 是否可以从一个static方法内部发出对非static方法的调用？

```
不可以，因为非static方法是要与对象关联在一起的，必须创建一个对象后，才可以在该对象上进行方法调用，而static方法调用的时候不需要创建对象，可以直接调用。也就是说，当一个static方法被调用时，可能还没有创建任何实例，如果从static方法发出对非static方法中发出对非static方法的调用，那个非static方法是关联到哪个对象上的呢？ 这个逻辑无法成立，所以，一个static方法内部无法发出对非static方法的调用。
```

##### 14. Integer与int的区别

```
	int是java提供的8种数据类型之一。java为每个原始类型提供封装类，integer是Java为int提供的分装类。int的默认值为0，而Integer的默认类型为null，即integer可以区分出未赋值和值为0的区别，int则无法表达出未赋值的情况，例如想要表达出没有参加考试和考试成绩为0的区别，则只能使用integer。在JSP开发中，integer的默认值为null，所以用el表达式在文本框中显示时，值为空白字符串，而int默认值为0，所以用el表达式在文本框中显示时，结果为0，所以，int不适合作为web层的表单数据的类型。
	在hibernate中，如果将OID定义为integer类型，那么hibernate就可以根据其值是否为null而判断一个对象是否是临时的，如果将OID定义为了int类型，还需要在hbm映射文件中设置其unsaved-value属性为0.
	另外，Integer提供了多个与整数相关的操作方法，例如，将一个字符串转换成整数，Integer中还定义了表示整数的最大值和最小值的常量。
```

##### 15. Math.round(11.5)等于多少？Math.round(-11.5)等于多少？

```
math类中提供了三个与取整相关的方法：ceil、floor、round，这些方法的作用与它们的英文名称相对应，
	例如，
	ceil的英文意义是天花板，该方法就表示向上取整，Math.ceil(11.3)的结果为12，Math.ceil(-11.3)的结果为-11；
	floor的英文意义是地板，该方法就表示向下取整，Math.floor(11.6)的结果为11，Math.floor(-11.6)的结果是-12；
	最难掌握的是round方法，它表示“四舍五入”，算法为math.floor(x+0.5),即将原来的数字加上0.5后再向下取整，所以，Math.round(11.5)的结果为12，Math.round(-11.5)的结果为-11.
```

##### 16. 下面的代码有什么不妥之处？

```
1.if(username.equals("zxx"))
username可能为NULL，会报空指针错误，改为“zxx".equals(username)
2.int x=1;
	return x==1?true:false;
这个改成return x==1;就可以
```

##### 17. 请说出作用域public，private，protected，以及不写时的区别

| 作用域       | 当前类  | 同一包(package) | 子孙类  | 其他包(package) |
| --------- | ---- | ------------ | ---- | ------------ |
| public    | ok   | ok           | ok   | ok           |
| protected | ok   | ok           | ok   | no           |
| friendly  | ok   | ok           | no   | no           |
| private   | ok   | no           | no   | no           |

```
这四个作用域的可见范围如上表所示。
说明：如果在修饰的元素上面没有写任何访问修饰符，则表示friendly。
备注：只要记住了有4种访问权限，4个访问范围，然后将全选和范围在水平和垂直方向上分别安排从小到大或从大到小的顺序排列，就很容易画出上面的图了。
```

##### 18. [Overload 和 Override的区别。Overloaded的方法是否可以改变返回值的类型？](http://blog.csdn.net/partner4java/article/details/7187846)

##### 19. 构造器Constructor是否可以被Override？

```
构造器Constructor不能被继承，因此不能重写Override，但可以被重载Overload.
```

##### 20.接口是否可继承接口？抽象类是否可实现（implements)接口？抽象类是否可继承具体类（concrete class）？抽象类中是否可以有静态的main方法？

```
接口可继承接口；抽闲类可以实现接口；抽象类可以继承具体类；抽象类中可以有静态的main方法。
备注：只要明白了接口和抽象类的本质和作用，这些问题都很好回答，你想想，如果你是Java语言设计者，你是否会提供这样的支持，如果不提供的话，有什么理由？如果你没有道理不提供，那答案就是肯定的了。
只要记住抽象类和普通类的唯一区别：就是不能创建实例对象和允许有abstract方法。
```

##### 21. 写clone（）方法时，通常都有一行代码，是什么？

```
clone有缺省行为
super.clone()；
因为首先要把父类中的成员复制到位，然后才是复制自己的成员。
```

##### 22. [面向对象的特征有哪些方面？](http://www.cnblogs.com/guweiwei/p/6599289.html)

##### 23. Java中实现多态的机制是什么？

```
靠的是父类或接口定义的引用变量指向子类或具体实现类的实例对象，而程序调用的方法在运行期才动态绑定，就是引用变量所指向的具体实例对象的方法，也就是内存里正在运行的那个对象的方法，而不是应用变量的类型中定义的方法。
```

##### 24. [abstract class 和 interface 有什么区别？](http://www.cnblogs.com/zss-xjx/p/5949457.html)

```
备注：这道题的思路是先从总体解释抽象类和接口的基本概念，然后再比较两者的语法细节，最后再说两者的应用区别。比较两者语法细节区别的条例是：
	先从一个类中的构造方法、普通成员变量和方法(包括抽象方法)，静态变量和方法，继承性等6个方面逐一去比较回答，接着从第三者继承的角度回答，特别最后用一个典型的例子来展现自己深厚的技术功底。
```

##### 25. abstract 的 method 是否可同时是static,是否可同时是native,是否可同时是synchronized? 

