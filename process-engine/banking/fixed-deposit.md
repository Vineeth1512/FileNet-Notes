# 🏦 Fixed Deposit (FD) Opening Process

## 🎯 Process Goal
Successfully open a Fixed Deposit account and generate FD receipt for customer.

## 🏢 Domain
Banking / Financial Services

## 👥 Participants (Roles & Swimlanes)
| Role | Responsibility |
|------|----------------|
| Customer | Requesting FD |
| Relationship Manager (RM) / Bank Teller | Collects details & initiates FD |
| Backend Operations | Verification & account linking |
| Core Banking System | Auto interest & maturity computation |
| Compliance / Risk Team | Checks AML, KYC |

---

## ✅ Detailed Process Flow
1. Customer requests FD with deposit amount & tenure
2. KYC & existing account validation
3. Check source of funds
4. Interest rate selection based on tenure / senior citizen
5. Block funds from linked account
6. FD account creation
7. FD certificate/receipt generation
8. Notify customer via SMS/Email

---

## 🔀 Decisions
- KYC valid or not
- Sufficient balance or not
- High-value deposit → Compliance review

---

## 📦 Process Outcomes
✅ FD created successfully  
❌ FD request rejected (reason documented)

---

## 📊 Mermaid Workflow Diagram

```mermaid
flowchart TD
    A([Start - Customer Requests FD]) --> B[Collect Customer Details & Amount]
    B --> C{KYC Valid?}
    C -- No --> Z1([Reject - Update KYC]) --> O([End])
    C -- Yes --> D[Check Linked SB Account Balance]
    D --> E{Sufficient Balance?}
    E -- No --> Z2([Reject - Insufficient Funds]) --> O([End])
    E -- Yes --> F[Check High-Value Deposit]
    F --> G{Above Threshold?}
    G -- Yes --> H[Compliance/AML Review]
    H --> I{Approved?}
    I -- No --> Z3([Reject - Compliance]) --> O([End])
    I -- Yes --> J[Configure Tenure & Interest Rate]
    G -- No --> J
    J --> K[Debit Linked Account]
    K --> L[Create FD Account in Core Banking]
    L --> M[Generate FD Receipt/SMS/Email]
    M --> O([End])
```


 Fixed Deposit (FD) Process Flow – Explained
- Start – Customer Requests FD
The process begins when a customer initiates a request to open a Fixed Deposit.
- Collect Customer Details & Amount
Capture essential information such as customer ID, deposit amount, and desired tenure.
- KYC Valid?
Check if the customer's Know Your Customer (KYC) details are up to date.
- No → Reject the request and prompt the customer to update KYC → End
- Yes → Proceed to the next step
- Check Linked Savings Account Balance
Verify if the linked savings account has enough funds to cover the FD amount.
- Sufficient Balance?
- No → Reject the request due to insufficient funds → End
- Yes → Continue
- Check High-Value Deposit
Determine if the deposit amount exceeds a predefined threshold (e.g., ₹10 lakh or regulatory limit).
- Above Threshold?
- Yes → Trigger a Compliance/AML (Anti-Money Laundering) Review
- Approved?
- No → Reject the request due to compliance concerns → End
- Yes → Proceed
- No → Skip compliance review and continue
- Configure Tenure & Interest Rate
Based on the deposit duration and customer type (e.g., senior citizen), assign the applicable interest rate.
- Debit Linked Account
Deduct the FD amount from the customer’s savings account.
- Create FD Account in Core Banking
Set up the FD account in the core banking system with all relevant details.
- Generate FD Receipt / SMS / Email
Create the FD certificate and send confirmation to the customer via SMS and/or email.
- End
The FD creation process is complete.

---

## 🌍 Real-Time Scenario (FileNet Perspective)
| Step | FileNet Workflow Object |
|------|------------------------|
| Customer request routed to Branch Teller | Work item in Queue |
| KYC status task | Step requiring approval |
| Compliance review (if needed) | Subprocess / Workflow fork |
| Final approval | System auto-complete step |
| Document storage | CE stores FD contract + acknowledgement |

---

## ⚙️ SLA/Timers
- Compliance team → must approve within 4 hours
- Funds blocking → immediate system task

---

## 🔔 Event Notifications
- Assignment notifications
- Auto-escalation if SLA breached

---

## 📝 Summary Table
| Feature | Banking Use |
|---------|-------------|
| Automatic interest payout | Monthly/Quarterly |
| Tax considerations | TDS on interest |
| Maturity workflow | Auto-renewal or payout process |

---

## ✅ Output Artifacts
📌 FD Acknowledgement Receipt  
📌 FD Terms & Conditions  
📌 Maturity Calendar Entry in CBS
