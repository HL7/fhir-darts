{:.stu-note}
All canonical (Official) URLs will be changed in the future and are not available currently on the web.

### Introduction

This operation psuedonymizes data containing PHI/PII.

* The operation takes a key and algorithm to be used for psuedonymization. 

* The operation takes a [List of Resource URLs](StructureDefinition-darts-operation-data-urls-parameter.html) that points to identifiable data in NDJSON format and will return back a set of links to NDJSON files that contains the psuedonymized data. 

* The operation also takes a salt or key to be used for creating the psuedonym

*The algorithm to be used for psuedonymization can be specified by the consumer of the service. Examples of algorithms that can be used are SHA256, RSA384.

* The operation uses the FHIR Async operation pattern documented in the [FHIR Async Specification](https://hl7.org/fhir/R4/async.html)