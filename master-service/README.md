# Master Service

## Usage
Service can interact with a certain table that is defined as master data

All responses will have the form similary to
```json
{
    "data": "Mixed type holding the content of the response",
    "message": "Description of what happened"
}
```

### List of master resources
- Employee
- Holiday
- Leave Type
- Leave Quota
- Position
- Department
- Division
- Approver
- Available Leave
- Bank

the endpoint services will prefix with Master resources name
such as, `GET /employees`, `GET /holidays`, `GET /leavetypes` and so forth

## Example of employee resource

### List all Employee

**Definition**

`GET /employees`

**Response**

- `200 OK` on success

```json
[
    {
        "id": "OTR0001",
        "employee_no": "001",
        "fingerprint_id": "202001",
        "provident_fund_no": "",
        "titileth": "นาย",
        "firstnameth": "บ๊อบ",
        "lastnameth": "โนมอนิเตอร์",
        "titileen": "Mr.",
        "firstnameen": "bob",
        "lastnameen": "nomornitor"
    },
    {
        "id": "OTR0002",
        "employee_no": "002",
        "fingerprint_id": "202002",
        "provident_fund_no": "",
        "titileth": "นาย",
        "firstnameth": "บ๊อบ2",
        "lastnameth": "โนมอนิเตอร์",
        "titileen": "Mr.",
        "firstnameen": "bob2",
        "lastnameen": "nomornitor"
    }
]
```

### Registering a new employee

**Definition**

`POST /employees`

**Arguments**

- `"id":string` a unique identifier for employee
- `"employee_no":string` a unique number to specify for employee
- `"fingerprint_id":string` a unique identifier for employee's finger print
- `"provident_fund_no":string` the number of individual employee's provident fund
- `"titileth":string` title in TH
- `"firstnameth":string` first name in TH
- `"lastnameth":string` last name in TH
- `"titileen":string` title in EN
- `"firstnameen":string` first name in EN
- `"lastnameen":string` last name in EN

If an employee with the given identifier already exists, the existing employee will be overwritten.

**Response**

- `201 Created` on success

```json
{
    "id": "OTR0001",
    "employee_no": "001",
    "fingerprint_id": "202001",
    "provident_fund_no": "",
    "titileth": "นาย",
    "firstnameth": "บ๊อบ",
    "lastnameth": "โนมอนิเตอร์",
    "titileen": "Mr.",
    "firstnameen": "bob",
    "lastnameen": "nomornitor"
}
```
## Lookup employee details

`GET /employees/<identifier>`

**Response**

- `404 Not Found` if the employee does not exist
- `200 OK` on success

```json
{
    "id": "OTR0001",
    "employee_no": "001",
    "fingerprint_id": "202001",
    "provident_fund_no": "",
    "titileth": "นาย",
    "firstnameth": "บ๊อบ",
    "lastnameth": "โนมอนิเตอร์",
    "titileen": "Mr.",
    "firstnameen": "bob",
    "lastnameen": "nomornitor"
}
```

## Delete an employee

**Definition**

`DELETE /employees/<identifier>`

**Response**

- `404 Not Found` if the device does not exist
- `204 No Content` on success