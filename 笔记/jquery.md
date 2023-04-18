#原生js缺陷
	不能添加多个入口，如果添加过个，后面会把前面覆盖
	原生api比较长
	原生js有时候代码沉余
	原生js容错比较低，前面代码错误，后面代码无法执行
	原生js兼容差
#jQuery优点
	可以运行多个入口函数
	jQuery代码简洁(有隐形迭代)
	没有兼容问题
	容错较高，前面代码出错，后面没有影响
	
    jQuery是一个快速，小巧且功能丰富的JavaScript库。
    就是一个封装了很多方法的js库
	:odd 以零开始，奇数行变色
	：even 以零开始，偶数行变色
	：eq 自定义行数变色 用下标控制
	mouseover 事件在鼠标移动到选取的元素及子集上时触发
	mouseenter 事件只在鼠标移动到选取的元素上触发
	addClass 添加类
	removeClass  移除类
	toggleClass  切换类
	hasClass  判断类
	/*参数一：代表执行动画的时长 毫秒数，
	    也可以是代表时长的字符串 fast(200) normal(400) slow(600)
	  参数二：代表动画执行完毕后的回调函数
	  切换：如果显示则隐藏，如果隐藏则显示
	show() 显示
	hide()	隐藏
	toggle() 切换
	
	slideDown() 滑下 
	slideUp() 滑出
	slideToggle() 切换
	
	fadeIn() 淡入
	fadeOut() 淡出
	fadeToggle() 切换
	fadeTo() 淡入到什么程度  ！参数一为时间，参数二为程度0-1
	*/
    stop 停止动画
	第一个参数 是否清除队列
	第二个参数 是否跳转到最终效果
	
	jquery创建元素节点
	html() $() 两种方法
	html() 会把原来的内容给覆盖
		   可以解析标签
	$() 能创建元素，但是创建的元素只存在内容中，如果要在页面中显示，就要追加
	几种追加节点方法
		append()  添加到最后，如果有参数则把参数剪切到最后
		prepend() 添加到第一个，如果有参数则把参数剪切到第一
		before()  把元素添加到前面，为兄弟节点添加
		after()   把元素添加到后面，为兄弟节点添加
		appendTo()参数为父级，添加位置。a.appendTo(b) 把a添加到b里面的最后一个

    empty() 清空元素，只清空内容
	remove() 清除某个元素，移除
	val()   获取到输入框里面的内容	
	响应状态码 200 404 403 401 500
	2** 状态表示成功
	处理结果 行 头 空行 体
#jquery处理请求
	jquery封装的get请求
		$.get("地址http://00.000",{
				account: "a", //参数
				possword:'b' // 
				
			},data=>{
				console.log(data)
			})
			
    jquery封装的post请求
		$.post("地址http://00.000",{
				account: "a", //参数
				possword:'b' // 
				
			},data=>{
				console.log(data)
			})