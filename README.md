# Spotlight

<img src="https://github.com/TakuSemba/Spotlight/blob/master/arts/logo.png" alt="alt text" style="width:200;height:200">

![Platform](http://img.shields.io/badge/platform-android-green.svg?style=flat)
![Download](https://api.bintray.com/packages/takusemba/maven/spotlight/images/download.svg)
![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)
![API](https://img.shields.io/badge/API-14%2B-brightgreen.svg?style=flat)

## Gradle

```groovy
dependencies {
    compile 'com.github.takusemba:spotlight:1.1.1'
}
```


## Usage

```java

Spotlight.with(this)
        .setDuration(1000L) // duration of Spotlight emerging and disappearing in ms
        .setAnimation(new DecelerateInterpolator(2f)) // animation of Spotlight
        .setTargets(firstTarget, secondTarget, thirdTarget ...) // set targets. see below for more info
        .setOnSpotlightStartedListener(new OnSpotlightStartedListener() { // callback when Spotlight starts
            @Override
            public void onStarted() {
                Toast.makeText(context, "spotlight is started", Toast.LENGTH_SHORT).show();
            }
        })
        .setOnSpotlightEndedListener(new OnSpotlightEndedListener() { // callback when Spotlight ends
            @Override
            public void onEnded() {
                Toast.makeText(context, "spotlight is ended", Toast.LENGTH_SHORT).show();
            }
        })
        .start(); // start Spotlight
                        
```

if you want to show Spotlight immediately, use `addOnGlobalLayoutListener` to wait until views are drawn.

```java
view.getViewTreeObserver().addOnGlobalLayoutListener(new ViewTreeObserver.OnGlobalLayoutListener() {
    @Override public void onGlobalLayout() {
        view.getViewTreeObserver().removeOnGlobalLayoutListener(this);
        Spotlight.with(this)...start();
    }
});
```

<br/>
<br/>

<img src="https://github.com/TakuSemba/Spotlight/blob/master/arts/simpleTarget.gif" align="left" width="300">

## Simple Target
simply set a title and description, these position will be automatically calculated.

```java

SimpleTarget simpleTarget = new SimpleTarget.Builder(this)
    .setPoint(100f, 340f) // position of the Target. setPoint(Point point), setPoint(View view) will work too.
    .setRadius(80f) // radius of the Target
    .setTitle("the title") // title
    .setDescription("the description") // description
    .setOnSpotlightStartedListener(new OnTargetStateChangedListener<SimpleTarget>() {
        @Override
        public void onStarted(SimpleTarget target) {
            // do something
        }
        @Override
        public void onEnded(SimpleTarget target) {
            // do something
        }
    })
    .build();

```

<br/>
<br/>
<br/>
<br/>

<img src="https://github.com/TakuSemba/Spotlight/blob/master/arts/customTarget.gif" align="left" width="300">

## Custom Target
use your own custom view.

```java

CustomTarget customTarget = new CustomTarget.Builder(this)
    .setPoint(100f, 340f) // position of the Target. setPoint(Point point), setPoint(View view) will work too.
    .setRadius(80f) // radius of the Target
    .setView(R.layout.layout_target) // custom view
    .setOnSpotlightStartedListener(new OnTargetStateChangedListener<CustomTarget>() {
        @Override
        public void onStarted(CustomTarget target) {
            // do something
        }
        @Override
        public void onEnded(CustomTarget target) {
            // do something
        }
    })
    .build();

```

<br/>
<br/>
<br/>
<br/>

### Sample
Clone this repo and check out the [app](https://github.com/TakuSemba/Spotlight/tree/master/app) module.

## Change Log

### Version: 1.0.3

  * add listener to target


### Version: 1.0.1, 1.0.2

  * bug fix

### Version: 1.0.0

  * Initial Build


## Author

* **Taku Semba**
    * **Github** - (https://github.com/takusemba)
    * **Twitter** - (https://twitter.com/takusemba)
    * **Facebook** - (https://www.facebook.com/takusemba)

## Licence
```
Copyright 2017 Taku Semba.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```

### Support:

If you want the good work to continue please support us on

* [PAYPAL](https://www.paypal.me/ishandutta2007)
* [BITCOIN ADDRESS: 3LZazKXG18Hxa3LLNAeKYZNtLzCxpv1LyD](https://www.coinbase.com/join/5a8e4a045b02c403bc3a9c0c)
