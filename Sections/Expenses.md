# Expenses
Use expenses to record your personal and project expenses in CMAP

## Get Expense Claims
* `GET v1/expenses` Returns all the expense claims for the logged in user

```json
[{
	"expenseClaimID" : "5", 
	"name" : "June 2015", 
	"dateSubmitted" : "01/06/2015", 
	"status" : "Open | FIN Rejected | MAN Rejected | Awaiting FIN Approval | Awaiting MAN Approval | Awaiting Payment | Paid"
},
{
	"expenseClaimID" : "6", 
	"name" : "July 2015", 
	"dateSubmitted" : "01/07/2015", 
	"status" : "Open | FIN Rejected | MAN Rejected | Awaiting FIN Approval | Awaiting MAN Approval | Awaiting Payment | Paid"
}]
```

* `GET v1/expenses/open` Returns all the expenses for the user with the matching status. The options for status are `Open | FIN Rejected | MAN Rejected | Awaiting FIN Approval | Awaiting MAN Approval | Awaiting Payment | Paid`

```json
[{
	"expenseClaimID" : "5", 
	"name" : "June 2015", 
	"dateSubmitted" : "01/06/2015", 
	"status" : "Open"
},
{
	"expenseClaimID" : "6", 
	"name" : "July 2015", 
	"dateSubmitted" : "01/07/2015", 
	"status" : "Open"
}]
```

* `GET v1/expenses/5` Returns the expense claim for the user with the matching id

```json
{
	"expenseClaimID" : "5", 
	"name" : "June 2015", 
	"dateSubmitted" : "01/06/2015", 
	"status" : "Open"
}
```

## Get Expense Claim Items
* `GET v1/expenses/5/items` Returns all the expense claim items for a single expense claim

```json
[{ 
	"amount" : "180.00",
	"billable" : i.BillingTypeID,
	"categoryId" : i.ExpenseCategoryID,
	"claimId" : "5",
	"currencyId" : "1",
	"date" : "2015-06-01",
	"description" : "Meal for the client",
	"exchangeRate" : "",
	"id" : "7658",
	"mileage" : "null",
	"mileageRateId" : "null",
	"projectId" : "8767",
	"projectName" : "8978 - New Website Project",
	"reimburse" : "true",
	"vatRateId" : "1" 
}]
```