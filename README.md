# Point Cloud Visualization
Bryan Begay and Katie Nicolato  **|**  GEOG 572 Geovisual Analytics  **|**  Spring 2019<br/>

## Objectives<br/>

## Overview<br/>

**Lidar**<br/>

**Structure from Motion (SfM)**<br/>

## Preprocessing<br/>

Before analyzing or visualizing a point cloud, clean and package the data to minimize error and corruption. Open source point cloud visualization and editing software are available for download:

*CloudCompare*

*Fusion*

*LAStools*


**LAS Format**

Ensure lidar and SfM are prepared in the correct .las format. Use open source software such as CloudCompare or Fusion to visualize the .las point cloud.

**Merge**

Users may acquire point cloud data in separate files. Use a merge command or tool in the suggested software or ArcGIS to combine .las files in preparation for clipping and analyses.

**Clip**

Users may have an area of interest, such as a polygon shapefile, for clipping a .las dataset. After merging, use a clipping command or tool in the suggested software or ArcGIS to clip a .las file to a polygon of interest.

**Normalize**

Some applications require "absolute" z-values devoid of elevation influence. For instance, to achieve absolute tree height, we subtract the ground elevation from the surface height (Digital Surface Model - Digital Elevation Model). This produces tree height from the ground to the canopy maxima and does not include elevation from sea level. The visualization result is a "flat" point cloud lacking terrain features.

*Pre-Normalization*
![]()
</br>
*Post-Normalization*
![]()
</br>

## Processing Structure from Motion Data

**Agisoft Metashape**



Agisoft Metashape

**3DF Zephyr**



3DF Zephyr is an open source

## Web Visualization with Potree Converter<br/>

Potree Converter transforms 3D point clouds into a web-friendly format for online visualization. The input file must be in .las format. The tool creates an HTML file with the associated point cloud and libraries for hosting on a web server. The resulting web page allows 360-degree viewing and zoom functions. The ouput Potree web page includes many tools for manipulating and measuring the target point cloud. Users can customize the page template through the source code.

**Conversion Code**<br/>

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

**GitHub Hosting**<br/>

1. Create a GitHub repository to host the 3D geovisualization.

2. Push the lib and point cloud folders and renamed index.html file to the repository.

3. The visualization will appear at the repository address "/index.html" (or renamed HTML).
<br/>

**Customizing Potree**<br/>

Users can customize the point cloud web page created with Potree Converter by exploring the source code. Users can add, remove, and manipulate default visuzliation and measurement tools.
