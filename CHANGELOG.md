# Changelog

All notable changes to Product Planner will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.1.0] - 2026-06-28

### 🎉 Major Update: From Passive Validation to Active Discovery

v1.1 transforms Product Planner from a passive validation tool into a proactive product advisor that can discover opportunities for you.

### ✨ Added

#### 🔍 Discovery Mode - NEW
- **Proactive Opportunity Finding**: AI now actively suggests project opportunities
- **Context Collection**: Understands your skills, time, goals, and interests
- **Market Trend Analysis**: Scans GitHub Trending, Hacker News, Reddit, Product Hunt
- **Opportunity Scoring System**: 
  - Multi-dimensional scoring: Market Demand (25%) + Competition (20%) + Technical Fit (20%) + Time to MVP (15%) + Ecosystem Value (20%)
  - Ranks 5+ opportunities, highlights top 3
- **New Command**: `/product-plan discover`

#### 🤖 New AI Agents
- **trend-analyzer**: Market trends, pain points, technology opportunities, gap discovery
- **opportunity-scout**: Project identification, feasibility evaluation, scoring and ranking

#### ✅ Quick Validation - NEW
- **Phase 0 in Validation Mode**: Rapid assessment before full analysis
- **Obsolescence Detection**: Catches outdated ideas (e.g., "AI commit tools" - now built-in)
- **Red Flag Detection**: Technical, market, execution, problem-solution fit issues
- **Go/Caution/Stop Recommendations**: Clear decision before investing time
- **Alternative Suggestions**: If rejected, suggests better directions
- **New Agent**: `idea-validator`

#### 🔀 Dual-Mode System
- **Mode Selection**: Choose Discovery or Validation at start
- **Four Command Variants**:
  - `/product-plan discover` - Launch Discovery Mode
  - `/product-plan validate [idea]` - Launch Validation Mode
  - `/product-plan` - Interactive mode selection
  - `/product-plan [idea]` - Defaults to Validation (legacy support)
- **Seamless Transition**: Deep dive from Discovery enters full Validation

### 🔄 Changed
- **README.md**: Updated to reflect dual-mode functionality
- **SKILL.md**: Complete rewrite with new workflows and agent documentation
- **Positioning**: From "Transform ideas" to "Discover opportunities or validate ideas"
- **Execution Time**: Discovery ~10-15 min, Validation ~15-20 min (with quick validation)

### 💡 Improved
- **Smarter Routing**: Avoids wasting time on non-viable ideas
- **Evidence-Based**: All recommendations backed by specific market data and links
- **User-Centric**: Matches opportunities to actual context, skills, and constraints
- **Fail-Fast**: Quick Validation catches problems in 10 minutes vs. full 20-minute analysis

### 📊 Impact

| Capability | v1.0 | v1.1 |
|------------|------|------|
| **Find Opportunities** | ❌ | ✅ |
| **Validate Ideas** | ✅ | ✅ |
| **Detect Obsolete Ideas** | ❌ | ✅ |
| **Market Trend Analysis** | ❌ | ✅ |
| **Opportunity Scoring** | ❌ | ✅ |
| **AI Agents** | 3 | 6 |
| **Mode Options** | 1 | 2 |

### 🎯 Why v1.1?

**User Insight**: "I want a product manager that can SUGGEST what to build, not just validate my ideas."

**Problem Solved**: 
- v1.0 was reactive (you bring ideas)
- v1.1 is proactive (AI finds opportunities)
- Quick validation prevents wasting time on dead ends

**Real Example**: 
- User suggested "AI commit message generator"
- Quick Validation detected: Cursor/Claude Code already do this automatically
- Recommended alternatives in emerging spaces instead

## [1.0.0] - 2026-06-27

### 🎉 Initial Release

First stable release of Product Planner - AI Product Manager for Developers.

### ✨ Features

#### Core Workflow
- **5-Phase Analysis Pipeline**: Complete product planning workflow
  - Phase 1: Project Understanding
  - Phase 2: Market Research
  - Phase 3: Product Definition
  - Phase 4: Roadmap Planning
  - Phase 5: Success Metrics & GTM

#### AI Agents
- **market-researcher**: Analyzes market size, trends, and user personas
- **competitor-analyzer**: Discovers and analyzes competitors
- **product-strategist**: Synthesizes insights into actionable strategy

#### Output Generation
- **Complete PRD**: Professional Product Requirements Document
- **Market Research Report**: Detailed market analysis
- **Competitor Analysis**: Competitive intelligence
- **Product Definition**: MVP and feature specifications
- **Roadmap**: Version evolution plan
- **Success Metrics**: KPI framework
- **GTM Strategy**: Go-to-market plan

#### User Experience
- Interactive guided workflow
- Quick start with direct input
- Progress indicators
- Clear phase transitions
- Helpful error messages

#### Documentation
- Comprehensive README
- Detailed user guide
- Architecture documentation
- Contributing guidelines
- Example analyses

### 📦 Templates
- PRD template with complete structure
- Roadmap template
- Competitor matrix template

### 📚 Examples
- CLI tool example (AI commit generator)
- SaaS product example (Developer analytics)
- Open source library example (React components)

### 🎯 Target Users
- Independent developers
- Open source maintainers
- Small team tech founders
- Side project builders

### 🔧 Technical
- Built as Claude Code plugin
- Markdown-based output
- Modular agent architecture
- Configurable via .product-planner.json

### 📝 Documentation
- [README.md](README.md) - Main documentation
- [ARCHITECTURE.md](ARCHITECTURE.md) - Technical design
- [CONTRIBUTING.md](CONTRIBUTING.md) - Contribution guidelines
- [LICENSE](LICENSE) - MIT License

---

## [Unreleased]

### Under Consideration for v1.2
- [ ] Save discovered opportunities for later review
- [ ] Compare multiple opportunities side-by-side
- [ ] Refine opportunity scores based on user feedback
- [ ] Track market trends over time

### Planned for v2.0
- [ ] Update existing product plans
- [ ] Export to multiple formats (PDF, Notion, etc.)
- [ ] Data visualizations (charts, graphs)
- [ ] Integration with GitHub Issues
- [ ] Integration with Linear/Jira
- [ ] Team collaboration features
- [ ] Pricing strategy analysis
- [ ] A/B testing recommendations

---

## Release Notes

### v1.0.0 - Initial Release

This is the first production-ready release of Product Planner. After extensive development and self-testing, we're excited to bring systematic product thinking to developers everywhere.

**Key Highlights:**
- Complete 5-phase product planning workflow
- AI-powered market research and competitive analysis
- Professional PRD generation in minutes
- Seamless integration with Claude Code

**What's Included:**
- 3 specialized AI agents for deep analysis
- Complete documentation and examples
- MIT license for maximum flexibility
- Ready for immediate use

**What's Next:**
We'll be gathering user feedback and iterating based on real-world usage. Community contributions are welcome!

**Installation:**
```bash
cd ~/.claude/skills/
git clone https://github.com/kobe8cong/product-planner.git
```

**Usage:**
```bash
/product-plan Your product idea here
```

---

## Development History

### 2026-06-28
- 🎯 User testing revealed v1.0 limitation: only validates, doesn't discover
- 💡 Designed v1.1 with Discovery Mode and Quick Validation
- 🤖 Implemented 3 new agents (trend-analyzer, opportunity-scout, idea-validator)
- 📝 Updated all documentation
- 🚀 v1.1.0 released

### 2026-06-27
- ✅ Product analysis completed
- ✅ Architecture design finalized
- ✅ Core agents implemented (market-researcher, competitor-analyzer, product-strategist)
- ✅ Templates created
- ✅ Documentation written
- ✅ Examples prepared
- 🚀 v1.0.0 released

---

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for how to contribute to Product Planner.

## Support

- 🐛 [Report Issues](https://github.com/kobe8cong/product-planner/issues)
- 💬 [Discussions](https://github.com/kobe8cong/product-planner/discussions)
- ⭐ [Star on GitHub](https://github.com/kobe8cong/product-planner)

---

[1.1.0]: https://github.com/kobe8cong/product-planner/releases/tag/v1.1.0
[1.0.0]: https://github.com/kobe8cong/product-planner/releases/tag/v1.0.0
[Unreleased]: https://github.com/kobe8cong/product-planner/compare/v1.1.0...HEAD
