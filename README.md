# Construct
Exhibition for Iowa State College of Design's 'Coding Design / Designing Code Symposium'


----crontab----

used for automatically running scripts


----8control.sh----

used to monitor status of printer. Credit https://github.com/ieatacid/octocontrol/blob/master/_8control.sh


----printwatch.sh----

uses 8control to check status of printer. if printer is ready and the .gcode file queue has an entry, it will automatically send the file to octoprint and begin printing. To prevent unanticipated prints, this is launched by the user and run continually.


----PiAutomatedCopy.bat----

batch file for windows pc creating the .stl 3d model files. Used to transfer file to the slicing Rpi.


----GcodeManipulator.py----

this python script takes the gcode from the sliced .stl file and alters it to allow the printer to print the new object directly on top of the old one, creating one continuous object from multiple .gcode files. It accounts for teh first object having a raft, and most importantly, it increases the Z axis .gcode value for every print after the first. Preable and Postable are removed. This is called by Bashslicer.sh


----Bashslicer.sh----

BashSlicer monitors the queue of .stl files provided by the Windows PC's batch file. It slices them in order and moves the resulting file to the gcode queue of the second Rpi. This script is ran on a schedule with crontab.
