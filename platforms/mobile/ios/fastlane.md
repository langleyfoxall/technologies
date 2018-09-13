# Fastlane Match Deployment

Match is used to handle distributing iOS certificates for both development &amp; production, 
we handle this all ourselves & disable the ability for XCode to automatically handle certs.

The general concept behind Match is that production & development certificates are encrypted 
and then stored in a private git repo inside of our Github. Match handles pulling down the 
certificates, decrypting them, installing them in your Keychain & generating the respective 
provisioning profiles for either production deployment or development.

### Deploying Existing Native iOS Project (TestFlight & App Store)

#### Installing fastlane
On your initial setup you will need to install fastlane.

Install the latest Xcode command line tools:

xcode-select --install`

Install fastlane using

```
#Using RubyGems 
sudo gem install fastlane -NV
```


```
# Alternatively using Homebrew
brew cask install fastlane
```


#### Setting up fastlane

##### New Projects
Navigate your terminal to your project's directory and run

`fastlane init`

##### Existing Projects

Navigate to your project folder and run one the following depending on your usecase:

```
fastlane match appstore
```
```
fastlane match adhoc
```
```
fastlane match development
```
```
fastlane match enterprise
```

You will be asked for a repository link for our certificates: `langleyfoxall/apple-certs` and 
be asked to log into your Apple Account. You should ensure your account has the perms of App Manager. 
If you don't have these permissions you need to ask a more Senior member.

You will also be asked for a encryption key - which we can provide.

Following this successful setup, you will be able to upload to the App Store as normal.
