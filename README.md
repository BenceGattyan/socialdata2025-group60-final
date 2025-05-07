# Final assignment for group 60: Traffic data of copenhagen

Data gathered from:__
Traffic data: https://www.opendata.dk/city-of-copenhagen/faste-trafiktaellinger __
Weather data: https://open-meteo.com/en/docs/historical-weather-api?start_date=2005-01-01&end_date=2014-12-31&timezone=auto&latitude=55.6806&longitude=12.5492&hourly=temperature_2m,relative_humidity_2m,rain,snowfall,wind_speed_10m,weather_code,apparent_temperature,cloud_cover __
Holiday data: https://www.timeanddate.com/holidays/denmark/ __
Holidays couldn't be directly obtained as csv so I scraped each relevant year by hand into a csv file.__

trafficconverter.ipynb removes the first few not needed rows of the original dataset and__
converts the UTM32 coordinates to lat and long and saves each year into new csv files

datacombiner works with these new files and the holiday and weather dataset and combines them__
it first reorders the traffic dataset so instead of the rows differenciating station and date while columns differentiate hours__
it'll have datetime in rows and each station has it's own column.

because not every station is present for every year some values will be missing, these are marked by traffic count = -1

Current format of dataset:

datetime: date and time in yyyy-mm-dd hh:mm:ss__
station1 +: incoming traffic count for station 1__
station1 -: outgoing traffic count for station 1__
station1 T: total traffic count for station 1__
... __
stationN +: incoming traffic count for station N__
stationN -: outgoing traffic count for station N__
stationN T: total traffic count for station N     (note: station is actually identified by it's id and not exactly like this)__
temperature_2m (C): Air temperature at 2 meters above ground__
relative_humidity_2m (%): Relative humidity at 2 meters above ground__
rain (mm): Preceding hour sum of rainfall__
snowfall (cm): Preceding hour sum of snowfall__
wind_wind_speed_10m (km/h): Wind speed at meters above ground__
weather_code (wmo code): Weather condition as a numeric code. Follow WMO weather interpretation codes__
appearent_temperature (C): Apparent temperature is the perceived feels-like temperature combining wind chill factor, relative humidity and solar radiation__
cloud_cover (%): Total cloud cover as an area fraction__
DayOfWeek: Day of week ("Monday", "Tuesday" etc)__
isHoliday: boolean indicator of holiday__
isWeekend:  boolean indicator of Weekend__
isWeekday:  boolean indicator of Weekday__
holidayName: name of Holiday (NaN if isHoliday is False) (example: New Year's Day)__
holidayType: type of Holiday (NaN if isHoliday is False) (example: National Holiday)__