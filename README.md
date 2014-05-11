Android Social Networks
=====================

<p>
<img src="https://raw.githubusercontent.com/antonkrasov/AndroidSocialNetworks/master/other/asn.png" width="200px" height="200px" align="left" hspace="15px" />
Android Social Networks is library which makes working with social networks easier.
If you sometime tried to work with social networks on android you should remember that this is a hell.
You should read documentation for every social network, download SDK or use some libraries for OAuth and make
http calls by yourself. This library should makes your life easier, it contains common interface for
Twitter, LinkedIn, Facebook and Google Plus, just build SocialNetworkManager and configure your AndroidManiferst and you can login users, or post messages or photos or add / remove friends.
</p>

**Library is still in development so more features will be added soon**

  - [Features](#features)
  - [Sample Application](#sample-application)
  - [Getting Started](#getting-started)
  - [Including in your project](#including-in-your-project)
  - [Dependencies](#dependencies)
  - [Developed By](#developed-by)
  - [License](#license)

### Features

  - Login (Twitter, LinkedIn, Facebook, Google Plus)
  - Get person info (Twitter, LinkedIn, Facebook, Google Plus)
  - Post message (Twitter, LinkedIn, Facebook)
  - Post photo (Twitter, LinekdIn)
  - Check is user in your friends list (Twitter, LinkedIn)
  - Add to friends (Twitter, LinkedIn)
  - Remove from friends (Twitter)

### Sample Application

  [Download](https://dl.dropboxusercontent.com/u/80518668/asn_api_demos.apk)

### Getting started

  First of all, you need to register you application, please check this links:

- [Facebook](wiki/Facebook)  
- [Twitter](wiki/Twitter)
- [LinkedIn](wiki/LinkedIn)
- [GooglePlus](wiki/Google-Plus)

  
  Next you need to initialize **mSocialNetworkManager**. Build it with **SocialNetworkManager.Builder** and
  add to fragment manager.

```java

    mSocialNetworkManager = (SocialNetworkManager) getFragmentManager().findFragmentByTag(SOCIAL_NETWORK_TAG);

    if (mSocialNetworkManager == null) {
        mSocialNetworkManager = SocialNetworkManager.Builder.from(getActivity())
                .twitter("3IYEDC9Pq5SIjzENhgorlpera", "fawjHMhyzhrfcFKZVB6d5YfiWbWGmgX7vPfazi61xZY9pdD1aE")
                .linkedIn("77ieoe71pon7wq", "pp5E8hkdY9voGC9y", "r_basicprofile+rw_nus+r_network+w_messages")
                .facebook()
                .googlePlus()
                .build();
        getFragmentManager().beginTransaction().add(mSocialNetworkManager, SOCIAL_NETWORK_TAG).commit();
    }

```  

  Now you can execute requests, for example login request:


```java
    mSocialNetworkManager.getTwitterSocialNetwork().requestLogin(new OnLoginCompleteListener() {
        @Override
        public void onLoginSuccess(int socialNetworkID) {

        }

        @Override
        public void onError(int socialNetworkID, String requestID, String errorMessage, Object data) {

        }
    });
```  

### Including in your project

Library is still in development, so for now it's only available in staging repo.

```groovy
  repositories {
      maven {
          url "https://oss.sonatype.org/content/repositories/snapshots"
      }
  }

  compile('com.github.androidsocialnetworks:library:0.2.0-SNAPSHOT@aar') {
      transitive = true
  }
```

### Dependencies

- [support-v4](http://developer.android.com/tools/support-library/index.html)
- [Twitter4j](http://twitter4j.org/en)
- [Google Play Services](http://developer.android.com/google/play-services/index.html)
- [Facebook SDK](https://developers.facebook.com/docs/android/)
- [linkedin-j-android](https://code.google.com/p/linkedin-j/)
- [signpost-core](https://code.google.com/p/oauth-signpost/)
- [signpost-commonshttp4](https://code.google.com/p/oauth-signpost/)

##Developed By

  Anton Krasov - <anton.krasov@gmail.com>

## License

Android Social Networks is made available under the [MIT license](http://opensource.org/licenses/MIT):

<pre>
The MIT License (MIT)

Copyright (c) 2014 Anton Krasov

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
</pre>
