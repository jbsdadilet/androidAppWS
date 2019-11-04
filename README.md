# Getting Started

1. Download Android Studios (latest version)
2. Finish the set up (use the recommended settings)
3. Start a new Android Studio project
4. Select "Empty Activity" under "Phone and Tablet"
5. Name your project ("myAndroidGame)
6. Name your package (format typically goes com.author.project)
7. Select "Java" for language
8. Choose Android 5.0 (Lollipop) for Minimum API level
9. Give a few minutes for Android Studios to download and configurate stuff
10. Click on "No devices", then "Open AVD Manager"
11. Click on "Create Virtual Device"
12. Pick Pixel 2, select download next to Oreo (Android 8.1)
12a. If "/dev/kvm device: permission denied", run sudo setfacl -m u:$USER:rwx /dev/kvm
12b. Restart Android Studios
13. Accept and hit next
14. More downloading woohoo!!
15. After everything is set up, go back to the main window and hit the green play button
16. Android emulator should be all set!

# Goal

Display a text with the name of the color. The text will be colored with a random color. The goal is to pick the color in the text, not the color of the test. (ex: If the text is "blue" and is colored red, you should pick the blue button). The users will have 3 seconds to press a button, and they will have to get 8 correct in a row to win.

# Components

We will need just two components for this game to function.

1. Text that displays the puzzle, the timer, and the result of the game
2. Colored buttons that i) acts as a start button ii) acts as an answer button

# TextView

```xml
<TextView
    android:id="@+id/resultTextView"
    android:visibility="invisible"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:textColor="@android:color/background_dark"
    android:textSize="30sp"
    app:layout_constraintBottom_toBottomOf="parent"
    app:layout_constraintEnd_toEndOf="parent"
    app:layout_constraintHorizontal_bias="0.498"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toTopOf="parent"
    app:layout_constraintVertical_bias="0.785" />
```

You will learn that getting the layout correct will be a pain. In the sample **TextView** code above, the ```app:___``` defines how the **TextView** will be positioned. I recommend you to copy the code from the source for those entries.

The attributes that we are interested in are _id, visibility, textSize,_ and _textColor_.

_id_, as the name suggests, gives the view a id so we can reference to this specific TextView in our code.

_visibility_ determines if the view is visible or not.

_textSize_ and _textColor_ does what you think it does.

# Button

```xml
<Button
    android:id="@+id/startButton"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:backgroundTint="@color/colorPrimaryDark"
    android:padding="50dp"
    android:text="GO!"
    android:textSize="80sp"
    android:onClick="start"
    android:tag="4"
    app:layout_constraintBottom_toBottomOf="parent"
    app:layout_constraintEnd_toEndOf="parent"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toTopOf="parent"
    app:layout_constraintVertical_bias="0.499" />
```

In addition to the properties that **TextViews** have, **Buttons** also have the _onClick_ attribute. It will execute the named function once clicked. _tag_ is additional information that you can define. We will see how this is useful.

# GridLayout

```xml
<android.widget.GridLayout
    android:layout_width="395dp"
    android:layout_height="262dp"
    android:columnCount="2"
    android:rowCount="2"
    app:layout_constraintBottom_toBottomOf="parent"
    app:layout_constraintEnd_toEndOf="parent"
    app:layout_constraintHorizontal_bias="0.5"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toTopOf="parent">
    ... (components here)
</android.widget.GridLayout>
```

Because we would like to display 4 buttons that act as answer choices, it will be easier for us to use **GridLayout** to ensure the proper placement instead of placing each buttons 1 at a time. Notice the _columnCount_ and _rowCount_ attribute. We can add _android:layout_column_ and _android:layout_row_ to the components inside the **GridLayout** to specify which row/column it goes to.

# Make the Layout!

Make a button in the center that displays "GO!". Once the button is pressed, it should display the 4 colored buttons, a timer, the puzzle, and the correct answer count.

# How?

Try to reference the sample code! Or you can simply copy paste the code in the repo, but that doesn't work, as the button does nothing (or it will not function at all)! This is because even though you defined the button to execute ***start***, you have not defined what ***start*** does!

# Writing "Actual" Code

Now that the front-end code is all set, we need to make the game work! Go to the ***MainActivity.java*** and import the following:

```java
import androidx.appcompat.app.AppCompatActivity;

import android.os.CountDownTimer;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;

import java.util.Random;
```

and make sure the MainActivity class extends AppCompatActivity.

When the app is opened, it runs the ```java onCreate``` method.
