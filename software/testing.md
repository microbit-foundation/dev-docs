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
## Overview

* TOC
{:toc}

This page details the ways in which you can test the micro:bit hardware with the various software environments.
The information applies to all board revisions, but specifics for the latest <span class="v2">v2</span> revision are noted here.

<span class="v2">v2</span>Features

- Microphone and LED indicator
- Speaker
- Face touch

<span class="v2">v2</span>Refinements

- Notched edge connector
- Power LED indicator and USB activity indicator
- Matte finish
- Copper plated antenna

## How do I use the v2 features?

The **speaker** works in the same way you would expect when you connect up your headphones or an external speaker to the micro:bit. By default, the sound output will be via the Edge Connector and the speaker.
The **microphone** has an additional set of blocks in MakeCode and objects in MicroPython to use, so that you can monitor and record sound. 
The **logo touch** is implemented in the same way as touching a pin on the edge connector and will have equivalent blocks in MakeCode and objects in MicroPython to use.

To access the features of the latest revision only (eg. to output sound only on the speaker and not the edge connector), you will need to add additional code to your programs. This ensures that the default editor experience continues to work for everyone, regardless of the board revision.


## Will my saved hex files work with the latest board revision?

Yes, however you will need to update the files by dragging and dropping them into the software editor in which they were created.

If you attempt to use an old .Hex file without updating it, the micro:bit will display a compatibility error `:( E029`

![Compatibility error](/docs/software/assets/compat-error.gif)

----------
# Hardware

**How do I get a device to test?**

If you haven’t already received a device, but would like one in order to test/develop an accessory or editor please contact us at [support@microbit.org](mailto:support@microbit.org?subject=Request%20for%20the%20latest%20micro%3Abit&body=Name%3A%0D%0A%0D%0AAddress%3A%0D%0A%0D%0AContact%20number%3A)

----------
# Software

## Makecode Editor

You can use the latest board revision in the beta editor at  [https://makecode.microbit.org/beta?compile=multiVariant](https://makecode.microbit.org/beta?compile=multiVariant)

A file downloaded in this editor will work on any micro:bit.

If you try to add an extension to your program, that is not supported in either the latest revision or previous revisions of the board, the micro:bit will throw an error. This will take the form of a single ‘blinking’ LED on the screen. If you are an accessory maker or extension author

### multiVariant Bookmarklet
You can force the beta editor into multivariant mode with this bookmarklet:

1. In Chrome go to makecode.microbit.org/beta#editor
2. Paste  this into the URL bar
    (function(){localStorage["compile"]="multiVariant";})()
3. Prepend the statement with javascript and press return
    javascript:(function(){localStorage["compile"]="multiVariant";})()
4. Reload the editor
5. Test downloading a file. It should be ~1.8Mb as opposed to ~700Kb

### v2 only (CODAL)
If you only want to compile for the <span class="v2">v2</span> revision, you can use https://makecode.microbit.org?compile=csv---mbcodal#

## Python Editor

You can use the latest board revision in the Python beta editor at [https://python-editor-next-release-review.microbit.org/](https://python-editor-next-release-review.microbit.org/)

If you find direct browser flashing (webUSB) isn't working, it is likely that you are visiting the page with the http protocol. We currently do not have https redirection enabled.

## Mu

Mu may not have been updated in time for new micro:bit variant devices entering the market, so it may be the case that you need to:

- Flash the micro:bit with the latest version of MicroPython
- The Flash, Files and REPL button should just work (This is because files are transferred via serial)
- In the odd case that an error is encountered within Mu, it will try to reflash MicroPython
    - This would try to use the built-in version of MicroPython, which wouldn't work on a v2 board, however there is a version check at this point, so instead it will just display an error indicating that you have a newer board version than Mu can support.

## iOS App

The iOS App TestFlight/beta has a hidden option that enables you to input the makecode version URL eg  [https://makecode.microbit.org/beta?compile=multiVariant](https://makecode.microbit.org/beta?compile=multiVariant)

To test, you will need to:

1. Provide your **Apple ID email address** to support@microbit.org.
2. Have an **iOS device with the** [**TestFlight**](https://testflight.apple.com/) **app installed**

You will be notified via email when you have been added to the TestFlight and the app will appear as an option to install within the TestFlight app.

When you open the app, tap on the word ‘beta’ in the top right of the screen. 

![iOS beta button](/docs/software/assets/ios-beta-button.png)

This will open a dialogue for you to enter in the URL suffix [compile=multiVariant](https://makecode.microbit.org/beta?compile=multiVariant). Pressing enter will reload the editor at this URL.

![iOS beta URL](/docs/software/assets/ios-beta-url.png)

## Android App

The Android app has a hidden option that enables you to input the makecode version URL eg  [https://makecode.microbit.org/beta?compile=multiVariant](https://makecode.microbit.org/beta?compile=multiVariant)

To test, you will need to:

1. Provide your **Google Account email address** to support@microbit.org.
2. Have an **Android device with the** [micro:bit Android app](https://play.google.com/store/apps/details?id=com.samsung.microbit) installed

You will be notified via email when a beta of the app is made available, with a link to sign up as a beta tester and the app will update itself.

When you open the app, tap and hold on the micro:bit logo.

![Android beta url](/docs/software/assets/android-beta-url.png)

This will open a dialogue for you to enter in the URL. The next time you tap **Create code** the editor will open at your chosen version.

## Windows App

TBC

## Offline App

TBC

## Swift Playgrounds

TBC


## Scratch

TBC


## Compiling in C++ (CODAL)


