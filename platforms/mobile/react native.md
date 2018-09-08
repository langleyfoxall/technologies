# Langley Foxall React Native

## Introduction
React Native is a mobile framework developed and maintained by Facebook that allows the developer to develop apps for Android and iOS simultaneously. React Native generates an Android Studio and Xcode that will automatically bundle a JavaScript file that will control a majority of the logic and UI of the app on build.

An open source toolchain called [Expo](https://expo.io) has also been developed around React Native. Expo removes the requirement for prerequisite knowledge of Android and iOS development. Having only a JavaScript file that a ReactJS app can be built using the exp command line tools or the Expo XDE application. The JavaScript file is bundled and delivered over the air to the developers device or simulator running the Expo app. *Note: You are required to download the Expo app and create an account if you wish to develop this way.*

Both Pure React Native and Expo applications can be built mostly like a regular ReactJS Application and most Node Modules will be compatible. A notable exception to this is Routing and Navigation. [See recommended packages](#recommended packages).

## Which should I use? ##

Below is be listed the recommended prerequisite knowledge for each platform as well as the advantages and disadvantages. Use cases where Expo cannot be used will also be listed below.

## Expo ##
The Expo SDK only requires a Web Development skill set as all code written is in JavaScript. This allows basic applications to be built quickly, and cross platform.

To see what Expo is capable of and for the quick start guide [visit the Expo documentation](https://docs.expo.io/versions/v29.0.0/sdk).

#### Prerequisite knowledge

   * ReactJS
   * CSS

#### Advantages

   * Rapid development
   * Apps can be easily loaded and shared using the Expo app

#### Disadvantages

   * Some Native features *i.e. Apple and Android Pay* are not available* or only work on one platform
   * Apps are built using Expo's build servers
   * Push Notifications have to be sent through Expo's servers
   * The Expo app can be unreliable, especially on Android
   * Large app size, since all Expo apps contain all of the Expo APIs iOS apps are atleast 33mb and Android apps are at least 20mb.
   * Remote assets are hosted on GCP and AWS and require internet to download

**See [Detaching](#detaching) for more information*

#### Over The Air Updates
Expo has support for OTAs for apps that have been distributed to users through the app store, however there are numerous open issues regarding them on the Expo GitHub page and due to the fact that projects cannot be shared between multiple accounts the update requires access to the original developer's Expo account.

***It is not recommended to use OTAs at this time.***

#### Cases where Expo cannot be used
   * Push notifications with custom sounds and images 
   * Background code execution *(Location tracking etc...)*
   * Bluetooth
   * WebRTC

#### Detaching
Expo has the ability to 'Detach' project to an Android Studio and Xcode project. This allows use of native modules such as Android and Apple pay and allows other native modules to be installed and linked to the project such as PDF Viewers.On top of this you can write your own native code and link it to the JavaScript code.

***This is not recommended, ejecting requires knowledge of Android and iOS build tools***

If you want to use Native Code, chances are you will not be taking advantage of all of Expo's features and extra unneeded overhead will be added. If you need features that Expo provides such as the Camera and the Gyroscope you will spend less time using Pure React Native and installing and linking those modules yourself than getting the detached Expo project working.

## Pure React Native ##
Using pure React Native gives the developer more freedom than using Expo but requires knowledge of more programming languages and development environments.

#### Prerequisite knowledge

   * ReactJS
   * CSS
   * Xcode
   * Android Studio
   * Obj-C
   * Java
   * Swift *(Optional)*

#### Advantages

   * No reliance on third party servers
   * Lean apps, only native modules that are needed are added
   * Freedom with push notifications
   * All assets are in the app bundle
   * Native code can be written as well
   * Rapid cross platform development

#### Disadvantages

   * Knowledge around Mobile Development needed
   * Open source packages or custom development needed for features Expo offers out of the box *(Such as Camera access, however the open source package Expo's APIs are built on can usually be found)*
   * Installing libraries can be tricky when getting to the Android portion
   * Native code must be written seperetly in Java and Obj-C or Swift

#### Linking libraries

As is the case with Expo node modules can simply be installed via NPM. However pure React Native also allows you to link native libraries giving you access to APIs such as Apple and Android pay and the camera. However installing these packages is not always as easy as using `npm install`. Instructions to install these libraries can be specific to the library as a special configuration in Xcode or Android studio may be needed. The first component that needs to be installed is the node module so that the library can be interacted with by the JavaScript. This is done the standard way using `npm install`. Installing the native code for the iOS project is usually as easy with the process being automated with the command `react-native link`. However every library will have different instructions to get it running on Android, always requiring dependencies to be added to the Gradle file [(read about the Android Dependencies here TODO: Niles)]().

For more detailed information and instructions on manual linking on iOS [visit the React Native documentation on this topic](https://facebook.github.io/react-native/docs/linking-libraries-ios).

#### Native code

Native code can be written and bridged to the JavaScript code, the code must be written seperetly for Android and iOS. React Native supports Obj-C, Swift and Java officially but it is possible to bridge Kotlin code as well. Native functions can have callbacks, return promises or be void.

For more information see the React Native documentation for [iOS](https://facebook.github.io/react-native/docs/native-modules-ios) and [Android](https://facebook.github.io/react-native/docs/native-modules-android).

#### Deploying

For information on how to deploy React Native apps please see the [Android Deployment Guide (TODO)]() and the [iOS Deployment Guide (TODO)](). Since React Native generates a seperate Xcode and Android Studio Project the procedures are the same.

## Recommended Packages

| Package  | Information | Expo Compatible |
| ------------- | ------------- | ------------- |
| [React Navigation](https://reactnavigation.org/)  | React Navigation is the de-facto React Native Navigation Package, it is already included by default on Expo packages.  | :heavy_check_mark: |

## Blacklisted Packages

| Package  | Reason |
| ------------- | ------------- |
| [React Router Flux](https://github.com/aksonov/react-native-router-flux/)  | Breaking updates and long standing issues .  |

## Useful Links

   * [Awesome React Native components](http://www.awesome-react-native.com/#components)