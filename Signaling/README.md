## Exploring the code

Connecting to the session

The `OT.initSession()` method initialized an OpenTok Session object, using the session ID and token (see [Configuring the application](https://github.com/opentok/opentok-cordova-samples#configuring-the-application)):
```javascript
  // Initialize Session Object
  var session = OT.initSession(apiKey, sessionId);
```
The `OT.initSession()` method takes two parameters -- the OpenTok API key and the session ID. It initializes and returns an OpenTok Session object.

The `connect()` method of the Session object connects the client application to the OpenTok session. You must connect before sending or receiving audio-video streams in the session (or before interacting with the session in any way). The `connect()` method takes two parameters -- a token and an optional completion handler function:
```javascript
    // Connect to the Session
    session.connect(token, (error) => {
      if (!error) {
        // set event listener
        setEventListener();
      }
    });
```
The Session object dispatches a `signal:type` event when the signal is sent. The application defines an event handler for this event:
```javascript
  session.on({
    'signal:chat': function(event) {
      
      // Create the message element if the chat is from someone else
    }
  });
```

The `setEventListener()` function is where we listen for the `click` event to get the value of the the message.

The `sendSignal()` function is where we send use `session.signal()` to send the chat message.

The `createMessageElement()` function is where we add the chat message to the DOM.
