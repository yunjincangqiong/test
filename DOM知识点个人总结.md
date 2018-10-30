
    <script>
        //DOM中页面中有一个顶级对象:Document
        //事件:三要素:事件源,触发,响应
        //推荐使用value属性设置和获取文本域标签textarea的内容
        //select元素的value值,只能获取第一个选中的项的 value 值;即使存在multiple属性,获取的也只是选中的第一个项的 value 值; 没有选中项时获取的是空字符串
        
        //偶数(even),用户看到的是奇数;奇数(odd),用户看到的是偶数

        //特性( attribute )和属性 ( property )
        //特性指元素标签中自带或者全局的属性
        //属性指元素的css属性
        //日常中都叫属性, 但一定要有所区分
        
        //DOM-CORE
        //可以操作所有的标记语言
        //元素.setAttribute("自定义属性/属性名字","值"); 设置标签的属性或者自定义属性及值
        //元素.getAttribute("自定义属性/属性名字");获取标签的属性或者自定义属性的值
        //元素.removeAttribute("自定义属性/属性名字"); 移除某个标签的属性或者自定义属性
        //以上操作添加或者移除都直接显示在元素开始标签上
        //HTML-DOM
        //只适用于HTML文档
        //用点的方式操作元素对象,只能操作元素标签自带的属性(可读写)
        //用点的方式添加自定义属性,控制台标签上不显示自定义属性;相当于为元素对象添加新的对象属性
        
        //设置或获取双标签中的纯文本内容可以使用innerText,textContent,还可以使用innerHTML
        //但是,innerText和textContent有兼容问题,所以,可以使用兼容代码或者innerHTML
        //=========注意:如果标签中只有文本,推荐使用innerHTML=======
        //设置或获取标签中的html标签及文本,用innerHTML
        //设置成对的标签中间的文本内容应该使用:textContent,这是标准写法
        //谷歌和火狐支持textContent,IE8不支持
        //innerText目前,谷歌,火狐,IE8都支持
        //除了兼容性问题,textContent和innerText属性获取的换行和空格的文本也不同

        //快捷访问(可读写)
        //document.title---->获取或者设置的是title标签中的值(!!字符串!!)
        //document.body----->获取或者设置body标签对象
        //document.documentElement----->获取或者设置html标签对象
        //document.head---->获取或者设置head标签对象

        //    定时器
        //    指定时间间隔循环执行
        //    var timer = setInterval(fn,时间(ms));
        //    clearInterval(timer);
        //    指定时间后执行(只执行一次)
        //    var timer = setTimeout(fn,时间(ms));
        //    clearTimeout(timer);
        //参数1:函数  参数2:时间---毫秒 无单位
        //返回值:该定时器的id(第1个返回数字1,第2个返回数字2...)
        //!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
        //执行过程:页面加载后,过了第二个参数毫秒后才执行函数中的代码
        //使用完成后清除定时器, 防止内存泄露

        //name属性和id属性区别?name属性为了将来向后台提交表单数据使用的,name属性值可以重复
        // 强调表单元素必须含有 name 属性, 否则传输数据时会传递失败此字段的值
        //如果元素标签中的这个属性和值,都是自己,并且只有一个,此时在js代码的DOM操作中值就是布尔类型,  判断选择时  checked=true 方式
        //checked,selected,disabled...

        //  根据id属性
        //  document.getElementById("id属性的值");返回一个对象;获取不到返回null
        //  根据标签名字
        //  document/tagName.getElementsByTagName("标签的名字");返回一个伪数组;获取不到返回空伪数组
        //  获取应用了class类样式的标签--h5中的
        //  document/tagName.getElementsByClassName("类样式的名字");返回一个伪数组;获取不到返回空伪数组
        //  根据name属性的值来获取元素,常用于表单元素选择中(存在兼容性问题一般不使用) IE里面还会获取到同名的id元素
        //  document/tagName.getElementsByName("name属性的值");返回一个伪数组;获取不到返回空伪数组
        //  根据css选择器的方式来获取--h5中的
        //  支持tagName选择 但是内部实现有问题 所以不推荐使用 
        //  document.querySelector("css选择器");返回一个元素对象;获取不到返回null
        //  document.querySelectorAll("css选择器");简称qsa方法;返回一个伪数组;!!支持forEach方法!!;获取不到返回空伪数组

        //JS中设置或获取元素的样式格式  对象.style.属性名 只能获取元素行内样式 默认值为空字符串
        //对象.style.属性="";时 恢复属性原来的默认值或者设定值
        //window.getComputedStyle( 元素 ).属性  获取元素样式(行内, 外链都可以获取)
        //凡是在css属性中,属性名字是多个单词组合,中间用-隔开的,在js代码DOM操作中,把-去掉,后面单词的首字母变大写(驼峰格式);例: ele.backgroundColor
        //兼容写法
        // 元素对象.style.属性 || window.getComputedStyle( 元素对象 ).属性
        // 注意个别时候获取的属性可能存在有无单位差别

        //阻止a标签跳转 return false; 或者 <a href="javascript:void(0); / javascript:;"></a>
        //javascript: 伪协议,不同于http https ftp 等真协议, 此伪协议只能用于执行js代码;但是不建议使用伪协议
        
        // 元素创建的三种方式
        //如果是在页面全部加载完毕后通过document.write()方式创建元素或者输出数据,会把页面中所有的内容全部覆盖掉
        // 1.document.write();
        // innerHTML的方式会覆盖调用该方法的对象的全部内容
        // 2.对象.innerHTML= 带元素节点的字符串/字符串/变量;
        // 3.document.createElement("标签名字");
        // 文本节点创建
        // document.createTextNode(文本);

        //keypress和keydown的区别 (同为键盘按下事件)
        //keypress只能识别正常键位(包括回车)
        //keydown能识别除正常键位的特殊键位(例如退格键和上下左右键)

        // 引用类型使用 == 或 === 比较时;比较的都是地址
        // [] == [] //false  {} == {} //false  (function(){} == function (){}) //false

        //对象.addEventListener("事件类型", 事件处理函数[, false]);
        /*
         * 参数1:事件类型----事件名字----名字是没有on(标准写法)
         * 参数2:事件处理函数---函数--可以是命名函数,也可以是匿名函数
         * 参数3:false------默认值 (事件冒泡阶段)
         *
         * addEventListener()谷歌和火狐都支持,这是标准写法,IE8不支持,IE11支持
         *
         * 对象.attachEvent("on+事件类型",事件处理函数)
         * 参数1:事件类型---事件名字---有on
         * 参数2:事件处理函数
         * IE11不支持此方法
         * 对象.attachEvent()谷歌和火狐都不支持,IE8支持
         *
         * 为元素绑定事件三种方式:
         * 1 对象.on+事件类型=事件处理函数
         * 例子:  my$("btn").onclick=function(){};
         * 事件处理函数:可以是命名函数,
         * 2 对象.addEventListener("事件类型",事件处理函数,false);
         * 例子: my$("btn").addEventListener("click",function(){},false);
         * 3 对象.attachEvent("on"+事件类型,事件处理函数);
         * 例子: my$("btn").attachEvent("onclick",function(){});
         *attachEvent只支持事件冒泡
         *如果使用attachEvent对一个元素的目标阶段(相当于对同一个元素)绑定了多次同一个事件，那么会按照绑定顺序的相反顺序进行触发
         *
         * 为元素解绑事件三种方式
         * 1 对象."on"+事件类型=null;
         * 例子: my$("btn").onclick=null;
         * 2 对象.removeEventListener("事件类型",事件处理函数名,false);
         * 例子: my$("btn").removeEventListener("click",f1,false);
         * 3 对象.detachEvent("on"+事件类型,事件处理函数名字);
         * 例子:l my$("btn").detachEvent("onclick",f1);
         * 这里的this是window对象
         * 最后:用什么方式绑定事件,就用对应的方式解绑事件
         *
         *  绑定和解绑样例: ele.addEventListener( 'click', fn =function(){}); ele.removeEventListener( 'click', fn );
         * 
         //事件冒泡:元素A中嵌套了另一个元素B,都注册了相同的事件click,如果里面的元素B的事件触发了,那么外面的这个元素A的事件也会被触发.
         //阻止事件冒泡:
         //事件处理函数中的参数e---事件参数对象  兼容写法 : e=window.event||e;
         my$("dv3").onclick=function (e){
             window.event;
             e;
         }
         //e.stopPropagation();//标准写法--谷歌支持,火狐支持,IE8中不支持
         //阻止事件冒泡继续向上传递;但是当前函数会执行完毕;不受e.stopPropagation() 代码所在行数影响;
         //IE8没有事件参数对象 IE8中window.event------就是事件参数e
         //window.event.cancelBubble=true;//IE8支持,谷歌也支持,火狐不支持
         //阻止事件冒泡兼容写法
         if(!window.event){
            e.stopPropagation();
         }else{
            window.event.cancelBubble = true;
         }
         /*
         * 事件的三个阶段:
         * 1.捕获阶段：从外向内 window->document->body->div
         * 2.目标阶段 button
         * 3.冒泡阶段: 从内向外 div->body->document->window
         *
         * addEventListener(参数1,参数2,参数3);
         * 参数3:是什么阶段触发函数,
         * false:默认是冒泡阶段
         * true:捕获阶段
         * 事件参数对象.eventPhase:值:三个:
         * 值:
         * 1----捕获阶段
         * 2----目标阶段
         * 3----冒泡阶段
         * eventPhase可以知道当前事件到底是什么阶段触发的
         *
         * 事件冒泡和事件捕获不可能同时发生;
         *
         * */
        //        my$("dv1").onclick=function (e) {
        //            //console.log(e.type);//触发该事件的事件类型---事件的名字,没有on
        //            //console.log(e.target);//事件源对象--谷歌和火狐
        //            //console.log(window.event.srcElement);//事件源对象---IE8写法
        //            事件源对象:点那个元素就是那个元素
        //            //console.log(e.currentTarget);//当前触发该事件的对象-->冒泡阶段一般都是被动触发的外层元素
        //        };


        //为同一个元素,注册多个不同的事件,指向的是同一个事件处理函数并实现不同的行为
        //        my$("btn").onclick=f1;
        //        my$("btn").onmouseover=f1;
        //        my$("btn").onmouseout=f1;
        //        function f1(e) {
        //            //e.type===事件类型(没有on)
        //            switch (e.type){
        //                case "click":this.style.fontSize="30px";break;
        //                case "mouseover":this.style.backgroundColor="deeppink";break;
        //                case "mouseout":this.style.backgroundColor="";break;
        //            }
        //        }

        //event.keyCode获取键盘按键的键码
        //非文本框只有window, documentElement, document 和 body 能获取键盘键码

        //用户按下鼠标时候,判断用户是否按下鼠标(左右键均可)的同时也按下了其他的键(alt,shift,control)
        //        my$("txt").onkeyup=function (e) {
        //            console.log(e.keyCode);//返回按下键盘键的对应键值(ASCLL码值)
        //        };
        //        my$("dv").onmousedown=function (e) {
        //            if(e.altKey){
        //                console.log("按下alt键同时和按下鼠标了");
        //            }else if(e.shiftKey){
        //                console.log("按下shift键同时和按下鼠标了");
        //            }else if(e.ctrlKey){
        //                console.log("按下ctrl键同时和按下鼠标了");
        //            }else{
        //                console.log("只按下了鼠标");
        //            }
        //        };

        // 文本框注册事件是大多使用keyup事件,防止按住键盘不松开多次触发keydown事件

        /*
         * 总结:
         * offset系列中的属性获取的值都是数字类型的
         * offsetWidth:获取的是元素自身的宽度(含border,padding)
         * offsetHeight:获取的是元素自身的高度(含border,padding)
         * offsetLeft:获取的是元素距离最近的定位祖先元素content左边位置的值(子元素脱标,相当于根据body content左上角定位)
         * offsetTop:同offsetLeft
         * offsetParent---距当前元素最近的已定位的祖先元素
         * */
        /*
         *
         * 
         * scroll:卷曲
         * scroll系列中的值都是数字类型
         * scrollHeight:元素内容实际的高度,不包含边框,如果内容超过盒子的高度(多出部分会产生滚动条),超出的部分也算作高度
         * scrollWidth:元素内容实际的宽度,不包含边框,如果内容超过盒子的宽度(多出部分会产生滚动条),超出的部分也算作宽度
         * scrollTop: 元素内容向上卷曲出去的距离
         * scrollLeft: 元素内容向左卷曲出去的距离
         * 以下为 IE 写法
         * window.pageXOffset: 元素内容向上卷曲出去的距离
         * window.pageYOffset: 元素内容向左卷曲出去的距离

         * client系列中的值都是数字类型
         * clientWidth: 获取的是元素(可视区域的)宽度,不包含边框
         * clientHeight: 获取的是元素(可视区域的)高度,不包含边框
         * clientLeft: 左边边框宽度
         * clientTop: 上面边框宽度
         
         * 事件参数对象坐标属性
         * client: 客户端
         * e.clientX  e.clientY
         * 相对于浏览器显示内容区域左上角的横纵坐标
         
         * page: 页面  存在兼容问题
         * e.pageX  e.pageY  火狐支持     e.x  e.y   IE支持
         * 相对于页面主体(document)左上角的横纵坐标(包含卷曲出页面的部分)

         * screen 屏幕
         * e.screenX  e.screenY
         * 相对于电脑屏幕的左上角的横纵坐标

         * offset: 偏移  存在兼容问题 火狐不支持 ie支持
         * e.offsetX  e.offsetY  
         * 相对于触发事件的容器的padding的左上角的横纵坐标
         * 特殊: 鼠标在border中可以获得负值坐标
         * 问题: 如果触发元素中有子元素,则在鼠标进入子元素时获取的是子元素的offset坐标

         * layer: 层  存在兼容问题 火狐支持 ie不支持
         * e.layerX  e.layerY
         * 相对于触发事件的容器的border的左上角的横纵坐标
    </script>


<script>
    //特殊<!DOCTYPE html><html>, <html><head> 和 </body></html> 标签之间的空白不算节点
    // document有两个子节点 <!DOCTYPE html> 和 html 元素 
    //节点(node):页面中所有的内容都是节点(标签,属性,注释,文本(文字、空行、空格、空白))
    //元素(element):页面中的标签
    //文档:(x)html文件或者xml文件
    //根元素(:root):html文档中的是 html 标签
    //下面的三个属性都是节点的属性
    //nodeType属性:节点的类型----值:1---标签节点,2---属性节点,3---文本节点 拓展: 一共16种类型 常用的就两种
    //nodeName属性:节点的名字----值:
    //如果这个节点是标签,值就是:大写标签名字,如果这个节点是属性:值就是:小写的属性名字,如果这个节点是文本,这个值就是#text
    //nodeValue属性:节点的值:如果是标签,这个值是null,如果是属性,这个值是属性的值,如果是文本,这个值是文本的内容
    //特殊tagName 标签名字 返回值为大写的标签名字
    //node:节点
    //element:元素

    //创建文本碎片 作用:用于在文档中添加大量的元素 创建出的元素跟文档元素没有任何区别
    //document.createDocumentFragment();
    //使用 赋值给变量 将创建的大量节点添加到变量中 然后一次性添加到文档中 好处: 对页面只进行一次渲染, 减少性能消耗
    //样例:
    //var oFragment = document.createDocumentFragment();
    //var p = document.createElement("p");
    //var text = document.createTextNode('asd');
    //p.appendChild(text);
    //oFragment.appendChild(p);
    //document.body.appendChild(oFragment);

    //节点操作
    //追加
    //父元素.appendChild()
    //插入
    //父元素.insertBefore('新节点','目标节点')
    //移除
    //父元素.removeChild('目标节点')
    //替换
    //父元素.replaceChild('新节点','目标节点')
    //克隆(不会克隆绑定的事件)返回克隆的节点
    //参数为true时返回克隆当前节点及其所有子节点
    //参数为false时只克隆当前节点
    //克隆节点.cloneNode(true)
    //获取元素的所有子节点
    //父元素.childNodes
    //父元素.childNodes[0] 获取第一个子节点
</script>
<!--=====================-->
<!--十二个对节点的操作-->
<ul id="uu">
    <li>第一个</li>
    <li>第二个</li>
    <li id="three">第三个</li>
    <li>第四个</li>
    <li>第五个</li>
</ul>
<script>
    //ul的父级节点
    console.log(my$("uu").parentNode);
    //ul的父级元素
    console.log(my$("uu").parentElement);
    //ul的所有子级节点
    console.log(my$("uu").childNodes);
    //ul的所有的子元素
    console.log(my$("uu").children);
    //ul中第一个子节点
    console.log(my$("uu").firstChild);
    //ul中第一个子元素
    console.log(my$("uu").firstElementChild);
    //ul中最后一个子节点
    console.log(my$("uu").lastChild);
    //ul中最后一个子元素
    console.log(my$("uu").lastElementChild);
    //某个li的前一个兄弟节点
    console.log(my$("three").previousSibling);
    //某个li的前一个兄弟元素
    console.log(my$("three").previousElementSibling);
    //某个li的后一个兄弟节点
    console.log(my$("three").nextSibling);
    //某个li的后一个兄弟元素
    console.log(my$("three").nextElementSibling);

    //总结:获取节点的代码,谷歌是获取节点,获取元素的代码,谷歌是获取元素
    //但是,到了IE8中,获取节点的代码是获取元素,获取元素的代码,ie8不支持此种语法,返回值为undefined

</script>

