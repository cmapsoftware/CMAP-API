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

* `* GET v1/Contacts?companyId=5` Returns all contacts belonging to the company
```javascript
[{
	"id" : "876876",
	"firstName" : "Mike",
	"lastName" : "Smith",
	"displayName" : "Smith, Mike",
	"email" : "mike.smith@something.com",
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
				"CountyState" : "Greater Manchester",
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

* `* GET v1/Contacts?email=email&name=name` Returns all the contacts that match the email address or name specified
```javascript
[{
 	"id" = "3455",
	"firstName" = "John",
	"lastName" = "Smith",
	"companyId" = "56546",
	"jobTitle" = "CEO",
	"directPhone" = "01625 521 000",
	"mobilePhone" = "07966 000 999",
	"emailAddress" = "john.smith@noreply.com",
	"contactOwner" = "",
	"mainContact" = true,
	"accountsContact" = false,
	"notes" = "",
	"company" = "No Reply Ltd",
	"name" = "John Smith",
	"matchingEmail" = "john.smith@noreply.com"
}]
```

* `* POST v1/Contacts` Creates a new client in CMAP
```javascript
{
	"firstName" : "Robert",
	"lastName" : "Smith",
	"companyId" : 12456,
	"jobTitle" : "Managing Director",
	"telephone" : "01625 521 000",
	"mobile" : "07799 876543",
	"email" : "robert.smith@abc.com",
	"addressId" : 324,
	"ownerId" : 454,
	"mainContact" : true,
	"financeContact" : false,
	"notes" : "Some information about this contact"
}


* `* PUT v1/Contacts` Updates a new client in CMAP
```javascript
{
	"contactId" : 987897
	"firstName" : "Robert",
	"lastName" : "Smith",
	"companyId" : 12456,
	"jobTitle" : "Managing Director",
	"telephone" : "01625 521 000",
	"mobile" : "07799 876543",
	"email" : "robert.smith@abc.com",
	"addressId" : 324,
	"ownerId" : 454,
	"mainContact" : true,
	"financeContact" : false,
	"notes" : "Some information about this contact"
}
