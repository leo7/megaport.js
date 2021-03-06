# Megaport JS Wrapper functions

## Initilising the wrapper

Staging Url 'https://api-staging.i.megaport.com'

```javascript
megaport = new mp('https://api-staging.i.megaport.com/v2/');
```

### Authenticating a User
```javascript
megaport.auth({
  username: 'wsmithers',
  password: 'password'
});

```
If you have a valid token you can pass that instead, { token: 'tokenstring' }

### Once Authenticated

######megaport.ready(callback)

Callback is run once a megaport wrapper has been authenticated.

```javascript
megaport.ready(
  function(credentials) {
    console.log(credentials);
  }
);
```

### On Authentication Failure

###### megaport.failauth(callback)

Callback is run once a megaport wrapper has failed an auth.

```javascript
megaport.failauth(function () {
  console.log('Authentication Failed');
});
```

## Menu Stats

Returning current authenicated profile account stats/notifications

```javascript
megaport.menuStats().then(
  function (menustats) {
    console.log(menustats);
  }
);
```

## Dashboard Info

Returning current authenicated profile dashboard information

```javascript
megaport.dashboard().then(
  function (menustats) {
    console.log(menustats);
  }
);
```

## User Profile

Returning current authenicated profile information

```javascript
megaport.profile().then(
  function (profileObj) {
    console.log(profileObj);
  }
);
```
Updating current authenicated profile information

```javascript
megaport.profile({
  firstName: "Pat",
}).then(
  function (response) {
    console.log(response);
  }
);
```

## Company Profile

Returning current users company

```javascript
megaport.company().then(
  function (profileObj) {
    console.log(profileObj);
  }
);
```
Updating current users company

```javascript
megaport.profile({
  www: 'http://www.megaport.com',
}).then(
  function (response) {
    console.log(response);
  }
);
```

## Markets

List of markets the current auth users company is registered in.

```javascript
megaport.market().then(
  function (m) {
    console.log(m);
  }
);
```

Market registration information by market id

```javascript
megaport.market(121).then(
 function (m) {
   console.log(m);
 }
);
```

Update market registration

```javascript
megaport.market(121, {
 "billingContactName": "112",
 "billingContactEmail": "112@asdasd.com",
 "billingContactPhone": "112",
 "address1": "112",
 "address2": "112",
 "postcode": "12",
 "country": "Australia",
 "city": "112",
 "state": "12",
 "web": "112"
}).then(
 function (m) {
   console.log(m);
 }
);
```

## Managing Services (products)

Return all services grouped by service groups you belong to.

```javascript
megaport.servicegroups().then(
  function (servicegroups) {
    console.log(servicegroups);
  }
);
```

Example Return

```json
[
  {
    "serviceGroupId": 122,
    "megaports": [
      {
        "productId": int,
        "associatedIxs": [...],
        "associatedVxcs": [...],
        "productName": "",
        "productType": "",
        "etc": ...
      }
    ]
  }
]
```

### Get Service Details by productId

megaport.product(productId)

works for both megaport and vxc and soon IX

```javascript
megaport.product(1).then(
  function (product) {
    console.log(product);
  }
);
```

### Update Service Details by productId

megaport.product(productId, obj);


```javascript
megaport.product(728, {
  name: "SG test port" //SG test port
}).then(
  function (product) {
    console.log(product);
  }
);
```

The object will have different params for product types (megaport/vxc/ix)

```json
megaport : {
  "name": String,
  "favourite": true/false
}
```

```json
vxc : {
  "name": String,
  "rateLimit": int,
  "aVlan": int,
  "bVlan": int
}
```

