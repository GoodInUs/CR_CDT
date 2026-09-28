# Cognitive Urban Twin — v0.3.1 WebProtégé-Clean Verification

The anonymous DecisionContext OWL restrictions were removed from the class hierarchy and moved to SHACL.

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

## WebProtégé expectation

`DecisionContext` should now appear as a normal named class with no blank/UUID restriction parents.

The minimum-cardinality requirements are preserved in the companion SHACL file instead.