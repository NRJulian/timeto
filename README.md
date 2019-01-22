# timeto
A simple Linux/Unix command to output the time till a specified date or event, with various output formatting options.

# Installation
Simply copy the script file (`timeto`) to `/usr/local/bin` or another directory specified in your system's path.

# Usage
```
$ timeto [OPTIONS] [EVENT_NAME | DATE]
```
You can easily use timeto with just a date, like so:
```
$ timeto 01-01-2025
2170 days, 9 hours, 2 minutes and 33 seconds until 2025-01-01
```
This will give you a detailed report of the time time until New Year's Day, 2025. timeto also keeps a file of user-specified events for quick access. Use the `-a` option (with an event name and date) to add an event to the database:
```
$ timeto -a x-mas 12-25-2025
Added x-mas (2025-12-25) to events list.
```
After adding an event to the database, you can use timeto with just the event name:
```
$ timeto x-mas
2528 days, 8 hours, 59 minutes and 18 seconds until x-mas
```
Use the `-r` option with just an event name to remove the event from the database:
```
$timeto -r x-mas
Clear x-mas from events list? [y/n] y
x-mas removed from events list.
```

# Formatting Output
Run with no options, timeto will give you a full, formatted report of the time until a day:
```
$ timeto 12-25-2019
336 days, 9 hours, 33 minutes and 54 seconds until 2019-12-25
```
Use the `-s`,`-m`,`-o` or `-d` option to specify only seconds, hours, minutes or days. This will give you the *number only* to facilitate piping and interoperability with command-line tools and scripts:
```
$ timeto -d 12-25-2019
336
```
Use the `-v` (verbose) option with `-s`,`-m`,`-o` or `-d` to specify just seconds, minutes, hours or days but also format it:
```
$ timeto -d -v 12-25-2019
336 days until 2019-12-25
```

# Full Options
```
-a [EVENT_NAME] [DATE]              Create an event in the database. Names
                                    are case sensitive and cannot contain  
                                    spaces. Date may be specified as       
                                    YYYY-MM-DD, MM-DD-YYYY, or MM.DD.YYYY. 
                                    (example: timeto -a xmas 2018-12-25)  
-c                                  Clear all events in the database      
-l                                  List all events in the database       
-r [EVENT_NAME]                     Remove event from the database        
-f                                  Show full report (days, hrs, min, sec)
-d                                  Show days until day of event          
-o                                  Show hours until day of event         
-m                                  Show minutes until day of event       
-s                                  Show seconds until day of event       
-v                                  Verbose output: used with -d,-o,-m,-s 
-h                                  Show help                             	
```
