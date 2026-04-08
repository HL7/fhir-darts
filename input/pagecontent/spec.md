This section defines the specific requirements for systems wishing to conform to DARTS services specified in this IG.

### Context

#### Pre-reading
Before reading this formal specification, implementers should first be familiar with two other key portions of the specification:

* The [Use Cases](usecases.html) page provides the business context and general process flow enabled by the formal specification.

* The [Background](background.html#underlying-specifications) page provides information about the underlying specifications and indicates what portions of each should be reviewed in order to have the necessary foundation to understand the constraints and usage guidance described in this detailed specification.


#### Conventions
This implementation guide uses terminology and key words from [RFC 2119](https://datatracker.ietf.org/doc/html/rfc2119) to indicate conformance requirements.


#### Claiming Conformance 

Systems asserting conformance to this implementation guide have to implement the requirements outlined in the [DARTS Service Provider capability statement](CapabilityStatement-darts-service-provider.html). The following definition of MUST SUPPORT is to be used in the implementation of the requirements.

##### MUST SUPPORT Definition

* <span class="fhir-conformance">Systems SHALL be capable of populating data elements as specified by the profiles and data elements are returned using the specified APIs in the capability statement.</span>

* <span class="fhir-conformance">Systems SHALL be capable of processing resource instances containing the MUST SUPPORT data elements without generating an error or causing the application to fail.</span>


* <span class="fhir-conformance">Systems SHOULD be capable of displaying the MUST SUPPORT data elements for human use or storing it for other purposes.</span>

* <span class="fhir-conformance">In situations where information on a particular data element is not present and the reason for absence is unknown, Systems SHALL NOT include the data elements in the resource instance returned from executing the API requests.</span>

* <span class="fhir-conformance">When accessing de-identified or anonymized data, Systems SHALL interpret missing data elements within resource instances returned from API requests as data that has been removed as part of the de-identification and anonymization process.</span>


#### Profiles

This specification makes significant use of [FHIR profiles]({{site.data.fhir.path}}profiling.html), search parameter definitions, and terminology artifacts to describe the content to be shared as part of exchanging de-identified and anonymized information . The implementation guide is based on [FHIR R4]({{site.data.fhir.path}}) and profiles are listed for each interaction.

The full set of profiles defined in this implementation guide can be found by following the links on the [DARTS FHIR Artifacts](artifacts.html) page.


#### SMART on FHIR Backend Services Authorization

This section outlines how the SMART on FHIR Backend Services Authorization will be used by the DARTS implementation guide. 

* <span class="fhir-conformance">When conforming to the SMART Backend Services Authorization, System Actors SHALL include token_endpoint, scopes_supported, token_endpoint_auth_methods_supported and token_endpoint_auth_signing_alg_values_supported as defined in the [SMART on FHIR IG Backend Services]({{site.data.fhir.smartapplaunch}}/backend-services.html) specification.</span>

* <span class="fhir-conformance">When Systems act as clients, they SHOULD share their JSON Web Key Set (JWKS) with the server System Actors using Uniform Resource Locators (URLs) as defined in the [SMART on FHIR IG Backend Services]({{site.data.fhir.smartapplaunch}}/backend-services.html) specification.</span>

* <span class="fhir-conformance">Client System Actors SHALL obtain the access token as defined in the [SMART on FHIR Backend Services]({{site.data.fhir.smartapplaunch}}/backend-services.html) specification.</span>


#### System Actors, Requirements and Capability Statements

 
##### DARTS Service Provider Requirements

This section identifies the different requirements for DARTS Service Provider that provides psuedonymization, de-identification and anonymization services.

* <span class="fhir-conformance">The DARTS Service Provider SHALL support the de-identify operation for each type of resource identified in the DAPL IG.</span>

* <span class="fhir-conformance">The DARTS Service Provider SHALL create an identifier that is retained internally to link between identifiable and de-identifiable data.</span>

* <span class="fhir-conformance">The DARTS Service Provider SHALL remove all identifiable data using the profiles specified in the DAPL IG and create NDJSON data based on the IG profiles.</span>

* <span class="fhir-conformance">The DARTS Service Provider SHALL remove all data elements that are not identified as "SUPPORTED" in the DAPL profile definitions.</span>

**Implementation Note:** Common data elements which may have identifiable data have been explicitly mentioned in the profile with a cardinality of 0..0 which means they are not expected to be present. However other data elements which may be allowed in the resource may be included by the EHR including extensions. These additional data element and extensions that are not specified in the DAPL profiles have to be removed explicitly by the DARTS Service Provider implementation.

* <span class="fhir-conformance">The DARTS Service Provider SHALL implement the de-identification requirements as per the [HHS De-identification Guidance Deterministic method](https://www.hhs.gov/sites/default/files/ocr/privacy/hipaa/understanding/coveredentities/De-identification/hhs_deid_guidance.pdf).</span>

* <span class="fhir-conformance">When choosing to implement the de-identification method using safe harbor provisions from the HHS De-identification Guidance, DARTS Service Providers **SHALL** eliminate records related to the specific zip codes as specified in the guidance.</span>

 
