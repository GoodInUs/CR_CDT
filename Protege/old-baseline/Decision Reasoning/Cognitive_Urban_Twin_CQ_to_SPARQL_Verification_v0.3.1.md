# Cognitive Urban Twin — CQ-to-SPARQL Verification Specification v0.3.1

Baseline ontology: `cognitive-urban-twin-v0.3.1-webprotege-clean.ttl`

This specification maps each competency question to the ontology classes and properties it exercises, the expected result, the executable SPARQL query, and the observed result against the verified heatwave exemplar.

| CQ | Competency question | Expected | Observed | Result |
|---|---|---|---:|---|
| CQ01 | What hazard is currently threatening critical urban infrastructure? | ≥1 hazard | 1 row(s) | PASS |
| CQ02 | Which infrastructure assets are threatened by the hazard? | DataCentre_East_01 | 1 row(s) | PASS |
| CQ03 | What evidence supports identification of the hazard? | Evidence_HeatForecast_01 | 1 row(s) | PASS |
| CQ04 | What infrastructure telemetry is available for the affected asset? | Evidence_DataCentreTelemetry_01 | 1 row(s) | PASS |
| CQ05 | What grid constraint is associated with the affected infrastructure? | GridConstraint_East_01 | 1 row(s) | PASS |
| CQ06 | Which electricity grid supplies the affected infrastructure? | ElectricityGrid_East | 1 row(s) | PASS |
| CQ07 | Which urban services depend upon the affected infrastructure? | 2 services | 2 row(s) | PASS |
| CQ08 | What impact is forecast for the hazard? | ImpactForecast_Heatwave_01 | 1 row(s) | PASS |
| CQ09 | Which services are expected to be affected? | 2 services | 2 row(s) | PASS |
| CQ10 | What evidence supports the impact assessment? | 4 evidence items | 4 row(s) | PASS |
| CQ11 | What is the current decision context? | DecisionContext_Heatwave_01 | 1 row(s) | PASS |
| CQ12 | What infrastructure and services are included in that context? | 1 infrastructure + 2 services | 2 row(s) | PASS |
| CQ13 | What evidence is available to support the decision? | 4 evidence items | 4 row(s) | PASS |
| CQ14 | What is the assessed decision risk? | HighDecisionRisk | 1 row(s) | PASS |
| CQ15 | What operational flexibility is available? | 2 resources | 2 row(s) | PASS |
| CQ16 | What candidate actions are available? | 2 actions | 2 row(s) | PASS |
| CQ17 | What recommendation has the cognitive twin generated? | Recommendation_Heatwave_01 | 1 row(s) | PASS |
| CQ18 | Which actions have been selected? | 2 actions | 2 row(s) | PASS |
| CQ19 | What evidence and explanation justify the recommendation? | 1 explanation + 4 evidence items | 4 row(s) | PASS |
| CQ20 | How confident is the system in the recommendation? | 0.86 | 1 row(s) | PASS |
| CQ21 | How quickly can each intervention be implemented? | 10 min and 30 min | 2 row(s) | PASS |
| CQ22 | What outcome observations are returned after an intervention? | ObservationBase_City_01 | 2 row(s) | PASS |
| CQ23 | Where are intervention outcomes subsequently supplied? | PredictionScenarioEngine_01 | 2 row(s) | PASS |
| CQ24 | What new impact forecast is produced from the updated state? | ImpactForecast_Heatwave_01 | 1 row(s) | PASS |
| CQ25 | How is the updated scenario returned to the cognitive twin? | CognitiveTwin_City_01 | 1 row(s) | PASS |
| CQ26 | Can the full decision trace be reconstructed end-to-end? | ≥1 complete trace | 4 row(s) | PASS |

## Validation interpretation

- A PASS means the exemplar ontology returned at least one result for the competency question.
- This is a functional query-level verification, not yet a complete logical-soundness proof.
- CQ26 acts as the integration test for the full closed-loop decision trace.

## Canonical end-to-end chain

```text
Hazard
  ↓
Affected infrastructure / services / grid constraint
  ↓
Decision evidence
  ↓
Impact forecast
  ↓
DecisionContext
  ↓
Candidate actions
  ↓
CognitiveTwin recommendation
  ↓
Selected actions
  ↓
Explanation / assurance / evidence
  ↓
Outcome observation
  ↓
PredictionScenarioEngine
  ↓
Updated CognitiveTwin state
  ↺
```