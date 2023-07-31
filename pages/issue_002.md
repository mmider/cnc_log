---
layout: page
title: Issue 002
description: How to test your GitHub Pages site locally.
---

# Issue 002

[Go back to Home Page](https://mmider.github.io/cnc_log) | [Previous issue](pages/issue_001.html)

## Description

About ~50mins into a job the machine unexpectedly jerks in the x-y plane and begins to veer off the predetermined toolpath, while continuing to jerk. The video below demonstrates the problem:

<iframe src="https://drive.google.com/file/d/1PsEUrcmvjTQ_bLlyu2D_KKeDT40kh4eI/preview" width="640" height="480" allow="autoplay"></iframe>

## Status

<span style="color:aquamarine; font-size:20px;">Provisionally resolved, pending further verification</span>

## The underlying issue

The two y-axis belts were stretched under unequal tension. The right one was significantly looser. Additionally, even the left one seemed like it could have benefited from a moderate tightening. After a certain amount of time, the temperature inside the enclosure would increase to the point where the slight expansion of the machine's components would reach a tipping point and the y-axis motors would stop working as they should, violently jerking the router.

## Solution

Both y-axis belts have been tighted in such a way that they are now under approximately equal tension.

## Troubleshooting log

### The protocol

The protocol prescriped by Carbide3D customer support comprised of the following:

1. Turn the machine on.
2. Disable the `BitSetter`.
3. Let the machine sit for 1 hour.
4. Complete the [hello_world](https://my.carbide3d.com/gswso/09/) lesson.
5. Take a picture of the result.
6. Check the X-motor and X-motor extension for any build-up of heat.
7. Move around the x-motor connections looking for high-pitched squeaks.
8. Jog x-axis left and right continuously while moving the X motor and X motor extension cables.

### Slight modification

Instead of checking the temperature only at one time point I wanted to monitor it coninuously. To this end I attached 3 [DS18B20](https://www.analog.com/media/en/technical-documentation/data-sheets/DS18B20.pdf) temperature sensors:

- one to the left y-axis,
- one to the x-axis (on its right side) and
- one to the x-axis extension (on its left side).

Pictures below demonstrate this.

|                                sensor                                 |                              y-axis left                              |                            x-axis (right)                             |                        x-axis extension (left)                        |
| :-------------------------------------------------------------------: | :-------------------------------------------------------------------: | :-------------------------------------------------------------------: | :-------------------------------------------------------------------: |
| ![](https://drive.google.com/uc?id=1DOfa3IxWCZ7btQMysCZSMZus7BLurivb) | ![](https://drive.google.com/uc?id=1SnqeOw5WQXzXTeM6RpynFJrzMN_D8kkj) | ![](https://drive.google.com/uc?id=1s_ICBoP_ERVhMDL1_HVLGTEGXQ4PkhcR) | ![](https://drive.google.com/uc?id=1Cp_FedafksR-8T6HEc0sLHy110FWc9PU) |

### Temperature readings

Below is the plot of the temperature recorded during this experiment:

![day1_temp](https://drive.google.com/file/d/1Yrz0iVZgJ77V6d8EfTqXKIKUfNxmwEOc/view?usp=drive_link)

The enclosure that the router sits inside is tightly locked behind a pair of doors. I additionally turned the LEDs, as well as the router on, in order to replicate as closely as possible the conditions that were present during the actual milling process. I turned the router off before running the actual job.

### First & second tests

As 1 hour of machine sitting idly inside the enclosure passed by, I was about to start running the first test. I haven't turned any cameras on yet. I started jogging the machine and immediately it jerked violently. I do not have footage of this first occurrence.

Right after that I stopped it and tried to re-initialize it. The machine failed to initialize as it started to jerk (see video below). One door to the enclosure remained opened and after a short moment I was able to re-try the initialization and it worked. I started to run the `hello_world`. It failed quickly (see video below). I let the machine sit for a short moment again and re-tried. It managed to go through the entire `hello_world` this time; however it did fail in the middle (see video below).

<iframe src="https://drive.google.com/file/d/1qBHhqwmv5cerZmSNxJVtboIUsMaPbMMK/preview" width="640" height="480" allow="autoplay"></iframe>

After running the second test I checked the X-motor and X-motor extension for any build-up of heat, but the temperature was uniform accross the motors and can be read off exactly from the graph (it wasn't at all hot to the touch). I then move around the x-motor connections looking for high-pitched squeaks, but found nothing. Finally I jogged x-axis left and right continuously while moving the X motor and X motor extension cables, but didn't find any issues.

### Test results

Here are the results of the first and the second `hello_world` respectively:

#### First test results

![first_test_results](https://drive.google.com/uc?id=13Zv1r79ZTerflDAYrxkcRcUEEnDO-ujZ)

#### Second test results

![second_test_results](https://drive.google.com/uc?id=1P-urvrM90CZrzHcYGD11D4afgDsofo42)

### Some observations

Note that the second test reveals that on top of a violent jerk there appears to have been a constant drift in the y-plane present.

Coming back to the video of the jerk in the second test:

<iframe src="https://drive.google.com/file/d/1d4ENmxRd_B_HR0jd95IaGf51bLDE56WK/preview" width="640" height="480" allow="autoplay"></iframe>

and focusing on the y-motors one can see that something is not right with them.

This led me to examine the y-axis belts on my machine, which revealed that the right one is looser than the left one and even the left could benefit from a slight tightening:

<iframe src="https://drive.google.com/file/d/1RptdtQsOBjRGPsaUMciYRRiqOYOHyA2h/preview" width="640" height="480" allow="autoplay"></iframe>

### Fix

I tighted both belts (right one more than the left one) so that both are approximatly under the same tension.

Here they are now:

<iframe src="https://drive.google.com/file/d/1A8az_foM4EWZtYMHwkyCLiATCdf6uqNj/preview" width="640" height="480" allow="autoplay"></iframe>

### Repeat of the test

I re-run the testing protocol and it completed successfully. Here is the result (I must have set the z-axis zero a little too low and the marker was pressed to the paper a little too hard, hence the less clear lines):

![test_three_results](https://drive.google.com/uc?id=1af4ekClENjxJAgyJxujv84TvJF4XJzuj)

Additionally, the tempterature readings throughout the experiment are given below (it took place the afternoon of the following day; hence the apparent jump back in time):

![day2_temp](https://drive.google.com/uc?id=1fmfHuMDDq2f08WFsJJ9py9rjY5TehBVU)

The jerking appears to be resolved.
