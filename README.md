# FHIRconnect Schema Explorer 🩺⚡

> An interactive visual documentation explorer and IDE-ready enriched JSON Schemas for **FHIRconnect v1.0.0** (openEHR ⇄ HL7® FHIR® bidirectional mapping engine).

---

## 📌 Overview

**FHIRconnect** bridges clinical data models between **openEHR** (Archetypes & Templates) and **HL7® FHIR® R4** (Profiles & StructureDefinitions). Writing mapping definitions requires adhering to two key JSON schemas:
1. **Model Mapping Schema (`model-mapping.schema.json`)**: Configures fine-grained clinical data element transformations, plugin types (`QUANTITY`, `CODEABLECONCEPT`, `PROPORTION`, etc.), conditions, unwinding hierarchies, and slot delegations.
2. **Contextual Mapping Schema (`contextual-mapping.schema.json`)**: Configures root container composition, contextual header metadata (subject, encounter, start time, composer), and bundle-to-composition bindings.

This repository provides:
- 🌐 **Interactive Single-Page Visual Explorer (`index.html`)**: Searchable, hierarchical documentation for both schemas with light/dark themes, YAML code snippets, and constraint tables.
- 💡 **IDE-Enriched JSON Schemas**: Complete schemas with detailed human-readable `"description"` attributes for instant hover docs and autocomplete in VS Code, Cursor, and JetBrains IDEs.
- 🔍 **Schema Discrepancy & Validation Notes**: Documented edge cases and structural findings in the upstream v1.0.0 schemas.

---

## 🚀 Live Demo

You can host this directly on GitHub Pages!

👉 **[Try the Live Explorer](https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/)** *(Replace with your GitHub repository Pages link)*

---

## ✨ Features of the Visual Explorer

- **Unified Explorer:** Switch seamlessly between **Model Mapping** and **Context Mapping** specifications, plus an **Architecture Overview** and **About & Disclaimers**.
- **Interactive Tree Browser:** Drill down from top-level properties into nested structures (`mappings[]`, `preprocessor`, `hierarchy`, `conditions`).
- **Instant Search:** Press <kbd>/</kbd> to filter elements by name, path, enum value, or descriptive text.
- **Detailed Property Inspector:**
  - Data types, format restrictions, and regex patterns.
  - Required vs. optional flags.
  - Allowed enum options with clinical and mapping explanations.
  - Ready-to-copy YAML examples.
  - Original JSON Schema fragment preview.
- **Light / Dark Mode:** Respects system color scheme by default, with a manual toggle stored in `localStorage`.
- **Zero Dependencies:** Pure vanilla HTML5, CSS, and modern JavaScript. No node build steps, bundlers, or CDNs required—works fully offline.

---

## 🛠️ Quick Start
1. Running Locally
Simply open index.html in any modern web browser

---

## ⚠️ Notes & Schema Observations
During the analysis and documentation of the FHIRconnect v1.0.0 draft schemas, the following nuances and potential schema discrepancies were identified:

Hierarchy Split (preprocessor.hierarchy.split.openehr): In model-mapping.schema.json, the openehr split definition is placed outside the properties block of split, preventing some validators from enforcing its structure.

Manual Mappings Array (manual / manual[].openehr): Defined as type: "array", but child constraints are specified under properties rather than items, meaning array elements may bypass strict JSON-schema validation.

Preprocessor Condition Symmetry: openehrCondition enforces a oneOf between targetAttribute and targetAttributes, whereas fhirCondition permits either or neither.

Context Schema Identifiers: contextual-mapping.schema.json does not strictly require profile.url or template.id in its required arrays.

(Refer to the in-app "About & Analysis" section for further details.)

---

## 📚 Upstream Sources & References
FHIRconnect Specification: https://sevkohler.github.io/FHIRconnect-spec/

Upstream GitHub Repository: https://github.com/SevKohler/FHIRconnect-spec

Model Mapping Schema Source: https://github.com/SevKohler/FHIRconnect-spec/blob/main/build/site/FHIRconnect/v1.0.0/_attachments/model-mapping.schema.json

Contextual Mapping Schema Source: https://github.com/SevKohler/FHIRconnect-spec/blob/main/build/site/FHIRconnect/v1.0.0/_attachments/contextual-mapping.schema.json

openEHR Specifications: https://specifications.openehr.org/

HL7 FHIR R4: https://www.hl7.org/fhir/R4/

## ⚖️ Disclaimer & Copyright
Schema & Specification Rights: The underlying FHIRconnect specification, conceptual design, and original schemas are created and maintained by Severin Köhler and contributors to the GitHub - SevKohler/FHIRconnect-spec project.

Visual Explorer & Descriptions: © 2026 Martin Andreas Koch for CatSalut. 

Disclaimer: This project is an independent community resource and is not officially affiliated with or endorsed by openEHR, HL7, or the FHIRconnect project. The tool and schemas are provided "AS IS", without warranty of any kind. Users are solely responsible for verifying mappings against official specifications prior to production deployment.

## 📄 License
This repository is licensed under Apache 2.0.