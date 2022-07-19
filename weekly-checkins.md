# Impactful Weather Meeting Notes

[Link to Task Document](https://hackmd.io/6_R9D86RRwmqqX-TmxME6Q)

## 19 July 2022
* Attendees
  * Max Grover
  * Scott Collis
  * Isaac Darling
  * Sanjiv Parthasarathy
  * KJ

### Updates
* Isaac
    * Played with the data the least
    * Found a couple of interesting things
* 

### Questions
* 

### Discussion
* Brainstorming session at next week's meeting
* 

## 5 July 2022
* Attendees
  * Max Grover
  * Ari Scourtas
  * Isaac Darling
  * Sanjiv Parthasarathy
  * Aadit
  * KJ
  * Braeden

### Questions
* How to output netcdf files
    * https://docs.xarray.dev/en/stable/generated/xarray.Dataset.to_netcdf.html
* What is the ultimate goal?
    * want to go from coarse res to high res, but "downscale" means make it higher resolution in the weather/climate realm (the opposite is true in ML)
    * goal is to train a model to get from coarse resolution to higher resolution 
* Which data are we trying to transform?
    * Trying to "downscale" the coarse ERA5 dataset to the level of the high resolution Houston radar data 
    * We have the ERA5 data and radar data for the same time/place (the Houston June 2 2022 data)
* Is there a target resolution we're aiming for?
    * the resolution of the radar dataset that you're gridding 
* Where does the project conclude?
    * once we have the model, can try applying to other datasets 
    * for example, could train on ERA5 data and ultimately apply to CMIP data 
* After data collection, what next?
    * Next steps would be collaborating together on researching which ML techniques would be best
    * up until now the focus has been on familiarizing yourselves with the data and techniques involved


### Discussion
* Great blog on "downscaling" climate data that Max found
    * https://carbonplan.org/research/cmip6-downscaling-explainer
* In step 8, there's a link to the ERA5 data portal
    * in the Download Data tab 
    * check Reanalysis button
    * check Total precipitation field and rain fields/other precipitation fields 
    * Check year, month, and date (June 2, 2022)
    * select all times 
    * export as NETCDF file (NOT grib)
* Max isn't here next week, KJ and Ari might not be either, may need to adjust meeting (SciPy 2022)


### Next Steps
* This week, focus on step 8 as well as finishing up any previous steps 
* Read the blog Max sent out https://carbonplan.org/research/cmip6-downscaling-explainer 
* Start thinking about what you want to do with the data!
* Start discussing with each other ideas about how to approach the ML ✨


## 28 June 2022
* Attendees
  * Max Grover
  * Ari Scourtas
  * Isaac Darling
  * Sanjiv Parthasarathy

### Updates
* Isaac - working through the cookbooks, learned new Python things!
    * Got through examples, applied gridding to the Houston radar data
    ```python
    files = sorted(fs.glob("s3://noaa-nexrad-level2/2022/06/02/KHGX/KHGX20220602_18*"))
    ```
    * Next step - making it work with the Houston radar form June 2, 2022
* Sanjiv - working through installation issues
    * working with Raf, will update us shortly 
    * Will reach out if more help needed with installation
* Aadit
    * Got through the cookbooks, made latitude and longitude grid out of the radar
    * Working to apply gridding algorithm to radar data
* Max
    * **Decision**: Clarified with Scott, the goal is to go from coarse resolution ERA5 or CMIP6 data to higher resolution

### Discussion
* What is areal mean?
    * Max: it's the mean over some area, for example let's say we have a grid with points across lat and longs -- it's the average across that area
    * see the xarray cookbook for more information and context 
* we can use Pangeo's Binder website now, if students want to 
    * part of the `radar-cookbook` repo
    * https://github.com/ProjectPythiaTutorials/radar-cookbook
* PyArt release coming this week that will resolve the numpy issue
    * For now, can use slightly older numpy (<1.23.0)


### Next Steps
* This week, focus on steps 4-7 in addition to wrapping up whatever is remaining from 1-3