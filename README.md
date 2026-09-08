# concept-study-lab · 概念学习实验室

> 用 AI 辅助完成的一次完整学习闭环：**建 Skill → 用 Skill 学概念 → 人工核查 → 版本化沉淀 → 推到 GitHub**。
> 本仓库既是一份作业成果，也是一个可以持续复用的"概念学习工具箱"。

---

## 1. 这个仓库是做什么的

我在这台电脑上：

1. 创建了一个 GitHub 仓库并克隆到本地；
2. 在 WorkBuddy 中打开本地仓库，**创建了一个"概念学习资料生成 Skill"**；
3. 把它作为**项目级 Skill** 存放在仓库根目录的 `.workbuddy/skills/`；
4. **调用这个 Skill**，学习了三个概念：`Agent`、`大模型的上下文`、`Skill`；
5. 对生成结果逐项核查修改，提交到本地 Git 仓库并 push 到 GitHub。

仓库里现在有两样东西：

- **一个可复用的 Skill** —— 以后学习任何新概念都能直接调用，不必重新写提示词；
- **三份学习资料 + 一份关系说明** —— 由这个 Skill 产出，格式统一、来源可核查。

---

## 2. 目录结构

```
concept-study-lab/
├── .workbuddy/
│   └── skills/
│       └── concept-study-kit/
│           └── SKILL.md              # 项目级 Skill（核心产物）
├── learning-materials/
│   ├── agent.html                    # 概念一：Agent
│   ├── llm-context.html              # 概念二：大模型的上下文
│   ├── skill.html                    # 概念三：Skill
│   ├── concept-relationship.md       # 三者关系说明（Markdown 源，含 Mermaid 图）
│   └── concept-relationship.html     # 三者关系说明（网页版，可直接浏览器打开）
├── README.md
└── .gitignore
```

---

## 3. Skill 说明

| 项目 | 内容 |
| --- | --- |
| 名称 | `concept-study-kit` |
| 存放路径 | `.workbuddy/skills/concept-study-kit/SKILL.md`（**项目级**，随仓库走） |
| 规范 | 遵循 [Agent Skills 开放标准](https://agentskills.io/specification)：`name` 与目录名一致、小写连字符；`description` 写清"做什么 + 何时用" |

`SKILL.md` 中完整定义了六件事：

1. **适用场景**（含"不适用"的边界，避免滥用）
2. **输入信息**（概念名、受众、深度、输出格式等 7 项，缺失时有默认值）
3. **生成步骤**（8 步：定位 → 检索 → 提炼 → 组织 → 辨析 → 自测 → 自检 → 交付）
4. **输出结构**（固定 8 个章节，每章都有硬性写作要求）
5. **资料来源要求**（可核查、一手优先、禁止伪造、禁止整段照搬、标注时间、区分事实与观点）
6. **自检要求**（10 项检查清单，不通过不许交付）

> **它不是为这三个概念写的一次性提示词。** 换成任意新概念（比如"向量数据库""RAG""多模态"），同一份 Skill 都能照流程跑出结构一致的资料。

---

## 4. 如何在 WorkBuddy 中调用这个 Skill

**前置条件**：用 WorkBuddy 打开本仓库目录（Skill 位于项目级目录，打开仓库即自动可用）。

**调用方式**（任选其一，直接对 WorkBuddy 说）：

```
用 concept-study-kit 学习「向量数据库」
```

```
用 concept-study-kit 学习「RAG 检索增强生成」，面向有 Python 基础的新手，
深度 standard，输出 HTML 到 learning-materials/rag.html，
重点关注「它和长上下文方案怎么选」。
```

也可以不点名，直接描述需求，Skill 会通过 `description` 被自动匹配：

```
帮我整理一份「MoE 混合专家模型」的学习笔记，要有机制和应用场景。
```

**调用后会发生什么**：命中 Skill → 读取 SKILL.md → 按 8 步流程检索来源、生成资料 → 跑 10 项自检 → 输出到 `learning-materials/`。

---

## 5. 已生成的学习资料

| 文件 | 概念 | 内容要点 |
| --- | --- | --- |
| [learning-materials/agent.html](learning-materials/agent.html) | **Agent** | 与 Workflow 的本质区别（控制流归属）、六部分构成、运行循环、退款排障场景、4 个常见误解 |
| [learning-materials/llm-context.html](learning-materials/llm-context.html) | **大模型的上下文** | 上下文装了什么、四层有限性（含 U 形位置偏差）、五种管理手段、代码库重构场景、6 个易混淆点 |
| [learning-materials/skill.html](learning-materials/skill.html) | **Skill** | 物理结构、元数据规范、三层渐进式披露、脚本即工具、本仓库 Skill 自身的复用案例 |
| [learning-materials/concept-relationship.md](learning-materials/concept-relationship.md) | **三者关系** | Mermaid 关系图 + 对照表，重点说明"上下文如何影响 Agent"与"Skill 如何沉淀知识" |

每份资料都包含：**学习目标 · 核心问题 · 我的理解（个人解释）· 核心机制 · 具体应用场景 · 易混淆问题与边界 · 5 道自测题（含答案）· 可核查来源**。

> 网页版直接用浏览器打开即可（纯内嵌 CSS，不依赖任何 CDN，离线可看）。

---

## 6. 三个概念的关系（简述）

> **上下文是 Agent 每一轮"能看到的世界"，Skill 是存放在这个世界之外、可按需取用的经验包。**

- **上下文 → Agent**：Agent 每轮的决策只能基于上下文中的内容；而它的循环会不断把工具结果塞回上下文，导致自我膨胀。所以上下文管理不是优化项，而是"Agent 能不能跑完"的决定项。
- **Skill → 上下文**：Skill 把知识放在文件系统里，通过三层渐进式披露按需注入上下文，从而在不撑爆窗口的前提下大幅扩展 Agent 的能力。
- **三者闭环**：Skill 让 Agent 更会做事 → Agent 产生大量上下文 → 上下文管理挑出值得留下的结论 → 沉淀成熟后固化为新的 Skill。

我的判断是：**上下文管理与 Skill 本质是同一个问题（如何在有限注意力预算里放入最有用的 token）的两个时间尺度**——前者管"本次会话"，后者管"跨任务复用"。详见 [concept-relationship.md](learning-materials/concept-relationship.md) 第 5 节。

---

## 7. 人工核查与修改记录（使用 AI 后我做了什么）

AI 生成的内容不能直接用。以下是本次**逐项人工核查**的结果：

### 7.1 来源核查（最重要）

- **逐条实际访问验证**：用 `curl` 对全部候选来源做可达性检查（HTTP 状态码），确认 200 才保留。
- **剔除了失效链接**：初稿计划引用的一篇官方文档页面返回 404，已直接删除，**未留在资料中**。
- **无法直连的补充 DOI**：`arxiv.org` 在本机网络环境不可达（连接超时），但该论文为规范引用，故**同时提供 DOI 链接**（`10.1162/tacl_a_00638`）以便核查，并在资料中如实说明了这一情况。
- **最终保留 12 条来源**，全部为官方工程博客、官方开发者文档、学术论文或开放标准规范，**无二手博客充数**。

### 7.2 内容修改

- **逐条比对规范原文**：`SKILL.md` 的字段规则不是凭印象写的，而是抓取 [agentskills.io/specification](https://agentskills.io/specification) 正文逐条核对（如 `name` ≤64 字符且必须与目录名一致、`description` ≤1024 字符）。
- **修正模糊表述**：初稿有一处把"上下文"与"记忆"混着说，已改为明确区分，并单列为易混淆点。
- **标注厂商自测数据**：资料中引用的性能提升数字（39% / 29% / 84%）来自厂商官方发布的自测结果，已显式标注"厂商自测、不宜跨产品对比"。
- **不写死易变数值**：上下文窗口大小随模型和版本变动，因此资料中**刻意不写任何具体数值**，改为提示"以官方文档为准"。
- **区分事实与个人观点**：所有推断性内容均标注"（我的判断）"，与来源事实分开，读者能一眼分辨。
- **统一格式**：三份资料的 8 段结构与样式完全对齐（由 Skill 的输出结构 + 自检清单保证）。

### 7.3 原创性

- 全部正文为**理解后的转述与个人类比**（如"办公桌""书架上的作业手册"），**未整段复制**任何来源原文。
- 直接引用仅用于必要处的短语，均标注出处。

### 7.4 安全检查

- 提交前确认：**无任何 API Key、密码、token、个人隐私信息**进入仓库。
- 本机 SSH **私钥从未进入仓库**（`.gitignore` 已排除 `id_ed25519`、`*.key`、`*.pem` 等）；SSH 公钥虽可公开，但亦未写入仓库文件。
- 未使用任何 PAT/token 完成推送，全程走 SSH 密钥认证。

---

## 8. 如何复现这套流程

```bash
# 1. 克隆仓库
git clone git@github.com:<你的用户名>/concept-study-lab.git
cd concept-study-lab

# 2. 用 WorkBuddy 打开该目录（Skill 会自动可用）

# 3. 调用 Skill 学习新概念（在 WorkBuddy 中说）
#    用 concept-study-kit 学习「向量数据库」

# 4. 提交与推送
git add -A
git commit -m "docs: 添加 XX 概念学习资料"
git push origin main
```

> 若 `git@github.com` 的 22 端口被网络阻断，本仓库所在机器的 SSH 配置已改用官方备用通道 `ssh.github.com:443`（见 `~/.ssh/config`）。

---

## 9. 后续可以做的事

- 用同一个 Skill 继续学习新概念，验证它的**通用性**（这是检验 Skill 是否合格的最好方式）。
- 把使用中发现的问题回写到 `SKILL.md`，形成"越用越准"的迭代闭环。
- 增加 `references/` 与 `scripts/`，把常用模板和检查脚本下沉，进一步压缩常驻上下文。

---

## 10. 许可与致谢

- 学习资料正文为个人学习笔记，引用内容版权归原作者所有，链接均已标注。
- 概念解释主要参考 Anthropic 工程博客、OpenAI 官方指南、Claude 官方文档、agentskills.io 开放标准规范及 Liu et al. 的学术论文，详见各资料末尾的"资料来源"章节。
