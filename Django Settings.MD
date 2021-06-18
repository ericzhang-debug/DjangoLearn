<!-- 
@Author : Eric Zhang
@CreateDate : 2021-6-18
@Editor : Visual Studio Code
 -->
 # settings.py
 ## 公有配置
 - 基础目录 ````BASE_DIR ```` 项目同名目录
 - 修改时区 ```TIME_ZONE```   中国 ```Asia/Shanghai```
 - 修改语言 ```LANGUAGE_CODE``` zh-hans中文
 - 配置数据库类型 ```DATABASES```
 - 启动模式（是否启动调试服务器）```DEBUG```
   - True 启动调试服务器，代码改动是自动实时加载（热启动），提供详细的报错页面
   - False 正常模式，生产模式，需要配置```ALLOWED_HOSTS```
 - 请求头HOST ```ALLOWED_HOSTS``` 过滤请求 上线时配置具体域名
 - 配置应用app ```INSTALLED_APPS``` 
 - 主路由配置 ```ROOT_URLCONF```
https://docs.djangoproject.com/en/3.2/ref/settings/#databases


文件引用 ```from django.conf import settings```

## 私有配置
XXX = XXX

文件引用 ```from django.conf import settings```


