---
layout: default
---

# Basic Tools
---
Tools such as SSH, Netcat, Tmux, and Vim are essential and are used daily by most information security professionals. Although these tools are not intended to be penetration testing tools, they are critical to the penetration testing process, so we must master them.

In this exercise we are asked to extract the flag using the tools that we have been taught in this section, in this case we will use the NetCat tool to extract the flag to solve the exercise.

![NetCat command!](/assets/images/BasicTools/01.png "NetCat command to extract the service version from the specified port.")

>Command structure:
>
>``netcat [TargetIP] [Port]``

As we can see in the screenshot we use the NetCat tool putting the IP that we want to attack together with the port we want to access so that it gives us as output the version and the service that is using.

[Back to exercises section](../GettingStarted.md)
