# Budgets
Use budgets to return budget specific data for a client or project

## Get Externals
* `GET v1/budgets/1/externals` Returns the additionals/externals for a given project

```javascript
[{ 
	"id" : "16",
	"name" : "Additional Fees"	
},{ 
	"id" : "17",
	"name" : "Reimbursable Travel Expenses"	
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