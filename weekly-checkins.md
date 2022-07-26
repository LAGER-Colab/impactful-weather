# Impactful Weather Meeting Notes

[Link to Task Document](https://hackmd.io/6_R9D86RRwmqqX-TmxME6Q)

## 26 July 2022
* Attendees
    * Max Grover
    * KJ Schmidt
    * Isaac Darling
    * Aadit Ambadkar
    * Braeden Cullen
    * Ari

### Updates
* Aadit
    * Lots of experimentation with different methods
    * Aadit used NN-based SRCNN at first pass (did this instead of SRGAN because they take a long time)
    * getting ERA5 data to match with NEXRAD data was hard -- starting with too few pixels in coarse data 
        * scaling from 3x3 to 16x16 seems feasible? need to figure out how to do it efficiently but scaling to 80x80 does not seem possible 
        * TODO: Will download and upload to the repo, with clear naming of method used 
    * Max has gridding packages to account for shape of the earth to help match resolutions 
    * Max: you can set up grid parameters to adjust the grid size to a 25km grid or something similar -- can regrid afterwards, or directly from the RADAR
        * Tool to resample and match datasets - https://xesmf.readthedocs.io/en/latest/
    * Decision: 16x16 is a reasonable target resolution
        * 25% seeems to be a good zone
* Braeden
    *  using a stack of SRCNNs, following the outline in the DeepSD paper in the blogpost Max sent 
    *  hopefully by next week he'll have something to show 
    *  also shooting for 16x16 resolution 
*  Sanjiv
    *  BDSR method -- fairly similar to SRGAN, wants to give it a try 
    *  read on websites and papers that this method had good results
*  Isaac
    *  browsing through google scholar and doing a lit search
    *  likes evolutionary algorithms 
    *  this week he's going to start implementations 

### Questions

### Discussion
* Planning on chatting later this week about methods!
    * Add to reference folder
    * Chat in the slack
    * Plan on running more algorithms this week
* Slides for future meetings?
    * Ari, Max, KJ draft something up, share the instructions


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
    * https://github.com/LAGER-Colab/impactful-weather/blob/main/references/evolution.txt
* Sanjiv
    * Looked at new method of downscaling the method (BCSD model)
    * Found article that used this method, and expanded on it
    * Journal Articles
        * Comparing BCSD to CEE models
            * BCSD: bias-correction and spatial disaggregation 
            * CEE: canonical correlation analysis filtering, multi-model ensemble and extreme learning machine (ELM) regression
            * https://iwaponline.com/jwcc/article/8/4/675/37933/A-new-downscaling-approach-and-its-performance

### Questions
* How to tell what model is best?
    * Look into it, test things out!

### Discussion
* Brainstorming session at next week's meeting
* Keep looking into new models, new resources!
* Isaac added a folder to the repo to put any notes or resources for ML models

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