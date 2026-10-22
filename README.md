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
