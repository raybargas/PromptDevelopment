# Role Playbooks
**The Rev.io Way - Detailed Guides for Each Role**

**Version:** 1.0  
**Last Updated:** 2025-01-XX

---

## 📋 Table of Contents
1. [Product Manager Playbook](#product-manager-playbook)
2. [Prompt Engineer Playbook](#prompt-engineer-playbook)
3. [Senior Engineer Playbook](#senior-engineer-playbook)
4. [Architect Playbook](#architect-playbook)

---

## 🎯 Product Manager Playbook

### Your Mission
**Lead product discovery, validate customer value, ensure stakeholder alignment, and hand off clear requirements to engineering.**

### Phase 1: Discovery with Mary

#### Getting Started
1. **Gather context before starting:**
   - Client focus group feedback
   - Prospect interviews and sales insights
   - Competitive research
   - Internal stakeholder perspectives

2. **Invoke Mary:**
   ```
   /analyst
   ```

3. **Start with elicitation (always):**
   - Mary will ask strategic questions
   - Be honest and comprehensive in your answers
   - Don't skip this—it surfaces unexpected insights

#### Key Activities During Discovery

**Answer Mary's questions about:**
- **Problem space:** What problem are we solving? For whom?
- **Users:** Who are they? What's their current workflow?
- **Goals:** What does success look like?
- **Constraints:** Technical, timeline, budget, resource limitations
- **Competition:** What exists today? How do we differentiate?

**Incorporate external insights:**
- Client pain points from focus groups
- Lost deal feedback from sales
- Competitive feature analysis
- Industry trends and best practices

#### Working with Mary's Outputs

**ProjectBrief.md**
- Review for accuracy on vision and problem statement
- Ensure target users are well-defined
- Validate business goals are measurable
- Confirm competitive context is accurate

**PRFAQ.md**
- Focus on customer value proposition
- Press release should be compelling to read
- FAQ should address key concerns
- Success metrics should be clearly defined

#### The Critical Gate: PRFAQ Ratification

**Why it matters:**
- This is "working backwards" methodology
- Validates customer value before building anything
- Prevents building the wrong thing
- Gets stakeholder buy-in early

**Who ratifies:**
- Executive leadership
- Product leadership
- Sales/success teams
- Key stakeholders

**The process:**
1. Schedule stakeholder review meeting
2. Present PRFAQ to all stakeholders
3. Gather honest feedback
4. Work with Mary to iterate
5. Achieve sign-off from all stakeholders
6. **DO NOT PROCEED** to Phase 2 without ratification

**Red flags to watch for:**
- Vague or non-committal feedback
- Stakeholders who say "looks good" but don't engage
- Disagreement in the room that gets swept under the rug
- Missing key stakeholders in the review

### Phase 2: Project Formation & PRD Creation

#### Complete PRD with Mary
1. Continue working with Mary using `/analyst`
2. Request full PRD creation
3. Ensure PRD includes:
   - Comprehensive problem statement
   - Functional and non-functional requirements
   - User epics defined
   - Success criteria
   - Constraints and dependencies

#### Collaborate on Sharding
**Work with your pod to shard the PRD:**

**Principles:**
- Each shard = one buildable piece
- Number sequentially (01-, 02-, 03-...)
- Organize by user flow, component area, or build order
- Each shard needs:
  - Detailed requirements
  - Architectural approach (high-level)
  - Technical metadata

**Example sharding:**
For a Project Management Module:
- `01-project-creation.md` - Create projects
- `02-phase-management.md` - Manage phases
- `03-milestone-tracking.md` - Track milestones
- `04-member-management.md` - Manage members
- `05-work-items.md` - Create work items

**Validate shards:**
- Review each shard for completeness
- Ensure no requirements are lost
- Verify sequencing makes sense
- Get team alignment

#### Handoff to Engineering
**Once shards are validated, hand off:**
- All sharded PRD documents
- Brief context on prioritization
- Any client constraints or special considerations
- Your availability for questions during spec review

### Phase 3 & 4: Stay Connected

#### Your Role During Implementation
**Watch, don't intervene:**
- Monitor Notion Progress Board
- Trust engineering to execute
- Only step in when blocked

**Client feedback loop:**
- Stay connected with clients as features ship
- Gather early feedback
- Prepare for iteration if needed

**No status meetings:**
- Notion Progress Board is your real-time status
- If something's blocked, you'll see it
- Spontaneous check-ins are fine

### Common Scenarios

**Scenario 1: Mary's questions seem off-topic**
- **Trust the process:** Elicitation surfaces unexpected insights
- **Answer honestly:** Mary needs the full picture
- **Stay patient:** Initial questions may seem basic but uncover nuance

**Scenario 2: Stakeholders want to skip PRFAQ ratification**
- **Push back:** This gate prevents costly mistakes
- **Explain:** "Working backwards" validates value before building
- **Provide data:** Show examples where skipping caused problems

**Scenario 3: Requirements aren't clear**
- **Go back to Mary:** Ask for more elicitation
- **Interview users:** Talk to actual users directly
- **Prototype:** Sometimes you need to see it to know what you want

**Scenario 4: Mid-project client request**
- **Assess scope:** Use entry point decision framework
- **Pod decides:** Collaborate with engineering on approach
- **Communicate timeline:** Set expectations with client

### Success Metrics
- PRFAQ ratified by all stakeholders
- Sharded PRDs complete and validated
- Zero "we built the wrong thing" moments
- Engineering has clear requirements to work from

---

## 🛠️ Prompt Engineer Playbook

### Your Mission
**Translate business requirements into technical implementation by orchestrating AI-powered development and bridging PM-engineering communication.**

### Phase 2: Receive Sharded PRDs

#### Initial Setup
1. **Read all sharded documents:**
   - Understand the full picture
   - Note dependencies between shards
   - Identify technical complexity

2. **Review Agent-OS config:**
   - Confirm `product/tech-stack.md` is complete
   - Review coding standards
   - Understand architecture patterns

3. **Plan your approach:**
   - Which shard to start with?
   - What's the technical complexity?
   - Any dependencies to resolve first?

### Phase 3: Technical Specification

#### Working Through Shards

**Step 1: Select current shard**
- Start with shard 01
- Work sequentially
- Don't skip shards

**Step 2: Feed to Agent-OS**
```
/create-spec [shard-document]
```

**What Agent-OS does:**
- Reads sharded PRD document
- Reads `product/tech-stack.md`
- Reads coding standards
- Generates features → stories → spec.md → tasks.md

**Step 3: Review generated spec**
- **Features:** Multiple features from shard scope?
- **Stories:** Clear user stories under each feature?
- **spec.md:** Architecture aligns with tech-stack?
- **tasks.md:** Granular tasks with dependencies?

**Step 4: Collaborate with pod**
- Present spec to team
- Facilitate spec review meeting
- Gather feedback from PM and Senior Engineer
- Iterate based on feedback

#### Common Issues and Solutions

**Issue: Agent-OS generates wrong architecture**
- **Check:** Is `product/tech-stack.md` complete?
- **Fix:** Update tech-stack.md with accurate details
- **Retry:** Feed shard to Agent-OS again

**Issue: Tasks aren't granular enough**
- **Prompt:** Ask Agent-OS to break down further
- **Guide:** Provide examples of desired granularity
- **Validate:** Ensure each task is independently buildable

**Issue: Agent-OS missing requirements**
- **Clarify:** Point to specific requirements in shard
- **Supplement:** Add clarifications to shard document
- **Retry:** Feed updated shard to Agent-OS

**Issue: Dependencies unclear**
- **Document:** Explicitly list dependencies
- **Sequence:** Ensure prerequisites are built first
- **Validate:** Confirm build order makes sense

### Phase 4: Implementation & Tracking

#### Execute Implementation

**Step 1: Run implementation**
```
/implement-spec
```

**Step 2: Monitor Agent-OS**
- Watch as it selects sub-agents
- Observe code being written
- Verify tests are created
- Confirm integration points are connected

**Step 3: Address blockers**
- If Agent-OS gets stuck, clarify requirements
- Provide additional context if needed
- Don't let it fail silently

**Step 4: Verify progress**
- Check GitHub roadmap updates
- Confirm Notion Progress Board reflects status
- Notify PM if blockers arise

#### Quality Checks During Implementation

**Before Senior Engineer review:**
- [ ] Code follows standards
- [ ] Tests are comprehensive
- [ ] Integration points work
- [ ] No obvious technical debt

**Common blocker scenarios:**

**Blocker: Agent-OS wants to use wrong library**
- **Fix:** Update `product/tech-stack.md` to specify correct library
- **Retry:** Feed shard again with correct context

**Blocker: Agent-OS doesn't understand API contracts**
- **Clarify:** Document API requirements explicitly
- **Provide:** Examples of similar implementations
- **Retry:** With clearer context

**Blocker: Tests are failing**
- **Debug:** Run tests locally
- **Fix:** Identify root cause
- **Guide:** Point Agent-OS to correct implementation
- **Retry:** Continue implementation

### Repeat for Each Shard

**After completing shard 01:**
1. Review output with Senior Engineer
2. Address any quality issues
3. Move to shard 02
4. Continue through all shards

### Success Metrics
- All shards have complete specs
- Tasks are clear and actionable
- Implementation is on track
- Quality gates pass smoothly

---

## 🏗️ Senior Engineer Playbook

### Your Mission
**Ensure quality, maintain architecture integrity, provide final approval to ship, while also performing Prompt Engineer duties for implementation execution.**

### Phase 2: Set Technical Foundation

#### Establish Standards

**Create `product/tech-stack.md`:**
- Frameworks: Which backend? Which frontend?
- Database: Which DB? Schema patterns?
- APIs: REST? GraphQL? Contract standards?
- Architecture: Patterns to follow

**Copy and customize standards:**
- Copy from `agent-os/standards/`
- Customize for project needs
- Document coding conventions
- Define testing requirements

**Set quality gates:**
- Test coverage thresholds
- Code review requirements
- Performance benchmarks
- Security requirements

#### Review Agent-OS Config
- Verify tech-stack.md accuracy
- Ensure standards are complete
- Validate architecture patterns
- Approve for Phase 3 use

### Phase 3: Spec Review Gate

#### Review Each Generated Spec

**Architecture validation:**
- [ ] Aligns with system design
- [ ] Follows established patterns
- [ ] No technical risks identified
- [ ] Dependencies are manageable

**Technical quality:**
- [ ] spec.md is technically sound
- [ ] Database schema is well-designed
- [ ] API contracts are clear
- [ ] Component architecture is clean

**Risk assessment:**
- Are there performance concerns?
- Security implications?
- Scalability considerations?
- Integration complexities?

#### Provide Feedback
- Highlight any architectural concerns
- Suggest improvements if needed
- Ask clarifying questions
- Approve when ready

### Phase 4: Implementation Execution

#### Perform Prompt Engineer Duties

**As Senior Engineer, you also:**
- Feed sharded PRD documents to Agent-OS
- Execute `/create-spec` and `/implement-spec`
- Monitor Agent-OS progress
- Address blockers and clarifications

**Why both roles?**
- You're responsible for implementation quality
- You understand technical trade-offs
- You can guide Agent-OS when needed
- You maintain architecture integrity throughout

#### Monitor Implementation Quality

**During execution:**
- Watch for quality deviations
- Catch technical debt early
- Guide Agent-OS when needed
- Maintain architectural integrity

**After execution:**
- Review all generated code
- Run comprehensive tests
- Check test coverage
- Verify integration points

### Quality Gate Process

#### Run Verifiers

**Before approval:**
1. **Backend verifier:**
   - Code quality
   - API correctness
   - Database integrity

2. **Frontend verifier:**
   - Component quality
   - UI/UX adherence
   - Performance

3. **Test verifier:**
   - Coverage thresholds
   - Test quality
   - Integration completeness

4. **Implementation verifier:**
   - Requirements met
   - Architecture followed
   - Standards compliance

#### Approve or Request Changes

**Approve if:**
- All verifiers pass
- Code quality is high
- Tests are comprehensive
- No technical debt introduced

**Request changes if:**
- Verifiers identify issues
- Code quality concerns
- Missing test coverage
- Architecture deviations

**Don't compromise on:**
- Code quality
- Test coverage
- Architecture integrity
- Security standards

### Common Scenarios

**Scenario 1: Agent-OS introduces technical debt**
- **Catch early:** Review code during implementation
- **Refactor immediately:** Don't let it accumulate
- **Guide Agent-OS:** Show correct patterns
- **Document:** Update standards if needed

**Scenario 2: Tests are missing**
- **Require:** Comprehensive test coverage
- **Guide:** Point Agent-OS to testing standards
- **Validate:** Run verifiers before approval
- **Don't merge:** Without proper tests

**Scenario 3: Architecture doesn't align**
- **Stop:** Don't continue with wrong architecture
- **Update:** Fix tech-stack.md or standards
- **Guide:** Provide explicit architectural guidance
- **Retry:** With correct foundation

**Scenario 4: Performance concerns**
- **Assess:** Benchmark current performance
- **Optimize:** Address bottlenecks
- **Document:** Performance requirements
- **Test:** Under load

### Success Metrics
- Zero architectural deviations
- High test coverage on all components
- All verifiers pass consistently
- Clean, maintainable code delivered

---

## 🏛️ Architect Playbook

### Your Mission
**Define technical foundation, establish architecture patterns, and provide guidance on complex technical decisions.**

### Phase 2: Technical Foundation Setup

#### Define Architecture

**Create `product/tech-stack.md`:**
- **Backend:** Framework, language, patterns
- **Frontend:** Framework, state management, UI library
- **Database:** Type, schema patterns, ORM
- **APIs:** REST/GraphQL, contract standards
- **Infrastructure:** Hosting, CI/CD, monitoring

**Establish Patterns:**
- Architecture patterns (MVC, microservices, etc.)
- Design patterns (factory, observer, etc.)
- Data access patterns
- Error handling patterns
- Logging and monitoring patterns

**Set Standards:**
- Copy from `agent-os/standards/`
- Customize for project needs
- Document coding conventions
- Define security standards

#### Review with Engineering Team
- Ensure standards are clear
- Validate architecture decisions
- Get team buy-in
- Document any trade-offs

### Ongoing Technical Guidance

#### Complex Decisions
**When to step in:**
- Architecture choices that affect multiple systems
- Performance-critical decisions
- Security implications
- Scalability concerns
- Integration complexities

**Your role:**
- Provide technical guidance
- Evaluate trade-offs
- Make difficult decisions
- Document rationale

#### Update Standards
**Keep standards current:**
- Update as patterns evolve
- Incorporate learnings
- Address new challenges
- Maintain consistency

### Success Metrics
- Clear technical foundation established
- Architecture patterns consistently followed
- Complex decisions well-documented
- Team aligned on technical approach

---

## 🤝 Pod Collaboration Moments

### Spec Review (Phase 3)
**Who:** PM + Prompt Engineer + Senior Engineer  
**When:** After Agent-OS generates spec  
**Purpose:** Validate alignment before implementation

**Each role validates:**
- **PM:** Business requirements captured correctly?
- **Prompt Engineer:** Tasks clear and actionable?
- **Senior Engineer:** Architecture sound and risks low?

### Quality Gate (Phase 4)
**Who:** Senior Engineer leads, team informed  
**When:** After implementation complete  
**Purpose:** Ensure quality before merge

**Process:**
- Senior Engineer runs verifiers
- Reviews code quality
- Gates merge approval
- Team celebrates milestone

### Blocker Resolution
**Who:** Entire pod  
**When:** Anytime a blocker arises  
**Purpose:** Unblock progress quickly

**Process:**
- Identify blocker
- Pod huddles (5 minutes)
- Decide on approach
- Execute solution
- Communicate update

---

*These playbooks are living documents. Update based on role learnings and process evolution.*


