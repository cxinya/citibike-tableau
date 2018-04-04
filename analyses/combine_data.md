

```python
import os
import pandas as pd
```


```python
# CSVs to read in 

all_files = os.listdir("../data")
files_2017 = all_files[0:12]
files_2018 = all_files[12:]
```


```python
# Read in data

dfs_2017 = [pd.read_csv(f'../data/{file}') for file in files_2017]
dfs_2018 = [pd.read_csv(f'../data/{file}') for file in files_2018]
```


```python
# Change column names - 2017
for file in dfs_2017:
    file.columns = ['Trip Duration',
                    'Start Time',
                    'Stop Time',
                    'Start Station ID',
                    'Start Station Name',
                    'Start Station Latitude',
                    'Start Station Longitude',
                    'End Station ID',
                    'End Station Name',
                    'End Station Latitude',
                    'End Station Longitude',
                    'Bike ID',
                    'User Type',
                    'Birth Year',
                    'Gender']
```


```python
# Change column names - 2018
for file in dfs_2018:
    file.columns = ['Trip Duration',
                    'Start Time',
                    'Stop Time',
                    'Start Station ID',
                    'Start Station Name',
                    'Start Station Latitude',
                    'Start Station Longitude',
                    'End Station ID',
                    'End Station Name',
                    'End Station Latitude',
                    'End Station Longitude',
                    'Bike ID',
                    'delete',
                    'User Type',
                    'Birth Year',
                    'Gender']
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-5-c74bc347b005> in <module>()
         16                     'User Type',
         17                     'Birth Year',
    ---> 18                     'Gender']
    

    C:\Users\Cynthia\Anaconda3\lib\site-packages\pandas\core\generic.py in __setattr__(self, name, value)
       2981         try:
       2982             object.__getattribute__(self, name)
    -> 2983             return object.__setattr__(self, name, value)
       2984         except AttributeError:
       2985             pass
    

    pandas\_libs\src\properties.pyx in pandas._libs.lib.AxisProperty.__set__ (pandas\_libs\lib.c:45103)()
    

    C:\Users\Cynthia\Anaconda3\lib\site-packages\pandas\core\generic.py in _set_axis(self, axis, labels)
        469 
        470     def _set_axis(self, axis, labels):
    --> 471         self._data.set_axis(axis, labels)
        472         self._clear_item_cache()
        473 
    

    C:\Users\Cynthia\Anaconda3\lib\site-packages\pandas\core\internals.py in set_axis(self, axis, new_labels)
       2834             raise ValueError('Length mismatch: Expected axis has %d elements, '
       2835                              'new values have %d elements' %
    -> 2836                              (old_len, new_len))
       2837 
       2838         self.axes[axis] = new_labels
    

    ValueError: Length mismatch: Expected axis has 15 elements, new values have 16 elements



```python
# Create dfs for 2017
df_2017 = pd.concat(dfs_2017)
df_2017.head(2)
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Trip Duration</th>
      <th>Start Time</th>
      <th>Stop Time</th>
      <th>Start Station ID</th>
      <th>Start Station Name</th>
      <th>Start Station Latitude</th>
      <th>Start Station Longitude</th>
      <th>End Station ID</th>
      <th>End Station Name</th>
      <th>End Station Latitude</th>
      <th>End Station Longitude</th>
      <th>Bike ID</th>
      <th>User Type</th>
      <th>Birth Year</th>
      <th>Gender</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>148</td>
      <td>2017-01-01 00:21:32</td>
      <td>2017-01-01 00:24:01</td>
      <td>3276</td>
      <td>Marin Light Rail</td>
      <td>40.714584</td>
      <td>-74.042817</td>
      <td>3185</td>
      <td>City Hall</td>
      <td>40.717733</td>
      <td>-74.043845</td>
      <td>24575</td>
      <td>Subscriber</td>
      <td>1983.0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1283</td>
      <td>2017-01-01 00:24:35</td>
      <td>2017-01-01 00:45:58</td>
      <td>3183</td>
      <td>Exchange Place</td>
      <td>40.716247</td>
      <td>-74.033459</td>
      <td>3198</td>
      <td>Heights Elevator</td>
      <td>40.748716</td>
      <td>-74.040443</td>
      <td>24723</td>
      <td>Subscriber</td>
      <td>1978.0</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Create dfs for 2018

df_2018 = pd.concat(dfs_2018)
df_2018 = df_2018.drop(['delete'], axis = 1)
df_2018.head(2)
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bike ID</th>
      <th>Birth Year</th>
      <th>End Station ID</th>
      <th>End Station Latitude</th>
      <th>End Station Longitude</th>
      <th>End Station Name</th>
      <th>Gender</th>
      <th>Start Station ID</th>
      <th>Start Station Latitude</th>
      <th>Start Station Longitude</th>
      <th>Start Station Name</th>
      <th>Start Time</th>
      <th>Stop Time</th>
      <th>Trip Duration</th>
      <th>User Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>29590</td>
      <td>1964.0</td>
      <td>3211</td>
      <td>40.721525</td>
      <td>-74.046305</td>
      <td>Newark Ave</td>
      <td>1</td>
      <td>3186</td>
      <td>40.719586</td>
      <td>-74.043117</td>
      <td>Grove St PATH</td>
      <td>2018-01-01 00:01:46</td>
      <td>2018-01-01 00:03:58</td>
      <td>132</td>
      <td>Subscriber</td>
    </tr>
    <tr>
      <th>1</th>
      <td>29613</td>
      <td>1989.0</td>
      <td>3269</td>
      <td>40.726012</td>
      <td>-74.050389</td>
      <td>Brunswick &amp; 6th</td>
      <td>2</td>
      <td>3276</td>
      <td>40.714584</td>
      <td>-74.042817</td>
      <td>Marin Light Rail</td>
      <td>2018-01-01 01:27:17</td>
      <td>2018-01-01 01:36:38</td>
      <td>560</td>
      <td>Subscriber</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Create final df

df_final = pd.concat([df_2017,df_2018])

# Check head
df_final.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bike ID</th>
      <th>Birth Year</th>
      <th>End Station ID</th>
      <th>End Station Latitude</th>
      <th>End Station Longitude</th>
      <th>End Station Name</th>
      <th>Gender</th>
      <th>Start Station ID</th>
      <th>Start Station Latitude</th>
      <th>Start Station Longitude</th>
      <th>Start Station Name</th>
      <th>Start Time</th>
      <th>Stop Time</th>
      <th>Trip Duration</th>
      <th>User Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>24575</td>
      <td>1983.0</td>
      <td>3185</td>
      <td>40.717733</td>
      <td>-74.043845</td>
      <td>City Hall</td>
      <td>1</td>
      <td>3276</td>
      <td>40.714584</td>
      <td>-74.042817</td>
      <td>Marin Light Rail</td>
      <td>2017-01-01 00:21:32</td>
      <td>2017-01-01 00:24:01</td>
      <td>148</td>
      <td>Subscriber</td>
    </tr>
    <tr>
      <th>1</th>
      <td>24723</td>
      <td>1978.0</td>
      <td>3198</td>
      <td>40.748716</td>
      <td>-74.040443</td>
      <td>Heights Elevator</td>
      <td>1</td>
      <td>3183</td>
      <td>40.716247</td>
      <td>-74.033459</td>
      <td>Exchange Place</td>
      <td>2017-01-01 00:24:35</td>
      <td>2017-01-01 00:45:58</td>
      <td>1283</td>
      <td>Subscriber</td>
    </tr>
    <tr>
      <th>2</th>
      <td>24620</td>
      <td>1989.0</td>
      <td>3211</td>
      <td>40.721525</td>
      <td>-74.046305</td>
      <td>Newark Ave</td>
      <td>1</td>
      <td>3183</td>
      <td>40.716247</td>
      <td>-74.033459</td>
      <td>Exchange Place</td>
      <td>2017-01-01 00:38:19</td>
      <td>2017-01-01 00:44:31</td>
      <td>372</td>
      <td>Subscriber</td>
    </tr>
    <tr>
      <th>3</th>
      <td>24668</td>
      <td>1961.0</td>
      <td>3271</td>
      <td>40.692640</td>
      <td>-74.088012</td>
      <td>Danforth Light Rail</td>
      <td>1</td>
      <td>3194</td>
      <td>40.725340</td>
      <td>-74.067622</td>
      <td>McGinley Square</td>
      <td>2017-01-01 00:38:37</td>
      <td>2017-01-01 01:03:50</td>
      <td>1513</td>
      <td>Subscriber</td>
    </tr>
    <tr>
      <th>4</th>
      <td>26167</td>
      <td>1993.0</td>
      <td>3203</td>
      <td>40.727596</td>
      <td>-74.044247</td>
      <td>Hamilton Park</td>
      <td>1</td>
      <td>3183</td>
      <td>40.716247</td>
      <td>-74.033459</td>
      <td>Exchange Place</td>
      <td>2017-01-01 01:47:52</td>
      <td>2017-01-01 01:58:31</td>
      <td>639</td>
      <td>Subscriber</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Check tail
df_final.tail()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bike ID</th>
      <th>Birth Year</th>
      <th>End Station ID</th>
      <th>End Station Latitude</th>
      <th>End Station Longitude</th>
      <th>End Station Name</th>
      <th>Gender</th>
      <th>Start Station ID</th>
      <th>Start Station Latitude</th>
      <th>Start Station Longitude</th>
      <th>Start Station Name</th>
      <th>Start Time</th>
      <th>Stop Time</th>
      <th>Trip Duration</th>
      <th>User Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>32340</th>
      <td>24551</td>
      <td>1956.0</td>
      <td>3203</td>
      <td>40.727596</td>
      <td>-74.044247</td>
      <td>Hamilton Park</td>
      <td>1</td>
      <td>3186</td>
      <td>40.719586</td>
      <td>-74.043117</td>
      <td>Grove St PATH</td>
      <td>2017-03-10 17:39:03</td>
      <td>2017-03-10 17:44:18</td>
      <td>315</td>
      <td>Subscriber</td>
    </tr>
    <tr>
      <th>32341</th>
      <td>24462</td>
      <td>1995.0</td>
      <td>3277</td>
      <td>40.714358</td>
      <td>-74.066611</td>
      <td>Communipaw &amp; Berry Lane</td>
      <td>1</td>
      <td>3185</td>
      <td>40.717732</td>
      <td>-74.043845</td>
      <td>City Hall</td>
      <td>2017-03-10 17:39:21</td>
      <td>2017-03-13 08:12:46</td>
      <td>221604</td>
      <td>Subscriber</td>
    </tr>
    <tr>
      <th>32342</th>
      <td>24541</td>
      <td>1988.0</td>
      <td>3276</td>
      <td>40.714584</td>
      <td>-74.042817</td>
      <td>Marin Light Rail</td>
      <td>1</td>
      <td>3183</td>
      <td>40.716247</td>
      <td>-74.033459</td>
      <td>Exchange Place</td>
      <td>2017-03-10 17:40:03</td>
      <td>2017-03-10 17:44:13</td>
      <td>250</td>
      <td>Subscriber</td>
    </tr>
    <tr>
      <th>32343</th>
      <td>24608</td>
      <td>1964.0</td>
      <td>3195</td>
      <td>40.730743</td>
      <td>-74.063784</td>
      <td>Sip Ave</td>
      <td>1</td>
      <td>3280</td>
      <td>40.719282</td>
      <td>-74.071262</td>
      <td>Astor Place</td>
      <td>2017-03-10 17:40:07</td>
      <td>2017-03-10 17:47:53</td>
      <td>465</td>
      <td>Subscriber</td>
    </tr>
    <tr>
      <th>32344</th>
      <td>26311</td>
      <td>1965.0</td>
      <td>3279</td>
      <td>40.721630</td>
      <td>-74.049968</td>
      <td>Dixon Mills</td>
      <td>1</td>
      <td>3267</td>
      <td>40.712419</td>
      <td>-74.038526</td>
      <td>Morris Canal</td>
      <td>2017-03-10 17:40:36</td>
      <td>2017-03-10 17:47:35</td>
      <td>418</td>
      <td>Subscriber</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_final.to_csv("../data/final_citibike_data.csv", index = False)
```
