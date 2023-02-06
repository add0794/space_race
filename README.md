# Analyze and Visualize the Space Race<br />

Data analysts often bifurcate into two groups: those that program (e.g. R, Python) and those that don’t. Those that code do have access to features that are bragworthy: Python comes with pandas, numpy, Matplotlib; R, with ggplot2, dplyr. Those that don’t code use a graphical user interface (GUI) that frequently can still get the job done. Unless you’re completing an assignment that absolutely requires programming (e.g. categorization using computer vision), you’re well off not using a programming language. Use whichever works for you, whether that’s Excel, Tableau, etc.<br />

I set off on completing the following assignment using Excel to show that Python isn’t always necessary, and you should still know how to use GUI-based platforms.<br />

Details for the assignment are as follows, based on Udemy’s 100 Days of Code bootcamp:<br /><br />
  *You'll find an incredibly rich dataset from nextspaceflight.com that includes all the space missions since the beginning of Space Race between the USA and the Soviet Union in 1957! It has data on the mission status (success/failure), the cost of the mission, the number of launches per country, and much, much more. There's so much we can learn from this dataset about the dominant organizations and the trends over time. For example:*
<ol>
  <li><i>Who launched the most missions in any given year?</i></li>
  <li><i>How has the cost of a space mission varied over time?</i></li>
  <li><i>Which months are the most popular for launches?</i></li>
  <li><i>Have space missions gotten safer or has the chance of failure remained unchanged?</i></li>
</ol>

  *I'm sure that you'll discover many more questions that you can formulate and answer with this dataset! Use it to practice what you learnt about creating various types of charts and visualisations, from choropleths to sunburst charts to segmented bar charts and see if you can turn data into insight. Good luck!*<br />

### Q1: Who launched the most missions in any given year?

**A**: RVSN USSR in 1977<br />
**Approach**: By identifying the organizations (columns) and years of each mission (rows), I counted how often each organization’s mission by using COUNTIFS. That provided a table of occurrences, where I then found the maximum value using the MAX function and used "find" to find the organization and given year: RVSN USSR in 1977.

### Q2: How has the cost of a space mission varied over time?

**A**: The cost of space missions peaked in the mid-1970s, then decreased to null ($0), as it had been previously. It peaked again in the late 1980s, then began to decrease. It continues to remain low.<br /><br />![Cost of Space Missions Per Year](https://github.com/add0794/space_race/blob/5e87d8f73edd8a67a13af8e9a45b8779fc4a8ce0/Cost%20of%20Space%20Missions%20Per%20Year.png)<br /><br />
**Approach**: First, I added "N/A" for the missions in which any cell for the Price column was empty. I took the average price by using the AVERAGEIF function and included an IFERROR to account for those years where there no missions. I plotted year (x-axis) against missions (y-axis).

### Q3: Which months are the most popular for launches?

**A**: Launches increased and hit a peak in 1971, then slightly decreased until they reached a relative peak in the late 1980s. Then on, launches decreased until 2014, when they suddenly increased. They decreased precipitously in 2020.<br /><br />
![Launch Popularity over Time](https://github.com/add0794/space_race/blob/5e87d8f73edd8a67a13af8e9a45b8779fc4a8ce0/Launch%20Popularity%20over%20Time.png)
<br /><br />
**Approach**: To find the number of missions per year, I used COUNTIF. I plotted year (x-axis) and occurrences as the y-axis.

### Q4: Have space missions gotten safer or has the chance of failure remained unchanged?

**A**: When space missions first began, the chance of failure was high. Space missions have increased, but failures have decreased substantially. That said, while space missions have gotten safer, there remains the chance of failure.<br /><br />
![Success Rate of Mission Type by Year.](https://github.com/add0794/space_race/blob/5e87d8f73edd8a67a13af8e9a45b8779fc4a8ce0/Success%20Rate%20of%20Mission%20Type%20by%20Year.png)
<br /><br />
**Approach**: Using the mission_status column, I calculated the occurrences for each unique value (i.e. success, failure, prelaunch failure, and partial failure) by using the COUNTIFS function in each year. I plotted year (x-axis) and occurrences as the y-axis, with the types of occurrences to group by type.

# Was it more convenient and easier to use Excel than to program?

No surprise! There were advantages and disadvantages to using Excel rather than Python.

Advantages:

- Excel is inherently a no-code GUI. Everything is laid out in front of you: function outputs, tables, etc. If you make a mistake, you can always undo the action. With Python, you need to set up the options to see the entire table. Even then, you're most likely getting a small subset of the results unless you're using a Jupyter notebook that allows you to open another page to read the entire table. Creating a graph requires that you run the code again. In other words, accessibility is limited—but for a reason.
-	As I said earlier, you can undo the output and review your results. If you made a mistake, it's much easier to fix. If you make a mistake on Python, you often must start your Jupyter notebook from the beginning or, at least now you realize (!), create a copy of the dataframe.
-	Many functions are just as easy to use as those of Python’s, such as UNIQUE and MAX. In fact, using Python’s requires fundamental knowledge of object-oriented programming. Otherwise, you’re printing an attribute rather than a method.

Disadvantages:

-	When data becomes big data, COUNTIFS and IFERROR just don’t cut it. Python provides you with a hybrid of object-oriented and functional programming with various packages that make things streamlined, quicker, and less memory intensive.
-	Creating matrices in Excel is messy. If I wanted a dictionary for each mission’s year that included the organizations, average prices, etc. – well, it’s not possible. That’s why Python has pandas’ dataframes and dictionaries.
-	Copying function outputs in Excel can be a headache. If I want to copy the UNIQUE outputs, for instance, I'd have to do it again; otherwise, I must make an absolute reference. Pandas allows you to create a new column with the results.

While I enjoyed using Excel, I often found myself frustrated by looking up unnecessary functions and using multiple functions at once (e.g. INDEX, VLOOKUP, and MATCH). That could just as easily be done by adding multiple methods to Python’s pandas. I absolutely have a proclivity for Python, but I, nonetheless, believe that, even with that headache, Excel provided me the results I needed.
