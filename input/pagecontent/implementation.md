### Implementation Guidance with Examples

This page contains relevant guidance for a DARTS service provider to implement the DARTS services with examples. 

#### Identifiable Data to demonstrate the various DARTS services

The table below summarizes data from [US Core Example Bundle](Bundle-bundle-with-identifiable-date.html) that conforms to US Core profiles containing identifiable data in the Patient and Condition resources.
 

| First Name | Last Name | DOB | ZIP | Gender | Disease |
| --- | --- | --- | --- | --- | --- |
| John | Miller | 1932-02-14 | 03601 | male | Diabetes |
| Mary | Thompson | 1931-11-08 | 02532 | female | CKD |
| David | Carter | 1975-06-21 | 560001 | male | Diabetes |
| Susan | Reed | 1980-09-13 | 560014 | female | CKD |
| Michael | Hayes | 1968-01-30 | 560034 | male | Diabetes |
| Linda | Brooks | 1972-04-27 | 560076 | female | CKD |
| Robert | Jenkins | 1985-12-05 | 560099 | male | Diabetes |
| Patricia | Ward | 1990-07-19 | 90210 | female | CKD |
| James | Foster | 1978-03-11 | 30301 | male | CKD |
| Barbara | Collins | 1988-10-02 | 60614 | female | Diabetes |

##### Patient resource snippet showing identifiable data

```json
{
  "resourceType": "Patient",
  "id": "patient-01",
  "name": [
    {
      "use": "official",
      "family": "Miller",
      "given": ["John"]
    }
  ],
  "gender": "male",
  "birthDate": "1932-02-14",
  "address": [
    {
      "use": "home",
      "postalCode": "03601"
    }
  ]
}
```


#### Psuedonymization service implementation

This section shows how the identifiable data can be psuedonymized. This is just an example and not the actual implementation of the psuedonymize service. 

The table below summarizes data from [Psuedonymized Example Bundle](Bundle-bundle-with-psuedonymized-date.html) that has been psuedonymized using the patient's first name, last name, key="Test" and algorithm="SHA256". The original bundle used as an input to the psuedonymization process is the [US Core Example Bundle](Bundle-bundle-with-identifiable-date.html).

In the FHIR Patient resource, the first name and last name is remvoed and instead a psuedonym is added to the Patient.identifier field. Additional fields can be added in the creation of the psuedonym as needed. Psuedonymized data is still considered as identifiable data and is useful to to link patient data across data sources within an enterprise. 


| Pseudonym | DOB | ZIP | Gender | Disease |
| --- | --- | --- | --- | --- |
| 098587a439372c2877d8e59f1819e1642997c641792c34133333d764fca7cba6 | 1990-07-19 | 90210 | female | CKD |
| 1369392dcab866cce7ef22d60aa0b0e3c218c58e3c343f5fbd636ce30ac369f6 | 1931-11-08 | 02532 | female | CKD |
| 2295f099765aa28a9c0b9c041b23c6a49a24c1ef621da8d6cc106151015c0c5b | 1975-06-21 | 560001 | male | Diabetes |
| 9c270bdf290ab0d44faecf35be2777bcbefd66778480f4663d86740003dd092a | 1932-02-14 | 03601 | male | Diabetes |
| c1f0cee075c6e3c863e563eafec42e87b616de5c3fc4dab85071ddebc71e9ddd | 1968-01-30 | 560034 | male | Diabetes |
| caa8c5308dbb2e704aa4932b3dec241e168d4fadfa5a518caf4a20780c4f8d3e | 1972-04-27 | 560076 | female | CKD |
| d424f6489bd37379cb91d913565d17aa177010b694cf607c919e9855178ccd5c | 1985-12-05 | 560099 | male | Diabetes |
| db088eafefc824dc78e0c191539141a1d613ba94f601214d8089861cfab791ce | 1988-10-02 | 60614 | female | Diabetes |
| f3decbc702e525a8d80021022c41092f214c99fb1be50c4dd9377d53d2996dc5 | 1978-03-11 | 30301 | male | CKD |
| f7557a4583e382a02c6e282a5505107469150a4b6cc7facd667985c6858f9ee7 | 1980-09-13 | 560014 | female | CKD |

##### Patient resource showing psuedonymized data 

```json
{
  "resourceType": "Patient",
  "id": "patient-<derived>",
  "identifier": [
    {
      "system": "http://example.org/fhir/pseudonym",
      "value": "<sha256 pseudonym>"
    }
  ],
  "gender": "male",
  "birthDate": "1932-02-14",
  "address": [
    {
      "postalCode": "03601"
    }
  ]
}
```

##### Sample function to implement psuedonymization

```python
import hashlib

salt = "Test"
base = f"{first_name}|{last_name}|{date_of_birth}|{salt}"
pseudonym = hashlib.sha256(base.encode("utf-8")).hexdigest()

patient.pop("name", None)
patient["identifier"] = [{
    "system": "http://example.org/fhir/pseudonym",
    "value": pseudonym
}]
```

---


##### Candidate fields for psuedonymizing a Patient  Resource

We request feedback from vendors on the fields that should be considered for psuedonymizing a patient resource for the following use case

* An enterprise or health center may have multiple systems (EHRs) such as a clinical system, dental system and reports data separately from each system to a Federal agency. However, if the same patient is present in both systems, they would be reported multiple times. In order to help the data receiver to identify that the same patient is being reported multiple times when receiving de-identified data a psuedonym could be used. The following fields are candidates to create a psuedonym

* First name 
* Last name
* Gender 
* Date of Birth

##### Key and Algorithm values for psuedonymizing resources 

* Psuedonymization is done using a high entropy key that is protected so that it is not reversible and it is recomended to use a 4096 bit x509 certificate.

* For the algorithm selection, it is recommended to use one of the following algorithms

* SHA256
* RSA384

NOTE: Implementers can provide feedback on the algorithms and keys that could be used for creating the psuedonym.


#### De-identification service implementation

This section shows how the identifiable data can be de-identified. This is just an example and not the actual implementation of the de-identification service. 

The table below summarizes data from [De-identified Example Bundle conforming to DAPL IG](Bundle-dapl-deidentified-bundle.html) that has been de-identified using the HHS Safe Harbour method and are conformant to the DAPL IG. The original bundle used as an input to the de-identification process is the [US Core Example Bundle](Bundle-bundle-with-identifiable-date.html).


| Age | State | Country | Gender | Disease | Onset Year |
| --- | --- | --- | --- | --- | --- |
| 90 | MA | US | male | Diabetes | 2018 |
| 90 | CA | US | female | CKD | 2019 |
| 51 | TX | US | male | Diabetes | 2020 |
| 46 | FL | US | female | CKD | 2021 |
| 58 | WA | US | male | Diabetes | 2017 |
| 54 | CO | US | female | CKD | 2016 |
| 41 | IL | US | male | Diabetes | 2022 |
| 36 | AZ | US | female | CKD | 2015 |
| 48 | MA | US | male | CKD | 2014 |
| 38 | TN | US | female | Diabetes | 2023 |

##### Patient resource showing de-identified data 

```json
{
  "resourceType": "Patient",
  "meta": {
    "profile": [
      "http://hl7.org/fhir/us/dapl/StructureDefinition/dapl-deidentified-patient"
    ]
  },
  "gender": "male",
  "address": [
    {
      "state": "MA",
      "country": "US"
    }
  ],
  "extension": [
    {
      "url": "http://hl7.org/fhir/us/dapl/StructureDefinition/dapl-age-extension",
      "valueAge": {
        "value": 90,
        "unit": "years",
        "system": "http://unitsofmeasure.org",
        "code": "a"
      }
    }
  ]
}
```

##### Sample code to implement de-identification

```python
CURRENT_YEAR = 2026

patient.pop("identifier", None)
patient.pop("name", None)
patient.pop("birthDate", None)
patient.pop("text", None)

age = CURRENT_YEAR - int(original_birth_date[:4])

patient["meta"] = {
    "profile": [
        "http://hl7.org/fhir/us/dapl/StructureDefinition/dapl-deidentified-patient"
    ]
}
patient["extension"] = [{
    "url": "http://hl7.org/fhir/us/dapl/StructureDefinition/dapl-age-extension",
    "valueAge": {
        "value": 90 if age > 89 else age,
        "unit": "years",
        "system": "http://unitsofmeasure.org",
        "code": "a"
    }
}]

for addr in patient.get("address", []):
    addr.pop("line", None)
    addr.pop("city", None)
    addr.pop("postalCode", None)

condition["meta"] = {
    "profile": [
        "http://hl7.org/fhir/us/dapl/StructureDefinition/dapl-diagnosis"
    ]
}
condition.pop("asserter", None)
condition.pop("text", None)
condition["subject"].pop("display", None)
condition["onsetDateTime"] = condition["onsetDateTime"][:4]
```


##### List of changes done to the US Core Patient and Condition resources to de-identify

- removed identifiers and names
- removed date of birth completely
- added age through `dapl-age-extension`
- reduced address to state and country
- removed narrative text
- removed practitioner linkage
- reduced onset date to year only

---

#### Anonymization Service implementation

This section shows how the identifiable data can be anonymized. This is just an example and not the actual implementation of the anonymization service. 

The table below summarizes data from Anonymized Example Bundle conforming to DAPL IG that has been anonymized using the k-anonymity method and are conformant to the DAPL IG. The original bundle used as an input to the anonymization process is the [US Core Example Bundle](Bundle-bundle-with-identifiable-date.html).


| Age Band | Region | Disease Count |
| --- | --- | --- |
| 90+ | Region A | 2 Diabetes |
| 40–60 | Region B | 3 Diabetes |
| 40–60 | Region B | 2 CKD |
| 30–50 | Region C | 3 CKD |

##### Example code to implement anonymization

```python
from collections import Counter

aggregated = Counter()
for record in deidentified_records:
    key = (record["age_band"], record["region"], record["disease"])
    aggregated[key] += 1

anonymized_output = [
    {
        "Age Band": age_band,
        "Region": region,
        "Disease Count": f"{count} {disease}"
    }
    for (age_band, region, disease), count in aggregated.items()
]
```

##### List of changes done to the de-identifeid Patient and Condition resources to anonymize

- Grouped patients by age, region and disease
- Retrained only the counts at the group level and there is no line level information
