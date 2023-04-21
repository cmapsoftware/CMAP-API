# TimeOff
Use TimeOff to manage holiday bookings in CMAP

## Get TimeOff
* `* GET v2/TimeOff/all` Returns all the time off 

```javascript
[{ 
	"id" : 234234,
	"actualDays" : 2, 
	"booked" : true, 
	"date" : "2015-07-01", 
	"duration" : 2, 
	"code" : "Holiday",
	"codeId" : 0,
	"notes" : "Some notes about the holiday", 
	"rejected" : true, 
	"requested" : true,
	"hours": 16,
	"isHoursBooking": false
}]
```

* `* GET v1/TimeOff` Returns all the time off for the logged in user

```javascript
[{ 
	"id" : 234234,
	"actualDays" : 2, 
	"booked" : true, 
	"date" : "2015-07-01", 
	"duration" : 2, 
	"code" : "Holiday",
	"codeId" : 0,
	"notes" : "Some notes about the holiday", 
	"rejected" : true, 
	"requested" : true
}]
```

* `* GET v1/TimeOff/5` Returns all the time off with the matching id

```javascript
[{ 
	"id" : 5,
	"actualDays" : 2, 
	"booked" : true, 
	"date" : "2015-07-01", 
	"duration" : 2, 
	"code" : "Holiday",
	"codeId" : 0,
	"notes" : "Some notes about the holiday", 
	"rejected" : true, 
	"requested" : true
}]
```

* `* GET v1/TimeOff/allowance` Returns the current years holiday allowance for the logged in user

```javascript
{
	"days" : 25,
	"daysRemaining" : 4,
	"carriedForward" : 3,
	"timeInLieu" = 0,
	"allowances" = [
		{"allowance":1, "allowanceRemaing" : 0, "code": "Birthday", "codeId" : 3},
		{"allowance":2, "allowanceRemaing" : 2, "code" : "Family Time", "codeId" : 2}
	]
}
```

* `* POST v1/TimeOff` Request a new holiday. `pm` allows `true` or `false`, true indicating that this holiday will start at 12 noon. HolidayCodeId 0 indicates the standard Holiday Allowances, whereas specifying the HolidayCodeId as something other than 0 indicates a specific time off code. Returns `Success` if the holiday was successfully requested, or `Conflict` if there was already holiday requests for this time period for this user.

```javascript
{
    "UserID": 123456, /* The user to book holiday for. Defaults to the user of the API, if you have the TimeOff admin permission then this can be a user other than the API user. */
    "Date": "2022-10-03",
    "Duration": 5,
    "Notes": "Optional notes about the holiday request",
    "pm": true | false,
    "status": "Requested" | "Approved", /* The status of the holiday, defaults to Requested, if you have the TimeOff admin permission then this can be created with the status Approved (No appproval emails will be sent). */
    "HolidayCodeID": 0 | [HolidayCodeId]
}
```

* `* PUT v1/TimeOff` Update a requested holiday. `pm` allows `true` or `false`, true indicating that this holiday will start at 12 noon. HolidayCodeId 0 indicates the standard Holiday Allowances, whereas specifying the HolidayCodeId as something other than 0 indicates a specific time off code. Note that HolidayID must be specified.

```javascript
{
    "HolidayId": 123456,
    "Date": "2022-10-03",
    "Duration": 5,
    "Notes": "Optional notes about the holiday request",
    "pm": true | false,
    "status": "Requested" | "Approved", /* The status of the holiday, defaults to Requested, if you have the TimeOff admin permission then this can be updated to the status Approved (No appproval emails will be sent). */
    "HolidayCodeID": 0 | [HolidayCodeId]
}
```

* `* DELETE v1/TimeOff/5` Deletes a holiday

* `* POST v1/TimeOffAllowance` Creates a holiday allowance for a user

```javascript
{
	"UserID":"12345" /* who the entitlement is for */
	"Year":"2020" /* When the entitlement is for */
	"HolidayCodeID":"0" /* This has to be 0 for regular CMAP holidays or the ID of the client specific holiday code */
	"Days":"25" /* number of days for the entitlement */
	"CarriedForward":"0" /* number of days, only relevant for CMAP Holidays */
	"InLieu":"0" /* number of days, only relevant for CMAP Holidays */
}
```


* `* PUT v1/TimeOffAllowance` Updates a holiday allowance for a user

```javascript
{
	"UserID":"12345" /* who the entitlement is for */
	"Year":"2020" /* When the entitlement is for */
	"HolidayCodeID":"0" /* This has to be 0 for regular CMAP holidays or the ID of the client specific holiday code */
	"Days":"25" /* number of days for the entitlement */
	"CarriedForward":"0" /* number of days, only relevant for CMAP Holidays */
	"InLieu":"0" /* number of days, only relevant for CMAP Holidays */
}
```
