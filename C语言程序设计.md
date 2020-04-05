



# C语言程序设计



## 第一周：绪论

### 1.程序的执行

__解释__: 借助一个程序，该程序试图理解你编写的程序，然后按照你的要求执行程序

__编译__：借助一个程序，像是一个翻译，把你写的程序翻译为计算机的语言（**机器语言**），然后执行

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

**<类型名称> <变量名称1>=<初始值1>,<变量名称2>=<初始值2>;**

### 4.读整数

```c
int price=0;

scanf("%d", &price);
```



### 5.常量

固定不变的数——常数，直接写在程序里，称为**直接量**(**literal**)

定义一个常量

```c
const int AMOUNT = 100; 
```

通常给常量的命名为全大写字母

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

float——单精度浮点数

double——双精度浮点数

### 10.double类型注意

输入输出

```c
double a, b;
scanf("%lf %lf", &a, &b);//注意是%lf表示double
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

### 16. 递增递减运算符

都是单目运算符，且算子必须为变量

递增运算符++

```c
count++;
count += 1;
count = count + 1;
```

递减运算符--

```c
count--;
count -= 1;
count = count - 1;
```


```c
#include <iostream>
#include <stdio.h>
/* run this program using the console pauser or add your own getch, system("pause") or input loop */

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
/* run this program using the console pauser or add your own getch, system("pause") or input loop */

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
/* run this program using the console pauser or add your own getch, system("pause") or input loop */

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
/* run this program using the console pauser or add your own getch, system("pause") or input loop */

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
/* run this program using the console pauser or add your own getch, system("pause") or input loop */

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

