# SOMtoday REST API docs

#### Dev Community

In case you have any questions about the docs or want to chat with other, you can join the community. There are several channels related to the SOMtoday API and other general purpose channels.

##### Matrix (bridged to Discord)

[![Matrix chat](https://img.shields.io/matrix/somtoday%3Aelisaado.com?server_fqdn=matrix.elisaado.com&fetchMode=summary)](https://matrix.to/#/#somtoday:elisaado.com)

##### Discord (bridged to Matrix)

[![Discord Chat](https://img.shields.io/discord/789249810032361502.svg)](https://discord.gg/yE3e3erCut)

## Table of contents

<!-- TOC -->

- [SOMtoday REST API docs](#somtoday-rest-api-docs)
  - [Discord](#discord)
  - [Table of contents](#table-of-contents)
  - [Some miscellaneous stuff](#some-miscellaneous-stuff)
  - [Authentication / authorization](Authentication.md)
    - [Getting a list of schools](Authentication.md#getting-a-list-of-schools)
    - [Authentication by mimicking the SOMToday app/webapp](Authentication.md#authentication-by-mimicking-the-somtoday-appwebapp)
    - [Fetching the access token via SSO](Authentication.md#authentication-using-sso-single-sign-on)
    - [Fetching the access token via Somtoday login: `POST /oauth2/token`](Authentication.md#fetching-the-access-token-via-somtoday-login)
    - [Refreshing the token: `POST /oauth2/token`](Authentication.md#refreshing-the-access-token)
  - [Fetching information](#fetching-information)
    - [Current student(s): `GET /rest/v1/leerlingen`](#current-students-get-restv1leerlingen)
    - [Student by ID: `GET /rest/v1/leerlingen/[id]`](#student-by-id-get-restv1leerlingenid)
    - [Get message recipients: `GET /rest/v1/medewerkers/ontvangers`](#get-message-recipients-get-restv1medewerkersontvangers)
    - [Schedule: `GET /rest/v1/afspraakitems/[student-id]/jaar/[year]/week/[week]`](#schedule-get-restv1afspraakitemsstudent-idjaaryearweekweek)
    - [Absence Reports: `GET /rest/v1/absentiemeldingen`](#absence-reports-get-restv1absentiemeldingen)
    - [Study Guides: `GET /rest/v1/studiewijzers`](#study-guides-get-restv1studiewijzers)
    - [Subjects: `GET /rest/v1/vakken`](#subjects-get-restv1vakken)
    - [User Account: `GET /rest/v1/account`](#account-get-restv1account--get-restv1accountid)
    - [School Years: `GET /rest/v1/schooljaren`](#schooljaren-get-restv1schooljaren--get-restv1schooljarenid)
    - [Vakkeuzes: `GET /rest/v1/vakkeuzes`](#vakkeuzes-get-restv1vakkeuzes)
    - [Waarnemingen: `GET /rest/v1/waarnemingen`](#waarnemingen-get-restv1waarnemingen)
    - [Messages: `GET /rest/v1/boodschappen/conversaties`](#messages-get-restv1boodschappenconversaties)
    - [Schoolgegevens: `GET /rest/v1/leerlingen/[id]/schoolgegevens`](#schoolgegevens-get-restv1idschoolgegevens)
    - [Vakanties: `GET /rest/v1/vakanties/leerling/[id]`](#vakanties-get-restv1vakantiesleerlingid)
    - [ICalendar: `GET /rest/v1/icalendar`](#icalendar-get-restv1icalendar)
    - [ICalendar: `DELETE /rest/v1/icalendar`](#icalendar-delete-restv1icalendar)
  - [Grades](Grades.md)
    - [Enrolled school years: `GET /rest/v1/plaatsingen?[studentid]?`](Grades.md#enrolled-school-years-get-restv1plaatsingenstudentid)
    - [Averages: `GET /rest/v1/vakkeuzes/plaatsing/[id]/vakgemiddelden`](Grades.md#averages-get-restv1vakkeuzesplaatsingidvakgemiddelden)
    - [Normal grades: `GET /rest/v1/geldendvoortgangsdossierresultaten/vakresultaten/[leerlingid]/vak/[vakid]/lichting/[lichtingid]`](Grades.md#normal-grades-get-restv1geldendvoortgangsdossierresultatenvakresultatenleerlingidvakvakidlichtinglichtingid)
    - [Exam grades: `GET /rest/v1/geldendexamendossierresultaten/vakresultaten/[leerlingid]/vak/[vakid]/lichting/[lichtingid]`](Grades.md#exam-grades-get-restv1geldendexamendossierresultatenvakresultatenleerlingidvakvakidlichtinglichtingid)
  - [Homework](Homework.md)
    - [1. Homework from appointments: `GET /rest/v1/studiewijzeritemafspraaktoekenningen`](Homework.md#1-homework-from-appointments-get-restv1studiewijzeritemafspraaktoekenningen)
    - [2. Homework from days: `GET /rest/v1/studiewijzeritemdagtoekenningen`](Homework.md#2-homework-from-days-get-restv1studiewijzeritemdagtoekenningen)
    - [3. Homework from weeks: `GET /rest/v1/studiewijzeritemweektoekenningen`](Homework.md#3-homework-from-weeks-get-restv1studiewijzeritemweektoekenningen)<br><br>
    - [1. Homework Made `PUT /rest/v1/swigemaakt/[id]`](Homework.md#1-homework-made-put-restv1swigemaaktid)
    - [2. Homework Made `PUT /rest/v1/swigemaakt/cou`](Homework.md#2-homework-made-put-restv1swigemaaktcou)
  - [Studiemateriaal](Studiemateriaal.md)
    - [General study materials: `GET /rest/v1/studiemateriaal/algemeen/[student_id]`](Studiemateriaal.md#general-study-materials-get-restv1studiemateriaalalgemeenstudent_id)
    - [Fetch subjects that have study material: `GET /rest/v1/vakken/studiemateriaal/[student_id]`](Studiemateriaal.md#fetch-subjects-that-have-study-material-get-restv1vakkenstudiemateriaalstudent_id)
    - [Fetch study material: `GET /rest/v1/studiemateriaal/[student_id]/vak/[stubject_uuid]`](Studiemateriaal.md#fetch-study-material-get-restv1studiemateriaalstudent_idvakstubject_uuid)
    - [Fetch file from study material folder: `GET /gcs/download/[filename]`](Studiemateriaal.md#fetch-file-from-study-material-folder-get-gcsdownloadfilename)


<!-- /TOC -->

## Some miscellaneous stuff
<details><summary>Click to open miscellaneous stuff</summary>


 - Endpoint for the API is returned when you fetch the access token
 - Always include the header "Accept" with the value of "application/json" so you won't get XML. (except if you want XML :-) ) (the authentication stuff always returns JSON)<br><br>

 - you can do sample requests using curl, for example:

```bash
curl http://example.com/user/blah?active=true&limit=3 -d "key=value&otherkey=value" -H "AHeader: Value"
```

which will be listed here as

| Name     | Type   | Value |
|----------|--------|-------|
| id       | URL    | blah  |
| active   | Query  | true  |
| limit    | Query  | 3     |
| key      | Body   | value |
| otherkey | Body   | value |
| AHeader  | Header | Value |

When there is a value that is unique to you (like username, password, or token), it will have a value like `[username]`

I don't recommend using curl in your programming language, except for PHP but even there it's a pain. There are much better libraries.

<details><summary>A list of libraries for your language </summary>  

JavaScript: [window.fetch](https://developers.google.com/web/updates/2015/03/introduction-to-fetch)<br>
NodeJS: [node-fetch](https://github.com/bitinn/node-fetch), [HTTP from stdlib](https://nodejs.org/api/http.html), [Request](https://github.com/request/request), [Axios](https://github.com/axios/axios)<br>
Go: [net/http](https://golang.org/pkg/net/http/)<br>
Ruby: [Faraday](https://github.com/lostisland/faraday), [HTTParty](https://github.com/jnunemaker/httparty)<br>
Python: [requests](http://docs.python-requests.org/en/master/)<br>

Please add more if you know more.

</details>

</details>

## Fetching information

baseurl: returned when you fetch a token (`somtoday_api_url`), usually api.somtoday.nl.

All routes here are prefixed with that baseurl.

### Current student(s): `GET /rest/v1/leerlingen`
<details><summary>Click to open</summary>

This REST method might return multiple students (I cannot test), since it says /leerlingen (Dutch plural for student).

I suppose it returns all students the current user has access to (so if a school administrator runs it, it will return all students on the school).

#### Parameters

| Name          | Type      | Value                 |
|---------------|-----------|-----------------------|
| Authorization | Header    | Bearer [access_token] |

#### Returns

```json
{
  "items": [
    {
      "$type": "leerling.RLeerling",
      "links": [
        {
          "id": 1234,
          "rel": "self",
          "type": "leerling.RLeerling",
          "href": "https://api.somtoday.nl/rest/v1/leerlingen/1234"
        }
      ],
      "permissions": [
        {
          "full": "leerling.RLeerlingPrimer:READ:INSTANCE(1234)",
          "type": "leerling.RLeerlingPrimer",
          "operations": [
            "READ"
          ],
          "instances": [
            "INSTANCE(1234)"
          ]
        }
      ],
      "additionalObjects": {},
      "UUID": "00000000-0000-0000-0000-000000000000",
      "leerlingnummer": 402638,
      "roepnaam": "Lenn",
      "achternaam": "Steenbergen",
      "pasfotoUrl": "https://api.somtoday.nl/rest/v1/pasfoto/0792a6e2-9833-45e8-b1eb-1498cf22f10d/AbC123dEf256gHi7890AbC123dEf256g",
      "email": "lennsteenbergen@leerling.school.nl",
      "mobielNummer": "06-00000000",
      "geboortedatum": "2000-00-00",
      "geslacht": "Man"
    }
  ]
}
```

#### Example

```bash
token='<REDACTED>' school_url=https://api.somtoday.nl
curl "$school_url/rest/v1/leerlingen" -H "Authorization: Bearer $token" -H "Accept: application/json"
```

---

### Student by ID: `GET /rest/v1/leerlingen/[id]`

#### Parameters

| Name          | Type   | Value                 |
|---------------|--------|-----------------------|
| id            | URL    | [user id]             |
| Authorization | Header | Bearer [access_token] |

#### Returns

```json
{
  "items": [
    {
      "$type": "leerling.RLeerling",
      "links": [
        {
          "id": 1234,
          "rel": "self",
          "type": "leerling.RLeerling",
          "href": "https://api.somtoday.nl/rest/v1/leerlingen/1234"
        }
      ],
      "permissions": [
        {
          "full": "leerling.RLeerlingPrimer:READ:INSTANCE(1234)",
          "type": "leerling.RLeerlingPrimer",
          "operations": [
            "READ"
          ],
          "instances": [
            "INSTANCE(1234)"
          ]
        }
      ],
      "additionalObjects": {},
      "UUID": "00000000-0000-0000-0000-000000000000",
      "leerlingnummer": 402638,
      "roepnaam": "Lenn",
      "achternaam": "Steenbergen",
      "pasfotoUrl": "https://api.somtoday.nl/rest/v1/pasfoto/0792a6e2-9833-45e8-b1eb-1498cf22f10d/AbC123dEf256gHi7890AbC123dEf256g",
      "email": "lennsteenbergen@leerling.school.nl",
      "mobielNummer": "06-00000000",
      "geboortedatum": "2000-00-00",
      "geslacht": "Man"
    }
  ]
}
```

#### Example

```bash
token='<REDACTED>' id=1234
curl "$school_url/rest/v1/leerlingen/$id" -H "Authorization: Bearer $token" -H "Accept: application/json"
```

</details>

### Get message recipients: `GET /rest/v1/medewerkers/ontvangers`
<details><summary>Click to open</summary>

#### Parameters

| Name          | Type     | Value                    |
|---------------|----------|--------------------------|
| Authorization | Header   | Bearer [access_token]    |
| additional    | Parameter| vakkenDocentVoorLeerling |

#### Returns

```json
{
  "items": [
    {
      "$type": "medewerker.RMedewerker",
      "links": [
        {
          "id": 1234,
          "rel": "self",
          "type": "medewerker.RMedewerker",
          "href": "https://api.somtoday.nl/rest/v1/medewerkers/1234"
        }
      ],
      "additionalObjects": {
        "vakkenDocentVoorLeerling": {
          "$type": "LinkableWrapper",
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
              "afkorting": "dutl",
              "naam": "Duitse taal en literatuur",
              "UUID": "00000000-0000-0000-0000-000000000000"
            },
            ...
          ]
        }
      },
      "UUID": "00000000-0000-0000-0000-000000000000",
      "nummer": 308382,
      "afkorting": "vrim",
      "achternaam": "REDACTED",
      "geslacht": "VROUW",
      "voorvoegsel": "de",
      "voorletters": "M.",
      "roepnaam": "REDACTED"
    },
    ...
  ]
}
```

</details>

### Schedule: `GET /rest/v1/afspraakitems/[student-id]/jaar/[year]/week/[week]`
<details><summary>Click to open</summary>

Fetch the appointments from the schedule of the student.

#### Parameters

| Name          | Type      | Value                 |
|---------------|-----------|-----------------------|
| student_id    | URL       | [student_id]          |
| week          | URL       | [week]                |
| year          | URL       | [year]                |
| Authorization | Header    | Bearer [access_token] |


#### Returns

```json
{
  "items": [
    {
      "$type": "participatie.live.RAfspraakItem",
      "uniqueIdentifier": "00000000000000",
      "afspraakItemType": "ROOSTER",
      "locatie": "c4",
      "beginDatumTijd": "2026-09-17T09:50:00",
      "eindDatumTijd": "2026-09-17T10:40:00",
      "beginLesuur": 3,
      "eindLesuur": 3,
      "titel": "c4 - h5.fatl1 - lenm",
      "onlineDeelname": false,
      "omschrijving": "c4 - h5.fatl1 - lenm",
      "vak": {
        "$type": "participatie.live.RAfspraakVak",
        "id": 1234,
        "naam": "Franse taal en literatuur",
        "afkorting": "fatl",
        "UUID": "00000000-0000-0000-0000-000000000000"
      },
      "bijlagen": [],
      "lesgroepen": [],
      "docentNamen": [
        "Mevr. M. REDACTED"
      ],
      "statusNotifications": []
    },
    {
      "$type": "participatie.live.RAfspraakItem",
      "uniqueIdentifier": "00000000000000",
      "afspraakItemType": "ROOSTER",
      "locatie": "d4",
      "beginDatumTijd": "2026-09-15T11:50:00",
      "eindDatumTijd": "2026-09-15T12:40:00",
      "beginLesuur": 5,
      "eindLesuur": 5,
      "titel": "d4 - h5.econ1 - kogm",
      "onlineDeelname": false,
      "omschrijving": "d4 - h5.econ1 - kogm",
      "vak": {
        "$type": "participatie.live.RAfspraakVak",
        "id": 1234,
        "naam": "economie",
        "afkorting": "econ",
        "UUID": "00000000-0000-0000-0000-000000000000"
      },
      "bijlagen": [],
      "lesgroepen": [],
      "docentNamen": [
        "Mevr. M. REDACTED"
      ],
      "statusNotifications": []
    },
    {
      "$type": "participatie.live.RAfspraakItem",
      "uniqueIdentifier": "00000000000000",
      "afspraakItemType": "INDIVIDUEEL",
      "beginDatumTijd": "2026-09-15T08:00:00",
      "eindDatumTijd": "2026-09-15T08:10:00",
      "titel": "Lesbrief Markt & Overheid mee ipv Vragers & Aanbieders! ",
      "onlineDeelname": false,
      "omschrijving": "<p>Denk eraan dat je de lesbrief Markt &amp; Overheid mee neemt in plaats van Vragers &amp; Aanbieders</p>",
      "vak": {
        "$type": "participatie.live.RAfspraakVak",
        "id": 1234,
        "naam": "economie",
        "afkorting": "econ",
        "UUID": "00000000-0000-0000-0000-000000000000"
      },
      "bijlagen": [],
      "lesgroepen": [
        {
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
              "full": "lesgroep.RLesgroep:READ,UPDATE,DELETE:INSTANCE(1234)",
              "type": "lesgroep.RLesgroep",
              "operations": ["READ", "UPDATE", "DELETE"],
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
                "full": "onderwijsinrichting.RSchooljaar:READ,UPDATE,DELETE:INSTANCE(1234)",
                "type": "onderwijsinrichting.RSchooljaar",
                "operations": ["READ", "UPDATE", "DELETE"],
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
                "full": "onderwijsinrichting.RVak:READ,UPDATE,DELETE:INSTANCE(1234)",
                "type": "onderwijsinrichting.RVak",
                "operations": ["READ", "UPDATE", "DELETE"],
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
                "full": "instelling.RVestiging:READ,UPDATE,DELETE:INSTANCE(1234)",
                "type": "instelling.RVestiging",
                "operations": ["READ", "UPDATE", "DELETE"],
                "instances": ["INSTANCE(1234)"]
              }
            ],
            "additionalObjects": {},
            "naam": "REDACTED",
            "afkorting": "REDACTED",
            "UUID": "00000000-0000-0000-0000-000000000000",
            "uuid": "00000000-0000-0000-0000-000000000000"
          }
        }
      ],
      "docentNamen": [
        "Mevr. M. REDACTED"
      ],
      "statusNotifications": []
    }
  ]
}
```

#### Example

```bash
token='<REDACTED>' student_id=1234 year=2026 week=37
curl "https://api.somtoday.nl/rest/v1/afspraakitems/$student_id/jaar/$year/week/$week" -H "Authorization: Bearer $token" -H "Accept: application/json"
```

</details>

### Absence Reports: `GET /rest/v1/absentiemeldingen`
<details><summary>Click to open</summary>

Fetches the absence reports of the user

#### Parameters

| Name           | Type      | Value                 |
|----------------|-----------|-----------------------|
| Authorization  | Header    | Bearer [access_token] |
| begindatumtijd | Parameter | yyyy-MM-dd            |
| einddatumtijd  | Parameter | yyyy-MM-dd            |

#### Returns

Array of absance reports

```json
{
  "items": [
    {
      "$type": "participatie.RAbsentieMelding",
      "links": [
        {
          "id": 1234567890123,
          "rel": "self",
          "type": "participatie.RAbsentieMelding",
          "href": "{{api_url}}/rest/v1/waarnemingen/1234567890123"
        }
      ],
      "permissions": [],
      "additionalObjects": {},
      "leerling": {
        "links": [
          {
            "id": 1234567890,
            "rel": "self",
            "type": "leerling.RLeerlingPrimer",
            "href": "{{api_url}}/rest/v1/leerlingen/1234567890"
          }
        ],
        "permissions": [],
        "additionalObjects": {},
        "UUID": "12abc34e-12a3-1a2b-a1b2-1a2b34cd5e67",
        "leerlingnummer": 100000,
        "roepnaam": "Name",
        "achternaam": "Name"
      },
      "absentieReden": {
        "links": [
          {
            "id": 1234567890,
            "rel": "self",
            "type": "participatie.RAbsentieRedenPrimer",
            "href": "{{api_url}}/rest/v1/absentieredenen/1234567890"
          }
        ],
        "permissions": [],
        "additionalObjects": {},
        "absentieSoort": "Absent",
        "afkorting": "XC",
        "omschrijving": "Onbekend",
        "geoorloofd": false
      },
      "datumTijdInvoer": "yyyy-MM-dd'T'HH:mm:ss.SSS+HH:mm",
      "beginDatumTijd": "yyyy-MM-dd'T'HH:mm:ss.SSS+HH:mm",
      "eindDatumTijd": "yyyy-MM-dd'T'HH:mm:ss.SSS+HH:mm",
      "beginLesuur": 3,
      "eindLesuur": 3,
      "afgehandeld": true,
      "eigenaar": {
        "links": [
          {
            "id": 1234567890,
            "rel": "self",
            "type": "medewerker.RMedewerker",
            "href": "{{api_url}}/rest/v1/medewerkers/1234567890"
          }
        ],
        "permissions": [],
        "additionalObjects": {},
        "UUID": "12abc34e-12a3-1a2b-a1b2-1a2b34cd5e67",
        "nummer": 100000,
        "afkorting": "HH",
        "achternaam": "Henk",
        "geslacht": "MAN",
        "voorletters": "H.H.",
        "roepnaam": "Hans"
      }
    }
  ]
}
```
</details>

### Study Guides: `GET /rest/v1/studiewijzers`
<details><summary>Click to open</summary>

Fetches the study guides for the user

#### Parameters

| Name          | Type      | Value                 |
|---------------|-----------|-----------------------|
| Authorization | Header    | Bearer [access_token] |
| additional    | Parameter | leerlingen            |
| additional    | Parameter | bijlagen              |
| additional    | Parameter | externeMaterialen     |
| additional    | Parameter | bijlageMappen         |

The additional parameters are optional GET parameters to include information in the result. `leerlingen` will only give back 1 result when queried by a student, but will fetch all students when queried by a teacher/school admin.

#### Returns

Depending on the additional parameters, some of the items in the result may not be present. Assuming all 4 are set:

```json
{
    "items": [
        {
            "$type": "studiewijzer.RStudiewijzer",
            "links": [
                {
                    "id": 3709468886305,
                    "rel": "self",
                    "type": "studiewijzer.RStudiewijzer",
                    "href": "https://api.somtoday.nl/rest/v1/studiewijzers/3709468886305"
                }
            ],
            "permissions": [
                {
                    "full": "studiewijzer.RStudiewijzer:READ:INSTANCE(3709468886305)",
                    "type": "studiewijzer.RStudiewijzer",
                    "operations": [
                        "READ"
                    ],
                    "instances": [
                        "INSTANCE(3709468886305)"
                    ]
                }
            ],
            "additionalObjects": {
                "bijlageMappen": {
                    "$type": "LinkableWrapper",
                    "items": []
                },
                "bijlagen": {
                    "$type": "LinkableWrapper",
                    "items": []
                },
                "leerlingen": {
                    "$type": "LinkableWrapper",
                    "items": [
                        {
                            "$type": "leerling.RLeerlingPrimer",
                            "links": [
                                {
                                    "id": 9496745174,
                                    "rel": "self",
                                    "type": "leerling.RLeerlingPrimer",
                                    "href": "https://api.somtoday.nl/rest/v1/leerlingen/9496745174"
                                }
                            ],
                            "permissions": [
                                {
                                    "full": "leerling.RLeerlingPrimer:READ:INSTANCE(9496745174)",
                                    "type": "leerling.RLeerlingPrimer",
                                    "operations": [
                                        "READ"
                                    ],
                                    "instances": [
                                        "INSTANCE(9496745174)"
                                    ]
                                }
                            ],
                            "additionalObjects": {},
                            "UUID": "f8cf6f6c-c213-4526-8ba1-6a306cf724a4",
                            "leerlingnummer": 123456,
                            "roepnaam": "{{first_name}}",
                            "achternaam": "{{last_name}}"
                        }
                    ]
                },
                "externeMaterialen": {
                    "$type": "LinkableWrapper",
                    "items": []
                }
            },
            "uuid": "4d2188a0-03d8-4dca-9f51-0e54d3c353c6",
            "naam": "vwo5.schka",
            "vestiging": {
                "links": [
                    {
                        "id": 9496567717,
                        "rel": "self",
                        "type": "instelling.RVestiging",
                        "href": "https://api.somtoday.nl/rest/v1/vestigingen/9496567717"
                    }
                ],
                "permissions": [
                    {
                        "full": "instelling.RVestiging:READ:INSTANCE(9496567717)",
                        "type": "instelling.RVestiging",
                        "operations": [
                            "READ"
                        ],
                        "instances": [
                            "INSTANCE(9496567717)"
                        ]
                    }
                ],
                "additionalObjects": {},
                "naam": "Stella Maris College Meerssen"
            },
            "lesgroep": {
                "links": [
                    {
                        "id": 3543707887108,
                        "rel": "self",
                        "type": "lesgroep.RLesgroep",
                        "href": "https://api.somtoday.nl/rest/v1/lesgroepen/3543707887108"
                    }
                ],
                "permissions": [
                    {
                        "full": "lesgroep.RLesgroep:READ:INSTANCE(3543707887108)",
                        "type": "lesgroep.RLesgroep",
                        "operations": [
                            "READ"
                        ],
                        "instances": [
                            "INSTANCE(3543707887108)"
                        ]
                    }
                ],
                "additionalObjects": {},
                "UUID": "d4afb5b8-fbf6-4bbd-ac73-cb50cc883392",
                "naam": "vwo5.schka",
                "schooljaar": {
                    "$type": "onderwijsinrichting.RSchooljaar",
                    "links": [
                        {
                            "id": 40851957,
                            "rel": "self",
                            "type": "onderwijsinrichting.RSchooljaar",
                            "href": "https://api.somtoday.nl/rest/v1/schooljaren/40851957"
                        }
                    ],
                    "permissions": [
                        {
                            "full": "onderwijsinrichting.RSchooljaar:READ:INSTANCE(40851957)",
                            "type": "onderwijsinrichting.RSchooljaar",
                            "operations": [
                                "READ"
                            ],
                            "instances": [
                                "INSTANCE(40851957)"
                            ]
                        }
                    ],
                    "additionalObjects": {},
                    "naam": "2021/2022",
                    "vanafDatum": "2021-08-01",
                    "totDatum": "2022-07-31",
                    "isHuidig": true
                },
                "vak": {
                    "links": [
                        {
                            "id": 9505018979,
                            "rel": "self",
                            "type": "onderwijsinrichting.RVak",
                            "href": "https://api.somtoday.nl/rest/v1/vakken/9505018979"
                        }
                    ],
                    "permissions": [
                        {
                            "full": "onderwijsinrichting.RVak:READ:INSTANCE(9505018979)",
                            "type": "onderwijsinrichting.RVak",
                            "operations": [
                                "READ"
                            ],
                            "instances": [
                                "INSTANCE(9505018979)"
                            ]
                        }
                    ],
                    "additionalObjects": {},
                    "afkorting": "schk",
                    "naam": "Scheikunde"
                },
                "heeftStamgroep": false,
                "examendossierOndersteund": true,
                "vestiging": {
                    "links": [
                        {
                            "id": 9496567717,
                            "rel": "self",
                            "type": "instelling.RVestiging",
                            "href": "https://api.somtoday.nl/rest/v1/vestigingen/9496567717"
                        }
                    ],
                    "permissions": [
                        {
                            "full": "instelling.RVestiging:READ:INSTANCE(9496567717)",
                            "type": "instelling.RVestiging",
                            "operations": [
                                "READ"
                            ],
                            "instances": [
                                "INSTANCE(9496567717)"
                            ]
                        }
                    ],
                    "additionalObjects": {},
                    "naam": "Stella Maris College Meerssen"
                }
            }
        }
        ...
    ]
}
```

</details>

### Subjects: `GET /rest/v1/vakken`
<details><summary>Click to open</summary>

Fetches the subjects for the user

#### Parameters

| Name          | Type   | Value                 |
|---------------|--------|-----------------------|
| Authorization | Header | Bearer [access_token] |

#### Returns

```json
{
  "items": [
    {
      "$type": "onderwijsinrichting.RVak",
      "links": [
        {
          "id": 123456789,
          "rel": "self",
          "type": "onderwijsinrichting.RVak",
          "href": "https://api.somtoday.nl/rest/v1/vakken/123456789"
        }
      ],
      "permissions": [
        {
          "full": "onderwijsinrichting.RVak:READ:INSTANCE(123456789)",
          "type": "onderwijsinrichting.RVak",
          "operations": [
            "READ"
          ],
          "instances": [
            "INSTANCE(123456789)"
          ]
        }
      ],
      "additionalObjects": {},
      "afkorting": "<abbreviation>",
      "naam": "<subject>"
    }
	...
  ]
}
```

</details>

### Account: `GET /rest/v1/account/` / `GET /rest/v1/account/[id]` / `GET /rest/v1/account/me`
<details><summary>Click to open</summary>

Fetches information about the account that is connected with the Somtoday access token

#### Parameters

| Name          | Type      | Value                 |
|---------------|-----------|-----------------------|
| id            | URL       | [user-id]             |
| Authorization | Header    | Bearer [access_token] |
| additional    | Parameter | restricties           |


#### Returns



```json
{
  "items": [
    {
      "$type": "auth.RAccount",
      "links": [
        {
          "id": 1234567890,
          "rel": "self",
          "type": "auth.RAccount",
          "href": "https://api.somtoday.nl/rest/v1/account/1234567890"
        }
      ],
      "permissions": [
        {
          "full": "auth.RAccount:READ:INSTANCE(1234567890)",
          "type": "auth.RAccount",
          "operations": [
            "READ"
          ],
          "instances": [
            "INSTANCE(1234567890)"
          ]
        }
      ],
      "additionalObjects": {
        "restricties": {
          "$type": "LinkableWrapper",
          "items": [
            {
              "$type": "restricties.REloRestricties",
              "links": [],
              "permissions": [],
              "additionalObjects": {},
              "vestigingsId": REDACTED,
              "leerlingId": REDACTED,
              "mobieleAppAan": true,
              "studiewijzerAan": true,
              "berichtenVerzendenAan": false,
              "leermiddelenAan": true,
              "adviezenTokenAan": true,
              "opmerkingRapportCijferTonenAan": true,
              "periodeGemiddeldeTonenResultaatAan": true,
              "rapportGemiddeldeTonenResultaatAan": true,
              "rapportCijferTonenResultaatAan": true,
              "toetssoortgemiddeldenAan": true,
              "seResultaatAan": true,
              "stamgroepLeerjaarAan": true,
              "emailWijzigenAan": false,
              "mobielWijzigenAan": false,
              "wachtwoordWijzigenAan": true,
              "absentiesBekijkenAan": true,
              "absentieConstateringBekijkenAan": true,
              "absentieMaatregelBekijkenAan": true,
              "absentieMeldingBekijkenAan": true,
              "berichtenBekijkenAan": true,
              "cijfersBekijkenAan": true,
              "huiswerkBekijkenAan": true,
              "nieuwsBekijkenAan": true,
              "pasfotoLeerlingTonenAan": true,
              "pasfotoMedewerkerTonenAan": false,
              "profielBekijkenAan": true,
              "roosterBekijkenAan": true,
              "roosterBeschikbaarIcalAan": true,
              "vakkenBekijkenAan": true,
              "lesurenVerbergenSettingAan": false
            }
          ]
        }
      },
      "gebruikersnaam": "[REDACTED]",
      "accountPermissions": [],
      "persoon": {
        "$type": "leerling.RLeerlingPrimer",
        "links": [
          {
            "id": "0123456789",
            "rel": "self",
            "type": "leerling.RLeerlingPrimer",
            "href": "https://api.somtoday.nl/rest/v1/leerlingen/0123456789"
          }
        ],
        "permissions": [
          {
            "full": "leerling.RLeerlingPrimer:READ:INSTANCE(1409824200)",
            "type": "leerling.RLeerlingPrimer",
            "operations": [
              "READ"
            ],
            "instances": [
              "INSTANCE(0123456789)"
            ]
          }
        ],
        "additionalObjects": {},
        "UUID": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
        "leerlingnummer": 100000,
        "roepnaam": "Name",
        "voorvoegsel": "Name",
        "achternaam": "Name"
      }
    }
  ]
}
```

</details>

### Schooljaren: `GET /rest/v1/schooljaren` / `GET /rest/v1/schooljaren/[id]`
<details><summary>Click to open</summary>

Fetches information about a school year

#### Parameters

| Name          | Type   | Value                 |
|---------------|--------|-----------------------|
| id            | URL    | [id]                  |
| id            | URL    | huidig                |
| Authorization | Header | Bearer [access_token] |

When you want info about the current school year add /huidig to the url

#### Returns

```json
{
  "items": [
    {
      "$type": "onderwijsinrichting.RSchooljaar",
      "links": [
        {
          "id": 40851958, //this id is for everyone the same (in this case for year 2022/2023)
          "rel": "self",
          "type": "onderwijsinrichting.RSchooljaar",
          "href": "https://api.somtoday.nl/rest/v1/schooljaren/40851958"
        }
      ],
      "permissions": [
        {
          "full": "onderwijsinrichting.RSchooljaar:READ:INSTANCE(40851958)",
          "type": "onderwijsinrichting.RSchooljaar",
          "operations": [
            "READ"
          ],
          "instances": [
            "INSTANCE(40851958)"
          ]
        }
      ],
      "additionalObjects": {},
      "naam": "2022/2023",
      "vanafDatum": "2022-08-01",
      "totDatum": "2023-07-31",
      "isHuidig": true
    },
    ...
  ]
}
```

</details>

### Vakkeuzes: `GET /rest/v1/vakkeuzes`
<details><summary>Click to open</summary>

Fetches all the subjects you are currently enrolled in.

#### Parameters

| Name          | Type      | Value                 |
|---------------|-----------|-----------------------|
| Authorization | Header    | Bearer [access_token] |
| additional    | Parameter | vaknormering          |
| additional    | Parameter | actiefOpPeildatum     |

#### Returns

```json
{
  "items": [
    {
      "$type": "onderwijsinrichting.RVakkeuze",
      "links": [
        {
          "id": xxxxxxxxxx,
          "rel": "self",
          "type": "onderwijsinrichting.RVakkeuze",
          "href": "https://api.somtoday.nl/rest/v1/vakkeuzes/xxxxxxxxxx"
        }
      ],
      "permissions": [
        {
          "full": "onderwijsinrichting.RVakkeuze:READ:INSTANCE(xxxxxxxxxx)",
          "type": "onderwijsinrichting.RVakkeuze",
          "operations": [
            "READ"
          ],
          "instances": [
            "INSTANCE(xxxxxxxxxx)"
          ]
        }
      ],
      "additionalObjects": {
        "vaknormering": {
          "$type": "onderwijsinrichting.RVakNormering",
          "vakId": yyyyyyyyyy,
          "toetsnormering1": "Standaard",
          "toetsnormering2": "Alternatief"
        }
      },
      "vak": {
        "links": [
          {
            "id": yyyyyyyyyy,
            "rel": "self",
            "type": "onderwijsinrichting.RVak",
            "href": "https://api.somtoday.nl/rest/v1/vakken/yyyyyyyyyy"
          }
        ],
        "permissions": [
          {
            "full": "onderwijsinrichting.RVak:READ:INSTANCE(yyyyyyyyyy)",
            "type": "onderwijsinrichting.RVak",
            "operations": [
              "READ"
            ],
            "instances": [
              "INSTANCE(yyyyyyyyyy)"
            ]
          }
        ],
        "additionalObjects": {},
        "afkorting": "ne",
        "naam": "Nederlandse taal"
      }
    },
    ...
  ]
}
```

</details>

### Waarnemingen: `GET /rest/v1/waarnemingen`
<details><summary>Click to open</summary>

Fetches all the waarnemingen currently tied to your account, filter them by date, isGeoorloofd and/or waarnemingSoort.

#### Parameters

| Name                       | Type      | Value                 |
|----------------------------|-----------|-----------------------|
| Authorization              | Header    | Bearer [access_token] |
| waarnemingSoort (optional) | Parameter | Afwezig/aanwezig      |
| isGeoorloofd (optional)    | Parameter | true/false            |

You can, if you want, provide dates to filter the results. If you don't provide any dates, it will return all the results. 
You can either provide a date range or a single date. If you provide a single date, it will return all the results from that date. If you provide a date range, it will return all the results inbetween those dates.

| Date types      | Type      | Value       |
|-----------------|-----------|-------------|
| begintNaOfOp    | Parameter | yyyy-MM-dd  |
| OR              |
| beginDatumTijd  | Parameter | yyyy-MM-dd  |
| eindDatumTijd   | Parameter | yyyy-MM-dd  |

#### Returns

```json
{
  "items": [
    {
      "$type": "participatie.RWaarneming",
      "links": [
        {
          "id": 1234567891234,
          "rel": "self",
          "type": "participatie.RWaarneming",
          "href": "https://api.somtoday.nl/rest/v1/waarnemingen/1234567891234"
        }
      ],
      "permissions": [
        {
          "full": "participatie.RWaarneming:READ:INSTANCE(1234567891234)",
          "type": "participatie.RWaarneming",
          "operations": [
            "READ"
          ],
          "instances": [
            "INSTANCE(1234567891234)"
          ]
        }
      ],
      "additionalObjects": {},
      "beginDatumTijd": "2023-01-09T11:05:00.000+01:00",
      "eindDatumTijd": "2023-01-09T11:55:00.000+01:00",
      "beginLesuur": 4,
      "eindLesuur": 4,
      "waarnemingSoort": "Aanwezig",
      "leerling": {
        "links": [
          {
            "id": 1234567890,
            "rel": "self",
            "type": "leerling.RLeerlingPrimer",
            "href": "https://api.somtoday.nl/rest/v1/leerlingen/1234567890"
          }
        ],
        "permissions": [
          {
            "full": "leerling.RLeerlingPrimer:READ:INSTANCE(1234567890)",
            "type": "leerling.RLeerlingPrimer",
            "operations": [
              "READ"
            ],
            "instances": [
              "INSTANCE(1234567890)"
            ]
          }
        ],
        "additionalObjects": {},
        "UUID": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
        "leerlingnummer": 100000,
        "roepnaam": "Name",
        "voorvoegsel": "Name",
        "achternaam": "Name"
      },
      "afspraak": {
        "links": [
          {
            "id": 12345678901345,
            "rel": "self",
            "type": "participatie.RAfspraakPrimer",
            "href": "https://api.somtoday.nl/rest/v1/afspraken/12345678901345"
          }
        ],
        "permissions": [
          {
            "full": "participatie.RAfspraak:READ:INSTANCE(12345678901345)",
            "type": "participatie.RAfspraak",
            "operations": [
              "READ"
            ],
            "instances": [
              "INSTANCE(12345678901345)"
            ]
          }
        ],
        "additionalObjects": {},
        "afspraakType": {
          "links": [
            {
              "id": 1234567890,
              "rel": "self",
              "type": "participatie.RAfspraakType",
              "href": "https://api.somtoday.nl/rest/v1/afspraaktype/1234567890"
            }
          ],
          "permissions": [
            {
              "full": "participatie.RAfspraakType:READ:INSTANCE(1234567890)",
              "type": "participatie.RAfspraakType",
              "operations": [
                "READ"
              ],
              "instances": [
                "INSTANCE(1234567890)"
              ]
            }
          ],
          "additionalObjects": {},
          "naam": "LES",
          "omschrijving": "LES",
          "standaardKleur": -16448251,
          "categorie": "Rooster",
          "activiteit": "Verplicht",
          "percentageIIVO": 100,
          "presentieRegistratieDefault": true,
          "actief": true,
          "vestiging": {
            "$type": "instelling.RVestiging",
            "links": [
              {
                "id": 1234567890,
                "rel": "self",
                "type": "instelling.RVestiging",
                "href": "https://api.somtoday.nl/rest/v1/vestigingen/1234567890"
              }
            ],
            "permissions": [
              {
                "full": "instelling.RVestiging:READ:INSTANCE(1234567890)",
                "type": "instelling.RVestiging",
                "operations": [
                  "READ"
                ],
                "instances": [
                  "INSTANCE(1234567890)"
                ]
              }
            ],
            "additionalObjects": {},
            "naam": "De super coole school",
          }
        },
        "locatie": "lokaal naam",
        "beginDatumTijd": "2023-01-09T11:05:00.000+01:00",
        "eindDatumTijd": "2023-01-09T11:55:00.000+01:00",
        "beginLesuur": 4,
        "eindLesuur": 4,
        "titel": "titel"
      },
      "afgehandeld": true,
      "invoerDatum": "2023-01-09T11:09:08.000+01:00",
      "laatstGewijzigdDatum": "2023-01-09T11:09:08.000+01:00",
      "herkomst": "Medewerker",
      "ingevoerdDoor": {
        "links": [
          {
            "id": 1234567890123,
            "rel": "self",
            "type": "medewerker.RMedewerkerPrimer",
            "href": "https://api.somtoday.nl/rest/v1/medewerkers/1234567890123"
          }
        ],
        "permissions": [],
        "additionalObjects": {},
        "UUID": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
        "nummer": 12345678,
        "afkorting": "afkorting",
        "achternaam": "name",
        "geslacht": "VROUW/MAN",
        "voorletters": "voorletter(s)",
        "roepnaam": "roepnaam"
      },
      "laatstGewijzigdDoor": {
        "links": [
          {
            "id": 1234567890123,
            "rel": "self",
            "type": "medewerker.RMedewerkerPrimer",
            "href": "https://api.somtoday.nl/rest/v1/medewerkers/1234567890123"
          }
        ],
        "permissions": [],
        "additionalObjects": {},
        "UUID": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
        "nummer": 12345678,
        "afkorting": "afkorting",
        "achternaam": "name",
        "geslacht": "VROUW/MAN",
        "voorletters": "voorletter(s)",
        "roepnaam": "roepnaam"
      }
    },
    ...
  ]
}
```
</details>

### Messages: `GET /rest/v1/boodschappen/conversaties`
<details><summary>Click to open</summary>
Fetches your SomToday messages/berichten.

#### Parameters

| Name          | Type      | Value                  |
|---------------|-----------|------------------------|
| Authorization | Header    | Bearer [access_token]  |
| additional    | Parameter | verzondenDoorGebruiker |
| additional    | Parameter | verzenderCorrespondent |
| additional    | Parameter | aantalExtraOntvangers  |
| additional    | Parameter | actiefVoorGebruiker    |
| alle          | Parameter | true/false             |

#### Returns
```json
{
    "items":[
        {
            "$type":"berichten.RBoodschapConversatie",
            "boodschappen":[
                {
                    "links":[
                        {
                            "id":1234567890,
                            "rel":"koppeling",
                            "type":"berichten.RBoodschap"
                        }
                    ],
            "permissions":[],
            "additionalObjects":{
                "aantalExtraOntvangers":0,
                "verzondenDoorGebruiker":false,
                "ontvangerCorrespondenten":{
                    "$type":"NonLinkableWrapper",
                    "items":[
                        {
                            "$type":"berichten.RBoodschapCorrespondent",
                            "naam":"REDACTED",
                            "vakken":[]
                        },
                            {
                                "$type":"berichten.RBoodschapCorrespondent",
                                "naam":"REDACTED",
                                "vakken":[]
                                }
                    ]             
                },
                    "verzenderCorrespondent":{
                        "$type":"berichten.RBoodschapCorrespondent",
                        "naam":"REDACTED",
                        "sorteerNaam":"REDACTED",
                        "initialen":"REDACTED",
                        "vakken":[
                            {
                                "links":[
                                    {
                                        "id":1234567890,
                                        "rel":"self",
                                        "type":"onderwijsinrichting.RVak",
                                        "href":"https://api.somtoday.nl/rest/v1/vakken/1234567890"
                                        }
                                    ],
                                    "permissions":[
                                        {
                                            "full":"onderwijsinrichting.RVak:READ,UPDATE,DELETE:INSTANCE(1234567890)",
                                            "type":"onderwijsinrichting.RVak",
                                            "operations":["READ","UPDATE","DELETE"],
                                            "instances":["INSTANCE(1234567890)"]
                                        }
                                    ],
                                    "additionalObjects":{},
                                    "afkorting":"schk",
                                    "naam":"scheikunde",
                                    "UUID":"UUID"
                            }
                        ]
                    },
                    "actiefVoorGebruiker":true,
                    "isOuderavondUitnodiging":false
            },
            "startPublicatie":"tijd",
            "verzendDatum":"tijd",
            "wijzigingsDatum":"tijd",
            "draft":false,
            "onderwerp":"REDACTED",
            "inhoud":"REDACTED",
            "prioriteit":"NORMAAL",
            "notificatieType":"Bericht",
            "bijlages":[
                {
                    "links":[
                        {
                            "id":1234567890,
                            "rel":"koppeling",
                            "type":"berichten.RBoodschapBijlage"
                        }
                    ],
                    "permissions":[],
                    "additionalObjects":{},
                    "assemblyResults":[
                        {
                            "links":[
                                {
                                    "id":1234567890,
                                    "rel":"koppeling",
                                    "type":"cloudfiles.bestanden.RAssemblyResult"
                                }
                            ],
                            "permissions":[],
                            "additionalObjects":{},
                            "assemblyFileType":"MISC",
                            "fileExtension":"xlsx",
                            "mimeType":"application/vnd.openxmlformats-officedocument.spreadsheetml.sheet",
                            "fileSize":11039,
                            "fileType":"office",
                            "fileUrl":"REDACTED.xlsx",
                            "sslUrl":"REDACTED.xlsx",
                            "fileName":"REDACTED.xlsx"
                        }
                    ],
                    "sortering":0
                }
            ]
                }
            ]
        },
        ...
    ]
}
```
</details>

### Schoolgegevens: `GET /rest/v1/leerlingen/[id]/schoolgegevens` 
<details><summary>Click to open</summary>

Fetches info about the school, including your mentor.

#### Parameters

| Name          | Type   | Value                 |
|---------------|--------|-----------------------|
| id            | URL    | [user id]             |
| Authorization | Header | Bearer [access_token] |

#### Returns

```json
[
    {
        "leerlingId": 1234,
        "instellingsnaam": "REDACTED",
        "huidigeVestiging": {
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
                    "operations": [
                        "READ"
                    ],
                    "instances": [
                        "INSTANCE(1234)"
                    ]
                }
            ],
            "additionalObjects": {},
            "naam": "REDACTED",
            "afkorting": "REDACTED",
            "UUID": "00000000-0000-0000-0000-000000000000",
            "uuid": "00000000-0000-0000-0000-000000000000"
        },
        "plaats": "REDACTED",
        "straat": "REDACTED",
        "postcode": "REDACTED",
        "telefoonnummer": "REDACTED",
        "email": "info@school.nl",
        "leerjaar": 5,
        "stamgroepnaam": "h5c",
        "mentoren": [
            "G. REDACTED"
        ],
        "loopbaan": "a1b - h2a - h3a - h4b - h5c",
        "opleidingNaam": "HAVO-EM"
    }
]
```

</details>

### Vakanties: `GET /rest/v1/vakanties/leerling/[id]`
<details><summary>Click to open</summary>

Fetches info about the school, including your mentor.

#### Parameters

| Name          | Type   | Value                 |
|---------------|--------|-----------------------|
| id            | URL    | [user id]             |
| Authorization | Header | Bearer [access_token] |

#### Returns

```json
{
    "items": [
        {
            "$type": "participatie.RVakantie",
            "links": [
                {
                    "id": 123456789,
                    "rel": "self",
                    "type": "participatie.RVakantie",
                    "href": "https://api.somtoday.nl/rest/v1/vakanties/123456789"
                }
            ],
            "permissions": [
                {
                    "full": "participatie.RVakantie:READ:INSTANCE(123456789)",
                    "type": "participatie.RVakantie",
                    "operations": [
                        "READ"
                    ],
                    "instances": [
                        "INSTANCE(123456789)"
                    ]
                }
            ],
            "additionalObjects": {},
            "naam": "Herfstvakantie",
            "beginDatum": "2023-10-16T00:00:00.000+02:00",
            "eindDatum": "2023-10-20T00:00:00.000+02:00"
        },
        ...
    ]
}
```

</details>

### Studiemateriaal: `GET /rest/v1/vakken/studiemateriaal/[id]` & `GET rest/v1/vakken/studiemateriaal/[id]/vak/[uuid]` & `/rest/v1/studiemateriaal/algemeen/[id]`
<details><summary>Click to open</summary>

Fetches all studiemateriaal. (I.E. Annual supplements, online textbooks, etc.)

First, make a request to `GET /rest/v1/vakken/studiemateriaal/[id]`. And then to `/rest/v1/vakken/studiemateriaal/[id]/vak/[uuid]` with the UUID of subject which studiemateriaal you want to fetch. 

#### Parameters

| Name          | Type   | Value                 |
|---------------|--------|-----------------------|
| id            | URL    | [user id]             |
| Authorization | Header | Bearer [access_token] |

#### Returns

`GET /rest/v1/vakken/studiemateriaal/[id]` returns:

```json
{
    "items": [
        {
            "$type": "onderwijsinrichting.RVak",
            "links": [
                {
                    "id": 123456789,
                    "rel": "self",
                    "type": "onderwijsinrichting.RVak",
                    "href": "https://api.somtoday.nl/rest/v1/vakken/123456789"
                }
            ],
            "permissions": [
                {
                    "full": "onderwijsinrichting.RVak:READ:INSTANCE(123456789)",
                    "type": "onderwijsinrichting.RVak",
                    "operations": [
                        "READ"
                    ],
                    "instances": [
                        "INSTANCE(123456789)"
                    ]
                }
            ],
            "additionalObjects": {},
            "afkorting": "ne",
            "naam": "Nederlandse taal",
            "UUID": "REDACTED"
        },
        ...
    ]
}
```
`GET /rest/v1/vakken/studiemateriaal/[id]/vak/[uuid]` returns:

```json
{
    "$type": "studiewijzer.RStudieMateriaal",
    "studiewijzer": {
        "links": [
            {
                "id": 123456789,
                "rel": "self",
                "type": "studiewijzer.RStudiewijzer",
                "href": "https://api.somtoday.nl/rest/v1/studiewijzers/123456789"
            }
        ],
        "permissions": [
            {
                "full": "studiewijzer.RStudiewijzer:READ:INSTANCE(123456789)",
                "type": "studiewijzer.RStudiewijzer",
                "operations": [
                    "READ"
                ],
                "instances": [
                    "INSTANCE(123456789)"
                ]
            }
        ],
        "additionalObjects": {},
        "uuid": "Redacted",
        "naam": "Nederland",
        "vestiging": {
            "links": [
                {
                    "id": 123456789,
                    "rel": "self",
                    "type": "instelling.RVestiging",
                    "href": "https://api.somtoday.nl/rest/v1/vestigingen/123456789"
                }
            ],
            "permissions": [
                {
                    "full": "instelling.RVestiging:READ:INSTANCE(123456789)",
                    "type": "instelling.RVestiging",
                    "operations": [
                        "READ"
                    ],
                    "instances": [
                        "INSTANCE(123456789)"
                    ]
                }
            ],
            "additionalObjects": {},
            "naam": "REDACTED",
            "uuid": "REDACTED"
        },
        "lesgroep": {
            "links": [
                {
                    "id": 123456789,
                    "rel": "self",
                    "type": "lesgroep.RLesgroep",
                    "href": "https://api.somtoday.nl/rest/v1/lesgroepen/123456789"
                }
            ],
            "permissions": [
                {
                    "full": "lesgroep.RLesgroep:READ:INSTANCE(123456789)",
                    "type": "lesgroep.RLesgroep",
                    "operations": [
                        "READ"
                    ],
                    "instances": [
                        "INSTANCE(123456789)"
                    ]
                }
            ],
            "additionalObjects": {},
            "UUID": "REDACTED",
            "naam": "REDACTED",
            "omschrijving": "REDACTED",
            "schooljaar": {
                "$type": "onderwijsinrichting.RSchooljaar",
                "links": [
                    {
                        "id": 12345689,
                        "rel": "self",
                        "type": "onderwijsinrichting.RSchooljaar",
                        "href": "https://api.somtoday.nl/rest/v1/schooljaren/12345689"
                    }
                ],
                "permissions": [
                    {
                        "full": "onderwijsinrichting.RSchooljaar:READ:INSTANCE(12345689)",
                        "type": "onderwijsinrichting.RSchooljaar",
                        "operations": [
                            "READ"
                        ],
                        "instances": [
                            "INSTANCE(12345689)"
                        ]
                    }
                ],
                "additionalObjects": {},
                "naam": "2023/2024",
                "vanafDatum": "2023-08-01",
                "totDatum": "2024-07-31",
                "isHuidig": true
            },
            "vak": {
                "links": [
                    {
                        "id": 12345689,
                        "rel": "self",
                        "type": "onderwijsinrichting.RVak",
                        "href": "https://api.somtoday.nl/rest/v1/vakken/12345689"
                    }
                ],
                "permissions": [
                    {
                        "full": "onderwijsinrichting.RVak:READ:INSTANCE(12345689)",
                        "type": "onderwijsinrichting.RVak",
                        "operations": [
                            "READ"
                        ],
                        "instances": [
                            "INSTANCE(12345689)"
                        ]
                    }
                ],
                "additionalObjects": {},
                "afkorting": "ne",
                "naam": "Nederlandse taal",
                "UUID": "REDACTED"
            },
            "heeftStamgroep": false,
            "examendossierOndersteund": false,
            "vestiging": {
                "links": [
                    {
                        "id": 12345689,
                        "rel": "self",
                        "type": "instelling.RVestiging",
                        "href": "https://api.somtoday.nl/rest/v1/vestigingen/12345689"
                    }
                ],
                "permissions": [
                    {
                        "full": "instelling.RVestiging:READ:INSTANCE(12345689)",
                        "type": "instelling.RVestiging",
                        "operations": [
                            "READ"
                        ],
                        "instances": [
                            "INSTANCE(12345689)"
                        ]
                    }
                ],
                "additionalObjects": {},
                "naam": "REDACTED",
                "uuid": "REDACTED"
            }
        }
    },
    ...
}
```
`GET /rest/v1/studiemateriaal/algemeen/[id]` returns:

```json
{
  "items": [
    {
      "$type": "leermiddel.REduRoutePortalUserProduct",
      "links": [
        {
          "id": 123456789,
          "rel": "self",
          "type": "leermiddel.REduRoutePortalUserProduct",
          "href": "https://api.somtoday.nl/rest/v1/edurouteportaluserproduct/123456789"
        }
      ],
      "permissions": [
        {
          "full": "leermiddel.REduRoutePortalUserProduct:READ:INSTANCE(123456789)",
          "type": "leermiddel.REduRoutePortalUserProduct",
          "operations": ["READ"],
          "instances": ["INSTANCE(123456789)"]
        }
      ],
      "additionalObjects": {},
      "leerling": {
        "$type": "leerling.RLeerlingPrimer",
        "links": [
          {
            "id": 9496745174,
            "rel": "self",
            "type": "leerling.RLeerlingPrimer",
            "href": "https://api.somtoday.nl/rest/v1/leerlingen/9496745174"
          }
        ],
        "permissions": [
          {
            "full": "leerling.RLeerlingPrimer:READ:INSTANCE(9496745174)",
            "type": "leerling.RLeerlingPrimer",
            "operations": ["READ"],
            "instances": ["INSTANCE(9496745174)"]
          }
        ],
        "additionalObjects": {},
        "UUID": "f8cf6f6c-c213-4526-8ba1-6a306cf724a4",
        "leerlingnummer": 123456,
        "roepnaam": "{{first_name}}",
        "achternaam": "{{last_name}}"
      },
      "product": {
        "$type": "leermiddel.REduRoutePortalProduct",
        "links": [
          {
            "id": 1234567890123,
            "rel": "self",
            "type": "leermiddel.REduRoutePortalProduct",
            "href": "https://api.somtoday.nl/rest/v1/edurouteportalproduct/1234567890123"
          }
        ],
        "permissions": [
          {
            "full": "leermiddel.REduRoutePortalProduct:READ:INSTANCE(1234567890123)",
            "type": "leermiddel.REduRoutePortalProduct",
            "operations": ["READ"],
            "instances": ["INSTANCE(1234567890123)"]
          }
        ],
        "additionalObjects": {},
        "title": "Chemie Overal ed 5.0 vwo 5 FLEX  boek + online",
        "url": "https://toegang.noordhoff.nl/1234567890123",
        "UUID": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
        "methodeInformatie": {
          "$type": "leermiddel.RMethodeInformatie",
          "links": [
            {
              "id": 1234567890123,
              "rel": "self",
              "type": "leermiddel.RMethodeInformatie",
              "href": "https://api.somtoday.nl/rest/v1/methodeinformatie/1234567890123"
            }
          ],
          "permissions": [
            {
              "full": "leermiddel.RMethodeInformatie:READ:INSTANCE(1234567890123)",
              "type": "leermiddel.RMethodeInformatie",
              "operations": ["READ"],
              "instances": ["INSTANCE(1234567890123)"]
            }
          ],
          "additionalObjects": {},
          "UUID": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
          "dashboardMethodeNaam": "Chemie overal",
          "methode": "Chemie overal",
          "uitgever": "Noordhoff"
        }
      },
      "UUID": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
    },
    ...
  ]
}

```

</details>

### ICalendar: `GET /rest/v1/icalendar`
<details><summary>Click to open</summary>

Fetches the url to the icalendar stream.

#### Parameters

| Name          | Type      | Value                 |
|---------------|-----------|-----------------------|
| Authorization | Header    | Bearer [access_token] |

#### Returns

```json
{
    "links": [],
    "permissions": [],
    "additionalObjects": {},
    "leerlingICalendarLink": "https://api.somtoday.nl/rest/v1/icalendar/stream/REDACTED"
}
```

</details>

### ICalendar: `DELETE /rest/v1/icalendar`
<details><summary>Click to open</summary>

Deletes the currently active icalendar stream

#### Parameters

| Name          | Type      | Value                 |
|---------------|-----------|-----------------------|
| Authorization | Header    | Bearer [access_token] |

#### Returns

NONE

</details>

### Undocumented:

- `GET /rest/v1/maatregeltoekenningen`
- `GET /rest/v1/leerlingadresseringen`
- `GET /rest/v1/verzorgers/`
- `GET /rest/v1/onderwijsopafstandperiodes/`
- `GET /rest/v1/edurouteportaluserproduct/[id]`
- `GET /rest/v1/methodeinformatie/[id]`
