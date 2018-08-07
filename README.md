This repo is a partial rewrite of the [get started guide](https://socket.io/get-started/chat/) in  which you can find in the socket.io homepage.

In the code examples, the socket.io team is using jQuery. While that might simplify the code for others, it may make it hard for other users to understand what's happening. In my opinion, it is helpful to have the examples in plain Javascript.

Below you can see the code examples that socket.io provides, and an identical example in ES6 Javascript.

 -
 ```javascript 
io.on('connection', function(socket){  
   console.log('a user connected');  
   socket.on('disconnect', function(){  
     console.log('user disconnected');  
 });  
});
```
```javascript
io.on('connection', (socket) => {
  console.log('a user connected'); 
  socket.on('disconnect', () => {
    console.log('user disconnected');
  });
});
```
-
```javascript
<script src="/socket.io/socket.io.js"></script>  
<script src="https://code.jquery.com/jquery-1.11.1.js"></script>  
<script>  
   $(function () {  
     var socket = io();  
     $('form').submit(function(){  
       socket.emit('chat message', $('#m').val());  
       $('#m').val('');  
        return false;  
     });  
   });  
</script>
```
```javascript
<script  src="/socket.io/socket.io.js"></script>

<script>
  const socket = io();
  const form = document.getElementById('form');
  const m = document.getElementById('m');
  const messages = document.getElementById('messages');

  form.addEventListener('submit', (e) => {
    e.preventDefault(); //Prevent page reload after submit
    socket.emit('chat message', m.value);
    m.value = '';
    return  false;
  });
</script>
```
-
```javascript
io.on('connection', function(socket){  
   socket.on('chat message', function(msg){  
   console.log('message: ' + msg);  
  });  
});
```
```javascript
io.on('connection', (socket) => {
  socket.on('chat message', (msg) => {
    console.log('message: ' + msg);
  });
});
```
-
```javascript
io.on('connection', function(socket){
  socket.on('chat message', function(msg){
    io.emit('chat message', msg);
  });
});
```
```javascript
io.on('connection', (socket) => {
  socket.on('chat message', (msg) => {
    io.emit('chat message', msg);
  });
});
```

**Alternatively**, if you just want to run the app, follow these instructions:

 1. Clone the repo
   ```$ git clone https://github.com/awareness481/Socket.io-Get-Started-Guide-in-ES6.git```
 2. Move to the right folder
   ```$ cd Socket.io-Get-Started-Guide-in-ES6```
 3. Run app.js
  ```$ node app.js ```
4. Visit localhost:3000
