
## Bash Script (sampling.sh) to Download-Extract-Merge-Sampling from a link of online Excel file (aditya-66kK)

### Must install ```pip``` in order to make the script works.

0. install all dependencies using ```pip install -r requirements.txt```

#### Steps explained below:

1. Downloading data and put inside folder **data**
```
wget -P ./data https://github.com/labusiam/dataset/raw/main/weather_data.xlsx
```


2. Extracting data from original excel file

- Extract weather data from **2014** year
```
in2csv ./data/weather_data.xlsx --sheet "weather_2014">./data/weather_2014.csv
```

- Extract weather data from **2015** year
```
in2csv ./data/weather_data.xlsx --sheet "weather_2015">./data/weather_2015.csv
```

3. Merge and remove
- **Merge** 2014 and 2015 into one csv file
```
csvstack ./data/weather_2014.csv ./data/weather_2015.csv >./data/weather.csv
```
- **Remove** excel original data
```
rm ./data/weather_data.xlsx
```

4. **Sampling** the merged data with 0.3 sampling rate
```
cat ./data/weather.csv | sample --rate 0.3 > ./data/sample_weather.csv
```
