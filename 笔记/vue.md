#vue
	一套用于构键用户界面的渐进式JavaScript框架
	2013 尤玉溪开发出一款轻量框架--seed。同年12月seed更名为vue，版本号0.6.0
	2014 vue正式对外发布，版本号0.8.0
	2015 10月27 正式发布vue1.0.0版本
	2016 10月1 正式发布vue2.0.0
	2020 9月18 正式发布vue3.0.0
	特点：
		1：采用组件化模式，提高代码复用率，让代码更好维护
		2：声明式编码，无需直接操作DOM，提高开发效率
		3：使用虚拟Dom+优秀的diff算法，尽量复用Dom节点
#初识vue：
	1，想让Vue工作，就必须创建一个Vue实例，且要传入一个配置对象
	2，Vue实例和容器是一一对应的
	3，真实开发中只有一个Vue实例，并且会配合着组件一起使用
	3，{{xxx}}中的xxx要写js表达式，且xxx可以自动读取data中的所有属性
	4，一旦data中的数据改变，摸版里面的内容也会自动更新改变
	
	注意区分：js表达式 和 js代码(语句)
		1，表达式：一个表达式会产生一个值，可以放在任何一个需要值得地方
			(1):a
			(2):a+b
			(3):demo(1)
			(4):x===y?'a':'b'
		2，js代码(语句)
			(1):if(){}
			(2):for(){}
#Vue摸板语法：
	1：插值语法：
		功能：用于解析标签体内容
		写法：{{xxxx}}，xxxx是js表达式，且可以直接读取到data中的所有属性
	2：指令语法：
		功能：用于解析标签(包括:标签属性，标签体内容，绑定事件...)
		举例：v-bind 可以简写为 ":" :href= 'xxx' xxx也是js表达式，且可以直接读取到data中所有属性
	
	data与el的两种写法：
		1：el有两种写法：
			(1)：new Vue({ })的时候配置el属性
			(2)：先创建Vue实例，随后再通过vm.$mount('#box') 指定el的值   const vm = new Vue({}) vm.$mount('#')
		2:data两种写法：
			(1)：对象式  data：{}
			(2)：函数式  data：function(){} 简写为 data(){ }      ！！！不能使用箭头函数，且函数式里面的this为Vue
		原则：
			由Vue管理的函数，一定不能使用箭头函数，一旦写了箭头函数，this会被改变就不是Vue实例
			
#Vue指令大全：
	v-bind：  单向绑定 可简写为 ":" 
	v-model   只能应用在表单类元素(含有value值) 双向绑定
	v-on:     绑定事件/监听，可简写为@
	v-if:     条件渲染(动态控制节点是否存在)，特点：不展示的Dom直接被移除
	v-else:   条件渲染(动态控制节点是否存在)
	v-show:   条件渲染(动态控制节点是否展示)，特点：不展示的Dom元素为被移除，仅隐藏样式
	v-for:    遍历数组/对象/字符串，基本和js一样，可以v-for = 'a in xxx' xxx为容器 v-for = 'a of xxx'
	v-text:   向其所在节点中渲染文本内容,会替换掉节点中的内容
	v-html:   向指定节点中渲染包含html结构的内容
			  !!!注意:v-html有安全性问题,在网站上动态渲染任意html容易导致xss攻击,一定要在可信任的内容上使用
	v-cloak:  特殊属性没有值,Vue实例创建完毕并接管容器后,会自动删除v-cloak属性
	v-once:   特殊属性没有值,所在节点在初次动态渲染后,变静态内容,以后的数据改变不会引起v-once所在结构的更新
	v-pre:    特殊属性没有值,跳过其所在节点的编译过程
#MVVM模型
	m   模型(model)data中的数据  
	v   视图(view) 摸板代码
	vm  视图模型(viewModel) Vue实例
	1:data中所有的属性,最后都出现在vm身上
	2:vm身上所有的属性和Vue原型上所有属性,在Vue摸板中都可以直接使用
#Vue中的数据代理
	通过vm对象来代理data对象中属性的操作(读/写)
	Vue数据代理的好处：
		更加方便的来操作data中的数据
	基本原理：
		通过Object.defineProperty()把data对象中所有属性添加到vm上
		为每一个添加到vm上的属性，都指定一个getter/setter
		在getter/setter内部去操作(读/写)data中对应的属性
##Vue常用的事件修饰符
	1：prevent: 阻止默认事件
	2：stop ： 阻止事件冒泡
	3：once ： 事件只触发一次
	4：captrue： 使用事件的捕获模式
	5：self ：  只有event.target是当前操作的元素时才触发事件
	6：passive： 事件的默认行为立即执行，无需等待事件回调执行完毕
#Vue事件
	Vue中的键盘事件：
	    1：Vue常用的按键别名：
			回车 => enter
			删除 => delete(删除和退格都可以)
			退出 => esc
			空格 => space
			换行 => tab(系统修饰键)
			上 => up
			下 => down
			左 => left
			右 => right
		2:Vue未提供别名的按键，可以使用按键原始的key值去绑定，但需要短横线命名法：kebab-case
		3：系统修饰键(用法特殊)：ctrl、alr、shift、tab、meta(win)
			(1):配合keyUp使用：按下修饰键的同时，再按下其他键，随后释放其他键，事件才会被触发
			(2)：配合keyDown使用：正常触发事件
		4:常规keyCode去指定具体按键 js里面有按键编码
		5：Vue.config.keyCodes.自定义键名 = 键码  可以自定义按键别名
##computed和watch之间的区别：
	计算属性:componted:
		1.定义：要用的属性不存在，要通过已有属性计算得来。
		2.原理：底层借助了Objcet.defineproperty方法提供的getter和setter。
		3.get函数什么时候执行？
			(1).初次读取时会执行一次
			(2).当依赖的数据发生改变时会被再次调用。
		4.优势：与methods实现相比，内部有缓存机制（复用），效率更高，调试方便。
		5.备注：
			1.计算属性最终会出现在vm上，直接读取使用即可。
            2.如果计算属性要被修改，那必须写set函数去响应修改，且set中要引起计算时依赖的数据发生改变。
    监视(侦听)属性watch：
        1.当被监视的属性变化时, 回调函数自动调用, 进行相关操作
        2.监视的属性必须存在，才能进行监视！！
		3.监视的两种写法：
            (1).new Vue时传入watch配置
	        (2).通过vm.$watch监视
		深度监视：
		     1，Vue中的watch默认不监测对象内部值得改变(一层)
		     2，配置deep：true可以监测对选哪个内部值改变(多层)
		备注：
		     1，Vue自身可以监测对象内部值得改变，但Vue提供的watch默认不可以
		     2，使用watch时根据数据的具体结构，决定是否采用深度监视
#Vue监视数据的原理：
	1,vue会监视data中所有层次的数据
	2,如何监测对象中的数据：
		通过setter实现监视，且要在new Vue时就传入要监测的数据。
		(1):对象后追加的属性，Vue默认不做响应式处理
		(2):如需给后添加的属性做响应式处理，请使用如下api
			Vue.set(tagert,'propertyName/index','val')或
			this.$set(tagert,'propertyName/index','val')
	3,如何监测数据中的数据:
		通过包裹数据更新元素的方式实现,本质就是做了两件事
		(1):调用原生对应的方法对数据进行更新
		(2):重新解析摸板,进而更新页面
	4,在Vue修改数组中的某个元素一定要使用以下方法:
		(1):使用这些api:puch()、pop()、shift()、unshift()、splice()、sort()、reverse()
		(2):Vue.set()或vm.$set()
	特别注意:Vue.set()和vm.$set() 不能给vm或vm的根数据对象添加属性！！！
#绑定样式：
	class样式：
		写法：class="xxx" xxx可以是字符串、对象、数组
		字符串写法适用于：类名不确定，要动态获取
		数组写法适用于：要绑定多个样式，样式个数和名字都不确定
		对象写法适用于：要绑定多个样式，个数确定，名字也确定，但不确定用不用
	style样式：
		：style="{fontSize：xxx}"其中xxx是动态值
		：style='[a,b]'其中a，b是样式对象
##react、vue中的key的作用(key的内部原理)！！！
	1：虚拟Dom中key的作用：
		key是虚拟Dom对象的标识，当数据发生改变时，vue会根据[新数据]生成[新的虚拟Dom]，
		随后vue进行[新虚拟Dom]与[旧虚拟Dom]的差异比较，比较规则如下：
	2：对比规则：
		(1).旧虚拟DOM中找到了新虚拟DOM相同的key：
			*1.若虚拟DOM中内容没变，直接使用之前的真实DOM
			*2.若虚拟DOM中内容改变了，则生成新的真实DOM，随后替换掉页面中之前真实的DOM
		(2).旧虚拟DOM中未找到与新虚拟DOM相同的key：
			创建新的真实DOM，随后渲染到页面
	3.用index作为key可能会引发的问题：
		(1).若对数据进行：逆序添加、逆序删除等破坏顺序操作：
			会产生没有必要的真实DOM更新==>界面效果没有问题，但效率低
		(2).如果结构中还包含输入类的DOM：
			会产生错误的D0M更新===>界面有问题
	4.开发中如何选择key：
		(1)：最好使用每条数据的唯一标识作为key，比如id、手机号、身份证号、学号等唯一值
		(2)：如果不存在对数据的逆序添加、逆序删除等破坏顺序操作，仅用于渲染列表所展示，
			 可以使用index作为key
#收集表单数据:
	若:<input type = 'text'/>则v-model收集的是value值，用户输入的就是value值
	若:<input type = 'radio'/>则v-model收集的是value值，且要给标签配置value值
	若:<input type = 'checkbox'/>
		1:没有配置input的value属性，那么收集的就是checkbox(勾选or未勾选,是布尔值)
		2:配置input的value值:
			(1):v-model的初始值是非数组，那么收集的就是checkbox(勾选or未勾选,是布尔值)
			(2):v-model的初始值是数组,那么收集的就是value组成的数组
	备注:v-model的三个修饰符:
		lazy:失去焦点再收集数据
		number:输入字符转换为有效的数字
		trim:输入首尾空滤
#过滤器
	过滤器定义:对要显示的数据进行特定格式化后再显示(适用于一些简单逻辑的处理)
	语法:
		1.注册过滤器:Vue.filter(name,funtion(){ }) (全局配置，必须写在vm前)
		  局部配置 new Vue({ filters:{}})
		2.使用过滤器:{{xxx|过滤器名}}或v-bind:属性="xxx|过滤器名"
	备注:
		1.过滤器也可以接收额外参数、多个过滤器也可以串联
		2.并没有改变原来的数据,是产生新的对应的数据
##Vue的生命周期:
	生命周期:
		1.又名:生命周期回调函数、生命周期函数、生命周期钩子
		2.是什么:Vue在关键时刻帮我们调用的一些特殊名称的函数
		3.生命周期函数的名字不可更改,但函数的具体内容是程序员根据需求编写的
		4.生命周期函数中的this指向是vm或组件实例对象
	常用的生命周期:
		1.mounted:发送Ajax请求,启动定时器、绑定自定义事件、订阅信息等[初始化操作]
		2.beforeDestroy:清除定时器、解绑自定义事件、取消订阅信息等[收尾工作]
	关于销毁Vue实例:
		1.销毁后借助Vue开发者工具看不到任何信息
		2.销毁后自定义事件会失效,但原生DOM事件依然有效
		3.一般不会在beforeDestroy操作数据,因为即使操作数据,也不会再触发更新流程了
	将要创建 ===> 调用beforeCreate
	创建完毕 ===> 调用created
	将要挂载 ===> 调用beforeMount
	挂载完毕 ===> 调用mounted          ！！！
	将要更新 ===> 调用beforeUpdate
	更新完毕 ===> 调用updated
	将要销毁 ===> 调用beforeDestroy    ！！！
	销毁完毕 ===> 调用destroyed
		特有的
	激活    ===>  调用activated
	失活    ===>  调用deactivated
##Vue组件
	Vue中使用组件的三大步骤:
		1.定义组件(创建组件)
		2.注册组件(局部,全局)
		3.使用组件(写组件标签)
	一.如何定义一个组件:
		使用Vue.extend({})基本和vm一样,区别有:
		1.不能写el,因为所有的组件最后都要经过vn的管理,由vm中的el决定
		2.data必须写成函数式,避免组件被复用,数据存在引用关系
		备注:使用templates可以配置组件结构
	二.如何注册组件
		1.局部注册(new Vue({ components:{'组件名':组件}})) 常用
		2.全局注册Vue.component('组件名',组件)
	三.编写组件标签
		<组件名></组件名>
	注意:每次调用Vue.exted放回的都是一个全新的VueCompontent
	VueCompontent简称vc   new Vue 简称vm
	关于this指向:
		1.组件配置中:
			data()函数、methods中的函数、watch中的函数、computed中的函数 它们的this都是vc
		2.vm配置中:
			data()函数、methods中的函数、watch中的函数、computed中的函数 它们的this都是vm
	重要的内置关系:
		1.VueCompontent.prototype.__proto__===Vue.prototype
			prototypr 显示原型属性
			__proto__ 隐式原型属性
			prototypr与__proto_指向同一个原型对象
		2.让组件实例对象(vc)可以访问到vue原型上的属性、方法
#关于不同版本的Vue
	1.vue.js与vue.runtime.xxx.js的区别:
		(1).vue.js是完整版的vue,包含:核心功能+摸板解析器
		(2).vue.runtime.xxx.js是运行版本的vue,只包含:核心功能:没有摸板解析器
	2.是因为vue.runtime.xxx.js没有摸板解析器,所以不能使用template配置项,需要使用
	  render函数接收到的createElement函数去指定具体内容
##脚手架结构
	|——node_modules
	|——public
	|	|——favition.ico:页签图标
	|	|——index.html:主页面
	|——src
	|	|——assets:存放静态资源
	|	|	|——logo.png
	|	|——component:存放组件
	|	|	|——HellWorld.vue
	|	|——App.vue:汇总所有组件
	|	|——main.js:入口文件
	|——.gitignore:git版本管理忽略的配置
	|——babel.config.js:babel的配置文件
	|——package.json:应用包配置文件
	|——README.md:应用描述文件
	|——package-lock.json:包版本控制文件
	|——vue.config.js:vue默认配置文件(不建议去修改)
#vue.config.js配置文件
	使用vue inspect >output.js 可以查看vue脚手架的默认配置
	使用vue.config.js可以对脚手架进行个性化定制  (可查看vue.cli官网，但不建议修改)
#ref属性
    1.被用来给元素或子组件注册引用信息(替代id)
    2.应用在html标签上获取的是真实DOM元素，应用在组件标签上是组件实例对象(vc)
    3.使用方式:
        打标识 `<h1 ref="xxx"></h1>`或者
            	   `<school ref = "xxx"/>`
        获取 this.$refs.xxx
##配置项props
    功能:让组件接收外部传过来的数据
        1.传递数据: 
            <Demo name="xxx"/>
        2.接收数据:
            (1):props:['name'] (只接收)
            (2):props:{
                    name：String
                } (可以限制类型)
            (3):props:{
                    name:{
                        type:String,  (类型)
                        required:true, (必要属性)
                        default:'xx'  (默认值)   
                    }
                }
    备注:props是只读的,Vue底层会监测你对props的修改,如果进行了修改,就会发出警告,
		若业务需求确需要修改,那么请复制props的内容到data中一份,然后去修改data中的数据。
#mixin混入
	功能:可以把多个组件公用的配置提取成一个混入对象
	使用方法:
		1:定义混合:
			{
				data(){...},
				methods:{...},
				...
			}
		2:使用混入:
			(1):全局混入:Vue.mixin(xxx)
			(2):局部混入:mixin:['xxx']
#插件
	功能:用于增强Vue
	本质:包含install方法的一个对象,install的第一个参数是Vue,第二个参数是参数使用者传递的数据
	定义插件:
		对象.install = function(Vue,option){
			1.添加全局过滤器
			Vue.filter(....)
			2.添加全局指令
			Vue.directive(....)
			3.配置全局混入
			Vue.mixin(....)
			4.添加实例方法
			Vue.prototype.$myMethod = function(){....}
			Vue.prototype.$myProperty = xxxx
		}
	使用插件Vue.use()
#scoped样式
	作用:让样式在局部生效,防止冲突
	写法:<style scoped>
##webStorage存储
	1.存储内容大小一般支持5MB左右(不同浏览器可能不一样)
	2.浏览器端通过Window.sessionStorage和Window.localStorage属性实现本地存储机制
	3.相关api:
		(1).xxxxStorage.setItem('key',value) 把键值对添加到存储中,如果已经存在相同的则会覆盖
		(2).xxxxStorage.getItem('person') 返回键名对应的值
		(1).xxxxStorage.removeItem('key') 删除一个键值对
		(1).xxxxStorage.clear() 清空存储的数据
	4.备注:
		(1).SessionStorage存储的内容会随着浏览器窗口关闭而消失
		(2).LocalStorage存储的内容，需要手动清除才会消失
		(3).xxxxStorage.getItem('xxx') 如果xxx的内容获取不到,则getItem返回的值为null
		(4).JSON.parse(null)的结果依然是null
#组件的自定义事件
	1.一种组件通信的方式,适用于:子组件===>父组件
	2.使用场景:A是父组件,B是子组件,B想给A传数据,那么就要在A中给B绑定自定义事件(事件的回调在A中)
	3.绑定自定义事件:
		(1).第一种方式,在父组件中:<Demo v-on:xxx="test"/>
		(2).第二种方式,在父组件中
			<Demo ref = 'xxx'/>
			.....
			mounted(){
				this.$refs.xxx.$on('xxx',this.test)
			}
		(3).若想让自定义组件只能触发一次,可以用once修饰符,或$once方法
	4.触发自定义事件:this.$emit('xxx',数据)
	5.解绑自定义事件:this.$off('xxx')
	6.组件上也可以绑定原生DOM事件,需要使用native修饰符
	7.注意:通过this.$refs.xxx.$on('xxx',回调)绑定自定义事件时,回调配置在methods中,要用箭头函数
		   否则this指向会出问题
#插槽
	1.作用:让父组件可以向子组件指定位置插入html结构,也是一种组件通信的方式,适用于父组件===>子组件
	2.分类:默认插槽,具名插槽,作用域插槽
##Vuex
	1.概念:在Vue中实现集中式状态(数据)管理的一个Vue插件,对vue应用多个组件的共享状态进行集中式
		   的管理,也是一种组件通信的方式,且适用于任意组件通信
	2.使用:多个组件需要共享数据时
	3.vuex中一共有五个状态 State  Getter  Mutation   Action   Module 
		(1).State:提供唯一的公共数据源，所有共享的数据统一放到store的state进行储存，相似与data
		(2).Mutation:更改 Vuex 的 store 中的状态的唯一方法是提交 mutation。Vuex 中的 mutation 
					 非常类似于事件：每个 mutation 都有一个字符串的事件类型 (type)和一个回调函数
					  (handler)。这个回调函数就是我们实际进行状态更改的地方，并且它会接受 state 
					  作为第一个参数
		(3).Action ——进行异步操作:Action和Mutation相似，一般不用Mutation 异步操作，若要进行异步
								 操作，使用Action原因：为了方便devtools打个快照存下来，方便管理
								 维护。所以说这个只是规范，而不是逻辑的不允许，只是为了让这个工具
								 能够追踪数据变化而已
		(4).Getter:类似于vue中的computed，进行缓存，对于Store中的数据进行加工处理形成新的数据
		(5).Module:模块化
##路由
    1.理解:一个路由(route)就是一组映射关系(key-value)，多个路由需要路由器(router)进行管理
    2.前端路由key是路径，value是组件。后端路由key是路径，value是函数
	缓存路由组件:
		(1).让不展示的路由保持挂载
		(2).<keep - alive></keep - alive>
##路由守卫
	全局前置:beforeEach
	全局后置:afterEach
	独享守卫:beforeEnter  独享只有前置没有后置
	组件内守卫:
		进入:beforeRouteEnter
		离开:beforeRouteLeave
#路由器的两种工作模式
	1.对于一个url来说,什么是hash值？--#及其后面的内容就是hash值
	2.hash不会包含在http请求中,即:hash值不会带给服务器
	3.hash模式:
		(1).地址中永远带着#,不美观
		(2).若以后将地址通过第三方手机app分享,若app效验严格,则地址会被标记为不合法
		(3).兼容性较好
	4.history模式
		(1).地址干净,美观
		(2).兼容性和hash模式相比略差
		(3).应用部署上线时需要后端人员支持,解决刷新页面服务端404的问题
#路由传递参数
	1.字符串形式
		this.$router.push("/xxx "+this.keyword"?K="+this.keyword.toUpperCase())
	2.摸板字符串
		this.$router.push(`/xxx/${this.keyword}?k=${this.keyword.toUpperCase()}`)
	3.对象写法
		需要namne属性
		this.$router.push({
			name:'xxx',
			params:{
				keyword:this.keyword
			},
			query:{
				k:this.keyword.toUpperCase()
			}
		})
#<router - link>的replace
	1.作用:控制路由跳转时操作浏览器历史记录的模式
	2.浏览器的历史记录有两种写入方式:分别为puch和replace,puch是追加历史记录,replace是替换当前记录。
	  路由跳转时候默认为puch
	3.开启方式 <router - link replace ...></router - link>
#UI组件库
	1.移动端常用UI组件库:
		Vant https://youzan.githup.io/vant
		Cube UI https://didi.githup.io/cube-ui
		Mint UI http://mint-ui.githup.io
	2.pc端常用ui组件库:
		Element UI https://element.eleme.cn
		IView UI https://www.iviewui.com
##编程式路由
	1.编程式路由跳转到当前路由(参数不变),多次执行会抛出NavigationDuplicated警告错误
		解决方案:
			重写push|replace
				第一个参数:告诉原来的参数,往哪里跳转(传递那些参数)
				第二个参数:成功回调
				第三个参数:失败回调
				let originPush = VueRouter.prototype.push
				let originReplace = VueRouter.prototype.replace
				VueRouter.prototype.push = function(location,resolve,reject){
					if(resolve&&reject){
						originPush.call(this,location,resolve.reject)
					}else{
						originPush.call(this,location,()=>{},()=>{})
					}
				}
				VueRouter.prototype.replace = function(location,resolve,reject){
					if(resolve&&reject){
						originReplace.call(this,location,resolve.reject)
					}else{
						originReplace.call(this,location,()=>{},()=>{})
					}
				}
			call和apply区别
				相同点:都可以调用函数一次,都可以篡改上下文
				不同点:call和apply传递参数用逗号隔开,apply方法执行,传递数组
##组件通信的方式
	父与子:props
	子与父:自定义事件,@on @emit
	全局事件总线:$bus  全能
	插槽
	vuex
	pubsub-js:vue基本不用 全能
	1:给原生DOM绑定自定义事件没有任何意义,因为没有办法触发$emit函数
	2:v-model实现原理:value与input事件实现的,而且还需要注意可以通过v-model实现父子组件数据同步
	3:属性修饰符:sync 可以实现父子组件数据同步
	4:$listeners与$attrs 他们两个是组件实例的属性,可以获取到父组件给子组件传递props与自定义事件
	5:$childer 组件实例的属性:可以获取到当前组件的全部子组件[数组]
	
	event深入 v-model深入 属性修饰符sync $attrs与$listeners $childer与$parent 作用域插槽scope-slot
##分页器封装原理
	1.知道当前第几页
	2.知道总数据
	3.知道每一页显示数据的个数  --	由2/3能知道一共分多少页
	4.知道连续的页码数
##Require 和 import
	<require和import的区别>
1.import在代码编译时被加载,所以必须放在文件开头
  require在代码运行时被加载,所以require理论上可以运用在代码的任何地方,所以import性能更好。
2.import引入的对象被修改时,源对象也会被修改,相当于浅拷贝
  require引入的对象被修改时,源对象不会被修改,官网称值拷贝,可以理解为深拷贝。
3.import会触发代码分割（把代码分离到不同的bundle中,然后可以按需加载或者并行加载这些文件,require不会触发。
4.import是es6的一个语法标准,如果要兼容浏览器的话必须转化成es5的语法,require是AMD规范引入方式。

目前所有的引擎都还没有实现import,import最终都会被转码为require,在webpack打包中,
import和require都会变为_webpack_require_。
##路由懒加载
	作用:按需去加载路由对应的资源，提高首屏加载速度。
	原理:将路由相关的组件,不再直接导入了,而是改写成异步组件的写法,
		 只有当函数被调用的时候，才去加载对应的组件内容。
#linux常用指令
	cd:跳转目录
	ls:查看
	mkdir:创建目录
	pwd:查看绝对路径
##nginx
	功能:
		1.正向代理
		2.反向代理
		3.负载均衡
		4.动静分离
	常用命令:
		nginx -t:
			1.显示当前的Nginx配置文件路径
			2.测试当前的Nginx配置是否有问题,如果有问题的话会报出那一行配错的
#nginx面试题
	什么是Nginx？
		Nginx是一个 轻量级/高性能的反向代理Web服务器，他实现非常高效的反向代理、
		负载平衡，他可以处理2-3万并发连接数，官方监测能支持5万并发，现在中国使用
		nginx网站用户有很多，例如：新浪、网易、 腾讯等。
	为什么要用Nginx？
		1.跨平台、配置简单、方向代理、高并发连接：处理2-3万并发连接数，官方监测能
		  支持5万并发，内存消耗小：开启10个nginx才占150M内存 ，nginx处理静态文件好,
		  耗费内存少。
		2.Nginx内置的健康检查功能：如果有一个服务器宕机，会做一个健康检查，再发送
		  的请求就不会发送到宕机的服务器了。重新将请求提交到其他的节点上。
		3.使用Nginx的话还能：
			节省宽带：支持GZIP压缩，可以添加浏览器本地缓存
			稳定性高：宕机的概率非常小
			接收用户请求是异步的
	为什么Nginx性能这么高？
		因为他的事件处理机制：异步非阻塞事件处理机制：运用了epoll模型，提供了一个队列，排队解决
	Nginx怎么处理请求的？
		nginx接收一个请求后，首先由listen和server_name指令匹配server模块，再匹配
		server模块里的location，location就是实际地址
	Nginx的优缺点？
		优点：
			占内存小，可实现高并发连接，处理响应快
			可实现http服务器、虚拟主机、方向代理、负载均衡
			Nginx配置简单
			可以不暴露正式的服务器IP地址
		缺点：
			动态处理差：nginx处理静态文件好,耗费内存少，但是处理动态页面则很鸡肋，
			现在一般前端用nginx作为反向代理抗住压力，
	Nginx应用场景？
		1.http服务器。Nginx是一个http服务可以独立提供http服务。可以做网页静态服务器。
		2.虚拟主机。可以实现在一台服务器虚拟出多个网站，例如个人网站使用的虚拟机。
		3.反向代理，负载均衡。当网站的访问量达到一定程度后，单台服务器不能满足用户的
		  请求时，需要用多台服务器集群可以使用nginx做反向代理。并且多台服务器可以平均
		  分担负载，不会应为某台服务器负载高宕机而某台服务器闲置的情况。
		4.nginz 中也可以配置安全管理、比如可以使用Nginx搭建API接口网关,对每个接口服务进行拦截。
	Nginx虚拟主机怎么配置?
	1、基于域名的虚拟主机，通过域名来区分虚拟主机——应用：外部网站
	2、基于端口的虚拟主机，通过端口来区分虚拟主机——应用：公司内部网站，外部网站的管理后台
	3、基于ip的虚拟主机。
##什么是正向代理和反向代理？
	1.正向代理就是一个人发送一个请求直接就到达了目标的服务器
	2.反方代理就是请求统一被Nginx接收，nginx反向代理服务器接收到之后，
	   按照一定的规 则分发给了后端的业务处理服务器进行处理了
#location的作用是什么？
	location指令的作用是根据用户请求的URI来执行不同的应用，
	也就是根据用户请求的网站URL进行匹配，匹配成功即进行相关的操作。
#Vue3
	reactive函数:
		作用:定义一个对象类型的响应式数据(基本类型不要用它,要用ref函数)
		语法:const(代理对象) = reactive(源对象)接收一个对象或数组,返回一个代理对象(Proxy的实例对象)
		reactive定义的响应式数据是深层次的
		内部基于es6的Proxy实现,通过代理对象操作源对象内部数据进行操作
##vue2和vue3的响应式原理
	v2:
		对象类型:通过Object.definePropety()对属性的读取,修改进行拦截(数据劫持)
		数组类型:通过重写更新数组的一些列方法来实现拦截。
		缺点:
			新增属性、删除属性,界面不会更新
			直接通过下标修改属性,界面不会更新
	v3:
		通过Proxy(代理):拦截对象中任意属性的变化,包括:属性值的读写、属性的添加、属性的删除等。
		通过Refilect(反射):对被代理对象的属性进行操作。
#ref与reactive
	ref:用来定义基本数据类型(也可以定义对象数组类型,但内部会自动通过reactive转为代理对象)
		原理:是通过Object.defineProperty()的get和set来实现响应式(数据劫持)
	reactive:用来定义对象数组类型数据
		原理:通过使用Proxy来实现响应式,并通过Reflect操作源对象内部的数据
#Vue3中的watch函数
	与Vue2的watch配置功能一致
	两个小坑:
		监视reactive定义的响应式数据时:oldValue无法正确获取、强制开启了深度监视(deep配置无效)
		监视reactive定义的响应式数据中某个属性时:deep配置有效
#Vue3中的watchEffect函数
	watch的套路是:既要指明监视的属性,也要指明监视的回调。
	watchEffect的套路是:不用指明监视哪个属性,监视的回调中用到哪个属性,那就监视哪个属性。
	watchEffect有点像computed:
		但computed更注重的是计算出来的值(回调函数返回的值),所以必须要写返回值。
		而watchEffect更注重的是过程(回调函数的函数体),所以不用写返回值。
##vue3的生命周期
	beforeCreate     创建前
	created			 创建完毕
	beforeMount		 挂载之前
	mounted			 挂载完毕
	beforeUpdate	 更新前
	updated			 更新完毕
	beforUnmount	 卸载前
	unmouted		 卸载完毕
#toRaw与markRaw
	toRaw:
		作用:将一个由reactive生成的响应式对象转为普通对象
		使用场景:用于读取响应式对象对应的普通对象,对这个普通对象的所有操作,不会引起页面更新
	markRaw:
		作用:标记一个对象,使其永远不会再成为响应式对象
		使用场景:
			1.有些值不应被设置为响应式的,例如复杂的第三方类库等。
			2.当渲染具有不可变数据的大列表时,跳过响应式转换为可以提高性能。