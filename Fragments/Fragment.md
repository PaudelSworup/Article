# Q. Article on fragment

 <h1 style="text-align:center; font-weight:700; letter-spacing:2px;">Fragments</h1>

## Fragments
<p style="text-align:justify;">A fragment is a part of applications user interface that is bound to an activity.Fragments have their lifecycle and layouts or UI components.Fragments help enrich your UI design, pass data between different screens, and adapt to different device configurations.Android introduced fragments in Android 3.0 (API level 11), primarily to support more dynamic and flexible UI designs on large screens, such as tablets.</p>


## Why do we need Fragments?
<p style="text-align:justify;">Fragment is simple to use as it can be used as container of activities. Fragments are used for different purpose and some of them are:
    <ol>
    <li>Simple to use </li>
    <li>Encapsulation of logic.</li>
    <li>Better handle of the lifecycle of the fragment.</li>
    <li>Reusable in other activities.</li>
    </ol>
    <hr>
    
Fragments have its lifecycle. Fragment can be understand from the figure below:
<hr>
<img src="https://developer.android.com/images/guide/fragments/fragment-view-lifecycle.png" width="auto"style="max-width:600; height:auto;"/>
<hr>
</p>

## Activity vs Fragments
<p style="text-align:justify;">An Activity is a user interface component that is mainly used to construct a single screen of the application and represents the main focus of attention on a screen. An activity can host one or more fragments at a time.</p>

<p style="text-align:justify;">Fragments, as tablets emerged with larger screens, are reusable components that are attached to and displayed within activities. It is basically a piece of an activity that enables more modular activity design. </p>

| Activity | Fragmet |
|---------------| ------------------|
|Activity is an application component that gives a user interface where the user can interact. | The fragment is only part of an activity, it basically contributes its UI to that activity.
|Activity is not dependent on fragment | Fragment is dependent on activity. It can’t exist independently.|
|we need to mention all activity it in the manifest.xml file | After using multiple fragments in a single activity, we can create a multi-screen UI.
|Activity can exist without a Fragment  | Fragment cannot be used without an Activity.|
|Creating a project using only Activity then it’s difficult to manage. | While Using fragments in the project, the project structure will be good and we can handle it easily.|
|Activity is not lite weight. | The fragment is the lite weight.|
<hr>

## Creating a Fragment?
<p style="text-align:justify;">A fragment represents a modular portion of the user interface within an activity. A fragment has its own lifecycle, receives its own input events, and you can add or remove fragments while the containing activity is running.</p>

### Steps for creating Fragments
<p>
<ol>
<li>Setup your environment</li>
    <p style="text-align:justify;">Fragments require a dependency on the AndroidX Fragment library. You need to add the Google Maven repository to your project's settings.gradle file in order to include this dependency.</p>
<hr>

<li>Create a fragment class</li>
    <p>To create a fragment, extend the AndroidX Fragment class, and override its methods to insert your app logic, similar to the way you would create an Activity class.</p>
    <p>Example: <br/>
    class ExampleFragment extends Fragment {<br/>
    public ExampleFragment() {<br/>
        super(R.layout.example_fragment);<br/>
    }
}
    </p>
<hr>
<li>Add a fragment to an activity</li>
    <p style="text-align:justify;">Generally, your fragment must be embedded within an AndroidX FragmentActivity to contribute a portion of UI to that activity's layout. FragmentActivity is the base class for AppCompatActivity, so if you're already subclassing AppCompatActivity to provide backward compatibility in your app, then you do not need to change your activity base class. Fragments can be added to your activites in two ways such as by using XML layout and by programmatically.</p>

## Example via XML layout

    <androidx.fragment.app.FragmentContainerView
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/fragment_container_view"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:name="com.example.ExampleFragment" />

## Example via programmatically
<p  style="text-align:justify;">Unlike the XML approach, the android:name attribute isn't used on the FragmentContainerView here, so no specific fragment is automatically instantiated. Instead, a FragmentTransaction is used to instantiate a fragment and add it to the activity's layout.</p>


    <androidx.fragment.app.FragmentContainerView
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/fragment_container_view"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
   />

  public class ExampleActivity extends <br/>AppCompatActivity {<br/>
    public ExampleActivity() {<br/>
        super(R.layout.example_activity);
    }<br/>
    @Override<br/>
    protected void onCreate(Bundle savedInstanceState) {<br/>
        super.onCreate(savedInstanceState);<br/>
        if (savedInstanceState == null) {<br/>
            getSupportFragmentManager().<br/>beginTransaction()<br/>
                .setReorderingAllowed(true)<br/>
                .add(R.id.fragment_container_view, <br/>ExampleFragment.class, null)<br/>
                .commit();<br/>
        }<br/>
    }<br/>
}
</ol>
</p>




