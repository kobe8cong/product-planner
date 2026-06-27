# Product Planner

AI Product Manager for Developers - Transform your ideas into well-researched product plans.

## Overview

Product Planner brings systematic product thinking to your development workflow. Instead of jumping straight into code, it guides you through market research, competitive analysis, MVP definition, and strategic planning - all powered by AI and integrated seamlessly into Claude Code.

## Command

### `/product-plan [project description]`

Launch a comprehensive product planning workflow that analyzes your project idea and generates a complete Product Requirements Document (PRD).

**Usage:**
```bash
# Interactive mode - guided questions
/product-plan

# Quick start - provide description directly
/product-plan An AI-powered CLI tool for generating git commit messages

# Show help
/product-plan --help
```

## What It Does

Product Planner runs a **5-phase analysis workflow**:

### Phase 1: Project Understanding 🎯
- Clarifies your project vision
- Identifies target users and goals
- Defines constraints and requirements
- Ensures we're solving the right problem

### Phase 2: Market Research 📊
- Analyzes market size and trends
- Identifies target user personas
- Discovers and analyzes competitors
- Finds market opportunities and gaps

**Launches 2 agents in parallel:**
- `market-researcher` - Market and user analysis
- `competitor-analyzer` - Competitive intelligence

### Phase 3: Product Definition 💎
- Defines core value proposition
- Creates user personas and pain points
- Generates comprehensive feature list
- Prioritizes features using value vs. cost matrix
- Defines MVP scope

**Asks for your confirmation before proceeding.**

### Phase 4: Roadmap Planning 🗺️
- Defines v1.0 MVP timeline and scope
- Plans v1.1, v2.0+ evolution
- Assesses technical feasibility
- Estimates resources and risks
- Sets milestone targets

### Phase 5: Success Metrics & GTM 📈
- Defines North Star Metric
- Sets up KPI framework
- Creates measurement plan
- Designs Go-to-Market strategy
- Recommends launch channels and timing

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

```
User Input: Project Idea
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

### market-researcher
Analyzes market dynamics and user needs:
- Market size estimation (TAM/SAM/SOM)
- Trend analysis and drivers
- User persona generation
- Pain point identification

### competitor-analyzer
Provides competitive intelligence:
- Discovers similar products/projects
- Analyzes features and positioning
- Compares GitHub metrics (stars, activity)
- Identifies differentiation opportunities

### product-strategist
Synthesizes insights into strategy:
- Defines value proposition
- Prioritizes features
- Plans roadmap phases
- Sets success criteria

## Features

✅ **Comprehensive Analysis** - Covers market, competition, product, and strategy  
✅ **Data-Driven** - Uses real market data and competitive intelligence  
✅ **Structured Output** - Professional PRD format ready to share  
✅ **Interactive** - Asks clarifying questions to understand your vision  
✅ **Fast** - Complete analysis in 5-10 minutes  
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

1. **Parse Input**
   - Check if project description provided
   - If not, ask for it interactively
   - Validate input is sufficient

2. **Execute Phase 1: Understanding**
   - Present clarifying questions
   - Collect answers
   - Summarize project brief
   - Ask for confirmation

3. **Execute Phase 2: Market Research**
   - Launch `market-researcher` agent with project brief
   - Launch `competitor-analyzer` agent with project brief (parallel)
   - Wait for both agents to complete
   - Synthesize findings
   - Present key insights

4. **Execute Phase 3: Product Definition**
   - Define value proposition
   - Generate user personas
   - List all possible features
   - Create priority matrix
   - Propose MVP scope
   - **Ask user to confirm MVP** before proceeding

5. **Execute Phase 4: Roadmap**
   - Define v1.0 MVP details
   - Plan v1.1, v2.0 evolution
   - Estimate timelines
   - Assess risks

6. **Execute Phase 5: Success Metrics & GTM**
   - Define North Star Metric
   - Set KPIs
   - Create GTM plan
   - Recommend channels

7. **Generate Output**
   - Create `docs/product/` directory if not exists
   - Generate PRD.md (comprehensive)
   - Generate individual phase reports
   - Save all files

8. **Summary**
   - List generated files
   - Highlight key recommendations
   - Suggest next steps

## Progress Display

Show clear progress indicators:

```
Product Planner: AI Product Manager for Developers

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

- If agent fails: Retry once, then continue with partial results
- If user cancels: Save progress to `.product-planner-draft/`
- If output directory not writable: Ask for alternative location
- If no internet: Warn that market research will be limited
