# http命名空间
使用Require引入http.js文件，引入规则请查看require的[官方网站](http://www.requirejs.cn)。

具体命名空间如下：

| 名称 | 参数 | 返回值 | 说明 |
| -- | -- | -- | -- |
| get | url | $.Deferred | get方式获取数据 |
| post  | url,dataJson | $.Deferred | post方式修改数据 |
| put | url,dataJson | $.Deferred | put方式添加新数据 |
| delete | url | $.Deferred | delete方式删除数据 |


