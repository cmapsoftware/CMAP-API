# Favourites
Use favourites to retrieve a list of items by type for a CMAP user

## Get Favourites
* `* GET v1/favourites/?type=contacts|companies|projects` Returns favourites for a user of the type requested

Favourite contacts
```javascript
[{ 
	"companyId" : "345435"
	"company" : "Smith Industries",
	"id" : "6456546",
	"email" : "john@smithind.com", 
	"name" : "John Doe",
	"mobile" : "09898 345 345",
	"telephone" : "01625 521 000"
 }]

```

Favourite companies
```javascript
[{
	"id" : "6456546",
	"email" : "john@smithind.com", 
	"name" : "John Doe",
	"telephone" : "01625 521 000"
}]
```

Favourite projects
```javascript
[{
	"company" : "Smith Industries",
	"code" : "243324",
	"id" : "234",
	"title" : "New website development",
	"codeAndTitle" : "243324 - New website development"
}]
```