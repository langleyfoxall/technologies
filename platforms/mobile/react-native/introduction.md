# Langley Foxall React Native



*   [Introduction](#introduction)
*   [Which should I use?](#whichshouldiuse)
*   [Expo](#expo)
    *   [Prerequisite knowledge](#Prerequisiteknowledge)
    *   [Advantages](#Advantages)
    *   [Disadvantages](#Disadvantages)
    *   [Over The Air Updates](#OverTheAirUpdates)
    *   [Cases where Expo cannot be used](#CaseswhereExpocannotbeused)
    *   [Detaching](#detaching)
*   [Pure React Native](#purereactnative)
    *   [Prerequisite knowledge](#Prerequisiteknowledge)
    *   [Advantages](#Advantages)
    *   [Disadvantages](#Disadvantages)
    *   [Linking Libraries](#linkinglibraries)
    *   [Native Code](#nativecode)
    *   [Deploying](#deploying)
*   [Code Standards](#codestandards)
*   [Recommended Packages](#recommendedpackages)
*   [Blacklisted Packages](#blacklistedpackages)
*   [Useful Links](#usefullinks)

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
   * NativeCSS, which is inspired by CSS

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
   * Push notifications
   * Background code execution *(Location tracking etc...)*
   * Bluetooth
   * WebRTC
   * Video playback

#### Detaching
This refers to detatching an existing Expo app to add custom features. Detatching a project to build it can be used to circumvent using Expo's build servers, which is recommended.

Expo has the ability to 'Detach' project to an Android Studio and Xcode project. This allows use of native modules such as Android and Apple pay and allows other native modules to be installed and linked to the project such as PDF Viewers.On top of this you can write your own native code and link it to the JavaScript code.

***This is not recommended, detatching requires knowledge of Android and iOS build tools***

If you want to use Native Code, chances are you will not be taking advantage of all of Expo's features and extra unneeded overhead will be added. If you need features that Expo provides such as the Camera and the Gyroscope you will spend less time using Pure React Native and installing and linking those modules yourself than getting the detached Expo project working.

## Pure React Native ##
Using pure React Native gives the developer more freedom than using Expo but requires knowledge of more programming languages and development environments.

#### Prerequisite knowledge

   * ReactJS
   * NativeCSS, which is inspired by CSS
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

#### Quick Start
See the quickstart guide for information on setting up a project, writing code, installing modules and deployment.

## Code Standards

To see the code standards please refer to the documentation for the respective languages.

   * [ReactJS]()
   * [Obj-C]()
   * [Swift]()
   * [Java]()

## Recommended Packages

| Package  | Information | Expo Compatible |
| ------------- | ------------- | :-------------: |
| [React Navigation](https://reactnavigation.org/)  | React Navigation is the de-facto React Native Navigation Package, already included by default on Expo packages.  | :heavy_check_mark: |

## Blacklisted Packages

| Package  | Reason |
| ------------- | ------------- |
| [React Router Flux](https://github.com/aksonov/react-native-router-flux/)  | Breaking updates and long standing issues .  |

## Useful Links

   * [Awesome React Native components](http://www.awesome-react-native.com/#components)