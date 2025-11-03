
# Business Process Documentation with Mermaid Diagrams

## Process Diagram 3 — Insurance Claim Processing
**Goal:** Approve or Reject insurance claim & settle payment  
**Domain:** Banking / Insurance

### Participants
- Customer
- Claim Processor
- Surveyor / Investigator
- Approval Manager
- System (Policy Validation + Fraud Check)

### Mermaid Workflow
```mermaid
flowchart TD
    A([Start - Customer Submits Claim]) --> B[Validate Policy & Claim Details]
    B --> C{Policy Active?}
    C -- No --> Z1([Reject Claim - Policy Inactive]) --> O([End])
    C -- Yes --> D[Assign Surveyor for Inspection]
    D --> E[Surveyor Assessment Report]
    E --> F{Fraud Suspected?}
    F -- Yes --> G[Escalate to Investigation Team] --> H{Fraud Confirmed?}
    H -- Yes --> Z2([Reject Claim - Fraud]) --> O([End])
    H -- No --> I[Approval Manager Review]
    F -- No --> I[Approval Manager Review]
    I --> J{Approved?}
    J -- No --> Z3([Reject Claim]) --> O([End])
    J -- Yes --> K[Calculate Settlement Amount]
    K --> L[Process Payment to Customer]
    L --> O([End])
```

---

## Process Diagram 4 — Employee Onboarding Process
**Goal:** Provide smooth joining experience & activate employee for work  
**Domain:** HR / Corporate

### Participants
- New Employee
- HR Team
- IT Team
- Admin (Facilities)
- Manager

### Mermaid Workflow
```mermaid
flowchart TD
    A([Start - Offer Accepted by Candidate]) --> B[HR collects documents]
    B --> C{Documents Complete?}
    C -- No --> Z1([Onboarding On-Hold]) --> O([End])
    C -- Yes --> D[Create Employee ID]
    D --> E[IT Laptop & Email Setup]
    E --> F[Facilities - Desk/Access Card Setup]
    F --> G[Manager Assigns Training & Mentor]
    G --> H(Welcome Orientation & HR Induction)
    H --> I{Any Pending Setup?}
    I -- Yes --> R1[Follow-up Tasks] --> H
    I -- No --> J([Onboarding Complete])
    J --> O([End])
```
