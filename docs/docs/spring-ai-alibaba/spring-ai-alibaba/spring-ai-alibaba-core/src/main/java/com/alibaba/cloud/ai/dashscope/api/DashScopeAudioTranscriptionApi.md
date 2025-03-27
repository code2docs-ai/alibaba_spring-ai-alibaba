# 基础信息

|      |      |
|------|------|
| 名称 | DashScopeAudioTranscriptionApi |
| 编码语言 | .java |
| 代码路径 | spring-ai-alibaba/spring-ai-alibaba-core/src/main/java/com/alibaba/cloud/ai/dashscope/api/DashScopeAudioTranscriptionApi.java |
| 包名 | com.alibaba.cloud.ai.dashscope.api |
| 依赖项 | ['com.alibaba.cloud.ai.dashscope.audio.DashScopeAudioTranscriptionOptions', 'com.alibaba.cloud.ai.dashscope.common.DashScopeApiConstants', 'com.alibaba.cloud.ai.dashscope.common.DashScopeException', 'com.alibaba.cloud.ai.dashscope.protocol.DashScopeWebSocketClient', 'com.alibaba.cloud.ai.dashscope.protocol.DashScopeWebSocketClientOptions', 'com.fasterxml.jackson.annotation.JsonInclude', 'com.fasterxml.jackson.annotation.JsonProperty', 'com.fasterxml.jackson.core.JsonProcessingException', 'com.fasterxml.jackson.databind.ObjectMapper', 'org.slf4j.Logger', 'org.slf4j.LoggerFactory', 'org.springframework.ai.retry.RetryUtils', 'org.springframework.http.ResponseEntity', 'org.springframework.web.client.ResponseErrorHandler', 'org.springframework.web.client.RestClient', 'reactor.core.publisher.Flux', 'java.io.InputStream', 'java.nio.ByteBuffer', 'java.util.List', 'java.net.URL', 'com.alibaba.cloud.ai.dashscope.common.DashScopeApiConstants.DEFAULT_BASE_URL'] |
| 概述说明 | DashScope音频转写API支持REST和WebSocket调用，具备实时控制和流处理功能。 |

# 说明

DashScope音频转写API类提供了REST和WebSocket两种调用方式，具备实时控制和流处理功能，适用于多种音频转写场景。

# 类列表 Class Summary

| 名称   | 类型  | 说明 |
|-------|------|-------------|
| DashScopeAudioTranscriptionApi | class | DashScope音频转写API类，支持REST和WebSocket调用，包含实时控制和流处理功能。 |



## 类 DashScopeAudioTranscriptionApi

|      |      |
|------|------|
| 访问范围 | public |
| 类型 | class |
| 名称 | DashScopeAudioTranscriptionApi |
| 说明 | DashScope音频转写API类，支持REST和WebSocket调用，包含实时控制和流处理功能。 |


### UML类图

```mermaid
classDiagram
    class DashScopeAudioTranscriptionApi {
        -Logger logger
        -RestClient restClient
        -DashScopeWebSocketClient webSocketClient
        +DashScopeAudioTranscriptionApi(String apiKey)
        +DashScopeAudioTranscriptionApi(String apiKey, String workSpaceId)
        +DashScopeAudioTranscriptionApi(String apiKey, String workSpaceId, String websocketUrl)
        +DashScopeAudioTranscriptionApi(String baseUrl, String apiKey, String workSpaceId, String websocketUrl)
        +DashScopeAudioTranscriptionApi(String baseUrl, String apiKey, String websocketUrl, RestClient.Builder restClientBuilder, ResponseErrorHandler responseErrorHandler)
        +DashScopeAudioTranscriptionApi(String baseUrl, String apiKey, String workSpaceId, String websocketUrl, RestClient.Builder restClientBuilder, ResponseErrorHandler responseErrorHandler)
        +ResponseEntity~Response~ call(Request request)
        +ResponseEntity~Response~ callWithTaskId(Request request, String taskId)
        +void realtimeControl(RealtimeRequest request)
        +Flux~RealtimeResponse~ realtimeStream(Flux~ByteBuffer~ audio)
        +Outcome getOutcome(String transcriptionUrl)
    }

    class Request {
        <<Record>>
        +String model
        +Input input
        +Parameters parameters
    }

    class Input {
        <<Record>>
        +List~String~ fileUrls
    }

    class Parameters {
        <<Record>>
        +List~Integer~ channelId
        +String vocabularyId
        +String phraseId
        +Boolean disfluencyRemovalEnabled
        +List~String~ languageHints
    }

    class Response {
        <<Record>>
        +Integer statusCode
        +String requestId
        +String code
        +String message
        +Usage usage
        +Output output
    }

    class Usage {
        <<Record>>
        +Double duration
    }

    class Output {
        <<Record>>
        +String taskId
        +TaskStatus taskStatus
        +String submitTime
        +String scheduledTime
        +String endTime
        +List~Result~ results
        +TaskMetrics taskMetrics
    }

    class Result {
        <<Record>>
        +String fileUrl
        +String transcriptionUrl
        +String subtaskStatus
    }

    class TaskMetrics {
        <<Record>>
        +Integer total
        +Integer succeeded
        +Integer failed
    }

    class Outcome {
        <<Record>>
        +String fileUrl
        +Properties properties
        +List~Transcript~ transcripts
    }

    class Properties {
        <<Record>>
        +String audioFormat
        +List~Integer~ channels
        +Integer originalSamplingRate
        +Integer originalDurationInMilliseconds
    }

    class Transcript {
        <<Record>>
        +Integer channelId
        +Integer contentDurationInMilliseconds
        +String text
        +List~Sentence~ sentences
    }

    class Sentence {
        <<Record>>
        +Integer beginTime
        +Integer endTime
        +String text
        +List~Word~ words
    }

    class Word {
        <<Record>>
        +Integer beginTime
        +Integer endTime
        +String text
        +String punctuation
    }

    class RealtimeRequest {
        <<Record>>
        +Header header
        +Payload payload
    }

    class Header {
        <<Record>>
        +DashScopeWebSocketClient.EventType action
        +String taskId
        +String streaming
    }

    class Payload {
        <<Record>>
        +String model
        +String taskGroup
        +String task
        +String function
        +Input input
        +Parameters parameters
    }

    class RealtimeResponse {
        <<Record>>
        +Header header
        +Payload payload
    }

    class Header {
        <<Record>>
        +String taskId
        +DashScopeWebSocketClient.EventType event
        +Attributes attributes
    }

    class Attributes {
        <<Record>>
    }

    class Payload {
        <<Record>>
        +Output output
        +Usage usage
    }

    class Output {
        <<Record>>
        +Sentence sentence
    }

    class Sentence {
        <<Record>>
        +String sentenceId
        +Integer beginTime
        +Integer endTime
        +String text
        +Integer channelId
        +String speakerId
        +Boolean sentenceEnd
        +List~Word~ words
        +Stash stash
    }

    class Word {
        <<Record>>
        +Integer beginTime
        +Integer endTime
        +String text
        +String punctuation
        +Boolean fixed
        +String speakerId
    }

    class Stash {
        <<Record>>
        +String sentenceId
        +String text
        +Integer beginTime
        +Integer currentTime
        +List~Word~ words
    }

    class Usage {
        <<Record>>
        +Double duration
    }

    class TaskStatus {
        <<Enum>>
        +String status
        +String getValue()
    }

    DashScopeAudioTranscriptionApi --> Request : 使用
    DashScopeAudioTranscriptionApi --> Response : 使用
    DashScopeAudioTranscriptionApi --> RealtimeRequest : 使用
    DashScopeAudioTranscriptionApi --> RealtimeResponse : 使用
    DashScopeAudioTranscriptionApi --> Outcome : 使用
    Request --> Input : 包含
    Request --> Parameters : 包含
    Response --> Usage : 包含
    Response --> Output : 包含
    Output --> Result : 包含
    Output --> TaskMetrics : 包含
    Outcome --> Properties : 包含
    Outcome --> Transcript : 包含
    Transcript --> Sentence : 包含
    Sentence --> Word : 包含
    RealtimeRequest --> Header : 包含
    RealtimeRequest --> Payload : 包含
    Payload --> Input : 包含
    Payload --> Parameters : 包含
    RealtimeResponse --> Header : 包含
    RealtimeResponse --> Payload : 包含
    Payload --> Output : 包含
    Payload --> Usage : 包含
    Output --> Sentence : 包含
    Sentence --> Word : 包含
    Sentence --> Stash : 包含
```

### 描述
`DashScopeAudioTranscriptionApi` 类是一个用于处理音频转录的API类，它通过REST客户端和WebSocket客户端与后端服务进行交互。该类提供了多种构造函数以适应不同的配置需求，并包含了多个内部记录类（Record）用于表示请求、响应、实时请求和响应等数据结构。这些记录类之间通过嵌套关系组织，形成了一个复杂的数据模型，用于处理音频转录的各个阶段和结果。


### 内部方法调用关系图

```mermaid
graph TD
    A["类DashScopeAudioTranscriptionApi"]
    B["属性: Logger logger"]
    C["属性: RestClient restClient"]
    D["属性: DashScopeWebSocketClient webSocketClient"]
    E["构造方法: DashScopeAudioTranscriptionApi(String apiKey)"]
    F["构造方法: DashScopeAudioTranscriptionApi(String apiKey, String workSpaceId)"]
    G["构造方法: DashScopeAudioTranscriptionApi(String apiKey, String workSpaceId, String websocketUrl)"]
    H["构造方法: DashScopeAudioTranscriptionApi(String baseUrl, String apiKey, String workSpaceId, String websocketUrl)"]
    I["构造方法: DashScopeAudioTranscriptionApi(String baseUrl, String apiKey, String websocketUrl, RestClient.Builder restClientBuilder, ResponseErrorHandler responseErrorHandler)"]
    J["构造方法: DashScopeAudioTranscriptionApi(String baseUrl, String apiKey, String workSpaceId, String websocketUrl, RestClient.Builder restClientBuilder, ResponseErrorHandler responseErrorHandler)"]
    K["方法: ResponseEntity<Response> call(DashScopeAudioTranscriptionApi.Request request)"]
    L["方法: ResponseEntity<Response> callWithTaskId(DashScopeAudioTranscriptionApi.Request request, String taskId)"]
    M["方法: void realtimeControl(DashScopeAudioTranscriptionApi.RealtimeRequest request)"]
    N["方法: Flux<RealtimeResponse> realtimeStream(Flux<ByteBuffer> audio)"]
    O["方法: Outcome getOutcome(String transcriptionUrl)"]
    P["内部类: Request"]
    Q["内部类: Response"]
    R["内部类: Outcome"]
    S["内部类: RealtimeRequest"]
    T["内部类: RealtimeResponse"]
    U["枚举: TaskStatus"]

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
    A --> R
    A --> S
    A --> T
    A --> U
```

这段代码定义了一个名为`DashScopeAudioTranscriptionApi`的类，用于处理音频转录相关的API调用。类中包含多个构造方法，用于初始化`RestClient`和`DashScopeWebSocketClient`对象，并提供了多个方法用于发送请求、处理实时控制和流式传输音频数据。此外，类中还定义了多个内部类和枚举，用于封装请求、响应和任务状态等信息。代码结构清晰，功能模块化，便于扩展和维护。

### 字段列表 Field List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| restClient | RestClient | 私有且不可变的RestClient实例。 |
| webSocketClient | DashScopeWebSocketClient | 私有且不可变的DashScopeWebSocketClient实例。 |
| logger = LoggerFactory.getLogger(DashScopeAudioTranscriptionApi.class) | Logger | DashScopeAudioTranscriptionApi类中定义了一个私有的静态日志记录器。 |

### 方法列表 Method List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| callWithTaskId | ResponseEntity<Response> | 调用任务ID的音频转录API，返回响应实体。 |
| realtimeControl | void | 实时控制方法通过WebSocket发送JSON格式请求，处理异常时抛出运行时错误。 |
| realtimeStream | Flux<RealtimeResponse> | 实时流处理音频数据，返回响应并处理JSON异常。 |
| call | ResponseEntity<Response> | 调用DashScope音频转录API，发送POST请求并返回响应实体。 |
| getOutcome | Outcome | 通过URL获取转录结果并返回Outcome对象，失败时抛出异常。 |




