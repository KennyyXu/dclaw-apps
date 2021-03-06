---
title: gate_release_example
description: simulation of a gate-release experiment
---

# Overview

A simulation of a gate-release experiment at the USGS debris-flow flume. This example uses bed-normal coordinates for the simple flume geometry. The variable flume slope-angle is set by the input file:

`init_data/aux/FlumeTheta.tt2 `

which is created by setinit.py, among other files, such as topography that is normal to the bed slope (flume walls).

# Preprocessing

Create needed DEMs for initialization with:
```
python setinit.py
```
This places DEMs for the topography and inital geometry etc. into gate_release_example/input_data/, read by setrun.py.

# Running/producing output

From your application directory:
```
make .output
```
Or, if you prefer, run in the background with `nohup` and `nice` (which prevents terminating the run if you log off or quit your terminal), and redirect screen output into `run.log` to keep a record of the run:
```
nohup nice make .output > run.log &
```

# Plotting with python

There are two examples of python plotting scripts, `setplot.py` and `setplot_1d.py`. The former produces a single set of overhead/mapview plots, the latter produces 1D cross-sectional plots. To choose which to use, modify the following line in Makefile:
```
CLAW_setplot_file = setplot.py      # File containing function to set plots
```
 or 
 ```
CLAW_setplot_file = setplot_1d.py      # File containing function to set plots
 ```

Then from your application directory:

```
make .plots
```
to check dependecies and take necessary steps to produce the plots. Alternatively, to make the plots from whatever output exists without checking dependencies:
```
make plots
```




