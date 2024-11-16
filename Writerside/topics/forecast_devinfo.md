# Developer information for the forecast visualization page

These are the main files:

| Group        | Files                | Relevance                                           |
|--------------|---------------------|-----------------------------------------------------|
| JavaScript   | forecast_data.js    | Main visualization logic, data handling, and plots  |
|              | data.js             | Data loading and processing utilities               |
| CSS          | main.css            | Global styles and USU theme                         |
|              | forecast.css        | Specific to the forecast visualization              |
| HTML         | forecast_data.html  | Main forecast visualization page                    |
|              | footer.html         | (in `\public\partials`) Footer object              |
|              | sidebar.html        | (in `\public\partials`) Sidebar object             |

These are the file relevances:
- `forecast_data.js`: Contains all the main logic for:
    - Test data generation with realistic patterns
    - Data visualization using Plotly.js
    - Interactive controls (checkboxes, date pickers)
    - Statistics calculations
    - Auto-updating functionality
    - USU color scheme implementation
- `forecast.css`: Specific styling for:
    - Control panel layout
    - Checkbox groups
    - Plot container
    - Statistics panels
    - USU branding colors

## Data flow
1. Data is currently generated within the application for testing (`isTestMode = true`). In production, it will be fetched from an API endpoint.
2. The data structure follows this format:
   ```json
   {
     "timestamp": {
       "location": {
         "parameter": "value"
       }
     }
   }
```
3. When user selects locations/parameters or changes dates:
    - Data is filtered based on selections
    - Plotly traces are generated for each location-parameter combination
    - Statistics are calculated and displayed
    - Plot is updated with USU styling
4. The visualization auto-updates every hour to show latest data.

## Test Data Generation
- Realistic patterns are generated for each parameter:
    - Temperature: Diurnal cycle with random variation
    - Wind Speed: Variable with time-dependent patterns
    - Ozone: Daily cycle with location-specific variations
    - Snow Depth: Slow-changing with minimal variation
    - Pressure: Gradual changes over time
    - Humidity: Daily cycle with weather-dependent patterns

### Notes
* The page uses Plotly.js for visualization, chosen for its:
    - Interactive features
    - Good performance with time series
    - Export capabilities
    - Responsive design
* USU branding colors are used throughout:
    - Primary: #00263A (deep blue)
    - Secondary: varying shades for differentiation
    - Accent colors for highlights and warnings

### TODOs
* Implement actual API integration when endpoint is ready
* Add data validation for API responses
* Consider caching mechanisms for historical data
* Add more statistical analysis options
* Implement data download functionality
* Add comparison tools between different time periods
* Consider adding forecast uncertainty visualization
* Add more parameters as they become available
* Implement user preferences storage
* Add more interactive features (zoom synchronization, cross-parameter analysis)

### Future Considerations
* May need to implement data streaming for real-time updates
* Consider adding more advanced statistical analysis
* Might want to add comparison with historical averages
* Could add model performance metrics
* Potential for adding machine learning predictions