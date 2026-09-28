# Cognitive Urban Twin — Complete Mermaid Figure Pack v1.0

**Status:** Reconstructed authoritative source from the verified publication figures and ontology traceability artefacts.  
**Scope:** Figures 4.1–4.8.  
**Design principle:** The ontology / Cognitive Twin Knowledge Core is treated as the semantic single source of truth across architecture, reasoning, dependency analysis, decision support, feedback and adaptation.

> Mermaid rendering can vary slightly between Mermaid versions. The source below uses standard Mermaid flowchart, classDiagram and sequenceDiagram syntax and avoids non-portable extensions where possible.

---

## Shared visual convention

The figures use a common semantic colour mapping:

- Blue — Hazard, weather, external context
- Green — Forecast and impact assessment
- Purple — Cognitive Twin Knowledge Core
- Orange — Data centre capability
- Teal — Urban service capability
- Gold — Cross-domain dependency
- Dark green — Decision, feedback and resilience

---

# Figure 4.1 — Cognitive Urban Twin Architecture

```mermaid
flowchart TB

%% ============================================================
%% Figure 4.1 Cognitive Urban Twin Architecture
%% ============================================================

subgraph EC["EXTERNAL CONTEXT<br/>Environment and external drivers influencing the city"]
direction LR
HC["Hazard & Context<br/>• ExtremeWeatherEvent<br/>• AffectedArea<br/>• EventSeverity<br/>• EventUncertainty"]
WO["Weather Observation<br/>• WeatherObservation<br/>• ObservationLocation<br/>• ObservationTime<br/>• ObservedParameter"]
WF["Weather Forecast<br/>• WeatherForecast<br/>• ForecastModel<br/>• ForecastTime<br/>• ForecastHorizon"]
ENV["Environment<br/>• EnvironmentalCondition<br/>• AirQualityIndex<br/>• Temperature<br/>• Humidity"]
GEO["Geospatial Context<br/>• SpatialRegion<br/>• LandUseType<br/>• Elevation<br/>• PopulationDensity"]
EXT["External Systems<br/>• ExternalSystem<br/>• UpstreamDependency<br/>• RegulatoryConstraint<br/>• MarketCondition"]
end

subgraph CTC["COGNITIVE TWIN CORE<br/>Knowledge, reasoning and decision intelligence"]
direction LR
KB["Knowledge Base<br/>• ObservationBase<br/>• DomainModel<br/>• InstanceData<br/>• ProvenanceRecord"]
DM["Dependency Model<br/>• CrossDomainDependency<br/>• DependencyCondition<br/>• DependencyCriticality<br/>• DependencyEvidence"]
IA["Impact Assessment<br/>• ImpactAssessment<br/>• ImpactType<br/>• ImpactMagnitude<br/>• ImpactLikelihood"]
DE["Decision Engine<br/>• ReasoningEngine<br/>• ScenarioSimulation<br/>• DecisionRecommendation<br/>• Explanation"]

KB <--> DM
DM <--> IA
IA <--> DE
end

subgraph DOMAINS["OPERATIONAL DOMAINS"]
direction LR

subgraph DC["DATA CENTRE DOMAIN"]
direction TB
DC1["Data Centre<br/>• DataCentre<br/>• Location<br/>• Operator<br/>• PowerCapacity"]
DC2["Computational Capability<br/>• ComputationalCapability<br/>• CapabilityType<br/>• Capacity<br/>• Availability"]
DC3["Computational Workload<br/>• ComputationalWorkload<br/>• WorkloadType<br/>• Priority<br/>• ResourceDemand"]
DC4["Supporting Resources<br/>• SupportingResource<br/>• Power<br/>• Cooling<br/>• Network"]
DC5["Operational State<br/>• OperationalState<br/>• StateType<br/>• HealthStatus<br/>• CapacityConstraint"]
DC1 --> DC2
DC2 --> DC3
DC4 --> DC2
DC5 --> DC2
end

subgraph XDD["CROSS-DOMAIN DEPENDENCY"]
direction TB
XD1["CrossDomainDependency"]
XD2["DependencyType"]
XD3["DependencyDirection"]
XD4["DependencyCriticality"]
XD5["DependencyCondition"]
XD6["DependencyEvidence"]
XD1 --> XD2
XD1 --> XD3
XD1 --> XD4
XD1 --> XD5
XD1 --> XD6
end

subgraph US["URBAN SERVICE DOMAIN"]
direction TB
US1["Urban Service<br/>• UrbanService<br/>• ServiceType<br/>• ServiceProvider<br/>• ServiceSLA"]
US2["Service Capability<br/>• ServiceCapability<br/>• Capacity<br/>• Availability<br/>• Performance"]
US3["Service Demand<br/>• ServiceDemand<br/>• DemandLevel<br/>• PopulationGroup<br/>• TemporalProfile"]
US4["Service Criticality<br/>• ServiceCriticality<br/>• CriticalityLevel<br/>• Priority<br/>• Consequence"]
US5["Service Operational State<br/>• ServiceOperationalState<br/>• StateType<br/>• HealthStatus<br/>• Degradation"]
US1 --> US2
US3 --> US2
US4 --> US2
US5 --> US2
end
end

subgraph DFR["DECISION, FEEDBACK & RESILIENCE"]
direction LR
DR["Decision Recommendation<br/>• DecisionRecommendation<br/>• RecommendedAction<br/>• Priority<br/>• Confidence"]
AE["Action Execution<br/>• ActionExecution<br/>• ActionType<br/>• TargetEntity<br/>• Status"]
OUT["Outcome<br/>• Outcome<br/>• OutcomeType<br/>• SuccessLevel<br/>• ImpactObserved"]
AR["Adaptation & Recovery<br/>• AdaptationAction<br/>• RecoveryPlan<br/>• ResourceReallocation<br/>• TimeToRecover"]
EP["Evidence & Provenance<br/>• EvidenceRecord<br/>• Source<br/>• Timestamp<br/>• Confidence"]
ML["Metrics & Learning<br/>• EvaluationMetric<br/>• MetricValue<br/>• Trend<br/>• LearningInsight"]

DR --> AE --> OUT --> AR
OUT --> EP
OUT --> ML
end

EC -. "provides context to" .-> CTC
CTC -. "integrates data and models from domains" .-> DC
CTC -. "integrates data and models from domains" .-> US
DC <-->|"depends on / supplies"| XDD
XDD <-->|"depends on / supplies"| US
DC -. "operational evidence" .-> CTC
US -. "service evidence" .-> CTC
XDD -. "dependency evidence" .-> CTC
CTC -->|"generates recommendation"| DR
DFR -. "feedback updates knowledge and models" .-> CTC

classDef blue fill:#eef6ff,stroke:#2563eb,stroke-width:1.5px,color:#111;
classDef green fill:#effbf2,stroke:#2e8b57,stroke-width:1.5px,color:#111;
classDef purple fill:#f5efff,stroke:#7c3aed,stroke-width:1.5px,color:#111;
classDef orange fill:#fff5e8,stroke:#d97706,stroke-width:1.5px,color:#111;
classDef teal fill:#ecfeff,stroke:#0f8b8d,stroke-width:1.5px,color:#111;
classDef gold fill:#fff9db,stroke:#b58900,stroke-width:1.5px,color:#111;
classDef darkgreen fill:#eef8ee,stroke:#287a3d,stroke-width:1.5px,color:#111;

class HC,WO,WF,ENV,GEO,EXT blue;
class KB,DM,IA,DE purple;
class DC1,DC2,DC3,DC4,DC5 orange;
class XD1,XD2,XD3,XD4,XD5,XD6 gold;
class US1,US2,US3,US4,US5 teal;
class DR,AE,OUT,AR,EP,ML darkgreen;
```

---

# Figure 4.2 — Ontology Development Workflow for the Cognitive Urban Twin

```mermaid
flowchart LR

S1["1. LITERATURE & REQUIREMENTS<br/><br/>• Systematic literature review<br/>• Existing ontologies and standards<br/>• Domain knowledge elicitation<br/>• Scope definition<br/>• Stakeholder analysis<br/><br/><b>Outputs</b><br/>Requirements, scope,<br/>competency-question seed list"]

S2["2. ARCHITECTURE DESIGN<br/><br/>• Define ontology purpose and scope<br/>• Identify top-level modules<br/>• Establish boundaries and context<br/>• Align with Cognitive Twin architecture<br/><br/><b>Outputs</b><br/>Ontology architecture,<br/>module structure, scope document"]

S3["3. COMPETENCY QUESTIONS<br/><br/>• Develop competency questions<br/>• Validate with stakeholders<br/>• Refine and prioritise<br/>• Map to use cases and decision needs<br/><br/><b>Outputs</b><br/>Validated competency questions,<br/>use-case mapping"]

S4["4. ONTOLOGY MODULES<br/><br/>• Define module boundaries<br/>• Identify key themes per module<br/>• Iterate with domain experts<br/>• Ensure module coherence<br/><br/><b>Outputs</b><br/>Module specifications and<br/>module-to-module interfaces"]

S5["5. CANONICAL CLASSES<br/><br/>• Identify canonical classes<br/>• Apply naming conventions<br/>• Define essential attributes<br/>• Establish class hierarchy<br/><br/><b>Outputs</b><br/>Canonical classes,<br/>hierarchy and attributes"]

S6["6. RELATIONSHIPS & SEMANTICS<br/><br/>• Define object properties<br/>• Define cardinalities<br/>• Model dependencies<br/>• Define semantic constraints<br/>• Align reusable vocabularies<br/><br/><b>Outputs</b><br/>Relationship model,<br/>semantic rules and mappings"]

S7["7. UML / FORMAL MODELLING<br/><br/>• Produce UML class view<br/>• Map classes to ontology concepts<br/>• Map Mermaid to future OWL<br/>• Define enumerations<br/>• Trace decisions and evidence<br/><br/><b>Outputs</b><br/>Integrated conceptual ontology,<br/>traceability artefacts"]

S8["8. VALIDATION & ITERATION<br/><br/>• Test competency questions<br/>• Validate logical consistency<br/>• Apply SHACL constraints<br/>• Review with domain experts<br/>• Refine through use cases<br/><br/><b>Outputs</b><br/>Validated ontology,<br/>issues log and next iteration"]

S1 --> S2 --> S3 --> S4 --> S5 --> S6 --> S7 --> S8

S8 -. "iterate" .-> S3
S8 -. "refine architecture" .-> S2
S6 -. "new semantic requirements" .-> S4

subgraph PRINCIPLES["Cross-cutting principles"]
direction LR
P1["Traceability"]
P2["Modularity"]
P3["Reuse of standards"]
P4["Explainability"]
P5["Validation"]
P6["Governance"]
end

PRINCIPLES -.-> S1
PRINCIPLES -.-> S4
PRINCIPLES -.-> S7
PRINCIPLES -.-> S8

classDef blue fill:#eef6ff,stroke:#2563eb,stroke-width:1.5px;
classDef green fill:#effbf2,stroke:#2e8b57,stroke-width:1.5px;
classDef purple fill:#f5efff,stroke:#7c3aed,stroke-width:1.5px;
classDef orange fill:#fff5e8,stroke:#d97706,stroke-width:1.5px;
classDef teal fill:#ecfeff,stroke:#0f8b8d,stroke-width:1.5px;
classDef gold fill:#fff9db,stroke:#b58900,stroke-width:1.5px;
classDef grey fill:#f6f7f9,stroke:#6b7280,stroke-width:1px;

class S1 blue;
class S2 green;
class S3 purple;
class S4 orange;
class S5 teal;
class S6 gold;
class S7 purple;
class S8 green;
class P1,P2,P3,P4,P5,P6 grey;
```

---

# Figure 4.3 — Conceptual Ontology Modules for the Cognitive Urban Twin

```mermaid
flowchart TB

subgraph M1["1. HAZARD & CONTEXT<br/>Represents environmental conditions and hazard events affecting the city."]
direction TB
M1A["WeatherForecast"]
M1B["WeatherObservation"]
M1C["ExtremeWeatherEvent"]
M1D["AffectedArea"]
M1E["EventSeverity"]
M1F["EventUncertainty"]
end

subgraph M2["2. FORECAST & IMPACT ASSESSMENT<br/>Models forecasting outputs and assesses potential impacts and risks."]
direction TB
M2A["ForecastModel"]
M2B["ImpactAssessment"]
M2C["PredictedImpact"]
M2D["RiskLevel"]
M2E["ConfidenceAssessment"]
M2F["AssessmentEvidence"]
end

subgraph M3["3. COGNITIVE TWIN KNOWLEDGE CORE<br/>Central knowledge and reasoning layer integrating data, dependencies, impacts and decisions."]
direction TB
M3A["ObservationBase"]
M3B["KnowledgeBase"]
M3C["CrossDomainDependency"]
M3D["DependencyModel"]
M3E["ImpactReasoning"]
M3F["DecisionEngine"]
M3G["DecisionRecommendation"]
M3H["Scenario"]
M3I["Explanation"]
end

subgraph M4["4. DATA CENTRE CAPABILITY<br/>Captures data-centre assets, capabilities, state and workloads."]
direction TB
M4A["DataCentre"]
M4B["OperationalState"]
M4C["ComputationalCapability"]
M4D["ComputationalWorkload"]
M4E["SupportingResource"]
M4F["InfrastructureComponent"]
M4G["CapacityConstraint"]
end

subgraph M5["5. URBAN SERVICE CAPABILITY<br/>Represents critical urban services, capability, demand and operational state."]
direction TB
M5A["UrbanService"]
M5B["ServiceCapability"]
M5C["ServiceOperationalState"]
M5D["ServiceDemand"]
M5E["ServiceCriticality"]
M5F["PopulationGroup"]
M5G["ServiceDependency"]
M5H["ServiceProvider"]
M5I["ServiceSLA"]
end

subgraph M6["6. CROSS-DOMAIN DEPENDENCY<br/>Represents dependencies linking infrastructure and services across domains."]
direction TB
M6A["CrossDomainDependency"]
M6B["DependencyType"]
M6C["DependencyDirection"]
M6D["DependencyCriticality"]
M6E["DependencyCondition"]
M6F["DependencyEvidence"]
M6G["PropagationPath"]
end

subgraph M7["7. DECISION, FEEDBACK & RESILIENCE<br/>Represents recommendations, actions, outcomes, provenance and learning."]
direction TB
M7A["DecisionRecommendation"]
M7B["ActionExecution"]
M7C["ActionOutcome"]
M7D["AdaptationAction"]
M7E["RecoveryPlan"]
M7F["EvidenceRecord"]
M7G["ProvenanceRecord"]
M7H["EvaluationMetric"]
M7I["LearningInsight"]
end

M1 -. "context" .-> M2
M1 -. "observations" .-> M3
M2 -. "assessments" .-> M3
M4 -. "capability state" .-> M3
M5 -. "service state" .-> M3
M4 --> M6
M5 --> M6
M6 -. "dependency model" .-> M3
M3 -->|"recommendations"| M7
M7 -. "feedback / learning" .-> M3

classDef blue fill:#eef6ff,stroke:#2563eb,stroke-width:1.5px;
classDef green fill:#effbf2,stroke:#2e8b57,stroke-width:1.5px;
classDef purple fill:#f5efff,stroke:#7c3aed,stroke-width:1.5px;
classDef orange fill:#fff5e8,stroke:#d97706,stroke-width:1.5px;
classDef teal fill:#ecfeff,stroke:#0f8b8d,stroke-width:1.5px;
classDef gold fill:#fff9db,stroke:#b58900,stroke-width:1.5px;
classDef darkgreen fill:#eef8ee,stroke:#287a3d,stroke-width:1.5px;

class M1A,M1B,M1C,M1D,M1E,M1F blue;
class M2A,M2B,M2C,M2D,M2E,M2F green;
class M3A,M3B,M3C,M3D,M3E,M3F,M3G,M3H,M3I purple;
class M4A,M4B,M4C,M4D,M4E,M4F,M4G orange;
class M5A,M5B,M5C,M5D,M5E,M5F,M5G,M5H,M5I teal;
class M6A,M6B,M6C,M6D,M6E,M6F,M6G gold;
class M7A,M7B,M7C,M7D,M7E,M7F,M7G,M7H,M7I darkgreen;
```

---

# Figure 4.4 — Integrated Conceptual Ontology for the Cognitive Urban Twin
## UML Class View with Canonical Relationships

```mermaid
classDiagram

%% ============================================================
%% MODULE 1 — HAZARD & CONTEXT
%% ============================================================

class WeatherForecast {
  +DateTime forecastTime
  +Duration forecastHorizon
  +String resolution
  +String source
}

class WeatherObservation {
  +DateTime observationTime
  +String parameter
  +Decimal value
  +String source
}

class ExtremeWeatherEvent {
  +String eventType
  +DateTime startTime
  +DateTime endTime
  +String description
}

class EventSeverity {
  +SeverityLevel level
  +Decimal intensity
  +Decimal confidence
}

class AffectedArea {
  +Geometry geometry
  +AreaType areaType
  +String location
}

class EventUncertainty {
  +String uncertaintyType
  +Decimal value
  +String method
}

WeatherForecast --> ExtremeWeatherEvent : predicts
WeatherObservation --> ExtremeWeatherEvent : observes
ExtremeWeatherEvent --> AffectedArea : occursIn
ExtremeWeatherEvent --> EventSeverity : hasSeverity
ExtremeWeatherEvent --> EventUncertainty : hasUncertainty

%% ============================================================
%% MODULE 2 — FORECAST & IMPACT ASSESSMENT
%% ============================================================

class ForecastModel {
  +ModelType modelType
  +Duration horizon
  +String resolution
  +Duration updateFrequency
}

class ImpactAssessment {
  +DateTime assessmentTime
  +String scenario
  +String method
  +RiskLevel overallRisk
}

class PredictedImpact {
  +ImpactType impactType
  +Decimal magnitude
  +Decimal probability
  +String unit
}

class RiskAssessmentLevel {
  +RiskLevel level
  +Decimal score
  +Decimal confidence
}

class ConfidenceAssessment {
  +Decimal confidence
  +String method
  +String evidenceBasis
}

class AssessmentEvidence {
  +String evidenceId
  +String source
  +DateTime timestamp
  +Decimal confidence
}

ForecastModel --> ImpactAssessment : generates
ImpactAssessment --> PredictedImpact : produces
ImpactAssessment --> RiskAssessmentLevel : determines
ImpactAssessment --> ConfidenceAssessment : estimates
PredictedImpact --> AssessmentEvidence : supportedBy
RiskAssessmentLevel --> AssessmentEvidence : supportedBy
ConfidenceAssessment --> AssessmentEvidence : supportedBy
ExtremeWeatherEvent --> ImpactAssessment : affects

%% ============================================================
%% MODULE 3 — COGNITIVE TWIN KNOWLEDGE CORE
%% ============================================================

class ObservationBase {
  +String observationId
  +DateTime time
  +String source
  +QualityLevel quality
}

class KnowledgeBase {
  +String knowledgeBaseId
  +String version
  +DateTime updatedAt
}

class DependencyModel {
  +String modelId
  +String modelType
  +String version
}

class ImpactReasoning {
  +String reasoningId
  +String ruleSet
  +DateTime executedAt
}

class DecisionEngine {
  +String engineId
  +String engineType
  +String version
}

class DecisionRecommendation {
  +String recommendationId
  +String recommendation
  +PriorityLevel priority
  +Decimal confidence
}

class Scenario {
  +String scenarioId
  +String name
  +String description
  +DateTime createdAt
}

class Explanation {
  +String explanationId
  +String rationale
  +String evidenceSummary
  +Decimal confidence
}

KnowledgeBase o-- ObservationBase : contains
KnowledgeBase o-- DependencyModel : contains
KnowledgeBase o-- Scenario : contains
ImpactAssessment --> KnowledgeBase : updates
DependencyModel --> ImpactReasoning : informs
ImpactReasoning --> DecisionEngine : suppliesInference
DecisionEngine --> DecisionRecommendation : generates
DecisionRecommendation --> Explanation : explainedBy
Scenario --> ImpactReasoning : evaluatedBy

%% ============================================================
%% MODULE 4 — DATA CENTRE CAPABILITY
%% ============================================================

class DataCentre {
  +String dataCentreId
  +String name
  +String location
  +String operator
}

class ComputationalCapability {
  +String capabilityId
  +String capabilityType
  +Decimal capacity
  +Decimal availability
}

class ComputationalWorkload {
  +String workloadId
  +WorkloadType workloadType
  +PriorityLevel priority
  +Decimal resourceDemand
}

class OperationalState {
  +String stateId
  +OperationalStateType stateType
  +Decimal availability
  +DateTime timestamp
}

class SupportingResource {
  +String resourceId
  +ResourceType resourceType
  +Decimal capacity
  +Decimal availability
}

class InfrastructureComponent {
  +String componentId
  +String componentType
  +String status
}

class CapacityConstraint {
  +String constraintId
  +String constraintType
  +Decimal threshold
  +String unit
}

DataCentre *-- InfrastructureComponent : comprises
DataCentre o-- ComputationalCapability : provides
DataCentre o-- SupportingResource : uses
ComputationalCapability --> ComputationalWorkload : supports
DataCentre --> OperationalState : hasState
ComputationalCapability --> CapacityConstraint : constrainedBy
SupportingResource --> CapacityConstraint : constrainedBy

%% ============================================================
%% MODULE 5 — URBAN SERVICE CAPABILITY
%% ============================================================

class UrbanService {
  +String serviceId
  +String serviceType
  +String name
}

class ServiceCapability {
  +String capabilityId
  +Decimal capacity
  +Decimal availability
  +Decimal performance
}

class ServiceOperationalState {
  +String stateId
  +OperationalStateType stateType
  +Decimal degradation
  +DateTime timestamp
}

class ServiceDemand {
  +String demandId
  +Decimal demandLevel
  +String temporalProfile
}

class ServiceCriticality {
  +CriticalityLevel criticality
  +PriorityLevel priority
  +String consequence
}

class PopulationGroup {
  +String populationGroupId
  +String description
  +Decimal populationSize
}

class ServiceDependency {
  +String dependencyId
  +DependencyType dependencyType
  +CriticalityLevel criticality
}

class ServiceProvider {
  +String providerId
  +String name
  +String organisationType
}

class ServiceSLA {
  +String slaId
  +Decimal availabilityTarget
  +Duration responseTarget
}

UrbanService o-- ServiceCapability : provides
UrbanService --> ServiceOperationalState : hasState
UrbanService --> ServiceDemand : experiences
UrbanService --> ServiceCriticality : hasCriticality
ServiceDemand --> PopulationGroup : relatesTo
UrbanService --> ServiceDependency : hasDependency
ServiceProvider --> UrbanService : operates
UrbanService --> ServiceSLA : governedBy

%% ============================================================
%% MODULE 6 — CROSS-DOMAIN DEPENDENCY
%% ============================================================

class CrossDomainDependency {
  +String dependencyId
  +DependencyType dependencyType
  +DependencyDirection direction
  +CriticalityLevel criticality
}

class DependencyCondition {
  +String conditionId
  +String expression
  +Decimal threshold
}

class DependencyEvidence {
  +String evidenceId
  +String evidenceType
  +String source
  +Decimal confidence
}

class PropagationPath {
  +String pathId
  +Integer hopCount
  +Decimal propagationConfidence
}

DataCentre --> CrossDomainDependency : participatesIn
UrbanService --> CrossDomainDependency : participatesIn
CrossDomainDependency --> DependencyCondition : activatedBy
CrossDomainDependency --> DependencyEvidence : supportedBy
CrossDomainDependency --> PropagationPath : propagatesVia
CrossDomainDependency --> DependencyModel : representedIn

%% ============================================================
%% MODULE 7 — DECISION, FEEDBACK & RESILIENCE
%% ============================================================

class ActionExecution {
  +String executionId
  +ActionType actionType
  +ExecutionStatus status
  +DateTime startTime
  +DateTime endTime
}

class ActionOutcome {
  +String outcomeId
  +String result
  +Boolean success
  +Decimal impact
}

class AdaptationAction {
  +String actionId
  +ActionType actionType
  +PriorityLevel priority
}

class RecoveryPlan {
  +String recoveryPlanId
  +String objective
  +Duration targetRecoveryTime
}

class EvidenceRecord {
  +String evidenceId
  +EvidenceType evidenceType
  +String source
  +QualityLevel quality
}

class ProvenanceRecord {
  +String recordId
  +DateTime generatedAt
  +String generatedBy
  +String method
}

class EvaluationMetric {
  +String metricId
  +MetricType metricType
  +Decimal value
  +String unit
}

class LearningInsight {
  +String insightId
  +String finding
  +Decimal confidence
}

DecisionRecommendation --> ActionExecution : authorises
ActionExecution --> ActionOutcome : produces
ActionOutcome --> AdaptationAction : triggers
AdaptationAction --> RecoveryPlan : contributesTo
ActionOutcome --> EvidenceRecord : evidencedBy
EvidenceRecord --> ProvenanceRecord : hasProvenance
ActionOutcome --> EvaluationMetric : evaluatedBy
EvaluationMetric --> LearningInsight : generates
LearningInsight --> KnowledgeBase : updates

%% ============================================================
%% CROSS-MODULE RELATIONSHIPS
%% ============================================================

WeatherObservation --> ObservationBase : contributesTo
WeatherForecast --> ForecastModel : generatedBy
AssessmentEvidence --> EvidenceRecord : becomes
OperationalState --> ObservationBase : contributesTo
ServiceOperationalState --> ObservationBase : contributesTo
ComputationalCapability --> DependencyModel : representedIn
ServiceCapability --> DependencyModel : representedIn
DecisionRecommendation --> EvidenceRecord : justifiedBy
Explanation --> EvidenceRecord : references

%% ============================================================
%% ENUMERATIONS / CONTROLLED VOCABULARIES
%% ============================================================

class SeverityLevel {
  <<enumeration>>
  Low
  Medium
  High
  Critical
}

class AreaType {
  <<enumeration>>
  Point
  Line
  Polygon
  Region
}

class ModelType {
  <<enumeration>>
  Weather
  DataCentre
  Service
  CrossDomain
}

class RiskLevel {
  <<enumeration>>
  Low
  Medium
  High
  VeryHigh
  Extreme
}

class WorkloadType {
  <<enumeration>>
  HPC
  AI_ML
  Analytics
  Storage
  Inference
  Batch
}

class OperationalStateType {
  <<enumeration>>
  Operational
  Degraded
  PartialOutage
  Outage
  Maintenance
}

class DependencyType {
  <<enumeration>>
  Power
  Cooling
  Network
  Data
  Service
  Logistical
  Regulatory
}

class DependencyDirection {
  <<enumeration>>
  Upstream
  Downstream
  Bidirectional
}

class ActionType {
  <<enumeration>>
  WorkloadShift
  LoadShedding
  CoolingAdjust
  BatteryDispatch
  TrafficReroute
  PublicAlert
  ResourceAllocate
  Other
}

class ExecutionStatus {
  <<enumeration>>
  Planned
  InProgress
  Completed
  Failed
  Cancelled
}

class DomainType {
  <<enumeration>>
  DataCentre
  UrbanService
}

class PriorityLevel {
  <<enumeration>>
  Low
  Medium
  High
  Critical
}

class CriticalityLevel {
  <<enumeration>>
  Low
  Medium
  High
  Critical
}

class EvidenceType {
  <<enumeration>>
  Observation
  Forecast
  ModelOutput
  OperatorReport
  SensorData
  Other
}

class MetricType {
  <<enumeration>>
  Availability
  ResponseTime
  Throughput
  Risk
  Cost
  Other
}

class QualityLevel {
  <<enumeration>>
  High
  Medium
  Low
  Unknown
}

class ResourceType {
  <<enumeration>>
  Power
  Cooling
  Network
  Storage
  Compute
  Other
}
```

---

# Figure 4.5 — Semantic Relationship Model Across the Cognitive Urban Twin Ontology

```mermaid
flowchart TB

%% HAZARD & CONTEXT
subgraph H["1. HAZARD & CONTEXT"]
direction TB
WF["WeatherForecast"]
WO["WeatherObservation"]
EWE["ExtremeWeatherEvent"]
AA["AffectedArea"]
ES["EventSeverity"]
EU["EventUncertainty"]

WF <-->|"refines 0..*"| WO
WF -->|"predicts 1..*"| EWE
WO -->|"observes 1..*"| EWE
EWE -->|"occursIn 1..*"| AA
EWE -->|"hasSeverity 1"| ES
EWE -->|"hasUncertainty 0..1"| EU
end

%% FORECAST & IMPACT
subgraph F["2. FORECAST & IMPACT ASSESSMENT"]
direction TB
FM["ForecastModel"]
IA["ImpactAssessment"]
PI["PredictedImpact"]
RL["RiskLevel"]
CA["ConfidenceAssessment"]
AE["AssessmentEvidence"]

FM -->|"generates 1..*"| IA
IA -->|"produces 1..*"| PI
IA -->|"determines 1"| RL
IA -->|"estimates 1"| CA
PI -->|"supportedBy 1..*"| AE
RL -->|"supportedBy 1..*"| AE
CA -->|"supportedBy 1..*"| AE
end

%% DATA CENTRE
subgraph D["4. DATA CENTRE CAPABILITY"]
direction TB
DC["DataCentre"]
CC["ComputationalCapability"]
CW["ComputationalWorkload"]
OS["OperationalState"]
SR["SupportingResource"]
IC["InfrastructureComponent"]
CT["CapacityConstraint"]

DC -->|"provides 1..*"| CC
CC -->|"supports 0..*"| CW
DC -->|"hasState 1"| OS
DC -->|"uses 1..*"| SR
DC -->|"comprises 1..*"| IC
CC -->|"constrainedBy 0..*"| CT
end

%% URBAN SERVICE
subgraph U["5. URBAN SERVICE CAPABILITY"]
direction TB
US["UrbanService"]
SC["ServiceCapability"]
SOS["ServiceOperationalState"]
SD["ServiceDemand"]
SCT["ServiceCriticality"]
PG["PopulationGroup"]
SDEP["ServiceDependency"]
SP["ServiceProvider"]
SLA["ServiceSLA"]

US -->|"provides 1..*"| SC
US -->|"hasState 1"| SOS
US -->|"experiences 0..*"| SD
US -->|"hasCriticality 1"| SCT
SD -->|"relatesTo 1..*"| PG
US -->|"hasDependency 0..*"| SDEP
SP -->|"operates 1..*"| US
US -->|"governedBy 0..1"| SLA
end

%% CROSS DOMAIN
subgraph X["6. CROSS-DOMAIN DEPENDENCY"]
direction TB
CDD["CrossDomainDependency"]
DCON["DependencyCondition"]
DEVID["DependencyEvidence"]
PP["PropagationPath"]

CDD -->|"activatedBy 0..*"| DCON
CDD -->|"supportedBy 1..*"| DEVID
CDD -->|"propagatesVia 0..*"| PP
end

%% CORE
subgraph C["3. COGNITIVE TWIN KNOWLEDGE CORE"]
direction TB
OB["ObservationBase"]
KB["KnowledgeBase"]
DM["DependencyModel"]
IR["ImpactReasoning"]
DE["DecisionEngine"]
DR["DecisionRecommendation"]
SCEN["Scenario"]
EXP["Explanation"]

KB o--|"contains 0..*"| OB
KB o--|"contains 0..*"| DM
KB o--|"contains 0..*"| SCEN
DM -->|"informs"| IR
SCEN -->|"evaluatedBy"| IR
IR -->|"suppliesInference"| DE
DE -->|"generates 1..*"| DR
DR -->|"explainedBy 1"| EXP
end

%% DECISION / FEEDBACK
subgraph R["7. DECISION, FEEDBACK & RESILIENCE"]
direction TB
AX["ActionExecution"]
AO["ActionOutcome"]
ADA["AdaptationAction"]
RP["RecoveryPlan"]
ER["EvidenceRecord"]
PR["ProvenanceRecord"]
EM["EvaluationMetric"]
LI["LearningInsight"]

AX -->|"produces 1"| AO
AO -->|"triggers 0..*"| ADA
ADA -->|"contributesTo 0..*"| RP
AO -->|"evidencedBy 1..*"| ER
ER -->|"hasProvenance 1"| PR
AO -->|"evaluatedBy 1..*"| EM
EM -->|"generates 0..*"| LI
end

H -->|"drives"| F
F -->|"updates / informs"| C
D -->|"provides capability evidence"| C
U -->|"provides service evidence"| C

DC -->|"participatesIn"| CDD
US -->|"participatesIn"| CDD
CDD -->|"representedIn"| DM

DR -->|"authorises"| AX
DR -->|"justifiedBy"| ER
LI -. "feedback updates knowledge" .-> KB

WF -. "reasoning / inference flow" .-> C
OS -. "observation" .-> OB
SOS -. "observation" .-> OB

classDef blue fill:#eef6ff,stroke:#2563eb,stroke-width:1.5px;
classDef green fill:#effbf2,stroke:#2e8b57,stroke-width:1.5px;
classDef purple fill:#f5efff,stroke:#7c3aed,stroke-width:1.5px;
classDef orange fill:#fff5e8,stroke:#d97706,stroke-width:1.5px;
classDef teal fill:#ecfeff,stroke:#0f8b8d,stroke-width:1.5px;
classDef gold fill:#fff9db,stroke:#b58900,stroke-width:1.5px;
classDef darkgreen fill:#eef8ee,stroke:#287a3d,stroke-width:1.5px;

class WF,WO,EWE,AA,ES,EU blue;
class FM,IA,PI,RL,CA,AE green;
class DC,CC,CW,OS,SR,IC,CT orange;
class US,SC,SOS,SD,SCT,PG,SDEP,SP,SLA teal;
class CDD,DCON,DEVID,PP gold;
class OB,KB,DM,IR,DE,DR,SCEN,EXP purple;
class AX,AO,ADA,RP,ER,PR,EM,LI darkgreen;
```

---

# Figure 4.6 — Cognitive Reasoning & Decision Sequence in the Cognitive Urban Twin

```mermaid
sequenceDiagram
autonumber

participant HC as 1. Hazard & Context
participant FI as 2. Forecast & Impact Assessment
participant DC as 4. Data Centre Capability
participant US as 5. Urban Service Capability
participant XD as 6. Cross-Domain Dependency
participant CT as 3. Cognitive Twin Knowledge Core
participant DR as 7. Decision, Feedback & Resilience
participant OUT as Outcome / Stakeholders & Systems

rect rgb(238,246,255)
Note over HC,CT: 1. SENSE & OBSERVE — Collect environmental data and detect hazard events
HC->>CT: WeatherObservation
HC->>CT: ExtremeWeatherEvent
HC->>CT: EventSeverity + AffectedArea
CT->>CT: Integrate observations into knowledge base
end

rect rgb(239,251,242)
Note over HC,CT: 2. PREDICT & ASSESS — Generate forecasts and assess potential impacts and risks
HC->>FI: WeatherForecast
FI->>FI: Run ForecastModel
FI->>FI: Generate ImpactAssessment
FI->>CT: PredictedImpact + RiskLevel
FI->>CT: ConfidenceAssessment + AssessmentEvidence
CT->>CT: Update scenario and impact knowledge
end

rect rgb(255,245,232)
Note over DC,US: 3. CHECK CAPABILITIES — Assess operational state and capability of critical infrastructure
DC->>CT: DataCentre OperationalState
DC->>CT: ComputationalCapability
DC->>CT: CapacityConstraint
US->>CT: ServiceOperationalState
US->>CT: ServiceCapability
US->>CT: ServiceDemand + ServiceCriticality
end

rect rgb(236,254,255)
Note over DC,CT: 4. ANALYSE DEPENDENCIES — Evaluate cross-domain dependencies and propagate impacts
CT->>XD: Evaluate relevant CrossDomainDependency
DC->>XD: Data-centre dependency evidence
US->>XD: Urban-service dependency evidence
XD->>XD: Evaluate DependencyCondition
XD->>XD: Determine PropagationPath
XD->>CT: DependencyCriticality + DependencyEvidence
CT->>CT: Update DependencyModel
end

rect rgb(245,239,255)
Note over CT,DR: 5. REASON & RECOMMEND — Cognitive reasoning and evidence-based recommendations
CT->>CT: Execute ImpactReasoning
CT->>CT: Evaluate Scenario
CT->>CT: Compare feasible responses
CT->>DR: DecisionRecommendation
CT->>DR: Explanation + confidence + evidence
end

rect rgb(238,248,238)
Note over DR,OUT: 6. DECIDE & ACT — Execute decisions and adapt operations
DR->>OUT: Authorise ActionExecution
OUT->>DC: Apply data-centre action
OUT->>US: Apply urban-service action
OUT->>DR: ActionOutcome
end

rect rgb(238,248,238)
Note over DR,CT: 7. FEEDBACK & LEARN — Capture outcomes and update knowledge for continuous learning
DR->>DR: Evaluate outcome metrics
DR->>CT: EvidenceRecord + ProvenanceRecord
DR->>CT: EvaluationMetric + LearningInsight
CT->>CT: Update knowledge, dependencies and models
CT-->>FI: Refine assessment assumptions
CT-->>XD: Refine dependency knowledge
end
```

---

# Figure 4.7 — Canonical Class Overview of the Cognitive Urban Twin Ontology

```mermaid
flowchart LR

subgraph M1["1. HAZARD & CONTEXT<br/>Environmental conditions and external drivers"]
direction TB
A1["WeatherForecast<br/>(Prediction)"]
A2["WeatherObservation<br/>(Observation)"]
A3["ExtremeWeatherEvent<br/>(Event)"]
A4["EnvironmentalCondition<br/>(Condition)"]
A5["Area<br/>(SpatialEntity)"]
A6["SeverityLevel<br/>(Severity)"]
A7["UncertaintyEstimate<br/>(Metadata)"]
end

subgraph M2["2. FORECAST & IMPACT ASSESSMENT<br/>Models, predictions and impact assessment"]
direction TB
B1["ForecastModel<br/>(Model)"]
B2["ImpactAssessment<br/>(Assessment)"]
B3["PredictedImpact<br/>(Impact)"]
B4["RiskLevel<br/>(Risk)"]
B5["ConfidenceAssessment<br/>(Confidence)"]
B6["AssessmentEvidence<br/>(Evidence)"]
end

subgraph M3["3. COGNITIVE TWIN KNOWLEDGE CORE<br/>Cognitive reasoning and knowledge management"]
direction TB
C1["ObservationBase<br/>(KnowledgeResource)"]
C2["KnowledgeBase<br/>(KnowledgeResource)"]
C3["DependencyModel<br/>(Model)"]
C4["ImpactReasoning<br/>(Reasoning)"]
C5["DecisionEngine<br/>(ReasoningEngine)"]
C6["DecisionRecommendation<br/>(Recommendation)"]
C7["Scenario<br/>(Scenario)"]
C8["Explanation<br/>(Explanation)"]
end

subgraph M4["4. DATA CENTRE CAPABILITY<br/>Assets, capabilities and operational state"]
direction TB
D1["DataCentre<br/>(Asset)"]
D2["ComputationalCapability<br/>(Capability)"]
D3["ComputationalWorkload<br/>(Workload)"]
D4["OperationalState<br/>(State)"]
D5["SupportingResource<br/>(Resource)"]
D6["InfrastructureComponent<br/>(Component)"]
D7["CapacityConstraint<br/>(Constraint)"]
end

subgraph M5["5. URBAN SERVICE CAPABILITY<br/>Critical services, demand and operational state"]
direction TB
E1["UrbanService<br/>(Service)"]
E2["ServiceCapability<br/>(Capability)"]
E3["ServiceOperationalState<br/>(State)"]
E4["ServiceDemand<br/>(Demand)"]
E5["ServiceCriticality<br/>(Criticality)"]
E6["PopulationGroup<br/>(Population)"]
E7["ServiceDependency<br/>(Dependency)"]
E8["ServiceProvider<br/>(Organisation)"]
E9["ServiceSLA<br/>(Agreement)"]
end

subgraph M6["6. CROSS-DOMAIN DEPENDENCY<br/>Interdependencies and propagation"]
direction TB
F1["CrossDomainDependency<br/>(Dependency)"]
F2["DependencyType<br/>(Classification)"]
F3["DependencyDirection<br/>(Direction)"]
F4["DependencyCriticality<br/>(Criticality)"]
F5["DependencyCondition<br/>(Condition)"]
F6["DependencyEvidence<br/>(Evidence)"]
F7["PropagationPath<br/>(Path)"]
end

subgraph M7["7. DECISION, FEEDBACK & RESILIENCE<br/>Actions, outcomes, provenance and learning"]
direction TB
G1["DecisionRecommendation<br/>(Recommendation)"]
G2["ActionExecution<br/>(Action)"]
G3["ActionOutcome<br/>(Outcome)"]
G4["AdaptationAction<br/>(Action)"]
G5["RecoveryPlan<br/>(Plan)"]
G6["EvidenceRecord<br/>(Evidence)"]
G7["ProvenanceRecord<br/>(Provenance)"]
G8["EvaluationMetric<br/>(Metric)"]
G9["LearningInsight<br/>(Learning)"]
end

M1 --> M2
M2 --> M3
M4 --> M3
M5 --> M3
M4 --> M6
M5 --> M6
M6 --> M3
M3 --> M7
M7 -.-> M3

classDef blue fill:#eef6ff,stroke:#2563eb,stroke-width:1.5px;
classDef green fill:#effbf2,stroke:#2e8b57,stroke-width:1.5px;
classDef purple fill:#f5efff,stroke:#7c3aed,stroke-width:1.5px;
classDef orange fill:#fff5e8,stroke:#d97706,stroke-width:1.5px;
classDef teal fill:#ecfeff,stroke:#0f8b8d,stroke-width:1.5px;
classDef gold fill:#fff9db,stroke:#b58900,stroke-width:1.5px;
classDef darkgreen fill:#eef8ee,stroke:#287a3d,stroke-width:1.5px;

class A1,A2,A3,A4,A5,A6,A7 blue;
class B1,B2,B3,B4,B5,B6 green;
class C1,C2,C3,C4,C5,C6,C7,C8 purple;
class D1,D2,D3,D4,D5,D6,D7 orange;
class E1,E2,E3,E4,E5,E6,E7,E8,E9 teal;
class F1,F2,F3,F4,F5,F6,F7 gold;
class G1,G2,G3,G4,G5,G6,G7,G8,G9 darkgreen;
```

---

# Figure 4.8 — Ontology Maturity Model for the Cognitive Urban Twin

```mermaid
flowchart LR

L0["0. INITIAL<br/>Ad-hoc & Isolated<br/><br/><b>Ontology</b>: Fragmented<br/>Local vocabularies; implicit semantics<br/><br/><b>Data</b>: Siloed<br/>Manual mapping; limited sharing<br/><br/><b>Reasoning</b>: Descriptive<br/>Human interpretation<br/><br/><b>Adaptation</b>: None / manual<br/><br/><b>Interoperability</b>: Point-to-point<br/><br/><b>Governance</b>: Informal<br/><br/><b>Value</b>: Local visibility"]

L1["1. FOUNDATIONAL<br/>Defined & Documented<br/><br/><b>Ontology</b>: Defined<br/>Core concepts; basic hierarchy; documented scope<br/><br/><b>Data</b>: Connected<br/>Standard models; ETL/ELT; basic interoperability<br/><br/><b>Reasoning</b>: Rule-aware<br/>Basic queries and thresholds<br/><br/><b>Adaptation</b>: Procedural<br/><br/><b>Interoperability</b>: Standardised<br/><br/><b>Governance</b>: Defined ownership<br/><br/><b>Value</b>: Shared understanding"]

L2["2. INTEGRATED<br/>Linked & Structured<br/><br/><b>Ontology</b>: Structured<br/>Modular ontology; richer entities; controlled vocabularies<br/><br/><b>Data</b>: Integrated<br/>Linked data; cross-domain mappings; consistent identifiers<br/><br/><b>Reasoning</b>: Analytical<br/>Cross-domain queries and dependency analysis<br/><br/><b>Adaptation</b>: Coordinated<br/><br/><b>Interoperability</b>: Semantic linking<br/><br/><b>Governance</b>: Managed lifecycle<br/><br/><b>Value</b>: Cross-domain insight"]

L3["3. COGNITIVE<br/>Reasoning & Predictive<br/><br/><b>Ontology</b>: Semantic<br/>Rich relationships; constraints; contextual semantics<br/><br/><b>Data</b>: Federated<br/>Semantic federation; real-time streams; provenance<br/><br/><b>Reasoning</b>: Predictive<br/>Inference, impact reasoning and explainable recommendations<br/><br/><b>Adaptation</b>: Decision-supported<br/><br/><b>Interoperability</b>: Context-aware<br/><br/><b>Governance</b>: Validated and auditable<br/><br/><b>Value</b>: Predictive decision support"]

L4["4. ADAPTIVE<br/>Self-Learning & Autonomous<br/><br/><b>Ontology</b>: Adaptive<br/>Dynamic context models; ontology evolution; feedback incorporation<br/><br/><b>Data</b>: Continuous<br/>Streaming updates; automated semantic alignment<br/><br/><b>Reasoning</b>: Adaptive<br/>Learning-informed reasoning and dynamic optimisation<br/><br/><b>Adaptation</b>: Closed-loop<br/><br/><b>Interoperability</b>: Dynamic<br/><br/><b>Governance</b>: Continuous assurance<br/><br/><b>Value</b>: Resilience and autonomous adaptation"]

L5["5. TRANSFORMATIVE<br/>Socio-Technical Impact<br/><br/><b>Ontology</b>: Transformative<br/>Self-evolving ontology; socio-technical alignment; anticipatory semantics<br/><br/><b>Data</b>: Ecosystem-wide<br/>Trusted multi-domain knowledge ecosystem<br/><br/><b>Reasoning</b>: Anticipatory<br/>System-wide optimisation and foresight<br/><br/><b>Adaptation</b>: Orchestrated<br/><br/><b>Interoperability</b>: Ecosystem semantic alignment<br/><br/><b>Governance</b>: Federated stewardship<br/><br/><b>Value</b>: Transformative urban outcomes"]

L0 --> L1 --> L2 --> L3 --> L4 --> L5

subgraph EN["CROSS-CUTTING ENABLERS"]
direction LR
E1["Standards & reusable ontologies"]
E2["Persistent identifiers"]
E3["Provenance"]
E4["SHACL / validation"]
E5["Governance & stewardship"]
E6["Security & access control"]
E7["Human oversight & explainability"]
end

EN -. supports .-> L1
EN -. supports .-> L2
EN -. supports .-> L3
EN -. supports .-> L4
EN -. supports .-> L5

classDef l0 fill:#f3f4f6,stroke:#6b7280,stroke-width:1.5px;
classDef l1 fill:#eef6ff,stroke:#2563eb,stroke-width:1.5px;
classDef l2 fill:#effbf2,stroke:#2e8b57,stroke-width:1.5px;
classDef l3 fill:#f5efff,stroke:#7c3aed,stroke-width:1.5px;
classDef l4 fill:#fff5e8,stroke:#d97706,stroke-width:1.5px;
classDef l5 fill:#eef2ff,stroke:#1e3a8a,stroke-width:1.5px;
classDef en fill:#ffffff,stroke:#6b7280,stroke-width:1px;

class L0 l0;
class L1 l1;
class L2 l2;
class L3 l3;
class L4 l4;
class L5 l5;
class E1,E2,E3,E4,E5,E6,E7 en;
```

---

# Supplementary Figure S1 — Ontology Package Structure

```mermaid
flowchart TB
ROOT["cut: Cognitive Urban Twin Ontology"]

ROOT --> HC["cut-hc:<br/>Hazard & Context"]
ROOT --> FI["cut-fi:<br/>Forecast & Impact Assessment"]
ROOT --> CORE["cut-core:<br/>Cognitive Twin Knowledge Core"]
ROOT --> DC["cut-dc:<br/>Data Centre Capability"]
ROOT --> US["cut-us:<br/>Urban Service Capability"]
ROOT --> XD["cut-xd:<br/>Cross-Domain Dependency"]
ROOT --> DR["cut-dr:<br/>Decision, Feedback & Resilience"]

CORE --> COMMON["cut-common:<br/>Shared upper concepts,<br/>controlled vocabularies and identifiers"]

HC -. imports .-> COMMON
FI -. imports .-> COMMON
DC -. imports .-> COMMON
US -. imports .-> COMMON
XD -. imports .-> COMMON
DR -. imports .-> COMMON

FI -. imports .-> HC
CORE -. imports .-> FI
CORE -. imports .-> XD
XD -. imports .-> DC
XD -. imports .-> US
DR -. imports .-> CORE
```

---

# Supplementary Figure S2 — Semantic Standards Alignment

```mermaid
flowchart LR
CUT["Cognitive Urban Twin Ontology"]

SOSA["SOSA / SSN<br/>Observations, sensors,<br/>features of interest"]
PROV["PROV-O<br/>Provenance, activities,<br/>agents and entities"]
GEO["GeoSPARQL<br/>Spatial entities,<br/>geometry and topology"]
TIME["OWL-Time<br/>Temporal entities,<br/>intervals and instants"]
QUDT["QUDT<br/>Quantities, units<br/>and measurements"]
SHACL["SHACL<br/>Validation and<br/>closed-world constraints"]
BRICK["Brick / building semantics<br/>Building assets and<br/>operational concepts"]

SOSA --> CUT
PROV --> CUT
GEO --> CUT
TIME --> CUT
QUDT --> CUT
SHACL --> CUT
BRICK --> CUT
```

---

# Supplementary Figure S3 — Reasoning and Validation Pipeline

```mermaid
flowchart LR
SRC["Observations & Domain Data"]
MAP["Semantic Mapping"]
KG["Knowledge Graph"]
OWL["OWL / Description-Logic Inference"]
RULES["Domain / Decision Rules"]
SHACL["SHACL Validation"]
CQ["Competency-Question Tests"]
DEC["Decision Engine"]
REC["Decision Recommendation"]
EXP["Explanation & Evidence"]
ACT["Action"]
OUT["Outcome"]
LEARN["Feedback / Learning"]

SRC --> MAP --> KG
KG --> OWL
KG --> RULES
OWL --> SHACL
RULES --> SHACL
SHACL --> CQ
CQ --> DEC
DEC --> REC --> EXP --> ACT --> OUT --> LEARN
LEARN -. updates .-> KG
```

---

# Supplementary Figure S4 — Decision Traceability Chain

```mermaid
flowchart TB
D["Decision / Recommendation"]
E["Evidence"]
I["Inference / Rule"]
CQ["Competency Question"]
KG["Knowledge Graph State"]
O["Observation / Forecast"]
P["Provenance"]
V["Validation Result"]
A["Action"]
OUT["Outcome / Evaluation Metric"]

D -->|"justifiedBy"| E
E -->|"derivedFrom"| I
I -->|"answers"| CQ
I -->|"queries"| KG
KG -->|"contains"| O
O -->|"hasProvenance"| P
E -->|"validatedBy"| V
D -->|"authorises"| A
A -->|"produces"| OUT
OUT -. "feedback" .-> KG
```

---

# Supplementary Figure S5 — Semantic Decision Traceability

```mermaid
flowchart LR
DEC["Decision"]
CQ["Competency Question"]
CLS["Required Ontology Classes"]
REL["Required Relationships"]
RULE["Reasoning Rule"]
EVID["Required Evidence"]
CONF["Confidence"]
VAL["Validation"]
ACT["Decision Action"]

DEC --> CQ --> CLS --> REL --> RULE --> EVID --> CONF --> VAL --> ACT
```

---

# Supplementary Figure S6 — Knowledge Lifecycle

```mermaid
flowchart LR
ACQ["Acquire"]
SEM["Semantically Integrate"]
VAL["Validate"]
STORE["Store / Govern"]
REASON["Reason"]
DECIDE["Recommend / Decide"]
ACT["Act"]
OBS["Observe Outcome"]
LEARN["Learn"]
EVOLVE["Update Knowledge / Ontology"]

ACQ --> SEM --> VAL --> STORE --> REASON --> DECIDE --> ACT --> OBS --> LEARN --> EVOLVE
EVOLVE --> STORE
EVOLVE -. "new requirements" .-> SEM
```

---

## Notes for publication use

1. Figures 4.1–4.8 use the same module numbering throughout.
2. Figure 4.4 is the canonical integrated class model.
3. Figure 4.5 should be used when the manuscript discusses explicit semantic object properties and cardinalities.
4. Figure 4.6 expresses the operational reasoning lifecycle rather than the static ontology structure.
5. Figure 4.7 is intentionally simpler than Figure 4.4 and should be used as the reader-facing class summary.
6. Figure 4.8 describes maturity of the ontology-enabled Cognitive Urban Twin, not generic digital-twin maturity.
7. The future OWL implementation should preserve the conceptual identities and relationships defined here while reusing established standards such as SOSA/SSN, PROV-O, GeoSPARQL, OWL-Time and QUDT where appropriate.
8. SHACL should be treated as the validation/assurance layer rather than as an inference language.
9. Mermaid is the publication-source representation; the OWL ontology should ultimately become the machine-executable semantic source of truth.
