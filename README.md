# ionic v2 Sample

Following the official guide: http://ionicframework.com/docs/v2/setup/installation/

## Guide Draft

### Registration

1. [Register the repository on bitrise.io](http://devcenter.bitrise.io/getting-started/create-your-first-app-on-bitrise/)
1. As [bitrise.io](https://www.bitrise.io) can't auto recognize Ionic projects right now, it's best to select the __Configure manually without project scanning__ option in the __Validation setup__ section during the setup
1. In the __Project build configuration__ section select __Other / Manual__ to make bitrise to generate a very minimal workflow - we'll replace this right away anyway.
1. In the __Stack selector:__
    * For Android builds: select the __Android & Docker, on Ubuntu 16.04__ option.
    * For iOS builds: select the right __Xcode x.x.x, on macOS__ option (the same Xcode version you use on your Mac).

### Prepare the Android project

1. Make sure that you don't .gitignore the `platforms/` directory (it's in `.gitignore` by default
if you generated the project with `ionic start ProjectName --v2`).
    * For Android this is actually optional, and you can distribute your app without this,
      but for iOS you'll have to do this.
    * Actually you'll have to remove additional `.gitignore` entries:
        * `platform/`
        * `www`
        * `plugins`
    * And the default `.gitignore` in the generated `platform/android` by default is incorrect,
      `/build` should be replaced with `build/`, and `.gradle` should be added.

### Prepare the iOS project

1. Make sure that you don't .gitignore the `platforms/` directory (it's in `.gitignore` by default
if you generated the project with `ionic start ProjectName --v2`).
1. Open the ios workspace (`platforms/ios/ProjectName.xcworkspace`)
1. Turn off the __Automatically manage signing__ option, then turn it back on
    * This is an issue with how Ionic generates the Xcode project code signing settings
1. Set the Team
1. In the top Device selector select __Generic iOS Device__
1. Do an Archive in Xcode
1. Fix any other issue you might have, until you can successfully generate an Archive from Xcode
1. Make sure the Scheme is shared!


## CI notes:

Either commit the `platforms/` directory into your repository (remove it from `.gitignore`),
or if you don't want to then you'll have to run `cordova platform add android`
on any new Mac/PC or in CI, as the `platforms/` directory is in the
default `.gitignore` which is generated by `ionic start ProjectName --v2`.


## Run locally

WIP

## ToDo:

* Build Cache
