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
string����Ҫ��һ���ǣ��ַ���һ���������ɱ��ı䡣����һ���ڴ��е�״����������ˣ�

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

������(��......)






