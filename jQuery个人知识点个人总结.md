
<script>
    //在文档中添加Jq文件  在头部标签引用即可
    //  <script src= "JQ文件名"><|/script>
    //在CDN中加载JQ文件
    //国内CDN
    //百度  src="http://libs.baidu.com/jquery/1.10.2/jquery.min.js"
    //又拍云 src="http://upcdn.b0.upaiyun.com/libs/jquery/jquery-2.0.2.min.js"
    //新浪 src="http://lib.sinaapp.com/js/jquery/2.0.2/jquery-2.0.2.min.js"

    //js创建入口函数  正常情况(有兼容代码可调用多次)下只能调用一次  第2次调用会覆盖前一个入口函数
    window.onload = function () {

    };

    //    应用Jquery的步骤:
    //    1.引入文件
    //    2.创建入口函数  能重复调用 不互相影响
    //    第一种方式 $(function () {
    //
    //    });
    //    第二种方式 $(document).ready(function () {
    //
    //    });

    //解决多库共存的两种方法(主要解决$符号冲突的问题)
    //卸载$符号  使用 新名字 代替$符号
    //  1.   var 新名字 = jQuery.noConflict();
    //  2.   使用jQuery代替$符号    $===jQuery

    //JQ中几乎没有属性  极大部分都为方法
    //JQ获取的元素都 存放在一个伪数组中 唯一一个可用的属性为 length 选定的元素的个数
    //JQ 挂载方法 核心 $.fn.挂载方法名
    //jQuery链式编程同一个对象可以用.符号连接的方式实现多个不同的方法的链式调用
    //例子 $(this).css().slideUp().hide();  从左到右顺序执行
    //中途可以改变对象的指向 通过 find() siblings()等

    //设置和获取属性都为字符串格式
    //属性值在设置时可以为数字格式(默认为单位px)
    //style样式多属性值设置 内部为对象数据格式 可以为连词符格式或者驼峰格式
    $(obj).css({attr1: value1, attr2: value2});
    //style样式只能单属性获取
    //注意: 内部迭代不会获取多个属性值,只会获取第一个元素的属性
    $(obj).css(attr);
    //元素自带属性,自定义属性(与H5最新规则不同 自定义属性可以不带data-头 并且获取时不为驼峰格式)获取及其设置
    $(obj).attr(attr);//获取
    $(obj).attr(attr, value);//设置
    //元素自带属性,表单单个属性获取及其设置 (例如 disabled checked selected readonly)
    $(obj).prop(attr);//获取
    $(obj).prop(attr, true || false);//设置

    //jQuery内置函数
    //隐藏/显示元素(核心display = none/block)
    //双参数 可有可无
    //设置时间参数时(单位为毫秒) 元素沿4个角其中一个(默认左上角)进行缩小 无时间时时间默认为400毫秒 无时间时直接隐藏/显示 时间极小(大概0-16)时 先执行回调函数在进行显示/隐藏操作(与pc硬件有关)
    //callback回调函数 元素完成动作后执行函数
    $(obj).hide(time, callback);//隐藏
    $(obj).show(time, callback);//显示
    $(obj).toggle(time, callback);//显示/隐藏切换

    //淡入/淡出元素(核心opacity属性display = none/block操作)
    //双参数 可有可无
    //设置时间参数时(单位为毫秒) 元素进行在设定时间之内完成操作 无时间时时间默认为400毫秒 时间极小(大概0-16)时 先执行回调函数在进行淡入/淡出操作
    //callback回调函数 元素完成动作后执行函数
    $(obj).fadeIn(time, callback);//淡入
    $(obj).fadeOut(time, callback);//淡出
    $(obj).fadeToggle(time, callback);//淡入/淡出切换
    //动作到指定的不透明度
    $(obj).fadeTo(time, value, 三次贝赛尔曲线, callback);

    //向下滑动/向上滑动元素
    //双参数 可有可无
    //设置时间参数时(单位为毫秒) 元素进行在设定时间之内完成操作 无时间时时间默认为400毫秒 时间极小(大概0-16)时 先执行回调函数在进行向下滑动/向上滑动操作
    //callback回调函数 元素完成动作后执行函数
    $(obj).slideDown(time, callback);//向下滑动
    $(obj).slideUp(time, callback);//向上滑动
    $(obj).slideToggle(time, callback);//滑动切换

    //自定义动画
    //后两个参数可有可无  没有时间参数时默认值为400ms
    //设置时间参数时(单位为毫秒) 元素进行在设定时间之内完成操作 无时间时时间默认为400毫秒 时间极小(大概0-16)时 先执行回调函数在进行向下滑动/向上滑动操作
    //callback回调函数 元素完成动作后执行函数
    $(obj).animate({attr: value}, time, timing-function(三次贝赛尔曲线), callbcak);
    //特殊使用方法
    //第一个参数 属性-值对象 为 {width:"hide||show||toggle"}  滑动隐藏/显示/切换

    //动画停止函数 stop()
    //两个参数可有可无 只有两个值true||false
    //第一个值控制是否停止全部动画
    //第二个值控制是否立刻完成动画
    //一般使用时不用添加参数 直接调用即可
    //$(obj).stop(stopAll,toAnd).动画操作;

    //jQuery各种事件 为js中各种事件名无on 例子  click()
    //必有参数为回调函数
    //$(obj).事件名(callback);
    //特殊 hover()事件 为鼠标移入移出事件 鼠标移入移出都执行函数 没有事件冒泡现象发生
    //当鼠标移动到元素上时，会触发指定的第一个函数(mouseenter);当鼠标移出这个元素时，会触发指定的第二个函数(mouseleave)
    //mouseenter,mouseleave 与 mouseover,mouseout的区别 前者解决了事件委托的问题(谁调用谁应用函数,与子元素无关)
    //jQ的each方法一可以遍历!!!!!任何对象!!!!!!
    //特殊使用方法 obj为任何数据  callback函数有两个参数 第一个参数为 对象的索引值(i) 第二个参数为 每个数据(item)
    //如果想要退出遍历  就输入return false; 退出遍历
    //$.each(obj,callback)  遍历函数 方法一
    //$(obj).each(callback);  遍历函数 方法二

    //可接收返回值 返回值为拓展后的对象
    //将参数对象的值添加到需要拓展的对象中  相同属性名的值就覆盖  原有的属性不动   没有的就添加
    // 改变需要拓展的对象值  参数对象不变
    //静态方法  $.extend(需要拓展的对象,参数对象1,参数对象2...);
    //例子
    //var settings = { validate: false, limit: 5, name: "foo" };
    //var options = { validate: true, name: "bar" };
    //var obj = $.extend(settings, options);
    //结果为
    //obj={ validate:true, limit: 5, name: "bar" };
    //settings={ validate:true, limit: 5, name: "bar" };
    //options = { validate: true, name: "bar" };

    //添加自定义插件时 注意链式编程  最后添加 返回对象 return obj(this);

    //扩展jQuery静态函数的两种方法(放在自调用函数中)
    //第一种方法
    //$.函数名 = function(){};
    //第二种方法  官方推荐 可以一次拓展多个静态函数
    //$.extend({函数名1:function(){},函数名2:function(){}});
    //调用时 都为 $.函数名  注意!!!!同名方法可以被重新赋值被覆盖!!!!!

    //JQ 和 JS 属性和方法不能互相使用
    //JQ对象使用JQ属性和方法 JS对象使用JS属性和方法
    //JQ对象转化为JS对象
    //因为JQ获取的dom元素都存放在一个伪数组中 所以$(ibj)[index]就可以获取相应的js对象
    //JS对象转化为JQ对象
    //在相应的JS的dom对象 加入 $(JS对象) 就可转化为JQ对象 例子 $(window)  $(this)

    //JQ对象中存在隐式迭代 (自带遍历元素)

    //JQ选择器和css选择器语法相同
    //不同为eq()选择器 $(obj).eq(index)为选择对象中索引值为index(从0开始计算)的元素进行相应的操作
    //$(obj:eq(index)) 为选择对象的索引值为index的元素添加style属性
    //:odd   选择奇数位置的元素
    //:even  选择偶数位置的元素
    //注意 JQ中 属性选择器[class=value] 为严格匹配
    //<例子  [class="class"]  匹配不到 <div class="class class1"></div>

    //index()方法 $(obj).index(obj);获取当前元素在当前选择器中的索引值  $(this).index()获取当前元素在文档中相对于其兄弟的索引值

    //.text()  获取/设置双标签元素的内容
    //.html()  获取/设置双标签元素的内容(包含后代元素标签)
    //.val()    获取/设置表单元素的内容(特殊  textarea)

    //节点操作
    //括号中可以传入参数  为选择条件
    //例子 $(ul).children(li[class=list]) 选择ul直接子代中的class为list的所有li元素
    //.parent()     直系父亲
    //.children()   直系儿子
    //.siblings()   直系兄弟(不包含自己)
    //.parents()  祖先
    //.find()    后代
    //.remove()   移除节点自身及其内容(包含后代元素)
    //.empty()    清空节点内容(包含后代元素)
    //.next()   返回后一个兄弟元素
    //.nextAll()  返回后面所有的兄弟元素
    //.prev()   返回前一个兄弟元素
    //.prevAll()  返回前面所有的兄弟元素

    //创建节点的三种方法
    //var str = "<li id='li'>asdasd</li>";
    //$("<li id='li'>asdasd</li>");
    //var str = document.createElement("");

    //parentNode.append(childNode)   添加子元素到内容最后面
    //childNode.appendTo(parentNode)   添加子元素到内容最后面
    //parentNode.prepend(childNode)   添加子元素到内容最前面
    //childNode.prependTo(parentNode)  添加子元素到内容最前面
    //siblingNode.after(添加的元素)      添加元素到内容同级前面
    //siblingNode.before(添加的元素)      添加元素到内容同级后面
    //$(要克隆的元素).clone(true)  参数为true时表示绑定的事件也一起克隆

    //添加一个或多个类 原来有的类不覆盖
    //$('div').addClass('box lei');
    //删除一个或多个类
    //$('div').removeClass('box lei');
    //切换添加或者删除一个或多个类
    //$('div').toggleClass('box lei');
    //判断元素是否有某个类名
    //$('div').hasClass('box');

    //绑定事件的方法
    //.click(function(){});
    //万能事件绑定方法  自带事件委托  可事件委托(给指定的子元素绑定事件  动态添加的相应的子元素也有绑定方法)
    //.on(事件类型,子元素选择器,json数据,事件处理程序);
    //(!!!!!!!!!!!!!!!新版本已废弃!!!!!!!!!!!!!!!!)
    //下面两个不常用  了解即可
    //.bind(事件类型,data数据,事件处理程序);
    //unbind() 相应的解除事件
    //只能做事件委托，子元素选择器不能省略
    //.delegate(子元素选择器,事件类型,json数据,事件处理程序);
    //undelegate() 相应的解除事件

    //万能解绑事件
    //$(解绑事件元素).off(事件名,子代元素,事件执行函数名);

    //例子  事件委托：
    //.father只作委托，真正的事件源其实是.son
    //可以为后面动态创建的元素也可以共享绑定的函数
    //    $('.father').on('click', '.son', {name: "小明"}, function (event) {
    //        console.log(event.data);
    //    });

    //event.pageX  获取鼠标指针相对于浏览器窗口的左上角(0.0)的横坐标
    //event.pageY  获取鼠标指针相对于浏览器窗口的左上角(0.0)的纵坐标
    //event.target 获取当前触发事件的元素(事件源)
    //event.type 获取当前触发事件的名称

    //offset({top:value1,left:value2})  设置或获取被选元素的偏移坐标（相对于浏览器窗口左上角）
    //例子 获取div元素左偏移坐标  $("div").offset().top
    //position({top:value1,left:value2}) 获取元素的偏移坐标(相对于已有定位的最近祖先元素）
    //返回相对自己的第一个已定位的祖先元素
    //offsetParent()

    //获取或者设置页面向上卷曲的距离
    //.scrollTop()
    //获取或者设置页面向左卷曲的距离
    //.scrollLeft()

    //width()       获取或设置元素的宽(不包含padding 和 border)
    //height()      获取或设置元素的高(不包含padding 和 border)
    //innerWidth()  获取或设置元素的宽(包含padding 不包含border)
    //innerHeight() 获取或设置元素的高(包含padding 不包含border)
    //outerWidth()  获取或设置元素的宽(包含padding 和 border)
    //outerHeight() 获取或设置元素的高(包含padding 和 border)
    //outerWidth(true)  获取或设置元素的宽(包含padding 和 border和margin)
    //outerHeight(true) 获取或设置元素的高(包含padding 和 border和margin)

    //属性值为boolean类型  禁用后不是不动  就是省略了过度效果
    //jQuery.fx.off = true/false  对所有动画进行全局禁用或启用

