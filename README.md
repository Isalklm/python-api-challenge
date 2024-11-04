
# WeatherPy and VacationPy

## Project Overview
The WeatherPy and VacationPy projects involve using weather data and mapping tools to analyze weather patterns and find ideal vacation locations based on certain weather criteria. This project uses data from the OpenWeatherMap API and Geoapify API to retrieve weather and geographical data for cities around the world, and visualize this information to support travel planning decisions.

## Project Structure
- **WeatherPy**: This section of the project focuses on analyzing weather data across different latitudes and generating visualizations for key weather metrics like temperature, humidity, cloudiness, and wind speed.
- **VacationPy**: This section narrows down the dataset to ideal weather conditions for a vacation and uses the Geoapify API to locate nearby hotels, displaying the information on an interactive map.

## Libraries and APIs Used
- **Python Libraries**:
  - `matplotlib.pyplot` for plotting graphs.
  - `pandas` for data manipulation and organization.
  - `numpy` for numerical operations.
  - `requests` to handle API requests.
  - `time` to manage API rate limits.
  - `scipy.stats.linregress` for performing linear regression.
  - `hvplot.pandas` and `geoviews` for interactive maps.
  - `warnings` to suppress unnecessary warning messages.

- **APIs**:
  - **OpenWeatherMap API**: Provides weather data for various cities globally.
  - **Geoapify API**: Locates hotels near specified coordinates.

## Contents
- **data/**:
  - `cities.csv`: Contains a list of cities with their latitude and longitude coordinates.
  - `output_data/cities.csv`: Output file with weather data collected for each city.

- **notebooks/**:
  - `WeatherPy.ipynb`: Jupyter Notebook containing the WeatherPy analysis, including data retrieval, linear regression analysis, and visualizations.
  - `VacationPy.ipynb`: Jupyter Notebook containing the VacationPy analysis, including narrowing down cities with ideal weather and mapping them with hotel information.

- **api_keys.py**: Contains API keys for OpenWeatherMap and Geoapify (excluded from version control for security).

## WeatherPy Analysis
In the WeatherPy section, weather data was retrieved and analyzed for cities across a range of latitudes. Key steps include:
1. **Data Collection**: Using the OpenWeatherMap API to gather data on temperature, humidity, cloudiness, and wind speed for randomly selected cities worldwide.
2. **Linear Regression Analysis**: Examining correlations between latitude and each weather metric to understand how latitude affects weather patterns.
3. **Visualization**: Creating scatter plots with linear regression lines for Northern and Southern Hemispheres to observe trends in weather metrics as they relate to latitude.

### Key Findings:
- **Temperature**: Generally decreases with increasing latitude in both hemispheres.
- **Humidity, Cloudiness, and Wind Speed**: Show weak correlations with latitude, suggesting that other geographical factors may have a stronger influence on these metrics.

## VacationPy Analysis
In the VacationPy section, cities with ideal weather conditions were identified and visualized on a map with nearby hotels. Key steps include:
1. **Filtering Ideal Weather Conditions**: Criteria include temperature range, low wind speed, and zero cloudiness. This narrowed down the cities to ideal vacation locations.
2. **Hotel Search**: Using the Geoapify API to locate hotels near each selected city.
3. **Interactive Mapping**: Displaying each city on an interactive map, with hotel information and country displayed on hover.

### Map Specifications:
- Map points represent cities with ideal weather.
- Hover information includes city name, country, humidity level, and nearest hotel.

## Usage
1. **WeatherPy**:
   - Open `WeatherPy.ipynb` and execute each cell to gather weather data, run linear regression analyses, and create visualizations.
2. **VacationPy**:
   - Open `VacationPy.ipynb`, filter for ideal vacation conditions, and run the Geoapify API code to retrieve hotel information.
   - Visualize the data on an interactive map to see ideal vacation locations with nearby hotel details.

## Data Source
All data for this project was obtained from the OpenWeatherMap and Geoapify APIs.

## Code Source
This project was completed using class materials and assistance. All code was developed independently based on these resources.

## Disclaimer
This project includes sensitive information like API keys, which should be kept secure. Ensure that `api_keys.py` is excluded from version control by adding it to `.gitignore`.

## Example Usage of the APIs
To retrieve weather data using OpenWeatherMap:
```python
import requests

# Example API call
base_url = "http://api.openweathermap.org/data/2.5/weather"
params = {
    "q": "London",
    "appid": weather_api_key
}
response = requests.get(base_url, params=params)
data = response.json()
print(data)
