# Fastlane

Fastlane is a tool that helps automate the deployment of iOS and Android apps. This file will talk exclusively about the iOS side of Fastlane and why it's awesome.

## Resources
- [Fastlane site](https://fastlane.tools/)
- [Getting Started](https://docs.fastlane.tools/getting-started/ios/setup/)

## Overview

Deploying iOS apps is a confusing and long process, from managing certificates to creating provisioning profiles to uploading your app to the app store, Fastlane knows this and attempts to make your life easier by automating everything to do with deployment.

At Langley Foxall we use Fastlane & it's various tools to do the following

- Manage our development & production certificates 
- Manage our provisoning profiles for both development and production (look at [`match.md`](match.md) for more information)
- Automatically take screenshots of the app for the app store.
- Upload metadata such as the app name and test credentials checked in the repo to the app store
- Automate the build and upload process, carried out through `lanes`
- Used occasionally in a CI environment to do all of this on a merge into the production branch

As you can see, it's incredibly powerful. All these things previously were done by hand and could take a few hours if this was the first time deploying, this has been cut down to mere minutes and all by running one command.

## Core Concepts

Fastlane is configured by multiple sets of `lanes`, these carry out a list of steps you define. This can be anything from just incrementing the build number to building the app, taking screenshots, uploading to the app store & submitting for review.

Lanes are stored in `fastlane/Fastfile` which is generated when you initialize Fastlane for your project by running `fastlane init` 

Below is an example `lane`:

```ruby
lane :release do
  capture_screenshots
  build_app
  upload_to_app_store       # Upload the screenshots and the binary to iTunes
  slack                     # Let your team-mates know the new version is live
end
```

Running the command `fastlane release` will run each of the above steps sequentially, that's it.

_this is a work in progress_