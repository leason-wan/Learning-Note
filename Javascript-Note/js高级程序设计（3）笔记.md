# javaScript简介
## javaScript实现：
- 核心：ECMAScript
- 文档对象模型：DOM
- 浏览器对象模型：BOM

## ECMAScript
规定了下列组成部分：
- 语法
- 类型
- 语句
- 关键字
- 保留字
- 操作符
- 对象
## ECMAScript兼容
- 支持ECMA-262描述的所有“类型、值、对象、属性、函数以及程序句法和语义”
- 支持Unicode字符标准
- 添加ECMA-262没有描述的“更多类型、值、对象、属性和函数”。
## 文档对象模型（DOM）
- DOM级别
    - DOM1级由两个模块组成：DOM核心和DOM HTML
    - DOM2级引入了下列新模块：
        1. DOM视图：定义了跟踪不同文档视图的接口；
        2. DOM事件：定义了事件和事件处理的接口；
        3. DOM样式：定义了基于CSS为元素应用样式的接口；
        4. DOM遍历和范围：定义了遍历和操作文档树的接口；
    - DOM3级：
        1. 引入了以统一方式加载和保存文档的方法——在DOM加载和保存模块中定义；
        2. 新增了验证文档的方法——在DOM验证模块中定义
- 其他DOM标准
    - 另外几种语言发布了只针对自己的DOM标准（基于XML）：
    1. SVG（可伸缩矢量图）1.0；
    2. MathML（数学标记语言）1.0；
    3. SMIL（同步多媒体集成语言）；
## 浏览器对象模型（BOM）
- BOM只处理浏览器窗口和框架 针对浏览器的JavaScript扩展：
    1. 弹出新浏览器窗口功能；
    2. 移动、缩放和关闭浏览器窗口的功能；
    3. 提供浏览器详细信息的navigator对象；
    4. 提供浏览器所加载页面的详细信息的location对象；
    5. 提供用户显示器分辨率详细信息的screen对象；
    6. 对cookies的支持；
    7. 像XHLHttpRequest和IE的ActiveXObject这样的自定义对象；
## 小结
JavaScript是一种专门为与网页交互而设计的脚本语言，由下列三个不同的部分组成：
    1. ECMAScript，由ECMA-262定义，提供核心语言功能；
    2. 文档对象模型（DOM），提供访问和操作网页内容的方法和接口；
    3. 浏览器对象模型（BOM），提供与浏览器交互的方法和接口；

---

# 在html中使用JavaScript
## 使用<script>元素
<script>的六个属性：
- async：可选。表示应该立即下载脚本，但不应妨碍页面中的其他操作，如下载其他资源或等待加载其他脚本。只对外部脚本文件有效；
- charset：可选。表示通过sec属性制定的代码的字符集。由于大多数浏览器会忽略它的值，因此这个属性很少有人用；
- defer：可选。表示脚本可以延迟到文档完全被解析和现实之后再执行。只对外部脚本有效；
- language：已废弃。原来用于表示编写代码使用的脚本语言，大多数浏览器会忽略；
- src：可选。表示包含要执行代码的外部文件。
- type：可选。可以看成language的替代属性；表示代码使用的脚本语言的内容类型（也称为MIME类型）。默认值为text/javascript;

使用<script>元素方式有两种：
1. 直接在页面中嵌入JavaScript代码；
2. 包含外部JavaScript文件；

注意：
- 不包含defer和async属性，浏览器一般遵循从上至下解释顺序；
- 不要在代码中出现‘</script>’;
- 外部JavaScript文件.js的扩展名不是必须的，为了确保服务器能够返回正确的MIME类型；
- 带有src属性的<script>元素不应该包含额外的JavaScript代码，不会执行；
- 一般放在<body>元素中（用户感觉打开速度加快了）；
- defer和async并不保证按照指定它们的先后顺序执行；
- 将页面的MIME类型指定为‘application/xhtml+xml’的情况下会触发XHTML模式；
- 浏览器不支持脚本和浏览器支持却禁用脚本可以使用<noscript>元素（浏览器会显示<noscript>元素中内容）；

外部文件的优点：
- 可维护性：遍及不同HTML页面的JavaScript会造成维护问题。
- 可缓存：如果有两个页面都使用同一个文件，那么这个文件只需下载一次（加快加载）；
- 适应未来：HTML和XHTML包含外部文件的语法是相同的；

# 基本概念
## 语法
### 区分大小写
### 标识符
- 第一个字符必须是一个字母、下划线（—）或一个美元符号（$）；
- 其他字符可以是字母、下划线、美元符号或者数字；
- *不能把关键字、保留字true、false和null用作标识符*
### 注释
- // 单行注释；
- /* 多行注释；
### 严格模式
- 在脚本顶部添加："use strict";
- 在函数顶部添加："use strict";
### 语句
- 最好使用“ ；”号结尾；
### 数据类型
用typeof判断：
- "undefined" -- 如果这个值未定义；
- "boolean" -- 如果这个值是布尔值；
- "string" -- 如果这个值是字符串；
- "number" -- 如果这个值是数值；
- "object" -- 如果这个值是对象或null;
- "function" -- 如果这个值是函数（Object）；
### undefined
- 在使用var声明变量但未对其加以初始化时，这个变量的值就是undefined；
- typeof对于一个未声明的变量也会返回一个undefined值；
### null
- 是一个空对象指针；
- undefined派生自null：

```
alert(null == undefined);   // true
```
- 建议null值初始化先声明；
- *建议显式地初始化变量，能区别空对象指针和未经初始化的变量；*
### boolean
- Boolean（）返回值见js视频笔记；
### number
- 不要测试某个特定的浮点数值（a + b == 0.3）；
- isFinite（）函数用于判断是否为有穷数；
- 任何数除以0会返回NaN；
- 任何涉及NaN的计算操作都会返回NaN;
- var num = Number(''); // 0   建议使用parseInt();
### String
- ECMAScript中的字符串是不可变得，改变要销毁原来的字符串（默认）；
- String()
    - 如果有toString()方法，则调用该方法并返回相应的结果；
    - 如果值是null，则返回‘null’；
    - 如果值是undefined，则返回‘undefined’；
- Object类型
- Object的每个实例都有下列的属性和方法：
    - Constructor：保存着用于创建当前对象的函数。
    - hasOwnproperty(propertyNma):用于检查给定的属性在当前对象实例中（不是在实例的原型中）是否存在；
    - ispropertyIsEnumerable(propertyName):用于检查给定的属性是否能够使用for-in语句来枚举。与hasOwnproperty（）方法一样，作为参数的属性名必须以字符串形式制定。
    - toLocaleString（）：返回对象的字符串表示，该字符串与执行环境 去对应。
    - toString（）：返回对象的字符串表示；
    - valueOf（）：返回对象的字符串、数值或布尔值表示。通常与toString（）方法的返回值相同。
### 操作符
- 逻辑非
    - 如果操作数是一个对象，返回false；
    - 如果操作数是一个空字符串，返回true；
    - 如果操作数是一个非空字符串，返回false；
    - 如果操作数是数值0，返回true；
    - 如果操作数是任意非0数值（包括Infinity），返回false；
    - 如果操作数是null，返回true；
    - 如果操作数是NaN，返回true；
    - 如果操作数是undefined，返回true；
- 逻辑与
    - 如果第一个操作数是对象，则返回第二个操作数；
    - 如果第二个操作数是对象，则只有在第一个操作数的求值结果为true的情况下才会返回该对象；
    - 如果两个操作数都是对象，则返回第二个操作数；
    - 如果有一个操作数是null，则返回null；
    - 如果有一个操作数是NaN，则返回NaN；
    - 如果有一个操作数是undefined,则返回undefined。
- 逻辑或
    - 如果第一个操作数是对象，则返回第一个操作数；
    - 如果第一个操作数的求值结果为false，则返回第二个操作数；
    - 如果两个操作数都是对象，则返回第一个操作数；
    - 如果两个操作数都是null，则返回null；
    - 如果两个操作数都是NaN，则返回NaN；
    - 如果两个操作数都是undefined，则返回undefined；
- 加性操作符
    - 如果两个操作符都是字符串，则将第二个操作数转换为字符串，然后再将两个字符串拼接起来；
- 减法
    - 如果有一个操作数是字符串、布尔值、bull或undefined，则先调用Number（）将其转换为数值，再执行运算；
    - 如果有一个值是对象，则调用对象的valueOf（）方法；
- 语句
    - label通常与break、continue一起使用，跳出总循环；
```
    var num = 0;
    output:
    for(var i = 0; i < 10; i++){
        if(var j = 0; j < 10; j++){
            break output;
        }
        num++;
    }
    alert(num);   // 55
```
- with语句
    - 将代码的作用域设置到一个特定的对象中：with（expression）statement；
- switch语句
    - 可以使用任何的数据类型（字符串、表达式、对象等）；
- 函数
    - 推荐始终返回一个值或者不返回值；
- 参数
    - 命名的参数只提供便利，但不是必须的；
    - 通过访问arguments对象的length属性可以获知多少个参数传给了函数；
    - arguments对象的长度是由传入的参数个数决定的，不是定义的命名参数个数；
    - arguments的值永远与对应的命名参数的值保持同步；
    - arguments模拟重载:
```
function(num1,num2){
    if(arguments == 1){
        alert(arguments[0] + 10);
    }
    if(arguments == 2){
        alert(num1 + num2);
    }
}
```
    
- JavaScript中没有重载

---
# 变量、作用域和内存问题
## 基本类型和引用类型的值
*JavaScript不允许直接访问内存中的位置，在操作对象时，实在操作对象的引用而不是实际的对象*
- 动态的属性
    - 对于引用类型的值，可以为其添加属性和方法，也可以改变和删除其属性和方法（delet）；
- 复制变量值
    - 从一个变量向另一个变量复制引用类型的值时，也会将存储在变量对象中的值复制一份放到新变量分配的空间中（这个值的副本实际上是一个指针）；
- 传递参数
    - 基本类型的值用参数传递；
    - 引用类型的值用引用传递；
- 检测类型
    - 引用类型的检测一般使用instanceof操作符；
    - 基本类型的检测一般使用typeof操作符；
## 执行环境和作用域
- 每个环境都可以向上搜索作用域链；
- 任何环境都不能向下搜索作用域链二进入里一个执行环境；
- 延长作用域链
    - try-catch语句的catch块；
    - with语句；
- 块级作用域
    - JavaScript中没有块级作用域；
    - 变量在声明它们的函数体以及这个函数体嵌套的任意函数体内都是有定义的；
    - 当使用var声明一个变量时，创建的这个属性是不可配置的，也就是说无法通过delete运算符删除；
    - 使用var声明变量会自动被添加到最近的环境中；
    - 没有使用var声明的变量会自动被添加到全局环境；
# 引用类型
- Object类型
    - 创建Object实例的的两种方式：
    ```
    var person = new Object();
    person.name = 'Neo';
    //第一种
    var person = {
        name : 'Neo'
    } 或者
    var person = {
        'name' : 'Neo'
    }
    //第二种不会调用Object构造函数
    ```
    - 访问对象属性两种方法：
    ```
    alert(person['name']);  // Neo
    alert(person.name);     // Neo
    方括号访问法更加灵活，可以通过变量来访问属性；
    也可以用作属性是关键字或保留字时；
    平时建议使用点来访问；
    ```
- Array类型
    - 创建数组方式：
    ```
    var colors = new Array();
    var colors = Array();
    var colors = new Array(20);     //20代表数组的length;
    var colors = new Array('red','blue','green');
    var colors = ['red','blue','green'];
    //该方法不调用Array构造函数；
    ```
    - 数组的length属性不止是可读的：
     ```
     var colors = ['red','blue','green'];
     colors.length = 2;
     alert(colors[2]);  // undefined;
     colors[colors.length] = 'black';   
     //向数组的尾部添加一个值；
     ```
    - 数组最多可以包含4294967295个项；
    - 检测数组的方法：Array.isArray(value);
    - 栈方法（后进先出）：
        - push（）；在数组尾部添加一个项，返回数组的长度； 
        - pop（）；移除数组尾部的项，返回移除的项；
    - 队列方法（先进先出）：
        - shift();移除数组中的第一个项，并返回该项；
        - unshift();在数组前端添加任意个项，返回数组的长度；
    - 重排序方法
        - reverse();反转数组项的顺序,返回排序后的数组；
        - sort();默认调用toString()方法，比较字符串的大小排序，返回排序后的数组；建议使用比较函数：
        ```
        function compare(value1 , value2){
            if(value1 > value2){
                return 1;
            }
            if(value1 < value2){
                return -1;
            }
            if(value1 = value2){
                return 0;
            }
        }
        var values = [0,1,5,10,15];
        values.sort(compare);
        alert(values);
        ```
    - 操作方法
        - concat()方法基于当前数组创建一个新数组，传递参数（可以是数组）添加到该数组的尾部，返回新数组，不影响原数组；
        - slice()方法基于当前数组创建一个新数组，返回截取的项(不影响原数组)：
        ```
        var colors = ['red','green','blue','yellow','purple'];
        var colors1 = colors.slice(1); 
        // 'green','blue','yellow','purple';
        var colors2 = colors.slice(1,4);
        // 'green','blue','yellow';
        ```
        - splice(x,y,'z'...),x为起始项，y为需要删除的项数，'z'...为需要在删除位置添加的项（不止一个）始终返回一个数组，该数组包含从原始数组中删除的项；
    - 位置方法
        - indexOf()接收两个参数，要查找的项和起始位置，返回查找的项的位置；
        - lastIndexOf()接收两个参数，要查找的项和起始位置，返回查找的项的位置（从后往前查找）；
    - 迭代方法（传入函数会接收到三个值：数组项的值、该项在数组中的位置、和数组本身）
        - every():对数组每一项运行给定函数，如果该函数对每一项都返回true，则返回true；
        - filter():对数组每一项运行给定函数，返回该函数会返回true的项组成的数组；
        - forEach():对数组每一项运行给定函数，没有返回值；
        - map():对数组每一项运行给定函数，返回每次函数调用的结果组成的数组；
        - some():对数组每一项运行给定函数，如果该函数对任一项返回true，则返回true；
    - 缩小方法
        - reduceRight()遍历方向和reduce()相反；
        - reduce()和reduceRight():
        ```
        var values = [1,2,3,4,5];
        var sum = values.reduce(function(pre,cur,index,array{
            return pre + cur;
        });
        alert(sum); // 15
        ```
- Date类型
    - Date.parse()接收格式是：May 25,2004;
    - Date.UTC()接收格式是：2004，4,25;
    - Date.now()获得当前时间（用毫秒数表示）；
    - Date类型的valueOf()方法，返回毫秒数；
    - 日期的格式化方法：
        - toDateString():以特定于实现的格式现实星期几、月、日和年；
        - toTimeString():以特定于实现的格式显示时、分、秒和时区；
        - toLocaleDateString():以特定于地区的格式显示星期几、月、日和年；
        - toLocaleTimeString():一特定于实现的格式显示时、分、秒；
        - toUTCString():以特定于实现的格式完整的UTC日期；
    - 常用方法：
        - getTime():返回表示日期的毫秒数；与valueOf()方法返回的值相同；
        - setTime():以毫秒数设置日期，会改变整个日期；
- RegExp类型
    - 两种创建方式：
    ```
    var pattern1 = /[bc]at/i;
    
    var pattern1 = new RegExp('[bc]at','i');
    ```
    - 使用正则表达式每次必须创建新的RegExp实例；
    - RegExp实例属性：
        - global:布尔值，表示是否设置了g标志；
        - ignoreCase:布尔值，表示是否设置了i标志；
        - lastIndex:整数，表示开始搜索下一个匹配的字符位置，从0算起；
        - multiline:布尔值，表示是否设置了m标志；
        - source:正则表达式的字符串表示，按照字面量形式而非传入构造函数中的字符串模式返回；
    - exec()方法：接收一个参数，返回包含匹配项信息的数组；
        - index表示匹配项在字符串中的位置；
        - input表示应用于正则表达式的字符串；
    - test()方法：接受一个参数，返回目标字符串与某个模式是否匹配；
    - toString和toLocaleSring()方法返回正则表达式的字面量；
    - valueOf()方法返回正则表达式本身；
- function类型
    - 函数是对象，函数名是指针；
    - 没有重载；
    - 解析器会率先读取函数声明；
    - 函数的名字仅仅是一个包含指针的变量；
    - 函数的内部属性：
        - arguments：主要保存函数参数；
            - callee属性：是一个指针，指向拥有这个arguments对象的函数；
            ```
            function factorial(num){
                if(num <= 1){
                    return 1;
                }else{
                    return num * factorial(num - 1);
                }
            }
            //计算阶乘的函数，用arguments.callee属性可以解耦；
            function factorial(num){
                if(num <= 1){
                    return 1;
                }else{
                    return num * arguments.callee(num - 1);
                }
            }
            ```
        - this属性：引用的是函数据以执行的环境对象；
        - caller属性：保存着调用当前函数的函数的引用，如果在全局作用域中调用当前函数，它的值为null；
        - 函数的属性和方法：
            - length：表示函数希望接收的命名参数的个数；
            - prototype：保存所有实例方法的真正所在（不可枚举）；
            - apply()方法接收两个参数：一个是在其中运行函数的作用域，另一个是参数数组；
            - call()方法和apply相同，不过第二个参数必    须逐个列举出来；
            - *使用call()和apply()方法扩充作用域的最大好处是对象不需要与方法有任何耦合关系*；
            - bind()方法：创建一个函数的实例，其作用域值会绑定到传给bind()函数的值；
- 基本==包装==类型
    - 引用类型和基本包装类型的主要区别就是==对象==的生存期。引用类型实例在执行流离开当前作用域之前都一直保存在内存中，而基本包装类型则只存在于一行代码的执行瞬间；
    - Boolean类型
        - 布尔表达式中所有对象都会被转换为true（==布尔对象都为true==）；
        - 对象是Boolean类型的实例，使用instanceof操作符测试Boolean对象会返回ture，而测试基本类型的布尔值则返回false；
    - Number类型
        - toFixed()方法会按照指定的小数位返回数值的字符串表示（可以四舍五入）；
        - toExponential（）方法返回以指数表示法（也称e表示法）表示的数值的字符串形式；
        - toPrecision（）方法会选择合适的格式输出Number字符串；
    - String类型
        - 字符方法：
            - charAt()方法以单字符字符串的形式返回给定位置的那个字符；
            - charCodeAt()以单字符字符编码的形式返回给定位置的那个字符；
    - 字符串操作方法
        - concat()方法专门用来拼接字符串（可以是多个）；
        - slice()和substr()和substring()三个方法都接受一个或两个参数，第一个参数指定子字符串的开始位置，slice()和substring()第二个参数表示子字符串到哪里结束，substr()表示返回的字符个数；
    - 字符串位置方法
        - indexOf()方法返回子字符串的位置，第一个参数是需要搜索的字符，第二个参数是开始查找的位置，从开头往后搜索；
        - lastIndexOf()返回子字符串的位置，第一个参数是需要搜索的字符，第二个参数是开始查找的位置，从结尾往前搜索；
    - trim()方法会创建一个字符串的副本，删除前置及后缀的所有空格，返回结果
    - 大小写转换的方法：
        - toLowerCase():转换为小写；
        - toUpperCase()：转换为大写；
- 单体内置对象
    - Global对象
        - URI编码方法：
            - encodeURI（）方法结果是除了空格之外的其他字符都原封不动；
            - encodeURIComponent（）方法会使用对应的编码替换所有非字母数字字符；
            - decodeURI（）方法只能对使用encodeURI（）方法的字符进行解码；
            - decodeURIComponent（）能够解码使用encodeURIComponent（）编码的所有字符，即它可以解码任何特殊字符的编码；
        - eval()方法是一个完整的ECMAScript解析器，eval()中创建的任何变量或函数都不会提升，它们只在eval()执行的时候创建；
    - Math对象
        - min()和max()方法用于确定一组数值中的最小值和最大值；
        - Math.ceil()执行向上舍入；
        - Math.floor()执行向下舍入；
        - Math.round()执行标准舍入（四舍五入）；
        - Math.random()方法返回结余0和1之间的一个随机数（不包括0和1）；
        ```
        var num = Math.floor(Math.radom() * 可能的总数 + 可能的最小值);
        //利用Math.random()方法从某个整数范围内随机选择一个值；
        function selectFrom(lowerValue , upperValue){
            var choice = upperValue - lowerValue + 1;
            return Math.floor(Math.random() * choice + lowerValue);
        }
        var num = selectFrom(2,10);
        alert(num);//介于2和10之间（包括2和10）的一个数值；
        var colors = ['red','green','blue','yellow','black'];
        var color = colors[selectFrom(0,colors.length-1)];
        alert(color);//返回一个随机颜色；
        ```
        

---

# 面向对象的程序设计
- 属性类型
    - 数据属性
        - [[Configurable]]:表示能通过delete否删除属性从而重新定义属性，默认为true(修改后不可变);
        - [[Enumerable]]:能否通过for-in循环返回属性，默认为true；
        - [[Writable]]:能够修改属性的值，默认为true；
        - [[value]]:包含属性的数据值，默认为undefined，设置后很难修改，建议不要使用;
        - 使用Object.defineProperty()方法设置的属性默认无法修改；
    - 访问器属性：
        - [[Configurable]]:能否通过delete删除属性，默认为true；
        - [[Enumerable]]:能否通过for-in循环返回属性，默认为true；
        - [[Get]]:读取属性时调用的函数，默认为undefined；
        - [[Set]]:写入属性时调用的函数，默认为undefined；
        - 访问器不能直接定义，必须使用Object.defineProperty()定义；
        ```
        var book = {
                year : 2004,
                edition : 1
            }
            Object.defineProperty(book,'year',{
                get : function () {
                    return this.year;
                },
                set : function (newYear) {
                    if(newYear > 2004){
                        this.edition += newYear - 2004;
                    }
                }
            });
            book.year = 2005;
            alert(book.edition);
        ```
    - 定义多个属性
        - Object.defineProperties()方法，接受两个参数，第一个是要修改的对象，第二个是该对象要修改的属性；
    - 读取属性的特性
        - getOWnPropertyDescriptor()方法
- 创建对象
    - 工厂模式
        - 优点：解决了创建对象相似的问题；
        - 缺点：无法识别对象的类型；
    - 构造函数模式
        - 建议首字母大写；
        - 用new操作符创建实例；
        - isPrototypeOf()方法来确定对象之间是否存在原型关系；
        - getPrototypeOf()方法返回对象的原型；
        - hasOwnProperty()方法检测一个属性是存在于实例（true），还是原型中；
        - in操作符会在通过对象能够访问给定属性时，返回true；
        ```
        function hasPrototypeProperty(Object,PrototypeName){
            return !Object.hasOwnProperty(PrototypeName) && 
            (PrototypeName in Object);
        }
        // 属性是否只存在于原型中；
        ```
        - Object.keys()方法接受一个对象，返回所有可枚举属性的字符串数组；
        - Object.getOwnPropertyName()方法返回所有实例属性（包括不可枚举类型）；
    - 组合使用
        - 构造函数用于定义实例属性，原型模式用于定义方法和共享的属性；
        - 如果在已经创建了实例的情况下重写原型，那么就会切断现有实例与新原型之间的联系；
    - 寄生构造函数模式
        - 在创建时较工厂模式多一个new关键字创建；
        - 创建的对象和构造函数之间没有关系，无法使用instanceof方法；
    - 稳妥构造函数模式
        - 和工厂模式相似，区别是属性私有化（安全）；
        - 创建的对象和构造函数之间没有关系，无法使用instanceof方法；
- 继承
    - 原型链继承：利用原型让一个引用类型继承另一个引用类型的属性和方法；
        - 先继承再写子类自身的方法；
        - 可以使用instenceof()操作符测试原型与实力的关系；
        - 缺点：子类容易污染父类的属性或者方法；
    - 借用构造函数继承：在子类型构造函数的内部调用超类型构造函数（使用call或者apply方法）；
        - 缺点：函数方法无法复用；
    - 组合继承（伪经典继承）：使用原型链对原型方法继承，通过借用构造函数对实例属性继承；
        - 优点：集合了借用和原型链的优点，是常用的继承模式
        - 可以使用instenceof和isPrototypeOf()识别；
    - 原型式继承
        - 使用Object.create()方法继承，和原型链继承相似，也会污染父类；
    - 寄生式继承
        - 和原型式继承相似，使用新对象，解决了污染父类的问题，但是不能做到函数复用；
    - 寄生式组合继承
        - 集合了原型式和寄生式地优点；
        - 效率比伪经典继承要高；
        

---

# 函数表达式

- 函数表达式的特征
    - function.name属性可以访问函数的名字；
    - 函数的声明提升；
    - if语句体内容不要使用匿名函数，建议使用函数表达式；
    - 把函数当成值来使用的情况下，可以使用匿名函数；
## 递归
- 递归函数是在一个函数通过名字调用自身的情况下构成的；
- 建议使用arguments.callee代替函数名，减少耦合性；
## 闭包
- 闭包是指有权访问另一个函数作用域中的变量的函数；
- 缺点：占用内存更多，建议绝对需要时再考虑使用；
- 闭包只能取得包含函数中任何变量的最后一个值；
- 闭包中匿名函数的执行环境具有全局性，其tihs对象通常指向window；
- 如果想要访问作用域中的arguments和this对象，必须将该对象的引用保存到另一个闭包能够访问的对象中；
## 内存泄漏
- 如果闭包的作用域链中保存着一个HTMl元素，那么意味着该元素无法被销毁；
- 内存泄漏会导致垃圾无法回收（计数策略回收），占用内存；
## 模仿块级作用域
- 函数声明后面不能跟圆括号，函数表达式可以；
- 使用圆括号让函数表达式立即执行，可以减少内存占用问题，模拟块级作用域；
## 私有变量
- 我们把有权访问私有变量和私有函数的公有方法称为特权方法；
- 在构造函数中定义特权方法会对每个实例都会创建同样的一组新方法；
- 静态私有变量
    - eg:
    ```
    (function () {
            var privateValue = 10;
            function privateFunc() {
                return false;
            }
            Myobject = function () {

            };
            Myobject.prototype.publicFunc = function () {
                privateValue++;
                alert(privateFunc());
            }
        })();
    ```
    - 多查找作用域链中的一个层次，就会影响查找速度，这是闭包和私有变量的一个缺点；
- 模块模式
    - 模块模式通过为单例添加私有变量和特权方法能够使其得到增强；
    - eg：
    ```
    var singleton = function () {
            var privateValue = 10;
            function privateFunc() {
                return false;
            }
            return {
                publicValue : true,
                publicFunc : function () {
                    privateValue++;
                    return privateFunc();
                }
            }
        }();
    ```
    - 单例通常都是作为全局对象存在的；
-增强的模块模式：用于创建的对象必须是某个对象的实例；
    - eg：
    ```
    var application = function () {
            var components = new Array();
            components.push(new BaseComponent());
            var app = new BaseComponent();
            app.getComponentCount = function () {
                return components.length;
            }
            app.registerComponent = function (component) {
                if(typeof component == "object"){
                    components.push(component);
                }
            }
            return app;
        }();
    ```
## 小结
- 函数表达式不同于函数声明。函数声明要求有名字，但函数表达式不需要。没有名字的函数表达式也叫作匿名函数；
- 在无法确定如何引用函数的情况下，递归函数就会变得比较复杂；
- 递归函数应该始终使用arguments.callee来递归调用自身；
- 在函数内部定义了其他函数时，就创建了闭包。闭包有权访问包含函数内部的所有变量，原理如下：
    - 在后台执行环境中，闭包的作用域链包含着它自己的作用域、包含函数的作用域和全局作用域。
    - 通常，函数的作用域及其所有变量都会在函数执行结束后被销毁；
    - 但是，当函数返回了一个闭包时，这个函数的作用域将会一直在内存中保存到闭包不存在为止；
- 使用闭包可以在JavaScript中模仿块级作用域，要点如下：
    - 创建并立即调用一个函数，这样既可以执行其中的代码，又不会在内存中留下对该函数的引用；
    - 结果就是函数内部的所有变量都会被立即销毁--除非将某些变量赋值给力包含作用域中的变量；
- 闭包还可以用于在对象中创建私有变量，相关概念和要点如下：
    - 即使JavaScript中没有正式的私有对象属性概念，但可以使用闭包爱实现公有方法，而通过公有方法可以访问在包含作用域中定义的变量；
    - 有权访问私有变量的公有方法叫做特权方法；
    - 可以使用构造函数模式、原型模式来实现自定义类型的特权方法，也可以使用模块模式、增强模块模式来实现单例的特权方法；

---
# BOM
## window对象
- BOM的核心对象是window，它表示浏览器的一个实例。在浏览器中它既是通过JavaScript访问浏览器窗口的一个接口，又是ECMAScript规定的Global对象
- 全局变量不能通过delete操作符删除，而直接在window对象上的定义的属性可以；
- 尝试访问未声明的变量会抛出错误，但通过查询window对象，可以知道某个可能未声明的变量是否存在（undefined）；

## 窗口关系及框架
- 如果页面中包含框架，则每个框架都拥有自己的window对象，并且保存在frames集合中；
- 每个window对象都有一个name属性，其中包含框架名称；
- top指向最高层的框架，parent指向当前框架的直接上层框架；
- 除非最高层窗口是通过window.open()打开的，否则其window对象的name属性不会包含任何值；

## 窗口位置
- 取得窗口左边和上边的位置：
```
var leftPos = (typeof window.screenLeft == 'number') ? window.screenLeft : window.scrollX;
var topPos = (typeof window.screenTop == 'number') ? window.screenTop : window.scrollY;
```
- moveTo():接收的是新位置的x和y坐标值；moveBy()：接收的是水平和垂直方向上移动的像素数；这两个方法可能会被禁用，且只能对最外层window使用；

## 导航和打开窗口
- window.open()方法可以接收四个参数：要加载的URL、窗口目标、一个特性字符串以及一个表示新页面是否取代浏览器历史记录中当前加载页面的布尔值；
- 浏览器阻止弹出窗口，window.open()会返回null；
- 浏览器扩展或其他程序阻止的弹出窗口，window.open()通常会抛出一个错误；

## 间歇调用和超时调用
- JavaScript是单线程程序的解释器；
- 超时调用：setTimeout()方法接收两个参数：要执行的代码和以毫秒表示的（等待）时间；第一个参数可以是包含代码的字符串，也可以是一个函数；
- setTimeout()方法会返回一个数值ID；clearTimeout()方法可以接收这个参数，并取消超时调用；
- 超时调用都是在全局作用域中执行的，因此函数中this的值在非严格模式下指向window对象，严格模式指向undefined；
- 间歇调用：setInterval()接收参数与setTimeout()相同，它会按照时间间隔重复执行代码，直至间歇调用被取消或者页面被卸载；
- setInterval()方法会返回一个间歇调用ID；clearInterval()方法可以接收这个参数，并取消间歇调用；
- eg：
```
var num = 0;
       var max = 10;
       var testId = null;
       function increateNumber() {
           num++;
           if(num == max){
               clearInterval(testId);
               alert(num);
           }
       }
       setInterval(increateNumber,500);
       //也可以用超时调用实现
       var num = 0;
       var max = 10;
       function increateNumber() {
           num++;
           if(num < max){
               setTimeout(increateNumber,500);
           }else {
               alert(num);
           }
       }
       setTimeout(increateNumber,500);
```
- 间歇调用可能会在前一个间歇调用结束之前启动，建议最好使用超时调用来模拟间歇调用；

## 系统对话框
- 系统对话框的外观由操作系统和浏览器设置决定，不是由CSS决定；
- 对话框都是同步和模态的，显示代码会停止执行，关掉后会恢复执行；
- alert()对话框向用户显示无法控制的消息，用户只能够看完消息后关闭对话框；
- confirm()对话框确认用户是否确认，返回true或者false，经常用于用户删除操作；
- prompt()是一个提示框，用于提示用户输入一些文本；
    - 接收两个参数，要显示给用户的文本和文本输入域的默认值（可以为空）；
    - 如果用户单击OK则返回文本域的值，如果用户单击Cancel或者其他方式关闭了对话框，则返回null；
- window.find()方法显示查找对话框，window.print()方法显示打印对话框，这两个方法是异步显示的；

## location对象
- location既是window对象的属性，也是document对象的属性；
- 不止保存着当前文档的信息，还将URL解析为独立的片段（详细信息见P207）；
- 查询字符串参数：
- eg：
```
function getQueryStringArgs() {
            var qs = (location.search.length > 0 ? location.search.substring(1) : '');
            var args = {};
            var items = qs.length ? qs.split('&') : [] ;
            var item = null;
            var name = null;
            var value = null;
            var i = 0;
            for(i ; i < items.length ; i++){
                item = items[i].split('==');
                name = decodeURIComponent(item[0]);
                value = decodeURIComponent(item[1]);
                if(name.length){
                    args[name] = value;
                }
            }
            return args;
        }
```
- 位置操作
    - assign()方法为其传递一个URL可以立即打开新的URL并在浏览器的历史记录中生成一条记录；
    - location.href或window.location设置一个URL值，也会以该值调用assign()方法；
    - 修改location对象的其他属性也可以改变当前加载的页面（hash/search/hostname/pathname/port）；
    - replace()方法只接受一个参数（URl），不会生成历史记录（用户点击后退无效）；
    - reload()方法重新加载页面（有可能从缓存加载），传递一个true值从服务器重新加载；

## navigator对象
- 识别客户端浏览器的事实标准（属性方法见P211）；
- 检测插件
    - 非IE浏览器使用plugins数组来达到这个目的，该数组每一项都包含下列属性：
    - name:插件名字；
    - description:插件的描述；
    - filename:插件的文件名；
    - length:插件所处理的MIME类型数量；
    - 在IE中检测插件使用ActiveXObject类型，必须知道其COM标识符；
    - plugins集合有一个refresh()方法，用于刷新plugins以反映最新安装的插件，只接受一个布尔值，设为true则会重新加载包含插件的所有页面，否则只更新plugins集合，不重新加载页面；

## history对象
- history对象保存着用户上网的历史记录；
- 使用go ()方法可以在用户的历史记录中任意跳转，这个方法接收一个参数（正数向前，负数向后）。也可以传递一个字符参数，浏览器会跳转到历史记录包含该字符串的第一个位置，如果历史记录不包含该字符串，那么这个方法什么也不做；
- back()和forward()方法是浏览器向后或向前跳转，和go()方法类似；
- length属性，保存着历史记录的数量；

# DOM
- IE中的所有对象都是以COM对象的形式实现的，与原生JavaScript对象的行为或活动特点并不一致；

## 节点层次
-  DOM可以将任何HTML或XML文档描绘成一个由多层节点构成的结构；
-  文档元素是文档的最外层元素，文档中其他所有元素都包含在文档元素中，每个文档只能有一个文档元素；
-  Node类型
    -  DOM1级定义了一个Node接口，该接口由DOM中所有节点类型实现，JavaScript作为Node类型实现的；
    -  JavaScript中的所有节点类型都继承自Node类型，共享相同的基本属性和方法（见P249）；
    -  nodeName属性保存的始终都是元素的标签名；
    -  nodeValue的值始终为null；
    -  每个节点都有一个childNodes属性，其中保存着一个NodeList对象（类数组，保存一组有序的节点）；
    -  NodeList对象
        - 访问保存在NodeList中的节点，可以通过方括号，也可以使用item（）方法；
        - length属性表示的是访问NodeList的那一刻，其中包含的节点数量（NodeList动态查询）；
    - 每个节点都有一个parentNode属性，指向文档树中的父节点；
    - previousSibling属性表示前一个节点；
    - nextSibling属性表示后一个节点；
    - hasChildNodes()方法在节点包含一个或多个子节点的情况下返回true；
    - ownerDocument属性指向表示整个文档的文档节点；
- 操作节点
    - appendChild()用于向childNodes列表的末尾添加一个节点，返回新增的节点；
    - insertBefore()方法接收两个参数：要插入的节点和作为参照的节点，返回被插入的节点，如果参照节点是null，执行appendChild相同的操作；
    - replaceChild（）方法接收两个参数：要插入的节点和要替换的节点，要替换的节点将由这个方法返回并从文档树中移除；
    - removeChild()方法接收一个参数：要移除的节点，返回被移除的节点；
    - cloneNode()接收一个布尔值参数，表示是否深复制（复制节点及其整个子节点树），返回复制的节点。该方法一般不会复制节点的JavaScript属性（IE中会）；
    - normalize()处理文档树中的文本节点，找到空文本节点，删除它。找到相邻的文本节点，合并为一个文本节点；

## Document类型
- document对象是HTMLDocument的一个实例；
- nodeType的值为9；
- nodeName的值为“#document”；
- nodeValue的值为null；
- parentNode的值为null；
- ownerDocument的值为null；
- 其子节点可能是一个DocumentType（最多一个）、Element（最多一个）、ProcessingInstruction或Comment；
- documentElement属性指向<html>元素；
- document.body指向<body>元素；
- document.title指向<title>元素；
- document.URL指向本页面地址栏中现实的的URL；
- documnet.domain属性中只包含页面域名（可以通过修改相同值来实现跨域），只能设置为松散的；
- document.referrer属性中保存着链接到本页面之前的URL（可能是null）；
- 查找元素Document类型提供了两个方法：
    - getElementById()接收一个参数：要取得的元素的ID，如果不存在返回null；
    - getElementsByTagName()接收一个参数：要取得元素的标签名，返回一个HTMLCollection对象，作为一个动态集合；
    - HTMLCollection对象中有一个方法：namedItem()；可以通过元素的name特性取得集合中的项；
    - getElementsByTagName()中传入'*'，取得页面中所有元素；
    - HTMLDocument类型才有的方法：getElementsByName()，返回带有给定name特性的所有元素；
- DOM一致性检测，除了使用hasFeature方法外，还需使用能力检测；
- 文档写入
    - write():接收一个字符串参数，原样写入；
    - writeln():接收一个字符串参数，写入后末尾换行；
    - open()：打开网页输出流；
    - close()：关闭网页输出流；

## Element类型
- 用于表现XML或HTML元素；
- nodeType的值为1；
- nodeName的值为元素的标签名；
- nodeValue的值为null；
- 访问元素的标签名，可以使用nodeName属性或者tagName属性（在HTML中标签名始终大写表示）；
- HTMl元素
    - 都由HTMElement类型或者它的子类型表示，HTMElement类型直接继承自Element并添加了一些属性；
    - id:元素在文档中的唯一标识符；
    - title:有关元素的附加说明信息，一般通过工具提示条显示出来；
    - lang:元素内容的语言代码，很少使用；
    - dir:语言的方向，很少使用；
    - classname:为元素指定的CSS类；
    - 自定义根据HTML5规范，应该加上data前缀；
    - 操作特性的三个DOM方法：
    - getAttribute()：如果给定名称的特性不存在，返回null（特性不区分大小写），访问style特性或onclick事件处理特性时，返回值可能与属性值不同（建议少用）；
    - setAttribute()接收两个参数：要设置的特性名和值，特性名已存在会以指定的值替换现有的值；
    - removeAttribute()：用于彻底删除元素的特性，不仅会清除特性的值，而且也会从元素中完全删除特性；
    - attributes属性是唯一一个DOM节点类型，包含一个NamedNodeMap，与NodeList类似，元素的每一个特性都由一个Attr节点表示，每个节点都保存在NamedNodeMap对象中；
        - getNamedItem(name):返回nodeName属性等于name的节点；
        - removeNamedItem(name):从列表中移除nodeName属性等于name的节点，与removettribute()方法效果相同，返回被删除特性的Attr节点；
        - setNameditem(node):向列表中添加节点，以节点的nodeName属性为索引；
        - item(pos):返回位于数字pos位置处的节点；
        - 经常使用getAttribute() 、removeAttribute()、 setAttribute()方法代替上面的方法；
        - attributes属性中包含一系列节点，每个节点的nodeName就是特性的名称，节点的nodeValue解释特性的值；
        ```
        // 输出节点的拥有的所有属性；（在IE中不适用）
        function outputAttributes(element) {
            var paris = new Array(),
                attrName,
                attrValue,
                i,
                len;
                for(i = 0 , len = element.attributes.length; i < len ; i++){
                    attrName = element.attributes[i].nodeName;
                    attrValue = element.attributes[i].nodeValue;
                    paris.push(attrName + " = \'" + attrValue + "\'");
                }
                alert(paris.join(' '));
        }
        var p = document.getElementById('p1');
        outputAttributes(p);
        ```
    - 创建元素
        - 使用document.createElement()方法可以创建新元素；
        - 要把新元素添加到文档树，可以使用appendChild() insertBefore() replaceChild()方法；
    - 元素的子节点
        - 通过childNodes属性遍历子节点，通常都要先检查一下nodeType属性(nodeTypr是否等于1)；
        - 元素也支持getElementsByTagName()方法，结果只会返回当前元素的后代；
## Text元素
- 纯文本可以包含转义后的HTML字符，但不能包含HTML代码；
- nodeType的值为3；
- nodeName的值为'#text';
- nodeValue的值为节点所包含的文本；
- parentNode是一个Element；
- 没有子节点；
- 修改文本节点的字符串会经过HTML编码（符号会被转义）；
- 如果两个文本节点是相邻的同胞节点，name这两个节点中的文本就会连起来显示，中间不会有空格；
- creatTextNode()方法可以创建新的Text节点；
- normalize()方法可以将所有文本节点合并成一个节点；
- splitText()方法可以按照指定的位置分割nodeValue值，返回剩下的文本；

## Comment类型
- nodetype的值为8；
- nodeName的值为'#comment';
- nodeValue的值是注释的内容；
- parentNode可能是Document或Element；
- Comment类型与Text类型继承自相同的基类，拥有除splitText()之外的所有字符串操作方法；
- creatComment()方法可以创建注释节点；
- 浏览器不会识别位于<html>标签后面的注释；

## CDATASection类型
- 继承自Text类型，拥有除splitText()之外的所有字符串操作方法；
- 多数浏览器都会把CDATA区域错误的解析为COmment或Element；
- createCDataSection()可以创建CDATA区域；

## DocumentFragment类型
- DOM规定文档片段是一种’轻量级‘的文档，可以包含和控制节点，不会占用资源。将文档中的节点添加到文档片段中，就会从文档树中移除该节点，可以将它作为一个’仓库‘使用
- 通过appendChild()或insertBefore()可以将文档片段中内容添加到文档中；
- eg:
```
var ul = document.getElementById('mylist');
        var fragment = document.createDocumentFragment();
        var li = null;
        for(var i = 0 ; i < 3 ; i++){
            li = document.createElement('li');
            var text = document.createTextNode('item' + (i + 1));
            li.appendChild(text);
            fragment.appendChild(li);
        }
        ul.appendChild(fragment);
```
## Arrt类型
- 元素特性在DOM中以Attr类型来表示，特性存在于元素的attributes属性中的节点；
- 在HTMl中不支持子节点；
- 在XML中子节点可以是Text或EntityRefernce；
- name属性是特性名称，value是特性的值，specified是一个布尔值（区别特性是在代码中指定的，还是默认的）；
- createAttribute并传入特性的名称可以创建新的特性节点；
- setAttributeNode()方法可以将新创建的特性添加到元素中；
- 不建议直接访问特性节点，使用getAttribute() setAttribute() removeAttribute()方法比操作特性节点更为方便；

## DOM操作技术
- 动态脚本
    - 动态加载的外部JavaScript文件能够立即执行；
    ```
    eg：
    function loadScript(url) {
            var sript = document.createElement('script');
            script.type = 'text/javaScript';
            script.src = url;
            document.body.appendChild(script);
        }
    ```
    - IE中将<script\>视为一个特殊的元素，不允许DOM访问其子节点（使用text属性来指定JavaScript代码）；
- 动态样式
    - 把CSS样式包含到HTML中的元素有两个：<link>和<style>；
    - 动态嵌入和<script>元素类似，在IE中使用styleSheet属性中的cssText属性来嵌入css代码；
- 操作表格
    - 为<table>元素添加属性和方法如下：
    - caption:保存着对<caption>的指针；
    - tBodies:是一个<tbody>元素的HTMLCllection；
    - tFoot:保存着对<tfoot>元素的指针；
    - tHead:保存着对<tHead>元素的指针；
    - rows:是一个表格中所有行的HTMLCollection；
    - createTHead():创建<thead>元素，将其放到表格中，返回引用；
    - createTFoot():创建<tfoot>元素，将其放到表格中，返回引用；
    - createCaption():创建<caption>元素，将其放到表格中，返回引用；
    - deleteTHead():删除<thead>元素；
    - deleteTFoot():删除<tfoot>元素；
    - deleteCaption():删除<caption>元素；
    - deleteRow(pos):删除指定位置的行；
    - insertRow(pos):向rows集合中的指定位置插入一行；
    - 为<tbody>元素添加属性和方法如下：
    - rows:保存着元素中行的HTMLCollection；
    - deleteRow():删除指定位置的行；
    - insertRow():向rows集合中的指定位置插入一行，返回对新插入行的引用；
    - 为<tr>元素添加属性和方法如下：
    - cells:保存着元素中单元格的HTMLCollection；
    - deleteCell(pos):删除指定位置的单元格；
    - insertCell(pos):向cells集合中的指定位置插入一个单元格，返回对新插入单元格的引用；

## 使用NodeList
- NodeList、NamedNodeMap、HTMLCollection这三个集合都是动态的，实时更新；
- 如果想要迭代NodeList，最好使用length属性初始化第二个变量；
```
var divs = document.getElementsByTagName('div'), i,len,div;
        for(i = 0 , len = divs.length ; i < len ; i++){
            div = document.createElement('div');
            document.body.appendChild(div);
        }
```
## 小结
- DOM是语言中立的API，用于访问和操作HTML和XML文档；
- DOM节点有各种节点构成；
- 最基本的节点类型是Node，用于抽象的表示文档中一个独立的部分；所有其他类型都继承自Node；
- Document类型表示整个文档，是一组分层节点的根节点，document对象是Document的一个实例；
- Element节点表示文档中的所有HTML或XML元素，可以用来操作这些元素的内容和特性；
- DOM操作往往是JavaScript程序中开销最大的部分，最好的办法就是减少DOM操作；

# DOM扩展
## 选择符API
- querySelector()方法接收一个CSS选择符，返回与该模式匹配的第一个元素，如果没有找到，返回null；
- 通过Document类型调用querySelector()方法时，会在文档元素的范围内查找元素，通过Element类型调用时，只会在该元素后代元素中查找；
- querySelectorAll()方法接收一个CSS选择符，返回所有匹配的元素，返回的是一个NodeList实例，如果没有返回一个空的NodeList对象；
- Document DocumentFragment和Element可以调用querySelectorAll()方法；
- matchesSelector()方法接收一个CSS选择符，如果调用元素与该选择符匹配，返回true，否则返回false。(此方法兼容性不是很好，需要编写一个包装函数)；
## 元素遍历
- Element Traversal API为DOM元素添加了以下5个属性；
- ChildElementCount:返回子元素（不包括文本节点和注释）的个数；
- firstElementChild:指向第一个子元素；firstChild的元素版；
- lastElementChild:指向最后一个子元素；lastChild的元素版；
- previousElementSibling:指向前一个同辈元素；previousSibling的元素版；
- nextElementSibling:指向后一个同辈元素；nextSibling的元素版；
## HTML5
- 与类相关的扩充
    - getElementByClassName()方法接收一个参数，返回带有指定类的所有元素的NodeList，类名的先后顺序不重要，只有位于调用元素子树中的元素才返回；
    - classList属性是新集合类型DOMTokenList的实例，包含length属性，可以使用item()方法或者方括号语法遍历，有下列方法：
    - add(value):将给定的字符串值添加到列表中，如果值已存在就不在添加；
    - contains(value):表示列表中是否存在给定的值，如果存在返回true，否则返回false；
    - remove(value):从列表中删除给定的字符串；
    - toggle(value):如果列表中已经存在给定的值，删除它，如果不存在，则添加它；
- 焦点管理
    - document.activeElement属性始终会引用DOM中当前获得了焦点的元素。文档加载完成是，默认情况下该元素保存的是document.body元素的引用。文档加载期间，document.activeElement的值为null；
    - document.haFocus()方法确定文档元素是否获得了焦点，可以知道用户是否正在与页面交互；
    - readyState属性：loading，正在加载文档。complete，已经加载完文档；
    - document.compataMode属性：CSS1Compat，标准模式。BackCompat，混杂模式；
    - document.head属性，引用文档的<head>元素；
    - document.charset属性表示文档中实际使用的字符集，默认值为‘UTF-16’；
    - document.defaultCharset属性表示文档中默认的字符集；
- 自定义数据属性：
        - HTML5规定可以为元素添加非标准的属性，弹药添加前缀data-；
        - 通过元素的dataset属性来访问自定义属性的值（没有data-前缀）；
- 插入标记
        - innerHTML属性在读模式下，返回调用元素的所有子节点（包括严肃、注释和文本节点）对应的HTML标记。在写模式下，会根据指定的值创建新的DOM树，然后用这个DOM树替换调用元素原先的所有子节点；
        - outerHTML属性在读模式下，返回调用它的元素及所有子节点的HTML标签。在写模式下，outerHTML会根据指定的HTML字符串创建新的DOM子树，然后完全替换调用元素；
        - insertAdjacentHTML()方法接收两个参数，插入位置和要插入的HTML文本。第一个参数必须是下列值之一：
        - 'beforebegin':在当前元素之前插入一个紧邻的同辈元素；
        - 'afterbegin':在当前元素之下插入一个新的子元素或在第一个子元素之前再插入新的子元素；
        - 'beforeend':在当前元素之下插入一个新的子元素或在最后一个子元素之后在插入新的子元素；
        - 'afterend':在当前元素之后插入一个紧邻的同辈元素；
- 内存与性能问题
        - 在使用innerHTML、outerHTML和insertAdjacentHTML方法时，最好先手工删除要被替换的元素的所有时间处理程序和JavaScript对象属性；
        - 创建和销毁HTML解析器会带来性能损失，要控制在合理的范围内；
- scrollIntoView()可以在所有HTML元素上调用，通过滚动浏览器窗口或某个容器元素，调用元素就可以出现在视口中。如果给这个方法传入true作为参数，那么窗口滚动之后会让调用元素的顶部与视口顶部尽可能平齐。如果传入false作为参数，调用元素会尽可能全部出现在视口中，不过顶部不一定平齐；

# DOM2和DOM3
## 遍历
- NodeIterator和TreeWalker这两个类型能够基于给定的起点对DOM结构执行深度优先的遍历操作；

### NodeIterator
- NodeIterator类型可以使用document.createNodeiterator()方法创建它的新实例，这个方法接收下列四个参数；
    - root:想要作为搜索起点的树中的节点；
    - whatToShow:表示要访问哪些节点的数字代码；
    - filter:是一个NodeFilter对象，或者一个表示应该接受还是拒绝某种特定节点的函数；
    - entityRefernceExpansion:布尔值，表示是否要扩展实体引用，在HTML页面中没有用(其中的实体引用不能扩展)；
- whatToShow参数是一个位掩码，通过应用一或多个过滤器（filter）来确定要访问哪些节点，这个参数的值以常量形式在NodeFilter类型中定义,如下所示：
- NodeFilter.SHUW_ALL:显示所有类型节点；
- NodeFilter.SHOW_ELEMNET:显示元素节点；
- NodeFilter.SHOW_TEXT:显示文本节点；
- NodeFilter.SHOW_COMMENT:显示注释节点；
- NodeFilter.SHOW_DOCUMENT:显示文档节点；
- NodeFilter.SHOW_DOCUMENT_TYOE:显示文档类型节点；
- 除了NodeFilter.SHUW_ALL之外，可以使用按位或操作符来组合多个选项；
- 有nextNode()和previousNode()两个方法；

### TreeWalker
- 提供了下列在不同方向上遍历DOM结构的方法：
- parentNode():遍历到当前节点的父节点；
- firstChild():遍历到当前节点的第一个子节点；
- lastChild():遍历到当前节点的最后一个子节点；
- nextSibling():遍历到当前节点的下一个同辈节点；
- previousSibling():遍历到当前节点的上一个同辈节点；
- 通过document.createTreeWalker()方法创建实例，接收的4个参数和createNodeIterator()相同；
- NodeFilter.FILTER_REJECT与NodeFilter.FLITER_SKIP不同，会跳过相应节点及其所有子树；
- currentNode属性表示任何遍历方法在上一次返回的节点；
- 该遍历方法比NodeIterator()方法更加灵活；

## 范围
- 使用createRange()来创建DOM范围，有下列方法：
- startContainer:包含范围起点的节点；
- startOffset:范围在startContainer中起点的偏移量；
- endContainer:包含范围终点的节点；
- endOffset:范围在endContainer中终点的偏移量；
- 使用selectNode()或selectNodeContents()方法选择文档中的一部分。接收一个参数（DOM节点），使用该节点填充范围；
- selectNode()方法选择整个节点（包括子节点），selectNodeContents()方法只选择节点的子节点；

# 事件
- 事件就是文档或浏览器窗口中发生的一些特定的交互瞬间，可以使用侦听器来预订事件；

## 事件流
- 事件冒泡：事件开始时由最具体的元素（文档中嵌套层次最深的那个节点）接收，然后逐级向上传播到较为不具体的节点（文档）；
- 事件捕获：不太具体的节点先接受到事件，最具体的节点最后接收到事件（现在主流浏览器都在使用）；
- DOM事件流：事件捕获阶段、处于目标阶段和事件冒泡阶段；

## 事件处理程序
- 相应某个事件的函数就叫做事件处理程序（或事件侦听器），事件处理程序的名字以“on”开头；
- HTML事件处理程序
    - 通过event变量可以直接访问事件对象；
    - this值等于事件的目标元素；
    - 该事件缺点太多，建议不要使用；
- DOM0级事件处理程序
    - 每个元素都有自己的事件处理程序属性，这些属性通常全部小写；
    - DOM0级指定事件处理程序被认为是元素的方法，在元素的作用域中运行；
    - 将事件处理程序设置为null后，单击将不会由任何动作发生；
- DOM2级事件处理程序
    - 指定和删除事件处理程序的操作：addEventListener()和removeEventListener()方法，都接受三个参数：要处理的事件名、作为事件处理程序的函数、和一个布尔值（true表示在捕获阶段调用事件处理程序，false表示在冒泡阶段调用事件处理程序）；
    - 通过addEventListener()添加的事件处理程序只能使用removeEventListener()方法来移除；
    - removeEventListener()方法第二个参数不能使用匿名函数；
    - 大多数情况下，都是将事件处理程序添加到事件流的冒泡阶段；

## 事件对象
- 在触发DOM上的某个事件时，会产生一个事件对象event，这个对象包含着所有与事件有关的信息（event属性见P356）；
- DOM中的事件对象
    - 在需要通过一个函数处理多个事件时，可以使用type属性；
    - 要阻止特定事件的默认行为，可以使用prevnetDefault()方法（需要将cancelable属性设置为true）；
    - stopPropagation()方法用于立即停止事件在DOM层次中的传播，进一步取消事件捕获或冒泡；
    - 事件对象的eventPhase属性，可以用来确定事件当前正位于事件流的那个阶段（捕获等于1，目标等于2，冒泡等于3）；

## 事件类型
- UI事件
    - load：当页面完全加载后再window上面触发，当图像加载完毕是在<img>元素上面触发，当嵌入内容加载完毕时在<object>元素上面触发；
    - unload:当页面完全卸载后在window上面触发，当嵌入内容卸载完毕时在<object>元素上面触发；
    - abort:在用户停止下载过程时，如果嵌入内容没有加载完，则在<object>元素上面触发；
    - error:当JavaScript错误时在window上面触发，当无法加载图像时在<img>元素上面触发，当无法加载嵌入内容时在<object>元素上面触发；
    - select:当用户选择文本框中的一或多个字符时触发；
    - resize:当窗口或框架大小变化时在window或框架上面触发；
    - scroll:当用户滚动带滚动条的元素中的内容时，在该元素上面触发（<body>元素中包含加载页面的滚动条）；
    - blur:在元素获得焦点时触发，这个事件不会冒泡；
    - focus:在元素获得焦点时触发，这个事件不会冒泡；
    - focusin:在元素获得焦点时触发，会冒泡；
    - focusout:在元素失去焦点时触发；
    - 即使focus和blur不冒泡，也可以在捕获阶段侦听到他们；
- 鼠标事件（大部分冒泡）
    - click:在用户单击主鼠标按钮或者按下回车；
    - dblclick:在用户双击主鼠标按钮时触发；
    - mousedown:在用户按下了任意鼠标按钮时触发；
    - mouseenter:在鼠标光标从元素外部首次移动到元素范围之内时触发（不冒泡，光标移动到后代元素上不会触发）；
    - mouseleave:在位于元素上方的鼠标光标移动到元素范围之外时触发（不冒泡，光标移动到后代元素上不会触发）；
    - mousemove:当鼠标指针在元素内部移动是重复地触发；
    - mouseout:在鼠标指针位于一个元素上方，然后用户将其移入另一个元素时触发；
    - mouseover:在鼠标指针位于一个元素外部，移入时触发；
    - mouseup:在用户释放鼠标按钮时触发；
    - mousewheel：在用户使用鼠标滚轮时就会触发；
- 键盘与文本事件
    - keydown:当用户按下键盘上的任意键时触发（按住不放会重复触发）；
    - keypress:当用户按下键盘上的字符键时触发（按住不放会重复触发）；
    - keyup:当用户释放键盘上的键时触发；
    - textInput:当用户在可编辑区域中输入字符时触发；
- HTML5事件
    - contextmenu:用户在右击会触发该事件（只有Firefox支持）；
    - beforeunload:会在浏览器卸载页面之前触发；
    - DOMContentLoaded:在形成完整的DOM树之后就会触发（不理会图像等资源的下载）；
    - haschange:URL参数列表发生变化时会触发；

## 内存和性能
- 事件委托
```
eg:
var ul =document.getElementById('menu');
        ul.onclick=function(){
            switch(event.target.id){
                case 'doSomethings':
                    document.title = 'I have change this title!';
                    break;
                case 'goSomeare':
                    location.href = 'http://www.baidu.com';
                    break;
                case 'sayHi':
                    alert('Hi Neo!');
                    break;
            }
        }
```
    - 优点：无需等待很快就可以访问；DOM引用少占用内存和消耗的事件都大量减少；
- 移除事件处理程序
    - 移除DOM需要先移除事件处理程序释放内存；
    - 页面卸载之前可以通过onunload事件处理程序移除所有事件处理程序；

## 模拟事件
- 可以在document对象上使用createEvent()方法创建event对象，这个方法接收一个参数，即要创建的事件类型的字符串：
    - UIEvents:一般化的UI事件；
    - MouseEvents:一般化的鼠标事件；
    - MutationEvents:一般化的DOM变动事件；
    - HTMLEvents:一般化的HTML事件；
- dispatchEvent()方法用来触发事件；
- createEvent()传入字符串‘MouseEvents’，返回的对象有一个initMouseEvent()方法，用于指定鼠标事件的信息，接收15个参数（见P406）；
- 自定义DOM事件：createEvent('CustomEvent'),返回initCustomEvent()方法，接收4个参数：
    - type（字符串）：触发的事件类型；
    - bubbles（布尔值）：表示事件是否应该冒泡；
    - cancelable（布尔值）：表示事件是否可以取消；
    - detail（对象）：任意值，保存在event对象的detail属性中；