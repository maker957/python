## 正则表达式匹配
正则表达式与之相关功能都位于标准库模块re中。因此需要先引用它，需要定义一个用于匹配的模式字符串以及一个匹配的对象：源字符串。

举例：

    result = re.match('You','Young Frankenstein')
'You'是模式，'Young Frankenstein'是源---你想要检查的字符串。match函数用于查看源是否以模式开头。

对于更复杂的匹配，可以先对模式进行编译以加快匹配速度：

    youpattern = re.compile('You')
    ...
    result = youpattern.match('You','Young Frankenstein')
search(),fandall(),split(),sub()

1.使用match()进行准确匹配
举例：

    import re
    source = 'Young Frankenstein'
    m = re.match('You',source)
    if m:
        print(m.group())
    ...
    You
match()只能检测以模式串作为开头的源字符串。但是search()能检测任何位置的匹配：

    m = re.search('Frank', source)
    if m:
        print(m.group())
    ...
    Frank
改变匹配模式：
    
    m =re.match('.*Frank', source)
    if m:
        print(m.group())
    ...
    Young Frank
新模式能够匹配成功的简单解释：
* .代表任何单一字符
* *代表任意一个它之前的字符，.*代表任意多个字符
* Frank是我们想要在源字符串中某处进行匹配的短语。

2.使用search()寻找首次匹配

 * 任意位置寻找模式

3.使用findall()寻找所有匹配

* 匹配完所有后停止

4.使用split()按匹配切分

* 依据模式而不是简单的字符串将一个字符串切分成由一系列子串组成的列表。

5.使用sub()替换匹配

* 与replace()方法类似，只不过使用的是模式而不是文本串。

例如：

    m = re.sub('n', '?', source)
    m
    'You?g Fra?ke?stei?'

一些基本模式：
* 普通的文本值代表自身，用于匹配非特殊字符
* 使用.代表除/n外的字符。
* 使用*表示任意多个字符（包括0个）
* 使用？表示可选字符。（0个或1个）

模式：使用标识符（见E/学习文件/python）
. , ^,$,?,^和$叫做锚点，^将搜索域定位到源字符串中的开头，$定位到末尾。

    source = ''' I wish I may,I wish I might...Have a dish of fish tonight.'''
任意位置查询wish或者fish：

    re.findall('wish|fish', source)
    ['wish', 'wish', 'fish']
从开头匹配wish:

    re.findall('^wish', source)
    []
结尾匹配fish:

    re.findall('find$', source)
    []
查询以w或f开头，后面紧接着ish的匹配：

    re.findall('[wf]ish', source)
    ['wish', 'wish', 'fish']
查询以若干个w,s或h组合的匹配：

    re.findall('[wsh]+', source)
    ['w','sh','w','sh','h','sh','sh','h']
查询以ght开头，后面紧跟一个非数字非字母字符的匹配：

    re.findall('ght\W', source)
    ['ght\n', 'ght.']
查询以I开头，后面跟着wish的匹配（wish出现次数尽量少）：

    re.findall('I(?=wish)', source)
    ['I ', 'I ']
查询以wish结尾，前面为I的匹配（I出现的次数尽量少）

    re.findall('(?<=I)wish', source)
    ['wish', 'wish']
模式：定义匹配的输出
如果用括号将某一模式包裹起来，括号中模式匹配得到的结果归入自己的group中，而调用m.groups()可以得到这些匹配的元组。如下：

    m = re.search(r'(.dish\b).*(\bfish)',source)
    m.group()
    'a dish of fish'
    ...
    m.groups()
    ('a dish', 'fish')