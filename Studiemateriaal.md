## Studiemateriaal
### General study materials: `GET /rest/v1/studiemateriaal/algemeen/[student_id]`
<details><summary>Click to open</summary>

Fetches the general study material for the user

#### Parameters

| Name          | Type      | Value                 |
|---------------|-----------|-----------------------|
| Authorization | Header    | Bearer [access_token] |
| student_id    | URL       | [student_id]          |

#### Returns

```json
{
    "items": [
        {
            "$type": "leermiddel.REduRoutePortalUserProduct",
            "links": [
                {
                    "id": 1234,
                    "rel": "self",
                    "type": "leermiddel.REduRoutePortalUserProduct",
                    "href": "https://api.somtoday.nl/rest/v1/edurouteportaluserproduct/1234"
                }
            ],
            "permissions": [
                {
                    "full": "leermiddel.REduRoutePortalUserProduct:READ:INSTANCE(1234)",
                    "type": "leermiddel.REduRoutePortalUserProduct",
                    "operations": ["READ"],
                    "instances": ["INSTANCE(1234)"]
                }
            ],
            "additionalObjects": {},
            "leerling": {
                "links": [
                    {
                        "id": 1234,
                        "rel": "self",
                        "type": "leerling.RLeerlingPrimer",
                        "href": "https://api.somtoday.nl/rest/v1/leerlingen/1234"
                    }
                ],
                "permissions": [
                    {
                        "full": "leerling.RLeerling:READ:INSTANCE(1234)",
                        "type": "leerling.RLeerling",
                        "operations": ["READ"],
                        "instances": ["INSTANCE(1234)"]
                    }
                ],
                "additionalObjects": {},
                "UUID": "00000000-0000-0000-0000-000000000000",
                "leerlingnummer": 402638,
                "roepnaam": "Lenn",
                "achternaam": "Steenbergen",
                "pasfotoUrl": "https://api.somtoday.nl/rest/v1/pasfoto/0792a6e2-9833-45e8-b1eb-1498cf22f10d/AbC123dEf256gHi7890AbC123dEf256g"
            },
            "product": {
                "$type": "leermiddel.REduRoutePortalProduct",
                "links": [
                    {
                        "id": 1234,
                        "rel": "self",
                        "type": "leermiddel.REduRoutePortalProduct",
                        "href": "https://api.somtoday.nl/rest/v1/edurouteportalproduct/1234"
                    }
                ],
                "permissions": [
                    {
                        "full": "leermiddel.REduRoutePortalProduct:READ:INSTANCE(1234)",
                        "type": "leermiddel.REduRoutePortalProduct",
                        "operations": ["READ"],
                        "instances": ["INSTANCE(1234)"]
                    }
                ],
                "additionalObjects": {},
                "title": "Libre Service LRN-line online + boek 5 havo 4-jaar afname",
                "url": "https://toegang.thiememeulenhoff.nl/9789006624595",
                "UUID": "00000000-0000-0000-0000-000000000000"
            },
            "UUID": "00000000-0000-0000-0000-000000000000"
        },
        {
            "$type": "leermiddel.REduRoutePortalUserProduct",
            "links": [
                {
                    "id": 1234,
                    "rel": "self",
                    "type": "leermiddel.REduRoutePortalUserProduct",
                    "href": "https://api.somtoday.nl/rest/v1/edurouteportaluserproduct/1234"
                }
            ],
            "permissions": [
                {
                    "full": "leermiddel.REduRoutePortalUserProduct:READ:INSTANCE(1234)",
                    "type": "leermiddel.REduRoutePortalUserProduct",
                    "operations": ["READ"],
                    "instances": ["INSTANCE(1234)"]
                }
            ],
            "additionalObjects": {},
            "leerling": {
                "links": [
                    {
                        "id": 1234,
                        "rel": "self",
                        "type": "leerling.RLeerlingPrimer",
                        "href": "https://api.somtoday.nl/rest/v1/leerlingen/1234"
                    }
                ],
                "permissions": [
                    {
                        "full": "leerling.RLeerling:READ:INSTANCE(1234)",
                        "type": "leerling.RLeerling",
                        "operations": ["READ"],
                        "instances": ["INSTANCE(1234)"]
                    }
                ],
                "additionalObjects": {},
                "UUID": "00000000-0000-0000-0000-000000000000",
                "leerlingnummer": 402638,
                "roepnaam": "Lenn",
                "achternaam": "Steenbergen",
                "pasfotoUrl": "https://api.somtoday.nl/rest/v1/pasfoto/0792a6e2-9833-45e8-b1eb-1498cf22f10d/AbC123dEf256gHi7890AbC123dEf256g"
            },
            "product": {
                "$type": "leermiddel.REduRoutePortalProduct",
                "links": [
                    {
                        "id": 1234,
                        "rel": "self",
                        "type": "leermiddel.REduRoutePortalProduct",
                        "href": "https://api.somtoday.nl/rest/v1/edurouteportalproduct/1234"
                    }
                ],
                "permissions": [
                    {
                        "full": "leermiddel.REduRoutePortalProduct:READ:INSTANCE(1234)",
                        "type": "leermiddel.REduRoutePortalProduct",
                        "operations": ["READ"],
                        "instances": ["INSTANCE(1234)"]
                    }
                ],
                "additionalObjects": {},
                "title": "Getal & Ruimte ed 13.0 havo A 3 FLEX boek + online",
                "url": "https://toegang.noordhoff.nl/9789001053789",
                "UUID": "00000000-0000-0000-0000-000000000000"
            },
            "UUID": "00000000-0000-0000-0000-000000000000"
        }
    ]
}
```

</details>

### Fetch subjects that have study material: `GET /rest/v1/vakken/studiemateriaal/[student_id]`
<details><summary>Click to open</summary>

Fetches the subjects that provide study material for the user

#### Parameters

| Name          | Type      | Value                 |
|---------------|-----------|-----------------------|
| Authorization | Header    | Bearer [access_token] |
| student_id    | URL       | [student_id]          |

#### Returns

```json
{
    "items": [
        {
            "$type": "onderwijsinrichting.RVak",
            "links": [
                {
                    "id": 1234,
                    "rel": "self",
                    "type": "onderwijsinrichting.RVak",
                    "href": "https://api.somtoday.nl/rest/v1/vakken/1234"
                }
            ],
            "permissions": [
                {
                    "full": "onderwijsinrichting.RVak:READ:INSTANCE(1234)",
                    "type": "onderwijsinrichting.RVak",
                    "operations": [
                        "READ"
                    ],
                    "instances": [
                        "INSTANCE(1234)"
                    ]
                }
            ],
            "additionalObjects": {},
            "afkorting": "netl",
            "naam": "Nederlandse taal en literatuur",
            "UUID": "00000000-0000-0000-0000-000000000000"
        },
        {
            "$type": "onderwijsinrichting.RVak",
            "links": [
                {
                    "id": 1234,
                    "rel": "self",
                    "type": "onderwijsinrichting.RVak",
                    "href": "https://api.somtoday.nl/rest/v1/vakken/1234"
                }
            ],
            "permissions": [
                {
                    "full": "onderwijsinrichting.RVak:READ:INSTANCE(1234)",
                    "type": "onderwijsinrichting.RVak",
                    "operations": [
                        "READ"
                    ],
                    "instances": [
                        "INSTANCE(1234)"
                    ]
                }
            ],
            "additionalObjects": {},
            "afkorting": "entl",
            "naam": "Engelse taal en literatuur",
            "UUID": "0000000-0000-0000-0000-00000000000"
        }
    ]
}
```
</details>

### Fetch study material: `GET /rest/v1/studiemateriaal/[student_id]/vak/[stubject_uuid]`
<details><summary>Click to open</summary>

Fetches study materials of specified subject, the return output is a custom made combined json output with all three variants of outputs. 
#### Parameters

| Name          | Type      | Value                 |
|---------------|-----------|-----------------------|
| Authorization | Header    | Bearer [access_token] |
| student_id    | URL       | [student_id]          |
| subject_uuid  | URL       | [subject_uuid]        |

#### Returns

```json
{
    "items": [
        {
            "$type": "studiewijzer.RStudieMateriaal",
            "studiewijzer": {
                "links": [
                    {
                        "id": 1234,
                        "rel": "self",
                        "type": "studiewijzer.RStudiewijzer",
                        "href": "https://api.somtoday.nl/rest/v1/studiewijzers/1234"
                    }
                ],
                "permissions": [
                    {
                        "full": "studiewijzer.RStudiewijzer:READ:INSTANCE(1234)",
                        "type": "studiewijzer.RStudiewijzer",
                        "operations": ["READ"],
                        "instances": ["INSTANCE(1234)"]
                    }
                ],
                "additionalObjects": {},
                "UUID": "00000000-0000-0000-0000-000000000000",
                "naam": "h5.dutl1",
                "vestiging": {
                    "links": [
                        {
                            "id": 1234,
                            "rel": "self",
                            "type": "instelling.RVestiging",
                            "href": "https://api.somtoday.nl/rest/v1/vestigingen/1234"
                        }
                    ],
                    "permissions": [
                        {
                            "full": "instelling.RVestiging:READ:INSTANCE(1234)",
                            "type": "instelling.RVestiging",
                            "operations": ["READ"],
                            "instances": ["INSTANCE(1234)"]
                        }
                    ],
                    "additionalObjects": {},
                    "naam": "REDACTED",
                    "afkorting": "REDACTED",
                    "UUID": "00000000-0000-0000-0000-000000000000",
                    "uuid": "00000000-0000-0000-0000-000000000000"
                },
                "lesgroep": {
                    "links": [
                        {
                            "id": 1234,
                            "rel": "self",
                            "type": "lesgroep.RLesgroep",
                            "href": "https://api.somtoday.nl/rest/v1/lesgroepen/1234"
                        }
                    ],
                    "permissions": [
                        {
                            "full": "lesgroep.RLesgroep:READ:INSTANCE(1234)",
                            "type": "lesgroep.RLesgroep",
                            "operations": ["READ"],
                            "instances": ["INSTANCE(1234)"]
                        }
                    ],
                    "additionalObjects": {},
                    "UUID": "00000000-0000-0000-0000-000000000000",
                    "naam": "h5.dutl1",
                    "omschrijving": "h5.dutl1",
                    "schooljaar": {
                        "$type": "onderwijsinrichting.RSchooljaar",
                        "links": [
                            {
                                "id": 1234,
                                "rel": "self",
                                "type": "onderwijsinrichting.RSchooljaar",
                                "href": "https://api.somtoday.nl/rest/v1/schooljaren/1234"
                            }
                        ],
                        "permissions": [
                            {
                                "full": "onderwijsinrichting.RSchooljaar:READ:INSTANCE(1234)",
                                "type": "onderwijsinrichting.RSchooljaar",
                                "operations": ["READ"],
                                "instances": ["INSTANCE(1234)"]
                            }
                        ],
                        "additionalObjects": {},
                        "naam": "2026/2027",
                        "vanafDatum": "2026-08-01",
                        "totDatum": "2027-07-31",
                        "isHuidig": true
                    },
                    "vak": {
                        "links": [
                            {
                                "id": 1234,
                                "rel": "self",
                                "type": "onderwijsinrichting.RVak",
                                "href": "https://api.somtoday.nl/rest/v1/vakken/1234"
                            }
                        ],
                        "permissions": [
                            {
                                "full": "onderwijsinrichting.RVak:READ:INSTANCE(1234)",
                                "type": "onderwijsinrichting.RVak",
                                "operations": ["READ"],
                                "instances": ["INSTANCE(1234)"]
                            }
                        ],
                        "additionalObjects": {},
                        "afkorting": "dutl",
                        "naam": "Duitse taal en literatuur",
                        "UUID": "00000000-0000-0000-0000-000000000000"
                    },
                    "heeftStamgroep": false,
                    "examendossierOndersteund": true,
                    "vestiging": {
                        "links": [
                            {
                                "id": 1234,
                                "rel": "self",
                                "type": "instelling.RVestiging",
                                "href": "https://api.somtoday.nl/rest/v1/vestigingen/1234"
                            }
                        ],
                        "permissions": [
                            {
                                "full": "instelling.RVestiging:READ:INSTANCE(1234)",
                                "type": "instelling.RVestiging",
                                "operations": ["READ"],
                                "instances": ["INSTANCE(1234)"]
                            }
                        ],
                        "additionalObjects": {},
                        "naam": "REDACTED",
                        "afkorting": "REDACTED",
                        "UUID": "00000000-0000-0000-0000-000000000000",
                        "uuid": "00000000-0000-0000-0000-000000000000"
                    }
                },
                "eigenaar": {
                    "links": [
                        {
                            "id": 1234,
                            "rel": "self",
                            "type": "medewerker.RMedewerker",
                            "href": "https://api.somtoday.nl/rest/v1/medewerkers/1234"
                        }
                    ],
                    "permissions": [],
                    "additionalObjects": {},
                    "UUID": "00000000-0000-0000-0000-000000000000",
                    "nummer": 308382,
                    "afkorting": "REDACTED",
                    "achternaam": "REDACTED",
                    "geslacht": "VROUW",
                    "voorvoegsel": "de",
                    "voorletters": "M.",
                    "roepnaam": "REDACTED"
                },
                "magBewerken": false,
                "uuid": "00000000-0000-0000-0000-000000000000"
            },
            "lesstof": [],
            "jaarBijlagenMappen": [],
            "jaarBijlagen": [],
            "externMateriaal": [],
            "leermiddelKeuzes": [
                {
                    "links": [
                        {
                            "id": 1234,
                            "rel": "self",
                            "type": "leermiddel.RLeermiddelKeuze",
                            "href": "https://api.somtoday.nl/rest/v1/leermiddelkeuze/1234"
                        }
                    ],
                    "permissions": [
                        {
                            "full": "leermiddel.RLeermiddelKeuze:READ,UPDATE,DELETE:INSTANCE(1234)",
                            "type": "leermiddel.RLeermiddelKeuze",
                            "operations": ["READ", "UPDATE", "DELETE"],
                            "instances": ["INSTANCE(1234)"]
                        }
                    ],
                    "additionalObjects": {},
                    "leermiddel": {
                        "links": [
                            {
                                "id": 1234,
                                "rel": "self",
                                "type": "leermiddel.RInstellingsLeermiddel",
                                "href": "https://api.somtoday.nl/rest/v1/instellingsleermiddelen/1234"
                            }
                        ],
                        "permissions": [
                            {
                                "full": "leermiddel.RInstellingsLeermiddel:READ,UPDATE,DELETE:INSTANCE(1234)",
                                "type": "leermiddel.RInstellingsLeermiddel",
                                "operations": ["READ", "UPDATE", "DELETE"],
                                "instances": ["INSTANCE(1234)"]
                            }
                        ],
                        "additionalObjects": {},
                        "ean": 9789402055207,
                        "titel": "Na klar! MAX boek + online havo/vwo bovenbouw 5 havo 6 jaar afname",
                        "url": "https://toegang.malmberg.nl/content?ean=9789402055207",
                        "UUID": "00000000-0000-0000-0000-000000000000",
                        "methodeInformatie": {
                            "$type": "leermiddel.RMethodeInformatie",
                            "links": [
                                {
                                    "id": 1234,
                                    "rel": "self",
                                    "type": "leermiddel.RMethodeInformatie",
                                    "href": "https://api.somtoday.nl/rest/v1/methodeinformatie/1234"
                                }
                            ],
                            "permissions": [
                                {
                                    "full": "leermiddel.RMethodeInformatie:READ,UPDATE,DELETE:INSTANCE(1234)",
                                    "type": "leermiddel.RMethodeInformatie",
                                    "operations": ["READ", "UPDATE", "DELETE"],
                                    "instances": ["INSTANCE(1234)"]
                                }
                            ],
                            "additionalObjects": {},
                            "UUID": "00000000-0000-0000-0000-000000000000",
                            "dashboardMethodeNaam": "Na klar!",
                            "methode": "Na klar!",
                            "uitgever": "Malmberg"
                        }
                    },
                    "UUID": "00000000-0000-0000-0000-000000000000"
                }
            ]
        },
        {
            "$type": "studiewijzer.RStudieMateriaal",
            "studiewijzer": {
                "links": [
                    {
                        "id": 1234,
                        "rel": "self",
                        "type": "studiewijzer.RStudiewijzer",
                        "href": "https://api.somtoday.nl/rest/v1/studiewijzers/1234"
                    }
                ],
                "permissions": [
                    {
                        "full": "studiewijzer.RStudiewijzer:READ:INSTANCE(1234)",
                        "type": "studiewijzer.RStudiewijzer",
                        "operations": ["READ"],
                        "instances": ["INSTANCE(1234)"]
                    }
                ],
                "additionalObjects": {},
                "UUID": "00000000-0000-0000-0000-000000000000",
                "naam": "h5.econ1",
                "vestiging": {
                    "links": [
                        {
                            "id": 1234,
                            "rel": "self",
                            "type": "instelling.RVestiging",
                            "href": "https://api.somtoday.nl/rest/v1/vestigingen/1234"
                        }
                    ],
                    "permissions": [
                        {
                            "full": "instelling.RVestiging:READ:INSTANCE(1234)",
                            "type": "instelling.RVestiging",
                            "operations": ["READ"],
                            "instances": ["INSTANCE(1234)"]
                        }
                    ],
                    "additionalObjects": {},
                    "naam": "REDACTED",
                    "afkorting": "REDACTED",
                    "UUID": "00000000-0000-0000-0000-000000000000",
                    "uuid": "00000000-0000-0000-0000-000000000000"
                },
                "lesgroep": {
                    "links": [
                        {
                            "id": 1234,
                            "rel": "self",
                            "type": "lesgroep.RLesgroep",
                            "href": "https://api.somtoday.nl/rest/v1/lesgroepen/1234"
                        }
                    ],
                    "permissions": [
                        {
                            "full": "lesgroep.RLesgroep:READ:INSTANCE(1234)",
                            "type": "lesgroep.RLesgroep",
                            "operations": ["READ"],
                            "instances": ["INSTANCE(1234)"]
                        }
                    ],
                    "additionalObjects": {},
                    "UUID": "00000000-0000-0000-0000-000000000000",
                    "naam": "h5.econ1",
                    "omschrijving": "h5.econ1",
                    "schooljaar": {
                        "$type": "onderwijsinrichting.RSchooljaar",
                        "links": [
                            {
                                "id": 1234,
                                "rel": "self",
                                "type": "onderwijsinrichting.RSchooljaar",
                                "href": "https://api.somtoday.nl/rest/v1/schooljaren/1234"
                            }
                        ],
                        "permissions": [
                            {
                                "full": "onderwijsinrichting.RSchooljaar:READ:INSTANCE(1234)",
                                "type": "onderwijsinrichting.RSchooljaar",
                                "operations": ["READ"],
                                "instances": ["INSTANCE(1234)"]
                            }
                        ],
                        "additionalObjects": {},
                        "naam": "2026/2027",
                        "vanafDatum": "2026-08-01",
                        "totDatum": "2027-07-31",
                        "isHuidig": true
                    },
                    "vak": {
                        "links": [
                            {
                                "id": 1234,
                                "rel": "self",
                                "type": "onderwijsinrichting.RVak",
                                "href": "https://api.somtoday.nl/rest/v1/vakken/1234"
                            }
                        ],
                        "permissions": [
                            {
                                "full": "onderwijsinrichting.RVak:READ:INSTANCE(1234)",
                                "type": "onderwijsinrichting.RVak",
                                "operations": ["READ"],
                                "instances": ["INSTANCE(1234)"]
                            }
                        ],
                        "additionalObjects": {},
                        "afkorting": "econ",
                        "naam": "economie",
                        "UUID": "00000000-0000-0000-0000-000000000000"
                    },
                    "heeftStamgroep": false,
                    "examendossierOndersteund": true,
                    "vestiging": {
                        "links": [
                            {
                                "id": 1234,
                                "rel": "self",
                                "type": "instelling.RVestiging",
                                "href": "https://api.somtoday.nl/rest/v1/vestigingen/1234"
                            }
                        ],
                        "permissions": [
                            {
                                "full": "instelling.RVestiging:READ:INSTANCE(1234)",
                                "type": "instelling.RVestiging",
                                "operations": ["READ"],
                                "instances": ["INSTANCE(1234)"]
                            }
                        ],
                        "additionalObjects": {},
                        "naam": "REDACTED",
                        "afkorting": "REDACTED",
                        "UUID": "00000000-0000-0000-0000-000000000000",
                        "uuid": "00000000-0000-0000-0000-000000000000"
                    }
                },
                "eigenaar": {
                    "links": [
                        {
                            "id": 1234,
                            "rel": "self",
                            "type": "medewerker.RMedewerker",
                            "href": "https://api.somtoday.nl/rest/v1/medewerkers/1234"
                        }
                    ],
                    "permissions": [],
                    "additionalObjects": {},
                    "UUID": "00000000-0000-0000-0000-000000000000",
                    "nummer": 308385,
                    "afkorting": "REDACTED",
                    "achternaam": "REDACTED",
                    "geslacht": "VROUW",
                    "voorletters": "M.",
                    "roepnaam": "REDACTED"
                },
                "magBewerken": false,
                "uuid": "00000000-0000-0000-0000-000000000000"
            },
            "lesstof": [],
            "jaarBijlagenMappen": [],
            "jaarBijlagen": [],
            "externMateriaal": [
                {
                    "links": [
                        {
                            "id": 1234,
                            "rel": "self",
                            "type": "studiewijzer.RStudiewijzerJaarExternMateriaal",
                            "href": "https://api.somtoday.nl/rest/v1/studiewijzerjaarexternematerialen/1234"
                        }
                    ],
                    "permissions": [
                        {
                            "full": "studiewijzer.RStudiewijzerJaarExternMateriaal:READ:INSTANCE(1234)",
                            "type": "studiewijzer.RStudiewijzerJaarExternMateriaal",
                            "operations": ["READ"],
                            "instances": ["INSTANCE(1234)"]
                        }
                    ],
                    "additionalObjects": {},
                    "uri": "https://padlet.com/REDACTED/H5eco",
                    "omschrijving": "Link padlet",
                    "contentType": "undefined",
                    "sortering": 0,
                    "zichtbaarVoorLeerling": true
                }
            ],
            "leermiddelKeuzes": []
        },
        {
            "$type": "studiewijzer.RStudieMateriaal",
            "studiewijzer": {
                "links": [
                    {
                        "id": 1234,
                        "rel": "self",
                        "type": "studiewijzer.RStudiewijzer",
                        "href": "https://api.somtoday.nl/rest/v1/studiewijzers/1234"
                    }
                ],
                "permissions": [
                    {
                        "full": "studiewijzer.RStudiewijzer:READ:INSTANCE(1234)",
                        "type": "studiewijzer.RStudiewijzer",
                        "operations": ["READ"],
                        "instances": ["INSTANCE(1234)"]
                    }
                ],
                "additionalObjects": {},
                "UUID": "00000000-0000-0000-0000-000000000000",
                "naam": "h5.maat3",
                "vestiging": {
                    "links": [
                        {
                            "id": 1234,
                            "rel": "self",
                            "type": "instelling.RVestiging",
                            "href": "https://api.somtoday.nl/rest/v1/vestigingen/1234"
                        }
                    ],
                    "permissions": [
                        {
                            "full": "instelling.RVestiging:READ:INSTANCE(1234)",
                            "type": "instelling.RVestiging",
                            "operations": ["READ"],
                            "instances": ["INSTANCE(1234)"]
                        }
                    ],
                    "additionalObjects": {},
                    "naam": "REDACTED",
                    "afkorting": "REDACTED",
                    "UUID": "00000000-0000-0000-0000-000000000000",
                    "uuid": "00000000-0000-0000-0000-000000000000"
                },
                "lesgroep": {
                    "links": [
                        {
                            "id": 1234,
                            "rel": "self",
                            "type": "lesgroep.RLesgroep",
                            "href": "https://api.somtoday.nl/rest/v1/lesgroepen/1234"
                        }
                    ],
                    "permissions": [
                        {
                            "full": "lesgroep.RLesgroep:READ:INSTANCE(1234)",
                            "type": "lesgroep.RLesgroep",
                            "operations": ["READ"],
                            "instances": ["INSTANCE(1234)"]
                        }
                    ],
                    "additionalObjects": {},
                    "UUID": "00000000-0000-0000-0000-000000000000",
                    "naam": "h5.maat3",
                    "omschrijving": "h5.maat3",
                    "schooljaar": {
                        "$type": "onderwijsinrichting.RSchooljaar",
                        "links": [
                            {
                                "id": 1234,
                                "rel": "self",
                                "type": "onderwijsinrichting.RSchooljaar",
                                "href": "https://api.somtoday.nl/rest/v1/schooljaren/1234"
                            }
                        ],
                        "permissions": [
                            {
                                "full": "onderwijsinrichting.RSchooljaar:READ:INSTANCE(1234)",
                                "type": "onderwijsinrichting.RSchooljaar",
                                "operations": ["READ"],
                                "instances": ["INSTANCE(1234)"]
                            }
                        ],
                        "additionalObjects": {},
                        "naam": "2026/2027",
                        "vanafDatum": "2026-08-01",
                        "totDatum": "2027-07-31",
                        "isHuidig": true
                    },
                    "vak": {
                        "links": [
                            {
                                "id": 1234,
                                "rel": "self",
                                "type": "onderwijsinrichting.RVak",
                                "href": "https://api.somtoday.nl/rest/v1/vakken/1234"
                            }
                        ],
                        "permissions": [
                            {
                                "full": "onderwijsinrichting.RVak:READ:INSTANCE(1234)",
                                "type": "onderwijsinrichting.RVak",
                                "operations": ["READ"],
                                "instances": ["INSTANCE(1234)"]
                            }
                        ],
                        "additionalObjects": {},
                        "afkorting": "maat",
                        "naam": "maatschappijleer",
                        "UUID": "00000000-0000-0000-0000-000000000000"
                    },
                    "heeftStamgroep": false,
                    "examendossierOndersteund": true,
                    "vestiging": {
                        "links": [
                            {
                                "id": 1234,
                                "rel": "self",
                                "type": "instelling.RVestiging",
                                "href": "https://api.somtoday.nl/rest/v1/vestigingen/1234"
                            }
                        ],
                        "permissions": [
                            {
                                "full": "instelling.RVestiging:READ:INSTANCE(1234)",
                                "type": "instelling.RVestiging",
                                "operations": ["READ"],
                                "instances": ["INSTANCE(1234)"]
                            }
                        ],
                        "additionalObjects": {},
                        "naam": "REDACTED",
                        "afkorting": "REDACTED",
                        "UUID": "00000000-0000-0000-0000-000000000000",
                        "uuid": "00000000-0000-0000-0000-000000000000"
                    }
                },
                "eigenaar": {
                    "links": [
                        {
                            "id": 1234,
                            "rel": "self",
                            "type": "medewerker.RMedewerker",
                            "href": "https://api.somtoday.nl/rest/v1/medewerkers/1234"
                        }
                    ],
                    "permissions": [],
                    "additionalObjects": {},
                    "UUID": "00000000-0000-0000-0000-000000000000",
                    "nummer": 151207,
                    "afkorting": "REDACTED",
                    "achternaam": "REDACTED",
                    "geslacht": "MAN",
                    "voorletters": "P.",
                    "roepnaam": "REDACTED"
                },
                "magBewerken": false,
                "uuid": "00000000-0000-0000-0000-000000000000"
            },
            "lesstof": [],
            "jaarBijlagenMappen": [
                {
                    "links": [
                        {
                            "id": 1234,
                            "rel": "self",
                            "type": "studiewijzer.RStudiewijzerJaarBijlageMap",
                            "href": "https://api.somtoday.nl/rest/v1/studiewijzerjaarbijlagemappen/1234"
                        }
                    ],
                    "permissions": [
                        {
                            "full": "studiewijzer.RStudiewijzerJaarBijlageMap:READ:INSTANCE(1234)",
                            "type": "studiewijzer.RStudiewijzerJaarBijlageMap",
                            "operations": ["READ"],
                            "instances": ["INSTANCE(1234)"]
                        }
                    ],
                    "additionalObjects": {},
                    "naam": "Actiepunt",
                    "zichtbaarVoorLeerling": true,
                    "sortering": 0
                }
            ],
            "jaarBijlagen": [
                {
                    "links": [
                        {
                            "id": 1234,
                            "rel": "self",
                            "type": "studiewijzer.RStudiewijzerJaarBijlage",
                            "href": "https://api.somtoday.nl/rest/v1/studiewijzerjaarbijlagen/1234"
                        }
                    ],
                    "permissions": [
                        {
                            "full": "studiewijzer.RStudiewijzerJaarBijlage:READ:INSTANCE(1234)",
                            "type": "studiewijzer.RStudiewijzerJaarBijlage",
                            "operations": ["READ"],
                            "instances": ["INSTANCE(1234)"]
                        }
                    ],
                    "additionalObjects": {},
                    "omschrijving": "Beoordeling Actiepunt 2026-2027.docx",
                    "bestand": {
                        "links": [
                            {
                                "id": 1234,
                                "rel": "koppeling",
                                "type": "bestanden.RBestand"
                            }
                        ],
                        "permissions": [],
                        "additionalObjects": {},
                        "bestanddataId": "00000000-0000-0000-0000-000000000000.docx",
                        "bestandsnaam": "Beoordeling Actiepunt 2026-2027.docx",
                        "bestandsgrootte": 17820
                    },
                    "assemblyResults": [],
                    "sortering": 0,
                    "zichtbaarVoorLeerling": true,
                    "jaarbijlageMap": {
                        "links": [
                            {
                                "id": 1234,
                                "rel": "self",
                                "type": "studiewijzer.RStudiewijzerJaarBijlageMap",
                                "href": "https://api.somtoday.nl/rest/v1/studiewijzerjaarbijlagemappen/1234"
                            }
                        ],
                        "permissions": [
                            {
                                "full": "studiewijzer.RStudiewijzerJaarBijlageMap:READ:INSTANCE(1234)",
                                "type": "studiewijzer.RStudiewijzerJaarBijlageMap",
                                "operations": ["READ"],
                                "instances": ["INSTANCE(1234)"]
                            }
                        ],
                        "additionalObjects": {},
                        "naam": "Actiepunt",
                        "zichtbaarVoorLeerling": true,
                        "sortering": 0
                    }
                },
                {
                    "links": [
                        {
                            "id": 1234,
                            "rel": "self",
                            "type": "studiewijzer.RStudiewijzerJaarBijlage",
                            "href": "https://api.somtoday.nl/rest/v1/studiewijzerjaarbijlagen/1234"
                        }
                    ],
                    "permissions": [
                        {
                            "full": "studiewijzer.RStudiewijzerJaarBijlage:READ:INSTANCE(1234)",
                            "type": "studiewijzer.RStudiewijzerJaarBijlage",
                            "operations": ["READ"],
                            "instances": ["INSTANCE(1234)"]
                        }
                    ],
                    "additionalObjects": {},
                    "omschrijving": "Actiepunt hv5 2026-2027.pptx",
                    "bestand": {
                        "links": [
                            {
                                "id": 1234,
                                "rel": "koppeling",
                                "type": "bestanden.RBestand"
                            }
                        ],
                        "permissions": [],
                        "additionalObjects": {},
                        "bestanddataId": "00000000-0000-0000-0000-000000000000.pptx",
                        "bestandsnaam": "Actiepunt hv5 2026-2027.pptx",
                        "bestandsgrootte": 178909
                    },
                    "assemblyResults": [],
                    "sortering": 1,
                    "zichtbaarVoorLeerling": true,
                    "jaarbijlageMap": {
                        "links": [
                            {
                                "id": 1234,
                                "rel": "self",
                                "type": "studiewijzer.RStudiewijzerJaarBijlageMap",
                                "href": "https://api.somtoday.nl/rest/v1/studiewijzerjaarbijlagemappen/1234"
                            }
                        ],
                        "permissions": [
                            {
                                "full": "studiewijzer.RStudiewijzerJaarBijlageMap:READ:INSTANCE(1234)",
                                "type": "studiewijzer.RStudiewijzerJaarBijlageMap",
                                "operations": ["READ"],
                                "instances": ["INSTANCE(1234)"]
                            }
                        ],
                        "additionalObjects": {},
                        "naam": "Actiepunt",
                        "zichtbaarVoorLeerling": true,
                        "sortering": 0
                    }
                }
            ],
            "externMateriaal": [],
            "leermiddelKeuzes": []
        }
    ]
}
```
</details>

### Fetch file from study material folder: `GET /gcs/download/[filename]`
<details><summary>Click to open</summary>

Fetches a download link for the specified file

#### Parameters

| Name          | Type      | Value                              |
|---------------|-----------|------------------------------------|
| Authorization | Header    | Bearer [access_token]              |
| filename      | URL       | [name from bestanddataId]          |

#### Returns

`https://storage.googleapis.com/filetoday-prod-processed/0792a6e2-9833-45e8-b1eb-1498cf22f10d/[filename]?X-Goog-Algorithm=GOOG4-RSA-SHA256&X-Goog-Credential=filetoday-backend%40te000-44ea9997293e087b245c.iam.gserviceaccount.com%2F20260920%2Fauto%2Fstorage%2Fgoog4_request&X-Goog-Date=20260920T161242Z&X-Goog-Expires=900&X-Goog-SignedHeaders=host&response-content-disposition=attachment%3B%20filename%3D%22ACTUALENCODEDFILENAME%22&X-Goog-Signature=SIGNATURE`

</details>
