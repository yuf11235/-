# C语言程序设计



## 第一周：绪论

### 1.程序的执行

__解释__: 借助一个程序，该程序试图**理解**你编写的程序，然后按照你的要求执行程序

__编译__：借助一个程序，像是一个翻译，把你写的程序**翻译**为计算机的语言（**机器语言**），然后执行

### 2.做计算——四则运算



## 第二周：计算

### 1.如何输入

输入在终端窗口中进行的

输入是以行为单位的，**行的结束标志是回车符**，在按下回车之前，程序不会读取到输入的东西

### 2.变量

变量定义的一般形式 

```c
<类型名称> <变量名称1>,<变量名称2>;
```



### 3.变量初始化

`<类型名称> <变量名称1>=<初始值1>,<变量名称2>=<初始值2>;`

### 4.读整数

```c
int price=0;

scanf("%d", &price);
```



### 5.常量

**固定不变**的数——常数，直接写在程序里，称为**直接量**(**literal**)

定义一个常量

```c
const int AMOUNT = 100; 
```

通常给常量的命名为全**大写字母**

**const**是一个修饰符，表示变量不变的属性——一旦初始化，再也不能修改

### 6.依次从键盘读入整数

```c
int a, b;

scanf("%d %d", &a, &b);
```

### 7.两个整数的运算结果只能是整数

```c
printf("%d\n", 10/3);//输出为3
printf("%d\n", 10/3*3);//输出为9
```

### 8.浮点数输出

```c
printf("%f\n", 10.0/3);//输出为3.333333
printf("%f\n", 10.0/3*3);//输出为10.000000
```

### 9.浮点数类型

`float`——单精度浮点数

`double`——双精度浮点数

### 10.double类型注意

输入`%lf`输出`%f`

```c
double a, b;
scanf("%lf %lf", &a, &b);//注意输入的时候是%lf表示double
printf("%f", (a+b));
```

### 11.表达式

运算符、运算子

### 12.运算符优先级

| 优先级 | 运算符 |   运算   | 结合关系 | 举例 |
| :----: | :----: | :------: | :------: | :--: |
|   1    |   +    | 单目不变 | 自右向左 | a*+b |
|   1    |   -    | 单目不变 | 自右向左 | a*-b |
|   2    |   *    |    乘    | 自左向右 | a*b  |
|   2    |   /    |    除    | 自左向右 | a/b  |
|   2    |   %    |   取余   | 自左向右 | a%b  |
|   3    |   +    |    加    | 自左向右 | a+b  |
|   3    |   -    |    减    | 自左向右 | a-b  |
|   4    |   =    |   赋值   | 自右向左 | a=b  |

作业题

```c
a = b+=c++-d+--e/-f
```

解答

```c
a = b = b + c++-d+--e/-f
a = b = b + c++-d+--e/(-f)
a = b = b + (c++)-d+(--e/(-f))
a = b = b + c - d - (e-1)/f
```



### 13.赋值运算符

赋值也是运算，也有结果

```c
a = 6;
```

a被赋值为6

```c
a = b = 6;
```

相当于

```c
a = (b = 6);
```

先将6赋值给b，再将b的值赋给a

### 14.交换变量的值

```c
int a, b;
int temp;
temp = a;
a = b;
b = temp;
```

### 15.复合运算符

| **+=** | **a += b+1** | **a = a+(b+1)** |
| :----: | :----------: | :-------------: |
| **-=** | **a -= b+1** | **a = a-(b+1)** |
| ***=** | **a *= b+1** | **a = a*(b+1)** |
| **/=** | **a /= b+1** | **a = a/(b+1)** |
| **%=** | **a %= b+1** | **a = a%(b+1)** |

### 16. 递增++递减--运算符

都是**单目运算符**，且算子必须为变量

递增运算符`++`

```c
count++;
count += 1;
count = count + 1;
```

递减运算符`--`

```c
count--;
count -= 1;
count = count - 1;
```


```c
#include <iostream>
#include <stdio.h>

int main(int argc, char** argv) {
	int a;
    
	a = 10;
	printf("a++=%d\n", a++);
	printf("a=%d\n", a);
    
	a = 10;
	printf("++a=%d\n", ++a);
	printf("a=%d\n", a);
    
	return 0;
}
```

输出结果为

```
a++=10
a=11

++a=11
a=11
```

| 表达式  |    运算    |   表达式的值    |
| :-----: | :--------: | :-------------: |
| count++ | 给count加1 |  count原来的值  |
| ++count | 给count加1 | count+1以后的值 |
| count-- | 给count减1 |  count原来的值  |
| --count | 给count减1 |  count-1后的值  |

### 作业题

#### 2-1

厘米换算英尺英寸

```c
#include <iostream>
#include <stdio.h>

int main(int argc, char** argv) {
	int cm=0;
	scanf("%d", &cm);
	
	int foot = cm / 30.48;//强制类型转换
	int inch = ((cm / 30.48) - foot) * 12;
	printf("%dcm = %dfoot %dinch\n", cm, foot, inch);
	return 0;
}
```

结果

```
175
175cm = 5foot 8inch
```

#### 2-2 

时间间隔 输入1120（11：20）和时间间隔110（min）输出1310（13：10）

```c
#include <iostream>
#include <stdio.h>

int main(int argc, char** argv) {
	int starttime, temp;
	scanf("%d %d", &starttime, &temp);
	int endtime = starttime/100 * 60 +starttime%100 +temp;
	
	printf("endtime=%d", endtime/60*100 + endtime%60);
	
	return 0;
}
```

结果

```
1120 110
endtime=1310
```

#### 2-3 

逆序的三位数 123到321（注700应输出7，而不是007）

```c
#include <iostream>
#include <stdio.h>

int main(int argc, char** argv) {
	int num;
	scanf("%d", &num);
	
	int inv_num = num/100 + num%100/10*10 + num%10*100;
	
	printf("inverse num=%d", inv_num);
	
	return 0;
}
```

结果c

```
123
inverse num=321
```

#### 2-4

输入[0, 153]范围内的正整数，返回BCD码

```c
#include <iostream>
#include <stdio.h>

int main(int argc, char** argv) {
	int num;
	scanf("%d", &num);
	
	int doct_num = num/16 * 10 + num%16;
	
	printf("%d", doct_num);
	
	return 0;
}
```

结果c

```
18
12
```



## 第三周：判断

### 1.关系运算符

| 运算符 |   意义   |
| :----: | :------: |
| **==** |   相等   |
|   !=   |  不相等  |
|   >    |   大于   |
|   >=   | 大于等于 |
|   <    |   小于   |
|   <=   | 小于等于 |

### 2.优先级

所有的关系运算符的优先级**比算术运算符低，比赋值运算符高**

判断是否相等的**==和!=的优先级比其他关系运算符的等级低**，且连续的关系运算是**从左往右**的

```c
5 > 3 == 6 < 4;
6 > 5 > 4;
a == b == 6;
a == b > 0;
```

### 3.else的匹配

总是与最近的if匹配

### 4.再if和else后面敲大括号，养成良好的编程习惯

### 5.单一出口

### 6.常见错误

把`==`写成`=`

在`if`后面写**分号**(;)

### 7.switch-case

通式

```c
switch(控制表达式){//控制表达式只能是整形的(int)
    case 常量:
        语句;
        break;
    default:
        语句;
        break;
}
```

case只是相当于一个路标，只是switch开始的地方

用`break`来**分割各个case**，如果当前case中没有break，则程序会继续向下执行，直至遇到break或者switch结束

举例

```c
switch(type){
    case 1:
        printf("case 1");
        break;
    case 2:
        printf("case 2");
        break;
    case 3:
        printf("case 3");
        break;
    default:
        printf("default");
        break;
}
```

### 8.成绩转换

只看分数的十位上的数字，score%10结合switch-case



## 第四周：循环

### 1.while循环

###### 如何计算数的位数

```c
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char const *argv[])
{
	int x;
	int n=0;
	scanf("%d", &x);
	n++;
	x /= 10;
	while(x > 0)
	{
		n++;
		x/10;
	}
	printf("%d\n", n);
	return 0;
}
```

当输入0的时候，输出的值也为1



```c
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char const *argv[])
{
	int x;
	int n=0;
	scanf("%d", &x);
	while(x > 0)
	{
		n++;
		x/10;
	}
	printf("%d\n", n);
	return 0;
}
```

当输入0的时候，输出的值也为0

### 2.do-while循环

在进入循环体的时候不做检查，而是在执行完一轮循环体的代码之后，再检查循环的条件是否满足，如果满足则继续下一轮，否则结束循环

###### 如何计算数的位数

```c
do
{
    <循环体>
}while(<循环条件>);//分号(;)莫忘
```

```c
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char const *argv[])
{
	int x;
	int n=0;
	scanf("%d", &x);
	do
	{
		n++;
		x/10;
	}while(x > 0);//分号(;)莫忘
	printf("%d\n", n);
	return 0;
}
```

当输入0的时候，输出的值也为1

###### 计算log2x

```c
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char const *argv[])
{
	int x;
	int ret=0;

	x = 128;
	int t=x;
	while(x > 1)//x > 2^0 也可以写为x >= 2，无论如何得把2的一次幂包含进去
	{
		x /= 2;
		ret++;
	}
	printf("log2 of %d is %d\n", t, ret);
	return 0;
}
```

###### 反转

```c
#include <stdio.h>

int main(int argc, char const *argv[])
{
	int x;
	scanf("%d", &x);
	int digit;
	int ret=0;

	while(x > 0)
	{
		digit = x%10;
		ret = ret*10 + digit;//妙啊
		x /= 10;
	}
	printf("%d\n", ret);
	return 0;
}
```

## 第五周：循环控制

### 1.阶乘

```c
#include <stdio.h>

int main(int argc, char const *argv[])
{
	int n;
	scanf("%d", &n);
	int factor = 1;
	int i = n;

	while(n>1)
	{
		factor *= n;
		n--;
	}
	printf("%d! = %d\n", i, factor);
	return 0;
}
```

```c
#include <stdio.h>

int main(int argc, char const *argv[])
{
	int n;
	scanf("%d", &n);
	int factor = 1;

	for(int i=2; i<=n;i++)//attention here
	{
		factor *= i;
	}

	printf("%d! = %d\n", n, factor);
	return 0;
}
```

```c
#include <stdio.h>

int main(int argc, char const *argv[])
{
	int n;
	scanf("%d", &n);
	int factor = 1;
	int i = n;

	for(n=n; n>1; n--)//attention here
	{
		factor *= n;
	}

	printf("%d! = %d\n", i, factor);
	return 0;
}
```

```c
#include <stdio.h>

int main(int argc, char const *argv[])
{
	int n;
	scanf("%d", &n);
	int factor = 1;
	int i = n;

	for(; n>1; n--)//attention here
	{
		factor *= n;
	}

	printf("%d! = %d\n", i, factor);
	return 0;
}
```

### 2.for循环

```c
for(初始条件;条件;每轮的动作)
{
    <循环体>;
}
```

for中的每一个表达式都是可以**省略**的

```c
for(;条件;) == while(条件)
```

### 3.tips for loops

|        要求        |   循环   |
| :----------------: | :------: |
| 固定次数(比如遍历) |   for    |
|    必须执行一次    | do-while |
|      其他情况      |  while   |

### 4.examples

#### 凑硬币1

```c
#include <stdio.h>

int main()
{
	int x;
	int one, two, five;
	
	scanf("%d", &x);
	for ( one = 1; one < x*10; one++ )
    {
		for ( two = 1; two < x*10/2; two++ ) 
        {
			for ( five = 1; five < x*10/5; five++ ) 
            {
				if ( one + two*2 + five*5 == x*10 ) 
                {
					printf("可以用%d个1角加%d个2角加%d个5角得到%d元\n", 
						one, two, five, x);
					break;
				}
			}
		}
	}
	
	return 0;
}
```

#### 凑硬币2

```c
#include <stdio.h>

int main()
{
	int x;
	int one, two, five;
	int exit = 0;
	
	scanf("%d", &x);
	for ( one = 1; one < x*10; one++ )
    {
		for ( two = 1; two < x*10/2; two++ ) 
        {
			for ( five = 1; five < x*10/5; five++ ) 
            {
				if ( one + two*2 + five*5 == x*10 ) 
                {
					printf("可以用%d个1角加%d个2角加%d个5角得到%d元\n", 
						one, two, five, x);
					exit = 1;
					break;
				}
			}
			if ( exit == 1 ) break;
		}
		if ( exit == 1 ) break;
	}
	
	return 0;
}
```

#### 凑硬币3

```c
#include <stdio.h>

int main()
{
	int x;
	int one, two, five;
	
	scanf("%d", &x);
	for ( one = 1; one < x*10; one++ ) 
    {
		for ( two = 1; two < x*10/2; two++ ) 
        {
			for ( five = 1; five < x*10/5; five++ ) 
            {
				if ( one + two*2 + five*5 == x*10 ) 
                {
					printf("可以用%d个1角加%d个2角加%d个5角得到%d元\n", 
						one, two, five, x);
					goto out;//out为标志，使用goto直接跳到out
				}
			}
		}
	}
out://标志
	return 0;
}
```

#### 判断一个数是否是素数

```c
#include <stdio.h>

int main()
{
	int x;

	scanf("%d", &x);
	
	int i;
	int isPrime = 1;	//	x是素数
	for ( i=2; i<x; i++ ) 
    {
		if ( x % i == 0 ) 
        {
			isPrime = 0;
			break;
		}
	}
	if ( isPrime == 1 ) 
    {
		printf("是素数\n");
	} 
    else 
    {
		printf("不是素数\n");
	}
	return 0;
}
```

#### 找出100以内的所有的素数

```c
#include <stdio.h>

int main()
{
	int x;
	
	for ( x=1; x<=100; x++ ) 
    {
		int i;
		int isPrime = 1;	//	x是素数
		for ( i=2; i<x; i++ ) 
        {
			if ( x % i == 0 ) 
            {
				isPrime = 0;
				break;
			}
		}
		if ( isPrime == 1 ) 
        {
			printf("%d ", x);
		} 
	}
	printf("\n");
	return 0;
}
```

#### 找出前50个素数

```c
#include <stdio.h>

int main()
{
	int x;
	int cnt = 0;

	x = 1;
	while ( cnt <50 ) 
    {
		int i;
		int isPrime = 1;	//	x是素数
		for ( i=2; i<x; i++ ) 
        {
			if ( x % i == 0 ) 
            {
				isPrime = 0;
				break;
			}
		}
		if ( isPrime == 1 ) 
        {
			cnt ++;
			printf("%d\t", x);
			if ( cnt %5 == 0 )
            {
				printf("\n");
			}
		} 
		x++;
	}
	return 0;
}
```



### 5.break vs continue

|   语句   |                     作用                     |
| :------: | :------------------------------------------: |
|  break   |                   跳出循环                   |
| continue | 跳出这一轮，剩下语句不会执行，直接进入下一轮 |

### 6.正向分解整数

```c
#include <stdio.h>

int main()
{
	int x;
	scanf("%d", &x);

	int mask = 1;
	int t = x;
	while ( t>9 ) 
    {
		t /= 10;
		mask *=10;
	} 
	printf("x=%d, mask=%d\n", x, mask);
	do {
		int d = x / mask;
		printf("%d", d);
		if ( mask > 9 ) 
        {
			printf(" ");
		}
		x %= mask;
		mask /= 10;
	} while ( mask > 0 );
	printf("\n");

	return 0;
}
```

### 7.求最大公约数

#### 枚举法

```c
#include <stdio.h>

int main()
{
	int a,b;
	int min;
	
	scanf("%d %d", &a, &b);
	if ( a<b ) 
    {
		min = a;
	} else 
    {
		min = b;
	}
	int ret = 0;
	int i;
	for ( i = 1; i < min; i++ ) 
    {
		if ( a%i == 0 ) 
        {
			if ( b%i == 0 ) 
            {
				ret = i;
			}
		}
	}
	printf("%d和%d的最大公约数是%d.\n", a, b, ret);
	
	return 0;
}
```

#### 辗转相除法

```c
#include <stdio.h>

int main()
{
	int a,b;
	int t;
	
	scanf("%d %d", &a, &b);
	int origa = a;
	int origb = b;
	while ( b != 0 ) 
    {
		t = a%b;
		a = b;
		b = t;
	}
	printf("%d和%d的最大公约数是%d.\n", origa, origb, a);
	
	return 0;
}
```

计算过程

|   a   |   b   |  t   |
| :---: | :---: | :--: |
|  12   |  18   |  12  |
|  18   |  12   |  6   |
|  12   |   6   |  0   |
| **6** | **0** |      |

当**b=0**时，最大公约数就是**a**

### 8.水仙花数

三位数153 = 1^3^ + 5^3^ + 3^3^

```c
#include <stdio.h>

int main(int argc, char const *argv[])
{
	int n;
	scanf("%d", &n);
	int first = 1;
	int i = 1;
	while(i < n)
	{
		first *= 10;
		i++;
	}
	i = first;
	while(i < first*10)
	{
		int t = i;
		int sum = 0;
		do
		{
			int d = t%10;
			t /= 10;
			int p = d;
			int j = 1;
			while(j < n)
			{
				p *= d;
				j++;
			}
		}while(t > 0)
		i++;
	}
	return 0;
}
```



## 第六周：数据类型

### 1.c语言中的类型

|    类型    |                                   |
| :--------: | :-------------------------------: |
|    整数    | char、short、int、long、long long |
|   浮点数   |    float、double、long double     |
|    逻辑    |     bool(可以合并到整数里面)      |
|    指针    |                                   |
| 自定义类型 |                                   |

#### 类型的不同点

|       不同点       |                             |
| :----------------: | :-------------------------: |
|    输入输出格式    |        %d、%ld、%lf         |
|    表达数的范围    | char<short<int<float<double |
| 内存中所占据的大小 |      1个字节到16个字节      |
|  内存中的表达形式  |    二进制数(补码)、编码     |

#### sizeof()

给出某个类型或变量在内存中所占据的字节数

```c
sizeof(int);
sizeof(i);
```

静态运算符，不要在sizeof的括号里做运算，这些运算不会做的

```c
int a;
sizeof(a);//4
sizeof(a++);//4
sizeof(a+1.0);//8-double类型，发生了强制类型转换
```

### 2.整数

|     类型      |                         大小                         |    表示范围    |
| :-----------: | :--------------------------------------------------: | :------------: |
|     char      |                    1字节（8比特）                    |    -128~127    |
| unsigned char |                    1字节（8比特）                    |     0~255      |
|     short     |                        2字节                         |  -32768~32767  |
|      int      | 取决于CPU，通常为**1个字**——总线宽度（32bit、64bit） | -2^32^~2^32^-1 |
|     long      | 取决于CPU，通常为**1个字**——总线宽度（32bit、64bit） | -2^32^~2^32^-1 |
|   long long   |                        8字节                         | -2^64^~2^64^-1 |

### 3.整数的内部表达

#### 如何表示负数

**-a**，其**补码**就是**0-a**, 实际是**2^n^-a**，n是这种类型的位数

#### 补码的意义

拿补码和原码可以加出一个溢出的“0”

正数的原码、反码及补码都相同

负数的反码等于其绝对值除符号位按位取反，补码在反码的基础上+1

举例

| 十进制 |   原码    |   反码    |   补码    |
| :----: | :-------: | :-------: | :-------: |
|   +3   | 0000 0011 | 0000 0011 | 0000 0011 |
|   -3   | 1000 0011 | 1111 1100 | 1111 1101 |

(+3)~补~+(-3)~补~=0000 0011 + 1111 1101 = **1** 0000 0000，最高位1溢出，得到结果为0000 0000，转换为十进制为0

### 4.整数的范围

对于一个字节（8位），表达范围0000 0000——1111 1111

|       二进制        | 十进制  |
| :-----------------: | :-----: |
|      0000 0000      |    0    |
| 1111 1111~1000 0000 | -1~-128 |
| 0000 0001~0111 1111 |  1~127  |

```c
char c=127;//0111 1111
c += 1;
printf("c=%d", c);//1000 0000
//output: c=-128
```

```c
char c=-128;//1000 0000
c -= 1;
printf("c=%d", c);//0111 1111
//output: c=127
```



```
#include <stdio.h>

int main(int argc, char const *argv[])
{
	char c = 255;
	int i = 255;
	printf("c=%d, i=%d\n", c, i);
	return 0;
}
```

输出结果

```c
c=-1, i=255
//实际上c为1111 1111，0借一位为1 0000 0000，-1 = 0 — 1，所以-1 = 1111 1111
//i为00000000 00000000 00000000 11111111
```

### 5.unsigned

做**纯二进制运算**，主要是为了**移位**

```c
#include <stdio.h>

int main(int argc, char const *argv[])
{
	unsigned char c = 255;//attention here
	int i = 255;
	printf("c=%d, i=%d\n", c, i);
	return 0;
}
```

输出结果

```c
c=255, i=255
```

### 6.整数的输入输出

只有两种形式int、long long

|      |        类型        |
| :--: | :----------------: |
|  %d  |  char、short、int  |
|  %u  |      unsigned      |
| %ld  |     long long      |
| %lu  | unsigned long long |

### 7.八进制和十六进制

|   进制   |      |
| :------: | :--: |
|  八进制  |  %o  |
| 十六进制 |  %x  |

### 8.选择整数类型

没有特殊要求，就选择`int`

### 9.浮点类型

|  类型  |   字长    |                       范围                       | 有效数字 |
| :----: | :-------: | :----------------------------------------------: | :------: |
| float  | 32(4字节) |  正负(1.20x10^-38^~3.40x10^38^)，0,正负inf, nan  |    7     |
| double | 64(8字节) | 正负(1.20x10^-308^~3.40x10^308^)，0,正负inf, nan |    15    |

### 10.浮点的输入输出

|  类型  | scanf |       printf        |
| :----: | :---: | :-----------------: |
| float  | `%f`  | %f, %e(E)科学计数法 |
| double | `%lf` | %f, %e(E)科学计数法 |

保留指定位数的小数点

```c
#include <stdio.h>

int main(int argc, char const *argv[])
{
	double ff = 1E-10;
	printf("%E, %.16f\n", ff, ff);//attention here %.16f
	return 0;
}
```

输出

```c
1.000000E-010, 0.0000000001000000
```

### 11.超出范围的浮点数

| printf |      表示      |
| :----: | :------------: |
|  inf   |    正负无穷    |
|  nan   | 不存在的浮点数 |

### 12.浮点运算的精度

带小数点的字面量是double而非float

float需要**f**或者**F**后缀来表明身份

判断浮点数是否相等一般使用

```c
float a, b;
a = 1.345f;
b = 1.123f;

float f1, f2;
fabs(f1-f2) < 1e-12;
```

### 13.选择浮点类型

没有特殊要求，只使用`double`

### 14.字符类型

char是一种**整数**，也是一种特殊的类型：**字符**

用单引号表示字符字面量：'**a**', **'1'**

**''**也是一个字符

printf和scanf里用%c来输入输出字符

```c
#include <stdio.h>

int main(int argc, char const *argv[])
{
	char c, d;
	c = 1;
	d = '1';
	printf("c=%d\n", c);
	printf("d=%d\n", d);
	printf("d=%c\n", d);
	return 0;
}
```

```
c=1
d=49//1的ASCII码
d=1
```

```c
#include <stdio.h>

int main(int argc, char const *argv[])
{
	char c;
	c = 'A';
	c++;
	printf("%c\n", c);
	return 0;
}
```

```
B
```

### 15.自动类型转换

当运算符的两边出现不一致的类型时，会自动转换为较大的类型，从而表示数的范围也变大

**char->short->int->long->long long**

**int->float->double**

### 16.强制类型转换

把一个量强制转换为另一个类型（通常是较小的类型）

```c
(类型)值；
```

such as 

```c
(int)10.2;
(short)32;
(double)10;
```

**强制类型转换的优先级高于四则运算**

### 17.bool

```c
#include <stdbool.g>
bool flag;
```

### 18.逻辑运算

对逻辑量进行运算，结果只有0和1

| 运算符 |  描述  |  示例  | 结果 |
| :----: | :----: | :----: | :--: |
|   ！   |   非   |   !a   | 取反 |
|   &&   | 逻辑与 |  a&&b  |      |
|  \|\|  | 逻辑或 | a\|\|b |      |

#### 优先级

**!>&&>||**

| 优先级 |         运算符          |  结合性  |
| :----: | :---------------------: | :------: |
|   1    |          （）           | 从左到右 |
|   2    | ! +(单目) -(单目) ++ -- | 从右到左 |
|   3    |          * / %          | 从左到右 |
|   4    |           + -           | 从左到右 |
|   5    |        < <= > >=        | 从左到右 |
|   6    |          == !=          | 从左到右 |
|   7    |           &&            | 从左到右 |
|   8    |          \|\|           | 从左到右 |
|   9    |    == += -= *= /= %=    | 从右到左 |

### 19.条件运算符

**a = x < y ? x : y;**

自右向左结合

### 20.逗号运算

优先级比赋值还低.......主要在for循环中使用

```c
int i;
i = (3+4, 5+6);//i = 11
```



## 第七周：函数

### 1.没有返回值的函数

`void 函数名(参数表)`

不能使用带值的return，也可以没有return

调用的时候不能做返回值的赋值

### 2.函数先后关系

C编译器自上而下分析程序

函数如果没有声明的话，其定义必须在使用之前；

如果实在想放在后面，得在调用前声明一下

### 3.C语言漏洞

调用函数时，参数类型可以不匹配，编译器会自动转换类型

### 4.参数传递

调用函数时，只是**传值**给函数，不是将~~变量~~传入，所以不会改变值，因为作用域的范围不一样

### 5.本地(局部)变量

函数每次运行会产生一个独立的变量空间，在这个空间中的变量，是函数的这次运行所独有的——本地变量

定义在函数内部的变量就是本地变量

参数也是本地变量

### 6.本地变量的规则

本地变量是定义在**块**(实际上就是`{}`)内的

```a
可以定义在函数的块内
可以定义在语句的块内
随便拉一对大括号来定义变量
```

程序运行进入这个块之前，其中的变量不存在，离开这个块，其中的变量就消失了

块外边定义的变量在块里面仍然有效

块里面定义了和块外边**同名的**变量则掩盖了外边的

```c
int a=5;
{
    int a=1;
    printf("%d\n", a);//output: 1
}
printf("%d\n", a);//Output: 5
```

不能在一个块内定义同名的变量

本地变量不会被默认初始化，参数在进入函数时就被初始化了



## 第八周：数组

### 1.定义数组

```c
<类型> 变量名称[元素数量];
int grades[100];
double weight[20];
```

元素数量必须是整数

C99之前：元素数量必须是编译时刻确定的字面量

C99之后：可以使用变量定义数组大小

### 2.数组特点——一种容器

```c
其中所有的元素具有相同的数据类型
一旦创建，不能改变大小
* 数组中的元素在内存中是连续依次排列的
数组下标从0开始
```

### 3.数组的集成初始化

```c
int a[]={1, 2, 3, 4, 5};
int a[5]={2};//a = {2, 0, 0, 0, 0}
```

集成初始化时的**定位**，用`[n]`在初始化数据中给出定位，没有定位的数据接在前面的位置后面，其他位置补0，适合**初始数据稀疏的数组**

```c
int a[10] = {[0]=2, [2]=3, 6};// a = {2, 0, 3, 6, 0, 0, 0, 0, 0, 0, 0}
sizeof(a);//40,一个元素(int)占据四个字节
sizeof(a)/sizeof(a[0]);//10,数组的长度
```

### 4.数组的赋值

**数组本身不能被赋值**

要把一个数组的所有元素赋给另一个数组，必须采用**遍历**

### 5.数组作为函数参数

**必须再用另一个参数来传入数组的大小**

### 6.求素数

```c
#include <stdio.h>

int main()
{
	const int maxNumber = 25;
	int isPrime[maxNumber];
	int i;
	int x;
	for(i=0; i<maxNumber; i++)
	{
		isPrime[i] = 1;
	}
	for(x=2; x<maxNumber; x++)
	{
		if(isPrime[x])
		{
			for(i=2; i*x<maxNumber; i++)
			{
				isPrime[i*x] = 0;
			}
		}
        
	}
	for(i=2; i<maxNumber; i++)
	{
		if(isPrime[i])
		{
			printf("%d\t", i);
		}
	}
	printf("\n");
	return 0;
}
```

```
2       3       5       7       11      13      17      19      23
```

```c
#include <stdio.h>

int main()
{
	const int maxNumber = 25;
	int isPrime[maxNumber];
	int i;
	int x;
	for(i=0; i<maxNumber; i++)
	{
		isPrime[i] = 1;
	}
	//for test
	printf("\t");
	for(i=2; i<maxNumber; i++)
	{
		printf("%d\t", i);
	}
	printf("\n");
	//for test
	for(x=2; x<maxNumber; x++)
	{
		if(isPrime[x])
		{
			for(i=2; i*x<maxNumber; i++)
			{
				isPrime[i*x] = 0;
			}
		}
		//for test
		printf("x=%d\t", x);
		for(i=2; i<maxNumber; i++)
		{
			printf("%d\t", isPrime[i]);
		}
		printf("\n");
		//for test
	}
	for(i=2; i<maxNumber; i++)
	{
		if(isPrime[i])
		{
			printf("%d\t", i);
		}
	}
	printf("\n");
	return 0;
}
```

```
2       3       4       5       6       7       8       9       10      11      12      13      14      15
        16      17      18      19      20      21      22      23      24
x=2     1       1       0       1       0       1       0       1       0       1       0       1       0       1
        0       1       0       1       0       1       0       1       0
x=3     1       1       0       1       0       1       0       0       0       1       0       1       0       0
        0       1       0       1       0       0       0       1       0
x=4     1       1       0       1       0       1       0       0       0       1       0       1       0       0
        0       1       0       1       0       0       0       1       0
x=5     1       1       0       1       0       1       0       0       0       1       0       1       0       0
        0       1       0       1       0       0       0       1       0
x=6     1       1       0       1       0       1       0       0       0       1       0       1       0       0
        0       1       0       1       0       0       0       1       0
x=7     1       1       0       1       0       1       0       0       0       1       0       1       0       0
        0       1       0       1       0       0       0       1       0
x=8     1       1       0       1       0       1       0       0       0       1       0       1       0       0
        0       1       0       1       0       0       0       1       0
x=9     1       1       0       1       0       1       0       0       0       1       0       1       0       0
        0       1       0       1       0       0       0       1       0
x=10    1       1       0       1       0       1       0       0       0       1       0       1       0       0
        0       1       0       1       0       0       0       1       0
x=11    1       1       0       1       0       1       0       0       0       1       0       1       0       0
        0       1       0       1       0       0       0       1       0
x=12    1       1       0       1       0       1       0       0       0       1       0       1       0       0
        0       1       0       1       0       0       0       1       0
x=13    1       1       0       1       0       1       0       0       0       1       0       1       0       0
        0       1       0       1       0       0       0       1       0
x=14    1       1       0       1       0       1       0       0       0       1       0       1       0       0
        0       1       0       1       0       0       0       1       0
x=15    1       1       0       1       0       1       0       0       0       1       0       1       0       0
        0       1       0       1       0       0       0       1       0
x=16    1       1       0       1       0       1       0       0       0       1       0       1       0       0
        0       1       0       1       0       0       0       1       0
x=17    1       1       0       1       0       1       0       0       0       1       0       1       0       0
        0       1       0       1       0       0       0       1       0
x=18    1       1       0       1       0       1       0       0       0       1       0       1       0       0
        0       1       0       1       0       0       0       1       0
x=19    1       1       0       1       0       1       0       0       0       1       0       1       0       0
        0       1       0       1       0       0       0       1       0
x=20    1       1       0       1       0       1       0       0       0       1       0       1       0       0
        0       1       0       1       0       0       0       1       0
x=21    1       1       0       1       0       1       0       0       0       1       0       1       0       0
        0       1       0       1       0       0       0       1       0
x=22    1       1       0       1       0       1       0       0       0       1       0       1       0       0
        0       1       0       1       0       0       0       1       0
x=23    1       1       0       1       0       1       0       0       0       1       0       1       0       0
        0       1       0       1       0       0       0       1       0
x=24    1       1       0       1       0       1       0       0       0       1       0       1       0       0
        0       1       0       1       0       0       0       1       0
2       3       5       7       11      13      17      19      23
```

### 7.二维数组初始化

```c
int a[][5] = {
    {0, 1, 2, 3, 4},
    {1, 2, 3, 4, 5},
};
```

**列数**是必须给出的，行数可以由编译器来数

每行一个`{}`,用`,`隔开

如果省略，表示补零

可以使用**定位**



## 第九周：指针

### 1.运算符&——取地址

获得**变量的地址**，操作数必须是**变量**

```c
#include <stdio.h>

int main()
{
	int i = 0;
	printf("0x%x\n", &i);
	printf("%p\n", &i);
	
	return 0;
}
```

```
0x62fe1c
000000000062FE1C
```



```c
#include <stdio.h>

int main()
{
	int i = 0;
	int p;
	printf("0x%x\n", &i);
	printf("0x%x\n", &p);
	
	return 0;
}
```



```
0x62fe1c
0x62fe18
```

### 2.数组的地址

```c
#include <stdio.h>

int main()
{
	int a[10];

	printf("%p\n", &a);
	printf("%p\n", a);//数组变量本身就是表达地址
	printf("%p\n", &a[0]);//数组a的地址=a[0]的地址
	printf("%p\n", &a[1]);

	return 0;
}
```

```
000000000062FDF0
000000000062FDF0
000000000062FDF0
000000000062FDF4//int为四个字节
```

### 3.指针

保存地址的变量

```c
int i;
int* p = &i;//此时p里面放的就是i的地址
int* p,q;//与下式效果相同，*p为int型指针，q为int型变量，不是int*代表指针
int *p,q;
```

### 4.指针变量

**指针变量的值是内存的地址**

普通变量的值是实际的值

指针变量的值是具有实际值的变量的地址

### 5.作为参数的指针

```c
void f(int *p);
```

被调用的时候得到了某个变量的地址

```c
int i=0;
f(&i);
```

在函数里面可以通过这个指针访问外面的这个`i`

### 6.访问那个地址上的变量`*`——访问地址

`*`是一个单目运算符，用来**访问**指针的值所表示的地址上的变量

可以做左值，也可做右值

```
int k = *p;//将p地址的值赋给k
*p = 5;//*p即表示地址为p单元的值
```

### 7.指针的运算符**&**和*****

相互反作用

```c
*&yptr -> *(&yptr) -> *(yptr的地址) -> 得到那个地址上的变量 ->yptr
&*yptr -> &(*yptr) -> &(y) -> 得到y的地址，即yptr -> yptr
```

### 8.指针的应用

#### 交换变量的值

```c
#include <stdio.h>

void swap(int *pa, int *pb);//int *pa是定义指针型变量

int main()
{
	int a=5;
	int b=6;
	swap(&a, &b);
	printf("a=%d, b=%d\n", a, b);

	return 0;
}

void swap(int *pa, int *pb)
{
	int t = *pa;//访问地址为pa的变量
	*pa = *pb;
	*pb = t;
}
```

```
a=6, b=5
```

#### 函数返回多个值，某些值只能通过指针返回

传入的参数实际上是需要保存带回的结果的变量

```c
#include <stdio.h>

void minmax(int a[], int len, int *max, int *min);

int main(int argc, char const *argv[])
{
	int a[] = {1, 2, 3, 4, 5, 6, 7, 8,};
	int min, max;
	minmax(a, sizeof(a)/sizeof(a[0]), &max, &min);
	printf("max=%d, min=%d\n", max, min);
	return 0;
}

void minmax(int a[], int len, int *max, int *min)
//a[]实际上是数组的指针，[]不能少，可以替换为*a
{
	int i;
	*min = *max = a[0];
	for(i=1; i<len; i++)
	{
		if(a[i] < *min)
		{
			*min = a[i];
		}
		if(a[i] > *max)
		{
			*max = a[i];
		}
	}
}
```

```
max=8, min=1
```

### 9.函数参数表中的数组

实际上是**指针**

**数组变量本身就是表达地址**

```c
int a[10];
int *p = a;//无需用&取地址，但是数组的单元表达的是变量，需要用&取地址
```

数组变量是`const`的指针，所以不能被赋值，数组变量之间不能互相赋值

```c
int a[]相当于int * const a;
```

### 10.指针是`const`类型

表示一旦得到了某个变量的地址，**不能再指向其他变量**

```c
int i;
int * const q = &i;//q是const类型
*q = 26;//相当于i = 26;
q++;//这会报错，因为q是const类型的，不会改变了
```

### 11.所指是`const`

表示**不能通过这个指针去修改那个变量**(并不能使得那个变量成为`const`)

```c
const int *p = &i;
*p = 26;//ERROR!(*p)是const
i = 16;//OK
p = &j;//OK
```

### 12.傻傻分不清楚

```c
int i;

const int* p = &i;//通过指针不可修改
int const* p = &i;//通过指针不可修改

int *const p = &i;//指针不可修改
```

判断哪个被`const`了的标志是看`const`在 `*` 的前面还是后面

### 13.const数组

```c
const int a[] = {1, 2, 3, 4, 5,};
```

数组变量已经是const的指针了，这里的const表明数组的**每个单元**都是`const int`，必须**通过初始化进行赋值**

#### 应用：保护数组值

因为把数组传入函数时传递的是地址，所以那个函数内部可以修改数组的值

为了保护数组不被函数破坏，可以设置参数为`const`

```c
int sum(const int a[], int length);
```

### 14.指针运算

```c
#include <stdio.h>

int main(int argc, char const *argv[])
{
	char ac[]={1, 2, 3, 4, 5, 6,}
	char *p = ac;//*(p+n)=ac[n],attention here
	printf("p  =%p\n", p);
	printf("p+1=%p\n", p+1);
	char ad[]={1, 2, 3, 4, 5, 6,}
	char *q = ad;//*(q+n)=ad[n],attention here
	printf("q  =%p\n", q);
	printf("q+1=%p\n", q+1);
	return 0;
}
```

```
p  =000000000062FE00
p+1=000000000062FE01//char是一个字节的
q  =000000000062FDE0
q+1=000000000062FDE4//int是四个字节长度的
```

|      指针运算      |                            |
| :----------------: | :------------------------: |
| 给指针加减一个整数 |        +、-、-=、+=        |
|      递增递减      |           ++、--           |
|    两个指针相减    | 两地址之间可以存放的单元数 |

### 15.  `*p++`

取出p所指的那个数据后，顺便把p移到下一个位置去，相当于`*(p++)`

*****的优先级没有**++**高

常用于数组类的连续空间操作

### 16.指针比较

<, <=, ==, >, >=, !=都可以对指针做

比较它们在内存中的地址

数组中的单元的地址肯定是线性递增的

### 17.0地址

0地址通常是个不能随便碰的地址，指针不应该具有0值

###### 可以用0地址来表示特殊的事情

返回的指针是无效的

指针没有被真正初始化(先初始化为0)

**NULL**是一个预定义的符号，表示0地址

### 18.指针的类型转换

`void*` 表示不知道指向什么东西的指针，计算时与`char*`**相同（但不相通）**

指针可以强制类型转换

```c
int *p = &i;
void *q = (void*)p;//并没有改变p所指的变量的类型，而是通过q，使用不同的眼光来看p所指的变量
```

### 19.指针的用处

需要传入较大的数据时用作参数

传入数组后对数组做操作

函数返回不止一个结果，需要用函数来修改不止一个变量

### 20.动态申请的内存

```c
#include <stdlib.h>
void* malloc(size_t size);
```

向`malloc`申请的空间大小是以字节为单位的

返回的结果是`void*`，需要类型转换为自己需要的类型

```c
int *p;
p = (int*) malloc(n*sizeof(int));
free(p);//用完就得释放，只需释放申请空间的首地址即可
```

在同一个地方`malloc`和`free`，除非函数的作用就是分配空间，否则不要在函数中malloc然后传出去用

**函数返回数组和返回指针是一样的，实际上返回的就是数组的地址**



## 第十周：字符串

### 1.字符串

以0(整数0)或'\0'结尾的一串字符，但是不是'0'，标志着字符串的结束，但是不是字符串的一部分，计算字符串长度的时候不包含这个0

#### 字符串以数组的形式存在，以数组或指针(常用)的形式访问

可以通过数组的方式遍历字符串，但不能用运算符对字符串做运算，可以用字符串字面量来初始化字符数组

string.h 里面有很多处理字符串的函数

### 2.字符串变量

```c
char *str = "Hello";
char word[] = "Hello";
char line[10] = "Hello";
```

### 3.字符串常量

```
"Hello"
实际上是{"H", "e", "l", "l", "o", "\0"}
```

两个相邻的字符串常量会被自动连接起来

```c
printf("这是这句话的一部分"
      "这也是这句话的一部分")
printf("这是这句话的一部分，\
这也是这句话的一部分");// \起到了连接作用
```

```c
char* s = "Hello World!";
```

s是一个指针，初始化为指向一个字符串常量，上句实际上是`const char* s`,所以字符串s是只读的，不可以写入

如果需要修改字符串，应当用数组来定义字符串

```c
char s[] = "Hello World!";
```

### 4.指针还是数组

#### 数组——构造一个字符串

```c
char word[] = "hello";
```

知道字符串的位置，作为本地变量空间自动被回收

#### 指针——处理一个字符串

```c
char *str = "hello";
```

不知道字符串的位置，处理参数，动态分配空间

### 5.char*是字符串？

字符串可以表达为`char*`，但`char*`不一定是字符串，可能是指向的是字符的数组(类似于`int*`)，而且只有他所指的字符数组的结尾有0，指向的才是字符串

### 6.字符串赋值？

```c
char *t = "title";
char *s;
s = t;
```

并不是重新给s产生一个新的字符串，只不过是s和t都指向了"title"字符串，对s做任何操作就是对t做的

### 7.字符串输入输出

```c
char string[8];
scanf("%s", string);
printf("%s", string);
```

scanf读入一个单词（以空格、tab或回车为分隔），不安全，不知道要读入的长度

###### 安全输入

```c
char string[8];
scanf("%7s", string);//表示最多允许读入7个
```

### 8.常见错误

```c
char *string;
scanf("%s", string);
```

以为char*是字符串类型，定义了一个字符串类型的变量string就可以直接使用了

没有对string初始化为0，不一定每次运行都会报错

### 9.空字符串

```c
char buffer[100] = "";//空字符串，buffer[0] == '\0'
char buffer[] = "";// 该数组的长度只有1...
```

### 10.字符串数组

```c
char **a;//a是一个指针，指向另一个指针，那个指针只想一个字符(串)
char a[][];//a的第二个维度不知道，不能编译
char a[][10];//a是一个二维数组，每一行都是一个长度为10的char
char *a[];//a是一个一维数组，其中的每一个元素都是一个指针char*
```

### 11.字符串输入输出

