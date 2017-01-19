Alexa
=====

To use Alexe Voice Service with ReSpeaker.


### Requirements
+ CherryPy
+ Requests
+ PyAudio
+ [ReSpeaker python library](https://github.com/respeaker/respeaker_python_library)
+ webrtcvad - for Voice Activity Detection, available on ReSpeaker by default
+ PocketSphinx - for Keyword Spotting, available on ReSpeaker
+ ffplay, part of [ffmpeg](https://ffmpeg.org/download.html)


### On Ubuntu

1. [Register for an Amazon Developer Account](https://github.com/alexa/alexa-avs-raspberry-pi#61---register-your-product-and-create-a-security-profile).
2. Run `git clone https://github.com/respeaker/Alexa.git && cd Alexa`
3. Rename `example_creds.py` to `creds.py` and fill `ProductID`, `Security_Profile_Description`, `Security_Profile_ID`, `Client_ID` and `Client_Secret` with your Alexa device information.
4. Run `sudo pip install cherrypy requests pyaudio webrtcvad pocketsphinx respeaker` to get required python packages.
5. You might also need these depdencies if you got errors at the above step: `sudo apt-get install python-dev portaudio19-dev swig libpulse-dev`. Then rerun step 4.
6. Run `python auth_web.py` and open [http://localhost:3000](http://localhost:3000)

    It will redirect you to Amazon to sign in.

7. Run `python alexa.py` to interact with Alexa.


### On ReSpeaker
Alexa will be installed at the lasest firmware of ReSpeaker. If the command `alexa` is available, skip step 1.

1. Download alexa ipk and install it.

  ```
  cd /tmp
  wget https://github.com/respeaker/get_started_with_respeaker/raw/master/files/alexa_2017-01-18_ramips_24kec.ipk
  opkg install alexa_2017-01-18_ramips_24kec.ipk
  ```

2. Run `alexa` or `/etc/init.d/alexa start` to start Alexa Voice Service

3. At the first time, you need to authorize the application.

  Connect ReSpeaker's Access Point, go to [http://192.168.100.1:3000]([http://192.168.100.1:3000) and tt will redirect you to Amazon to sign up or login in.

4. Run `python alexa.py` to interact with Alexa.

>Note: if you get error `IOError: [Errno -9998] Invalid number of channels`, It's likely that `mopidy-hallo` or `alexa` is running and using the audio input channel.
>You can stop `mopidy` by running `/etc/init.d/mopidy stop`. `/etc/init.d/mopidy disable` will disable it to auto-run.
>`/etc/init.d/alexa start` will run `alexa` on background. 


### Credits
+ [AlexaPi](https://github.com/sammachin/AlexaPi).
