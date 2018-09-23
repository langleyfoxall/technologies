# React Native Quick Start

This is a Quick Start guide for Expo, see the React Native Quick Start Guide for Pure React Native.

## Dependencies ##

   * [Node](https://nodejs.org/en/download/)
   * [Expo Client](https://expo.io/tools)
   * [Xcode (Only for production build)](https://developer.apple.com/xcode/)
   * [Android Studio (Only for production build)](https://developer.android.com/studio/)

## Getting Started ##
You will either need to install the `create-react-native-app` package using npm, run the command `npm install -g create-react-native-app` or download the [Expo XDE](https://github.com/expo/xde). They both achieve the same thing, it is purely down to preference if you want to use the terminal.

You will also need Xcode and Android Studio configured if you will be building the app for production. See the respective guides for setting up [Xcode]() and [Android Studio]() if you do not have them set up already.
### Setting up the project
In order to develop using Expo you will need an account, you can create one [here](https://expo.io/signup).

If you are using the terminal, once the dependencies are installed and you have an account we can set up the project. To do this run the command `create-react-native-app {project name}`, this will create a new directory with the project name inside the directory the command was ran in. You will be given the option to create a blank project or one with example screens, you can choose either.

If you are using XDE login and click `Create a new project`. You can choose where you want the project and if you want a blank project or one with Navigation pre installed.

In order to run the build server if you are using the terminal navigate to the project in the terminal and run `npm start`.

If you are using XDE open the project in XDE and the build server will start.

No matter which method you used if you are logged in with the same account on the Expo client as when starting the build server, the app will appear on the client home screen.

### Writing Code
You can now build the React App in App.js as you would with any React Application.