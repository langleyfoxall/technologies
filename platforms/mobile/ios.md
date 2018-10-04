# Langley Foxall iOS

iOS is a big part of the company and it's what got us started. The general rule of thumb for iOS development is to use Swift to write your apps as it's something that can easily be picked up by other members of the team & is the flagship language of Apple, more niche tasks or projects might require a dip into Objective-C or even C++ but this isn't the case for most projects.

Because Swift is a reletively new language and that iOS itself changes every year, ensuring we have an up to date guide full of good-to-knows & best practices is the key to ensuring we stay on top of iOS.

## Good to Knows
- If your app is designed for iPads, you will need to upload iPad Pro screenshots when submitting your app to the app store, this can cause issues because we often don't design our apps for the 12.9" display and because of this the constraints for the app's layout could not be compatible. Please ensure your app is compatible with the iPad Pro at a minimum.
- If your app is designed for iPhones, you will need to upload iPhone X screenshots when submitting your app to the app store, this shouldn't be too big of an issue because the iPhone X screen size is very similair to other devices in the iPhone family.
- Even if your app is built for iPad only, it still has to work on iPhone through the scaling feature used when running iPad apps on iPhone (look at apps like Snapchat & Instagram)

## Tools
- Managing certificates & provisioning profiles can be a huge pain, we use [Match](https://docs.fastlane.tools/actions/match/) to handle our certs, more is coming soon about this process!
- [Fastlane](https://fastlane.tools/) is used for new apps to automate common tasks involved in deploying your app, this includes building your app for TestFlight & the App Store, taking screenshots & automating the filling of app store metadata, greatly decreasing the overhead in terms of deploying iOS applications (More coming soon!)
