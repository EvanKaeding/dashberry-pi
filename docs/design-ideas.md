# Hardware

In vetting the idea to have a centralized Raspberry Pi dashboard to several people, the main question I've come accross is "why can't I just use my phone instead?". The short answer is, well , you can. It's really pretty easy to download, install, load and configure apps that are built by other people that will usually get you the information you need relatively quickly. With the new iOS update (at time of writing this is iOS 11) there are several new features on the 'Today' tab that actually do this.

However, my core argument in favor of the raspberry pi is that smartphones are not ideally suited for the job of providing information of this kind with a high rate of customizability. The degree to which their user interfaces can be customized is despairingly small. Their ability to run custom routines to fetch data and display it is highly limited, if not non-existant. 

Furthermore, if you want to glean data from local sensors (like temperature sensors inside your house, motion sensors in your driveway, depth sensors on your fishtank, etc.) you're at the mercy of the sensor manufacturer, hoping that they've developed an app that runs natively on your device.

---

What I like about the Raspberry Pi is that it's small, it doesn't consume much power, it comes out of the box with bluetooth, wireless 802.11 ac and HDMI, making it super easy to connect stuff to. Also, it's super affordable for the average home-hacker.

# Software

After doing some investigation and talking to other people about this project, I've decided it makes the most sense to go forward using Python as the main language for development. The key reasons are as follows:

+ Python is super easy to learn
+ It comes natively installed on Raspbian (the Raspberry Pi specific OS)
+ It's relatively lightweight
+ There are already lots of libraries out there for data connection, manipulation and aggregation in Python

I initially wanted to use R, but decided against it for the following reasons:

+ R is bulky
+ R is hard to install on Raspbian
+ R isn't exactly as user-friendly as Python

# Design Focus

When working on this project, some of the principles that should be at the forefront of thinking are:

+ Modularization
+ Customization
+ Light-weight code
+ Thorough documentation

