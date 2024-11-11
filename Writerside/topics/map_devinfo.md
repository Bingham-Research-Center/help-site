# Developer information for the observation map page

These are the main files:

| Group        | Files            | Relevance                                           |
|--------------|------------------|-----------------------------------------------------|
| JavaScript   | config.js        | The lats/lons for map markers; legend thresholds.   |
|              | mapUtils.js      | Functions for plotting markers; may merge?          |
|              | data.js          | Loading observation data                            |
|              | map.js           | Main map functions                                  |
| CSS          | main.css         | Always useful, I guess. The boss CSS.               |
|              | map.css          | Specific to the map page.                           |
| HTML         | lcoations.html   | Map page. Want to rename to "map.html"!             |
|              | footer.html      | (in `\public\partials`)  Footer object              |
|              | sidebar.html     | (in `\public\partials`)  Sidebar object             |


These are the file relevances:
- `config.js`: This has latitude and longitude lookups for map markers etc. There is a lookup dictionary for legend thresholds---for the purpose of plot-marker color. This is independent of `map.js` because the lookups are used in other places.
- `mapUtils.js`: This has functions for plotting markers. It may be merged with `map.js`.
- `data.js`: This loads observation data from json data in `\public\data`.

## Data flow 
1. Observations are first drawn from [TODO - from Synoptic Weather directly, or keep a local table/copy?] outside of this website's purview. They are stored in a json file in `\public\data` in a format predictable for scripts to plot.
2. When the map is drawn, it reads the json file and plots the markers according to the data. The markers are color-coded according to the EPA's Air Quality Index (AQI) --- the legend is shown in the bottom right of the map.
3. Clicking a marker brings up a pop-up with the station name and current levels of air-quality values. There is a link to further time series of observations for that station.
4. The map is updated every 5 minutes. [TODO - updated table or map?]

### Notes
* Traffic is not expected to cause demand on our site, the CHPC data server, or condequent calls to Synoptic Weather's API.
* Scripts for loading data will be kept in a tentative new repo `chpc-scripts` or something with common helper functions.


### TODOs
* Here
* There



