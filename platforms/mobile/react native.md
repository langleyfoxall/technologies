# Langley Foxall React Native

## Introduction
React Native is a mobile framework developed and maintained by Facebook that allows the developer to develop apps for Android and iOS simultaneously. React Native generates an Android Studio and Xcode that will automatically bundle a JavaScript file that will control a majority of the logic on the app on build.

An open source toolchain called [Expo](https://expo.io) has also been developed around React Native. Expo removes the requirement for prerequisite knowledge of Android and iOS development. Having only a JavaScript file that a react app can be built in, using the exp command line tools or Expo XDE. The JavaScript file is bundled and delivered over the air to the developers device or simulator running the Expo app. *Note: You are required to download the Expo app and create an account if you wish to develop this way.*

Both Pure React Native and Expo applications can be built mostly like a regular React Application and most Node Modules will be compatible. An exception to this is Routing and Navigation. See recommended packages.

## Which should I use? ##

Below is be listed the recommended prerequisite knowledge for each platform as well as the advantages and disadvantages. Use cases where Expo cannot be used will also be listed below.

## Expo ##
Expo only requires a Web Development skill set as all code written is in JavaScript. This allows basic applications to be built quickly and cross platform.

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

**See [Ejecting](#ejecting) for more information*

#### Over The Air Updates
Expo has support for OTAs, however there are numerous open issues regarding them on the Expo GitHub page and due to the fact that projects cannot be shared between multiple accounts the update requires access to the original developer's Expo account.

*It is not recommended to use OTAs at this time.*

#### Cases where Expo cannot be used
   * Push notifications with custom sounds and images 

#### Ejecting
Expo has the ability to 'Eject' a project to an Android Studio and Xcode project. This allows use of native modules such as Android and Apple pay and allows other native modules to be installed and linked to the project such as PDF Viewers as well as writing your own code.

***This is not recommended, ejecting requires knowledge of Android and iOS build tools***

If you want to use Native Code, chances are you will not be taking advantage of Expo. If you need features that Expo provides such as the Camera and the Gyroscope you will spend less time using Pure React Native and installing and linking those modules yourself than getting the detached Expo project working.