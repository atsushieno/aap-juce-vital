# Vitaloid!

It is an ongoing port of [Vital](https://github.com/mtytel/vital) to [AAP](https://github.com/atsushieno/android-audio-plugin-framework). Since any unofficial builds must be named otherwise than "Vital", I call it "Vitaloid" so far.

It runs on Android as a standalone app, just with almost not controllable UI on the small screen and probably no useful file import/export features (anything that involves file dialog).

And as an AAP it still crashes, due to lack of juceaap module in the build. It will be fixed soon.

![sshot](https://user-images.githubusercontent.com/53929/146684386-9233832a-54d5-466d-9d92-9f2d3878dbf3.png)


## updating metadata

Vital has somewhat tricky project structure and normal aap-juce plugin setup does not work. AAP build is based on `standalone/vital.jucer` while `aap_metadata.xml` generator is based on `plugin/vital.jucer`. Here is the command I set up in Makefile and aap-juce to get `update-aap-metadata` task working:

> make VITAL_UPDATE_METADATA=1 update-aap-metadata
