# cordova-support-google-services<br>[![NPM version][npm-version]][npm-url] [![NPM downloads][npm-downloads]][npm-url]
> Cordova plugin to add google service support

As part of enabling Google APIs or Firebase services in your Android application you may have to add the [google-services plugin](https://developers.google.com/android/guides/google-services-plugin) to your `build.gradle` file.

## Installation

    cordova plugin add cordova-support-google-services --save

Read details about the gradle plugin at https://developers.google.com/android/guides/google-services-plugin.

You also need to put `google-services.json` on Android and `GoogleService-Info.plist` on iOS into appropriate folders. The best way is to use [`<resource-file>`](http://cordova.apache.org/docs/en/latest/config_ref/index.html#resource-file) tag. Put those files into the cordova project root folder and add new tags in your `config.xml` like below:

```xml
<platform name="android">
    <resource-file src="google-services.json" target="google-services.json" />
    ...
</platform>
<platform name="ios">
    <resource-file src="GoogleService-Info.plist" />
    ...
</platform>
```

## FAQ

#### Build Error: Failed to apply plugin [class 'com.google.gms.googleservices.GoogleServicesPlugin']
It looks like you have another dependency on a google play services lib with a generic verison `*`. You have to fix ALL dependency version(s) to be more more specific like `11.0.+`. In order to do that fix version strings for any play services library you have in `platforms/android/project.properties`.

#### Build Error: Could not generate a proxy class for class com.google.gms.googleservices.GoogleServicesTask.
Open `platform/android/build.gradle` and change version of the first `com.android.tools.build:gradle`:

    classpath 'com.android.tools.build:gradle:1.2.3+'

#### Duplicate resources: .../platforms/android/build/generated/res/google-services/armv7/debug/values/values.xml:string/google_api_key, .../platforms/android/res/values/strings.xml:string/google_api_key
Remove `google_api_key` and `google_app_id` from any existing xml file from `platform/android/res/` folder. Those values now come from an automatically generated `values.xml`.

[npm-url]: https://www.npmjs.com/package/cordova-support-google-services
[npm-version]: https://img.shields.io/npm/v/cordova-support-google-services.svg
[npm-downloads]: https://img.shields.io/npm/dt/cordova-support-google-services.svg
