# Cognitive Urban Twin — Reasoning Test Pack v0.2.1

Corrected ontology with guaranteed inverse-property axioms.

| Test | Inference | Asserted? | Entailed? | Result |
|---|---|---:|---:|---|
| R1 | Heatwave inferred as WeatherHazard | No | Yes | PASS |
| R2 | Workload action inferred as AnticipatoryAction | No | Yes | PASS |
| R3 | Data centre inferred as isDependedOnBy traffic service | No | Yes | PASS |
| R4 | Data centre inferred as isThreatenedBy heatwave | No | Yes | PASS |
| R5 | Data centre inferred as isSuppliedElectricityBy grid | No | Yes | PASS |
| R6 | dependsOn entails generic dependency relationship | No | Yes | PASS |
| R7 | threatens entails generic risk relationship | No | Yes | PASS |
| R8 | recommendsAction entails generic decision relationship | No | Yes | PASS |
| R9 | DataCentre type available | Yes | Yes | PASS |
| R10 | Threat subject inferred as WeatherHazard | No | Yes | PASS |

## Interpretation

Rows with Asserted = No and Entailed = Yes demonstrate genuinely derived knowledge.

This lightweight test suite covers:
- subclass/type inference
- inverse-property inference
- property-hierarchy inference
- domain/range inference.