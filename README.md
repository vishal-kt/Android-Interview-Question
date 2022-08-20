# Android-Interview-Question


## What is Android ?

1. Android is mobile platform it consist of linux operating system , middleware and key Application
2. By Google **Android is an open source , linux based software stack created for  wide array of devices and form factors**



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

--------------
## Activity Lifecycle
### Activity Lifecycle (in execution order) -

| Method  | Called When  |
|---|---|
| onCreate()   | Activity is first created.  |
| onStart()    | Activity is becoming visible to the user.  |
| onResume()   | Activity will start interacting with the user.  |
| onPause()    | Activity is not interactable to the user.  |
| onStop()     | Activity is no longer visible to the user.  |
| onRestart()  | After activity is stopped, prior to start.  |
| onDestroy()  | Before activity is destroyed.  |

 >*Note - The onCreate() and onDestroy() methods are called only once throughout the activity lifecycle.



### Uses case of activity lifecycle with execution order

##### **When activity is opened:**
```kotlin
onCreate()

onStart()

onResume()
```
##### **When moved to another activity:**
> Here A == first activity and B == second activity

```kotlin
onPause() - (A)

onCreate() - (B)

onStart() - (B)

onResume() - (B)

onStop() - (A)
```

##### **When another activity is closed and moving back to first activity:**

```kotlin
onPause() - (B)

onRestart() - (A)

onStart() - (A)

onResume() - (A)

onStop() - (B)

onDestroy() - (B)
```

### onStart vs onResume
**onStart()** -> called when the activity becomes visible, but might not be in the foreground (e.g. an AlertFragment is on top or any other possible use case).

suppose there are two activities when app starts and first activity open ... oncreate()...onStrart()...OnResume()...when we click on button to move second activity
...onPause()firstActivity .....and second activities ...onCreate()..onStart()..onResume()..and for firstActivity..onStop()...when we click on back button \
onPause()for second activity get called ... then for first Activity.. onRestart()..onStart()...onResume()....then onStop()...and ... onDestroy()for second Activity

**When We click on lock screen button what happen to the activity life cycle**

when we click on lock screen button ...first there is onCreate()...onStart()...onResume()... then we click on screen lock button .. onPasuse()...onStop().. if we open our phone screen it will be back to onRestart()...onStart()...onResume()... \

**When We click on  Home button what happen to the activity life cycle**

first our app  onCreate()...onStart()...onResume()... when we click on  Home Button onPause()...onStop()... when we go back to the app ..onRestart()...onStart()...onResume()   \

**when we kill the app**
first our app  onCreate()...onStart()...onResume()...when we kill the app onPause()..onStop()..onDestroy()..  \


### **What is the project structure of an Android Application?**



**onResume()** -> called when the activity is in the foreground, or the user can interact with the Activity.

### onPause vs onStop
**onPause()** -> If you can still see any part of it (Activity coming to foreground either doesn't occupy the whole screen, or it is somewhat transparent).

**onStop()** -> If you cannot see any part of it


## What is the project structure of an Android Application? <img align="right" width="306px" src="https://github.com/tech-deity/Android-Interview-Question/blob/main/android_app_project_folder_structure.png" />


A project in Android Studio contains everything that defines your workspace for an app, from source code and assets, to test code and build configurations.
The android project contains different types of app modules, source code files, and resource files..

**Module**
A module is a collection of source files and build settings that allow you to divide your project into discrete units of functionality. 
Your project can have one or many modules, and one module may use another module as a dependency.
You can independently build, test, and debug each module.

**manifests**
Manifests folder contains AndroidManifest.xml for our creating the android application. 
This file contains information about our application such as the Android version, metadata, 
states package for Kotlin file, and other application components. It acts as an intermediator between android OS and our application.

 **Java folder** contains all the java and Kotlin source code (.java) files that we create during the app development, including other Test files.
**res/drawable folder**
It contains the different types of images used for the development of the application. We need to add all the images in a drawable folder for the application development.
 

**res/layout folder**
The layout folder contains all XML layout files which we used to define the user interface of our application. It contains the activity_main.xml file.

**res/mipmap folder**
This folder contains launcher.xml files to define icons that are used to show on the home screen. It contains different density types of icons depending upon the size of the device such as hdpi, mdpi, xhdpi.
 

**res/values folder**
Values folder contains a number of XML files like strings, dimensions, colors, and style definitions. One of the most important files is the strings.xml file which contains the resources. 

**Gradle Scripts folder**
Gradle means automated build system and it contains a number of files that are used to define a build configuration that can be applied to all modules in our application. In build.gradle (Project) there are buildscripts and in build.gradle (Module) plugins and implementations are used to build configurations that can be applied to all our application modules, we define all the dependency here ..


## CONTEXT 

**What is Context** \
The Context in Android is actually the context of what we are talking about and where we are currently present. \
It is the context of current state of application \
It can be used to get the information regarding application and activity \
It can be used to get the access of resources , databases and shared preferences \
Both the Activity and Application class extends the Context class 


**There are Two types of context** 

**Application Context** \
This Context is tied to the Lifecycle of an Application. \
Mainly it is an instance that is a singleton and can be accessed via getApplicationContext() \
 **USE CASE of Application Context** 
 
when you have to create a singleton object for your application and that object needs a context, always pass the application context. \
when you have to initialize a library in an activity, always pass the application context, not the activity context. \

Load Resource Values  \ 
Start a Service  \ 
Bind to a Service  \ 
Send a Broadcast  \ 
Register BroadcastReceiver  \ 

**Activity Context**

This Context is available in an activity  . this context is tied to the lifecycle of activity ..
this context is used when u are passing context in the scope of activity or u need context whoes lifecycle is attached to the current context  \
 If you have to create an object whose lifecycle is attached to an activity, you can use the activity context. \
 Whenever you are in Activity, for any UI operations like showing toast, dialogs, and etc, use the Activity Context.
 
 
 Always try to use the nearest context which is available to you. When you are in Activity, the nearest context is Activity context. When you are in Application, the nearest context is the Application context. If Singleton, use the Application Context. 
 
 Context directly available to you from the enclosing component you’re working within. You can safely hold a reference to it as long as that reference does not extend beyond the lifecycle of that component. As soon as you need to save a reference to a Context from an object that lives beyond your Activity or Service, even temporarily, switch that reference you save over to the application context.
 
 ## What is Application Class 
 
  Application class in Android is the base class within an Android app that contains all other components such as activities and services. 
  The Application class, or any subclass of the Application class, is instantiated before any other class when the process for your application/package is created.
  
  ## Why we need to call setContentView() in onCreate() of Activity class..
  because OnCreate() method is called only once in the activity life cycle we do all the initialization related task there
  
  ## When only onDestroy is called for an activity without onPause() and onStop()?
   When we call Finish() method inside  onCreate() method in that case onDestroy is directly called 
  
  
  ** What is onSavedInstanceState() and onRestoreInstanceState() in activity? **
  
 onSavedInstanceState() - This method is used to store data before pausing the activity.
 onRestoreInstanceState() - This method is used to recover the saved state of an activity when the activity is recreated after destruction. So, the onRestoreInstanceState() receive the bundle that contains the instance state information.
 
 ## 5 Anti  Common Android Anti-Patterns
 Using Base Class -- using base class cauases tight coupling ,instead use extension function  \
 Putting all dependencies in AppModule: Hard to read and during testing, we can't get the specific module \
 Use Fragment Instead of One activity per screen \
 Hardcoding dispatchers: It forces the coroutine to use the particular dispatcher whereas in testing we need to pass the test dispatcher \
 Using GlobalScope: Its keeps running during the application process and doesn't care about the lifecycle of the component which causes memory leak or dead object exception.
 
 
 ## 6 Design pattern every android developer must know
- Singleton
- Factory
- Builder
- Facade
- Dependency Injection
- Adapter
  
