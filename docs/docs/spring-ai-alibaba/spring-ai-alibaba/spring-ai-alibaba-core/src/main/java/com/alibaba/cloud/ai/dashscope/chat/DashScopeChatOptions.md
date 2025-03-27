# 基础信息

|      |      |
|------|------|
| 名称 | DashScopeChatOptions |
| 编码语言 | .java |
| 代码路径 | spring-ai-alibaba/spring-ai-alibaba-core/src/main/java/com/alibaba/cloud/ai/dashscope/chat/DashScopeChatOptions.java |
| 包名 | com.alibaba.cloud.ai.dashscope.chat |
| 依赖项 | ['java.util', 'com.alibaba.cloud.ai.dashscope.api.DashScopeApi', 'com.alibaba.cloud.ai.dashscope.api.DashScopeResponseFormat', 'com.fasterxml.jackson.annotation.JsonIgnore', 'com.fasterxml.jackson.annotation.JsonInclude', 'com.fasterxml.jackson.annotation.JsonProperty', 'org.springframework.ai.chat.prompt.ChatOptions', 'org.springframework.ai.model.ModelOptionsUtils', 'org.springframework.ai.model.function.FunctionCallback', 'org.springframework.ai.model.function.FunctionCallingOptions', 'org.springframework.util.Assert'] |
| 概述说明 | DashScopeChatOptions类配置聊天模型参数，含模型ID、温度、随机种子等。 |

# 说明

DashScopeChatOptions类用于配置聊天模型的各种参数，主要包括模型ID、温度设置、随机种子、采样阈值、停止条件、互联网搜索功能以及工具调用等。通过这些参数，用户可以精细调整聊天模型的行为和输出，以满足不同的应用场景和需求。

# 类列表 Class Summary

| 名称   | 类型  | 说明 |
|-------|------|-------------|
| DashScopeChatOptions | class | DashScopeChatOptions类用于配置聊天模型参数，包括模型ID、温度、随机种子、采样阈值、停止条件、互联网搜索、工具调用等。 |



## 类 DashScopeChatOptions

|      |      |
|------|------|
| 访问范围 | @JsonInclude(JsonInclude.Include.NON_NULL);public |
| 类型 | class |
| 名称 | DashScopeChatOptions |
| 说明 | DashScopeChatOptions类用于配置聊天模型参数，包括模型ID、温度、随机种子、采样阈值、停止条件、互联网搜索、工具调用等。 |


### UML类图

```mermaid
classDiagram
    class DashScopeChatOptions {
        <<Interface>> FunctionCallingOptions
        <<Interface>> ChatOptions
        -String model
        -Boolean stream
        -Double temperature
        -Integer seed
        -Double topP
        -Integer topK
        -List~Object~ stop
        -Boolean enableSearch
        -DashScopeResponseFormat responseFormat
        -Integer maxTokens
        -Boolean incrementalOutput
        -Double repetitionPenalty
        -List~DashScopeApi.FunctionTool~ tools
        -Object toolChoice
        -Boolean vlHighResolutionImages
        -List~FunctionCallback~ functionCallbacks
        -Set~String~ functions
        -Boolean multiModel
        -Boolean proxyToolCalls
        -Map~String, Object~ toolContext
        +String getModel()
        +Double getFrequencyPenalty()
        +Integer getMaxTokens()
        +Integer setMaxTokens()
        +Double getPresencePenalty()
        +List~String~ getStopSequences()
        +void setModel(String model)
        +Boolean getStream()
        +void setStream(Boolean stream)
        +Double getTemperature()
        +void setTemperature(Double temperature)
        +Double getTopP()
        +ChatOptions copy()
        +void setTopP(Double topP)
        +Integer getTopK()
        +void setTopK(Integer topK)
        +List~Object~ getStop()
        +void setStop(List~Object~ stop)
        +DashScopeResponseFormat getResponseFormat()
        +void setResponseFormat(DashScopeResponseFormat responseFormat)
        +Boolean getEnableSearch()
        +void setEnableSearch(Boolean enableSearch)
        +Double getRepetitionPenalty()
        +void setRepetitionPenalty(Double repetitionPenalty)
        +List~DashScopeApi.FunctionTool~ getTools()
        +void setTools(List~DashScopeApi.FunctionTool~ tools)
        +Object getToolChoice()
        +void setToolChoice(Object toolChoice)
        +Integer getSeed()
        +void setSeed(Integer seed)
        +Boolean getProxyToolCalls()
        +void setProxyToolCalls(Boolean proxyToolCalls)
        +List~FunctionCallback~ getFunctionCallbacks()
        +void setFunctionCallbacks(List~FunctionCallback~ functionCallbacks)
        +Set~String~ getFunctions()
        +void setFunctions(Set~String~ functions)
        +Map~String, Object~ getToolContext()
        +void setToolContext(Map~String, Object~ toolContext)
        +Boolean getIncrementalOutput()
        +void setIncrementalOutput(Boolean incrementalOutput)
        +Boolean getVlHighResolutionImages()
        +void setVlHighResolutionImages(Boolean vlHighResolutionImages)
        +Boolean getMultiModel()
        +void setMultiModel(Boolean multiModel)
        +static DashscopeChatOptionsBuilder builder()
        +static DashScopeChatOptions fromOptions(DashScopeChatOptions fromOptions)
        +boolean equals(Object o)
        +int hashCode()
        +String toString()
    }

    class DashscopeChatOptionsBuilder {
        -DashScopeChatOptions options
        +DashscopeChatOptionsBuilder()
        +DashscopeChatOptionsBuilder withModel(String model)
        +DashscopeChatOptionsBuilder withMaxToken(Integer maxTokens)
        +DashscopeChatOptionsBuilder withTemperature(Double temperature)
        +DashscopeChatOptionsBuilder withTopP(Double topP)
        +DashscopeChatOptionsBuilder withTopK(Integer topK)
        +DashscopeChatOptionsBuilder withStop(List~Object~ stop)
        +DashscopeChatOptionsBuilder withResponseFormat(DashScopeResponseFormat responseFormat)
        +DashscopeChatOptionsBuilder withEnableSearch(Boolean enableSearch)
        +DashscopeChatOptionsBuilder withRepetitionPenalty(Double repetitionPenalty)
        +DashscopeChatOptionsBuilder withTools(List~DashScopeApi.FunctionTool~ tools)
        +DashscopeChatOptionsBuilder withToolChoice(Object toolChoice)
        +DashscopeChatOptionsBuilder withStream(Boolean stream)
        +DashscopeChatOptionsBuilder withFunctionCallbacks(List~FunctionCallback~ functionCallbacks)
        +DashscopeChatOptionsBuilder withFunction(String functionName)
        +DashscopeChatOptionsBuilder withFunctions(Set~String~ functionNames)
        +DashscopeChatOptionsBuilder withProxyToolCalls(Boolean proxyToolCalls)
        +DashscopeChatOptionsBuilder withSeed(Integer seed)
        +DashscopeChatOptionsBuilder withIncrementalOutput(Boolean incrementalOutput)
        +DashscopeChatOptionsBuilder withToolContext(Map~String, Object~ toolContext)
        +DashscopeChatOptionsBuilder withVlHighResolutionImages(Boolean vlHighResolutionImages)
        +DashscopeChatOptionsBuilder withMultiModel(Boolean multiModel)
        +DashScopeChatOptions build()
    }

    DashScopeChatOptions --> DashscopeChatOptionsBuilder : 依赖
```

**描述**：`DashScopeChatOptions` 类实现了 `FunctionCallingOptions` 和 `ChatOptions` 接口，用于配置聊天模型的参数，如模型名称、温度、随机种子、采样策略等。它提供了丰富的属性和方法，允许开发者精细控制模型的行为。`DashscopeChatOptionsBuilder` 是一个构建器类，用于简化 `DashScopeChatOptions` 对象的创建和配置。两者之间存在依赖关系，构建器用于生成 `DashScopeChatOptions` 实例。


### 内部方法调用关系图

```mermaid
graph TD
    A["类DashScopeChatOptions"]
    B["属性: String model"]
    C["属性: Boolean stream"]
    D["属性: Double temperature"]
    E["属性: Integer seed"]
    F["属性: Double topP"]
    G["属性: Integer topK"]
    H["属性: List<Object> stop"]
    I["属性: Boolean enableSearch"]
    J["属性: DashScopeResponseFormat responseFormat"]
    K["属性: Integer maxTokens"]
    L["属性: Boolean incrementalOutput"]
    M["属性: Double repetitionPenalty"]
    N["属性: List<DashScopeApi.FunctionTool> tools"]
    O["属性: Object toolChoice"]
    P["属性: Boolean vlHighResolutionImages"]
    Q["属性: List<FunctionCallback> functionCallbacks"]
    R["属性: Set<String> functions"]
    S["属性: Boolean multiModel"]
    T["属性: Boolean proxyToolCalls"]
    U["属性: Map<String, Object> toolContext"]
    V["方法: String getModel()"]
    W["方法: Double getFrequencyPenalty()"]
    X["方法: Integer getMaxTokens()"]
    Y["方法: Integer setMaxTokens()"]
    Z["方法: Double getPresencePenalty()"]
    AA["方法: List<String> getStopSequences()"]
    AB["方法: void setModel(String model)"]
    AC["方法: Boolean getStream()"]
    AD["方法: void setStream(Boolean stream)"]
    AE["方法: Double getTemperature()"]
    AF["方法: void setTemperature(Double temperature)"]
    AG["方法: Double getTopP()"]
    AH["方法: ChatOptions copy()"]
    AI["方法: void setTopP(Double topP)"]
    AJ["方法: Integer getTopK()"]
    AK["方法: void setTopK(Integer topK)"]
    AL["方法: List<Object> getStop()"]
    AM["方法: void setStop(List<Object> stop)"]
    AN["方法: DashScopeResponseFormat getResponseFormat()"]
    AO["方法: void setResponseFormat(DashScopeResponseFormat responseFormat)"]
    AP["方法: Boolean getEnableSearch()"]
    AQ["方法: void setEnableSearch(Boolean enableSearch)"]
    AR["方法: Double getRepetitionPenalty()"]
    AS["方法: void setRepetitionPenalty(Double repetitionPenalty)"]
    AT["方法: List<DashScopeApi.FunctionTool> getTools()"]
    AU["方法: void setTools(List<DashScopeApi.FunctionTool> tools)"]
    AV["方法: Object getToolChoice()"]
    AW["方法: void setToolChoice(Object toolChoice)"]
    AX["方法: Integer getSeed()"]
    AY["方法: void setSeed(Integer seed)"]
    AZ["方法: Boolean getProxyToolCalls()"]
    BA["方法: void setProxyToolCalls(Boolean proxyToolCalls)"]
    BB["方法: List<FunctionCallback> getFunctionCallbacks()"]
    BC["方法: void setFunctionCallbacks(List<FunctionCallback> functionCallbacks)"]
    BD["方法: Set<String> getFunctions()"]
    BE["方法: void setFunctions(Set<String> functions)"]
    BF["方法: Map<String, Object> getToolContext()"]
    BG["方法: void setToolContext(Map<String, Object> toolContext)"]
    BH["方法: Boolean getIncrementalOutput()"]
    BI["方法: void setIncrementalOutput(Boolean incrementalOutput)"]
    BJ["方法: Boolean getVlHighResolutionImages()"]
    BK["方法: void setVlHighResolutionImages(Boolean vlHighResolutionImages)"]
    BL["方法: Boolean getMultiModel()"]
    BM["方法: void setMultiModel(Boolean multiModel)"]
    BN["方法: static DashscopeChatOptionsBuilder builder()"]
    BO["方法: static DashScopeChatOptions fromOptions(DashScopeChatOptions fromOptions)"]
    BP["方法: boolean equals(Object o)"]
    BQ["方法: int hashCode()"]
    BR["方法: String toString()"]
    BS["内部类: DashscopeChatOptionsBuilder"]
    BT["方法: DashscopeChatOptionsBuilder withModel(String model)"]
    BU["方法: DashscopeChatOptionsBuilder withMaxToken(Integer maxTokens)"]
    BV["方法: DashscopeChatOptionsBuilder withTemperature(Double temperature)"]
    BW["方法: DashscopeChatOptionsBuilder withTopP(Double topP)"]
    BX["方法: DashscopeChatOptionsBuilder withTopK(Integer topK)"]
    BY["方法: DashscopeChatOptionsBuilder withStop(List<Object> stop)"]
    BZ["方法: DashscopeChatOptionsBuilder withResponseFormat(DashScopeResponseFormat responseFormat)"]
    CA["方法: DashscopeChatOptionsBuilder withEnableSearch(Boolean enableSearch)"]
    CB["方法: DashscopeChatOptionsBuilder withRepetitionPenalty(Double repetitionPenalty)"]
    CC["方法: DashscopeChatOptionsBuilder withTools(List<DashScopeApi.FunctionTool> tools)"]
    CD["方法: DashscopeChatOptionsBuilder withToolChoice(Object toolChoice)"]
    CE["方法: DashscopeChatOptionsBuilder withStream(Boolean stream)"]
    CF["方法: DashscopeChatOptionsBuilder withFunctionCallbacks(List<FunctionCallback> functionCallbacks)"]
    CG["方法: DashscopeChatOptionsBuilder withFunction(String functionName)"]
    CH["方法: DashscopeChatOptionsBuilder withFunctions(Set<String> functionNames)"]
    CI["方法: DashscopeChatOptionsBuilder withProxyToolCalls(Boolean proxyToolCalls)"]
    CJ["方法: DashscopeChatOptionsBuilder withSeed(Integer seed)"]
    CK["方法: DashscopeChatOptionsBuilder withIncrementalOutput(Boolean incrementalOutput)"]
    CL["方法: DashscopeChatOptionsBuilder withToolContext(Map<String, Object> toolContext)"]
    CM["方法: DashscopeChatOptionsBuilder withVlHighResolutionImages(Boolean vlHighResolutionImages)"]
    CN["方法: DashscopeChatOptionsBuilder withMultiModel(Boolean multiModel)"]
    CO["方法: DashScopeChatOptions build()"]

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
    A --> V
    A --> W
    A --> X
    A --> Y
    A --> Z
    A --> AA
    A --> AB
    A --> AC
    A --> AD
    A --> AE
    A --> AF
    A --> AG
    A --> AH
    A --> AI
    A --> AJ
    A --> AK
    A --> AL
    A --> AM
    A --> AN
    A --> AO
    A --> AP
    A --> AQ
    A --> AR
    A --> AS
    A --> AT
    A --> AU
    A --> AV
    A --> AW
    A --> AX
    A --> AY
    A --> AZ
    A --> BA
    A --> BB
    A --> BC
    A --> BD
    A --> BE
    A --> BF
    A --> BG
    A --> BH
    A --> BI
    A --> BJ
    A --> BK
    A --> BL
    A --> BM
    A --> BN
    A --> BO
    A --> BP
    A --> BQ
    A --> BR
    A --> BS
    BS --> BT
    BS --> BU
    BS --> BV
    BS --> BW
    BS --> BX
    BS --> BY
    BS --> BZ
    BS --> CA
    BS --> CB
    BS --> CC
    BS --> CD
    BS --> CE
    BS --> CF
    BS --> CG
    BS --> CH
    BS --> CI
    BS --> CJ
    BS --> CK
    BS --> CL
    BS --> CM
    BS --> CN
    BS --> CO
```

这段代码定义了一个名为 `DashScopeChatOptions` 的类，该类实现了 `FunctionCallingOptions` 和 `ChatOptions` 接口。类中包含多个属性，用于控制聊天生成的参数，如模型、温度、随机种子、核采样概率等。类中还包含多个 getter 和 setter 方法，用于获取和设置这些属性的值。此外，类中定义了一个内部类 `DashscopeChatOptionsBuilder`，用于构建 `DashScopeChatOptions` 对象。该类还提供了 `equals`、`hashCode` 和 `toString` 方法，用于对象的比较和字符串表示。

### 字段列表 Field List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| seed | Integer | 私有属性seed，类型为Integer。 |
| multiModel = false | Boolean | 属性multiModel默认值为false。 |
| responseFormat | DashScopeResponseFormat | 私有属性responseFormat，类型为DashScopeResponseFormat。 |
| stop | List<Object> | 私有属性stop为List<Object>类型。 |
| topP | Double | 私有属性topP，类型为Double，使用JsonProperty注解。 |
| stream | Boolean | 忽略JSON序列化的私有布尔类型变量stream。 |
| incrementalOutput = true | Boolean | 私有属性incrementalOutput默认值为true。 |
| topK | Integer | 私有属性topK，类型为Integer，使用JsonProperty注解。 |
| functions = new HashSet<>() | Set<String> | 忽略JSON序列化的私有字符串集合变量functions。 |
| functionCallbacks = new ArrayList<>() | List<FunctionCallback> | 忽略JSON序列化的函数回调列表。 |
| tools | List<DashScopeApi.FunctionTool> | 私有属性tools，类型为DashScopeApi.FunctionTool列表。 |
| vlHighResolutionImages | Boolean | 私有布尔属性，用于高分辨率图像配置。 |
| maxTokens | Integer | 私有属性maxTokens，类型为Integer。 |
| toolContext | Map<String, Object> | 忽略序列化的工具上下文映射。 |
| proxyToolCalls | Boolean | 忽略JSON序列化中的proxyToolCalls字段。 |
| enableSearch = false | Boolean | 私有布尔变量enableSearch默认值为false。 |
| model | String | 该代码定义了私有字符串变量model，并使用JsonProperty注解进行序列化映射。 |
| repetitionPenalty | Double | 该代码定义了一个私有变量repetitionPenalty，类型为Double，使用JsonProperty注解进行序列化。 |
| temperature | Double | 私有属性temperature，类型为Double，使用JsonProperty注解。 |
| toolChoice | Object | 属性tool_choice定义为私有对象类型。 |

### 方法列表 Method List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| setEnableSearch | void | 设置搜索功能启用状态的Java方法。 |
| setMaxTokens | Integer | 方法返回整数类型的maxTokens值。 |
| getTopP | Double | 该方法返回当前对象的topP值。 |
| setTopK | void | 设置topK参数值的方法。 |
| setSeed | void | 定义方法设置种子值为整数类型。 |
| getSeed | Integer | 获取种子值的方法。 |
| setMultiModel | void | 设置多模型属性的布尔值。 |
| setIncrementalOutput | void | 设置增量输出属性值。 |
| getFrequencyPenalty | Double | 该方法返回空值，未实现频率惩罚功能。 |
| getMaxTokens | Integer | 方法getMaxTokens返回空值。 |
| setFunctionCallbacks | void | 重写方法，设置函数回调列表。 |
| getVlHighResolutionImages | Boolean | 该方法返回高分辨率图像的布尔值。 |
| getTopK | Integer | 重写getTopK方法，返回topK值。 |
| getIncrementalOutput | Boolean | 方法返回布尔值，表示是否启用增量输出。 |
| getTemperature | Double | 重写getTemperature方法，返回当前温度值。 |
| setProxyToolCalls | void | 设置代理工具调用的布尔值。 |
| getRepetitionPenalty | Double | 该方法返回重复惩罚值。 |
| setStream | void | 设置流媒体状态的方法。 |
| setFunctions | void | 重写setFunctions方法，用于设置函数集合。 |
| setVlHighResolutionImages | void | 设置高分辨率图像属性的方法。 |
| getFunctionCallbacks | List<FunctionCallback> | 该方法返回当前对象的函数回调列表。 |
| getFunctions | Set<String> | 重写getFunctions方法，返回当前对象的functions集合。 |
| setTemperature | void | 设置温度值的方法。 |
| getToolChoice | Object | 该方法返回toolChoice对象。 |
| getResponseFormat | DashScopeResponseFormat | 获取DashScope响应格式的方法。 |
| builder | DashscopeChatOptionsBuilder | 创建并返回DashscopeChatOptionsBuilder实例。 |
| copy | ChatOptions | 重写ChatOptions的copy方法，返回DashScopeChatOptions实例。 |
| equals | boolean | equals方法比较DashScopeChatOptions对象的所有属性是否相等。 |
| getPresencePenalty | Double | 该方法返回null，表示未设置存在惩罚值。 |
| getStopSequences | List<String> | 该方法重写getStopSequences，返回空列表。 |
| hashCode | int | 重写hashCode方法，返回多个参数的哈希值。 |
| setToolChoice | void | 设置工具选择属性，更新当前对象工具选择值。 |
| getTools | List<DashScopeApi.FunctionTool> | 该方法返回一个包含DashScopeApi.FunctionTool对象的列表。 |
| getStream | Boolean | 该方法返回布尔类型的stream值。 |
| getProxyToolCalls | Boolean | 重写方法返回代理工具调用布尔值。 |
| getToolContext | Map<String,Object> | 重写getToolContext方法，返回toolContext对象。 |
| setToolContext | void | 重写方法，设置工具上下文为传入的映射。 |
| getStop | List<Object> | 返回名为stop的列表对象。 |
| setTools | void | 设置工具列表方法，接受函数工具列表参数。 |
| fromOptions | DashScopeChatOptions | 静态方法创建DashScopeChatOptions对象，复制所有属性值。 |
| toString | String | DashScopeChatOptions的toString方法返回对象JSON字符串。 |
| getModel | String | 重写getModel方法，返回model变量。 |
| setTopP | void | 设置topP属性值为指定Double类型参数。 |
| setModel | void | 该方法用于设置模型属性，将传入的字符串赋值给类的成员变量model。 |
| getEnableSearch | Boolean | 该方法返回布尔值，表示搜索功能是否启用。 |
| setResponseFormat | void | 设置响应格式的方法，接受DashScopeResponseFormat参数。 |
| setStop | void | 该方法用于设置对象的停止列表。 |
| setRepetitionPenalty | void | 设置重复惩罚值方法。 |
| getMultiModel | Boolean | 该方法返回布尔值multiModel。 |




