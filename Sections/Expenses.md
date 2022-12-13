# Expenses
Use expenses to record your personal and project expenses in CMAP

## Get Expense Claims

* **`GET v1/expenses`**
Returns the 5 most recent expense claims for the logged in User
* **`GET v1/expenses?page={PAGE}&claimsPerPage={CLAIMS_PER_PAGE}`**
Returns the specific page of Expense Claims specified in `PAGE`, ordered by most recent and showing the number of items per page specified in `CLAIMS_PER_PAGE`, for the logged in User

```json
[{
	"expenseClaimID" : "5", 
	"name" : "June 2015", 
	"dateSubmitted" : "01/06/2015",
	"currencyID": 1,
	"status" : "Open | FIN Rejected | MAN Rejected | Awaiting FIN Approval | Awaiting MAN Approval | Awaiting Payment | Paid"
},
{
	"expenseClaimID" : "6", 
	"name" : "July 2015", 
	"dateSubmitted" : "01/07/2015",
	"currencyID": 1,
	"status" : "Open | FIN Rejected | MAN Rejected | Awaiting FIN Approval | Awaiting MAN Approval | Awaiting Payment | Paid"
}]
```

* **`GET v1/expenses/?status={STATUS}`**
Returns all the expenses for the user with the matching Expense Claim Status specified by `{STATUS}`. The options for status are `Open | FINRejected | MANRejected | AwaitingFINApproval | AwaitingMANApproval | AwaitingPayment | Paid`

```json
[{
	"expenseClaimID" : "5", 
	"name" : "June 2015", 
	"dateSubmitted" : "01/06/2015", 
	"currencyID": 1,
	"status" : "Open"
},
{
	"expenseClaimID" : "6", 
	"name" : "July 2015", 
	"dateSubmitted" : "01/07/2015", 
	"status" : "Open"
}]
```

* **`GET v1/expenses/{EXPENSE_CLAIM_ID}`**
Returns the Expense Claim for the User with the matching Expense Claim ID

```json
{
	"expenseClaimID" : "5", 
	"name" : "June 2015", 
	"dateSubmitted" : "01/06/2015",
	"currencyID": 1,
	"status" : "Open",
	"userId": 123456
}
```

* **`POST v1/expenses`**
Create a new Expense Claim. This returns the ID of the new Expense Claim. To default to using Expense Claim names of the month and year in the format "Dec 2022", supply a JSON body with no name property

```json
{
	"name" : "July Expenses"
}
```

```json
{} // will default to the current month and year in the format "Dec 2022"
```


```json
// Return Response
{
	"id": 123456
}
```

* **`PUT v1/expenses/{EXPENSE_CLAIM_ID}`**
Update the name of an Expense Claim for the relevant Expense Claim ID. Returns a `200 OK` response if the name was successfully updated

```json
{
	"name" : "July Expense Claim"
}
```

* **`POST v1/expenses/{EXPENSE_CLAIM_ID}/submit`**
Submit an Expense Claim for either Line Manager or Financial Manager approval depending upon the client's CMAP configuration. Returns a `true` or `false` success status and notification message

```json
// Return result
{
	"result": "{success: true, notification: '' | success: false, notification: ''}"
}
```

## Get Expense Claim Items
* **`GET v1/expenses/{EXPENSE_CLAIM_ID}/items`**
Returns all the Expense Claim Items for a single Expense Claim. To retrieve the list of `BillingTypeID` values, make a `GET` request to `v1/resources/expensebillingtypes`. In the event that an Expense Claim Item is a mileage item, then `categoryId` will be `0`, `currencyId` will be `0` and `mileage` and `mileageRateId` will have values. For all other Expense Claim Item types, the `mileage` and `mileageRateId` fields will be `null` and `categoryId` and `currencyId` will be non-zero. To retrieve the `BudgetExternalID` make a `GET` request to `v1/budgets/{PROJECT_ID}/externals`.

```json
[{ 
	"amount" : 123.45,
	"billable" : 1, /* nullable */
	"categoryId" : 12345,
	"categoryName": "Transport",
	"claimId" : 123456,
	"currencyId" : 1,
	"currencyName": "GBP",
	"date" : "2015-06-01T00:00:00",
	"description" : "Meal for the client",
	"exchangeRate" : 0.0, /* nullable */
	"id" : "7658",
	"mileage" : 123.45, /* nullable */
	"mileageRateId" : 123, /* nullable */
	"projectId" : "8767", /* nullable */
	"projectName" : "Sample Account, 8978 - New Website Project",
	"reimburse" : true,
	"vatRateId" : 1,
	"budgetExternalID": 1234567,
	"chargeable": false,
	"sageAccountCode": "SAGE1234"
}]
```

* **`GET v1/expenses/{EXPENSE_CLAIM_ID}/items/{EXPENSE_CLAIM_ITEM_ID}`**
Returns the Expense Claim Item for the Expense Claim ID specified by `EXPENSE_CLAIM_ID` and the Expense Claim Item ID specified by `EXPENSE_CLAIM_ITEM_ID`.  To retrieve the list of `BillingTypeID` values for the `billable` field, make a `GET` request to `v1/resources/expensebillingtypes` Only one pair of `projectId` and `projectName` or `internalCodeId` and `internalCodeName` will be populated in the response. `receiptImage` is a `base64` encoded string representing an encoded `JPG` image.  To retrieve the `BudgetExternalID` make a `GET` request to `v1/budgets/{PROJECT_ID}/externals`.

```json
[{ 
	"amount" : 123.45,
	"billable" : 1, /* nullable */
	"categoryId" : 12345,
	"categoryName": "Transport",
	"claimId" : 123456,
	"claimName": "Expense Claim - Dec 2022",
	"currencyId" : 1,
	"currency": "GBP",
	"currencyName": "Great British Pounds",
	"date" : "2015-06-01T00:00:00",
	"description" : "Meal for the client",
	"exchangeRate" : 0.0, /* nullable */
	"id" : "7658",
	"mileage" : 123.45, /* nullable */
	"mileageRateId" : 123, /* nullable */
	"internalCodeId": 12345,
	"internalCodeName": "Training & Development",
	"projectId" : "8767", /* nullable */
	"projectName" : "Sample Account, 8978 - New Website Project",
	"reimburse" : true,
	"receiptImage": "ABCDEF1234560...",
	"vatRateId" : 1,
	"vatrate": 20.0,
	"budgetExternalID": 1234567,
	"chargeable": false,
	"sageAccountCode": "SAGE1234"
}]
```

* **`POST v1/expenses/{EXPENSE_CLAIM_ID}/items`**
Create a new Expense Claim Item, returning the newly created Expense Claim Item ID. To retrieve the list of `BillingTypeID` values, make a `GET` request to `v1/resources/expensebillingtypes`. To retrieve the `BudgetExternalID` make a `GET` request to `v1/budgets/{PROJECT_ID}/externals`. `receiptImage` is a `base64` encoded string representing an encoded `JPG` image.

```json
// Mileage Expense Claim Item
{
	"ExpenseClaimID": 123456,
	"ExpenseCategoryID": 0,
	"ContractID": 12345, /* only used when the Expense Claim is for a Contract */
	"ProjectID": 12345, /* only used when the Expense Claim is for a Project */
	"InternalCodeID": 12345, /* only used when the Expense Claim is for an Internal Code */
	"ClaimDate": "2015-06-01",
	"Mileage": 123.45,
	"MileageRateID": 12345,
	"CurrencyID": 1,
	"Description": "Description of the Expense Claim Item",
	"ExchangeRate": 1,
	"Reimburse": true,
	"Receipt": true,
	"VATRateID": 1,
	"AccountID": 12345,
	"BillingTypeID": 1,
	"BudgetExternalID": 1234567,
	"ReceiptImage": "ABCDEF1234560...",
	"InvoiceID": 123456,
	"VatAmount": 20.0,
	"ExpenseClaimStatusID": 1
}
```
```json
// Non-Mileage Expense Claim Item
{
	"ExpenseClaimID": 123456,
	"ExpenseCategoryID": 12345,
	"ContractID": 12345, /* only used when the Expense Claim is for a Contract */
	"ProjectID": 12345, /* only used when the Expense Claim is for a Project */
	"InternalCodeID": 12345, /* only used when the Expense Claim is for an Internal Code */
	"ClaimDate": "2015-06-01",
	"Value": 123.45,
	"CurrencyID": 1,
	"Description": "Description of the Expense Claim Item",
	"ExchangeRate": 1,
	"Reimburse": true,
	"Receipt": true,
	"VATRateID": 1,
	"AccountID": 12345,
	"BillingTypeID": 1,
	"BudgetExternalID": 1234567,
	"ReceiptImage": "ABCDEF1234560...",
	"InvoiceID": 123456,
	"VatAmount": 20.0,
	"ExpenseClaimStatusID": 1
}
```

* **`PUT v1/expenses/5/items/1`**
Updates an Expense Claim Item. To retrieve the list of `BillingTypeID` values, make a `GET` request to `v1/resources/expensebillingtypes`. To retrieve the `BudgetExternalID` make a `GET` request to `v1/budgets/{PROJECT_ID}/externals`. `receiptImage` is a `base64` encoded string representing an encoded `JPG` image.

```json
// Mileage Expense Claim Item
{
	"ExpenseClaimItemID": 1234567,
	"ExpenseClaimID": 123456,
	"ExpenseCategoryID": 0,
	"ContractID": 123456, /* only used when the expense claim is for a contract */
	"ProjectID": 123456, /* only used when the expense claim is for a project */
	"InternalCodeID": 123456, /* only used when the expense claim is for an internal code */
	"ClaimDate": "2015-06-01",
	"Mileage": 123.45,
	"MileageRateID": 12345,
	"CurrencyID": 1,
	"Description": "Description of the expense claim item",
	"ExchangeRate": 1,
	"Reimburse": true,
	"Receipt": true,
	"VATRateID": 1,
	"AccountID": 123456,
	"BillingTypeID": 1,
	"BudgetExternalID": 1234567,
	"ReceiptImage": "ABCDEF1234560...",
	"InvoiceID": 123456,
	"VatAmount": 20.0,
	"ExpenseClaimStatusID": 1
}
```

```json
// Non-Mileage Expense Claim Item
{
	"ExpenseClaimItemID": 1234567,
	"ExpenseClaimID": 123456,
	"ExpenseCategoryID": 123456,
	"ContractID": 123456, /* only used when the expense claim is for a contract */
	"ProjectID": 123456, /* only used when the expense claim is for a project */
	"InternalCodeID": 123456, /* only used when the expense claim is for an internal code */
	"ClaimDate": "2015-06-01",
	"Value": 123.45,
	"CurrencyID": 1,
	"Description": "Description of the expense claim item",
	"ExchangeRate": 1,
	"Reimburse": true,
	"Receipt": true,
	"VATRateID": 1,
	"AccountID": 123456,
	"BillingTypeID": 1,
	"BudgetExternalID": 1234567,
	"ReceiptImage": "ABCDEF1234560...",
	"InvoiceID": 123456,
	"VatAmount": 20.0,
	"ExpenseClaimStatusID": 1
}
```

* **`DELETE v1/expenses/5/items/1`**
Deletes an expense claim item. Returns a `true` or `false` indicating a successful deletion and a notification message.
```json
{
    "result": {
        "success": true,
        "notification": "Item Deleted"
    }
}
```

