# Custom Fields
Use custom fields to manage custom field information in CMAP

* `* POST v1/CustomFields/SetField` Creates the custom field information for the specified user.

```javascript
{ "UserID" = "12345", 
  "CustomFieldName" = "Legal Entity", 
  "CustomFieldValue" = "UK"
  }
  ```
  
  * `* PUT v1/CustomFields/SetField` Updates the custom field information for the specified user.

```javascript
{ "UserID" = "12345", 
  "CustomFieldName" = "Legal Entity", 
  "CustomFieldValue" = "USA"
  }
  ```
