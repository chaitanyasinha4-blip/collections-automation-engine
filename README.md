# Collections Automation Engine

A project-driven workflow that identifies overdue invoices, assigns collection priorities, and routes follow-up actions using Make.com and Google Sheets.

## 1. Business Problem

Collections teams often review invoice data manually to identify overdue accounts and decide which customers need immediate attention.

This workflow demonstrates how business rules can automate that initial review and standardise follow-up actions.

## 2. Solution

The workflow:

1. Checks Google Sheets for newly added invoice rows.
2. Evaluates invoice amount and days overdue.
3. Assigns a priority and escalation path.
4. Writes the result back to the spreadsheet.

The scenario checks for new rows every 15 minutes.

```flowchart TD A["Google Sheets: Watch New Rows"] --> B{"Invoice > 500000 AND Days Overdue > 30?"} B -->|Yes| C["High Priority: Finance Manager"] B -->|No| D["Normal Priority: Account Owner"] C --> E["Update Google Sheets"] D --> E
```

## 3. Business Rules

| Condition | Priority | Escalation | Action |
|---|---|---|---|
| Invoice amount > ₹5,00,000 AND days overdue > 30 | High | Finance Manager | Immediate Follow-up |
| All other cases | Normal | Account Owner | Standard Follow-up |

## 4. Tools Used

- Make.com: Workflow automation and conditional logic
- Google Sheets: Input data and output tracking

## 5. Validation

The workflow was tested with dummy invoice data.

Test scenarios included:

- A high-value invoice more than 30 days overdue
- A lower-value invoice more than 30 days overdue
- A high-value invoice within 30 days overdue
- A lower-value invoice within 30 days overdue
- A newly added invoice processed by the scheduled trigger

The workflow successfully routed the test cases and populated the corresponding output fields.

## 6. Business Value

This prototype demonstrates how collections teams can:

- Standardise invoice prioritisation
- Reduce repetitive manual review
- Route follow-ups consistently
- Improve visibility into collection actions

No production collection or financial system is connected. All demonstration data is fictional.

## 7. Future Improvements

- Add an AI-generated explanation for each priority decision
- Introduce missing-data and duplicate-record checks
- Add exception handling and human approval
- Track operational metrics such as processing time and overdue balances
- Integrate with a CRM or finance system
