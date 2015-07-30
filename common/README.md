# common命名空间
common命名空间是为了满足列表模板而定义的，使用者可以自定义修改common命名空间内容。

下面为属性说明：

| 名称 | 类型 | 说明 |
| -- | -- | -- |
| staticPageSize | 属性 | 页面显示数据量 |
| pageSize | 属性 | 页面显示数据量（请修改时确保上面和下面两个属性的值一致） |
| currentIndex | 属性 | 当前页面索引，从1开始，请勿修改此值，因为目前获取数据的方式是通过索引获取数据的所有值即：pageIndex*pageSize为每页的pageSize |
| sizeIndex | 属性 | 当前页面索引，从1开始 |
| pageCount | 属性 | 一共有多少页 |
| promise | 属性 | 字符串类型，表示获取当前数据的方法，返回$.Deferred类型的值，但是需要传递字符串类型，为了确保参数的正确性 |
| searchparams | 属性 | 搜索时传递参数，目前只针对订单搜索 |
| params | 属性 | 获取数据时传递的参数，包含如排序方式开始时间等等 |
| compile | 方法 | 编译数据通过Handlebars模板化数据 |
| showMessage | 方法 | 显示提示数据 |
| helper | 方法 | 注册自定义的Handlebars 的helper |
| showMessage | 方法 | 显示提示数据 |
| get | 方法 | 服务端拉取需要显示的分页数据 |
| closeModal | 方法 | 关闭显示的弹出框 |
| page | 方法 | 定义通过拖拽的方式获取数据的基本方法 |

调用方式：具体请参考目前使用的界面（users.html、orders.html、producst.html）

```
common.helper(function(){
        //注册用户状态
        Handlebars.registerHelper('status', function(status) {
            var result = '';
            switch (status)
            {
                case 0:
                    result = "创建";
                    break;
                case 1:
                    result = "启用";
                    break;
                case 2:
                    result = "禁用";
                    break;
                case 4:
                    result = "编辑";
                    break;
                case 5:
                    result = "重置密码";
                    break;
                default:
                    result = "其他";
                    break;
            }
            return new Handlebars.SafeString(result);
        });
        //注册用户性别
        Handlebars.registerHelper('gender', function(gender) {
            var result = '';
            switch (gender)
            {
                case "M":
                    result = "男";
                    break;
                case "F":
                    result = "女";
                    break;
            }
            return new Handlebars.SafeString(result);
        });
        //注册用户同步状态
        Handlebars.registerHelper('sync', function(sync) {
            var result = '';
            switch (sync)
            {
                case 0:
                    result = "待同步";
                    break;
                case 1:
                    result = "同步成功";
                    break;
                case 2:
                    result = "同步失败";
                    break;
            }
            return new Handlebars.SafeString(result);
        });
    },function(){
        common.params.Name = $(".am-modal-prompt-input").val();
    });
    common.promise = "data.users.info.action(common.currentIndex,common.pageSize,common.params)";
    common.array = [
        {
            flag:data.users.status.flagEnabel,
            id:"UserID",
            callback:function(flag,userId){
                return data.users.status.action(flag,[userId]);
            },
            msg:"启用用户"
        },
        {
            flag:data.users.status.flagForbidden,
            id:"UserID",
            callback:function(flag,userId){
                return data.users.status.action(flag,[userId]);
            },
            msg:"禁用用户"
        },
        {
            flag:data.users.status.flagForSync,
            id:"UserID",
            callback:function(flag,userId){
                return data.users.status.action(flag,[userId]);
            },
            msg:"同步用户"
        }
    ];
    common.get(null);
    common.page();
```



