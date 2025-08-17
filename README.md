# prompt-test
本项目使用PromptMinder提示词管理平台进行测试，旨在展示prompt提示词落地效果。
测试模型为GLM-4-Flash，模型参数设置为Temperature = 0.7（控制输出随机性和创造性），Max Tokens = 2000（限制模型回答最大长度），Top P = 0.7（控制词汇选择多样性）；

<img width="545" height="275" alt="image" src="https://github.com/user-attachments/assets/2231621f-fe00-4ca1-ac1d-b3bbd3c7d5b7" />

Prompt
```
# Role
你是一位专业的法律顾问。

## Skills
- 精通中国法律和欧盟法律
- 知识储备丰富
- 能够理解文本

## Action
请按要求，一步一步的完成任务。
1.我会提供给你一段文本，使用三引号(""")包裹起来，提取出对应的背景、涉及的主体、法律争议点以及结果或进展。
2.将第一步中的答案翻译成英语，并以JSON格式输出。
"""
近年来，医疗健康领域涌现出多起涉及药品专利与数据保护的法律纠纷。2020 年，某跨国药企就其研发的一款靶向抗癌药物获得核心化合物专利及晶型专利。2023 年，该企业对一家仿制药公司提起专利侵权诉讼，主张后者生产的仿制药在分子结构与制剂工艺上落入其专利保护范围。然而，法院经审理认为，原告专利中关于晶型稳定性的技术特征已在申请日前被行业期刊公开报道，丧失新颖性，最终裁定部分专利权无效，驳回了原告诉讼请求。同期，另有多起纠纷围绕生物类似药的数据独占期展开，涉及药企对临床试验数据的保护与仿制药企业的合理使用边界争议。

在欧洲，德国联邦最高法院审理了一起关于远程医疗服务资质的案件。一名未取得医师执业资格的技术人员通过自研算法提供在线疾病风险评估服务，收取费用并给出治疗建议。原告医疗行业协会主张其行为违反《联邦医师法》，被告则辩称其提供的是数据分析服务，不属于医疗实践范畴。法院最终裁决，疾病风险评估与治疗建议直接关联患者健康决策，属于医疗行为的延伸，必须由具备资质的医师实施；同时明确，即使借助人工智能技术，核心医疗判断环节仍需医师主导，被告被禁止在无医师监督的情况下开展相关业务。

随着人工智能技术的广泛应用，算法歧视引发的法律规制成为焦点。2024 年，美国加利福尼亚州颁布《算法公平性法案》，要求从事信贷、就业、住房领域的企业公开其自动化决策系统的基本原理，禁止使用包含种族、性别等敏感特征的训练数据，并建立算法偏见检测与修正机制。欧盟则在《人工智能法案》中增设专门条款，规定高风险 AI 系统在部署前需通过独立机构的合规审查，对因算法错误导致的损害确立举证责任倒置原则。中国也在《生成式人工智能服务管理暂行办法》中明确，服务提供者需对算法生成内容的合法性负责，因算法滥用造成他人权益损害的，应承担民事赔偿责任。
"""

## Constrains
- 忽略无关内容
- 请确保符合逻辑
- 请保持友好的服务态度


## Format
对应JSON的key为：background, involved_subjects, dispute_points, outcomes

```
<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/af0891f4-a33f-41a8-b289-234fa2ac039a" />

输入：请完成提示词任务

输出：
```json
[
  {
    "background": "Medical health field has witnessed many legal disputes involving drug patents and data protection in recent years.",
    "involved_subjects": "A multinational pharmaceutical company and a generic drug company",
    "dispute_points": "The generic drug company's product infringes on the patent protection of the core compound and crystal form of the drug developed by the multinational company, and the patentability of the technical features of crystal stability in the plaintiff's patent has been lost due to prior publication.",
    "outcomes": "The court ruled that part of the patent rights were invalid and rejected the plaintiff's lawsuit request."
  },
  {
    "background": "In Europe, the German Federal Supreme Court heard a case about the qualification of telemedicine services.",
    "involved_subjects": "A technician without a medical practice qualification who provides online disease risk assessment services using self-developed algorithms, charges fees, and gives treatment advice",
    "dispute_points": "The plaintiff's medical industry association argues that the defendant's actions violate the Federal Medical Practitioner Law, while the defendant claims that the service provided is data analysis and does not belong to the scope of medical practice.",
    "outcomes": "The court ruled that disease risk assessment and treatment advice are directly related to patients' health decisions and are an extension of medical practice, which must be implemented by qualified physicians; at the same time, it was clarified that even with the help of artificial intelligence technology, the core medical judgment process still needs to be led by physicians, and the defendant was prohibited from carrying out related business without physician supervision."
  },
  {
    "background": "With the wide application of artificial intelligence technology, the legal regulation of algorithmic discrimination has become a focus.",
    "involved_subjects": "California, the European Union, and China",
    "dispute_points": "California enacted the 'Algorithm Fairness Act' requiring enterprises in the credit, employment, and housing fields to disclose the basic principles of their automated decision-making systems, prohibit the use of training data containing sensitive features such as race and gender, and establish algorithm bias detection and correction mechanisms. The European Union has added special provisions in the 'Artificial Intelligence Act' stipulating that high-risk AI systems must pass compliance review by independent institutions before deployment, and establish a reverse burden of proof principle for damages caused by algorithm errors. China has also clearly stipulated in the 'Interim Measures for the Administration of Generative Artificial Intelligence Services' that service providers must be responsible for the legality of algorithm-generated content, and shall bear civil liability for damages caused by algorithm abuse.",
    "outcomes": "California, the European Union, and China have implemented or are implementing laws and regulations to regulate algorithmic discrimination."
  }
]
```
