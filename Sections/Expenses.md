# Expenses
Use expenses to record your personal and project expenses in CMAP

## Get Expense Claims
`GET v1/expenses` Returns all the expense claims for the logged in user

```javascript
{
	expenseClaimID = 5, 
	name = "July 2015", 
	dateSubmitted = "01/07/2015", 
	status = "Open | FIN Rejected | MAN Rejected | Awaiting FIN Approval | Awaiting MAN Approval | Awaiting Payment | Paid"
}
```
