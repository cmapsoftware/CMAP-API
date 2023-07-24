# Budgets
Use budgets to return budget specific data for a client or project

## Tabs
* `GET v2/Budgets/123/Tabs` Returns the tabs for a given Non-AEC project.
```javascript
[{
    "Id" : 123456,
    "ProjectId": 123456,
    "Name" : "Additional Fees",
}]
```

## Stages
* `GET v2/Budgets/123/Stages` Returns the stages for a given project.
```javascript
[{
    "Id" : 123456,
	"TabId": 123546
    "ProjectId": "123", // AEC only
    "FeeType": "AEC", // AEC only
    "Name" : "Additional Fees",
    "StartDate": "2023-01-01T00:00:00",
    "EndDate": "2023-01-01T00:00:00",
}]
```

## Tasks
* `GET v2/Budgets/123/Tasks` Returns the tasks for a given project.
```javascript
[{
    "Id" : 123456,
    "StageId": 123456,
    "Name": "Additional Fees",
    "Notes": "",
    "StartDate": "2023-01-01T00:00:00",
    "EndDate": "2023-01-01T00:00:00",
    "Roles": [
        {
            "Name": "Test Role",
            "Hours": 7.5, // If BudgetInDays Feature is off
            "Days": 1, // If BudgetInDays Feature is on
            "Value": 100
        }
    ]
}]
```

## Externals
* `GET v2/Budgets/123/Externals` Returns the externals for a given AEC project.
```javascript
[{
    "StageId" : 123456,
    "CalculationType": "Fixed Fee",
    "BillingType": "Scheduled",
    "Name": "External 1",
    "CostPrice": 99.99,
    "SalePrice": 99.99,
    "ActualPrice": 99.99,
}]
```

## Additionals
* `GET v2/Budgets/123/Additionals` Returns the additionals for a given Non-AEC project.
```javascript
[{
    "Name": "External 1",
    "CostPrice": 99.99,
    "SalePrice": 99.99,
    "ActualPrice": 99.99,
}]
```

## Adjustments
* `GET v2/Budgets/123/Adjustments` Returns the adjustments for a given Non-AEC project.
```javascript
[{
    "Description" : "Test Adjustment",
    "Value": 99.99,
}]
```

## Get Externals
* `GET v1/budgets/1/externals` Returns the additionals/externals for a given project

```javascript
[{ 
	"id" : "16",
	"name" : "Additional Fees",
	"workstageId": 6522501,
	"isWorkstageClosed": false,
	"costPrice": "20000.00",
	"salePrice": "20000.00",
	"actualPrice": "25000.00",
	"projectId": 456784,
	"billingType": "Bill as Scheduled",
	"calculationType": "Fixed Fee"
},{ 
	"id" : "17",
	"name" : "Reimbursable Travel Expenses",
	"workstageId": 6522501,
	"isWorkstageClosed": false,
	"costPrice": "20000.00",
	"salePrice": "20000.00",
	"actualPrice": "25000.00",
	"projectId": 456784,
	"billingType": "Bill as Scheduled",
	"calculationType": "Fixed Fee"
}]
```

## Create External
* `POST v1/budgets/1/externals/` Create a new additional/external for the given project

```javascript
{
	"name": "Taxi Travel",
	"workstage": "Workstage Name",
	"calculationType": "FixedFee", // One of PercentageOfConstructionCost, FixedFee
	"billingType": "Scheduled", // One of Scheduled, Incurred, PassThrough
	"costPrice": 250,
	"salePrice": 150
}
```

## Update External
* `PUT v1/budgets/1/externals/1000` Update an additional/external for the given project

```javascript
{
	"name": "Taxi Travel to Airport",
	"workstage": "Workstage Name",
	"calculationType": "PercentageOfConstructionCost", // One of PercentageOfConstructionCost, FixedFee
	"billingType": "Incurred", // One of Scheduled, Incurred, PassThrough
	"costPrice": 300,
	"salePrice": 300
}
```

## Get Workstages
* `GET v1/budgets/1/workstages` Returns the workstages for a given project

```javascript
[
	{
		"name": "Planning",
		"startDate": "2019-02-14T00:00:00",
		"endDate": "2020-02-24T00:00:00",
		"probability": 100,
		"feeType": "Fixed Fee",
		"timeChargeCap": 15750,
		"costPlus": 15,
		"percentOfFee": 30.75,
		"fee": 20000,
		"retentionTarget": 31.50,
		"expensesAllowance": 350.00,
		"feePlanBudget": 6250,
		"resourceProfileBudget": 6500,
		"underOverBudget": 3200,
		"profitEstimate": 4000,
		"isClosed": false
	},
	{
		"name": "Design and Development",
		"startDate": "2019-02-14T00:00:00",
		"endDate": "2020-02-24T00:00:00",
		"probability": 100,
		"feeType": "Fixed Fee",
		"timeChargeCap": 15750,
		"costPlus": 15,
		"percentOfFee": 30.75,
		"fee": 20000,
		"retentionTarget": 31.50,
		"expensesAllowance": 350.00,
		"feePlanBudget": 6250,
		"resourceProfileBudget": 6500,
		"underOverBudget": 3200,
		"profitEstimate": 4000,
		"isClosed": false
	}
]
```
