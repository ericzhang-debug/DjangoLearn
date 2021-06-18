# 路由基础结构
项目同名文件夹下 ```urls.py```

```urlpatterns```中插入```path()```

path(路由地址,视图函数 __名__ ,name=别名) => http://[ 地址 ]/page/2003/
- 路由地址 例如```'page/2003/'```，前不加```/```  后加不加```/```都可以
- 首页/的```route=''```
- 视图函数不能加(),加上就表示引入的是函数的返回值，而这里只需要名称

<br><br>

## Path转换器
匹配到响应的数据，按照关键字传参的方式传给视图函数

语法 <type:Name>
```PY
path('page/<int:page>/',views.XXX, )
```
需要加```<>```

视图函数预留传入参数
```PY
Example:

def pagen_view(request,pg):
    html = '<h1>这是我的编号为%s的网站</h1>'%(pg)
    return HttpResponse(html)
```

### 常见转换器类型
| Type | 作用 |备注|
|---|---|---| 
| str | 匹配除了```'/'```之外的所有 __非空__ 字符串 ||
|int|匹配0或者任何正整数，返回int||
|slug|配置任意由ASCII字母或数字和`-`、`_`|Django 2.0 以上支持|
|path|匹配非空字符串和`/`||

### 优先级
```urls.py```的```urlpatterns```数组由前到后根据是否符合规则匹配





