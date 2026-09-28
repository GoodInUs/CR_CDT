# Cognitive Urban Twin v0.3.2 — Verification and Chapter Narrative Scaffold

## 1. Purpose of the demonstrator

The exemplar demonstrates how an ontology-driven cognitive urban twin can move beyond monitoring and scenario representation toward evidence-grounded, explainable and closed-loop decision support. A heatwave scenario is used to connect environmental hazard, digital infrastructure, electricity-grid constraints and dependent urban services to a bounded decision context and a set of anticipatory interventions.

## 2. Urban dependency model

The initiating `Heatwave_August_01` individual threatens `DataCentre_East_01`. The data centre contributes demand to `GridConstraint_East_01`, while `ElectricityGrid_East` both supplies the data centre and experiences the same constraint. `UrbanService_TrafficManagement` depends on the data centre and is linked through `hasServiceImpactTarget` to `ImpactForecast_Heatwave_01`. The ontology therefore represents both physical/operational dependencies and their potential service consequences.

## 3. Evidence-grounded decision context

Four `DecisionEvidence` individuals ground the decision in heterogeneous evidence: a heat forecast, data-centre telemetry, electricity-grid state and service-dependency evidence. These evidence objects are attached to `DecisionContext_Heatwave_01`, together with affected infrastructure and services, the impact assessment, decision risk, available flexibility and candidate actions. This makes the decision itself, rather than the interoperating systems alone, an explicit semantic object.

## 4. Recommendation and explainability

`CognitiveTwin_City_01` has the heatwave decision context and generates `Recommendation_Heatwave_01`. The recommendation selects a composite response consisting of deferring elastic compute load and dispatching battery storage. The recommendation is linked to `Explanation_Heatwave_01`, which records provenance, confidence and the evidence supporting the recommendation. This provides a traceable relationship between evidence, decision context, recommendation and intervention.

## 5. Closed-loop adaptation

Both selected actions return outcome data to `ObservationBase_City_01`. The updated state is supplied to `PredictionScenarioEngine_01`, which produces an updated impact forecast and feeds an updated scenario back to `CognitiveTwin_City_01`. The model therefore represents an iterative loop of observation, contextualisation, assessment, decision, intervention, outcome observation and predictive reassessment.

## 6. Verification approach

Verification was performed at several complementary levels. First, the exemplar was manually inspected in WebProtégé at class, property and individual levels. Second, 26 competency questions were encoded as SPARQL queries covering hazard awareness, infrastructure dependency, evidence, impact, decision context, action selection, explainability and feedback. All 26 returned the expected exemplar results. Third, decision-reasoning regression checks passed 12/12. Fourth, the v0.3.2 validation-clean model passed all 11 currently defined SHACL-style property constraints after validation identified and corrected two literal datatype issues and confirmed subclass-aware action typing.

## 7. What the demonstrator establishes

The demonstrator shows that the ontology can connect heterogeneous urban-domain knowledge to a decision-centred semantic structure and preserve an end-to-end trace from initiating hazard and supporting evidence through impact assessment, candidate interventions, recommendation, explanation, selected action and subsequent observation. It therefore provides a semantic foundation for explainable and adaptive cognitive-twin decision support.

## 8. Current limitations

The exemplar is intentionally bounded and should not yet be presented as evidence of city-scale operational performance. The current validation demonstrates structural, query-level and constraint-level coherence of the exemplar. Independent standards-engine SHACL validation and fuller OWL reasoner consistency testing remain desirable before publication. Quantitative optimisation of competing interventions, uncertainty propagation, formal provenance modelling and evaluation against live or historical city datasets are also natural extensions.

## 9. Publication figure

Use `Cognitive_Urban_Twin_Closed_Loop_Decision_Trace_v0.3.2.mmd` as the canonical simplified reasoning figure. The full ontology remains the source of truth; the figure is a publication-oriented projection of the validated decision trace.
