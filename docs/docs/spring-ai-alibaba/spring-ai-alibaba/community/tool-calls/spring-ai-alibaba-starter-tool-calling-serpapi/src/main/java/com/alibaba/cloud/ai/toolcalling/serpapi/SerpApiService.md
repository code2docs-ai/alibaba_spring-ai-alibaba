# 基础信息

|      |      |
|------|------|
| 名称 | SerpApiService |
| 编码语言 | .java |
| 代码路径 | spring-ai-alibaba/community/tool-calls/spring-ai-alibaba-starter-tool-calling-serpapi/src/main/java/com/alibaba/cloud/ai/toolcalling/serpapi/SerpApiService.java |
| 包名 | com.alibaba.cloud.ai.toolcalling.serpapi |
| 依赖项 | ['com.fasterxml.jackson.annotation.JsonClassDescription', 'com.fasterxml.jackson.annotation.JsonInclude', 'com.fasterxml.jackson.annotation.JsonProperty', 'com.fasterxml.jackson.annotation.JsonPropertyDescription', 'com.google.gson.Gson', 'com.google.gson.JsonArray', 'com.google.gson.JsonElement', 'com.google.gson.JsonObject', 'org.jsoup.Jsoup', 'org.jsoup.nodes.Document', 'org.slf4j.Logger', 'org.slf4j.LoggerFactory', 'org.springframework.http.HttpHeaders', 'org.springframework.http.HttpMethod', 'org.springframework.util.StringUtils', 'org.springframework.web.reactive.function.client.WebClient', 'reactor.core.publisher.Mono', 'java.util.ArrayList', 'java.util.List', 'java.util.function.Function', 'com.alibaba.cloud.ai.toolcalling.serpapi.SerpApiProperties.SERP_API_URL', 'com.alibaba.cloud.ai.toolcalling.serpapi.SerpApiProperties.USER_AGENT_VALUE'] |
| 概述说明 | SerpApiService通过API实现搜索功能，解析并返回结果数据。 |

# 说明

SerpApiService实现了一个搜索功能，该功能通过调用API获取搜索结果，并对这些结果进行解析处理，最终返回响应数据。这一过程确保了搜索功能的完整性和数据的准确性，为用户提供了可靠的搜索结果。

# 类列表 Class Summary

| 名称   | 类型  | 说明 |
|-------|------|-------------|
| SerpApiService | class | SerpApiService实现搜索功能，通过API获取并解析搜索结果，返回响应数据。 |



## 类 SerpApiService

|      |      |
|------|------|
| 访问范围 | public |
| 类型 | class |
| 名称 | SerpApiService |
| 说明 | SerpApiService实现搜索功能，通过API获取并解析搜索结果，返回响应数据。 |


### UML类图

```mermaid
classDiagram
    class SerpApiService {
        -Logger logger
        -WebClient webClient
        -String apikey
        -String engine
        -static final int MEMORY_SIZE
        -static final int BYTE_SIZE
        -static final int MAX_MEMORY_SIZE
        +SerpApiService(SerpApiProperties properties)
        +Response apply(Request request)
        -List~SearchResult~ parseJson(String jsonResponse)
    }

    class SerpApiProperties {
        +String getApikey()
        +String getEngine()
    }

    class Request {
        <<Record>>
        +String query
    }

    class Response {
        <<Record>>
        +List~SearchResult~ results
    }

    class SearchResult {
        <<Record>>
        +String title
        +String text
    }

    SerpApiService --> SerpApiProperties : 依赖
    SerpApiService --> Request : 处理
    SerpApiService --> Response : 返回
    Response --> SearchResult : 包含
```

**描述：**  
`SerpApiService` 是一个实现 `Function` 接口的类，用于通过 SerpAPI 进行搜索。它依赖于 `SerpApiProperties` 来获取 API 密钥和搜索引擎类型。`SerpApiService` 接收 `Request` 对象作为输入，处理后返回 `Response` 对象，其中包含多个 `SearchResult`。`Request` 和 `Response` 是记录类，分别表示搜索请求和响应。`SearchResult` 记录类包含搜索结果的标题和文本内容。


### 内部方法调用关系图

```mermaid
graph TD
    A["类SerpApiService"]
    B["属性: Logger logger"]
    C["属性: WebClient webClient"]
    D["属性: String apikey"]
    E["属性: String engine"]
    F["常量: int MEMORY_SIZE"]
    G["常量: int BYTE_SIZE"]
    H["常量: int MAX_MEMORY_SIZE"]
    I["构造方法: SerpApiService(SerpApiProperties properties)"]
    J["方法: Response apply(Request request)"]
    K["方法: List<SearchResult> parseJson(String jsonResponse)"]
    L["内部类: Request"]
    M["内部类: Response"]
    N["内部类: SearchResult"]

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

    I --> C
    I --> D
    I --> E

    J --> K
    K --> N
```

```mermaid
sequenceDiagram
    participant A as SerpApiService
    participant B as WebClient
    participant C as Logger
    participant D as Gson
    participant E as Jsoup

    A->>A: apply(Request request)
    alt request == null or request.query is empty
        A-->>A: return null
    else
        A->>B: webClient.method(HttpMethod.GET)
        B->>B: uriBuilder.queryParam('api_key', apikey).queryParam('engine', engine).queryParam('q', request.query).build()
        B->>B: retrieve()
        B->>B: bodyToMono(String.class)
        B-->>A: responseMono
        A->>A: responseMono.block()
        A->>C: logger.info('serpapi search: {},result:{}', request.query, response)
        A->>A: parseJson(response)
        A->>D: gson.fromJson(jsonResponse, JsonObject.class)
        D-->>A: JsonObject object
        A->>A: object.getAsJsonArray('organic_results')
        loop for each JsonElement in jsonArray
            A->>A: jsonElement.getAsJsonObject()
            A->>A: resultObject.get('title').getAsString()
            A->>A: resultObject.get('link').getAsString()
            A->>E: Jsoup.connect(link).userAgent(USER_AGENT_VALUE).get()
            E-->>A: Document document
            A->>A: document.body().text()
            A->>A: resultList.add(new SearchResult(title, textContent))
        end
        A-->>A: return new Response(resultList)
    end
```

**流程图描述：**  
该流程图展示了`SerpApiService`类的结构和主要方法调用关系。类中包含多个属性和常量，构造方法用于初始化`webClient`、`apikey`和`engine`。`apply`方法处理搜索请求，调用`parseJson`方法解析JSON响应，并通过`Jsoup`获取网页内容。内部类`Request`、`Response`和`SearchResult`分别用于封装请求、响应和搜索结果。

### 字段列表 Field List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| engine | String | 定义了一个私有且不可变的字符串类型变量engine。 |
| webClient | WebClient | 定义了一个私有且不可变的WebClient实例。 |
| MEMORY_SIZE = 5 | int | 定义常量MEMORY_SIZE，值为5。 |
| logger = LoggerFactory.getLogger(SerpApiService.class) | Logger | SerpApiService类中定义了一个私有的静态日志记录器。 |
| apikey | String | 私有且不可变的字符串变量apikey。 |
| MAX_MEMORY_SIZE = MEMORY_SIZE * BYTE_SIZE * BYTE_SIZE | int | 定义了最大内存大小，基于内存大小和字节大小的乘积。 |
| BYTE_SIZE = 1024 | int | 定义常量BYTE_SIZE，值为1024。 |

### 方法列表 Method List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| parseJson | List<SearchResult> | 解析JSON响应，提取搜索结果并获取网页内容。 |
| apply | Response | 处理请求，调用API获取搜索结果，解析并返回响应，异常时记录错误。 |




