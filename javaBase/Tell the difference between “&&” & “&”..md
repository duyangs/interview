##### Tell the difference between “&&” & “&”.

##### 说说&和&&的区别。

>	& && and can be used as a logic and operator, said logic and (and), when the operator on both sides of the expression is the result of the true, the result is true, otherwise, if one party is false, the result is false.
&& also has short circuit function, that is, if the first expression is false, the second expression is no longer calculated, for example, for if (STR! = null &&! STR. Equals (")) expression, when STR is null, the following expression will not be executed, so NullPointerException will not appear if & when it is changed to &, it will throw nullpointered potion.
X = 31 if (x = = 33 & + + y > 0) y increases, the if (x = = 33 && + + y > 0) y won't grow.
& also can be used as an operator, when the expression is not on both sides of the & operator Boolean type, & said bitwise and operation, we usually use 0 x0f to & operation with an integer, to obtain the minimum 4 bit integer, for example, 0 x31 & 0 x0f to 0 x01 results.
Note: this question starts with the similarities between the two, and gives some examples of the classic examples to illustrate the depth of understanding and practical experience.
	
>	&和&&都可以用作逻辑与的运算符，表示逻辑与(and)，当运算符两边的表达式的结果都为true时，整个运算结果才为true，否则，只要一方为false，则结果为false。
	&&还具有短路的功能，即如果第一个表达式为false，则不再计算第二个表达式，例如，对于if(str != null && !str.equals(""))表达式，当str为null时，后面的表达式不会执行，所以不会出现NullPointerException如果将&&改为&，则会抛出NullPointerExcepotion.
	x=31 if(x == 33 & ++y>0) y会增长，if(x==33 && ++y>0) y不会增长。
	&还可以用作位运算符，当&操作符两边的表达式不是boolean类型时，&表示按位与运算，我们通常使用0x0f来与一个整数进行&运算，来获取该整数的最低4个bit位，例如，0x31&0x0f的结果为0x01。
	备注：这道题先说两者的共同点，再说出&&和&的特殊之处，并列举一些经典的例子来表明理解透彻深入、实际经验丰富。


