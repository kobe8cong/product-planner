# Product Planner v1.1 设计文档

## 🎯 核心改进

**从被动分析 → 主动发现 + 被动验证**

---

## 📋 新的用户体验流程

### 用户启动 `/product-plan`

```
Product Planner: AI Product Manager for Developers

I can help you in two ways:

1️⃣  Discover Opportunities
    I'll analyze market trends, identify gaps, and recommend 
    project ideas that match your skills and goals.
    
    → Choose this if you're looking for ideas

2️⃣  Validate Your Idea
    I'll analyze your existing project idea with market research,
    competitor analysis, and strategic planning.
    
    → Choose this if you already have an idea

Which mode would you like?
```

---

## 🆕 Mode 1: Discovery Mode（发现模式）

### Workflow

```
User Input → Context Collection → Opportunity Analysis → Recommendations → Deep Dive
```

### Phase 0: Context Collection（收集背景）

**Questions:**
```
Let me understand your context:

1. Your Skills & Experience
   - Primary tech stack? (e.g., JavaScript/TypeScript, Python, Go)
   - Years of experience? (Beginner / Intermediate / Expert)
   - Team or solo? (Solo / Small team / Have team)

2. Available Resources
   - Time commitment? (5-10h/week, 10-20h/week, 20+h/week, full-time)
   - Budget for APIs/services? (Free only, <$50/mo, <$200/mo, flexible)
   - Existing audience? (GitHub followers, Twitter, blog readers)

3. Your Goals (select all that apply)
   a) Build portfolio / Get GitHub stars
   b) Generate income / Build a business
   c) Learn new technologies
   d) Solve a personal pain point
   e) Contribute to open source ecosystem

4. Interest Areas (select up to 3)
   a) AI / Machine Learning
   b) Developer Tools
   c) Productivity / Automation
   d) Web3 / Blockchain
   e) SaaS / B2B Tools
   f) Open Source Infrastructure
   g) Content / Media Tools
   h) Other: [specify]

5. Constraints / Preferences
   - Any topics you want to avoid?
   - Must be open source? Or can be commercial?
   - Prefer CLI, Web, or doesn't matter?
```

### Phase 1: Market & Trend Analysis（市场趋势分析）

**Launch Agent: trend-analyzer**

**职责：**
- 扫描当前技术趋势
- 识别市场痛点
- 发现竞争空白

**数据源：**
- GitHub Trending repositories
- Hacker News front page & discussions
- Reddit (r/SideProject, r/opensource, r/programming)
- Product Hunt recent launches
- Stack Overflow trends
- Tech Twitter discussions

**输出：**
```markdown
# Trend Analysis Report

## Hot Trends (Rising Interest)
1. **[Trend Name]**
   - What: [Description]
   - Why hot: [Growth indicators]
   - Opportunity: [What's missing]

## Pain Points (Recurring Complaints)
1. **[Pain Point]**
   - Where observed: [Platform/community]
   - Frequency: High/Medium
   - Current solutions: [Existing but inadequate]

## Technology Opportunities (New Capabilities)
1. **[Technology]**
   - What's new: [Capability]
   - Unlocks: [New possibilities]
   - Adoption: Early/Growing/Mainstream
```

### Phase 2: Opportunity Identification（机会识别）

**Launch Agent: opportunity-scout**

**职责：**
- 基于趋势分析，识别具体项目方向
- 评估每个方向的可行性
- 匹配用户背景和目标

**分析框架：**

**机会评分矩阵：**
```
Market Demand (1-10)    × 0.25
Competition Level (1-10) × 0.20  [低竞争得高分]
Technical Fit (1-10)    × 0.20
Time to MVP (1-10)      × 0.15  [快速得高分]
Ecosystem Value (1-10)  × 0.20

Total: Opportunity Score (1-100)
```

**输出：**
```markdown
# Discovered Opportunities

## Top 5 Opportunities (Ranked by Score)

### Opportunity #1: [Project Name/Direction]
**Opportunity Score: 85/100**

**What:** [1-2 sentence description]

**Why Now:**
- Trend: [Related to which trend]
- Pain: [Which pain point it solves]
- Gap: [What's missing in current market]

**Target Users:**
- [Primary persona]
- [Market size estimate]

**Competition:**
- Direct competitors: [X found]
- Competition level: Low/Medium/High
- Your advantage: [Differentiation angle]

**Feasibility:**
- Technical fit: ⭐⭐⭐⭐⭐ (matches your skills)
- Time to MVP: ~2 weeks
- Required resources: Minimal / Moderate / Significant
- Risk level: Low / Medium / High

**Potential Outcome:**
- GitHub stars potential: [Estimate based on similar projects]
- Monetization potential: [If applicable]
- Ecosystem impact: [Value to community]

**Why This Scores High:**
- [Specific reason 1]
- [Specific reason 2]

**Risks/Considerations:**
- [Risk 1]
- [Mitigation]

---

[Repeat for Opportunity #2-5]
```

### Phase 3: User Selection & Deep Dive

**Present to User:**
```
Based on your context, I've identified 5 high-potential opportunities.

Here are your top 3 recommendations:

🥇 #1: [Name] (Score: 85)
    [One-line description]
    Best fit because: [Reason]

🥈 #2: [Name] (Score: 78)
    [One-line description]
    Best fit because: [Reason]

🥉 #3: [Name] (Score: 72)
    [One-line description]
    Best fit because: [Reason]

Want to see:
a) Full details on all 5 opportunities
b) Deep dive into #1
c) Deep dive into #2
d) Deep dive into #3
e) Different direction (tell me what)
```

**If user chooses to deep dive:**
→ Switch to Validation Mode for that specific idea
→ Run full 5-phase analysis (Market Research, Product Definition, Roadmap, Metrics, GTM)

---

## ✅ Mode 2: Validation Mode（验证模式）

### 这是原有的流程，但增加快速验证：

### Phase 0.5: Quick Validation（快速验证）

**在详细分析前，先判断：**

**Launch Agent: idea-validator**

**职责：**
- 快速判断这个想法的时效性
- 识别明显的红旗
- 给出继续/调整/放弃的建议

**分析：**
```markdown
# Quick Validation

## Idea: [User's project idea]

## Time Sensitivity Check
- Is this problem still relevant? ✅/⚠️/❌
- Has the market moved on? (e.g., AI tools now solve this)
- Evidence: [Specific observations]

## Market Saturation Check
- Number of similar solutions: [X found]
- Market maturity: Emerging / Growing / Mature / Saturated
- Adoption of existing solutions: Low / Medium / High

## Red Flags
- ⚠️ [Flag 1, if any]
- ⚠️ [Flag 2, if any]

## Initial Assessment
🟢 Promising - Recommend full analysis
🟡 Proceed with caution - [Specific concern]
🔴 Not recommended - [Reason] → Consider these alternatives: [X, Y, Z]

## Recommendation
[Continue with full analysis / Adjust focus / Consider alternatives]
```

**If 🔴 Not recommended:**
→ Offer to switch to Discovery Mode
→ Or adjust the idea based on findings

**If 🟢 or 🟡:**
→ Continue with Phase 1-5 (existing flow)

---

## 🆕 New Agents

### 1. trend-analyzer.md
- 分析市场趋势
- 识别技术机会
- 发现用户痛点

### 2. opportunity-scout.md
- 识别具体项目方向
- 评分和排序
- 匹配用户背景

### 3. idea-validator.md
- 快速验证想法
- 红旗检测
- 继续/调整/放弃建议

---

## 📝 Updated SKILL.md

### New Command Structure

```bash
# Discovery Mode - Find opportunities
/product-plan discover

# Validation Mode - Analyze your idea
/product-plan validate [your idea]

# Legacy support (shows mode selection)
/product-plan
/product-plan [your idea]  # defaults to validation mode
```

### New User Flow

```
/product-plan
  ↓
Mode Selection
  ↓
┌─────────┴─────────┐
│                   │
Discovery       Validation
Mode            Mode
│                   │
↓                   ↓
Context         Quick Validation
Collection          ↓
↓               🟢 Continue?
Trend Analysis      ↓
↓               Phase 1-5
Opportunity     (existing)
Scout               ↓
↓               Generate PRD
Top 5               
Recommendations
↓
User Selects
↓
Deep Dive
(Phase 1-5)
↓
Generate PRD
```

---

## 🎯 v1.1 Implementation Plan

### Step 1: Create New Agents (优先)
- [ ] `agents/trend-analyzer.md`
- [ ] `agents/opportunity-scout.md`
- [ ] `agents/idea-validator.md`

### Step 2: Update SKILL.md
- [ ] Add mode selection at start
- [ ] Add Discovery Mode workflow
- [ ] Add Quick Validation in Validation Mode
- [ ] Update command structure

### Step 3: Update Documentation
- [ ] Update README.md with new modes
- [ ] Update examples with Discovery Mode output
- [ ] Add v1.1 to CHANGELOG.md

### Step 4: Test
- [ ] Test Discovery Mode with different user contexts
- [ ] Test Quick Validation with various ideas
- [ ] Test mode switching

### Step 5: Release
- [ ] Update version to v1.1.0
- [ ] Create GitHub release
- [ ] Update announcement materials

---

## 📊 Expected Impact

### For Users:
✅ 不需要自己想项目了
✅ 获得数据驱动的建议
✅ 避免浪费时间在过时的想法上
✅ 更高的项目成功率

### For Product Planner:
✅ 从"工具"变成"顾问"
✅ 更主动、更有价值
✅ 差异化竞争优势
✅ 更符合"Product Manager"定位

---

## 🚀 Next Steps

立即开始实现 v1.1：
1. 创建 3 个新 agents
2. 更新 SKILL.md
3. 测试验证
4. 发布更新

**预计时间：** 2-3 小时
**价值：** 质的飞跃

---

**准备好开始实现了吗？** 🎯
