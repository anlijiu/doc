### Expr  代数表达式

Expression -> Expression + Term | Term

由 + 或 - 号分隔的代数表达式的几个部分称为表达式的项。这些项可以是单个数字、变量或数字和变量的乘积 。根据项数，多项式分为单项式、二项式、三项式。因此，我们得到了源自希腊词poly和nomial 的多项式的多项式含义。这些术语可以是相似的术语或不同的术语。

2a 2b有一项。是单项式的。
2xy - 3 有 2 个项，称为二项式。
x 2  + 3x + 2 有 3 项并且是三项式。 

通常表达式产生新值

### Term  项

Term -> Term x Factor | Factor

### Factor 因子

Factor -> Expression | a

5y 表示为 5 * y， 所以5和y都是  term 5y的 factors
将术语表示为 2 个或更多变量或数字的乘积称为分解。我们可能需要分解任何给定的代数表达式。
y^2 + y 可以表示为 y * (y + 1) , 所以 y 和 y+1 都是  y^2 + y 的因子factors
a^2 - b^2 可以表示为 (a+b)(a-b)， 所以 a+b 和 a-b 都是a^2 - b^2的因子factors

### Coefficients 系数
对于 4a^2 来说，  4 是 a^2 的数值系数(numerical coefficient),  a^2 是 4 的字面系数(literal coefficient).
对于 12n 来说， 12 是 n 的数值系数.
如果没有数字， 那么认为数值系数为1.
例如expr:  a^2 + b， 那么 term a^2 的数值系数为1,  term b 的数值系数为1
拥有相同字面系数的 terms 被成为相似项(liked terms), 不同字面系数的为不同项

例如 3x^3 ,   -x^3,  2x^3  这三个terms拥有相同的字面系数 x^3 ， 所以这三个项为相似项
2x^2, 6x, -x^4 这三个terms字面系数不同， 所以为不同项

![expr-term-factor](https://raw.githubusercontent.com/anlijiu/doc/assets/expression-term-factor-coefficient.png)

### 例子  a^2 - 6a + 9
Terms(项):  a^2, 6a, 9    三个terms
Variables(变量): a^2, a   两个variables 
Constants(常数): 9
Factors(因子): a 是 term1 的factor
               -6 和 a 是 term2 的factors
               9 是 term3 的factor
Coefficients(系数):  1 是 a^2 的系数
                    -6 是 a 的系数
                    9 是常数项的系数
Operators(运算符): - and +

https://zhuanlan.zhihu.com/p/362072187

https://zhuanlan.zhihu.com/p/363588226

### Statement 语句
语句是命令式编程语言的句法单元，表示要执行的某些操作。
程序由一个或多个语句的序列组成。
语句可能具有内部组件（例如，expressions）。
expression是表达式，不是程序。表达式可被求值。 如 3 + 5,  (let b = 3) in b + 5
而statement，可以理解为最短的程序。语句不一定有值。 如 a = 3 + 5 ( let a = 3 + 5)
程序由语句和表达式组成。
1. 表达式有值，语句没有值， 能作为函数参数即为表达式，否则为语句。
2. C语言中的控制结构为语句。
3. 函数式语言中的所有东西都有值， 都是表达式

声明式语言一般有三种statement
Expression statements: change values of variables, call methods, and create objects.
Declaration statements: declare variables.
Control-flow statements: determine the order that statements are executed. 

### reference
+ [rust reference](https://doc.rust-lang.org/stable/reference/)
+ [java18 specification](https://docs.oracle.com/javase/specs/jls/se18/html/index.html)
