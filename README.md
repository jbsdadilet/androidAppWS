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
