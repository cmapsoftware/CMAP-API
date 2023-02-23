# Resources
Use resources to return various helper items used throughout the system

## Get Resources
* `* GET v1/resources/vatrates` Returns the vat rates available based on the logged in user's team

```javascript
[{ 
	"id" : "12",
	"name" : "0%",
	"rate" : "0" 	
},{ 
	"id" : "13",
	"name" : "20%",
	"rate" : "20" 	
}]
```

* `* GET v1/resources/expensecategories` Returns the available expenses categories that expense items can be booked to, and the default VAT rate id if applicable

```javascript
[{ 
	"id" : "12",
	"name" : "Accommodation",
	"defaultVatRateId": "13"
},{ 
	"id" : "13",
	"name" : "Train Tickets",
	"defaultVatRateId": ""
}]
```


* `* GET v1/resources/mileagerates` Returns the mileage rates available for expense claims based on the logged in user

```javascript
[{ 
	"id" : "12",
	"name" : "Private Miles",
	"rate" : "0.45" 	
},{ 
	"id" : "13",
	"name" : "Company Car",
	"rate" : "0.35" 	
}]
```

* `* GET v1/resources/internalcodes` Returns the list of internal codes available for timesheet entries

```javascript
[{ 
	"id" : "12",
	"name" : "Meeting"	
},{ 
	"id" : "13",
	"name" : "Travel"	
}]
```

* `* GET v1/resources/workactivities` Returns the list of work activities for the client
```javascript
[{ 
	"id" : "1",
	"name" : "Site Investigation",
	"order" : "1",
	"isArchived" : false
},{ 
	"id" : "1",
	"name" : "Site Review",
	"order" : "2",
	"isArchived" : false	
}]
```

* `* GET v1/resources/currencies` Returns the list of currencies available for the client

```javascript
[{ 
	"abbreviation" : "GBP",
	"id" : "343",
	"name" : "Great British Pounds",
	"symbol" : "£"
},{ 
	"abbreviation" : "EUR",
	"id" : "345",
	"name" : "EURO",
	"symbol" : "€"
}]
```

* `* GET v1/resources/holidaycodes` Returns the list of holiday codes based on the logged in user's office

```javascript
[{ 
	"id" : "12",
	"code" : "Birthday"	
},{ 
	"id" : "13",
	"code" : "Sickness"	
}]
```

* `* GET v1/resources/activitycategories` Returns the list of currently available activity categories

```javascript
[{ 
	"id" : "1",
	"name" : "Meeting"	
},{ 
	"id" : "2",
	"name" : "Telephone Call"	
}]
```

* `* GET v1/resources/expensebillingtypes` Returns the list of billing types related to expenses

```javascript
[{ 
	"id" : "1",
	"name" : "Charge"	
},{ 
	"id" : "2",
	"name" : "No Charge"	
},{ 
	"id" : "3",
	"name" : "Allowance"	
}]
```

* `* GET v1/resources/clientholidaycodes` Returns the list of client holiday codes

```javascript
[{ 
	"id" : "1",
	"code" : "Sickness",
	"officeId" : "1",
	"officeName" : "UK"
},{ 
	"id" : "2",
	"code" : "Training",
	"officeId" : "1",
	"officeName" : "UK"	
}]
```
