# Invoices
Use Invoices to manage invoice related items in CMap

* `* GET v1/invoices/forimport` Returns all invoices that have yet to be marked as imported (imported into external finance system) within CMap

```javascript
[{  "InvoiceID" = 12354,
    "InvoiceNumber" = "1234",
    "Net" = 99.99, // converted to the currency of the office that the associated project belongs to
    "VAT" = 99.99, // converted to the currency of the office that the associated project belongs to
    "SourceNet" = 99.99, //value of the original invoice before any currency conversions
    "SourceVAT" = 99.99, //value of the original invoice before any currency conversions
    "Office" = "UK Office",
    "Team" = "Design Team",
    "LegalEntity" = "UK",
    "AccountName" = "ABC Ltd",
    "ProjectCode" = "98765",
    "ProjectTitle" = "New Website Design",
    "Date = "2022-01-01",
    "InvoiceAddress1" = "Head Office",
    "InvoiceAddress2" = "Church Street",
    "InvoiceTownCity" = "Wilsmlow",
    "InvoiceCountyState" = "Cheshire",
    "InvoicePostCode" = "SK9 1AX",
    "ContactTelNo" = "01625 521 000",
    "ContactName" = "Richard Smith",
    "ExtVATID" = "346", // T-Code from external finance system
    "VATRate" = 20,
    "PONumber" = "4343534",
    "Description" = "Initial 50%",
    "CurrencyID" = "1",
    "CurrencyAbbreviatedName" = "GBP",
    "CurrencySymbol" = "£",
    "SageAccountCode" = "ABC123",
    "Location" = "Design Team",
    "InvoiceLines" = [{
        "Information" = "Invoice Line Description,
        "Net" = 99.99,
        "VAT" = 99.99,
        "EntityType" = "BudgetSection" // This will be BudgetSection representing a stage in the Fee Estimator or Additional for an External
        }]
  }]
```

* `* PUT v1/invoices/Import` Marks invoices with matching Ids as imported into the external finance system
``` javascript
{
   "InvoiceIds":[23,34,45]
}
```

* `* POST v1/invoices/MarkAsPaid` Marks invoices with matching Ids as paid
``` javascript
[23,34,45]
```