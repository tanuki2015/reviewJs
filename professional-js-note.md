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
string最重要的一点是，字符串一旦创建不可被改变。（想一下内存中的状况就能理解了）

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

操作符(略......)






