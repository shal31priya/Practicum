
#### Update



## Introduction

In this work, we aim to simplify the design of GCN to make it more concise and appropriate for recommendation. We propose a new model named LightGCN,including only the most essential component in GCN—neighborhood aggregation—for collaborative filtering



Flickr Data Refer the configuration manual



## Enviroment Requirement

`pip install -r requirements.txt`



## Dataset

We provide three processed datasets: Yelp2018 
see more in `dataloader.py`

## An example to run a 3-layer LightGCN





*NOTE*:

1. User-Item Matrix Splitting
Although we provide the option to split the user-item matrix for matrix multiplication, we strongly advise against enabling it as it significantly slows down the training speed.

Improving Test Process Speed
If you notice slow test execution, consider increasing the testbatch size and enabling the multicore option. (Note: The multicore option may cause issues on Windows systems.)

Using TensorBoard
We recommend using the tensorboard option as it provides valuable insights into the training process.

Reproducibility
We set fixed seeds (--seed=2020) for both numpy and torch to ensure reproducibility. Running the commands as outlined will produce the same output logs, even if the training times vary (e.g., check the outputs for epoch 5 and epoch 116).

Extending the System
Running LightGCN on Custom Datasets
To run LightGCN on your own dataset, modify the dataloader.py file by implementing a custom dataloader inherited from BasicDataset, and then register it in register.py.

Using Custom Models
To run your own models on the provided datasets, implement your model in model.py, inheriting from BasicModel, and register it in register.py.

Implementing Custom Sampling Methods
If you want to apply custom sampling methods, modify Procedure.py to include your function, and then update the corresponding code in main.py.

## Results
*all metrics is under top-20*

***pytorch* version results** (stop at 1000 epochs):

(*for seed=2020*)


* yelp2018

|             | Recall | ndcg | precision |
| ----------- | ---------------------------- | ----------------- | ---- |
| **layer=1** | 0.05604     | 0.04557 | 0.02519 |
| **layer=2** | 0.05988               | 0.04956 | 0.0271 |
| **layer=3** | 0.06347          | 0.05238 | 0.0285 |
| **layer=4** | 0.06515                | 0.05325 | 0.02917 |


Folder Structure of Travel_cp

├── Data Processing and Analysis
│   ├── DA_Cleaning_Business.ipynb
│   ├── DA_Review.ipynb
│   ├── example_plot
│   ├── loss.png
│   ├── mkyelp2018.py
│   ├── ndcg-recalll.png
│   ├── nohup.out
│   ├── plot.ipynb
│   └── yelp-json-EDA.ipynb
├── Procedure.py
├── __pycache__
│   ├── Procedure.cpython-311.pyc
│   ├── dataloader.cpython-311.pyc
│   ├── filter.cpython-311.pyc
│   ├── idIndex.cpython-311.pyc
│   ├── model.cpython-311.pyc
│   ├── parse.cpython-311.pyc
│   ├── rcmdweb.cpython-311.pyc
│   ├── recommendation.cpython-311.pyc
│   ├── register.cpython-311.pyc
│   ├── utils.cpython-311.pyc
│   └── world.cpython-311.pyc
├── checkpoints
│   └── lgn-yelp2018-3-64.pth.tar
├── dataloader.py
├── filter.py
├── idIndex.py
├── model.py
├── parse.py
├── recommendation.py
├── register.py
├── train.py
├── utils.py
└── world.py

###Weather data 
It initially began as an exploratory analysis on weather data but evolved int  comprehensive travel recommendation application that provides travel and hotel suggestions based on user weather preferences.

Data Collection
Data was sourced from various open-source APIs:

Weather Data: Collected from the OpenWeatherMap API.
City Locations: Retrieved using CitiPy.
Hotel & Map Information: Created using the Google Maps API.
Weather Analysis
The project involved analyzing key weather metrics such as temperature, humidity, cloudiness, and wind speed. The analysis was split by hemispheres and visualized with regression and heat maps.

WeatherPy.ipynb contains detailed analysis, including:
Regression analysis (Northern and Southern Hemispheres)
Heat maps of weather parameters by latitude
Key Figures
Weather by Latitude:

Latitude vs Temperature

Latitude vs Humidity

Latitude vs Cloudiness

Latitude vs Wind Speed

Linear Regression by Hemisphere:

Northern Hemisphere (Temperature, Humidity, Cloudiness, Wind Speed)
Southern Hemisphere (Temperature, Humidity, Cloudiness, Wind Speed)
Heat Maps:

Temperature

Humidity

Cloudiness

Wind Speed

Travel Recommendation Software
The core of this project is a recommendation system that provides travel suggestions based on user-preferred weather conditions. There are two main components:

City-based Weather Recommendations: The user inputs their preferred weather conditions, and the software provides a list of cities matching those preferences.

Itinerary-Based Travel Recommendations: This program suggests four nearby cities within the same country with matching weather, along with accommodation details.

Data
A larger dataset was collected from OpenWeatherMap to feed into both recommendation systems. The dataset and collection files can be found in the weather_database folder.

Vacation Search
The first program generates a map showing popular accommodations, city locations, and current weather for cities worldwide. This map is displayed to users as part of the vacation search feature.

Sample Output:
The vacation_search folder contains all relevant files, data, and images.

Vacation Itinerary
The second program recommends an itinerary of four nearby cities that match the user’s desired weather. The program outputs:

A navigation map between the cities.

Accommodation and weather details for each city.

The final destination matches the first city for ease of return travel.

Sample Output:

Navigation Map

Accommodation and Weather Map

All relevant files, data, and images are stored in the vacation_itinerary folder.

Technologies Used
Pandas: Data manipulation and analysis
Numpy: Numerical computations
Matplotlib: Data visualization
SciPy: Statistical analysis
OpenWeatherMap API: Weather data
Google Maps API: City locations and maps
Python: Programming language used for development
This version condenses the details into a more structured, concise format s





My github Link https://github.com/shal31priya/Practicum
