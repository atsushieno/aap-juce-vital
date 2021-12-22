# Vitaloid

It is our port of [Vital](https://github.com/mtytel/vital) to [aap-juce](https://github.com/atsushieno/aap-juce). Since any unofficial builds must be named otherwise than "Vital", I call it "Vitaloid" so far.

The JUCE GUI is awkward, clipped only some part of the entire UI by default. It can be "fixed" a little bit by making some build changes (described below) but that disabled audio plugin build.

![sshot/plugin](https://user-images.githubusercontent.com/53929/146757902-9cfdf8ae-f737-4cf7-96b1-72c110d72784.png)

I haven't verified my changes to various dialog changes. Probably it resulted in no useful file import/export features (anything that involves file dialog).

Note that the open source build of "Vial" (it is renamed from Vital in the official repo) contains no synth presets. We don't either (even the Basic presets from the official distribution are non-free).

## Building

There is a GitHub Actions setup that gives the normative build setup.

Once the environment is set up, `make` should take care of the entire build.

## Standalone build (local changes required)

It can run on Android as a standalone app, which shows the "right" UI, just with almost non-controllable on the small screen. Maybe somewhat useful on tablets.

![sshot/standalone](https://user-images.githubusercontent.com/53929/146684386-9233832a-54d5-466d-9d92-9f2d3878dbf3.png)

To build this version, overwrite `apps/override.vitaloid.jucer` with `apps/override.vitaloid-standalone.jucer` and run `make`.

## Licenses

aap-juce-vital is distributed under the GPLv3 license.

[mtytel/vital](https://github.com/mtytel/vital/) is distributed under the GPLv3 license.
