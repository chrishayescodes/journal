---
title: "Ask-Based Planning: How to Actually Make Decisions in Software Teams"
date: 2025-01-10
tags: [planning, management, decision-making, methodology]
---

# Ask-Based Planning: How to Actually Make Decisions in Software Teams

Stop overthinking. Start asking: "What's the actual ask here?"

Every software project drowns in complexity—architectural debates, framework wars, process ceremonies. But what if we reduced everything to a simple question: What are we actually being asked to deliver?

## The Fundamental Problem with Modern Planning

We've inverted the planning process. We start with:
- What's the best architecture?
- What framework should we use?
- What would be the most elegant solution?

When we should start with:
- What's the deadline?
- What's the budget?
- Who's going to build this?
- What problem are we solving?

This isn't settling for mediocrity. It's acknowledging reality.

## Why "Ask" Instead of Bug/Story/Task?

Traditional issue tracking creates unnecessary complexity:

### The Taxonomy Problem
Teams waste hours debating:
- "Is this a bug or a feature request?"
- "Should this be a story or a task?"
- "Is it an epic or just a large story?"
- "Does a bug in a new feature count as a defect?"

**Meanwhile, what actually matters:**
- How important is this?
- How much work is it?
- Who's affected?
- When do we do it?

### The Status Game
Traditional categories create politics:
- "Bugs" automatically get priority over "features"
- "Technical debt" gets ignored because it's not a "story"
- "Tasks" sound less important than "epics"
- Teams game the system: "Let's call it a bug so it gets prioritized"

### The Beautiful Simplicity of "Ask"
Everything is just an ask:
- Customer asks for checkout to work → Ask
- CEO asks for new dashboard → Ask
- Developer asks to refactor code → Ask
- Support asks to fix login issue → Ask

**No taxonomy arguments.** Just evaluate each ask on its merits:
- Impact (who needs this?)
- Effort (how hard is it?)
- Priority (how important is it?)
- Risk (what could go wrong?)

### Real Example
**Traditional Approach:**
```
Type: Bug
Severity: P2
Component: Authentication
Labels: backend, security, customer-reported
Story Points: 5
Epic: User Management
```

**Ask-Based Approach:**
```
ASK: Users can't reset passwords
IMPACT: 50+ support tickets daily
EFFORT: 2 days
PRIORITY: 1 (blocking customers)
DECISION: Fix today
```

Which one helps you make decisions faster?

## The Three Pillars of Ask-Based Planning

### 1. Identify the Unmovables

Some things don't change. Amazon built an empire on three constants:
- People want things cheaper
- People want things faster
- People want decent quality

These haven't changed in 30 years. They won't change in the next 30.

**Your unmovables might be:**
- Users want pages to load fast
- The system must be available 24/7
- Customers need to trust their data is safe
- The business needs to make money

Stop chasing trends. Build around constants.

### 2. Map Your Actual Constraints

Constraints aren't limitations—they're clarity. Every real project has:

**Budget Constraints**
- "We have $50K, not $500K"
- "We can't afford a dedicated DevOps team"
- "Cloud costs must stay under $1000/month"

**Team Constraints**
- "We have 3 developers, not 30"
- "Nobody knows Rust"
- "Sarah is the only one who understands the payment system"

**Time Constraints**
- "The conference is in 6 weeks"
- "Compliance deadline is March 1st"
- "Competitor launches similar feature next month"

**Infrastructure Constraints**
- "We're stuck with this database"
- "Can't migrate off Windows Server"
- "The CEO loves Excel exports"

Acknowledge these. Plan around them. Stop pretending they'll magically disappear.

### 3. Make Decisions Based on the Ask

Every technical decision should answer: "What are we being asked to deliver?"

**Example: "Build a customer dashboard"**

Traditional approach:
- Debate React vs Vue for 2 weeks
- Design perfect microservice architecture
- Plan comprehensive testing strategy
- Estimate: 6 months

Ask-based approach:
- Who needs this? (5 internal users)
- When? (Board meeting in 3 weeks)
- What's the core need? (See monthly revenue)
- Solution: SQL query + basic HTML table
- Delivered: 2 days

## The Decision Framework

For every technical choice, ask in this order:

1. **What's the actual ask?**
   - Not what you think they need
   - Not what would be cool to build
   - What they literally asked for

2. **What are our unmovable constraints?**
   - Deadline (when must this ship?)
   - Budget (what can we actually spend?)
   - Team (who's actually available?)
   - Technical (what systems must we use?)

3. **What's the simplest solution that satisfies both?**
   - Not the best solution
   - Not the most scalable solution
   - The solution that ships on time and works

## Getting to the Real Ask: The 5 Whys

Most asks are symptoms, not root causes. Drill down to find what's really needed:

### Example 1: "We need a dashboard"

**Ask:** "We need a real-time analytics dashboard"

**Why 1:** Why do you need a dashboard?
→ "To see our sales numbers"

**Why 2:** Why do you need to see sales numbers?
→ "To know if we're hitting targets"

**Why 3:** Why don't you know if you're hitting targets?
→ "The reports come monthly and are always late"

**Why 4:** Why are reports monthly and late?
→ "Bob manually compiles them from 3 systems"

**Why 5:** Why does Bob manually compile them?
→ "The systems don't talk to each other"

**Real Ask:** Automate data export from 3 systems (2 days work)
**Not:** Build complex real-time dashboard (2 months work)

### Example 2: "The system is slow"

**Ask:** "We need to rewrite the system for performance"

**Why 1:** Why do you think we need a rewrite?
→ "The system is too slow"

**Why 2:** Why is it slow?
→ "Pages take 10 seconds to load"

**Why 3:** Why do pages take 10 seconds?
→ "The database queries are slow"

**Why 4:** Why are the queries slow?
→ "We're loading all customer history on every page"

**Why 5:** Why are we loading all history?
→ "The original developer thought we might need it"

**Real Ask:** Add pagination to customer history query (4 hours work)
**Not:** Rewrite entire system (6 months work)

### The Pattern

Surface ask → Often an expensive solution to a symptom
Deep ask → Usually a simple fix to the root cause

**Questions that reveal the real ask:**
- "What problem are you trying to solve?"
- "What happens if we don't do this?"
- "What would success look like?"
- "Have you tried anything else?"
- "When did this become a problem?"

### When to Stop Asking Why

Stop when you reach:
- **External constraint:** "Because regulations require it"
- **Business fundamental:** "Because that's how we make money"
- **Actual user need:** "Because customers can't check out"
- **Technical reality:** "Because the server only has 2GB RAM"

### The Anti-Pattern: Solution Disguised as Ask

**Red flags:**
- "We need microservices" (That's a solution, not an ask)
- "We need to use React" (That's a technology choice, not a need)
- "We need to refactor everything" (That's an approach, not a problem)

**Always translate to actual need:**
- "We need microservices" → "We need to scale different parts independently"
- "We need React" → "We need better UI interactivity"
- "We need to refactor" → "We can't add features without breaking things"

Then ask: Is the proposed solution the simplest way to meet the actual need?

## Real-World Applications

### The "Investigation Budget" Approach

Instead of endless analysis paralysis:
- "Spend 2 days investigating payment providers"
- "Take a week to prototype both approaches"
- "Research for 3 days, then we decide"

Time-boxed investigation with clear decision points.

### The "Harvest vs. Perfect" Principle

- **Farmer mentality:** "Get crops to market"
- **Engineer mentality:** "Optimize yield perfectly"

Good enough that ships beats perfect that doesn't.

### The "Natural Organization" Pattern

Let constraints drive organization:
- Database slow? → Database expert leads optimization
- API integration needed? → API person takes point
- UI broken? → Frontend dev drives fix

No complex ceremonies. Clear ownership based on expertise.

## The Estimation Problem: Why Story Points Failed

### The Theater of False Precision

Traditional estimation creates elaborate rituals with no value:

**Planning Poker**
- Spend 2 hours debating if something is 5 or 8 points
- Fibonacci sequences pretending complexity is mathematical
- Team consensus that's really just averaging wild guesses
- Points that mean different things to different people

**Velocity Tracking**
- "We completed 47 points last sprint!"
- But what value was delivered?
- Points inflate over time (gaming the system)
- Velocity becomes the goal instead of value

### What Estimates Actually Communicate

The precision paradox reveals the truth:

**"1 hour"** = "I've done this exact thing before"
- High confidence
- Probably accurate

**"2-3 days"** = "I understand the problem"
- Medium confidence
- Reasonable accuracy

**"2 weeks"** = "This is complex but I see the pieces"
- Getting uncertain
- Could be 1-4 weeks

**"2 months"** = "I have no idea"
- Very low confidence
- Could be 2 weeks or 6 months

**The pattern:** Long estimates are really saying "I don't understand this yet."

### The Confidence-Based Approach

Instead of false precision, be honest:

```
ASK: Add user profiles
ESTIMATE: 1-3 weeks
CONFIDENCE: Low (30%)
WHY LOW: Never built profiles, unsure about requirements
NEXT STEP: 2-day investigation to understand better
```

### Investigation Budgets: Buying Certainty

When confidence is low, time-box investigation:

**"Spend 2 days researching, then estimate"**
Better than: "It'll take 2 months (maybe)"

**"Build a prototype for 1 week, then decide"**
Better than: "The architecture might not work"

**"Talk to 3 users, then scope it"**
Better than: "We think users want this"

### Knowing When to Abandon

Set investigation limits upfront:

```
INVESTIGATION BUDGET: 1 week
ABANDON IF:
- Estimate exceeds 3 months
- Requires skills we don't have
- Third-party API doesn't support our needs
- Compliance requirements too complex
```

Don't fall for sunk cost fallacy. Sometimes the best decision is "This isn't worth it."

### Patterns Over Predictions

Track what actually happens:

- "Database work always takes 2x our estimate"
- "UI changes are usually accurate"
- "Third-party integrations always have surprises"
- "Sarah's estimates are consistently reliable"

Use patterns to adjust future estimates, not story points to create velocity theater.

## Training Teams in Ask-Based Thinking

### Week 1: The Constants Exercise
List what won't change:
- What do users always want?
- What does the business always need?
- What technical realities persist?

### Week 2: The Constraint Audit
Document reality:
- Actual budget (not wished-for budget)
- Actual team skills (not theoretical capabilities)
- Actual deadlines (not ideal timelines)

### Week 3: The Decision Practice
For every decision this week:
- First ask: "What's the ask?"
- Then check: "What constraints apply?"
- Finally decide: "What's simplest that works?"

### Week 4: The Retrospective Reality Check
- Which decisions served the ask?
- Which decisions ignored constraints?
- What would we do differently?

## The Priority Hierarchy That Makes Decisions Automatic

Stop debating. Use this order:

### Priority 1: Does this block customers?
- Site down, can't log in, can't purchase
- **Decision time:** Immediate
- **Who decides:** Anyone can call Priority 1

### Priority 2: Legal/Security/Compliance Risk?
- Data breach, regulatory violation, security hole
- **Decision time:** Within 24 hours
- **Who decides:** Security/legal team escalates

### Priority 3: Does this make/save significant money?
- New revenue stream, major cost reduction
- **Decision time:** This week
- **Who decides:** Product/business owner

### Priority 4: Performance/Reliability Issues?
- Slow but working, occasional failures
- **Decision time:** Next sprint
- **Who decides:** Tech lead with product input

### Priority 5: Everything Else
- Nice-to-haves, UI improvements, refactoring
- **Decision time:** When there's capacity
- **Who decides:** Team consensus

**This eliminates arguments.** Higher priority always wins. Most decisions make themselves.

## The Triage Mindset: Medical Emergency Room for Software

Think like an ER doctor, not an architect:

### Red (Immediate)
- System down, data loss, security breach
- **Drop everything**

### Yellow (Delayed)
- Performance issues, reliability problems
- **Fix this week**

### Green (Walking Wounded)
- UI bugs, minor issues
- **Fix when possible**

### Black (Expectant)
- Legacy systems too broken to save
- **Plan replacement, don't waste resources**

**Triage Discipline:**
- Don't fix green issues while red patients are dying
- Don't spend hours on black cases when yellow needs help
- Constantly reassess—conditions change

## The Pre-Ask Checklist: Right-Sizing Your Response

Not every ask needs a full analysis. Triage first:

### Trivial (< 1 hour)
Just do it. No analysis needed.
- Fix typo
- Update config value
- Add log statement

### Simple (< 1 day)
Quick team check, then execute.
- Add form field
- Update error message
- Fix obvious bug

### Standard (< 1 week)
Use the basic framework:
- What's the ask?
- What's the effort?
- What's the priority?
- Who owns it?

### Complex (> 1 week)
Full analysis needed:
- **Impact:** How many users affected?
- **Effort:** Person-days required?
- **Risk:** What could go wrong?
- **Dependencies:** What's blocking?
- **Alternatives:** Other solutions?

### Strategic (Changes everything)
Board-level decision:
- Major architecture change
- Platform migration
- Business model shift

**The rule:** Match analysis effort to decision impact.

## The Comprehensive Ask Parameters

When you need full analysis, here's what matters:

```
THE ASK: [What are we being asked to do?]

IMPACT ASSESSMENT:
- Users affected: [Number/percentage]
- Revenue impact: [Dollar amount if applicable]
- Risk if we don't: [What happens?]

EFFORT ASSESSMENT:
- Time estimate: [Days/weeks]
- People needed: [Who specifically]
- Complexity: [Simple/Medium/Complex]

CONSTRAINTS:
- Deadline: [Hard date or flexible]
- Dependencies: [What must happen first]
- Budget: [Cost in time/money]

PRIORITY CATEGORY: [1-5 from hierarchy above]

DECISION: [Do now/Do later/Don't do]
REASONING: [One sentence why]
```

## Real Examples Using Priority + Triage

```
ASK: Homepage loads in 8 seconds
PRIORITY: 4 (Performance issue)
TRIAGE: Yellow
DECISION: Fix next week

ASK: Users can't checkout
PRIORITY: 1 (Blocks customers)
TRIAGE: Red
DECISION: Drop everything now

ASK: Add dark mode
PRIORITY: 5 (Nice to have)
TRIAGE: Green
DECISION: Backlog

ASK: GDPR compliance gap
PRIORITY: 2 (Legal risk)
TRIAGE: Yellow/Red depending on deadline
DECISION: Fix this week
```

## Risk Assessment: Know What Can Go Wrong

Every ask has risk. Identify it upfront:

### Technical Risks
- **Breaking Changes:** Will this affect existing functionality?
- **Performance Impact:** Could this slow down the system?
- **Security Vulnerabilities:** Are we exposing new attack surfaces?
- **Data Loss Potential:** Could we corrupt or lose data?
- **Integration Failures:** Will third-party systems break?

### Business Risks
- **Customer Impact:** How many users affected if this fails?
- **Revenue Risk:** Could this stop sales/payments?
- **Reputation Risk:** Will failures be visible/embarrassing?
- **Compliance Risk:** Legal/regulatory consequences?
- **Competitive Risk:** Do we fall behind if we don't do this?

### Operational Risks
- **Knowledge Silos:** Only one person knows how?
- **Maintenance Burden:** Will this be hard to support?
- **Dependency Risk:** Relying on external services/vendors?
- **Reversibility:** Can we roll back if it goes wrong?
- **Technical Debt:** Making future changes harder?

### Risk Levels and Response

**Low Risk (Green Light)**
- Well-understood problem
- Team has done similar before
- Easy to test and rollback
- **Action:** Proceed with normal process

**Medium Risk (Yellow Light)**
- Some unknowns or dependencies
- Moderate complexity
- Recovery plan needed
- **Action:** Add safeguards, monitoring, staged rollout

**High Risk (Red Light)**
- Critical systems affected
- Many unknowns
- Hard to reverse
- **Action:** Prototype first, extensive testing, executive approval

### Risk Mitigation Strategies

**For Technical Risks:**
- Feature flags for easy rollback
- Staged rollouts (5% → 25% → 100%)
- Comprehensive testing before deploy
- Monitoring and alerts from day one

**For Business Risks:**
- Clear communication plans
- Customer support preparation
- Backup systems ready
- Documentation of changes

**For Operational Risks:**
- Knowledge sharing sessions
- Pair programming on critical parts
- Documentation as you build
- Avoid single points of failure

## The Cost-Benefit Reality Check

Always ask: "Is the juice worth the squeeze?"

### The Risk-Adjusted Matrix

|              | Low Risk | High Risk |
|--------------|----------|-----------|
| **High Impact** | Do Now | Plan Carefully |
| **Low Impact** | Do Later | Don't Do |

### High Impact, Low Risk (Quick Wins)
Do immediately. These fund everything else.
- Database index that speeds up queries
- Bug fix that unblocks customers
- Simple feature users are begging for

### High Impact, High Risk (Strategic Bets)
Plan carefully, prototype first, monitor closely.
- Platform migration
- Major architecture change
- New business model features

### Low Impact, Low Risk (Cleanup)
Do during slow periods or assign to juniors.
- Code formatting
- Documentation updates
- Minor UI improvements

### Low Impact, High Risk (Danger Zone)
Just say no. These kill teams.
- Experimental technology for non-critical features
- Major refactoring of working code
- Premature optimization

## Common Objections (And Responses)

**"This promotes technical debt!"**
No, it acknowledges reality. Perfect systems that never ship create infinite technical debt.

**"We should build for scale!"**
When you need scale. Most systems die before reaching scale problems.

**"This isn't engineering excellence!"**
Engineering excellence is delivering value within constraints. NASA didn't have unlimited budgets either.

**"What about best practices?"**
Best practices assume standard conditions. Your conditions aren't standard.

## The Leadership Shift

Traditional leadership asks:
- "What's the best way to do this?"
- "How do we follow industry standards?"
- "What would Google do?"

Ask-based leadership asks:
- "What are we actually trying to achieve?"
- "What constraints are we working with?"
- "What ships and solves the problem?"

## Practical Templates

### Daily Decision Template
```
THE ASK: [What are we being asked to do?]
UNMOVABLE DEADLINE: [When must this be done?]
AVAILABLE RESOURCES: [Who/what do we have?]
SIMPLEST SOLUTION: [What gets us there?]
DECISION: [What we're doing]
```

### Project Planning Template
```
BUSINESS ASK: [What does the business need?]
USER ASK: [What do users need?]

CONSTRAINTS:
- Budget: [Actual money available]
- Team: [Actual people available]
- Time: [Actual deadline]
- Technical: [Systems we must use]

PROPOSED SOLUTION: [Simplest thing that satisfies ask within constraints]

SUCCESS CRITERIA: [How we know we delivered the ask]
```

## The Meta-Truth About Ask-Based Planning

It's not about lowering standards. It's about hitting targets.

An Olympic archer doesn't debate arrow metallurgy during the competition. They identify the target, account for wind (constraints), and shoot.

Software teams spend so much time perfecting their bow, they forget to aim.

## Kanban and Ask-Based Planning: Perfect Together

### Why Kanban Works for Asks

Kanban's simplicity aligns perfectly with ask-based thinking:

**Visual Reality**
- See all asks in one place
- Watch work actually flow (or get stuck)
- No hiding behind sprint boundaries

**Natural Flow**
- Work moves when ready, not on schedule
- Small asks flow fast, big asks flow slow
- Reality enforces honesty

### The Simple Ask Board

```
| BACKLOG | READY | WORKING | REVIEW | DONE |
|---------|-------|---------|--------|------|
| Dark    | Login | Payment | Search |      |
| mode    | fix   | API     | update |      |
|         |       | 🔴 Day 5 |        |      |
| Export  | Cache |         |        |      |
| feature | bug   |         |        |      |
```

**Key Rules:**
1. **Limit WIP:** Max 2-3 asks in WORKING per developer
2. **Pull, don't push:** Take work when ready, not when assigned
3. **Flow metrics:** Track how long asks take, not points
4. **Blockage = Emergency:** Red dot means all-hands response

### When Flow Stops: Emergency Protocol

**Blocked Ask Response:**
```
ASK: Payment API integration
STATUS: 🔴 Blocked Day 5
PROBLEM: Third-party docs incorrect
RESPONSE:
1. Stop new work entering WORKING
2. Swarm the problem (multiple people investigate)
3. Time-box solution attempt (2 days max)
4. Abandon if unsolvable (cut losses)
```

### Flow Patterns Tell Truth

After a month, patterns emerge:
- "API integrations always get blocked in REVIEW"
- "Database asks flow fast through WORKING but stuck in TESTING"
- "UI asks move smoothly end-to-end"

**Use patterns to improve:**
- Add API prototype step before WORKING
- Strengthen testing resources
- Let UI asks flow freely

### Kanban Eliminates Estimation Theater

**No story points needed.**
- Small asks naturally flow in days
- Large asks naturally take weeks
- Average cycle time becomes your forecast

**Track only what matters:**
- How many asks completed this week?
- Where do asks get stuck?
- What's our average time to DONE?

### The Beautiful Simplicity

**Traditional Scrum + Jira:**
- Sprint planning (4 hours)
- Story pointing (2 hours)
- Daily standups (15 min × 5)
- Sprint review (2 hours)
- Retrospective (1 hour)
- **Total:** 10+ hours/sprint on ceremony

**Kanban + Asks:**
- Look at board (2 minutes)
- Move card when done (10 seconds)
- Address blockages immediately (as needed)
- **Total:** Actual work time

## Start Tomorrow

Pick one decision you're facing. Apply the framework:
1. What's the actual ask?
2. What constraints are real?
3. What's the simplest solution?

Then ship it.

Because at the end of the day, working software that solves real problems beats architectural diagrams every time. Your users don't care about your design patterns. They care that it works, it's fast, and it solves their problem.

Ask what they're asking for. Acknowledge your constraints. Deliver what works.

That's ask-based planning.

---

*Remember: Constraints aren't the enemy of creativity—they're its catalyst. Every masterpiece was created within constraints. Your software can be too.*