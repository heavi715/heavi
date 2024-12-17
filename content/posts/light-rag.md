+++
title = 'AI Graph RAG'
date = 2024-11-30T15:45:51+08:00
draft = true
+++


### Graph RAG

GraphRAG的缺点
https://aka.ms/graphrag 项目旨在通过利用非结构化文本中的隐式关系来扩展 AI 系统可以在私有数据集上回答的问题类别。与传统向量 RAG（或“语义搜索”）相比，GraphRAG 的一个关键优势是它能够回答针对整个数据集的全局查询，例如“数据中的主要主题是什么”或“对 X 最重要的影响是什么？相反，矢量 RAG 擅长于答案类似于查询并且可以在特定文本区域中找到的本地查询，例如“who”、“what”、“when”和“where”问题的典型情况。

* GraphRAG 运行速度非常慢，因为它需要多个 LLM API 调用，可能会达到速率限制。
* 它的成本较高。
* 为了将新数据合并到现有的图形索引中，我们还需要为以前的数据重建整个 KG，这是一种低效的方法。
* 没有对重复元素执行明确的重复数据删除步骤，这会导致图形索引嘈杂。

与 Naive RAG 相比，LightRAG 提供：
* 综合信息检索，答案多样。
* 高效且低成本的检索
* 快速适应数据并以最少的重新索引来更新数据。

### [LightRAG](https://github.com/HKUDS/LightRAG)
LightRAG 解决了 GraphRAG 的两个主要痛点，
* 通过比社区遍历更好的方法减少索引和响应时间。
* 使用仅更新特定元素实例的增量更新算法轻松适应新数据。


## Light RAG
- 支持fastapi server
- 中文不友好
  
分四种查询方式
- local
- global
- hybrid
- naive

<https://github.com/aiproductguy/lightrag-gui/blob/demo2/notebooks/streamlit-app-lightrag.py>

存储：
![存储：](https://camo.githubusercontent.com/fa79bd2d317163583e8acdeb7c28b16d10652cfcd92c4bab85cc00954ffb1888/68747470733a2f2f6c6561726e6f70656e63762e636f6d2f77702d636f6e74656e742f75706c6f6164732f323032342f31312f4c696768745241472d566563746f7244422d4a736f6e2d4b562d53746f72652d496e646578696e672d466c6f7763686172742d7363616c65642e6a7067)
查询：
![查询：](https://camo.githubusercontent.com/32d67fdd28040d24756373fc674cae593b9961c2ef84fb8a0a8104f33735ab2a/68747470733a2f2f6c6561726e6f70656e63762e636f6d2f77702d636f6e74656e742f75706c6f6164732f323032342f31312f4c696768745241472d5175657279696e672d466c6f7763686172742d4475616c2d4c6576656c2d52657472696576616c2d47656e65726174696f6e2d4b6e6f776c656467652d4772617068732d7363616c65642e6a7067)

### rusult

百草园是什么

Understanding "Bai Cao Yuan" (百草园)
"Bai Cao Yuan" (百草园) translates to "The Hundred Herb Garden" in English. It is a significant setting in the autobiographical writings of Chinese author [[鲁迅]] (Lu Xun). The garden embodies a nostalgic representation of childhood, exploring themes of innocence, exploration, and the natural world.

Key Aspects of Bai Cao Yuan:
Symbol of Childhood:

Bai Cao Yuan serves as a playground for the narrator during their youth, filled with various plants and creatures, symbolizing the joys and adventures of childhood. The garden represents a carefree time before the responsibilities and strictures of adulthood set in.
Natural Environment:

The garden is described as vibrant and alive, with diverse flora and fauna. It features elements like vegetable plots (菜畦), the tall soapberry tree (皂荚树), and raspberries (覆盆子), all contributing to its lush atmosphere and the narrator's fond memories.
Contrast with Winter:

The text highlights how the garden transforms with the seasons. In winter, Bai Cao Yuan becomes less lively, contrasting sharply with its summer vibrancy. This seasonal change reflects the passage of time and the inevitable loss of childhood innocence.
Cultural Significance:

The garden is not just a physical space but also a metaphor for the narrator's emotional landscape and the cultural context of childhood in a traditional Chinese setting. It evokes a sense of longing for simpler times and the connection to nature.
Conclusion
In conclusion, "Bai Cao Yuan" represents more than just a garden; it is a poignant symbol of childhood memories, the beauty of nature, and the bittersweet passage of time. The richness of its description allows readers to connect deeply with the themes of nostalgia and innocence.

Answer: Bai Cao Yuan symbolizes childhood innocence, exploration, and the beauty of nature, contrasting vibrancy in summer with stillness in winter.

Sources: Source 1, Source 2, Source 3

理解《百草园》

《百草园》（Bai Cao Yuan）在英文中译为“百草园”。这是中国作家鲁迅（Lu Xun）自传体作品中一个重要的场景。这个花园象征着童年的怀旧情怀，探讨了纯真、探索和自然世界等主题。

百草园的关键方面：

童年象征：

百草园作为叙述者年轻时的游乐场，充满了各种植物和动物，象征着童年的欢乐和冒险。这个花园代表了成年责任和严格规定之前的无忧无虑时光。

自然环境：

花园被描述得生机勃勃、充满活力，拥有多样化的植物和动物。它有蔬菜田（菜畦）、高大的肥皂荚树（皂荚树）和覆盆子等元素，都为它丰富的氛围和叙述者的美好回忆做出了贡献。

与冬天的对比：

文本强调了花园随着季节的变化而转变。冬天，百草园变得不那么活跃，与夏天的活力形成鲜明对比。这种季节变化反映了时间的流逝和童年纯真的不可避免的损失。

文化意义：

这个花园不仅仅是一个物理空间，也是叙述者情感世界和传统中国背景下童年文化背景的隐喻。它唤起了对更简单时代的渴望和对自然的联系。

结论

总之，《百草园》不仅仅是一个花园；它是童年记忆、自然之美和时间苦乐参半流逝的感人的象征。其丰富的描述让读者能够深入地与怀旧和纯真等主题产生共鸣。

答案：《百草园》象征着童年纯真、探索和自然之美，对比夏天活力四射与冬天宁静平和。

来源：来源1、来源2、来源3