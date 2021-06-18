<!-- 
@Author : Eric Zhang
@CreateDate : 2021-6-18
@Editor : Visual Studio Code
 -->
 # 视图函数
 接受HttpRequest对象，通过HttpResponse对象返回响应的函数，主要处理接受来的请求
 ```py
 from django.http import HttpResponse

 def xxx_view(request,[其他参数])：
    ......
    return <HttpResponse>Object
 ```
 - 视图函数的第一个传入参数必须是```request```
 
 使用了Path转换器的视图函数编写见 ```Django Route.py```

