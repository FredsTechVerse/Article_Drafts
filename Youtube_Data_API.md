## YouTube Data API and Client Libraries

- The YouTube Data API lets developers programmatically interact with YouTube features like uploading, reading, and deleting videos. 
- Google provides client libraries that simplify API interactions, handling authentication and API calls for various programming languages.


`oAuth2Client.on("tokens", () => {})` is an event listener triggered when new tokens are obtained or existing tokens are refreshed. It can be used to store refresh tokens securely in a database or whatever we want. The callback is really at our disposal

`oAuth2Client.setCredentials(tokens)` - This method sets OAuth 2.0 credentials (access tokens, refresh tokens, etc.) on the client instance. Automatically includes credentials in API requests, simplifying authentication. The client checks token validity and refreshes the access token as needed.

 
```js
  //TOKEN BODY STRUCTURE TO BE EXPECTED
 {
       "access_token": "your-access-token",
       "refresh_token": "your-refresh-token",
        "scope": "scopes-requested",
       "token_type": "Bearer",
        "expiry_date": UNIX_TIMESTAMP
  }
```
` oAuth2Client.refreshToken()` method is used to exchange a refresh token for a new set of access and refresh tokens. 

## Granting Offline Access

Granting offline access means giving a third-party app permission to access user resources even when the user isn't actively using the app. When a user grants offline access, an app receives a refresh token, allowing it to obtain new access tokens without user interaction. This maintains access to resources while respecting user control and security.

- Access tokens are short-lived and automatically refreshed.
- Refresh tokens are valid for 6 months and are vital for long-term access.
- We capture and store refresh tokens securely for future use.

In summary, the YouTube Data API, OAuth 2.0, and granting offline access provide a secure and efficient way for applications to interact with user resources, ensuring continuous access and user control over their data.

### PROCESS SUMMARY

There are three major aspects to it:-

- We need a header, body/metadata and then we wait for the response which contains the location (presignedUrl) where we can upload the video file.
- While requesting for the presigned url,we only pass the access token and the content type which is application/json to the header.
- With the aid of a put request , presigned url and the body armed with snippet and status which are objects containing the title and description of the video , we can upload the video file to youtube.
- The keys , function and additional parameters are separated just as with the axios request methods.....

