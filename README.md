# SoundCloud for Processing
Library to use the [SoundCloud API](https://developers.soundcloud.com/docs/api/guide) in [Processing](http://processing.org/).


## Table of Contents

- [Download](#download)
- [Installation](#installation)
- [Dependencies](#dependencies)
- [Tested](#tested)
- [Usage](#usage)
- [Questions?](#questions)
- [License](#license)


## Download

- [SoundCloud for Processing](download/SoundCloudForProcessing.zip?raw=true)


## Installation

Unzip and put the extracted *SoundCloudForProcessing* folder into the libraries folder of your Processing sketches. Reference and examples are included in the *SoundCloudForProcessing* folder. For more help read the [tutorial](http://www.learningprocessing.com/tutorials/libraries/) by [Daniel Shiffman](https://github.com/shiffman).


## Dependencies

- [SoundCloud Java library](https://github.com/voidplus/soundcloud-java-library) (It's included internally.)


## Tested

System:

- **OSX** (*Mac OS X 10.7 and higher - tested with Mac OS X 10.10 Yosemite*)
- **Windows** (*not tested yet, but x86 and x64 should work*) (*Windows 7 and 8*)

Processing version:

- **2.2.1**


## Usage

I recommend to use the library with [Minim](http://code.compartmental.net/tools/minim/) ([GitHub](https://github.com/ddf/Minim)). It uses JavaSound to provide an easy-to-use audio library while still providing flexibility for more advanced users.

```java
import de.voidplus.soundcloud.*;
import ddf.minim.*;

SoundCloud soundcloud;
Minim minim;
AudioPlayer player;

void setup(){
  
  // http://soundcloud.com/you/apps for APP_CLIENT_ID and APP_CLIENT_SECRET
  soundcloud = new SoundCloud("APP_CLIENT_ID", "APP_CLIENT_SECRET");
  
  // If you need any permissions:
  // soundcloud.login("LOGIN_NAME", "LOGIN_PASS");
  
  // show user details
  User me = soundcloud.get("me");
  println(me);
  
  // play the first track of search
  ArrayList<Track> result = soundcloud.findTrack("Chromatics");
  if(result!=null){
    println("Tracks: "+result.size());

    minim = new Minim(this);  
    player = minim.loadFile(result.get(0).getStreamUrl());
    player.play();
  }
  
  minim = new Minim(this);
}

void draw(){}

void stop(){
  player.close();
  minim.stop();
}
```


## Questions?

Don't be shy and feel free to contact me via [Twitter](http://twitter.voidplus.de).


## License

[MIT License by SoundCloud](https://raw.github.com/soundcloud/java-api-wrapper/master/LICENSE). The Processing library is Open Source Software released under the [MIT License](MIT-LICENSE.txt). It's developed by [Darius Morawiec](http://voidplus.de).