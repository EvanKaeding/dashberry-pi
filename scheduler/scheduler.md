This will be the back-bone of the Dashberry Pi. Tasks handled by the Scheduler will include:

+ Getting data from a source (via http GET, sensor data, etc.)
+ Maintaining a clock that dictates when data will be fetched
+ Pushing that data to something (local MySQL database, hosted dashboard app, etc.)

# Configuration

The scheduler will be configured using a JSON file. A separate configuration file is preferable to hard-coded values for lots of reasons (ease of customization, ability to add a GUI config menu in the future, etc.) JSON is preferable over yaml and other config file variants because:

+ JSON is ubiquitous
+ JSON is light and fast
+ JSON is human readable
+ We don't really need any of the specialized functionality associated with yaml files (serializing native arbitrary data structures)


