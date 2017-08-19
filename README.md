*asammdf* is a fast parser/editor for ASAM (Associtation for Standardisation of Automation and Measuring Systems) MDF (Measurement Data Format) files. 

*asammdf* supports both MDF version 3 and 4 formats. 

*asammdf* works on Python 2.7, and Python >= 3.4


Project goals
=============
The main goals for this library are:

* to be faster than the other Python based mdf libraries
* to have clean and easy to understand code base

Features
========

* read sorted and unsorted MDF v3 and v4 files
* files are loaded in RAM for fast operations

    * for low memory computers or for large data files there is the option to load only the metadata and leave the raw channel data (the samples) unread; this of course will mean slower channel data access speed

* extract channel data, master channel and extra channel information as *Signal* objects for unified operations with v3 and v4 files
* time domain operation using the *Signal* class

    * Pandas data frames are good if all the channels have the same time based
    * usually a measuremetn will have channels from different sources at different rates
    * the *Signal* class facilitates operations with such channels
    
* remove data group by index or by specifing a channel name inside the target data group
* create new mdf files from scratch
* append new channels
* convert to different mdf version
* add and extract attachments
* mdf 4.10 zipped blocks
* mdf 4 structure channels

Major features still not implemented
====================================

* functionality related to sample reduction block (but the class is defined)
* mdf 3 channel dependency save and append (only reading is implemented)
* handling of unfinnished measurements (mdf 4)
* mdf 4 channel arrays
* xml schema for TXBLOCK and MDBLOCK

Usage
=====

```python
   from asammdf import MDF
   mdf = MDF('sample.mdf')
   speed = mdf.get('WheelSpeed')
 ```  
 
Check the *examples* folder for extended usage demo.

Documentation
=============
http://asammdf.readthedocs.io/en/2.1.1/

Installation
============
*asammdf* is available on 

* github: https://github.com/danielhrisca/asammdf/
* PyPI: https://pypi.org/project/asammdf/
    
```
   pip install asammdf
```
    
Dependencies
============
asammdf uses the following libraries

* numpy : the heart that makes all tick
* numexpr : for algebraic and rational channel conversions
* blosc : optionally used for in memmory raw channel data compression
* matplotlib : for Signal plotting
* pandas : for DataFrame export

Benchmarks
==========

Python 3 x64
------------

![](benchmarks/x64_open.png)

![](benchmarks/x64_open_ram_usage.png)

![](benchmarks/x64_save.png)

![](benchmarks/x64_save_ram_usage.png)

![](benchmarks/x64_get_all_channels.png)

![](benchmarks/x64_get_all_channels_ram_usage.png)

Python 3 x86
------------

![](benchmarks/x86_open.png)

![](benchmarks/x86_open_ram_usage.png)

![](benchmarks/x86_save.png)

![](benchmarks/x86_save_ram_usage.png)

![](benchmarks/x86_get_all_channels.png)

![](benchmarks/x86_get_all_channels_ram_usage.png)
