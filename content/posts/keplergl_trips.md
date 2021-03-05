+++
title = "Preparing GPS data for kepler.gl trip visualization"
description = ""
type = ["posts","post"]
tags = [
    "gps",
    "geospatial",
    "kepler.gl",
    "visualization",
    "data analytics",
]
date = "2021-03-05"
categories = [ 
"visualiztion",
]
series = ["Hugo 101"]
[ author ]
  name = "Ding Luo"
+++

Over the past years I have been using [kepler.gl](https://kepler.gl/) more and more often for geospatial visualiztion. The reason is
just simple: powerful, easy, fast. It serves as a perfect visualization tool for EDA tasks. Very often when I show
the visualization to my stakeholders, especially those who are from the traditional business side, they are immediately
impressed!

In this post, I want to simply share some python scripts for preparing GPS trajectory data for kepler.gl's [trip
visualization feature](https://docs.kepler.gl/docs/user-guides/c-types-of-layers/k-trip). This would help because
my experience is that most GPS trajectory data would share a similar structure with the key columns of trip ID, timestamp, 
latitude, and longitude. Such data are always stored and shared in a tabular form, thus could be directly loaded 
as a pandas dataframe. What the python scripts do is to further convert such a dataframe to the geojson file required by
kepler.gl.

This post is inspired by [one of the Geoff Boeing's posts](https://geoffboeing.com/2015/10/exporting-python-data-geojson/).
(Check out Geoff Boeing's awesome research and open source tool [osmnx](https://github.com/gboeing/osmnx) - ABSOLUTELY
a game changer for urban analytics!)
I modified his code by adding a time conversion function (timestamp to unix time string) and making the geojson
output compatible with kepler.gl's requirement.

The functions used are shown below.
```python
import json
import time

import numpy as np


def timestamp2unixtime(dt: str) -> int:
    """
    Convert a "Date Time" string to unix time string
    https://en.wikipedia.org/wiki/Unix_time
    Example:
        '2021-02-25 17:18:30' -> 1614269910
    """
    import time
    new_time = time.strptime(dt, "%Y-%m-%d %H:%M:%S")
    return int(time.mktime(new_time))


def df_to_geojson(df, properties, trip_id, timestamp, lat, lon):
    geojson = {
        "type": "FeatureCollection",
        "features": []
    }
    ls_trip_id = df[trip_id].unique().tolist()
    for trip_id in ls_trip_id:
        tmp_df = df[df[trip_id] == trip_id].copy()
        tmp_df.sort_values(by=timestamp, inplace=True)
        cur_feature = {
            "type": "Feature", 
            "properties": {}, 
            "geometry": {"type": "LineString"}
        }
        for prop in properties:
            prop_value = str(tmp_df[prop].iloc[0])
            cur_feature["properties"][prop] = prop_value
        
        coords = []
        for _, row in tmp_df.iterrows():
            dt = str(row[timestamp])
            unix_time = int(timestamp2unixtime(dt))
            longitude = round(row[lon], 6)
            latitude = round(row[lat], 6)
            if ~np.isnan(unix_time) \
                and ~np.isnan(longitude) \ 
                and ~np.isnan(latitude):
                point = [longitude, latitude, 0, unix_time]
                coords.append(point)
        cur_feature["geometry"]["coordinates"] = coords
        geojson["features"].append(cur_feature)

    return geojson


def save_geojson_file(filename, geojson):
    with open(filename, 'w') as fp:
        json.dump(geojson, fp)
```

To show an example, I found some cycling GPS data used in my master's thesis research back in Stockholm (-_-).
I will try to share the dataset as well.
But here we go with the cool visualization of all cycling trips!
<center>
<img src="../../../../img/cyclists.gif" width = "700" alt="quote" align=center />
</center>




    

