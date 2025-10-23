# Decision Framework
**The Rev.io Way - How to Make Common Decisions**

**Version:** 1.0  
**Last Updated:** 2025-01-XX

---

## 🎯 Which Phase Do I Start At?

### Use This Framework for Mid-Project Requests

When a new request comes in during an active project, use this decision tree to determine where to enter the workflow.

---

## Decision Tree

```
                    New Request Comes In
                           |
                           |
                    ┌──────┴──────┐
                    │             │
            Requirements       Requirements
             Are Clear?        Are Unclear?
                    │             │
                    │             │
              Yes   │      ┌──────┴──────┐
                    │      │             │
                    │  Small Change  Large Feature
                    │      │             │
                    │      │             │
         ┌──────────┴──────┴─────────────┴──────────┐
         │                                          │
    Start at Phase 3                          Start at Phase 1
    (/create-spec)                    (Discovery with Mary)
         │                                          │
         │                                          │
    Well-defined                             Unclear Requirements
    Small change                             Multiple Stakeholders
    Low complexity                           Significant Business Impact
    Low risk                                 Requires Validation
```

---

## 📊 Decision Matrix

| **Scenario** | **Entry Point** | **Reasoning** |
|------------|----------------|---------------|
| New major feature or module | Phase 1 (Full Discovery) | Unclear requirements, multiple stakeholders, significant impact |
| Requirements unclear, problem space fuzzy | Phase 1 (Full Discovery) | Need elicitation and validation |
| Multiple stakeholders with competing needs | Phase 1 (Full Discovery) | Need consensus building |
| Significant business impact or risk | Phase 1 (Full Discovery) | Justifies full discovery process |
| Client validation required | Phase 1 (Full Discovery) | Need PRFAQ ratification |
| Clear requirements, medium-sized feature | Phase 2 (Component PRD) | Requirements known, needs documentation |
| Client/stakeholder alignment exists | Phase 2 (Component PRD) | Skip validation, write PRD |
| Fits within existing architecture | Phase 2 (Component PRD) | No new architecture needed |
| Small, well-defined change | Phase 3 (/create-spec) | Simple, straightforward, low risk |
| Pod agrees on approach in 5-minute huddle | Phase 3 (/create-spec) | Quick consensus, proceed |
| Low complexity, low risk | Phase 3 (/create-spec) | Trust pod decision-making |
| Brief written summary sufficient | Phase 3 (/create-spec) | Don't need full PRD |

---

## 🔍 Detailed Entry Point Criteria

### Start at Phase 1: Full Discovery with Mary

**When to use:**
- New major feature or module
- Unclear requirements or problem space
- Multiple stakeholders (clients, prospects, internal) with competing needs
- Significant business impact or risk
- Requires PRFAQ ratification and focus group validation

**What happens:**
1. PM invokes Mary with `/analyst`
2. Mary conducts elicitation
3. Generate ProjectBrief + PRFAQ
4. PRFAQ ratification gate
5. Proceed through all phases

**Example:**
- New Product Management Module
- Clear problem, but many stakeholders
- Need validation across client groups
- Significant development effort

---

### Start at Phase 2: Component PRD

**When to use:**
- Requirements are clear but need formal documentation
- Medium-sized feature that fits within existing architecture
- Client/stakeholder alignment already exists
- PM writes lightweight component PRD

**What happens:**
1. PM writes lightweight component PRD
2. Hand to engineering
3. Skip Phase 1 (PRFAQ)
4. Proceed through Phases 2 → 3 → 4

**Example:**
- Adding "Priority" field to existing projects
- Requirements clear from client calls
- Small to medium scope
- Fits existing architecture

---

### Start at Phase 3: Create Spec

**When to use:**
- Small, well-defined change (like adding a field)
- Pod has quick conversation and reaches agreement
- Low complexity, low risk, no client validation needed
- Requirements fit in a brief written summary

**What happens:**
1. Pod has 5-minute huddle
2. Reach agreement on requirements
3. Document brief written summary
4. Start at `/create-spec`
5. Continue through Phases 3 → 4

**Example:**
- Add "Priority" dropdown to project form
- Pod agrees: High/Medium/Low values
- Straightforward database + UI change
- No architecture impact

---

## 🎓 Pod Decision Process

### The 5-Minute Huddle

**When to have it:**
- Mid-project request comes in
- Scope is ambiguous
- Pod needs to align on approach

**How it works:**
1. **PM presents:** What's the request? What do clients need?
2. **Engineering assesses:** Technical complexity? Architecture impact?
3. **Pod discusses:** Entry point? Risks? Concerns?
4. **Decision:** Where to start? Who owns what?
5. **Execute:** Begin work at agreed entry point

**Key questions:**
- Is this clear or ambiguous?
- Is this small, medium, or large?
- Do we need client validation?
- Are there technical risks?
- Can we document in brief summary?

---

## 🚨 Red Flags: Don't Skip Discovery

**Warning signs you should start at Phase 1:**

- [ ] Multiple stakeholders giving different requirements
- [ ] "I'll know it when I see it" responses
- [ ] Significant business impact uncertain
- [ ] Technical approach unclear
- [ ] "We need this ASAP" pressure
- [ ] Scope keeps expanding in conversation
- [ ] No clear success criteria

**If you see these flags:**
- Push back on skipping discovery
- Explain "working backwards" methodology
- Invest time in Phase 1 to save time later
- Get stakeholder alignment before building

---

## 📝 Documentation Requirements

### Phase 1 Entry
**Minimum Documentation:**
- ProjectBrief.md
- PRFAQ.md (ratified)
- PRD.md
- Sharded component documents

**Why:** Full validation and consensus

---

### Phase 2 Entry
**Minimum Documentation:**
- Lightweight component PRD
- Requirements summary
- Architectural approach

**Why:** Clear requirements, minimal formality

---

### Phase 3 Entry
**Minimum Documentation:**
- Brief written summary
- Pod agreement documented
- Technical approach aligned

**Why:** Speed for simple changes

---

## 💡 Decision Principles

### Principle 1: When in Doubt, Document More
- Bias toward more documentation rather than less
- Better to over-document than under-document
- Documentation prevents misalignment

### Principle 2: Client-Facing Changes Need PM Validation
- Any change users will see
- PM should validate requirement clarity
- Align with business goals

### Principle 3: Pod Decides Together
- Not PM-only decision
- Not engineering-only decision
- Collaborative assessment of scope and complexity

### Principle 4: Risk Increases with Ambiguity
- Unclear requirements = high risk
- Multiple stakeholders = high risk
- Complex technical scope = high risk
- Higher risk = more documentation needed

### Principle 5: Speed Comes from Clarity
- Clear requirements enable fast execution
- Skipping discovery doesn't speed things up
- Invest in clarity to save time later

---

## 🔄 Iteration Within Phases

### Can I Iterate Without Starting Over?

**Yes, within limits:**

**Within Phase 1:**
- Iterate on PRFAQ with Mary
- Refine requirements
- Adjust scope
- Repackage but don't restart

**Within Phase 2:**
- Modify component PRD
- Adjust sharding
- Update technical approach
- Don't need to go back to Phase 1

**Within Phase 3:**
- Adjust spec based on review
- Modify tasks breakdown
- Clarify requirements
- Iterate on spec before implementation

**Within Phase 4:**
- Refactor during implementation
- Adjust approach based on learnings
- Don't need to regenerate spec

**Restart Phase 1 if:**
- Requirements fundamentally changed
- New major stakeholder introduced
- Business impact significantly altered
- Discovery assumptions were wrong

---

## 🎯 Example Scenarios

### Scenario 1: Mid-Project Client Request
**Request:** "Can we add project templates?"

**Pod Discussion:**
- PM: "Multiple clients asked for this. It's a new feature."
- Engineering: "Medium complexity, new database tables, UI changes."
- Prompt Engineer: "Requires discovery to understand templates."

**Decision:** Start at Phase 1 (Full Discovery)

**Rationale:** New feature, client validation needed, medium complexity

---

### Scenario 2: Clarification Request
**Request:** "Make the project name field required"

**Pod Discussion:**
- PM: "Straightforward validation change."
- Engineering: "One line in validation schema."
- Prompt Engineer: "Clear requirements."

**Decision:** Start at Phase 3 (/create-spec)

**Rationale:** Simple, well-defined, low risk

---

### Scenario 3: Enhancement Request
**Request:** "Add custom fields to projects"

**Pod Discussion:**
- PM: "Fits existing architecture but adds complexity."
- Engineering: "EAV pattern, needs thought on schema."
- Prompt Engineer: "Requires spec to get architecture right."

**Decision:** Start at Phase 2 (Component PRD)

**Rationale:** Medium complexity, needs some documentation

---

## 📚 Quick Reference Table

| **Start Here** | **When** | **Pod Huddle** | **Time** |
|---------------|----------|----------------|----------|
| Phase 1 | Unclear, complex, high impact | Required | Days |
| Phase 2 | Clear, medium, validated | Quick alignment | Hours |
| Phase 3 | Simple, well-defined, low risk | 5 minutes | Minutes |

---

*Use this framework for all mid-project decisions. When in doubt, err on the side of more documentation.*


