# Last Dance

> v1.1.0 · 交付前的最后一遍

Last Dance 用在内容快要交付的时候。方案、PPT、周报、邮件、对外介绍都已经写完了，但还嫌绕、嫌虚、嫌像 AI，就跑一遍。

它做的是编辑工作：删废话，收句子，把悬着的概念落回原文已经写出来的事实。交付时默认只给清洗后的正文，拿去替换就行。

## 它和常见“去 AI 味”工具有什么不同

| 常见做法 | Last Dance |
| --- | --- |
| 重点找敏感词、固定句式和套话。 | 先看这句话有没有在承担信息；能删就删，不能删再改。 |
| 常把正式材料改得更口语，甚至加一点情绪。 | 看原来的场合说话。周报就像周报，方案就像方案；品牌文案和演讲稿可以保留劲儿。 |
| 为了让文字更生动，容易补画面、补案例、补态度。 | 不补原文没有的事实、客户反馈、数字、动作和情绪。 |
| 容易顺手删掉条件、责任人和承诺范围。 | 这些先圈起来。数字、日期、术语、负责人、风险、待确认项都要保住。 |
| 给一份“修改说明”或前后对照。 | 默认只给干净正文。只有你明确要审稿，才把需要你拍板的地方单列出来。 |

它更像交付前的编辑，不像“把一段话改得更像人”的生成器。话可以变，事情不能变。

## v1.1.0 新增

- **支持自定义改动幅度**：可以说“轻一点”“正常”或“可以重写”。
  **Adjustable edit level**: Say “light”, “standard”, or “rewrite”.
- **支持自定义特殊词表**：可以告诉它哪些词必须保留，哪些词统一换成什么说法。
  **Custom lexicon**: Mark terms to preserve or replace consistently.
- **支持用户记忆**：说“记住”后，它会把这些约定记在当前项目，不带到别的项目。
  **Project memory**: Say “remember” to save rules for this project only.
- **支持直接反馈**：可以直接说“太重了”“别像广告”“第二段别动”。它会按这次反馈重做；只有你说“记住”，才会变成长期规则。
  **Direct feedback**: Say “too heavy”, “less promotional”, or “keep paragraph two”. It only becomes a lasting rule when you say “remember”.

平时贴正文就行。没有设置文件时，Last Dance 会直接清洗，不会先让你设置。
Just paste the text. Without saved settings, Last Dance cleans it directly instead of asking you to configure it first.

## 安装

仓库里的 Skill 位于 `lastdance/`。

在 Codex 中运行：

```bash
python3 ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo nico-zhuang/lastdance \
  --path lastdance
```

也可以把这个仓库链接发给 Codex，并说明“安装这个 Skill”：

`https://github.com/nico-zhuang/lastdance/tree/main/lastdance`

安装后从下一轮任务起可用。

## 怎么用

把成稿贴进来，再说“Last Dance”“去 AI 味”“最后过一遍”或“交付前清洗”。内容和结构还没定，就别急着用它；先把事写完整。

对外材料可以这样用：

```text
先跑一次 Last Dance，再跑一次 Last Dance review。
```

前者把话收干净；后者在正文之外留一小段“请你确认”，只放那些不能替你决定的事。

## 它会保住什么

数字、日期、金额、比例、版本号、链接、项目名、人名、产品名、字段、命令、代码，以及责任人、条件、风险、待确认项和承诺范围，都不该为了“更简洁”被洗掉。

合同、法规、政策原文、审批口径和直接引语默认不动。术语看着生硬，也不代表该换；不确定是不是业务专名，就留着。

## 它什么时候会问一句

大多数时候不会打断你。下面三种情况，它会停下来问：

- 给的是提纲：`这还是个提纲。要我先补成稿，还是只顺一顺现有的句子？`
- 同一句话放进方案和拿去演讲，写法会差很多：`这段最后放进正式材料，还是拿去讲、拿去传播？`
- 对外材料里有关键数字，但当前输入看不到出处：`“<关键数字或结论>”的来源确定吗？不确定的话，我先不动这句。`

它不会因此去网上查数据，也不会擅自把“达到 10 倍”改成“可能提升 10 倍”。普通清洗时，数字和原有语气照留；只有你开了审稿或对外检查，才会问来源。

## 团队里怎么放

内部材料：成稿后跑一次 Last Dance。对外材料：先跑一次 Last Dance，再跑一次 Last Dance review。

别拿它代替研究、策略判断或事实核查。它只负责把已经想清楚的内容，写得干净、稳当、能交付。

## 仓库结构

```text
lastdance/
├── lastdance/
│   ├── agents/openai.yaml
│   ├── references/
│   │   ├── interaction-cases.md
│   │   ├── lexicon-template.md
│   │   └── preferences-template.md
│   └── SKILL.md
└── README.md
```
