# tinyMeteo: A Weather Prediction Project using TinyML and Python

## Project Overview

TinyMeteo is a machine learning project that uses Tiny Machine Learning (TinyML) and Python to predict weather conditions based on temperature, humidity, and pressure data. The project utilizes an Arduino Nano 33 Sense board to collect environmental data, which is then processed and fed into a machine learning model to predict the weather conditions.

The dataset for this project is obtained from World Weather Online, and contains environmental data such as temperature, humidity, and pressure. JSON-formatted data  over a 13 year period for Athens in Greece collected, filtered and parsed into CSV format for easier handling.

Linear regression is selected as the machine learning model for this project, as it is well-suited for predicting continuous numerical values such as temperature and pressure. Once the model is trained, it is evaluated using standard machine learning metrics such as mean squared error (MSE) and coefficient of determination (R-squared) to assess its accuracy and performance.

The trained model is then deployed onto the Arduino Nano 33 Sense board using the TensorFlow Lite for Microcontrollers (TFLite Micro) library. This enables the board to make real-time weather predictions based on the current temperature, humidity, and pressure readings.

<br>

### Tools and Technologies:
- Arduino Nano 33 BLE Sense Rev2
- Python
- REST APIs
- Node.js, Express.js
- Angular
- Tensorflow, Tensorflow Lite Micro
  

  </br>
## Data Details
Historical weather data is obtained via [World Weather Online](https://www.worldweatheronline.com) APIs for the exact location where weather predictions will be tested.
- Location: Athens, Greece
- Duration: between 1. January 2009 and 31. December 2022
- API Endpoint: https://api.worldweatheronline.com/premium/v1/past-weather.ashx
- API Documentation: https://www.worldweatheronline.com/weather-api/api/docs/historical-weather-api.aspx#qparameter    


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

