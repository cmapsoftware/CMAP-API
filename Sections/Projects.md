# Projects
Use projects to search for projects within CMAP

## Get Projects
* `* GET v1/projects/?type=[expenses|timesheets]&q=[query]` Returns the projects that match search query. Type can be `expenses` or `timesheets`. This returns projects for the user that are available for the to book time to on their timesheets and book expenses against.

```javascript
[{
	"ProjectId" : "767678",
	"AccountName" : "Smith Industries",
	"Code" : "34543",
	"Title" : "34543 - New Project",
	"StatusId" : "3" //1 = Potential, 3 = Live Project, 4 = Closed Project
},
{
	"ProjectId" : "767678",
	"AccountName" : "Smith Industries",
	"Code" : "34543",
	"Title" : "34543 - New Project",
	"StatusId" : "3" //1 = Potential, 3 = Live Project, 4 = Closed Project
}]
```

## Get Projects
* `* GET v1/projects/?status=[status]&q=[query]` Returns the projects that match search query and status. Status can be `potential` or `project` or `closed`

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
        "Total Project Value" : 0 
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
        "Total Project Value" : 0 
}
```

## Create Potential Project
* `* POST v1/projects` Create a new Project in CMAP

```javascript
{
  "Title":"Awesome New Opportunity",
  "Company":"Awesome Inc",
  "Contact":"Dave Awesome",
  "Stage":"",
  "Probability":"50",
  "StartDate":"2019-01-01",
  "EndDate":"2019-12-31",
  "Sector":"Creative",
  "ProjectType":"CMAP Services",
  "LeadSource":"Email",
  "ProjectManager":"Gary Thickett",
  "Owner":"Gary Thickett",
  "ExternalRef":"50345-sdf",              
}
```
