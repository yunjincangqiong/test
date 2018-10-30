
    基本类型 number string boolean undefined null
    基本包装类型 Number Boolean String(特殊 字符串调用方法时自动转换成string对象 结束后销毁string对象)
    型如 var num = new Number(10); var bool = new Boolean(true);
    var str = new String("6666");
    一般不使用基本包装类型, 一方面会产生歧义, 另一方面书写不方便
    var flag = new Boolean(false); console.log( flag === false )// false
    复杂类型 Object Array Math Function Date RegExp

    typeof 返回的值的类型有 number string boolean undefined object function es6添加新的类型 symbol 标识符

    特殊:两个包含着完全相同的字符并且字符排列书序也相同的两个字符串是完全相同的 
    例如: "a"+"bc" === "abc"  // true

    // == 与 === 的区别
    // == 与 === 在比较的时候与左右两边的数据类型是有关系的
    // 1> 基本类型与基本类型
    //  == 会对数据进行转换, 再进行比较
    //  === 会先比较类型, 然后再比较值

    // 2> 引用类型与引用类型
    //  无论是 == 还是 === 都比较的是地址

    // 3> 引用类型 与 基本类型
    //  == 会将引用类型转换成 基本类型 再比较
    //  === 永远为 false

    <!--  || 和 && -->
    都存在逻辑中断 ||: 只要左边为true;右边不计算直接返回左边的值或表达式 例: 1||2  // 1
    &&: 只要左边为false;右边不计算直接返回左边的值或表达式 例: 0&&2  // 0
    // 注意逻辑运算不是强制转换数据为boolean类型,只在判断true or false 时强制转换数据用于判断;并不会改变原数据

    函数的声明式和表达式
    声明式: function 函数名(){ 函数体 }
    声明形态的特征是一个 在全局范围 或 在某一个函数内 的顶级语法层实现;顶级语法层, 独立与其他任何代码
    声明式形态在声明时不可以直接调用
    注意一下,不允许放到 if, 循环等结构中( 浏览器兼容性 )
    表达式: 是放在一条语句中的 函数形式的语法;一般放在一个圆括号内, 或一段运算式的结构中
    例如: (function [函数名](){})();或者 var fn = function [函数名](){};
    表达式形态在声明时可以直接调用

    两边只要有一个是字符串，那么+就是字符串拼接功能
    1. undefined
    1.1变量只声明不赋值的时候值默认是undefined;
    1.2数组未赋值元素也为undefined;
    1.3函数没有返回值时 输出也是undefined;
    1.4获取一个对象上不存在的属性;

    2. null表示一个空，变量的值如果想为null，必须手动设置
        DOM核心获取元素对象方法获取不到时, 返回null;
    3. Boolean： true和false，区分大小写
        - 计算机内部存储：true为1，false为0

    <script>
        var a = 1;
        var aa = "1";
        var b = "str";
        var c = true;
        var d;
        var e = null;
        console.log(b + c);//strtrue
        console.log(b + d);//strundefined
        console.log(b + e);//strnull
        //字符串与数字进行加法计算时为字符串连接
        console.log(a + aa);//11
        //字符串与数字进行除加法之外的计算时为正常数字计算
        console.log(a - aa);//0
        //boolean类型或null类型参与计算时当隐式转换为数字计算
        //null = 0 ; true = 1 ; false = 0;
        //undefined与非字符串计算时(+ - * / %)结果为NaN
        console.log(a + c);//2
        console.log(a + d);//NaN
        console.log(a + e);//1
        console.log(c + d);//NaN
        console.log(c + e);//1
        console.log(d + e);//NaN
    </script>

    switch 语句在比较值时使用的是全等操作符, 因此不会发生类型转换

    转换为true 非空字符串 非0数字 true 任何对象
    转换成false 空字符串("") 0 -0 false null undefined NaN


    break:立即跳出当前所在循环，break后面的代码不执行,即当前所在循环结束，开始执行循环体后面的内容
    continue:立即停止执行当前循环，开始下一次循环（跳到i++的地方）

    for语句代码执行顺序 语句1->语句2->函数体->语句3->语句2->函数体->语句3......
    for(语句1;语句2;语句3){
        函数体;
    }

    /**
    *不同script标签中的同名函数不互相影响
    *第二个函数相当于重新赋值
    */
    <script>
        function f1() {
            console.log("哇塞");
        }

        f1();//哇塞
    </script>
    <script>
        f1();//哦买噶的

        function f1() {
            console.log("哦买噶的");
        }
    </script>


    /*
    *两个变量交换值
    */
    <script>
        var m = 1;
        var n = 2;
        //[m,n]=[n,m];第一种
        //n = [m, m = n][0];//第2种
        var x = [m, m = n][0];
        var y = [m, m = n][1];
        console.log(x);//1
        console.log(y);//2
        //console.log(m, n);
        //第三种
        //^为按位异或操作符
        m = m ^ n;
        n = m ^ n;
        m = m ^ n;
        //第四种
        m = m + n;
        n = m - n;
        m = m - n;
        //第五种
        var temp = m;
        m = n;
        n = temp;
    </script>


    /*
    *函数的自调用:函数在定义的时候直接调用 立即执行
    自调用函数:特点:一次性的, 单独作用域
    * */
    <script>
        //格式  (函数)() 或者 (函数())
        //又名  沙箱 黑盒 环境
        (function () {
            console.log("日照香炉生紫烟,一对情侣在林间...嘿嘿");
        })();
    </script>


    <script>
        function add(x, y) {
            var sum = x + y;
            //情况一 没有return
            //return; 情况二 有return 无返回值
            //情况三 return和返回值没在同一行
            return//相当于自动添加;
            100;//是没有返回值的
        }

        var result = add(10, 20);
        console.log(result);//undefined
    </script>


    /*
    *//函数可以作为另一个函数的参数使用
    ---->结论(回调函数(作为参数的函数就是回调函数))
    *
    */
    <script>
        function f2(x, y) {
            return x - y;
        }

        function ff(x, y, fn) {
            //fn是一个函数.fn();函数的调用,fn(x,y)--->调用的时候传入的参数
            return fn(x, y);
        }

        var result = ff(10, 20, f2);
        console.log(result);
    </script>


    /*
    *定义函数的形参个数和调用函数的实参个数,不一致,可以执行.
    *形参数多于实参数 多余的形参数为undefined(相当于定义变量未赋值);
    *实参数多于形参数 多余的实参忽略;但是可以在 arguments 中拿到
    */


    <script>
        //隐式全局变量 在函数f1调用之后可以被获取(内存中有此数)
        //没调用f1则报错(number为未定义) 函数预解析只把函数声明提前
        function f1() {
            number = 10000;
        }

        f1();
        console.log(number);
    </script>


    <script>
        // es6之前只有函数作用域和全局作用域
        // 局部变量:在函数中定义的变量就是局部变量
        // 全局变量:除了函数以外任意的地方定义的变量,都是全局变量
        // 局部变量的使用范围:只能在函数中使用
        // 全局变量的使用范围:在页面的任何位置都可以(声明该全局变量script标签中及其下面的script标签)
        //隐式的全局变量:声明变量,不使用var
        //全局变量一旦定义不可轻易删除 在用户退出浏览器时清除全局变量
        var x = 10;
        y = 100;
        delete x;//把全局变量删除
        delete y;//把隐式全局变量删除
        console.log(x);//10
        console.log(y);//报错未定义

        注意 delete 会删除数组的值 但是不会改变数组的长度
        例: var arr = [1]; delete arr[0]; console.log(arr[0]); // undefined
         console.log(arr.length); // 1
    </script>


    <!--=======js代码的自上向下执行-->
    <script>
        console.log(i);//在上script标签中为报错未定义
    </script>
    <script>
        console.log(i);//在同一script标签中为undefined
        for (var i = 0; i < 9; i++) {

        }
        console.log(i);//i=9
    </script>
    <script>
        console.log(i);//在下script标签中为9
    </script>

    /*
    *面向过程:针对每一步都要清楚,凡事都要亲力亲为,
    要知道细节,注重的是过程
    *面向对象:针对的是一个对象,就是提需求,要结果,注重的是结果
    *面向对象特性:封装,继承,多态----抽象性
    *
    */


    //浏览器能够把页面显示出来,浏览器中有一个js的解析器,可以解析js的代码
    //预解析:在解释代码之前发生的事情 !!!!从上到下依次预解析!!!!
    //变量的预解析:在使用这个变量的时候,会把变量的声明提前到当前所在域(script标签)的最上面,赋值不会提前.这个过程就叫变量的预解析
    //函数的预解析:在调用这个函数的时候,会把该函数的声明(赋值和调用不会提前)提前当前所在域的最上面(变量提升的下面),这个过程,叫函数的预解析
    //预解析的时候,函数中的局部变量的声明会提升到当前函数里面的最上面,不会提升到其他的作用域中
    //预解析的时候,如果有多对的script标签,那么如果函数名相同,预解析的时候相互之间不会受到影响的(相当于变量的重新赋值)


    <script>
        function f1() {
            //可拆解成 var a ; c=9;b=9;a=9;
            //a为局部变量 b c为隐式全局变量
            var a = b = c = 9;
            console.log(a);//9
            console.log(b);//9
            console.log(c);//9
        }

        //f1调用以后 隐式全局变量可以在页面各处使用(此script标签下面的script标签)
        f1();
        console.log(c);//9
        console.log(b);//9
        console.log(a);//报错 未定义
    </script>


    <script>
        var x = 1;
        var y = 0;
        var z = 0;
        var add = function (n) {
            n = n + 1;
            return n;
        };
        y = add(x);//2
        //add被重新赋值
        add = function (n) {
            n = n + 3;
            return n;
        };
        z = add(x);//4
        console.log(y + "," + z);//2,4
    </script>


    //构造函数:就是一个特殊的函数,一般这个函数的名字的首字母是大写的
    //构造函数的目的:主要是为了创建对象
    <script>
        //创建多个对象 方法一 工厂模式
        function createNewObject(name, age) {
            var obj = new Object();
            obj.name = name;
            obj.age = age;
            obj.eat = function () {
                console.log("eat");
            };
            return obj;
        }

        var person1 = createNewObject("wang", 45);
        console.log(person1.name);
        console.log(person1.age);
        person1.eat();
        //======================================
        //创建多个对象 方法二 自定义模式(构造函数模式)
        function Person(name, age) {
            this.name = name;
            this.age = age;
            this.eat = function () {
                console.log("eat");
            }
        }

        //创建一个Person的实例
        var per1 = new Person("wang", 45);
        console.log(per1.name);
        console.log(per1.age);
        per1.eat();
        注意: 使用自定义构造函数时, 一定要带 new 关键字, 否则自定义构造函数的this就会错误的指向window, 并创建出多余的全局变量 
    </script>


    <script>
        //字符串的不可变性:
        //  创建新的字符串都会创建新的内存空间,闲置的字符串会被回收
        //  例: var str = '123'; str[1] = 5; console.log(str) //'123'
        //  
        /* String原型对象内置方法 以下方法均不改变原字符串(对原字符串的副本的操作);
         * .charAt(索引);--->返回的是指定索引位置的字符 找不到返回 空字符串
         * 字符串[索引];同上 找不到 返回undefined
         * .charCodeAt(索引);--->返回的是指定索引位置的字符串的unicode码值 找不到返回NaN
         * .concat("字符串1"[,"字符串2",...]);--->字符串拼接,返回新的字符串
         * .indexOf("要查找的字符串",查找开始位置的索引);返回的是查找匹配的第一个字符的索引值,第二个参数可以省略,找不到则返回-1
         * .lastIndexOf("要查找的字符串",查找开始位置的索引);从后向前找字符串,第二个参数可以省略,
         * 查找开始位置的索引和返回的索引值均为正着数的索引,返回的是查找后匹配的第一个字符串的索引值,找不到则返回-1
         * .slice(开始的位置,结束的索引);返回的是截取后的字符串,截取是只能从左往右截取,包含开始位置的字符串,不包含结束位置的字符串;可以使用负数,字符串尾部索引为 -1 ;
         特殊: '123'.slice(-2,-1)// 2   '123'.slice(-1)// 3
         * .substring(开始的索引,结束的索引);返回的是截取后的字符串,包含开始位置的字符串,不包含结束位置的字符串 (与前者区别主要在参数为负数上 基本用不到)
         * .substr(开始的索引,截取字符串的长度);返回的是截取后的字符串,包含开始位置的字符串,如果只有第一个参数没有第二个参数 则返回截取从开始索引(包括开始索引处)到末尾的字符串
         * .replace("要替换的字符串","替换后的字符串");返回替换后新的字符串
         * .trim()去掉字符串两端的空格,字符串中的空格不能去掉,返回去掉空格的字符串
         * .split("以什么为分割点字符串",想要返回的值的个数);返回的是切割后的字符串的数组,第二个参数可以省略
         * 特殊例子var str = "  1 2 3";console.log(str.split(" "));返回数据为  [" "," ","1","2","3"];
         * .toLocaleLowerCase();转成小写格式
         * .toLocaleUpperCase();转成大写格式
         * 推荐使用上面的方法 兼容性高
         * .toLowerCase();转成小写格式
         * .toUpperCase();转成大写格式
         * */
    </script>


    <script>
        /*Array原型对象内置方法 除了几个特殊的剩下的都对原数组的副本进行操作(不改变原数组数据)
         * Array.isArray(变量或者对象);静态方法,判断是否为数组,返回的是布尔类型(高版本浏览器支持)
         * 关键字 instanceof 判断一个变量是否是某个对象的实例对象(用new关键字声明 特殊:数组和对象用字面量方法也返回true),
         * 返回一个布尔类型值, 用法:变量/值 instanceof 构造函数名(Array, Object,Number,Boolean,String,Function)
         * Object.prototype.toString.call([]); // '[object Array]'
         * .concat(变量,[],...);在原数组后连接数组数据,返回一个新的数组
         *
         * 必须记住的四个 !!!改变原数组的值!!!
         * .push(数据);向数组后追加数据,返回值是追加数据后的数组的长度
         * .unshift(数据);向数组中第一个元素前插入数据,返回值是插入数据后数组的长度
         * .shift();删除数组中的第一个数据,返回值是删除的那个数据
         * .pop();删除数组中的最后一个数据,返回值是删除的那个数据
         *
         * .splice(start,deletecount,item1,item2...);!!!改变原数组的值!!!
         * 参数 : start :指定修改的开始位置（从0计数）。如果超出了数组的长度，则从数组末尾开始添加内容；
         * 如果是负值，则表示从数组末位开始的第几位（从-1计数）。
         *** deletecount(可选) : 整数，表示要移除的数组元素的个数。
         * 如果 deleteCount 是 0，则不移除元素。这种情况下，至少应添加一个新元素。
         * 如果 deleteCount 大于start 之后的元素的总数，则从 start 后面的元素都将被删除（含第 start 位）。
         * 如果deleteCount被省略，则其相当于(arr.length - start)。也就是相当于从start位置处后的所有元素
         *** items(可选) : 要添加进数组的元素,从start 位置开始。如果不指定，则 splice() 将只删除数组元素。
         *** 返回值 : 由被删除的元素组成的一个数组。
         * 如果只删除了一个元素，则返回只包含一个元素的数组。如果没有删除元素，则返回空数组。
         *
         *
         * .reverse();反转数组数据 !!!!!改变原数组的值!!!!!
         * .sort(回调函数或者回调函数名);数组排序,默认为从小到大排序,按照ASCII码值排序 对字母数组进行排序是直调用即可  !!!!!改变原数组的值!!!!!
         * 正向排序回调函数为
         function (a, b) {
            return a - b;
            //return ~~(a > b); 
         }
         反向排序回调函数为
         function (a, b) {
            return b - a;
            //return ~~(a < b);
         }
         * .slice(开始索引,结束索引);截取数组中的数据,返回新的数组,包含开始索引位置处的值,不包含结束索引处的值
         * .indexOf(要查找的数据,开始查找位置的索引);找到了第一个匹配的值,返回值就是索引,找不到就是-1
         * .lastIndexOf(要查找的数据,开始查找位置的索引);倒叙查找,找到了第一个匹配的值,返回值就是索引,找不到就是-1
         * .join("字符串");是把数组每个元素中间加上一个字符串,返回值是字符串
         *
         *  以下方法回调函数均有3个形参 item(每个数组数据) index(索引) array(全部数组数据)
         * .forEach(回调函数),遍历数组元素
         * 以下方法都需要 return 返回数据
         * .filter(回调函数);返回符合回调函数条件的数据组成的新数组
         * .every(回调函数),每个元素都要满足条件才返回true
         * .some(回调函数),至少有一个元素满足条件返回true
         * .map(回调函数),每个元素都要执行一次回调函数,返回操作后的数据
         * */
    </script>


    <script>
        console.log(isNaN("blue"));//true
        //存在隐式类型转换
        console.log(isNaN("666"));//false
    </script>


    <script>
        //基础类型数据是传值
        //核心:对象赋值是赋予引用(地址)
        function Person(name, age, salary) {
            this.name = name;
            this.age = age;
            this.salary = salary;
        }

        function f1(person) {
            person.name = "ls";
            //person 重新赋值 指针改变指向
            person = new Person("aa", 18, 10);
        }

        var p = new Person("zs", 18, 1000);
        console.log(p.name);//zs
        f1(p);
        console.log(p.name);//ls
    </script>


    <script>
        var num1 = 55;
        var num2 = 66;

        function f1(num, num1) {
            num = 100;
            num1 = 100;
            num2 = 100;
            console.log(num);//100
            console.log(num1);//100
            console.log(num2);//100
        }

        f1(num1, num2);
        console.log(num1);//55
        console.log(num2);//100
        console.log(num);//报错
    </script>


    <script>
        var a = 10;
        var b = 20;

        function ff(a, b) {
            var a;//前面已经声明过形参a,b;所以此处声明无效会被忽略
            var b;//前面已经声明过形参a,b;所以此处声明无效会被忽略
            console.log(a);//形参a 20
            console.log(b);//形参b 10
            a = 20;
            b = 10;
            console.log(a);//形参a 20
            console.log(b);//形参b 10
        }

        ff(b, a);
        console.log(a);//全局变量a 10
        console.log(b);//全局变量b 20
    </script>

