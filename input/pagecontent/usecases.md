### Service Definitions

This section clarifies the basic service definitions specified in the IG and provides the context in which they need to be used.

#### Psuedonymization 

Pseudonymization is the process by which PII/PHI can no longer be attributed to a specific patient without the use of additional information. Pseudonymization does not remove PII/PHI but rather it translates the information into a token. Pseudonymized data is still considered PII/PHI as it can be reidentified with a mapping key.

For example, Patient John Doe may be called as Patient_12345, which is produced by using some kind of mapping key or algorithm and is always linked back to John Doe.
 

#### De-identification 

Under the HIPAA privacy rule in 45 CFR §164.514(a), de-identified information is, “Health information that does not identify an individual and with respect to which there is no reasonable basis to believe that the information can be used to identify an individual.” 

Alternately, de-identification is the process of removing or transforming identifiers so that an individual cannot be readily identified, with a very low risk of re-identification. Note that there are de-identification use cases that may require re-identification with re-identification performed in controlled circumstances; re-identification is not part of this IG. 

For example, patient John Doe’s data will not have any patient identifier or name.


According to [HHS Safe Harbor Guidance](https://www.hhs.gov/hipaa/for-professionals/special-topics/de-identification/index.html), 18 different patient-related attributes should be removed for the data to be called de-identified data. These attributes that need to be removed are specified in the [HHS Safe Harbor De-identification Standard](https://www.hhs.gov/hipaa/for-professionals/special-topics/de-identification/index.html#standard) and are listed here for convenience.


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


##### Reidentification of de-identified information 

During the de-identification process, the assignment of a unique code to the set of de-identified health information to permit re-identification is the prescribed method of reidentifying information. The entity that is submitting the de-identified information is responsible to protect the reidentified information as per organization, local, state and federal policies.


#### Anonymization 

Anonymization is the irreversible process of transforming data so that individuals cannot be identified by any reasonably likely means, now or in the future. In other words, data is anonymous if individuals are not identifiable, taking into account all means “reasonably likely” to be used to identify the person. 

For example, John Doe a male patient, 56 and with diabetes needs to be included in a  data set. John Doe's record would be included in a data set without any identifying information such as names or date of birth; instead John Doe's record would be included in an age group between 50 and 60 consisting of many individuals with Diabetes who are males. Location information would be generalized from a specific address to a large geographical area such as one or more states or the entire country. The greater number of individuals with similar characteristics the lower the risk of identification. Rare data points would be combined into a group such as "Other" to avoid identification.


### Summary of differences between the various services

The table below summarizes the differences between the above three services


{% include ServiceCharacteristics.html %} 


### Business Need and Use Cases
The section identifies the business needs and specific user stories for DARTS IG.

#### Use Cases for De-identification 

**Use Case 1: Federal Agency Reporting:** 

Currently there are many reporting programs across the US where health care organizations submit data to state and federal agencies in aggregate form. While these aggregate reports meet current mandates, there is a desire to obtain more detailed line-level information instead of aggregate data. However, in many instances the federal agency may not have the authorities necessary to receive PII/PHI data and hence requires the data to be de-identified in order to receive more granular data. The following are the examples of such reporting

* UDS reporting from Federally Qualified Health Centers (FQHCs) to HRSA

**Use Case 2: Clinical Research Reporting:** 

There are many research programs that require researchers to track a specific disease and treatment. For example, a researcher studying diabetes outcomes will require labs, medications, approximate timelines but does not require the identity of the individual. This requires PII/PHI to be de-identified and then submitted to the researcher. 

**Use Case 3: AI/ML Model to predict hospital readmissions**

As the use of AI/ML models increase new models are being created which need data to predict outcomes such as the number of hospital readmissions expected for the month. These AI models do not require identifiable information but require the clinical encounter information and the context of these encounters which can be achieved by de-identifying the information before submitting to the AI model.

**Use Case 4: Quality Improvement Initiatives** 

Quality improvement initiatives different from clinical research programs that are measuring treatment effectiveness, patient outcomes require line level granular data without identifiable information and de-identification is necessary before submission to these quality improvement programs. 


#### Use Cases for Anonymization 

**Use Case 1: Federal Agency published Disease Prevalance statistics:** 

Federal agencies collect data from the states and perform analysis and publish common data sets such as disease prevalence statistics that are an open data set and can be used by the public. This requires anonymization of the data without reidentification risk.  

**Use Case 2: Datasets Released to Global Researchers:** 

Hospitals, aggregators, agencies may wish to release certain datasets to global researchers to enable innovations and studies. These data sets cannot have any reidentification risk and will require anonymization of the data before making the data set and releasing it to the global research community. 

**Use Case 3: Journal Publications**

Publishing of data in journals requires only aggregated insights and does not require granular PHI/PII details. This can be achieved by anonymizing the datasets without risk of reidentification for studies and publications. 

**Use Case 4: Data Sharing with Third Party Analytics Vendors** 

Many entities share data with third party analytics vendors to examine population analytics and trends and create interventions based on analytics etc. These situations do not require PHI/PII and the data set should avoid reidentification and hence anonymized data is required to be submitted to these vendors for analytics. 


### Use Cases Mapped to Services 

The table below summarizes the what services to consider for the different kind of use cases

{% include ServiceUsage.html %} 


### Identification Risk

The risk of identification when using the above services has to be ascertained by the healthcare organization releasing or providing the data based on the use case. The following are links that provide valuable industry regulations and guidance for risk assessments

* [HHS HIPAA De-identification Guidance](https://www.hhs.gov/hipaa/for-professionals/special-topics/de-identification/index.html) 
* [NIST Guidance](https://www.nist.gov/itl/iad/deidentification) 
* [NIST IR 8053 for De-identification](https://csrc.nist.gov/pubs/ir/8053/final)


