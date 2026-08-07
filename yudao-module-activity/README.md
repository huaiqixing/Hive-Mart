# yudao-module-activity 活动平台模块

活动平台业务模块，用于承载营销活动相关功能。

## 功能规划

> 🚧 模块初始化中，以下为规划方向，可按需调整：

- 营销活动（满减、折扣、秒杀）
- 优惠券（领取、核销、过期）
- 签到（每日签到、积分奖励）
- 抽奖（大转盘、刮刮卡）
- 活动数据统计

## 模块分层

遵循芋道统一分层规范：

| 包 | 职责 |
|---|---|
| `api` | 模块间内部 API，供其它模块跨模块调用 |
| `controller/admin` `controller/app` | 管理后台 / 用户端 REST 接口 |
| `service` | 业务逻辑 |
| `dal` | 数据访问（mysql/redis/dataobject） |
| `convert` | MapStruct 对象转换 |
| `enums` | 枚举与错误码 |
| `framework` | 模块级框架定制 |
| `mq` | 消息生产消费 |
| `job` | 定时任务 |
| `util` | 工具类 |

## 技术能力（继承自 yudao-framework）

- 多租户 SaaS（透明隔离）
- 数据权限（部门级 / 自定义规则）
- 认证鉴权（Token + 按钮级权限）
- 代码生成器（infra 模块一键生成 CRUD）
- 多数据库 / 多消息队列适配

## 开发指引

1. 在 `sql/mysql/ruoyi-vue-pro.sql` 中追加活动相关建表语句
2. 使用 infra 代码生成器生成 Controller / Service / DO 骨架
3. 业务代码遵循 `controller -> service -> dal` 调用链，跨模块通过 `api` 包交互
