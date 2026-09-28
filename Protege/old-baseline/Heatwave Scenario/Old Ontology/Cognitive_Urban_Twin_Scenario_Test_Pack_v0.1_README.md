# Cognitive Urban Twin — Scenario Test Pack v0.1

## Files

- `cognitive-urban-twin-scenario-heatwave-v0.1.ttl`
  - Example individuals for a heatwave / data-centre / urban-service scenario.

- `cognitive-urban-twin-sparql-v0.1/`
  - SPARQL queries implementing a subset of the competency questions.

- `cognitive-urban-twin-heatwave-validation-v0.1.txt`
  - Local SHACL validation result.

## Scenario narrative

A severe heatwave threatens `DataCentre_East_01` while the electricity grid is constrained.
Traffic-management and emergency-response services depend on that data centre.
The Cognitive Twin receives observations and a semantic model, evaluates an impact forecast,
generates a recommendation, and recommends two actions:

1. defer/throttle an elastic workload;
2. dispatch battery/grid flexibility.

Both actions return outcome data to the Observation Base.

## Query execution test

- CQ1_hazard_exposure.rq: 0 row(s)
- CQ2_service_dependency.rq: 2 row(s)
- CQ5_impact_forecast.rq: 1 row(s)
- CQ10_twin_state.rq: 1 row(s)
- CQ12_recommendation_generation.rq: 1 row(s)
- CQ13_recommendation_assurance.rq: 1 row(s)
- CQ14_recommended_actions.rq: 2 row(s)
- CQ19_traceability.rq: 2 row(s)

## Protégé use

Import/open the ontology first:
`cognitive-urban-twin-v0.2.ttl`

Then import or merge the scenario data:
`cognitive-urban-twin-scenario-heatwave-v0.1.ttl`

The scenario individuals should then appear under the relevant classes.
