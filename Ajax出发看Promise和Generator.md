```js
var request = new XMLHttpRequest();

request.onreadystatechange = function () {
    if (request.readyState === 4) {
        if (request.status === 200) {
            return success(request.responseText);
        } else {
            return fail(request.status);
        }
    }
}

request.open('GET', '/api/categories');
request.send();
```

