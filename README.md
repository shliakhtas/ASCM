# ASCM
<b>Antropo-spatial capacity modeling(ASCM) | </b>
<br />
 It`s a git repo for technical part of same-named PhD desertation and open-sorce scientific project, based on it 
 <br />
 <br />
 <b>Metological steps for each type of integral indicators of economic life in anthropospatial space Big Data</b>
 <br />
1) creation of dataset
- extraction and processing of spatial data from resources that allow to see in real time integral indicators of economic life in anthropospatial space.
- creation of a set of images on which these integral indicators will display , thanks to visualization tools on the maps or clustering (for example k-mean clustering) 
- creating pandas DataFrame with coordinates, and the main characteristics of these images
2) data correctness analysis
- creating mechanisms to determine the correctness of data, for example, by comparing results from several sources, comparing different parts of images, etc.
3) visualization of data analysis
- creation of interactive web page displaying the received data for the largest cities of Ukraine
4) species prediction
- prediction of the future view of images based on existing images in specific time-series, thanks to the application of linear regression neural networks to them
5) data visualization
- creating an interactive web page displaying previously defined spatial features
6) analysis of spatial features
- nuclear separation and peripheralization
- determination of growth and decline poles
- spatial trendsetting
- downsizing heatmaps
7) visualization of spatial features
- creating an interactive web page displaying previously defined spatial features
8) subtracting space saturation
- calculation for each pixel of the value of coverage of integral indicators of economic life in anthropospatial space by a certain zone around it
9) forecast of space saturation
- prediction of the future type of space saturation images on the basis of existing images in specific time-series, thanks to the application of linear regression neural networks to them
10) visualization space saturation
- creating an interactive web page showing the saturation defined earlier
</br>
<b>Creating dataset from rental site</b> | <a href='https://colab.research.google.com/github/shliakhtas/ASCM/blob/main/rental_housing.ipynb'>open in colab<a>
</br>
<ul>
<li>parsing a rental site using BeautifulSoup and creating pandas DataFrame with the following columns: "district", "street", "sity", "price", "price_dollars", "rooms", "squere", "description", "date".</li>
<li>Data correction: removal of abbreviations in names, whitespaces, rows with no street names, date corrections from "Tommorow", "hover ago" in correct format, conversion of columns ' price ',' price_dollars', "rooms", "squere" from string to numerical format.</li>
<li>Creating additional columns with the price per unit of space and per room</li>
<li>Creating an ellipse around the city center, extracting only the streets included in it from the OpenStreet Maps dataset and creating the corresponding DataFrame </li>
<li>Create in that table columns with street names and their types from such possible ones:
"Lane", "row", "street", "driveway", "avenue", "square","embankment", "boulevard", "passageway", and "others"</li>
<li>Merge two tables into one by the "street" column</li>
<li>Creation of new columns with longitude and latitude, thanks to the processing of the "geometry" column</li>
<li>Grouping by "street" column and defining for each group the average price per unit of area and per room, it count, deleting groups where count is less than 3 and creating DataFrame with this data.</li>
<li>Adding this new data to the previous table by merging it with this table in the "street" column.</li>
<li>Creation of the function for grading a column into 5 categories, implementation of this function for 'mean_per_room', 'mean_per_squere', 'count' columns and creation of an additional color column for these columns, depending on the corresponding grading.</li>
<li>grading by dates depending on season winter-spring-summer-autumn for each year</li>
<li>Visualization of streets depending on the gradation of some column thanks to contextily and matplotlib.pyplot.</li>
  </ul>
