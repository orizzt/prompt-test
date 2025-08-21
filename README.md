# prompt-test
本项目使用PromptMinder提示词管理平台进行测试，旨在展示prompt提示词落地效果。
测试模型为GLM-4-Flash，模型参数设置为Temperature = 0.7（控制输出随机性和创造性），Max Tokens = 2000（限制模型回答最大长度），Top P = 0.7（控制词汇选择多样性）；

<img width="545" height="275" alt="image" src="https://github.com/user-attachments/assets/2231621f-fe00-4ca1-ac1d-b3bbd3c7d5b7" />

Prompt
```
# Role：法律顾问

## Background：
您提供了一段法律纠纷文本。这些案例涉及药品专利、数据保护、医疗行为和算法歧视等多个法律领域，需要我将文本中的信息拆分成独立案例，并提取每个案例的背景、涉及主体、争议焦点和裁决结果。

## Profile：
- Description: 作为一名专业的法律顾问，我具备丰富的法律知识和实践经验，能够准确理解文本内容，并从中提取关键信息。我精通中国法律和欧盟法律，并熟悉中、欧法律术语的标准英译。
- Skills:
  - 理解和分析复杂法律文本
  - 精通中、欧法律体系
  - 提取并整合关键信息
  - 精确使用法律术语和案例描述

## Goals：
- 将文本中的案例拆分成独立单元
- 提取每个案例的背景、涉及主体、争议焦点和裁决结果
- 以JSON数组格式输出

## Constrains：
- 确保法律术语翻译准确
- JSON格式符合语法规范
- 包含所有核心要素

## Workflow：
1. 阅读并理解提供的文本
2. 将文本中的案例进行拆分
3. 对每个案例提取背景、涉及主体、争议焦点和裁决结果
4. 将提取的信息翻译成英语
5. 按照JSON格式输出

## OutputFormat：
- background
- involved_subjects
- dispute_points
- outcomes

## Suggestions：
- 确保在翻译法律术语时使用权威译法
- 仔细检查JSON格式的键名、值和语法
- 确保所有案例的核心要素都被包含在输出中
```
输入：近年来，随着新能源汽车行业的快速发展，电池知识产权纠纷逐渐增多。国内某新能源车企自主研发了一项关于动力电池热管理的核心技术，并申请了发明专利。随后，该车企发现另一家同行企业生产的车型所搭载的电池系统，在热管理逻辑和核心控制算法上与自身专利技术高度相似，遂向法院提起专利侵权诉讼，要求对方停止侵权并赔偿经济损失。

被诉车企辩称，其技术是独立研发的，且在研发过程中未接触过原告的专利技术资料，不存在侵权行为。同时，被诉方指出原告专利中的部分技术特征在申请日前已在行业公开论坛上被讨论过，不具备新颖性和创造性，请求法院宣告该专利无效。

法院受理案件后，委托专业的技术鉴定机构对双方技术方案进行比对。鉴定结果显示，被诉车企的电池热管理系统确实落入了原告专利的保护范围。关于专利有效性的争议，法院审查发现，行业论坛上的讨论仅涉及技术概念，并未公开具体的实现方式和关键参数，原告专利仍符合授权条件。最终，法院判决被诉车企构成专利侵权，需立即停止使用相关技术，并赔偿原告经济损失5000万元。此案也引发了行业内对新能源技术研发边界和知识产权保护的广泛讨论，推动了多家企业加强内部研发流程的合规审查。

输出：
```json
[
  {
    "background": "With the rapid development of the new energy vehicle industry, a domestic new energy vehicle manufacturer's independently developed core technology for battery thermal management has been suspected of infringement by another industry peer, leading to a patent infringement lawsuit.",
    "involved_subjects": {
      "plaintiff": "A domestic new energy vehicle manufacturer (patent holder)",
      "defendant": "The suspected infringing industry peer"
    },
    "dispute_points": "The defendant claimed that its technology was independently developed and that it had not come into contact with the plaintiff's patent technology during the development process. Additionally, the defendant requested the court to declare the plaintiff's patent invalid, arguing that the patent did not possess novelty and inventiveness.",
    "outcomes": {
      "tribunal": "The court",
     "decision": "The court entrusted a professional technical appraisal institution to compare the technical schemes of both parties. The appraisal results showed that the defendant's battery thermal management system fell within the scope of protection of the plaintiff's patent. The court found that the plaintiff's patent was still in compliance with the authorization conditions, as the discussions on the industry forum only involved technical concepts and did not disclose specific implementation methods and key parameters. The court ruled that the defendant constitutes patent infringement, must immediately cease the use of the relevant technology, and compensate the plaintiff for economic losses of 50 million yuan. This case also sparked widespread discussions within the industry on the boundaries of new energy technology research and development and intellectual property protection, prompting many companies to strengthen the compliance review of their internal research and development processes."
    }
  }
]
```
<img width="400" height="600" alt="image" src="https://github.com/user-attachments/assets/d8cd53a1-9a7f-4761-ad22-17cf517c524f" />
