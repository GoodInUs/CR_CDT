# Cognitive Urban Twin — v0.3.2 Validation Clean

- Ontology syntax: **PASS** (877 triples)
- SHACL shapes syntax: **PASS** (64 triples)
- SHACL property checks: **11 executed**
- SHACL violations: **0**
- SHACL result: **PASS**
- Reasoning checks: **12/12 PASS**
- Competency questions: **26/26 PASS**

## Fixes applied

1. `decisionUrgency` is now explicitly typed `xsd:string`.
2. `recommendationId` is now explicitly typed `xsd:string`.
3. SHACL `sh:class` validation is evaluated with subclass awareness, so `CandidateAction` instances correctly satisfy `AnticipatoryAction` constraints.

## SHACL constraint results

| Focus node | Property | Values | Result |
|---|---|---:|---|
| `DecisionContext_Heatwave_01` | `hasDecisionStatus` | 1 | PASS |
| `DecisionContext_Heatwave_01` | `hasDecisionRisk` | 1 | PASS |
| `DecisionContext_Heatwave_01` | `decisionWindow` | 1 | PASS |
| `DecisionContext_Heatwave_01` | `decisionUrgency` | 1 | PASS |
| `DecisionContext_Heatwave_01` | `hasAffectedInfrastructure` | 1 | PASS |
| `DecisionContext_Heatwave_01` | `hasRiskAssessment` | 1 | PASS |
| `DecisionContext_Heatwave_01` | `hasCandidateAction` | 2 | PASS |
| `DecisionContext_Heatwave_01` | `hasDecisionEvidence` | 4 | PASS |
| `Recommendation_Heatwave_01` | `justifiedBy` | 1 | PASS |
| `Recommendation_Heatwave_01` | `recommendsAction` | 2 | PASS |
| `Recommendation_Heatwave_01` | `recommendationId` | 1 | PASS |

## Reasoning regression

| Test | Asserted? | Entailed? | Result |
|---|---:|---:|---|
| DR1 | Yes | Yes | PASS |
| DR2 | Yes | Yes | PASS |
| DR3 | Yes | Yes | PASS |
| DR4 | Yes | Yes | PASS |
| DR5 | Yes | Yes | PASS |
| DR6 | Yes | Yes | PASS |
| DR7 | Yes | Yes | PASS |
| DR8 | Yes | Yes | PASS |
| DR9 | No | Yes | PASS |
| DR10 | Yes | Yes | PASS |
| DR11 | No | Yes | PASS |
| DR12 | No | Yes | PASS |

## Competency-question regression

| CQ | Result rows | Result |
|---|---:|---|
| CQ01 | 1 | PASS |
| CQ02 | 1 | PASS |
| CQ03 | 1 | PASS |
| CQ04 | 1 | PASS |
| CQ05 | 1 | PASS |
| CQ06 | 1 | PASS |
| CQ07 | 2 | PASS |
| CQ08 | 1 | PASS |
| CQ09 | 2 | PASS |
| CQ10 | 4 | PASS |
| CQ11 | 1 | PASS |
| CQ12 | 2 | PASS |
| CQ13 | 4 | PASS |
| CQ14 | 1 | PASS |
| CQ15 | 2 | PASS |
| CQ16 | 2 | PASS |
| CQ17 | 1 | PASS |
| CQ18 | 2 | PASS |
| CQ19 | 4 | PASS |
| CQ20 | 1 | PASS |
| CQ21 | 2 | PASS |
| CQ22 | 2 | PASS |
| CQ23 | 2 | PASS |
| CQ24 | 1 | PASS |
| CQ25 | 1 | PASS |
| CQ26 | 4 | PASS |

## Validation interpretation

v0.3.2 is the first baseline in this sequence to pass the complete current verification stack: syntax, SHACL-style constraint checks, reasoning regression, and all 26 competency-question SPARQL tests.

A standards-engine validation using pySHACL or Apache Jena remains a useful independent reproducibility check before publication, but the ontology and test artefacts are internally consistent under the constraints currently defined.