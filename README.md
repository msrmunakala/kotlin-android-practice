
# kotlin-android-practice
![CI](https://github.com/hieuwu/kotlin-android-practice/workflows/CI/badge.svg)

Some small projects to practice Android Basics with Kotlin for beginners. Every project in this repository is simplest. Besides making your own project following this, you should improve the UI for better look and feel, or maybe add more functionalities to upgrade your skill. Happy coding !

**How to use:**
1. CLone this repo to your local machine then choose one to open with Android Studio
2. For each project, you should overview the code inside the activity first, if there is something unclear, get back here then read the References part of each project

# Tictactoe

 - Simple layout design with TableLayout    
 - Handle click event to change
   button's attributes   
 - Handle simple logic for game playing
   
   ![](https://i.imgur.com/De3BQXr.png)
   
**References:**
- [Button](https://developer.android.com/reference/android/widget/Button)
- [Declaring Variables Kotlin](https://kotlinlang.org/docs/tutorials/kotlin-for-py/declaring-variables.html)
- [Control Flow Kotlin](https://kotlinlang.org/docs/reference/control-flow.html)
- [ArrayList Kotlin](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-array-list/)
- [Function Kotlin](https://kotlinlang.org/docs/reference/functions.html)

# Calculator

- Simple layout design with TableLayout, LinearLayout
- Support multiple screens sizes 
- Handle calculating operations "+ - * /". The +/- and %
   is your part

 **Multiple screens Instruction:**
 These are some kind of screens that you have to support: ldpi, mdpi, hdpi, xhdpi, xxhdpi, xxxhdpi
 You have to do this for every Ativity that you need it to be supported.
 
 **Follow these steps:**

 1. Add new resource file in layout folder
    
 2.  Name that new file by the name of the root activity. And the
    directory shoud follow this convention: layout-ldpi or
    layout-xxxhdpi
    
 3.   Use Design tab and choose the device with suitable kind of screen to
    see your layout in that screen
    
 4.  Change the layout if needed

![](https://i.imgur.com/ylZF0O8.png)

**References:**
- [EditText](https://developer.android.com/reference/android/widget/EditText)
- [Support Different Screens](https://developer.android.com/training/multiscreen/screensizes)


# Disneyworld
 - Play with Google Map SDK Android: change map types, view angle
 - Add toolbar menu to perform some actions
 - Use Thread, GPS service to get location continuously
 
 ![](https://i.imgur.com/J4lPrHO.png)

**References:**
 
- [Request App Permission](https://developer.android.com/training/permissions/requesting)
- [BitMapDescriptorFactory](https://developers.google.com/android/reference/com/google/android/gms/maps/model/BitmapDescriptorFactory)
- [BitMapDescriptor](https://developers.google.com/android/reference/com/google/android/gms/maps/model/BitmapDescriptor)
- [LocationListener](https://developer.android.com/reference/android/location/LocationListener)
- [LocationManager](https://developer.android.com/reference/android/location/LocationManager)
- [Marker](https://developers.google.com/maps/documentation/android-sdk/marker)
- [Map Types](https://developers.google.com/maps/documentation/android-sdk/map#map_types)
- [Menu](https://developer.android.com/guide/topics/ui/menus?hl=vi)
- [Toolbar](https://developer.android.com/training/appbar/setting-up)
- [Multithread Kotlin](https://medium.com/@korhanbircan/multithreading-and-kotlin-ac28eed57fea)
- [Nested and Inner Class Kotlin](https://kotlinlang.org/docs/reference/nested-classes.html)
- [Classes and Inheritance Kotlin](https://kotlinlang.org/docs/reference/classes.html)
- [Interfaces Kotlin](https://kotlinlang.org/docs/reference/interfaces.html)
- [Exceptions: try, catch Kotlin](https://kotlinlang.org/docs/reference/exceptions.html)

# MVC Pattern Demo

**Not completed yet**
- Model: data - Bean classes, database, Content Provider
- View: user interface - define how to display the data
- Controller: event handling, navigation, communicator between Model and View



**References:**

- [MVC Android](https://medium.com/upday-devs/android-architecture-patterns-part-1-model-view-controller-3baecef5f2b6)

# Android Architecture References
- [Code - Android Architecture Blueprints](https://github.com/android/architecture-samples)
- [Blog - Android Architecture Pattern](https://android-developers.googleblog.com/2017/05/android-and-architecture.html)
- [Blog - Android Architecture MVP](https://medium.com/upday-devs/android-architecture-patterns-part-2-model-view-presenter-8a6faaae14a5)
- [Doc - Guide Android Architecture](https://developer.android.com/jetpack/guide)
- [Talk Android Architecture Component](https://www.youtube.com/watch?v=pErTyQpA390)
- [Talk Droidcon A Journey Through MV Wonderland](https://www.youtube.com/watch?v=QrbhPcbZv0I)
- [Blog - Android Architecture Pattern](https://android-developers.googleblog.com/2017/05/android-and-architecture.html)







# About Me APP
- Simple layout with LinearLayout
- Data binding basic technique

![](https://i.imgur.com/FDOtTiG.png)

**Problem with findViewById()**
When our app has complex view hierarchies, `findViewById()` function will slow down the app. Why? Given that you need to access to a View, which is nested in a nested nested nested ViewGroup...Uh ohh...

Android need to traverse all over the view herrachies from the root until get the needed one. If our app has so complex view, it is expensive to find a desired view. Is there a way for the View to update whenever the data changes and we don't need to go so far with expensive `findViewById()`? Use **Data Binding**

**Benefits from Data Binding**
- Code is shorter, easier to read, maintain
- Data and Views are separated, make it easier for Unit Test
- Android system only traverses once to get view, during app start up, not at runtime
- Type safty when access views. We can get exception while compiling and fix it earlier

**Follow these steps:**
1. Go to `build.gradle`, add this block
```kotlin
buildFeatures {
   dataBinding true
 }
```
2. Wrap the whole layout with `<layout>` as a root view
3. Define a binding varialbe:
`private lateint var binding:ActivityMainBinding`
4. Replace `setContentView()` with `binding = DataBindingUtil.setContentView(this, R.layout.activity_main)`
5. Replace `findViewById()` with references to the view in binding object.
`findViewById<Button>(R.id.done_button)` =>  `binding.doneButton` (**Note:** name of the view will be the `id` in XML but is defined as camel case)
6. Create a class for data
7. Add `<data>` block inside `<layout>` tag
8. Define `<variable>` with name and type to the data class
```xml
<data>
   <variable
       name="myName"
       type="com.example.android.aboutme.MyName" />
</data>
```

9. Back at `MainActivity`, create value for our binding variable. Ex: `private val myName: MyName = MyName("Hieu Vu")`
10. Bind your data with the variable `binding.myName = myName`
11. Change the content of the View to display our data with the name in the `<data>` block. `android:text="@={myName.name}"`
**Note:** Whenever you change your data, remember to call  `invalidateAll()` method to notify the UI to refresh with new data.

**References:**
- [Google codelab with Kotlin](https://codelabs.developers.google.com/android-kotlin-fundamentals/)

# Dessert Clicker
- When `onPause()` is called, the app no longer has focus. After `onStop()`, the app is no longer visible on screen
- `onCreate()` and `onDestroy()` only run once
- `onCreate()`: where all your first-time initialization goes, where you set up the layout for the first time by inflating it, and where you initialize your variables, data binding...
- `onRestart()` method is a place to put code that you only want to call if your activity is not being started for the first time.
- When our application starts, the `onCreate()`, `onStart()` and `onResume()` run orderly
- At the very first Activity, if we press `Physical Back button` and move to the home screen of the device ,  `onPause()`, `onStop()`, `onDestroy()` run orderly
- If we reopen the app, it will call three methods `onCreate()`, `onStart()` and `onResume()` again
- If we press `Home button`, `onPause()` and `onStop()` are called
- If we reopen our app, the `onRestart()`,   `onStart()`,  `onResume()` will be called
- When we press the `Tabs button`, `onPause()` and `onStop()` will be called
- Then if we go back to our app, `onRestart()`, `onStart()`, `onResume()` wil be called
- Whatever code runs in `onPause()` blocks other things from displaying, so keep the code in `onPause()` lightweight. For example, if a phone call comes in, the code in `onPause()` may delay the incoming-call notification.

- `onAttach()`: Called when the fragment is associated with its owner activity.
- `onCreate()`: Similarly to onCreate() for the activity, onCreate() for the fragment is called to do initial fragment creation (other than layout).
- `onCreateView()`: Called to inflate the fragment's layout.
- `onViewCreated()`: Called immediately after onCreateView() has returned, but before any saved state has been restored into the view.
- `onStart()`: Called when the fragment becomes visible; parallel to the activity's onStart().
- `onResume()`: Called when the fragment gains the user focus; parallel to the activity's onResume()

- `onPause()`: Called when the fragment loses the user focus; parallel to the activity's onPause().
- `onStop()`: Called when the fragment is no longer visible on screen; parallel to the activity's onStop().
- `onDestroyView()`: Called when the fragment's view is no longer needed, to clean up the resources associated with that view.

- To add skeleton override methods to your classes in Android Studio, select **Code > Override** Methods or press`Control+o`.
**Logging with Timber**
A logging library better thant the default one. Benefits: 
- Generates the log tag for you based on the class name.
- Helps avoid showing logs in a release version of your Android app.
- Allows for integration with crash reporting libraries.

**Steps to add Timber:**
1. Add dependencies to `gradle.build`
2. Create a class extends the `Application` class
3. In the `onCreate()` of new class, add `Timber.plant(Timber.DebugTree())`
4. Add `android:name` with your new application class to `<application>` tag
5. Call with this syntax `Timber.i("Log example")`

# License

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Giấy phép Creative Commons " style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">Kotlin Android Practice</span> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License. </a>.<br />Based on a work at <a xmlns:dct="http://purl.org/dc/terms/" href="https://github.com/hieuwu/kotlin-android-practice" rel="dct:source">https://github.com/hieuwu/kotlin-android-practice</a>.
