# 基础信息

|      |      |
|------|------|
| 名称 | ai |
| 编码语言 | .java |
| 代码路径 | spring-ai-alibaba/community/document-readers/spring-ai-alibaba-starter-document-reader-poi/src/main/java/com/alibaba/cloud/ai |
| 包名 | spring-ai-alibaba.community.document-readers.spring-ai-alibaba-starter-document-reader-poi.src.main.java.com.alibaba.cloud.ai |
| 概述说明 | PoiDocumentReader类提取文档，支持自定义格式和元数据。 |

# 说明

PoiDocumentReader类是一个用于从资源中提取文档的工具，支持用户自定义文本格式化功能，并且能够包含与文档相关的元数据源信息。该类的主要作用是高效地从指定资源中读取文档内容，同时允许用户根据需要调整文本的格式，并保留文档的元数据，以便进一步处理或分析。


### 包内部结构视图

```mermaid
graph TD
    ai --> reader
    reader --> poi
    poi --> PoiDocumentReader.java
```

该流程图展示了从`ai`到`PoiDocumentReader.java`的层级关系。首先，`ai`目录下包含`reader`子目录，`reader`目录下又包含`poi`子目录，最后在`poi`目录中找到`PoiDocumentReader.java`文件。这种层级结构清晰地反映了文件的组织方式，便于理解和导航。

# 文件列表 File List

| 名称   | 类型  | 说明 |
|-------|------|-------------|
| [reader](reader/_module.md) | package | PoiDocumentReader类提取文档，支持自定义格式和元数据。 |


