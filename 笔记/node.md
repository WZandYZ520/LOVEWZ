#http模块
	在开发测试期间，127.0.0.1对应的域名是localhost，它们都代表本台电脑
	请求交互的基本过程：
		客户端——————(请求行，请求头，请求体)——————>服务器
		服务器——————(状态行，响应头，实体内容)————>客户端
	端口号：
		每个端口号不能同时被多个web服务占用
		URL中的80端口号可以被省略
	web服务器：
		1.导入http模块						  const http = require('http')
		2.创建web服务器 http.createServer()    const server = http.createServer()
		3.为服务器绑定request事件     		  server.on('request',(req,res)=>{ })
		4.启动服务器							  server.listen(80,()=>{ })
	http协议的无状态性：
		http协议的无状态性：指客户端的每次http请求都是独立的，连续多个请求之间没有直接的关系，服务器不会主动保留
		每次http请求的状态
#第三方包
	如果只在项目开发阶段用到，在项目上线之后不会用到，则建议把这些包记录到devDependencies节点中  npm快捷键 -D
	如果上线以后和开发阶段都需要，则建议把这些包记录到dependencies
#获取URL参数
	一个url组成的部分有  (http Ip 端口号 路径 请求参数 哈希值)
	 req.query 是可以过去客户端发送过来的请求，查询参数，默认是空对象
	动态参数：
		req.params
	接收客户端请求体数据：
		req.body  默认情况下，如果不配置解析中间件，则默认为undefined
	app.use(express.static()) 静态资源共享
#路由
	1:导入express  require('express')
	2:express.router() 创建路由
	3:挂载具体的路由
	4：向外导出路由对象  module.exports
	中间件：
		app.use() 是注册全局中间件
		req.startTime() 是请求到达服务器的时间
		多个中间件是共享一份请求，共享一份req，res，但他们分别处理
		1：中间件一定要在路由之前注册  由上往下执行
		2：执行完中间件的业务代码后，必须调用next()函数    
		3：调用多个局部中间件可以用数组包含 			app.get('/',[mw1,mw2,mw3],(req,res)={ })
	应用级别的中间件：
		通过app.use()[全局] app.get()[局部] app.post()[局部] 绑定到app实例上面的中间件，都属于应用级别的中间件
	路由级别的中间价：
		绑定到express.Router() 上面的中间件叫做路由中间件(基本和应用级别一致)
	错误级别的中间件：
		专门用来捕获整个项目中发生的异常错误，从而防止项目异常崩溃的问题
		1：错误级别中间件的function处理函数中，必须有四个形参且顺序从前到后不能改变 (err,req,res,next)
		2:必须注册在所有路由之后
	express内置中间件：
		express.static() 快速托管静态资源
		express.json() 解析json格式的请求体数据
		express.urlencoded() 解析URL-encoded格式的请求体数据  固定写法 express.urlencodede({extended:false})
	第三方的中间件：
		const bodyp = require('body-parser') 用来解析格式
		app.use(bodyp())
#cors 
	CORS (Cross-Origin Resource Sharing) 跨域资源共享 由一系列http响应头组成，这些http响应头决定
	浏览器是否阻止前端js代码跨域获取资源
	1：cors主要在服务器端进行配置，客户端浏览器无需做任何额外的配置
	2：cors在浏览器中有兼容性。只有支持xmlHttpRequest Level2的浏览器，才能正常访问开启cors的服务器端口
		(ie10+ chrome4+ firefox3.5+)
	cors的响应头：
		1：Access-Control-Allow-Origin    res.setHeader('Access-Control-Allow-Origin','*')
			//允许某种URL 跨域
		2：Access-Control-Allow-Headers   res.setHeader('Access-Control-Allow-Headers','Content-Type，X-Custom-Header')
		 如果客户端向服务器发送了额外的请求头信息，则需要在服务器端，通过 Access-Control-Allow-Headers对额外的
		 请求头进行声明，否则这次请求就会失败
		 仅支持 Accept Accept-Language Content-Language DPR Downlink Save-Data Viewport-Width With 
			   Content-Type(值仅限于text/plain multipart/form-data application/x-www-form-urlencoded 三者之一)
		3：Access-Control-Allow-Methods  
			默认情况下，cors仅支持客户端发起Get Post HEAD请求
			如果客户端希望通过put，delete 等方式的请求，则需要在服务器端，通过Access-Control-Allow-Methods来指明实际
			请求所允许使用的http方法
			res.setHeader('Access-Control-Allow-Methods','get,post,head') 只允许使用某种方法
			res.setHeader('Access-Control-Allow-Methods','*')  允许所有http请求方法
	cors请求的分类：
		简单请求：
			1：get post head 三者请求方式之一
			2：http头部信息不超过以下几种字段(无自定义字段 Accept Accept-Language Content-Language DPR Downlink Save-Data Viewport-Width With 
			   Content-Type(值仅限于text/plain multipart/form-data application/x-www-form-urlencoded 三者之一 )
		预检请求：满足一个即为预检请求
			1：get post head 以外的method类型请求
			2：请求头中包含自定义头部字段
			3：向客户端发送application/json格式的类型
		区别：
			1：简单请求(客户端与服务器之间只会发生一次请求)
			   预检请求(客户端与服务器之间会发生两次请求，option预检请求成功之后，才会发生真正的请求)
#JSON和jsonp
	JSON：
	    javascript Object notation js
	    JSON是js对象标记， 是一种常用的数据结构
	    JSON里面只能放纯数据， 不能定义变量， 语法更加规范， 键值对要用双引号， 不能用单引号， 里面也不能多余的符号
	jsonp：
	    jsonp 是一种网络请求技术
	    JSONp 数据请求原理： 使用script标签的src属性发起数据的数据请求
	    jsonp只支持get请求不支持post请求
	    jsonp不能携带大量参数， 内存小， 安全保密性差。
	    callback是jsonp重要参数， 只有含有callback参数才可以是jsonp请求， 可以跨域
#cookie和webhttpstorage
	cookie是一种document属性的， 用来存储浏览器字段
	网页刷新时， 不会被重置， 可以用max - age修改有效期， 以秒为单位， 如果改为负值则为立即删除
	cookie只能在同源请求下才会放在请求头中， 跨域不会被放在 请求头中
	webhttpstorage 是由localStorage + sessionStorage 两种类型属于window类型
	localStorage 本地存储
	sessionStorage 会话存储
	里面有增删改查和clear清除
	setitem removeitem setitem getitem
	setitem 里面有相同为修改， 没有相同为增加
#Axios理解与使用
	前端最流行的ajax库
	特点：
		1：基本promise的异步ajax请求库
		2：浏览器端/node端都可以使用
		3：支持请求/响应拦截器
		4：支持请求取消
		5：请求/响应数据装换
		6：批量发送多个请求
	拦截器：拦截相同的请求，不拦不同端口的请求