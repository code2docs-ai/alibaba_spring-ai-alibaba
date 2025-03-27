# 基础信息

|      |      |
|------|------|
| 名称 | multi |
| 编码语言 | .java |
| 代码路径 | spring-ai-alibaba/community/document-parsers/spring-ai-alibaba-starter-document-parser-multi-modality/src/main/java/com/alibaba/cloud/ai/parser/multi |
| 包名 | spring-ai-alibaba.community.document-parsers.spring-ai-alibaba-starter-document-parser-multi-modality.src.main.java.com.alibaba.cloud.ai.parser.multi |
| 概述说明 | ImageDashScopeParser类解析图像文本，兼容多系统路径处理。SttDashScopeParser类转换音频为文本，集成API密钥高效识别。 |

# 说明

## 概述

该代码模块是一个多模态文档解析工具集，主要提供图像和音频文件的文本解析功能。模块通过集成先进的API技术，实现了高效的图像文字识别和音频转文本功能。模块中的类设计兼容多种操作系统环境，确保路径处理的灵活性，同时支持通过API密钥访问特定的模型，以满足不同应用场景的需求。

## 主要业务场景

1. **图像文字识别**：通过`ImageDashScopeParser`类，用户可以解析图像文件中的文本内容。该类支持在不同操作系统上处理路径，并通过调用多模态API实现高效的图像文字识别与提取。适用于需要从图像中提取文字的应用场景，如文档扫描、图像中的文字识别等。

2. **音频转文本**：通过`SttDashScopeParser`类，用户可以将音频文件转换为可读的文本。该类通过使用API密钥和特定模型，高效准确地将音频数据转换为文本。适用于需要将语音转换为文字的应用场景，如语音转录、语音助手等。

这两个类共同构成了一个强大的多模态文档解析工具集，能够处理多种类型的文件，并从中提取有用的文本信息。


### 包内部结构视图

```mermaid
graph TD
    multi --> ImageDashScopeParser.java
    multi --> SttDashScopeParser.java
```

该流程图展示了 `spring-ai-alibaba` 项目中 `multi` 目录下的文件结构。`multi` 目录包含两个文件：`ImageDashScopeParser.java` 和 `SttDashScopeParser.java`，这两个文件分别用于处理多模态文档解析的不同功能模块。

# 文件列表 File List

| 名称   | 类型  | 说明 |
|-------|------|-------------|
| [SttDashScopeParser.java](SttDashScopeParser.md) | file | SttDashScopeParser类解析音频文件，利用API密钥和模型生成文本。 |
| [ImageDashScopeParser.java](ImageDashScopeParser.md) | file | ImageDashScopeParser类解析图像文本，支持多系统路径，调用多模态API提取文字。 |


