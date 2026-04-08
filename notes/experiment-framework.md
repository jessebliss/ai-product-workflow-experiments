# Experiment Framework for AI Workflow Features

A lightweight framework for testing whether AI assistance creates real product value while controlling operational risk.

## 1) Hypothesis

State one clear, testable hypothesis.

- Example: "AI-generated draft summaries will reduce average case handling time by 20% without increasing correction rate above 10%."

## 2) Primary Success Metric

Choose one metric that represents value.

- Examples: time-to-complete, acceptance rate, throughput, first-response time.

## 3) Guardrail Metrics

Define risk constraints that must not regress.

- Examples: error rate, human override rate, customer escalation rate, compliance incidents.

## 4) Cohorts and Rollout

- Define treatment and control groups.
- Start with low-risk users/use cases.
- Use staged rollout (e.g., 5% → 25% → 50% → 100%) with pause criteria.

## 5) Measurement Window

- Define start/end dates and minimum sample size.
- Account for weekly seasonality where relevant.

## 6) Decision Rules

- **Ship**: Primary metric improves and guardrails stay within bounds.
- **Iterate**: Some improvement but guardrails drift slightly.
- **Rollback**: Guardrails breach or no measurable benefit.

## 7) Learning Capture

After each experiment, capture:

- What changed
- What happened
- Why it likely happened
- What to test next
