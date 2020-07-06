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
* `* GET v1/users/status` Returns status information for the logged in user such as current timesheet week, holiday days remaining, no. of weeks behind on their timesheet etc..

```javascript
[{
	"additionalTime" : true /* whether or not the client has the additional time feature activated */
	"workingHours" : "37.5" /* The user's current working hours */
	"weeksOverdue" : "4", /* number of weeks behind on their timesheets */
	"timesheetWeek" : "2015-11-16",
	"openClaims" : "3", /* no. of open expense claims */
	"overdueActivities" : "0",
	"todaysActivities" : "5",
	"contacts" : "4534", /* no. of contacts in the client's database */
	"users" : "45", /* no. of user accounts */
	"daysRemaining" : "1.5" /* no. of holiday days remaining */ 
}]
```


* `* GET v1/users/5/photo` Returns the profile photo for the specified user as a png

* `* GET v1/users/current` Returns the details for the logged in user

```javascript
[{
	"userId": 123456,
	"firstname": "Arthur",
	"lastname": "Dent",
	"locale": "en-gb",
	"timesheetWeek": "2019-07-22T00:00:00",
	"timeZone": "GMT Standard Time",
	"currencyId": 2,
	"currency": "United States Dollars",
	"currencyAbbreviated": "USD",
	"workingHours": 37.5,
	"dateFormat": "dd-mm-yy"
}]
```
* `* POST v1/users` Creates a User in CMAP

```javascript
{
"Firstname":"David",
"Lastname":"Smith",
"Email":"david.smith@abccorp.com",
"StartDate":"2020-01-01", /* must be in this format*/
"Status":"Employee",
"Office":"UK",
"Team":"Manchester",
"JobTitle":"Architect",
"DefaultRole":"Architect",
"Currency":"GBP",
"WorkingHours":"37.5",
"LineManager":"brian.davies@abccorp.com", /* must be an email address */
"TimeOffApprover":"brian.davies@abccorp.com", /* must be an email address */
"ExpenseApprover":"brian.davies@abccorp.com" /* must be an email address */
}
```

* `* PUT v1/users` Updates a User in CMAP

```javascript
{
"UserID":"12345",
"Firstname":"David",
"Lastname":"Smith",
"Email":"david.smith@abccorp.com",
"StartDate":"2020-01-01", /* must be in this format*/
"Status":"Employee",
"Office":"UK",
"Team":"Manchester",
"JobTitle":"Architect",
"DefaultRole":"Architect",
"Currency":"GBP",
"WorkingHours":"37.5",
"LineManager":"brian.davies@abccorp.com", /* must be an email address */
"TimeOffApprover":"brian.davies@abccorp.com", /* must be an email address */
"ExpenseApprover":"brian.davies@abccorp.com" /* must be an email address */
}
```
