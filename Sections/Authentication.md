# Authentication
All CMAP Integration Apps must include their Client API Key in as a header
`ClientApi-Key: [your key goes here]`
Request a token for a CMAP user to make further requests to the API. Once a token has been requested this must be included on all subsequent requests as an `Authorization` header (Bearer token)

## POST Request Token
* `POST v1/Auth/Requesttoken` returns valid token for user
```javascript
{
	"username":"[user's cmap username]",
  "password":"[user's cmap password]",
  "subdomain":"[cmap sub domain]"
}
```
