---
gallery: true
categories:
- access control
---
## Email domain whitelist

This rule will only allow access to users with specific email domains.

```js
function (user, context, callback) {
    var whitelist = ['example.com', 'example.org']; //authorized domains
    var userHasAccess = whitelist.some(
      function (domain) {
        var emailSplit = user.email.split('@');
        return emailSplit[emailSplit.length - 1].toLowerCase() === domain;
      });

    if (!userHasAccess) {
      return callback(new UnauthorizedError('Access denied.'));
    }

    return callback(null, user, context);
}
```
