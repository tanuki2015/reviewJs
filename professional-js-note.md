#professional js note
##JavaScript��������
###js�������ͷ��������֣�

ֵ����5�֣�
1. number
2. string
3. boolean
4. null
5. undefined.

��������һ����
object
______

typeof���صĽ���ַ���������������֮һ��

typeof�������Ĳ����������Ǳ�������������
```
        var a = "I'm a string";
        console.log(typeof a); // ��������a�������
        console.log(typeof 123); // ��������������
```

####Udefined����ֻ��һ��ֵ undefined
```
        var message; // δ��ֵ��ϵͳ�Զ���ֵundefined
        // ��������Ƚ���������
        console.log(message == undefined); // true
```

������û�ж���ı�����Ψһ�����Ĳ�����typeof�������������ᱨ��
```
        var message;
        console.log(message) // undefined
        console.log(age) // ����:age is not defined
```
����˼���Ƕ�һ��δ�����ı���typeof������ֵ��Ҳ�� undefined
������û��ֵ��û�б����壬��ϵͳ��˵�������ã����Զ���undefined���ɴ˵ó� undefined==undefined
```
var message;
        console.log(message);  // undefined
        console.log(typeof message == typeof age); //true
```

####Null����
null����Ҳֻ��һ��ֵ null���߼��Ͻ�null��һ���ն���ָ�룬����typeof����object��
�˼���һ�������ֻ�������ڿ����֣�����object�ͺܺ����ˡ�

Ȼ��˵undefined������null����ֻ�����Ϊ�����ڴ��л�Ĵ����У�ֵ������ʵҲ��һ���ڴ��ַ��ָ��ʵ�ʵ��ڴ��е�ֵ
����������÷������ơ�
����ECMA-262�涨null==undefined
`console.log(null == undefined); // true`

####Boolean
Boolean����������ֵtrue��false
����ÿ�����Ͷ�������Boolean()����ת����Booleanֵ

��������        ת��Ϊtrueֵ        ת��Ϊfalseֵ
1. number       ��������               0��NaN
2. string       �ǿ��ַ���           ���ַ���
3. boolean      true                false
4. undefined    ��N/A��            undefined
5. object       ���ж���            null
6. null          (N/A)            false      (��һ���Ҽӵ�)

N/A ��ʾnot applicable ������

```
        console.log(Boolean(3)); // true ����Ϊ��
        console.log(true == 3); // false �������3��������3,
```
�κ������ж����ݶ���ת����Boolean���ͣ�����Ҫ������ת������

####Number
��Ҫ�������͸�������
��������ʮ���ƣ�8���ƺ�16���ơ�
����������С�����������һ����ͺ��������һλ��Ч���֡�
Ҳ������e����ʾ������
`var floatNum = 3.125e7 // 3.125 * 10��7�η� =31250000`

ע��js���㾫�������⣬�磺
`console.log(0.1+0.2); // ������0.3 ������0.0000000000000004`

����js��Χ�ļ���ͼ�С������infinity��-infinity��ʾ

NaN��ʾ�ڴ�number��ʱ��û�з���number���ͷ������NaN����ʵ�õĵط����ڳ���0��ʱ�����ڱ�����
NaN�������ص㣺
1. �κ�����NaN�������������NaN��
2. NaN ������ NaN��

��isNaN��������������ж�ĳ�����Ƿ�ΪNaN��

ת����ֵ��3������
Number()    Ӧ������������
parseInt()  �����ַ�����
parseFloat()  �ַ�����

####String
string����Ҫ��һ���ǣ��ַ���һ���������ɱ��ı䡣�������������У��ַ�����Ϊ�������ͱ�������js�����������ͳ��

�ַ���ת��
number��boolean��object��string����toString()������
�ر�ĵط�������string���Ͷ���toString������toString(����)�����ַ�����һ��������

####Object
js�����ж���̳���Object���������湫�������Ժͷ�����
1. constructor
2. hasOwnPropert()
3. isPrototypeOf()
4. propertyIsEnumerable()
5. toLocaleString()
6. toString()
7. valueOf()
------

������(��......)

####����������
���߼���
&& �߼���
|| �߼���

�����κ�ֵ����������һ���߼�����ֵ
���� ����һ���ã��൱��Boolean��������һ������ɲ���ֵ���ڶ�������������Ӧ�Ĳ���ֵ
```
console.log(!!"blue"); //true
console.log(!!0); //false
console.log(!!NaN); //false
```

&& �߼��� ��·����
```
var found = true;
var result = (found && someUndefinedVariable); // �����ֵ��ֵ��������
alert(result);  // ����ִ��

// �����·

var found = false;
var result = (found && someUndefinedVariable); // �����ֵ��ֵ��������
alert(result);  // false

```

|| �߼��� ��·����
���߼���һ��Ҳ�Ƕ�·��ֻ���߼���ͬ����
js�г��õĵط��ǣ������������null��undefinedֵ
`var myObject = preferredObject || backupObject`
ǰ��Ϊ���򷵻�ǰ���ֵ�����򷵻ر���ֵ��

------

+ ������
��Ҫע����ǣ���������������ַ������ڿ��ǵ������ַ����Ĳ��������Զ��ᱻת��Ϊ�ַ�����ִ�����ӵĲ�����
`var result = 2 + '3'; // 23`

- ������
�����ַ��������number��������Ϊ������ֻ�������ֵļ���

����Function
1. �����Դ�arguments���󣬴���Ĳ��������ֲ�����ʹ�ã�������arguments�е�����ͬ�����¡�
2. û�����أ�ֻ��ͨ������ǩ��������ͬ��Ӧ��ģ�����ء�

##���� ��������ڴ�����
��2015/09/10 11:26��
1. ִ�л�����execution context��
2. ������scope��
3. this ��execution context������������ߵ�һ�����ԣ�

���Ƕ�֪���������Ǳ����ı߽磬���������ȷ������߽磿������ִ�л�����ȷ�ϡ�
ִ�л�����һ�����󣬴����������еı����ͺ�����
ÿ����������һ��ִ�л����Ķ��󣨽��������activation object��

��ȫ��ִ�е�ʱ��ֻ��һ��activation object��������һ������������scope chain�������scope chain�е�һ��������ǵ�ǰ��activation object�����Ժ��Ӻ���ִ�е�ʱ����ᴴ����activation object����������ӵ����������У�Ȼ���ӻ�����execution context����ѹ���ջ��ÿ���Ȩ���ӻ����еĴ������scope chain�е�activation object��һ��һ���Ĳ��ұ����ͺ�����ʹ�����ǡ�������Ӻ���ִ����ϣ��򱻶�ջ�����������ӻ��������٣�����Ȩת�ص��ϼ�ִ�л�����

jsͨ��scope chain ������ʵ�������򣬶������򱳺���execution context�Ļ��Ƶ���ʵ�֡�

this��arguments�Ǻ�����Ĭ�����ԣ� thisͨ��ָ���ĵ����ߣ���������û����ʽ�ĵ�����ʱ������Ϊ��ȫ�ֻ�������������������ȫ�ֻ����У�Ҳ����activation object��һ��this���ԣ�����ֵ����window��

##������ ��������
###Object
���帴�����ݡ�
������;���ö����������������
����ע�⣺BOM��DOM�������������ǲ���ECMA-262�����壬���������ṩ�Ͷ��塣
--���ݶ������ʱ���Ա���ֵ�������������룬�Զ����ѡ�����ö�������װ��

��������ֵ���÷���
```
        var obj = {
            name: "feifei",
            age: 100,
            sayHi: function(){
                console.log("Hi");
            }
        };

        // key��������������ֵ�ö���.key������ʾ

        for(var key in obj){
            console.log(key + ": ",obj[key]);
        }

        // ����Ƿ�Ϊ ��������

        function hasPubProperty(attr,obj){
            return (attr in obj) && !(obj.hasOwnProperty(attr));
        }
```
���������֣�1�������ԣ������ģ���2����������
�������Ե���Ĭ�ϵ�put�������ã����������������£�

```
        // ������������getter �� setter ���÷���
        var person1 = {
            _name: "feifei", // Լ����˽��������ǰ���»��ߣ���ʵ���ϻ��ǹ��е�
            get name(){ //�﷨��һ��������function
                console.log("read name: ");
                return this._name;
            },
            set name(value){
                console.log("write name: " + value);
                this._name = value;
            }
        };
        console.log(person1.name);  // read name: feifei ������������get name ����
        person1.name = "bobo";  // write name: bobo д������������set name ����
```
���������Ե���;����ϣ����ȡ��д������ͬʱ�ᴥ��һЩ��Ϊ�������ʱ�򣬾��Լ�дget��set������

####����ԭ�ͣ�prototype��
```
        var Person = function(){};
        var person1 = new Person;

        console.log(Person.prototype.hasOwnProperty("constructor")); // true
        console.log(person1.__proto__.hasOwnProperty("constructor")); // true
        console.log(Person.prototype.hasOwnProperty == person1.__proto__.hasOwnProperty); // true
        // ����֤�������캯����ԭ�ͺ���ʵ����ԭ����һ������
        // ֻ�������ڹ��캯������prototype������֣���ʵ������__proto__������֣������������ʵ�ֵģ�
        
        console.log(Person.__proto__ == Function.prototype); // true
        console.log(Person.__proto__ == Object.prototype); // false
        // ������֤�������캯����ԭ��Ҳָ��������ԭ��--Function��ԭ�͡�
        // ��Ҳ˵�������캯������һ������Ҳ��һ������������˫�����
        // ���������й��캯��������prototype���ԣ�Ҳ����ͨ�����__proto__����
```

ԭ�Ͷ����constructor���ԣ�ָ�򴴽����Ĺ��캯������ϵͳ���õļ������캯��������Object,Function,Array�ȣ�
�о�������һ������ģʽ��Ϊ�˴��������Ķ�������ڡ�
constructorֻ���������ĺ����йأ������̳��޹ء�
```
        function FnA(){}
        function FnB(){}

        var objA = new FnA;

        FnB.prototype = new FnA; // ��һ�����ע�͵�������������Ϊfalse��true��false
        var objB = new FnB;

        // objB���ڼ̳���FnA�������Ĺ��캯�����Ǵ������ĺ���
        console.log(objB.constructor == objA.constructor); // true �ⶼ����ԭ�����ҵ���
        console.log(objB instanceof FnB); //true
        console.log(objB instanceof FnA); //true
```

��forѭ�������˽������

```
        var empty = {name:"feifei", age: 99};

        for(var property in empty){
            if(empty.hasOwnProperty(property)){
                console.log(property);
            }
        }

```

####�̳�
js�ǻ��ڶ�������ԣ�object base������js������Զ����Ƕ���������ļ򵥳��֡�������������ڶ������������˼����������ĸ��������������
����ôһ����������˻��ڶ�������������ȫ��ͬ��������

������������װ���̳кͶ�̬��

��װ����������У�������ö�˵��

�̳У�js��ֻ�ж��󣬵�Ȼ̸����ʲô�̳У����ǣ�Ϊ����js�м̳е����ԣ������˸��ָ��������۵ķ�������򵥵��ǻ���ԭ�����ļ̳С�
��������������У��������࣬���������࣬����˵�������Դ��̳У�ֱ�ӾͿ���ʵ�֡�

����̬������jsû�к���ǩ��������Ҳֻ����ת��ȥģ�⡣

Object.create()����������һ���̳еĶ���

#####����ļ̳У�����ԭ�͵ķ���

```
        // ʹ�������������������̨�Ĳ�������Object.create����
        
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

��һ�����ӣ�
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

        console.log(person2 instanceof person1);    // ��������ļ̳У��漰����ʵ����ʵ��һ�����ɹ��캯��new������
```

#####����ļ̳У����ڹ��캯��
Ϊʲô��Ҫ���캯���ļ̳У������Ѿ���ԭ�����ļ̳�����
��Ϊԭ�����ļ̳�ֻ�Ǽ򵥵ĵ��������ļ̳У���Ϊ�˱���ĳ������µļ̳У��͵��õ����캯���ļ̳��ˡ�

```
 function MyConstructor(){}  // ������һ��������ʱ��js�����������������
        
        MyConstructor.prototype = Object.create(Object.prototype,{
            constructor:{
                configurable: true,
                enumerable: true,
                value: MyConstructor,
                writable: true
            }
        }); //ϵͳ����һ���̳еĶ��󣬲�������constructor��������Ϊ�乹�캯����
        
        console.log(MyConstructor.prototype.constructor == MyConstructor);  // ��������Ϊ true
        // �ɼ��κκ�����ԭ���϶��������constructor���������ǹ��캯����
```

��ͳ�Ĺ��캯���̳�ͨ�����£�

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

�����������ڼ̳е�ʱ�򣬸���Ĺ��캯���������У����п����ڲ����ı������£���ʼ�������⣬����������ĸĽ�������
ʹ��Object.create()����,���������κι��캯����û�в���������

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

ͨ����˵������ļ̳з����Ѿ������ˣ�����ʱ��������Ҫ���ø���Ĺ��캯��ʱ������Ҫ��call��apply���������á�
��Ϊ���ַ�ʽģ��������������Ի�����ļ̳У�����Ҳ��Ϊjs��α��̳С�
```
        // inherits from Rectangle
        function Square(size){
            Rectangle.call(this,size,size); // ���ø��๹�캯��������Ĵ��벻��
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
        
        // ��������õ��ø���ķ���toString���ͬ���Ĺ���
        Square.prototype.toString = function(){
            var text = Rectangle.prototype.toString.call(this); // �����callָ��Ҳ��������ʵ������
            return text.replace("Rectangle", "Square");
        };   
```

####����ģʽ
#####ģ��ģʽ
js���������Զ��ǹ����ģ��������ϣ�����Լ���˽�����ԣ��Ǿͱ����õ� ģ��ģʽ(��ִ�к����������հ����������) ��������⡣
```
        // ������ʽ
        var yourObject = (function(){
                // private data
                return {
                    // public methods and properties
                }
        })();
        
        // һ������,��¶ģ��ģʽ�������˽�����Ժͷ������ڱհ��У����ص����ݣ��ӿڣ��ö���д��һ�𣬱ȵ�����ģ��ģʽ�׶�
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
        
                console.log(person.age); // ˽������,���ʲ�����undefined
                console.log(person.getAge()); // 18
                person.growOlder();
                console.log(person.getAge()); // 19
                console.log(person.name); // feifei
```



###Array
������飺
���淽����`if(value instanceOf Array){'do something'};`

ECMAScript5֧�ֵģ� Array.isArray()������
`if(Array.isArray(value)){'do something'};`

ת�����������ж����е�toString(),valueOf(),toLocalString().

�����������Щת������ʱ�������е�ÿһ��ֱ���ã���Ϊ��ȡ����Ĳ�������һ��һ�������

join()����
join����˼����룬��Ȼ���ö�������Ϊһ�����join������ķ�����������ж�����������ֵ��string��

join()����һ��������Ϊ�ָ������������ַ����зָ��ַ���

```
var colors = ["red","green","blue"];
console.log(colors.join()); // red,green,blue ����������Ĭ���Ƕ���
console.log(colors.join("|")); // red|green|blue
```

####ջ������last-in-first-out��
��΢���루ѹջ-��ջ����֪����ֻ��Ҫ��ջ�ͳ�ջ�������������ˣ�push(),pop().
��Ȼ�Ǻ������Ȼ�Ǵ�����β�����в�����

####���з�����first-in-first-out��
��ȻҲ��Ҫ�����������Ŷӵĳ������������е�ʱ��Ӻ��������push()�Ϳ�����
����ʱ���ǰͷ������Ҫshift()����

���ϳ�ջ�ͳ����еķ����Ļ��з���ֵ�����ǳ������Ǹ��һﱾ��

���Ƶģ�Ϊ�˴��෴�ķ���������У�������unshift()������ͬpop()���ʹ�á�

####�������򷽷�
reverse()��ת����
sort()�Ƚ����飬�����ǱȽϺ�����

####��������
�⼸�����������з���ֵ
concat()
slice()
splice()

####λ�÷���
indexOf() //����˼�巵������ֵ
lastIdexOf() //�Ӻ��濪ʼ����

####��������
every() ��p96
some()
filter()
map()
forEach()

####�鲢����
reduce() ��p97
reduceRight()

###Date��
�о��Ƚ����õ��������
```
        var start = Date.now();
        for(var i=0;i<1000000;i++){};
        var end = Date.now();
        console.log(end-start);
```










