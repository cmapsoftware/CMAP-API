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
	"internalCode" : "",
	"taskId" : 34534,
	"roleId" : 4234
}]
```


* `* GET v1/timesheets?week=2015-09-21&projectId=[id]` Returns all the timesheet entries for the specified week and specified projectId

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
	"internalCode" : "",
	"taskId" : 34534,
	"roleId" : 4234
}]
```

* `* GET v1/timesheets?week=2015-09-21&internalCodeId=[id]` Returns all the timesheet entries for the specified week and specified internalcodeId

```javascript
[{ 
	"id" : 2423,
	"hours" : 7.5,
	"date" : "2015-07-01",
	"notes" : "Lots of coding",
	"projectId" : null,
	"contractId" : null,
	"internalCodeId" : 456456,
	"project" : "",
	"internalCode" : "Internal Meeting",
	"taskId" : 34534,
	"roleId" : 4234 
}]
```


* `* GET v1/timesheets?date=2015-09-21` Returns all the timesheet entries for the specified date

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
	"internalCode" : "",
	"taskId" : 34534,
	"roleId" : 4234
}]
```

* `* GET v1/timesheets/projectactivities` Returns all the project activity codes for the client

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
	"tasks":[{
	"BudgetSectionID" : 34534,
	"BudgetTaskID" : 243,
	"Name" : "Task One",
	"OrderNo" : 1,
	"PercentageComplete" : 50,
	"Section" : "Section One",
	"Tab" : "Development"
	},{
	"BudgetSectionID" : 34534,
	"BudgetTaskID" : 345,
	"Name" : "Task Two",
	"OrderNo" : 2,
	"PercentageComplete" : 25,
	"Section" : "Section One",
	"Tab" : "Development"
	}]
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

* `* POST v1/timesheets/` Creates a timesheet entry and returns the id of the new entry

```javascript
{ 
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
* `* PUT v1/timesheets/5` Updates a timesheet entry

```javascript
{ 
	"id" : 34543, 
	"date" : "2015-09-21",
	"taskId" : 2343,
	"projectId" : 5413,
	"internalCodeId" : null,
	"contractId" : null,
	"hours" : 7,
	"notes" : "Working hard in this project, now with extra notes",
	"roleId" : 345,
	"workTypeId" : null,
	"contractWorkTypeId" : null,
	"additionalTime" : false
}
```

* `* DELETE v1/timesheets/65` Deletes the timesheet entry
```javascript
{ 
	"result" : true
}
```

* `* POST - v1/timesheets/AddRow?week&projectId&internalCodeId` Adds a project or internal code to the users timesheet week. Supply either the projectId or internalCodeId but not both

* `* DELETE - v1/timesheets/RemoveRow?week&projectId&internalCodeId` Removes a project or internal code from the users timesheet week. Supply either the projectId or internalCodeId but not both

* `* POST v1/timesheets/submit` Submits the current users timesheet week
