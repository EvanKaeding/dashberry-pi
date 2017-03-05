In order to make things modular, it's important to start with a robust organization scheme from the beginning. The Dashberry Pi is going to be comprised of the following elements, in order of data flow:

# Data Sources
All of the data that the Dashberry Pi displays will come from data sources. Instead of attempting to encapsulate all possible primary data sources under one cohesive definition, I'll provide a couple of examples of what these are:

+ A local sensor (temperature, light, etc.)
+ Publicly available data sources (Twitter, weather, etc.)
+ Private data sources (Calendar, tasks, etc.)

# Scheduler
This will be the back-bone of the Dashberry Pi. Tasks handled by the Scheduler will include:

+ Getting data from a source (via http GET, sensor data, etc.)
+ Maintaining a clock that dictates when data will be fetched
+ Pushing that data to something (local MySQL database, hosted dashboard app, etc.)
+ Reading instructions from each module (see next section)

This will be running pretty much all the time, so it's important to make sure this has a lot of error handling sequences built in.

# Modules

Each module is essentially a set of instructions that the internal scheduler reads. The module is data specific, containing instructions for each element in the dashboard such as:

+ How to access data (ex. http GET request to specific URL)
+ Any specific login credentials or instructions (access tokens)
+ Instructions for transforming the data (data cleaning, aggregation, manipulation, etc.)

# Pusher

Once the scheduler has decided that it's time to fetch some data, has read instructions from the module on how to do that and pulled down some data, it needs to do something with it. The scheduler will read instructions from the pusher that will tell it what to do with the data. The pusher will have instructions for doing some of the following:

+ Pushing data to a local/remote database
+ Posting data to a publicly accessible API
+ Pushing the data to a separate application for visualization

# Example

It's usually helpful to have a full example to help illustrate the flow of events. Here it goes:

1. Scheduler clock hits 2:00:00 UTC (example initiation time)
2. Scheduler looks for the first module on its configuration list, which happens to be a publicly available weather API
3. Scheduler reads instructions from the first module and fetches data, that may include an array of forecasted temperatures over the next 12 hours
4. Scheduler transforms data based on instructions in the module, which may be pulling out the min, max, and average
5. Scheduler pushes data by reading instructions from the pusher, which may be storing these three calculated values in a local database
6. Scheduler looks for any other modules and does the fetch, aggregate and push routine for each
7. Scheduler completes its routine and resets its initialization value to 2:15:00 UTC

