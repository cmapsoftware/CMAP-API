# Projects
Use projects to search for projects within CMAP

## Get Projects
* `* GET v1/projects/?status=potential|project|closed&q=[query]` Returns the projects that match search query and status

```javascript
[{
	"company" : "Smith Industries",
	"code" : "34543",
	"codeAndTitle" : "34543 - New Project",
	"id" : "7867",
	"title" : "New Project"
},
{
	"company" : "Smith Corp",
	"code" : "10001",
	"codeAndTitle" : "10001 - Website Project",
	"id" : "453466",
	"title" : "Website Project"
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
