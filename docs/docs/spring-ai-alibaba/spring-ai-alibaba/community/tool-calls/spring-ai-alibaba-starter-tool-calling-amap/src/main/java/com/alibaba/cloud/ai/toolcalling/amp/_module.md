# 基础信息

|      |      |
|------|------|
| 名称 | amp |
| 编码语言 | .java |
| 代码路径 | spring-ai-alibaba/community/tool-calls/spring-ai-alibaba-starter-tool-calling-amap/src/main/java/com/alibaba/cloud/ai/toolcalling/amp |
| 包名 | spring-ai-alibaba.community.tool-calls.spring-ai-alibaba-starter-tool-calling-amap.src.main.java.com.alibaba.cloud.ai.toolcalling.amp |
| 概述说明 | AmapProperties类管理高德地图API密钥，WeatherSearchService提供基于地址的天气查询，WeatherTools获取城市编码和天气信息，AmapAutoConfiguration自动加载天气搜索服务。 |

# 说明

## 概述
该代码模块主要用于集成高德地图API，提供基于地理位置的天气查询服务。模块通过管理高德地图API密钥、获取城市编码和天气信息等功能，实现了从地址解析到天气数据获取的自动化流程。模块的设计旨在简化与高德地图API的交互，确保服务的便捷性、准确性和高效性。

## 主要业务场景
1. **API密钥管理**：通过`AmapProperties`类，用户可以配置和管理高德地图API密钥，确保应用程序能够正确调用高德地图的API接口。该类的设计支持灵活更新和修改密钥，保障了密钥管理的便捷性和安全性。
2. **天气查询服务**：`WeatherSearchService`服务通过输入地址信息，自动获取该地址对应的城市编码，并查询该城市的天气情况。该服务为用户提供了基于地理位置的详细天气信息，确保查询结果的准确性和相关性。
3. **工具类支持**：`WeatherTools`类提供了获取城市编码和天气信息的工具方法。通过配置高德地图API密钥，用户可以便捷地访问高德地图的相关服务，简化了与API的交互过程。
4. **自动配置**：`AmapAutoConfiguration`类在系统初始化时，根据条件自动加载与高德地图相关的天气搜索服务。这种设计提高了系统的灵活性和效率，确保服务在需要时可用，同时避免了不必要的资源消耗。


### 包内部结构视图

```mermaid
graph TD
    amp --> AmapProperties.java
    amp --> WeatherSearchService.java
    amp --> WeatherTools.java
    amp --> AmapAutoConfiguration.java
```

该流程图展示了路径2中的层级关系。所有文件都位于`amp`目录下，包括`AmapProperties.java`、`WeatherSearchService.java`、`WeatherTools.java`和`AmapAutoConfiguration.java`。这些文件都是`amp`目录的直接子节点，没有进一步的嵌套层级。

# 文件列表 File List

| 名称   | 类型  | 说明 |
|-------|------|-------------|
| [AmapAutoConfiguration.java](AmapAutoConfiguration.md) | file | 配置类启用Amap属性，条件加载天气搜索服务。 |
| [WeatherSearchService.java](WeatherSearchService.md) | file | WeatherSearchService根据地址获取城市编码并查询天气。 |
| [WeatherTools.java](WeatherTools.md) | file | WeatherTools类通过高德地图API获取城市编码和天气信息，需配置API密钥。 |
| [AmapProperties.java](AmapProperties.md) | file | AmapProperties类配置高德地图API密钥，支持获取和设置操作。 |


