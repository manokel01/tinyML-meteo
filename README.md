# tinyMeteo

## Project Overview

The objective of this project is to build a weather prediction system using tinyML. The system will collect data from environmental sensors and use that data to train a neural network model. Once the model is trained, it will be deployed onto a microcontroller for use in real-time weather prediction. The overall goal of this project is to develop a highly accurate weather prediction system that can be used in a variety of applications, from agriculture to transportation. By leveraging the power of tinyML, we can build a system that is highly efficient, cost-effective, and can be deployed in even the most remote locations.

<br>

## A. Data Source
Historical weather data is obtained via [World Weather Online](https://www.worldweatheronline.com) APIs for the exact location where weather predictions will be tested.
- Location: Athens, Greece
- Duration: between 1. January 2009 and 31. December 2022
- Endpoint: HTTPS: https://api.worldweatheronline.com/premium/v1/past-weather.ashx
- API Documentation: https://www.worldweatheronline.com/weather-api/api/docs/historical-weather-api.aspx#qparameter    
  
<br>

## B. API Response of datasets:

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

## C. Data Collection

Since the API only allows for data up to 30 days to be accesses each time, a Python script (data_scrapper.py) was used to collect all data for the required duration.

<br>

## C. Data Filtering and Formatting

The desired data is extracted for the values of temperature, humidity, pressure and weather conditions (e.g. "Sunny", "Cloudy", etc) and converted into a single CSV file for easier processing.

<br>

