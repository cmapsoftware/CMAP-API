# UserFigures
User the below UserFigures endpoints to query, add and update a users' User Figure records.

> ⚠️ WARNING: Using the below endpoints can overwrite your data, use with caution!

## Get User Figures
* **`GET v1/Users/{UserId}/UserFigures`** returns all User Figures for a specific User in date order. Note that `ContractType`, `ContractMonthlySalary` and `ContractMultiplier` are unavailable without the Dynamic Cost Rate feature being turned on. Data in these fields when this feature is not turned on will return `null`.

```javascript
[
    {
        "StartDate": "2021-01-01T00:00:00",
        "EndDate": "2021-05-06T23:59:59",
        "WorkingHours": 0.0,
        "ProductivityTarget": 0.0,
        "ActualCostRate": 0.0,
        "RoleName": "Managing Director"  | "Non-Chargeable Admin",
        "ContractType": null,
        "ContractMonthlySalary": null,
        "ContractMultiplier": null
    },
    {
        "StartDate": "2021-05-07T00:00:00",
        "EndDate": "2021-05-12T23:59:59",
        "WorkingHours": 37.5,
        "ProductivityTarget": 0.0,
        "ActualCostRate": 0.0,
        "RoleName": "Managing Director" | "Non-Chargeable Admin",
        "ContractType": null,
        "ContractMonthlySalary": null,
        "ContractMultiplier": null
    },
    ...
]
```

## Create a New User Figure
* **`POST v1/Users/{UserId}/UserFigures`** creates a new User Figure for a specific User with the information supplied. Note that `ContractType`, `ContractMonthlySalary` and `ContractMultiplier` are unavailable without the Dynamic Cost Rate feature being turned on. Submitting data to these fields without this feature turned on will not save the data.
``` javascript
{
    "StartDate": "2021-06-01T00:00:00",
    "EndDate": null,
    "WorkingHours": 40,
    "ProjectAvailability": 62.5,
    "ActualCost": 125,
    "Office": "Office Name",
    "Team": "Team Name",
    "Role": "Managing Director" | "Non-Chargeable Admin",
    "ContractType": "JobSalary" | "OvertimeSalary" | "Hourly",
    "ContractMonthlySalary": 2250,
    "ContractMultiplier": 1.41
}
```

## Update an existing User Figure
* **`PUT v1/Users/{UserId}/UserFigures`** updates and existing User Figure with the supplied UserFigureId for the user with the information supplied. Note that `ContractType`, `ContractMonthlySalary` and `ContractMultiplier` are unavailable without the Dynamic Cost Rate feature being turned on. Submitting data to these fields without this feature turned on will not save the data.
``` javascript
{
    "UserFigureId": 1234567,
    "StartDate": "2021-06-01T00:00:00",
    "EndDate": null,
    "WorkingHours": 40,
    "ProjectAvailability": 62.5,
    "ActualCost": 125,
    "Office": "Office Name",
    "Team": "Team Name",
    "Role": "Managing Director" | "Non-Chargeable Admin",
    "ContractType": "JobSalary" | "OvertimeSalary" | "Hourly",
    "ContractMonthlySalary": 2250,
    "ContractMultiplier": 1.41
}
```