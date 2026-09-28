# Cognitive Urban Twin — v0.2 + Heatwave Scenario

Open this file directly in Protégé/WebProtégé:

`cognitive-urban-twin-v0.2-with-heatwave-scenario.ttl`

## What to inspect

### Classes → Individuals

Expand these classes and check that the following individuals appear:

- `ExtremeHeat`
  - `Heatwave_August_01`

- `DataCentre`
  - `DataCentre_East_01`

- `ElectricityGrid`
  - `ElectricityGrid_East`

- `GridConstraint`
  - `GridConstraint_East_01`

- `UrbanService`
  - `UrbanService_TrafficManagement`
  - `UrbanService_EmergencyResponse`

- `ImpactForecast`
  - `ImpactForecast_Heatwave_01`

- `CognitiveTwin`
  - `CognitiveTwin_City_01`

- `ObservationBase`
  - `ObservationBase_City_01`

- `KnowledgeBase`
  - `KnowledgeBase_City_01`

- `DecisionBase`
  - `DecisionBase_City_01`

- `PredictionScenarioEngine`
  - `PredictionScenarioEngine_01`

- `DecisionRecommendation`
  - `Recommendation_Heatwave_01`

- `ExplanationAssurance`
  - `Explanation_Heatwave_01`

- `WorkloadManagement`
  - `Action_Defer_Elastic_Load_01`

- `GridBrokering`
  - `Action_Dispatch_Battery_01`

## Key object-property checks

Select the individuals and confirm these assertions:

- `Heatwave_August_01`
  - `threatens` → `DataCentre_East_01`

- `UrbanService_TrafficManagement`
  - `dependsOn` → `DataCentre_East_01`

- `UrbanService_EmergencyResponse`
  - `dependsOn` → `DataCentre_East_01`

- `ElectricityGrid_East`
  - `suppliesElectricityTo` → `DataCentre_East_01`

- `ImpactForecast_Heatwave_01`
  - `hasHazardInput` → `Heatwave_August_01`
  - `providesRiskContextTo` → `CognitiveTwin_City_01`

- `CognitiveTwin_City_01`
  - `hasObservationBase` → `ObservationBase_City_01`
  - `hasKnowledgeBase` → `KnowledgeBase_City_01`
  - `hasDecisionBase` → `DecisionBase_City_01`
  - `generatesRecommendation` → `Recommendation_Heatwave_01`

- `Recommendation_Heatwave_01`
  - `justifiedBy` → `Explanation_Heatwave_01`
  - `recommendsAction` → both action individuals

- both actions
  - `returnsOutcomeDataTo` → `ObservationBase_City_01`

## What this proves

This merged ontology demonstrates the complete conceptual chain:

`Hazard → Infrastructure → Service Dependency → Impact Forecast → Cognitive Twin → Recommendation → Action → Observation Feedback`

It is now suitable for:
- Protégé exploration
- SPARQL querying
- reasoner experiments
- SHACL validation
- chapter screenshots / demonstration
