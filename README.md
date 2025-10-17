# DIT3-1-Ashley-Hermione-Gomez-Act02

## Reflection

### What I observed about the app lifecycle when switching between screens or minimizing the app:

At first, I didn't realize how many things happen behind the scenes when you just click a button or press the home button! When I clicked "Go to Screen 2", I saw in the Logcat that MainActivity didn't just disappear and it went through onPause() and onStop() first. Meanwhile, SecondActivity started fresh with onCreate(), onStart(), and onResume(). It's like the app is putting the first screen to sleep instead of killing it.

The weirdest thing was when I rotated my phone. The whole activity got destroyed and recreated! I saw onPause() → onStop() → onDestroy() → onCreate() → onStart() → onResume() all happen just from rotating. I guess Android does this to reload the layout properly, but it seems like a lot of work.

When I minimized the app (pressed home button), it called onPause() and onStop(), but NOT onDestroy(). So the app is still in memory, just hidden. When I came back to it, it continued right where I left off using onRestart().

### What I learned about activity management in Android:

I learned that Android is really smart about managing memory and resources. Activities don't just "exist" or "not exist" and they go through different states depending on what the user is doing. This is important because phones have limited resources compared to computers.

The lifecycle methods give us control over what happens at each stage. For example, if I was making a video player app, I would pause the video in onPause() so it doesn't keep playing when the user switches to another app. Or if I had a game, I'd save the player's progress in onStop() in case Android kills the app to free up memory.

I also realized why apps sometimes lose your data when you rotate your phone and if the developer didn't properly save the state, everything gets reset when the activity is recreated. Now I understand why some apps ask you to enter information again after rotating!

Overall, I think the lifecycle seems complicated at first, but it actually makes sense once you see it in action. Every method has a purpose, and knowing when to use each one will help me build better, more stable apps that don't waste battery or crash randomly.
