# Vitaloid

It is our port of [Vital](https://github.com/mtytel/vital) to [aap-juce](https://github.com/atsushieno/aap-juce). Since any unofficial builds must be named otherwise than "Vital", I call it "Vitaloid" so far.

(Note that the open source build of "Vial" - it is renamed from Vital in the official repo - contains no synth presets. We don't either. Even the Basic presets from the official distribution are non-free.)

## Development Status

The JUCE GUI is somewhat awkward; basically, reusing the desktop UI on mobile is not a good idea, and for Vital the UI is almost not controllable by fingers.

![sshot](https://user-images.githubusercontent.com/53929/147199726-c0b49d89-e1d0-494a-aa2c-895d63b5d11e.png)

Some UI components are clipped, and anything that involved a file dialog on desktop could result in weird behavior or weird rendering.

Current build replaces vital's JUCE modules with JUCE 6.1.4, then patch the changes made in vital repo (explained at "Hacking" section).

## Building

There is a GitHub Actions setup that gives the normative build setup.

Once the environment is set up, `make` should take care of the entire build.

## Standalone build (less JUCE changes involved)

It can run on Android as a standalone app, which shows the "right" UI, just with almost non-controllable on the small screen. Maybe somewhat useful on tablets. This works even without replacing JUCE modules.

![sshot/standalone](https://user-images.githubusercontent.com/53929/146684386-9233832a-54d5-466d-9d92-9f2d3878dbf3.png)

To build this version, overwrite `apps/override.vitaloid.jucer` with `apps/override.vitaloid-standalone.jucer` and run `make`.

## Hacking

### Upgrading to JUCE to 6.1.4 (or any later versions)

vital comes with its own version of JUCE in `third_party/JUCE` which is based on some version around JUCE 6.0.5, stripping out any extraneous bits.

To make it possible to upgrade JUCE versions, first I created a diff between JUCE 6.0.5 and vital: https://gist.github.com/atsushieno/158b40759b01c7d70c60a682620277e9

If you want to use later versions of JUCE, you might want to first patch the diff above against the target JUCE tree, then copy the required modules into `third_party/JUCE/modules/`.

Note that there could be breaking changes that breaks vital builds. For example JUCE 6.1.0 broke build by requiring `using namespace juce::gl;` explicitly. (The change is in our `vitaloid-aap.patch` so that you don't have to worry about this particular breakage.)

## Licenses

aap-juce-vital is distributed under the GPLv3 license.

[mtytel/vital](https://github.com/mtytel/vital/) is distributed under the GPLv3 license.
