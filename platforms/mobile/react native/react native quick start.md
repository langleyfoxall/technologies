# React Native Quick Start

This is a Quick Start guide for Pure React Native, see the Expo Quick Start Guide for Expo.

## Dependencies ##

   * [Node](https://nodejs.org/en/download/)
   * [Homebrew](https://brew.sh/)
   * [Xcode](https://developer.apple.com/xcode/)
   * [Android Studio](https://developer.android.com/studio/)

## Getting Started ##
You will need to install the `react-native-cli` package using npm, run the command `npm install -g react-native-cli`. You will also need to install `watchman` using Homebrew, run the command `brew install watchman`.

You will also need Xcode and Android Studio configured. See the respective guides for setting up [Xcode]() and [Android Studio]() if you do not have them set up already.
#### Setting up the project
Once the dependencies are installed we can set up the project. To do this run the command `react-native init {project name}`, this will create a new directory with the project name inside the directory the command was ran in. You will have the following files and directories inside this directory.

##### App.js
This is a place holder component that is used as an entry point for the ReactJs App when the JavaScript bundle is loaded into the app. This is usually where routing is managed with app screens being imported as components. 

##### Index.js
This is the root file of the ReactJs App. This usually should be ingnored and App.js should be used to build the app.

##### App.json
The app configuration is stored in this file. The two fields are `name` and `displayName`. The field `name` is the short name for the app that won't appear on the device. The `displayName` is the name that will appear below the app icon on the users home screen.

##### ios
The `ios` directory contains the Xcode project. Unless you are writing native code or running your app on an actual device you will not need to touch this until you come to build the app for production.

##### android
The `android` directory contains the Android Studio project. Unless you are writing native code you will not need to touch this until you come to build the app for production.

#### Running your app
##### iOS
In order to run the app on an iOS simulator simply run the command `react-native run-ios`.

Running the app on an actual iOS device is more complicated. Navigate to the `ios` directory and follow the guide for setting up Fastlane for the project. Once you have initialised Fastlane run the command `fastlane match development`. Now you can open the `.xcodeproj` file. This will open the xcode project. On the left you you will a file tree, click on the root object which will be the name of the project. You should see the screen pictured below. 

![No Certificate](images/xcode-no-cert.png "Xcode project with no Certificate")

Change the bundle identifier to `com.langleyfoxall.{project name}` and untick `Automatically manage signing`. You will now be given the option to select your own provisioning profile and certificates. For debug select the match development certificate and provisioning profile. You can now plug your device into the Mac and select the device in the top right and click the play button to load the app onto the device. While building the app the JavaScript bundle will be complied and bundled into the app. **There is no need to reinstall the app when changes are made to the JavaScript files. Shake the device when the app is open and enable live reloading, this will send the updates for the JavaScript OTA.** If you make any changes to native code you will have to install the app with the updated code.

##### Android
To run your app on your Android device or Emulator simply run the command `react-native run-android`.

You can also open the `android` directory in Android Studio and load the app onto the device using Android Studio. Clicking on the play button at the top right will open a list of connected devices with developer mode enabled. Select the device and click OK.

#### Writing code
The React app can now be written in `App.js`. This can be treated as any React app and with the exception of routing, almost any node module written for react can be used and installed using npm. For routing the defacto package is [React Navigation](https://github.com/react-navigation/react-navigation). If you wish to use a native API such as the camera a Native Module must be used. You can also write native code that interacts with the JavaScript.

#### Linking libraries

As is the case with Expo node modules can simply be installed via NPM. However pure React Native also allows you to link native libraries giving you access to APIs such as Apple and Android pay and the camera. However installing these packages is not always as easy as using `npm install`. Instructions to install these libraries can be specific to the library as a special configuration in Xcode or Android studio may be needed. The first component that needs to be installed is the node module so that the library can be interacted with by the JavaScript. This is done the standard way using `npm install`. Installing the native code for the iOS project is usually as easy with the process being automated with the command `react-native link`. However every library will have different instructions to get it running on Android, always requiring dependencies to be added to the Gradle file [(read about the Android Dependencies here TODO: Niles)]().

For more detailed information and instructions on manual linking on iOS [visit the React Native documentation on this topic](https://facebook.github.io/react-native/docs/linking-libraries-ios).

#### Native code

Native code can be written and bridged to the JavaScript code, the code must be written seperetly for Android and iOS. React Native supports Obj-C, Swift and Java officially but it is possible to bridge Kotlin code as well. Native functions can have callbacks, return promises or be void.

For more information see the React Native documentation for [iOS](https://facebook.github.io/react-native/docs/native-modules-ios) and [Android](https://facebook.github.io/react-native/docs/native-modules-android).

#### Deployment

#####iOS
For deployment for iOS fastlane should be used. The Xcode project generated when the project is created can be used as any Xcode project and the procedures outlined in the Fastlane documentation should be followed.

#####Android
To generate a development APK for distribution for testing select `Build` from the menu bar and click on `Build APK(s)`. Follow on screen instructions to build an unsigned APK. ***This build is not suitable for production distribution***.

To build an app for production the Android Studio project can be treated as a normal android studio project and you can follow the Android distribution guide.