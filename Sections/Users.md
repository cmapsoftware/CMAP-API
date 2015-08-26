# Users
Use users to list all users or search for users

## Get Users
* `* GET v1/users` Returns all unarchived users for the client

```javascript
[{
	"ddi" : "016125 521 002"
	"email" : "jim.murphy@ozone.com"
	"firstname" : "Jim",
	"id" : "23423",
	"jobTitle" : "Director",
	"lastname" : "Murphy",
	"mobile" : "07955 876 365",
	"officeTelephone" : "01625 521 000" 
}]
```

* `* GET v1/users?q=[query]` Returns all unarchived users for the client that match the search query

```javascript
[{
	"ddi" : "016125 521 002"
	"email" : "jim.murphy@ozone.com"
	"firstname" : "Jim",
	"id" : "23423",
	"jobTitle" : "Director",
	"lastname" : "Murphy",
	"mobile" : "07955 876 365",
	"officeTelephone" : "01625 521 000" 
}]
```

* `* GET v1/users/5/photo` Returns the profile photo for the specified user as a png