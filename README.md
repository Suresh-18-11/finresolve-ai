# FinResolve AI

### Financial Transaction Dispute Investigation Copilot

**Project status:** Requirements and environment setup. Implementation has not started.

## Overview

FinResolve AI is a portfolio project that assists financial dispute analysts in investigating customer transaction complaints.

Set at the fictional card issuer **CedarBridge Financial**, the copilot will gather synthetic records, investigate disputes, apply fictional policy rules, and prepare evidence-supported recommendations for authorized human review.

All customers, accounts, transactions, policies, and financial actions are fictional or simulated.

## Business Problem

Dispute analysts must reconcile customer statements with transaction records, refund information, and previous cases before recommending an outcome.

When information is scattered or incomplete, investigations involve repetitive work and can produce inconsistent or poorly supported recommendations.

FinResolve AI aims to reduce this investigation effort while preserving human control and making recommendations easier to review.

## Primary User

The primary user is an internal financial dispute analyst.

The analyst uses the copilot to gather evidence and prepare a case. An authorized human reviewer controls final outcomes and customer communication.

## Planned Version 1 Capabilities

- Accept a customer’s transaction-dispute message.
- Extract structured complaint information.
- Retrieve synthetic customer, transaction, refund, and dispute records.
- Select investigation tools based on the available evidence.
- Classify the dispute and identify missing or contradictory information.
- Apply deterministic fictional policy rules.
- Prepare a case summary and recommended next action.
- Pause for human approval, rejection, editing, or escalation.
- Simulate an approved case action.
- Draft customer communication for human review.
- Preserve workflow progress using checkpointing and thread IDs.
- Record evidence, rule results, recommendations, and human decisions.

## Planned Dispute Scenarios

- Unrecognized or potentially unauthorized transactions
- Possible duplicate charges
- Incorrect amounts
- Refunds not received
- Recurring subscription charges
- Products or services not received
- Missing information or ambiguous transaction matches

Support will be implemented incrementally.

## Design Approach

Version 1 will use a controlled hybrid workflow:

- **Deterministic stages** enforce identity matching, mandatory conditions, allowed actions, and stopping limits.
- **LLM-assisted tasks** interpret complaints, classify disputes, and summarize evidence.
- **Agentic investigation** selects tools, observes results, and adjusts the investigation when necessary.
- **Human review** controls sensitive outcomes and customer communication.

The investigation will have explicit stopping conditions and a maximum step limit.

## Safety and Authority

> The agent controls investigation. Deterministic rules enforce mandatory conditions. An authorized human controls financial decisions.

The copilot must distinguish customer claims from verified evidence and clearly identify uncertainty.

It will not execute real payments, issue real refunds, access real accounts, or send real customer messages.

## Version 1 Technology

- Python
- Pydantic structured output
- LLM API integration
- Tool/function calling
- LangGraph
- Conditional routing
- Checkpointing and thread IDs
- Human-in-the-Loop
- Synthetic Python records and mock tools
- Terminal interaction

Memory will be added only where it serves a defined purpose. A database is not required for Version 1.

## Synthetic Data

Test scenarios will include:

- Clean and incomplete records
- Incorrect transaction IDs
- Merchant-name confusion
- Pending versus completed transactions
- Possible duplicate charges
- Existing refunds
- Conflicting customer statements
- Prior dispute history
- Multiple possible transaction matches
- Insufficient evidence

Retrieval tools will have stable inputs and outputs so that the underlying storage can be replaced later.

## Version 1 Exclusions

- Real customer or financial data
- Real bank integrations or payment execution
- Real email sending
- RAG, embeddings, or vector databases
- PostgreSQL
- MCP
- Multi-agent architecture
- Complex frontend development
- Cloud deployment
- Claims of regulatory compliance

## Success Measures

The project will be evaluated on synthetic cases for:

- Correct customer and transaction matching
- Appropriate investigation-tool selection
- Accurate distinction between claims and evidence
- Identification of missing or contradictory information
- Correct enforcement of fictional policy rules
- Evidence-supported recommendations
- Human review before sensitive outcomes
- Reliable pause and resume behavior
- Investigation effort compared with a manual baseline

Targets and results will be documented as evaluation is implemented. No performance improvements are claimed yet.

## Planned Evolution

1. **RAG:** Retrieve relevant fictional policy passages with citations.
2. **PostgreSQL:** Replace mock storage with structured case and transaction data.
3. **Reliability and evaluation:** Expand recovery, testing, logging, and measurements.
4. **MCP:** Expose investigation tools through standard interfaces.
5. **Production engineering:** Explore authentication, persistent storage, observability, deployment, and security controls.
6. **Validation strategy:** Document a path from synthetic testing to sandbox and domain-expert review.

These are future learning milestones, not completed features.

## Development Process

Development will proceed through requirements, acceptance criteria, data contracts, incremental implementation, code review, and testing.

Documentation will explain the business purpose, design decisions, limitations, and validation of each implemented feature.

## Project Disclaimer

FinResolve AI is an educational portfolio project. It does not represent an internal system at Bank of America, American Express, or any other financial institution. It is not production banking software.
