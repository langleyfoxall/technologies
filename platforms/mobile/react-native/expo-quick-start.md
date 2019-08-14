# React Native Quick Start

This is a Quick Start guide for Expo, see the React Native Quick Start Guide for Pure React Native.

## Dependencies ##

   * [Node](https://nodejs.org/en/download/)
   * [Expo Client](https://expo.io/tools)
   * [Xcode (Only for production build)](https://developer.apple.com/xcode/)
   * [Android Studio (Only for production build)](https://developer.android.com/studio/)

## Getting Started ##
In order to get started with Expo run the command `npm install -g expo-cli` to globally install the Expo CLI.

You will also need Xcode and Android Studio configured if you will be building the app for production. See the respective guides for setting up [Xcode]() and [Android Studio]() if you do not have them set up already.
### Setting up the project
In order to develop using Expo it will help to have an account, you can create one [here](https://expo.io/signup).

Navigate to the directory that you wish to start your project in and run the command `expo init`. You will be presented with 3 options: Blank, Tabs and Bare Minimum. Blank and Tabs are `Managed Workflow` templates which means that they can be written purely in JavaScript without ever need to use native development environments. Managed Workflow projects can later be `detached` if you want to use native development environments and write native code. Selecting `Bare Minimum` will give you an empty project that only has `expo`, `react`, and `react-native` as dependencies. Selecting `Tabs` will create a project that with the dependencies previously mentioned with the addition of `react-navigation` and some sample code demonstrating a simple app with a tab bar. This is a good place to start if you are new to `react-navigation`.

You can now run `expo start` to start the bundler. A new browser tab will open, this webpage is a control panel that allows you to control your local development server. In the center you will see the log output from your app, on the left you can select which device you will see logs from. You can also see logs from the bundler which will contain any errors from bundling. Above the QR code on the left you will see the options `Tunnel`, `LAN` and `Local`. Tunnel will allow you to access your app on networks outside your own using a fork of `ngrok`, a link to your tunnel can be seen below the buttons when this option is selected.  Local will allow you to access your app on your local network, when selected you can see your local IP and the port the bundler is running on below the buttons. Local will run the server on localhost. This is the fastest option and can be used by sharing the network from your computer to your phone or using an emulator, by default if you connect an iPhone to a Mac the network will be shared and you will be able to use this.

On an Android device you can scan the QR code with the Expo client to load the app. Due to Apple's restrictions this isn't possible on iOS so you must send yourself the link. If you're logged into Expo on your computer and phone any app you have building will show on the `Projects` tab on the Expo app. You can log in with the cli by running `expo login` and entering your credentials.

### Writing Code
You can now build the React App in App.js as you would with any React Application.
