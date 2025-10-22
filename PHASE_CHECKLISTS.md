# Phase Checklists
**The Rev.io Way - Task Checklists for Each Phase**

**Version:** 1.0  
**Last Updated:** 2025-01-XX

---

## Phase 1: Discovery with Mary (PM)

### Pre-Phase Setup
- [ ] Gather client focus group feedback
- [ ] Conduct competitive research
- [ ] Review sales team insights on lost deals
- [ ] Prepare initial problem statement
- [ ] Invoke Mary with `/analyst`

### During Discovery
- [ ] Answer Mary's strategic questions about:
  - [ ] Problem space and pain points
  - [ ] Target users and their needs
  - [ ] Business goals and success metrics
  - [ ] Competitive landscape
  - [ ] Constraints and limitations
- [ ] Incorporate insights from:
  - [ ] Client focus groups
  - [ ] Prospect feedback
  - [ ] Competitive analysis
  - [ ] Internal stakeholders

### Outputs to Validate
- [ ] **ProjectBrief.md**
  - [ ] Vision statement is clear
  - [ ] Problem statement resonates with users
  - [ ] Target users are well-defined
  - [ ] Business goals are measurable
  - [ ] Competitive context is accurate
- [ ] **PRFAQ.md**
  - [ ] Customer value proposition is clear
  - [ ] Press release narrative is compelling
  - [ ] FAQ addresses key concerns
  - [ ] Success metrics are defined

### PRFAQ Ratification Gate
- [ ] Schedule stakeholder review meeting
- [ ] Present PRFAQ to:
  - [ ] Executive leadership
  - [ ] Product leadership
  - [ ] Sales/success teams
- [ ] Gather feedback and iterate
- [ ] Achieve stakeholder approval
- [ ] **CRITICAL:** Do not proceed to Phase 2 without ratification

### Handoff Checklist
- [ ] ProjectBrief.md approved
- [ ] PRFAQ.md ratified by all stakeholders
- [ ] Ready to move to Phase 2
- [ ] Notify team that discovery is complete

---

## Phase 2: Project Formation & PRD Creation (Team)

### PM: Complete Discovery
- [ ] Work with Mary to create full PRD
- [ ] Ensure PRD includes:
  - [ ] Problem statement
  - [ ] Requirements (functional + non-functional)
  - [ ] Epics defined
  - [ ] Success criteria
  - [ ] Constraints and dependencies
- [ ] Validate PRD completeness with Mary

### Team: Shard PRD
- [ ] Collaborate to break PRD into components
- [ ] Organize by:
  - [ ] User flow
  - [ ] Component area
  - [ ] Build order
- [ ] Number sequentially (01-, 02-, 03-...)
- [ ] Each shard should include:
  - [ ] Detailed requirements
  - [ ] Architectural approach
  - [ ] Technical metadata
- [ ] Validate sharded documents with team

### Engineering: Set Up Infrastructure
- [ ] **Notion Board Setup**
  - [ ] Create PRD Board (Notion → GitHub sync)
  - [ ] Create Progress Board (GitHub → Notion sync)
  - [ ] Configure bidirectional sync for PRD Board
  - [ ] Configure one-way sync for Progress Board
  - [ ] Verify sync is working
- [ ] **Agent-OS Configuration**
  - [ ] Copy templates from `agent-os/standards/`
  - [ ] Create `product/mission.md` with:
    - [ ] Project vision
    - [ ] Goals
    - [ ] Success metrics
  - [ ] Create `product/roadmap.md` with:
    - [ ] Development phases
    - [ ] Timeline
  - [ ] Create `product/tech-stack.md` with:
    - [ ] Frameworks (backend + frontend)
    - [ ] Database choices
    - [ ] API approaches
    - [ ] Architecture patterns
  - [ ] Review coding standards in `standards/`

### Team Validation
- [ ] Review all sharded documents together
- [ ] Ensure each shard represents one buildable piece
- [ ] Verify sequential order makes sense
- [ ] Confirm technical metadata is complete
- [ ] Align on sharding approach

### Handoff Checklist
- [ ] PRD.md complete and validated
- [ ] Sharded documents numbered and sequenced
- [ ] Notion boards configured and syncing
- [ ] Agent-OS project config complete
- [ ] Technical standards documented
- [ ] Team aligned on approach
- [ ] Ready to move to Phase 3

---

## Phase 3: Technical Specification (Prompt Engineer + Senior Engineer)

### Pre-Specification
- [ ] Verify sharded PRD documents are accessible
- [ ] Confirm Agent-OS project config is complete
- [ ] Review `product/tech-stack.md` for accuracy
- [ ] Understand coding standards

### Working Through Shards
- [ ] **Select current shard** (start with 01)
- [ ] Read sharded document completely
- [ ] Feed document to Agent-OS with `/create-spec`
- [ ] Monitor Agent-OS progress

### Validate Generated Spec
- [ ] **Features:** Logically organized?
- [ ] **Stories:** Clear and actionable?
- [ ] **spec.md:** Architecture aligns with tech-stack?
- [ ] **tasks.md:** Granular enough with dependencies?
- [ ] Review with pod before implementation

### Pod Spec Review Gate
- [ ] **PM validates:**
  - [ ] Business requirements captured correctly
  - [ ] Will meet client needs
- [ ] **Prompt Engineer validates:**
  - [ ] Tasks are clear and actionable
  - [ ] Breakdown is logical
- [ ] **Senior Engineer validates:**
  - [ ] Architecture aligns with system design
  - [ ] No technical risks identified
  - [ ] Standards are followed
- [ ] Iterate on spec based on feedback
- [ ] Get alignment across team

### Repeat for Each Shard
- [ ] Complete shard 01 → Review → Approved
- [ ] Complete shard 02 → Review → Approved
- [ ] Complete shard 03 → Review → Approved
- [ ] Continue sequentially through all shards

### Handoff Checklist
- [ ] All shards have generated specs
- [ ] Each spec reviewed and approved by pod
- [ ] Technical architecture validated
- [ ] Tasks breakdown logical
- [ ] Ready to move to Phase 4

---

## Phase 4: Implementation & Tracking (Prompt Engineer + Senior Engineer)

### Pre-Implementation
- [ ] Verify spec is approved by pod
- [ ] Confirm test environment is set up
- [ ] Review technical dependencies
- [ ] Clear any blockers

### Execute Implementation
- [ ] Run `/implement-spec` for current shard
- [ ] Monitor Agent-OS as it:
  - [ ] Selects appropriate sub-agents
  - [ ] Writes code
  - [ ] Creates tests
  - [ ] Connects integration points
- [ ] Watch for any Agent-OS errors or blockers
- [ ] Address clarifications promptly

### Validate Implementation
- [ ] **Code Quality:**
  - [ ] Follows coding standards
  - [ ] Architecture integrity maintained
  - [ ] No technical debt introduced
- [ ] **Tests:**
  - [ ] Unit tests pass
  - [ ] Integration tests pass
  - [ ] Test coverage meets standards
- [ ] **Integration:**
  - [ ] All integration points working
  - [ ] No breaking changes
  - [ ] Backward compatibility maintained

### Quality Gate (Senior Engineer)
- [ ] Run verifier agents:
  - [ ] Backend verifier
  - [ ] Frontend verifier
  - [ ] Test verifier
  - [ ] Implementation verifier
- [ ] Review verifier outputs
- [ ] Address any quality issues
- [ ] **Approve for merge**

### Progress Tracking
- [ ] Verify progress updates in GitHub roadmap
- [ ] Confirm Notion Progress Board shows latest status
- [ ] Update PM if blockers arise
- [ ] Mark shard as complete in Progress Board

### Complete Shard
- [ ] All features implemented
- [ ] All stories complete
- [ ] Tests passing
- [ ] Quality gate passed
- [ ] Merged to main branch
- [ ] Move to next shard

### Ongoing Monitoring
- [ ] **Prompt Engineer:** Execute `/implement-spec`, monitor progress
- [ ] **Senior Engineer:** Review quality, run verifiers, gate merges
- [ ] **PM:** Watch Notion Progress Board, stay connected with clients

### Completion Checklist
- [ ] All shards implemented
- [ ] All quality gates passed
- [ ] Tests passing for all components
- [ ] Integration points working
- [ ] Progress Board shows 100% complete
- [ ] Ready for deployment

---

## 🔧 One-Off Request Checklist

### Assess Scope
- [ ] Is this a large, unclear feature? → Phase 1
- [ ] Is this a medium-sized, clear feature? → Phase 2
- [ ] Is this a small, well-defined change? → Phase 3

### Small Change Path (Skip to Phase 3)
- [ ] Pod has 5-minute huddle
- [ ] Reach agreement on requirements
- [ ] Document brief written summary
- [ ] Proceed with `/create-spec`
- [ ] Continue through Phase 3 → Phase 4

### Medium Change Path (Skip to Phase 2)
- [ ] PM writes lightweight component PRD
- [ ] Hand to engineering
- [ ] Continue through Phase 2 → Phase 3 → Phase 4

### Large Change Path (Full Discovery)
- [ ] Return to Phase 1
- [ ] Work with Mary
- [ ] Complete full discovery
- [ ] Proceed through all phases

---

## 📊 Progress Tracking Checklist

### Daily
- [ ] Check Notion Progress Board
- [ ] Note completed items
- [ ] Identify blockers
- [ ] Address urgent items

### Weekly
- [ ] Review overall progress across all shards
- [ ] Assess if timeline is on track
- [ ] Re-evaluate prioritization if needed
- [ ] Communicate with stakeholders

### End of Phase
- [ ] Document lessons learned
- [ ] Update templates if needed
- [ ] Celebrate milestones
- [ ] Prepare for next phase

---

*These checklists are living documents. Update based on project learnings.*


