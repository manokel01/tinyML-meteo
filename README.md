# tinyMeteo

## Project Overview

The objective of this project is to build a weather prediction system using tinyML. The system will collect data from environmental sensors and use that data to train a neural network model. Once the model is trained, it will be deployed onto a microcontroller for use in real-time weather prediction. The overall goal of this project is to develop a highly accurate weather prediction system that can be used in a variety of applications, from agriculture to transportation. By leveraging the power of tinyML, we can build a system that is highly efficient, cost-effective, and can be deployed in even the most remote locations.



### A. The Data
Historical weather data is obtained via https://www.worldweatheronline.com/ APIs for the exact location where weather predictions will tested.
Data between 1. July 2007 and 1. January 2023 for a particular location in Athens Greece (37.995453,23.792475).

   - GET Request: http://api.worldweatheronline.com/premium/v1/past-weather.ashx?q=37.995453,23.792475&date=2008-07-01&key=913fd593e9a8439490861717230805&format=json&tp=1&enddate=2023-01-01
   - Response Elements: https://www.worldweatheronline.com/weather-api/api/docs/historical-weather-api.aspx#qparameter

## A. Data Source
Historical weather data is obtained via [World Weather Online](https://www.worldweatheronline.com) APIs for the exact location where weather predictions will be tested.
- Location: Athens, Greece
- Duration: between 1. July 2008 and 31. December 2022 for a particular location in Athens Greece (37.995453,23.792475).
- Endpoint: HTTPS: https://api.worldweatheronline.com/premium/v1/past-weather.ashx
- Documentation: https://www.worldweatheronline.com/weather-api/api/docs/historical-weather-api.aspx#qparameter    
<br>

## B. Data Collection

Since the API only allows for data up to 30 days to be accesses each time, a Python script (data_scrapper.py) was used to collect all data for the required duration (1/7/2008 - 31/12/2022).

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

### A. tinyML

1. Data Collection:
   - The relevant environmental values are temperature, humidity and barometric pressure correspoonding to available sensors of the Arduino Nano 33 Sense BLE.
   - Download temperature, humidity and barometric pressure  data in CSV format from Kaggle.com
   - Process data.
2. Model Training:
   - Use TensorFlow to build and train a neural network model for weather prediction, using the data collected from the sensors as input.
   - Optimize the trained model for deployment on a microcontroller by converting it to a TensorFlow Lite format.
3. Model Deployment:
   - Deploy the optimized TensorFlow Lite model onto the Arduino Nano 33 Sense BLE using the TensorFlow Lite Micro framework.
   - Write code to load the model onto the microcontroller and integrate it with the sensor data collection module.
   - Use the deployed model to generate weather predictions in real-time.
4. Testing and Validation:
   - Test the system by collecting data from the environmental sensors and comparing the predictions generated by the model with actual weather conditions.
   - Evaluate the performance of the system and make any necessary adjustments to improve the accuracy of the weather predictions.
5. Documentation:
   - Document the project by creating a detailed report that includes the system design, implementation details, and performance evaluation.
   - Include code samples, diagrams, and other relevant information that can help others to understand and replicate the project.

### B. Collect Sensor Data in Database
Firebase:
1. Create a Firebase project:
   - Go to the Firebase Console and create a new project.
   - Follow the prompts to set up the project and choose a name for your database.

2. Set up the Firebase SDK:
   - Install the Firebase SDK for your programming language of choice.
   - Initialize the SDK with your Firebase project credentials.

3. Configure the database rules:
   - Set up security rules for your Firebase database to ensure that only authorized users can read or write data.
   - For example, the following rules allow only authenticated users to write data to a "sensor_data" collection in the database:
     ```
     rules_version = '2';
     service cloud.firestore {
       match /databases/{database}/documents {
         match /sensor_data/{document=**} {
           allow write: if request.auth != null;
         }
       }
     }
     ```

4. Collect and format the sensor data:
   - Collect the sensor data using your Arduino or other microcontroller.
   - Format the data in a suitable format for storage in a Firebase database, such as JSON.
   - For example, the following code formats sensor data as a JSON object:
     ```
     // Collect sensor data
     float temperature = read_temperature();
     float humidity = read_humidity();
     
     // Format as JSON
     String data = "{\"temperature\": " + String(temperature) + ", \"humidity\": " + String(humidity) + "}";
     ```

5. Store the data in the Firebase database:
   - Use the Firebase SDK to store the sensor data in the Firebase database.
   - For example, the following code stores the sensor data in a "sensor_data" collection in the database:
     ```
     // Store sensor data
     firebase.firestore().collection("sensor_data").add(JSON.parse(data));
     ```

6. Verify the data is being stored:
   - Check the Firebase console to ensure that the data is being stored correctly.
   - Review the database rules to ensure that the data can be accessed only by authorized users.


### C. Visualize Database Data and Predictions
Develop an AngularJS front-end that displays the predictions from the TinyML model in a user-friendly manner. Consider using visualization tools such as charts and graphs to help users track their movement patterns throughout the day.

### Tools and Technologies:
- Arduino Nano 33 BLE Sense Rev2
- Python
- REST APIs
- Node.js, Express.js
- Angular
- Tensorflow, Tensorflow Lite Micro

