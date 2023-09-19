# Automatic and Human Evaluation
https://www.mdpi.com/2227-7390/11/4/1006  
A Survey on Evaluation Metrics for Machine Translation
![image](https://github.com/YRH0/book/assets/74707759/d61d23df-4a2e-4429-9e4d-4878f28e1bba)
![image](https://github.com/YRH0/book/assets/74707759/f4aa905d-e860-495f-bd91-60b27bbbd5dc)
![image](https://github.com/YRH0/book/assets/74707759/de612494-f5b9-49c9-b678-77ded3d5a2ac)

## 自动评价
使用计算机评价
### BLEU
BLEU基于N-gram，只对词汇变化敏感，不能识别句子语义或语法的变化，因此，它们被反复证明与人工评估差距较大。1-gram的结果代表了文中有多少个词被单独翻译出来了，因此它反映的是这篇译文的忠实度；而当我们计算2-gram以上时，更多时候结果反映的是译文的流畅度，值越高文章的可读性就越好。
https://www.cnblogs.com/by-dream/p/7679284.html

BLEURT
![image](https://github.com/YRH0/book/assets/74707759/926713fd-bc32-4d41-be4c-69a779a7065e)
Similarity refers to the human-annotated semantic similarity between sentence 1 and sentence 2. Scores are normalized.

## 人类评价
Can Machine Translation Systems be Evaluated by the Crowd Alone
提出一个新的方法众包的人类翻译质量评估。
它允许员工个人发展自己的个人评估策略。

## 元评价（评价方法的评价）

