# Projects
Use projects to search for projects within CMAP

## Get Projects
* `* GET GET v1/projects/?status=potential|project|closed&q=[query]` Returns the projects that match search query and status

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