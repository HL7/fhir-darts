This section provides an overview of the implementation guide.

### IG Purpose

Currently many federal reporting use cases use aggregate data reporting because they are not authorized to receive PHI/PII as part of the reports. However, there is a desire to use de-identified or anonymized information to generate more insights. This requires data submitters to effectively remove PHI/PII data before submission. Interest in more granular reporting without PHI/PII exists across agencies.In addition, there are research, quality improvement initiatives and AI/ML use cases that require de-identified and anonymized information. The following are some example programs that require these capabilities 

* Federal Agency Reporting

Read the <a href="usecases.html">Use Cases</a> section to get an idea of the various systems, actors and the data flow requirements. 

### Guiding Principles for the IG

The following are the guiding principles for the DARTS IG:

* Reduce EHR burden in generating the de-identified/anonymized data by providing a consistent representation of the data 
* Align with existing standards such as HL7 Fast Healthcare Interoperability Resources (FHIR) and USCDI and regulations such as ONC 2015 Edition, 2015 Edition Cures Update and Health Data, Technology, and Interoperability (HTI-1) Final Rule while improving the timeliness and completeness of data for the specified [Use Cases](usecases.html). 
 

### IG In-Scope Requirements

The following requirements are in-scope for the DARTS IG based on the use cases

* Define the service that can de-identify FHIR data using a policy identifier
* Define a mechanism to link de-identifeid data across data sources within an enterprise
* Define the service that can anonymize FHIR data.

### IG Out-of-Scope 

The following aspects are out-of-scope for the DARTS IG

* Risk assessment for the services specified by the DARTS FHIR IG
* Policies and processes followed by data submitters that allow data sharing, collecting of consent, or compliance with regulatory requirements.
* Mechanisms to identify the patients for whom the data needs to be de-identified or anonymized 

### Underlying Specifications

This guide is based on the [HL7 FHIR R4]({{site.data.fhir.path}}index.html) standard, and is aligned with [US Core IG]({{site.data.fhir.uscoreR4}}/index.html) profiles and terminology.

Implementers of the DARTS IG must understand some basic information about [HL7 FHIR R4]({{site.data.fhir.path}}index.html) and [US Core IG]({{site.data.fhir.uscoreR4}}/index.html) to successfully use the DARTS IG.

