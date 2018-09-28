# Activities
Use activities to manage activities in CMAP

* `* GET v1/Activities?due=-1|0|n` Returns all the activies for the logged on users that are due in the number of days passed in. For overdue activities pass in a negative number.

```javascript
[{ "id" = "123", 
  "companyId" = "434532", 
  "company" = "ABC Pharma", 
  "contactId" = "3456", 
  "contactName" = "Matt Smith", 
  "details" = "The information about the activity", 
  "documentId" = "0000-0000-00000-0000", 
  "documentName" = "Activity.xlsx", 
  "dueDate" = "2017-01-01", 
  "isCompleted" = false
  "projectId" = "7987", 
  "projectTitle" = "10001 - Website Design", 
  "type" = "Meeting", 
  "typeId" = "3",
  "ownerId" = 2468
  }]
```

* `* GET v1/Activities/5` Returns the activity for the supplied id, if it exists

```javascript
{ "id" = "5", 
  "companyId" = "434532", 
  "company" = "ABC Pharma", 
  "contactId" = "3456", 
  "contactName" = "Matt Smith", 
  "details" = "The information about the activity", 
  "documentId" = "0000-0000-00000-0000", 
  "documentName" = "Activity.xlsx", 
  "dueDate" = "2017-01-01", 
  "isCompleted" = false
  "projectId" = "7987", 
  "projectTitle" = "10001 - Website Design", 
  "type" = "Meeting", 
  "typeId" = "3",
  "ownerId" = 2468
  }
```

* `* GET - v1/Activities/?contactId=34534&open=true` Returns all the activities logged for the specified contact and whether you want open or completed activities

```javascript
[{ "id" = "123", 
  "companyId" = "434532", 
  "company" = "ABC Pharma", 
  "contactId" = "34534", 
  "contactName" = "Matt Smith", 
  "details" = "The information about the activity", 
  "documentId" = "0000-0000-00000-0000", 
  "documentName" = "Activity.xlsx", 
  "dueDate" = "2017-01-01", 
  "isCompleted" = false
  "projectId" = "7987", 
  "projectTitle" = "10001 - Website Design", 
  "type" = "Meeting", 
  "typeId" = "3",
  "ownerId" = 2468
  }]
```


* `* DELETE v1/Activities/5` Deletes an activity 
``` javascript 
{ 
	"result" : true
}
```

* `* POST v1/Activities` Creates an activity. AccountID is required for any activity record regardless of what type of entity the activity is associated to. `EntityType` must be one of the following options: Account, Contact, Project, Lead, or RFP. `ActivityTypeID` should be one of the following: 1 = Note, 2 = Telephone Call, 3 = Meeting, 4 = Email, 5 = Document, 6 = Letter, 7 = Email Campaign, 8 = New Sales Meeting, 9 = Followup Meeting, 10 = Project Deadline
``` javascript
{
   AccountID:210954,
   DueDate:'2018-07-27',
   UserID:2468,
   EntityType:'Contact',
   EntityID:61471,
   ActivityTypeID:1,
   IsCompleted:false,
   Details:'The details of the activity'
}
```


* `* PUT v1/Activities` Updates an activity.  AccountID is required for any activity record regardless of what type of entity the activity is associated to. `EntityType` must be one of the following options: Account, Contact, Project, Lead, or RFP. `ActivityTypeID` should be one of the following: 1 = Note, 2 = Telephone Call, 3 = Meeting, 4 = Email, 5 = Document, 6 = Letter, 7 = Email Campaign, 8 = New Sales Meeting, 9 = Followup Meeting, 10 = Project Deadline
``` javascript
{
   ActivityID: 2344,
   AccountID:210954,
   DueDate:'2018-07-27',
   UserID:2468,
   EntityType:'Contact',
   EntityID:61471,
   ActivityTypeID:1,
   IsCompleted:false,
   Details:'The details of the activity'
}
```

* `* PUT v1/Activities/2134/status?completed=true|false` Updates an activity status. Pass either true or false for the completed flag
