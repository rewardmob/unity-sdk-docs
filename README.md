# RewardMob Unity SDK Overview
The RewardMob Unity SDK gives game developers access to a completely new method of monetization for their products.

By removing advertisements from your game, and bringing them onto our platform, we make your game more about the gameplay
and less about the immersion-breaking advertisements.

## RewardMob SDK Integration Steps (Required)
1. Download the latest version of the RewardMob SDK from https://github.com/rewardmob/unity-sdk-docs/releases

2. Import the plugin inside of an existing project

3. Place a **RewardMobManager** prefab inside of any scene within your project

4. Populate the **RewardMobData** resource object's game ID field with the ID provided to you inside the e-mail we sent you

5. Place a **RewardMobCanvas** prefab inside of any scene where you wish to display the RewardMob Button. 
Feel free to change it's position. **Please do not disable this GameObject, 
as it will disable itself.**

**Follow the following steps as required.**

## Android Integration Steps (Optional)
1. (IF RUNNING UNITY 5.6.1) Modify your main activity's ```android:name``` from ```com.unity3d.player.UnityPlayerActivity``` to ```net.gree.unitywebview.CUnityPlayerActivity``` inside of your AndroidManifest.xml located in ```Resources/Plugins/Android```
 
 
## To Reference RewardMob SDK Calls
Include our library at the top of the relevant script.
```C#
using RewardMobSDK;
```


## Rewarding a User
Locate a point in your game where you believe a user should be worthy of earning a reward, and call the function below. We typically suggest distributing a reward every 30 seconds of gameplay to retain user engagement with RewardMob. However, this can vary between experiences.
```C#
RewardMob.instance.SendReward(string achievementDetails, int amountOfRewards);
```
```
string achievementDetails = A short message that describes how the reward was earned. 

int amountOfRewards = The amount of rewards to give the user. 
```


## Show the RewardMob Button
This should be displayed at a point where users should be able to view the tournament information. 

For example, after a user completes a level, or dies in your game. 
```C#
RewardMob.instance.ShowButton();
```


## Hide the RewardMob Button
Simply hides the RewardMob button if it happens to be active inside of the scene.
```C#
RewardMob.instance.HideButton();
```


## Testing RewardMob Tournaments
We've recently implemented a completely new system for developers to test tournament functionality in a live environment. The steps to test your application is as follows:

1. Download the latest version of the RewardMob app from Google Play on Android, or the App Store on iOS

2. Send your e-mail/username to **tanner@rewardmob.com** to be flagged for test mode tournaments

3. Launch your game containing the RewardMob SDK, and log in

If your account has been flagged as a tester for that game, you will see a test mode tournament!
