# CR_CDT

**Cognitive Digital Twin Architecture for Climate-Resilient Smart Cities Operations**

This repository contains Mermaid diagrams and Protégé-compatible RDF/OWL files for the proposed ontological model accompanying a book chapter of the same title. The model connects extreme weather, data centre operations, computational workloads, electricity-grid constraints, and critical urban services within a federated Cognitive Digital Twin (CDT) architecture.

## Research context

Critical urban services depend on data centres for computation, storage, communication, and timely decisions. Extreme weather can affect the data centre and the services that depend on it at the same time. The proposed CDT links these domains so that operators can trace dependencies, assess potential service impacts, consider operational flexibility and workload priorities, explain recommended interventions, and use observed outcomes to update subsequent assessments.

The chapter describes a systematic literature review informing the architecture and ontology, a UML-based conceptualisation formalised as RDF/OWL, competency-question-driven SPARQL and reasoning/constraint checks, and structured expert feedback on the federated architecture. The files here document the conceptual model and a bounded ontology demonstrator; they are not a deployed city operations system.

## Start here

| Resource | Purpose |
| --- | --- |
| [Complete Mermaid figure pack](Mermaid/Cognitive_Urban_Twin_Complete_Mermaid_Source_v1.0.md) | Architecture and related chapter diagrams (Figures 4.1–4.8) as Mermaid source. |
| [Integrated conceptual class diagram](Mermaid/CDT_class_diagram_v2.mmd) | UML-style view of the environmental, infrastructure, service, energy, analytics, decision and action domains. |
| [Conceptual ontology diagram](Mermaid/Cognitive_Urban_Twin_Conceptual_Ontology_Mermaid_v2.txt) | More detailed cross-domain conceptual ontology in Mermaid syntax. |
| [Reference ontology v0.3.2](Protege/cognitive-urban-twin-v0.3.2-validation-clean.ttl) | Main RDF/OWL Turtle file, including the heatwave exemplar; begin here for ontology inspection and queries. |
| [Competency-question SPARQL queries](Protege/cognitive-urban-twin-cq-sparql-v0.3.1/) | 26 executable queries covering hazard, dependencies, impact, evidence, decisions, actions and feedback. |
| [Validation report](Protege/validation-clean-baseline/Cognitive_Urban_Twin_v0.3.2_Validation_Report.md) | Recorded results and scope of the v0.3.2 checks. |
| [Closed-loop decision trace](Protege/validation-clean-baseline/Cognitive_Urban_Twin_Closed_Loop_Decision_Trace_v0.3.2_PUBLICATION.svg) | Publication-oriented view of the heatwave reasoning path. The [Mermaid source](Protege/validation-clean-baseline/Cognitive_Urban_Twin_Closed_Loop_Decision_Trace_v0.3.2_PUBLICATION.mmd) is also available. |

## Repository layout

- `Mermaid/` — source diagrams for the architecture and conceptual models. GitHub renders Mermaid fences in the figure-pack Markdown; standalone `.mmd` and Mermaid-formatted `.txt` files can be opened in a Mermaid editor.
- `Protege/` — the v0.3.2 reference ontology, the 26 v0.3.1 SPARQL query files, and reduced WebVOWL presentation profiles. The `webvowl-profile` and `webvowl-decision-path` Turtle files are for visualisation; they are not substitutes for the reference ontology.
- `Protege/validation-clean-baseline/` — the v0.3.2 report, trace matrix, narrative scaffold, and source/export versions of the closed-loop figure.
- `Protege/old-baseline/` — earlier ontology, scenario, shapes, and verification artefacts kept for version history. Use the v0.3.2 file above as the current reference.

The version numbers describe individual artefacts: the current ontology is **v0.3.2**, while the executable query set is named **v0.3.1** and was included in the recorded v0.3.2 regression.

## Explore the ontology

1. Open [`cognitive-urban-twin-v0.3.2-validation-clean.ttl`](Protege/cognitive-urban-twin-v0.3.2-validation-clean.ttl) in Protégé or another RDF/OWL tool that supports Turtle.
2. Inspect the classes and relations linking hazards, data centres, grids, dependent services, impact forecasts, decision evidence, candidate actions, recommendations, and outcome observations.
3. Load the same Turtle file into an RDF store or SPARQL-capable environment and run queries from [the CQ directory](Protege/cognitive-urban-twin-cq-sparql-v0.3.1/). For an end-to-end example, start with [`CQ26_end_to_end_trace.rq`](Protege/cognitive-urban-twin-cq-sparql-v0.3.1/CQ26_end_to_end_trace.rq). The queries use the ontology's `https://example.org/cognitive-urban-twin#` namespace.
4. Compare results with the [CQ verification specification](Protege/old-baseline/Decision%20Reasoning/Cognitive_Urban_Twin_CQ_to_SPARQL_Verification_v0.3.1.md) and the [v0.3.2 validation report](Protege/validation-clean-baseline/Cognitive_Urban_Twin_v0.3.2_Validation_Report.md). The [narrative scaffold](Protege/validation-clean-baseline/Cognitive_Urban_Twin_Narrative_Scaffold.md) explains the demonstrator and its limits.

The heatwave exemplar traces a hazard affecting a data centre, a grid constraint and dependent urban services. Evidence and an impact forecast inform a decision context; the twin recommends deferring an elastic load and dispatching battery storage. Outcomes return to the observation base and prediction/scenario engine for reassessment. This is a modelled decision path, not evidence that those actions were executed in a real city.

## Validation and scope

The repository's [v0.3.2 report](Protege/validation-clean-baseline/Cognitive_Urban_Twin_v0.3.2_Validation_Report.md) records ontology and shapes syntax passes, 11/11 defined constraint checks without violations, 12/12 reasoning regression checks, and expected results for all 26 competency-question queries against the exemplar. These are reported results for the included, bounded scenario; they do not establish city-scale operational performance or independent reproduction. The accompanying narrative identifies independent standards-engine SHACL validation and fuller OWL reasoner consistency checks as further work.

The conceptual diagrams cover more possible hazards, resources, and response types than the heatwave exemplar verifies. For formal analysis, use the reference ontology and its actual assertions rather than treating every conceptual diagram element or visualisation profile as an implemented and tested feature.
