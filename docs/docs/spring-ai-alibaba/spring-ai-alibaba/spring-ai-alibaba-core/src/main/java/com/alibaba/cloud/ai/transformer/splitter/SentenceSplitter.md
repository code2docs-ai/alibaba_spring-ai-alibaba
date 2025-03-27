# 基础信息

|      |      |
|------|------|
| 名称 | SentenceSplitter |
| 编码语言 | .java |
| 代码路径 | spring-ai-alibaba/spring-ai-alibaba-core/src/main/java/com/alibaba/cloud/ai/transformer/splitter/SentenceSplitter.java |
| 包名 | com.alibaba.cloud.ai.transformer.splitter |
| 依赖项 | ['java.io.IOException', 'java.io.InputStream', 'java.util.ArrayList', 'java.util.Collections', 'java.util.List', 'com.knuddels.jtokkit.Encodings', 'com.knuddels.jtokkit.api.Encoding', 'com.knuddels.jtokkit.api.EncodingRegistry', 'com.knuddels.jtokkit.api.EncodingType', 'opennlp.tools.sentdetect.SentenceDetectorME', 'opennlp.tools.sentdetect.SentenceModel', 'org.springframework.ai.transformer.splitter.TextSplitter', 'org.springframework.util.Assert'] |
| 概述说明 | SentenceSplitter类用于文本分句，支持自定义块大小和CL100K_BASE编码。 |

# 说明

SentenceSplitter类专门用于将文本按句子进行分割，支持用户自定义块大小，并采用CL100K_BASE编码方式进行处理。

# 类列表 Class Summary

| 名称   | 类型  | 说明 |
|-------|------|-------------|
| SentenceSplitter | class | SentenceSplitter类用于按句子分割文本，支持自定义块大小，使用CL100K_BASE编码。 |



## 类 SentenceSplitter

|      |      |
|------|------|
| 访问范围 | public |
| 类型 | class |
| 名称 | SentenceSplitter |
| 说明 | SentenceSplitter类用于按句子分割文本，支持自定义块大小，使用CL100K_BASE编码。 |


### UML类图

```mermaid
classDiagram
    class TextSplitter {
        <<Interface>>
        +List~String~ splitText(String text)
    }

    class SentenceSplitter {
        -EncodingRegistry registry
        -Encoding encoding
        -int DEFAULT_CHUNK_SIZE
        -SentenceModel sentenceModel
        -int chunkSize
        +SentenceSplitter()
        +SentenceSplitter(int chunkSize)
        +List~String~ splitText(String text)
        -SentenceModel getSentenceModel()
        -List~Integer~ getEncodedTokens(String text)
    }

    class EncodingRegistry {
        <<Interface>>
        +Encoding getEncoding(EncodingType encodingType)
    }

    class Encoding {
        <<Interface>>
        +IntStream encode(String text)
    }

    class SentenceModel {
        +SentenceModel(InputStream is)
    }

    class SentenceDetectorME {
        +SentenceDetectorME(SentenceModel model)
        +String[] sentDetect(String text)
    }

    class InputStream {
        <<Interface>>
    }

    TextSplitter <|.. SentenceSplitter : 实现
    SentenceSplitter --> EncodingRegistry : 依赖
    SentenceSplitter --> Encoding : 依赖
    SentenceSplitter --> SentenceModel : 依赖
    SentenceSplitter --> SentenceDetectorME : 依赖
    SentenceSplitter --> InputStream : 依赖
    EncodingRegistry --> Encoding : 依赖
    SentenceDetectorME --> SentenceModel : 依赖
```

### 描述
`SentenceSplitter` 类继承自 `TextSplitter` 接口，用于将文本按句子分割成指定大小的块。它依赖于 `EncodingRegistry` 和 `Encoding` 来处理文本编码，使用 `SentenceModel` 和 `SentenceDetectorME` 来检测句子。`SentenceSplitter` 通过 `splitText` 方法将文本分割成块，并通过 `getEncodedTokens` 方法获取编码后的 token 列表。`getSentenceModel` 方法用于加载句子模型文件。整个类设计用于高效处理文本分割任务。


### 内部方法调用关系图

```mermaid
graph TD
    A["类SentenceSplitter"]
    B["属性: EncodingRegistry registry"]
    C["属性: Encoding encoding"]
    D["属性: int DEFAULT_CHUNK_SIZE"]
    E["属性: SentenceModel sentenceModel"]
    F["属性: int chunkSize"]
    G["构造方法: SentenceSplitter()"]
    H["构造方法: SentenceSplitter(int chunkSize)"]
    I["重写方法: List<String> splitText(String text)"]
    J["私有方法: SentenceModel getSentenceModel()"]
    K["私有方法: List<Integer> getEncodedTokens(String text)"]
    L["创建: SentenceDetectorME sentenceDetector"]
    M["调用: sentenceDetector.sentDetect(text)"]
    N["判断: texts == null || texts.length == 0"]
    O["返回: Collections.emptyList()"]
    P["创建: List<String> chunks"]
    Q["创建: StringBuilder chunk"]
    R["循环: for (int i = 0; i < texts.length; i++)"]
    S["计算: int currentChunkSize = getEncodedTokens(chunk.toString()).size()"]
    T["计算: int textTokenSize = getEncodedTokens(texts[i]).size()"]
    U["判断: currentChunkSize + textTokenSize > chunkSize"]
    V["添加: chunks.add(chunk.toString())"]
    W["重新创建: chunk = new StringBuilder(texts[i])"]
    X["追加: chunk.append(texts[i])"]
    Y["判断: i == texts.length - 1"]
    Z["添加: chunks.add(chunk.toString())"]
    AA["返回: chunks"]
    AB["加载: InputStream is = getClass().getResourceAsStream('/opennlp/opennlp-en-ud-ewt-sentence-1.2-2.5.0.bin')"]
    AC["判断: is == null"]
    AD["抛出异常: throw new RuntimeException('sentence model is invalid')"]
    AE["返回: new SentenceModel(is)"]
    AF["抛出异常: throw new RuntimeException(e)"]
    AG["判断: Assert.notNull(text, 'Text must not be null')"]
    AH["返回: this.encoding.encode(text).boxed()"]

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
    G --> H
    H --> J
    I --> L
    L --> M
    M --> N
    N --> O
    N --> P
    P --> Q
    Q --> R
    R --> S
    S --> T
    T --> U
    U --> V
    V --> W
    U --> X
    R --> Y
    Y --> Z
    Z --> AA
    J --> AB
    AB --> AC
    AC --> AD
    AC --> AE
    AE --> AF
    K --> AG
    AG --> AH
```

这段代码定义了一个 `SentenceSplitter` 类，用于将文本按句子分割，并根据指定的块大小将句子组合成块。类中包含了两个构造方法，分别用于初始化块大小和句子模型。`splitText` 方法负责将输入文本分割成句子，并根据编码后的令牌数量将句子组合成块。`getSentenceModel` 方法用于加载句子模型，`getEncodedTokens` 方法用于获取文本的编码令牌。流程图展示了类中各个方法的调用关系和逻辑流程。

### 字段列表 Field List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| registry = Encodings.newLazyEncodingRegistry() | EncodingRegistry | 创建私有且不可变的编码注册表实例。 |
| sentenceModel | SentenceModel | 私有不可变的句子模型实例。 |
| DEFAULT_CHUNK_SIZE = 1024 | int | 定义默认块大小为1024的私有静态常量。 |
| chunkSize | int | 私有整型变量chunkSize。 |
| encoding = registry.getEncoding(EncodingType.CL100K_BASE) | Encoding | 私有编码对象初始化为注册表中CL100K_BASE类型的编码。 |

### 方法列表 Method List

| 名称  | 类型  | 说明 |
|-------|-------|------|
| getEncodedTokens | List<Integer> | 获取文本编码后的整数列表，确保文本非空。 |
| splitText | List<String> | 方法将文本按句子分割，并根据块大小合并为合适的分块。 |
| getSentenceModel | SentenceModel | 获取OpenNLP句子模型，若无效或异常则抛出运行时错误。 |




