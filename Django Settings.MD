<!-- 
@Author : Eric Zhang
@CreateDate : 2021-6-18
@Editor : Visual Studio Code
 -->
 # settings.py
 - 基础目录 ````BASE_DIR ```` 项目同名目录
 - 修改时区 ```TIME_ZONE```
 - 修改语言 ```LANGUAGE_CODE```
 - 配置数据库类型 ```DATABASES```
 - 启动模式（是否启动调试服务器）```DEBUG```
   - True 启动调试服务器，代码改动是自动实时加载（热启动），提供详细的报错页面
   - False 正常模式，生产模式，需要配置```ALLOWED_HOSTS```
 - 请求头HOST ```ALLOWED_HOSTS``` 过滤请求