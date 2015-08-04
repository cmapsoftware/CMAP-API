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


* `POST v1/expenses` Create a new expense claim, returns the id of the new claim

```json
{
	"name" : "July Expenses"
}
```

* `PUT v1/expenses5` Updates the name of an expense claim

```json
{
	"name" : "July Expense Claim"
}
```

* `POST v1/expenses/5/submit` Submits an expense claim for either line manager or financial approval depnding upon the client's CMAP configuration
 


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

* `GET v1/expenses/5/items/1` Returns the expense claim item


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

* `POST v1/expenses/5/items` Create a new expense claim item, returns the newly created epxense claim item id

```json
{
	"ExpenseClaimID" : "5",
	"ExpenseCategoryID" : "45", /* 0 for mileage claim items */
	"ContractID" : "5", /* only used when the expense claim is for a contract */
	"ProjectID" : "6", /* only used when the expense claim is for a project */
	"ClaimDate" : "2015-06-01",
	"Mileage" : "100", /* used when a mileage claim item, nullable */
	"MileageRateID" : "78", /* used when a mileage claim item, nullable */
	"Value" : "99.89", /* this value is auto calculated for mileage claims */
	"CurrencyID" : "1",
	"Description" : "Description of the expense claim item",
	"ExchangeRate" : "1",
	"Reimburse" : "true",
	"Receipt" : "true",
	"VATRateID" : "1",
	"AccountID" : "34", /* supplier id */
	"ReceiptImage" : "" /* a base64 string representation of a jpg image */
}
```

* `PUT v1/expenses/5/items/1` Updates an expense claim item

```json
{
	"ExpenseClaimItemID" : "1",
	"ExpenseClaimID" : "5",
	"ExpenseCategoryID" : "45", /* 0 for mileage claim items */
	"ContractID" : "5", /* only used when the expense claim is for a contract */
	"ProjectID" : "6", /* only used when the expense claim is for a project */
	"ClaimDate" : "2015-06-01",
	"Mileage" : "100", /* used when a mileage claim item, nullable */
	"MileageRateID" : "78", /* used when a mileage claim item, nullable */
	"Value" : "99.89", /* this value is auto calculated for mileage claims */
	"CurrencyID" : "1",
	"Description" : "Description of the expense claim item",
	"ExchangeRate" : "1",
	"Reimburse" : "true",
	"Receipt" : "true",
	"VATRateID" : "1",
	"AccountID" : "34", /* supplier id */
	"ReceiptImage" : "" /* a base64 string representation of a jpg image */
}
```

* `DELETE v1/expenses/5/items/1` Deletes an expense claim item