# Commands Used

# Appium + WebDriver.IO Demo Framework - Android & IOS Example

This project has been created to demonstrate how a QA Engineer can perform Mobile Testing using Appium + WebDriver.IO
More commands and insights about the integration at [WebDriverIO Appium docs](https://webdriver.io/docs/api/appium/)

- - - 
## General System Requirements

#### Node JS

We need node js to download Appium beta version & drivers easily.
* Download[ Node Js](https://linktodocumentation) depending on your operating system.
#### Java JDK & JAVA_HOME variable

* [Open JDK](https://openjdk.org)
* [JAVA_HOME setup for Windows](https://confluence.atlassian.com/doc/setting-the-java_home-variable-in-windows-8895.html)
* [JAVA_HOME setup for Mac](https://mkyong.com/java/how-to-set-java_home-environment-variable-on-mac-os-x/)

I Tested the following steps on MAC OS Monterrey:

* Installed Adopted [Open JDK with Homebrew](https://formulae.brew.sh/cask/adoptopenjdk)
* To return where was the SDK installed I used the command:
```bash
    /usr/libexec/java_home
```
* If you want to check the java version:
```bash
    /usr/libexec/java_home -V
```
* Open the zshenv file to insert the JAVA_HOME variable (i):
```bash
    vim ~/.zshenv
```
* Enter the environment variable and save the vim session (:wq!):
```bash
    export JAVA_HOME=$(/usr/libexec/java_home)
```
* Source and apply the changes in the system:
```bash
    source ~/.zshenv
```
* You can check if it was set correctly running the command:
```bash
    echo $JAVA_HOME
```
* It should return something like: 
```bash
    /Library/Java/JavaVirtualMachines/adoptopenjdk-16.jdk/Contents/Home
```

## Android Setup
#### Android Studio & ANDROID_HOME variable

* [Android Studio](https://developer.android.com/studio?hl=es-419&gclsrc=aw.ds&gclid=Cj0KCQjwyOuYBhCGARIsAIdGQRNrDv20QvoOy_-I5E1LoZdOLu3nvhlwX_7EjPeHcE1kGQNNcIVOme0aAqckEALw_wcB)
* [ANDROID_HOME setup for Windows](https://www.testingdocs.com/setting-android_home-environment-variable-on-windows/)
* [ANDROID_HOME setup for Mac](https://stackoverflow.com/questions/19986214/setting-android-home-enviromental-variable-on-mac-os-x)

Tested the following steps on MAC OS Monterrey:
* Android studio on Mac can be located at:
```bash
    * cd /Users/[USER]/Library/Android/sdk
```
* We need to add a reference to a couple of folders inside of that SDK
   * Tools & Platform Tools
* Open the zshenv file to insert the ANDROID_HOME variable (i):
```bash
    vim ~/.zshenv
```
* Enter the environment variables and save the vim session (:wq!):
```bash
    export ANDROID_HOME="/Users/[USER]/Library/Android/sdk"
    export PATH=$ANDROID_HOME/platform-tools:$PATH
    export PATH=$ANDROID_HOME/tools:$PATH
```
* Source and apply the changes in the system:
```bash
    source ~/.zshenv
```
* You can check if it was set correctly running the command:
```bash
    echo $ANDROID_HOME
```
* It should return something like: 
```bash
    /Users/[USER]/Library/Android/sdk
```
* With this configured you can access the command [Android Debug Bridge](https://developer.android.com/studio/command-line/adb)
```bash
    adb
```
- - -

## IOS Setup

1. Install XCode from the MacOs App Store
2. Install [XCode Command line tools](https://www.freecodecamp.org/news/install-xcode-command-line-tools/)
```bash
    xcode-select --install
```
- Make sure it is installed correctly using the following command:
```bash
    xcode-select -p
```
- It should return something like(may defer from your OS version):
```bash
    /Applications/Xcode.app/Contents/Developer
```
3. Install Carthage(It is a simple dependency manager for macOS and iOS, created by a group of developers from GitHub).
```bash
    brew install carthage
```

---

#### Download Appium Inspector
In order to find the correct locators to map elements, you will need to have this tool installed in your computer.

* [Appium Inspector Releases](https://github.com/appium/appium/blob/1.x/docs/en/writing-running-appium/web/chromedriver.md)

For this project you can use the following configuration:

| Server Key | Server Value |
| ------------- | ------------- |
| Remote Host | 0.0.0.0 |
| Remote Port | 4724 |
| Remote Path | / |

Android Desired Capabilities(Example)
| Desired Capability Key  | Desired Capability Value |
| ------------- | ------------- |
| platformName  | Android |
| platformVersion  | [OS VERSION / IMAGE]  |
| deviceName | [EMULATED_DEVICE_NAME] | 
| app | /[PROJECT_PATH]/[APP_NAME].apk |
| appium:automationName | UIAutomator2 |

IOS Desired Capabilities(Emulator - App)
| Desired Capability Key  | Desired Capability Value |
| ------------- | ------------- |
| platformName  | IOS |
| platformVersion  | [OS VERSION / IMAGE]  |
| deviceName | [EMULATED_DEVICE_NAME] | 
| app | /[PROJECT_PATH]/[APP_NAME].app |
| appium:automationName | XCUItest |

#### Install Apium 
Appium is an open source test automation framework for use with native, hybrid and mobile web apps. 
It drives iOS, Android, and Windows apps using the WebDriver protocol.

* Install [Appium](https://appium.io) from the official documentation 
* Install [Appium 2](https://appiumpro.com/editions/122-installing-appium-20-and-the-driver-and-plugins-cli) by Node JS(Beta):
```bash
    npm install -g appium@next
```
Check the appium version using
```bash
    appium -v
```

#### Appium Doctor
To check if your OS meets the appium requirements, install this node package.
* [Appium Doctor Package](https://github.com/appium/appium-doctor)
Install it using the command 
```bash 
npm install appium-doctor -g
```
And then use the library:
```bash 
appium-doctor
```

#### Appium drivers
If you want Appium to work correctly, you need to download and have the android/ios driver in your system.
Run the commands:
```bash 
appium driver install xcuitest
appium driver install uiautomator2
```
Check the installed drivers using
```bash 
appium driver list
```

#### Sample applications
Sample Application that you can use:

[SauceDemo Hybrid App - React Native)](https://github.com/saucelabs/my-demo-app-rn) - (Framework is configured to use this one)

[Sauce Labs Native Sample Application](https://github.com/saucelabs/sample-app-mobile)

[WebdriverIO Demo App for iOS and Android](https://github.com/webdriverio/native-demo-app)

***Important Note:***
For IOS you are going to need an app build to run it in simulators, but an .IPA file to run it in real devices. It required additonal desired capabilities, and you can see which ones in the next article: [Appium XCUITest Driver Real Device Setup
](https://appium.io/docs/en/drivers/ios-xcuitest-real-devices/)

## Setup WebDriverIO

1- Run the command to create the package.json & continue with the installation process
```bash
    npm init wdio .
```
2- Using the WDIO Configuration Helper select the options you want to select. In my case I decided to use:
* local - for e2e testing of web and mobile applications   
* On my local machine
* no appium setup
* Mocha
* No compiler
* Spect Location: Default
* Do you want WebDriverIO to generate some test files?: No
* Reporter: Spec
* No Plugin 
* Service: Appium
* Base URL: Default
* NPM Install: Yes

3- Add your tests at 
```bash
'./[yourProject]/specs/**/*.js'
```
This should be done in your wdio.conf.js file as following in our case
```
    specs: [
        // ToDo: define location for spec files here
        './test/specs/**/*.js'
    ],
```

4 - Setting up capabilities:

* Set up the capabilities for Android(Emulator sample)
```bash
    capabilities: [{
        platformName: 'Android',
        'appium:automationName': 'UiAutomator2',
        'appium:deviceName': 'vivo 1920',
        'appium:appPackage': 'com.android.bbkcalculator',
        'appium:appActivity': 'com.android.bbkcalculator.Calculator',
        'appium:udid':'*****',
        'appium:platformVersion':'12',
    }],
```

* Install Appium in your project
```bash
    npm install --save-dev appium@next
```

* Check if the drivers are still available, if not install them again:
```bash 
appium driver list
```
```bash 
appium driver install xcuitest
appium driver install uiautomator2
```

* If you are using node version greater than 16 also install the following things
```bash
npm i -D typescript ts-node
```

* Run your scripts using
```bash
npx wdio
```