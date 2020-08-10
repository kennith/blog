---
title: Playing with Laravel Sanctum
layout: post
categories: ['programming', 'laravel']
---
Laravel first party package Sanctum solves the token based API implementation. Sanctum makes it very easy making your API accessible for a Single Page Application (SPA) or Token-based application.

The official [documentation](https://laravel.com/docs/7.x/sanctum) explains very well about how it works. The following content is how I get comfortable with Sanctum.

I started off by following the [installation](https://laravel.com/docs/7.x/sanctum#installation) guide. 

Then, I started to experiment with Sanctum by using [Tinkerwell](https://tinkerwell.app/) to get the concept.

## Token-based authentication

1. Create a user with `factory(User::class)->create();`
2. Get the token of the user with `$user->createToken('test-token')->plainTextToken;`
3. Copy the `plainTextToken` to my clipboard for future use.

Since I have the [protected route](https://laravel.com/docs/7.x/sanctum#protecting-routes) setup. Let me test if I can access the site with the token in the terminal first.

```bash
curl http://127.0.0.1:8000/api/user \ 
    -H "Accept: application/json" \ 
    -H "Authorization: <plain-text-token>"
```

I see the `JSON` representation of the user in the output. It means it is working. Then I tried with a incorrect `plain-text-token`, it shows `{"message", "unauthenticated"}`. The token based system is working. 😎

Now, let's try this in PHP.

```php
$client = new GuzzleHttp\Client([
]);

$headers = [
    'Authorization' => 'Bearer '.$plainTextToken,
    'Accept' => 'application/json'
];

$response = $client->get('https://127.0.0.1:8000/api/user', [
    'headers' => $headers
]);
```

It works because I can again see the `json` representation of the user. API token based works. 

## SPA Authentication

Next, I work on the SPA authentication.

There are couple things needs to be taken care of. 

1. CORS
2. Setup stateful domains

### CORS

Thankfully, there is a package call [fruitcake/laravel-cors](https://packagist.org/packages/fruitcake/laravel-cors) that helps easing the CORS settings. 

```php
// Update config/cors.php to allow CORS
'paths' => ['api/*', 'sanctum/*']
'supports_credentials' => true,
```

```php
// Update stateful in
// config/sanctum.php or .env
// if your URL has specific port, you must include it.
'stateful' => explode(',', 'your-spa-domain:3000');
```

Then, I build a Vue application to test authenticating through a SPA. I use axios to handle the background fetch.

```javascript
import axios from "axios";

// enable withCredentials
// `withCredentials` indicates whether or not cross-site Access-Control 
// requests should be made using credentials
axios.defaults.withCredentials = true;
```

Then I created a button, a form with email and password in a single file component (SFC). The important line is getting the CSRF cookie to allow authentication with Laravel Sanctum.

```javascript
// create a login function
login() {
  axios.get("//localhost:8000/sanctum/csrf-cookie/").then(
    (response) => {
      axios
        .post("//127.0.0.1:8000/login", {
          email: this.email,
          password: this.password,
        })
        .then(
          (response) => {
            // handle response
          },
          function (error) {
            // handle error
          }
        );
    },
    function (error) {
      console.log(error.response.statusText);
    }
  );
}
```

Next, I created a method as a test to retrieve a protected route to see if I can get the protected data.

```javascript
getProtectedContent: {
      axios
        .get("//127.0.0.1:8000/api/api-user")
        .then((response) => console.log(response.data));
    }
```

I also created a logout button, just to clear out the session and see if I still could get the data from a protected route.

```javascript
logout() {
    axios.post("//127.0.0.1:8000/logout");
}
```

It works. 

Laravel Sanctum made creating a token based API or SPA authentication very easy to implement. Laravel just made another developer experience very happy. 😉
