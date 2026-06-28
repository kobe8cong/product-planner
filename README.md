# Product Planner

> AI Product Manager for Developers - Discover opportunities or validate your ideas with data-driven analysis.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Plugin-blue)](https://claude.ai/code)
[![Version](https://img.shields.io/badge/version-1.1.0-green.svg)](https://github.com/kobe8cong/product-planner/releases)

Product Planner brings systematic product thinking to your development workflow. It can **actively discover** high-potential project opportunities based on market trends, or **validate** your existing ideas through comprehensive research—all powered by AI and integrated seamlessly into Claude Code.

## ✨ Why Product Planner?

**The Problem:** Developers are great at building, but often:
- ❌ Don't know what to build next
- ❌ Build features nobody wants
- ❌ Miss market opportunities  
- ❌ Waste time on outdated ideas
- ❌ Launch without strategy

**The Solution:** Product Planner provides:
- ✅ **Proactive opportunity discovery** (NEW in v1.1)
- ✅ **Quick idea validation** to avoid wasted effort (NEW in v1.1)
- ✅ Systematic product methodology
- ✅ AI-powered market research
- ✅ Data-driven feature prioritization
- ✅ Professional PRD generation
- ✅ Go-to-market strategy

## 🚀 Quick Start

### Discovery Mode - Find Opportunities
```bash
# Let AI suggest projects based on market analysis
/product-plan discover
```

### Validation Mode - Analyze Your Idea
```bash
# Validate your specific idea
/product-plan validate Your amazing product idea here
```

That's it! In 10-20 minutes, you'll have:
- 🔍 Market trend analysis (Discovery mode)
- 🎯 Top project recommendations (Discovery mode)
- ✅ Quick validation check (Validation mode)
- 📊 Complete market analysis
- 🎯 Defined MVP scope
- 🗺️ Product roadmap
- 📈 Success metrics
- 🚀 Launch strategy

## 🎯 What It Does

Product Planner offers **two powerful modes**:

### 🔍 Discovery Mode - Find Opportunities

**Can't decide what to build?** Let Product Planner discover opportunities for you.

1. **Context Collection** - Understand your skills, time, goals
2. **Trend Analysis** - Scan GitHub, HN, Reddit, Product Hunt
3. **Opportunity Scout** - Identify and score 5+ project ideas
4. **Recommendations** - Present top 3 with detailed analysis
5. **Deep Dive** - Choose one for full product planning

**Uses specialized agents:**
- `trend-analyzer` - Market trends and pain point discovery
- `opportunity-scout` - Project identification and scoring

### ✅ Validation Mode - Analyze Your Idea

**Have an idea?** Let Product Planner validate it thoroughly.

**Phase 0: Quick Validation (NEW)**
- Checks if idea is obsolete (e.g., AI now does this automatically)
- Validates market demand with evidence
- Identifies red flags early
- Recommends: Go / Caution / Stop

**If validation passes:**

### Phase 1: Project Understanding 🎯
Clarifies your vision through strategic questions.

### Phase 2: Market Research 📊
Analyzes market size, trends, and competitors using specialized AI agents.

### Phase 3: Product Definition 💎
Prioritizes features and defines MVP using value vs. cost framework.

### Phase 4: Roadmap Planning 🗺️
Creates phased evolution strategy from MVP to scale.

### Phase 5: Success Metrics & GTM 📈
Defines KPIs and go-to-market strategy.

## 📄 Output

Generates professional documentation in `docs/product/`:

```
your-project/
└── docs/
    └── product/
        ├── PRD.md                   # Complete Product Requirements Document
        ├── market-research.md       # Market analysis with user personas
        ├── competitor-analysis.md   # Competitive intelligence
        ├── product-definition.md    # MVP and feature specifications
        ├── roadmap.md              # Version evolution plan
        ├── success-metrics.md      # KPIs and measurement framework
        └── gtm-strategy.md         # Go-to-market plan
```

## 🤖 AI Agents

Product Planner uses specialized agents for deep analysis:

### Discovery Mode Agents
- **trend-analyzer** - Scans GitHub, HN, Reddit, Product Hunt for trends and opportunities
- **opportunity-scout** - Identifies and scores concrete project opportunities

### Validation Mode Agents
- **idea-validator** - Quick validation and red flag detection (NEW in v1.1)
- **market-researcher** - Market dynamics and user needs analysis
- **competitor-analyzer** - Competitive intelligence and differentiation
- **product-strategist** - Strategic synthesis and prioritization

## 🎬 Example

See a real analysis in `examples/`:
- [CLI Tool Example](examples/example-cli-tool/) - AI commit message generator
- [SaaS Product Example](examples/example-saas-product/) - Developer analytics
- [Open Source Library](examples/example-open-source-lib/) - React components

## 💡 When to Use

**Perfect for:**
- 💡 Starting a new side project
- 🚀 Launching an open source project
- 📦 Building a SaaS product
- 🔧 Creating developer tools
- 📱 Planning a mobile app

**Especially valuable when:**
- Unsure if an idea is worth building
- Need to validate market fit before coding
- Want to prioritize features with limited resources
- Applying for funding or partnerships
- Attracting contributors to open source projects

## 📦 Installation

### Method 1: Clone to Skills Directory

```bash
cd ~/.claude/skills/
git clone https://github.com/kobe8cong/product-planner.git
```

### Method 2: Download and Extract

1. Download the latest release
2. Extract to `~/.claude/skills/product-planner/`

### Method 3: Via Claude Code Marketplace (Coming Soon)

```bash
/plugin install product-planner
```

## 🎓 Usage

### Interactive Mode

```bash
/product-plan
```

Follow the guided questions to build your product plan.

### Quick Start Mode

```bash
/product-plan An AI-powered CLI tool that generates git commit messages based on staged changes
```

Provide your idea directly to skip initial setup.

### Help

```bash
/product-plan --help
```

## 🏆 Features

✅ **Comprehensive Analysis** - Market, competition, product, and strategy  
✅ **Data-Driven** - Real market data and competitive intelligence  
✅ **Structured Output** - Professional PRD format  
✅ **Interactive** - Clarifying questions for precision  
✅ **Fast** - Complete analysis in 5-10 minutes  
✅ **Integrated** - Seamless Claude Code workflow  
✅ **Flexible** - Update existing plans or start fresh  
✅ **Export-Friendly** - Markdown format, version control ready  

## 🔧 Configuration

Optional configuration in `.product-planner.json`:

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

## 📚 Documentation

- [User Guide](docs/user-guide.md) - Complete documentation
- [Architecture](ARCHITECTURE.md) - Technical design
- [Best Practices](docs/best-practices.md) - Tips for success
- [FAQ](docs/faq.md) - Common questions

## 🤝 Contributing

We welcome contributions! See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

**Ways to contribute:**
- 🐛 Report bugs
- 💡 Suggest features
- 📝 Improve documentation
- 🔧 Submit pull requests
- ⭐ Star the project

## 📊 Roadmap

### v1.0 - MVP ✅ (Current)
- Core 5-phase workflow
- 3 specialized agents
- PRD generation

### v1.1 - Enhancements (Planned)
- Update existing plans
- Export to multiple formats
- Custom templates

### v2.0 - Scale (Future)
- Data visualizations
- Integration with project management tools
- Team collaboration features

See [full roadmap](docs/roadmap.md) for details.

## 🙏 Acknowledgments

Built with:
- [Claude Code](https://claude.ai/code) - AI-powered development environment
- [Claude 4](https://www.anthropic.com/) - Advanced AI reasoning

Inspired by product management best practices from:
- [Shape Up](https://basecamp.com/shapeup) by Basecamp
- [Inspired](https://www.svpg.com/books/inspired/) by Marty Cagan
- [The Lean Startup](http://theleanstartup.com/) by Eric Ries

## 📝 License

MIT License - see [LICENSE](LICENSE) file for details.

## 🌟 Support

- 🐛 [Report Issues](https://github.com/kobe8cong/product-planner/issues)
- 💬 [Discussions](https://github.com/kobe8cong/product-planner/discussions)
- 📧 [Email](mailto:kobe8cong@users.noreply.github.com)
- ⭐ [Star on GitHub](https://github.com/kobe8cong/product-planner)

---

**Created with ❤️ for developers who want to build products that matter.**

---

## 🎯 Status

- **Version:** 1.0.0
- **Status:** Production Ready
- **Last Updated:** 2026-06-27
- **Maintainer:** [@kobe8cong](https://github.com/kobe8cong)

## 📈 Stats

![GitHub stars](https://img.shields.io/github/stars/kobe8cong/product-planner?style=social)
![GitHub forks](https://img.shields.io/github/forks/kobe8cong/product-planner?style=social)
![GitHub watchers](https://img.shields.io/github/watchers/kobe8cong/product-planner?style=social)

---

<p align="center">
  <strong>Transform your ideas into products that succeed.</strong>
</p>

<p align="center">
  <a href="#-quick-start">Quick Start</a> •
  <a href="#-what-it-does">Features</a> •
  <a href="#-installation">Installation</a> •
  <a href="docs/user-guide.md">Documentation</a> •
  <a href="CONTRIBUTING.md">Contributing</a>
</p>
