# Clients
Use clients to retrieve information about a client, for example what features they have switched on

## Get Features
* `* GET v1/Clients/Features` Returns all features switched on for the client
```javascript
{
  "Timesheets" = true,
  "TimesheetRolePicker" = true,
  "TimesheetWorkActivities": false
}
```
