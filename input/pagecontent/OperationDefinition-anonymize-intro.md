{:.stu-note}
All canonical (Official) URLs will be changed in the future and are not available currently on the web.

### Introduction

The anonymize operation is to be used to anonymize the data containing PHI/PII. The approach for anonymization is left to the DARTS service provider.

* The operation takes a [List of Resource URLs](StructureDefinition-darts-operation-data-urls-parameter.html) that points to identifiable data in NDJSON format and will return back a set of links to NDJSON files that contains the anonymized data. 

* The operation uses the FHIR Async operation pattern documented in the [FHIR Async Specification](https://hl7.org/fhir/R4/async.html)