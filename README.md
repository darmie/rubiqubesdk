# RubiQube Android SDK
RubiQube is a reward – based advertising platform that drives engagement and monetization opportunities for online publishers, while delivering rewards to their end users and providing advertisers with engaged customers.


#USAGE

### Include rubiqube sdk in your gradle dependency
Download and copy `rubiqubesdk.aar` file into your project's `libs` folder
```
dependencies {
  compile (name: 'rubiqubesdk', ext:'aar')
  compile 'com.android.support:appcompat-v7:23.3.0' //IMPORTANT: Rubiqube sdk depends on this library to work
  compile 'com.loopj.android:android-async-http:1.4.9'    //IMPORTANT: Rubiqube sdk depends on this library to work
}
```

### Initialize rubiqube sdk

```
import rubiqube.ng.rubiqubesdk.*;

Ad rubiqube = Ad.getInstance();
rubiqube.init(publisherID, placementID, callback_url);
```
#####Params
(INT) publisherID
(INT) placementID
(STRING) callback_url

Get your publisher and placement IDs from RubiQube website, the callback url will be used to update your database. 

### Listen to RubiQube internal events

```
rubiqube.setOnAdListener( new Ad.OnAdListener(){
            @Override
            public void onFinished(){
                Toast.makeText(getApplicationContext(), "YOU HAVE BEEN REWARDED 10G Points", Toast.LENGTH_LONG).show();
                Log.v("MAIN ACTIVITY", "VIDEO AD FINISHED");
            }

            @Override
            public void onInitError(){

                Toast.makeText(getApplicationContext(), "ADVERT VIDEO COULD NOT BE INITIALIZED", Toast.LENGTH_LONG).show();
                Log.v("MAIN ACTIVITY", "VIDEO COULD NOT BE INITIALIZED");
            }

            @Override
            public void onInitSuccess(){
                //This is the right time to play the video Ad 
                Toast.makeText(getApplicationContext(), "VIDEO IS INITIALIZED", Toast.LENGTH_LONG).show();
                Log.v("MAIN ACTIVITY", "VIDEO IS INITIALIZED");
            }

        });
```

### Play video Ad
`rubiqube.showVideo(_activity);  //_activity is the current activity from which you wish to launch the video Ad`


