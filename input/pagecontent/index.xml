<div xmlns="http://www.w3.org/1999/xhtml" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://hl7.org/fhir ../../input-cache/schemas/R5/fhir-single.xsd">
  <!-- The spaces between the open and close "a" tag are mandatory.  (Cuz HTML renderers are dumb...) -->
    
  
  <a name="intro"> </a>
  <h3>Introduction</h3>
  <p>
  The health care industry has embraced FHIR as the standard for data exchange and has been implementing FHIR in the real-world as part of the various accelerators such as Argonaut, DaVinci, and Helios. The adoption of FHIR has been further expedited by the Assistant Secretary for Technology Policy (ASTP) and Centers for Medicare and Medicaid Services (CMS) regulations that require the implementation of FHIR for multiple use cases. One of the competing requirements that is emerging in the industry is the need for data that does not contain protected health information (PHI) or personally identifiable information (PII). These requirements are common among federal reporting use cases such as Health Resources and Services Administration (HRSA) Uniform Data System (UDS) reporting, public health reporting to Centers for Disease Control and Prevention (CDC), data needs for training artificial intelligence (AI) models, and data needs for research programs. This implementation guide creates a set of services that can de-identify, anonymize, and redact data represented by United States Core Data for Interoperability (USCDI) resources based on a policy identifier.
  </p>
  <p>
  This implementation guide (IG) defines the specifications by which federal agencies such as HRSA, Substance Abuse and Mental Health Administration (SAMHSA), and others can receive line level de-identified information and can publish anonymized datasets. The IG specifies services to
  <ul>
  <li><b>De-identify patient data based on a policy identifier</b></li>
  <li><b>Anonymize health care data sets using specific techniques</b></li>
  </ul>
  </p>
	
  <a name="walkthrough"> </a>
  <p>
    The main sections of this IG are:
  </p>
  <ul>
    <li>
      <a href="background.html">Background</a> - The page provides introduction and definitions for de-identification, pseudonymization, and anonymization.
    </li>
    <li>
      <a href="usecases.html">Use Cases</a> - Defines the  use case, workflows. actors and systems that will be used as part of the IG.
    </li>
    <li>
      <a href="spec.html">Formal Specification</a> - Defines the  formal specification in terms of requirements that need to be implemented by a service provider.
    </li>
    <li>
      <a href="artifacts.html">FHIR Artifacts</a> - Defines the FHIR artifacts for the IG.
    </li>
    <li>
      <a href="downloads.html">Downloads</a> - Allows downloading a copy of this implementation guide and other useful information
    </li>
  </ul>

  <a name="relationship"> </a>
	<h3>Relationship to other Implementation Guides</h3>
	<p>
	This section elaborates the relationship of this IG to other implementation guides.
        </p>
	<a name="us-core-relationship"> </a>
	<h4>Relationship to US Core Implementation Guide</h4>
	<p>
	This implementation guide, leverages terminology from US Core, and also uses US Core profiles to specify the inputs to the DARTS services. The outputs of DARTS services will be represented using profiles  specified in the DAPL IG.
        </p>
	<a name="dapl-relationship"> </a>
	<h4>Relationship to De-identified, Anonymized FHIR Profiles Library (DAPL) Implementation Guide</h4>
	<p>
	This DARTS IG complements the De-identified, Anonymized FHIR Profiles Library (DAPL) Implementation Guide by defining the services that implement techniques and algorithms for de-identification and anonymization, whereas the DAPL IG defines the set of profiles to represent the de-identified and anonymized information.
    </p>
    

    <div>
        <p>The following is a diagram that shows the relationship between US Core, DARTS IG and DAPL IG.</p>
  		<img src="darts-dapl-context.png" alt="US Core, DARTS and DAPL IG relationship diagram"/>
	</div>

	<br/>
    
	<a name="ds4p-relationship"> </a>
	<h4>Relationship to Data Segmentation for Privacy (DS4P) Implementation Guide</h4>
	<p>
	The DS4P IG provides guidance for applying security labels in FHIR that can be used to protect the privacy of patients' data. DARTS IG on the other hand aims to remove PHI/PII from the data and hence will not be using the DS4P tags currently.
    </p>
	<a name="udsplus-relationship"> </a>
	<h4>Relationship to HRSA UDS+ Implementation Guide</h4>
	<p>
	The HRSA UDS+ IG defines the specific content and APIs for federally-funded health centers to report data to HRSA annually. UDS+ will use services from the DARTS IG to create de-identified content and the DAPL IG profiles to represent de-identified content.
    </p>
</div>
