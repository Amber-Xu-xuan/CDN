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
- 用户
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
-  如何配置中间件
配置在setting.py中
域名相同避免出现跨域访问不到


## webTerminal打开远程主机ssh界面
1. 用户请求luna获取连接
2. luna将远程主机的连接信息、登录协议、连接方式、允许的操作等传递给jumpserver
3. luna创建命令窗口
4. 通过websocket发起请求，与koko建立连接
5. koko获取cookie中的sessionID和csrfToken
6. koko向jumpserver获取用户信息、获取主机资产信息、主机系统用户信息、验证权限、获取命令过滤列表等
7. koko通过SSH连接主机（go语言的插件）

- luna显示连接成功后进入命令模式，用户输入命令
1. 检查命令是否有权执行（luna->koko)
2. 通过websocket传输命令给koko
3. koko通过SSH远程执行命令
4. 将主机返回信息打印到luna界面上


## webTeminal如何打开远程主机的图形界面
环境配置：
1. 目标主机安装vnc远程控制软件
2. jumpserver部署guacamole组件
3. nginx配置guacamole路径
[图片]


## 文件管理页面
通过koko操作资产上的文件，设置cookie的sessionID和csrfToken，打开对应网址

## 客户端软件如何通过堡垒机访问远程主机
客户机输入jumpserver的网址和端口，输入用户名和密码
koko监听对应端口
1. 客户端连接koko
2. 获取用户允许访问的节点
3. 客户输入指令，发送指令，获取允许访问的主机（不同的指令对应着不同的api）
4. 用户选择使用的主机，发送指令给koko，koko获取主机账号密码jump server

## 记录在线会话
koko建立连接之后发送会话建立日志给jumpserver，记录在terminal_session表中

