# BH_dianping

基于黑马点评教学项目继续开发的本地生活服务后端练习项目。保留了店铺、探店博客、关注和优惠券等基础功能，并围绕缓存、限流及秒杀链路进行了扩展与实验。本仓库用于展示学习过程与代码实现，不是生产系统。

## 技术栈

Java 8、Spring Boot 2.3、MyBatis-Plus、MySQL、Redis、Caffeine、Kafka。

## 代码导航

- `src/main/java/com/hmdp/service/impl/`：店铺、博客、优惠券及订单业务实现。
- `src/main/java/com/hmdp/service/cache/`：优惠券列表的 Caffeine / Redis 缓存实现。
- `src/main/java/com/hmdp/limiter/` 与 `src/main/resources/limiter.lua`：注解式 Redis 滑动窗口限流。
- `src/main/resources/seckill.lua`：秒杀库存和一人一单的 Redis 原子校验。
- `src/main/resources/db/hmdp.sql`：数据库表结构及部分演示数据；示例用户记录已移除。

## 本地运行

1. 准备 JDK 8、Maven、MySQL、Redis。根据 `src/main/resources/application.yaml` 配置连接地址，并设置环境变量 `DB_PASSWORD`。
2. 创建 `hmdp` 数据库，导入 `src/main/resources/db/hmdp.sql`。
3. 运行 `mvn spring-boot:run`。默认端口为 `8081`。

## 当前状态

秒杀订单的 Kafka 消费监听目前处于注释状态。当前代码只完成了 Redis 资格校验和消息发送的实验部分，尚不能保证秒杀订单最终落库；这一链路仍需补全消费、失败补偿和一致性验证。仓库中没有智能客服、支付关单等功能实现，请以代码为准。

## 来源

本项目基于黑马点评教学项目及已有的 Gitee 工程继续学习和修改。基础业务和教学代码并非全部由本人从零编写；可查看各模块代码区分原有实现与后续扩展。
