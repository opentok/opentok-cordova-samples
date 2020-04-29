# OpenTok Cordova Samples

<img src="https://assets.tokbox.com/img/vonage/Vonage_VideoAPI_black.svg" height="48px" alt="Tokbox is now known as Vonage" />

### In this repo, you'll find the following sample applications:

- ##### Basic Video Chat
  - This sample application shows how to connect to an OpenTok session, publish a stream, and subscribe to a **single stream** in an iOS and Android application.
- ##### Signaling
  - This sample application shows how to connect to an OpenTok session and use signaling to create a basic iOS and Android **chat** application.
- ##### Multiparty-Video-Chat
  - This sample application shows how to connect to an OpenTok session, publish a stream, and subscribe to **multiple streams** in an iOS and Android application.

## Prerequisites:

1. Install [node.js](https://nodejs.org/)

2. Install Cordova: `npm install -g cordova`

3. Install and update [Xcode](https://developer.apple.com/xcode/) (you will need a Mac)

4. Install and update [Android Studio](https://developer.android.com/studio/index.html)

##### Note: Please make sure to run the commands in the same order as below

1.  Clone this repo

2.  In your terminal, change your directory to the root of the sample project you want to run.

3.  Run the command:

        npm install

    to install required node modules

4.  Run the command:

        cordova platform add ios

    to add iOS your project

5.  Run:

        cordova platform add android

    to add Android your project

## Configuring the application

Before running the application, you need to configure it to use the API key for your OpenTok project, along with an OpenTok session ID and token. For development purposes, you can obtain a session ID and token by navigating to your [TokBox account](https://tokbox.com/account/#/) page, selecting a project, and scrolling to the bottom of the page where it says `Generate Token`.

Open the `wwww/js/config.js` file in your project and set the `apiKey`, `sessionId`, and `token` values to the API key, session ID, and token you obtained from your TokBox account:

```
// Set Credentials
var apiKey = '';    // Add your API key.
var sessionId = ''; // Add the session ID.
var token = '';     // Add the token.
```

An OpenTok session connects different clients letting them share audio-video streams and send messages. Clients in the same session can include iOS, Android, and web browsers.

For testing, you can use a session ID and token generated at your TokBox account page. However, the final application should obtain these values using the OpenTok server SDKs. For more information, see the OpenTok [server SDK guides](https://tokbox.com/developer/sdks/server/) on session and token creation.

## Running the application

#### For Android

1. In the root directory of the sample project, run `cordova prepare android`.
2. Open Android Studio.
3. Click `Open an existing Android Studio project`.
4. Navigate to the `platforms/android` subdirectory of this project and select the `build.gradle` file.
5. Click `OK` to use the Gradle wrapper.
6. Click run.

##### Note: If you're using the simulator, you will see a black container for your publisher since the simulator doesn't have a camera.

#### For iOS

##### Camera & Microphone Permissions

Add the following to the project's `info.plist` file:

```
<key>NSCameraUsageDescription</key>
<string>The camera is required to publish video</string>
<key>NSMicrophoneUsageDescription</key>
<string>The microphone is required to publish audio</string>
```

Make sure to update the description of each permission request to what best fits your needs.

1. In the root directory of the sample project, run `cordova prepare ios`.
2. Open Xcode.
3. Click `Open another project...`
4. Navigate to the `platforms/ios` subdirectory of this project and select `OpenTokCordova.xcodeproj`.
5. Sign the project.
6. Run.

##### Note: If you're using the simulator, you will see a simulation for your publisher since the simulator doesn't have a camera.

## Development and Contributing

Interested in contributing? We :heart: pull requests! See the
[Contribution](CONTRIBUTING.md) guidelines.

## Getting Help

We love to hear from you so if you have questions, comments or find a bug in the project, let us know! You can either:

- Open an issue on this repository
- See <https://support.tokbox.com/> for support options
- Tweet at us! We're [@VonageDev](https://twitter.com/VonageDev) on Twitter
- Or [join the Vonage Developer Community Slack](https://developer.nexmo.com/community/slack)
