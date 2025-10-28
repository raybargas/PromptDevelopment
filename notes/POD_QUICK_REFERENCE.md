# Pod Quick Reference
**The Rev.io Way - Quick Start Guide for All Pod Members**

**Version:** 1.0  
**Last Updated:** 2025-01-XX

---

## 🎯 What's Your Role?

### Product Manager (PM)
**Your Focus:** Vision, customer value, stakeholder alignment

**What You Do:**
- Work with Mary (AI analyst) to discover and document requirements
- Validate business value with PRFAQ ratification
- Hand off sharded PRD documents to engineering
- Monitor progress in Notion (no status meetings needed)

**Key Commands:**
- `/analyst` - Invoke Mary for discovery and documentation

---

### Prompt Engineer
**Your Focus:** Translate business requirements into technical implementation

**What You Do:**
- Receive sharded PRD documents from PM
- Feed documents to Agent-OS sequentially
- Execute `/create-spec` and `/implement-spec`
- Monitor Agent-OS progress and address blockers

**Key Commands:**
- `/create-spec` - Generate technical specs from PRD
- `/implement-spec` - Execute implementation

---

### Senior Engineer
**Your Focus:** Quality, architecture integrity, final approval

**What You Do:**
- Review specs before implementation
- Validate implementation quality
- Run verifiers to check quality
- Gate code before merge
- **Additionally:** Perform Prompt Engineer duties (feed specs, execute commands)

**Key Tools:**
- Verifier agents (backend, frontend, test, implementation)
- Code review tools
- Testing frameworks

---

## 📋 The 4-Phase Workflow

### Phase 1: Discovery with Mary
**Who:** PM only  
**Duration:** 1-3 days  
**Output:** ProjectBrief + PRFAQ

**Quick Steps:**
1. PM invokes `/analyst`
2. Mary asks strategic questions
3. PM answers (problem, users, goals, constraints)
4. Mary generates ProjectBrief + PRFAQ
5. **Gate:** PRFAQ must be ratified by stakeholders before proceeding

---

### Phase 2: Project Formation & PRD Creation
**Who:** PM + Engineers (team collaboration)  
**Duration:** 1-2 days  
**Output:** PRD + Sharded documents + Project infrastructure

**Quick Steps:**
1. **PM Stream:** Mary creates full PRD
2. **Team Stream:** Shard PRD into numbered documents (01-, 02-, 03-...)
3. **Engineering Stream:** Set up Notion boards + Agent-OS config
4. **Collaboration:** Team validates sharded documents

**Parallel Work:**
- PM finishes discovery with Mary
- Engineering sets up infrastructure (Notion boards, Agent-OS)

---

### Phase 3: Technical Specification
**Who:** Prompt Engineer + Senior Engineer  
**Duration:** 1-2 days per shard  
**Output:** Features, stories, spec.md, tasks.md

**Quick Steps:**
1. Engineer selects next sequential shard (01, then 02, then 03...)
2. Feed shard to Agent-OS with `/create-spec`
3. Agent-OS generates features → stories → spec.md → tasks.md
4. **Team Review:** Pod validates spec before implementation

---

### Phase 4: Implementation & Tracking
**Who:** Prompt Engineer + Senior Engineer  
**Duration:** Ongoing  
**Output:** Working code + Automatic progress tracking

**Quick Steps:**
1. Engineer runs `/implement-spec`
2. Agent-OS orchestrates sub-agents automatically
3. Code written, tests created, integration points connected
4. Progress auto-updates in Notion Progress Board
5. Senior Engineer reviews quality and gates merge

---

## 🔧 Handling Mid-Project Requests

**When a small change comes in mid-project, decide together:**

| **Scope** | **Entry Point** | **Example** |
|----------|----------------|-------------|
| **Large, unclear** | Phase 1 (Full Discovery) | New major feature, competing needs |
| **Medium, clear** | Phase 2 (Component PRD) | PM writes lightweight PRD |
| **Small, well-defined** | Phase 3 (/create-spec) | Add a field, simple change |

**Key principle:** Pod decides together based on scope, clarity, and risk.

---

## 📁 Where Everything Lives

### Notion (PM Workspace)
- **PRD Board:** Your PRDs and specs (Notion → GitHub sync)
- **Progress Board:** Real-time engineering progress (GitHub → Notion sync)

### GitHub (Engineering Workspace)
- **Specs:** `agent-os/specs/YYYY-MM-DD-{project}/`
- **Components:** Numbered sharded documents (01-, 02-, 03-...)
- **Project Config:** `agent-os/product/` (mission.md, tech-stack.md, roadmap.md)

---

## 🚨 Critical Gates

1. **PRFAQ Ratification (End of Phase 1)**
   - Must be approved by stakeholders before proceeding
   - PM leads review, gathers feedback, iterates

2. **Spec Review (Mid Phase 3)**
   - Entire pod reviews generated spec before implementation
   - PM: Validates business requirements
   - Prompt Engineer: Validates task clarity
   - Senior Engineer: Validates architecture and risks

3. **Quality Gate (End of Phase 4)**
   - Senior Engineer runs verifiers
   - Approval required before merge

---

## 💡 Pro Tips

**For PM:**
- Trust Mary's elicitation process—answer questions honestly
- Don't skip PRFAQ ratification, even if it feels redundant
- Watch Notion Progress Board instead of scheduling status meetings

**For Prompt Engineer:**
- Work through shards sequentially (01 → 02 → 03)
- Don't skip spec review—catches misalignment early
- If Agent-OS gets stuck, clarify requirements and retry

**For Senior Engineer:**
- Set quality standards early in Phase 2 (tech-stack.md, standards)
- Always run verifiers before approving merge
- Balance speed with quality—don't skip validation

**For All:**
- Communicate blockers immediately
- When in doubt, document more rather than less
- Keep Notion Progress Board updated (automatic for engineering)

---

## 📞 Quick Troubleshooting

**Problem:** Mary's questions seem off-topic  
**Solution:** Trust the process—elicitation surfaces unexpected insights

**Problem:** Agent-OS generates wrong architecture  
**Solution:** Check `product/tech-stack.md` is complete and accurate

**Problem:** Progress not showing in Notion  
**Solution:** Verify GitHub → Notion sync is configured (Phase 2 setup)

**Problem:** Don't know which phase to start at  
**Solution:** Use entry point decision framework (see above)

---

## 🎓 Remember

**Each pod member focuses on their expertise.** PM drives vision. Prompt Engineer orchestrates AI development. Senior Engineer ensures quality. Mary handles documentation. Agent-OS handles implementation. **The pod focuses on building the right thing, the right way, for our clients.**

---

*This is a living document. Update as processes evolve.*


