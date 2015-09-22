# Contacts
Use contacts to list, view or search for contacts within CMAP

## Get Contacts
* `* GET v1/Contacts` Returns all contacts belonging to the client
```javascript
[{
	"company" : "Smith Industries",
	"id" : "876876",
	"name" : "Mike Smith"
}]
```

* `* GET v1/Contacts/5` Returns the contact with the matching id (if that contact exists)
```javascript
[{ 
	"id" : "234234",
	"email" : "mike.smith@smithindustries.com",
	"firstname" : "Mike",
	"lastname" : "Smith",
	"linkedIn" : "linkedin profile url",
	"mainContact" : "true",
	"mobile" : "07533 234 234",
	"notes" : "notes about this contact",
	"telephone" : "01625 521 000",
	"title" : "Mr",
	"twitter" : "twitter url",
	"jobTitle" : "Software Developer",
	"companyId" : "33454",
	"company" : "Smith Industries",
	"companyTelephone" : "01625 521 000",
	"address" : { "Address1" : "5 Hope Street",
				"Address2" : "",
				"Address3" : "",
				"TownCity" : "Manchester",
				'CountyState" : "Greater Manchester",
				"Postcode" : "M22 4TG" 
				}
}]
```

* `* GET v1/Contacts?q=[query]` Returns all contacts that match the search query
```javascript
[{
	"company" : "Smith Industries",
	"id" : "876876",
	"name" : "Mike Smith"
	},{
	"company" : "Smith Industries",
	"id" : "3534",
	"name" : "Mike Jones"
}]
```