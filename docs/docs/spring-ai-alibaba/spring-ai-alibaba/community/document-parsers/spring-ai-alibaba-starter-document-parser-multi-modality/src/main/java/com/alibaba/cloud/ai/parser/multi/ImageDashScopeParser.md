# 基础信息

|      |      |
|------|------|
| 名称 | ImageDashScopeParser |
| 编码语言 | .java |
| 代码路径 | spring-ai-alibaba/community/document-parsers/spring-ai-alibaba-starter-document-parser-multi-modality/src/main/java/com/alibaba/cloud/ai/parser/multi/ImageDashScopeParser.java |
| 包名 | com.alibaba.cloud.ai.parser.multi |
| 依赖项 | ['java.io.InputStream', 'java.util.Arrays', 'java.util.Collections', 'java.util.List', 'java.util.Map', 'java.util.HashMap', 'com.alibaba.cloud.ai.document.DocumentParser', 'com.alibaba.dashscope.aigc.multimodalconversation.MultiModalConversation', 'com.alibaba.dashscope.aigc.multimodalconversation.MultiModalConversationParam', 'com.alibaba.dashscope.aigc.multimodalconversation.MultiModalConversationResult', 'com.alibaba.dashscope.common.MultiModalMessage', 'com.alibaba.dashscope.common.Role', 'com.alibaba.dashscope.exception.ApiException', 'com.alibaba.dashscope.exception.NoApiKeyException', 'com.alibaba.dashscope.exception.UploadFileException', 'org.springframework.ai.document.Document'] |
| 概述说明 | ImageDashScopeParser类解析图像文本，支持多系统路径，调用多模态API提取文字。 |

# 说明

ImageDashScopeParser类是一个用于解析图像文本的工具，支持在不同操作系统上处理路径，并通过调用多模态API来提取图像中的文字内容。该类的设计旨在兼容多种操作系统环境，确保路径处理的灵活性，同时利用先进的API技术实现高效的图像文字识别与提取功能。

# 类列表 Class Summary

| 名称   | 类型  | 说明 |
|-------|------|-------------|
| ImageDashScopeParser | class | ImageDashScopeParser类用于解析图像文本，支持不同操作系统路径处理，调用多模态API提取图像文字。 |



## 类 ImageDashScopeParser

|      |      |
|------|------|
| 访问范围 | public |
| 类型 | class |
| 名称 | ImageDashScopeParser |
| 说明 | ImageDashScopeParser类用于解析图像文本，支持不同操作系统路径处理，调用多模态API提取图像文字。 |


### UML类图

```mermaid
classDiagram
    class ImageDashScopeParser {
        -String OS
        -String model
        -String maxPixels
        -String minPixels
        -String apiKey
        +ImageDashScopeParser(String apiKey)
        +ImageDashScopeParser(String apiKey, String model)
        +ImageDashScopeParser(String apiKey, String model, String maxPixels, String minPixels)
        +List~Document~ parse(String path)
        +List~Document~ parse(InputStream inputStream)
    }

    class Document {
        // Document类表示解析后的文档
    }

    class MultiModalConversation {
        +MultiModalConversationResult call(MultiModalConversationParam param)
    }

    class MultiModalConversationParam {
        +String apiKey
        +String model
        +MultiModalMessage message
        +MultiModalConversationParam builder()
    }

    class MultiModalMessage {
        +String role
        +List~Object~ content
        +MultiModalMessage builder()
    }

    class MultiModalConversationResult {
        +Output getOutput()
    }

    class Output {
        +List~Choice~ getChoices()
    }

    class Choice {
        +Message getMessage()
    }

    class Message {
        +Map~String, Object~ getContent()
    }

    class ApiException {
        // 表示API调用异常
    }

    class NoApiKeyException {
        // 表示缺少API密钥异常
    }

    class UploadFileException {
        // 表示文件上传异常
    }

    ImageDashScopeParser --> Document : 生成
    ImageDashScopeParser --> MultiModalConversation : 依赖
    MultiModalConversation --> MultiModalConversationParam : 依赖
    MultiModalConversationParam --> MultiModalMessage : 依赖
    MultiModalConversation --> MultiModalConversationResult : 依赖
    MultiModalConversationResult --> Output : 依赖
    Output --> Choice : 依赖
    Choice --> Message : 依赖
    ImageDashScopeParser --> ApiException : 捕获
    ImageDashScopeParser --> NoApiKeyException : 捕获
    ImageDashScopeParser --> UploadFileException : 捕获
```

**描述：**  
`ImageDashScopeParser` 类用于解析图像文档，通过调用多模态对话API来提取图像中的文本。它依赖于 `MultiModalConversation` 类来处理API请求，并生成 `Document` 对象。该类还处理了多种异常情况，如 `ApiException`、`NoApiKeyException` 和 `UploadFileException`，以确保代码的健壮性。


### 内部方法调用关系图

```mermaid
graph TD
    A["类ImageDashScopeParser"]
    B["属性: String OS"]
    C["属性: String model"]
    D["属性: String maxPixels"]
    E["属性: String minPixels"]
    F["属性: String apiKey"]
    G["构造方法: ImageDashScopeParser(String apiKey)"]
    H["构造方法: ImageDashScopeParser(String apiKey, String model)"]
    I["构造方法: ImageDashScopeParser(String apiKey, String model, String maxPixels, String minPixels)"]
    J["方法: List<Document> parse(String path)"]
    K["方法: List<Document> parse(InputStream inputStream)"]
    L["创建MultiModalConversation对象"]
    M["判断path是否以'http'开头"]
    N["判断操作系统是否为Windows"]
    O["判断操作系统是否为Unix/Linux/Mac"]
    P["构建filePath"]
    Q["创建Map对象并放入image, max_pixels, min_pixels"]
    R["构建MultiModalMessage对象"]
    S["构建MultiModalConversationParam对象"]
    T["调用conversation.call(param)"]
    U["返回Document对象"]
    V["捕获异常并抛出RuntimeException"]

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
    J --> L
    J --> M
    M -->|是| P
    M -->|否| N
    N -->|是| P
    N -->|否| O
    O -->|是| P
    J --> Q
    J --> R
    J --> S
    J --> T
    J --> U
    J --> V
```

**描述：**  
`ImageDashScopeParser`类用于解析图像文档，通过构造方法初始化API密钥、模型名称、最大像素和最小像素等属性。`parse(String path)`方法根据路径判断是否为HTTP链接或本地文件，并构建相应的文件路径。然后，通过`MultiModalConversation`对象进行图像文本的识别，最终返回解析后的文档内容。若在解析过程中出现异常，将抛出`RuntimeException`。

### 字段列表 Field List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| OS = System.getProperty("os.name").toLowerCase() | String | 获取系统名称并转换为小写存储。 |
| minPixels | String | 私有字符串变量minPixels的声明。 |
| model | String | 定义了一个私有的不可变字符串变量model。 |
| apiKey | String | 声明一个私有的不可变字符串变量apiKey。 |
| maxPixels | String | 私有字符串变量maxPixels |

### 方法列表 Method List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| parse | List<Document> | 解析路径生成多模态对话，返回图像文本内容。 |
| parse | List<Document> | 重写parse方法，返回空文档列表。 |




