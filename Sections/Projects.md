# Projects
Use projects to search for projects within CMAP

## Get Projects
* `* GET v1/projects/?type=[expenses|timesheets]&q=[query]` Returns the projects that match search query. Type can be `expenses` or `timesheets`. This returns projects for the user that are available for the to book time to on their timesheets and book expenses against.

```javascript
[{
	"Id" : "767678",
	"AccountName" : "Smith Industries",
	"Code" : "34543",
	"Title" : "34543 - New Project",
	"StatusId" : "3", //1 = Potential, 3 = Live Project, 4 = Closed Project
	"IsContract": false,
	"projectManager": {
		"id": 12345,
		"name": "John Smith",
		"email": "john.smith@company.com"
	},
	"owner": {
		"id": 12345,
		"name": "John Smith",
		"email": "john.smith@company.com"
	}
},
{
	"Id" : "767678",
	"AccountName" : "Smith Industries",
	"Code" : "34543",
	"Title" : "34543 - New Project",
	"StatusId" : "3", //1 = Potential, 3 = Live Project, 4 = Closed Project,
	"IsContract": false,
	"projectManager": {
		"id": 12345,
		"name": "John Smith",
		"email": "john.smith@company.com"
	},
	"owner": {
		"id": 12345,
		"name": "John Smith",
		"email": "john.smith@company.com"
	}
}]
```

## Get Projects
* `* GET v1/projects/?status=[status]&q=[query]` Returns the projects that match search query and status. Status can be `Potential` or `Project` or `Closed` - note: status is case sensitive

```javascript
[{
	"companyId" : "767678",
	"company" : "Smith Industries",
	"code" : "34543",
	"codeAndTitle" : "34543 - New Project",
	"id" : "7867",
	"title" : "New Project"
},
{
	"companyId" : "767668",
	"company" : "Smith Corp",
	"code" : "10001",
	"codeAndTitle" : "10001 - Website Project",
	"id" : "453466",
	"title" : "Website Project"
}]
```

## Get Projects
* `* GET v1/projects/?type=[type]&q=[query]` Returns the projects for timesheets or expenses that match the search query. The type can be `expenses` or `timesheets`

```javascript
[{
	"id" : "7867"
	"name" : "34543 - New Project",
	"isContract" : "false"
},
{
	"id" : "453466",
	"name" : "10001 - Website Project",
	"isContract" : "false"
}]
```

## Get Contact Projects
* `* GET v1/projects/?status=[status]&contactId=876` Returns all the projects associated with a contact. The status of the project can be `potential` or `project` or `closed` or 'lead' or 'rfp'

```javascript
[{
	"id" : "7867"
	"code" : "34543",
	"title" : "Onboarding Project"
	"fee" : £57899
},
{
	"id" : "4356"
	"code" : "45656",
	"title" : "Development Project"
	"fee" : £89789
}]
```

## Get Company Projects
* `* GET v1/projects/?status=[status]&companyId=823423` Returns all the projects associated with a contact. The status of the project can be `potential` or `project` or `closed` or 'lead' or 'rfp'

```javascript
[{
	"id" : "7867"
	"code" : "34543",
	"title" : "Onboarding Project"
	"fee" : £57899
},
{
	"id" : "4356"
	"code" : "45656",
	"title" : "Development Project"
	"fee" : £89789
}]
```

## Get Project Details
* `* GET v1/project/[id]` Returns the details for a project with the specified ID

```javascript
{ 
	"Title", "Smith Industries"
	"Code", "34543",
	"Status", "Potential",
	"Contact", "John Smith",
	"Stage", "Initial Lead",
	"Probability", 10,
	"EstimatedPrice", 10000,
	"StartDate", "01/01/2017T00:00:00",
	"EndDate", "01/01/2018T00:00:00",
	"FeeType", "Fixed Fee",
	"Sector", "Health",
	"ProjectType", "Strategy",
	"LeadSource", "Existing Client",
	"Owner", "Jane Smith",
	"Private", "No"
	"Bio", ""
	"Total Project Value" : 0,
	"CustomFields" : {
		"TextField": "Custom Field Text",
		"TextAreaField": "Custom Field TextArea",
		"DropdownField": "Item 1",
		"DateField": "2019-12-31",
		"YesNoField": "Yes" | "No",
		"MultiLevelDropdownField": ["Item 1", "Item 1a", "Item 1aa"],
		"MultiSelectField": ["Item 1", "Item 3", "Item 4"],
		"UserDropdownField": "Gary Thickett",
		"UserMultiselectDropdownField": ["First User", "Second User", "Third User"],
		"NumberField": 1234567.89
	}
}
```
## Get Projects Updated Between Date Range
* `* GET v1/projects/updated?from=2019-01-01&to=2019-01-31` Returns the details for projects updated between the from and to dates

```javascript
{ 
	"Title", "Smith Industries"
	"Code", "34543",
	"Status", "Potential",
	"Contact", "John Smith",
	"Stage", "Initial Lead",
	"Probability", 10,
	"EstimatedPrice", 10000,
	"StartDate", "01/01/2017T00:00:00",
	"EndDate", "01/01/2018T00:00:00",
	"FeeType", "Fixed Fee",
	"Sector", "Health",
	"ProjectType", "Strategy",
	"LeadSource", "Existing Client",
	"Owner", "Jane Smith",
	"Private", "No"
	"Bio", ""
	"Total Project Value" : 0,
	"CustomFields" : {
		"TextField": "Custom Field Text",
		"TextAreaField": "Custom Field TextArea",
		"DropdownField": "Item 1",
		"DateField": "2019-12-31",
		"YesNoField": "Yes" | "No",
		"MultiLevelDropdownField": ["Item 1", "Item 1a", "Item 1aa"],
		"MultiSelectField": ["Item 1", "Item 3", "Item 4"],
		"UserDropdownField": "Gary Thickett",
		"UserMultiselectDropdownField": ["First User", "Second User", "Third User"],
		"NumberField": 1234567.89
	}
}
```

## Create Potential Project
* `* POST v1/project` Create a new Potential Project in CMAP. Note that if `Architectural` is supplied as a `FeeType` then the Project will be created as a Live project and not a Potential project. Any Custom Field created on the Project page can be specified in the `CustomFields` area with the field name and value, and these will be set when the new project is created.<br/><br/>Note that the logged in User will only be able to create a `Project` for an `Office` and `Team` that they have access to in CMap. Not specifying `Office` and `Team` will result in the Project defaulting back to the `Office` and `Team` linked to the `Owner` field specified.

```javascript
{
  "Title":"Awesome New Opportunity",
  "Company":"Awesome Inc",
  "Contact":"Dave Awesome",
  "Email": "email@email.com",
  "Office": "Office Name",
  "Team": "Team Name",
  "Stage":"Project Stage 1",
  "Probability":"50",
  "StartDate":"2019-01-01",
  "EndDate":"2019-12-31",
  "Sector":"Creative",
  "ProjectType":"CMAP Services",
  "LeadSource":"Email",
  "ProjectManager":"Gary Thickett",
  "Owner":"Gary Thickett",
  "FeeType": "FixedFee" | "Architectural" | "PureTimeMaterials" | "ResourcedTimeMaterials" | "Syndication" | "Retainer",
  "EstimatedPrice": 1000000,
  "ExternalRef":"50345-sdf",              
  "CustomFields" : {
	  "TextField": "Custom Field Text",
	  "TextAreaField": "Custom Field TextArea",
	  "DropdownField": "Item 1",
	  "DateField": "2019-12-31",
	  "YesNoField": "Yes" | "No",
	  "MultiLevelDropdownField": ["Item 1", "Item 1a", "Item 1aa"],
	  "MultiSelectField": ["Item 1", "Item 3", "Item 4"],
	  "UserDropdownField": "Gary Thickett",
	  "UserMultiselectDropdownField": ["First User", "Second User", "Third User"],
	  "NumberField": 1234567.89
  }
}
```

## Update Project
* `* PUT v1/projects/UpdateProject` Update a Project in CMAP. Only `Live` or `Potential` projects can be updated. Any Custom Field on the Project page can be specified in the `CustomFields` area with the field name and value, and these will be updated with the project.<br/><br/>Note that the logged in User will only be able to update a `Project` to an  `Office` and `Team` that they have access to in CMap. Not specifying `Office` and `Team` will result in the Project defaulting back to the `Office` and `Team` linked to the `Owner` field specified.<br><br/>`Stage`, `Probability` and `FeeType` can only be updated on `Potential` projects only.

```javascript
{
  "Title":"Awesome New Opportunity",
  "Company":"Awesome Inc",
  "Contact":"Dave Awesome",
  "Email": "email@email.com",
  "Office": "Office Name",
  "Team": "Team Name",
  "Stage":"Project Stage 1",
  "Probability":"50",
  "StartDate":"2019-01-01",
  "EndDate":"2019-12-31",
  "Sector":"Creative",
  "ProjectType":"CMAP Services",
  "LeadSource":"Email",
  "ProjectManager":"Gary Thickett",
  "Owner":"Gary Thickett",
  "FeeType": "FixedFee" | "Architectural" | "PureTimeMaterials" | "ResourcedTimeMaterials" | "Syndication" | "Retainer",
  "EstimatedPrice": 1000000,
  "ExternalRef":"50345-sdf",              
  "CustomFields" : {
	  "TextField": "Custom Field Text",
	  "TextAreaField": "Custom Field TextArea",
	  "DropdownField": "Item 1",
	  "DateField": "2019-12-31",
	  "YesNoField": "Yes" | "No",
	  "MultiLevelDropdownField": ["Item 1", "Item 1a", "Item 1aa"],
	  "MultiSelectField": ["Item 1", "Item 3", "Item 4"],
	  "UserDropdownField": "Gary Thickett",
	  "UserMultiselectDropdownField": ["First User", "Second User", "Third User"],
	  "NumberField": 1234567.89
  }
}
```
