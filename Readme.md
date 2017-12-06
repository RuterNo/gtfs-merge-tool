# Ruter GTFS Merge Script 
This Maven project is just configuration for running onebussaway gtfs merge tool. 

To run it, use:
```
  $ export MAVEN_OPTS=-Xmx2048M 
  $ mvn package -DinputFiles=../files -DresultDir=../result
```

The merge tool execution is part of the Maven lifecycle phase `package`. 


## Script parameters 
The script need to know where the GTFS input is and where to put the result. These args are passed into Maven using 
Maven properties.
### inputFiles
```
-DinputFiles=[<rootDir>|<fileList>]
```
If the `inputFiles` is set to one directory with subdirectories those directories are passed into the merge tool - not 
the directory it self. Subdirectories starting with `.` is ignored.

If `inputFiles` is set to a list of directories those directories are passed into the merge tool.

Given the following directory structure:
```
  |-- gtfsmergetool
  |-- result
  +-- input
    |-- bra
    | |-- agency.txt
    | |-- calendar.txt
    | |-- calendar_dates.txt
    | |-- feed_info.txt
    | |-- routes.txt
    | |-- stop_times.txt
    | |-- stops.txt
    | +-- trips.txt
    +-- rut
      |-- agency.txt
      |-- calendar.txt
      |-- calendar_dates.txt
      |-- feed_info.txt
      |-- routes.txt
      |-- stop_times.txt
      |-- stops.txt
      +-- trips.txt

```
the following 2 command give the same result:
```
  # In directory 'gtfsmergetool'
  $ mvn package -DinputFiles=../input -DresultDir=../result
  $ mvn package -DinputFiles="../input/bra ../input/rut" -DresultDir=../result  
```

### resultDir
```
-DresultDir=<dir>
```
The target directory for putting the merged GTFS files.

     