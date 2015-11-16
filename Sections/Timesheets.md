# Timesheets
Use Timesheets to manage timesheet entries for the logged in user

* `* GET v1/timesheets?week=2015-09-21` Returns all the timesheet entries for the timesheet week, if the timesheet week is omitted then the user's current timesheet week data is returned

```javascript
[{ 
	"id" : 2423,
	"hours" : 7.5,
	"date" : "2015-07-01",
	"notes" : "Lots of coding",
	"projectId" : 3424,
	"contractId" : null,
	"internalCodeId" : null,
	"project" : "1003 - The Coding Project",
	"contract" : "",
	"internalCode" : "" 
}]
```

* `* GET v1/timesheets/projectactivites` Returns all the project activity codes for the client

```javascript
[
	{
		"projectId" : 123,
		"workActivityId" : 1
	},
	{
		"projectId" : 123,
		"workActivityId" : 3
	}
]
```

* `* GET v1/timesheets/roles` Returns the roles available for each task for projects that are listed on the users' current timesheet week

```javascript
[
	{
		"taskId" : 345,
		"budgetRoles" : [{"budgetRoleID":1, "Designer"},{"budgetRoleID":2, "Developer"}]
	},
	{
		"taskId" : 654,
		"budgetRoles" : [{"budgetRoleID":1, "Designer"},{"budgetRoleID":2, "Developer"}]
	}
]
```

* `* GET v1/timesheets/tasks?projectId=23423` Returns all the tasks associated to the project

```javascript
{
	"tasks":{
		"228510":[{
			"BudgetId":228585,
			"BudgetTabId":344234,
			"Name":"CMAP Customisations",
			"OrderNo":0,
			"ReadOnly":false,
			"FeeValue":0.0,
			"ActualCostValue":0.0,
			"Margin":0.0,
			"BudgetSections":[{
				"BudgetTabId":344234,
				"BudgetSectionId":595309,
				"Name":"CMAP Configuration",
				"OrderNo":0,
				"Locked":false,
				"BudgetTasks":[{
					"BudgetSectionId":595309,
					"BudgetTaskId":947606,
					"Name":"Configuration Tasks",
					"Duration":2.0,
					"MonthlyDuration":null,
					"FeePercentage":null,
					"OurFee":null,
					"BudgetUnits":null,
					"PercentComplete":0.0,
					"Start":"2015-02-16T00:00:00",
					"End":null,
					"DailyValue":null,
					"projectId":null,
					"Project":null,
					"IgnoreWeekends":null,
					"Notes":null,
					"OrderNo":null,
					"Probability":null,
					"CurrencyId":null,
					"RoleId":null,
					"BusinessUnitId":null
					}]
				}]
			}]
		}
}
```
* `* GET v1/timesheets/5` Returns an individual timesheet entry

```javascript
{ 
	"id" : 34543, 
	"date" : "2015-09-21",
	"taskId" : 2343,
	"projectId" : 5413,
	"internalCodeId" : null,
	"contractId" : null,
	"hours" : 7.5,
	"notes" : "Working hard in this project",
	"roleId" : 345,
	"workTypeId" : null,
	"contractWorkTypeId" : null,
	"additionalTime" : false
}
```

* `* POST v1/timesheets/submit` Submits the current users timesheet week
