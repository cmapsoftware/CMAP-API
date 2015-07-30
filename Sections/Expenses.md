# Expenses
Use expenses to record your personal and project expenses in CMAP

## Get Expense Claims
`GET v1/expenses` Returns all the expense claims for the logged in user

```json
	{
		"expenseClaimID" : "5", 
		"name" : "July 2015", 
		"dateSubmitted" : "01/07/2015", 
		"status" : "Open | FIN Rejected | MAN Rejected | Awaiting FIN Approval | Awaiting MAN Approval | Awaiting Payment | Paid"
	}
```

`GET v1/expenses/open` Returns all the expenses for the user with the matching status. The options for status are `Open | FIN Rejected | MAN Rejected | Awaiting FIN Approval | Awaiting MAN Approval | Awaiting Payment | Paid`

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