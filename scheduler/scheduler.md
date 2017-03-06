This will be the back-bone of the Dashberry Pi. Tasks handled by the Scheduler will include:

+ Getting data from a source (via http GET, sensor data, etc.)
+ Maintaining a clock that dictates when data will be fetched
+ Pushing that data to something (local MySQL database, hosted dashboard app, etc.)

# Configuration

The scheduler will be configured using a yaml file. A separate configuration file is preferable to hard-coded values for lots of reasons (ease of customization, ability to add a GUI config menu in the future, etc.) yaml is preferable over JSON and other config file variants because:

+ yaml is generally better for human reading
+ Although JSON is considered faster, the file contents are stored and accessed locally, so network latency is not a concern
+ yaml and Python tend to work better together due to shared indentation schemes


