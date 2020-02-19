# Actually useful stuff
Well, here is actually  some useful information. Prerequisite is that you setup ReactNative like described in the [README.md](README.md).


# Local Development 

## Starting your simulator
Start the DEV server locally
```bash
npm run start 
``` 

Then open *another* Terminal tab and run your simulator of choice
```bash
npm run android 
npm run ios 
``` 

## Android 
[Read this pretty nice article](https://desmart.com/blog/3-things-to-know-about-android-as-react-native-developer) if your are not familiar with the android folder structure, app icons, signing, etc.

### Debug
Run 
```bash
npm run android-build-debug
```
and wait a little :) It builds your .apk in debug configuration ([needs a runnung DEV-Server](#local-development--starting-your-simulator)). It outputs the .apk in `android/app/build/outputs/apk/debug/`.

### Accessing device logs
If your physical device is connected via USB, you can access the logs in detail if you run 
```bash
adb logcad
```
on your computer. Useful for debugging in debug (lol) and release mode. 

### Release

#### Signing
To build a release version, just sign your apk beforehand. The needed `android/app/my-upload-key.keystore` file is excluded from Git and can be found in Azure in `Consolidate / Gless / Pipelines / Library` and then look for 'Secure files', download it and add it to the `android/app/` folder.

Now you need to provide the `storePassword` and `keyPassword` in the [app gradle file](android/app/build.gradle). Currently it's fetching it from the Keychain Access app on Mac, so the password isn't commited in plain text to our public repository.

**IF YOU ABSOLUTELY NEED** to build a release version locally, grab the signing password from the Azure pipeline (ConsolidateGless.Rocket.Chat.ReactNative) under 'Variables'. 

❗️**BUT BE SURE NOT TO COMMIT THE PASSWORD IN PLAIN TEXT!** ❗️

Okay, enough capsing around, lets head to [building your release APK locally](#building).

#### Building
If you have setup the Signing stuff, you can build your release .APK with
```bash
npm run android-build-release
```
It outputs the .apk in `android/app/build/outputs/apk/release/`.

## iOS
TODO:  
Gather relevant Information and place it right here.

# Continous Integration
Goal is to setup a CI so it uploads our release ready Android and iOS app's to our Gless server. I'll inform you when it's time ;) 



