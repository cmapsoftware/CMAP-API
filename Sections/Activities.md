# Activities
Use activities to manage activities in CMAP

* `GET v1/Activities?due=-1|0|n`

Returns all the activities for the logged on users that are due in the number of days passed in. For **all** overdue activities pass in -1, for activities due today pass in 0, for activities due in the future number of days pass in the number of days - for example passing in 5 will return all activities due in the next 5 days.

If an Activity is marked as Private, or is related to the HR module, it will not show.

```javascript
[{ 
  "id": 123, 
  "companyId": "434532", 
  "company": "ABC Pharma", 
  "contactId": 3456, 
  "contactName": "Matt Smith", 
  "details": "The information about the activity", 
  "documentId": "0000-0000-0000-0000", 
  "documentName": "Activity.xlsx", 
  "dueDate": "2017-01-01", 
  "isCompleted": false,
  "leadId": 12345,
  "projectId": 7987, 
  "projectTitle": "10001 - Website Design",
  "type": "Meeting", 
  "typeId": "3",
  "ownerId": 2468,
  "notes": "Activity notes",
  "startDate": "2017-01-01",
  "isPrivate": false
  }
]
```

* `GET v1/Activities/5`

Returns the activity for the supplied id if it exists

```javascript
{ 
  "id": 123, 
  "companyId": "434532", 
  "company": "ABC Pharma", 
  "contactId": 3456, 
  "contactName": "Matt Smith", 
  "details": "The information about the activity", 
  "documentId": "0000-0000-0000-0000", 
  "documentName": "Activity.xlsx", 
  "dueDate": "2017-01-01", 
  "isCompleted": false,
  "leadId": 12345,
  "projectId": 7987, 
  "projectTitle": "10001 - Website Design",
  "type": "Meeting", 
  "typeId": "3",
  "ownerId": 2468,
  "notes": "Activity notes",
  "startDate": "2017-01-01",
  "isPrivate": false
}
```

* `GET - v1/Activities/?contactId=123456&open=true`

Returns all the activities logged for the specified contact, that are either Open or Completed

```javascript
[{ 
    "id": 123, 
    "companyId": "434532", 
    "company": "ABC Pharma", 
    "contactId": 3456, 
    "contactName": "Matt Smith", 
    "details": "The information about the activity", 
    "documentId": "0000-0000-0000-0000", 
    "documentName": "Activity.xlsx", 
    "dueDate": "2017-01-01", 
    "isCompleted": false,
    "leadId": 12345,
    "projectId": 7987, 
    "projectTitle": "10001 - Website Design",
    "type": "Meeting", 
    "typeId": "3",
    "ownerId": 2468,
    "notes": "Activity notes",
    "startDate": "2017-01-01",
    "isPrivate": false
  }
]
```

* `DELETE v1/Activities/5`

Deletes the specified Activity
``` javascript 
{ 
	"result": true
}
```

* `* POST v1/Activities` Creates a new Activity. The AccountID is required for any activity record regardless of what type of entity the activity is associated to. `EntityType` must be one of the following options: `Account`, `Contact`, `Project`, `Lead`, or `RFP`. `ActivityCategoryID` can be obtained by sending a GET request to `/v1/Resources/ActivityCategories`.
``` javascript
{
   "AccountID": 123456,
   "ContactID": 123456,
   "StartDate": "2022-11-01",
   "DueDate": "2022-11-01",
   "UserID": 123456,
   "EntityType": "Contact",
   "EntityID": 123456,
   "ActivityCategoryID": 123456,
   "IsCompleted": false,
   "Details": "The details of the activity",
   "Notes": "Some notes for the activity",
   "IsPrivate": false
}
```

* `* PUT v1/Activities` Updates an existing Activity. The ActivityID must be supplied. The AccountID is required for any activity record regardless of what type of entity the Activity is associated to. `EntityType` must be one of the following options: `Account`, `Contact`, `Project`, `Lead`, or `RFP`. `ActivityCategoryID` can be obtained by sending a GET request to `/v1/Resources/ActivityCategories`.
``` javascript
{
   "ActivityID": 123456,
   "AccountID": 123456,
   "ContactID": 123456,
   "StartDate": "2022-11-01",
   "DueDate": "2022-11-01",
   "UserID": 123456,
   "EntityType": "Contact",
   "EntityID": 123456,
   "ActivityCategoryID": 123456,
   "IsCompleted": false,
   "Details": "The details of the activity",
   "Notes": "Some notes for the activity",
   "IsPrivate": false
}
```

* `* PUT v1/Activities/2134/status?completed=true|false` Updates the status of an Activity. Pass either true or false for the completed flag, true to complete the task, else false
