# Adding Cookies to Requests

Adding cookies to a request can sometimes me necessary, for example when authenticating using cookies. In postman, this can be done by navigating to a request and clicking the **"Cookies"** button below the "Send". 

Clicking this button will open a dialog, where domains can be added. Adding a domain will then allow you to add the individual cookies that you need. 

Postman supports the following attributes:
- **cookieName, cookieValue**
- **Domain**
- **Path**
- **HttpOnly**
- **Secure**
- **Expires**

```
<cookieName>=<cookieValue>; path=/; domain=.domain.com; HttpOnly; Secure; Expires=Tue, 19 Jan 2038 03:14:07 GMT;
```

[source](https://learning.postman.com/docs/sending-requests/cookies/)