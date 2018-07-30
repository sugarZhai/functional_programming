# 函数式编程Functional-Programming

1、参考链接
https://www.cnblogs.com/tugenhua0707/p/5046854.html
https://zhuanlan.zhihu.com/p/21714695
https://www.ibm.com/developerworks/cn/web/1006_qiujt_jsfunctional/
https://github.com/MostlyAdequate/mostly-adequate-guide




2、apply和call的区别
 apply和call都能继承另外一个对象的方法和属性； Function.apply(obj,args)方法能接收两个参数 obj：这个对象将代替Function类里this对象 args：这个是数组，它将作为参数传给Function（args-->arguments）
 call:和apply的意思一样,只不过是参数列表不一样. Function.call(obj,[param1[,param2[,…[,paramN]]]]) obj：这个对象将代替Function类里this对象 params：这个是一个参数列表
 使用apply的情况：在给对象参数的情况下,如果参数的形式是数组的时候,比如apply示例里面传递了参数arguments,这个参数是数组类型。
 使用call的情况： 如果我的Person的参数列表是这样的(age,name),而Student的参数列表是(name,age,grade),这样就可以用call来实现了,也就是直接指定参数列表对应值的位置(Person.call(this,age,name,grade));
 
 Apply巧妙之处：可以将一个数组默认的转换为一个参数列表[param1,param2,param3] (apply会将一个数组装换为一个参数接一个参数的传递给方法)
 Call巧妙之处:1、直接用A对象方法来替换B对象 2、直接用B对象来执行A对象的方法3、可以用 call 来实现继承 
 
 
 
 
 
 3、闭包的结构有如下2个特性
   
     1.封闭性：外界无法访问闭包内部的数据，如果在闭包内声明变量，外界是无法访问的，除非闭包主动向外界提供访问接口；
   
     2.持久性：一般的函数，调用完毕之后，系统自动注销函数，而对于闭包来说，在外部函数被调用之后，闭包结构依然保存在
   
    系统中，闭包中的数据依然存在，从而实现对数据的持久使用。
   
    缺点：
   
    使用闭包会占有内存资源，过多的使用闭包会导致内存溢出等.
    
    
 4、理解函数引用和函数调用的区别
 当引用函数时候，多个变量内存存储的是函数的相同的入口指针，因此对于同一个函数来讲，无论多少个变量引用，他们都是相等的，因为对于引用类型(对象，数组，函数等)都是比较的是内存地址，如果他们内存地址一样的话，说明是相同的；但是对于函数调用来讲，比如代码三;每次调用的时候，都被分配一个新的内存地址，所以他们的内存地址不相同，因此他们会返回false，但是对于代码二来讲，我们看到他们没有返回函数，只是返回数值，他们比较的不是内存地址，而是比较值，所以他们的值相等
 
 
 5、事实上柯里化是一种“预加载”函数的方法，通过传递较少的参数，得到一个已经记住了这些参数的新函数，某种意义上讲，这是一种对参数的“缓存”，是一种非常高效的编写函数的方法：