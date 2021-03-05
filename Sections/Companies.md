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

* `* POST v1/Companies/` Creates the Company and returns the Id
```javascript
[{ 
	"name" : "Smith Industries",
	"telephone" : "01625 521 000",
	"website" : "http://www.smithindustries.com",
	"fax" : "01625 521 001",
	"paymentDays": "30",
	"notes" : "Some information about this company",
	"addresses" : [{
		"description":"HQ",
		"address1":"1 Hope Street",
		"address2":"",
		"address3":"",
		"townCity":"Manchester",
		"countyState":"Greater Manchester",
		"postcode":"M22 4TG"
	}]
}]
```

* `* PUT v1/Companies/` Creates the Company and returns the Id
```javascript
[{ 
	"accountId":"5",
	"name" : "Smith Industries",
	"telephone" : "01625 521 000",
	"website" : "http://www.smithindustries.com",
	"fax" : "01625 521 001",
	"paymentDays": "30",
	"notes" : "Some information about this company",
	"addresses" : [{
		"description":"HQ",
		"address1":"1 Hope Street",
		"address2":"",
		"address3":"",
		"townCity":"Manchester",
		"countyState":"Greater Manchester",
		"postcode":"M22 4TG"
	}]
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

* `* GET v1/Companies/5/Addresses` Returns all addresses associated with a company
```javascript
[{
	"AddressID" : 32432,
	"Description" : "Manchester Headquarters",
	"Address1" : "5 Hope Street",
	"Address2" : "",
	"Address3" : "",
	"TownCity" : "Manchester",
	"CountyState" : "Greater Manchester",
	"Postcode" : "M22 4TG"
}]
```
