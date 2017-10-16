# Facebook SDK
login at https://developers.facebook.com/
## Add to build.gradle(project) above dependencies lines
```
repositories {
	mavenCentral() 
}
```

## Add to build.gradle(module)
```
dependencies { 
  compile 'com.facebook.android:facebook-android-sdk:4.+'
}
```
## Add to AndroidManifest.xml
```
<uses-permission android:name="android.permission.INTERNET" />
```

## Get Key Hash
### add in onCreate() and run to get key hash
```
PackageInfo packageInfo = null;
        try {
            packageInfo = getPackageManager().getPackageInfo(
                    "com.nhutstudio.facebooksdk", PackageManager.GET_SIGNATURES);
        } catch (PackageManager.NameNotFoundException e) {
            e.printStackTrace();
        }
        for (Signature signature : packageInfo.signatures){
            MessageDigest messageDigest = null;
            try {
                messageDigest = MessageDigest.getInstance("SHA");
            } catch (NoSuchAlgorithmException e) {
                e.printStackTrace();
            }
            messageDigest.update(signature.toByteArray());
            Log.d("KeyHash: ", Base64.encodeToString(messageDigest.digest(), Base64.DEFAULT));
        }
```

<img src="https://github.com/dinhtho/FacebookSDK/blob/master/image2.png" width="800"/>

## Add to strings.xml
```
<string name="facebook_app_id">176299539503870</string>
```

## Add in <Application></Application> in Manifest.xml
```
<meta-data
            android:name="com.facebook.sdk.ApplicationId"
            android:value="@string/facebook_app_id" />
```
<img src="https://github.com/dinhtho/FacebookSDK/blob/master/image.png" width="800"/>