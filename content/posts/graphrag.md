+++
title = 'graphrag'
date = 2024-11-04T15:45:51+08:00
draft = true
+++

[https://github.com/microsoft/graphrag](https://github.com/microsoft/graphrag)

• GraphRAG（由微软）：此系统运用大型语言模型构建基于实体的知识图谱，并预先生成相关实体组的社区摘要，能够捕捉文档集合内的局部和全局关系，从而强化以查询为中心的摘要（QFS）任务。利用开源的 RAG 工具包快速实现，例如LlamaIndex、langchain等。
[https://github.com/microsoft/graphrag](https://github.com/microsoft/graphrag)
• GraphRAG（由 NebulaGraph）：该项目是首个工业 GraphRAG 系统，由 NebulaGraph 公司开发。此项目将大型语言模型融入 NebulaGraph 数据库，旨在提供更智能、更精准的搜索结果。
[https://www.nebula-graph.io/posts/graph-RAG](https://www.nebula-graph.io/posts/graph-RAG)
• GraphRAG（由 Antgroup）：该框架基于诸如 DB-GPT、知识图谱引擎 OpenSPG 和图形数据库 TuGraph 等数个 AI 工程框架开发而成。先是利用大型语言模型从文档中提取三元组，接着将其存于图形数据库中。在检索阶段，它从查询中识别关键字，在图形数据库中定位相应节点，并使用 BFS 或 DFS 遍历子图。在生成阶段，将检索到的子图数据格式化为文本，并与上下文和查询一同提交给大型语言模型处理。
[https://github.com/eosphoros-ai/DB-GPT](https://github.com/eosphoros-ai/DB-GPT)
• NallM（由 Neo4j）：NaLLM（Neo4j 和大型语言模型）框架将 Neo4j 图形数据库技术与大型语言模型相融合。它致力于探索并展示 Neo4j 与大型语言模型之间的协同作用，重点关注三个主要用例：知识图谱的自然语言接口、从非结构化数据创建知识图谱以及利用静态数据和大型语言模型数据生成报告。
[https://github.com/neo4j/NaLLM](https://github.com/neo4j/NaLLM)
• LLM 图形构建器（由 Neo4j）：这是 Neo4j 开发的用于自动构建知识图谱的项目，适用于 GraphRAG 的图形数据库构建和索引阶段。该项目主要借助大型语言模型从非结构化数据中提取节点、关系及其属性，并利用 LangChain 框架创建结构化知识图谱。
[https://github.com/neo4j-labs/llm-graph-builder](https://github.com/neo4j-labs/llm-graph-builder)
[https://llm-graph-builder.neo4jlabs.com/?&amp;utm_campaign=&amp;utm_content=&amp;utm_medium=&amp;utm_source=YouTube&amp;utm_justglobal=NA](https://llm-graph-builder.neo4jlabs.com/?&utm_campaign=&utm_content=&utm_medium=&utm_source=YouTube&utm_justglobal=NA)

[http://neo4j.bangong.xxxxbox.cn/](http://neo4j.bangong.xxxxbox.cn/)

```
neo4j://39.102.46.10:7687
neo4j/password
```

```
https://console.neo4j.io/

key: ****-ZbFwZdp26fulANCoSRI
```

# 安装配置

* pip install graphrag
* mkdir -p ./ragtest/input
* curl [https://www.gutenberg.org/cache/epub/24022/pg24022.txt](https://www.gutenberg.org/cache/epub/24022/pg24022.txt) -o ./ragtest/input/book.txt
* python -m graphrag.index --init --root ./ragtest
* edit files: .env and settings.yaml in the ./ragtest directory.
* python -m graphrag.index --root ./ragtest

# Queery

## method local

[local_searh](./../../graphrag/docs/query/local_search.md)

```

(venv) ➜  rag python3.10 -m graphrag.query --root ./ragtest --method local  '我家的花园叫什么'

INFO: Vector Store Args: {}
creating llm client with {'api_key': 'REDACTED,len=51', 'type': "openai_chat", 'model': 'gpt-4-turbo-preview', 'max_tokens': 4000, 'temperature': 0.0, 'top_p': 1.0, 'n': 1, 'request_timeout': 180.0, 'api_base': '[http://one-api.bangong.xxxxbox.cn/v1](http://one-api.bangong.xxxxbox.cn/v1)', 'api_version': None, 'organization': None, 'proxy': None, 'cognitive_services_endpoint': None, 'deployment_name': None, 'model_supports_json': True, 'tokens_per_minute': 0, 'requests_per_minute': 0, 'max_retries': 10, 'max_retry_wait': 10.0, 'sleep_on_rate_limit_recommendation': True, 'concurrent_requests': 25}
creating embedding llm client with {'api_key': 'REDACTED,len=51', 'type': "openai_embedding", 'model': 'text-embedding-3-small', 'max_tokens': 4000, 'temperature': 0, 'top_p': 1, 'n': 1, 'request_timeout': 180.0, 'api_base': '[http://one-api.bangong.xxxxbox.cn/v1](http://one-api.bangong.xxxxbox.cn/v1)', 'api_version': None, 'organization': None, 'proxy': None, 'cognitive_services_endpoint': None, 'deployment_name': None, 'model_supports_json': None, 'tokens_per_minute': 0, 'requests_per_minute': 0, 'max_retries': 10, 'max_retry_wait': 10.0, 'sleep_on_rate_limit_recommendation': True, 'concurrent_requests': 25}
None
None

SUCCESS: Local Search Response:

```

```
您家的花园被称为百草园。百草园是一个广阔的园林，它不仅对于讲述者来说充满了美好的回忆，如堆雪人和捉鸟等活动，而且它的历史和传承也赋予了它特别的意义。百草园的每一个角落都承载着过去的欢乐和现在的宁静，使其成为一个独特而迷人的地方 [Data: Entities (0)]。

### 百草园的特色

百草园曾经是一个乐园，现在属于朱文公的子孙。这个地方不仅对于讲述者来说充满了美好的回忆，包括堆雪人和捉鸟等活动，而且它的历史和传承也赋予了它特别的意义。百草园的每一个角落都承载着过去的欢乐和现在的宁静，使其成为一个独特而迷人的地方 [Data: Entities (0)]。

### 百草园的历史

百草园现在是早已并屋子一起卖给朱文公的子孙了，连那最末次的相见也已经隔了七八年。其中似乎确凿只有一些野草；但那时却是讲述者的乐园 [Data: Sources (0)]。

### 百草园的生态

百草园中生长着各种植物，如何首乌、木莲、覆盆子等，还有传说中居住着的赤练蛇。这些元素共同构成了百草园丰富的生态环境和神秘的氛围 [Data: Entities (1, 2, 3, 4)]。

百草园不仅是一个充满历史和文化的地方，也是一个生态多样性丰富的自然环境，为讲述者和其他人提供了一个探索和回忆的空间。

```

## method global

[global_search](./../../graphrag/docs/query/global_search.md)

```
python3.10 -m graphrag.query --root ./ragtest --method global  '百草园是什么'

creating llm client with {'api_key': 'REDACTED,len=51', 'type': "openai_chat", 'model': 'gpt-4-turbo-preview', 'max_tokens': 4000, 'temperature': 0.0, 'top_p': 1.0, 'n': 1, 'request_timeout': 180.0, 'api_base': '[http://one-api.bangong.xxxxbox.cn/v1](http://one-api.bangong.xxxxbox.cn/v1)', 'api_version': None, 'organization': None, 'proxy': None, 'cognitive_services_endpoint': None, 'deployment_name': None, 'model_supports_json': True, 'tokens_per_minute': 0, 'requests_per_minute': 0, 'max_retries': 10, 'max_retry_wait': 10.0, 'sleep_on_rate_limit_recommendation': True, 'concurrent_requests': 25}
None
None

SUCCESS: Global Search Response:
```

```
### 百草园概述

百草园不仅仅是一个普通的花园，它是一个充满生命和历史的博物馆，展示了丰富的文化遗产和神秘的传说。这个花园由朱文公所有，成为了连接各种实体的中心枢纽，包括珍稀的神话植物和传说中的生物。百草园内部的每一寸土地，每一株植物，都承载着深厚的文化意义和历史价值，使其成为了一个独特的文化宝库。

### 文化与传承

朱文公作为百草园的所有者，不仅仅是土地的拥有者，更是一个文化遗产的守护者。他的角色超越了单纯的所有者，成为了连接过去与现在，传统与现代的桥梁。百草园的存在，不仅仅是为了展示植物或者提供一个观赏的场所，它更是一个教育和传承文化的平台，通过每一株植物，每一个传说，向人们讲述着历史和文化的故事。

### 神秘的生态宝库

百草园内的植物种类繁多，其中包括具有深厚文化根基和民间传说背景的何首乌和木莲。这些植物不仅在植物学上具有重要意义，也在传统医学和民间传说中占据着重要的位置。此外，赤练蛇的传说为百草园增添了一层神秘和吸引力，象征着花园中神秘未被驯服的本质，吸引着人们前来探索。

### 结论

综上所述，百草园不仅是一个展示神话植物和传说生物的花园，它更是一个文化和历史的见证者，通过朱文公的守护和传承，成为了一个连接过去与现在，自然与文化的独特场所。百草园的每一株植物，每一个角落，都充满了故事和意义，是一个值得深入探索和学习的地方 [Data: Reports (1)]。
```
