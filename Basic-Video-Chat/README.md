## Exploring the code

#### Connecting to the session

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
      if (error) {
         console.log(`There was an error connecting to the session: ${error}`);
      }
    });
```
The Session object dispatches a `streamDestroyed` event when the stream is destroyed. The application defines an event handler for this event:
```javascript
  session.on({
    streamDestroyed: (event) => {
      console.log(`Stream ${event.stream.name} ended because ${event.reason}`);
    }
  });
```

The Session object dispatches a `sessionConnected` event when the client connects to the session. The application defines an event handler for this event:
```javascript
  session.on({
    sessionConnected: (event) => {
      // publish
    }
  });
```
#### Publishing an audio video stream to the session

Upon successfully connecting to the OpenTok session (see the previous section), the application publishes an audio-video stream to the session. This is done inside the event handler for the `sessionConnected` event, since you should only publish to the session once you are connected to it.

The Publisher object is initialized as shown below. The `OT.initPublisher()` method takes two parameters:

The target DOM element or DOM element ID for placement of the publisher video

A set of publisher properties (optional)
```javascript
  var publisher = OT.initPublisher('publisher');
```
Once the Publisher object is initialized, we publish to the session using the `publish()` method of the Session object:
```javascript
  session.publish(publisher);
```
#### Subscribing to another client's audio-video stream

The Session object dispatches a `streamCreated` event when a new stream (other than your own) is created in a session. A stream is created when a client publishes to the session. The `streamCreated` event is also dispatched for each existing stream in the session when you first connect. This event is defined by the StreamEvent object, which has a `stream` property, representing stream that was created. The application adds an event listener for the streamCreated event and subscribes to all streams created in the session using the `session.subscribe()` method:
```javascript
    // Subscribe to a newly created stream
    session.on({
      streamCreated: (event) => {
        session.subscribe(event.stream, 'subscriber');
      }
    });
```
The `session.subscribe()` method takes four parameters:

The Stream object to which we are subscribing to
The target DOM element or DOM element ID (optional) for placement of the subscriber video
A set of properties (optional) that customize the appearance of the subscriber view
An optional completion handler.
