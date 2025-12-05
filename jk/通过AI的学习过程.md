# jk自己的学习方法

## 1. 通过AI快速检索信息
AI会给出很长的大段信息，如果中途遇到很多不理解的地方，递归学习很麻烦，所以需要减少AI每次回答的篇幅，尽量控制不理解的知识出现的频率，遇到不理解的东西时立即发给AI让其回答，然后再仔细品读此次回答，试图理解，可以适当让AI给出一些例子方便理解，当完成一整块知识的学习时，退到最上层，看看是否可以完全的理解。如果不能理解，请继续这个过程。直到完全理解这一块的知识。结束的时候可以让AI画出一个此次学习的流程图（遇到的知识点，自己的误解区），这样可以加深自己的理解，整理出更适合自己的知识点，方便以后复习。

```mermaid
flowchart LR
  %% 精简版横向学习闭环，节点合并并增大字体
  %% 将大部分节点共用 largeClass 以增大字体显示
  Start([开始])
  G1[1. 设定小且清晰的学习目标]
  G2[2. 读要点：让 AI 给短答（≤3 段）]
  Check{是否理解？}
  Ask[3. 若不懂：立刻把“第一个不懂点”精确发给 AI（短问）]
  AIAns[AI: 短答 + 1 个游戏业务例子]
  Verify[用例子快速验证（手动/模拟）]
  More{解决了吗？}
  Practice[4. 理解后：动手实践并自测（2-5 分钟）]
  Pass{自测通过？}
  Integrate[5. 将该点合入上层知识块并复述一遍]
  Finish([完成：导出学习流程图与误解地图])

  %% 主流程
  Start --> G1 --> G2 --> Check

  %% 不理解分支（合并列出/提问步骤，循环直到该点解决）
  Check -- 否 --> Ask --> AIAns --> Verify --> More
  More -- 否 --> Ask
  More -- 是 --> Check

  %% 理解后实践与自测（失败退回提问）
  Check -- 是 --> Practice --> Pass
  Pass -- 否 --> Ask
  Pass -- 是 --> Integrate --> Finish

  %% 视觉样式：统一放大字体，节点更宽
  classDef largeFont fill:#fff,stroke:#333,stroke-width:1px,font-size:18px;
  class Start,G1,G2,Check,Ask,AIAns,Verify,More,Practice,Pass,Integrate,Finish largeFont;
  style Start width:120px,height:60px
  style Finish width:200px,height:60px
```