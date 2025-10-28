# Tools Integration Guide
**The Rev.io Way - AI Agents & Integration Setup**

**Version:** 1.0  
**Last Updated:** 2025-01-XX

---

## 🎯 Overview

The Rev.io Way leverages cutting-edge AI agents and automation tools that work together seamlessly through Model Context Protocol (MCP). This guide explains what each tool does, how to set them up, and when to use them.

---

## 🤖 AI Agents & Orchestration

### Mary (BMAD / Analyst)

**What it is:** AI analyst that guides product discovery and generates PRDs through strategic elicitation.

**When to use:**
- Phase 1: Discovery with PM
- Creating ProjectBrief and PRFAQ
- Generating PRD documents
- Sharding PRD into components

**How to invoke:**
```
/analyst
```

**Key capabilities:**
- Strategic elicitation (asks questions)
- Document generation (ProjectBrief, PRFAQ, PRD)
- Requirements analysis
- Competitive context integration

**Setup requirements:**
- Configured in `.claude/commands/agent-os/analyst.md`
- Available in Claude Code
- MCP integration configured

**Pro tips:**
- Trust the elicitation process—answer questions honestly
- Be comprehensive in your responses
- Don't skip elicitation even if you think you know the answer
- Use Mary iteratively—refine based on feedback

---

### Agent-OS

**What it is:** Engineering orchestrator that generates technical specs, creates features/stories/tasks, and coordinates specialized sub-agents.

**When to use:**
- Phase 3: Generating technical specifications
- Phase 4: Orchestrating implementation
- Creating features, stories, and tasks
- Coordinating sub-agents automatically

**How to invoke:**
```
/create-spec [shard-document]
/implement-spec
```

**Key capabilities:**
- Technical specification generation
- Feature/story/task breakdown
- Sub-agent orchestration (API, UI, database, testing)
- Progress tracking and roadmap updates

**Setup requirements:**
- Local setup (multi-agent mode enabled)
- Project configuration (`product/mission.md`, `product/tech-stack.md`, `product/roadmap.md`)
- Standards templates copied from `agent-os/standards/`
- GitHub repository configured

**Sub-agents:**
- **API Agent:** Backend API development
- **UI Agent:** Frontend component development
- **Database Agent:** Schema and migrations
- **Testing Agent:** Test creation and validation

**Pro tips:**
- Ensure project config is complete before use
- Review generated specs before implementation
- Monitor Agent-OS progress during implementation
- Update tech-stack.md if architecture needs refinement

---

## 🔌 Integrations & Connectivity (via MCP)

### Model Context Protocol (MCP)

**What it is:** Framework enabling seamless connections between AI agents and external systems.

**How it works:**
- Agents interact with tools autonomously or at your request
- You don't access tools directly—agents do it for you
- Bi-directional communication between agents and systems

**Why it matters:**
- Agents can research, update, and use tools independently
- Reduces manual work
- Ensures agents have accurate, up-to-date information
- Enables autonomous agent workflows

---

### Notion MCP

**What it does:** Agents sync with Notion for PRD boards and progress tracking.

**Setup:**
1. Create Notion API integration
2. Generate integration token
3. Configure MCP connection
4. Set up bidirectional sync for PRD Board
5. Set up one-way sync for Progress Board

**How agents use it:**
- **PM:** Edit PRDs in Notion, changes sync to GitHub
- **Engineering:** Code progress syncs from GitHub to Notion
- **Mary:** Can read and update PRD boards
- **Agent-OS:** Updates progress boards automatically

**Two boards per project:**

**PRD Board (Notion = Source of Truth)**
- Houses PRDs and sharded component PRDs
- Sync: Notion → GitHub
- PM makes changes here
- Engineers read from GitHub

**Progress Board (GitHub = Source of Truth)**
- Displays Agent-OS roadmap tasks and progress
- Sync: GitHub → Notion (one-way)
- PM sees real-time engineering progress
- Auto-updates as work happens

**Verification:**
- Test sync in both directions
- Confirm changes appear correctly
- Verify progress updates automatically

---

### GitHub MCP

**What it does:** Agents access repositories for code and documentation sync.

**Setup:**
1. Generate GitHub personal access token
2. Configure MCP connection
3. Set up repository access
4. Configure branch protection if needed

**How agents use it:**
- **Agent-OS:** Reads specs, writes code, updates roadmaps
- **Mary:** Can read existing documentation
- **Sync:** Notion PRDs → GitHub specs
- **Sync:** GitHub progress → Notion board

**Repository structure:**
```
agent-os/
├── specs/                    # Generated specs per component
├── product/                  # Project configuration
│   ├── mission.md
│   ├── roadmap.md
│   └── tech-stack.md
└── standards/                # Templates (don't edit)
```

**Verification:**
- Confirm agents can read repos
- Test code write permissions
- Verify roadmap updates work

---

### Devin (DeepWiki)

**What it does:** Agents research Rev.io repositories to understand tech stacks, coding patterns, and standards.

**When to use:**
- Need to understand existing codebase
- Research coding patterns and standards
- Learn about architectural decisions
- Find examples of similar implementations

**How agents use it:**
- Research before generating specs
- Find existing patterns to follow
- Understand architectural context
- Learn coding conventions

**Setup:**
- Configure Devin integration
- Grant repository access
- Enable for Agent-OS use

**Pro tips:**
- Let Devin research before starting new features
- Use findings to inform Agent-OS instructions
- Share Devin insights with team

---

### Context7

**What it does:** Agents retrieve version-specific, up-to-date documentation preventing API hallucinations and ensuring accurate code suggestions.

**When to use:**
- Need accurate API documentation
- Preventing "hallucinated" code
- Ensuring version compatibility
- Getting current best practices

**How agents use it:**
- Retrieve library documentation
- Get version-specific API details
- Find breaking changes and migrations
- Access latest coding patterns

**Setup:**
- Configure Context7 MCP integration
- Specify library versions
- Enable for Agent-OS use

**Pro tips:**
- Let Context7 provide docs automatically
- Trust it over general knowledge
- It prevents API version mistakes

---

### Zen

**What it does:** Agents perform consensus gathering, contrarian analysis, and deep research.

**When to use:**
- Complex architectural decisions
- Need multiple perspectives
- Deep research required
- Consensus building needed

**How agents use it:**
- Gather expert opinions
- Perform contrarian analysis
- Deep research on topics
- Build consensus on decisions

**Setup:**
- Configure Zen MCP integration
- Enable for complex decisions
- Use when consensus needed

**Pro tips:**
- Use for high-stakes decisions
- Get contrarian views before committing
- Leverage for research depth

---

### Playwright

**What it does:** Agents test their own work autonomously and iterate during builds.

**When to use:**
- UI implementation testing
- End-to-end testing
- Automated QA during builds
- Browser testing needs

**How agents use it:**
- Test UI components automatically
- Run E2E tests during implementation
- Verify user flows work
- Iterate based on test results

**Setup:**
- Install Playwright
- Configure MCP integration
- Enable for Agent-OS use

**Pro tips:**
- Let agents test autonomously
- Monitor test results
- Fix issues agent identifies

---

### Figma

**What it does:** Agents reference UI/UX design mocks directly during implementation.

**When to use:**
- UI implementation needs design context
- Verify UI matches designs
- Understand interaction patterns
- Reference design specifications

**How agents use it:**
- Read Figma designs
- Extract UI specifications
- Match implementation to designs
- Verify visual consistency

**Setup:**
- Configure Figma API access
- Set up MCP integration
- Enable for Agent-OS use

**Pro tips:**
- Share Figma links with agents
- Keep designs up to date
- Reference designs explicitly

---

## 🛠️ Setup & Configuration

### One-Time Setup

**Step 1: Environment Setup**
- Install Node.js and required dependencies
- Set up local development environment
- Configure Git and GitHub access

**Step 2: MCP Configuration**
- Set up Model Context Protocol
- Configure each MCP server (Notion, GitHub, Devin, Context7, Zen, Playwright, Figma)
- Generate API tokens and credentials
- Test each integration

**Step 3: Agent-OS Setup**
- Clone Agent-OS repository
- Enable multi-agent mode
- Copy standards templates
- Create project configuration

**Step 4: Mary Setup**
- Configure analyst in Claude Code
- Set up commands
- Test `/analyst` invocation

**Step 5: Notion Boards**
- Create PRD Board
- Create Progress Board
- Configure bidirectional sync
- Test sync functionality

### Per-Project Setup

**Step 1: Create Project Config**
- Copy templates from `agent-os/standards/`
- Create `product/mission.md`
- Create `product/roadmap.md`
- Create `product/tech-stack.md`

**Step 2: Set Up Notion Boards**
- Create PRD Board for project
- Create Progress Board for project
- Configure syncs

**Step 3: Verify Tool Access**
- Test Mary invocation
- Test Agent-OS commands
- Verify MCP integrations
- Confirm sync functionality

---

## 🔍 Verification & Troubleshooting

### Verifying MCP Integrations

**Test each integration:**
- Notion: Can agents read/write?
- GitHub: Can agents commit code?
- Devin: Can agents research repos?
- Context7: Can agents get docs?
- Zen: Can agents gather consensus?
- Playwright: Can agents run tests?
- Figma: Can agents read designs?

### Common Issues

**Issue: Agent can't access Notion**
- Check API token
- Verify board permissions
- Test MCP connection

**Issue: GitHub sync not working**
- Check repository access
- Verify branch permissions
- Test commit capabilities

**Issue: Agent-OS generates wrong code**
- Check `product/tech-stack.md`
- Verify standards completeness
- Review project configuration

**Issue: MCP connection timeout**
- Check network connectivity
- Verify API credentials
- Test server availability

---

## 📚 Best Practices

### For PMs
- Use Mary for all discovery work
- Trust the elicitation process
- Keep Notion PRD Board updated
- Monitor Progress Board daily

### For Prompt Engineers
- Keep `product/tech-stack.md` current
- Review standards regularly
- Verify Agent-OS outputs
- Guide agents when needed

### For Senior Engineers
- Set quality standards early
- Keep standards updated
- Run verifiers consistently
- Don't compromise on quality

### For All
- Understand what each tool does
- Let agents do their work
- Monitor progress regularly
- Communicate blockers immediately

---

## 🎓 Training & Onboarding

### New Team Member Checklist
- [ ] Read RevioProductWorkflow.html
- [ ] Read POD_QUICK_REFERENCE.md
- [ ] Complete tool setup
- [ ] Verify MCP integrations
- [ ] Complete test run with Mary
- [ ] Complete test run with Agent-OS
- [ ] Understand role-specific playbook
- [ ] Participate in first project

### Tool Training Resources
- Mary: Analyst commands and elicitation guide
- Agent-OS: Command reference and architecture docs
- MCP: Integration setup guides
- Notion: Board setup and sync configuration
- GitHub: Repository structure and permissions

---

*This guide is updated as tools evolve. Always refer to latest documentation.*


