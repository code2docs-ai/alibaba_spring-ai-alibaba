# 基础信息

|      |      |
|------|------|
| 名称 | alibaba |
| 编码语言 | .java |
| 代码路径 | spring-ai-alibaba/community/document-readers/spring-ai-alibaba-starter-document-reader-poi/src/main/java/com/alibaba |
| 包名 | spring-ai-alibaba.community.document-readers.spring-ai-alibaba-starter-document-reader-poi.src.main.java.com.alibaba |
| 概述说明 | PoiDocumentReader类提取文档，支持自定义格式和元数据。 |

# 说明

PoiDocumentReader类是一个用于从资源中提取文档的工具，支持用户自定义文本格式化功能，并且能够包含与文档相关的元数据源信息。该类的主要作用是高效地从指定资源中读取文档内容，同时允许用户根据需要调整文本的格式，并保留文档的元数据，以便进一步处理或分析。


### 包内部结构视图

```mermaid
graph TD
    alibaba --> cloud
    cloud --> ai
    ai --> reader
    reader --> poi
    poi --> PoiDocumentReader.java
```

该流程图展示了从`alibaba`到`PoiDocumentReader.java`的层级关系。路径从`alibaba`开始，逐级深入到`cloud`、`ai`、`reader`和`poi`，最终指向`PoiDocumentReader.java`文件。每个节点代表路径中的一个层级，清晰地展示了文件在项目结构中的位置。

# 文件列表 File List

| 名称   | 类型  | 说明 |
|-------|------|-------------|
| [cloud](cloud/_module.md) | package | PoiDocumentReader类提取文档，支持自定义格式和元数据。 |


