# Entity Framework Core

1. 将linq语言翻译为sql
2. 执行查询
3. 根据查询结果创建.net对象
4. 设置对象与对象之间的关系连接
5. 生成跟踪快照

## IEnumerable

- AsEnumerable()先查数据库再过滤,

## IQueryable

- AsQueryable()将条件生成sql，一起在数据库中过滤。

## AsNoTracking

- 当确定查询出来的数据**不会改变**的时候使用AsNoTracking();

- 使用context.Entry<User>(user).State 查看对象监听状态。

## 立即执行

​	ToList()、Count() 、FirstOrDefault()、迭代器IEnumerable/foreach

