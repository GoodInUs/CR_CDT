# Cognitive Urban Twin — SHACL Constraint Check v0.3.1

- Ontology syntax: **PASS** (876 triples)
- SHACL syntax: **PASS** (64 triples)
- Property-constraint checks executed: **11**
- Constraint violations: **3**
- Overall result: **FAIL**

## Constraint results

| Focus node | Property | Values | Result |
|---|---|---:|---|
| `DecisionContext_Heatwave_01` | `hasDecisionStatus` | 1 | PASS |
| `DecisionContext_Heatwave_01` | `hasDecisionRisk` | 1 | PASS |
| `DecisionContext_Heatwave_01` | `decisionWindow` | 1 | PASS |
| `DecisionContext_Heatwave_01` | `decisionUrgency` | 1 | FAIL |
| `DecisionContext_Heatwave_01` | `hasAffectedInfrastructure` | 1 | PASS |
| `DecisionContext_Heatwave_01` | `hasRiskAssessment` | 1 | PASS |
| `DecisionContext_Heatwave_01` | `hasCandidateAction` | 2 | PASS |
| `DecisionContext_Heatwave_01` | `hasDecisionEvidence` | 4 | PASS |
| `Recommendation_Heatwave_01` | `justifiedBy` | 1 | PASS |
| `Recommendation_Heatwave_01` | `recommendsAction` | 2 | FAIL |
| `Recommendation_Heatwave_01` | `recommendationId` | 1 | FAIL |

## Violations

- `https://example.org/cognitive-urban-twin#DecisionContext_Heatwave_01` / `https://example.org/cognitive-urban-twin#decisionUrgency`: High does not have datatype http://www.w3.org/2001/XMLSchema#string
- `https://example.org/cognitive-urban-twin#Recommendation_Heatwave_01` / `https://example.org/cognitive-urban-twin#recommendsAction`: https://example.org/cognitive-urban-twin#Action_Defer_Elastic_Load_01 is not explicitly typed https://example.org/cognitive-urban-twin#AnticipatoryAction; https://example.org/cognitive-urban-twin#Action_Dispatch_Battery_01 is not explicitly typed https://example.org/cognitive-urban-twin#AnticipatoryAction
- `https://example.org/cognitive-urban-twin#Recommendation_Heatwave_01` / `https://example.org/cognitive-urban-twin#recommendationId`: REC-HEAT-001 does not have datatype http://www.w3.org/2001/XMLSchema#string

## Validation note

The environment did not contain the pySHACL package, so this report evaluates the specific SHACL Core property constraints used by the v0.3.1 shapes graph directly against the RDF graph. A standards-engine pySHACL/Jena validation remains a useful independent reproducibility check before publication.