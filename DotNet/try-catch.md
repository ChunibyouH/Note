# try catch

```c#
try//使用try时catch、finally至少配合一个使用
{
    //不出异常正常执行
    //出异常则跳到catch
}
catch (Exception e)
{
    //捕获try中的异常
}
finally
{
    //在try或catch中的代码执行完成后执行。
}
```



## 多个catch块

```c#
try
{
    string str = null;
    if (str == null)
    {
        throw new ArgumentNullException("hello");
    }
}
catch (ArgumentNullException e)//捕获指定类型异常
{
    Console.WriteLine("{0} First exception caught.", e);
}
catch (Exception e)//Exception只能出现在最后，兜底捕获所有异常
{
    Console.WriteLine("{0} Second exception caught.", e);
}
```



## when

异常筛选器更简洁

```c#
try
{
    throw new Exception("123");//a:123
}
catch (System.Exception e) when (e.Message == "123")
{
    System.Console.WriteLine($"a:{e.Message}");
}
catch (System.Exception e)
{
    System.Console.WriteLine($"b:{e.Message}");
}
```

