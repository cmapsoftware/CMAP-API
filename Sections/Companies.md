# Companies
Use companies to list, view or search for companies within CMAP

## Get Companies
* `* GET v1/Companies` Returns all companies belonging to the client
```javascript
[{
	"id" : "876876",
	"name" : "Smith Industries"
}]
```

* `* GET v1/Companies/5` Returns the company with the matching id (if that company exists)
```javascript
[{ 
	"id" : "23423",
	"name" : "Smith Industries",
	"telephone" : "01625 521 000",
	"website" : "http://www.smithindustries.com",
	"fax" : "01625 521 001",
	"notes" : "Some information about this company",
	"address" : "1 Hope Street, Manchester, M22 4TG" 
}]
```

* `* GET v1/Companies?q=[query]` Returns all companies that match the search query
```javascript
[{
	"id" : "876876",
	"name" : "Smith Industries"
	},{
	"id" : "3345345",
	"name" : "Smith Corp."
}]
```