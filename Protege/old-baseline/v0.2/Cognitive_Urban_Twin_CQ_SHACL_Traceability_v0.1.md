# Cognitive Urban Twin — CQ / SHACL Traceability v0.1

| CQ | Core ontology elements | SHACL coverage | Status |
|---|---|---|---|
| CQ1 Hazard exposure | WeatherHazard, DataCentre, threatens | ThreatenedDataCentreShape | Partial |
| CQ2 Service dependency | UrbanService, DataCentre, dependsOn | ServiceDependencyShape | Partial |
| CQ3 Power dependency | ElectricityGrid, DataCentre, suppliesElectricityTo | Not yet constrained | Open |
| CQ4 Grid constraints | GridConstraint, contributesDemandTo, experiencesGridConstraint | Not yet constrained | Open |
| CQ5 Impact assessment | WeatherHazard, ImpactForecast, hasHazardInput | ImpactForecastShape | Covered |
| CQ6 Vulnerability/exposure | VulnerabilityProfile, ExposureProfile, ImpactForecast | Requires explicit informedBy modelling | Open |
| CQ7 Service risk | UrbanService, ImpactForecast | Not yet constrained | Open |
| CQ8 Flexibility availability | FlexibleResource subclasses | Not yet constrained | Open |
| CQ9 Elastic workload flexibility | ElasticDataLoad, ComputeFlexibility | Not yet constrained | Open |
| CQ10 Twin state | CognitiveTwin + three bases | CognitiveTwinShape | Covered |
| CQ11 Scenario generation | ObservationBase, KnowledgeBase, PredictionScenarioEngine | Not yet constrained | Open |
| CQ12 Recommendation generation | CognitiveTwin, DecisionRecommendation | DecisionRecommendationShape | Partial |
| CQ13 Recommendation assurance | DecisionRecommendation, ExplanationAssurance | DecisionRecommendationShape | Covered |
| CQ14 Recommended actions | DecisionRecommendation, AnticipatoryAction | DecisionRecommendationShape | Covered |
| CQ15 Action feedback | AnticipatoryAction, ObservationBase | Not yet constrained | Open |
| CQ16 Data-centre response | DataCentreFeedbackAction hierarchy | AnticipatoryActionShape | Partial |
| CQ17 Service response | UrbanServiceFeedbackAction hierarchy | AnticipatoryActionShape | Partial |
| CQ18 Semantic representation | KnowledgeBase, represents, interprets | Not yet constrained | Open |
| CQ19 Traceability | End-to-end reasoning chain | Future SPARQL/SHACL-AF test | Open |
| CQ20 Decision readiness | Recommendation completeness | DecisionRecommendationShape | Covered |
