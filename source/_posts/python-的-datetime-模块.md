---
title: python 的 datetime 模块
date: 2019-03-29 21:56:59
tags:
- python
- date-time
categories:
- python
img: https://blog-cdn.wcmoon.com/python.jpg
---

开发的时候不可避免会遇到获取时间和处理时间的场景，python 为开发者提供了一个模块叫 datetime，运用这个模块可以很好地处理大部分问题。

### 获取当前的日期和时间
```
import datetime

now = datetime.datetime.now()
print(now)
```
运行以上代码，在我本机上输出为
```
2019-03-29 15:02:26.404151
```
### 获取当前的日期
```
import datetime

today = datetime.date.today()
print(today)
```
运行得到结果
```
2019-03-29
```
### datatime里有什么
如果你够细心，应该已经发现，在第一个例子里，我们用的是

```
datetime.datetime
```
而在第二个例子里，我们用的是

```
datetime.date
```
这里的 `datetime` 和 `date` 就是 `datetime` 这个库的里的两个类。

所以 `datetime` 里到底有什么呢，我们可以用 `dir` 函数来看看

```
import datetime

print(dir(datetime))
```
这样可以把 `datetime` 的所有属性值打印出来
```
['MAXYEAR', 'MINYEAR', '__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__spec__', 'date', 'datetime', 'datetime_CAPI', 'time', 'timedelta', 'timezone', 'tzinfo']
```
一般来说，我们常用 datetime 这四个类：
```
data
time
datetime
timedelta
```
下面用几个例子看看这几个类

## datetime.date
### 用 `Date` 对象表示日期
```
import datetime

d = datetime.date(2019, 4, 13)
print(d)
```
输出
```
2019-04-13
```
上面的 `date()` 是 `date` 类的构造函数，这个构造函数传入三个参数：`year, month, day`。

### 获取当前日期
```
from datetime import date

today = date.today()

print("Current date =", today)
```
这里用类里的 today() 函数创建了一个包含当前日期的 `data` 对象。
输出
```
Current date = 2019-03-29
```
### 从 `timestamp` 里获取日期
`timestamp` 是从 `UTC` 时间的1970年1月1号到某个时间的秒数。可以通过 `fromtimestamp()` 方法把 `timestamp` 转化为日期。
```
from datetime import date

timestamp = date.fromtimestamp(1553853181)
print("Date =", timestamp)
```
输出
```
Date = 2019-03-29
```
## datetime.time
一个 time 类构造出的 time 对象表示了当地的时间

### 用 time 对象表示时间
```
from datetime import time

# time(hour = 0, minute = 0, second = 0)
a = time()
print("a =", a)

# time(hour, minute and second)
b = time(11, 34, 56)
print("b =", b)

# time(hour, minute and second)
c = time(hour = 11, minute = 34, second = 56)
print("c =", c)

# time(hour, minute, second, microsecond)
d = time(11, 34, 56, 234566)
print("d =", d)
```
输出的是
```
a = 00:00:00
b = 11:34:56
c = 11:34:56
d = 11:34:56.234566
```
打印时、分、秒、毫秒
```
from datetime import time

a = time(11, 34, 56)

print("hour =", a.hour)
print("minute =", a.minute)
print("second =", a.second)
print("microsecond =", a.microsecond)
```
打印输出
```
hour = 11
minute = 34
second = 56
microsecond = 0
```
我们并没有初始化秒表信息，它的默认值为0

## datetime.datetime
这个类包含了 日期 和 时间 的信息

### datetime 对象
```
from datetime import datetime

#datetime(year, month, day)
a = datetime(2018, 11, 28)
print(a)

# datetime(year, month, day, hour, minute, second, microsecond)
b = datetime(2017, 11, 28, 23, 55, 59, 342380)
print(b)
```
打印输出
```
2018-11-28 00:00:00
2017-11-28 23:55:59.342380
```
`datetime()` 构造函数里的前三个参数 `year, month, day` 是必须的。

### 打印年、月、日、时、分、秒和时间戳
```
from datetime import datetime

a = datetime(2017, 11, 28, 23, 55, 59, 342380)
print("year =", a.year)
print("month =", a.month)
print("hour =", a.hour)
print("minute =", a.minute)
print("timestamp =", a.timestamp())
```
打印输出
```
year = 2017
month = 11
hour = 23
minute = 55
timestamp = 1511884559.34238
```
## datetime.timedelta
timedelta 可以用来做 两个日期和时间 之间的计算

### dates 和 times 的差值
```
from datetime import datetime, date

t1 = date(year = 2018, month = 7, day = 12)
t2 = date(year = 2017, month = 12, day = 23)
t3 = t1 - t2
print("t3 =", t3)

t4 = datetime(year = 2018, month = 7, day = 12, hour = 7, minute = 9, second = 33)
t5 = datetime(year = 2019, month = 6, day = 10, hour = 5, minute = 55, second = 13)
t6 = t4 - t5
print("t6 =", t6)

print("type of t3 =", type(t3))
print("type of t6 =", type(t6))
```
打印输出
```
t3 = 201 days, 0:00:00
t6 = -333 days, 1:14:20
type of t3 = <class 'datetime.timedelta'>
type of t6 = <class 'datetime.timedelta'>
```
注意，t3 和 t6 是

```
<class 'datetime.timedelta'>
```
### 两个 timedelta 对象的差值
```
from datetime import timedelta

t1 = timedelta(weeks = 2, days = 5, hours = 1, seconds = 33)
t2 = timedelta(days = 4, hours = 11, minutes = 4, seconds = 54)
t3 = t1 - t2

print("t3 =", t3)
```
打印输出
```
t3 = 14 days, 13:55:39
```
### timedelta 对象可以为负值
```
from datetime import timedelta

t1 = timedelta(seconds = 33)
t2 = timedelta(seconds = 54)
t3 = t1 - t2

print("t3 =", t3)
print("t3 =", abs(t3))
```
打印输出
```
t3 = -1 day, 23:59:39
t3 = 0:00:21
```
### 用秒数表示时间间隔
我们可以用 `total_seconds()` 把 `timedelta` 对象表示成秒数
```
from datetime import timedelta

t = timedelta(days = 5, hours = 1, seconds = 33, microseconds = 233423)
print("total seconds =", t.total_seconds())
```
打印输出
```
total seconds = 435633.233423
```
`timedelta` 对象之间也支持 `+` 运算符。`timedelta` 对象和整型和浮点型数之间也可以使用 乘法 和 除法。

## python 格式化日期和时间
在 python 里我们一般可以用 `strftime()` 和 `strptime()` 方法来处理格式化数据问题。

### strftime() - 把 datetime 对象转化为 string
```
from datetime import datetime

# current date and time
now = datetime.now()

t = now.strftime("%H:%M:%S")
print("time:", t)

s1 = now.strftime("%m/%d/%Y, %H:%M:%S")
# mm/dd/YY H:M:S format
print("s1:", s1)

s2 = now.strftime("%d/%m/%Y, %H:%M:%S")
# dd/mm/YY H:M:S format
print("s2:", s2)
```
打印输出
```
time: 09:16:25
s1: 03/31/2019, 09:16:25
s2: 31/03/2019, 09:16:25
```
这里的 `%Y %m %d %H` 就是格式化的代码。 `strftime()` 方法接受一个或多个格式化代码，返回一个格式化后的字符串。
```
%Y - year
%m - month
%d - day
%H - hour
%M - month
%S - second
```
### strptime() - 把 string 转化为 datetime 对象
```
from datetime import datetime

date_string = "21 June, 2018"
print("date_string =", date_string)

date_object = datetime.strptime(date_string, "%d %B, %Y")
print("date_object =", date_object)
```
打印输出
```
date_string = 21 June, 2018
date_object = 2018-06-21 00:00:00
```
strptime() 函数接收两个参数

1. 一个表示日期和时间的 string
2. 格式化代码

## 处理时区
python 更推荐使用第三方库 `pytZ` 类库来处理时区问题
```
from datetime import datetime
import pytz

local = datetime.now()
print("Local:", local.strftime("%m/%d/%Y, %H:%M:%S"))


tz_NY = pytz.timezone('America/New_York') 
datetime_NY = datetime.now(tz_NY)
print("NY:", datetime_NY.strftime("%m/%d/%Y, %H:%M:%S"))

tz_London = pytz.timezone('Europe/London')
datetime_London = datetime.now(tz_London)
print("London:", datetime_London.strftime("%m/%d/%Y, %H:%M:%S"))
```
打印输出
```
Local: 03/31/2019, 09:37:37
NY: 03/30/2019, 21:37:37
London: 03/31/2019, 02:37:37
```
