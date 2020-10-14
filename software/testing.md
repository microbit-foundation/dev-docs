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

## Software

### Makecode Editor

You can use the beta editor at [https://makecode.microbit.org/beta](https://makecode.microbit.org/beta)

A file downloaded in this editor will work on any micro:bit.

If you add an extension to your program that is not supported in either the latest revision or previous revisions of the board, the micro:bit will throw an error.

### Python Editor

You can use the Python beta editor at [https://python.microbit.org/v/beta](https://python.microbit.org/v/beta)

If you find direct browser flashing (webUSB) isn't working, it is likely that you are visiting the page with the http protocol. We currently do not have https redirection enabled.

### iOS App

The iOS App beta is released via Apple TestFlight.

To test, you will need to:

1. Provide your **Apple ID email address** to support@microbit.org.
2. Have an **iOS device with the** [**TestFlight**](https://testflight.apple.com/) **app installed**

You will be notified via email when you have been added to the TestFlight and the app will appear as an option to install within the TestFlight app.

To switch to the beta editor within the app:

1. Select **Create Code** to open the MakeCode editor
2. Press and hold the micro:bit logo to open the drop-down menu
3. Toggle the button for **Use Beta version** to reload the editor in beta.

![iOS beta button](/docs/software/assets/ios-beta-button.png)

### Android App

The Android app has a hidden option that enables you to input the makecode version URL eg  [https://makecode.microbit.org/beta](https://makecode.microbit.org/beta)

To test, you will need to:

1. Provide your **Google Account email address** to support@microbit.org.
2. Have an **Android device with the** [micro:bit Android app](https://play.google.com/store/apps/details?id=com.samsung.microbit) installed

You will be notified via email when a beta of the app is made available, with a link to sign up as a beta tester, and the app will update itself.

When you open the app, tap and hold on the micro:bit logo.

![Android beta url](/docs/software/assets/android-beta-url.png)

This will open a dialogue for you to enter in the URL. The next time you tap **Create code** the editor will open at your chosen version.

### Mu

The [Mu](https://codewith.mu/) editor releases are available on the [Mu download page](https://codewith.mu/en/download). If you want to test an updated or custom version of MicroPython, you can do so in the following way:

1. Flash the micro:bit with the version of MicroPython you want to test.
2. Click the **REPL** to communicate with the board directly via serial.
3. To download a python file to the microbit, Click on **Save** and then click on the **Files** button.
4. Copy `main.py` from the Files on your computer to the Files on your micro:bit

![Copy main.py](/docs/latest-revision/assets/copy-main-py-mu.gif){: width="600"}
