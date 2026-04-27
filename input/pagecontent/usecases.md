### Service Definitions

This section clarifies the basic service definitions specified in the IG and provides the context in which they need to be used.

#### Pseudonymization 

Pseudonymization is the process by which PII/PHI can no longer be attributed to a specific patient without the use of additional information. Pseudonymization does not remove PII/PHI but rather it translates the information into a token. Pseudonymized data is still considered PII/PHI as it can be re-identified with a mapping key.

For example, Patient John Doe may be referred to as Patient_12345, which is produced by using some kind of mapping key or algorithm and can always be linked back to John Doe.
 

#### De-identified data 

Under the HIPAA privacy rule in 45 CFR §164.514(a), de-identified information is, “Health information that does not identify an individual and with respect to which there is no reasonable basis to believe that the information can be used to identify an individual.” 

Alternately, de-identification is the process of removing or transforming identifiers so that an individual cannot be readily identified, with a very low risk of re-identification. Note that there are de-identification use cases that may require re-identification with re-identification performed in controlled circumstances; re-identification is not part of this IG. 

For example, patient John Doe’s data will not include any patient identifier or name.


According to [HHS Safe Harbor Guidance](https://www.hhs.gov/hipaa/for-professionals/special-topics/de-identification/index.html), 18 different patient-related attributes should be removed for the data to be called de-identified data. These attributes that need to be removed are specified in the [HHS Safe Harbor De-identification Standard](https://www.hhs.gov/hipaa/for-professionals/special-topics/de-identification/index.html#standard) and are listed here for convenience. See the [standard](https://www.hhs.gov/hipaa/for-professionals/special-topics/de-identification/index.html#standard) for the full legal requirements.


* Names
* Addresses and geographic locations
* Dates
* Telephone numbers
* Fax numbers
* Email addresses
* Social Security numbers
* Medical Record numbers
* Health plan beneficiary numbers
* Account numbers
* Certificate/license numbers 
* Vehicle identifiers and license plate numbers
* Device Identifiers and serial numbers
* Web Universal Resource Locators (URLs)
* Internet Protocol (IP) addresses
* Biometric identifiers including finger and voice prints
* Full-face photographs and comparable images
* Any other unique identifying characteristic, code of the individual


##### Re-identification of de-identified information 

Re-identification uses a unique code assigned to the set of de-identified health information during the de-identification process to enable re-identification. The entity submitting the de-identified information is responsible for protecting the re-identification information as per organization, local, state and federal policies


#### Anonymization 

Anonymization is the irreversible process of transforming data so that individuals cannot be identified by any reasonably likely means, now or in the future. In other words, data is anonymous if individuals are not identifiable, taking into account all means “reasonably likely” to be used to identify the person. 

For example, John Doe, a male patient aged 56 with diabetes, would be included in an age group between 50 and 60 consisting of many individuals with diabetes who are males. Location information would be generalized from a specific address to a large geographical area such as one or more states or the entire country. Rare data points would be combined into a group such as “Other” to avoid identification.

The above definitions are used to create the necessary services to transform identifiable data into de-identified or anonymized data.


### Summary of differences between the various services

The table below summarizes the differences between the above three services


{% include ServiceCharacteristics.html %} 


### Business Need and Use Cases
The section identifies the business needs and specific user stories for DARTS IG.

#### Use Cases for De-identification 

**Use Case 1: Federal Agency Reporting:** 

Currently there are many reporting programs across the US where health care organizations submit data to state and federal agencies in aggregate form. While these aggregate reports meet current mandates, many agencies desire to obtain more detailed line-level information instead of aggregate data. However, in many instances the federal agency may not have the authorities necessary to receive PII/PHI data and therefore requires the data to be de-identified in order to receive more granular data. The following are the examples of such reporting

* Reporting from Federally Qualified Health Centers (FQHCs) to Federal Agencies

**Use Case 2: Clinical Research Reporting:** 

There are many research programs that require researchers to track a specific disease and treatment. For example, a researcher studying diabetes outcomes will require labs, medications, approximate timelines but will not require the identity of the individual. This requires PII/PHI to be de-identified and then submitted to the researcher. 

**Use Case 3: AI/ML Model to predict hospital readmissions**

As the use of AI/ML models increase new models are being created which need data to predict outcomes such as the number of hospital readmissions expected for the month. These AI models do not require identifiable information but require the clinical encounter information and the context of these encounters which can be achieved by de-identifying the information before submitting to the AI model.

**Use Case 4: Quality Improvement Initiatives** 

Quality improvement initiatives different from clinical research programs that are measuring treatment effectiveness and patient outcomes require line level granular data without identifiable information. De-identification is necessary before submission to these quality improvement programs. 


#### Use Cases for Anonymization 

**Use Case 1: Federal agencies publish disease Prevalence statistics:** 

Federal agencies collect data from the states and perform analysis and publish common data sets such as disease prevalence statistics in open data sets that can be used by the public. This requires anonymization of the data without re-identification risk.  

**Use Case 2: Datasets Released to Global Researchers:** 

Hospitals, aggregators and agencies may wish to release certain datasets to global researchers to enable innovations and studies. These data sets cannot have any re-identification risk and will require anonymization of the data before making the data set and releasing it to the global research community. 

**Use Case 3: Publications in Journals**

Publishing of data in journals requires only aggregated insights and does not require granular PHI/PII details. This can be achieved by anonymizing the data sets without risk of re-identification for studies and publications. 

**Use Case 4: Data Sharing with Third-Party Analytics Vendors** 

Many entities share data with third-party analytics vendors to examine population analytics and trends and create interventions based on analytics etc. These situations do not require PHI/PII as these data sets should avoid re-identification making anonymized data the appropriate form to submit to these vendors for analytics. 


### Use Cases Mapped to Services 

The table below summarizes the what services to consider for the different kind of use cases

{% include ServiceUsage.html %} 

### Actors and Definitions

This section contains a list of actors based on the above use cases.

#### DARTS Service Provider 

A DARTS Service Provider is an actor that implements the pseudonymization, de-identifciation and anonymization services defined in this implementation guide. Examples of these actors include cloud service providers such as Amazon, Microsoft.

#### DARTS Consumer

A DARTS Consumer is an actor who uses the services provided by the DARTS Service Provider. Examples of these actors include data submitters such as Health centers, Hospitals and their EHR systems. Data Receivers such as Federal agencies are also DARTS consumers as they use the DAPL IG and profiles to validate the information being received from data submitters.


### Identification Risk

The risk of identification when using the services defined in this IG has to be ascertained by the health care organization releasing or providing the data based on the use case. The following are links that provide valuable industry regulations and guidance for risk assessments

* [HHS HIPAA De-identification Guidance](https://www.hhs.gov/hipaa/for-professionals/special-topics/de-identification/index.html) 
* [NIST Guidance](https://www.nist.gov/itl/iad/deidentification) 
* [NIST IR 8053 for De-identification](https://csrc.nist.gov/pubs/ir/8053/final)


