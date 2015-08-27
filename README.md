i-v-vs-time-taker
=================

This project contains a graphical user interface for controlling a keithley 2400 sourcemeter, useful for investigating transient events in I-V sweeps of solar cells. This tool can produce data files that contain current and voltage measurements as a function of time sampled at ~200Hz (as fast as I can currently get the Keithley to go) during an I-V sweep measaurement. Such 'high speed' data sampling can be used to intelligently advance the sweep once a steady state has been reached at each point in the sweep. This prevents over-estimation of the current in solar cells with large RC constants such as certian perovskite cell architectures.

Two other projects accompany this project:
- batch-i-v-analysis
 - a GUI that can plot the current and voltage verses time data files generated here. Also does fully automated curve fitting and analysis on regular i vs v data sets
- hystAnalysis
 - a MATLAB script that does much more in depth analysis of the current and voltage verses time data files generated here

### If you find this code useful...
---
Please cite our work:  
[DOI: 10.1039/C4EE02465F](http://pubs.rsc.org/en/Content/ArticleLanding/2014/EE/C4EE02465F)  
and shoot me an email. grey [AT] christoforo [DOT] net

### Files here
---
- **i-v-vs-time-taker.py**
 - Main python script. Run this to use the tool. You can edit the code in this file directly using your favorite python editor.
- **ivSweeper.ui**
 - Contains user interface design for main window, edit with Qt Designer (I used version 4.8.5)
- **ivSweeperUI.py**
 - Do not edit this file directly. Instead generate it from ivSweeper.ui by issuing:  
`pyuic4 -o ivSweeperUI.py ivSweeper.ui`
- **gpib.py**
 - Contains thread-safe gpib interface for communication with the sourcemeter

###  Setup & Initial run
---
For Arch Linux:
```
sudo pacman -S python2-pyqt4 python2-scipy python2-matplotlib git
yaourt -S python2-pyvisa
git clone https://github.com/greysAcademicCode/i-v-vs-time-taker.git
cd i-v-vs-time-taker
pyuic4 -o ivSweeperUI.py ivSweeper.ui
python2 i-v-vs-time-taker.py
```
