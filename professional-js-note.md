#professional js note
##JavaScript基本概念
###js变量类型分两类六种：

值类型5种：
1. number
2. string
3. boolean
4. null
5. undefined.

引用类型一个：
object
______

typeof返回的结果字符串，就是这六种之一。

typeof操作符的操作数可以是变量和字面量。
```
        var a = "I'm a string";
        console.log(typeof a); // 操作数是a这个变量
        console.log(typeof 123); // 操作数是字面量
```

####Udefined类型只有一个值 undefined
```
        var message; // 未赋值，系统自动赋值undefined
        // 所以下面比较条件成立
        console.log(message == undefined); // true
```

而对于没有定义的变量，唯一能做的操作是typeof，其他操作都会报错
```
        var message;
        console.log(message) // undefined
        console.log(age) // 报错:age is not defined
```
有意思的是对一个未声明的变量typeof，返回值是也是 undefined
定义了没赋值和没有被定义，对系统来说都不可用，所以都是undefined，由此得出 undefined==undefined
```
var message;
        console.log(message);  // undefined
        console.log(typeof message == typeof age); //true
```

####Null类型
null类型也只有一个值 null，逻辑上讲null是一个空对象指针，所以typeof返回object。
人家是一个对象嘛，只不过现在空着咧，返回object就很合理了。

然后说undefined派生自null，我只能理解为，在内存中或寄存器中，值变量其实也是一个内存地址，指向实际的内存中的值
跟对象的引用方法类似。
所以ECMA-262规定null==undefined
`console.log(null == undefined); // true`

####Boolean
Boolean类型有两个值true和false
其他每种类型都可以用Boolean()方法转换成Boolean值

数据类型        转换为true值        转换为false值
1. number       非零数字               0和NaN
2. string       非空字符串           空字符串
3. boolean      true                false
4. undefined    （N/A）            undefined
5. object       所有对象            null
6. null          (N/A)            false      (这一条我加的)

N/A 表示not applicable 不适用

```
        console.log(Boolean(3)); // true 非零为真
        console.log(true == 3); // false 非零包括3但不限于3,
```
任何条件判断内容都会转换成Boolean类型，所以要理解这个转化规则

####Number
主要是整数和浮点数。
整数包括十进制，8进制和16进制。
浮点数就是小数，必须包括一个点和后面的至少一位有效数字。
也可以用e来表示浮点数
`var floatNum = 3.125e7 // 3.125 * 10的7次方 =31250000`

注意js浮点精度有问题，如：
`console.log(0.1+0.2); // 不等于0.3 而等于0.0000000000000004`

超出js范围的极大和极小数，用infinity和-infinity表示

NaN表示期待number的时候没有返回number，就返回这个NaN。最实用的地方是在除以0的时候不至于崩溃。
NaN的两个特点：
1. 任何数与NaN操作，结果都是NaN。
2. NaN 不等于 NaN。

用isNaN（）这个方法来判断某变量是否为NaN。

转换数值的3个函数
Number()    应用于所有类型
parseInt()  对于字符类型
parseFloat()  字符类型

####String
string最重要的一点是，字符串一旦创建不可被改变。（在其他语言中，字符串作为引用类型保留，而js放弃了这个传统）

字符串转换
number，boolean，object，string都有toString()方法。
特别的地方，就连string类型都有toString方法，toString(方法)返回字符串的一个副本。

####Object
js中所有对象继承与Object，具有下面公共的属性和方法：
1. constructor
2. hasOwnPropert()
3. isPrototypeOf()
4. propertyIsEnumerable()
5. toLocaleString()
6. toString()
7. valueOf()
------

操作符(略......)

####布尔操作符
！逻辑非
&& 逻辑与
|| 逻辑或

！与任何值操作都返回一个逻辑布尔值
！！ 两个一起用，相当于Boolean（），第一个！变成布尔值，第二个！就是他对应的布尔值
```
console.log(!!"blue"); //true
console.log(!!0); //false
console.log(!!NaN); //false
```

&& 逻辑与 短路操作
```
var found = true;
var result = (found && someUndefinedVariable); // 后面的值求值出错，报错
alert(result);  // 不会执行

// 下面短路

var found = false;
var result = (found && someUndefinedVariable); // 后面的值求值出错，报错
alert(result);  // false

```

|| 逻辑或 短路操作
与逻辑与一样也是短路，只是逻辑不同而已
js中常用的地方是：避免给变量赋null或undefined值
`var myObject = preferredObject || backupObject`
前面为真则返回前面的值，否则返回备用值。

------

+ 操作符
需要注意的是，操作数中如果有字符，由于考虑到连接字符串的操作，所以都会被转换为字符串来执行连接的操作。
`var result = 2 + '3'; // 23`

- 操作符
遇到字符串会调用number（），因为减操作只能做数字的减法

函数Function
1. 函数自带arguments对象，传入的参数当做局部变量使用，并且于arguments中的内容同步更新。
2. 没有重载，只能通过函数签名做出不同反应，模拟重载。

##变量 作用域和内存问题
（2015/09/10 11:26）
1. 执行环境（execution context）
2. 作用域（scope）
3. this （execution context，或者其调用者的一个属性）

我们都知道作用域是变量的边界，而程序如何确认这个边界？答案是由执行环境来确认。
执行环境是一个对象，存放这个环境中的变量和函数。
每个作用域都有一个执行环境的对象（叫做活动对象activation object）

在全局执行的时候，只有一个activation object，并创建一个作用域链（scope chain），这个scope chain中第一个对象就是当前的activation object。而以后当子函数执行的时候，则会创建子activation object，并把它添加到作用域链中，然后子环境（execution context）被压入堆栈获得控制权，子环境中的代码根据scope chain中的activation object，一级一级的查找变量和函数来使用它们。当这个子函数执行完毕，则被堆栈弹出，于是子环境被销毁，控制权转回到上级执行环境。

js通过scope chain 机制来实现作用域，而作用域背后由execution context的机制得以实现。

this和arguments是函数的默认属性， this通常指他的调用者，而当函数没有显式的调用者时，就认为是全局环境调用了他。所以在全局环境中，也就是activation object有一个this属性，他的值等于window。

##第五章 引用类型
###Object
定义复合数据。
常规用途：用对象给函数传参数。
额外注意：BOM和DOM是宿主对象，他们不由ECMA-262所定义，而由宿主提供和定义。

属性名和值的用法：
```
        var obj = {
            name: "feifei",
            age: 100,
            sayHi: function(){
                console.log("Hi");
            }
        };

        // key是属性名，属性值用对象.key完整表示

        for(var key in obj){
            console.log(key + ": ",obj[key]);
        }

        // 检测是否为 公有属性

        function hasPubProperty(attr,obj){
            return (attr in obj) && !(obj.hasOwnProperty(attr));
        }
```
属性有两种，1数据属性（常见的），2访问器属性
数据属性调用默认的put方法设置，访问器属性则如下：

```
        // 访问器属性由getter 和 setter 设置方法
        var person1 = {
            _name: "feifei", // 约定的私有属性名前加下划线，但实际上还是公有的
            get name(){ //语法不一样，无需function
                console.log("read name: ");
                return this._name;
            },
            set name(value){
                console.log("write name: " + value);
                this._name = value;
            }
        };
        console.log(person1.name);  // read name: feifei 读操作调用了get name 方法
        person1.name = "bobo";  // write name: bobo 写操作，调用了set name 方法
```
访问器属性的用途：当希望读取，写入属性同时会触发一些行为或操作的时候，就自己写get和set方法。


--传递多个参数时，对必须值用命名参数传入，对多个可选参数用对象来封装。

###Array
检测数组：
常规方法：`if(value instanceOf Array){'do something'};`

ECMAScript5支持的： Array.isArray()方法。
`if(Array.isArray(value)){'do something'};`

转换方法：所有对象都有的toString(),valueOf(),toLocalString().

但数组调用这些转换方法时，数组中的每一项被分别调用，因为读取数组的操作必须一项一项的来。

join()方法
join顾名思义加入，当然是让多项加入成为一项。所以join是数组的方法，数组才有多个项嘛。而返回值是string。

join()接受一个参数作为分隔符，用于在字符串中分割字符。

```
var colors = ["red","green","blue"];
console.log(colors.join()); // red,green,blue 不传参数，默认是逗号
console.log(colors.join("|")); // red|green|blue
```

####栈方法（last-in-first-out）
稍微想想（压栈-出栈）就知道，只需要进栈和出栈两个方法就行了，push(),pop().
既然是后出，当然是从数组尾部进行操作。

####队列方法（first-in-first-out）
当然也需要两个方法（排队的场景），进队列的时候从后面进，用push()就可以了
出的时候从前头出，需要shift()方法

以上出栈和出队列的方法的会有返回值，就是出来的那个家伙本身。

相似的，为了从相反的方向进出队列，就有了unshift()方法，同pop()配合使用。

####重新排序方法
reverse()反转数组
sort()比较数组，参数是比较函数。

####操作数组
这几个方法都会有返回值
concat()
slice()
splice()

####位置方法
indexOf() //顾名思义返回索引值
lastIdexOf() //从后面开始查找

####迭代方法
every() 见p96
some()
filter()
map()
forEach()

####归并方法
reduce() 见p97
reduceRight()

###Date类
感觉比较有用的是这个：
```
        var start = Date.now();
        for(var i=0;i<1000000;i++){};
        var end = Date.now();
        console.log(end-start);
```










