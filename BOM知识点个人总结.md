
    <script>
        //BOM:Browser Object Model:浏览器对象模型
        //把一个浏览器看成是一个对象
        //BOM中的顶级对象就是window
        //页面中所有的内容都是window,变量是属于window的,函数也是属于window,对象等都是window的
        //!!!!!!!为了开发方便和维护,window可以省略!!!!!!!!!!

        //内置3个框
        //window.alert(变量/"文本");警告框 返回值是undefined
        //window.prompt("提示文本",默认值);提示框 返回输入的数据(为字符串类型)(默认值可以省略)
        //window.confirm("提示文本");确认框 返回点击的boolean值 确认true 取消false

        //location是window对象下的一个属性,实际上也是一个对象,主要是对浏览器的地址栏做操作
        //获取地址的,设置地址,地址改变,就会跳转,地址保存在历史记录中
        //location.href="https://www.baidu.com";
        //跳转页面了,和location.href是一样的
        //同时会把原来的页面的记录会保存到历史记录中
        //location.assign("https://www.baidu.com");
        //把当前页面的地址,替换成一个新的地址,不会保存到历史记录中
        //location.replace("https://www.baidu.com");
        //常用
        //地址栏上#及后面的内容
        //console.log(window.location.hash);
        //搜索的内容:获取的是?及后面的内容
        //console.log(window.location.search);
        //刷新页面
        //location.reload();
        //不常用
        //主机名字和端口号
        //console.log(window.location.host);
        //主机名字
        //console.log(window.location.hostname);
        //文件的相对路径
        //console.log(window.location.pathname);
        //端口
        //console.log(window.location.port);
        //协议
        //console.log(window.location.protocol);

        //navigator对象是window下的一个属性,主要是获取本地的用户相关信息
        //是不同浏览器的信息
        //console.log(navigator.userAgent);
        //电脑系统的信息
        //console.log(navigator.platform);

        //history对象是window下的一个属性,主要是对历史记录的操作,前进或者是后退
        //想要前进和后退,前提:必须要有历史记录
        //前进
        //history.forward();
        //后退
        //history.back();
        //如果是正数就是前进,负数就是后退; 注意数字为必写参数,否则不触发函数
        //history.go(数字);


        //定时器:两个
        // setInterval(函数,时间);返回的就是定时器id(数字1).对应clearInterval(定时器的id)清理定时器
        //!!!!注意 setInterval第一次执行的时候会等待设定时间过后才会执行相应的代码!!!!!
        // 一次性的定时器---
        //setTimeout(函数,时间);返回的就是定时器id(数字1).对应clearTimeout(定时器的id)清理定时器
        //定时器用完就要清理定时器

        //以上的window属性和方法中的 this 都指向 window

前进后退例子
// <input type="button" value="跳一下" id="btn1"/>
第一个页面
// <input type="button" value="去吧,皮卡丘" id="btn2"/>

    document.getElementById("btn1").onclick=function () {
        // location.href="https://www.baidu.com";  //与下面的效果相同
        location.assign("https://www.baidu.com");
    };
    document.getElementById("btn2").onclick=function () {
        //前进
        history.forward();
    };
</script>

