# MALA-GPR
<H2>MALA GPR Coordinate File to Shapefile (R script)</H2>
MALA GPR systems collect great data and integrate a GPS signal with the data if you desire.  Often the GPS elevation is not to standard (unless you are using an RTK), and attaching a good Lidar elevation from a TIF or other dataset is desirable.  

The initial MALA-GPR project focuses on creating ArcGIS shapefiles (maybe file geodatabases in the future?) from the COR file created with the GPR, using that shapefile to extract lidar elevation data from the point, and push that back to the original COR file where the position and elevation data are kept.   Future work may involve reading and processing the actual GPR radargram, but that is currently beyond my capabilities.  Please add on!

<h2>Libraries and packages to install</h2>
      abind
      gdalUtils
      maptools
      marmap (not really)
      raster
      rgdal
      rgeos
      shapefiles
      sp
      ....at least the ones I know of..there may be others
      

<b>Complete</b></br>
1.  DAT_nnnn.cor file to shapefile is complete.
      The script searches all directory structures below your set work directory setwd() and creates a shapefile for each .cor file found in the same location as the .cor file.
      At the end of the script, it produces a shapefile will all of the files processed in that run

<b>Next Steps</b></br>
2. Extract good elevation data from GeoTIFF
    a.  pull the latitude,longitude pairs from the corData (if using R only) or the shapefile (if in ArcGIS py)
    b.  convert the WGS-1984 projection to the projection of the dataset (set variable at top of file)
    c.  extract the Z and convert to meters if necessary from the point intersect with the GeoTIFF
    d.  replace the Z value in the corData dataframe
    e.  copy the original .cor file to .cor.old
    f.  export the columns from the corData to the new-and-improved DAT_nnnn.cor (in the right directory)
    (may be possible/efficient/necessary to do this step prior to Shapefile creation)
    
3.  Create a GUI that allows for variables to be set
    a.  browse to top directory structure (parent.folder)
    b.  choose the projection of the original DAT_nnnn.cor file (I have only seen LL from gps here, but it may exist)
    c.  choose the geoTIFF with the elevation data
    d.  choose the projection of the geoTIFF (usually UTM-17 WGS-1984 for me)
    e.  choose the output location for the final geodatabase (that has the new Z value, too)
    
4.  Make maps for each process
    a.  select a specific map background from existing packages
    b.  plot by unique fileID
    c.  Choose output format (pdf, png, jpeg, tif)
    d.  Choose output size
    
    
