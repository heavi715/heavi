
+++
title = 'AI LazyGraphRAG'
date = 2024-11-30T15:45:51+08:00
draft = true
+++

### [LazyGraphRAG](https://www.microsoft.com/en-us/research/blog/lazygraphrag-setting-a-new-standard-for-quality-and-cost/)
https://mp.weixin.qq.com/s/kDUcg5CzRcL7lTGllv-GKA

LazyGraphRAG 旨在融合向量RAG 和GraphRAG 的优点，同时克服它们各自的局限性：矢量 RAG 是一种最佳优先搜索形式，它使用与查询的相似性来选择最匹配的源文本块。但是，它不知道全局查询要考虑的数据集的广度。GraphRAG 全局搜索是一种广度优先搜索形式，它使用源文本实体的社区结构来确保在考虑数据集的全部广度的情况下回答查询。但是，它不知道本地查询要考虑的最佳社区。LazyGraphRAG 以迭代深化的方式结合了最佳优先和广度优先搜索动态（表 1）。与完整 GraphRAG 的全局搜索机制相比，这种方法在延迟 LLM 使用并显着提高答案生成效率的方式上是“懒惰的”。整体性能可以通过一个主要参数（相关性测试预算）进行扩展，该参数以一致的方式控制成本-质量权衡。


