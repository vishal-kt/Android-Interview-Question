# Android-Interview-Question

## Android Components
### Explain briefly all the Android application components

**App components** are the essential building blocks of an Android app. Each component is an entry point through which the system or a user can enter your app.
There are four different types of app components :

* **Activities** - An activity is the entry point for app interaction with the user. It represents a single screen with a user interface.
* **Services** - A service is a general-purpose entry point for keeping an app running in the background for all kinds of reasons. It is a component that runs in the background to perform long-running operations or to perform work for remote processes.
* **Broadcast receivers** - A broadcast receiver is a component that enables the system to deliver events to the app outside of a regular user flow, allowing the app to respond to system-wide broadcast announcements.
* **Content providers** - A content provider manages a shared set of app data that you can store in the file system, in a SQLite database, on the web, or on any other persistent storage location that your app can access.



### What is an Activity?

An **Activity** represent a single screen with a user interface just like window or frame of java .. Android activity is the subclass of context Theme Wrapper Class

An **activity** provides the window in which the app draws its UI. This window typically fills the screen, but may be smaller than the screen and float on top of other windows. Generally, one activity implements one screen in an app. For instance, one of an app’s activities may implement a Preferences screen, while another activity implements a Select Photo screen.
