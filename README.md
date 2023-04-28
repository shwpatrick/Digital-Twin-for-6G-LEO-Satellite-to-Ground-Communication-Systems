# A-Simulation-Framework-of-LEO-Satellite-Communication-Integrating-Building-Models


Please execute the program using main.ipynb. 
The following will explain the .ipynb files that are executed within it.

# ===============================================================================
Library.ipynb           Listed below are the imported libraries.
Class_Definition.ipynb  It includes all the custom-defined Class formats.
Folder_Creation.ipynb   It creates corresponding folder formats in the root directory 
                        to organize large numbers of image files and information.

# ===============================================================================
The "data" folder will contain four subfolders.
  1.Buildings               The folder location for storing building models.
  2.SatelliteList_Celestrak The folder location for storing TLE data from satellites.
  3.Geojson                 The folder location for storing data in GeoJSON format.
  4.FigurePlot              The folder location for storing plotted images.

# ===============================================================================
There are several adjustable parameters in main.ipynb.
 
shp_buildings              The name of the building shapefile that needs to be imported.
time_s                     The start time of the simulation.
time_e                     The end time of the simulation.
time_step                  The time interval for creating satellite-to-user coordinate data.
ue_number                  The number of user devices.
ue_list                    The list of user devices, including the device names 
                           and latitude-longitude coordinate information.
     
para.Sat_num               The expected number of satellites to be captured.                      
para.Level_avg_height      The default height (in meters) for each floor in the simulation.
para.Effective_range       The range (in meters) around the user to consider surrounding buildings.
para.Fc = 2204.400 * 10e6  The satellite frequency (in Hz) used in the simulation.

Note:
If the time interval is too short or the simulation time is too long, 
it may cause difficulties for lower-performance computers due to the large amount of data generated.
You can reduce the simulation time and generate GeoJSON files in batches.
When plotting the images, read multiple GeoJSON files to concatenate the data.

# ===============================================================================
At this point, the program will generate corresponding GeoJSON files based on the data.
The file naming convention is as follows:

gdf_3857_ED_20230327000000_20230328000000_5.geojson

gdf_3857:         Coordinate projection format
ED:               User device name
20230327000000:   Start time of the simulation
20230328000000:   End time of the simulation
5:                Number of satellites used in the simulation
 
# ===============================================================================
The figure plot section will use %run to import functions for drawing different formats of images.
The main categories for the figure plot section are as follows:

map:                        functions for drawing images related to buildings and maps
bar:                        functions for drawing bar chart data
time-dependent sequence:    functions for drawing time-dependent data
skyplot:                    functions for drawing skyplots.

# ===============================================================================
Here, the glob function can be used to merge the geojson data needed, 
and the commented functions can be opened for drawing pictures.
Each function will create a corresponding folder in data/FigurePlot/ to save the pictures.
It is recommended not to use all the plotting functions at once.

# ===============================================================================
Below is a brief description of each plotting function.

plot_intersection_and_sectionview(df_all,buildingsData,para)  Plot the intersection and polygon of each time point 
                                                              in the dataframe.
                                                              Because the calculation required for plotting is very large, 
                                                              usually only a portion of the images are generated 
                                                              as a demonstration.

plot_basemap(buildingsData)                                   Plotting 2D maps combining building models and basemaps.
plot_basemap_rain(buildingsData)                              Draw a 2D map that combines building models with rainfall map                                                                 (tested only on Taiwan map).

plot_bar_satellite_location_percentage(df_all,50,70)          For each user device, for different satellites.
                                                              Draw LOS/NLOS percentage statistics.
                                                              50, 70 represent the elevation angle interval used for 
                                                              reference data, which is only between 50 and 70 degrees.


plot_bar_angle_samples(df_all)                                For each user device, for different elevation angle ranges
                                                              Plotting the statistics of LOS/NLOS samples.
plot_bar_angle_percentage(df_all)                             For each user device, for different elevation angle ranges
                                                              Plot the percentage statistics of LOS/NLOS.

plot_time_dependent_state(df_all)                             For different user equipment and different satellites,
                                                              Plot the NLOS/NLOS state for each sampling time point.

plot_time_dependent_basic_path_loss(df_all,para)              For different user devices and different satellites.
                                                              Plot the simulation diagram of basic path loss.

                                                             

plot_skyplot_date(df_all)                                     For different user devices, and for different satellites.
                                                              Plot the satellite orbits for different dates on a skyplot.

plot_skyplot_contour(df_all)                                  For different user devices, use all satellites.
                                                              Draw contour lines based on the LOS/NLOS state 
                                                              at each elevation angle point.
                                                              To observe the building profile.


# ===============================================================================
The remaining portion is a test using rainfall map data not included in the paper.



                                                             

                                                               
  
 
