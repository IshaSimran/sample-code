# Express Routes
Routes are the combination of an HTTP method and a URL endpoint. The endpoint refers to a resource, such as a file or JSON object, and the method tells us what we want to do with that resource.

See [Standard CRUD Methods](crud/server.js) to see examples of the methods we'll be covering in this course (mostly `GET` and `POST`).

## Express route methods
Also called route handlers, route methods have similar functionality to the `if` statement: if a request method matches a given method and url, it invokes the callback assigned to it.

This Express GET method:

```js
app.get('/',function(request,response){
  response.send('GET request: Read data');
});
```

Is functionally equivalent to this `if` statement:

```js
if (request.method === 'GET' && request.url === '/') {
  response.send('GET request: Read data')
}
```

There is no other functional difference between these handlers:
- `app.get()`
- `app.post()`
- `app.put()`
- `app.delete()`

## Activities
### Activity 1: Postman Practice
1. Copy the [Standard CRUD Methods](crud) example into a new project folder.
2. Launch the server and try to activate each endpoint handler using Postman.
    - Take note of the `Content-type`
3. Try changing the output inside `response.send()`. For example, try changing `GET request: Read data` to:
    - `<h1>GET request: Read Data</h1>`, or
    - `{method: 'GET', message: 'Read Data'}`

    How does this affect the response that Express sends? Hint: find the `Content-type` header in Postman or Firefox.
4. Add some static files using `express.static()` from yesterday.
    1. Copy a `public` directory from yesterday into your project folder.
    2. Add `express.static()` middleware _above_ the method handlers:
        
        ```js
        app.use(express.static(path.join(__dirname, 'public')));
        ```

    3. Create a new `app.get()` handler that matches a static file located in `public`, which one wins? 
    4. Try moving the middleware _after_ the method handlers. Is there any change in behaviour?

### Activity 2: Register form POST request 
1. Find your Register and Login assignment from CPNT 260.
2. Using the [subscribe example](post-requests/subscribe) as a starting point, create a new Express project and replace the contents of `public` with your assignment files.
3. To the Register `form`:
    1. Add an `action` attribute of `users`;
    2. Add a `method` attribute of `post`.
4. In `server.js`:
    1. Add `express.urlencoded()` middleware near the top of the file;
    2. Create a `app.post` handler for `/users`.
    3. Inside this handler, send a personalized response back to the user (but maybe don't send the password).
5. Submit the form to see the customized response.
6. Try changing the form `method` to `get`. What happens? Why is `post` better?