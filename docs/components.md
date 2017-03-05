In order to make things modular, it's important to start with a robust organization scheme from the beginning. The Dashberry Pi is going to be comprised of the following elements, in order of data flow:

# Data Sources
All of the data that the Dashberry Pi displays will come from data sources. Instead of attempting to encapsulate all possible primary data sources under one cohesive definition, I'll provide a couple of examples of what these are:

+ A local sensor (temperature, light, etc.)
+ Publicly available data sources (Twitter, weather, etc.)
+ Private data sources (Calendar, tasks, etc.)

# An Internal Scheduler
This will be the back-bone of the Dashberry Pi. Tasks handled by the Scheduler will include:

+ Getting data from a source (via http GET, sensor data, etc.)
+ Maintaining a clock that dictates when data will be fetched
+ Pushing that data to something (local MySQL database, hosted dashboard app, etc.)
+ Reading instructions from each module (see next section)

This will be running pretty much all the time, so it's important to make sure this has a lot of error handling sequences built in.

# Modules

