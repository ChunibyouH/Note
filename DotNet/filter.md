## [过滤器](https://docs.microsoft.com/zh-cn/aspnet/core/mvc/controllers/filters)

​	ASP.NET Core MVC 中的过滤器允许在执行管道中的特定阶段之前或之后运行代码。可以对全局，也可以对每个控制器或每个操作配置过滤器。

|                     | 实现                                                         | 描述                                                         |
| ------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| AuthorizationFilter | 实现 [IResourceFilter](https://docs.microsoft.com/zh-cn/dotnet/api/microsoft.aspnetcore.mvc.filters.iresourcefilter) 或 [IAsyncResourceFilter](https://docs.microsoft.com/zh-cn/dotnet/api/microsoft.aspnetcore.mvc.filters.iasyncresourcefilter) 接口。 | 是筛选器管道中运行的第一个筛选器。<br />控制对操作方法的访问。<br />具有在它之前的执行的方法，但没有之后执行的方法。 |
| ResourceFilter      | 实现 [IActionFilter](https://docs.microsoft.com/zh-cn/dotnet/api/microsoft.aspnetcore.mvc.filters.iactionfilter) 或 [IAsyncActionFilter](https://docs.microsoft.com/zh-cn/dotnet/api/microsoft.aspnetcore.mvc.filters.iasyncactionfilter) 接口。 | 资源筛选器<br />缓存命中，则缓存筛选器可以绕开管道的其余阶段。 |
| ExceptionFilter     | 实现 [IExceptionFilter](https://docs.microsoft.com/zh-cn/dotnet/api/microsoft.aspnetcore.mvc.filters.iexceptionfilter) 或 [IAsyncExceptionFilter](https://docs.microsoft.com/zh-cn/dotnet/api/microsoft.aspnetcore.mvc.filters.iasyncexceptionfilter)接口。 | 捕获未捕获的异常                                             |
| ActionFilter        | 实现 IActionFilter 或 IAsyncActionFilter 接口。              | 作用于Action                                                 |
| ResultFilter        | 实现[IResultFilter](https://docs.microsoft.com/zh-cn/dotnet/api/microsoft.aspnetcore.mvc.filters.iresultfilter) 或 [IAsyncResultFilter](https://docs.microsoft.com/zh-cn/dotnet/api/microsoft.aspnetcore.mvc.filters.iasyncresultfilter)接口。 | 作用于Action结果                                             |

### 作用域

- 标记Action，只对Action生效

- 标记Controller，对Controller下所有Action生效

- 全局注册，对所有Action生效

  ```c#
  //ConfigureServices中
  services.AddMvc(op =>
  {
      op.Filters.Add<TestResultFilter>();
  });
  //or
  services.AddControllersWithViews(op =>
  {
      op.Filters.Add<TestResultFilter>();
      //op.Filters.Add(new TestResultFilter());//通过实例则该实例应用于每一个请求
  });
  ```

### 执行顺序

​	由端点中间件调用

请求通过

- 授权过滤器
- 资源过滤器
- 模型绑定
- 操作过滤器
- 操作执行和操作结果转换
- 异常过滤器
- 结果过滤器和结果执行进行处理 

返回时，请求仅由结果过滤器和资源过滤器进行处理，变成发送到客户端的响应。

![请求通过授权过滤器、资源过滤器、模型绑定、操作过滤器、操作执行和操作结果转换、异常过滤器、结果过滤器和结果执行进行处理。 返回时，请求仅由结果过滤器和资源过滤器进行处理，变成发送到客户端的响应。](https://docs.microsoft.com/zh-cn/aspnet/core/mvc/controllers/filters/_static/filter-pipeline-2.png?view=aspnetcore-5.0)

![ASP.NET Core 筛选器管道](https://docs.microsoft.com/zh-cn/aspnet/core/fundamentals/middleware/index/_static/mvc-endpoint.svg?view=aspnetcore-5.0)

### 取消和设置短路

​	设置过滤器上下文参数中的Result属性，可在任一过滤其中短路管道

```c#
public class TestActionFilter : Attribute, IActionFilter
{
    public void OnActionExecuted(ActionExecutedContext context)
    {
        Console.WriteLine("Action 后");
    }

    public void OnActionExecuting(ActionExecutingContext context)
    {
        context.Result = new ContentResult() { Content = "短路" };
        Console.WriteLine("Action 前");
    }
}
```

### 依赖项注入

- 将为每个请求创建一个实例。
- [依赖关系注入](https://docs.microsoft.com/zh-cn/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-5.0) (DI) 将填充所有构造函数依赖项。

#### ServiceFilterAttribute

```c#
//filter构造函数添加注入项
public class TestActionFilter : Attribute, IActionFilter
{
    private ILogger _logger;
    public TestActionFilter(ILoggerFactory loggerFactory)
    {
        _logger = loggerFactory.CreateLogger<AddHeaderResultServiceFilter>();
    }
    ...
}
//将filter添加到DI容器中
services.AddTransient<TestActionFilter>();
//使用全局注册or添加Controller、Action上
[ServiceFilter(typeof(TestActionFilter))]
```

#### TypeFilterAttribute

​	TypeFilter所需参数使用[Microsoft.Extensions.DependencyInjection.ObjectFactory](https://docs.microsoft.com/zh-cn/dotnet/api/microsoft.extensions.dependencyinjection.objectfactory) 进行实例化，不会通过DI解析，所以不需要注册在 DI 容器中。

```c#
//添加Controller、Action上
[TypeFilter(typeof(TestActionFilter))]
```

