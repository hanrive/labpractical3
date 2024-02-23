# Required Items
With Server admin access: https://luna.flemingcollege.ca:6443/arcgis/rest/services/geom99am/hariveCanada/MapServer
Without Server admin access: https://luna.flemingcollege.ca/arcgis/rest/services/geom99am/hariveCanada/MapServer

# Adding ArcGIS Server (Luna) Map Services to ArcGIS Online

Published map service: https://luna.flemingcollege.ca:6443/arcgis/rest/services/geom99am/hariveCanada/MapServer

AGOL item: https://fleming.maps.arcgis.com/home/item.html?id=1c6489e53ae749e1b98fe7280c3218d0

Web Map: https://www.arcgis.com/home/webmap/viewer.html?url=https%3A%2F%2Fluna.flemingcollege.ca%3A6443%2Farcgis%2Frest%2Fservices%2Fgeom99am%2FhariveCanada%2FMapServer&source=sd

*Why did you have to add ADROOT\ to the login information when adding the luna layer reference to ArcGIS Online? Did your map projection change? What is the initial map extent? What properties from your originally published map carry forward?*
- ADROOT\ (active directory root) is the active directory domain provided by Microsoft of where my user information is and by using ADROOT\ is telling ArcGIS PRO where my fleming details are located
- The map projection from my hariveCanada pro file and on AGOL is PCS_Lambert_Conformal_Conic with the following extent via luna:
> XMin: 3689439.0113999993
> YMin: 659338.8599999994
> XMax: 9015736.631399997
> YMax: 5242088.937100001
> Spatial Reference: >PROJCS["PCS_Lambert_Conformal_Conic",GEOGCS["GCS_North_American_1983",DATUM["D_North_American_1983",SPHEROID["GRS_1980",6378137.0,298.257222101]],PRIMEM["Greenwich",0.0],UNIT["Degree",0.0174532925199433]],PROJECTION["Lambert_Conformal_Conic"],PARAMETER["False_Easting",6200000.0],PARAMETER["False_Northing",3000000.0],PARAMETER["Central_Meridian",-91.86666666666666],PARAMETER["Standard_Parallel_1",49.0],PARAMETER["Standard_Parallel_2",77.0],PARAMETER["Latitude_Of_Origin",63.390675],UNIT["Meter",1.0]]
- On my originally published map I changed the display field to PRNAME to show the provinces and territories as unique values for symbology and that has carried over to AGOL

# Using ArcGIS Server Map Services
*"What cartographic options are available to override the map service cartography and save a newly-styled map in the ArcGIS Pro Project to Submit in the next practical lab."*

According to: https://pro.arcgis.com/en/pro-app/3.1/help/sharing/overview/overwrite-a-map-service.htm
*"You can overwrite a map service that has been published to a stand-alone ArcGIS Server 10.6 or later site. Reasons to overwrite a map service include updating source data, changing map or layer properties (such as layer symbology), editing the item description, and setting different configuration properties. When you overwrite a map service, any maps that use the service in client applications are updated.*

*Overwriting a map service is similar to publishing a map service. You can change most of the properties of a map service when you overwrite it, including properties of the map as well as configuration settings. You can't change the name of the service or its location (the service URL). If you are overwriting a cached map service, see the Cached map service considerations section below. You can also use ArcPy to overwrite a map service to a stand-alone server. To learn more, see Automate publishing services."*
