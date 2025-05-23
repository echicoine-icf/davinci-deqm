
#### Examples
{:.no_toc}

**Scenario:**

A Client would like to know if the patient, *gaps-patient01*, has any open, closed, or prospective gaps for the colorectal cancer screening measure and the cervical cancer screening measure for the period from 2020-01-01 to 2020-12-31. The Client requested a Gaps in Care Report from a Server's system on 2020-06-30.

**GET Gaps in Care Report**


```
GET [base]/Measure/$care-gaps?measureurl=http://hl7.org/fhir/us/davinci-deqm/Measure/measure-exm130-example|2.0.0&measureurl=http://hl7.org/fhir/us/davinci-deqm/Measure/measure-exm124-example|2.0.0&subject=Patient/gaps-patient01&periodStart=2020-01-01&periodEnd=2020-12-31&status=open-gap&status=closed-gap&status=prospective-gap
```

**Request body**
~~~
(Note that request body is not applicable in this example)
~~~

**Response**

~~~
HTTP/1.1 200
Date: Wed, 22 July 2020 01:02:06 GMT
Content-Type: application/fhir+json;charset=UTF-8
...Other Headers...

{
  "resourceType": "Bundle",
  "id": "single-gaps-open-indv-report01",
  "meta": {
    "profile": [
      "http://hl7.org/fhir/us/davinci-deqm/StructureDefinition/gaps-bundle-deqm"
    ]
  },
  "identifier": {
    "system": "urn:ietf:rfc:3986",
    "value": "urn:uuid:77f43ef5-8c60-4222-ae58-36969063a093"
  },
  "type": "document",
  "timestamp": "2020-06-30T13:08:53+00:00",
  "entry": [{
      "fullUrl": "http://example.org/fhir/gaps/Composition/gaps-composition01",
      "resource": {
        "resourceType": "Composition",
        "id": "gaps-composition01",
        "meta": {
          "profile": [
            "http://hl7.org/fhir/us/davinci-deqm/StructureDefinition/gaps-composition-deqm"
          ]
        },
        "status": "final",
        "type": {
          "coding": [{
              "system": "http://loinc.org",
              "code": "96315-7",
              "display": "Gaps in care report"
            }
          ]
        },
        "subject": {
          "reference": "Patient/gaps-patient01"
        },
        "date": "2020-06-30T13:08:53+00:00",
        "author": [{
            "reference": "Organization/gaps-organization-reportingvendor"
          }
        ],
        "title": "Care Gap Report for patient gaps-patient01",
        "section": [{
            "title": "Colorectal Cancer Screening",
            "focus": {
              "reference": "MeasureReport/gaps-indv-measurereport01"
            },
            "entry": [{
                "reference": "DetectedIssue/gaps-detectedissue01"
              }
            ]
          }, {
            "title": "Cervical Cancer Screening",
            "focus": {
              "reference": "MeasureReport/gaps-indv-measurereport02"
            },
            "entry": [{
                "reference": "DetectedIssue/gaps-detectedissue02"
              }
            ]
          }, {
            "title": "MRP Cancer Screening",
            "focus": {
              "reference": "MeasureReport/gaps-indv-measurereport03"
            },
            "entry": [{
                "reference": "DetectedIssue/gaps-detectedissue03"
              }
            ]
          }
        ]
      }
    }, {
      "fullUrl": "http://example.org/fhir/gaps/MeasureReport/gaps-indv-measurereport01",
      "resource": {
        "resourceType": "MeasureReport",
        "id": "gaps-indv-measurereport01",
        "meta": {
          "profile": [
            "http://hl7.org/fhir/us/davinci-deqm/StructureDefinition/indv-measurereport-deqm"
          ]
        },
        "extension": [{
            "url": "http://hl7.org/fhir/us/davinci-deqm/StructureDefinition/extension-measureScoring",
            "valueCodeableConcept": {
              "coding": [{
                  "system": "http://terminology.hl7.org/CodeSystem/measure-scoring",
                  "code": "proportion"
                }
              ]
            }
          }, {
            "url": "http://hl7.org/fhir/us/davinci-deqm/StructureDefinition/extension-certificationIdentifier",
            "valueIdentifier": {
              "system": "urn:oid:2.16.840.1.113883.3.2074.1",
              "value": "0015HQN9BD3304E"
            }
          }, {
            "url": "http://hl7.org/fhir/us/davinci-deqm/StructureDefinition/extension-reportingVendor",
            "valueReference": {
              "reference": "Organization/gaps-organization-reportingvendor"
            }
          }
        ],
        "status": "complete",
        "type": "individual",
        "measure": "http://hl7.org/fhir/us/davinci-deqm/Measure/measure-exm130-example",
        "subject": {
          "reference": "Patient/gaps-patient01"
        },
        "date": "2020-06-30T13:08:52+00:00",
        "reporter": {
          "reference": "Organization/organization01"
        },
        "period": {
          "start": "2020-01-01T00:00:00+00:00",
          "end": "2020-12-31T00:00:00+00:00"
        },
        "improvementNotation": {
          "coding": [{
              "system": "http://terminology.hl7.org/CodeSystem/measure-improvement-notation",
              "code": "increase"
            }
          ]
        },
        "group": [{
            "id": "group-exm130",
            "population": [{
                "code": {
                  "coding": [{
                      "system": "http://terminology.hl7.org/CodeSystem/measure-population",
                      "code": "initial-population",
                      "display": "Initial Population"
                    }
                  ]
                },
                "count": 1
              }, {
                "code": {
                  "coding": [{
                      "system": "http://terminology.hl7.org/CodeSystem/measure-population",
                      "code": "numerator",
                      "display": "Numerator"
                    }
                  ]
                },
                "count": 0
              }, {
                "code": {
                  "coding": [{
                      "system": "http://terminology.hl7.org/CodeSystem/measure-population",
                      "code": "denominator",
                      "display": "Denominator"
                    }
                  ]
                },
                "count": 1
              }, {
                "code": {
                  "coding": [{
                      "system": "http://terminology.hl7.org/CodeSystem/measure-population",
                      "code": "denominator-exclusion",
                      "display": "Denominator Exclusion"
                    }
                  ]
                },
                "count": 0
              }
            ],
            "measureScore": {
              "value": 0.0
            }
          }
        ],
        "evaluatedResource": [{
            "extension": [{
                "url": "http://hl7.org/fhir/us/davinci-deqm/StructureDefinition/extension-criteriaReference",
                "valueString": "initial-population"
              }
            ],
            "reference": "Encounter/gaps-encounter01"
          }, {
            "extension": [{
                "url": "http://hl7.org/fhir/us/davinci-deqm/StructureDefinition/extension-criteriaReference",
                "valueString": "initial-population"
              }
            ],
            "reference": "Patient/gaps-patient01"
          }
        ]
      }
    }, {
      "fullUrl": "http://example.org/fhir/gaps/MeasureReport/gaps-indv-measurereport02",
      "resource": {
        "resourceType": "MeasureReport",
        "id": "gaps-indv-measurereport02",
        "meta": {
          "profile": [
            "http://hl7.org/fhir/us/davinci-deqm/StructureDefinition/indv-measurereport-deqm"
          ]
        },
        "extension": [{
            "url": "http://hl7.org/fhir/us/davinci-deqm/StructureDefinition/extension-measureScoring",
            "valueCodeableConcept": {
              "coding": [{
                  "system": "http://terminology.hl7.org/CodeSystem/measure-scoring",
                  "code": "proportion"
                }
              ]
            }
          }, {
            "url": "http://hl7.org/fhir/us/davinci-deqm/StructureDefinition/extension-certificationIdentifier",
            "valueIdentifier": {
              "system": "urn:oid:2.16.840.1.113883.3.2074.1",
              "value": "0015HQN9BD3304E"
            }
          }, {
            "url": "http://hl7.org/fhir/us/davinci-deqm/StructureDefinition/extension-reportingVendor",
            "valueReference": {
              "reference": "Organization/gaps-organization-reportingvendor"
            }
          }
        ],
        "status": "complete",
        "type": "individual",
        "measure": "http://hl7.org/fhir/us/davinci-deqm/Measure/measure-exm124-example",
        "subject": {
          "reference": "Patient/gaps-patient01"
        },
        "date": "2020-07-02T13:08:52+00:00",
        "reporter": {
          "reference": "Organization/organization01"
        },
        "period": {
          "start": "2020-01-01T00:00:00+00:00",
          "end": "2020-12-31T00:00:00+00:00"
        },
        "improvementNotation": {
          "coding": [{
              "system": "http://terminology.hl7.org/CodeSystem/measure-improvement-notation",
              "code": "increase"
            }
          ]
        },
        "group": [{
            "id": "group-exm124",
            "population": [{
                "code": {
                  "coding": [{
                      "system": "http://terminology.hl7.org/CodeSystem/measure-population",
                      "code": "initial-population",
                      "display": "Initial Population"
                    }
                  ]
                },
                "count": 1
              }, {
                "code": {
                  "coding": [{
                      "system": "http://terminology.hl7.org/CodeSystem/measure-population",
                      "code": "numerator",
                      "display": "Numerator"
                    }
                  ]
                },
                "count": 0
              }, {
                "code": {
                  "coding": [{
                      "system": "http://terminology.hl7.org/CodeSystem/measure-population",
                      "code": "denominator",
                      "display": "Denominator"
                    }
                  ]
                },
                "count": 1
              }, {
                "code": {
                  "coding": [{
                      "system": "http://terminology.hl7.org/CodeSystem/measure-population",
                      "code": "denominator-exclusion",
                      "display": "Denominator Exclusion"
                    }
                  ]
                },
                "count": 0
              }
            ],
            "measureScore": {
              "value": 0.0
            }
          }
        ],
        "evaluatedResource": [{
            "extension": [{
                "url": "http://hl7.org/fhir/us/davinci-deqm/StructureDefinition/extension-criteriaReference",
                "valueString": "initial-population"
              }, {
                "url": "http://hl7.org/fhir/us/davinci-deqm/StructureDefinition/extension-criteriaReference",
                "valueString": "denominator"
              }
            ],
            "reference": "Encounter/gaps-encounter01"
          }, {
            "extension": [{
                "url": "http://hl7.org/fhir/us/davinci-deqm/StructureDefinition/extension-criteriaReference",
                "valueString": "initial-population"
              }, {
                "url": "http://hl7.org/fhir/us/davinci-deqm/StructureDefinition/extension-criteriaReference",
                "valueString": "denominator"
              }
            ],
            "reference": "Patient/gaps-patient01"
          }
        ]
      }
    }, {
      "fullUrl": "http://example.org/fhir/gaps/MeasureReport/gaps-indv-measurereport03",
      "resource": {
        "resourceType": "MeasureReport",
        "id": "gaps-indv-measurereport03",
        "meta": {
          "profile": [
            "http://hl7.org/fhir/us/davinci-deqm/StructureDefinition/indv-measurereport-deqm"
          ]
        },
        "extension": [{
            "url": "http://hl7.org/fhir/us/davinci-deqm/StructureDefinition/extension-measureScoring",
            "valueCodeableConcept": {
              "coding": [{
                  "system": "http://terminology.hl7.org/CodeSystem/measure-scoring",
                  "code": "proportion"
                }
              ]
            }
          }, {
            "url": "http://hl7.org/fhir/us/davinci-deqm/StructureDefinition/extension-certificationIdentifier",
            "valueIdentifier": {
              "system": "urn:oid:2.16.840.1.113883.3.2074.1",
              "value": "0015HQN9BD3304E"
            }
          }, {
            "url": "http://hl7.org/fhir/us/davinci-deqm/StructureDefinition/extension-reportingVendor",
            "valueReference": {
              "reference": "Organization/gaps-organization-reportingvendor"
            }
          }
        ],
        "status": "complete",
        "type": "individual",
        "measure": "http://hl7.org/fhir/us/davinci-deqm/Measure/measure-mrp-example",
        "subject": {
          "reference": "Patient/gaps-patient01"
        },
        "date": "2020-07-02T13:08:52+00:00",
        "reporter": {
          "reference": "Organization/organization01"
        },
        "period": {
          "start": "2020-01-01T00:00:00+00:00",
          "end": "2020-12-31T00:00:00+00:00"
        },
        "improvementNotation": {
          "coding": [{
              "system": "http://terminology.hl7.org/CodeSystem/measure-improvement-notation",
              "code": "increase"
            }
          ]
        },
        "group": [{
            "population": [{
                "code": {
                  "coding": [{
                      "system": "http://terminology.hl7.org/CodeSystem/measure-population",
                      "code": "initial-population",
                      "display": "Initial Population"
                    }
                  ]
                },
                "count": 1
              }, {
                "code": {
                  "coding": [{
                      "system": "http://terminology.hl7.org/CodeSystem/measure-population",
                      "code": "numerator",
                      "display": "Numerator"
                    }
                  ]
                },
                "count": 0
              }, {
                "code": {
                  "coding": [{
                      "system": "http://terminology.hl7.org/CodeSystem/measure-population",
                      "code": "denominator",
                      "display": "Denominator"
                    }
                  ]
                },
                "count": 1
              }, {
                "code": {
                  "coding": [{
                      "system": "http://terminology.hl7.org/CodeSystem/measure-population",
                      "code": "denominator-exclusion",
                      "display": "Denominator Exclusion"
                    }
                  ]
                },
                "count": 0
              }
            ],
            "measureScore": {
              "value": 0.0
            }
          }
        ],
        "evaluatedResource": [{
            "extension": [{
                "url": "http://hl7.org/fhir/us/davinci-deqm/StructureDefinition/extension-criteriaReference",
                "valueString": "initial-population"
              }, {
                "url": "http://hl7.org/fhir/us/davinci-deqm/StructureDefinition/extension-criteriaReference",
                "valueString": "denominator"
              }
            ],
            "reference": "Encounter/gaps-encounter01"
          }, {
            "extension": [{
                "url": "http://hl7.org/fhir/us/davinci-deqm/StructureDefinition/extension-criteriaReference",
                "valueString": "initial-population"
              }, {
                "url": "http://hl7.org/fhir/us/davinci-deqm/StructureDefinition/extension-criteriaReference",
                "valueString": "denominator"
              }
            ],
            "reference": "Patient/gaps-patient01"
          }
        ]
      }
    }, {
      "fullUrl": "http://example.org/fhir/gaps/DetectedIssue/gaps-detectedissue01",
      "resource": {
        "resourceType": "DetectedIssue",
        "id": "gaps-detectedissue01",
        "meta": {
          "profile": [
            "http://hl7.org/fhir/us/davinci-deqm/StructureDefinition/gaps-detectedissue-deqm"
          ]
        },
        "modifierExtension": [{
            "url": "http://hl7.org/fhir/us/davinci-deqm/StructureDefinition/extension-gapStatus",
            "valueCodeableConcept": {
              "coding": [{
                  "system": "http://hl7.org/fhir/us/davinci-deqm/CodeSystem/gaps-status",
                  "code": "closed-gap"
                }
              ]
            }
          }
        ],
        "status": "final",
        "code": {
          "coding": [{
              "system": "http://terminology.hl7.org/CodeSystem/v3-ActCode",
              "code": "CAREGAP",
              "display": "Care Gaps"
            }
          ]
        },
        "patient": {
          "reference": "Patient/gaps-patient01"
        },
        "evidence": [{
            "detail": [{
                "reference": "MeasureReport/gaps-indv-measurereport01"
              }
            ]
          }
        ]
      }
    }, {
      "fullUrl": "http://example.org/fhir/gaps/DetectedIssue/gaps-detectedissue02",
      "resource": {
        "resourceType": "DetectedIssue",
        "id": "gaps-detectedissue02",
        "meta": {
          "profile": [
            "http://hl7.org/fhir/us/davinci-deqm/StructureDefinition/gaps-detectedissue-deqm"
          ]
        },
        "modifierExtension": [{
            "url": "http://hl7.org/fhir/us/davinci-deqm/StructureDefinition/extension-gapStatus",
            "valueCodeableConcept": {
              "coding": [{
                  "system": "http://hl7.org/fhir/us/davinci-deqm/CodeSystem/gaps-status",
                  "code": "closed-gap"
                }
              ]
            }
          }
        ],
        "status": "final",
        "code": {
          "coding": [{
              "system": "http://terminology.hl7.org/CodeSystem/v3-ActCode",
              "code": "CAREGAP",
              "display": "Care Gaps"
            }
          ]
        },
        "patient": {
          "reference": "Patient/gaps-patient01"
        },
        "evidence": [{
            "detail": [{
                "reference": "MeasureReport/gaps-indv-measurereport02"
              }
            ]
          }
        ]
      }
    }, {
      "fullUrl": "http://example.org/fhir/gaps/DetectedIssue/gaps-detectedissue03",
      "resource": {
        "resourceType": "DetectedIssue",
        "id": "gaps-detectedissue03",
        "meta": {
          "profile": [
            "http://hl7.org/fhir/us/davinci-deqm/StructureDefinition/gaps-detectedissue-deqm"
          ]
        },
        "modifierExtension": [{
            "url": "http://hl7.org/fhir/us/davinci-deqm/StructureDefinition/extension-gapStatus",
            "valueCodeableConcept": {
              "coding": [{
                  "system": "http://hl7.org/fhir/us/davinci-deqm/CodeSystem/gaps-status",
                  "code": "prospective-gap"
                }
              ]
            }
          }
        ],
        "status": "final",
        "code": {
          "coding": [{
              "system": "http://terminology.hl7.org/CodeSystem/v3-ActCode",
              "code": "CAREGAP",
              "display": "Care Gaps"
            }
          ]
        },
        "patient": {
          "reference": "Patient/gaps-patient01"
        },
        "evidence": [{
            "detail": [{
                "reference": "MeasureReport/gaps-indv-measurereport03"
              }
            ]
          }
        ]
      }
    }, {
      "fullUrl": "http://example.org/fhir/gaps/Encounter/gaps-encounter01",
      "resource": {
        "resourceType": "Encounter",
        "id": "gaps-encounter01",
        "meta": {
          "profile": [
            "http://hl7.org/fhir/us/core/StructureDefinition/us-core-encounter"
          ]
        },
        "status": "finished",
        "class": {
          "system": "http://terminology.hl7.org/CodeSystem/v3-ActCode",
          "code": "AMB",
          "display": "ambulatory"
        },
        "type": [{
            "coding": [{
                "system": "http://www.ama-assn.org/go/cpt",
                "code": "99201",
                "display": "Office or other outpatient visit for the evaluation and management of a new patient, which requires these 3 key components: A problem focused history; A problem focused examination; Straightforward medical decision making. Counseling and/or coordination of care with other physicians, other qualified health care professionals, or agencies are provided consistent with the nature of the problem(s) and the patient's and/or family's needs. Usually, the presenting problem(s) are self limited or minor. Typically, 10 minutes are spent face-to-face with the patient and/or family."
              }
            ]
          }
        ],
        "subject": {
          "reference": "Patient/gaps-patient01"
        },
        "period": {
          "start": "2020-05-30T00:00:00-00:00",
          "end": "2020-05-31T00:00:00-00:00"
        }
      }
    }, {
      "fullUrl": "http://example.org/fhir/gaps/Patient/gaps-patient01",
      "resource": {
        "resourceType": "Patient",
        "id": "gaps-patient01",
        "meta": {
          "profile": [
            "http://hl7.org/fhir/us/core/StructureDefinition/us-core-patient"
          ]
        },
        "extension": [{
            "extension": [{
                "url": "ombCategory",
                "valueCoding": {
                  "system": "urn:oid:2.16.840.1.113883.6.238",
                  "code": "2028-9",
                  "display": "Asian"
                }
              }, {
                "url": "text",
                "valueString": "Asian"
              }
            ],
            "url": "http://hl7.org/fhir/us/core/StructureDefinition/us-core-race"
          }, {
            "extension": [{
                "url": "ombCategory",
                "valueCoding": {
                  "system": "urn:oid:2.16.840.1.113883.6.238",
                  "code": "2135-2",
                  "display": "Hispanic or Latino"
                }
              }, {
                "url": "text",
                "valueString": "Hispanic or Latino"
              }
            ],
            "url": "http://hl7.org/fhir/us/core/StructureDefinition/us-core-ethnicity"
          }
        ],
        "identifier": [{
            "use": "usual",
            "type": {
              "coding": [{
                  "system": "http://terminology.hl7.org/CodeSystem/v2-0203",
                  "code": "MR",
                  "display": "Medical Record Number"
                }
              ]
            },
            "system": "http://hospital.smarthealthit.org",
            "value": "999995992"
          }
        ],
        "name": [{
            "family": "Susan",
            "given": [
              "Parker"
            ]
          }
        ],
        "gender": "female",
        "birthDate": "1965-01-01"
      }
    }, {
      "fullUrl": "http://example.org/fhir/gaps/Organization/gaps-organization-reportingvendor",
      "resource": {
        "resourceType": "Organization",
        "id": "gaps-organization-reportingvendor",
        "meta": {
          "profile": [
            "http://hl7.org/fhir/us/qicore/StructureDefinition/qicore-organization"
          ]
        },
        "identifier": [{
            "use": "official",
            "type": {
              "coding": [{
                  "system": "http://terminology.hl7.org/CodeSystem/v2-0203",
                  "code": "TAX",
                  "display": "Tax ID number"
                }
              ]
            },
            "system": "urn:oid:2.16.840.1.113883.4.4",
            "value": "123446789",
            "assigner": {
              "display": "www.irs.gov"
            }
          }
        ],
        "active": true,
        "type": [{
            "coding": [{
                "system": "http://terminology.hl7.org/CodeSystem/organization-type",
                "code": "pay",
                "display": "Payer"
              }
            ]
          }
        ],
        "name": "GapsReportingVendor01",
        "telecom": [{
            "system": "phone",
            "value": "(+1) 401-545-1212"
          }
        ],
        "address": [{
            "line": [
              "13 Drive Street"
            ],
            "city": "Cityplace",
            "state": "MA",
            "postalCode": "01101",
            "country": "USA"
          }
        ]
      }
    }
  ]
}

~~~
