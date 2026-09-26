# What is a decision model?

A chat LLM writes an answer token by token, and your code then parses that text back into an `if`. A decision model skips the writing. You send it a **state** (any text: a ticket, a diff, a web page) and a set of **typed questions**, and it reads every answer directly off the model in a single, non-autoregressive pass. Each answer is one of the options you defined, with a probability attached.

Three question types have become the de facto standard: `noul` (yes/no probability), `choice` (pick one of N labels) and `score` (a point on an ordered rubric).

```jsonc
// request
{
  "state": "Billed twice for March. Refund the duplicate today or we cancel.",
  "questions": {
    "department": { "type": "choice", "criteria": { "billing": "...", "technical": "...", "other": "..." } },
    "churn_risk": { "type": "noul", "instructions": "Does the user threaten to leave?" }
  }
}

// response (tens of milliseconds, zero output tokens)
{
  "answers": {
    "department": { "choice": "billing", "probabilities": { "billing": 0.94, "technical": 0.03, "other": 0.03 } },
    "churn_risk": { "noul": 0.97 }
  }
}
```

Because the answer can never fall outside the options, decision models are used as the fast "System 1" beside a slower LLM: routing, triage, guardrails, picking the next browser action, deciding what to keep in an agent's context.
