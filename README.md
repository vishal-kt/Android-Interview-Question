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

***Android App Architecture***  \
-robust \
-testable \
-maintainable \
 allows the app to scale, increases the app's robustness, and makes the app easier to test. \
 architecture defines the boundaries between parts of the app and the responsibilities each part should have. 
 
 ## principles that architecture follows 
 
 **Separation of concerns ** \
 separating a computer program into distinct sections. Each section addresses a separate concern like UI-based classes should only contain logic that handles UI and operating system interactions , business logic vlass should care about there concerns and data logics should concern to data . \
 
 **Drive UI from data models ** \
 drive your UI from data models, preferably persistent models. Data models represent the data of an app. They're independent from the UI elements and other components in your app.  \

Persistent models are ideal for the following reasons:

Your users don't lose data if the Android OS destroys your app to free up resources.

Your app continues to work in cases when a network connection is flaky or not available \


**single Source of Truth** \
single source of truth (SSOT), is the practice of structuring information models and associated schemata such that every data element is stored exactly once.

This pattern brings multiple benefits: \

It centralizes all the changes to a particular type of data in one place. \
It protects the data so that other types cannot tamper with it. \
It makes changes to the data more traceable. Thus, bugs are easier to spot. \

**Unidirectional Data Flow** \
in Unidirectional data flow state flows in only one direction. The events that modify the data flow in the opposite direction \
https://developer.android.com/topic/architecture

## Solid Principle 
https://medium.com/@asheshb/programming-principles-android-app-architecture-by-example-part-2-5-41d87eaf30bf

**Single Responsibility Principle (SRP)**
This principle takes direct guidance from the separation of concerns. A class should be responsible for one thing or we can say that there should be only one reason for it to change. Only one reason because if there are two reasons to change then the probability of an error or instability becomes twice and so on. \

**Open Closed Principle**

A class should be open for extension but closed for modification. 

For example, let’s say we have a ReportWriter class which calls getReportData() function of PdfReport to get the data and print it.It is reasonable to assume that in near future we may need to print the report in text, xml or other formats. When that happens we will have to modify the ReportWriter class to adjust for any new format. That would be a violation of OCP, which says that a class should be closed for modification.
A better way to make our code future ready is to depend on abstraction.
We can declare an interface Report and make the concrete class PdfReport implement it. We can pass PdfReport as Report object to the ReportWriter class. This way ReportWriter will depend on abstraction and wouldn’t be concerned with the concrete class which is implementing that interface. \

**Liskov Substitution Principle (LSP)**

A child object should behave like its parent when passed as a parent. Let’s say Class B extends Class A. There is a function which requires Class A object but instead, if we pass Class B object (perfectly legal in object-oriented world) then Class B object should behave like Class A object. \

**Interface Segregation Principle (ISP)**
Many client specific interfaces are better than one general purpose interface.....
divide the large single interface into multiple interface and let clients use them. This way clients would know about only those methods which it requires. Remember, separation of concerns?

Now Service class is implementing 3 interfaces instead of a single large interface. Other than that there is no change in Service class but the exposure to clients are now reduced to only those functions they require.   \

**Dependency Inversion Principle (DIP)**
High-level modules should not depend on low-level modules

A high level class should not depend on low level class and both should depend on abstraction. Before going further let’s see what’s a high/low level class.

An Android app executes inside a boundary. Outside the boundary, there is the Android framework itself, various service manager etc. A class which is closest to the boundary is the lower level class. For example Activity/Fragment get events directly from the Android framework which is outside the boundary so it’s low level class. A low level class is based on implementation/details.

A high level class is more abstract, dealing with business logic (the code specific to your app). High level classes are less dependent on the platform/third party libraries.Let’s say Repository class needs to get data from DB class. Here Repository is a higher level class than DB class because DB class is more dependent on detail (SQLite). Now, Repository class can’t directly depend on DB class as it would be a violation of DIP.

What we do is create an Interface DataInterface which is implemented by DB class and then Repository class uses an object of DataInterface . The data interface is an abstract class and at the same level as Repository so it’s fine for the Repository to depend on it.

Also if we see both Repository and DB class now depend on abstraction. This helps to loosely couple the classes. Another advantage is now that we have DataInterface , a network class can implement it and Repository class (without any modification) would be ready to get data from the network.

**Android ProcessLifecycleOwner**
Manage life cycle of whole application process , many application changes there behaviour state  when they move from  foreground to background and vice versa ... there are certain application which calculate sessions when the app is in foreground this can be achieved using Android Processlife Cycle Owner class which will keep eye on changes in the state of app and according to that it will behave .  \

To Know when your application in foreground or in background we need  \
We can use Lifecycle event for it: \
— when application moved to background ON_STOP event will be triggered \
— when application moved to foreground ON_START event will be triggered \

class ApplicationObserver(val analytics: Analytics) : LifecycleObserver {
    
    @OnLifecycleEvent(Lifecycle.Event.ON_STOP)
    fun onBackground() {
    }
    @OnLifecycleEvent(Lifecycle.Event.ON_START)
    fun onForeground() {
    }
}

 The next step is attaching ApplicationObserver to our application. \
 register it in the application class \
 
 class MapNotesApp : Application() {
    override fun onCreate() {
        super.onCreate()
        ...
        val analytics = Analytics()
        analytics.addReporter(LogReporter())
        ProcessLifecycleOwner
            .get()
            .lifecycle
            .addObserver(ApplicationObserver(analytics))
    
    }
    ...
}

The Analytics class allows us to collect session information. \
class Analytics {
    private var startSessionTimestamp: Long = -1
    private val reporters = mutableListOf<AnalyticsReporter>()
    fun addReporter(reporter: AnalyticsReporter) {
        reporters.add(reporter)
    }
    fun startSession() {
        startSessionTimestamp = Date().time
    }
    fun stopSession() {
        reportSession()
        sendAllEvents()
        startSessionTimestamp = -1
    }
    private fun reportSession() {
        reporters.forEach {reporter ->
        val currentTime = Date().time
        // we should check if session was started and stopped correctly
        val sessionTime = (currentTime - startSessionTimestamp) / 1000
            reporter.report("Session time: $sessionTime sec" )
        }
    }
    private fun sendAllEvents() {
        reporters.forEach {reporter ->
            reporter.sendAllEvents()
        }
    }
}

The AnalyticsReporter interface is an abstraction for all reporters, like LogReporter.

interface AnalyticsReporter {
    fun report(event: String)
    fun sendAllEvents()
}
class LogReporter : AnalyticsReporter {
    private val events = mutableListOf<String>()
    override fun report(event: String) {
        events.add(event)
    }
    override fun sendAllEvents() {
        events.forEach { event ->
            Log.d(this.javaClass.simpleName, event)
        }
        events.clear()
    }
}

class ApplicationObserver(val analytics: Analytics) : LifecycleObserver {
    @OnLifecycleEvent(Lifecycle.Event.ON_START)
    fun onForeground() {
        analytics.startSession()
    }
    @OnLifecycleEvent(Lifecycle.Event.ON_STOP)
    fun onBackground() {
        analytics.stopSession()
    }
}

  
