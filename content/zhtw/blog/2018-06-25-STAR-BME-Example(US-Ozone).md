---
title: "STAR-BME Example(US Ozone)"
date: 2018-06-25
image_webp: 
image: /images/blog/STARBME-US/1.png
author: stemlab
---

## US Ozone Example

1. Set CRS(Coordinate Reference System)
Select WGS84(EPSG:4326) in “Coordinate Reference System Selector”
2. Specify data
Specify Hard data and Soft data in “Specify Data” window
i. Hard data
Select “HardData-wgs84.csv” from downloaded example file under “US_TotalOzone_ST\Data\csv”

ii. Soft data
Select “SoftData_gaussian_wgs84.csv” from downloaded example file under “US_TotalOzone_ST\Data\csv”
a. Soft PDF Type:Gaussian.
b. Soft PDF From: Linear

After import hard data and soft data. BMEobj will be created,soft data and hard data will be load in QGIS.

![](/images/blog/STARBME-US/1.png)

Figure2.1

Time View of hard data

![](/images/blog/STARBME-US/2.png)

Time View of Soft data

![](/images/blog/STARBME-US/3.png)

Hard data (circle) and soft data (triangle) are showed. From figure2.1, color bar and time bar of data are showed on the left and below of figure.

3. Compute Trend and Residual From Data
User can choose “No Detrending”, “Kernel Smoothing” or “STmean” in this step. In this example, we will use “No Detrending”.

4. Covariance Analysis

4.1 Empirical Covariance Estimation
For this case, we will set:
Spatial Distance Limit: 71.14 Temporal Distance Limit: 2.667
Number of Spatial Lags:11 Number of Temporal Lags:11
Spatial Lag Tolerance:10.16 Spatial Temporal Tolerance:0.381

![](/images/blog/STARBME-US/4.png)

And press “Plot Empirical Covariance”.

4.2 Covariance Model Fitting
After fitting covariance, 2D and 3D Fit covariance will be plotted.
Nest Number = 2
Fit Covariance Model
C1 = 59.31, S1 = 7.11,T1 = 0.46
C2 =238.62, S2 = 21.53,T2 = 11.75

![](/images/blog/STARBME-US/5.png)

5. Prediction
Specify location: For this case, we use “Grid Input”, which STARBME will generate grid coordinate for predict. Press “Predict” for predict the coordinate that generate by “Grid Input”, we will set coordinate boundary by select “ Set By Data Boundary”
For Grid Input,
Xn = 50
Yn = 50
Tn = 5
For Predict,
Order = ZeroMean
Spatial Range = 21.53
Temporal Range = 11.75
Spatial/Temporal Ratio = 1.832
Nhmax = 5, nsmax = 2
Cross Validation
Hard Data only, with sample size = 377

6. Output result
T = 6

![](/images/blog/STARBME-US/6.png)

T = 7

![](/images/blog/STARBME-US/7.png)

T = 8

![](/images/blog/STARBME-US/8.png)

T = 9

![](/images/blog/STARBME-US/9.png)

T = 10

![](/images/blog/STARBME-US/10.png)
