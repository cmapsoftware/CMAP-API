# Purchase Invoices

Use Purchase Invoices to manage the pushing of Purchase Invoices into CMap from an external source

## Create Batch

- `* POST v1/PurchaseInvoices/PushPurchaseInvoices` Creates a Batch of Purchase Invoices containing the array of supplied Purchase Invoices, the Batch will be named "Imported - dd/MM/yy HH:mm" and will be associated the Office of the User making the API call.

### Headers

| Header         | Value          | Description                                                                                     |
| -------------- | -------------- | ----------------------------------------------------------------------------------------------- |
| Authorization  | Bearer {token} | The authentication token for the user making the API call.                                      |
| Content-Type   | application/json | The media type of the request body.                                                           |

### Body

Body must be an array of JSON objects. The following properties are supported:

| Property              | Type     | Description                                                                                                                                                                                             |
| --------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Date`                | `string` | Date of invoice - in format `"yyyy-mm-dd"`.                                                                                                                                                             |
| `InvoiceNumber`       | `string` | Invoice number to save purchase invoice as.                                                                                                                                                             |
| `InternalReference`   | `string` | Internal Reference of the purchase invoice to.                                                                                                                                                          |
| `Currency`            | `string` | 3 letter currency code eg. EUR                                                                                                                                                                          |
| `AccountId`           | `int64`  | ID of the supplier in CMap.                                                                                                                                                                             |
| `AccountName`         | `string` | The account name in CMap of the supplier only used if AccountId is not populated. Either AccountId or AccountName must match an existing supplier in CMap otherwise purchase invoice will not be saved. |
| `Nominal`             | `string` | Name of nominal to save invoice to. Must match nominal in CMap if provided.                                                                                                                             |
| `ProjectId`           | `int64`  | ID of the project to assign the invoice to in CMap - One of ProjectId, ProjectCode, or ProjectCodeAndTitle used to identify which project to save invoice against. Optional - Default 0 if not supplied |
| `ProjectCode`         | `string` | Project Code in CMap ie. the number before the project title. Only used if ProjectId is not populated.                                                                                                  |
| `ProjectCodeAndTitle` | `string` | Full project code and title in format: `ProjectCode - ProjectTitle`. NOT RECOMMENDED: use ProjectCode instead. Only used if ProjectId and ProjectCode are not populated.                                |
| `PurchaseOrderNumber` | `string` | Purchase Order number to save purchase invoice to. Must have a populated project with a matching PO.                                                                                                    |
| `BudgetExternalId`    | `int64`  | ID of the budget external (additional) in CMap to save to. Requires a project to have been matched ID most match a budget external on said project. Optional - default 0.                               |
| `VATRate`             | `double` | Percentage VAT rate as a double (eg. for 17.5% use 17.5) must match a VAT rate for the API user's BusinessUnit.                                                                                         |
| `ExtVATID`            | `int64`  | Rate ID for vat rate. Assigns VatRate by matching on ExtVATID, VAT rate to match on must exist for API user's business unit. Overrides VatRate property.                                                |
| `Description`         | `string` | Description of the Purchase Invoice.                                                                                                                                                                    |
| `Net`                 | `double` | Net Value of the purchase invoice in currency specified.                                                                                                                                                |
| `VAT`                 | `double` | Amount of VAT in currency specified.                                                                                                                                                                    |


#### Example:
```json
[
  {
    "AccountId": 123,
    "AccountName": "Acme Inc.", // Only used if AccountId is not present
    "ProjectId": 123,
    "ProjectCode": "1004", // Only used if projectId is not present
    "ProjectCodeAndTitle": "1004 - My project", // Only used if ProjectId and ProjectCodeAndTitle are not present
    "BudgetExternalId": 202148,
    "Currency": "USD",
    "Date": "2024-04-04", // Date must be in this format: yyyy-mm-dd
    "Description": "Client description of purchase invoice",
    "InternalReference": "INT-0141",
    "InvoiceNumber": "INV-0024",
    "Nominal": "Q007-000 - Legal",
    "PurchaseOrderNumber": "1021",
    "Net": 1000,
    "VAT": 175,
    "VATRate": 17.5,
    "ExtVATID": "132" // Overwrites VatRate,
  },
  {
    // ...etc
  }
]
```
Note that even if you only have one item in the batch you still need to send them as an array (using square brackets).

### Returns
Returns an array of JSON objects containing Ids of PIs successfully pushed to allow further requests to update them.

| Property              | Type     | Description                                                                                                                                                                                             |
| --------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `PurchaseInvoiceId`   | `int`    | The ID of the purchase invoice that was successfully pushed.                                                                                                                                            |
| `InternalReference`   | `string` | The internal reference of the purchase invoice.                                                                                                                                                         |
| `InvoiceNumber`       | `string` | The invoice number of the purchase invoice.                                                                                                                                                             |

#### Example:
```json
[
  {
    "PurchaseInvoiceId": 28724,
    "InternalReference": "INT-0141",
    "InvoiceNumber": "INV-0024",
  },
  {
    // ...etc
  }
]
```



## Attach Document To Purchase Invoice

- `POST v1/PurchaseInvoices/{purchaseInvoiceId}/AttachDocument?fileName={documentName.extension}` Uploads and attaches the provided document purchase invoice specified.

### Example Request

```
POST /v1/PurchaseInvoices/123/AttachDocument?fileName=MyFile.pdf
Host: api.cmaphq.com
Content-Type: application/pdf
Content-Length: 19

<RAW FILE CONTENTS>
```

### Headers

Required headers:

| Header          | Value           | Description                                                                                   |
| --------------- | --------------- | --------------------------------------------------------------------------------------------- |
| Authorization   | Bearer {token}  | The authentication token for the user making the API call.                                    |
| Content-Type    | [MIME Type]     | This needs to be set to match the MIME type of the file you want to attach.                   |
| Content-Length  | [File Size]     | Size of the file you want to attach in Bytes.                                                 |


### Parameters

| Parameter  | Type     | Description                                                                     |
| ---------- | -------- | ------------------------------------------------------------------------------- |
| `fileName` | `string` | The name of the file including the file extension. This is a required parameter |

### Returns

If successful you will receive a `200 OK` status along with a JSON response object.

| Property            | Type     | Description                                              |
| ------------------- | -------- | -------------------------------------------------------- |
| `PurchaseInvoiceId` | `int64`  | Id of the purchase invoice the document was attached to. |
| `DocumentName`      | `string` | Name of the document.                                    |
| `DocumentId`        | `int64`  | Id of the document that was uploaded.                    |
| `DocumentMimeType`  | `string` | MimeType document saved as.                              |
| `DocumentSize`      | `int64`  | Size of the file that was uploaded in bytes              |

#### Example Response:

```
{
    "PurchaseInvoiceId": 123,
    "DocumentName": "MyFile.pdf",
    "DocumentId": 456,
    "DocumentMimeType": "application/pdf",
    "DocumentSize": 10000
}
```

### Restrictions

#### Permitted File Types

| File Extension    | Content-Type                                                              |
| ----------------- | ------------------------------------------------------------------------- |
| `.pdf`            | `application/pdf`                                                         |
| `.png`            | `image/png`                                                               |
| `.jpg` or `.jpeg` | `image/jpeg`                                                              |
| `.txt`            | `text/plain`                                                              |
| `.csv`            | `text/csv`                                                                |
| `.xls`            | `application/vnd.ms-excel`                                                |
| `.xlsx`           | `application/vnd.openxmlformats-officedocument.spreadsheetml.sheet`       |
| `.doc`            | `application/msword`                                                      |
| `.docx`           | `application/vnd.openxmlformats-officedocument.wordprocessingml.document` |

#### File Name Restrictions

- All File names must be URL encoded.
- Any file names containing any ASCII control characters or any of the following characters will be rejected: ` < > : " / \ | ? * \0`.
- The length of any file name (including the extension) must be `200` characters or less.
- All file names must include the file extension of the particular file at that must match the provided content-type (see above for full list.)

#### File Size Restrictions

- Any file being uploaded must be less than 150Mb in size.

#### Permissions

- You CMap instance must have the documents module enabled.
- The user account making the request must have `Full Control` permissions to edit the purchase invoice via the relevant finance page (ie. single line purchase invoice or (batch) purchase invoice).
