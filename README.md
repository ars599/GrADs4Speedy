

# How to save topography data with “grd” format in SPEEDY
Step-by-Step Instruction

## ** SPEEDY version: 41 **
Original version was developed by: Fred Kucharski, Franco Molteni, and Martin P. King

## 1. Make sure that the “NetCDF” file you made satisfies the reading regulation of GrADS
If you have a message of “SDF file has no discernable X coordinate,” please refer to Figure 1.


** The problem of variables attributes

** Figure 1 GrADS can not use sdfopen to read & GrADS can use sdfopen to read

![](https://github.com/ars599/ESMVal_Examples/blob/main/recipe_perfmetrics_CMIP56_simple_v3_working/plots/collect/RMSD/Picture1.png)


## 2. Creat “grd” file by using GrADS: step1_write_nc2grd.gs
Using GrADS to read in NetCDF file and output “grd” file. This step can successfully create a “grd” file that GrADS can read. However, the y-dir of this file is upside-down. We need next step to reverse it.

> INPUT: the NC file you prepared (e.g., orog_lsm_alb_text.t30.nc)
> OUTPUT: orog_lsm_alb_test.t30.ydir.grd

In addition, you will need to copy a “ctl” file for next step.

> CTL: orog_lsm_alb_test.t30.ydir.ctl (Figure 2)


** Figure 2 The “ctl” file used in the next step

![](https://github.com/ars599/ESMVal_Examples/blob/main/recipe_perfmetrics_CMIP56_simple_v3_working/plots/collect/RMSD/Picture2.png)

## 3. Reverse y-dir by using GrADS: step2_reverse_ydir.gs
Using GrADS to read in “grd” file with the “ctl” file we created in previous step.

>INPUT: orog_lsm_alb_test.t30.ydir.grd & orog_lsm_alb_test.t30.ydir.ctl
>OUTPUT: orog_lsm_alb_test.t30.grd

You also need to create another “ctl” file for GrADS to read the final “grd” file.

>CTL: orog_lsm_alb_test.t30.ctl

