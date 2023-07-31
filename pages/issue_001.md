---
layout: page
title: Issue 001
description: x-axis proximity sensor fails to register collision
---

# Issue 001

[Go back to Home Page](https://mmider.github.io/cnc_log) | <code>&#124;</code> [Next issue](issue_002.html)

> ⚠️ This issue has been resolved prior to my decision to start documenting problems I encounter when working with my CNC machine; hence, no detailed logs, pictures nor videos exist.

## Description

During initialization of the machine, the x-axis proximity switch fails to work correctly and does not recognize the router mount approaching the x-axis maximum. As a result, the router mount rams into the x-axis max (as well as the proximity switch that is placed there), while the x-axis motor keeps churning and tries to push the mount through the immovable y-axis rail.

## Status

<span style="color:green; font-size:20px;">Resolved<sup>\*</sup></span>

<sup>\*</sup>See `Caveat` section for more details

## The underlying issue

The cables connecting the x-axis proximity switch have some minor imperfections and sometimes don't connect well. Moving them around too much may lead to the x-axis proximity switch losing its connection to the control board.

## Solution

Re-connecting the wires and moving them around a little seemed to have fixed this issue.

## Caveat

The wires remain a little finicky and they do occasinally lose the connection to the machine. To ensure that this has no effect on the milling process please verify manually before each initialization of the machine that the x-axis proximity switch works. To do this, simply place a metal plate before the proximity sensor and double check that the red LED lights up.

In the future it might become necessary to rewire the x-axis proximity switch.
