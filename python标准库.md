## 模块
导入模块：import module

导入模块的一部分：from report import get_description
## 包
为使python应用更具有可扩展性，可以吧多个模块组织成文件层次，称之为包

也许我们需要使用两种类型的天气预报，一是次日的，二是下周的，一种可行的方式是创建目录sources，在该目录中新建两个模块daily.py和weekly.p.

主程序是 boxes/weather.py:

    from sources import deily, weekly
    ...
    ...
    ...
模块一是：boxes/sources/daily.py:

    def forecast():
    ...
    ...
模块二是：boxes/sources/weekly.py

    def forecast():
    ...
    ...
还需要在sources目录下添加一个文件：init.py。这个文件可以是空的，但是python需要它，以便把该目录作为一个包

### 使用setdefault()和defaultdict()处理缺失的键

如果键不在字典中，新的默认值会被添加进去：

    periodic_table = {'Hy':1, 'He':2}
    carbon = periodic_table.setdefault('Carbon', 12)
    carbon
    12
如果试图把一个不同的默认值赋给已经存在的键，不会改变原来的值，仍将返回初始值。

defaultdict()的参数 是一个函数，把函数int作为参数传入，会按照int（）调用，返回整数0。

    from collections import defaultdict
    periodic_table = dafaultdict(int)
任何缺失的值都会被赋为整数0.

同样可以使用int(),list()或者dict()返回默认空的值，也可以使用lambda来定义默认值函数：

    bestiary = defaultdict(lambda: 'Huh?')
    bestiary['E']
    'Huh?'
### 使用counter()计数
标准库的计数器。使用：

    from collections import Counter
    breakfast = ['spam', 'spam', 'eggs', 'spam']
    breakfast_counter = Counter(breakfast)
    breakfast_counter 
    Counter({'spam':3,'eggs':1})
函数most_commom()以降序返回所有元素。

组合计数器：breakfast_counter + lunch_counter。从一个计数器去掉另一个计数器 使用‘-‘，也可以使用&求交集

使用有序字典OrderedDict()按键排序，它记忆字典键添加的顺序，然后从一个迭代器按照顺序返回，使用：

    from collections import OrderedDict
    quotes = OrderedDict([(),(),()])
### 双端队列：栈+队列

deque是一种双端队列，同时具有栈和队列的特征，它可以从任何一端添加和删除项。
我们从一个词的两端扫向中间，判断是否为回文。

    def palidrome(word):
        from collertions import deque
        dq = deque(word)
        while len(dq) > 1:
            if dq.popleft() !=  dq.pop():
                return False
        return True
    ...
    palidrome('a')
    True
    ...
    palindrome('racecar')
    True
    ...
    palindrome('halibut')
    Flase
*快速p判断回文的程序，只需要把字符串反转并和原字符串对比即可，利用反向切片的方式反转

    def another_pailndrome(word):
        return word == word[::-1]
### 使用itertools()迭代代码结构
itertools()包含特殊用途的迭代器函数。在for...in循环中调用迭代函数，每次会返回一项，并记住当前调用的状态。


即使cchain()的参数只是单个迭代对象，它也会使用参数进行迭代。

    import itertools
    for item in itertools.chain([1, 2].['a', 'b'])
        print(item)
    ...
    1
    2
    a
    b
cycle()是一个在它的参数之间循环的无限迭代器“

    import itertools
    for item in itertools.cycle([1, 2])
        print(item)
        ...
        1
        2
        1
        2
        .
        .
        .
accumulate()计算积累的值，默认的话，他计算的是累加和。可以把一个函数作为accumulate()的第二个参数，代替默认的加法函数。
### 使用pprint()友好输出
pprint()增加程序可读性，通过尽量排列输出元素从而增加可读性。