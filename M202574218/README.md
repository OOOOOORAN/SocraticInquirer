# Socratic Inquirer

prompt for learning by questioning

**提示词 baseline**:

    请聚焦论文未充分论证的部分及可能影响论文可信度的潜在问题，对论文实际落地的可行性、核心贡献的代价与收益矛盾、实验场景与负载的代表性等角度，对这篇论文提出深入且尖锐的质疑。不要复述论文内容，仅提出批判性问题。

**常用模型**：DeepSeek、KIMI、豆包、文心、ChatGPT

**交叉评价**:

$$\{evaluator(reviewer(paper)) | reviewer, evaluator \in [DS, KM, DB], paper \in ReadingList\}$$

0. 基于**学术评价参考论文**，准备评分提示词 $Prompt_{evaluator_{id}}$
1. 在 reviewer 模型中，上传目标论文，使用提示词 $Prompt_{baseline}$ 质疑论文，得出**向论文的提问** $Question_{paper}$
2. 在 evaluator 模型中，上传目标论文，使用评分提示词，对 $Question_{paper}$ 打分
3. 根据 reviewer 和 evaluator 所用模型，归纳数据

**学术评价参考论文**

1. **IEEE Network Reviewer Guidelines**  
   **来源**: IEEE Communications Society  
   **链接**: [IEEE Network 审稿指南](https://www.comsoc.org/publications/magazines/ieee-network/reviewer-guidelines)  
   **说明**: 强调对方法理论完备性和实验可重复性的评估标准。
2. **Wang, Y., Zhang, L., & Chen, H. (2017)**  
   *Questioning Techniques Promote Critical Thinking in Engineering Education*  
   **期刊**: IEEE Transactions on Education  
   **链接**: [IEEE Xplore](http://ieeexplore.ieee.org/document/7942978/)  
   **说明**: 该研究验证了创新性质疑对工程教育中论文修改后创新指数提升23%的量化效果。
3. **Gupta, R. et al. (2021)**  
   *Models for Finding Quality Questions in Scientific Discussions*  
   **会议**: ACL  
   **链接**: [ACL Anthology](https://aclanthology.org/2021.acl-long.32/)  
   **说明**: 基于BERT的语义相似度计算框架（F1=66.6%）。
4. **Shin, H. et al. (2025)**  
   *Mind the Blind Spots: A Focus-Level Evaluation Framework for LLM Reviews*  
   **预印本**: arXiv:2502.17086  
   **链接**: [arXiv](https://arxiv.org/abs/2502.17086)  
   **说明**: 量化分析LLM生成的评审对技术有效性关注度比人类高30%，但创新性评估不足。
5. 严炜炜,黄为,温馨. 学术社交网络问答质量智能评价与服务优化研究[J]. 图书情报工作,2021,65(6):129-137.
6. 吴雅威,张向先,陶兴,等. 基于用户感知的学术问答社区答案质量评价指标构建[J]. 情报科学,2020,38(10):141-147

**准备评分提示词**

    请结合这篇论文，根据提问是否准确把握论文核心、体现背景理解、能追溯研究基础、提出有深度且可证伪的质疑、指出潜在缺陷、推动学术讨论与方法反思等维度，从0到10分科学评价其提问质量。

## 评分统计

对论文 FLATQUANT: Flatness Matters for LLM Quantization 进行DeepSeek、KIMI、豆包、文心的质疑与相互评分统计，共得到16组得分。

| 质疑模型 | Deepseek打分 | Kimi打分 | 豆包打分 | 文心打分 | ChatGPT打分 |
|:-----------------:|:---------:|:-----:|:-----:|:---------:|:---------:|
| Deepseek         | 9.5    | 9.3 | 9.5 | 8.8 | 9.0 |
| Kimi             | 9.2    | 9.6 | 9.5 | 8.5 | 9.4 |
| 豆包             | 9.0    | 9.4 | 9.8 | 8.5      | 9.0 |
| 文心一言         | 8.8 |   9.2    | 9.6 | 8.3   | 8.5 |
|  ChatGPT        | 9.0 | 9.2 | 9.5 | 8.5 | 9.0      |

