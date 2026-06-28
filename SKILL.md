# Product Planner

AI Product Manager for Developers - Discover opportunities or validate your ideas with data-driven analysis.

## Overview

Product Planner brings systematic product thinking to your development workflow. It can **actively discover** high-potential project opportunities based on market trends, or **validate** your existing ideas through comprehensive research. Powered by AI and integrated seamlessly into Claude Code.

## Command

### `/product-plan [optional: project description]`

Launch Product Planner in one of two modes:

**Usage:**
```bash
# Interactive mode - choose Discovery or Validation
/product-plan

# Discovery mode - find opportunities for you
/product-plan discover

# Validation mode - analyze your idea
/product-plan validate [your project idea]

# Legacy support - defaults to mode selection
/product-plan An AI-powered CLI tool for generating git commit messages

# Show help
/product-plan --help
```

## What It Does

Product Planner offers **two powerful modes**:

---

### 🔍 Discovery Mode - Find Opportunities

Can't decide what to build? Let Product Planner discover opportunities for you.

**Workflow:**
1. **Context Collection** - Understand your skills, time, goals, interests
2. **Trend Analysis** - Scan GitHub, Hacker News, Reddit, Product Hunt for trends
3. **Opportunity Scout** - Identify 5+ concrete project ideas, score them
4. **Recommendations** - Present top 3 opportunities with detailed analysis
5. **Deep Dive** - Choose one to run full product analysis

**Launches 2 agents in parallel:**
- `trend-analyzer` - Market trends and pain point discovery
- `opportunity-scout` - Project identification and scoring

**Best for:**
- Looking for your next project idea
- Want data-driven recommendations
- Curious what's hot in the market
- Need validation before committing to an idea

---

### ✅ Validation Mode - Analyze Your Idea

Have an idea? Let Product Planner validate it thoroughly.

**Workflow:**
1. **Quick Validation** - Rapid assessment (is this still relevant? any red flags?)
2. **Market Research** - Deep dive into market, users, competitors
3. **Product Definition** - Value prop, features, MVP scope
4. **Roadmap Planning** - Version evolution and timelines
5. **Success Metrics & GTM** - KPIs and launch strategy

**Phase 0: Quick Validation (NEW)**
- **Launches:** `idea-validator` agent
- Checks if idea is obsolete (e.g., AI now does this automatically)
- Identifies red flags before investing time
- Recommends: Continue / Adjust / Try Discovery Mode instead

**If validation passes:**

**Phase 1: Project Understanding 🎯**
- Clarifies your project vision
- Identifies target users and goals
- Defines constraints and requirements

**Phase 2: Market Research 📊**
- Analyzes market size and trends
- Identifies target user personas
- Discovers and analyzes competitors
- Finds market opportunities and gaps

**Launches 2 agents in parallel:**
- `market-researcher` - Market and user analysis
- `competitor-analyzer` - Competitive intelligence

**Phase 3: Product Definition 💎**
- Defines core value proposition
- Creates user personas and pain points
- Generates comprehensive feature list
- Prioritizes features using value vs. cost matrix
- Defines MVP scope

**Asks for your confirmation before proceeding.**

**Phase 4: Roadmap Planning 🗺️**
- Defines v1.0 MVP timeline and scope
- Plans v1.1, v2.0+ evolution
- Assesses technical feasibility
- Estimates resources and risks
- Sets milestone targets

**Phase 5: Success Metrics & GTM 📈**
- Defines North Star Metric
- Sets up KPI framework
- Creates measurement plan
- Designs Go-to-Market strategy
- Recommends launch channels and timing

**Best for:**
- You have a specific idea to analyze
- Want to validate before building
- Need comprehensive product planning
- Creating PRD for team/investors

## Output

Product Planner generates professional, structured documentation saved to `docs/product/`:

```
your-project/
└── docs/
    └── product/
        ├── PRD.md                    # Complete Product Requirements Document
        ├── market-research.md        # Detailed market analysis
        ├── competitor-analysis.md    # Competitive intelligence
        ├── product-definition.md     # MVP and feature specifications
        ├── roadmap.md               # Version evolution plan
        ├── success-metrics.md       # KPIs and measurement framework
        └── gtm-strategy.md          # Go-to-Market plan
```

## When to Use

**Perfect for:**
- 💡 Starting a new side project
- 🚀 Launching an open source project
- 📦 Building a SaaS product
- 🔧 Creating developer tools
- 📱 Planning a mobile app

**Especially valuable when:**
- You have an idea but unsure if it's worth building
- You want to validate market fit before coding
- You need to prioritize features with limited resources
- You're applying for funding or partnerships
- You want to attract contributors to your open source project

**Skip it for:**
- Quick bug fixes
- Well-defined maintenance tasks
- Proof-of-concept experiments where research isn't needed

## Workflow

### Discovery Mode Flow
```
/product-plan discover
         ↓
  Mode: Discovery
         ↓
Context Collection
  (skills, goals, time, interests)
         ↓
  Trend Analysis
  ↓ (parallel agents)
├─ trend-analyzer (market trends)
└─ opportunity-scout (score projects)
         ↓
 Top 5 Opportunities
   (ranked by score)
         ↓
   User Selects
         ↓
    Deep Dive
  (run Validation Mode phases 1-5)
         ↓
   Generate PRD
```

### Validation Mode Flow
```
/product-plan validate [idea]
         ↓
   Mode: Validation
         ↓
  Quick Validation
  ↓ (idea-validator)
[Check relevance, demand, red flags]
         ↓
  🟢 Pass / 🟡 Caution / 🔴 Stop
         ↓
    [If Pass]
         ↓
    [Phase 1]
Project Understanding
  ↓ (clarifying questions)
User Answers
         ↓
    [Phase 2]
  Market Research
  ↓ (2 agents parallel)
├─ market-researcher
└─ competitor-analyzer
         ↓
    [Phase 3]
 Product Definition
  ↓ (user confirms MVP)
User Approval
         ↓
    [Phase 4]
   Roadmap Planning
         ↓
    [Phase 5]
Success Metrics & GTM
         ↓
   Generate PRD
         ↓
Save to docs/product/
```

## Example Output

Here's what a generated PRD includes:

- **Executive Summary** - One-page project overview
- **Market Analysis** - TAM, trends, opportunities
- **Competitive Landscape** - Competitor comparison matrix
- **User Research** - Personas, pain points, use cases
- **Value Proposition** - Why users should care
- **Feature Specifications** - Detailed feature list with priorities
- **MVP Definition** - Minimum viable product scope
- **Product Roadmap** - Multi-version evolution plan
- **Success Metrics** - KPIs and measurement plan
- **Go-to-Market** - Launch strategy and channels
- **Risk Assessment** - Potential challenges and mitigation

## AI Agents

Product Planner uses specialized AI agents for deep analysis:

### Discovery Mode Agents

#### trend-analyzer
Analyzes market dynamics and emerging opportunities:
- Scans GitHub Trending, Hacker News, Reddit, Product Hunt
- Identifies hot trends, pain points, technology opportunities
- Discovers market gaps with validated demand
- Ranks findings by relevance to user context

#### opportunity-scout
Transforms trends into concrete project opportunities:
- Generates 5+ specific project ideas
- Evaluates feasibility and competition
- Scores using multi-dimensional matrix
- Matches opportunities to user skills and goals

### Validation Mode Agents

#### idea-validator
Quick validation and red flag detection:
- Checks if idea is still relevant (technology displacement)
- Validates market demand with evidence
- Assesses competition saturation
- Identifies blocking issues early
- Recommends: Go / Caution / Stop

#### market-researcher
Analyzes market dynamics and user needs:
- Market size estimation (TAM/SAM/SOM)
- Trend analysis and drivers
- User persona generation
- Pain point identification

#### competitor-analyzer
Provides competitive intelligence:
- Discovers similar products/projects
- Analyzes features and positioning
- Compares GitHub metrics (stars, activity)
- Identifies differentiation opportunities

#### product-strategist
Synthesizes insights into strategy:
- Defines value proposition
- Prioritizes features
- Plans roadmap phases
- Sets success criteria

## Features

✅ **Dual Mode System** - Discover opportunities OR validate your ideas  
✅ **Proactive Discovery** - AI suggests projects based on market analysis  
✅ **Quick Validation** - Detect obsolete ideas and red flags early  
✅ **Comprehensive Analysis** - Covers market, competition, product, and strategy  
✅ **Data-Driven** - Uses real market data and competitive intelligence  
✅ **Structured Output** - Professional PRD format ready to share  
✅ **Interactive** - Asks clarifying questions to understand your vision  
✅ **Fast** - Discovery in 10-15 min, Validation in 15-20 min  
✅ **Integrated** - Works seamlessly in your Claude Code workflow  
✅ **Flexible** - Can update existing plans or start fresh  
✅ **Export-Friendly** - Markdown format, easy to share and version control  

## Tips for Best Results

1. **Be specific in your initial description**
   - Include the problem you're solving
   - Mention target users if known
   - Note any constraints (time, budget, tech)

2. **Answer clarifying questions thoughtfully**
   - Phase 1 questions shape the entire analysis
   - Be honest about uncertainties
   - Say "not sure, recommend" if you want suggestions

3. **Review competitor analysis carefully**
   - The tool finds competitors, but you know your market best
   - Note any missing competitors in your PRD

4. **Adjust MVP scope realistically**
   - Phase 3 proposes an MVP - you can expand or trim it
   - Consider your actual time and resources

5. **Use the PRD as a living document**
   - Update it as you learn from users
   - Run `/product-plan` again to refresh analysis

## Configuration

Product Planner works out of the box, but you can customize it:

Create `.product-planner.json` in your project root:

```json
{
  "outputDir": "docs/product",
  "phases": ["understanding", "market", "product", "roadmap", "metrics"],
  "enabledAgents": ["market-researcher", "competitor-analyzer", "product-strategist"],
  "templates": {
    "prd": "templates/custom-prd.md"
  }
}
```

## Requirements

- Claude Code CLI or Desktop App
- Internet connection (for market research and competitor analysis)
- Git repository (recommended for version control)

## Examples

See `examples/` directory for complete product plans generated by Product Planner:
- `examples/example-cli-tool/` - AI commit message generator
- `examples/example-saas-product/` - Developer analytics platform
- `examples/example-open-source-lib/` - React component library

## Support

- 📖 [User Guide](docs/user-guide.md) - Detailed documentation
- 💡 [Best Practices](docs/best-practices.md) - Tips from experienced users
- ❓ [FAQ](docs/faq.md) - Common questions
- 🐛 [Issues](https://github.com/kobe8cong/product-planner/issues) - Report bugs or request features
- 💬 [Discussions](https://github.com/kobe8cong/product-planner/discussions) - Community support

## Contributing

We welcome contributions! See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## License

MIT License - see [LICENSE](LICENSE) for details.

---

**Created with ❤️ for developers who want to build products that matter.**

---

## Implementation Notes

When this skill is invoked, follow this workflow:

### Step 1: Parse Input & Mode Selection

**Check user input:**
- If `/product-plan discover` → Discovery Mode
- If `/product-plan validate [idea]` → Validation Mode with idea
- If `/product-plan [idea]` → Default to Validation Mode
- If `/product-plan` (no args) → Show mode selection

**Mode Selection Prompt:**
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

### Discovery Mode Workflow

**Phase 0: Context Collection**

Ask the user:
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

**Phase 1: Trend Analysis**
- Launch `trend-analyzer` agent with user context
- Agent scans: GitHub Trending, Hacker News, Reddit, Product Hunt
- Agent outputs: Hot trends, pain points, technology opportunities, market gaps

**Phase 2: Opportunity Scout**
- Launch `opportunity-scout` agent with:
  - User context
  - Trend analysis results
- Agent generates 5+ concrete project opportunities
- Agent scores using matrix: Market Demand (25%) + Competition (20%) + Technical Fit (20%) + Time to MVP (15%) + Ecosystem Value (20%)
- Agent ranks by total score

**Phase 3: Present Recommendations**
```
Based on your context, I've identified 5 high-potential opportunities.

Here are your top 3 recommendations:

🥇 #1: [Name] (Score: 85/100)
    [One-line description]
    Best fit because: [Reason]

🥈 #2: [Name] (Score: 78/100)
    [One-line description]
    Best fit because: [Reason]

🥉 #3: [Name] (Score: 72/100)
    [One-line description]
    Best fit because: [Reason]

Want to see:
a) Full details on all 5 opportunities
b) Deep dive into #1
c) Deep dive into #2
d) Deep dive into #3
e) Different direction (tell me what)
```

**Phase 4: User Selection & Deep Dive**
- If user chooses to deep dive on an opportunity
- Run full Validation Mode analysis (Phases 1-5) on that specific idea
- Generate complete PRD

---

### Validation Mode Workflow

**Phase 0: Quick Validation (NEW)**
- Launch `idea-validator` agent with user's project idea
- Agent checks:
  - Time sensitivity (is this obsolete? AI solved it?)
  - Market demand (evidence of need)
  - Competition saturation
  - Red flags (technical, market, execution)
- Agent outputs: 🟢 Go / 🟡 Caution / 🔴 Stop

**If 🔴 Stop:**
```
Quick Validation: Not Recommended

[Explanation of issues]

Alternative directions to consider:
1. [Alternative 1]
2. [Alternative 2]

Would you like to:
a) Switch to Discovery Mode to find better opportunities
b) Adjust your idea based on these findings
c) Proceed anyway (I'll do full analysis)
```

**If 🟡 Caution:**
```
Quick Validation: Proceed with Caution

[Specific concerns]

Recommendation: [Adjust focus / Narrow scope / etc]

Continue with full analysis? (yes/no)
```

**If 🟢 Go:**
Continue to Phase 1 (existing workflow)

**Phase 1: Project Understanding**
- Present clarifying questions
- Collect answers
- Summarize project brief
- Ask for confirmation

**Phase 2: Market Research**
- Launch `market-researcher` agent with project brief
- Launch `competitor-analyzer` agent with project brief (parallel)
- Wait for both agents to complete
- Synthesize findings
- Present key insights

**Phase 3: Product Definition**
- Define value proposition
- Generate user personas
- List all possible features
- Create priority matrix
- Propose MVP scope
- **Ask user to confirm MVP** before proceeding

**Phase 4: Roadmap**
- Define v1.0 MVP details
- Plan v1.1, v2.0 evolution
- Estimate timelines
- Assess risks

**Phase 5: Success Metrics & GTM**
- Define North Star Metric
- Set KPIs
- Create GTM plan
- Recommend channels

**Phase 6: Generate Output**
- Create `docs/product/` directory if not exists
- Generate PRD.md (comprehensive)
- Generate individual phase reports
- Save all files

**Phase 7: Summary**
- List generated files
- Highlight key recommendations
- Suggest next steps

## Progress Display

### Discovery Mode Progress

```
Product Planner: AI Product Manager for Developers

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Discovery Mode: Finding Opportunities for You

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Phase 0: Understanding Your Context

[Context collection questions]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Phase 1: Market Trend Analysis

🔍 Scanning market trends and opportunities...
✓ GitHub Trending analyzed
✓ Hacker News discussions reviewed
✓ Reddit communities surveyed
✓ Product Hunt launches checked

Found:
- 4 hot trends
- 5 validated pain points
- 3 technology opportunities
- 3 market gaps

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Phase 2: Opportunity Identification

🎯 Generating project opportunities...
✓ 12 candidates identified
✓ Filtered to 5 strong opportunities
✓ Scored and ranked

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Top 3 Recommendations:

🥇 #1: [Name] (Score: 85/100)
🥈 #2: [Name] (Score: 78/100)
🥉 #3: [Name] (Score: 72/100)

[Present choices]
```

### Validation Mode Progress

```
Product Planner: AI Product Manager for Developers

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Validation Mode: Analyzing Your Idea

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Phase 0: Quick Validation

🔍 Running rapid assessment...
✓ Time sensitivity check
✓ Market demand validation
✓ Competition analysis
✓ Red flag detection

Assessment: 🟢 Promising - Recommend full analysis

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Phase 1/5: Understanding Your Project

[Questions and interaction]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Phase 2/5: Market Research

🔍 Analyzing market and competitors...
✓ Market size analysis complete
✓ Found 5 competitors
✓ User research complete

[Present findings]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[... continue through phases ...]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

✅ Product Plan Complete!

Generated documents:
📄 docs/product/PRD.md
📄 docs/product/market-research.md
📄 docs/product/competitor-analysis.md
📄 docs/product/roadmap.md
📄 docs/product/success-metrics.md

Next steps:
1. Review your PRD
2. Share with team/advisors
3. Start building your MVP

Ready to build something great! 🚀
```

## Error Handling

**Discovery Mode:**
- If trend-analyzer fails: Retry once, then use cached trend data or ask user for interest areas
- If opportunity-scout fails: Generate opportunities based on user context only
- If user provides vague context: Ask follow-up questions to clarify

**Validation Mode:**
- If idea-validator recommends Stop: Offer Discovery Mode or alternative directions
- If agent fails: Retry once, then continue with partial results
- If user cancels: Save progress to `.product-planner-draft/`
- If output directory not writable: Ask for alternative location
- If no internet: Warn that market research will be limited

**General:**
- If mode unclear: Show mode selection prompt
- If user switches modes mid-flow: Confirm before switching
- If incomplete context: Ask clarifying questions rather than making assumptions
