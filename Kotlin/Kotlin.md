## 变量
```kotlin
/*
声明常量的三种正确方式
1.在顶层声明
2.在object修饰的类中声明，在kotlin中称为对象声明，它相当于Java中一种形式的单例类 (未学)
3.在伴生对象中声明 (未学)
 */

const val P: Int = 10 // 在顶层声明常量


fun main() {
    // 关键字 变量名: 数据类型 = xxx      val: 不可变 var: 可变
    val a: Int = 10 // 立即初始化
    val b: Int // 不初始化，必须指明类型
    b = 10// 只能赋值一次
    println(b)

    // 声明可空变量 var/val 变量名: 数据类型？ = xxx
    var c: Int? = null // var c: Int = null 错误
}

class Test1(){
    // 在类中必须初始化 或者使用 lateinit关键字不能用于基本类型
    var a: Int
    init {
        a = 10
    }
}
```
## 数据类型
```kotlin
fun main() {
    var a: Byte = 1 // 字节
    var b: Short = 1 // 短整型
    var c: Int = 1 // 整形
    var d: Long = 1L // 长整型
    var e: Float = 1.0F // 单精度
    var f: Double = 1.0 // 双精度
    var char1: Char = '1' // 单引号 ‘ ’表示 并且不能直接视为数字 不过可以显式转换为数字 支持字符转义

    // 不支持八进制
    var g: Int = 0xff // 十六进制
    var h: Int = 0b1111 // 二进制
    var i: Int = 123 // 十进制
    var j: Int = 123_123_123 // 可以使用 '_' 分割数字
    println(j)

    // 两个数的比较 ==: 判断值是否相同 ===: 判断地址是否相同
    var x: Int = 123
    var y: Int = 129
    println("x == y 结果为 ${x == y}, x === y 结果为 ${x === y}")
    // Int类型值在[-128, 127]之间 使用同一个对象

    /*
    显式转换: 较小的类型不会被隐式转换为更大的类型，故而系统提供了显式转换。提供的显式转换方法如下：
    toByte() => 转换为字节型
    toShort() => 转换为短整型
    toInt() => 转换为整型
    toLong() => 转换为长整型
    toFloat() => 转换为浮点型
    toDouble() => 转换为双精度浮点型
    toChar() => 转换为字符型
    toString() => 转换为字符串型
     */
    var numA: Int = 97
    println(numA.toByte())
    println(numA.toShort())
    println(numA.toInt())
    println(numA.toLong())
    println(numA.toFloat())
    println(numA.toDouble())
    println(numA.toChar())
    println(numA.toString())
    // 隐式转换 类型是从上下文推断出来的，即算术运算则被重载为适当的转换
    var num = 10L + 10 // 自动转为Long型

    /*
    位运算符
    shl(bits) => 有符号向左移 (类似Java的<<)
    shr(bits) => 有符号向右移 (类似Java的>>)
    ushr(bits) => 无符号向右移 (类似Java的>>>)
    and(bits) => 位运算符 and (同Java中的按位与)
    or(bits) => 位运算符 or (同Java中的按位或)
    xor(bits) => 位运算符 xor (同Java中的按位异或)
    inv() => 位运算符 按位取反 (同Java中的按位取反)
     */
    var num1: Int = 8
    println(num1 shl(2))

    /*
    布尔类型（Boolean）
    Boolean关键字表示布尔类型，并且其值有true和false

    逻辑操作符（与Java相同）
    ' || ' => 逻辑或（或者）
    ' && ' => 逻辑与（并且）
    ' ! ' => 逻辑非（取反）
     */

    /*
    String 字符串类型 不可变的 可以通过str[index]来访问
    可以用 ${} 引用变量的值或者表达式的值 {}里可以是一个表达式或者变量名
    */
    var str: String = "hello world"
    for (i in str)
        print(i)
    println()
    // 数组

    /*
    1.arrayOf() 创建一个数组，参数是一个可变参数的泛型对象
    2.arrayOfNulls() 用于创建一个指定数据类型且可以为空元素的给定元素个数的数组
    3.工厂函数 使用一个工厂函数Array()，它使用数组大小和返回给定其索引的每个数组元素的初始值的函数
    Array() => 第一个参数表示数组元素的个数，第二个参数则为使用其元素下标组成的表达式
     */

    var arr1 = arrayOf(1, 2, 3, 4)
    arr1[1] = 3 // 可以修改值
    for (i in arr1)
        print("$i ")
    println()

    var arr2 = arrayOfNulls<Int>(5)
    for (i in arr2)
        print("$i ")
    println()

    var arr3 = Array(5, {idx -> idx * 2})
    for (i in arr3)
        print("$i ")
    println()

    /*
    原始类型数组
    ByteArray => 表示字节型数组
    ShortArray => 表示短整型数组
    IntArray => 表示整型数组
    LongArray => 表示长整型数组
    BooleanArray => 表示布尔型数组
    CharArray => 表示字符型数组
    FloatArray => 表示浮点型数组
    DoubleArray => 表示双精度浮点型数组
    Kotlin中不支持字符串类型这种原始类型数组
     */

    var arr4: IntArray = intArrayOf(1, 2, 3)
    for (i in arr4)
        print("$i ")
    println()
}
```
## 控制语句
```kotlin
fun main() {
    /*
    1.if语句 可以作为一个表达式
    一个块结构的最后一句表达式的值为块的值
    2.for语句
    3.when语句
    4.while语句
    5.do while语句
    6.跳转语句 return、break、continue  (与C语言一样)

    检查值是否存在于集合或数组中
    操作符 in 在 !in 不在 只能适用于数值型

    检查值是否为指定类型的值
    操作符 is 是 !is 不是
     */

    // if
    var num1 = 2
    var num2 = if (num1 > 1){
        num1 ++
        println(num1)
        num1 ++
    } else {
        num1 ++
    }
    println(num2)

    // for
    for (i in 0 until 10) // [0, 9]
        println("$i ")
    for (i in 0 until 10 step 2) // [0, 2, 4, 6, 8]
        println("$i ")
    for (i in 0 .. 9) // [0, 9]
        println("$i ")
    for (i in 9 downTo 0) // [9, 0]
        println("$i ")

    // when 如果不带参数和if-elseif-else 差不多
    when(5){
        1 -> {
            println("1")
        }
        2 -> println("2")
        3 -> println("3")
        5 -> {
            println("5")
        }
        else -> {
            println("0")
        }
    }

    // while语句 与Java中的while循环一样
    //do...while语句 与Java中的do...while循环一样

}
```
## 空值判断与处理
```kotlin
fun main() {
    /*
    定义一个可空类型的变量的格式为：修饰符 变量名: 类型? = 值
    当一个函数/方法有返回值时，如果方法中的代码使用?.去返回一个值，那么方法的返回值的类型后面也要加上?符号
     */
    var a: String? = null

    /*
    判断是否为null
     */

    println(a?.length)
    if (a == null)
        println("a is null")
    else
        println("a not null")

    println(a?.length)

    /*
    let操作符
    let操作符的作用：当时用符号?.验证的时候忽略掉null
    let的用法：变量?.let{ ... }
     */
    a?.let { println(a) }
    a = "hhh"
    a?.let { println(a) }

    /*
    ?： 这个操作符表示在判断一个可空类型时，会返回一个我们自己设定好的默认值.
    !! 这个操作符表示在判断一个可空类型时，会显示的抛出空引用异常（NullPointException）.
    as? 这个操作符表示为安全的类型转换.
     */
    var len = 0
    len = a?.length ?: 1
    println(len)

//    val str : String? = null
//    println(str!!.length)

    var b: Int? = "hhh" as? Int
    println(b)
}
```
## 函数
```kotlin
/*
定义格式为：可见性修饰符 fun 函数名(参数名 ：类型,...) : 返回值{}
默认为public可见性修饰符
返回值为Unit类型 这个类可以理解为函数无返回值。

 */

fun main() {
    println(sum1(1, 2))
    println(sum2())
    println(sum3(1, 2, 3, 4, 5))
    println(sum4(1, 1))
}

//基本格式
fun sum1(a: Int, b: Int): Int{
    return a + b
}

// 参数为默认值 可以对是参数有默认值的参数不传递参数值。
fun sum2(a: Int = 1, b: Int = 1): Int{
    return a + b
}
/*
可变数量参数 当一个函数中的参数是不定数量的个数并且是同一个类型，则可是使用vararg修饰符去修饰这个变量，
则被vararg修饰的参数相当于一个固定类型的数组。
声明格式：fun 函数名(vararg 参数名 ： 类型，...) ：返回值{}
 */
fun sum3(vararg arr: Int): Int{
    var sum = 0
    for (i in arr)
        sum += i
    return sum
}

// 单表达式函数

fun sum4(a: Int, b: Int) = a + b



```
## 字符串操作
```kotlin
// 字符串操作
fun main() {
    var str: String = "hello world"
    // 获取第一个元素
    println(str.first())
    println(str[0])
    println(str.firstOrNull())

    // 获取最后一个元素
    println(str.last())
    println(str.lastOrNull())

    println(str.length) // 获取长度

    // 查找等于某一个字符的最后一个元素
    println(str.last { it == 'h' }) //未查找到满足条件的元素, 抛出NoSuchElementException异常
    str.lastOrNull { it == 'i' } // 未查找到满足条件的元素, 会返回null

    println(str.find { it == 'l' })
    println(str.findLast { it == 'l' })

    println(str.indexOf('h')) // 查找某一个元素
    str.indexOfFirst{it == 'h'} // 查找某一个元素
    println(str.indexOf('o',0)) // 某个下标 查找某一个元素
    println(str.indexOf("very",0)) // 从某个下标查找相同的字符串
    println(str.lastIndexOf('o')) // 查找某元素最后一次出现的下标
    println(str.lastIndexOf("good")) // 查找某个字符串最后一次出现的下标

    println(str.substring(0,5)) // 用subString()函数截取
    println(str.subSequence(0, 5)) // 用subSequence()函数截取

    println(str.replace('l', ' ')) // 把原字符串中的某一个字符全部替换成新的字符。
    println(str.replace("ll", "hhh")) // 把原字符串中的某一个字符串全部替换成新的字符串。
    println(str.replaceFirst('l', 'h')) // 把满足条件的第一个字符或字符串替换成新的字符或字符串

    println(str.replaceBefore('h', "hhh")) // 在满足第一个字符或字符串后面的字符串，包含满足条件字符或字符串自身，并在其前面加上新的字符串。
    println(str.replaceAfter('h', "aaa")) // 截取满足条件的第一个字符或字符串前面的字符串，包含满足条件字符或字符串自身，并在其后面加上新的字符串。
    println(str.replaceBeforeLast('h', "qqqq")) // 在满足条件的最后一个字符或字符串后面的字符串，包含满足条件字符或字符串自身，并在其前面加上新的字符串。

    // 字符串分割
    for (i in str.split(' ')) // 可以有多个参数
        println("$i ")
    println()
    for (i in str.split(" "))
        println("$i ")

    println(str.count{it == 'l'}) // 统计每个字符的重复次数

    println(str.reversed()) // 字符串反转
}
```
## 类
```kotlin
import java.time.Period

fun main() {
    /*
    类的格式 class 类名(){
    }

    类可以有属性 用val var声明 当用var修饰时，必须为属性赋默认值
    get、set方法不能直接赋值 要用field赋值
    lateinit 该关键字必须声明在类的主体内，并且只能是用var修饰的属性。并且该属性没有自定义的setter()与getter()函数。

    主构造函数 在类名的括号内传入 在init代码块中初始化
    init 只能包含初始化代码能使用主构造器的参数
    此构造函数 用constructor 关键字 需要通过另一个辅助构造函数直接或间接地委派给主构造函数
    使用this关键字对同一类的另一个构造函数进行委派：

    类的实例化 调用构造函数

    超类(Any) 与Java中的Object相同
    类的继承 定义继承类的关键字为：open。不管是类、还是成员都需要使用open关键字。
    当存在主构造函数时，主构造函数一般实现基类型中参数最多的构造函数，参数少的构造函数则用this关键字引用即可了。

    重载 父类函数默认被final修饰 需要加上open才能重载 并在重载函数前加上override关键字

     */
    var person = Person(12)
    person.age = 123
    person.name = "zs"
    println(person.name + person.age)
    var stu = Student(12)
    println(stu.age)
    println(stu.name)
}

open class Person(a: Int){
    open var age: Int = 0
        set(value){field = value}
        get() = field
    open var name = ""
        set(value) {field = value}
        get() = field
    init {
        age = a
    }
    constructor (str: String, age: Int): this(age){
        name = str
    }
    open fun p(){
        println("hhh")
    }
}

class Student(a: Int): Person(a){
    override fun p(){
        println("666")
    }
    override var age: Int = 100
}
```
## 接口类与枚举类
```kotlin
/*
枚举类
enum class 类名{
}

访问枚举常量
不需要实例化枚举类就可以访问枚举常量
使用方式为：
枚举类名.枚举常量.属性

可以初始化枚举常量

接口类
interface 接口名{
}

 */

enum class num(var a: Int){
    one(1), two(2), three(3)
}

fun main() {
    println(num.two.a)
    var sum = inpl(1,1)
    println(sum.sum())
}

interface test{
    var a: Int
    var b: Int
    fun sum(): Int // 不带结构体的函数可以省略大括号
}

class inpl(override var a: Int, override var b: Int): test { // 重写属性的时候可以在实现类的类参数中
    override fun sum(): Int {
        return a + b;
    }

}

```
## 数据类和密封类（未完成）
```kotlin
/*
数据类
data class 类名(var param1: 数据类型,...){}
在没有结构体的时候，大括号{}可省略。
构造函数中必须存在至少一个参数，并且必须使用val或var修饰
参数的默认值可有可无。（若要实例一个无参数的数据类，则就要用到默认值）

自动生成
equals()函数与hasCode()函数
toString()函数，由类名（参数1 = 值1，参数2 = 值2，....）构成
由所定义的属性自动生成component1()、component2()、...、componentN()函数，其对应于属性的声明顺序。
copy()函数

数据类的特性
主构造函数需要至少有一个参数
主构造函数的所有参数需要标记为 val 或 var；
数据类不能是抽象、开放、密封或者内部的；
数据类是可以实现接口的，如(序列化接口)，同时也是可以继承其他类的，如继承自一个密封类。

密封类
sealed class 类名()
密封类是不能被实例化的
 */

fun main() {
    var user = User(1, "zs")
    var newuser = user.copy(age = 88) // 数据类的修改 可以只修改某一个属性
    println(newuser) // 自动实现tostring方法
    println(Test.User(1,"zs"))
}

data class User(var age: Int, var name: String){

}

sealed class Test(){
    data class User(var age: Int, var name: String)
}
```
## 抽象类与内部类
```kotlin
/*
抽象类
声明一个抽象（类或函数）的关键字为：abstract
抽象可以分为抽象类、抽象函数、抽象属性。
一个抽象类和普通类的区别在于抽象类除了可以有其自己的属性、构造函数、方法等组成部分，
还包含了抽象函数以及抽象属性。
抽象类不能直接被实例化

内部类
1.嵌套类 调用格式为：外部类.嵌套类().嵌套类方法/属性 套类不能使用外部类的属性和成员
2.内部类 调用内部类的属性或方法的格式为：外部类().内部类().内部类方法/属性 内部类不能使用外部类的属性和成员
3.匿名内部类 未完成
4.局部类 即定义在方法（函数）中的类。
局部类只能在定义该局部类的方法中使用。
定义在实例方法中的局部类可以访问外部类的所有变量和方法。但不能修改
局部类中的可以定义属性、方法。并且可以修改局部方法中的变量。
 */

fun main() {
    var s = imp()
    println(s.sum(1,1))
    println(One.Two().str)
    println(Outer().Inner().str)
    test()
}

abstract class test1{
    abstract fun sum(a: Int, b: Int): Int
}

class imp: test1() {
    override fun sum(a: Int, b: Int): Int {
        return a + b
    }
}

// 嵌套类
class One(){
    var str: String = "hhh"
    class Two(){
        var str: String = "hhh"
    }
}

//内部类
class Outer(){
    var str: String = "hhh"
    inner class Inner(){
        var str: String = "hhh"
    }
}

//局部类
fun test(){
    var str = "123123"
    class Inner{
        fun print(){
            println("$str")
            str = "hhhhh"
        }
    }
    var inner = Inner()
    inner.print()
    println("$str")
}



```
## lambda与匿名函数
```kotlin
fun main() {
    // 1.无参数的情况 var/val 变量名 = {代码}
    // invoke()函数：表示为通过函数变量调用自身 hi.invoke()等价于hi()
    var hi = { println("hello world")}
    hi()


    /*
2.有参数的情况
val/var 变量名 : (参数的类型，参数类型，...) -> 返回值类型 = {参数1，参数2，... -> 操作参数的代码 }
可等价于 val/var 变量名 = { 参数1 ： 类型，参数2 : 类型, ... -> 操作参数的代码 }
此种写法：即表达式的返回值类型会根据操作的代码自推导出来。
*/
    var sum1: (Int, Int) -> Int = {a, b -> a + b}
    println(sum1(1, 1))

    var sum2 = {a: Int, b: Int -> a + b}
    println(sum2(1, 1))

    println(sum3(1) { num1, num2 -> num1 + num2 })

    /*
it并不是Kotlin中的一个关键字(保留字)。
it是在当一个高阶函数中Lambda表达式的参数只有一个的时候可以使用it来使用此参数
*/
    println(sum4(1, { it.toInt() }))

    // 在使用Lambda表达式的时候，可以用下划线(_)表示未使用的参数，表示不处理这个参数。
    var sum5: (Int, Int) -> Int = {_, b -> b}
    println(sum5(1, 1))

    // 匿名函数例子
    var sum6 = fun(a: Int, b: Int) = a + b
    var sum7 = fun(a: Int, b: Int): Int = a + b
    var sum8 = fun(a: Int, b: Int): Int{
        return a + b
    }
}


/*
高阶函数，当Lambda表达式作为其一个参数时，只为其表达式提供了参数类型与返回类型
所以，我们在调用此高阶函数的时候我们要为该Lambda表达式写出它的具体实现。
*/
fun sum3(a: Int, b: (num1: Int, num2: Int) -> Int) : Int{
    return a + b(2,3)
}

fun sum4(a: Int, b: (String) -> Int): Int{
    return a + b("2")
}

/*
总结1.匿名函数传值时在小括号内传递 而lambda表达式传值 可以省略小括号
2.匿名函数通过return返回 lambda返回值为最后一句的值
*/

```
