# Cognitive Urban Twin — Decision Reasoning Test Pack v0.3

This pack extends the verified v0.2.1 baseline with an explicit decision-context and evidence layer.

| Test | Check | Asserted? | Entailed? | Result |
|---|---|---:|---:|---|
| DR1 | Cognitive Twin has a decision context | Yes | Yes | PASS |
| DR2 | Decision context is linked to the heatwave impact forecast | Yes | Yes | PASS |
| DR3 | Decision context identifies the affected data centre | Yes | Yes | PASS |
| DR4 | Decision context identifies the traffic-management service | Yes | Yes | PASS |
| DR5 | Decision context identifies the grid constraint | Yes | Yes | PASS |
| DR6 | Decision context identifies compute flexibility | Yes | Yes | PASS |
| DR7 | Decision context has high decision risk | Yes | Yes | PASS |
| DR8 | Decision context is actionable | Yes | Yes | PASS |
| DR9 | Workload action is inferred as AnticipatoryAction via CandidateAction | No | Yes | PASS |
| DR10 | Explanation is linked to a machine-readable evidence object | Yes | Yes | PASS |
| DR11 | Selected action entails generic decision relationship | No | Yes | PASS |
| DR12 | Decision context inverse navigation is inferable | No | Yes | PASS |

## Decision reasoning structure

```text
Weather hazard
    ↓
Impact forecast
    ↓
DecisionContext
 ├─ affected infrastructure
 ├─ affected services
 ├─ grid constraint
 ├─ available flexibility
 ├─ decision evidence
 ├─ decision risk
 └─ candidate actions
    ↓
DecisionRecommendation
    ↓
selected action(s)
    ↓
ExplanationAssurance + machine-readable evidence
```

## Interpretation

The ontology can now represent not only a recommendation, but also the decision context and evidence used to justify that recommendation.

This remains an ontology-level reasoning layer rather than a numerical optimisation engine. A later version can add explicit rule execution or optimisation criteria.