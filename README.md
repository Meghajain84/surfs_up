# surfs_up

# Overview of the statistical analysis:
We are looking into weather conditions in Oahu, HI in order to determine of surf and ice -cream shop is sustainable business. 
We have gathered the June and Dec temperature statistics from 12 years worth data as part of deliverable 1 and 2.

# Results: Three key differences in weather between June and December

**Refer the image below for the the key differences:**

![Jun_Dec_temp](https://github.com/Meghajain84/surfs_up/blob/main/Jun_Dec_temp.PNG)

* The minimum temperature in Dec is 8 degrees less in December than June, but not too low in December that people can't go for surfing or have ice cream
* There is a significant difference between counts of readings in June(1700) and December(1517); if December readings count was almoast same as June count, results would have been more accurate or comparable.
* Average and percentiles are about 4 degrees less in December as compared to June, which is not that much of the difference. 

# Summary: 
## A high-level summary of the results 
Looking at above results, temperature is less in December as compared to June, but it's not that bad that people won't go for surfing. 
The two additional queries in next section can give us better statistics.

## The two additional queries that you would perform to gather more weather data for June and December.
1)  Instead of looking 12 years of temperature data, I would rather compare temperature data from latest 5 years to be more accurate. The data given to us has latest year of 2017, hence I looked at data from 2012 and after. 
I would have used the below queries to gather only latest 5 years of temperature data in June and December.

    Dec_temp_measurement = session.query(Measurement.date, Measurement.tobs).filter((extract('month', Measurement.date) == 12) & (extract('year', Measurement.date) >= 2012)) 

    Jun_temp_measurement = session.query(Measurement.date, Measurement.tobs).filter((extract('month', Measurement.date) == 6) & (extract('year', Measurement.date) >= 2012)) 

This also shows same trend that December is bit colder than June.

2) Taking average of precipitation per month would really help in determing the success rate of surf shop
Query that I would use is as follows-

    res = session.query((extract('month', Measurement.date)), func.avg(Measurement.prcp)).group_by((extract('month', Measurement.date)))

This query shows that it rains bit more in November and December than summer months, but not too bad overall. 




