

## 重视分析问题和程序设计的思想

### if流程控制语句

```shell
if 条件内容
   then 
     内容
fi
```



###for循环语句

```shell
for
do
    内容
done

```



### 环境变量

```
evn 只显示全局变量
set 显示全局变量和局部变量
set -o显示bash shell的所有参数配置信息
```



### 设置环境变量

```
全局变量设置路径： /etc/bashrc  (推荐优先设置)     /etc/profile    /etc/profile.d

1. export  变量名=value
2. declare -x 变量名=value
3. 变量名=value; export 变量名
```



 ### 取消环境变量   

```
1. unset $变量名 
2. 单引号，不会将变量转换成其对应的值，双引号和无符号则会将变量转换成对应的值
```





### 把linux命令结果作为结果赋值给变量名书写规范

```
1. ls命令      变量名=$(Linux指令)            CMD=$(ls)       

2. 当有变量连接其他字符是，变量名要用大括号   $dbname_tname          ${dbname}_tname 
```



### sed命令

```
作用：文本编辑留
sed命令格式：
sed [option] 'command' file(s)
sed [option] -f scriptfile file(s)
处理机制：一行一行顺序执行命令
```



### awk命令

```linux
作用：格式化文本，对文本进行较复杂处理
1. BEGIN 先执行BEGIN的内容，在执行文本内容
   e.g: awk 'BEGIN {print "a", "b"} {print $NF, $1}' test.log
2. END 先执行文本内容，再执行END的内容
   e.g: awk 'END {print "a", "b"} 作用：文本编辑留

3. $0表示整行信息   $NF表示最后一个字段   NF表示文本信息的列数
4. NR表示行号   
5. OFS 表示当前输出显示信息的分隔符，显示在终端
   e.g: awk '{OFS=":"} {print $NF, $1}' test.log     自定义分隔符
6. FS 表示当前信息显示的分隔符
   e.g: awk '{FS=":"} {print $NF, $1}' test.log
```



### Linux数字特殊处理

```linux
1. N范围：1~9, 用$N，若N>9, 用{$N}
2. N=0, $N：获取当前脚本文件执行的名称
3. $#: 获取脚本传参的总个数
4. $*：获取当前shell脚本所有传参的全部参数，"$*"将所有的参数视为单个字符串，"$1, $2, $3"
5. $@: 获取当前shell脚本所有传参的全部参数，"$@"将所有的参数视为独立的字符，"$1", "$2", "$3"
6. $?: 获取执行上一个指令的执行状态返回值（0成功，非零失败）
7. $$: 获取当前执行的shell脚本的进程号(PID)
```



### shell内置变量命令

```
1. echo 在终端打印  -n:不换行  \n：换行   -e：转义
2. eval,set命令：
3. exec: 能够在不创建新的子进程下去执行指定命令
4. shift: 每执行一次shift,参数从第一个逐渐减少， ($3, $2, $1) shift之后（$2, $1）
```



### shell变量子串说明

```
1. ${paramrter} 获取变量的value    
2. ${#parameter} 获取变量内容的长度，包含字符间的空格
3. ${parameter:offset} 在parameter变量中，从位置offset之后的位置开始提取子串到结尾  ${parameter：2}
4. ${parameter:offset:length} 在parameter变量中，从位置offset之后的位置开始提取长度为length的子串
    $(parameter:2:4)
5. ${parameter#word} 从变量parameter开头(第一个位置)开始删除最短匹配的word子串，
6. ${parameter##word} 从变量parameter开头(第一个位置)开始删除最长匹配的word子串
7. ${parameter%word} 从变量parameter结尾(第一个位置)处开始删除最短匹配的word子串
8. ${parameter%%word} 从变量parameter结尾处(第一个位置)开始删除最长匹配的word子串
9. ${parameter/pattern/string} 使用string代替第一个匹配到的pattern
10. ${parameter//pattern/string}  使用string代替匹配到的所有pattern
```



### shell特殊变量拓展

```
1. ${parameter:-word} 若变量存在，输出其值，不存在，输出word
   用途：如果变量未定义，则返回备用值，防止变量为空值或因未定义而导致异常
   e.g：result=${name:-unset}
2. ${parameter:=word} 若变量存在，输出其值，不存在，则变量被赋值word
3. ${parameter:?word} 若变量存在，输出其值，不存在，word作为标准错误输出。
   用途：捕捉变量未定义或为空值而导致的错误，并推出程序
4. ${parameter:+word} 若变量存在，则用word替换变量的值，若变量未定义和为空，则输出为空
```



### shell数值运算

```
1. (()): 用于整数的数值运算和数值比较 
 	  e.g: echo $((1+1))
2. let: 命令运算符，let赋值表达式
   e.g: i=2 let i=i+8 将i=2的值赋值给表达式
3. bc管道命令  echo 4+4|bc
4. awk命令计算： echo "20 30" |awk '{peint ($1+S2)}'
5. $[]: i=5 i=$[i+6]  echo $i      $[]: 用于整数运算
6. expr  
   e.g expr 1 + 1 

```



### 逻辑判断test

```linux
test 与符号[]效果相同
-f: 普通文件
-d: 目录
-x: 执行权限
-r: 可读权限
-w: 写权限
-s: size
-n: no zero   字符长度不为零
-z: zero  字符长度为零
-a: and  与
-o: or  或
!: 非
判断文件是否存在： 
[ -f test.sh && echo true || echo false]
test -f test.sh && echo true || echo false
```



### 运算符号

```
-eq: equel 等于          =
-ne: no equel 不等于     !=
-gt: greater  大于       >
-ge: greater equel 大于或等于     >=
-lt: less than  小于   <
-le: less equel 小于或等于    <=
```



### if语句表达式

```shell
if <条件表达式>
 then
   指令
fi


if <条件表达式>; then
   指令
fi

if <条件表达式>
	then
		if <条件表达式>
			then
				指令
		fi
fi
```



### if else/elif语句表达式

```shell
if <条件表达式1>
	then
		指令集1
elif <条件表达式2>
		then
			指令2
else
		指令集3
fi
```



### function函数

```shell
推荐写法：
function 函数名() {
	指令
	return n
}

简写1：
函数名() {
	指令
	return n
}

简写2：
函数名 {
	指令
	return n
}
```



### case语句

```shell
case "变量" in
	值1）
		指令1...
		;;
	值2）
		指令2...
		;;
	*）
		指令3...
esac
		
```

### while && unit

```shell
while <条件表达式>    先判断条件是否满足，满足，在执行循环语句
do 
	指令...
done


until <条件表达式>  先判断条件是否满足，不满足，执行循环语句
do
	指令
done
```



### for循环语句

```
for 变量名 in 变量取值列表
do
	指令...
done

{5..1} 大括号生成数字序列的方法
`ls` 命令用反括号括起来
```



### shell数组定义

```shell
定义数组：
arrary=(value1 value2 value3 ...)
arrary=([1]=one [2]=two [3]=three ...)

读取数组值：
echo ${array[*]}   echo ${array[@]} 读取所有的数组值
echo ${array[1]}   索引
${#arrary[*]}      获取数组的长度
arrary[0] = tanwenjian   数组赋值
unset arrary[0] 数组删除
unset arrary    删除整个数组
echo ${arrary[*]:1:3}   截取下表为1-3的元素值
echo ${arrary[*]/1/b}   将数组中的1替换成b, 不会修改原来数组的内容

echo ${arrary[*]#o*}    从左边开始匹配最短的元素并删除
echo ${arrary[*]##o*}   从左边开始匹配最长的元素并删除

echo ${arrary[*]%f*}    从右边开始匹配最短的元素并删除
echo ${arrary[*]%%f*}   从右边开始匹配最长的元素并删除
```

