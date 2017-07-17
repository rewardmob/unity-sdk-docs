# RewardMob Unity SDK Overview
The RewardMob Unity SDK gives game developers access to a completely new method of monetization for their products.

By removing advertisements from your game, and bringing them onto our platform, we make your game more about the gameplay
and less about the immersion-breaking advertisements.

## RewardMob SDK Integration Steps (Required)
1. Download zip/clone this repository

2. Import the plugin inside of an existing project

3. Place a **RewardMobManager** prefab inside of any scene within your project

4. Populate the **RewardMobData** resource object's game ID field with the ID provided to you inside the RewardMob Developer Panel

5. Place a **RewardMobCanvas** prefab inside of any scene where you wish to display the RewardMob Button. 
Feel free to change it's position. **Please do not disable this GameObject, 
as it will disable itself.**

**Follow the following steps as required.**

## Android Integration Steps (Optional)
1. Paste the following XML as its own activity inside of your AndroidManifest.xml file located at: 

**YOUR_PROJECT_PATH->Assets->Plugins->Android->AndroidManifest.xml** 
``` 
<activity 
android:configChanges="mcc|mnc|locale|touchscreen|keyboard|keyboardHidden|
navigation|orientation|screenLayout|uiMode|screenSize|smallestScreenSize|fontScale" 
android:name="com.rewardmob.sdk.android.AuthPlugin" 
android:screenOrientation="fullSensor">       
  <intent-filter>         
    <data android:scheme="rm<YOUR_GAME_ID_HERE>" />         
    <action android:name="android.intent.action.VIEW" />         
    <category android:name="android.intent.category.DEFAULT" />         
    <category android:name="android.intent.category.BROWSABLE" />       
  </intent-filter> 
</activity> 
```
2. Replace the ```<YOUR_GAME_ID_HERE>``` in the XML markup pasted in the previous step with the game ID weâ€™ve provided you (```ie. if ID is 12345 replace with rm12345```)

3. Modify your main activity's ```android:name``` from ```com.unity3d.player.UnityPlayerActivity``` to ```net.gree.unitywebview.CUnityPlayerActivity``` inside of your AndroidManifest.xml located in ```Resources/Plugins/Android```
 
 
## To Reference RewardMob SDK Calls
Include our library at the top of the relevant script.
```C#
using RewardMobSDK;
```


## Rewarding a User
Locate a point in your game where you believe a user should be worthy of earning a reward, and call the function below.
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


## Testing the RewardMob SDK in RewardMob's Development Mode
We've recently implemented a completely new system for developers to test tournament functionality in a non-production environment. The steps to test your application is as follows:

1. Download the latest version of the RewardMob app from Google Play on Android, or the App Store on iOS

2. Open up the following URL in your mobile device's web browser **(https://dev.rewardmob.com/auth/links)**

3. Enter the game ID we've provided you in the **RewardMob Client ID** field on the link provided in the previous step, and select "Development Mode" from the dropdown

4. Launch the RewardMob application in "Development Mode" by clicking **"Development Environment"** under the RewardMob App header on the website previously mentioned