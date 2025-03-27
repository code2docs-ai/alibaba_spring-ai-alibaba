# 基础信息

|      |      |
|------|------|
| 名称 | yuque |
| 编码语言 | .java |
| 代码路径 | spring-ai-alibaba/community/tool-calls/spring-ai-alibaba-starter-tool-calling-yuque/src/main/java/com/alibaba/cloud/ai/toolcalling/yuque |
| 包名 | spring-ai-alibaba.community.tool-calls.spring-ai-alibaba-starter-tool-calling-yuque.src.main.java.com.alibaba.cloud.ai.toolcalling.yuque |
| 概述说明 | Yuque服务类实现文档查询、更新、删除及书籍查询功能，通过WebClient发送HTTP请求，支持自动化配置。 |

# 说明

## 概述
该代码模块是一个基于Spring框架的Yuque API调用工具，旨在简化与Yuque文档管理系统的交互。模块通过使用`WebClient`工具，实现了对Yuque文档的查询、更新、删除以及书籍信息的查询功能。此外，模块还提供了自动配置功能，通过`YuqueAutoConfiguration`类，系统能够根据配置自动启用Yuque API调用，从而减少手动操作，提升用户体验。

## 主要业务场景
1. **文档查询**：通过`YuqueQueryDocService`类，系统能够发送POST请求，查询指定文档的信息，并将结果返回给调用方。
2. **文档更新**：`YuqueUpdateDocService`类负责发送PUT请求，更新指定文档的内容，并返回更新操作的响应结果。
3. **书籍查询**：`YuqueQueryBookService`类通过发送GET请求，查询书籍的相关信息，并将查询结果返回给调用方。
4. **文档删除**：`YuqueDeleteDocService`类负责发送DELETE请求，删除指定文档，并接收并返回服务器的响应。
5. **自动配置**：`YuqueAutoConfiguration`类通过配置自动启用Yuque API调用，简化文档管理流程，提高效率。
6. **属性管理**：`YuqueProperties`类用于管理Yuque API调用的基础URL和认证令牌信息，提供这些属性的getter和setter方法，方便配置和获取。


### 包内部结构视图

```mermaid
graph TD
    yuque --> YuqueQueryDocService.java
    yuque --> YuqueUpdateDocService.java
    yuque --> YuqueAutoConfiguration.java
    yuque --> YuqueQueryBookService.java
    yuque --> YuqueDeleteDocService.java
    yuque --> YuqueProperties.java
```

该流程图展示了 `yuque` 目录下的多个服务类文件的层级关系。`yuque` 作为根节点，包含了六个不同的服务类文件，分别是 `YuqueQueryDocService.java`、`YuqueUpdateDocService.java`、`YuqueAutoConfiguration.java`、`YuqueQueryBookService.java`、`YuqueDeleteDocService.java` 和 `YuqueProperties.java`。这些文件均直接隶属于 `yuque` 目录，没有进一步的子目录结构。

# 文件列表 File List

| 名称   | 类型  | 说明 |
|-------|------|-------------|
| [YuqueProperties.java](YuqueProperties.md) | file | 定义YuqueProperties类，含BASE_URL和authToken属性及其getter和setter方法。 |
| [YuqueDeleteDocService.java](YuqueDeleteDocService.md) | file | YuqueDeleteDocService通过WebClient发送DELETE请求实现文档删除功能并返回响应。 |
| [YuqueQueryBookService.java](YuqueQueryBookService.md) | file | YuqueQueryBookService使用WebClient进行GET请求，查询并返回书籍信息。 |
| [YuqueAutoConfiguration.java](YuqueAutoConfiguration.md) | file | 基于配置启用Yuque API，自动配置文档查询服务。 |
| [YuqueQueryDocService.java](YuqueQueryDocService.md) | file | YuqueQueryDocService实现Function接口，使用WebClient发送POST请求查询文档信息。 |
| [YuqueUpdateDocService.java](YuqueUpdateDocService.md) | file | YuqueUpdateDocService类通过WebClient发送PUT请求实现文档更新并返回响应。 |


