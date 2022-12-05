# Onelogin

Full support out of the box.
https://developers.onelogin.com/openid-connect

Edit config file App.js 


```js
const config = {
  issuer: 'https://{subdomain}.onelogin.com/oidc/2',
  clientId: '{clientId}',
  clientSecret: '{clientSecret}',
  redirectUrl: 'com.{yourReversedOneloginDomain}://callback',
  scopes: ['openid', 'profile']
};

// Log in to get an authentication token
const authState = await authorize(config);

// Refresh token
const refreshedState = await refresh(config, {
  refreshToken: authState.refreshToken,
});

// Revoke token
await revoke(config, {
  tokenToRevoke: refreshedState.refreshToken
});

// End session
await logout(config, {
  idToken: authState.idToken,
  postLogoutRedirectUrl: 'com.{yourReversedOktaDomain}:/logout'
});
```
