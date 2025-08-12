## C++与C#区别 ##   
| 对比点                | **C++**                                              | **C#**                                                                          |
| ------------------ | ---------------------------------------------------- | ------------------------------------------------------------------------------- |
| 🧱 **类型种类**        | 原始类型（`int`, `float`）、结构体（`struct`）、类（`class`）、指针、引用等 | 值类型（`int`, `struct`）、引用类型（`class`）、接口、委托、数组等                                    |
| 🧠 **类型系统基础**      | 无统一基类，类型间无继承关系（除非自定义）                                | 所有类型都继承自 `object`（System.Object）                                                |
| 📦 **值类型 vs 引用类型** | 自由混用（按语义/效率选择）                                       | 严格区分：`struct` 是值类型，`class` 是引用类型                                                |
| 📌 **内存管理**        | 手动管理（`new`/`delete` 或智能指针）                           | 自动内存管理（垃圾回收 GC）                                                                 |
| 🔗 **继承机制**        | 支持多继承（多个基类）                                          | 不支持类的多继承，只支持接口的多继承                                                              |
| 🧰 **类型扩展性**       | 模板（template）、继承、虚函数                                  | 接口、委托、泛型、LINQ、反射等                                                               |
| 🧠 **类型推断**        | `auto`（编译时类型推断）                                      | `var`（编译时）和 `dynamic`（运行时）                                                      |
| 📌 **指针支持**        | 全面支持                                                 | 默认不允许指针（需 `unsafe`）                                                             |
| 🧱 **结构体行为**       | 类似类（可继承、带方法等）                                        | 简化版类，**不能继承另一个 struct 或 class**，但可以实现接口                                         |
| 🔐 **访问权限**        | `public`、`private`、`protected`                       | 同样有 `public`、`private`、`protected`，但默认不同（C++ struct 默认 public，class 默认 private） |
| 📦 **装箱/拆箱**       | 无装箱概念                                                | 值类型 → 引用类型时会装箱，引用 → 值类型时要拆箱                                                     |

1.include就是引入头文件（包含函数声明等），cs没有，只需要using导入命名空间就好，命名空间就是一些方法写在这个作用域里，需要导入才能直接使用，否则要使用作用域名   
2.cpp没有静态类，有静态函数，可以不实例化直接使用，成员变量需要在类外赋值：  

    class Math {
    public:
        static int add(int a, int b) {
            return a + b;
        }
    };
    int main() {
        std::cout << Math::add(3, 5) << std::endl;  // 输出 8，不需要 Math 对象
        return 0;
    }
   
在 C# 中，static class 表示一个不能被实例化的类，它的所有成员必须是 static 的，成员变量在类内赋值：

    public static class MathTools
    {
        public static int Add(int a, int b)
        {
            return a + b;
        }

        public static int Multiply(int a, int b)
        {
            return a * b;
        }
    }
    class Program
    {
        static void Main()
        {
            int sum = MathTools.Add(3, 4);        // 不用 new 对象
            int product = MathTools.Multiply(2, 5);
            Console.WriteLine(sum);               // 输 出 7
            Console.WriteLine(product);           // 输出 10
        }
    }
3.cpp用cout<<""<<;cs用Console.WriteLine("Hello World!");Console.ReadKey();
第一个表示用Console静态类，输出完就关闭界面，第二个函数可以等待输入一个任意键再关闭
#### 4.cpp可以用指针操作内存，需要手动释放：delete；cs不允许访问内存，由cs自动管理 
5.当一个值类型转换为对象类型时，则被称为 装箱；另一方面，当一个对象类型转换为值类型时，则被称为 拆箱。  
6.cpp的auto是编译是确定类型，一旦推导不可改变；cs的动态类型是运行时类型，随时改变内部类型   
#### 7.cpp的类就是自定义的一个类型，然后当作int使用，class是个关键字，cs里也是，只不过class创建的类都是继承于object   
8.字符串（String）类型的值可以通过两种形式进行分配：引号和 @引号（将转义字符（\）当作普通字符对待，@ 字符串中可以任意换行，换行符及缩进空格都计算在字符串长度之内）

    string str = @"C:\Windows";
    string str = @"<script type=""text/javascript"">
    <!--
    -->
    </script>";
9.在 C# 中，所有类型（包括值类型和引用类型）最终都继承自 System.Object  
10.cpp可以继承多个，有多个父类，cs只能有一个
#### 11.cpp局部变量（函数内定义的普通变量）不初始化，它的值是未定义的（垃圾值）全局变量、静态变量如果不显式初始化，会自动初始化为零，类的成员变量如果在构造函数中不初始化，也是不确定值；cs局部变量必须初始化后才能使用，否则编译器报错，类中默认为0   
#### 12.cs的函数和变量都必须写在类中，不像cpp可以全局变量   
13.for循环：

    cpp：
        for (auto& element : collection) 
        {
            // 使用 element
        }
    cs：
        foreach (int num in numbers)
        {
            Console.WriteLine(num * num);
        }
14.cs的函数包括main函数都要写入类中，cpp全局都可以  
15.cpp类中可以分区规定成员可见性，cs每个必须写   
16.cpp实例化对象可以堆上和栈上：

    Person p(10);
    Person p=new Person(10);
cs实例化必须使用new，因为是自动管理内存：

    Person p=new Person();
#### 17.cpp的引用就是取了个别名，防止复制，属于语法；cs的引用类型保存的地址，赋值时是传地址，修改一个其他也会修改，类似指针，但是不需要解引用：

    class Person {
        public string name;
    }

    Person p1 = new Person();
    p1.name = "Alice";

    Person p2 = p1;  // p2 和 p1 指向同一对象（像指针）
    p2.name = "Bob";
    Console.WriteLine(p1.name);  // 输出 Bob
#### 值类型在栈上，引用在堆上    
18.cpp用class创建；类之后当作int一样使用；cs创建的类都继承于object    
#### 19.cs多了internal访问修饰符，只在当前程序可以访问，public其他程序也可以访问；和cpp一样默认private；类本身，cpp只要include就都可以见；cs默认对当当前程序可见   
20.格式化字符串

    cpp：
    #include <format>
    std::string s = std::format("I am {} years old", 25);
    cs：
    int age = 25;
    string s = string.Format("I am {0} years old", age);

21.cpp引用不额外分配内存，指针需要分配储存地址；cs引用类型储存的是对象的地址，数据在堆内存上；值类型可以直接写，引用类型必须new，除了string   
22.引用传递参数，cpp接受别名；cs需要用ref关键字，将变量在内存的地址传入，传入后的参数成为了别名：

    void ChangeValue(ref int x)
    {
        x = 100; //x是a的别名
    }

    int a = 10;
    ChangeValue(ref a);
    Console.WriteLine(a); // 输出 100
out参数用来输出：  

    void GetValues(out int a, out int b)
    {
        a = 5;
        b = 10;
    }

    int x, y;
    GetValues(out x, out y);
    Console.WriteLine(x); // 输出 5
    Console.WriteLine(y); // 输出 10
23.可空类型（Nullable types）**允许值类型（如 int, double, bool 等）存储 null，这在默认情况下是不允许的；cpp没有这个机制：

    int? x = null;
    本质上为：
    Nullable<int> x = new Nullable<int>();
24.cpp的数组属于值类型，在栈上，是一块连续内存；cs的数组是引用类型，在堆上：

    cpp：
    int arr[5]; // 创建长度为5的int数组，未初始化（内容不确定）
    cs：
    int[] arr = new int[5]; // 创建长度为5的int数组，自动初始化为0
语法不同：

    cpp：
        int arr[5];              // 声明长度为5的int数组
        int arr[] = {1, 2, 3};   // 可以自动推断长度为3
        int* arr = new int[5];   //堆上
    cs：
        int[] arr = new int[5];               // 使用new创建
        int[] arr = new int[] {1, 2, 3};      // 显式初始化
        int[] arr = {1, 2, 3};                // 简写形式
25.cpp结构体类似类，默认public，cs类似c语言，是值类型，默认private，但是可以写入方法和带参数构造函数，不能写析构函数  
26.cpp和cs都可以在子类中访问父类的方法：

    cpp：父类::方法
    cs：base.方法
27.在多态中，cpp的抽象类用纯虚函数实现（只用virtual关键字声明，不写实现方法）；cs用abstract在类前声明；都不能实例化，由子类重写实现具体方法

    抽象函数实现
    cpp：
    virtual void MakeSound() = 0;
    cs：
    public abstract void MakeSound();
28.var相当于cpp中的auto；var编译时确定类型，dynamic运行时随时改变  
29.List<>是动态数组，相当于cpp的vector  

    class Program
    {
        static void Main()
        {
            // 创建一个整数List
            List<int> numbers = new List<int>();

            // 添加元素
            numbers.Add(10);
            numbers.Add(20);
            numbers.Add(30);

            // 访问元素
            Console.WriteLine(numbers[1]);  // 输出 20

            // 遍历
            foreach (int num in numbers)
            {
                Console.WriteLine(num);
            }

            // 删除元素
            numbers.Remove(20);
        }
    }
30.cpp继承可以有访问修饰符；cs没有，统一为public  
31.cpp实例化不用new，cs必须用


