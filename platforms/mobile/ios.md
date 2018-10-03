# Langley Foxall iOS

iOS is a big part of the company and it's what got us started. We write our iOS apps in purely Swift.

Because Swift is a reletively new language and that iOS itself changes every year, ensuring we have an up to date guide full of good-to-knows & best practices is the key to ensuring we stay on top of iOS.

## Good to Knows
- To submit your app to the app store you have to upload iPad Pro screenshots, this can cause issues because we often don't design our apps for the 12.9" display and because of this the constraints for the app's layout could not be compatible. Please ensure your app is compatible with the iPad Pro at a minimum.
- Even if your app is built for iPad only, it still has to work on iPhone through the scaling feature used when running iPad apps on iPhone (look at apps like Snapchat & Instagram)

## Tools
- Managing certificates & provisioning profiles can be a huge pain, we use [Match](https://docs.fastlane.tools/actions/match/) to handle our certs, more is coming soon about this process!
- [Fastlane](https://fastlane.tools/) is used for new apps to automate common tasks involved in deploying your app, this includes building your app for TestFlight & the App Store, taking screenshots & automating the filling of app store metadata, greatly decreasing the overhead in terms of deploying iOS applications (More coming soon!)
