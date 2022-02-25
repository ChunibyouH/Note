## 执行顺序

```c#
class Program
{
    static void Main(string[] args)
    {
        Console.WriteLine("Hello World!");
        Task.Run(() => { var b = new B(); }).Wait();
        GC.Collect();//强制对所有代进行即时垃圾回收。
        Task.Run(() => Thread.Sleep(1 * 1000)).Wait();
    }
}

class A
{
    private C ca = new C("A");
    static A()
    {
        Console.WriteLine("A静态构造函数初始化！");
    }
    public A()
    {
        Console.WriteLine("A构造函数初始化！");
    }
    ~A()
    {
        Console.WriteLine("A析构");
    }
}
class B : A
{
    private C cb = new C("B");
    static B()
    {
        Console.WriteLine("B静态构造函数初始化！");
    }
    public B()
    {
        Console.WriteLine("B构造函数初始化!");
    }
    ~B()
    {
        Console.WriteLine("B析构");
    }
}

public class C
{
    public C(string str)
    {
        Console.WriteLine($"{str}调用C构造");
    }
}
//Hello World!
//B静态构造函数初始化！
//B调用C构造
//A静态构造函数初始化！
//A调用C构造
//A构造函数初始化！
//B构造函数初始化!
//B析构
//A析构
```

