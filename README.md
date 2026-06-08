# Loan-Approval-Automation

An automated backend workflow system built to streamline the loan application lifecycle. By connecting data tracking systems with automated decision-making and messaging logic, this project eliminates manual intervention, reduces underwriting turnaround time, and ensures real-time communication for applicants and internal stakeholders.

---

## ⚙️ How It Works

The automation functions as an end-to-end event-driven pipeline:
1. **Data Ingestion:** A centralized spreadsheet tracks incoming loan applications and current processing statuses.
2. **Orchestration Engine:** An automation workflow monitors changes in the data layer, executes business logic (such as basic eligibility, financial risk assessment, or credit evaluation parameters), and branches into specific execution tracks.
3. **Notification Layer:** Based on the automated logic outcome, the system instantly triggers formatted alert templates to notify relevant teams or applicants.

---

## 🛠️ Tech Stack & Integration

* **Data & CRM Layer:** Google Sheets (acts as the primary source of truth for credit parameters and application logs).
* **Workflow Orchestration:** n8n (handles webhook listeners, conditional routing, and multi-app integration).
* **Communication Channel:** Integrated communication tools (e.g., Slack, Microsoft Teams, or Email APIs) to dispatch instantaneous status updates.

---

## 📁 Repository Structure & Visual Assets

As shown in the repository snapshot (`image_c1d3c2.png`), the system architecture, data models, and output interfaces are documented through the following project assets:

| File Name | Description |
| :--- | :--- |
| `assetsgoogle- Sheets.pnj.png` | **Data Layer:** Schema structure and tracking layout used to manage applicant financials and loan statuses. |
| `assetn8n-workflow.ow.pnj.png` | **Logic Layer:** End-to-end backend automation visual blueprint built within n8n. |
| `assetapproval-alert.pnj.png` | **Output UI:** Real-time alert template triggered upon a successful **Approved** loan decision. |
| `asstspending - alert.pnj.png` | **Output UI:** Real-time alert template triggered when an application requires **Manual Underwriting / Pending Review**. |
| `assetrejection- alert.pnj.png` | **Output UI:** Real-time alert template triggered upon a **Rejected** loan decision based on unmet credit criteria. |

---

## 📊 Process Flow & Logic Gateways

```mermaid
graph TD
    A[New Application / Status Change in Google Sheets] --> B(n8n Webhook / Poll Trigger)
    B --> C{Credit Evaluation Engine}
    
    C -->|Meets Financial Criteria| D[Dispatch Approved Alert]
    C -->|Requires Manual Underwriting| E[Dispatch Pending Review Alert]
    C -->|Fails Risk Thresholds| F[Dispatch Rejection Alert]

    style D fill:#d4edda,stroke:#28a745,stroke-width:2px
    style E fill:#fff3cd,stroke:#ffc107,stroke-width:2px
    style F fill:#f8d7da,stroke:#dc3545,stroke-width:2px
