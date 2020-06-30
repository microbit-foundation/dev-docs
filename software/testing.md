---
layout: page
order:
title: Beta testing
heading: Beta testing apps and Editors  
description: How to access beta versions of the micro:bit editors and apps
permalink: /software/beta/
ref: software
lang: en
---

* TOC
{:toc}

This page details the ways in which you can test the micro:bit hardware with the various software environments.
The information applies to all board revisions, but specifics for the latest (v2) revision are noted here.

Within the technical reference we may refer to the version number of the board, 

Features on new revision 

- Microphone and LED indicator
- Speaker
- Face touch

## How do I use the new features?

The **speaker** works in the same way you would expect when you connect up your headphones or an external speaker to the micro:bit and you can control the volume of the speaker in your program. 
The **microphone** has an additional set of blocks in MakeCode and classes in MicroPython to use, so that you can monitor and record sound. 
The **face touch** is implemented in the same way as touching a pin.


## Will my saved hex files work with the new board?

Yes, however you will need to update the files by dragging and dropping them into the software editor in which they were created.


----------
# Hardware

**How do I get a device to test?**

If you haven’t already received a device, but would like one in order to test/develop an accessory or editor please contact us at [support@microbit.org](mailto:support@microbit.org)

----------
# Software

## Makecode Editor

You can use the latest board revision in the beta editor at  [https://makecode.microbit.org/beta?compile=multiVariant](https://makecode.microbit.org/beta?compile=multiVariant)

A file downloaded in this editor will work on any micro:bit.

If you try to add an extension to your program, that is not supported in either the latest revision or previous revisions of the board, the micro:bit will throw an error. This will take the form of a single ‘blinking’ LED on the screen. If you are an accessory maker or extension author

**multivariant Bookmark**
You can force the beta editor into multivariant mode with this bookmark:

1. In Chrome go to makecode.microbit.org/beta#editor
2. Paste  this into the URL bar
    (function(){localStorage["compile"]="multiVariant";})()
3. Prepend the statement with javascript and press return
    javascript:(function(){localStorage["compile"]="multiVariant";})()
4. Reload the editor
5. Test downloading a file. It should be ~1.8Mb as opposed to ~700Kb

## Python Editor

TBC

## Mu

Mu may not have been updated in time for new micro:bit variant devices entering the market, so it may be the case that you need to:

- Flash the micro:bit with the latest version of MicroPython
- The Flash, Files and REPL button should just work (This is because files are transferred via serial)
- In the odd case that an error is encountered within Mu, it will try to reflash MicroPython
    - This would try to use the built-in version of MicroPython, which wouldn't work on a v2 board, however there is a version check at this point, so instead it will just display an error indicating that you have a newer board version than Mu can support.

## Classroom

To test a specific editor version, classroom allows us to pass the URL of the editor e.g. 

**Makecode**
You can use this to specify a MakeCode version as used in their URL
paths (e.g. v2.2.4 or beta). 
https://classroom.microbit.org/?editorVersion=beta
You can also use the [+v2 testing info pack: multivariant-Bookmark](https://paper.dropbox.com/doc/v2-testing-info-pack-multivariant-Bookmark-suquZ9PBQPwOLkKG0OEab#:h2=multivariant-Bookmark) to force the editor version.

1. Open MakeCode and add the bookmark.
2. Go to classroom and setup a MakeCode session, the iFrame will then pull in the multivariant version

**Python**
For Python you can use 2.1.0-beta-3 (it makes a very big assumption and
maps to the python-editor-${versionMunged}.microbit.org)
TBC with Edu team and @Matt H 

## iOS App

The iOS App TestFlight/beta has a hidden option that enables you to input the makecode version URL eg  [https://makecode.microbit.org/beta?compile=multiVariant](https://makecode.microbit.org/beta?compile=multiVariant)

To test, you will need to:


1. Provide your **Apple ID email address** to support@microbit.org.
2. Have an **iOS device with the** [**TestFlight**](https://testflight.apple.com/) **app installed**

You will be notified via email when you have been added to the TestFlight and the app will appear as an option to install within the TestFlight app.

When you open the app, tap on the word ‘beta’ in the top right of the screen. This will open a dialogue for you to enter in the URL suffix [beta?compile=multiVariant](https://makecode.microbit.org/beta?compile=multiVariant). Pressing enter will reload the editor at this URL.

## Android App

Android users will need an Android device and provide their Google Account that they use for the Play Store. Mark will add them in via this email address.

## Windows App

TBC

## Offline App

TBC

## Swift Playgrounds

TBC


## Scratch

TBC


## Compiling in C++ (CODAL)

These are the current CODAL build instructions  This is likely to be replaced by a Yotta build as with the DAL.

**Instructions for building**

    git clone https://www.github.com/microbit-foundation/codal
    cd codal
    python build.py

If this fails, for example because you're using GH 2FA and https, then you need to manually fetch all repos:


    cd libraries/
    ls
    git clone git@github.com:microbit-foundation/codal-core.git
    git clone git@github.com:microbit-foundation/codal-microbit-next.git
    git clone git@github.com:microbit-foundation/codal-mbedos.git
    git clone git@github.com:microbit-foundation/codal-nrf52.git
    ls # You should have the four directories now
    cd codal-core/
    git checkout nrf52833-mbedos
    cd ../
    cd codal-mbedos/
    git checkout nrf52833-bringup-includes 
    cd ../
    cd codal-nrf52/
    git checkout nrf52833-mbedos
    cd ../
    cd codal-microbit-next/
    git checkout nrf52833-mbedos
    cd ../../

If your build failed the first time
    rm -rf ./build
Verify you are where you think you are and everything's at the right branch
    python build.py -s #s is for status
    python build.py

**Troubleshooting**
If your build fails with missing toolchain, remove the build dir and try again. This usually happens if the first attempt to run build.py fails and we don't check out all the relevant libraries (often due to GH permissions)

If you get include issues, ensure you're on the right branch for codal-mbedos (listed above)

