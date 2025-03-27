# 基础信息

|      |      |
|------|------|
| 名称 | ai |
| 编码语言 | .java |
| 代码路径 | spring-ai-alibaba/community/document-parsers/spring-ai-alibaba-starter-document-parser-pdf-tables/src/main/java/com/alibaba/cloud/ai |
| 包名 | spring-ai-alibaba.community.document-parsers.spring-ai-alibaba-starter-document-parser-pdf-tables.src.main.java.com.alibaba.cloud.ai |
| 概述说明 | PdfTablesParser类解析PDF表格，支持指定页码和元数据，提取为文档列表。 |

# 说明

PdfTablesParser类用于解析PDF文件中的表格数据，支持用户指定特定的页码和元数据。通过该类的功能，能够将PDF中的表格数据提取并转换为文档列表，便于后续处理和分析。这一工具在处理包含大量表格的PDF文件时，能够有效提高数据提取的效率和准确性。


### 包内部结构视图

```mermaid
graph TD
    ai --> parser
    parser --> pdf
    pdf --> tables
    tables --> PdfTablesParser.java
```

该流程图展示了从`ai`目录到`PdfTablesParser.java`文件的层级关系。`ai`目录下包含`parser`子目录，`parser`下又包含`pdf`子目录，`pdf`下包含`tables`子目录，最终在`tables`目录中找到`PdfTablesParser.java`文件。该图清晰地反映了路径的嵌套结构，展示了从顶层目录到具体文件的层级关系。

# 文件列表 File List

| 名称   | 类型  | 说明 |
|-------|------|-------------|
| [parser](parser/_module.md) | package | PdfTablesParser类解析PDF表格，支持指定页码和元数据，提取为文档列表。 |


