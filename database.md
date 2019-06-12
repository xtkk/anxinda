# 数据库设计文档

## VIP客户表
> 设计目的：由于该软件针对特定用户，所以没有注册功能，所有订车人信息由甲方提供，并在后台导入

字段 | 类型 | 说明
---|---|---
id | int64 | 主键id
name | string | 订车人姓名
phone | string | 订车人手机号
openid | string | 小程序的openid
createdAt | date | 导入时间
updatedAt | date | 更新时间
lastLoginAt | date | 最后登录时间


## 司机表
字段 | 类型 | 说明
---|---|---
id | int64 | 主键id
name | string | 司机姓名
phone | string | 司机电话
createdAt | date | 司机注册时间
updatedAt | date | 司机更新时间
active | bool | 当天是否打卡(每天凌晨自动重置为false)


## 车辆表
字段 | 类型 | 说明
---|---|---
id | int64 | 主键id
modal | string | 车型
color | string | 颜色
No | string | 车牌号码
sales | int | 座位数量
createdAt | date | 车辆登记时间


## 订单表
字段 | 类型 | 说明
---|---|---
id | string | 订单ID
name | string | 乘车人姓名
phone | string | 乘车人电话
start_addr | string | 上车点位置
start_loc | 暂定 | 上车点坐标
end_addr | string | 下车点位置
end_loc | 暂定 | 下车点坐标
distance | number | 订单距离
date | date | 预约时间
price | decimal | 订单费用
extra_price | decimal | 增值服务费
state | string | 订单状态
remark | text | 订单备注
reason | string | 订单失败或取消原因
comment | text | 订单评价
createdAt | date | 订单创建时间
successAt | date | 订单预约成功时间
finishedAt | date | 订单完成时间
canceledAt | date | 订单取消时间


## 订单调度表
字段 | 类型 | 说明
---|---|---
id | int64 | 主键id
orderId | string | 订单ID
driverId | string | 司机id
carId | string | 车辆id
createdAt | date | 调度时间
active | bool | 是否有效(订单完成自动失效)


## 后台管理员表(客服使用)
字段 | 类型 | 说明
---|---|---
id | int64 | 主键id
username | string | 用户名
passwd | string | 密码
salt | string | 盐
lastLoginAt | date | 最后登录时间
loastLoginIp | string | 最后登录ip
loginAccount | int | 登录次数


## 系统日志表
字段 | 类型 | 说明
---|---|---
id | int64 | 主键id
type | string | 日志类型
level | string | 日志级别
date | date | 日志记录时间
content | string | 日志内容