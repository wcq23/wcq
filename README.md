```mermaid
graph TD
    subgraph A[数据源]
        A1(专业知识<br>如:产品手册)
        A2(客服采纳回答<br>如:高质量Q&A)
        A3(业务知识落地<br>如:服务规范SOP)
    end

    subgraph B[数据处理与入库]
        B1(汇聚与清洗)
        B2(文本切分与向量化)
        B3[📚 业务知识库<br>(向量数据库)]
    end

    subgraph C[智能问答核心 (RAG)]
        C1(用户/客服提问)
        C2{🤖 AI Agent}
        C3(大语言模型<br>LLM)
        C4(✅ 生成专业回复)
    end

    subgraph D[应用层]
        D1(知识问答)
        D2(实时辅助)
        D3(数据分析)
    end

    %% 定义流程连接
    A1 --> B1
    A2 --> B1
    A3 --> B1

    B1 --> B2
    B2 --> B3

    C1 --> C2

    C2 --"1. 检索相关知识"--> B3
    B3 --"返回知识片段"--> C2
    C2 --"2. 结合知识生成答案"--> C3
    C3 --"返回优化后的答案"--> C2
    C2 --> C4

    C4 --> D1
    C4 --> D2
    C4 --> D3
```
