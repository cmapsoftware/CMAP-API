# Security
Use security to check whether the logged in user has access to certain permissions based on their Security Group

## Get Features
* `* POST v1/Security/HasPermission` Given an array of the security permissions required (SecurityID and valid permissions supplied by CMAP Software as needed)
```javascript
[
	{
		"SecurityID": 256,
        "SecurityPermission": "DefaultOptions.Edit"
	},
	{
		"SecurityID": 258,
        "SecurityPermission": "YesNo"
	},
	{
		"SecurityID": 2048,
        "SecurityPermission": "None",
        "ProjectID": 362854
	},
	{
		"SecurityID": 532,
        "SecurityPermission": "MinMax",
        "Value": 6000
	},
	{
		"SecurityID": 3072,
        "SecurityPermission": "OfficeOptions.FullControl"
	}
]
```
returns whether the user has access and a message, if needed.
```javascript
[
    {
        "SecurityID": 256,
        "SecurityPermission": "DefaultOptions.Edit",
        "ProjectID": null,
        "Value": null,
        "HasPermission": true,
        "Message": null
    },
    {
        "SecurityID": 258,
        "SecurityPermission": "YesNo",
        "ProjectID": null,
        "Value": null,
        "HasPermission": false,
        "Message": "You do not have permission, please speak to your CMAP administrator."
    },
    {
        "SecurityID": 2048,
        "SecurityPermission": "None",
        "ProjectID": 362854,
        "Value": null,
        "HasPermission": true,
        "Message": null
    },
    {
        "SecurityID": 532,
        "SecurityPermission": "MinMax",
        "ProjectID": null,
        "Value": 6000,
        "HasPermission": false,
        "Message": "You do not have permission, please speak to your CMAP administrator."
    },
    {
        "SecurityID": 3072,
        "SecurityPermission": "OfficeOptions.FullControl",
        "ProjectID": null,
        "Value": null,
        "HasPermission": false,
        "Message": "You do not have permission, please speak to your CMAP administrator."
    }
]
```