# Ruter GTFS Merge Script 
This Maven project is just configuration for running onebussaway gtfs merge tool. 

To run it, use:
```
  $ export MAVEN_OPTS=-Xmx2048M 
  $ mvn package -DinputFiles=files -DresultDir=target
```
If the `files` argument is a directory with subdirectories these directories are pased in to the merge tool - not the 
root directory. Subdirectories starting with `.` is ignored.

     