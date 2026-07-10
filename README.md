# Pistoia-Alliance-Ontologies
Public access repository to Pistoia Alliance Ontologies

## [IDMP-O ontology](https://github.com/Pistoia-Alliance-Inc/Pistoia-Alliance-Ontologies/tree/main)

<!-- migrate-releases:release-notes:begin -->

## Release notes

<details>
<summary>IDMP Ontology Release 1.7.0 (master_v1.7.0) - 2026-07-10</summary>

# IDMP Ontology Release 1.7.0

The 1.7.0 release of IDMP-O (Identification of Medicinal Products Ontology) includes development efforts accomplished in the second quarter of 2026. 

The main focus of the release is new ontology content around packaging. 
Pack size is represented with structured values, following the EMA/ISO guidance that the pack size is the total number of units contained in the manufactured item or package item, expressed per unit of presentation. 
Composite packs are expressed as one pack-size term per component, and combination products such as powder-and-solvent packs requiring reconstitution are detected through the combined pharmaceutical dose form. 
A SHACL rule derives pack sizes from per-constituent quantities, and competency questions verify that asserted pack sizes match the aggregation. 
We have added new units of presentation (vial, capsule, syringe) to the UCUM vocabulary with mappings to the EMA SPOR RMS Units of Presentation, as well as new convenience properties.

In addition, the ontology sources were migrated from RDF/XML to Turtle. The migration from RDF/XML to TTL was done while keeping all triples i.e., the converted ontologies contain the identical RDF content as before.

### Content modifications

- Added the class idmp-mprd:PackSize to the medicinal-products module (from ISO 11615). It is a subclass of cmns-qtu:ScalarQuantityValue. [[Issue IDMPO-1]](https://pistoiaalliance-jira.atlassian.net/browse/IDMPO-1)
- Added the object property idmp-mprd:hasPackSize to the medicinal-products module (from ISO 11615), relating idmp-mprd:PackagedMedicinalProduct to its pack sizes. [[Issue IDMPO-1]](https://pistoiaalliance-jira.atlassian.net/browse/IDMPO-1)
- Added the generic object property idmp-mprd:hasDerivedValue to the medicinal-products module (from ISO 11615) for quantity values computed by a system rather than asserted, used for pack sizes derived from constituent quantities. [[Issue IDMPO-1]](https://pistoiaalliance-jira.atlassian.net/browse/IDMPO-1)
- Added the individuals idmp-ucum:Vial, idmp-ucum:Capsule, and idmp-ucum:Syringe as units of presentation to the UCUM vocabulary. [[Issue IDMPO-1]](https://pistoiaalliance-jira.atlassian.net/browse/IDMPO-1)
- Added the object properties idmp-uom:isDenominatorOf and idmp-uom:isNumeratorOf to the units-of-measurement module (from ISO 11240). [[Issue IDMPO-4]](https://pistoiaalliance-jira.atlassian.net/browse/IDMPO-4)
- Added five examples EXMP/PackSizeExample-* demonstrating the pack-size pattern. [[Issue IDMPO-1]](https://pistoiaalliance-jira.atlassian.net/browse/IDMPO-1)

### Validation and test additions

- Added a SHACL shape validating every asserted pack size (exactly one decimal value, at most one unit of presentation) and SHACL-AF rules deriving pack sizes from per-constituent quantities. [[Issue IDMPO-1]](https://pistoiaalliance-jira.atlassian.net/browse/IDMPO-1)
- Added competency questions asking for the pack size of a packaged medicinal product and checking that asserted pack sizes match the aggregation from constituents. [[Issue IDMPO-1]](https://pistoiaalliance-jira.atlassian.net/browse/IDMPO-1)

### Fixes

- Changed the namespace bound to the prefix cmns-bfo in the MVF-to-BFO mapping to the canonical IRI of the MAP/MappingCommonsToBFO ontology. [[Issue IDMPO-1]](https://pistoiaalliance-jira.atlassian.net/browse/IDMPO-1)
- Added the missing rdfs:label to the property recipePrecedes. [[Issue IDMPO-12]](https://pistoiaalliance-jira.atlassian.net/browse/IDMPO-12)

### New release artifact

- The release bundle contains the merged single-file release artifact composite/IdentificationOfMedicinalProductsOntology.ttl. It combines all released modules (with maturity level Release from ISO, META, and VOCAB) under one ontology header, keeps the external foundational ontologies as owl:imports, and includes the Commons ProductsAndServices. It reproduces the structure of the composites of releases 1.2.0 to 1.6.0. [[Issue IDMPO-7]](https://pistoiaalliance-jira.atlassian.net/browse/IDMPO-7)

### Technical modifications

- Migrated every ontology, vocabulary, and example source file from RDF/XML to Turtle and updated the catalogs accordingly. The RDF content is unchanged, the conversion keeps all triples. [[Issue IDMPO-10]](https://pistoiaalliance-jira.atlassian.net/browse/IDMPO-10)
- The release bundle includes quality reports (hygiene, SHACL, consistency) under hygiene/. [[Issue IDMPO-7]](https://pistoiaalliance-jira.atlassian.net/browse/IDMPO-7)
- The engineering infrastructure of the repository was changed. The previous build workflow under etc/ was replaced by a self-contained build pipeline (build/idmp_build) stored next to the ontology artifacts and executed in GitHub. [[Issue IDMPO-10]](https://pistoiaalliance-jira.atlassian.net/browse/IDMPO-10)

**No ontologies were removed. All terms published in release 1.6.0 remain present.**

### Delivered Change Requests (JIRA Tickets)

Complete list of the tickets delivered in this release

- [[Issue IDMPO-1]](https://pistoiaalliance-jira.atlassian.net/browse/IDMPO-1) Add structured pack size (model, units of presentation with SPOR mappings, examples, SHACL derivation, and competency questions) by @hk-accurids
- [[Issue IDMPO-3]](https://pistoiaalliance-jira.atlassian.net/browse/IDMPO-3) Create initial set of IDMP-O tests to be run before the next release by @hk-accurids 
- [[Issue IDMPO-4]](https://pistoiaalliance-jira.atlassian.net/browse/IDMPO-4) Add inverse properties isDenominatorOf and isNumeratorOf by @hk-accurids 
- [[Issue IDMPO-5]](https://pistoiaalliance-jira.atlassian.net/browse/IDMPO-5) Add direct properties between pharmaceutical product and manufactured item by @hk-accurids. Delivered and subsequently REVERTED after review feedback, not part of release 1.7.0.
- [[Issue IDMPO-7]](https://pistoiaalliance-jira.atlassian.net/browse/IDMPO-7) Generate the merged publication artifact IdentificationOfMedicinalProductsOntology.ttl as part of the release bundle by @hk-accurids 
- [[Issue IDMPO-10]](https://pistoiaalliance-jira.atlassian.net/browse/IDMPO-10) Migrate the repository to Turtle and introduce the release pipeline with reporting by @hk-accurids 
- [[Issue IDMPO-11]](https://pistoiaalliance-jira.atlassian.net/browse/IDMPO-11) Separate IDMP Ontology Core from Supplementary Modules by @hk-accurids 
- [[Issue IDMPO-12]](https://pistoiaalliance-jira.atlassian.net/browse/IDMPO-12) Add label to cmc:recipePrecedes by @hk-accurids

### List of changed terms

| Status | Label | Triples added | Triples deleted | Term IRI |
| --- | --- | --- | --- | :--- |
| added | IDMP-O Example, pack size, aggregated | 12 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleAggregated/ |
| added | pack size aggregated, container constituent, 4 tablets | 8 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleAggregated/ContainerConstituent-4Tablets |
| added | pack size aggregated, container constituent, 6 tablets | 8 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleAggregated/ContainerConstituent-6Tablets |
| added | pack size aggregated, manufactured item, tablets batch a | 4 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleAggregated/ManufacturedItem-TabletsBatchA |
| added | pack size aggregated, manufactured item, tablets batch b | 4 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleAggregated/ManufacturedItem-TabletsBatchB |
| added | pack size aggregated, medicinal product, tablets | 3 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleAggregated/MedicinalProduct-Tablets |
| added | pack size aggregated, package item, 10 tablets | 5 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleAggregated/PackageItem-10Tablets |
| added | pack size aggregated, packaged medicinal product, 10 tablets | 9 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleAggregated/PackagedMedicinalProduct-10Tablets |
| added | IDMP-O Example, pack size, aggregated mismatch | 12 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleAggregatedMismatch/ |
| added | pack size aggregated mismatch, container constituent, 4 tablets | 8 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleAggregatedMismatch/ContainerConstituent-4Tablets |
| added | pack size aggregated mismatch, container constituent, 6 tablets | 8 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleAggregatedMismatch/ContainerConstituent-6Tablets |
| added | pack size aggregated mismatch, manufactured item, tablets batch a | 4 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleAggregatedMismatch/ManufacturedItem-TabletsBatchA |
| added | pack size aggregated mismatch, manufactured item, tablets batch b | 4 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleAggregatedMismatch/ManufacturedItem-TabletsBatchB |
| added | pack size aggregated mismatch, medicinal product, tablets | 3 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleAggregatedMismatch/MedicinalProduct-Tablets |
| added | pack size aggregated mismatch, package item, tablets | 5 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleAggregatedMismatch/PackageItem-Mismatch |
| added | pack size aggregated mismatch, packaged medicinal product, asserted 9 tablets | 9 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleAggregatedMismatch/PackagedMedicinalProduct-Mismatch |
| added | IDMP-O Example, pack size, composite of different units | 12 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleComposite/ |
| added | pack size composite, combined pharmaceutical dose form, powder and solvent for solution for injection | 3 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleComposite/CombinedPharmaceuticalDoseForm |
| added | pack size composite, container constituent, 1 powder vial | 8 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleComposite/ContainerConstituent-PowderVial |
| added | pack size composite, container constituent, 1 solvent syringe | 8 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleComposite/ContainerConstituent-SolventSyringe |
| added | pack size composite, manufactured item, powder vial | 4 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleComposite/ManufacturedItem-PowderVial |
| added | pack size composite, manufactured item, solvent syringe | 4 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleComposite/ManufacturedItem-SolventSyringe |
| added | pack size composite, medicinal product, vial and syringe | 4 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleComposite/MedicinalProduct-Composite |
| added | pack size composite, package item, vial and syringe | 5 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleComposite/PackageItem-VialAndSyringe |
| added | pack size composite, packaged medicinal product, 1 vial and 1 syringe | 13 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleComposite/PackagedMedicinalProduct-VialAndSyringe |
| added | IDMP-O Example, pack size, liquid reconstitution | 12 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleReconstitution/ |
| added | pack size reconstitution, combined pharmaceutical dose form, powder and solvent for solution for injection | 3 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleReconstitution/CombinedPharmaceuticalDoseForm |
| added | pack size reconstitution, container constituent, 1 powder vial | 8 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleReconstitution/ContainerConstituent-PowderVial |
| added | pack size reconstitution, container constituent, 1 solvent vial | 8 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleReconstitution/ContainerConstituent-SolventVial |
| added | pack size reconstitution, manufactured item, powder vial | 4 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleReconstitution/ManufacturedItem-PowderVial |
| added | pack size reconstitution, manufactured item, solvent vial | 4 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleReconstitution/ManufacturedItem-SolventVial |
| added | pack size reconstitution, medicinal product, powder and solvent vials | 4 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleReconstitution/MedicinalProduct-Reconstitution |
| added | pack size reconstitution, package item, two vials | 5 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleReconstitution/PackageItem-TwoVials |
| added | pack size reconstitution, packaged medicinal product, 1 vial and 1 vial | 13 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleReconstitution/PackagedMedicinalProduct-TwoVials |
| added | IDMP-O Example, pack size, single count | 12 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleSingleCount/ |
| added | pack size single count, container constituent, 150 capsules | 8 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleSingleCount/ContainerConstituent-150Capsules |
| added | pack size single count, container constituent, 28 tablets | 8 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleSingleCount/ContainerConstituent-28Tablets |
| added | pack size single count, manufactured item, capsule | 4 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleSingleCount/ManufacturedItem-Capsule |
| added | pack size single count, manufactured item, tablet | 4 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleSingleCount/ManufacturedItem-Tablet |
| added | pack size single count, medicinal product, capsules | 3 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleSingleCount/MedicinalProduct-Capsules |
| added | pack size single count, medicinal product, tablets | 3 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleSingleCount/MedicinalProduct-Tablets |
| added | pack size single count, package item, 150 capsules | 4 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleSingleCount/PackageItem-150Capsules |
| added | pack size single count, package item, 28 tablets | 4 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleSingleCount/PackageItem-28Tablets |
| added | pack size single count, packaged medicinal product, 150 capsules | 9 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleSingleCount/PackagedMedicinalProduct-150Capsules |
| added | pack size single count, packaged medicinal product, 28 tablets | 9 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/PackSizeExampleSingleCount/PackagedMedicinalProduct-28Tablets |
| added | is denominator of | 13 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/ISO/ISO11240-UnitsOfMeasurement/isDenominatorOf |
| added | is numerator of | 13 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/ISO/ISO11240-UnitsOfMeasurement/isNumeratorOf |
| added | pack size | 15 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/ISO/ISO11615-MedicinalProducts/PackSize |
| added | has derived value | 5 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/ISO/ISO11615-MedicinalProducts/hasDerivedValue |
| added | has pack size | 6 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/ISO/ISO11615-MedicinalProducts/hasPackSize |
| added | capsule | 5 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/VOCAB/UnifiedCodeForUnitsOfMeasure/Capsule |
| added | syringe | 5 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/VOCAB/UnifiedCodeForUnitsOfMeasure/Syringe |
| added | vial | 5 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/VOCAB/UnifiedCodeForUnitsOfMeasure/Vial |
| modified | recipe precedes | 1 | 0 | https://spec.pistoiaalliance.org/cmc/ontology/PharmaceuticalProcess#recipePrecedes |
| modified | About IDMP Development - Reference Individuals | 5 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/AboutIDMPDev-ReferenceIndividuals/ |
| modified | terlipressin denominator in terlipressin acetate 1 mg/ml solution for injection concentration strength | 1 | 1 | https://spec.pistoiaalliance.org/idmp/ontology/EXMP/TerlipressinExample/TerlipressinDenominatorInTerlipressinAcetate1MgPerMlSolutionForInjectionConcentrationStrength |
| modified | ISO 11240 Units of Measurement (UOM) Ontology | 1 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/ISO/ISO11240-UnitsOfMeasurement/ |
| modified | Mapping MVF to BFO Ontology | 1 | 1 | https://spec.pistoiaalliance.org/idmp/ontology/MVF/MappingMVFToBFO/ |
| modified | ampoule | 1 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/VOCAB/UnifiedCodeForUnitsOfMeasure/Ampoule |
| modified | tablet | 1 | 0 | https://spec.pistoiaalliance.org/idmp/ontology/VOCAB/UnifiedCodeForUnitsOfMeasure/Tablet |

[This Excel table](https://github.com/Pistoia-Alliance-Inc/IDMP-O/blob/gh-pages/releases/v1.7.0/2026-07-10-Changed-Triples-from-1.6.0-to-1.7.0.xlsx) contains the complete list of changed triples between 1.6.0 and 1.7.0.

</details>

<details>
<summary>IDMP Ontology Release 1.6.0 (master_v1.6.0) - 2026-05-12</summary>

# IDMP Ontology Release 1.6.0

The 1.6.0 release of IDMP-O (Identification of Medicinal Products Ontology) includes development efforts accomplished in the first four months of 2026. Although only 3 issues were addressed in this period, two of them were more significant than might appear at first blush. In late 2025, two main use cases were addressed, one of which focused on batch tracking involving multiple manufacturers, sites, batches, and lots. The batch tracking example pulled in content from the Basic Formal Ontology (BFO), Financial Industry Business Ontology (FIBO), Industrial Ontologies Foundry (IOF), and the Pistoia Chemistry, Manufacturing, and Controls (CMC) process ontology, but had not actually completed the mapping or cached the relevant ontologies as needed for future releases. We completed that work as a part of the IDMP-807 issue resolution, including a significant effort to map the external ontologies to IDMP-O as needed. The mapping effort involved significant testing and a bit of rework to eliminate logical inconsistencies and other reasoning issues, among other challenges. While the resulting mapping may appear to be lighter weight than we had hoped, users should be aware that some of the issues we ran into involved ontological commitments made at lower levels in the mapped ontologies that tied our hands. Challenges included lower level disjointness, restrictions, and other logic, particularly in the IOF ontologies which are heavily reused by the BMIC and CMC ontologies that depend on them. There were also suspicious details in some of lower level IOF and BMIC ontologies, particularly those that were not yet released when we initiated the mapping effort. Recent changes in the IOF and BMIC ontologies may address some of these issues, but release of those changes won't be complete for a few more weeks. Thus we could revisit remapping to the newer versions in another round of maintenance updates. Among other changes, they restructured all of the identifiers for all of the constructs in those ontologies (i.e. changed the structure and nature of all of the IRIs). We also revised some of the vocabularies and examples as part of this effort - filling in a few gaps, adding metadata, and so forth, to enable some of them to be released and to provide a more stable base for further work.

Finally, we created composite 1.5 and 1.6 ontologies for future public release, and addressed a few additional bugs where we noticed them in completing the work on the 1.6 consolidated ontology.

## Qualitative Comparison To Previous Release

### Overview

There were no major structural changes in this release, since most of the work required was completed at the end of last year. Content-specific modifications included significant revisions to the mapping files, a few changes to the main ISO ontologies (mainly substances) to harmonize the class hierarchy and address a couple of issues we uncovered during the mapping process, and revisions to vocabularies and examples as mentioned above.

## What's Changed
* IDMP-1.4.0-forBioPortal - Create a combined version of the released OWL ontologies for publication on the BioPortal by @ElisaKendall
* IDMP-807 - Create link between idmp:LotNumber & cmc:LotIdentification by @ElisaKendall
* IDMP-827 - Create a composite IDMP-O v1.5 ontology for publication purposes by @ElisaKendall
* IDMP-828 - Create a composite IDMP-O v1.6 ontology for publication purposes by @ElisaKendall

</details>

<details>
<summary>IDMP Ontology Release 1.5.0 (master_v1.5.0) - 2025-12-12</summary>

# IDMP Ontology Release 1.5.0

The 1.5.0 release of IDMP-O (Identification of Medicinal Products Ontology) is based on development work accomplished in 2025. Two primary use cases were addressed in this release: (1) cross-jurisdiction regulatory reporting, with a focus on the use of controlled vocabularies that differ from jurisdiction to jurisdiction, for dose forms, ingredient roles, basis of strength, and related concepts, and (2) batch tracking involving multiple manufacturers, sites, batches, and lots. These use cases built on prior work in jurisdiction-specific representation and supply chain, but were driven by steering committee members with real data that we could leverage to show how the ontology could be used internally to address the competency questions provided. Many additional examples (all fragments for various existing or hypothetical products) were added, and gaps uncovered in IDMP-O were addressed in order to facilitate demonstrations and actual implementation. From a maintenance perspective, a number of additional issues were addressed, including several related to improving the structure of the non-ISO-IDMP content provided, such as consolidating controlled vocabularies used in examples, consolidating external ontologies used either in the released IDMP-O ontologies or in examples, creating a new folder for mappings, and so forth. Other maintenance issues addressed emerging metadata requirements from Pistoia Alliance, as well as feedback from users. Planned work for a 1.6.0 release towards the end of Q1 2026 will include fleshing out some of the newer vocabularies and examples, cleaning up issues reported by users or uncovered in implementation to date, and other emerging requirements from Pistoia Alliance. Additional mappings to demonstrate interoperability between IDMP-O and other external and Pistoia ontologies, such as the CMC ontology, will also be included in the 1.6.0 revision.

## Qualitative Comparison To Previous Release

### Overview

1. Structural Modifications - These include:
- Replacing placeholder ontologies that had been under CMNS for geopolitical entities, which did not dereference, with their equivalents from the Financial Industry Business Ontology (FIBO), which are part of the FIBO standard and do dereference properly, with inclusion of the relevant FIBO ontologies for reference purposes in the IDMP GitHub
- Inclusion of new and revised ontologies from Object Management Group (OMG)'s Commons Ontology Library v1.3 and Multiple Vocabulary Facility v1.1 under CMNS and MVF respectively, and revising references to the relevant concepts in IDMP-O as needed
- Consolidating the various jurisdiction-specific regulatory agencies and registration authorities required either by the ISO IDMP specifications or as needed for examples under a single, ISO/JurisdictionSpecificAgencies folder and releasing those that were ready for release
- Consolidating non-ISO IDMP vocabularies in a new VOCAB folder rather than having them distributed between the ISO, EXT, SPAR, and other locations and releasing those that were ready for release
- Moving the examples from EXT/Examples to EXMP for simplification and to clarify for IDMP users exactly what they are so that they can be easily excluded from operational implementations as appropriate
- Creating new CMC, IOF and MAP folders to cache the Pistoia CMC ontology used in our batch tracking use case, cache the set of IOF (Industrial Ontologies Foundry) and related BMIC (formerly NIIMBL) ontologies used in our batch tracking use case, and new mapping ontologies for use in linking between IDMP-O and the CMC ontology (which will be further developed for 1.6.0

2. Content Modifications - These include:
- Many new example ontologies needed to support the two Phase 4 use cases mentioned above, including competency questions, the content needed to answer those questions, and their addition to the set of regression tests used when changes are made to any IDMP-O ontology
- A number of new vocabularies and revisions to existing vocabularies, particularly in support of the regulatory reporting use case
- Release of several jurisdiction-specific vocabularies and the addition of a new provisional vocabulary for the regulatory agencies and registration authorities used in IDMP-O, which will be further extended in 2026 as needed
- Additional metadata to cover emerging Pistoia requirements
- Revisions to the main IDMP-O ontologies as needed either due to (1) better understanding of the ISO specifications, (2) bug fixes, and (3) requirements that emerged from implementation of the new use cases or in general from project stakeholders

3. New consolidated ontologies reflecting only the released content for IDMP-O 1.2.0 and 1.3.0 - in these cases, the content from each of those releases was merged into a single file for ease of use by academics and others that do not need the external ontologies, vocabularies, or examples that are part of the full scope of IDMP-O. A similar consolidated ontology will be available in early 2026 for the 1.4.0 and 1.5.0 versions of IDMP-O.

One ontology was removed:
1. MetadataEXT

| One hundred and thirty eight ontologies were added, including (1) many new cached external references to the Financial Industry Business Ontology (FIBO), Industrial Ontologies Foundry (IOF), and Pistoia Chemistry, Manufacturing, and Controls (CMC) ontology, (2) many new examples and vocabularies, and (3) related metadata files for new folders: | |
|-----------------------------------------------------|----------------------------------------------------------|
| 1\. LegalCapacity | 70\. TiotropiumbromideExample |
| 2\. EtanerceptExample | 71\. PharmaceuticalProcess |
| 3\. MappingCommonsToBFO | 72\. CorporateOwnership |
| 4\. SwissIngredientRoles | 73\. AllFND |
| 5\. MappingIDMPOToBFO | 74\. MetadataFNDLaw |
| 6\. DenosumabExample | 75\. CentralAmericanGovernmentEntitiesAndJurisdictions |
| 7\. Facilities | 76\. CentralAsiaGovernmentEntitiesAndJurisdictions |
| 8\. AccountingEquity | 77\. AllFND\-NorthAmerica |
| 9\. Control | 78\. IdentifiersAndIndices |
| 10\. MappingMVFToBFO | 79\. Material |
| 11\. AllBE\-NorthAmerica | 80\. RealProperty |
| 12\. MetadataFNDAgreements | 81\. Lifecycles |
| 13\. Parties | 82\. MXGovernmentEntitiesAndJurisdictions |
| 14\. MetadataFNDOrganizations | 83\. Partnerships |
| 15\. AmericanDoseForms | 84\. AboutIDMP\-O\-and\-BFO |
| 16\. MetadataBEOwnershipAndControl | 85\. Corporations |
| 17\. LinagliptinExample | 86\. ClassificationSchemes |
| 18\. MetadataBESoleProprietorships | 87\. MetadataFNDAgentsAndPeople |
| 19\. Ratings | 88\. MetadataBEPartnerships |
| 20\. Agents | 89\. USPostalServiceAddressesIndividuals |
| 21\. MetadataFNDParties | 90\. Executives |
| 22\. MetadataBECorporations | 91\. Trusts |
| 23\. REATransactions | 92\. SoutheasternAsiaGovernmentEntitiesAndJurisdictions |
| 24\. MetadataBE | 93\. LEIEntities |
| 25\. USExampleEntities | 94\. MetadataFNDOwnershipAndControl |
| 26\. SouthAmericanRegulatoryAgencies | 95\. CorporateControl |
| 27\. IdentificationOfMedicinalProductsOntology | 96\. PrivateLimitedCompanies |
| 28\. MetadataEXMP | 97\. Jurisdiction |
| 29\. MetadataFNDGoalsAndObjectives | 98\. Physical |
| 30\. SouthernAsiaGovernmentEntitiesAndJurisdictions | 99\. AllBE |
| 31\. Recipe | 100\. EmpagliflozinExample |
| 32\. EasternAsiaGovernmentEntitiesAndJurisdictions | 101\. ApremilastExample |
| 33\. MetadataFNDPlaces | 102\. FinancialDates |
| 34\. CanadianDoseForms | 103\. People |
| 35\. TiotropiumolodaterolExample | 104\. Objectives |
| 36\. ArgentinianIngredientRoles | 105\. MetadataBEPrivateLimitedCompanies |
| 37\. VirtualPlaces | 106\. MetadataFNDAccounting |
| 38\. MetadataFNDArrangements | 107\. OwnershipParties |
| 39\. MetadataFNDTransactionsExt | 108\. Ownership |
| 40\. FormalBusinessOrganizations | 109\. MetadataFND |
| 41\. MetadataBEFunctionalEntities | 110\. CinacalcetExample |
| 42\. Analytics | 111\. MetadataFNDRelations |
| 43\. Arrangements | 112\. CorporateBodies |
| 44\. AllBE\-NorthAmericanExamples | 113\. CashFlows |
| 45\. CurrencyAmount | 114\. EvolocumabExample |
| 46\. CarfilzomibExample | 115\. MetadataBEGovernmentEntities |
| 47\. Publishers | 116\. MetadataFNDUtilities |
| 48\. USExampleExecutives | 117\. Product1Example |
| 49\. AllBE\-Europe | 118\. AllBE\-ReferenceIndividuals |
| 50\. USPostalServiceAddresses | 119\. Contracts |
| 51\. SecuritiesTransactions | 120\. BlinatumomabExample |
| 52\. MetadataFNDDatesAndTimes | 121\. PegfilgrastimExample |
| 53\. Assessments | 122\. MetadataBELegalEntities |
| 54\. Core | 123\. SoleProprietorships |
| 55\. Occurrences | 124\. PaymentsAndSchedules |
| 56\. LegalCore | 125\. Languages |
| 57\. SotorasibExample | 126\. ChileanIngredientRoles |
| 58\. LegalPersons | 127\. MarketTransactions |
| 59\. MetadataFIBO | 128\. Product2Example |
| 60\. AllBE\-ExampleIndividuals | 129\. MetadataVOCAB |
| 61\. ControlParties | 130\. ExtendedEudraVigilenceProductRolesAndCodes |
| 62\. DabigatranExample | 131\. FormalOrganizations |
| 63\. MetadataFNDProductsAndServices | 132\. BusinessAuthorizations |
| 64\. CaribbeanGovernmentEntitiesAndJurisdictions | 133\. IpratropiumbromideExample |
| 65\. ISO4217\-CurrencyCodes | 134\. SouthAmericanGovernmentEntitiesAndJurisdictions |
| 66\. OwnershipAndControl | 135\. FunctionalEntities |
| 67\. Relations | 136\. MetadataBETrusts |
| 68\. ManufacturingExecution | 137\. Agreements |
| 69\. BusinessDates | 138\. Reporting |

The following ontologies were revised and/or extended, including, structural moves, reflected in cases where resources were deleted and readded:

| Ontologies | Deleted Resources | New Resources | Modified Resources |
|--------------------------------------------------|-------------------|---------------|---------------------|
| Addresses | 83 | 77 | 0 |
| AmlodipineExample | 76 | 76 | 167 |
| AnnotationVocabulary | 0 | 5 | 0 |
| CAGovernmentEntitiesAndJurisdictions | 42 | 42 | 0 |
| CommonTerminologyCriteriaForAdverseEvents | 10 | 10 | 0 |
| ContextualDesignators | 0 | 0 | 3 |
| DatesAndTimes | 0 | 0 | 4 |
| Designators | 0 | 2 | 4 |
| doco | 0 | 0 | 14 |
| DocumentComponents | 23 | 23 | 0 |
| Documents | 16 | 5 | 0 |
| EasternEuropeGovernmentEntitiesAndJurisdictions | 30 | 30 | 0 |
| EUGovernmentEntitiesAndJurisdictions | 8 | 8 | 0 |
| EuropeanRegistrationAuthorities | 30 | 30 | 0 |
| EuropeanRegulatoryAgencies | 6 | 9 | 0 |
| EuropeanUnionClinicalTrialsRegister | 41 | 41 | 11 |
| GovernmentEntities | 29 | 36 | 0 |
| ISO1087\-TerminologyScience | 0 | 10 | 5 |
| ISO1087\-VocabularyForTermsAndDefinitions | 2 | 2 | 13 |
| ISO11238\-RegistrationAuthorities | 8 | 2 | 10 |
| ISO11238\-Substances | 0 | 0 | 68 |
| ISO11239\-PharmaceuticalDoseForms | 0 | 0 | 1 |
| ISO11240\-UnitsOfMeasurement | 0 | 0 | 2 |
| ISO11615\-MedicinalProducts | 1 | 11 | 80 |
| ISO11616\-PharmaceuticalProducts | 0 | 0 | 1 |
| ISO21090\-HarmonizedDatatypes | 0 | 9 | 13 |
| ISO5218\-RepresentationOfHumanSexes | 11 | 11 | 0 |
| LanguageRepresentation | 0 | 0 | 2 |
| Locations | 43 | 18 | 1 |
| MedicalDictionaryForRegulatoryActivities | 18 | 18 | 0 |
| MetadataIDMP | 0 | 0 | 2 |
| MetadataISO | 0 | 0 | 2 |
| MetadataSPAR | 1 | 1 | 0 |
| MultipleVocabularyFacility | 0 | 2 | 13 |
| MVFtoSKOSMapping | 3 | 2 | 1 |
| NorthAmericanRegistrationAuthorities | 59 | 59 | 0 |
| NorthAmericanRegulatoryAgencies | 7 | 8 | 0 |
| NorthernEuropeGovernmentEntitiesAndJurisdictions | 30 | 30 | 0 |
| Organizations | 34 | 15 | 0 |
| PartiesAndSituations | 0 | 0 | 2 |
| po | 0 | 0 | 8 |
| ProductsAndServices | 25 | 37 | 0 |
| PublicHealthInformationNetwork | 20 | 20 | 0 |
| QlairaExample | 106 | 106 | 112 |
| RegistrationAuthorities | 0 | 0 | 8 |
| RegulatoryAgencies | 0 | 0 | 2 |
| SitesAndFacilities | 0 | 0 | 4 |
| SouthernEuropeGovernmentEntitiesAndJurisdictions | 45 | 45 | 0 |
| StatisticalMeasures | 0 | 0 | 3 |
| StructuredCollections | 0 | 0 | 1 |
| SubstancesProductsOrganisationsReferentials | 121 | 139 | 0 |
| TerlipressinExample | 57 | 57 | 7 |
| UKGovernmentEntitiesAndJurisdictions | 21 | 21 | 0 |
| UnifiedCodeForUnitsOfMeasure | 30 | 30 | 1 |
| USGovernmentEntitiesAndJurisdictions | 171 | 171 | 0 |
| WesternAsiaGovernmentEntitiesAndJurisdictions | 54 | 54 | 0 |
| WesternEuropeGovernmentEntitiesAndJurisdictions | 27 | 27 | 0 |

## What's Changed
* IDMP-1.2.0-forBioPortal - Create a combined version of the released OWL ontologies for publication on the BioPortal by @ElisaKendall
* IDMP-1.3.0-forBioPortal - Create a combined version of the released OWL ontologies for publication on the BioPortal by @ElisaKendall
* IDMP-1.2.0-forBioPortal-a - Simplify the ontology by removing references to the external OMG MVF and LCC ontologies by @ElisaKendall
* IDMP-735 - Add preliminary mapping of Commons, LCC, and MVF to BFO by @ElisaKendall
* IDMP-785 - Reduce dependencies on MVF where possible by @ElisaKendall
* IDMP-784 - Revise the definitions of batch, lot, batch number and lot number by @ElisaKendall
* IDMP-790 - uc_cmc_cq5.sparql missing link between material and materialID by @Toby-Broom
* IDMP-783 - Replace references to the OMG ontologies that are not dereferenceable for ease of use by external users by @ElisaKendall
* IDMP-M2-Maint-668 - The dev version must contain the copyright statement [High priority] by @ElisaKendall
* GitHub-M2-Maint-671 - Duplicate individual representing the US jurisdiction in the North American Regulatory Agencies ontology by @ElisaKendall
* IDMP-796 Resolve inconsistency of hasEarlierForm with preceded by by @ElisaKendall
* IDMP-1.2.0-forBioPortal - Create a combined version of the released OWL IDMP v1.2.0 ontologies for public release and publication on the BioPortal by @ElisaKendall
* IDMP-1.3.0-forBioPortal - Create a combined version of the released 1.3.0 IDMP-O OWL ontologies for public release and publication on the BioPortal by @ElisaKendall
* IDMP-797 - Add rights statement to the 1.2.0 and 1.3.0 ontologies by @ElisaKendall
* IDMP-793 - Augment the set of examples to support the regulatory use case by @ElisaKendall
* IDMP-794 - Augment the set of examples to support the batch tracking use case by @Toby-Broom
* IDMP-799 - Replace CMNS government entities and jurisdictions, which will not resolve, with the FIBO equivalents by @ElisaKendall
* IDMP-800 - A number of vocabularies that are not intrinsic to the ISO IDMP standards should be moved to a separate module by @ElisaKendall
* IDMP-809 - Move mapping files to a new MAP module by @ElisaKendall
* IDMP-813 - Revise the OMG MVF ontologies archived to reflect the changes included in the upcoming MVF 1.1 specification by @ElisaKendall
* IDMP-818 - Migrate the SPAR ontologies to a separate folder under VOCAB by @ElisaKendall
* IDMP-810 - Clean up vocabs that use invalid IRI patterns by @Toby-Broom
* IDMP-819 - Move the two higher level vocabularies for document components and UCUM to the VOCAB folder by @ElisaKendall
* IDMP-798 - Add 2nd example to support the batch tracking use case by @Toby-Broom
* IDMP-820 - Move controlled vocabularies currently managed under EXT/Vocabulary to VOCAB by @ElisaKendall
* IDMP-823 - Move the examples, currently under EXT/Examples to a top-level folder (WIP) by @ElisaKendall

## New Contributors
* @Toby-Broom made their first contribution

</details>

<details>
<summary>IDMP Ontology Release 1.4.0 (master_v1.4.0) - 2025-02-24</summary>

# IDMP Ontology Release 1.4.0

The focus of IDMP development work for Q4 2024 was on bridging gaps related to supply chain and manufacturing, in response to recent use cases. Most of the work involved developing competency questions related to batch tracking, filling in manufacturing details such as site (business operations) and facility related content, and revising the relationship between medicinal products, packaged medicinal products, materials, package items and other related entities to improve flow and eliminate some unnecessary complexity. The resulting ontologies are cleaner and more easily understood. Additional work will be needed in the next phase of the project to support more granular product versions, related metadata, details needed to continue to improve traceability and enable mapping across complex ERP, regulatory reporting and other systems. The Amlodipine example was extended substantially to support this initial batch tracking testing effort. Most of the work was done under two issues - IDMP-744 and the GitHub-AmlodipineExample issue, listed below.

## Qualitative Comparison To Previous Release

### Overview

Four ontologies were added:
1. Addresses
1. USGovernmentEntitiesAndJurisdictions
1. CAGovernmentEntitiesAndJurisdictions
1. SitesAndFacilities

The following ontologies were revised and/or extended:

Ontologies | Deleted Resources | New Resources | Modified Resources
-- | -- | -- | --
AmlodipineExample | 3 | 20 | 14
doco | 0 | 0 | 14
DocumentComponents | 0 | 0 | 5
EuropeanRegistrationAuthorities | 0 | 0 | 1
ISO1087-TerminologyScience | 0 | 0 | 1
ISO1087-VocabularyForTermsAndDefinitions | 0 | 0 | 2
ISO11238-RegistrationAuthorities | 0 | 0 | 1
ISO11238-Substances | 0 | 6 | 41
ISO11239-PharmaceuticalDoseForms | 0 | 0 | 3
ISO11615-MedicinalProducts | 0 | 6 | 38
ISO11616-PharmaceuticalProducts | 0 | 0 | 1
MedicalDictionaryForRegulatoryActivities | 0 | 0 | 2
NorthAmericanRegistrationAuthorities | 0 | 0 | 1
Organizations | 0 | 0 | 3
po | 0 | 0 | 8
ProductsAndServices | 5 | 0 | 4
QlairaExample | 5 | 1 | 8
RegistrationAuthorities | 0 | 0 | 3
StatisticalMeasures | 0 | 0 | 3
StructuredCollections | 0 | 0 | 3
SubstancesProductsOrganisationsReferentials | 0 | 0 | 1

## What's Changed
* IDMP-744 - Investigate simplifying potential circularities in the packaging / container specification part of the ontology by @ElisaKendall
* GitHub-AmlodipineExample - Added details for manufacturing operation and site for Pfizer by @ElisaKendall
* Updated 2 of the CMC UC CQs to reflect ontology revisions by @ElisaKendall

</details>

<details>
<summary>IDMP Ontology Release 1.3.0 (master_v1.3.0) - 2025-02-18</summary>

# IDMP Ontology Release 1.3.0

## Ontology Development in Details

Significant additional content was added to the IDMP-O ontologies in the Q3 2024, 1.3 release. New material covers parts of the ISO 11615 standard related to marketing authorizations, marketing status, manufacturing authorizations, manufacturers, manufacturing / business operations and related concepts, and so forth. These additions were made primarily to address new use cases, such as the EMA SPOR PMS-related use case, but have increased our coverage of the specification at the same time in preparation for inclusion of the ontology in the set of ISO standards for Identification of Medicinal Products. In addition, we have addressed numerous bug fixes and inconsistencies identified through existing and newly added hygiene testing, thereby increasing the quality of the ontologies. The latest release of the Object Management Group’s Commons Ontology Library v1.3 has also been integrated in advance of formal publication in the OMG’s specification catalog, anticipated in Q4. Dereferenceable ontologies corresponding to 5 that are currently only available in GitHub, used by IDMP-O, will be available directly from the OMG site before the end of the year (final approval is quorate with voting underway).

## Qualitative Comparison To Previous Release

### Overview

No ontology was added or deleted.

The following ontologies were revised and/or extended:

Ontologies | Deleted Resources | New Resources | Modified Resources
-- | -- | -- | --
AmlodipineExample | 0 | 0 | 1
Classifiers | 0 | 0 | 2
CommonTerminologyCriteriaForAdverseEvents | 0 | 0 | 3
Designators | 0 | 2 | 1
doco | 0 | 0 | 14
DocumentComponents | 0 | 0 | 5
EUGovernmentEntitiesAndJurisdictions | 0 | 0 | 1
EuropeanRegistrationAuthorities | 0 | 1 | 20
EuropeanUnionClinicalTrialsRegister | 0 | 0 | 1
GovernmentEntities | 0 | 0 | 11
ISO1087-TerminologyScience | 0 | 0 | 1
ISO1087-VocabularyForTermsAndDefinitions | 0 | 0 | 2
ISO11238-RegistrationAuthorities | 0 | 0 | 8
ISO11238-Substances | 0 | 0 | 45
ISO11239-PharmaceuticalDoseForms | 0 | 0 | 1
ISO11240-UnitsOfMeasurement | 0 | 0 | 3
ISO11615-MedicinalProducts | 0 | 60 | 53
ISO11616-PharmaceuticalProducts | 0 | 0 | 1
ISO21090-HarmonizedDatatypes | 0 | 11 | 1
Locations | 5 | 28 | 12
MedicalDictionaryForRegulatoryActivities | 0 | 0 | 3
NorthAmericanRegistrationAuthorities | 0 | 0 | 30
Organizations | 2 | 15 | 14
po | 0 | 0 | 8
ProductsAndServices | 6 | 0 | 13
PublicHealthInformationNetwork | 0 | 0 | 2
QlairaExample | 0 | 0 | 1
QuantitiesAndUnits | 5 | 2 | 7
RegistrationAuthorities | 5 | 0 | 13
RegulatoryAgencies | 5 | 0 | 8
StatisticalMeasures | 3 | 0 | 8
StructuredCollections | 0 | 0 | 5
SubstancesProductsOrganisationsReferentials | 1 | 4 | 12
TerlipressinExample | 0 | 0 | 1
UKGovernmentEntitiesAndJurisdictions | 0 | 0 | 1

## What's Changed
* IDMP-747 - Complete the ISO 11615 details related to marketing authorization by @ElisaKendall
* IDMP-750 - Complete the work required to fill in marketing status related attributes (EMA-PMS) by @ElisaKendall
* IDMP-753 - xEVMPD code class definition check by @ElisaKendall
* IDMP-771 - Revise the Quantities and Units ontology to reflect the latest revisions in the OMG Commons library by @ElisaKendall
* IDMP-745 - Augment the medicinal products ontology to flesh out the medicinal product name by @ElisaKendall
* GitHub-626 - Address punning in SPOR schema definitions for RMS, PMS by @ElisaKendall
* Unused hygiene tests to be "parked" by @mereolog
* GitHub-629 - Punning of idmp-spor:SPOR-Domain by @ElisaKendall
* IDMP-774 - Update remaining Commons ontologies to reflect the latest additions and changes to the OMG specification by @ElisaKendall
* Update to property punning checks by @mereolog
* Use hash for substance name in SPOR SMS by @aliariff
* Checks for punning on classes and individuals by @mereolog
* IDMP-779 - Augment the ISO 11615 ontology to include a property chain from manufacturer to the manufacturing site by @ElisaKendall
* IDMP-776 - Harmonize Strength naming: Change "Concentration" to "Concentration Strength" by @ElisaKendall

</details>

<details>
<summary>IDMP Ontology Release 1.2.0 (master_v1.2.0) - 2024-07-12</summary>

# IDMP Ontology Release 1.2.0

## Ontology Development in Details

This quarter our focus was on bug fixing, usability, and simplification, in preparation for extensions supporting additional use cases in Q3. Analysis done over several weeks led to the conclusion that certain constructs, including some related to packaging, could be simplified for ease of use as well as to increase representation and reasoning efficiency. Because of the complexity involved not only in the ontology but in the IDMP standards, we are unwinding certain parts of the ontology incrementally rather than in a single issue. Simplification efforts will continue into Q3, when we will also be adding a number of new constructs. New work will involve fleshing out details for concepts needed for use cases such as the EMA PMS Data Alignment PoC, filling in gaps where there are missing attributes, for example, for some parts of the model.

## Qualitative Comparison To Previous Release

### Overview

No ontology was added or deleted.

The following ontologies were revised and/or extended:

Ontologies | Deleted Resources | New Resources | Modified Resources
| -- | -- | -- | -- |
AmlodipineExample | 0 | 0 | 7
doco | 0 | 0 | 14
DocumentComponents | 0 | 0 | 5
EuropeanRegistrationAuthorities | 0 | 0 | 13
ISO1087-TerminologyScience | 0 | 0 | 1
ISO1087-VocabularyForTermsAndDefinitions | 0 | 0 | 2
ISO11238-RegistrationAuthorities | 0 | 0 | 11
ISO11238-Substances | 0 | 1 | 58
ISO11239-PharmaceuticalDoseForms | 0 | 0 | 4
ISO11615-MedicinalProducts | 3 | 5 | 57
ISO21090-HarmonizedDatatypes | 0 | 0 | 6
Locations | 0 | 0 | 4
MedicalDictionaryForRegulatoryActivities | 0 | 0 | 2
MultipleVocabularyFacility | 0 | 0 | 2
NorthAmericanRegistrationAuthorities | 0 | 0 | 22
Organizations | 0 | 0 | 9
po | 0 | 0 | 8
ProductsAndServices | 0 | 2 | 4
QlairaExample | 0 | 0 | 5
QuantitiesAndUnits | 0 | 2 | 9
RegistrationAuthorities | 0 | 0 | 3
RegulatoryAgencies | 0 | 0 | 4
StatisticalMeasures | 0 | 0 | 3
SubstancesProductsOrganisationsReferentials | 0 | 0 | 1
TerlipressinExample | 0 | 0 | 1

## What's Changed
* IDMP-GitHub-564 - Textual values for substance names by @ElisaKendall
* IDMP-GitHub-567 - Two typos in reference to rdfs:subPropertyOf by @ElisaKendall
* IDMP-GitHub-573 - Correct a wrong prefix for reference source by @ElisaKendall
* IDMP-GitHub-571 - Simplify the licensing definitions in Commons to facilitate mapping to BFO by @ElisaKendall
* hygiene tests added for prefLabels by @mereolog
* IDMP-734 - Add skos:prefLabel to terms that have multilingual labels by @ElisaKendall
* IDMP-720 - Few SHACL examples added for discussion by @mereolog
* GitHub-589 - Improper references to IDMP resources by @ElisaKendall
* IDMP-GitHub-584 - Loosen constraints on MVF Element to allow for mapping MEDdra terms to those in EMA SPOR and other vocabularies by @ElisaKendall
* GitHub-590 - Missing disjointness axiom on starting material role by @ElisaKendall
* GitHub-587 - "Broken" URLs in IDMPO literals by @ElisaKendall
* GitHub-580: add mvf-trm:Term as parent class for MedDRA term by @tw-osthus
* GitHub-594 - Possibly broken URLs in IDMP Prod literals by @ElisaKendall
* GitHub-586 - Add the additional definitional material for substance from ISO 11238 to the current definition from Commons as annotations by @ElisaKendall
* GitHub-583 - Possible ill-formed definition for MarketingStatusReasonCode by @ElisaKendall
* GitHub-577 - Potentially vicious "circular" restrictions by @ElisaKendall
* GitHub-601 - Modify the SPAR PO ontology to eliminate the SWRL Builtin statements which cannot be processed by certain reasoners by @ElisaKendall
* GitHub-598 - Obsolete restriction on idmp-sub:Amount by @ElisaKendall
* Additional hygiene test for obsolete restrictions by @mereolog
* IDMP-682 - Investigate simplifying potential circularity in population characteristic by @ElisaKendall
* IDMP-748 - Modify the packaging approach to make package roles individuals by @ElisaKendall
* IDMP-738: Fix uri in GSRS transformation files by @aliariff
* Update SPOR transformation files by @aliariff
* Fix Warning in GitHub Actions CI by @aliariff

</details>

<details>
<summary>IDMP Ontology Release 1.1.0 (master_v1.1.0) - 2024-04-10</summary>

# IDMP Ontology Release 1.1.0

## Ontology Development in Details

In Q1 2024 there were two primary areas of work, including:
1. significant additions to cover details needed for representation of biologics – organisms, parts of organisms, the subset of the Linnean taxonomy needed for herbal substances, inheritance relationships between organisms, completion of the model with respect to target and target interaction, and related areas in the ISO 11238 Substance ontology, and 
1. significant additions to cover gaps in the ISO 11615 model related to medicinal products, package items and other concepts required for the jurisdiction-agnostic UC4 – adding concepts representing attributes and relations that were not completely modeled for therapeutic indications, contraindications, and population characteristics; completing the definition of pharmaceutical product characteristic, completing details for manufactured item and package item, completing details related to pharmaceutical dose form and its subclasses (administrable, combined), and related restrictions on medicinal product, and adding missing attributes and relations such as ‘special measures’, pediatric use indicator, and monitoring indicator, as well as addressing other miscellaneous gaps and issues in restrictions in that part of the ontology for ISO 11615.

## Qualitative Comparison To Previous Release

### Overview
Three of the SPAR ontologies (related to library science, which we were not using) were deleted:
- frbr
- c4o
- datacite

The following ontologies were changed:

Ontologies | Deleted Resources | New Resources | Modified Resources
| -- | -- | -- | -- |
AmlodipineExample | 0 | 0 | 2
deo | 16 | 0 | 0
doco | 16 | 13 | 37
DocumentComponents | 0 | 0 | 8
ISO1087-TerminologyScience | 0 | 0 | 1
ISO1087-VocabularyForTermsAndDefinitions | 0 | 0 | 2
ISO11238-Substances | 2 | 53 | 44
ISO11615-MedicinalProducts | 1 | 17 | 50
ISO21090-HarmonizedDatatypes | 2 | 0 | 3
MedicalDictionaryForRegulatoryActivities | 0 | 0 | 1
Organizations | 0 | 0 | 8
po | 31 | 30 | 0
ProductsAndServices | 0 | 0 | 4
QlairaExample | 6 | 8 | 4
QuantitiesAndUnits | 0 | 2 | 18
RegistrationAuthorities | 0 | 0 | 3
RegulatoryAgencies | 0 | 0 | 2
StatisticalMeasures | 0 | 0 | 3
SubstancesProductsOrganisationsReferentials | 0 | 0 | 1

## What's Changed
* IDMP-657 - add missing package item properties by @tw-osthus
* IDMP-713 - Augment the ontology to incorporate additional information related to biologics by @ElisaKendall
* IDMP-713a - Augment the ontology to incorporate additional information related to biologics by @ElisaKendall
* IDMP-726 - Augment / revise the ontology to cover gaps w.r.t. ISO 11615 for UC4 by @ElisaKendall

</details>

<details>
<summary>IDMP Ontology Release 1.0.0 (master_v1.0.0) - 2024-01-05</summary>

# IDMP Ontology Release 1.0.0

## Ontology Development in Details
Over the last quarter, since the 0.5.0 release, the development team has focused on:
1. better coverage of the ISO 11238 Substances content.
1. better coverage of the ISO 11615 Medicinal Products content.
1. extending and improving examples to demonstrate how to use the ontologies in real-world applications.

We have also worked towards increased usability and flexibility, and augmented these two ontologies with additional metadata to improve understandability. Details, including additional references and the degree to which a given element complies with the ISO standard(s), were also added. 

In addition to adding new content, we have taken advantage of revisions to the OMG Commons Ontology Library v1.1 updates. Four additional ontologies have been added as formal standards at OMG, which are now dereferenceable from the OMG website. They include the Documents, Parties and Situations, Roles and Compositions, and Quantities and Units ontologies that IDMP-O depends on. We anticipate publication of another update to the Commons Library, including the other 5 ontologies that our main ISO standard ontologies depend on in mid-2024. See https://www.omg.org/spec/Commons/ for more information.

Also, in order to demonstrate how to extend labeling details as required by the ISO IDMP standards with tables or other rich document content, we've integrated a new family of ontologies from the library science community called the "SPAR Ontologies", or Semantic Publishing and Referencing Ontologies (see http://www.sparontologies.net/ and https://github.com/sparontologies for more information). These ontologies include a few issues which we are working with their development team to resolve, and are only used in examples as a consequence. Together with a new DocumentComponents ontology in IDMP, they address challenges for IDMP based regulatory reporting related to linking content embedded in documents, including rich tables, which are referenced as string values in the IDMP ISO documents. These are described under the quantitative view, below, among the 7 new ontologies listed. They are also described in examples at [Pattern: Citing and linking into reference documents - REVIEW]
(https://wiki.edmcouncil.org/display/IDMP/Pattern%3A+Citing+and+linking+into+reference+documents+-+REVIEW).

We removed one starting point example which may be reintegrated over the coming months if it is needed. It did not show enough new content to warrant integration in the 1.0 release.

## Qualitative Comparison To Previous Release

### Overview
One ontology was deleted:
1. CellCeptExample – incomplete example that may be added back later this year
7 new ontologies were added:
1. c40 – Citation Counting and Context Characterisation Ontology (C4O)
1. datacite – covers the DataCite Metadata Schema Specification for citations
1. deo – Discourse Elements Ontology (DEO)
1. doco – Document Components Ontology (DoCo)
1. frbr – Essential FRBR in OWL2 DL Ontology (FRBR), which corresponds to the IFLA report on the Functional Requirements for Bibliographic Records (FRBR)
1. po – Pattern Ontology (PO)
1. DocumentComponents – an extension to the SPAR ontologies primarily focused on table content 

Except for the last one, all of them are SPAR ontologies.

The following ontologies were changed:

Ontologies | Deleted Resources | New Resources | Modified Resources
| -- | -- | -- | -- |
AmlodipineExample | 58 | 259 | 24
EuropeanRegulatoryAgencies | 0 | 0 | 2
EuropeanUnionClinicalTrialsRegister | 4 | 12 | 5
ISO11238-Substances | 4 | 66 | 114
ISO1087-TerminologyScience | 0 | 0 | 1
ISO1087-VocabularyForTermsAndDefinitions | 0 | 0 | 2
ISO11238-RegistrationAuthorities | 0 | 0 | 1
ISO11240-UnitsOfMeasurement | 0 | 5 | 
ISO11615-MedicinalProducts | 2 | 78 | 84
ISO21090-HarmonizedDatatypes | 0 | 0 | 14
MedicalDictionaryForRegulatoryActivities | 0 | 0 | 5
Organizations | 0 | 0 | 2
ProductsAndServices | 0 | 0 | 4
QlairaExample | 79 | 226 | 5
RegistrationAuthorities | 0 | 0 | 3
RegistrationAuthorities | 0 | 0 | 2
StatisticalMeasures | 0 | 0 | 3
SubstancesProductsOrganisationsReferentials | 6 | 1 | 69
TerlipressinExample | 7 | 19 | 19

## What's Changed
* More possible typos in annotations fixed by @mereolog
* Spellcheck automation as a GitHub action by @mereolog
* IDMP-665 - Update the Qlaira example to use the proper IRIs for the SPOR details by @ElisaKendall
* IDMP-594 - Complete the definition of protein substances by @ElisaKendall
* IDMP-659 - add package components, medical device and characteristics by @tw-osthus
* fix wrong rdf:type on classifier instance by @tw-osthus
* IDMP-673 - Complete the minimal set of required fields from Annex L for Polymers by @ElisaKendall
* GitHub-511 - dmp-sub:SubstanceNameClassifier-CommonName has incomplete definition by @ElisaKendall
* GitHub-505 - Non-classifying, but just denoting, classifiers by @ElisaKendall
* IDMP-674 - Exclude shelf life type and special precautions for storage from the SPOR ontology in advance of regeneration of the SPOR lists and vocabulary elements by @ElisaKendall
* IDMP-634 - Remove the default code for ingredient and active ingredient by @ElisaKendall
* IDMP-640 add characteristics for target populations by @tw-osthus
* IDMP-675 - Complete the minimal set of required fields from Annex L for Mixtures by @ElisaKendall
* GitHub-512 - idmp-mprd:hasSpecialStorageConditions has wrong range by @tw-osthus
* GitHub-525 - hasSPORTermDescription is an ObjectProperty by @tw-osthus
* Idmp 670 by @konradkrebs1411
* IDMP-645 add SPAR ontologies and an extension by @tw-osthus
* Fixed URLs by @konradkrebs1411
* Spellcheck ignores reified languages by @mereolog
* Fix to underspecified examples hygiene test by @mereolog
* GitHub-501 - ISO non-compliant definitions by @ElisaKendall
* Add and modify catalog files in subfolders by @mereolog
* GitHub-538 - remove functional from properties by @tw-osthus
* IDMP-616 enhance Amlodipine example by @tw-osthus
* IDMP-678 - apply GSRS pattern for substances and substance names by @tw-osthus
* IDMP-677 - Add missing macro content for ISO 11615 by @ElisaKendall
* IDMP-677a - Add missing macro content for ISO 11615, addressing remaining gaps by @ElisaKendall
* IDMP-679 - Remove the CellCept example prior to the 1.0 release by @ElisaKendall
* Update spor-substances.rqg by @konradkrebs1411
* IDMP-322 - ISO11238: Document the ISO IDMP conformance level as annotations in the IDMP-O where deviations exist by @ElisaKendall
* IDMP-383 - ISO11615: Document the ISO IDMP conformance level as annotations in the IDMP-O where deviations exist by @ElisaKendall

</details>

<details>
<summary>IDMP Ontology Release 0.5.0 (master_v0.5.0) - 2023-10-05</summary>

# IDMP Ontology Release 0.5.0

## Ontology Development in Details

Major accomplishments in the 0.5.0 release range from significant improvements in representation of controlled vocabularies, including but not limited to EMA SPOR vocabularies, to extensions in a number of areas related to the ISO 11238 Substances and ISO 11615 Medicinal Products ontologies.
The revised model for controlled vocabularies extends the Object Management Group's (OMG) Commons Ontology Library with the OMG Multiple Vocabulary Facility (MVF) ontologies, designed specifically to support controlled vocabularies, taxonomies, and nomenclature representation based on ISO 1087. The Commons Ontology Library was also updated to incorporate ontologies that have been revised or added in the 1.1 revision of that standard.
Several controlled vocabularies were added in addition to better support for EMA SPOR, including support for MedDRA vocabularies, Common Terminology Criteria for Adverse Events, ISO 5218 vocabulary for the representation of human sexes, and content from the Public Health Information Network. Content related to the US and EU regulatory agencies and repositories was also extended and US-specific content moved to a new North American module rather than in the main ISO Regulatory Agencies ontology, which ultimately will be limited to international bodies and repositories such as the WHO.
Additional content related to ISO 11238 includes complete coverage for nucleic acids and structurally diverse substances, as well as for more basic concepts such as properties of substances that apply to multiple kinds of substances. Updates to the ISO 11615 Medicinal Products ontology include support for therapeutic indications as well as packaging related details. Most examples were extended to cover the new content and the CellCeptExample was added to support additional competency questions.

## Qualitative Comparison To Previous Release

### Overview
12 new ontologies were added:

1. CellCeptExample
1. CommonTerminologyCriteriaForAdverseEvents
1. ISO1087-TerminologyScience*
1. ISO1087-VocabularyForTermsAndDefinitions*
1. ISO5218-RepresentationOfHumanSexes
1. MedicalDictionaryForRegulatoryActivities
1. MultipleVocabularyFacility*
1. MVFtoSKOSMapping*
1. NorthAmericanRegistrationAuthorities
1. NorthAmericanRegulatoryAgencies
1. PublicHealthInformationNetwork
1. RolesAndCompositions*

Ontologies marked with '*' are OMG-related, either Commons Ontology Library v1.1 or Multiple Vocabulary Facility (MVF). As noted above, the ISO11238-Substances-DeprecatedElements ontology, which was managed independently in order to facilitate elimination, was deleted.

The following ontologies were changed:

Ontology Short Name | Deleted Resources | New Resources | Modified Resources
-- | -- | -- | --
AmlodipineExample | 5 | 13 | 42
ChangeManagement | 1 | 0 |  
DatesAndTimes* | 0 | 9 | 8
Documents* | 14 | 3 | 11
EUGovernmentEntitiesAndJurisdictions | 0 | 0 | 2
EuropeanRegistrationAuthorities | 0 | 2 | 10
EuropeanRegulatoryAgencies | 0 | 0 | 5
EuropeanUnionClinicalTrialsRegister | 0 | 0 | 18
GovernmentEntities | 0 | 0 | 2
ISO11238-RegistrationAuthorities | 62 | 0 | 4
ISO11238-Substances | 3 | 72 | 160
ISO11615-MedicinalProducts | 9 | 42 | 68
ISO21090-HarmonizedDatatypes | 0 | 2 | 49
Organizations* | 0 | 0 | 5
PartiesAndSituations* | 9 | 1 | 30
ProductsAndServices | 0 | 0 | 11
QlairaExample | 1 | 0 | 48
QuantitiesAndUnits | 3 | 5 | 20
RegistrationAuthorities | 0 | 0 | 5
RegulatoryAgencies | 0 | 0 | 4
StatisticalMeasures | 0 | 0 | 6
SubstancesProductsOrganisationsReferentials | 19 | 108 | 10
TerlipressinExample | 0 | 3 | 29

Ontologies marked with '*' are OMG-related, modified as part of the Commons Ontology Library v1.1 release. Note that certain OMG-specific ontologies were simplified, although some of the content, such as the concepts related to regulatory reporting, will come back in a separate ontology in the 1.2 revision of the Commons library. Elements that were eliminated from the Quantities and Units ontology were renamed to reflect the fact that they actually define scalar quantities. An upcoming addition to the library will cover arrays, tensors, and vectors as well as the related tensor and vector quantities, and a reference library of over 700 units will be generated from the new OMG SysML v2 library of quantities and units. We look forward to being able to use that, given that it is OWL DL compliant, which the QUDT ontology is not, and other ontologies for units tend to be incomplete.

## What's Changed
* IDMP-599 Adding UC2-CQ1 Amlodipine to sparql and unit tests. by @stsilva-osthus
* IDMP-371 - Add RIM related SPOR Referentials: Shelf Life Type and Special Precautions for Storage by @ElisaKendall
* GitHub-278 - hasSimplifiedMolecularInputLineEntrySpecification is misleading and inconsistent by @ElisaKendall
* Update spor-organisations.rqg for ORG-code property by @konradkrebs1411
* Update binding SPOR SMS by @aliariff
* IDMP-138 - Extension of Registration Authorities by @ElisaKendall
* IDMP-597 Revise therapeutic text by @tw-osthus
* Update spor-referentials.rqg by @konradkrebs1411
* IDMP-615 UC3-CQ2 SPARQL query by @tw-osthus
* IDMP-614 add route of administration by @tw-osthus
* Update EDQM transformation by @konradkrebs1411
* owl:sameAs added to ignored properties of test for deprecated properties by @mereolog
* IDMP-618 Augment Example Data for UC3 CQ 3 by @tw-osthus
* Mark out some OWL constraints as inappropriate for shaclisation by @mereolog
* IDMP-533 - Provide alignment/mapping for ISO "codedConcept" to the target IDMP-O Pattern for Reference Code Lists by @ElisaKendall
* GitHub-434 - cmns-ra:designates is equivalent to cmns-ra:isDesignatedBy by @ElisaKendall
* IDMP-633 - The definition of product role is too narrow by @ElisaKendall
* IDMP-636 - Extend the concept of structural representation in the ISO 11238 substances ontology to include molfile by @ElisaKendall
* improve competency questions by @MaFi2000
* Update GSRS for Molfile and cleanup by @konradkrebs1411
* IDMP-639 added other therapy specifics related by @tw-osthus
* Some missing unit tests added by @mereolog
* IDMP-642 - Integrate the latest revisions from the Commons ontologies, splitting parties and situations into two ontologies and renaming constituency to composition by @ElisaKendall
* IDMP-646 add CTCAE by @tw-osthus
* fix owl:class to owl:Class by @tw-osthus
* IDMP-650: Update SPOR URIs by @aliariff
* IDMP-533a - Provide alignment/mapping for ISO "codedConcept" to the target IDMP-O Pattern for Reference Code Lists by @ElisaKendall
* Fix to some typos in unit tests by @mereolog
* IDMP-GitHub-465 - idmp-spor:hasSPORTermDescription is language dependent by @ElisaKendall
* IDMP-647 moved MedDRA related concepts into separate ontology by @tw-osthus
* IDMP-635 - Augment the substance ontology with coverage for structurally diverse substances by @ElisaKendall
* IDMP-619 add UC3 CQ3 by @tw-osthus
* IDMP-650: Update SPOR URIs in EDQM by @aliariff
* Update unit_tests_run.yml to orchestrate cache rebuild by @mereolog
* GitHub-470 by @tw-osthus
* IDMP-641 add CDC - PHIN Race and Ethnicity with agencies by @tw-osthus
* IDMP-654 - Remove deprecated elements prior to 1.0 release by @ElisaKendall
* IDMP-655 - Revise the Commons ontologies and related changes for Commons 1.1 by @ElisaKendall
* Unit test extension for gsrs by @mereolog
* GitHub-478 fix namespace by @tw-osthus
* IDMP-643 add ISO 5128 representations of human sexes by @tw-osthus
* hasShelfLifeTimePeriod should expect a cmns-dt:Duration instead of cmns-dt:DatePeriod for medicinal products by @ElisaKendall
* Update IRIs in transformation scripts by @mereolog
* IDMP-656: Remove generated UUID in GSRS transformation by @aliariff
* IDMP-592 - Complete the preliminary modeling work required for Nucleic Acid, covering all detail provided in ISO 11238 by @ElisaKendall
* Some spelling typos fixed by @mereolog
* IDMP-638 add package item type by @tw-osthus
* IDMP-632 - Batch should be a subclass of Constituent rather than Product by @ElisaKendall
* IDMP-661 - Revise the Amlodipine example to match the current patterns for strength and reference strength by @ElisaKendall
* IDMP-662 - Revise the Terlipressin example to address hygiene issues by @ElisaKendall
* AboutIDMPDev-ReferenceIndividuals.rdf alignment with AboutIDMPDev.rdf by @ElisaKendall

## New Contributors
* @MaFi2000 made their first contribution

</details>

<details>
<summary>IDMP Ontology Release 0.4.0 (master_v0.4.0) - 2023-07-10</summary>

# IDMP Ontology Release 0.4.0

## Ontology Development in Details
A number of significant extensions were added in the Q2 0.4.0 release, including (1) the ability to answer new competency questions, (2) integration of additional data sources as well as improved use of existing sources for better question answering / mapping, (3) increased coverage more generally of some areas of the ISO standards, (4) integration of new examples, and (5) refinements to improve usability and address user feedback. Some of the major changes made include the following.

1. New Competency Question Answering - the primary additions in Q2 involved UC3 - Therapeutic Indications. See [UC3: Use Case Therapeutic Indication](https://wiki.edmcouncil.org/display/IDMP/UC3%3A+Use+Case+Therapeutic+Indication) for details. Preliminary coverage was added in Q2, and additional competency questions will be supported in Q3. Note that one of the more important changes with respect to question answering is that we now use the competency questions and sample answers as part of regression testing. Three of our example ontologies will be continuously updated in order to fully support this testing and provide examples that can be used by the pharma participants as good examples for mapping purposes: Amlodipine, Terlipressin, and the EU Clinical Trials example, all of which are in GitHub under /EXT/Examples.
 
1. Data Source Integration and Support – in Q2 we've added preliminary support for EDQM and have continued to improve mappings and support for GSRS and SPOR. Note that the IRIs in the SPOR data are not consistent with the guidelines for IRIs for use in RDF/OWL, so we have ongoing challenges there are representing the content on the Pistoia site as a work-around.
1. Increased Coverage of the ISO Standards – the main changes to the ontologies this quarter include completion of coverage of the forthcoming Annex L to the ISO 11238 implementation guide (ISO 19844) at the substance and chemical substance levels. We've also increased coverage of ISO 11615 with respect to ingredients and related concepts, which led to some of the renaming indicated by deprecated resources (which are mapped to their replacements). We also added some preliminary content for ISO 11239, Pharmaceutical Dose Forms, pending review of the revised standard once it is publicly available.
1. New Examples – The documentation includes a number of examples that are not covered in the ontology per se, but one new example ontology covers the Qlaira content from the EMA PMS Implementation Guide, Chapter 8. Existing examples have been extended as well, to include new content for testing the latest additions and updates in the ontologies.
1. Usability – see the detailed GitHub revisions for usability related revisions.

## Qualitative Comparison To Previous Release

### Overview
Three new ontologies were added:
1. StatisticalMeasures
1. ISO11238-Substances-DeprecatedElements
1. StructuredCollections

The following ontologies were changed:

Ontology Short Name | New Resources | Deleted Resources | Modified Resources
-- | -- | -- | --
AmlodipineExample | 9 | 4 | 14
ChangeManagement | 0 | 0 | 1
Documents | 0 | 0 | 1
EasternEuropeGovernmentEntitiesAndJurisdictions | 0 | 0 | 2
EUGovernmentEntitiesAndJurisdictions | 0 | 0 | 3
EuropeanUnionClinicalTrialsRegister | 0 | 0 | 1
ISO11238-RegistrationAuthorities | 6 | 0 | 2
ISO11238-Substances | 155 | 9 | 53
ISO11239-PharmaceuticalDoseForms | 18 | 0 | 4
ISO11615-MedicinalProducts | 42 | 0 | 42
ISO11616-PharmaceuticalProducts | 2 | 0 | 1
Organisations | 0 | 0 | 2
PartiesAndSituations | 0 | 0 | 1
ProductsAndServices | 0 | 0 | 20
QlairaExample | 74 | 74 | 1
QuantitiesAndUnits | 1 | 0 | 1
RegistrationAuthorities | 0 | 0 | 4
RegulatoryAgencies | 0 | 0 | 2
SubstancesProductsOrganisationsReferentials | 0 | 0 | 1
TerlipressinExample | 2 | 2 | 13
WesternEuropeGovernmentEntitiesAndJurisdictions | 0 | 0 | 1

## Deprecated Resources

The following 13 resources are considered as deprecated in 0.4.0.

https://spec.pistoiaalliance.org/idmp/ontology/ISO/ISO11238-RegistrationAuthorities/RegulatoryContext-FoodAndDrugAdministrationPatentExclusive
https://spec.pistoiaalliance.org/idmp/ontology/ISO/ISO11238-Substances/ActiveIngredientRole
https://spec.pistoiaalliance.org/idmp/ontology/ISO/ISO11238-Substances/AdjuvantRole
https://spec.pistoiaalliance.org/idmp/ontology/ISO/ISO11238-Substances/ExcipientRole
https://spec.pistoiaalliance.org/idmp/ontology/ISO/ISO11238-Substances/InactiveIngredientRole
https://spec.pistoiaalliance.org/idmp/ontology/ISO/ISO11238-Substances/IngredientRole
https://spec.pistoiaalliance.org/idmp/ontology/ISO/ISO11238-Substances/SubstanceConstituency
https://spec.pistoiaalliance.org/idmp/ontology/ISO/ISO11615-MedicinalProducts/hasActiveIngredientRole
https://spec.pistoiaalliance.org/idmp/ontology/ISO/ISO11615-MedicinalProducts/hasIngredientRole
https://spec.pistoiaalliance.org/idmp/ontology/ISO/ISO11615-MedicinalProducts/ProductConstituency
https://spec.pistoiaalliance.org/idmp/ontology/META/ChangeManagement/Specification
https://www.omg.org/spec/LCC/Countries/ISO3166-1-CountryCodes/L001
https://www.omg.org/spec/LCC/Countries/ISO3166-1-CountryCodes/Montenegrin

## What's Changed
* IDMP-466 - PhP and MI are disjoint classes by @ElisaKendall
* explicit json diff on failed unit test by @tw-osthus
* IDMP-512 - Need the concept of an ordered collection to define polymers by @ElisaKendall
* IDMP-483 - Complete the set of optional fields from Annex L: for Substance and Chemical Substance (excluding the reference information from Figure 16) by @ElisaKendall
* IDMP-525 - Release the ISO 11615 Medicinal Products Ontology by @ElisaKendall
* bugfix for `#344` by @tw-osthus
* Fix URL link by @aliariff
* IDMP-514 - Review and Correct the target role for GSRS "Active Moiety (Exclusivity)" used in Aripiprazole Lauroxil by @ElisaKendall
* IDMP-510 - Moiety has no restrictions for "moiety identifier" and "moiety name" by @ElisaKendall
* BugFix-346 - Ontology StructuredCollections.rdf by @ElisaKendall
* IDMP-531 - Add concepts for WHO case/demo e.g., release characteristics by @ElisaKendall
* GSRS: Avoid obsolete triples by @aliariff
* IDMP-528 - The definition of physical substance in the ISO 11238 ontology should correspond to the precise wording from paragraph 3.84 by @ElisaKendall
* IDMP-527 - Revise the CMNS/ProductsAndServices ontology to reflect the latest discussions with GS1 by @ElisaKendall
* IDMP-538 - Complete the definition of pharmaceutical dose form for the WHO demonstration by @ElisaKendall
* IDMP-549 - Augment the definition of pharmaceutical dose form with two additional properties by @ElisaKendall
* IDMP-304 - Complete the set of roles corresponding to the table in ISO/TS 20443, pages 112-113 (ingredient roles) by @ElisaKendall
* Update GSRS transformation script for Active Moiety (Exclusivity) by @aliariff
* IDMP-541 - Connect Manufactured Item and Pharmaceutical Product via Transformation by @ElisaKendall
* IDMP-542 - Add script to retrieve all EDQM lists by @aliariff
* IDMP-540 - Complete the set of optional fields from Annex L: for Substance and Chemical Substance for Modification (Figure 15) by @tw-osthus
* IDMP-539 Complete the set of optional fields from Annex L: for Substance and Chemical Substance for Figure 14 Information model for structure and isotope by @tw-osthus
* IDMP-417: Add test for GSRS by @aliariff
* IDMP-561 - Augment the IDMP ontologies to cover therapeutic indications by @tw-osthus
* IDMP-395 - Check definition for 'marketing authorization holder' by @ElisaKendall
* IDMP-522 - Complete the set of optional fields from Annex L: for Substance and Chemical Substance for Reference Information (Figure 16) by @ElisaKendall
* IDMP-581 The MedDRA individuals for the Amlodipine Example cause punning by @tw-osthus
* Legal punning in d9ececf commit in master by @ElisaKendall
* Add uuids to catalog files by @mereolog
* IDMP-550 - Document the modelling pattern for Marketing Authorization by @ElisaKendall

</details>

<details>
<summary>IDMP Ontology Release 0.3.0 (master_v0.3.0) - 2023-04-07</summary>

# IDMP Ontology Release 0.3.0

## Ontology Development in Details
This quarter the development team made significant progress in several key areas, including:
- Augmenting the ontologies to incorporate concepts and relationships needed to support Use Case 2 (UC-2), relating regulatory reporting requirements to the manufacturing side of the business, e.g., packaging concepts
- Refactoring some of our original work to address areas where shortcuts had been taken for Phase 1, such as to better address the relationship between products and their ingredients
- Refactoring to distinguish substance and product specifications from their physical counterparts
- Adding initial support for molecular entities, including molecules and atoms

The work also involved revising our original set of competency questions and adding new ones for UC-2 as well as increasing support for mappings to EMA SPOR. We also added a new example from the EMA PMS Implementation Guide, Chapter 8, for Qlaira. This particular example, which is mapped to SPOR, is important because the same medicinal product includes several pharmaceutical products.

## Qualitative Comparison To Previous Release

### Overview

One new ontology was added: **QlairaExample**.

No ontology was removed.

The following existing ontologies were changed:

Ontology Short Name | New Resources | Deleted Resources | Modified Resources
-- | -- | -- | --
AboutIDMPDev | 0 | 0 | 1
AboutIDMPDev-ReferenceIndividuals | 0 | 0 | 1
AboutIDMPProd | 0 | 0 | 1
AboutIDMPProd-ReferenceIndividuals | 0 | 0 | 1
AmlodipineExample | 37 | 4 | 11
ChangeManagement | 0 | 0 | 3
Documents | 4 | 0 | 1
EuropeanUnionClinicalTrialsRegister | 3 | 4 | 0
GovernmentEntities | 0 | 0 | 8
ISO11238-Substances | 51 | 6 | 52
ISO11239-PharmaceuticalDoseForms | 0 | 0 | 2
ISO11240-UnitsOfMeasurement | 1 | 0 | 1
ISO11615-MedicinalProducts | 26 | 1 | 27
MetadataEXT | 0 | 0 | 2
MetadataIDMP | 1 | 1 | 1
Organizations | 0 | 0 | 7
ProductsAndServices | 0 | 0 | 4
QuantitiesAndUnits | 1 | 0 | 0
RegistrationAuthorities | 0 | 1 | 3
RegulatoryAgencies | 0 | 0 | 2
SubstancesProductsOrganisationsReferentials | 20 | 1 | 5
TerlipressinExample | 12 | 5 | 12

### Details

(Tha last file is a json file - to see its contents use a json editor, e.g., https://jsonviewer.stack.hu)

## Deprecated Resources

The following resources were deprecated and may be deleted in v0.4.0 release:
https://spec.pistoiaalliance.org/idmp/ontology/ISO/ISO11238-Substances/ActiveIngredientRole
https://spec.pistoiaalliance.org/idmp/ontology/ISO/ISO11238-Substances/AdjuvantRole
https://spec.pistoiaalliance.org/idmp/ontology/ISO/ISO11238-Substances/ExcipientRole
https://spec.pistoiaalliance.org/idmp/ontology/ISO/ISO11238-Substances/InactiveIngredientRole
https://spec.pistoiaalliance.org/idmp/ontology/ISO/ISO11238-Substances/IngredientRole
https://spec.pistoiaalliance.org/idmp/ontology/ISO/ISO11238-Substances/SubstanceConstituency
https://spec.pistoiaalliance.org/idmp/ontology/ISO/ISO11615-MedicinalProducts/ProductConstituency
https://spec.pistoiaalliance.org/idmp/ontology/ISO/ISO11615-MedicinalProducts/hasActiveIngredientRole
https://spec.pistoiaalliance.org/idmp/ontology/ISO/ISO11615-MedicinalProducts/hasIngredientRole
https://spec.pistoiaalliance.org/idmp/ontology/META/ChangeManagement/Specification
https://www.omg.org/spec/LCC/Countries/ISO3166-1-CountryCodes/L001
https://www.omg.org/spec/LCC/Countries/ISO3166-1-CountryCodes/Montenegrin

## What's Changed
* single substance has max 1 molecular structure is wrong by @ElisaKendall
* Fix to ISO conformance level test by @mereolog
* IDMP-243 - stereochemisty by @tw-osthus
* IDMP-GitHub-284 - Notes on certain classes for structure, molecular structure, and stereochemistry are needed by @ElisaKendall
* IDMP-398 - Add concept for Marketing Status (SPOR RMS) by @ElisaKendall
* Competency questions split to one query per file by @mereolog
* Add more cleanup instructions for SPOR OMS transformation by @aliariff
* Update SPOR OMS Transformation by @aliariff
* IDMP-385: Update URI pattern by @aliariff
* IDMP-393 & IDMP-408: Add SPOR RMS Transformation by @aliariff
* IDMP 400 - GitHub action for competency questions run as unit tests by @mereolog
* IDMP-405 - Refactor the substance class hierarchy to differentiate actual physical substances from classifiers for substances by @ElisaKendall
* Update config files by @patrycjamia
* All competency questions run as unit tests by @mereolog
* IDMP-416 - Update Amlodipine Example (RDF file) by @ElisaKendall
* IDMP-415 - Update Terlipressin Example for reference strength (RDF) by @ElisaKendall
* IDMP-435 - Create classes for SSG1, SSG2, SSG3, SSG4 by @ElisaKendall
* IDMP viewer config files are updated by @mereolog
* Idmp 462: UC1 CQ Update by @stsilva-osthus
* IDMP-465 - Integrate revised manufactured item and packaging strategy for UC-2 by @ElisaKendall
* IDMP-436: Update SPOR SMS Transformation regarding SSG1 and SSG3 by @aliariff
* IDMP-473 - Integrate the Qlaira Example into our Test Suite by @ElisaKendall
* IDMP-433: Add idmp-sub:hasMoiety by @aliariff
* Idmp 462 Use Case 2 Competency Questions by @stsilva-osthus
* IDMP-479 - Further clean-up is needed to address remaining issues with the Qlaira example by @ElisaKendall
* New cqs added as unit tests by @mereolog

## New Contributors
* @tw-osthus made their first contribution

</details>

<details>
<summary>IDMP Ontology Release 0.2.0 (master_v0.2.0) - 2023-01-05</summary>

# Summary
This was a short quarter for us, as the Phase II project did not really get started in earnest until mid-November. The changes made during this period fell into several categories:
•	Commons ontology revisions – including alignment of those that have been released by the Object Management Group (OMG) with the formal specification and extension of the products and services ontology to incorporate GTINs, UPCs, and SKUs, and add organizations and in particular, government organizations together with jurisdictions for the EU (others will follow in 2023)
•	ISO IDMP ontology revisions – addressing some of the issues that came up during meetings in Boston, a very preliminary ontology for SPOR-related controlled vocabularies, the addition of some of the concepts required to answer competency questions related to UC-2, bridging the gap between regulatory and manufacturing, the addition of metadata annotations to enable clearer identification of deviations from the ISO standards in the ontologies, and additional restructuring needed to provide better semantics for substance-related concepts (which deviate from what is in the ISO standards, including new annotations)
•	Revision of the UC-1 SPARQL queries to align with the changes made to the ontologies
•	Revision of the GSRS transformation scripts to simplify them and align with changes to the ontologies
•	New mappings and transformations to support SPOR reference data (OMS and SMS)
•	New hygiene tests as a part of the infrastructure to address potential performance issues, including a new report to summarize deviations from the ISO standards using the new metadata annotations
•	Governance and Infrastructure configuration updates

# Detailed Description
## Category: Commons Ontology Library (CMNS)
Summary: This quarter, 11 of the ontologies included in the current CMNS ontologies were published as a formal standard by the Object Management Group (OMG). The current library in use by the IDMP project includes an additional 9 ontologies that we will work on standardizing at OMG in 2023 along with a subset of the jurisdictions that we hope to complete and promote at OMG by the end of this year. Most of them were originally part of the Financial Industry Business Ontology (FIBO), and well tested in that context. They are all quite general useful for many ontology projects in addition to the IDMP effort. We will be revising FIBO and other projects to leverage the same version of these ontologies that we promote at OMG, and will incorporate any new insights that come from the other projects that use them as appropriate.
Changes to the ontologies that are not yet standardized by OMG, incorporated this quarter, include extension of the products and services ontology to incorporate GTINs, UPCs, and SKUs, the addition of small ontologies for organizations and in particular, government organizations, a small locations ontology, and 7 new jurisdiction-specific ontologies covering the EU, United Kingdom, and Western Asia, as some countries in Western Asia are members of the Council of Europe. These jurisdiction-specific ontologies and others that we have yet to generalize from FIBO are needed to represent the various regulatory agencies required for IDMP.
## Category: ISO IDMP Ontologies
Summary: Shortly after the initial Phase I release closed, the ontology team met with some of our stakeholders in Boston for workshops after the Pistoia Alliance conference. Several questions came up during those discussions, some of which led to Jira issues that we have addressed since. One of those was that IDMP ontology users were generally confused by the way ingredients were modeled in the ontology, which has been refined with this release.
Another issue was that a number of our stakeholders understood the need to model various concepts differently in the ontology from their more relational representation in the IDMP standards, but wanted a way to highlight those differences and report them back to the ISO working group as potential areas for enhancement in the standards. A new ontology that provides annotations for various ways that an IDMP ontology might differ from the relevant ISO standard was added to the META partition, and we have initiated incorporation of those annotations where they are appropriate. We will perform a comprehensive review in Q1 to ensure that we have annotated all such deviations properly and using a new reporting capability discussed below under hygiene testing can run the report at any time to highlight the deviations for our users and to forward to ISO TC 215 as appropriate.
Yet another issue that was discussed in Boston had to do with the simplistic way jurisdictions were modeled in the Phase I ontology. We initiated work to address this in Q4 for the EU by (1) including EU-specific governments and jurisdictions in Commons as mentioned above, and (2) moving the EU-specific regulatory agencies and registration authorities from the current ISO 11238 Registration Authorities ontology to a couple of new jurisdiction-specific ontologies in a new European Jurisdiction partition of the ISO category. We expect to continue moving and expanding on the number and nature of regulatory agencies and registration authorities for other jurisdictions following a similar pattern over the coming months until we have good coverage for the rest of the planet. Jurisdictions are divided based on the United Nations’ M49 codes for continents and the countries that are located in those continents, as well as based on ISO 3166 countries and country subdivisions.
One of the main areas of work this quarter was the addition of the mapping to SPOR. Most of that work involved the mapping and transformations discussed below, though we added a new, small starting point ontology to capture some of the SPOR-specific controlled vocabularies. More of these will be added over the coming months.
Finally, we initiated work on changes to the ontologies to support our next set of competency questions related to bridging the gap between manufacturing and the regulatory areas of the pharmaceutical industry, as well as continuing a bit of restructuring of substance related concepts to provide more scientifically oriented semantics than is reflected in the ISO standards. The concepts that no longer conform to the standards are annotated using the new metadata annotations defined for that purpose.
## Category: Competency Questions (SPARQL Queries)
Summary: The primary changes made over the last several weeks involved streamlining the existing queries and revising them to reflect the latest revisions to the ontologies. Several additional queries were added to better reflect what is needed to answer the questions and to provide examples that the various pharma companies can use as examples for internal query and mapping efforts.
## Category: Mappings and Transformations
Summary: This quarter a significant effort was focused on the preliminary integration of the IDMP ontologies with data from the European Commission’s SPOR repository. This includes support for reference data from several SPOR repositories. Some preliminary work to generate content reflecting various SPOR-specific controlled vocabularies was included as a part of this initial effort, which will be aligned with the ontology as the vocabularies are mapped more completely in 2023. In addition to SPOR integration, the GSRS transformation scripts were updated to simplify them and align with changes to the ontologies.

## Classes being deprecated
The classes listed below are now deprecated and are likely to be deleted soon:
https://spec.pistoiaalliance.org/idmp/ontology/ISO/ISO11238-Substances/ActiveIngredientRole
https://spec.pistoiaalliance.org/idmp/ontology/ISO/ISO11238-Substances/AdjuvantRole
https://spec.pistoiaalliance.org/idmp/ontology/ISO/ISO11238-Substances/ExcipientRole
https://spec.pistoiaalliance.org/idmp/ontology/ISO/ISO11238-Substances/InactiveIngredientRole
https://spec.pistoiaalliance.org/idmp/ontology/ISO/ISO11238-Substances/IngredientRole
https://spec.pistoiaalliance.org/idmp/ontology/ISO/ISO11615-MedicinalProducts/hasActiveIngredientRole
https://spec.pistoiaalliance.org/idmp/ontology/ISO/ISO11615-MedicinalProducts/hasIngredientRole

## What's Changed - By Pull Request
* IDMP-GitHub-MaturityAlignment - Maturity Levels to About File Contents Alignment by @ElisaKendall
* Update config file by @patrycjamia
* IDMP-298 - Rename IngredientRole to Ingredient, including its subclasses by @ElisaKendall
* IDMP-CMNS-1.0 - Revise the Commons Ontology Library per OMG updates by @ElisaKendall
* IDMP-356: Simplify GSRS transformation scripts by @aliariff
* Fix typo by @aliariff
* IDMP-326 - Add the concept of a Global Trade Item Number (GTIN) by @ElisaKendall
* IDMP-235: Fix ChemblDatabase URI by @aliariff
* Sync GSRS transformation files by @aliariff
* Fix GSRS script for result generation by @aliariff
* IDMP-GitHub-228 - Nameless substances by @ElisaKendall
* Cq updates mvp.01 by @stsilva-osthus
* IDMP-305 - Update Ontology with jurisdiction concepts as discussed in Boston workshop by @ElisaKendall
* Update config by @patrycjamia
* IDMP-366: Add RIM related IDMP concept: Packaged Medicinal Product by @ElisaKendall
* IDMP-312: Add SPOR Substances Transformation by @aliariff
* Remove old GSRS sparql-gen scripts by @aliariff
* IDMP-GitHub-249 - Wrong versionIRI in ISO/EuropeanJurisdiction/EuropeanRegistrationAuthorities.rdf by @ElisaKendall
* New about and metadata files by @mereolog
* CQ00 by @stsilva-osthus
* IDMP-350: Add SPOR OMS Transformation by @aliariff
* Update MetadataISO with missing import statements by @mereolog
* IDMP-380 - Make "isStoichiometric" on chemical substances optional by @ElisaKendall
* IDMP-357 - Add EMA SPOR SMS 'substance domain' to the Substances ontology by @ElisaKendall
* IDMP-380 - Make "isStoichiometric" on chemical substances optional (reverse) by @ElisaKendall
* IDMP-367 - Include SKUs in IDMP-O by @ElisaKendall
* Adjust transformation for SPOR SMS by @aliariff
* Performance driven hygiene tests by @mereolog
* IDMP-390 - Add annotations to suggest changes to definitions that are needed in the IDMP standard by @ElisaKendall
* IDMP-348 - ISO conformance report as a hygiene test by @mereolog
* Update catalog-v001.xml to fix an obsolete Locations.rdf resolution by @mereolog
* IDMP-391 - The relationship between structure and structural representation should be better defined by @ElisaKendall
* IDMP-387 - Complete the set of terms required to answer UC-2, CQ-1 by @ElisaKendall

## New Contributors
* @aliariff made their first contribution

</details>

<details>
<summary>IDMP MVP Release 0.1.0 (master_v0.1.0) - 2022-10-03</summary>

# Release Summary
This release provides the very first draft of the IDMP Ontology together with a set of competency questions related to our first use case.

For this release we focused on substance identification at various stages of product life-cycle. We managed to develop the data architecture capable to answer the eight competency questions which concerns the use case whereby substances are identified in clinical trials as active ingredients of medicinal products:

# (New) Contributors
* @mereolog made their first contribution
* @ElisaKendall made their first contribution
* @trojczak made their first contribution
* @stsilva-osthus made their first contribution
* @patrycjamia made their first contribution

</details>

<!-- migrate-releases:release-notes:end -->
