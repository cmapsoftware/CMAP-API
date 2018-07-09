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
  "typeId" = "3"
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
  "typeId" = "3"
  }
```

* `* DELETE v1/Activities/5` Deletes an activity 
``` javascript 
{ 
	"result" : true
}
```
