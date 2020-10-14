---
layout: page
title: Working together on the latest BBC micro:bit
heading: Introducing the latest BBC micro:bit
description: As we announce the latest micro:bit we invite you to learn about the device and join us to make incredible things with it.
permalink: /latest-revision/announcement/
ref: latest-revision-announcement
lang: en
---

## micro:bit V2

Today we’re [announcing a new version of the BBC micro:bit](https://microbit.org/new-microbit/), adding a speaker, a microphone and the CPU power to run AI and Machine Learning workloads. With these additional capabilities, we are opening up the world of AI and ML to the same collaborative design and innovation that led to the original micro:bit’s success. 

This article is a more technical companion to the [news over at microbit.org](https://microbit.org/new-microbit/). 

![micro:bit v2 image](/docs/latest-revision/assets/blog/microbit-v2-tech-site.png){: width="600"}  

Although the latest micro:bit isn’t available to buy yet, we’re talking about it now because the micro:bit isn’t about one organisation, or the official editors, or even one device.

The micro:bit stands out as unique because of the collaborative way in which it was developed. [It is a tool carefully engineered by an interdisciplinary partnership](https://microbit.org/impact/case-studies/milestones-for-the-bbc-microbit/) of organizations to engage a diverse range of students and meet the needs of teachers and learners in the classroom.

This innovative device is highly accessible, easy to program, instantly interactive, and beautiful. It kicked off a wave of innovation in educational technology. Five years after its launch, the micro:bit is one of the best-loved tools for teaching computational thinking for young people aged 8-15: five million micro:bits are now in use by an estimated 25 million teachers and students around the world.

By making affordable, developer-quality hardware and creating elegant and simple ways for students to use it, we can help create a generation that understands how transformative technologies like AI and ML are shaping the world around them.

## Working in partnership

The many voices that have come together to create the micro:bit experience are key to its success in attracting a diverse range of people to engage with and embrace technology.

It’s in that same spirit of partnership and collaboration that we’ve worked to evolve the device and create the [latest micro:bit](/latest-revision/), laying the foundations for years more digital exploration while maintaining the stability and reliability that have helped people around the world depend on the device as a core part of their teaching.

At the Micro:bit Educational Foundation we are working with Lancaster University, Microsoft, NXP, and MicroPython to ensure that the core micro:bit experience is as creative, compelling and consistent as it’s ever been. But launching a new micro:bit wouldn't be complete without the input of the incredible community of editor authors, accessory providers, content authors and supporters of micro:bit.

## We’re building this together, not alone

![A wall of micro:bit accessories](/docs/latest-revision/assets/blog/accessory-wall-bett.jpg){: width="600"}
*The wall of accessories displayed at BETT*

We recognise and support the huge contribution the wider micro:bit ecosystem makes to our community, and so we are making available all [key technical information about the new micro:bit](/latest-revision), and open source tools to make it easy to support in advance of the device being available to users.

We’ve compiled all this information on an updated version of tech.microbit.org, including details of how to get advanced access to a device if you need one to test or develop something.

- [All the technical details about the latest micro:bit and how to use it](/latest-revision)
- Advice on supporting the device for:
    - [accessory makers](/latest-revision/accessories/) (including information on how [MakeCode Arcade will be supported](/latest-revision/accessories/#makecode-arcade))
    - [content authors](/latest-revision/content/)
    - [editor developers](/latest-revision/editors/)

## Creating code for the latest micro:bit

The latest micro:bit supports all features of the original version so there are many cases where a user won’t need to distinguish between the devices; every tutorial or programme that already exists today is supported on the latest hardware. However, as the machine code that runs on the two devices is different, the latest micro:bit supports a new kind of hex.  We’re calling it ‘[universal hex](/software/hex-format/)’: this contains the machine code for both versions of the micro:bit. Thanks to the fantastic support of NXP who have worked on [DAPLink](https://github.com/ARMmbed/DAPLink), the Arm project that enables the micro:bit USB interface, the latest micro:bit is able to choose which code it should use from the universal hex. The files are designed so the original micro:bits do not need any update to use them.
![Creation of a Universal Hex](/docs/latest-revision/assets/blog/uhex2.png)

To make the experience of developing programs for these universal hexes as seamless as possible we’ve deepened our collaboration with Arm, Lancaster University and [Microsoft Research](https://www.microsoft.com/en-us/research/project/the-bbc-microbit-and-microsoft/), who were [co-creators of the original micro:bit,](https://www.lancaster.ac.uk/news/articles/2016/lancaster-university-helps-bbc-get-kids-coding/). Because of the open source nature of [Lancaster’s CODAL](https://github.com/lancaster-university/codal), the evolution of the original microbit-dal, we had a ready platform to make the latest micro:bit work. We have also included a full compatibility layer for [microbit-dal](https://github.com/lancaster-university/microbit-dal), so that existing projects and environments can be easily recompiled to work on the latest board. On top of the careful compatibility work there’s plenty of exciting new features designed for the latest hardware, like an advanced SoundExpressions synthesiser and audio pipeline architecture. 
![micro:bit Software Architecture with CODAL](/docs/latest-revision/assets/blog/software-overview-v2.svg){: width="600"}

MakeCode, MicroPython and Scratch are using CODAL to support the new device, and we recommend that anyone building software to run on the micro:bit do the same to ensure consistent experience across micro:bit editors. This will also ensure that as new features get added they can be incorporated easily and made available to users (it’s easy to forget that micro:bit radio wasn’t in the original micro:bit release!)

## Raising the roof

When it launched in 2015, one of the key goals of the original micro:bit was to create something that was highly capable but with an instant interactivity and ease of access that engaged new audiences. We’ve always aimed for a “low floor and a high ceiling”: it must be super easy to get started, and you shouldn’t hit any barriers as your projects get more complex and grow beyond the device itself.

Part of ensuring this was putting the same hardware that real developers were using at the time into the hands of students. This is what has enabled some of the more incredible uses of the micro:bit: [Handwriting recognition using an optical mouse sensor](https://www.cs.ox.ac.uk/teaching/studentprojects/630.html); [use in a BLE mesh](https://docs.zephyrproject.org/latest/samples/bluetooth/mesh_demo/README.html), a [presentation remote](https://os.mbed.com/teams/microbit/code/microbit_presenter/), or a [custom piece of assistive technology.](https://hackaday.io/project/26143-handshake) 

![Creation of a Universal Hex](/docs/latest-revision/assets/blog/nrf52833.jpg){: width="600"}

With the latest micro:bit, we’re doing this again: the [nRF52833](https://www.nordicsemi.com/Products/Low-power-short-range-wireless/nRF52833) is a modern, exciting part recently released by Nordic, and being used across the industry for new designs. It’s capable of running machine learning workloads, and so opens up a new realm of possibilities, both for applications of the device, but especially for helping to expose and demonstrate what machine learning really is: not magic, but sufficiently advanced application of technology.

The original micro:bit elegantly demonstrated the technology in a phone (the screen, buttons, wireless communication, motion sensors, all driven by a processor) and helped young people feel confident that they could understand and control these devices. The new BBC micro:bit extends the capabilities of the hardware to include making and responding to sound, helping demystify the latest wave of consumer technologies including AI smart speakers and digital assistants. 

## New creative possibilities

Music and sound on the micro:bit were pioneered in MicroPython as part of the original community effort around the BBC micro:bit – not least thanks to Nicholas Tollervey and Mark Shannon for introducing things like the [speech synthesizer](https://www.nordicsemi.com/Products/Low-power-short-range-wireless/nRF52833)! Now with the addition of a speaker to the latest micro:bit it is really coming into its own. If you connect headphones or an amplified speaker, you get even better quality sound. Just as the 5x5 display on the micro:bit is perfect for getting started, but a colour LCD is still a welcome way to extend your projects, the sound driver written by Lancaster University is capable of reproducing high quality sound on the edge connector. We don’t expect to see the end of crocodile clips connecting headphone jack sockets just yet!

![micro:bit guitar](/docs/latest-revision/assets/blog/microbit-guitar.jpg){: width="600"}

But beyond music, sound is the way many of us communicate. Our voice and our accent is part of our identity and personality. When adding ‘sound’ as a feature of the micro:bit we wanted to make sure we gave it a personality too. The careful thought put into the visual and structural elements of the micro:bit, led by Technology Will Save Us in 2015 showed how paying careful attention to design of a device had a huge impact its approachability, and the ease with which people could make an emotional connection to hardware. The sounds for the micro:bit learn from this, and are there to make the micro:bit’s voice friendly and approachable. We’ve been working on a synthesiser to make these amazing sounds, with lots of input from a sound designer to tune it and make it useful.

The microphone, like the microphones on a smart speaker or digital assistant, allows the device to respond to sound and sense the noise around the micro:bit. Paired with the greater capability of the new micro:bit this is opening up fantastic potential around AI and machine learning with sound. Exemplifying the thought given to educational environments, the microphone’s dedicated ‘operating’ indicator doesn’t interfere with the visual design of the board when off, but makes it clear when the microphone is on and sensing sound. This allows teachers to engage with students about privacy issues and the impact of listening devices.

## Exploring AI and ML

![Tensorflow Logo](/docs/latest-revision/assets/blog/tensorflow-logo.png){: width="300"}

Within days of getting a device, Gordon Williams, lead developer of [Espruino](https://www.espruino.com/) had the micro:bit supported in their online platform. This allowed JavaScript programs to run on the device, including Espruino’s gesture recognition libraries that were originally designed for bangle.js and use Tensorflow Lite. Unlike the "gestures" you might be used to on the micro:bit, like "shake", this demo allows you to train a machine learning model to recognise any gestures you can collect data for - it takes recordings of the gestures being performed, and builds a model that can recognise them. This means you can have much more complex, subtle gestures, and even customise them for yourself or something you’ve attached the micro:bit to.

[Edge Impulse](https://www.edgeimpulse.com/), working similarly fast, took a video recording of each member of the micro:bit team saying “micro:bit” three times (what better way to conclude the weekly team meeting?) and used the Edge Impulse cloud service to create a model that could recognise the word “micro:bit” being said. [You can read more about this demo here](https://www.edgeimpulse.com/blog/voice-activated-microbit), but it clearly shows the possibility of training micro:bits to recognise unique sounds!

![Edge Impulse visualisation](/docs/latest-revision/assets/blog/edge-impulse.png)

## What’s next?

There’s much more about the new device to explain and explore, and we’ll be expanding on the technical documentation as well as the available code over the next few days (weeks, months and years, too, I’m sure!) Much of the magic of the micro:bit is in the seamless way that all the features are easily accessible and can co-exist: you can use capacitive touch, and the microphone, and the edge connector, and still go into low power sleep, and there’s lots to share about how that’s been made possible. As CODAL grows for micro:bit v2 we expect to provide the same easy composition for the core aspects of machine learning and sound.

With so much speculation and often misunderstanding about the possibilities, risks and complexities of AI/ML we believe that the micro:bit device can bring the same transformative simplicity to the teaching of these concepts that it brought to physical computing and computational thinking. This isn’t something we can do overnight though. Now the device is launched we’re starting the process of collaboration with universities, industry, schools and makers to make this transformational experience a reality. The demos we have today show just some of what the new hardware can do. We’re confident that the latest micro:bit will empower young people to understand and eventually re-shape the inner workings of the intelligent systems and algorithms that have an increasing impact on their lives.

Now is the time to come and engage again with micro:bit and help build the next phase of the project with us.
