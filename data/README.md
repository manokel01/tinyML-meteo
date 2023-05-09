# tinyMeteo - Data

## A. Data Source
Historical weather data is obtained via [World Weather Online](https://www.worldweatheronline.com) APIs for the exact location where weather predictions will be tested.
- Location: Athens, Greece
- Duration: between 1. July 2008 and 31. December 2022 for a particular location in Athens Greece (37.995453,23.792475).
- Endpoint: HTTPS: https://api.worldweatheronline.com/premium/v1/past-weather.ashx
- Documentation: https://www.worldweatheronline.com/weather-api/api/docs/historical-weather-api.aspx#qparameter    
<br>

## B. Data Collection

Since the API only allows for data up to 30 days to be accesses each time, a Python script was used to collect all data for the required duration (1/7/2008 - 31/12/2022).

The Python scrapper snippet:

```
import requests
import json
import os
from calendar import monthrange

api_key = '913fd593e9a8439490861717230805'
location = '37.995453,23.792475'
start_year = 2008
end_year = 2022

for year in range(start_year, end_year+1):
    for month in range(1, 13):
        _, num_days = monthrange(year, month)
        start_date = f'{year}-{month:02d}-01'
        end_date = f'{year}-{month:02d}-{num_days:02d}'
        url = f'https://api.worldweatheronline.com/premium/v1/past-weather.ashx?key={api_key}&q={location}&format=json&date={start_date}&enddate={end_date}'
        response = requests.get(url)
        data = response.json()
        filename = f'Papagou_{year}-{month:02d}.json'
        with open(os.path.join('weather_data', filename), 'w') as f:
            json.dump(data, f)

```
<br>

## C. Data Format

The data is collected in JSON format:

```
{
    "data": {
      "request": [
        {
          "type": "LatLon",
          "query": "Lat 38.00 and Lon 23.79"
        }
      ],
      "weather": [
        {
          "date": "2008-07-01",
          "astronomy": [
            {
              "sunrise": "06:06 AM",
              "sunset": "08:51 PM",
              "moonrise": "03:47 AM",
              "moonset": "07:37 PM",
              "moon_phase": "Waning Crescent",
              "moon_illumination": "4"
            }
          ],
          "maxtempC": "32",
          "maxtempF": "89",
          "mintempC": "22",
          "mintempF": "72",
          "avgtempC": "27",
          "avgtempF": "81",
          "totalSnow_cm": "0.0",
          "sunHour": "14.0",
          "uvIndex": "7",
          "hourly": [
            {
              "time": "0",
              "tempC": "23",
              "tempF": "74",
              "windspeedMiles": "8",
              "windspeedKmph": "13",
              "winddirDegree": "328",
              "winddir16Point": "NNW",
              "weatherCode": "113",
              "weatherIconUrl": [
                {
                  "value": "https://cdn.worldweatheronline.com/images/wsymbols01_png_64/wsymbol_0008_clear_sky_night.png"
                }
              ],
              "weatherDesc": [
                {
                  "value": "Clear"
                }
              ],
              "precipMM": "0.0",
              "precipInches": "0.0",
              "humidity": "51",
              "visibility": "10",
              "visibilityMiles": "6",
              "pressure": "1013",
              "pressureInches": "30",
              "cloudcover": "3",
              "HeatIndexC": "25",
              "HeatIndexF": "77",
              "DewPointC": "12",
              "DewPointF": "54",
              "WindChillC": "23",
              "WindChillF": "74",
              "WindGustMiles": "14",
              "WindGustKmph": "23",
              "FeelsLikeC": "25",
              "FeelsLikeF": "77",
              "uvIndex": "1"
            },
            {
              "time": "100",
              "tempC": "23",
              "tempF": "73",
              "windspeedMiles": "7",
              "windspeedKmph": "11",
              "winddirDegree": "331",
              "winddir16Point": "NNW",
              "weatherCode": "113",
              "weatherIconUrl": [
                {
                  "value": "https://cdn.worldweatheronline.com/images/wsymbols01_png_64/wsymbol_0008_clear_sky_night.png"
                }
              ],
              "weatherDesc": [
                {
                  "value": "Clear"
                }
              ],
              "precipMM": "0.0",
              "precipInches": "0.0",
              "humidity": "52",
              "visibility": "10",
              "visibilityMiles": "6",
              "pressure": "1013",
              "pressureInches": "30",
              "cloudcover": "3",
              "HeatIndexC": "25",
              "HeatIndexF": "77",
              "DewPointC": "13",
              "DewPointF": "55",
              "WindChillC": "23",
              "WindChillF": "73",
              "WindGustMiles": "14",
              "WindGustKmph": "22",
              "FeelsLikeC": "25",
              "FeelsLikeF": "77",
              "uvIndex": "1"
            },
         ...
```