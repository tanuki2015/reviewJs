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
--传递多个参数时，对必须值用命名参数传入，对多个可选参数用对象来封装。

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

####关于原型（prototype）
```
        var Person = function(){};
        var person1 = new Person;

        console.log(Person.prototype.hasOwnProperty("constructor")); // true
        console.log(person1.__proto__.hasOwnProperty("constructor")); // true
        console.log(Person.prototype.hasOwnProperty == person1.__proto__.hasOwnProperty); // true
        // 以上证明，构造函数的原型和其实例的原型是一个东西
        // 只是他们在构造函数上用prototype这个名字，在实例上用__proto__这个名字（这是由浏览器实现的）
        
        console.log(Person.__proto__ == Function.prototype); // true
        console.log(Person.__proto__ == Object.prototype); // false
        // 这两句证明，构造函数的原型也指向创造他的原型--Function的原型。
        // 这也说明，构造函数既是一个对象，也是一个函数，他有双重身份
        // 所以他即有构造函数的属性prototype属性，也有普通对象的__proto__属性
```

原型对象的constructor属性，指向创建他的构造函数。而系统内置的几个构造函数，比如Object,Function,Array等，
感觉就像是一个工厂模式，为了创建基本的对象而存在。
constructor只跟创建他的函数有关，而跟继承无关。
```
        function FnA(){}
        function FnB(){}

        var objA = new FnA;

        FnB.prototype = new FnA; // 这一句如果注释掉，下面结果将成为false，true，false
        var objB = new FnB;

        // objB现在继承于FnA，但他的构造函数还是创建他的函数
        console.log(objB.constructor == objA.constructor); // true 这都是在原型上找到的
        console.log(objB instanceof FnB); //true
        console.log(objB instanceof FnA); //true
```

在for循环中输出私有属性

```
        var empty = {name:"feifei", age: 99};

        for(var property in empty){
            if(empty.hasOwnProperty(property)){
                console.log(property);
            }
        }

```

####继承
js是基于对象的语言（object base），在js中万物皆对象，是对世间事物的简单呈现。而面向对象是在对世间事物抽象思考后，有了类的概念，再派生出对象。
就这么一个区别，造就了基于对象和面向对象完全不同的特征。

三大特征：封装，继承和多态。

封装大家天生都有，这个不用多说。

继承：js中只有对象，当然谈不上什么继承，于是，为了让js有继承的特性，就有了各种各样的曲折的方法，最简单的是基于原型链的继承。
而面向对象语言中，天生有类，类又有子类，所以说是天生自带继承，直接就可以实现。

而多态，由于js没有函数签名，所以也只能婉转的去模拟。

Object.create()方法，创造一个继承的对象。

#####对象的继承，基于原型的方法

```
        // 使用字面量创建对象，其后台的操作如下Object.create方法
        
        var book = {
            title: "the principles of Objected JavaScript"
        };
        
        var book = Object.create(Object,{
            title: {
                configurable: true,
                enumerable: true,
                value: "the principles of Objected JavaScript",
                writable: true
            }
        });
```

另一个例子：
```
        var person1 = {
            name: "papa",
            sayName: function(){
                console.log(this.name);
            }
        };

        var person2 = Object.create(person1,{
            name: {
                configurable: true,
                enumerable: true,
                value: "son",
                writable: true
            }
        });

        person1.sayName();  // papa
        person2.sayName();  // son
        console.log(person1.hasOwnProperty("sayName")); // true
        console.log(person2.hasOwnProperty("sayName")); // false
        console.log(person1.isPrototypeOf(person2)); // true

        console.log(person2 instanceof person1);    // 报错，对象的继承，涉及不到实例，实例一定是由构造函数new出来的
```

#####对象的继承，基于构造函数
为什么需要构造函数的继承？不是已经有原型链的继承了吗？
因为原型链的继承只是简单的单个对象间的继承，而为了表现某个类别下的继承，就得用到构造函数的继承了。

```
 function MyConstructor(){}  // 当定义一个函数的时候，js引擎做了下面的事情
        
        MyConstructor.prototype = Object.create(Object.prototype,{
            constructor:{
                configurable: true,
                enumerable: true,
                value: MyConstructor,
                writable: true
            }
        }); //系统创造一个继承的对象，并把它的constructor属性设置为其构造函数。
        
        console.log(MyConstructor.prototype.constructor == MyConstructor);  // 所以这里为 true
        // 可见任何函数的原型上都会有这个constructor，不仅仅是构造函数。
```

传统的构造函数继承通常如下：

```
        function Rectangle(length,width){
            this.length = length;
            this.width = width;
        }

        Rectangle.prototype.getArea = function(){
            return this.length * this.width;
        };

        Rectangle.prototype.toString = function(){
            return "[Rectangle " + this.length + "x" + this.width + "]";
        };
        
        // inherits from Rectangle
        function Square(size){
            this.length = size;
            this.width = size;
        }
        
        Square.prototype = new Rectangle();
        Square.prototype.constructor = Square;
        
        Square.prototype.toString = function(){
            return "[Square " + this.length + "x" + this.width + "]";
        }
```

他的问题是在继承的时候，父类的构造函数必须运行，就有可能在参数改变的情况下，初始化出问题，所以有下面的改进方法：
使用Object.create()方法,无需运行任何构造函数，没有参数的问题

```
        // inherits from Rectangle
        function Square(size){
            this.length = size;
            this.width = size;
        }
        
        
        Square.prototype = Object.create(Rectangle.prototype,{
            constructor: {
                configurable: true,
                enumerable: true,
                value: Square,
                writable: true
            }
        });

        Square.prototype.toString = function(){
            return "[Square " + this.length + "x" + this.width + "]";
        };
```

通常来说，上面的继承方法已经够用了，但有时候子类需要调用父类的构造函数时，就需要用call，apply方法来借用。
因为这种方式模仿了面向对象语言基于类的继承，所以也称为js的伪类继承。
```
        // inherits from Rectangle
        function Square(size){
            Rectangle.call(this,size,size); // 调用父类构造函数，下面的代码不变
        }

        Square.prototype = Object.create(Rectangle.prototype,{
            constructor: {
                configurable: true,
                enumerable: true,
                value: Square,
                writable: true
            }
        });

        Square.prototype.toString = function(){
            return "[Square " + this.length + "x" + this.width + "]";
        };
        
        // 下面这段用调用父类的方法toString完成同样的工作
        Square.prototype.toString = function(){
            var text = Rectangle.prototype.toString.call(this); // 这里的call指的也是这个类的实例对象。
            return text.replace("Rectangle", "Square");
        };   
```

####对象模式
#####模块模式
js中所有属性都是公开的，如果对象希望有自己的私有属性，那就必须用到 模块模式(自执行函数，产生闭包来隔离变量) 来解决问题。
```
        // 基本格式
        var yourObject = (function(){
                // private data
                return {
                    // public methods and properties
                }
        })();
        
        // 一个例子,暴露模块模式，定义的私有属性和方法放在闭包中，返回的内容（接口）用对象写在一起，比单纯的模块模式易读
                var person = (function(){
                    var age = 18;
                    var getAge = function(){
                        return age;
                    };
                    var growOlder = function(){
                        age++;
                    };
        
                    return {
                        name:  "feifei",
                        getAge: getAge,
                        growOlder: growOlder
                    }
                })();
        
                console.log(person.age); // 私有属性,访问不到，undefined
                console.log(person.getAge()); // 18
                person.growOlder();
                console.log(person.getAge()); // 19
                console.log(person.name); // feifei
```



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










