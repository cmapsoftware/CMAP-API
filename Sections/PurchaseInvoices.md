# Purchase Invoices
Use Purchase Invoices to manage the pushing of Purchase Invoices into CMap

## Create Batch
* `* POST v1/PurchaseInvoices/PushPurchaseInvoices` Creates a Batch of Purchase Invoices containing the array of supplied Purchase Invoices, the Batch will be named "Imported - dd/MM/yy HH:mm" and will be associated the Office of the User making the API call.
```javascript
[{
      "Date":"2023-01-01",
      "InvoiceNumber":"5435345",
      "InternalReference":"Ref 234234234",
      "Currency":"GBP",
      "AccountId":123, //either AccountId or AccountName must be supplied and match an existing Account else the Purchase Invoice won't be correctly imported, default of 0 if not supplied 
      "AccountName":"Acme Inc.",
      "Nominal":"Q007-000 - Legal", //must match an existing nominal if provided
      "ProjectId":1232432, //either ProjectId or ProjectCode must be supplied and match an existing Project for the Purchase Invoice, default of 0 if not supplied
      "ProjectCode":"5679",
      "BudgetExternalId":4534534, //Id of the Budget External the Purchase Invoice should be associated with (optional), default of 0 if not supplied
      "VATRate":"20", //must match an existing VAT Rate
      "Description":"Client description of purchase invoice",
      "Net":"100", 
      "VAT":"20"
}]
```
