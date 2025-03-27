# 基础信息

|      |      |
|------|------|
| 名称 | RedisChatMemory |
| 编码语言 | .java |
| 代码路径 | spring-ai-alibaba/community/memories/spring-ai-alibaba-redis-memory/src/main/java/com/alibaba/cloud/ai/memory/redis/RedisChatMemory.java |
| 包名 | com.alibaba.cloud.ai.memory.redis |
| 依赖项 | ['java.util.ArrayList', 'java.util.List', 'com.alibaba.cloud.ai.memory.redis.serializer.MessageDeserializer', 'com.fasterxml.jackson.core.JsonProcessingException', 'com.fasterxml.jackson.databind.ObjectMapper', 'com.fasterxml.jackson.databind.module.SimpleModule', 'org.slf4j.Logger', 'org.slf4j.LoggerFactory', 'redis.clients.jedis.Jedis', 'redis.clients.jedis.JedisPool', 'redis.clients.jedis.JedisPoolConfig', 'org.springframework.ai.chat.memory.ChatMemory', 'org.springframework.ai.chat.messages.Message'] |
| 概述说明 | RedisChatMemory类管理聊天内存，支持Redis存储、增删改查消息。 |

# 说明

RedisChatMemory类是一个用于管理聊天内存的工具，支持通过Redis进行数据存储。该类提供了多种功能，包括添加新的聊天消息、获取已存储的消息、清除现有消息以及更新消息内容。通过这些功能，RedisChatMemory类能够有效地管理和维护聊天记录，确保数据的持久性和可访问性。

# 类列表 Class Summary

| 名称   | 类型  | 说明 |
|-------|------|-------------|
| RedisChatMemory | class | RedisChatMemory类实现聊天内存管理，支持Redis存储、添加、获取、清除和更新消息。 |



## 类 RedisChatMemory

|      |      |
|------|------|
| 访问范围 | public |
| 类型 | class |
| 名称 | RedisChatMemory |
| 说明 | RedisChatMemory类实现聊天内存管理，支持Redis存储、添加、获取、清除和更新消息。 |


### UML类图

```mermaid
classDiagram
    class RedisChatMemory {
        -Logger logger
        -String DEFAULT_KEY_PREFIX
        -String DEFAULT_HOST
        -int DEFAULT_PORT
        -String DEFAULT_PASSWORD
        -JedisPool jedisPool
        -Jedis jedis
        -ObjectMapper objectMapper
        +RedisChatMemory()
        +RedisChatMemory(String host, int port, String password)
        +void add(String conversationId, List~Message~ messages)
        +List~Message~ get(String conversationId, int lastN)
        +void clear(String conversationId)
        +void close()
        +void clearOverLimit(String conversationId, int maxLimit, int deleteSize)
        +void updateMessageById(String conversationId, String messages)
    }
    <<Interface>> class ChatMemory {
        +void add(String conversationId, List~Message~ messages)
        +List~Message~ get(String conversationId, int lastN)
        +void clear(String conversationId)
    }
    <<Interface>> class AutoCloseable {
        +void close()
    }
    RedisChatMemory ..|> ChatMemory
    RedisChatMemory ..|> AutoCloseable
```

**描述：**  
`RedisChatMemory` 类实现了 `ChatMemory` 和 `AutoCloseable` 接口，用于管理基于 Redis 的聊天记录。它通过 `Jedis` 客户端与 Redis 进行交互，支持添加、获取、清除聊天记录，以及清理超出限制的记录和更新特定消息。类中包含默认的 Redis 连接配置，并通过 `ObjectMapper` 进行消息的序列化和反序列化。`ChatMemory` 接口定义了基本的聊天记录操作方法，而 `AutoCloseable` 接口则确保资源在使用后能够正确关闭。


### 内部方法调用关系图

```mermaid
graph TD
    A["类RedisChatMemory"]
    B["属性: Logger logger"]
    C["属性: String DEFAULT_KEY_PREFIX"]
    D["属性: String DEFAULT_HOST"]
    E["属性: int DEFAULT_PORT"]
    F["属性: String DEFAULT_PASSWORD"]
    G["属性: JedisPool jedisPool"]
    H["属性: Jedis jedis"]
    I["属性: ObjectMapper objectMapper"]
    J["构造方法: RedisChatMemory()"]
    K["构造方法: RedisChatMemory(String host, int port, String password)"]
    L["方法: add(String conversationId, List<Message> messages)"]
    M["方法: get(String conversationId, int lastN)"]
    N["方法: clear(String conversationId)"]
    O["方法: close()"]
    P["方法: clearOverLimit(String conversationId, int maxLimit, int deleteSize)"]
    Q["方法: updateMessageById(String conversationId, String messages)"]

    A --> B
    A --> C
    A --> D
    A --> E
    A --> F
    A --> G
    A --> H
    A --> I
    A --> J
    A --> K
    A --> L
    A --> M
    A --> N
    A --> O
    A --> P
    A --> Q

    J --> K
    K --> G
    K --> H
    K --> I
    L --> "生成key"
    L --> "序列化消息"
    L --> "存储消息"
    M --> "生成key"
    M --> "获取消息"
    M --> "反序列化消息"
    N --> "生成key"
    N --> "删除消息"
    O --> "关闭Jedis连接"
    O --> "关闭JedisPool"
    P --> "生成key"
    P --> "获取所有消息"
    P --> "删除超限消息"
    P --> "重新存储消息"
    Q --> "生成key"
    Q --> "删除旧消息"
    Q --> "存储新消息"
```

这段代码定义了一个名为 `RedisChatMemory` 的类，用于管理与Redis数据库的聊天记录交互。类中包含多个方法，用于添加、获取、清除、关闭连接、清理超限消息以及更新消息等操作。代码通过Jedis库与Redis进行交互，并使用ObjectMapper进行消息的序列化和反序列化。流程图展示了类中各个方法之间的调用关系以及主要操作步骤。

### 字段列表 Field List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| logger = LoggerFactory.getLogger(RedisChatMemory.class) | Logger | RedisChatMemory类中定义了一个静态的Logger实例。 |
| DEFAULT_PASSWORD = null | String | 默认密码设为空值。 |
| jedis | Jedis | 私有Jedis实例变量。 |
| jedisPool | JedisPool | 私有且不可变的JedisPool实例。 |
| DEFAULT_HOST = "127.0.0.1" | String | 默认主机地址为127.0.0.1。 |
| DEFAULT_KEY_PREFIX = "spring_ai_alibaba_chat_memory" | String | 默认键前缀为spring_ai_alibaba_chat_memory。 |
| DEFAULT_PORT = 6379 | int | 默认端口号为6379。 |
| objectMapper | ObjectMapper | 私有且不可变的ObjectMapper实例。 |

### 方法列表 Method List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| close | void | 关闭Redis连接和Jedis池，并记录日志。 |
| updateMessageById | void | 通过ID更新Redis中的聊天记录，删除旧记录并添加新消息。 |
| add | void | 将消息序列化后存入Redis列表，记录日志。 |
| clear | void | 清除指定会话ID的消息记录。 |
| get | List<Message> | 从Redis获取指定对话的最后N条消息并反序列化为对象。 |
| clearOverLimit | void | 清理Redis中超过最大限制的聊天记录，保留指定数量。 |




