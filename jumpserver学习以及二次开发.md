堡垒机	
	万台服务器
	
- 跳板机和堡垒机的区别
	跳板机不对操作行为做出限制和监控
	实时收集
	监测网络环境
	集中报警

RDP
VNC协议:
webTeminal
	
jumpserve = go + python(Django)

	jumpserve:Django，有数据库
	luna:python+angularJS
	koko:go语言
	guacamole：

### jumpserve
	#### 用户
		jumpserve用户（AXE用户）【web界面、ssh登录】
		客户机管理用户【将命令推送到目标机，ansible执行】 
		客户机系统用户
			字符终端
			图形界面
			文件管理
		
- 资产授权：用户有哪些权限
- 命令过滤：设置可以执行和禁止的命令

## 会话管理
在线会话
历史会话

## 日志审计
- 登录日志
-ftp日志
- 操作日志
- 批量命令


jump serve只是AXE中的子系统
## jumpserver打开webTerminal（luna）
- 如何传递用户信息
cookie中记录sessionId，将session信息存储在redis中，sessionId存取session信息
- cookie如何设置sessionId
通过SessionMiddleWare
- 什么是中间件？
python的中间件相当于Java中的拦截器
-  配置中间件

## python命名规则
class:CapWords
Exceptions:CapWords
Functions:lower_with_under()
参数：lower_with_under