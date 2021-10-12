# 电商管理后台 API 接口文档

[TOC]

## 1.1. API V1 接口说明

- 接口基准地址：`http://127.0.0.1:8081/api/`
- 服务端已开启 CORS 跨域支持
- API 认证统一使用 Token 认证
- 需要授权的 API ，必须在请求头中使用 `token` 字段提供 `token` 令牌
- 使用 HTTP Status Code 标识状态
- 数据返回格式统一使用 JSON

### 1.1.1. 支持的请求方法

- GET（SELECT）：从服务器取出资源（一项或多项）。
- POST（CREATE）：在服务器新建一个资源。

### 1.1.2. 通用返回状态说明

| *状态码* | *含义*                               | *说明* |
| -------- | ------------------------------------ | ------ |
| 101      | 无token，请登录后操作！              |        |
| 102      | 用户不存在，请重新登录！             |        |
| 200      | 请求成功                             |        |
| 201      | 创建成功                             |        |
| 202      | 创建失败                             |        |
| 203      | 修改成功                             |        |
| 204      | 修改失败                             |        |
| 205      | 删除成功                             |        |
| 206      | 删除失败                             |        |
| 207      | 查询成功                             |        |
| 208      | 查询失败                             |        |
| 400      | 请求的地址不存在或者包含不支持的参数 |        |
| 401      | 未授权                               |        |
| 403      | 被禁止访问                           |        |
| 404      | 请求的资源不存在                     |        |
| 500      | 内部错误                             |        |
|          |                                      |        |

------

## 1.2. 登录

### 1.2.1. 登录验证接口

- 请求路径：mg_login
- 请求方法：post
- 请求参数

| 参数名 | 参数说明 | 备注     |
| ------ | -------- | -------- |
| mgName | 用户名   | 不能为空 |
| mgPwd  | 密码     | 不能为空 |

- 响应参数

| 参数名   | 参数说明    | 备注            |
| -------- | ----------- | --------------- |
| mgId     | 用户 ID     |                 |
| roleId   | 用户角色 ID |                 |
| mgName   | 用户名      |                 |
| mgMobile | 手机号      |                 |
| mgEmail  | 邮箱        |                 |
| token    | 令牌        | 基于 jwt 的令牌 |

- 响应数据

```json
{
  "data": {
    "total": 6,
    "list": [
      {
        "mgId": 500,
        "mgName": "admin",
        "mgPwd": "$2y$10$sZlpZNoLAnoD1DtYO9REAODCPkpMb5bwl4oMzrMvJa83k9BY3KRwq",
        "mgTime": 1486720211,
        "roleId": 0,
        "mgMobile": "18088083365",
        "mgEmail": "adsfad@qq.com",
        "mgState": 1
      }
    ],
    "pageNum": 1,
    "pageSize": 1
  },
  "meta": {
    "msg": "请求成功！",
    "status": 200
  }
}
```

## 1.3. 用户管理

### 1.3.1. 用户数据列表

- 请求路径：/manager/getByParam
- 请求方法：post
- 请求参数

| 参数名   | 参数说明     | 备注     |
| -------- | ------------ | -------- |
| mgName   | 查询参数     | 可以为空 |
| pageNum  | 当前页码     | 不能为空 |
| pageSize | 每页显示条数 | 不能为空 |

- 响应参数

| 参数名  | 参数说明     | 备注 |
| ------- | ------------ | ---- |
| total   | 总记录数     |      |
| pageNum | 当前页码     |      |
| list    | 用户数据集合 |      |

- 响应数据

```json
{
  "data": {
    "total": 1,
    "list": [
      {
        "mgId": 511,
        "mgName": "test",
        "mgPwd": "test",
        "mgTime": 1,
        "roleId": 0,
        "mgMobile": "1",
        "mgEmail": "1",
        "mgState": 1
      }
    ],
    "pageNum": 1,
    "pageSize": 1,
    "size": 1
  },
  "meta": {
    "msg": "请求成功！",
    "status": 200
  }
}
```

### 1.3.2. 添加用户

- 请求路径：manager/add
- 请求方法：post
- 请求参数

| 参数名   | 参数说明 | 备注     |
| -------- | -------- | -------- |
| mgName   | 用户名称 | 不能为空 |
| mgPwd    | 用户密码 | 不能为空 |
| mgEmail  | 邮箱     | 可以为空 |
| mgMobile | 手机号   | 可以为空 |

- 响应参数

| 参数名   | 参数说明    | 备注 |
| -------- | ----------- | ---- |
| mgId     | 用户 ID     |      |
| roleId   | 用户角色 ID |      |
| mgName   | 用户名      |      |
| mgMobile | 手机号      |      |
| mgEmail  | 邮箱        |      |

- 响应数据

```json
{
  "data": {
    "mgId": 512,
    "mgName": "asd",
    "mgPwd": "123456",
    "mgTime": "2020-02-18 14:43:28",
    "roleId": null,
    "mgMobile": "18088083365",
    "mgEmail": "1757895437@qq.com",
    "mgState": null
  },
  "meta": {
    "msg": "请求成功！",
    "status": 200
  }
}
```

### 1.3.3. 修改用户状态

- 请求路径：manager/state
- 请求方法：put
- 请求参数

| 参数名  | 参数说明   | 备注                                        |
| ------- | ---------- | ------------------------------------------- |
| mgId    | 管理员ID   | 不能为空`携带在url中`                       |
| mgState | 管理员状态 | 不能为空`携带在url中`，'1’为启用，‘0’为停用 |

- 响应数据

```json
{
  "data": {
    "mgId": "511",
    "mgName": "test",
    "mgPwd": "test",
    "mgTime": "1",
    "roleId": 0,
    "mgMobile": "1",
    "mgEmail": "1",
    "mgState": 0
  },
  "meta": {
    "msg": "修改成功",
    "status": 203
  }
}
```

### 1.3.4. 根据 ID 查询用户信息

- 请求路径：manager/getById
- 请求方法：get
- 请求参数

| 参数名 | 参数说明  | 备注                  |
| ------ | --------- | --------------------- |
| mgId   | 管理员 ID | 不能为空`携带在url中` |

- 响应参数

| 参数名   | 参数说明 | 备注 |
| -------- | -------- | ---- |
| mgId     | 用户 ID  |      |
| roleId   | 角色 ID  |      |
| mgMobile | 手机号   |      |
| mgEmail  | 邮箱     |      |

- 响应数据

```json
{
  "data": {
    "mgId": "511",
    "mgName": "test",
    "mgPwd": "test",
    "mgTime": "1",
    "roleId": 0,
    "mgMobile": "1",
    "mgEmail": "1",
    "mgState": 0
  },
  "meta": {
    "msg": "查询成功",
    "status": 207
  }
}
```

### 1.3.5. 编辑用户提交

- 请求路径：manager/updById
- 请求方法：put
- 请求参数

| 参数名   | 参数说明  | 备注                        |
| -------- | --------- | --------------------------- |
| mgId     | 管理员 id | 不能为空 `参数是url参数:id` |
| mgEmail  | 邮箱      | 可以为空                    |
| mgMobile | 手机号    | 可以为空                    |

- 响应参数

| 参数名   | 参数说明 | 备注 |
| -------- | -------- | ---- |
| mgId     | 用户 ID  |      |
| roleId   | 角色 ID  |      |
| mgMobile | 手机号   |      |
| mgEmail  | 邮箱     |      |

- 响应数据

```json
/* 200表示成功，500表示失败 */
{
  "data": {
    "mgId": "511",
    "mgName": "test",
    "mgPwd": "test",
    "mgTime": "1",
    "roleId": 0,
    "mgMobile": "12312312312",
    "mgEmail": "123@123.com",
    "mgState": 0
  },
  "meta": {
    "msg": "修改成功",
    "status": 203
  }
}
```

### 1.3.6. 删除单个用户

- 请求路径：manager/delById
- 请求方法：delete
- 请求参数

| 参数名 | 参数说明 | 备注                       |
| ------ | -------- | -------------------------- |
| mgId   | 管理员id | 不能为空`参数是url参数:id` |

- 响应参数
- 响应数据

```json
{
  "data": null,
  "meta": {
    "msg": "删除成功",
    "status": 205
  }
}
```

### 1.3.7. 分配用户角色

- 请求路径：manager/updRole
- 请求方法：put
- 请求参数

| 参数名 | 参数说明  | 备注                       |
| ------ | --------- | -------------------------- |
| mgId   | 管理员 ID | 不能为空`参数是url参数:id` |
| roleId | 角色 id   | 不能为空`参数body参数`     |

- 响应参数

| 参数名   | 参数说明  | 备注 |
| -------- | --------- | ---- |
| mgId     | 管理员 ID |      |
| roleId   | 角色 id   |      |
| mgMobile | 手机号    |      |
| mgEmail  | 邮箱      |      |

- 响应数据

```json
{
  "data": {
    "mgId": "c4bc207e-828a-46b4-936b-0674cb1a0f2d",
    "mgName": "manager",
    "mgPwd": "manager",
    "mgTime": "2020-02-18 16:16:32",
    "roleId": "31",
    "mgMobile": "11111111111",
    "mgEmail": "111@111.com",
    "mgState": 1
  },
  "meta": {
    "msg": "修改成功",
    "status": 203
  }
}
```

## 1.4. 权限管理

### 1.4.1. 所有权限列表

- 请求路径：/rights
- 请求方法：get
- 请求参数

| 参数名 | 参数说明 | 备注                                                         |
| ------ | -------- | ------------------------------------------------------------ |
| type   | 类型     | 值 list 或 tree , list 列表显示权限, tree 树状显示权限,`参数是url参数:type` |

- 响应参数

| 参数名  | 参数说明     | 备注 |
| ------- | ------------ | ---- |
| psId    | 权限 ID      |      |
| psName  | 权限说明     |      |
| psLevel | 权限层级     |      |
| psPid   | 权限父 ID    |      |
| path    | 对应访问路径 |      |

- 响应数据 type=list

```json
  {
  "data": [
    {
      "psId": "101",
      "psName": "商品管理",
      "psPid": "0",
      "psC": "",
      "psA": "",
      "psLevel": "0",
      "path": "goods",
      "children": null
    },
    {
      "psId": "102",
      "psName": "订单管理",
      "psPid": "0",
      "psC": "",
      "psA": "order",
      "psLevel": "0",
      "path": "orders",
      "children": null
    }
  ],
  "meta": {
    "msg": "查询成功",
    "status": 207
  }
}
```

type=tree

```json
 {
  "data": [
    {
      "psId": "101",
      "psName": "商品管理",
      "psPid": "0",
      "psC": "",
      "psA": "",
      "psLevel": "0",
      "children": [
        {
          "psId": "104",
          "psName": "商品列表",
          "psPid": "101",
          "psC": "Goods",
          "psA": "index",
          "psLevel": "1",
          "children": [
            {
              "psId": "105",
              "psName": "添加商品",
              "psPid": "104",
              "psC": "Goods",
              "psA": "tianjia",
              "psLevel": "2",
              "children": []
            }
          ]
        }
      ]
    }
  ],
  "meta": {
    "msg": "查询成功",
    "status": 207
  }
}
```

### 1.4.2. 左侧菜单权限

- 请求路径：menus
- 请求方法：get
- 响应数据

```json
{
  "data": [
    {
      "psId": "101",
      "psName": "商品管理",
      "psPid": "0",
      "psC": "",
      "psA": "",
      "psLevel": "0",
      "path": "goods",
      "children": [
        {
          "psId": "104",
          "psName": "商品列表",
          "psPid": "101",
          "psC": "Goods",
          "psA": "index",
          "psLevel": "1",
          "path": "goods",
          "children": null
        }
      ]
    }
  ],
  "meta": {
    "msg": "查询成功",
    "status": 207
  }
}
```

## 1.5. 角色管理

### 1.5.1. 角色列表

- 请求路径：roles/getRoleList

- 请求方法：get

- 响应数据说明

  - 第一层为角色信息

  - 第二层开始为权限说明，权限一共有 3 层权限
  - 最后一层权限，不包含 `children` 属性

- 响应数据

```json
{
    "data": [
        {
            "id": 30,
            "roleName": "主管",
            "roleDesc": "技术负责人",
            "children": [
                {
                    "id": 101,
                    "authName": "商品管理",
                    "path": null,
                    "children": [
                        {
                            "id": 104,
                            "authName": "商品列表",
                            "path": null,
                            "children": [
                                {
                                    "id": 105,
                                    "authName": "添加商品",
                                    "path": null
                                }
                            ]
                        }
                    ]
                }
            ]
        }
    ],
    "meta": {
        "msg": "获取成功",
        "status": 200
    }
}
```

### 1.5.2. 添加角色

- 请求路径：roles/addRole
- 请求方法：post
- 请求参数

| 参数名   | 参数说明 | 备注     |
| -------- | -------- | -------- |
| roleName | 角色名称 | 不能为空 |
| roleDesc | 角色描述 | 可以为空 |

- 响应参数

| 参数名   | 参数说明 | 备注 |
| -------- | -------- | ---- |
| roleId   | 角色 ID  |      |
| roleName | 角色名称 |      |
| roleDesc | 角色描述 |      |

- 响应数据

```json
{
    "data": {
        "roleId": 40,
        "roleName": "admin2",
        "roleDesc": "admin2Desc"
    },
    "meta": {
        "msg": "创建成功",
        "status": 201
    }
}
```

### 1.5.3. 根据 ID 查询角色

- 请求路径：roles/getById
- 请求方法：get
- 请求参数

| 参数名 | 参数说明 | 备注                  |
| ------ | -------- | --------------------- |
| roleId | 角色 ID  | 不能为空`携带在url中` |

- 响应参数

| 参数名   | 参数说明 | 备注 |
| -------- | -------- | ---- |
| roleId   | 角色 ID  |      |
| roleName | 角色名称 |      |
| roleDesc | 角色描述 |      |

- 响应数据

```json
{
  "data": {
    "roleId": "30",
    "roleName": "主管",
    "psIds": "101,0,104,116,115,142,143,121,122,123,149,102,107,109,103,111,129,130,134,135,138,140,141,112,147,125,110,131,132,133,136,137,145,146,148",
    "psCa": "Goods-index,Goods-tianjia,Category-index,Order-showlist,Brand-index",
    "roleDesc": "技术负责人"
  },
  "meta": {
    "msg": "查询成功",
    "status": 207
  }
}
```

### 1.5.4. 编辑提交角色

- 请求路径：roles/update
- 请求方法：post
- 请求参数

| 参数名   | 参数说明 | 备注                  |
| -------- | -------- | --------------------- |
| roleId   | 角色 ID  | 不能为空`携带在url中` |
| roleName | 角色名称 | 不能为空              |
| roleDesc | 角色描述 | 可以为空              |

- 响应数据

```json
{
  "data": {
    "roleId": "30",
    "roleName": "测试aa",
    "psIds": "101,0,104,116,115,142,143,121,122,123,149,102,107,109,103,111,129,130,134,135,138,140,141,112,147,125,110,131,132,133,136,137,145,146,148",
    "psCa": "Goods-index,Goods-tianjia,Category-index,Order-showlist,Brand-index",
    "roleDesc": "测试"
  },
  "meta": {
    "msg": "修改成功",
    "status": 203
  }
}
```

### 1.5.5. 删除角色

- 请求路径：roles/del
- 请求方法：get
- 请求参数

| 参数名 | 参数说明 | 备注                  |
| ------ | -------- | --------------------- |
| roleId | 角色 ID  | 不能为空`携带在url中` |

- 响应数据

```json
{
  "data": null,
  "meta": {
    "msg": "删除成功",
    "status": 205
  }
}
```

### 1.5.6. 角色授权

- 请求路径：roles/setRights
- 请求方法：post
- 请求参数：通过 `请求体` 发送给后端

| 参数名 | 参数说明               | 备注                                                         |
| ------ | ---------------------- | ------------------------------------------------------------ |
| roleId | 角色 ID                | 不能为空`携带在url中`                                        |
| psIds  | 权限 ID 列表（字符串） | 以 `,` 分割的权限 ID 列表（获取所有被选中、叶子节点的key和半选中节点的key, 包括 1，2，3级节点） |

- 响应数据

```json
{
  "data": {
    "roleId": "41",
    "roleName": "dsdf",
    "psIds": "105,142,101,104,115",
    "psCa": null,
    "roleDesc": "sf "
  },
  "meta": {
    "msg": "修改成功",
    "status": 203
  }
}
```

### 1.5.7. 删除角色指定权限

- 请求路径：/roles/delRights

- 请求方法：get

- 请求参数

  | 参数名  | 参数说明 | 备注                  |
  | ------- | -------- | --------------------- |
  | roleId  | 角色 ID  | 不能为空`携带在url中` |
  | rightId | 权限 ID  | 不能为空`携带在url中` |

- 响应数据说明

  - 返回的data, 是当前角色下最新的权限数据

- 响应数据

```json
{
  "data": [
    {
      "psId": "101",
      "psName": "商品管理",
      "psPid": "0",
      "psC": "",
      "psA": "",
      "psLevel": "0",
      "path": null,
      "children": [
        {
          "psId": "115",
          "psName": "分类参数",
          "psPid": "101",
          "psC": "Type",
          "psA": "index",
          "psLevel": "1",
          "path": null,
          "children": [
            {
              "psId": "142",
              "psName": "获取参数列表",
              "psPid": "115",
              "psC": "",
              "psA": "",
              "psLevel": "2",
              "path": null,
              "children": []
            }
          ]
        }
      ]
    }
  ],
  "meta": {
    "msg": "删除成功",
    "status": 205
  }
}
```

## 1.6. 商品分类管理

### 1.6.1. 商品分类数据列表

- 请求路径：/cate/getByParam
- 请求方法：post
- 请求参数

| 参数名   | 参数说明           | 备注                                                         |
| -------- | ------------------ | ------------------------------------------------------------ |
| type     | 0/1/2              | 值：0，1，2 分别表示显示一层二层三层分类列表 【可选参数】如果不传递，则默认获取所有级别的分类 |
| pageNum  | 当前页码值         | 【可选参数】如果不传递，则默认获取所有分类                   |
| pageSize | 每页显示多少条数据 | 【可选参数】如果不传递，则默认获取所有分类                   |

- 响应参数

| 参数名   | 参数说明     | 备注 |
| -------- | ------------ | ---- |
| catId    | 分类 ID      |      |
| catName  | 分类名称     |      |
| catPid   | 分类父 ID    |      |
| catLevel | 分类当前层级 |      |

- 响应数据

```json
{
    "data": [
        {
            "cat_id": 1,
            "cat_name": "大家电",
            "cat_pid": 0,
            "cat_level": 0,
            "cat_deleted": false,
            "children": [
                {
                    "cat_id": 3,
                    "cat_name": "电视",
                    "cat_pid": 1,
                    "cat_level": 1,
                    "cat_deleted": false,
                    "children": [
                        {
                            "cat_id": 6,
                            "cat_name": "曲面电视",
                            "cat_pid": 3,
                            "cat_level": 2,
                            "cat_deleted": false
                        },
                        {
                            "cat_id": 7,
                            "cat_name": "海信",
                            "cat_pid": 3,
                            "cat_level": 2,
                            "cat_deleted": false
                        }
                    ]
                }
            ]
        }
    ],
    "meta": {
        "msg": "获取成功",
        "status": 200
    }
}
```

### 1.6.2. 添加分类

- 请求路径：/cate/addCate
- 请求方法：post
- 请求参数

| 参数名    | 参数说明  | 备注                                                        |
| --------- | --------- | ----------------------------------------------------------- |
| cat_pid   | 分类父 ID | 不能为空，如果要添加1级分类，则父分类Id应该设置为 `0`       |
| cat_name  | 分类名称  | 不能为空                                                    |
| cat_level | 分类层级  | 不能为空，`0`表示一级分类；`1`表示二级分类；`2`表示三级分类 |

- 响应数据

```json
{
  "data": {
    "catId": "8ca42342-baf4-4cfe-9beb-247d3767db45",
    "catName": "aa",
    "catPid": "1",
    "catLevel": 2,
    "catDeleted": 0,
    "catIcon": null,
    "catSrc": null
  },
  "meta": {
    "msg": "请求成功",
    "status": 201
  }
}
```

### 1.6.3. 根据 id 查询分类

- 请求路径：/cate/getById
- 请求方法：get
- 请求参数

| 参数名 | 参数说明 | 备注                  |
| ------ | -------- | --------------------- |
| catId  | 分类 ID  | 不能为空`携带在url中` |

- 响应数据

```
{
  "data": {
    "catId": "3",
    "catName": "电视",
    "catPid": "1",
    "catLevel": 1,
    "catDeleted": 0,
    "catIcon": "",
    "catSrc": ""
  },
  "meta": {
    "msg": "查询成功",
    "status": 207
  }
}
```

### 1.6.4. 编辑提交分类

- 请求路径：/cate/updCate
- 请求方法：post
- 请求参数

| 参数名  | 参数说明 | 备注     |
| ------- | -------- | -------- |
| catId   | 分类 ID  | 不能为空 |
| catName | 分类名称 | 不能为空 |

- 响应数据

```
{
  "data": {
    "catId": "8ca42342-baf4-4cfe-9beb-247d3767db45",
    "catName": "测试",
    "catPid": "1",
    "catLevel": 2,
    "catDeleted": 0,
    "catIcon": null,
    "catSrc": null
  },
  "meta": {
    "msg": "修改成功",
    "status": 203
  }
}
```

### 1.6.5. 删除分类

- 请求路径：/cate/delCate
- 请求方法：get
- 请求参数

| 参数名 | 参数说明 | 备注                  |
| ------ | -------- | --------------------- |
| catId  | 分类 ID  | 不能为空`携带在url中` |

- 响应数据

```
{
  "data": null,
  "meta": {
    "msg": "删除成功",
    "status": 205
  }
}
```

## 1.7. 分类参数管理

### 1.7.1. 参数列表

- 请求路径：/attr/getAttrList
- 请求方法：post
- 请求参数

| 参数名  | 参数说明    | 备注                                                      |
| ------- | ----------- | --------------------------------------------------------- |
| catId   | 分类 ID     | 不能为空                                                  |
| attrSel | [only,many] | 不能为空,通过 only 或 many 来获取分类静态参数还是动态参数 |

- 响应参数

| 参数名    | 参数说明                                       | 备注 |
| --------- | ---------------------------------------------- | ---- |
| attrId    | 分类参数 ID                                    |      |
| attrName  | 分类参数名称                                   |      |
| catId     | 分类参数所属分类                               |      |
| attrSel   | only:输入框(唯一) many:后台下拉列表/前台单选框 |      |
| attrWrite | manual:手工录入 list:从列表选择                |      |
| attrVals  | 如果 attr_write:list,那么有值，该值以逗号分隔  |      |

- 响应数据

```
{
  "data": {
    "total": 3802,
    "list": [
      {
        "attrId": "1",
        "attrName": "主观参数-型号",
        "catId": "1191",
        "attrSel": "only",
        "attrWrite": "manual",
        "deleteTime": null,
        "attrVals": "00002"
      }
	}
  "meta": {
    "msg": "查询成功",
    "status": 207
  }
}
```

### 1.7.2. 添加动态参数或者静态属性

- 请求路径：/attr/addAttr
- 请求方法：post
- 请求参数

| 参数名   | 参数说明                                   | 备注         |
| -------- | ------------------------------------------ | ------------ |
| catId    | 分类 ID                                    | 不能为空     |
| attrName | 参数名称                                   | 不能为空     |
| attrSel  | [only,many]                                | 不能为空     |
| attrVals | 如果是 many 就需要填写值的选项，以逗号分隔 | 【可选参数】 |

- 响应数据

```
{
  "data": {
    "attrId": "f4f44add-33f6-43ec-9929-226b91f8e4cb",
    "attrName": "主观参数-型号",
    "catId": "1191",
    "attrSel": "only",
    "attrWrite": "manual",
    "deleteTime": null,
    "attrVals": "00002"
  },
  "meta": {
    "msg": "创建成功",
    "status": 201
  }
}
```

### 1.7.3. 删除参数

- 请求路径： /attr/delAttr
- 请求方法：get
- 请求参数

| 参数名 | 参数说明 | 备注                  |
| ------ | -------- | --------------------- |
| catId  | 分类 ID  | 不能为空`携带在url中` |
| attrId | 参数 ID  | 不能为空`携带在url中` |

- 响应数据

```
{
    "data": null,
    "meta": {
        "msg": "删除成功",
        "status": 205
    }
}
```

### 1.7.4. 根据 ID 查询参数

- 请求路径：/attr/findById
- 请求方法：post
- 请求参数

| 参数名    | 参数说明                                   | 备注     |
| --------- | ------------------------------------------ | -------- |
| catId     | 分类 ID                                    | 不能为空 |
| attrId    | 属性 ID                                    | 不能为空 |
| attr_sel  | [only,many]                                | 不能为空 |
| attr_vals | 如果是 many 就需要填写值的选项，以逗号分隔 |          |

- 响应数据

```
{
  "data": {
    "attrId": "1",
    "attrName": "主观参数-型号",
    "catId": "1191",
    "attrSel": "only",
    "attrWrite": "manual",
    "deleteTime": null,
    "attrVals": "00002"
  },
  "meta": {
    "msg": "查询成功",
    "status": 207
  }
}
```

### 1.7.5. 编辑提交参数

- 请求路径：/attr/updAttr
- 请求方法：post
- 请求参数

| 参数名   | 参数说明               | 备注                        |
| -------- | ---------------------- | --------------------------- |
| catId    | 分类 ID                | 不能为空，携带在`请求体`中` |
| attrId   | 属性 ID                | 不能为空，携带在`请求体`中` |
| attrName | 新属性的名字           | 不能为空，携带在`请求体`中  |
| attrSel  | 属性的类型[many或only] | 不能为空，携带在`请求体`中  |
| attrVals | 参数的属性值           | 可选参数，携带在`请求体`中  |

- 响应数据

```
{
  "data": {
    "attrId": "1",
    "attrName": "主观参数-型号1",
    "catId": "1191",
    "attrSel": "only",
    "attrWrite": "manual",
    "deleteTime": null,
    "attrVals": "00002"
  },
  "meta": {
    "msg": "修改成功",
    "status": 203
  }
}
```