# Java基础文档

[TOC]

> Java跨平台语言
>
> 跨平台示意图:
>
> > ![Java从零学习-Java跨平台特性.drawio](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409171056147.png)
> >
> > 编译:
> >
> > ![image-20240917110539504](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409171105614.png)

# 一、Java基础

##  1、转义字符

```java
// 演示转义字符使用
public class ChangeChar{
	public static void main(String args[]){
		// \t:制表符
		// System.out.println("北京\t天津\t上海");
		// \n:换行符
		// System.out.println("jack\nsmith\nmary");
		// \\: \
	   //System.out.println("C:\\Windows\\System32\\cmd.exe");
		// \": "
		// System.out.println("我说:\"要好好学习编程\"");
		// \': '
		// System.out.println("我说:\'要好好学习编程\'");
		// \r: 回车
		System.out.println("朱鹏材\r云南"); // 云南材
	}
}
```

- 练习输出以下格式

  ` 书名	作者	价格	销量`

  `三国	罗贯中	120	1000`

  ```java
  // 练习输出:
  // 书名 作者 价格 销量
  // 三国 罗贯中 120 1000
  
  public class ChangeCharTest{
  	public static void main(String args[]){
  		// System.out.println("书名\t作者\t价格\t销量");
  		// System.out.println("三国\t罗贯中\t120\t1000");
  		System.out.println("书名\t作者\t价格\t销量\n三国\t罗贯中\t120\t1000");
  	}
  }
  ```

## 2. 注释

> 用于解释说明程序的文字就是注释，提高代码可读性

1. 单行注释

   ```java
   // 单行注释
   ```

   

2. 多行注释

   ```java
   /*
   * 多行注释
   */
   ```

   

3. 文档注释

   > 注释内容可以被JDK提供的工具javadoc所解析，生成一套以网页文件形式体现该程序的说明文档，一般写在类上。 

   - 基本格式

     ```java
     /**
      * @author 朱鹏材
      * @version 1.0
      * */
     public class Comment01{
     	public static void main(String args[]){
     
     	}
     }
     ```

   - 如何生成对应的文档注释
     ```bash
     # -xx -yy 指的是注释中的关键词
     javadoc -d 文件夹名 -xx -yy Demo3.java
     ```

   - 应用实例
    ![image-20240917115150444](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409171151740.png)
   
## 3. Java代码规范

![image-20240917115401447](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409171154561.png)

## 4. 变量

> 变量是程序的基本组成原理。
>
> 变量有三个基本要素（类型+名称+值）

- 变量基本原理

![Java从零学习-Java变量原理.drawio](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409171219889.png)

```java
/**
 * @author zpc
 * @version 1.0
 * */
public class Var01{
	public static void main(String args[]){
	          int a; 
	          a =100; // 定义变量
	          System.out.println("a="+a);
	}
}
```

- **基础数据类型**

| 变量类型 | 所占字节数(B) | 范围                                               |
| :------: | :-----------: | -------------------------------------------------- |
| long(L)  |       8       | -($2^{63}$)~$2^{63}$-1                             |
|   int    |       4       | -($2^{31}$)~ $2^{31}$-1(-22147483648~-22147483647) |
|  short   |       2       | -($2^{15}$) ~ $2^{15}$-1(-32768~32767)             |
|   byte   |       1       | -128~127                                           |
|   char   |       1       | -128~127                                           |
| float(F) |       4       | -($2^{31}$)~ $2^{31}$-1(-22147483648~-22147483647) |
|  double  |       8       | -($2^{63}$)~$2^{63}$-1                             |
| boolean  |       1       | -128~127                                           |

- **引用数据类型**
  
    - 类(class)
    - 接口(interface)
    - 数组([])
    
- **科学计数法**
  > $5.12e2[5.12*10^{2}]$
  >
  > $5.13E-2[5.12*10^{-2}]$

### 1. 浮点数计算陷阱

```java
public class FloatDetail{
    public static void main(String args[]){
        double num1 = 2.7;
        double num2 = 8.1/3;
        System.out.println(num1); // 2.7
        System.out.println(num2); // 接近2.7的一个小数
        // 当计算结果为小数时并进行相等判断时，要小心
        if(num1==num2){
            System.out.println("equals");
        }
        // 正确比较方法： 通过计算两个数的差值的绝对值，在某个精度范围内判断
        // if(Math.abs(num1-num2)){
           // System.out.println("equals");
        //}
        
    }
}
```

### 2. Java API文档

[中文在线文档](https://www.matools.com/api/java8)

![Java从零学习-Java类的组织形式.drawio](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409172019578.png)

### 3. 自动类型转换细节

> `(byte,short)和char类型不能相互转化`

> - byte，short,char 三者可以计算，计算时首先转换为int类型
>
> - boolean 不参与转换
> - 自动提升原则： 表达式结果的类型自动提升为 操作数中最大的类型

### 4.强制类型转换

> - 强转符号只针对最近的操作数有效，往往会使用小括号提升优先级。
> - char类型可以保存int的常量值，但不能保存int的变量值，需要强制类型转换。
>
>  ```java
>  char c1 = 100; // ✅
>  int m = 100;
>  char c2 = m; // ✖️
>  char c3 = (char)m;
>  ```
>
> 

###  5.基本数据类型和字符串(String)互转

> - 基本数据类型转字符串：
>    - 语法： 将基本数据类型的值+`“”`
>
>    ![image-20240917221744952](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409172217034.png)
>    
> - String转换为基本数据类型:
>     - 语法: 通过基本类型的包装类调用parsexx方法
>     
>     ![image-20240917221724570](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409172217651.png)

### 6.数据类型

![image-20240918142709602](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409181427724.png)

## 5.运算符

> 运算符是一种特殊的符号，用以表示数据的运算、赋值和比较等

###  1.算数运算符

![image-20240917222557654](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409172225775.png)

### 2.赋值运算符



### 3.关系运算符[比较运算符]

![image-20240917222623408](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409172226516.png)

### 4.逻辑运算符

![image-20240917222720010](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409172227138.png)

### 5.位运算符[需要二进制基础]

![image-20240917222921975](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409172229126.png)

![image-20240917222959388](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409172229513.png)

### 6.三元运算符

 ![image-20240917222742200](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409172227300.png)

### 7.算符优先级

![image-20240917222855109](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409172228213.png)

## 6.控制结构

### 1.顺序结构

> 程序从上到下执行，中间没有任何判断和跳转

![image-20240918131614877](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409181316001.png)

### 2.分支结构（if,else,switch）

#### 单分支

>  ![image-20240918131738237](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409181317402.png)
>
> ![image-20240918131852649](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409181318821.png)

#### 双分支

>  ![image-20240918131916096](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409181319307.png)
>
>  ![image-20240918131943068](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409181319286.png)

#### 多分支

>  ![image-20240918132140370](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409181321509.png)
>
>  ![image-20240918132215080](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409181322176.png)

#### 嵌套分支

![image-20240918132503751](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409181325008.png)

#### switch分支结构

![image-20240918132545011](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409181325144.png)

![image-20240918132552977](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409181325075.png)

![image](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409181326419.png)

### 3.🚩循环控制（for,while,dowhile,多重循环）

#### for循环

> 化繁为简，先死后活
>
> 1. 化繁为简: 即将复杂需求，拆解成简单的需求，逐步完成
> 2. 先死后活： 先考虑固定值，然后转成可以灵活变化的值

![image-20240918132921621](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409181329725.png)

![image-20240918132936913](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409181329051.png)

#### while循环

![image-20240918133410849](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409181334001.png)

![image-20240918133441804](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409181334904.png)

#### dowhile循环

![image-20240918133503163](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409181335304.png)

#### 多重循环

![image-20240918133601426](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409181336633.png)

#### 练习

![image-20240918135947709](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409181359034.png)

```java
/**
 * @author zpc
 * @version 1.0
 * @desccription:
 *      空心金字塔
 *          *
 *        *   *
 *      *       *
 *     * * * * * *
 * */
public class Stars{
	public static void main(String[] args){
		// 打印金字塔
		for(int i=1;i<=5;i++){
			// 打印空格 = (总层数-当前层)
			for(int k=1;k<=5-i;k++){
				System.out.print(" ");
			}
			// 打印星号
            for(int j=1;j<=2*i-1;j++){
            	// 镂空=> 当前层第一个位置和最后一个位置打印*
            	if(j==1||j==2*i-1 || i==5){
                    System.out.print("*");     
            	}else{
            		System.out.print(" ");
            	}
            }
            System.out.println("");
 		}
	}
}

```



### 4.break

![image-20240918141016520](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409181410691.png)

![image-20240918141222897](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409181412206.png)

### 5.continue

![image-20240918141244469](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409181412704.png)

### 6.return

![image-20240918141922746](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409181419940.png)

## 🚩7.数组

### 1. 数组

> 数组可以存放等多个同一数据类型的数据。数组也是一种数据类型，是引用数据类型：即数组就是一组数据。

![image-20240918143221653](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409181432886.png)

![image-20240918143320298](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409181433488.png)

![image-20240918143400135](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409181434318.png)

![image-20240918143420561](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409181434842.png)

#### 练习01

> 创建一个char类型数组存储26个英文字母，并打印

```java
/**
 * @author zpc
 * @version 1.0
 * @description:
 *     创建一个char类型数组存储26个英文字母，并打印
 * */

 public class ArrayExercise01{
 	public static void main(String[] args){
             char[] chars = new char[26];
             for(int i=0;i<chars.length;i++){
             	chars[i] = (char) (i+'A'); // i+'A'->int 需要强制转换为char
             }
             printAlphabet(chars);
 	}

 	public static void printAlphabet(char[] arr){
 		for(int i=0;i<arr.length;i++){
 			System.out.print(arr[i]+"\t");
 		}
 	}
 }
```

#### 练习02

> 请求出一个数组中的int[]的最大值，{4,-1,9,10,23} 并得到对应的下标

```java
/**
 * @author zpc
 * @version 1.0
 * @description:
 *     请求出一个数组中的int[]的最大值，{4,-1,9,10,23} 并得到对应的下标
 * */

 public class ArrayExercise02{
 	public static void main(String[] args){
             int[]  arr = {4,-1,9,10,23};
             int result = findMax(arr);
             System.out.println("最大值为: "+arr[result]+"下标为: "+result);
 	}

 	public static int findMax(int[] arr){
        int maxIndex = 0;
 		for(int i = 0;i<arr.length;i++){
 			if(arr[maxIndex]<arr[i]){
                 maxIndex = i;
            }
 		}
        return maxIndex;
 	}
 }
```

#### 3. 数组赋值机制

![image-20240918145756424](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409181457595.png)

![Java从零学习-Java数组赋值机制.drawio](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409181523036.png)

#### 4.数组反转

```java
/**
 * @author zpc
 * @version 1.0
 * @description 
 *      数组反转
 * */
public class ArrayReverse{
	public static void main(String[] args){
		int[] arr ={11,22,33,44,55};
		int len = arr.length;
		printIntArr(arr);
		for(int i=0;i<len/2;i++){
                int tmp = arr[len-1-i];
                arr[len-1-i] = arr[i];
                arr[i] = tmp;
		}
		printIntArr(arr);
	}

	static void printIntArr(int[] arr){
           for(int i=0;i<arr.length;i++){
           	      System.out.print(arr[i]+"\t");
           }
           System.out.println("");
	}
}
```

#### 5.数组扩容

> ![image-20240918153707774](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409181537925.png)

```java
import java.util.Scanner;
/**
 * @author zpc
 * @version 1.0
 * @description
 *      数组扩容，通过控制台输入，动态添加元素
 * */
public class ArrayAdd02{
 	public static void main(String[] args){
         // 思路分析:
 		   /*
              1. 定义初始化数组: int[] arr = {1, 2, 3} // 下标0-2
              2. 定义一个新的数组: int[] arrnew = new int[arr.length+1];
              3. 遍历arr数组将arr中的元素值拷贝到新数组arrnew中
              4. 将新增的值赋值: 4 = arrnew[arrnew.length-1]
              5. 将arr指向arrnew: arr = arrnew; // 修改指向 
              6. 创建Scanner可以接受用户输入
              7. 因为用户什么时候退出，不确定 ， 使用do-while+break控制
 		   */
                 
           Scanner sc = new Scanner(System.in);  // 创建Scanner对象
           int[] arr={1, 2, 3};
           do{
                 System.out.println("原数组:");
                 printIntArr(arr);
                 int[] arrnew = new int[arr.length+1]; 
                 // 拷贝数组
                 for (int i=0;i<arr.length;i++ ) {
                       arrnew[i] = arr[i];
                 }
                 System.out.println("请输入要添加的整数: "); 
                 // 接收输入数字
                 int addele = sc.nextInt();
                 // 赋值新元素到数组的最后位置
                 arrnew[arrnew.length-1] = addele;
                 arr = arrnew;
                 System.out.println("增加元素扩容后数组： ");
                 printIntArr(arrnew);
                 System.out.println("是否继续添加元素y/n？🤔");
                 char key = sc.next().charAt(0);
                 if(key=='n'){
                     break;
                 }
           }while(true);
           
	}
 	public static void printIntArr(int[] arr){
           for(int i=0;i<arr.length;i++){
           	      System.out.print(arr[i]+"\t");
           }
           System.out.println("");
	}
}
```

## 🚩8.面向对象基础

###  1.类

> ![image-20240918231509529](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409182315784.png)
>
> ![image-20240918231624975](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409182316095.png)

### 2.对象内存布局

> ![Java从零学习-Java对象内存布局.drawio](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409182331419.png)
>
> ![image-20240918233159948](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409182332161.png)

###  3.创建对象

![image-20240918233306057](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409182333206.png)

### 4.对象创建过程

![Java从零学习-Java对象创建过程.drawio](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409182349565.png)

![image-20240918235031527](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409182350788.png)

### 5.成员方法

![image-20240918235156523](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409182351673.png)

![image-20240918235230456](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409182352603.png)

### 6.方法调用机制

![Java从零学习-Java方法调用机制.drawio](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409190015984.png)

### 7.成员方法的好处

![image-20240919001729986](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409190017125.png)

### 8.成员方法定义

![image-20240919001808035](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409190018224.png)

### 9.方法使用细节

![image-20240919001902580](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409190019813.png)

![image-20240919001930567](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409190019833.png)

![image-20240919002010197](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409190020421.png)

### 10. 方法传参机制

> **🔴重点掌握方法参数到底是传值还是传地址**

![image-20240919002654583](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409190026735.png)

![image-20240919002921582](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409190029722.png)

### 11.方法递归调用

![image-20240919003511363](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409190035513.png)

![image-20240919003908480](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409190039660.png)

#### **递归机制**

![image-20240919004721692](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409190047848.png)

#### **递归重要原则**

![image-20240919094819973](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409190948206.png)

#### **递归斐波那契数列**

```java
/**
 * @author zpc
 * @version 1.0
 * @description 
 *     斐波那契数列
 * */
public class RecursionExercise {
	public static void main(String[] args) {
		/*
		  使用递归求斐波那契额数列1,1,2,3,5,8....
		*/
		int n = -1;
		Tool tool = new Tool();
        int result = tool.fibonacci(n);
        if(result != -1) {
             System.out.println("当n= "+n+"时"+"斐波那契数为: "+result);
        }else {
             System.out.println("要求输入的n>=1的整数。");
        }
        
	}
}

class Tool {
	/*
        思路分析:
          1. 当n = 1 数列为1
          2. 当n = 2 数列为1
          3. 当n = 3 数列为2
          4. 当n = 4 数列为5
          .................
          .................
          n-2. 当n = n-1 数列为m
          n-1. 当n = n-2 数列为t
          n. 当n = n 数列为 m+t
	*/

	public int fibonacci(int n) {
		if(n>=1) {
            if(n==1 || n==2) {
	           return 1;
			} else {
	           return fibonacci(n-1)+fibonacci(n-2);
			}
		}else {
             return -1;
		}
	}
}
```

#### **猴子吃桃**

![image-20240919102053909](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409191020095.png)

```java
/**
 * @author zpc
 * @version 1.0
 * @description 
 *     斐波那契数列
 * */
public class RecursionExercise {
	public static void main(String[] args) {
		Tool tool = new Tool(); // 创建对象
        /*
         猴子吃桃： 有一堆桃子，猴子第一天吃了其中一半，并再多吃一个，以后每天猴子都吃一半，
         然后再多吃一个。当第10天时，想再吃时，发现只有1个桃子了。问：最初共多少个桃子?
        */
        int day = 1;
        int peachNum =  tool.peach(day);
        if(peachNum != day){
              System.out.println("最初有: "+peachNum+"个桃子。");
        }


        
	}
}

class Tool {
	/*
      猴子吃桃： 有一堆桃子，猴子第一天吃了其中一半，并再多吃一个，以后每天猴子都吃一半，
      然后再多吃一个。当第10天时，想再吃时，发现只有1个桃子了。问：最初共多少个桃子?
	  思路分析
	  10. day10 = 10 1
	  9. day9 = (day10+1)*2 = 4
	  8. day8 = ((day10+1)*2+1)*2 = 10
	  ...............................
	  1. day1 = (day2+1)*2
	*/
    public int peach(int day){
    	if(day == 10){
             return 1;
    	}else if ( day >= 1 && day <= 9 ) {
           return (peach(day+1)+1)*2;
    	}else{
    		System.out.println("day需要再1-10之间");
    		return -1;
    	}
    }


}
```

#### **迷宫问题**

![image-20240919193720985](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409191937214.png)

```java
/**
 * @author zpc
 * @version 1.0
 * @description 
 *    迷宫问题
 * */
public class MiGong{
	public static void main(String[] args){
		// 思路分析
		// 1. 创建一个二维数组存储迷宫 int[][] map = new int[8][7]
		// 2. 先规定map 数组的元素值: 0元素表示可以走 1表示障碍物
		int[][] map = new int[8][7];
		// 3. 将上面的一行和最下面的一行，全部设置为1
		for(int i = 0; i < 7; i++){
            map[0][i] = 1;
            map[7][i] = 1;
		}
		// 4. 将最左边和最右边的列，全部设置为1
		for(int i = 1; i < 7; i++){
            map[i][0] = 1;
            map[i][6] = 1;
		}
		// 设置障碍物
		map[3][1] = 1;
		map[3][2] = 1;
		// 打印地图
		showMap(map);
		// findWay
		Tool tool = new Tool();
		tool.findWay(map, 1, 1); // 寻找出路
		// 此时地图
		showMap(map);
	}

	public static void showMap(int[][] map){
		  System.out.println("当前地图: ");
          for(int i = 0; i < 8; i++){
          	  for(int j = 0; j < 7; j++){
          	  	  System.out.print(map[i][j]+" "); // row
          	  }
          	  System.out.println(""); // \n
          }
	}
}


class Tool{
	// 使用递归回溯的思想来解决老鼠出迷宫问题
	/*
	  1. findWay方法就是专门找出迷宫的路
	  2. 如果找到，就返回true,否则返回false
	  3. map 就是二维数组，即表示迷宫
	  4. i,j就是老鼠的位置，初始化的位置为(1,1)
	  5. 因为我们是递归的找路，所以先定义map数组的各个值的含义
	    - 0 表示可以走的路
        - 1 表示有障碍物
        - 2 表示可以走（走过，可以走通）
        - 3 表示走过，但是走不通是思路
      6. 当map[6][5] = 2时说明找到通路，否则就继续寻找
      7. 先确定老鼠找路策略 下->右->上->左
	*/
	public boolean findWay(int[][] map,int i, int j){ // i 行 j 列
		if(map[6][5] == 2){
            return true;
		} else {
          if(map[i][j] == 0){
          	 map[i][j] = 2;
          	 if(findWay(map, i+1, j)){  // 下
                 return true;
          	 } else if(findWay(map, i, j+1)) { // 右
                  return true;
          	 } else if(findWay(map, i-1, j)){ // 上
                  return true;
          	 } else if(findWay(map, i, j-1)){ // 左
                  return true;
          	 } else {
          	 	  map[i][j] = 3; // 此路不同
          	 	  return false;
          	 }
          } else {// map[i][j] = 1 | 2 | 3
              return false;
          }
		}
	}
}
```

####  **汉诺塔**

```java
/**
 * @author zpc
 * @version 1.0
 * @description
 *    汉诺塔
 * */
public class HanoiTower {
	public static void main(String[] args) {
           Tower tower = new Tower();
           tower.move(5, 'A', 'B', 'C');
	}
}


class Tower {

	// num 表示要移动的个数 a,b,c 分别表示A塔，B塔，C塔
    public void move(int num, char a, char b, char c) {
    	// 如果只有一个盘的时候 num = 1
    	if(num == 1){
    		System.out.println(a+"->"+c);
    	} else {
    		// 如果有多个，可以看成是两个，最下面的盘和上面的所有盘
    		// (1) 先移动上面所有的盘到b，借助c
    		move(num-1, a, c, b);
    		// (2) 下面的所有盘移动到c
    		System.out.println(a + "->" + c);
    		// (3) 再把b塔的所有盘移动到c,借助a
    		move(num-1, b, a, c);
    	}
    }
}
```

#### **八皇后问题（TODO）**

![image-20240919231351956](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409192313170.png)

```java
```

### 马踏棋盘

```java
package com.zpc;

import java.awt.*;
import java.util.ArrayList;

/**
 * @author : zpc20 //作者
 * @version : 1.0 // 版本
 * @ClassName : Main  //类名
 * @Description : 马踏棋盘  //描述
 * @Date: 2024-09-30  上午 12:23
 */
public class Main {

    private static int X = 6; // 列
    private static int Y = 6; // 行
    private static int[][] board = new int[Y][X]; // 棋盘
    private static boolean[] visited = new boolean[X * Y]; // 记录某个位置是否走过
    private static boolean finished = false; // 记录马儿是否遍历完棋盘

    public static void main(String[] args) {
        printBoard(board);
        long start = System.currentTimeMillis();
        traversalChessBoard(board, 4, 4, 1);
        long end = System.currentTimeMillis();
        System.out.println("耗时: "+(end-start));
        printBoard(board);
    }

    public static void traversalChessBoard(int[][] chessBoard, int row, int col, int step) {
        // 记录board
        chessBoard[row][col] = step;
        // 把这个位置设置为访问
        visited[row * X + col] = true;
        // 获取可做位置
        ArrayList<Point> points = nextStep(new Point(col, row));
        sort(points); // 排序升序，使得取出的点集是最少的
        // 遍历
        while (!points.isEmpty()) {
            // 取出当前数组的第一个位置
            Point p = points.remove(0);
            // 判断是否走过，未走过，则递归遍历
            if (!visited[p.y * X + p.x]) {
                // 递归变量
                traversalChessBoard(chessBoard, p.y, p.x, step + 1);
            }
        }
        // 退出while循环，看遍历是否成功,未成功，就重置，让后回溯
        if (step < X * Y && !finished) {
            // 重置
            chessBoard[row][col] = 0;
            visited[row * X + col] = false;
        } else {
            finished = true;
        }
    }

    public static void sort(ArrayList<Point> points){
        points.sort((Point o1,Point o2)->{
             return nextStep(o1).size() - nextStep(o2).size();
        });
    }

    // 下一步可走位置
    public static ArrayList<Point> nextStep(Point currentPoint) {
        // 创建ArrayList
        ArrayList<Point> points = new ArrayList<>();
        // 准备放入的point
        Point point = new Point();
        // 判断该点是否可走
        // 判断位置1
        if ((point.x = currentPoint.x - 2) >= 0 && (point.y = currentPoint.y - 1) >= 0) {
            points.add(new Point(point)); // new 更改指向
        }
        // 判断位置2
        if ((point.x = currentPoint.x - 1) >= 0 && (point.y = currentPoint.y - 2) >= 0) {
            points.add(new Point(point)); // new 更改指向
        }
        // 判断位置3
        if ((point.x = currentPoint.x + 1) < X && (point.y = currentPoint.y - 2) >= 0) {
            points.add(new Point(point)); // new 更改指向
        }
        // 判断位置4
        if ((point.x = currentPoint.x + 2) < X && (point.y = currentPoint.y - 1) >= 0) {
            points.add(new Point(point)); // new 更改指向
        }
        // 判断位置5
        if ((point.x = currentPoint.x + 2) < X && (point.y = currentPoint.y + 1) < Y) {
            points.add(new Point(point)); // new 更改指向
        }
        // 判断位置6
        if ((point.x = currentPoint.x + 1) < X && (point.y = currentPoint.y + 2) < Y) {
            points.add(new Point(point)); // new 更改指向
        }
        // 判断位置7
        if ((point.x = currentPoint.x - 1) >= 0 && (point.y = currentPoint.y + 2) < Y) {
            points.add(new Point(point)); // new 更改指向
        }
        // 判断位置8
        if ((point.x = currentPoint.x - 2) >= 0 && (point.y = currentPoint.y + 1) < Y) {
            points.add(new Point(point)); // new 更改指向
        }

        return points;
    }

    public static void printBoard(int[][] arr) {
        for (int i = 0; i < Y; i++) {
            for (int j = 0; j < X; j++) {
                System.out.print(arr[i][j] + "\t");
            }
            System.out.println("");
        }
    }
}
```

### 12.🔴方法重载(Overload)

> Java中允许同一个类中，多个同名方法的存在，但要求形参列表不一致！

- **重载优点**

1) 减轻了起名的麻烦。
2) 减轻了记名的麻烦。

- **重载案例**

 ```java
 /**
  * @author zpc
  * @version 1.0
  * @description 
  *    重载入门案例
  * */
 public class Overload01 {
 	public static void main(String[] args) {
          Calculator calc = new Calculator();
          System.out.println(calc.calculate(10, 20));
          System.out.println(calc.calculate(10.0d, 20));
          System.out.println(calc.calculate(10.0d, 20.0d));
          System.out.println(calc.calculate(10, 20, 30));
 	}
 }
 
 
 // Caculator 计算器
 class Calculator {
 
 	// 计算 两个整数和
 	public int calculate(int a, int b) {
            return a+b;
 	}
     
     // 计算 两个Double的和
 	public double calculate(double a, double b) {
            return a+b;
 	}
 
     // 计算 一个double a 和一个int b的和
 	public double calculate(double a, int b) {
            return a+b;
 	}
  
     // 计算 三个整数的和
 	public int calculate(int a, int b, int c) {
            return a+b+c;
 	}
 
 }
 ```

- **重载细节**

![image-20240920151434457](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409201514664.png)

  ```java
  /**
   * @author zpc
   * @version 1.0
   * @description 
   *    重载入门案例
   * */
  public class Overload01 {
  	public static void main(String[] args) {
           Calculator calc = new Calculator();
           System.out.println(calc.calculate(10, 20));
           System.out.println(calc.calculate(10.0d, 20));
           System.out.println(calc.calculate(10.0d, 20.0d));
           System.out.println(calc.calculate(10, 20, 30));
  	}
  }
  
  
  // Caculator 计算器
  class Calculator {
  
  	// 计算 两个整数和
  	public int calculate(int a, int b) {
             return a+b;
  	}
      
      // 计算 两个Double的和
  	public double calculate(double a, double b) {
             return a+b;
  	}
  
      // 计算 一个double a 和一个int b的和
  	public double calculate(double a, int b) {
             return a+b;
  	}
   
      // 计算 三个整数的和
  	public int calculate(int a, int b, int c) {
             return a+b+c;
  	}
  
  }
  ```

### 13. 可变参数

![image-20240920195709231](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409201957424.png)

![image-20240920195719290](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409201957468.png)

```java
/**
 * @author zpc
 * @version 1.0
 * @description
 *     可变参数
 * 
 * */
public class VarParameter {
	public static void main(String[] args) {
           HspMethod hs = new HspMethod();
           System.out.println(hs.sum(1, 2, 3));
           System.out.println(hs.sum(1, 2, 3, 4));
           System.out.println(hs.sum(1, 2, 3, 4, 5));
	}
}


class HspMethod {

      // 可以计算2个数的和，3个数的和，4个数的和
	  // 方法名相同，功能相同，参数个数不同->使用可变参数优化
	  /*
          1. int... 表示可以接收的是可变参数， 类型是int 
          即可接收多个int值
          2. 使用可变参数时
	  */
	  public int sum(int... nums) {
	  	 int result = 0;
	  	 for(int i = 0; i < nums.length; i++) {
               result+=nums[i];
	  	 }
	  	 return result;
	  }
}
```

![image-20240920200942831](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409202009083.png)

### 14. 🔴Java作用域

![image-20240920201127440](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409202011712.png)

```java
/**
 * @author zpc
 * @version 1.0
 * @description
 *       作用域
 * */
public class VarScope {
	
	public static void main(String[] args) {
           
           Cat cat = new Cat();
           cat.cry();
           cat.eat();     

	}
}

class Cat {
	// 全局作用域： 也就是属性，作用域为整个类体 Cat类： 
	//       cry等方法使用属性
	// 属性定义时，可以直接赋值
	int age = 10; // 赋值为10
    
    public void cry() {
        // 1. 局部变量一般是指在成员方法中定义的变量
        // 2. n和 name就是局部变量
        // 3. n和name的作用域在cry方法中
    	int n = 10;
    	String name = "jack";

    	System.out.println(name+" age "+n);
    }

    public void eat() {

    	System.out.println("age= "+age);
    }
}
```



![image-20240920202430849](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409202024113.png)

![image-20240920202529251](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409202025551.png)

### 15.构造方法/构造器

![image-20240920202918745](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409202029943.png)

![image-20240920202928632](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409202029825.png)

![image-20240920203017799](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409202030029.png)

![image-20240920203108316](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409202031552.png)

![image-20240920203241680](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409202032935.png)

### 15. 对象创建流程02

![image-20240920203751845](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409202037281.png)

### 16. this关键字

#### 1. 引出

![image-20240920203923477](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409202039874.png)

#### 2.入门

![image-20240920204003862](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409202040056.png)

![image-20240920204010724](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409202040904.png)

#### 3.本质

> 简单的说： 哪个对象调用，this就代表哪个对象

### 17. 包

> **本质：**
>
> > 包的本质就是创建不同的文件夹来保存类文件，示意图:
> >
> > ![image-20240920234028083](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409202340345.png)
>
> **作用: **
>
> ![image-20240920233445492](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409202334705.png)

#### 1. 基础语法

![image-20240920233508025](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409202335219.png)

#### 2. 快速入门

![image-20240920234333094](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409202343307.png)

#### 3. 包的命名

![image-20240920234503004](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409202345344.png)

#### 4. 常用的包

![image-20240920234623497](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409202346706.png)

#### 5. 包使用细节

![image-20240920234852063](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409202348277.png)

![image-20240920235105800](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409202351019.png)

### 18. 访问修饰符

![image-20240920235208877](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409202352089.png)

![image-20240920235225353](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409202352643.png)

## 9. 面向对象三大特征

> - 封装
> - 继承
> - 多态

### 1.🚩 封装

> **封装(*encapsulation*)**

![image-20240920235608818](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409202356071.png)

#### 优点

![image-20240920235852993](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409202358225.png)

#### 实现

![image-20240920235921483](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409202359732.png)

![image-20240921000252560](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409210002790.png)

### 2. 🚩继承

> 继承作用:
>
> 1. 提高代码复用
>
> 2. 代码的扩展和可维护性
>
>    ![image-20240921000425865](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409210004072.png)
>
>    > 本质：
>    >
>    >  ![image-20240921002415637](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409210024911.png)
>
>    示意图
>
>    ![image-20240921000631032](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409210006237.png)

#### 1. 继承基本语法

![image-20240921000514210](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409210005421.png)

#### 2. 使用细节

![image-20240921001221409](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409210012595.png)

![image-20240921001321134](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409210013366.png)

![image-20240921001746994](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409210017258.png)

![image-20240921002029736](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409210020991.png)

![image-20240921002140568](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409210021795.png)

#### 3. super关键字

![image-20240921002641874](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409210026203.png)

**细节**

![image-20240921002710397](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409210027643.png)

![image-20240921002850148](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409210028332.png)

![image-20240921003042801](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409210030029.png)

![image-20240921003109601](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409210031851.png)

#### 4. 方法重写

![image-20240921003146180](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409210031386.png)

![image-20240921003321782](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409210033033.png)

### 3. 🚩多态

> ![image-20240921003955322](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409210039499.png)

#### 1.方法多态

![image-20240921004117081](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409210041226.png)

#### 2.对象多态

> **父类的引用指向子类对象**

![image-20240921004208945](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409210042186.png)

**向上转型**

![image-20240921004507090](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409210045300.png)

**向下转型**

![image-20240921005224850](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409210052032.png)

![image-20240921005455366](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409210054503.png)

> 属性没有重写之说
>
> ![image-20240921005739349](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409210057488.png)
>
> ![image-20240921005819045](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409210058187.png)

![image-20240921010338116](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409210103275.png)

![image-20240921012805239](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409210128384.png)

## 10. Object类中的方法

![image-20240921013129294](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409210131465.png)

![image-20240921013243387](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409210132540.png)

![image-20240921013800560](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409210138791.png)

![image-20240921013928132](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409210139402.png)

![image-20240921014040451](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409210140700.png)

## 11. 面向对象高级

### 1. 类变量和类方法

#### **类变量**

> JDK8以后static 存储在堆中:
>
>  java.lang.Class 对象和 [static](https://so.csdn.net/so/search?q=static&spm=1001.2101.3001.7020) 成员变量在运行时内存的位置。**JDK 1.8 中，两者都位于堆（Heap），且static 成员变量位于 Class对象内。**

![image-20240922104407014](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221044191.png)

> 不管static变量，即类变量在哪里:
>
> 1. static变量是同一个类所有对象共享
> 2. static类变量，在类加载的时候生成

![image-20240922104928996](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221049222.png)

![image-20240922105139177](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221051379.png)

![image-20240922105437488](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221054659.png)

#### **类方法**

![image-20240922105635965](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221056185.png)

![image-20240922110102868](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221101069.png)

![image-20240922110303452](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221103629.png)

![image-20240922110437898](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221104121.png)

### 2.理解main方法语法

![image-20240922110741393](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221107563.png)

![image-20240922111130211](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221111370.png)

### 3. 代码块

> 代码块调用的顺序优先于构造器

![image-20240922111155671](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221111875.png)

![image-20240922111210689](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221112840.png)

#### **细节**

![image-20240922111619202](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221116403.png)

![image-20240922112024165](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221120347.png)

![image-20240922112247570](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221122755.png)

![image-20240922112445903](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221124050.png)

![image-20240922112543424](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221125657.png)

### 4. 单例设计模式

> 设计模式:
>
> ![image-20240922113240055](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221132228.png)

![image-20240922113259812](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221132954.png)

#### 饿汉式

![image-20240922113417639](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221134842.png)

#### 懒汉式

> 使用时再创建

![image-20240922113829183](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221138404.png)

![image-20240922113805945](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221138085.png)

### 5. final关键字

![image-20240922114012343](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221140560.png)

![image-20240922114110435](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221141643.png)

![image-20240922114128406](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221141626.png)

### 6. 抽象类

![image-20240922114808393](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221148546.png)

![image-20240922114834035](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221148269.png)

![image-20240922114915599](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221149770.png)

![image-20240922114933112](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221149318.png)

![image-20240922115037196](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221150413.png)

#### **模版设计模式**

![image-20240922115143345](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221151467.png)

```java
package com.zpc;

/**
 * @ClassName : TmplateClass  //类名
 * @Description : 模版类设计模式  //描述
 * @Author : zpc20 //作者
 * @Date: 2024-09-22  上午 11:54
 */
public class TmplateClass {
    public static void main(String[] args) {
        AA aa = new AA();
        aa.calculateTime();
        BB bb = new BB();
        bb.calculateTime();
        CC cc = new CC();
        cc.calculateTime();
    }
}

abstract class Template {

    public abstract void job();

    public void calculateTime() {
        // 开始时间
        long start = System.currentTimeMillis();
        // 执行方法
        job();
        // 结束时间
        long end = System.currentTimeMillis();
        System.out.println("AA 执行时间 " + (end - start));
    }
}


class AA extends Template {
    // public void calculateTime() {
    //     // 开始时间
    //     long start = System.currentTimeMillis();
    //     // 执行方法
    //     job();
    //     // 结束时间
    //     long end = System.currentTimeMillis();
    //     System.out.println("AA 执行时间 " + (end - start));
    // }

    // 计算任务
    public void job() {

        long num = 1;

        for (int i = 0; i < 800000; i++) {
            num += i;
        }
        System.out.println(num);
    }
}

class BB extends Template {
    // public void calculateTime() {
    //     // 开始时间
    //     long start = System.currentTimeMillis();
    //     // 执行方法
    //     job();
    //     // 结束时间
    //     long end = System.currentTimeMillis();
    //     System.out.println("BB 执行时间 " + (end - start));
    // }

    // 计算任务
    public void job() {

        long num = 0;

        for (int i = 0; i < 700000; i++) {
            num += i;
        }

        System.out.println(num);
    }
}

class CC extends Template {
    // public void calculateTime() {
    //     // 开始时间
    //     long start = System.currentTimeMillis();
    //     // 执行方法
    //     job();
    //     // 结束时间
    //     long end = System.currentTimeMillis();
    //     System.out.println("CC 执行时间 " + (end - start));
    // }

    // 计算任务
    public void job() {

        long num = 0;

        for (int i = 0; i < 600000; i++) {
            num += i;
        }

        System.out.println(num);
    }
}

```



### 7.接口

![image-20240922120806807](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221208020.png)

![image-20240922120926721](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221209854.png)

![image-20240922120940605](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221209728.png)

![image-20240922121147835](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221211032.png)

![image-20240922121450365](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221214552.png)

![image-20240922121817067](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221218283.png)

![image-20240922121834238](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221218431.png)

![image-20240922122304051](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221223215.png)

### 8.内部类

![image-20240922122709539](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221227764.png)

![image-20240922122728602](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221227762.png)

![image-20240922122735871](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221227014.png)

![image-20240922122904640](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221229813.png)

#### 1. 局部内部类

![image-20240922123012551](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221230750.png)

![image-20240922123519185](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221235382.png)

#### 2. 匿名内部类

![image-20240922123731508](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221237658.png)

![image-20240922123802246](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221238408.png)

![image-20240922124221585](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221242724.png)

![image-20240922124434710](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221244855.png)

![image-20240922124528657](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221245862.png)

#### 3.成员内部类

![image-20240922124824276](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221248472.png)

![image-20240922124933918](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221249086.png)

**其他外部类访问内部类**

![image-20240922125328370](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221253513.png)

![image-20240922125350309](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221253524.png)

#### 4.静态内部类

![image-20240922125513019](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221255182.png)

![image-20240922125659013](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221256167.png)

![image-20240922125740711](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221257907.png)

![image-20240922125930282](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221259424.png)

## 12. 枚举类

> ![image-20240922132548464](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221325620.png)

### 1.自定义枚举类

![image-20240922132605239](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221326403.png)

```java
public class Enumeration01 {
    public static void main(String[] args) {
        System.out.println(Season.SPRING);
        System.out.println(Season.SUMMEER);
        System.out.println(Season.AUTUMN);
        System.out.println(Season.WINTER);
    }
}



class Season{
    private String name;
    private String desc;

    public static final Season SPRING = new Season("春天", "温暖");
    public static final Season SUMMEER = new Season("夏天", "炎热");
    public static final Season AUTUMN = new Season("秋天", "凉爽");
    public static final Season WINTER = new Season("冬天", "寒冷");

    // 私有化构造器
    private Season(String name, String desc) {
        this.name = name;
        this.desc = desc;
    }

    public String getName() {
        return name;
    }

    public String getDesc() {
        return desc;
    }

    @Override
    public String toString() {
        return "Season{" +
                "name='" + name + '\'' +
                ", desc='" + desc + '\'' +
                '}';
    }
}
```

### 2.enum枚举类

![image-20240922134253294](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221342514.png)

![image-20240922133903169](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221339360.png)

```java
package com.zpc;

/**
 * @author : zpc20 //作者
 * @version : 1.0 // 版本
 * @ClassName : Enumeration02  //类名
 * @Description : 枚举类02  //描述
 * @Date: 2024-09-22  下午 01:33
 */
public class Enumeration02 {
    public static void main(String[] args) {
        System.out.println(Season1.SPRING);
        System.out.println(Season1.SUMMER);
        System.out.println(Season1.AUTUMN);
        System.out.println(Season1.WINTER);
    }
}

enum Season1{


    // public static final Season SPRING = new Season("春天", "温暖");
    // 代替 SPRING("春天", "温暖");
    // public static final Season SUMMEER = new Season("夏天", "炎热");
    // public static final Season AUTUMN = new Season("秋天", "凉爽");
    // public static final Season WINTER = new Season("冬天", "寒冷");
    SPRING("春天", "温暖"),
    SUMMER("夏天", "炎热"),
    AUTUMN("秋天", "凉爽"),
    WINTER("冬天", "寒冷");

    private String name;
    private String desc;
    // 私有化构造器
    private Season1(String name, String desc) {
        this.name = name;
        this.desc = desc;
    }

    public String getName() {
        return name;
    }

    public String getDesc() {
        return desc;
    }

    @Override
    public String toString() {
        return "Season{" +
                "name='" + name + '\'' +
                ", desc='" + desc + '\'' +
                '}';
    }
}
```

### 3. 常用方法

![image-20240922134901854](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221349000.png)

![image-20240922134912360](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221349534.png)

**valueOf未匹配错误**

![image-20240922140047479](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221400622.png)

```java
package com.zpc;

/**
 * @author : zpc20 //作者
 * @version : 1.0 // 版本
 * @ClassName : Enumeration02  //类名
 * @Description : 枚举类02  //描述
 * @Date: 2024-09-22  下午 01:33
 */
public class Enumeration03 {
    public static void main(String[] args) {
        Season2 autumn = Season2.AUTUMN;
        // 获取名称
        System.out.println(autumn.name());
        // 枚举的编号 从0开始编号
        System.out.println(autumn.ordinal());
        // 含有所有定义的枚举对象的数组
        // System.out.println(Arrays.toString(Season2.values()));
        Season2[] values = Season2.values();
        System.out.println("====增强for循环====");
        for (Season2 value : values) {
            System.out.println(value);
        }
        // valueOf 字符串转换为枚举对象
        // 找到则返回未找到则报错
        Season2 autumn1 = Season2.valueOf("AUTUMN");
        System.out.println("autumn1 = " + autumn1);
        System.out.println(autumn == autumn1);

        // compareTo: 比较两个枚举常量， 比较的就是编号
        /*
        * public final int compareTo(E o) {
        *       // .....
        *       return self.ordinal - other.ordinal;
        *   }
        * 本质是： 两个枚举次序值之间的差值
        * */
        System.out.println(Season2.AUTUMN.compareTo(Season2.SUMMER));
    }
}

enum Season2 {


    // public static final Season SPRING = new Season("春天", "温暖");
    // 代替 SPRING("春天", "温暖");
    // public static final Season SUMMEER = new Season("夏天", "炎热");
    // public static final Season AUTUMN = new Season("秋天", "凉爽");
    // public static final Season WINTER = new Season("冬天", "寒冷");
    SPRING("春天", "温暖"),
    SUMMER("夏天", "炎热"),
    AUTUMN("秋天", "凉爽"),
    WINTER("冬天", "寒冷");

    private String name;
    private String desc;

    // 私有化构造器
    private Season2(String name, String desc) {
        this.name = name;
        this.desc = desc;
    }

    public String getName() {
        return name;
    }

    public String getDesc() {
        return desc;
    }

    @Override
    public String toString() {
        return "Season{" +
                "name='" + name + '\'' +
                ", desc='" + desc + '\'' +
                '}';
    }
}

```

![image-20240922140636841](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221406046.png)

## 13. 注解

![image-20240922140800939](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221408168.png)

![image-20240922140936365](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221409566.png)

![image-20240922141209880](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221412105.png)

![image-20240922141509815](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221415030.png)

#### 1. 元注解

![image-20240922141544755](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221415004.png)

**1. Retention**

![image-20240922141635414](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221416641.png)

![image-20240922141750688](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221417008.png)

**2.  Target**

![image-20240922141823929](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221418164.png)

**3. Documented**

![image-20240922141903930](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221419189.png)

**4. Inherited**

![image-20240922141956478](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221419688.png)

## 14. 🚩异常🚨处理(Exception)

### 1. 概念

 ![image-20240922144042223](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221440497.png)

### 2. 🚩体系图

![image-20240922144221502](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221442738.png)

![image-20240922144424929](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221444114.png)

> ![image-20240922144459532](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221444807.png)

### 3. 常见异常

![image-20240922144526596](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221445803.png)

#### 1. 空指针异常

![image-20240922144557607](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221445822.png)

#### 2. 数学运算异常

![image-20240922144738052](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221447270.png)

#### 3. 数组越界异常

![image-20240922144754293](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221447501.png)

#### 4. 类型转换异常 ![image-20240922144814368](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221448608.png)

#### 5. 数字格式不正确异常

![image-20240922144919136](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221449281.png)

### 4. 异常处理

> IDEA 快捷键`ctrl+alt+t`

![image-20240922144946971](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221449151.png)

![image-20240922145100564](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221451682.png)

![image-20240922145152573](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221451720.png)

![image-20240922145337171](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221453361.png)

![image-20240922145758199](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221457301.png)

![image-20240922145728395](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221457514.png)

![image-20240922145844392](C:/Users/zpc20/AppData/Roaming/Typora/typora-user-images/image-20240922145844392.png)

![image-20240922150228613](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221502759.png)

![image-20240922150314258](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221503456.png)

### 5. 自定义异常

![image-20240922150629617](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221506731.png)

#### **步骤**

![image-20240922150658715](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221506832.png)

![image-20240922150741618](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221507748.png)

### 6. throw 和thows对比

![image-20240922150812971](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221508077.png)

![image-20240922151135515](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221511681.png)

## 15. 常用类

### 1. 包装类

> ![image-20240922151715204](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221517314.png)

| 基本数据类型 |  包装类   |  父类  |
| :----------: | :-------: | :----: |
|   boolean    |  Boolean  |        |
|     char     | Character |        |
|     byte     |   Byte    | Number |
|    short     |   Short   | Number |
|     int      |  Integer  | Number |
|     long     |   Long    | Number |
|    float     |   Float   | Number |
|    double    |  Double   | Number |

![image-20240922151842627](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221518748.png)

![image-20240922151851893](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221518988.png)

#### 1. 装箱和拆箱

![image-20240922152013732](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221520918.png)

![image-20240922152710120](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221527269.png)

![image-20240922153044707](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221530882.png)

### 2. String 类

![image-20240922153124434](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409221531720.png)

> 继承关系图: 
>
> ​     ![202409222158122](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222158122.png)
>
> ![image-20240922220953856](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222209090.png)

![image-20240922221043349](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222210608.png)

![image-20240922221110426](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222211639.png)

#### 1. 创建String对象的两种方式

![image-20240922221252553](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222212786.png)

![image-20240922221327211](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222213481.png)

![image-20240922221622621](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222216887.png)

**练习**

![image-20240922222255331](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222222604.png)

![image-20240922222200357](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222222599.png)

 #### 2.特性

![image-20240922222656718](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222226003.png)

![image-20240922222742344](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222227610.png)

![image-20240922223605342](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222236658.png)

![image-20240922224047486](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222240733.png)

![image-20240922224150775](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222241062.png)

![image-20240922224245594](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222242855.png)

![image-20240922224908196](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222249825.png)

#### 3.常用方法

![image-20240922225332772](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222253091.png)

![image-20240922225222184](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222252551.png)

![image-20240922225110719](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222251002.png)

![image-20240922230257719](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222302960.png)

![image-20240922230536937](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222305178.png)

%.2f[^1]

![image-20240922230810330](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222308551.png)

[^1]: 进行四舍五入

### 3. StringBuffer类

> **线程安全**

> ![image-20240922231550709](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222315890.png)
>
> ![image-20240922231650242](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222316460.png)



![image-20240922231832883](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222318064.png)

> StringBuffer是一个final类，不能被继承

![image-20240922231928940](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222319183.png)

![image-20240922232131616](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222321796.png)

#### 1. 构造器

![image-20240922232201578](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222322764.png)

![image-20240922232448388](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222324582.png)

![image-20240922232603944](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222326139.png)

![image-20240922232706395](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222327565.png)

#### 2.常见方法

![image-20240922232811230](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222328438.png)

![image-20240922233539201](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222335483.png)

### 4.StringBuilder类

> **线程不安全**
>
> **适合单线程**

![image-20240922234138987](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222341205.png)

![image-20240922234256290](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222342471.png)

### 5. String、StringBuffer和StringBuilder总结

![image-20240922234442591](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222344891.png)

![image-20240922234602222](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222346491.png)

### 6. Math类

![2](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222346195.png)

![image-20240922234707660](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222347832.png)

![image-20240922234731743](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222347971.png)

### 7.Arrays类

![image-20240922234833454](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222348696.png)

#### 1. Sort

![image-20240922235101792](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222351969.png)

![image-20240922235244614](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409222352808.png)

### 8. System类

![image-20240923003237434](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409230032689.png)

### 9.大数处理类(BigInteger和BigDecimal)

![image-20240923003435245](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409230034418.png)

![image-20240923003456197](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409230034373.png)

### 10. Date类

![image-20240923003745928](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409230037106.png)

![image-20240923003723009](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409230037256.png)



### 11.Calender类

> 单例模式
>
> 🚨**线程不安全**

![image-20240923004108020](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409230041201.png)

![image-20240923004207769](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409230042064.png)

![image-20240923004220693](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409230042863.png)

### 12.JDK8 LocalDate、LocalTime、LocalDateTime

![image-20240923004501759](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409230045964.png)

![image-20240923004443780](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409230044014.png)

![image-20240923004625362](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409230046654.png)

![image-20240923004659367](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409230046571.png)

## 16. 🚩集合

> **数组缺点：**
>
> ![image-20240923123411570](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409231234756.png)
>
> ![image-20240923130407513](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409231304651.png)
>
> **🟊🟊🟊🟊🟊框架体系图🟊🟊🟊🟊🟊**:
>
> ![image-20240923131057566](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409231310709.png)
>
> ![image-20240923131214585](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409231312683.png)
>
> ![image-20240923130452288](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409231304415.png)

### 1. Collection

> ![image-20240923131658478](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409231316656.png)

**常用方法**

![image-20240923131736144](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409231317288.png)

**迭代器遍历【Iterator】**

![image-20240923132015430](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409231320622.png)

![image-20240923132243370](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409231322527.png)

**增强For循环**

![image-20240923132342625](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409231323857.png)

#### 1. List

> ![image-20240923142629266](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409231426485.png)
>
> **遍历**
>
> ![image-20240923143602975](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409231436141.png)

##### **ArrayList**

> **线程不安全**

**注意**

![image-20240923191212178](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409231912333.png)

**源码**

> **transient标识不会被序列化**

![image-20240923191347052](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409231913271.png)

###### **源码解析**

![image-20240924095028979](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409240950135.png)

![image-20240923204448636](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409232044796.png)

![image-20240924093922179](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409240939360.png)

![image-20240924094242010](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409240942154.png)

##### **LinkedList**

> **线程不安全**

![image-20240924100514169](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241005295.png)

![image-20240924100559691](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241005893.png)

![image-20240924103359521](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241033675.png)

###### **源码解析**

![image-20240924101821496](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241018619.png)

![image-20240924101903401](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241019521.png)

![image-20240924102353491](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241023623.png)

![image-20240924103232170](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241032307.png)

![image-20240924103253246](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241032387.png)

###### **ArrayList和Linked的比较**

![image-20240924103518407](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241035549.png)

![image-20240924103637338](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241036537.png)

##### **Vector**

> **线程安全**

![image-20240924095641460](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409240956684.png)

![image-20240924095743274](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409240957424.png)

###### **源码解析**

![image-20240924100041017](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241000145.png)

![image-20240924100102717](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241001844.png)

![image-20240924100114590](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241001713.png)

![image-20240924100246492](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241002652.png)

#### 2.Set

> ![image-20240924103826772](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241038998.png)
>
> ![image-20240924103904698](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241039922.png)

##### **HashSet**

![image-20240924104000326](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241040529.png)

![image-20240924104252215](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241042346.png)

![image-20240924105246267](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241052416.png)

![image-20240924104612170](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241046315.png)

###### **源码解析**

![image-20240924105639912](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241056061.png)

![image-20240924110210662](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241102837.png)

![image-20240924110234483](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241102611.png)

![image-20240924110314149](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241103269.png)

![image-20240924110323327](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241103452.png)

![image-20240924110401282](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241104420.png)

![image-20240924110532821](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241105969.png)

![image-20240924111036812](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241110955.png)

![image-20240924111341316](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241113462.png)

![image-20240924111426176](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241114311.png)

![image-20240924113323483](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241133672.png)

![image-20240924113559523](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241135651.png)

![image-20240924114230834](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241142992.png)

![image-20240924114644132](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241146282.png)

> **表的长度扩容到64且当个链表达到8才树化链表**

![image-20240924115026034](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241150179.png)

**扩容机制**

![image-20240924115101481](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241151648.png)

![image-20240924120031949](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241200096.png)



##### **LinkedHashSet**

![image-20240924122145425](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241221654.png)

![image-20240924122545436](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241225730.png)

![image-20240924123450072](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241234215.png)

![image-20240924123520179](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241235318.png)

##### **TreeSet**

![image-20240924172603311](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241726437.png)

![image-20240924172626641](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241726763.png)

![image-20240924172721461](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241727612.png)

![image-20240924173046600](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241730733.png)

![image-20240924173025416](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241730575.png)

![image-20240924173156230](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241731405.png)

### 2.Map

> ![image-20240924125549708](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241255938.png)
>
> ![image-20240924161533473](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241615694.png)
>
> ![image-20240924162223071](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241622262.png)
>
> ![image-20240924162612031](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241626158.png)
>
> ![image-20240924162641458](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241626712.png)
>
> ![image-20240924162727852](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241627023.png)
>
> ![image-20240924163050153](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241630283.png)
>
> ![image-20240924163549200](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241635368.png)

#### 1. HashMap

> **线程不安全**

![image-20240924163707122](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241637329.png)

![image-20240924164231511](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241642785.png)

![image-20240924164410186](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241644447.png)

##### **源码解析**

![image-20240924165613490](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241656650.png)

![image-20240924165432133](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241654296.png)

![image-20240924165709811](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241657975.png)

![image-20240924165729114](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241657272.png)

![image-20240924165809078](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241658216.png)

![image-20240924165855990](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241658136.png)

#### 2. HashTable

> **线程安全**

![image-20240924170046038](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241700190.png)

![image-20240924170924779](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241709911.png)

![image-20240924171145346](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241711473.png)

![image-20240924171419458](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241714603.png)

##### **扩容**

![image-20240924171439552](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241714671.png)

#### 3. LinkedHashMap



#### 4. TreeMap

![image-20240924173559643](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241735792.png)

##### **源码解析**

![image-20240924173653869](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241736027.png)

![image-20240924173746252](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241737422.png)

![image-20240924173816740](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241738903.png)

#### 5.Properties

![image-20240924171645518](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241716727.png)

### 3.Collections

> **工具类**

![image-20240924174019110](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241740432.png)

![image-20240924174209887](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241742140.png)

### 4.选型规则

![image-20240924172146137](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241721388.png)

## 17.泛型

> ![image-20240924183705290](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241837442.png)
>
> ![image-20240924183924095](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241839297.png)

![image-20240924184035279](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241840492.png)

![image-20240924184539878](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241845050.png)

![image-20240924184606715](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241846000.png)

![image-20240924184846550](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241848846.png)

#### 1.自定义泛型

##### **泛型类**

![image-20240924185339497](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241853790.png)

##### **泛型接口**

![image-20240924185951142](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241859338.png)

##### **泛型方法**

> 既可以使用类声明的泛型又可以使用自己声明的方法

![image-20240924190438921](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241904183.png)

![image-20240924190748806](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241907939.png)



### 2. 泛型的继承和通配符

![image-20240924191017563](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241910746.png)

## 18.Junit

![image-20240924191607514](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409241916676.png)

# 二、线程（基础）

## 1. 线程介绍

> ![image-20240924231837698](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409242318852.png)
>
> ![image-20240924231853182](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409242318380.png)
>
> ![image-20240924232120564](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409242321734.png)
>
> ![image-20240924232231996](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409242322174.png)
>
> ![image-20240924232315358](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409242323625.png)

## 2. Thread类图

![image-20240924234730011](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409242347136.png)

![image-20240924233206575](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409242332756.png)

## 3. 线程基本使用

![image-20240924234811175](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409242348332.png)

**jconsole**

![image-20240924235419166](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409242354334.png)

### 1. 继承Thread

![image-20240924233251547](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409242332800.png)

```java
package com.zpc.threaduse;

/**
 * @author : zpc20 //作者
 * @version : 1.0 // 版本
 * @ClassName : Thread01  //类名
 * @Description : 线程使用案列01  //描述
 * @Date: 2024-09-24  下午 11:33
 */
public class Thread01 {
    public static void main(String[] args) throws InterruptedException {
        MyThread myThread = new MyThread();
        myThread.start(); // 启动线程
        System.out.println("主线程继续执行: " + Thread.currentThread().getName());
        for (int i = 0; i < 10; i++) {
            System.out.println("主线程 i= " + i);
            // 主线程休眠
            Thread.sleep(1000);
        }
    }
}


class MyThread extends Thread {
    int times = 0;

    @Override
    public void run() {
        // 重写run方法写上自己的业务逻辑
        // 每隔1s在控制台输出 你好！
        while (true) {
            System.out.println("你好！" + (++times) + "Thread名字: " + Thread.currentThread().getName());
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                throw new RuntimeException(e);
            }
            if (times == 80) {
                break; // 80次后退出循环
            }
        }


    }
}
```

#### 为什么是start方法

> 如果直接使用run方法是串行执行（即在同一个线程中执行）

![image-20240924235655483](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409242356624.png)

![image-20240924235850590](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409242358769.png)

![image-20240924235917799](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409242359954.png)

### 2.实现Runnable接口

 ![image-20240925000032761](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409250000927.png)

![image-20240925000509905](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409250005168.png)

![image-20240925001305134](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409250013317.png)

```java
package com.zpc.threaduse;

/**
 * @author : zpc20 //作者
 * @version : 1.0 // 版本
 * @ClassName : Thread01  //类名
 * @Description : 线程使用案列01  //描述
 * @Date: 2024-09-24  下午 11:33
 */
public class Thread02 {
    public static void main(String[] args) throws InterruptedException {
        Thread myThread1 = new Thread(new MyThread1());
        myThread1.start(); // 启动线程
        System.out.println("主线程继续执行: " + Thread.currentThread().getName());
        for (int i = 0; i < 10; i++) {
            System.out.println("主线程 i= " + i);
            // 主线程休眠
            Thread.sleep(1000);
        }
    }
}


class MyThread1 implements Runnable {
    int times = 0;

    @Override
    public void run() {
        // 重写run方法写上自己的业务逻辑
        // 每隔1s在控制台输出 你好！
        while (true) {
            System.out.println("你好！" + (++times) + "Thread名字: " + Thread.currentThread().getName());
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                throw new RuntimeException(e);
            }
            if (times == 80) {
                break; // 80次后退出循环
            }
        }


    }
}
```

![image-20240925002832980](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409250028127.png)

## 4.线程常用方法

![image-20240925003256666](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409250032881.png)

![image-20240925003735737](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409250037000.png)

![image-20240925004235864](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409250042067.png)

## 5. 守护线程

> ![image-20240925134019160](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409251340335.png)
>
> **Daemon【守护线程】**

![image-20240925134458271](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409251344431.png)

## 6.线程生命周期

![image-20240925134537153](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409251345295.png)

![image-20240925134853267](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409251348434.png)

## 7.线程同步机制

![image-20240925135234686](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409251352907.png)

### 实现

![image-20240925135401785](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409251354950.png)

### 原理

![image-20240925140601429](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409251406692.png)

![image-20240925140623137](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409251406353.png)

![image-20240925141248463](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409251412901.png)

## 8. 线程死锁

![image-20240925141617507](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409251416661.png)

## 9.释放锁

![image-20240925142046160](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409251420405.png)

![image-20240925142157325](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409251421513.png)

# 三、文件操作

## 1.文件

![image-20240925154904643](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409251549795.png)

![image-20240925154939542](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409251549723.png)

## 2.常用文件操作

### 1.创建文件

![image-20240925213229713](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409252132939.png)

### 2. 获取文件信息

![image-20240925223432932](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409252234152.png)

![image-20240925223445125](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409252234350.png)

### 3. 目录操作

![image-20240925223604575](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409252236750.png)

### 4.IO流原理以及流的分类

![image-20240925223852315](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409252238536.png)

![image-20240925224013183](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409252240460.png)

![image-20240925224056780](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409252240986.png)

![image-20240925224345713](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409252243895.png)

![image-20240925224644255](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409252246423.png)

![image-20240925230017436](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409252300565.png)

![image-20240925230600497](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409252306813.png)

![image-20240925230656591](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409252306904.png)

![image-20240925230726153](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409252307295.png)

![image-20240925232032793](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409252320092.png)

### 5.节点流和处理流

![image-20240925232512148](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409252325298.png)

![image-20240925232210817](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409252322108.png)

![image-20240925232230199](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409252322380.png)

![image-20240925232950133](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409252329479.png)

![image-20240926103001095](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261030421.png)

![image-20240926103205661](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261032908.png)

![image-20240926103355070](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261033276.png)

![image-20240926103412318](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261034471.png)

![image-20240926104025548](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261040685.png)

![image-20240926104551247](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261045467.png)

![image-20240926104631384](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261046536.png)

#### 标准输入

![image-20240926105049091](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261050293.png)

#### 转换流

![image-20240926105345159](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261053342.png)

![image-20240926105647814](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261056037.png)

![image-20240926105936979](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261059234.png)

#### 打印流

![image-20240926110531466](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261105617.png)

![image-20240926110911883](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261109043.png)

![image-20240926111006756](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261110906.png)

#### Properties配置文件读取

![image-20240926111631950](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261116218.png)

![image-20240926111615912](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261116191.png)

# 四、网络编程

![image-20240926112744714](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261127971.png)

![image-20240926112857553](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261128809.png)

## 1. IP地址

![image-20240926114330852](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261143111.png)

![image-20240926115345708](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261153886.png)

![image-20240926115354962](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261153106.png)

![image-20240926115900980](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261159324.png)

## 2. 域名和端口号

> **💡IP+端口访问服务**

![image-20240926120044069](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261200343.png)

![image-20240926120323717](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261203889.png)

## 3. 网络协议

![image-20240926120723122](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261207320.png)

![image-20240926120910793](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261209958.png)

![image-20240926120931804](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261209082.png)

![image-20240926124444112](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261244293.png)

##### TCP和UDP

![image-20240926124633696](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261246970.png)

###### **TCP协议三次握手**

![image-20240926124654937](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261246076.png)![image-20240926124717493](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261247659.png)

![image-20240926124726110](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261247247.png)

## 4. InetAddress类

![image-20240926125207149](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261252339.png)

![image-20240926125453279](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261254430.png)

```java
package com.zpc.simple;

import java.net.InetAddress;
import java.net.UnknownHostException;

/**
 * @author : zpc20 //作者
 * @version : 1.0 // 版本
 * @ClassName : API  //类名
 * @Description : 网络API  //描述
 * @Date: 2024-09-26  下午 12:53
 */
public class API {
    public static void main(String[] args) throws UnknownHostException {
        // 1. 获取本机地址
        InetAddress inetAddress = InetAddress.getLocalHost();
        System.out.println(inetAddress);
        System.out.println("=========================");
        // 2. 根据主机名 获取 InetAddress对象
        InetAddress host1 = InetAddress.getByName("zpc");
        System.out.println(host1);
        System.out.println("=========================");
        // 3. 根据域名返回InetAddress对象 eg: www.baidu.com
        InetAddress host2 = InetAddress.getByName("www.baidu.com");
        System.out.println(host2);
        System.out.println("=========================");
        // 4. 根据InetAddress对象 获取对应的地址
        String address = host2.getHostAddress();
        System.out.println(address);
    }
}
```

## 5. Socket

> 1. **TCP 💡可靠**
> 2. **UDP 💡不可靠**

![image-20240926130304173](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261303443.png)

![image-20240926130546586](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261305842.png)

![image-20240926130601298](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261306532.png)

## 【TCP】 案例1【使用字节流】

![image-20240926130839170](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261308373.png)

![image-20240926131050442](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261310768.png)

### 1. Client代码

```java
package com.zpc.socket;

import java.io.BufferedOutputStream;
import java.io.IOException;
import java.net.InetAddress;
import java.net.Socket;

/**
 * @author : zpc20 //作者
 * @version : 1.0 // 版本
 * @ClassName : Client  //类名
 * @Description : 客户端 发送消息"hello,server" ==> 服务端 //描述
 * @Date: 2024-09-26  下午 01:13
 */
public class Client {
    public static void main(String[] args) throws IOException {
        // 1. 连接服务端【IP+端口】
        //    连接成功返回Socket对象
        Socket socket = new Socket(InetAddress.getLocalHost(),9999);
        System.out.println("客户端 socket返回 = "+socket.getClass());
        // 2. 连接上后，生成Socket，通过
        //    socket.getOutputStream() // 输出流
        // 3. 通过输出流，写入数据到 数据通道
        // 3.1 获取输出流
        BufferedOutputStream outputStream = new BufferedOutputStream(socket.getOutputStream());
        // 3.2 通过输出流写入数据到数据通道
        outputStream.write("hello,Server".getBytes());
        // 3.3 关闭流对象和socket,必须关闭
        outputStream.close();
        socket.close();
        System.out.println("客户端传输数据 = " + "hello,Server");
    }
}

```

### 2.Server服务端代码

```java
package com.zpc.socket;

import java.io.IOException;
import java.io.InputStream;
import java.net.ServerSocket;
import java.net.Socket;

/**
 * @author : zpc20 //作者
 * @version : 1.0 // 版本
 * @ClassName : Server  //类名
 * @Description : 服务端  //描述
 * @Date: 2024-09-26  下午 01:13
 */
public class Server {
    public static void main(String[] args) throws IOException {
        // 1. 本机9999端口监听
        //    注意: 💡1.要求没有服务占用9999端口
        //         💡2.这个ServerSocket 可以通过 accept() 返回多个Socket【多并发】
        ServerSocket serverSocket = new ServerSocket(9999);
        System.out.println("监听9999端口，等待连接。。。");
        // 2. 当没有客户端连接时，程序阻塞
        //    如果有客户端连接，则会返回Socket对象，程序继续。。。
        Socket socket = serverSocket.accept();
        System.out.println("服务端 scoket = " + socket.getClass());
        // 3. 通过socket.getInputStream()读取客户端
        //     写入的数据，并显示
        int read = 0;
        byte[] buf = new byte[1024];
        InputStream inputStream = socket.getInputStream();
        while(!((read = inputStream.read(buf)) == -1)){
            // System.out.println((char)read);
            System.out.println(new String(buf,0,read));
        }

        // 4. 关闭流和socket severSocket
        inputStream.close();
        socket.close();
        serverSocket.close();
    }
}
```

![image-20240926135449928](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261354184.png)

![image-20240926135523365](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261355546.png)

![image-20240926135849501](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261358109.png)

## 【TCP】案例2 【上传文件】

![image-20240926140111554](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261401826.png)

![image-20240926140528256](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261405548.png)

### 1. Client客户端

```java
package com.zpc.socket.upload;

import java.io.*;
import java.net.InetAddress;
import java.net.Socket;

/**
 * @author : zpc20 //作者
 * @version : 1.0 // 版本
 * @ClassName : Client  //类名
 * @Description : 客户端 发送消息"hello,server" ==> 服务端 //描述
 * @Date: 2024-09-26  下午 01:13
 */
public class Client {
    public static void main(String[] args) throws IOException {
        // 1. 连接服务端【IP+端口】
        //    连接成功返回Socket对象
        Socket socket = new Socket(InetAddress.getLocalHost(),9998);
        // 2. 读取磁盘文件
        String filePath = "C:\\Users\\zpc20\\OneDrive\\图片\\屏幕快照\\bg.png";
        BufferedInputStream bis = new BufferedInputStream(new FileInputStream(filePath));
        byte[] fileByte = StreamUtil.streamToByteArray(bis);
        // 3. 通过socket 输出流发送到服务端
        BufferedOutputStream bos = new BufferedOutputStream(socket.getOutputStream());
        bos.write(fileByte); // 写入数据到数据通道
        bis.close(); // 关闭输入流
        socket.shutdownOutput(); //写入结束标记
        // 4. 接收回复消息
        InputStream inputStream = socket.getInputStream();
        String s = StreamUtil.streamToStringStream(inputStream);
        System.out.println(s);

        // 关闭相关流
        inputStream.close();
        bos.close();
        socket.close();
    }
}
```

### 2. Server服务端

```java
package com.zpc.socket.upload;

import java.io.*;
import java.net.ServerSocket;
import java.net.Socket;

/**
 * @author : zpc20 //作者
 * @version : 1.0 // 版本
 * @ClassName : Server  //类名
 * @Description : 服务端  //描述
 * @Date: 2024-09-26  下午 01:13
 */
public class Server {
    public static void main(String[] args) throws IOException {
        // 1. 本机9999端口监听
        //    注意: 💡1.要求没有服务占用9999端口
        //         💡2.这个ServerSocket 可以通过 accept() 返回多个Socket【多并发】
        ServerSocket serverSocket = new ServerSocket(9998);
        System.out.println("监听9998端口，等待连接。。。");
        // 2. 获取socket连接
        Socket socket = serverSocket.accept();

        // 3. 读取客户端数据
        BufferedInputStream bis = new BufferedInputStream(socket.getInputStream());
        byte[] fileBytes = StreamUtil.streamToByteArray(bis);
        // 4. 保存数据【磁盘】
        String filePath = "C:\\Users\\zpc20\\Desktop\\截图\\bg.png";
        BufferedOutputStream bos = new BufferedOutputStream(new FileOutputStream(filePath));
        bos.write(fileBytes);
        bos.close();

        // 5. 回复客户端 接收成功
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(socket.getOutputStream()));
        bw.write("接收到图片");
        bw.flush(); // 刷新数据
        socket.shutdownOutput(); // 写入结束标记



        // 关闭流
        bw.close();
        bis.close();
        socket.close();
        serverSocket.close();

    }
}

```

### 3. StreamUtil工具类

```java
package com.zpc.socket.upload;

import java.io.*;

/**
 * @author : zpc20 //作者
 * @version : 1.0 // 版本
 * @ClassName : StreamUtil  //类名
 * @Description : 工具类  //描述
 * @Date: 2024-09-26  下午 02:10
 */
public class StreamUtil {

    /**
     * 功能： 把一个输入流转换为字节数组
     *
     * @param is 输入流
     * @return byte[]
     */
    public static byte[] streamToByteArray(InputStream is) throws IOException {
        // 创建字节数组输出流
        ByteArrayOutputStream bos = new ByteArrayOutputStream();
        byte[] b = new byte[1024]; // buffer
        int len;
        while ((len = is.read(b)) != -1) {
            bos.write(b, 0, len);
        }
        byte[] array = bos.toByteArray();
        bos.close();
        return array;
    }

    /**
     * InputStream 转换为String
     *
     * @param is 输入流
     * @return String
     */
    public static String streamToStringStream(InputStream is) throws IOException {
        byte[] b = new byte[1024]; // buffer
        int len;
        StringBuilder s = new StringBuilder(); // 返回
        while ((len = is.read(b)) != -1) {
            s.append(new String(b, 0, len));
        }
        return s.toString();
    }

    /**
     * InputStream 转换为 String
     *
     * @param is 输入流
     * @return String
     */
    public static String streamToStringReader(InputStream is) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(is));
        StringBuilder stringBuffer = new StringBuilder();
        String line;
        while((line = br.readLine())!=null){
            stringBuffer.append(line).append("\r\n");
        }
        return stringBuffer.toString();
    }
}
```

## TCP 案例3【文件下载】

### 1.客户端代码
```java
package com.zpc.socket.download;

import java.io.*;
import java.net.InetAddress;
import java.net.Socket;
import java.util.Scanner;

/**
 * @author : zpc20 //作者
 * @version : 1.0 // 版本
 * @ClassName : Client  //类名
 * @Description : 客户端 发送消息"hello,server" ==> 服务端 //描述
 * @Date: 2024-09-26  下午 01:13
 */
public class Client {
    public static void main(String[] args) throws IOException {
        // 1. 获取用户输入
        Scanner scanner = new Scanner(System.in);
        System.out.println("输入要下载的文件名: ");
        String fileName = scanner.next();
        // 2. 创建连接
        Socket socket = new Socket(InetAddress.getLocalHost(), 9998);
        // 3. 通过socket 输出流发送到服务端
        BufferedOutputStream outputStream = new BufferedOutputStream(socket.getOutputStream());
        outputStream.write(fileName.getBytes()); // 写入数据到数据通道
        outputStream.flush();
        socket.shutdownOutput(); // 写入结束标记


        // 4. 接收下载文件
        BufferedInputStream bis = new BufferedInputStream(socket.getInputStream());
        byte[] fileBytes = StreamUtil.streamToByteArray(bis);
        System.out.println(fileBytes.length);
        String filePath = "C:\\Users\\zpc20\\Desktop\\截图\\downloads\\" + fileName;
        BufferedOutputStream bosTo = new BufferedOutputStream(new FileOutputStream(filePath));
        bosTo.write(fileBytes);

        // 关闭相关流
        bosTo.close();
        bis.close();
        socket.close();
    }
}
```

### 2.服务端代码

```java
package com.zpc.socket.download;

import java.io.*;
import java.net.ServerSocket;
import java.net.Socket;

/**
 * @author : zpc20 //作者
 * @version : 1.0 // 版本
 * @ClassName : Server  //类名
 * @Description : 服务端  //描述
 * @Date: 2024-09-26  下午 01:13
 */
public class Server {
    public static void main(String[] args) throws IOException {
        // 1. 本机9999端口监听
        //    注意: 💡1.要求没有服务占用9999端口
        //         💡2.这个ServerSocket 可以通过 accept() 返回多个Socket【多并发】
        ServerSocket serverSocket = new ServerSocket(9998);
        System.out.println("监听9998端口，等待连接。。。");
        // 2. 获取socket连接
        Socket socket = serverSocket.accept();

        // 3. 读取客户端数据 ==> 下载文件名
        InputStream inputStream = socket.getInputStream();
        String fileName = StreamUtil.streamToStringStream(inputStream);
        System.out.println("获取到文件名: " + fileName);

        // 4. 根据文件名寻找文件
        String root = "C:\\Users\\zpc20\\Desktop\\截图\\resource";
        String filePath = FileUtil.findFilePathByName(root, fileName);
        if (filePath == null) {
            // 默认返回文件
            filePath = root + "\\404.html";
        }
        // 获取本地文件流
        BufferedInputStream bis = new BufferedInputStream(new FileInputStream(filePath));
        byte[] fileBytes = StreamUtil.streamToByteArray(bis);
        System.out.println(fileBytes.length);
        // 发送文件
        BufferedOutputStream bos = new BufferedOutputStream(socket.getOutputStream());
        bos.write(fileBytes);
        bos.flush(); // 刷新数据到通道🔴🔴🔴🔴🚨🚨🚨
        socket.shutdownOutput();


        // 关闭流
        bis.close();
        inputStream.close();
        socket.close();
        serverSocket.close();

    }

}
```

### 3. StreamUtil工具

```java
package com.zpc.socket.download;

import java.io.*;

/**
 * @author : zpc20 //作者
 * @version : 1.0 // 版本
 * @ClassName : StreamUtil  //类名
 * @Description : 工具类  //描述
 * @Date: 2024-09-26  下午 02:10
 */
public class StreamUtil {

    /**
     * 功能： 把一个输入流转换为字节数组
     *
     * @param is 输入流
     * @return byte[]
     */
    public static byte[] streamToByteArray(InputStream is) throws IOException {
        // 创建字节数组输出流
        ByteArrayOutputStream bos = new ByteArrayOutputStream();
        byte[] b = new byte[1024]; // buffer
        int len;
        while ((len = is.read(b)) != -1) {
            bos.write(b, 0, len);
        }
        byte[] array = bos.toByteArray();
        bos.close();
        return array;
    }

    /**
     * InputStream 转换为String
     *
     * @param is 输入流
     * @return String
     */
    public static String streamToStringStream(InputStream is) throws IOException {
        byte[] b = new byte[1024]; // buffer
        int len;
        StringBuilder s = new StringBuilder(); // 返回
        while ((len = is.read(b)) != -1) {
            s.append(new String(b, 0, len));
        }
        return s.toString();
    }

    /**
     * InputStream 转换为 String
     *
     * @param is 输入流
     * @return String
     */
    public static String streamToStringReader(InputStream is) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(is));
        StringBuilder stringBuffer = new StringBuilder();
        String line;
        while((line = br.readLine())!=null){
            stringBuffer.append(line).append("\r\n");
        }
        return stringBuffer.toString();
    }
}

```

### 4. FileUtil工具

```java
package com.zpc.socket.download;

import java.io.File;

/**
 * @author : zpc20 //作者
 * @version : 1.0 // 版本
 * @ClassName : FileUtil  //类名
 * @Description : 文件工具类  //描述
 * @Date: 2024-09-26  下午 03:43
 */
public class FileUtil {
    /**
     * 根据根目录和文件名获取文件路径
     * 递归实现遍历
     *
     * @param root // 根目录
     * @param name // 文件名
     * @return String
     */
    public static String findFilePathByName(String root, String name) {
        File file = existFile(root, name);
        if (file != null) {
            return file.getAbsolutePath();
        }
        return null;
    }

    /**
     * 判断文件是否存在root目录中
     *
     * @param root // 根目录
     * @param name // 文件名
     * @return
     */
    public static File existFile(String root, String name) {
        File file = new File(root);
        File[] files = file.listFiles();
        for (int i = 0; i < files.length; i++) {
            if (files[i].isDirectory()) {
                findFilePathByName(files[i].getAbsolutePath(), name);
            } else if (files[i].isFile() && files[i].getName().equals(name)) {
                return files[i];
            }
        }
        return null;
    }

    // @Test
    // public void testFindFilePathByName() {
    //     String filePath = findFilePathByName("C:\\Users\\zpc20\\Desktop\\截图\\resource", "bg.png");
    //     System.out.println(filePath);
    // }
}
```




## 🤔netstat指令

![image-20240926145615267](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261456508.png)

![image-20240926145958664](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261459863.png)

![image-20240926150234023](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261502282.png)

## UDP编程【了解】

![image-20240926150524188](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261505446.png)

![image-20240926150738079](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261507336.png)

![image-20240926150749429](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261507688.png)

### 1.Reciver接收端

```java
package com.zpc.socket.UDP;

import java.io.IOException;
import java.net.DatagramPacket;
import java.net.DatagramSocket;
import java.net.InetAddress;

/**
 * @author : zpc20 //作者
 * @version : 1.0 // 版本
 * @ClassName : Reciver  //类名
 * @Description : 接收端  //描述
 * @Date: 2024-09-26  下午 03:09
 */
public class Reciver {
    public static void main(String[] args) throws IOException {
        // 1. 创建DatagramSocket准备接收数据
        DatagramSocket socket = new DatagramSocket(9999);
        // 2. 构建一个DatagramPacket对象，准备接收数据
        byte[] buf = new byte[1024]; // UDP最大64k
        DatagramPacket dp = new DatagramPacket(buf, buf.length);
        // 3. 接收数据 填充到packet对象
        socket.receive(dp);
        // 4. 可以把packet 进行拆包 取出数据 并显示
        int len = dp.getLength();
        byte[] data = dp.getData();
        System.out.println(new String(data, 0, len));

        //  发送
        byte[] sData = "OK".getBytes();
        socket.send(new DatagramPacket(sData,sData.length, InetAddress.getByName("192.168.3.15"),9998));

        // 5. 关闭资源
        socket.close();
    }
}
```

### 2. Send发送端

```java
package com.zpc.socket.UDP;

import java.io.IOException;
import java.net.*;

/**
 * @author : zpc20 //作者
 * @version : 1.0 // 版本
 * @ClassName : Sender  //类名
 * @Description : 发送端  //描述
 * @Date: 2024-09-26  下午 03:09
 */
public class Sender {
    public static void main(String[] args) throws IOException {
        // 1. 创建DatagramSocket对象
        DatagramSocket socket = new DatagramSocket(9998);
        // 2. 发送数据 封装到Packet中
        byte[] data = "Hello,World".getBytes();
        DatagramPacket dp = new DatagramPacket(data, data.length, InetAddress.getByName("192.168.3.15"), 9999);
        socket.send(dp);

        // 接收
        byte[] bytes = new byte[1024];
        DatagramPacket reciverdp = new DatagramPacket(bytes,bytes.length);
        socket.receive(reciverdp);
        // 拆包
        int len = reciverdp.getLength();
        byte[] reciverData = reciverdp.getData();
        System.out.println(new String(reciverData, 0, len));

        // 3. 关闭资源
        socket.close();


    }
}
```

# 五、项目开发流程

![image-20240926180054159](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409261800453.png)

# 六、反射

> ![image-20240927160610907](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409271606205.png)
>
> ![image-20240927160732515](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409271607686.png)
>
> **原理图**
>
> ![image-20240927161325720](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409271613218.png)

![image-20240927161419982](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409271614230.png)

## 1. 反射相关的类

![image-20240927161443296](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409271614528.png)

## 2.优缺点

![image-20240927161723563](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409271617804.png)

## 3. 常用方法

![image-20240927161920650](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409271619994.png)

![image-20240927162041381](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409271620566.png)

![image-20240927162057490](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409271620679.png)

![image-20240927162110298](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409271621506.png)



![image-20240927214434161](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409272144370.png)

## 4.几种类加载方式

![image-20240927162230950](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409271622265.png)

![image-20240927214821250](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409272148419.png)

![image-20240927215012733](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409272150924.png)

![image-20240927215150593](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409272151799.png)

![image-20240927215241716](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409272152952.png)

![image-20240927220257726](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409272202951.png)

![image-20240927220347084](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409272203342.png)

![image-20240927220940202](C:/Users/zpc20/AppData/Roaming/Typora/typora-user-images/image-20240927220940202.png)

## 5.哪些类有class

![image-20240927221052716](C:/Users/zpc20/AppData/Roaming/Typora/typora-user-images/image-20240927221052716.png)

![image-20240927221336882](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409272213073.png)

![image-20240927221404198](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409272214371.png)

![image-20240927223321278](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409272233478.png)

![image-20240927223636672](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409272236874.png)

## 6.类加载原理

![image-20240927223740845](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409272237159.png)

![image-20240927224102757](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409272241983.png)

### 1.过程图

![image-20240927224452661](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409272244934.png)

![image-20240927224530301](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409272245727.png)

![image-20240927224639902](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409272246107.png)

![image-20240927224656819](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409272246192.png)

![image-20240927224822953](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409272248171.png)

![image-20240927225047989](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409272250194.png)

![image-20240927225102423](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409272251771.png)

![image-20240927225628949](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409272256109.png)

## 7.类结构信息

![image-20240927225940854](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409272259106.png)

## 8. 反射创建对象

### 1.构造器

![image-20240927230912897](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409272309228.png)

```java
package com.zpc.advance;

import java.lang.reflect.Constructor;
import java.lang.reflect.InvocationTargetException;

/**
 * @author : zpc20 //作者
 * @version : 1.0 // 版本
 * @ClassName : ReflectCreateObject  //类名
 * @Description : 反射创建对象  //描述
 * @Date: 2024-09-27  下午 11:09
 */
public class ReflectCreateObject {
    public static void main(String[] args) throws ClassNotFoundException, InstantiationException, IllegalAccessException, NoSuchMethodException, InvocationTargetException {
        // 1. 获取Class对象
        Class<?> userClass = Class.forName("com.zpc.advance.User");
        // 2. 通过public的无参构造器创建
        Object o = userClass.newInstance();
        System.out.println(o);
        // 3. 通过public的有参构造器创建
        Constructor<?> constructor = userClass.getConstructor(String.class);
        Object o1 = constructor.newInstance("klj");
        System.out.println(o1);
        // 4. 通过private的有参构造器创建
        Constructor<?> constructor1 = userClass.getDeclaredConstructor(int.class, String.class);
        constructor1.setAccessible(true); // 爆破，使用反射可以访问private构造器
        Object o2 = constructor1.newInstance(100, "zsf");
        System.out.println(o2);
    }
}

class User {
    private String name = "zpc";
    private int age = 10;

    public User() { // public 无参

    }

    public User(String name) { // public 有参
        this.name = name;
    }

    private User(int age, String name) { // private 有参构造器
        this.age = age;
        this.name = name;
    }

    @Override
    public String toString() {
        return "User{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }
}
```

### 2. 属性

![image-20240927232357855](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409272323124.png)

![image-20240927232759001](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409272327191.png)

### 3. 成员【方法】

![image-20240927232926745](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409272329986.png)

# 七、正则表达式

> ![image-20240929213419256](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292134484.png)
>
> ![image-20240929213448850](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292134076.png)

## 1. 快速入门

### 案例【提取文章中的所有的单词和数字】

```java
package com.zpc.regexp.simple;

import java.util.regex.Matcher;
import java.util.regex.Pattern;

/**
 * @author : zpc20 //作者
 * @version : 1.0 // 版本
 * @ClassName : Regexp  //类名
 * @Description : 正则表达式使用  //描述
 * @Date: 2024-09-29  下午 09:14
 */
public class Regexp {
    public static void main(String[] args) {
        // 要处理的文本
        String content = "1995年，" +
                "互联网的蓬勃发展给了Oak机会" +
                "。业界为了使死板、单调的静态网页能够“灵活”起来，急需一种软件技术来开发一种程序" +
                "，这种程序可以通过网络传播并且能够跨平台运行。" +
                "于是，世界各大IT企业为此纷纷投入了大量的人力、物力和财力。" +
                "这个时候，Sun公司想起了那个被搁置起来很久的Oak，" +
                "并且重新审视了那个用软件编写的试验平台，由于它是按照嵌入式系统硬件平台体系结构进行编写的，" +
                "所以非常小，特别适用于网络上的传输系统，而Oak也是一种精简的语言，程序非常小，适合在网络上传输。" +
                "Sun公司首先推出了可以嵌入网页并且可以随同网页在网络上传输的Applet（Applet是一种将小程序嵌入到网页中进行执行的技术），" +
                "并将Oak更名为Java。" +
                "5月23日，Sun公司在Sun world会议上正式发布Java和HotJava浏览器。" +
                "IBM、Apple、DEC、Adobe、HP、Oracle、Netscape和微软等各大公司都纷纷停止了自己的相关开发项目，" +
                "竞相购买了Java使用许可证，并为自己的产品开发了相应的Java平台。";
        // 提取文章中的所有的单词
        // 1. 传统的方式，使用遍历方式,代码量大,效率不高
        // 2. 正则表达式
        // 1. 创建一个Pattern对象，模式对象，可以理解为就是一个正则表达式
        // Pattern pattern = Pattern.compile("[a-zA-Z]+"); // 匹配字母
        // Pattern pattern = Pattern.compile("[0-9]+"); // 匹配数字
        Pattern pattern = Pattern.compile("([0-9]+)|([a-zA-Z]+)"); // 匹配数字+字母
        // 2. 创建匹配器对象
        /**
         * 理解: 就是matcher 匹配器按照pattern【模式/样式】,到content中匹配
         * 找到返回true,否则false
         */
        Matcher matcher = pattern.matcher(content);
        // 3. 循环匹配
        while(matcher.find()){
            // 查找匹配, 匹配的内容放入m.group(0)
            System.out.println("匹配的字符串: "+matcher.group());
        }

    }
}
```

## 2.底层实现

![image-20240929214124988](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292141212.png)

![image-20240929214334701](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292143910.png)

![image-20240929214642504](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292146719.png)

![image-20240929214846539](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292148742.png)

![image-20240929215154320](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292151503.png)

## 3. 基本介绍

![image-20240929215602404](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292156699.png)

![image-20240929215706513](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292157841.png)

![image-20240929215930182](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292159410.png)

#### 1. 匹配符

![image-20240929220403334](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292204593.png)

![image-20240929222727095](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292227488.png)

![image-20240929223109762](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292231052.png)

![image-20240929223408006](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292234299.png)

![image-20240929223802261](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292238507.png)

#### 2. 限定符

![image-20240929223914886](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292239121.png)

![image-20240929224257884](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292242133.png)

##### **🔴细节🔴**

![image-20240929224549491](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292245663.png)

![image-20240929224728515](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292247851.png)

#### 3. 定位符

![image-20240929225241695](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292252967.png)

#### 4. 分组

![image-20240929225900282](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292259526.png)

![image-20240929230121944](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292301172.png)

![image-20240929230548983](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292305188.png)

#### 5.实例

![image-20240929230744101](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292307294.png)

![image-20240929230926467](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292309652.png)

![image-20240929231033418](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292310607.png)

![image-20240929231126213](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292311405.png)

![image-20240929231757018](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292317238.png)

#### 6. 常用类

![image-20240929232144049](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292321327.png)

![image-20240929232611483](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292326676.png)

##### 1. Macher类

![image-20240929232645915](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292326183.png)

![image-20240929233043739](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292330999.png)

#### 7. 反向引用

![image-20240929233427735](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292334034.png)

![image-20240929233656363](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292336570.png)

> 3. `(\\d)(\\d)\\2\\1`

![image-20240929234651445](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292346687.png)

![image-20240929234701618](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292347813.png)

![image-20240929234809049](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292348232.png)

![image-20240929234916624](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292349809.png)

```java
String con = "我我我要要要要学Java";
con = con.replaceAll("(.)\\1+","$1");
System.out.println(con);
```

![image-20240929235308145](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409292353339.png)

![image-20240930001031791](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409300010271.png)

![image-20240930001332778](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409300013983.png)

![image-20240930001418953](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409300014137.png)

![image-20240930002034584](https://mygithubcdn.educatedtest.eu.org/gh/mycodeoen/MyPicture@main/blog/202409300020779.png)

