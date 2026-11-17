# GitaLaw Ontology Suite

A modular, seven-layer OWL/RDF ontology framework modeling the philosophical, psychological, ethical, and situational knowledge structures of the **Bhagavad Gita**.

## Ontology Architecture

The knowledge graph consists of **63,950 explicit RDF triples** serialized in Turtle (`.ttl`) format across seven interconnected modules:

| Module | File | Domain & Scope |
| :--- | :--- | :--- |
| **BGSO** | `1-BGSO_Complete.ttl` | **Source Layer:** Chapters and verse nodes covering all 700 verses of the Bhagavad Gita. |
| **BGLO** | `2-BGLO_Complete.ttl` | **Law Layer:** 547 fine-grained philosophical laws (`CHx_FLy`) and canonical law groupings. |
| **BGMSO** | `3-BGMSO_Complete.ttl` | **Mental State Layer:** Psychological and cognitive states affected by philosophical laws. |
| **BGGO** | `4-BGGO_Complete.ttl` | **Guna Layer:** Dispositional traits (*Sattva*, *Rajas*, *Tamas*) associated with laws. |
| **BGEVO** | `5-BGEVO_Complete.ttl` | **Ethical Value Layer:** Virtues and vices linked to behavioral and philosophical principles. |
| **BGSJO** | `6-BGSJO_Complete.ttl` | **Spiritual Journey Layer:** Transitions between current and next spiritual stages. |
| **BGLRO** | `7-BGLRO_Complete.ttl` | **Life Resolution Layer:** Real-world life situations mapped to applicable laws and verses. |

## Quick Start (GraphDB / Protégé)

1. **Create a Repository:** In Ontotext GraphDB (or Apache Jena Fuseki), create a new repository with **Ruleset = No inference (Empty)** to preserve exact explicit triple counts (`63,950` triples).
2. **Import Ontologies:** Load all seven `.ttl` files from the `ontologies/` directory into the default graph.
3. **Run Competency Questions:** Execute the SPARQL queries in `queries/competency_questions.rq` to verify cross-layer traversal.

### Sample SPARQL Query (Law → Mental States)
```sparql
PREFIX bglo: [http://www.semanticweb.org/bglo#](http://www.semanticweb.org/bglo#)
PREFIX rdfs: [http://www.w3.org/2000/01/rdf-schema#](http://www.w3.org/2000/01/rdf-schema#)

SELECT ?ms ?msName WHERE {
  bglo:CH1_FL1 bglo:affectsMentalState ?ms .
  ?ms rdfs:label ?msName .
}
