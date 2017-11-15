# OpenTok Cordova Basic Video Chat

### In this repo, you'll find the following sample applications:

* ##### Basic Video Chat
  * This sample application shows how to connect to an OpenTok session, publish a stream, and subscribe to a **single stream** in an iOS and Android application.
* ##### Signaling
  * This sample application shows how to connect to an OpenTok session and use signaling to create a basic iOS and Android **chat** application.
* ##### Multiparty-Video-Chat
  * This sample application shows how to connect to an OpenTok session, publish a stream, and subscribe to **multiple streams** in an iOS and Android application.

## Prerequisites:

1. Node.js

2. Cordova: `sudo npm install -g cordova`

3. Xcode

4. Android Studio

##### Note: Please make sure to run the commands in the same order as below

1. Clone this repo

2. In your terminal run: `$ cordova platform add ios` // This will add iOS your project

3. In your terminal run: `$ cordova platform add android` // This will add Android your project

4. Next run: `$ npm install`

## Configuring the application

Before running the application, you need to configure it to use the API key for your OpenTok project, along with an OpenTok session ID and token. For test purposes, you can get a test session ID and token for your project at your TokBox account page.

Open the wwww/js/index.js file and set the `apiKey`, `sessionId`, and `token` values to the API key, session ID, and token:
```
    // Set Credentials
    var apiKey = '';    // Add your API key.
    var sessionId = ''; // Add the session ID.
    var token = '';     // Add the token.
```
An OpenTok session connects different clients letting them share audio-video streams and send messages. Clients in the same session can include iOS, Android, and web browsers.

For testing, you can use a session ID and token generated at your TokBox account page. However, the final application should obtain these values using the OpenTok server SDKs. For more information, see the OpenTok developer guides on session creation and token creation.

## Running the application

#### For Android

1. In the root directory of the sample project, run `cordova prepare android`.
2. Open Android Studio.
3. Click `Open an existing Android Studio project`.
4. Navigate to the `platforms/android` subdirectory of this project and select the `build.gradle` file.
5. Click run.

##### Note: If you're using the simulator, you will see a black container for your publisher since the simulator doesn't have a camera.

#### For iOS

##### Camera & Microphone Permissions

Add the following to the `OpenTokCordova.xcodeproj` project's `info.plist` file:
```
<key>NSCameraUsageDescription</key>
<string>The camera is required to publish video</string>
<key>NSMicrophoneUsageDescription</key>
<string>The microphone is required to publish audio</string>
Make sure to update the description of each permission request to what best fits your needs.
```
1. In the root directory of the sample project, run `cordova prepare ios`.
2. Open Xcode.
3. Click `Open another project...`
4. Navigate to the `platforms/ios` subdirectory of this project and select `OpenTokCordova.xcodeproj`.
5. Sign the project.
6. Run.

##### Note: If you're using the simulator, you will see a simulation for your publisher since the simulator doesn't have a camera.
