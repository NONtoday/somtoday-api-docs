## Self-planning

### Make appointment `POST /rest/v1/zelfplannen/afspraken`
<details><summary>Click to open</summary>
Makes an appointment at specified date/time.

#### Parameters

| Name          | Type      | Value                               |
|---------------|-----------|-------------------------------------|
| Authorization | Header    | Bearer [access_token]               |

### Example POST data
```json
{
  "titel": "Go biking",
  "begindatumtijd": "2026-10-28T08:00:00.000Z",
  "einddatumtijd": "2026-10-28T09:00:00.000Z",
  "locatie": "All around the city",
  "omschrijving": "Gotta bike to school"
}
```

#### Returns
```json
[
  {
    "uuid": "00000000-0000-0000-0000-000000000000",
    "titel": "Go biking",
    "begindatumtijd": "2026-10-29T08:10:00.000Z",
    "einddatumtijd": "2026-10-29T09:00:00.000Z",
    "locatie": "All around the city",
    "omschrijving": "Gotta bike to school"
  }
]
```
</details>

### Get appointments `GET /rest/v1/zelfplannen/afspraken?vanafDatumtijd=[ISO-8601-time]&totEnMetDatumtijd=[ISO-8601-time2]`
<details><summary>Click to open</summary>
Request appointments. Replace time/date with preferred time/date.

#### Parameters

| Name          | Type      | Value                               |
|---------------|-----------|-------------------------------------|
| Authorization | Header    | Bearer [access_token]               |
| ISO-8601-time | Parameter | 2026-11-01T23:00:00.000Z            |
| ISO-8601-time | Parameter | 2026-11-08T22:59:59.999Z            |

#### Returns

```json
[
  {
    "uuid": "00000000-0000-0000-0000-000000000000",
    "titel": "Go biking",
    "begindatumtijd": "2026-10-29T08:10:00.000Z",
    "einddatumtijd": "2026-10-29T09:00:00.000Z",
    "locatie": "All around the city",
    "omschrijving": "Gotta bike to school"
  }
]
```
</details>

### Make task `POST /rest/v1/zelfplannen/taken`

<details><summary>Click to open</summary>
Makes a task.

#### Parameters

| Name          | Type      | Value                               |
|---------------|-----------|-------------------------------------|
| Authorization | Header    | Bearer [access_token]               |

### Example POST data

```json
{
  "titel": "Learn french",
  "inplannenOp": "2026-10-26",
  "omschrijving": "Apprendre 1-4"
}
```

#### Returns

```json
[
  {
    "uuid": "00000000-0000-0000-0000-000000000000",
    "titel": "Learn french",
    "inplannenOp": "2026-10-26",
    "omschrijving": "Apprendre 1-4"
  }
]
```
</details>

### Get tasks `GET /rest/v1/zelfplannen/taken?vanafDatum=[startdate]&totEnMetDatum=[enddate]`

<details><summary>Click to open</summary>
Request tasks. Replace date with preferred date.

#### Parameters

| Name          | Type      | Value                               |
|---------------|-----------|-------------------------------------|
| Authorization | Header    | Bearer [access_token]               |
| ISO-8601-time | Parameter | 2026-11-09                          |
| ISO-8601-time | Parameter | 2026-11-15                          |

#### Returns

```json
[
  {
    "uuid": "00000000-0000-0000-0000-000000000000",
    "titel": "Learn french",
    "inplannenOp": "2026-10-26",
    "omschrijving": "Apprendre 1-4"
  }
  ...
]
```
</details>
