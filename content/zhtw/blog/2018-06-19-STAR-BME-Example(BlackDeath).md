---
title: "STAR-BME Example(BlackDeath)"
date: 2018-06-19
image_webp: 
image: /images/blog/STARBME-BlackDeath/1.png
author: stemlab
---

## BlackDeath Example

1. Set CRS(Coordinate Reference System)
Select WGS84(EPSG:4326) in “Coordinate Reference System Selector”
2. Specify data
Specify Hard data and Soft data in “Specify Data” window
i. Hard data
Select “BD-1-Input-HD.csv” from downloaded example file under “BlackDeath/data/ Harddata”

ii. Soft data
Select “BD-2-SoftLinear.csv” from downloaded example file under “BlackDeath/data/ Harddata”
a. Soft PDF Type:User Defined.
b. Soft PDF From: Linear

After import hard data and soft data. BMEobj will be created,soft data and hard data will be load in QGIS.

![](/images/blog/STARBME-BlackDeath/1.png)

Time View of hard data

![](/images/blog/STARBME-BlackDeath/2.png)

Time View of Soft data

![](/images/blog/STARBME-BlackDeath/3.png)

Hard data (circle) and soft data (triangle) are showed. From figure2.1, color bar and time bar of data are showed on the left and below of figure.

3. Compute Trend and Residual From Data
User can choose “No Detrending”, “Kernel Smoothing” or “STmean” in this step. In this example, we will use “No Detrending”.

4. Covariance Analysis
4.1 Empirical Covariance Estimation
For this case, we will set:
Spatial Distance Limit: 0.5, Temporal Distance Limit: 31.33
Number of Spatial Lags:11 ,Number of Temporal Lags:11
Spatial Lag Tolerance:0.03 ,Spatial Temporal Tolerance:4.476

![](/images/blog/STARBME-BlackDeath/4.png)

And press “Plot Empirical Covariance”.

4.2 Covariance Model Fitting
After fitting covariance, 2D and 3D Fit covariance will be plotted.
Nest Number = 2
Fit Covariance Model
C1 = 2.98, S1 = 2.5, T1 = 8.08
C2 = 2.02, S2 = 0.19, T2 = 7.74

![](/images/blog/STARBME-BlackDeath/5.png)

5. Prediction
Specify location: For this case, we use “Grid Input”, which STARBME will generate grid coordinate for predict. Press “Predict” for predict the coordinate that generate by “Grid Input” , we will set coordinate boundary by select “ Set By Data Boundary”
For Grid Input,
Xn = 50
Yn = 50
Tn = 5
For Predict,
Order = ZeroMean
Spatial Range = 8.08
Temporal Range = 7.74
Spatial/Temporal Ratio = 1.04392
Nhmax = 5, nsmax = 2

6. Output result
Specify Task for result: Add Result to QGIS(Raster with Mask), with select countries.shp from BlackDeath\Background_shp.

![](/images/blog/STARBME-BlackDeath/6.png)