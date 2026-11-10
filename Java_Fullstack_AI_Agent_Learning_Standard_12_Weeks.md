# Java 全栈进阶学习规范

**适用对象：** 有约 5 年前端经验，熟悉 React 与
Vue，有其他后端语言经验，希望转向 Java 后端，并能够使用 Codex、Claude
Code 等 AI Agent 开发和维护 Java 项目的工程师。

**学习周期：** 12 周\
**投入时间：** 每天 2--3 小时，每周约 14--20 小时\
**主线项目：** AI API Gateway Platform

> 核心原则：不重复学习初级编程；以真实业务项目驱动知识学习；从第一周开始使用
> AI Agent，但由工程师负责架构、验证与最终决策。

------------------------------------------------------------------------

## 1. 学习目标

12 周后，目标是建立可持续的 Java 工程能力，而不是把自己包装成资深 Java
专家。

-   能够独立阅读、理解和修改 Spring Boot 项目。
-   能够设计数据库、REST API、业务模块与事务边界。
-   能够处理认证授权、并发、幂等、缓存和数据一致性问题。
-   能够开发、测试、部署一个具有完整业务闭环的 Java 服务。
-   能够审查 AI 生成的代码、SQL、测试和架构变更。
-   能够根据日志、指标、线程与 SQL 信息定位常见故障。

## 2. 技术栈基线

  -----------------------------------------------------------------------------------------------
  领域                    主线选择                       学习边界
  ----------------------- ------------------------------ ----------------------------------------
  语言与运行时            Java 21 LTS、JVM               泛型、集合、注解、反射、并发基础和常见
                                                         JVM 诊断

  构建与测试              Maven、JUnit 5、Mockito        构建、测试、依赖与测试问题定位

  应用框架                Spring Boot、Spring            IoC、DI、AOP、Bean、请求链路和配置
                          MVC、Validation                

  安全                    Spring Security、JWT、RBAC     认证、授权、密码存储、接口权限

  数据访问                MySQL 8、MyBatis、Flyway       SQL、索引、事务、锁、数据库迁移

  缓存与异步              Redis；后续引入 MQ             缓存一致性、限流、幂等；先同步后异步

  部署运维                Docker Compose、Nginx、GitHub  可重复部署、配置隔离、日志与健康检查
                          Actions                        

  AI 协作                 Codex / Claude                 研究、计划、实现、测试、Review、Debug
                          Code、AGENTS.md、MCP（按需）   
  -----------------------------------------------------------------------------------------------

**版本原则：** Java 21
是学习基线，不代表所有项目都必须使用该版本。实际项目以 Spring
Boot、依赖兼容性和组织运行环境为准，不为追新而频繁升级。

## 3. 知识依赖顺序

1.  **Java 语言与运行机制：** 泛型、集合、异常、注解、反射、JVM
    基础、线程基础。
2.  **Spring 核心：** IoC、DI、Bean 生命周期、AOP、代理、自动配置。
3.  **Web 与数据访问：** Spring MVC
    请求链路、参数绑定、校验、异常处理、MyBatis、SQL。
4.  **事务与业务建模：**
    事务边界、隔离级别、MVCC、锁、幂等、业务不变量。
5.  **安全与并发：** Spring
    Security、JWT、RBAC、线程池、Redis、限流和缓存一致性。
6.  **生产工程：** 测试、Docker、CI/CD、日志、指标、追踪、性能诊断。
7.  **AI Agent 工程化：**
    项目上下文、任务拆解、实施计划、受控修改、测试验证、代码审查与维护。

AI Agent 从第 1
周开始使用，但遵循"先理解、再委托；先计划、再修改；先验证、再合并"。Agent
是执行与研究助手，不是最终架构责任人。

## 4. 每日与每周学习节奏

  --------------------------------------------------------------------------------------
  时间                    活动                    要求
  ----------------------- ----------------------- --------------------------------------
  30 分钟                 概念学习                围绕当天一个问题学习，不泛读大量资料

  60--90 分钟             编码与实战              将概念应用到练习项目或主线项目

  30 分钟                 AI Review 与验证        检查
                                                  Diff、测试、异常路径、事务与安全边界

  15--30 分钟             复盘记录                记录概念、踩坑、未解决问题和下一步
  --------------------------------------------------------------------------------------

执行规则：

-   每周至少完成一个可运行、可验证的交付物。
-   每周至少一次复盘：解释关键机制，而不只是列出学过的 API。
-   每个功能必须有验收条件；没有运行测试，不得标记为完成。
-   时间不足时优先保留编码、测试和复盘，减少无目标的视频观看。

------------------------------------------------------------------------

## 5. 12 周学习任务与验收标准

### 第 1 周｜Java 语言差异与 JVM 基础

**学习重点**

-   泛型与类型擦除。
-   集合与 Map。
-   Stream / Lambda。
-   异常体系。
-   注解与反射。
-   线程基础。
-   Maven、JUnit 5。

**实战交付**

建立纯 Java 项目，实现：

-   泛型转换。
-   内存缓存。
-   线程安全计数器。
-   基于注解的简单字段校验器。

**验收标准**

-   [ ] 能读写常见 Java 泛型、集合和 Stream 代码。
-   [ ] 能解释 HashMap 与 ConcurrentHashMap 的差异。
-   [ ] 能解释注解、反射和类型擦除的基本机制。
-   [ ] 能用 Maven 构建并用 JUnit 5 编写测试。

### 第 2 周｜Spring Framework 核心

**学习重点**

-   IoC、DI。
-   Bean 生命周期与 Scope。
-   构造器注入。
-   AOP。
-   JDK 动态代理、CGLIB。
-   Spring Boot 自动配置。

**实战交付**

实现简化版 IoC 容器：

1.  扫描指定包。
2.  发现组件。
3.  实例化对象。
4.  注册 Bean。
5.  实现构造器注入。

**验收标准**

-   [ ] 能解释 IoC、DI、AOP 的作用与边界。
-   [ ] 能说明 Bean 创建和依赖注入的基本过程。
-   [ ] 能解释代理对象与事务/AOP 拦截的关系。
-   [ ] 能识别常见循环依赖问题。

### 第 3 周｜Spring Boot Web

**学习重点**

-   Spring MVC 请求链路。
-   Controller / Service / Mapper。
-   Filter / Interceptor。
-   参数绑定与 Validation。
-   全局异常处理。
-   DTO / VO / Entity。
-   OpenAPI。
-   多环境配置。

**实战交付**

实现用户 CRUD API，包含分页、校验、统一响应、异常处理和 Swagger/OpenAPI
文档。

接口示例：

``` text
POST   /api/users
GET    /api/users/{id}
GET    /api/users
PUT    /api/users/{id}
DELETE /api/users/{id}
```

**验收标准**

-   [ ] 能独立实现一组 REST API。
-   [ ] 能解释请求从 Servlet 容器到 Controller 的主要链路。
-   [ ] 能区分 DTO、Entity、VO。
-   [ ] 能通过 Swagger UI 调试接口并编写接口测试。

### 第 4 周｜MySQL、MyBatis 与事务

**学习重点**

-   SQL 执行计划。
-   B+Tree、联合索引、EXPLAIN。
-   ACID、隔离级别、MVCC。
-   行锁、间隙锁。
-   MyBatis。
-   Spring 事务。

**实战交付**

实现账户余额系统：

-   账户创建。
-   充值。
-   扣款。
-   转账。
-   流水记录。

并发发起 100 次扣款，验证余额。

**验收标准**

-   [ ] 能设计账户与流水表。
-   [ ] 能分析关键 SQL 的执行计划与索引。
-   [ ] 能解释事务隔离、MVCC 和常见锁。
-   [ ] 能正确划分事务边界并排查常见事务失效问题。
-   [ ] 并发测试不出现超扣、负余额或流水不一致。

### 第 5 周｜Spring Security 与权限

**学习重点**

-   Security Filter Chain。
-   Authentication / Authorization。
-   SecurityContext。
-   JWT、Refresh Token。
-   密码哈希。
-   RBAC。
-   CORS / CSRF。
-   API Key。

**实战交付**

实现登录、登出、刷新 Token、角色权限、资源归属校验和安全测试。

角色示例：

-   Admin
-   User
-   Operator

权限示例：

-   `user:read`
-   `user:write`
-   `order:read`
-   `order:refund`

**验收标准**

-   [ ] 能解释认证与授权的区别。
-   [ ] 能配置 Security Filter Chain。
-   [ ] 普通用户不能访问管理员接口或其他用户私有数据。
-   [ ] 密码安全存储，Token 失效策略清晰。
-   [ ] 关键权限有自动化测试。

### 第 6 周｜Redis、并发与幂等

**学习重点**

-   Redis 数据结构。
-   Cache Aside。
-   缓存一致性。
-   缓存穿透、击穿、雪崩。
-   线程池、原子操作。
-   幂等键。
-   限流。
-   分布式锁风险。

**实战交付**

为账户系统增加：

-   Redis 缓存。
-   查询限流。
-   幂等请求 ID。
-   并发扣款保护。
-   重复请求检测。

**验收标准**

-   [ ] 能解释常见缓存故障及应对策略。
-   [ ] 能设计可验证的幂等接口。
-   [ ] 能实现基础限流并解释限流算法。
-   [ ] 能使用线程池处理受控异步任务。
-   [ ] 能说明 Redis 锁的失效、续期和误用风险。

### 第 7 周｜AI API Gateway 架构启动

**学习重点**

-   模块化单体。
-   领域边界。
-   数据库 ER 图。
-   API 契约。
-   配置管理。
-   Flyway。
-   Docker Compose。
-   健康检查。

**实战交付**

初始化主线项目，完成：

1.  README。
2.  架构图。
3.  模块职责。
4.  ER 图。
5.  API 契约。
6.  基础环境。
7.  健康检查。

**验收标准**

-   [ ] 架构图和模块职责清晰。
-   [ ] 数据库表结构有主键、唯一约束和必要索引。
-   [ ] MySQL、Redis、应用可通过 Docker Compose 启动。
-   [ ] Flyway 能从空库完成迁移。
-   [ ] Agent 能依据项目文档理解项目约束。

### 第 8 周｜核心业务模块

**学习重点**

-   用户、角色。
-   API Key。
-   渠道、模型、分组。
-   钱包、流水。
-   兑换码。
-   审计日志。

**实战交付**

完成用户认证、API Key
生命周期、渠道/模型配置、充值扣款、兑换码创建和兑换。

**验收标准**

-   [ ] API Key 不以明文持久化；明文仅在创建时展示。
-   [ ] 资金变动有流水，金额使用 BigDecimal。
-   [ ] 兑换码只能成功兑换一次。
-   [ ] 关键业务有唯一约束、幂等保护和自动化测试。

### 第 9 周｜API 转发、SSE 与异步

**学习重点**

-   Java HttpClient 或 Spring WebClient。
-   连接池。
-   超时与重试边界。
-   SSE。
-   CompletableFuture。
-   MQ 基础。
-   请求状态机。

**实战交付**

先完成非流式上游 API 转发，再实现
SSE；加入请求状态、额度预留/结算和调用记录。

建议请求流程：

``` text
用户请求
   ↓
API Key 验证
   ↓
模型路由
   ↓
检查用户余额
   ↓
创建请求记录 / 预留额度
   ↓
转发上游 API
   ↓
接收响应 / SSE
   ↓
计算实际费用
   ↓
结算余额
   ↓
记录调用日志
```

**验收标准**

-   [ ] 能完成真实上游 API 转发。
-   [ ] 能处理超时、取消、上游错误和流式断开。
-   [ ] 不在等待远程 HTTP 时持有长数据库事务。
-   [ ] 结算、退款和回调具有幂等性。
-   [ ] 能解释请求状态和资金状态的转换。

### 第 10 周｜测试体系与部署

**学习重点**

-   JUnit 5、Mockito。
-   Spring Boot Test、MockMvc。
-   Testcontainers。
-   CI/CD。
-   Docker 镜像。
-   配置隔离。
-   日志与监控。

**实战交付**

为关键业务补充集成测试；配置 CI
自动构建、测试和镜像构建；完成测试环境部署。

**验收标准**

-   [ ] 关键业务同时覆盖成功路径和失败路径。
-   [ ] 使用 Testcontainers 验证真实数据库行为。
-   [ ] CI 能自动运行测试并阻止失败变更合并。
-   [ ] 生产密钥与配置不写入代码仓库。
-   [ ] 部署过程可重复，具备健康检查和回滚方案。

### 第 11 周｜JVM、性能与故障排查

**学习重点**

-   Heap / Stack / Metaspace。
-   GC 日志。
-   jcmd / jstack / jstat。
-   线程池与连接池。
-   慢 SQL。
-   Trace ID。
-   JMeter 或 k6。

**实战交付**

模拟 CPU 异常、慢
SQL、线程池耗尽或连接池耗尽，完成故障定位记录和压测报告。

**验收标准**

-   [ ] 能定位一次慢 SQL 并给出证据。
-   [ ] 能分析线程池和数据库连接池状态。
-   [ ] 能使用 JVM 诊断工具采集信息。
-   [ ] 能通过 Trace ID 串联请求日志。
-   [ ] 压测报告包含环境、场景、指标和结论，不虚构性能数字。

### 第 12 周｜AI Agent 工程化与交付

**学习重点**

-   AGENTS.md。
-   项目上下文。
-   Research / Planning / Implementation / Review / Debugging。
-   Git Diff。
-   测试门禁。
-   架构决策记录（ADR）。

**实战交付**

让 Agent：

1.  分析项目。
2.  实现新模块。
3.  补充测试。
4.  定位预设事务 Bug。
5.  审查并发风险。
6.  根据日志排障。

所有变更由工程师独立审核后再合并。

**验收标准**

-   [ ] 能为 Agent 提供明确的项目约束和验收条件。
-   [ ] 能要求 Agent 先研究和计划，再修改代码。
-   [ ] 能审查 SQL、事务、安全、并发与测试质量。
-   [ ] 能通过 Diff、测试和日志验证 Agent 交付。
-   [ ] 项目有可运行说明、架构文档、数据库迁移和维护手册。

------------------------------------------------------------------------

## 6. 主线实战项目：AI API Gateway Platform

项目定位：模块化单体的 AI API 聚合与计费平台，用于练习用户、API
Key、渠道路由、模型分组、钱包、兑换码、请求转发、费用结算和调用统计。

> 未完成安全审查、压测和运维准备前，不应直接承载真实资金或生产流量。

### 6.1 模块划分

  模块                 职责与关键问题
  -------------------- ------------------------------------------------
  Auth / User          登录、身份、用户资料、资源归属和权限
  API Key              创建、展示、哈希存储、禁用、权限范围与轮换
  Channel / Model      上游渠道配置、模型映射、模型分组和路由策略
  Wallet / Billing     账户、资金流水、额度预留、结算、退款、对账
  Voucher              兑换码批次、有效期、单次兑换与安全存储策略
  Gateway              请求校验、路由、上游转发、超时、SSE 和错误映射
  Usage / Statistics   调用记录、费用统计、审计和运营报表

### 6.2 核心业务不变量

-   余额不得因并发扣款而超扣；所有资金变动必须有可追溯流水。
-   同一支付回调、兑换码或幂等请求不能重复入账或重复扣款。
-   API Key、上游密钥、密码等敏感信息不得明文写入日志。
-   客户端不能决定支付成功、最终费用或自身权限。
-   远程上游调用不应被包在长时间数据库事务中。
-   请求状态、额度状态和资金流水需要可审计、可恢复。

### 6.3 建议目录结构

``` text
ai-gateway/
├── AGENTS.md
├── README.md
├── docs/
│   ├── architecture.md
│   ├── database.md
│   ├── api-contract.md
│   ├── business-rules.md
│   ├── security.md
│   ├── runbook.md
│   └── adr/
├── backend/
│   ├── pom.xml
│   └── src/
├── frontend/
├── docker-compose.yml
└── .github/workflows/
```

------------------------------------------------------------------------

## 7. AI Agent 协作规范

### 7.1 标准工作流

1.  **需求澄清：** 工程师定义业务目标、边界条件、权限和验收标准。
2.  **Research：** Agent
    先阅读文档与代码，解释现状和调用链，不直接改文件。
3.  **Planning：** Agent 列出受影响模块、文件、数据库/API
    变化、风险与测试计划。
4.  **Human Review：** 工程师确认事务边界、数据一致性、安全和兼容性。
5.  **Implementation：** Agent 小步实施，避免一次性大范围重构。
6.  **Verification：**
    运行编译、单元测试、集成测试、静态检查，检查迁移脚本。
7.  **Code Review：** 工程师审查
    Diff、SQL、异常处理、日志、权限和并发行为。
8.  **Delivery：** 更新文档、记录 ADR、提交 Git，并说明未解决风险。

### 7.2 Agent 使用红线

-   禁止在没有阅读现有实现前直接重写模块。
-   禁止擅自改变业务规则、数据库契约或 API 契约。
-   禁止把密钥、Token、真实用户数据放入提示词或日志。
-   禁止只用 Agent
    自己生成的测试证明实现正确；关键业务必须有独立验收场景。
-   禁止未经审查执行破坏性数据库操作、生产部署或数据迁移。
-   Agent 未运行测试时，必须明确标注未验证，不得声称已完成。

## 8. AGENTS.md 项目规则模板

将以下内容作为项目根目录 `AGENTS.md` 的起点，再按实际仓库调整：

``` markdown
# Java Backend Engineering Rules

## Project Stack
- Java 21; Spring Boot version follows project compatibility.
- Maven, Spring MVC, MyBatis, MySQL, Redis, JUnit 5.

## Architecture
- Use a modular monolith unless an approved ADR says otherwise.
- Keep Controller / Service / Mapper responsibilities separate.
- Controllers handle HTTP concerns only.
- Business rules belong in Service/domain logic.
- Prefer constructor injection.

## Database
- Use Flyway for schema migrations.
- Never change production schema manually.
- Use BigDecimal for monetary values.
- Use database constraints for critical invariants.
- Review indexes and EXPLAIN for critical queries.

## Transactions
- Define transaction boundaries explicitly.
- Do not hold database transactions during external HTTP calls.
- Review propagation and rollback behavior.
- Financial operations must be idempotent and auditable.

## Security
- Never store plaintext passwords or API keys.
- Validate external input and enforce authorization server-side.
- Never expose secrets or sensitive data in logs.
- Do not trust client-submitted payment status or final price.

## Code Quality
- Avoid unnecessary abstractions and dependencies.
- Keep methods focused and readable.
- Preserve existing API and database contracts unless approved.

## Testing
- Test success and failure paths.
- Test transaction rollback and concurrency for financial flows.
- Use integration tests for database-dependent behavior.
- Do not claim completion without reporting executed commands/results.

## Agent Workflow
Before changes:
1. Read relevant docs and code.
2. Explain current behavior.
3. Identify affected modules and risks.
4. Propose implementation and test plan.

After changes:
1. Run build and relevant tests.
2. Review changed files and migrations.
3. Check security, transaction and concurrency behavior.
4. Summarize changes, evidence and unresolved risks.
```

------------------------------------------------------------------------

## 9. 暂缓学习的主题

  ------------------------------------------------------------------------------------------------
  主题                    当前策略                          重新学习的触发条件
  ----------------------- --------------------------------- --------------------------------------
  Spring Cloud / Nacos /  12 周主线暂缓                     单体系统瓶颈明确且确有服务拆分需求
  Dubbo                                                     

  Kubernetes              暂缓深入                          需要管理多服务、多副本和复杂部署环境

  Kafka 深入原理          先理解消息、ACK、重试、重复消费   业务吞吐或事件流场景确实需要

  Netty 源码              暂缓                              明确需要自定义高性能网络服务

  JVM GC 源码             先会诊断常见问题                  出现明确 GC 性能或延迟问题

  DDD 全套理论            先掌握模块化与业务边界            复杂领域模型和团队协作需要更严格建模

  Hibernate / JPA 深入    MyBatis 作为主线                  目标项目或团队主要使用 JPA

  Reactor 深入            先掌握同步、线程池和异步基础      项目使用 WebFlux 或响应式链路
  ------------------------------------------------------------------------------------------------

------------------------------------------------------------------------

## 10. 最终交付清单

-   [ ] 可运行的 Spring Boot 项目，具备明确模块边界。
-   [ ] 完整 README：本地启动、配置、测试、部署说明。
-   [ ] 架构图、ER 图、API 契约和关键业务规则文档。
-   [ ] Flyway 数据库迁移脚本和可复现的 Docker Compose 环境。
-   [ ] 认证授权、API Key、钱包、流水、兑换码等核心业务。
-   [ ] 上游 API 转发与 SSE，包含超时、异常和结算处理。
-   [ ] 关键业务的单元测试、集成测试和并发测试。
-   [ ] CI 自动构建与测试，部署和回滚说明。
-   [ ] 日志、Trace ID、健康检查和基础故障排查手册。
-   [ ] AGENTS.md、ADR 和 Agent 协作记录。
-   [ ] 至少一次由自己独立完成的 AI 代码审查与故障排查演练。

## 11. 学习原则与每周复盘

-   学概念不是为了背定义，而是能解释它解决什么问题、有什么代价、何时不该用。
-   先完成模块化单体，再考虑微服务；先理解事务，再引入复杂异步架构。
-   先掌握 SQL 与数据一致性，再依赖 ORM 或缓存抽象。
-   把 AI Agent
    当作高效率协作者，工程师始终对需求、架构、安全和交付负责。
-   每周复盘：能否不依赖 Agent
    解释关键代码？能否设计失败测试？能否定位实现问题？

建议每周记录：

``` text
本周交付物：
掌握的机制：
遇到的故障：
测试证据：
Agent 误判案例：
下一周风险与计划：
```

------------------------------------------------------------------------

**学习规范结束**
