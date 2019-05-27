# Point Cloud Visualization
Bryan Begay and Katie Nicolato  **|**  GEOG 572 Geovisual Analytics  **|**  Spring 2019

![](img/potree_lion.JPG)
An example of a visualized point cloud from the Potree website.

## Objectives

* Understanding point cloud geovisualization
* LiDAR basics
* Structure from Motion basics
* Unmanned Aerial Systems overview
* Potree and 3DF Zephyr data processing

## Overview of .las files, LiDAR, and Structure from Motion (SfM)

LAS datasets and LAS files are an industry standard binary format that allows LiDAR and Structure from Motion (SfM) data aquisitions to be stored quickly and easily. The LAS files contain point clouds, which are large numbers of discrete data points in space. Each point contains XYZ coordinates with intensity associated RGB color values. 3-D scanners, LiDAR, and SfM generate point clouds stored in LAS files.

Detailed point clouds are captured with active sensors such as LiDAR, or with passive remote sensing techniques from a high resolution multispectral camera (e.g. SfM). Active sensors generate their own energy to record data (e.g. laser pulses), and passive sensors gather imagery from passive energy sources (e.g. light reflecting off of objects and sensed in a camera lens).

LiDAR data is stored inherently in LAS files as point data, but SfM requires software and overlapping images to create LAS datasets with mathematical models and computer software generating points in space. Careful data collection and sufficient preprocessing generates a high quality dataset for use in analyses. Visualizing point cloud datasets is a fundamental step in understanding the datasets and using point clouds as a tool for education or visual aid.

## Preprocessing

Before analyzing or visualizing a point cloud, clean and package the data to minimize error and corruption. Open source point cloud visualization and editing software are available for download:

CloudCompare (All-Around Visualization) https://www.danielgm.net/cc/

Fusion (Forestry) http://forsys.cfr.washington.edu/fusion/fusionlatest.html

lidR (R Package for Forestry) https://github.com/Jean-Romain/lidR

LAStools (Editing and Analyses) https://rapidlasso.com/lastools/

**LAS Format**

Ensure lidar and SfM are prepared in the correct .las format. Use open source software such as CloudCompare or Fusion to visualize the .las point cloud.

**Merge**

Users may acquire point cloud data in separate files. Use a merge command or tool in the suggested software or ArcGIS to combine .las files in preparation for clipping and analyses.

**Clip**

Users may have an area of interest, such as a polygon shapefile, for clipping a .las dataset. After merging, use a clipping command or tool in the suggested software or ArcGIS to clip a .las file to a polygon of interest.

**Normalize**

Some applications require "absolute" z-values devoid of elevation influence. For instance, to achieve absolute tree height, we subtract the ground elevation from the surface height (Digital Surface Model - Digital Elevation Model). This produces tree height from the ground to the canopy maxima and does not include elevation from sea level. The visualization result is a "flat" point cloud lacking terrain features.

*Pre-Normalization*
![](img/prenormalization.JPG)

*Post-Normalization*
![](img/postnormalization.JPG)

## Processing Structure from Motion Data

**Agisoft Metashape**

Agisoft Metashape is an industry standard visualization software for SfM data. A free trial is available, but full access requires payment.

https://www.agisoft.com/

**3DF Zephyr**

3DF Zephyr is an open source SfM visualization software. The free version allows users to take up to 50 photos for 3D model production.

https://www.3dflow.net/3df-zephyr-pro-3d-models-from-photos/

## Web Visualization with Potree Converter

Potree Converter transforms 3D point clouds into a web-friendly format for online visualization. The input file must be in .las format. The tool creates an HTML file with the associated point cloud and libraries for hosting on a web server. The resulting web page allows 360-degree viewing and zoom functions. The ouput Potree web page includes many tools for manipulating and measuring the target point cloud. Users can customize the page template through the source code.

**Conversion Code**

1. Create a Workspace folder to store all files in a single working directory.

2. Download Potree Converter into the folder: https://github.com/potree/PotreeConverter

3. Move target .las file into the folder.

4. Open Command Prompt and navigate to the folder.

5. Enter the code below, making the following substitutions:

`PotreeConverter.exe G:\input.las -o G:\output -p index --overwrite --output-format LAS`

*PotreeConverter.exe* = Full file path for the Potree Converter executable<br/>
*G:\input.las* = Full file path for the input .las file<br/>
*G:\output* = Full file path for the output location. The program will create a folder with this title to store the ouputs.<br/>

6. If successful, you will receive this CMD output:

![](img/CMD_potree_output.JPG)

7. Check the output folder for files. It should contain a folder for libraries, the point cloud, and an index.html file. Rename the index.html file to a name that suits your application:

![](img/potree_output_files.JPG)

8. Potree requires a web server to host the point cloud visualization files. We will use GitHub as our web server.

**GitHub Hosting**

1. Create a GitHub repository to host the 3D geovisualization.

2. Extract the lib and point cloud folders and renamed index.html file from the output folder and push them to the repository.

3. The visualization will appear at the repository address "/index.html" (or renamed HTML).

**Customizing Potree**

Users can customize the point cloud web page created with Potree Converter by exploring the source code. Users can add, remove, and manipulate the default visuzliation and measurement tools provided.
