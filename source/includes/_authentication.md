# Authentication #

The Pricemoov API uses API keys to authenticate requests.

## Generating authentication token ##

Your authentication token carry many privileges, so be sure to keep them secure! Do not share your key in publicly accessible areas such as GitHub, client-side code, and so forth.

All API requests must be made over HTTPS. Calls made over plain HTTP will fail. API requests without authentication will also fail. See the error section.

Default lifetime of JWT tokens is 24h

### HTTP Request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-post">POST</i>
		<h6>/login</h6>
	</div>
</div>


```shell
# Generate a token
curl --location --request POST 'https:/api.pricemoov.com/login' \
--header 'Content-Type: application/json' \
--data-raw '{"email":"example@company.com","password":"XXXYYYYZZZ"}'
```

```python
import requests

url = 'https://api.pricemoov.com/login'
headers = {'Content-Type': 'application/json'}
payload = {"email": "example@company.com", "password": "XXXYYYYZZZ"}

response = requests.post(url, headers=headers, json=payload)
token = response.json()['token']
```

```javascript
fetch('https://api.pricemoov.com/login', {
  method: 'POST',
  headers: {'Content-Type': 'application/json'},
  body: JSON.stringify({email: 'example@company.com', password: 'XXXYYYYZZZ'})
})
.then(response => response.json())
.then(data => {
  const token = data.token;
  // do something with the token
})
.catch(error => console.error(error));
```


```php
$url = 'https://api.pricemoov.com/login';
$headers = array('Content-Type: application/json');
$data = array('email' => 'example@company.com', 'password' => 'XXXYYYYZZZ');

$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, $url);
curl_setopt($ch, CURLOPT_POST, true);
curl_setopt($ch, CURLOPT_HTTPHEADER, $headers);
curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode($data));
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);

$response = curl_exec($ch);
curl_close($ch);

$token = json_decode($response, true)['token'];

```




## Using the token to make API requests ##

Now that you have generated the token, you can use it to make API requests as follow.

<!-- TODO: Example -->

```python
requests.get(
    "http://api.pricemoov.com/product_catalog", 
    headers={
        "Authorization": "jwt eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9l"
    }
)

```
