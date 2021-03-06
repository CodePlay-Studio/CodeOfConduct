# Guidelines for Android development in Java and Kotlin
###### Version 1.0.0
A collection of coding styles and practices for standardizing code formatting, naming, and organization across Android projects. These are not intended to be absolute. However, if a particular project does not follow the defined styles and practices, it should have another README.md underneath its own project folder (e.g. android/[`project name`]/README.md) that lists the changes and reasons.

## 1 Project Structure
Every Android projects should follow the standard [Android project guidelines](https://developer.android.com/studio/projects/index.html).

## 2 Application Configurations
This section describes how some of the essential characteristics of an app are reflected in the manifest and build configuration files.

### 2.1 App's Package Name and Application ID
The app's package name (also the project's base package name) MUST apply the company domain (codeplay.com.my) in reversed order and follow by the project/product name (e.g. my.com.codeplay/`name`).

Application ID is usually kept the same as the app's package name. However, there are times when a project/product has its own or client's domain, the Application ID is then set to this domain but the app's package name should remain the same. In short:

### 2.2 Minimum and Target API Level
minSdkVersion: set to __21__ when starting a new project/module unless otherwise specify in a requirement, as Material Design is introduced in Android 5.0 (API level 21) and some of its features are only available on this API level and above. Also, worth mentioning that in this API level and higher uses ART runtimes which natively supports loading multiple DEX files from APK files, therefore multidex support library is not needed if an app and its libraries references exceed 65,536 methods (64K reference limit).

May refer to [Android Distribution dashboard](https://developer.android.com/about/dashboards/) for a global statistics about the relative number of devices running a given version of the Android platform on Google Play store.

targetSdkVersion: Starting from August 1, 2018, Google Play store requires new app target at least Android 8.0 (API level 26) and apps that update from November 1, 2018.

Every new Android version introduces changes that bring significant security and performance improvements – and enhance the user experience of Android overall. Some of these changes only apply to apps that explicitly declare support through their targetSdkVersion manifest attribute (also known as the target API level).

Configuring an app to target a recent API level ensures that users can benefit from these improvements and allows it to take advantage of the platform's latest features, while still allowing it to run on older Android versions.

### 2.3 Version Code and Version Name

### 2.4 Dependencies
Prefer Maven dependency resolution over importing jar files where possible, and avoid the use of dynamic dependency versions, such as `2.1.+` as this may result in different and unstable builds or subtle, untracked differences in behavior between builds. The use of static versions such as `2.1.1` helps create a more stable, predictable and repeatable development environment.

## 3 File Naming

### 3.1 Class files
Class names should be written in [UpperCamelCase](http://en.wikipedia.org/wiki/CamelCase). For classes that extend an Android component, the name of the class should end with the name of the component:
* `SignUpActivity`
* `SignUpFragment`
* `DataSyncService`
* `MediaProvider`

### 3.2 Resource files
Resources file names are written in __lowercase__ and each word is separated with an __underscore__ (no space is allowed) e.g. `ic_launcher`, `ic_settings_black_48dp`.

#### 3.2.1 Layout files
Layout file names should be prefixed with the name of the component and followed by the name to describe the class. Example:

| Component        | Class Name             | Layout Name            |
| ---------------- | ---------------------- | ---------------------- |
| Activity         | `SignUpActivity`       | `activity_sign_up.xml` |
| Fragment         | `SignUpFragment`       | `fragment_sign_up.xml` |
| Dialog           | `SignUpDialog`         | `dialog_sign_up.xml`   |
| AdapterView item | `DataViewHolder`       | `item_data.xml`        |

### 4 Code Guidelines

#### 4.1 Java language rules

#### 4.2 Kotlin language rules

#### 4.3 XML style rules
Prefer self closing tags if there are no child element within a tag. Example:

```xml
<TextView
	  android:id="@+id/TextView"
	  android:layout_width="wrap_content"
	  android:layout_height="wrap_content" />
```

**Not**
```xml
<TextView
    android:id="@+id/TextView"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content" >
</TextView>
```
