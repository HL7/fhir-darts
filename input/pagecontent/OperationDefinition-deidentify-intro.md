{:.stu-note}
All canonical (Official) URLs will be changed in the future and are not available currently on the web.

### Introduction

The de-identify operation is to be used to de-identify the data containing PHI/PII. The approach for de-identification is based on policy identifiers.

* Currently the supported Policy Identifiers is based on HHS Safe Harbor Guidance which removes 18 different identifiable attributes from the input data.

* The operation takes a [List of Resource URLs](StructureDefinition-darts-operation-data-urls-parameter.html) that points to identifiable data in NDJSON format and will return back a set of links to NDJSON files that does not contain the identifiable data. 

* The operation uses the FHIR Async operation pattern documented in the [FHIR Async Specification](https://hl7.org/fhir/R4/async.html)