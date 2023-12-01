## 标识符

- 第一个字符必须是字母表中字母或下划线 _ 。
- 标识符的其他的部分由字母、数字和下划线组成。
- 标识符对大小写敏感。
在 Python3 中，可以用中文作为变量名，非 ASCII 标识符也是允许的了。

## python保留字
保留字即关键字，我们不能把它们用作任何标识符名称。Python 的标准库提供了一个 keyword 模块，可以输出当前版本的所有关键字：
```python
>>> import keyword
>>> keyword.kwlist
['False', 'None', 'True', 'and', 'as', 'assert', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
```


## 注释
单行注释：#
多行注释：'''和“”“
```python
#单行注释
'''
多行
注释
'''
```

## 行与缩进
python用缩进和空格代替了{}和()符号
语句后面的:表示代码组的开始，相同的缩进空格数表示一个代码组
```python
if True:
	print('True')
else:
	print('False')
```

## 多行语句
Python 通常是一行写完一条语句，但如果语句很长，我们可以使用反斜杠 \\ 来实现多行语句
```python
total = 1 + \
        2 + \
        3
```
在 \[], {}, 或 () 中的多行语句，不需要使用反斜杠 \，例如：
```python
total = ['bob', 'kip', 
         'jojo']
```

## 输入和输出
### 输出
输出一般用print()函数
```python
print('xia')        #xia
print(200+100)      #300
print('xia','yi')   #xia yi   (输出,自动变为空格)
print('xia'+'yi')   #xiayi    (+没有空格)
print("%.3f" %2.3)  #2.300    (后面的%相当于,)
```

print( )函数执行后会自动换行，如果想不要自动换行，后面加上参数`end=''`

`print('hello',end='')`

end参数是用来控制输出的结尾字符，在默认情况下，end='/n'即换行，那么改成空字符就不会换行



### 输入

输入一般用`input()`函数
```python
name=input('请输入您的名字：')  #括号里放提示语
print('Hello,',name)  #Hello, Jack
```
注意：input()返回的数据类型是**string**，如果输入的是数字，则需要转换成数字类型。
```python
s=intput('age:')
Age=int(s)
```



# 数据类型

Python3中常见的数据类型有：
- Number（数字）
- String（字符串）
- bool（布尔类型）
- List（列表）
- Tuple（元组）
- Set（集合）
- Dictionary（字典）

可以分为：
- 不可变数据：Number（数字）、String（字符串）、Tuple（元组）
- 可变数据：List（列表）、Dictionary（字典）、Set（集合）
此外还有一些高级的数据类型，如: 字节数组类型(bytes)。

判断类型
内置的 type() 函数可以用来查询变量所指的对象类型。
```python
>>> a, b, c, d = 20, 5.5, True, 4+3j
>>> print(type(a), type(b), type(c), type(d))
<class 'int'> <class 'float'> <class 'bool'> <class 'complex'>
```

此外还可以用 isinstance 来判断
```python
>>> a = 111
>>> isinstance(a, int)
True
```
isinstance 和 type 的区别在于：
- type()不会认为子类是一种父类类型。
- isinstance()会认为子类是一种父类类型。

## 变量
python中的变量不用数据类型声明，可以把任意数据类型赋值给变量
```python
var1=1          #创建变量
del var1        #删除变量
var1,var2=1,2   #创建多个变量 (注意这与其他语言不同)
del var1,var2   #删除多个变量
```
这种类型不固定的变量的语言称之为动态语言，与之对应的是静态语言。静态语言有Java,cpp

### 存储原理
	a='ABC'
Python解释器：
1. 在内存中创建了一个`ABC`的字符串
2. 在内存中创建了一个名为`a`的变量，并把它指向`ABC`
即变量a中存放的是字符串`ABC`的地址
```python
a='ABC'
b=a
a='DEF'
print(b)#out:ABC (b中存放的是字符串'ABC'的地址)
```

### 常量
常量就是数值不变的变量。在Python中通常用大写字母表示常量
	`PI=3.1415926`
但事实上`PI`仍然是一个变量，Python根本没有任何机制保证`PI`不会被改变

### 空值
空值是Python里一个特殊的值，用`None`表示。`None`不能理解为`0`，因为`0`是有意义的，而`None`是一个特殊的空值。




## Number数字
数字类型包括了：
- int整型：1,2,3  ---没有大小限制
- float浮点型：1.2 ，1.34e2(134) ---小数点和科学计数法
- complex复数：a+bj ,complex(a,b)  ---由实部a和虚部b组成(a,b都是浮点型)

### 整型
十六进制的表示：0x12,0xff00  0x表示后面的数字是十六进制数字
对于很大的数，例如100000000很难数清楚0的个数，允许在数字之间以`_`分隔，写成1_0000_0000是和100000000等价的，且十六进制也可以如此写作



### 数值运算

加减乘除和其他语言都是一样的

幂运算：**       （ 2**2相当于2的平方为4

整除运算：//     （ 5//2得2 得到商的整数部分



### bool

布尔值只有`True`,`False`两个值 
bool是int的子类，布尔值和布尔代数表示一致，True=1,False=0,布尔值可以和数字做运算

布尔值可以用`and`、`or`和`not`运算

## str字符串

字符串是以单引号`'`或双引号`"`括起来的任意文本。如果`'`本身也是一个字符，那就可以用`""`括起来，比如`"I'm OK"`
如果字符串内部既包含`'`又包含`"`怎么办？可以用转义字符`\`来标识，比如：
	`'I\'m \"OK\"!'


## list列表
list是一种有序的集合，可以随时添加和删除其中的元素。
```python
classmates=['Bob','Lang','Jack']
print(classmates) #['Bob', 'Lang', 'Jack']
```

```python
classmates=['Bob','Lang','Jack']
#获取元素个数
len(classmates) #out:3
#索引访问单个元素
classmates[0]   #out:'Bob'
classmates[-1]  #out:'Jack'
#添加元素
classmates.append('Jojo') #['Bob','Lang','Jack','Jojo']
classmates.insert(1,'Adam') #['Bob','Adam','Lang','Jack','Jojo']
#删除元素
classmates.pop() #['Bob','Adam','Lang','Jack']
classmates.pop(1)#['Bob','Lang','Jack']
#替换元素，直接赋值替换
classmates[1]='Michael'#['Bob','Michael','Jack']
#List可以包涵任何数据类型
L = ['Apple', 123, True]
s = ['python', 'java', ['asp', 'php'], 'scheme']#注意len(s)=4
#多重列表的索引
p = ['asp', 'php']
s = ['python', 'java', p, 'scheme']
p[1]    #out:'php'
s[2][1] #out:'php'
#空列表
L=[] #len(L)=0
```


## tuple元组
另一种有序列表叫元组：tuple。tuple和list非常类似，但是tuple一旦初始化就不能修改
```python
classmates = ('Michael', 'Bob', 'Tracy')
print(classmates) #('Michael', 'Bob', 'Tracy')
```
这个classmates没有append(),insert()等方法，也不能重新赋值，但索引是跟list相同的

优点：tuple元素不可变，代码更加安全。尽量用tuple去替换list
```python
#定义tuple的注意事项
t=()    #定义一个空元组
t=(1,)  #定义只有一个元素的元组
#因为括号()既可以表示tuple又可以表示数学中的符号，计算机就会对其产生分歧。所以，规定只有1个元素的tuple定义时后面要有,

#"可变"tuple
t=('a','b',('X','Y'))
t[2][0]='C'
t[2][1]='D'
print(t) #out:('a','b',('C','D'))
```

![[Pasted image 20230714172859.png|493]]
tuple里面其实存放的是地址，所以内层tuple元素改变但不改变地址


## set集合
set集合是一个无序、无重复元素的容器，每个元素都被视为键值和实值二者。

```python
s=set([1,2,3])
print(s) #{1, 2, 3}
#注意，传入的参数[1, 2, 3]是一个list，而显示的{1, 2, 3}只是告诉你这个set内部有1，2，3这3个元素，显示的顺序也不表示set是有序的。
```

```python
s=set([1,1,2,2,3,3,4,4])
print(s)    #{1,2,3,4}  自动过滤重复元素
#添加元素
s.add(5)    #{1,2,3,4,5}
#删除元素
s.remove(3) #{1,2,4,5}

#set可以看成数学意义上的无序和无重复元素的集合，因此，两个set可以做数学意义上的交集、并集等操作：
s1=set([1,2,3])
s2=set([2,3,4])
s1&s2  #{2,3}      交集
s1|s2  #{1,2,3,4}  并集
```
set和dict的唯一区别仅在于没有存储对应的value，但是，set的原理和dict一样，所以，同样不可以放入可变对象，因为无法判断两个可变对象是否相等，也就无法保证set内部“不会有重复元素”。试试把list放入set，看看是否会报错。



## dictionary字典

字典也就是map键值对，具有极快的查找速度。dict里面的元素**可以增删**。字典的元素是**无序的**
```python
d={'A':90,'B':80,'c':60}
print(d) #{'A':90,'B':80,'c':60}
d['A']   #90
```

```python
#替换值，直接赋值替换
d['A']=20 
#删除元素
d.pop('C') #{'A':90,'B':80}
```

如果key不存在，dict就会报错。避免报错就需要判断key是否存在
```python
#方式一：in
'D' in d #False
#方式二：dict的get()方法
d.get('D')     #如果key不存在，返回None
d.get('D',-1)  #或者返回自己指定的value
```

和list比较，dict有以下几个特点：
1. 查找和插入的速度极快，不会随着key的增加而变慢；
2. 需要占用大量的内存，内存浪费多。
而list相反：
1. 查找和插入的时间随着元素的增加而增加；
2. 占用空间小，浪费内存很少。
所以，dict是用空间来换取时间的一种方法。

`注意`：dict的key必须是**不可变对象**。
这是因为dict根据key来计算value的存储位置(哈希算法)，如果每次计算相同的key得出的结果不同，那dict内部就完全混乱了。要保证hash的正确性，作为key的对象就不能变。在Python中，字符串、整数等都是不可变的，因此，可以放心地作为key。而list是可变的，就不能作为key

```python
key=[1,2,3]
d[key]='list'
#error:TypeError: unhashable type: 'list'
```



```python
#字典的遍历
d = {
    'a':90,
    'b':80,
    'c':70,
    'd':60
}
for key ,value in d.items(): #item()遍历键和值
    print(key,value)
>>> a 90
	b 80
	c 70
	d 60
for i in d.values():  #values()遍历值
    print(i)
>>> 90
	80
	70
	60
for i in d.keys(): #keys()遍历键
    print(i)
>>> a
	b
	c
	d
```





### 不可变对象

对于可变对象，比如list，对list进行操作，list内部的内容是会变化的，比如：
```python
a = ['c', 'b', 'a']
a.sort()  #调用对象自身方法会改变自身对象内容
print(a)  #['a', 'b', 'c']
```

而对于不可变对象，比如str，对str进行操作呢：
```python
a = 'abc'
b=a.replace('a', 'A')  
print(a)   #'abc'
print(b)   #'Abc'
#调用a.replace时，创建了一个新的字符串'Abc'并返回，所以原先的变量a不变
```
所以，对于不变对象来说，调用对象自身的任意方法，也不会改变该对象自身的内容。相反，这些方法会创建新的对象并返回，这样，就保证了不可变对象本身永远是不可变的。



# 流程控制

## if条件判断

```python
if x:
    print('True')
#只要x是非零数值、非空字符串、非空list等，就判断为True，否则为False
age = 3
if age >= 18:
    print('adult')
elif age >= 6:
    print('teenager')
else:
    print('kid')
```



## 循环语句

### for语句
```python
a=[1,2,3]
for x in a:
	print(x) #out: 1 2 3
#range()函数表示范围
for x in range(0,100) #out:0~100 总共101个数
```

### while语句
```python
while x>0:
	print('>0')
```

### break语句
```python
n=1
while n<100:
	if n>10:
		break
	print(n)
#1~10
```

### continue语句

跳过这次循环，到下一轮



## pass关键字

pass是一个特殊的关键字，其主要作用是作为空操作或占位语句。它被设计出来是为了保持程序结构的完整性。当遇到某些语法需要有语句块但是还不需要实现任何功能时，就可以使用pass来填充。例如，在你定义一个函数但还未想好其具体逻辑时，就可以先放置一个pass语句。

此外，pass也常用在循环和条件判断语句中，如for循环、while循环以及if条件判断等场景。在这些地方，如果暂时不希望执行任何操作，也可以使用pass来填充。在某些复杂的代码结构中，合理使用pass可以使代码更加清晰和易于理解。

```python
def f():
    pass
```







# 函数
定义函数需要使用`def`语句
```python
def f(x):
	if x>0:
		return x
```
如果没有`return`语句，函数执行完毕后也会返回结果，只是结果为`None`。`return None`可以简写为`return`



## 主函数

在Py中其实不需要主函数，程序会默认从顶部往下运行所有代码。

但是，定义main函数相当于定义了程序的执行起点。main函数只在程序直接运行时执行，而被作为模块导入时不会执行，使得我们能清晰区分程序运作的方式。

`__name__`是一个内置变量，用于表示该模块的名字。当一个Python文件被直接运行时，其`__name__`变量的值为`"__main__"`；而当该文件被导入到其他文件中时，其`__name__`变量的值为该文件的模块名。

```python
def main():
    print('Hello,World')
if '__name__'=='__main__':
    main()         #也可以不用main函数，直接在这个if下写执行代码
```



## 空函数

如果想定义一个什么事也不做的空函数，可以用`pass`语句
```python
def nop():
	pass
#pass还可以用在其他语句里
if age >= 18:
	pass
```
pass可以用来作为占位符，比如现在还没想好怎么写函数的代码，就可以先放一个pass，让代码能运行起来。

## 参数检查
内置函数会在参数类型出错时点出错误，但自己定义的函数只会检查出参数个数错误(TypeError)而没有参数类型错误
用内置函数`isinstance()`实现数据类型检查

```python
def my_abs(x):
	if not isinstance(x,(int,float)): #传入的类型只能是int,float
		raise TypeError('bad operand type')
	if x>=0:
		return x
	else:
		return -x
```

## 返回多个值
```python
def f(x):
	y=x+1
	return x,y
a,b=f(1) #a接收了x值，b接收了y值，其实f(1)=(1,2)是一个tuple
```
`return x,y`返回的值是一个tuple，但在语法上返回一个tuple可以省略括号，而多个变量可以同时接收一个tuple，按位置赋给对应的值，所以，Python的函数返回多值其实就是返回一个tuple，但写起来更方便。



## 参数

### 位置参数

[位置参数].(https://zhuanlan.zhihu.com/p/412273465#%E4%BD%8D%E7%BD%AE%E5%8F%82%E6%95%B0)

### 默认参数

`def f(x,y=2)`
- 必选参数在前，默认参数在后，否则Python的解释器会报错。传入参数会先传给前面的变量
- 当函数有多个参数时，把变化大的参数放前面，变化小的参数放后面。变化小的参数就可以作为默认参数。
```python
def enroll(name,gender,age=19,city='Beijing'):
	return name,gender,age,city
enroll('Bon','F')                  #('Bon','F',19,'Beijing')
enroll('July','M',7)               #('July','M',7,'Beijing')
enroll('Jacky','M',8,'Xian')       #('Jacky','M',8,'Xian')
enroll('Jack','M',city='Xianning') #('Jack','M',19,Xianning)
#默认参数不是固定必须的，可以传入另外的值，而其他仍然使用默认参数
```

`注意`：定义默认参数要牢记，**默认参数必须指向不变对象**

```python
def add_end(L=[]):
	L.append('END')
	return L
add_end()  #调用默认参数 out:['END']
add_end()  #out:['END'，'END']
add_end()  #out:['END'，'END'，'END']
#调用默认参数，按理来说应该返回的只有['END']，而结果却越来越多，这是因为函数中L的指向逐渐增加了['END']

#可以用None不变对象来实现默认参数的无数次实现
def add_end(L=None):
	if L is None:
		L=[]
	L.append('END')
	return L
```

### 可变参数

通过在参数前加`*`实现传入参数的可变性
```python
def calc(numbers):
	for x in numbers
calc([1,2,3,4])  #可以使用list或tuple实现可变参数
#--------------------------
def calc(*numbers):
	for x in numbers
calc(1,2,3,4)    #用*来直接传入参数。但是在函数内部，number仍然收到的是一个tuple，只是省略了()
calc() #0个参数也是可以的
```

### 关键字参数

关键字参数允许传入0个或任意个含参数名的参数，这些关键字参数在函数内部自动组装为一个dict
```python
def person(name,age,**kw):  
	print('name:',name,'age:',age,'kw:',kw)  #用了,就不能用+
person('a',23)  #name: a age: 23 kw: {}
person('b',12,city='Beijing')  #name: b age: 12 kw: {'city': 'Beijing'}
person('c',34,city='Xian',gender='F')#name: c age: 34 kw: {'city': 'Xian', 'gender': 'F'}
#---------------------------------------
#检查是否有特点参数
def person(name,age,**kw):  
	if 'city' in kw:
		pass
```
关键字参数可以扩展函数的功能。比如，在person函数里，我们保证能接收到name和age这两个参数，但是，如果调用者愿意提供更多的参数，我们也能收到。试想你正在做一个用户注册的功能，除了用户名和年龄是必填项外，其他都是可选项，利用关键字参数来定义这个函数就能满足注册的需求。

和可变参数类似，也可以先组装出一个dict，然后，把该dict转换为关键字参数传进去：

```python
extra = {'city': 'Beijing', 'job': 'Engineer'}
person('Jack', 24, city=extra['city'], job=extra['job'])#out: name: Jack age: 24 other: {'city': 'Beijing', 'job': 'Engineer'}
#当然，上面复杂的调用可以用简化的写法：
extra = {'city': 'Beijing', 'job': 'Engineer'}
person('Jack', 24, **extra)#out: name: Jack age: 24 other: {'city': 'Beijing', 'job': 'Engineer'}
```
\*\*extra表示把extra这个dict的所有key-value用关键字参数传入到函数的\*\*kw参数，kw将获得一个dict，注意kw获得的dict是extra的一份拷贝，对kw的改动不会影响到函数外的extra

### 命名关键字参数

用命名关键字参数限制关键字参数的名字，\*后面的参数都被视作命名关键字参数
```python
#只接受city,job的关键字参数
def person(name,age,*,city,job):
person('Jack',24,city='Beijing',job='cleaner') #必须传入参数名city=xxx,job=xxx否则会报错
#如果参数定义中有一个可变参数，后面的命名关键字参数就不需要*了。命名关键字参数也可以有默认参数
def person(name,age,*args,city,job='Engineer')
```
`注意`：使用命名关键字参数时，如果没有可变参数就必须加`*`作为特殊分隔符。如果缺少*，将会被看位置参数

### 参数组合

在Python中定义函数，可以用必选参数、默认参数、可变参数、关键字参数和命名关键字参数，这5种参数都可以组合使用。但是请注意，参数定义的顺序必须是：必选参数、默认参数、可变参数、命名关键字参数和关键字参数。
```python
def f1(a, b, c=0, *args, **kw):
def f2(a, b, c=0, *, d, **kw):
```

通过一个tuple和dict，你也可以调用上述函数
```python
 args = (1, 2, 3, 4)
>>> kw = {'d': 99, 'x': '#'}
>>> f1(*args, **kw)
a = 1 b = 2 c = 3 args = (4,) kw = {'d': 99, 'x': '#'}
>>> args = (1, 2, 3)
>>> kw = {'d': 88, 'x': '#'}
>>> f2(*args, **kw)
a = 1 b = 2 c = 3 d = 88 kw = {'x': '#'}
```
所以，对于任意函数，都可以通过类似`func(*args, **kw)`的形式调用它，无论它的参数是如何定义的。



### 顺序

参数（位置参数）必须在默认参数和可变参数之前，命名关键字参数必须在关键字参数之前。同时，当混合特定的参数匹配模型时，例如位置参数、关键字参数和*sequence形式的组合，参数在函数调用中的顺序应当遵循：先出现任何位置参数，然后是任何关键字参数，最后是*sequence形式。这种规定可以帮助编程者更好地组织代码，提高代码的可读性和易用性。



## 递归函数

递归函数就是函数调用自身
```python
def f(n):
	if n==1:
		return 1
	return n*f(n-1)
```
使用递归函数需要注意防止栈溢出。在计算机中，函数调用是通过栈（stack）这种数据结构实现的，每当进入一个函数调用，栈就会加一层栈帧，每当函数返回，栈就会减一层栈帧。`栈溢出`就是向栈中写入了超出限定长度的数据，溢出的数据会覆盖栈中其它数据，从而影响程序的运行。所以，递归调用的次数过多，会导致栈溢出

解决递归调用栈溢出的方法是通过**尾递归**优化，事实上尾递归和循环的效果是一样的，所以，把循环看成是一种特殊的尾递归函数也是可以的。



## range()

range函数返回一个range类型的整数序列

```python
range(start,stop,step)
'''
start省略情况为0
stop的值不会输出'''

#只保留stop
range(10) :0,1,2,3,4,5,6,7,8,9
#保留start和stop
range(1,10) :1,2,3,4,5,6,7,8,9
#保留start和stop和步长
range(1,10,2) :1,3,5,7,9
#负数
range(-5,-1) :-5,-4,-3,-2

#注意：range()返回的是range类型，如果要放在容器中，要用list()函数转换成列表
list1=[range(3)]         #range(3)
list2=[list(range(3))]   #0,1,2
```




# 高级特性
## 切片
切片(Slice)操作符可以指定取出的索引范围
`[首索引:末索引:步长]`  (都是向右遍历)

```python
L=['a','b','c']
L[0:3]    # ['a','b','c']  从索引0开始到索引3结束，但不包括索引3
L[:3]     #第一个索引是0，可以省略
L[-2:]    #['b', 'c']
L[0:3:2]  #['a', 'c']  #步长为2，隔两个取一个
```

## 迭代

如果给定一个list或tuple，我们可以通过for循环来遍历这个list或tuple，这种遍历我们称为迭代（Iteration）。
在python中，无论有无下标，只要是可迭代对象，都可以迭代

```python
d = {'a': 1, 'b': 2, 'c': 3}
for key in d:
	print(key)  # a b c 默认输出的是key值
#如果变量要为value值，可以改为：
for value in d.values()
#同时迭代key和value：
for k,v in d.items()
```

判断对象是否能迭代
通过`collections.abc`模块中的`Iterable`类判断
```python
from collections.abc import Iterable
isinstance('abc',Iterable)    #True
isinstance([1,2,3],Iterable)  #True
isinstance(123,Iterable)      #false
```


```python
#对list实现下标循环
for i,v in enumerate(['a','b','c']):
	print(i,v)   #0 a  1 b  2 c
#同时引用两个变量
for x,y in [(1,2),(3,4)]  #1 2   3 4
```


## 列表生成式
列表生成式即List Comprehensions，是Python内置的非常简单却强大的可以用来创建list的生成式。(只能创建list)
`[表达式 循环体 条件语句]`

```python
#生成[1*1,2*2,3*3,...,10*10]的列表
[x*x for x in range(1,11)]
#for后面加if判断，只筛选x是偶数的项
[x*x for x in range(1,11) if x%2==0]
#还可以使用两层循环
[m + n for m in 'ABC' for n in 'XYZ']#['AX', 'AY', 'AZ', 'BX', 'BY', 'BZ', 'CX', 'CY', 'CZ']
#也可以出当前目录下的所有文件和目录名
import os
[d for d in os.listdir('.')]  #os.listdir可以列出文件和目录
#也可以使用两个变量来生成list
d = {'x': 'A', 'y': 'B', 'z': 'C' }
[k + '=' + v for k, v in d.items()] #['y=B', 'x=A', 'z=C']
#最后把一个list中所有的字符串变成小写
L = ['Hello', 'World', 'IBM', 'Apple']
[s.lower() for s in L] #['hello', 'world', 'ibm', 'apple']
```

`注意`：if...else的使用
- 当if在for循环后面时只能有一个if，没有else
- 当if在for循环前面时有if必须加else
```python
#if在循环后面
[x for x in range(1,11) if x%2==0] #if只是一个筛选作用，不能带else
#if在循环前面
[x if x%2==0 else -x for x in range(1,11)]#for循环给了x：1~10的值,x%2==0只判断了偶数，还有其他数字没有判断，那么必须加上else判断其他数字
```

## 迭代器
迭代就是依次遍历对象的所有元素。迭代器是一个可以记住遍历的位置的对象。迭代器对象从集合的第一个元素开始访问，直到所有的元素被访问完结束。迭代器只能往前**不会后退**。
迭代器有两个基本的方法：`iter()` 和 `next()`

```python
list=[1,2,3,4]
it = iter(list)    #  创建迭代器对象
print (next(it))   #1 输出迭代器的下一个元素
print (next(it))   #2
for x in it:
	print(x)       #  迭代器对象也可以使用常规for语句遍历
```
大多数容器对象都可以使用for语句迭代。其实在幕后，for语句会在容器对象上调用iter()。iter()返回了一个包含__next__() 方法的迭代器对象，此方法将逐一访问容器中的元素。当元素用尽时，\_\_next__() 将引发StopIteration 异常来通知终止for 循环。
你可以使用next() 内置函数来调用__next__() 方法

给自己定义的类添加迭代器：定义一个__iter__() 方法来返回一个带有__next__() 方法的对象。如果类已定义了__next__()，则__iter__() 可以简单地返回self:
```python
class Reverse:
	def __init__(self, data):
		self.data = data
		self.index = len(data)
	def __iter__(self):
		return self
	def __next__(self):
		if self.index == 0:
			raise StopIteration
		self.index = self.index - 1
		return self.data[self.index]
```


## 生成器
生成器是一个用于创建迭代器的简单而强大的工具。它们的写法类似于标准的函数，但当它们要返回数据时会使用yield 语句。在 Python 中，使用了`yield`的函数被称为`生成器`（generator）。`yield`是一个关键字，定义了生成器函数(返回迭代器对象)，只能用于迭代操作，生成器就相当于迭代器。生成器在迭代过程中逐步产生值，而不是一次性返回所有结果。
生成器解释：
当在生成器函数中使用 **yield** 语句时，函数的执行将会暂停，并将 **yield** 后面的表达式作为当前迭代的值返回。然后，每次调用生成器的 **next()** 方法或使用 **for** 循环进行迭代时，函数会从上次暂停的地方继续执行，直到再次遇到 **yield** 语句。这样，生成器函数可以逐步产生值，而不需要一次性计算并返回所有结果。

```python
def countdown(n):
    while n > 0:
        yield n
        n -= 1 #没有这语句，n的值将不会发生改变
# 创建生成器对象
generator = countdown(5)
# 通过迭代生成器获取值
print(next(generator))  # 输出: 5
print(next(generator))  # 输出: 4
print(next(generator))  # 输出: 3
# 使用 for 循环迭代生成器
for value in generator:
    print(value)  # 输出: 2 1
```



# 模块

在Python中，一个.py文件就是一个模块(Module)。模块中存放着不同的函数。模块提高了代码的可维护性；避免函数名和变量名冲突，相同的名字可以分别存在不同的模块中。
相同类型的模块被组织为包(Package)，包中存放各种不同的模块
比如包：mycompany
![[Pasted image 20230716105338.png]]
那么abc.py的模块名从abc变为mycompany.abc
包目录下面的`__init__.py`文件是表明这个目录是个包，而不是普通目录

## 使用模块
Python本身就内置了很多非常有用的模块，只要安装完毕，这些模块就可以立刻使用
`import sys` 直接使用sys中的方法
`from urllib import request ` 从urllib模块中只引用request



# OOP

## 类和实例
`class Class_name:`
class后面接类名，类名通常是大写开头的单词

```python
class Student:
	pass
a=Student()  #构造实例
```
	注意：类方法参数必须包含self，且放在第一位

构造方法
`def __init__(self)
`注意`：
- `__init__`方法第一个参数必须是`self`，self就是实例本身，跟java的this作用相同
- 定义了构造方法，就必须传入参数，形参里没有self
```python
class Student:  
    gender='man'  #类属性定义不用self
	def __init__(self,name,age):  
		self.name=name  #在方法中调用属性就必须使用self.
		self.age=age  
a=Student('xia',12) 
```



### 实例属性和类属性

由于Python是动态语言，根据类创建的实例可以任意绑定属性。给实例或类绑定属性可以直接定义变量，也可以使用self
```python
class A(object):
	def __init__(self,x):
		self.x=x
	age=15  #直接在类中定义类属性
a=A(2)
a.x          #2
a.name='xia' #xia   给类绑定一个变量name，属于实例属性
A.c='lang'   #lang  给类绑定一个变量c，属于类属性，类和实例都能访问
A.age        #15
del A.c      #删除类属性  [注意]：类属性只能删除类属性，不能删除a.c通过实例的类属性
```



### 限制实例的属性

可以在类定义一个`__slots__`变量来限制class实例能添加的属性
```python
class A(object):
	__slots__=('name','age') #使用tuple定义只允许绑定的属性名
```
注意：`__slots__`限制作用的范围仅针对当前的类，对继承的子类不起作用，除非在子类也添加



### @property绑定属性

如果想在绑定属性时检查参数就要用set方法，但不免有些繁琐。使用内置的装饰器`@property`，将类中的方法变为属性调用
```python
class A(object):
	@property#'财产'    如果只定义@property，那么只能有'getter'就是只读状态，不能修改属性值
	def score(self):
		return self._score
	
    @score.setter
    def score(self,value):
	    if not isinstance(value,int):
		    raise ValueError('score must be an integer!')
		if value < 0 or value > 100:
            raise ValueError('score must between 0 ~ 100!')
	    self._score=value
a=A()
a.score=60       #实际转换为了a.set_score(60)
>>>a.score#60     实际转换为了a.get_score()
```
`注意`：**属性的方法名不要和实例变量重名**
```python
class Student(object):
    # 方法名称和实例变量均为birth:
    @property
    def birth(self):
        return self.birth
#这是因为调用s.birth时，首先转换为方法调用，在执行return self.birth时，又视为访问self的属性，于是又转换为方法调用，造成无限递归，最终导致栈溢出报错RecursionError。    
```



### 实例方法和类方法

```python
class A(object):
	pass
a=A()
def set_age(self,age)
	self.age=age
from types import MethodType  #使用MethodType给实例绑定方法
a.set_age=MethodType(set_age,s)
A.set_age=set_age             #给类绑定方法
```



### 数据封装

通过在类中定义方法去访问类变量，就不用在类外部访问变量，相当于把“数据”封装起来了
```python
class Student:  
	def __init__(self,name,age):  
		self.name=name  
		self.age=age 
	def print(self):
		print(self.name,self.age)
a=Student('xia',12) 
a.print  # xia 12  直接调用方法，不用访问类中的变量
```
`注意`：如果类中要使用实例变量，就必须使用self参数




### 访问限制
在类中直接定义一个变量，在外部调用时是可以修改的，那么可以在变量名前增加`__`声明私有变量(private),那么就不能再修改了，且不能通过模块导入
```python
class Student:  
	def __init__(self,name,age):  
		self.__name=name  #声明为私有变量
		self.age=age 
	def get_name(self):   #定义get_name(self)方法获取私有属性
		return self.__name
	def set_name(self,name): #定义set_name(self)方法修改私有属性
		self.__name=name #set方法中，可以对参数做检查，避免传入无效参数
```

[__和_].(https://blog.csdn.net/oldboyedu1/article/details/129535148?ops_request_misc=&request_id=&biz_id=102&utm_term=python%20_&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-129535148.nonecase&spm=1018.2226.3001.4187).



## 继承和多态
Python中的父类直接在子类后面用()括起来
`class 子类(父类)`
继承父类的子类可以获得父类全部属性方法
```python
class Animal(Object):
	def run(self):
		print('Animal is running...')
class Cat(Animal):
	pass
class Dog(Animal):
	def run(self):
		def run(self): #方法覆盖
			print('Dog is running...')
	pass
dog=Dog()
dog.run() #Dog is running...
#class也是一个数据类型，不过是我们自定义的。
isinstance(dog,Animal)  #True
isinstance(dog,Dog)     #True
```



### 静态语言和动态语言的区别

对于静态语言（例如Java）来说，如果需要传入`Animal`类型，则传入的对象必须是`Animal`类型或者它的子类，否则，将无法调用`run()`方法。
于Python这样的动态语言来说，则不一定需要传入`Animal`类型。我们只需要保证传入的对象有一个`run()`方法就可以了




### 多重继承
Python是支持多继承的，跟Java的单继承不同。通过多继承实现更多的功能
```python
class Dog(Mammal, Runnable):#Dog就继承了Mammal和Runnable两个类
    pass
```
但是在设计类的继承关系时，通常是单一继承下来。如果要'混入'额外的功能，就可以多重继承下来。这种设计方式称为`MixIn`。MixIn目的就是给一个类增加多个功能，且能更好看出继承关系。所以，在设计类的时候优先考虑通过多重继承来组合多个MixIn的功能，而不是复杂的多继承关系
```python
#比如Animal中，分出肉食动物CarnivorousMixIn和植食动物HerbivoresMixIn，分出跑步RunnableMixIn和飞行FlyableMixIn
class Dog(Mammal,RunnableMixIn,CarnivorousMixIn)：
	pass
```
Python自带的很多库也使用了MixIn。比如Python自带了`TCPServer`和`UDPServer`这两类网络服务，而要同时服务多个用户就必须使用多进程或多线程模型，这两种模型由`ForkingMixIn`和`ThreadingMixIn`提供。通过组合，我们就可以创造出合适的服务来。



## 获取对象信息
### type()
```python
#判断基本数据类型
type(123)    #<class 'int'>
type('abc')  #<class 'str'>
type(None)   #<class 'NoneType'>
type(abs)    #<class 'builtin_function_or_method'>
type(a)      #<class '__main__.Animal'>  a是Animal的实例
```
`type()`返回的是`class`类型，如果想用`if`判断，就需要比较他们的type类型是否相等
```python
type(123)==type(435)       #True
type('abc')==type('sfd')   #True
type('abc')==str           #True
```
```python
#判断函数
import types #使用types模块中的常量
type f(): 
type(f())==type.FunctionType         #True
type(abs)==type.BuiltinFunctionType  #True
type(lambda x: x)==types.LambdaType  #True
type((x for x in range(10)))==types.GeneratorType  #True
```

### isinstance()
对于class的继承关系来说，使用type()就很不方便。判断class类型就可以用`isinstance()`函数
```python
class Animal
class Dog(Animal)
class Coco(Dog)
isinstance(coco,Animal)  #True 
isinstance(coco,Dog)     #True
isinstance(coco,Coco)    #True
#判断基本数据类型
isinstance('a',str)      #True
isinstance(123,int)      #True
isinstance(b'a',bytes)   #True
#判断变量是否是某些类型的一种
isinstance([1,2,3],(list,tuple)) #True  是否是list或tuple中的一种
isinstance({'a':1},(list,tuple)) #False
```

### dir()
如果要获得一个对象的所有属性和方法，可以使用`dir()`函数，返回字符串的list
```python
dir('abc')
#['__add__', '__class__',..., '__subclasshook__', 'capitalize', 'casefold',..., 'zfill']
```
类似`__xxx__`的属性和方法在Python中都是有特殊用途的，比如`__len__`方法返回长度。在Python中，如果你调用`len()`函数试图获取一个对象的长度，实际上，在`len()`函数内部，它自动去调用该对象的`__len__()`方法，所以，下面的代码是等价的：
```python
len('ABC')       #3
'ABC'.__len__()  #3
```

那么我们可以引申出自定义类使用len()函数
```python
class Dog(object):
	def __len__(self):
		return 100
d=Dog()
len(d)  #100  也就是d.__len__()
```

### xxxattr()

获取对象的状态
`getattr()`、`setattr()`以及`hasattr()`
```python
class Animal(object):
	def __init__(self):
		self.name='animal'
a=Animal()
print(hasattr(a,'__init__'))  #True  判断是否有方法
hasattr(a,'name')  #True  判断是否有属性
hasattr(a,'x')     #False
setattr(a,'y',10)  #设置一个变量'y'=10
getattr(a,'y')     #获取属性'y' out:10
getattr(a,'z',404) #获取属性'z'，如果不存在就返回404
```

## 特殊方法

`__`双下划线开头和结尾的特殊方法被称为"魔术方法"或"特殊方法"，含有特定的功能，例如`__init__`方法是构造函数，它在生成对象时被调用；`__del__`是析构函数，它在释放对象时使用。特殊方法是一种内置函数，相当于对象的属性，可以通过`对象.方法()`调用。例如，`__len__`就是一个特殊方法，当我们对一个对象使用`len()`函数时，实际上调用的就是该对象的`__len__`方法。

虽然特殊方法是内置的，但我们可以根据需要自定义自己的特殊方法。例如，我们可以定义`__str__`方法来指定当我们打印类的实例时返回什么信息。



### \_\_str__



### \_\_iter__



### \_\_getitem__



### \_\_getattr__



### \_\_call__





## 枚举类
定义大量常量时，可以在类中直接定义类属性，但是并不严谨，也不怎么安全。那我们可以使用`Enum类`实现枚举
```python
class color():
    YELLOW  = 1
    YELLOW  = 3   # 注意这里又将YELLOW赋值为3，会覆盖前面的1
    RED     = 2
    GREEN   = 3
    PINK    = 4
# 可以在外部修改定义的枚举项的值，这是不应该发生的
color.YELLOW = 99
print(color.YELLOW) # 99
#--------------------------------------
#使用Enum类枚举
from enum import Enum,unique
@unique    #@unique装饰器可以检查保证没有重复的key
class color(Enum):
    YELLOW  = 1
    BEOWN   = 1 
    # 注意BROWN的值和YELLOW的值相同，这是允许的，此时的BROWN相当于YELLOW的别名
    RED     = 2
    GREEN   = 3
    PINK    = 4
>>>color.YELLOW       #color.YELLOW 访问YELLOW项 
>>>color.YELLOW.value #1
>>>color.YELLOW=2     #AttributeError('Cannot reassign members.')不能在外面修改值
#-------------------------------
#另一种枚举类定义方式
Month=Enum('Month',('Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'))
>>>Month.Jan       #Month.Jan
>>>Month.Jan.value #1
#语句说明：创建一个Enum类名为Month，后面tuple是里面的常量，且第一个定义为1，后面按顺序依次2,3...
#--------------------------------
#遍历枚举类
for name, member in Month.__members__.items():
    print(name, '=>', member, ',', member.value)
>>>Jan => Month.Jan , 1
>>>Feb => Month.Feb , 2
```
注意：
- 导入Enum之后，一个枚举类中的Key和Value，Key不能相同，Value可以相，但是Value相同的各项Key都会当做别名
- 写成class类型就必须自己定义常量值，按语句的话会自动按1往后赋值


## 元类





## 装饰器

在Python编程语言中，装饰器是一种可以用于改变其他函数或类的功能的特殊类型的函数。它们的主要作用是在代码执行前后对函数、方法、类等进行一些额外的操作或者扩展，而且不需要修改原有函数的源代码和调用方式。

Python的标准库中已经定义了一些常用的装饰器，比如`@lru_cache`。此装饰器来自functools模块，非常易于使用，主要用于加速函数的连续运行，通过使用缓存技术来提高性能。此外，社区也有很多第三方库提供了各种各样的装饰器。

工作原理：首先定义一个装饰器函数，这个函数接受一个函数作为参数；然后在这个装饰器函数内部再定义一个包装函数，这个包装函数会调用传入的函数，并在调用前后添加一些额外的操作；最后，装饰器函数返回这个包装函数。

总的来说，Python的装饰器是一个非常强大的功能，它可以让代码更简短、更Pythonic，同时还能增加程序的灵活性和可复用性



### @property

@property是一个特殊的装饰器，其主要功能是将一个方法转变为属性，使得这个方法可以在不需要加括号的情况下被调用。这样，我们可以像访问属性一样访问这个方法，而不用将其视为一个独立的函数调用。

```python
class Person:
    @property
    def f(self):
        print('hello')
p=Person()
p.f       #hello   
```







# 错误

在程序运行过程中，总会遇到各种各样的错误。有的错误是程序编写有问题造成的，比如本来应该输出整数结果输出了字符串，这种错误我们通常称之为bug，bug是必须修复的。有的错误是用户输入造成的，比如让用户输入email地址，结果得到一个空字符串，这种错误可以通过检查用户输入来做相应的处理。还有一类错误是完全无法在程序运行过程中预测的，比如写入文件的时候，磁盘满了，写不进去了，或者从网络抓取数据，网络突然断掉了。
错误也称为异常，在程序中通常是必须处理的，否则，程序会因为各种问题终止并退出。

## 错误处理
`try...except..finally`错误处理机制

```python
try:
    print('try...')
    r = 10 / 0
    print('result:', r)   #上句直接跳转到错误处理，此句没有执行
except ZeroDivisionError as e:
    print('except:', e)
else:
	print('no error!')  #当没有错误发生时，自动执行else语句
finally:        #有finally就执行，且无论有没有错误都会执行
    print('finally...')
print('END')
'''out:
try...
except: division by zero
finally...
END
'''
```


Python的错误其实也是class，所有的错误类型都继承自`BaseException`，所以在使用`except`时需要注意的是，它不但捕获该类型的错误，还把其子类也“一网打尽”。比如：
```python
except ValueError as e:
    print('ValueError')
except UnicodeError as e:
    print('UnicodeError')
```
第二个except永远也捕获不到UnicodeError，因为UnicodeError是ValueError的子类，如果有，也被第一个except给捕获了。
Python所有的错误都是从`BaseException`类派生的，常见的错误类型和继承关系看这里：[错误继承].(https://docs.python.org/3/library/exceptions.html#exception-hierarchy)


使用`try...except`捕获错误还有一个巨大的好处，就是可以跨越多层调用，比如函数`main()`调用`bar()`，`bar()`调用`foo()`，结果`foo()`出错了，这时，只要`main()`捕获到了，就可以处理
```python
def foo(s):
    return 10 / int(s)

def bar(s):
    return foo(s) * 2

def main():
    try:
        bar('0')
    except Exception as e:
        print('Error:', e)
    finally:
        print('finally...')
```
也就是说，不需要在每个可能出错的地方去捕获错误，只要在合适的层次去捕获错误就可以了。

## 调用栈
如果错误没有被捕获，它就会一直往上抛，最后被Python解释器捕获，打印一个错误信息，然后程序退出。然后根据调用栈信息分析出错原因：
```python
def foo(s):
    return 10 / int(s) #这里出错

def bar(s):
    return foo(s) * 2

def main():
    bar('0')

main()
#程序在foo(s)出错，因为没有捕获错误，就会抛向bar(s)，再抛向main()，一直向上抛
#------------------------------
#Python抛出的错误信息：
Traceback (most recent call last):   #告诉我们这是错误的跟踪信息。
  File "err.py", line 11, in <module>#第11行的main()出错，原因是下面内容
    main()
  File "err.py", line 9, in main     #第9行的bar()出错，原因是下面内容
    bar('0')
  File "err.py", line 6, in bar
    return foo(s) * 2
  File "err.py", line 3, in foo

```


## 抛出错误
因为错误是class，捕获一个错误就是捕获到该class的一个实例。因此，错误并不是凭空产生的，而是有意创建并抛出的。Python的内置函数会抛出很多类型的错误，我们自己编写的函数也可以抛出`raise`错误
```python
class FooError(ValueError):
    pass

def foo(s):
    n = int(s)
    if n==0:
        raise FooError('invalid value: %s' % s) #抛出自己定义的错误
    return 10 / n

foo('0')
```

混合错误处理


```python
#捕获之后再抛出
def foo(s):
    n = int(s)
    if n==0:
        raise ValueError('invalid value: %s' % s)
    return 10 / n

def bar():
    try:
        foo('0')
    except ValueError as e:
        print('ValueError!')
        raise   #raise去了就只有ValueError！

bar()
#foo()出错，被捕获打印一个'ValueError!'，又把错误raise出去
#raise语句如果不带参数，就会把当前错误原样抛出
#-------------------------------------
#捕获后抛出其他类型错误
try:
    10 / 0
except ZeroDivisionError:
    raise ValueError('input error!') #错误类型改变
```


## 调试
程序能一次写完并正常运行的概率很小，那我们在出错时要知道哪些变量出错，因此需要一整套调试程序的手段来修复bug
### print
用`print()`把可能有问题的变量打印出来看看
```python
def foo(s):
    n = int(s)
    print('>>> n = %d' % n)
    return 10 / n

def main():
    foo('0')

main()
```

### assert
用print()最大的坏处是将来还得删掉它，且运行时很多垃圾信息。可以用`assert断言`来替代
```python
def foo(s):
    n = int(s)
    assert n != 0, 'n is zero!'
    return 10 / n

def main():
    foo('0')

main()
```
`assert`意思是后面的表达式(n!=0)一定是正确的，否则程序抛出`AssertionError`:'n is zero!'
也可以关闭assert：`python -O 文件名.py`,asser语句就会当做pass（参数是字母 O）

### logging
`logging`不会抛出错误，而且可以输出到文件

```python
import logging
logging.basicConfig(level=logging.INFO)

s = '0'
n = int(s)
logging.info('n = %d' % n)
print(10 / n)
'''
INFO:root:n = 0
Traceback (most recent call last):
  File "err.py", line 8, in <module>
    print(10 / n)
ZeroDivisionError: division by zero
'''
```
这就是`logging`的好处，它允许你指定记录信息的级别，有`debug`，`info`，`warning`，`error`等几个级别，当我们指定`level=INFO`时，`logging.debug`就不起作用了。同理，指定`level=WARNING`后，`debug`和`info`就不起作用了。这样一来，你可以放心地输出不同级别的信息，也不用删除，最后统一控制输出哪个级别的信息。
`logging`的另一个好处是通过简单的配置，一条语句可以同时输出到不同的地方，比如console和文件。

## IDE
置断点、单步执行

## 单元测试

## 文档测试


# IO
IO在计算机中指Input/Output，也就是输入和输出。由于程序和运行时数据是在内存中驻留，由CPU这个超快的计算核心来执行，涉及到数据交换的地方，通常是磁盘、网络等，就需要IO接口。

## 文件读写

在磁盘上读写文件的功能都是由操作系统提供的，现代操作系统不允许普通的程序直接操作磁盘，所以，读写文件就是请求操作系统打开一个文件对象（通常称为文件描述符），然后，通过操作系统提供的接口从这个文件对象中读取数据（读文件），或者把数据写入这个文件对象（写文件）

### open()
`open()`方法用于打开一个文件，并返回文件对象。在对文件进行处理过程都需要使用到这个函数，如果该文件无法被打开，会抛出`OSError`
`注意`：使用 open() 方法一定要保证关闭文件对象，即调用 close() 方法。
open() 函数常用形式是接收两个参数：文件名(file)和模式(mode)。
`open(file, mode='r')`    一般最常用的是前两个参数
完整形式：open(file, mode='r', buffering=-1, encoding=None, errors=None, newline=None, closefd=True, opener=None)
参数说明：

- file: 必需，文件路径（相对或者绝对路径）。
- mode: 可选，文件打开模式
- buffering: 设置缓冲
- encoding: 编码格式，一般使用utf8
- errors: 报错级别
- newline: 区分换行符
- closefd: 传入的file参数类型
- opener: 设置自定义开启器，开启器的返回值必须是一个打开的文件描述符

`mode参数`：  

| 模式 | 描述                                                                                                                                                               |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| t    | 文本模式 (默认)。                                                                                                                                                  |
| x    | 写模式，新建一个文件，如果该文件已存在则会报错。                                                                                                                   |
| b    | 二进制模式。                                                                                                                                                       |
| +    | 打开一个文件进行更新(可读可写)。                                                                                                                                   |
| U    | 通用换行模式（**Python 3 不支持**）。                                                                                                                              |
| r    | 以只读方式打开文件。文件的指针将会放在文件的开头。这是默认模式。                                                                                                   |
| rb   | 以二进制格式打开一个文件用于只读。文件指针将会放在文件的开头。这是默认模式。一般用于非文本文件如图片等。                                                           |
| r+   | 打开一个文件用于读写。文件指针将会放在文件的开头。                                                                                                                 |
| rb+  | 以二进制格式打开一个文件用于读写。文件指针将会放在文件的开头。一般用于非文本文件如图片等。                                                                         |
| w    | 打开一个文件只用于写入。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。                                           |
| wb   | 以二进制格式打开一个文件只用于写入。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。一般用于非文本文件如图片等。   |
| w+   | 打开一个文件用于读写。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。                                             |
| wb+  | 以二进制格式打开一个文件用于读写。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。一般用于非文本文件如图片等。     |
| a    | 打开一个文件用于追加。如果该文件已存在，文件指针将会放在文件的结尾。也就是说，新的内容将会被写入到已有内容之后。如果该文件不存在，创建新文件进行写入。             |
| ab   | 以二进制格式打开一个文件用于追加。如果该文件已存在，文件指针将会放在文件的结尾。也就是说，新的内容将会被写入到已有内容之后。如果该文件不存在，创建新文件进行写入。 |
| a+   | 打开一个文件用于读写。如果该文件已存在，文件指针将会放在文件的结尾。文件打开时会是追加模式。如果该文件不存在，创建新文件用于读写。                                 |
| ab+  | 以二进制格式打开一个文件用于追加。如果该文件已存在，文件指针将会放在文件的结尾。如果该文件不存在，创建新文件用于读写。                                             |

默认为文本模式，如果要以二进制模式打开，加上 b 。

```python
f=open('/Users/test.txt','r')  #只读方式打开文件
#如果文件不存在，open()函数就会抛出一个IOError的错误
f.read()   #文件成功打开，接下来调用read()方法读取内容
f.close()  #最后关闭文件。文件使用完毕后必须关闭，因为文件对象会占用操作系统的资源，并且操作系统同一时间能打开的文件数量也是有限的
```

使用
由于文件读写时都有可能产生`IOError`，一旦出错，后面的`f.close()`就不会调用。所以，为了保证无论是否出错都能正确地关闭文件，我们可以使用`try ... finally`来实现

```python
try:
    f = open('/path/to/file', 'r')
    print(f.read())
finally:
    if f:
        f.close()
```

但是每次都这么写实在太繁琐，所以，Python引入了`with`语句来自动帮我们调用`close()`方法：
```python
with open('/path/to/file', 'r') as f:
    print(f.read())
```
这和前面的`try ... finally`是一样的，但是代码更佳简洁，并且不必调用`f.close()`方法。

调用`read()`会一次性读取文件的全部内容，如果文件有10G，内存就爆了，所以，要保险起见，可以反复调用`read(size)`方法，每次最多读取size个字节的内容。另外，调用`readline()`可以每次读取一行内容，调用`readlines()`一次读取所有内容并按行返回`list`。因此，要根据需要决定怎么调用。

如果文件很小，`read()`一次性读取最方便；如果不能确定文件大小，反复调用`read(size)`比较保险；如果是配置文件，调用`readlines()`最方便：
```python
for line in f.readlines():
    print(line.strip()) # 把末尾的'\n'删掉
```


其他参数的使用
```python
 f = open('/Users/michael/gbk.txt', 'r', encoding='gbk', errors='ignore')
```

写文件
写文件和读文件是一样的，唯一区别是调用`open()`函数时，传入标识符`'w'`或者`'wb'`表示写文本文件或写二进制文件：

```python
f = open('/Users/michael/test.txt', 'w')
f.write('Hello, world!')
f.close()
```
你可以反复调用`write()`来写入文件，但是务必要调用`f.close()`来关闭文件。当我们写文件时，操作系统往往不会立刻把数据写入磁盘，而是放到内存缓存起来，空闲的时候再慢慢写入。只有调用`close()`方法时，操作系统才保证把没有写入的数据全部写入磁盘。忘记调用`close()`的后果是数据可能只写了一部分到磁盘，剩下的丢失了所以，还是用`with`语句来得保险：
```python
with open('/Users/michael/test.txt', 'w') as f:
    f.write('Hello, world!')
```
`注意`：`w`模式会直接覆盖原先文件内容，如果要追加写就使用`a`参数



```python
#找出文本文件中出现频率最高的单词。
with open(file_path,'r') as file:
    text = file.read()
words = text.split() #string.split()会将字符串按空格字符分隔出单个的单词，都存放到一个列表中
word_counts={}
for word in words:
    if word in word_counts:
        word_counts[word] += 1#如果存在在字典中，就次数加一
    else:
        word_counts[word] = 1#如果不存在，就在字典中加入这个键并赋予1
max_word = max(word_counts,key = word_counts.get) #max()找出容器中的最大值.max(dict,key=dict.get) dict表示是一个字典，dict.get表示比较的是字典的值.注意，第二个参数必须为key=...

```





## StringIO和BytesIO
### StringIO
很多时候，数据读写不一定是文件，也可以在内存中读写。`StringIO`就是在内存中读写str
```python
from io import StringIO
f = StringIO()
f.write('hello')    #5
f.write(' ')        #1
f.write('world!')   #6
print(f.getvalue()) #hello world!
```
读取StringIO，跟文件读取一样
```python
from io import StringIO
f = StringIO('Hello!\nHi!\nGoodbye!')
while True:
	s = f.readline()
		if s == '':
			break
			print(s.strip())
'''
Hello!
Hi!
Goodbye!
```

### BytesIO
StringIO操作的只能是str，如果要操作二进制数据，就需要使用BytesIO。
```python
from io import BytesIO
f = BytesIO()
f.write('中文'.encode('utf-8'))#6
print(f.getvalue())#b'\xe4\xb8\xad\xe6\x96\x87'
#注意：写入的不是str，而是经过UTF-8编码的bytes
```
和StringIO类似，像读文件一样读取：
```python
from io import BytesIO
f = BytesIO(b'\xe4\xb8\xad\xe6\x96\x87')
f.read() #b'\xe4\xb8\xad\xe6\x96\x87'
```

## 操作文件和目录
如果要操作文件、目录，可以在命令行下面输入OS提供的各种命令来完成。这些命令也只是简单调用了OS提供的接口函数。Python内置的`os`模块也可以直接调用操作系统提供的接口函数。
```python
>>>import os
>>>os.name #'nt'(操作系统类型)  'nt'是windows，'posix'是Unix,Linux,MaxOs
>>>os.uname()#详细系统类型 与platform.uname()作用相同，os的win上用不了
>>>os.environ #存放OS中定义的环境变量
>>>os.environ.get('key') #获取某个环境变量的值
```
操作文件和目录的函数一部分放在`os`模块中，一部分放在`os.path`模块中。


```python
# 查看当前目录的绝对路径:
>>> os.path.abspath('.')
'/Users/michael'
# 在某个目录下创建一个新目录，首先把新目录的完整路径表示出来:
>>> os.path.join('/Users/michael', 'testdir')
'/Users/michael/testdir'
# 创建一个目录:
>>> os.mkdir('/Users/michael/testdir')
# 删掉一个目录:
>>> os.rmdir('/Users/michael/testdir')
# 拆分路径
>>>os.path.split('/Users/michael/testdir/file.txt')
('/Users/michael/testdir', 'file.txt')
# 拆分路径（可以直接得到文件扩展名）
>>> os.path.splitext('/path/to/file.txt')
('/path/to/file', '.txt')
# 对文件重命名:
>>> os.rename('test.txt', 'test.py')
# 删掉文件:
>>> os.remove('test.py')
# 筛选文件，列出当前目录下的所有目录
>>> [x for x in os.listdir('.') if os.path.isdir(x)]
# 列出所有的.py文件
>>> [x for x in os.listdir('.') if os.path.isfile(x) and os.path.splitext(x)[1]=='.py']
```
复制文件的函数在`os`模块中不存在！原因是复制文件并非由操作系统提供的系统调用。但`shutil`模块提供了`copyfile()`的函数，你还可以在`shutil`模块中找到很多实用函数，它们可以看做是`os`模块的补充。

## 序列化
把变量从内存中变成可存储或传输的过程称之为`序列化`(pickling)，序列化之后，就可以把序列化后的内容写入磁盘，或者通过网络传输到别的机器上。反过来，把变量内容从序列化的对象重新读到内存里称之为`反序列化`(unpickling)
通过Python内置模块`pickle`来实现序列化
```python
import pickle
d = dict(name='Bob', age=20, score=88)
pickle.dumps(d)  #dump()方法吧任意对象序列化成一个bytes，然后把这个bytes写入文件
#或用另一个方法pickle.dump()直接把对象序列化后写入一个file-like Object
f = open('dump.txt', 'wb')
pickle.dump(d, f)
f.close()
```
同样`pickle`实现反序列化：
```python
import pickle
dic = {"k1":"v1","k2":123}
s = pickle.dumps(dic)
dic2 = pickle.loads(s) #内容读到一个bytes直接反序列化出
>>>dic2    #{'k1': 'v1', 'k2': 123}
#直接pickle.load()从一个file-like Object中反序列化出对象
f = open('dump.txt', 'rb')
d = pickle.load(f)
f.close()
>>> d
{'age': 20, 'score': 88, 'name': 'Bob'}
```

### JSON
如果我们要在不同的编程语言之间传递对象，就必须把对象序列化为标准格式。最好的方法是序列化为JSON，因为JSON表示出来就是一个字符串，可以被所有语言读取，也可以方便地存储到磁盘或者通过网络传输。JSON不仅是标准格式，并且比XML更快，而且可以直接在Web页面中读取，非常方便。

JSON表示的对象就是标准的JavaScript语言的对象，JSON和Python内置的数据类型对应如下：

|JSON类型|Python类型|
|---|---|
|{}|dict|
|[]|list|
|"string"|str|
|1234.56|int或float|
|true/false|True/False|
|null|None|

Python内置的`json`模块提供了非常完善的Python对象到JSON格式的转换。我们先看看如何把Python对象变成一个JSON：
```python
>>> import json
>>> d = dict(name='Bob', age=20, score=88)
>>> json.dumps(d)
'{"age": 20, "score": 88, "name": "Bob"}'
```
`dumps()`方法返回一个`str`，内容就是标准的JSON。类似的，`dump()`方法可以直接把JSON写入一个`file-like Object`。
要把JSON反序列化为Python对象，用`loads()`或者对应的`load()`方法，前者把JSON的字符串反序列化，后者从`file-like Object`中读取字符串并反序列化：
```python
>>> json_str = '{"age": 20, "score": 88, "name": "Bob"}'
>>> json.loads(json_str)
{'age': 20, 'score': 88, 'name': 'Bob'}
```
由于JSON标准规定JSON编码是UTF-8，所以我们总是能正确地在Python的`str`与JSON的字符串之间转换。


# 进程和线程



# 数据分析

## numpy

​	NumPy，全称为Numerical Python，是Python的一个扩展程序库。它主要支持大量的维度数组与矩阵运算，并提供了大量的数学函数库以便于进行数学运算。

​	NumPy的核心是ndarray对象，也被称为array。在Python中，我们通常所说的"数组"，实际上是列表(list)和元组(tuple)。列表是Python的内置数据类型，它是一种有序的集合，可以随时添加和删除其中的元素。元组与列表类似，但是元素不能修改。请注意，虽然这两种数据结构在某种程度上类似于其他编程语言中的数组，但它们并不完全相同。比如，数组在Java，C / C ++，JavaScript等大多数编程语言中都很流行，它们可以包含任何类型的数据，并且每个元素都有一个唯一的索引。但在Python中，list中的数据类型不必相同，而元组中的所有元素类型必须完全相同。



### 快速入门

### 创建数组

```python
#使用列表或元组创建数组
a=np.array([2,3,4])
>>>[2,3,4]
dtype(a)    #数组的类型是从里面的元素类型推断出来的
>>>int32
#-----常见错误
np.array(2,3,4) #直接将元素传进函数参数，而函数一般只有1、2个位置参数

#二维数组，多维数组依此类推
np.array([[1,2,3],[3,4,5]]) #注意：二维数组应该在[]里面，[]用[]、()都是一样的
>>>[[1 2 3]
 [3 4 5]]

#显示指定数组里的数据类型
np.array([1,2,3],dtype=complex) #dtype参数在创建数组时都适用
>>>[1.+0.j 2.+0.j 3.+0.j]  #注意：默认情况下类型是float64，所以有的数字后面有个.

#函数创建
np.ones([2,3])
>>>[[1. 1. 1.]
 [1. 1. 1.]]
np.zeros([2,3])
>>>[[0. 0. 0.]
 [0. 0. 0.]]
np.empty([2,3])  #创建一个给定形状的新数组，但不初始化数组元素
>>>[[0. 0. 0.]
 [0. 0. 0.]]
np.arange(1,10) #用法跟range函数一样
>>>[1,2,3,4,5,6,7,8,9]
#注意：当arange与浮点参数一起使用时，由于浮点精度有限，通常无法预测获得的元素数量。因此，通常最好使用linspace获得数组
np.linspace(0,2,9)
>>>[0.   0.25 0.5  0.75 1.   1.25 1.5  1.75 2.  ] #在0到2之间生成9个等间距的数
```



### 打印矩阵

```python
np.arange(6) #一维数组
>>>[0 1 2 3 4 5]
np.arange(12).reshape(4, 3) #二维矩阵
>>>[[ 0  1  2]
 [ 3  4  5]
 [ 6  7  8]
 [ 9 10 11]]
np.arange(24).reshape(2, 3, 4) #三维矩阵列表
>>>[[[ 0  1  2  3]
  [ 4  5  6  7]
  [ 8  9 10 11]]

 [[12 13 14 15]
  [16 17 18 19]
  [20 21 22 23]]]

#如果数组太大而无法打印，会自动跳过中心部分
np.arange(10000) 
>>>[   0    1    2 ... 9997 9998 9999]
#也可以设置强制打印：np.set_printoptions(threshold=sys.maxsize)
```



### 基本操作

```python
a=np.array([0,1,2,3])
b=np.array([4,5,6,7])
a+b
>>>[4,6,8,10]
b**2
>>>[16 25 36 49]
b<5
>>>[ True False False False]

#多维矩阵
A = np.array([[1, 1],
              [0, 1]])
B = np.array([[2, 0],
              [3, 4]])
A * B
>>>array([[2, 0],
       [0, 4]])
A @ B / A.dot(B) #矩阵点乘
>>>array([[5, 4],
       [3, 4]])

#数组的自加自减
a=np.array([0,1,2]) #dtype:int32
b=np.array([1.1,2.1,3.1]) #dtype:float64
a*3
>>>[0 3 6]
b+=a
>>>[1.1 5.1 9.1] #向上转换，转换成内存更大的类型

a+=b #注意：这个是错误的。 因为a数组只能放int类型，b数组不能自动转型，而且float大于int，所以不能加

#指定行、列
a=np.arange(12).reshape(3,4)
>>>[[ 0  1  2  3]
    [ 4  5  6  7]
    [ 8  9 10 11]]
a.sum(axis=0) #axis=0表示每列运算
>>>[12 15 18 21]
a.sum(axis=1) #axis=1表示每行运算
>>>[ 6 22 38]
```



### 通用函数ufunc

```python
```



### 索引、切片和迭代

```python
a=np.arange(5) #[0,1,2,3,4]
a[1] #索引跟数组一样
>>>1
a[start:stop:step] #stop下标不访问
a[::-1]  #步长可以为负数，即反转遍历
>>>[4 3 2 1 0]

#二维数组的遍历
def f(x, y):
    return 10 * x + y
b = np.fromfunction(f, (5, 4), dtype=int)
>>>[[ 0,  1,  2,  3],
    [10, 11, 12, 13],
    [20, 21, 22, 23],
    [30, 31, 32, 33],
    [40, 41, 42, 43]]
b[2,3] / b[2][3]
>>>23
b[行,列]
b[0:5, 1] #0~5行，第2列
>>>[ 1, 11, 21, 31, 41] #第二列的元素
b[:,1]
>>>[ 1, 11, 21, 31, 41] #第二列的元素
b[1:3, :] 
>>>[[10, 11, 12, 13],
    [20, 21, 22, 23]]
b[-1] #b[-1]->b[-1,:]  如果索引不完整，会自动补齐成完整的索引
>>>[40, 41, 42, 43]
#当有多个维度/轴的数组时，用...表示全选的轴
a[1,2,...] -> a[1,2,:,:,:] #5维的数组，...表示省略
a[1,...,3,:] -> a[1,:,:,3,:]

#数组迭代
a=np.arange(12).reshape(3,4)
print(a)  #直接用print是输出对象
>>>[[ 0  1  2  3]
 [ 4  5  6  7]
 [ 8  9 10 11]]
for x in a:  #for遍历是输出数组里的元素，没有[]
    print(x)
>>>[0 1 2 3]
[4 5 6 7]
[8 9 10 11]
for x in a.flat: #flat是直接把元素单个拿出来，完全没有[]
    print(x)
>>>0 1 2 3 4 ...
```



### 操控形状

```python
#以下三个命令均返回修改后的数组，但不会更改原始数组
a=np.arange(12).reshape(3,4)
a.ravel() #将多维数组转换为一维数组
>>>[ 0  1  2  3  4  5  6  7  8  9 10 11]
a.reshape(4,3) #reshape(3,-1) 参数为-1，则列会自动计算尺寸
>>>[[ 0  1  2]
    [ 3  4  5]
    [ 6  7  8]
    [ 9 10 11]]
a.T  #行列倒转
>>>[[ 0  4  8]
    [ 1  5  9]
    [ 2  6 10]
    [ 3  7 11]]

#resize修改本身
a=np.arange(12).reshape(3,4)
a=resize(4,3)
a
>>>[[ 0  1  2]
    [ 3  4  5]
    [ 6  7  8]
    [ 9 10 11]]
```







## pandas

jupyter notebook进入

<img src="D:\NOTES\zattachment\image-20231101221639384.png" alt="image-20231101221639384" style="zoom:67%;" />

<img src="D:\NOTES\zattachment\image-20231029165859247.png" alt="image-20231029165859247" style="zoom: 50%;" />



pandas基本数据结构有 Series：一维数组,DataFrame：二维数据类型

### 基本操作

```python
# 读取数据
data = pd.read_csv("./ttt.csv")
#read_csv   读取纯文本文件，比如csv,txt
#read_excel 读取xlsx文件
#read_mysql 读取MySQL文件
pvuv = pd.read_csv(
    fpath,
    sep="\t",     #列的分隔符
    header=None,  #没有标题行
    names=['pdate', 'pv', 'uv'] #自己设置列名
)
>>> pdate	    pv	uv
0	2019-09-10	139	92
1	2019-09-09	185	153
2	2019-09-08	123	59

conn = pymysql.connect(
        host='127.0.0.1',
        user='root',
        password='12345678',
        database='test',
        charset='utf8'
    )
mysql_page = pd.read_sql("select * from crazyant_pvuv", con=conn)#数据库的链接connection

# 查看前几行数据
data.head()
>>>userId	movieId	rating	timestamp
	0	1	1	4.0	964982703
	1	1	3	4.0	964981247
	2	1	6	4.0	964982224
	3	1	47	5.0	964983815
	4	1	50	5.0	964982931

# 查看数据的形状
data.shape
>>>(100, 4)
# 查看列名列表
data.columns 
>>>Index(['userId', 'movieId', 'rating', 'timestamp'], dtype='object')
# 查看索引列
data.index
>>>RangeIndex(start=0, stop=100, step=1)
# 查看每列的数据类型
data.dtypes
>>> userId         int64
	movieId        int64
	rating       float64
	timestamp      int64
	dtype: object



```



## 数据结构

### Series

Series是一种类似于一维数组的对象，它由一组数据（不同数据类型）以及一组与之相关的数据

```python
s=pd.Series([1,2,'a']) #左侧为索引，右侧为元素
>>> 0    1
	1    2
	2    a
dtype: object
# 获取索引
s.index
>>>RangeIndex(start=0, stop=3, step=1)
# 获取数据
s.values
>>>[1 2 'a']

# 创建一个具有标签索引的Series
s=pd.Series([1,2,'str'],index=['a','b','c'])
>>> a      1
	b      2
	c    str
dtype: object
s.index
>>>Index(['a', 'b', 'c'], dtype='object')

#使用Python字典创建Series
d={'a':90,'b':80,'c':60}
s=pd.Series(d)
>>> a    90
	b    80
	c    60
dtype: int64

#根据标签索引查询数据
s['a']
>>>90
type(s['a'])
>>><class 'numpy.int64'>
s[['a','b']]
>>> a    90
	b    80
	dtype: int64
```



### DataFrame

DataFrame是一个表格型的数据结构

- 每列可以是不同的值类型（数值、字符串、布尔值等）
- 既有行索引index,也有列索引columns
- 可以被看做由Series组成的字典

```python
data={
        'state':['Ohio','Ohio','Ohio','Nevada','Nevada'],
        'year':[2000,2001,2002,2001,2002],
        'pop':[1.5,1.7,3.6,2.4,2.9]
     }
df = pd.DataFrame(data)
>>>  state year  pop
0    Ohio  2000  1.5
1    Ohio  2001  1.7
2    Ohio  2002  3.6
3  Nevada  2001  2.4
4  Nevada  2002  2.9
df.dtypes
>>> state      object
	year       int64
    pop        float64
	dtype: object
df.conlumns
>>>Index(['state', 'year', 'pop'], dtype='object')
df.index
>>>RangeIndex(start=0, stop=5, step=1)

#DataFrame查询Series，如果只查询一列或一行，返回的则是pd.Series。多行、列就是pd.DataFrame
df['year'] #查询一列
>>> 0    2000
	1    2001
	2    2002
	3    2001
	4    2002
	Name: year, dtype: int64
type(df['year'])
>>>pandas.core.series.Series

df.loc[1] #查询一行
>>> state    Ohio
	year     2001
	pop       1.7
	Name: 1, dtype: object
type(df.loc[1])
>>>pandas.core.series.Series

df[['year', 'pop']]
>>> year	pop
	0	2000	1.5
	1	2001	1.7
	2	2002	3.6
	3	2001	2.4
	4	2002	2.9
type(df[['year', 'pop']])
>>>pandas.core.frame.DataFrame
df.loc[1:3]#左闭右闭
>>>     state   year    pop
	1	Ohio	2001	1.7
	2	Ohio	2002	3.6
	3	Nevada	2001	2.4
type(df.loc[1:3])
>>>pandas.core.frame.DataFrame

```



## 查询数据

```python


```







## Matplotlib

Matplotlib是一个Python的2D绘图库，它提供了各种类型的图表，如折线图、散点图、柱状图等。Matplotlib的缩写是由三个单词组成的：matrix（矩阵）、plot（绘图）以及library（库）。然而，需要注意的是，尽管Matplotlib自身命名比较长，但在使用时通常不能直接调用，而是需使用其子模块pyplot。这是因为pyplot是Matplotlib的核心绘图模块，包含了大多数常用的绘图函数。为了简化代码，用户通常会导入pyplot并将其简写为plt，然后直接使用plt下的方法来绘图。



## Seaborn



# 爬虫

















































































































































































































































































































































































































































































































































































































































































































































































