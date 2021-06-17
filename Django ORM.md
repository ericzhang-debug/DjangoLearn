<!-- 
@Author : Eric Zhang
@CreateDate : 2021-6-16
@Editor : Visual Studio Code
 -->

## ORM模型设计
models.py 

 ```from django.db import models```
 
 class都继承自 models.Model
 创建完Model后迁移（任何修改完就执行）
 ```shell
 python manage.py makemigrations
 python manage.py migrate
 ```
### 字段
都属于model.XXXX()，第一个参数是在admin的显示名称

#### CharField()
- 对应varchar
- 必须制定最大长度
#### IntegerField()
- 对应int
#### EmailField()
- 对应varchar 
#### DateField()
- 对应 date
- 年月日
- 必须参数
    - auto_now 相当于update
    - auto_now_add 相当于create
    - default 程序设计时候设置固定值
#### DateTimeField()
- 对应 datetime
- 年月日时分秒
- 必须参数
    - auto_now 相当于update (bool)
    - auto_now_add 相当于create (bool)
    - default 程序设计时候设置固定值 (bool)
#### DecimalField() 小数
- 对应decimal
- 必须参数
    - max_digists 总位数
    - decimal_places 小数点的位置
    ```
    Example:
        0 0 0 0 0.0 0 
        max_digists=7
        decimal_places=2
    ```

### 字段选项
#### primary_key
- 没有指定就会自动添加递增ID作为主键 (bool)
#### blank
- 字段可否为空
#### null(小心使用)
- 值是否为空
- 默认False
#### default
- 设置默认值
- 一般和null=False(不能为空)连用
- 新增字段必须添加
#### db_index
- 是否添加普通索引
#### unique 
- 是否重复(唯一索引)
#### db_column
- 指定在数据库里的名称
- 不指定的就采用属性名（数据库：Model_属性名）
#### verbose_name
- 在admin的显示自定义名称


### 内部类 Meta
控制所在的这个类对应的模型的属性
```py
class Father(models.Model):
    pass
        class Meta:
            [TODO]
```
#### db_table 自定义表名 （默认:Model_属性名）


## ORM CRUD
对象管理器:方法 ```MyModel.objects.XXX()```

### 创建数据C

#### 方案一
##### 使用对象管理器(objects) create()
```py
MyModel.objects.create(属性n=属性n……)

```
##### 创建MyModel对象
```py
obj = MyModel()
obj.[key] = [value]
obj.save()  #必须执行这个
```

### 查询数据R
#### all()
返回QuerySet对象(类似数组)，内部是实例
#### __ str __
定义在class中，执行实例化的QuerySet对象时返回的字符串内容
```py
def __str__(self):
    return ....
```
```py
Example:
格式化返回图书的信息
def __str__(self):
    return '%s_%s_%s_%s'%(self.title,self.price,self.pub,self.market_price)

>>> from bookstore.models import Book
>>> books=Book.objects.all()
>>> books
<QuerySet [<Book: python_20.00_清华大学出版社_25.00>, <Book: django_210.00_北京邮电大学_250.00>]>
```
#### values()
查询部分列的数据并返回QuerySet对象，该对象里面存放的是字典
```py
Example:
>>> a2=Book.objects.values('title','pub')
>>> a2
<QuerySet [{'title': 'python', 'pub': '清华大学出版社'}, {'title': 'django', 'pub': '北京邮电大学'}]>

# 遍历一下，用字典的方法

>>> for book in a2:
>>>     print(book['title'])
python
django
```

#### values_list()
和values()的方法类似，但是返回的是元组，存在顺序，使用索引访问

#### order_by()
用法：order_by()

对字段选择性排序（字母先后顺序），默认升序排序，相当于执行all()、values()等后再对结果排序，重点在于QuerySet对象

当列前加'-'时按降序排序

```py
对所有的title的数据降序排列
a=Book.objects.values('title').order_by('-title')
等价于
a=Book.objects.order_by('-title')
```

#### *query属性
```<QuerySet>.query```得到SQL语句

```SQL
>>> print(a.query)
SELECT "bookstore_book"."title" FROM "bookstore_book" ORDER BY "bookstore_book"."title" DESC
```





