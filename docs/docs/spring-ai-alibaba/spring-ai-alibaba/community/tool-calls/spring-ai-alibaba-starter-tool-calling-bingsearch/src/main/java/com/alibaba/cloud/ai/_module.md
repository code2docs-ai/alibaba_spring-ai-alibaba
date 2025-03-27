# 基础信息

|      |      |
|------|------|
| 名称 | ai |
| 编码语言 | .java |
| 代码路径 | spring-ai-alibaba/community/tool-calls/spring-ai-alibaba-starter-tool-calling-bingsearch/src/main/java/com/alibaba/cloud/ai |
| 包名 | spring-ai-alibaba.community.tool-calls.spring-ai-alibaba-starter-tool-calling-bingsearch.src.main.java.com.alibaba.cloud.ai |
| 概述说明 | BingSearchProperties类配置Bing搜索token属性，确保搜索请求正确执行。BingSearchAutoConfiguration类自动注册并动态启用Bing搜索服务。BingSearchService通过Bing API执行查询，返回搜索结果。 |

# 说明

## 概述
该代码模块主要用于集成和管理Bing搜索功能，提供了从配置到实际搜索操作的完整解决方案。模块通过`BingSearchProperties`类管理Bing搜索的token属性，确保搜索请求的认证和授权信息正确设置。`BingSearchAutoConfiguration`类实现了Bing搜索服务的自动注册和条件判断，确保在满足特定条件时自动启用搜索功能。`BingSearchService`类则负责实际调用Bing API执行搜索操作，并返回相应的搜索结果。该模块的设计旨在简化Bing搜索的集成过程，提供灵活的配置选项，并确保搜索功能的安全性和有效性。

## 主要业务场景
1. **Bing搜索配置管理**：通过`BingSearchProperties`类，用户可以定义和调整Bing搜索的token获取、验证及使用方式，确保搜索请求的安全性和有效性。
2. **Bing搜索服务自动注册**：`BingSearchAutoConfiguration`类根据预设条件动态控制Bing搜索服务的激活状态，确保在满足特定条件时自动启用搜索功能，提升系统的灵活性和智能化水平。
3. **Bing搜索功能实现**：`BingSearchService`类通过调用Bing API执行查询操作，为用户提供准确和相关的搜索结果，满足各种信息检索需求。


### 包内部结构视图

```mermaid
graph TD
    ai --> toolcalling
    toolcalling --> bingsearch
    bingsearch --> BingSearchProperties.java
    bingsearch --> BingSearchAutoConfiguration.java
    bingsearch --> BingSearchService.java
```

该流程图展示了spring-ai-alibaba项目中Bing搜索工具调用的层级结构。从`ai`目录开始，依次进入`toolcalling`和`bingsearch`子目录，最终展示了`bingsearch`目录下的三个Java文件：`BingSearchProperties.java`、`BingSearchAutoConfiguration.java`和`BingSearchService.java`。

# 文件列表 File List

| 名称   | 类型  | 说明 |
|-------|------|-------------|
| [toolcalling](toolcalling/_module.md) | package | BingSearchProperties类配置Bing搜索token属性，确保搜索请求正确执行。BingSearchAutoConfiguration类自动注册并动态启用Bing搜索服务。BingSearchService通过Bing API执行查询，返回搜索结果。 |


