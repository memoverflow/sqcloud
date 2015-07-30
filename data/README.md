# data命名空间
data命名空间的定义是为了将所有的用户逻辑分离，不涉及操作界面DOM的内容。
data命名空间以内容区分分为下面几个命名空间：
1. user
2. users
3. orders
4. products

此命名空间的定义并不能满足所有需求，希望接下来的开发者能够使用此命名空间按照如下模式继续添加
```
info:{
    desc:"获取订单",
    url:"/api/ecorder/",
    action:function(pageIndex,pageSize,params,searchparams){
        var sortBy = params.sortedBy;
        var sortDir = params.sortDir;
        return $http.post(this.url+'?pageIndex=' + pageIndex + "&pageSize=" + pageSize + "&sortBy=" + sortBy + "&sortDir=" + sortDir, searchparams);
    }
}
```


具体命名空间如下（dataJson的结构说明请其他童鞋补充）：

| 名称 | 参数 | 返回值 | 说明 |
| -- | -- | -- | -- |
| user.info.action |  | $.Deferred | 获取当前用户信息 |
| user.validatePwd.action  | dataJson | $.Deferred | 验证密码是否正确 |
| user.changePwd.action | dataJson | $.Deferred | 修改当前用户的密码 |
| users.info.action | pageIndex,pageSize,params | $.Deferred | 获取用户数据 |
| users.status.action | flag,dataJson | $.Deferred | 修改用户状态 启用/禁用 |
| orders.chart.action |  | $.Deferred | 获取订单图表 |
| orders.info.action | pageIndex,pageSize,params,searchparams | $.Deferred | 获取订单的分页展示数据 |
| orders.cancel.action | ids | $.Deferred | 取消订单 |
| products.info.action | pageIndex,pageSize,params | $.Deferred | 获取产品列表的分页数据 |
| products.enabel.action | flag,dataJson | $.Deferred | 开通产品 |
| myproducts.info.action | pageIndex,pageSize,params | $.Deferred | 获取当前用户的数据 |
| myproducts.status.action | flag,dataJson | $.Deferred | 修改产品状态 启用/禁用/同步 |
