This section provides an overview of the Implementation Guide (IG).

### IG Purpose

Currently many Federal Reporting use cases use aggregate data reporting because they are not authorized to receive PHI/PII data as part of the reports. However there is a desire to use deidentified or anonymized information to generate more insights for the population at large. This requires data submitters to effectively remove PHI/PII data and submit non PHI/PII data to the agencies. This need for more granular information without PHI/PII exists across agencies. The following are some example programs that require these capabilities 

* HRSA's UDS+ Reporting

Read the <a href="usecases.html">Use Cases</a> section to get an idea of the various systems, actors and the data flow requirements. 

### Guiding Principles for the IG

The following are the guiding principles for the DARTS IG.

* Reduce EHR burden in generating the deidentified/anonymized data by providing a consistent representation of the data 
* Align with existing standards (e.g., Health Level 7 (HL7) Fast Healthcare Interoperability Resources (FHIR), and regulations (e.g., ONC 2015 Edition, 2015 Edition Cures Update, HTI1, HTI4), United States Core Data for Interoperability (USCDI) while improving the timeliness and completeness of data for the specified [Use Cases](usecases.html). 
 

### IG In-Scope Requirements

The following requirements are in-scope for the DARTS IG based on the use cases

* Define the service that can deidentify FHIR data using a policy identifier
* Define a mechanism to link deidentifeid data across data sources within an enterprise
* Define the service that can anonymize FHIR data.

### IG Out-of-Scope 

The following aspects are out-of-scope for the DARTS IG

* Risk Assessment for the services specified by the DARTS FHIR IG
* Policies and processes followed by Data Submitters which allow data sharing, collecting of consent, or compliance with regulatory requirements.
* Mechanisms to identify the patients for whom the data needs to be deidentified or anonymized 

### Underlying Specifications

This guide is based on the [HL7 FHIR R4]({{site.data.fhir.path}}index.html) standard, and is aligned with [US Core IG]({{site.data.fhir.uscoreR4}}/index.html) profiles and terminology.

Implementers of the DARTS IG must understand some basic information about the underlying specifications listed above.

