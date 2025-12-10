# The Vector Delivery System (VDS)

![Version](https://img.shields.io/badge/Version-3.0-blue?style=for-the-badge&labelColor=black) ![Date](https://img.shields.io/badge/Date-October_2025-lightgrey?style=for-the-badge&labelColor=black) ![Status](https://img.shields.io/badge/Status-Operational_Standard-success?style=for-the-badge&labelColor=black) ![Clearance](https://img.shields.io/badge/Clearance-Internal_Use-red?style=for-the-badge&labelColor=black)

![Architect](https://img.shields.io/badge/Architect-Xopher-purple?style=flat-square) ![Department](https://img.shields.io/badge/Dept-Hall_of_the_Gods-000000?style=flat-square)

---

## 1.0 Executive Summary
![Metric](https://img.shields.io/badge/Focus-Velocity_>_Speed-critical) ![Philosophy](https://img.shields.io/badge/Philosophy-No_Chaos-success)

Most small engineering teams are trapped in one of two extremes: the **Suffocating Bureaucracy** of enterprise Agile, or the **Fragile Chaos** of "cowboy coding." Both extremes kill the only metric that actually matters: **Velocity**.

* **🏎️ Speed** is how fast you type code.
* **🚀 Velocity** is how fast you ship stable value to users.

**The Vector Delivery System (VDS)** is the antidote to the "Hidden Tax" of modern development—the endless cycle of merge conflicts, broken demos, and "it works on my machine" bugs.

VDS is a hybrid operational architecture specifically designed for high-performing teams who need to move fast without breaking things. It harmonizes the discipline of Scrum, the clarity of MoSCoW prioritization, and the agility of Trunk-Based Development into a single, streamlined engine.

**The Goal:** Stop managing chaos and start shipping value.

---

## 2.0 Structural Dynamics (Roles)
![Structure](https://img.shields.io/badge/Structure-3_Roles-orange) ![Optimization](https://img.shields.io/badge/Optimization-Low_Handoff-blue)

VDS collapses the bloated roster of traditional Agile into three hyper-focused roles. This structure minimizes hand-offs and maximizes ownership.

### 2.1 The Product Owner (PO)
* **Primary Directive**: Value Definition.
* **Responsibility**: Owns the **Scope** ("What are we building?") and the **Sequence** ("In what order?"). The PO protects the team from external noise.

### 2.2 The System Architect
* **Primary Directive**: Feasibility & Flow.
* **Responsibility**: Owns the **Pipeline** ("How do we ship?") and the Technical Strategy. The Architect ensures the "Main" branch remains buildable and scalable.

### 2.3 The Builder
* **Primary Directive**: Execution.
* **Responsibility**: The primary generator of code.
    * *(Note: In VDS, the Architect frequently steps into the Builder role during execution phases).*

---

## 3.0 Technical Architecture: The "Stream" Model
![Strategy](https://img.shields.io/badge/Strategy-Trunk--Based-blueviolet) ![Source](https://img.shields.io/badge/Source_of_Truth-Main-success)

VDS rejects the traditional "GitFlow" model of maintaining permanent dev, test, and release branches. Instead, VDS utilizes **Trunk-Based Development** with Short-Lived Feature Branches.



### 3.1 The Two States of Code

1.  **The Stream (`main`)**:
    * The single source of truth.
    * Always buildable. Always deployable to Staging.
    * **Rule**: No direct pushes. Changes arrive only via Squashed Pull Requests.

2.  **The Anchors (`tags:vYYYY.M.P`)**:
    * Immutable snapshots of the Stream.
    * Production environments run exclusively on Anchors.
    * Versioning is automated based on the Sprint Calendar (See Section 7.0).

### 3.2 The Branching Protocol

All development occurs in ephemeral environments to ensure isolation without stagnation.

1.  **Branch**: Developer creates `feature/xyz` from `main`.
2.  **Commit**: Frequent local commits.
3.  **PR**: Open Pull Request against `main` for review.
4.  **Squash & Merge**: Upon approval, the branch is flattened into a single commit and merged to `main`.
5.  **Destruction**: The feature branch is deleted immediately.

---

## 4.0 The Control Plane (Workflow)
![Flow](https://img.shields.io/badge/Flow-Linear-yellow) ![Tracking](https://img.shields.io/badge/Tracking-Phase_Based-blue)

VDS utilizes a linear status flow to map the physical location of code to its lifecycle phase.

### Phase I: Planning (The "Why")
*Before code exists.*

* 🔥 **In Refinement (PO)**: Raw idea dump. PO defines the "User Story."
* 🦾 **In Refinement (Tech)**: Architect validates feasibility.
* 🃏 **Awaiting Estimation**: Requirements are clear; awaiting Story Points.
* 🚦 **Ready to Start**: **LOCKED**. Estimated, Prioritized, and assigned to a Sprint.

### Phase II: Execution (The "Build")
*Code is active.*

* 🚧 **In Progress**: Code exists on a local machine or a `feature/` branch.
* 🧐 **In Peer Review**: PR is open. Automated CI checks are passing. Human review is pending.

### Phase III: Delivery (The "Merge")
*Code enters the Stream.*

* 🏗️ **Awaiting Tag**: Merged to `main`. Waiting for the Automated Code Freeze.
* 🔖 **Tagged (Candidate)**: A Version Tag has been cut (e.g., `v2025.1.1`). Deployed to Staging/QA for validation.
* 🚢 **Released (Promoted)**: The Tag is promoted to a formal GitHub Release. Production deployment is triggered.

---

## 5.0 Governance: The Single-Slot Priority Matrix
![Governance](https://img.shields.io/badge/Governance-Single_Slot-red) ![Logic](https://img.shields.io/badge/Logic-Strict_FIFO-red)

VDS manages complexity by treating the Team (not the Project) as the constraint. We utilize a **Strict Slotting System** to force absolute prioritization across competing initiatives.

### 5.1 Axis A: MoSCoW (The Buckets)
*Determines the Sprint Commitment.*

* 🧬 **Must Have**: The Contract. The Sprint fails if any of these are missing.
* ✨ **Should Have**: High value, but acts as a buffer.
* 🎀 **Could Have**: Fillers/Bonus.
* 🦄 **Won't Have**: Explicitly out of scope.

### 5.2 Axis B: Operational Priority (The Sequence)
*Determines the Execution Order within a Bucket.*

* 🚑 **Critical**: Immediate next task.
* 🚒 **Expedite**: High urgency.
* 🚓 **High**: Standard Priority.
* 🚕 **Medium**: Standard Priority.
* 🛵 **Low**: Filler.

### 5.3 The Single-Slot Rule (Strict FIFO)
To prevent "Priority Inflation," VDS enforces a hard cap: **Each intersection of Scope (MoSCoW) and Priority (Sequence) acts as a single container slot.**

* There is only one "Must Have / Critical" slot.
* There is only one "Must Have / High" slot.

If a slot is occupied, a new task cannot enter it without displacing the incumbent. This creates a cascade effect that forces the Product Owner to verify the relative value of *every single task* against the others.

### 5.4 The Displacement Protocol
When a new task enters a populated sprint, it triggers a **Rank Check**.

* **Challenge**: A new task fights for the `Must Have / Critical` slot.
* **Defense**: Is it more important than the current occupant?
* **Result**: The loser is demoted to the next slot down (Expedite), displacing that occupant, and cascading down the chain.

---

## 6.0 Quality Assurance: The PR Protocol
![Protocol](https://img.shields.io/badge/Protocol-Environment_Check-important) ![Assurance](https://img.shields.io/badge/Assurance-Traceability-blue)

In VDS, the Pull Request (PR) is not for syntax checking—it is for **Environment Compatibility**.

### 6.1 The Automation Layer
Compilers, Linters, and Static Analysis tools (AI) handle code style and syntax. If the build fails, the PR is blocked automatically.

### 6.2 The Human Layer
The reviewer is responsible for the "**Works on My Machine**" Certification.

1.  **Checkout**: Pull the branch locally.
2.  **Smoke Test**: Validate the feature functions as described.
3.  **Infra-Check**: If `package.json` or `Dockerfile` was touched, a full rebuild is mandatory.

### 6.3 Traceability (The Stream Guard)
To prevent "Ghost Work," VDS enforces a strict link between Code and Planner.

* **The Check**: Automated `verify-traceability` action runs on every PR.
* **The Rule**: PRs must contain a valid Asana Link (`app.asana.com`).
* **The Result**: If missing, the build fails and merge is blocked. Code must earn its slot.

---

## 7.0 Temporal Rhythms & Automated Release
![Cycle](https://img.shields.io/badge/Cycle-3_Weeks-0055ff) ![Automation](https://img.shields.io/badge/Automation-Github_Actions-2ea44f)

VDS minimizes synchronous meetings and manual release steps. We operate on a **3-Week Cycle** governed by a "Code Freeze Action" that automates versioning based on the calendar.

### 7.1 The Release Train (Automation)
The release schedule is immutable and handled by the Code Freeze Action. The train leaves on time, regardless of payload.

| Event | Timing | Version Action | Description |
| :--- | :--- | :--- | :--- |
| **Sprint Start** | **Monday 08:00 EST** | **Minor Bump** (`v2025.1.0`) | Starts the 3-week cycle. Resets the Patch count. |
| **Mid-Week Freeze** | **Tue & Thu 11:57 PM PST** | **Patch Bump** (`v2025.1.1`) | "The Train." If changes exist on `main`, the next sequential tag is cut. |
| **Year Rollover** | **First Sprint of Jan** | **Major Bump** (`v2025.0.0`) | Automated year rollover logic. |

> **Operational Note (The Immutable Flow)**:
> * **Tags are Forever**: Once a tag is cut, it exists. We never delete tags or reuse version numbers.
> * **The Filter**: Every tag creates a **Draft Release**. If `v2025.1.1` is found to be buggy during staging validation, we simply do not promote it to Production.
> * **The Next Train**: The next scheduled freeze will create `v2025.1.2` regardless of the fate of the previous tag. The patch number always moves forward.

### 7.2 The Cycle Reset (Ritual)
*Duration: 120 Minutes.*

Combines Review, Retro, and Planning into one high-energy session at the end of Week 3.

* **Demo**: Show the functionality shipped in the last Minor Version.
* **Retro**: Process check (Velocity vs. Friction).
* **The Lock**: Populate the Single-Slot Matrix for the next 3 weeks.

### 7.3 Vector Labs (Innovation)
*Duration: 1 Full Day (Final Friday).*

An "Innovation Valve" is reserved for the final day of the sprint.

* **Condition**: Unlocked only if Sprint "Must Haves" are 100% complete.
* **Activity**: R&D, AI prototyping, refactoring experiments.

### 7.4 The Stand-up (Daily)
*Duration: 15 Minutes Max.*

* **Focus**: Blockers only.
* **Banned Phrase**: "Yesterday I worked on..." (The board already shows this).

---

## 8.0 Conclusion

![Agreement](https://img.shields.io/badge/Agreement-Binding-lightgrey?style=for-the-badge) ![Value](https://img.shields.io/badge/Value-Accountability-blue?style=for-the-badge) ![Value](https://img.shields.io/badge/Value-Transparency-success?style=for-the-badge) ![Value](https://img.shields.io/badge/Value-Collaboration-orange?style=for-the-badge) ![Value](https://img.shields.io/badge/Value-Productivity-yellow?style=for-the-badge)

The Vector Delivery System is not just a set of rules; it is a **contract**. The Business agrees to respect the **Slots** (The Capacity), and Engineering agrees to respect the **Stream** (The Stability of `main`). By adhering to this pact, we achieve high velocity without the chaos.

> **The VDS Promise:**
> If you follow the protocol, your team will be:
>
> ![Harder](https://img.shields.io/badge/-Better-critical?style=flat-square) ![Better](https://img.shields.io/badge/-Faster-critical?style=flat-square) ![Faster](https://img.shields.io/badge/-Stronger-critical?style=flat-square)
>
> *Money Back Guaranteed.*

---
*Property of Hall of the Gods Engineering Dept. Do not modify without a Pull Request.*
