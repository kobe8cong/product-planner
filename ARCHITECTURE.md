# Product Planner - 技术架构设计

## 📐 架构概述

### 设计原则
1. **模块化** - 每个分析阶段独立，易于测试和扩展
2. **可组合** - 用户可以单独运行某个阶段
3. **可扩展** - 易于添加新的分析维度
4. **轻量级** - 最小化依赖，快速安装
5. **开发者友好** - 清晰的代码结构，完善的文档

---

## 🏗️ 系统架构

### 整体架构图

```
┌─────────────────────────────────────────────────────────┐
│                   Claude Code CLI                        │
│                   /product-plan                          │
└──────────────────────┬──────────────────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────────────┐
│              Product Planner Plugin                      │
├─────────────────────────────────────────────────────────┤
│  Entry Point: SKILL.md                                   │
│  ├─ Command Handler                                      │
│  ├─ Workflow Orchestrator                                │
│  └─ State Manager                                        │
└──────────────────────┬──────────────────────────────────┘
                       │
        ┌──────────────┼──────────────┐
        ▼              ▼              ▼
┌─────────────┐ ┌─────────────┐ ┌─────────────┐
│   Phase 1   │ │   Phase 2   │ │   Phase 3   │
│   项目理解   │ │   市场研究   │ │   产品定义   │
└─────────────┘ └─────────────┘ └─────────────┘
        │              │              │
        ▼              ▼              ▼
┌─────────────┐ ┌─────────────┐ ┌─────────────┐
│   Phase 4   │ │   Phase 5   │ │   Output    │
│   路线图    │ │ 成功指标+GTM │ │   生成器    │
└─────────────┘ └─────────────┘ └─────────────┘
                                       │
                       ┌───────────────┴───────────────┐
                       ▼                               ▼
                ┌─────────────┐               ┌─────────────┐
                │  PRD.md     │               │  Artifacts  │
                │  生成       │               │  (可选)     │
                └─────────────┘               └─────────────┘
```

---

## 📦 目录结构

```
product-planner/
├── README.md                    # 项目说明
├── LICENSE                      # MIT License
├── CLAUDE.md                    # Plugin 元信息
├── SKILL.md                     # Skill 入口点
├── PRODUCT_ANALYSIS.md          # 本项目的产品分析
├── ARCHITECTURE.md              # 本文档
├── CONTRIBUTING.md              # 贡献指南
├── CHANGELOG.md                 # 版本历史
│
├── agents/                      # Agent 定义
│   ├── market-researcher.md    # 市场研究 agent
│   ├── competitor-analyzer.md  # 竞品分析 agent
│   └── product-strategist.md   # 产品策略 agent
│
├── phases/                      # 阶段实现（可选，如需细分）
│   ├── phase1-understanding.md
│   ├── phase2-market-research.md
│   ├── phase3-product-definition.md
│   ├── phase4-roadmap.md
│   └── phase5-success-metrics.md
│
├── templates/                   # 输出模板
│   ├── prd-template.md
│   ├── roadmap-template.md
│   └── competitor-matrix-template.md
│
├── examples/                    # 使用示例
│   ├── example-saas-product/
│   ├── example-cli-tool/
│   └── example-open-source-lib/
│
└── docs/                        # 额外文档
    ├── user-guide.md
    ├── best-practices.md
    └── faq.md
```

---

## 🎯 核心组件设计

### 1. SKILL.md - 入口点

**职责：**
- 定义 `/product-plan` 命令
- 接收用户输入
- 编排整个工作流
- 处理用户交互

**实现要点：**
```markdown
# Product Planner Skill

## Command: /product-plan

**Usage:**
- `/product-plan` - 交互式引导
- `/product-plan [项目描述]` - 直接开始
- `/product-plan --help` - 查看帮助

**Workflow:**
1. 收集项目信息
2. 运行 5 阶段分析
3. 生成完整 PRD
4. 保存到项目目录
```

**工作流逻辑：**
1. **输入验证** - 检查项目描述是否足够
2. **Phase 1: 项目理解** - 澄清模糊需求
3. **Phase 2-5** - 顺序执行各阶段
4. **输出生成** - 创建 PRD 和相关文档
5. **保存** - 写入 `docs/product/` 目录

### 2. Agents 设计

#### Agent 1: market-researcher (市场研究员)

**职责：**
- 分析市场规模和趋势
- 识别目标用户群体
- 评估市场机会

**输入：**
- 项目描述
- 产品类别
- 目标市场

**输出：**
```markdown
# Market Research Report

## Market Size & Trends
- Total Addressable Market (TAM)
- Current trends and drivers
- Growth projections

## Target Users
- Primary user personas (2-3)
- Secondary audiences
- User pain points

## Opportunities
- Market gaps
- Underserved segments
- Timing advantages
```

**实现策略：**
- 使用 WebSearch 获取市场数据
- 分析 GitHub trending、Product Hunt 等平台
- 结合已知数据和推理

#### Agent 2: competitor-analyzer (竞品分析师)

**职责：**
- 发现相关竞品
- 深度对比分析
- 识别差异化机会

**输入：**
- 项目描述
- 产品类别

**输出：**
```markdown
# Competitor Analysis

## Identified Competitors
1. Competitor A - [description]
2. Competitor B - [description]
3. Competitor C - [description]

## Feature Comparison Matrix
| Feature | Us | Competitor A | Competitor B | Competitor C |
|---------|----|--------------|--------------| -------------|
| ...     |    |              |              |              |

## Competitive Advantages
- Our unique value props
- Gaps in competitor offerings
- Positioning strategy

## Threats
- Competitive risks
- Market saturation concerns
```

**实现策略：**
- GitHub search for similar projects
- WebSearch for commercial alternatives
- 分析 stars、forks、issues 活跃度
- 对比功能和定位

#### Agent 3: product-strategist (产品策略师)

**职责：**
- 综合所有分析
- 定义产品策略
- 制定路线图

**输入：**
- 市场研究报告
- 竞品分析报告
- 项目约束条件

**输出：**
```markdown
# Product Strategy

## Value Proposition
- One-liner
- Core benefits
- Target audience fit

## MVP Definition
- Must-have features
- Nice-to-have features
- Out-of-scope features

## Product Roadmap
### v1.0 - MVP (Timeline)
- Feature list
- Success criteria

### v2.0+ - Evolution
- Future enhancements
- Scaling strategy

## Success Metrics
- North Star Metric
- Key Performance Indicators
- Milestone targets
```

### 3. Phase 实现设计

每个 Phase 是一个独立的分析单元：

#### Phase 1: 项目理解 (Understanding)

**目标：** 确保需求清晰、完整

**流程：**
1. 接收初始项目描述
2. 提出澄清问题：
   - 目标用户是谁？
   - 要解决什么问题？
   - 有什么约束条件？
   - 时间和资源限制？
3. 总结项目定义
4. 确认理解正确

**输出：** `project-brief.md`

#### Phase 2: 市场研究 (Market Research)

**目标：** 理解市场环境和机会

**流程：**
1. **并行启动 2 个 agents：**
   - `market-researcher` - 市场分析
   - `competitor-analyzer` - 竞品分析
2. 综合两个 agent 的输出
3. 识别关键洞察
4. 生成市场研究报告

**输出：** `market-research.md`

**技术实现：**
```typescript
// 伪代码示例
async function phase2_marketResearch(projectBrief) {
  // 并行启动 agents
  const [marketReport, competitorReport] = await Promise.all([
    launchAgent('market-researcher', projectBrief),
    launchAgent('competitor-analyzer', projectBrief)
  ]);
  
  // 综合分析
  const synthesis = synthesizeResearch(marketReport, competitorReport);
  
  // 生成报告
  return generateMarketReport(synthesis);
}
```

#### Phase 3: 产品定义 (Product Definition)

**目标：** 明确产品核心和 MVP

**流程：**
1. 基于市场研究定义价值主张
2. 创建用户画像 (2-3 个 personas)
3. 列举所有可能功能
4. 使用价值 vs 成本矩阵排序
5. 定义 MVP 范围
6. **用户确认** MVP 定义

**输出：** `product-definition.md`

**功能优先级矩阵：**
```markdown
| 功能 | 用户价值 | 开发成本 | 优先级 | MVP |
|-----|---------|---------|--------|-----|
| ... | ⭐⭐⭐⭐⭐ | 🔨🔨🔨 | P0 | ✅ |
```

#### Phase 4: 路线图规划 (Roadmap)

**目标：** 制定分阶段实施计划

**流程：**
1. 定义 v1.0 MVP 范围和时间
2. 规划 v1.1, v2.0 演进路径
3. 评估技术可行性
4. 估算资源需求
5. 识别关键里程碑

**输出：** `roadmap.md`

#### Phase 5: 成功指标与 GTM (Success Metrics & GTM)

**目标：** 定义成功标准和发布策略

**流程：**
1. 定义北极星指标
2. 设置 KPI 体系
3. 制定里程碑目标
4. 规划 Go-to-Market 策略
5. 确定推广渠道和时间表

**输出：** `success-metrics.md` + `gtm-strategy.md`

### 4. 输出生成器 (Output Generator)

**职责：** 将所有分析整合成结构化文档

**生成文档：**

1. **PRD.md** - 完整产品需求文档
   - 整合所有 5 个阶段的输出
   - 专业的格式和结构
   - 包含所有关键决策和依据

2. **ROADMAP.md** - 可视化路线图
   - 版本演进计划
   - 时间线和里程碑
   - 功能优先级

3. **METRICS.md** - 成功指标追踪
   - KPI 定义
   - 测量方法
   - 目标值和当前值

4. **README-template.md** - 项目 README 模板
   - 基于 PRD 生成
   - 包含核心价值主张
   - 快速上手指南

**文件组织：**
```
your-project/
└── docs/
    └── product/
        ├── PRD.md                 # 主文档
        ├── market-research.md     # 详细市场分析
        ├── competitor-analysis.md # 竞品分析
        ├── roadmap.md            # 路线图
        ├── success-metrics.md    # 成功指标
        └── gtm-strategy.md       # GTM 策略
```

---

## 🔧 技术实现细节

### 使用的 Claude Code 能力

1. **Agent 系统**
   ```markdown
   Launch multiple agents in parallel for thorough analysis:
   - market-researcher
   - competitor-analyzer
   - product-strategist
   ```

2. **工具调用**
   - `WebSearch` - 市场数据和竞品搜索
   - `WebFetch` - 获取竞品详细信息
   - `Grep` / `Glob` - 分析现有代码（如果项目已存在）
   - `Write` - 生成文档
   - `AskUserQuestion` - 用户交互

3. **状态管理**
   - 使用临时文件保存中间结果
   - 可选：使用 `.product-planner/` 目录缓存

### 数据流

```
User Input
    ↓
[Phase 1] → project-brief.json
    ↓
[Phase 2] → market-research.json + competitor-analysis.json
    ↓
[Phase 3] → product-definition.json
    ↓
[Phase 4] → roadmap.json
    ↓
[Phase 5] → success-metrics.json + gtm-strategy.json
    ↓
[Output Generator] → PRD.md + other docs
```

### 错误处理

1. **输入验证**
   - 项目描述不能为空
   - 必要信息缺失时提示用户

2. **Agent 失败重试**
   - Agent 超时：重试 1 次
   - Agent 返回不完整：请求补充

3. **用户中断**
   - 保存当前进度
   - 下次可以从中断处继续

### 性能优化

1. **并行执行**
   - Phase 2 的两个 agents 并行
   - 独立的分析任务并行

2. **缓存机制**
   - 竞品信息缓存（避免重复搜索）
   - 市场数据缓存（时效性：24小时）

3. **增量更新**
   - 支持更新已有分析
   - 只重新运行需要更新的部分

---

## 🎨 用户体验设计

### 命令交互流程

```
$ /product-plan

Product Planner: AI Product Manager for Developers

I'll help you create a comprehensive product plan.

What's your project idea? (Describe in 1-2 sentences)
> An AI-powered git commit message generator

Great! Let me understand your project better...

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Phase 1/5: Understanding Your Project

I need to clarify a few things:

1. Target users?
   a) All developers
   b) Enterprise teams
   c) Open source maintainers
   d) Specific language/framework developers

> a

2. Primary goal?
   a) Save time writing commits
   b) Enforce commit conventions
   c) Improve commit quality
   d) All of the above

> d

... [more questions]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Phase 2/5: Market Research

🔍 Analyzing market and competitors...

[Progress indicators]
✓ Market size analysis
✓ Competitor discovery (found 5 similar projects)
✓ User research

Key Findings:
• Market: 100M+ developers, growing AI tools adoption
• Main competitors: Conventional Commits, commitizen
• Gap: AI-powered, zero-config solutions

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Phase 3/5: Product Definition

Based on research, here's the MVP:

Core Features (Must-have):
✓ AI commit message generation
✓ Multiple commit formats
✓ CLI interface

Your MVP scope looks good? (yes/no/adjust)
> yes

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Phase 4/5: Roadmap

v1.0 MVP (2 weeks)
└─ Basic AI generation
└─ CLI tool
└─ 3 formats support

v1.1 (1 week)
└─ Git hooks integration

v2.0 (1 month)
└─ Team conventions learning
└─ Editor plugins

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Phase 5/5: Success Metrics & GTM

North Star Metric:
📊 Weekly active users completing commits

Launch Plan:
Week 1: GitHub + Reddit
Week 2: HN + Dev.to
Week 3: Product Hunt

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

✅ Product Plan Complete!

Generated documents:
📄 docs/product/PRD.md
📄 docs/product/roadmap.md
📄 docs/product/success-metrics.md

Next steps:
1. Review the PRD
2. Start with MVP features
3. Set up project structure

Ready to build something great! 🚀
```

### 进度可视化

使用 Unicode 字符增强体验：
```
Phase 2/5: Market Research
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

⠋ Researching market size...
✓ Market analysis complete
⠙ Finding competitors...
✓ Found 5 competitors
⠹ Analyzing trends...
✓ Research complete

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## 🧪 测试策略

### 单元测试

**测试 Phase 逻辑：**
- Phase 1: 问题生成和验证
- Phase 2: Agent 输出解析
- Phase 3: 功能优先级算法
- Phase 4: 路线图生成
- Phase 5: KPI 定义

### 集成测试

**端到端测试：**
1. 使用预定义输入运行完整流程
2. 验证输出文档格式
3. 检查所有必需部分存在

**测试用例：**
- SaaS 产品
- CLI 工具
- 开源库
- 移动应用

### 自我验证

**狗粮测试：**
用 Product Planner 分析一个新项目（如 `ai-commit`），验证：
- 分析深度足够
- 建议可执行
- 文档专业
- 用户体验流畅

---

## 📈 可扩展性设计

### 插件化架构

**支持自定义 Agents：**
```markdown
# Custom Agent: pricing-strategist

用户可以在 `agents/` 目录添加自己的分析维度
```

### 配置化

**`.product-planner.config.json`:**
```json
{
  "phases": ["understanding", "market", "product", "roadmap", "metrics"],
  "enabledAgents": ["market-researcher", "competitor-analyzer"],
  "outputDir": "docs/product",
  "templates": {
    "prd": "custom-prd-template.md"
  }
}
```

### 模板自定义

用户可以提供自己的模板：
- PRD 模板
- 路线图模板
- 竞品分析模板

---

## 🔐 安全与隐私

### 数据处理

1. **本地优先**
   - 所有分析在本地完成
   - 不向第三方发送敏感信息

2. **API 调用**
   - 仅使用 Claude API（用户已授权）
   - WebSearch 使用公开数据

3. **缓存管理**
   - 缓存数据存储在 `.product-planner/cache/`
   - 用户可以清除缓存

### 凭证管理

- 不存储任何 API keys
- 依赖 Claude Code 的认证机制

---

## 📚 文档策略

### 用户文档

1. **README.md** - 快速开始
2. **docs/user-guide.md** - 完整指南
3. **docs/examples/** - 使用示例
4. **docs/faq.md** - 常见问题

### 开发者文档

1. **ARCHITECTURE.md** (本文档)
2. **CONTRIBUTING.md** - 贡献指南
3. **docs/api.md** - API 文档
4. **Code comments** - 代码注释

---

## 🚀 部署与发布

### 发布流程

1. **开发完成**
   - 所有功能实现
   - 测试通过
   - 文档完善

2. **版本标记**
   ```bash
   git tag -a v1.0.0 -m "First stable release"
   git push origin v1.0.0
   ```

3. **GitHub Release**
   - 创建 Release
   - 添加 Release Notes
   - 附上安装说明

4. **社区提交**
   - 提交到 Claude Code plugin 市场
   - 发布到 npm (如果需要)

### 安装方式

**方式 1: 通过 Claude Code 市场**
```bash
# 未来支持
/plugin install product-planner
```

**方式 2: Git Clone**
```bash
cd ~/.claude/skills/
git clone https://github.com/kobe8cong/product-planner.git
```

**方式 3: 手动下载**
```bash
# Download and extract to ~/.claude/skills/product-planner/
```

---

## 🔄 维护与演进

### 版本管理

**语义化版本：**
- v1.0.0 - 首个稳定版
- v1.1.0 - 增加功能
- v1.1.1 - Bug 修复
- v2.0.0 - 重大变更

### 反馈收集

1. **GitHub Issues** - Bug 报告和功能请求
2. **Discussions** - 用户讨论
3. **定期调研** - 用户满意度

### 持续改进

- 每月回顾使用数据
- 根据反馈优先级迭代
- 保持与 Claude Code 更新同步

---

## 🎯 下一步行动

**立即开始实现：**

1. **创建项目结构**
   - 初始化目录
   - 创建基础文件

2. **实现 SKILL.md**
   - 定义命令入口
   - 编写主工作流

3. **实现 Agents**
   - market-researcher
   - competitor-analyzer
   - product-strategist

4. **实现 Phases**
   - 5 个阶段逻辑

5. **输出生成**
   - PRD 模板
   - 文档生成器

6. **测试验证**
   - 自我验证
   - 示例项目测试

**预计时间：** 1-2 天完成 MVP

---

**架构设计完成时间：** 2026-06-27  
**下一步：** 开始 MVP 开发  
**负责人：** Claude (kobe8cong workspace)
