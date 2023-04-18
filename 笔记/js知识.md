#javaSccript
	javaScript是一种弱类型的脚本语言
	它里面有四个比较大的模块
	ECMAscript  定义js的语法规范，定义语言本身的变量，数据值，操作语句,内存管理...等内容 
	DOM   		document object model文档对象模型，提供对应的属性和方法,可以让js操作页面中的dom元素 
	事件对象		是用户与页面交互的桥梁，页面通过事件告诉用户做了那些操作
	bom			browser object model浏览器对象模型，提供浏览器的属性和方法
#js中的数据类型：
	基本类型：
		number
		string
		null
		symbol:
			symbol是唯一值， 两个symbol也不相等
		undefined
		boolean
		bigint
	引用类型：
		object：
			[]数组对象：
				创建数组：
					1：字面量定义 var arr = 【‘xxxx’10】
					2：通过构造函数定义
					var p2 = new array（‘hello’，2，3）参数是元素列表
					var p3 = new array（10）是参数长度
					var p4 = new array（[1，2，3] ）参数是数组
				遍历：
					forEach()
					map()
					find()
				增删改查：splice(n,m,z)从n后删除m个，补为z
					增：
						puch()    添加到最后
						unshift() 添加到最前
					删：
						pop()    删除最后一位
						shift()  删除第一位
					查：
						slice(n,m)从n截取到m
						IndexOf()第一次出现的位置
						lastIndexOf()最后一次出现的位置
						include()检测数组里面是否含有该元素
					截取：
						slice(n,m)从n截取到m
						substr(n，m)从n往后截取m个
						substring(n，m)从n截取到m
					拼接：concat()
					过滤：filter() 
					无穷大 infinity 
					转换为字符串：toString()
					排序：
						sort()默认从小到大
						reverse()倒叙数组
			{}普通对象
			 RegExp正则：
				用来处理字符串的规则，具有：
					懒惰性(设置全局匹配修饰符g后可以解决)
					贪婪性(默认捕获时，是按照正则所匹配的最长结果来获取)取消捕获贪婪性 +？(按照正则匹配最短结果获取)
				有两种创建方式：let reg = /\d+/;斜杠中间都是规则元字符
				let reg2 =new RegExp("\\d+"); 构造函数模式创建 两个参数：元字符，修饰字符
				正则表达式由：元字符和修饰符组成
				常用的元字符：
					* 零到多次
					+ 一到多次
					？ 左边是非量词元字符  零次或者一次
					   左边是量词元字符  取消捕获贪婪性
					   (?:)只匹配不捕获
					   (?=)正向预查
					   (?!)负向预查
					{n} 出现n次
					{n，}出现n次以上
					{n，m}n到m次
				特殊元字符：
					g 全局查找
					\  转义字符
					. 除换行以外的任意字符
					^ 以哪一个元字符作为开始
					$ 以哪一个元字符作为结束
					\n 换行
					\d 0-9之间的一个数字
					\D 非0-9之间的一个数字
					\w 数字，字母，下划线中的任意一个字符
					\s 一个空白字符
					\t 一个制表符(一个TAB键：四个空格)
					\b 匹配一个单词的边界
					x|y x或者y中的一个字符
					[]中括号出现的字符一般都代表本身的含义
					[xyz] x或y或z中的一个字符
					[^xy] 除了xy以外的字符
					[a-z] 指定a-z范围中的任意字符
					() 正则中的分组符号
					(?:)只匹配不捕获
					(?=)正向预查
					(?!)负向预查
				普通元字符：
					/xxxx/ 此正则匹配的就是本身
				重点字符:
					汉字/^[\u4E00-\u9FA5]$/
				正则表达式常用的修饰符：
					img：
						i==ignoreCase 忽略单词大小写匹配
						m==multiline 可以进行多行匹配
						g==global 全局匹配
						test 查找
				正则捕获的方法：
					正则RegExp.prototype上的方法：
						exec
						test
					字符串String.prototype上支持正则表达式处理方法：
						replace 字符串中替换的意思(一般伴随正则出现)，在字符串中只能替换一次，在正则里面可以全部替换
						match
						splite
			math：
				Math.found()四舍五入
				Math.random()随机数
				Math.abs()绝对值
				Math.sqrt（）开平方
				Math.pi() π
				Math.ceil()向上取整
				Math.floor()向下取整
				Math.pow(n,m)n的m次方
				Math.max()取数组最大值
				Math.min()取数组最小值
			日期对象:
				getFullYear（） 获取年
				getMonth（）获取月，后面要加1
				getData（）获取日期
				getHours（）获取小时
				getMinutes（）获取分钟
				getSeconds（）获取秒
				getDay（）获取日期
				getMilliseconds（）获取ms
				
				parse 把字符串转化为时间戳
				toDataString() 只保留年
				toString（） 转化为字符串
				toTimeString（）只保留时间

		function
		class
基本数据类型是按照值操作，直接把值存储到栈内存
引用数据类型的值是存储到堆内存当中，我们操作的都是堆内存的引用地址。
#js中检测数据类型的方式:
	typeof:
		注意：typeof null  == 'object'
	instanceof
	constructor
	Object.prototype.toString.call
#浏览器常用内核：
	（老）webkit：谷歌
	（新）blink ：谷歌
	gecko：火狐
	trident：ie
#js创建变量的几种方式：
	var    全局声明变量
	let		声明变量 (块级作用域)
	const   声明常量(块级作用域)
	class	声明类
	function 创建函数
	import/require 导入模块
#字符转换：
	let an = "abCD"
	console.log(an.toLocaleUpperCase())全部转换为大写
	console.log(an.toLocaleLowerCase())转换为小写
	
	字母与ASCII的转换
	let b = "abc";
	console.log(b.charCodeAt(0)) 索引值0的ASCII的值
	console.log(b.charAt(0))索引值0的代码
	String.fromCharCode(0)把ASCII转换为字符
	console.log(b.startsWith('a'))以a为开头
	console.log(b.endsWith())以谁为结尾
	
	indexof
	let c = "bca"
	console.log(c.indexOf("a"))获取字符的下标值
	console.log(c.lastIndexOf())倒着获取字符的下标值
	console.log("-".repeat())重复次数
#js输出：
	console控制在控制台输出
	console.log控制台输出日志，特点输出任意数据类型的数据，可以一次性输出多个值
	console.dir控制台详细输出，输出一个对象或者一个值得详细信息，只能输出一个值
	console.warn已警告的方式输出
	console.table把多维的JSON数据以表格形式输出
	alert  
	prompt
	innerHTML
	console.time
	里面代码的所加载时间
	console.timeEnd
#延迟过渡：
	transition-property:   ; 定义过渡样式
	transition-duration: ; 定义过度时间
	transition-delay： ；定义过渡延迟时间
	transition-timing-function:linear; 过渡事件函数
	linear 时间函数 速率均匀
	ease-in 开始慢
	ease-in-out 开始和结束慢
	out-in 结束慢
	animation：  动画
	transorm：  3d运动
	transorm：translatr  运动 可以X轴 Y轴 Z轴
	
	animation:动画  关键帧可以中间
	设置多个状态变化过程，实现复杂的效果
	
	transition 过渡动画 只能实现简单动画效果
	同一个样式只能有状态变化
	
	使用关键帧动画的样式 
	动画名字 动画时间  动画速率 重复次数infinite无线重复
#值传递和引用传递：
    值传递: 基本数据类型在赋值 把一个赋值给另一个变量 改其中之一 另外不会修改
	引用传递:复杂类型在赋值的时候  把一个赋值给另一个变量 改其中之一 另外会修改 
	实现深拷贝: 
		var s1 = JSON.stringify(o1)  //先对o1进行转成字符串
		var o2 = JSON.parse(s1)  //再对字符串进行转成对象
	怎么实现对象的遍历:
		 for...of Object.valaues()
	     for...in...   
	字符串常用的API  repalce() subString() substr()  startsWith() endswith() indexOf()
		from() 把原数据拷贝到新对象里面，这个操作属于浅拷贝过程
		assign()把第二个参数拷贝到第一个参数对象身上，浅拷贝
		source 源数据
		target 目标数据
		assign() 把第二个参数对象 拷贝到第一个参数对象上 浅拷贝过程
#dom docution object model 文档对象类型
#获取dom的方式:
	docution.getElementById():只能用docution
	getElementByTagName(["标签名"])
	getElementsByClassName([样式类名]) 不兼容IE6-8低版本浏览器
	docution.docutionElement:获取整个HTML
	querySelector()获取一个元素对象,不管匹配结果有多少个，都只获得第一个
	querySelectorAll()获取一组对象，获取的都是集合
	document.all 页面里面所有标签
	document.imges 页面所有img
	document.script[0] 页面中script对象
	document.anchors 获取页面所有锚点
	document.querySelector  属性=属性值
	document.body.childer body里面所有标签
#给dom元素设置内容
	innerHTML/innerTEXT
	value 操作表单元素的内容
	元素.style.xxx：""  操作的都是行内样式
	元素.className：""  操作的是当前元素的样式类
	元素.classList.add()："" 和className类似，兼容性较差
#获取dom节点的属性和方法
	页面中所有呈现的内容，都是一个节点（node）
	xxx.chidNodes 获取当前容器所有子节点（包含各种类型的节点）
	xxx.children 获取当前容器所有的元素子节点（只有元素标签的）
	[node].parentNode 获取，某一个节点的父节点
	[node].previousSibling 获取某一个节点的上一个节点（哥哥节点）
	[node].previousElementSibling 获取某一个节点的上一个哥哥元素节点
	[node].nextSibling 获取某一个节点的下一个节点(弟弟节点)
	[node].nextElementSibling 获取某一个节点的下一个弟弟元素节点
	xxx.firstChild 获取容器中第一个子节点
	xxx.firstElementChild 获取容器第一个元素子节点
	xxx.lastChild 获取容器中最后一个子节点
	xxx.lastElementChild 获取容器最后一个元素子节点
	获取当前节点的索引值：
		前面有几个哥哥，他的索引就是几
	document文档节点
		nodeType:9
		nodeName:document
		nodeValue:null
	元素节点：元素标签
		nodeType:1
		nodeName:大写标签名
		nodeValue:null
	文本节点：文字或者标签之间的空格和换行也被当做文本节点
		nodeType：3
		nodeName:"#text"
		nodeValue:文本内容
	注释节点：注释内容 
		nodeType:8
		nodeName:"#comment"
		nodeValue:注释内容
#jQuery获取节点
	prev 获取上一个元素哥哥节点
	next 获取下一个元素弟弟节点
	prevAll 获取所有的哥哥元素节点
	nextAll 获取所有的弟弟元素节点
	siblings 获取兄弟元素节点
	index 获取他的索引
	children 获取所有的元素子节点
#关于DOM元素中的增删改
	容器：container
	document.createElement()是在对象中创建一个对象，要与appendChild() 或insertBefore()方法联合使用。
	其中，appendChild()方法在节点的子节点列表末添加新的子节点。
		 insertBefore() 方法在节点的子节点列表任意位置插入新的节点
	增：document.createElement([标签名])：动态创建一个DOM元素
			 createTextNode 创建文本对象
	   [容器].appendChild([元素]):把元素动态插入指定容器的末尾
	   [容器].insertBefore([元素],[原始页面元素]):把新创建的元素放置到指定容器
	   原始页面前面，[原始元素]一定在容器里面
		document.createTextNode(): 创建一个文本节点
	删：[容器].removeChild([元素]) 在指定容器中移除元素
	改：replaceChild(new,old)  实现子节点(对象)的替换
	克隆：cloneNode() 浅拷贝 默认false
		cloneNode(true)  深拷贝
	什么是深拷贝和浅拷贝？
		浅拷贝就是只复制数组（对象）本身，而不复制其内容（引用类型的数据内容），最终两个数组中指向同一套数据。
		深拷贝则是既赋值本身也赋值内容。
	Js中对于引用类型的数据，默认进行的都是浅拷贝。
#给元素设置自定义属性
	xxx.getAttribute 操作的是dom	结构
	xxx.[" "] 操作的是堆内存
#js事件绑定的方式
	标签 onclick ="xxx" 
	获取标签.onclick=function(){}  不能绑定多个同类型事件
	获取标签.addEventListenner("不加on事件类型"，事件处理程序，布尔值)
	ie10及以下也可以用attchEvent()	
#取消事件绑定(要跟绑定事件的参数一模一样)
	标签.onclick= null；
	获取标签.removeEventListener("不加on事件类型"，事件处理程序) 不能取消匿名函数
	获取标签.detachEvent()
#事件流 事件执行顺序 传播顺序
	事件冒泡 ie
	事件捕获 netScape
	DOM事件流 既支持冒泡(默认) 也支持捕获
#阻止事件默认行为
	e.preventDefault() : 非 IE 使用
	e.returnValue = false ：IE 使用
#阻止事件冒泡
	event.stopPropagation();  事件处理过程中，阻止了事件冒泡，但不会阻击默认行为（执行超链接的跳转）
	event.cancelBubble=true ie和dom都能使用
    return false;  事件处理过程中，阻止了事件冒泡，也阻止了默认行为（不执行超链接的跳转） 
	event.preventDefault()事件处理过程中，不阻击事件冒泡，但阻击默认行为（它只执行所有弹框，却没有执行超链接跳转）
#事件委托
	事件委托又称事件代理
	JS高程上讲：事件委托就是利用事件冒泡， 只制定一个时间处理程序， 就可以管理某一类型的所有事件。
#定时器：
	如果定时器开启时候在按钮点击事件里面，每点击一次,都开启了一个定时器，所以定时器频率会变快
	其实目的就是为了点击时候加上一个判断，防止用户高频率的点击按钮
	浏览器刷新频率是1s 60帧，  一帧的时间 1000/60 = 16.67ms
			定时器 每隔一段时间执行一个方法
			// 参数1回调函数
			// 参数2是时间 以ms为单位
			// setInterval 属于异步执行：不会影响后续代码的执行，不会阻塞代码的
	clearInterval(timer)  关闭定时器 但是timer这个变量还存在，关闭定时器之后需要把timer置位空 
#防抖和节流
	防抖：是在多次触发事件中，只执行最后一次
	节流：是用户多次触发事件，会在多次触发的过程中，间隔执行事件。
#键盘事件
	keypress()事件
	keypress 当按钮被按下时，会发生该事件，我们可以理解为按下并抬起同一个按键。
	keydown()事件
	当按钮被按下时，发生 keydown 事件。
	keyup()事件
	keyup 事件会在按键释放时触发，也就是你按下键盘起来后的事件
	键盘的keyCode值
		左37 上38 右39 下40
		字母键和数字键
			1	2	3	4	5	6	7	8	9	0
			49	50	51	52	53	54	55	56	57	48
			Q	W	E	R	T	Y	U	I	O	P
			81	87	69	82	84	89	85	73	79	80
			A	S	D	F	G	H	J	K	L
			65	83	68	70	71	72	74	75	76
			Z	X	C	V	B	N	M
			90	88	67	86	66	78	77
		 数字键盘区（Pad区）
			/	*	-
			111	106	109
			7	8	9	+
			103	104	105	107
			4	5	6
			100	101	102
			1	2	3	Enter
			97	98	99	108
			0	·
			96	110
		功能键
			F1	F2	F3	F4
			112	113	114	115
			F5	F6	F7	F8
			116	117	118	119
			F9	F10	F11	F12
			120	121	122	123
#BOM浏览器对象
	screenLeft 窗口在屏幕的位置
	screenX	 窗口在屏幕的x坐标
	outerWidth  浏览器外观的大小
	innerWidth  浏览器的可视区域
	screen  屏幕信息
	clientWidth 文档宽度
	open() 打开新窗口
	close  关闭窗口
	loction 地址
	history  历史记录
	history.forword 下一页
	history.back   上一页
	history.go(0) 当前 go(-1)上一页 go(1)下一页
#Ajax
	ajax: async javascript and xml
	  异步的js和xml
	xml : extensible markup language
	  一种标记语言,可扩展标记语言
	api：
		XmlHttpRequest() 创建xnr对象的构造函数
		status()  响应状态码值 200 404
		statusText() 响应状态文本
		readyState()  标识请求状态的制度属性
			0  初始
			1  open()之后
			2  send()之后
			3  请求中
			4  请求成功
		onreadystaechange 绑定readyState改变的监听
		responseType 指定响应数据类型，如果是JSON，后自动解析响应头数据
		response  响应体数据，类型取决于responseText的指定
		timeout   指定请求超过时间，默认为0代表没有限制
		ontimeout  绑定超时的监听
		onerror  绑定请求网络错误的监听
		open()   初始化一个请求，参数为(method，url[，async])
		send(data) 发送请求
		abort()   中断请求
		getResponseHeader(name)	 获取指定名称的响应头值
		getAllResponseHeaders()  获取所有响应头组成的字符串
		setRequestHeader(name,value)  设置请求头
	ajax 实现的核心 new XMLHttpRequest() 对象
	  	四步:
	  		1:创建对象
	  		2:初始化设置
	  		3:发送
	  		4:绑定事件
	ajax的优点
	 1 ajax属于一个异步任务，不会阻塞代码，用户体验好
	 2 ajax不用刷新整个页面，可以实现局部刷新 
	 ajax 实现的核心 new XMLHttpRequest() 对象
	 1. 原生ajax-get 请求
			function ajax_get(){
				var xhr = new XMLHttpRequest()
				xhr.open("get","http://000.000.000.000:0000")
				xhr.send()
				xhr.onreadystatechange=function(){
					if(xhr.readyState==4){
						console.log(xhr.responseText)
					}
				}
			}
			ajax_get()
	2. 原生ajax_post 请求
	  function ajax_post(){
	      var xhr = new XMLHttpRequest()
	      xhr.open("post", "http://192.168.208.117:5000/login")
	      xhr.setRequestHeader("Content-Type", "application/x-www-form-urlencoded")
	      xhr.send("account=a&password=b")
	      xhr.onreadystatechange = function(){
	          if(xhr.readyState == 4){
	              console.log(2, JSON.parse(xhr.responseText))
	          }
	      }
	  }
	 ajax_post()
##原生ajax-get 请求
	function ajax_get(){
	  var xhr = new XMLHttpRequest()
	  xhr.open("get","http://000.000.000.000:0000")
	  xhr.send()
	  xhr.onreadystatechange=function(){
		if(xhr.readyState==4){
			console.log(xhr.responseText)
		}
	  }
	}
	ajax_get()
##原生ajax_post 请求
	 function ajax_post(){
		var xhr = new XMLHttpRequest()
	    xhr.open("post", "http://192.168.208.117:5000/login")
	    xhr.setRequestHeader("Content-Type", "application/x-www-form-urlencoded")
        xhr.send("account=a&password=b")
        xhr.onreadystatechange = function(){
	       if(xhr.readyState == 4){
	            console.log(2, JSON.parse(xhr.responseText))
	          }
	      }
	     }
	        ajax_post()
##jquery封装的get请求
	$.get("地址http://00.000",{
		account: "a",  
		possword:'b'  参数
		
		},data=>{
			console.log(data)
		})
		
##jquery封装的post请求
		$.post("地址http://00.000",{
			account: "a", //参数
			possword:'b' // 
			
		},data=>{
			console.log(data)
		})
		
##axios插件封装的get请求
		axios.get("地址http://00.000",{
			params:{account: "a",possword:'b'} //参数
			
		}),then(res=>{
			console.log(res.data)
		})
		
##axios插件封装的post请求
		axios.post("地址http://00.000",{
			account: "a",
			possword:'b' //参数
			
		}),then(res=>{
			console.log(res.data)
		})
		
##fetch es6新增的请求方式，默认get请求，不建议使用fetch的post请求
		fetch("地址").then(res=>{
			res.json().then(data=>{
				console.log(data)
			})
		})
#cookie
	cookie : 是浏览器中一个存储数据的字段
	英文 cookie 点心，甜点
	不同域名下的Cookie各自独立，每当客户端发起请求时，会自动把当前域名下所有未过期的Cookie一同发送到服务器
	Cookie 不具有安全性
	特点：
		1：自动发送
		2：域名独立
		3：过期时限
		4：4kb限制
	1，cookie是一段字符串，网页刷新时，不会重置
	2，cookie虽然是字符串，但里边的数据是以键值对存储的，可以通过键改变值，相同的键会替换，不同的值会拼接
	3，不是键值对，会被键值对覆盖，他有默认的键为空
	4，cookie有效期：默认是回话cookie，窗口关闭则过期销毁
		cookie可以设置有效期，实现长期有效，叫有效期cookie、长期cookie
		max-age="" cookie设置有效期方法，以秒为单位
		删除的话，把有效期改为-1 负值 表示立即删除
	5，当浏览器发起ajax请求时，会把本地的cookie自动放入请求头部发给服务器
		限制条件 ：cookie只支持同源请求，跨域请求头中没有cookie
		注意 ： 由于请求头不支持中文，所以cookie中尽量不放中文
	webstorage = localStorage + sessionstrorage
		sessionStorage 会话存储，作用相当于没有设置有效期的cookie
		localStorage 本地存储，作用相当设置了有效期的cookie
	增
		localStorage.setItem(“”)
		sessionStorage.setItem("")
	删
		localStorage.removeItem("")
		sessionStorage.removeItem("")
	清除
		localStorage.clear("")
		sessionStorage.clear("")
	改
		setitem 如果已经有，则为修改，如果没有，则为增加
	查询
		getitem 
		可以通过循环来遍历每一个键
		
		-------------------------------------------
		cookie 和 webstrorage的区别
	1 ：cookie是document的属性，webstrorage是window的属性
	2 ：cookie限制大小4kb，webstrorage限制大小5mb
	3 ：cookie会随ajax请求头发给服务器, webStorage只能在浏览器本地存储
#web开发模式
	比如企业级网站，主要功能是展示而没有复杂的交互，并且需要良好的SEO，则需要使用服务器端渲染
	类似后台管理项目，交互性强，不需要考虑SEO，则使用前后端分离的开发者模式
#不同模式下的身份认证
	服务器端渲染推荐使用Session认证机制
	前后端分离推荐使用jwt认证机制：
		jwt：JSON web token 是目前最流行的跨域认证解决方案			
			由Header(头部) payload(有效核载) Signature(签名)组成 三者之间用英文"."分割
			其中Payload部分才是真正的用户信息，它是用户信息经过加密过后产生的字符串
			Header和Signature是安全性相关的部分，只是为了保证token的安全性
#es6
	let 变量不能重复声明
		块级作用域
	const 只能声明，不能修改的常量
		  一般常量都大写，并且一定要有值，块级作用域。
	原型对象：
		__propo__与prototype指向同一个对象  __propo__指向propotyre原型对象
		原型链：Object.defineProperty()参数有：
					enumerable：true/false 控制属性是否可以被枚举
					writable：true/false  控制属性是否可以被修改
					configurable：true/false  控制属性是否可以被删除
	promiss: 是js中进行异步编程的新解决方案
			从语法上来讲promiss是一个构造函数
			从功能上讲promiss对象用来封装一个异步操作并可以获取其值
			特点：
				链式调用(主要解决回调地狱问题)
				指定回调函数的方式更加灵活
			promiss 形式实现
			resolve 解决   函数类型的数据
			reject 拒绝	   函数类型的数据
			api：
				catch()用来处理失败的函数
				Promise.resolve()  如果传入的参数为非Promise类型的对象，则返回的结果为成功的Promise对象
								   如果传入的参数为Promise类型的对象，则参数的结果决定了resolve的结果
				Promise.reject()  不管传入什么值结果都为失败，失败值为参数
				all() 参数必须都为成功对象才能返回一个Promise对象，如果有一个失败，则状态为失败失败值为失败参数
				race() 第一个参数的状态为最终状态
			1：promise 的状态
			   实例对象的一个属性 【promiseState】只有三个值 pending(初始) resolved(成功) rejected(失败)
			2：promise对象的值
				实例对象的另一个属性【promiseResult】保存着【成功/失败】的结果
			3:then()的状态
				1：由then()指定的回调函数执行结果决定
				2：如果抛出异常，则then的状态为失败
				3：如果返回一个非Promise对象，为成功
				4：如果返回一个Promise对象，此Promise结果就为then的状态
			4:中断Promise链
				有且只有一种办法  return new Promise(()=>{ }) 让promise状态变为pending 就无法向下执行传递
	async与await
		async函数：
			函数的返回值为promise对象
			promise对象的结果由async函数执行的返回值决定
		await表达式:
			await右侧的表达式一般为promise对象，但也可以是其他值
			如果表达式是promise对象，await返回的promise成功的值
			如果表达式是其他值，直接将此值作为await的返回值
		注意:1:awiait必须写在async函数中，但async函数中可以没有await
			 2:如果await的promise失败了，就会抛出异常，需要通过try...catch捕获处理
#异步编程的类别
	fs 文件操作
	数据库操作
	ajax
	定时器
#js请求类型方式
	get 从服务器端读取数据
	post 向服务器端添加新数据
	put 更新服务器端已有数据
	delete 删除服务器端数据
	head
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
#git和svn
	svn是集中式版本控制系统，版本库是几种放在中央服务器的。集中式版本控制系统是必须联网才能工作。
	git是分布式版本控制系统，没有中央服务器，每个人的电脑就是一个完整的版本库，
		工作的时候不需要联网，可以离线工作。