# OAuth 2 Authentication
To use CMAP's OAuth 2 authentication then you must first request your `client_id` and `client_secret` from our Support Team

## GET RequestAuth
Pass your `client_id` as a querystring variable along with `state` and your `redirect_uri`
* `GET v1/OAuth/RequestAuth` Returns a signin page for CMAP for the user to authenticate their account

## POST Retrieve Access Token
Use to exchange the Authorization Code for an Access Token
* `POST v1/OAuth/Exchange` Returns an access token
``` javascript
{
	code:[this is the authorization code returned from the initial RequestAuth request],
	client_id:[your client id],
	client_secret:[your client secret],
	redirect_url:[the url to redirect to],
	grant_type:'authorization_code'
}
```

## POST Refresh Access Token
Use to refresh the Access Token
* `POST v1/OAuth/Exchange` Returns a new access token
``` javascript
{
	refresh_token:[current access token],
	client_id:[your client id],
	client_secret:[your client secret],
	grant_type:'refresh_token'
}
```





# APP Authentication
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

## POST Forgot Password
* `POST v1/Auth/ForgotPassword` submits a forgotten password message for the supplied details. The subdomain is optional and you are able to just submit the username.
```javascript
{
	"username":"[user's cmap username]",
	"subdomain":"[cmap sub domain]"
}
```
