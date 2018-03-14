
# For loops Lab

### Learning Objectives

* Understand how for loops can help us reduce repetition
* Understand the syntax of for loops 

### Picking up where we last left off

In the last lesson, we plotted some of our travel data.


```python
import pandas
file_name = './cities.xlsx'
travel_df = pandas.read_excel(file_name)
cities = travel_df.to_dict('records')
```


```python
import plotly

plotly.offline.init_notebook_mode(connected=True)

x_values = [cities[0]['City'], cities[1]['City'], cities[2]['City']]
y_values = [cities[0]['Population'], cities[1]['Population'], cities[2]['Population']]
trace_first_three_pops = {'x': x_values, 'y': y_values, 'type': 'bar'}
plotly.offline.iplot([trace_first_three_pops])
```


<script>requirejs.config({paths: { 'plotly': ['https://cdn.plot.ly/plotly-latest.min']},});if(!window.Plotly) {{require(['plotly'],function(plotly) {window.Plotly=plotly;});}}</script>



<div id="8923027b-3a3c-4a34-b486-6978ab1ade64" style="height: 525px; width: 100%;" class="plotly-graph-div"></div><script type="text/javascript">require(["plotly"], function(Plotly) { window.PLOTLYENV=window.PLOTLYENV || {};window.PLOTLYENV.BASE_URL="https://plot.ly";Plotly.newPlot("8923027b-3a3c-4a34-b486-6978ab1ade64", [{"x": ["Solta", "Greenville", "Buenos Aires"], "y": [1700, 84554, 13591863], "type": "bar"}], {}, {"showLink": true, "linkText": "Export to plot.ly"})});</script>


In this lesson, we will use our `for` loop to display information about our travel locations.

### Learning Objectives

### Introduction to the For Loop

Our `cities` list contains information about the top 12 cities.  For our upcoming iteration tasks, it will be useful to have a list of the numbers 0 through 11.  Use what we know about `len` and `range`to generate a list of numbers 1 through 11.  Assign this to a variable called `city_indices`.


```python
city_indices = list(range(0, len(cities)))
city_indices # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11]
```




    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11]



Now we want to create labels for each of the cities. We'll provide a list of the `citie_names` for you. 


```python
city_names = ['Solta', 'Greenville', 'Buenos Aires', 'Los Cabos', 'Walla Walla Valley', 'Marakesh', 
              'Albuquerque', 'Archipelago Sea', 'Iguazu Falls', 'Salina Island', 'Toronto', 'Pyeongchang']
```

Your task is to assign the variable `names_and_ranks` equal to a list, with each element equal to the city name and it's corresponding rank.  For example, the first element would be, `"1. Solta"` and the second would be `"2. Greenville"`.  Use a `for` loop, `city_indices` and `city_names` to accomplish this.


```python
names_and_ranks = ['change this'] # make sure the list is empty
```


```python
names_and_ranks[0] # '1. Solta'
names_and_ranks[-1] # '12. Pyeongchang'
```




    'change this'



Ok, now let's create a new variable called `city_populations`.  Use a `for` loop to iterate through `cities` and have `city_populations` equal to each of the populations.


```python
city_populations = []
```


```python
city_populations
```

Great! Now we can begin to plot this data.  First, let's create a trace of our populations and set it to the variable `trace_populations`.


```python
trace_populations = {'x': names_and_ranks, 'y': city_populations, 'text': names_and_ranks, 'type': 'bar', 'name': 'populations'}
```


```python
import plotly
plotly.offline.init_notebook_mode(connected=True)
plotly.offline.iplot([trace_populations])
```

Now we want declare a variable called `city_areas` that points to a list of all of the areas of the cities.  Let's use a `for` loop to iterate through our `cities` and have `city_areas` equal to each area of the city.  


```python
city_areas = []
```


```python
trace_areas = {'x': names_and_ranks, 'y': city_areas, 'text': names_and_ranks, 'type': 'bar', 'name': 'areas'}
```


```python
import plotly
plotly.offline.init_notebook_mode(connected=True)
plotly.offline.iplot([trace_populations, trace_areas])
```

Ok, let's just plot the middle areas separately now.


```python
import plotly
plotly.offline.init_notebook_mode(connected=True)
plotly.offline.iplot([middle_trace_areas])
```

### Summary

In this section we saw how we can use `for` loops to go through elements of a list and perform the same operation on each.  With using `for` loops we were able to reduce the amount of code that we wrote and write more expressive code.
