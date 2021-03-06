Manager
---
>By zjien

##**超级管理员**
##### 以下接口只适用于超管

#### **创建管理员（即场馆负责人）**
`/Admin/Manager/createManager` `POST`

字段 | 描述 | 是否必须 | 数据类型 | 备注
------------------------- | -------------------------- | :-----------------------: | --------------------------- | ----------------------
account | 管理员账号 | Y | string | 6-12位
password | 密码 | Y | string | 6-18位

**Response**
```json
{
    "code": 20000,
    "response": "创建成功"
}
```
---

#### **删除管理员**
`/Admin/Manager/deleteManager` `POST`

字段 | 描述 | 是否必须 | 数据类型 | 备注
------------------------- | -------------------------- | :-----------------------: | --------------------------- | ----------------------
ma_id | 管理员表id | Y | int | 
**Response**
```json
{
    "code": 20000,
    "response": "删除成功"
}
```
---

#### **禁用管理员**
`/Admin/Manager/banManager` `POST`

字段 | 描述 | 是否必须 | 数据类型 | 备注
------------------------- | -------------------------- | :-----------------------: | --------------------------- | ----------------------
ma_id | 管理员表id | Y | int | 
**Response**
```json
{
    "code": 20000,
    "response": "禁用成功"
}
```
---

##**管理员**
##### 以下接口只适用于管理员

#### **创建员工**
`/Admin/Manager/createStaff` `POST`

字段 | 描述 | 是否必须 | 数据类型 | 备注
------------------------- | -------------------------- | :-----------------------: | --------------------------- | ----------------------
account | 员工账号 | Y | string | 6-12位
password | 密码 | Y | string | 6-18位

**Response**
```json
{
    "code": 20000,
    "response": "创建成功"
}
```
---

#### **删除员工**
`/Admin/Manager/deleteStaff` `POST`

字段 | 描述 | 是否必须 | 数据类型 | 备注
------------------------- | -------------------------- | :-----------------------: | --------------------------- | ----------------------
ma_id | 员工id | Y | int | 注意管理员和员工放同一张表
**Response**
```json
{
    "code": 20000,
    "response": "删除成功"
}
```
---

#### **禁用员工**
`/Admin/Manager/banStaff` `POST`

字段 | 描述 | 是否必须 | 数据类型 | 备注
------------------------- | -------------------------- | :-----------------------: | --------------------------- | ----------------------
ma_id | 员工id | Y | int | 注意管理员和员工放同一张表 
**Response**
```json
{
    "code": 20000,
    "response": "禁用成功"
}
```
---

## **员工**
##### 以下接口只适用于员工

#### **查看预约订单**
`/Admin/Manager/listBooking` `GET`
##### 返回的字段解释

字段 | 描述 | 是否必须 | 数据类型 | 备注
------------------------- | -------------------------- | :-----------------------: | --------------------------- | ----------------------
dv_id | 场馆预约订单id |  | int | 
ma_id | 该场馆管理员id |  | int |
subscriber | 预约人id |  | int | 即用户id
vi_id | 场馆id |  | int |
date_time | 预约时间 |  | int | 即用户使用场馆的时间
order_time | 下单时间 |  | int | 即用户下单预约的时间
done | 完成 |  | bool | 是否结单，0代表未结，1代表已结
**Response**
```json
{
    "code": 20000,
    "response": [
        {
            "dv_id": "1",
            "ma_id": "2",
            "subscriber": "1",
            "vi_id": "1"
            "date_time": "1423159938",
            "order_time": "1423151968",
            "done": "0"
        },
        {
            "dv_id": "2",
            "ma_id": "3",
            "subscriber": "5",
            "vi_id": "2"
            "date_time": "1423159950",
            "order_time": "1423151998",
            "done": "0"
        },
        {
            "dv_id": "6",
            "ma_id": "7",
            "subscriber": "8",
            "vi_id": "6"
            "date_time": "1423159960",
            "order_time": "1423152968",
            "done": "0"
        }
    ]
}
```
---

#### **结单**
`/Admin/Manager/doneOrder` `POST`

字段 | 描述 | 是否必须 | 数据类型 | 备注
------------------------- | -------------------------- | :-----------------------: | --------------------------- | ----------------------
dv_id | 场馆预约表id | Y | int | 一般在列表中获取
**Response**
```json
{
    "code": 20000,
    "response": "操作成功"
}
```
---

#### **查看预约用户的信息**
`/Admin/Manager/getUserInfo` `POST`

字段 | 描述 | 是否必须 | 数据类型 | 备注
------------------------- | -------------------------- | :-----------------------: | --------------------------- | ----------------------
subscriber | 预约用户的id | Y | int | 一般在预约订单列表中获取
**Response**  
```json
{
    "code": 20000,
    "response": {
        "u_id": "2",
        "account": "zjien1",
        "nickname": "zjien1",
        "sex": "男",
        "phone": null,
        "email": "zjien1@qq.com",
        "avatar": null,
        "intro": null,
        "birth": null,
        "spt_favor": null,
        "region": "江门",
        "ctime": "1422430617",
        "cIP": "127.0.0.1",
        "last_time": "1422430617",
        "last_IP": "127.0.0.1"
    }
}
```
---

## **通用**
##### 以下接口只适用于超管、管理员、员工

#### **登录**
`/Admin/Manager/login` `POST`

字段 | 描述 | 是否必须 | 数据类型 | 备注
------------------------- | -------------------------- | :-----------------------: | --------------------------- | ----------------------
account | 账号 | Y | string | 
password | 密码 | Y | string | 
**Response**  
```json
{
    "code": 20000,
    "response": {
        "ma_id": "1",
        "account": "admin1",
        "nickname": "admin1",
        "phone": "12345678901",
        "email": "admin1@qq.com",
        "create_time": "1422430617",
        "create_IP": "127.0.0.1",
        "last_time": "1422430617",
        "last_IP": "127.0.0.1"
    }
}
```
---


#### **更新信息**
`/Admin/Manager/update` `POST`

字段 | 描述 | 是否必须 | 数据类型 | 备注
------------------------- | -------------------------- | :-----------------------: | --------------------------- | ----------------------
nickname | 昵称 | N | string |
email | 电邮 | N | string |
phone | 电话 | N | string |
**Response**  
```json
{
    "code": 20000,
    "response": {
        "ma_id": "1",
        "account": "admin1",
        "nickname": "newnickname",
        "phone": "1234586522",
        "email": "newemail@qq.com",
        "create_time": "1422430617",
        "create_IP": "127.0.0.1",
        "last_time": "1422430617",
        "last_IP": "127.0.0.1"
    }
}
```
---

#### **更新密码**
`/Admin/Manager/updatePassword` `POST`

字段 | 描述 | 是否必须 | 数据类型 | 备注
------------------------- | -------------------------- | :-----------------------: | --------------------------- | ----------------------
password | 原密码 | Y | string |
newPassword | 新密码 | Y | string |
**Response**  
```json
{
    "code": 20000,
    "response": "操作成功"
}
```
---

#### **退出**
`/Admin/Manager/logout` `POST`

**Response**  
```json
{
    "code": 20000,
    "response": "操作成功"
}
```
---