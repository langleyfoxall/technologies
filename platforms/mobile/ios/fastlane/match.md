# Match
Match is a tool by Fastlane which implements a best practice guide for handling certifcates and provisioning profiles in a team.

## Resources
- [Original code signing guide](https://codesigning.guide/)
- [Match homepage](https://docs.fastlane.tools/actions/match/)

## Core Concepts
Match essentially stores encrypted certifcates inside of a Git repo that we control, when you want to setup your Mac to use our development and production certs, Match downloads them from the Git repo, decrypts them with the encryption key you provide and then installs them in your keychain. It will also handle generation of production and development provisoning profiles for your current project.

- Downloads certifcates from our Git repo
- Decrypts them with the encryption key you provide 
- Install the decrypted certifcates into your keychain
- Installs any provisoning profiles found per the bundle identifiers found in the project or entered during setup

## Getting Started
Getting your machine setup to be able to start developing or deploying apps is incredibly easy, just follow the steps below.

Repeat the below steps for the following commands based on your needs.
- `fastlane match appstore` for production certificates & profiles
- `fastlane match adhoc` for production certifcates & adhoc profiles
- `fastlane match development` for development certificates & profiles

- Ensure you have Fastlane installed globally (Look at [`core.md`](core.md) for more Fastlane details)
- You will be asked to enter the URL to the Git repo containing the certifcates, talk to your project manager to get the URL (Make sure this is the ssh url)
- Match will then attempt to clone the Git repo (you might hit some issues here, see the troubleshooting section at the bottom)
- After that you'll be promoted to enter the encryption key, ask your project manager for this key
- Fastlane will then ask you to enter your app bundle identifiers, enter the bundle identifiers (command seperated) of the project(s) you want to generate both development and production provisoning profiles for. Feel free to leave this blank if you just want to install the certificates.
- If everything goes well, all certifcates should be installed and the provisoning profiles required created or downloaded.

## Existing Apps
If you cast your eyes back to the previous section, you'll see that Fastlane will ask you to enter your bundle identifiers at some point, this can be inferred from your current project by setting up match to work with the project.

Before anything, please ensure you have created an App ID on the member center with a bundle identifier that matches the bundle identifier of your app.

If your project already has a `Matchfile` then Match has already been setup for your project so you only need to run one of the four commands in the previous section to download the correct provisioning profiles. 

If your project doesn't have a `Matchfile` then you need to init Match for your project, run the command `fastlane match init`, you can then proceed with the commands in the above section.

## Handling Expired Certs

Every year or so the distribution & development certificates will expire as they're valid for a year from the date of creation - as a result of this all provisioning profiles created with those certs will be invalidated.

This means that Match will no longer hold correct certs and profiles, you also won't be able to build the app for testing or push any builds to the appstore. Thankfully this isn't too big of an issue and can be easily resolved with a bit of manual work.

1. Delete all invalid or expired provisoning profiles from the Apple member center, the expired certificate will automatically be deleted by Apple.
3. Clone down the `apple-certs` repository from the company Github and delete the relevant provisioning profiles for the expired cert in the `profiles` folder (if only development expired only delete all development provisioning profiles etc).
4. Delete the invalid certificate(s) & key(s) from the `certs` folder.
5. Push the changes up to Github.
6. Re-run Match inside of your project directory to recreate the relevant certificate and provisioning profile (`fastlane match appstore` for distribution & `fastlane match development` for development)

That's it - you'll have to re-run match for any project that previously had it's provisioning profile managed by Match.

# Troubleshooting
- When running the command `fastlane match [option]` I get so far but then I get the following error `An app with that bundle ID needs to exist in order to create a provisioning profile for it` - This is because Match cannot create App IDs on the member center, you'll have to do that manually.
- I'm having an authention issue when attempting to clone the certificates repo. - Make sure you are authenticated to communicate with Github through ssh (try doing a `git pull` in one of your projects) also make sure you provide Fastlane with the `.git` ssh url when asked.

