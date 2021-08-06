# [中间件](https://docs.microsoft.com/zh-cn/aspnet/core/fundamentals/middleware/?view=aspnetcore-5.0)

​		请求处理模式显示请求到达、通过三个中间件进行处理以及响应离开应用。 每个中间件运行其逻辑，并在 next() 语句处将请求传递到下一个中间件。 在第三个中间件处理请求之后，请求按相反顺序返回通过前两个中间件，以进行离开应用前并在其 next() 语句后的其他处理，作为对客户端的响应
​		用 [Use](https://docs.microsoft.com/zh-cn/dotnet/api/microsoft.aspnetcore.builder.useextensions.use) 将多个请求委托链接在一起。 `next` 参数表示管道中的下一个委托。 可通过不调用 next 使管道短路。

![请求处理模式显示请求到达、通过三个中间件进行处理以及响应离开应用。 每个中间件运行其逻辑，并在 next() 语句处将请求传递到下一个中间件。 在第三个中间件处理请求之后，请求按相反顺序返回通过前两个中间件，以进行离开应用前并在其 next() 语句后的其他处理，作为对客户端的响应。](https://docs.microsoft.com/zh-cn/aspnet/core/fundamentals/middleware/index/_static/request-delegate-pipeline.png?view=aspnetcore-5.0)

## 顺序

​	可自定义如何重新排列现有中间件，并非所有中间件都能自定义排列，中间件顺序参考 [内置中间件](https://docs.microsoft.com/zh-cn/aspnet/core/fundamentals/middleware/?view=aspnetcore-5.0#built-in-middleware)

![ASP.NET Core 中间件管道](https://docs.microsoft.com/zh-cn/aspnet/core/fundamentals/middleware/index/_static/middleware-pipeline.svg?view=aspnetcore-5.0)

## 对中间件管道进行分支

### [Map](https://docs.microsoft.com/zh-cn/dotnet/api/microsoft.aspnetcore.builder.mapextensions.map)

​		根据请求路由的匹配创建管道分支。

```c#
public class Startup
{
    private static void HandleMapTest1(IApplicationBuilder app)
    {
        app.Run(async context =>
        {
            await context.Response.WriteAsync("Map Test 1");
        });
    }

    private static void HandleMapTest2(IApplicationBuilder app)
    {
        app.Run(async context =>
        {
            await context.Response.WriteAsync("Map Test 2");
        });
    }

    public void Configure(IApplicationBuilder app)
    {
        app.Map("/map1", HandleMapTest1);

        app.Map("/map2", HandleMapTest2);

        app.Run(async context =>
        {
            await context.Response.WriteAsync("Hello from non-Map delegate. <p>");
        });
    }
}
```

### [MapWhen](https://docs.microsoft.com/zh-cn/dotnet/api/microsoft.aspnetcore.builder.mapwhenextensions.mapwhen)

​		给定条件确定是否应执行分支操作

```c#
app.MapWhen(context => context.Request.Query.ContainsKey("branch"),HandleBranch);
```

### [UseWhen](https://docs.microsoft.com/zh-cn/dotnet/api/microsoft.aspnetcore.builder.usewhenextensions.usewhen) 

​		有条件地在请求管道中创建分支，分支没有发生短路或包含终端中间件则将其重新加入到主管道。

```c#
app.UseWhen(context => context.Request.Query.ContainsKey("branch"),appBuilder => HandleBranchAndRejoin(appBuilder, logger));
```

