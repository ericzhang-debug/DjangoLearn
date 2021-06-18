<!-- 
@Author : Eric Zhang
@CreateDate : 2021-6-18
@Editor : Visual Studio Code
 -->
 # GET 处理
request.GET返回QueryDict对象，类似于字典
- request.GET
```PY
request.GET['参数名']

Example :
/?a=1&b=2   #request.GET['a']得到 1
```
- request.GET.get()
```PY
request.GET.get('参数名','默认值')
#没有c的时候使用默认值
```
- request.GET.getlist()
```PY
request.GET.getlist()
# 当一个变量有多个值的时候使用
# 如果只用request.GET[]时返回最后一个
# 常用于复选框
```
